---
title: "Cannot mount truecrypted 1TB-disk in karmic"
date: 2009-12-13
forum: General Help
---

### Post by MufflonMannenDX on 2009-12-13
Hi all!
I'm having a slight problem with my encrypted disks since I upgraded from Jaunty to Karmic. Background story:
I have 4 disks in my computer, 2x200Gb and 2x1Tb. Three of these disks are completely encrypted with Truecrypt. I had no problems mounting these in Jaunty but now in Karmic I can't seem to be able to mount my large disks.
When I choose to auto-mount devices it finds the small disk but not the large ones. This is a little head-ache of mine that I hope that you guys will be able to alleviate!
Attached is my dmesg and a screenshot of treucrypt and what it reports that it sees.

Worth noting is that the disks were able to mount in Jaunty with no problems at all and they still work in Windows. So I have no idea what the problem is.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: root=UUID=5e90d374-2071-4c04-bbe4-366207a9553e ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  modified: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  modified: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cffb0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cffb0000 page 4k
[    0.000000] kernel direct mapping tables up to cffb0000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000230000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ 12000-14000
[    0.000000] RAMDISK: 37833000 - 37fef3ac
[    0.000000] ACPI: RSDP 00000000000fa010 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cffb0100 0005C (v01 040109 OEMXSDT  20090401 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cffb0290 000F4 (v03 040109 OEMFACP  20090401 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cffb0440 0B167 (v01  P0021 P0021000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffbe000 00040
[    0.000000] ACPI: APIC 00000000cffb0390 0006C (v01 040109 OEMAPIC  20090401 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cffb0400 0003C (v01 040109 OEMMCFG  20090401 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffbe040 00071 (v01 040109 AMI_OEM  20090401 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cffbb5b0 00038 (v01 040109 OEMHPET  20090401 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000cffbb5f0 00110 (v01 040109 OEMOSFR  20090401 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffbb700 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000005dfff] pages 46
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0230000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [0037833000 - 0037fef3ac]          RAMDISK ==> [0037833000 - 0037fef3ac]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3294]              BRK ==> [00019e3000 - 00019e3294]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880028600000-ffff88002f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cffb0
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2096959
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833512 pages, LIFO batch:31
[    0.000000]   Normal zone: 17024 pages used for memmap
[    0.000000]   Normal zone: 1228160 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cffb0000 - 00000000cffbe000
[    0.000000] PM: Registered nosave memory: 00000000cffbe000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028034000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2065496
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=5e90d374-2071-4c04-bbe4-366207a9553e ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 2142000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 8186724k/9175040k available (5313k kernel code, 787204k absent, 201112k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2606.054 MHz processor.
[    0.002155] Console: colour VGA+ 80x25
[    0.002158] console [tty0] enabled
[    0.010000] allocated 83886080 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000]   alloc irq_desc for 24 on node 0
[    0.010000]   alloc kstat_irqs on node 0
[    0.010000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5212.10 BogoMIPS (lpj=26060500)
[    0.010032] Security Framework initialized
[    0.010054] AppArmor: AppArmor initialized
[    0.010566] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.014457] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.016262] Mount-cache hash table entries: 256
[    0.016399] Initializing cgroup subsys ns
[    0.016404] Initializing cgroup subsys cpuacct
[    0.016407] Initializing cgroup subsys memory
[    0.016414] Initializing cgroup subsys freezer
[    0.016416] Initializing cgroup subsys net_cls
[    0.016428] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.016430] CPU: L2 Cache: 512K (64 bytes/line)
[    0.016433] CPU 0/0x0 -> Node 0
[    0.016436] tseg: 0000000000
[    0.016450] CPU: Physical Processor ID: 0
[    0.016452] CPU: Processor Core ID: 0
[    0.016454] mce: CPU supports 6 MCE banks
[    0.016465] using C1E aware idle routine
[    0.016467] Performance Counters: AMD PMU driver.
[    0.016471] ... version:                 0
[    0.016472] ... bit width:               48
[    0.016473] ... generic counters:        4
[    0.016475] ... value mask:              0000ffffffffffff
[    0.016476] ... max period:              00007fffffffffff
[    0.016477] ... fixed-purpose counters:  0
[    0.016479] ... counter mask:            000000000000000f
[    0.018118] ACPI: Core revision 20090521
[    0.038861] Setting APIC routing to flat
[    0.039200] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.139201] CPU0: AMD Phenom(tm) II X4 810 Processor stepping 02
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5213.33 BogoMIPS (lpj=26066674)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.291314] CPU1: AMD Phenom(tm) II X4 810 Processor stepping 02
[    0.291324] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300069] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 5213.33 BogoMIPS (lpj=26066667)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.461240] CPU2: AMD Phenom(tm) II X4 810 Processor stepping 02
[    0.461247] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470069] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 5213.32 BogoMIPS (lpj=26066639)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.631261] CPU3: AMD Phenom(tm) II X4 810 Processor stepping 02
[    0.631275] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640013] Brought up 4 CPUs
[    0.640015] Total of 4 processors activated (20852.09 BogoMIPS).
[    0.640069] CPU0 attaching sched-domain:
[    0.640071]  domain 0: span 0-3 level MC
[    0.640073]   groups: 0 1 2 3
[    0.640078] CPU1 attaching sched-domain:
[    0.640079]  domain 0: span 0-3 level MC
[    0.640081]   groups: 1 2 3 0
[    0.640085] CPU2 attaching sched-domain:
[    0.640086]  domain 0: span 0-3 level MC
[    0.640087]   groups: 2 3 0 1
[    0.640091] CPU3 attaching sched-domain:
[    0.640092]  domain 0: span 0-3 level MC
[    0.640094]   groups: 3 0 1 2
[    0.640171] Booting paravirtualized kernel on bare hardware
[    0.640171] regulator: core version 0.5
[    0.640171] Time: 23:46:46  Date: 12/13/09
[    0.640171] NET: Registered protocol family 16
[    0.640190] node 0 link 0: io port [1000, ffffff]
[    0.640193] TOM: 00000000d0000000 aka 3328M
[    0.640195] Fam 10h mmconf [e0000000, efffffff]
[    0.640198] node 0 link 0: mmio [a0000, bffff]
[    0.640200] node 0 link 0: mmio [d0000000, dfffffff]
[    0.640202] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.640205] node 0 link 0: mmio [f0000000, ffefffff]
[    0.640206] TOM2: 0000000230000000 aka 8960M
[    0.640208] bus: [00,07] on node 0 link 0
[    0.640210] bus: 00 index 0 io port: [0, ffff]
[    0.640212] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640213] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.640215] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.640217] bus: 00 index 4 mmio: [230000000, fcffffffff]
[    0.640243] ACPI: bus type pci registered
[    0.640306] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.640309] PCI: Not using MMCONFIG.
[    0.640310] PCI: Using configuration type 1 for base access
[    0.640312] PCI: Using configuration type 1 for extended access
[    0.640341] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.640342] mtrr: probably your BIOS does not setup all CPUs.
[    0.640343] mtrr: corrected configuration.
[    0.640863] bio: create slab <bio-0> at 0
[    0.640863] ACPI: EC: Look up EC in DSDT
[    0.655113] ACPI: Interpreter enabled
[    0.655116] ACPI: (supports S0 S1 S3 S4 S5)
[    0.655135] ACPI: Using IOAPIC for interrupt routing
[    0.655258] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.659627] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.665918] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.671788] ACPI Warning: Incorrect checksum in table [OEMB] - F0, should be EF 20090521 tbutils-246
[    0.671917] ACPI: No dock devices found.
[    0.672257] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.672384] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.672387] pci 0000:00:02.0: PME# disabled
[    0.672445] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.672447] pci 0000:00:0a.0: PME# disabled
[    0.672506] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.672513] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.672520] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.672527] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.672535] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.672542] pci 0000:00:11.0: reg 24 32bit mmio: [0xf7fff800-0xf7fffbff]
[    0.672562] pci 0000:00:11.0: set SATA to AHCI mode
[    0.672613] pci 0000:00:12.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffefff]
[    0.672675] pci 0000:00:12.1: reg 10 32bit mmio: [0xf7ffd000-0xf7ffdfff]
[    0.672756] pci 0000:00:12.2: reg 10 32bit mmio: [0xf7fff000-0xf7fff0ff]
[    0.672815] pci 0000:00:12.2: supports D1 D2
[    0.672817] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.672821] pci 0000:00:12.2: PME# disabled
[    0.672858] pci 0000:00:13.0: reg 10 32bit mmio: [0xf7ffc000-0xf7ffcfff]
[    0.672919] pci 0000:00:13.1: reg 10 32bit mmio: [0xf7ffb000-0xf7ffbfff]
[    0.673000] pci 0000:00:13.2: reg 10 32bit mmio: [0xf7ffa800-0xf7ffa8ff]
[    0.673060] pci 0000:00:13.2: supports D1 D2
[    0.673061] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.673065] pci 0000:00:13.2: PME# disabled
[    0.673198] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.673205] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.673212] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.673218] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.673225] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.673300] pci 0000:00:14.2: reg 10 64bit mmio: [0xf7ff4000-0xf7ff7fff]
[    0.673348] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.673353] pci 0000:00:14.2: PME# disabled
[    0.673470] pci 0000:00:14.5: reg 10 32bit mmio: [0xf7ff9000-0xf7ff9fff]
[    0.673630] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.673640] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.673649] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.673656] pci 0000:01:00.0: reg 24 io port: [0xd800-0xd87f]
[    0.673661] pci 0000:01:00.0: reg 30 32bit mmio: [0xfce80000-0xfcefffff]
[    0.673748] pci 0000:00:02.0: bridge io port: [0xd000-0xdfff]
[    0.673751] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfcefffff]
[    0.673756] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.673805] pci 0000:02:00.0: reg 10 64bit mmio: [0xfcffc000-0xfcffffff]
[    0.673812] pci 0000:02:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.673834] pci 0000:02:00.0: reg 30 32bit mmio: [0xfcfc0000-0xfcfdffff]
[    0.673868] pci 0000:02:00.0: supports D1 D2
[    0.673869] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.673873] pci 0000:02:00.0: PME# disabled
[    0.673933] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.673936] pci 0000:00:0a.0: bridge 32bit mmio: [0xfcf00000-0xfcffffff]
[    0.674004] pci 0000:03:05.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.674139] pci 0000:03:08.0: reg 10 32bit mmio: [0xfebff000-0xfebfffff]
[    0.674206] pci 0000:03:08.0: supports D1 D2
[    0.674207] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot
[    0.674212] pci 0000:03:08.0: PME# disabled
[    0.674261] pci 0000:00:14.4: transparent bridge
[    0.674268] pci 0000:00:14.4: bridge 32bit mmio: [0xfd000000-0xfebfffff]
[    0.674286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.674446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.674519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.677558] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.677652] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.677744] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.677835] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.677931] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.678026] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.678120] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 11 12 14 15) *0, disabled.
[    0.678215] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.678344] SCSI subsystem initialized
[    0.678381] libata version 3.00 loaded.
[    0.678381] usbcore: registered new interface driver usbfs
[    0.678381] usbcore: registered new interface driver hub
[    0.678381] usbcore: registered new device driver usb
[    0.678381] ACPI: WMI: Mapper loaded
[    0.678381] PCI: Using ACPI for IRQ routing
[    0.700019] Bluetooth: Core ver 2.15
[    0.700054] NET: Registered protocol family 31
[    0.700054] Bluetooth: HCI device and connection manager initialized
[    0.700054] Bluetooth: HCI socket layer initialized
[    0.700054] NetLabel: Initializing
[    0.700054] NetLabel:  domain hash size = 128
[    0.700054] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.700054] NetLabel:  unlabeled traffic allowed by default
[    0.700214] PCI-DMA: Disabling AGP.
[    0.700334] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.700335] PCI-DMA: using GART IOMMU.
[    0.700339] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.702929] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.702936] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.710049] hpet: hpet2 irq 24 for MSI
[    0.740023] Switched to high resolution mode on CPU 0
[    0.741194] Switched to high resolution mode on CPU 2
[    0.741223] Switched to high resolution mode on CPU 3
[    0.741273] Switched to high resolution mode on CPU 1
[    0.760058] pnp: PnP ACPI init
[    0.760080] ACPI: bus type pnp registered
[    0.763721] pnp: PnP ACPI: found 14 devices
[    0.763723] ACPI: ACPI bus type pnp unregistered
[    0.763735] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.763738] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.763743] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.763745] system 00:09: ioport range 0x40b-0x40b has been reserved
[    0.763747] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[    0.763749] system 00:09: ioport range 0xc00-0xc01 has been reserved
[    0.763753] system 00:09: ioport range 0xc14-0xc14 has been reserved
[    0.763755] system 00:09: ioport range 0xc50-0xc51 has been reserved
[    0.763757] system 00:09: ioport range 0xc52-0xc52 has been reserved
[    0.763759] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[    0.763761] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[    0.763763] system 00:09: ioport range 0xcd0-0xcd1 has been reserved
[    0.763765] system 00:09: ioport range 0xcd2-0xcd3 has been reserved
[    0.763767] system 00:09: ioport range 0xcd4-0xcd5 has been reserved
[    0.763770] system 00:09: ioport range 0xcd6-0xcd7 has been reserved
[    0.763772] system 00:09: ioport range 0xcd8-0xcdf has been reserved
[    0.763774] system 00:09: ioport range 0x800-0x89f has been reserved
[    0.763776] system 00:09: ioport range 0xb00-0xb3f has been reserved
[    0.763778] system 00:09: ioport range 0x900-0x90f has been reserved
[    0.763780] system 00:09: ioport range 0x910-0x91f has been reserved
[    0.763782] system 00:09: ioport range 0xfe00-0xfefe has been reserved
[    0.763784] system 00:09: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.763787] system 00:09: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.763794] system 00:0b: ioport range 0xe00-0xe0f has been reserved
[    0.763796] system 00:0b: ioport range 0xe80-0xe8f has been reserved
[    0.763798] system 00:0b: ioport range 0xf40-0xf4f has been reserved
[    0.763800] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.763804] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.763808] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.763810] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.763812] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.763814] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
[    0.763816] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.768491] AppArmor: AppArmor Filesystem Enabled
[    0.768524] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.768526] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.768530] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfcefffff
[    0.768533] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.768538] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.768540] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.768544] pci 0000:00:0a.0:   MEM window: 0xfcf00000-0xfcffffff
[    0.768546] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.768549] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.768551] pci 0000:00:14.4:   IO window: disabled
[    0.768556] pci 0000:00:14.4:   MEM window: 0xfd000000-0xfebfffff
[    0.768560] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.768571]   alloc irq_desc for 18 on node 0
[    0.768573]   alloc kstat_irqs on node 0
[    0.768577] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.768581] pci 0000:00:02.0: setting latency timer to 64
[    0.768587] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.768590] pci 0000:00:0a.0: setting latency timer to 64
[    0.768599] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.768601] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.768604] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.768606] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfcefffff]
[    0.768607] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.768610] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.768612] pci_bus 0000:02: resource 1 mem: [0xfcf00000-0xfcffffff]
[    0.768614] pci_bus 0000:03: resource 1 mem: [0xfd000000-0xfebfffff]
[    0.768615] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.768617] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.768651] NET: Registered protocol family 2
[    0.768849] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.770187] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.773879] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.774331] TCP: Hash tables configured (established 524288 bind 65536)
[    0.774334] TCP reno registered
[    0.774445] NET: Registered protocol family 1
[    0.774507] Trying to unpack rootfs image as initramfs...
[    0.921058] Freeing initrd memory: 7920k freed
[    0.924839] Scanning for low memory corruption every 60 seconds
[    0.924965] audit: initializing netlink socket (disabled)
[    0.924980] type=2000 audit(1260748005.920:1): initialized
[    0.932364] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.933490] VFS: Disk quotas dquot_6.5.2
[    0.933532] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.934021] fuse init (API version 7.12)
[    0.934082] msgmni has been set to 16005
[    0.934363] alg: No test for stdrng (krng)
[    0.934379] io scheduler noop registered
[    0.934381] io scheduler anticipatory registered
[    0.934383] io scheduler deadline registered
[    0.934414] io scheduler cfq registered (default)
[    1.120089] pci 0000:01:00.0: Boot video device
[    1.120313]   alloc irq_desc for 25 on node 0
[    1.120315]   alloc kstat_irqs on node 0
[    1.120324] pcieport-driver 0000:00:02.0: irq 25 for MSI/MSI-X
[    1.120330] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.120459]   alloc irq_desc for 26 on node 0
[    1.120460]   alloc kstat_irqs on node 0
[    1.120465] pcieport-driver 0000:00:0a.0: irq 26 for MSI/MSI-X
[    1.120470] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.120538] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.120556] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.120652] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.120655] ACPI: Power Button [PWRF]
[    1.120702] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.120708] ACPI: Power Button [PWRB]
[    1.120997] processor LNXCPU:00: registered as cooling_device0
[    1.120999] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.121023] processor LNXCPU:01: registered as cooling_device1
[    1.121048] processor LNXCPU:02: registered as cooling_device2
[    1.121071] processor LNXCPU:03: registered as cooling_device3
[    1.123948] Linux agpgart interface v0.103
[    1.123957] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.124087] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.124323] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.124991] brd: module loaded
[    1.125282] loop: module loaded
[    1.125334] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.125473] ahci 0000:00:11.0: version 3.0
[    1.125490]   alloc irq_desc for 22 on node 0
[    1.125491]   alloc kstat_irqs on node 0
[    1.125497] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.125624] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.125627] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.125950] scsi0 : ahci
[    1.126056] scsi1 : ahci
[    1.126103] scsi2 : ahci
[    1.126146] scsi3 : ahci
[    1.126174] ata1: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fff900 irq 22
[    1.126178] ata2: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fff980 irq 22
[    1.126181] ata3: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffa00 irq 22
[    1.126184] ata4: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffa80 irq 22
[    1.126437]   alloc irq_desc for 16 on node 0
[    1.126438]   alloc kstat_irqs on node 0
[    1.126442] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.126469] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.126551] scsi4 : pata_atiixp
[    1.126598] scsi5 : pata_atiixp
[    1.127712] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.127714] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.128143] Fixed MDIO Bus: probed
[    1.128166] PPP generic driver version 2.4.2
[    1.128238] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.128325]   alloc irq_desc for 17 on node 0
[    1.128326]   alloc kstat_irqs on node 0
[    1.128330] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.128348] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.128390] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.128413] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.128433] ehci_hcd 0000:00:12.2: debug port 1
[    1.128449] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf7fff000
[    1.150045] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.150120] usb usb1: configuration #1 chosen from 1 choice
[    1.150147] hub 1-0:1.0: USB hub found
[    1.150154] hub 1-0:1.0: 6 ports detected
[    1.150277]   alloc irq_desc for 19 on node 0
[    1.150279]   alloc kstat_irqs on node 0
[    1.150283] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.150299] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.150324] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.150346] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.150365] ehci_hcd 0000:00:13.2: debug port 1
[    1.150381] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf7ffa800
[    1.170038] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.170105] usb usb2: configuration #1 chosen from 1 choice
[    1.170125] hub 2-0:1.0: USB hub found
[    1.170131] hub 2-0:1.0: 6 ports detected
[    1.170202] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.170265] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.170279] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.170311] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.170338] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf7ffe000
[    1.234113] usb usb3: configuration #1 chosen from 1 choice
[    1.234134] hub 3-0:1.0: USB hub found
[    1.234147] hub 3-0:1.0: 3 ports detected
[    1.234266] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.234281] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.234305] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.234321] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf7ffd000
[    1.294130] usb usb4: configuration #1 chosen from 1 choice
[    1.294150] hub 4-0:1.0: USB hub found
[    1.294163] hub 4-0:1.0: 3 ports detected
[    1.294278] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.294293] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.294317] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.294340] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf7ffc000
[    1.303043] ata5.00: ATAPI: PIONEER DVD-RW  DVR-115D, 1.22, max UDMA/66
[    1.342994] ata5.00: configured for UDMA/66
[    1.343097] ata5.00: TEST_UNIT_READY failed (err_mask=0x2)
[    1.354123] usb usb5: configuration #1 chosen from 1 choice
[    1.354142] hub 5-0:1.0: USB hub found
[    1.354154] hub 5-0:1.0: 3 ports detected
[    1.354267] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.354283] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.354306] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.354325] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf7ffb000
[    1.414110] usb usb6: configuration #1 chosen from 1 choice
[    1.414130] hub 6-0:1.0: USB hub found
[    1.414143] hub 6-0:1.0: 3 ports detected
[    1.414257] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.414272] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.414296] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.414314] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf7ff9000
[    1.474112] usb usb7: configuration #1 chosen from 1 choice
[    1.474131] hub 7-0:1.0: USB hub found
[    1.474144] hub 7-0:1.0: 2 ports detected
[    1.474201] uhci_hcd: USB Universal Host Controller Interface driver
[    1.474277] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.474278] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.474350] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.474406] mice: PS/2 mouse device common for all mice
[    1.474477] rtc_cmos 00:03: RTC can wake from S4
[    1.474503] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.474530] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.474597] device-mapper: uevent: version 1.0.3
[    1.474681] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.474802] device-mapper: multipath: version 1.1.0 loaded
[    1.474805] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.475040] cpuidle: using governor ladder
[    1.475041] cpuidle: using governor menu
[    1.475345] TCP cubic registered
[    1.475435] NET: Registered protocol family 10
[    1.475774] lo: Disabled Privacy Extensions
[    1.475980] NET: Registered protocol family 17
[    1.475996] Bluetooth: L2CAP ver 2.13
[    1.475997] Bluetooth: L2CAP socket layer initialized
[    1.475999] Bluetooth: SCO (Voice Link) ver 0.6
[    1.476001] Bluetooth: SCO socket layer initialized
[    1.476049] Bluetooth: RFCOMM TTY layer initialized
[    1.476052] Bluetooth: RFCOMM socket layer initialized
[    1.476053] Bluetooth: RFCOMM ver 1.11
[    1.476089] powernow-k8: Found 1 AMD Phenom(tm) II X4 810 Processor processors (4 cpu cores) (version 2.20.00)
[    1.476123] powernow-k8:    0 : pstate 0 (2600 MHz)
[    1.476124] powernow-k8:    1 : pstate 1 (1900 MHz)
[    1.476126] powernow-k8:    2 : pstate 2 (1400 MHz)
[    1.476127] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.477978] PM: Resume from disk failed.
[    1.477990] registered taskstats version 1
[    1.478114]   Magic number: 5:690:807
[    1.478164] misc snapshot: hash matches
[    1.478248] rtc_cmos 00:03: setting system clock to 2009-12-13 23:46:47 UTC (1260748007)
[    1.478250] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.478252] EDD information not available.
[    1.494308] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.650053] ata2: softreset failed (device not ready)
[    1.650057] ata2: applying SB600 PMP SRST workaround and retrying
[    1.650077] ata1: softreset failed (device not ready)
[    1.650079] ata1: applying SB600 PMP SRST workaround and retrying
[    1.650096] ata3: softreset failed (device not ready)
[    1.650098] ata3: applying SB600 PMP SRST workaround and retrying
[    1.650115] ata4: softreset failed (device not ready)
[    1.650118] ata4: applying SB600 PMP SRST workaround and retrying
[    1.650143] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    1.830073] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.830103] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.830122] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.830142] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.834271] ata2.00: ATA-6: WDC WD2000JD-00HBB0, 08.02D08, max UDMA/133
[    1.834274] ata2.00: 390721968 sectors, multi 16: LBA48 
[    1.834281] ata1.00: ATA-6: WDC WD2000JD-00HBB0, 08.02D08, max UDMA/133
[    1.834284] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.836422] ata3.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    1.836432] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.836441] ata4.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    1.836444] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.839749] ata2.00: configured for UDMA/133
[    1.839773] ata1.00: configured for UDMA/133
[    1.842854] ata3.00: configured for UDMA/133
[    1.842874] ata4.00: configured for UDMA/133
[    1.853923] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JD-00H 08.0 PQ: 0 ANSI: 5
[    1.854032] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.854062] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.854088] sd 0:0:0:0: [sda] Write Protect is off
[    1.854090] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.854104] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.854194]  sda:
[    1.854260] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2000JD-00H 08.0 PQ: 0 ANSI: 5
[    1.854324] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.854345] sd 1:0:0:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.854366] sd 1:0:0:0: [sdb] Write Protect is off
[    1.854368] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.854379] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.854436]  sdb:
[    1.863874] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.863978] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.864006] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.864032] sd 2:0:0:0: [sdc] Write Protect is off
[    1.864034] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.864047] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.864125]  sdc:
[    1.864232] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.864331] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.864357] sd 3:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.864381] sd 3:0:0:0: [sdd] Write Protect is off
[    1.864383] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.864395] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.864467]  sdd: sdc1
[    1.869023]  sdd1
[    1.869082] sd 2:0:0:0: [sdc] Attached SCSI disk
[    1.869221] sd 3:0:0:0: [sdd] Attached SCSI disk
[    1.871823]  sda1 sda2 sda3
[    1.872027] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.875439]  sdb1
[    1.875611] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.913297] usb 1-5: configuration #1 chosen from 1 choice
[    2.200047] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    2.395514] usb 3-1: configuration #1 chosen from 1 choice
[    2.690046] usb 3-2: new full speed USB device using ohci_hcd and address 3
[    2.896384] usb 3-2: configuration #1 chosen from 1 choice
[    6.500510] ata5.00: configured for UDMA/66
[    6.500617] ata5.00: TEST_UNIT_READY failed (err_mask=0x2)
[    6.500620] ata5.00: limiting speed to UDMA/66:PIO3
[   11.660499] ata5.00: configured for UDMA/66
[   11.660592] ata5.00: TEST_UNIT_READY failed (err_mask=0x2)
[   11.660594] ata5.00: disabled
[   11.660634] ata5: soft resetting link
[   11.820147] ata5: EH complete
[   11.991529] Freeing unused kernel memory: 660k freed
[   11.991756] Write protecting the kernel read-only data: 7580k
[   12.085818] usbcore: registered new interface driver hiddev
[   12.088567] sky2 driver version 1.23
[   12.088684] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.088704] sky2 0000:02:00.0: setting latency timer to 64
[   12.088762] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
[   12.088841]   alloc irq_desc for 27 on node 0
[   12.088843]   alloc kstat_irqs on node 0
[   12.088857] sky2 0000:02:00.0: irq 27 for MSI/MSI-X
[   12.089403] sky2 eth0: addr 00:24:8c:08:6d:13
[   12.103857] input: Microsoft Microsoft IntelliMouse® Explorer as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input4
[   12.103942] generic-usb 0003:045E:0095.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft IntelliMouse® Explorer] on usb-0000:00:12.0-1/input0
[   12.110579] ohci1394 0000:03:08.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.119077] generic-usb 0003:413C:5109.0002: hiddev96,hidraw1: USB HID v1.00 Device [Dell Dell Photo AIO 922] on usb-0000:00:12.0-2/input2
[   12.119098] usbcore: registered new interface driver usbhid
[   12.119101] usbhid: v2.6:USB HID core driver
[   12.172108] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   13.500317] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001b8724d]
[   13.998424] xor: automatically using best checksumming function: generic_sse
[   14.040000]    generic_sse: 10777.600 MB/sec
[   14.040002] xor: using function: generic_sse (10777.600 MB/sec)
[   14.041713] device-mapper: dm-raid45: initialized v0.2594b
[   14.145347] EXT4-fs (sda2): barriers enabled
[   14.154850] kjournald2 starting: pid 522, dev sda2:8, commit interval 5 seconds
[   14.154873] EXT4-fs (sda2): delayed allocation enabled
[   14.154878] EXT4-fs: file extents enabled
[   14.156404] EXT4-fs: mballoc enabled
[   14.156417] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   14.975280] type=1505 audit(1260748020.995:2): operation="profile_load" pid=545 name=/usr/share/gdm/guest-session/Xsession
[   15.006649] type=1505 audit(1260748021.025:3): operation="profile_load" pid=546 name=/sbin/dhclient3
[   15.006870] type=1505 audit(1260748021.025:4): operation="profile_load" pid=546 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.007001] type=1505 audit(1260748021.025:5): operation="profile_load" pid=546 name=/usr/lib/connman/scripts/dhclient-script
[   15.073864] type=1505 audit(1260748021.094:6): operation="profile_load" pid=547 name=/usr/bin/evince
[   15.077506] type=1505 audit(1260748021.094:7): operation="profile_load" pid=547 name=/usr/bin/evince-previewer
[   15.079701] type=1505 audit(1260748021.094:8): operation="profile_load" pid=547 name=/usr/bin/evince-thumbnailer
[   15.099564] type=1505 audit(1260748021.115:9): operation="profile_load" pid=549 name=/usr/lib/cups/backend/cups-pdf
[   15.099828] type=1505 audit(1260748021.115:10): operation="profile_load" pid=549 name=/usr/sbin/cupsd
[   15.112950] type=1505 audit(1260748021.125:11): operation="profile_load" pid=550 name=/usr/sbin/ntpd
[   17.297188] EXT4-fs (sda2): internal journal on sda2:8
[   18.879036] udev: starting version 147
[   21.413205] lp: driver loaded but no devices found
[   21.732480] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.159527] nvidia: module license 'NVIDIA' taints kernel.
[   24.159533] Disabling lock debugging due to kernel taint
[   24.414127] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.414137] nvidia 0000:01:00.0: setting latency timer to 64
[   24.414388] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   24.923159] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   24.923164] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.923186] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[   25.219824] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   25.230987] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x413C pid 0x5109
[   25.231005] usbcore: registered new interface driver usblp
[   25.755177] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   25.755314] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   25.755319] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   25.755322] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   25.755323]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   25.755324]     Might be a BIOS bug, if BIOS says ECC is enabled
[   25.755325]     Use of the override can cause unknown side effects.
[   25.755349] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   26.225116] Linux video capture interface: v2.00
[   26.918286] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   26.936711] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   26.936852]   alloc irq_desc for 20 on node 0
[   26.936848] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input5
[   26.936862]   alloc kstat_irqs on node 0
[   26.936871] cx8800 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   26.936893] usbcore: registered new interface driver uvcvideo
[   26.936896] USB Video Class driver (v0.1.0)
[   26.937306] cx88[0]: subsystem: 107d:6611, board: Leadtek Winfast 2000XP Expert [card=5,autodetected], frontend(s): 0
[   26.937309] cx88[0]: TV tuner type 44, Radio tuner type -1
[   28.974351] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.316581] sky2 eth0: enabling interface
[   29.317752] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.737780] All bytes are equal. It is not a TEA5767
[   29.737838] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   30.009579] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   30.032088] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   30.432055] tda9887 0-0043: creating new instance
[   30.432059] tda9887 0-0043: tda988[5/6/7] found
[   30.493241] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=38, eeprom[0]=0x01
[   30.809494] tuner-simple 0-0060: creating new instance
[   30.809498] tuner-simple 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   30.813473] input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:14.4/0000:03:05.0/input/input7
[   30.813523] cx88[0]/0: found at 0000:03:05.0, rev: 5, irq: 20, latency: 64, mmio: 0xfd000000
[   30.813537] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.813586] cx88[0]/0: registered device video1 [v4l2]
[   30.813611] cx88[0]/0: registered device vbi0
[   30.813635] cx88[0]/0: registered device radio0
[   31.503869] 4:3:1: cannot get freq at ep 0x86
[   32.259399] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   32.260589] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.275287] set volume quirk for QuickCam E3500
[   32.275611] usbcore: registered new interface driver snd-usb-audio
[   36.343572] RPC: Registered udp transport module.
[   36.343575] RPC: Registered tcp transport module.
[   36.932294] svc: failed to register lockdv1 RPC service (errno 97).
[   38.978052] usplash:463 freeing invalid memtype fffffffff9000000-fffffffff9e00000
[   41.518899] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   41.518902] vboxdrv: Successfully done.
[   41.518904] vboxdrv: Found 4 processor cores.
[   41.518968] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d21480
[   41.519059] vboxdrv: fAsync=0 offMin=0x944 offMax=0x7683
[   41.519095] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   41.519097] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   41.800375] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0ec0220
[   41.802340] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa0ed9b20
[   42.573779] eth0: no IPv6 routers present
[   43.706647] ppdev: user-space parallel port driver
[   46.135171] usb 3-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[  102.010589] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  131.091239] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  191.493822] hda-intel: Too big adjustment 32
[  191.744959] hda-intel: Too big adjustment 32
```

If you need any additional information I'll try to fill you to the best of my capabilities!
Thankful for help!
//MufflonMannenDX

---

