---
title: "ASUS K50in 10.10 AMD64 Screen freeze"
date: 2010-12-05
forum: General Help
---

### Post by rocker2344 on 2010-12-05
Running a dual boot of winders 7 64bit and ubuntu 10.10 64bit
On the ubuntu side i can connect to wifi just find on AC power, but as soon as i go to battery power my whole system freezes; like a prank on a windows comp with the screen shot background and killing explorer.exe (USB, Ethernet, Wireless)

sudo lshw -C network output
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: XX:XX:XX:XX:XX:XX
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:e800(size=256) memory:f9fff000-f9ffffff memory:f9ff8000-f9ffbfff memory:feaf0000-feafffff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-23-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:febf0000-febfffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 80:00:60:0f:e8:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=169.254.2.2 link=yes multicast=yes

```I have been dealing with this for a while, manily because my battery life sucks; about 2 hours if i am lucky
Suggestions would be GREAT!!!!

---

### Post by !Anti! on 2011-01-02
I got the same problem with my Asus K50ID. I have tried both Ubuntu 10.10 and Kubuntu 10.10 but both act exactly the same way.

---

