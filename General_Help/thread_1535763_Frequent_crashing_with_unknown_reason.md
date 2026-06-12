---
title: "Frequent crashing with unknown reason"
date: 2010-07-21
forum: General Help
---

### Post by thankqwerty on 2010-07-21
Hi all,

I have just installed Ubuntu 10.04 on my machine, and it crashes 3-4 a day ever since. My computer previously runs fine on XP and Ubuntu 8.04 (or something).

I can't really work out a pattern of the cause of the crashes. I don't really know what I should do.

Here is part of the file "/var/log/messages" (since the last crash).

```

Jul 21 11:01:48 lui-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 21 11:01:48 lui-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="709" x-info="http://www.rsyslog.com"] (re)start
Jul 21 11:01:48 lui-desktop rsyslogd: rsyslogd's groupid changed to 103
Jul 21 11:01:48 lui-desktop rsyslogd: rsyslogd's userid changed to 101
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Linux version 2.6.32-23-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=74772b9c-e1a4-4757-9cb9-3bdf5e5f9e6d ro quiet splash
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] KERNEL supported cpus:
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   Intel GenuineIntel
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] DMI 2.4 present.
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] last_pfn = 0x7ffa0 max_arch_pfn = 0x400000000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] modified physical RAM map:
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000007ffa0000 (usable)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 000000007ffa0000 - 000000007ffae000 (ACPI data)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 000000007ffe0000 - 0000000080000000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007ffa0000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] RAMDISK: 377f8000 - 37fef371
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: RSDP 00000000000fa980 00014 (v00 ACPIAM)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: RSDT 000000007ffa0000 00038 (v01 A M I  OEMRSDT  10000626 MSFT 00000097)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: FACP 000000007ffa0200 00084 (v02 A M I  OEMFACP  10000626 MSFT 00000097)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: DSDT 000000007ffa0440 08A52 (v01  A0545 A0545000 00000000 INTL 20060113)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: FACS 000000007ffae000 00040
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: APIC 000000007ffa0390 0006C (v01 A M I  OEMAPIC  10000626 MSFT 00000097)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: MCFG 000000007ffa0400 0003C (v01 A M I  OEMMCFG  10000626 MSFT 00000097)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: OEMB 000000007ffae040 0007B (v01 A M I  AMI_OEM  10000626 MSFT 00000097)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: HPET 000000007ffa8ea0 00038 (v01 A M I  OEMHPET  10000626 MSFT 00000097)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] No NUMA configuration found
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Faking a node at 0000000000000000-000000007ffa0000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007ffa0000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000026ff7] pages 10
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007ffa0000]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a2de64]    TEXT DATA BSS ==> [0001000000 - 0001a2de64]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #3 [00377f8000 - 0037fef371]          RAMDISK ==> [00377f8000 - 0037fef371]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #5 [0001a2e000 - 0001a2e288]              BRK ==> [0001a2e000 - 0001a2e288]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 21 11:01:48 lui-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007ffa0
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516811
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Policy zone: DMA32
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=74772b9c-e1a4-4757-9cb9-3bdf5e5f9e6d ro quiet splash
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Initializing CPU#0
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Checking aperture...
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] No AGP bridge found
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Memory: 2048412k/2096768k available (5419k kernel code, 452k absent, 47904k reserved, 2974k data, 880k init)
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] console [tty0] enabled
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 21 11:01:48 lui-desktop kernel: [    0.000000] Detected 2135.075 MHz processor.
Jul 21 11:01:48 lui-desktop kernel: [    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4270.15 BogoMIPS (lpj=21350750)
Jul 21 11:01:48 lui-desktop kernel: [    0.000035] Security Framework initialized
Jul 21 11:01:48 lui-desktop kernel: [    0.000055] AppArmor: AppArmor initialized
Jul 21 11:01:48 lui-desktop kernel: [    0.010171] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    0.011215] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    0.011693] Mount-cache hash table entries: 256
Jul 21 11:01:48 lui-desktop kernel: [    0.011837] Initializing cgroup subsys ns
Jul 21 11:01:48 lui-desktop kernel: [    0.011843] Initializing cgroup subsys cpuacct
Jul 21 11:01:48 lui-desktop kernel: [    0.011847] Initializing cgroup subsys memory
Jul 21 11:01:48 lui-desktop kernel: [    0.011854] Initializing cgroup subsys devices
Jul 21 11:01:48 lui-desktop kernel: [    0.011856] Initializing cgroup subsys freezer
Jul 21 11:01:48 lui-desktop kernel: [    0.011858] Initializing cgroup subsys net_cls
Jul 21 11:01:48 lui-desktop kernel: [    0.011879] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 21 11:01:48 lui-desktop kernel: [    0.011882] CPU: L2 cache: 2048K
Jul 21 11:01:48 lui-desktop kernel: [    0.011885] CPU 0/0x0 -> Node 0
Jul 21 11:01:48 lui-desktop kernel: [    0.011887] CPU: Physical Processor ID: 0
Jul 21 11:01:48 lui-desktop kernel: [    0.011889] CPU: Processor Core ID: 0
Jul 21 11:01:48 lui-desktop kernel: [    0.011892] mce: CPU supports 6 MCE banks
Jul 21 11:01:48 lui-desktop kernel: [    0.011900] CPU0: Thermal monitoring enabled (TM2)
Jul 21 11:01:48 lui-desktop kernel: [    0.011905] using mwait in idle threads.
Jul 21 11:01:48 lui-desktop kernel: [    0.011907] Performance Events: Core2 events, Intel PMU driver.
Jul 21 11:01:48 lui-desktop kernel: [    0.011913] ... version:                2
Jul 21 11:01:48 lui-desktop kernel: [    0.011914] ... bit width:              40
Jul 21 11:01:48 lui-desktop kernel: [    0.011916] ... generic registers:      2
Jul 21 11:01:48 lui-desktop kernel: [    0.011918] ... value mask:             000000ffffffffff
Jul 21 11:01:48 lui-desktop kernel: [    0.011919] ... max period:             000000007fffffff
Jul 21 11:01:48 lui-desktop kernel: [    0.011921] ... fixed-purpose events:   3
Jul 21 11:01:48 lui-desktop kernel: [    0.011923] ... event mask:             0000000700000003
Jul 21 11:01:48 lui-desktop kernel: [    0.014394] ACPI: Core revision 20090903
Jul 21 11:01:48 lui-desktop kernel: [    0.030007] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 21 11:01:48 lui-desktop kernel: [    0.030015] ftrace: allocating 22524 entries in 89 pages
Jul 21 11:01:48 lui-desktop kernel: [    0.040056] Setting APIC routing to flat
Jul 21 11:01:48 lui-desktop kernel: [    0.040360] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 21 11:01:48 lui-desktop kernel: [    0.141198] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
Jul 21 11:01:48 lui-desktop kernel: [    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] Initializing CPU#1
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] CPU: L2 cache: 2048K
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] CPU 1/0x1 -> Node 0
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] CPU: Physical Processor ID: 0
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] CPU: Processor Core ID: 1
Jul 21 11:01:48 lui-desktop kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Jul 21 11:01:48 lui-desktop kernel: [    0.300113] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
Jul 21 11:01:48 lui-desktop kernel: [    0.300120] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 21 11:01:48 lui-desktop kernel: [    0.310016] Brought up 2 CPUs
Jul 21 11:01:48 lui-desktop kernel: [    0.310019] Total of 2 processors activated (8540.23 BogoMIPS).
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] devtmpfs: initialized
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] regulator: core version 0.5
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] Time: 10:01:34  Date: 07/21/10
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] NET: Registered protocol family 16
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] Trying to unpack rootfs image as initramfs...
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] ACPI: bus type pci registered
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] PCI: Not using MMCONFIG.
Jul 21 11:01:48 lui-desktop kernel: [    0.310523] PCI: Using configuration type 1 for base access
Jul 21 11:01:48 lui-desktop kernel: [    0.320147] bio: create slab <bio-0> at 0
Jul 21 11:01:48 lui-desktop kernel: [    0.323917] ACPI: Executed 1 blocks of module-level executable AML code
Jul 21 11:01:48 lui-desktop kernel: [    0.331138] ACPI: Interpreter enabled
Jul 21 11:01:48 lui-desktop kernel: [    0.331145] ACPI: (supports S0 S1 S3 S4 S5)
Jul 21 11:01:48 lui-desktop kernel: [    0.331170] ACPI: Using IOAPIC for interrupt routing
Jul 21 11:01:48 lui-desktop kernel: [    0.331227] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 21 11:01:48 lui-desktop kernel: [    0.334319] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jul 21 11:01:48 lui-desktop kernel: [    0.337106] PCI: Using MMCONFIG at e0000000 - efffffff
Jul 21 11:01:48 lui-desktop kernel: [    0.346011] ACPI Warning: Incorrect checksum in table [OEMB] - 85, should be 78 (20090903/tbutils-314)
Jul 21 11:01:48 lui-desktop kernel: [    0.346144] ACPI: No dock devices found.
Jul 21 11:01:48 lui-desktop kernel: [    0.346260] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 21 11:01:48 lui-desktop kernel: [    0.346370] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.346374] pci 0000:00:01.0: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.346579] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.346583] pci 0000:00:1a.7: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.346659] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.346663] pci 0000:00:1b.0: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.346720] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.346724] pci 0000:00:1c.0: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.346785] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.346789] pci 0000:00:1c.3: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.346849] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.346852] pci 0000:00:1c.4: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.347089] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.347093] pci 0000:00:1d.7: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.347210] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Jul 21 11:01:48 lui-desktop kernel: [    0.347214] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Jul 21 11:01:48 lui-desktop kernel: [    0.347218] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
Jul 21 11:01:48 lui-desktop kernel: [    0.347310] pci 0000:00:1f.2: PME# supported from D3hot
Jul 21 11:01:48 lui-desktop kernel: [    0.347314] pci 0000:00:1f.2: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.347433] pci 0000:00:1f.5: PME# supported from D3hot
Jul 21 11:01:48 lui-desktop kernel: [    0.347436] pci 0000:00:1f.5: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.347824] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
Jul 21 11:01:48 lui-desktop kernel: [    0.347829] pci 0000:03:00.0: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.348013] pci 0000:02:00.0: PME# supported from D3hot
Jul 21 11:01:48 lui-desktop kernel: [    0.348018] pci 0000:02:00.0: PME# disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.348244] pci 0000:00:1e.0: transparent bridge
Jul 21 11:01:48 lui-desktop kernel: [    0.363226] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jul 21 11:01:48 lui-desktop kernel: [    0.363342] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 21 11:01:48 lui-desktop kernel: [    0.363455] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Jul 21 11:01:48 lui-desktop kernel: [    0.363567] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 21 11:01:48 lui-desktop kernel: [    0.363678] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 21 11:01:48 lui-desktop kernel: [    0.363791] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 21 11:01:48 lui-desktop kernel: [    0.363904] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jul 21 11:01:48 lui-desktop kernel: [    0.364015] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Jul 21 11:01:48 lui-desktop kernel: [    0.364143] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 21 11:01:48 lui-desktop kernel: [    0.364148] vgaarb: loaded
Jul 21 11:01:48 lui-desktop kernel: [    0.364262] SCSI subsystem initialized
Jul 21 11:01:48 lui-desktop kernel: [    0.364423] usbcore: registered new interface driver usbfs
Jul 21 11:01:48 lui-desktop kernel: [    0.364434] usbcore: registered new interface driver hub
Jul 21 11:01:48 lui-desktop kernel: [    0.364459] usbcore: registered new device driver usb
Jul 21 11:01:48 lui-desktop kernel: [    0.364595] ACPI: WMI: Mapper loaded
Jul 21 11:01:48 lui-desktop kernel: [    0.364597] PCI: Using ACPI for IRQ routing
Jul 21 11:01:48 lui-desktop kernel: [    0.364769] NetLabel: Initializing
Jul 21 11:01:48 lui-desktop kernel: [    0.364771] NetLabel:  domain hash size = 128
Jul 21 11:01:48 lui-desktop kernel: [    0.364773] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 21 11:01:48 lui-desktop kernel: [    0.364786] NetLabel:  unlabeled traffic allowed by default
Jul 21 11:01:48 lui-desktop kernel: [    0.364820] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 21 11:01:48 lui-desktop kernel: [    0.364825] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 21 11:01:48 lui-desktop kernel: [    0.370240] Switching to clocksource tsc
Jul 21 11:01:48 lui-desktop kernel: [    0.371794] AppArmor: AppArmor Filesystem Enabled
Jul 21 11:01:48 lui-desktop kernel: [    0.371813] pnp: PnP ACPI init
Jul 21 11:01:48 lui-desktop kernel: [    0.371833] ACPI: bus type pnp registered
Jul 21 11:01:48 lui-desktop kernel: [    0.375906] pnp: PnP ACPI: found 16 devices
Jul 21 11:01:48 lui-desktop kernel: [    0.375909] ACPI: ACPI bus type pnp unregistered
Jul 21 11:01:48 lui-desktop kernel: [    0.375921] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375930] system 00:08: ioport range 0x290-0x297 has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375936] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375939] system 00:09: ioport range 0x800-0x87f has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375942] system 00:09: ioport range 0x480-0x4bf has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375945] system 00:09: iomem range 0xffafe000-0xffb0cbff could not be reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375948] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375950] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375953] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375956] system 00:09: iomem range 0xfff00000-0xfffffffe has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375962] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375965] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375971] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375977] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375979] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375982] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.375985] system 00:0f: iomem range 0x100000-0x7fffffff could not be reserved
Jul 21 11:01:48 lui-desktop kernel: [    0.380744] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jul 21 11:01:48 lui-desktop kernel: [    0.380747] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
Jul 21 11:01:48 lui-desktop kernel: [    0.380751] pci 0000:00:01.0:   MEM window: 0xfc700000-0xfe8fffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380755] pci 0000:00:01.0:   PREFETCH window: 0x000000bbe00000-0x000000dfdfffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380759] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
Jul 21 11:01:48 lui-desktop kernel: [    0.380762] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Jul 21 11:01:48 lui-desktop kernel: [    0.380767] pci 0000:00:1c.0:   MEM window: 0x80000000-0x803fffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380770] pci 0000:00:1c.0:   PREFETCH window: 0x000000dfe00000-0x000000dfefffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380776] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
Jul 21 11:01:48 lui-desktop kernel: [    0.380779] pci 0000:00:1c.3:   IO window: 0xb000-0xbfff
Jul 21 11:01:48 lui-desktop kernel: [    0.380784] pci 0000:00:1c.3:   MEM window: 0xfea00000-0xfeafffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380787] pci 0000:00:1c.3:   PREFETCH window: 0x00000080400000-0x000000805fffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380793] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
Jul 21 11:01:48 lui-desktop kernel: [    0.380796] pci 0000:00:1c.4:   IO window: 0xa000-0xafff
Jul 21 11:01:48 lui-desktop kernel: [    0.380801] pci 0000:00:1c.4:   MEM window: 0xfe900000-0xfe9fffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380804] pci 0000:00:1c.4:   PREFETCH window: 0x00000080600000-0x000000807fffff
Jul 21 11:01:48 lui-desktop kernel: [    0.380810] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Jul 21 11:01:48 lui-desktop kernel: [    0.380812] pci 0000:00:1e.0:   IO window: disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.380816] pci 0000:00:1e.0:   MEM window: disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.380819] pci 0000:00:1e.0:   PREFETCH window: disabled
Jul 21 11:01:48 lui-desktop kernel: [    0.380841] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:48 lui-desktop kernel: [    0.380852] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Jul 21 11:01:48 lui-desktop kernel: [    0.380855] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:48 lui-desktop kernel: [    0.380871] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul 21 11:01:48 lui-desktop kernel: [    0.380883] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:48 lui-desktop kernel: [    0.380969] NET: Registered protocol family 2
Jul 21 11:01:48 lui-desktop kernel: [    0.381105] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    0.381821] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    0.383811] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    0.384336] TCP: Hash tables configured (established 262144 bind 65536)
Jul 21 11:01:48 lui-desktop kernel: [    0.384339] TCP reno registered
Jul 21 11:01:48 lui-desktop kernel: [    0.384467] NET: Registered protocol family 1
Jul 21 11:01:48 lui-desktop kernel: [    1.339706] Scanning for low memory corruption every 60 seconds
Jul 21 11:01:48 lui-desktop kernel: [    1.339837] audit: initializing netlink socket (disabled)
Jul 21 11:01:48 lui-desktop kernel: [    1.339851] type=2000 audit(1279706494.339:1): initialized
Jul 21 11:01:48 lui-desktop kernel: [    1.349265] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 21 11:01:48 lui-desktop kernel: [    1.350677] VFS: Disk quotas dquot_6.5.2
Jul 21 11:01:48 lui-desktop kernel: [    1.350729] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 21 11:01:48 lui-desktop kernel: [    1.351323] fuse init (API version 7.13)
Jul 21 11:01:48 lui-desktop kernel: [    1.351402] msgmni has been set to 4000
Jul 21 11:01:48 lui-desktop kernel: [    1.351612] alg: No test for stdrng (krng)
Jul 21 11:01:48 lui-desktop kernel: [    1.351666] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 21 11:01:48 lui-desktop kernel: [    1.351669] io scheduler noop registered
Jul 21 11:01:48 lui-desktop kernel: [    1.351671] io scheduler anticipatory registered
Jul 21 11:01:48 lui-desktop kernel: [    1.351673] io scheduler deadline registered
Jul 21 11:01:48 lui-desktop kernel: [    1.351705] io scheduler cfq registered (default)
Jul 21 11:01:48 lui-desktop kernel: [    1.352286] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 21 11:01:48 lui-desktop kernel: [    1.352385] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 21 11:01:48 lui-desktop kernel: [    1.352493] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 21 11:01:48 lui-desktop kernel: [    1.352497] ACPI: Power Button [PWRB]
Jul 21 11:01:48 lui-desktop kernel: [    1.352543] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 21 11:01:48 lui-desktop kernel: [    1.352546] ACPI: Power Button [PWRF]
Jul 21 11:01:48 lui-desktop kernel: [    1.353004] ACPI Warning: Incorrect checksum in table [SSDT] - 34, should be 3B (20090903/tbutils-314)
Jul 21 11:01:48 lui-desktop kernel: [    1.353011] ACPI: SSDT 000000007ffa8ee0 002E3 (v01    AMI   CPU1PM 00000001 INTL 20060113)
Jul 21 11:01:48 lui-desktop kernel: [    1.353282] processor LNXCPU:00: registered as cooling_device0
Jul 21 11:01:48 lui-desktop kernel: [    1.353419] ACPI: SSDT 000000007ffa91d0 002DA (v01    AMI   CPU2PM 00000001 INTL 20060113)
Jul 21 11:01:48 lui-desktop kernel: [    1.353675] processor LNXCPU:01: registered as cooling_device1
Jul 21 11:01:48 lui-desktop kernel: [    1.357956] Linux agpgart interface v0.103
Jul 21 11:01:48 lui-desktop kernel: [    1.357994] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 21 11:01:48 lui-desktop kernel: [    1.358088] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 21 11:01:48 lui-desktop kernel: [    1.358381] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 21 11:01:48 lui-desktop kernel: [    1.359511] brd: module loaded
Jul 21 11:01:48 lui-desktop kernel: [    1.359985] loop: module loaded
Jul 21 11:01:48 lui-desktop kernel: [    1.360067] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 21 11:01:48 lui-desktop kernel: [    1.360181] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 21 11:01:48 lui-desktop kernel: [    1.360186] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jul 21 11:01:48 lui-desktop kernel: [    1.425657] Freeing initrd memory: 8156k freed
Jul 21 11:01:48 lui-desktop kernel: [    1.519707] scsi0 : ata_piix
Jul 21 11:01:48 lui-desktop kernel: [    1.519846] scsi1 : ata_piix
Jul 21 11:01:48 lui-desktop kernel: [    1.521643] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 19
Jul 21 11:01:48 lui-desktop kernel: [    1.521648] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 19
Jul 21 11:01:48 lui-desktop kernel: [    1.521703] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 21 11:01:48 lui-desktop kernel: [    1.521708] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jul 21 11:01:48 lui-desktop kernel: [    1.521785] scsi2 : ata_piix
Jul 21 11:01:48 lui-desktop kernel: [    1.521840] scsi3 : ata_piix
Jul 21 11:01:48 lui-desktop kernel: [    1.523043] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 19
Jul 21 11:01:48 lui-desktop kernel: [    1.523047] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 19
Jul 21 11:01:48 lui-desktop kernel: [    1.523149] pata_acpi 0000:02:00.1: enabling device (0000 -> 0001)
Jul 21 11:01:48 lui-desktop kernel: [    1.523164] pata_acpi 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 21 11:01:48 lui-desktop kernel: [    1.523209] pata_acpi 0000:02:00.1: PCI INT B disabled
Jul 21 11:01:48 lui-desktop kernel: [    1.523492] Fixed MDIO Bus: probed
Jul 21 11:01:48 lui-desktop kernel: [    1.523524] PPP generic driver version 2.4.2
Jul 21 11:01:48 lui-desktop kernel: [    1.523585] tun: Universal TUN/TAP device driver, 1.6
Jul 21 11:01:48 lui-desktop kernel: [    1.523587] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 21 11:01:48 lui-desktop kernel: [    1.523683] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 21 11:01:48 lui-desktop kernel: [    1.523705] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 21 11:01:48 lui-desktop kernel: [    1.523723] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.523756] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jul 21 11:01:48 lui-desktop kernel: [    1.523783] ehci_hcd 0000:00:1a.7: debug port 1
Jul 21 11:01:48 lui-desktop kernel: [    1.527674] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfebffc00
Jul 21 11:01:48 lui-desktop kernel: [    1.549604] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jul 21 11:01:48 lui-desktop kernel: [    1.549705] usb usb1: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.549740] hub 1-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.549748] hub 1-0:1.0: 4 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.549820] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul 21 11:01:48 lui-desktop kernel: [    1.549835] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.549880] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jul 21 11:01:48 lui-desktop kernel: [    1.549904] ehci_hcd 0000:00:1d.7: debug port 1
Jul 21 11:01:48 lui-desktop kernel: [    1.553796] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff800
Jul 21 11:01:48 lui-desktop kernel: [    1.569643] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 21 11:01:48 lui-desktop kernel: [    1.569737] usb usb2: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.569770] hub 2-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.569777] hub 2-0:1.0: 6 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.569844] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 21 11:01:48 lui-desktop kernel: [    1.569862] uhci_hcd: USB Universal Host Controller Interface driver
Jul 21 11:01:48 lui-desktop kernel: [    1.569895] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:48 lui-desktop kernel: [    1.569904] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.569934] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jul 21 11:01:48 lui-desktop kernel: [    1.569961] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
Jul 21 11:01:48 lui-desktop kernel: [    1.570045] usb usb3: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.570069] hub 3-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.570074] hub 3-0:1.0: 2 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.570118] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 21 11:01:48 lui-desktop kernel: [    1.570128] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.570158] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jul 21 11:01:48 lui-desktop kernel: [    1.570185] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000e000
Jul 21 11:01:48 lui-desktop kernel: [    1.570267] usb usb4: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.570291] hub 4-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.570296] hub 4-0:1.0: 2 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.570336] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul 21 11:01:48 lui-desktop kernel: [    1.570344] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.570384] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jul 21 11:01:48 lui-desktop kernel: [    1.570407] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d480
Jul 21 11:01:48 lui-desktop kernel: [    1.570486] usb usb5: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.570513] hub 5-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.570518] hub 5-0:1.0: 2 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.570557] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 21 11:01:48 lui-desktop kernel: [    1.570565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.570605] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jul 21 11:01:48 lui-desktop kernel: [    1.570626] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
Jul 21 11:01:48 lui-desktop kernel: [    1.570714] usb usb6: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.570742] hub 6-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.570748] hub 6-0:1.0: 2 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.570786] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 21 11:01:48 lui-desktop kernel: [    1.570794] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 21 11:01:48 lui-desktop kernel: [    1.570824] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jul 21 11:01:48 lui-desktop kernel: [    1.570845] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d880
Jul 21 11:01:48 lui-desktop kernel: [    1.570923] usb usb7: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    1.570947] hub 7-0:1.0: USB hub found
Jul 21 11:01:48 lui-desktop kernel: [    1.570953] hub 7-0:1.0: 2 ports detected
Jul 21 11:01:48 lui-desktop kernel: [    1.571040] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 21 11:01:48 lui-desktop kernel: [    1.571042] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul 21 11:01:48 lui-desktop kernel: [    1.571517] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 21 11:01:48 lui-desktop kernel: [    1.571618] mice: PS/2 mouse device common for all mice
Jul 21 11:01:48 lui-desktop kernel: [    1.571722] rtc_cmos 00:03: RTC can wake from S4
Jul 21 11:01:48 lui-desktop kernel: [    1.571759] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 21 11:01:48 lui-desktop kernel: [    1.571781] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul 21 11:01:48 lui-desktop kernel: [    1.571896] device-mapper: uevent: version 1.0.3
Jul 21 11:01:48 lui-desktop kernel: [    1.571993] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 21 11:01:48 lui-desktop kernel: [    1.572058] device-mapper: multipath: version 1.1.0 loaded
Jul 21 11:01:48 lui-desktop kernel: [    1.572061] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 21 11:01:48 lui-desktop kernel: [    1.572206] cpuidle: using governor ladder
Jul 21 11:01:48 lui-desktop kernel: [    1.572208] cpuidle: using governor menu
Jul 21 11:01:48 lui-desktop kernel: [    1.572530] TCP cubic registered
Jul 21 11:01:48 lui-desktop kernel: [    1.572644] NET: Registered protocol family 10
Jul 21 11:01:48 lui-desktop kernel: [    1.573065] lo: Disabled Privacy Extensions
Jul 21 11:01:48 lui-desktop kernel: [    1.573330] NET: Registered protocol family 17
Jul 21 11:01:48 lui-desktop kernel: [    1.573972] registered taskstats version 1
Jul 21 11:01:48 lui-desktop kernel: [    1.574346]   Magic number: 2:604:22
Jul 21 11:01:48 lui-desktop kernel: [    1.574418] rtc_cmos 00:03: setting system clock to 2010-07-21 10:01:35 UTC (1279706495)
Jul 21 11:01:48 lui-desktop kernel: [    1.574421] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 21 11:01:48 lui-desktop kernel: [    1.574423] EDD information not available.
Jul 21 11:01:48 lui-desktop kernel: [    1.594270] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 21 11:01:48 lui-desktop kernel: [    1.881100] ata3: SATA link down (SStatus 0 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    1.891771] ata4: SATA link down (SStatus 0 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.070754] ata2.00: SATA link down (SStatus 0 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.070766] ata2.01: SATA link down (SStatus 4 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.100041] usb 6-2: new low speed USB device using uhci_hcd and address 2
Jul 21 11:01:48 lui-desktop kernel: [    2.220754] ata1.00: SATA link down (SStatus 0 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.220766] ata1.01: SATA link down (SStatus 4 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.220809] Freeing unused kernel memory: 880k freed
Jul 21 11:01:48 lui-desktop kernel: [    2.221050] Write protecting the kernel read-only data: 7692k
Jul 21 11:01:48 lui-desktop kernel: [    2.235343] udev: starting version 151
Jul 21 11:01:48 lui-desktop kernel: [    2.284758] usb 6-2: configuration #1 chosen from 1 choice
Jul 21 11:01:48 lui-desktop kernel: [    2.289560] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 21 11:01:48 lui-desktop kernel: [    2.289580] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 21 11:01:48 lui-desktop kernel: [    2.290235] eth0: RTL8168b/8111b at 0xffffc9000034a000, 00:18:f3:0a:0f:fc, XID 18000000 IRQ 28
Jul 21 11:01:48 lui-desktop kernel: [    2.296590] ahci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:48 lui-desktop kernel: [    2.311657] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jul 21 11:01:48 lui-desktop kernel: [    2.311663] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Jul 21 11:01:48 lui-desktop kernel: [    2.321605] scsi4 : ahci
Jul 21 11:01:48 lui-desktop kernel: [    2.330925] Floppy drive(s): fd0 is 1.44M
Jul 21 11:01:48 lui-desktop kernel: [    2.333861] usbcore: registered new interface driver hiddev
Jul 21 11:01:48 lui-desktop kernel: [    2.335168] scsi5 : ahci
Jul 21 11:01:48 lui-desktop kernel: [    2.335289] ata5: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe100 irq 16
Jul 21 11:01:48 lui-desktop kernel: [    2.335293] ata6: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe180 irq 16
Jul 21 11:01:48 lui-desktop kernel: [    2.335345] pata_jmicron 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 21 11:01:48 lui-desktop kernel: [    2.342892] scsi6 : pata_jmicron
Jul 21 11:01:48 lui-desktop kernel: [    2.346216] scsi7 : pata_jmicron
Jul 21 11:01:48 lui-desktop kernel: [    2.346916] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input4
Jul 21 11:01:48 lui-desktop kernel: [    2.347009] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
Jul 21 11:01:48 lui-desktop kernel: [    2.347035] usbcore: registered new interface driver usbhid
Jul 21 11:01:48 lui-desktop kernel: [    2.347038] usbhid: v2.6:USB HID core driver
Jul 21 11:01:48 lui-desktop kernel: [    2.347049] ata7: PATA max UDMA/100 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 17
Jul 21 11:01:48 lui-desktop kernel: [    2.347053] ata8: PATA max UDMA/100 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 17
Jul 21 11:01:48 lui-desktop kernel: [    2.353733] FDC 0 is a post-1991 82077
Jul 21 11:01:48 lui-desktop kernel: [    2.520732] ata7.00: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
Jul 21 11:01:48 lui-desktop kernel: [    2.520736] ata7.00: 240121728 sectors, multi 0: LBA 
Jul 21 11:01:48 lui-desktop kernel: [    2.560731] ata7.00: configured for UDMA/100
Jul 21 11:01:48 lui-desktop kernel: [    2.680046] ata5: SATA link down (SStatus 0 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.680077] ata6: SATA link down (SStatus 0 SControl 300)
Jul 21 11:01:48 lui-desktop kernel: [    2.700166] scsi 6:0:0:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
Jul 21 11:01:48 lui-desktop kernel: [    2.700349] sd 6:0:0:0: Attached scsi generic sg0 type 0
Jul 21 11:01:48 lui-desktop kernel: [    2.700430] sd 6:0:0:0: [sda] 240121728 512-byte logical blocks: (122 GB/114 GiB)
Jul 21 11:01:48 lui-desktop kernel: [    2.700476] sd 6:0:0:0: [sda] Write Protect is off
Jul 21 11:01:48 lui-desktop kernel: [    2.700503] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 21 11:01:48 lui-desktop kernel: [    2.700626]  sda: sda1 sda2 < sda5 >
Jul 21 11:01:48 lui-desktop kernel: [    2.742515] sd 6:0:0:0: [sda] Attached SCSI disk
Jul 21 11:01:48 lui-desktop kernel: [    3.114808] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jul 21 11:01:48 lui-desktop kernel: [    3.114812] EXT4-fs (sda1): write access will be enabled during recovery
Jul 21 11:01:48 lui-desktop kernel: [    3.277592] EXT4-fs (sda1): orphan cleanup on readonly fs
Jul 21 11:01:48 lui-desktop kernel: [    3.277701] EXT4-fs (sda1): 2 orphan inodes deleted
Jul 21 11:01:48 lui-desktop kernel: [    3.277704] EXT4-fs (sda1): recovery complete
Jul 21 11:01:48 lui-desktop kernel: [    3.701194] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul 21 11:01:48 lui-desktop kernel: [   14.313078] udev: starting version 151
Jul 21 11:01:48 lui-desktop kernel: [   14.348398] Adding 4920312k swap on /dev/sda5.  Priority:-1 extents:1 across:4920312k 
Jul 21 11:01:48 lui-desktop kernel: [   14.478845] lp: driver loaded but no devices found
Jul 21 11:01:48 lui-desktop kernel: [   14.558963] type=1505 audit(1279706508.475:2):  operation="profile_load" pid=636 name="/sbin/dhclient3"
Jul 21 11:01:48 lui-desktop kernel: [   14.559596] type=1505 audit(1279706508.475:3):  operation="profile_load" pid=636 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 21 11:01:48 lui-desktop kernel: [   14.559943] type=1505 audit(1279706508.475:4):  operation="profile_load" pid=636 name="/usr/lib/connman/scripts/dhclient-script"
Jul 21 11:01:48 lui-desktop kernel: [   14.571203] parport_pc 00:0b: reported by Plug and Play ACPI
Jul 21 11:01:48 lui-desktop kernel: [   14.571310] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jul 21 11:01:48 lui-desktop kernel: [   14.573397] [drm] Initialized drm 1.1.0 20060810
Jul 21 11:01:48 lui-desktop kernel: [   14.628882] ppdev: user-space parallel port driver
Jul 21 11:01:48 lui-desktop kernel: [   14.641443] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:48 lui-desktop kernel: [   14.650207] lp0: using parport0 (interrupt-driven).
Jul 21 11:01:48 lui-desktop kernel: [   14.651760] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5000a2)
Jul 21 11:01:48 lui-desktop kernel: [   14.652125] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Jul 21 11:01:48 lui-desktop kernel: [   14.734345] [drm] nouveau 0000:01:00.0: ... appears to be valid
Jul 21 11:01:48 lui-desktop kernel: [   14.734350] [drm] nouveau 0000:01:00.0: BIT BIOS found
Jul 21 11:01:48 lui-desktop kernel: [   14.734353] [drm] nouveau 0000:01:00.0: Bios version 70.16.2e.00
Jul 21 11:01:48 lui-desktop kernel: [   14.734404] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Jul 21 11:01:48 lui-desktop kernel: [   14.734407] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Jul 21 11:01:48 lui-desktop kernel: [   14.734410] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Jul 21 11:01:48 lui-desktop kernel: [   14.734413] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Jul 21 11:01:48 lui-desktop kernel: [   14.734415] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
Jul 21 11:01:48 lui-desktop kernel: [   14.734418] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
Jul 21 11:01:48 lui-desktop kernel: [   14.734421] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000302 00020030
Jul 21 11:01:48 lui-desktop kernel: [   14.734424] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02000300 00000000
Jul 21 11:01:48 lui-desktop kernel: [   14.734426] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01032310 00000000
Jul 21 11:01:48 lui-desktop kernel: [   14.734428] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02021362 00020010
Jul 21 11:01:48 lui-desktop kernel: [   14.734436] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD3F5
Jul 21 11:01:48 lui-desktop kernel: [   14.817414] r8169: eth0: link up
Jul 21 11:01:48 lui-desktop kernel: [   14.817422] r8169: eth0: link up
Jul 21 11:01:48 lui-desktop kernel: [   14.819386] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 21 11:01:48 lui-desktop kernel: [   14.821909] [drm] nouveau 0000:01:00.0: 0xD717: Condition still not met after 20ms, skipping following opcodes
Jul 21 11:01:48 lui-desktop kernel: [   14.839533] type=1505 audit(1279706508.755:5):  operation="profile_load" pid=787 name="/usr/share/gdm/guest-session/Xsession"
Jul 21 11:01:48 lui-desktop kernel: [   14.841054] type=1505 audit(1279706508.765:6):  operation="profile_replace" pid=788 name="/sbin/dhclient3"
Jul 21 11:01:48 lui-desktop kernel: [   14.841731] type=1505 audit(1279706508.765:7):  operation="profile_replace" pid=788 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 21 11:01:48 lui-desktop kernel: [   14.842071] type=1505 audit(1279706508.765:8):  operation="profile_replace" pid=788 name="/usr/lib/connman/scripts/dhclient-script"
Jul 21 11:01:48 lui-desktop kernel: [   14.844686] type=1505 audit(1279706508.765:9):  operation="profile_load" pid=789 name="/usr/bin/evince"
Jul 21 11:01:48 lui-desktop kernel: [   14.851317] [drm] nouveau 0000:01:00.0: 0xD71B: Condition still not met after 20ms, skipping following opcodes
Jul 21 11:01:48 lui-desktop kernel: [   14.851339] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD905
Jul 21 11:01:48 lui-desktop kernel: [   14.853036] type=1505 audit(1279706508.775:10):  operation="profile_load" pid=789 name="/usr/bin/evince-previewer"
Jul 21 11:01:48 lui-desktop kernel: [   14.858037] type=1505 audit(1279706508.775:11):  operation="profile_load" pid=789 name="/usr/bin/evince-thumbnailer"
Jul 21 11:01:48 lui-desktop kernel: [   14.911422] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE78C
Jul 21 11:01:48 lui-desktop kernel: [   14.911433] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE7CA
Jul 21 11:01:48 lui-desktop kernel: [   14.972871] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEA0A
Jul 21 11:01:48 lui-desktop kernel: [   14.972874] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEA6F
Jul 21 11:01:48 lui-desktop kernel: [   15.001285] [drm] nouveau 0000:01:00.0: 0xEA6F: Condition still not met after 20ms, skipping following opcodes
Jul 21 11:01:48 lui-desktop kernel: [   15.001295] [drm] nouveau 0000:01:00.0: 0xC080: parsing output script 0
Jul 21 11:01:48 lui-desktop kernel: [   15.001298] [drm] nouveau 0000:01:00.0: 0xC080: parsing output script 0
Jul 21 11:01:49 lui-desktop kernel: [   15.160817] [TTM] Zone  kernel: Available graphics memory: 1028726 kiB.
Jul 21 11:01:49 lui-desktop kernel: [   15.160827] [drm] nouveau 0000:01:00.0: 1024 MiB VRAM
Jul 21 11:01:49 lui-desktop kernel: [   15.178624] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Jul 21 11:01:49 lui-desktop kernel: [   15.179461] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Jul 21 11:01:49 lui-desktop kernel: [   15.183080] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Jul 21 11:01:49 lui-desktop kernel: [   15.183508] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Jul 21 11:01:49 lui-desktop kernel: [   15.183511] [drm] nouveau 0000:01:00.0: Detected a DAC output
Jul 21 11:01:49 lui-desktop kernel: [   15.183514] [drm] nouveau 0000:01:00.0: Detected a DAC output
Jul 21 11:01:49 lui-desktop kernel: [   15.183516] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Jul 21 11:01:49 lui-desktop kernel: [   15.183519] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Jul 21 11:01:49 lui-desktop kernel: [   15.183722] [drm] nouveau 0000:01:00.0: Detected a VGA connector
Jul 21 11:01:49 lui-desktop kernel: [   15.183846] [drm] nouveau 0000:01:00.0: Detected a DVI-D connector
Jul 21 11:01:49 lui-desktop kernel: [   15.286135] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Jul 21 11:01:49 lui-desktop kernel: [   15.521419] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x40250000, bo ffff8800702d6c00
Jul 21 11:01:49 lui-desktop kernel: [   15.521472] fb0: nouveaufb frame buffer device
Jul 21 11:01:49 lui-desktop kernel: [   15.521474] registered panic notifier
Jul 21 11:01:49 lui-desktop kernel: [   15.521479] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Jul 21 11:01:49 lui-desktop kernel: [   15.521512] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 21 11:01:49 lui-desktop kernel: [   15.521516] hda_intel: Disable MSI for Nvidia chipset
Jul 21 11:01:49 lui-desktop kernel: [   15.523326] vga16fb: mapped to 0xffff8800000a0000
Jul 21 11:01:49 lui-desktop kernel: [   15.523329] vga16fb: not registering due to another framebuffer present
Jul 21 11:01:49 lui-desktop kernel: [   15.534269] Console: switching to colour frame buffer device 160x64
Jul 21 11:01:49 lui-desktop kernel: [   15.535947] [drm] nouveau 0000:01:00.0: 0x74A8: parsing clock script 0
Jul 21 11:01:50 lui-desktop kernel: [   16.856231] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
Jul 21 11:01:50 lui-desktop kernel: [   16.860260] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
Jul 21 11:04:35 lui-desktop pulseaudio[1395]: ratelimit.c: 2 events suppressed

```

---

