---
title: "Multi partition fresh windows load..."
date: 2011-04-20
forum: General Help
---

### Post by Eleutherios on 2011-04-20
So i needed windows for some school work, so i partitioned out 100 gigs for an xp instal, formatted NTFS, loaded windows up on her, and realized it marked my Ubuntu poartion inactive.... :( how do I go abouts reinstalling the grub, or is it more a matter of marking the ubuntu partition as primary...?

---

### Post by lmarmisa on 2011-04-20
Please, boot your system into a Ubuntu Live CD, then visit the page  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) , run Boot Info Script and post the results on this thread (follow the instructions of that page).

According to those results you will receive more information for reinstalling GRUB.

---

### Post by Mark Phelps on 2011-04-21
> **Eleutherios said:**
> So i needed windows for some school work, so i partitioned out 100 gigs for an xp instal, formatted NTFS, loaded windows up on her, and realized it marked my Ubuntu poartion inactive.... :( how do I go abouts reinstalling the grub, or is it more a matter of marking the ubuntu partition as primary...?

Unlike Windows, Ubuntu doesn't need active or boot flags on its partitions.

To get access to Ubuntu back, boot from an Ubuntu CD and reinstall GRUB.  

See attached link below:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by brpylko on 2011-04-21
ALWAYS install windows first so that grub will be on there in the future.

---

