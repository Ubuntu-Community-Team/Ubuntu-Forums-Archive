---
title: "CD/DVD drive automount problem"
date: 2010-08-13
forum: General Help
---

### Post by craigni on 2010-08-13
Does anyone have an idea how to fix this (10.04 Ubuntu x64):

A couple of weeks ago, my CD/DVD drive stopped working.  I'd put in a disk, the light would flash, but it wouldn't appear as a mounted drive.  Thinking the drive had finally died, I bought a new one.  Same problem.

The drive is recognized by BIOS.  I have it as try to mount first in BIOS, and if I put in the Ubuntu boot CD, it boots.

If I put
```
/dev/sr0	/media/cd-dvd	udf,iso9660	defaults	0	0
```
into /etc/fstab, and then mount -a, the drive contents appear and are accessible.  However, as expected, the system chokes on boot if there isn't a CD in the drive, and I have to mount -a manually every time I start the system.  Ugly.

So this is pretty clearly a software OS problem.  Any ideas how I can get the automount for my CD/DVD drive back?

Many TIA,
Craig

---

### Post by ellgor on 2010-08-13
Hi,

Have you tried changing the boot order in the bios, lose it altogether if you have to, let it boot from the hard-drive and change back only when necessary.

Regards, Ellgor.

---

### Post by craigni on 2010-08-15
Thanks, Ellgor.  Unfortunately what that required is to leave a CD in the drive as it booted up (ugly.)  So, ultimately this was a strangely easy fix:

I removed the line referencing the CD/DVD drive from /etc/fstab.

I noticed a lot of old directories in /media.  I deleted them all.

Now, everything is working perfectly.

This is my guess: the OS looks in /media and tries to mount it all.  If it can't, it either takes forever to mount what it can, or just gives up.  So if anyone notices their CD/DVD mysteriously stopping working, first look to see if old directories (representing devices that didn't properly unmount) live in /media, and delete them.

Hope this helps someone in the future,
Craig

---

### Post by Automat2 on 2010-08-17
> **craigni said:**
> Thanks, Ellgor. 
I removed the line referencing the CD/DVD drive from /etc/fstab.

I noticed a lot of old directories in /media.  I deleted them all.

Craig
Craig, did you mean the line you said in the first post?

I had only one hidden file in /media, which I removed. But I'm still having the same problem. The drive still does not mount.

](*,)

---

