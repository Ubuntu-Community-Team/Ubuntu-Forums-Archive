---
title: "Blank screen before ubuntu loads"
date: 2011-03-21
forum: General Help
---

### Post by rishabh0206 on 2011-03-21
I am new to ubuntu and i am using ubuntu 10.10 on dell studio. I use dual boot between ubuntu and windows 7 with the GRUB bootloader. As soon as I load into Ubuntu it shows a blank screen with a blinking cursor before loading, which increases the boot time. The blank screen takes around 20-30 seconds and then the ubuntu screen takes around 10 seconds. So can I remove that blank screen or do something to reduce this time.. Any help will be highly appreciated.

---

### Post by andrewthomas on 2011-03-21
This may help.

[http://ubuntuforums.org/showpost.php?p=9965194&postcount=8](http://ubuntuforums.org/showpost.php?p=9965194&postcount=8)


The entire thread could be of use to you.

**Known Maverick Meerkat issues/bugs with workarounds**

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

---

### Post by rishabh0206 on 2011-03-21
Open Terminal and type -
gksu gedit /etc/initramfs-tools/conf.d/splash

and add this line to the file, FRAMEBUFFER=y, save the file.

Again go to terminal and type -

sudo update-initramfs -u


This removes the blank screen but it does not reduces the boot time. Anyways splash screen is always better than the blank screen

---

