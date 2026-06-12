---
title: "Help with this tutorial"
date: 2010-12-27
forum: General Help
---

### Post by Jwag598 on 2010-12-27
Ok, I'm trying to follow this guy's tutorial ([http://www.youtube.com/watch?v=ACEv2EgDT8I&feature=related](http://www.youtube.com/watch?v=ACEv2EgDT8I&feature=related)) just for fun, I'm only doing it on my wifi. But this always comes up.
I am on Ubuntu 10.10 on a laptop

josh@josh-SiS-650:~$ sudo -s
[sudo] password for josh: 
root@josh-SiS-650:~# airmon-ng


Interface    Chipset        Driver

wlan0        Atheros     ath5k - [phy0]
mon0        Atheros     ath5k - [phy0]

root@josh-SiS-650:~# airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

root@josh-SiS-650:~# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
637    avahi-daemon
641    avahi-daemon
642    NetworkManager
675    wpa_supplicant
2002    dhclient
Process with PID 2002 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Atheros     ath5k - [phy0]
                (monitor mode enabled on mon1)
mon0        Atheros     ath5k - [phy0]

I have no idea what any of this means or how to fix it and continue with the tutorial.
Could someone help me?
Thanks in advance

---

### Post by realzippy on 2010-12-27
There is enough stuff out there googling "airmon-ng",seriously.
Btw,the output you posted gives a few answers.
Start with googling if your wlan card/driver supports what you want to do...
and welcome to UF!

---

### Post by Jwag598 on 2010-12-27
I've already tried googling it and I was utterly lost in everything (I'm a complete noob) and have no idea what to do, so I was wondering if someone would be nice enough and help walk me through it, orat least get me started.

---

### Post by realzippy on 2010-12-27
> **Jwag598 said:**
> I've already tried googling it and I was utterly lost in everything (I'm a complete noob) and have no idea what to do, so I was wondering if someone would be nice enough and help walk me through it, orat least get me started.

Google' first hit gives all you need,of course you need (very) basic network/wlan knowledge;after all you want to test your network..
```
iwconfig
```
lists a wlan device you want to use for airmon-ng,eg wlan0;
stop the network manager (or anything using this device) and try:
```
airmon-ng start wlan0
```

If refusing to learn/read google for "spoonwep2",a step to step GUI for
airmon/airdump,which is included in "Nubuntu" eg...  ;)

---

