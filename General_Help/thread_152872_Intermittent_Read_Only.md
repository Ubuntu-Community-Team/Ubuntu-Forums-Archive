---
title: "Intermittent Read Only?"
date: 2006-03-30
forum: General Help
---

### Post by psychomonkey on 2006-03-30
Not sure if I posted in the correct area. I have 1 80GB drive that the o/s is installed on and i have 2 250GB Sata drives setup with software raid. I'm using Webmin to administer this. I've mounted the raid to folder /mnt/e and setup up as read/write with user/group as "nobody". I've then set up a samba share with read/write permissions. I go to my windows xp system and I can see the share. The problem is that, intermittently, I can upload files to my linux server. I start to upload some files, then after a few minutes, I get error "Cannot create or replace: Access Denied/Make sure the disk is not full or write-protected". I even try from a terminal window to see if I can copy a file to the mounted drive and I get error "Read Only Filesystem". I just don't understand why I can start to transfer then all of a sudden the file system turns read only. Does anyone have any suggestions? It would be greatly appreciated.

---

### Post by dcstar on 2006-03-30
[QUOTE=psychomonkey]Not sure if I posted in the correct area. I have 1 80GB drive that the o/s is installed on and i have 2 250GB Sata drives setup with software raid. I'm using Webmin to administer this. I've mounted the raid to folder /mnt/e and setup up as read/write with user/group as "nobody". I've then set up a samba share with read/write permissions. I go to my windows xp system and I can see the share. The problem is that, intermittently, I can upload files to my linux server. I start to upload some files, then after a few minutes, I get error "Cannot create or replace: Access Denied/Make sure the disk is not full or write-protected". I even try from a terminal window to see if I can copy a file to the mounted drive and I get error "Read Only Filesystem". I just don't understand why I can start to transfer then all of a sudden the file system turns read only. Does anyone have any suggestions? It would be greatly appreciated.[/QUOTE]
If the disk has any hardware errors that cause it to unmount and then remount, then it may remount as RO so you have a chance to investigate any problem.

You really need look at any log files generated when the problem occurs.

---

### Post by psychomonkey on 2006-03-30
I haven't noticed any specific error. Is there a specific log file I should be looking for that in?

Also I was thinking I should delete the Array and try to recreate it since I didn't do that this last time I installed Ubuntu. I guess another question would be, should I make the file system ext3 or vfat, just for windows compatability? I dont' have the system dual booted at the moment, nore do I really have plans in the near future to make it dual boot.

---

