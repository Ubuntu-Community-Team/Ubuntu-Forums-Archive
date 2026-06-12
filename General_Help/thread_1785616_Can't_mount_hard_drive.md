---
title: "Can't mount hard drive"
date: 2011-06-18
forum: General Help
---

### Post by lmp90 on 2011-06-18
I'mm trying to mount a hard drive in Ubuntu but it doesn't work
i typed the following commands
```
cd ../..
sudo  mkdir /media/windows
sudo mount /dev/sda /media/windows -t ntfs
```and then it says
```
Error opening '/dev/sda': Read-only file system
Failed to mount '/dev/sda': Read-only file system
```i wanted to access my files, not write to it, so is there anyway to mount as read only?

---

### Post by TheDoctorX on 2011-06-18
try to see what format do you have for this hard disk ... or try to open it from the graphic interface .. win files are on host folder

---

### Post by lmp90 on 2011-06-18
it's my internal hdd, it's new tech file system
when i double click on it in nautilus it says : No Application installed for block devices

---

### Post by lmp90 on 2011-06-25
bump

---

### Post by linuchsan on 2011-06-25
It is, mount -t ntfs-3g. What does fdisk -l say?

---

### Post by Morbius1 on 2011-06-25
You can't mount /dev/sda. /dev/sda is the entire entire hard drive. You mount partitions. It should be something like /dev/sda1.

---

### Post by lmp90 on 2011-06-25
> **linuchsan said:**
> It is, mount -t ntfs-3g. What does fdisk -l say?

i typed the command:
```
# mount -t ntfs-3g /dev/sda /media/windows
```
and got
```
Failed to read bootsector (size=0)
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```
i tried:
```
fdisk -l
```
but nothing shows

---

### Post by lmp90 on 2011-06-25
> **Morbius1 said:**
> You can't mount /dev/sda. /dev/sda is the entire entire hard drive. You mount partitions. It should be something like /dev/sda1.

/dev/sda is the only part of my hdd

---

### Post by linuchsan on 2011-06-25
nop, it must have a number. Try sudo fdisk -l again.

---

### Post by linuchsan on 2011-06-25
Sorry...i forgot the sudo ;)

---

### Post by lmp90 on 2011-06-25
```
sudo fdisk -l
``````
Disk /dev/sdb: 500.1 GB, 500079525888 bytes
255 heads, 63 sectors/track, 60797 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007526a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       55757   447862305    7  HPFS/NTFS
/dev/sdb2           55758       60798    40489755    f  W95 Ext'd (LBA)
/dev/sdb5           55758       60013    34179687+  83  Linux
/dev/sdb6           60013       60798     6309888   82  Linux swap / Solaris

Disk /dev/mmcblk0: 8031 MB, 8031043584 bytes
99 heads, 18 sectors/track, 8802 cylinders
Units = cylinders of 1782 * 512 = 912384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               5        8803     7838720    b  W95 FAT32
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 995 MB, 995622912 bytes
1 heads, 62 sectors/track, 7841 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7842      972286    5  Extended
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/sdc5               1        7842      972284    b  W95 FAT32
Partition 5 does not start on physical sector boundary.

```

---

### Post by Morbius1 on 2011-06-26
You don't have a /dev/sda.

The only ntfs partition you have is /dev/sdb1. You should be able to mount that through Nautilus but if you want to mount it manually it would be:
```
sudo mount -t ntfs /dev/sdb1 /media/windows
```

---

### Post by lmp90 on 2011-06-30
/dev/sdb1 is my external hdd,
/dev/sda is my entire windows hdd

---

### Post by Morbius1 on 2011-07-01
I don't know what to tell you. Try as you might you cannot mount /dev/sda for two primary reasons:

[1] You have no /dev/sda

[2] You cannot mount a hard drive which is what /dev/sda would be if you had a /dev/sda. You can only mount partitions located on /dev/sda if you had a /dev/sda which you do not.

---

