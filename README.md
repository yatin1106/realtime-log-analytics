# Real-Time Log Analytics Pipeline

A real-time distributed data pipeline that ingests high-volume events through a C++ server, streams them via Kafka, processes them with Spark, stores results in MongoDB, and displays live metrics on a React dashboard.

## Stack

- C++ — high-performance ingestion server with thread pool
- Apache Kafka — distributed message streaming
- Apache Spark — real-time stream processing
- MongoDB — storage for processed event data
- Node.js + Express — REST API
- React — live analytics dashboard

## Architecture

```
Python Load Test -> C++ Server -> Kafka -> Spark -> MongoDB -> Node API -> React Dashboard
```

## How to run

1. Start Kafka: `docker run -d --name kafka -p 9092:9092 apache/kafka:3.7.0`
2. Start MongoDB: `brew services start mongodb-community`
3. Compile and run C++ server: `g++ -std=c++17 -o server_kafka server_kafka.cpp -lrdkafka++ -lrdkafka -pthread && ./server_kafka`
4. Run Spark consumer: `python3 spark_consumer.py`
5. Start backend: `cd dashboard && node server.js`
6. Start frontend: `cd frontend && npm start`
7. Send events: `python3 load_test.py`

Open http://localhost:3000 to view the dashboard.
