---
title: "Patching Question &amp; Help"
date: 2009-08-25
forum: General Help
---

### Post by Saprissa on 2009-08-25
Hola everyone!

I am trying to follow a tutorial  from linuxtv.org that involves patching a file, but the patching fails.

The tutorial is located here:
[http://www.linuxtv.org/wiki/index.php/Trident_TM6000#TM6000_based_Devices](http://www.linuxtv.org/wiki/index.php/Trident_TM6000#TM6000_based_Devices)

> Step 1: Clone a v4l-dvb tree in a directory of your choice

$hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Step 2: Apply the Makefile patch to the tree (which allows to build the driver later on)

$ cd v4l-dvb
$ wget [http://colabti.de/~feb/tm6000-makefile-dvb-tree.patch]("http://colabti.de/%7Efeb/tm6000-makefile-dvb-tree.patch")
$ patch -p1 < tm6000-makefile-dvb-tree.patch

Step 3: Download the driver and extract it

$ cd linux/drivers/media/video/
$ wget [http://colabti.de/tm6000/tm6000.tar.gz](http://colabti.de/tm6000/tm6000.tar.gz)
$ tar xvzf tm6000.tar.gz

Step 4: Compile everything

$ cd ../../../../
$ make

Step 5: Install everything

$ su -c "make install"

Step 6: Remove all the V4L/DVB modules that are currently loaded (or alternatively reboot the system) and load the driver module

$ su -c "make rmmod; /sbin/modprobe tm6000"
When I execute the patch command I get the following:

```
patching file linux/drivers/media/video/Kconfig
Hunk #1 succeeded at 910 with fuzz 2 (offset 214 lines).
patching file linux/drivers/media/video/Makefile
Hunk #1 FAILED at 67.
1 out of 1 hunk FAILED -- saving rejects to file linux/drivers/media/video/Makefile.rej
```I think there might be a typo in the tutorial that causes the command to try to patch the wrong file, but I am too inexperienced to understand what file I need to actually patch.

Thanks so much for your help.

---

### Post by Kilbur on 2009-11-12
Sorry for my English, I'm Italian! 
 I have the exact same problem, I do not know how to solve! I'm trying in every way! 
 Hopefully soon someone will give us an idea!

---

### Post by samuelhug on 2009-11-12
Try inserting in linux/drivers/media/video/Makefile

```
obj-m += tm6000/
```

on line 101 right after

```
obj-$(CONFIG_VIDEO_EM28XX) += em28xx/
```

and before

```
obj-$(CONFIG_VIDEO_CX231XX) += cx231xx/
```

then continue with the tutorial

---

### Post by brus46 on 2009-11-17
This doesn't work for me :( same error with the same usb receiver :(

---

