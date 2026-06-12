---
title: "Tried install ubuntu (wubi), now Win7 won't boot (noob alert)"
date: 2009-11-28
forum: General Help
---

### Post by CosmoKramer on 2009-11-28
Hey,

So today I decided to try ubuntu on my Win7 x64 bit pc. But I didn't even get to wubi part.
My disk setup:
2 hdds
First: 3 ntfs partitions, one for win7 x64, one for apps, one for games
Second Disk: storage.

I went ahead and tried to create a separate partition for ubuntu by shrinking games partition (on disk one), it asked if I'm sure I want to convert to dynamic (and warning me that system might not boot). Me not knowing what the hell they asked for I foolishly hit yes. It created a partition and converted Win7 disk to dynamic. Now pc won't boot.

Please help, how to I change it back to basic so that I can boot into win7? I'm writing this from kubuntu livecd :D

---

### Post by mikeac72 on 2009-11-28
Download P[artition Wizard Bootable Disk]("http://www.partitionwizard.com/partition-wizard-bootable-cd.html"), and burn it to a CD, make sure you can boot it.

Start your computer with the CD in, right click Disk 1 (the windows one) and click convert dynamic disk to basic disk.

---

### Post by sobol_rz on 2009-11-28
> **mikeac72 said:**
> Download P[artition Wizard Bootable Disk]("http://www.partitionwizard.com/partition-wizard-bootable-cd.html"), and burn it to a CD, make sure you can boot it.

Start your computer with the CD in, right click Disk 1 (the windows one) and click convert dynamic disk to basic disk.

Or maybe put windows cdrom then boot from cd go to repait console > fixmbr , maybe that will be easier...And maybe will help ... ;/
Regards.

---

### Post by CosmoKramer on 2009-11-28
> **mikeac72 said:**
> Download P[artition Wizard Bootable Disk]("http://www.partitionwizard.com/partition-wizard-bootable-cd.html"), and burn it to a CD, make sure you can boot it.

Start your computer with the CD in, right click Disk 1 (the windows one) and click convert dynamic disk to basic disk.
Didn't work, says cannot perform operation or something like that.

Will try repair but doubt it will work as the whole disk is set to dynamic and even offline method didn't work.

Where did I go wrong besides clicking yes to convert to dynamic, should I have installed to a separate physical disk? I followed [http://www.youtube.com/watch?v=Fy1ISEJIv84](http://www.youtube.com/watch?v=Fy1ISEJIv84)  and in the video he didn't have the same prompt as I did.

---

### Post by chicoharv on 2009-11-28
Inside windows you should have let it do its own thing.Only need tp partion if dual system, then let cd do its own thing again, if it can. sometimes you don't have enough free space for this auto partion so proceed only if you know what you are doing or want to replace windows with Linux completely.

---

