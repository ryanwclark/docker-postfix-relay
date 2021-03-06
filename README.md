# docker-postfix-relay

[![Docker Pulls](https://img.shields.io/docker/pulls/ryanwclark/postfix-relay.svg)](https://hub.docker.com/r/ryanwclark/postfix-relay)
[![Docker Stars](https://img.shields.io/docker/stars/ryanwclark/postfix-relay.svg)](https://hub.docker.com/r/ryanwclark/postfix-relay)


## About

Dockerfile to build a simple Postfix container designed to relay messages to an external SMTP Server

This Container uses Alpine:3.8 as a base.

[Changelog](CHANGELOG.md)

## Maintainer

- [Ryan Clark](https://github.com/ryanwclark)

## Table of Contents

- [docker-postfix-relay](#docker-postfix-relay)
  - [About](#about)
  - [Maintainer](#maintainer)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites and Assumptions](#prerequisites-and-assumptions)
  - [Installation](#installation)
    - [Quick Start](#quick-start)
  - [Configuration](#configuration)
    - [Persistent Storage](#persistent-storage)
    - [Environment Variables](#environment-variables)
  - [Maintenance](#maintenance)
    - [Shell Access](#shell-access)
  - [References](#references)

## Prerequisites and Assumptions

This image will need to connect to an external SMTP Server with User Authentication enabled.


## Installation

Automated builds of the image are available on [Registry](https://hub.docker.com/r/ryanwclark/postfix-relay) and is the recommended method of installation.


```bash
docker pull ryanwclark/postfix-relay
```

### Quick Start

* The quickest way to get started is using [docker-compose](https://docs.docker.com/compose/). See the examples folder for a working [docker-compose.yml](examples/docker-compose.yml) that can be modified for development or production use.

* Set various [environment variables](#environment-variables) to understand the capabilities of this image.
* Map [persistent storage](#data-volumes) for access to configuration and data files for backup.

## Configuration

### Persistent Storage

The following directories are used for configuration and can be mapped for persistent storage.

| Directory | Description |
|-----------|-------------|
| `/var/log` | Postfix Mail Logs |


### Environment Variables

Below is the complete list of available options that can be used to customize your installation.

| Parameter | Description |
|-----------|-------------|
| `SMTP_HOST` | The SMTP Host to forward mails to (e.g. mail.hostname.com) |
| `SMTP_USER` | The username for authentication to remote SMTP (e.g. username@hostname.com) |
| `SMTP_PASS` | The password for above username (e.g. password) |
| `SERVER_NAME` | The hostname to identify ourselves to the remote SMTP Server (e.g. yourhost.hostname.com) |
| `ACCEPTED_NETWORKS` | Who to allow access to relay (Default 172.16.0.0/12)
| `USE_TLS` | Use TLS when sending (either yes or no)
| `TLS_VERIFY` | Trust Level for checking remote cert (none, may, encrypt, dane, dane-only, 
fingerprint, verify, secure - Default may)


## Maintenance
### Shell Access

For debugging and maintenance purposes you may want access the containers shell. 

```bash
docker exec -it (whatever your container name is e.g. postfix-relay) bash
```

## References

* https://www.postfix.org


