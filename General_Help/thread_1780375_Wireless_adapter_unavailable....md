---
title: "Wireless adapter unavailable...?"
date: 2011-06-11
forum: General Help
---

### Post by artimeus on 2011-06-11
Hello, 

I am completely new to Linux and Ubuntu. I installed it on an older Compaq Presario V2000 (512MB RAM 40 GB HD ) that was running a bootleg version of Window's 7 (which it could barely handle, wasn't my laptop).

Everything looks great however I cant get the wireless card enabled. I have tried doing some research and have even gone so far as to download some driver's for the wireless card. I know how to get a terminal up, but am having a hard time finding what commands I need to go to get to the driver and see if it's working.

I have found commands to install 
ndiswrapper [FONT=Verdana] and have made sure that's installed correctly but am at a total loss to get the wireless card up besides that. I am a little overwhelmed by the whole idea of terminal commands, so please go easy on me. 

The modem is enabled and the Internet when routed through an Ethernet cord works just fine. But the option to "Endable Wireless" is unavailable. I'm used to Windows and I'm wondering if maybe just the driver for the wireless adapter isn't installed? The wireless button no longer responds.

Sorry if this is the wrong forum for this, but I wasn't sure where to start. Thank you! 
[/FONT]

---

### Post by Synoc on 2011-06-11
first thing to do is type in this

```

lspci

```
and paste the results here. Highlight the text once pasted and click on the # sign to make it "code" so nothing gets chopped off or altered.

---

### Post by artimeus on 2011-06-11
> 
lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
Here you go! :)

---

### Post by wildmanne39 on 2011-06-12
> **artimeus said:**
> Here you go! :)

Hi, follow these directions [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44) and you should get it working.

---

