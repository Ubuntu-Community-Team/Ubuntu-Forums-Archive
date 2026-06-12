---
title: "Switch Drivers"
date: 2010-07-15
forum: General Help
---

### Post by Geek9 on 2010-07-15
So awhile back I was having trouble using the standard bcm driver to connect to connect to my wpa-tkip security, but now I have that down, but have a new problem. I installed aircrack and unfortunately it does not work with my new driver, so what I'm looking for is a program that let's me easily switch drivers for my wifi.

---

### Post by Geek9 on 2010-07-16
more info for help, this is a insprion 1525 with intel 3945ABG wifi chipset, all I want is a command or even a program that allows me to use my patched wifi driver so I can use aircrack.

---

### Post by Geek9 on 2010-07-20
Fixed it myself again (sigh see posts) for anyone wondering and having the same problem use > sudo rmmod (your driver name, in my case) ndiswrapper
sudo modprobe (your new driver, in my case) iwl3945 
works like a charm.

---

