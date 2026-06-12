---
title: "WUBI wireless"
date: 2011-01-19
forum: General Help
---

### Post by grlanker on 2011-01-19
I just installed WUBI and tried to connect to my home router but am unable to. I can connect to nearby unlocked routers, but am unable to connect to mine which is WPA-PSK [TKIP]. Any help would be appreciated. Also, this is the first time I've even seen Ubuntu, so please keep it simple. Thanks!

---

### Post by lithopsian on 2011-01-19
What card do you have?  Have you connected it with any Linux distro before?

---

### Post by grlanker on 2011-01-19
Intel 5100 AGN. Never connected with Linux Distro.

---

### Post by lithopsian on 2011-01-19
Do you have wpa_supplicant installed?  Is the iwlagn (driver for your card) module loaded?

If so, try:
ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 

You might need to set up wpa_supplicant.conf by hand, but see how it goes.

Or are you running wicd?

---

### Post by lithopsian on 2011-01-19
Do you have wpa_supplicant installed?  Is the iwlagn (driver for your card) module loaded?

If so, try:
ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 

You might need to set up wpa_supplicant.conf by hand, but see how it goes.

Or are you running wicd?

---

