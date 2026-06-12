---
title: "Can't connect to internet"
date: 2009-08-16
forum: General Help
---

### Post by bizhat on 2009-08-16
Hi,

I installed Ubuntu on my pc as dual boot with windows.

Everything worked fine. I can connect to internet.

My computer have 2 LAN cards. One connect to internet through DSL modem. Other connect to other computers on local network (LAN).

After i try to share internet as per

[http://webhostingneeds.com/Internet_sharing_in_linux](http://webhostingneeds.com/Internet_sharing_in_linux)

I was able to share internet. Other pc on network was able to access internet.

When i checked after a day, i can't connect to Internet or even modem internal pages.

I tried to modify network conguration. After many try, now network setting is a mess.

Here is my settings

> 
root@boby-desktop:/etc/network# cat interfaces 
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp


root@boby-desktop:/etc/network# lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
root@boby-desktop:/etc/network# 


ifconfig result is

> 
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:48:fa:51  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe48:fa51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10854 (10.8 KB)
          Interrupt:251 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:80:48:46:63:9d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fe46:639d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13456 (13.4 KB)  TX bytes:7212 (7.2 KB)
          Interrupt:17 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:142361 (142.3 KB)  TX bytes:142361 (142.3 KB)

When i use windows, following are the network configuratiion

LAN CARDS

> 
Realtek RTL8139 Family PCI Fast Ethernet NIC (CONNECT TO DSL MODEM)
Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC	(connect to LAN)



ipconfig


> 
Windows IP Configuration

Ethernet adapter MODEM:

   Connection-specific DNS Suffix  . : 
   IP Address. . . . . . . . . . . . : 192.168.1.2
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Ethernet adapter LAN:

   Connection-specific DNS Suffix  . : 
   IP Address. . . . . . . . . . . . : 192.168.0.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 


Can anyone tell how to restore network in ubuntu to its orginal state so i can connect to internet (just internet is fine, sharing is secondary, not important).

Thanks,

Santhosh

---

