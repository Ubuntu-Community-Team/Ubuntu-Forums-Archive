---
title: "Problems using Disks to add 2nd HD"
date: 2006-04-03
forum: General Help
---

### Post by kkelly on 2006-04-03
Hello ive been using disks to try mount my second hd i can see it in disks but when i click enable nothing is happing ?:/ i push help and it says help isnt installed :D so im lost i can post any information you require from term in order to help me but tbh i dunno what im doing :o)

---

### Post by Sutekh on 2006-04-04
Sure but the best way (that I know) is to get this done from the terminal not the GUI.

Can you provide the output from 
```
sudo fdisk -l
```
 - This lists the partitions on your hard drives, so we know *what* to mount

Also post the output from
```
cat /etc/fstab
```
 - This file contains the relevant information for mounting partitions.  

 - You can configure this file to choose the folder the partition will be mounted to, allow certain access to the partition and even choose whether it will be automatically mounted.

---

### Post by frup on 2006-04-04
make sure you are setting a mount directory... in my / folder i made a folder called otheros and then you have to open that in the browse... helpful to click the partition too

---

### Post by woodwrkr97 on 2006-04-05
Hello, I'm a newbie and am having problems as well trying to mount a second hard drive. I've edited /etc/fstab trying to mount it....I'm sure this is probably wrong, can you give me any help.....ABSOLUTELY LOST HERE ](*,)
The hard drive is a 250G and I thought it would be called hdb but I can't find it anywhere. Any good tutorials on this as well????

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    5  Extended
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris
tom@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb /music/nfs/defaults,errors=remount-ro/0/0

---

### Post by NeghVar on 2006-04-05
It will probably be numbered hdb1, unless u have partitions. can u see it in 

System>Administration>Disks?

If you can that will tell you what its number is, if not then youll need more detailed help than I can offer.

---

### Post by Sutekh on 2006-04-06
[QUOTE=woodwrkr97]
The hard drive is a 250G and I thought it would be called hdb but I can't find it anywhere.[/QUOTE]
What sort of drive is it?  IDE/SATA/Removable?  I assume that it is detected by your BIOS and other operating sytems (if any)?

---

