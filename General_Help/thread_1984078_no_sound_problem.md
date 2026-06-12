---
title: "no sound problem"
date: 2012-05-21
forum: General Help
---

### Post by koloss on 2012-05-21
Hey guys
 
I am using Ubuntu 12 on my Sylvania gnet  13001 and there is no sound at all , I tried Ubuntu help but none of there ways works I even tried ''alsamixer'' (I don't actually know what to do with it all what I did is playing with the master sound) please I need help

---

### Post by raja.genupula on 2012-05-21
post the output of ```
lspci 
```

and have you gone through this ?? [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) 

[https://wiki.ubuntu.com/Audio](https://wiki.ubuntu.com/Audio)

---

### Post by koloss on 2012-05-21
00:00.0 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge (rev 10)
00:00.1 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. CX700/VX700 RAID Controller
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. CX700/VX700 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. CX700/VX700 Internal Module Bus
00:13.0 PCI bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. CX700/VX700 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] (rev 03)
02:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
03:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by hal8000 on 2012-05-21
Yoor sound is on your motherboard, a VIA chipset:

02:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)


Did you get sound with the Ubuntu CD in live mode?


Have a look at this thread, it may help:

[http://ubuntuforums.org/showthread.php?t=1894474](http://ubuntuforums.org/showthread.php?t=1894474)

---

### Post by koloss on 2012-05-25
no i didn't ,and the thread didn't also work with me because i didn't know what to do

---

