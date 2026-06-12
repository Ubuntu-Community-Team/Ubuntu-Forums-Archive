---
title: "Nvidia drivers and kernel"
date: 2005-03-11
forum: General Help
---

### Post by stenbock on 2005-03-11
I did compile a new kernel and I can boot. The only problem is the nvidia drivers, the kernel wont boot the drivers. The question is what to do:

 1. Is there a way to build the nvidia drivers into the kernel
 2. What should i do the get the nvidia drivers to work.

I did download the drivers throug apt-get

---

### Post by Tichondrius on 2005-03-11
[QUOTE=stenbock]I did compile a new kernel and I can boot. The only problem is the nvidia drivers, the kernel wont boot the drivers. The question is what to do:

 1. Is there a way to build the nvidia drivers into the kernel
 2. What should i do the get the nvidia drivers to work.

I did download the drivers throug apt-get[/QUOTE]

you need to copy the kernel module from your old kernel into the new kernel. If the kernel version is not significantly different between the old and new kernels, then it should work.

for example, if the old version is 2.6.8.1 and new version is 2.6.10.1 then do this (you can see the current kernel version by typing the command 'uname -r') :

To find the old module:

$ cd /lib/modules
$ find  2.6.8.1 -name nvidia.ko

Then copy it into the new kernel:
$ sudo cp 2.6.8.1/kernel/drivers/video/nvidia.ko 2.6.10.1/kernel/drivers/video
$ sudo depmod 2.6.10.1

reboot

---

### Post by stenbock on 2005-03-11
Thanks for the fast help, running the new kernel  :smile:

---

