---
title: "Accessing NTFS raid0 in Kubuntu"
date: 2010-07-15
forum: General Help
---

### Post by AndyM3 on 2010-07-15
I just encountered a huge problem with my PC. It's a Sony VAIO VGC-RC210G with the first two HDDs in a RAID0 configuration. Windows Vista is installed on the RAID and Kubuntu on another HDD.
We had a power outage yesterday and the PC was powered on. Vista wouldn't boot, something which I traced to crcdisk.sys (stupid f***ing CRC check). I tried mounting the RAID array in Ubuntu to recover my dad's files (my files were on the third disk). Lo and behold, dmraid -ay returned this:
```
RAID set "isw_bjgfjedfji_Volume0" already active
```
However, mounting failed. Then, dmraid -r returned this:
```
/dev/sdb: isw, "isw_bjgfjedfji", GROUP, ok, 312581806 sectors, data@ 0
```
WTF? Why isn't my 2 HDD RAID0 stripe there? I then tried using mdadm:
```
# mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb
mdadm: array /dev/md0 built and started.
```
Great, right? But...
```
# mount -t ntfs /dev/md0 /mnt/raid
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
Someone, please help me! The Vista DVD won't start (crcdisk.sys again, I guess), the XP CD hangs on checking the RAID, Knoppix gives the same errors, and testdisk found hundreds of various partitions (image files?), but the NTFS that I need was deemed "unrecoverable".
I really need to get my dad's files off that HDD! It's really serious! Can anyone help me?

---

### Post by AndyM3 on 2010-07-16
Well, nevermind. I messed up the mdadm command. It should have been:
```
# mdadm --build /dev/md0 --chunk=128 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb
```
Also, the mount command should have been:
```
# mount -t ntfs -o ro /dev/md0p1 /mnt/raid
```
Posting it just in case anyone has this problem.

---

