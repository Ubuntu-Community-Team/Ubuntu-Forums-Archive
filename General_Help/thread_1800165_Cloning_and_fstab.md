---
title: "Cloning and fstab"
date: 2011-07-08
forum: General Help
---

### Post by PeterOakland on 2011-07-08
I cloned one of my hard drives to another, using Acronis True Image Home 2011.
In the process, of course, fstab got copied verbatim from old to new.
I then, using a livecd on a flash drive, mounted the new drive, went into fstab and rewrote the UUID's, using the numbers I'd gotten previously by doing sudo blkid.
Now, the new drive had the UUID's revealed by that command.
Then, I used boot-repair, from yannubuntu, to make that drive bootable, since it wasn't after the cloning and after the fstab rewrite.
The drive is bootable, and it's mountable from a flash drive, or from the old drive.
I can access files either way.
Question:  the fstab file on the new drive still has the old numbers, yet when I ran boot-repair, it apparently changed the UUID's for sectors 1 and 5 on the new drive.
fstab seems to be irrelevant at this point, yet everything I read about it indicates that it is not only relevant, but necessary.
I don't understand how I can be accessing the drive when the fstab contains UUID's that are no longer pertinent to any hardware on my system.
I'd appreciate any enlightenment (on this subject) anyone can provide.
(Actually I'd appreciate any enlightenment whatsoever, but that's probably for some other forum to take on.)
Thanks.

---

### Post by gizmo720 on 2011-07-08
fstab is not (and cannot be) used to mount the root filesystem. The location of the root filesystem is passed as a boot parameter to the kernel by the bootloader. Once it has mounted the root filesystem, the kernel reads fstab, and quietly fails at mounting the partitions mentioned in it.

---

### Post by PeterOakland on 2011-07-09
Pardon me, please, my ignorance -- but how would I know/notice that quiet failing?
What would be different?
Right now, when I boot that cloned drive with nothing else in the system, and then go to Disk Utility, it shows all the partitions, and clicking on each one doesn't betray anything amiss that I can see.  And as I indicated, my vision might well be flawed -- I'm not that familiar with the workings of fstab.

Thanks very much.

---

### Post by gizmo720 on 2011-07-09
Fstab only contains instructions for what to mount when the system boots. Once booted, programs look in the /dev directory to see all partitions, regardless of fstab. Any errors it encounters while trying to mount to the partitions in fstab should be recorded in /var/log/syslog

---

### Post by PeterOakland on 2011-07-10
Thanks for that explanation.
I kind of understand.  What I don't get, though, is how I would see anything that would let me know that my fstab was incorrect, given that I can boot from that drive (with the incorrect UUJID's in fstab), access it from the original drive, and from a flash drive using LiveCD.

---

### Post by gizmo720 on 2011-07-10
If you aren't looking for problems, the only indication of a bad fstab is that something doesn't get mounted automatically when the computer boots. If an error is encountered while trying to mount something in ftsab, the line that gave the error is ignored, and the system moves on to the next line. If your system is working, I wouldn't worry about a bad fstab. These errors are probably recorded in /var/log/syslog. 

Any system other than the one fstab is in sees it only as a text file, (And for the most part, after boot the system it is in also sees it a a normal text file)

---

