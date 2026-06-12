---
title: "two swap partitions?"
date: 2012-04-12
forum: General Help
---

### Post by gandalf3 on 2012-04-12
I'm new to Linux, and am running Ubuntu 11.10.
i installed Ubuntu while i had 1GB of ram, but i knew I'd probably get some more so i made a 3GB swap partition.
now i have my 3GB of ram, but on restarting from hibernation it acts like there's not enough swap space..
in the disk utility it looks like the installer made a different partition for swap than the one i made.. here's a screen shot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215917&stc=1&d=1334258039[/IMG]
my question is, how do i go about deleting the currant swap partition and telling it to use the other one as swap? (without destroying anything?)
and is this even what it seems to be? did something else happen?
any help appreciated..:confused:

---

### Post by PhantomTurtle on 2012-04-12
First you need to get gparted,
```
sudo apt-get install gparted
```
right click on the new swap partition and click swapon, if it says swapoff instead then it is activated already(then you can just skip this part). Next right click on the old swap partition and click swapoff. If it says swapon instead, then it is already deactivated. After it is deactivated just delete it.
It is recommended to have 2 x RAM for swap partition(so if you have 1GB RAM, make a 2GB swap partition).

---

### Post by ajgreeny on 2012-04-12
Please post back here the output of these four commands
```
sudo fdisk -l
sudo blkid -cu
cat /etc/fstab
free -m
```

---

### Post by oldfred on 2012-04-12
You need to check fstab to see which swap it is mounting and change to the larger one's UUID.

# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

### Post by gandalf3 on 2012-04-13
> **ajgreeny said:**
> Please post back here the output of these four commands
```
sudo fdisk -l
sudo blkid -cu
cat /etc/fstab
free -m
```

sudo fdisk -l
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00ba00ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40d96571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     6294023     3145988   82  Linux swap / Solaris
/dev/sdb2         6295550   156301311    75002881    5  Extended
/dev/sdb5         6295552   154204159    73954304   83  Linux
/dev/sdb6       154206208   156301311     1047552   82  Linux swap / Solaris

```sudo blkid -cu
```
/dev/sda1: UUID="186087CA6087ACD6" TYPE="ntfs" 
/dev/sdb1: TYPE="swap" 
/dev/sdb5: UUID="f87cd4d8-d0fa-4312-af07-0ca84582ddf0" TYPE="ext4" 
/dev/sdb6: UUID="f3e0f74b-bdaa-4789-81ce-e0cc892d0f34" TYPE="swap" 

```cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=f87cd4d8-d0fa-4312-af07-0ca84582ddf0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f3e0f74b-bdaa-4789-81ce-e0cc892d0f34 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```free -m
```
             total       used       free     shared    buffers     cached
Mem:          3025       1082       1942          0         86        397
-/+ buffers/cache:        598       2427
Swap:         1022          0       1022

```> **PhantomTurtle said:**
> First you need to get gparted,
```
sudo apt-get install gparted
```right click on the new swap partition and click swapon, if it says swapoff instead then it is activated already(then you can just skip this part). Next right click on the old swap partition and click swapoff. If it says swapon instead, then it is already deactivated. After it is deactivated just delete it.
It is recommended to have 2 x RAM for swap partition(so if you have 1GB RAM, make a 2GB swap partition).
is that (2x ram size for swap space) completely necessary? 
i have somewhat limited hard drive space but i do have enough do it, just what would happen if i only had something like, 500MB more swap than ram?

> **oldfred said:**
> You need to check fstab to see which swap it is mounting and change to the larger one's UUID.

# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

Thanks..
is this way of doing it any safer than any other ways?


anyway, thanks for all the replies! :)
i'll post back how things go..

---

### Post by oldfred on 2012-04-13
Your blkid did not show a UUID for sdb1 which is strange. What does gparted then say about that partition. You cannot edit fstab with a new UUID for sdb1 if it does not have one, but it should be automatically generated when you created it.

If gparted does not create a UUID this may.

sudo tune2fs -U random /dev/sdb1

---

### Post by gandalf3 on 2012-04-13
thanks..
i don't know if this relevant or not, but i created the partition with the partition editor in the installer.

---

