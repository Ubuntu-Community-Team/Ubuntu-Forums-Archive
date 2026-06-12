---
title: "Touchscreen Driver / ATI Driver problem, Quanta Inc Touchscreen"
date: 2010-07-11
forum: General Help
---

### Post by Excurion on 2010-07-11
Hey guys,

I've recently bought the Medion MD 20165 screen, which is a multitouchscreen.

The touchoverlay this screen packs is from Quanta Inc, and has the usb-id 0408:3000.
According to my research, this multitouchscreen doesn't work in the current ubuntu 10.04
kernel (2.6.32) because the quanta-driver in it is outdated.

I've also found out that the newer kernel, 2.6.35, does have the correct driver in it, and my
touchscreen works fine when using this kernel. The downside however is, with the 2.6.35
kernel, I can't install the ati catalyst driver for my ATI Radeon HD 5700 graphics-card.

If anyone could provide me with any help solving this, that would be very much appreciated.

So my question is,could anyone help me find the way how to patch the drivers in the kernel.

Further information would be:
```

Bus 002 Device 006: ID 0408:3000 Quanta Computer, Inc

01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
```

> **Excurion said:**
> Ok, I figured this out:









From: [http://lii-enac.fr/en/projects/shareit/linux-howto.html](http://lii-enac.fr/en/projects/shareit/linux-howto.html)

Don't understand how to properly do these steps though. There is no  hid-core.h and no hid-ids.h as far as I've seen. I just need the headers  of the current kernel (2.6.32) right?

Could someone elaborate on the steps, so that I have a better  understanding of what they do.

---

### Post by Woody1987 on 2010-07-11
You will not be able to install fglrx on this kernel. ATI are VERY slow at supporting new kernels, and i highly doubt a working driver will be made available until 10.10 is released.

---

### Post by Excurion on 2010-07-11
So you think it's best to just stick to the 2.6.32 kernel? Could you perhaps help me find out how to patch this quanta touchscreen driver?

---

### Post by Excurion on 2010-07-11
Ok, I figured this out:

> **General procedure: ** have a source tree of your Linux kernel, ready for recompiling  modules in it. As we'll have to make changes in the hid subsystem, you might want  to make sure that hid is compiled as a module and not a static part of the  kernel. In the following, '/' means the root of your source tree and '//' the root of your file system. 
in /include/linux/hid.h, change the end of the macro  IS_INPUT_APPLICATION to (a >= 0xd0002 && a <= 0xd0006). 
in a recent hid-core.c (see [here]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/hid/hid-core.c")), take  the lines that refer to your hardware (check for MOSART, QUANTA, STANTUM or 3M) and put them in /drivers/hid/hid-core.c, replacing lines if necessary. 
same in hid-ids.h 
put the hid-{yourpanel}.c file in /drivers/hid/ 
in drivers/hid/Makefile add a line obj-m += hid-{yourpanel}.o 
make sure that /Module.symvers exists. Otherwise, the only  solution we found is to compile the whole kernel and have the file produced during the  process. 
in /drivers/hid, 'make -C ../.. SUBDIRS=`pwd` modules' 
copy the files hid-{yourpanel}.ko and hid.ko into your OS  modules, that is in //lib/modules/2.6.xxx/kernel/drivers/hid. If you don't have hid.ko,  this means that hid is not configured as a module but as a static part of the  kernel; you will need to change this or compile and install the whole kernel. 
 load the new module hid-{yourpanel}.ko for the first time: insmod /lib/modules/2.6.xxx/kernel/drivers/hid/hid-{yourpanel}.ko 
 re-load the modules each time you modify and compile them. For  this, you need to unload them (rmmod hid-{yourpanel}, for instance) then reload  them (modprobe hid-{yourpanel}). You need to do it at least once for hid; for  this, you need to unload all modules that use it ('rmmod hid-{yourpanel}  usbhid hid') then load them again ('modprobe hid', 'modprobe usbhid', 'modprobe  hid-mosart').


> **Ubuntu 10.04 procedure:** The kernel in Ubuntu 10.04 is a 2.6.32 with some added suport for  multitouch. Basically, what was added is the set of drivers that was available in  2.6.34-rc1; what is missing is the patch to the hid module and the more recent  drivers (cando, egalax). Therefore you need to: 
grab the sources of your kernel 
modify hid.h and recompile/install the hid module  as described  in the general procedure at the top of this page, 
if your device is cando-based or egalax-based, obtain the  sources of the driver and compile/install it as described in the general procedure (modification  in hid-core.c and hid-ids.h, etc) 


> 
**Stantum, 3M, MosArt and Quanta: ** The drivers are included in the upstream kernel since version 2.6.34. If you are using an earlier version you have to download the drivers and  apply the procedure.

From: [http://lii-enac.fr/en/projects/shareit/linux-howto.html](http://lii-enac.fr/en/projects/shareit/linux-howto.html)

Don't understand how to properly do these steps though. There is no hid-core.h and no hid-ids.h as far as I've seen. I just need the headers of the current kernel (2.6.32) right?

Could someone elaborate on the steps, so that I have a better understanding of what they do.

---

