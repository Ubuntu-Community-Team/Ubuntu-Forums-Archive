---
title: "GRUB issues"
date: 2009-11-24
forum: General Help
---

### Post by whatshisfoot on 2009-11-24
I dual boot Ubuntu and XP, and until previously, when i selected Ubuntu in my windows bootloader, GRUB popped right up with my kernel options. I installed the most recent updates, rebooted into windows, then tried to boot ubuntu later, and I got the GRUB command line. I don't know how to load the kernel manually, and I don't want to reinstall, what can I do to either load the kernel, or repair the bootloader?

---

### Post by oldfred on 2009-11-25
The instruction are a lot different depending on which version of grub you have. Most upgrades still have grub legacy or grub.97 and new installs have grub2 which is still at 1.97 beta4.

Grub version command:
grub-install -v

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

chroot to repair
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

