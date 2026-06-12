---
title: "Gnome Problems"
date: 2010-10-16
forum: General Help
---

### Post by wabbit46 on 2010-10-16
I have just upgraded to version 10.10 of Ubuntu.

The mouse pointer has to be set above the item I wish to select otherwise it fails to select it.

In addition the bottom panel of the Gnome Screen is only partially visible and nothing can be selected from it. This makes this distro very difficult to use.

I have an Nvidia Intergrated graphics chip on my motherboard and am using an old 17" LG 775 CRT display which worked perfectly with previous versions of Ubuntu but this version says it is an unknown monitor.

Any advice would be greatly appreciated.

---

### Post by bashphoenux on 2010-10-16
do a fresh install.
most of the time upgrade screws things up in Ubuntu .
Try restarting your system if you haven't after the upgrade !

---

### Post by wabbit46 on 2010-10-16
> **bashphoenux said:**
> do a fresh install.
most of the time upgrade screws things up in Ubuntu .
Try restarting your system if you haven't after the upgrade !

bashphoenux - Thanks for your advice but I did a fresh Install and have rebooted my computer several times. 

The only difference I have noted is that previous versions have required me to download a Proprietry Video Driver. Could this be a driver problem ?

---

### Post by dino99 on 2010-10-16
as you work with a CRT, save your xorg.conf to xorg.conf.old, then detete the actual xorg.conf (kernel directly deal with X now)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

then reboot and use nvidia-settings to tweak your prefs (system admin nvidia-settings)

---

### Post by wabbit46 on 2010-10-16
> **dino99 said:**
> as you work with a CRT, save your xorg.conf to xorg.conf.old, then detete the actual xorg.conf (kernel directly deal with X now)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

then reboot and use nvidia-settings to tweak your prefs (system admin nvidia-settings)

Thanks for your advice dino99
However there is no file /etc/X11/xorg.conf 

As a result the rest of the procedure fails.

---

