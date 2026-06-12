---
title: "problem updating, installing or uninstalling"
date: 2011-06-19
forum: General Help
---

### Post by vivek.pandey on 2011-06-19
hey everyone whenever i am trying to update my system i get following error
```


vivek@neo:~$ sudo apt-get upgrade
[sudo] password for vivek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-28-generic-pae (2.6.35-28.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic-pae
Failed to symbolic-link boot/initrd.img-2.6.35-28-generic-pae to initrd.img: File exists
dpkg: error processing linux-image-2.6.35-28-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.35-28-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
this appears even when i am installing or uninstalling a package.. please help

---

