# Dockerized HTML Website with Nginx

This repository provides a guide on how to create a Docker image to host an HTML website using Nginx. It includes an example Dockerfile and instructions for building and running the Docker container. You can use any HTML template, such as those available on [Free CSS Templates](https://www.free-css.com/free-css-templates).

## Prerequisites

Before you begin, ensure you have the following installed on your local machine:

- [Docker](https://docs.docker.com/get-docker/)

## Notes
- Ensure you replace <yourdockerhubusername> with your actual Docker Hub username in the commands.
- For security purposes, avoid using the latest tag in production environments.
- specify a specific version number instead.

## Steps to Create and Run a Docker Image with HTML Website

### 1. Choose and Download an HTML Template

1. Visit [Free CSS Templates](https://www.free-css.com/free-css-templates) and browse through the available templates.
2. Choose a template you like and download it as a ZIP file.
3. Extract the contents of the ZIP file to a folder on your local machine.

### 2. Prepare Your Project Directory

1. Create a new directory for your project:

    ```bash
    mkdir html-website-docker
    cd html-website-docker
    ```

2. Inside this directory, create a subdirectory named `website` and move the extracted HTML template files into this folder:

    ```bash
    mkdir website
    mv /path/to/extracted-html-template/* website/
    ```

3. Your project directory structure should look like this:

    ```plaintext
    html-website-docker/
    ├── Dockerfile
    └── website/
        ├── index.html
        ├── about.html
        ├── css/
        ├── js/
        ├── images/
        └── ... (other HTML/CSS/JS files and assets)
    ```

### 3. Create the Dockerfile

Create a `Dockerfile` in the `html-website-docker` directory with the following content:

```dockerfile
# Use the official Nginx image as the base image
FROM nginx:alpine

# Copy the HTML website files to the Nginx directory
COPY website/ /usr/share/nginx/html

# Expose port 80 to the outside world
EXPOSE 80
```
### 4. Build the Docker Image
Run the following command to build the Docker image. Replace yourdockerhubusername with your Docker Hub username.

```bash
docker build -t yourdockerhubusername/html-website:latest .
```
This command will create a Docker image tagged as yourdockerhubusername/html-website:latest.

### 5. Run the Docker Container
To run the Docker container and expose it on port 8080 of your local machine, use the following command:
```bash
docker run -d -p 8080:80 yourdockerhubusername/html-website:latest
```
This command will run the Docker container in detached mode (-d) and map port 80 inside the container to port 8080 on your host machine.

### 6. Access Your Website
Open a web browser and navigate to http://localhost:8080 to view your HTML website hosted by Nginx.

### 7. Push the Docker Image to Docker Hub (Optional)
If you want to share your Docker image, push it to Docker Hub using the following command:
Login to your Dockerhub Account:

```bash
docker login
```
Push the image: 
```bash
docker push yourdockerhubusername/html-website:latest
```
### 8. Pull and Run the Docker Image from Docker Hub (Optional)
Others can pull and run your Docker image from Docker Hub using:
```bash
docker pull yourdockerhubusername/html-website:latest
docker run -d -p 8080:80 yourdockerhubusername/html-website:latest
```
### Conclusion
You have successfully created and run a Docker container that serves an HTML website using Nginx. 
Feel free to experiment with different HTML templates from Free CSS Templates or customize the Dockerfile to suit your needs!
