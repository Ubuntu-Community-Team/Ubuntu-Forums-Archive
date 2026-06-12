---
title: "Filesystem checking a FAT32 usb drive?"
date: 2006-04-24
forum: General Help
---

### Post by kidcharles on 2006-04-24
I've got a problem with a FAT32 usb drive, I can mount it fine but there seems to be a corrupt folder that causes Nautilis to lock up when I try to access it, and even locks up a console when I try to access it with the command line. Is there a way to do a filesystem check and repair on this FAT32 drive under Ubuntu? Thanks.

---

### Post by mjziegle on 2006-04-24
There are a series of file checking utitilities fsck.<file system type>

Do a man fsck to make sure you understand.

Unmount your partition and then use 

fsck.vfat -d <path to bad files> </dev/sda or whatever you usb drive is>

-Matt

[QUOTE=kidcharles]I've got a problem with a FAT32 usb drive, I can mount it fine but there seems to be a corrupt folder that causes Nautilis to lock up when I try to access it, and even locks up a console when I try to access it with the command line. Is there a way to do a filesystem check and repair on this FAT32 drive under Ubuntu? Thanks.[/QUOTE]

---

