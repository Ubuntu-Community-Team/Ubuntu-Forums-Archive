---
title: "reformatting a NTFS drive to ext4"
date: 2009-10-31
forum: General Help
---

### Post by donarntz on 2009-10-31
I'm a linux newbie and former windoze user.  I'm trying to reformat my second hard drive (I've tried fdisk, disk utility, and gparted), it says it formatted to ext4 correctly, but I can't get it to mount.  I get this error every time:

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Waaaah please help!  This is driving me nuts!

Don

---

### Post by macaholic on 2009-10-31
How did you go about reformatting it in the first place exactly? What program did you use and what output did it give you?
It doesn't appear that you reformatted it to ext4.

---

### Post by donarntz on 2009-10-31
I created a new ext4 partition. with new partition table.  Gparted says it's a ext4 on /dev/sdb1 but I can't mount it.

---

### Post by wildweathel on 2009-10-31
It sounds to me like this is what happened:

1) You started with NTFS on your second hard drive 
2) You installed Karmic.  The installer detected your NTFS partition.
3) You reformatted that partition to ext4.
4) Karmic is now looking for NTFS, but is finding ext4.  This confuses it.

If that's the case, you need to change the file /etc/fstab so Karmic looks for ext4, not NTFS.  If you're not sure how to do that, post the contents of /etc/fstab and we'll try to help from there.

---

### Post by seeker5528 on 2009-10-31
What wildweathal said seems likely, but just to be sure all the bases are covered. When you say......

> **donarntz said:**
> I created a new ext4 partition. with new partition table.

You deleted the existing partition first so the new one could be created, correct?

Otherwise the partition type of the partition might still be set with the code for NTFS. This can be changed with cfdisk. Not sure how safe it is if you have data on the partition, but it sounds like you don't have data to worry about anyway.

Later, Seeker

---

### Post by delcypher on 2009-10-31
post the output of ```
sudo fdisk -l
``` and tell us which drive in the list it returns you are trying to mount and command you are trying to use to mount it with.

---

