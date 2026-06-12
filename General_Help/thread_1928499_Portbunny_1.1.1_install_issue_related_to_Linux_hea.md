---
title: "Portbunny 1.1.1 install issue related to Linux headers"
date: 2012-02-20
forum: General Help
---

### Post by shayno90 on 2012-02-20
Ran into an installation issue during the 'make' stage of the installation:

root@user:/home/user/PortBunny-1.1.1# make
make -C /lib/modules/2.6.32-35-generic/build M=/home/user/PortBunny-1.1.1 modules
make[1]: leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
  CC [M]  /home/user/PortBunny-1.1.1/scanner_module.o
In file included from /home/user/PortBunny-1.1.1/scanner_module.c:76:
/home/user/PortBunny-1.1.1/scan_job_manager.h:5:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/home/user/PortBunny-1.1.1/scanner_module.o] Error 1
make[1]: *** [_module_/home/user/PortBunny-1.1.1] Error 2
make[1]: leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
make: *** [all] Error 2

Applied the patch below but no change and the same result as above:

user@user:~$ patch -Np1 -d PortBunny-1.1.1 < portbunny-noui.diff 
patching file UI/share/portbunny/PBunnyOptionParser.py
patching file UI/share/portbunny/UILogic.py
patching file UI/share/portbunny/UserEventHandler.py

How can I correct the Linux headers or Portbunny package in order to compile and install it correctly?

---

### Post by shayno90 on 2012-02-22
The file semaphore.h is not in the appropriate install directory, it is located in  /usr/src/linux-headers-2.6.32-35-generic/include/linux instead of  /usr/src/linux-headers-2.6.32-35-generic/include/asm-generic.

In later kernels "semaphore.h" was moved to .../include/linux instead of asm

I managed to compile and install this version of Portbunny050109:

[http://portbunny.recurity.com/tarbal...109-dev.tar.gz]("http://portbunny.recurity.com/tarballs/PortBunny050109-dev.tar.gz")

I had to install 2 patches to properly compile and install it:

[http://git.server-speed.net/aur/tree...7610e4c1c85946]("http://git.server-speed.net/aur/tree/portbunny?id=545b0b7de32c86264d4ec1eb7b7610e4c1c85946")

The patches that need to be added are:

1. installpath.patch
2. timespec.patch

I will try at some stage to compile and install Portbunny-1.1.1 by creating the directory and adding a symlink.

---

