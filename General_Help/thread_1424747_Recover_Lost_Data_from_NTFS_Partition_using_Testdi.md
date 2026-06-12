---
title: "Recover Lost Data from NTFS Partition using Testdisk/Photorec"
date: 2010-03-08
forum: General Help
---

### Post by ushpiy on 2010-03-08
Hello!

I am in a bit of a mess here. My main partition having all my data like movies, music, files,etc has become inaccessible. Its file system was NTFS. 
Due to some recent resizing using GParted, the partition as well as my WIndows 7 OS has become unbootable due to some errors.
[COLOR=Black]The data partition's file system has become unknown.[/COLOR]
I don't care much about the OS but I would like to recover my drive. I am trying to achieve this using Testdisk and Photorec but haven't met with much success so far.
The main problem is I can see my partition and all my files through Testdisk but I am not able to copy them to another drive.
When I try to copy the option I get is of copying them to the DVD and not to any other partition.
So could any of you help me to copy my data back to my any other partition?
Thanks

If you want any other information then please ask.

In short:
My NTFS partition's file system has become unknown (in GParted) and I request you guys to kindly help me recover my data.

---

### Post by cong06 on 2010-03-08
I'm curious what all changes you made, so I guess another "fdisk -l" is in order?

Maybe if you could give us a brief summary of what exactly you did, that would be helpful also. Just so we know how doable this is.

(I assume you've already seen this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery))

---

### Post by ushpiy on 2010-03-08
Here's the output:
===
Welcome - Parted Magic (Linux 2.6.28.7-pmagic)
Most of the filesystem tools and partition programs featured by Parted Magic
include man pages.  To read a manual page,  simply type man and
the name of the tool. (Examples: 'man ntfsprogs' or 'man fdisk')

root@PartedMagic:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd694ae23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391    7  HPFS/NTFS
/dev/sda2              14        6540    52428127+   7  HPFS/NTFS
/dev/sda3            6541       58190   414878625    5  Extended
/dev/sda4   *       58191       60801    20972857+  af  Unknown
/dev/sda5            6541       32039   204816097    7  HPFS/NTFS
/dev/sda6           40611       43221    20972826   af  Unknown
/dev/sda7           43222       58190   120238461    7  HPFS/NTFS
root@PartedMagic:~# 
===

Ok so what I did was:-
sda2 was originally 119 GB I resized it to 50 GB and added the rest of the space to sda3.
From sda3 I added the space to sda5.
This is what I did.
Now what has happened is sda5 has remained 195 GB and the unallocated 65 GB from sda2 is in sda3, meaning it was not added to sda 5.
sda 5 contains all my precious data and I request you all to please help me.
I can see my files through Testdisk but am not able to copy them to another partition on the hard disk. It only allows me to copy to the Live CD.

EDIT:
I am giving up all hopes of recovering my data as after reading through the link in the above post, I have realized that they cannot transfer recovered data to another partition (right) and as I don't have another drive of size 195 GB, I cannot recover the data.
Please guys if you have any other option which may help me recover the data ten please do enlighten me about that.
Thanks.

---

### Post by Mark Phelps on 2010-03-08
IF your partitions are badly corrupted, there's going to be no way you can do data recovery to the same physical drive -- something you've already discovered.

Your only options for recovering data are going to be to use an external drive of some kind -- hard drive or USB stick.

In future, if you have stuff you don't want to risk damaging or losing, you would do better to do two things: (1) check these forums before you do something (there are LOTS of posts, many of them from me, about NOT using GParted to resize Win7 partitions), and (2) do a backup of your valuable, irreplaceable data.

---

### Post by ushpiy on 2010-03-08
Actually only one partition (I hope) is badly corrupted. 
Yeah, learnt my lesson about Backups.

EDIT: I would like to close this thread as I have resolved this issue.

---

