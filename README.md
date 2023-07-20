# building-docker-for-jupyter-notebook

- I am running an exisiting or making a new docker image with python:

```terminal
docker run -it --name <your-name> python:<your-version> bash
```
where 'your-name' is the name of your docker image and 'your-version' is the version of your python, 'bash' opens bash in the new running image

- Install all the needed packages and upgrade PIP

```terminal
pip install --upgrade pip
pip install jupyter numpy pandas tensorflow etc
```
- Creating a config file in the docker for your jupyter

```terminal
jupyter notebook --generate-config
jupyter notebook password
```

- Running jupyter notebook in the docker image

``` terminal
jupyter notebook --ip=0.0.0.0 --port=<container-port> --allow-root --NotebookApp.token='<your-token>' --NotebookApp.allow_origin='*'
```

where --ip=0.0.0.0 resets the ip of your docker inside the docker image. in order to check your real ip run:
``` termial
docker inspect <the name of the image>
```
'container-port' is the port for your running docker image - standard --port=8888

'your-token' can be replaced by any token of yours...


Example of the commands I personally run:

```terminal
docker run -it --name tensorflow-docker python:3.8 bash

pip install --upgrade pip

pip install numpy pandas jupyter tensorflow matplotlib scikit-learn

jupyter notebook --generate-config
jupyter notebook password

jupyter notebook --ip=0.0.0.0 --port=8888 --allow-root --NotebookApp.token='helloworld' --NotebookApp.allow_origin='*'
```
