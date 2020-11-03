FROM ubuntu:bionic

LABEL maintainer "ming.zhong@etu.unice.fr"

ENV EDITOR="emacs -nw"

ENV TZ=Asia/Shanghai

COPY emacs-27.0.91.tar.xz /root

COPY .emacs.d /root

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone && \
    apt-get update && \	     
    DEBIAN_FRONTEND=noninteractive && \
    apt-get install -y \
    tzdata \
    xz-utils \
    build-essential \
    texinfo \
    libx11-dev \
    libxpm-dev \
    libjpeg-dev \
    libpng-dev \
    libgif-dev \
    libtiff-dev \
    libgtk2.0-dev \
    libgtk-3-dev \
    libncurses-dev \
    libxpm-dev \
    automake \
    autoconf \
    gnutls-dev \
    git \
    && rm -rf /var/lib/apt/lists/*

RUN cd /root && tar xvf emacs-27.0.91.tar.xz && \
    cd emacs-27.0.91 && \
    ./configure --prefix=/opt/emacs/ --with-mailutils --with-pop && \
    make && make install && \
    ln -s /opt/emacs/bin/emacs /usr/bin/emacs && \
    cd .. && \
    rm -rf emacs-27.0.91.tar.xz emacs-27.0.91

CMD ["emacs"]

