---
title: "Using Wireless on Ubuntu 11.04 64bit"
date: 2011-08-05
forum: General Help
---

### Post by SugoiDesu on 2011-08-05
Hello there! :)
I've been using Ubuntu 11.04 for a long time and I decided to install it on my laptop.
I've this annoying problem - It won't connect any wireless.
I tried to install a driver, but it won't help.
(I'm using a DELL computer)
Help? :popcorn:

---

### Post by garvinrick4 on 2011-08-05
Can you show us your wireless card and we can tell you what to install to get you up and going.
```
sudo lshw -C network
```

---

### Post by SugoiDesu on 2011-08-06
And again, I'm truely sorry for being a newbie.
> 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:70:2a:63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:de:dc:51
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb v2.17 ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:48 memory:fc000000-fc00ffff

Thank you!

---

### Post by Matt__ on 2011-08-06
Search is your friend...
[http://ubuntuforums.org/showthread.php?t=1604868&highlight=bcm4312](http://ubuntuforums.org/showthread.php?t=1604868&highlight=bcm4312)
lots of hints and solutions in this thread

---

### Post by SugoiDesu on 2011-08-06
Still not working.
It says "Wireless is disabled my hardware switch".

---

### Post by gandaran on 2011-08-06
everything here to fix your problem
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by SugoiDesu on 2011-08-06
Still doesn't work, and I'd installed everything in Synaptic and untarred the b43 package.
Ummm... when I put "rfkill list", it says that dell-wifi is blocked.
How do I suppose to unblock it? I tried to write "rfkill unblock dell-wifi", but it doesn't work.
And again, sorry for being a noob.

---

### Post by Nithogger on 2011-08-06
> **SugoiDesu said:**
> Still not working.
It says "Wireless is disabled my hardware switch".

tried to activate the hardware switch ? And I reckon it says by and not my (?)

Btw, to others who read this: Could this be a DELL Issue? my dad has the same problem with wireless wifi. I suggested him to get wired internet connection and update the drivers, restart the comp. Haven't hear whether it worked or not though... But I see a lot of DELL laptop's with this problem

---

### Post by garvinrick4 on 2011-08-07
> **SugoiDesu said:**
> Still doesn't work, and I'd installed everything in Synaptic and untarred the b43 package.
Ummm... when I put "rfkill list", it says that dell-wifi is blocked.
How do I suppose to unblock it? I tried to write "rfkill unblock dell-wifi", but it doesn't work.
And again, sorry for being a noob.
See if post 5 helps you out.
[http://ubuntuforums.org/showthread.php?t=1791482](http://ubuntuforums.org/showthread.php?t=1791482)

---

