---
title: "Enabling LightDM"
date: 2011-10-15
forum: General Help
---

### Post by K3fka on 2011-10-15
Hey, I just switched from Ubuntu to Xubuntu today. Apparently the lightdm packages are already installed, which is good. I was just wondering how to activate it, or if it will even work properly.

---

### Post by effenberg0x0 on 2011-10-15
sudo apt-get remove --purge gdm
sudo dpkg-reconfigure lightdm
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo service lightdm stop
sudo service lightdm start

Effenberg

---

