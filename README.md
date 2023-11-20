
# IPsec VPN Server on Docker

 根据 hwdsl2/ipsec-vpn-server 的源代码构建镜像， 所有运行参数都可以以原作者的为准。
 本代码仅更新了支持TP-link的加密方式，方便对接TP-Link路由器

 --感谢原作者hwdsl2
 
## Quick start

Use this command to set up an IPsec VPN server on Docker:

```
docker run \
    --name ipsec-vpn-server \
    --restart=always \
    -v ikev2-vpn-data:/etc/ipsec.d \
    -v /lib/modules:/lib/modules:ro \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -d --privileged \
    hwdsl2/ipsec-vpn-server
```

Your VPN login details will be randomly generated. See [Retrieve VPN login details](#retrieve-vpn-login-details).

To learn more about how to use this image, read the sections below.
 
## Download

Get the trusted build from the [Docker Hub registry](https://hub.docker.com/r/hwdsl2/ipsec-vpn-server/):

```
docker pull hwdsl2/ipsec-vpn-server
```

Alternatively, you may download from [Quay.io](https://quay.io/repository/hwdsl2/ipsec-vpn-server):

```
docker pull quay.io/hwdsl2/ipsec-vpn-server
docker image tag quay.io/hwdsl2/ipsec-vpn-server hwdsl2/ipsec-vpn-server
```

Supported platforms: `linux/amd64`, `linux/arm64` and `linux/arm/v7`.

Advanced users can [build from source code](docs/advanced-usage.md#build-from-source-code) on GitHub.

### Image comparison

Two pre-built images are available. The default Alpine-based image is only ~17MB.

|                   | Alpine-based             | Debian-based                   |
| ----------------- | ------------------------ | ------------------------------ |
| Image name        | hwdsl2/ipsec-vpn-server  | hwdsl2/ipsec-vpn-server:debian |
| Compressed size   | ~ 17 MB                  | ~ 63 MB                        |
| Base image        | Alpine Linux 3.18        | Debian Linux 12                |
| Platforms         | amd64, arm64, arm/v7     | amd64, arm64, arm/v7           |
| Libreswan version | 4.12                     | 4.12                           |
| IPsec/L2TP        | ✅                       | ✅                              |
| Cisco IPsec       | ✅                       | ✅                              |
| IKEv2             | ✅                       | ✅                              |

 
