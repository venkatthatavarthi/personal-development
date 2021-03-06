# Docker

## Key terms
| Term | Meaning |
| ---- | ------- |
| Docker | A platform for developers to develop, deploy and run applications with containers |
| Docker Compose | A tool for defining and running multi-container Docker applications |
| Docker Machine | A tool for creating and managing machines running Docker |
| Image | An executable package that includes everything needed to run an application - the code, a runtime, libraries, environment variables, and configuration files
| Container | A runtime instance of an image - what the image becomes in memory when executed (that is, an image with state, or a user process)
| Repository | A collection of images (like a GitHub repository, but with the code already built) |
| Registry | A collection of repositories |
| Service | A distinct part of a distributed application e.g. a database, a front-end etc. A service runs only one image, but replicas are common for e.g. load-balancing. Scaling a service entails increasing the number of containers running the application, assigning more computing resources to it. |
| Task | A single container running in a service. |
| Swarm | A group of machines running Docker, joined into a cluster. The swarm is orchestrated by a swarm manager |
| Node | A machine that is a member of a swarm (either a swarm manager or a worker). |

## Useful commands
### General docker commands
| Command | Description |
| :------ | :---------- |
| `docker --version` | See docker version |
| `docker info` | See docker info |
| `docker version` | See shorter docker info |

### Image and container commands
| Command | Description |
| :------ | :---------- |
| `docker image ls` | See all docker images on machine |
| `docker container ls` | See all (active) docker containers |
| `docker container ls --all` | See all previously run containers |
| `docker container ls -aq` | See just the uuids of all previously run containers (quiet mode) |

### Building images and running containers
| Command | Description |
| :------ | :---------- |
| `docker build -t friendly_name .` | Build a docker image from the current directory and tag it with `friendly_name` |
| `docker run image_name` | Run image `image_name` |
| `docker run -p machine_port:container_port friendly_name` | Run the image `friendly_name` and map the resulting container's published `container_port` to the `machine_port` |
| `docker run -d -p machine_port:container_port friendly_name` | Same as above, but detach from the container (run it in the background) and return the container ID |
| `docker container stop container_id` | Stop container `container_id` | 

### Sharing/deploying images
| Command | Description |
| :------ | :---------- |
| `docker login` | Log into the Docker public registry |
| `docker tag image_name username/respository:tag` | Tag an image for upload to a `repository` under account `username` in a registry; the `tag` is often used for versioning of the image |
| `docker push username/respository:tag` | Push an image to a repository in the Docker public registry. The container can now be deployed on any machine by using `docker run -p machine_port:container_port username/repository:tag` |

### Services
| Command | Description |
| :------ | :---------- |
| `docker swarm init` | Initialise a swarm of containers |
| `docker stack deploy -c docker-compose.yml app_name` | Deploy a new stack or update one, starting `app_name` by composing (`-c`) from a `docker-compose.yml` file |
| `docker service ls` | See all running services |
| `docker service ps app_name_service_name` | List the tasks of a service `service_name` running under `app_name` |
| `docker stack rm app_name` | Take down an app |
| `docker swarm leave --force` | Take down the swarm |

### Swarms
| Command | Description |
| :------ | :---------- |
| 
