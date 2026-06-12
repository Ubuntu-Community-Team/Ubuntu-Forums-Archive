---
title: "configuring boot list in 9.10"
date: 2009-10-30
forum: General Help
---

### Post by germund on 2009-10-30
Hello,

I have successfully installed Ubuntu 9.10 on a second partition on my Windows Vista machine.  for the time being, until I can persuade my family to switch from windows altogether, I would like Vista to be the default OS at bootup.  I had found an article that told me how to edit the boot list in older versions of Ubuntu, (sudo gedit/boot/grub/menu.lst)  However, I can't seem to find menu.lst there in 9.10.  Where do I find menu.lst, or how do I go about reconfiguring the boot menu if menu.lst is obsolete?

Thanks

Bruce

---

### Post by Tuliku on 2009-10-30
Instead of "menu.lst" it is now "grub.conf"..
Have fun

---

### Post by Brandon Williams on 2009-10-30
9.10 uses grub2, so menu.lst won't help.

Google told me to start looking [here](http://ubuntuforums.org/showthread.php?p=8192085) and [here](https://answers.launchpad.net/ubuntu/+source/grub/+question/81959).

---

