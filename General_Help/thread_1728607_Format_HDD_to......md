---
title: "Format HDD to....."
date: 2011-04-13
forum: General Help
---

### Post by greatermold on 2011-04-13
Hey there - 

Currently duel booting win7 and ubuntu.  Currently have media on a 1.5 Terr formatted in ext4.  Obviously Win cannot read/write to this.  I want it to.  

Im going to move everything over to different drives, reformat to NTFS, then throw everything back on it achieving read/write for both platforms.

Is this my best option or can someone suggest a better solution?

Thanks

---

### Post by K_45 on 2011-04-13
You could kill Windows (do you really need it?) but otherwise I can't see an alternative.

---

### Post by rosencrantz on 2011-04-13
Reformatting is the thing to do. There are ext drivers for Windows, but those are a bit of a pain and, personally, I wouldn't trust them further than read-only.
Some people prefer FAT32 because it's supposed to be faster, but it has the 4GB file size limit and also some limits as to how many files you can put in one folder (I hit that limit once with 20,000 image files with relatively long file names, so it's probably not that relevant for you).
I'd use NTFS like you were planning. If it's an external drive, your writing speed is going to be limited by the USB bus anyway.

---

### Post by seawolf167 on 2011-04-14
For dual booting and being able to read/write to the same drive I'd just as soon stick with NTFS. Just make sure that the things you are reading/writing to the drive do NOT include any backups (i.e. rsync) of your Ubuntu system (unless they are images from something like Clonezilla).

If you format with GParted you'll also want to get

```
sudo apt-get install ntfsprogs
```

---

