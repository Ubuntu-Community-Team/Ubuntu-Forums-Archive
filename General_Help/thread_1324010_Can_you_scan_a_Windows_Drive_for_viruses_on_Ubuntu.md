---
title: "Can you scan a Windows Drive for viruses on Ubuntu"
date: 2009-11-12
forum: General Help
---

### Post by alexsmith_12 on 2009-11-12
I am attempting to scan a Hard Drive from another machine that has windows on it. I have avast! and KlamAV, i have attempted to install AVG but for some reason it isn't working properly. I really don't see the point in having AntiVirus Software on a linux machine other than to scan a windows partition or a windows hard drive.

So is it possible to scan this hard drive from Ubuntu?
IF you can, how?

---

### Post by dvlchd3 on 2009-11-12
This guide will walk you through installing ClamAV:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

Then you can mount the Windows drive, open ClamAV Go to File -> Scan a Directory and point it to where you mounted the Windows HDD.

---

### Post by John Bean on 2009-11-12
> **alexsmith_12 said:**
> I really don't see the point in having AntiVirus Software on a linux machine other than to scan a windows partition or a windows hard drive.
It's available because almost all data - including malware - will pass through a Linux (or Unix) machine somewhere on it's route between one Windows PC and another. It's an opportunity to eliminate it.

> So is it possible to scan this hard drive from Ubuntu?
IF you can, how?A mounted NTFS volume is just another branch in the filesystem. You can scan it the same way you scan anything else.

---

### Post by wojox on 2009-11-12
If it's on another computer you should download [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

And scan it with that. It has ClamAv installed. It will only tell you you have a virus and where it is. It won't remove it.

---

### Post by Mark Phelps on 2009-11-12
You can also download and burn bootable CDs from Avira or Kaspersky -- and they boot into Linux to run their AV scans.

---

### Post by alexsmith_12 on 2009-11-12
> **dvlchd3 said:**
> This guide will walk you through installing ClamAV:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

Then you can mount the Windows drive, open ClamAV Go to File -> Scan a Directory and point it to where you mounted the Windows HDD.


thanks alot man. works well.

---

