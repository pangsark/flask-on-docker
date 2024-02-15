# Flask on Docker

## Overview

This repository holds the Docker configuration to deploy a Flask application for both developmental and production environments. 
The Flask application is equipped with Postgres, Nginx, and Gunicorn to manage both static and media files. This repository is created
by following the [tutorial](https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx) by Michael Herman. 

Example of uploading and viewing an image through this Flask app is shown below:

## Build Instructions

Before starting, clone this repository and go to the project directory

### Development

1. Build and run the development containers with this command: 

```
$ docker-compose up -d --build
```

2. To sanity check run this command: 

```
$ curl http://localhost:1351
```

You should be getting an output like this:
```
{
  "hello": "world"
}
```

3. You can bring the development container down with this command: 

```
$ docker-compose down -v
```

### Production

1. At the project directory, run these commands to build and run the production containers:

```
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```

2. You can now upload an image using the flask app by visiting: http://localhost:1351/upload
3. Then, you can view the image at: http://localhost:1337/media/IMAGE_FILE_NAME

4. To bring the production containers down, use the following command:

```
$ docker-compose -f docker-compose.prod.yml down -v
```


