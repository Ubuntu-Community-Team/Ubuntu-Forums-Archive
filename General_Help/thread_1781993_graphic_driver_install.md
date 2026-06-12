---
title: "graphic driver install?????"
date: 2011-06-14
forum: General Help
---

### Post by gene simmons on 2011-06-14
hi all,i recently tried to fix my plymouth not loading at startup issue with a script posted on here and that worked but i think it uninstalled or did somthing to my graphic driver,i have a cheapy acer d250 netbook and the graphics are awful like in safe mode now and when i go to monitor it says inknown and no drop downs are available,when i put xrandr in terminal it says fail to find monitor.did my driver get unisntalled or changed somehow.any tips or sugestions guys,thanx

dave

---

### Post by pqwoerituytrueiwoq on 2011-06-14
what script was it link?
you can try reinstalling the xserver-org-video-intel package
then restart gdm
sudo service gdm restart (close all apps 1st you will need to relogin)

---

### Post by Frogs Hair on 2011-06-14
Check the software center or synaptic to see if your driver is installed.

---

### Post by gene simmons on 2011-06-14
> **pqwoerituytrueiwoq said:**
> what script was it link?
you can try reinstalling the xserver-org-video-intel package
then restart gdm
sudo service gdm restart (close all apps 1st you will need to relogin)

thnx for reply

heres the link to the script i used to get the plymouth working


[Fix Plymouth on Ubuntu after installing NVIDIA or ATI proprietary drivers for Ubuntu 11.04 Natty | Paolo Bernardi’s Weblog]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/")

---

