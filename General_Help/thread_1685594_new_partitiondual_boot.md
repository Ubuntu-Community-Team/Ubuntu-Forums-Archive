---
title: "new partition/dual boot"
date: 2011-02-10
forum: General Help
---

### Post by drewa on 2011-02-10
I have 10.10 installed on a Compaq laptop and want to set it up as a dual boot machine.  I'm not sure how to 1) set up another partition 2) set up the dual boot and 3) install my second operating system.  I'm sure that this is a pretty vanilla thing to do and am frustrated after trying to find out how to do it for a bit now.

Thanks
drew

---

### Post by mikewhatever on 2011-02-11
To create a partition, use Gparted under System-Admin from the Ubuntu live cd/usb.
To set up dual boot, it depends on the other OS. Many Linux distros will pick up Ubuntu boot files and add an option to the boot menu. Windows will require either a Grub reinstall or the use of EasyBCD.

[Reinstall Grub from live cd]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
[EasyBCD]("http://neosmart.net/dl.php?id=1")

---

### Post by drewa on 2011-02-11
Thanks for that.  I'll pull down the install for 10.10 and start there.  MY plan is to try and put OS X on it.  I'll nose around and see how to get that done once I get the partitions set up.

Thanks for the help.

---

