FROM golang

#
# BEGIN: CONTAINERD IN DOCKER
#

RUN go get github.com/opencontainers/runc v1.0.0-rc92

RUN apt-get update && \
  apt-get install -y libbtrfs-dev libseccomp-dev

# Mount containerd and runc
RUN -it --privileged \
  -v /var/lib/containerd \
  -v ${GOPATH}/src/github.com/opencontainers/runc:/go/src/github.com/opencontainers/runc \
  -v ${GOPATH}/src/github.com/containerd/containerd:/go/src/github.com/containerd/containerd \
  -e GOPATH=/go \
  -w /go/src/github.com/containerd/containerd containerd/build sh



