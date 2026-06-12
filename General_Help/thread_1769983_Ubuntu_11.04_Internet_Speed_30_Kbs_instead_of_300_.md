---
title: "Ubuntu 11.04 Internet Speed 30 Kb/s instead of 300 Kb/s"
date: 2011-05-28
forum: General Help
---

### Post by Toten on 2011-05-28
Hello everyone.

First of all, thank you for your help.

I recently installed Ubuntu 11.04 on my laptop with Windows Vista. Everything is working fine, but my Internet speed; specifically my download speed, is very slow. For example, in Windows Vista I usually download at 300 Kb/s, but now (Ubuntu 11.04) I am downloading at 30 - 50 Kb/s.

Here is some information you might find useful:

**lspci | grep Wir**
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

**sudo lshw -C network**
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:96:ee:27
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:f6:5c:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.40.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:d3200000-d320ffff

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1e:33:96:ee:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:f6:5c:0f  
          inet addr:192.168.40.100  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fef6:5c0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10017929 (10.0 MB)  TX bytes:2629973 (2.6 MB)

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Casa-Wifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:0F:EB:B5:D4   
          Bit Rate=48 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:82   Missed beacon:0

---

