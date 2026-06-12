---
title: "Dual Booting Ubuntu &amp; Mac OSX ?"
date: 2006-05-15
forum: General Help
---

### Post by indiehead on 2006-05-15
Hi, i've got one of the 12" 1.33Ghz iBook's at home with Mac OSX on it and i'd like to dual-boot Ubuntu on it?

Any idea whether the Ubuntu installer will do the partition resizing for me (Mac running HFS+Journaling).

Any ideas?

Played around with Ubuntu 6.06 Flight 7 over the weekend, really impressed, lots of good work done there!

Look forward to any replies on this, all the best,

;)

---

### Post by iball on 2006-05-15
I am not sure if the Ubuntu partitioner will resize, so it might be easier to reinstall OS X, and partition the drive with the OS X installer.  In any case, you will need a 1MB partition at the beginning of the drive for the Yaboot bootloader, and obviously space for OS X and Ubuntu.

On a side note, I have a Powerbook G4, and I have had some problems getting Linux to run on it successfully.  The airport is not fully supported, although I believe the latest Kernel has support for it.  I can not get my powerbook to sleep when I close the lid, so I have to shut it down to carry it around.  It also seems to get warmer than usual when running Linux.  This is just to let you know some problems you may face, but don't be put off.  You may have better success, particularly if you try Dapper instead of Breezy.

I hope this helps
--Ian

---

### Post by indiehead on 2006-05-15
thanks,

i think i might try doing a copy of the laptop's hard drive contents to cd and external hdd (maybe as an image).

i think if i boot my computer with the mac osx installer disk i might be able to resize the main partition and then split it up.

big maybe.

any views on this ?

---

### Post by iball on 2006-05-15
The MacOS X installer may let you resize partitions, but I am not sure.  Backup everything important first, and then try.  If it can resize, try it; if not, just repartition and reinstall OS X.

--Ian

---

