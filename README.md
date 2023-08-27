ansible-k2d
=========

This role will help you to setup / install [k2d](https://k2d.io/) on your system.

K2d is a ultra lightweight solution to emulate a Kubernetes cluster from within a docker
container. It's mainly ment for small or "edge" host systems.

This role only manages the k2d container itself. If you have deployed workload on your
k2d, even recreating the k2d setup with this role, will keep the deployed workload running.

Requirements
------------

 - Ansible 2.7 or higher.
 - ansible-k2d will only work on Debian OS family (Debian, Ubuntu, Raspberry Pi OS...) as for now.

All required software for k2d will be installed using this role. You don't need to install
software manually. For instance, Docker is needed and will be installed.

Role Variables
--------------

## Optional variables

| Variable Name      | Description                                                                            | Default value               |
| ------------------ | -------------------------------------------------------------------------------------- | --------------------------- |
| k2d_container_name | Container name of k2d                                                                  | `k2d`                       |
| k2d_server_ip      | Should be the IP of your Docker host. This parameter is mandatory to be set.           | `empty`                     |
| k2d_secret         | Secret to retrieve Kubeconfig after k2d is running                                     | `Supersecret`               |
| k2d_image          | Which image and image version should be used by this playbook to deploy the container. | `portainer/k2d:1.0.0-alpha` |

Dependencies
------------

None.

Example Playbook
----------------

You can find an example playbook in this repository as `ansible-k2d.yml`. Here are some
examples in calling this playbook:

    - ansible-playbook ansible-k2d.yml -e "HOSTS=myraspberry" -e "k2d_server_ip=192.168.2.15 k2d_image=portainer/k2d:1.0.0-alpha" -k -K -u <username>

License
-------

GPL 3.0

Author Information
------------------

ansible-k2d was created by Philip Haberkern (thedatabaseme).