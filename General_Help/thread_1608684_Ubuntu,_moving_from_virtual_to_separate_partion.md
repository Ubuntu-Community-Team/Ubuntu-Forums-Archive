---
title: "Ubuntu, moving from virtual to separate partion"
date: 2010-10-29
forum: General Help
---

### Post by DirtyPC on 2010-10-29
Ubuntu 10.10 64bit, moving from virtual to separate partion

I have finally decided ubuntu is for me. I no longer want or need xp, i would just like to know how to put ubuntu separate and get rid of xp. Please be very specific yet simple, as I dont wanna f*** this up.
/Thanks/

---

### Post by matt_symes on 2010-10-29
Hi

What exactly are you trying to do? 
Use your existing vm file and converting it from a VM file to the drive? (This is meant to be possible but hard, i have never tried it)
Do you want a fresh install on the drive overwriting existing XP and VM?

BTW my advice would be the latter

Kind regards

---

### Post by DirtyPC on 2010-10-29
> **matt_symes said:**
> Hi

What exactly are you trying to do? 
Use your existing vm file and converting it from a VM file to the drive? (This is meant to be possible but hard, i have never tried it)
Do you want a fresh install on the drive overwriting existing XP and VM?

BTW my advice would be the latter

Kind regards
I want to make ubuntu independant, and get rid of xp and have ubuntu as my main OS on its own partion, but i want to keep my files.. something like LVPM

---

### Post by matt_symes on 2010-10-29
Hi

Never used LVPM before so the only advice i will give is clone you drive first using clonezilla or some such.

This tutorial looks alright.
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I will bail out and leave advice to someone who has used it.

Kind regards

---

### Post by cpmman on 2010-10-29
I have done this on my Compaq CQ61 where I had wubi 10.10 in Windows 7 and whilst it is possible it is complex.  Click on the WubiGuide in my signature to see the various options.

Firstly take a backup so if anything goes wrong you can restore and start again.  If you are sure you don't want XP then make a note of your XP licence number so that if you later want to you can load a legal version in a VM (Virtualbox or similar).

Secondly, whatever you decide take a separate copy of your wanted files - from /home/username down including . (hidden) directories&files which you can load back to the new installation.

Follow the instructions from the WubiGuide to complete if you choose that way.

I shall recommend you to use a live cd to install using the whole disc.  You may wish to consider separate / , /home , swap partitions to aid subsequent upgrades or leaving some disc space unallocated (in an extended partition) for additional installs if you have a large disc.

---

### Post by DirtyPC on 2010-10-29
> **cpmman said:**
> I have done this on my Compaq CQ61 where I had wubi 10.10 in Windows 7 and whilst it is possible it is complex.  Click on the WubiGuide in my signature to see the various options.

Firstly take a backup so if anything goes wrong you can restore and start again.  If you are sure you don't want XP then make a note of your XP licence number so that if you later want to you can load a legal version in a VM (Virtualbox or similar).

Secondly, whatever you decide take a separate copy of your wanted files - from /home/username down including . (hidden) directories&files which you can load back to the new installation.

Follow the instructions from the WubiGuide to complete if you choose that way.

I shall recommend you to use a live cd to install using the whole disc.  You may wish to consider separate / , /home , swap partitions to aid subsequent upgrades or leaving some disc space unallocated (in an extended partition) for additional installs if you have a large disc.
thanks, also didnt realise LVPM worked under 64 bit, no matter. I've just got my 500gb seagate hard drive for my ubuntu and a little 80gb one for windows, just in case, thanks anyway
/thread closed

---

