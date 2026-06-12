---
title: "Help a N00b out please - Wireless and Desktop issue"
date: 2011-03-12
forum: General Help
---

### Post by Hollyecho_Montgomery on 2011-03-12
I have been installing Ubuntu, and Kubuntu on computers, and the last one I had installed it on was 3 months ago (ok, I am embarrassed). 

Here is the current problems.
1.  Wireless is installed, indicator light is on, computer recognizes it, but it can not see any wireless networks.  Broadcom Wireless.  Updated, used wicp.  Nothing no networks seen. I have followed so many forums, I have done so many sudo aptgets and updates, and installs, I may have made it worse instead of better.

2.  I have an empty transparent window in the upper left hand side of the desktop that i can not get rid of, or move, or just make disappear.  My Kubuntu on my HP Laptop does not have these issues.  I am trying to put this on a laptop of a friend.  (I fix Win computers for a living, so this is embarrassing to be so inept at getting this great program to work as it should) I have not installed wine yet, wanted to get these issues fixed first, and this time the cure will be written down in k-notes for any future install I will do for people.:confused:

---

### Post by Hollyecho_Montgomery on 2011-03-13
Ok, when I installed wine, the transparent box on the desktop has dissappeared.  What it had to do with the installation of Wine, I have no idea.  Now, just need to figure out the wireless problem.:lolflag:

---

### Post by ugm6hr on 2011-03-13
For wifi - give us more info...
See wifi help link below.

---

### Post by Hollyecho_Montgomery on 2011-03-14
BTW the transparent window is back on my desktop, 
Here are the answers to all the questions you asked on the WiFi page:

lspci
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw -class network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:5c:8e:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.106 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:3000(size=256) memory:e0208800-e02088ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:e0204000-e0205fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b6:39:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg

ISP is irrlevant - All other computers, including another Kubuntu wireless computer is connected.

Kubuntu 10.10

uname -a
Linux jack-Presario 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

Yes, I am connected via Eithernet Cable, yes, I am posting from that computer.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:5c:8e:d5  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe5c:8ed5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:821388 (821.3 KB)  TX bytes:123437 (123.4 KB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640 (640.0 B)  TX bytes:640 (640.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:b6:39:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:5c:8e:d5  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe5c:8ed5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:821388 (821.3 KB)  TX bytes:123437 (123.4 KB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640 (640.0 B)  TX bytes:640 (640.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:b6:39:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jack@jack-Presario:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

Yes, tried open network, it FINDS NO NETWORKS

No This is not a dual boot

---

