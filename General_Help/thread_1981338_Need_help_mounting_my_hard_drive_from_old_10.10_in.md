---
title: "Need help mounting my hard drive from old 10.10 install"
date: 2012-05-16
forum: General Help
---

### Post by ingramproductions on 2012-05-16
I have 12.04 installed on hard drive sda. If I add the second hard drive (sdb, which has 10.10 on it), I can't mount any partitions execpt for sdb1, which doesn't have any of my data on it. If I only use the disk with 10.10, I can boot to it just fine.

So how do I mount the partitions on the second disk while I'm booted from the first disk with 12.04 on it??
```
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012c83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945139199   972568576   83  Linux
/dev/sda2      1945141246  1953523711     4191233    5  Extended
/dev/sda5      1945141248  1953523711     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c27c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   976771071   488134657    5  Extended
/dev/sdb5          501760   976771071   488134656   8e  Linux LVM
```
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       927G   20G  861G   3% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           807M  840K  806M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  1.4M  2.0G   1% /run/shm
/dev/sdb1       228M   73M  143M  34% /media/19308615-47dd-4e35-b947-6bca5c02f2bb
```

---

### Post by steeldriver on 2012-05-16
looks like your old system used LVM (look at the partition type / number for sdb5)

this may help - sorry I'm only just starting out with lvm myself so I don't know exactly how to do it

[http://linuxers.org/howto/how-mount-linux-lvm-volume-partitions-linux](http://linuxers.org/howto/how-mount-linux-lvm-volume-partitions-linux)

---

