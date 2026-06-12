---
title: "Can' t see Ubuntu drive on Windows XP"
date: 2010-11-24
forum: General Help
---

### Post by Punkristo on 2010-11-24
I have a dual boot with Windows XP and Ubuntu as the main OS. I can see Windows drive on Ubuntu with no problems but if I try to enter Ubuntus drive on Windows XP it doesn't let me. I tried the programs Ext2IFS and Linux reader but I still cant access the drives with them. I added a screenshot of the errors I get with each program.

---

### Post by Neek0 on 2010-11-24
I have not found a way to do this yet.  I just keep a 3rd partition, fat32 or ntfs, which both OS's can read.  I store all of my files that i want to keep, or have access to from both OS's, on there.

---

### Post by James78 on 2010-11-24
Windows doesn't natively support ext, and as for those tools not working, they don't support ext4. From what I've heard, you can use the ext2/ext3 filesystem driver to mount an ext4 drive, but only if you have disabled extents (which are on by default).

---

### Post by wilee-nilee on 2010-11-24
You just need a shared NTFS partition, basically Windows wont read Ubuntu or any Linux without some serious tweaking and maybe changing to a slower partition type for Ubuntu. There are supposed programs that will work, but the word on this forum is a shared partition from the pro's.

---

### Post by bhishan on 2010-11-24
Hope this link will be helpful

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

---

### Post by James78 on 2010-11-24
> **bhishan said:**
> Hope this link will be helpful

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)
It is, but unfortunately it is still subject to what I posted earlier about disabled extents. :(

---

