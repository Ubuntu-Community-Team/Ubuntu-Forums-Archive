---
title: "Having Wifi connection issues 11.04"
date: 2011-12-07
forum: General Help
---

### Post by LibmasterLib on 2011-12-07
I'm using Ubuntu 11.04 on a borderline 4 year old HP Pavillion dv6000 laptop and a D-Link DIR-615 wireless router

The past few months I've noticed a lot of issues when it comes to connecting to wireless internet.  I have been having a lot of trouble connecting to my wireless network.  A lot of the time I'm completely unable to get connected to it, and my roommates wont have an issue.  I can still connect to other routers, but with some the performance is much slower than with people on other laptops & devices.

I think that maybe my wireless card is dying, but I'd like to rule out other possible problems before I look into buying a new one.  Has anyone else here had issues with connecting to wireless routers, especially D-Link ones?

Thanks for any advice/support!

---

### Post by josephmills on 2011-12-07
> **LibmasterLib said:**
> I'm using Ubuntu 11.04 on a borderline 4 year old HP Pavillion dv6000 laptop and a D-Link DIR-615 wireless router

The past few months I've noticed a lot of issues when it comes to connecting to wireless internet.  I have been having a lot of trouble connecting to my wireless network.  A lot of the time I'm completely unable to get connected to it, and my roommates wont have an issue.  I can still connect to other routers, but with some the performance is much slower than with people on other laptops & devices.

I think that maybe my wireless card is dying, but I'd like to rule out other possible problems before I look into buying a new one.  Has anyone else here had issues with connecting to wireless routers, especially D-Link ones?

Thanks for any advice/support!

Hello there and Welcome to Ubuntu Forums !! 

could you please open you terminal (ctrl+alt+t) and  enter 
```
sudo lshw -c network && lsmod && lsusb && lspci -nn && rfkill list all  
```


And paste here thanks .

---

### Post by oldtimer7777 on 2011-12-07
I've had really great results using the Dlink USB wireless adapter than the PCMCI cards, and even the internet Wifi on some specific models/make laptops/notebook computers. 

> **LibmasterLib said:**
> I'm using Ubuntu 11.04 on a borderline 4 year old HP Pavillion dv6000 laptop and a D-Link DIR-615 wireless router

The past few months I've noticed a lot of issues when it comes to connecting to wireless internet.  I have been having a lot of trouble connecting to my wireless network.  A lot of the time I'm completely unable to get connected to it, and my roommates wont have an issue.  I can still connect to other routers, but with some the performance is much slower than with people on other laptops & devices.

I think that maybe my wireless card is dying, but I'd like to rule out other possible problems before I look into buying a new one.  Has anyone else here had issues with connecting to wireless routers, especially D-Link ones?

Thanks for any advice/support!

---

### Post by LibmasterLib on 2011-12-07
> **josephmills said:**
> could you please open you terminal (ctrl+alt+t) and  enter 
```
sudo lshw -c network && lsmod && lsusb && lspci -nn && rfkill list all  
```


And paste here thanks .

Here's what I got
```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:ae:6c:ad
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.102 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:9d:34:c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f6000000-f6003fff
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by josephmills on 2011-12-07
please read 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)


you need the b43 not the wl
try this 
```
sudo rmmod wl* && sudo modprobe b43 && dmesg | grep b43 
```
then paste here (or just look and read link) :D

---

