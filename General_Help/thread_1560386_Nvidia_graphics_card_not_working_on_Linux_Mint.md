---
title: "Nvidia graphics card not working on Linux Mint"
date: 2010-08-24
forum: General Help
---

### Post by genjix on 2010-08-24
Hi,
I activated my graphics card on Linux Mint which is Nvidia GEFORCE GT 130M. Now when I boot up, after bios the loading screen looks like in the picture (sorry its crappy quality). When it gets to the login screen and afterwards it is just blank, but i can tell its running underneath because i can shut down by doing ctrl alt backspace and then tab and enter. I tried entering recovery mode but it was the same. Atm im using a live cd. Sorry if im just being a nub :|
[ATTACH]167429[/ATTACH]

---

### Post by ellgor on 2010-08-25
Hi,

Read that the nvidia drivers don't get installed correctly, found this guide to get things working correctly:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

As for the startup picture, go Admin> Startup- man> and set the screen to a good resolution with 24bit colours.

Regards, Ellgor.

---

### Post by genjix on 2010-08-25
hi thanks, but how can i access my pc when i boot up the screen is blank?

---

