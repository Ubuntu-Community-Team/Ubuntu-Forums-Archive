---
title: "Can i access my Windows software RAID 1 from Linux"
date: 2010-11-16
forum: General Help
---

### Post by gossoon on 2010-11-16
Hi All

I have done a bit of googling and a search of the forum, but can't find the answer to my question. Hopefully someone here can help

Firstly i am using Crunchbang Linux (built on Ubuntu 9.04)

I have Win7 installed on the first HD in the system (500GB) and as such /dev/sda in Linux

I have two 1TB HD's which are in a RAID 1 configuration, built using Windows Logical Disk Manager, in Linux they are /dev/sdb & /dev/sdc 

I have my fourth drive (again 500GB) with Crunchbang installed at /dev/sdd

```
root@crunchbang:/# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x833c47df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x279e9e46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761528+  42  SFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x439d4fd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976761528+  42  SFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d238e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       58336   468583888+  83  Linux
/dev/sdd2           58337       60801    19800112+   5  Extended
/dev/sdd5           58337       60801    19800081   82  Linux swap / Solaris

```My question is, how can i access the raid drive while in Linux (i spend most of my time in linux now) can i just create an md device and define it as RAID1 one somehow? but then how do the SFS filesystems work

Much confussion here

Thanks in advance

The Gossoon

---

### Post by BobMUK on 2010-11-18
The principles behind RAID are the same regardless of the OS being used.

However the implementation of the design will vary from platform to platform.  This means that arrays from one source (whether a hardware controller, Linux mdraid, Windows, etc) cannot be used elsewhere.

Unless someone out there has reverse-engineered the Windows RAID drivers and implemented them for Linux then you're out of luck (and the chances are slim I'm affraid).

---

### Post by k999 on 2011-03-15
I can't say it any better than Martigen does in this article:

[http://ubuntuforums.org/showpost.php?p=5217561&postcount=5](http://ubuntuforums.org/showpost.php?p=5217561&postcount=5)

I'll just quote this:

> 
Piffle, this is Linux, anything is possible :)


I have used this to successfully mount windows software RAID0 under Linux. Haven't tried RAID1 because I didn't have one, but I don't see why it shouldn't work.

If you get it working, please post the command line you used.

---

### Post by grezzo on 2012-01-12
Did you get it working in the end? I am trying it now, and am having trouble.

---

