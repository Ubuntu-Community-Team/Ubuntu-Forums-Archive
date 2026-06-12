---
title: "Ubuntu 12.04 boots for more then 60s."
date: 2012-05-08
forum: General Help
---

### Post by GPilot on 2012-05-08
My Ubuntu (version 12.04 with latest updates), installed with Wubi alongside Windows 7, boots abnormally slow. I timed it both with bootchart (unfortunately not possible to post in attachment because of the resulting poor quality) and a stopwatch and it always needed more then 60/70 seconds from when I chose Ubuntu in GRUB to when the login menu appeared. I had previous installs of Ubuntu with Wubi on other machines but it never took so long for them to boot as with this install. I also booted several times to see if this was a one-time issue, but it always needed more then a minute. Once it has booted and I logged in it runs just fine!

My specs:
Computer: HP Pavilion g7 Laptop, Core i5
Ubuntu: 12.04, 64 bit version

What I have already tried but what didn't work or had little impact on my boot time:
[http://www.ubuntubuzz.com/2012/01/how-to-increasespeed-up-ubuntu-booting.html]("http://www.ubuntubuzz.com/2012/01/how-to-increasespeed-up-ubuntu-booting.html")
[http://ubuntu.mindseeder.com/12.04/]("http://ubuntu.mindseeder.com/12.04/")

So my question is: What can I do to fix this? Is it a common issue nowadays with Wubi and should I switch to real partitioning? Or are there some scripts/adjustments I could use/make to make to make it faster?

Thanks in advance for any help,
GPilot

---

### Post by brainwash on 2012-05-08
You should take a look at the kernel messages. Run this command in a terminal and attach the output:
```
dmesg
```

---

### Post by GPilot on 2012-05-08
This is the output of dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@yellow) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=F288B2FC88B2BE83 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ce3f000 (usable)
[    0.000000]  BIOS-e820: 000000009ce3f000 - 000000009cebf000 (reserved)
[    0.000000]  BIOS-e820: 000000009cebf000 - 000000009cfbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009cfbf000 - 000000009cfff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009cfff000 - 000000009d000000 (usable)
[    0.000000]  BIOS-e820: 000000009d000000 - 000000009fa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000015fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion g7 Notebook PC      /1672, BIOS F.33 08/30/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x15fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09D000000 mask FFF000000 uncachable
[    0.000000]   3 base 09E000000 mask FFE000000 uncachable
[    0.000000]   4 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 base 140000000 mask FE0000000 write-back
[    0.000000]   7 base 15FE00000 mask FFFE00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0x9d000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fe1b0] fe1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000009d000000
[    0.000000]  0000000000 - 009d000000 page 2M
[    0.000000] kernel direct mapping tables up to 9d000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000015fe00000
[    0.000000]  0100000000 - 015fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 15fe00000 @ 9ce38000-9ce3f000
[    0.000000] RAMDISK: 364e4000 - 3726a000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000009cffe120 0008C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 000000009cffc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 000000009cfed000 0BD0A (v01 HP     1672     00000000 MSFT 01000013)
[    0.000000] ACPI: FACS 000000009cf6c000 00040
[    0.000000] ACPI: ASF! 000000009cffd000 000A5 (v32 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 000000009cffb000 00038 (v01 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000009cffa000 0008C (v02 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000009cff9000 0003C (v01 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000009cfec000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MSDM 000000009cfeb000 00055 (v03 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009cfea000 00D52 (v01 HP     1672     00001000 MSFT 01000013)
[    0.000000] ACPI: BOOT 000000009cfe8000 00028 (v01 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 000000009cfe5000 00034 (v07 HP     1672     00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009cfe4000 007C2 (v01 HP     1672     00003000 INTL 20100121)
[    0.000000] ACPI: SSDT 000000009cfe3000 00996 (v01 HP     1672     00003000 INTL 20100121)
[    0.000000] ACPI: SSDT 000000009cfdd000 0219F (v01 HP     1672     00001000 INTL 20100121)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000015fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000015fe00000
[    0.000000]   NODE_DATA [000000015fdfb000 - 000000015fdfffff]
[    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015b400000-ffff88015f3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0015fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009ce3f
[    0.000000]     0: 0x0009cfff -> 0x0009d000
[    0.000000]     0: 0x00100000 -> 0x0015fe00
[    0.000000] On node 0 totalpages: 1035213
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 622208 pages, LIFO batch:31
[    0.000000]   Normal zone: 6136 pages used for memmap
[    0.000000]   Normal zone: 386568 pages, LIFO batch:31
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
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009ce3f000 - 000000009cebf000
[    0.000000] PM: Registered nosave memory: 000000009cebf000 - 000000009cfbf000
[    0.000000] PM: Registered nosave memory: 000000009cfbf000 - 000000009cfff000
[    0.000000] PM: Registered nosave memory: 000000009d000000 - 000000009fa00000
[    0.000000] PM: Registered nosave memory: 000000009fa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at 9fa00000 (gap: 9fa00000:40600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88015fa00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1012688
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=F288B2FC88B2BE83 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3978680k/5765120k available (6566k kernel code, 1624268k absent, 162172k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.703 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.40 BogoMIPS (lpj=9578812)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000039] AppArmor: AppArmor initialized
[    0.000040] Yama: becoming mindful.
[    0.000431] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001507] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001961] Mount-cache hash table entries: 256
[    0.002068] Initializing cgroup subsys cpuacct
[    0.002072] Initializing cgroup subsys memory
[    0.002079] Initializing cgroup subsys devices
[    0.002081] Initializing cgroup subsys freezer
[    0.002082] Initializing cgroup subsys blkio
[    0.002087] Initializing cgroup subsys perf_event
[    0.002112] CPU: Physical Processor ID: 0
[    0.002113] CPU: Processor Core ID: 0
[    0.002118] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002119] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002122] mce: CPU supports 7 MCE banks
[    0.002131] CPU0: Thermal monitoring handled by SMI
[    0.002138] using mwait in idle threads.
[    0.004604] ACPI: Core revision 20110623
[    0.023220] ftrace: allocating 27049 entries in 107 pages
[    0.046716] x2apic not enabled, IRQ remapping init failed
[    0.047194] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.086830] CPU0: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz stepping 07
[    0.192083] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.192097] PEBS disabled due to CPU errata.
[    0.192103] ... version:                3
[    0.192106] ... bit width:              48
[    0.192110] ... generic registers:      4
[    0.192113] ... value mask:             0000ffffffffffff
[    0.192117] ... max period:             000000007fffffff
[    0.192121] ... fixed-purpose events:   3
[    0.192125] ... event mask:             000000070000000f
[    0.192497] NMI watchdog enabled, takes one hw-pmu counter.
[    0.192685] Booting Node   0, Processors  #1
[    0.192692] smpboot cpu 1: start_ip = 98000
[    0.284006] CPU1: Thermal monitoring handled by SMI
[    0.304094] NMI watchdog enabled, takes one hw-pmu counter.
[    0.304300]  #2
[    0.304304] smpboot cpu 2: start_ip = 98000
[    0.391841] CPU2: Thermal monitoring handled by SMI
[    0.411969] NMI watchdog enabled, takes one hw-pmu counter.
[    0.412145]  #3
[    0.412148] smpboot cpu 3: start_ip = 98000
[    0.499675] CPU3: Thermal monitoring handled by SMI
[    0.519815] NMI watchdog enabled, takes one hw-pmu counter.
[    0.519872] Brought up 4 CPUs
[    0.519878] Total of 4 processors activated (19156.87 BogoMIPS).
[    0.529305] devtmpfs: initialized
[    0.531227] EVM: security.selinux
[    0.531230] EVM: security.SMACK64
[    0.531234] EVM: security.capability
[    0.531295] PM: Registering ACPI NVS region at 9cebf000 (1048576 bytes)
[    0.533388] print_constraints: dummy: 
[    0.533438] RTC time: 15:00:51, date: 05/08/12
[    0.533518] NET: Registered protocol family 16
[    0.533747] Trying to unpack rootfs image as initramfs...
[    0.533768] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.533774] ACPI: bus type pci registered
[    0.533947] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.533956] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.648854] PCI: Using configuration type 1 for base access
[    0.651145] bio: create slab <bio-0> at 0
[    0.651349] ACPI: Added _OSI(Module Device)
[    0.651354] ACPI: Added _OSI(Processor Device)
[    0.651359] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.651364] ACPI: Added _OSI(Processor Aggregator Device)
[    0.655415] ACPI: EC: Look up EC in DSDT
[    0.659400] ACPI: Executed 1 blocks of module-level executable AML code
[    0.719414] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.720653] ACPI: SSDT 000000009ce70798 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.721714] ACPI: Dynamic OEM Table Load:
[    0.721721] ACPI: SSDT           (null) 00727 (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.751901] ACPI: SSDT 000000009ce71a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.753038] ACPI: Dynamic OEM Table Load:
[    0.753045] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.783500] ACPI: SSDT 000000009ce6fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    0.784547] ACPI: Dynamic OEM Table Load:
[    0.784553] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    0.863944] ACPI: Interpreter enabled
[    0.863955] ACPI: (supports S0 S3 S4 S5)
[    0.864027] ACPI: Using IOAPIC for interrupt routing
[    0.873591] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.873935] ACPI: No dock devices found.
[    0.873939] HEST: Table not found.
[    0.873946] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.874716] \_SB_.PCI0:_OSC invalid UUID
[    0.874720] _OSC request data:1 8 1f 
[    0.874731] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.876077] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.876084] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.876090] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.876099] pci_root PNP0A08:00: host bridge window [mem 0x9fa00000-0xfeafffff]
[    0.876126] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.876221] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.876306] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.876314] pci 0000:00:01.0: PME# disabled
[    0.876348] pci 0000:00:01.1: [8086:0105] type 1 class 0x000604
[    0.876430] pci 0000:00:01.1: PME# supported from D0 D3hot D3cold
[    0.876437] pci 0000:00:01.1: PME# disabled
[    0.876470] pci 0000:00:01.2: [8086:0109] type 1 class 0x000604
[    0.876552] pci 0000:00:01.2: PME# supported from D0 D3hot D3cold
[    0.876558] pci 0000:00:01.2: PME# disabled
[    0.876601] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    0.876629] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    0.876647] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.876660] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    0.876802] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.876852] pci 0000:00:16.0: reg 10: [mem 0xc3604000-0xc360400f 64bit]
[    0.877011] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.877020] pci 0000:00:16.0: PME# disabled
[    0.877093] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.877555] pci 0000:00:1a.0: reg 10: [mem 0xc3609000-0xc36093ff]
[    0.880072] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.880082] pci 0000:00:1a.0: PME# disabled
[    0.880137] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.880175] pci 0000:00:1b.0: reg 10: [mem 0xc3600000-0xc3603fff 64bit]
[    0.880346] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.880354] pci 0000:00:1b.0: PME# disabled
[    0.880402] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.880581] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.880591] pci 0000:00:1c.0: PME# disabled
[    0.880642] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.880821] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.880830] pci 0000:00:1c.1: PME# disabled
[    0.880882] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    0.881060] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.881069] pci 0000:00:1c.2: PME# disabled
[    0.881141] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.881575] pci 0000:00:1d.0: reg 10: [mem 0xc3608000-0xc36083ff]
[    0.884085] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.884095] pci 0000:00:1d.0: PME# disabled
[    0.884142] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    0.884390] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.884440] pci 0000:00:1f.2: reg 10: [io  0x5088-0x508f]
[    0.884461] pci 0000:00:1f.2: reg 14: [io  0x5094-0x5097]
[    0.884482] pci 0000:00:1f.2: reg 18: [io  0x5080-0x5087]
[    0.884503] pci 0000:00:1f.2: reg 1c: [io  0x5090-0x5093]
[    0.884525] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    0.884546] pci 0000:00:1f.2: reg 24: [mem 0xc3607000-0xc36077ff]
[    0.884669] pci 0000:00:1f.2: PME# supported from D3hot
[    0.884678] pci 0000:00:1f.2: PME# disabled
[    0.884719] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.884757] pci 0000:00:1f.3: reg 10: [mem 0xc3605000-0xc36050ff 64bit]
[    0.884811] pci 0000:00:1f.3: reg 20: [io  0x5040-0x505f]
[    0.884954] pci 0000:01:00.0: [1002:6760] type 0 class 0x000300
[    0.884989] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.885017] pci 0000:01:00.0: reg 18: [mem 0xc2600000-0xc261ffff 64bit]
[    0.885037] pci 0000:01:00.0: reg 20: [io  0x4000-0x40ff]
[    0.885070] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.885152] pci 0000:01:00.0: supports D1 D2
[    0.891064] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.891072] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.891079] pci 0000:00:01.0:   bridge window [mem 0xc2600000-0xc35fffff]
[    0.891089] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.891146] pci 0000:00:01.1: PCI bridge to [bus 02-02]
[    0.891211] pci 0000:00:01.2: PCI bridge to [bus 03-03]
[    0.891378] pci 0000:04:00.0: [1814:5390] type 0 class 0x000280
[    0.891438] pci 0000:04:00.0: reg 10: [mem 0xc2500000-0xc250ffff]
[    0.899070] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.899084] pci 0000:00:1c.0:   bridge window [mem 0xc2500000-0xc25fffff]
[    0.899233] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    0.899268] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
[    0.899327] pci 0000:05:00.0: reg 18: [mem 0xc0404000-0xc0404fff 64bit pref]
[    0.899366] pci 0000:05:00.0: reg 20: [mem 0xc0400000-0xc0403fff 64bit pref]
[    0.899522] pci 0000:05:00.0: supports D1 D2
[    0.899526] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.899537] pci 0000:05:00.0: PME# disabled
[    0.907044] pci 0000:00:1c.1: PCI bridge to [bus 05-05]
[    0.907054] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.907073] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.907216] pci 0000:06:00.0: [10ec:5209] type 0 class 0x00ff00
[    0.907252] pci 0000:06:00.0: reg 10: [mem 0xc1500000-0xc1500fff]
[    0.907495] pci 0000:06:00.0: supports D1 D2
[    0.907500] pci 0000:06:00.0: PME# supported from D1 D2 D3hot
[    0.907511] pci 0000:06:00.0: PME# disabled
[    0.915032] pci 0000:00:1c.2: PCI bridge to [bus 06-06]
[    0.915042] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.915052] pci 0000:00:1c.2:   bridge window [mem 0xc1500000-0xc24fffff]
[    0.915067] pci 0000:00:1c.2:   bridge window [mem 0xc0500000-0xc14fffff 64bit pref]
[    0.915126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.915445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.915515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.915594] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.915692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.915885] \_SB_.PCI0:_OSC invalid UUID
[    0.915889] _OSC request data:1 1f 1f 
[    0.915899]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.915978] \_SB_.PCI0:_OSC invalid UUID
[    0.915982] _OSC request data:1 0 1d 
[    0.915992]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.915996] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.921827] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.921944] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.922054] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.922161] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.922267] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.922376] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.922484] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.922591] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.922850] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.922870] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.922877] vgaarb: loaded
[    0.922880] vgaarb: bridge control possible 0000:01:00.0
[    0.922884] vgaarb: no bridge control possible 0000:00:02.0
[    0.923129] i2c-core: driver [aat2870] using legacy suspend method
[    0.923133] i2c-core: driver [aat2870] using legacy resume method
[    0.923276] SCSI subsystem initialized
[    0.923393] libata version 3.00 loaded.
[    0.923492] usbcore: registered new interface driver usbfs
[    0.923514] usbcore: registered new interface driver hub
[    0.923579] usbcore: registered new device driver usb
[    0.923775] PCI: Using ACPI for IRQ routing
[    0.941067] PCI: pci_cache_line_size set to 64 bytes
[    0.941247] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.941253] reserve RAM buffer: 000000009ce3f000 - 000000009fffffff 
[    0.941260] reserve RAM buffer: 000000009d000000 - 000000009fffffff 
[    0.941265] reserve RAM buffer: 000000015fe00000 - 000000015fffffff 
[    0.941483] NetLabel: Initializing
[    0.941487] NetLabel:  domain hash size = 128
[    0.941491] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.941514] NetLabel:  unlabeled traffic allowed by default
[    0.941632] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.941648] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.943691] Switching to clocksource hpet
[    0.958430] AppArmor: AppArmor Filesystem Enabled
[    0.958480] pnp: PnP ACPI init
[    0.958515] ACPI: bus type pnp registered
[    0.959489] pnp 00:00: [bus 00-fe]
[    0.959499] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.959505] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.959509] pnp 00:00: [io  0x0d00-0xffff window]
[    0.959515] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.959520] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.959525] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.959531] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.959536] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.959541] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.959546] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.959551] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.959556] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.959561] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.959566] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.959571] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.959576] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.959581] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.959586] pnp 00:00: [mem 0x9fa00000-0xfeafffff window]
[    0.959714] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.959768] pnp 00:01: [io  0x0000-0x001f]
[    0.959773] pnp 00:01: [io  0x0081-0x0091]
[    0.959778] pnp 00:01: [io  0x0093-0x009f]
[    0.959782] pnp 00:01: [io  0x00c0-0x00df]
[    0.959788] pnp 00:01: [dma 4]
[    0.959869] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.959889] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.959944] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.960126] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.960183] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.960207] pnp 00:04: [io  0x00f0]
[    0.960225] pnp 00:04: [irq 13]
[    0.960277] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.960303] pnp 00:05: [io  0x002e-0x002f]
[    0.960308] pnp 00:05: [io  0x004e-0x004f]
[    0.960312] pnp 00:05: [io  0x0061]
[    0.960316] pnp 00:05: [io  0x0063]
[    0.960320] pnp 00:05: [io  0x0065]
[    0.960323] pnp 00:05: [io  0x0067]
[    0.960327] pnp 00:05: [io  0x0070]
[    0.960331] pnp 00:05: [io  0x0080]
[    0.960335] pnp 00:05: [io  0x0092]
[    0.960339] pnp 00:05: [io  0x00b2-0x00b3]
[    0.960344] pnp 00:05: [io  0x0680-0x069f]
[    0.960348] pnp 00:05: [io  0x1004-0x1013]
[    0.960352] pnp 00:05: [io  0xffff]
[    0.960356] pnp 00:05: [io  0xffff]
[    0.960360] pnp 00:05: [io  0x0400-0x0453]
[    0.960369] pnp 00:05: [io  0x0454-0x0457]
[    0.960373] pnp 00:05: [io  0x0458-0x047f]
[    0.960377] pnp 00:05: [io  0x0500-0x057f]
[    0.960381] pnp 00:05: [io  0x164e-0x164f]
[    0.960386] pnp 00:05: [io  0x0380-0x0387]
[    0.960390] pnp 00:05: [io  0x0068-0x006f]
[    0.960509] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.960515] system 00:05: [io  0x1004-0x1013] has been reserved
[    0.960521] system 00:05: [io  0xffff] has been reserved
[    0.960527] system 00:05: [io  0xffff] has been reserved
[    0.960533] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.960539] system 00:05: [io  0x0454-0x0457] has been reserved
[    0.960544] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.960550] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.960556] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.960562] system 00:05: [io  0x0380-0x0387] has been reserved
[    0.960570] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.960590] pnp 00:06: [io  0x0070-0x0077]
[    0.960601] pnp 00:06: [irq 8]
[    0.960657] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.960695] pnp 00:07: [io  0x0060]
[    0.960699] pnp 00:07: [io  0x0064]
[    0.960709] pnp 00:07: [irq 1]
[    0.960778] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.960816] pnp 00:08: [irq 12]
[    0.960888] pnp 00:08: Plug and Play ACPI device, IDs SYN1e40 SYN1e00 SYN0002 PNP0f13 (active)
[    0.961124] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.961129] pnp 00:09: [mem 0xfed10000-0xfed17fff]
[    0.961134] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.961138] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.961143] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.961147] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.961152] pnp 00:09: [mem 0xfed90000-0xfed93fff]
[    0.961157] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.961161] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    0.961166] pnp 00:09: [mem 0x9fa00000-0x9fa00fff]
[    0.961267] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.961274] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.961280] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.961286] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.961293] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.961299] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.961305] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.961311] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.961318] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.961324] system 00:09: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    0.961332] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.961800] pnp 00:0a: [mem 0x20000000-0x201fffff]
[    0.961805] pnp 00:0a: [mem 0x40000000-0x401fffff]
[    0.961925] system 00:0a: [mem 0x20000000-0x201fffff] could not be reserved
[    0.961932] system 00:0a: [mem 0x40000000-0x401fffff] could not be reserved
[    0.961939] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.961982] pnp: PnP ACPI: found 11 devices
[    0.961986] ACPI: ACPI bus type pnp unregistered
[    0.971663] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.971677] PCI: max bus depth: 1 pci_try_num: 2
[    0.971764] pci 0000:01:00.0: BAR 6: assigned [mem 0xc2620000-0xc263ffff pref]
[    0.971784] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.971794] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.971803] pci 0000:00:01.0:   bridge window [mem 0xc2600000-0xc35fffff]
[    0.971811] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.971821] pci 0000:00:01.1: PCI bridge to [bus 02-02]
[    0.971836] pci 0000:00:01.2: PCI bridge to [bus 03-03]
[    0.971850] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.971862] pci 0000:00:1c.0:   bridge window [mem 0xc2500000-0xc25fffff]
[    0.971881] pci 0000:00:1c.1: PCI bridge to [bus 05-05]
[    0.971888] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.971905] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.971920] pci 0000:00:1c.2: PCI bridge to [bus 06-06]
[    0.971927] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.971939] pci 0000:00:1c.2:   bridge window [mem 0xc1500000-0xc24fffff]
[    0.971949] pci 0000:00:1c.2:   bridge window [mem 0xc0500000-0xc14fffff 64bit pref]
[    0.971993] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.972002] pci 0000:00:01.0: setting latency timer to 64
[    0.972013] pci 0000:00:01.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.972020] pci 0000:00:01.1: setting latency timer to 64
[    0.972029] pci 0000:00:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.972036] pci 0000:00:01.2: setting latency timer to 64
[    0.972058] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.972068] pci 0000:00:1c.0: setting latency timer to 64
[    0.972083] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.972092] pci 0000:00:1c.1: setting latency timer to 64
[    0.972114] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.972123] pci 0000:00:1c.2: setting latency timer to 64
[    0.972132] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.972137] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.972143] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.972149] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    0.972154] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.972160] pci_bus 0000:01: resource 1 [mem 0xc2600000-0xc35fffff]
[    0.972166] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    0.972173] pci_bus 0000:04: resource 1 [mem 0xc2500000-0xc25fffff]
[    0.972179] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.972185] pci_bus 0000:05: resource 2 [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.972191] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    0.972197] pci_bus 0000:06: resource 1 [mem 0xc1500000-0xc24fffff]
[    0.972203] pci_bus 0000:06: resource 2 [mem 0xc0500000-0xc14fffff 64bit pref]
[    0.972272] NET: Registered protocol family 2
[    0.972635] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.975033] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.978683] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.979004] TCP: Hash tables configured (established 524288 bind 65536)
[    0.979010] TCP reno registered
[    0.979037] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.979089] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.979274] NET: Registered protocol family 1
[    0.979315] pci 0000:00:02.0: Boot video device
[    0.979342] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.991793] pci 0000:00:1a.0: PCI INT A disabled
[    0.991846] pci 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.007759] pci 0000:00:1d.0: PCI INT A disabled
[    1.007820] PCI: CLS 64 bytes, default 64
[    1.007825] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.007831] Placing 64MB software IO TLB between ffff880098e38000 - ffff88009ce38000
[    1.007836] software IO TLB at phys 0x98e38000 - 0x9ce38000
[    1.007857] Simple Boot Flag at 0x44 set to 0x1
[    1.008883] audit: initializing netlink socket (disabled)
[    1.008902] type=2000 audit(1336489251.824:1): initialized
[    1.084363] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.110256] VFS: Disk quotas dquot_6.5.2
[    1.110384] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.111488] fuse init (API version 7.17)
[    1.111723] msgmni has been set to 7770
[    1.112528] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.112591] io scheduler noop registered
[    1.112597] io scheduler deadline registered
[    1.112669] io scheduler cfq registered (default)
[    1.112872] pcieport 0000:00:01.0: setting latency timer to 64
[    1.112940] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.113035] pcieport 0000:00:01.1: setting latency timer to 64
[    1.113090] pcieport 0000:00:01.1: irq 41 for MSI/MSI-X
[    1.113178] pcieport 0000:00:01.2: setting latency timer to 64
[    1.113232] pcieport 0000:00:01.2: irq 42 for MSI/MSI-X
[    1.113640] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.113698] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.113816] intel_idle: MWAIT substates: 0x21120
[    1.113820] intel_idle: v0.4 model 0x2A
[    1.113824] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.114143] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.114413] ACPI: AC Adapter [ACAD] (off-line)
[    1.114757] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.115143] ACPI: Lid Switch [LID0]
[    1.115244] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.115254] ACPI: Power Button [PWRB]
[    1.115357] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.115365] ACPI: Power Button [PWRF]
[    1.123444] [Firmware Bug]: Invalid critical threshold (0)
[    1.124864] thermal LNXTHERM:00: registered as thermal_zone0
[    1.124870] ACPI: Thermal Zone [TZ01] (40 C)
[    1.124909] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.124926] ACPI: Battery Slot [BAT0] (battery present)
[    1.124985] ERST: Table is not found!
[    1.124990] GHES: HEST is not enabled!
[    1.125188] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.186144] ACPI: Battery Slot [BAT0] (battery present)
[    1.228427] Freeing initrd memory: 13848k freed
[    1.332242] Linux agpgart interface v0.103
[    1.332449] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.332728] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.335747] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.335989] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    1.339198] brd: module loaded
[    1.340886] loop: module loaded
[    1.341148] ahci 0000:00:1f.2: version 3.0
[    1.341187] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.341281] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.355257] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    1.355266] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.355277] ahci 0000:00:1f.2: setting latency timer to 64
[    1.364278] scsi0 : ahci
[    1.364460] scsi1 : ahci
[    1.364614] scsi2 : ahci
[    1.364765] scsi3 : ahci
[    1.364906] scsi4 : ahci
[    1.365047] scsi5 : ahci
[    1.365260] ata1: SATA max UDMA/133 abar m2048@0xc3607000 port 0xc3607100 irq 43
[    1.365266] ata2: DUMMY
[    1.365269] ata3: DUMMY
[    1.365273] ata4: DUMMY
[    1.365278] ata5: SATA max UDMA/133 abar m2048@0xc3607000 port 0xc3607300 irq 43
[    1.365283] ata6: DUMMY
[    1.366125] Fixed MDIO Bus: probed
[    1.366164] tun: Universal TUN/TAP device driver, 1.6
[    1.366168] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.366295] PPP generic driver version 2.4.2
[    1.366531] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.366565] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.366606] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.366613] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.366717] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.366766] ehci_hcd 0000:00:1a.0: debug port 2
[    1.370664] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.370694] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc3609000
[    1.383188] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.383480] hub 1-0:1.0: USB hub found
[    1.383490] hub 1-0:1.0: 2 ports detected
[    1.383617] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.383650] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.383657] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.383762] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.383805] ehci_hcd 0000:00:1d.0: debug port 2
[    1.387698] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.387727] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xc3608000
[    1.403155] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.403414] hub 2-0:1.0: USB hub found
[    1.403423] hub 2-0:1.0: 2 ports detected
[    1.403551] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.403576] uhci_hcd: USB Universal Host Controller Interface driver
[    1.403675] usbcore: registered new interface driver libusual
[    1.403752] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.412620] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.412634] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.412919] mousedev: PS/2 mouse device common for all mice
[    1.413799] rtc_cmos 00:06: RTC can wake from S4
[    1.413995] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.414038] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.414201] device-mapper: uevent: version 1.0.3
[    1.414351] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.414633] cpuidle: using governor ladder
[    1.415053] cpuidle: using governor menu
[    1.415058] EFI Variables Facility v0.08 2004-May-17
[    1.415535] TCP cubic registered
[    1.415753] NET: Registered protocol family 10
[    1.416726] NET: Registered protocol family 17
[    1.416757] Registering the dns_resolver key type
[    1.417062] PM: Hibernation image not present or could not be loaded.
[    1.417112] registered taskstats version 1
[    1.434664] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.443301]   Magic number: 12:146:32
[    1.443485] rtc_cmos 00:06: setting system clock to 2012-05-08 15:00:52 UTC (1336489252)
[    1.445074] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.445079] EDD information not available.
[    1.682843] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.682885] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.686187] ata5.00: ATAPI: hp      DVD A  DS8A5LH, 1H68, max UDMA/100
[    1.687885] ata5.00: configured for UDMA/100
[    1.693063] ata1.00: ATA-8: ST9500325AS, 0005HPM1, max UDMA/100
[    1.693073] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.694823] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.715966] ata1.00: configured for UDMA/100
[    1.716426] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0005 PQ: 0 ANSI: 5
[    1.716821] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.716881] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.716919] sd 0:0:0:0: [sda] Write Protect is off
[    1.716926] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.716990] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.722209] scsi 4:0:0:0: CD-ROM            hp       DVD A  DS8A5LH   1H68 PQ: 0 ANSI: 5
[    1.728527] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.728538] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.728889] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.729140] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.779332]  sda: sda1 sda2 sda3 sda4
[    1.780324] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.784377] Freeing unused kernel memory: 920k freed
[    1.784629] Write protecting the kernel read-only data: 12288k
[    1.797941] Freeing unused kernel memory: 1608k freed
[    1.808066] Freeing unused kernel memory: 1196k freed
[    1.827614] hub 1-1:1.0: USB hub found
[    1.827716] hub 1-1:1.0: 6 ports detected
[    1.876118] udevd[120]: starting version 175
[    1.938407] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.948227] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.948278] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.948351] r8169 0000:05:00.0: setting latency timer to 64
[    1.948473] r8169 0000:05:00.0: irq 44 for MSI/MSI-X
[    1.949733] r8169 0000:05:00.0: eth0: RTL8105e at 0xffffc90000672000, 10:1f:74:b6:e5:4b, XID 00a00000 IRQ 44
[    2.006316] Refined TSC clocksource calibration: 2394.560 MHz.
[    2.006329] Switching to clocksource tsc
[    2.071258] hub 2-1:1.0: USB hub found
[    2.071393] hub 2-1:1.0: 6 ports detected
[    2.349945] usb 2-1.1: new low-speed USB device number 3 using ehci_hcd
[    2.467644] input: HID 04d9:2517 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input4
[    2.467883] generic-usb 0003:04D9:2517.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04d9:2517] on usb-0000:00:1d.0-1.1/input0
[    2.480344] input: HID 04d9:2517 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input5
[    2.480638] generic-usb 0003:04D9:2517.0002: input,hidraw1: USB HID v1.10 Mouse [HID 04d9:2517] on usb-0000:00:1d.0-1.1/input1
[    2.480671] usbcore: registered new interface driver usbhid
[    2.480675] usbhid: USB HID core driver
[    2.529669] usb 2-1.5: new high-speed USB device number 4 using ehci_hcd
[    3.894054] EXT3-fs (loop0): recovery required on readonly filesystem
[    3.894065] EXT3-fs (loop0): write access will be enabled during recovery
[    8.838878] kjournald starting.  Commit interval 5 seconds
[    8.839214] EXT3-fs (loop0): recovery complete
[    8.839939] EXT3-fs (loop0): mounted filesystem with ordered data mode
[   38.885250] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.887052] udevd[359]: starting version 175
[   39.019549] cfg80211: Calling CRDA to update world regulatory domain
[   39.304322] cfg80211: World regulatory domain updated:
[   39.304325] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   39.304328] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.304331] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.304334] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.304336] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.304339] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.304811] wmi: Mapper loaded
[   39.307833] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110623/dsopcode-236)
[   39.307839] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880158a3eaa0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.307848] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880158a3ee10), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.307877] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110623/dsopcode-236)
[   39.307881] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880158a3eaa0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.307886] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880158a3ee10), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.307936] input: HP WMI hotkeys as /devices/virtual/input/input6
[   39.308543] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110623/dsopcode-236)
[   39.308549] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880158a3eaa0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.308560] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880158a3ee10), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.308607] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110623/dsopcode-236)
[   39.308612] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880158a3eaa0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.308621] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880158a3ee10), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[   39.375453] type=1400 audit(1336482090.486:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=528 comm="apparmor_parser"
[   39.375637] type=1400 audit(1336482090.486:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=576 comm="apparmor_parser"
[   39.375733] type=1400 audit(1336482090.486:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=528 comm="apparmor_parser"
[   39.375930] type=1400 audit(1336482090.486:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=528 comm="apparmor_parser"
[   39.375984] type=1400 audit(1336482090.486:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=576 comm="apparmor_parser"
[   39.376178] type=1400 audit(1336482090.486:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=576 comm="apparmor_parser"
[   39.471140] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   39.471493] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.471500] mei 0000:00:16.0: setting latency timer to 64
[   39.471561] mei 0000:00:16.0: irq 45 for MSI/MSI-X
[   39.475006] rt2800pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.475040] rt2800pci 0000:04:00.0: setting latency timer to 64
[   39.478407] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   39.478412] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478415] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   39.478437] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478440] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   39.478443] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478445] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   39.478448] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478450] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   39.478453] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478456] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   39.478459] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478461] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   39.478464] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478466] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   39.478469] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478471] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   39.478474] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478477] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   39.478479] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478482] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   39.478485] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   39.478487] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   39.478490] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.478493] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   39.478495] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.478498] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   39.478501] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   39.482877] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   39.483216] Registered led device: rt2800pci-phy0::radio
[   39.483235] Registered led device: rt2800pci-phy0::assoc
[   39.483265] Registered led device: rt2800pci-phy0::quality
[   39.551420] [drm] Initialized drm 1.1.0 20060810
[   39.569231] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.569235] i915 0000:00:02.0: setting latency timer to 64
[   39.611955] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   39.611959] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   39.611961] [drm] Driver supports precise vblank timestamp query.
[   39.612805] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   39.612808] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   39.884379] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[   39.933132] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   40.037028] Linux video capture interface: v2.00
[   40.037458] uvcvideo: Found UVC 1.00 device HP Webcam-101 (04f2:b249)
[   40.050675] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8
[   40.050745] usbcore: registered new interface driver uvcvideo
[   40.050747] USB Video Class driver (1.1.1)
[   40.070705] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   40.071535] Initializing Realtek PCIE storage driver...
[   40.071571] rts_pstor 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   40.073353] Resource length: 0x1000
[   40.073367] Original address: 0xc1500000, remapped address: 0xffffc90000676000
[   40.073370] pci->irq = 18
[   40.073372] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[   40.073394] rts_pstor 0000:06:00.0: setting latency timer to 64
[   40.186189] fbcon: inteldrmfb (fb0) is primary device
[   40.186277] Console: switching to colour frame buffer device 200x56
[   40.186304] fb0: inteldrmfb frame buffer device
[   40.186306] drm: registered panic notifier
[   40.188338] acpi device:1a: registered as cooling_device4
[   40.190141] acpi device:1b: registered as cooling_device5
[   40.190216] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/LNXVIDEO:00/input/input9
[   40.190316] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   40.211729] acpi device:20: registered as cooling_device6
[   40.211898] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10
[   40.211954] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   40.212005] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   40.212051] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   40.212105] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   40.212134] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   40.273510] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
[   40.273619] rts_pstor: waiting for device to settle before scanning
[   40.694998] [drm] radeon defaulting to kernel modesetting.
[   40.695000] [drm] radeon kernel modesetting enabled.
[   40.695011] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   40.695051] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   40.695058] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.695064] radeon 0000:01:00.0: setting latency timer to 64
[   40.695205] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6760 0x103C:0x1672).
[   40.695242] [drm] register mmio base: 0xC2600000
[   40.695243] [drm] register mmio size: 131072
[   40.695244] vga_switcheroo: enabled
[   40.695337] radeon atpx: version is 1
[   40.888667] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   40.888741] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   40.888834] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   40.888907] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   41.271776] rts_pstor: device scan complete
[   41.271874] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   41.271902] Bad LUN (0:1)
[   41.271948] Bad target number (1:0)
[   41.271987] Bad target number (2:0)
[   41.272023] Bad target number (3:0)
[   41.272056] Bad target number (4:0)
[   41.272089] Bad target number (5:0)
[   41.272123] Bad target number (6:0)
[   41.272158] Bad target number (7:0)
[   41.272311] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   41.272555] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   41.399084] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
[   41.971080] ATOM BIOS: HP
[   41.971447] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   41.971449] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   41.973282] [drm] Detected VRAM RAM=1024M, BAR=256M
[   41.973285] [drm] RAM width 64bits DDR
[   41.973333] [TTM] Zone  kernel: Available graphics memory: 1998126 kiB.
[   41.973335] [TTM] Initializing pool allocator.
[   41.973355] [drm] radeon: 1024M of VRAM memory ready
[   41.973357] [drm] radeon: 512M of GTT memory ready.
[   41.973367] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   41.973368] [drm] Driver supports precise vblank timestamp query.
[   41.973411] radeon 0000:01:00.0: irq 48 for MSI/MSI-X
[   41.973416] radeon 0000:01:00.0: radeon: using MSI.
[   41.973475] [drm] radeon: irq initialized.
[   41.973479] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   41.973800] [drm] Loading CAICOS Microcode
[   42.013470] EXT3-fs (loop0): using internal journal
[   42.073508] init: failsafe main process (805) killed by TERM signal
[   42.099741] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   42.099894] radeon 0000:01:00.0: WB enabled
[   42.116172] [drm] ring test succeeded in 3 usecs
[   42.116282] [drm] radeon: ib pool ready.
[   42.116382] [drm] ib test succeeded in 0 usecs
[   42.117187] [drm] Radeon Display Connectors
[   42.117189] [drm] Connector 0:
[   42.117190] [drm]   VGA
[   42.117193] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   42.117194] [drm]   Encoders:
[   42.117196] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   42.117214] [drm] Internal thermal controller without fan control
[   42.118094] [drm] radeon: power management initialized
[   42.222663] No connectors reported connected with modes
[   42.222667] [drm] Cannot find any crtc or sizes - going 1024x768
[   42.225267] [drm] fb mappable at 0xA0142000
[   42.225268] [drm] vram apper at 0xA0000000
[   42.225269] [drm] size 3145728
[   42.225270] [drm] fb depth is 24
[   42.225271] [drm]    pitch is 4096
[   42.225337] fb1: radeondrmfb frame buffer device
[   42.225344] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 1
[   42.412092] lp: driver loaded but no devices found
[   42.538955] ppdev: user-space parallel port driver
[   42.546575] type=1400 audit(1336482093.662:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=879 comm="apparmor_parser"
[   42.546911] type=1400 audit(1336482093.662:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=879 comm="apparmor_parser"
[   42.639093] Bluetooth: Core ver 2.16
[   42.639106] NET: Registered protocol family 31
[   42.639107] Bluetooth: HCI device and connection manager initialized
[   42.639109] Bluetooth: HCI socket layer initialized
[   42.639110] Bluetooth: L2CAP socket layer initialized
[   42.639114] Bluetooth: SCO socket layer initialized
[   42.640430] Bluetooth: RFCOMM TTY layer initialized
[   42.640433] Bluetooth: RFCOMM socket layer initialized
[   42.640434] Bluetooth: RFCOMM ver 1.11
[   42.899200] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.899203] Bluetooth: BNEP filters: protocol multicast
[   43.084775] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   43.103913] type=1400 audit(1336482094.218:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=930 comm="apparmor_parser"
[   43.104204] type=1400 audit(1336482094.218:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=930 comm="apparmor_parser"
[   43.122404] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.169262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.455526] r8169 0000:05:00.0: eth0: link down
[   43.455531] r8169 0000:05:00.0: eth0: link down
[   43.455805] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.456084] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.134148] r8169 0000:05:00.0: eth0: link up
[   45.134415] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   55.602449] eth0: no IPv6 routers present
```

---

### Post by brainwash on 2012-05-08
There is a 30 seconds delay during boot. Might be related to udev and a buggy initialization of the realtek network module.

So you might want to try this:
```
echo "blacklist r8169" | sudo tee /etc/modprobe.d/blacklist-ethernet.conf
```
```
gksudo gedit /etc/rc.local
```
Add "modprobe r8169" before the last line (exit 0) and reboot.

If this does not change anything, try to blacklist the wireless module instead.

---

### Post by philinux on 2012-05-08
Hangs on error ADDRCONF(NETDEV_UP): eth0: link is not ready

See post 5 [http://www.linuxquestions.org/questions/slackware-14/addrconf-netdev_up-eth0-link-is-not-ready-815130/](http://www.linuxquestions.org/questions/slackware-14/addrconf-netdev_up-eth0-link-is-not-ready-815130/)

You never know.

Also seems a common ish problem.

[http://www.google.com/search?client=ubuntu&channel=fs&q=ADDRCONF%28NETDEV_UP%29%3A+eth0%3A+link+is+not+ready&ie=utf-8&oe=utf-8&gl=uk](http://www.google.com/search?client=ubuntu&channel=fs&q=ADDRCONF%28NETDEV_UP%29%3A+eth0%3A+link+is+not+ready&ie=utf-8&oe=utf-8&gl=uk)

---

### Post by flemur13013 on 2012-05-08
**[SIZE=1][B][http://www.linuxtoday.com/high_performance/boot-speed-competition-ubuntu-kubuntu-and-mint.html](http://www.linuxtoday.com/high_performance/boot-speed-competition-ubuntu-kubuntu-and-mint.html)**[/SIZE][/B]

**[SIZE=2]Boot speed competition - Ubuntu, Kubuntu and Mint[/SIZE]**

M[SIZE=2]ay 01, 2012, 14:00[/SIZE]
                                               
[SIZE=2]The most important finding is not the  rather expected variation in boot times for such seemingly similar          distributions, it's the great lack of major time boost with SSD  compared to older hardware and much slower         disks....[/SIZE]

 [SIZE=2]To sum it up, Mint and Ubuntu will get  you there in 10 seconds or less, Kubuntu will manage in about 22          seconds. Overall, all three results are fairly satisfactory for modern  standards.[/SIZE]

---

### Post by GPilot on 2012-05-08
> **brainwash said:**
> There is a 30 seconds delay during boot. Might be related to udev and a buggy initialization of the realtek network module.

So you might want to try this:
```
echo "blacklist r8169" | sudo tee /etc/modprobe.d/blacklist-ethernet.conf
```
```
gksudo gedit /etc/rc.local
```
Add "modprobe r8169" before the last line (exit 0) and reboot.

If this does not change anything, try to blacklist the wireless module instead.

Unfortunately that didn't work...

---

### Post by GPilot on 2012-05-08
> **flemur13013 said:**
> **[SIZE=1][B][http://www.linuxtoday.com/high_performance/boot-speed-competition-ubuntu-kubuntu-and-mint.html](http://www.linuxtoday.com/high_performance/boot-speed-competition-ubuntu-kubuntu-and-mint.html)**[/SIZE][/B]

**[SIZE=2]Boot speed competition - Ubuntu, Kubuntu and Mint[/SIZE]**

M[SIZE=2]ay 01, 2012, 14:00[/SIZE]
                                               
[SIZE=2]The most important finding is not the  rather expected variation in boot times for such seemingly similar          distributions, it's the great lack of major time boost with SSD  compared to older hardware and much slower         disks....[/SIZE]

 [SIZE=2]To sum it up, Mint and Ubuntu will get  you there in 10 seconds or less, Kubuntu will manage in about 22          seconds. Overall, all three results are fairly satisfactory for modern  standards.[/SIZE]

10s sounds GREAT, but unfortunately my Ubuntu ,,get's me there'' in 70s... My problem likely is not distribution specific, it has to do with f.e. (as someone mentioned in this thread) the wireless module causing 30s extra or something similar.

---

### Post by GPilot on 2012-05-08
> **philinux said:**
> Hangs on error ADDRCONF(NETDEV_UP): eth0: link is not ready

See post 5 [http://www.linuxquestions.org/questions/slackware-14/addrconf-netdev_up-eth0-link-is-not-ready-815130/](http://www.linuxquestions.org/questions/slackware-14/addrconf-netdev_up-eth0-link-is-not-ready-815130/)

You never know.

Also seems a common ish problem.

[http://www.google.com/search?client=ubuntu&channel=fs&q=ADDRCONF%28NETDEV_UP%29%3A+eth0%3A+link+is+not+ready&ie=utf-8&oe=utf-8&gl=uk](http://www.google.com/search?client=ubuntu&channel=fs&q=ADDRCONF%28NETDEV_UP%29%3A+eth0%3A+link+is+not+ready&ie=utf-8&oe=utf-8&gl=uk)

Sadly switching cables, etc. didn't work either for me :(

---

### Post by GPilot on 2012-05-14
So guys, thanks for all of your suggestions, but sadly none of them has worked. Any other ideas related to this? It still is a problem, the booting time hasn't improved :(

---

### Post by GPilot on 2012-05-30
It works again!
After a month or so I tried a fresh install again and got it right. It was probably just a bug which they fixed. Thanks nevertheless for your efforts!

---

### Post by manuganji on 2012-07-03
this is my dmesg output
> [    0.634807] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    0.634893] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.634936] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.634938] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.634940] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.634942] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.634943] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.634998] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.635001] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.635003] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.635006] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.635008] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.635011] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.635041] pnp 00:02: [dma 4]
[    0.635043] pnp 00:02: [io  0x0000-0x000f]
[    0.635045] pnp 00:02: [io  0x0081-0x0083]
[    0.635046] pnp 00:02: [io  0x0087]
[    0.635048] pnp 00:02: [io  0x0089-0x008b]
[    0.635049] pnp 00:02: [io  0x008f]
[    0.635051] pnp 00:02: [io  0x00c0-0x00df]
[    0.635075] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.635084] pnp 00:03: [io  0x0070-0x0071]
[    0.635096] pnp 00:03: [irq 8]
[    0.635117] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.635127] pnp 00:04: [io  0x0061]
[    0.635149] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.635157] pnp 00:05: [io  0x00f0-0x00ff]
[    0.635163] pnp 00:05: [irq 13]
[    0.635188] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.635204] pnp 00:06: [io  0x0010-0x001f]
[    0.635206] pnp 00:06: [io  0x0022-0x003f]
[    0.635208] pnp 00:06: [io  0x0044-0x005f]
[    0.635209] pnp 00:06: [io  0x0068-0x006f]
[    0.635211] pnp 00:06: [io  0x0072-0x007f]
[    0.635212] pnp 00:06: [io  0x0080]
[    0.635214] pnp 00:06: [io  0x0084-0x0086]
[    0.635215] pnp 00:06: [io  0x0088]
[    0.635217] pnp 00:06: [io  0x008c-0x008e]
[    0.635219] pnp 00:06: [io  0x0090-0x009f]
[    0.635220] pnp 00:06: [io  0x00a2-0x00bf]
[    0.635222] pnp 00:06: [io  0x00e0-0x00ef]
[    0.635223] pnp 00:06: [io  0x04d0-0x04d1]
[    0.635225] pnp 00:06: [mem 0xfe800000-0xfe8001ff]
[    0.635268] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.635271] system 00:06: [mem 0xfe800000-0xfe8001ff] has been reserved
[    0.635274] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.635291] pnp 00:07: [irq 12]
[    0.635320] pnp 00:07: Plug and Play ACPI device, IDs DLL0447 SYN0600 SYN0002 PNP0f13 (active)
[    0.635334] pnp 00:08: [io  0x0060]
[    0.635336] pnp 00:08: [io  0x0064]
[    0.635338] pnp 00:08: [io  0x0062]
[    0.635339] pnp 00:08: [io  0x0066]
[    0.635345] pnp 00:08: [irq 1]
[    0.635369] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.635494] pnp 00:09: [io  0x0400-0x047f]
[    0.635496] pnp 00:09: [io  0x1180-0x119f]
[    0.635498] pnp 00:09: [io  0x0500-0x057f]
[    0.635500] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.635502] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.635503] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.635505] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.635546] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.635548] system 00:09: [io  0x1180-0x119f] has been reserved
[    0.635550] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.635553] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.635556] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.635558] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.635561] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.635564] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.635645] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.635679] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.635877] pnp: PnP ACPI: found 11 devices
[    0.635878] ACPI: ACPI bus type pnp unregistered
[    0.643457] PCI: max bus depth: 1 pci_try_num: 2
[    0.643518] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd1600000-0xd17fffff 64bit pref]
[    0.643522] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.643525] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd1800000-0xd19fffff]
[    0.643528] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd1a00000-0xd1bfffff 64bit pref]
[    0.643531] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.643534] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.643536] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.643540] pci 0000:00:01.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.643543] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.643547] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.643550] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.643556] pci 0000:00:1c.0:   bridge window [mem 0xd1800000-0xd19fffff]
[    0.643561] pci 0000:00:1c.0:   bridge window [mem 0xd1a00000-0xd1bfffff 64bit pref]
[    0.643569] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.643572] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.643578] pci 0000:00:1c.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.643583] pci 0000:00:1c.1:   bridge window [mem 0xd1600000-0xd17fffff 64bit pref]
[    0.643592] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.643595] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.643602] pci 0000:00:1c.2:   bridge window [mem 0xfb300000-0xfbcfffff]
[    0.643607] pci 0000:00:1c.2:   bridge window [mem 0xd0c00000-0xd15fffff 64bit pref]
[    0.643615] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.643618] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.643625] pci 0000:00:1c.4:   bridge window [mem 0xfa900000-0xfb2fffff]
[    0.643630] pci 0000:00:1c.4:   bridge window [mem 0xd0100000-0xd0afffff 64bit pref]
[    0.643638] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    0.643670] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.643674] pci 0000:00:01.0: setting latency timer to 64
[    0.643685] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.643690] pci 0000:00:1c.0: setting latency timer to 64
[    0.643699] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.643704] pci 0000:00:1c.1: setting latency timer to 64
[    0.643717] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.643722] pci 0000:00:1c.2: setting latency timer to 64
[    0.643730] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.643735] pci 0000:00:1c.4: setting latency timer to 64
[    0.643743] pci 0000:00:1e.0: setting latency timer to 64
[    0.643748] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.643750] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.643752] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.643755] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[    0.643757] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.643759] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.643761] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.643764] pci_bus 0000:11: resource 0 [io  0x3000-0x3fff]
[    0.643766] pci_bus 0000:11: resource 1 [mem 0xd1800000-0xd19fffff]
[    0.643768] pci_bus 0000:11: resource 2 [mem 0xd1a00000-0xd1bfffff 64bit pref]
[    0.643771] pci_bus 0000:12: resource 0 [io  0x2000-0x2fff]
[    0.643773] pci_bus 0000:12: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.643775] pci_bus 0000:12: resource 2 [mem 0xd1600000-0xd17fffff 64bit pref]
[    0.643778] pci_bus 0000:13: resource 0 [io  0xd000-0xdfff]
[    0.643780] pci_bus 0000:13: resource 1 [mem 0xfb300000-0xfbcfffff]
[    0.643782] pci_bus 0000:13: resource 2 [mem 0xd0c00000-0xd15fffff 64bit pref]
[    0.643784] pci_bus 0000:15: resource 0 [io  0xc000-0xcfff]
[    0.643787] pci_bus 0000:15: resource 1 [mem 0xfa900000-0xfb2fffff]
[    0.643789] pci_bus 0000:15: resource 2 [mem 0xd0100000-0xd0afffff 64bit pref]
[    0.643791] pci_bus 0000:20: resource 4 [io  0x0000-0x0cf7]
[    0.643793] pci_bus 0000:20: resource 5 [io  0x0d00-0xffff]
[    0.643796] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[    0.643798] pci_bus 0000:20: resource 7 [mem 0xc0000000-0xffffffff]
[    0.643801] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.643803] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.643842] NET: Registered protocol family 2
[    0.643990] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.644961] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.647700] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.648031] TCP: Hash tables configured (established 524288 bind 65536)
[    0.648034] TCP reno registered
[    0.648046] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.648083] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.648199] NET: Registered protocol family 1
[    0.648233] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.772229] pci 0000:00:1a.0: PCI INT A disabled
[    0.772274] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.899973] pci 0000:00:1d.0: PCI INT A disabled
[    0.899999] pci 0000:01:00.0: Boot video device
[    0.900028] PCI: CLS 64 bytes, default 64
[    0.900030] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.900033] Placing 64MB software IO TLB between ffff8800bb5a6000 - ffff8800bf5a6000
[    0.900035] software IO TLB at phys 0xbb5a6000 - 0xbf5a6000
[    0.900568] audit: initializing netlink socket (disabled)
[    0.900580] type=2000 audit(1341306922.732:1): initialized
[    0.931973] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.951363] VFS: Disk quotas dquot_6.5.2
[    0.951417] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.951955] fuse init (API version 7.17)
[    0.952052] msgmni has been set to 7605
[    0.952511] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.952547] io scheduler noop registered
[    0.952549] io scheduler deadline registered
[    0.952582] io scheduler cfq registered (default)
[    0.952695] pcieport 0000:00:01.0: setting latency timer to 64
[    0.952725] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.952777] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.952827] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.952910] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.952960] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.953040] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.953091] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.953173] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.953223] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.953314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.953434] pciehp: Using ACPI for slot detection.
[    0.953499] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[    0.953535] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.953541] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.953591] intel_idle: MWAIT substates: 0x1120
[    0.953593] intel_idle: v0.4 model 0x25
[    0.953594] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.953677] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.953723] ACPI: AC Adapter [AC] (off-line)
[    0.953821] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.953826] ACPI: Power Button [PWRB]
[    0.953865] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.955418] ACPI: Lid Switch [LID0]
[    0.955458] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.955462] ACPI: Sleep Button [SBTN]
[    0.955497] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.955500] ACPI: Power Button [PWRF]
[    0.967676] thermal LNXTHERM:00: registered as thermal_zone0
[    0.967680] ACPI: Thermal Zone [THM] (59 C)
[    0.967712] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.967724] ACPI: Battery Slot [BAT0] (battery present)
[    0.967759] ERST: Table is not found!
[    0.967761] GHES: HEST is not enabled!
[    0.967886] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.980196] ACPI: Battery Slot [BAT0] (battery present)
[    1.031086] Freeing initrd memory: 13836k freed
[    1.191756] Linux agpgart interface v0.103
[    1.193385] brd: module loaded
[    1.194194] loop: module loaded
[    1.194319] ahci 0000:00:1f.2: version 3.0
[    1.194343] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.194399] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.194485] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.194489] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.194494] ahci 0000:00:1f.2: setting latency timer to 64
[    1.207822] scsi0 : ahci
[    1.207912] scsi1 : ahci
[    1.207992] scsi2 : ahci
[    1.208069] scsi3 : ahci
[    1.208147] scsi4 : ahci
[    1.208221] scsi5 : ahci
[    1.208350] ata1: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06100 irq 45
[    1.208354] ata2: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06180 irq 45
[    1.208356] ata3: DUMMY
[    1.208357] ata4: DUMMY
[    1.208360] ata5: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06300 irq 45
[    1.208362] ata6: DUMMY
[    1.208750] Fixed MDIO Bus: probed
[    1.208766] tun: Universal TUN/TAP device driver, 1.6
[    1.208767] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.208833] PPP generic driver version 2.4.2
[    1.208943] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.208960] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.208977] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.208981] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.209042] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.209078] ehci_hcd 0000:00:1a.0: debug port 2
[    1.213033] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.213048] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbf08000
[    1.227302] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.227454] hub 1-0:1.0: USB hub found
[    1.227459] hub 1-0:1.0: 2 ports detected
[    1.227526] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.227541] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.227545] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.227594] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.227623] ehci_hcd 0000:00:1d.0: debug port 2
[    1.231595] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.231612] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbf07000
[    1.247261] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.247401] hub 2-0:1.0: USB hub found
[    1.247404] hub 2-0:1.0: 2 ports detected
[    1.247461] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.247471] uhci_hcd: USB Universal Host Controller Interface driver
[    1.247515] usbcore: registered new interface driver libusual
[    1.247547] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.272294] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.272301] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.272438] mousedev: PS/2 mouse device common for all mice
[    1.273551] rtc_cmos 00:03: RTC can wake from S4
[    1.273674] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.273707] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.273781] device-mapper: uevent: version 1.0.3
[    1.273858] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.273951] cpuidle: using governor ladder
[    1.274089] cpuidle: using governor menu
[    1.274090] EFI Variables Facility v0.08 2004-May-17
[    1.274306] TCP cubic registered
[    1.274399] NET: Registered protocol family 10
[    1.274845] NET: Registered protocol family 17
[    1.274858] Registering the dns_resolver key type
[    1.275033] PM: Hibernation image not present or could not be loaded.
[    1.275050] registered taskstats version 1
[    1.291495]   Magic number: 4:901:271
[    1.291690] rtc_cmos 00:03: setting system clock to 2012-07-03 09:15:23 UTC (1341306923)
[    1.292888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.292890] EDD information not available.
[    1.302020] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.526808] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.526850] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.526887] ata5: SATA link down (SStatus 0 SControl 300)
[    1.538757] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.545384] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633C, DW40, max UDMA/100
[    1.545390] ata2.00: applying bridge limits
[    1.565854] ata2.00: configured for UDMA/100
[    1.572511] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ002D, max UDMA/100
[    1.572517] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.573570] ata1.00: configured for UDMA/100
[    1.573904] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
[    1.574139] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.574195] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.574429] sd 0:0:0:0: [sda] Write Protect is off
[    1.574432] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.574579] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.576088] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633C DW40 PQ: 0 ANSI: 5
[    1.583264] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.583270] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.583583] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.583720] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.671552] hub 1-1:1.0: USB hub found
[    1.671768] hub 1-1:1.0: 6 ports detected
[    1.704029]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 >
[    1.706288] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.707736] Freeing unused kernel memory: 920k freed
[    1.707879] Write protecting the kernel read-only data: 12288k
[    1.712585] Freeing unused kernel memory: 1604k freed
[    1.716256] Freeing unused kernel memory: 1196k freed
[    1.735193] udevd[106]: starting version 175
[    1.777770] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.777818] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.777859] r8169 0000:13:00.0: setting latency timer to 64
[    1.777928] r8169 0000:13:00.0: irq 46 for MSI/MSI-X
[    1.778614] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc9000064e000, a4:ba:db:b8:70:ba, XID 04e00000 IRQ 46
[    1.782225] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.898072] Refined TSC clocksource calibration: 2261.000 MHz.
[    1.898080] Switching to clocksource tsc
[    1.914786] hub 2-1:1.0: USB hub found
[    1.914822] hub 2-1:1.0: 8 ports detected
[    1.985981] usb 1-1.6: new full-speed USB device number 3 using ehci_hcd
[    2.129743] usb 1-1.6: new high-speed USB device number 4 using ehci_hcd
[    2.337286] usb 2-1.6: new full-speed USB device number 3 using ehci_hcd
[    2.431748] hub 2-1.6:1.0: USB hub found
[    2.431947] hub 2-1.6:1.0: 3 ports detected
[    2.700565] usb 2-1.6.1: new full-speed USB device number 4 using ehci_hcd
[    2.799522] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input5
[    2.799685] generic-usb 0003:413C:8161.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[    2.799710] usbcore: registered new interface driver usbhid
[    2.799714] usbhid: USB HID core driver
[    2.864258] usb 2-1.6.2: new full-speed USB device number 5 using ehci_hcd
[    2.966485] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input6
[    2.966702] generic-usb 0003:413C:8162.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[    2.998093] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   42.025119] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.353109] Adding 5957628k swap on /dev/sda9.  Priority:-1 extents:1 across:5957628k 
[   43.388353] udevd[445]: starting version 175
[   43.421391] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   43.421756] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   43.421766] mei 0000:00:16.0: setting latency timer to 64
[   43.421844] mei 0000:00:16.0: irq 47 for MSI/MSI-X
[   43.422861] lib80211: common routines for IEEE802.11 drivers
[   43.422864] lib80211_crypt: registered algorithm 'NULL'
[   43.428383] lp: driver loaded but no devices found
[   43.428900] wl: module license 'MIXED/Proprietary' taints kernel.
[   43.428905] Disabling lock debugging due to kernel taint
[   43.437254] wl 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   43.437264] wl 0000:12:00.0: setting latency timer to 64
[   43.438986] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   43.439000] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   43.439456] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   43.450629] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   43.479802] lib80211_crypt: registered algorithm 'TKIP'
[   43.487809] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   43.498629] acpi device:03: registered as cooling_device4
[   43.498840] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   43.498925] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   43.512344] [fglrx] Maximum main memory to use for locked dma buffers: 3659 MBytes.
[   43.512633] [fglrx]   vendor: 1002 device: 68e0 count: 1
[   43.513146] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   43.513166] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   43.513176] pci 0000:01:00.0: setting latency timer to 64
[   43.513423] [fglrx] Kernel PAT support is enabled
[   43.513447] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   43.558148] type=1400 audit(1341287165.843:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
[   43.558567] type=1400 audit(1341287165.843:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[   43.558805] type=1400 audit(1341287165.843:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
[   43.562495] wmi: Mapper loaded
[   43.562780] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   43.568040] Linux video capture interface: v2.00
[   43.568689] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6461)
[   43.573433] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   43.573505] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   43.573541] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   43.593278] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   43.652705] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   43.654191] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   43.654463] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   43.654552] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   43.654582] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   43.675194] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   43.675295] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   43.684648] input: Dell WMI hotkeys as /devices/virtual/input/input11
[   43.715612] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input12
[   43.715699] usbcore: registered new interface driver uvcvideo
[   43.715702] USB Video Class driver (1.1.1)
[   43.933935] EXT4-fs (sda8): re-mounted. Opts: (null)
[   44.383305] init: failsafe main process (795) killed by TERM signal
[   44.629030] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   44.671155] ppdev: user-space parallel port driver
[   44.703374] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   44.716631] Bluetooth: Core ver 2.16
[   44.716661] NET: Registered protocol family 31
[   44.716663] Bluetooth: HCI device and connection manager initialized
[   44.716667] Bluetooth: HCI socket layer initialized
[   44.716669] Bluetooth: L2CAP socket layer initialized
[   44.716930] Bluetooth: SCO socket layer initialized
[   44.721826] Bluetooth: RFCOMM TTY layer initialized
[   44.721833] Bluetooth: RFCOMM socket layer initialized
[   44.721836] Bluetooth: RFCOMM ver 1.11
[   44.722134] type=1400 audit(1341287167.011:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=863 comm="apparmor_parser"
[   44.723539] type=1400 audit(1341287167.011:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=863 comm="apparmor_parser"
[   44.728079] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.728083] Bluetooth: BNEP filters: protocol multicast
[   44.749249] type=1400 audit(1341287167.039:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=900 comm="apparmor_parser"
[   44.749262] type=1400 audit(1341287167.039:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=901 comm="apparmor_parser"
[   44.749840] type=1400 audit(1341287167.039:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=902 comm="apparmor_parser"
[   44.750264] type=1400 audit(1341287167.039:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
[   44.750519] type=1400 audit(1341287167.039:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
[   44.789954] r8169 0000:13:00.0: eth0: link down
[   44.790306] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.790612] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.740359] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   45.740363] vesafb: scrolling: redraw
[   45.740366] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   45.742414] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90011400000, using 3072k, total 3072k
[   45.743325] Console: switching to colour frame buffer device 128x48
[   45.743354] fb0: VESA VGA frame buffer device
[   45.759609] init: gdm main process (1072) killed by TERM signal
[   46.125341] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   46.126014] [fglrx] Firegl kernel thread PID: 1088
[   46.126108] [fglrx] Firegl kernel thread PID: 1089
[   46.126170] [fglrx] Firegl kernel thread PID: 1090
[   46.126270] [fglrx] IRQ 50 Enabled
[   46.254527] [fglrx] Gart USWC size:1196 M.
[   46.254530] [fglrx] Gart cacheable size:473 M.
[   46.254535] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   46.254537] [fglrx] Reserved FB block: Unshared offset:f941000, size:3bf000 
[   46.254539] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   48.200875] init: anacron main process (974) killed by TERM signal
[   76.869234] eth1: no IPv6 routers present
[  112.690723] init: plymouth-stop pre-start process (2205) terminated with status 1


I connect through wi-fi. And I can't see the files etc/modprobe.d/blacklist-ethernet.conf or /usr/sbin/ethtool in my  system. So, I couldn't try the solutions given above. My laptop runs win-7 and ubuntu 12.04. I upgraded from 11.10 to 12.04.  Please help. Please let me know if you need any further details.

---

