---
title: "Cloning hard drive that will soo die"
date: 2012-07-10
forum: General Help
---

### Post by dwlamb on 2012-07-10
Not a  happy day! Woke up this morning and discovered my hard drive is in imminent prospect of dying according to SMART.  Found [this link]("http://ubuntuforums.org/showthread.php?t=2011739") and ran the SMART utilities using 
```

sudo -i
apt-get install smartmontools
smartctl -a /dev/sdc

```According to the report, the drive might die in the next 24 hours.  The machine is off and I am using a different PC until I get a replacement drive.

The drive, 1TB, is partioned into 3, 2 for the system and 1 in NTFS to keep things compatible in Windows (dual boot). I  plan to use the live CD to clone the replacement.  Is there any chance I might lose data cloning, even if the drive sounds like it is still healthy? 

I'm religious about back-ups, but cloning the drive will be faster than the tedium of restoring back-ups.

---

### Post by lindsay7 on 2012-07-10
I would use Clonezilla to do the job. This works like a live linux cd. It works much easier if you use the same size drive to clone your current drive.

---

### Post by Double.J on 2012-07-10
[FONT=Arial]plus one to clonezilla; probably the easiest way to go!

There's no need to worry about data lose through the clonezilla route - it's just a front end to several linux commands such as dd.

If you're really really obsessive about this you run the dd command from the ubuntu terminal with a smaller block size and you'd also need options such as conv[/FONT][FONT=Arial]=sync and noerror. The smaller block size (as low as 1K) makes it even more accurate, but would literally take a day or so on 1TB. With a failing drive this is a LOT of work for the drive. Personally I'd take the chance to grab the most important files off it, then use clonezilla to clone the drive... just incase it goes before clonezilla finishes. 

When cloning the drive it will do a block by block clone, so the image you make... or drive you clone to will be identical; partitions, bootloaders, mbr, the works :)
[/FONT]

---

### Post by dwlamb on 2012-07-10
Thank you both for the help.  In a few days' time, I hope to share the results.

---

