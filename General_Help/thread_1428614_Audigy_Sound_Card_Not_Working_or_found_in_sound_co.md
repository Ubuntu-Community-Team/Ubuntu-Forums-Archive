---
title: "Audigy Sound Card Not Working or found in sound configuration"
date: 2010-03-13
forum: General Help
---

### Post by berlinbrown on 2010-03-13
I am having trouble getting my sound card to work.  I don't see any hardware information on the sound card when I try to select sound.

I did run the 9.10 software testing:

Here is some of my data from that report:

This report was created using checkbox-gtk 0.7.1 on 2010-03-13T01:03:44, on Ubuntu 9.10 (i386).

P: /devices/pci0000:00/0000:00:13.1/0000:05:09.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:13.1/0000:05:09.0
E: DRIVER=EMU10K1_Audigy
E: PCI_CLASS=40100
E: PCI_ID=1102:0004
E: PCI_SUBSYS_ID=1102:005B
E: PCI_SLOT_NAME=0000:05:09.0
E: MODALIAS=pci:v00001102d00000004sv00001102sd0000005Bbc04sc01i00
E: SUBSYSTEM=pci


P: /devices/pci0000:00/0000:00:13.1/0000:05:09.0/sound/card0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:13.1/0000:05:09.0/sound/card0
E: SUBSYSTEM=sound
E: SOUND_INITIALIZED=1
E: ID_VENDOR_FROM_DATABASE=Creative Labs
E: ID_MODEL_FROM_DATABASE=SB Audigy
E: ID_BUS=pci
E: ID_VENDOR_ID=0x1102
E: ID_MODEL_ID=0x0004
E: ID_PATH=pci-0000:05:09.0



05:09.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)
	Subsystem: Creative Labs Device [1102:005b]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at e400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

find /etc/modprobe.* -name \*.conf | xargs cat

---

