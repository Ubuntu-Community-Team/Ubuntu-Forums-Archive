---
title: "Problem booting Windows 7 after Ubuntu installation"
date: 2010-03-17
forum: General Help
---

### Post by linix129 on 2010-03-17
Hey guys, I'm a noob when it comes to this kind of stuff, so bear with me.

Ok so my computer has 4 hard drives, a 640gb, 500gb, and two 320gbs. I have the larger two on a raid 0 array, which is also where I have windows installed. I installed Ubuntu on one of my spare 320gb drives, so that I wouldn't have to worry about partitioning. But now every time I boot my raid array in order to boot windows, grub will load and my computer will boot Ubuntu instead. Help please!

---

### Post by oldfred on 2010-03-17
I do not know raid and that can confuse things. When you installed Ubuntu, grub automatically installs to the drive in BIOS that you boot. There is an advanced button where you can choose to select another drive.

I would install grub to the drive that you installed ubuntu to and reinstall the windows boot loader to your current default boot. Then set the ubuntu drive to be the boot drive in BIOS.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Be sure to install the correct version of grub - grub2 for Karmic new installs or grub legacy (0.97) for everything else.

To make sure grub remember to install to the correct drive you may need to run this, the last screen sets default drive:
sudo dpkg-reconfigure grub-pc

---

