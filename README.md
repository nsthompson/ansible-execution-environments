# ansible-execution-environments

This repo contains execution and decision environment definitions and dependencies for the Ansible Automation Platform.

## Execution Environments

| Name | Description |
|-|-|
| k8s-ee | EE with suppport for Kubernetes and Openshift |
| meraki-ee | EE with support for Certified Meraki Collection |
| wwt-de | Event-Driven Ansible DE with support for wwt.eda Collection |

## Building an Execution Environment

1. Log in to the Red Hat Registry so you can pull the required base instances

    ```shell
    podman login -u=<username> -p=<token/hash> registry.redhat.io
    ```

2. Pull the base image as defined in the `execution-environment.yml` file.

    ```shell
    podman pull registry.redhat.io/<image-name>:<image-tag>
    ```

3. Change into the directory of the EE you want to build

    ```shell
    cd <ee-directory>
    ```

4. Build the EE

    ```shell
    ansible-builder build --tag=<automation-hub-hostname>/<ee-name>
    ```

5. Log in to your automation hub instance

    ```shell
    podman login --tls-verify=false -u=<username> -p=<password> <automation-hub-hostname>
    ```

6. Push EE to your automation hub

    ```shell
    podman push <automation-hub-hostname>/<ee-name>
    ```

## Contributors

Nick Thompson <<https://github.com/nsthompson>>
