---
title: "Wireless Internet is trolling me again."
date: 2012-02-02
forum: General Help
---

### Post by Asad3ainJalout on 2012-02-02
So ever since i re installed windows 7 Ultimate i have been having trouble with my wireless and Ethernet. At first my windows was not working, that was solved by installing the proper drivers. After that my ubuntu 11.10 would not work. I downgraded to the 10.04 and it still would not work. I finally got the wireless to work but it only works on my school's campus and will refuse to connect to my wireless at home. It will not connect via wire either. I am currently on ubuntu 10.10

---

### Post by TeoBigusGeekus on 2012-02-02
What's your hardware?
Can you post the output of
```
sudo lshw -C network
```
?

---

### Post by Asad3ainJalout on 2012-02-02
Okay, here it is, sorry for the late replay wife was on skype. Had to wait for her.
```
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 20:7c:8f:0c:61:dc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:7000(size=256) memory:f3100000-f3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
version: c1
       serial: c8:0a:a9:85:61:ca
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f3000000-f303ffff ioport:6000(size=128)


```

Edit: changed from quote to Code.

---

### Post by TeoBigusGeekus on 2012-02-02
Ah, the atheros junk again...
See [this]("http://ubuntuforums.org/showthread.php?t=1505697") thread.

---

