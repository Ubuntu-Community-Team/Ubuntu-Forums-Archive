---
title: "I screwed up on install, then i deleted the linux partition from windows."
date: 2009-09-18
forum: General Help
---

### Post by travm on 2009-09-18
Stupid eh, anyway without thinking the whole situation through very well I deleted my linux partition from within windows on my dual boot machine.  After i did this i thought, hrmm, i bet i just deleted my boot loader.  Sure enough grub doesnt load anything anymore.
It gives me an error 17.
I want to be able to boot back into windows, and then re-install ubuntu into the "correct" drive.  
The reason I deleted the partition was i partitioned my drive in 40gb, 40gb, and 320 gb.  The 2 40gb drives where intended for the OS, and 320 gb for data.  When i installed ubuntu i somehow screwed up and i ended up with a 40gb data drive and a 320gb ubuntu drive.  This worked for awhile, then i ran out of space.  
The kicker here is I have a significant amount of pictures and other irreplaceable data on my windows partition (and the data partition).  I'm hoping there is an easy way to get my windows install working again so I can start over.  I know I can but dont want to pull the drive and restore data manually.
Thanks
Travm

---

### Post by skatinjj on 2009-09-18
You can try using a windows disc to go into the recovery console and run:

```
fixmbr
```

---

### Post by Redundant Username on 2009-09-18
[Instructions in detail]("http://gaiatech.sorrowind.net/wiki/index.php/Reinstalling_Windows_boot_loader")

---

