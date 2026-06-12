---
title: "Cannot save GRUB kernel parameters"
date: 2011-04-27
forum: General Help
---

### Post by scott8035 on 2011-04-27
We're using 10.10-server. We are trying to make grub boot changes permanent. I've already looked at thread [http://ubuntuforums.org/showthread.php?p=10726849#post10726849](http://ubuntuforums.org/showthread.php?p=10726849#post10726849). We updated /etc/default/grub, and update-grub propagates those changes into /boot/grub/grub.cfg, but not into menu.lst. It appears to use menu.lst as the source at boot, so our change doesn't show up as a linux parm. Any ideas?

---

### Post by dino99 on 2011-04-27
menu.lst is from grub (grub-legacy) and conflict with grub2. So delete it first.

then from synaptic: remove/purge then reinstall both grub-pc & grub-common

reboot

---

### Post by wojox on 2011-04-27
You have GrubLegacy and Grub2 installed. Remove grub legacy. [Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by HeyEugene on 2011-04-28
Yes, thanks, I had mistakenly installed both grub legacy and grub2.  Removing legacy grub and re-installation of grub-pc and grub-common resolved the problem.

Sincerely,
Green Eugene ( I work for scott8035, the initiator of this thread. )

---

