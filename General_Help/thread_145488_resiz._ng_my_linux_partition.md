---
title: "resiz. ng my linux partition"
date: 2006-03-16
forum: General Help
---

### Post by njzillest on 2006-03-16
i just deleted fedora 4 from my computer because i perfer UBUNTU.

now i have 155 gigs of free hard drive space, i used Gparted to format that free space.


what should i format it as (currently ubuntu is ext3) so should i make it an extended partition or a primary?


thanks for the help 

much aprreciated

---

### Post by taurus on 2006-03-16
If Ubuntu is the only OS on your machine, then format it as ext3 since it's safer with journal thing.  However, if you want to share that with Windows (read/write), then better format it as fat32 (or vfat).  Doesn't really matter whether it's a primary or an extended partition but go with primary then...

---

### Post by njzillest on 2006-03-16
i have windows on a DB 


but i heard that vfat and fat32 was very very buggy when its on windows

(ie it reads the wrong memory)h

---

### Post by njzillest on 2006-04-05
Ubuntu is my only OS, shoudl i make it extended or primary? my current partition is ext 3, should i format it as ext3??


thanks

---

### Post by Al3xanR0 on 2006-04-05
[QUOTE=njzillest]Ubuntu is my only OS, shoudl i make it extended or primary? my current partition is ext 3, should i format it as ext3??


thanks[/QUOTE]
 If Ubuntu is the only OS on the drive then primary is fine, however, if you intend on creating additionally partitions or segregating for example / /boot /home /usr directories then I recommend making your /boot primary then place all other partions on an extended. Ext3 is fine just keep in mind that fsck becomes cumbersomb the larger the drive is. If you have a HDD that is in excess of 40GB I recommend using ReiserFS. On a Final Note --notice all recommendations begin with "I" others may recommend other solutions it is a matter of preference. Furthermore, it also depends on what you have and what your needs are.

---

