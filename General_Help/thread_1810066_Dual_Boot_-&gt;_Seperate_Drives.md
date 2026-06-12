---
title: "Dual Boot -&gt; Seperate Drives"
date: 2011-07-22
forum: General Help
---

### Post by iCeD00D on 2011-07-22
Good afternoon. Is it possible to copy just my Ubuntu 11.04 partition on a dual-boot system to a seperate disk? If so, how ... I'm finding the need for a larger drive. Tks....

---

### Post by ~!geek!~ on 2011-07-22
I m afraid its a bit tough!! If u r able to do it successfully, please let me know by sending a message to me. :)

---

### Post by iCeD00D on 2011-07-22
Argggh!  I was hoping I could just use Clonezilla, pick the partition and then mod the MBR some how but maybe your right, might be tough ....

---

### Post by altometer on 2011-07-22
You bet it is. Go get a copy of Hiren's UBCD. the newest version right now is 14.  Use one of the linux based disk cloning programs on there to create a disk image from the linux partition.

Then simply do a image to partition rewrite onto the new drive. You will need to fix grub because the locations of your installs will be broken. Use ```
Sudo update-grub
```

Finally, extend the partition by booting to an ubuntu live CD and use gparted to extend your windows and linux partitions on each drive.

If you have any questions I have personally done exactly what you are asking about successfully. I can provide more detail on any specific part rather easily.

Alternatively, if you are not partial to re-installing ubuntu, Just do that. It would be a heck-of-a-lot faster to just back up your ubuntu data, install ubuntu on the new drive, then extend the windows partition to fill up the rest of the old drive.

---

### Post by seawolf167 on 2011-07-22
> **iCeD00D said:**
> Good afternoon. Is it possible to copy just my Ubuntu 11.04 partition on a dual-boot system to a seperate disk? If so, how ... I'm finding the need for a larger drive. Tks....

Sure - its quite easy, boot up off [Clonezilla]("http://www.clonezilla.org"), image that particular partition, then restore it to your new hard drive.

You have to do two things after:

[LIST]
[*]restore Grub by following [these]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2") instructions
[*]resize your ubuntu partition by booting off a livecd, then using GParted to resize the partition
[/LIST]

---

### Post by iCeD00D on 2011-07-22
Thanks much for the replies... I appreciate the help ! ... I'll yell if something goes wrong.. but then again been having a little bit of the 'charlie brown' luck lately :lolflag:
 
Tks again ...

---

### Post by seawolf167 on 2011-07-22
Once you get it all working, mark the thread as solved :P Or... tell us what isn't working so we can help out!

---

