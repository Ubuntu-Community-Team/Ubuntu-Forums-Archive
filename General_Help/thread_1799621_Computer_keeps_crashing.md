---
title: "Computer keeps crashing"
date: 2011-07-07
forum: General Help
---

### Post by Tuskator on 2011-07-07
I have a 2005 emachines desktop tri-booting WinXP, Puppy Linux 5.2.5, and Ubuntu 10.04 LTS AMD64. I installed Ubuntu 10.04 LTS today from DVD and ran the update manager. The only other package I've installed is GParted. The computer has crashed twice today. Once when using Firefox and once while idling. Pictures off screen are attached.

Specs:
871 MiB of memory
AMD Athlon(tm) 64 Processor 3200+
160GB hardrive, 19 GB Ubuntu partition, 1 GB swap partition, rest ntfs WinXP
60GB hardrive, 1GB Puppy partition, rest ntfs data partition
Hardware:
Internal graphics card (VGA), keyboard, and mouse
Using wireless USB adapter to access  internet (Netgear WG111v2)
Has one CD drive and one DVD drive

---

### Post by Tuskator on 2011-07-08
It crashed again this time running firefox doing normal web browsing. A picture of the screen is attached. Any help fixing this crash problem would be appreciated.

---

### Post by Tuskator on 2011-07-10
I took out both harddrives and put in a 160GB harddrive I had laying around to see if it would help. Nope; it crashed while the live cd of ubuntu 10.04 was installing ubuntu(Picture attached). I think it might be the graphics card causing the trouble so I'll stick in a DVI card I have although the graphics card I have now is on-board so I can't remove it. Any help for disabling the old card or advise on fixing this?

edit: Also the new card is a Geforce FX 5200 128MB PCI

---

### Post by cbraxton on 2011-07-10
I would test the hardware and visually check for blown capacitors on the motherboard. (E-machines are cheaper for a reason, they tend to be built with the cheapest available components though of course any system can develop hardware faults.)

---

### Post by Tuskator on 2011-07-10
I tried the new card but the screen was blank on boot even before the computer loaded grub. Any suggestions?

---

### Post by Tuskator on 2011-07-10
> **cbraxton said:**
> I would test the hardware and visually check for blown capacitors on the motherboard. (E-machines are cheaper for a reason, they tend to be built with the cheapest available components though of course any system can develop hardware faults.)

Could you explain "test the hardware" more?

---

### Post by Tuskator on 2011-07-10
I looked and nothing seemed to have blown. I don't think that could be the problem because windows worked fine with the exception of its fair share of viruses.

---

### Post by Tuskator on 2011-07-10
here is the result of lspci
```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 04)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

```
and lspci |grep VGA
```
$ lspci |grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
```

Does anyone know if Radoen Xpress 200g has any problems with ubuntu?

---

### Post by wildmanne39 on 2011-07-11
Hi, there are some known issues with ati drivers have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Also some people with those cards can fix there issue by doing what is mentioned in this link.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by Tuskator on 2011-07-15
Thanks, I'll look at them later today or tomorrow when I have more time.

---

### Post by linuxuser12345 on 2011-07-15
I have had issues like this before, too. Try using Ubuntu 10.10 or 11.04. That will probably fix your problem.

---

### Post by Tuskator on 2011-07-19
> **wildmanne39 said:**
> Hi, there are some known issues with ati drivers have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Also some people with those cards can fix there issue by doing what is mentioned in this link.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

I started the proccess on the 1st link but then realized my  wireless adapter isn't reconized anymore (a Netgear WG111v2). I am trying to install a Trendnet TEW-424UB laying around with ndiswrapper. I'll post back when/if I get it to work.

I did find fglrx files with both  ```
$ dpkg -l '*fglrx*'
``` and ```
$ locate fglrx
``` so that could be the problem.

Also on the 2nd link I couldn't find the OpenGL tab.

---

