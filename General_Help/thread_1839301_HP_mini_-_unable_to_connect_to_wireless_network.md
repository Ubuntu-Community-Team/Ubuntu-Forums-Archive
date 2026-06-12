---
title: "HP mini - unable to connect to wireless network"
date: 2011-09-05
forum: General Help
---

### Post by jeropon on 2011-09-05
I need help connecting to my wireless network, and I would greatly appreciate any help I can get. I replaced windows XP with ubuntu v11 yesterday, and I'm unable to connect to my wireless network, which is still running; I have another laptop. My mini does not have a port for a network cable. From the threads I have looked at, the following commands seem to be important, so I have provided the output below for starters
**[FONT=Batang]lshw -c network[/FONT]**
**[FONT=Batang]nm-tool[/FONT]**
 
 
**[FONT=Batang][SIZE=3]sudo lshw -c network[/SIZE][/FONT]**
 
[SIZE=3][FONT=Batang]PCI (sysfs) [/FONT][/SIZE]
[SIZE=3][FONT=Batang]*-network [/FONT][/SIZE]
[SIZE=3][FONT=Batang]description: Network controller[/FONT][/SIZE]
[SIZE=3][FONT=Batang]product: BCM4312 802.11b/g LP-PHY[/FONT][/SIZE]
[SIZE=3][FONT=Batang]vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Batang]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]bus info: pci@0000:01:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]version: 01[/FONT][/SIZE]
[SIZE=3][FONT=Batang]width: 64 bits[/FONT][/SIZE]
[SIZE=3][FONT=Batang]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Batang]capabilities: pm msi pciexpress bus_master cap_list[/FONT][/SIZE]
[SIZE=3][FONT=Batang]configuration: driver=b43-pci-bridge latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]resources: irq:16 memory:feafc000-feafffff[/FONT][/SIZE]
[SIZE=3][FONT=Batang]*-network[/FONT][/SIZE]
[SIZE=3][FONT=Batang]description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Batang]product: 88E8040 PCI-E Fast Ethernet Controller[/FONT][/SIZE]
[SIZE=3][FONT=Batang]vendor: Marvell Technology Group Ltd.[/FONT][/SIZE]
[SIZE=3][FONT=Batang]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]bus info: pci@0000:02:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]logical name: eth0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]version: 00[/FONT][/SIZE]
[SIZE=3][FONT=Batang]serial: 00:24:81:46:67:6e[/FONT][/SIZE]
[SIZE=3][FONT=Batang]capacity: 100Mbit/s[/FONT][/SIZE]
[SIZE=3][FONT=Batang]width: 64 bits[/FONT][/SIZE]
[SIZE=3][FONT=Batang]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Batang]capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
[SIZE=3][FONT=Batang]configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair[/FONT][/SIZE]
[SIZE=3][FONT=Batang]resources: iomemory:ffffffff0-fffffffef irq:42 memory:febfc000-febfffff ioport:ec00(size=256)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]*-network DISABLED[/FONT][/SIZE]
[SIZE=3][FONT=Batang]description: Wireless interface[/FONT][/SIZE]
[SIZE=3][FONT=Batang]physical id: 1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]logical name: wlan0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]serial: 00:24:2b:bf:23:5a[/FONT][/SIZE]
[SIZE=3][FONT=Batang]capabilities: ethernet physical wireless[/FONT][/SIZE]
[SIZE=3][FONT=Batang]configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE]
 
[FONT=Batang][SIZE=3]---------------------------------------------------------[/SIZE][/FONT]
[SIZE=3][FONT=Batang]**nm-tool**[/FONT][/SIZE]
 
[FONT=Batang][SIZE=3]NetworkManager Tool[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]State: disconnected[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]- Device: eth0 -----------------------------------------------------------------[/SIZE][/FONT]
[SIZE=3][FONT=Batang]Type: Wired[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Driver: sky2[/FONT][/SIZE]
[SIZE=3][FONT=Batang]State: unavailable[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Default: no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]HW Address: 00:24:81:46:67:6E[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Capabilities:[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Carrier Detect: yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Wired Properties[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Carrier: off[/FONT][/SIZE]
 
 
[FONT=Batang][SIZE=3]- Device: wlan0 ----------------------------------------------------------------[/SIZE][/FONT]
[SIZE=3][FONT=Batang]Type: 802.11 WiFi[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Driver: b43[/FONT][/SIZE]
[SIZE=3][FONT=Batang]State: unavailable[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Default: no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]HW Address: 00:24:2B:BF:23:5A[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Capabilities:[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Wireless Properties[/FONT][/SIZE]
[SIZE=3][FONT=Batang]WEP Encryption: yes[/FONT][/SIZE]
[SIZE=3][FONT=Batang]WPA Encryption: yes[/FONT][/SIZE]
[SIZE=3][FONT=Batang]WPA2 Encryption: yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Wireless Access Points[/FONT][/SIZE]

---

