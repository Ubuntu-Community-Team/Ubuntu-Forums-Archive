---
title: "Installing Ubuntu on an external hard drive question"
date: 2009-12-09
forum: General Help
---

### Post by Eevee. on 2009-12-09
I have successfully installed ubuntu onto an external hard drive, which was not that difficult.  

However I do not know how to install ubuntu onto just a portion of the external hard drive, while allowing it to let me use the other portion to store files in windows.


Is this possible and if so what do I have to do?  I know I'm just an annoying one poster asking for help but I plan to introduce myself tomorrow after class.  Just wanted to post this now in hopes that I get a few replies tomorrow to work with.  

Thanks in advanced  0=]

---

### Post by Vishnu V on 2009-12-09
You can use gpart to resize the partition and create a partition with file system FAT32 or NTFS so that you can access this from windows

If you are going to install ubuntu again .During the partitioning option select "specify partition manually " and create 1 partition for windows and other for installing ubuntu

---

