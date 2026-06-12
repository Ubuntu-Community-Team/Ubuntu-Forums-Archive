---
title: "vgdisplay and lvdisplay No volume groups found"
date: 2012-05-08
forum: General Help
---

### Post by senzacionale on 2012-05-08
root@ubuntu-server:~# pvdisplay
root@ubuntu-server:~# vgdisplay
  No volume groups found
root@ubuntu-server:~# lvdisplay
  No volume groups found
root@ubuntu-server:~#

what to do. I can't find solutions on google or somewhere else?

i try:

pvcreate /dev/sdb5
  Device /dev/sdb5 not found (or ignored by filtering).

and this is my fdisk:

 fdisk -l

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050ccb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   488396799   243947521    5  Extended
/dev/sdb5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050ccb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   fd  Linux raid autodetect
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   fd  Linux raid autodetect

Disk /dev/mapper/ubuntu--server-root: 247.7 GB, 247652679680 bytes
255 heads, 63 sectors/track, 30108 cylinders, total 483696640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--server-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--server-swap_1: 2143 MB, 2143289344 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4186112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--server-swap_1 doesn't contain a valid partition table

and my df -h

df -h

Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--server-root  231G  5,0G  214G   3% /
udev                             993M   12K  993M   1% /dev
tmpfs                            401M  356K  401M   1% /run
none                             5,0M     0  5,0M   0% /run/lock
none                            1002M     0 1002M   0% /run/shm
/dev/sdb1                        228M   25M  192M  12% /boot

---

