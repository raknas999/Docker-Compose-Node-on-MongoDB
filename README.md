# How to use Docker Compose to run complex multi container apps - Node on MongoDB

This docker files shows how to build your own base image for various cloudera components running on Centos6.6
This is a simple setup with 3 Nodes and one MongoDB as backend run along with Weave for service discovery. Later will show you how to use [Apache Bench](http://httpd.apache.org/docs/2.2/programs/ab.html) to test the nodes and the fault tolerance of failing one _NODE_ intentionally

### We'll be using the following tools, technologies, and services in this post:
* Docker
* Docker Compose
* NodeJS
* MongoDB
* Weave
* Docker Hub
* Git
* OMDB API

## Composing our Services
To get our five container configuration set up we first need to create a `docker-compose.yml` file. We will need three containers webNode1, webNode2 and webNode3
based on our web application image and one haproxy container. The webservers will be running on port `8081` and the haproxy admin port will be `70`. Feel free to change them in `docker-compose.yml` and `Dockerfile` to which ever ports are convinient for you.



### Sample Code
```
                       |WebNode1|
User <--> HAProxy <--> |WebNode2| <--> MongoDB-Node1
                       |WebNode3|
```


##### To Do
- [x] Setup [Apache Bench](http://httpd.apache.org/docs/2.2/programs/ab.html) along with Docker Compose
- [ ] Find a way to add vm.swapiness during build, probably echo it into the file?
