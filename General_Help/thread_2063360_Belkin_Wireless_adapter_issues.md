---
title: "Belkin Wireless adapter issues"
date: 2012-09-26
forum: General Help
---

### Post by falonyn on 2012-09-26
I just recently installed Unbuntu 12.04 on my desktop. It easily recognized the Belkin USB Wireless N Adapter (F5D8053 v4), but every 5 to 10 minutes it will stop connecting to the internet. It continues to show that it is connected to the network, but nothing will download and pages will not load. Unplugging the adapter and plugging it back in will solve the problem for a short time, and then it will go down again. I was wondering if anyone else has had this problem and if there is a fix.

AMD Phenom X4
Redeon HD 6850 1GB
8Gb RAM

---

### Post by Rexilion on 2012-09-27
Can you plug it in and post the output of:

```
lspci -vvv
dmesg
lsmod
```

---

### Post by falonyn on 2012-09-27
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
joydev                 17693  0 
hid_microsoft          12888  0 
vesafb                 13844  1 
arc4                   12529  2 
usbhid                 47199  0 
hid                    99559  2 hid_microsoft,usbhid
rfcomm                 47604  0 
bnep                   18281  2 
snd_hda_codec_hdmi     32474  1 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_realtek   224173  1 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
cfg80211              205544  2 rt2x00lib,mac80211
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                97362  0 
k10temp                13166  0 
mac_hid                13253  0 
fglrx                3263886  178 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13791  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13301  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
pata_atiixp            13204  0 
usb_storage            49198  1

---

### Post by Rexilion on 2012-09-27
And where is the rest?

---

### Post by falonyn on 2012-09-28
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
	Subsystem: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 3: Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 41
	Region 0: I/O ports at c000 [size=8]
	Region 1: I/O ports at b000 [size=4]
	Region 2: I/O ports at a000 [size=8]
	Region 3: I/O ports at 9000 [size=4]
	Region 4: I/O ports at 8000 [size=16]
	Region 5: Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe7fe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe7ff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe7fd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe7ff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe7fc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe7f7000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe7ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts PRO [ATI Radeon HD 6800 Series] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Device 174b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at fe8e0000 (64-bit, non-prefetchable) [size=128K]
	Region 4: I/O ports at d000 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx_updates, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
	Subsystem: PC Partner Limited Device aa88
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 43
	Region 0: Memory at fe8bc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 42
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at fdff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169



[    0.569027] pci 0000:00:02.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.569029] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.569032] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[    0.569042] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.569050] pci 0000:00:15.1: PCI bridge to [bus 04-04]
[    0.569052] pci 0000:00:15.1:   bridge window [io  0xe000-0xefff]
[    0.569056] pci 0000:00:15.1:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.569059] pci 0000:00:15.1:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.569073] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.569076] pci 0000:00:02.0: setting latency timer to 64
[    0.569089] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.569092] pci 0000:00:15.0: setting latency timer to 64
[    0.569097] pci 0000:00:15.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.569100] pci 0000:00:15.1: setting latency timer to 64
[    0.569103] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.569104] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.569106] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.569107] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.569109] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.569111] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.569112] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.569114] pci_bus 0000:01: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.569116] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.569118] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.569119] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.569121] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.569122] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000dffff]
[    0.569124] pci_bus 0000:02: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.569126] pci_bus 0000:02: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.569128] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.569129] pci_bus 0000:04: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.569131] pci_bus 0000:04: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.569165] NET: Registered protocol family 2
[    0.569315] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.570210] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.572149] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.572385] TCP: Hash tables configured (established 524288 bind 65536)
[    0.572387] TCP reno registered
[    0.572395] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.572437] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.572580] NET: Registered protocol family 1
[    0.572602] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.420116] pci 0000:00:12.0: PCI INT A disabled
[    1.420166] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.420241] pci 0000:00:12.2: PCI INT B disabled
[    1.420258] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.500118] pci 0000:00:13.0: PCI INT A disabled
[    1.500146] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.500219] pci 0000:00:13.2: PCI INT B disabled
[    1.500254] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.580111] pci 0000:00:14.5: PCI INT C disabled
[    1.580144] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.660122] pci 0000:00:16.0: PCI INT A disabled
[    1.660149] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.660221] pci 0000:00:16.2: PCI INT B disabled
[    1.660256] pci 0000:01:00.0: Boot video device
[    1.660271] PCI: CLS 64 bytes, default 64
[    1.661655] PCI-DMA: Disabling AGP.
[    1.661736] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.661738] PCI-DMA: using GART IOMMU.
[    1.661740] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.665179] IBS: LVT offset 1 assigned
[    1.665195] perf: AMD IBS detected (0x0000001f)
[    1.665319] audit: initializing netlink socket (disabled)
[    1.665333] type=2000 audit(1348713891.660:1): initialized
[    1.681127] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.683126] VFS: Disk quotas dquot_6.5.2
[    1.683171] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.683606] fuse init (API version 7.17)
[    1.683676] msgmni has been set to 15961
[    1.684099] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.684132] io scheduler noop registered
[    1.684133] io scheduler deadline registered
[    1.684156] io scheduler cfq registered (default)
[    1.684261] pcieport 0000:00:02.0: setting latency timer to 64
[    1.684289] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.684499] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.684518] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.684615] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.684620] ACPI: Power Button [PWRB]
[    1.684649] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.684651] ACPI: Power Button [PWRF]
[    1.684698] ACPI: processor limited to max C-state 1
[    1.852825] ERST: Table is not found!
[    1.852827] GHES: HEST is not enabled!
[    1.852897] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.873299] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.944846] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.980453] Linux agpgart interface v0.103
[    1.981633] brd: module loaded
[    1.982215] loop: module loaded
[    1.982386] ahci 0000:00:11.0: version 3.0
[    1.982401] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.982460] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
[    1.982531] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.982534] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.983017] scsi0 : ahci
[    1.983105] scsi1 : ahci
[    1.983164] scsi2 : ahci
[    1.983217] scsi3 : ahci
[    1.983285] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 41
[    1.983288] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 41
[    1.983291] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 41
[    1.983293] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 41
[    1.983417] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.983437] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.983756] Fixed MDIO Bus: probed
[    1.983770] tun: Universal TUN/TAP device driver, 1.6
[    1.983771] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.983815] PPP generic driver version 2.4.2
[    1.983892] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.983938] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.983951] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.983992] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.983999] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.984039] QUIRK: Enable AMD PLL fix
[    1.984048] ehci_hcd 0000:00:12.2: debug port 1
[    1.984065] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff800
[    1.996096] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.996326] hub 1-0:1.0: USB hub found
[    1.996329] hub 1-0:1.0: 5 ports detected
[    1.996447] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.996459] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.996499] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.996505] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.996522] ehci_hcd 0000:00:13.2: debug port 1
[    1.996533] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe7ff400
[    2.008091] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.008304] hub 2-0:1.0: USB hub found
[    2.008307] hub 2-0:1.0: 5 ports detected
[    2.008423] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.008437] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    2.008475] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    2.008481] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.008498] ehci_hcd 0000:00:16.2: debug port 1
[    2.008509] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe7ff000
[    2.020086] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.020222] hub 3-0:1.0: USB hub found
[    2.020225] hub 3-0:1.0: 4 ports detected
[    2.020352] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.020439] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.020452] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.020494] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.020514] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe7fe000
[    2.080181] hub 4-0:1.0: USB hub found
[    2.080186] hub 4-0:1.0: 5 ports detected
[    2.080359] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.080371] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.080408] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.080420] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fd000
[    2.140174] hub 5-0:1.0: USB hub found
[    2.140179] hub 5-0:1.0: 5 ports detected
[    2.140354] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.140367] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.140403] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.140417] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe7fc000
[    2.200186] hub 6-0:1.0: USB hub found
[    2.200191] hub 6-0:1.0: 2 ports detected
[    2.200363] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.200376] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.200413] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.200425] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe7f7000
[    2.260189] hub 7-0:1.0: USB hub found
[    2.260194] hub 7-0:1.0: 4 ports detected
[    2.260307] uhci_hcd: USB Universal Host Controller Interface driver
[    2.260390] usbcore: registered new interface driver libusual
[    2.260416] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.260753] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.260757] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.260926] mousedev: PS/2 mouse device common for all mice
[    2.261041] rtc_cmos 00:02: RTC can wake from S4
[    2.261120] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.261141] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.261199] device-mapper: uevent: version 1.0.3
[    2.261248] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    2.261254] cpuidle: using governor ladder
[    2.261256] cpuidle: using governor menu
[    2.261257] EFI Variables Facility v0.08 2004-May-17
[    2.261417] TCP cubic registered
[    2.261478] NET: Registered protocol family 10
[    2.261819] NET: Registered protocol family 17
[    2.261822] Registering the dns_resolver key type
[    2.261938] PM: Hibernation image not present or could not be loaded.
[    2.261946] registered taskstats version 1
[    2.267710]   Magic number: 12:939:713
[    2.267792] rtc_cmos 00:02: setting system clock to 2012-09-27 02:44:53 UTC (1348713893)
[    2.267807] powernow-k8: Found 1 AMD Phenom(tm) II X4 960T Processor (4 cpu cores) (version 2.20.00)
[    2.267820] powernow-k8: Core Performance Boosting: on.
[    2.267853] powernow-k8:    0 : pstate 0 (3000 MHz)
[    2.267855] powernow-k8:    1 : pstate 1 (2300 MHz)
[    2.267856] powernow-k8:    2 : pstate 2 (1600 MHz)
[    2.267857] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.268121] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.268123] EDD information not available.
[    2.300147] ata4: SATA link down (SStatus 0 SControl 300)
[    2.304146] ata3: SATA link down (SStatus 0 SControl 300)
[    2.308135] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.443043] Initializing USB Mass Storage driver...
[    2.443170] scsi4 : usb-storage 1-1:1.0
[    2.443212] usbcore: registered new interface driver usb-storage
[    2.443213] USB Mass Storage support registered.
[    2.472116] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.472159] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.475660] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22NS90, HN00S300, max UDMA/100
[    2.477025] ata2.00: configured for UDMA/100
[    2.483845] ata1.00: ATA-8: Corsair Force 3 SSD, 1.3.3, max UDMA/133
[    2.483848] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.493806] ata1.00: configured for UDMA/133
[    2.494037] scsi 0:0:0:0: Direct-Access     ATA      Corsair Force 3  1.3. PQ: 0 ANSI: 5
[    2.494158] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.494174] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.494296] sd 0:0:0:0: [sda] Write Protect is off
[    2.494298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.494334] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.494883]  sda: sda1 sda2 < sda5 >
[    2.495251] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.499200] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS90  HN00 PQ: 0 ANSI: 5
[    2.502006] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.502015] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.502196] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.502331] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.503512] Freeing unused kernel memory: 920k freed
[    2.503702] Write protecting the kernel read-only data: 12288k
[    2.507583] Freeing unused kernel memory: 1616k freed
[    2.510787] Freeing unused kernel memory: 1200k freed
[    2.524906] udevd[144]: starting version 175
[    2.553142] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.553161] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.553189] r8169 0000:04:00.0: setting latency timer to 64
[    2.553244] r8169 0000:04:00.0: irq 42 for MSI/MSI-X
[    2.553552] r8169 0000:04:00.0: eth0: RTL8168d/8111d at 0xffffc90000c18000, 8c:89:a5:32:df:be, XID 081000c0 IRQ 42
[    2.553555] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.554009] scsi5 : pata_atiixp
[    2.556196] scsi6 : pata_atiixp
[    2.556320] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.556323] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.578076] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.664112] Refined TSC clocksource calibration: 2999.945 MHz.
[    2.664125] Switching to clocksource tsc
[    2.672099] usb 3-2: new high-speed USB device number 2 using ehci_hcd
[    2.932092] usb 3-3: new high-speed USB device number 3 using ehci_hcd
[    3.128396] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.134024] udevd[383]: starting version 175
[    3.136697] Adding 8386556k swap on /dev/sda5.  Priority:-1 extents:1 across:8386556k SS
[    3.155464] lp: driver loaded but no devices found
[    3.171666] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.221144] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    3.229813] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    3.229879] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[    3.234314] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    3.234317] Disabling lock debugging due to kernel taint
[    3.235705] MCE: In-kernel MCE decoding enabled.
[    3.237192] EDAC MC: Ver: 2.1.0
[    3.253831] AMD64 EDAC driver v3.4.0
[    3.256386] [fglrx] Maximum main memory to use for locked dma buffers: 7751 MBytes.
[    3.256483] [fglrx]   vendor: 1002 device: 6739 count: 1
[    3.256927] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[    3.256941] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.256946] pci 0000:01:00.0: setting latency timer to 64
[    3.257103] EDAC amd64: DRAM ECC disabled.
[    3.257110] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    3.257111]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    3.257112]  (Note that use of the override may cause unknown side effects.)
[    3.257264] [fglrx] Kernel PAT support is enabled
[    3.257279] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[    3.282178] cfg80211: Calling CRDA to update world regulatory domain
[    3.297085] type=1400 audit(1348713894.525:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=720 comm="apparmor_parser"
[    3.297475] type=1400 audit(1348713894.525:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=720 comm="apparmor_parser"
[    3.297679] type=1400 audit(1348713894.525:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=720 comm="apparmor_parser"
[    3.298063] type=1400 audit(1348713894.525:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=695 comm="apparmor_parser"
[    3.298447] type=1400 audit(1348713894.525:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[    3.298650] type=1400 audit(1348713894.525:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[    3.303116] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.332085] usb 4-2: new low-speed USB device number 2 using ohci_hcd
[    3.345559] init: failsafe main process (748) killed by TERM signal
[    3.351106] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input2
[    3.351162] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input3
[    3.351203] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[    3.351242] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    3.351298] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    3.351338] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    3.351376] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    3.351415] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    3.351939] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.352117] snd_hda_intel 0000:01:00.1: irq 43 for MSI/MSI-X
[    3.352140] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[    3.352990] ppdev: user-space parallel port driver
[    3.377378] Bluetooth: Core ver 2.16
[    3.377399] NET: Registered protocol family 31
[    3.377401] Bluetooth: HCI device and connection manager initialized
[    3.377404] Bluetooth: HCI socket layer initialized
[    3.377405] Bluetooth: L2CAP socket layer initialized
[    3.377409] Bluetooth: SCO socket layer initialized
[    3.378395] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[    3.378463] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input10
[    3.378584] cfg80211: World regulatory domain updated:
[    3.378587] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.378589] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.378591] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.378593] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.378594] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.378596] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.390741] type=1400 audit(1348713894.617:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=849 comm="apparmor_parser"
[    3.391190] type=1400 audit(1348713894.617:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=849 comm="apparmor_parser"
[    3.392850] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.392852] Bluetooth: BNEP filters: protocol multicast
[    3.399724] Bluetooth: RFCOMM TTY layer initialized
[    3.399728] Bluetooth: RFCOMM socket layer initialized
[    3.399729] Bluetooth: RFCOMM ver 1.11
[    3.421059] type=1400 audit(1348713894.649:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=923 comm="apparmor_parser"
[    3.440661] scsi 4:0:0:0: Direct-Access     WDC      WD5000AAVS-00ZTB 3.00 PQ: 0 ANSI: 4
[    3.441348] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.444059] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.444777] sd 4:0:0:0: [sdb] Write Protect is off
[    3.444780] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    3.445413] sd 4:0:0:0: [sdb] No Caching mode page present
[    3.445416] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.447290] sd 4:0:0:0: [sdb] No Caching mode page present
[    3.447292] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.453671]  sdb: sdb1
[    3.456279] sd 4:0:0:0: [sdb] No Caching mode page present
[    3.456283] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.456285] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.518313] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input11
[    3.518415] generic-usb 0003:046D:C01E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-2/input0
[    3.518446] usbcore: registered new interface driver usbhid
[    3.518447] usbhid: USB HID core driver
[    3.581018] r8169 0000:04:00.0: eth0: link down
[    3.581793] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.582082] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.600035] usb 3-2: reset high-speed USB device number 2 using ehci_hcd
[    3.771111] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.771114] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771116] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.771118] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771120] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.771122] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771123] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.771125] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771126] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.771128] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771130] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.771131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771133] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.771135] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771136] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.771138] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771139] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.771141] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771143] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.771145] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771146] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.771148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.771149] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.771151] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.771153] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.771154] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.771156] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.771158] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.773764] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    3.774198] Registered led device: rt2800usb-phy0::radio
[    3.774211] Registered led device: rt2800usb-phy0::assoc
[    3.774224] Registered led device: rt2800usb-phy0::quality
[    3.774251] usbcore: registered new interface driver rt2800usb
[    3.865241] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    3.865244] vesafb: scrolling: redraw
[    3.865246] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.869667] usb 4-5: new low-speed USB device number 3 using ohci_hcd
[    3.870391] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011c00000, using 5824k, total 5824k
[    3.870577] Console: switching to colour frame buffer device 175x65
[    3.870601] fb0: VESA VGA frame buffer device
[    3.884160] init: plymouth-splash main process (1234) terminated with status 1
[    3.980853] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.981123] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.081327] input: Microsoft Natural\xffffffc2\xffffffae\xffffffae Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input12
[    4.081466] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural\xffffffc2\xffffffae\xffffffae Ergonomic Keyboard 4000] on usb-0000:00:12.0-5/input0
[    4.097261] input: Microsoft Natural\xffffffc2\xffffffae\xffffffae Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.1/input/input13
[    4.097350] microsoft 0003:045E:00DB.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Natural\xffffffc2\xffffffae\xffffffae Ergonomic Keyboard 4000] on usb-0000:00:12.0-5/input1
[    4.219350] fglrx_pci 0000:01:00.0: irq 44 for MSI/MSI-X
[    4.219931] [fglrx] Firegl kernel thread PID: 1262
[    4.220000] [fglrx] Firegl kernel thread PID: 1263
[    4.220093] [fglrx] Firegl kernel thread PID: 1264
[    4.220200] [fglrx] IRQ 44 Enabled
[    4.420185] [fglrx] Gart USWC size:1280 M.
[    4.420188] [fglrx] Gart cacheable size:508 M.
[    4.420191] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[    4.420193] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[    4.420195] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[    7.280341] wlan0: authenticate with 00:22:75:52:80:ce (try 1)
[    7.282056] wlan0: authenticated
[    7.336333] wlan0: associate with 00:22:75:52:80:ce (try 1)
[    7.339797] wlan0: RX AssocResp from 00:22:75:52:80:ce (capab=0x411 status=0 aid=3)
[    7.339806] wlan0: associated
[    7.367990] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[32380.512204] usb 3-3: USB disconnect, device number 3

---

### Post by Rexilion on 2012-09-28
Okay, wireless USB that uses rt2800 usb driver. Seems to work properly:

> [ 7.280341] wlan0: authenticate with 00:22:75:52:80:ce (try 1)
[ 7.282056] wlan0: authenticated
[ 7.336333] wlan0: associate with 00:22:75:52:80:ce (try 1)
[ 7.339797] wlan0: RX AssocResp from 00:22:75:52:80:ce (capab=0x411 status=0 aid=3)
[ 7.339806] wlan0: associated

Could you:

- unplug USB
- execute: 'sudo dmesg -c'
- plugin USB
- make sure internet works
- use it till it drops
- execute: 'sudo dmesg >& dmesg.log'

Post the contents (or the file itself) of dmesg.log here.

---

### Post by falonyn on 2012-09-28
Where does the log appear? When I ran the second command, it asked for the password and then does not give me a log.

---

### Post by Rexilion on 2012-09-29
> **falonyn said:**
> Where does the log appear? When I ran the second command, it asked for the password and then does not give me a log.

>& dmesg.log means: output to dmesg.log.

You should see a dmesg.log file in the directory you ran the command.

---

### Post by falonyn on 2012-09-30
[126591.724115] usb 3-2: new high-speed USB device number 6 using ehci_hcd
[126591.988074] usb 3-2: reset high-speed USB device number 6 using ehci_hcd
[126592.159255] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[126592.159266] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159273] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[126592.159280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159286] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[126592.159293] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159299] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[126592.159306] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159311] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[126592.159318] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159323] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[126592.159330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159335] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[126592.159342] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159348] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[126592.159354] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159360] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[126592.159366] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159372] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[126592.159379] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159384] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[126592.159391] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126592.159396] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[126592.159403] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126592.159409] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[126592.159415] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126592.159421] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[126592.159428] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126592.159660] ieee80211 phy3: Selected rate control algorithm 'minstrel_ht'
[126592.161010] Registered led device: rt2800usb-phy3::radio
[126592.161061] Registered led device: rt2800usb-phy3::assoc
[126592.161112] Registered led device: rt2800usb-phy3::quality
[126592.378653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126592.381905] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126595.696801] wlan0: authenticate with 00:22:75:52:80:ce (try 1)
[126595.703605] wlan0: authenticated
[126595.748671] wlan0: associate with 00:22:75:52:80:ce (try 1)
[126595.752226] wlan0: RX AssocResp from 00:22:75:52:80:ce (capab=0x411 status=0 aid=3)
[126595.752236] wlan0: associated
[126595.782020] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[126709.336810] usb 3-2: USB disconnect, device number 6
[126709.337817] wlan0: deauthenticating from 00:22:75:52:80:ce by local choice (reason=3)
[126709.436360] cfg80211: All devices are disconnected, going to restore regulatory settings
[126709.436373] cfg80211: Restoring regulatory settings
[126709.436383] cfg80211: Calling CRDA to update world regulatory domain
[126709.489233] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[126709.489244] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489251] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[126709.489258] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489264] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[126709.489271] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489277] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[126709.489283] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489289] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[126709.489296] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489301] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[126709.489308] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489313] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[126709.489320] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489325] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[126709.489332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489338] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[126709.489344] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489350] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[126709.489357] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489362] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[126709.489369] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489375] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[126709.489381] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126709.489387] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[126709.489394] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126709.489399] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[126709.489406] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126709.489414] cfg80211: World regulatory domain updated:
[126709.489418] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[126709.489424] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489431] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126709.489437] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126709.489443] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126709.489449] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.320087] usb 3-2: new high-speed USB device number 7 using ehci_hcd
[126711.584107] usb 3-2: reset high-speed USB device number 7 using ehci_hcd
[126711.755170] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[126711.755181] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755188] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[126711.755196] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755202] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[126711.755209] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755214] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[126711.755221] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755227] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[126711.755233] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755239] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[126711.755246] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755251] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[126711.755258] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755263] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[126711.755270] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755276] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[126711.755282] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755288] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[126711.755294] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755300] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[126711.755307] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[126711.755312] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[126711.755319] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126711.755325] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[126711.755331] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126711.755337] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[126711.755344] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[126711.755566] ieee80211 phy4: Selected rate control algorithm 'minstrel_ht'
[126711.756924] Registered led device: rt2800usb-phy4::radio
[126711.756975] Registered led device: rt2800usb-phy4::assoc
[126711.757023] Registered led device: rt2800usb-phy4::quality
[126711.971047] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126711.974343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126715.284535] wlan0: authenticate with 00:22:75:52:80:ce (try 1)
[126715.289918] wlan0: authenticated
[126715.332388] wlan0: associate with 00:22:75:52:80:ce (try 1)
[126715.335815] wlan0: RX AssocResp from 00:22:75:52:80:ce (capab=0x411 status=0 aid=3)
[126715.335824] wlan0: associated
[126715.366372] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by Rexilion on 2012-10-01
Did you disconnect the device after the internet connection drops? (just to make sure)

---

### Post by falonyn on 2012-10-01
I did, but I can run it again just to be sure when I get home from work this evening.

---

### Post by falonyn on 2012-10-01
I believe I did, yes.

---

### Post by Rexilion on 2012-10-02
Thank you for confirming.

It seems that the device suddenly disconnect's itself from the USB bus (not the network):

>  [126595.782020] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[126709.336810] usb 3-2: USB disconnect, device number 6
[126709.337817] wlan0: deauthenticating from 00:22:75:52:80:ce by local choice (reason=3)
[126709.436360] cfg80211: All devices are disconnected, going to restore regulatory settings

Deauthentication by local choice huh?

Could you do the following:

> - Unplug device
- sudo stop networkmanager
- sudo NetworkManager --no-daemon >& ~/nm_log.txt
- Plug in USB
- Connect to internet
- Wait for connection to drop
- In the terminal where you ran NetworkManager press 'CTRL+C'
- sudo start networkmanager
- Please provide the output of: ~/nm_log.txt

Good luck!

---

### Post by falonyn on 2012-10-02
NetworkManager is already running (pid 838)

That is all that came up, although any time that I typed in "sudo stop/start network manager", I got "stop/start: Unknown job: networkmanager"

I am unsure as to why. 

And it looks like you have found what the issue is, but for some reason it never stops showing me connected to the wireless network. I just lose internet connectivity. 

Thank you!

---

### Post by Rexilion on 2012-10-02
Ah, that is because:

> sudo stop networkmanager

should be

> sudo stop network-manager

Sorry for that, Gentoo habit :rolleyes:.

---

### Post by falonyn on 2012-10-02
NetworkManager[8312]: <info> NetworkManager (version 0.9.4.0) is starting...
NetworkManager[8312]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
NetworkManager[8312]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
NetworkManager[8312]: <info> DNS: loaded plugin dnsmasq
NetworkManager[8312]:    SCPlugin-Ifupdown: init!
NetworkManager[8312]:    SCPlugin-Ifupdown: update_system_hostname
NetworkManager[8312]:    SCPluginIfupdown: management mode: unmanaged
NetworkManager[8312]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0/net/eth0, iface: eth0)
NetworkManager[8312]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
NetworkManager[8312]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
NetworkManager[8312]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
NetworkManager[8312]:    SCPlugin-Ifupdown: end _init.
NetworkManager[8312]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
NetworkManager[8312]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
NetworkManager[8312]:    Ifupdown: get unmanaged devices count: 0
NetworkManager[8312]:    SCPlugin-Ifupdown: (30612272) ... get_connections.
NetworkManager[8312]:    SCPlugin-Ifupdown: (30612272) ... get_connections (managed=false): return empty list.
NetworkManager[8312]:    keyfile: parsing Virus ... 
NetworkManager[8312]:    keyfile:     read connection 'Virus'
NetworkManager[8312]:    Ifupdown: get unmanaged devices count: 0
NetworkManager[8312]: <info> trying to start the modem manager...
NetworkManager[8312]: <info> monitoring kernel firmware directory '/lib/firmware'.
NetworkManager[8312]: <info> WiFi enabled by radio killswitch; enabled by state file
NetworkManager[8312]: <info> WWAN enabled by radio killswitch; enabled by state file
NetworkManager[8312]: <info> WiMAX enabled by radio killswitch; enabled by state file
NetworkManager[8312]: <info> Networking is enabled by state file
NetworkManager[8312]: <warn> failed to allocate link cache: (-10) Operation not supported
NetworkManager[8312]: <info> (eth0): carrier is OFF
NetworkManager[8312]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
NetworkManager[8312]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
NetworkManager[8312]: <info> (eth0): now managed
NetworkManager[8312]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
NetworkManager[8312]: <info> (eth0): bringing up device.
NetworkManager[8312]: <info> (eth0): preparing device.
NetworkManager[8312]: <info> (eth0): deactivating device (reason 'managed') [2]
NetworkManager[8312]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0/net/eth0
/sbin/ifup: interface lo already configured
NetworkManager[8312]: <info> modem-manager is now available
NetworkManager[8312]: <info> found WiFi radio killswitch rfkill11 (at /sys/devices/pci0000:00/0000:00:16.2/usb3/3-2/3-2:1.0/ieee80211/phy11/rfkill11) (driver (unknown))
NetworkManager[8312]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.2/usb3/3-2/3-2:1.0/net/wlan0, iface: wlan0)
NetworkManager[8312]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.2/usb3/3-2/3-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
NetworkManager[8312]: <info> (wlan0): using nl80211 for WiFi device control
NetworkManager[8312]: <warn> (wlan0): driver supports Access Point (AP) mode
NetworkManager[8312]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 16)
NetworkManager[8312]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
NetworkManager[8312]: <info> (wlan0): now managed
NetworkManager[8312]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
NetworkManager[8312]: <info> (wlan0): bringing up device.
NetworkManager[8312]: <info> (wlan0): preparing device.
NetworkManager[8312]: <info> (wlan0): deactivating device (reason 'managed') [2]
NetworkManager[8312]: <info> (wlan0): supplicant interface state: starting -> ready
NetworkManager[8312]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
NetworkManager[8312]: <info> (wlan0): supplicant interface state: ready -> inactive
NetworkManager[8312]: <warn> Trying to remove a non-existant call id.
NetworkManager[8312]: <info> Auto-activating connection 'Virus'.
NetworkManager[8312]: <info> Activation (wlan0) starting connection 'Virus'
NetworkManager[8312]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
NetworkManager[8312]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager[8312]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager[8312]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager[8312]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager[8312]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager[8312]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
NetworkManager[8312]: <info> Activation (wlan0/wireless): connection 'Virus' has security, and secrets exist.  No new secrets needed.
NetworkManager[8312]: <info> Config: added 'ssid' value 'Virus'
NetworkManager[8312]: <info> Config: added 'scan_ssid' value '1'
NetworkManager[8312]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
NetworkManager[8312]: <info> Config: added 'auth_alg' value 'OPEN'
NetworkManager[8312]: <info> Config: added 'psk' value '<omitted>'
NetworkManager[8312]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager[8312]: <info> Config: set interface ap_scan to 1
NetworkManager[8312]: <info> (wlan0): supplicant interface state: inactive -> scanning
NetworkManager[8312]: <info> (wlan0): supplicant interface state: scanning -> authenticating
NetworkManager[8312]: <info> (wlan0): supplicant interface state: authenticating -> associating
NetworkManager[8312]: <info> (wlan0): supplicant interface state: associating -> associated
NetworkManager[8312]: <info> (wlan0): supplicant interface state: associated -> completed
NetworkManager[8312]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Virus'.
NetworkManager[8312]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager[8312]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager[8312]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
NetworkManager[8312]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
NetworkManager[8312]: <info> dhclient started with pid 8335
NetworkManager[8312]: <info> Activation (wlan0) Beginning IP6 addrconf.
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

NetworkManager[8312]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager[8312]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Listening on LPF/wlan0/00:1c:df:68:f2:87
Sending on   LPF/wlan0/00:1c:df:68:f2:87
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.10 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.10 from 192.168.2.1
bound to 192.168.2.10 -- renewal in 2147483648 seconds.
NetworkManager[8312]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
NetworkManager[8312]: <info>   address 192.168.2.10
NetworkManager[8312]: <info>   prefix 24 (255.255.255.0)
NetworkManager[8312]: <info>   gateway 192.168.2.1
NetworkManager[8312]: <info>   nameserver '192.168.2.1'
NetworkManager[8312]: <info>   domain name 'Belkin'
NetworkManager[8312]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
NetworkManager[8312]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
NetworkManager[8312]: <info> DNS: starting dnsmasq...
NetworkManager[8312]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
NetworkManager[8312]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
NetworkManager[8312]: <info> Policy set 'Virus' (wlan0) as default for IPv4 routing and DNS.
NetworkManager[8312]: <info> Activation (wlan0) successful, device activated.
NetworkManager[8312]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
NetworkManager[8312]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
NetworkManager[8312]: <info> Activation (wlan0) Beginning DHCPv6 transaction (timeout in 45 seconds)
NetworkManager[8312]: <info> dhclient started with pid 8413
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Bound to *:546
Listening on Socket/wlan0
Sending on   Socket/wlan0
PRC: Soliciting for leases (INIT).
NetworkManager[8312]: <info> (wlan0): DHCPv6 state changed nbi -> preinit6
XMT: Forming Solicit, 0 ms elapsed.
XMT:  X-- IA_NA df:68:f2:87
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on wlan0, interval 1010ms.
NetworkManager[8312]: <info> DNS: starting dnsmasq...
NetworkManager[8312]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
NetworkManager[8312]: <info> Policy set 'Virus' (wlan0) as default for IPv4 routing and DNS.
NetworkManager[8312]: <info> Policy set 'Virus' (wlan0) as default for IPv6 routing and DNS.
XMT: Forming Solicit, 1010 ms elapsed.
XMT:  X-- IA_NA df:68:f2:87
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on wlan0, interval 2050ms.
XMT: Forming Solicit, 3060 ms elapsed.
XMT:  X-- IA_NA df:68:f2:87
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on wlan0, interval 4150ms.
XMT: Forming Solicit, 7210 ms elapsed.
XMT:  X-- IA_NA df:68:f2:87
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on wlan0, interval 8490ms.
XMT: Forming Solicit, 15710 ms elapsed.
XMT:  X-- IA_NA df:68:f2:87
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on wlan0, interval 17440ms.
XMT: Forming Solicit, 33170 ms elapsed.
XMT:  X-- IA_NA df:68:f2:87
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on wlan0, interval 33690ms.
NetworkManager[8312]: <warn> (wlan0): DHCPv6 request timed out.
NetworkManager[8312]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 8413
NetworkManager[8312]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
NetworkManager[8312]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
NetworkManager[8312]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
NetworkManager[8312]: <warn> error monitoring device for netlink events: No buffer space available
NetworkManager[8312]: <warn> error monitoring device for netlink events: No buffer space available
NetworkManager[8312]: <warn> error monitoring device for netlink events: No buffer space available
NetworkManager[8312]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
NetworkManager[8312]: <info> caught signal 2, shutting down normally.
NetworkManager[8312]: <warn> quit request received, terminating...
NetworkManager[8312]: <info> (eth0): now unmanaged
NetworkManager[8312]: <info> caught signal 2, shutting down normally.
NetworkManager[8312]: <info> (eth0): taking down device.
NetworkManager[8312]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
NetworkManager[8312]: <info> (wlan0): now unmanaged
NetworkManager[8312]: <info> (wlan0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
NetworkManager[8312]: <info> (wlan0): deactivating device (reason 'removed') [36]
NetworkManager[8312]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 8335
NetworkManager[8312]: <info> DNS: starting dnsmasq...
NetworkManager[8312]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
NetworkManager[8312]: <info> DNS: starting dnsmasq...
NetworkManager[8312]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
NetworkManager[8312]: <info> (wlan0): cleaning up...
NetworkManager[8312]: <info> (wlan0): taking down device.
NetworkManager[8312]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
NetworkManager[8312]: <info> (wlan0): removing resolv.conf from /sbin/resolvconf
NetworkManager[8312]: <info> exiting (success)

---

### Post by Rexilion on 2012-10-02
Did you encounter/apply/try the procedures/bug encountered [here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889")?

Of not, please provide the output of:

> cat /etc/network/interfaces

Do you have more wireless devices attached to this box?

If yes, seems like the 'fix' is a dirty workaround for devices not supporting everything NetworkManager requires (I think). But this option is only worth investigating if that is the issue.

---

### Post by falonyn on 2012-10-02
That did not sound at all like what I am running into. I never get anything about the "offline mode". Even when it is not working, it still says that it is connected to the network. 

That is the only wireless device I have connected too. The only other thing I have hooked up through USB has been an external HD which works perfectly.

---

### Post by Rexilion on 2012-10-03
Good, then please provide the output of:

```
sudo cat /etc/network/interfaces
```

---

### Post by falonyn on 2012-10-03
auto lo
iface lo inet loopback

---

### Post by Rexilion on 2012-10-03
No issue's there. Then the only thing (as a last resort) is to upgrade your kernel or update your firmware...

---

### Post by falonyn on 2012-10-03
And would you be able to reply with the best way to update the firmware for the adapter?

---

### Post by Rexilion on 2012-10-04
I think you already have the latest version, but since I can't check for sure I want to ask you to provide the output of:

```
md5sum /lib/firmware/rt*
```

Btw, upgrading firmware is nothing more than moving files and rebooting. We can easily restore to the original state.

---

### Post by falonyn on 2012-10-04
99bce75086ea635a2f8288d9b835f787  /lib/firmware/rt2561.bin
2878d5eaa4ff907d4df36a834915aa53  /lib/firmware/rt2561s.bin
9998485bc152cf0f39dd61a33b92ad9b  /lib/firmware/rt2661.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin
36c944c3138125605d28c0a3a1338be9  /lib/firmware/rt2870.bin
36c944c3138125605d28c0a3a1338be9  /lib/firmware/rt3070.bin
9a10bd0220c3e36ad966b6eab929b2f1  /lib/firmware/rt3071.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt3090.bin
bd733372ae21a010bf8a5511d7711c2d  /lib/firmware/rt73.bin
md5sum: /lib/firmware/rtl_nic: Is a directory
md5sum: /lib/firmware/rtlwifi: Is a directory

---

### Post by Rexilion on 2012-10-04
Too bad, that's the same version the linux-firmware repository has :/. I guess your only and last resort is to upgrade your kernel and give a bleeding edge kernel a shot. I do not know of any PPA that has 3.6 for precise.

As a normal user:

```
sudo aptitude -R install gcc make bzip2
wget http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.6.tar.bz2
tar -xjf linux-3.6.tar.bz2
cd linux-3.6
# cp the attachment [1] of this post inside this directory and rename it as '.config'
make
sudo make install
sudo make modules_install
```

Above procedure installs a new kernel alongside the kernel provided by Ubuntu, reverting to the older versions should be no problem. Make sure you know how to access the Grub bootloader menu in order to select new / old kernels. This new kernel can also easily be removed.

Reboot and select the new kernel in your grub menu. When you boot, confirm you are running the new kernel by opening a terminal and typing:

```
uname -r
```

This should mention something which starts with 3.6. Then test your wireless. There are 4 releases between 3.2 and 3.6 (which means a lot has changed), I think you have a good chance of getting your USB working.

[1] [http://pastebin.com/download.php?i=fvFcy6Hj](http://pastebin.com/download.php?i=fvFcy6Hj)

---

### Post by falonyn on 2012-10-04
nicholas@nicholas-MS-7599:~$ sudo aptitude -R install gcc make bzip2
sudo: aptitude: command not found

---

### Post by Rexilion on 2012-10-05
Eh? Is aptitude not installed by default anymore?

try:

```
sudo apt-get install gcc make bzip2
```

Instead.

---

### Post by falonyn on 2012-10-06
nicholas@nicholas-MS-7599:~/linux-3.6$ make
scripts/kconfig/conf --silentoldconfig Kconfig
***
*** Configuration file ".config" not found!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make[1]: Nothing to be done for `all'.
make[1]: Nothing to be done for `relocs'.
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
nicholas@nicholas-MS-7599:~/linux-3.6$ sudo make install
scripts/kconfig/conf --silentoldconfig Kconfig
***
*** Configuration file ".config" not found!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
sh /home/nicholas/linux-3.6/arch/x86/boot/install.sh  arch/x86/boot/bzImage \
		System.map "/boot"

 *** Missing file: System.map
 *** You need to run "make" before "make install".

make[1]: *** [install] Error 1
make: *** [install] Error 2

---

### Post by Rexilion on 2012-10-07
> **Rexilion said:**
> ```
# cp the attachment [1] of this post inside this directory and rename it as '.config'
```

[1] [http://pastebin.com/download.php?i=fvFcy6Hj](http://pastebin.com/download.php?i=fvFcy6Hj)

Did you to the above, as I mentioned?

---

### Post by falonyn on 2012-10-08
I suppose it would help if I knew better how to go about doing that. Command line is something that I have never been good with. I apologize.

---

### Post by Rexilion on 2012-10-09
Okay, no problem. You don't have to use the commandline for this specific step. Just click on [this link]("http://pastebin.com/download.php?i=fvFcy6Hj"). This will download a file called 'fvFcy6Hj'.

Open your file explorer, and drag this file into the folder linux-3.6 you generated earlier. Go into linux-3.6. Then rename 'fvFcy6Hj' to '.config'. And then continue with the next step in the terminal.

Mind you that the new filename is '***_._***config' and not 'config'.

---

