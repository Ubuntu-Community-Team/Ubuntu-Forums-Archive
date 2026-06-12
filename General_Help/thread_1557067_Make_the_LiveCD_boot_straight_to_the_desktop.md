---
title: "Make the LiveCD boot straight to the desktop?"
date: 2010-08-20
forum: General Help
---

### Post by blazemore on 2010-08-20
I have a "persistant" LiveCD that I need to boot straight into the desktop without having to click "Try Ubuntu".
Is this possible?

It's going to be running without a monitor and connecting over remote desktop.

---

### Post by oldfred on 2010-08-20
Do not know, but I have the opposite problem with my flash drive. Which for me is ok.

I installed grub2 and copied several ISOs to the flash drive. When I boot I get the standard grub menu and it directly boots into the live version. I install from that.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

---

