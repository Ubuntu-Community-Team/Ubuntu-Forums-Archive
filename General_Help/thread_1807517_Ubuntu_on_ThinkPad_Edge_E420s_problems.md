---
title: "Ubuntu on ThinkPad Edge E420s problems"
date: 2011-07-19
forum: General Help
---

### Post by AugustinZ on 2011-07-19
Hello,

I've installed Kubuntu 11.04 (64 bit) on my ThinkPad Edge E420s laptop and certain things are not working.

**1) Battery charging [Priority: HIGH]** - when I plug the laptop in, KDE battery applet says "n% (Charged)" but not "Charging" and the percentage remains on n%. What should I do to get it charge itself?

**2) [SOLVED, see the link] Wireless [Priority: HIGH]** - not working at all, I installed the official driver from Realtek, but not working either. For more info see [http://askubuntu.com/questions/53625/wireless-on-thinkpad-edge-e420s/53710#53710]("http://askubuntu.com/questions/53625/wireless-on-thinkpad-edge-e420s/53710#53710") 

**3) Display brightness [Priority: LOW]** - I can't adjust the display brightness from KDE. I can adjust it using the hardware buttons, but I would like to be able to adjust it from the KDE as well.


Advanced info:
I've got Win7 installed beside Kubuntu where everything is working, so these things MUST be software issues.

lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
0c:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
0c:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

acpi -V
```
Battery 0: Unknown, 4%
Battery 0: design capacity 3455 mAh, last full capacity 3383 mAh = 97%
Adapter 0: on-line
Thermal 0: ok, 29.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10

```


Some additional questions:
1) Is the situation better in some other distro?
2) Should I give a try to Ubuntu? Is it better then Kubuntu in these things?
3) Should I try 32bit version of Kubuntu? Is the situation different there?
4) Are the things on my laptop not working just because it is new and the developers didn't get enough time yet to fix the issues? Is the situation going to be better in 11.10? 


Thanks for your time and help in advance.

---

