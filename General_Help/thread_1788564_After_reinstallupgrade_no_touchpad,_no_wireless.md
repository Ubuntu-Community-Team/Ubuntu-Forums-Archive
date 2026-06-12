---
title: "After reinstall/upgrade no touchpad, no wireless"
date: 2011-06-22
forum: General Help
---

### Post by smcrossman on 2011-06-22
This may actually (likely is) be two issues.  But since both are happening since I did a reinstall (my term I think you all call it a upgrade 11.04-11.04) I thought I'd lump them together first.

My dell Inspiron mini has (of course) a touchpad and the wireless adapter is AR9285.  The touchpad is not being recognized (although in a brief boot up into windows 7 it is fine there).  I've tried adding backports, as I found in the documentation, but I'm lost.  The wireless adaptor is being identified but the network is being shown as unclaimed.  It too worked in Windows, so I'm fairly sure that although both worked fine after initial install, something was lost in the recent upgrade.

My problem is I don't know what to do for either issue next.  Most of the documentation is on earlier Ubuntu releases (not 11.04) and I am not ready to backup in order to do a clean install right now.  I have a new install I'm cleaning up and a clean reinstall that I just finished and am reloading backed up files onto.  

I'm hoping I'm missing something simple on this one...just once that would be really nice!  So any quick answers? Do I need to split them into 2 issues and post elsewhere?

---

### Post by smcrossman on 2011-06-22
Okay....I figure someone is going to want to see at least one of these so here they are:  iwconfig, lspci, & lshw....not sure what exactly you might need for the touchpad....let me know.....

```
suzanna@Corky:~$ [COLOR=Navy]iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

suzanna@Corky:~$ [COLOR=Navy]lspci[/COLOR]
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]

```
[COLOR=Navy]
sudo lshw -C network[/COLOR]
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:f7:bd:f7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.70 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0f20000-f0f20fff memory:f0f10000-f0f1ffff memory:f0f40000-f0f5ffff
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0a00000-f0a0ffff

```

---

### Post by smcrossman on 2011-06-23
<bump>

---

### Post by smcrossman on 2011-07-17
Well this is now solved although I'm not sure how/why.  I have had to do a lot of stuff in windows because of issues with my iPhone.  In the process I have also completely changed internet access.  I also went into the Windows files while over there and copied the driver packages (from the system files) onto my desktop in preparation  of trying to install them in Ubuntu.  Basically the next time I went into Ubuntu both the touchpad and the wifi adapter were working fine.  How very strange....

Of course update manager installed a lot of updates in Ubuntu as well so maybe it was just a corrupted or outdated file somewhere.

---

