+++
title = "What is container?"
description = "Deep dive into container virtualization"
tags = [
    "linux",
    "docker",
    "kubernetes",
    "container",
]
date = "2021-11-20"
categories = [
    "DevOps",
    "container",
]
menu = "main"
+++

What’s the container? Is it a VM? or a lightweight VM? Actually, containers aren't VM or lightweight VM. ontainer is just a process in a Linux machine like many other processes; however when we start to work with it, it feels like a VM.

Containers were implemented using three old features on the Linux kernel.

- Namespace
- Cgroup
- Copy on Write

The Namespace referenced here is not the Kubernetes Namespace. I hope that you don’t get yourself confused with both. Linux namespace is way more complicated than Kubernetes namespaces. Containers need many kinds of namespaces on the Linux kernel. Basically, it creates a new namespace of the whole current stack.

Cgroup is used to limit resources, account for resource usage of resources, and protect the host system from out of resources. The Linux kernel provides several kinds of groups like namespaces. Metrics provided by Docker and Kubernetes are a result of this cgroups.

I believe you had previous experience with mounting like partition mounting. Mounting is a feature of copy-on-write. Container runtime like Docker uses mounting rather than copying.

If you are really good at scripting you can do a container runtime within a few 100s of lines. However, it’s not an easy for everyone and it’s not portable and scalable. Docker uses an [Overlay file system](https://docs.docker.com/storage/storagedriver/overlayfs-driver/) to store images and it works in a rsync way that is why it's highly portable, less time-consuming and a scalable approach.
