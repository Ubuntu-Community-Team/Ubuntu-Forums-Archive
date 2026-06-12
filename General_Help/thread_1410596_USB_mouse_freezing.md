---
title: "USB mouse freezing"
date: 2010-02-18
forum: General Help
---

### Post by Rayve on 2010-02-18
[LEFT]I know this has been touched on before, but I wondered if anyone has heard anything further on the issue with USB mice (corded) freezing randomly in Karmic?  Sometimes I can go for days without my mouse freezing, and sometimes I get no more than twenty minutes of use before I have to reboot.

While I'm getting very good at keyboard shortcuts, I'd still like to be able to have a functioning mouse.  My lsusb remains the same whether the mouse is working or not, so far the only thing I've noticed is this message, repeatedly, in dmesg:

```
 4: 1: 1: usb_set_interface_failed
```

Anyone have any ideas on a fix for this, or know if one has been implemented?  I thought that changing the kernel might help, but I have two different versions installed (.14 and .19) but I can't get to choose between them (I'm not dual-booting on this machine, it's solely Linux).

Thanks!
[/LEFT]

---

### Post by utnubuuser on 2010-02-19
"esc" to access grub menu at boot


startupmanager can also make selection possible> sudo apt-get install startupmanager

---

### Post by Rayve on 2010-02-22
Thanks for pointing me to startupmanager!  At least now if I find a working kernel, I know how to boot into it.

Anyone know which kernel version currently does *not* have the USB bug?

EDIT: My mouse just froze again recently.  Here is my dmesg output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-generic root=UUID=93551730-a90f-4806-b910-567e9ba3b893 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000009ffa0000 - 000000009ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009ffae000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000250000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x250000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000250000000 aka 9472M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000a0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x9ffa0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009ffa0000 (usable)
[    0.000000]  modified: 000000009ffa0000 - 000000009ffae000 (ACPI data)
[    0.000000]  modified: 000000009ffae000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  modified: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000250000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-000000009ffa0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ffa0000 page 4k
[    0.000000] kernel direct mapping tables up to 9ffa0000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000250000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0240000000 page 1G
[    0.000000]  0240000000 - 0250000000 page 2M
[    0.000000] kernel direct mapping tables up to 250000000 @ 12000-14000
[    0.000000] RAMDISK: 3786f000 - 37feff7d
[    0.000000] ACPI: RSDP 00000000000fb590 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000009ffa0000 00040 (v01 7612MS A7612200 20090928 MSFT 00000097)
[    0.000000] ACPI: FACP 000000009ffa0200 00084 (v01 7612MS A7612200 20090928 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000009ffa0450 08E27 (v01  A7612 A7612200 00000200 INTL 20051117)
[    0.000000] ACPI: FACS 000000009ffae000 00040
[    0.000000] ACPI: APIC 000000009ffa0390 00080 (v01 7612MS A7612200 20090928 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000009ffa0410 0003C (v01 7612MS OEMMCFG  20090928 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000009ffae040 00073 (v01 7612MS A7612200 20090928 MSFT 00000097)
[    0.000000] ACPI: INFO 000000009ffae0c0 00124 (v01 7612MS AMDINFO  20090928 MSFT 00000097)
[    0.000000] ACPI: NVHD 000000009ffae1f0 00284 (v01 7612MS  NVHDCP  20090928 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000009ffaa450 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000250000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000250000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  0000000000061fff] pages 4a
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0250000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786f000 - 0037feff7d]          RAMDISK ==> [003786f000 - 0037feff7d]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3149]              BRK ==> [00019e3000 - 00019e3149]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00081fffff] PMD -> [ffff880028600000-ffff88002f3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00250000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009ffa0
[    0.000000]     0: 0x00100000 -> 0x00250000
[    0.000000] On node 0 totalpages: 2031407
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 636888 pages, LIFO batch:31
[    0.000000]   Normal zone: 18816 pages used for memmap
[    0.000000]   Normal zone: 1357440 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x2008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009ffa0000 - 000000009ffae000
[    0.000000] PM: Registered nosave memory: 000000009ffae000 - 000000009fff0000
[    0.000000] PM: Registered nosave memory: 000000009fff0000 - 00000000a0000000
[    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5ec00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028034000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1998152
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-generic root=UUID=93551730-a90f-4806-b910-567e9ba3b893 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 7928852k/9699328k available (5313k kernel code, 1573700k absent, 196776k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3199.889 MHz processor.
[    0.000011] spurious 8259A interrupt: IRQ7.
[    0.001894] Console: colour VGA+ 80x25
[    0.001896] console [tty0] enabled
[    0.010000] allocated 81264640 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 6399.77 BogoMIPS (lpj=31998850)
[    0.010023] Security Framework initialized
[    0.010036] AppArmor: AppArmor initialized
[    0.010440] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012686] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013681] Mount-cache hash table entries: 256
[    0.013767] Initializing cgroup subsys ns
[    0.013769] Initializing cgroup subsys cpuacct
[    0.013771] Initializing cgroup subsys memory
[    0.013776] Initializing cgroup subsys freezer
[    0.013777] Initializing cgroup subsys net_cls
[    0.013784] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.013786] CPU: L2 Cache: 512K (64 bytes/line)
[    0.013788] CPU 0/0x0 -> Node 0
[    0.013790] tseg: 0000000000
[    0.013799] CPU: Physical Processor ID: 0
[    0.013800] CPU: Processor Core ID: 0
[    0.013802] mce: CPU supports 6 MCE banks
[    0.013809] using C1E aware idle routine
[    0.013810] Performance Counters: AMD PMU driver.
[    0.013813] ... version:                 0
[    0.013814] ... bit width:               48
[    0.013815] ... generic counters:        4
[    0.013816] ... value mask:              0000ffffffffffff
[    0.013817] ... max period:              00007fffffffffff
[    0.013818] ... fixed-purpose counters:  0
[    0.013819] ... counter mask:            000000000000000f
[    0.014933] ACPI: Core revision 20090521
[    0.025248] Setting APIC routing to flat
[    0.025710] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.125730] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6400.24 BogoMIPS (lpj=32001228)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.280822] CPU1: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.280832] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290043] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6400.25 BogoMIPS (lpj=32001295)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.450881] CPU2: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.450890] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.460042] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6400.26 BogoMIPS (lpj=32001328)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.620804] CPU3: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.620813] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.630007] Brought up 4 CPUs
[    0.630009] Total of 4 processors activated (25600.54 BogoMIPS).
[    0.630100] CPU0 attaching sched-domain:
[    0.630102]  domain 0: span 0-3 level MC
[    0.630104]   groups: 0 1 2 3
[    0.630108] CPU1 attaching sched-domain:
[    0.630109]  domain 0: span 0-3 level MC
[    0.630110]   groups: 1 2 3 0
[    0.630113] CPU2 attaching sched-domain:
[    0.630114]  domain 0: span 0-3 level MC
[    0.630115]   groups: 2 3 0 1
[    0.630118] CPU3 attaching sched-domain:
[    0.630119]  domain 0: span 0-3 level MC
[    0.630120]   groups: 3 0 1 2
[    0.630178] Booting paravirtualized kernel on bare hardware
[    0.630178] regulator: core version 0.5
[    0.630178] Time:  8:39:57  Date: 02/22/10
[    0.630178] NET: Registered protocol family 16
[    0.630178] node 0 link 0: io port [1000, ffffff]
[    0.630178] TOM: 00000000b0000000 aka 2816M
[    0.630178] Fam 10h mmconf [e0000000, efffffff]
[    0.630178] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.630178] node 0 link 0: mmio [b0000000, dfffffff]
[    0.630178] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.630180] node 0 link 0: mmio [a0000, bffff]
[    0.630182] TOM2: 0000000250000000 aka 9472M
[    0.630183] bus: [00,07] on node 0 link 0
[    0.630185] bus: 00 index 0 io port: [0, ffff]
[    0.630186] bus: 00 index 1 mmio: [b0000000, dfffffff]
[    0.630187] bus: 00 index 2 mmio: [f0000000, ffffffff]
[    0.630189] bus: 00 index 3 mmio: [a0000, bffff]
[    0.630190] bus: 00 index 4 mmio: [250000000, fcffffffff]
[    0.630197] ACPI: bus type pci registered
[    0.630246] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.630247] PCI: Not using MMCONFIG.
[    0.630249] PCI: Using configuration type 1 for base access
[    0.630250] PCI: Using configuration type 1 for extended access
[    0.630685] bio: create slab <bio-0> at 0
[    0.630685] ACPI: EC: Look up EC in DSDT
[    0.643712] ACPI: Interpreter enabled
[    0.643714] ACPI: (supports S0 S1 S3 S4 S5)
[    0.643727] ACPI: Using IOAPIC for interrupt routing
[    0.643768] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.648429] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.653966] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.663651] ACPI Warning: Incorrect checksum in table [OEMB] - 18, should be 17 20090521 tbutils-246
[    0.663825] ACPI: No dock devices found.
[    0.664165] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.664409] pci 0000:00:01.0: reg 10 io port: [0x2f00-0x2fff]
[    0.664445] pci 0000:00:01.1: reg 10 io port: [0x2900-0x293f]
[    0.664454] pci 0000:00:01.1: reg 20 io port: [0x2d00-0x2d3f]
[    0.664457] pci 0000:00:01.1: reg 24 io port: [0x2e00-0x2e3f]
[    0.664475] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.664480] pci 0000:00:01.1: PME# disabled
[    0.664531] pci 0000:00:01.3: reg 10 32bit mmio: [0xf4d80000-0xf4dfffff]
[    0.664650] pci 0000:00:02.0: reg 10 32bit mmio: [0xf4d7f000-0xf4d7ffff]
[    0.664671] pci 0000:00:02.0: supports D1 D2
[    0.664672] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664674] pci 0000:00:02.0: PME# disabled
[    0.664694] pci 0000:00:02.1: reg 10 32bit mmio: [0xf4d7ec00-0xf4d7ecff]
[    0.664719] pci 0000:00:02.1: supports D1 D2
[    0.664720] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664722] pci 0000:00:02.1: PME# disabled
[    0.664745] pci 0000:00:04.0: reg 10 32bit mmio: [0xf4d7d000-0xf4d7dfff]
[    0.664765] pci 0000:00:04.0: supports D1 D2
[    0.664767] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664769] pci 0000:00:04.0: PME# disabled
[    0.664790] pci 0000:00:04.1: reg 10 32bit mmio: [0xf4d7e800-0xf4d7e8ff]
[    0.664814] pci 0000:00:04.1: supports D1 D2
[    0.664815] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664818] pci 0000:00:04.1: PME# disabled
[    0.664848] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.664875] pci 0000:00:07.0: reg 10 32bit mmio: [0xf4d78000-0xf4d7bfff]
[    0.664896] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.664898] pci 0000:00:07.0: PME# disabled
[    0.664942] pci 0000:00:09.0: reg 10 io port: [0xa080-0xa087]
[    0.664945] pci 0000:00:09.0: reg 14 io port: [0xa000-0xa003]
[    0.664948] pci 0000:00:09.0: reg 18 io port: [0x9c00-0x9c07]
[    0.664950] pci 0000:00:09.0: reg 1c io port: [0x9880-0x9883]
[    0.664953] pci 0000:00:09.0: reg 20 io port: [0x9800-0x980f]
[    0.664956] pci 0000:00:09.0: reg 24 32bit mmio: [0xf4d76000-0xf4d77fff]
[    0.664989] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf4d7c000-0xf4d7cfff]
[    0.664992] pci 0000:00:0a.0: reg 14 io port: [0x9480-0x9487]
[    0.664994] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf4d7e400-0xf4d7e4ff]
[    0.664997] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf4d7e000-0xf4d7e00f]
[    0.665015] pci 0000:00:0a.0: supports D1 D2
[    0.665016] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665019] pci 0000:00:0a.0: PME# disabled
[    0.665045] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665047] pci 0000:00:0b.0: PME# disabled
[    0.665250] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665256] pci 0000:00:10.0: PME# disabled
[    0.665491] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665498] pci 0000:00:13.0: PME# disabled
[    0.665731] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665737] pci 0000:00:14.0: PME# disabled
[    0.665857] pci 0000:01:09.0: reg 10 32bit mmio: [0xf4eff800-0xf4efffff]
[    0.665862] pci 0000:01:09.0: reg 14 io port: [0xbc00-0xbc7f]
[    0.665892] pci 0000:01:09.0: supports D2
[    0.665893] pci 0000:01:09.0: PME# supported from D2 D3hot D3cold
[    0.665896] pci 0000:01:09.0: PME# disabled
[    0.665919] pci 0000:00:08.0: transparent bridge
[    0.665922] pci 0000:00:08.0: bridge io port: [0xb000-0xbfff]
[    0.665924] pci 0000:00:08.0: bridge 32bit mmio: [0xf4e00000-0xf4efffff]
[    0.665940] pci 0000:02:00.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.665944] pci 0000:02:00.0: reg 14 64bit mmio: [0xb8000000-0xbfffffff]
[    0.665948] pci 0000:02:00.0: reg 1c 64bit mmio: [0xb6000000-0xb7ffffff]
[    0.665951] pci 0000:02:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.665954] pci 0000:02:00.0: reg 30 32bit mmio: [0xf4fe0000-0xf4ffffff]
[    0.665977] pci 0000:00:0b.0: bridge io port: [0xc000-0xcfff]
[    0.665979] pci 0000:00:0b.0: bridge 32bit mmio: [0xf4f00000-0xf5ffffff]
[    0.665982] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xb6000000-0xbfffffff]
[    0.666018] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.666021] pci 0000:03:00.0: PME# disabled
[    0.666065] pci 0000:00:10.0: bridge io port: [0xd000-0xefff]
[    0.666072] pci 0000:00:10.0: bridge 32bit mmio: [0xf6000000-0xfdffffff]
[    0.666085] pci 0000:00:10.0: bridge 64bit mmio pref: [0xc0000000-0xdfffffff]
[    0.666113] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.666115] pci 0000:04:00.0: PME# disabled
[    0.666146] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold
[    0.666148] pci 0000:04:02.0: PME# disabled
[    0.666170] pci 0000:03:00.0: bridge io port: [0xd000-0xefff]
[    0.666172] pci 0000:03:00.0: bridge 32bit mmio: [0xf6000000-0xfdffffff]
[    0.666176] pci 0000:03:00.0: bridge 64bit mmio pref: [0xc0000000-0xdfffffff]
[    0.666211] pci 0000:05:00.0: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.666222] pci 0000:05:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.666232] pci 0000:05:00.0: reg 1c 64bit mmio: [0xf6000000-0xf7ffffff]
[    0.666239] pci 0000:05:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.666245] pci 0000:05:00.0: reg 30 32bit mmio: [0xf8fe0000-0xf8ffffff]
[    0.666307] pci 0000:04:00.0: bridge io port: [0xd000-0xdfff]
[    0.666309] pci 0000:04:00.0: bridge 32bit mmio: [0xf6000000-0xf9ffffff]
[    0.666313] pci 0000:04:00.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.666339] pci 0000:06:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.666347] pci 0000:06:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.666355] pci 0000:06:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.666359] pci 0000:06:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.666364] pci 0000:06:00.0: reg 30 32bit mmio: [0xfcfe0000-0xfcffffff]
[    0.666412] pci 0000:04:02.0: bridge io port: [0xe000-0xefff]
[    0.666415] pci 0000:04:02.0: bridge 32bit mmio: [0xfa000000-0xfdffffff]
[    0.666418] pci 0000:04:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.666603] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.666788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.666859] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.666904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.666952] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.666995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.679713] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.679896] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.680079] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.680262] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10
[    0.680446] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.680626] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.680811] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *11
[    0.680999] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.681180] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.681361] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.681541] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.681721] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.681903] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.682084] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.682265] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.682445] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.682630] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.682810] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.682991] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.683171] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.683355] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *15
[    0.683536] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.683717] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.683898] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.684082] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.684265] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.684445] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.684626] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.684807] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.684987] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.685168] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.685348] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.685529] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.685709] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.685890] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.686071] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.686256] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[    0.686439] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.686623] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *15
[    0.686805] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.686989] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.687172] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *7
[    0.687357] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.687540] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.687750] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.687934] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *10
[    0.688118] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.688221] SCSI subsystem initialized
[    0.688243] libata version 3.00 loaded.
[    0.688243] usbcore: registered new interface driver usbfs
[    0.688243] usbcore: registered new interface driver hub
[    0.688243] usbcore: registered new device driver usb
[    0.688243] ACPI: WMI: Mapper loaded
[    0.688243] PCI: Using ACPI for IRQ routing
[    0.710012] Bluetooth: Core ver 2.15
[    0.710030] NET: Registered protocol family 31
[    0.710030] Bluetooth: HCI device and connection manager initialized
[    0.710030] Bluetooth: HCI socket layer initialized
[    0.710030] NetLabel: Initializing
[    0.710030] NetLabel:  domain hash size = 128
[    0.710030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.710030] NetLabel:  unlabeled traffic allowed by default
[    0.710271] PCI-DMA: Disabling AGP.
[    0.710336] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.710337] PCI-DMA: using GART IOMMU.
[    0.710339] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.740024] pnp: PnP ACPI init
[    0.740039] ACPI: bus type pnp registered
[    0.744695] pnp: PnP ACPI: found 12 devices
[    0.744696] ACPI: ACPI bus type pnp unregistered
[    0.744704] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.744706] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.744708] system 00:05: ioport range 0x2000-0x207f has been reserved
[    0.744710] system 00:05: ioport range 0x2080-0x20ff has been reserved
[    0.744711] system 00:05: ioport range 0x2400-0x247f has been reserved
[    0.744714] system 00:05: ioport range 0x2480-0x24ff has been reserved
[    0.744716] system 00:05: ioport range 0x2800-0x287f has been reserved
[    0.744717] system 00:05: ioport range 0x2880-0x28ff has been reserved
[    0.744720] system 00:05: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.744722] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.744725] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.744727] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.744730] system 00:09: ioport range 0xa00-0xadf has been reserved
[    0.744731] system 00:09: ioport range 0xae0-0xaef has been reserved
[    0.744734] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.744737] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.744739] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.744740] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.744742] system 00:0b: iomem range 0x100000-0xafffffff could not be reserved
[    0.744744] system 00:0b: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.749370] AppArmor: AppArmor Filesystem Enabled
[    0.749449] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.749451] pci 0000:00:08.0:   IO window: 0xb000-0xbfff
[    0.749453] pci 0000:00:08.0:   MEM window: 0xf4e00000-0xf4efffff
[    0.749456] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.749458] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.749460] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
[    0.749462] pci 0000:00:0b.0:   MEM window: 0xf4f00000-0xf5ffffff
[    0.749464] pci 0000:00:0b.0:   PREFETCH window: 0x000000b6000000-0x000000bfffffff
[    0.749467] pci 0000:04:00.0: PCI bridge, secondary bus 0000:05
[    0.749469] pci 0000:04:00.0:   IO window: 0xd000-0xdfff
[    0.749472] pci 0000:04:00.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.749475] pci 0000:04:00.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.749478] pci 0000:04:02.0: PCI bridge, secondary bus 0000:06
[    0.749480] pci 0000:04:02.0:   IO window: 0xe000-0xefff
[    0.749483] pci 0000:04:02.0:   MEM window: 0xfa000000-0xfdffffff
[    0.749486] pci 0000:04:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.749489] pci 0000:03:00.0: PCI bridge, secondary bus 0000:04
[    0.749491] pci 0000:03:00.0:   IO window: 0xd000-0xefff
[    0.749494] pci 0000:03:00.0:   MEM window: 0xf6000000-0xfdffffff
[    0.749497] pci 0000:03:00.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
[    0.749500] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.749504] pci 0000:00:10.0:   IO window: 0xd000-0xefff
[    0.749513] pci 0000:00:10.0:   MEM window: 0xf6000000-0xfdffffff
[    0.749519] pci 0000:00:10.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
[    0.749531] pci 0000:00:13.0: PCI bridge, secondary bus 0000:07
[    0.749532] pci 0000:00:13.0:   IO window: disabled
[    0.749541] pci 0000:00:13.0:   MEM window: disabled
[    0.749547] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.749553] pci 0000:00:14.0: PCI bridge, secondary bus 0000:08
[    0.749554] pci 0000:00:14.0:   IO window: disabled
[    0.749563] pci 0000:00:14.0:   MEM window: disabled
[    0.749569] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.749579] pci 0000:00:08.0: setting latency timer to 64
[    0.749583] pci 0000:00:0b.0: setting latency timer to 64
[    0.749851] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.749854]   alloc irq_desc for 19 on node 0
[    0.749855]   alloc kstat_irqs on node 0
[    0.749862] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.749869] pci 0000:00:10.0: setting latency timer to 64
[    0.749875] pci 0000:03:00.0: setting latency timer to 64
[    0.749880] pci 0000:04:00.0: setting latency timer to 64
[    0.749885] pci 0000:04:02.0: setting latency timer to 64
[    0.750148] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 18
[    0.750149]   alloc irq_desc for 18 on node 0
[    0.750150]   alloc kstat_irqs on node 0
[    0.750155] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 18 (level, low) -> IRQ 18
[    0.750163] pci 0000:00:13.0: setting latency timer to 64
[    0.750421] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 17
[    0.750422]   alloc irq_desc for 17 on node 0
[    0.750423]   alloc kstat_irqs on node 0
[    0.750429] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 17 (level, low) -> IRQ 17
[    0.750436] pci 0000:00:14.0: setting latency timer to 64
[    0.750441] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.750443] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.750444] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.750446] pci_bus 0000:01: resource 1 mem: [0xf4e00000-0xf4efffff]
[    0.750447] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.750449] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.750450] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.750452] pci_bus 0000:02: resource 1 mem: [0xf4f00000-0xf5ffffff]
[    0.750453] pci_bus 0000:02: resource 2 pref mem [0xb6000000-0xbfffffff]
[    0.750455] pci_bus 0000:03: resource 0 io:  [0xd000-0xefff]
[    0.750456] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xfdffffff]
[    0.750458] pci_bus 0000:03: resource 2 pref mem [0xc0000000-0xdfffffff]
[    0.750459] pci_bus 0000:04: resource 0 io:  [0xd000-0xefff]
[    0.750461] pci_bus 0000:04: resource 1 mem: [0xf6000000-0xfdffffff]
[    0.750462] pci_bus 0000:04: resource 2 pref mem [0xc0000000-0xdfffffff]
[    0.750464] pci_bus 0000:05: resource 0 io:  [0xd000-0xdfff]
[    0.750465] pci_bus 0000:05: resource 1 mem: [0xf6000000-0xf9ffffff]
[    0.750467] pci_bus 0000:05: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.750468] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.750470] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfdffffff]
[    0.750471] pci_bus 0000:06: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.750495] NET: Registered protocol family 2
[    0.750649] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.751508] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.753511] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.753769] TCP: Hash tables configured (established 524288 bind 65536)
[    0.753770] TCP reno registered
[    0.753833] NET: Registered protocol family 1
[    0.753873] Trying to unpack rootfs image as initramfs...
[    0.866841] Freeing initrd memory: 7683k freed
[    0.868820] Scanning for low memory corruption every 60 seconds
[    0.868903] audit: initializing netlink socket (disabled)
[    0.868912] type=2000 audit(1266827996.860:1): initialized
[    0.874748] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.875614] VFS: Disk quotas dquot_6.5.2
[    0.875647] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.876007] fuse init (API version 7.12)
[    0.876053] msgmni has been set to 15501
[    0.876228] alg: No test for stdrng (krng)
[    0.876237] io scheduler noop registered
[    0.876238] io scheduler anticipatory registered
[    0.876240] io scheduler deadline registered
[    0.876265] io scheduler cfq registered (default)
[    0.910172] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.910271] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.910375] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    0.910478] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.910678] pci 0000:05:00.0: Boot video device
[    0.911089]   alloc irq_desc for 24 on node 0
[    0.911090]   alloc kstat_irqs on node 0
[    0.911107] pcieport-driver 0000:00:10.0: irq 24 for MSI/MSI-X
[    0.911125] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    0.911506]   alloc irq_desc for 25 on node 0
[    0.911507]   alloc kstat_irqs on node 0
[    0.911522] pcieport-driver 0000:00:13.0: irq 25 for MSI/MSI-X
[    0.911540] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    0.911902]   alloc irq_desc for 26 on node 0
[    0.911903]   alloc kstat_irqs on node 0
[    0.911918] pcieport-driver 0000:00:14.0: irq 26 for MSI/MSI-X
[    0.911935] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    0.912186] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.912201] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.912277] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.912279] ACPI: Power Button [PWRF]
[    0.912315] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.912320] ACPI: Power Button [PWRB]
[    0.912555] processor LNXCPU:00: registered as cooling_device0
[    0.912575] processor LNXCPU:01: registered as cooling_device1
[    0.912593] processor LNXCPU:02: registered as cooling_device2
[    0.912611] processor LNXCPU:03: registered as cooling_device3
[    0.917267] Linux agpgart interface v0.103
[    0.917272] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.917356] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.917516] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.918026] brd: module loaded
[    0.918242] loop: module loaded
[    0.918280] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.918364] ahci 0000:00:09.0: version 3.0
[    0.918644] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.918647]   alloc irq_desc for 23 on node 0
[    0.918648]   alloc kstat_irqs on node 0
[    0.918655] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.918684]   alloc irq_desc for 27 on node 0
[    0.918685]   alloc kstat_irqs on node 0
[    0.918689] ahci 0000:00:09.0: irq 27 for MSI/MSI-X
[    0.918734] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    0.918736] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    0.918738] ahci 0000:00:09.0: setting latency timer to 64
[    0.918988] scsi0 : ahci
[    0.919042] scsi1 : ahci
[    0.919074] scsi2 : ahci
[    0.919104] scsi3 : ahci
[    0.919134] scsi4 : ahci
[    0.919164] scsi5 : ahci
[    0.919233] ata1: SATA max UDMA/133 abar m8192@0xf4d76000 port 0xf4d76100 irq 27
[    0.919235] ata2: SATA max UDMA/133 abar m8192@0xf4d76000 port 0xf4d76180 irq 27
[    0.919236] ata3: SATA max UDMA/133 abar m8192@0xf4d76000 port 0xf4d76200 irq 27
[    0.919238] ata4: SATA max UDMA/133 abar m8192@0xf4d76000 port 0xf4d76280 irq 27
[    0.919240] ata5: SATA max UDMA/133 abar m8192@0xf4d76000 port 0xf4d76300 irq 27
[    0.919242] ata6: SATA max UDMA/133 abar m8192@0xf4d76000 port 0xf4d76380 irq 27
[    0.919417] pata_amd 0000:00:06.0: version 0.4.1
[    0.919438] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.919501] scsi6 : pata_amd
[    0.919543] scsi7 : pata_amd
[    0.920308] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.920309] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.920676] Fixed MDIO Bus: probed
[    0.920694] PPP generic driver version 2.4.2
[    0.920745] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.921054] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.921056]   alloc irq_desc for 22 on node 0
[    0.921057]   alloc kstat_irqs on node 0
[    0.921064] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    0.921072] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.921074] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.921100] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.921121] ehci_hcd 0000:00:02.1: debug port 1
[    0.921124] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.921138] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf4d7ec00
[    0.940021] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.940073] usb usb1: configuration #1 chosen from 1 choice
[    0.940090] hub 1-0:1.0: USB hub found
[    0.940095] hub 1-0:1.0: 6 ports detected
[    0.940427] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    0.940429]   alloc irq_desc for 21 on node 0
[    0.940430]   alloc kstat_irqs on node 0
[    0.940436] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    0.940444] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.940446] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.940464] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.940482] ehci_hcd 0000:00:04.1: debug port 1
[    0.940485] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.940500] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf4d7e800
[    0.960022] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.960068] usb usb2: configuration #1 chosen from 1 choice
[    0.960083] hub 2-0:1.0: USB hub found
[    0.960087] hub 2-0:1.0: 6 ports detected
[    0.960128] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.960425] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.960427]   alloc irq_desc for 20 on node 0
[    0.960428]   alloc kstat_irqs on node 0
[    0.960434] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.960442] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.960444] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.960462] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.960482] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf4d7f000
[    1.022071] usb usb3: configuration #1 chosen from 1 choice
[    1.022088] hub 3-0:1.0: USB hub found
[    1.022093] hub 3-0:1.0: 6 ports detected
[    1.022416] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    1.022418] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    1.022427] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.022428] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.022446] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.022465] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf4d7d000
[    1.082076] usb usb4: configuration #1 chosen from 1 choice
[    1.082090] hub 4-0:1.0: USB hub found
[    1.082095] hub 4-0:1.0: 6 ports detected
[    1.082136] uhci_hcd: USB Universal Host Controller Interface driver
[    1.082187] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.082189] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.082255] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.082295] mice: PS/2 mouse device common for all mice
[    1.082352] rtc_cmos 00:06: RTC can wake from S4
[    1.082376] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.082422] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.082475] device-mapper: uevent: version 1.0.3
[    1.082524] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.082592] device-mapper: multipath: version 1.1.0 loaded
[    1.082594] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.082734] cpuidle: using governor ladder
[    1.082735] cpuidle: using governor menu
[    1.082972] TCP cubic registered
[    1.083040] NET: Registered protocol family 10
[    1.083296] lo: Disabled Privacy Extensions
[    1.083462] NET: Registered protocol family 17
[    1.083472] Bluetooth: L2CAP ver 2.13
[    1.083473] Bluetooth: L2CAP socket layer initialized
[    1.083475] Bluetooth: SCO (Voice Link) ver 0.6
[    1.083476] Bluetooth: SCO socket layer initialized
[    1.083503] Bluetooth: RFCOMM TTY layer initialized
[    1.083505] Bluetooth: RFCOMM socket layer initialized
[    1.083506] Bluetooth: RFCOMM ver 1.11
[    1.083529] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor processors (4 cpu cores) (version 2.20.00)
[    1.083551] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.083552] powernow-k8:    1 : pstate 1 (2500 MHz)
[    1.083553] powernow-k8:    2 : pstate 2 (2100 MHz)
[    1.083554] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.083804] PM: Resume from disk failed.
[    1.083810] registered taskstats version 1
[    1.083904]   Magic number: 14:606:675
[    1.083936] vtconsole vtcon0: hash matches
[    1.083993] rtc_cmos 00:06: setting system clock to 2010-02-22 08:39:57 UTC (1266827997)
[    1.083995] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.083996] EDD information not available.
[    1.099503] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.101219] ata7.00: ATAPI: OPTIARC DVD-ROM DDU1678A, 1.00, max UDMA/33
[    1.101235] ata7: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)
[    1.141166] ata7.00: configured for UDMA/33
[    1.240865] Switched to high resolution mode on CPU 3
[    1.240880] Switched to high resolution mode on CPU 1
[    1.240939] Switched to high resolution mode on CPU 2
[    1.250038] Switched to high resolution mode on CPU 0
[    1.260025] ata6: SATA link down (SStatus 0 SControl 300)
[    1.260043] ata5: SATA link down (SStatus 0 SControl 300)
[    1.260056] ata4: SATA link down (SStatus 0 SControl 300)
[    1.440022] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.440032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.440038] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.441276] ata3.00: ATA-8: Hitachi HDS722020ALA330, JKAOA20N, max UDMA/133
[    1.441279] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.442253] ata1.00: ATAPI: Optiarc DVD RW AD-7240S, 1.03, max UDMA/100, ATAPI AN
[    1.442671] ata3.00: configured for UDMA/133
[    1.444438] ata1.00: configured for UDMA/100
[    1.446228] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7240S  1.03 PQ: 0 ANSI: 5
[    1.447691] ata2.00: ATA-8: WDC WD3000HLFS-01G6U1, 04.04V02, max UDMA/133
[    1.447693] ata2.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.450457] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.450459] Uniform CD-ROM driver Revision: 3.20
[    1.450506] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.450532] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.454702] ata2.00: configured for UDMA/133
[    1.454758] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3000HLFS-0 04.0 PQ: 0 ANSI: 5
[    1.454829] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.454843] sd 1:0:0:0: [sda] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    1.454864] sd 1:0:0:0: [sda] Write Protect is off
[    1.454866] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.454876] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.454939]  sda:
[    1.454988] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72202 JKAO PQ: 0 ANSI: 5
[    1.455055] sd 2:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.455057] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.455169] sd 2:0:0:0: [sdb] Write Protect is off
[    1.455170] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.455180] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.455241]  sdb:
[    1.456378] scsi 6:0:0:0: CD-ROM            OPTIARC  DVD-ROM DDU1678A 1.00 PQ: 0 ANSI: 5
[    1.458648]  sdb1 sdb2
[    1.458781] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.460367] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.460410] sr 6:0:0:0: Attached scsi CD-ROM sr1
[    1.460433] sr 6:0:0:0: Attached scsi generic sg3 type 5
[    1.460475] ata8: port disabled. ignoring.
[    1.462033]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.489411] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.489419] Freeing unused kernel memory: 660k freed
[    1.489541] Write protecting the kernel read-only data: 7580k
[    1.562657] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.562991] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.562995] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.562999] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.567421] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 16
[    1.567426]   alloc irq_desc for 16 on node 0
[    1.567427]   alloc kstat_irqs on node 0
[    1.567435] ohci1394 0000:01:09.0: PCI INT A -> Link[LNKD] -> GSI 16 (level, low) -> IRQ 16
[    1.573312] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    1.573457] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/input/input4
[    1.573481] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    1.601274] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    1.622059] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4eff800-f4efffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.641123] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 40:61:86:64:31:9c
[    1.641126] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.827121] usb 3-2: configuration #1 chosen from 1 choice
[    1.830094] hub 3-2:1.0: USB hub found
[    1.833078] hub 3-2:1.0: 4 ports detected
[    2.141091] usb 3-2.1: new low speed USB device using ohci_hcd and address 3
[    2.269131] usb 3-2.1: configuration #1 chosen from 1 choice
[    2.280059] usbcore: registered new interface driver hiddev
[    2.286226] input: Gaming Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.1/3-2.1:1.0/input/input5
[    2.286258] generic-usb 0003:046D:C221.0001: input,hidraw0: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:02.0-2.1/input0
[    2.300126] input: Gaming Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.1/3-2.1:1.1/input/input6
[    2.300173] generic-usb 0003:046D:C221.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:02.0-2.1/input1
[    2.300181] usbcore: registered new interface driver usbhid
[    2.300182] usbhid: v2.6:USB HID core driver
[    2.355098] usb 3-2.2: new full speed USB device using ohci_hcd and address 4
[    2.492135] usb 3-2.2: configuration #1 chosen from 1 choice
[    2.507129] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.2/3-2.2:1.3/input/input7
[    2.507161] generic-usb 0003:046D:0A0B.0003: input,hidraw2: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:02.0-2.2/input3
[    2.595106] usb 3-2.3: new low speed USB device using ohci_hcd and address 5
[    2.716146] usb 3-2.3: configuration #1 chosen from 1 choice
[    2.726219] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input8
[    2.726256] generic-usb 0003:046D:C018.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:02.0-2.3/input0
[    2.805113] usb 3-2.4: new full speed USB device using ohci_hcd and address 6
[    2.932175] usb 3-2.4: configuration #1 chosen from 1 choice
[    2.946163] input: G11 Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.4/3-2.4:1.0/input/input9
[    2.946208] generic-usb 0003:046D:C225.0005: input,hiddev97,hidraw4: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:02.0-2.4/input0
[    2.953826] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0001a0a370]
[    3.123789] PM: Starting manual resume from disk
[    3.123791] PM: Resume from partition 8:1
[    3.123792] PM: Checking hibernation image.
[    3.123852] PM: Resume from disk failed.
[    3.149372] kjournald starting.  Commit interval 5 seconds
[    3.149378] EXT3-fs: mounted filesystem with writeback data mode.
[    3.509250] type=1505 audit(1266827999.919:2): operation="profile_load" pid=508 name=/usr/share/gdm/guest-session/Xsession
[    3.518729] type=1505 audit(1266827999.929:3): operation="profile_load" pid=509 name=/sbin/dhclient3
[    3.518908] type=1505 audit(1266827999.929:4): operation="profile_load" pid=509 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.519010] type=1505 audit(1266827999.929:5): operation="profile_load" pid=509 name=/usr/lib/connman/scripts/dhclient-script
[    3.540614] type=1505 audit(1266827999.949:6): operation="profile_load" pid=510 name=/usr/bin/evince
[    3.543466] type=1505 audit(1266827999.949:7): operation="profile_load" pid=510 name=/usr/bin/evince-previewer
[    3.545181] type=1505 audit(1266827999.959:8): operation="profile_load" pid=510 name=/usr/bin/evince-thumbnailer
[    3.559186] type=1505 audit(1266827999.969:9): operation="profile_load" pid=512 name=/usr/lib/cups/backend/cups-pdf
[    3.559401] type=1505 audit(1266827999.969:10): operation="profile_load" pid=512 name=/usr/sbin/cupsd
[    4.044289] Adding 7325600k swap on /dev/sda1.  Priority:-1 extents:1 across:7325600k 
[    4.333565] udev: starting version 147
[    4.810060] lp: driver loaded but no devices found
[    4.824607] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2d00
[    4.824610] ACPI: I/O resource nForce2_smbus [0x2e00-0x2e3f] conflicts with ACPI region SM00 [0x2e00-0x2e3f]
[    4.824612] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.824614] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    4.875958] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.913303] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    4.921586] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[    4.921859] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    4.921863] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[    4.921905] HDA Intel 0000:00:07.0: setting latency timer to 64
[    4.935029] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    5.587100] EXT3 FS on sda6, internal journal
[    5.721256] nvidia: module license 'NVIDIA' taints kernel.
[    5.721260] Disabling lock debugging due to kernel taint
[    5.742378] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.973595] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    5.973894] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[    5.973898] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[    5.973904] nvidia 0000:02:00.0: setting latency timer to 64
[    5.974109] nvidia 0000:05:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    5.974115] nvidia 0000:05:00.0: setting latency timer to 64
[    5.974225] nvidia 0000:06:00.0: enabling device (0000 -> 0003)
[    5.974492] ACPI: PCI Interrupt Link [LN0C] enabled at IRQ 19
[    5.974495] nvidia 0000:06:00.0: PCI INT A -> Link[LN0C] -> GSI 19 (level, low) -> IRQ 19
[    5.974500] nvidia 0000:06:00.0: setting latency timer to 64
[    5.974600] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.53  Wed Dec  9 15:29:46 PST 2009
[    6.006914] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    6.007039] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    6.007041] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[    6.007042] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[    6.088786] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    6.254544] kjournald starting.  Commit interval 5 seconds
[    6.257616] EXT3 FS on sda5, internal journal
[    6.257620] EXT3-fs: mounted filesystem with writeback data mode.
[    6.284479] usbcore: registered new interface driver snd-usb-audio
[    6.410019] hda_codec: Unknown model for ALC889, trying auto-probe from BIOS...
[    6.450065] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input10
[    7.037310] kjournald starting.  Commit interval 5 seconds
[    7.037606] EXT3 FS on sda7, internal journal
[    7.037610] EXT3-fs: mounted filesystem with writeback data mode.
[    7.641530] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    7.641532] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    7.641534] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    7.641535]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    7.641536]     Might be a BIOS bug, if BIOS says ECC is enabled
[    7.641537]     Use of the override can cause unknown side effects.
[    7.641548] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.838441] kjournald starting.  Commit interval 5 seconds
[    8.838733] EXT3 FS on sda8, internal journal
[    8.838738] EXT3-fs: mounted filesystem with writeback data mode.
[    9.297887] __ratelimit: 3 callbacks suppressed
[    9.297889] type=1505 audit(1266828005.709:12): operation="profile_replace" pid=1234 name=/usr/share/gdm/guest-session/Xsession
[    9.298792] type=1505 audit(1266828005.709:13): operation="profile_replace" pid=1235 name=/sbin/dhclient3
[    9.298972] type=1505 audit(1266828005.709:14): operation="profile_replace" pid=1235 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.299073] type=1505 audit(1266828005.709:15): operation="profile_replace" pid=1235 name=/usr/lib/connman/scripts/dhclient-script
[    9.300993] type=1505 audit(1266828005.709:16): operation="profile_replace" pid=1236 name=/usr/bin/evince
[    9.303853] type=1505 audit(1266828005.719:17): operation="profile_replace" pid=1236 name=/usr/bin/evince-previewer
[    9.305586] type=1505 audit(1266828005.719:18): operation="profile_replace" pid=1236 name=/usr/bin/evince-thumbnailer
[    9.308775] type=1505 audit(1266828005.719:19): operation="profile_replace" pid=1238 name=/usr/lib/cups/backend/cups-pdf
[    9.308991] type=1505 audit(1266828005.719:20): operation="profile_replace" pid=1238 name=/usr/sbin/cupsd
[    9.309976] type=1505 audit(1266828005.719:21): operation="profile_replace" pid=1239 name=/usr/sbin/tcpdump
[   10.521288] usplash:448 freeing invalid memtype fffffffff7000000-fffffffff7e00000
[   10.921896]   alloc irq_desc for 28 on node 0
[   10.921899]   alloc kstat_irqs on node 0
[   10.921905] forcedeth 0000:00:0a.0: irq 28 for MSI/MSI-X
[   11.599744] ppdev: user-space parallel port driver
[   21.373762] eth0: no IPv6 routers present
[   30.970019] timeout: still 7 active urbs..
[   36.970016] timeout: still 3 active urbs..
[   46.974722] 4:1:1: usb_set_interface failed
[   51.973893] 4:1:1: usb_set_interface failed
[   56.974070] 4:1:1: usb_set_interface failed
[   58.257701] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   58.259006] SGI XFS Quota Management subsystem
[   58.271518] JFS: nTxBlock = 8192, nTxLock = 65536
[   58.291331] NTFS driver 2.1.29 [Flags: R/O MODULE].
[   58.306136] QNX4 filesystem 0.2.3 registered.
[   58.571182] kjournald starting.  Commit interval 5 seconds
[   58.571188] EXT3-fs: mounted filesystem with writeback data mode.
[   61.974258] 4:1:1: usb_set_interface failed
[   66.970431] 4:1:1: usb_set_interface failed
[   71.970618] 4:1:1: usb_set_interface failed
[   76.970839] 4:1:1: usb_set_interface failed
[   81.973998] 4:1:1: usb_set_interface failed
[   86.972259] 4:1:1: usb_set_interface failed
[   91.974327] 4:1:1: usb_set_interface failed
[   96.974552] 4:1:1: usb_set_interface failed
[  101.970736] 4:1:1: usb_set_interface failed
[  106.970915] 4:1:1: usb_set_interface failed
[  111.971095] 4:1:1: usb_set_interface failed
[  116.974258] 4:1:1: usb_set_interface failed
[ 1721.451803] 4:1:1: usb_set_interface failed
[ 1726.450984] 4:1:1: usb_set_interface failed
[ 1731.454146] 4:1:1: usb_set_interface failed
[ 1736.455987] 4:1:1: usb_set_interface failed
[ 1741.454523] 4:1:1: usb_set_interface failed
[ 1746.453699] 4:1:1: usb_set_interface failed
[ 1751.453868] 4:1:1: usb_set_interface failed
[ 1756.454042] 4:1:1: usb_set_interface failed
[ 1761.454222] 4:1:1: usb_set_interface failed
[ 1766.457384] 4:1:1: usb_set_interface failed

```

---

### Post by ggerri on 2010-02-22
Can you try to plug the mouse into ps/2 with adapter? Was able to solve some problems in games with that...

---

### Post by tom.swartz07 on 2010-02-23
> **ggerri said:**
> Can you try to plug the mouse into ps/2 with adapter? Was able to solve some problems in games with that...

You could also try plugging in *after* you boot up. Ive seen some people with strange problems with USB devices (hard drives, usb keys, etc) when theyre plugged in as they boot up.



Could you verify that it is not just limited to the one mouse? For example, do you have another usb mouse that you could try- see if the same problems occur?

---

### Post by Rayve on 2010-02-26
I tried the PS/2 adapter (and extension cable) and got nothing from my mouse - this was after it had frozen, and then I kept it in PS/2 after a reboot and still had nothing.  So I plugged it in directly to my keyboard hub again, which would make this one "after having it unplugged during boot up" so we'll see how long this one lasts.

If that doesn't work, I bought another USB mouse yesterday for my other computer, which I can try to use here.

Thanks for the ideas!

---

### Post by Rayve on 2010-02-26
Unfortunately, no luck with not having it plugged it at boot up and then plugging it in later... mouse just froze.  :(

---

### Post by Rayve on 2010-03-29
Just as a note in case any one else comes across this thread: another way to boot into a different kernel is to press shift (numerous times) past your POST screen, as GRUB loads.  This will allow you to choose generic/safe mode for kernels you have downloaded, as well as other boot-up options.

---

### Post by go_beep_yourself on 2010-04-02
I'm having the same issue with the mouse freezing. I also saw this error many times "usb_set_interface failed". I tried a different installed kernel and had the same results. My mouse is freezing more often than yours. It freezes within 10~20 seconds. I think it may have something to do with Gnome. At the gdm login screen, the mouse would not freeze. Please tell if you find a solution to this problem.

---

### Post by go_beep_yourself on 2010-04-02
I think I found the solution. Try blacklisting the module snd_usb_audio.

```
echo "blacklist snd_usb_audio" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

---

### Post by Rayve on 2010-04-16
Thanks for the suggestion beep!  After rebooting due to a frozen mouse again, I just input it now and will see how it goes.

---

