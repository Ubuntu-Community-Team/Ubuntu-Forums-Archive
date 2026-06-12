---
title: "Setting up a ubuntu gateway server with bandwidth monitoring?"
date: 2006-03-26
forum: General Help
---

### Post by DjKritical on 2006-03-26
Howdy,

I'm setting up a ubuntu machine as an internet gateway,

I've set one up previous using iptables & firestarter which was fairly straight forward,

A couple of things I would like to do

- Monitor monthly bandwidth usage based on lan ip
- Restrict bandwidth on certain ips? maybe even restrict bandwidth during certain times?

I don't nessessarily need a step by step guide, just a point in the right direction and I should be able to figure out the rest 8) 

Cheers!

---

### Post by DjKritical on 2006-03-26
~ bump ~

;)

---

### Post by nanotube on 2006-03-26
look into using package "tcng" with the tc tool. that has a whole bunch of traffic monitoring/shaping capabilities.
following links may be helpful:
[http://www.knowplace.org/pages/howtos/traffic_shaping_with_linux.php](http://www.knowplace.org/pages/howtos/traffic_shaping_with_linux.php)
[http://tcng.sourceforge.net/](http://tcng.sourceforge.net/)

---

### Post by DjKritical on 2006-03-26
Thanks for the links nanotube :rolleyes: 

Looks like that strategy may be a bit over my head unfortunately, to my understanding you need to install tc then use scripts to initiate the policies.

This would mean making a custom script for each of the following:

Initiating bandwidth throttling for each lan ip/mac address
Logging bandwidth usage
Bandwidth Capping

I've seen some examples which use an http interface for doing this, however I can't find one for linux...

It's definately an idea that I will have a look into though, maybe it's not as hard as it looks? :-k

---

### Post by mulperi on 2006-03-27
This thread discusses how to provide QoS for the WLAN basestations. The scripts included are in .ipk package format, but if I remember correctly you could just tar xvzf filename.ipk them.

[http://forum.openwrt.org/viewtopic.php?id=3847&p=1](http://forum.openwrt.org/viewtopic.php?id=3847&p=1)

---

### Post by DjKritical on 2006-03-27
Okay I've been reading up on QoS which sorts out bandwidth throttling,

What about monitoring usage? Does QoS accomplish this?

Looks like QoS runs through IPTables?.. (as does the gateway setup)...

:-k it's a little overwhelming trying to setup a linux gateway for the first time

---

### Post by Jason_25 on 2006-03-27
I would also like to know about this, but that page seems pretty confusing.  If that is the official authority on QOS/bandwidth limiting on linux then we are in a bad way.  

I have set up a basic access point with essid hiding and port blocking with ubuntu very easily on a Netgear MA311 with a prism2 chipset.  It basically came down to this for me.

1.install wireless card
2.flash firmware (the firmware on my card was too old)
3.stop prism drivers from loading (delete from /lib/modules)
4.host ap drivers should take over automatically on a reboot
5.install hostap-utils, hostapd for wireless authentication/security
6.setup the hostapd config file
7.set wlan0 to master
8.set wlan0 essid to youressidhere
9.set wlan0 ip to 192.168.0.1
10.set wireless client to 192.168.0.1 and gateway to 192.168.1.1 (my router)
11.edit /etc/sysctl.conf to turn on port forwarding
12.this starts the nat.  eth0 here is your interface connected to the internet.
```

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
13.restart host apd
```

sudo /etc/init.d/hostapd restart

```
14.Connect!

A few extra points:
```

sudo cat /proc/net/ip_conntrack

```
Lists your nat connections, for basic network monitoring.  Something like tcpdump    would of course be more descriptive.

```

iwpriv ath0 enh_sec 0
iwpriv ath0 enh_sec 1
iwpriv ath0 enh_sec 2 
iwpriv ath0 enh_sec 3

```
This is the essid security level.  0 being least secure, 3 being most.  I have mine on 3 and cannot even see the essid with airodump.

```

sudo iptables -A FORWARD -p tcp --sport 0:1023 -j DROP
sudo iptables -A FORWARD -p udp --sport 0:1023 -j DROP

```
Since my makeshift wireless network only exists to feed skype to my pocket pc I am using this to block all the ports that skype doesn't need.

```

sudo iptables -X
sudo iptables -F
sudo iptables -Z

```
Should start you over again if you mess up.

Good luck.  Let us know if you have trouble.

---

