---
title: "manually add ubuntu boot on partition to boot.ini in xp"
date: 2010-02-17
forum: General Help
---

### Post by vaportrail123 on 2010-02-17
Well, i had ubuntu 9.04 on my netbook, and i tossed windows XP on an empty partition, and now i cant quite figure out what to add to the boot.ini to give me the option to boot from the the ubuntu partition.

---

### Post by undecim on 2010-02-17
You can't boot Ubuntu from XP. Windows just doesn't have that capability. You will need to use a live CD or a live USB drive to reinstall grub, which can boot either windows or linux.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) has some info on that.

---

### Post by vaportrail123 on 2010-02-17
this looks like something that will screw up my netbook if i do it wrong... any advice?

---

### Post by undecim on 2010-02-18
Having a back up of all your important files is always a good idea. (You can do this from the live CD)

This tutorial isn't dealing with partitions, so as long as you follow the directions properly, you will be perfectly fine. The only thing that you can easily screw up is your MBR, which will make it so that you can't boot into XP until you fix GRUB properly. (in other words, if you mess up, you can just try again)

If you do make a mistake, post in this thread what you typed and what the result was, and I'll help you out.

Also, 9.04 uses Grub Legacy by default, so unless you explicitly installed Grub 2, you will have Grub Legacy. Once you mount your ubuntu partition by viewing it in a file manager, you can skip to "Overwriting the Master Boot Record" part of the guide.

---

### Post by louieb on 2010-02-18
you can boot Linux with XP. The short of it is  1st) install GRUB in the boot sector of the Linux install partition. 2nd) copy the 1st 466 bytes of the boot sector to a file and put it in windows c:\  . 3rd) modify boot.ini - add an entry for Linux. 

[Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692") 

> this looks like something that will screw up my netbook if i do it wrong...

Grub is easier to set up.

---

