---
title: "Wireless Greyed Out - Ubuntu 9.04"
date: 2009-11-14
forum: General Help
---

### Post by ameerical on 2009-11-14
I recently reformatted my xp tower with a clean install of Ubuntu 9.04, I tried establishing a network connection with my router but nothing seems to be working, 

here are my stats:

   main@main-desktop:~$ sudo lshw -C network
    *-network:0             
         description: Network controller
         product: BCM4306 802.11b/g Wireless LAN Controller
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:01:00.0
         version: 03
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master
         configuration: driver=b43-pci-bridge latency=32 module=ssb
    *-network:1
         description: Ethernet interface
         product: 82801BA/BAM/CA/CAM Ethernet Controller
         vendor: Intel Corporation
         physical id: 8
         bus info: pci@0000:01:08.0
         logical name: eth0
         version: 03
         serial: 00:02:55:a5:2a:17
         size: 10MB/s
         capacity: 100MB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
    *-network:0 DISABLED
         description: Wireless interface
         physical id: 1
         logical name: wlan0
         serial: 00:0f:66:1e:36:56
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
    *-network:1 DISABLED
         description: Ethernet interface
         physical id: 2
         logical name: pan0
         serial: 7e:32:5f:e8:5f:df
         capabilities: ethernet physical
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by SPr on 2009-11-14
Take a look here [http://ubuntuforums.org/search.php?searchid=66774896](http://ubuntuforums.org/search.php?searchid=66774896)

or here... [http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

---

