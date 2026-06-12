---
title: "1 min 30'' boot time after upgrading to 11.04"
date: 2011-05-07
forum: General Help
---

### Post by vilxes91 on 2011-05-07
Good morning (At least in spain!)

I upgraded to 11.04 on April 29, and since then my boot time has gone from about 30 seconds to 1'30''. I have tried to disable the splash screen to see what happens, but I just don't have so much background in booting processes.

```
The dmesg shows something "strange":
[    2.489729] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   29.084441] <30>udev[318]: starting version 167
```
I don't know if that 30 seconds delay time are usual or not.

The complete dmesg is the following:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic-pae (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 (Ubuntu 2.6.38-8.42-generic-pae 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000be626000 (usable)
[    0.000000]  BIOS-e820: 00000000be626000 - 00000000be629000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000be629000 - 00000000bfca8000 (usable)
[    0.000000]  BIOS-e820: 00000000bfca8000 - 00000000bfcbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfcbf000 - 00000000bfd86000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd86000 - 00000000bfdbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfdea000 (usable)
[    0.000000]  BIOS-e820: 00000000bfdea000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv5 Notebook PC/3603, BIOS F.0C 09/18/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 base 0FFFE0000 mask FFFFE0000 write-protect
[    0.000000]   7 base 0FFFD8000 mask FFFFF8000 write-protect
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 36784000 - 373ba000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT bfdfe120 00064 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP bfdfd000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT bfded000 0B5FA (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS bfd92000 00040
[    0.000000] ACPI: HPET bfdfc000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC bfdfb000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG bfdfa000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! bfdf9000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC bfdec000 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: BOOT bfdeb000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT bfdea000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4228MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000be626
[    0.000000]     0: 0x000be629 -> 0x000bfca8
[    0.000000]     0: 0x000bfcbf -> 0x000bfd86
[    0.000000]     0: 0x000bfdbf -> 0x000bfdea
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1047846
[    0.000000] free_area_init_node: node 0, pgdat c17babc0, node_mem_map f3f84200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 811153 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u524288
[    0.000000] pcpu-alloc: s32320 r0 d20928 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1037605
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=fbd6926d-7840-4b70-a833-eaf53cd85ee1 ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 26214080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 4101596k/5242880k available (5349k kernel code, 89788k reserved, 2599k data, 720k init, 3278440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539545 - 0xc17c3540   (2599 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539545   (5349 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.056 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.11 BogoMIPS (lpj=7980224)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004040] Security Framework initialized
[    0.004059] AppArmor: AppArmor initialized
[    0.004064] Yama: becoming mindful.
[    0.004128] Mount-cache hash table entries: 512
[    0.004276] Initializing cgroup subsys ns
[    0.004283] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004291] Initializing cgroup subsys cpuacct
[    0.004299] Initializing cgroup subsys memory
[    0.004310] Initializing cgroup subsys devices
[    0.004314] Initializing cgroup subsys freezer
[    0.004319] Initializing cgroup subsys net_cls
[    0.004323] Initializing cgroup subsys blkio
[    0.004363] CPU: Physical Processor ID: 0
[    0.004367] CPU: Processor Core ID: 0
[    0.004372] mce: CPU supports 6 MCE banks
[    0.004383] CPU0: Thermal monitoring enabled (TM1)
[    0.004389] using mwait in idle threads.
[    0.008406] ACPI: Core revision 20110112
[    0.016014] ftrace: allocating 24250 entries in 48 pages
[    0.024061] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024406] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067305] CPU0: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] CPU 1 irqstacks, hard=f74d0000 soft=f74d2000
[    0.068003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.156026] Brought up 2 CPUs
[    0.156036] Total of 2 processors activated (7980.50 BogoMIPS).
[    0.156470] devtmpfs: initialized
[    0.157288] print_constraints: dummy: 
[    0.157323] Time: 10:10:23  Date: 05/07/11
[    0.157370] NET: Registered protocol family 16
[    0.157409] Trying to unpack rootfs image as initramfs...
[    0.157517] EISA bus registered
[    0.157540] ACPI: bus type pci registered
[    0.157627] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.157636] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.157641] PCI: Using MMCONFIG for extended config space
[    0.157646] PCI: Using configuration type 1 for base access
[    0.172092] bio: create slab <bio-0> at 0
[    0.175047] ACPI: EC: Look up EC in DSDT
[    0.177791] ACPI: Executed 1 blocks of module-level executable AML code
[    0.179996] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.312548] ACPI: SSDT bfcb4c18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.313247] ACPI: Dynamic OEM Table Load:
[    0.313254] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.313441] ACPI: SSDT bfcb2598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.314112] ACPI: Dynamic OEM Table Load:
[    0.314119] ACPI: SSDT   (null) 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.376437] ACPI: SSDT bfcb3e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.377164] ACPI: Dynamic OEM Table Load:
[    0.377172] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.408211] ACPI: SSDT bfcb4f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.408909] ACPI: Dynamic OEM Table Load:
[    0.408916] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.441008] ACPI: Interpreter enabled
[    0.441008] ACPI: (supports S0 S3 S4 S5)
[    0.441008] ACPI: Using IOAPIC for interrupt routing
[    0.450068] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.450321] ACPI: No dock devices found.
[    0.450327] HEST: Table not found.
[    0.450334] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.450815] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.451599] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.451607] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.451613] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.451621] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.451643] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.451674] DMAR: Forcing write-buffer flush capability
[    0.451678] DMAR: Disabling IOMMU for graphics on this chipset
[    0.451710] pci 0000:00:01.0: [8086:2a41] type 1 class 0x000604
[    0.451757] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.451761] pci 0000:00:01.0: PME# disabled
[    0.451820] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.451883] pci 0000:00:1a.0: reg 20: [io  0xa0e0-0xa0ff]
[    0.451949] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.452012] pci 0000:00:1a.1: reg 20: [io  0xa0c0-0xa0df]
[    0.452099] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.452129] pci 0000:00:1a.7: reg 10: [mem 0xdf305c00-0xdf305fff]
[    0.452234] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.452240] pci 0000:00:1a.7: PME# disabled
[    0.452272] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.452295] pci 0000:00:1b.0: reg 10: [mem 0xdf300000-0xdf303fff 64bit]
[    0.452377] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.452382] pci 0000:00:1b.0: PME# disabled
[    0.452411] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.452495] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.452500] pci 0000:00:1c.0: PME# disabled
[    0.452531] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.452614] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.452619] pci 0000:00:1c.1: PME# disabled
[    0.452650] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.452734] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.452740] pci 0000:00:1c.2: PME# disabled
[    0.452771] pci 0000:00:1c.3: [8086:2946] type 1 class 0x000604
[    0.452858] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.452863] pci 0000:00:1c.3: PME# disabled
[    0.452894] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.452978] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.452983] pci 0000:00:1c.4: PME# disabled
[    0.453014] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
[    0.453097] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.453102] pci 0000:00:1c.5: PME# disabled
[    0.453139] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.453204] pci 0000:00:1d.0: reg 20: [io  0xa0a0-0xa0bf]
[    0.453269] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.453332] pci 0000:00:1d.1: reg 20: [io  0xa080-0xa09f]
[    0.453396] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.453459] pci 0000:00:1d.2: reg 20: [io  0xa060-0xa07f]
[    0.453522] pci 0000:00:1d.3: [8086:2939] type 0 class 0x000c03
[    0.453588] pci 0000:00:1d.3: reg 20: [io  0xa040-0xa05f]
[    0.453663] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.453693] pci 0000:00:1d.7: reg 10: [mem 0xdf305800-0xdf305bff]
[    0.453798] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.453803] pci 0000:00:1d.7: PME# disabled
[    0.453830] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.453913] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.454066] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.454095] pci 0000:00:1f.2: reg 10: [io  0xa108-0xa10f]
[    0.454107] pci 0000:00:1f.2: reg 14: [io  0xa114-0xa117]
[    0.454119] pci 0000:00:1f.2: reg 18: [io  0xa100-0xa107]
[    0.454131] pci 0000:00:1f.2: reg 1c: [io  0xa110-0xa113]
[    0.454143] pci 0000:00:1f.2: reg 20: [io  0xa020-0xa03f]
[    0.454154] pci 0000:00:1f.2: reg 24: [mem 0xdf305000-0xdf3057ff]
[    0.454206] pci 0000:00:1f.2: PME# supported from D3hot
[    0.454211] pci 0000:00:1f.2: PME# disabled
[    0.454236] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.454259] pci 0000:00:1f.3: reg 10: [mem 0xdf306000-0xdf3060ff 64bit]
[    0.454291] pci 0000:00:1f.3: reg 20: [io  0xa000-0xa01f]
[    0.454340] pci 0000:00:1f.6: [8086:2932] type 0 class 0x001180
[    0.454372] pci 0000:00:1f.6: reg 10: [mem 0xdf304000-0xdf304fff 64bit]
[    0.454536] pci 0000:01:00.0: [10de:06e8] type 0 class 0x000300
[    0.454564] pci 0000:01:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    0.454587] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.454616] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit]
[    0.454632] pci 0000:01:00.0: reg 24: [io  0x9000-0x907f]
[    0.454647] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.460060] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.460074] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.460078] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    0.460085] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.460246] pci 0000:02:00.0: [14e4:4315] type 0 class 0x000280
[    0.460316] pci 0000:02:00.0: reg 10: [mem 0xde200000-0xde203fff 64bit]
[    0.460606] pci 0000:02:00.0: supports D1 D2
[    0.460771] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.460780] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
[    0.460785] pci 0000:00:1c.0:   bridge window [mem 0xde200000-0xdf2fffff]
[    0.460794] pci 0000:00:1c.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
[    0.460878] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.460900] pci 0000:03:00.0: reg 10: [io  0x6000-0x60ff]
[    0.460938] pci 0000:03:00.0: reg 18: [mem 0xd4010000-0xd4010fff 64bit pref]
[    0.460963] pci 0000:03:00.0: reg 20: [mem 0xd4000000-0xd400ffff 64bit pref]
[    0.460979] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.461032] pci 0000:03:00.0: supports D1 D2
[    0.461035] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.461041] pci 0000:03:00.0: PME# disabled
[    0.467603] Freeing initrd memory: 12504k freed
[    0.468087] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.468113] pci 0000:00:1c.1:   bridge window [io  0x6000-0x7fff]
[    0.468119] pci 0000:00:1c.1:   bridge window [mem 0xdd200000-0xde1fffff]
[    0.468128] pci 0000:00:1c.1:   bridge window [mem 0xd4000000-0xd50fffff 64bit pref]
[    0.468208] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.468216] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.468222] pci 0000:00:1c.2:   bridge window [mem 0xdc200000-0xdd1fffff]
[    0.468231] pci 0000:00:1c.2:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
[    0.468297] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.468306] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.468311] pci 0000:00:1c.3:   bridge window [mem 0xdb200000-0xdc1fffff]
[    0.468320] pci 0000:00:1c.3:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
[    0.468413] pci 0000:06:00.0: [197b:2380] type 0 class 0x000c00
[    0.468449] pci 0000:06:00.0: reg 10: [mem 0xda100000-0xda1007ff]
[    0.468470] pci 0000:06:00.0: reg 14: [mem 0xda100d00-0xda100d7f]
[    0.468529] pci 0000:06:00.0: reg 20: [mem 0xda100c80-0xda100cff]
[    0.468551] pci 0000:06:00.0: reg 24: [mem 0xda100c00-0xda100c7f]
[    0.468684] pci 0000:06:00.1: [197b:2382] type 0 class 0x000880
[    0.468711] pci 0000:06:00.1: reg 10: [mem 0xda100b00-0xda100bff]
[    0.468905] pci 0000:06:00.2: [197b:2381] type 0 class 0x000805
[    0.468931] pci 0000:06:00.2: reg 10: [mem 0xda100a00-0xda100aff]
[    0.469141] pci 0000:06:00.3: [197b:2383] type 0 class 0x000880
[    0.469168] pci 0000:06:00.3: reg 10: [mem 0xda100900-0xda1009ff]
[    0.469362] pci 0000:06:00.4: [197b:2384] type 0 class 0x000880
[    0.469388] pci 0000:06:00.4: reg 10: [mem 0xda100800-0xda1008ff]
[    0.476071] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.476086] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.476091] pci 0000:00:1c.4:   bridge window [mem 0xda100000-0xdb1fffff]
[    0.476100] pci 0000:00:1c.4:   bridge window [mem 0xd7100000-0xd80fffff 64bit pref]
[    0.476167] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
[    0.476174] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.476180] pci 0000:00:1c.5:   bridge window [mem 0xd9100000-0xda0fffff]
[    0.476188] pci 0000:00:1c.5:   bridge window [mem 0xd8100000-0xd90fffff 64bit pref]
[    0.476276] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a] (subtractive decode)
[    0.476285] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.476291] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.476299] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.476303] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.476306] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.476309] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.476312] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.476361] pci_bus 0000:00: on NUMA node 0
[    0.476371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.476740] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.476796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.476922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.476992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.477069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.477139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.477208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.477313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.477473]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.477685]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.484953] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.485037] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.485115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.485192] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.485268] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.485343] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.485419] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.485495] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.485677] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.485690] vgaarb: loaded
[    0.485936] SCSI subsystem initialized
[    0.485957] libata version 3.00 loaded.
[    0.485957] usbcore: registered new interface driver usbfs
[    0.485957] usbcore: registered new interface driver hub
[    0.485957] usbcore: registered new device driver usb
[    0.485957] wmi: Mapper loaded
[    0.485957] PCI: Using ACPI for IRQ routing
[    0.485957] PCI: pci_cache_line_size set to 64 bytes
[    0.485957] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.485957] reserve RAM buffer: 00000000be626000 - 00000000bfffffff 
[    0.485957] reserve RAM buffer: 00000000bfca8000 - 00000000bfffffff 
[    0.485957] reserve RAM buffer: 00000000bfd86000 - 00000000bfffffff 
[    0.485957] reserve RAM buffer: 00000000bfdea000 - 00000000bfffffff 
[    0.485957] reserve RAM buffer: 00000000bfe00000 - 00000000bfffffff 
[    0.485957] NetLabel: Initializing
[    0.485957] NetLabel:  domain hash size = 128
[    0.485957] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.485957] NetLabel:  unlabeled traffic allowed by default
[    0.485957] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.485957] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.485957] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.492058] Switching to clocksource hpet
[    0.495852] Switched to NOHz mode on CPU #0
[    0.495967] Switched to NOHz mode on CPU #1
[    0.501172] AppArmor: AppArmor Filesystem Enabled
[    0.501217] pnp: PnP ACPI init
[    0.501242] ACPI: bus type pnp registered
[    0.501281] pnp 00:00: [mem 0xf8000000-0xfbffffff]
[    0.501373] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.501381] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.502097] pnp 00:01: [bus 00-ff]
[    0.502101] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.502104] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.502107] pnp 00:01: [io  0x0d00-0xffff window]
[    0.502110] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.502112] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    0.502118] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    0.502121] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    0.502124] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    0.502127] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    0.502130] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    0.502132] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    0.502135] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    0.502138] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    0.502141] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    0.502143] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    0.502146] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    0.502149] pnp 00:01: [mem 0x000f0000-0x000fffff window]
[    0.502152] pnp 00:01: [mem 0xc0000000-0xfebfffff window]
[    0.502155] pnp 00:01: [mem 0xfed40000-0xfed44fff window]
[    0.502250] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.502458] pnp 00:02: [io  0x002e-0x002f]
[    0.502461] pnp 00:02: [io  0x004e-0x004f]
[    0.502463] pnp 00:02: [io  0x164e-0x164f]
[    0.502466] pnp 00:02: [io  0x0061]
[    0.502468] pnp 00:02: [io  0x0070]
[    0.502470] pnp 00:02: [io  0x0080]
[    0.502472] pnp 00:02: [io  0x0092]
[    0.502475] pnp 00:02: [io  0x00b2-0x00b3]
[    0.502477] pnp 00:02: [io  0x0063]
[    0.502479] pnp 00:02: [io  0x0065]
[    0.502482] pnp 00:02: [io  0x0067]
[    0.502484] pnp 00:02: [io  0x0600-0x060f]
[    0.502486] pnp 00:02: [io  0x0610]
[    0.502489] pnp 00:02: [io  0x0800-0x080f]
[    0.502491] pnp 00:02: [io  0x0810-0x0817]
[    0.502493] pnp 00:02: [io  0x0820-0x0823]
[    0.502496] pnp 00:02: [io  0x0400-0x047f]
[    0.502498] pnp 00:02: [io  0x0500-0x053f]
[    0.502500] pnp 00:02: [io  0x0380-0x0383]
[    0.502503] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    0.502506] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    0.502508] pnp 00:02: [mem 0xfed10000-0xfed13fff]
[    0.502511] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.502513] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.502516] pnp 00:02: [mem 0xfec00000-0xfec00fff]
[    0.502518] pnp 00:02: [mem 0xfed20000-0xfed3ffff]
[    0.502521] pnp 00:02: [mem 0xfed40000-0xfed44fff]
[    0.502523] pnp 00:02: [mem 0xfed45000-0xfed8ffff]
[    0.502526] pnp 00:02: [mem 0xfee00000-0xfee00fff]
[    0.502667] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.502676] system 00:02: [io  0x0600-0x060f] has been reserved
[    0.502682] system 00:02: [io  0x0610] has been reserved
[    0.502687] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.502693] system 00:02: [io  0x0810-0x0817] has been reserved
[    0.502699] system 00:02: [io  0x0820-0x0823] has been reserved
[    0.502705] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.502710] system 00:02: [io  0x0500-0x053f] has been reserved
[    0.502716] system 00:02: [io  0x0380-0x0383] has been reserved
[    0.502723] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.502729] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.502735] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.502741] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.502747] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.502754] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.502760] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.502766] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.502772] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.502779] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.502786] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.502799] pnp 00:03: [io  0x0000-0x001f]
[    0.502801] pnp 00:03: [io  0x0081-0x0091]
[    0.502804] pnp 00:03: [io  0x0093-0x009f]
[    0.502809] pnp 00:03: [io  0x00c0-0x00df]
[    0.502812] pnp 00:03: [dma 4]
[    0.502855] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.502884] pnp 00:04: [io  0x0070-0x0077]
[    0.502928] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.503008] pnp 00:05: [irq 0 disabled]
[    0.503019] pnp 00:05: [irq 8]
[    0.503022] pnp 00:05: [mem 0xfed00000-0xfed003ff]
[    0.503067] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.503081] pnp 00:06: [io  0x00f0]
[    0.503087] pnp 00:06: [irq 13]
[    0.503131] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.503144] pnp 00:07: [mem 0xff800000-0xffffffff]
[    0.503189] pnp 00:07: Plug and Play ACPI device, IDs INT0800 (active)
[    0.503209] pnp 00:08: [io  0x0060]
[    0.503211] pnp 00:08: [io  0x0064]
[    0.503217] pnp 00:08: [irq 1]
[    0.503263] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.503287] pnp 00:09: [irq 12]
[    0.503338] pnp 00:09: Plug and Play ACPI device, IDs SYN014f SYN0100 SYN0002 PNP0f13 (active)
[    0.503373] pnp 00:0a: [io  0x0380-0x0383]
[    0.503379] pnp 00:0a: [irq 4]
[    0.503427] pnp 00:0a: Plug and Play ACPI device, IDs ENE0100 (active)
[    0.503637] pnp 00:0b: [irq 23]
[    0.503705] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.503816] pnp: PnP ACPI: found 12 devices
[    0.503821] ACPI: ACPI bus type pnp unregistered
[    0.503828] PnPBIOS: Disabled by ACPI PNP
[    0.540520] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.540531] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.540622] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.540628] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.540634] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.540642] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    0.540649] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.540659] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.540666] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
[    0.540675] pci 0000:00:1c.0:   bridge window [mem 0xde200000-0xdf2fffff]
[    0.540683] pci 0000:00:1c.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
[    0.540697] pci 0000:03:00.0: BAR 6: assigned [mem 0xd4020000-0xd402ffff pref]
[    0.540704] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.540710] pci 0000:00:1c.1:   bridge window [io  0x6000-0x7fff]
[    0.540720] pci 0000:00:1c.1:   bridge window [mem 0xdd200000-0xde1fffff]
[    0.540728] pci 0000:00:1c.1:   bridge window [mem 0xd4000000-0xd50fffff 64bit pref]
[    0.540740] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.540747] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.540756] pci 0000:00:1c.2:   bridge window [mem 0xdc200000-0xdd1fffff]
[    0.540764] pci 0000:00:1c.2:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
[    0.540776] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.540782] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.540792] pci 0000:00:1c.3:   bridge window [mem 0xdb200000-0xdc1fffff]
[    0.540800] pci 0000:00:1c.3:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
[    0.540813] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.540819] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.540829] pci 0000:00:1c.4:   bridge window [mem 0xda100000-0xdb1fffff]
[    0.540837] pci 0000:00:1c.4:   bridge window [mem 0xd7100000-0xd80fffff 64bit pref]
[    0.540849] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
[    0.540855] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.540865] pci 0000:00:1c.5:   bridge window [mem 0xd9100000-0xda0fffff]
[    0.540873] pci 0000:00:1c.5:   bridge window [mem 0xd8100000-0xd90fffff 64bit pref]
[    0.540885] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a]
[    0.540890] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.540899] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.540906] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.540931] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.540939] pci 0000:00:01.0: setting latency timer to 64
[    0.540951] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.540959] pci 0000:00:1c.0: setting latency timer to 64
[    0.540968] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.540976] pci 0000:00:1c.1: setting latency timer to 64
[    0.540984] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.540994] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.541004] pci 0000:00:1c.2: setting latency timer to 64
[    0.541011] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.541022] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.541032] pci 0000:00:1c.3: setting latency timer to 64
[    0.541040] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.541048] pci 0000:00:1c.4: setting latency timer to 64
[    0.541056] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.541064] pci 0000:00:1c.5: setting latency timer to 64
[    0.541073] pci 0000:00:1e.0: setting latency timer to 64
[    0.541078] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.541081] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.541084] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.541087] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.541089] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.541092] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xd2ffffff]
[    0.541095] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.541098] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
[    0.541101] pci_bus 0000:02: resource 1 [mem 0xde200000-0xdf2fffff]
[    0.541104] pci_bus 0000:02: resource 2 [mem 0xd3000000-0xd3ffffff 64bit pref]
[    0.541107] pci_bus 0000:03: resource 0 [io  0x6000-0x7fff]
[    0.541109] pci_bus 0000:03: resource 1 [mem 0xdd200000-0xde1fffff]
[    0.541112] pci_bus 0000:03: resource 2 [mem 0xd4000000-0xd50fffff 64bit pref]
[    0.541115] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
[    0.541118] pci_bus 0000:04: resource 1 [mem 0xdc200000-0xdd1fffff]
[    0.541121] pci_bus 0000:04: resource 2 [mem 0xd5100000-0xd60fffff 64bit pref]
[    0.541124] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    0.541127] pci_bus 0000:05: resource 1 [mem 0xdb200000-0xdc1fffff]
[    0.541130] pci_bus 0000:05: resource 2 [mem 0xd6100000-0xd70fffff 64bit pref]
[    0.541132] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
[    0.541135] pci_bus 0000:06: resource 1 [mem 0xda100000-0xdb1fffff]
[    0.541138] pci_bus 0000:06: resource 2 [mem 0xd7100000-0xd80fffff 64bit pref]
[    0.541141] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    0.541144] pci_bus 0000:07: resource 1 [mem 0xd9100000-0xda0fffff]
[    0.541147] pci_bus 0000:07: resource 2 [mem 0xd8100000-0xd90fffff 64bit pref]
[    0.541150] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    0.541152] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
[    0.541155] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
[    0.541158] pci_bus 0000:0a: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.541202] NET: Registered protocol family 2
[    0.541288] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.541561] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.542008] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.542323] TCP: Hash tables configured (established 131072 bind 65536)
[    0.542329] TCP reno registered
[    0.542335] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.542350] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.542490] NET: Registered protocol family 1
[    0.542937] pci 0000:01:00.0: Boot video device
[    0.543010] PCI: CLS 64 bytes, default 64
[    0.543039] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.543046] Simple Boot Flag at 0x44 set to 0x1
[    0.543292] cpufreq-nforce2: No nForce2 chipset.
[    0.543450] audit: initializing netlink socket (disabled)
[    0.543465] type=2000 audit(1304763023.536:1): initialized
[    0.554358] highmem bounce pool size: 64 pages
[    0.554369] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.556433] VFS: Disk quotas dquot_6.5.2
[    0.556509] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.557301] fuse init (API version 7.16)
[    0.557417] msgmni has been set to 1632
[    0.557706] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.557742] io scheduler noop registered
[    0.557748] io scheduler deadline registered
[    0.557768] io scheduler cfq registered (default)
[    0.557929] pcieport 0000:00:01.0: setting latency timer to 64
[    0.557972] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.558061] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.558115] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.558219] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.558272] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.558378] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.558431] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.558537] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.558590] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.558694] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.558748] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.558856] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.558909] pcieport 0000:00:1c.5: irq 46 for MSI/MSI-X
[    0.559038] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.559045] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.559052] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.559075] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.559081] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.559089] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.559114] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.559120] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.559128] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.559151] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.559159] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.559184] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.559193] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.559218] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.559223] pci 0000:06:00.0: Signaling PME through PCIe PME interrupt
[    0.559228] pci 0000:06:00.1: Signaling PME through PCIe PME interrupt
[    0.559233] pci 0000:06:00.2: Signaling PME through PCIe PME interrupt
[    0.559238] pci 0000:06:00.3: Signaling PME through PCIe PME interrupt
[    0.559243] pci 0000:06:00.4: Signaling PME through PCIe PME interrupt
[    0.559252] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.559276] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.559285] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.559309] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.559342] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.559422] intel_idle: MWAIT substates: 0x1110
[    0.559424] intel_idle: does not run on family 6 model 15
[    0.559755] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.560092] ACPI: AC Adapter [ACAD] (on-line)
[    0.560216] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.560226] ACPI: Power Button [PWRB]
[    0.560281] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.560666] ACPI: Lid Switch [LID0]
[    0.560726] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.560735] ACPI: Sleep Button [SLPB]
[    0.560808] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.560816] ACPI: Power Button [PWRF]
[    0.561142] ACPI: acpi_idle registered with cpuidle
[    0.561322] Monitor-Mwait will be used to enter C-1 state
[    0.561352] Monitor-Mwait will be used to enter C-2 state
[    0.561360] Marking TSC unstable due to TSC halts in idle
[    0.565445] [Firmware Bug]: Invalid critical threshold (0)
[    0.566023] thermal LNXTHERM:00: registered as thermal_zone0
[    0.566030] ACPI: Thermal Zone [TZ01] (55 C)
[    0.566057] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.566142] ERST: Table is not found!
[    0.566244] isapnp: Scanning for PnP cards...
[    0.566259] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.583558] ACPI: Battery Slot [BAT0] (battery present)
[    0.921802] isapnp: No Plug & Play device found
[    0.926260] Linux agpgart interface v0.103
[    0.927995] brd: module loaded
[    0.928718] loop: module loaded
[    0.928832] i2c-core: driver [adp5520] using legacy suspend method
[    0.928837] i2c-core: driver [adp5520] using legacy resume method
[    0.929412] Fixed MDIO Bus: probed
[    0.929450] PPP generic driver version 2.4.2
[    0.929496] tun: Universal TUN/TAP device driver, 1.6
[    0.929501] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.929614] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.929640] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.929663] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.929667] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.929712] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.929786] ehci_hcd 0000:00:1a.7: debug port 1
[    0.933690] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.933712] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xdf305c00
[    0.948016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.948161] hub 1-0:1.0: USB hub found
[    0.948169] hub 1-0:1.0: 4 ports detected
[    0.948282] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.948301] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.948305] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.948353] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.948420] ehci_hcd 0000:00:1d.7: debug port 1
[    0.952306] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.952323] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf305800
[    0.968016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.968146] hub 2-0:1.0: USB hub found
[    0.968153] hub 2-0:1.0: 8 ports detected
[    0.968263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.968285] uhci_hcd: USB Universal Host Controller Interface driver
[    0.968320] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.968334] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.968338] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.968392] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.968458] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a0e0
[    0.968609] hub 3-0:1.0: USB hub found
[    0.968617] hub 3-0:1.0: 2 ports detected
[    0.968716] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.968727] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.968731] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.968781] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.968843] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a0c0
[    0.968989] hub 4-0:1.0: USB hub found
[    0.968996] hub 4-0:1.0: 2 ports detected
[    0.969090] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.969101] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.969105] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.969157] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.972051] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000a0a0
[    0.972198] hub 5-0:1.0: USB hub found
[    0.972206] hub 5-0:1.0: 2 ports detected
[    0.972301] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.972312] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.972316] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.972368] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.972422] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a080
[    0.972571] hub 6-0:1.0: USB hub found
[    0.972578] hub 6-0:1.0: 2 ports detected
[    0.972667] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.972678] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.972682] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.972727] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.972778] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000a060
[    0.972927] hub 7-0:1.0: USB hub found
[    0.972935] hub 7-0:1.0: 2 ports detected
[    0.973021] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.973032] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.973036] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.973082] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.973144] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000a040
[    0.973290] hub 8-0:1.0: USB hub found
[    0.973297] hub 8-0:1.0: 2 ports detected
[    0.973489] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.994783] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.994793] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.994950] mousedev: PS/2 mouse device common for all mice
[    0.996995] rtc_cmos 00:04: RTC can wake from S4
[    0.997072] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.997106] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.997212] device-mapper: uevent: version 1.0.3
[    0.997311] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.997399] device-mapper: multipath: version 1.2.0 loaded
[    0.997405] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.997497] EISA: Probing bus 0 at eisa.0
[    0.997503] EISA: Cannot allocate resource for mainboard
[    0.997507] Cannot allocate resource for EISA slot 1
[    0.997512] Cannot allocate resource for EISA slot 2
[    0.997517] Cannot allocate resource for EISA slot 3
[    0.997521] Cannot allocate resource for EISA slot 4
[    0.997526] Cannot allocate resource for EISA slot 5
[    0.997530] Cannot allocate resource for EISA slot 6
[    0.997535] Cannot allocate resource for EISA slot 7
[    0.997539] Cannot allocate resource for EISA slot 8
[    0.997543] EISA: Detected 0 cards.
[    0.997663] cpuidle: using governor ladder
[    0.997756] cpuidle: using governor menu
[    0.998098] TCP cubic registered
[    0.998256] NET: Registered protocol family 10
[    0.998953] NET: Registered protocol family 17
[    0.998976] Registering the dns_resolver key type
[    0.999397] Using IPI No-Shortcut mode
[    0.999514] PM: Hibernation image not present or could not be loaded.
[    0.999526] registered taskstats version 1
[    1.000211]   Magic number: 11:194:173
[    1.000242] pcie_pme 0000:00:1c.0:pcie01: hash matches
[    1.000264] acpi device:36: hash matches
[    1.000331] rtc_cmos 00:04: setting system clock to 2011-05-07 10:10:24 UTC (1304763024)
[    1.000338] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.000343] EDD information not available.
[    1.000562] Freeing unused kernel memory: 720k freed
[    1.000898] Write protecting the kernel text: 5352k
[    1.000987] Write protecting the kernel read-only data: 2188k
[    1.000992] NX-protecting the kernel data: 4888k
[    1.016890] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.034900] <30>udev[67]: starting version 167
[    1.120050] sdhci: Secure Digital Host Controller Interface driver
[    1.120060] sdhci: Copyright(c) Pierre Ossman
[    1.150080] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[    1.150112] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.150390] sdhci-pci 0000:06:00.1: setting latency timer to 64
[    1.150402] mmc0: no vmmc regulator found
[    1.150452] Registered led device: mmc0::
[    1.150505] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[    1.150525] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[    1.150547] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.150562] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[    1.150573] sdhci-pci 0000:06:00.2: PCI INT A disabled
[    1.169847] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.169884] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.169936] r8169 0000:03:00.0: setting latency timer to 64
[    1.170007] r8169 0000:03:00.0: irq 47 for MSI/MSI-X
[    1.170621] r8169 0000:03:00.0: eth0: RTL8168c/8111c at 0xf842a000, 00:23:8b:03:0e:75, XID 1c4000c0 IRQ 47
[    1.187648] firewire_ohci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.187668] firewire_ohci 0000:06:00.0: setting latency timer to 64
[    1.214861] ahci 0000:00:1f.2: version 3.0
[    1.214878] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.214946] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    1.214966] ahci 0000:00:1f.2: BIOS update required for suspend/resume
[    1.215042] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.215050] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc ems sxs 
[    1.215061] ahci 0000:00:1f.2: setting latency timer to 64
[    1.239176] scsi0 : ahci
[    1.239415] scsi1 : ahci
[    1.239524] scsi2 : ahci
[    1.239617] scsi3 : ahci
[    1.239711] scsi4 : ahci
[    1.239810] scsi5 : ahci
[    1.240053] ata1: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305100 irq 48
[    1.240063] ata2: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305180 irq 48
[    1.240069] ata3: DUMMY
[    1.240073] ata4: DUMMY
[    1.240078] ata5: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305300 irq 48
[    1.240085] ata6: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305380 irq 48
[    1.264442] firewire_ohci: Added fw-ohci device 0000:06:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10
[    1.320043] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.564073] ata6: SATA link down (SStatus 0 SControl 300)
[    1.564113] ata5: SATA link down (SStatus 0 SControl 300)
[    1.712034] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    1.736043] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.736064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.738019] ata1.00: ATA-8: WDC WD3200BEVT-60ZCT0, 12.01A12, max UDMA/100
[    1.738026] ata1.00: 625142448 sectors, multi 0: LBA48 
[    1.739582] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T30L, GC04, max UDMA/100
[    1.740013] ata1.00: configured for UDMA/100
[    1.740181] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 12.0 PQ: 0 ANSI: 5
[    1.740407] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.740421] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.740475] sd 0:0:0:0: [sda] Write Protect is off
[    1.740482] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.740518] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.744308] ata2.00: configured for UDMA/100
[    1.764133] firewire_core: created device fw0: GUID 00241b0032db3d01, S400
[    1.825337]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.825794] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.859509] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T30L  GC04 PQ: 0 ANSI: 5
[    1.969574] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.969586] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.969760] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.969865] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.011413] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input5
[    2.011589] generic-usb 0003:04D9:1133.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1a.1-2/input0
[    2.011618] usbcore: registered new interface driver usbhid
[    2.011623] usbhid: USB HID core driver
[    2.489729] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   29.084441] <30>udev[318]: starting version 167
[   29.112693] Adding 9064444k swap on /dev/sda6.  Priority:-1 extents:1 across:9064444k 
[   29.120332] lp: driver loaded but no devices found
[   29.128523] coretemp coretemp.0: TjMax is assumed as 100 C!
[   29.128592] coretemp coretemp.1: TjMax is assumed as 100 C!
[   29.140443] Linux video capture interface: v2.00
[   29.310335] hp_accel: hardware type HPDV5_I found
[   29.337177] lis3lv02d: 8 bits sensor found
[   29.358685] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr
[   29.373658] acpi device:08: registered as cooling_device2
[   29.374195] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/LNXVIDEO:01/input/input6
[   29.374721] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.458362] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xc0
[   29.458366] ene_ir: PLL freq = 1406
[   29.458368] ene_ir: KB3926C detected
[   29.458382] ene_ir: Firmware regs: c0 00
[   29.458384] ene_ir: Hardware features:
[   29.458385] ene_ir: * Uses GPIO 40 for IR demodulated input
[   29.464056] IR NEC protocol handler initialized
[   29.473281] IR RC5(x) protocol handler initialized
[   29.473324] lib80211: common routines for IEEE802.11 drivers
[   29.473328] lib80211_crypt: registered algorithm 'NULL'
[   29.486643] IR RC6 protocol handler initialized
[   29.495882] IR JVC protocol handler initialized
[   29.510931] IR Sony protocol handler initialized
[   29.513244] <30>udev[385]: renamed network interface eth0 to eth1
[   29.522432] lirc_dev: IR Remote Control driver registered, major 249 
[   29.523841] IR LIRC bridge handler initialized
[   29.525846] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.525858] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[   29.545416] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[   29.545979] Registered led device: hp::hddprotect
[   29.546026] hp_accel: driver loaded
[   29.608906] type=1400 audit(1304755853.104:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=605 comm="apparmor_parser"
[   29.609874] type=1400 audit(1304755853.104:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=605 comm="apparmor_parser"
[   29.610488] type=1400 audit(1304755853.104:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=605 comm="apparmor_parser"
[   29.612515] type=1400 audit(1304755853.108:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=614 comm="apparmor_parser"
[   29.613472] type=1400 audit(1304755853.108:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[   29.614088] type=1400 audit(1304755853.108:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[   29.717149] wl: module license 'MIXED/Proprietary' taints kernel.
[   29.717156] Disabling lock debugging due to kernel taint
[   29.721802] Registered IR keymap rc-rc6-mce
[   29.722078] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input8
[   29.722269] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
[   29.730739] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
[   29.730745] ene_ir: driver has been succesfully loaded
[   29.735972] uvcvideo: Found UVC 1.00 device HP Webcam (0408:03ba)
[   29.821357] r8169 0000:03:00.0: eth1: link down
[   29.822557] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   29.983960] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input9
[   29.984679] usbcore: registered new interface driver uvcvideo
[   29.984683] USB Video Class driver (v1.0.0)
[   30.023936] type=1400 audit(1304755853.516:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=742 comm="apparmor_parser"
[   30.024957] type=1400 audit(1304755853.520:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=743 comm="apparmor_parser"
[   30.029141] type=1400 audit(1304755853.524:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
[   30.029754] type=1400 audit(1304755853.524:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
[   30.197294] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.197309] wl 0000:02:00.0: setting latency timer to 64
[   30.347315] lib80211_crypt: registered algorithm 'TKIP'
[   30.401436] input: HP WMI hotkeys as /devices/virtual/input/input10
[   30.558794] eth0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[   30.568558] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   30.568638] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   30.568673] HDA Intel 0000:00:1b.0: setting latency timer to 64

```

What can I do to get more info during boot?
In the dmesg, [   30.568673] means "30.56 seconds after startup"?
What happens between 30s and the complete loading of the desktop?

Thanks very much!

---

### Post by Gillingham on 2011-05-07
There is a package bootchart that lets you see what is happening during the boot process.

David

---

### Post by colin.p on 2011-05-07
I have, as well as several others, noticed a much longer boot time in natty. Mine is around a minute or so. Don't know if it's peculiar to unity or not, but I leave my laptop in sleep mode, instead of turning off, so I only boot up a couple times a week. However, I would be interested as to what is causing the slow boot process as well.

---

### Post by 4manifold on 2011-05-18
I've also noticed longer boot times in natty, although I haven't timed it.  Sorry, I have nothing helpful to say, but I hope this gets sorted out sometime.

---

### Post by lithopsian on 2011-05-18
dmesg doesn't show you the whole story, only a few kernel messages.  2s to mount the inititial file system is about right. 30s to begin udev is not right.  Something is hanging in there, possibly the same problem several other people are having.

---

