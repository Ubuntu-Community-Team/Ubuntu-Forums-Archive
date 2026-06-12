---
title: "external HD restore"
date: 2011-07-07
forum: General Help
---

### Post by AstroLlama on 2011-07-07
Hi everybody, hoping the forums can work their magic like they have in the past.

here's the situation: My WD external drive got the tables corrupted from being improperly ejected, I plugged it in and after mounting, The entire folder hierarchy was there, but none of the folders showed any data in them, it seemed that they were empty, but disk still registered being 40%full of data)

After digging around on google/forums I discovered that what might be wrong was a damaged superblock.

I unmounted the external HD and ran gparted to "fix" the problem. It deleted the file names and now after mounting the drive in Nautilus it seems like they have been deleted for real...

I'm normally very careful about my data but now I'm afraid that i've lost everything! i'm still hopeful however because running fsck on /dev/sdb1 it still prompts me to delete "orphaned long entries" which i haven't done yet.

Is there any hope for saving this data?

---

### Post by seawolf167 on 2011-07-07
[TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")*may *help you, preferably this would have been used right after you noticed the bad superblock and you could have attempted to restore a backup superblock. Not sure if/how well it would work now however. 

Good luck!

---

### Post by FakeOutdoorsman on 2011-07-07
Immediately make an image of your disc and use the recovery tools on the image and not your original disc. You can use *dd* (or alternatively *dd_rescue* or *ddrescue*) to make the image.

This is a preventative step to make sure your recovery steps do not cause more harm than good.

---

### Post by AstroLlama on 2011-07-10
Thanks for the replies. I used testdisk and managed to recover a few lost folders, unfortunately none of the important things. But I'm amazed that it worked at all! 

moral of the day, backup your backups! :/

---

