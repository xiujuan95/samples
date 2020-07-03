FROM registry.access.redhat.com/ubi8-minimal

ARG cnb_uid=1000
ARG cnb_gid=1000

# Install packages that we want to make available at both build and run time
RUN microdnf install -y yum
RUN yum install -y libicu
RUN microdnf -y update
RUN microdnf -y --nodocs install gcc
RUN microdnf install -y git
#RUN yum install devtoolset-9-toolchain
#RUN apk update && apk add
#RUN apt-get update && \
#  apt-get install -y xz-utils ca-certificates && \
#  rm -rf /var/lib/apt/lists/*

# Create user and group
RUN groupadd cnb --gid ${cnb_gid} && \
  useradd --uid ${cnb_uid} --gid ${cnb_gid} -m -s /bin/bash cnb

# Set required CNB information
ENV CNB_USER_ID=${cnb_uid}
ENV CNB_GROUP_ID=${cnb_gid}
