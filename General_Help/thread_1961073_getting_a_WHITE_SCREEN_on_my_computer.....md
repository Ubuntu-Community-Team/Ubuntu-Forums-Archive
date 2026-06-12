---
title: "getting a WHITE SCREEN on my computer...."
date: 2012-04-18
forum: General Help
---

### Post by shantiq on 2012-04-18
.... repeatedly in the last few days


never had this before

using 11.10 with nvidia


often happens when using opera but not exclusively


any ideas as to why this could be and any fixes one can think of



thanx:KS


> lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 8400 GS] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)


---

### Post by raja.genupula on 2012-04-18
any new updates installation ?

---

### Post by shantiq on 2012-04-18
well Raja there was that pesky new Flashplayer a week or 2 ago that gave so many of us headaches    it might be related to that

but i simply have my updates done automatically in the background at load-up so not sure about specifics really


what are you thinking?

---

### Post by raja.genupula on 2012-04-18
while in the discussion today , i got to know new Nvidia giving problems to some hardware . give a try with reinstalling your drivers by booting with failsafeX mode in the recovery menu .

---

### Post by wojox on 2012-04-18
I've had a similar problem and installing the older 173.* nvidia driver fixed it. Is that an option?

---

### Post by raja.genupula on 2012-04-18
> **wojox said:**
> I've had a similar problem and installing the older 173.* nvidia driver fixed it. Is that an option?
Hi wojox , an alternative option up to new break got fixed . better to report it to Lp bugs area .

---

### Post by wojox on 2012-04-18
> **raja.genupula said:**
> Hi wojox , an alternative option up to new break got fixed . better to report it to Lp bugs area .

Hey raja, I'm sure one has been filed since this has been an issue for a few releases. Nvidia drivers are closed source so I don't even know what they could do. :p

---

### Post by shantiq on 2012-04-18
> **raja.genupula said:**
> while in the discussion today , i got to know new Nvidia giving problems to some hardware . give a try with reinstalling your drivers by booting with failsafeX mode in the recovery menu .



well tht did not work for me as in recovery all freezes


so i went sysstem settings/additional drivers/   and removed and reinstalled nvidia drivers



does that do the same?

can you please explain a bit more    thanx       shan

---

### Post by raja.genupula on 2012-04-19
If that re-installation wont work for you , then we have only one chance that using of old drivers which are worked for previoulsy as our friend Wojox Suggested  Up to the new drivers will get the Fix ! . 

So look at the older versions of your drivers and install them if this reinstallation not worked .

---

