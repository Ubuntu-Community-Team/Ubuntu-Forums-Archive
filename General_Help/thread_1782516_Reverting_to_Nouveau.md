---
title: "Reverting to Nouveau"
date: 2011-06-14
forum: General Help
---

### Post by Robbyx on 2011-06-14
I found the following instructions at:

[https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)

> Here is a recipe which removes all old video drivers, and reinstalls nouveau:

  sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg


I tried the first line and it reports:

nvidia-settings: unrecognized option: "--uninstall"

**Does anyone know the way to revert to nouveau in natty?**

---

### Post by Robbyx on 2011-06-14
I have just worked out how to do it on my machine:

Ignore the steps in the first post

Go into system settings---hardware---- additional drivers. disable the in use driver by removing it (ie deactivate it).

rename   /etc/x11/xorg.conf  to xorg.conf.old

Restart

Check monitor settings in system settings. Make sure both monitors are in use if you have 2.

If it fails to work you can get back into Ubuntu via the low graphics option that appears when you start via the recovery mode. You may then reverse what you did to use nouveau.

---

### Post by pqwoerituytrueiwoq on 2011-06-14
try nvidia-installer --uninstall

---

### Post by Robbyx on 2011-06-15
**Is there any point in my going through the details of my post 1?** Maybe not doing so will cause me trouble. I do not know. I  have nouveau working without those steps. Instead I followed my advice at posting 2.

---

