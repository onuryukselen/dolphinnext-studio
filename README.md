DolphinNext docker version
========
DolphinNext original repository is located at https://github.com/UMMS-Biocore/dolphinnext.

For a quick start please check our quick start guide. https://dolphinnext.readthedocs.io/en/latest/dolphinNext/quick.html

DolphinNext can also be run as a standalone application using a docker container.
First docker image need to be build unless you want to use prebuild from dockerhub. So, any change in the Dockerfile requires to build the image. But if you want to use prebuild version just skip building it and start the container.

Build docker image
---------

1. To build docker image first clone one of the latest dolphinnext-docker

```
git clone https://github.com/UMMS-Biocore/dolphinnext-studio.git
```

2. Build the image
  
  ```
  cd dolphinnext-studio 
  docker build -t dolphinnext-studio .
  ```

Start the container
---------

1. We move database outside of the container to be able to keep the changes in the database everytime you start the container.
Please choose a directory in your machine to mount and replace `/path/to/mount` with your path. 
* Note: Please don't change the target directory(`/export`) in the docker image. 

```
mkdir -p /path/to/mount
```

2. While running the container;
```
docker run -m 10G -p 8080:80 -v /path/to/mount:/export -ti dolphinnext-docker /bin/bash
```
*if you want to run a pre-build
```
docker run -m 10G -p 8080:80 -v /path/to/mount:/export -ti ummsbiocore/dolphinnext-studio /bin/bash
```
3. After you start the container, you need to start the mysql and apache server usign the command below;
```
startup
```
4. Now, you can open your browser to access dolphinnext using the url below.

http://localhost:8080/dolphinnext


