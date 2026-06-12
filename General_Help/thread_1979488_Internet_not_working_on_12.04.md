---
title: "Internet not working on 12.04"
date: 2012-05-13
forum: General Help
---

### Post by memecs on 2012-05-13
I have both 12.04 and 11.10 installed on the same machine. Internet (both wireless and wired) it's not working on 12.04. Any help?

lshw -C network

```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82567LF-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:21:9b:1b:9e:31
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-5 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f9dc0000-f9ddffff memory:f9df4000-f9df4fff ioport:a080(size=32)
  *-network
       description: Wireless interface
       product: AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:b0:ce:f1:ff
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic firmware=N/A ip=192.168.1.129 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f9ef0000-f9efffff

```

IWCONFIG

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FASTWEB-1-bztAlI1hzEaT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D4:D1:84:02:F0:80   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:914   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by Geffers on 2012-05-13
> **memecs said:**
> I have both 12.04 and 11.10 installed on the same machine. Internet (both wireless and wired) it's not working on 12.04. Any help?



I've had the wifi working and not working on the same installation but with different desktop managers :confused:

I don't use the later version, still on mercat myself.This may be a silly suggestion but if you have a network icon on the taskbar is it enabled.

---

### Post by memecs on 2012-05-13
Networking is enabled :) !

---

### Post by memecs on 2012-05-13
... but still internet is not working... any help?

---

### Post by idoitprone on 2012-05-13
> **memecs said:**
> ... but still internet is not working... any help?


```
lspci -nnk
```

---

### Post by Geffers on 2012-05-13
> **memecs said:**
> ... but still internet is not working... any help?

Does ifconfig show both the wifi and ethernet interfaces.

You could then try ifconfig wlan0 up (might need sudo ifconfig wlan0 up)    if wlan0 is the description of your wifi interface.

Geffers

---

