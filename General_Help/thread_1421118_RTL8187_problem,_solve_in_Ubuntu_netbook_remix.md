---
title: "RTL8187 problem, solve in Ubuntu netbook remix"
date: 2010-03-03
forum: General Help
---

### Post by agolasol on 2010-03-03
my desktop pc has RTL8187 usb wireless lan. when i install UBUNTU, wifi wont work just stay connected but cant browse. i downloaded and install the latest driver of said wireless card still wont work. I try kubuntu, xubuntu, debian, fedora but still cant browse. 

When i installed Ubuntu netbook remix in my Desktop pc, I was surprised that the wireless work flawlessly and no problem in browsing, downloading and even using aircrack-ng.

I just disabled the notebook luncher during start-up to remove netbook interface. And look like standard UBUNTU.

My Desktop PC specs is:
Intel Celeron dual e1200
2g 667 Ram kingston
ECS 945GCT-m2/1333
Nvidia Geforce 7200gs 256mb
80g harddisk samsung sata
realtek 8187 usb wireless lan

Just want to share.

---

### Post by cariboo on 2010-03-04
Check to see what driver is used on the netbook by opening a terminal and typing:

```
sudo lshw -C network
```

Look for driver= in the output, then check to see if your desktop is using the same driver.

---

### Post by agolasol on 2010-03-04
hi!

my eeepc 2g surf running standard ubuntu in SDHC. my deskstop pc running UNR. 
i cant browse when i put the realtek8187 usb wireless adapter in eeepc 2g surf.

anyway i will run that command in my desktop with UNR and my eeepc with standard ubuntu. with that said wireless plug in desktop then  eeepc.

Im using 9.10 karmic kuala.

---

### Post by agolasol on 2010-03-04
**IN MY DESKTOP PC**

jok@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:21:97:84:0c:1c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:ef:09:a9:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11bg
jok@ubuntu:~$ 


I dont see any driver data last part unlike in eth0



[B]IN MY EEE PC 2G SURF

[/B]jok@jok:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:c9:33:9c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:78:14:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fbef0000-fbefffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan2
       serial: 00:1a:ef:09:a9:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
jok@jok:~$ 


DO I HAVE TO INSTALL STANDARD UBUNTU 9.10 IN MY DESKTOP JUST TO VERIFY?

---

