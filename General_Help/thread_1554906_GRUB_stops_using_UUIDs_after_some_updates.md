---
title: "GRUB stops using UUIDs after some updates"
date: 2010-08-17
forum: General Help
---

### Post by alphaamanitin on 2010-08-17
Hello forum friends.

So the other day  I installed some updates, and turned my computer off.   I turned it back on and :mad:.  Gets past grub, puts up the Ubuntu symbol and then nothing.  I recognized this as having had my drive location switched from the past and tried to fix it.  For some reason it has now happened twice where an update removes my use of UUID in grub and replaces it with an incorrect drive location, typically sdc1.  I had a hard time fixing it for whatever reasons.  It did not seem to want to change to sdb1.  I would make the change and then hit tab, which says it saves changes.  Anyway, after a bit that worked.  I booted into Ubuntu and ran sudo update-grub.  Now everything works fine.  So is there a way I can make it so that the file(s) responsible for the drive location in grub cannot be changed?  Even though it has only happened twice I find it really tiresome.

I should mention I am booting Ubuntu from an external hard drive with a crappy Gateway computer.  I have the bios set to boot from USB first-though my bios sucks and this hardly ever happens, I almost always have to interupt the boot process with ctrl+alt+delete, and then hit F10 to go to boot options.  I don't think it makes a difference but I am using Vista 32 bit.   

Thanks,

AlphaA

---

### Post by Cavsfan on 2010-08-17
> **alphaamanitin said:**
> Hello forum friends.

So the other day  I installed some updates, and turned my computer off.   I turned it back on and :mad:.  Gets past grub, puts up the Ubuntu symbol and then nothing.  I recognized this as having had my drive location switched from the past and tried to fix it.  For some reason it has now happened twice where an update removes my use of UUID in grub and replaces it with an incorrect drive location, typically sdc1.  I had a hard time fixing it for whatever reasons.  It did not seem to want to change to sdb1.  I would make the change and then hit tab, which says it saves changes.  Anyway, after a bit that worked.  I booted into Ubuntu and ran sudo update-grub.  Now everything works fine.  So is there a way I can make it so that the file(s) responsible for the drive location in grub cannot be changed?  Even though it has only happened twice I find it really tiresome.

I should mention I am booting Ubuntu from an external hard drive with a crappy Gateway computer.  I have the bios set to boot from USB first-though my bios sucks and this hardly ever happens, I almost always have to interupt the boot process with ctrl+alt+delete, and then hit F10 to go to boot options.  I don't think it makes a difference but I am using Vista 32 bit.   

Thanks,

AlphaA


You could look in the tutorial in my signature. You can set it up and probably fix the UUID issue once and for all.
Let me know if you need anything else.

---

### Post by alphaamanitin on 2010-08-17
I went ahead and marked it as solved.  You gave me a solution and I can't reliably test whether it worked or not due to the problem being very unreliably expressed (twice in 6 months).  

Thanks,

AlphaA

---

### Post by Cavsfan on 2010-08-17
> **alphaamanitin said:**
> I went ahead and marked it as solved.  You gave me a solution and I can't reliably test whether it worked or not due to the problem being very unreliably expressed (twice in 6 months).  

Thanks,

AlphaA

I hope you don't have any more problems! Intermittent problems are the worst kind!
I hope you check out my tutorial when you get a chance if you haven't already, because 
you'll only have one place where there is a UUID and that will be in a custom file that will 
never be updated by anyone but you. And someone asked about making the font bigger 
and I added that to it today too. I did not think there was a way, but found someone on 
this forum knew how to do it.

---

