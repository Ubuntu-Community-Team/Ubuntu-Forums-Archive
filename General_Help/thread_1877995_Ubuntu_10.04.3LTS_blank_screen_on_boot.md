---
title: "Ubuntu 10.04.3LTS blank screen on boot"
date: 2011-11-09
forum: General Help
---

### Post by irc0x00 on 2011-11-09
I am using ubuntu 10.04.3LTS on my desktop. I used to have a nvidia card, which stopped working, and so i removed the nvidia drivers using 'apt-get purge nvidia*' - Ubuntu was running fine after this. Recently i got a old nvidia-8400GS from a friend, plugged it in. Following this i am getting a blank(black) screen after boot. I have tried removing the card, but that doesn't help either. Weird thing is, on doing a 'killall Xsession' from tty1, X auto restarts fine, and i get the gdm login screen, though under restricted drivers its says that 'nvidia-current is activated but not currently in use'. The problem reappears on reboot.
(PS: i have already tried with 'nomodeset' parameter during boot, to no avail. I've also tried  'apt-purge nvidia*' followed by 'apt-get install nvidia-current' followed by 'ldconfig' , 'nvidia-xconfig' and reboot, again to no avail. And I've also tried with the nvidia-173 drivers.)

I'll be grateful for any help :)

---

### Post by dcstar on 2011-11-10
> **irc0x00 said:**
> I am using ubuntu 10.04.3LTS on my desktop. I used to have a nvidia card, which stopped working, and so i removed the nvidia drivers using 'apt-get purge nvidia*' - Ubuntu was running fine after this. Recently i got a old nvidia-8400GS from a friend, plugged it in. Following this i am getting a blank(black) screen after boot. I have tried removing the card, but that doesn't help either. Weird thing is, on doing a 'killall Xsession' from tty1, X auto restarts fine, and i get the gdm login screen, though under restricted drivers its says that 'nvidia-current is activated but not currently in use'. The problem reappears on reboot.
(PS: i have already tried with 'nomodeset' parameter during boot, to no avail. I've also tried  'apt-purge nvidia*' followed by 'apt-get install nvidia-current' followed by 'ldconfig' , 'nvidia-xconfig' and reboot, again to no avail. And I've also tried with the nvidia-173 drivers.)

I'll be grateful for any help :)

Rename the xorg.conf file and reboot, then if you like install the nvidia drivers from scratch to recreate a fresh file.

---

