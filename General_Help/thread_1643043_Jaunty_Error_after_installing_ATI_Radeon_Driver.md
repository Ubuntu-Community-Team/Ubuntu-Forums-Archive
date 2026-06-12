---
title: "Jaunty Error after installing ATI Radeon Driver"
date: 2010-12-11
forum: General Help
---

### Post by botak89 on 2010-12-11
I'm using jaunty for almost 2 months on my Toshiba satellite A-105, and this afternoon i try to install ATI Radeon driver from add/remove program, everything work fine until my laptop rebooted, the GDM wont start, after looking for some ways on google I found a way to fix it:
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install -–reinstall libgl1-mesa-glx libgl1-mesa-dri
  dpkg-reconfigure xserver-xorg
sudo apt-get install –reinstall xserver-xorg-core 

after reboot my jaunty work fine until I realize that Compiz not active, i try to reactivate the compiz but it wont start, it says "Desktop Effect Could Not be Enabled", also I cant change my screen resolution it says "monitor unknown".
would somebody help me to solve this???

thanks for your help, sorry if my english bad, :-)

---

### Post by botak89 on 2010-12-11
*bump*

---

