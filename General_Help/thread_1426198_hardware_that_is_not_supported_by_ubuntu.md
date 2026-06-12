---
title: "hardware that is not supported by ubuntu"
date: 2010-03-10
forum: General Help
---

### Post by nonedrinkwater on 2010-03-10
i never thought i would see this day... 

so here are my specs. 

2.8 pent d
dga 865 sa intel mobo
2 gigs ddr2 kingston
audigy 1394
netgear wireless 
6600 gt

none of my devices work. no sound no network not even a decent resolution for my monitor. 

everything on my dell 700m works without drivers or tinkering. 

what gives??

---

### Post by Fafler on 2010-03-10
Audigy cards are badly supported. There's supposed to be a binary driver, but i haven't tried it and from what i've heard, it's not that good.

The 6600 GT, it's very well supported, but you need the binary Nvidia driver which is not installed by default. Go to System -> Administration -> Hardware Drivers.

As for the Netgear, i can't tell you anything before i know the exact model.

---

### Post by IcarusR on 2010-03-10
Rather than saying > hardware that is not supported by ubuntu search the forum & internet or start a thread asking for help.

Post output of lspci from a terminal & we may be able to help you

---

### Post by nonedrinkwater on 2010-03-18
ls pci
ls: cannot access pci: No such file or directory
[EMAIL="kefka@ubuntu:~$"]kefka@ubuntu:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
02:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

---

### Post by nonedrinkwater on 2010-03-19
bump

---

### Post by nonedrinkwater on 2010-03-23
bump

---

### Post by Muzer on 2010-03-23
Could you please give the output of:

lspci -nn


(This command displays device numbers as well as names, which are much easier to search)

(Don't know why the previous poster didn't ask for the -nn version)

---

### Post by nonedrinkwater on 2010-03-23
i never thought i would see this day... 

so here are my specs. 

2.8 pent d
dga 865 sa intel mobo
2 gigs ddr2 kingston
audigy 1394
netgear wireless 
6600 gt

none of my devices work. no sound no network not even a decent resolution for my monitor. 

everything on my dell 700m works without drivers or tinkering. 

what gives??



----------------

kefka@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
02:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

---

### Post by cariboo on 2010-03-23
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by nonedrinkwater on 2010-03-24
bump!!

---

### Post by Aped on 2010-03-24
You still have not posted the output of 'lspci -nn'

Another thing you could do instead is 'lshw -html > somefile.html' -- this will be good for your own records as it's easier to read as a human. 

Is it your wireless or wired network adapter that doesn't work? 

put the output of ifconfig and iwconfig in here too, please. 

Anyway, you'll quite possibly end up using ndiswrapper for the Marvell 88w8335; check the sticky at the top of the Networking subforum or this link for more info on that: 
[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

Good luck.

---

### Post by nonedrinkwater on 2010-03-31
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600 GT] [10de:00f1] (rev a2)
02:01.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)
02:04.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 03)
02:04.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001]
&#12288;

---

### Post by nonedrinkwater on 2010-03-31
bump!!!!

---

### Post by nonedrinkwater on 2010-03-31
.....

...
..

---

### Post by nonedrinkwater on 2010-04-01
> **Fafler said:**
> Audigy cards are badly supported. There's supposed to be a binary driver, but i haven't tried it and from what i've heard, it's not that good.

The 6600 GT, it's very well supported, but you need the binary Nvidia driver which is not installed by default. Go to System -> Administration -> Hardware Drivers.

As for the Netgear, i can't tell you anything before i know the exact model.

please advise.

---

### Post by nonedrinkwater on 2010-04-02
> **Muzer said:**
> Could you please give the output of:

lspci -nn


(This command displays device numbers as well as names, which are much easier to search)

(Don't know why the previous poster didn't ask for the -nn version)


...

---

### Post by cascade9 on 2010-04-02
Wireless. Yes, its the same link as Aped-

[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

nVidia 6600GT. Yes, its the same as what Fafler said- 

Go to System -> Administration -> Hardware Drivers.

There should be a fix for the audigy, but untill you actually try out what over people have suggested, or at least put in an update saying that some things are now working, I cant be bothered to find it.  ;)

---

### Post by nonedrinkwater on 2010-04-07
bump

---

### Post by nonedrinkwater on 2010-04-20
i cant get it to work...

---

### Post by nonedrinkwater on 2010-04-21
well after the ndiswrapper thing didnt work on my ubuntu i tried it on mandriva and it works beautifully.

---

