---
title: "Upgrading from II8.10 to JJ9.04"
date: 2009-09-11
forum: General Help
---

### Post by ww711 on 2009-09-11
Currently running II 8.10 on a Compaq nx6325 laptop perfectly with 3rd party drivers and was considering upgrading to JJ 9.04 but had reservations because of my existing hardware and previously getting II 8.10  to work with the hardware was quite a task. I've run the 9.04 live CD on my laptop, everything seems to function fine when I'm using the live CD though when I try to activate the Broadcom STA driver it says I have to reboot, but this wont' work because it reboots the whole system and stopping the live cd session. 

lspci 

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]**
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
**30:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)**
```

Unsure whether to upgrade or not...though I have a working system, it'd be good to upgrade the distro to 9.04, or even wait for KK 9.10? Will my hardware be easy to get up and running with 9.10 when it's out? Any recommendations?

---

### Post by Ocxic on 2009-09-11
if your worried just make an image of you hard drive if you can before the update, if anything goes wrong you'll be able to restore your whole system.

---

### Post by pastalavista on 2009-09-11
> 01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
I have the same graphics card and Jaunty can't use the 3D acceleration very well yet without a downgrade of the xserver. I did the upgrade because I don't game or use intense graphics programs or compiz. Jaunty boots faster and runs cooler and has the ext4 filesystem.

ps.. your wireless will work fine after you use a wired connection to install the drivers

pps.. you can't upgrade directly from 8.10 to 9.10... have to upgrade twice. best to do a clean install (after backing up your /home)

---

### Post by ww711 on 2009-09-12
> **pastalavista said:**
>  Jaunty boots faster 

I decided to upgrade and agree that Jaunty does a boot a lot faster compared to Intrepid

> **pastalavista said:**
>  ps.. your wireless will work fine after you use a wired connection to install the drivers 

Yep it worked first time without any configuration using the Broadcom wireless sta driver

---

