---
title: "Random mouse/keyboard freeze"
date: 2010-05-01
forum: General Help
---

### Post by gredorian on 2010-05-01
Here's my story. I downloaded and burnt the Kubuntu 10.04 release to a CD. I tried to install it. First time, couldn't find the disks and eventually it froze. Ok, second try, when it's contacting the "time server" (or whatever) another freeze, but this time I notice everything is running fine and then get a nice little image with the current time (increasing seconds and all). Third attemp, clicked the "update this installer" and it went fine. "Yay!" I thought. Well, a few minutes in my beautiful 10.04 system and again, another freeze. Hit the power button and to my surprise a "Shutdown" dialog shows up with a countdown. After 30 seconds it logs out and mouse is working again. I log back in and come here to write this long post, and as I was writing the title "Random mouse/ke..." guess what? Yeah, it froze again. And the little bar that goes after the writing continued happily blinking. Hit the power button but this time mouse and keyboard were still frozen in the login screen.

Short version: mouse and keyboard randomly freeze while the rest of the system apparently work fine. Any ideas?

---

### Post by P4man on 2010-05-01
is this a wireless keyboard and mouse ? USB or bluetooth? Do you see anything in dmesg log?

---

### Post by gredorian on 2010-05-01
It's not a wireless mouse or keyboard. I just found this on launchpad: [https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/573182](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/573182)

"When using LyX, it sometimes stops receiving any keyboard or mouse input.
Strangely, this can be cured by ensuring that its window is in full-screen mode and the dragging that window (I'm using compiz) so that it is out of full-screen. That's right, just switching in and out of full screen with alt-f10 won't help -- I have to force it out with compiz in order to get LyX to respond to keyboard again. I haven't seen this problem with any other program."

Added today. It's probably the same problem. I didn't try the fullscreen thing because I just can't input anything.

---

### Post by P4man on 2010-05-01
hmm, not convinced. 
Can you open a terminal (konsole I think on kde) and type in:

```
dmesg
```

and copy paste the output here (please use # code tags as its a long output)  ? Ideally after you had a freeze.

---

### Post by gredorian on 2010-05-01
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=b463f58c-57a8-4489-bf5b-b523b9381b92 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0FFFE0000 mask FFFFF0000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf770000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf770000 page 4k
[    0.000000] kernel direct mapping tables up to bf770000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
[    0.000000] RAMDISK: 377fe000 - 37fefb37
[    0.000000] ACPI: RSDP 00000000000fb9a0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bf770000 0003C (v01 081909 RSDT1047 20090819 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf770200 00084 (v01 081909 FACP1047 20090819 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf7704a0 0E603 (v01  A1325 A1325001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf788000 00040
[    0.000000] ACPI: APIC 00000000bf770390 000CC (v01 081909 APIC1047 20090819 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf770460 0003C (v01 081909 OEMMCFG  20090819 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf788040 00072 (v01 081909 OEMB1047 20090819 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf77f4a0 00038 (v01 081909 OEMHPET  20090819 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf7890f0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fe000 - 0037fefb37]          RAMDISK ==> [00377fe000 - 0037fefb37]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a2c0]              BRK ==> [0001a2a000 - 0001a2a2c0]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf770
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046271
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765864 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf770000 - 00000000bf788000
[    0.000000] PM: Registered nosave memory: 00000000bf788000 - 00000000bf7dc000
[    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u131072
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028248
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=b463f58c-57a8-4489-bf5b-b523b9381b92 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4041076k/5242880k available (5409k kernel code, 1057796k absent, 144008k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:536
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 25 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 26 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 27 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 28 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2674.477 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5348.95 BogoMIPS (lpj=26744770)
[    0.000019] Security Framework initialized
[    0.000032] AppArmor: AppArmor initialized
[    0.000283] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001043] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001363] Mount-cache hash table entries: 256
[    0.001445] Initializing cgroup subsys ns
[    0.001448] Initializing cgroup subsys cpuacct
[    0.001451] Initializing cgroup subsys memory
[    0.001455] Initializing cgroup subsys devices
[    0.001457] Initializing cgroup subsys freezer
[    0.001458] Initializing cgroup subsys net_cls
[    0.001471] CPU: Physical Processor ID: 0
[    0.001472] CPU: Processor Core ID: 0
[    0.001475] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001477] CPU: L2 cache: 256K
[    0.001478] CPU: L3 cache: 8192K
[    0.001480] CPU 0/0x0 -> Node 0
[    0.001482] mce: CPU supports 9 MCE banks
[    0.001490] CPU0: Thermal monitoring enabled (TM1)
[    0.001493] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 SHD:8
[    0.001500] using mwait in idle threads.
[    0.001501] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
[    0.001505] ... version:                3
[    0.001506] ... bit width:              48
[    0.001507] ... generic registers:      4
[    0.001508] ... value mask:             0000ffffffffffff
[    0.001510] ... max period:             000000007fffffff
[    0.001511] ... fixed-purpose events:   3
[    0.001512] ... event mask:             000000070000000f
[    0.003235] ACPI: Core revision 20090903
[    0.119791] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.119794] ftrace: allocating 22518 entries in 89 pages
[    0.125739] Setting APIC routing to physical flat
[    0.126065] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.225842] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.337939] Booting processor 1 APIC 0x2 ip 0x6000
[    0.348382] Initializing CPU#1
[    0.497515] CPU: Physical Processor ID: 0
[    0.497516] CPU: Processor Core ID: 1
[    0.497518] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.497519] CPU: L2 cache: 256K
[    0.497520] CPU: L3 cache: 8192K
[    0.497522] CPU 1/0x2 -> Node 0
[    0.497530] CPU1: Thermal monitoring enabled (TM1)
[    0.497533] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.497550] CPU1: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.497556] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.517578] Booting processor 2 APIC 0x4 ip 0x6000
[    0.527915] Initializing CPU#2
[    0.677131] CPU: Physical Processor ID: 0
[    0.677132] CPU: Processor Core ID: 2
[    0.677134] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.677135] CPU: L2 cache: 256K
[    0.677136] CPU: L3 cache: 8192K
[    0.677138] CPU 2/0x4 -> Node 0
[    0.677147] CPU2: Thermal monitoring enabled (TM1)
[    0.677150] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.677189] CPU2: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.677195] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.697217] Booting processor 3 APIC 0x6 ip 0x6000
[    0.707554] Initializing CPU#3
[    0.856747] CPU: Physical Processor ID: 0
[    0.856748] CPU: Processor Core ID: 3
[    0.856750] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.856751] CPU: L2 cache: 256K
[    0.856752] CPU: L3 cache: 8192K
[    0.856754] CPU 3/0x6 -> Node 0
[    0.856763] CPU3: Thermal monitoring enabled (TM1)
[    0.856765] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.856828] CPU3: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.856834] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.876803] Brought up 4 CPUs
[    0.876805] Total of 4 processors activated (21398.54 BogoMIPS).
[    0.878059] CPU0 attaching sched-domain:
[    0.878062]  domain 0: span 0-3 level MC
[    0.878064]   groups: 0 1 2 3
[    0.878069] CPU1 attaching sched-domain:
[    0.878070]  domain 0: span 0-3 level MC
[    0.878071]   groups: 1 2 3 0
[    0.878075] CPU2 attaching sched-domain:
[    0.878076]  domain 0: span 0-3 level MC
[    0.878077]   groups: 2 3 0 1
[    0.878080] CPU3 attaching sched-domain:
[    0.878082]  domain 0: span 0-3 level MC
[    0.878083]   groups: 3 0 1 2
[    0.878247] devtmpfs: initialized
[    0.878490] regulator: core version 0.5
[    0.878513] Time: 16:58:06  Date: 05/01/10
[    0.878546] NET: Registered protocol family 16
[    0.878611] Trying to unpack rootfs image as initramfs...
[    0.878633] ACPI: bus type pci registered
[    0.878683] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.878685] PCI: Not using MMCONFIG.
[    0.878686] PCI: Using configuration type 1 for base access
[    0.879215] bio: create slab <bio-0> at 0
[    0.880007] ACPI: EC: Look up EC in DSDT
[    0.881277] ACPI: Executed 1 blocks of module-level executable AML code
[    0.893085] ACPI: Interpreter enabled
[    0.893088] ACPI: (supports S0 S1 S3 S4 S5)
[    0.893105] ACPI: Using IOAPIC for interrupt routing
[    0.893150] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.896003] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.900989] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.909620] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.909690] ACPI Warning: Incorrect checksum in table [OEMB] - F3, should be F2 (20090903/tbutils-314)
[    0.909800] ACPI: No dock devices found.
[    0.910080] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.910182] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.910185] pci 0000:00:03.0: PME# disabled
[    0.910429] pci 0000:00:1a.0: reg 10 32bit mmio: [0xfbafe000-0xfbafe3ff]
[    0.910477] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.910481] pci 0000:00:1a.0: PME# disabled
[    0.910517] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbaf8000-0xfbafbfff]
[    0.910553] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.910556] pci 0000:00:1b.0: PME# disabled
[    0.910610] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.910613] pci 0000:00:1c.0: PME# disabled
[    0.910670] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.910673] pci 0000:00:1c.4: PME# disabled
[    0.910727] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.910730] pci 0000:00:1c.5: PME# disabled
[    0.910784] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.910787] pci 0000:00:1c.6: PME# disabled
[    0.910842] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.910845] pci 0000:00:1c.7: PME# disabled
[    0.910889] pci 0000:00:1d.0: reg 10 32bit mmio: [0xfbafd000-0xfbafd3ff]
[    0.910937] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.910941] pci 0000:00:1d.0: PME# disabled
[    0.911095] pci 0000:00:1f.2: reg 10 io port: [0x9c00-0x9c07]
[    0.911100] pci 0000:00:1f.2: reg 14 io port: [0x9880-0x9883]
[    0.911105] pci 0000:00:1f.2: reg 18 io port: [0x9800-0x9807]
[    0.911109] pci 0000:00:1f.2: reg 1c io port: [0x9480-0x9483]
[    0.911114] pci 0000:00:1f.2: reg 20 io port: [0x9400-0x940f]
[    0.911118] pci 0000:00:1f.2: reg 24 io port: [0x9080-0x908f]
[    0.911158] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfbafc000-0xfbafc0ff]
[    0.911169] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.911207] pci 0000:00:1f.5: reg 10 io port: [0xac00-0xac07]
[    0.911211] pci 0000:00:1f.5: reg 14 io port: [0xa880-0xa883]
[    0.911216] pci 0000:00:1f.5: reg 18 io port: [0xa800-0xa807]
[    0.911220] pci 0000:00:1f.5: reg 1c io port: [0xa480-0xa483]
[    0.911225] pci 0000:00:1f.5: reg 20 io port: [0xa400-0xa40f]
[    0.911230] pci 0000:00:1f.5: reg 24 io port: [0xa080-0xa08f]
[    0.911280] pci 0000:01:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.911287] pci 0000:01:00.0: reg 18 64bit mmio: [0xfbbe0000-0xfbbeffff]
[    0.911292] pci 0000:01:00.0: reg 20 io port: [0xb000-0xb0ff]
[    0.911299] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbbc0000-0xfbbdffff]
[    0.911316] pci 0000:01:00.0: supports D1 D2
[    0.911344] pci 0000:01:00.1: reg 10 64bit mmio: [0xfbbfc000-0xfbbfffff]
[    0.911375] pci 0000:01:00.1: supports D1 D2
[    0.911403] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
[    0.911406] pci 0000:00:03.0: bridge 32bit mmio: [0xfbb00000-0xfbbfffff]
[    0.911410] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.911607] pci 0000:03:00.0: reg 24 32bit mmio: [0xfbdfe000-0xfbdfffff]
[    0.911643] pci 0000:03:00.0: PME# supported from D3hot
[    0.911647] pci 0000:03:00.0: PME# disabled
[    0.911696] pci 0000:03:00.1: reg 10 io port: [0xdc00-0xdc07]
[    0.911704] pci 0000:03:00.1: reg 14 io port: [0xd880-0xd883]
[    0.911712] pci 0000:03:00.1: reg 18 io port: [0xd800-0xd807]
[    0.911720] pci 0000:03:00.1: reg 1c io port: [0xd480-0xd483]
[    0.911728] pci 0000:03:00.1: reg 20 io port: [0xd400-0xd40f]
[    0.911811] pci 0000:00:1c.6: bridge io port: [0xd000-0xdfff]
[    0.911814] pci 0000:00:1c.6: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]
[    0.911860] pci 0000:02:00.0: reg 10 io port: [0xc800-0xc8ff]
[    0.911879] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfafff000-0xfaffffff]
[    0.911891] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfaff8000-0xfaffbfff]
[    0.911899] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfbcf0000-0xfbcfffff]
[    0.911935] pci 0000:02:00.0: supports D1 D2
[    0.911936] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.911940] pci 0000:02:00.0: PME# disabled
[    0.911992] pci 0000:00:1c.7: bridge io port: [0xc000-0xcfff]
[    0.911995] pci 0000:00:1c.7: bridge 32bit mmio: [0xfbc00000-0xfbcfffff]
[    0.912000] pci 0000:00:1c.7: bridge 64bit mmio pref: [0xfaf00000-0xfaffffff]
[    0.912034] pci 0000:07:03.0: reg 10 32bit mmio: [0xfbeff800-0xfbefffff]
[    0.912040] pci 0000:07:03.0: reg 14 io port: [0xec00-0xec7f]
[    0.912079] pci 0000:07:03.0: supports D2
[    0.912081] pci 0000:07:03.0: PME# supported from D2 D3hot D3cold
[    0.912084] pci 0000:07:03.0: PME# disabled
[    0.912122] pci 0000:00:1e.0: transparent bridge
[    0.912125] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.912128] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.912158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.912312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.912415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.912472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.912522] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.912571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
[    0.912620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    0.912680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    0.933863] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.933974] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.934082] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.934192] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.934301] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.934411] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.934521] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.934630] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.934722] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.934725] vgaarb: loaded
[    0.934795] SCSI subsystem initialized
[    0.934867] libata version 3.00 loaded.
[    0.934914] usbcore: registered new interface driver usbfs
[    0.934921] usbcore: registered new interface driver hub
[    0.934937] usbcore: registered new device driver usb
[    0.935031] ACPI: WMI: Mapper loaded
[    0.935032] PCI: Using ACPI for IRQ routing
[    0.935159] NetLabel: Initializing
[    0.935160] NetLabel:  domain hash size = 128
[    0.935161] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.935172] NetLabel:  unlabeled traffic allowed by default
[    0.935199] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    0.935203] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.946568] hpet: hpet2 irq 24 for MSI
[    0.946720] hpet: hpet3 irq 25 for MSI
[    0.956624] hpet: hpet4 irq 26 for MSI
[    0.966629] hpet: hpet5 irq 27 for MSI
[    0.966640] Switching to clocksource tsc
[    0.967808] AppArmor: AppArmor Filesystem Enabled
[    0.967820] pnp: PnP ACPI init
[    0.967830] ACPI: bus type pnp registered
[    0.970592] pnp: PnP ACPI: found 17 devices
[    0.970594] ACPI: ACPI bus type pnp unregistered
[    0.970601] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    0.970603] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    0.970605] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    0.970607] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.970612] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.970616] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.970618] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.970620] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.970622] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.970624] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.970626] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.970629] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.970633] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.970635] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.970639] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.970642] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.970644] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.970646] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.970648] system 00:10: iomem range 0x100000-0xbfffffff could not be reserved
[    0.970650] system 00:10: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.975315] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.975317] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
[    0.975320] pci 0000:00:03.0:   MEM window: 0xfbb00000-0xfbbfffff
[    0.975323] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.975327] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
[    0.975329] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.975333] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.975336] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.975341] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
[    0.975343] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.975347] pci 0000:00:1c.4:   MEM window: 0xc0400000-0xc05fffff
[    0.975350] pci 0000:00:1c.4:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    0.975355] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.975357] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
[    0.975360] pci 0000:00:1c.5:   MEM window: 0xc0800000-0xc09fffff
[    0.975364] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
[    0.975369] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03
[    0.975371] pci 0000:00:1c.6:   IO window: 0xd000-0xdfff
[    0.975374] pci 0000:00:1c.6:   MEM window: 0xfbd00000-0xfbdfffff
[    0.975378] pci 0000:00:1c.6:   PREFETCH window: 0x000000c0c00000-0x000000c0dfffff
[    0.975382] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02
[    0.975385] pci 0000:00:1c.7:   IO window: 0xc000-0xcfff
[    0.975388] pci 0000:00:1c.7:   MEM window: 0xfbc00000-0xfbcfffff
[    0.975391] pci 0000:00:1c.7:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.975396] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.975398] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.975402] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.975405] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.975416]   alloc irq_desc for 16 on node -1
[    0.975417]   alloc kstat_irqs on node -1
[    0.975421] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.975424] pci 0000:00:03.0: setting latency timer to 64
[    0.975430] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.975432]   alloc irq_desc for 17 on node -1
[    0.975433]   alloc kstat_irqs on node -1
[    0.975436] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.975439] pci 0000:00:1c.0: setting latency timer to 64
[    0.975445] pci 0000:00:1c.4: enabling device (0104 -> 0107)
[    0.975447] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.975450] pci 0000:00:1c.4: setting latency timer to 64
[    0.975456] pci 0000:00:1c.5: enabling device (0104 -> 0107)
[    0.975459] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.975462] pci 0000:00:1c.5: setting latency timer to 64
[    0.975468]   alloc irq_desc for 18 on node -1
[    0.975472]   alloc kstat_irqs on node -1
[    0.975474] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.975477] pci 0000:00:1c.6: setting latency timer to 64
[    0.975483]   alloc irq_desc for 19 on node -1
[    0.975484]   alloc kstat_irqs on node -1
[    0.975487] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.975490] pci 0000:00:1c.7: setting latency timer to 64
[    0.975494] pci 0000:00:1e.0: setting latency timer to 64
[    0.975498] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.975499] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.975501] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.975503] pci_bus 0000:01: resource 1 mem: [0xfbb00000-0xfbbfffff]
[    0.975504] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.975506] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.975508] pci_bus 0000:06: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.975509] pci_bus 0000:06: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.975511] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
[    0.975513] pci_bus 0000:05: resource 1 mem: [0xc0400000-0xc05fffff]
[    0.975514] pci_bus 0000:05: resource 2 pref mem [0xc0600000-0xc07fffff]
[    0.975516] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.975517] pci_bus 0000:04: resource 1 mem: [0xc0800000-0xc09fffff]
[    0.975519] pci_bus 0000:04: resource 2 pref mem [0xc0a00000-0xc0bfffff]
[    0.975521] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.975522] pci_bus 0000:03: resource 1 mem: [0xfbd00000-0xfbdfffff]
[    0.975524] pci_bus 0000:03: resource 2 pref mem [0xc0c00000-0xc0dfffff]
[    0.975526] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.975527] pci_bus 0000:02: resource 1 mem: [0xfbc00000-0xfbcfffff]
[    0.975529] pci_bus 0000:02: resource 2 pref mem [0xfaf00000-0xfaffffff]
[    0.975530] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
[    0.975532] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.975534] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.975535] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.975558] NET: Registered protocol family 2
[    0.975683] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.976416] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.978710] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.978989] TCP: Hash tables configured (established 524288 bind 65536)
[    0.978991] TCP reno registered
[    0.979077] NET: Registered protocol family 1
[    0.979140] pci 0000:01:00.0: Boot video device
[    0.979380] Scanning for low memory corruption every 60 seconds
[    0.979465] audit: initializing netlink socket (disabled)
[    0.979472] type=2000 audit(1272733086.739:1): initialized
[    0.987125] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.988104] VFS: Disk quotas dquot_6.5.2
[    0.988143] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.988576] fuse init (API version 7.13)
[    0.988632] msgmni has been set to 7892
[    0.988784] alg: No test for stdrng (krng)
[    0.988821] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.988823] io scheduler noop registered
[    0.988825] io scheduler anticipatory registered
[    0.988826] io scheduler deadline registered
[    0.988852] io scheduler cfq registered (default)
[    0.988949]   alloc irq_desc for 29 on node -1
[    0.988951]   alloc kstat_irqs on node -1
[    0.988957] pcieport 0000:00:03.0: irq 29 for MSI/MSI-X
[    0.988963] pcieport 0000:00:03.0: setting latency timer to 64
[    0.989043]   alloc irq_desc for 30 on node -1
[    0.989044]   alloc kstat_irqs on node -1
[    0.989049] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
[    0.989056] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.989138]   alloc irq_desc for 31 on node -1
[    0.989139]   alloc kstat_irqs on node -1
[    0.989144] pcieport 0000:00:1c.4: irq 31 for MSI/MSI-X
[    0.989150] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.989233]   alloc irq_desc for 32 on node -1
[    0.989234]   alloc kstat_irqs on node -1
[    0.989239] pcieport 0000:00:1c.5: irq 32 for MSI/MSI-X
[    0.989246] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.989328]   alloc irq_desc for 33 on node -1
[    0.989331]   alloc kstat_irqs on node -1
[    0.989336] pcieport 0000:00:1c.6: irq 33 for MSI/MSI-X
[    0.989342] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.989427]   alloc irq_desc for 34 on node -1
[    0.989428]   alloc kstat_irqs on node -1
[    0.989433] pcieport 0000:00:1c.7: irq 34 for MSI/MSI-X
[    0.989439] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.989497] Firmware did not grant requested _OSC control
[    0.989499] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.989506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.989516] Firmware did not grant requested _OSC control
[    0.989528] Firmware did not grant requested _OSC control
[    0.989537] Firmware did not grant requested _OSC control
[    0.989547] Firmware did not grant requested _OSC control
[    0.989557] Firmware did not grant requested _OSC control
[    0.989576] Firmware did not grant requested _OSC control
[    0.989586] Firmware did not grant requested _OSC control
[    0.989595] Firmware did not grant requested _OSC control
[    0.989605] Firmware did not grant requested _OSC control
[    0.989614] Firmware did not grant requested _OSC control
[    0.989624] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.989690] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.989693] ACPI: Power Button [PWRB]
[    0.989720] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.989722] ACPI: Power Button [PWRF]
[    0.990569] ACPI: SSDT 00000000bf7880c0 01028 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.990901] processor LNXCPU:00: registered as cooling_device0
[    0.990928] processor LNXCPU:01: registered as cooling_device1
[    0.990951] processor LNXCPU:02: registered as cooling_device2
[    0.990974] processor LNXCPU:03: registered as cooling_device3
[    0.994380] Linux agpgart interface v0.103
[    0.994399] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.994489] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.994751] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.995444] brd: module loaded
[    0.995751] loop: module loaded
[    0.995798] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.995850] ata_piix 0000:00:1f.2: version 2.13
[    0.995861]   alloc irq_desc for 21 on node -1
[    0.995864]   alloc kstat_irqs on node -1
[    0.995867] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.995871] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.995897] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.995939] scsi0 : ata_piix
[    0.995987] scsi1 : ata_piix
[    0.997099] ata1: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 21
[    0.997104] ata2: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 21
[    0.997120] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.997133] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.997155] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.997178] scsi2 : ata_piix
[    0.997213] scsi3 : ata_piix
[    0.998135] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 21
[    0.998138] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 21
[    0.998192] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.998197] pata_acpi 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.998216] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.998226] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.998413] Fixed MDIO Bus: probed
[    0.998433] PPP generic driver version 2.4.2
[    0.998453] tun: Universal TUN/TAP device driver, 1.6
[    0.998455] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.998510] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.998522] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.998535] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.998537] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.998556] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.998577] ehci_hcd 0000:00:1a.0: debug port 2
[    1.002449] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    1.002461] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbafe000
[    1.016610] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.016671] usb usb1: configuration #1 chosen from 1 choice
[    1.016689] hub 1-0:1.0: USB hub found
[    1.016694] hub 1-0:1.0: 2 ports detected
[    1.016728]   alloc irq_desc for 23 on node -1
[    1.016729]   alloc kstat_irqs on node -1
[    1.016733] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.016744] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.016746] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.016768] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.016789] ehci_hcd 0000:00:1d.0: debug port 2
[    1.018781] Freeing initrd memory: 8134k freed
[    1.020662] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    1.020677] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbafd000
[    1.036569] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.036687] usb usb2: configuration #1 chosen from 1 choice
[    1.036709] hub 2-0:1.0: USB hub found
[    1.036714] hub 2-0:1.0: 2 ports detected
[    1.036752] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.036763] uhci_hcd: USB Universal Host Controller Interface driver
[    1.036818] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.039393] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.039397] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.039453] mice: PS/2 mouse device common for all mice
[    1.039515] rtc_cmos 00:03: RTC can wake from S4
[    1.039541] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.039565] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.039651] device-mapper: uevent: version 1.0.3
[    1.039723] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.039781] device-mapper: multipath: version 1.1.0 loaded
[    1.039783] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.039912] cpuidle: using governor ladder
[    1.039913] cpuidle: using governor menu
[    1.040174] TCP cubic registered
[    1.040260] NET: Registered protocol family 10
[    1.040607] lo: Disabled Privacy Extensions
[    1.040807] NET: Registered protocol family 17
[    1.041950] PM: Resume from disk failed.
[    1.041961] registered taskstats version 1
[    1.042373]   Magic number: 10:207:994
[    1.042438] rtc_cmos 00:03: setting system clock to 2010-05-01 16:58:07 UTC (1272733087)
[    1.042440] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.042441] EDD information not available.
[    1.059593] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.335874] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.356588] ata4: SATA link down (SStatus 0 SControl 300)
[    1.367287] ata3: SATA link down (SStatus 0 SControl 300)
[    1.485955] usb 1-1: configuration #1 chosen from 1 choice
[    1.486044] hub 1-1:1.0: USB hub found
[    1.486134] hub 1-1:1.0: 6 ports detected
[    1.605263] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.705849] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.705861] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.755266] usb 2-1: configuration #1 chosen from 1 choice
[    1.755354] hub 2-1:1.0: USB hub found
[    1.755447] hub 2-1:1.0: 8 ports detected
[    1.854741] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.854757] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.914746] ata2.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[    1.914749] ata2.00: ATA-7: SAMSUNG HD161HJ, JF100-19, max UDMA7
[    1.914751] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.934695] ata2.01: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.934697] ata2.01: ATA-7: SAMSUNG HD502IJ, 1AA01113, max UDMA7
[    1.934699] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.954764] ata2.00: configured for UDMA/133
[    1.974744] ata2.01: configured for UDMA/133
[    1.974833] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD161HJ  JF10 PQ: 0 ANSI: 5
[    1.974915] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.974917] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.974946] sd 1:0:0:0: [sda] Write Protect is off
[    1.974948] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.974969] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.974984] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    1.975065] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.975073] sd 1:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.975079]  sda: sda1 sda2 sda3 sda4 <
[    1.982619] sd 1:0:1:0: [sdb] Write Protect is off
[    1.982623] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.001280]  sda5 >
[    2.001305] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.001472]  sdb: sdb1 sdb2 sdb3
[    2.011994] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.012103] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.012117] Freeing unused kernel memory: 876k freed
[    2.012242] Write protecting the kernel read-only data: 7680k
[    2.021824] udev: starting version 151
[    2.037183] ahci 0000:03:00.0: version 3.0
[    2.037200] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.049017] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.049032] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.049074] r8169 0000:02:00.0: setting latency timer to 64
[    2.049113]   alloc irq_desc for 35 on node -1
[    2.049114]   alloc kstat_irqs on node -1
[    2.049125] r8169 0000:02:00.0: irq 35 for MSI/MSI-X
[    2.049504] eth0: RTL8168d/8111d at 0xffffc9000065e000, 90:e6:ba:15:d9:58, XID 083000c0 IRQ 35
[    2.063183] ohci1394 0000:07:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.064360] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.064363] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.064368] ahci 0000:03:00.0: setting latency timer to 64
[    2.065066] scsi4 : ahci
[    2.065122] scsi5 : ahci
[    2.065190] ata5: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 18
[    2.065194] ata6: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 18
[    2.065235] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.065258] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    2.065313] scsi6 : pata_jmicron
[    2.065352] scsi7 : pata_jmicron
[    2.065820] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 19
[    2.065822] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 19
[    2.126395] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.254701] ata7.01: ATAPI: HL-DT-STDVD-RAM GSA-H58N, 1.00, max UDMA/66
[    2.294616] ata7.01: configured for UDMA/66
[    2.423397] ata6: SATA link down (SStatus 0 SControl 300)
[    2.423433] ata5: SATA link down (SStatus 0 SControl 300)
[    2.444794] scsi 6:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H58N 1.00 PQ: 0 ANSI: 5
[    2.449245] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.449250] Uniform CD-ROM driver Revision: 3.20
[    2.449351] sr 6:0:1:0: Attached scsi CD-ROM sr0
[    2.449385] sr 6:0:1:0: Attached scsi generic sg2 type 5
[    2.509402] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    3.451152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000a9032d]
[    9.880333] udev: starting version 151
[    9.899309] lp: driver loaded but no devices found
[    9.903928] vga16fb: initializing
[    9.903931] vga16fb: mapped to 0xffff8800000a0000
[    9.903991] fb0: VGA16 VGA frame buffer device
[    9.907331] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.907333] Disabling lock debugging due to kernel taint
[    9.941840] Adding 3908600k swap on /dev/sda5.  Priority:-1 extents:1 across:3908600k 
[    9.983008] [fglrx] Maximum main memory to use for locked dma buffers: 3793 MBytes.
[    9.983119] [fglrx]   vendor: 1002 device: 9490 count: 1
[    9.983356] [fglrx] ioport: bar 4, base 0xb000, size: 0x100
[    9.983366] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.983370] pci 0000:01:00.0: setting latency timer to 64
[    9.983517] [fglrx] Kernel PAT support is enabled
[    9.983529] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[    9.992623] type=1505 audit(1272743896.464:2):  operation="profile_load" pid=682 name="/sbin/dhclient3"
[    9.993009] type=1505 audit(1272743896.464:3):  operation="profile_load" pid=682 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.993218] type=1505 audit(1272743896.464:4):  operation="profile_load" pid=682 name="/usr/lib/connman/scripts/dhclient-script"
[   10.014029] ATK0110 ATK0110:00: EC enabled
[   10.111236] Console: switching to colour frame buffer device 80x30
[   10.131382]   alloc irq_desc for 22 on node -1
[   10.131384]   alloc kstat_irqs on node -1
[   10.131389] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.131426] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.277489] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.277527] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.486995] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   10.512729] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   10.645717] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   10.752608] r8169: eth0: link up
[   10.752612] r8169: eth0: link up
[   10.753171] type=1505 audit(1272743897.224:5):  operation="profile_replace" pid=959 name="/sbin/dhclient3"
[   10.753561] type=1505 audit(1272743897.224:6):  operation="profile_replace" pid=959 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.753774] type=1505 audit(1272743897.224:7):  operation="profile_replace" pid=959 name="/usr/lib/connman/scripts/dhclient-script"
[   10.756575] type=1505 audit(1272743897.234:8):  operation="profile_load" pid=962 name="/usr/lib/cups/backend/cups-pdf"
[   10.757203] type=1505 audit(1272743897.234:9):  operation="profile_load" pid=962 name="/usr/sbin/cupsd"
[   10.758666] type=1505 audit(1272743897.234:10):  operation="profile_load" pid=970 name="/usr/sbin/mysqld-akonadi"
[   10.759732] type=1505 audit(1272743897.234:11):  operation="profile_load" pid=971 name="/usr/sbin/tcpdump"
[   10.992760]   alloc irq_desc for 36 on node -1
[   10.992762]   alloc kstat_irqs on node -1
[   10.992771] fglrx_pci 0000:01:00.0: irq 36 for MSI/MSI-X
[   10.993204] [fglrx] Firegl kernel thread PID: 1014
[   10.993395] [fglrx] IRQ 36 Enabled
[   11.052184] ppdev: user-space parallel port driver
[   11.156611] CPU0 attaching NULL sched-domain.
[   11.156615] CPU1 attaching NULL sched-domain.
[   11.156617] CPU2 attaching NULL sched-domain.
[   11.156618] CPU3 attaching NULL sched-domain.
[   11.243452] CPU0 attaching sched-domain:
[   11.243454]  domain 0: span 0-3 level MC
[   11.243456]   groups: 0 1 2 3
[   11.243460] CPU1 attaching sched-domain:
[   11.243461]  domain 0: span 0-3 level MC
[   11.243463]   groups: 1 2 3 0
[   11.243466] CPU2 attaching sched-domain:
[   11.243467]  domain 0: span 0-3 level MC
[   11.243469]   groups: 2 3 0 1
[   11.243472] CPU3 attaching sched-domain:
[   11.243473]  domain 0: span 0-3 level MC
[   11.243474]   groups: 3 0 1 2
[   11.935425] [fglrx] Gart USWC size:1234 M.
[   11.935428] [fglrx] Gart cacheable size:490 M.
[   11.935432] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   11.935433] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000 
[   11.935435] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   20.487471] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   20.619436] CPU0 attaching NULL sched-domain.
[   20.619443] CPU1 attaching NULL sched-domain.
[   20.619446] CPU2 attaching NULL sched-domain.
[   20.619450] CPU3 attaching NULL sched-domain.
[   20.685470] CPU0 attaching sched-domain:
[   20.685474]  domain 0: span 0-3 level MC
[   20.685478]   groups: 0 1 2 3
[   20.685486] CPU1 attaching sched-domain:
[   20.685489]  domain 0: span 0-3 level MC
[   20.685493]   groups: 1 2 3 0
[   20.685500] CPU2 attaching sched-domain:
[   20.685502]  domain 0: span 0-3 level MC
[   20.685505]   groups: 2 3 0 1
[   20.685512] CPU3 attaching sched-domain:
[   20.685515]  domain 0: span 0-3 level MC
[   20.685518]   groups: 3 0 1 2
[   21.025031] eth0: no IPv6 routers present
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=b463f58c-57a8-4489-bf5b-b523b9381b92 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0FFFE0000 mask FFFFF0000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf770000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf770000 page 4k
[    0.000000] kernel direct mapping tables up to bf770000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
[    0.000000] RAMDISK: 377fe000 - 37fefb37
[    0.000000] ACPI: RSDP 00000000000fb9a0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bf770000 0003C (v01 081909 RSDT1047 20090819 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf770200 00084 (v01 081909 FACP1047 20090819 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf7704a0 0E603 (v01  A1325 A1325001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf788000 00040
[    0.000000] ACPI: APIC 00000000bf770390 000CC (v01 081909 APIC1047 20090819 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf770460 0003C (v01 081909 OEMMCFG  20090819 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf788040 00072 (v01 081909 OEMB1047 20090819 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf77f4a0 00038 (v01 081909 OEMHPET  20090819 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf7890f0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fe000 - 0037fefb37]          RAMDISK ==> [00377fe000 - 0037fefb37]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a2c0]              BRK ==> [0001a2a000 - 0001a2a2c0]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf770
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046271
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765864 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf770000 - 00000000bf788000
[    0.000000] PM: Registered nosave memory: 00000000bf788000 - 00000000bf7dc000
[    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u131072
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028248
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=b463f58c-57a8-4489-bf5b-b523b9381b92 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4041076k/5242880k available (5409k kernel code, 1057796k absent, 144008k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:536
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 25 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 26 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 27 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 28 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2674.477 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5348.95 BogoMIPS (lpj=26744770)
[    0.000019] Security Framework initialized
[    0.000032] AppArmor: AppArmor initialized
[    0.000283] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001043] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001363] Mount-cache hash table entries: 256
[    0.001445] Initializing cgroup subsys ns
[    0.001448] Initializing cgroup subsys cpuacct
[    0.001451] Initializing cgroup subsys memory
[    0.001455] Initializing cgroup subsys devices
[    0.001457] Initializing cgroup subsys freezer
[    0.001458] Initializing cgroup subsys net_cls
[    0.001471] CPU: Physical Processor ID: 0
[    0.001472] CPU: Processor Core ID: 0
[    0.001475] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001477] CPU: L2 cache: 256K
[    0.001478] CPU: L3 cache: 8192K
[    0.001480] CPU 0/0x0 -> Node 0
[    0.001482] mce: CPU supports 9 MCE banks
[    0.001490] CPU0: Thermal monitoring enabled (TM1)
[    0.001493] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 SHD:8
[    0.001500] using mwait in idle threads.
[    0.001501] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
[    0.001505] ... version:                3
[    0.001506] ... bit width:              48
[    0.001507] ... generic registers:      4
[    0.001508] ... value mask:             0000ffffffffffff
[    0.001510] ... max period:             000000007fffffff
[    0.001511] ... fixed-purpose events:   3
[    0.001512] ... event mask:             000000070000000f
[    0.003235] ACPI: Core revision 20090903
[    0.119791] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.119794] ftrace: allocating 22518 entries in 89 pages
[    0.125739] Setting APIC routing to physical flat
[    0.126065] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.225842] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.337939] Booting processor 1 APIC 0x2 ip 0x6000
[    0.348382] Initializing CPU#1
[    0.497515] CPU: Physical Processor ID: 0
[    0.497516] CPU: Processor Core ID: 1
[    0.497518] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.497519] CPU: L2 cache: 256K
[    0.497520] CPU: L3 cache: 8192K
[    0.497522] CPU 1/0x2 -> Node 0
[    0.497530] CPU1: Thermal monitoring enabled (TM1)
[    0.497533] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.497550] CPU1: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.497556] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.517578] Booting processor 2 APIC 0x4 ip 0x6000
[    0.527915] Initializing CPU#2
[    0.677131] CPU: Physical Processor ID: 0
[    0.677132] CPU: Processor Core ID: 2
[    0.677134] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.677135] CPU: L2 cache: 256K
[    0.677136] CPU: L3 cache: 8192K
[    0.677138] CPU 2/0x4 -> Node 0
[    0.677147] CPU2: Thermal monitoring enabled (TM1)
[    0.677150] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.677189] CPU2: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.677195] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.697217] Booting processor 3 APIC 0x6 ip 0x6000
[    0.707554] Initializing CPU#3
[    0.856747] CPU: Physical Processor ID: 0
[    0.856748] CPU: Processor Core ID: 3
[    0.856750] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.856751] CPU: L2 cache: 256K
[    0.856752] CPU: L3 cache: 8192K
[    0.856754] CPU 3/0x6 -> Node 0
[    0.856763] CPU3: Thermal monitoring enabled (TM1)
[    0.856765] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.856828] CPU3: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.856834] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.876803] Brought up 4 CPUs
[    0.876805] Total of 4 processors activated (21398.54 BogoMIPS).
[    0.878059] CPU0 attaching sched-domain:
[    0.878062]  domain 0: span 0-3 level MC
[    0.878064]   groups: 0 1 2 3
[    0.878069] CPU1 attaching sched-domain:
[    0.878070]  domain 0: span 0-3 level MC
[    0.878071]   groups: 1 2 3 0
[    0.878075] CPU2 attaching sched-domain:
[    0.878076]  domain 0: span 0-3 level MC
[    0.878077]   groups: 2 3 0 1
[    0.878080] CPU3 attaching sched-domain:
[    0.878082]  domain 0: span 0-3 level MC
[    0.878083]   groups: 3 0 1 2
[    0.878247] devtmpfs: initialized
[    0.878490] regulator: core version 0.5
[    0.878513] Time: 16:58:06  Date: 05/01/10
[    0.878546] NET: Registered protocol family 16
[    0.878611] Trying to unpack rootfs image as initramfs...
[    0.878633] ACPI: bus type pci registered
[    0.878683] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.878685] PCI: Not using MMCONFIG.
[    0.878686] PCI: Using configuration type 1 for base access
[    0.879215] bio: create slab <bio-0> at 0
[    0.880007] ACPI: EC: Look up EC in DSDT
[    0.881277] ACPI: Executed 1 blocks of module-level executable AML code
[    0.893085] ACPI: Interpreter enabled
[    0.893088] ACPI: (supports S0 S1 S3 S4 S5)
[    0.893105] ACPI: Using IOAPIC for interrupt routing
[    0.893150] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.896003] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.900989] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.909620] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.909690] ACPI Warning: Incorrect checksum in table [OEMB] - F3, should be F2 (20090903/tbutils-314)
[    0.909800] ACPI: No dock devices found.
[    0.910080] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.910182] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.910185] pci 0000:00:03.0: PME# disabled
[    0.910429] pci 0000:00:1a.0: reg 10 32bit mmio: [0xfbafe000-0xfbafe3ff]
[    0.910477] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.910481] pci 0000:00:1a.0: PME# disabled
[    0.910517] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbaf8000-0xfbafbfff]
[    0.910553] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.910556] pci 0000:00:1b.0: PME# disabled
[    0.910610] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.910613] pci 0000:00:1c.0: PME# disabled
[    0.910670] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.910673] pci 0000:00:1c.4: PME# disabled
[    0.910727] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.910730] pci 0000:00:1c.5: PME# disabled
[    0.910784] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.910787] pci 0000:00:1c.6: PME# disabled
[    0.910842] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.910845] pci 0000:00:1c.7: PME# disabled
[    0.910889] pci 0000:00:1d.0: reg 10 32bit mmio: [0xfbafd000-0xfbafd3ff]
[    0.910937] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.910941] pci 0000:00:1d.0: PME# disabled
[    0.911095] pci 0000:00:1f.2: reg 10 io port: [0x9c00-0x9c07]
[    0.911100] pci 0000:00:1f.2: reg 14 io port: [0x9880-0x9883]
[    0.911105] pci 0000:00:1f.2: reg 18 io port: [0x9800-0x9807]
[    0.911109] pci 0000:00:1f.2: reg 1c io port: [0x9480-0x9483]
[    0.911114] pci 0000:00:1f.2: reg 20 io port: [0x9400-0x940f]
[    0.911118] pci 0000:00:1f.2: reg 24 io port: [0x9080-0x908f]
[    0.911158] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfbafc000-0xfbafc0ff]
[    0.911169] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.911207] pci 0000:00:1f.5: reg 10 io port: [0xac00-0xac07]
[    0.911211] pci 0000:00:1f.5: reg 14 io port: [0xa880-0xa883]
[    0.911216] pci 0000:00:1f.5: reg 18 io port: [0xa800-0xa807]
[    0.911220] pci 0000:00:1f.5: reg 1c io port: [0xa480-0xa483]
[    0.911225] pci 0000:00:1f.5: reg 20 io port: [0xa400-0xa40f]
[    0.911230] pci 0000:00:1f.5: reg 24 io port: [0xa080-0xa08f]
[    0.911280] pci 0000:01:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.911287] pci 0000:01:00.0: reg 18 64bit mmio: [0xfbbe0000-0xfbbeffff]
[    0.911292] pci 0000:01:00.0: reg 20 io port: [0xb000-0xb0ff]
[    0.911299] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbbc0000-0xfbbdffff]
[    0.911316] pci 0000:01:00.0: supports D1 D2
[    0.911344] pci 0000:01:00.1: reg 10 64bit mmio: [0xfbbfc000-0xfbbfffff]
[    0.911375] pci 0000:01:00.1: supports D1 D2
[    0.911403] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
[    0.911406] pci 0000:00:03.0: bridge 32bit mmio: [0xfbb00000-0xfbbfffff]
[    0.911410] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.911607] pci 0000:03:00.0: reg 24 32bit mmio: [0xfbdfe000-0xfbdfffff]
[    0.911643] pci 0000:03:00.0: PME# supported from D3hot
[    0.911647] pci 0000:03:00.0: PME# disabled
[    0.911696] pci 0000:03:00.1: reg 10 io port: [0xdc00-0xdc07]
[    0.911704] pci 0000:03:00.1: reg 14 io port: [0xd880-0xd883]
[    0.911712] pci 0000:03:00.1: reg 18 io port: [0xd800-0xd807]
[    0.911720] pci 0000:03:00.1: reg 1c io port: [0xd480-0xd483]
[    0.911728] pci 0000:03:00.1: reg 20 io port: [0xd400-0xd40f]
[    0.911811] pci 0000:00:1c.6: bridge io port: [0xd000-0xdfff]
[    0.911814] pci 0000:00:1c.6: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]
[    0.911860] pci 0000:02:00.0: reg 10 io port: [0xc800-0xc8ff]
[    0.911879] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfafff000-0xfaffffff]
[    0.911891] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfaff8000-0xfaffbfff]
[    0.911899] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfbcf0000-0xfbcfffff]
[    0.911935] pci 0000:02:00.0: supports D1 D2
[    0.911936] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.911940] pci 0000:02:00.0: PME# disabled
[    0.911992] pci 0000:00:1c.7: bridge io port: [0xc000-0xcfff]
[    0.911995] pci 0000:00:1c.7: bridge 32bit mmio: [0xfbc00000-0xfbcfffff]
[    0.912000] pci 0000:00:1c.7: bridge 64bit mmio pref: [0xfaf00000-0xfaffffff]
[    0.912034] pci 0000:07:03.0: reg 10 32bit mmio: [0xfbeff800-0xfbefffff]
[    0.912040] pci 0000:07:03.0: reg 14 io port: [0xec00-0xec7f]
[    0.912079] pci 0000:07:03.0: supports D2
[    0.912081] pci 0000:07:03.0: PME# supported from D2 D3hot D3cold
[    0.912084] pci 0000:07:03.0: PME# disabled
[    0.912122] pci 0000:00:1e.0: transparent bridge
[    0.912125] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.912128] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.912158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.912312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.912415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.912472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.912522] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.912571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
[    0.912620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    0.912680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    0.933863] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.933974] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.934082] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.934192] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.934301] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.934411] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.934521] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.934630] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.934722] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.934725] vgaarb: loaded
[    0.934795] SCSI subsystem initialized
[    0.934867] libata version 3.00 loaded.
[    0.934914] usbcore: registered new interface driver usbfs
[    0.934921] usbcore: registered new interface driver hub
[    0.934937] usbcore: registered new device driver usb
[    0.935031] ACPI: WMI: Mapper loaded
[    0.935032] PCI: Using ACPI for IRQ routing
[    0.935159] NetLabel: Initializing
[    0.935160] NetLabel:  domain hash size = 128
[    0.935161] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.935172] NetLabel:  unlabeled traffic allowed by default
[    0.935199] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    0.935203] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.946568] hpet: hpet2 irq 24 for MSI
[    0.946720] hpet: hpet3 irq 25 for MSI
[    0.956624] hpet: hpet4 irq 26 for MSI
[    0.966629] hpet: hpet5 irq 27 for MSI
[    0.966640] Switching to clocksource tsc
[    0.967808] AppArmor: AppArmor Filesystem Enabled
[    0.967820] pnp: PnP ACPI init
[    0.967830] ACPI: bus type pnp registered
[    0.970592] pnp: PnP ACPI: found 17 devices
[    0.970594] ACPI: ACPI bus type pnp unregistered
[    0.970601] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    0.970603] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    0.970605] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    0.970607] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.970612] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.970616] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.970618] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.970620] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.970622] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.970624] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.970626] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.970629] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.970633] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.970635] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.970639] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.970642] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.970644] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.970646] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.970648] system 00:10: iomem range 0x100000-0xbfffffff could not be reserved
[    0.970650] system 00:10: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.975315] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.975317] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
[    0.975320] pci 0000:00:03.0:   MEM window: 0xfbb00000-0xfbbfffff
[    0.975323] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.975327] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
[    0.975329] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.975333] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.975336] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.975341] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
[    0.975343] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.975347] pci 0000:00:1c.4:   MEM window: 0xc0400000-0xc05fffff
[    0.975350] pci 0000:00:1c.4:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    0.975355] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.975357] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
[    0.975360] pci 0000:00:1c.5:   MEM window: 0xc0800000-0xc09fffff
[    0.975364] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
[    0.975369] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03
[    0.975371] pci 0000:00:1c.6:   IO window: 0xd000-0xdfff
[    0.975374] pci 0000:00:1c.6:   MEM window: 0xfbd00000-0xfbdfffff
[    0.975378] pci 0000:00:1c.6:   PREFETCH window: 0x000000c0c00000-0x000000c0dfffff
[    0.975382] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02
[    0.975385] pci 0000:00:1c.7:   IO window: 0xc000-0xcfff
[    0.975388] pci 0000:00:1c.7:   MEM window: 0xfbc00000-0xfbcfffff
[    0.975391] pci 0000:00:1c.7:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.975396] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.975398] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.975402] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.975405] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.975416]   alloc irq_desc for 16 on node -1
[    0.975417]   alloc kstat_irqs on node -1
[    0.975421] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.975424] pci 0000:00:03.0: setting latency timer to 64
[    0.975430] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.975432]   alloc irq_desc for 17 on node -1
[    0.975433]   alloc kstat_irqs on node -1
[    0.975436] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.975439] pci 0000:00:1c.0: setting latency timer to 64
[    0.975445] pci 0000:00:1c.4: enabling device (0104 -> 0107)
[    0.975447] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.975450] pci 0000:00:1c.4: setting latency timer to 64
[    0.975456] pci 0000:00:1c.5: enabling device (0104 -> 0107)
[    0.975459] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.975462] pci 0000:00:1c.5: setting latency timer to 64
[    0.975468]   alloc irq_desc for 18 on node -1
[    0.975472]   alloc kstat_irqs on node -1
[    0.975474] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.975477] pci 0000:00:1c.6: setting latency timer to 64
[    0.975483]   alloc irq_desc for 19 on node -1
[    0.975484]   alloc kstat_irqs on node -1
[    0.975487] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.975490] pci 0000:00:1c.7: setting latency timer to 64
[    0.975494] pci 0000:00:1e.0: setting latency timer to 64
[    0.975498] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.975499] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.975501] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.975503] pci_bus 0000:01: resource 1 mem: [0xfbb00000-0xfbbfffff]
[    0.975504] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.975506] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.975508] pci_bus 0000:06: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.975509] pci_bus 0000:06: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.975511] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
[    0.975513] pci_bus 0000:05: resource 1 mem: [0xc0400000-0xc05fffff]
[    0.975514] pci_bus 0000:05: resource 2 pref mem [0xc0600000-0xc07fffff]
[    0.975516] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.975517] pci_bus 0000:04: resource 1 mem: [0xc0800000-0xc09fffff]
[    0.975519] pci_bus 0000:04: resource 2 pref mem [0xc0a00000-0xc0bfffff]
[    0.975521] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.975522] pci_bus 0000:03: resource 1 mem: [0xfbd00000-0xfbdfffff]
[    0.975524] pci_bus 0000:03: resource 2 pref mem [0xc0c00000-0xc0dfffff]
[    0.975526] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.975527] pci_bus 0000:02: resource 1 mem: [0xfbc00000-0xfbcfffff]
[    0.975529] pci_bus 0000:02: resource 2 pref mem [0xfaf00000-0xfaffffff]
[    0.975530] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
[    0.975532] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.975534] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.975535] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.975558] NET: Registered protocol family 2
[    0.975683] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.976416] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.978710] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.978989] TCP: Hash tables configured (established 524288 bind 65536)
[    0.978991] TCP reno registered
[    0.979077] NET: Registered protocol family 1
[    0.979140] pci 0000:01:00.0: Boot video device
[    0.979380] Scanning for low memory corruption every 60 seconds
[    0.979465] audit: initializing netlink socket (disabled)
[    0.979472] type=2000 audit(1272733086.739:1): initialized
[    0.987125] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.988104] VFS: Disk quotas dquot_6.5.2
[    0.988143] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.988576] fuse init (API version 7.13)
[    0.988632] msgmni has been set to 7892
[    0.988784] alg: No test for stdrng (krng)
[    0.988821] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.988823] io scheduler noop registered
[    0.988825] io scheduler anticipatory registered
[    0.988826] io scheduler deadline registered
[    0.988852] io scheduler cfq registered (default)
[    0.988949]   alloc irq_desc for 29 on node -1
[    0.988951]   alloc kstat_irqs on node -1
[    0.988957] pcieport 0000:00:03.0: irq 29 for MSI/MSI-X
[    0.988963] pcieport 0000:00:03.0: setting latency timer to 64
[    0.989043]   alloc irq_desc for 30 on node -1
[    0.989044]   alloc kstat_irqs on node -1
[    0.989049] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
[    0.989056] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.989138]   alloc irq_desc for 31 on node -1
[    0.989139]   alloc kstat_irqs on node -1
[    0.989144] pcieport 0000:00:1c.4: irq 31 for MSI/MSI-X
[    0.989150] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.989233]   alloc irq_desc for 32 on node -1
[    0.989234]   alloc kstat_irqs on node -1
[    0.989239] pcieport 0000:00:1c.5: irq 32 for MSI/MSI-X
[    0.989246] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.989328]   alloc irq_desc for 33 on node -1
[    0.989331]   alloc kstat_irqs on node -1
[    0.989336] pcieport 0000:00:1c.6: irq 33 for MSI/MSI-X
[    0.989342] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.989427]   alloc irq_desc for 34 on node -1
[    0.989428]   alloc kstat_irqs on node -1
[    0.989433] pcieport 0000:00:1c.7: irq 34 for MSI/MSI-X
[    0.989439] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.989497] Firmware did not grant requested _OSC control
[    0.989499] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.989506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.989516] Firmware did not grant requested _OSC control
[    0.989528] Firmware did not grant requested _OSC control
[    0.989537] Firmware did not grant requested _OSC control
[    0.989547] Firmware did not grant requested _OSC control
[    0.989557] Firmware did not grant requested _OSC control
[    0.989576] Firmware did not grant requested _OSC control
[    0.989586] Firmware did not grant requested _OSC control
[    0.989595] Firmware did not grant requested _OSC control
[    0.989605] Firmware did not grant requested _OSC control
[    0.989614] Firmware did not grant requested _OSC control
[    0.989624] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.989690] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.989693] ACPI: Power Button [PWRB]
[    0.989720] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.989722] ACPI: Power Button [PWRF]
[    0.990569] ACPI: SSDT 00000000bf7880c0 01028 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.990901] processor LNXCPU:00: registered as cooling_device0
[    0.990928] processor LNXCPU:01: registered as cooling_device1
[    0.990951] processor LNXCPU:02: registered as cooling_device2
[    0.990974] processor LNXCPU:03: registered as cooling_device3
[    0.994380] Linux agpgart interface v0.103
[    0.994399] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.994489] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.994751] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.995444] brd: module loaded
[    0.995751] loop: module loaded
[    0.995798] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.995850] ata_piix 0000:00:1f.2: version 2.13
[    0.995861]   alloc irq_desc for 21 on node -1
[    0.995864]   alloc kstat_irqs on node -1
[    0.995867] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.995871] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.995897] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.995939] scsi0 : ata_piix
[    0.995987] scsi1 : ata_piix
[    0.997099] ata1: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 21
[    0.997104] ata2: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 21
[    0.997120] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.997133] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.997155] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.997178] scsi2 : ata_piix
[    0.997213] scsi3 : ata_piix
[    0.998135] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 21
[    0.998138] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 21
[    0.998192] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.998197] pata_acpi 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.998216] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.998226] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.998413] Fixed MDIO Bus: probed
[    0.998433] PPP generic driver version 2.4.2
[    0.998453] tun: Universal TUN/TAP device driver, 1.6
[    0.998455] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.998510] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.998522] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.998535] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.998537] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.998556] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.998577] ehci_hcd 0000:00:1a.0: debug port 2
[    1.002449] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    1.002461] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbafe000
[    1.016610] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.016671] usb usb1: configuration #1 chosen from 1 choice
[    1.016689] hub 1-0:1.0: USB hub found
[    1.016694] hub 1-0:1.0: 2 ports detected
[    1.016728]   alloc irq_desc for 23 on node -1
[    1.016729]   alloc kstat_irqs on node -1
[    1.016733] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.016744] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.016746] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.016768] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.016789] ehci_hcd 0000:00:1d.0: debug port 2
[    1.018781] Freeing initrd memory: 8134k freed
[    1.020662] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    1.020677] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbafd000
[    1.036569] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.036687] usb usb2: configuration #1 chosen from 1 choice
[    1.036709] hub 2-0:1.0: USB hub found
[    1.036714] hub 2-0:1.0: 2 ports detected
[    1.036752] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.036763] uhci_hcd: USB Universal Host Controller Interface driver
[    1.036818] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.039393] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.039397] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.039453] mice: PS/2 mouse device common for all mice
[    1.039515] rtc_cmos 00:03: RTC can wake from S4
[    1.039541] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.039565] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.039651] device-mapper: uevent: version 1.0.3
[    1.039723] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.039781] device-mapper: multipath: version 1.1.0 loaded
[    1.039783] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.039912] cpuidle: using governor ladder
[    1.039913] cpuidle: using governor menu
[    1.040174] TCP cubic registered
[    1.040260] NET: Registered protocol family 10
[    1.040607] lo: Disabled Privacy Extensions
[    1.040807] NET: Registered protocol family 17
[    1.041950] PM: Resume from disk failed.
[    1.041961] registered taskstats version 1
[    1.042373]   Magic number: 10:207:994
[    1.042438] rtc_cmos 00:03: setting system clock to 2010-05-01 16:58:07 UTC (1272733087)
[    1.042440] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.042441] EDD information not available.
[    1.059593] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.335874] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.356588] ata4: SATA link down (SStatus 0 SControl 300)
[    1.367287] ata3: SATA link down (SStatus 0 SControl 300)
[    1.485955] usb 1-1: configuration #1 chosen from 1 choice
[    1.486044] hub 1-1:1.0: USB hub found
[    1.486134] hub 1-1:1.0: 6 ports detected
[    1.605263] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.705849] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.705861] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.755266] usb 2-1: configuration #1 chosen from 1 choice
[    1.755354] hub 2-1:1.0: USB hub found
[    1.755447] hub 2-1:1.0: 8 ports detected
[    1.854741] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.854757] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.914746] ata2.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[    1.914749] ata2.00: ATA-7: SAMSUNG HD161HJ, JF100-19, max UDMA7
[    1.914751] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.934695] ata2.01: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.934697] ata2.01: ATA-7: SAMSUNG HD502IJ, 1AA01113, max UDMA7
[    1.934699] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.954764] ata2.00: configured for UDMA/133
[    1.974744] ata2.01: configured for UDMA/133
[    1.974833] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD161HJ  JF10 PQ: 0 ANSI: 5
[    1.974915] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.974917] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.974946] sd 1:0:0:0: [sda] Write Protect is off
[    1.974948] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.974969] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.974984] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    1.975065] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.975073] sd 1:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.975079]  sda: sda1 sda2 sda3 sda4 <
[    1.982619] sd 1:0:1:0: [sdb] Write Protect is off
[    1.982623] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.001280]  sda5 >
[    2.001305] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.001472]  sdb: sdb1 sdb2 sdb3
[    2.011994] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.012103] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.012117] Freeing unused kernel memory: 876k freed
[    2.012242] Write protecting the kernel read-only data: 7680k
[    2.021824] udev: starting version 151
[    2.037183] ahci 0000:03:00.0: version 3.0
[    2.037200] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.049017] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.049032] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.049074] r8169 0000:02:00.0: setting latency timer to 64
[    2.049113]   alloc irq_desc for 35 on node -1
[    2.049114]   alloc kstat_irqs on node -1
[    2.049125] r8169 0000:02:00.0: irq 35 for MSI/MSI-X
[    2.049504] eth0: RTL8168d/8111d at 0xffffc9000065e000, 90:e6:ba:15:d9:58, XID 083000c0 IRQ 35
[    2.063183] ohci1394 0000:07:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.064360] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.064363] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.064368] ahci 0000:03:00.0: setting latency timer to 64
[    2.065066] scsi4 : ahci
[    2.065122] scsi5 : ahci
[    2.065190] ata5: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 18
[    2.065194] ata6: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 18
[    2.065235] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.065258] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    2.065313] scsi6 : pata_jmicron
[    2.065352] scsi7 : pata_jmicron
[    2.065820] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 19
[    2.065822] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 19
[    2.126395] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.254701] ata7.01: ATAPI: HL-DT-STDVD-RAM GSA-H58N, 1.00, max UDMA/66
[    2.294616] ata7.01: configured for UDMA/66
[    2.423397] ata6: SATA link down (SStatus 0 SControl 300)
[    2.423433] ata5: SATA link down (SStatus 0 SControl 300)
[    2.444794] scsi 6:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H58N 1.00 PQ: 0 ANSI: 5
[    2.449245] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.449250] Uniform CD-ROM driver Revision: 3.20
[    2.449351] sr 6:0:1:0: Attached scsi CD-ROM sr0
[    2.449385] sr 6:0:1:0: Attached scsi generic sg2 type 5
[    2.509402] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    3.451152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000a9032d]
[    9.880333] udev: starting version 151
[    9.899309] lp: driver loaded but no devices found
[    9.903928] vga16fb: initializing
[    9.903931] vga16fb: mapped to 0xffff8800000a0000
[    9.903991] fb0: VGA16 VGA frame buffer device
[    9.907331] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.907333] Disabling lock debugging due to kernel taint
[    9.941840] Adding 3908600k swap on /dev/sda5.  Priority:-1 extents:1 across:3908600k 
[    9.983008] [fglrx] Maximum main memory to use for locked dma buffers: 3793 MBytes.
[    9.983119] [fglrx]   vendor: 1002 device: 9490 count: 1
[    9.983356] [fglrx] ioport: bar 4, base 0xb000, size: 0x100
[    9.983366] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.983370] pci 0000:01:00.0: setting latency timer to 64
[    9.983517] [fglrx] Kernel PAT support is enabled
[    9.983529] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[    9.992623] type=1505 audit(1272743896.464:2):  operation="profile_load" pid=682 name="/sbin/dhclient3"
[    9.993009] type=1505 audit(1272743896.464:3):  operation="profile_load" pid=682 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.993218] type=1505 audit(1272743896.464:4):  operation="profile_load" pid=682 name="/usr/lib/connman/scripts/dhclient-script"
[   10.014029] ATK0110 ATK0110:00: EC enabled
[   10.111236] Console: switching to colour frame buffer device 80x30
[   10.131382]   alloc irq_desc for 22 on node -1
[   10.131384]   alloc kstat_irqs on node -1
[   10.131389] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.131426] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.277489] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.277527] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.486995] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   10.512729] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   10.645717] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   10.752608] r8169: eth0: link up
[   10.752612] r8169: eth0: link up
[   10.753171] type=1505 audit(1272743897.224:5):  operation="profile_replace" pid=959 name="/sbin/dhclient3"
[   10.753561] type=1505 audit(1272743897.224:6):  operation="profile_replace" pid=959 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.753774] type=1505 audit(1272743897.224:7):  operation="profile_replace" pid=959 name="/usr/lib/connman/scripts/dhclient-script"
[   10.756575] type=1505 audit(1272743897.234:8):  operation="profile_load" pid=962 name="/usr/lib/cups/backend/cups-pdf"
[   10.757203] type=1505 audit(1272743897.234:9):  operation="profile_load" pid=962 name="/usr/sbin/cupsd"
[   10.758666] type=1505 audit(1272743897.234:10):  operation="profile_load" pid=970 name="/usr/sbin/mysqld-akonadi"
[   10.759732] type=1505 audit(1272743897.234:11):  operation="profile_load" pid=971 name="/usr/sbin/tcpdump"
[   10.992760]   alloc irq_desc for 36 on node -1
[   10.992762]   alloc kstat_irqs on node -1
[   10.992771] fglrx_pci 0000:01:00.0: irq 36 for MSI/MSI-X
[   10.993204] [fglrx] Firegl kernel thread PID: 1014
[   10.993395] [fglrx] IRQ 36 Enabled
[   11.052184] ppdev: user-space parallel port driver
[   11.156611] CPU0 attaching NULL sched-domain.
[   11.156615] CPU1 attaching NULL sched-domain.
[   11.156617] CPU2 attaching NULL sched-domain.
[   11.156618] CPU3 attaching NULL sched-domain.
[   11.243452] CPU0 attaching sched-domain:
[   11.243454]  domain 0: span 0-3 level MC
[   11.243456]   groups: 0 1 2 3
[   11.243460] CPU1 attaching sched-domain:
[   11.243461]  domain 0: span 0-3 level MC
[   11.243463]   groups: 1 2 3 0
[   11.243466] CPU2 attaching sched-domain:
[   11.243467]  domain 0: span 0-3 level MC
[   11.243469]   groups: 2 3 0 1
[   11.243472] CPU3 attaching sched-domain:
[   11.243473]  domain 0: span 0-3 level MC
[   11.243474]   groups: 3 0 1 2
[   11.935425] [fglrx] Gart USWC size:1234 M.
[   11.935428] [fglrx] Gart cacheable size:490 M.
[   11.935432] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   11.935433] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000 
[   11.935435] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   20.487471] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   20.619436] CPU0 attaching NULL sched-domain.
[   20.619443] CPU1 attaching NULL sched-domain.
[   20.619446] CPU2 attaching NULL sched-domain.
[   20.619450] CPU3 attaching NULL sched-domain.
[   20.685470] CPU0 attaching sched-domain:
[   20.685474]  domain 0: span 0-3 level MC
[   20.685478]   groups: 0 1 2 3
[   20.685486] CPU1 attaching sched-domain:
[   20.685489]  domain 0: span 0-3 level MC
[   20.685493]   groups: 1 2 3 0
[   20.685500] CPU2 attaching sched-domain:
[   20.685502]  domain 0: span 0-3 level MC
[   20.685505]   groups: 2 3 0 1
[   20.685512] CPU3 attaching sched-domain:
[   20.685515]  domain 0: span 0-3 level MC
[   20.685518]   groups: 3 0 1 2
[   21.025031] eth0: no IPv6 routers present
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=b463f58c-57a8-4489-bf5b-b523b9381b92 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0FFFE0000 mask FFFFF0000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf770000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf770000 page 4k
[    0.000000] kernel direct mapping tables up to bf770000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
[    0.000000] RAMDISK: 377fe000 - 37fefb37
[    0.000000] ACPI: RSDP 00000000000fb9a0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bf770000 0003C (v01 081909 RSDT1047 20090819 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf770200 00084 (v01 081909 FACP1047 20090819 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf7704a0 0E603 (v01  A1325 A1325001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf788000 00040
[    0.000000] ACPI: APIC 00000000bf770390 000CC (v01 081909 APIC1047 20090819 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf770460 0003C (v01 081909 OEMMCFG  20090819 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf788040 00072 (v01 081909 OEMB1047 20090819 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf77f4a0 00038 (v01 081909 OEMHPET  20090819 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf7890f0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fe000 - 0037fefb37]          RAMDISK ==> [00377fe000 - 0037fefb37]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a2c0]              BRK ==> [0001a2a000 - 0001a2a2c0]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf770
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046271
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765864 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf770000 - 00000000bf788000
[    0.000000] PM: Registered nosave memory: 00000000bf788000 - 00000000bf7dc000
[    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u131072
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028248
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=b463f58c-57a8-4489-bf5b-b523b9381b92 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4041076k/5242880k available (5409k kernel code, 1057796k absent, 144008k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:536
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 25 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 26 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 27 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 28 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2674.477 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5348.95 BogoMIPS (lpj=26744770)
[    0.000019] Security Framework initialized
[    0.000032] AppArmor: AppArmor initialized
[    0.000283] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001043] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001363] Mount-cache hash table entries: 256
[    0.001445] Initializing cgroup subsys ns
[    0.001448] Initializing cgroup subsys cpuacct
[    0.001451] Initializing cgroup subsys memory
[    0.001455] Initializing cgroup subsys devices
[    0.001457] Initializing cgroup subsys freezer
[    0.001458] Initializing cgroup subsys net_cls
[    0.001471] CPU: Physical Processor ID: 0
[    0.001472] CPU: Processor Core ID: 0
[    0.001475] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001477] CPU: L2 cache: 256K
[    0.001478] CPU: L3 cache: 8192K
[    0.001480] CPU 0/0x0 -> Node 0
[    0.001482] mce: CPU supports 9 MCE banks
[    0.001490] CPU0: Thermal monitoring enabled (TM1)
[    0.001493] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 SHD:8
[    0.001500] using mwait in idle threads.
[    0.001501] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
[    0.001505] ... version:                3
[    0.001506] ... bit width:              48
[    0.001507] ... generic registers:      4
[    0.001508] ... value mask:             0000ffffffffffff
[    0.001510] ... max period:             000000007fffffff
[    0.001511] ... fixed-purpose events:   3
[    0.001512] ... event mask:             000000070000000f
[    0.003235] ACPI: Core revision 20090903
[    0.119791] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.119794] ftrace: allocating 22518 entries in 89 pages
[    0.125739] Setting APIC routing to physical flat
[    0.126065] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.225842] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.337939] Booting processor 1 APIC 0x2 ip 0x6000
[    0.348382] Initializing CPU#1
[    0.497515] CPU: Physical Processor ID: 0
[    0.497516] CPU: Processor Core ID: 1
[    0.497518] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.497519] CPU: L2 cache: 256K
[    0.497520] CPU: L3 cache: 8192K
[    0.497522] CPU 1/0x2 -> Node 0
[    0.497530] CPU1: Thermal monitoring enabled (TM1)
[    0.497533] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.497550] CPU1: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.497556] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.517578] Booting processor 2 APIC 0x4 ip 0x6000
[    0.527915] Initializing CPU#2
[    0.677131] CPU: Physical Processor ID: 0
[    0.677132] CPU: Processor Core ID: 2
[    0.677134] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.677135] CPU: L2 cache: 256K
[    0.677136] CPU: L3 cache: 8192K
[    0.677138] CPU 2/0x4 -> Node 0
[    0.677147] CPU2: Thermal monitoring enabled (TM1)
[    0.677150] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.677189] CPU2: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.677195] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.697217] Booting processor 3 APIC 0x6 ip 0x6000
[    0.707554] Initializing CPU#3
[    0.856747] CPU: Physical Processor ID: 0
[    0.856748] CPU: Processor Core ID: 3
[    0.856750] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.856751] CPU: L2 cache: 256K
[    0.856752] CPU: L3 cache: 8192K
[    0.856754] CPU 3/0x6 -> Node 0
[    0.856763] CPU3: Thermal monitoring enabled (TM1)
[    0.856765] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.856828] CPU3: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.856834] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.876803] Brought up 4 CPUs
[    0.876805] Total of 4 processors activated (21398.54 BogoMIPS).
[    0.878059] CPU0 attaching sched-domain:
[    0.878062]  domain 0: span 0-3 level MC
[    0.878064]   groups: 0 1 2 3
[    0.878069] CPU1 attaching sched-domain:
[    0.878070]  domain 0: span 0-3 level MC
[    0.878071]   groups: 1 2 3 0
[    0.878075] CPU2 attaching sched-domain:
[    0.878076]  domain 0: span 0-3 level MC
[    0.878077]   groups: 2 3 0 1
[    0.878080] CPU3 attaching sched-domain:
[    0.878082]  domain 0: span 0-3 level MC
[    0.878083]   groups: 3 0 1 2
[    0.878247] devtmpfs: initialized
[    0.878490] regulator: core version 0.5
[    0.878513] Time: 16:58:06  Date: 05/01/10
[    0.878546] NET: Registered protocol family 16
[    0.878611] Trying to unpack rootfs image as initramfs...
[    0.878633] ACPI: bus type pci registered
[    0.878683] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.878685] PCI: Not using MMCONFIG.
[    0.878686] PCI: Using configuration type 1 for base access
[    0.879215] bio: create slab <bio-0> at 0
[    0.880007] ACPI: EC: Look up EC in DSDT
[    0.881277] ACPI: Executed 1 blocks of module-level executable AML code
[    0.893085] ACPI: Interpreter enabled
[    0.893088] ACPI: (supports S0 S1 S3 S4 S5)
[    0.893105] ACPI: Using IOAPIC for interrupt routing
[    0.893150] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.896003] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.900989] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.909620] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.909690] ACPI Warning: Incorrect checksum in table [OEMB] - F3, should be F2 (20090903/tbutils-314)
[    0.909800] ACPI: No dock devices found.
[    0.910080] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.910182] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.910185] pci 0000:00:03.0: PME# disabled
[    0.910429] pci 0000:00:1a.0: reg 10 32bit mmio: [0xfbafe000-0xfbafe3ff]
[    0.910477] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.910481] pci 0000:00:1a.0: PME# disabled
[    0.910517] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbaf8000-0xfbafbfff]
[    0.910553] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.910556] pci 0000:00:1b.0: PME# disabled
[    0.910610] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.910613] pci 0000:00:1c.0: PME# disabled
[    0.910670] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.910673] pci 0000:00:1c.4: PME# disabled
[    0.910727] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.910730] pci 0000:00:1c.5: PME# disabled
[    0.910784] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.910787] pci 0000:00:1c.6: PME# disabled
[    0.910842] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.910845] pci 0000:00:1c.7: PME# disabled
[    0.910889] pci 0000:00:1d.0: reg 10 32bit mmio: [0xfbafd000-0xfbafd3ff]
[    0.910937] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.910941] pci 0000:00:1d.0: PME# disabled
[    0.911095] pci 0000:00:1f.2: reg 10 io port: [0x9c00-0x9c07]
[    0.911100] pci 0000:00:1f.2: reg 14 io port: [0x9880-0x9883]
[    0.911105] pci 0000:00:1f.2: reg 18 io port: [0x9800-0x9807]
[    0.911109] pci 0000:00:1f.2: reg 1c io port: [0x9480-0x9483]
[    0.911114] pci 0000:00:1f.2: reg 20 io port: [0x9400-0x940f]
[    0.911118] pci 0000:00:1f.2: reg 24 io port: [0x9080-0x908f]
[    0.911158] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfbafc000-0xfbafc0ff]
[    0.911169] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.911207] pci 0000:00:1f.5: reg 10 io port: [0xac00-0xac07]
[    0.911211] pci 0000:00:1f.5: reg 14 io port: [0xa880-0xa883]
[    0.911216] pci 0000:00:1f.5: reg 18 io port: [0xa800-0xa807]
[    0.911220] pci 0000:00:1f.5: reg 1c io port: [0xa480-0xa483]
[    0.911225] pci 0000:00:1f.5: reg 20 io port: [0xa400-0xa40f]
[    0.911230] pci 0000:00:1f.5: reg 24 io port: [0xa080-0xa08f]
[    0.911280] pci 0000:01:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.911287] pci 0000:01:00.0: reg 18 64bit mmio: [0xfbbe0000-0xfbbeffff]
[    0.911292] pci 0000:01:00.0: reg 20 io port: [0xb000-0xb0ff]
[    0.911299] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbbc0000-0xfbbdffff]
[    0.911316] pci 0000:01:00.0: supports D1 D2
[    0.911344] pci 0000:01:00.1: reg 10 64bit mmio: [0xfbbfc000-0xfbbfffff]
[    0.911375] pci 0000:01:00.1: supports D1 D2
[    0.911403] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
[    0.911406] pci 0000:00:03.0: bridge 32bit mmio: [0xfbb00000-0xfbbfffff]
[    0.911410] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.911607] pci 0000:03:00.0: reg 24 32bit mmio: [0xfbdfe000-0xfbdfffff]
[    0.911643] pci 0000:03:00.0: PME# supported from D3hot
[    0.911647] pci 0000:03:00.0: PME# disabled
[    0.911696] pci 0000:03:00.1: reg 10 io port: [0xdc00-0xdc07]
[    0.911704] pci 0000:03:00.1: reg 14 io port: [0xd880-0xd883]
[    0.911712] pci 0000:03:00.1: reg 18 io port: [0xd800-0xd807]
[    0.911720] pci 0000:03:00.1: reg 1c io port: [0xd480-0xd483]
[    0.911728] pci 0000:03:00.1: reg 20 io port: [0xd400-0xd40f]
[    0.911811] pci 0000:00:1c.6: bridge io port: [0xd000-0xdfff]
[    0.911814] pci 0000:00:1c.6: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]
[    0.911860] pci 0000:02:00.0: reg 10 io port: [0xc800-0xc8ff]
[    0.911879] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfafff000-0xfaffffff]
[    0.911891] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfaff8000-0xfaffbfff]
[    0.911899] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfbcf0000-0xfbcfffff]
[    0.911935] pci 0000:02:00.0: supports D1 D2
[    0.911936] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.911940] pci 0000:02:00.0: PME# disabled
[    0.911992] pci 0000:00:1c.7: bridge io port: [0xc000-0xcfff]
[    0.911995] pci 0000:00:1c.7: bridge 32bit mmio: [0xfbc00000-0xfbcfffff]
[    0.912000] pci 0000:00:1c.7: bridge 64bit mmio pref: [0xfaf00000-0xfaffffff]
[    0.912034] pci 0000:07:03.0: reg 10 32bit mmio: [0xfbeff800-0xfbefffff]
[    0.912040] pci 0000:07:03.0: reg 14 io port: [0xec00-0xec7f]
[    0.912079] pci 0000:07:03.0: supports D2
[    0.912081] pci 0000:07:03.0: PME# supported from D2 D3hot D3cold
[    0.912084] pci 0000:07:03.0: PME# disabled
[    0.912122] pci 0000:00:1e.0: transparent bridge
[    0.912125] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.912128] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.912158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.912312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.912415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.912472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.912522] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.912571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
[    0.912620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    0.912680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    0.933863] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.933974] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.934082] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.934192] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.934301] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.934411] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.934521] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.934630] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.934722] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.934725] vgaarb: loaded
[    0.934795] SCSI subsystem initialized
[    0.934867] libata version 3.00 loaded.
[    0.934914] usbcore: registered new interface driver usbfs
[    0.934921] usbcore: registered new interface driver hub
[    0.934937] usbcore: registered new device driver usb
[    0.935031] ACPI: WMI: Mapper loaded
[    0.935032] PCI: Using ACPI for IRQ routing
[    0.935159] NetLabel: Initializing
[    0.935160] NetLabel:  domain hash size = 128
[    0.935161] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.935172] NetLabel:  unlabeled traffic allowed by default
[    0.935199] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    0.935203] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.946568] hpet: hpet2 irq 24 for MSI
[    0.946720] hpet: hpet3 irq 25 for MSI
[    0.956624] hpet: hpet4 irq 26 for MSI
[    0.966629] hpet: hpet5 irq 27 for MSI
[    0.966640] Switching to clocksource tsc
[    0.967808] AppArmor: AppArmor Filesystem Enabled
[    0.967820] pnp: PnP ACPI init
[    0.967830] ACPI: bus type pnp registered
[    0.970592] pnp: PnP ACPI: found 17 devices
[    0.970594] ACPI: ACPI bus type pnp unregistered
[    0.970601] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    0.970603] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    0.970605] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    0.970607] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.970612] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.970616] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.970618] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.970620] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.970622] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.970624] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.970626] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.970629] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.970633] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.970635] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.970639] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.970642] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.970644] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.970646] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.970648] system 00:10: iomem range 0x100000-0xbfffffff could not be reserved
[    0.970650] system 00:10: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.975315] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.975317] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
[    0.975320] pci 0000:00:03.0:   MEM window: 0xfbb00000-0xfbbfffff
[    0.975323] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.975327] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
[    0.975329] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.975333] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.975336] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.975341] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
[    0.975343] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.975347] pci 0000:00:1c.4:   MEM window: 0xc0400000-0xc05fffff
[    0.975350] pci 0000:00:1c.4:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    0.975355] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.975357] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
[    0.975360] pci 0000:00:1c.5:   MEM window: 0xc0800000-0xc09fffff
[    0.975364] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
[    0.975369] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03
[    0.975371] pci 0000:00:1c.6:   IO window: 0xd000-0xdfff
[    0.975374] pci 0000:00:1c.6:   MEM window: 0xfbd00000-0xfbdfffff
[    0.975378] pci 0000:00:1c.6:   PREFETCH window: 0x000000c0c00000-0x000000c0dfffff
[    0.975382] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02
[    0.975385] pci 0000:00:1c.7:   IO window: 0xc000-0xcfff
[    0.975388] pci 0000:00:1c.7:   MEM window: 0xfbc00000-0xfbcfffff
[    0.975391] pci 0000:00:1c.7:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.975396] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.975398] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.975402] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.975405] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.975416]   alloc irq_desc for 16 on node -1
[    0.975417]   alloc kstat_irqs on node -1
[    0.975421] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.975424] pci 0000:00:03.0: setting latency timer to 64
[    0.975430] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.975432]   alloc irq_desc for 17 on node -1
[    0.975433]   alloc kstat_irqs on node -1
[    0.975436] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.975439] pci 0000:00:1c.0: setting latency timer to 64
[    0.975445] pci 0000:00:1c.4: enabling device (0104 -> 0107)
[    0.975447] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.975450] pci 0000:00:1c.4: setting latency timer to 64
[    0.975456] pci 0000:00:1c.5: enabling device (0104 -> 0107)
[    0.975459] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.975462] pci 0000:00:1c.5: setting latency timer to 64
[    0.975468]   alloc irq_desc for 18 on node -1
[    0.975472]   alloc kstat_irqs on node -1
[    0.975474] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.975477] pci 0000:00:1c.6: setting latency timer to 64
[    0.975483]   alloc irq_desc for 19 on node -1
[    0.975484]   alloc kstat_irqs on node -1
[    0.975487] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.975490] pci 0000:00:1c.7: setting latency timer to 64
[    0.975494] pci 0000:00:1e.0: setting latency timer to 64
[    0.975498] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.975499] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.975501] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.975503] pci_bus 0000:01: resource 1 mem: [0xfbb00000-0xfbbfffff]
[    0.975504] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.975506] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.975508] pci_bus 0000:06: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.975509] pci_bus 0000:06: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.975511] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
[    0.975513] pci_bus 0000:05: resource 1 mem: [0xc0400000-0xc05fffff]
[    0.975514] pci_bus 0000:05: resource 2 pref mem [0xc0600000-0xc07fffff]
[    0.975516] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.975517] pci_bus 0000:04: resource 1 mem: [0xc0800000-0xc09fffff]
[    0.975519] pci_bus 0000:04: resource 2 pref mem [0xc0a00000-0xc0bfffff]
[    0.975521] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.975522] pci_bus 0000:03: resource 1 mem: [0xfbd00000-0xfbdfffff]
[    0.975524] pci_bus 0000:03: resource 2 pref mem [0xc0c00000-0xc0dfffff]
[    0.975526] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.975527] pci_bus 0000:02: resource 1 mem: [0xfbc00000-0xfbcfffff]
[    0.975529] pci_bus 0000:02: resource 2 pref mem [0xfaf00000-0xfaffffff]
[    0.975530] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
[    0.975532] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.975534] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.975535] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.975558] NET: Registered protocol family 2
[    0.975683] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.976416] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.978710] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.978989] TCP: Hash tables configured (established 524288 bind 65536)
[    0.978991] TCP reno registered
[    0.979077] NET: Registered protocol family 1
[    0.979140] pci 0000:01:00.0: Boot video device
[    0.979380] Scanning for low memory corruption every 60 seconds
[    0.979465] audit: initializing netlink socket (disabled)
[    0.979472] type=2000 audit(1272733086.739:1): initialized
[    0.987125] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.988104] VFS: Disk quotas dquot_6.5.2
[    0.988143] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.988576] fuse init (API version 7.13)
[    0.988632] msgmni has been set to 7892
[    0.988784] alg: No test for stdrng (krng)
[    0.988821] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.988823] io scheduler noop registered
[    0.988825] io scheduler anticipatory registered
[    0.988826] io scheduler deadline registered
[    0.988852] io scheduler cfq registered (default)
[    0.988949]   alloc irq_desc for 29 on node -1
[    0.988951]   alloc kstat_irqs on node -1
[    0.988957] pcieport 0000:00:03.0: irq 29 for MSI/MSI-X
[    0.988963] pcieport 0000:00:03.0: setting latency timer to 64
[    0.989043]   alloc irq_desc for 30 on node -1
[    0.989044]   alloc kstat_irqs on node -1
[    0.989049] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
[    0.989056] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.989138]   alloc irq_desc for 31 on node -1
[    0.989139]   alloc kstat_irqs on node -1
[    0.989144] pcieport 0000:00:1c.4: irq 31 for MSI/MSI-X
[    0.989150] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.989233]   alloc irq_desc for 32 on node -1
[    0.989234]   alloc kstat_irqs on node -1
[    0.989239] pcieport 0000:00:1c.5: irq 32 for MSI/MSI-X
[    0.989246] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.989328]   alloc irq_desc for 33 on node -1
[    0.989331]   alloc kstat_irqs on node -1
[    0.989336] pcieport 0000:00:1c.6: irq 33 for MSI/MSI-X
[    0.989342] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.989427]   alloc irq_desc for 34 on node -1
[    0.989428]   alloc kstat_irqs on node -1
[    0.989433] pcieport 0000:00:1c.7: irq 34 for MSI/MSI-X
[    0.989439] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.989497] Firmware did not grant requested _OSC control
[    0.989499] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.989506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.989516] Firmware did not grant requested _OSC control
[    0.989528] Firmware did not grant requested _OSC control
[    0.989537] Firmware did not grant requested _OSC control
[    0.989547] Firmware did not grant requested _OSC control
[    0.989557] Firmware did not grant requested _OSC control
[    0.989576] Firmware did not grant requested _OSC control
[    0.989586] Firmware did not grant requested _OSC control
[    0.989595] Firmware did not grant requested _OSC control
[    0.989605] Firmware did not grant requested _OSC control
[    0.989614] Firmware did not grant requested _OSC control
[    0.989624] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.989690] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.989693] ACPI: Power Button [PWRB]
[    0.989720] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.989722] ACPI: Power Button [PWRF]
[    0.990569] ACPI: SSDT 00000000bf7880c0 01028 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.990901] processor LNXCPU:00: registered as cooling_device0
[    0.990928] processor LNXCPU:01: registered as cooling_device1
[    0.990951] processor LNXCPU:02: registered as cooling_device2
[    0.990974] processor LNXCPU:03: registered as cooling_device3
[    0.994380] Linux agpgart interface v0.103
[    0.994399] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.994489] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.994751] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.995444] brd: module loaded
[    0.995751] loop: module loaded
[    0.995798] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.995850] ata_piix 0000:00:1f.2: version 2.13
[    0.995861]   alloc irq_desc for 21 on node -1
[    0.995864]   alloc kstat_irqs on node -1
[    0.995867] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.995871] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.995897] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.995939] scsi0 : ata_piix
[    0.995987] scsi1 : ata_piix
[    0.997099] ata1: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 21
[    0.997104] ata2: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 21
[    0.997120] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.997133] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.997155] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.997178] scsi2 : ata_piix
[    0.997213] scsi3 : ata_piix
[    0.998135] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 21
[    0.998138] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 21
[    0.998192] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.998197] pata_acpi 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.998216] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.998226] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.998413] Fixed MDIO Bus: probed
[    0.998433] PPP generic driver version 2.4.2
[    0.998453] tun: Universal TUN/TAP device driver, 1.6
[    0.998455] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.998510] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.998522] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.998535] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.998537] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.998556] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.998577] ehci_hcd 0000:00:1a.0: debug port 2
[    1.002449] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    1.002461] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbafe000
[    1.016610] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.016671] usb usb1: configuration #1 chosen from 1 choice
[    1.016689] hub 1-0:1.0: USB hub found
[    1.016694] hub 1-0:1.0: 2 ports detected
[    1.016728]   alloc irq_desc for 23 on node -1
[    1.016729]   alloc kstat_irqs on node -1
[    1.016733] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.016744] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.016746] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.016768] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.016789] ehci_hcd 0000:00:1d.0: debug port 2
[    1.018781] Freeing initrd memory: 8134k freed
[    1.020662] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    1.020677] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbafd000
[    1.036569] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.036687] usb usb2: configuration #1 chosen from 1 choice
[    1.036709] hub 2-0:1.0: USB hub found
[    1.036714] hub 2-0:1.0: 2 ports detected
[    1.036752] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.036763] uhci_hcd: USB Universal Host Controller Interface driver
[    1.036818] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.039393] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.039397] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.039453] mice: PS/2 mouse device common for all mice
[    1.039515] rtc_cmos 00:03: RTC can wake from S4
[    1.039541] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.039565] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.039651] device-mapper: uevent: version 1.0.3
[    1.039723] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.039781] device-mapper: multipath: version 1.1.0 loaded
[    1.039783] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.039912] cpuidle: using governor ladder
[    1.039913] cpuidle: using governor menu
[    1.040174] TCP cubic registered
[    1.040260] NET: Registered protocol family 10
[    1.040607] lo: Disabled Privacy Extensions
[    1.040807] NET: Registered protocol family 17
[    1.041950] PM: Resume from disk failed.
[    1.041961] registered taskstats version 1
[    1.042373]   Magic number: 10:207:994
[    1.042438] rtc_cmos 00:03: setting system clock to 2010-05-01 16:58:07 UTC (1272733087)
[    1.042440] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.042441] EDD information not available.
[    1.059593] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.335874] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.356588] ata4: SATA link down (SStatus 0 SControl 300)
[    1.367287] ata3: SATA link down (SStatus 0 SControl 300)
[    1.485955] usb 1-1: configuration #1 chosen from 1 choice
[    1.486044] hub 1-1:1.0: USB hub found
[    1.486134] hub 1-1:1.0: 6 ports detected
[    1.605263] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.705849] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.705861] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.755266] usb 2-1: configuration #1 chosen from 1 choice
[    1.755354] hub 2-1:1.0: USB hub found
[    1.755447] hub 2-1:1.0: 8 ports detected
[    1.854741] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.854757] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.914746] ata2.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[    1.914749] ata2.00: ATA-7: SAMSUNG HD161HJ, JF100-19, max UDMA7
[    1.914751] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.934695] ata2.01: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.934697] ata2.01: ATA-7: SAMSUNG HD502IJ, 1AA01113, max UDMA7
[    1.934699] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.954764] ata2.00: configured for UDMA/133
[    1.974744] ata2.01: configured for UDMA/133
[    1.974833] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD161HJ  JF10 PQ: 0 ANSI: 5
[    1.974915] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.974917] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.974946] sd 1:0:0:0: [sda] Write Protect is off
[    1.974948] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.974969] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.974984] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    1.975065] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.975073] sd 1:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.975079]  sda: sda1 sda2 sda3 sda4 <
[    1.982619] sd 1:0:1:0: [sdb] Write Protect is off
[    1.982623] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.001280]  sda5 >
[    2.001305] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.001472]  sdb: sdb1 sdb2 sdb3
[    2.011994] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.012103] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.012117] Freeing unused kernel memory: 876k freed
[    2.012242] Write protecting the kernel read-only data: 7680k
[    2.021824] udev: starting version 151
[    2.037183] ahci 0000:03:00.0: version 3.0
[    2.037200] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.049017] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.049032] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.049074] r8169 0000:02:00.0: setting latency timer to 64
[    2.049113]   alloc irq_desc for 35 on node -1
[    2.049114]   alloc kstat_irqs on node -1
[    2.049125] r8169 0000:02:00.0: irq 35 for MSI/MSI-X
[    2.049504] eth0: RTL8168d/8111d at 0xffffc9000065e000, 90:e6:ba:15:d9:58, XID 083000c0 IRQ 35
[    2.063183] ohci1394 0000:07:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.064360] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.064363] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.064368] ahci 0000:03:00.0: setting latency timer to 64
[    2.065066] scsi4 : ahci
[    2.065122] scsi5 : ahci
[    2.065190] ata5: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 18
[    2.065194] ata6: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 18
[    2.065235] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.065258] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    2.065313] scsi6 : pata_jmicron
[    2.065352] scsi7 : pata_jmicron
[    2.065820] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 19
[    2.065822] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 19
[    2.126395] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.254701] ata7.01: ATAPI: HL-DT-STDVD-RAM GSA-H58N, 1.00, max UDMA/66
[    2.294616] ata7.01: configured for UDMA/66
[    2.423397] ata6: SATA link down (SStatus 0 SControl 300)
[    2.423433] ata5: SATA link down (SStatus 0 SControl 300)
[    2.444794] scsi 6:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H58N 1.00 PQ: 0 ANSI: 5
[    2.449245] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.449250] Uniform CD-ROM driver Revision: 3.20
[    2.449351] sr 6:0:1:0: Attached scsi CD-ROM sr0
[    2.449385] sr 6:0:1:0: Attached scsi generic sg2 type 5
[    2.509402] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    3.451152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000a9032d]
[    9.880333] udev: starting version 151
[    9.899309] lp: driver loaded but no devices found
[    9.903928] vga16fb: initializing
[    9.903931] vga16fb: mapped to 0xffff8800000a0000
[    9.903991] fb0: VGA16 VGA frame buffer device
[    9.907331] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.907333] Disabling lock debugging due to kernel taint
[    9.941840] Adding 3908600k swap on /dev/sda5.  Priority:-1 extents:1 across:3908600k 
[    9.983008] [fglrx] Maximum main memory to use for locked dma buffers: 3793 MBytes.
[    9.983119] [fglrx]   vendor: 1002 device: 9490 count: 1
[    9.983356] [fglrx] ioport: bar 4, base 0xb000, size: 0x100
[    9.983366] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.983370] pci 0000:01:00.0: setting latency timer to 64
[    9.983517] [fglrx] Kernel PAT support is enabled
[    9.983529] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[    9.992623] type=1505 audit(1272743896.464:2):  operation="profile_load" pid=682 name="/sbin/dhclient3"
[    9.993009] type=1505 audit(1272743896.464:3):  operation="profile_load" pid=682 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.993218] type=1505 audit(1272743896.464:4):  operation="profile_load" pid=682 name="/usr/lib/connman/scripts/dhclient-script"
[   10.014029] ATK0110 ATK0110:00: EC enabled
[   10.111236] Console: switching to colour frame buffer device 80x30
[   10.131382]   alloc irq_desc for 22 on node -1
[   10.131384]   alloc kstat_irqs on node -1
[   10.131389] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.131426] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.277489] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.277527] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.486995] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   10.512729] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   10.645717] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   10.752608] r8169: eth0: link up
[   10.752612] r8169: eth0: link up
[   10.753171] type=1505 audit(1272743897.224:5):  operation="profile_replace" pid=959 name="/sbin/dhclient3"
[   10.753561] type=1505 audit(1272743897.224:6):  operation="profile_replace" pid=959 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.753774] type=1505 audit(1272743897.224:7):  operation="profile_replace" pid=959 name="/usr/lib/connman/scripts/dhclient-script"
[   10.756575] type=1505 audit(1272743897.234:8):  operation="profile_load" pid=962 name="/usr/lib/cups/backend/cups-pdf"
[   10.757203] type=1505 audit(1272743897.234:9):  operation="profile_load" pid=962 name="/usr/sbin/cupsd"
[   10.758666] type=1505 audit(1272743897.234:10):  operation="profile_load" pid=970 name="/usr/sbin/mysqld-akonadi"
[   10.759732] type=1505 audit(1272743897.234:11):  operation="profile_load" pid=971 name="/usr/sbin/tcpdump"
[   10.992760]   alloc irq_desc for 36 on node -1
[   10.992762]   alloc kstat_irqs on node -1
[   10.992771] fglrx_pci 0000:01:00.0: irq 36 for MSI/MSI-X
[   10.993204] [fglrx] Firegl kernel thread PID: 1014
[   10.993395] [fglrx] IRQ 36 Enabled
[   11.052184] ppdev: user-space parallel port driver
[   11.156611] CPU0 attaching NULL sched-domain.
[   11.156615] CPU1 attaching NULL sched-domain.
[   11.156617] CPU2 attaching NULL sched-domain.
[   11.156618] CPU3 attaching NULL sched-domain.
[   11.243452] CPU0 attaching sched-domain:
[   11.243454]  domain 0: span 0-3 level MC
[   11.243456]   groups: 0 1 2 3
[   11.243460] CPU1 attaching sched-domain:
[   11.243461]  domain 0: span 0-3 level MC
[   11.243463]   groups: 1 2 3 0
[   11.243466] CPU2 attaching sched-domain:
[   11.243467]  domain 0: span 0-3 level MC
[   11.243469]   groups: 2 3 0 1
[   11.243472] CPU3 attaching sched-domain:
[   11.243473]  domain 0: span 0-3 level MC
[   11.243474]   groups: 3 0 1 2
[   11.935425] [fglrx] Gart USWC size:1234 M.
[   11.935428] [fglrx] Gart cacheable size:490 M.
[   11.935432] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   11.935433] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000 
[   11.935435] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   20.487471] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   20.619436] CPU0 attaching NULL sched-domain.
[   20.619443] CPU1 attaching NULL sched-domain.
[   20.619446] CPU2 attaching NULL sched-domain.
[   20.619450] CPU3 attaching NULL sched-domain.
[   20.685470] CPU0 attaching sched-domain:
[   20.685474]  domain 0: span 0-3 level MC
[   20.685478]   groups: 0 1 2 3
[   20.685486] CPU1 attaching sched-domain:
[   20.685489]  domain 0: span 0-3 level MC
[   20.685493]   groups: 1 2 3 0
[   20.685500] CPU2 attaching sched-domain:
[   20.685502]  domain 0: span 0-3 level MC
[   20.685505]   groups: 2 3 0 1
[   20.685512] CPU3 attaching sched-domain:
[   20.685515]  domain 0: span 0-3 level MC
[   20.685518]   groups: 3 0 1 2
[   21.025031] eth0: no IPv6 routers present
[  235.498717] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.

```

As for doing this after a freeze, well, could you teach me how to run a dmesg >> /home/user/Desktop/dmesg.txt every minute or so?

---

### Post by P4man on 2010-05-01
> **gredorian said:**
> 
As for doing this after a freeze, well, could you teach me how to run a dmesg >> /home/user/Desktop/dmesg.txt every minute or so?

No need. The logs are saved, just go to system > adminstration > log file viewer. Have a look, especially syslog.. See if you can find an error that corresponds with the time of the freeze.

The log you posted was not after a freeze? That last line is not normal and suggests a problem with the input device. Is this a laptop with a touchpad?

---

### Post by gredorian on 2010-05-01
I noticed that line too but can't tell anything about it. No, this is a desktop computer with a wired non-usb mouse and keyboard. And now I also noticed another problem: some times the mouse can only scroll horizontally and vertically and extremely fast (I mean it can only go right/left and top/bottom but not diagonally). It's solved by just clicking anywhere but still weird.

These kind of stuff never happened to me before. I used all versions of Ubuntu since 6.04 and had a pretty solid 9.10 running smooth. I just couldn't resist getting the new LTS release. Oh well I guess I'm making a Windows partition until the next updates because I don't feel like downloading 9.10 all over again.

---

### Post by P4man on 2010-05-01
next time it freezes, see if you can change capslock or numlock. Sure sounds like a problem with the ps2 port. Perhaps you can try booting the kernel with this option:

i8042.reset

and/or 

i8042.nomux

edit: another thought. This is a Core i5 machine. Does it have Turbo mode? If so, can you try disabling it in the bios.

---

### Post by gredorian on 2010-05-01
Turbo is off, caps and numlock can't be switched because no keyboard input happens at all. And I'm back to Windows. I don't think I'll be going back for now. Unfortunately I don't have the patience to keep rebooting every once in a while. That's a shame since I was waiting for 10.04 so I could install it in my shiny new laptop. I just hope some dev will look at this topic and try to figure something out. Perhaps the GNOME variant will work better?

---

### Post by Babuloseo on 2010-05-01
My wireless mouse and keyboard do not WORK!!!!! Only works when i plug it in to my monitors usb ports (really slow and messed but usable)

My USB adapters in my pc are not getting detected.

My RAID and my NTFS and my other partitions are not getting detected.

When i boot it does not take 10 seconds or 15.. more like 30 secs or something around 45 secs... the splash screen and boot is messed up!!

My WIRED NIC is not getting detected :(

---

### Post by P4man on 2010-05-01
> **gredorian said:**
> Turbo is off, caps and numlock can't be switched because no keyboard input happens at all. And I'm back to Windows. I don't think I'll be going back for now. Unfortunately I don't have the patience to keep rebooting every once in a while. That's a shame since I was waiting for 10.04 so I could install it in my shiny new laptop. I just hope some dev will look at this topic and try to figure something out. Perhaps the GNOME variant will work better?

If its a kernel issue, gnome or kde wont change a thing, but I really cant say I know for fact its kernel related.

as for devs, they dont read the forums. To get their attention you need to file a bug report on launchpad:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by gredorian on 2010-05-02
I'm writing from another computer since not only is the problem still around in the GNOME counterpart (I installed it) but Ubuntu also somehow screwed my computer network even for the Windows partition (I have no idea how). That does it. I'm leaving Ubuntu until Canonical releases a version that doesn't **** me off so much. As I said I used Ubuntu since 6.04 and this is the first one that makes me give up. :evil:

---

### Post by gredorian on 2010-05-06
Well I gave it some thought after my ragequit and realised it's just not fair to go out and say "screw it", specially because this community is pretty helpful. So I came back to give a few more details about the issue that hopefully will prove useful for someone. After another freeze I tried plugin in my USB wireless mouse and it started working again (except for the keyboard). After extensive use of the wireless mouse exclusively I didn't get any issue with either mouse or keyboard, which means that the mouse is probably the trigger of this bug.

I did install Kubuntu 10.04 in my laptop and it's working fine. So far I can say it's a pretty solid release except for that issue. Mousepad and laptop keyboard seems to work just fine for any ammount of time. And the network stuff... well the Windows driver fixed that after several annoying attemps of screwing around and rebooting. 

My system specs are as follow:

Motherboard: P7P55D PRO LGA 1156
Processor: Intel Core i5 750
Memory: 2x2GB Corsair DDR 1600mhz
HDD: 160GB SAMSUNG master drive with Kubuntu 10.04 and
     500GB SAMSUNG for MS Windows and Storage
Mouse: this [http://www.atera.com.br/dispprod.asp?COD=PM-520PRETO](http://www.atera.com.br/dispprod.asp?COD=PM-520PRETO), pretty cheap one but never had issues
Keyboard: pretty crappy but functional one

Well at least I get Kubuntu for my laptop which was my main goal. Hopefully someone with a similar system and problem will find this thread and confirm the problem.

---

### Post by drablaz on 2010-05-13
Hi, I can confirm the issue on a similar system as gredgorian.

I am running on a p7p55d pro as well with core i5, and mouse and keyboard goes dead after random time, usually a short one.

mouse and keyboard are ps2, i haven't tested usb ones because I don't have any now :P

Something I've noticed too, is that sometimes keyboard and mouse starts behaving strange, like if a (or maybe a few) keys are being pressed, so when you move the mouse, you get unexpected behaviour (change desktop, resize windows, changing focus), so if you type a key everything goes back to normal

One more thing, yet unconfirmed, is that I had a few keyboard freezes on terminal mode... but it happened just a few times (I'm don't use it much either)

Also when it freezes all system still works, clock, video, messenger, even an usb joystick works :P

That is as far as it goes with symptoms (at least for me) I can't really tell about logs, it's quite hard to find any hints as to where the problem comes from.

Is there a chance that a memory protection failure is happening? like if a random process writes on input buffer or something like that, thus leaving input useless? Or maybe I'm going nuts :P

Hope some miracle happens, my win7 is gettin slower by the hour u.u

---

### Post by Andrew.Stevenson on 2010-05-14
Hi,

Seems this ubuntu forum account finally works :)

I have a p7p55d and i am experiencing the same problems that drablaz and gredorian have. keyboard get stuck every now and then (less than an hour usually). i have been fiddling a bit today to find out what was going on.
you can try to add either these parameters to kernel command line (via grub etc):

i8042.reset
i8042.nomux
i8042.nopnp
i8042.noaux

so far, it seems to work here with the parameters "i8042.nopnp" set. i guess it's a bios/motherboard bug that messes up ps/2 pnp device detection on linux.

if you need debugging, you can use i8042.debug options too, or set it
after boot using:

echo 1 > /sys/module/i8042/parameters/debug

after setting this flag, and when my keyboard was frozen (i had to use the mouse to type commands char by char.. what a pain), i had this message in "dmesg":

[...] drivers/input/serio/i8042.c: interrupt 1, without any data

and the keyboard interrupt wouldn't tick anymore. you can check in realtime keyboard interrupts using the following command (keep pressing keys on keyboard and see if interrupts # increases):

watch "cat /proc/interrupts | grep i8042"

as a summary, *without* i8042.nopnp parameter set, i had in dmesg the following lines:

[    1.709441] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.709443] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.709968] serio: i8042 KBD port at 0x60,0x64 irq 1
 [    1.710008] mice: PS/2 mouse device common for all mice
[    1.729471] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0

and *with* i8042.nopnp set:

[    1.694592] i8042: PNP detection disabled
[    1.699719] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.699957] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.700244] mice: PS/2 mouse device common for all mice
[    1.720429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0

Hope this helps..

EDIT: this doesn't work, please check new post at [http://ubuntuforums.org/showthread.php?p=9304883#post9304883](http://ubuntuforums.org/showthread.php?p=9304883#post9304883)

---

### Post by jbreid on 2010-05-15
Yes my motherboard is an ASUS P7P55D EVO and I get the random mouse pointer freeze using a PS/2 mouse. My keyboard doesn't freeze but it is a USB connected keyboard. I have changed the mouse to a USB mouse and that avoids the problem.

---

### Post by gredorian on 2010-05-16
Thanks for the insight Andrew.Stevenson. I guess it's pretty safe to call this bug "confirmed" by now. I'll keep track of the issue in the other thread.

---

