ARG DOCKER_REGISTRY=public.aml-repo.cms.waikato.ac.nz:443/
FROM ${DOCKER_REGISTRY}ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
       git-core \
       wget \
       python3 \
       python3-dev \
       python3-venv \
       python3-pip \
       python3-pandas \
       python3-chardet \
       python3-full \
       build-essential \
       libglib2.0-0 \
       libsm6 \
       libxrender-dev \
       libxext6 \
       libgl1 \
       libglx-mesa0 \
       libpq-dev && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m venv /opt/image-dataset-converter && \
    /opt/image-dataset-converter/bin/pip --no-cache-dir install \
        image_dataset_converter_all==0.0.12

ENV PATH=/opt/image-dataset-converter/bin:$PATH
ENV NUMBA_CACHE_DIR=/tmp
ENV MPLCONFIGDIR=/tmp
COPY bash.bashrc /etc/bash.bashrc
WORKDIR /workspace
