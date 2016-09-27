# Ansible Container Hydra

Deploy Hydra to Docker with [Ansible Container](https://github.com/ansible/ansible-container).

*Status:* Exploratory development.

*Work in Progress Note:* This container clones the Hydra application into the container's /app directory and
installs the Ruby gems. To support development, it then mounts the working directory in
place of the container's /app directory.

Currently provisions a Docker container to install Hydra on a mountable volume.

    git clone https://github.com/skng5/ansible-container-hydra.git

To install, clone this repository into your Hydra development enviornment

Build the container:

    ansible-container build

And run the container:

    ansible-container run

Since this is an exploratory container, you can shell in from a separate termial session:

    docker exec -it ansible_tulhydra_1 bash

Switch to the hydra user:

    su - tulhydra

Prep your application:

    cd /app
    bundle install
    rake db:migrate
    rake jetty:start

Wait until jetty is up and running. You should see it running at `http://localhost:8983`.
When it's running, start your hydra server:

    rails server

And you should see your application running at `http://localhost:3000`.

To stop the container, go to the session where you ran the container and hit `CTRL-c`.

