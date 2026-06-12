---
title: "Can't create bootable usb drive"
date: 2012-09-27
forum: General Help
---

### Post by ryanyeah on 2012-09-27
So I've been trying to create a bootable copy of gparted ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)). This is driving me crazy but I don't know what I'm doing wrong. As root, I execute dd if=/location/of/iso of=/dev/sdx and it seems to copy all the files to the usb and it yet whenever I try and boot from the usb, my computer fails to boot from it and just boots from whatever is next in the boot priority order. Any ideas? Does the format of the drive matter before I do the dd?

---

### Post by jingaling on 2012-09-27
Create an Ubuntu live USB pen with persistence and install Gparted in there. If fact, doesn't Ubuntu have Gparted installed by default?

If that's the case then just create an Ubuntu live USB pen. Job done.


Kev

---

### Post by C.S.Cameron on 2012-09-27
MultiBootUSB can be used to make a bootable gparted flash drive.

---

### Post by z5um on 2012-09-27
You don't need to make a bootable device for using gparted. Type 
```
sudo apt-get install gparted
``` into your shell and then run it with```
sudo gparted
```

---

### Post by oldfred on 2012-09-27
I do not know if gparted is a hybrid install that can be installed with dd. Only since Oneriric has Ubuntu been a hybrid.

The daily ISOs for the Ubuntu Oneiric development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs.
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

---

### Post by Abhinav Kumar on 2012-10-28
Try unetbootin. Starts after giving root password

---

### Post by cwsnyder on 2012-10-28
I have noted Problems with some individual (especially inexpensive) flash devices being unable to be prepared to boot.  I don't know if it is a fault in the flash drive?  I have had best luck with PNY drives.

---

