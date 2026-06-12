---
title: "format usb hard disc"
date: 2010-05-14
forum: General Help
---

### Post by cyberEl on 2010-05-14
hello,
i have a maxtor 160gb ATA hard disc of a friend and i want to format it in ntfs (windows user)
i have this hdd connected to my computer with an ATA - usb cable and i managed to save his data, 
when i try to format it or even check its filesystem using  the "Disc Utlity" i get this error: 

Device is mounted and no online capability in fsck tool for file system

if i unmount the hard disk (given as device  /dev/sdb) i don't see it anymore on the Disk Utility window

if usufull for any help i use 10.04 lynx and my hard drive, /dev/sda is Sata

---

### Post by dabl on 2010-05-14
Make a Parted Magic Live CD, and boot it, and your project will get way simpler.

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

Use the partitioner to select the connected drive, and format it with NTFS filesystem.

---

### Post by dmurphy787 on 2010-09-16
How can I fix this error if it is the C drive of my computer?

---

### Post by nemiux on 2010-09-16
Hey, I'm not sure what's the command, try searching in the google, cause now my internet is very bad, but it's called mkfs, its for formatting hard drives, search hot to format NTFS with that command, I think it should help

---

