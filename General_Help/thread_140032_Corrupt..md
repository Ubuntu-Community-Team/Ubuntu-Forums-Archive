---
title: "Corrupt."
date: 2006-03-05
forum: General Help
---

### Post by TheSundanceKid on 2006-03-05
Hey, I have winXP installed on my system, however it appears my HDD is corrupt and I need to run CHKDSK on it. Is there anyway I can do this through Ubuntu? I've tried mounting the volume, but it doesn't work and says it's corrupt.

---

### Post by wpshooter on 2006-03-05
If you have another computer, try downloading the Ultimate Boot CD.  It should have about every utility you should ever need.

---

### Post by TheSundanceKid on 2006-03-05
Hmm my laptop is in for repair at the moment, how could I burn the CD using my Ubuntu Live Disc, as I only have one Disc Drive?

---

### Post by TheSundanceKid on 2006-03-05
Or could I make a USB drive bootable and run an MS-DOS bootdisc off there??

---

### Post by lcg on 2006-03-05
[QUOTE=TheSundanceKid]Hey, I have winXP installed on my system, however it appears my HDD is corrupt and I need to run CHKDSK on it.[/QUOTE]
You could boot your XP install CD and start the recovery console. You can then run 'chkdsk c:' (or whatever drive letter) from there.

[QUOTE=TheSundanceKid]Is there anyway I can do this through Ubuntu? I've tried mounting the volume, but it doesn't work and says it's corrupt.[/QUOTE]
According to the [Linux NTFS project's status web site]("http://www.linux-ntfs.org/content/view/15/29/"), there is 'ntfsfix', which should "[...] force Windows to check NTFS at boot time". I don't know if it is on the Live CD, though.

HTH,
Lars

---

