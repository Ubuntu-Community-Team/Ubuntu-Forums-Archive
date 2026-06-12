---
title: "Backup and restore full system."
date: 2010-11-05
forum: General Help
---

### Post by kanishkdudeja on 2010-11-05
hey i heard of some software partimage which can backup whole system and restore exactly like the backup..but it does not support ext4 filesystem which is the default in ubuntu 10.10..basically i hav any only 1 partition..n i want to back up it up fully..so that in case of a failure i can use it and restore my system perfectly like it functioned earlier..also many of my friends want to try ubuntu and dey want some extra packages installed by default like sun java etc etc because they do not hav an internet connection..so im thinking of backuping up my full system in an image file..and den i can use the image file to make theyre system the same as mine..is der any command or software which can do dis for me ? everybody suggested partimage but it does not work for ext4..so tell me some alternative.

---

### Post by sikander3786 on 2010-11-05
If you simply want to backup the packages only, there is no better choice than APTonCD.

[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

If you want to do a complete backup of your PC, I would recommend clonezilla.

[http://clonezilla.org](http://clonezilla.org)

---

### Post by searchfgold6789 on 2010-11-05
As for the backup software, I would recommend Clonezilla.
But if you need to install software without an internet connection, I would not make it as complicated, but instead download the .deb package files to a CD, DVD, or USB stick, and then open the files on their Ubuntu systems.

---

### Post by sikander3786 on 2010-11-05
> instead download the .deb package files to a CD, DVD, or USB stick, and then open the files on their Ubuntu systems.

It won't work that way because you never know which dependencies are already installed and which ones you need to download. Not possible.

---

### Post by cpmman on 2010-11-05
You would need the local repositories:

[***_http://ubuntuforums.org/showthread.php?t=352460_***]("http://ubuntuforums.org/showthread.php?t=352460")

---

### Post by kanishkdudeja on 2010-11-05
In aptonCd the possible media options to save the packages are cd/dvd..can it be a usb pen drive ? or mayb an iso file that i can mount on the system i want to install the packages on ?

---

### Post by kanishkdudeja on 2010-11-05
got the answer myself..:)

---

