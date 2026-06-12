---
title: "Setting up wifi to use internet on android phone"
date: 2010-10-20
forum: General Help
---

### Post by jsriz on 2010-10-20
Well I have installed the wireless driver shown in the additional drivers tool but am unable to understand how to set up a wifi hotspot so that i can use internet on my android phone 
the guides google returned are a bit too complicated with ip tables and all  please help.....:(

---

### Post by RebateFX on 2010-10-20
I've been trying to set this up too but without success.

There is a blog post at [http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/](http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/) that suggests to use built in functionality of the Network Manager, but I think ad-hoc networks are filtered out on Android for some reason. A bit of a Google search reveals that you can hack in ad-hoc support for Android but the process isn't for the faint of heart so I think i will wait until a future Android version fixes the problem.

---

### Post by jsriz on 2010-10-23
> **RebateFX said:**
> I've been trying to set this up too but without success.

There is a blog post at [http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/](http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/) that suggests to use built in functionality of the Network Manager, but I think ad-hoc networks are filtered out on Android for some reason. A bit of a Google search reveals that you can hack in ad-hoc support for Android but the process isn't for the faint of heart so I think i will wait until a future Android version fixes the problem.

hey thanks for the info i flashed the zip file now it detects the adhoc network but stops at obtaining the ip address from the network


a program in windows "Connectify-me" got the job done but i need to do it in linux as i am not that much of a windows user..

---

### Post by jsriz on 2010-10-23
Edit:
It Works
Earlier I was trying add a new connection from the configure vpn menus.
now i just used the "Create New Wireless Network..." available in the menu.
Guess i was doing all thye hard work of setting up the dhcp server for nothing it works out of the box (ofcourse with the edit in the android os).

---

