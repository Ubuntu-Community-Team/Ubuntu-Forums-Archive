---
title: "Issues with Wifi and 9.10"
date: 2009-11-24
forum: General Help
---

### Post by danny_b on 2009-11-24
Hey everyone.

So I've browsed the forums for about an hour now and I cannot find this issue. I just installed 9.10 nbr on my wife's dell mini 9 and cannot get the wifi to work. I installed the package bcmwl (or whatever it is) and I can get the hardware drivers to recognize the broadcom b43 and sta drivers. Neither are activated so when i try to activate them (i have tried both), it opens a blank window that says "Downloading and installing drivers" but nothing happens.

I've run the network code in terminal and got this (i'm hardwired right now which is why i have an ip):

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:98:01:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.105 latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)

Please help!

---

