---
title: "Boot taking forever"
date: 2010-07-04
forum: General Help
---

### Post by J V on 2010-07-04
Specifically, the part of the boot between when grub is supposed to show and when the splash screen pops up.

Have grub set to 0 timeout so it will speed ahead (Holding shift doesn't open it up strangely)

Recently installed video card, did profile so that's not the problem.

Any ideas? Where should I look in the logs?

---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-04
I don't remember exactly what I searched for, but there was code that worked for me. Try searching using plymouth boot splash screen stall or something.

---

### Post by philinux on 2010-07-04
> **J V said:**
> Specifically, the part of the boot between when grub is supposed to show and when the splash screen pops up.

Have grub set to 0 timeout so it will speed ahead (Holding shift doesn't open it up strangely)

Recently installed video card, did profile so that's not the problem.

Any ideas? Where should I look in the logs?

See the general help forum sticky. Try disabling the floppy in the bios if you dont have one.

---

### Post by J V on 2010-07-04
Great thanks! I'll be right back...

---

### Post by J V on 2010-07-04
Nope, that didn't fix it... no floppy in bios, no floppy in machine...

Also, when I log out theres a graphical error: I get the non-graphical terminal overlayed with the "Dots" that appear under the ubuntu logo (But no ubuntu logo) - could this have something to do with it?

---

### Post by philinux on 2010-07-04
> **J V said:**
> Nope, that didn't fix it... no floppy in bios, no floppy in machine...

Also, when I log out theres a graphical error: I get the non-graphical terminal overlayed with the "Dots" that appear under the ubuntu logo (But no ubuntu logo) - could this have something to do with it?

Have a look in /var/log/messages for anything odd.

You could install bootchart and examine the boot process.

---

### Post by J V on 2010-07-04
```
Jul  4 16:07:01 jubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul  4 16:07:01 jubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="895" x-info="http://www.rsyslog.com"] (re)start
Jul  4 16:07:01 jubuntu rsyslogd: rsyslogd's groupid changed to 103
Jul  4 16:07:01 jubuntu rsyslogd: rsyslogd's userid changed to 101
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Linux version 2.6.32-23-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=83a8c7db-bc5b-42c5-8ea3-2e1e0df77f4f ro splash vga=795 quiet splash
Jul  4 16:07:01 jubuntu kernel: [    0.000000] KERNEL supported cpus:
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   Intel GenuineIntel
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jul  4 16:07:01 jubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fcafe00 (usable)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 000000007fcb1e00 - 000000007fcb1ea0 (ACPI NVS)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 000000007fcb1ea0 - 0000000080000000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed40000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed45000 - 0000000100000000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] DMI 2.5 present.
Jul  4 16:07:01 jubuntu kernel: [    0.000000] last_pfn = 0x7fcaf max_arch_pfn = 0x400000000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul  4 16:07:01 jubuntu kernel: [    0.000000] modified physical RAM map:
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007fcafe00 (usable)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 000000007fcb1e00 - 000000007fcb1ea0 (ACPI NVS)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 000000007fcb1ea0 - 0000000080000000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 00000000f4000000 - 00000000f8000000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fed40000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000]  modified: 00000000fed45000 - 0000000100000000 (reserved)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007fcaf000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jul  4 16:07:01 jubuntu kernel: [    0.000000] RAMDISK: 37286000 - 37feff16
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: RSDP 00000000000e5c10 00014 (v00 COMPAQ)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: RSDT 000000007fcc1e40 00044 (v01 HPQOEM SLIC-BPC 20070718      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: FACP 000000007fcc1ee8 00074 (v01 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: DSDT 000000007fcc2427 0A1B6 (v01 COMPAQ DSDT_PRJ 00000001 MSFT 0100000E)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: FACS 000000007fcc1e00 00040
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: APIC 000000007fcc1f5c 00084 (v01 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: ASF! 000000007fcc1fe0 00063 (v32 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: MCFG 000000007fcc2043 0003C (v01 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: TCPA 000000007fcc207f 00032 (v01 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: SLIC 000000007fcc20b1 00176 (v01 HPQOEM SLIC-BPC 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: HPET 000000007fcc2227 00038 (v01 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: DMAR 000000007fcc225f 00160 (v01 COMPAQ BEARLAKE 00000001      00000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] No NUMA configuration found
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007fcaf000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fcaf000
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   bootmap [000000000000f000 -  000000000001ef97] pages 10
Jul  4 16:07:01 jubuntu kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007fcaf000]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #2 [0001000000 - 0001a2de64]    TEXT DATA BSS ==> [0001000000 - 0001a2de64]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #3 [0037286000 - 0037feff16]          RAMDISK ==> [0037286000 - 0037feff16]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #5 [0001a2e000 - 0001a2e12c]              BRK ==> [0001a2e000 - 0001a2e12c]
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
Jul  4 16:07:01 jubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f9bf0] f9bf0
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Zone PFN ranges:
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jul  4 16:07:01 jubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jul  4 16:07:01 jubuntu kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul  4 16:07:01 jubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Jul  4 16:07:01 jubuntu kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul  4 16:07:01 jubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007fcaf
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xf808
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul  4 16:07:01 jubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  4 16:07:01 jubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul  4 16:07:01 jubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:74000000)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  4 16:07:01 jubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Jul  4 16:07:01 jubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
Jul  4 16:07:01 jubuntu kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Jul  4 16:07:01 jubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516079
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Policy zone: DMA32
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=83a8c7db-bc5b-42c5-8ea3-2e1e0df77f4f ro splash vga=795 quiet splash
Jul  4 16:07:01 jubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Initializing CPU#0
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Checking aperture...
Jul  4 16:07:01 jubuntu kernel: [    0.000000] No AGP bridge found
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Memory: 2039856k/2093756k available (5419k kernel code, 408k absent, 53492k reserved, 2974k data, 880k init)
Jul  4 16:07:01 jubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jul  4 16:07:01 jubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Console: colour dummy device 80x25
Jul  4 16:07:01 jubuntu kernel: [    0.000000] console [tty0] enabled
Jul  4 16:07:01 jubuntu kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Jul  4 16:07:01 jubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  4 16:07:01 jubuntu kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jul  4 16:07:01 jubuntu kernel: [    0.000000] Detected 2992.068 MHz processor.
Jul  4 16:07:01 jubuntu kernel: [    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.13 BogoMIPS (lpj=29920680)
Jul  4 16:07:01 jubuntu kernel: [    0.010033] Security Framework initialized
Jul  4 16:07:01 jubuntu kernel: [    0.010051] AppArmor: AppArmor initialized
Jul  4 16:07:01 jubuntu kernel: [    0.010198] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.011243] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.011834] Mount-cache hash table entries: 256
Jul  4 16:07:01 jubuntu kernel: [    0.011969] Initializing cgroup subsys ns
Jul  4 16:07:01 jubuntu kernel: [    0.011973] Initializing cgroup subsys cpuacct
Jul  4 16:07:01 jubuntu kernel: [    0.011976] Initializing cgroup subsys memory
Jul  4 16:07:01 jubuntu kernel: [    0.011984] Initializing cgroup subsys devices
Jul  4 16:07:01 jubuntu kernel: [    0.011986] Initializing cgroup subsys freezer
Jul  4 16:07:01 jubuntu kernel: [    0.011987] Initializing cgroup subsys net_cls
Jul  4 16:07:01 jubuntu kernel: [    0.012006] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  4 16:07:01 jubuntu kernel: [    0.012008] CPU: L2 cache: 4096K
Jul  4 16:07:01 jubuntu kernel: [    0.012010] CPU 0/0x0 -> Node 0
Jul  4 16:07:01 jubuntu kernel: [    0.012012] CPU: Physical Processor ID: 0
Jul  4 16:07:01 jubuntu kernel: [    0.012013] CPU: Processor Core ID: 0
Jul  4 16:07:01 jubuntu kernel: [    0.012015] mce: CPU supports 6 MCE banks
Jul  4 16:07:01 jubuntu kernel: [    0.012022] CPU0: Thermal monitoring enabled (TM2)
Jul  4 16:07:01 jubuntu kernel: [    0.012027] using mwait in idle threads.
Jul  4 16:07:01 jubuntu kernel: [    0.012028] Performance Events: Core2 events, Intel PMU driver.
Jul  4 16:07:01 jubuntu kernel: [    0.012032] ... version:                2
Jul  4 16:07:01 jubuntu kernel: [    0.012034] ... bit width:              40
Jul  4 16:07:01 jubuntu kernel: [    0.012035] ... generic registers:      2
Jul  4 16:07:01 jubuntu kernel: [    0.012036] ... value mask:             000000ffffffffff
Jul  4 16:07:01 jubuntu kernel: [    0.012037] ... max period:             000000007fffffff
Jul  4 16:07:01 jubuntu kernel: [    0.012038] ... fixed-purpose events:   3
Jul  4 16:07:01 jubuntu kernel: [    0.012039] ... event mask:             0000000700000003
Jul  4 16:07:01 jubuntu kernel: [    0.013895] ACPI: Core revision 20090903
Jul  4 16:07:01 jubuntu kernel: [    0.027104] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul  4 16:07:01 jubuntu kernel: [    0.027108] ftrace: allocating 22524 entries in 89 pages
Jul  4 16:07:01 jubuntu kernel: [    0.030047] Setting APIC routing to flat
Jul  4 16:07:01 jubuntu kernel: [    0.030346] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul  4 16:07:01 jubuntu kernel: [    0.134546] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
Jul  4 16:07:01 jubuntu kernel: [    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
Jul  4 16:07:01 jubuntu kernel: [    0.020000] Initializing CPU#1
Jul  4 16:07:01 jubuntu kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  4 16:07:01 jubuntu kernel: [    0.020000] CPU: L2 cache: 4096K
Jul  4 16:07:01 jubuntu kernel: [    0.020000] CPU 1/0x1 -> Node 0
Jul  4 16:07:01 jubuntu kernel: [    0.020000] CPU: Physical Processor ID: 0
Jul  4 16:07:01 jubuntu kernel: [    0.020000] CPU: Processor Core ID: 1
Jul  4 16:07:01 jubuntu kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Jul  4 16:07:01 jubuntu kernel: [    0.290044] CPU1: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
Jul  4 16:07:01 jubuntu kernel: [    0.290049] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul  4 16:07:01 jubuntu kernel: [    0.300015] Brought up 2 CPUs
Jul  4 16:07:01 jubuntu kernel: [    0.300017] Total of 2 processors activated (11969.14 BogoMIPS).
Jul  4 16:07:01 jubuntu kernel: [    0.300585] devtmpfs: initialized
Jul  4 16:07:01 jubuntu kernel: [    0.300585] regulator: core version 0.5
Jul  4 16:07:01 jubuntu kernel: [    0.300585] Time: 16:06:24  Date: 07/04/10
Jul  4 16:07:01 jubuntu kernel: [    0.300585] NET: Registered protocol family 16
Jul  4 16:07:01 jubuntu kernel: [    0.300585] Trying to unpack rootfs image as initramfs...
Jul  4 16:07:01 jubuntu kernel: [    0.300585] ACPI: bus type pci registered
Jul  4 16:07:01 jubuntu kernel: [    0.300585] PCI: MCFG configuration 0: base f4000000 segment 0 buses 0 - 63
Jul  4 16:07:01 jubuntu kernel: [    0.300585] PCI: MCFG area at f4000000 reserved in E820
Jul  4 16:07:01 jubuntu kernel: [    0.300760] PCI: Using MMCONFIG at f4000000 - f7ffffff
Jul  4 16:07:01 jubuntu kernel: [    0.300761] PCI: Using configuration type 1 for base access
Jul  4 16:07:01 jubuntu kernel: [    0.310113] bio: create slab <bio-0> at 0
Jul  4 16:07:01 jubuntu kernel: [    0.321070] ACPI: Interpreter enabled
Jul  4 16:07:01 jubuntu kernel: [    0.321075] ACPI: (supports S0 S3 S4 S5)
Jul  4 16:07:01 jubuntu kernel: [    0.321090] ACPI: Using IOAPIC for interrupt routing
Jul  4 16:07:01 jubuntu kernel: [    0.325668] ACPI: No dock devices found.
Jul  4 16:07:01 jubuntu kernel: [    0.325992] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.325997] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007db2ab20), AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.326003] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Jul  4 16:07:01 jubuntu kernel: [    0.326018] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Jul  4 16:07:01 jubuntu kernel: [    0.326023] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  4 16:07:01 jubuntu kernel: [    0.326102] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326105] pci 0000:00:01.0: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.326162] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326164] pci 0000:00:03.0: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.326369] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326372] pci 0000:00:19.0: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.326577] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326581] pci 0000:00:1a.7: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.326646] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326649] pci 0000:00:1b.0: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.326697] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326700] pci 0000:00:1c.0: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.326753] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.326756] pci 0000:00:1c.1: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.327021] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul  4 16:07:01 jubuntu kernel: [    0.327025] pci 0000:00:1d.7: PME# disabled
Jul  4 16:07:01 jubuntu kernel: [    0.327128] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH6 ACPI/GPIO/TCO
Jul  4 16:07:01 jubuntu kernel: [    0.327131] pci 0000:00:1f.0: quirk: region fa00-fa3f claimed by ICH6 GPIO
Jul  4 16:07:01 jubuntu kernel: [    0.327134] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0400 (mask 007f)
Jul  4 16:07:01 jubuntu kernel: [    0.327136] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0480 (mask 000f)
Jul  4 16:07:01 jubuntu kernel: [    0.327139] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0cb0 (mask 000f)
Jul  4 16:07:01 jubuntu kernel: [    0.327570] pci 0000:00:1e.0: transparent bridge
Jul  4 16:07:01 jubuntu kernel: [    0.328097] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.328101] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007db2ab20), AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.328119] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Jul  4 16:07:01 jubuntu kernel: [    0.347842] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.347926] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.348004] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.348084] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.348161] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.348239] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.348317] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 14 15)
Jul  4 16:07:01 jubuntu kernel: [    0.348396] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
Jul  4 16:07:01 jubuntu kernel: [    0.348503] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul  4 16:07:01 jubuntu kernel: [    0.348506] vgaarb: loaded
Jul  4 16:07:01 jubuntu kernel: [    0.348601] SCSI subsystem initialized
Jul  4 16:07:01 jubuntu kernel: [    0.348733] usbcore: registered new interface driver usbfs
Jul  4 16:07:01 jubuntu kernel: [    0.348744] usbcore: registered new interface driver hub
Jul  4 16:07:01 jubuntu kernel: [    0.348762] usbcore: registered new device driver usb
Jul  4 16:07:01 jubuntu kernel: [    0.348878] ACPI: WMI: Mapper loaded
Jul  4 16:07:01 jubuntu kernel: [    0.348880] PCI: Using ACPI for IRQ routing
Jul  4 16:07:01 jubuntu kernel: [    0.349008] NetLabel: Initializing
Jul  4 16:07:01 jubuntu kernel: [    0.349009] NetLabel:  domain hash size = 128
Jul  4 16:07:01 jubuntu kernel: [    0.349011] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  4 16:07:01 jubuntu kernel: [    0.349021] NetLabel:  unlabeled traffic allowed by default
Jul  4 16:07:01 jubuntu kernel: [    0.349047] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul  4 16:07:01 jubuntu kernel: [    0.349051] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jul  4 16:07:01 jubuntu kernel: [    0.360113] Switching to clocksource tsc
Jul  4 16:07:01 jubuntu kernel: [    0.361397] AppArmor: AppArmor Filesystem Enabled
Jul  4 16:07:01 jubuntu kernel: [    0.361411] pnp: PnP ACPI init
Jul  4 16:07:01 jubuntu kernel: [    0.361426] ACPI: bus type pnp registered
Jul  4 16:07:01 jubuntu kernel: [    0.363450] pnp 00:0e: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
Jul  4 16:07:01 jubuntu kernel: [    0.363453] pnp 00:0e: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
Jul  4 16:07:01 jubuntu kernel: [    0.363455] pnp 00:0e: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
Jul  4 16:07:01 jubuntu kernel: [    0.363458] pnp 00:0e: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling
Jul  4 16:07:01 jubuntu kernel: [    0.364013] pnp: PnP ACPI: found 17 devices
Jul  4 16:07:01 jubuntu kernel: [    0.364015] ACPI: ACPI bus type pnp unregistered
Jul  4 16:07:01 jubuntu kernel: [    0.364029] system 00:0e: ioport range 0x400-0x41f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364031] system 00:0e: ioport range 0x420-0x43f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364033] system 00:0e: ioport range 0x440-0x45f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364034] system 00:0e: ioport range 0x460-0x47f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364036] system 00:0e: ioport range 0x480-0x48f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364038] system 00:0e: ioport range 0xfa00-0xfa3f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364040] system 00:0e: ioport range 0xfc00-0xfc7f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364042] system 00:0e: ioport range 0xfc80-0xfcff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364044] system 00:0e: ioport range 0xfe00-0xfe7f has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364046] system 00:0e: ioport range 0xfe80-0xfeff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364050] system 00:0f: ioport range 0x4d0-0x4d1 has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364054] system 00:10: iomem range 0x0-0x9ffff could not be reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364056] system 00:10: iomem range 0x100000-0x7fffffff could not be reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364058] system 00:10: iomem range 0xe4000-0xfffff could not be reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364060] system 00:10: iomem range 0xfec01000-0xfecfffff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364062] system 00:10: iomem range 0xfed00400-0xfed3ffff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364064] system 00:10: iomem range 0xfed45000-0xffffffff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364066] system 00:10: iomem range 0xf4000000-0xf7ffffff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.364068] system 00:10: iomem range 0xd0000-0xe3fff has been reserved
Jul  4 16:07:01 jubuntu kernel: [    0.368757] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf0000000-0xefffffff]
Jul  4 16:07:01 jubuntu kernel: [    0.368760] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jul  4 16:07:01 jubuntu kernel: [    0.368762] pci 0000:00:01.0:   IO window: 0x1000-0x1fff
Jul  4 16:07:01 jubuntu kernel: [    0.368765] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf2ffffff
Jul  4 16:07:01 jubuntu kernel: [    0.368767] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Jul  4 16:07:01 jubuntu kernel: [    0.368770] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:20
Jul  4 16:07:01 jubuntu kernel: [    0.368773] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
Jul  4 16:07:01 jubuntu kernel: [    0.368776] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
Jul  4 16:07:01 jubuntu kernel: [    0.368779] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
Jul  4 16:07:01 jubuntu kernel: [    0.368784] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:30
Jul  4 16:07:01 jubuntu kernel: [    0.368786] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
Jul  4 16:07:01 jubuntu kernel: [    0.368790] pci 0000:00:1c.1:   MEM window: 0x80400000-0x805fffff
Jul  4 16:07:01 jubuntu kernel: [    0.368793] pci 0000:00:1c.1:   PREFETCH window: 0x00000080600000-0x000000807fffff
Jul  4 16:07:01 jubuntu kernel: [    0.368797] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Jul  4 16:07:01 jubuntu kernel: [    0.368799] pci 0000:00:1e.0:   IO window: disabled
Jul  4 16:07:01 jubuntu kernel: [    0.368802] pci 0000:00:1e.0:   MEM window: 0xf3100000-0xf31fffff
Jul  4 16:07:01 jubuntu kernel: [    0.368805] pci 0000:00:1e.0:   PREFETCH window: disabled
Jul  4 16:07:01 jubuntu kernel: [    0.368825] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  4 16:07:01 jubuntu kernel: [    0.368845] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul  4 16:07:01 jubuntu kernel: [    0.368905] NET: Registered protocol family 2
Jul  4 16:07:01 jubuntu kernel: [    0.369012] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.369557] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.371615] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.372204] TCP: Hash tables configured (established 262144 bind 65536)
Jul  4 16:07:01 jubuntu kernel: [    0.372206] TCP reno registered
Jul  4 16:07:01 jubuntu kernel: [    0.372309] NET: Registered protocol family 1
Jul  4 16:07:01 jubuntu kernel: [    0.372615] Scanning for low memory corruption every 60 seconds
Jul  4 16:07:01 jubuntu kernel: [    0.372737] audit: initializing netlink socket (disabled)
Jul  4 16:07:01 jubuntu kernel: [    0.372746] type=2000 audit(1278259584.369:1): initialized
Jul  4 16:07:01 jubuntu kernel: [    0.379539] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul  4 16:07:01 jubuntu kernel: [    0.380550] VFS: Disk quotas dquot_6.5.2
Jul  4 16:07:01 jubuntu kernel: [    0.380591] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul  4 16:07:01 jubuntu kernel: [    0.381028] fuse init (API version 7.13)
Jul  4 16:07:01 jubuntu kernel: [    0.381084] msgmni has been set to 3984
Jul  4 16:07:01 jubuntu kernel: [    0.381242] alg: No test for stdrng (krng)
Jul  4 16:07:01 jubuntu kernel: [    0.381278] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  4 16:07:01 jubuntu kernel: [    0.381281] io scheduler noop registered
Jul  4 16:07:01 jubuntu kernel: [    0.381282] io scheduler anticipatory registered
Jul  4 16:07:01 jubuntu kernel: [    0.381283] io scheduler deadline registered
Jul  4 16:07:01 jubuntu kernel: [    0.381308] io scheduler cfq registered (default)
Jul  4 16:07:01 jubuntu kernel: [    0.381667] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  4 16:07:01 jubuntu kernel: [    0.381774] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.381779] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007db2ab20), AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.381801] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Jul  4 16:07:01 jubuntu kernel: [    0.381876] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.381881] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007db2ab20), AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.381898] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Jul  4 16:07:01 jubuntu kernel: [    0.381980] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.381984] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007db2ab20), AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.382001] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Jul  4 16:07:01 jubuntu kernel: [    0.382070] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.382074] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88007db2ab20), AE_ALREADY_EXISTS
Jul  4 16:07:01 jubuntu kernel: [    0.382092] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Jul  4 16:07:01 jubuntu kernel: [    0.382106] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  4 16:07:01 jubuntu kernel: [    0.382188] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul  4 16:07:01 jubuntu kernel: [    0.382397] ACPI: Power Button [PBTN]
Jul  4 16:07:01 jubuntu kernel: [    0.382429] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul  4 16:07:01 jubuntu kernel: [    0.382431] ACPI: Power Button [PWRF]
Jul  4 16:07:01 jubuntu kernel: [    0.382814] ACPI: SSDT 000000007fccd42b 003AC (v01 COMPAQ  CPU_TM2 00000001 MSFT 0100000E)
Jul  4 16:07:01 jubuntu kernel: [    0.383063] ACPI: SSDT 000000007fccd2af 0017C (v01 COMPAQ      CST 00000001 MSFT 0100000E)
Jul  4 16:07:01 jubuntu kernel: [    0.383237] Marking TSC unstable due to TSC halts in idle
Jul  4 16:07:01 jubuntu kernel: [    0.383282] processor LNXCPU:00: registered as cooling_device0
Jul  4 16:07:01 jubuntu kernel: [    0.383439] Switching to clocksource hpet
Jul  4 16:07:01 jubuntu kernel: [    0.383489] processor LNXCPU:01: registered as cooling_device1
Jul  4 16:07:01 jubuntu kernel: [    0.386127] Linux agpgart interface v0.103
Jul  4 16:07:01 jubuntu kernel: [    0.386149] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul  4 16:07:01 jubuntu kernel: [    0.386237] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  4 16:07:01 jubuntu kernel: [    0.386489] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  4 16:07:01 jubuntu kernel: [    0.386593] serial 0000:00:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul  4 16:07:01 jubuntu kernel: [    0.386635] 0000:00:03.3: ttyS1 at I/O 0x2240 (irq = 17) is a 16550A
Jul  4 16:07:01 jubuntu kernel: [    0.387319] brd: module loaded
Jul  4 16:07:01 jubuntu kernel: [    0.387637] loop: module loaded
Jul  4 16:07:01 jubuntu kernel: [    0.387692] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul  4 16:07:01 jubuntu kernel: [    0.387770] ata_piix 0000:00:1f.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Jul  4 16:07:01 jubuntu kernel: [    0.387773] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jul  4 16:07:01 jubuntu kernel: [    0.524001] Freeing initrd memory: 13735k freed
Jul  4 16:07:01 jubuntu kernel: [    0.551492] scsi0 : ata_piix
Jul  4 16:07:01 jubuntu kernel: [    0.551603] scsi1 : ata_piix
Jul  4 16:07:01 jubuntu kernel: [    0.551772] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x21f0 irq 14
Jul  4 16:07:01 jubuntu kernel: [    0.551776] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x21f8 irq 15
Jul  4 16:07:01 jubuntu kernel: [    0.551809] ata_piix 0000:00:1f.5: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Jul  4 16:07:01 jubuntu kernel: [    0.551814] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jul  4 16:07:01 jubuntu kernel: [    0.710092] scsi2 : ata_piix
Jul  4 16:07:01 jubuntu kernel: [    0.710147] scsi3 : ata_piix
Jul  4 16:07:01 jubuntu kernel: [    0.710178] ata3: SATA max UDMA/133 cmd 0x2258 ctl 0x2278 bmdma 0x2210 irq 18
Jul  4 16:07:01 jubuntu kernel: [    0.710182] ata4: SATA max UDMA/133 cmd 0x2260 ctl 0x227c bmdma 0x2218 irq 18
Jul  4 16:07:01 jubuntu kernel: [    0.710241] pata_acpi 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul  4 16:07:01 jubuntu kernel: [    0.710268] pata_acpi 0000:00:03.2: PCI INT C disabled
Jul  4 16:07:01 jubuntu kernel: [    0.710466] Fixed MDIO Bus: probed
Jul  4 16:07:01 jubuntu kernel: [    0.710491] PPP generic driver version 2.4.2
Jul  4 16:07:01 jubuntu kernel: [    0.710548] tun: Universal TUN/TAP device driver, 1.6
Jul  4 16:07:01 jubuntu kernel: [    0.710550] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  4 16:07:01 jubuntu kernel: [    0.710624] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  4 16:07:01 jubuntu kernel: [    0.710645] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jul  4 16:07:01 jubuntu kernel: [    0.710662] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.710685] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jul  4 16:07:01 jubuntu kernel: [    0.710709] ehci_hcd 0000:00:1a.7: debug port 1
Jul  4 16:07:01 jubuntu kernel: [    0.714595] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xf3026000
Jul  4 16:07:01 jubuntu kernel: [    0.730028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jul  4 16:07:01 jubuntu kernel: [    0.730111] usb usb1: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.730138] hub 1-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.730146] hub 1-0:1.0: 4 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.730209] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul  4 16:07:01 jubuntu kernel: [    0.730217] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.730239] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jul  4 16:07:01 jubuntu kernel: [    0.730261] ehci_hcd 0000:00:1d.7: debug port 1
Jul  4 16:07:01 jubuntu kernel: [    0.734156] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf3026400
Jul  4 16:07:01 jubuntu kernel: [    0.750021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul  4 16:07:01 jubuntu kernel: [    0.750095] usb usb2: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.750120] hub 2-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.750126] hub 2-0:1.0: 6 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.750181] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  4 16:07:01 jubuntu kernel: [    0.750194] uhci_hcd: USB Universal Host Controller Interface driver
Jul  4 16:07:01 jubuntu kernel: [    0.750219] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul  4 16:07:01 jubuntu kernel: [    0.750225] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.750254] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jul  4 16:07:01 jubuntu kernel: [    0.750273] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00002120
Jul  4 16:07:01 jubuntu kernel: [    0.750328] usb usb3: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.750345] hub 3-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.750349] hub 3-0:1.0: 2 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.750385] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul  4 16:07:01 jubuntu kernel: [    0.750391] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.750411] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jul  4 16:07:01 jubuntu kernel: [    0.750436] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00002140
Jul  4 16:07:01 jubuntu kernel: [    0.750494] usb usb4: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.750510] hub 4-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.750514] hub 4-0:1.0: 2 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.750546] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul  4 16:07:01 jubuntu kernel: [    0.750552] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.750571] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jul  4 16:07:01 jubuntu kernel: [    0.750592] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002160
Jul  4 16:07:01 jubuntu kernel: [    0.750650] usb usb5: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.750666] hub 5-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.750670] hub 5-0:1.0: 2 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.750698] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul  4 16:07:01 jubuntu kernel: [    0.750706] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.750728] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jul  4 16:07:01 jubuntu kernel: [    0.750746] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00002180
Jul  4 16:07:01 jubuntu kernel: [    0.750809] usb usb6: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.750828] hub 6-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.750832] hub 6-0:1.0: 2 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.750861] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jul  4 16:07:01 jubuntu kernel: [    0.750867] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul  4 16:07:01 jubuntu kernel: [    0.750892] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jul  4 16:07:01 jubuntu kernel: [    0.750910] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000021a0
Jul  4 16:07:01 jubuntu kernel: [    0.750967] usb usb7: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    0.750986] hub 7-0:1.0: USB hub found
Jul  4 16:07:01 jubuntu kernel: [    0.750990] hub 7-0:1.0: 2 ports detected
Jul  4 16:07:01 jubuntu kernel: [    0.751062] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
Jul  4 16:07:01 jubuntu kernel: [    0.753840] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  4 16:07:01 jubuntu kernel: [    0.753847] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  4 16:07:01 jubuntu kernel: [    0.753928] mice: PS/2 mouse device common for all mice
Jul  4 16:07:01 jubuntu kernel: [    0.754010] rtc_cmos 00:03: RTC can wake from S4
Jul  4 16:07:01 jubuntu kernel: [    0.754038] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul  4 16:07:01 jubuntu kernel: [    0.754058] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul  4 16:07:01 jubuntu kernel: [    0.754141] device-mapper: uevent: version 1.0.3
Jul  4 16:07:01 jubuntu kernel: [    0.754207] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul  4 16:07:01 jubuntu kernel: [    0.754255] device-mapper: multipath: version 1.1.0 loaded
Jul  4 16:07:01 jubuntu kernel: [    0.754257] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul  4 16:07:01 jubuntu kernel: [    0.754405] cpuidle: using governor ladder
Jul  4 16:07:01 jubuntu kernel: [    0.754463] cpuidle: using governor menu
Jul  4 16:07:01 jubuntu kernel: [    0.754695] TCP cubic registered
Jul  4 16:07:01 jubuntu kernel: [    0.754777] NET: Registered protocol family 10
Jul  4 16:07:01 jubuntu kernel: [    0.755087] lo: Disabled Privacy Extensions
Jul  4 16:07:01 jubuntu kernel: [    0.755270] NET: Registered protocol family 17
Jul  4 16:07:01 jubuntu kernel: [    0.756655] registered taskstats version 1
Jul  4 16:07:01 jubuntu kernel: [    0.756951]   Magic number: 2:68:135
Jul  4 16:07:01 jubuntu kernel: [    0.756967] block ram0: hash matches
Jul  4 16:07:01 jubuntu kernel: [    0.757026] rtc_cmos 00:03: setting system clock to 2010-07-04 16:06:25 UTC (1278259585)
Jul  4 16:07:01 jubuntu kernel: [    0.757028] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  4 16:07:01 jubuntu kernel: [    0.757029] EDD information not available.
Jul  4 16:07:01 jubuntu kernel: [    1.070644] ata4: SATA link down (SStatus 0 SControl 300)
Jul  4 16:07:01 jubuntu kernel: [    1.081286] ata3: SATA link down (SStatus 0 SControl 300)
Jul  4 16:07:01 jubuntu kernel: [    1.170031] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jul  4 16:07:01 jubuntu kernel: [    1.410069] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  4 16:07:01 jubuntu kernel: [    1.410079] ata1.01: SATA link down (SStatus 0 SControl 300)
Jul  4 16:07:01 jubuntu kernel: [    1.410246] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  4 16:07:01 jubuntu kernel: [    1.410257] ata2.01: SATA link down (SStatus 0 SControl 300)
Jul  4 16:07:01 jubuntu kernel: [    1.430357] ata2.00: ATAPI: TSSTcorp CDDVDW TS-H653Q, HC01, max UDMA/100
Jul  4 16:07:01 jubuntu kernel: [    1.430428] ata1.00: ATA-8: Hitachi HDP725025GLA380, GM2OA5KA, max UDMA/100
Jul  4 16:07:01 jubuntu kernel: [    1.430430] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jul  4 16:07:01 jubuntu kernel: [    1.455526] usb 2-1: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    1.470296] ata2.00: configured for UDMA/100
Jul  4 16:07:01 jubuntu kernel: [    1.490216] ata1.00: configured for UDMA/100
Jul  4 16:07:01 jubuntu kernel: [    1.490302] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72502 GM2O PQ: 0 ANSI: 5
Jul  4 16:07:01 jubuntu kernel: [    1.490388] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  4 16:07:01 jubuntu kernel: [    1.490443] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul  4 16:07:01 jubuntu kernel: [    1.490558] sd 0:0:0:0: [sda] Write Protect is off
Jul  4 16:07:01 jubuntu kernel: [    1.490577] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  4 16:07:01 jubuntu kernel: [    1.490679]  sda:
Jul  4 16:07:01 jubuntu kernel: [    1.491088] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Q  HC01 PQ: 0 ANSI: 5
Jul  4 16:07:01 jubuntu kernel: [    1.496262] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  4 16:07:01 jubuntu kernel: [    1.496265] Uniform CD-ROM driver Revision: 3.20
Jul  4 16:07:01 jubuntu kernel: [    1.496384] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  4 16:07:01 jubuntu kernel: [    1.512055]  sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
Jul  4 16:07:01 jubuntu kernel: [    1.555744] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  4 16:07:01 jubuntu kernel: [    1.555758] Freeing unused kernel memory: 880k freed
Jul  4 16:07:01 jubuntu kernel: [    1.555977] Write protecting the kernel read-only data: 7692k
Jul  4 16:07:01 jubuntu kernel: [    1.567152] udev: starting version 151
Jul  4 16:07:01 jubuntu kernel: [    1.611865] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Jul  4 16:07:01 jubuntu kernel: [    1.611868] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Jul  4 16:07:01 jubuntu kernel: [    1.611914] e1000e 0000:00:19.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul  4 16:07:01 jubuntu kernel: [    1.662011] FDC 0 is a post-1991 82077
Jul  4 16:07:01 jubuntu kernel: [    1.882346] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:0f:fe:ed:af:35
Jul  4 16:07:01 jubuntu kernel: [    1.882349] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Jul  4 16:07:01 jubuntu kernel: [    1.882369] 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: 1062ff-0ff
Jul  4 16:07:01 jubuntu kernel: [    1.970023] usb 4-2: new full speed USB device using uhci_hcd and address 2
Jul  4 16:07:01 jubuntu kernel: [    2.123071] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90004980000, using 5120k, total 5120k
Jul  4 16:07:01 jubuntu kernel: [    2.123073] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
Jul  4 16:07:01 jubuntu kernel: [    2.123075] vesafb: scrolling: redraw
Jul  4 16:07:01 jubuntu kernel: [    2.123076] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jul  4 16:07:01 jubuntu kernel: [    2.123123] fb0: VESA VGA frame buffer device
Jul  4 16:07:01 jubuntu kernel: [    2.126040] Console: switching to colour frame buffer device 160x64
Jul  4 16:07:01 jubuntu kernel: [    2.159540] usb 4-2: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    2.168482] usbcore: registered new interface driver hiddev
Jul  4 16:07:01 jubuntu kernel: [    2.168589] usbcore: registered new interface driver usbhid
Jul  4 16:07:01 jubuntu kernel: [    2.168591] usbhid: v2.6:USB HID core driver
Jul  4 16:07:01 jubuntu kernel: [    2.440020] usb 6-1: new full speed USB device using uhci_hcd and address 2
Jul  4 16:07:01 jubuntu kernel: [    2.620850] usb 6-1: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    2.628022] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input3
Jul  4 16:07:01 jubuntu kernel: [    2.628070] generic-usb 0003:1532:0109.0002: input,hidraw0: USB HID v1.10 Keyboard [Razer Razer Lycosa] on usb-0000:00:1d.1-1/input0
Jul  4 16:07:01 jubuntu kernel: [    2.632857] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input4
Jul  4 16:07:01 jubuntu kernel: [    2.632916] generic-usb 0003:1532:0109.0003: input,hidraw1: USB HID v1.10 Device [Razer Razer Lycosa] on usb-0000:00:1d.1-1/input1
Jul  4 16:07:01 jubuntu kernel: [    2.910020] usb 6-2: new full speed USB device using uhci_hcd and address 3
Jul  4 16:07:01 jubuntu kernel: [    3.087841] usb 6-2: configuration #1 chosen from 1 choice
Jul  4 16:07:01 jubuntu kernel: [    3.095829] input: Razer Razer Lachesis as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input5
Jul  4 16:07:01 jubuntu kernel: [    3.096036] generic-usb 0003:1532:000C.0004: input,hidraw2: USB HID v1.00 Mouse [Razer Razer Lachesis] on usb-0000:00:1d.1-2/input0
Jul  4 16:07:01 jubuntu kernel: [    3.097997] input: Razer Razer Lachesis as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input6
Jul  4 16:07:01 jubuntu kernel: [    3.098042] generic-usb 0003:1532:000C.0005: input,hidraw3: USB HID v1.00 Keyboard [Razer Razer Lachesis] on usb-0000:00:1d.1-2/input1
Jul  4 16:07:01 jubuntu kernel: [   17.161473] sony 0003:054C:0268.0001: timeout initializing reports
Jul  4 16:07:01 jubuntu kernel: [   17.161535] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input7
Jul  4 16:07:01 jubuntu kernel: [   17.161634] sony 0003:054C:0268.0001: input,hiddev96,hidraw4: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1a.1-2/input0
Jul  4 16:07:01 jubuntu kernel: [   22.210137] sony: probe of 0003:054C:0268.0001 failed with error -110
Jul  4 16:07:01 jubuntu kernel: [   22.460034] EXT4-fs (sda8): mounted filesystem with ordered data mode
Jul  4 16:07:01 jubuntu kernel: [   35.011632] udev: starting version 151
Jul  4 16:07:01 jubuntu kernel: [   35.099665] vga16fb: mapped to 0xffff8800000a0000
Jul  4 16:07:01 jubuntu kernel: [   35.099668] vga16fb: not registering due to another framebuffer present
Jul  4 16:07:01 jubuntu kernel: [   35.151645] Adding 1951824k swap on /dev/sda6.  Priority:-1 extents:1 across:1951824k 
Jul  4 16:07:01 jubuntu kernel: [   35.162962] lp: driver loaded but no devices found
Jul  4 16:07:01 jubuntu kernel: [   35.220230] nvidia: module license 'NVIDIA' taints kernel.
Jul  4 16:07:01 jubuntu kernel: [   35.220233] Disabling lock debugging due to kernel taint
Jul  4 16:07:01 jubuntu kernel: [   35.247795] type=1505 audit(1278252419.982:2):  operation="profile_load" pid=657 name="/sbin/dhclient3"
Jul  4 16:07:01 jubuntu kernel: [   35.248248] type=1505 audit(1278252419.982:3):  operation="profile_load" pid=657 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul  4 16:07:01 jubuntu kernel: [   35.248492] type=1505 audit(1278252419.982:4):  operation="profile_load" pid=657 name="/usr/lib/connman/scripts/dhclient-script"
Jul  4 16:07:01 jubuntu kernel: [   35.494386] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Jul  4 16:07:01 jubuntu kernel: [   35.497104] rt2860 0000:07:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jul  4 16:07:01 jubuntu kernel: [   35.497169] 
Jul  4 16:07:01 jubuntu kernel: [   35.497170] 
Jul  4 16:07:01 jubuntu kernel: [   35.497170] === pAd = ffffc90005dc3000, size = 627064 ===
Jul  4 16:07:01 jubuntu kernel: [   35.497171] 
Jul  4 16:07:01 jubuntu kernel: [   35.497172] <-- RTMPAllocAdapterBlock, Status=0
Jul  4 16:07:01 jubuntu kernel: [   35.504428] Linux video capture interface: v2.00
Jul  4 16:07:01 jubuntu kernel: [   35.506302] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
Jul  4 16:07:01 jubuntu kernel: [   35.513625] parport_pc 00:07: reported by Plug and Play ACPI
Jul  4 16:07:01 jubuntu kernel: [   35.513677] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul  4 16:07:01 jubuntu kernel: [   35.532881] ppdev: user-space parallel port driver
Jul  4 16:07:01 jubuntu kernel: [   35.535245] input: UVC Camera (046d:0802) as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input8
Jul  4 16:07:01 jubuntu kernel: [   35.535289] usbcore: registered new interface driver uvcvideo
Jul  4 16:07:01 jubuntu kernel: [   35.535292] USB Video Class driver (v0.1.0)
Jul  4 16:07:01 jubuntu kernel: [   35.577741] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jul  4 16:07:01 jubuntu kernel: [   35.590161] lp0: using parport0 (interrupt-driven).
Jul  4 16:07:01 jubuntu kernel: [   35.590705] tpm_tis 00:0b: 1.2 TPM (device-id 0xB, rev-id 16)
Jul  4 16:07:01 jubuntu kernel: [   35.743856] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  4 16:07:01 jubuntu kernel: [   35.743867] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul  4 16:07:01 jubuntu kernel: [   35.744005] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Jul  4 16:07:01 jubuntu kernel: [   35.851276] usbcore: registered new interface driver snd-usb-audio
Jul  4 16:07:01 jubuntu kernel: [   36.034434] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
Jul  4 16:07:01 jubuntu kernel: [   36.571071] EXT4-fs (sda5): mounted filesystem with writeback data mode
Jul  4 16:07:01 jubuntu kernel: [   36.747932] type=1505 audit(1278252421.482:5):  operation="profile_load" pid=935 name="/usr/share/gdm/guest-session/Xsession"
Jul  4 16:07:01 jubuntu kernel: [   36.749000] type=1505 audit(1278252421.482:6):  operation="profile_replace" pid=936 name="/sbin/dhclient3"
Jul  4 16:07:01 jubuntu kernel: [   36.749458] type=1505 audit(1278252421.482:7):  operation="profile_replace" pid=936 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul  4 16:07:01 jubuntu kernel: [   36.749705] type=1505 audit(1278252421.482:8):  operation="profile_replace" pid=936 name="/usr/lib/connman/scripts/dhclient-script"
Jul  4 16:07:01 jubuntu kernel: [   36.751779] type=1505 audit(1278252421.492:9):  operation="profile_load" pid=937 name="/usr/bin/evince"
Jul  4 16:07:01 jubuntu kernel: [   36.757679] type=1505 audit(1278252421.492:10):  operation="profile_load" pid=937 name="/usr/bin/evince-previewer"
Jul  4 16:07:01 jubuntu kernel: [   36.761549] type=1505 audit(1278252421.502:11):  operation="profile_load" pid=937 name="/usr/bin/evince-thumbnailer"
Jul  4 16:07:01 jubuntu kernel: [   36.960338] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  4 16:07:01 jubuntu kernel: [   36.965023] RX DESC ffff88005f3a1000  size = 2048
Jul  4 16:07:01 jubuntu kernel: [   36.965146] <-- RTMPAllocTxRxRingMemory, Status=0
Jul  4 16:07:01 jubuntu kernel: [   36.968172] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Jul  4 16:07:01 jubuntu kernel: [   36.968174] 1. Phy Mode = 0
Jul  4 16:07:01 jubuntu kernel: [   36.968175] 2. Phy Mode = 0
Jul  4 16:07:01 jubuntu kernel: [   36.980683] RTMPSetPhyMode: channel is out of range, use first channel=1 
Jul  4 16:07:01 jubuntu kernel: [   36.984453] 3. Phy Mode = 0
Jul  4 16:07:01 jubuntu kernel: [   36.987792] MCS Set = 00 00 00 00 00
Jul  4 16:07:01 jubuntu kernel: [   36.989351] <==== RTMPInitialize, Status=0
Jul  4 16:07:01 jubuntu kernel: [   36.989413] 0x1300 = 00073200
Jul  4 16:07:03 jubuntu kernel: [   38.490923] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
Jul  4 16:07:03 jubuntu kernel: [   38.490926] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Jul  4 16:07:03 jubuntu kernel: [   38.491158] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul  4 16:07:03 jubuntu kernel: [   38.738345] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e47a20
Jul  4 16:07:03 jubuntu kernel: [   38.738355] vboxdrv: fAsync=0 offMin=0x144 offMax=0x735
Jul  4 16:07:03 jubuntu kernel: [   38.738819] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul  4 16:07:06 jubuntu kernel: [   42.099228] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1276
Jul  4 16:07:15 jubuntu kernel: [   51.036930] Intel AES-NI instructions are not detected.
Jul  4 16:07:15 jubuntu kernel: [   51.062038] padlock: VIA PadLock not detected.
Jul  4 16:07:27 jubuntu kernel: [   62.261300] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1516
```I have no idea what I'm looking at here, but given the huge amount of messages at 16:07:01, I guess it's in there somewhere...

Take a look at:
```
Jul  4 16:07:01 jubuntu kernel: [   17.161473] sony 0003:054C:0268.0001: timeout initializing reports
```I'm guessing thats 17.16 seconds into the boot or something? There was a large gap in that field right before it...

---

### Post by philinux on 2010-07-04
Try unplugging any usb stuff except mouse and keyboard.

```
Jul  4 **16:07:06 **jubuntu kernel: [   42.099228] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1276
Jul  4 16:07:15 jubuntu kernel: [   51.036930] Intel AES-NI instructions are not detected.
Jul  4 16:07:15 jubuntu kernel: [   51.062038] padlock: VIA PadLock not detected.
Jul  4 **16:07:27** jubuntu kernel: [   62.261300] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1516
```

Time delays here, Via Padlock? Have you got encrypted home?. I would install bootchart and get a good timing.

---

### Post by J V on 2010-07-04
That section is what happens after I log in, that's not where the problem is...

"Forever" may be an overstatement, it's more like 10 seconds or so...

Edit: Found it, it was the PS3 controller...

---

