# Echo-Server / Docker / Kubernetes / Helm

[![Codecov](https://img.shields.io/codecov/c/github/ealenn/echo-server?style=for-the-badge&logo=codecov)](https://codecov.io/gh/Ealenn/Echo-Server)
[![GitHub stars](https://img.shields.io/github/stars/Ealenn/Echo-Server?style=for-the-badge&logo=github)](https://github.com/Ealenn/Echo-Server/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/Ealenn/Echo-Server?style=for-the-badge&logo=github)](https://github.com/Ealenn/Echo-Server/issues)
[![DockerHub](https://img.shields.io/docker/pulls/ealen/echo-server.svg?style=for-the-badge&logo=docker)](https://hub.docker.com/repository/docker/ealen/echo-server)
[![DockerHub](https://img.shields.io/badge/SIZE-%3C%2013%20MB-1488C6?style=for-the-badge&logo=docker)](https://hub.docker.com/repository/docker/ealen/echo-server)

> Read the docs : [https://ealenn.github.io/Echo-Server](https://ealenn.github.io/Echo-Server) - Read the [release notes](https://github.com/Ealenn/Echo-Server/releases)

An echo server is a server that replicates the request sent by the client and sends it back.

More information [Project Repository](https://github.com/Ealenn/Echo-Server)

## Adding the Repository

```bash
helm repo add ealenn https://ealenn.github.io/charts
helm repo update
```

## Deploy Echo-Server with helm

```bash
helm upgrade -i ${name} ealenn/echo-server --namespace ${namespace} --force
```

## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| application.enable.environment | bool | `true` | Enable environment in response |
| application.enable.file | bool | `true` | Enable file in response |
| application.enable.host | bool | `true` | Enable request in response |
| application.enable.http | bool | `true` |  |
| application.enable.request | bool | `true` |  |
| application.logs.ignore.ping | bool | `false` | Don't log ping request on route `/ping` |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ealen/echo-server"` | https://hub.docker.com/r/ealen/echo-server |
| image.tag | string | `"0.4.0"` | https://github.com/Ealenn/Echo-Server/releases |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` | Example `kubernetes.io/ingress.class: nginx` for Nginx Ingress |
| ingress.enabled | bool | `false` | Enable ingress |
| ingress.hosts[0].host | string | `"cluster.local"` |  |
| ingress.hosts[0].paths[0] | string | `"/"` |  |
| ingress.tls | list | `[]` |  |
| livenessProbe.failureThreshold | int | `3` |  |
| livenessProbe.httpGet.httpHeaders[0].name | string | `"X-ECHO-CODE"` |  |
| livenessProbe.httpGet.httpHeaders[0].value | string | `"200"` |  |
| livenessProbe.httpGet.path | string | `"/ping"` |  |
| livenessProbe.initialDelaySeconds | int | `5` |  |
| livenessProbe.periodSeconds | int | `10` |  |
| livenessProbe.successThreshold | int | `1` |  |
| livenessProbe.timeoutSeconds | int | `2` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` | Pod replicas |
| resources.limits.cpu | string | `"50m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"50m"` |  |
| resources.requests.memory | string | `"128Mi"` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `nil` |  |
| tolerations | list | `[]` |  |

## Changelog

### 0.3.0

- App Version [0.4.0](https://github.com/Ealenn/Echo-Server/releases/tag/0.4.0)
- Fix Header `X-ECHO-CODE`

### 0.2.2

- Fix invalid values in liveness probe
- Default liveness value Header `ECHO_CODE` on `/ping` -> HTTP 200 

### 0.2.1

- Customize liveness probe
- Automatically Roll Deployments
- Increased default memory allocation

### 0.2.0

- App Version [0.3.0](https://github.com/Ealenn/Echo-Server/releases/tag/0.3.0)
- Additional Documentation
