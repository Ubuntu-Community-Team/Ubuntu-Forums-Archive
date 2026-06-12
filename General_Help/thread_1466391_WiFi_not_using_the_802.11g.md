---
title: "WiFi not using the 802.11g"
date: 2010-04-30
forum: General Help
---

### Post by Naminator_X_ on 2010-04-30
I have Toshiba Satellite p100 with wifi adapter 

Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks

now what is the problem. Well me and my neighbor share the same internet via wireless router. We both connect without problems. BUT there is a problem...I'm really close to the router (1-2 walls) but the ubuntu decides to use 802.11b instead of 802.11g and i can't seem to make it use the better freq >..< Is there a way to make it automatically detect what's best for it or at least some way for me to alter these settings by myself. I found some intel driver but it required kernel recompile or something like that and this is the one thing that i don't want to do. If you have better ideas i'm listening. If not i hope you give me enough information so i can do it myself. Thanks in advance

the response of lshw --class network
> 
*-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:44:1d:63
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.5-5 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:44000000-4401ffff ioport:3000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:3b:ad:5e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.101 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:44100000-44100fff


---

### Post by Naminator_X_ on 2010-05-05
bump :S

---

