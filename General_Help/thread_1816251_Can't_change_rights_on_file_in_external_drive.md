---
title: "Can't change rights on file in external drive"
date: 2011-08-01
forum: General Help
---

### Post by lagu2653 on 2011-08-01
I have an external HDD connected via eSata to my lap-top with Ubuntu 11.04 32-bit and Windows 7 dual boot. All files on it have been copied to it using Linux. But I can't change the rights on any of the files using Nautilus or chmod. What am I doing wrong? On my OS disk it works.

---

### Post by AlphaLexman on 2011-08-01
If the partition is formatted to NTFS the permissions and ownership attributes will not save. It would need to be ext2, ext3 or ext4 at minimum.

---

