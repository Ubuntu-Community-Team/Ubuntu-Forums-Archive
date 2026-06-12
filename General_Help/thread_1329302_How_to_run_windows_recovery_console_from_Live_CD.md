---
title: "How to run windows recovery console from Live CD?"
date: 2009-11-17
forum: General Help
---

### Post by Darvenkry on 2009-11-17
Okay, i have a friends corrupted windows computer. It cant even boot the windows recovery disc, just hangs at  "Setting up hardware or something"
However I have managed to boot unbuntu live cd and can actually mount the harddrive using ntfs-3g. I look into the drive and its empty, yet i look at "properties" and it is actually still full (12.3GB used), just i cant see any files.

Now i believe that the MBR is corrupted. In the windows Recovery Console, i can run things like FIXBOOT and FIXMBR to fix this drive. I need to run this inside the live CD. Any ideas anyone? Otherwise any other way to recover the data on the drive. Theres some important files on there that need to be saved

---

### Post by cybiko123 on 2009-11-17
You can't run the recovery console from Ubuntu, but you can run "testdisk" (you will need to download/install it from Synaptic).

---

### Post by Giblet5 on 2009-11-17
The MBR is the least of the problems with this system.

If the Windows CD won't boot, then the system has hardware problems and you'll have to fix those problems before doing anything else. These are the same hardware problems that caused this problem in the first place.


Start with memtest86 from the LiveCD boot menu. It should run for four hours with zero errors. Don't stop short of four hours and think it's OK...

Once the hardware is fixed, then you can proceed to figure out what, if anything, is salvageable on the Windows disk partition.

If the disk seems to be partially full, but you can't see any files after mounting it, then the MFT (Master File Table) is corrupted.

You can attempt to fix this via ```
sudo ntfsfix /dev/sdXX
``` where XX is the ntfs partition.

I'm doubtful that will work. You'll wind up reinstalling no matter what. The only questions is whether any data can be salvaged. With a trashed MFT, I think not.

---

### Post by Darvenkry on 2009-11-17
Okay, im running the memtest now. I would like to add some additional information bout the problem. My friend said it happened right after he accidentally flicked off the powerpoint before the computer was shutdown properly. The main error is "A disk read error occurred Press Ctrl + Alt + Del to restart" as soon as you past POST.Now, when i try windows recovery disc, it hangs at " setup is detecting your hardware". Just wondering can turning off the computer improperly damage a harddrive???

---

### Post by mixmaster on 2009-11-18
Just a couple of thoughts.

1. Is the disk encrypted? That could give the results you are seeing.
2. If you can't boot the windows CD but you can boot the live CD then there is something strange happening.  Possibly the windows CD is failing because it is trying and failing to access the suspect disk.  I'd be tempted to pull the drive out of the current box and plug it into another and see if you can access it there, either with windows or linux.

There are various tools that will recover files from a disk with a corrupt MFT - google on RAW REVCOVERY - but some of them are expensive and most will be labourous to use.

> Just wondering can turning off the computer improperly damage a harddrive??? 
It is unlikely, but immediately after a power-down is the most likely time for you to notice a problem.

---

### Post by lvlint67 on 2009-11-18
I've seen trippy behaviour from windows recovery disks through the years.

my guess: the harddrive data got corrupted.
solution: 
throw the hardrive into a second computer as a slave.
add another hardrive to recover to
find some opensource freeware recovery programs to recover corrupt data (do NOT write ANYTHING to the corrupt disk)

the short answer is probably: acquire a new m$ boot disk. format and install.
If that doesn't work then there might be hardware problems... start with the disk...

---

