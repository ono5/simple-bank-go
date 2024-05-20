# Simple 

## Postgres

```bash
docker run --name postgres12 -p 5432:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=secret -d postgres:12-alpine
docker exec -it postgres12 psql -U root
docker logs postgres12
```

## Tools

### go-migrate
```bash
brew install golang-migrate

migrate -version
v4.17.1

mkdir -p db/migration 

migrate create -ext sql -dir db/migration -seq init_schema

migrate -path db/migration -database "postgres://root:secret@localhost:5432/simple_bank?sslmode=disable" -verbose up
```

### sqlx
```bash
brew install kyleconroy/sqlc/sqlc

sqlc version

sqlc init
sqlc generate
```