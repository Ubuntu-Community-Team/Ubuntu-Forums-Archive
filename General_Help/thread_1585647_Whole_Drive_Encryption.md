---
title: "Whole Drive Encryption"
date: 2010-09-30
forum: General Help
---

### Post by kellyapproved on 2010-09-30
On my Windows 7 box, I use bitlocker to encrypt the entire drive.  Unlocking is done with a USB key + PIN.

Is there something similar for Ubuntu that I can use?

---

### Post by Herman on 2010-09-30
Yes, if you download and install from the Ubuntu 'Alternate' CD, you may install Ubuntu ina LUKS encrypted file system. 
The letters 'LUKS' are an acronym for 'Linux Unified Key Setup, and here's a wikipedai link about it, [Linux Unified Key Setup]("http://en.wikipedia.org/wiki/Linux_Unified_Key_Setup").

Ubuntu Community docs gives this link, [EncryptedFilesystemLVMHowto]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto"), 

which includes a choice of either this,
[Encrypted LVM for Root, Home and Swap using Manual Partitioning]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/")


or this,
[Encrypted LVM with Root and Swap using Guided Partitioning]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml"):  This howto explains how to use the guided encrypted LVM partition mode  to automatically partition an entire disk (erasing all data on the  drive) and create an LVM with a root and swap partition. No manual  partitioning or setup is necessary. 

and finally, here is a link to my own web pages about how I did it,  [Ubuntu Encrypted Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html")

Regards, Herman :)

---

