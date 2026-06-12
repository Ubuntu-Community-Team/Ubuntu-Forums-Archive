---
title: "No Wireless Mouse after fstab edit"
date: 2011-04-30
forum: General Help
---

### Post by Derek Karpinski on 2011-04-30
So, I've installed 11.04 3 times already.  The last and sucessufull time, I unplugged all USB devices (external drive, printer, IR reciever, webcam) because when I would boot up, the USB wireless mouse would not respond for a few minutes.

After installing with everything unplugged except for the mouse, everything was working great.

I added a few lines to the /etc/fstab file to mount my external drive for music and backups.  Still everything was working great. Next, I wanted to bind my windows documents folder to my /home dir. Now, I have the same wireless mouse hanging issue. See my syslog file.  You can see the USB errors, and the long time it takes to recognize the 3 button mouse.

I commented out the bind command in fstab, and rebooted, but I still have the error.  Also, I had booted into Windows Vista after editting the fstab.  Don't know if that makes a difference, but those are the details.

Syslog:
```
4:24:50 home-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 30 14:24:50 home-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 30 14:24:50 home-pc kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Apr 30 14:24:50 home-pc kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=cf8d00a6-eaff-476c-8b7b-950aa8745431 ro splash vga=799 quiet quiet splash vt.handoff=7
Apr 30 14:24:50 home-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
Apr 30 14:24:50 home-pc kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 30 14:24:50 home-pc kernel: [    0.000000] DMI 2.4 present.
Apr 30 14:24:50 home-pc kernel: [    0.000000] DMI: HP-Pavilion GC673AA-ABA m8100n/Nettle2, BIOS 5.27  06/10/2008
Apr 30 14:24:50 home-pc kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Apr 30 14:24:50 home-pc kernel: [    0.000000] No AGP bridge found
Apr 30 14:24:50 home-pc kernel: [    0.000000] last_pfn = 0x160000 max_arch_pfn = 0x400000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] MTRR default type: uncachable
Apr 30 14:24:50 home-pc kernel: [    0.000000] MTRR fixed ranges enabled:
Apr 30 14:24:50 home-pc kernel: [    0.000000]   00000-9FFFF write-back
Apr 30 14:24:50 home-pc kernel: [    0.000000]   A0000-BFFFF uncachable
Apr 30 14:24:50 home-pc kernel: [    0.000000]   C0000-C7FFF write-protect
Apr 30 14:24:50 home-pc kernel: [    0.000000]   C8000-FFFFF uncachable
Apr 30 14:24:50 home-pc kernel: [    0.000000] MTRR variable ranges enabled:
Apr 30 14:24:50 home-pc kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Apr 30 14:24:50 home-pc kernel: [    0.000000]   1 base 0080000000 mask FFC0000000 write-back
Apr 30 14:24:50 home-pc kernel: [    0.000000]   2 base 0100000000 mask FFC0000000 write-back
Apr 30 14:24:50 home-pc kernel: [    0.000000]   3 base 0140000000 mask FFE0000000 write-back
Apr 30 14:24:50 home-pc kernel: [    0.000000]   4 disabled
Apr 30 14:24:50 home-pc kernel: [    0.000000]   5 disabled
Apr 30 14:24:50 home-pc kernel: [    0.000000]   6 disabled
Apr 30 14:24:50 home-pc kernel: [    0.000000]   7 disabled
Apr 30 14:24:50 home-pc kernel: [    0.000000] TOM2: 0000000160000000 aka 5632M
Apr 30 14:24:50 home-pc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 30 14:24:50 home-pc kernel: [    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
Apr 30 14:24:50 home-pc kernel: [    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x400000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] found SMP MP-table at [ffff8800000f3e90] f3e90
Apr 30 14:24:50 home-pc kernel: [    0.000000] initial memory mapped : 0 - 20000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bfee0000
Apr 30 14:24:50 home-pc kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Apr 30 14:24:50 home-pc kernel: [    0.000000]  00bfe00000 - 00bfee0000 page 4k
Apr 30 14:24:50 home-pc kernel: [    0.000000] kernel direct mapping tables up to bfee0000 @ 1fffb000-20000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000160000000
Apr 30 14:24:50 home-pc kernel: [    0.000000]  0100000000 - 0160000000 page 2M
Apr 30 14:24:50 home-pc kernel: [    0.000000] kernel direct mapping tables up to 160000000 @ bfed9000-bfee0000
Apr 30 14:24:50 home-pc kernel: [    0.000000] RAMDISK: 35b4c000 - 36d9e000
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: RSDP 00000000000f7f00 00014 (v00 HPQOEM)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: RSDT 00000000bfee3040 0003C (v01 HPQOEM SLIC-CPC 42302E31 NVDA 00000000)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: FACP 00000000bfee30c0 00074 (v01 HPQOEM SLIC-CPC 42302E31 NVDA 00000000)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110112/tbfadt-557)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: DSDT 00000000bfee3180 05B41 (v01 HPQOEM SLIC-CPC 00001000 MSFT 0100000E)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: FACS 00000000bfee0000 00040
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: SSDT 00000000bfee8e00 002CC (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: HPET 00000000bfee9140 00038 (v01 HPQOEM SLIC-CPC 42302E31 NVDA 00000098)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: SLIC 00000000bfee91c0 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: MCFG 00000000bfee9380 0003C (v01 HPQOEM SLIC-CPC 42302E31 NVDA 00000000)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: APIC 00000000bfee8d40 0007C (v01 HPQOEM SLIC-CPC 42302E31 NVDA 00000000)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 14:24:50 home-pc kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr 30 14:24:50 home-pc kernel: [    0.000000] No NUMA configuration found
Apr 30 14:24:50 home-pc kernel: [    0.000000] Faking a node at 0000000000000000-0000000160000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000160000000
Apr 30 14:24:50 home-pc kernel: [    0.000000]   NODE_DATA [000000015fffb000 - 000000015fffffff]
Apr 30 14:24:50 home-pc kernel: [    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff88015b600000-ffff88015f5fffff] on node 0
Apr 30 14:24:50 home-pc kernel: [    0.000000] Zone PFN ranges:
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Apr 30 14:24:50 home-pc kernel: [    0.000000]   Normal   0x00100000 -> 0x00160000
Apr 30 14:24:50 home-pc kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 14:24:50 home-pc kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr 30 14:24:50 home-pc kernel: [    0.000000]     0: 0x00000010 -> 0x0000009b
Apr 30 14:24:50 home-pc kernel: [    0.000000]     0: 0x00000100 -> 0x000bfee0
Apr 30 14:24:50 home-pc kernel: [    0.000000]     0: 0x00100000 -> 0x00160000
Apr 30 14:24:50 home-pc kernel: [    0.000000] On node 0 totalpages: 1179243
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA zone: 6 pages reserved
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA zone: 3917 pages, LIFO batch:0
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Apr 30 14:24:50 home-pc kernel: [    0.000000]   DMA32 zone: 767768 pages, LIFO batch:31
Apr 30 14:24:50 home-pc kernel: [    0.000000]   Normal zone: 5376 pages used for memmap
Apr 30 14:24:50 home-pc kernel: [    0.000000]   Normal zone: 387840 pages, LIFO batch:31
Apr 30 14:24:50 home-pc kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 14:24:50 home-pc kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: IRQ14 used by override.
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: IRQ15 used by override.
Apr 30 14:24:50 home-pc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 14:24:50 home-pc kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Apr 30 14:24:50 home-pc kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr 30 14:24:50 home-pc kernel: [    0.000000] nr_irqs_gsi: 40
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfee3000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee3000 - 00000000bfef0000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bff00000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000f0000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:30100000)
Apr 30 14:24:50 home-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 30 14:24:50 home-pc kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Apr 30 14:24:50 home-pc kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800bfc00000 s84416 r8192 d22080 u1048576
Apr 30 14:24:50 home-pc kernel: [    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
Apr 30 14:24:50 home-pc kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Apr 30 14:24:50 home-pc kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1159525
Apr 30 14:24:50 home-pc kernel: [    0.000000] Policy zone: Normal
Apr 30 14:24:50 home-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=cf8d00a6-eaff-476c-8b7b-950aa8745431 ro splash vga=799 quiet quiet splash vt.handoff=7
Apr 30 14:24:50 home-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.000000] Checking aperture...
Apr 30 14:24:50 home-pc kernel: [    0.000000] No AGP bridge found
Apr 30 14:24:50 home-pc kernel: [    0.000000] Node 0: aperture @ b4000000 size 32 MB
Apr 30 14:24:50 home-pc kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Apr 30 14:24:50 home-pc kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr 30 14:24:50 home-pc kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr 30 14:24:50 home-pc kernel: [    0.000000] This costs you 64 MB of RAM
Apr 30 14:24:50 home-pc kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ b4000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000b4000000 - 00000000b8000000
Apr 30 14:24:50 home-pc kernel: [    0.000000] Memory: 4487384k/5767168k available (5940k kernel code, 1050196k absent, 229588k reserved, 5017k data, 956k init)
Apr 30 14:24:50 home-pc kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr 30 14:24:50 home-pc kernel: [    0.000000] Hierarchical RCU implementation.
Apr 30 14:24:50 home-pc kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Apr 30 14:24:50 home-pc kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Apr 30 14:24:50 home-pc kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Apr 30 14:24:50 home-pc kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr 30 14:24:50 home-pc kernel: [    0.000000] vt handoff: transparent VT on vt#7
Apr 30 14:24:50 home-pc kernel: [    0.000000] Console: colour dummy device 80x25
Apr 30 14:24:50 home-pc kernel: [    0.000000] console [tty0] enabled
Apr 30 14:24:50 home-pc kernel: [    0.000000] allocated 47185920 bytes of page_cgroup
Apr 30 14:24:50 home-pc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 30 14:24:50 home-pc kernel: [    0.000000] hpet clockevent registered
Apr 30 14:24:50 home-pc kernel: [    0.000000] Fast TSC calibration using PIT
Apr 30 14:24:50 home-pc kernel: [    0.000000] Detected 2812.738 MHz processor.
Apr 30 14:24:50 home-pc kernel: [    0.000000] Marking TSC unstable due to TSCs unsynchronized
Apr 30 14:24:50 home-pc kernel: [    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.47 BogoMIPS (lpj=28127380)
Apr 30 14:24:50 home-pc kernel: [    0.010009] pid_max: default: 32768 minimum: 301
Apr 30 14:24:50 home-pc kernel: [    0.010040] Security Framework initialized
Apr 30 14:24:50 home-pc kernel: [    0.010060] AppArmor: AppArmor initialized
Apr 30 14:24:50 home-pc kernel: [    0.010061] Yama: becoming mindful.
Apr 30 14:24:50 home-pc kernel: [    0.010830] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.021360] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.024491] Mount-cache hash table entries: 256
Apr 30 14:24:50 home-pc kernel: [    0.024660] Initializing cgroup subsys ns
Apr 30 14:24:50 home-pc kernel: [    0.024664] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Apr 30 14:24:50 home-pc kernel: [    0.024667] Initializing cgroup subsys cpuacct
Apr 30 14:24:50 home-pc kernel: [    0.024671] Initializing cgroup subsys memory
Apr 30 14:24:50 home-pc kernel: [    0.024684] Initializing cgroup subsys devices
Apr 30 14:24:50 home-pc kernel: [    0.024686] Initializing cgroup subsys freezer
Apr 30 14:24:50 home-pc kernel: [    0.024688] Initializing cgroup subsys net_cls
Apr 30 14:24:50 home-pc kernel: [    0.024690] Initializing cgroup subsys blkio
Apr 30 14:24:50 home-pc kernel: [    0.024728] tseg: 00bff00000
Apr 30 14:24:50 home-pc kernel: [    0.024730] CPU: Physical Processor ID: 0
Apr 30 14:24:50 home-pc kernel: [    0.024731] CPU: Processor Core ID: 0
Apr 30 14:24:50 home-pc kernel: [    0.024733] mce: CPU supports 5 MCE banks
Apr 30 14:24:50 home-pc kernel: [    0.024746] using C1E aware idle routine
Apr 30 14:24:50 home-pc kernel: [    0.026227] ACPI: Core revision 20110112
Apr 30 14:24:50 home-pc kernel: [    0.030020] ftrace: allocating 24314 entries in 96 pages
Apr 30 14:24:50 home-pc kernel: [    0.037210] Setting APIC routing to flat
Apr 30 14:24:50 home-pc kernel: [    0.037671] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 14:24:50 home-pc kernel: [    0.137948] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 03
Apr 30 14:24:50 home-pc kernel: [    0.140000] Performance Events: AMD PMU driver.
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... version:                0
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... bit width:              48
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... generic registers:      4
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... value mask:             0000ffffffffffff
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... max period:             00007fffffffffff
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... fixed-purpose events:   0
Apr 30 14:24:50 home-pc kernel: [    0.140000] ... event mask:             000000000000000f
Apr 30 14:24:50 home-pc kernel: [    0.140000] Booting Node   0, Processors  #1 Ok.
Apr 30 14:24:50 home-pc kernel: [    0.290062] Brought up 2 CPUs
Apr 30 14:24:50 home-pc kernel: [    0.290063] Total of 2 processors activated (11251.13 BogoMIPS).
Apr 30 14:24:50 home-pc kernel: [    0.290323] devtmpfs: initialized
Apr 30 14:24:50 home-pc kernel: [    0.290892] print_constraints: dummy: 
Apr 30 14:24:50 home-pc kernel: [    0.290927] Time: 14:24:36  Date: 04/30/11
Apr 30 14:24:50 home-pc kernel: [    0.290975] NET: Registered protocol family 16
Apr 30 14:24:50 home-pc kernel: [    0.291017] Trying to unpack rootfs image as initramfs...
Apr 30 14:24:50 home-pc kernel: [    0.291108] node 0 link 0: io port [8000, ffff]
Apr 30 14:24:50 home-pc kernel: [    0.291112] TOM: 00000000c0000000 aka 3072M
Apr 30 14:24:50 home-pc kernel: [    0.291114] node 0 link 0: mmio [a0000, bffff]
Apr 30 14:24:50 home-pc kernel: [    0.291117] node 0 link 0: mmio [c0000000, efffffff]
Apr 30 14:24:50 home-pc kernel: [    0.291119] node 0 link 0: mmio [f4000000, fe02ffff]
Apr 30 14:24:50 home-pc kernel: [    0.291121] node 0 link 0: mmio [f0000000, f03fffff]
Apr 30 14:24:50 home-pc kernel: [    0.291123] TOM2: 0000000160000000 aka 5632M
Apr 30 14:24:50 home-pc kernel: [    0.291125] bus: [00, 04] on node 0 link 0
Apr 30 14:24:50 home-pc kernel: [    0.291128] bus: 00 index 0 [io  0x0000-0xffff]
Apr 30 14:24:50 home-pc kernel: [    0.291129] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Apr 30 14:24:50 home-pc kernel: [    0.291131] bus: 00 index 2 [mem 0xc0000000-0xf3ffffff]
Apr 30 14:24:50 home-pc kernel: [    0.291133] bus: 00 index 3 [mem 0xf4000000-0xffffffff]
Apr 30 14:24:50 home-pc kernel: [    0.291134] bus: 00 index 4 [mem 0x160000000-0xfcffffffff]
Apr 30 14:24:50 home-pc kernel: [    0.291147] ACPI: bus type pci registered
Apr 30 14:24:50 home-pc kernel: [    0.291226] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Apr 30 14:24:50 home-pc kernel: [    0.291229] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Apr 30 14:24:50 home-pc kernel: [    0.296141] PCI: Using configuration type 1 for base access
Apr 30 14:24:50 home-pc kernel: [    0.296924] bio: create slab <bio-0> at 0
Apr 30 14:24:50 home-pc kernel: [    0.298004] ACPI: EC: Look up EC in DSDT
Apr 30 14:24:50 home-pc kernel: [    0.301552] ACPI: Interpreter enabled
Apr 30 14:24:50 home-pc kernel: [    0.301555] ACPI: (supports S0 S1 S3 S4 S5)
Apr 30 14:24:50 home-pc kernel: [    0.301575] ACPI: Using IOAPIC for interrupt routing
Apr 30 14:24:50 home-pc kernel: [    0.306791] ACPI: No dock devices found.
Apr 30 14:24:50 home-pc kernel: [    0.306793] HEST: Table not found.
Apr 30 14:24:50 home-pc kernel: [    0.306795] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr 30 14:24:50 home-pc kernel: [    0.307303] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
Apr 30 14:24:50 home-pc kernel: [    0.308342] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
Apr 30 14:24:50 home-pc kernel: [    0.308344] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
Apr 30 14:24:50 home-pc kernel: [    0.308346] pci_root PNP0A08:00: host bridge window [io  0x8000-0xffff]
Apr 30 14:24:50 home-pc kernel: [    0.308348] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df]
Apr 30 14:24:50 home-pc kernel: [    0.308351] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Apr 30 14:24:50 home-pc kernel: [    0.308353] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xefffffff]
Apr 30 14:24:50 home-pc kernel: [    0.308355] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff]
Apr 30 14:24:50 home-pc kernel: [    0.308357] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
Apr 30 14:24:50 home-pc kernel: [    0.308359] pci_root PNP0A08:00: host bridge window [io  0x4700-0x470b]
Apr 30 14:24:50 home-pc kernel: [    0.308361] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80]
Apr 30 14:24:50 home-pc kernel: [    0.308363] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff]
Apr 30 14:24:50 home-pc kernel: [    0.308390] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
Apr 30 14:24:50 home-pc kernel: [    0.308539] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
Apr 30 14:24:50 home-pc kernel: [    0.308575] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
Apr 30 14:24:50 home-pc kernel: [    0.308586] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
Apr 30 14:24:50 home-pc kernel: [    0.308599] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
Apr 30 14:24:50 home-pc kernel: [    0.308604] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
Apr 30 14:24:50 home-pc kernel: [    0.308623] pci 0000:00:01.1: PME# supported from D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.308628] pci 0000:00:01.1: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.308640] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
Apr 30 14:24:50 home-pc kernel: [    0.308678] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
Apr 30 14:24:50 home-pc kernel: [    0.308685] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
Apr 30 14:24:50 home-pc kernel: [    0.308712] pci 0000:00:02.0: supports D1 D2
Apr 30 14:24:50 home-pc kernel: [    0.308714] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.308716] pci 0000:00:02.0: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.308729] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
Apr 30 14:24:50 home-pc kernel: [    0.308738] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
Apr 30 14:24:50 home-pc kernel: [    0.308769] pci 0000:00:02.1: supports D1 D2
Apr 30 14:24:50 home-pc kernel: [    0.308771] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.308774] pci 0000:00:02.1: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.308791] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
Apr 30 14:24:50 home-pc kernel: [    0.308827] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
Apr 30 14:24:50 home-pc kernel: [    0.308837] pci 0000:00:05.0: reg 10: [mem 0xfe024000-0xfe027fff]
Apr 30 14:24:50 home-pc kernel: [    0.308867] pci 0000:00:05.0: PME# supported from D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.308870] pci 0000:00:05.0: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.308887] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
Apr 30 14:24:50 home-pc kernel: [    0.308907] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
Apr 30 14:24:50 home-pc kernel: [    0.308932] pci 0000:00:07.0: [10de:03ef] type 0 class 0x000680
Apr 30 14:24:50 home-pc kernel: [    0.308941] pci 0000:00:07.0: reg 10: [mem 0xfe02d000-0xfe02dfff]
Apr 30 14:24:50 home-pc kernel: [    0.308945] pci 0000:00:07.0: reg 14: [io  0xec00-0xec07]
Apr 30 14:24:50 home-pc kernel: [    0.308969] pci 0000:00:07.0: supports D1 D2
Apr 30 14:24:50 home-pc kernel: [    0.308970] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.308974] pci 0000:00:07.0: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.308987] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
Apr 30 14:24:50 home-pc kernel: [    0.308995] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
Apr 30 14:24:50 home-pc kernel: [    0.308999] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
Apr 30 14:24:50 home-pc kernel: [    0.309003] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
Apr 30 14:24:50 home-pc kernel: [    0.309007] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
Apr 30 14:24:50 home-pc kernel: [    0.309011] pci 0000:00:08.0: reg 20: [io  0xd800-0xd80f]
Apr 30 14:24:50 home-pc kernel: [    0.309015] pci 0000:00:08.0: reg 24: [mem 0xfe02c000-0xfe02cfff]
Apr 30 14:24:50 home-pc kernel: [    0.309040] pci 0000:00:08.1: [10de:03f6] type 0 class 0x000101
Apr 30 14:24:50 home-pc kernel: [    0.309048] pci 0000:00:08.1: reg 10: [io  0x09e0-0x09e7]
Apr 30 14:24:50 home-pc kernel: [    0.309052] pci 0000:00:08.1: reg 14: [io  0x0be0-0x0be3]
Apr 30 14:24:50 home-pc kernel: [    0.309056] pci 0000:00:08.1: reg 18: [io  0x0960-0x0967]
Apr 30 14:24:50 home-pc kernel: [    0.309060] pci 0000:00:08.1: reg 1c: [io  0x0b60-0x0b63]
Apr 30 14:24:50 home-pc kernel: [    0.309064] pci 0000:00:08.1: reg 20: [io  0xc400-0xc40f]
Apr 30 14:24:50 home-pc kernel: [    0.309068] pci 0000:00:08.1: reg 24: [mem 0xfe02b000-0xfe02bfff]
Apr 30 14:24:50 home-pc kernel: [    0.309094] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
Apr 30 14:24:50 home-pc kernel: [    0.309112] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.309115] pci 0000:00:09.0: PME# disabled
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> NetworkManager (version 0.8.3.998) is starting...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> trying to start the modem manager...
Apr 30 14:24:50 home-pc kernel: [    0.309128] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
Apr 30 14:24:50 home-pc kernel: [    0.309145] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.309147] pci 0000:00:0b.0: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.309160] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
Apr 30 14:24:50 home-pc kernel: [    0.309177] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.309179] pci 0000:00:0c.0: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.309201] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Apr 30 14:24:50 home-pc kernel: [    0.309218] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Apr 30 14:24:50 home-pc kernel: [    0.309238] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Apr 30 14:24:50 home-pc kernel: [    0.309256] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Apr 30 14:24:50 home-pc kernel: [    0.309308] pci 0000:01:05.0: [14f1:5b7a] type 0 class 0x000400
Apr 30 14:24:50 home-pc kernel: [    0.309321] pci 0000:01:05.0: reg 10: [mem 0xe8000000-0xebffffff]
Apr 30 14:24:50 home-pc kernel: [    0.309380] pci 0000:01:09.0: [1106:3044] type 0 class 0x000c00
Apr 30 14:24:50 home-pc kernel: [    0.309392] pci 0000:01:09.0: reg 10: [mem 0xeffff000-0xeffff7ff]
Apr 30 14:24:50 home-pc kernel: [    0.309400] pci 0000:01:09.0: reg 14: [io  0xbc00-0xbc7f]
Apr 30 14:24:50 home-pc kernel: [    0.309440] pci 0000:01:09.0: supports D2
Apr 30 14:24:50 home-pc kernel: [    0.309441] pci 0000:01:09.0: PME# supported from D2 D3hot D3cold
Apr 30 14:24:50 home-pc kernel: [    0.309445] pci 0000:01:09.0: PME# disabled
Apr 30 14:24:50 home-pc kernel: [    0.309468] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309472] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
Apr 30 14:24:50 home-pc kernel: [    0.309475] pci 0000:00:04.0:   bridge window [mem 0xe8000000-0xefffffff]
Apr 30 14:24:50 home-pc kernel: [    0.309478] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Apr 30 14:24:50 home-pc kernel: [    0.309481] pci 0000:00:04.0:   bridge window [io  0x0000-0x03af] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309484] pci 0000:00:04.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309486] pci 0000:00:04.0:   bridge window [io  0x8000-0xffff] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309488] pci 0000:00:04.0:   bridge window [io  0x03b0-0x03df] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309490] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309493] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xefffffff] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309495] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xfe02ffff] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309497] pci 0000:00:04.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309500] pci 0000:00:04.0:   bridge window [io  0x4700-0x470b] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309502] pci 0000:00:04.0:   bridge window [io  0x1c00-0x1c80] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309504] pci 0000:00:04.0:   bridge window [mem 0xfec80000-0xfecbffff] (subtractive decode)
Apr 30 14:24:50 home-pc kernel: [    0.309532] pci 0000:02:00.0: [10de:0a65] type 0 class 0x000300
Apr 30 14:24:50 home-pc kernel: [    0.309539] pci 0000:02:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
Apr 30 14:24:50 home-pc kernel: [    0.309547] pci 0000:02:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.309555] pci 0000:02:00.0: reg 1c: [mem 0xde000000-0xdfffffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.309561] pci 0000:02:00.0: reg 24: [io  0xac00-0xac7f]
Apr 30 14:24:50 home-pc kernel: [    0.309567] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
Apr 30 14:24:50 home-pc kernel: [    0.309600] pci 0000:02:00.1: [10de:0be3] type 0 class 0x000403
Apr 30 14:24:50 home-pc kernel: [    0.309608] pci 0000:02:00.1: reg 10: [mem 0xfcffc000-0xfcffffff]
Apr 30 14:24:50 home-pc kernel: [    0.320014] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Apr 30 14:24:50 home-pc kernel: [    0.320017] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
Apr 30 14:24:50 home-pc kernel: [    0.320020] pci 0000:00:09.0:   bridge window [mem 0xfb000000-0xfcffffff]
Apr 30 14:24:50 home-pc kernel: [    0.320023] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.320041] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Apr 30 14:24:50 home-pc kernel: [    0.320044] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
Apr 30 14:24:50 home-pc kernel: [    0.320046] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Apr 30 14:24:50 home-pc kernel: [    0.320049] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.320067] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Apr 30 14:24:50 home-pc kernel: [    0.320070] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
Apr 30 14:24:50 home-pc kernel: [    0.320073] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Apr 30 14:24:50 home-pc kernel: [    0.320076] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.320085] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 14:24:50 home-pc kernel: [    0.320219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Apr 30 14:24:50 home-pc kernel: [    0.320344]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Apr 30 14:24:50 home-pc kernel: [    0.341848] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.341892] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.341934] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.341976] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342022] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342063] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342105] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342148] ACPI: PCI Interrupt Link [LNK8] (IRQs *5 7 9 10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342189] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342231] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342274] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342317] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342359] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342400] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342443] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342486] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342527] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342570] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342613] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Apr 30 14:24:50 home-pc kernel: [    0.342689] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Apr 30 14:24:50 home-pc kernel: [    0.342761] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342832] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.342910] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Apr 30 14:24:50 home-pc kernel: [    0.342981] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Apr 30 14:24:50 home-pc kernel: [    0.343052] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.343124] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.343196] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Apr 30 14:24:50 home-pc kernel: [    0.343268] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.343340] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Apr 30 14:24:50 home-pc kernel: [    0.343412] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Apr 30 14:24:50 home-pc kernel: [    0.343485] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.343555] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Apr 30 14:24:50 home-pc kernel: [    0.343625] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Apr 30 14:24:50 home-pc kernel: [    0.343698] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Apr 30 14:24:50 home-pc kernel: [    0.343771] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.343844] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Apr 30 14:24:50 home-pc kernel: [    0.343916] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Apr 30 14:24:50 home-pc kernel: [    0.343986] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Apr 30 14:24:50 home-pc kernel: [    0.344116] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr 30 14:24:50 home-pc kernel: [    0.344119] vgaarb: loaded
Apr 30 14:24:50 home-pc kernel: [    0.344323] SCSI subsystem initialized
Apr 30 14:24:50 home-pc kernel: [    0.344402] libata version 3.00 loaded.
Apr 30 14:24:50 home-pc kernel: [    0.344462] usbcore: registered new interface driver usbfs
Apr 30 14:24:50 home-pc kernel: [    0.344473] usbcore: registered new interface driver hub
Apr 30 14:24:50 home-pc kernel: [    0.344505] usbcore: registered new device driver usb
Apr 30 14:24:50 home-pc kernel: [    0.344624] wmi: Mapper loaded
Apr 30 14:24:50 home-pc kernel: [    0.344626] PCI: Using ACPI for IRQ routing
Apr 30 14:24:50 home-pc kernel: [    0.344629] PCI: pci_cache_line_size set to 64 bytes
Apr 30 14:24:50 home-pc kernel: [    0.344690] reserve RAM buffer: 000000000009b800 - 000000000009ffff 
Apr 30 14:24:50 home-pc kernel: [    0.344692] reserve RAM buffer: 00000000bfee0000 - 00000000bfffffff 
Apr 30 14:24:50 home-pc kernel: [    0.344801] NetLabel: Initializing
Apr 30 14:24:50 home-pc kernel: [    0.344802] NetLabel:  domain hash size = 128
Apr 30 14:24:50 home-pc kernel: [    0.344803] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 30 14:24:50 home-pc kernel: [    0.344817] NetLabel:  unlabeled traffic allowed by default
Apr 30 14:24:50 home-pc kernel: [    0.344854] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 30 14:24:50 home-pc kernel: [    0.344860] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Apr 30 14:24:50 home-pc kernel: [    0.344863] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Apr 30 14:24:50 home-pc kernel: [    0.350209] Switching to clocksource hpet
Apr 30 14:24:50 home-pc kernel: [    0.359525] Switched to NOHz mode on CPU #0
Apr 30 14:24:50 home-pc kernel: [    0.359555] Switched to NOHz mode on CPU #1
Apr 30 14:24:50 home-pc kernel: [    0.359678] AppArmor: AppArmor Filesystem Enabled
Apr 30 14:24:50 home-pc kernel: [    0.359723] pnp: PnP ACPI init
Apr 30 14:24:50 home-pc kernel: [    0.359752] ACPI: bus type pnp registered
Apr 30 14:24:50 home-pc kernel: [    0.360389] pnp 00:00: [bus 00-04]
Apr 30 14:24:50 home-pc kernel: [    0.360392] pnp 00:00: [io  0x0cf8-0x0cff]
Apr 30 14:24:50 home-pc kernel: [    0.360394] pnp 00:00: [io  0x0000-0x03af window]
Apr 30 14:24:50 home-pc kernel: [    0.360396] pnp 00:00: [io  0x03e0-0x0cf7 window]
Apr 30 14:24:50 home-pc kernel: [    0.360397] pnp 00:00: [io  0x8000-0xffff window]
Apr 30 14:24:50 home-pc kernel: [    0.360399] pnp 00:00: [io  0x03b0-0x03df window]
Apr 30 14:24:50 home-pc kernel: [    0.360402] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Apr 30 14:24:50 home-pc kernel: [    0.360404] pnp 00:00: [mem 0xc0000000-0xefffffff window]
Apr 30 14:24:50 home-pc kernel: [    0.360406] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
Apr 30 14:24:50 home-pc kernel: [    0.360408] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Apr 30 14:24:50 home-pc kernel: [    0.360410] pnp 00:00: [io  0x4700-0x470b window]
Apr 30 14:24:50 home-pc kernel: [    0.360412] pnp 00:00: [io  0x1c00-0x1c80 window]
Apr 30 14:24:50 home-pc kernel: [    0.360414] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
Apr 30 14:24:50 home-pc kernel: [    0.360509] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Apr 30 14:24:50 home-pc kernel: [    0.360609] pnp 00:01: [io  0x1000-0x107f]
Apr 30 14:24:50 home-pc kernel: [    0.360611] pnp 00:01: [io  0x1080-0x10ff]
Apr 30 14:24:50 home-pc kernel: [    0.360613] pnp 00:01: [io  0x1400-0x147f]
Apr 30 14:24:50 home-pc kernel: [    0.360615] pnp 00:01: [io  0x1480-0x14ff]
Apr 30 14:24:50 home-pc kernel: [    0.360617] pnp 00:01: [io  0x1800-0x187f]
Apr 30 14:24:50 home-pc kernel: [    0.360624] pnp 00:01: [io  0x1880-0x18ff]
Apr 30 14:24:50 home-pc kernel: [    0.360626] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Apr 30 14:24:50 home-pc kernel: [    0.360628] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
Apr 30 14:24:50 home-pc kernel: [    0.360630] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
Apr 30 14:24:50 home-pc kernel: [    0.360632] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Apr 30 14:24:50 home-pc kernel: [    0.360634] pnp 00:01: [io  0x2000-0x207f]
Apr 30 14:24:50 home-pc kernel: [    0.360636] pnp 00:01: [io  0x2080-0x20ff]
Apr 30 14:24:50 home-pc kernel: [    0.360712] system 00:01: [io  0x1000-0x107f] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360715] system 00:01: [io  0x1080-0x10ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360717] system 00:01: [io  0x1400-0x147f] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360719] system 00:01: [io  0x1480-0x14ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360722] system 00:01: [io  0x1800-0x187f] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360724] system 00:01: [io  0x1880-0x18ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360727] system 00:01: [io  0x2000-0x207f] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360729] system 00:01: [io  0x2080-0x20ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360732] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360735] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360738] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 30 14:24:50 home-pc kernel: [    0.360803] pnp 00:02: [io  0x0010-0x001f]
Apr 30 14:24:50 home-pc kernel: [    0.360804] pnp 00:02: [io  0x0022-0x003f]
Apr 30 14:24:50 home-pc kernel: [    0.360806] pnp 00:02: [io  0x0044-0x004d]
Apr 30 14:24:50 home-pc kernel: [    0.360808] pnp 00:02: [io  0x0050-0x005e]
Apr 30 14:24:50 home-pc kernel: [    0.360810] pnp 00:02: [io  0x0062-0x0063]
Apr 30 14:24:50 home-pc kernel: [    0.360811] pnp 00:02: [io  0x0065-0x006f]
Apr 30 14:24:50 home-pc kernel: [    0.360813] pnp 00:02: [io  0x0074-0x007f]
Apr 30 14:24:50 home-pc kernel: [    0.360815] pnp 00:02: [io  0x0091-0x0093]
Apr 30 14:24:50 home-pc kernel: [    0.360817] pnp 00:02: [io  0x00a2-0x00bf]
Apr 30 14:24:50 home-pc kernel: [    0.360818] pnp 00:02: [io  0x00e0-0x00ef]
Apr 30 14:24:50 home-pc kernel: [    0.360820] pnp 00:02: [io  0x04d0-0x04d1]
Apr 30 14:24:50 home-pc kernel: [    0.360822] pnp 00:02: [io  0x0800-0x087f]
Apr 30 14:24:50 home-pc kernel: [    0.360824] pnp 00:02: [io  0x0290-0x0297]
Apr 30 14:24:50 home-pc kernel: [    0.360879] system 00:02: [io  0x04d0-0x04d1] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360881] system 00:02: [io  0x0800-0x087f] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360884] system 00:02: [io  0x0290-0x0297] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.360886] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 30 14:24:50 home-pc kernel: [    0.360898] pnp 00:03: [dma 4]
Apr 30 14:24:50 home-pc kernel: [    0.360900] pnp 00:03: [io  0x0000-0x000f]
Apr 30 14:24:50 home-pc kernel: [    0.360901] pnp 00:03: [io  0x0080-0x0090]
Apr 30 14:24:50 home-pc kernel: [    0.360903] pnp 00:03: [io  0x0094-0x009f]
Apr 30 14:24:50 home-pc kernel: [    0.360905] pnp 00:03: [io  0x00c0-0x00df]
Apr 30 14:24:50 home-pc kernel: [    0.360938] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Apr 30 14:24:50 home-pc kernel: [    0.360987] pnp 00:04: [irq 0 disabled]
Apr 30 14:24:50 home-pc kernel: [    0.361004] pnp 00:04: [irq 8]
Apr 30 14:24:50 home-pc kernel: [    0.361005] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
Apr 30 14:24:50 home-pc kernel: [    0.361034] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Apr 30 14:24:50 home-pc kernel: [    0.361058] pnp 00:05: [io  0x0070-0x0073]
Apr 30 14:24:50 home-pc kernel: [    0.361092] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr 30 14:24:50 home-pc kernel: [    0.361100] pnp 00:06: [io  0x0061]
Apr 30 14:24:50 home-pc kernel: [    0.361130] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Apr 30 14:24:50 home-pc kernel: [    0.361138] pnp 00:07: [io  0x00f0-0x00ff]
Apr 30 14:24:50 home-pc kernel: [    0.361146] pnp 00:07: [irq 13]
Apr 30 14:24:50 home-pc kernel: [    0.361183] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr 30 14:24:50 home-pc kernel: [    0.361390] pnp 00:08: [io  0x0060]
Apr 30 14:24:50 home-pc kernel: [    0.361392] pnp 00:08: [io  0x0064]
Apr 30 14:24:50 home-pc kernel: [    0.361400] pnp 00:08: [irq 1]
Apr 30 14:24:50 home-pc kernel: [    0.361429] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Apr 30 14:24:50 home-pc kernel: [    0.361982] pnp 00:09: [mem 0xf0000000-0xf3ffffff]
Apr 30 14:24:50 home-pc kernel: [    0.362045] system 00:09: [mem 0xf0000000-0xf3ffffff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362048] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 30 14:24:50 home-pc kernel: [    0.362116] pnp 00:0a: [mem 0x000f0000-0x000fffff]
Apr 30 14:24:50 home-pc kernel: [    0.362118] pnp 00:0a: [mem 0xfeff0000-0xfeff00ff]
Apr 30 14:24:50 home-pc kernel: [    0.362120] pnp 00:0a: [mem 0xbfee0000-0xbfefffff]
Apr 30 14:24:50 home-pc kernel: [    0.362122] pnp 00:0a: [mem 0xffff0000-0xffffffff]
Apr 30 14:24:50 home-pc kernel: [    0.362124] pnp 00:0a: [mem 0x00000000-0x0009ffff]
Apr 30 14:24:50 home-pc kernel: [    0.362126] pnp 00:0a: [mem 0x00100000-0xbfedffff]
Apr 30 14:24:50 home-pc kernel: [    0.362132] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Apr 30 14:24:50 home-pc kernel: [    0.362134] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
Apr 30 14:24:50 home-pc kernel: [    0.362136] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
Apr 30 14:24:50 home-pc kernel: [    0.362138] pnp 00:0a: [mem 0xfefff000-0xfeffffff]
Apr 30 14:24:50 home-pc kernel: [    0.362140] pnp 00:0a: [mem 0xfff80000-0xfff80fff]
Apr 30 14:24:50 home-pc kernel: [    0.362141] pnp 00:0a: [mem 0xfff90000-0xfffbffff]
Apr 30 14:24:50 home-pc kernel: [    0.362143] pnp 00:0a: [mem 0xfffed000-0xfffeffff]
Apr 30 14:24:50 home-pc kernel: [    0.362213] system 00:0a: [mem 0x000f0000-0x000fffff] could not be reserved
Apr 30 14:24:50 home-pc kernel: [    0.362216] system 00:0a: [mem 0xfeff0000-0xfeff00ff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362219] system 00:0a: [mem 0xbfee0000-0xbfefffff] could not be reserved
Apr 30 14:24:50 home-pc kernel: [    0.362221] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362224] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
Apr 30 14:24:50 home-pc kernel: [    0.362228] system 00:0a: [mem 0x00100000-0xbfedffff] could not be reserved
Apr 30 14:24:50 home-pc kernel: [    0.362230] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr 30 14:24:50 home-pc kernel: [    0.362233] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362236] system 00:0a: [mem 0xfefff000-0xfeffffff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362238] system 00:0a: [mem 0xfff80000-0xfff80fff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362241] system 00:0a: [mem 0xfff90000-0xfffbffff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362243] system 00:0a: [mem 0xfffed000-0xfffeffff] has been reserved
Apr 30 14:24:50 home-pc kernel: [    0.362246] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr 30 14:24:50 home-pc kernel: [    0.362266] pnp: PnP ACPI: found 11 devices
Apr 30 14:24:50 home-pc kernel: [    0.362267] ACPI: ACPI bus type pnp unregistered
Apr 30 14:24:50 home-pc kernel: [    0.368672] pci 0000:00:04.0: PCI bridge to [bus 01-01]
Apr 30 14:24:50 home-pc kernel: [    0.368675] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
Apr 30 14:24:50 home-pc kernel: [    0.368678] pci 0000:00:04.0:   bridge window [mem 0xe8000000-0xefffffff]
Apr 30 14:24:50 home-pc kernel: [    0.368681] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Apr 30 14:24:50 home-pc kernel: [    0.368689] pci 0000:02:00.0: BAR 6: assigned [mem 0xd0000000-0xd007ffff pref]
Apr 30 14:24:50 home-pc kernel: [    0.368692] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Apr 30 14:24:50 home-pc kernel: [    0.368694] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
Apr 30 14:24:50 home-pc kernel: [    0.368697] pci 0000:00:09.0:   bridge window [mem 0xfb000000-0xfcffffff]
Apr 30 14:24:50 home-pc kernel: [    0.368699] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.368703] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Apr 30 14:24:50 home-pc kernel: [    0.368705] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
Apr 30 14:24:50 home-pc kernel: [    0.368707] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Apr 30 14:24:50 home-pc kernel: [    0.368710] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.368713] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Apr 30 14:24:50 home-pc kernel: [    0.368716] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
Apr 30 14:24:50 home-pc kernel: [    0.368719] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Apr 30 14:24:50 home-pc kernel: [    0.368721] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.368733] pci 0000:00:04.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.368737] pci 0000:00:09.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.368741] pci 0000:00:0b.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.368745] pci 0000:00:0c.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.368748] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
Apr 30 14:24:50 home-pc kernel: [    0.368750] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
Apr 30 14:24:50 home-pc kernel: [    0.368752] pci_bus 0000:00: resource 6 [io  0x8000-0xffff]
Apr 30 14:24:50 home-pc kernel: [    0.368754] pci_bus 0000:00: resource 7 [io  0x03b0-0x03df]
Apr 30 14:24:50 home-pc kernel: [    0.368756] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
Apr 30 14:24:50 home-pc kernel: [    0.368758] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xefffffff]
Apr 30 14:24:50 home-pc kernel: [    0.368760] pci_bus 0000:00: resource 10 [mem 0xf4000000-0xfe02ffff]
Apr 30 14:24:50 home-pc kernel: [    0.368762] pci_bus 0000:00: resource 11 [mem 0xfed40000-0xfed44fff]
Apr 30 14:24:50 home-pc kernel: [    0.368764] pci_bus 0000:00: resource 12 [io  0x4700-0x470b]
Apr 30 14:24:50 home-pc kernel: [    0.368766] pci_bus 0000:00: resource 13 [io  0x1c00-0x1c80]
Apr 30 14:24:50 home-pc kernel: [    0.368768] pci_bus 0000:00: resource 14 [mem 0xfec80000-0xfecbffff]
Apr 30 14:24:50 home-pc kernel: [    0.368770] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Apr 30 14:24:50 home-pc kernel: [    0.368772] pci_bus 0000:01: resource 1 [mem 0xe8000000-0xefffffff]
Apr 30 14:24:50 home-pc kernel: [    0.368774] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
Apr 30 14:24:50 home-pc kernel: [    0.368777] pci_bus 0000:01: resource 4 [io  0x0000-0x03af]
Apr 30 14:24:50 home-pc kernel: [    0.368779] pci_bus 0000:01: resource 5 [io  0x03e0-0x0cf7]
Apr 30 14:24:50 home-pc kernel: [    0.368781] pci_bus 0000:01: resource 6 [io  0x8000-0xffff]
Apr 30 14:24:50 home-pc kernel: [    0.368783] pci_bus 0000:01: resource 7 [io  0x03b0-0x03df]
Apr 30 14:24:50 home-pc kernel: [    0.368785] pci_bus 0000:01: resource 8 [mem 0x000a0000-0x000bffff]
Apr 30 14:24:50 home-pc kernel: [    0.368787] pci_bus 0000:01: resource 9 [mem 0xc0000000-0xefffffff]
Apr 30 14:24:50 home-pc kernel: [    0.368789] pci_bus 0000:01: resource 10 [mem 0xf4000000-0xfe02ffff]
Apr 30 14:24:50 home-pc kernel: [    0.368791] pci_bus 0000:01: resource 11 [mem 0xfed40000-0xfed44fff]
Apr 30 14:24:50 home-pc kernel: [    0.368793] pci_bus 0000:01: resource 12 [io  0x4700-0x470b]
Apr 30 14:24:50 home-pc kernel: [    0.368795] pci_bus 0000:01: resource 13 [io  0x1c00-0x1c80]
Apr 30 14:24:50 home-pc kernel: [    0.368797] pci_bus 0000:01: resource 14 [mem 0xfec80000-0xfecbffff]
Apr 30 14:24:50 home-pc kernel: [    0.368800] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
Apr 30 14:24:50 home-pc kernel: [    0.368802] pci_bus 0000:02: resource 1 [mem 0xfb000000-0xfcffffff]
Apr 30 14:24:50 home-pc kernel: [    0.368804] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xdfffffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.368806] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
Apr 30 14:24:50 home-pc kernel: [    0.368808] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
Apr 30 14:24:50 home-pc kernel: [    0.368811] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.368813] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
Apr 30 14:24:50 home-pc kernel: [    0.368815] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
Apr 30 14:24:50 home-pc kernel: [    0.368817] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
Apr 30 14:24:50 home-pc kernel: [    0.368857] NET: Registered protocol family 2
Apr 30 14:24:50 home-pc kernel: [    0.369116] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.372094] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.379309] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.380231] TCP: Hash tables configured (established 524288 bind 65536)
Apr 30 14:24:50 home-pc kernel: [    0.380233] TCP reno registered
Apr 30 14:24:50 home-pc kernel: [    0.380256] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.380407] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.380628] NET: Registered protocol family 1
Apr 30 14:24:50 home-pc kernel: [    0.400086] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400131] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400185] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400237] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400290] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400346] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400404] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400466] pci 0000:00:00.0: Found enabled HT MSI Mapping
Apr 30 14:24:50 home-pc kernel: [    0.400492] pci 0000:02:00.0: Boot video device
Apr 30 14:24:50 home-pc kernel: [    0.400501] PCI: CLS 64 bytes, default 64
Apr 30 14:24:50 home-pc kernel: [    0.401414] PCI-DMA: Disabling AGP.
Apr 30 14:24:50 home-pc kernel: [    0.401573] PCI-DMA: aperture base @ b4000000 size 65536 KB
Apr 30 14:24:50 home-pc kernel: [    0.401574] PCI-DMA: using GART IOMMU.
Apr 30 14:24:50 home-pc kernel: [    0.401579] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr 30 14:24:50 home-pc kernel: [    0.405563] audit: initializing netlink socket (disabled)
Apr 30 14:24:50 home-pc kernel: [    0.405578] type=2000 audit(1304173476.400:1): initialized
Apr 30 14:24:50 home-pc kernel: [    0.417543] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr 30 14:24:50 home-pc kernel: [    0.419221] VFS: Disk quotas dquot_6.5.2
Apr 30 14:24:50 home-pc kernel: [    0.419275] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr 30 14:24:50 home-pc kernel: [    0.419872] fuse init (API version 7.16)
Apr 30 14:24:50 home-pc kernel: [    0.419955] msgmni has been set to 8893
Apr 30 14:24:50 home-pc kernel: [    0.420187] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr 30 14:24:50 home-pc kernel: [    0.420210] io scheduler noop registered
Apr 30 14:24:50 home-pc kernel: [    0.420212] io scheduler deadline registered
Apr 30 14:24:50 home-pc kernel: [    0.420248] io scheduler cfq registered (default)
Apr 30 14:24:50 home-pc kernel: [    0.420392] pcieport 0000:00:09.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.420423] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
Apr 30 14:24:50 home-pc kernel: [    0.420493] pcieport 0000:00:0b.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.420510] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
Apr 30 14:24:50 home-pc kernel: [    0.420568] pcieport 0000:00:0c.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    0.420584] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
Apr 30 14:24:50 home-pc kernel: [    0.420642] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 14:24:50 home-pc kernel: [    0.420664] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 30 14:24:50 home-pc kernel: [    0.420833] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr 30 14:24:50 home-pc kernel: [    0.420838] ACPI: Power Button [PWRB]
Apr 30 14:24:50 home-pc kernel: [    0.420897] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr 30 14:24:50 home-pc kernel: [    0.420900] ACPI: Power Button [PWRF]
Apr 30 14:24:50 home-pc kernel: [    0.420955] ACPI: Fan [FAN] (on)
Apr 30 14:24:50 home-pc kernel: [    0.421170] ACPI: acpi_idle registered with cpuidle
Apr 30 14:24:50 home-pc kernel: [    0.423337] thermal LNXTHERM:00: registered as thermal_zone0
Apr 30 14:24:50 home-pc kernel: [    0.423339] ACPI: Thermal Zone [THRM] (40 C)
Apr 30 14:24:50 home-pc kernel: [    0.423388] ERST: Table is not found!
Apr 30 14:24:50 home-pc kernel: [    0.423461] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr 30 14:24:50 home-pc kernel: [    0.643368] Freeing initrd memory: 18760k freed
Apr 30 14:24:50 home-pc kernel: [    1.020413] Linux agpgart interface v0.103
Apr 30 14:24:50 home-pc kernel: [    1.021563] brd: module loaded
Apr 30 14:24:50 home-pc kernel: [    1.022068] loop: module loaded
Apr 30 14:24:50 home-pc kernel: [    1.022163] i2c-core: driver [adp5520] using legacy suspend method
Apr 30 14:24:50 home-pc kernel: [    1.022165] i2c-core: driver [adp5520] using legacy resume method
Apr 30 14:24:50 home-pc kernel: [    1.022381] pata_acpi 0000:00:06.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.022575] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Apr 30 14:24:50 home-pc kernel: [    1.022591] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Apr 30 14:24:50 home-pc kernel: [    1.022612] pata_acpi 0000:00:08.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.022618] pata_acpi 0000:00:08.0: PCI INT A disabled
Apr 30 14:24:50 home-pc kernel: [    1.022781] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Apr 30 14:24:50 home-pc kernel: [    1.022784] pata_acpi 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Apr 30 14:24:50 home-pc kernel: [    1.022796] pata_acpi 0000:00:08.1: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.022801] pata_acpi 0000:00:08.1: PCI INT B disabled
Apr 30 14:24:50 home-pc kernel: [    1.023207] Fixed MDIO Bus: probed
Apr 30 14:24:50 home-pc kernel: [    1.023238] PPP generic driver version 2.4.2
Apr 30 14:24:50 home-pc kernel: [    1.023272] tun: Universal TUN/TAP device driver, 1.6
Apr 30 14:24:50 home-pc kernel: [    1.023274] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 30 14:24:50 home-pc kernel: [    1.023366] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 30 14:24:50 home-pc kernel: [    1.023529] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Apr 30 14:24:50 home-pc kernel: [    1.023539] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Apr 30 14:24:50 home-pc kernel: [    1.023568] ehci_hcd 0000:00:02.1: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.023570] ehci_hcd 0000:00:02.1: EHCI Host Controller
Apr 30 14:24:50 home-pc kernel: [    1.023627] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Apr 30 14:24:50 home-pc kernel: [    1.060064] ehci_hcd 0000:00:02.1: debug port 1
Apr 30 14:24:50 home-pc kernel: [    1.060071] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Apr 30 14:24:50 home-pc kernel: [    1.060094] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
Apr 30 14:24:50 home-pc kernel: [    1.080012] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Apr 30 14:24:50 home-pc kernel: [    1.080126] hub 1-0:1.0: USB hub found
Apr 30 14:24:50 home-pc kernel: [    1.080131] hub 1-0:1.0: 10 ports detected
Apr 30 14:24:50 home-pc kernel: [    1.080223] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 30 14:24:50 home-pc kernel: [    1.080386] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Apr 30 14:24:50 home-pc kernel: [    1.080395] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Apr 30 14:24:50 home-pc kernel: [    1.080404] ohci_hcd 0000:00:02.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.080407] ohci_hcd 0000:00:02.0: OHCI Host Controller
Apr 30 14:24:50 home-pc kernel: [    1.080445] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Apr 30 14:24:50 home-pc kernel: [    1.080486] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Apr 30 14:24:50 home-pc kernel: [    1.142106] hub 2-0:1.0: USB hub found
Apr 30 14:24:50 home-pc kernel: [    1.142111] hub 2-0:1.0: 10 ports detected
Apr 30 14:24:50 home-pc kernel: [    1.142189] uhci_hcd: USB Universal Host Controller Interface driver
Apr 30 14:24:50 home-pc kernel: [    1.160035] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Apr 30 14:24:50 home-pc kernel: [    1.160037] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Apr 30 14:24:50 home-pc kernel: [    1.160185] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 14:24:50 home-pc kernel: [    1.160284] mousedev: PS/2 mouse device common for all mice
Apr 30 14:24:50 home-pc kernel: [    1.160409] rtc_cmos 00:05: RTC can wake from S4
Apr 30 14:24:50 home-pc kernel: [    1.179157] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Apr 30 14:24:50 home-pc kernel: [    1.190058] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 30 14:24:50 home-pc kernel: [    1.190095] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Apr 30 14:24:50 home-pc kernel: [    1.190175] device-mapper: uevent: version 1.0.3
Apr 30 14:24:50 home-pc kernel: [    1.190239] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Apr 30 14:24:50 home-pc kernel: [    1.190332] device-mapper: multipath: version 1.2.0 loaded
Apr 30 14:24:50 home-pc kernel: [    1.190335] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 30 14:24:50 home-pc kernel: [    1.190464] cpuidle: using governor ladder
Apr 30 14:24:50 home-pc kernel: [    1.190466] cpuidle: using governor menu
Apr 30 14:24:50 home-pc kernel: [    1.190711] TCP cubic registered
Apr 30 14:24:50 home-pc kernel: [    1.190817] NET: Registered protocol family 10
Apr 30 14:24:50 home-pc kernel: [    1.191333] NET: Registered protocol family 17
Apr 30 14:24:50 home-pc kernel: [    1.191346] Registering the dns_resolver key type
Apr 30 14:24:50 home-pc kernel: [    1.191367] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (2 cpu cores) (version 2.20.00)
Apr 30 14:24:50 home-pc kernel: [    1.191421] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0x8
Apr 30 14:24:50 home-pc kernel: [    1.191422] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xa
Apr 30 14:24:50 home-pc kernel: [    1.191424] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xc
Apr 30 14:24:50 home-pc kernel: [    1.191426] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xe
Apr 30 14:24:50 home-pc kernel: [    1.191427] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
Apr 30 14:24:50 home-pc kernel: [    1.191429] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
Apr 30 14:24:50 home-pc kernel: [    1.191431] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
Apr 30 14:24:50 home-pc kernel: [    1.191592] PM: Hibernation image not present or could not be loaded.
Apr 30 14:24:50 home-pc kernel: [    1.191607] registered taskstats version 1
Apr 30 14:24:50 home-pc kernel: [    1.191838]   Magic number: 7:102:436
Apr 30 14:24:50 home-pc kernel: [    1.191962] rtc_cmos 00:05: setting system clock to 2011-04-30 14:24:37 UTC (1304173477)
Apr 30 14:24:50 home-pc kernel: [    1.191964] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 14:24:50 home-pc kernel: [    1.191966] EDD information not available.
Apr 30 14:24:50 home-pc kernel: [    1.193496] Freeing unused kernel memory: 956k freed
Apr 30 14:24:50 home-pc kernel: [    1.193995] Write protecting the kernel read-only data: 10240k
Apr 30 14:24:50 home-pc kernel: [    1.194641] Freeing unused kernel memory: 184k freed
Apr 30 14:24:50 home-pc kernel: [    1.198945] Freeing unused kernel memory: 1444k freed
Apr 30 14:24:50 home-pc kernel: [    1.220252] <30>udev[99]: starting version 167
Apr 30 14:24:50 home-pc kernel: [    1.316713] sata_nv 0000:00:08.0: version 3.5
Apr 30 14:24:50 home-pc kernel: [    1.316730] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Apr 30 14:24:50 home-pc kernel: [    1.316800] sata_nv 0000:00:08.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.318698] scsi0 : sata_nv
Apr 30 14:24:50 home-pc kernel: [    1.320370] scsi1 : sata_nv
Apr 30 14:24:50 home-pc kernel: [    1.320525] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Apr 30 14:24:50 home-pc kernel: [    1.320528] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Apr 30 14:24:50 home-pc kernel: [    1.341709] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Apr 30 14:24:50 home-pc kernel: [    1.341793] sata_nv 0000:00:08.1: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.342063] scsi2 : sata_nv
Apr 30 14:24:50 home-pc kernel: [    1.342145] scsi3 : sata_nv
Apr 30 14:24:50 home-pc kernel: [    1.342287] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Apr 30 14:24:50 home-pc kernel: [    1.342290] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Apr 30 14:24:50 home-pc kernel: [    1.342407] pata_amd 0000:00:06.0: version 0.4.1
Apr 30 14:24:50 home-pc kernel: [    1.342445] pata_amd 0000:00:06.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.342749] scsi4 : pata_amd
Apr 30 14:24:50 home-pc kernel: [    1.342818] scsi5 : pata_amd
Apr 30 14:24:50 home-pc kernel: [    1.343164] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Apr 30 14:24:50 home-pc kernel: [    1.343166] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Apr 30 14:24:50 home-pc kernel: [    1.343229] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Apr 30 14:24:50 home-pc kernel: [    1.343368] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Apr 30 14:24:50 home-pc kernel: [    1.343383] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
Apr 30 14:24:50 home-pc kernel: [    1.343386] forcedeth 0000:00:07.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    1.520020] usb 1-2: new high speed USB device using ehci_hcd and address 3
Apr 30 14:24:50 home-pc kernel: [    1.680293] ata3: SATA link down (SStatus 0 SControl 300)
Apr 30 14:24:50 home-pc kernel: [    1.686211] usbcore: registered new interface driver uas
Apr 30 14:24:50 home-pc kernel: [    1.800020] usb 1-3: new high speed USB device using ehci_hcd and address 4
Apr 30 14:24:50 home-pc kernel: [    1.810041] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 30 14:24:50 home-pc kernel: [    1.830122] ata1.00: ATA-7: WDC WD5000AAKS-65TMA0, 12.01C01, max UDMA/133
Apr 30 14:24:50 home-pc kernel: [    1.830126] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 30 14:24:50 home-pc kernel: [    1.870117] ata1.00: configured for UDMA/133
Apr 30 14:24:50 home-pc kernel: [    1.870239] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
Apr 30 14:24:50 home-pc kernel: [    1.870419] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 14:24:50 home-pc kernel: [    1.870520] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr 30 14:24:50 home-pc kernel: [    1.870565] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 14:24:50 home-pc kernel: [    1.870567] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 14:24:50 home-pc kernel: [    1.870587] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 14:24:50 home-pc kernel: [    1.870929] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:b9:74:2e:47
Apr 30 14:24:50 home-pc kernel: [    1.870932] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Apr 30 14:24:50 home-pc kernel: [    1.935131]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
Apr 30 14:24:50 home-pc kernel: [    1.935470] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 14:24:50 home-pc kernel: [    2.360040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 30 14:24:50 home-pc kernel: [    2.380127] ata2.00: ATAPI: HL-DT-STDVDRRW GSA-H30L, S755, max UDMA/33
Apr 30 14:24:50 home-pc kernel: [    2.420115] ata2.00: configured for UDMA/33
Apr 30 14:24:50 home-pc kernel: [    2.423649] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-H30L  S755 PQ: 0 ANSI: 5
Apr 30 14:24:50 home-pc kernel: [    2.427032] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 30 14:24:50 home-pc kernel: [    2.427035] cdrom: Uniform CD-ROM driver Revision: 3.20
Apr 30 14:24:50 home-pc kernel: [    2.427183] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 14:24:50 home-pc kernel: [    2.427256] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 14:24:50 home-pc kernel: [    2.760293] ata4: SATA link down (SStatus 0 SControl 300)
Apr 30 14:24:50 home-pc kernel: [    2.760375] ata6: port disabled. ignoring.
Apr 30 14:24:50 home-pc kernel: [    2.767673] Initializing USB Mass Storage driver...
Apr 30 14:24:50 home-pc kernel: [    2.767928] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Apr 30 14:24:50 home-pc kernel: [    2.767948] firewire_ohci 0000:01:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
Apr 30 14:24:50 home-pc kernel: [    2.767954] firewire_ohci 0000:01:09.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [    2.768086] scsi6 : usb-storage 1-2:1.0
Apr 30 14:24:50 home-pc kernel: [    2.768216] usbcore: registered new interface driver usb-storage
Apr 30 14:24:50 home-pc kernel: [    2.768218] USB Mass Storage support registered.
Apr 30 14:24:50 home-pc kernel: [    2.840076] firewire_ohci: Added fw-ohci device 0000:01:09.0, OHCI v1.0, 4 IR + 8 IT contexts, quirks 0x11
Apr 30 14:24:50 home-pc kernel: [    2.888873] vesafb: framebuffer at 0xdf000000, mapped to 0xffffc90005c80000, using 7552k, total 7552k
Apr 30 14:24:50 home-pc kernel: [    2.888877] vesafb: mode is 1600x1200x32, linelength=6400, pages=0
Apr 30 14:24:50 home-pc kernel: [    2.888879] vesafb: scrolling: redraw
Apr 30 14:24:50 home-pc kernel: [    2.888881] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Apr 30 14:24:50 home-pc kernel: [    2.889050] Console: switching to colour frame buffer device 200x75
Apr 30 14:24:50 home-pc kernel: [    2.889083] fb0: VESA VGA frame buffer device
Apr 30 14:24:50 home-pc kernel: [    3.195638] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Apr 30 14:24:50 home-pc kernel: [    3.340156] firewire_core: created device fw0: GUID 00000ae6ffc17497, S400
Apr 30 14:24:50 home-pc kernel: [    3.760642] scsi 6:0:0:0: Direct-Access     WD       5000AAK External 1.06 PQ: 0 ANSI: 0
Apr 30 14:24:50 home-pc kernel: [    3.761149] sd 6:0:0:0: Attached scsi generic sg2 type 0
Apr 30 14:24:50 home-pc kernel: [    3.761624] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr 30 14:24:50 home-pc kernel: [    3.762372] sd 6:0:0:0: [sdb] Write Protect is off
Apr 30 14:24:50 home-pc kernel: [    3.762374] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
Apr 30 14:24:50 home-pc kernel: [    3.763124] sd 6:0:0:0: [sdb] Asking for cache data failed
Apr 30 14:24:50 home-pc kernel: [    3.763126] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 14:24:50 home-pc kernel: [    3.765370] sd 6:0:0:0: [sdb] Asking for cache data failed
Apr 30 14:24:50 home-pc kernel: [    3.765372] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 14:24:50 home-pc kernel: [   10.808783]  sdb: sdb1 sdb2
Apr 30 14:24:50 home-pc kernel: [   10.811123] sd 6:0:0:0: [sdb] Asking for cache data failed
Apr 30 14:24:50 home-pc kernel: [   10.811126] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 14:24:50 home-pc kernel: [   10.811129] sd 6:0:0:0: [sdb] Attached SCSI disk
Apr 30 14:24:50 home-pc kernel: [   11.219953] <30>udev[384]: starting version 167
Apr 30 14:24:50 home-pc kernel: [   11.255608] lp: driver loaded but no devices found
Apr 30 14:24:50 home-pc kernel: [   11.381940] MCE: In-kernel MCE decoding enabled.
Apr 30 14:24:50 home-pc kernel: [   11.389182] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Apr 30 14:24:50 home-pc kernel: [   11.411121] EDAC MC: Ver: 2.1.0 Apr 11 2011
Apr 30 14:24:50 home-pc kernel: [   11.486132] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  ModemManager (version 0.4) starting...
Apr 30 14:24:50 home-pc avahi-daemon[891]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Apr 30 14:24:50 home-pc avahi-daemon[891]: Successfully dropped root privileges.
Apr 30 14:24:50 home-pc avahi-daemon[891]: avahi-daemon 0.6.30 starting up.
Apr 30 14:24:50 home-pc kernel: [   11.486166] i2c i2c-1: nForce2 SMBus adapter at 0xf400
Apr 30 14:24:50 home-pc kernel: [   11.492716] type=1400 audit(1304198687.789:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=591 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   11.493025] type=1400 audit(1304198687.789:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=591 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   11.493216] type=1400 audit(1304198687.789:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=591 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   11.509390] EDAC amd64_edac: v3.3.0
Apr 30 14:24:50 home-pc kernel: [   11.509635] Linux video capture interface: v2.00
Apr 30 14:24:50 home-pc kernel: [   11.520626] EDAC amd64: DRAM ECC disabled.
Apr 30 14:24:50 home-pc kernel: [   11.520636] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Apr 30 14:24:50 home-pc kernel: [   11.520637]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Apr 30 14:24:50 home-pc kernel: [   11.520638]  (Note that use of the override may cause unknown side effects.)
Apr 30 14:24:50 home-pc kernel: [   11.731507] cx18:  Start initialization, version 1.4.0
Apr 30 14:24:50 home-pc kernel: [   11.733691] cx18-0: Initializing card 0
Apr 30 14:24:50 home-pc kernel: [   11.733698] cx18-0: Autodetected Hauppauge card
Apr 30 14:24:50 home-pc kernel: [   11.733909] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Apr 30 14:24:50 home-pc kernel: [   11.733933] cx18 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:24:50 home-pc kernel: [   11.733945] cx18-0: Unreasonably low latency timer, setting to 64 (was 2)
Apr 30 14:24:50 home-pc kernel: [   11.739511] cx18-0: cx23418 revision 01010000 (B)
Apr 30 14:24:50 home-pc kernel: [   11.743523] nvidia: module license 'NVIDIA' taints kernel.
Apr 30 14:24:50 home-pc kernel: [   11.743529] Disabling lock debugging due to kernel taint
Apr 30 14:24:50 home-pc kernel: [   11.776789] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Apr 30 14:24:50 home-pc kernel: [   11.776800] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Apr 30 14:24:50 home-pc kernel: [   11.776804] hda_intel: Disable MSI for Nvidia chipset
Apr 30 14:24:50 home-pc kernel: [   11.776859] HDA Intel 0000:00:05.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [   12.359903] tveeprom 2-0050: Hauppauge model 74551, rev C1A3, serial# 1898996
Apr 30 14:24:50 home-pc kernel: [   12.359907] tveeprom 2-0050: MAC address is 00:0d:fe:1c:f9:f4
Apr 30 14:24:50 home-pc kernel: [   12.359910] tveeprom 2-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
Apr 30 14:24:50 home-pc kernel: [   12.359912] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
Apr 30 14:24:50 home-pc kernel: [   12.359915] tveeprom 2-0050: audio processor is CX23418 (idx 38)
Apr 30 14:24:50 home-pc kernel: [   12.359917] tveeprom 2-0050: decoder processor is CX23418 (idx 31)
Apr 30 14:24:50 home-pc kernel: [   12.359918] tveeprom 2-0050: has radio
Apr 30 14:24:50 home-pc kernel: [   12.359921] cx18-0: Autodetected Hauppauge HVR-1600
Apr 30 14:24:50 home-pc kernel: [   12.359922] cx18-0: Simultaneous Digital and Analog TV capture supported
Apr 30 14:24:50 home-pc kernel: [   12.436376] i2c-core: driver [tuner] using legacy suspend method
Apr 30 14:24:50 home-pc kernel: [   12.436379] i2c-core: driver [tuner] using legacy resume method
Apr 30 14:24:50 home-pc kernel: [   12.446874] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
Apr 30 14:24:50 home-pc kernel: [   12.449430] tda9887 3-0043: creating new instance
Apr 30 14:24:50 home-pc kernel: [   12.449434] tda9887 3-0043: tda988[5/6/7] found
Apr 30 14:24:50 home-pc kernel: [   12.452058] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
Apr 30 14:24:50 home-pc kernel: [   12.456326] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
Apr 30 14:24:50 home-pc kernel: [   12.463894] tuner-simple 3-0061: creating new instance
Apr 30 14:24:50 home-pc kernel: [   12.463898] tuner-simple 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
Apr 30 14:24:50 home-pc kernel: [   12.466183] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
Apr 30 14:24:50 home-pc kernel: [   12.466186] DVB: registering new adapter (cx18)
Apr 30 14:24:50 home-pc kernel: [   12.504385] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
Apr 30 14:24:50 home-pc kernel: [   12.504394] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:24:50 home-pc kernel: [   12.504404] nvidia 0000:02:00.0: setting latency timer to 64
Apr 30 14:24:50 home-pc kernel: [   12.504409] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr 30 14:24:50 home-pc kernel: [   12.504768] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
Apr 30 14:24:50 home-pc kernel: [   12.524611] MXL5005S: Attached at address 0x63
Apr 30 14:24:50 home-pc kernel: [   12.524618] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Apr 30 14:24:50 home-pc kernel: [   12.524748] cx18-0: DVB Frontend registered
Apr 30 14:24:50 home-pc kernel: [   12.524750] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
Apr 30 14:24:50 home-pc kernel: [   12.524785] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
Apr 30 14:24:50 home-pc kernel: [   12.524812] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
Apr 30 14:24:50 home-pc kernel: [   12.524838] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
Apr 30 14:24:50 home-pc kernel: [   12.524865] cx18-0: Registered device radio0 for encoder radio
Apr 30 14:24:50 home-pc kernel: [   12.524867] cx18-0: Initialized card: Hauppauge HVR-1600
Apr 30 14:24:50 home-pc kernel: [   12.524918] cx18:  End initialization
Apr 30 14:24:50 home-pc kernel: [   12.532387] cx18-alsa: module loading...
Apr 30 14:24:50 home-pc kernel: [   12.655956] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
Apr 30 14:24:50 home-pc kernel: [   12.774777] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
Apr 30 14:24:50 home-pc kernel: [   12.775273] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Apr 30 14:24:50 home-pc kernel: [   12.781014] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
Apr 30 14:24:50 home-pc kernel: [   12.870316] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Apr 30 14:24:50 home-pc kernel: [   13.628118] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
Apr 30 14:24:50 home-pc kernel: [   13.647306] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
Apr 30 14:24:50 home-pc kernel: [   13.983736] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Apr 30 14:24:50 home-pc kernel: [   14.090060] hda_codec: ALC1200: SKU not ready 0x411111f0
Apr 30 14:24:50 home-pc kernel: [   14.185487] type=1400 audit(1304198690.479:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=888 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   14.190792] type=1400 audit(1304198690.489:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=889 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   14.191119] type=1400 audit(1304198690.489:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=889 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   14.191489] type=1400 audit(1304198690.489:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=889 comm="apparmor_parser"
Apr 30 14:24:50 home-pc gdm-binary[873]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 30 14:24:50 home-pc avahi-daemon[891]: Successfully called chroot().
Apr 30 14:24:50 home-pc avahi-daemon[891]: Successfully dropped remaining capabilities.
Apr 30 14:24:50 home-pc avahi-daemon[891]: Loading service file /services/udisks.service.
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Nokia
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin ZTE
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin X22X
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Linktop
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Longcheer
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Gobi
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin SimTech
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Sierra
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Ericsson MBM
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Huawei
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Option High-Speed
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Generic
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin MotoC
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Option
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin AnyData
Apr 30 14:24:50 home-pc modem-manager[887]: <info>  Loaded plugin Novatel
Apr 30 14:24:50 home-pc avahi-daemon[891]: Network interface enumeration completed.
Apr 30 14:24:50 home-pc avahi-daemon[891]: Registering HINFO record with values 'X86_64'/'LINUX'.
Apr 30 14:24:50 home-pc avahi-daemon[891]: Server startup complete. Host name is home-pc.local. Local service cookie is 853356546.
Apr 30 14:24:50 home-pc avahi-daemon[891]: Service "home-pc" (/services/udisks.service) successfully established.
Apr 30 14:24:50 home-pc kernel: [   14.210317] type=1400 audit(1304198690.509:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=893 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   14.217336] type=1400 audit(1304198690.509:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=893 comm="apparmor_parser"
Apr 30 14:24:50 home-pc kernel: [   14.222430] type=1400 audit(1304198690.519:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=895 comm="apparmor_parser"
Apr 30 14:24:50 home-pc polkitd[898]: started daemon version 0.101 using authority implementation `local' version `0.101'
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: init!
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: update_system_hostname
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPluginIfupdown: management mode: unmanaged
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/net/eth0, iface: eth0)
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: end _init.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 30 14:24:50 home-pc NetworkManager[884]:    Ifupdown: get unmanaged devices count: 0
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: (30858592) ... get_connections.
Apr 30 14:24:50 home-pc NetworkManager[884]:    SCPlugin-Ifupdown: (30858592) ... get_connections (managed=false): return empty list.
Apr 30 14:24:50 home-pc NetworkManager[884]:    Ifupdown: get unmanaged devices count: 0
Apr 30 14:24:50 home-pc init: apport pre-start process (1000) terminated with status 1
Apr 30 14:24:50 home-pc anacron[1029]: Anacron 2.3 started on 2011-04-30
Apr 30 14:24:50 home-pc acpid: starting up with proc fs
Apr 30 14:24:50 home-pc cron[1011]: (CRON) INFO (pidfile fd = 3)
Apr 30 14:24:50 home-pc acpid: 32 rules loaded
Apr 30 14:24:50 home-pc acpid: waiting for events: event logging is off
Apr 30 14:24:50 home-pc init: apport post-stop process (1037) terminated with status 1
Apr 30 14:24:50 home-pc cron[1038]: (CRON) STARTUP (fork ok)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Networking is enabled by state file
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): carrier is OFF
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): now managed
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): bringing up device.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): preparing device.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): deactivating device (reason: 2).
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:07.0/net/eth0
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): carrier now ON (device state 2)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> modem-manager is now available
Apr 30 14:24:50 home-pc NetworkManager[884]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Trying to start the supplicant...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) starting connection 'Auto eth0'
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> dhclient started with pid 1045
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 30 14:24:50 home-pc kernel: [   14.390890] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
Apr 30 14:24:50 home-pc dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr 30 14:24:50 home-pc dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr 30 14:24:50 home-pc dhclient: All rights reserved.
Apr 30 14:24:50 home-pc dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 30 14:24:50 home-pc dhclient: 
Apr 30 14:24:50 home-pc gdm-binary[873]: WARNING: Unable to find users: no seat-id found
Apr 30 14:24:50 home-pc gdm-simple-slave[1047]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 30 14:24:50 home-pc anacron[1029]: Normal exit (0 jobs run)
Apr 30 14:24:50 home-pc cron[1038]: (CRON) INFO (Running @reboot jobs)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 30 14:24:50 home-pc acpid: client connected from 1089[0:0]
Apr 30 14:24:50 home-pc acpid: 1 client rule loaded
Apr 30 14:24:50 home-pc dhclient: Listening on LPF/eth0/00:1b:b9:74:2e:47
Apr 30 14:24:50 home-pc dhclient: Sending on   LPF/eth0/00:1b:b9:74:2e:47
Apr 30 14:24:50 home-pc dhclient: Sending on   Socket/fallback
Apr 30 14:24:50 home-pc dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 14:24:50 home-pc dhclient: DHCPOFFER of 192.168.0.100 from 192.168.0.1
Apr 30 14:24:50 home-pc dhclient: DHCPREQUEST of 192.168.0.100 on eth0 to 255.255.255.255 port 67
Apr 30 14:24:50 home-pc dhclient: DHCPACK of 192.168.0.100 from 192.168.0.1
Apr 30 14:24:50 home-pc dhclient: bound to 192.168.0.100 -- renewal in 242026 seconds.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info>   address 192.168.0.100
Apr 30 14:24:50 home-pc NetworkManager[884]: <info>   prefix 24 (255.255.255.0)
Apr 30 14:24:50 home-pc NetworkManager[884]: <info>   gateway 192.168.0.1
Apr 30 14:24:50 home-pc NetworkManager[884]: <info>   nameserver '192.168.0.1'
Apr 30 14:24:50 home-pc NetworkManager[884]: <info>   domain name 'sd.cox.net'
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Scheduling stage 5
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Done scheduling stage 5
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 30 14:24:50 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 30 14:24:50 home-pc avahi-daemon[891]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.100.
Apr 30 14:24:50 home-pc kernel: [   14.620820] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Apr 30 14:24:50 home-pc kernel: [   14.620828] HDA Intel 0000:02:00.1: PCI INT B -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:24:50 home-pc kernel: [   14.620831] hda_intel: Disable MSI for Nvidia chipset
Apr 30 14:24:50 home-pc kernel: [   14.620860] HDA Intel 0000:02:00.1: setting latency timer to 64
Apr 30 14:24:50 home-pc avahi-daemon[891]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 14:24:50 home-pc avahi-daemon[891]: Registering new address record for 192.168.0.100 on eth0.IPv4.
Apr 30 14:24:50 home-pc anacron[1185]: Anacron 2.3 started on 2011-04-30
Apr 30 14:24:50 home-pc anacron[1185]: Normal exit (0 jobs run)
Apr 30 14:24:51 home-pc acpid: client connected from 1089[0:0]
Apr 30 14:24:51 home-pc acpid: 1 client rule loaded
Apr 30 14:24:51 home-pc kernel: [   15.525298] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr 30 14:24:51 home-pc kernel: [   15.617508] EXT4-fs (sda2): re-mounted. Opts: commit=0
Apr 30 14:24:51 home-pc NetworkManager[884]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Apr 30 14:24:52 home-pc NetworkManager[884]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Apr 30 14:24:52 home-pc NetworkManager[884]: <info> Activation (eth0) successful, device activated.
Apr 30 14:24:52 home-pc NetworkManager[884]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 30 14:24:52 home-pc kernel: [   15.977021] EXT4-fs (sda7): re-mounted. Opts: commit=0
Apr 30 14:24:52 home-pc gdm-session-worker[1286]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 30 14:24:52 home-pc avahi-daemon[891]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21b:b9ff:fe74:2e47.
Apr 30 14:24:52 home-pc avahi-daemon[891]: New relevant interface eth0.IPv6 for mDNS.
Apr 30 14:24:52 home-pc avahi-daemon[891]: Registering new address record for fe80::21b:b9ff:fe74:2e47 on eth0.*.
Apr 30 14:24:52 home-pc init: plymouth-stop pre-start process (1333) terminated with status 1
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Successfully called chroot.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Successfully dropped privileges.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Successfully limited resources.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Running.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Watchdog thread running.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Canary thread running.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Successfully made thread 1332 of process 1332 (n/a) owned by '106' high priority at nice level -11.
Apr 30 14:24:52 home-pc rtkit-daemon[1338]: Supervising 1 threads of 1 processes of 1 users.
Apr 30 14:24:52 home-pc anacron[1390]: Anacron 2.3 started on 2011-04-30
Apr 30 14:24:52 home-pc anacron[1390]: Normal exit (0 jobs run)
Apr 30 14:24:52 home-pc gdm-simple-greeter[1284]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Apr 30 14:24:53 home-pc kernel: [   16.800717] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr 30 14:24:53 home-pc kernel: [   16.804339] EXT4-fs (sda2): re-mounted. Opts: commit=0
Apr 30 14:24:53 home-pc kernel: [   16.807458] EXT4-fs (sda7): re-mounted. Opts: commit=0
Apr 30 14:24:53 home-pc gdm-simple-greeter[1284]: WARNING: Unable to load CK history: no seat-id found
Apr 30 14:24:53 home-pc kernel: [   16.920053] usb 1-3: device descriptor read/64, error -110
Apr 30 14:24:54 home-pc kernel: [   18.600401] ppdev: user-space parallel port driver
Apr 30 14:24:54 home-pc kernel: [   18.617101] audit_printk_skb: 9 callbacks suppressed
Apr 30 14:24:54 home-pc kernel: [   18.617105] type=1400 audit(1304198694.909:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1476 comm="apparmor_parser"
Apr 30 14:24:54 home-pc kernel: [   18.618349] type=1400 audit(1304198694.909:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1476 comm="apparmor_parser"
Apr 30 14:24:55 home-pc kernel: [   18.769908] Intel AES-NI instructions are not detected.
Apr 30 14:24:55 home-pc kernel: [   18.811544] padlock_aes: VIA PadLock not detected.
Apr 30 14:24:55 home-pc kernel: [   18.857499] padlock_sha: VIA PadLock Hash Engine not detected.
Apr 30 14:24:55 home-pc modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.38-8-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Apr 30 14:24:55 home-pc kernel: [   18.993335] Adding 7811068k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:7811068k 
Apr 30 14:24:59 home-pc rtkit-daemon[1338]: Successfully made thread 1557 of process 1332 (n/a) owned by '106' RT at priority 5.
Apr 30 14:24:59 home-pc rtkit-daemon[1338]: Supervising 2 threads of 1 processes of 1 users.
Apr 30 14:24:59 home-pc pulseaudio[1332]: module-alsa-card.c: Failed to find a working profile.
Apr 30 14:24:59 home-pc pulseaudio[1332]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="2" name="pci-0000_02_00.1" card_name="alsa_card.pci-0000_02_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 30 14:24:59 home-pc rtkit-daemon[1338]: Successfully made thread 1561 of process 1332 (n/a) owned by '106' RT at priority 5.
Apr 30 14:24:59 home-pc rtkit-daemon[1338]: Supervising 3 threads of 1 processes of 1 users.
Apr 30 14:24:59 home-pc rtkit-daemon[1338]: Successfully made thread 1562 of process 1332 (n/a) owned by '106' RT at priority 5.
Apr 30 14:24:59 home-pc rtkit-daemon[1338]: Supervising 4 threads of 1 processes of 1 users.
Apr 30 14:25:00 home-pc ntpdate[1260]: adjust time server 91.189.94.4 offset 0.095082 sec
Apr 30 14:25:01 home-pc kernel: [   25.220022] eth0: no IPv6 routers present
Apr 30 14:25:08 home-pc kernel: [   32.150043] usb 1-3: device descriptor read/64, error -110
Apr 30 14:25:08 home-pc kernel: [   32.380039] usb 1-3: new high speed USB device using ehci_hcd and address 5
Apr 30 14:25:14 home-pc gdm-session-worker[1286]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 30 14:25:18 home-pc gdm-session-worker[1286]: pam_sm_authenticate: Called
Apr 30 14:25:18 home-pc gdm-session-worker[1286]: pam_sm_authenticate: username = [derek]
Apr 30 14:25:18 home-pc gdm-session-worker[1566]: Passphrase file wrapped
Apr 30 14:25:20 home-pc rtkit-daemon[1338]: Successfully made thread 1664 of process 1664 (n/a) owned by '1000' high priority at nice level -11.
Apr 30 14:25:20 home-pc rtkit-daemon[1338]: Supervising 5 threads of 2 processes of 2 users.
Apr 30 14:25:21 home-pc rtkit-daemon[1338]: Successfully made thread 1701 of process 1664 (n/a) owned by '1000' RT at priority 5.
Apr 30 14:25:21 home-pc rtkit-daemon[1338]: Supervising 6 threads of 2 processes of 2 users.
Apr 30 14:25:21 home-pc rtkit-daemon[1338]: Successfully made thread 1702 of process 1664 (n/a) owned by '1000' RT at priority 5.
Apr 30 14:25:21 home-pc rtkit-daemon[1338]: Supervising 7 threads of 2 processes of 2 users.
Apr 30 14:25:21 home-pc nautilus: [N-A] Nautilus-Actions Tracker 3.0.5 initializing...
Apr 30 14:25:21 home-pc nautilus: [N-A] Nautilus-Actions Menu Extender 3.0.5 initializing...
Apr 30 14:25:22 home-pc rtkit-daemon[1338]: Successfully made thread 1749 of process 1664 (n/a) owned by '1000' RT at priority 5.
Apr 30 14:25:22 home-pc rtkit-daemon[1338]: Supervising 8 threads of 2 processes of 2 users.
Apr 30 14:25:23 home-pc kernel: [   47.266074] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
Apr 30 14:25:23 home-pc kernel: [   47.500059] usb 1-3: device descriptor read/64, error -110
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Successfully made thread 1833 of process 1664 (n/a) owned by '1000' RT at priority 5.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Supervising 9 threads of 2 processes of 2 users.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Successfully made thread 1836 of process 1836 (n/a) owned by '1000' high priority at nice level -11.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Supervising 10 threads of 3 processes of 2 users.
Apr 30 14:25:29 home-pc pulseaudio[1836]: pid.c: Daemon already running.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Successfully made thread 1837 of process 1837 (n/a) owned by '1000' high priority at nice level -11.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Supervising 10 threads of 3 processes of 2 users.
Apr 30 14:25:29 home-pc pulseaudio[1837]: pid.c: Daemon already running.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Successfully made thread 1839 of process 1839 (n/a) owned by '1000' high priority at nice level -11.
Apr 30 14:25:29 home-pc rtkit-daemon[1338]: Supervising 10 threads of 3 processes of 2 users.
Apr 30 14:25:29 home-pc pulseaudio[1839]: pid.c: Daemon already running.
Apr 30 14:25:39 home-pc kernel: [   62.730025] usb 1-3: device descriptor read/64, error -110
Apr 30 14:25:39 home-pc kernel: [   62.960041] usb 1-3: new high speed USB device using ehci_hcd and address 6
Apr 30 14:25:44 home-pc kernel: [   67.990258] usb 1-3: device descriptor read/8, error -110
Apr 30 14:25:49 home-pc kernel: [   73.120067] usb 1-3: device descriptor read/8, error -110
Apr 30 14:25:49 home-pc kernel: [   73.350039] usb 1-3: new high speed USB device using ehci_hcd and address 7
Apr 30 14:25:54 home-pc kernel: [   78.380077] usb 1-3: device descriptor read/8, error -110
Apr 30 14:25:59 home-pc kernel: [   83.510165] usb 1-3: device descriptor read/8, error -110
Apr 30 14:25:59 home-pc kernel: [   83.620068] hub 1-0:1.0: unable to enumerate USB device on port 3
Apr 30 14:26:00 home-pc kernel: [   83.960061] usb 1-7: new high speed USB device using ehci_hcd and address 10
Apr 30 14:26:00 home-pc kernel: [   84.112894] scsi7 : usb-storage 1-7:1.0
Apr 30 14:26:00 home-pc kernel: [   84.450052] usb 2-1: new full speed USB device using ohci_hcd and address 2
Apr 30 14:26:01 home-pc udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1
Apr 30 14:26:01 home-pc udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2/2-1
Apr 30 14:26:01 home-pc udev-configure-printer: Device vendor/product is 03F0:3F11
Apr 30 14:26:01 home-pc kernel: [   84.730355] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
Apr 30 14:26:01 home-pc kernel: [   84.731548] usbcore: registered new interface driver usblp
Apr 30 14:26:01 home-pc udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/usb/lp0
Apr 30 14:26:01 home-pc kernel: [   85.030050] usb 2-3: new full speed USB device using ohci_hcd and address 3
Apr 30 14:26:01 home-pc kernel: [   85.111122] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Apr 30 14:26:01 home-pc kernel: [   85.111844] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Apr 30 14:26:01 home-pc kernel: [   85.112465] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Apr 30 14:26:01 home-pc kernel: [   85.113091] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Apr 30 14:26:01 home-pc kernel: [   85.114269] sd 7:0:0:0: Attached scsi generic sg3 type 0
Apr 30 14:26:01 home-pc kernel: [   85.114927] sd 7:0:0:1: Attached scsi generic sg4 type 0
Apr 30 14:26:01 home-pc kernel: [   85.118210] sd 7:0:0:2: Attached scsi generic sg5 type 0
Apr 30 14:26:01 home-pc kernel: [   85.118563] sd 7:0:0:3: Attached scsi generic sg6 type 0
Apr 30 14:26:01 home-pc kernel: [   85.126232] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Apr 30 14:26:01 home-pc kernel: [   85.128719] sd 7:0:0:1: [sdd] Attached SCSI removable disk
Apr 30 14:26:01 home-pc kernel: [   85.129773] sd 7:0:0:2: [sde] Attached SCSI removable disk
Apr 30 14:26:01 home-pc kernel: [   85.130341] sd 7:0:0:3: [sdf] Attached SCSI removable disk
Apr 30 14:26:16 home-pc kernel: [  100.210055] usb 2-3: device descriptor read/64, error -110
Apr 30 14:26:31 home-pc kernel: [  115.500042] usb 2-3: device descriptor read/64, error -110
Apr 30 14:26:32 home-pc kernel: [  115.790053] usb 2-3: new full speed USB device using ohci_hcd and address 4
Apr 30 14:26:47 home-pc kernel: [  130.970052] usb 2-3: device descriptor read/64, error -110
Apr 30 14:27:02 home-pc kernel: [  146.260053] usb 2-3: device descriptor read/64, error -110
Apr 30 14:27:02 home-pc kernel: [  146.550051] usb 2-3: new full speed USB device using ohci_hcd and address 5
Apr 30 14:27:07 home-pc kernel: [  151.580467] usb 2-3: device descriptor read/8, error -110
Apr 30 14:27:13 home-pc kernel: [  156.711016] usb 2-3: device descriptor read/8, error -110
Apr 30 14:27:13 home-pc kernel: [  157.000049] usb 2-3: new full speed USB device using ohci_hcd and address 6
Apr 30 14:27:18 home-pc kernel: [  162.030668] usb 2-3: device descriptor read/8, error -110
Apr 30 14:27:23 home-pc kernel: [  167.160247] usb 2-3: device descriptor read/8, error -110
Apr 30 14:27:23 home-pc kernel: [  167.270065] hub 2-0:1.0: unable to enumerate USB device on port 3
Apr 30 14:27:23 home-pc kernel: [  167.610050] usb 2-4: new full speed USB device using ohci_hcd and address 7
Apr 30 14:27:24 home-pc kernel: [  167.884781] IR NEC protocol handler initialized
Apr 30 14:27:24 home-pc kernel: [  167.889851] IR RC5(x) protocol handler initialized
Apr 30 14:27:24 home-pc kernel: [  167.895769] IR RC6 protocol handler initialized
Apr 30 14:27:24 home-pc kernel: [  167.901146] IR JVC protocol handler initialized
Apr 30 14:27:24 home-pc kernel: [  167.905501] IR Sony protocol handler initialized
Apr 30 14:27:24 home-pc kernel: [  167.913057] lirc_dev: IR Remote Control driver registered, major 250 
Apr 30 14:27:24 home-pc kernel: [  167.916074] IR LIRC bridge handler initialized
Apr 30 14:27:24 home-pc kernel: [  167.920147] Registered IR keymap rc-rc6-mce
Apr 30 14:27:24 home-pc kernel: [  167.920516] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:060c) as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/rc/rc0/input3
Apr 30 14:27:24 home-pc kernel: [  167.920675] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:060c) as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/rc/rc0
Apr 30 14:27:24 home-pc kernel: [  167.920876] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
Apr 30 14:27:24 home-pc kernel: [  167.920944] mceusb 2-4:1.0: Registered   BB+ Dongle(e.d) on usb2:7
Apr 30 14:27:24 home-pc kernel: [  167.920991] usbcore: registered new interface driver mceusb
Apr 30 14:27:24 home-pc kernel: [  168.180062] usb 2-6: new low speed USB device using ohci_hcd and address 8
Apr 30 14:27:24 home-pc kernel: [  168.458567] input: HP HP Wireless 3 Button Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input4
Apr 30 14:27:24 home-pc kernel: [  168.458883] generic-usb 0003:0461:4D89.0001: input,hidraw0: USB HID v1.10 Mouse [HP HP Wireless 3 Button Mouse] on usb-0000:00:02.0-6/input0
Apr 30 14:27:24 home-pc kernel: [  168.458931] usbcore: registered new interface driver usbhid
Apr 30 14:27:24 home-pc kernel: [  168.458936] usbhid: USB HID core driver
Apr 30 14:27:24 home-pc udev-configure-printer: failed to claim interface
Apr 30 14:27:24 home-pc udev-configure-printer: invalid or missing IEEE 1284 Device ID
Apr 30 14:27:24 home-pc udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2/2-1
Apr 30 14:27:24 home-pc udev-configure-printer: MFG:hp MDL:psc 1310 series  SERN:MY42Q2D2J0O2 serial:MY42Q2D2J0O2
Apr 30 14:27:25 home-pc kernel: [  169.603493] usb 2-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Apr 30 14:27:27 home-pc udev-configure-printer: SERN fields match
Apr 30 14:27:27 home-pc udev-configure-printer: URI match: usb://hp/psc%201310%20series?serial=MY42Q2D2J0O2
Apr 30 14:27:27 home-pc udev-configure-printer: SERN fields match
Apr 30 14:27:27 home-pc udev-configure-printer: URI match: hp:/usb/psc_1310_series?serial=MY42Q2D2J0O2
Apr 30 14:27:27 home-pc udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Apr 30 14:27:27 home-pc udev-configure-printer: URI of print queue: hp:/usb/psc_1310_series?serial=MY42Q2D2J0O2, normalized: psc 1310 series serial my42q2d2j0o2
Apr 30 14:27:27 home-pc udev-configure-printer: URI of detected printer: usb://hp/psc%201310%20series?serial=MY42Q2D2J0O2, normalized: psc 1310 series serial my42q2d2j0o2
Apr 30 14:27:27 home-pc udev-configure-printer: Queue ipp://localhost:631/printers/psc-1310-series has matching device URI
Apr 30 14:27:27 home-pc udev-configure-printer: URI of detected printer: hp:/usb/psc_1310_series?serial=MY42Q2D2J0O2, normalized: psc 1310 series serial my42q2d2j0o2
Apr 30 14:27:27 home-pc udev-configure-printer: Queue ipp://localhost:631/printers/psc-1310-series has matching device URI

```

---

### Post by Derek Karpinski on 2011-04-30
lsusb:

```
derek@home-pc:~$ lsusb
Bus 002 Device 008: ID 0461:4d89 Primax Electronics, Ltd 
Bus 002 Device 007: ID 0471:060c Philips (or NXP) Consumer Infrared Transceiver (HP)
Bus 002 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 003: ID 1058:0910 Western Digital Technologies, Inc. MyBook Essential External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Wireless mouse is: Bus 002 Device 008: ID 0461:4d89 Primax Electronics, Ltd

---

### Post by Derek Karpinski on 2011-04-30
Xorg.0.log:

```
[    14.715] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.716] X Protocol Version 11, Revision 0
[    14.716] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.716] Current Operating System: Linux home-pc 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    14.716] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=cf8d00a6-eaff-476c-8b7b-950aa8745431 ro splash vga=799 quiet quiet splash vt.handoff=7
[    14.716] Build Date: 19 April 2011  03:40:45PM
[    14.716] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    14.716] Current version of pixman: 0.20.2
[    14.716] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.716] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.716] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 30 16:17:58 2011
[    14.716] (==) Using config file: "/etc/X11/xorg.conf"
[    14.716] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.716] (==) No Layout section.  Using the first Screen section.
[    14.716] (==) No screen section available. Using defaults.
[    14.716] (**) |-->Screen "Default Screen Section" (0)
[    14.716] (**) |   |-->Monitor "<default monitor>"
[    14.716] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    14.716] (**) |   |-->Device "Default Device"
[    14.716] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.716] (==) Automatically adding devices
[    14.716] (==) Automatically enabling devices
[    14.716] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.716] 	Entry deleted from font path.
[    14.716] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.716] 	Entry deleted from font path.
[    14.716] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.716] 	Entry deleted from font path.
[    14.717] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.717] 	Entry deleted from font path.
[    14.717] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.717] 	Entry deleted from font path.
[    14.717] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.717] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.717] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.717] (II) Loader magic: 0x7e0280
[    14.717] (II) Module ABI versions:
[    14.717] 	X.Org ANSI C Emulation: 0.4
[    14.717] 	X.Org Video Driver: 10.0
[    14.717] 	X.Org XInput driver : 12.3
[    14.717] 	X.Org Server Extension : 5.0
[    14.717] (--) PCI: (0:1:5:0) 14f1:5b7a:0070:7400 rev 0, Mem @ 0xe8000000/67108864
[    14.717] (--) PCI:*(0:2:0:0) 10de:0a65:10de:0000 rev 162, Mem @ 0xfb000000/16777216, 0xc0000000/268435456, 0xde000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/524288
[    14.718] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.718] (II) LoadModule: "extmod"
[    14.718] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.719] (II) Module extmod: vendor="X.Org Foundation"
[    14.719] 	compiled for 1.10.1, module version = 1.0.0
[    14.719] 	Module class: X.Org Server Extension
[    14.719] 	ABI class: X.Org Server Extension, version 5.0
[    14.719] (II) Loading extension MIT-SCREEN-SAVER
[    14.719] (II) Loading extension XFree86-VidModeExtension
[    14.719] (II) Loading extension XFree86-DGA
[    14.719] (II) Loading extension DPMS
[    14.719] (II) Loading extension XVideo
[    14.719] (II) Loading extension XVideo-MotionCompensation
[    14.719] (II) Loading extension X-Resource
[    14.719] (II) LoadModule: "dbe"
[    14.719] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.719] (II) Module dbe: vendor="X.Org Foundation"
[    14.719] 	compiled for 1.10.1, module version = 1.0.0
[    14.719] 	Module class: X.Org Server Extension
[    14.719] 	ABI class: X.Org Server Extension, version 5.0
[    14.719] (II) Loading extension DOUBLE-BUFFER
[    14.719] (II) LoadModule: "glx"
[    14.719] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    14.756] (II) Module glx: vendor="NVIDIA Corporation"
[    14.756] 	compiled for 4.0.2, module version = 1.0.0
[    14.756] 	Module class: X.Org Server Extension
[    14.756] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    14.756] (II) Loading extension GLX
[    14.756] (II) LoadModule: "record"
[    14.757] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.757] (II) Module record: vendor="X.Org Foundation"
[    14.757] 	compiled for 1.10.1, module version = 1.13.0
[    14.757] 	Module class: X.Org Server Extension
[    14.757] 	ABI class: X.Org Server Extension, version 5.0
[    14.757] (II) Loading extension RECORD
[    14.757] (II) LoadModule: "dri"
[    14.757] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.757] (II) Module dri: vendor="X.Org Foundation"
[    14.757] 	compiled for 1.10.1, module version = 1.0.0
[    14.757] 	ABI class: X.Org Server Extension, version 5.0
[    14.757] (II) Loading extension XFree86-DRI
[    14.757] (II) LoadModule: "dri2"
[    14.757] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.757] (II) Module dri2: vendor="X.Org Foundation"
[    14.757] 	compiled for 1.10.1, module version = 1.2.0
[    14.757] 	ABI class: X.Org Server Extension, version 5.0
[    14.758] (II) Loading extension DRI2
[    14.758] (==) Matched nvidia as autoconfigured driver 0
[    14.758] (==) Matched nouveau as autoconfigured driver 1
[    14.758] (==) Matched nv as autoconfigured driver 2
[    14.758] (==) Matched vesa as autoconfigured driver 3
[    14.758] (==) Matched fbdev as autoconfigured driver 4
[    14.758] (==) Assigned the driver to the xf86ConfigLayout
[    14.758] (II) LoadModule: "nvidia"
[    14.758] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    14.758] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.758] 	compiled for 4.0.2, module version = 1.0.0
[    14.758] 	Module class: X.Org Video Driver
[    14.759] (II) LoadModule: "nouveau"
[    14.759] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.759] (II) Module nouveau: vendor="X.Org Foundation"
[    14.759] 	compiled for 1.10.0, module version = 0.0.16
[    14.759] 	Module class: X.Org Video Driver
[    14.759] 	ABI class: X.Org Video Driver, version 10.0
[    14.759] (II) LoadModule: "nv"
[    14.768] (WW) Warning, couldn't open module nv
[    14.768] (II) UnloadModule: "nv"
[    14.768] (II) Unloading nv
[    14.768] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.768] (II) LoadModule: "vesa"
[    14.768] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.768] (II) Module vesa: vendor="X.Org Foundation"
[    14.768] 	compiled for 1.10.0, module version = 2.3.0
[    14.768] 	Module class: X.Org Video Driver
[    14.768] 	ABI class: X.Org Video Driver, version 10.0
[    14.768] (II) LoadModule: "fbdev"
[    14.768] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.768] (II) Module fbdev: vendor="X.Org Foundation"
[    14.769] 	compiled for 1.10.0, module version = 0.4.2
[    14.769] 	ABI class: X.Org Video Driver, version 10.0
[    14.769] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    14.769] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.769] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    14.769] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.769] 	RIVA TNT    (NV04)
[    14.769] 	RIVA TNT2   (NV05)
[    14.769] 	GeForce 256 (NV10)
[    14.769] 	GeForce 2   (NV11, NV15)
[    14.769] 	GeForce 4MX (NV17, NV18)
[    14.769] 	GeForce 3   (NV20)
[    14.769] 	GeForce 4Ti (NV25, NV28)
[    14.769] 	GeForce FX  (NV3x)
[    14.769] 	GeForce 6   (NV4x)
[    14.769] 	GeForce 7   (G7x)
[    14.769] 	GeForce 8   (G8x)
[    14.769] (II) VESA: driver for VESA chipsets: vesa
[    14.769] (II) FBDEV: driver for framebuffer: fbdev
[    14.769] (++) using VT number 7

[    14.769] (II) Loading sub module "fb"
[    14.769] (II) LoadModule: "fb"
[    14.769] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.769] (II) Module fb: vendor="X.Org Foundation"
[    14.769] 	compiled for 1.10.1, module version = 1.0.0
[    14.769] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.770] (II) Loading sub module "wfb"
[    14.770] (II) LoadModule: "wfb"
[    14.770] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.770] (II) Module wfb: vendor="X.Org Foundation"
[    14.770] 	compiled for 1.10.1, module version = 1.0.0
[    14.770] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.770] (II) Loading sub module "ramdac"
[    14.770] (II) LoadModule: "ramdac"
[    14.770] (II) Module "ramdac" already built-in
[    14.770] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    14.770] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.770] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.770] (WW) Falling back to old probe method for vesa
[    14.770] (WW) Falling back to old probe method for fbdev
[    14.770] (II) Loading sub module "fbdevhw"
[    14.770] (II) LoadModule: "fbdevhw"
[    14.770] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.770] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.770] 	compiled for 1.10.1, module version = 0.0.2
[    14.770] 	ABI class: X.Org Video Driver, version 10.0
[    14.770] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.770] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    14.770] (==) NVIDIA(0): RGB weight 888
[    14.770] (==) NVIDIA(0): Default visual is TrueColor
[    14.770] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.770] (**) NVIDIA(0): Option "NoLogo" "True"
[    15.493] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    15.493] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    15.494] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:2:0:0 (GPU-0)
[    15.494] (--) NVIDIA(0): Memory: 1048576 kBytes
[    15.494] (--) NVIDIA(0): VideoBIOS: 70.18.66.00.0b
[    15.494] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    15.494] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    15.494] (--) NVIDIA(0): Connected display device(s) on GeForce 210 at PCI:2:0:0
[    15.494] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[    15.494] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    15.494] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    15.563] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    15.563] (==) NVIDIA(0): 
[    15.563] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    15.563] (==) NVIDIA(0):     will be used as the requested mode.
[    15.563] (==) NVIDIA(0): 
[    15.563] (II) NVIDIA(0): Validated modes:
[    15.563] (II) NVIDIA(0):     "nvidia-auto-select"
[    15.563] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    15.598] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    15.598] (--) NVIDIA(0):     option
[    15.599] (II) UnloadModule: "nouveau"
[    15.599] (II) Unloading nouveau
[    15.599] (II) UnloadModule: "vesa"
[    15.599] (II) Unloading vesa
[    15.599] (II) UnloadModule: "fbdev"
[    15.599] (II) Unloading fbdev
[    15.599] (II) UnloadModule: "fbdevhw"
[    15.599] (II) Unloading fbdevhw
[    15.599] (--) Depth 24 pixmap format is 32 bpp
[    15.599] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    15.604] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    15.628] (II) Loading extension NV-GLX
[    15.665] (==) NVIDIA(0): Disabling shared memory pixmaps
[    15.665] (==) NVIDIA(0): Backing store disabled
[    15.665] (==) NVIDIA(0): Silken mouse enabled
[    15.666] (==) NVIDIA(0): DPMS enabled
[    15.666] (II) Loading extension NV-CONTROL
[    15.666] (II) Loading extension XINERAMA
[    15.666] (II) Loading sub module "dri2"
[    15.666] (II) LoadModule: "dri2"
[    15.666] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.667] (II) Module dri2: vendor="X.Org Foundation"
[    15.667] 	compiled for 1.10.1, module version = 1.2.0
[    15.667] 	ABI class: X.Org Server Extension, version 5.0
[    15.667] (II) NVIDIA(0): [DRI2] Setup complete
[    15.667] (==) RandR enabled
[    15.667] (II) Initializing built-in extension Generic Event Extension
[    15.667] (II) Initializing built-in extension SHAPE
[    15.667] (II) Initializing built-in extension MIT-SHM
[    15.667] (II) Initializing built-in extension XInputExtension
[    15.667] (II) Initializing built-in extension XTEST
[    15.667] (II) Initializing built-in extension BIG-REQUESTS
[    15.667] (II) Initializing built-in extension SYNC
[    15.667] (II) Initializing built-in extension XKEYBOARD
[    15.667] (II) Initializing built-in extension XC-MISC
[    15.667] (II) Initializing built-in extension SECURITY
[    15.667] (II) Initializing built-in extension XINERAMA
[    15.667] (II) Initializing built-in extension XFIXES
[    15.667] (II) Initializing built-in extension RENDER
[    15.667] (II) Initializing built-in extension RANDR
[    15.667] (II) Initializing built-in extension COMPOSITE
[    15.667] (II) Initializing built-in extension DAMAGE
[    15.667] (II) Initializing built-in extension GESTURE
[    15.669] (II) Initializing extension GLX
[    15.692] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.701] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.701] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.701] (II) LoadModule: "evdev"
[    15.701] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.702] (II) Module evdev: vendor="X.Org Foundation"
[    15.702] 	compiled for 1.10.0.902, module version = 2.6.0
[    15.702] 	Module class: X.Org XInput Driver
[    15.702] 	ABI class: X.Org XInput driver, version 12.3
[    15.702] (II) Using input driver 'evdev' for 'Power Button'
[    15.702] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.702] (**) Power Button: always reports core events
[    15.702] (**) Power Button: Device: "/dev/input/event1"
[    15.750] (--) Power Button: Found keys
[    15.750] (II) Power Button: Configuring as keyboard
[    15.750] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.750] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.750] (**) Option "xkb_rules" "evdev"
[    15.750] (**) Option "xkb_model" "pc105"
[    15.750] (**) Option "xkb_layout" "us"
[    15.753] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.753] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.753] (II) Using input driver 'evdev' for 'Power Button'
[    15.753] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.753] (**) Power Button: always reports core events
[    15.753] (**) Power Button: Device: "/dev/input/event0"
[    15.780] (--) Power Button: Found keys
[    15.780] (II) Power Button: Configuring as keyboard
[    15.780] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.780] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.780] (**) Option "xkb_rules" "evdev"
[    15.780] (**) Option "xkb_model" "pc105"
[    15.780] (**) Option "xkb_layout" "us"
[    15.787] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    15.787] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.787] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.787] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.787] (**) AT Translated Set 2 keyboard: always reports core events
[    15.787] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    15.840] (--) AT Translated Set 2 keyboard: Found keys
[    15.840] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    15.840] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    15.840] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    15.840] (**) Option "xkb_rules" "evdev"
[    15.840] (**) Option "xkb_model" "pc105"
[    15.840] (**) Option "xkb_layout" "us"
[   167.813] (II) config/udev: Adding input device HP HP Wireless 3 Button Mouse (/dev/input/event3)
[   167.813] (**) HP HP Wireless 3 Button Mouse: Applying InputClass "evdev pointer catchall"
[   167.813] (II) Using input driver 'evdev' for 'HP HP Wireless 3 Button Mouse'
[   167.813] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   167.814] (**) HP HP Wireless 3 Button Mouse: always reports core events
[   167.814] (**) HP HP Wireless 3 Button Mouse: Device: "/dev/input/event3"
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found 3 mouse buttons
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found scroll wheel(s)
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found relative axes
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found x and y relative axes
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found absolute axes
[   167.860] (II) evdev-grail: failed to open grail, no gesture support
[   167.860] (II) HP HP Wireless 3 Button Mouse: Configuring as mouse
[   167.860] (II) HP HP Wireless 3 Button Mouse: Adding scrollwheel support
[   167.860] (**) HP HP Wireless 3 Button Mouse: YAxisMapping: buttons 4 and 5
[   167.860] (**) HP HP Wireless 3 Button Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   167.860] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input3/event3"
[   167.860] (II) XINPUT: Adding extended input device "HP HP Wireless 3 Button Mouse" (type: MOUSE)
[   167.861] (II) HP HP Wireless 3 Button Mouse: initialized for relative axes.
[   167.861] (WW) HP HP Wireless 3 Button Mouse: ignoring absolute axes.
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) keeping acceleration scheme 1
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration profile 0
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration factor: 2.000
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration threshold: 4
[   167.862] (II) config/udev: Adding input device HP HP Wireless 3 Button Mouse (/dev/input/mouse0)
[   167.862] (II) No input driver/identifier specified (ignoring)

```

Notice the 150+ seconds it takes to configure the mouse!!!

Please help. :KS

---

### Post by Derek Karpinski on 2011-04-30
Even swapping the port the USB receiver is plugged into has no effect.

Strange thing though, after the mouse starts working, I can unplug the receiver, and plug it back in, and the Xorg.0.log shows almost no delay on configuring the mouse.

Xorg.0.log:
```
[   167.815] (II) config/udev: Adding input device HP HP Wireless 3 Button Mouse (/dev/input/event3)
[   167.815] (**) HP HP Wireless 3 Button Mouse: Applying InputClass "evdev pointer catchall"
[   167.815] (II) Using input driver 'evdev' for 'HP HP Wireless 3 Button Mouse'
[   167.815] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   167.815] (**) HP HP Wireless 3 Button Mouse: always reports core events
[   167.815] (**) HP HP Wireless 3 Button Mouse: Device: "/dev/input/event3"
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found 3 mouse buttons
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found scroll wheel(s)
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found relative axes
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found x and y relative axes
[   167.860] (--) HP HP Wireless 3 Button Mouse: Found absolute axes
[   167.860] (II) evdev-grail: failed to open grail, no gesture support
[   167.860] (II) HP HP Wireless 3 Button Mouse: Configuring as mouse
[   167.860] (II) HP HP Wireless 3 Button Mouse: Adding scrollwheel support
[   167.861] (**) HP HP Wireless 3 Button Mouse: YAxisMapping: buttons 4 and 5
[   167.861] (**) HP HP Wireless 3 Button Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   167.861] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input3/event3"
[   167.861] (II) XINPUT: Adding extended input device "HP HP Wireless 3 Button Mouse" (type: MOUSE)
[   167.861] (II) HP HP Wireless 3 Button Mouse: initialized for relative axes.
[   167.861] (WW) HP HP Wireless 3 Button Mouse: ignoring absolute axes.
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) keeping acceleration scheme 1
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration profile 0
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration factor: 2.000
[   167.861] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration threshold: 4
[   167.862] (II) config/udev: Adding input device HP HP Wireless 3 Button Mouse (/dev/input/mouse0)
[   167.863] (II) No input driver/identifier specified (ignoring)
[   347.160] (II) config/udev: removing device HP HP Wireless 3 Button Mouse
[   347.161] (II) HP HP Wireless 3 Button Mouse: Close
[   347.161] (II) UnloadModule: "evdev"
[   347.161] (II) Unloading evdev
[   354.405] (II) config/udev: Adding input device HP HP Wireless 3 Button Mouse (/dev/input/mouse0)
[   354.406] (II) No input driver/identifier specified (ignoring)
[   354.408] (II) config/udev: Adding input device HP HP Wireless 3 Button Mouse (/dev/input/event3)
[   354.408] (**) HP HP Wireless 3 Button Mouse: Applying InputClass "evdev pointer catchall"
[   354.408] (II) Using input driver 'evdev' for 'HP HP Wireless 3 Button Mouse'
[   354.408] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   354.408] (**) HP HP Wireless 3 Button Mouse: always reports core events
[   354.408] (**) HP HP Wireless 3 Button Mouse: Device: "/dev/input/event3"
[   354.450] (--) HP HP Wireless 3 Button Mouse: Found 3 mouse buttons
[   354.450] (--) HP HP Wireless 3 Button Mouse: Found scroll wheel(s)
[   354.450] (--) HP HP Wireless 3 Button Mouse: Found relative axes
[   354.450] (--) HP HP Wireless 3 Button Mouse: Found x and y relative axes
[   354.450] (--) HP HP Wireless 3 Button Mouse: Found absolute axes
[   354.450] (II) evdev-grail: failed to open grail, no gesture support
[   354.450] (II) HP HP Wireless 3 Button Mouse: Configuring as mouse
[   354.450] (II) HP HP Wireless 3 Button Mouse: Adding scrollwheel support
[   354.450] (**) HP HP Wireless 3 Button Mouse: YAxisMapping: buttons 4 and 5
[   354.450] (**) HP HP Wireless 3 Button Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   354.451] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input4/event3"
[   354.451] (II) XINPUT: Adding extended input device "HP HP Wireless 3 Button Mouse" (type: MOUSE)
[   354.451] (II) HP HP Wireless 3 Button Mouse: initialized for relative axes.
[   354.451] (WW) HP HP Wireless 3 Button Mouse: ignoring absolute axes.
[   354.451] (**) HP HP Wireless 3 Button Mouse: (accel) keeping acceleration scheme 1
[   354.451] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration profile 0
[   354.451] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration factor: 2.000
[   354.451] (**) HP HP Wireless 3 Button Mouse: (accel) acceleration threshold: 4

```

Note, at [   347.160] I unplugged the receiver.

at [   354.405] I plugged it back in and we're off and running in 50msec.

What is hanging this up at boot time?:confused:

---

### Post by Derek Karpinski on 2011-04-30
Even a bootchart doesn't show any unnecessary delays:

[IMG]http://img3.imageshack.us/i/homepcnatty201104301.png/[/IMG]

---

### Post by Derek Karpinski on 2011-05-01
Not really 'solved' but reinstalling (for the 4th time) fixed everything.

I'm afraid to try mounting anything or adding any software for fear of breaking such a fragile install.

---

### Post by Derek Karpinski on 2011-05-09
Okay..............it's back (or was)

I've been trying to get my machine to resume from suspend with no luck.  The last thing I tried was adding 'nomodeset' to the grub kernel options. After a grub-update2 and reboot, I pressed the sleep button on my keyboard.  It went to sleep, but no resume.....just like always.  So I hard reset it by holding in the power button.

On reboot, I'm getting all kinds of errors about my external drive not being ready to be mounted.  I press 'S' for skip on the 2 errors there.  Then the GDM screen comes up, and no mouse!  I'm freaking, because I don't want to reinstall everything.  I edit the grub file and remove 'nomodeset', update grub, and reboot.  Same thing, but this time more errors about not being able to mount my swap (I have an encrypted home).  ****.....wait, log in, reboot........same thing.  Now errors about .ICEauthority or something, and no GDM screen, couldn't make my home directory.  Unplugged the external drive, booted into safe mode and watched the error messages.  The USB was having all kinds of errors for 150+ seconds.

Reboot from command line, start windows vista.  Blank screen, no windows.  Hard reset. Everything plugged in, Vista again, it fires up no prob, browse to external drive, use mouse right away, reboot again.  Back into Ubuntu, and everything seems to be working great.

So, I'm trying to figure out what the hell is going on so I don't do it again.  My fiance would leave me if I had to ask her to set up her Ubuntu password again, and frankly I don't blame her, its half the reason we just bought her a laptop.

So, does anyone have any ideas?  Is it a sleep thing? Don't mess around with fstab thing?  HELP!!!!!!

---

