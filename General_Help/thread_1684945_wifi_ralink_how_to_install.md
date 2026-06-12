---
title: "wifi ralink how to install"
date: 2011-02-09
forum: General Help
---

### Post by cyberboy109 on 2011-02-09
first of all I kno there is a website were i can just download the drivers and install as i did it before for jolicloud linux problem now 4 months down the line i cant find it and the ones i do find i have to all commands and to be honest im not good at commands
the wifi card info is ralink rt2860/rt3090
the reason i want the wifi driver is a number of os jolicloud,moblin and meego run perfectly on my girl friend netbook...but ubuntu mint linux and pclinux all run oki but all refuse to turn of even with all the commands 

as i said before i did find the driver once but i cant now....i just wanna be able to download and install

---

### Post by 3rdalbum on 2011-02-09
Most of the Ralink drivers are in the kernel already in Ubuntu, but sometimes don't work due to some overlap in drivers. The solution is to blacklist the overlapping driver.

I have the Ralink rt2870, apparently; this might work for you too.

Add the following to /etc/modprobe.d/blacklist.conf:

```
blacklist rt2800usb
```

Shut down completely and reboot.

---

### Post by cyberboy109 on 2011-02-09
thanks....eh sorry should have made it more clear i need the file to use on other os such as jolicloud 
all the ubuntu iv used reconise the card rite away....i would keep ubuntu netbook on but doesnt shout down and can be a bit slow

---

