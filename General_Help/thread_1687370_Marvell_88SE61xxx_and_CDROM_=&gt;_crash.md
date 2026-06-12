---
title: "Marvell 88SE61xxx and CDROM =&gt; crash"
date: 2011-02-13
forum: General Help
---

### Post by thinker-tinker on 2011-02-13
Hello,

I'm having some trouble running Ubuntu on my machine with a marvell SATA controller inside. As I have pointed out in [http://ubuntuforums.org/showthread.php?t=1685868](http://ubuntuforums.org/showthread.php?t=1685868) Ubuntu/GNOME consistently crash on me when I have IDE enabled in the Bios of my MSI P35 NEO2. I have now narrowed the problem down a little further but still have no solution to it: The crash occurs _only_ when I have a cd in one of my drives. As long as there is none, ubuntu runs happily. I have no problem booting/accessing my harddrive which is plugged into the ICH9 SATA port on my board and configured as IDE in the bios. pata_marvell is loaded, but something seems to be wrong with the IDE side. What should I look for?

---

