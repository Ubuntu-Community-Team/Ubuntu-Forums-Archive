---
title: "Un-Mountable Sony DVD+R/RW DRU540A !?"
date: 2010-01-04
forum: General Help
---

### Post by JKirchartz on 2010-01-04
Hey, I can't get Ubuntu to mount my Sony DRU540A, no matter what I do. Audio CDs, Data CDs and burning are impossible, does anybody have any ideas on how to mount this unmountable drive?

It worked well enough to install Jaunty Jackalope, and I never had any problems using this drive with windows xp, but now that I've upgraded Karmic Koala it doesn't seem to work no matter what I try.

---

### Post by askreet on 2010-01-04
Open a Terminal (Applications > Accessories > Terminal) and provide the output of the following commands, please:

```
dmesg
```
```
ls -l /dev/sd*
```

Place a known good data disc in the drive, wait 10-15 seconds, and get the output of:
```
mount
```
```
cat /proc/mounts
```

This'll help us help you.  =)

- Kyle

---

### Post by JKirchartz on 2010-01-04
dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-protect
[    0.000000]   F0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 0E0000000 mask FFC000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 base 0E0000000 mask FFC000000 write-combining
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37868000 - 37fef1fe
[    0.000000] Allocated new RAMDISK: 008ad000 - 010341fe
[    0.000000] Move RAMDISK from 0000000037868000 - 0000000037fef1fd to 008ad000 - 010341fd
[    0.000000] ACPI: RSDP 000f7730 00014 (v00 KT400 )
[    0.000000] ACPI: RSDT 3fff3000 0002C (v01 KT400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 3fff3040 00074 (v01 KT400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 3fff30c0 03C14 (v01 KT400  AWRDACPI 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3fff0000 00040
[    0.000000] ACPI: APIC 3fff6d00 00054 (v01 KT400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac08a]              BRK ==> [00008a9000 - 00008ac08a]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 00010341fe]      NEW RAMDISK ==> [00008ad000 - 00010341fe]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5c10] f5c10
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1035200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34530 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c183a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
[    0.000000] Kernel command line: root=UUID=54c7e704-28a7-428e-a785-aa06ef004063 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5242240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fff0)
[    0.000000] Memory: 1017932k/1048512k available (4566k kernel code, 29772k reserved, 2142k data, 540k init, 139208k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2166.223 MHz processor.
[    0.000872] Console: colour VGA+ 80x25
[    0.000877] console [tty0] enabled
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 4332.44 BogoMIPS (lpj=8664892)
[    0.004051] Security Framework initialized
[    0.004098] AppArmor: AppArmor initialized
[    0.004108] Mount-cache hash table entries: 512
[    0.004312] Initializing cgroup subsys ns
[    0.004319] Initializing cgroup subsys cpuacct
[    0.004324] Initializing cgroup subsys memory
[    0.004335] Initializing cgroup subsys freezer
[    0.004338] Initializing cgroup subsys net_cls
[    0.004357] CPU: CLK_CTL MSR was 6003d223. Reprogramming to 2003d223
[    0.004362] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004365] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004371] mce: CPU supports 4 MCE banks
[    0.004399] Performance Counters: AMD PMU driver.
[    0.004408] ... version:                 0
[    0.004410] ... bit width:               48
[    0.004412] ... generic counters:        4
[    0.004414] ... value mask:              0000ffffffffffff
[    0.004416] ... max period:              00007fffffffffff
[    0.004419] ... fixed-purpose counters:  0
[    0.004421] ... counter mask:            000000000000000f
[    0.004427] Checking 'hlt' instruction... OK.
[    0.020639] SMP alternatives: switching to UP code
[    0.026576] Freeing SMP alternatives: 19k freed
[    0.026605] ACPI: Core revision 20090521
[    0.035803] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075487] CPU0: AMD Unknown CPU Type stepping 00
[    0.076001] Brought up 1 CPUs
[    0.076001] Total of 1 processors activated (4332.44 BogoMIPS).
[    0.076001] CPU0 attaching NULL sched-domain.
[    0.076001] Booting paravirtualized kernel on bare hardware
[    0.076001] regulator: core version 0.5
[    0.076001] Time: 21:21:44  Date: 01/03/10
[    0.076001] NET: Registered protocol family 16
[    0.076001] EISA bus registered
[    0.076001] ACPI: bus type pci registered
[    0.080373] PCI: PCI BIOS revision 2.10 entry at 0xfb4d0, last bus=1
[    0.080376] PCI: Using configuration type 1 for base access
[    0.081379] bio: create slab <bio-0> at 0
[    0.081925] ACPI: EC: Look up EC in DSDT
[    0.086885] ACPI: Interpreter enabled
[    0.086891] ACPI: (supports S0 S1 S4 S5)
[    0.086914] ACPI: Using IOAPIC for interrupt routing
[    0.090630] ACPI: No dock devices found.
[    0.090734] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.090786] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.090864] pci 0000:00:01.0: supports D1
[    0.090899] pci 0000:00:0a.0: reg 10 io port: [0xb000-0xb01f]
[    0.090934] pci 0000:00:0a.0: supports D1 D2
[    0.090961] pci 0000:00:0a.1: reg 10 io port: [0xb400-0xb407]
[    0.090996] pci 0000:00:0a.1: supports D1 D2
[    0.091033] pci 0000:00:0e.0: reg 10 io port: [0xb800-0xb8ff]
[    0.091070] pci 0000:00:0e.0: supports D1 D2
[    0.091098] pci 0000:00:0f.0: reg 10 io port: [0xbc00-0xbc07]
[    0.091104] pci 0000:00:0f.0: reg 14 io port: [0xc000-0xc003]
[    0.091110] pci 0000:00:0f.0: reg 18 io port: [0xc400-0xc407]
[    0.091116] pci 0000:00:0f.0: reg 1c io port: [0xc800-0xc803]
[    0.091123] pci 0000:00:0f.0: reg 20 io port: [0xcc00-0xccff]
[    0.091132] pci 0000:00:0f.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.091188] pci 0000:00:10.0: reg 20 io port: [0xd000-0xd01f]
[    0.091210] pci 0000:00:10.0: supports D1 D2
[    0.091213] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091217] pci 0000:00:10.0: PME# disabled
[    0.091259] pci 0000:00:10.1: reg 20 io port: [0xd400-0xd41f]
[    0.091280] pci 0000:00:10.1: supports D1 D2
[    0.091283] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091287] pci 0000:00:10.1: PME# disabled
[    0.091328] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]
[    0.091349] pci 0000:00:10.2: supports D1 D2
[    0.091351] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091355] pci 0000:00:10.2: PME# disabled
[    0.091383] pci 0000:00:10.3: reg 10 32bit mmio: [0xe4120000-0xe41200ff]
[    0.091418] pci 0000:00:10.3: supports D1 D2
[    0.091420] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091424] pci 0000:00:10.3: PME# disabled
[    0.091479] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.091487] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    0.091491] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[    0.091546] pci 0000:00:11.1: reg 20 io port: [0xdc00-0xdc0f]
[    0.091602] pci 0000:00:12.0: reg 10 io port: [0xe000-0xe0ff]
[    0.091609] pci 0000:00:12.0: reg 14 32bit mmio: [0xe4121000-0xe41210ff]
[    0.091641] pci 0000:00:12.0: supports D1 D2
[    0.091643] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091648] pci 0000:00:12.0: PME# disabled
[    0.091695] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.091701] pci 0000:01:00.0: reg 14 io port: [0xa000-0xa0ff]
[    0.091707] pci 0000:01:00.0: reg 18 32bit mmio: [0xe4020000-0xe402ffff]
[    0.091721] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.091737] pci 0000:01:00.0: supports D1 D2
[    0.091764] pci 0000:01:00.1: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.091770] pci 0000:01:00.1: reg 14 32bit mmio: [0xe4030000-0xe403ffff]
[    0.091797] pci 0000:01:00.1: supports D1 D2
[    0.091830] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.091835] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe40fffff]
[    0.091839] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.091847] pci_bus 0000:00: on NUMA node 0
[    0.091852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.109403] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.109566] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.109729] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.109893] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.110052] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.110206] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.110380] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.110542] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.110759] SCSI subsystem initialized
[    0.110837] libata version 3.00 loaded.
[    0.110933] usbcore: registered new interface driver usbfs
[    0.110953] usbcore: registered new interface driver hub
[    0.110986] usbcore: registered new device driver usb
[    0.111137] ACPI: WMI: Mapper loaded
[    0.111140] PCI: Using ACPI for IRQ routing
[    0.111295] Bluetooth: Core ver 2.15
[    0.111332] NET: Registered protocol family 31
[    0.111334] Bluetooth: HCI device and connection manager initialized
[    0.111338] Bluetooth: HCI socket layer initialized
[    0.111341] NetLabel: Initializing
[    0.111343] NetLabel:  domain hash size = 128
[    0.111344] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.111363] NetLabel:  unlabeled traffic allowed by default
[    0.114150] pnp: PnP ACPI init
[    0.114186] ACPI: bus type pnp registered
[    0.117185] pnp: PnP ACPI: found 13 devices
[    0.117188] ACPI: ACPI bus type pnp unregistered
[    0.117193] PnPBIOS: Disabled by ACPI PNP
[    0.117208] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[    0.117212] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[    0.117215] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.117219] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.117222] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.117226] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.117229] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.117233] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.117236] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.117240] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.117243] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.117251] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.117255] system 00:02: ioport range 0x800-0x805 has been reserved
[    0.117258] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.151965] AppArmor: AppArmor Filesystem Enabled
[    0.151991] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.151995] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.152011] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe40fffff
[    0.152016] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.152031] pci 0000:00:01.0: setting latency timer to 64
[    0.152039] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.152042] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.152045] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.152048] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe40fffff]
[    0.152051] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.152098] NET: Registered protocol family 2
[    0.152217] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.152754] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.154583] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.155546] TCP: Hash tables configured (established 131072 bind 65536)
[    0.155549] TCP reno registered
[    0.155701] NET: Registered protocol family 1
[    0.155802] Trying to unpack rootfs image as initramfs...
[    0.384868] Freeing initrd memory: 7708k freed
[    0.397572] cpufreq-nforce2: No nForce2 chipset.
[    0.397609] Scanning for low memory corruption every 60 seconds
[    0.397766] audit: initializing netlink socket (disabled)
[    0.397794] type=2000 audit(1262553704.396:1): initialized
[    0.406420] highmem bounce pool size: 64 pages
[    0.406428] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.408008] VFS: Disk quotas dquot_6.5.2
[    0.408082] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.408654] fuse init (API version 7.12)
[    0.408744] msgmni has been set to 1732
[    0.408977] alg: No test for stdrng (krng)
[    0.408992] io scheduler noop registered
[    0.408994] io scheduler anticipatory registered
[    0.408997] io scheduler deadline registered
[    0.409039] io scheduler cfq registered (default)
[    0.409053] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.409124] pci 0000:01:00.0: Boot video device
[    0.409216] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.409248] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.409388] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.409394] ACPI: Power Button [PWRF]
[    0.409451] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.409454] ACPI: Power Button [PWRB]
[    0.409508] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.409514] ACPI: Sleep Button [SLPB]
[    0.409562] fan PNP0C0B:00: registered as cooling_device0
[    0.409567] ACPI: Fan [FAN] (on)
[    0.409821] processor LNXCPU:00: registered as cooling_device1
[    0.411771] thermal LNXTHERM:01: registered as thermal_zone0
[    0.411779] ACPI: Thermal Zone [THRM] (46 C)
[    0.411894] isapnp: Scanning for PnP cards...
[    0.652086] Switched to high resolution mode on CPU 0
[    0.765138] isapnp: No Plug & Play device found
[    0.766301] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.766410] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.766488] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.766738] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.766840] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.767922] brd: module loaded
[    0.768432] loop: module loaded
[    0.768518] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.768900]   alloc irq_desc for 18 on node -1
[    0.768903]   alloc kstat_irqs on node -1
[    0.768913] pata_hpt366 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.768926] pata_hpt366 0000:00:0f.0: PCI INT A disabled
[    0.768948] pata_hpt3x2n 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.772466] pata_hpt37x: bus clock 33MHz, using 66MHz DPLL.
[    0.772945] scsi0 : pata_hpt3x2n
[    0.773093] scsi1 : pata_hpt3x2n
[    0.773128] ata1: PATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xcc00 irq 18
[    0.773132] ata2: PATA max UDMA/133 cmd 0xc400 ctl 0xc800 bmdma 0xcc08 irq 18
[    0.773329] pata_via 0000:00:11.1: version 0.3.4
[    0.773662] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.773665] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.773669]   alloc irq_desc for 20 on node -1
[    0.773671]   alloc kstat_irqs on node -1
[    0.773677] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.774069] scsi2 : pata_via
[    0.774153] scsi3 : pata_via
[    0.776897] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xdc00 irq 14
[    0.776901] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xdc08 irq 15
[    0.777436] Fixed MDIO Bus: probed
[    0.777478] PPP generic driver version 2.4.2
[    0.777632] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.777895] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.777899] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.777902]   alloc irq_desc for 21 on node -1
[    0.777905]   alloc kstat_irqs on node -1
[    0.777910] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.777932] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.778005] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.778083] ehci_hcd 0000:00:10.3: irq 21, io mem 0xe4120000
[    0.788008] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.788108] usb usb1: configuration #1 chosen from 1 choice
[    0.788142] hub 1-0:1.0: USB hub found
[    0.788158] hub 1-0:1.0: 6 ports detected
[    0.788225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.788240] uhci_hcd: USB Universal Host Controller Interface driver
[    0.788303] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.788311] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.788358] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.788378] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d000
[    0.788475] usb usb2: configuration #1 chosen from 1 choice
[    0.788502] hub 2-0:1.0: USB hub found
[    0.788515] hub 2-0:1.0: 2 ports detected
[    0.788578] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.788585] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.788617] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.788636] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d400
[    0.788732] usb usb3: configuration #1 chosen from 1 choice
[    0.788766] hub 3-0:1.0: USB hub found
[    0.788778] hub 3-0:1.0: 2 ports detected
[    0.788826] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.788833] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.788872] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.788892] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    0.789004] usb usb4: configuration #1 chosen from 1 choice
[    0.789036] hub 4-0:1.0: USB hub found
[    0.789047] hub 4-0:1.0: 2 ports detected
[    0.789142] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.789544] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.789552] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.789626] mice: PS/2 mouse device common for all mice
[    0.789736] rtc_cmos 00:04: RTC can wake from S4
[    0.789779] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.789825] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.789906] device-mapper: uevent: version 1.0.3
[    0.790032] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.790131] device-mapper: multipath: version 1.1.0 loaded
[    0.790135] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.790273] EISA: Probing bus 0 at eisa.0
[    0.790290] Cannot allocate resource for EISA slot 4
[    0.790293] Cannot allocate resource for EISA slot 5
[    0.790304] EISA: Detected 0 cards.
[    0.790373] cpuidle: using governor ladder
[    0.790376] cpuidle: using governor menu
[    0.790912] TCP cubic registered
[    0.791072] NET: Registered protocol family 10
[    0.791550] lo: Disabled Privacy Extensions
[    0.791889] NET: Registered protocol family 17
[    0.791910] Bluetooth: L2CAP ver 2.13
[    0.791912] Bluetooth: L2CAP socket layer initialized
[    0.791916] Bluetooth: SCO (Voice Link) ver 0.6
[    0.791918] Bluetooth: SCO socket layer initialized
[    0.791955] Bluetooth: RFCOMM TTY layer initialized
[    0.791959] Bluetooth: RFCOMM socket layer initialized
[    0.791961] Bluetooth: RFCOMM ver 1.11
[    0.791980] powernow-k8: Processor cpuid 6a0 not supported
[    0.792035] Using IPI No-Shortcut mode
[    0.792109] PM: Resume from disk failed.
[    0.792129] registered taskstats version 1
[    0.792259]   Magic number: 10:244:398
[    0.792404] rtc_cmos 00:04: setting system clock to 2010-01-03 21:21:45 UTC (1262553705)
[    0.792409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.792411] EDD information not available.
[    0.816094] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.967504] ata3.00: ATA-4: IBM-DPTA-372730, P78DA30A, max UDMA/66
[    0.967507] ata3.00: 53464320 sectors, multi 16: LBA 
[    0.967741] ata3.01: ATA-7: Maxtor 6Y160L4, YAR41VW0, max UDMA/133
[    0.967744] ata3.01: 320173056 sectors, multi 16: LBA48 
[    1.000658] ata3.00: configured for UDMA/66
[    1.016374] ata3.01: configured for UDMA/133
[    1.095160] scsi 2:0:0:0: Direct-Access     ATA      IBM-DPTA-372730  P78D PQ: 0 ANSI: 5
[    1.095298] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.095368] scsi 2:0:1:0: Direct-Access     ATA      Maxtor 6Y160L4   YAR4 PQ: 0 ANSI: 5
[    1.095472] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    1.095521] sd 2:0:0:0: [sda] 53464320 512-byte logical blocks: (27.3 GB/25.4 GiB)
[    1.095581] sd 2:0:0:0: [sda] Write Protect is off
[    1.095585] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.095615] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.095780]  sda:
[    1.099637] sd 2:0:1:0: [sdb] 320173056 512-byte logical blocks: (163 GB/152 GiB)
[    1.099688] sd 2:0:1:0: [sdb] Write Protect is off
[    1.099692] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.099719] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.099845]  sdb: sda1 sda2 <
[    1.100015] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.101265]  sdb1
[    1.119565]  sda5 >
[    1.119818] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.119912] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.233821] usb 1-1: configuration #1 chosen from 1 choice
[    1.260333] ata4.00: ATAPI: SONY    DVD RW DRU-540A, 1.0a, max UDMA/33
[    1.276213] ata4.00: configured for UDMA/33
[    1.277024] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DRU-540A  1.0a PQ: 0 ANSI: 5
[    1.279268] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.279272] Uniform CD-ROM driver Revision: 3.20
[    1.279356] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.279400] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.279431] Freeing unused kernel memory: 540k freed
[    1.280223] Write protecting the kernel text: 4568k
[    1.280257] Write protecting the kernel read-only data: 1836k
[    1.492945] Linux agpgart interface v0.103
[    1.495799] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[    1.527429] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    1.527571] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.527576] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    1.527934] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    1.527937] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.527944]   alloc irq_desc for 23 on node -1
[    1.527947]   alloc kstat_irqs on node -1
[    1.527956] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.532657] eth0: VIA Rhine II at 0xe4121000, 00:50:2c:06:63:fc, IRQ 23.
[    1.533366] eth0: MII PHY found at address 1, status 0x782d advertising 01e1 Link 45e1.
[    1.535881] Floppy drive(s): fd0 is 1.44M
[    1.561253] FDC 0 is a post-1991 82077
[    1.693450] [drm] Initialized drm 1.1.0 20060810
[    1.739308] [drm] radeon default to kernel modesetting DISABLED.
[    1.739433]   alloc irq_desc for 16 on node -1
[    1.739436]   alloc kstat_irqs on node -1
[    1.739448] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.739747] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.747064] Initializing USB Mass Storage driver...
[    1.747529] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.748063] usbcore: registered new interface driver usb-storage
[    1.748067] USB Mass Storage support registered.
[    1.748432] usb-storage: device found at 2
[    1.748435] usb-storage: waiting for device to settle before scanning
[    2.846530] xor: automatically using best checksumming function: pIII_sse
[    2.864005]    pIII_sse  :  2486.000 MB/sec
[    2.864008] xor: using function: pIII_sse (2486.000 MB/sec)
[    2.867724] device-mapper: dm-raid45: initialized v0.2594b
[    3.166723] PM: Starting manual resume from disk
[    3.166729] PM: Resume from partition 8:5
[    3.166731] PM: Checking hibernation image.
[    3.166932] PM: Resume from disk failed.
[    3.199024] kjournald starting.  Commit interval 5 seconds
[    3.199040] EXT3-fs: mounted filesystem with writeback data mode.
[    4.277697] type=1505 audit(1262553708.983:2): operation="profile_load" pid=380 name=/usr/share/gdm/guest-session/Xsession
[    4.323391] type=1505 audit(1262553709.027:3): operation="profile_load" pid=381 name=/sbin/dhclient3
[    4.323711] type=1505 audit(1262553709.027:4): operation="profile_load" pid=381 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.323891] type=1505 audit(1262553709.027:5): operation="profile_load" pid=381 name=/usr/lib/connman/scripts/dhclient-script
[    4.436255] type=1505 audit(1262553709.143:6): operation="profile_load" pid=382 name=/usr/bin/evince
[    4.442793] type=1505 audit(1262553709.147:7): operation="profile_load" pid=382 name=/usr/bin/evince-previewer
[    4.446624] type=1505 audit(1262553709.151:8): operation="profile_load" pid=382 name=/usr/bin/evince-thumbnailer
[    4.490222] type=1505 audit(1262553709.195:9): operation="profile_load" pid=384 name=/usr/bin/freshclam
[    4.518263] type=1505 audit(1262553709.223:10): operation="profile_load" pid=385 name=/usr/lib/cups/backend/cups-pdf
[    6.748148] usb-storage: device scan complete
[    6.748857] scsi 4:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
[    6.749340] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.749957] sd 4:0:0:0: [sdc] 31588352 512-byte logical blocks: (16.1 GB/15.0 GiB)
[    6.750452] sd 4:0:0:0: [sdc] Write Protect is off
[    6.750456] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
[    6.750459] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.752830] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.752835]  sdc: sdc1
[    6.887837] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.887842] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    9.256117] udev: starting version 147
[    9.261074] Adding 1108444k swap on /dev/sda5.  Priority:-1 extents:1 across:1108444k 
[    9.927465] EXT3 FS on sda1, internal journal
[    9.960782] udev: renamed network interface eth0 to eth1
[   10.755229] lp: driver loaded but no devices found
[   11.246000] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.246043] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.299611] ppdev: user-space parallel port driver
[   11.340313] lp0: using parport0 (interrupt-driven).
[   12.118231] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.231323] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.330562] psmouse serio1: ID: 10 00 64
[   12.478969] gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xb400, speed 1193kHz
[   12.578247] irda_init()
[   12.578293] NET: Registered protocol family 23
[   13.069649] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   15.366439]   alloc irq_desc for 19 on node -1
[   15.366444]   alloc kstat_irqs on node -1
[   15.366455] C-Media PCI 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.810079] EMU10K1_Audigy 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.911986] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   18.249368] __ratelimit: 6 callbacks suppressed
[   18.249374] type=1505 audit(1262553722.955:13): operation="profile_replace" pid=1014 name=/usr/share/gdm/guest-session/Xsession
[   18.251908] type=1505 audit(1262553722.955:14): operation="profile_replace" pid=1015 name=/sbin/dhclient3
[   18.252323] type=1505 audit(1262553722.959:15): operation="profile_replace" pid=1015 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.252503] type=1505 audit(1262553722.959:16): operation="profile_replace" pid=1015 name=/usr/lib/connman/scripts/dhclient-script
[   18.264100] type=1505 audit(1262553722.971:17): operation="profile_replace" pid=1016 name=/usr/bin/evince
[   18.271887] type=1505 audit(1262553722.975:18): operation="profile_replace" pid=1016 name=/usr/bin/evince-previewer
[   18.275944] type=1505 audit(1262553722.979:19): operation="profile_replace" pid=1016 name=/usr/bin/evince-thumbnailer
[   18.283730] type=1505 audit(1262553722.987:20): operation="profile_replace" pid=1018 name=/usr/bin/freshclam
[   18.286737] type=1505 audit(1262553722.991:21): operation="profile_replace" pid=1019 name=/usr/lib/cups/backend/cups-pdf
[   18.287147] type=1505 audit(1262553722.991:22): operation="profile_replace" pid=1019 name=/usr/sbin/cupsd
[   23.895026] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   23.895053] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.895109] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   24.133075] [drm] Setting GART location based on new memory map
[   24.133088] [drm] Loading R200 Microcode
[   24.133126] [drm] writeback test succeeded in 1 usecs
[   27.140023] eth1: no IPv6 routers present
```

dmesg on the DVD-RW drive.
```
[    1.260333] ata4.00: ATAPI: SONY    DVD RW DRU-540A, 1.0a, max UDMA/33
[    1.276213] ata4.00: configured for UDMA/33
[    1.277024] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DRU-540A  1.0a PQ: 0 ANSI: 5
[    1.279268] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.279272] Uniform CD-ROM driver Revision: 3.20
[    1.279356] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.279400] sr 3:0:0:0: Attached scsi generic sg2 type 5
```

ls -l /dev/sd*
```
brw-rw---- 1 root disk 8,  0 2010-01-03 16:21 /dev/sda
brw-rw---- 1 root disk 8,  1 2010-01-03 16:21 /dev/sda1
brw-rw---- 1 root disk 8,  2 2010-01-03 16:21 /dev/sda2
brw-rw---- 1 root disk 8,  5 2010-01-03 16:21 /dev/sda5
brw-rw---- 1 root disk 8, 16 2010-01-03 16:21 /dev/sdb
brw-rw---- 1 root disk 8, 17 2010-01-03 16:21 /dev/sdb1
brw-rw---- 1 root disk 8, 32 2010-01-03 16:21 /dev/sdc
brw-rw---- 1 root disk 8, 33 2010-01-03 16:22 /dev/sdc1
```

mount
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jkirchartz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jkirchartz)
```

cat /proc/mounts
```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev tmpfs rw,relatime,mode=755 0 0
/dev/disk/by-uuid/54c7e704-28a7-428e-a785-aa06ef004063 / ext3 rw,relatime,errors=remount-ro,data=writeback 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/jkirchartz/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
```

---

### Post by askreet on 2010-01-06
What do you see if you run the following command after putting a data CD in the drive?
```
sudo mount /media/cdrom
```

- Kyle

---

### Post by JKirchartz on 2010-01-06
sudo mount dev/cdrom
```
mount: no medium found on /dev/sr0
```

I wonder why the drive is detected & everything, but not being read?

---

