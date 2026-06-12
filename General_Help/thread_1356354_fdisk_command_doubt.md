---
title: "fdisk command doubt"
date: 2009-12-16
forum: General Help
---

### Post by shariefbe on 2009-12-16
Hi i am trying to do partition in my SD card. for that i tried 

my device name is sdb1. but it says

```

ariem@ariem-desktop:/dev$ fdisk /dev/sdb1

Unable to open /dev/sdb1

```
 I dont know what will be the problem. Please help me

---

### Post by dcstar on 2009-12-16
> **shariefbe said:**
> Hi i am trying to do partition in my SD card. for that i tried 

my device name is sdb1. but it says

```

ariem@ariem-desktop:/dev$ fdisk /dev/sdb1

Unable to open /dev/sdb1

```
 I dont know what will be the problem. Please help me

```
sudo fdisk /dev/sdb1
```

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> Hi i am trying to do partition in my SD card. for that i tried 

my device name is sdb1. but it says

```

ariem@ariem-desktop:/dev$ fdisk /dev/sdb1

Unable to open /dev/sdb1

```
 I dont know what will be the problem. Please help me

/dev/sdb1 is the first partition on the second drive. Are you sure that's the one you have to partition?

Why don't you try a GUI tool, like [GParted]("apt://gparted"),  to partition the drive? I use the cli a lot, but for partitioning I found the GUI more intuitive.

---

### Post by shariefbe on 2009-12-16
Yes thank you. Now it works fine. I partitionaed my SD card. ANd it shows the out for "print the partition table" is

```

Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1           4        8032+  83  Linux
/dev/sdb1p2               5          11       14112   83  Linux
/dev/sdb1p3              12         956     1905120   83  Linux

Command (m for help): 

```
 Now in what file system this partitions are. And how to change the file system of each partition.
 When i open /media/disk i am not seeing any partitioned part. Just it shows all the things. what is wrong?

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> Yes thank you. Now it works fine. I partitionaed my SD card. ANd it shows the out for "print the partition table" is

```

Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1           4        8032+  83  Linux
/dev/sdb1p2               5          11       14112   83  Linux
/dev/sdb1p3              12         956     1905120   83  Linux

Command (m for help): 

```
 Now in what file system this partitions are. And how to change the file system of each partition.
 When i open /media/disk i am not seeing any partitioned part. Just it shows all the things. what is wrong?

You have partitioned the first partition. :)

Type q and press enter to quit without saving the changes.

You have to run:
```
sudo fdisk /dev/sdb
```
to create a new partition table on the whole drive.

But, once again, use a GParted, is much easier.

---

### Post by shariefbe on 2009-12-16
Yes thank you. Now i partitoned the whole disk. see the partition table 

```
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4        8032+  83  Linux
/dev/sdb2               5          11       14112   83  Linux
/dev/sdb3              12         957     1907136   83  Linux


```

Now how to change the file system for each partion?
i want to change
first partition as RAW
Second partition as FAT32
Third as EXT3
 What are the command i have to give change the file system of each partition. I am confused. Please help me

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> Yes thank you. Now i partitoned the whole disk. see the partition table 

```
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4        8032+  83  Linux
/dev/sdb2               5          11       14112   83  Linux
/dev/sdb3              12         957     1907136   83  Linux


```

Now how to change the file system for each partion?
i want to change
first partition as RAW
Second partition as FAT32
Third as EXT3
 What are the command i have to give change the file system of each partition. I am confused. Please help me

Type L to list the known partition types. To change the type of the partition, press t, you will be asked for the partition number and the hex code(you get from L).

NOTE: fdisk only creates the partition table, you will have to format the partitions with the mkfs (mkfs.ext3, mkfs.vfat) command.

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")

---

### Post by shariefbe on 2009-12-16
yes Thank you and think i changed the file system sdc2 and sdc3 partitions. see the output. is this changed 
```
root@ariem-desktop:/dev# mkfs.ext3 /dev/sdc3
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
119280 inodes, 476784 blocks
23839 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=490733568
15 block groups
32768 blocks per group, 32768 fragments per group
7952 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Writing inode tables: done                            
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@ariem-desktop:/dev# mkfs.vfat /dev/sdc2
mkfs.vfat 3.0.1 (23 Nov 2008)
root@ariem-desktop:/dev# 

```
But i am getting my disk in /media. just i am geeting my device names in /dev file system. why it is like this?is there any wrong?

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> yes Thank you and think i changed the file system sdc2 and sdc3 partitions. see the output. is this changed 
```
root@ariem-desktop:/dev# mkfs.ext3 /dev/sdc3
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
119280 inodes, 476784 blocks
23839 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=490733568
15 block groups
32768 blocks per group, 32768 fragments per group
7952 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Writing inode tables: done                            
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@ariem-desktop:/dev# mkfs.vfat /dev/sdc2
mkfs.vfat 3.0.1 (23 Nov 2008)
root@ariem-desktop:/dev# 

```
But i am getting my disk in /media. just i am geeting my device names in /dev file system. why it is like this?is there any wrong?

try to mount them manually:

```

sudo mkdir /mnt/tmp
sudo mount -t auto -o defaults /dev/sd**XY** /mnt/temp
```

if it works, try to reboot.

---

### Post by shariefbe on 2009-12-16
Thats is fine. what about the file system? i think the file system for 3rd partition has changed. why this 2nd file system has not changed?

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> Thats is fine. what about the file system? i think the file system for 3rd partition has changed. why this 2nd file system has not changed?

Please post the output of:
```
sudo fdisk -l
```

---

### Post by shariefbe on 2009-12-16
This is the outpit of fdisk -l
```

root@ariem-desktop:/media# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015ad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       30401    97715362+   5  Extended
/dev/sda5           18237       18844     4883728+  82  Linux swap / Solaris
/dev/sda6           18845       30401    92831571   83  Linux

Disk /dev/sdd: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           4        8032+  83  Linux
/dev/sdd2               5          11       14112   83  Linux
/dev/sdd3              12         957     1907136   83  Linux
root@ariem-desktop:/media# 


```

---

### Post by sisco311 on 2009-12-16
```
sudo fdisk /dev/sdd
```
press t to change the type, then 2 to select the second partition, c to set the type, then w to write the changes to the disk.

then:
```
sudo mkfs.vfat -F 32 /dev/sdd2
```

---

### Post by shariefbe on 2009-12-16
yes thank you. I changed.
Now i am facing another problem. I dont know it is a problem anyway i will post it. 

I am getting 2 disk,one is having 1.7 GB space and another one is 14.5 MB space. Why it is coming like this When i remove my SD card and inserted.
i partitioned as 5MB,10MB,Remaining. But it shows the wrong volume. why it happened?

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> yes thank you. I changed.
Now i am facing another problem. I dont know it is a problem anyway i will post it. 

I am getting 2 disk,one is having 1.7 GB space and another one is 14.5 MB space. Why it is coming like this When i remove my SD card and inserted.
i partitioned as 5MB,10MB,Remaining. But it shows the wrong volume. why it happened?

According to fdisk -l:
```

Disk /dev/sdd: **1977 MB**, 1977614336 bytes
64 heads, 63 sectors/track, **957 cylinders**
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000


Device Boot         Start         End      Blocks   Id  System
/dev/sdd1               1           4        8032+  83  Linux
/dev/sdd2               5          11       14112   83  Linux
/dev/sdd3              12         957     1907136   83  Linux
```

1977 MB = 957 cylinders 

sdd2 = 6 cylinders = 6*1977/957 MB =~12MB
sdd3 = 945 cylinders = 945*1977/957 MB =~1952MB =~ 1.7GB

---

### Post by shariefbe on 2009-12-16
ok Thanks a lot. Then why this first partition is  not viewing?Only two partitions are viewing?

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> ok Thanks a lot. Then why this first partition is  not viewing?Only two partitions are viewing?

Probably because it's unallocated.

Did you set the partition type and format it?

---

### Post by shariefbe on 2009-12-16
No i dont want to create file system in that first partition. Because i am going to load u boot bootloader in that first partition. That partition should be in RAW, Thats why.

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> No i dont want to create file system in that first partition. Because i am going to load u boot bootloader in that first partition. That partition should be in RAW, Thats why.

You can't mount an unformatted (unallocated) partition, that's why it doesn't shows up.

---

### Post by shariefbe on 2009-12-16
So it is not possible to store the information in 1st partition?
but the documentation says that it should me like that. 
see

The partition layout of bootable SD card is shown as below:

SD Card Partition  -  4G bytes
+-------------------+
|  4MB RAW      | uBoot image + boot info
+-------------------+
|  8MB FAT32   | Partition 1:  Boot Signature + uImage kernel
+-------------------+
|           EXT3    |  Partition 2: ROOTFS
+-------------------+

what to do?

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> So it is not possible to store the information in 1st partition?
but the documentation says that it should me like that. 
see

The partition layout of bootable SD card is shown as below:

SD Card Partition  -  4G bytes
+-------------------+
|  4MB RAW      | uBoot image + boot info
+-------------------+
|  8MB FAT32   | Partition 1:  Boot Signature + uImage kernel
+-------------------+
|           EXT3    |  Partition 2: ROOTFS
+-------------------+

what to do?

Please post a link to the HOWTO/Documentation.

You can use the dd command to copy the image to the partition.

---

### Post by shariefbe on 2009-12-16
no its not open to all. Its in board developers ftp site. for your kind information i will attch the documentation with this poat. refer it. And i am using u boot.

---

### Post by sisco311 on 2009-12-16
> **shariefbe said:**
> no its not open to all. Its in board developers ftp site. for your kind information i will attch the documentation with this poat. refer it. And i am using u boot.

Oh, OKAY. If I understand the doc correctly you have to copy the  uBoot image to the first(RAW) partition:
```
sudo dd if=/path/to/image of=/dev/sdd1 bs=1M
```


EDIT: Please remove the attachment, the license of the doc doesn't allows you to disclose it.

---

### Post by shariefbe on 2009-12-16
i am getting some error in dmesg. i dont know what it is. i will post some few lines below which shows error in dmesg
```
[15437.732731] usb-storage: waiting for device to settle before scanning
[15442.732464] usb-storage: device scan complete
[15442.736843] scsi 12:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9412 PQ: 0 ANSI: 0
[15443.025944] sd 12:0:0:0: [sdb] 3862528 512-byte hardware sectors: (1.97 GB/1.84 GiB)
[15443.027061] sd 12:0:0:0: [sdb] Write Protect is off
[15443.027064] sd 12:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15443.027068] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[15443.029614] sd 12:0:0:0: [sdb] 3862528 512-byte hardware sectors: (1.97 GB/1.84 GiB)
[15443.030690] sd 12:0:0:0: [sdb] Write Protect is off
[15443.030695] sd 12:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15443.030698] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[15443.030705]  sdb: sdb1 sdb2 sdb3
[15443.033819] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[15443.033919] sd 12:0:0:0: Attached scsi generic sg2 type 0
[15443.748027] kjournald starting.  Commit interval 5 seconds
[15443.750588] EXT3 FS on sdb3, internal journal
[15443.750595] EXT3-fs: mounted filesystem with ordered data mode.
[15443.900734] EXT3-fs error (device sdd3): ext3_find_entry: reading directory #2 offset 0
[15443.900880] FAT: Directory bread(block 57) failed
[15443.900887] FAT: Directory bread(block 58) failed
[15443.900893] FAT: Directory bread(block 59) failed
[15443.900899] FAT: Directory bread(block 60) failed
[15443.900905] FAT: Directory bread(block 61) failed
[15443.900910] FAT: Directory bread(block 62) failed
[15443.900916] FAT: Directory bread(block 63) failed
[15443.900922] FAT: Directory bread(block 64) failed
[15443.900928] FAT: Directory bread(block 65) failed
[15443.900934] FAT: Directory bread(block 66) failed
[15443.900940] FAT: Directory bread(block 67) failed
[15443.900946] FAT: Directory bread(block 68) failed
[15443.900951] FAT: Directory bread(block 69) failed
[15443.900957] FAT: Directory bread(block 70) failed
[15443.900963] FAT: Directory bread(block 71) failed
[15443.900969] FAT: Directory bread(block 72) failed
[15443.900975] FAT: Directory bread(block 73) failed
[15443.900980] FAT: Directory bread(block 74) failed
[15443.900986] FAT: Directory bread(block 75) failed
[15443.900992] FAT: Directory bread(block 76) failed
[15443.900998] FAT: Directory bread(block 77) failed
[15443.901003] FAT: Directory bread(block 78) failed
[15443.901009] FAT: Directory bread(block 79) failed
[15443.901015] FAT: Directory bread(block 80) failed
[15443.901021] FAT: Directory bread(block 81) failed
[15443.901027] FAT: Directory bread(block 82) failed
[15443.901033] FAT: Directory bread(block 83) failed
[15443.901038] FAT: Directory bread(block 84) failed
[15443.901044] FAT: Directory bread(block 85) failed
[15443.901050] FAT: Directory bread(block 86) failed
[15443.901056] FAT: Directory bread(block 87) failed
[15443.901062] FAT: Directory bread(block 88) failed
ariem@ariem-desktop:~$ 

```

---

### Post by shariefbe on 2009-12-16
see after i copied its not getting unmount
```
ariem@ariem-desktop:~$ sudo dd if=/home/ariem/Desktop/pegatron/u-boot-200901-lange51/u-boot.bin of=/dev/sdb1 bs=1M
[sudo] password for ariem: 
0+1 records in
0+1 records out
125048 bytes (125 kB) copied, 0.00392614 s, 31.9 MB/s
ariem@ariem-desktop:~$ umount /dev/sdb1
umount: /dev/sdb1 is not mounted (according to mtab)
ariem@ariem-desktop:~$ umount /dev/sdb
umount: /dev/sdb is not mounted (according to mtab)
ariem@ariem-desktop:~$ 

```

---

