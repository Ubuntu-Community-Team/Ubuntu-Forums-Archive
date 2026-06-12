---
title: "Network is gone sometimes"
date: 2011-01-31
forum: General Help
---

### Post by ngoc on 2011-01-31
Hi,

Sometimes since ubuntu 8.x, I lost my network. "No connection available" I ckecked my box, the cable is still here, tried to restart network-manager, networking and network-interface but no way to get internet back. I have to reboot the computer.

It appears at anytime (2 min or 6 hours after starting the system). I do not have this case with Windows Xp / seven

Any idea?

---

### Post by TheHackOps on 2011-01-31
Is there anything running in the background that has a constant connection to the internet or LAN

---

### Post by ngoc on 2011-01-31
No I supposed :/ 
It happens even after booting the system (few minutes). My network card is a realtek

---

### Post by perspectoff on 2011-01-31
Usually, IME, has to do with Network Manager.

Try removing all the network manager components (including gnome-netowkr-manager if you are using Ubuntu) and installing WICD instead. I have never had a problem with Wicd.

---

### Post by ngoc on 2011-02-20
Hi,

It also happenned with WICD. When happenned, it looks i have never "eth0" or whatever network card.

Now network manager components are uninstalled, can i uninstall wicd and manage network card such as on debian?

---

