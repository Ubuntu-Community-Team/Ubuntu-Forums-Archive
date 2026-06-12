---
title: "Can't connect to wired network"
date: 2012-08-27
forum: General Help
---

### Post by maximex on 2012-08-27
I'm not exactly sure what's wrong with my wired network, since my computer connects just fine wirelessly to the router.

my /etc/network/interfaces shows:
auto eth0
iface eth0 inet dhcp

lshw -C network shows:

  *-network:0             
       description: Ethernet interface
       product: VT86C100A [Rhine]
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 06
       serial: 00:50:ba:de:f3:7b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 maxlatency=152 mingnt=118 multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 ioport:e000(size=128) memory:ee010000-ee01007f memory:3c000000-3c00ffff

ifconfig shows:

eth0      Link encap:Ethernet  HWaddr 00:50:ba:de:f3:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 

I really hope someone can help me out

Thanks

---

### Post by CrusaderAD on 2012-08-27
Is your "Enable Networking" option checked in the global menu?

---

### Post by maximex on 2012-08-27
I'm not sure how to check the global menu, could you let me know?
But I think that it would be if my wireless works perfectly.
I want to switch to a wired network because of distance and obstacles between router (several brick walls).

The ethernet cable is directly connected to the wireless router that I am currently using.

Thanks

---

### Post by CrusaderAD on 2012-08-27
See screen shot.

---

