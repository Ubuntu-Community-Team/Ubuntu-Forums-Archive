---
title: "Split partition on existing Ubuntu installation"
date: 2010-11-22
forum: General Help
---

### Post by toolmania1 on 2010-11-22
[FONT=Calibri]I have installedUbuntu 10.10 already.  I want to splitthe hard drive and create a new partition at the end of the drive?  Can I do this since I already installedUbuntu?  If so, how?  Or are there already posts in here aboutthis.  I looked, but have not foundanything yet.[/FONT]

---

### Post by SecretCode on 2010-11-22
Yes, it's possible, but it always carries a risk and you should back up your data (and be prepared to reinstall) and if possible clone the entire system beforehand.

You'll need to run from a Live CD (you can't resize the partition while it's in use by the installed operating system). Boot the live CD, go to System > Administration > Gparted partition editor and in that tool, first shrink the existing partition (this may take a few minutes) and then create a new partition in the free space (should be quick).

Do you have just one partition on the disk so far?

You may find a swap partition, which a normal install of Ubuntu creates. You should leave that in place.

Remember you can wipe everything if you get something wrong. But if you're careful, it's straightforward.

---

### Post by toolmania1 on 2010-11-22
Ok, I found this also.  Luckily, I dont have much to lose at this point.
 
 
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

