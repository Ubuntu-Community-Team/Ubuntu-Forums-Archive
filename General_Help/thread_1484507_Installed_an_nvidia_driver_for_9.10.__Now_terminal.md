---
title: "Installed an nvidia driver for 9.10.  Now terminal appears when computer boots up"
date: 2010-05-15
forum: General Help
---

### Post by feralin on 2010-05-15
I'm not sure what Nvidia driver I installed the other day, but it's messed things up.  After Ubuntu boots up and asks for login, I am greeted with terminal.  Setting 1152Xwhatever resolution failed.  Setting to 1024X768.  My xorg.conf.old file is completely empty, so I have no idea what the original settings were.  I have tried removing and reinstalling xserver.xorg but that hasn't seemed to get me anywhere.  I have also used the "apt-cache search nvidia" command to see what drivers could be installed, but every single driver that I attempt to remove isn't installed.  Any suggestions?     Thanks a lot.

---

### Post by angry_johnnie on 2010-05-15
to find out which driver you have installed you could do

```
aptitude search nvidia
```

this will yield something like this (for example):

i   nvidia-173
p   nvidia-173-dev
p   nvidia-173-kernel-source

and so on...

the ones with the letter **i** are the ones you have installed.

remove it.

when you log in again, use the hardware drivers utility instead, to install the driver you need.

---

### Post by fragos on 2010-05-15
Did you use Administration, Hardware Drivers to install the recommended Nvidia driver?

---

### Post by feralin on 2010-05-17
I used the software center for the driver installation.  It turns out I had 3 different nvidia drivers installed, which have now been removed.  How do I go about installation Nvidia's restricted drivers for Ubuntu?  I went into Hardware Drivers with a blank list.

---

### Post by fragos on 2010-05-17
There was no need to remove nvidia drivers. They were installed to be used or not as needed. I believe the nvidia packages that you'd want for the newest driver are:

nvidia-current
nvidia-settings
nvidia-common
nvidia-current-modaliases

---

### Post by Danno2468 on 2010-05-29
When you get to that Low graphics screen.  Try hitting ctrl+alt+F1 at the same time.  That should bring you to a cli. Then I would shut down the display manager.  Get rid of the old Nvidia driver, and install a new one.  Configure a new xorg.conf

sudo gdm stop
sudo rm /etc/X11/xorg.conf
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-xconfig

---

