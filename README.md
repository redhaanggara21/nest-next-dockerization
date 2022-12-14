create apps sound detacted

- Backend
  - NestJS
  - Prisma
  - GraphQL
- Frontend
  - Next.js / React
  - GraphQL Code Generator
  - Apollo Client
  - Semantic UI
  - emotion
- Other
  - np workspace
  - ESLint / Prettier / husky
  - Docker / Docker Compose
  - Vercel
  - GCP (CloudSQL / Cloud Run / Cloud Build)

## Getting Started

### Docker

You can launch the development environment with one command!

```bash
docker-compose up
```

After successful launch, go to the following URL in your browser!
- Backend: http://localhost:3300/graphql
- Frontend: http://localhost:3000

:warning: Containers have dependencies, but the next container may start to be started before the preparation is complete.
If it fails for that reason, please specify the start-up separately as follows.

```bash
docker-compose up mysql
```

See `docker-compose.yaml` if you want to know more.

### Local

1. Prepare MySQL and create a database for development.
Then create file `packages/backend/.env` and fill in the environment variables.

```.env.example
DATABASE_URL="mysql://username:password@localhost:3306/nest_next_sample"
```


2. Do a database migration.

```bash
cd packages/backend
npm install
npm migrate:deploy
```

3. Run the startup command for backend.

```bash
npm start:dev
```

After successful launch, go to http://localhost:3300/graphql in your browser!

4. Create file `packages/frontend/.env` and fill in the environment variables.

```.env.example
SERVER_APOLLO_URI="http://localhost:3300"
PUBLIC_APOLLO_URI="http://localhost:3300"
```

5. Run the startup command for frontend.

```bash
cd packages/frontend
npm dev
```

After successful launch, go to http://localhost:3000 in your browser!


## GraphQL exmaple

```graphql
mutation {
  saveTask(task: { title: "test", categoryIds: [] }) {
    id
    title
    categories {
      id
      name
      color
    }
  }
}
```

```graphql
query {
  task(id: 1) {
    id
    title
    taskContents {
      id
      checked
    }
    categories {
      id
      name
    }
  }
}
```

