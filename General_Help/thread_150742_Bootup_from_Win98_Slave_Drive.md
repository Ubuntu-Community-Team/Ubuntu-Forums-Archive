---
title: "Bootup from Win98 Slave Drive"
date: 2006-03-26
forum: General Help
---

### Post by fishmorg909 on 2006-03-26
I just got a 40GB Maxtor hard drive set up as a slave drive, and got Ubuntu to mount it perfectly (thanks to search for help on these threads). But I can't figure out how to bootup from it -- it has Win98 on it, and while I can find everything on it with Ubuntu, I want to run it and see if there's anything I can use. Looked at CMOS at setup, but that doesn't do it. 

I've been looking around here, and I apparently have to tell GRUB something... can't quite find what or how, though.

(edit) By the way, the new (slave) HDD has 2 partitions. cat /etc/fstab shows this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/hdb5 /media/hdb5 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

I keep finding instructions on how to setup i GRUB, but they all seem to refer to partitions on the same disk.

---

### Post by Sutekh on 2006-03-26
[quote=fishmorg909]
I keep finding instructions on how to setup i GRUB, but they all seem to refer to partitions on the same disk.[/quote]

You can modify those commands to meet your needs

Which partition is Windows 98 on?  hdb1? or hdb5?  In these instructions I'm going to asume that its hdb1.


First make a backup of the GRUB menu and device map, in case this doesn't work (makes it easier to undo changes)
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo cp /boot/grub/device.map /boot/grub/device.map_backup
```

Okay then you need to edit the device map.
```
sudo nano /boot/grub/device.map
```
The file probably has one line, like this one
```
(hd0) /dev/hda
```
You should add another for the slave hard drive
```
(hd1) /dev/hdb
```
This basically tells GRUB that /dev/hdb will be known as hd1

Save (Ctrl+O) and exit (Ctrl+X), and then edit the GRUB menu
```
sudo nano /boot/grub/menu.lst
```
You need to move down to the end of the file and past these lines
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

```
Once there you can add the GRUB menu entry for Windows 98
```
title Windows 98
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader +1
```
 - The title can have whatever you wish to see in the GRUB menu

 - The two map commands are a little bit of GRUB trickery, they basically fool Windows 98 into thinking it is on the first partition of the first hard disc.

Save the file (Ctrl+O) and exit (Ctrl+X) and give it a shot.

---

