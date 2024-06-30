# docker-challenge-template

Docker Installation Guide
By: Romeo Costillas

The very first thing to do in this project is to install the Docker Desktop in our computer. Here are the simple steps to achieve this.

a. Navigate to this site and download the Docker installer

Link: https://www.docker.com/products/docker-desktop/

After installation, you can either sign up for an account if you don't have one, sign in if you already do, or simply click "Continue without signing up" located at the bottom of the pop-up message.

Challenge #1 - Simple Static Page Server
This is a simple introduction on how to use Docker to serve some static pages.

Goals
• Learn the basics of Docker
• Build a Docker Image
• Be able to run the container and see the results on a browser
• Publish the Dockerfile and related files on GitHub.

Steps to Achieve this

1. Create a new folder called “challenge1”.
2. Add a “public” folder inside the “challenge1” folder.
3. Inside the “public” folder, create a new file called “index.html”.
4. Add some basic html codes that will show your basic information like your Name, Sait ID, and Date Submitted.
5. Create a new file named "Dockerfile" in the public folder, which will use Nginx to serve pages.

To create our custom image, we start by using a base image. We use the “FROM” command to pull the nginx image to our local machine, and then build our custom image on top of it. Next, we use the “COPY” command to place our index.html file into the /usr/share/nginx/html directory inside the container, overwriting the default index.html file provided by nginx. [1]

6. To build a docker image, we need to navigate to the folder “challenge1” and type docker build --t challenge1 . [2]
7. You will be able to see when building is finished. No error should be displayed in the terminal screen.
8. Go back to Docker Desktop to validate if the image is there.
9. Run action by clicking the play button located in the right corner of the screen.
10. Provide necessary details including “Container name”, host port to set to “8080” then click the “Run” button.
11. In the containers section, you’ll see the “challenge1” image is running and beginning to create a container.
12. Once completed, the container will be available in the port specified earlier. In our example, the port is 8080.
13. After finishing the setup of your Docker container, accessing your index.html file using Docker Studio is simple. Clicking on port 8080 grants you direct access to view the index.html page. This port acts as the entry point through which Docker Studio directs requests to the container that hosts your application.

Within Docker Studio, accessing port 8080 enables you to engage with the content served by your Docker container. This user-friendly interface facilitates the management and monitoring of your Dockerized applications, offering insights into container performance and the content delivered to users or other system components. 14. Commit and publish it in GitHub.

Challenge #2 – NodeJS Application
Here's a basic guide on using Docker to expose endpoints for external clients and orchestrate a NodeJS application with a web server using Docker Compose.

Goals
• Introduce the concept of Docker compose.
• Given a simple NodeJS application, create the Dockerfile.
• Watch a dynamic application running on Docker.
• Build a foundation for the next step.

Steps to Achieve this

1. Create a new folder called “challenge2”.
2. Add a “public” folder inside the “challenge1” folder.
3. Extract the files from challenge2.zip into the root folder of the challenge2 folder.
   a. Package-lock.json
   b. Package.json
   c. Server.js
4. Create a new file named “Dockerfile” inside challenge2 folder to build the server’s Docker container.

A Dockerfile has a specific format and syntax. Every line in a Dockerfile represents a layer within the image. Beginning with the definition of a Node.js base image, the Dockerfile then sets the working directory, copies over dependency files, installs them using npm, transfers the application code, exposes port 3000 for external connectivity, and concludes by specifying the command to start the application with node app.js when the container is launched. [3]

This setup configures a nginx server to operate on port 80. Incoming requests to the server's root (/) are forwarded to a service called "app" running on port 3000 using HTTP protocol version 1.1. Extra headers such as Upgrade, Connection, and Host are configured to ensure seamless proxying, especially for applications that rely on WebSocket connections. [4]

5. To build a docker image, go to terminal and navigate to the folder “challenge2” and type docker build --t challenge2 .
6. You will be able to see when building is finished. No error should be displayed in the terminal screen.
7. Go back to Docker Desktop to validate if the image is there.
8. Run action by clicking the play button located in the right corner of the screen.
9. Provide necessary details including “Container name”, host port to set to “8080” then click the “Run” button.
10. In the containers section, make sure that “challenge1” container is not running.
11. To start running the “challenge2” container, click the “Run” button.
12. Go to http://localhost:8080/api/books.
13. To access ID number 1 or 3, simply add “/” followed by the respective ID to the URL. Refer to the screenshot below for clarification.
14. Commit and publish it in GitHub.

References:
[1] P. McKee. “How to use the NGINX Docker Official Image.” Docker. Accessed: Jun. 29, 2024. [Online]. Available: https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/

[2] “How to Build a Docker Image.” Software AG. Accessed: Jun. 29, 2024. [Online]. Available: https://documentation.softwareag.com/adabas/ada701luw/docker/docker-build.htm

[3] A. Fawade. “How to Create a Docker Project for a Node.js Web Application | 90 Days Of DevOps.” Medium. Accessed: Jun. 29, 2024. [Online]. Available: https://medium.com/@ajitfawade/how-to-create-a-docker-project-for-a-node-js-web-application-90-days-of-devops-e3623f46bf7

[4] Linode. “Use NGINX as a Reverse Proxy.” Linode. Accessed: Jun. 29, 2024. [Online]. Available: https://www.linode.com/docs/guides/use-nginx-reverse-proxy/
