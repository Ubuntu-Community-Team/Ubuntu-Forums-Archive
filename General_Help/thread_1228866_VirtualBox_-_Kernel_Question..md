---
title: "VirtualBox - Kernel Question."
date: 2009-08-01
forum: General Help
---

### Post by Roasted on 2009-08-01
Do you guys find yourselves getting the "VirtualBox - Error" telling you to:


```
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

I get this every now and then. I just got it now while I had ran this command about 3 weeks ago. *shrug*

---

### Post by kpkeerthi on 2009-08-01
This might happen if there was a kernel upgrade. The vbox kernel driver need to be recompiled for the new kernel. You may install **dkms** if you want this done automatically.

---

### Post by Roasted on 2009-08-01
Bingo. I just got the updated kernel for Ubuntu the other day. It seems just like yesterday I had to do this though...

---

