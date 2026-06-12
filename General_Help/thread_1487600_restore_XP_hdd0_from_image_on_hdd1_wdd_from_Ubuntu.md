---
title: "restore XP hdd0 from image on hdd1 w/dd from Ubuntu LiveCD"
date: 2010-05-19
forum: General Help
---

### Post by mscir on 2010-05-19
I would like to keep an iso image of an XP installation on hdd 0 on a 2nd hdd 1, so I can restore hdd 0 using a Ubuntu live CD. I'm a beginner with Ubuntu so I did a little blind searching and found that dd might handle the job, maybe something like:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

ddrescue /dev/hdd0 /dev/hdd1/hdd0image logfile

But I'm wondering if dd is the best tool for the job. Also I read that several windows utilities can compress an image, and ignore empty space, on the partition that the image is being made from, resulting in a smaller image. The backup hdd1 is 10 GB and that should be plenty if empty space is ignored, hdd0 is 160 GB. 

Do any Ubuntu iso creators ignore white space, or optionally compress data? I did a man dd but didn't see these features. 

Also, does it matter what program I use to make the iso image? Is it recommended that the same same program is used to create the image as to  restore from it, or is the iso format standardized enough that it doesn't matter? 

Any suggestions would be appreciated, thanks. 
Mike

---

### Post by john newbuntu on 2010-05-19
For backing up and restoring partitions or whole disks, I use clonezilla.  Clonezilla can be installed as a bootable CD, USB or even on a partition on disk. The interface is not very friendly for a newbie but does its job well.  Looking at the image size, I am guessing it takes only the data and ignores spaces.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by mscir on 2010-05-19
@john newbuntu

Thanks for the recommendation, this looks great. 

[INDENT]I am guessing it takes only the data and ignores spaces.[/INDENT]

"Clonezilla saves and restores only used blocks in the harddisk."

Looking good, thanks very much,
Mike

---

