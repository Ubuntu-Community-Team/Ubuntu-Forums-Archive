---
title: "Good file system"
date: 2006-06-22
forum: General Help
---

### Post by playmobiel on 2006-06-22
Hi , i'm looking for a good file system for a 250gb external (usb) hard disk, but linux and windows need to read/write it without problems, i know fat32 does this, but fat32 doensn't support files larger than 4gb, and i want to store files that are larger than 4 gb , so if there is a filesystem that windows/linux can write/read without additional drivers installations and stuff , could somebody tell me ?

Thanks

---

### Post by mips on 2006-06-22
ext2 or ext3. You can access it from windows with the ext2ifs driver.

---

### Post by playmobiel on 2006-06-22
yes , i know, but isn't there any fs that you can use on both system without installing a driver?

---

### Post by aysiu on 2006-06-22
Your magical filesystem doesn't exist.

Use FAT32 or use Ext3 and install [http://www.fs-driver.org](http://www.fs-driver.org) on Windows.

---

### Post by playmobiel on 2006-06-22
damn, i already tought so , then i'm going to learn how to program a fs :D

---

