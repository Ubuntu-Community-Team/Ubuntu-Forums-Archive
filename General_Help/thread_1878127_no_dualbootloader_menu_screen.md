---
title: "no dualbootloader menu screen"
date: 2011-11-09
forum: General Help
---

### Post by rahulhoare on 2011-11-09
I installed ubuntu11.10. But there was no bootloader menu asking for a choice to switch between win7 and ubuntu, and the comp by default booted into ubuntu. so i inserted win recovery disk and restored the win7 bootloader. now the comp only boots into win7. :( i don't know how to get a dual boot screen so as to switch between both.

Also, when the computer starts, it does so in 800x600 resolution,after installing ubuntu, during booting, the screen goes blank and a message comes to use recommended 1366x768. but after some time, the screen clears and normal booting proceeds. it only started after installing ubuntu. please help

---

### Post by Gatemaze on 2011-11-09
win7 have wiped out grub in mbr. There are a million posts on the topic, please search in the forum and in the web. For example:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
and see reinstalling grub2 from livecd.

---

### Post by Mark Phelps on 2011-11-09
What you should have done is come here BEFORE you reinstalled the Win7 boot loader.  It would then have been a lot easier to get dual-boot working.  What you've done now is overwrite GRUB in the MBR.

You will have to reinstall GRUB to the MBR from the Ubuntu desktop CD.  See the link below for details:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

