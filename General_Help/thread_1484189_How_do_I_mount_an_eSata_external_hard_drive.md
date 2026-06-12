---
title: "How do I mount an eSata external hard drive?"
date: 2010-05-15
forum: General Help
---

### Post by maelstrom209 on 2010-05-15
I have an eSata external hard drive connected to my desktop running Ubuntu 10.04 LTS. I searched around for some info on how to mount an eSata external hard drive and was not successful. Most of the posts were talking about stuff after the drive has been mounted. Thanks in advance for any tips on this.

---

### Post by scouser73 on 2010-05-15
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by quadproc on 2010-05-15
> **maelstrom209 said:**
> I have an eSata external hard drive connected to my desktop running Ubuntu 10.04 LTS. I searched around for some info on how to mount an eSata external hard drive and was not successful. Most of the posts were talking about stuff after the drive has been mounted. Thanks in advance for any tips on this.
Mounting an eSATA drive is just like mounting any other kind of a drive; that may be why your search did not produce anything useful.  The mount command deals with the logical organization of the disk and the command does not care about the physical or electrical characteristics of the device.  A CDROM mounts like a floopy disk which mounts like a hard disk which mounts like an external, plugged in eSATA disk.

I usually specify the file system type when I mount an external device.  That provides a bit of self-checking in case I plugged in an incorrect device.  I would normally do something like```
 sudo mount -t ext3 /dev/sdi /y
```Of course, you will need to alter the ext3, sdi, and y to suit your setup.

Please remember to umount the drive when you are finished with it.

quadproc

---

### Post by lykeion on 2010-05-15
I use scsiadd to hotplug my eSATA drive, like it is described in this thread:

[http://ubuntuforums.org/showthread.php?t=907124]("http://ubuntuforums.org/showthread.php?t=907124")

---

### Post by jtappin on 2010-06-03
> **quadproc said:**
> Mounting an eSATA drive is just like mounting any other kind of a drive; that may be why your search did not produce anything useful.  The mount command deals with the logical organization of the disk and the command does not care about the physical or electrical characteristics of the device.  A CDROM mounts like a floppy disk which mounts like a hard disk which mounts like an external, plugged in eSATA disk.

quadproc

Unfortunately this is no longer true at the user level.

As of Lucid (and recent versions of Arch), an eSATA drive is considered an internal drive rather than removable. So unlike a USB drive, it's non-trivial to make it mountable without needing an administrator password.

---

