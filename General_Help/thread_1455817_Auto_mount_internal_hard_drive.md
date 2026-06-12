---
title: "Auto mount internal hard drive"
date: 2010-04-16
forum: General Help
---

### Post by seadart on 2010-04-16
I have 2 internal hard drives. Drive 1 has 3 partitions; Windows 7, ext4 and swap, the ubuntu system in the ext4 is ofcourse accessible. Drive 2 is my data disk and I would like it to mount automatically when I load Ubuntu. I have seen a reference to PySDM and got that running but what I see does not match what is in the description. I believe I should have hda as disk 1 with hda1, hda2 and hda3 as the partitions. Then I should have hdb with hdb1 being the data partition. I should also see the cdRom.

All I see is sda with sda1, sdc with sdc1, and sdb with sdb1; in that order. All type ntfs!!!!

Could somebody explain to simple old me what is going on and how I get my 2nd internal disk to mount like the first disk at start-up. (the second disk is not in etc/fstab)

see attachment

---

### Post by nikhilbhardwaj on 2010-04-16
post the output of 
```

sudo fdisk -l

```

---

### Post by seadart on 2010-04-16
Here you go:-

chris@chris-ubuntu:~$ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x386ff7d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       53078   426342048+   7  HPFS/NTFS
/dev/sda2           53079       60801    62034997+   5  Extended
/dev/sda5           53079       60480    59456533+  83  Linux
/dev/sda6           60481       60801     2578401   82  Linux swap / Solaris

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x7102e793

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1     1453521   732574552+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17440c91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
chris@chris-ubuntu:~$ ^C
chris@chris-ubuntu:~$

---

### Post by bwhite82 on 2010-04-16
They have an 's' instead of an 'h' because they are SCSI disks (ie sda instead of hda). Do you know which disk is your Data disk? What file format?

Once you know which one (sda1)? You can append your fstab to include it. But first you'll need to find its UUID. You can find it by:

> sudo blkid -o full /dev/**sda1** (change bold according to your disk)

Then add it to your fstab. Example of fstab line:

> UUID=**ec17d2c5-1a15-4764-828a-bdf232eeb83f** /               ntfs    errors=remount-ro 0       1 (change bold to your disk's UUID)

---

### Post by mk1w86 on 2010-04-16
First, could you please post the output of:

```
sudo fdisk -l
```

The best way to auto mount your partition would be to add it to the fstab.

To do this I would first create a permanent mount point in /mnt by running:

```
sudo mkdir /mnt/[mount point name]
```

Then run:

```
sudo chown [your username]:[your username] [mount point name]
```

Next add the partition to your fstab, for a guide on doing that have a look here:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The reason you see sda, sdb etc. and not hda, hdb is simply because Ubuntu now uses sd instead of hd for all hard drives. ;)

---

### Post by seadart on 2010-04-16
Hi,

The sdc is an external drive - I do not expect to autu mount that. The one I need is sdb.

---

### Post by bwhite82 on 2010-04-16
It looks like SDC is your data disk then? If so, change the values of my post above to sdc.

---

### Post by seadart on 2010-04-16
mount point name - would that be sdb in this case or is it just a name I choose?

Thanks for the help!

---

### Post by nikhilbhardwaj on 2010-04-16
if you want to mount the partition at boot and have read write permissions as an ordinary user you may want to read this:
[HTML]http://my.opera.com/nikbhardwaj/blog/automatically-mounting-windows-partitions-at-boot-up[/HTML]

---

### Post by bwhite82 on 2010-04-16
Right, so look in my first post and replace the bold to: /dev/sdb

---

### Post by mk1w86 on 2010-04-16
> **seadart said:**
> mount point name - would that be sdb in this case or is it just a name I choose?

Thanks for the help!

It can be any name you choose, a mount point is a directory, you will then specify it in fstab after the UUID or name of the partition. ;)

e.g. UUID=ec17d2c5-1a15-4764-828a-bdf232eeb83f /mnt/chris_data ntfs errors=remount-ro 0 0

---

### Post by seadart on 2010-04-16
Thanks everyone, I'll go away and play with this - carefully! If you don't hear from me on this topic again then it is solved. Otherwise I'll get back.

(But why did Pysdm not work?)

---

### Post by nikhilbhardwaj on 2010-04-16
is that /dev/sdb a windows partition
or is it a new hard disk without a filesystem

if its is the latter then you'll need to create a filesystem on it before trying to mount it

---

### Post by mk1w86 on 2010-04-16
> **nikhilbhardwaj said:**
> is that /dev/sdb a windows partition
or is it a new hard disk without a filesystem

if its is the latter then you'll need to create a filesystem on it before trying to mount it

It is a Windows partition as you can see here:

> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17440c91

Device Boot Start End Blocks Id System
/dev/sdb1 1 60801 488384001 7 HPFS/NTFS

---

### Post by Morbius1 on 2010-04-16
Good heavens !

This is the way it was done in the olden days. 

* STEP 1: Find out how the system sees your partitions - DONE*
> [COLOR=Blue] /dev/sdb1               [/COLOR]1       60801   488384001    7  HPFS/NTFS*STEP 2: Create a mount point for your partition to live in*

Open **Terminal**
Type **sudo mkdir [COLOR=DarkGreen]/media/WinData[/COLOR]**

* STEP 3: Add a line to /etc/fstab/ to have this partition mount at boot:*

```
[COLOR=Blue]/dev/sdb1[/COLOR] [COLOR=DarkGreen]/media/WinData [COLOR=Black]ntfs[/COLOR][/COLOR] defaults,nls=utf8,umask=007,gid=46 0 0
```*Step 4: Mount them by executing the new fstab*

Open **Terminal**
Type **sudo mount -a**
[B]
umask=007[/B] is user mask at it will allow owner (first digit) and group (second digit) read write access and everyone else ( third digit) will have no access.
**gid=46** is group id. It's set to 46 ( plugdev). All local login users are members of the plugdev group by default - and that includes you.

---

### Post by eriktheblu on 2010-04-16
Don't forget to 
```
sudo mount -a
```
after changing /etc/fstab

---

### Post by seadart on 2010-04-16
I am instructed to mark this 'solved' under 'thread tools'. I only see 'printable version' under thread tools???

---

### Post by tstduke on 2010-05-19
I had the same issue with NTFS drives. Installing "NTFS configuration tool" from the software centre fixed the problem.

---

### Post by old_codger on 2010-08-10
> **Morbius1 said:**
> Good heavens !

This is the way it was done in the olden days. 

Can someone just explain to me WHY we had to change? I assume it's got something to do with the change to ext3 or ext4 or something and standardising across the partition types but even so... the addition of a meaningless multi-character device ID is hardly the kind of thing to make life easier for people coming from windoze or apple, is it!

---

