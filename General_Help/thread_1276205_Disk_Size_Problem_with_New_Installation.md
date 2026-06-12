---
title: "Disk Size Problem with New Installation"
date: 2009-09-26
forum: General Help
---

### Post by am6465 on 2009-09-26
I just installed ubuntu alongside my XP installation. When the options came up for where to install Ubuntu (either partition the hard drive or install next to current OS) I chose to install it next to the current os. When I log in everything work fine until i try to download things. When i attempted to run updates it tells me my disk is full and I have to delete things before I can download the files. I have no idea why and my hard drive is definitely not filled. Any ideas? Thanks

---

### Post by Shazaam on 2009-09-26
Look in gparted (System>Administration>Partition Editor) if you have it installed and check your partition sizes. You can also do that with the livecd.
If you can, post the output of
```
df -h
```
and
```
sudo fdisk -lu
```
(lowercase L)
Here is mine...
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              99G   32G   63G  34% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  224K 1007M   1% /var/run
varlock              1007M  8.0K 1007M   1% /var/lock
udev                 1007M  176K 1007M   1% /dev
tmpfs                1007M   96K 1007M   1% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile
```
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   260060219   130030078+   5  Extended
/dev/sda5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sda6         4369743   214194644   104912451   83  Linux
/dev/sda7       214194708   260060219    22932756   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS
```
If you find you have run out of room you can resize your partitions. Use the Ubuntu livecd for that. Make sure you defrag Windows first.

---

### Post by michy99 on 2009-09-26
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

