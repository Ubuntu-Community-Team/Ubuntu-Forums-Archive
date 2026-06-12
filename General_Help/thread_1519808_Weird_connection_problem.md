---
title: "Weird connection problem"
date: 2010-06-28
forum: General Help
---

### Post by SiegHard on 2010-06-28
Hello i am using ubuntu and with all versions i have one pretty anoying problem. My wired connection sometimes lost connection and i can't reconnect for 3-10min. sometime longer. Technically everything is allright. With win7 i never had such problems. Any solutions how to fix this problem? :) Laptop: Lenovo Sl510  T5870(2GHz), 2GB RAM, 250GB 5400rpm HD, 15.4in 1366x768 LCD, Intel 4500MHD, CDRW/DVDRW, Intel 802.11agn wireless, Bluetooth, 1Gb Ethernet, UltraNav, Camera, 6c Li-Ion

---

### Post by cariboo on 2010-06-28
What chipset does the your ethernet device use? What driver? You can check by running in a terminal:

```
sudo lshw -C network
```

---

### Post by andyhelloween on 2010-06-30
Same problem at this end. Started after I upgraded to Lucid. Out of the sudden, I lost the wireless connection... reboot... and goes back on - don't like to wait :p.
My laptop is an HP DV6.

I'll try that command later on. Thanks!

---

### Post by SiegHard on 2010-09-27
> **cariboo907 said:**
> What chipset does the your ethernet device use? What driver? You can check by running in a terminal:

```
sudo lshw -C network
```
[http://pastebin.com/WEeKRbKX](http://pastebin.com/WEeKRbKX) :) Any ideas?

---

### Post by SiegHard on 2010-11-05
Hmm accidently found the solution if i make to start ubuntu with login it sloves all problems :D

---

