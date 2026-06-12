---
title: "Change partitions permissions"
date: 2006-06-13
forum: General Help
---

### Post by XTend on 2006-06-13
OK.Here's my problem. I have an 80 gb Maxtor HDD. I have 4 partitions in total. The C: drive is for WinXP,the d:is for personal data, and 5.5 gb of hdd space is alocated for Ubuntu (with 512 mb swap size).
The problem is that I need to make available at boot the d: drive because it's the biggest partition and I need space to save some things. The ideea is that I can only edit things in D: only with gksudo nautilus. But I need to acces it from a normal window. If I try to mount it I can't acces it because I don't have the permission.
Could anyone tell me how to change permissions ?
10x.

---

### Post by Sutekh on 2006-06-14
You should read this link and follow the instructions. It will show you how to mount Windows partitions with the ability to access them.  

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

If they are formatted with a FAT filesystem, you will be able to write to them.  If they are formatted with a NTFS filesystem, you will only be able to get read and execute access.

---

