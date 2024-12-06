🚀 TinyURL Service
---
🌐 A URL Shortener Service Built with Cutting-Edge Technologies <br>
This project is a high-performance URL shortener built using Spring Boot, Redis, MongoDB, Cassandra, and integrated with Swagger for API documentation.
---
🛠️ Features

    Fast and Scalable: Powered by Redis, MongoDB, and Cassandra for optimal performance.
    Dynamic API Documentation: Seamlessly integrated with Swagger for easy testing and exploration.
    Interactive Backend: Spring Boot and Java provide a robust foundation.
    Dockerized Services: Effortlessly manage Redis, MongoDB, and Cassandra using Docker Compose.
---
🎯 Why Choose This Stack?
🏎️ Redis

    Blazing Fast in-memory database, ensuring quick lookups for shortened URLs.
    Built-in Support for operations like SET and GET, ensuring easy-to-use data manipulation.
    Ideal for use cases requiring real-time response times.

🌱 MongoDB

    Flexible Schema: Perfect for storing user and URL data with dynamic fields.
    Scales horizontally for handling large datasets efficiently.

💾 Cassandra

    Highly Available: Offers a distributed, fault-tolerant database for user click analytics.
    Linear Scalability: Handles massive data throughput with ease.

📖 Swagger

    Auto-generated API Documentation for seamless testing.
    Integrated UI at http://localhost:8080/swagger-ui.html to explore endpoints.

##🐳 Docker

    Docker simplifies the deployment of services in isolated containers.
    Docker Compose orchestrates multiple services (e.g., Redis, MongoDB, Cassandra) with one command.
    Run all dependencies using a single docker-compose up -d command, ensuring portability and consistency across environments.
---
🚧 Project Setup
1️⃣ Clone Repository

git clone <repository-url>
cd tinyurl

2️⃣ Setup Hosts File

Edit your /etc/hosts file to map services locally:

127.0.0.1 cassandra  
127.0.0.1 redis  
127.0.0.1 mongo  

3️⃣ Run Docker Services

Start the required services using Docker Compose:

docker-compose up -d

Verify containers are running:

docker ps
---
🚀 Endpoints
🎯 URL Shortening

    Generate Tiny URL
    POST /tiny

    Request:

{
  "longUrl": "https://www.example.com",
  "userName": "testUser"
}

Response:

    http://localhost:8080/AbCdEf/

    Redirect to Original URL
    GET /{tiny}/
    Redirects to the original longUrl.

📋 User Management

    Create User
    POST /user
    Query Parameter: name=YourName

    Get User by Name
    GET /user/{name}

    Get User Clicks
    GET /user/{name}/clicks
---
⚙️ Swagger Integration
1. Add the following to pom.xml:

<dependency>
  <groupId>io.springfox</groupId>
  <artifactId>springfox-swagger-ui</artifactId>
  <version>2.6.1</version>
</dependency>
<dependency>
  <groupId>io.springfox</groupId>
  <artifactId>springfox-swagger2</artifactId>
  <version>2.6.1</version>
</dependency>

2. Configure SwaggerConfig.java:

@Configuration
@EnableSwagger2
public class SwaggerConfig {
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .select()
                .apis(RequestHandlerSelectors.any())
                .paths(PathSelectors.any())
                .build();
    }
}

3. Access Swagger UI:

http://localhost:8080/swagger-ui.html
---
📦 Technologies Used
Technology	Purpose	Advantages
Spring Boot	Backend Framework	Fast development, scalable architecture
Redis	In-Memory Database	High-speed read/write, simple API
MongoDB	NoSQL Database	Flexible schema, great for JSON data
Cassandra	Distributed Database	Highly available, handles big data
Swagger	API Documentation	Interactive and auto-generated
Docker	Containerization	Portable, easy to manage environments
---
🌍 How It Works

    User provides a long URL and optional username.
    Backend generates a unique, 6-character Tiny URL.
    Redis stores the mapping for lightning-fast lookups.
    MongoDB tracks users and their created URLs.
    Cassandra logs click analytics for reporting and insights.
---
🤝 Contributing

Contributions are welcome! Please fork this repository and submit a pull request with your changes.
---
🎉 Happy Coding!
