FROM golang:alpine AS builder

WORKDIR /app

COPY fullcycle.go .
COPY go.mod .

RUN go mod tidy
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o fullcycle .

FROM scratch

COPY --from=builder /app/fullcycle /fullcycle

CMD ["/fullcycle"]