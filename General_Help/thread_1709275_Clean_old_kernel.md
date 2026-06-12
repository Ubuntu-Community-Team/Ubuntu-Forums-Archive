---
title: "Clean old kernel"
date: 2011-03-18
forum: General Help
---

### Post by LNH_Sniper on 2011-03-18
[SIZE=3]hi,everyone.

today, I clean my linux kernel meet a simpale question.

i use the command to get the infomation of my linux kernel;
[/SIZE]
[SIZE=3]sudo dpkg --get-selections|grep linux

use this cmd to delete the old kernel

sudo apt-get remove linux-image-2.6.32-29-generic

but i forget --purge that cause zhe following item show like this

linux-image-2.6.32-28-generic            deinstall

what shold i do to clean the meau list totally?
thanks everybody.
[/SIZE]

---

### Post by Krytarik on 2011-03-18
Follow this guide to remove the excess kernel packages, but you should at least retain the last two kernels:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

Also, you can check with the filter features of Synaptic if your previous removal has left some config files of those package (which is what "purge" is all about), and if so, remove those now.

---

