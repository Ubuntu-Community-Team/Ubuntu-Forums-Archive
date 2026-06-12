---
title: "Fedora boot loader and Ubuntu grub2"
date: 2010-03-14
forum: General Help
---

### Post by Kevbert on 2010-03-14
I've just installed Fedora 12 and am multi-booting with Ubuntu and Win XP.
My primary OS is Ubuntu 10.04 and Fedora was the last OS installed so when I boot up the first thing that happens is that I get the option to boot Fedora or Other. If I select Other I get the Grub2 menu. In 10.04 I've performed a grub update so that Fedora appears in the Grub2 menu.
Is it possible to get rid of the Fedora bootloader that appears and if so how ?

---

### Post by oldfred on 2010-03-14
You should just have to reinstall Uubntu's grub to the MBR. Does the Fedora boot ok from grub2, I have seen both issues and it working in some cases.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Anyone with multiple operating systems needs to understand what is booting and where things are installed. This script is for solving boot issues but I like to keep a copy of the results.txt before & after any system changes so I know what is where and can figure out my own issues. You do not need to post the results.txt unless you have issues or want help understanding it.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

