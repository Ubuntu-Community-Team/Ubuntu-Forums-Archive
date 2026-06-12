---
title: "HELP !  i formated my ext4 to FAT"
date: 2010-04-30
forum: General Help
---

### Post by Sianegad on 2010-04-30
Trying to make a usb startup disk i formated my 1TB external drive from ext4 to fat32, (stupidest mistake ever) with everything dear to me on it.  I wrote nothing over it, there must be a way to revert but i cant find it (panicking brain probably)

Any one can point me to the right tools, id prefer not having to find professional services.  

i tried some commands to reset a 4GB stick,
sudo blockdev --rereadpt /dev/sdg
sudo dd if=/dev/zero of=/dev/sdg bs=1M count=1
it wont even show up in gparted anymore

the one i care about was mounted as dev/sdf, but is there a chance that those command went further than /dev/sdg in anyway?

---

### Post by Serpher on 2010-04-30
Is this the USB you're trying to format or the 1TB hardrive?

If you want to reformat something that will delete everthing, you have to execute:

```
$sudo mkfs -t ext4 /dev/sd?
```

---

### Post by dino99 on 2010-04-30
[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by srs5694 on 2010-04-30
AFAIK, the only way to recover your system is on a file-by-file basis, using tools like [PhotoRec.](http://www.cgsecurity.org/wiki/PhotoRec) If this was a boot disk, recovering your boot files will be a huge effort, and not a worthwhile one. If you want to recover user files (digital photos, word processing documents, music files, etc.), you may be able to recover most of them, but you may need to do a lot of sorting to figure out what's what.

---

### Post by Sianegad on 2010-04-30
Thx for the pointers, i want to get back my pics  and videos. And lots of stuff. 500GB.  I am buying a second drive tonite and setup backups.    lessons learned.  May  the great coder in thé sky have pity of me.

---

