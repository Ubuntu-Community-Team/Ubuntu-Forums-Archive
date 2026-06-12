---
title: "Swallow Windows"
date: 2012-03-13
forum: General Help
---

### Post by Serson_Person on 2012-03-13
My Windows 7 Partition isn't working.  I've had no grief about it, figure installing Ubuntu solo would be better anyways... only problem is all of the files I have, my music, videos, etc.

Is there a way to convert the Windows partition into one that I can combine with Ubuntu?  Expanding Ubuntu to use the whole disc, but still keep my files?

---

### Post by linoseros on 2012-03-13
you can use is as it is no need for any change ;)

---

### Post by Mark Phelps on 2012-03-13
> **Serson_Person said:**
> My Windows 7 Partition isn't working.  I've had no grief about it, 

Having "no grief" means that it's been giving you NO problems -- probably NOT what you intended to convey, right?

> Is there a way to convert the Windows partition into one that I can combine with Ubuntu? 
NOT without losing all the existing data.  Reformatting a partition to change the filesystem effectively erases the data -- but does not actually WIPE it from the drive.

>  Expanding Ubuntu to use the whole disc, but still keep my files?
Again, NO.  Expanding Ubuntu would require removing the existing Windows partition -- again, effectively erasing the files.

Have you gone to the Windows 7 forum (sevenforums.com) with your problems? And did they fail to help you or to solve your problems?

You might want to consider that before you completely give up on it.  If your existing Win7 install won't boot or won't run, they may be able to get it working well enough so you can salvage your data before you erase the partitions.

---

### Post by Serson_Person on 2012-03-14
> **Mark Phelps said:**
> Having "no grief" means that it's been giving you NO problems -- probably NOT what you intended to convey, right?


I just meant I wasn't grieving it's loss.  There was no sensation of panic, no over-whelming desperation to get it back.

Yeah.  I may fix it later, and just forget about it.  I know I can still access all of the files with Ubuntu anyways, I just wanted to make the drive less messy.

---

### Post by dino99 on 2012-03-14
ubuntu (linux) automatically access the ntfs partition via ntfs-3g, nothing to worry about :) create a /home partition for your data.

---

### Post by cortman on 2012-03-14
> **Serson_Person said:**
> I just meant I wasn't grieving it's loss.  There was no sensation of panic, no over-whelming desperation to get it back.

Yeah.  I may fix it later, and just forget about it.  I know I can still access all of the files with Ubuntu anyways, I just wanted to make the drive less messy.

Copy all the files you want to keep from the Win7 partition onto an external HD (or, if your Ubuntu partition is big enough, simply copy them over to the Ubuntu partition in Ubuntu), and remove the Win7 partition with GParted. Then you can expand the Ubuntu partition to use up all the new empty space.
But as always BACK UP both your Win7 files and your Ubuntu files before you attempt any partitioning work.

---

### Post by Serson_Person on 2012-03-14
> **cortman said:**
> Copy all the files you want to keep from the Win7 partition onto an external HD (or, if your Ubuntu partition is big enough, simply copy them over to the Ubuntu partition in Ubuntu), and remove the Win7 partition with GParted. Then you can expand the Ubuntu partition to use up all the new empty space.
But as always BACK UP both your Win7 files and your Ubuntu files before you attempt any partitioning work.

My problem right now is that my back up hard drive bit the dust :/

I'll probably just wait until I get paid and buy a new one, sigh... lol.  

Thanks everyone! :)

---

