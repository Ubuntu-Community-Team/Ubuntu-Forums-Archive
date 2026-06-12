---
title: "[Help] Wirless will no longer turning on??"
date: 2012-09-04
forum: General Help
---

### Post by Knoxorz on 2012-09-04
I'm very confused, I have an acer one netbook, downloaded ubuntu onto it and is now the only OS on the system. everything worked fine... Untill out of the blue I was unable to see my networks and i couldn't connect... but after a while i found the if i went to system network settings, the airplane mode was turned on? (Never touched it befor) and the wireless was off?!! so i turned airplane mode off, and tried to switch the wireless on, but it didn't work.. it will turn on for a split second.... just a fast... every time i click it and turn right back to off... I don't get it... anyone know what might be wrong? Thanks...! (Need it for school!)

---

### Post by handimanmark on 2012-10-07
I had similar symptoms with a Sony Vaio E series 14in. Core i5 with Atheros AR9485 Wireless Network Adapter. the following is from Terminal and the solution for the problem on the Sony is at the bottom.

catherine@LLTF-Mobile:~$  sudo lshw -C network
[sudo] password for catherine: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 84:4b:f5:c4:eb:55
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 30:f9:ed:f1:9b:bc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

catherine@LLTF-Mobile:~$ sudo rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

catherine@LLTF-Mobile:~$ sudo lspci | grep RTL
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

catherine@LLTF-Mobile:~$ sudo rfkill unblock all

Thanks to kurt18947

I hope this helps.

---

