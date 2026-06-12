---
title: "help- drivers issues"
date: 2011-08-21
forum: General Help
---

### Post by p.wolf on 2011-08-21
```
*-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:12:00.0
                logical name: eth1
                version: 01
                serial: 78:e4:00:ae:f4:df
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.4 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:fbc00000-fbc03fff

```
 
hey all i have a dual boot, struggling on windows because my wlan wont work. i need to get the drivers but cant find the right ones, i have enclosed above the netowrk info i got from the terminal in ubuntu, but im still confused as to what drivers i need.

---

### Post by Script Warlock on 2011-08-21
this might [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") you

---

### Post by Mark Phelps on 2011-08-22
> **p.wolf said:**
> hey all i have a dual boot, struggling on windows because my wlan wont work. 

That's NOT good news -- because Windows PCs typically have the correct drivers installed and wireless works "out of the box".

You should connect your PC with a wired connection to your network, and use Device Manager to look for driver updates for your Wireless device.  If that installs the drivers and you still can not connect Wireless -- you have a different problem than driver issues.

---

