# CodeAlpha Docker Web Server

A simple web server deployment project built using Docker and Nginx.

This project demonstrates how to containerize a static HTML website using Docker and serve it through an Nginx web server.

## Project Objectives

- Learn Docker containerization
- Build a Docker image using a Dockerfile
- Run a web server inside a Docker container
- Configure port mapping
- Monitor container health
- Check container logs
- Understand container lifecycle and troubleshooting

## Technologies Used

- Docker
- Nginx
- Alpine Linux
- HTML
- Git
- GitHub

## Project Structure

```text
CodeAlpha_DockerWebServer/
│
├── Dockerfile
├── index.html
└── README.md

## Architecture
User Browser
     |
     | HTTP Request
     ↓
localhost:8080
     |
     | Port Mapping: 8080 → 80
     ↓
Docker Container
     |
     ↓
Nginx Web Server
     |
     ↓
index.html
     |
     | HTTP Response
     ↓
User Browser
Dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=3s --retries=3 CMD wget --no-verbose --tries=1 --spider http://localhost/ || exit 1
Dockerfile Explanation
Base Image

FROM nginx:alpine uses a lightweight Nginx image based on Alpine Linux.

Copy Website

COPY index.html /usr/share/nginx/html/index.html copies the website into the default Nginx web root.

Expose Port

EXPOSE 80 documents that Nginx listens on port 80 inside the container.

Health Check

The health check periodically verifies that the Nginx web server is responding successfully.

How to Build the Docker Image
docker build -t codealpha-webserver .
How to Run the Container
docker run -d -p 8080:80 --name codealpha-webserver-container codealpha-webserver
Access the Web Server

Open this URL in your browser:

http://localhost:8080
Container Management
Check Running Containers
docker ps
Stop Container
docker stop codealpha-webserver-container
Start Container
docker start codealpha-webserver-container
Restart Container
docker restart codealpha-webserver-container
View Container Logs
docker logs codealpha-webserver-container
Check Container Health
docker ps

The container should show:

(healthy)
Troubleshooting

Docker logs can be used to identify problems with the Nginx web server:

docker logs codealpha-webserver-container

The container status can be checked using:

docker ps

If the container is stopped, start it using:

docker start codealpha-webserver-container

If the container needs to be restarted:

docker restart codealpha-webserver-container
Learning Outcomes

Through this project, I learned:

Docker images and containers
Dockerfile instructions
Nginx web server deployment
Docker port mapping
Container lifecycle management
Container logs
Docker health checks
Basic container troubleshooting
Git and GitHub workflow
