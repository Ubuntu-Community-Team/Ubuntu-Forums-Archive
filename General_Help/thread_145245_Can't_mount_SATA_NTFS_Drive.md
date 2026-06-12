---
title: "Can't mount SATA NTFS Drive"
date: 2006-03-15
forum: General Help
---

### Post by reazn on 2006-03-15
Recently installed ubuntu, loving it :) I read somewhere that i'm able to mount my 200gb NTFS drive (which is my windows partition) as read-only on ubuntu.

I can't compute without my music which is on the 200gb drive :(

I've managed to make a fat32 partition which is good for switching between to two OS's.. but still i would like access to my 200gb drive in ubuntu. 

its a: SATA BARRACUDA 200gb

i get this when doing a lspci:
> 0000:05:00.0 Unknown mass storage controller: Silicon Image, Inc. (formerly CMD Technology Inc): Unknown device 3132 (rev 01)
0000:06:06.0 Unknown mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 13)


here is what i have currently:
> fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         122      979933+  83  Linux
/dev/hda2             123         244      979965   82  Linux swap / Solaris
/dev/hda3             245        7295    56637157+  83  Linux
/dev/hda4            7296        9729    19551105    b  W95 FAT32


---

### Post by Jedeye on 2006-03-15
try this guide [http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows") also if you still have trouble post what is in your fstab ```
sudo gedit /etc/fstab
```

---

### Post by reazn on 2006-03-15
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hda4       /fat32          vfat    defaults        0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I can't see the 200gb Drive there.. I'm guessing i need drivers or something?

---

### Post by Jedeye on 2006-03-15
what do you see when you go to System>Administration>Disks

---

### Post by aysiu on 2006-03-15
Your *sudo fdisk -l* says you have one hard drive, which is 80 GB.

There's no 200 GB hard drive, according to Ubuntu. Are you sure it's plugged in?

---

### Post by reazn on 2006-03-15
Yep, its definatley plugged in.

---

### Post by reazn on 2006-03-15
it just shows my 80gb drive.

---

### Post by aysiu on 2006-03-15
That's weird.

*sudo fdisk -l* should show you everything that's plugged in, even if it's not yet mounted.

---

### Post by Sutekh on 2006-03-15
Try unplugging the drive, then entering this code in a terminal window
```
tail -f /var/log/messages
```
This will show the last 10 lines and will follow them (-f) as more appear.

Leave the window open and plug the drive back in,and take note of the messages that appear.  That might tell you the device location of the drive.

---

### Post by reazn on 2006-03-15
[QUOTE=Sutekh]Try unplugging the drive, then entering this code in a terminal window
```
tail -f /var/log/messages
```
This will show the last 10 lines and will follow them (-f) as more appear.

Leave the window open and plug the drive back in,and take note of the messages that appear.  That might tell you the device location of the drive.[/QUOTE]
yea, i didn't see anything in the log..

.. ? im confused.

---

### Post by reazn on 2006-03-16
[QUOTE=reazn]yea, i didn't see anything in the log..

.. ? im confused.[/QUOTE]


*bump*

somone help?

---

### Post by reazn on 2006-03-16
[QUOTE=reazn]*bump* x2

somone help?[/QUOTE]

barmp

---

### Post by aysiu on 2006-03-16
I wish I could help.

In my experience, and based on what I've read in these forums of others' experiences, *sudo fdisk -l* has always listed every drive that's plugged in (regardless of whether or not it's mounted).

Since it's not recognizing it... I'm stuck, just as you are.

---

### Post by tyspot on 2006-03-16
is this drive Raid set? are you able to boot into the Windows OS? Have you ever seen it (200GB Drive) in your ubuntu or linux sessions?

May want to try setting the CMOS settings for your SATA mode to legacy or compatible if it is NOT a raid drive or drive array. 

Lets also try using a LiveCD or something and see if it sees the drive. 


Maybe a Spot o help i Hope

---

### Post by reazn on 2006-03-16
i'll try change my BIOS settings, yes i can boot into windows.. 

I have never seen the 200gb drive in any ubuntu sessions. 

I actually couldn't use the live CD, turns out i needed to install drivers and get X up and running, which i just did in the full install. 

Thanks, stay tuned :P

---

### Post by reazn on 2006-03-17
had a look in BIOS, theres no legacy mode available.. 

Frustrating :(

I'm guessing ubuntu isn't supporting the drive..? or i need drivers?

---

### Post by Jason_25 on 2006-03-17
Are you using other sata drives or just that one?  Maybe your motherboard's sata controller is unsupported.

---

### Post by reazn on 2006-03-18
Just the one.. :(

---

