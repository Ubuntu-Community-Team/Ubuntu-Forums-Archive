---
title: "No partitions showing in partition manager"
date: 2012-02-15
forum: General Help
---

### Post by cerberos1 on 2012-02-15
I'm trying to install ubuntu on a harddrive that previously had XP on it. When I got the disk I added partitions for future use but now when I try the ubuntu partition manager or gparted no partitions show up.

I have some data I don't want to lose on /dev/hda6, otherwise I'd just format the drive. I've been trying to fix this for days to no avail.

Here's the output from fdisk -lu
```
Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/hda2        40966144    64403455    11718656   83  Linux
/dev/hda3        64405504    76122111     5858304   83  Linux
/dev/hda4        76122144   976784129   450330993    f  W95 Ext'd (LBA)
/dev/hda5        76124160    81930223     2903032   82  Linux swap / Solaris
/dev/hda6        81931563   935802314   426935376    7  HPFS/NTFS

```Here's the output from sfdisk -d
```
# partition table of /dev/hda
unit: sectors

/dev/hda1 : start=       63, size= 40965687, Id= 7, bootable
/dev/hda2 : start= 40966144, size= 23437312, Id=83
/dev/hda3 : start= 64405504, size= 11716608, Id=83
/dev/hda4 : start= 76122144, size=900661986, Id= f
/dev/hda5 : start= 76124160, size=  5806064, Id=82
/dev/hda6 : start= 81931563, size=853870752, Id= 7
```

---

### Post by jerrrys on 2012-02-15
You can use the live cd to copy over your files to maybe a flash drive.

---

### Post by Mark Phelps on 2012-02-15
Is your problem that the Ubuntu Installer does now show any partitions?  Or is it that GParted doesn't show partitions?

If the first, it's because you already have the maximum number of Primary partitions, so the installer won't provide the option to create any more.

---

### Post by oldfred on 2012-02-15
It looks like your extended partition is beyond the end of the drive.

> drive: 976773168
Extend:  976784129

Fixparts - Repair broken partition tables (not overlapping issues) 
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by cerberos1 on 2012-02-15
Thanks for your replies.

> **jerrrys said:**
> You can use the live cd to copy over your files to maybe a flash drive.

There's too much data for a flash drive.

> **Mark Phelps said:**
> Is your problem that the Ubuntu Installer  does now show any partitions?  Or is it that GParted doesn't show  partitions?

If the first, it's because you already have the maximum number of  Primary partitions, so the installer won't provide the option to create  any more.

Both Ubuntu installer and GParted don't show any partitions, they both show the drive as unpartitioned free space.

> **oldfred said:**
> It looks like your extended partition is beyond the end of the drive.

Fixparts - Repair broken partition tables (not overlapping issues) 
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

I've backed up the partition table to a usb drive, I'll try fixparts and report how I get on.

---

