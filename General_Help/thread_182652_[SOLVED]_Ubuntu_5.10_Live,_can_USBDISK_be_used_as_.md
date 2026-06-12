---
title: "[SOLVED] Ubuntu 5.10 Live, can USBDISK be used as work space?"
date: 2006-05-26
forum: General Help
---

### Post by susanto on 2006-05-26
I am trying to set USBdisk(flash) as my working space with Ubuntu Live 5.10 DVD. Unfortunately it failed with error messege, can not create symlink. 
I wonder if this mean USBDisk is only a backup drive and can not be used as
live working space ?
Note, no problem to create it on the desktop.
Thanks for any comment.

---

### Post by badrinarayan on 2006-05-26
I believe you have a FAT partition on your USB Disk, which does not support symbolic links. You can use your USB Disk as your "working space" (say your home directory), if you
* can do without symlinks or
* can repartition so you have an ext3 file system in it.

---

