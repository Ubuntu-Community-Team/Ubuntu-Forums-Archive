---
title: "Wireless Interface now showing up"
date: 2010-12-14
forum: General Help
---

### Post by TheRaiderNation on 2010-12-14
I can connect to the Internet just fine through my wireless card (I'm assuming ubuntu is using basic drivers) but the card doesn't show up when I run the iwconfig command. I'm guessing it should show up as wlan0, but it doesn't. Any one know how I can get it to show up?

Here's the output of iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:207  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

As it turns out, eth1 is my wifi, Why is it labelled eth1 instead of wlan0?

---

### Post by Mosabama on 2010-12-14
it is eth1 .. exactly what shows in my machine. I dont know why it doesnt show as wlan0 any more in 10.10 .. but it is eth1

---

### Post by Mosabama on 2010-12-14
maybe you want to check this if you want it to be wlan0. but it works fine I guess with the name eth1
[http://ubuntuforums.org/showthread.php?t=338332](http://ubuntuforums.org/showthread.php?t=338332)

---

