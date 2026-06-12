---
title: "Having some Trouble mounting NTFS drive with GPT"
date: 2010-01-05
forum: General Help
---

### Post by digital_alchemy on 2010-01-05
I'm using BT4 I came to these forums only because BT4 is bases on ubuntu and couldn't find the answer any place else.


I'm running BT4 on a 16GB thumb drive set up for persistent changes.
I've been trying to mount a NTFS drive that I use on the windows system to store files.
I've searched for a solution but can't seem to find one; I think my problem is with the GPT.

Here are the results of fdisk -l and the error I get when I try to mount.  

Any help is greatly appreciated.


root@BT4:~# fdisk -l

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59bdd487

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       15566   124930048    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT

Disk /dev/sdc: 16.0 GB, 16009658368 bytes
255 heads, 63 sectors/track, 1946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdc61bf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1859    14932386   83  Linux
/dev/sdc2            1860        1946      698827+   5  Extended
/dev/sdc5            1860        1946      698796   82  Linux swap / Solaris

root@BT4:~# mount -v -t ntfs /dev/sdb1 /mnt/ntfs

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by v.cecchetto on 2010-01-07
Hi,
fdisk doesn't recognize GPT partition table.

If you want to manage GPT partition table you have to use gdisk. 
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Are you sure the file system is NTFS and not FAT?
Try to mount it like FAT.

mount -v -t vfat /dev/sdb1 /mnt/temp

---

### Post by digital_alchemy on 2010-01-13
Thanks for the reply.

Yeah it's a NTFS partition.  Here are the results from testdisk:

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition                           Start                                End             Size in sectors
P NTFS                      16  113  34 121601     57  56  1953259520 [Video Drive]

---

### Post by (morgoth) on 2011-07-03
Did you solve the problem? I am trying to mount a 8TB NTFS-Partition and having the same problem.
Testdisk finds the partition with the right name and size but i cannot mount it.

---

