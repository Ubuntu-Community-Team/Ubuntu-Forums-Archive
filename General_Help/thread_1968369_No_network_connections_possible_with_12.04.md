---
title: "No network connections possible with 12.04"
date: 2012-04-29
forum: General Help
---

### Post by jamesisin on 2012-04-29
I have this eMachines laptop I built to test the latest LTS before I start building it for folks.  I am running the 64 bit version of 12.04 on this system.

I have neither a wireless nor a wired connection available.  The wireless kindly tells me "device not ready (Firmware missing)"; however, I won't be able to use the wired connection to do anything about it.

Anyone want to have a go at helping me with this one?

(eMachines m6805)

---

### Post by jamesisin on 2012-04-29
By the way the wired connection was working under 10.04...

---

### Post by jamesisin on 2012-05-02
Anybody?

---

### Post by jamesisin on 2012-05-15
Network driver experts?

---

### Post by roelforg on 2012-05-15
```

sudo lshw -C network
sudo ifconfig -a
sudo lspci
cat /etc/resolv.conf
cat /etc/network/interfaces

```
Run those commands and wait until your prompt comes back (the first one may take a while).
Post the output

---

### Post by jamesisin on 2012-05-15
Sanitized for your reading pleasure...

```
$ sudo lshw -C network
[sudo] password for [me]: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:0d:9e:3a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.100.230 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:1800(size=256) memory:d0002c00-d0002cff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:7b:46:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:0d:9e:3a  
          inet addr:[IP.Addrs.my.network]  Bcast:[IP.Addrs.my.network]  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe0d:9e3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34408 errors:0 dropped:0 overruns:0 frame:1
          TX packets:28030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32543526 (32.5 MB)  TX bytes:4524589 (4.5 MB)
          Interrupt:23 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1133045 (1.1 MB)  TX bytes:1133045 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:7b:46:37  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 [Mobility Radeon 9600 M10]

$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search [MyNetwork].local

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

$
```

---

