# Fleet Telemetry Helm Chart 
* Installs the fleet-telemetry system. [fleet-telemetry](https://github.com/teslamotors/fleet-telemetry)
## Get Repo Info
```console
helm repo add teslamotors https://teslamotors.github.io/helm-charts/
helm repo update
```
_See [helm repo](https://helm.sh/docs/helm/helm_repo/) for command documentation._

## Installing the Chart

To install the chart with the release name `fleet-telemetry`:

```console
helm install fleet-telemetry charts/fleet-telemetry -n fleet-telemetry
```

## Uninstalling the Chart

To uninstall/delete the fleet-telemetry deployment:

```console
helm uninstall fleet-telemetry -n fleet-telemetry
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

## Upgrade the Chart
To upgrade the chart with the release name `fleet-telemetry`:
```console
helm upgrade fleet-telemetry charts/fleet-telemetry -n fleet-telemetry
```

## Configuration
| Parameter             | Description                                                                         | Default                 |
|-----------------------|-------------------------------------------------------------------------------------|-------------------------|
| `tlsSecret.name`      | Name of existing secret, if this value is set `tlsCrt` and `tlsKey` will be ignored | `nil`                   |
| `tlsSecret.tlsCrt`    | value of the certification                                                          | `nil`                   |
| `tlsSecret.tlsKey`    | value of the encryption key                                                         | `nil`                   |
| `image.repository`    | value of the docker image repo                                                      | `tesla/fleet-telemetry` |
| `image.tag`           | value of the docker image tag                                                       | `v0.0.3`                |
| `resources`           | CPU/Memory resource requests/limits                                                 | {}                      |
| `nodeSelector`        | Node labels for pod assignment                                                      | {}                      |
| `tolerations`         | Toleration labels for pod assignment                                                | {}                      |
| `replicas`            | Number of pods                                                                      | `1`                     |
| `service.annotations` | Service Annotations                                                                 | {}                      |
| `service.type`        | Service Type                                                                        | ClusterIP               |

## Example
service:
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-type: "internal"
    service.beta.kubernetes.io/aws-load-balancer-nlb-target-type: "ip"
    service.beta.kubernetes.io/aws-load-balancer-subnets: subnet-8e0d7ff8, subnet-5d7b2139, subnet-1327954b
  type: LoadBalancer
tlsSecret:
  tlsCrt: |
    value of the cert PEM
  tlsKey: |
    value the private key
