---
title: "Packet loss on LAN"
date: 2011-03-10
forum: General Help
---

### Post by mashedbear on 2011-03-10
I have a small home network, which experiences quite high rates of packet loss e.g.:
> 
2524 packets transmitted, 2045 received, 18% packet loss, time 2524313ms
rtt min/avg/max/mdev = 0.330/0.740/224.381/5.020 ms


This packet loss was measured on an Ethernet connection. To be honest the packet loss can be higher. 

The workaround is to reboot the router - which seems to fix the issue temporarily

I am looking for some help and advice to track down the root cause and fix the issue.

The router is a Netgear 54mbps wireless model WGR614v6 with firmware V2.0.19_1.0.19. There are 4 Ethernet ports. The PC is Ubuntu 10.10 and is connected on Ethernet. 

Thanks

---

### Post by mashedbear on 2011-03-11
Bump. Help appreciated!

---

### Post by SeijiSensei on 2011-03-11
First things to try are hardware-based.  Try using a different ethernet port on the router.  Replace the ethernet cable.  Replace the computer's network card if that's possible.  Try testing with a different computer/cable.

---

### Post by dcstar on 2011-03-12
> **SeijiSensei said:**
> First things to try are hardware-based.  Try using a different ethernet port on the router.  Replace the ethernet cable.  Replace the computer's network card if that's possible.  Try testing with a different computer/cable.

Install the **ethtool** package to alter the network card settings.

---

### Post by mashedbear on 2011-03-15
Thanks. I've started to take a look at ethtool and the physical cabling, but even though I haven't actually done anything - like change ports or change card settings -  the problem seems to have gone away!

e.g. 57 packets transmitted, 57 received, 0% packet loss, time 55996ms
rtt min/avg/max/mdev = 0.564/0.677/0.729/0.051 ms

I'm going to leave alone for now - until starts playing around again - and then press on with your suggestions. 

Thanks for your help!

---

