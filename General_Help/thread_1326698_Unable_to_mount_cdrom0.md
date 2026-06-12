---
title: "Unable to mount cdrom0"
date: 2009-11-14
forum: General Help
---

### Post by jomacintosh on 2009-11-14
Getting this error since I installed 9.10  It also comes with the message "mount: special device /dev/scd0 does not exist"

Another person posted a similar thread, but their fix was simple...put disk in drive.

My fix however is not so simple.  My DVD-RW drive does not seem to recogonize anything, CD, DVD, empty or full.

Something interesting, ran sudo  lshw -C disk

My HDD shows up, but not the DVD-RW.

I'd appreciate any input.  I'm also having some other issues, but one thing at a time!

jomac

---

### Post by undecim on 2009-11-14
Does the drive work for booting media (for example, and Ubuntu Live CD)?

---

### Post by jomacintosh on 2009-11-14
Strangely, no.  Not since I installed 9.10

---

### Post by undecim on 2009-11-15
If you cannot boot from the drive, then it's either a hardware problem or a BIOS problem.

The fact that it stopped working when you install 9.10 may just be coincidence. Either that or the last use from installation was the last straw before it wore out.

---

