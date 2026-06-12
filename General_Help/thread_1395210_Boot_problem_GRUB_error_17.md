---
title: "Boot problem GRUB error 17"
date: 2010-01-31
forum: General Help
---

### Post by jbarn on 2010-01-31
I installed Ubuntu to dual boot with XP. While in XP Disk Management, I managed to delete(!) the Ubuntu partition. When I restart, I get the message GRUB LOADING 1.5 and then ERROR 17.

I plan to reinstall Ubuntu, but I cannot boot into XP either at this stage because of the Grub loading error. Once in XP, I can download the Ubuntu OS again.
 Any suggestions?

---

### Post by djchandler on 2010-01-31
> **jbarn said:**
> I installed Ubuntu to dual boot with XP. While in XP Disk Management, I managed to delete(!) the Ubuntu partition. When I restart, I get the message GRUB LOADING 1.5 and then ERROR 17.

I plan to reinstall Ubuntu, but I cannot boot into XP either at this stage because of the Grub loading error. Once in XP, I can download the Ubuntu OS again.
 Any suggestions?

Boot the Ubuntu install disk and re-install Ubuntu.

The GRUB menu is stored on the Ubuntu partition in the /boot directory. When you deleted the partition, you deleted  the GRUB menu.

You can also try [Supergrub]("http://www.supergrubdisk.org/") to try and boot your system if you need/want to get into XP before re-installing Ubuntu. It should find your XP partition and let you load it. Be aware that supergrub will not work properly once you have installed GRUB2 that is used in 9.10.

Finally you can use the the XP install disk to repair XP install and your master boot record by re-installing the NT Bootloader.

---

### Post by Leppie on 2010-01-31
you should've removed ubuntu through the add/remove applet in control panel...
easiest way to restore the mbr is either with a ubuntu livecd or the windows recovery cd. if you cannot download and burn anything and you don't have either of those disks asks a friend?

---

### Post by espressobeanie on 2010-01-31
In n00blish, the LiveCD is also the AlternateCD. 

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

