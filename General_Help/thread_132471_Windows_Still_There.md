---
title: "Windows Still There?"
date: 2006-02-18
forum: General Help
---

### Post by jasrog on 2006-02-18
How do I know if i messed up install and windows is gone?

---

### Post by SVFUSiON on 2006-02-18
is it showing up in GRUB under "Other Operating Systems"?

---

### Post by jasrog on 2006-02-18
How do I exactly check that? I am a rookie....

---

### Post by SVFUSiON on 2006-02-18
When your computer boots, does it boot to a "Boot Loader"?

---

### Post by jasrog on 2006-02-18
I do not select anything Ubuntu just loads....

---

### Post by SVFUSiON on 2006-02-18
I think you might have formated your whole drive since grub did not set up  automatic. 

type sudo nano /boot/grub/grub.conf then copy and past it to a post.

---

### Post by SVFUSiON on 2006-02-18
if that don't work try 
sudo nano /etc/grub.conf

---

### Post by jasrog on 2006-02-18
How Do I do that?

---

### Post by SVFUSiON on 2006-02-18
at the top in "Applications" then goto "Accessories" then "Terminal"

---

### Post by jasrog on 2006-02-18
When i do that stuff gets highlighted in black but no info appears...

---

### Post by SVFUSiON on 2006-02-18
EDIT

actually do this

type
sudo fdisk -l  /This should show your partiton tables, if no NTFS table shows up...

if it does show up try this to mount windows partiton

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

### Post by jasrog on 2006-02-18
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
  This is what shows up... now what?

---

### Post by SVFUSiON on 2006-02-18
you hit I and not L :rolleyes:

---

### Post by jasrog on 2006-02-18
I am lost how do I do that?  I thank you for your patience...

---

### Post by SVFUSiON on 2006-02-18
in the Terminal, type 

sudo fdisk -l 

(the l is a lower case L)

---

### Post by jasrog on 2006-02-18
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19075   153219906   83  Linux
/dev/sda2           19076       19452     3028252+   5  Extended
/dev/sda5           19076       19452     3028221   82  Linux swap / Solaris

This appears so does this mean windows is gone?

---

### Post by SVFUSiON on 2006-02-18
Sorry bud, you formated your hard drive completely.I hate it when that happens, but it does happen.I hope you do not turn your back on Linux, as this stuff happens, we are always learning.

---

### Post by sean.smithson on 2006-02-18
snip

---

### Post by jasrog on 2006-02-18
I definetly don't turn my back...but how do I install Windows now?....i want dual boot...

---

### Post by SVFUSiON on 2006-02-18
What I would do is install windows xp (delete all the linux partitions) then format the drive NTFS, then download a partiton editor (I always have good luck with Partiton Magic 8) then resize the partiton to around half (or as much as you want too) then when it is done, install ubuntu in the space you have left. That is what I did, if you need help you can MSN me.

---

### Post by SVFUSiON on 2006-02-18
acutally you might want to format the windows with FAT32 so you can read/write to it in linux, if you do NTFS you only can read it.

---

### Post by naptrix on 2006-02-19
Hi, I kinda have the same problem. When I boot up my grub shows me ubuntu, recovery, ubuntu, and recovery. 
There are nothing caled Other operating systems. Dont know what I have done wrong this time, but I need help. I have xp also :

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2354    18908473+   c  W95 FAT32 (LBA)
/dev/hda2            2610        3647     8337735   83  Linux
/dev/hda3            2484        2609     1012095    f  W95 Ext'd (LBA)
/dev/hda4            2355        2483     1036192+   b  W95 FAT32
/dev/hda5            2484        2609     1012063+  82  Linux swap / Solaris

I should have ca 20GB for xp, and about 8GB for ubuntu, but I dont knot what went wrong. 
Can someone help me to get xp back on my boot screen?

---

### Post by MadMan2k on 2006-02-19
1. I'd rather use ext2 for data exchange:
[http://www.madman2k.net/?module=article&id=19#p1](http://www.madman2k.net/?module=article&id=19#p1)

2. you can use gparted for patitioning as well.it is included on the liveCD.

3. you have to install windows first and then linux - otherwise windows will kick GRUB.
so you do it best like:
- partiton your harddrive using the liveCD
- install Windows on the first partition
- install Ubuntu and tell it which partition to use this time

---

