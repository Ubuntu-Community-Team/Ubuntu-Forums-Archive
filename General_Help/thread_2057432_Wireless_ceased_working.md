---
title: "Wireless ceased working"
date: 2012-09-13
forum: General Help
---

### Post by mathematical on 2012-09-13
Hello my wireless has recently stopped working. I have been running Ubuntu for over a year and within the past few weeks my wireless signal would randomly drop. Yesterday my wireless ceased working altogether. The output from lshw -C network said "unclaimed" yesterday and below is the output from today:

*-network               
       description: Ethernet interface
       product: 82567LF Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:27:13:65:a2:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.8-3 ip=192.168.2.6 latency=0 multicast=yes
       resources: irq:45 memory:fc100000-fc11ffff memory:fc324000-fc324fff ioport:1820(size=32)


Any help would be greatly appreciated.

---

### Post by kjohri on 2012-09-14
Try the command,

sudo rfkill unblock all

---

