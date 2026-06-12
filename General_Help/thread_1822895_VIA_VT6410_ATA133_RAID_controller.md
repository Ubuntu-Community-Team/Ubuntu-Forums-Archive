---
title: "VIA VT6410 ATA133 RAID controller"
date: 2011-08-11
forum: General Help
---

### Post by JackHarper on 2011-08-11
I am trying to add additional hard drives to my PC with this PCI to IDE card, however it doesn't recognise any drives. I can see it ok in the disk utility under PATA Host Adapter this is what I get from lspci BTW I am using Natty

media@media-System-Name:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
00:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:0d.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro FX 500/600 PCI] (rev a1)


Any help is much appreciated.

---

### Post by Kira_Belka on 2011-08-11
mmmm.. it has to help [http://ubuntuforums.org/archive/index.php/t-4090.html](http://ubuntuforums.org/archive/index.php/t-4090.html)

---

### Post by JackHarper on 2011-08-11
Link does nothing...


Anyone else??

---

### Post by coffee412 on 2011-08-11
Can you either look at the card and get an actual make and model off it or do a lspci -vv and post the vender and product id? Then we can probably get a pdf on the card and discover more about it.

---

### Post by Kira_Belka on 2011-08-11
> **JackHarper said:**
> Link does nothing...


Anyone else??
:popcorn:

it was just example :P so did you try to find driver on official site of via? and something about link :) 
Asus p4p800 has same controller.. Asus has no bad support service :P

---

### Post by JackHarper on 2011-08-12
00:0d.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
	Subsystem: VIA Technologies, Inc. VT6410 ATA133 RAID controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at b400 [size=8]
	Region 1: I/O ports at b000 [size=4]
	Region 2: I/O ports at a800 [size=8]
	Region 3: I/O ports at a400 [size=4]
	Region 4: I/O ports at a000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

---

### Post by coffee412 on 2011-08-12
Iam reading alot about the chipset in question here for the controller card. 

[http://www.digisland.com/page2.php?title=160&cata=20](http://www.digisland.com/page2.php?title=160&cata=20)

See if there is a setup of the card via booting your system and hitting <TAB> when directed by the onscreen display. YOu may have to setup the drives before you can use them.

coffee

---

