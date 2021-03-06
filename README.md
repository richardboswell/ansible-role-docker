# ansible-role-docker

[Ansible](https://github.com/ansible/ansible) role for adding
and managing Docker Engine services.

## Requirements

None known.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# only needs to be set if running ubuntu
ubuntu_release: trusty

# disable docker bridge?
docker_disable_bridge: false

# where to place/look for DOCKER_OPTS
docker_env_file: /etc/default/docker

# the docker service unit file to modify as necessary
# given additional variables below
docker_unit_file: /lib/systemd/system/docker.service

# Which bridge to use for Docker in bridged mode
docker_bridge_device: docker0

# Additional options to add to the docker deamon
docker_opts: ""

# used to disable actions that might fail when
# running tests under docker.
docker_running_under_docker: false

# if flannel is running, read in theat environment.
flannel_env_file: /var/run/flannel/subnet.env

# This is commented for doc purposes only. If defined
# docker_opts (see above) will get added to the docker
# daemon command line at start. For example:
#   --dns 8.8.8.8 --dns 8.8.4.4
#docker_opts: daemon

# docker user/group ids (gets created) for socket access
# and similar
docker_user: docker
docker_gid: 995
```

## Example playbook

```yaml
---
- hosts: dockers
  sudo: True
  roles:
    - docker
  vars:
    docker_opts: "--dns 8.8.8.8 --dns 8.8.4.4"
```

# License and Copyright

Copyright 2015 VMware, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Author Information

This role was created in 2015 by [Tom Hite / VMware](http://www.vmware.com/).
