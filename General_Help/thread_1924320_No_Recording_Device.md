---
title: "No Recording Device"
date: 2012-02-12
forum: General Help
---

### Post by pinbill on 2012-02-12
Hello,

I am trying to set up skype and I can't get the mic to work. Have been messing around with pulse audio while on the skype test call. Please help,

Thanks,

Bill

---

### Post by linoseros on 2012-02-12
Could you past what shows the command lspci and tell us what version of ubuntu you have ?

---

### Post by pinbill on 2012-02-12
Here are the results:

Ubuntu 10.4

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 57)
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

Thanks,

---

### Post by ajgreeny on 2012-02-12
> **pinbill said:**
> Hello,

I am trying to set up skype and I can't get the mic to work. Have been messing around with pulse audio while on the skype test call. Please help,

Thanks,

Bill
What do you mean by "Have been messing around with pulse audio while on the skype test call.?  Do you have pavucontrol installed?  If you don't then sudo apt-get install pavucontrol will get it for you and then you can open **pulseaudio-volume-control** and play around some more.

Also worth running ```
alsamixer
``` in terminal and checking that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture", where you can navigate to **mic** and hit spacebar if it is not enabled.  If it's enabled it will show
```
[COLOR=Red]L     R
CAPTURE[/COLOR]
```above it
Esc will save and exit.

---

### Post by pinbill on 2012-02-12
Thanks for the reply, I have pulse audio installed. I played with pavucontrol and I ended up getting it working but it is not that great. The sound is kind of staticy. I think I might use the desktop to skype with windows and install ubuntu 11.10 on my laptop to surf and download. 

Thanks again for your help,

Bill

---

