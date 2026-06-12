---
title: "inc backup changed files"
date: 2011-09-06
forum: General Help
---

### Post by sectshun8 on 2011-09-06
So the girlfriend came up to me today asking about a better way (free being key here as well) to copy all of her work files that have changed in the past 5 weeks from her work external HDD to her home backup drive.  She just did a FULL backup and it took almost 30 hrs.

So basically from one external to another, to only copy the "new" files.

Also, no need to tar or any of that, just to copy... ideas?

---

### Post by lisati on 2011-09-06
*Thread moved to **General Help**.*
Please read the "[Criteria for threads in the Tutorials and Tips section]("http://ubuntuforums.org/showthread.php?t=677396")" before posting there.

---

### Post by haqking on 2011-09-06
> **sectshun8 said:**
> So the girlfriend came up to me today asking about a better way (free being key here as well) to copy all of her work files that have changed in the past 5 weeks from her work external HDD to her home backup drive.  She just did a FULL backup and it took almost 30 hrs.

So basically from one external to another, to only copy the "new" files.

Also, no need to tar or any of that, just to copy... ideas?

*find /path -mtime -35  -ls >filename.txt*

will find all files in location you choose that were modified in the last 35 days and you can change it to ctime though this is change time which includes permissions and pipes it to a filename of your choice

see 
*man find*

once you find all those files you can then copy them.

You could also use the gui/nautilus

to browse the drive and set your columns to show the specific files.

I am not sure if this gives you what you want though.

There must be an easier way, its getting late and i have brain zzzzzz ;-)

---

