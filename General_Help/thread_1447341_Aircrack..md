---
title: "Aircrack."
date: 2010-04-05
forum: General Help
---

### Post by Colo2 on 2010-04-05
-EDITED-

Hey - if this is the wrong selection, feel free to move it.

Could someone help me? airodump-ng wlan0 returns:


> tom@tom-laptop:~$ sudo airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.


---

### Post by NoaHall on 2010-04-05
You need to run ```
sudo ifconfig wlan0 down
``` first.
Then ```
sudo ifconfig wlan0 up
```

Run ```
sudo airmon-ng start wlan0 
```
And kill each process it lists until airodump-ng wlan0 works.
This is a bit hit and miss recently, with some network cards, it requires it to be down, some require up. So if it still doesn't work, try with ```
sudo ifconfig wlan0 down
```

---

