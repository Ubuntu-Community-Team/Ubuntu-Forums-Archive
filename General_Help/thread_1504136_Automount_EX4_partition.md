---
title: "Automount EX4 partition"
date: 2010-06-07
forum: General Help
---

### Post by Frogster on 2010-06-07
Good Evening everyone,

This has been covered loads but for some reason I seem to always end up completely messing it up!

I wish to get sdb3 to automount as "Little Empty", very happy to use the command line. 

Seems like all I have to do is tell Ubuntu that "sdb3" exist, create the directory and edit fstab! "Simple"  Hmmm 

Any help would be greatly appreciated.

```
keith@Ernie:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=41e85f65-b770-4045-8202-6cc71e955794 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=a87e36fc-a20a-424c-b5bd-91b3c8e8d37b /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=1d330ddf-4192-4a0e-87b7-f18eed3f0d89 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
keith@Ernie:~$ 
keith@Ernie:~$ sudo fdisk -l
[sudo] password for keith: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004010a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a6431cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2             244        1459     9765888   83  Linux
/dev/sdb3            1459       19458   144571392   83  Linux

```

---

### Post by Frogster on 2010-06-07
Any help please

---

### Post by Frogster on 2010-06-08
Please

---

### Post by Frogster on 2010-06-08
Bump

---

### Post by stlsaint on 2010-06-08
Please post the output of the following commands:

```
sudo fdisk -l (thats a lowercase L)
```
and
```
sudo blkid
``` (this shows the uuids needed to properly configure fstab.

---

### Post by Frogster on 2010-06-08
Here you go thanks for the reply

```
keith@Ernie:~$ sudo fdisk -l
[sudo] password for keith: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004010a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a6431cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2             244        1459     9765888   83  Linux
/dev/sdb3            1459       19458   144571392   83  Linux
keith@Ernie:~$ sudo blkid
/dev/sda1: LABEL="Big Empty" UUID="6cb0d2c0-ed4b-430d-85f3-f0211242f37c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="1d330ddf-4192-4a0e-87b7-f18eed3f0d89" TYPE="swap" 
/dev/sdb2: UUID="a87e36fc-a20a-424c-b5bd-91b3c8e8d37b" TYPE="ext4" 
/dev/sdb3: UUID="41e85f65-b770-4045-8202-6cc71e955794" TYPE="ext4" 
```

:p

---

### Post by stlsaint on 2010-06-09
im not fully understanding what it is you are trying to do. You have sdb3 mounted with / (root) but you say you want it to mount as "Little Emtpy"!! Is this to mean that you want the partition sdb3 to be empty and used for data or as a seperate partition? If so than you need to partition of some hdd space as this "data partition" and give it a label of "Little Empty". This can be done via gparted which should already be installed on your system but the partition will not be sdb3. It will be given uuid and number.

---

### Post by pizza-is-good on 2010-06-09
Is 'little empty' just the name that you want to give to the volume???

---

### Post by Frogster on 2010-06-10
Thank you all for the replies.

All I want is for the partition sdb3 to be automounted and labelled "Little Empty". 

When I installed 10.4 I split the disk in to swap, home and the remainder. I didn't realise that Ubuntu wouldn't automatically mount the partition.

But I now see what I have done. I should have made sdb3 my home directory and sdb2 my root directory! Hmmm live and learn.

So now I have to resize the partitions with Gparted and then sort out automounting sdb2.

---

