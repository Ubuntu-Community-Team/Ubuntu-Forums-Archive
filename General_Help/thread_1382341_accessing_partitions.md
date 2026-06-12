---
title: "accessing partitions"
date: 2010-01-15
forum: General Help
---

### Post by wetworks on 2010-01-15
Hi,

I was installing ubuntu 9.10 and i kinda partition my HDD. next thing i knew, my windows was removed. i now have 2 partitions. One with ubuntu in it, the other partition I cannot access. this partition is a swap area.

I am hoping that the partition did not delete my work. Thus please advise if I could access the other partition from ubuntu.

I am new to this OS, thus bear with me :|

FYI,
I have tried mounting the other partition with "sudo mount -t ext2/ dev/sda2 /mnt /hd" and received this error instead: "mount: wrong fs type, bad option, bad superblock on dev/sda2, missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg | or tail or so"

---

### Post by john newbuntu on 2010-01-15
If you think the other partition is the swap area, boot into Ubuntu first and list the contents of /etc/fstab.
Also list the output of "sudo fdisk -l" and "sudo blkid"

---

### Post by wetworks on 2010-01-16
> **john newbuntu said:**
> If you think the other partition is the swap area, boot into Ubuntu first and list the contents of /etc/fstab.
Also list the output of "sudo fdisk -l" and "sudo blkid"

Hi John,

Thanks for replying back. Below are the output from the commands from the 2 "sudo" you were asking me to do.

As for /etc/fstab, the permission was denied.

--------------------------------------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44ad43cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         889     7139328   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         890       14480   109166400   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3           14481       19457    39977280    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           14481       19248    38291368+  83  Linux
/dev/sda6           19248       19457     1685848+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfbd05ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
laptop@laptop:~$ sudo blkid
/dev/sda1: UUID="603866CA38669F32" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="6bbc02a1-8864-42b6-bf62-ca2be510c02f" TYPE="swap" 
/dev/sda5: UUID="2c0dcc4e-dbcb-44ef-b489-8c2a3b07a8c8" TYPE="ext4" 
/dev/sda6: UUID="a9a9f358-d547-4a96-8ebd-bc66ee3139e1" TYPE="swap"

-----------------------------------------------------------------

Alternatively, I have a 2.5" case. Was thinking of taking out the HD and put it into the case..plug it into a PC..backup my file...(which is the thing I need now)...then format the whole HD..

Do you think when I plug it into the PC, I am able to retrieve files from that particular partition?

---

### Post by john newbuntu on 2010-01-16
I am confused at the sizes of /dev/sda1 and /dev/sda2.  Swap looks huge and windows so small.  So, I guess something is messed up.  I would first suggest correcting your partitions using a utility called testdisk.  Once that is done, you will have to do a file system checking on at least /dev/sda5.
Please wait on a second opinion before you do anything.

---

### Post by wetworks on 2010-01-16
> **john newbuntu said:**
> I am confused at the sizes of /dev/sda1 and /dev/sda2.  Swap looks huge and windows so small.  So, I guess something is messed up.  I would first suggest correcting your partitions using a utility called testdisk.  Once that is done, you will have to do a file system checking on at least /dev/sda5.
Please wait on a second opinion before you do anything.

I suspect /dev/sda1 could be the windows vista recovery pre-set by lenovo. while /dev/sda2 was my windows 7(upgrade from Vista) which after partition got screwed.

---

### Post by john newbuntu on 2010-01-16
If no one has a better suggestion, see if "testdisk"/photorec can be used to repair your /dev/sda2 partition:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by wetworks on 2010-01-18
> **john newbuntu said:**
> If no one has a better suggestion, see if "testdisk"/photorec can be used to repair your /dev/sda2 partition:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)


Appreciate the help John. I have managed to use testdisk to retrieve my lost data. Afterwhich, I have formatted my HD.

Mod, you can close topic.

---

