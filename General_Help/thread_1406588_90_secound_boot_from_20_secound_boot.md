---
title: "90 secound boot from 20 secound boot"
date: 2010-02-14
forum: General Help
---

### Post by Naiki Muliaina on 2010-02-14
Not sure what i did to cause this one. I had a 20 secoundish boot time on karmic, that has gone up to more like 90 secounds. It happens between me selecting an OS in grub1.97 to when you see the Ubuntu Usplash symbol. All i see is a blinking command line. Everything else appears to work fine once booted.

Attached a boot chart if it helps at all.

Running 4 hard drives all with Ubuntu (or derivative) and swap on.

---

### Post by efflandt on 2010-02-14
Does dmesg give you a clue which steps it is lagging between?

On my laptop it took some time figuring out TV modes even though I don't use the TV output (I would use VGA if connected to HDTV).

---

### Post by Naiki Muliaina on 2010-02-14
Hmm eeek, no idea what im looking at :)

Im assuming thats time in secounds to left, it hangs a few times. Maybe the way i have hard drives/dvd drives set up in PC?

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 (Ubuntu 2.6.31-20.57-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=f7e6856a-efb0-4726-b3ac-70c1a78dd521 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFF00000 mask FFFFFFF00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFF00000000 write-back
[    0.000000]   5 base 000200000000 mask FFFFE0000000 write-back
[    0.000000]   6 base 000220000000 mask FFFFF0000000 write-back
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  modified: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  modified: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfee0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfee0000 page 4k
[    0.000000] kernel direct mapping tables up to cfee0000 @ 8000-b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000230000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ a000-c000
[    0.000000] RAMDISK: 3786c000 - 37fef135
[    0.000000] ACPI: RSDP 00000000000f6fe0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfee3000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfee30c0 070C8 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfee0000 00040
[    0.000000] ACPI: SSDT 00000000cfeea280 0088C (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfeeab40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfeeab80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: TAMG 00000000cfeeabc0 0040A (v01 GBT    GBT   B0 5455312E BG 53450101)
[    0.000000] ACPI: APIC 00000000cfeea1c0 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000055fff] pages 46
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0230000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e8c8c]    TEXT DATA BSS ==> [0001000000 - 00019e8c8c]
[    0.000000]   #3 [003786c000 - 0037fef135]          RAMDISK ==> [003786c000 - 0037fef135]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e9000 - 00019e90fe]              BRK ==> [00019e9000 - 00019e90fe]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000f55d0] f55d0
[    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880028600000-ffff88002f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfee0
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2096762
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3836 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 17024 pages used for memmap
[    0.000000]   Normal zone: 1228160 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
[    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
[    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028034000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2065300
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=f7e6856a-efb0-4726-b3ac-70c1a78dd521 ro quiet splash
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
[    0.000000] Memory: 8186128k/9175040k available (5328k kernel code, 787992k absent, 200920k reserved, 3013k data, 664k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3415.209 MHz processor.
[    0.000009] spurious 8259A interrupt: IRQ7.
[    0.001292] Console: colour VGA+ 80x25
[    0.001294] console [tty0] enabled
[    0.010000] allocated 83886080 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000]   alloc irq_desc for 24 on node 0
[    0.010000]   alloc kstat_irqs on node 0
[    0.010000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6830.40 BogoMIPS (lpj=34152040)
[    0.010019] Security Framework initialized
[    0.010031] AppArmor: AppArmor initialized
[    0.010387] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012353] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013246] Mount-cache hash table entries: 256
[    0.013324] Initializing cgroup subsys ns
[    0.013326] Initializing cgroup subsys cpuacct
[    0.013329] Initializing cgroup subsys memory
[    0.013333] Initializing cgroup subsys freezer
[    0.013334] Initializing cgroup subsys net_cls
[    0.013341] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.013343] CPU: L2 Cache: 512K (64 bytes/line)
[    0.013345] CPU 0/0x0 -> Node 0
[    0.013347] tseg: 00cff00000
[    0.013348] CPU: Physical Processor ID: 0
[    0.013349] CPU: Processor Core ID: 0
[    0.013351] mce: CPU supports 6 MCE banks
[    0.013357] using C1E aware idle routine
[    0.013358] Performance Counters: AMD PMU driver.
[    0.013360] ... version:                 0
[    0.013361] ... bit width:               48
[    0.013362] ... generic counters:        4
[    0.013363] ... value mask:              0000ffffffffffff
[    0.013364] ... max period:              00007fffffffffff
[    0.013365] ... fixed-purpose counters:  0
[    0.013366] ... counter mask:            000000000000000f
[    0.014412] ACPI: Core revision 20090521
[    0.030054] Setting APIC routing to flat
[    0.030525] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.137393] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 03
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6830.87 BogoMIPS (lpj=34154393)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.290799] CPU1: AMD Phenom(tm) II X4 965 Processor stepping 03
[    0.290804] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300041] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6830.87 BogoMIPS (lpj=34154381)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.460845] CPU2: AMD Phenom(tm) II X4 965 Processor stepping 03
[    0.460850] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470041] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6830.87 BogoMIPS (lpj=34154388)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.630799] CPU3: AMD Phenom(tm) II X4 965 Processor stepping 03
[    0.630803] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640007] Brought up 4 CPUs
[    0.640014] Total of 4 processors activated (27323.04 BogoMIPS).
[    0.640106] CPU0 attaching sched-domain:
[    0.640107]  domain 0: span 0-3 level MC
[    0.640109]   groups: 0 1 2 3
[    0.640112] CPU1 attaching sched-domain:
[    0.640114]  domain 0: span 0-3 level MC
[    0.640115]   groups: 1 2 3 0
[    0.640117] CPU2 attaching sched-domain:
[    0.640118]  domain 0: span 0-3 level MC
[    0.640119]   groups: 2 3 0 1
[    0.640122] CPU3 attaching sched-domain:
[    0.640123]  domain 0: span 0-3 level MC
[    0.640124]   groups: 3 0 1 2
[    0.640176] Booting paravirtualized kernel on bare hardware
[    0.640176] regulator: core version 0.5
[    0.640176] Time: 12:01:28  Date: 02/14/10
[    0.640176] NET: Registered protocol family 16
[    0.640176] node 0 link 0: io port [b000, ffff]
[    0.640176] TOM: 00000000d0000000 aka 3328M
[    0.640176] Fam 10h mmconf [e0000000, e00fffff]
[    0.640176] node 0 link 0: mmio [a0000, bffff]
[    0.640176] node 0 link 0: mmio [d0000000, dfffffff]
[    0.640176] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.640176] node 0 link 0: mmio [e0000000, e04fffff] ==> [e0100000, e04fffff]
[    0.640176] TOM2: 0000000230000000 aka 8960M
[    0.640176] bus: [00,04] on node 0 link 0
[    0.640176] bus: 00 index 0 io port: [0, ffff]
[    0.640176] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640176] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.640176] bus: 00 index 3 mmio: [e0500000, ffffffff]
[    0.640176] bus: 00 index 4 mmio: [e0100000, e04fffff]
[    0.640176] bus: 00 index 5 mmio: [230000000, fcffffffff]
[    0.640176] ACPI: bus type pci registered
[    0.640198] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.640200] PCI: MCFG area at e0000000 reserved in E820
[    0.646343] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.646344] PCI: Using configuration type 1 for base access
[    0.646758] bio: create slab <bio-0> at 0
[    0.646758] ACPI: EC: Look up EC in DSDT
[    0.655765] ACPI: Interpreter enabled
[    0.655770] ACPI: (supports S0 S3 S4 S5)
[    0.655784] ACPI: Using IOAPIC for interrupt routing
[    0.658522] ACPI: No dock devices found.
[    0.658596] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.658627] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.658663] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.658665] pci 0000:00:02.0: PME# disabled
[    0.658689] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.658691] pci 0000:00:04.0: PME# disabled
[    0.658720] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.658722] pci 0000:00:0a.0: PME# disabled
[    0.658764] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    0.658769] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    0.658775] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    0.658780] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    0.658786] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.658791] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f3ff]
[    0.658807] pci 0000:00:11.0: set SATA to AHCI mode
[    0.658846] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.658893] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.658956] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe02c000-0xfe02c0ff]
[    0.659001] pci 0000:00:12.2: supports D1 D2
[    0.659002] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.659006] pci 0000:00:12.2: PME# disabled
[    0.659032] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.659080] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.659142] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe029000-0xfe0290ff]
[    0.659188] pci 0000:00:13.2: supports D1 D2
[    0.659189] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.659192] pci 0000:00:13.2: PME# disabled
[    0.659293] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.659299] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.659304] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.659309] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.659315] pci 0000:00:14.1: reg 20 io port: [0xfa00-0xfa0f]
[    0.659372] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe024000-0xfe027fff]
[    0.659409] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.659412] pci 0000:00:14.2: PME# disabled
[    0.659502] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe028000-0xfe028fff]
[    0.659613] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.659620] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.659627] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.659631] pci 0000:01:00.0: reg 24 io port: [0xef00-0xef7f]
[    0.659635] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.659698] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.659700] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.659703] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.659764] pci 0000:02:00.0: reg 24 32bit mmio: [0xfdafe000-0xfdafffff]
[    0.659791] pci 0000:02:00.0: PME# supported from D3hot
[    0.659795] pci 0000:02:00.0: PME# disabled
[    0.659832] pci 0000:02:00.1: reg 10 io port: [0xdf00-0xdf07]
[    0.659838] pci 0000:02:00.1: reg 14 io port: [0xde00-0xde03]
[    0.659844] pci 0000:02:00.1: reg 18 io port: [0xdd00-0xdd07]
[    0.659850] pci 0000:02:00.1: reg 1c io port: [0xdc00-0xdc03]
[    0.659856] pci 0000:02:00.1: reg 20 io port: [0xdb00-0xdb0f]
[    0.659933] pci 0000:00:04.0: bridge io port: [0xd000-0xdfff]
[    0.659935] pci 0000:00:04.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.659937] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.659966] pci 0000:03:00.0: reg 10 io port: [0xce00-0xceff]
[    0.660012] pci 0000:03:00.0: reg 18 64bit mmio: [0xfddff000-0xfddfffff]
[    0.660021] pci 0000:03:00.0: reg 20 64bit mmio: [0xfdde0000-0xfddeffff]
[    0.660026] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.660051] pci 0000:03:00.0: supports D1 D2
[    0.660053] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660056] pci 0000:03:00.0: PME# disabled
[    0.660108] pci 0000:00:0a.0: bridge io port: [0xc000-0xcfff]
[    0.660109] pci 0000:00:0a.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.660112] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.660171] pci 0000:04:0e.0: reg 10 32bit mmio: [0xfdcff000-0xfdcff7ff]
[    0.660178] pci 0000:04:0e.0: reg 14 32bit mmio: [0xfdcf8000-0xfdcfbfff]
[    0.660231] pci 0000:04:0e.0: supports D1 D2
[    0.660232] pci 0000:04:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.660236] pci 0000:04:0e.0: PME# disabled
[    0.660267] pci 0000:00:14.4: transparent bridge
[    0.660271] pci 0000:00:14.4: bridge io port: [0xb000-0xbfff]
[    0.660274] pci 0000:00:14.4: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.660277] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.660289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.660447] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.660496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.660529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.660567] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.670776] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.670850] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.670911] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.670971] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.671032] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.671092] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.671154] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.671215] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.671317] SCSI subsystem initialized
[    0.671348] libata version 3.00 loaded.
[    0.671348] usbcore: registered new interface driver usbfs
[    0.671348] usbcore: registered new interface driver hub
[    0.671348] usbcore: registered new device driver usb
[    0.671348] ACPI: WMI: Mapper loaded
[    0.671348] PCI: Using ACPI for IRQ routing
[    0.671348] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.671348] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.710015] Bluetooth: Core ver 2.15
[    0.710038] NET: Registered protocol family 31
[    0.710038] Bluetooth: HCI device and connection manager initialized
[    0.710038] Bluetooth: HCI socket layer initialized
[    0.710038] NetLabel: Initializing
[    0.710038] NetLabel:  domain hash size = 128
[    0.710038] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.710038] NetLabel:  unlabeled traffic allowed by default
[    0.710165] PCI-DMA: Disabling AGP.
[    0.710230] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.710231] PCI-DMA: using GART IOMMU.
[    0.710233] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.711620] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.711625] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.720039] hpet: hpet2 irq 24 for MSI
[    0.740019] Switched to high resolution mode on CPU 0
[    0.740759] Switched to high resolution mode on CPU 3
[    0.740762] Switched to high resolution mode on CPU 1
[    0.740801] Switched to high resolution mode on CPU 2
[    0.760033] pnp: PnP ACPI init
[    0.760046] ACPI: bus type pnp registered
[    0.761593] pnp 00:0d: mem resource (0xcd200-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.761595] pnp 00:0d: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.761597] pnp 00:0d: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.761599] pnp 00:0d: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.761601] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.761603] pnp 00:0d: mem resource (0x100000-0xcfedffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.761651] pnp: PnP ACPI: found 14 devices
[    0.761652] ACPI: ACPI bus type pnp unregistered
[    0.761659] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.761660] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.761662] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.761665] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.761666] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.761668] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.761669] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.761671] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.761672] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.761673] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.761675] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.761678] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.761680] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.761681] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.761683] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.761684] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.761686] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.761687] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.761689] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.761690] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.761694] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.761697] system 00:0d: iomem range 0xcfee0000-0xcfefffff could not be reserved
[    0.761699] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.761701] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.761703] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.761704] system 00:0d: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.766299] AppArmor: AppArmor Filesystem Enabled
[    0.766322] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.766324] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.766326] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
[    0.766328] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.766331] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.766333] pci 0000:00:04.0:   IO window: 0xd000-0xdfff
[    0.766335] pci 0000:00:04.0:   MEM window: 0xfda00000-0xfdafffff
[    0.766337] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.766340] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:03
[    0.766341] pci 0000:00:0a.0:   IO window: 0xc000-0xcfff
[    0.766343] pci 0000:00:0a.0:   MEM window: 0xfde00000-0xfdefffff
[    0.766345] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.766348] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.766350] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    0.766354] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.766358] pci 0000:00:14.4:   PREFETCH window: 0xfdb00000-0xfdbfffff
[    0.766365]   alloc irq_desc for 18 on node 0
[    0.766366]   alloc kstat_irqs on node 0
[    0.766372] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.766375] pci 0000:00:02.0: setting latency timer to 64
[    0.766378]   alloc irq_desc for 16 on node 0
[    0.766379]   alloc kstat_irqs on node 0
[    0.766384] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.766386] pci 0000:00:04.0: setting latency timer to 64
[    0.766390] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.766391] pci 0000:00:0a.0: setting latency timer to 64
[    0.766398] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.766399] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.766401] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.766402] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.766404] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.766405] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.766407] pci_bus 0000:02: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.766408] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.766410] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.766411] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.766413] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.766414] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.766416] pci_bus 0000:04: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.766417] pci_bus 0000:04: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.766418] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.766420] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.766443] NET: Registered protocol family 2
[    0.766579] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.767356] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.769155] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.769387] TCP: Hash tables configured (established 524288 bind 65536)
[    0.769388] TCP reno registered
[    0.769448] NET: Registered protocol family 1
[    0.769485] Trying to unpack rootfs image as initramfs...
[    0.875566] Freeing initrd memory: 7692k freed
[    0.877414] Scanning for low memory corruption every 60 seconds
[    0.877488] audit: initializing netlink socket (disabled)
[    0.877497] type=2000 audit(1266148887.870:1): initialized
[    0.882991] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.883761] VFS: Disk quotas dquot_6.5.2
[    0.883792] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.884109] fuse init (API version 7.12)
[    0.884149] msgmni has been set to 16003
[    0.884316] alg: No test for stdrng (krng)
[    0.884326] io scheduler noop registered
[    0.884327] io scheduler anticipatory registered
[    0.884329] io scheduler deadline registered
[    0.884350] io scheduler cfq registered (default)
[    1.030056] pci 0000:01:00.0: Boot video device
[    1.030187]   alloc irq_desc for 25 on node 0
[    1.030188]   alloc kstat_irqs on node 0
[    1.030193] pcieport-driver 0000:00:02.0: irq 25 for MSI/MSI-X
[    1.030197] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.030268]   alloc irq_desc for 26 on node 0
[    1.030269]   alloc kstat_irqs on node 0
[    1.030272] pcieport-driver 0000:00:04.0: irq 26 for MSI/MSI-X
[    1.030275] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.030335]   alloc irq_desc for 27 on node 0
[    1.030336]   alloc kstat_irqs on node 0
[    1.030339] pcieport-driver 0000:00:0a.0: irq 27 for MSI/MSI-X
[    1.030342] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.030380] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.030395] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.030463] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.030465] ACPI: Power Button [PWRF]
[    1.030492] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.030493] ACPI: Power Button [PWRB]
[    1.030677] processor LNXCPU:00: registered as cooling_device0
[    1.030704] processor LNXCPU:01: registered as cooling_device1
[    1.030731] processor LNXCPU:02: registered as cooling_device2
[    1.030758] processor LNXCPU:03: registered as cooling_device3
[    1.032334] Linux agpgart interface v0.103
[    1.032339] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.032435] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.032632] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.033102] brd: module loaded
[    1.033310] loop: module loaded
[    1.033350] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.033438] ahci 0000:00:11.0: version 3.0
[    1.033448]   alloc irq_desc for 22 on node 0
[    1.033449]   alloc kstat_irqs on node 0
[    1.033456] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.033546] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.033548] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.033725] scsi0 : ahci
[    1.033783] scsi1 : ahci
[    1.033811] scsi2 : ahci
[    1.033837] scsi3 : ahci
[    1.033887] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.033890] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.033892] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.033895] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.033961] ahci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.050046] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.050048] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.050052] ahci 0000:02:00.0: setting latency timer to 64
[    1.050166] scsi4 : ahci
[    1.050202] scsi5 : ahci
[    1.050219] ata5: SATA max UDMA/133 abar m8192@0xfdafe000 port 0xfdafe100 irq 16
[    1.050222] ata6: SATA max UDMA/133 abar m8192@0xfdafe000 port 0xfdafe180 irq 16
[    1.050406] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.050479] scsi6 : pata_atiixp
[    1.050508] scsi7 : pata_atiixp
[    1.051125] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.051126] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.051252] pata_jmicron 0000:02:00.1: enabling device (0000 -> 0001)
[    1.051256]   alloc irq_desc for 17 on node 0
[    1.051257]   alloc kstat_irqs on node 0
[    1.051263] pata_jmicron 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.051279] pata_jmicron 0000:02:00.1: setting latency timer to 64
[    1.051324] scsi8 : pata_jmicron
[    1.051353] scsi9 : pata_jmicron
[    1.051371] ata9: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
[    1.051372] ata10: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
[    1.051645] Fixed MDIO Bus: probed
[    1.051662] PPP generic driver version 2.4.2
[    1.051707] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.051838] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.051849] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.051865] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.051891] ehci_hcd 0000:00:12.2: debug port 1
[    1.051900] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.070025] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.070070] usb usb1: configuration #1 chosen from 1 choice
[    1.070085] hub 1-0:1.0: USB hub found
[    1.070089] hub 1-0:1.0: 6 ports detected
[    1.070159]   alloc irq_desc for 19 on node 0
[    1.070160]   alloc kstat_irqs on node 0
[    1.070167] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.070177] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.070194] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.070219] ehci_hcd 0000:00:13.2: debug port 1
[    1.070239] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.090024] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.090064] usb usb2: configuration #1 chosen from 1 choice
[    1.090079] hub 2-0:1.0: USB hub found
[    1.090082] hub 2-0:1.0: 6 ports detected
[    1.090125] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.090160] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.090170] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.090187] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.090200] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.154061] usb usb3: configuration #1 chosen from 1 choice
[    1.154077] hub 3-0:1.0: USB hub found
[    1.154084] hub 3-0:1.0: 3 ports detected
[    1.154156] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.154165] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.154182] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.154195] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.214070] usb usb4: configuration #1 chosen from 1 choice
[    1.214083] hub 4-0:1.0: USB hub found
[    1.214089] hub 4-0:1.0: 3 ports detected
[    1.214161] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.214171] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.214191] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.214216] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.231724] ata7.00: ATAPI: Optiarc DVD RW AD-5170A, 1.52, max UDMA/66
[    1.271671] ata7.00: configured for UDMA/66
[    1.274064] usb usb5: configuration #1 chosen from 1 choice
[    1.274077] hub 5-0:1.0: USB hub found
[    1.274083] hub 5-0:1.0: 3 ports detected
[    1.274156] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.274166] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.274181] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.274194] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.334064] usb usb6: configuration #1 chosen from 1 choice
[    1.334077] hub 6-0:1.0: USB hub found
[    1.334084] hub 6-0:1.0: 3 ports detected
[    1.334157] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.334168] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.334184] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.334196] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.381341] ata3: SATA link down (SStatus 0 SControl 300)
[    1.394064] usb usb7: configuration #1 chosen from 1 choice
[    1.394077] hub 7-0:1.0: USB hub found
[    1.394083] hub 7-0:1.0: 2 ports detected
[    1.394119] uhci_hcd: USB Universal Host Controller Interface driver
[    1.394172] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.394517] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.394530] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.394584] mice: PS/2 mouse device common for all mice
[    1.394638] rtc_cmos 00:05: RTC can wake from S4
[    1.394656] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.394684] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.394761] device-mapper: uevent: version 1.0.3
[    1.394810] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.394885] device-mapper: multipath: version 1.1.0 loaded
[    1.394887] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.395035] cpuidle: using governor ladder
[    1.395036] cpuidle: using governor menu
[    1.395256] TCP cubic registered
[    1.395322] NET: Registered protocol family 10
[    1.395560] lo: Disabled Privacy Extensions
[    1.395714] NET: Registered protocol family 17
[    1.395724] Bluetooth: L2CAP ver 2.13
[    1.395725] Bluetooth: L2CAP socket layer initialized
[    1.395727] Bluetooth: SCO (Voice Link) ver 0.6
[    1.395728] Bluetooth: SCO socket layer initialized
[    1.395773] Bluetooth: RFCOMM TTY layer initialized
[    1.395775] Bluetooth: RFCOMM socket layer initialized
[    1.395776] Bluetooth: RFCOMM ver 1.11
[    1.395798] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor processors (4 cpu cores) (version 2.20.00)
[    1.395821] powernow-k8:    0 : pstate 0 (3400 MHz)
[    1.395822] powernow-k8:    1 : pstate 1 (2700 MHz)
[    1.395823] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.395824] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.396050] PM: Resume from disk failed.
[    1.396057] registered taskstats version 1
[    1.396135]   Magic number: 14:259:26
[    1.396184] rtc_cmos 00:05: setting system clock to 2010-02-14 12:01:29 UTC (1266148889)
[    1.396185] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.396186] EDD information not available.
[    1.401289] ata6: SATA link down (SStatus 0 SControl 300)
[    1.410206] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.560032] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.560053] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.560069] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.560848] ata4.00: ATA-8: Hitachi HDP725032GLA360, GM3OA52A, max UDMA/133
[    1.560850] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.561824] ata4.00: configured for UDMA/133
[    1.566381] ata1.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
[    1.566383] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.566401] ata2.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
[    1.566403] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.572808] ata1.00: configured for UDMA/133
[    1.572823] ata2.00: configured for UDMA/133
[    1.580029] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.584126] ata5.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100, ATAPI AN
[    1.588445] ata5.00: configured for UDMA/100
[    1.593829] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    1.593903] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.593929] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.593950] sd 0:0:0:0: [sda] Write Protect is off
[    1.593951] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.593962] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.594019]  sda:
[    1.594059] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    1.594110] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.594132] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.594151] sd 1:0:0:0: [sdb] Write Protect is off
[    1.594152] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.594162] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.594207]  sdb:
[    1.594240] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDP72503 GM3O PQ: 0 ANSI: 5
[    1.594291] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.594324] sd 3:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.594345] sd 3:0:0:0: [sdc] Write Protect is off
[    1.594346] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.594356] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.594418]  sdc: sda1 sda2 < sdb1 sdb2 <
[    1.607114] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
[    1.608518]  sdc1
[    1.608951] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.617614]  sda5 >
[    1.617754] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.628085] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.628087] Uniform CD-ROM driver Revision: 3.20
[    1.628130] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.628153] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    1.633768]  sdb5 >
[    1.633907] sd 1:0:0:0: [sdb] Attached SCSI disk
[   22.950037] ata7: lost interrupt (Status 0x58)
[   23.001262] ata7: drained 32768 bytes to clear DRQ.
[   23.031017] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   23.031022] ata7.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   23.031023]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   23.031024]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   23.031025] ata7.00: status: { DRDY }
[   23.031043] ata7: soft resetting link
[   23.250421] ata7.00: configured for UDMA/66
[   23.250658] ata7: EH complete
[   43.950050] ata7: lost interrupt (Status 0x58)
[   43.960036] ata7: drained 32768 bytes to clear DRQ.
[   44.031036] ata7.00: limiting speed to UDMA/44:PIO4
[   44.031038] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   44.031043] ata7.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   44.031043]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   44.031044]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   44.031046] ata7.00: status: { DRDY }
[   44.031063] ata7: soft resetting link
[   44.250421] ata7.00: configured for UDMA/44
[   44.250647] ata7: EH complete
[   64.950039] ata7: lost interrupt (Status 0x58)
[   64.960026] ata7: drained 32768 bytes to clear DRQ.
[   65.031030] ata7.00: limiting speed to UDMA/33:PIO4
[   65.031031] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   65.031036] ata7.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   65.031037]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   65.031037]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   65.031039] ata7.00: status: { DRDY }
[   65.031056] ata7: soft resetting link
[   65.250421] ata7.00: configured for UDMA/33
[   65.250648] ata7: EH complete
[   85.950049] ata7: lost interrupt (Status 0x58)
[   85.960036] ata7: drained 32768 bytes to clear DRQ.
[   86.031034] ata7.00: limiting speed to PIO4
[   86.031035] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   86.031040] ata7.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   86.031041]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   86.031041]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   86.031043] ata7.00: status: { DRDY }
[   86.031060] ata7: soft resetting link
[   86.250421] ata7.00: configured for PIO4
[   86.250612] ata7: EH complete
[   86.250615] scsi scan: 96 byte inquiry failed.  Consider BLIST_INQUIRY_36 for this device
[   86.251038] scsi 6:0:0:0: CD-ROM            Optiarc  DVD RW AD-5170A  1.52 PQ: 0 ANSI: 5
[   86.253489] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   86.253526] sr 6:0:0:0: Attached scsi CD-ROM sr1
[   86.253545] sr 6:0:0:0: Attached scsi generic sg4 type 5
[   86.475251] ata8.00: ATA-7: ST3160215AS, 3.AAC, max UDMA/133
[   86.475252] ata8.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   86.558570] ata8.00: configured for UDMA/100
[   86.558628] scsi 7:0:0:0: Direct-Access     ATA      ST3160215AS      3.AA PQ: 0 ANSI: 5
[   86.558693] sd 7:0:0:0: Attached scsi generic sg5 type 0
[   86.558698] sd 7:0:0:0: [sdd] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[   86.558719] sd 7:0:0:0: [sdd] Write Protect is off
[   86.558720] sd 7:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   86.558730] sd 7:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   86.558786]  sdd: sdd1 sdd3 < sdd5 sdd6 >
[   86.629982] sd 7:0:0:0: [sdd] Attached SCSI disk
[   86.721294] Freeing unused kernel memory: 664k freed
[   86.721405] Write protecting the kernel read-only data: 7596k
[   86.791275] Floppy drive(s): fd0 is 1.44M
[   86.806894] ohci1394 0000:04:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   86.812297] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   86.812311] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   86.812347] r8169 0000:03:00.0: setting latency timer to 64
[   86.812376]   alloc irq_desc for 28 on node 0
[   86.812377]   alloc kstat_irqs on node 0
[   86.812386] r8169 0000:03:00.0: irq 28 for MSI/MSI-X
[   86.812717] eth0: RTL8168c/8111c at 0xffffc90000c76000, 00:24:1d:c4:dc:1c, XID 3c4000c0 IRQ 28
[   86.816524] FDC 0 is a post-1991 82077
[   86.870056] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   87.889001] PM: Starting manual resume from disk
[   87.889003] PM: Resume from partition 8:5
[   87.889004] PM: Checking hibernation image.
[   87.889114] PM: Resume from disk failed.
[   87.938437] EXT4-fs (sda1): barriers enabled
[   87.959685] kjournald2 starting: pid 479, dev sda1:8, commit interval 5 seconds
[   87.959757] EXT4-fs (sda1): delayed allocation enabled
[   87.959760] EXT4-fs: file extents enabled
[   88.017133] EXT4-fs: mballoc enabled
[   88.017142] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   88.191378] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00cb00190000241d]
[   88.590107] type=1505 audit(1266148976.693:2): operation="profile_load" pid=506 name=/usr/share/gdm/guest-session/Xsession
[   88.591385] type=1505 audit(1266148976.693:3): operation="profile_load" pid=507 name=/sbin/dhclient3
[   88.591552] type=1505 audit(1266148976.693:4): operation="profile_load" pid=507 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   88.591647] type=1505 audit(1266148976.693:5): operation="profile_load" pid=507 name=/usr/lib/connman/scripts/dhclient-script
[   88.635994] type=1505 audit(1266148976.735:6): operation="profile_load" pid=508 name=/usr/bin/evince
[   88.638659] type=1505 audit(1266148976.735:7): operation="profile_load" pid=508 name=/usr/bin/evince-previewer
[   88.640262] type=1505 audit(1266148976.735:8): operation="profile_load" pid=508 name=/usr/bin/evince-thumbnailer
[   88.655957] type=1505 audit(1266148976.755:9): operation="profile_load" pid=511 name=/usr/lib/cups/backend/cups-pdf
[   88.656159] type=1505 audit(1266148976.755:10): operation="profile_load" pid=511 name=/usr/sbin/cupsd
[   88.670200] type=1505 audit(1266148976.765:11): operation="profile_load" pid=512 name=/usr/sbin/tcpdump
[   99.852699] udev: starting version 147
[   99.868203] Adding 24009100k swap on /dev/sda5.  Priority:-1 extents:1 across:24009100k 
[   99.873575] lp: driver loaded but no devices found
[   99.874172] Adding 24009100k swap on /dev/sdb5.  Priority:-2 extents:1 across:24009100k 
[   99.877864] EDAC MC: Ver: 2.1.0 Feb  8 2010
[   99.882243] Adding 2931820k swap on /dev/sdc1.  Priority:-3 extents:1 across:2931820k 
[   99.898061] nvidia: module license 'NVIDIA' taints kernel.
[   99.898063] Disabling lock debugging due to kernel taint
[   99.933218] ip_tables: (C) 2000-2006 Netfilter Core Team
[  100.002537] EDAC amd64_edac:  Ver: 3.2.0 Feb  8 2010
[  100.150530] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  100.150592] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  100.150596] nvidia 0000:01:00.0: setting latency timer to 64
[  100.150781] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[  100.161067] logips2pp: Detected unknown logitech mouse model 127
[  100.264603] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
[  100.264760] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input4
[  100.268450] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[  100.268452] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  100.268680] EDAC amd64: This node reports that Memory ECC is currently disabled.
[  100.268682] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[  100.268683] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[  100.268684]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[  100.268685]     Might be a BIOS bug, if BIOS says ECC is enabled
[  100.268686]     Use of the override can cause unknown side effects.
[  100.268696] amd64_edac: probe of 0000:00:18.2 failed with error -22
[  100.553092] EXT4-fs (sda1): internal journal on sda1:8
[  100.629034] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[  100.720618] type=1505 audit(1266148988.817:12): operation="profile_replace" pid=1101 name=/usr/share/gdm/guest-session/Xsession
[  100.721499] type=1505 audit(1266148988.817:13): operation="profile_replace" pid=1102 name=/sbin/dhclient3
[  100.721667] type=1505 audit(1266148988.817:14): operation="profile_replace" pid=1102 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  100.721762] type=1505 audit(1266148988.817:15): operation="profile_replace" pid=1102 name=/usr/lib/connman/scripts/dhclient-script
[  100.723585] type=1505 audit(1266148988.817:16): operation="profile_replace" pid=1103 name=/usr/bin/evince
[  100.726271] type=1505 audit(1266148988.827:17): operation="profile_replace" pid=1103 name=/usr/bin/evince-previewer
[  100.727882] type=1505 audit(1266148988.827:18): operation="profile_replace" pid=1103 name=/usr/bin/evince-thumbnailer
[  100.731586] type=1505 audit(1266148988.827:19): operation="profile_replace" pid=1106 name=/usr/lib/cups/backend/cups-pdf
[  100.731790] type=1505 audit(1266148988.827:20): operation="profile_replace" pid=1106 name=/usr/sbin/cupsd
[  100.732753] type=1505 audit(1266148988.827:21): operation="profile_replace" pid=1107 name=/usr/sbin/tcpdump

```



[I]

Edit  Update :

Unplugged a DVD drive and had a huge speed increase. Guessing i had the cables around wrong or something. If i get it working fully ill shout and mark solved. :)

Edit update update :

Changed the IDE cable to the DVD drive, everythings working fine again. TY Efflandt for the quick reply

[/I]

---

