---
title: "Problems with partitions"
date: 2010-05-04
forum: General Help
---

### Post by ooddaa on 2010-05-04
Hi folks.
I've installed Ubuntu 10.4 in the secondary partition (200gb) of my 320Gb Hd. Now it's only capable of recognizing the primary partition with WindowsXP folders and system stuff, whilst all the rest is left competely ignored. There's no possibility to mount the secondary partition no matter what, but still Ubuntu is aware that the HD is 320GB in total... How do i deal with it?

---

### Post by Elfy on 2010-05-04
Can you post the output of this from a terminal please - Apps > Accessories > Terminal. Command will need your password - it will not show as you type it - this is normal.

```
sudo fdisk -l
```

---

### Post by ooddaa on 2010-05-04
says this

onet@ubuntu:~$ sudo fdisk -l
[sudo] password for onet: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12736   102301888+   7  HPFS/NTFS
/dev/sda2           12737       38913   210266752+   5  Extended
/dev/sda5           12737       38913   210266721    7  HPFS/NTFS

in File Browser there's only one disk to be mounted thou(

---

### Post by Elfy on 2010-05-04
Wubi install I assume.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

---

### Post by ooddaa on 2010-05-04
Sorry, i've bothered you before really checking everything around. I found all data to be located in /host directory. 
thx

---

