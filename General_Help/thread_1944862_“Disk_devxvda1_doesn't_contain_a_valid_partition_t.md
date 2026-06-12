---
title: "“Disk /dev/xvda1 doesn't contain a valid partition table”"
date: 2012-03-22
forum: General Help
---

### Post by dr_dumb99 on 2012-03-22
Iam newbie to EC2 and Ubuntu 11 (EC2 Free tier Ubuntu). I have made following commands.
sudo mkfs -t ext4 /dev/xvdf6
sudo mkdir /db
sudo vim /etc/fstab 
/dev/xvdf6 /db ext4 noatime,noexec,nodiratime 0 0
sudo mount /dev/xvdf6 /db
fdisk -l 
I got following output. Can some one guide me what I am doing wrong and how it can be rectified.
Disk /dev/xvda1: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Disk /dev/xvda1 doesn't contain a valid partition table
Disk /dev/xvdf6: 6442 MB, 6442450944 bytes
255 heads, 63 sectors/track, 783 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Disk /dev/xvdf6 doesn't contain a valid partition table.

---

