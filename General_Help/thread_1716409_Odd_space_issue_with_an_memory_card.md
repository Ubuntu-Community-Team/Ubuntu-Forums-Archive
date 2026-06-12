---
title: "Odd space issue with an memory card"
date: 2011-03-28
forum: General Help
---

### Post by ~Middle on 2011-03-28
Hello, this is a bit weird and may be hardware related but i thought i would show you guys to see if it was an issue with Ubuntu first. 

Basically i was trying to copy some music onto my PSP's M2 8GB memory card, it said that there was not enough room so i removed some files and the free space value stayed the same. Here is a screen shot that is a little odd:

[IMG]http://k.min.us/ikdhoi.png[/IMG]

Thanks a lot

---

### Post by newbuntuxx on 2011-03-28
This maybe a gui bug. 

run:

```
df -kh /media/folder_where_card_is_mounted
```

Paste the output.

---

### Post by ~Middle on 2011-03-28
My bad it must have just been a user error :S

middle@The-Beast:/media/disk/MUSIC$ df -kh /media/disk
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             7.6G  7.6G   11M 100% /media/disk

middle@The-Beast:/media/disk/MUSIC$ mv DreamTheater/ /home/middle/

middle@The-Beast:/media/disk/MUSIC$ df -kh /media/disk
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             7.6G  7.0G  566M  93% /media/disk

Sorry for wasting your time, but thanks for the command :)

---

### Post by Joe of loath on 2011-03-28
I've had this happen to me, turns out I've not been clearing the trash :lol:

---

