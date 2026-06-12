---
title: "fat32 discovery problems"
date: 2011-02-23
forum: General Help
---

### Post by neillyoung on 2011-02-23
I have an external hard drive that is formatted to fat32 that literally takes hours for Ubuntu to recognize is there any way to speed this up?

---

### Post by coldraven on 2011-02-23
Could be that the drive is failing.
Look at System>Admin>Disk Utility, select your USB drive and see if "Smart Data" tells you anything useful.
Does it take as long when plugged into another PC?

---

### Post by neillyoung on 2011-02-24
No. I have a windows 7 laptop that I plug it into quite often and takes no more than 3 seconds for autoplay to pop up and everything works fine.

---

### Post by neillyoung on 2011-02-24
could there be some kind of driver/kernel i need to install for large usb disks to work?
I use smaller (4gb) flash drives with it all the time.

---

### Post by coldraven on 2011-02-25
It should work without any drivers or kernel mods.
I have a 1TB USB drive that came with FAT32 and it worked fine.
However there is a 4GB file size limit with FAT32 so I formated it to NTFS so that I could store DVDs on it.
Maybe someone else can give advice. When you are in Win7 can you run chkdsk on it?
Maybe it just has a corrupt file that confuses Linux.

---

### Post by neillyoung on 2011-02-25
OK thanks i'll try that

---

