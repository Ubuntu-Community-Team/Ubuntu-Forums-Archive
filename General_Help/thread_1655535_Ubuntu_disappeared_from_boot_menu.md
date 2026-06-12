---
title: "Ubuntu disappeared from boot menu"
date: 2010-12-29
forum: General Help
---

### Post by urepedese on 2010-12-29
I have been running a dual boot 9.04/xp setup without major problems for nearly a year now.(just an unresolved kyocera printer problem)

I have had issues with windows and recently needed to reinstall windows. To do this I created a slipstreamed SP3 disk. I switched to boot priority to CD and ran a repair install from there, trouble was this gave me two installs of windows at the boot menu but ubuntu disappeared from the menu at this point.

I successfully ran the repair install again from the original windows install.

I then deleted the second windows installation.

Now it boots straight to windows without the boot menu at all.

The ubuntu partition is still there however.

*Please note that since ubuntu has performed well I have almost forgotten all I know about it.

---

### Post by davidmohammed on 2010-12-29
I presume that since you are using 9.04, you are using grub rather than grub2 bootloader.

In that case - the [following]("http://ubuntuforums.org/showthread.php?t=224351") instructions would help you.

---

### Post by urepedese on 2011-01-01
*I presume that since you are using 9.04, you are using grub rather than grub2 bootloader.*

You would presume right by the look of it, although I have no idea what grub2 bootloader is.

Lucky I can follow instructions because they worked a treat.

Thank you.

---

