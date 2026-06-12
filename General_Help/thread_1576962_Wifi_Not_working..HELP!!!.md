---
title: "Wifi Not working..HELP!!!"
date: 2010-09-18
forum: General Help
---

### Post by fish123 on 2010-09-18
hi,

I am using Dell vostro A480 series laptop. Not able to detect wireless card/network.

details below:

fish@fish-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:e2:48:dc  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee2:48dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096353 (1.9 MB)  TX bytes:351741 (343.4 KB)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70100 (68.4 KB)  TX bytes:70100 (68.4 KB)

fish@fish-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:e2:48:dc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.5 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


please hELP!!!!

---

### Post by fish123 on 2010-09-18
hi,

I am using Dell vostro A480 series laptop. Not able to detect wireless card/network.

details below:

**fish@fish-laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:22:19:e2:48:dc  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee2:48dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096353 (1.9 MB)  TX bytes:351741 (343.4 KB)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70100 (68.4 KB)  TX bytes:70100 (68.4 KB)

**fish@fish-laptop:~$ sudo lshw -C network**
  *-network UNCLAIMED     
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:e2:48:dc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.5 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


please hELP!!!!

---

### Post by realzippy on 2010-09-18
Is there any driver offered in System/Administration/HardwareDrivers?
If not,have you tried to install the madwifi driver for your card (atheros-ar242)?
E.g. here:
[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

---

### Post by mörgæs on 2010-09-18
Please don't double-post.

---

