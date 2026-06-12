---
title: "Ubuntu 11.10 continuously freeze"
date: 2012-02-08
forum: General Help
---

### Post by TheMicZ on 2012-02-08
Hi,
I need a help! My Ubuntu (since 3 days) continuously freeze without a valid reason. For restart my pc, I must use the button on the case! (I can't use mouse, keyboard... so I can't neither do REISUB)

this is my last dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 (Ubuntu 3.0.0-15.26-generic 3.0.13)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=2b4f30a7-acd2-4fc2-81c2-14b8240dd241 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
[    0.000000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/P5Q-PRO, BIOS 2102    02/23/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 4096M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] reg 4, base: 4608MB, range: 256MB, type WB
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff70000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff70000 page 4k
[    0.000000] kernel direct mapping tables up to cff70000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ cff6a000-cff70000
[    0.000000] RAMDISK: 365bc000 - 372d6000
[    0.000000] ACPI: RSDP 00000000000faff0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff70000 00040 (v01 A_M_I_ OEMRSDT  02000923 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff70200 00084 (v02 A_M_I_ OEMFACP  02000923 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff70440 09724 (v01  A1012 A1012001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff7e000 00040
[    0.000000] ACPI: APIC 00000000cff70390 0006C (v01 A_M_I_ OEMAPIC  02000923 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff70400 0003C (v01 A_M_I_ OEMMCFG  02000923 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff7e040 00089 (v01 A_M_I_ AMI_OEM  02000923 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff79b70 00038 (v01 A_M_I_ OEMHPET  02000923 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000cff79bb0 000B0 (v01 A_M_I_ OEMOSFR  02000923 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff7e9d0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012b600000-ffff88012effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000cff70
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048316
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833448 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
[    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031287
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=2b4f30a7-acd2-4fc2-81c2-14b8240dd241 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4038416k/4980736k available (6136k kernel code, 787472k absent, 154848k reserved, 6898k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.369 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5332.73 BogoMIPS (lpj=10665476)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004034] Security Framework initialized
[    0.004049] AppArmor: AppArmor initialized
[    0.004051] Yama: becoming mindful.
[    0.004404] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005983] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008678] Mount-cache hash table entries: 256
[    0.008813] Initializing cgroup subsys cpuacct
[    0.008818] Initializing cgroup subsys memory
[    0.008827] Initializing cgroup subsys devices
[    0.008829] Initializing cgroup subsys freezer
[    0.008830] Initializing cgroup subsys net_cls
[    0.008832] Initializing cgroup subsys blkio
[    0.008839] Initializing cgroup subsys perf_event
[    0.008865] CPU: Physical Processor ID: 0
[    0.008866] CPU: Processor Core ID: 0
[    0.008868] mce: CPU supports 6 MCE banks
[    0.008876] CPU0: Thermal monitoring enabled (TM2)
[    0.008880] using mwait in idle threads.
[    0.011082] ACPI: Core revision 20110413
[    0.016008] ftrace: allocating 25728 entries in 101 pages
[    0.020398] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062072] CPU0: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 97000
[    0.152111]  #2
[    0.152114] smpboot cpu 2: start_ip = 97000
[    0.244082]  #3 Ok.
[    0.244084] smpboot cpu 3: start_ip = 97000
[    0.336026] Brought up 4 CPUs
[    0.336028] Total of 4 processors activated (21330.72 BogoMIPS).
[    0.338246] devtmpfs: initialized
[    0.338246] PM: Registering ACPI NVS region at cff7e000 (335872 bytes)
[    0.338246] print_constraints: dummy: 
[    0.338246] Time: 15:31:23  Date: 02/06/12
[    0.338246] NET: Registered protocol family 16
[    0.338246] Trying to unpack rootfs image as initramfs...
[    0.340035] ACPI: bus type pci registered
[    0.340095] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.340097] PCI: not using MMCONFIG
[    0.340098] PCI: Using configuration type 1 for base access
[    0.340722] bio: create slab <bio-0> at 0
[    0.341123] ACPI: EC: Look up EC in DSDT
[    0.342165] ACPI: Executed 1 blocks of module-level executable AML code
[    0.348248] ACPI: SSDT 00000000cff7e0d0 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.348494] ACPI: Dynamic OEM Table Load:
[    0.348496] ACPI: SSDT           (null) 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.348675] ACPI: SSDT 00000000cff7e310 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.348919] ACPI: Dynamic OEM Table Load:
[    0.348922] ACPI: SSDT           (null) 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.349102] ACPI: SSDT 00000000cff7e550 00235 (v01 DpgPmm  P003Ist 00000012 INTL 20060113)
[    0.349347] ACPI: Dynamic OEM Table Load:
[    0.349350] ACPI: SSDT           (null) 00235 (v01 DpgPmm  P003Ist 00000012 INTL 20060113)
[    0.349530] ACPI: SSDT 00000000cff7e790 00235 (v01 DpgPmm  P004Ist 00000012 INTL 20060113)
[    0.349778] ACPI: Dynamic OEM Table Load:
[    0.349781] ACPI: SSDT           (null) 00235 (v01 DpgPmm  P004Ist 00000012 INTL 20060113)
[    0.349914] ACPI: Interpreter enabled
[    0.349917] ACPI: (supports S0 S1 S3 S4 S5)
[    0.349934] ACPI: Using IOAPIC for interrupt routing
[    0.349953] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.350753] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.389740] ACPI: No dock devices found.
[    0.389743] HEST: Table not found.
[    0.389746] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.389809] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.389937] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.389940] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.389942] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.389944] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.389946] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.389948] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.389959] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.389991] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.390015] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.390017] pci 0000:00:01.0: PME# disabled
[    0.390049] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.390086] pci 0000:00:1a.0: reg 20: [io  0xb800-0xb81f]
[    0.390123] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.390161] pci 0000:00:1a.1: reg 20: [io  0xb880-0xb89f]
[    0.390198] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.390234] pci 0000:00:1a.2: reg 20: [io  0xbc00-0xbc1f]
[    0.390278] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.390298] pci 0000:00:1a.7: reg 10: [mem 0xfe7ffc00-0xfe7fffff]
[    0.390361] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.390365] pci 0000:00:1a.7: PME# disabled
[    0.390386] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.390399] pci 0000:00:1b.0: reg 10: [mem 0xfe7f8000-0xfe7fbfff 64bit]
[    0.390444] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.390447] pci 0000:00:1b.0: PME# disabled
[    0.390465] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.390511] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.390514] pci 0000:00:1c.0: PME# disabled
[    0.390533] pci 0000:00:1c.4: [8086:3a48] type 1 class 0x000604
[    0.390581] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.390584] pci 0000:00:1c.4: PME# disabled
[    0.390601] pci 0000:00:1c.5: [8086:3a4a] type 1 class 0x000604
[    0.390647] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.390650] pci 0000:00:1c.5: PME# disabled
[    0.390670] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.390706] pci 0000:00:1d.0: reg 20: [io  0xb080-0xb09f]
[    0.390743] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.390781] pci 0000:00:1d.1: reg 20: [io  0xb400-0xb41f]
[    0.390818] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.390854] pci 0000:00:1d.2: reg 20: [io  0xb480-0xb49f]
[    0.390899] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.390917] pci 0000:00:1d.7: reg 10: [mem 0xfe7ff800-0xfe7ffbff]
[    0.390981] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.390985] pci 0000:00:1d.7: PME# disabled
[    0.391003] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.391050] pci 0000:00:1f.0: [8086:3a16] type 0 class 0x000601
[    0.391122] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.391127] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
[    0.391160] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.391176] pci 0000:00:1f.2: reg 10: [io  0xac00-0xac07]
[    0.391183] pci 0000:00:1f.2: reg 14: [io  0xa880-0xa883]
[    0.391189] pci 0000:00:1f.2: reg 18: [io  0xa800-0xa807]
[    0.391196] pci 0000:00:1f.2: reg 1c: [io  0xa480-0xa483]
[    0.391203] pci 0000:00:1f.2: reg 20: [io  0xa400-0xa41f]
[    0.391210] pci 0000:00:1f.2: reg 24: [mem 0xfe7fe800-0xfe7fefff]
[    0.391237] pci 0000:00:1f.2: PME# supported from D3hot
[    0.391240] pci 0000:00:1f.2: PME# disabled
[    0.391253] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.391266] pci 0000:00:1f.3: reg 10: [mem 0xfe7ff400-0xfe7ff4ff 64bit]
[    0.391284] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.391332] pci 0000:01:00.0: [1002:9440] type 0 class 0x000300
[    0.391344] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.391353] pci 0000:01:00.0: reg 18: [mem 0xfe8e0000-0xfe8effff 64bit]
[    0.391360] pci 0000:01:00.0: reg 20: [io  0xc000-0xc0ff]
[    0.391371] pci 0000:01:00.0: reg 30: [mem 0xfe8c0000-0xfe8dffff pref]
[    0.391386] pci 0000:01:00.0: supports D1 D2
[    0.391402] pci 0000:01:00.1: [1002:aa30] type 0 class 0x000403
[    0.391413] pci 0000:01:00.1: reg 10: [mem 0xfe8fc000-0xfe8fffff 64bit]
[    0.391451] pci 0000:01:00.1: supports D1 D2
[    0.391478] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.391481] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.391483] pci 0000:00:01.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.391487] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.391521] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.391525] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.391529] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.391534] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.391581] pci 0000:03:00.0: [11ab:6121] type 0 class 0x000101
[    0.391596] pci 0000:03:00.0: reg 10: [io  0xec00-0xec07]
[    0.391607] pci 0000:03:00.0: reg 14: [io  0xe880-0xe883]
[    0.391618] pci 0000:03:00.0: reg 18: [io  0xe800-0xe807]
[    0.391628] pci 0000:03:00.0: reg 1c: [io  0xe480-0xe483]
[    0.391639] pci 0000:03:00.0: reg 20: [io  0xe400-0xe40f]
[    0.391650] pci 0000:03:00.0: reg 24: [mem 0xfeaffc00-0xfeafffff]
[    0.391690] pci 0000:03:00.0: supports D1
[    0.391691] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.391696] pci 0000:03:00.0: PME# disabled
[    0.391711] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.391719] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.391722] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.391726] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.391731] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.391781] pci 0000:02:00.0: [1969:1026] type 0 class 0x000200
[    0.391802] pci 0000:02:00.0: reg 10: [mem 0xfe9c0000-0xfe9fffff 64bit]
[    0.391813] pci 0000:02:00.0: reg 18: [io  0xdc00-0xdc7f]
[    0.391890] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.391895] pci 0000:02:00.0: PME# disabled
[    0.391923] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.391931] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
[    0.391934] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.391937] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.391942] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.391974] pci 0000:05:03.0: [11c1:5811] type 0 class 0x000c00
[    0.391989] pci 0000:05:03.0: reg 10: [mem 0xfebff000-0xfebfffff]
[    0.392054] pci 0000:05:03.0: supports D1 D2
[    0.392055] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.392059] pci 0000:05:03.0: PME# disabled
[    0.392095] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.392099] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.392102] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.392108] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.392110] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.392112] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.392114] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.392116] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.392119] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.392121] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.392138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.392217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.392242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.392299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.392321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.392361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.392382]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.392385]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.392386] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.398157] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.398196] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.398232] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.398267] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.398303] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.398340] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.398376] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.398412] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.398512] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.398515] vgaarb: loaded
[    0.398516] vgaarb: bridge control possible 0000:01:00.0
[    0.398676] SCSI subsystem initialized
[    0.398726] libata version 3.00 loaded.
[    0.398726] usbcore: registered new interface driver usbfs
[    0.398726] usbcore: registered new interface driver hub
[    0.398726] usbcore: registered new device driver usb
[    0.398726] PCI: Using ACPI for IRQ routing
[    0.404093] PCI: pci_cache_line_size set to 64 bytes
[    0.404168] reserve RAM buffer: 000000000009cc00 - 000000000009ffff 
[    0.404171] reserve RAM buffer: 00000000cff70000 - 00000000cfffffff 
[    0.404259] NetLabel: Initializing
[    0.404261] NetLabel:  domain hash size = 128
[    0.404262] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.404272] NetLabel:  unlabeled traffic allowed by default
[    0.404310] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.404315] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.404319] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.412054] Switching to clocksource hpet
[    0.412147] Switched to NOHz mode on CPU #0
[    0.415930] Switched to NOHz mode on CPU #1
[    0.415784] Switched to NOHz mode on CPU #2
[    0.415839] Switched to NOHz mode on CPU #3
[    0.418013] AppArmor: AppArmor Filesystem Enabled
[    0.418042] pnp: PnP ACPI init
[    0.418056] ACPI: bus type pnp registered
[    0.418156] pnp 00:00: [bus 00-ff]
[    0.418159] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.418161] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.418163] pnp 00:00: [io  0x0d00-0xffff window]
[    0.418164] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.418166] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.418168] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    0.418170] pnp 00:00: [mem 0xf0000000-0xffffffff window]
[    0.418229] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.418237] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.418285] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.418288] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.418317] pnp 00:02: [dma 4]
[    0.418318] pnp 00:02: [io  0x0000-0x000f]
[    0.418320] pnp 00:02: [io  0x0081-0x0083]
[    0.418321] pnp 00:02: [io  0x0087]
[    0.418323] pnp 00:02: [io  0x0089-0x008b]
[    0.418325] pnp 00:02: [io  0x008f]
[    0.418326] pnp 00:02: [io  0x00c0-0x00df]
[    0.418344] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.418353] pnp 00:03: [io  0x0070-0x0071]
[    0.418363] pnp 00:03: [irq 8]
[    0.418381] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.418388] pnp 00:04: [io  0x0061]
[    0.418409] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.418417] pnp 00:05: [io  0x00f0-0x00ff]
[    0.418422] pnp 00:05: [irq 13]
[    0.418440] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.418644] pnp 00:06: [io  0x03f0-0x03f5]
[    0.418646] pnp 00:06: [io  0x03f7]
[    0.418651] pnp 00:06: [irq 6]
[    0.418652] pnp 00:06: [dma 2]
[    0.418697] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.418745] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.418747] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.418749] pnp 00:07: [io  0x0290-0x029f]
[    0.418783] system 00:07: [io  0x0290-0x029f] has been reserved
[    0.418786] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.418857] pnp 00:08: [io  0x0010-0x001f]
[    0.418859] pnp 00:08: [io  0x0022-0x003f]
[    0.418861] pnp 00:08: [io  0x0044-0x004d]
[    0.418862] pnp 00:08: [io  0x0050-0x005f]
[    0.418864] pnp 00:08: [io  0x0062-0x0063]
[    0.418865] pnp 00:08: [io  0x0065-0x006f]
[    0.418867] pnp 00:08: [io  0x0072-0x007f]
[    0.418868] pnp 00:08: [io  0x0080]
[    0.418870] pnp 00:08: [io  0x0084-0x0086]
[    0.418871] pnp 00:08: [io  0x0088]
[    0.418873] pnp 00:08: [io  0x008c-0x008e]
[    0.418874] pnp 00:08: [io  0x0090-0x009f]
[    0.418876] pnp 00:08: [io  0x00a2-0x00bf]
[    0.418877] pnp 00:08: [io  0x00e0-0x00ef]
[    0.418879] pnp 00:08: [io  0x04d0-0x04d1]
[    0.418880] pnp 00:08: [io  0x0800-0x087f]
[    0.418882] pnp 00:08: [io  0x0400-0x03ff disabled]
[    0.418883] pnp 00:08: [io  0x0500-0x057f]
[    0.418885] pnp 00:08: [mem 0xfed08000-0xfed08fff]
[    0.418887] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.418888] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.418890] pnp 00:08: [mem 0xfed50000-0xfed8ffff]
[    0.418940] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.418942] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.418944] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.418947] system 00:08: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.418949] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.418951] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.418954] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.418956] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419009] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.419032] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.419068] pnp 00:0a: [mem 0xffb00000-0xffbfffff]
[    0.419070] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.419091] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.419121] pnp 00:0b: [mem 0xffc00000-0xffefffff]
[    0.419155] system 00:0b: [mem 0xffc00000-0xffefffff] has been reserved
[    0.419158] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419327] pnp 00:0c: [io  0x03f8-0x03ff]
[    0.419332] pnp 00:0c: [irq 4]
[    0.419334] pnp 00:0c: [dma 0 disabled]
[    0.419386] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.419428] pnp 00:0d: [io  0x0000-0xffffffffffffffff disabled]
[    0.419430] pnp 00:0d: [io  0x0000-0xffffffffffffffff disabled]
[    0.419432] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.419433] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.419469] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.419472] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.419475] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419500] pnp 00:0e: [io  0x0060]
[    0.419502] pnp 00:0e: [io  0x0064]
[    0.419506] pnp 00:0e: [irq 1]
[    0.419531] pnp 00:0e: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.419565] pnp 00:0f: [irq 12]
[    0.419591] pnp 00:0f: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.419628] pnp 00:10: [mem 0xe0000000-0xefffffff]
[    0.419663] system 00:10: [mem 0xe0000000-0xefffffff] has been reserved
[    0.419665] system 00:10: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.419774] pnp 00:11: [mem 0x00000000-0x0009ffff]
[    0.419776] pnp 00:11: [mem 0x000c0000-0x000cffff]
[    0.419778] pnp 00:11: [mem 0x000e0000-0x000fffff]
[    0.419779] pnp 00:11: [mem 0x00100000-0xcfffffff]
[    0.419781] pnp 00:11: [mem 0xe0000000-0xffffffff]
[    0.419824] system 00:11: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.419827] system 00:11: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.419829] system 00:11: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.419832] system 00:11: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.419834] system 00:11: [mem 0xe0000000-0xffffffff] could not be reserved
[    0.419837] system 00:11: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.419934] pnp: PnP ACPI: found 18 devices
[    0.419935] ACPI: ACPI bus type pnp unregistered
[    0.425690] PCI: max bus depth: 1 pci_try_num: 2
[    0.425728] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.425731] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.425734] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0400000-0xf07fffff]
[    0.425737] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.425740] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.425742] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.425745] pci 0000:00:01.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.425748] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.425751] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.425754] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.425758] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf07fffff]
[    0.425762] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.425767] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.425770] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.425774] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.425777] pci 0000:00:1c.4:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.425782] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
[    0.425785] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.425789] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.425792] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.425797] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.425799] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.425803] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.425806] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.425824] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.425828] pci 0000:00:01.0: setting latency timer to 64
[    0.425833] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.425839] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.425842] pci 0000:00:1c.0: setting latency timer to 64
[    0.425847] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.425850] pci 0000:00:1c.4: setting latency timer to 64
[    0.425856] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.425859] pci 0000:00:1c.5: setting latency timer to 64
[    0.425864] pci 0000:00:1e.0: setting latency timer to 64
[    0.425867] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.425869] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.425871] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.425873] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.425875] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.425877] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
[    0.425879] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.425881] pci_bus 0000:01: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.425883] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.425885] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.425887] pci_bus 0000:04: resource 1 [mem 0xf0400000-0xf07fffff]
[    0.425889] pci_bus 0000:04: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.425891] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.425893] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.425895] pci_bus 0000:03: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.425897] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.425899] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.425901] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.425903] pci_bus 0000:05: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.425905] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.425907] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.425908] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.425910] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.425912] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.425914] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xffffffff]
[    0.425956] NET: Registered protocol family 2
[    0.426087] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.427037] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.430379] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.430593] TCP: Hash tables configured (established 524288 bind 65536)
[    0.430595] TCP reno registered
[    0.430603] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.430626] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.430741] NET: Registered protocol family 1
[    0.430888] pci 0000:01:00.0: Boot video device
[    0.430899] PCI: CLS 32 bytes, default 64
[    0.430901] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.430903] Placing 64MB software IO TLB between ffff8800cbf6a000 - ffff8800cff6a000
[    0.430905] software IO TLB at phys 0xcbf6a000 - 0xcff6a000
[    0.431235] audit: initializing netlink socket (disabled)
[    0.431242] type=2000 audit(1328542282.424:1): initialized
[    0.458462] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.478870] VFS: Disk quotas dquot_6.5.2
[    0.478919] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.479421] fuse init (API version 7.16)
[    0.479490] msgmni has been set to 7887
[    0.479912] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.479955] io scheduler noop registered
[    0.479957] io scheduler deadline registered
[    0.479987] io scheduler cfq registered (default)
[    0.480092] pcieport 0000:00:01.0: setting latency timer to 64
[    0.480120] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.480155] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.480186] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.480235] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.480265] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.480309] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.480339] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.480402] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.480419] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.480453] intel_idle: MWAIT substates: 0x22220
[    0.480454] intel_idle: does not run on family 6 model 23
[    0.480525] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.480530] ACPI: Power Button [PWRB]
[    0.480566] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.480569] ACPI: Power Button [PWRF]
[    0.480591] ACPI: acpi_idle registered with cpuidle
[    0.482445] ERST: Table is not found!
[    0.482491] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.502818] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.564178] Freeing initrd memory: 13416k freed
[    0.744428] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.744615] Linux agpgart interface v0.103
[    0.745562] brd: module loaded
[    0.745947] loop: module loaded
[    0.746065] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.746087] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.746098] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.746314] Fixed MDIO Bus: probed
[    0.746331] PPP generic driver version 2.4.2
[    0.746359] tun: Universal TUN/TAP device driver, 1.6
[    0.746360] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.746420] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.746436] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.746464] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.746467] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.746496] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.746523] ehci_hcd 0000:00:1a.7: debug port 1
[    0.750409] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.750424] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[    0.764012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.764124] hub 1-0:1.0: USB hub found
[    0.764134] hub 1-0:1.0: 6 ports detected
[    0.764194] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.764202] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.764205] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.764234] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.764254] ehci_hcd 0000:00:1d.7: debug port 1
[    0.768140] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.768151] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[    0.784012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.784121] hub 2-0:1.0: USB hub found
[    0.784125] hub 2-0:1.0: 6 ports detected
[    0.784184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.784193] uhci_hcd: USB Universal Host Controller Interface driver
[    0.784210] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.784214] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.784217] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.784243] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.784270] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    0.784354] hub 3-0:1.0: USB hub found
[    0.784358] hub 3-0:1.0: 2 ports detected
[    0.784406] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.784411] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.784413] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.784438] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.784466] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    0.784552] hub 4-0:1.0: USB hub found
[    0.784555] hub 4-0:1.0: 2 ports detected
[    0.784600] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.784605] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.784608] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.784632] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.784652] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    0.784736] hub 5-0:1.0: USB hub found
[    0.784739] hub 5-0:1.0: 2 ports detected
[    0.784782] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.784787] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.784789] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.784815] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.784835] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    0.784916] hub 6-0:1.0: USB hub found
[    0.784921] hub 6-0:1.0: 2 ports detected
[    0.784969] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.784974] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.784976] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.785005] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.785032] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.785115] hub 7-0:1.0: USB hub found
[    0.785118] hub 7-0:1.0: 2 ports detected
[    0.785166] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.785170] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.785173] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.785208] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.785228] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    0.785318] hub 8-0:1.0: USB hub found
[    0.785322] hub 8-0:1.0: 2 ports detected
[    0.785400] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.788098] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.788108] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.788269] mousedev: PS/2 mouse device common for all mice
[    0.788376] rtc_cmos 00:03: RTC can wake from S4
[    0.788460] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.788481] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.788589] device-mapper: uevent: version 1.0.3
[    0.788646] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.788655] cpuidle: using governor ladder
[    0.788657] cpuidle: using governor menu
[    0.788658] EFI Variables Facility v0.08 2004-May-17
[    0.788877] TCP cubic registered
[    0.788972] NET: Registered protocol family 10
[    0.789371] NET: Registered protocol family 17
[    0.789388] Registering the dns_resolver key type
[    0.789479] PM: Hibernation image not present or could not be loaded.
[    0.789489] registered taskstats version 1
[    0.804426]   Magic number: 0:493:537
[    0.804443] bdi 1:15: hash matches
[    0.804454] tty ttyS17: hash matches
[    0.804531] rtc_cmos 00:03: setting system clock to 2012-02-06 15:31:23 UTC (1328542283)
[    0.805358] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.805360] EDD information not available.
[    0.806884] Freeing unused kernel memory: 988k freed
[    0.807048] Write protecting the kernel read-only data: 12288k
[    0.813002] Freeing unused kernel memory: 2036k freed
[    0.817434] Freeing unused kernel memory: 1388k freed
[    0.820957] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.831664] udevd[88]: starting version 173
[    0.862072] ahci 0000:00:1f.2: version 3.0
[    0.862090] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.862143] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    0.862198] ahci: SSS flag set, parallel bus scan disabled
[    0.862234] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.862237] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.862241] ahci 0000:00:1f.2: setting latency timer to 64
[    0.866592] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.866607] ATL1E 0000:02:00.0: setting latency timer to 64
[    0.874694] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.889122] Floppy drive(s): fd0 is 1.44M
[    0.900614] scsi0 : ahci
[    0.900742] scsi1 : ahci
[    0.900832] scsi2 : ahci
[    0.900919] scsi3 : ahci
[    0.901009] scsi4 : ahci
[    0.901103] scsi5 : ahci
[    0.901237] ata1: SATA max UDMA/133 abar m2048@0xfe7fe800 port 0xfe7fe900 irq 44
[    0.901240] ata2: SATA max UDMA/133 abar m2048@0xfe7fe800 port 0xfe7fe980 irq 44
[    0.901242] ata3: SATA max UDMA/133 abar m2048@0xfe7fe800 port 0xfe7fea00 irq 44
[    0.901244] ata4: SATA max UDMA/133 abar m2048@0xfe7fe800 port 0xfe7fea80 irq 44
[    0.901247] ata5: SATA max UDMA/133 abar m2048@0xfe7fe800 port 0xfe7feb00 irq 44
[    0.901249] ata6: SATA max UDMA/133 abar m2048@0xfe7fe800 port 0xfe7feb80 irq 44
[    0.907748] FDC 0 is a post-1991 82077
[    0.928080] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    0.986306] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.986334] pata_marvell 0000:03:00.0: setting latency timer to 64
[    0.986633] scsi6 : pata_marvell
[    0.986719] scsi7 : pata_marvell
[    0.986760] ata7: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[    0.986762] ata8: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
[    1.148398] ata7.00: ATAPI: Optiarc DVD RW AD-7203A, 1.06, max UDMA/66
[    1.164380] ata7.00: configured for UDMA/66
[    1.264014] usb 2-4: new high speed USB device number 4 using ehci_hcd
[    1.392022] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.392254] ata1.00: ATA-8: Patriot Torqx TRB 64GB SSD, 100730, max UDMA/133
[    1.392257] ata1.00: 117980200 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.392507] ata1.00: configured for UDMA/133
[    1.392621] scsi 0:0:0:0: Direct-Access     ATA      Patriot Torqx TR 1007 PQ: 0 ANSI: 5
[    1.392769] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.392796] sd 0:0:0:0: [sda] 117980200 512-byte logical blocks: (60.4 GB/56.2 GiB)
[    1.392867] sd 0:0:0:0: [sda] Write Protect is off
[    1.392869] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.392887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.393480]  sda: sda1 sda2 < sda5 >
[    1.393753] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.402928] usbcore: registered new interface driver uas
[    1.428094] firewire_core: created device fw0: GUID 001e8c000198b68a, S400
[    1.448023] Refined TSC clocksource calibration: 2666.363 MHz.
[    1.448028] Switching to clocksource tsc
[    1.512012] usb 2-5: new high speed USB device number 5 using ehci_hcd
[    1.645502] hub 2-5:1.0: USB hub found
[    1.645827] hub 2-5:1.0: 4 ports detected
[    1.756014] usb 2-6: new high speed USB device number 6 using ehci_hcd
[    1.884012] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.885055] ata2.00: ATA-8: ST3500418AS, CC46, max UDMA/133
[    1.885058] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.886294] ata2.00: configured for UDMA/133
[    1.886386] scsi 1:0:0:0: Direct-Access     ATA      ST3500418AS      CC46 PQ: 0 ANSI: 5
[    1.886498] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.886553] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.886557] sd 1:0:0:0: [sdb] Write Protect is off
[    1.886559] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.886581] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.907686]  sdb: sdb1 sdb2
[    1.907888] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.256010] usb 6-2: new full speed USB device number 2 using uhci_hcd
[    2.376013] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.376184] ata3.00: ATA-8: OCZ-VERTEX, 1.6, max UDMA/133
[    2.376188] ata3.00: 125045424 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.376881] ata3.00: configured for UDMA/133
[    2.376992] scsi 2:0:0:0: Direct-Access     ATA      OCZ-VERTEX       1.6  PQ: 0 ANSI: 5
[    2.377134] sd 2:0:0:0: [sdc] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[    2.377155] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.377187] sd 2:0:0:0: [sdc] Write Protect is off
[    2.377190] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.377210] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.377620]  sdc: unknown partition table
[    2.377778] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.664008] usb 7-1: new low speed USB device number 2 using uhci_hcd
[    2.696013] ata4: SATA link down (SStatus 0 SControl 300)
[    3.016014] ata5: SATA link down (SStatus 0 SControl 300)
[    3.508011] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.509084] ata6.00: ATA-8: ST3500418AS, CC46, max UDMA/133
[    3.509088] ata6.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.510330] ata6.00: configured for UDMA/133
[    3.510417] scsi 5:0:0:0: Direct-Access     ATA      ST3500418AS      CC46 PQ: 0 ANSI: 5
[    3.510529] sd 5:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.510564] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.510575] sd 5:0:0:0: [sdd] Write Protect is off
[    3.510578] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.510595] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.512360] scsi 6:0:0:0: CD-ROM            Optiarc  DVD RW AD-7203A  1.06 PQ: 0 ANSI: 5
[    3.514654] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.514657] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.514773] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    3.514836] sr 6:0:0:0: Attached scsi generic sg4 type 5
[    3.532547]  sdd: unknown partition table
[    3.532683] sd 5:0:0:0: [sdd] Attached SCSI disk
[    3.679914] Initializing USB Mass Storage driver...
[    3.680474] usbcore: registered new interface driver usbhid
[    3.680476] usbhid: USB HID core driver
[    3.682342] scsi8 : usb-storage 2-4:1.0
[    3.682508] usbcore: registered new interface driver usb-storage
[    3.682510] USB Mass Storage support registered.
[    3.735438] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.735441] EXT4-fs (sda1): write access will be enabled during recovery
[    4.681234] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9328 PQ: 0 ANSI: 0
[    4.735985] scsi 8:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9328 PQ: 0 ANSI: 0
[    4.736723] scsi 8:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9328 PQ: 0 ANSI: 0
[    4.737360] scsi 8:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9328 PQ: 0 ANSI: 0
[    4.740588] sd 8:0:0:0: Attached scsi generic sg5 type 0
[    4.740747] sd 8:0:0:1: Attached scsi generic sg6 type 0
[    4.740919] sd 8:0:0:2: Attached scsi generic sg7 type 0
[    4.741222] sd 8:0:0:3: Attached scsi generic sg8 type 0
[    4.747734] sd 8:0:0:0: [sde] Attached SCSI removable disk
[    4.748345] sd 8:0:0:1: [sdf] Attached SCSI removable disk
[    4.748967] sd 8:0:0:3: [sdh] Attached SCSI removable disk
[    4.749591] sd 8:0:0:2: [sdg] Attached SCSI removable disk
[    5.442226] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.443836] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839377
[    5.444118] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839371
[    5.447142] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 915816
[    5.447198] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839375
[    5.447212] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839367
[    5.447225] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839364
[    5.447237] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839338
[    5.447249] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839325
[    5.447261] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839365
[    5.447272] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838950
[    5.447284] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839246
[    5.447296] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839361
[    5.447307] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839363
[    5.447318] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839362
[    5.447329] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839345
[    5.449039] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1833173
[    5.450323] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1833481
[    5.450343] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1833169
[    5.452132] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838795
[    5.452153] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838759
[    5.452169] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838804
[    5.452185] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838934
[    5.452227] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838943
[    5.455574] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1832054
[    5.455593] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838752
[    5.459645] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831694
[    5.459665] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838799
[    5.459680] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1832008
[    5.459699] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831819
[    5.459715] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838729
[    5.459731] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1832980
[    5.459747] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1838751
[    5.459762] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 915724
[    5.459772] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831527
[    5.459789] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839182
[    5.459805] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839175
[    5.459820] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 915726
[    5.459835] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831940
[    5.459852] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1832121
[    5.462507] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3271671
[    5.462528] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3271658
[    5.462547] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831697
[    5.462563] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831992
[    5.462579] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831929
[    5.462595] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831711
[    5.462610] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831689
[    5.462625] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1831709
[    5.462640] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839167
[    5.462661] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1839248
[    5.462676] EXT4-fs (sda1): 49 orphan inodes deleted
[    5.462678] EXT4-fs (sda1): recovery complete
[    5.511773] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.811332] udevd[414]: starting version 173
[    5.815131] Adding 4191228k swap on /dev/sda5.  Priority:-1 extents:1 across:4191228k SS
[    5.951627] lp: driver loaded but no devices found
[    5.976897] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    5.976902] Disabling lock debugging due to kernel taint
[    6.029767] type=1400 audit(1328542288.721:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=625 comm="apparmor_parser"
[    6.030090] type=1400 audit(1328542288.721:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=625 comm="apparmor_parser"
[    6.030296] type=1400 audit(1328542288.721:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=625 comm="apparmor_parser"
[    6.037973] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.038025] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    6.038052] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.050908] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.088258] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
[    6.088664] [fglrx]   vendor: 1002 device: 9440 count: 1
[    6.089504] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[    6.089520] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.089525] pci 0000:01:00.0: setting latency timer to 64
[    6.089805] [fglrx] Kernel PAT support is enabled
[    6.089824] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[    6.107940] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.108135] HDA Intel 0000:01:00.1: irq 46 for MSI/MSI-X
[    6.108160] HDA Intel 0000:01:00.1: setting latency timer to 64
[    6.136576] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[    6.136792] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input3
[    6.259754] input: Wacom Graphire2 4x5 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4
[    6.265667] logips2pp: Detected unknown logitech mouse model 62
[    6.268934] skipping empty audio interface (v1)
[    6.268969] snd-usb-audio: probe of 2-6:1.0 failed with error -5
[    6.268980] skipping empty audio interface (v1)
[    6.268985] snd-usb-audio: probe of 2-6:1.1 failed with error -5
[    6.272012] Linux video capture interface: v2.00
[    6.305119] usbcore: registered new interface driver wacom
[    6.305123] wacom: v1.52:USB Wacom tablet driver
[    6.394682] type=1400 audit(1328542289.085:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1064 comm="apparmor_parser"
[    6.395537] type=1400 audit(1328542289.085:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1064 comm="apparmor_parser"
[    6.395751] type=1400 audit(1328542289.085:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1064 comm="apparmor_parser"
[    6.398170] type=1400 audit(1328542289.089:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1063 comm="apparmor_parser"
[    6.399186] type=1400 audit(1328542289.089:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1069 comm="apparmor_parser"
[    6.400502] type=1400 audit(1328542289.093:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1072 comm="apparmor_parser"
[    6.403268] type=1400 audit(1328542289.093:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1069 comm="apparmor_parser"
[    6.521463] init: failsafe main process (1017) killed by TERM signal
[    6.521800] init: apport pre-start process (1124) terminated with status 1
[    6.527526] init: apport post-stop process (1151) terminated with status 1
[    6.554305] ATL1E 0000:02:00.0: irq 47 for MSI/MSI-X
[    6.554435] ATL1E 0000:02:00.0: eth0: NIC Link is Up <100 Mbps Full Duplex>
[    6.554796] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.555150] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    6.557331] /dev/vmmon[1174]: Module vmmon: registered with major=10 minor=165
[    6.557341] /dev/vmmon[1174]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[    6.557346] /dev/vmmon[1174]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[    6.557349] /dev/vmmon[1174]: Module vmmon: initialized

```


Can anyone help me?

thanks in advance and forgive for my english!

---

### Post by dino99 on 2012-02-08
your log show lot of errors like this one:

EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode ....

i dont know how you have installed ubuntu & formated your partitions. Here is how i do installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

to get a clean installation, better to follow this howto rather than trying to fix your borkrd one.

---

### Post by Mark Phelps on 2012-02-09
You could try booting from an Ubuntu desktop CD, selecting Try Ubuntu, and once you get to a desktop, open Disk Utility and use the option to run a Check on the Linux filesystem partitions on your drive.

If you do this and repeatedly encounter filesystem errors, that is an indication that your drive is failing.

---

### Post by TheMicZ on 2012-02-09
Thanks for the help. 
I think I have a problem with my SSD, because although I reinstalled my OS, I have the same problems!

I will try your tips. Thanks for now.

---

### Post by TheMicZ on 2012-02-09
I am back! :D

I tried many times to check the filesystem on my SSD from the live Ubuntu... and I always receive this reply: 

```
File system check on "56 GB Filesystem" (Partition 1 of ATA Patriot Torqx TRB 64GB SSD) completed
File system is clean.
```

I will try to install Ubuntu on a simple HD.


p.s.; the test smart data say to me that the SSD works perfectly: "**disk is healtly**"

---

