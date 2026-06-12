---
title: "Wired network"
date: 2011-01-30
forum: General Help
---

### Post by mc228608 on 2011-01-30
Using ubuntu with grub 2 and all that jazz and having some problems with the Wired Network.
When i plug in my Ethernet cord it detects it and starts to auto connect but after a few seconds fails and sat network disconnected. im using a different computer ATM so im to lazy to put up spec info, but am willing to do so.
so where should i start? and what should i do?


Thank you 
M

---

### Post by SaintDanBert on 2011-01-30
There are known troubles with some Intel parts and their driver.
Many have troubles with dropped connections both wire and wireless.

I found a work around by replacing **network-manager** with **wicd**. I really preferred wicd over n-m and have never looked back even after my update from 8.04 to 10.04.

I would also make sure that you have the latest firmware for your network adapters. Check your repositories and visit the manufacturer site.

Bonne chance,
~~~ 0;-Dan

---

