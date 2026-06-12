---
title: "Error when upgrading"
date: 2006-04-21
forum: General Help
---

### Post by shmk on 2006-04-21
When I'm trying to upgrade thorugh ubuntuupdatemanager, synaptic or apt I'll get this error.

> 
Preconfiguring packages ...
(Reading database ... 91464 files and directories currently installed.)
Preparing to replace nvidia-kernel-common 1.0.7174+1 (using .../nvidia-kernel-common_1.0.7174+1_all.deb) ...
Error: the current /etc/modules.conf is not automatically generated.
Use "update-modules force" to force (re)generation.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Error: the current /etc/modules.conf is not automatically generated.
Use "update-modules force" to force (re)generation.
dpkg: error processing /var/cache/apt/archives/nvidia-kernel-common_1.0.7174+1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Error: the current /etc/modules.conf is not automatically generated.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace evms 2.5.1-1ubuntu4 (using .../evms_2.5.1-1ubuntu4.1_i386.deb) ...
Unpacking replacement evms ...
Error: the current /etc/modules.conf is not automatically generated.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Error: the current /etc/modules.conf is not automatically generated.
dpkg: error processing /var/cache/apt/archives/evms_2.5.1-1ubuntu4.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Error: the current /etc/modules.conf is not automatically generated.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-kernel-common_1.0.7174+1_all.deb
 /var/cache/apt/archives/evms_2.5.1-1ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone give me a hand ?:-k

---

### Post by shmk on 2006-04-21
After I restart my ubuntu X doesn't start because it can't find nvidia drivers no more.
I changed in xorg.conf "nvidia" to "vesa" and after X starts, but obviously my nvidia drivers aren't installed correctly :(

This error is linked with the one before ? (I think "yes", because before that upgrade all was fine...)

---

