---
title: "/dev/sdx always changing..."
date: 2012-10-12
forum: General Help
---

### Post by Jean-Claude Tergal on 2012-10-12
Hi,
 

 When I reboot, the "/dev/sdx" of hard drives is changing.
 For example, if I run KDE partition manager, I got this:
 

 > disk 1 --> /dev/sda
disk 2 --> /dev/sdb
disk 3 --> /dev/sdc
disk 4 --> /dev/sdd If I reboot and rerun KDE partition manager, it becomes
 

 > disk 1 --> /dev/sda
disk 2 --> /dev/sdb
disk 3 --> /dev/sdc
disk 4 --> /dev/sdh Ubuntu works fine except the plasmoid "Hard disk status" which don't find all hard drives.
 

 Can I force the system to use a specific "/dev/sdx"?
 Note that I use UUIDs in my FSTAB.
 I presume it work better with "/dev/sdx" (I've not try) but It seems that UUID becomes the standard.
 

 Otherswise, KDE partition manager tell me a warning: > Partition 4 does not start on physical sector boundary on /, home & swap...
 

 Has someone an idea?
 

 Thanks!

---

### Post by Rexilion on 2012-10-13
UUID's were invented just for this: Your OS will still be able to find the (correct) disk no matter how/when/if it's detected.

So switching your fstab to /dev/sdx notation will bork your system boot procedure (depending on how worse the disk shuffles are).

Maybe the last disk is failing? Can you provide the output of:

```
sudo dmesg
```

Lastly, you might want to read this:

[http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/cha.udev.html#sec.udev.rules](http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/cha.udev.html#sec.udev.rules)

---

### Post by cwsnyder on 2012-10-13
Disk 4 could also be slow responding, or shutting down between accesses.  Is it an internal drive, flash drive, or external USB drive?

---

### Post by Jean-Claude Tergal on 2012-10-13
Thank you for the answer!

> **Rexilion said:**
> 
So switching your fstab to /dev/sdx notation will bork your system boot procedure (depending on how worse the disk shuffles are).

Ok

> **Rexilion said:**
> 
Maybe the last disk is failing? Can you provide the output of:
 
I don't think so. It's not always the same disk. it's random. Sometimes I've got sda1/sdb1/sdc1 & sdd1 but mixed, sometimes I've sde1, sdf1...

> **Rexilion said:**
> 
[http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/cha.udev.html#sec.udev.rules](http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/cha.udev.html#sec.udev.rules)
Interesting. I will analyse this possibility.

I forgot to tell you an important thing: the plasmoid has the probleme since I've installed Precise (conserving my home). It was working perfectly with Lucid!

Here is the dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic-pae 3.2.28)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Acer Aspire T135/K8VM800MAE, BIOS R01-B2 08/30/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fff0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CFFFF uncachable
[    0.000000]   D0000-D7FFF write-back
[    0.000000]   D8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 00E0000000 mask FFFC000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f5480] f5480
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 35968000 - 36cac000
[    0.000000] ACPI: RSDP 000f6e20 00014 (v00 VIAK8 )
[    0.000000] ACPI: RSDT 7fff3000 0002C (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: FACP 7fff3040 00074 (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: DSDT 7fff30c0 04366 (v01 VIAK8  AWRDACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 7fff0000 00040
[    0.000000] ACPI: APIC 7fff7440 0005A (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fff0
[    0.000000] On node 0 totalpages: 524159
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4968200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 293610 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7be3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520063
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=169efccc-0014-4396-84af-2dd3b136f285 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8388096 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007fff0)
[    0.000000] Memory: 2041056k/2097088k available (5818k kernel code, 55580k reserved, 2846k data, 740k init, 1183688k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1808.236 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3616.47 BogoMIPS (lpj=7232944)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004043] Security Framework initialized
[    0.004077] AppArmor: AppArmor initialized
[    0.004080] Yama: becoming mindful.
[    0.004163] Mount-cache hash table entries: 512
[    0.004341] Initializing cgroup subsys cpuacct
[    0.004350] Initializing cgroup subsys memory
[    0.004362] Initializing cgroup subsys devices
[    0.004366] Initializing cgroup subsys freezer
[    0.004370] Initializing cgroup subsys blkio
[    0.004380] Initializing cgroup subsys perf_event
[    0.004413] mce: CPU supports 5 MCE banks
[    0.004704] SMP alternatives: switching to UP code
[    0.018311] Freeing SMP alternatives: 24k freed
[    0.018340] ACPI: Core revision 20110623
[    0.024159] ftrace: allocating 26555 entries in 52 pages
[    0.028103] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028477] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.069617] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (3616.47 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] EVM: security.selinux
[    0.072003] EVM: security.SMACK64
[    0.072003] EVM: security.capability
[    0.072003] PM: Registering ACPI NVS region at 7fff0000 (12288 bytes)
[    0.072003] print_constraints: dummy: 
[    0.072003] RTC time: 12:57:17, date: 10/13/12
[    0.072003] NET: Registered protocol family 16
[    0.072003] EISA bus registered
[    0.072003] node 0 link 0: io port [1000, fffff]
[    0.072003] TOM: 0000000080000000 aka 2048M
[    0.072003] node 0 link 0: mmio [a0000, bffff]
[    0.072003] node 0 link 0: mmio [80000000, ffb7ffff]
[    0.072003] bus: [00, ff] on node 0 link 0
[    0.072003] bus: 00 index 0 [io  0x0000-0xffff]
[    0.072003] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.072003] bus: 00 index 2 [mem 0x80000000-0xfcffffffff]
[    0.072003] ACPI: bus type pci registered
[    0.078453] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.078458] PCI: PCI BIOS revision 2.10 entry at 0xfb150, last bus=1
[    0.078461] PCI: Using configuration type 1 for base access
[    0.080190] bio: create slab <bio-0> at 0
[    0.080314] ACPI: Added _OSI(Module Device)
[    0.080317] ACPI: Added _OSI(Processor Device)
[    0.080320] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.080323] ACPI: Added _OSI(Processor Aggregator Device)
[    0.080974] ACPI: EC: Look up EC in DSDT
[    0.081794] ACPI: Actual Package length (6) is larger than NumElements field (2), truncated
[    0.081799] 
[    0.084163] ACPI: Interpreter enabled
[    0.084171] ACPI: (supports S0 S3 S4 S5)
[    0.084194] ACPI: Using IOAPIC for interrupt routing
[    0.088427] ACPI: No dock devices found.
[    0.088432] HEST: Table not found.
[    0.088438] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.088515] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.088672] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.088676] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.088680] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.088684] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.088688] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.088711] pci 0000:00:00.0: [1106:0204] type 0 class 0x000600
[    0.088720] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe3ffffff pref]
[    0.088803] pci 0000:00:00.1: [1106:1204] type 0 class 0x000600
[    0.088844] pci 0000:00:00.2: [1106:2204] type 0 class 0x000600
[    0.088884] pci 0000:00:00.3: [1106:3204] type 0 class 0x000600
[    0.088922] pci 0000:00:00.4: [1106:4204] type 0 class 0x000600
[    0.088962] pci 0000:00:00.7: [1106:7204] type 0 class 0x000600
[    0.089006] pci 0000:00:01.0: [1106:b188] type 1 class 0x000604
[    0.089052] pci 0000:00:01.0: supports D1
[    0.089080] pci 0000:00:0b.0: [1106:3249] type 0 class 0x000104
[    0.089096] pci 0000:00:0b.0: reg 10: [io  0xa000-0xa00f]
[    0.089106] pci 0000:00:0b.0: reg 14: [io  0xa400-0xa40f]
[    0.089116] pci 0000:00:0b.0: reg 18: [io  0xa800-0xa80f]
[    0.089125] pci 0000:00:0b.0: reg 1c: [io  0xac00-0xac0f]
[    0.089134] pci 0000:00:0b.0: reg 20: [io  0xb000-0xb01f]
[    0.089143] pci 0000:00:0b.0: reg 24: [io  0xb400-0xb4ff]
[    0.089153] pci 0000:00:0b.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.089196] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000101
[    0.089212] pci 0000:00:0f.0: reg 10: [io  0xb800-0xb807]
[    0.089221] pci 0000:00:0f.0: reg 14: [io  0xbc00-0xbc03]
[    0.089231] pci 0000:00:0f.0: reg 18: [io  0xc000-0xc007]
[    0.089240] pci 0000:00:0f.0: reg 1c: [io  0xc400-0xc403]
[    0.089250] pci 0000:00:0f.0: reg 20: [io  0xc800-0xc80f]
[    0.089260] pci 0000:00:0f.0: reg 24: [io  0xcc00-0xccff]
[    0.089307] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.089348] pci 0000:00:0f.1: reg 20: [io  0xd000-0xd00f]
[    0.089408] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.089447] pci 0000:00:10.0: reg 20: [io  0xd400-0xd41f]
[    0.089484] pci 0000:00:10.0: supports D1 D2
[    0.089487] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089492] pci 0000:00:10.0: PME# disabled
[    0.089509] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.089548] pci 0000:00:10.1: reg 20: [io  0xd800-0xd81f]
[    0.089585] pci 0000:00:10.1: supports D1 D2
[    0.089587] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089592] pci 0000:00:10.1: PME# disabled
[    0.089609] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.089647] pci 0000:00:10.2: reg 20: [io  0xdc00-0xdc1f]
[    0.089684] pci 0000:00:10.2: supports D1 D2
[    0.089687] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089692] pci 0000:00:10.2: PME# disabled
[    0.089708] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.089747] pci 0000:00:10.3: reg 20: [io  0xe000-0xe01f]
[    0.089783] pci 0000:00:10.3: supports D1 D2
[    0.089786] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089791] pci 0000:00:10.3: PME# disabled
[    0.089808] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.089824] pci 0000:00:10.4: reg 10: [mem 0xe8000000-0xe80000ff]
[    0.089884] pci 0000:00:10.4: supports D1 D2
[    0.089886] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089891] pci 0000:00:10.4: PME# disabled
[    0.089912] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
[    0.089965] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.090009] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
[    0.090025] pci 0000:00:11.5: reg 10: [io  0xe400-0xe4ff]
[    0.090088] pci 0000:00:11.5: supports D1 D2
[    0.090109] pci 0000:00:13.0: [10ec:8139] type 0 class 0x000200
[    0.090125] pci 0000:00:13.0: reg 10: [io  0xe800-0xe8ff]
[    0.090134] pci 0000:00:13.0: reg 14: [mem 0xe8001000-0xe80010ff]
[    0.090190] pci 0000:00:13.0: supports D1 D2
[    0.090193] pci 0000:00:13.0: PME# supported from D1 D2 D3hot D3cold
[    0.090198] pci 0000:00:13.0: PME# disabled
[    0.090214] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.090239] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.090259] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.090278] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.090304] PCI: peer root bus 00 res updated from pci conf
[    0.090340] pci 0000:01:00.0: [10de:0221] type 0 class 0x000300
[    0.090353] pci 0000:01:00.0: reg 10: [mem 0xe4000000-0xe4ffffff]
[    0.090361] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff pref]
[    0.090368] pci 0000:01:00.0: reg 18: [mem 0xe5000000-0xe5ffffff]
[    0.090388] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.090437] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.090444] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe6ffffff]
[    0.090450] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.090458] pci_bus 0000:00: on NUMA node 0
[    0.090462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.090683]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.115426] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[    0.115521] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.115616] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.115712] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[    0.115783] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.115851] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.115919] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.115987] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.116120] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.116237] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.116373] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.116496] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.116698] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.116702] vgaarb: loaded
[    0.116703] vgaarb: bridge control possible 0000:01:00.0
[    0.116874] i2c-core: driver [aat2870] using legacy suspend method
[    0.116877] i2c-core: driver [aat2870] using legacy resume method
[    0.116997] SCSI subsystem initialized
[    0.117077] libata version 3.00 loaded.
[    0.117151] usbcore: registered new interface driver usbfs
[    0.117168] usbcore: registered new interface driver hub
[    0.117199] usbcore: registered new device driver usb
[    0.117333] PCI: Using ACPI for IRQ routing
[    0.117339] PCI: pci_cache_line_size set to 64 bytes
[    0.117421] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.117425] reserve RAM buffer: 000000007fff0000 - 000000007fffffff 
[    0.117575] NetLabel: Initializing
[    0.117578] NetLabel:  domain hash size = 128
[    0.117580] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.117594] NetLabel:  unlabeled traffic allowed by default
[    0.127317] AppArmor: AppArmor Filesystem Enabled
[    0.127366] pnp: PnP ACPI init
[    0.127391] ACPI: bus type pnp registered
[    0.127603] pnp 00:00: [mem 0x000d0000-0x000d7fff]
[    0.127607] pnp 00:00: [mem 0x000f0000-0x000f7fff]
[    0.127610] pnp 00:00: [mem 0x000f8000-0x000fbfff]
[    0.127612] pnp 00:00: [mem 0x000fc000-0x000fffff]
[    0.127615] pnp 00:00: [mem 0x7fff0000-0x7fffffff]
[    0.127618] pnp 00:00: [mem 0xffff0000-0xffffffff]
[    0.127621] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.127624] pnp 00:00: [mem 0x00100000-0x7ffeffff]
[    0.127627] pnp 00:00: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.127631] pnp 00:00: [mem 0xfec00000-0xfec00fff]
[    0.127633] pnp 00:00: [mem 0xfee00000-0xfee00fff]
[    0.127637] pnp 00:00: [mem 0xfff80000-0xfffeffff]
[    0.127716] system 00:00: [mem 0x000d0000-0x000d7fff] has been reserved
[    0.127720] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.127724] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.127727] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.127731] system 00:00: [mem 0x7fff0000-0x7fffffff] could not be reserved
[    0.127735] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
[    0.127739] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.127743] system 00:00: [mem 0x00100000-0x7ffeffff] could not be reserved
[    0.127747] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.127751] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.127754] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.127760] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.127827] pnp 00:01: [bus 00-ff]
[    0.127830] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.127833] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.127836] pnp 00:01: [io  0x0d00-0xffff window]
[    0.127839] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.127842] pnp 00:01: [mem 0x000c0000-0x000dffff window]
[    0.127845] pnp 00:01: [mem 0x80000000-0xfebfffff window]
[    0.127899] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.127921] pnp 00:02: [io  0x4000-0x407f]
[    0.127924] pnp 00:02: [io  0x40f0-0x40ff]
[    0.127926] pnp 00:02: [io  0x5000-0x500f]
[    0.127979] system 00:02: [io  0x4000-0x407f] has been reserved
[    0.127982] system 00:02: [io  0x40f0-0x40ff] has been reserved
[    0.127986] system 00:02: [io  0x5000-0x500f] has been reserved
[    0.127990] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128375] pnp 00:03: [io  0x0010-0x001f]
[    0.128378] pnp 00:03: [io  0x0022-0x003f]
[    0.128381] pnp 00:03: [io  0x0044-0x005f]
[    0.128383] pnp 00:03: [io  0x0062-0x0063]
[    0.128386] pnp 00:03: [io  0x0065-0x006f]
[    0.128389] pnp 00:03: [io  0x0074-0x007f]
[    0.128391] pnp 00:03: [io  0x0091-0x0093]
[    0.128394] pnp 00:03: [io  0x00a2-0x00bf]
[    0.128396] pnp 00:03: [io  0x00e0-0x00ef]
[    0.128399] pnp 00:03: [io  0x04d0-0x04d1]
[    0.128402] pnp 00:03: [io  0x0290-0x029f]
[    0.128404] pnp 00:03: [io  0x0800-0x0805]
[    0.128490] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.128494] system 00:03: [io  0x0290-0x029f] has been reserved
[    0.128498] system 00:03: [io  0x0800-0x0805] has been reserved
[    0.128502] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128518] pnp 00:04: [dma 4]
[    0.128521] pnp 00:04: [io  0x0000-0x000f]
[    0.128524] pnp 00:04: [io  0x0080-0x0090]
[    0.128526] pnp 00:04: [io  0x0094-0x009f]
[    0.128529] pnp 00:04: [io  0x00c0-0x00df]
[    0.128566] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.128578] pnp 00:05: [io  0x0070-0x0073]
[    0.128592] pnp 00:05: [irq 8]
[    0.128637] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.128647] pnp 00:06: [io  0x0061]
[    0.128687] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.128698] pnp 00:07: [io  0x00f0-0x00ff]
[    0.128703] pnp 00:07: [irq 13]
[    0.128740] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.128882] pnp 00:08: [io  0x03f0-0x03f5]
[    0.128884] pnp 00:08: [io  0x03f7]
[    0.128890] pnp 00:08: [irq 6]
[    0.128892] pnp 00:08: [dma 2]
[    0.128949] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.129132] pnp 00:09: [io  0x03f8-0x03ff]
[    0.129138] pnp 00:09: [irq 4]
[    0.129222] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.129418] pnp 00:0a: [io  0x02f8-0x02ff]
[    0.129424] pnp 00:0a: [irq 3]
[    0.129492] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.129697] pnp 00:0b: [io  0x0378-0x037f]
[    0.129702] pnp 00:0b: [irq 7]
[    0.129777] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.129878] pnp 00:0c: [io  0x0060]
[    0.129880] pnp 00:0c: [io  0x0064]
[    0.129889] pnp 00:0c: [irq 1]
[    0.129932] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.129956] pnp: PnP ACPI: found 13 devices
[    0.129958] ACPI: ACPI bus type pnp unregistered
[    0.129963] PnPBIOS: Disabled by ACPI PNP
[    0.166866] Switching to clocksource acpi_pm
[    0.166900] PCI: max bus depth: 1 pci_try_num: 2
[    0.166927] pci 0000:00:0b.0: BAR 6: assigned [mem 0x80000000-0x8000ffff pref]
[    0.166933] pci 0000:01:00.0: BAR 6: assigned [mem 0xe6000000-0xe601ffff pref]
[    0.166937] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.166943] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe6ffffff]
[    0.166947] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.166962] pci 0000:00:01.0: setting latency timer to 64
[    0.166967] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.166970] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.166973] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
[    0.166977] pci_bus 0000:01: resource 1 [mem 0xe4000000-0xe6ffffff]
[    0.166980] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.167043] NET: Registered protocol family 2
[    0.167122] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.167471] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.167471] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.167471] TCP: Hash tables configured (established 131072 bind 65536)
[    0.167471] TCP reno registered
[    0.167471] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.167471] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.167471] NET: Registered protocol family 1
[    0.167471] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.167471] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.167471] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.167471] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.167471] pci 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.167471] pci 0000:00:10.0: PCI INT A disabled
[    0.167471] pci 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.167471] pci 0000:00:10.1: PCI INT A disabled
[    0.167471] pci 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.167471] pci 0000:00:10.2: PCI INT B disabled
[    0.167471] pci 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.167471] pci 0000:00:10.3: PCI INT B disabled
[    0.167471] pci 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.167471] pci 0000:00:10.4: PCI INT C disabled
[    0.167471] pci 0000:01:00.0: Boot video device
[    0.167471] PCI: CLS 32 bytes, default 64
[    0.167471] audit: initializing netlink socket (disabled)
[    0.167471] type=2000 audit(1350133037.164:1): initialized
[    0.196292] Trying to unpack rootfs image as initramfs...
[    0.232117] highmem bounce pool size: 64 pages
[    0.232125] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.240128] VFS: Disk quotas dquot_6.5.2
[    0.240230] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.241007] fuse init (API version 7.17)
[    0.241138] msgmni has been set to 1674
[    0.252430] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.252475] io scheduler noop registered
[    0.252478] io scheduler deadline registered
[    0.252487] io scheduler cfq registered (default)
[    0.252666] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.252701] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.252900] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.252907] ACPI: Power Button [PWRB]
[    0.252973] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.252977] ACPI: Power Button [PWRF]
[    0.254370] ERST: Table is not found!
[    0.254372] GHES: HEST is not enabled!
[    0.254563] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.274945] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.280174] isapnp: Scanning for PnP cards...
[    0.364671] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.410038] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.492729] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.516553] Linux agpgart interface v0.103
[    0.516596] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
[    0.518932] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    0.525001] brd: module loaded
[    0.525964] loop: module loaded
[    0.526509] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.526514] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.526535] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.526598] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.526621] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.526645] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.527179] Fixed MDIO Bus: probed
[    0.527209] tun: Universal TUN/TAP device driver, 1.6
[    0.527211] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.527312] PPP generic driver version 2.4.2
[    0.527441] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.527472] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.527498] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.527550] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.527610] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe8000000
[    0.575773] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.656521] hub 1-0:1.0: USB hub found
[    0.656529] hub 1-0:1.0: 8 ports detected
[    0.656643] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.656667] uhci_hcd: USB Universal Host Controller Interface driver
[    0.656710] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.656725] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.660298] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.660335] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    0.660552] hub 2-0:1.0: USB hub found
[    0.660558] hub 2-0:1.0: 2 ports detected
[    0.660654] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.660669] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.660738] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.660768] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    0.660939] hub 3-0:1.0: USB hub found
[    0.660944] hub 3-0:1.0: 2 ports detected
[    0.661027] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.661039] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.661098] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.661123] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.661296] hub 4-0:1.0: USB hub found
[    0.661301] hub 4-0:1.0: 2 ports detected
[    0.661391] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.661403] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.661460] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.661485] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e000
[    0.661658] hub 5-0:1.0: USB hub found
[    0.661663] hub 5-0:1.0: 2 ports detected
[    0.661821] usbcore: registered new interface driver libusual
[    0.661879] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.661881] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.662062] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.662227] mousedev: PS/2 mouse device common for all mice
[    0.662393] rtc_cmos 00:05: RTC can wake from S4
[    0.662569] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.662607] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.662694] device-mapper: uevent: version 1.0.3
[    0.662799] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.662863] EISA: Probing bus 0 at eisa.0
[    0.662868] EISA: Cannot allocate resource for mainboard
[    0.662872] Cannot allocate resource for EISA slot 1
[    0.662874] Cannot allocate resource for EISA slot 2
[    0.662877] Cannot allocate resource for EISA slot 3
[    0.662880] Cannot allocate resource for EISA slot 4
[    0.662882] Cannot allocate resource for EISA slot 5
[    0.662885] Cannot allocate resource for EISA slot 6
[    0.662888] Cannot allocate resource for EISA slot 7
[    0.662890] Cannot allocate resource for EISA slot 8
[    0.662893] EISA: Detected 0 cards.
[    0.662907] cpufreq-nforce2: No nForce2 chipset.
[    0.662911] cpuidle: using governor ladder
[    0.662913] cpuidle: using governor menu
[    0.662915] EFI Variables Facility v0.08 2004-May-17
[    0.663195] TCP cubic registered
[    0.663366] NET: Registered protocol family 10
[    0.663966] NET: Registered protocol family 17
[    0.663972] Registering the dns_resolver key type
[    0.664046] Using IPI No-Shortcut mode
[    0.665647] PM: Hibernation image not present or could not be loaded.
[    0.665672] registered taskstats version 1
[    0.802130] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.935906] isapnp: No Plug & Play device found
[    1.196143] Refined TSC clocksource calibration: 1808.313 MHz.
[    1.196152] Switching to clocksource tsc
[    1.225732] Freeing initrd memory: 19728k freed
[    1.259408]   Magic number: 0:715:986
[    1.259546] rtc_cmos 00:05: setting system clock to 2012-10-13 12:57:18 UTC (1350133038)
[    1.259552] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ (1 cpu cores) (version 2.20.00)
[    1.259609] powernow-k8: fid 0xa (1800 MHz), vid 0x6
[    1.259611] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.259676] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.259679] EDD information not available.
[    1.259899] Freeing unused kernel memory: 740k freed
[    1.260836] Write protecting the kernel text: 5820k
[    1.260855] Write protecting the kernel read-only data: 2376k
[    1.260858] NX-protecting the kernel data: 4420k
[    1.295122] udevd[82]: starting version 175
[    1.392087] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.454828] Floppy drive(s): fd0 is 1.44M
[    1.471965] FDC 0 is a post-1991 82077
[    1.490626] pata_via 0000:00:0f.1: version 0.3.4
[    1.490650] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.505175] scsi0 : pata_via
[    1.508367] scsi1 : pata_via
[    1.509996] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    1.510000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    1.515232] sata_via 0000:00:0b.0: version 2.6
[    1.515270] sata_via 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.515333] sata_via 0000:00:0b.0: routed to hard irq line 10
[    1.519060] scsi2 : sata_via
[    1.522483] scsi3 : sata_via
[    1.526007] scsi4 : sata_via
[    1.526107] ata3: SATA max UDMA/133 port i16@0xa000 bmdma 0xb000 irq 19
[    1.526112] ata4: SATA max UDMA/133 port i16@0xa400 bmdma 0xb008 irq 19
[    1.526116] ata5: PATA max UDMA/133 port i16@0xa800 bmdma 0xb010 irq 19
[    1.526199] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.526246] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.529340] scsi5 : sata_via
[    1.532224] scsi6 : sata_via
[    1.532329] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 20
[    1.532333] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 20
[    1.544119] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.544150] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.579045] Initializing USB Mass Storage driver...
[    1.584075] scsi7 : usb-storage 4-1:1.0
[    1.584206] usbcore: registered new interface driver usb-storage
[    1.584209] USB Mass Storage support registered.
[    1.681377] ata1.00: ATA-6: WDC WD1600BB-00DWA0, 15.05R15, max UDMA/100
[    1.681383] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.682939] ata1.01: ATA-7: Maxtor 6L080P0, BAJ41G20, max UDMA/133
[    1.682943] ata1.01: 160086528 sectors, multi 16: LBA 
[    1.697252] ata1.00: configured for UDMA/100
[    1.713736] ata1.01: configured for UDMA/133
[    1.713898] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BB-00D 15.0 PQ: 0 ANSI: 5
[    1.714177] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.714234] sd 0:0:0:0: [sda] Write Protect is off
[    1.714238] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.714262] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.714639] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.729777] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6L080P0   BAJ4 PQ: 0 ANSI: 5
[    1.730052]  sda: sda1 sda2 sda3
[    1.730170] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.730624] sd 0:0:1:0: [sdb] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.730681] sd 0:0:1:0: [sdb] Write Protect is off
[    1.730685] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.730709] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.730900] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.736016] ata6: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.748545]  sdb: sdb1
[    1.749055] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.808012] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    1.852044] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.860365] ata3.00: ATA-8: Hitachi HDS721032CLA362, JPFOA3EA, max UDMA/133
[    1.860369] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.876355] ata3.00: configured for UDMA/133
[    1.892331] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB02, max UDMA/33
[    1.908202] ata2.00: configured for UDMA/33
[    1.909523] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB02 PQ: 0 ANSI: 5
[    1.915505] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.915511] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.916160] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.916379] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.916598] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72103 JPFO PQ: 0 ANSI: 5
[    1.916810] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    1.916957] sd 2:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.917014] sd 2:0:0:0: [sdc] Write Protect is off
[    1.917017] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.917042] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.932435]  sdc: sdc1
[    1.932775] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.236051] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.244393] ata4.00: ATA-8: Hitachi HDS721032CLA362, JPFOA39C, max UDMA/133
[    2.244397] ata4.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.260378] ata4.00: configured for UDMA/133
[    2.260520] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDS72103 JPFO PQ: 0 ANSI: 5
[    2.260785] sd 3:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.260842] sd 3:0:0:0: [sdd] Write Protect is off
[    2.260845] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.260870] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.261260] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    2.277150]  sdd: sdd1
[    2.277503] sd 3:0:0:0: [sdd] Attached SCSI disk
[    2.588262] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.591247] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.594244] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.597245] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.601316] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    2.602804] sd 7:0:0:1: Attached scsi generic sg6 type 0
[    2.603056] sd 7:0:0:2: Attached scsi generic sg7 type 0
[    2.603275] sd 7:0:0:3: Attached scsi generic sg8 type 0
[    2.628019] ata7: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.868270] sd 7:0:0:2: [sdg] Attached SCSI removable disk
[    2.892273] sd 7:0:0:0: [sde] Attached SCSI removable disk
[    2.897254] sd 7:0:0:1: [sdf] Attached SCSI removable disk
[    2.902252] sd 7:0:0:3: [sdh] Attached SCSI removable disk
[    2.903456] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.903520] 8139too 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.904445] 8139too 0000:00:13.0: eth0: RealTek RTL8139 at 0xe800, 00:0f:ea:30:ba:a3, IRQ 18
[    2.922224] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:10.3/usb5/5-2/5-2:1.0/input/input3
[    2.922394] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:10.3-2/input0
[    2.922422] usbcore: registered new interface driver usbhid
[    2.922425] usbhid: USB HID core driver
[    4.513805] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    4.513810] vesafb: scrolling: redraw
[    4.513814] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.514281] vesafb: framebuffer at 0xd0000000, mapped to 0xf8500000, using 3072k, total 3072k
[    4.514471] Console: switching to colour frame buffer device 128x48
[    4.514505] fb0: VESA VGA frame buffer device
[    5.502233] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.025354] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.077952] udevd[394]: starting version 175
[   15.107473] Adding 3999740k swap on /dev/sda2.  Priority:-1 extents:1 across:3999740k 
[   15.145744] lp: driver loaded but no devices found
[   15.380260] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.511148] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.511197] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.606922] lp0: using parport0 (interrupt-driven).
[   15.855911] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.295943] type=1400 audit(1350133053.530:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=637 comm="apparmor_parser"
[   16.296691] type=1400 audit(1350133053.534:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=637 comm="apparmor_parser"
[   16.297024] type=1400 audit(1350133053.534:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=637 comm="apparmor_parser"
[   16.299496] nvidia: module license 'NVIDIA' taints kernel.
[   16.299503] Disabling lock debugging due to kernel taint
[   17.083671] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.083688] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.120179] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.49  Mon Apr 30 23:30:07 PDT 2012
[   17.635101] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   17.635107] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   17.635129] snd_via82xx 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   17.635282] snd_via82xx 0000:00:11.5: setting latency timer to 64
[   17.792711] ppdev: user-space parallel port driver
[   18.780306] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   19.131601] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[   19.231272] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   19.363135] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   19.590470] init: failsafe main process (912) killed by TERM signal
[   19.657601] Bluetooth: Core ver 2.16
[   19.657662] NET: Registered protocol family 31
[   19.657665] Bluetooth: HCI device and connection manager initialized
[   19.657670] Bluetooth: HCI socket layer initialized
[   19.657673] Bluetooth: L2CAP socket layer initialized
[   19.658502] Bluetooth: SCO socket layer initialized
[   19.694814] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.694820] Bluetooth: BNEP filters: protocol multicast
[   19.725157] Bluetooth: RFCOMM TTY layer initialized
[   19.725166] Bluetooth: RFCOMM socket layer initialized
[   19.725169] Bluetooth: RFCOMM ver 1.11
[   19.755812] type=1400 audit(1350133056.990:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=965 comm="apparmor_parser"
[   19.777629] type=1400 audit(1350133057.014:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=965 comm="apparmor_parser"
[   19.895088] type=1400 audit(1350133057.130:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1010 comm="apparmor_parser"
[   19.897251] type=1400 audit(1350133057.134:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
[   19.897600] type=1400 audit(1350133057.134:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   19.906237] type=1400 audit(1350133057.142:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1012 comm="apparmor_parser"
[   19.907044] type=1400 audit(1350133057.142:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1012 comm="apparmor_parser"
[   19.998427] 8139too 0000:00:13.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   20.770079] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   20.770097] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   20.770167] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   30.944016] eth0: no IPv6 routers present
[   82.400137] Marking TSC unstable due to cpufreq changes
[   82.400281] Switching to clocksource acpi_pm


```

---

### Post by Jean-Claude Tergal on 2012-10-13
> **cwsnyder said:**
> Disk 4 could also be slow responding, or shutting down between accesses.  Is it an internal drive, flash drive, or external USB drive?

Hi,

It's not always disk 4. It's random.
I have 4 hard drives:
1 IDE master with 3 partitions (home, / , swap)
1 IDE Slave & 2 SATAS

---

### Post by Rexilion on 2012-10-14
In the dmesg you posted, the drives are in perfect order.

Can you post a dmesg where this is not the case?

---

### Post by Jean-Claude Tergal on 2012-10-15
Here is the dmesg after a boot wherein /dev/sdh is used instead /dev/sdd

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic-pae 3.2.28)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Acer Aspire T135/K8VM800MAE, BIOS R01-B2 08/30/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fff0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CFFFF uncachable
[    0.000000]   D0000-D7FFF write-back
[    0.000000]   D8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 00E0000000 mask FFFC000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f5480] f5480
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 35968000 - 36cac000
[    0.000000] ACPI: RSDP 000f6e20 00014 (v00 VIAK8 )
[    0.000000] ACPI: RSDT 7fff3000 0002C (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: FACP 7fff3040 00074 (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: DSDT 7fff30c0 04366 (v01 VIAK8  AWRDACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 7fff0000 00040
[    0.000000] ACPI: APIC 7fff7440 0005A (v01 VIAK8  AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fff0
[    0.000000] On node 0 totalpages: 524159
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4968200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 293610 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7be3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520063
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=169efccc-0014-4396-84af-2dd3b136f285 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8388096 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007fff0)
[    0.000000] Memory: 2041056k/2097088k available (5818k kernel code, 55580k reserved, 2846k data, 740k init, 1183688k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1808.343 MHz processor.
[    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3616.68 BogoMIPS (lpj=7233372)
[    0.008010] pid_max: default: 32768 minimum: 301
[    0.008043] Security Framework initialized
[    0.008077] AppArmor: AppArmor initialized
[    0.008080] Yama: becoming mindful.
[    0.008164] Mount-cache hash table entries: 512
[    0.008342] Initializing cgroup subsys cpuacct
[    0.008350] Initializing cgroup subsys memory
[    0.008363] Initializing cgroup subsys devices
[    0.008367] Initializing cgroup subsys freezer
[    0.008371] Initializing cgroup subsys blkio
[    0.008381] Initializing cgroup subsys perf_event
[    0.008414] mce: CPU supports 5 MCE banks
[    0.008705] SMP alternatives: switching to UP code
[    0.022081] Freeing SMP alternatives: 24k freed
[    0.022110] ACPI: Core revision 20110623
[    0.028158] ftrace: allocating 26555 entries in 52 pages
[    0.032103] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032477] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.073384] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
[    0.076004] Performance Events: AMD PMU driver.
[    0.076004] ... version:                0
[    0.076004] ... bit width:              48
[    0.076004] ... generic registers:      4
[    0.076004] ... value mask:             0000ffffffffffff
[    0.076004] ... max period:             00007fffffffffff
[    0.076004] ... fixed-purpose events:   0
[    0.076004] ... event mask:             000000000000000f
[    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.076004] Brought up 1 CPUs
[    0.076004] Total of 1 processors activated (3616.68 BogoMIPS).
[    0.076004] devtmpfs: initialized
[    0.076004] EVM: security.selinux
[    0.076004] EVM: security.SMACK64
[    0.076004] EVM: security.capability
[    0.076004] PM: Registering ACPI NVS region at 7fff0000 (12288 bytes)
[    0.076004] print_constraints: dummy: 
[    0.076004] RTC time:  4:38:32, date: 10/15/12
[    0.076004] NET: Registered protocol family 16
[    0.076004] EISA bus registered
[    0.076004] node 0 link 0: io port [1000, fffff]
[    0.076004] TOM: 0000000080000000 aka 2048M
[    0.076004] node 0 link 0: mmio [a0000, bffff]
[    0.076004] node 0 link 0: mmio [80000000, ffb7ffff]
[    0.076004] bus: [00, ff] on node 0 link 0
[    0.076004] bus: 00 index 0 [io  0x0000-0xffff]
[    0.076004] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.076004] bus: 00 index 2 [mem 0x80000000-0xfcffffffff]
[    0.076004] ACPI: bus type pci registered
[    0.082455] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.082460] PCI: PCI BIOS revision 2.10 entry at 0xfb150, last bus=1
[    0.082462] PCI: Using configuration type 1 for base access
[    0.084190] bio: create slab <bio-0> at 0
[    0.084315] ACPI: Added _OSI(Module Device)
[    0.084318] ACPI: Added _OSI(Processor Device)
[    0.084320] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.084323] ACPI: Added _OSI(Processor Aggregator Device)
[    0.084975] ACPI: EC: Look up EC in DSDT
[    0.085795] ACPI: Actual Package length (6) is larger than NumElements field (2), truncated
[    0.085800] 
[    0.088163] ACPI: Interpreter enabled
[    0.088172] ACPI: (supports S0 S3 S4 S5)
[    0.088194] ACPI: Using IOAPIC for interrupt routing
[    0.092429] ACPI: No dock devices found.
[    0.092433] HEST: Table not found.
[    0.092440] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.092517] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.092674] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.092678] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.092682] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.092686] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.092689] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.092712] pci 0000:00:00.0: [1106:0204] type 0 class 0x000600
[    0.092722] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe3ffffff pref]
[    0.092805] pci 0000:00:00.1: [1106:1204] type 0 class 0x000600
[    0.092846] pci 0000:00:00.2: [1106:2204] type 0 class 0x000600
[    0.092886] pci 0000:00:00.3: [1106:3204] type 0 class 0x000600
[    0.092924] pci 0000:00:00.4: [1106:4204] type 0 class 0x000600
[    0.092965] pci 0000:00:00.7: [1106:7204] type 0 class 0x000600
[    0.093008] pci 0000:00:01.0: [1106:b188] type 1 class 0x000604
[    0.093055] pci 0000:00:01.0: supports D1
[    0.093082] pci 0000:00:0b.0: [1106:3249] type 0 class 0x000104
[    0.093098] pci 0000:00:0b.0: reg 10: [io  0xa000-0xa00f]
[    0.093108] pci 0000:00:0b.0: reg 14: [io  0xa400-0xa40f]
[    0.093118] pci 0000:00:0b.0: reg 18: [io  0xa800-0xa80f]
[    0.093127] pci 0000:00:0b.0: reg 1c: [io  0xac00-0xac0f]
[    0.093136] pci 0000:00:0b.0: reg 20: [io  0xb000-0xb01f]
[    0.093146] pci 0000:00:0b.0: reg 24: [io  0xb400-0xb4ff]
[    0.093155] pci 0000:00:0b.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.093199] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000101
[    0.093214] pci 0000:00:0f.0: reg 10: [io  0xb800-0xb807]
[    0.093224] pci 0000:00:0f.0: reg 14: [io  0xbc00-0xbc03]
[    0.093233] pci 0000:00:0f.0: reg 18: [io  0xc000-0xc007]
[    0.093243] pci 0000:00:0f.0: reg 1c: [io  0xc400-0xc403]
[    0.093252] pci 0000:00:0f.0: reg 20: [io  0xc800-0xc80f]
[    0.093262] pci 0000:00:0f.0: reg 24: [io  0xcc00-0xccff]
[    0.093309] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.093351] pci 0000:00:0f.1: reg 20: [io  0xd000-0xd00f]
[    0.093411] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.093450] pci 0000:00:10.0: reg 20: [io  0xd400-0xd41f]
[    0.093486] pci 0000:00:10.0: supports D1 D2
[    0.093489] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093494] pci 0000:00:10.0: PME# disabled
[    0.093511] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.093550] pci 0000:00:10.1: reg 20: [io  0xd800-0xd81f]
[    0.093587] pci 0000:00:10.1: supports D1 D2
[    0.093589] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093594] pci 0000:00:10.1: PME# disabled
[    0.093610] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.093649] pci 0000:00:10.2: reg 20: [io  0xdc00-0xdc1f]
[    0.093686] pci 0000:00:10.2: supports D1 D2
[    0.093688] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093693] pci 0000:00:10.2: PME# disabled
[    0.093710] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.093748] pci 0000:00:10.3: reg 20: [io  0xe000-0xe01f]
[    0.093785] pci 0000:00:10.3: supports D1 D2
[    0.093787] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093792] pci 0000:00:10.3: PME# disabled
[    0.093809] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.093825] pci 0000:00:10.4: reg 10: [mem 0xe8000000-0xe80000ff]
[    0.093885] pci 0000:00:10.4: supports D1 D2
[    0.093888] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093892] pci 0000:00:10.4: PME# disabled
[    0.093913] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
[    0.093967] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.094011] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
[    0.094027] pci 0000:00:11.5: reg 10: [io  0xe400-0xe4ff]
[    0.094091] pci 0000:00:11.5: supports D1 D2
[    0.094111] pci 0000:00:13.0: [10ec:8139] type 0 class 0x000200
[    0.094127] pci 0000:00:13.0: reg 10: [io  0xe800-0xe8ff]
[    0.094136] pci 0000:00:13.0: reg 14: [mem 0xe8001000-0xe80010ff]
[    0.094192] pci 0000:00:13.0: supports D1 D2
[    0.094195] pci 0000:00:13.0: PME# supported from D1 D2 D3hot D3cold
[    0.094200] pci 0000:00:13.0: PME# disabled
[    0.094217] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.094241] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.094261] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.094280] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.094305] PCI: peer root bus 00 res updated from pci conf
[    0.094342] pci 0000:01:00.0: [10de:0221] type 0 class 0x000300
[    0.094355] pci 0000:01:00.0: reg 10: [mem 0xe4000000-0xe4ffffff]
[    0.094362] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff pref]
[    0.094370] pci 0000:01:00.0: reg 18: [mem 0xe5000000-0xe5ffffff]
[    0.094389] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.094439] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.094446] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe6ffffff]
[    0.094451] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.094459] pci_bus 0000:00: on NUMA node 0
[    0.094464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.094686]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.119426] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[    0.119520] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.119615] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.119711] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[    0.119782] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.119850] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.119918] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.119986] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.120119] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.120236] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.120373] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.120496] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.120699] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.120702] vgaarb: loaded
[    0.120704] vgaarb: bridge control possible 0000:01:00.0
[    0.120875] i2c-core: driver [aat2870] using legacy suspend method
[    0.120877] i2c-core: driver [aat2870] using legacy resume method
[    0.120997] SCSI subsystem initialized
[    0.121076] libata version 3.00 loaded.
[    0.121151] usbcore: registered new interface driver usbfs
[    0.121168] usbcore: registered new interface driver hub
[    0.121199] usbcore: registered new device driver usb
[    0.121333] PCI: Using ACPI for IRQ routing
[    0.121339] PCI: pci_cache_line_size set to 64 bytes
[    0.121420] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.121424] reserve RAM buffer: 000000007fff0000 - 000000007fffffff 
[    0.121575] NetLabel: Initializing
[    0.121577] NetLabel:  domain hash size = 128
[    0.121579] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.121593] NetLabel:  unlabeled traffic allowed by default
[    0.131313] AppArmor: AppArmor Filesystem Enabled
[    0.131361] pnp: PnP ACPI init
[    0.131386] ACPI: bus type pnp registered
[    0.131599] pnp 00:00: [mem 0x000d0000-0x000d7fff]
[    0.131603] pnp 00:00: [mem 0x000f0000-0x000f7fff]
[    0.131606] pnp 00:00: [mem 0x000f8000-0x000fbfff]
[    0.131609] pnp 00:00: [mem 0x000fc000-0x000fffff]
[    0.131612] pnp 00:00: [mem 0x7fff0000-0x7fffffff]
[    0.131615] pnp 00:00: [mem 0xffff0000-0xffffffff]
[    0.131617] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.131620] pnp 00:00: [mem 0x00100000-0x7ffeffff]
[    0.131624] pnp 00:00: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.131627] pnp 00:00: [mem 0xfec00000-0xfec00fff]
[    0.131630] pnp 00:00: [mem 0xfee00000-0xfee00fff]
[    0.131633] pnp 00:00: [mem 0xfff80000-0xfffeffff]
[    0.131712] system 00:00: [mem 0x000d0000-0x000d7fff] has been reserved
[    0.131716] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.131720] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.131724] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.131727] system 00:00: [mem 0x7fff0000-0x7fffffff] could not be reserved
[    0.131731] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
[    0.131735] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.131739] system 00:00: [mem 0x00100000-0x7ffeffff] could not be reserved
[    0.131743] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.131747] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.131751] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.131756] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.131822] pnp 00:01: [bus 00-ff]
[    0.131826] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.131829] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.131832] pnp 00:01: [io  0x0d00-0xffff window]
[    0.131835] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.131838] pnp 00:01: [mem 0x000c0000-0x000dffff window]
[    0.131841] pnp 00:01: [mem 0x80000000-0xfebfffff window]
[    0.131895] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.131917] pnp 00:02: [io  0x4000-0x407f]
[    0.131919] pnp 00:02: [io  0x40f0-0x40ff]
[    0.131922] pnp 00:02: [io  0x5000-0x500f]
[    0.131975] system 00:02: [io  0x4000-0x407f] has been reserved
[    0.131978] system 00:02: [io  0x40f0-0x40ff] has been reserved
[    0.131982] system 00:02: [io  0x5000-0x500f] has been reserved
[    0.131986] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.132371] pnp 00:03: [io  0x0010-0x001f]
[    0.132373] pnp 00:03: [io  0x0022-0x003f]
[    0.132376] pnp 00:03: [io  0x0044-0x005f]
[    0.132379] pnp 00:03: [io  0x0062-0x0063]
[    0.132381] pnp 00:03: [io  0x0065-0x006f]
[    0.132384] pnp 00:03: [io  0x0074-0x007f]
[    0.132386] pnp 00:03: [io  0x0091-0x0093]
[    0.132389] pnp 00:03: [io  0x00a2-0x00bf]
[    0.132392] pnp 00:03: [io  0x00e0-0x00ef]
[    0.132394] pnp 00:03: [io  0x04d0-0x04d1]
[    0.132397] pnp 00:03: [io  0x0290-0x029f]
[    0.132400] pnp 00:03: [io  0x0800-0x0805]
[    0.132486] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.132490] system 00:03: [io  0x0290-0x029f] has been reserved
[    0.132494] system 00:03: [io  0x0800-0x0805] has been reserved
[    0.132498] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.132514] pnp 00:04: [dma 4]
[    0.132517] pnp 00:04: [io  0x0000-0x000f]
[    0.132519] pnp 00:04: [io  0x0080-0x0090]
[    0.132522] pnp 00:04: [io  0x0094-0x009f]
[    0.132524] pnp 00:04: [io  0x00c0-0x00df]
[    0.132561] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.132574] pnp 00:05: [io  0x0070-0x0073]
[    0.132588] pnp 00:05: [irq 8]
[    0.132632] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.132643] pnp 00:06: [io  0x0061]
[    0.132683] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.132693] pnp 00:07: [io  0x00f0-0x00ff]
[    0.132699] pnp 00:07: [irq 13]
[    0.132736] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.132877] pnp 00:08: [io  0x03f0-0x03f5]
[    0.132880] pnp 00:08: [io  0x03f7]
[    0.132885] pnp 00:08: [irq 6]
[    0.132888] pnp 00:08: [dma 2]
[    0.132944] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.133127] pnp 00:09: [io  0x03f8-0x03ff]
[    0.133133] pnp 00:09: [irq 4]
[    0.133217] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.133413] pnp 00:0a: [io  0x02f8-0x02ff]
[    0.133419] pnp 00:0a: [irq 3]
[    0.133487] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.133691] pnp 00:0b: [io  0x0378-0x037f]
[    0.133697] pnp 00:0b: [irq 7]
[    0.133771] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.133872] pnp 00:0c: [io  0x0060]
[    0.133875] pnp 00:0c: [io  0x0064]
[    0.133884] pnp 00:0c: [irq 1]
[    0.133927] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.133951] pnp: PnP ACPI: found 13 devices
[    0.133953] ACPI: ACPI bus type pnp unregistered
[    0.133958] PnPBIOS: Disabled by ACPI PNP
[    0.170863] Switching to clocksource acpi_pm
[    0.170897] PCI: max bus depth: 1 pci_try_num: 2
[    0.170924] pci 0000:00:0b.0: BAR 6: assigned [mem 0x80000000-0x8000ffff pref]
[    0.170930] pci 0000:01:00.0: BAR 6: assigned [mem 0xe6000000-0xe601ffff pref]
[    0.170934] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.170940] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe6ffffff]
[    0.170944] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.170959] pci 0000:00:01.0: setting latency timer to 64
[    0.170964] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.170967] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.170970] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
[    0.170974] pci_bus 0000:01: resource 1 [mem 0xe4000000-0xe6ffffff]
[    0.170977] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.171039] NET: Registered protocol family 2
[    0.171118] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.171467] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.171467] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.171467] TCP: Hash tables configured (established 131072 bind 65536)
[    0.171467] TCP reno registered
[    0.171467] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.171467] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.171467] NET: Registered protocol family 1
[    0.171467] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.171467] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.171467] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.171467] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.171467] pci 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.171467] pci 0000:00:10.0: PCI INT A disabled
[    0.171467] pci 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.171467] pci 0000:00:10.1: PCI INT A disabled
[    0.171467] pci 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.171467] pci 0000:00:10.2: PCI INT B disabled
[    0.171467] pci 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.171467] pci 0000:00:10.3: PCI INT B disabled
[    0.171467] pci 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.171467] pci 0000:00:10.4: PCI INT C disabled
[    0.171467] pci 0000:01:00.0: Boot video device
[    0.171467] PCI: CLS 32 bytes, default 64
[    0.171467] audit: initializing netlink socket (disabled)
[    0.171467] type=2000 audit(1350275911.168:1): initialized
[    0.200293] Trying to unpack rootfs image as initramfs...
[    0.236116] highmem bounce pool size: 64 pages
[    0.236125] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.244128] VFS: Disk quotas dquot_6.5.2
[    0.244229] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.245006] fuse init (API version 7.17)
[    0.245137] msgmni has been set to 1674
[    0.256429] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.256473] io scheduler noop registered
[    0.256476] io scheduler deadline registered
[    0.256485] io scheduler cfq registered (default)
[    0.256663] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.256698] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.256897] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.256904] ACPI: Power Button [PWRB]
[    0.256970] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.256974] ACPI: Power Button [PWRF]
[    0.258366] ERST: Table is not found!
[    0.258369] GHES: HEST is not enabled!
[    0.258560] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.278942] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.284171] isapnp: Scanning for PnP cards...
[    0.368674] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.414037] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.496725] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.520548] Linux agpgart interface v0.103
[    0.520590] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
[    0.522928] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    0.528996] brd: module loaded
[    0.529959] loop: module loaded
[    0.530504] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.530508] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.530530] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.530592] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.530616] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.530640] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.531173] Fixed MDIO Bus: probed
[    0.531204] tun: Universal TUN/TAP device driver, 1.6
[    0.531206] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.531307] PPP generic driver version 2.4.2
[    0.531435] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.531467] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.531493] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.531545] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.531605] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe8000000
[    0.579775] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.660527] hub 1-0:1.0: USB hub found
[    0.660535] hub 1-0:1.0: 8 ports detected
[    0.660649] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.660674] uhci_hcd: USB Universal Host Controller Interface driver
[    0.660716] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.660731] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.664303] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.664339] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    0.664557] hub 2-0:1.0: USB hub found
[    0.664563] hub 2-0:1.0: 2 ports detected
[    0.664659] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.664673] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.664742] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.664772] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    0.664943] hub 3-0:1.0: USB hub found
[    0.664948] hub 3-0:1.0: 2 ports detected
[    0.665031] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.665044] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.665103] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.665129] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.665302] hub 4-0:1.0: USB hub found
[    0.665307] hub 4-0:1.0: 2 ports detected
[    0.665394] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.665406] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.665463] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.665489] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e000
[    0.665662] hub 5-0:1.0: USB hub found
[    0.665666] hub 5-0:1.0: 2 ports detected
[    0.665826] usbcore: registered new interface driver libusual
[    0.665884] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.665886] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.666067] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.666230] mousedev: PS/2 mouse device common for all mice
[    0.666395] rtc_cmos 00:05: RTC can wake from S4
[    0.666572] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.666609] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.666697] device-mapper: uevent: version 1.0.3
[    0.666802] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.666866] EISA: Probing bus 0 at eisa.0
[    0.666871] EISA: Cannot allocate resource for mainboard
[    0.666874] Cannot allocate resource for EISA slot 1
[    0.666877] Cannot allocate resource for EISA slot 2
[    0.666880] Cannot allocate resource for EISA slot 3
[    0.666882] Cannot allocate resource for EISA slot 4
[    0.666885] Cannot allocate resource for EISA slot 5
[    0.666888] Cannot allocate resource for EISA slot 6
[    0.666890] Cannot allocate resource for EISA slot 7
[    0.666893] Cannot allocate resource for EISA slot 8
[    0.666895] EISA: Detected 0 cards.
[    0.666910] cpufreq-nforce2: No nForce2 chipset.
[    0.666913] cpuidle: using governor ladder
[    0.666915] cpuidle: using governor menu
[    0.666918] EFI Variables Facility v0.08 2004-May-17
[    0.667197] TCP cubic registered
[    0.667369] NET: Registered protocol family 10
[    0.667968] NET: Registered protocol family 17
[    0.667974] Registering the dns_resolver key type
[    0.668051] Using IPI No-Shortcut mode
[    0.669204] PM: Hibernation image not present or could not be loaded.
[    0.669224] registered taskstats version 1
[    0.806142] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.939952] isapnp: No Plug & Play device found
[    1.200190] Refined TSC clocksource calibration: 1808.313 MHz.
[    1.200199] Switching to clocksource tsc
[    1.229794] Freeing initrd memory: 19728k freed
[    1.263483]   Magic number: 0:155:616
[    1.263623] rtc_cmos 00:05: setting system clock to 2012-10-15 04:38:33 UTC (1350275913)
[    1.263629] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ (1 cpu cores) (version 2.20.00)
[    1.263686] powernow-k8: fid 0xa (1800 MHz), vid 0x6
[    1.263688] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.263749] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.263752] EDD information not available.
[    1.263975] Freeing unused kernel memory: 740k freed
[    1.264876] Write protecting the kernel text: 5820k
[    1.264894] Write protecting the kernel read-only data: 2376k
[    1.264897] NX-protecting the kernel data: 4420k
[    1.298984] udevd[82]: starting version 175
[    1.396086] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.442662] Floppy drive(s): fd0 is 1.44M
[    1.473956] FDC 0 is a post-1991 82077
[    1.501902] sata_via 0000:00:0b.0: version 2.6
[    1.501935] sata_via 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.501994] sata_via 0000:00:0b.0: routed to hard irq line 10
[    1.517462] scsi0 : sata_via
[    1.520749] scsi1 : sata_via
[    1.523723] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.524504] scsi2 : sata_via
[    1.524624] ata1: SATA max UDMA/133 port i16@0xa000 bmdma 0xb000 irq 19
[    1.524629] ata2: SATA max UDMA/133 port i16@0xa400 bmdma 0xb008 irq 19
[    1.524633] ata3: PATA max UDMA/133 port i16@0xa800 bmdma 0xb010 irq 19
[    1.524754] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.524803] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.527755] scsi3 : sata_via
[    1.532191] scsi4 : sata_via
[    1.532295] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 20
[    1.532299] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 20
[    1.532369] pata_via 0000:00:0f.1: version 0.3.4
[    1.532387] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.536268] scsi5 : pata_via
[    1.540063] scsi6 : pata_via
[    1.541724] ata6: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    1.541729] ata7: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    1.545446] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.581115] Initializing USB Mass Storage driver...
[    1.585097] scsi7 : usb-storage 4-1:1.0
[    1.585221] usbcore: registered new interface driver usb-storage
[    1.585224] USB Mass Storage support registered.
[    1.717368] ata6.00: ATA-6: WDC WD1600BB-00DWA0, 15.05R15, max UDMA/100
[    1.717374] ata6.00: 312581808 sectors, multi 16: LBA48 
[    1.718945] ata6.01: ATA-7: Maxtor 6L080P0, BAJ41G20, max UDMA/133
[    1.718949] ata6.01: 160086528 sectors, multi 16: LBA 
[    1.733234] ata6.00: configured for UDMA/100
[    1.736017] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.753703] ata6.01: configured for UDMA/133
[    1.812010] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    1.844042] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.852381] ata1.00: ATA-8: Hitachi HDS721032CLA362, JPFOA3EA, max UDMA/133
[    1.852385] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.868376] ata1.00: configured for UDMA/133
[    1.868534] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72103 JPFO PQ: 0 ANSI: 5
[    1.870134] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.870223] sd 0:0:0:0: [sda] Write Protect is off
[    1.870227] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.870251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.870731] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.883681]  sda: sda1
[    1.884089] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.188050] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.196393] ata2.00: ATA-8: Hitachi HDS721032CLA362, JPFOA39C, max UDMA/133
[    2.196397] ata2.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.212380] ata2.00: configured for UDMA/133
[    2.212520] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72103 JPFO PQ: 0 ANSI: 5
[    2.212782] sd 1:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.212839] sd 1:0:0:0: [sdb] Write Protect is off
[    2.212843] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.212867] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.213249] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.230661]  sdb: sdb1
[    2.231025] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.580022] ata5: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.590824] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1600BB-00D 15.0 PQ: 0 ANSI: 5
[    2.591276] sd 5:0:0:0: [sdc] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.591334] sd 5:0:0:0: [sdc] Write Protect is off
[    2.591338] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.591362] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.592072] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.592495] scsi: waiting for bus probes to complete ...
[    2.595264] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.598252] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.601268] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.604255] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.608223] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    2.609689] sd 7:0:0:1: Attached scsi generic sg4 type 0
[    2.609900] sd 7:0:0:2: Attached scsi generic sg5 type 0
[    2.610102] sd 7:0:0:3: Attached scsi generic sg6 type 0
[    2.610324]  sdc: sdc1 sdc2 sdc3
[    2.610439] scsi 5:0:1:0: Direct-Access     ATA      Maxtor 6L080P0   BAJ4 PQ: 0 ANSI: 5
[    2.610687] sd 5:0:1:0: [sdh] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    2.610745] sd 5:0:1:0: [sdh] Write Protect is off
[    2.610749] sd 5:0:1:0: [sdh] Mode Sense: 00 3a 00 00
[    2.610831] sd 5:0:1:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.611228] sd 5:0:1:0: Attached scsi generic sg7 type 0
[    2.631426]  sdh: sdh1
[    2.631603] sd 5:0:0:0: [sdc] Attached SCSI disk
[    2.631894] sd 5:0:1:0: [sdh] Attached SCSI disk
[    2.772346] ata7.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB02, max UDMA/33
[    2.788277] ata7.00: configured for UDMA/33
[    2.789572] scsi 6:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB02 PQ: 0 ANSI: 5
[    2.795469] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.795476] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.795677] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    2.795870] sr 6:0:0:0: Attached scsi generic sg8 type 5
[    2.875277] sd 7:0:0:2: [sdf] Attached SCSI removable disk
[    2.894277] sd 7:0:0:3: [sdg] Attached SCSI removable disk
[    2.899260] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    2.904259] sd 7:0:0:1: [sde] Attached SCSI removable disk
[    2.905176] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.905237] 8139too 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.906127] 8139too 0000:00:13.0: eth0: RealTek RTL8139 at 0xe800, 00:0f:ea:30:ba:a3, IRQ 18
[    2.924290] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:10.3/usb5/5-2/5-2:1.0/input/input3
[    2.924464] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:10.3-2/input0
[    2.924492] usbcore: registered new interface driver usbhid
[    2.924495] usbhid: USB HID core driver
[    4.586893] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    4.586897] vesafb: scrolling: redraw
[    4.586901] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.587369] vesafb: framebuffer at 0xd0000000, mapped to 0xf8500000, using 3072k, total 3072k
[    4.587560] Console: switching to colour frame buffer device 128x48
[    4.587594] fb0: VESA VGA frame buffer device
[    5.582064] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   15.168285] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.201330] udevd[394]: starting version 175
[   15.268910] lp: driver loaded but no devices found
[   15.291667] Adding 3999740k swap on /dev/sdc2.  Priority:-1 extents:1 across:3999740k 
[   15.548285] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.548335] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.645984] lp0: using parport0 (interrupt-driven).
[   15.696182] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.078233] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro
[   16.463648] nvidia: module license 'NVIDIA' taints kernel.
[   16.463654] Disabling lock debugging due to kernel taint
[   17.461883] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.461898] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.473977] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.49  Mon Apr 30 23:30:07 PDT 2012
[   17.833999] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.854807] type=1400 audit(1350275930.087:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=736 comm="apparmor_parser"
[   17.855474] type=1400 audit(1350275930.087:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=736 comm="apparmor_parser"
[   17.855815] type=1400 audit(1350275930.087:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=736 comm="apparmor_parser"
[   18.112585] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   18.535980] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   18.535986] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   18.566360] snd_via82xx 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   18.566522] snd_via82xx 0000:00:11.5: setting latency timer to 64
[   18.581564] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.887087] ppdev: user-space parallel port driver
[   19.389817] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   20.021169] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[   20.177023] EXT4-fs (sdh1): mounted filesystem with ordered data mode. Opts: (null)
[   33.981711] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   34.154759] init: failsafe main process (991) killed by TERM signal
[   34.217387] Bluetooth: Core ver 2.16
[   34.217447] NET: Registered protocol family 31
[   34.217450] Bluetooth: HCI device and connection manager initialized
[   34.217455] Bluetooth: HCI socket layer initialized
[   34.217458] Bluetooth: L2CAP socket layer initialized
[   34.220983] Bluetooth: SCO socket layer initialized
[   34.264473] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.264479] Bluetooth: BNEP filters: protocol multicast
[   34.284078] Bluetooth: RFCOMM TTY layer initialized
[   34.284087] Bluetooth: RFCOMM socket layer initialized
[   34.284090] Bluetooth: RFCOMM ver 1.11
[   34.318312] type=1400 audit(1350275946.551:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1045 comm="apparmor_parser"
[   34.337216] type=1400 audit(1350275946.571:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1045 comm="apparmor_parser"
[   34.460139] type=1400 audit(1350275946.695:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1090 comm="apparmor_parser"
[   34.460812] type=1400 audit(1350275946.695:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1090 comm="apparmor_parser"
[   34.461158] type=1400 audit(1350275946.695:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1090 comm="apparmor_parser"
[   34.470196] type=1400 audit(1350275946.703:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1092 comm="apparmor_parser"
[   34.471006] type=1400 audit(1350275946.703:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1092 comm="apparmor_parser"
[   34.475549] type=1400 audit(1350275946.707:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1093 comm="apparmor_parser"
[   34.475924] type=1400 audit(1350275946.707:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1093 comm="apparmor_parser"
[   34.482791] type=1400 audit(1350275946.715:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1095 comm="apparmor_parser"
[   34.552938] 8139too 0000:00:13.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.332934] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   35.332950] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   35.333021] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   45.568018] eth0: no IPv6 routers present
[   97.108152] Marking TSC unstable due to cpufreq changes
[   97.108221] Switching to clocksource acpi_pm
[  154.095987] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56686 PROTO=2 
[  154.096776] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56687 PROTO=2 
[  278.692046] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56688 PROTO=2 
[  278.692898] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56689 PROTO=2 
[  403.468107] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56690 PROTO=2 
[  403.468596] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56691 PROTO=2 
[  528.401778] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56692 PROTO=2 
[  528.402613] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56693 PROTO=2 
[  653.348645] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56694 PROTO=2 
[  653.349421] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56695 PROTO=2 
[  778.482487] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56696 PROTO=2 
[  778.483226] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56697 PROTO=2 
[  903.332601] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56698 PROTO=2 
[  903.333093] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56699 PROTO=2 
[ 1028.964944] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56700 PROTO=2 
[ 1028.965442] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56701 PROTO=2 
[ 1153.811864] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56702 PROTO=2 
[ 1153.812485] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56703 PROTO=2 
[ 1278.450771] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56704 PROTO=2 
[ 1278.451326] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56705 PROTO=2 
[ 1403.757574] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56706 PROTO=2 
[ 1403.758222] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56707 PROTO=2 
[ 1529.184209] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56708 PROTO=2 
[ 1529.184971] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56709 PROTO=2 
[ 1653.527418] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56710 PROTO=2 
[ 1653.528045] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e0:a1:d7:12:b8:08:08:00 SRC=172.16.255.254 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1 ID=56711 PROTO=2 


```

---

### Post by Rexilion on 2012-10-15
Yes, this is a race condition:

> [    2.595264] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.598252] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.601268] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.604255] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0

Your card reader is sometimes faster to initialize then one or more of your disks:

> [    2.875277] sd 7:0:0:2: [sdf] Attached SCSI removable disk
[    2.894277] sd 7:0:0:3: [sdg] Attached SCSI removable disk
[    2.899260] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    2.904259] sd 7:0:0:1: [sde] Attached SCSI removable disk

Compare this to the dmesg where your disks were detected first:

> [    2.868270] sd 7:0:0:2: [sdg] Attached SCSI removable disk
[    2.892273] sd 7:0:0:0: [sde] Attached SCSI removable disk
[    2.897254] sd 7:0:0:1: [sdf] Attached SCSI removable disk
[    2.902252] sd 7:0:0:3: [sdh] Attached SCSI removable disk

You can see that in both the dmesg examples you gave that your last disk is handled after your generic USB reader. Which causes it to come after.

You can check if my hypothesis holds. Everytime your disk layout is 'scrambled', there should be four 'emtpy holes' between their numbering. E.g.

> sda
sdb
< card reader >
sdh
sdi

or

> < card reader >
sde
sdf
sdg
sdh

or

> sda
sdb
sdc
< card reader >
sdh


Things work as expected, when you see this:

> sda
sdb
sdc
sdd
< card reader >

You should be able to fix this by creating static udev rules. You will lose some flexibility when you add or remove disks, but should provide a solid and reliable workaround for this race condition.

---

### Post by Jean-Claude Tergal on 2012-10-15
> **Rexilion said:**
> Yes, this is a race condition:

Yes! It's clearly now.


> **Rexilion said:**
>  You can check if my hypothesis holds. Everytime your disk layout is 'scrambled', there should be four 'emtpy holes' between their numbering. E.g.

Ok. I will check that.

> **Rexilion said:**
> 
You should be able to fix this by creating static udev rules. You will lose some flexibility when you add or remove disks, but should provide a solid and reliable workaround for this race condition.
Ok. I will try creating udev rules. But just for test. Random assignations are not annoying for me.
I'm relieved that my system is healthy. It's the more important.

I will give a feedback after testing.

Meantime: a great thank for your help Rexilion!=D>

---

### Post by Jean-Claude Tergal on 2012-10-19
Hi! Here are some news.

So I've read the doc about udev and tried to test it.
It seems that I misunderstood something...
I've read [here]("http://www.uubu.fr/spip.php?article188") (sorry, it's in french) that kernel and NAME can't specify differents names. So what is the feature of NAME? 

Is it really possible to change the sdx assigned by the kernel?

I've create a file in /etc/udev/rules.d

Here is the content of the file 
```
KERNELS=="0:0:0:0", NAME="hitachi1"
```After reboot, I can see in console (it seems to be right, i see hitachi instead sda):
```
cyrille@ordi-cyrille:/dev/disk/by-uuid$ ls -la
total 0
drwxr-xr-x 2 root root 160 oct.  19 20:42 .
drwxr-xr-x 6 root root 120 oct.  19 20:42 ..
lrwxrwxrwx 1 root root  10 oct.  19 20:42 169efccc-0014-4396-84af-2dd3b136f285 -> ../../sdc1
lrwxrwxrwx 1 root root  14 oct.  19 20:42 1b7d773f-af2a-4192-90df-6c111fde6ab3 -> ../../hitachi1
lrwxrwxrwx 1 root root  10 oct.  19 20:42 4f3b2927-5550-4411-b743-180603830967 -> ../../sdc2
lrwxrwxrwx 1 root root  10 oct.  19 20:42 798eba91-c245-4767-9584-91cd4c5a4d47 -> ../../sdd1
lrwxrwxrwx 1 root root  10 oct.  19 20:42 edd8a3ac-2952-4a5d-bb13-5f8f7eefc761 -> ../../sdb1
lrwxrwxrwx 1 root root  10 oct.  19 20:42 f81b8da4-9ec1-43cc-8e6b-46d24d035de5 -> ../../sdc3
```However, KDE partitions manager show me this (it seems to be wrong, i still see "sda"):
[IMG]http://nsa32.casimages.com/img/2012/10/19/121019092836108820.jpg[/IMG]

Has someone any idea?

---

### Post by Rexilion on 2012-10-20
How are the disk listed in /dev?

---

### Post by Jean-Claude Tergal on 2012-10-20
Thank you for the answer.
Here is the content of /dev:

```

cyrille@ordi-cyrille:/dev$ ls -la | egrep 'hitach|sd'
brw-rw----   1 root disk      8,   1 oct.  20 10:43 hitachi1
brw-------   1 root root      8,   0 oct.  20 10:42 sda
brw-------   1 root root      8,   1 oct.  20 10:42 sda1
brw-rw----   1 root disk      8,  16 oct.  20 10:43 sdb
brw-rw----   1 root disk      8,  17 oct.  20 10:43 sdb1
brw-rw----   1 root disk      8,  32 oct.  20 10:43 sdc
brw-rw----   1 root disk      8,  33 oct.  20 10:43 sdc1
brw-rw----   1 root disk      8,  34 oct.  20 10:43 sdc2
brw-rw----   1 root disk      8,  35 oct.  20 10:43 sdc3
brw-rw----   1 root disk      8,  48 oct.  20 10:42 sdd
brw-rw----   1 root disk      8,  64 oct.  20 10:42 sde
brw-rw----   1 root disk      8,  80 oct.  20 10:42 sdf
brw-rw----   1 root disk      8,  96 oct.  20 10:42 sdg
brw-rw----   1 root disk      8, 112 oct.  20 10:43 sdh
brw-rw----   1 root disk      8, 113 oct.  20 10:43 sdh1

```Is this what you expect?

---

### Post by Rexilion on 2012-10-20
Bad news, the /dev/sd* are somewhat arbitrary by design, they cannot be changed.

Look: [http://lists.us.dell.com/pipermail/linux-poweredge/2009-August/040049.html](http://lists.us.dell.com/pipermail/linux-poweredge/2009-August/040049.html)

And here: [http://askubuntu.com/questions/127695/force-specific-letter-for-usb-drive-in-dev-sd](http://askubuntu.com/questions/127695/force-specific-letter-for-usb-drive-in-dev-sd)

The fact that KDE partition manager still shows the partitions 'as is' is a good thing since you don't want to mess with that (imagine formatting the incorrect disk since the labels overlap!).

I guess that KDE partition manager still fetches the info from an ioctl() or from /proc/partitions (which are not under control by udev).

However, your problem with the "Hard disk status" plasmoid still stands in the fact that it should show all disks. That is a bug. I was under the impression you could work around this with udev. But I was wrong about that. Sorry for that.

---

### Post by Jean-Claude Tergal on 2012-10-20
So, change the sdx is not so easy.
It's not really a problem for me.
I leave them as they are.

The workaround for the plasmoide is to delete the line contain 'uuid' in ~/.kde/share/config/plasmadesktop-appletsrc.

It was very interesting to exchange about udev with you. I've learn a lot.

> **Rexilion said:**
> 
The fact that KDE partition manager still shows the partitions 'as is' is a good thing since you don't want to mess with that (imagine formatting the incorrect disk since the labels overlap!).


Certainly.

I will soon alert the developper of this plasmoid about this problem.

Thank you.

---

