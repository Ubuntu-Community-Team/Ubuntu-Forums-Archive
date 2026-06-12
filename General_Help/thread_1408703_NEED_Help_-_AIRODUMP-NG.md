---
title: "NEED Help - AIRODUMP-NG"
date: 2010-02-16
forum: General Help
---

### Post by cold_linux on 2010-02-16
when i try to run airodump-ng wlan0 i get this 

            root@cold28-laptop:/home/cold28# airodump-ng wlan0
                   ioctl(SIOCSIFFLAGS) failed: Unknown error 132


          can anyone help. thank u

---

### Post by croto on 2010-02-16
Is wlan0 set in monitor mode? what drivers are you using on your wireless card?

---

### Post by cold_linux on 2010-02-16
I'm running  it on my laptop, and monitor is enable , i was using if fine on day and the next it was giving me that error

---

### Post by cold_linux on 2010-02-16
and sometimes i get this message 

                ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

---

### Post by croto on 2010-02-16
I get the (second) error message when I have an interface set to station mode (not monitor) and try to use airodump with it. Can you post the output of iwconfig when you get that error message?

---

### Post by cold_linux on 2010-02-17
root@cold28-laptop:/home/cold28# airmon-ng stop wlan0


Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode disabled)

root@cold28-laptop:/home/cold28# ifconfig wlan0 down
root@cold28-laptop:/home/cold28# macchanger --mac 00:11:22:33:44:55 wlan0
Current MAC: 00:1f:3b:a4:ee:b3 (unknown)
Faked MAC:   00:11:22:33:44:55 (Cimsys Inc)
root@cold28-laptop:/home/cold28# airmon-ng start wlan0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
882    NetworkManager
905    avahi-daemon
906    avahi-daemon
1190    wpa_supplicant


Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]SIOCSIFFLAGS: Unknown error 132

                (monitor mode enabled on mon0)

root@cold28-laptop:/home/cold28# airodump-ng wlan0
ioctl(SIOCSIFFLAGS) failed: Unknown error 132



this is what im doing and thats the error MSG im getting. thats all i know.. i don't know how to fix it or what type of commands to put in. can u show me any thing new or commands to fix that.. thank u for all ur hlep.

---

### Post by croto on 2010-02-17
> 
wlan0 Intel 4965/5xxx iwlagn - [phy0]SIOCSIFFLAGS: Unknown error 132

(monitor mode enabled on mon0)


It says it enabled monitor mode on mon0, did you try this?
```

airodump-ng mon0

```

Also, as mentioned by airmon-ng, if it works and later it stops working, you may need to kill these processes:
NetworkManager
avahi-daemon
avahi-daemon
wpa_supplicant

---

### Post by cold_linux on 2010-02-17
thank u very much croto. it worked thank u very much.

---

### Post by croto on 2010-02-17
great! go break some WEP now ;)

---

### Post by cold_linux on 2010-02-17
lol. ill try and see how it goes. "its for educational purpose only:)"..lol..maybe

---

