---
title: "DVD Drives Help"
date: 2010-01-20
forum: General Help
---

### Post by Ironman1965 on 2010-01-20
I have 2 dvd drives.

IDE DVD burner = sr0
SATA HD/BR/DVD Burner = sr1

Is there a way to swap their priority so that...


SATA HD/BR/DVD Burner = sr0
IDE DVD burner = sr1

Thanks.

---

### Post by Ironman1965 on 2010-01-20
Apparently they can be renamed as root but does they revert back after a reboot.  Any ideas how to make it stick?

---

### Post by lyall on 2010-01-20
this might work I do not know just guessing

power off your PC and disconnect the IDE drive and reboot
then shut down and connect the IDE drvie

It might works

good luck and have fun learnig

---

### Post by Ironman1965 on 2010-01-21
Just finished watching a show with the kids.  Thanks lyall.  I read the Linux partition HOWTO and that same Idea was going through my head.  I'll try it later and report back.  I'm just not sure if it will work because for some reason IDE channels always seem to get a higher priority.  Got my fingers crossed though.  Thanks again.

---

### Post by Ironman1965 on 2010-01-21
Just tried it and doesn't work.  Soon as the IDE drive is plugged back in it takes over sr0 again.  Any other help out there?

---

