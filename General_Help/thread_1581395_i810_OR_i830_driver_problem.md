---
title: "i810 OR i830 driver problem"
date: 2010-09-24
forum: General Help
---

### Post by Detroit_Bad_Boy on 2010-09-24
I am running Ubuntu 10.4.1. I ran the lspci -vv command and this is what I got back. I am trying to change the visual effects mode but it seems that every time I try, it does not accept it. As it is, the text on my browser screen almost requires a magnifying glass to read it and I think that being unable to change the visual effects mode has something to do with it.
     I have been trying to find a suitable (not a generic ubuntu version) video and graphics driver that will work on an HP Pavilion XT963. This would need to be a ubuntu style driver.
     If anyne knows a driver that I can install to use the visual effects screen, it would be greatly appreciated

dave@dave-desktop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
	Subsystem: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Region 1: Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f4100000-f41fffff
	Prefetchable memory behind bridge: 10000000-100fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Intel Corporation 82801AA IDE Controller
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 1800 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
	Subsystem: Intel Corporation 82801AA USB Controller
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 19
	Region 4: I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
	Subsystem: Intel Corporation 82801AA SMBus Controller
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 9
	Region 4: I/O ports at 1810 [size=16]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 5643
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 1200 [size=256]
	Region 1: I/O ports at 1300 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:0b.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
	Subsystem: Accton Technology Corporation SMC2-1211TX
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 3000 [size=256]
	Region 1: Memory at f4100000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 10000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too

01:0e.0 Communication controller: Agere Systems LT WinModem (rev 02)
	Subsystem: Risq Modular Systems, Inc. Device 044e
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B+ DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at f4100400 (32-bit, non-prefetchable) [disabled] [size=256]
	Region 1: I/O ports at 3800 [disabled] [size=8]
	Region 2: I/O ports at 3400 [disabled] [size=256]
	Capabilities: <access denied>

dave@dave-desktop:

---

