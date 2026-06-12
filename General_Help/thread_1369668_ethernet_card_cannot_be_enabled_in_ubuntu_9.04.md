---
title: "ethernet card cannot be enabled in ubuntu 9.04"
date: 2010-01-01
forum: General Help
---

### Post by bhuvi on 2010-01-01
i tried to connect internet in ubuntu 9.04 by using sudo pppoeconf
and now network manager is displaying as ethernet device not managed.i couldnt connect internet in ubuntu.how can i enable ethernet card in ubuntu.please help!!!

---

### Post by spiderbatdad on 2010-01-01
pppoeconf is for telephone modem. Ethernet is broadband. Which are you using. What type of modem or network card?

---

### Post by Iowan on 2010-01-01
The "device not managed" method frequently means the device is defined in */etc/network/interfaces*. If so, you can comment out the definition, save, and restart/reboot. (If you need it back, you can un-comment the lines).

---

### Post by bhuvi on 2010-01-01
> **Iowan said:**
> The "device not managed" method frequently means the device is defined in */etc/network/interfaces*. If so, you can comment out the definition, save, and restart/reboot. (If you need it back, you can un-comment the lines).
THank you lowan the problem is now solved.

---

### Post by bhuvi on 2010-01-01
> **spiderbatdad said:**
> pppoeconf is for telephone modem. Ethernet is broadband. Which are you using. What type of modem or network card?
actually i was connecting to a broadband internet connection,it was the method i used to connect internet in my ubuntu 8.04.That's why i used this method in ubuntu 9.04 and ended up with a disabled ethernet card.Anyway the problem is now solved.Thanks for your reply

---

