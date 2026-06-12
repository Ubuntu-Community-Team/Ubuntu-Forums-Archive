---
title: "Ext3 Parition incorrect disk space"
date: 2009-07-18
forum: General Help
---

### Post by psycho5 on 2009-07-18
Hi,

I am using ubuntu 9.04 kernel 2.6.28-13-generic dual boot with windows. I have an ext3 parition called media mounted through fstab. I could read and write to this parition while I was in XP and wanted to access my data. 

I upgraded to windows 7 recently, and I have been using ext2 IFS 1.11a to mount and assign drive letter to that parition. Recently I discovered when I go into ubuntu now and read anything from that partition, everything is okay. However when I try to write to it, I get an error message saying parition is full. 

If I check in gparted it shows the correct disk space available, but I don't see it in nautilus. 

Back in windows, I can read and write to it, but windows doesn't show that blue bar anymore that indicates the disk space. If I go to properties the proper disk space is indicated. 

How can I fix this problem? Can anyone guide me to a probable solution? Thanks alot.

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c064c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            7268       38913   254196495   83  Linux
/dev/sda3            1913        7267    43014037+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf475003c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6750    54219343+  83  Linux
/dev/sdb2            6751        7043     2353522+  82  Linux swap / Solaris
/dev/sdb3   *        7044        8955    15358140    7  HPFS/NTFS
/dev/sdb4            8956       24792   127210702+   5  Extended
/dev/sdb5            8956       24792   127210671    7  HPFS/NTFS
oj@oj-desktop:~$ df -h /dev/sda2
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             239G  227G     0 100% /media/Media
oj@oj-desktop:~$ 

```

it says used 100% but its not true.

---

