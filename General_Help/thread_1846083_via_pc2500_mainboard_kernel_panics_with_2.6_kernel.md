---
title: "via pc2500 mainboard kernel panics with 2.6 kernel"
date: 2011-09-18
forum: General Help
---

### Post by markolonius on 2011-09-18
Hello,

I'm not exactly sure when this started but its been going on for a long time.  I have a via pc2500 mainboard that keeps giving me kernel panics.  Then happen at random times, but seem to have the same stack trace.  I managed to find a dmesg that contains some stack trace, which is attached along with the dmesg.0.  I ran damn small linux which runs on 2.4 kernel and no kernel panics at all.  I feel like its something to do with acpi, but I can be very wrong. If anyone has any idea how to fix this, the help would be very much appreciated. 

(most system info can be found in the dmesg)

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic-pae (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 (Ubuntu 2.6.38-11.48-generic-pae 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: IDOT ID-PCM7E PC2500/ID-PCM7E PC2500, BIOS 6.00 PG 09/26/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7bf00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-EFFFF uncachable
[    0.000000]   F0000-F7FFF write-through
[    0.000000]   F8000-F8FFF uncachable
[    0.000000]   F9000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07C000000 mask FFC000000 uncachable
[    0.000000]   2 base 0E8000000 mask FF8000000 write-combining
[    0.000000]   3 base 07BF00000 mask FFFF00000 write-through
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f39d0] f39d0
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 365dc000 - 372e6000
[    0.000000] 1091MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007bf00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007bf00
[    0.000000] On node 0 totalpages: 507535
[    0.000000] free_area_init_node: node 0, pgdat c17bac40, node_mem_map f565c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2183 pages used for memmap
[    0.000000]   HighMem zone: 277115 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] Intel MultiProcessor Specification v1.1
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: OEM00000
[    0.000000] MPTABLE: Product ID: PROD00000000
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] Processors: 1
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7bf00000 (gap: 7bf00000:82d00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s32320 r0 d20928 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503568
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-11-generic-pae root=/dev/mapper/media-root ro acpi=off noapic nolapic quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10152640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007bf00)
[    0.000000] Memory: 1980460k/2030592k available (5351k kernel code, 49680k reserved, 2597k data, 720k init, 1117192k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539e95 - 0xc17c35c0   (2597 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539e95   (5351 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f7406000 soft=f7408000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.341 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.68 BogoMIPS (lpj=5985364)
[    0.004019] pid_max: default: 32768 minimum: 301
[    0.004075] Security Framework initialized
[    0.004134] AppArmor: AppArmor initialized
[    0.004140] Yama: becoming mindful.
[    0.004289] Mount-cache hash table entries: 512
[    0.004590] Initializing cgroup subsys ns
[    0.004599] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004608] Initializing cgroup subsys cpuacct
[    0.004622] Initializing cgroup subsys memory
[    0.004645] Initializing cgroup subsys devices
[    0.004653] Initializing cgroup subsys freezer
[    0.004659] Initializing cgroup subsys net_cls
[    0.004666] Initializing cgroup subsys blkio
[    0.008767] SMP alternatives: switching to UP code
[    0.036180] Freeing SMP alternatives: 20k freed
[    0.036237] ftrace: allocating 24259 entries in 48 pages
[    0.040184] SMP disabled
[    0.040194] Performance Events: 
[    0.041345] Brought up 1 CPUs
[    0.041355] Total of 1 processors activated (2992.68 BogoMIPS).
[    0.041641] devtmpfs: initialized
[    0.045252] print_constraints: dummy: 
[    0.045303] Time: 10:17:14  Date: 09/18/11
[    0.045407] NET: Registered protocol family 16
[    0.045662] EISA bus registered
[    0.054070] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.054080] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
[    0.054086] PCI: Using configuration type 1 for base access
[    0.056837] bio: create slab <bio-0> at 0
[    0.057080] ACPI: Interpreter disabled.
[    0.057250] vgaarb: loaded
[    0.057728] SCSI subsystem initialized
[    0.057855] libata version 3.00 loaded.
[    0.057978] usbcore: registered new interface driver usbfs
[    0.058013] usbcore: registered new interface driver hub
[    0.058070] usbcore: registered new device driver usb
[    0.058283] PCI: Probing PCI hardware
[    0.058289] PCI: Probing PCI hardware (bus 00)
[    0.058390] pci 0000:00:00.0: [1106:0314] type 0 class 0x000600
[    0.058410] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.058498] pci 0000:00:00.1: [1106:1314] type 0 class 0x000600
[    0.058560] pci 0000:00:00.2: [1106:2314] type 0 class 0x000600
[    0.058623] pci 0000:00:00.3: [1106:3208] type 0 class 0x000600
[    0.058685] pci 0000:00:00.4: [1106:4314] type 0 class 0x000600
[    0.058753] pci 0000:00:00.7: [1106:7314] type 0 class 0x000600
[    0.058819] pci 0000:00:01.0: [1106:b198] type 1 class 0x000604
[    0.058878] pci 0000:00:01.0: supports D1
[    0.058915] pci 0000:00:08.0: [1317:0985] type 0 class 0x000200
[    0.058940] pci 0000:00:08.0: reg 10: [io  0xf200-0xf2ff]
[    0.058957] pci 0000:00:08.0: reg 14: [mem 0xfdfff000-0xfdfff3ff]
[    0.059013] pci 0000:00:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.059039] pci 0000:00:08.0: supports D1 D2
[    0.059046] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.059056] pci 0000:00:08.0: PME# disabled
[    0.059094] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000101
[    0.059120] pci 0000:00:0f.0: reg 10: [io  0xff00-0xff07]
[    0.059136] pci 0000:00:0f.0: reg 14: [io  0xfe00-0xfe03]
[    0.059153] pci 0000:00:0f.0: reg 18: [io  0xfd00-0xfd07]
[    0.059170] pci 0000:00:0f.0: reg 1c: [io  0xfc00-0xfc03]
[    0.059187] pci 0000:00:0f.0: reg 20: [io  0xfb00-0xfb0f]
[    0.059203] pci 0000:00:0f.0: reg 24: [io  0xf400-0xf4ff]
[    0.059265] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.059329] pci 0000:00:0f.1: reg 20: [io  0xfa00-0xfa0f]
[    0.059411] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
[    0.059495] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.059552] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
[    0.059578] pci 0000:00:11.5: reg 10: [io  0xf000-0xf0ff]
[    0.059662] pci 0000:00:11.5: supports D1 D2
[    0.059744] pci 0000:01:00.0: [1106:3344] type 0 class 0x000300
[    0.059768] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf7ffffff pref]
[    0.059784] pci 0000:01:00.0: reg 14: [mem 0xfb000000-0xfbffffff]
[    0.059828] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.059855] pci 0000:01:00.0: supports D1 D2
[    0.059906] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.059916] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.059926] pci 0000:00:01.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.059937] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff pref]
[    0.060806] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.061216] PCI: pci_cache_line_size set to 64 bytes
[    0.061302] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.061310] reserve RAM buffer: 000000007bf00000 - 000000007bffffff 
[    0.061597] NetLabel: Initializing
[    0.061602] NetLabel:  domain hash size = 128
[    0.061607] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.061637] NetLabel:  unlabeled traffic allowed by default
[    0.061766] Switching to clocksource pit
[    0.078932] AppArmor: AppArmor Filesystem Enabled
[    0.078989] pnp: PnP ACPI: disabled
[    0.078998] PnPBIOS: Scanning system for PnP BIOS support...
[    0.079203] PnPBIOS: Found PnP BIOS installation structure at 0xc00faa00
[    0.079211] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xaa30, dseg 0xf0000
[    0.079299] pnp 00:00: [irq 2]
[    0.079306] pnp 00:00: [io  0x0020-0x0021]
[    0.079313] pnp 00:00: [io  0x00a0-0x00a1]
[    0.079371] pnp 00:00: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.079387] pnp 00:01: [dma 4]
[    0.079393] pnp 00:01: [io  0x0000-0x000f]
[    0.079399] pnp 00:01: [io  0x0081-0x0083]
[    0.079405] pnp 00:01: [io  0x0087]
[    0.079411] pnp 00:01: [io  0x0089-0x008b]
[    0.079417] pnp 00:01: [io  0x008f-0x0091]
[    0.079423] pnp 00:01: [io  0x00c0-0x00df]
[    0.079476] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.079490] pnp 00:02: [irq 0]
[    0.079495] pnp 00:02: [io  0x0040-0x0043]
[    0.079541] pnp 00:02: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.079560] pnp 00:03: [irq 8]
[    0.079566] pnp 00:03: [io  0x0070-0x0071]
[    0.079612] pnp 00:03: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.079625] pnp 00:04: [irq 1]
[    0.079631] pnp 00:04: [io  0x0060]
[    0.079637] pnp 00:04: [io  0x0064]
[    0.079682] pnp 00:04: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.079696] pnp 00:05: [io  0x0061]
[    0.079747] pnp 00:05: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.079761] pnp 00:06: [irq 13]
[    0.079767] pnp 00:06: [io  0x00f0-0x00ff]
[    0.079814] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.079829] pnp 00:07: [mem 0x00000000-0x0009ffff]
[    0.079837] pnp 00:07: [mem 0xfffffffffffe0000-0xffffffffffffffff]
[    0.079845] pnp 00:07: [mem 0xfffffffffec00000-0xfffffffffec0ffff]
[    0.079853] pnp 00:07: [mem 0xfffffffffee00000-0xfffffffffee0ffff]
[    0.079860] pnp 00:07: [mem 0x00100000-0x00ffffff]
[    0.079973] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.079982] system 00:07: [mem 0xfffffffffffe0000-0xffffffffffffffff] could not be reserved
[    0.079992] system 00:07: [mem 0xfffffffffec00000-0xfffffffffec0ffff] could not be reserved
[    0.080002] system 00:07: [mem 0xfffffffffee00000-0xfffffffffee0ffff] could not be reserved
[    0.080013] system 00:07: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.080022] system 00:07: Plug and Play BIOS device, IDs PNP0c01 (active)
[    0.080037] pnp 00:08: [mem 0x000f0000-0x000f3fff]
[    0.080043] pnp 00:08: [mem 0x000f4000-0x000f7fff]
[    0.080050] pnp 00:08: [mem 0x000f8000-0x000fffff]
[    0.080057] pnp 00:08: [mem 0x000cfe00-0x000cffff]
[    0.080136] system 00:08: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.080145] system 00:08: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.080154] system 00:08: [mem 0x000f8000-0x000fffff] could not be reserved
[    0.080162] system 00:08: [mem 0x000cfe00-0x000cffff] has been reserved
[    0.080171] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.080186] pnp 00:09: [io  0x04d0-0x04d1]
[    0.080192] pnp 00:09: [io  0x0cf8-0x0cff]
[    0.080239] pnp 00:09: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.080254] pnp 00:0a: [irq 12]
[    0.080313] pnp 00:0a: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.080382] pnp 00:0b: [irq 4]
[    0.080388] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.080463] pnp 00:0b: Plug and Play BIOS device, IDs PNP0501 (active)
[    0.080512] pnp 00:0c: [dma 2]
[    0.080518] pnp 00:0c: [io  0x03f0-0x03f5]
[    0.080524] pnp 00:0c: [io  0x03f7]
[    0.080530] pnp 00:0c: [irq 6]
[    0.080619] pnp 00:0c: Plug and Play BIOS device, IDs PNP0700 (active)
[    0.080694] pnp 00:0d: [irq 7]
[    0.080700] pnp 00:0d: [io  0x0378-0x037f]
[    0.080706] pnp 00:0d: [io  0x0778-0x077f]
[    0.080787] pnp 00:0d: Plug and Play BIOS device, IDs PNP0400 (active)
[    0.080799] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[    0.085419] pci 0000:00:08.0: BAR 6: assigned [mem 0x7c000000-0x7c01ffff pref]
[    0.085436] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc000000-0xfc00ffff pref]
[    0.085445] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.085454] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.085466] pci 0000:00:01.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.085477] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff pref]
[    0.085502] pci 0000:00:01.0: setting latency timer to 64
[    0.085513] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.085520] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.085528] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.085536] pci_bus 0000:01: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.085544] pci_bus 0000:01: resource 2 [mem 0xf4000000-0xf7ffffff pref]
[    0.085658] NET: Registered protocol family 2
[    0.085822] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.086628] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.088530] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.089459] TCP: Hash tables configured (established 131072 bind 65536)
[    0.089468] TCP reno registered
[    0.089481] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.089523] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.089790] NET: Registered protocol family 1
[    0.089851] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.089878] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.089900] pci 0000:01:00.0: Boot video device
[    0.089907] PCI: CLS 64 bytes, default 64
[    0.090266] cpufreq-nforce2: No nForce2 chipset.
[    0.090671] audit: initializing netlink socket (disabled)
[    0.090703] type=2000 audit(1316341034.088:1): initialized
[    0.117938] Trying to unpack rootfs image as initramfs...
[    0.151849] highmem bounce pool size: 64 pages
[    0.151864] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.163062] VFS: Disk quotas dquot_6.5.2
[    0.163276] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.165118] fuse init (API version 7.16)
[    0.165402] msgmni has been set to 1686
[    0.170765] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.170848] io scheduler noop registered
[    0.170854] io scheduler deadline registered
[    0.170902] io scheduler cfq registered (default)
[    0.171230] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.171290] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.175527] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.180047] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.180109] isapnp: Scanning for PnP cards...
[    0.192461] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.247138] Linux agpgart interface v0.103
[    0.247317] agpgart: Detected VIA VT3314 chipset
[    0.257499] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.260862] brd: module loaded
[    0.271381] loop: module loaded
[    0.271722] i2c-core: driver [adp5520] using legacy suspend method
[    0.271727] i2c-core: driver [adp5520] using legacy resume method
[    0.272250] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.272331] pata_acpi 0000:00:0f.1: setting latency timer to 64
[    0.273248] Fixed MDIO Bus: probed
[    0.273335] PPP generic driver version 2.4.2
[    0.273505] tun: Universal TUN/TAP device driver, 1.6
[    0.273511] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.273769] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.273824] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.273857] uhci_hcd: USB Universal Host Controller Interface driver
[    0.274109] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.274651] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.274675] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.279489] mousedev: PS/2 mouse device common for all mice
[    0.279783] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.279843] rtc0: alarms up to one day, 114 bytes nvram
[    0.280114] device-mapper: uevent: version 1.0.3
[    0.280321] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.280525] device-mapper: multipath: version 1.2.0 loaded
[    0.280532] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.280762] EISA: Probing bus 0 at eisa.0
[    0.280826] EISA: Detected 0 cards.
[    0.283503] cpuidle: using governor ladder
[    0.283513] cpuidle: using governor menu
[    0.284364] TCP cubic registered
[    0.284741] NET: Registered protocol family 10
[    0.286144] NET: Registered protocol family 17
[    0.286306] Registering the dns_resolver key type
[    0.286369] longhaul: Use acpi-cpufreq driver for VIA C7
[    0.286383] Using IPI No-Shortcut mode
[    0.286689] PM: Hibernation image not present or could not be loaded.
[    0.286720] registered taskstats version 1
[    0.287066]   Magic number: 11:150:275
[    0.287163] tty tty12: hash matches
[    0.287263] rtc_cmos 00:03: setting system clock to 2011-09-18 10:17:14 UTC (1316341034)
[    0.287272] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.287277] EDD information not available.
[    0.310460] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    0.838075] isapnp: No Plug & Play device found
[    1.114467] Switching to clocksource tsc
[    1.449685] Freeing initrd memory: 13352k freed
[    1.475938] Freeing unused kernel memory: 720k freed
[    1.477472] Write protecting the kernel text: 5352k
[    1.477644] Write protecting the kernel read-only data: 2192k
[    1.477649] NX-protecting the kernel data: 4888k
[    1.561465] <30>udev[57]: starting version 167
[    2.001787] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.001910] tulip_init_one: Enabled WOL support for AN983B
[    2.002501] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1
[    2.070030] net eth0: ADMtek Comet rev 17 at Port 0xf200, 00:06:25:07:d2:f8, IRQ 10
[    2.070102] pata_via 0000:00:0f.1: version 0.3.4
[    2.073527] scsi0 : pata_via
[    2.075540] scsi1 : pata_via
[    2.075722] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.075731] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.075968] sata_via 0000:00:0f.0: version 2.6
[    2.076070] sata_via 0000:00:0f.0: routed to hard irq line 11
[    2.079114] scsi2 : sata_via
[    2.080773] scsi3 : sata_via
[    2.080961] ata3: SATA max UDMA/133 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 11
[    2.080969] ata4: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 11
[    2.246721] ata1.00: ATAPI: LG CD-RW CED-8080B, 1.03, max UDMA/33
[    2.246738] ata1.01: ATAPI: MATSHITADVD-ROM SR-8585, 1W21, max UDMA/33
[    2.262516] ata1.00: configured for UDMA/33
[    2.270481] ata1.01: configured for UDMA/33
[    2.271779] scsi 0:0:0:0: CD-ROM            LG       CD-RW CED-8080B  1.03 PQ: 0 ANSI: 5
[    2.273670] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.273681] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.274040] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.274287] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.277320] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-ROM SR-8585  1W21 PQ: 0 ANSI: 5
[    2.278483] sr1: scsi3-mmc drive: 61x/61x cd/rw xa/form2 cdda tray
[    2.278855] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    2.279063] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.286258] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.444297] ata2.00: ATA-7: Maxtor 6L300R0, BAJ41G20, max UDMA/133
[    2.444305] ata2.00: 586114704 sectors, multi 1: LBA48 
[    2.456539] ata3.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.456548] ata3.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    2.460044] ata2.00: configured for UDMA/133
[    2.460330] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L300R0   BAJ4 PQ: 0 ANSI: 5
[    2.460830] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    2.461077] sd 1:0:0:0: [sda] 586114704 512-byte logical blocks: (300 GB/279 GiB)
[    2.461178] sd 1:0:0:0: [sda] Write Protect is off
[    2.461187] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.461232] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.471295] ata3.00: configured for UDMA/133
[    2.471583] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    2.472062] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    2.472343] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.472444] sd 2:0:0:0: [sdb] Write Protect is off
[    2.472453] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.472496] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.478557]  sdb: sdb1
[    2.479197] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.488048]  sda: sda1 sda2 < sda5 >
[    2.488871] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.674257] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.461136] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    3.461150] EXT4-fs (dm-0): write access will be enabled during recovery
[    3.714656] EXT4-fs (dm-0): recovery complete
[    3.715147] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   10.745636] <30>udev[258]: starting version 167
[   10.892663] Adding 2027516k swap on /dev/mapper/media-swap_1.  Priority:-1 extents:1 across:2027516k 
[   10.977943] lp: driver loaded but no devices found
[   11.326625] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   11.873765] type=1400 audit(1316341046.081:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=334 comm="apparmor_parser"
[   11.878463] type=1400 audit(1316341046.089:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=334 comm="apparmor_parser"
[   11.879045] type=1400 audit(1316341046.089:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=334 comm="apparmor_parser"
[   12.120422] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.302137] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   13.832471] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input1
[   15.247633] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.283956] 0000:00:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   15.283980] net eth0: Setting full-duplex based on MII#1 link partner capability of 4de1
[   16.080749] type=1400 audit(1316341050.289:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=624 comm="apparmor_parser"
[   16.083554] type=1400 audit(1316341050.293:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=624 comm="apparmor_parser"
[   16.084141] type=1400 audit(1316341050.293:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=624 comm="apparmor_parser"
[   16.106597] type=1400 audit(1316341050.317:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=627 comm="apparmor_parser"
[   16.107915] type=1400 audit(1316341050.317:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=627 comm="apparmor_parser"
[   16.116982] type=1400 audit(1316341050.325:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=628 comm="apparmor_parser"
[   16.223061] vesafb: framebuffer at 0xf4000000, mapped to 0xf8680000, using 1216k, total 1216k
[   16.223073] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   16.223079] vesafb: scrolling: redraw
[   16.223088] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   16.223573] Console: switching to colour frame buffer device 80x30
[   16.245607] fb0: VESA VGA frame buffer device
[   16.333674] ppdev: user-space parallel port driver
[   16.431647] parport_pc 00:0d: reported by Plug and Play BIOS
[   16.431710] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.526686] lp0: using parport0 (interrupt-driven).
[   16.551798] BUG: unable to handle kernel NULL pointer dereference at 00000004
[   16.552633] IP: [<c110a42e>] copy_pte_range+0x3ce/0x490
[   16.553230] *pdpt = 0000000036aac001 *pde = 0000000000000000 
[   16.553891] Oops: 0000 [#1] SMP 
[   16.554216] last sysfs file: /sys/bus/pci/drivers/parport_pc/uevent
[   16.554216] Modules linked in: parport_pc ppdev vesafb snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device psmouse snd i2c_viapro soundcore serio_raw shpchp lp parport pata_via tulip sata_via
[   16.554216] 
[   16.554216] Pid: 273, comm: udevd Not tainted 2.6.38-11-generic-pae #48-Ubuntu IDOT ID-PCM7E PC2500/ID-PCM7E PC2500
[   16.554216] EIP: 0060:[<c110a42e>] EFLAGS: 00010282 CPU: 0
[   16.554216] EIP is at copy_pte_range+0x3ce/0x490
[   16.554216] EAX: f6509300 EBX: fffb9330 ECX: 75698045 EDX: 00000000
[   16.554216] ESI: 75698045 EDI: 80000000 EBP: f6a73e5c ESP: f6a73dd4
[   16.554216]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   16.554216] Process udevd (pid: 273, ti=f6a72000 task=f75f4bc0 task.ti=f6a72000)
[   16.554216] Stack:
[   16.554216]  75698045 80000000 00000246 c17bafc0 75698045 00000001 f451ca4c f451884c
[   16.554216]  f75f4bc0 79f07000 00000000 79f07000 00000000 fffb9280 7ba74000 00000000
[   16.554216]  7ba74000 00000000 f4518800 fffba280 f2874e38 f659a0ec f65d0e8c f451ca00
[   16.554216] Call Trace:
[   16.554216]  [<c110bd45>] copy_page_range+0x185/0x290
[   16.554216]  [<c1056a6f>] dup_mmap+0x1cf/0x2e0
[   16.554216]  [<c10572fb>] dup_mm+0xab/0x180
[   16.554216]  [<c1057b01>] copy_process+0x701/0xbc0
[   16.554216]  [<c113be3b>] ? putname+0x2b/0x40
[   16.554216]  [<c1058063>] do_fork+0x63/0x2d0
[   16.554216]  [<c10129e4>] sys_clone+0x34/0x40
[   16.554216]  [<c100ac99>] ptregs_clone+0x15/0x3c
[   16.554216]  [<c100ab5f>] ? sysenter_do_call+0x12/0x28
[   16.554216] Code: fe ff ff 8b 5d 10 31 d2 8b 45 d4 89 1c 24 e8 7a e2 ff ff 85 c0 0f 85 69 ff ff ff 8b 75 c8 8b 06 8b 56 04 e9 8c fc ff ff 8b 50 0c <8b> 72 04 3e ff 42 04 e9 54 fe ff ff 83 f8 1f 75 84 8b 45 d8 83 
[   16.554216] EIP: [<c110a42e>] copy_pte_range+0x3ce/0x490 SS:ESP 0068:f6a73dd4
[   16.554216] CR2: 0000000000000004
[   16.743247] ---[ end trace f6f493b80ca63ec4 ]---
[   16.757182] note: udevd[273] exited with preempt_count 2
[   16.771258] BUG: scheduling while atomic: udevd/273/0x10000002
[   16.785394] Modules linked in: parport_pc ppdev vesafb snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device psmouse snd i2c_viapro soundcore serio_raw shpchp lp parport pata_via tulip sata_via
[   16.844456] Pid: 273, comm: udevd Tainted: G      D     2.6.38-11-generic-pae #48-Ubuntu
[   16.874430] Call Trace:
[   16.888862]  [<c1047dd2>] ? __schedule_bug+0x62/0x70
[   16.903299]  [<c1530353>] ? schedule+0x713/0x740
[   16.917361]  [<c1282a14>] ? rb_erase+0xb4/0x120
[   16.930998]  [<c12836e8>] ? timerqueue_del+0x28/0x70
[   16.944299]  [<c107a82f>] ? __remove_hrtimer+0x2f/0x90
[   16.957719] Clocksource tsc unstable (delta = 335969049 ns)
[   16.971255]  [<c1052ecb>] ? __cond_resched+0x1b/0x30
[   16.984869]  [<c1530498>] ? _cond_resched+0x28/0x30
[   16.998621]  [<c1531530>] ? down_read+0x10/0x20
[   17.012403]  [<c109a9df>] ? acct_collect+0x3f/0x170
[   17.026248]  [<c105cfc3>] ? do_exit+0x283/0x350
[   17.040122]  [<c15337c6>] ? oops_end+0x96/0xd0
[   17.054000]  [<c103693c>] ? no_context+0xbc/0xd0
[   17.067922]  [<c1036b35>] ? __bad_area_nosemaphore+0x95/0x140
[   17.082050]  [<c1535900>] ? do_page_fault+0x0/0x490
[   17.095943]  [<c1036bf7>] ? bad_area_nosemaphore+0x17/0x20
[   17.109558]  [<c1535cdb>] ? do_page_fault+0x3db/0x490
[   17.122999]  [<c10f23a9>] ? __alloc_pages_nodemask+0xf9/0x710
[   17.136195]  [<c103cb9c>] ? kmap_atomic_prot+0x4c/0x120
[   17.149161]  [<c1535900>] ? do_page_fault+0x0/0x490
[   17.162045]  [<c1532c6f>] ? error_code+0x67/0x6c
[   17.174757]  [<c110a42e>] ? copy_pte_range+0x3ce/0x490
[   17.187380]  [<c110bd45>] ? copy_page_range+0x185/0x290
[   17.199674]  [<c1056a6f>] ? dup_mmap+0x1cf/0x2e0
[   17.211558]  [<c10572fb>] ? dup_mm+0xab/0x180
[   17.222966]  [<c1057b01>] ? copy_process+0x701/0xbc0
[   17.234053]  [<c113be3b>] ? putname+0x2b/0x40
[   17.244784]  [<c1058063>] ? do_fork+0x63/0x2d0
[   17.255150]  [<c10129e4>] ? sys_clone+0x34/0x40
[   17.265570]  [<c100ac99>] ? ptregs_clone+0x15/0x3c
[   17.275891]  [<c100ab5f>] ? sysenter_do_call+0x12/0x28
[   17.290046] Switching to clocksource pit
[   17.332760] BUG: scheduling while atomic: udevd/273/0x00000002
[   17.335696] Modules linked in: parport_pc ppdev vesafb snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device psmouse snd i2c_viapro soundcore serio_raw shpchp lp parport pata_via tulip sata_via
[   17.350310] Pid: 273, comm: udevd Tainted: G      D     2.6.38-11-generic-pae #48-Ubuntu
[   17.354676] Call Trace:
[   17.358792]  [<c1047dd2>] ? __schedule_bug+0x62/0x70
[   17.363319]  [<c1530353>] ? schedule+0x713/0x740
[   17.367840]  [<c1009951>] ? __switch_to+0xe1/0x190
[   17.372297]  [<c1048dc9>] ? finish_task_switch+0x39/0xc0
[   17.376775]  [<c1531edd>] ? rwsem_down_failed_common+0x9d/0xf0
[   17.381355]  [<c1531f62>] ? rwsem_down_read_failed+0x12/0x14
[   17.385834]  [<c1531f9f>] ? call_rwsem_down_read_failed+0x7/0xc
[   17.386295]  [<c153153c>] ? down_read+0x1c/0x20
[   17.390612]  [<c109a9df>] ? acct_collect+0x3f/0x170
[   17.394937]  [<c105cfc3>] ? do_exit+0x283/0x350
[   17.399223]  [<c15337c6>] ? oops_end+0x96/0xd0
[   17.403384]  [<c103693c>] ? no_context+0xbc/0xd0
[   17.407570]  [<c1036b35>] ? __bad_area_nosemaphore+0x95/0x140
[   17.411897]  [<c1535900>] ? do_page_fault+0x0/0x490
[   17.416350]  [<c1036bf7>] ? bad_area_nosemaphore+0x17/0x20
[   17.420879]  [<c1535cdb>] ? do_page_fault+0x3db/0x490
[   17.425420]  [<c10f23a9>] ? __alloc_pages_nodemask+0xf9/0x710
[   17.430240]  [<c103cb9c>] ? kmap_atomic_prot+0x4c/0x120
[   17.435076]  [<c1535900>] ? do_page_fault+0x0/0x490
[   17.439920]  [<c1532c6f>] ? error_code+0x67/0x6c
[   17.444721]  [<c110a42e>] ? copy_pte_range+0x3ce/0x490
[   17.449489]  [<c110bd45>] ? copy_page_range+0x185/0x290
[   17.454039]  [<c1056a6f>] ? dup_mmap+0x1cf/0x2e0
[   17.454239]  [<c10572fb>] ? dup_mm+0xab/0x180
[   17.461911]  [<c1057b01>] ? copy_process+0x701/0xbc0
[   17.465255]  [<c113be3b>] ? putname+0x2b/0x40
[   17.468159]  [<c1058063>] ? do_fork+0x63/0x2d0
[   17.470700]  [<c10129e4>] ? sys_clone+0x34/0x40
[   17.476918]  [<c100ac99>] ? ptregs_clone+0x15/0x3c
[   17.479219]  [<c100ab5f>] ? sysenter_do_call+0x12/0x28
[   17.554544] type=1400 audit(1316341051.766:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=682 comm="apparmor_parser"
[   17.617740] type=1400 audit(1316341051.826:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=682 comm="apparmor_parser"

```

dmesg.0
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic-pae (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 (Ubuntu 2.6.38-11.48-generic-pae 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: IDOT ID-PCM7E PC2500/ID-PCM7E PC2500, BIOS 6.00 PG 09/26/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7bf00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-EFFFF uncachable
[    0.000000]   F0000-F7FFF write-through
[    0.000000]   F8000-F8FFF uncachable
[    0.000000]   F9000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07C000000 mask FFC000000 uncachable
[    0.000000]   2 base 0E8000000 mask FF8000000 write-combining
[    0.000000]   3 base 07BF00000 mask FFFF00000 write-through
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f39d0] f39d0
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 365dc000 - 372e6000
[    0.000000] 1091MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007bf00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007bf00
[    0.000000] On node 0 totalpages: 507535
[    0.000000] free_area_init_node: node 0, pgdat c17bac40, node_mem_map f565c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2183 pages used for memmap
[    0.000000]   HighMem zone: 277115 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] Intel MultiProcessor Specification v1.1
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: OEM00000
[    0.000000] MPTABLE: Product ID: PROD00000000
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] Processors: 1
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7bf00000 (gap: 7bf00000:82d00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s32320 r0 d20928 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503568
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-11-generic-pae root=/dev/mapper/media-root ro acpi=off noapic nolapic quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10152640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007bf00)
[    0.000000] Memory: 1980460k/2030592k available (5351k kernel code, 49680k reserved, 2597k data, 720k init, 1117192k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539e95 - 0xc17c35c0   (2597 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539e95   (5351 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f7406000 soft=f7408000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.341 MHz processor.
[    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.68 BogoMIPS (lpj=5985364)
[    0.008019] pid_max: default: 32768 minimum: 301
[    0.008077] Security Framework initialized
[    0.008136] AppArmor: AppArmor initialized
[    0.008141] Yama: becoming mindful.
[    0.008292] Mount-cache hash table entries: 512
[    0.008591] Initializing cgroup subsys ns
[    0.008600] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008610] Initializing cgroup subsys cpuacct
[    0.008624] Initializing cgroup subsys memory
[    0.008647] Initializing cgroup subsys devices
[    0.008654] Initializing cgroup subsys freezer
[    0.008661] Initializing cgroup subsys net_cls
[    0.008667] Initializing cgroup subsys blkio
[    0.012799] SMP alternatives: switching to UP code
[    0.040207] Freeing SMP alternatives: 20k freed
[    0.040262] ftrace: allocating 24259 entries in 48 pages
[    0.044185] SMP disabled
[    0.044195] Performance Events: 
[    0.045345] Brought up 1 CPUs
[    0.045355] Total of 1 processors activated (2992.68 BogoMIPS).
[    0.045643] devtmpfs: initialized
[    0.049277] print_constraints: dummy: 
[    0.049328] Time: 19:33:40  Date: 09/17/11
[    0.049434] NET: Registered protocol family 16
[    0.049687] EISA bus registered
[    0.058096] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.058107] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
[    0.058113] PCI: Using configuration type 1 for base access
[    0.060855] bio: create slab <bio-0> at 0
[    0.061096] ACPI: Interpreter disabled.
[    0.061264] vgaarb: loaded
[    0.061740] SCSI subsystem initialized
[    0.061866] libata version 3.00 loaded.
[    0.061989] usbcore: registered new interface driver usbfs
[    0.062023] usbcore: registered new interface driver hub
[    0.062080] usbcore: registered new device driver usb
[    0.062291] PCI: Probing PCI hardware
[    0.062297] PCI: Probing PCI hardware (bus 00)
[    0.062399] pci 0000:00:00.0: [1106:0314] type 0 class 0x000600
[    0.062419] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.062507] pci 0000:00:00.1: [1106:1314] type 0 class 0x000600
[    0.062570] pci 0000:00:00.2: [1106:2314] type 0 class 0x000600
[    0.062633] pci 0000:00:00.3: [1106:3208] type 0 class 0x000600
[    0.062695] pci 0000:00:00.4: [1106:4314] type 0 class 0x000600
[    0.062763] pci 0000:00:00.7: [1106:7314] type 0 class 0x000600
[    0.062829] pci 0000:00:01.0: [1106:b198] type 1 class 0x000604
[    0.062888] pci 0000:00:01.0: supports D1
[    0.062925] pci 0000:00:08.0: [1317:0985] type 0 class 0x000200
[    0.062951] pci 0000:00:08.0: reg 10: [io  0xf200-0xf2ff]
[    0.062968] pci 0000:00:08.0: reg 14: [mem 0xfdfff000-0xfdfff3ff]
[    0.063023] pci 0000:00:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.063050] pci 0000:00:08.0: supports D1 D2
[    0.063057] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.063067] pci 0000:00:08.0: PME# disabled
[    0.063105] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000101
[    0.063131] pci 0000:00:0f.0: reg 10: [io  0xff00-0xff07]
[    0.063147] pci 0000:00:0f.0: reg 14: [io  0xfe00-0xfe03]
[    0.063164] pci 0000:00:0f.0: reg 18: [io  0xfd00-0xfd07]
[    0.063181] pci 0000:00:0f.0: reg 1c: [io  0xfc00-0xfc03]
[    0.063198] pci 0000:00:0f.0: reg 20: [io  0xfb00-0xfb0f]
[    0.063215] pci 0000:00:0f.0: reg 24: [io  0xf400-0xf4ff]
[    0.063276] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.063341] pci 0000:00:0f.1: reg 20: [io  0xfa00-0xfa0f]
[    0.063423] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
[    0.063506] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.063564] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
[    0.063589] pci 0000:00:11.5: reg 10: [io  0xf000-0xf0ff]
[    0.063674] pci 0000:00:11.5: supports D1 D2
[    0.063756] pci 0000:01:00.0: [1106:3344] type 0 class 0x000300
[    0.063780] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf7ffffff pref]
[    0.063795] pci 0000:01:00.0: reg 14: [mem 0xfb000000-0xfbffffff]
[    0.063840] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.063867] pci 0000:01:00.0: supports D1 D2
[    0.063918] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.063928] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.063937] pci 0000:00:01.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.063948] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff pref]
[    0.064817] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.065227] PCI: pci_cache_line_size set to 64 bytes
[    0.065312] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.065320] reserve RAM buffer: 000000007bf00000 - 000000007bffffff 
[    0.065608] NetLabel: Initializing
[    0.065613] NetLabel:  domain hash size = 128
[    0.065618] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.065647] NetLabel:  unlabeled traffic allowed by default
[    0.065775] Switching to clocksource pit
[    0.082940] AppArmor: AppArmor Filesystem Enabled
[    0.082998] pnp: PnP ACPI: disabled
[    0.083007] PnPBIOS: Scanning system for PnP BIOS support...
[    0.083214] PnPBIOS: Found PnP BIOS installation structure at 0xc00faa00
[    0.083222] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xaa30, dseg 0xf0000
[    0.083311] pnp 00:00: [irq 2]
[    0.083318] pnp 00:00: [io  0x0020-0x0021]
[    0.083324] pnp 00:00: [io  0x00a0-0x00a1]
[    0.083382] pnp 00:00: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.083398] pnp 00:01: [dma 4]
[    0.083403] pnp 00:01: [io  0x0000-0x000f]
[    0.083410] pnp 00:01: [io  0x0081-0x0083]
[    0.083416] pnp 00:01: [io  0x0087]
[    0.083421] pnp 00:01: [io  0x0089-0x008b]
[    0.083428] pnp 00:01: [io  0x008f-0x0091]
[    0.083434] pnp 00:01: [io  0x00c0-0x00df]
[    0.083487] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.083500] pnp 00:02: [irq 0]
[    0.083506] pnp 00:02: [io  0x0040-0x0043]
[    0.083552] pnp 00:02: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.083571] pnp 00:03: [irq 8]
[    0.083576] pnp 00:03: [io  0x0070-0x0071]
[    0.083622] pnp 00:03: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.083636] pnp 00:04: [irq 1]
[    0.083642] pnp 00:04: [io  0x0060]
[    0.083647] pnp 00:04: [io  0x0064]
[    0.083693] pnp 00:04: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.083707] pnp 00:05: [io  0x0061]
[    0.083758] pnp 00:05: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.083772] pnp 00:06: [irq 13]
[    0.083778] pnp 00:06: [io  0x00f0-0x00ff]
[    0.083824] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.083840] pnp 00:07: [mem 0x00000000-0x0009ffff]
[    0.083848] pnp 00:07: [mem 0xfffffffffffe0000-0xffffffffffffffff]
[    0.083856] pnp 00:07: [mem 0xfffffffffec00000-0xfffffffffec0ffff]
[    0.083864] pnp 00:07: [mem 0xfffffffffee00000-0xfffffffffee0ffff]
[    0.083871] pnp 00:07: [mem 0x00100000-0x00ffffff]
[    0.083983] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.083993] system 00:07: [mem 0xfffffffffffe0000-0xffffffffffffffff] could not be reserved
[    0.084003] system 00:07: [mem 0xfffffffffec00000-0xfffffffffec0ffff] could not be reserved
[    0.084013] system 00:07: [mem 0xfffffffffee00000-0xfffffffffee0ffff] could not be reserved
[    0.084023] system 00:07: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.084032] system 00:07: Plug and Play BIOS device, IDs PNP0c01 (active)
[    0.084047] pnp 00:08: [mem 0x000f0000-0x000f3fff]
[    0.084054] pnp 00:08: [mem 0x000f4000-0x000f7fff]
[    0.084061] pnp 00:08: [mem 0x000f8000-0x000fffff]
[    0.084067] pnp 00:08: [mem 0x000cfe00-0x000cffff]
[    0.084148] system 00:08: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.084157] system 00:08: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.084166] system 00:08: [mem 0x000f8000-0x000fffff] could not be reserved
[    0.084174] system 00:08: [mem 0x000cfe00-0x000cffff] has been reserved
[    0.084183] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.084198] pnp 00:09: [io  0x04d0-0x04d1]
[    0.084204] pnp 00:09: [io  0x0cf8-0x0cff]
[    0.084251] pnp 00:09: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.084266] pnp 00:0a: [irq 12]
[    0.084325] pnp 00:0a: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.084394] pnp 00:0b: [irq 4]
[    0.084400] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.084474] pnp 00:0b: Plug and Play BIOS device, IDs PNP0501 (active)
[    0.084524] pnp 00:0c: [dma 2]
[    0.084529] pnp 00:0c: [io  0x03f0-0x03f5]
[    0.084535] pnp 00:0c: [io  0x03f7]
[    0.084541] pnp 00:0c: [irq 6]
[    0.084630] pnp 00:0c: Plug and Play BIOS device, IDs PNP0700 (active)
[    0.084705] pnp 00:0d: [irq 7]
[    0.084711] pnp 00:0d: [io  0x0378-0x037f]
[    0.084717] pnp 00:0d: [io  0x0778-0x077f]
[    0.084798] pnp 00:0d: Plug and Play BIOS device, IDs PNP0400 (active)
[    0.084809] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[    0.089437] pci 0000:00:08.0: BAR 6: assigned [mem 0x7c000000-0x7c01ffff pref]
[    0.089454] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc000000-0xfc00ffff pref]
[    0.089463] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.089472] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.089484] pci 0000:00:01.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.089495] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff pref]
[    0.089519] pci 0000:00:01.0: setting latency timer to 64
[    0.089530] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.089537] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.089546] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.089553] pci_bus 0000:01: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.089561] pci_bus 0000:01: resource 2 [mem 0xf4000000-0xf7ffffff pref]
[    0.089676] NET: Registered protocol family 2
[    0.089838] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.090644] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.092435] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.093362] TCP: Hash tables configured (established 131072 bind 65536)
[    0.093371] TCP reno registered
[    0.093384] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.093431] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.093697] NET: Registered protocol family 1
[    0.093758] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.093784] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.093806] pci 0000:01:00.0: Boot video device
[    0.093814] PCI: CLS 64 bytes, default 64
[    0.094105] cpufreq-nforce2: No nForce2 chipset.
[    0.094577] audit: initializing netlink socket (disabled)
[    0.094610] type=2000 audit(1316288019.092:1): initialized
[    0.121941] Trying to unpack rootfs image as initramfs...
[    0.155845] highmem bounce pool size: 64 pages
[    0.155861] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.167051] VFS: Disk quotas dquot_6.5.2
[    0.167264] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.169105] fuse init (API version 7.16)
[    0.169387] msgmni has been set to 1686
[    0.174741] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.174822] io scheduler noop registered
[    0.174827] io scheduler deadline registered
[    0.174876] io scheduler cfq registered (default)
[    0.175204] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.175266] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.179502] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.184021] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.184084] isapnp: Scanning for PnP cards...
[    0.196441] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.251111] Linux agpgart interface v0.103
[    0.251289] agpgart: Detected VIA VT3314 chipset
[    0.267280] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.270680] brd: module loaded
[    0.272276] loop: module loaded
[    0.272615] i2c-core: driver [adp5520] using legacy suspend method
[    0.272621] i2c-core: driver [adp5520] using legacy resume method
[    0.273152] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.273234] pata_acpi 0000:00:0f.1: setting latency timer to 64
[    0.274150] Fixed MDIO Bus: probed
[    0.278396] PPP generic driver version 2.4.2
[    0.278605] tun: Universal TUN/TAP device driver, 1.6
[    0.278611] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.278875] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.278944] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.278979] uhci_hcd: USB Universal Host Controller Interface driver
[    0.279234] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.279703] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.279734] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.280074] mousedev: PS/2 mouse device common for all mice
[    0.280336] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.280391] rtc0: alarms up to one day, 114 bytes nvram
[    0.280641] device-mapper: uevent: version 1.0.3
[    0.280844] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.283469] device-mapper: multipath: version 1.2.0 loaded
[    0.283481] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.283817] EISA: Probing bus 0 at eisa.0
[    0.283881] EISA: Detected 0 cards.
[    0.290674] cpuidle: using governor ladder
[    0.290684] cpuidle: using governor menu
[    0.291522] TCP cubic registered
[    0.291904] NET: Registered protocol family 10
[    0.293295] NET: Registered protocol family 17
[    0.293353] Registering the dns_resolver key type
[    0.293416] longhaul: Use acpi-cpufreq driver for VIA C7
[    0.293430] Using IPI No-Shortcut mode
[    0.293735] PM: Hibernation image not present or could not be loaded.
[    0.293774] registered taskstats version 1
[    0.294121]   Magic number: 11:341:597
[    0.294466] rtc_cmos 00:03: setting system clock to 2011-09-17 19:33:40 UTC (1316288020)
[    0.294476] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.294481] EDD information not available.
[    0.309301] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    0.886070] isapnp: No Plug & Play device found
[    1.118651] Switching to clocksource tsc
[    1.453852] Freeing initrd memory: 13352k freed
[    1.480145] Freeing unused kernel memory: 720k freed
[    1.481678] Write protecting the kernel text: 5352k
[    1.481850] Write protecting the kernel read-only data: 2192k
[    1.481856] NX-protecting the kernel data: 4888k
[    1.564085] <30>udev[57]: starting version 167
[    1.973623] sata_via 0000:00:0f.0: version 2.6
[    1.973732] sata_via 0000:00:0f.0: routed to hard irq line 11
[    2.008821] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.018960] scsi0 : sata_via
[    2.020686] scsi1 : sata_via
[    2.020867] ata1: SATA max UDMA/133 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 11
[    2.020876] ata2: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 11
[    2.022382] pata_via 0000:00:0f.1: version 0.3.4
[    2.026402] scsi2 : pata_via
[    2.028666] scsi3 : pata_via
[    2.028853] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.028862] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.029077] tulip_init_one: Enabled WOL support for AN983B
[    2.029607] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1
[    2.072451] net eth0: ADMtek Comet rev 17 at Port 0xf200, 00:06:25:07:d2:f8, IRQ 10
[    2.206662] ata3.00: ATAPI: LG CD-RW CED-8080B, 1.03, max UDMA/33
[    2.206679] ata3.01: ATAPI: MATSHITADVD-ROM SR-8585, 1W21, max UDMA/33
[    2.222242] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.222587] ata3.00: configured for UDMA/33
[    2.230473] ata3.01: configured for UDMA/33
[    2.400710] ata1.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.400719] ata1.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    2.414982] ata1.00: configured for UDMA/133
[    2.415264] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    2.415759] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.416083] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.416187] sd 0:0:0:0: [sda] Write Protect is off
[    2.416196] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.416240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.422745]  sda: sda1
[    2.423326] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.618265] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.629690] scsi 2:0:0:0: CD-ROM            LG       CD-RW CED-8080B  1.03 PQ: 0 ANSI: 5
[    2.631618] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.631630] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.632000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.632209] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.635226] scsi 2:0:1:0: CD-ROM            MATSHITA DVD-ROM SR-8585  1W21 PQ: 0 ANSI: 5
[    2.636474] sr1: scsi3-mmc drive: 61x/61x cd/rw xa/form2 cdda tray
[    2.636868] sr 2:0:1:0: Attached scsi CD-ROM sr1
[    2.637070] sr 2:0:1:0: Attached scsi generic sg2 type 5
[    2.800196] ata4.00: ATA-7: Maxtor 6L300R0, BAJ41G20, max UDMA/133
[    2.800206] ata4.00: 586114704 sectors, multi 1: LBA48 
[    2.816017] ata4.00: configured for UDMA/133
[    2.816288] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6L300R0   BAJ4 PQ: 0 ANSI: 5
[    2.816774] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.816984] sd 3:0:0:0: [sdb] 586114704 512-byte logical blocks: (300 GB/279 GiB)
[    2.817083] sd 3:0:0:0: [sdb] Write Protect is off
[    2.817092] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.817136] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.840863]  sdb: sdb1 sdb2 < sdb5 >
[    2.841657] sd 3:0:0:0: [sdb] Attached SCSI disk
[    3.569280] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    3.569292] EXT4-fs (dm-0): write access will be enabled during recovery
[    3.774300] EXT4-fs (dm-0): recovery complete
[    3.774806] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   10.679382] <30>udev[255]: starting version 167
[   10.937998] lp: driver loaded but no devices found
[   10.991267] Adding 2027516k swap on /dev/mapper/media-swap_1.  Priority:-1 extents:1 across:2027516k 
[   11.406533] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   11.768767] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.833835] type=1400 audit(1316288032.034:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=334 comm="apparmor_parser"
[   11.853271] type=1400 audit(1316288032.054:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=334 comm="apparmor_parser"
[   11.853841] type=1400 audit(1316288032.054:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=334 comm="apparmor_parser"
[   12.291045] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   14.091865] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input1
[   15.227968] 0000:00:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   15.227992] net eth0: Setting full-duplex based on MII#1 link partner capability of 4de1
[   15.358614] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.919236] type=1400 audit(1316288036.122:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=637 comm="apparmor_parser"
[   15.929732] type=1400 audit(1316288036.130:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=637 comm="apparmor_parser"
[   15.938850] type=1400 audit(1316288036.142:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=637 comm="apparmor_parser"
[   15.989103] type=1400 audit(1316288036.190:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=643 comm="apparmor_parser"
[   16.004678] type=1400 audit(1316288036.206:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=643 comm="apparmor_parser"
[   16.035608] type=1400 audit(1316288036.238:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=650 comm="apparmor_parser"
[   16.238284] vesafb: framebuffer at 0xf4000000, mapped to 0xf8680000, using 1216k, total 1216k
[   16.238296] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   16.238302] vesafb: scrolling: redraw
[   16.238311] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   16.238796] Console: switching to colour frame buffer device 80x30
[   16.260808] fb0: VESA VGA frame buffer device
[   16.363632] ppdev: user-space parallel port driver
[   16.456732] parport_pc 00:0d: reported by Plug and Play BIOS
[   16.456796] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.550748] lp0: using parport0 (interrupt-driven).
[   16.646582] type=1400 audit(1316288036.850:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=708 comm="apparmor_parser"

```

---

### Post by markolonius on 2011-09-18
here is a stack trace on the screen after the kernel panic.  any guidance would be helpful.  also attached is dmesg, kern.log, kern.log.1, and syslogs.  sorry had to zip the logs.


thank you for any help

---

