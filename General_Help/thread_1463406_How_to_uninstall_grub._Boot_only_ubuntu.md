---
title: "How to uninstall grub. Boot only ubuntu"
date: 2010-04-26
forum: General Help
---

### Post by nilankaraja on 2010-04-26
Hi all,

I previously had more than one OS in my laptop. Now it only has ubuntu. Is it possible to remove Grub and boot ubuntu straigt so that the boot time' will become faster. 
I checked this sort of thread in this forum and I am unable to find one.

thanks in advance.

---

### Post by eriqjaffe on 2010-04-26
You can't uninstall grub, since that's the bootloader.  The best you can do is edit its' config so that it is displayed for 0 seconds, which basically makes it invisible.

Depending on which version of grub you have (a fresh install of 9.10 will have grub2, previous/upgraded version of Ubuntu will have "legacy" grub), there are different ways to do this.

Legacy:  [http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/)

grub2: [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by wilee-nilee on 2010-04-27
If you have grub2 sudo update grub will find whats on the HD and you will be set.

---

