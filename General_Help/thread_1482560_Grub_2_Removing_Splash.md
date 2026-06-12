---
title: "Grub 2 Removing Splash"
date: 2010-05-13
forum: General Help
---

### Post by spikoley on 2010-05-13
I am trying to remove the splash screen on Karmic Koala.  I have tried removing *quiet splash* from the kernel entry and then running *update-grub* from /boot/grub/grub.cfg.  It didn't work and it looks like Grub is putting quiet splash back in.  How do I remove the splash screen?

---

### Post by oldfred on 2010-05-13
You need to change this line and run update
gksudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

sudo update-grub

More info:
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by spikoley on 2010-05-13
> **oldfred said:**
> You need to change this line and run update
gksudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

sudo update-grub

More info:
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thank, that worked!

---

