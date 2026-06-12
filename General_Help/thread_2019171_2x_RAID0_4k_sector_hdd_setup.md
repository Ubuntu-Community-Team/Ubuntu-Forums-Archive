---
title: "2x RAID0 4k sector hdd setup"
date: 2012-07-07
forum: General Help
---

### Post by Red Kelly on 2012-07-07
HI all

I am rather confused and am looking for clarification.

What I have:
4x 2TB hhd with 4k sectors (WD20EADS)
1x 160GB hhd for OS
motherboard Asus M4A78T-E

I have been using 2 of the 2TB hard drives for media and backup, so they are full and I wont to keep that data.

I have disconnected the old drives and was attempting to create one 4TB raid0 partition with the new drives and worked through the motherboards manual and activated the on-board chip but in Ubuntu they still show as 2 separate drives?

What I'd like to do:
1x 4TB partition Media
1x 4TB partition Backup
1x 160 for OS

Is it possible to create a 4TB raid0 partion with the 2 new drives, copy over the 2TB of info in the old hhd and then merg the old hhd in a raid0 setup?


Questions:
Is this possible? 
what is the best format for media and backup partitions?
How do I work RAID in Linux?

EDIT: using Ubuntu 10.04LTS 64bit

---

### Post by steeldriver on 2012-07-07
You might just need to install the dmraid package to get your current system to recognize the mobo RAID 

HOWEVER I would recommend you do some more research before going down that route - maybe Linux soft RAID would be a better solution here - or if you are just looking to combine drives into a single volume (not really making use of the write striping of the RAID0) then just creating a non-RAID LVM volume might be a better idea

---

### Post by Gompa on 2012-07-07
i would not use wd green disks in raid, from the wd website :

Critical: WD Caviar Black, Caviar Green, and Caviar Blue hard drives are not recommended for and are not warranted for use in RAID environments utilizing Enterprise HBAs and/or expanders and in multi-bay chassis, as they are not designed for, nor tested in, these specific types of RAID applications. For all Business Critical RAID applications, please consider WD’s Enterprise Hard Drives that are specifically designed with RAID-specific, time-limited error recovery (TLER), are tested extensively in 24x7 RAID applications, and include features like enhanced RAFF technology and thermal extended burn-in testing.
[http://wdc.custhelp.com/app/answers/detail/a_id/996/](http://wdc.custhelp.com/app/answers/detail/a_id/996/)

---

### Post by steeldriver on 2012-07-07
^^^ good point, I didn't look at the drive type

fwiw I am running a RAID0 mirror using WDC Greens - however I have disabled the idle timer using idle3-tools

[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

---

