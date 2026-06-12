---
title: "uninstall Ubuntu --- How to"
date: 2010-03-13
forum: General Help
---

### Post by spanner707 on 2010-03-13
I've accidently installed ubuntu 9.1 twice in parallel boot with Win XP. I think somehow I corrupted the first installation of Ubuntu and thought I could simply re-install Ubuntu over the top of the first install but instead it installed another Ubuntu system. How can I completely remove one of the ubuntu 9.1 installations leaving just Win XP and one install of Ubuntu.
 
As you can see I'm a complete newbie and desperately in need of assistance.
I couldn't find anything about un-installing by searching.
 
All help appreciated

---

### Post by chris billington on 2010-03-13
You may actually have successfully installed over the top. The bootloader doesn't know anything about which boot options are actually still installed, and so it wouldn't have removed the option from the list. 

You can check in 'Computer' to see if the hard drive partition of the old installation is still around. If its not, then your install was over the top of the old one. You can then just remove the entry in the bootloader with these instructions:

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

Make sure you don't remove the wrong one or you wont be able to boot! Maybe first rename the entry you want to remove, so that you can reboot and confirm that its the right one before you actually remove it.

If the partition is still there, you can just format it and use it for whatever you like. Look up the program gparted if you want to do that, and be careful of course not to format a partition you're using!

---

### Post by spanner707 on 2010-03-13
Thanks for the help Chris.  I'll follow up your suggestion and see if I can delele one of the Ubuntu installations.
 
Cheers

---

