# Reproducible Jupyter RISE presentation environment

Build interactive Reveal.js slide decks from Jupyter notebooks with a ready-to-use RISE environment for Docker or Vagrant. This reusable template is intended for teachers, lecturers, workshops, and technical presentations that combine executable Python with slides.

## Included presentation features

The example RISE notebook includes:

* two columns
* lists
* manim animation
* fragments
* subslides
* notes
* hidden input cells
* highlights

For complete teaching examples, see the [public interactive lecture notes](https://github.com/tapekuna-ai/public-lecture-notes-tapkuna.ai). For a modern, browser-only JupyterLite alternative, see [RISE Lite](https://github.com/thomasliebig/RISE-lite).

## Quick start with Docker

```bash
git clone https://github.com/tapekuna-ai/jupyter-notebook-RISE-environment.git
cd jupyter-notebook-RISE-environment
docker-compose up -d
```

Open <http://localhost:8000/notebooks/Template.ipynb> and start adapting the presentation template.

## Starting with Vagrant

### Initialization

Build virtual machine

```bash
vagrant up
```

Take snapshot of the virtual machine

```bash
vagrant snapshot save jupyter
```

### Start of the Session

```bash
vagrant snapshot restore jupyter
```

* point your browser to http://localhost:8000/ or http://localhost:8000/notebooks/Template.ipynb for a slide template to get started

### End of the Session

```bash
vagrant halt
```

### Reprovision (In case something went wrong)

```bash
vagrant provision
```

## Docker details

This repo includes a Dockerfile, wich builds the image to run jupyter notebook with all slide extensions described earlier. Additionally, it contains a `docker-compose.yml` file, which allows easy starting and stopping of the container.

### Prerequisites

1. [Docker](https://docs.docker.com/engine/install/) needs to be installed and running
2. [Docker-Compose](https://docs.docker.com/compose/install/linux/) needs to be installed, if it is not shipped with the Docker install.
3. The host machine needs to have an open port on 8000 for accessing the jupyter notebook interface in a browser. If the port is not available, you can change it in the `docker-compose.yml` file.

### Starting
You need to start a terminal with _RISE-Environment_ as the current __working directory__. The first startup can take some time, since the image needs to be built first. Afterwards, each startup should take less than 10 seconds.
To start the application simply run:
```
docker-compose up -d
```

### Stopping
To stop the application simply run:
```
docker-compose stop
```
The current state of the notebook will be automatically persisted in the notebooks folder of this repository.

### Removal of the image
To remove the image completely from the disk, simply run:
```
docker-compose down
``` 
