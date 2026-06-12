---
title: "Why is there an AGPGart module for my PCI card?"
date: 2009-08-30
forum: General Help
---

### Post by madu on 2009-08-30
Hello,

Maybe I have got this all wrong but I have had problems with my vid card.
Right now the problem has come to not loading GLX module.

When I run lsmod I get these entries:
> @desktop:~# lsmod | grep nvidia
nvidia               7233116  20 
agpgart                42696  2 nvidia,intel_agp


Wiki says AGPgart is related to AGP vid cards. I have a PCI-e 2.0 Nvidia GTX-260 card. Is there something really wrong here or this is normal?

Also my nvidia modules are as follows:
> @desktop:~# find /lib/modules/2.6.28-15-generic/  -name *nvidia*ko
/lib/modules/2.6.28-15-generic/updates/dkms/nvidia.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/video/nvidia/nvidiafb.ko


Also
> root@desktop:~# find /lib/modules/2.6.28-15-generic/  -name *glx*ko
root@desktop:~# 

There are no glx modules there.

But 
> root@desktop:~# find /usr/lib/xorg/modules/ -name *glx*
/usr/lib/xorg/modules/extensions/libglx.so.180.60
/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/xorg/modules/extensions/libglx.so.180.44
/usr/lib/xorg/modules/libglx.so


The problem I have is, why is the GLX module has a .SO extension because I think with the newer lernels it should be .KO extension.

Anybody has any idea what is happening?

Cheers.

---

### Post by Liolikas on 2009-08-30
You mess too much somehow. 
It should be just install proprietary drivers and relogin.

---

### Post by madu on 2009-08-30
> **Liolikas said:**
> You mess too much somehow. 
It should be just install proprietary drivers and relogin.

Thanks mate.

But has done it half a dozen times.. literally.. 

The question I posted before here: 
[http://ubuntuforums.org/showthread.php?t=1250716](http://ubuntuforums.org/showthread.php?t=1250716)

---

### Post by Liolikas on 2009-08-30
I had 2 PC with Linux nvidia and never problems...
Read here:
[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)

Try Build manually, with a custom kernel if nothing helps.

---

### Post by gsocker on 2009-08-30
You're confusing the GLX library(userspace code)  with the kernel modules. GLX is part of X Windows, not the kernel.

---

