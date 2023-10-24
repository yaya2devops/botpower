# Chatbot Development Documentation

## Requirements

To set up your environment for building chatbot tools, make sure you have the following components installed:

1. Docker
2. Miniconda
3. JupyterLab


### Miniconda setup

(flow: activate +jupyter lab port)

```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh


~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init zsh
```

- Create a py env for chatbot
```
conda create -n chatbot python=3.7
```

- Activate that chatbot and verif py
```
conda activate chatbot
python --version
```

### JypterLab Setup


- Using miniconda, get jypterlab
```
conda install jupyterlab 
```

- Create our workspace and go to it
```
mkdir chatbot && cd chatbot
```

- Start a new lab using

```
jupyter lab
```

- You can also access using the following;
```
jupyter lab --ip 0.0.0.0 --port 5050
```


### Screen Package Use Case

You use some server shell and want it play in the background. Then get screened.


1. Install the "screen" package using apt if you haven't already.
```
sudo apt install screen
```


2. To start a new screen session named "jupyterlab", Open a terminal and type the following command:
```
screen -S jupyterlab
```

This will take you to a new screen session where you can run other commands or shells.


3. To detach from the current screen session and return to the main terminal:

> Press `Ctrl + A` and then `Ctrl + D`.

4. If you've detached from the screen session and want to get back to it, use the following command:

```
screen -r jupyterlab
```

## Building Chatbot Tools

You can build chatbot tools using the following technologies:

1. Dialogflow
2. Botpress (Free to use, Docker-based)

## Setting up Jupyter Lab

1. Open Jupyter Lab.
2. Go to your terminal in the chatbot directory.
3. Install the 'wget' and 'zipurl' packages.
4. Install 'zip' and 'unzip' packages using the command: `sudo apt install zip unzip`.

## Chatbot Configuration

In the chatbot configuration, consider the following steps:

1. Care about Docker Compose files, and select the one for the community version.
2. Ensure you update the `EXTERNAL_URL` in your Compose file. If you are using a virtual machine, change the IP accordingly.
3. Update the password for PostgreSQL (psql) if required.

### Docker Volumes

For Docker Compose, you need to create and configure directories:

1. Create directories for Botpress data and language using `mkdir -p ./botpress/data` and `./botpress/language`.
2. Give permission to both directories using `sudo chmod -R 777` for both directories.
3. Update the volume paths in Docker Compose to `botpress_data` and `botpress_language`. This ensures the volumes are attached to Docker, not stored locally.

### Dockerfile Update

Inside the Botpress directory, update the image version from DockerHub in your Dockerfile.

## Testing the Environment

Refer to the README of your Docker Compose configuration for the exact command to run the community version. Run it using `sudo`.

## Keeping Botpress Maintained

To keep Botpress up to date:

1. Update the version in your Dockerfile `FROM`.
2. Add the flag `--auto-migrate` to the `CMD` to enable automatic migrations.

Sometimes, a fresh installation is required. To do this:

1. Clean your resources by turning down all containers using `sudo docker-compose down`.
2. Remove any containers using `sudo docker rm -f $(sudo docker ps -a -q)`.
3. Terminate all resources with `sudo docker system prune -a`.

Now you are ready to reinstall Botpress.

## Designing Chatbot Flow

When designing your chatbot's flow, consider the following:

- Implement proper delay times using "execute code" and run utility functions.
- Organize the "on enter" order effectively.
- Store data from conversations in storage functions.
- Provide file attachments for the user.

## Workflow Representation

It's essential to apply your scenario on paper and later translate it into a chatbot flow using nodes connected to one another.

## Considerations

When designing your chatbot's flow, keep these considerations in mind:

- Ensure proper delay times using "execute code" and utility functions.
- Organize the "on enter" order effectively.
- Utilize storage functions to store and retrieve information from conversations.
- Allow users to attach files for enhanced interactions.