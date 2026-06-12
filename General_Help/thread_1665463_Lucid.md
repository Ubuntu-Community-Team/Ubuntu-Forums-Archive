---
title: "Lucid"
date: 2011-01-12
forum: General Help
---

### Post by Rudra Brahm on 2011-01-12
I am not able to update my system. whenever I tried I got a pop up message....

"Not enough free disk space

The upgrade needs a total of 19.9M free space on disk '/boot'. Please free at least an additional 13.7M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

But there is more than 80% free space in the boot partition. Please HELP!!!

---

### Post by oldos2er on 2011-01-12
Can you run these two commands, and post the output here? ```
sudo fdisk -l
df -h
```

---

### Post by Rudra Brahm on 2011-01-12
the output for "sudo fdisk-l" is...

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe19de19d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       94208   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              12        4866    38985729    5  Extended
/dev/sda5              12         883     6995968   83  Linux
/dev/sda6             884        1256     2995200   82  Linux swap / Solaris
/dev/sda7            1257        4866    28992512   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5aba4ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4570    36700160    7  HPFS/NTFS
/dev/sdb2            4570       11097    52428800    7  HPFS/NTFS
/dev/sdb3           11097       17624    52428800    7  HPFS/NTFS
/dev/sdb4           17624       38914   171011072    f  W95 Ext'd (LBA)
/dev/sdb5           17624       24151    52428800    7  HPFS/NTFS
/dev/sdb6           24151       30678    52428800    7  HPFS/NTFS
/dev/sdb7           30678       38914    66150400    7  HPFS/NTFS

Disk /dev/sdc: 507 MB, 507379712 bytes
16 heads, 61 sectors/track, 1015 cylinders
Units = cylinders of 976 * 512 = 499712 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      797271     1966850   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(797270, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1966849, 14, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      172838     2156474   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(172837, 10, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2156473, 1, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1915863     3899498   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1915862, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3899497, 9, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?           1     3726667  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3726666, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

and the output for dh-l is

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe19de19d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       94208   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              12        4866    38985729    5  Extended
/dev/sda5              12         883     6995968   83  Linux
/dev/sda6             884        1256     2995200   82  Linux swap / Solaris
/dev/sda7            1257        4866    28992512   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5aba4ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4570    36700160    7  HPFS/NTFS
/dev/sdb2            4570       11097    52428800    7  HPFS/NTFS
/dev/sdb3           11097       17624    52428800    7  HPFS/NTFS
/dev/sdb4           17624       38914   171011072    f  W95 Ext'd (LBA)
/dev/sdb5           17624       24151    52428800    7  HPFS/NTFS
/dev/sdb6           24151       30678    52428800    7  HPFS/NTFS
/dev/sdb7           30678       38914    66150400    7  HPFS/NTFS

Disk /dev/sdc: 507 MB, 507379712 bytes
16 heads, 61 sectors/track, 1015 cylinders
Units = cylinders of 976 * 512 = 499712 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      797271     1966850   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(797270, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1966849, 14, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      172838     2156474   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(172837, 10, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2156473, 1, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1915863     3899498   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1915862, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3899497, 9, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?           1     3726667  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3726666, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
suren@suren-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.6G  4.1G  2.2G  65% /
none                  1.5G  344K  1.5G   1% /dev
none                  1.5G  312K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G  4.0K  1.5G   1% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda7              28G   22G  4.7G  82% /home
/dev/sda1              90M   79M  6.0M  93% /boot
/dev/sr1              9.9M  9.9M     0 100% /media/Access Manager
/dev/sdc              484M  439M   46M  91% /media/Suren

---

### Post by oldos2er on 2011-01-12
> /dev/sda1 90M 79M 6.0M 93% /boot

There's only 6MB free in /boot, as you can see. If you have two or more kernels installed, uninstalling one or more would get you a little space, but sooner or later you'd run into the same problem. Two other possibilities; resize partitions, or buy a bigger hard disk.

---

### Post by lionaneesh on 2011-01-12
If you want you could delete the unwanted kernels....
Method :-
[http://www.go4expert.com/forums/showthread.php?t=24436](http://www.go4expert.com/forums/showthread.php?t=24436)

---

### Post by Rudra Brahm on 2011-01-13
Thanks a lot oldos2er and lioaneesh. I will try removing the unused kernal..

---

### Post by Rudra Brahm on 2011-01-13
Thanks a lot again. It works.:D

---

### Post by lionaneesh on 2011-01-13
> **Rudra Brahm said:**
> Thanks a lot again. It works.:D

Welcome my Pleasure!!!!

---

