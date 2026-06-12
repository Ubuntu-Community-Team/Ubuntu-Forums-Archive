---
title: "Wireless internet drops when idle"
date: 2010-02-04
forum: General Help
---

### Post by tonytouch0099a on 2010-02-04
since ive upgraded to ubuntu 9.10 i have noticed that when i leave my computer for a while or just stop using it or leave it idling my internet connection drops.  my comp doesnt hibernate or go to stand by.  does anyone know any reasons for this? or know how to stop this?  its hard to download something when my comp drops the internet connection.

any help would be great.  thanks

---

### Post by spiderbatdad on 2010-02-04
I don't know if anyone can properly help you without a little more information. Certainly the model of the wireless card should help. In your terminal run ```
sudo lshw -C net
``` and copy the output into another post in this thread.

---

### Post by hryanjones on 2010-04-13
Hi there,

I realize this post is a bit old now, but I'm having a similar problem and willing to do a little command line legwork.  First, as a bit of a primer I'm running 9.10 on an Acer AspireOne Netbook (model ZG5).

Another clue might be that it doesn't seem to have the same dropping tendencies when it's plugged in, only when it's on battery (maybe a power setting that turns off wireless and fails to turn it back on).

Following is the monstrous output of
>>> sudo lshw -C net


 [I]*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:f8:d0:82
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:7d:5e:38
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.10 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:55200000-5520ffff
[/I]

Thanks for any help or hints you can provide!

---

### Post by hryanjones on 2010-04-13
Another clue.  A cursory glance at the output of ifconfig shows this device a **wlan0** device before the idling but not after.

---

