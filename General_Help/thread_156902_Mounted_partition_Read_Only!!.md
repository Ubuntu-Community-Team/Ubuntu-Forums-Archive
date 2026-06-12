---
title: "Mounted partition Read Only!!??"
date: 2006-04-08
forum: General Help
---

### Post by priyaaank on 2006-04-08
Hi,
I am a newbie to ubuntu and linux as well.. I migrated from Windows and three of my partitions are in FAT32 format...
Unfortunately, they are still being mounted as read only... how can I make sure, that I am able to rw on them?
I tried to look up fstab.. but the value is "defaults" which I assume that mounts partitions in read-write format!
I have my user, in root group also... 
Please help me out, as I am running out of space in rieser partition.... and I badly need a fix for this... :( 

Thanks in advance

---

### Post by dcstar on 2006-04-08
[QUOTE=priyaaank]Hi,
I am a newbie to ubuntu and linux as well.. I migrated from Windows and three of my partitions are in FAT32 format...
Unfortunately, they are still being mounted as read only... how can I make sure, that I am able to rw on them?
I tried to look up fstab.. but the value is "defaults" which I assume that mounts partitions in read-write format!
I have my user, in root group also... 
Please help me out, as I am running out of space in rieser partition.... and I badly need a fix for this... :( 

Thanks in advance[/QUOTE]
Here is a FAT32 line from my fstab that works, try and use it as a base for yours:
```
/dev/hda1       /c		vfat    	umask=000,noatime,auto			0       0
```

If you have further problems, do a forum search and you should find many threads with information that will be of use.

---

### Post by sands on 2006-04-08
[http://www.ubuntuguide.org/#mountunmountfat](http://www.ubuntuguide.org/#mountunmountfat)

---

### Post by sands on 2006-04-08
During every startup of ubuntu, fat filesystem check may occur..(It happened in my case)
To cancel that use ctrl+c and then ctrl+d during that process..

---

### Post by OffHand on 2006-04-08
[http://makuchaku.info/amnesty/#windows](http://makuchaku.info/amnesty/#windows)

---

