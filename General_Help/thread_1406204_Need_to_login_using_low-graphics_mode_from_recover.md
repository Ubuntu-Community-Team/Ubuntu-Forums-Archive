---
title: "Need to login using low-graphics mode from recovery"
date: 2010-02-13
forum: General Help
---

### Post by Xog on 2010-02-13
For reasons beyond explanation I need to use recovery mode and boot into low-graphics mode to the ubuntu desktop. I just don't know the command for it. Can anyone help me out?


+++no need for answers for below statements+++
And for any of the big-dawgs out there that deal with bigger problems, I've discovered why so many people are experiencing the "blank black screen" upon updating drivers for their video cards, specifically nvidia. Apparently when you install the driver, it doesn't look for the kernel as a dependency.

> 
After a kernel upgrade, my Ubuntu Karmic started the X server in low-resolution mode. My Xorg.0.log said:

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

I tried modprobe nvidia and such, but it seemed that the module actually did not exist. This module should be installed by the package nvidia-185-kernel-source, which was present on my system. However, it turns out that the kernel module is compiled on-the-fly by a program called jockey which controls DKMS, the Dynamic Kernel Module Support.

It is possible to force a recompile using dpkg-reconfigure:

$ sudo dpkg-reconfigure nvidia-185-kernel-source
Removing all DKMS Modules
Done.
Loading new nvidia-185.18.36 DKMS files...
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

I need the kernel source, eh? Why the hell is that not a dependency, if the driver package is useless without it? Anyway, let's install the kernel source then:

$ uname -r
2.6.31-19-generic
$ sudo apt-get install linux-source-2.6.31

Installs fine, but makes no difference. Turns out that dpkg-reconfigure was lying: I just need the headers. Here we go:

$ sudo apt-get install linux-headers-2.6.31-19-generic
...
$ sudo dpkg-reconfigure nvidia-185-kernel-source
Removing all DKMS Modules
Done.
Loading new nvidia-185.18.36 DKMS files...
Building for architecture x86_64
Building initial module for 2.6.31-19-generic
Done.

nvidia.ko:
Running module version sanity check.
- Original module
- No original module exists within this kernel
- Installation
- Installing to /lib/modules/2.6.31-19-generic/updates/dkms/

depmod......

DKMS: install Completed.
$ modprobe nvidia
$

This should fix those issues with nvidia drivers.

---

### Post by Xog on 2010-02-13
Bump.

---

### Post by Xog on 2010-02-15
Bump.

---

### Post by Xog on 2010-02-15
Bump.

---

