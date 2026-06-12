---
title: "After power loss files not displayed but still using space"
date: 2011-05-31
forum: General Help
---

### Post by vanzippee on 2011-05-31
After a power outage my external hard drive that I use to serve a DLNA server with content lost all the files.
The parent directories are still displayed, but there is nothing inside them, and I cannot write anything into them. (creating any file in them does not work.)
I assume that I have a corrupted drive but I was hoping to find a way to recover the content. Most of it is backed up, but I have become a bit lazy in the past month, and have not backed up so there are a number of videos I don't want to lose.
It seams odd that the directories show up, but the files don't. The drive properties also show that the correct amount of the drive space is taken up (for the videos to be present) so I haven't reformatted because I assume that will wipe out all traces of the data.

---

### Post by linuxinstalledfromhdd on 2011-05-31
Try this:

[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

### Post by prshah on 2011-05-31
> **vanzippee said:**
> After a power outage my external hard drive that I use to serve a DLNA server with content lost all the files.

What format is your partition? Eg, ext4, ntfs, vfat, etc?

I suggest that you just conduct a disk check. If that fails, you can use testdisk or photorec to repair the partition information or recover individual files.

diskcheck```
#first, ensure that the target partition in Umounted
fsck /dev/sdXY
```

Replace /dev/sdXY with the correct device for your external partition. Note that this will not repair anything, just run a check. If the results seem OK, add the "-a" switch to automatically fix errors.

fsck should automatically detect the filesystem and run the correct type (eg, ext2/3/4, fat, etc). 

Please post back with results.

---

### Post by timgood on 2011-05-31
It's worthwhile looking in the directory /lost+found to see if the files are there (they must be somewhere if they are still taking up space). I've found files there before in similar situations. Sometimes the files extensions are missing and the files need to be renamed, but they should work just fine if they are there.

Good luck...

---

### Post by vanzippee on 2011-06-05
I wish I had found photo rec before I recovered the files. I broke down and tried MS file check. It returned all the files, but all 2300 of them were named FILE####.CHK. So I spent the past couple days renaming all of the files that were recovered.](*,) 
Next time (I hope it never happens) I will know to use photorec, everyone says it is works. 
On the prevention side I am shelling out the $100 to get a 2nd drive and setting up raid.;)

---

### Post by prshah on 2011-06-05
> **vanzippee said:**
> I wish I had found photo rec before I recovered the files. I broke down and tried MS file check. It returned all the files, but all 2300 of them were named FILE####.CHK.

Heh, photorec does the same. RECUP.DIR.1 (Every 500 files, a new RECUP.DIR.x+1 directory is created.). All the filenames are removed too. However, it usually preserves the extentions; and you can also set filters for the recovery process (Eg, recover only MPG,MP3,JPG,JPEG etc files).

This is why I always recommend photorec as a last option  (eg, disk check preferred).

---

