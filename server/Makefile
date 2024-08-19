postgresinit:
	docker run --name postgres15 -p 5434:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=password -d postgres:15-alpine

postgres:
	docker exec -it postgres15 psql

createdb:
	docker exec -it postgres15 createdb --username=root --owner=root go-realtime-chat

dropdb:
	docker exec -it postgres15 dropdb go-realtime-chat

migrateup:
	migrate -path db/migrations -database "postgresql://root:password@localhost:5434/go-realtime-chat?sslmode=disable" -verbose up

migratedown:
	migrate -path db/migrations -database "postgresql://root:password@localhost:5434/go-realtime-chat?sslmode=disable" -verbose down

.PHONY: postgresinit postgres createdb dropdb