---
title: "Ubuntu 11.10 freeze"
date: 2011-10-19
forum: General Help
---

### Post by donniezazen on 2011-10-19
Hi,

Ubuntu is freezing on me without break. The system is pretty much useless. I have to hard reboot it.

Thanks.

---

### Post by donniezazen on 2011-10-21
Here is dmesg log. Please Help.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=f01ed762-2568-487f-86ae-300e813f9ae6 ro quiet splash pcie_aspm=force i915.i915_enable_rc6=1 vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000ba99f000 (usable)
[    0.000000]  BIOS-e820: 00000000ba99f000 - 00000000bae9f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae9f000 - 00000000baf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000baf9f000 - 00000000bafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bafff000 - 00000000bb000000 (usable)
[    0.000000]  BIOS-e820: 00000000bb000000 - 00000000bfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed08000 - 00000000fed09000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd20000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000023e600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: LENOVO 4177CTO/4177CTO, BIOS 83ET64WW (1.34 ) 09/08/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x23e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 23F000000 mask FFF000000 uncachable
[    0.000000]   8 base 23E800000 mask FFF800000 uncachable
[    0.000000]   9 base 23E600000 mask FFFE00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb000000
[    0.000000]  0000000000 - 00bb000000 page 2M
[    0.000000] kernel direct mapping tables up to bb000000 @ ba99b000-ba99f000
[    0.000000] init_memory_mapping: 0000000100000000-000000023e600000
[    0.000000]  0100000000 - 023e600000 page 2M
[    0.000000] kernel direct mapping tables up to 23e600000 @ 23e5f6000-23e600000
[    0.000000] RAMDISK: 365b8000 - 372d4000
[    0.000000] ACPI: RSDP 00000000000f00e0 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000baffe120 000AC (v01 LENOVO TP-83    00001340 PTEC 00000002)
[    0.000000] ACPI: FACP 00000000bafe8000 000F4 (v04 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000bafeb000 0E3EA (v01 LENOVO TP-83    00001340 INTL 20061109)
[    0.000000] ACPI: FACS 00000000baf2d000 00040
[    0.000000] ACPI: SLIC 00000000baffd000 00176 (v01 LENOVO TP-83    00001340 PTEC 00000001)
[    0.000000] ACPI: SSDT 00000000baffc000 00249 (v01 LENOVO TP-SSDT2 00000200 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000baffb000 00033 (v01 LENOVO TP-SSDT1 00000100 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000baffa000 00797 (v01 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: HPET 00000000bafe7000 00038 (v01 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: APIC 00000000bafe6000 00098 (v01 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000bafe5000 0003C (v01 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: ECDT 00000000bafe4000 00052 (v01 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: ASF! 00000000bafea000 000A5 (v32 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: TCPA 00000000bafe3000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT 00000000bafe2000 00A69 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe1000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: DMAR 00000000bafe0000 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 00000000bafdf000 0003E (v01 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafde000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000bafdd000 00292 (v01 LENOVO TP-83    00001340 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000023e600000
[    0.000000] Initmem setup node 0 0000000000000000-000000023e600000
[    0.000000]   NODE_DATA [000000023e5fb000 - 000000023e5fffff]
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880235c00000-ffff88023cbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0023e600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000ba99f
[    0.000000]     0: 0x000bafff -> 0x000bb000
[    0.000000]     0: 0x00100000 -> 0x0023e600
[    0.000000] On node 0 totalpages: 2067245
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 744920 pages, LIFO batch:31
[    0.000000]   Normal zone: 17829 pages used for memmap
[    0.000000]   Normal zone: 1286235 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000ba99f000 - 00000000bae9f000
[    0.000000] PM: Registered nosave memory: 00000000bae9f000 - 00000000baf9f000
[    0.000000] PM: Registered nosave memory: 00000000baf9f000 - 00000000bafff000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed08000
[    0.000000] PM: Registered nosave memory: 00000000fed08000 - 00000000fed09000
[    0.000000] PM: Registered nosave memory: 00000000fed09000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd20000
[    0.000000] PM: Registered nosave memory: 00000000ffd20000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:38600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88023e200000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2035075
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=f01ed762-2568-487f-86ae-300e813f9ae6 ro quiet splash pcie_aspm=force i915.i915_enable_rc6=1 vt.handoff=7
[    0.000000] PCIe ASPM is forcedly enabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.000000] Memory: 8060364k/9410560k available (6104k kernel code, 1141580k absent, 208616k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2691.655 MHz processor.
[    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5383.31 BogoMIPS (lpj=10766620)
[    0.000016] pid_max: default: 32768 minimum: 301
[    0.000070] Security Framework initialized
[    0.000101] AppArmor: AppArmor initialized
[    0.000104] Yama: becoming mindful.
[    0.002280] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.007436] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009511] Mount-cache hash table entries: 256
[    0.009764] Initializing cgroup subsys cpuacct
[    0.009776] Initializing cgroup subsys memory
[    0.009791] Initializing cgroup subsys devices
[    0.009796] Initializing cgroup subsys freezer
[    0.009800] Initializing cgroup subsys net_cls
[    0.009804] Initializing cgroup subsys blkio
[    0.009817] Initializing cgroup subsys perf_event
[    0.009877] Disabled fast string operations
[    0.009883] CPU: Physical Processor ID: 0
[    0.009886] CPU: Processor Core ID: 0
[    0.009898] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.009901] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.009908] mce: CPU supports 7 MCE banks
[    0.009938] CPU0: Thermal monitoring enabled (TM1)
[    0.009953] using mwait in idle threads.
[    0.014650] ACPI: Core revision 20110413
[    0.034613] ftrace: allocating 25651 entries in 101 pages
[    0.056821] DMAR: Host address width 36
[    0.056827] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.056843] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.056848] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.056861] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.056866] DMAR: RMRR base: 0x000000bacd5000 end: 0x000000bacebfff
[    0.056870] DMAR: RMRR base: 0x000000bb800000 end: 0x000000bf9fffff
[    0.056874] DMAR: No ATSR found
[    0.056956] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.056960] HPET id 0 under DRHD base 0xfed91000
[    0.056963] HPET id 0 under DRHD base 0xfed91000
[    0.056966] HPET id 0 under DRHD base 0xfed91000
[    0.056969] HPET id 0 under DRHD base 0xfed91000
[    0.056972] HPET id 0 under DRHD base 0xfed91000
[    0.056975] HPET id 0 under DRHD base 0xfed91000
[    0.056979] HPET id 0 under DRHD base 0xfed91000
[    0.056982] HPET id 0 under DRHD base 0xfed91000
[    0.057512] Enabled IRQ remapping in x2apic mode
[    0.057516] Enabling x2apic
[    0.057519] Enabled x2apic
[    0.057527] Switched APIC routing to cluster x2apic.
[    0.058006] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.097651] CPU0: Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz stepping 07
[    0.201957] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.201972] ... version:                3
[    0.201975] ... bit width:              48
[    0.201978] ... generic registers:      4
[    0.201981] ... value mask:             0000ffffffffffff
[    0.201985] ... max period:             000000007fffffff
[    0.201988] ... fixed-purpose events:   3
[    0.201992] ... event mask:             000000070000000f
[    0.203021] Booting Node   0, Processors  #1
[    0.203028] smpboot cpu 1: start_ip = 98000
[    0.293860] Disabled fast string operations
[    0.314150]  #2
[    0.314155] smpboot cpu 2: start_ip = 98000
[    0.401715] Disabled fast string operations
[    0.421992]  #3
[    0.421996] smpboot cpu 3: start_ip = 98000
[    0.509569] Disabled fast string operations
[    0.529680] Brought up 4 CPUs
[    0.529686] Total of 4 processors activated (21530.58 BogoMIPS).
[    0.536975] devtmpfs: initialized
[    0.537286] PM: Registering ACPI NVS region at bae9f000 (1048576 bytes)
[    0.540909] print_constraints: dummy: 
[    0.540948] Time:  8:11:13  Date: 10/21/11
[    0.541025] NET: Registered protocol family 16
[    0.541251] Trying to unpack rootfs image as initramfs...
[    0.541270] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.541276] ACPI: bus type pci registered
[    0.541781] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.541789] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.578010] PCI: Using configuration type 1 for base access
[    0.579705] bio: create slab <bio-0> at 0
[    0.584355] ACPI: EC: EC description table is found, configuring boot EC
[    0.596807] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.703200] ACPI: SSDT 00000000bae8c018 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.704352] ACPI: Dynamic OEM Table Load:
[    0.704359] ACPI: SSDT           (null) 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.733861] ACPI: SSDT 00000000bae8da98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.735078] ACPI: Dynamic OEM Table Load:
[    0.735084] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.765451] ACPI: SSDT 00000000bae8bd98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.766587] ACPI: Dynamic OEM Table Load:
[    0.766593] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.798571] ACPI: Interpreter enabled
[    0.798579] ACPI: (supports S0 S3 S4 S5)
[    0.798630] ACPI: Using IOAPIC for interrupt routing
[    0.845902] ACPI: Power Resource [PUBS] (on)
[    0.851887] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.853682] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.853688] HEST: Table not found.
[    0.853694] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.853980] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.854103] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.854109] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.854115] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.854123] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xfebfffff]
[    0.854128] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed4bfff]
[    0.854157] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.854241] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.854307] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.854314] pci 0000:00:01.0: PME# disabled
[    0.854362] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    0.854391] pci 0000:00:02.0: reg 10: [mem 0xf1400000-0xf17fffff 64bit]
[    0.854407] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.854420] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    0.854544] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.854593] pci 0000:00:16.0: reg 10: [mem 0xf2925000-0xf292500f 64bit]
[    0.854723] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.854732] pci 0000:00:16.0: PME# disabled
[    0.854801] pci 0000:00:19.0: [8086:1502] type 0 class 0x000200
[    0.854846] pci 0000:00:19.0: reg 10: [mem 0xf2900000-0xf291ffff]
[    0.854867] pci 0000:00:19.0: reg 14: [mem 0xf292b000-0xf292bfff]
[    0.854888] pci 0000:00:19.0: reg 18: [io  0x5080-0x509f]
[    0.855008] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.855017] pci 0000:00:19.0: PME# disabled
[    0.855073] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.855118] pci 0000:00:1a.0: reg 10: [mem 0xf292a000-0xf292a3ff]
[    0.855272] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.855280] pci 0000:00:1a.0: PME# disabled
[    0.855331] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.855368] pci 0000:00:1b.0: reg 10: [mem 0xf2920000-0xf2923fff 64bit]
[    0.855503] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.855512] pci 0000:00:1b.0: PME# disabled
[    0.855558] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.855704] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.855713] pci 0000:00:1c.0: PME# disabled
[    0.855763] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.855910] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.855919] pci 0000:00:1c.1: PME# disabled
[    0.855976] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    0.856122] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.856131] pci 0000:00:1c.4: PME# disabled
[    0.856198] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.856243] pci 0000:00:1d.0: reg 10: [mem 0xf2929000-0xf29293ff]
[    0.856397] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.856406] pci 0000:00:1d.0: PME# disabled
[    0.856453] pci 0000:00:1f.0: [8086:1c4f] type 0 class 0x000601
[    0.856676] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.856725] pci 0000:00:1f.2: reg 10: [io  0x50a8-0x50af]
[    0.856746] pci 0000:00:1f.2: reg 14: [io  0x50bc-0x50bf]
[    0.856767] pci 0000:00:1f.2: reg 18: [io  0x50a0-0x50a7]
[    0.856787] pci 0000:00:1f.2: reg 1c: [io  0x50b8-0x50bb]
[    0.856808] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    0.856829] pci 0000:00:1f.2: reg 24: [mem 0xf2928000-0xf29287ff]
[    0.856916] pci 0000:00:1f.2: PME# supported from D3hot
[    0.856925] pci 0000:00:1f.2: PME# disabled
[    0.856968] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.857007] pci 0000:00:1f.3: reg 10: [mem 0xf2924000-0xf29240ff 64bit]
[    0.857060] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    0.857210] pci 0000:01:00.0: [10de:1057] type 0 class 0x000300
[    0.857233] pci 0000:01:00.0: reg 10: [mem 0xf0000000-0xf0ffffff]
[    0.857258] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.857285] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.857303] pci 0000:01:00.0: reg 24: [io  0x4000-0x407f]
[    0.857320] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    0.865096] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.865103] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.865110] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.865120] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.865226] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.865236] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.865246] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.865263] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.865650] pci 0000:03:00.0: [8086:0084] type 0 class 0x000280
[    0.866012] pci 0000:03:00.0: reg 10: [mem 0xf2800000-0xf2801fff 64bit]
[    0.867440] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.867497] pci 0000:03:00.0: PME# disabled
[    0.873208] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.873218] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.873227] pci 0000:00:1c.1:   bridge window [mem 0xf2800000-0xf28fffff]
[    0.873242] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.873390] pci 0000:0d:00.0: [1180:e823] type 0 class 0x000805
[    0.873434] pci 0000:0d:00.0: reg 10: [mem 0xf2000000-0xf20000ff]
[    0.873643] pci 0000:0d:00.0: supports D1 D2
[    0.873647] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.873657] pci 0000:0d:00.0: PME# disabled
[    0.881085] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.881095] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.881105] pci 0000:00:1c.4:   bridge window [mem 0xf2000000-0xf27fffff]
[    0.881119] pci 0000:00:1c.4:   bridge window [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.881167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.881374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[    0.881442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.881499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.881560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.881876]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.882268]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.882273] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.887159] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.887297] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11)
[    0.887429] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.887557] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.887684] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11)
[    0.887792] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.887929] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11)
[    0.888057] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11)
[    0.888254] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.888273] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.888280] vgaarb: loaded
[    0.888283] vgaarb: bridge control possible 0000:01:00.0
[    0.888286] vgaarb: bridge control possible 0000:00:02.0
[    0.888652] SCSI subsystem initialized
[    0.888786] libata version 3.00 loaded.
[    0.888880] usbcore: registered new interface driver usbfs
[    0.888901] usbcore: registered new interface driver hub
[    0.888975] usbcore: registered new device driver usb
[    0.889161] PCI: Using ACPI for IRQ routing
[    0.893294] PCI: pci_cache_line_size set to 64 bytes
[    0.893490] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.893496] reserve RAM buffer: 00000000ba99f000 - 00000000bbffffff 
[    0.893502] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
[    0.893507] reserve RAM buffer: 000000023e600000 - 000000023fffffff 
[    0.893692] NetLabel: Initializing
[    0.893696] NetLabel:  domain hash size = 128
[    0.893699] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.893721] NetLabel:  unlabeled traffic allowed by default
[    0.893803] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.893818] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.895845] Switching to clocksource hpet
[    0.897044] Switched to NOHz mode on CPU #0
[    0.897215] Switched to NOHz mode on CPU #3
[    0.897229] Switched to NOHz mode on CPU #2
[    0.897236] Switched to NOHz mode on CPU #1
[    0.907712] AppArmor: AppArmor Filesystem Enabled
[    0.907755] pnp: PnP ACPI init
[    0.907780] ACPI: bus type pnp registered
[    0.908653] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.908659] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    0.908663] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    0.908667] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    0.908671] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.908675] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    0.908680] pnp 00:00: [mem 0x000d4000-0x000d7fff]
[    0.908684] pnp 00:00: [mem 0x000d8000-0x000dbfff]
[    0.908688] pnp 00:00: [mem 0x000dc000-0x000dffff]
[    0.908692] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    0.908696] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    0.908700] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    0.908704] pnp 00:00: [mem 0x000ec000-0x000effff]
[    0.908709] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.908713] pnp 00:00: [mem 0x00100000-0xbf9fffff]
[    0.908717] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    0.908722] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    0.908837] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.908844] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.908849] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.908855] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.908860] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.908866] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.908871] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    0.908881] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    0.908887] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    0.908893] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.908898] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.908904] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.908909] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.908915] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.908920] system 00:00: [mem 0x00100000-0xbf9fffff] could not be reserved
[    0.908927] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.908933] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.908941] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.908991] pnp 00:01: [bus 00-fe]
[    0.908996] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.909001] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.909005] pnp 00:01: [io  0x0d00-0xffff window]
[    0.909010] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.909015] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    0.909020] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    0.909025] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    0.909029] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    0.909034] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    0.909038] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    0.909043] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    0.909047] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    0.909052] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    0.909057] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    0.909061] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    0.909066] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    0.909070] pnp 00:01: [mem 0xbfa00000-0xfebfffff window]
[    0.909075] pnp 00:01: [mem 0xfed40000-0xfed4bfff window]
[    0.909183] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.909329] pnp 00:02: [io  0x0010-0x001f]
[    0.909334] pnp 00:02: [io  0x0090-0x009f]
[    0.909338] pnp 00:02: [io  0x0024-0x0025]
[    0.909341] pnp 00:02: [io  0x0028-0x0029]
[    0.909345] pnp 00:02: [io  0x002c-0x002d]
[    0.909353] pnp 00:02: [io  0x0030-0x0031]
[    0.909357] pnp 00:02: [io  0x0034-0x0035]
[    0.909361] pnp 00:02: [io  0x0038-0x0039]
[    0.909365] pnp 00:02: [io  0x003c-0x003d]
[    0.909369] pnp 00:02: [io  0x00a4-0x00a5]
[    0.909373] pnp 00:02: [io  0x00a8-0x00a9]
[    0.909377] pnp 00:02: [io  0x00ac-0x00ad]
[    0.909381] pnp 00:02: [io  0x00b0-0x00b5]
[    0.909384] pnp 00:02: [io  0x00b8-0x00b9]
[    0.909388] pnp 00:02: [io  0x00bc-0x00bd]
[    0.909392] pnp 00:02: [io  0x0050-0x0053]
[    0.909396] pnp 00:02: [io  0x0072-0x0077]
[    0.909400] pnp 00:02: [io  0x0400-0x047f]
[    0.909404] pnp 00:02: [io  0x0500-0x057f]
[    0.909408] pnp 00:02: [io  0x0800-0x080f]
[    0.909412] pnp 00:02: [io  0x15e0-0x15ef]
[    0.909416] pnp 00:02: [io  0x1600-0x167f]
[    0.909420] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    0.909424] pnp 00:02: [mem 0x00000000-0x00000fff]
[    0.909429] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    0.909433] pnp 00:02: [mem 0xfed10000-0xfed13fff]
[    0.909437] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.909441] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.909445] pnp 00:02: [mem 0xfed45000-0xfed4bfff]
[    0.909570] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.909576] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.909581] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.909586] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.909592] system 00:02: [io  0x1600-0x167f] has been reserved
[    0.909598] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.909604] system 00:02: [mem 0x00000000-0x00000fff] could not be reserved
[    0.909610] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.909616] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.909621] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.909627] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.909633] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.909640] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.909747] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.909803] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.909824] pnp 00:04: [io  0x0000-0x000f]
[    0.909828] pnp 00:04: [io  0x0080-0x008f]
[    0.909832] pnp 00:04: [io  0x00c0-0x00df]
[    0.909837] pnp 00:04: [dma 4]
[    0.909887] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.909904] pnp 00:05: [io  0x0061]
[    0.909961] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.909979] pnp 00:06: [io  0x00f0]
[    0.910002] pnp 00:06: [irq 13]
[    0.910055] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.910073] pnp 00:07: [io  0x0070-0x0071]
[    0.910087] pnp 00:07: [irq 8]
[    0.910138] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.910157] pnp 00:08: [io  0x0060]
[    0.910161] pnp 00:08: [io  0x0064]
[    0.910173] pnp 00:08: [irq 1]
[    0.910230] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.910258] pnp 00:09: [irq 12]
[    0.910314] pnp 00:09: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.910385] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.910443] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.911126] pnp: PnP ACPI: found 11 devices
[    0.911130] ACPI: ACPI bus type pnp unregistered
[    0.918360] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.918371] PCI: max bus depth: 1 pci_try_num: 2
[    0.918446] pci 0000:01:00.0: BAR 6: assigned [mem 0xf1000000-0xf107ffff pref]
[    0.918453] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.918459] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.918467] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.918475] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.918484] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.918489] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.918501] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.918510] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.918524] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.918528] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.918540] pci 0000:00:1c.1:   bridge window [mem 0xf2800000-0xf28fffff]
[    0.918549] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.918564] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.918571] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.918583] pci 0000:00:1c.4:   bridge window [mem 0xf2000000-0xf27fffff]
[    0.918593] pci 0000:00:1c.4:   bridge window [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.918636] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.918645] pci 0000:00:01.0: setting latency timer to 64
[    0.918659] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.918671] pci 0000:00:1c.0: setting latency timer to 64
[    0.918695] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.918705] pci 0000:00:1c.1: setting latency timer to 64
[    0.918720] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.918729] pci 0000:00:1c.4: setting latency timer to 64
[    0.918738] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.918743] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.918748] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.918753] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfebfffff]
[    0.918758] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff]
[    0.918763] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.918768] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf10fffff]
[    0.918773] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.918779] pci_bus 0000:03: resource 1 [mem 0xf2800000-0xf28fffff]
[    0.918784] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff]
[    0.918788] pci_bus 0000:0d: resource 1 [mem 0xf2000000-0xf27fffff]
[    0.918793] pci_bus 0000:0d: resource 2 [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.918859] NET: Registered protocol family 2
[    0.919473] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.924796] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.928464] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.928783] TCP: Hash tables configured (established 524288 bind 65536)
[    0.928787] TCP reno registered
[    0.928831] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.928930] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.929172] NET: Registered protocol family 1
[    0.929204] pci 0000:00:02.0: Boot video device
[    0.929410] PCI: CLS 64 bytes, default 64
[    0.929421] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.929426] Placing 64MB software IO TLB between ffff8800b699b000 - ffff8800ba99b000
[    0.929431] software IO TLB at phys 0xb699b000 - 0xba99b000
[    0.930340] audit: initializing netlink socket (disabled)
[    0.930357] type=2000 audit(1319184673.756:1): initialized
[    1.005418] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.047385] VFS: Disk quotas dquot_6.5.2
[    1.047505] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.048782] fuse init (API version 7.16)
[    1.048969] msgmni has been set to 15742
[    1.049761] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.049822] io scheduler noop registered
[    1.049829] io scheduler deadline registered
[    1.049920] io scheduler cfq registered (default)
[    1.050107] pcieport 0000:00:01.0: setting latency timer to 64
[    1.050178] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    1.050591] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.050638] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.050721] intel_idle: MWAIT substates: 0x21120
[    1.050725] intel_idle: v0.4 model 0x2A
[    1.050728] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.051034] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.051262] ACPI: AC Adapter [AC] (off-line)
[    1.051650] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.051857] ACPI: Lid Switch [LID]
[    1.051936] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.051946] ACPI: Sleep Button [SLPB]
[    1.052038] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.052045] ACPI: Power Button [PWRF]
[    1.052124] ACPI: acpi_idle yielding to intel_idle
[    1.062019] thermal LNXTHERM:00: registered as thermal_zone0
[    1.062025] ACPI: Thermal Zone [THM0] (50 C)
[    1.062066] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.062104] ERST: Table is not found!
[    1.062220] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.074857] ACPI: Battery Slot [BAT0] (battery present)
[    1.236485] Freeing initrd memory: 13424k freed
[    1.308325] Linux agpgart interface v0.103
[    1.308516] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.308861] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.312776] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.312989] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.314962] brd: module loaded
[    1.315919] loop: module loaded
[    1.316719] Fixed MDIO Bus: probed
[    1.316763] PPP generic driver version 2.4.2
[    1.316830] tun: Universal TUN/TAP device driver, 1.6
[    1.316834] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.316988] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.317020] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.317029] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.317045] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.317082] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.317090] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.317151] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.317200] ehci_hcd 0000:00:1a.0: debug port 2
[    1.321078] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.321116] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf292a000
[    1.335714] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.335939] hub 1-0:1.0: USB hub found
[    1.335949] hub 1-0:1.0: 3 ports detected
[    1.336061] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.336070] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.336100] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.336129] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.336136] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.336206] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.336249] ehci_hcd 0000:00:1d.0: debug port 2
[    1.340126] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.340155] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf2929000
[    1.355686] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.355887] hub 2-0:1.0: USB hub found
[    1.355895] hub 2-0:1.0: 3 ports detected
[    1.356004] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.356026] uhci_hcd: USB Universal Host Controller Interface driver
[    1.356141] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.359501] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.359515] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.359808] mousedev: PS/2 mouse device common for all mice
[    1.360052] rtc_cmos 00:07: RTC can wake from S4
[    1.360218] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.360260] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.360477] device-mapper: uevent: version 1.0.3
[    1.360620] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.360897] cpuidle: using governor ladder
[    1.361308] cpuidle: using governor menu
[    1.361313] EFI Variables Facility v0.08 2004-May-17
[    1.361768] TCP cubic registered
[    1.362047] NET: Registered protocol family 10
[    1.363007] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.363276] NET: Registered protocol family 17
[    1.363304] Registering the dns_resolver key type
[    1.363471] PM: Hibernation image not present or could not be loaded.
[    1.363494] registered taskstats version 1
[    1.398217]   Magic number: 15:66:170
[    1.398281] acpi device:33: hash matches
[    1.398379] rtc_cmos 00:07: setting system clock to 2011-10-21 08:11:14 UTC (1319184674)
[    1.402091] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.402093] EDD information not available.
[    1.403211] Freeing unused kernel memory: 984k freed
[    1.403303] Write protecting the kernel read-only data: 10240k
[    1.403449] Freeing unused kernel memory: 20k freed
[    1.406025] Freeing unused kernel memory: 1400k freed
[    1.416499] udevd[87]: starting version 173
[    1.438110] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    1.438113] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.438148] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.438159] e1000e 0000:00:19.0: setting latency timer to 64
[    1.438267] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.450401] sdhci: Secure Digital Host Controller Interface driver
[    1.450404] sdhci: Copyright(c) Pierre Ossman
[    1.450613] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e823] (rev 5)
[    1.450637] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.450676] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    1.450688] mmc0: no vmmc regulator found
[    1.450713] Registered led device: mmc0::
[    1.451145] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    1.622937] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:21:cc:5d:6d:d0
[    1.622940] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.622975] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    1.622998] ahci 0000:00:1f.2: version 3.0
[    1.623022] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.623073] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.623121] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    1.623124] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.623128] ahci 0000:00:1f.2: setting latency timer to 64
[    1.627833] scsi0 : ahci
[    1.627956] scsi1 : ahci
[    1.628006] scsi2 : ahci
[    1.628056] scsi3 : ahci
[    1.628108] scsi4 : ahci
[    1.628152] scsi5 : ahci
[    1.628454] ata1: SATA max UDMA/133 abar m2048@0xf2928000 port 0xf2928100 irq 44
[    1.628457] ata2: SATA max UDMA/133 abar m2048@0xf2928000 port 0xf2928180 irq 44
[    1.628458] ata3: DUMMY
[    1.628459] ata4: DUMMY
[    1.628460] ata5: DUMMY
[    1.628460] ata6: DUMMY
[    1.647412] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.780015] hub 1-1:1.0: USB hub found
[    1.780103] hub 1-1:1.0: 6 ports detected
[    1.891109] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.927045] Refined TSC clocksource calibration: 2691.258 MHz.
[    1.927057] Switching to clocksource tsc
[    1.947033] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.947097] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.948229] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.948240] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.948247] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.949461] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.949761] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.949772] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.951331] ata2.00: ATAPI: HL-DT-STDVDRAM GT33N, LT20, max UDMA/66
[    1.953811] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.953984] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.953992] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.955513] ata2.00: configured for UDMA/66
[    1.991089] ata1.00: ATA-8: ST9500420AS, 0003LVM1, max UDMA/100
[    1.991098] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.993277] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.993288] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.993295] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.995033] ata1.00: configured for UDMA/100
[    1.995207] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0003 PQ: 0 ANSI: 5
[    1.995343] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.995366] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.995394] sd 0:0:0:0: [sda] Write Protect is off
[    1.995397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.995411] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.996758] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT33N     LT20 PQ: 0 ANSI: 5
[    1.999678] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.999687] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.999830] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.999870] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.023526] hub 2-1:1.0: USB hub found
[    2.023627] hub 2-1:1.0: 8 ports detected
[    2.059976]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    2.060330] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.095002] usb 1-1.3: new full speed USB device number 3 using ehci_hcd
[    2.258602] usb 1-1.6: new high speed USB device number 4 using ehci_hcd
[    2.630170] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.282553] udevd[328]: starting version 173
[   13.304207] lp: driver loaded but no devices found
[   13.306644] coretemp coretemp.0: TjMax is 100 C.
[   13.306654] coretemp coretemp.0: TjMax is 100 C.
[   13.311443] [drm] Initialized drm 1.1.0 20060810
[   13.316369] i915 0000:00:02.0: power state changed by ACPI to D0
[   13.316373] i915 0000:00:02.0: power state changed by ACPI to D0
[   13.316380] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.316383] i915 0000:00:02.0: setting latency timer to 64
[   13.317064] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   13.322629] cfg80211: Calling CRDA to update world regulatory domain
[   13.323600] wmi: Mapper loaded
[   13.329025] Non-volatile memory driver v1.3
[   13.333437] Adding 16487420k swap on /dev/sda7.  Priority:-1 extents:1 across:16487420k 
[   13.336048] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.336051] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   13.336150] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.336159] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.336229] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.350448] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
[   13.357364] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   13.357367] iwlagn 0000:03:00.0: Device SKU: 0X9
[   13.357369] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.360769] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.360874] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[   13.364851] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   13.364856] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   13.364861] nouveau 0000:01:00.0: enabling device (0000 -> 0003)
[   13.364867] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.364872] nouveau 0000:01:00.0: setting latency timer to 64
[   13.384102] mtrr: no more MTRRs available
[   13.384105] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   13.396045] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   13.396050] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.396051] [drm] Driver supports precise vblank timestamp query.
[   13.396253] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[   13.396268] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.396270] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   13.429694] type=1400 audit(1319206286.544:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=588 comm="apparmor_parser"
[   13.429976] type=1400 audit(1319206286.544:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
[   13.430157] type=1400 audit(1319206286.544:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=588 comm="apparmor_parser"
[   13.467659] Linux video capture interface: v2.00
[   13.468122] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b221)
[   13.471733] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input4
[   13.471826] usbcore: registered new interface driver uvcvideo
[   13.471828] USB Video Class driver (v1.1.0)
[   13.489580] cfg80211: World regulatory domain updated:
[   13.489583] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.489586] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.489588] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.489589] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.489591] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.489593] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.491615] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   13.491618] thinkpad_acpi: http://ibm-acpi.sf.net/
[   13.491619] thinkpad_acpi: ThinkPad BIOS 83ET64WW (1.34 ), EC unknown
[   13.491621] thinkpad_acpi: Lenovo ThinkPad T420, model 4177CTO
[   13.491877] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   13.491992] thinkpad_acpi: radio switch found; radios are enabled
[   13.493370] Registered led device: tpacpi::thinklight
[   13.493428] Registered led device: tpacpi::power
[   13.493476] Registered led device: tpacpi::standby
[   13.493519] Registered led device: tpacpi::thinkvantage
[   13.493603] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   13.493763] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   13.494834] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input5
[   13.531621] fbcon: inteldrmfb (fb0) is primary device
[   13.532069] Console: switching to colour frame buffer device 170x48
[   13.532081] fb0: inteldrmfb frame buffer device
[   13.532082] drm: registered panic notifier
[   13.538035] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.538135] Registered led device: phy0-led
[   13.538155] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.540043] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.553299] acpi device:01: registered as cooling_device4
[   13.553620] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   13.553663] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   13.555031] acpi device:0b: registered as cooling_device5
[   13.555144] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input7
[   13.555177] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[   13.555223] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.555253] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.555262] mei 0000:00:16.0: setting latency timer to 64
[   13.557174] [drm] nouveau 0000:01:00.0: Unsupported chipset 0x0d9170a1
[   13.558779] nouveau 0000:01:00.0: PCI INT A disabled
[   13.558786] nouveau: probe of 0000:01:00.0 failed with error -22
[   13.563569] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.563642] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   13.563666] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.213240] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   14.213257] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.261743] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.268008] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   14.508513] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   15.016081] type=1400 audit(1319206288.132:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=957 comm="apparmor_parser"
[   15.016482] type=1400 audit(1319206288.132:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=958 comm="apparmor_parser"
[   15.016594] type=1400 audit(1319206288.132:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
[   15.016793] type=1400 audit(1319206288.132:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[   15.016896] type=1400 audit(1319206288.132:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=961 comm="apparmor_parser"
[   15.016988] type=1400 audit(1319206288.132:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[   15.019364] type=1400 audit(1319206288.136:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=959 comm="apparmor_parser"
[   15.047065] ppdev: user-space parallel port driver
[   15.105590] init: failsafe main process (900) killed by TERM signal
[   15.106084] init: apport pre-start process (1034) terminated with status 1
[   15.112391] init: apport post-stop process (1063) terminated with status 1
[   15.236108] Bluetooth: Core ver 2.16
[   15.236126] NET: Registered protocol family 31
[   15.236128] Bluetooth: HCI device and connection manager initialized
[   15.236129] Bluetooth: HCI socket layer initialized
[   15.236131] Bluetooth: L2CAP socket layer initialized
[   15.236470] Bluetooth: SCO socket layer initialized
[   15.237522] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.237526] Bluetooth: BNEP filters: protocol multicast
[   15.237632] Bluetooth: RFCOMM TTY layer initialized
[   15.237636] Bluetooth: RFCOMM socket layer initialized
[   15.237637] Bluetooth: RFCOMM ver 1.11
[   15.249880] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   15.305720] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   15.306210] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.336508] init: anacron main process (1062) killed by TERM signal
[   15.430872] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.575442] wlan0: authenticate with 00:21:91:fe:1d:eb (try 1)
[   17.578400] wlan0: authenticated
[   17.583796] wlan0: associate with 00:21:91:fe:1d:eb (try 1)
[   17.586728] wlan0: RX AssocResp from 00:21:91:fe:1d:eb (capab=0x431 status=0 aid=4)
[   17.586731] wlan0: associated
[   17.590734] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.863394] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=60
[   19.067478] EXT4-fs (sda5): re-mounted. Opts: commit=60
[   19.278937] init: plymouth-stop pre-start process (1497) terminated with status 1
[   20.712776] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.991216] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   29.667094] wlan0: no IPv6 routers present
```

---

### Post by linuxinstalledfromhdd on 2011-10-21
I would roll back to 10.10 for now until they can get the bugs out of this. 

I can't even change my user because "User Accounts" isn't fuctional today in Ubuntu 11.10. 

I'm going to go to Debian if this continues....

---

### Post by donniezazen on 2011-10-21
> **linuxinstalledfromhdd said:**
> I would roll back to 10.10 for now until they can get the bugs out of this. 

I can't even change my user because "User Accounts" isn't fuctional today in Ubuntu 11.10. 

I'm going to go to Debian if this continues....

That's depressing.

---

