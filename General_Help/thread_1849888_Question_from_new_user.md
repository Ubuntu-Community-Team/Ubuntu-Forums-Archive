---
title: "Question from new user"
date: 2011-09-25
forum: General Help
---

### Post by Juan Largo on 2011-09-25
I am using another Debian-based KDE operating system ATM.  I installed Kubuntu 10.04 in VirtualBox.  I like the experience so far, and I'm considering installing Kubuntu on my HDD.  However, I'm holding back from making the change because Kubuntu does things a lot differently from what I'm used to.  So here are my questions:

* Can I add lines to /etc/fstab to mount partitions automatically?

* Where is the Kubuntu version of /etc/X11/xorg.conf file if I need to make changes to the X configuration?

* Where is Kubuntu version of the /boot/grub/menu.lst file for making changes to the boot order or to add cheat codes?

---

### Post by Elfy on 2011-09-25
fstab - yes

xorg.conf - same place - though it's not used unless necessary, when my machine was first installed there was no xorg - none on fact until I installed the nvidia driver

menu.lst - is legacy *buntu uses grub2 now - no menu.lst 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Juan Largo on 2011-09-25
Thanks, forestpiskie, for that info.

Two final questions:

*  Although Kubuntu uses grub2, is it possible to install classic grub after Kubuntu is installed?

*  If I'm forced to use grub2 on the Kubuntu partition, can I still chain load into Kubuntu from another distro that uses classic grub?

---

### Post by Elfy on 2011-09-25
I believe so - I did have fedora controlling boot a few months ago - I added ubuntu to it and that was using grub2

I believe that you can also install grub legacy as well

Edit - oldish thread that looks current - check out the whole thing just in case = [http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

