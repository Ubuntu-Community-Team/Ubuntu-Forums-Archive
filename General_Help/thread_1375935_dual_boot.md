---
title: "dual boot"
date: 2010-01-08
forum: General Help
---

### Post by Linc_mc on 2010-01-08
I know this is an easy question but for the life of me I can remember how to set up a dual boot. I know that I have to partition the drive but at the moment Ubuntu is taking up the whole drive, so would i still be able to partition without loosing anything?

---

### Post by mk1w86 on 2010-01-08
First, what do you want to dual boot with? e.g. Windows or other Linux distro.

Secondly, if Ubuntu is taking up the whole drive you will have to resize the partition it is on to make space for a new one.  If you repartition the whole drive you will loose your current Ubuntu installation.

---

### Post by Linc_mc on 2010-01-08
yes I want to put winbloze on and keep my current install of ubuntu.

---

### Post by Leppie on 2010-01-08
from a livecd you can resize you linux partition, make sure you have 1 of the 4 slots for primary partitions available for your windows install.
install windows into the free space on the disk.
after the installation, boot with your karmic cd and re-install grub2 to the mbr update your grub.cfg

---

### Post by oldfred on 2010-01-08
Use gparted from a liveCD to shrink the Ubuntu partition and create primary NTFS partition for windows. It must be a primary partition to work, but does not have to be the first partition as some may say.

Versions may be different but the process is the same:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Depending on which version of ubuntu you will need to reinstall grub or grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Linc_mc on 2010-01-08
thanx for the help though I wonder if virtualization would be a better option as the problem is that i have windows programs that i run that do now work well under wine.

---

### Post by mk1w86 on 2010-01-08
If you are going to use virtualization may I recommend VirtualBox. :biggrin:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

