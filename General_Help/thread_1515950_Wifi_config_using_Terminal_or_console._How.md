---
title: "Wifi config using Terminal or console. How?"
date: 2010-06-23
forum: General Help
---

### Post by lordskid on 2010-06-23
1. Can you configure wifi while netmanager is running?
2. How do you do above in terminal? what commands do you use?

---

### Post by lordskid on 2010-06-23
ok I tried the following commands...

1. iwconfig -> to determine which interface is wireless...
2. iwlist wlan0 scan -> it scans networks fine....
3. iwconfig wlan0 mode managed key open "my wep key" essid "essidname"
4. iwconfig wlan0 ap [accesspoint mac address]
5. dhclient wlan0 -> this failed so I did an ifconfig...
6. ifconfig wlan0 192.168.1.2 netmask 255.255.255.0
7. route add default gw 192.168.1.1
8. echo nameserver 192.168.1.1 >> /etc/resov.conf

all steps from 6 to 8 finished without any messages so I assume no errors.

but when I ping 192.168.1.1 it says host is unreachable.... can someone tell me where I went wrong? or is netmanager blocking/conflicting with my manual setup?

---

### Post by lordskid on 2010-06-23
Can someone help me? I am halfway through an upgrade from karmic to lucid. and it froze. then I couldnt boot my installation. but the recovery mode for ubuntu can go in except I don't have net connection to continue the update.

---

### Post by iponeverything on 2010-06-24
Configuring the device via /etc/network/interfaces will cause it to be ignored by Network Manager. This is what you want.

If you don't want to go that route, kill off NM and configure the device from the command line. Doing what your doing, configuring the device from the command line while NM still has control over the device -- causes unexpected results. Please look at:

[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

---

