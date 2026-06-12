---
title: "problem backing up with partimage"
date: 2009-11-21
forum: General Help
---

### Post by milenixloerdi on 2009-11-21
Hi,

I am trying to backup my partition /dev/sda1 where my /home directory is onto the /dev/sdb2 partition, using "PartImage". 

```
hristo@Desktop:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b896ac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18241   146520801   83  Linux

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd5bcd5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7781    62500851   83  Linux
/dev/sdb2            7782        9964    17534947+   7  HPFS/NTFS

Disk /dev/sdc: 515 MB, 515768320 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f3122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          62      497983+  82  Linux swap / Solaris
hristo@Desktop:~$ sudo mkdir /backup
hristo@Desktop:~$ sudo mount -t ext3 /dev/sdb2 /backup
hristo@Desktop:~$ sudo partimage
hristo@Desktop:~$ 

```

I am not sure wether I created the /backup directory on the /dev/sdb2 partition and I cannot seem to be able to umount the /home directory (partimage says /home is mounted and cannot proceed with backup).

```
hristo@Desktop:~$ cd /
hristo@Desktop:/$ umount /home
umount: only root can unmount UUID=e35f907c-0fc1-4c70-86cc-be40e6ac1fd3 from /home

```

Frankly, I do not know how to "go to the root and umount /home" and...wether and how I have to mount /home after the backup finishes so that I can access the /home again.

Please, help me if you can, thanks!

---

### Post by dcstar on 2009-11-21
> **milenixloerdi said:**
> Hi,

I am trying to backup my partition /dev/sda1 where my /home directory is onto the /dev/sdb2 partition, using "PartImage". 
........
Frankly, I do not know how to "go to the root and umount /home" and...wether and how I have to mount /home after the backup finishes so that I can access the /home again.

Please, help me if you can, thanks!

You cannot unmount partitions that are in use. Boot off a Live CD/USB if you want to work on system partitions.

If you want to back up mounted data then use something like unison.

---

