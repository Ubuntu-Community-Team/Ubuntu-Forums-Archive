---
title: "Reverting any changes made to plymouth"
date: 2010-08-09
forum: General Help
---

### Post by ALF102 on 2010-08-09
Hi, I just change the theme to plymouth and also apply this command:

sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

sudo update-alternatives --config default.plymouth

sudo update-initramfs -u


I know that it made the boot time much longer and now I want to undo/revert the changes that I've made.

---

### Post by ALF102 on 2010-08-09
oh yeah, for some reason...after enabling the plymouth using:

sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

the booting process is stuck at the slash screen and now I'm running on live CD

---

