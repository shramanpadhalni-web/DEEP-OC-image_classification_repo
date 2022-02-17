<div align="center">
<img src="https://marketplace.deep-hybrid-datacloud.eu/images/logo-deep.png" alt="logo" width="300"/>
</div>

# DEEP-OC-image_classification_repo

[![Build Status](https://jenkins.indigo-datacloud.eu/buildStatus/icon?job=Pipeline-as-code/DEEP-OC-org/DEEP-OC-image_classification_repo/master)](https://jenkins.indigo-datacloud.eu/job/Pipeline-as-code/job/DEEP-OC-org/job/DEEP-OC-image_classification_repo/job/master)

This is a container that will run [image_classification_repo](https://github.com/shramanpadhalni-web/image_classification_repo) application leveraging the DEEP as a Service API component ([DEEPaaS API V2](https://github.com/indigo-dc/DEEPaaS)).

    
## Running the container

### Directly from Docker Hub

To run the Docker container directly from Docker Hub and start using the API
simply run the following command:

```bash
$ docker run -ti -p 5000:5000 -p 6006:6006 shramanpadhalni-web/deep-oc-image_classification_repo
```

This command will pull the Docker container from the Docker Hub
[shramanpadhalni-web](https://hub.docker.com/u/shramanpadhalni-web/) repository and start the default command (deepaas-run --listen-ip=0.0.0.0).

**N.B.** For either CPU-based or GPU-based images you can also use [udocker](https://github.com/indigo-dc/udocker).


### Running via docker-compose

docker-compose.yml allows you to run the application with various configurations via docker-compose, for example:

```bash
$ docker-compose up image_classification_repo
```

**N.B!** docker-compose.yml is of version '2.3', one needs docker 17.06.0+ and docker-compose ver.1.16.0+, see https://docs.docker.com/compose/install/

If you want to use Nvidia GPU, you need nvidia-docker and docker-compose ver1.19.0+ , see [nvidia/FAQ](https://github.com/NVIDIA/nvidia-docker/wiki/Frequently-Asked-Questions#do-you-support-docker-compose)


### Building the container

If you want to build the container directly in your machine (because you want
to modify the `Dockerfile` for instance) follow the following instructions:

Building the container:

1. Get the `DEEP-OC-image_classification_repo` repository (this repo):

    ```bash
    $ git clone https://github.com/shramanpadhalni-web/DEEP-OC-image_classification_repo
    ```

2. Build the container:

    ```bash
    $ cd DEEP-OC-image_classification_repo
    $ docker build -t shramanpadhalni-web/deep-oc-image_classification_repo .
    ```

3. Run the container (if you enable JupyterLab during the build, `--build-arg jlab=true`, 
you should also add port 8888, i.e. `-p 8888:8888`):

    ```bash
    $ docker run -ti -p 5000:5000 -p 6006:6006 shramanpadhalni-web/deep-oc-image_classification_repo
    ```

These three steps will download the repository from GitHub and will build the
Docker container locally on your machine. You can inspect and modify the
`Dockerfile` in order to check what is going on. For instance, you can pass the
`--debug=True` flag to the `deepaas-run` command, in order to enable the debug
mode.


## Connect to the API

Once the container is up and running, browse to `http://localhost:5000` to get
the [OpenAPI (Swagger)](https://www.openapis.org/) documentation page.
