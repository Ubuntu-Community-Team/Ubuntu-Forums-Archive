---
title: "Ubuntu 9.10 GUI Wont Start after Kernel Upgrade"
date: 2009-11-28
forum: General Help
---

### Post by tessa80 on 2009-11-28
hi... just installed fresh install of 9.10. Installed Nvidia graphics drivers so I could apply effects and compiz... then I installed updates, which updated the kernel, then on reboot the GUI doesn't appear after boot.. just the full screen shell login prompt.. I can't even login though because the screen is constantly flickering and when I type the keys they don't always enter, so I can't enter password correctly. Obviously there is a problem with the nvidia driver, but I have no idea how I can rectify this? I'm logged in now on the previous kernel, but I have the latest Nvidia driver installed.. not too sure what I need to do? I'm fairly new to linux by the way. 

thanks in advance for any advise.

---

### Post by jamesisin on 2009-11-28
Have you tried accessing the new kernel without the nVidia driver (ie: removing it)?

---

### Post by tessa80 on 2009-11-28
well I was thinking of trying that, but I'm not too sure how to remove the nvidia driver?

---

### Post by efflandt on 2009-11-28
There is a sticky at the top of the installation forum about flickering with nVidia [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

However, something related to the kernel update to 2.6.31-15, or that batch of updates, seems to have broken grub2 for me.  I can boot (recovery) menu items to the shell (where I can run startx to get into gnome).  But the only way I can boot directly to GUI login for either -14 or -15 kernel, 32 or 64-bit, is by entering commands at the grub prompt. Same thing for 64-bit 9.10 installed on a USB drive with grub2 on that drive.  Just a brief flashing cursor, and then no disk activity.

---

