---
title: "Backup HDD of New PC Before First Boot"
date: 2009-11-10
forum: General Help
---

### Post by clevertomato on 2009-11-10
I will receive my new laptop any day now (a Lenovo IdeaPad Y550). It will come with Windows 7 64-bit and a myriad of other junk I presume. Even if I were going to use Windows 7, the first order of business would be to do a clean install, but I plan on installing Ubuntu as my only OS.

I would, however, like to make a snapshot / image / [whatever you want to call it] of the drive exactly as it is from the factory in case I ever need to put that back on it. Yes, I may be able to reproduce that in the future by using discs that come with the PC ... if they come with the PC, but I'd like a way to just preserve the contents of the hdd before my first [hdd] boot.

Is there a good method to do this using a Live CD that does not write anything to the hdd and creates a restorable chunk of the actual data (not the full disk size or partition size)? I'm not interested in buying software and would even prefer something that is built-in to Linux as opposed to a software package, but as long as it's fairly simple, free, and reliable, I'll consider it.

---

### Post by andrewc6l on 2009-11-10
If you have another machine on a network (or a spare hard drive that will fit), you might want to try the System Rescue CD at sysresccd.org - and in particular, sfdisk and partimage as described here:
[http://sysresccd.org/Sysresccd-manual-en_System_software](http://sysresccd.org/Sysresccd-manual-en_System_software)

---

### Post by Commander_Keen on 2009-11-10
You could always ghost the box.
You could use the windows 7 backup application.
You can ask the Vendor if they already have something like this on the HD system.

---

