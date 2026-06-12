---
title: "Problem compiling drivers against new kernel"
date: 2012-04-29
forum: General Help
---

### Post by someitalian123 on 2012-04-29
I can't compile the driver for my wlan card that uses the rt3062 chipset. I have the build essential installed as well as the headers but for some reason I can't compile drivers against new kernels. 

```
root@upstairs:/home/antoniu/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
make -C tools
make[1]: Entering directory `/home/antoniu/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/antoniu/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/antoniu/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/antoniu/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/antoniu/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [LINUX] Error 2

```

This isn't even the only driver that's failing to compile. I got an error from synaptic when trying to install the 32-bit kernel in hopes that the pae kernel may have been the problem. It was posted automatically to launchpad

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/990912]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/990912")

```
DKMS make.log for virtualbox-4.1.12 for kernel 3.2.0-24-generic (i686)
Sun Apr 29 01:09:58 EDT 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make: Makefile: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
make: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
```

---

