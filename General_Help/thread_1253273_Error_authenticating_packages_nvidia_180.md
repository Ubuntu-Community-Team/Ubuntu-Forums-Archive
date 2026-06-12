---
title: "Error authenticating packages nvidia 180"
date: 2009-08-29
forum: General Help
---

### Post by kachofool on 2009-08-29
Hey all,

I'm trying to run updates (am on 8.10, want to upg to 9.04). Initially just trying to run all default updates, I get a prompt saying only partial updates can be done. When I try to run partial updates, almost immediately I get an "Error authenticating some packages" message. The packages listed are:

nvidia-180-kernel-source
nvidia-180-libvdpau
nvidia-180-modaliases
nvidia-glx-180
nvidia-glx-180-dev

I don't know how to get around this issue. I'd appreciate any help.

---

### Post by 3rdalbum on 2009-08-29
Try going to the website for the repository that you've added. (the one with the Nvidia drivers). Find the GPG key for the repository and add it.

---

