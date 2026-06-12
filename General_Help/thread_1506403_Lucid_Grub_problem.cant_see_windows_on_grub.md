---
title: "Lucid Grub problem.cant see windows on grub"
date: 2010-06-10
forum: General Help
---

### Post by topbyter on 2010-06-10
Hey Guys, can you help me out? i installed Ubuntu Lucid on a partition on my machine which was formerly running windows XP on another partition. after a successfull installation, it happens i ubuntu loads at boot up without showing me GRUB to select my preferred partition or OS.

Hey guys i am waiting please. Any help will be appreciated. i have checked for menu.lst to set GRUB to load windows XP but i cant discover it only to read that Lucid uses GRUB 2 with different configurations.

Thanks....

---

### Post by oldfred on 2010-06-10
If booting with grub2 and grub only finds one operating system, it does not show the menu. You can hold down the shift key from BIOS until it shows. (it was escape key in old grub)

If windows is ok this should find it and add it to the menu.
sudo update-grub

To see you entire configuration, if the command above does not fix it.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

