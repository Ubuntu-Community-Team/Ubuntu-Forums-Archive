---
title: "HP Compaq nx7010 wont boot after clean install!"
date: 2010-04-29
forum: General Help
---

### Post by branko.savic on 2010-04-29
I have installed Ubuntu 9.10 from a live cd, on a HP Compaq nx7010! I selected to use the entire drive, so nothing else is on there!

The problem is when I start up the machine it wont boot into ubuntu! Instead I get a menu with 4 options:

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (Recovery mode)
Memory test (Memtest86+)
Memory test (Memtest86+, serial console 115200)

If I choose the first menu option I get the following error:

error: no such device: 07850f66-baab-4a48-B6C4-01268fee1523
Press any key to continue...

Pressing a key gets me back to the menu again!

I have tried to install several times, thinking that maybe, just maybe something went wrong with the installation! But no such luck! :(

I have also tried with different flavours such as ubuntu, xubunt and kubuntu with the same results!

I am now in desperate need for help, becouse I need this machine going ASAP!

Thanks for any help in this matter!

---

### Post by branko.savic on 2010-04-29
Anyone?

---

### Post by dino99 on 2010-04-29
this uuid is probably wrong: 07850f66-baab-4a48-B6C4-01268fee1523

what to do:
- boot from a cd or usb stick
- chroot to ubuntu partition following this example:
    [http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)
of course use the real path on your system ( this an example)

- when done, you can do everything about the broken distro: updating, ...

In your case you need to tun theses commands:
- sudo grub-mkconfig
- update-grub

then unmount in reverse order and reboot

note: this is for grub2

---

