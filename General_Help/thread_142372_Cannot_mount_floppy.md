---
title: "Cannot mount floppy"
date: 2006-03-10
forum: General Help
---

### Post by OMRebel on 2006-03-10
I followed the how to in one of the threads I found in here, but whenever I went to update pmount, it said I already had the newest installed.  Whenever I try to mount the floppy, I get:

Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount


Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by hajk on 2006-03-10
The newer pmount package that you need is in backports, so edit your /etc/apt/sources.list and uncomment the backport lines. Then running 
"sudo apt-get update" and "sudo apt-get upgrade" will install the newer pmount for you (and may be a few other upgrades as well).

---

### Post by StefanoCole on 2006-03-13
Maybe, in fstab file you have to change > /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

with > /dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

Stefano

---

### Post by OMRebel on 2006-03-13
Thanks guys!  That got it working.  :)

---

### Post by SteveHoffmanUK on 2006-03-20
I have a similar but slightly different problem in mounting my floppy.

When I have a floppy inserted that contains a file with a .doc extension, I can mount it with no problems and read/write the files successfully. But when I insert a floppy containing files with extensions of .tar.bz2 and .deb (modem driver), I get the message:

[I]Mount Error: Unable to mount the selected volume.
[Show more details:] mount: I could not determine the filesystem type, and none was specified 
[/I]
I don't yet have Internet access on this machine (that's why I am trying to input my modem driver), so I can't update anything with the bug fixes mentioned at the start of this thread.

My fstab:
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

The floppies are created on an XP machine, if that's relevant.

I'm a noob, so I don't understand why a hardware command like 'mount' is affected by the content of the particular file in the device I'm trying to mount.

Can you suggest what I can do to be able to access the contents (modem driver) on my floppy?

---

### Post by StefanoCole on 2006-03-20
Try the following command from terminal: > sudo mount -t vfat /dev/fd0 /media/floppy0

Stefano

---

### Post by SteveHoffmanUK on 2006-03-20
Stefano: thanks for the quick response. I get:

> /dev/fd0 is not a valid block device 

---

### Post by SteveHoffmanUK on 2006-03-20
Sorry, sorry! Hadn't inserted the floppy disk in the device. Successfully mounted. Many thanks.

---

