---
title: "Resizing ubuntu disk"
date: 2011-01-19
forum: General Help
---

### Post by chroniccommand on 2011-01-19
So I installed Ubuntu with wubi a while ago. I created a 60GB partition for it but when I installed with wubi it only made the installation size 25G.

My question is, how can I make my ubuntu disk 50GB instead of 25G?

I'm running Ubuntu 10.04

---

### Post by mikewhatever on 2011-01-19
The simple answer is, you can't. Wubi doesn't use partitions, but installs into a file inside Windows file system. There is a way to migrate a wubi installation to a partition. See wubi FAQ for more info.

---

### Post by lithopsian on 2011-01-19
Need to see your gparted output.  Or at least a representation of it showing the existing partitions, sizes, free space, etc.  Partitions can be expanded into free space next to them easily enough.  If the free space is not next to them it gets more tricky, but hard to be specific without seeing the details.

---

### Post by chroniccommand on 2011-01-20
> **lithopsian said:**
> Need to see your gparted output.  Or at least a representation of it showing the existing partitions, sizes, free space, etc.  Partitions can be expanded into free space next to them easily enough.  If the free space is not next to them it gets more tricky, but hard to be specific without seeing the details.
Well here is the output of fdisk -lu
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   269249399   134623676    7  HPFS/NTFS
/dev/sda2       269250560   348514303    39631872    7  HPFS/NTFS
/dev/sda3       348516352   488392703    69938176    7  HPFS/NTFS

```
sda1 is windows, sda2 is an empty 37GB partition and sda3 is ubuntu.

---

### Post by mikewhatever on 2011-01-20
Well, sda3 is probably where the wubi installation is, but it's not Ubuntu. Ubuntu doesn't use NTFS file system for its installations.

---

### Post by Krzysiaczek99 on 2011-02-13
I have similar problem. How I can resize this partition created by wubi ? Here is my disk info, I beleive there is a space there.

krzysztof@ubuntu:~$ sudo fdisk -lu
[sudo] password for krzysztof: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcaa5a3b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953523711   976760832    7  HPFS/NTFS
krzysztof@ubuntu:~$

---

### Post by BslBryan on 2012-11-28
I understand this thread is old, but the information here is putting a grimace on my face.  If you don't know how to do something, the answer is not "you can't do it."  

Information regarding resizing Wubi virtual partitions can be found [here.]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk") 

Once downloaded, cd to the directory you extracted the tarball, and run ```
sudo bash wubi-resize.sh size
``` in an Ubuntu terminal where "size" is the number of GB you would like to resize to.  Note that this will create a duplicate virtual disk, so if you want to create a 40gb wubi install, you must have 40gb of additional hard disk space.

---

