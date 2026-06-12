---
title: "wireless card quite working"
date: 2012-03-12
forum: General Help
---

### Post by rollinsmoke on 2012-03-12
hi i dont know what changed with my computer but my wireless card just suddenly quite working it powers on and works in other computer and lshw shows it working but no network access through it oh i guess i should ad im using ubuntu 11.10 


heres what lshw shows up



 *-network               
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:13:20:9a:13:47
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=1.0-5 ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:e3100000-e311ffff ioport:1000(size=32)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=136 maxlatency=28 mingnt=10
       resources: memory:e3000000-e300ffff

---

### Post by rollinsmoke on 2012-03-13
Bump

---

