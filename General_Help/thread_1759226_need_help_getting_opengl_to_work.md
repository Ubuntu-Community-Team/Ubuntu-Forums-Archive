---
title: "need help getting opengl to work"
date: 2011-05-15
forum: General Help
---

### Post by alfe256 on 2011-05-15
i was following this tutorial [http://www.youtube.com/watch?v=wEJr3IUPk-c](http://www.youtube.com/watch?v=wEJr3IUPk-c) for opengl, it has me install sdl1.3 and freeglut3, after installing, i use the sdl test and i get an error in the terminal saying "no opengl support on this system". also installed the video drivers for my nvidia card. what should i do?

---

### Post by josephmills on 2011-05-15
please post ```
lspci -nn
```

---

### Post by alfe256 on 2011-05-15
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 13)
00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13)
00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:14.3 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers [8086:3438] (rev 13)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
00:1c.2 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 [8086:3a44]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
01:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
02:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller [1b4b:9123] (rev 10)
02:00.1 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:91a4] (rev 11)
03:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [Geforce GTX 570] [10de:1081] (rev a1)
03:00.1 Audio device [0403]: nVidia Corporation GF110 High Definition Audio Controller [10de:0e09] (rev a1)
06:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
07:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
08:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6121 SATA II Controller [11ab:6121] (rev b2)
09:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70)

---

