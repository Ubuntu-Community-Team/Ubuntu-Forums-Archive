---
title: "Apps/Drivers don't start on start-up"
date: 2012-03-17
forum: General Help
---

### Post by sreezon on 2012-03-17
Hello,

My wireless driver doesn't always activate on start-up. It acts as if there is no wireless driver since it just says that the Ethernet cable is unplugged. I have to restart and hope that it starts the next time around. 

Moreover, I have a program called "Synaptiks" (for touchpad and mouse settings) that I've set to automatically start on start-up but it almost never does. 

Also:

```

@M11x-R2:~$ uname -mr
3.0.0-16-generic x86_64

```

And for what it's worth:

```

*-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:b9:e4:0d:0a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:b6800000-b683ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9300 Wireless LAN adaptor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:37:f4:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:b5800000-b581ffff memory:b2800000-b280ffff

```

What is going on? How do I fix this?

Thanks

---

### Post by CynicRus on 2012-03-17
Give output lsmog |grep auth

---

### Post by sreezon on 2012-03-17
```

@M11x-R2:~$ lsmog |grep auth
No command 'lsmog' found, did you mean:
 Command 'lsmod' from package 'module-init-tools' (main)
lsmog: command not found
@M11x-R2:~$ lsmod |grep auth
@M11x-R2:~$ 

```

It doesn't give any output.

---

