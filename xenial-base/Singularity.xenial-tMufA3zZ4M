# Last modified 20 December 2018 by Robert Nicholas <ren10@psu.edu>.

BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://us.archive.ubuntu.com/ubuntu/


%runscript

    exec /bin/bash "$@"


%post

    # fix package sources
    echo "deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse" > /etc/apt/sources.list
    echo "deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse" >> /etc/apt/sources.list
    echo "deb http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse" >> /etc/apt/sources.list
    echo "deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse" >> /etc/apt/sources.list

    # upgrade packages in base image
    DEBIAN_FRONTEND=noninteractive apt-get update && apt-get -y dist-upgrade
    DEBIAN_FRONTEND=noninteractive apt-get -y install joe mc htop fish

    # create a few ACI-specific directories within the container
    mkdir -p /storage/home
    mkdir -p /storage/work
    mkdir -p /gpfs/group
    mkdir -p /gpfs/scratch
    mkdir -p /var/spool/torque

