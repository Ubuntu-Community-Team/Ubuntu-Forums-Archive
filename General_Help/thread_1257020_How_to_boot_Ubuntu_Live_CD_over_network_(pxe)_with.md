---
title: "How to boot Ubuntu Live CD over network (pxe) without nfs (storage on  USB key)"
date: 2009-09-03
forum: General Help
---

### Post by neilsanner on 2009-09-03
Hi,

I have a laptop with : 
-Broken dvd drive
-No floppy
-USB booting not possible

It can boot via network/pxe.

Is there a way to boot the live Ubuntu on there? 
I don't want to install Ubuntu. I want to use live Ubuntu as a rescue tool.
I would prefer not setting up a NFS. I would like to put all the CD files on a USB key. The network tftp server would be used to initiate the booting process. Then the files would be accessed from the USB drive.

Any ideas of the steps to boot live Ubuntu over the network?

---

### Post by ppatrick on 2013-03-05
you can do it with Serva and an Ethernet cable
read here
[http://vercot.com/~serva/an/NonWindowsPXE3.html](http://vercot.com/~serva/an/NonWindowsPXE3.html)

---

### Post by Cheesemill on 2013-03-05
If you set up [Plop]("http://www.plop.at/en/bootmanagers.html") to boot from the network via PXE, you could then use it to boot your system from a USB stick.

---

### Post by wildmanne39 on 2013-03-05
Old thread closed!

---

