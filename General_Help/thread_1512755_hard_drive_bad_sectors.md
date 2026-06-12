---
title: "hard drive bad sectors"
date: 2010-06-18
forum: General Help
---

### Post by spiky001 on 2010-06-18
Hi I,m in need of some help, I have a windows laptop that is showing bad sectors on hard drive, I ran Ubuntu live cd that also reported bad drive, is there a way to **fix/mark/or partition,** the drive so it is usable, either from Windows or from linux live cd.
 The drive is a sata drive if it makes any difference, Losing data is not a problem
Any more info needed I can get
Would appreciate some help plz

---

### Post by gdonwallace on 2010-06-18
Bad sectors are an indication that the drive most likely will die.  Depending on how many, it could be days, weeks, months or longer.  

I have a machine at work that is showing a couple bad sectors, but I have been running it for over a year with no problem.

As far as patitioning the bad sectors, that most likely can't be done; as the sectors could be on different sections of the hard drive.

If you are concerned about the drive crashing, and loosing data is not an issue; I would suggest a reinstall of the OS (Windows or Ubuntu).  Either way, as you reformat, those bad sectors will be marked, and the OS will not use them.  Ubuntu takes it a step further after install.  It will periodically scan the Hard Drive, if it finds any data on bad sectors it will move that data and then mark the sector and not use it.  Can't say with 100% certainty if Windows does this, but I think it does; only you may have to do a manual scan of the hard drive.

Good Luck.

---

### Post by spiky001 on 2010-06-18
Is there a built in operation within windows that will scan drive before new install or is that likly to be part of install?

---

### Post by dcstar on 2010-06-19
> **spiky001 said:**
> Hi I,m in need of some help, I have a windows laptop that is showing bad sectors on hard drive, I ran Ubuntu live cd that also reported bad drive, is there a way to **fix/mark/or partition,** the drive so it is usable, either from Windows or from linux live cd.
 The drive is a sata drive if it makes any difference, Losing data is not a problem


Modern hard drives relocate bad blocks themselves, if there are still bad blocks then the drive will essentially be unusable because it obviously has massive problems.

You can only "mark" bad blocks within a partition, and if you delete that partition then you lose all that info.

---

### Post by spiky001 on 2010-06-19
I ran chkdsk from windows it did mark the bad sectors as not to use, will have to try it today see if it still crashes thks for help
Glad I use linux

---

