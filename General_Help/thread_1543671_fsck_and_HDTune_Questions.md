---
title: "fsck and HDTune Questions"
date: 2010-08-01
forum: General Help
---

### Post by Vimmander on 2010-08-01
If I simply type fsck in the terminal of a LiveCD, does it only check the linux file systems on my drive, or will it also check other partitions (such as XP, Vista, and Windows 7...I currently dual boot with 7)? I'd rather let the Windows chkdsk command take care of Windows. As a side note to disk checking, I ran an HDTune disk check in Windows, and it checked the whole drive, Windows 7 AND Ubuntu. Is that dangerous? __________________

---

### Post by mcduck on 2010-08-01
If you simply type "fsck" it will complain and tell you to define what partition you want to check ("fsck /dev/sda1", for example).

If you use "fsck -a" it will check the partitions that are defined in /etc/fstab (so that's not really useful on a live-CD).

So no, it will not try to check your windows partition unless you specifically tell it to do so. Not that it would make any difference, as far as I know there is no fsck.ntfs so fsck will just skip the check anyway.

HDtune doesn't care about the file system, it checks the disk itself, not the filesystems. So unless you use some of it's secure erase functions it's not dangerous.

---

### Post by hal8000 on 2010-08-01
> **GrogTheDreamer said:**
> If I simply type fsck in the terminal of a LiveCD, does it only check the linux file systems on my drive, or will it also check other partitions (such as XP, Vista, and Windows 7...I currently dual boot with 7)? I'd rather let the Windows chkdsk command take care of Windows. As a side note to disk checking, I ran an HDTune disk check in Windows, and it checked the whole drive, Windows 7 AND Ubuntu. Is that dangerous? __________________


You dont want to run fsck on any mounted filesystems.
In addition the filesystem check has many extensions and you would
normally apply it to the partition under question.
Example

fsck.ext3 /dev/sda6
(check ext3 filesystem on partition 6)

fsck.cramfs /dev/sdb1

checks cramfs on first partition of second sata hard drive etc.

Windows cant check linux filesystems, it only recognises fat32 and ntfs.

From the live cd:
sudo fdisk -l 
will show you your partitions on all hard drive(s)

---

### Post by Vimmander on 2010-08-01
What would the difference be between running a disk check on /dev/sda4 (Extended) and the individually listed linux partitions?  In GParted, the linux partitions are under Extended.  Better yet, should I do Extended AND the three partitions I made?

---

### Post by mcduck on 2010-08-01
> **GrogTheDreamer said:**
> What would the difference be between running a disk check on /dev/sda4 (Extended) and the individually listed linux partitions?  In GParted, the linux partitions are under Extended.  Better yet, should I do Extended AND the three partitions I made?

The difference is that you *can't* check an extended partition.,

Fsck checks file systems, not partitions. Extended partition doesn't have a file system.

---

