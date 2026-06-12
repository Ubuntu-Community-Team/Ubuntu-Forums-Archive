---
title: "USB on SiS motherboard doesn't work."
date: 2010-05-28
forum: General Help
---

### Post by dragos240 on 2010-05-28
I have a SiS motherboard on a new laptop (well, new to me). And linux is not recognizing any USB devices.

Dmesg isn't picking up any input. Help?

---

### Post by dragos240 on 2010-05-30
Bump

---

### Post by colorlessprism on 2010-05-30
i have run into a USB issue like this before before (9.10) when my webcam was on nothing USB would work. try disabling your webcam (use the hardware keys should be FN+<some key>) and restarting your computer. if this fixes your problem you may need to look into a BIOS update

edit:
im not sure if this applies to laptops but it might be worth a shot. occasionally one of my desktops has problems with the USB ports. i have to shutdown the computer and unplug the powercord for aprox 30 secs. then everything works again. you could unplug the power cord and remove the battery for a while then turn the laptop back on.

---

### Post by dragos240 on 2010-05-30
> **colorlessprism said:**
> i have run into a USB issue like this before before (9.10) when my webcam was on nothing USB would work. try disabling your webcam (use the hardware keys should be FN+<some key>) and restarting your computer. if this fixes your problem you may need to look into a BIOS update

edit:
im not sure if this applies to laptops but it might be worth a shot. occasionally one of my desktops has problems with the USB ports. i have to shutdown the computer and unplug the powercord for aprox 30 secs. then everything works again. you could unplug the power cord and remove the battery for a while then turn the laptop back on.

This computer is about 4-5 years old, so no webcam.

---

### Post by ibuclaw on 2010-05-30
Well, I guess the basics will be a start:

```

uname -a
cat /proc/version_signature
sudo lspci -vvnn
dmesg
lsusb

```

Regards

---

### Post by dragos240 on 2010-05-30
> **ibuclaw said:**
> Well, I guess the basics will be a start:

```

uname -a
cat /proc/version_signature
sudo lspci -vvnn
dmesg
lsusb

```Regards

Thanks. I'll post these as soon as I get home...... tomorrow..... maybe......

---

### Post by dragos240 on 2010-06-01
> **ibuclaw said:**
> Well, I guess the basics will be a start:

```

uname -a
cat /proc/version_signature
sudo lspci -vvnn
dmesg
lsusb

```Regards
Linux amundsen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2

```

00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 741/741GX/M741 Host [1039:0741] (rev 03)
    Subsystem: Silicon Integrated Systems [SiS] 741/741GX/M741 Host [1039:0741]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64
    Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=32M]
    Capabilities: [c0] AGP version 3.5
        Status: RQ=32 Iso- ArqSz=2 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000dfff
    Memory behind bridge: e0000000-efffffff
    Prefetchable memory behind bridge: a0000000-afffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 0
    Region 4: I/O ports at 1400 [disabled] [size=32]
    Kernel driver in use: sis96x_smbus
    Kernel modules: i2c-sis96x

00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (prog-if 80 [Master])
    Subsystem: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 128
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    Region 4: I/O ports at 1100 [size=16]
    Kernel driver in use: pata_sis

00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:8170]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 11
    Region 0: I/O ports at e000 [size=256]
    Region 1: I/O ports at e100 [size=128]
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel modules: snd-intel8x0m

00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:8140]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (13000ns min, 2750ns max)
    Interrupt: pin C routed to IRQ 11
    Region 0: I/O ports at e200 [size=256]
    Region 1: I/O ports at e300 [size=128]
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10)
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at 28020000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10)
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 11
    Region 0: Memory at 28021000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] (prog-if 20)
    Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin D routed to IRQ 11
    Region 0: Memory at 28022000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
    Subsystem: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (13000ns min, 2750ns max)
    Interrupt: pin A routed to IRQ 7
    Region 0: I/O ports at e400 [size=256]
    Region 1: Memory at f2000000 (32-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 28000000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: sis900
    Kernel modules: sis900

00:07.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6833]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at f2002000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: rt2500pci
    Kernel modules: rt2500pci

00:0c.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
    Subsystem: ENE Technology Inc CB1410 Cardbus Controller [1524:1410]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 7
    Region 0: Memory at 28023000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 00001800-000018ff
    I/O window 1: 00001c00-00001cff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:8130]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 10
    BIST result: 00
    Region 0: Memory at a0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=128K]
    Region 2: I/O ports at c000 [size=128]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] AGP version 3.0
        Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
        Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
    Kernel modules: sisfb

```

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dffffc0 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-E7FFF write-protect
[    0.000000]   E8000-EBFFF uncachable
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 010000000 mask FF8000000 write-back
[    0.000000]   2 base 018000000 mask FFC000000 write-back
[    0.000000]   3 base 01C000000 mask FFE000000 write-back
[    0.000000]   4 base 0F0000000 mask FFE000000 write-combining
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  modified: 000000001dff0000 - 000000001dffffc0 (ACPI data)
[    0.000000]  modified: 000000001dffffc0 - 000000001e000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001dff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001dc00000 page 2M
[    0.000000]  001dc00000 - 001dff0000 page 4k
[    0.000000] kernel direct mapping tables up to 1dff0000 @ 7000-c000
[    0.000000] RAMDISK: 15b1f000 - 16833e48
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 1dfffbc0 00030 (v01 INSYDE RSDT_000 00000001 _CSI 00010101)
[    0.000000] ACPI: FACP 1dfffac0 00074 (v01 INSYDE FACP_000 00000100 _CSI 00010101)
[    0.000000] ACPI: DSDT 1dffc980 03138 (v01 INSYDE   VT8603 00001002 INTL 02002036)
[    0.000000] ACPI: FACS 1dffffc0 00040
[    0.000000] ACPI: BOOT 1dfffb50 00028 (v01 INSYDE ISC_BOOT 00000100 _CSI 00010101)
[    0.000000] ACPI: DBGP 1dfffb80 00034 (v01 INSYDE DBGP_000 00000001 _CSI 00010101)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dff0000
[    0.000000]   low ram: 0 - 1dff0000
[    0.000000]   node 0 low ram: 00000000 - 1dff0000
[    0.000000]   node 0 bootmap 00008000 - 0000bc00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [0015b1f000 - 0016833e48]          RAMDISK ==> [0015b1f000 - 0016833e48]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd144]              BRK ==> [00008da000 - 00008dd144]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dff0
[    0.000000]   HighMem  0x0001dff0 -> 0x0001dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001dff0
[    0.000000] On node 0 totalpages: 122763
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 928 pages used for memmap
[    0.000000]   Normal zone: 117840 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1e000000 (gap: 1e000000:e1f80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121803
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=20ee07a2-738c-4f32-b674-6a90b30709a2 ro nomce quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2457280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 462420k/491456k available (4673k kernel code, 28192k reserved, 2121k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xde7f0000 - 0xff7fe000   ( 528 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1666.753 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3333.50 BogoMIPS (lpj=6667012)
[    0.004046] Security Framework initialized
[    0.004100] AppArmor: AppArmor initialized
[    0.004114] Mount-cache hash table entries: 512
[    0.004360] Initializing cgroup subsys ns
[    0.004367] Initializing cgroup subsys cpuacct
[    0.004374] Initializing cgroup subsys memory
[    0.004391] Initializing cgroup subsys devices
[    0.004396] Initializing cgroup subsys freezer
[    0.004400] Initializing cgroup subsys net_cls
[    0.004436] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004441] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004463] Performance Events: AMD PMU driver.
[    0.004481] ... version:                0
[    0.004484] ... bit width:              48
[    0.004487] ... generic registers:      4
[    0.004490] ... value mask:             0000ffffffffffff
[    0.004493] ... max period:             00007fffffffffff
[    0.004495] ... fixed-purpose events:   0
[    0.004498] ... event mask:             000000000000000f
[    0.004505] Checking 'hlt' instruction... OK.
[    0.020838] SMP alternatives: switching to UP code
[    0.029828] Freeing SMP alternatives: 19k freed
[    0.029875] ACPI: Core revision 20090903
[    0.038924] ACPI: setting ELCR to 0200 (from 0c80)
[    0.040020] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040035] ftrace: allocating 21771 entries in 43 pages
[    0.048220] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.048228] weird, boot CPU (#0) not listed by the BIOS.
[    0.048232] SMP motherboard not detected.
[    0.048237] Local APIC not detected. Using dummy APIC emulation.
[    0.048240] SMP disabled
[    0.048719] Brought up 1 CPUs
[    0.048723] Total of 1 processors activated (3333.50 BogoMIPS).
[    0.049598] CPU0 attaching NULL sched-domain.
[    0.049983] devtmpfs: initialized
[    0.052219] regulator: core version 0.5
[    0.052251] Time: 14:54:34  Date: 06/01/10
[    0.052336] NET: Registered protocol family 16
[    0.052547] EISA bus registered
[    0.052570] ACPI: bus type pci registered
[    0.053159] PCI: PCI BIOS revision 2.10 entry at 0xe93d4, last bus=1
[    0.053163] PCI: Using configuration type 1 for base access
[    0.054429] bio: create slab <bio-0> at 0
[    0.055089] ACPI: EC: Look up EC in DSDT
[    0.058060] ACPI: Interpreter enabled
[    0.058071] ACPI: (supports S0 S3 S4 S5)
[    0.058099] ACPI: Using PIC for interrupt routing
[    0.060152] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.060321] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.065703] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.065904] ACPI: No dock devices found.
[    0.066128] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.066205] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf1ffffff]
[    0.066400] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.066466] pci 0000:00:02.1: reg 20 io port: [0x1400-0x141f]
[    0.066546] pci 0000:00:02.5: reg 20 io port: [0x1100-0x110f]
[    0.066614] pci 0000:00:02.6: reg 10 io port: [0xe000-0xe0ff]
[    0.066624] pci 0000:00:02.6: reg 14 io port: [0xe100-0xe17f]
[    0.066683] pci 0000:00:02.6: supports D1 D2
[    0.066686] pci 0000:00:02.6: PME# supported from D3hot D3cold
[    0.066693] pci 0000:00:02.6: PME# disabled
[    0.066745] pci 0000:00:02.7: reg 10 io port: [0xe200-0xe2ff]
[    0.066756] pci 0000:00:02.7: reg 14 io port: [0xe300-0xe37f]
[    0.066814] pci 0000:00:02.7: supports D1 D2
[    0.066817] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.066823] pci 0000:00:02.7: PME# disabled
[    0.066857] pci 0000:00:03.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.066931] pci 0000:00:03.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.067020] pci 0000:00:03.2: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.067082] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.067088] pci 0000:00:03.2: PME# disabled
[    0.067146] pci 0000:00:04.0: reg 10 io port: [0xe400-0xe4ff]
[    0.067156] pci 0000:00:04.0: reg 14 32bit mmio: [0xf2000000-0xf2000fff]
[    0.067191] pci 0000:00:04.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.067218] pci 0000:00:04.0: supports D1 D2
[    0.067221] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.067227] pci 0000:00:04.0: PME# disabled
[    0.067279] pci 0000:00:07.0: reg 10 32bit mmio: [0xf2002000-0xf2003fff]
[    0.067397] pci 0000:00:0c.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.067424] pci 0000:00:0c.0: supports D1 D2
[    0.067427] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.067433] pci 0000:00:0c.0: PME# disabled
[    0.067522] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xa0000000-0xa7ffffff]
[    0.067531] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xe001ffff]
[    0.067539] pci 0000:01:00.0: reg 18 io port: [0xc000-0xc07f]
[    0.067580] pci 0000:01:00.0: supports D1 D2
[    0.067629] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.067636] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xefffffff]
[    0.067643] pci 0000:00:01.0: bridge 32bit mmio pref: [0xa0000000-0xafffffff]
[    0.067679] pci_bus 0000:00: on NUMA node 0
[    0.067685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.067766] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.VPCI._PRT]
[    0.071030] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.071223] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 11) *0, disabled.
[    0.071442] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 *11)
[    0.071658] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 *7 11)
[    0.071847] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 7 11) *0, disabled.
[    0.072052] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 7 11) *0, disabled.
[    0.072245] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 7 11) *0, disabled.
[    0.072436] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 11) *0, disabled.
[    0.072648] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.072653] vgaarb: loaded
[    0.072861] SCSI subsystem initialized
[    0.073000] libata version 3.00 loaded.
[    0.073134] usbcore: registered new interface driver usbfs
[    0.073154] usbcore: registered new interface driver hub
[    0.073202] usbcore: registered new device driver usb
[    0.073426] ACPI: WMI: Mapper loaded
[    0.073429] PCI: Using ACPI for IRQ routing
[    0.073659] NetLabel: Initializing
[    0.073662] NetLabel:  domain hash size = 128
[    0.073665] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.073692] NetLabel:  unlabeled traffic allowed by default
[    0.073754] Switching to clocksource tsc
[    0.076001] AppArmor: AppArmor Filesystem Enabled
[    0.076001] pnp: PnP ACPI init
[    0.076001] ACPI: bus type pnp registered
[    0.092309] pnp: PnP ACPI: found 10 devices
[    0.092312] ACPI: ACPI bus type pnp unregistered
[    0.092319] PnPBIOS: Disabled by ACPI PNP
[    0.092344] system 00:03: iomem range 0x0-0x9ffff could not be reserved
[    0.092349] system 00:03: iomem range 0xcc000-0xcffff has been reserved
[    0.092354] system 00:03: iomem range 0xe0000-0xfffff could not be reserved
[    0.092359] system 00:03: iomem range 0x100000-0x1fffffff could not be reserved
[    0.092363] system 00:03: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.092368] system 00:03: iomem range 0xffee0000-0xffefffff has been reserved
[    0.092372] system 00:03: iomem range 0xfffc0000-0xffffffff has been reserved
[    0.092383] system 00:05: ioport range 0x300-0x301 has been reserved
[    0.092387] system 00:05: ioport range 0x310-0x31f has been reserved
[    0.092392] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.092396] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.092400] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.092405] system 00:05: ioport range 0x1080-0x10ff has been reserved
[    0.127238] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.127244] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.127253] pci 0000:00:01.0:   MEM window: 0xe0000000-0xefffffff
[    0.127260] pci 0000:00:01.0:   PREFETCH window: 0xa0000000-0xafffffff
[    0.127271] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
[    0.127275] pci 0000:00:0c.0:   IO window: 0x001800-0x0018ff
[    0.127282] pci 0000:00:0c.0:   IO window: 0x001c00-0x001cff
[    0.127289] pci 0000:00:0c.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.127295] pci 0000:00:0c.0:   MEM window: 0x24000000-0x27ffffff
[    0.127641] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[    0.127646] PCI: setting IRQ 7 as level-triggered
[    0.127654] pci 0000:00:0c.0: PCI INT A -> Link[LNKD] -> GSI 7 (level, low) -> IRQ 7
[    0.127666] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.127670] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.127674] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.127678] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xefffffff]
[    0.127682] pci_bus 0000:01: resource 2 pref mem [0xa0000000-0xafffffff]
[    0.127686] pci_bus 0000:02: resource 0 io:  [0x1800-0x18ff]
[    0.127690] pci_bus 0000:02: resource 1 io:  [0x1c00-0x1cff]
[    0.127694] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.127697] pci_bus 0000:02: resource 3 mem: [0x24000000-0x27ffffff]
[    0.127764] NET: Registered protocol family 2
[    0.127912] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.128342] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.128701] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.129037] TCP: Hash tables configured (established 16384 bind 16384)
[    0.129041] TCP reno registered
[    0.129145] NET: Registered protocol family 1
[    0.129194] pci 0000:01:00.0: Boot video device
[    0.129355] Simple Boot Flag at 0x37 set to 0x1
[    0.129448] cpufreq-nforce2: No nForce2 chipset.
[    0.129499] Scanning for low memory corruption every 60 seconds
[    0.129764] audit: initializing netlink socket (disabled)
[    0.129785] type=2000 audit(1275404074.126:1): initialized
[    0.141705] Trying to unpack rootfs image as initramfs...
[    0.154808] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.160687] VFS: Disk quotas dquot_6.5.2
[    0.160798] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.161693] fuse init (API version 7.13)
[    0.161823] msgmni has been set to 904
[    0.166729] alg: No test for stdrng (krng)
[    0.166907] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.166913] io scheduler noop registered
[    0.166917] io scheduler anticipatory registered
[    0.166920] io scheduler deadline registered
[    0.167006] io scheduler cfq registered (default)
[    0.167207] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.167243] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.182457] ACPI: AC Adapter [AC] (on-line)
[    0.182625] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.182634] ACPI: Power Button [PBTN]
[    0.182712] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.198703] ACPI: Lid Switch [LID]
[    0.198887] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.198896] ACPI: Sleep Button [SLPB]
[    0.199002] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.199006] ACPI: Power Button [PWRF]
[    0.199239] Marking TSC unstable due to TSC halts in idle
[    0.199328] processor LNXCPU:00: registered as cooling_device0
[    0.202365] Switching to clocksource acpi_pm
[    0.248293] thermal LNXTHERM:01: registered as thermal_zone0
[    0.248319] ACPI: Thermal Zone [THZN] (56 C)
[    0.250985] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.251131] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.251915] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.251921] PCI: setting IRQ 11 as level-triggered
[    0.251929] serial 0000:00:02.6: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.251942] serial 0000:00:02.6: PCI INT C disabled
[    0.253642] brd: module loaded
[    0.254433] loop: module loaded
[    0.254591] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.254813] pata_sis 0000:00:02.5: version 0.5.2
[    0.260718] isapnp: Scanning for PnP cards...
[    0.266255] scsi0 : pata_sis
[    0.268085] scsi1 : pata_sis
[    0.269466] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.269472] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.270050] Fixed MDIO Bus: probed
[    0.270116] PPP generic driver version 2.4.2
[    0.270261] tun: Universal TUN/TAP device driver, 1.6
[    0.270264] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.270475] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.270511] ehci_hcd 0000:00:03.2: enabling device (0000 -> 0002)
[    0.270876] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.270884] ehci_hcd 0000:00:03.2: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.270927] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    0.270987] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    0.273102] ehci_hcd 0000:00:03.2: can't setup
[    0.273109] ehci_hcd 0000:00:03.2: USB bus 1 deregistered
[    0.320366] ehci_hcd 0000:00:03.2: PCI INT D disabled
[    0.320373] ehci_hcd 0000:00:03.2: init 0000:00:03.2 fail, -110
[    0.320383] ehci_hcd: probe of 0000:00:03.2 failed with error -110
[    0.320436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.320470] ohci_hcd 0000:00:03.0: enabling device (0000 -> 0002)
[    0.320846] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    0.320853] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    0.320886] ohci_hcd 0000:00:03.0: setting latency timer to 64
[    0.320891] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.320975] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    0.321028] ohci_hcd 0000:00:03.0: irq 11, io mem 0x28020000
[    0.408372] ohci_hcd 0000:00:03.0: USB HC reset timed out!
[    0.408382] ohci_hcd 0000:00:03.0: can't start
[    0.408406] ohci_hcd 0000:00:03.0: startup error -1
[    0.408416] ohci_hcd 0000:00:03.0: USB bus 1 deregistered
[    0.408614] ohci_hcd 0000:00:03.0: PCI INT A disabled
[    0.408618] ohci_hcd 0000:00:03.0: init 0000:00:03.0 fail, -1
[    0.408629] ohci_hcd: probe of 0000:00:03.0 failed with error -1
[    0.408663] ohci_hcd 0000:00:03.1: enabling device (0000 -> 0002)
[    0.409081] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.409089] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.409124] ohci_hcd 0000:00:03.1: setting latency timer to 64
[    0.409129] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.409217] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 1
[    0.409259] ohci_hcd 0000:00:03.1: irq 11, io mem 0x28021000
[    0.428788] ata1.00: ATAPI: Slimtype COMBO SOSC-2483K, KKF1, max UDMA/33
[    0.444602] ata1.00: configured for UDMA/33
[    0.496121] ohci_hcd 0000:00:03.1: USB HC reset timed out!
[    0.496132] ohci_hcd 0000:00:03.1: can't start
[    0.496156] ohci_hcd 0000:00:03.1: startup error -1
[    0.496167] ohci_hcd 0000:00:03.1: USB bus 1 deregistered
[    0.496365] ohci_hcd 0000:00:03.1: PCI INT B disabled
[    0.496370] ohci_hcd 0000:00:03.1: init 0000:00:03.1 fail, -1
[    0.496380] ohci_hcd: probe of 0000:00:03.1 failed with error -1
[    0.496427] uhci_hcd: USB Universal Host Controller Interface driver
[    0.496617] PNP: PS/2 Controller [PNP0303:KBC,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    0.500796] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.507919] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.507936] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.512286] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.512364] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.512411] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.512675] mice: PS/2 mouse device common for all mice
[    0.512965] rtc_cmos 00:01: RTC can wake from S4
[    0.513064] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.513097] rtc0: alarms up to one year, 114 bytes nvram
[    0.513306] device-mapper: uevent: version 1.0.3
[    0.515249] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.516993] device-mapper: multipath: version 1.1.0 loaded
[    0.516999] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.518353] EISA: Probing bus 0 at eisa.0
[    0.518367] Cannot allocate resource for EISA slot 1
[    0.518401] EISA: Detected 0 cards.
[    0.519221] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.521400] cpuidle: using governor ladder
[    0.521488] cpuidle: using governor menu
[    0.522159] TCP cubic registered
[    0.522379] NET: Registered protocol family 10
[    0.523038] lo: Disabled Privacy Extensions
[    0.523456] NET: Registered protocol family 17
[    0.523533] powernow-k8: Processor cpuid 6a0 not supported
[    0.523636] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    0.528185] powernow: Trying ACPI perflib
[    0.533237] powernow: Minimum speed 400 MHz. Maximum speed 1666 MHz.
[    0.533343] Using IPI No-Shortcut mode
[    0.533578] PM: Resume from disk failed.
[    0.533610] registered taskstats version 1
[    0.533940]   Magic number: 14:448:939
[    0.534151] rtc_cmos 00:01: setting system clock to 2010-06-01 14:54:35 UTC (1275404075)
[    0.534157] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.534159] EDD information not available.
[    0.956056] isapnp: No Plug & Play device found
[    0.957611] scsi 0:0:0:0: CD-ROM            Slimtype COMBO SOSC-2483K KKF1 PQ: 0 ANSI: 5
[    0.963068] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    0.963079] Uniform CD-ROM driver Revision: 3.20
[    0.963356] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.963507] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.074035] Freeing initrd memory: 13395k freed
[    1.124364] ACPI: Battery Slot [BAT2] (battery present)
[    1.125091] ata2.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[    1.125097] ata2.00: 117210240 sectors, multi 16: LBA48 
[    1.125128] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.140729] ata2.00: configured for UDMA/33
[    1.141032] scsi 1:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    1.141374] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.141527] sd 1:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.141618] sd 1:0:0:0: [sda] Write Protect is off
[    1.141623] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.141669] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.141934]  sda: sda1 sda2 sda3 sda4
[    1.185841] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.185873] Freeing unused kernel memory: 656k freed
[    1.187293] Write protecting the kernel text: 4676k
[    1.187336] Write protecting the kernel read-only data: 1840k
[    1.222923] udev: starting version 151
[    1.588729] vga16fb: initializing
[    1.588742] vga16fb: mapped to 0xc00a0000
[    1.588881] fb0: VGA16 VGA frame buffer device
[    1.590409] Linux agpgart interface v0.103
[    1.599714] sis900.c: v1.08.10 Apr. 2 2006
[    1.599796] sis900 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 7 (level, low) -> IRQ 7
[    1.606883] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.616697] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 2.
[    1.629327] 0000:00:04.0: Using transceiver found at address 2 as default
[    1.639597] acpi device:01: registered as cooling_device1
[    1.639898] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[    1.640108] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.689199] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 7, 00:40:ca:cd:f6:8f
[    1.689254] agpgart-sis 0000:00:00.0: SiS chipset [1039/0741]
[    1.693726] agpgart-sis 0000:00:00.0: AGP aperture is 32M @ 0xf0000000
[    1.750213] Console: switching to colour frame buffer device 80x30
[    2.292129] xor: automatically using best checksumming function: pIII_sse
[    2.312024]    pIII_sse  :  3581.000 MB/sec
[    2.312028] xor: using function: pIII_sse (3581.000 MB/sec)
[    2.340740] device-mapper: dm-raid45: initialized v0.2594b
[    2.462856] EXT3-fs: INFO: recovery required on readonly filesystem.
[    2.462864] EXT3-fs: write access will be enabled during recovery.
[    8.945483] kjournald starting.  Commit interval 5 seconds
[    8.945524] EXT3-fs: sda3: orphan cleanup on readonly fs
[    8.945534] ext3_orphan_cleanup: deleting unreferenced inode 621876
[    8.945628] ext3_orphan_cleanup: deleting unreferenced inode 621872
[    8.975073] ext3_orphan_cleanup: deleting unreferenced inode 621867
[    8.975090] ext3_orphan_cleanup: deleting unreferenced inode 621863
[    8.975105] ext3_orphan_cleanup: deleting unreferenced inode 621859
[    8.975120] ext3_orphan_cleanup: deleting unreferenced inode 621857
[    9.003851] ext3_orphan_cleanup: deleting unreferenced inode 621846
[    9.053574] ext3_orphan_cleanup: deleting unreferenced inode 596873
[    9.095356] EXT3-fs: sda3: 8 orphan inodes deleted
[    9.095360] EXT3-fs: recovery complete.
[    9.101001] EXT3-fs: mounted filesystem with ordered data mode.
[   11.341371] Adding 1052248k swap on /dev/sda2.  Priority:-1 extents:1 across:1052248k 
[   11.892679] udev: starting version 151
[   12.848265] lp: driver loaded but no devices found
[   14.130227] cfg80211: Calling CRDA to update world regulatory domain
[   14.137660] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
[   14.147943] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.470604] cfg80211: World regulatory domain updated:
[   14.470613]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.470619]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.470623]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.470628]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.470632]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.470635]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.582861] input: PS/2 Mouse as /devices/platform/i8042/serio3/input/input7
[   14.605334] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio3/input/input8
[   14.860676] yenta_cardbus 0000:00:0c.0: CardBus bridge found [1524:1410]
[   14.860710] yenta_cardbus 0000:00:0c.0: Enabling burst memory read transactions
[   14.860718] yenta_cardbus 0000:00:0c.0: Using CSCINT to route CSC interrupts to PCI
[   14.860721] yenta_cardbus 0000:00:0c.0: Routing CardBus interrupts to PCI
[   14.860730] yenta_cardbus 0000:00:0c.0: TI: mfunc 0x01021002, devctl 0x44
[   14.964058] yenta_cardbus 0000:00:0c.0: TI: probing PCI interrupt failed, trying to fix
[   15.068121] yenta_cardbus 0000:00:0c.0: Yenta TI: no PCI interrupts. Fish. Please report.
[   15.068137] yenta_cardbus 0000:00:0c.0: no PCI IRQ, CardBus support disabled for this socket.
[   15.068140] yenta_cardbus 0000:00:0c.0: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   15.196772] yenta_cardbus 0000:00:0c.0: ISA IRQ mask 0x0000, PCI irq 0
[   15.196782] yenta_cardbus 0000:00:0c.0: Socket status: 1ecca3b2
[   15.197495] rt2500pci 0000:00:07.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   15.603509] phy0: Selected rate control algorithm 'minstrel'
[   15.604747] Registered led device: rt2500pci-phy0::radio
[   15.604776] Registered led device: rt2500pci-phy0::quality
[   15.843825] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   15.845785] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.846568] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.847276] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.848355] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.975238] Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   16.620930] EXT3 FS on sda3, internal journal
[   16.800050] intel8x0_measure_ac97_clock: measured 55261 usecs (2659 samples)
[   16.800058] intel8x0: clocking to 48000
[   18.040795] kjournald starting.  Commit interval 5 seconds
[   18.041123] EXT3 FS on sda4, internal journal
[   18.041133] EXT3-fs: mounted filesystem with ordered data mode.
[   22.945931] eth0: Media Link Off
[   22.946111] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.977363] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.086650] ppdev: user-space parallel port driver
[  103.625979] wlan0: direct probe to AP 00:22:6b:77:da:f1 (try 1)
[  103.626089] wlan0: deauthenticating from 00:22:6b:77:da:f1 by local choice (reason=3)
[  103.626217] wlan0: direct probe to AP 00:22:6b:77:da:f1 (try 1)
[  103.630918] wlan0: direct probe responded
[  103.630946] wlan0: authenticate with AP 00:22:6b:77:da:f1 (try 1)
[  103.636748] wlan0: authenticated
[  103.636859] wlan0: associate with AP 00:22:6b:77:da:f1 (try 1)
[  103.638874] wlan0: RX AssocResp from 00:22:6b:77:da:f1 (capab=0x401 status=0 aid=3)
[  103.638891] wlan0: associated
[  103.642454] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.646044] cfg80211: Calling CRDA for country: US
[  103.678755] cfg80211: Received country IE:
[  103.678780] cfg80211: Regulatory domain: US
[  103.678792]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  103.678812]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  103.678824] cfg80211: CRDA thinks this should applied:
[  103.678834] cfg80211: Regulatory domain: US
[  103.678843]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  103.678859]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  103.678876]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  103.678892]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  103.678908]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  103.678924]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  103.678939]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  103.678951] cfg80211: We intersect both of these and get:
[  103.678961] cfg80211: Regulatory domain: 98
[  103.678970]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  103.678986]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  103.679017] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[  103.679031] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[  103.679044] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[  103.679065] cfg80211: Current regulatory domain updated by AP to: US
[  103.679075]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  103.679092]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  103.828087] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  104.748189] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  105.748138] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  106.216189] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  107.060134] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  107.288201] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  107.648174] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  107.828107] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  108.080097] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  108.280225] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  108.896060] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  109.530404] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  109.836096] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  110.076094] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  110.636150] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  111.024108] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  114.568038] wlan0: no IPv6 routers present
[  117.828136] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  118.672132] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  120.364049] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  120.808064] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  124.452184] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  124.664195] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  124.868101] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  125.180197] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  125.384129] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  125.588106] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  130.848147] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  132.596102] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  132.856206] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  137.868149] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  139.184098] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  139.736057] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  140.248140] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  145.660124] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  145.860184] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  146.360246] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  147.112120] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  147.544138] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  154.284111] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  158.540133] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  160.936090] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  162.068151] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  175.932205] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  177.692084] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  208.000192] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  216.612197] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  217.064189] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  217.756204] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  237.640201] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  268.000156] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  282.652198] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  297.632189] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  305.664155] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  306.084103] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  321.084110] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  327.700207] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  341.232142] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  342.232136] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  342.644090] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  356.927664] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  357.268070] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  357.836088] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  388.184194] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  397.632193] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  412.472114] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  414.648063] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  415.308081] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  416.076067] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  417.200345] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  448.184171] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  463.184104] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  477.328217] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  478.168212] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  487.108078] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[  517.628194] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).

```

lsusb gives no response.

---

### Post by ibuclaw on 2010-06-01
> **dragos240 said:**
> Linux amundsen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2


lsusb gives no response.

Snipping out the interesting bits.

```

00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10)
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at 28020000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10)
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 11
    Region 0: Memory at 28021000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] (prog-if 20)
    Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin D routed to IRQ 11
    Region 0: Memory at 28022000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```
USB Controllers are picked up OK, however no kernel module is using them, else you would have ie:

Kernel driver in use: ehci_hcd

Outputted at the bottom of each device stanza.


Now, as to why there are no kernel modules using them...
```

[    0.270475] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.270511] ehci_hcd 0000:00:03.2: enabling device (0000 -> 0002)
[    0.270876] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.270884] ehci_hcd 0000:00:03.2: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.270927] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    0.270987] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    0.273102] ehci_hcd 0000:00:03.2: can't setup
[    0.273109] ehci_hcd 0000:00:03.2: USB bus 1 deregistered
[    0.320366] ehci_hcd 0000:00:03.2: PCI INT D disabled
[    0.320373] ehci_hcd 0000:00:03.2: init 0000:00:03.2 fail, -110
[    0.320383] ehci_hcd: probe of 0000:00:03.2 failed with error -110
[    0.320436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.320470] ohci_hcd 0000:00:03.0: enabling device (0000 -> 0002)
[    0.320846] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    0.320853] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    0.320886] ohci_hcd 0000:00:03.0: setting latency timer to 64
[    0.320891] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.320975] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    0.321028] ohci_hcd 0000:00:03.0: irq 11, io mem 0x28020000
[    0.408372] ohci_hcd 0000:00:03.0: USB HC reset timed out!
[    0.408382] ohci_hcd 0000:00:03.0: can't start
[    0.408406] ohci_hcd 0000:00:03.0: startup error -1
[    0.408416] ohci_hcd 0000:00:03.0: USB bus 1 deregistered
[    0.408614] ohci_hcd 0000:00:03.0: PCI INT A disabled
[    0.408618] ohci_hcd 0000:00:03.0: init 0000:00:03.0 fail, -1
[    0.408629] ohci_hcd: probe of 0000:00:03.0 failed with error -1
[    0.408663] ohci_hcd 0000:00:03.1: enabling device (0000 -> 0002)
[    0.409081] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.409089] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.409124] ohci_hcd 0000:00:03.1: setting latency timer to 64
[    0.409129] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.409217] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 1
[    0.409259] ohci_hcd 0000:00:03.1: irq 11, io mem 0x28021000
[    0.428788] ata1.00: ATAPI: Slimtype COMBO SOSC-2483K, KKF1, max UDMA/33
[    0.444602] ata1.00: configured for UDMA/33
[    0.496121] ohci_hcd 0000:00:03.1: USB HC reset timed out!
[    0.496132] ohci_hcd 0000:00:03.1: can't start
[    0.496156] ohci_hcd 0000:00:03.1: startup error -1
[    0.496167] ohci_hcd 0000:00:03.1: USB bus 1 deregistered
[    0.496365] ohci_hcd 0000:00:03.1: PCI INT B disabled
[    0.496370] ohci_hcd 0000:00:03.1: init 0000:00:03.1 fail, -1
[    0.496380] ohci_hcd: probe of 0000:00:03.1 failed with error -1
[    0.496427] uhci_hcd: USB Universal Host Controller Interface driver

```

Hmm... that is something that will need to look up. :)

---

### Post by dragos240 on 2010-06-01
I wonder what's wrong. Tell me if you find something.

---

### Post by ibuclaw on 2010-06-02
I can only really think of 2 explanations:

1) The USB Controller provides too little current.
2) An issue with the System board resource allocation.


You could try booting with various pci= options, and I'd recommend checking BIOS too, see if there are any options that you can tweak.

Regards

---

### Post by dragos240 on 2010-06-02
I do however know that windows is able to use it. Maybe it's a driver issue. Also, to boot into linux I need to add a nomce option. Not sure why, but it provides a kernel taint debugging error if I don't.

---

### Post by ibuclaw on 2010-06-02
> **dragos240 said:**
> I do however know that windows is able to use it. Maybe it's a driver issue. Also, to boot into linux I need to add a nomce option. Not sure why, but it provides a kernel taint debugging error if I don't.

That old, eh? ;)


Well, to start you off, you could try booting with one of
```

irqpoll
pci=noacpi

```
And check dmesg to see how Linux reacts to discovering the USB Controller.

---

### Post by ibuclaw on 2010-06-02
And try loading ohci (am pretty certain the USB controller should be handled by the OHCI driver, and there is no evidence to suggest that this controller is buggy on other systems) with the option "no_handshake".

/etc/modprobe.d/ohci-usb.conf
```
options ohci-hcd no_handshake
```

Also, don't suppose you could rebuild the kernel with the config option CONFIG_USB_DEBUG enabled, could you? :)

---

### Post by dragos240 on 2010-06-02
> **ibuclaw said:**
> And try loading ohci (am pretty certain the USB controller should be handled by the OHCI driver, and there is no evidence to suggest that this controller is buggy on other systems) with the option "no_handshake".

/etc/modprobe.d/ohci-usb.conf
```
options ohci-hcd no_handshake
```Also, don't suppose you could rebuild the kernel with the config option CONFIG_USB_DEBUG enabled, could you? :)

Where would that be on menuconfig. Since I'm a former gentoo user, rebuilding a kernel will be a snap.

---

### Post by dragos240 on 2010-06-02
Also those options didn't work. Please tell me what option it's labeled in menuconfig.

---

### Post by ibuclaw on 2010-06-02
> **dragos240 said:**
> Also those options didn't work. Please tell me what option it's labeled in menuconfig.

I can't say where it is off hand, but should be able to search for it using the '**/**' key.

---

### Post by dragos240 on 2010-06-03
> **ibuclaw said:**
> I can't say where it is off hand, but should be able to search for it using the '**/**' key.

You're right. In the .config?

"vim .config"?

---

### Post by ibuclaw on 2010-06-03
> **dragos240 said:**
> You're right. In the .config?

"vim .config"?

In 'make menuconfig' ... you can search using '**/**' ... 

I take it you've never done this before then... ;)

---

### Post by dragos240 on 2010-06-03
> **ibuclaw said:**
> In 'make menuconfig' ... you can search using '**/**' ... 

I take it you've never done this before then... ;)

The gentoo manual did not specify that. That's all I knew.

---

