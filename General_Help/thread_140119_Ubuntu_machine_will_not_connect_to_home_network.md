---
title: "Ubuntu machine will not connect to home network"
date: 2006-03-05
forum: General Help
---

### Post by Uboytu on 2006-03-05
I had set up a pc with Ubuntu for my mother to use. I installed the OS and was able to connect to the internet on my home network fine. After I brought it over to their home network I could not get the machine to connect. I tried using several NICs, tried using manual and DHCP settings, tried resetting the router, and tried reinstalling the OS. Nothing seemed to let me connect to the internet. When I plugged a spare Mac to the network, it connected perfectly. It was using DHCP.

Im fresh out of ideas! Is this a common problem with Ubuntu? Is there anything that can be done? Thanks!

---

### Post by jamesr on 2006-03-05
```
sudo ifconfig -a
```

At the console

---

### Post by Randomskk on 2006-03-05
I've seen IPv6 be the problem in some cases like this.
Try disabling it - while I have no idea how off the top of my head, I'm sure a forum search may come up with something.

---

### Post by njzillest on 2006-03-05
make sure that you have her router set to B and G band.. 

maybe ubuntu has your adapter configured to use it as B band..


do iwconfig.. when it sais IEEE 802.11 G --- then it will be G band

if the G is replaced with B then its B band




----------------
hope this helped

---

