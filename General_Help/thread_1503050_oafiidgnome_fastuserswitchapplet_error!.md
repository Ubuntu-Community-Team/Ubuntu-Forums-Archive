---
title: "oafiid:gnome_fastuserswitchapplet error!"
date: 2010-06-06
forum: General Help
---

### Post by xpluto on 2010-06-06
every time i log in  i get this error
oafiid:gnome_fastuserswitchapplet

and i can't find network manager   
i already have notification area

im using lucid lynx

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
sudo aptitude install gnome-applets

---

### Post by xpluto on 2010-06-06
Fixed removing everything from /etc/network/interfaces and replacing it  with:
 
```
auto lo
iface lo inet loopback 
```
:popcorn:

---

