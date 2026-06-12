---
title: "WPA Connections in 8.04"
date: 2009-07-28
forum: General Help
---

### Post by mrd489 on 2009-07-28
I am visiting a friend who uses a WPA-PSK [TKIP] + WPA2-PSK [AES] connection and I cannot connect to it on my Ubuntu 8.04. How can I set this up? He cannot change the wifi settings because that will mess up all the wireless devices in his house. Thank you!

---

### Post by Vaphell on 2009-08-31
network is detected? (sudo iwlist scan)
do you have wpa supplicant installed? reportedly it is required when connecting to WPA/WPA2 networks

once i had to configure 8.04 notebook to use my wifi router.
Ubuntu somehow couldn't connect unless forced manually. Finally I installed some additional GUI software that allows scanning and later selecting a network to connect. It was not pretty but at least it worked.
By the way you can always try the oldschool way of the wire :D

---

