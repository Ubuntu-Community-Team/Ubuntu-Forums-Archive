---
title: "Turn off eth0 permanently?"
date: 2006-03-15
forum: General Help
---

### Post by cronholio on 2006-03-15
I have this laptop with WiFi (eth1) and Ethernet interface (eth0). During boot, configuring network interfaces takes forever. WiFi gets a DHCP address immediately (I can see that in the LED) and eth0 takes forever though I don't even use it. I tried to give a bogus static IP (10.0.0.1) to eth0 which will make the next boot very fast, but only that one. Even if I deactivate it (using "ip link set eth0 down" or the GUI networking config) it will be activated again at the next boot.

I don't use eth0 at all so is there a way to permanently disable it?

---

### Post by Stemp on 2006-03-15
edit /etc/network/interfaces

---

### Post by cronholio on 2006-03-15
It works. Merci beaucoup!

---

