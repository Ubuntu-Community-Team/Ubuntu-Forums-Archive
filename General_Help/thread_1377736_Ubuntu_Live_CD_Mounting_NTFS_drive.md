---
title: "Ubuntu Live CD: Mounting NTFS drive"
date: 2010-01-10
forum: General Help
---

### Post by afbase on 2010-01-10
I'm having an issue mounting my ntfs hard drive using the 9.10 live cd

Here are my drives, one 80 gb, NTFS, hard drive and my thumbnail USB
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1248b54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab8eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1967    15794144+   c  W95 FAT32 (LBA)

```I tried mounting /dev/sda1 like so 
```

sudo mount -t ntfs-3g /dev/sda1 /mnt/windows
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```
/mnt/windows is an existing folder location

I have some malware (Malware Defense) on the NTFS partition.  I cannot go into safe mode because of the VPN setup.  It simply will not let me have access with my user name and password.

Any help is greatly appreciated.

---

### Post by michy99 on 2010-01-10
It looks like you need to run a chkdsk on it. Do you have a xp or vista cd?

---

### Post by afbase on 2010-01-10
> **michy99 said:**
> It looks like you need to run a chkdsk on it. Do you have a xp or vista cd?
Yes I do have an XP installation disk.  I'll try that. and see what happens.

---

### Post by afbase on 2010-01-11
> **afbase said:**
> Yes I do have an XP installation disk.  I'll try that. and see what happens.
I used my XP installation disk, went to recovery mode.  I ran chkdsk and I recieved an error saying the volume's directory could not be enumerated or something of that nature.  I just tried defragmenting the drive and it will not work properly :(

I deleted Malware defender and its Registry successfully.  At the moment I'm getting a horrible error on IE6.  I'm going to upgrade it to IE8.

---

### Post by aysiu on 2010-01-11
So can we assume just going to Places and selecting (with your mouse) the drive doesn't mount it?

---

### Post by garvinrick4 on 2010-01-11
You have no Linux installation, you are using a 16 gig flash that you have used USB creator
or something close with 4 gig of persistence that you use as linux system and want to use
as a Live CD for your Windows XP installation. I do not believe anything is wrong with your
idea except you have somehow made a mess of XP.  Seems like a Windows problem, not a dual boot, not a Linux, not a Grub. You need a person that is a XP user not a Linux user. Maybe there are better forums out there for your need. But you might get lucky and find someone who
is capable with a XP recovery disc. If you have 10 gig to use as a Linux partition you could make
a dual boot and enjoy linux the way it was meant.  Good luck to you.

---

### Post by afbase on 2010-01-12
> **garvinrick4 said:**
> You have no Linux installation, you are using a 16 gig flash that you have used USB creator
or something close with 4 gig of persistence that you use as linux system and want to use
as a Live CD for your Windows XP installation. I do not believe anything is wrong with your
idea except you have somehow made a mess of XP.  Seems like a Windows problem, not a dual boot, not a Linux, not a Grub. You need a person that is a XP user not a Linux user. Maybe there are better forums out there for your need. But you might get lucky and find someone who
is capable with a XP recovery disc. If you have 10 gig to use as a Linux partition you could make
a dual boot and enjoy linux the way it was meant.  Good luck to you.

Yes it is definitely a windows problem. I will resort to windows forum resources. :(

---

