---
title: "How to make automount able to recognize vfat or ntfs?"
date: 2009-08-04
forum: General Help
---

### Post by aspora.isernia on 2009-08-04
Hi all,
I've a (hope not stupid) question: I've added in **/etc/fstab** a line to make automount able to mount my flash USB pendrive. The line is the following:
```
/dev/sdb1	/media/dir	vfat	user,noauto,exec 0 0 
``` When I connect a USB hard drive with an ntfs partition, automount tries and fails to mount it as a vfat partition, and I have to manually mount it with the option **-t ntfs**.
Now the question: is it possible to make automount able to recognize if a disk is ntfs or vfat? Something like guess-n-try-again?
Thanks in advance for any hint.
Cheers

a.i :)

---

### Post by martinbaselier on 2009-08-04
If you add a line to your fstab automount will no longer work. fstab is not meant for removal media. 

It should normally work automatically. If you run ubuntu, gnome-automount ought to mount the usb stick automatically. It doesn't matter if it's formatted in ntfs, fat or ext2/ext3/ext4.

---

### Post by aspora.isernia on 2009-08-04
Wow. You're absolutely right. I've removed the line and now it works like a charm. Many thanks!!
Cheers

a.i :popcorn:

---

