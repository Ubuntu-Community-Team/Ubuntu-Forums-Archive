---
title: "disk full error, know it cant be"
date: 2012-09-26
forum: General Help
---

### Post by netopalis45 on 2012-09-26
The past couple days I have been getting a disk full error even though I know that it can't be full. I have 1.5TB of space and haven't installed anything nor added more than a couple text files. It has gotten to the point that most Java applications will not run and the classic Gnome panel will not load on login. When I try to start it from terminal I get this error
```
** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/activate_window_menu': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/activate_window_menu

** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/toggle_maximized': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/toggle_maximized

** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/maximize': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/maximize

** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/unmaximize': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/unmaximize

** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/toggle_shaded': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/toggle_shaded

** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/begin_move': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/begin_move

** (gnome-panel:3161): WARNING **: Error getting value for '/apps/metacity/window_keybindings/begin_resize': Type mismatch: Expected `string' got `list' for key /apps/metacity/window_keybindings/begin_resize
Segmentation fault (core dumped)

```

When I tried to use the disk usage analyser it says that my /home folder contains over 400GB of data but when I look through the sizes of all the files it just doesn't add up. This is making my computer unusable and I really want to avoid reinstalling Ubuntu but as far as I can tell that may be my only option. Any help would be much appreciated.

---

### Post by HiImTye on 2012-09-27
paste the output of
```
df -h
```

---

### Post by Rexilion on 2012-09-27
Maybe also provide which filesystem you are using?

---

### Post by netopalis45 on 2012-09-27
Thanks for the replies. I left my computer off overnight and now it says that I have about 87GB worth of data instead of over 400. Not sure why this happened but for now it is fixed.

---

### Post by Rexilion on 2012-09-27
You should check 'sudo dmesg' for pointers, this is not normal.

---

### Post by netopalis45 on 2012-09-27
Just did that but I don't really know what it means. Maybe you could shed some light.

```

  	 	 	 	 	 	   [    0.000000] Initializing cgroup subsys cpuset [    0.000000] Initializing cgroup subsys cpu [    0.000000] Linux version 3.2.0-31-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic 3.2.28) [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=4cd0557b-8f88-403a-a559-f8135e4acb9e ro quiet splash vt.handoff=7 [    0.000000] KERNEL supported cpus: [    0.000000]   Intel GenuineIntel [    0.000000]   AMD AuthenticAMD [    0.000000]   Centaur CentaurHauls [    0.000000] BIOS-provided physical RAM map: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable) [    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved) [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) [    0.000000]  BIOS-e820: 0000000000100000 - 00000000ddc0f000 (usable) [    0.000000]  BIOS-e820: 00000000ddc0f000 - 00000000ddfd9000 (reserved) [    0.000000]  BIOS-e820: 00000000ddfd9000 - 00000000ddfdb000 (usable) [    0.000000]  BIOS-e820: 00000000ddfdb000 - 00000000de5e0000 (reserved) [    0.000000]  BIOS-e820: 00000000de5e0000 - 00000000de834000 (ACPI NVS) [    0.000000]  BIOS-e820: 00000000de834000 - 00000000de841000 (ACPI data) [    0.000000]  BIOS-e820: 00000000de841000 - 00000000de860000 (ACPI NVS) [    0.000000]  BIOS-e820: 00000000de860000 - 00000000de865000 (ACPI data) [    0.000000]  BIOS-e820: 00000000de865000 - 00000000de8a8000 (ACPI NVS) [    0.000000]  BIOS-e820: 00000000de8a8000 - 00000000decb8000 (usable) [    0.000000]  BIOS-e820: 00000000decb8000 - 00000000deff4000 (reserved) [    0.000000]  BIOS-e820: 00000000deff4000 - 00000000df000000 (usable) [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved) [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved) [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved) [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved) [    0.000000]  BIOS-e820: 0000000100000000 - 000000019f000000 (usable) [    0.000000] NX (Execute Disable) protection: active [    0.000000] DMI 2.7 present. [    0.000000] DMI: System manufacturer System Product Name/P8Z77-V LK, BIOS 0404 05/23/2012 [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved) [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable) [    0.000000] No AGP bridge found [    0.000000] last_pfn = 0x19f000 max_arch_pfn = 0x400000000 [    0.000000] MTRR default type: uncachable [    0.000000] MTRR fixed ranges enabled: [    0.000000]   00000-9FFFF write-back [    0.000000]   A0000-BFFFF uncachable [    0.000000]   C0000-CFFFF write-protect [    0.000000]   D0000-E7FFF uncachable [    0.000000]   E8000-FFFFF write-protect [    0.000000] MTRR variable ranges enabled: [    0.000000]   0 base 000000000 mask F00000000 write-back [    0.000000]   1 base 100000000 mask F80000000 write-back [    0.000000]   2 base 180000000 mask FF0000000 write-back [    0.000000]   3 base 190000000 mask FF8000000 write-back [    0.000000]   4 base 198000000 mask FFC000000 write-back [    0.000000]   5 base 19C000000 mask FFE000000 write-back [    0.000000]   6 base 19E000000 mask FFF000000 write-back [    0.000000]   7 base 0E0000000 mask FE0000000 uncachable [    0.000000]   8 disabled [    0.000000]   9 disabled [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 [    0.000000] original variable MTRRs [    0.000000] reg 0, base: 0GB, range: 4GB, type WB [    0.000000] reg 1, base: 4GB, range: 2GB, type WB [    0.000000] reg 2, base: 6GB, range: 256MB, type WB [    0.000000] reg 3, base: 6400MB, range: 128MB, type WB [    0.000000] reg 4, base: 6528MB, range: 64MB, type WB [    0.000000] reg 5, base: 6592MB, range: 32MB, type WB [    0.000000] reg 6, base: 6624MB, range: 16MB, type WB [    0.000000] reg 7, base: 3584MB, range: 512MB, type UC [    0.000000] total RAM covered: 6128M [    0.000000] Found optimal setting for mtrr clean up [    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 6  	lose cover RAM: 0G [    0.000000] New variable MTRRs [    0.000000] reg 0, base: 0GB, range: 2GB, type WB [    0.000000] reg 1, base: 2GB, range: 1GB, type WB [    0.000000] reg 2, base: 3GB, range: 512MB, type WB [    0.000000] reg 3, base: 4GB, range: 2GB, type WB [    0.000000] reg 4, base: 6GB, range: 512MB, type WB [    0.000000] reg 5, base: 6640MB, range: 16MB, type UC [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved) [    0.000000] last_pfn = 0xdf000 max_arch_pfn = 0x400000000 [    0.000000] found SMP MP-table at [ffff8800000fcd00] fcd00 [    0.000000] initial memory mapped : 0 - 20000000 [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480 [    0.000000] init_memory_mapping: 0000000000000000-00000000df000000 [    0.000000]  0000000000 - 00df000000 page 2M [    0.000000] kernel direct mapping tables up to df000000 @ 1fffb000-20000000 [    0.000000] init_memory_mapping: 0000000100000000-000000019f000000 [    0.000000]  0100000000 - 019f000000 page 2M [    0.000000] kernel direct mapping tables up to 19f000000 @ deff8000-df000000 [    0.000000] RAMDISK: 358ec000 - 36c6e000 [    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA) [    0.000000] ACPI: XSDT 00000000de834070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013) [    0.000000] ACPI: FACP 00000000de83e9a8 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013) [    0.000000] ACPI: DSDT 00000000de834168 0A83E (v02 ALASKA    A M I 00000015 INTL 20051117) [    0.000000] ACPI: FACS 00000000de85ef80 00040 [    0.000000] ACPI: APIC 00000000de83eaa0 00072 (v03 ALASKA    A M I 01072009 AMI  00010013) [    0.000000] ACPI: MCFG 00000000de83eb18 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097) [    0.000000] ACPI: HPET 00000000de83eb58 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005) [    0.000000] ACPI: SSDT 00000000de83eb90 0036D (v01 SataRe SataTabl 00001000 INTL 20091112) [    0.000000] ACPI: SSDT 00000000de83ef00 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117) [    0.000000] ACPI: SSDT 00000000de83f8b0 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117) [    0.000000] ACPI: BGRT 00000000de840348 00038 (v00 ALASKA    A M I 01072009 AMI  00010013) [    0.000000] ACPI: Local APIC address 0xfee00000 [    0.000000] No NUMA configuration found [    0.000000] Faking a node at 0000000000000000-000000019f000000 [    0.000000] Initmem setup node 0 0000000000000000-000000019f000000 [    0.000000]   NODE_DATA [000000019effb000 - 000000019effffff] [    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880198600000-ffff88019e5fffff] on node 0 [    0.000000] Zone PFN ranges: [    0.000000]   DMA      0x00000010 -> 0x00001000 [    0.000000]   DMA32    0x00001000 -> 0x00100000 [    0.000000]   Normal   0x00100000 -> 0x0019f000 [    0.000000] Movable zone start PFN for each node [    0.000000] early_node_map[6] active PFN ranges [    0.000000]     0: 0x00000010 -> 0x0000009d [    0.000000]     0: 0x00000100 -> 0x000ddc0f [    0.000000]     0: 0x000ddfd9 -> 0x000ddfdb [    0.000000]     0: 0x000de8a8 -> 0x000decb8 [    0.000000]     0: 0x000deff4 -> 0x000df000 [    0.000000]     0: 0x00100000 -> 0x0019f000 [    0.000000] On node 0 totalpages: 1560506 [    0.000000]   DMA zone: 64 pages used for memmap [    0.000000]   DMA zone: 5 pages reserved [    0.000000]   DMA zone: 3912 pages, LIFO batch:0 [    0.000000]   DMA32 zone: 16320 pages used for memmap [    0.000000]   DMA32 zone: 888941 pages, LIFO batch:31 [    0.000000]   Normal zone: 10176 pages used for memmap [    0.000000]   Normal zone: 641088 pages, LIFO batch:31 [    0.000000] ACPI: PM-Timer IO Port: 0x408 [    0.000000] ACPI: Local APIC address 0xfee00000 [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled) [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled) [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled) [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1]) [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23 [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) [    0.000000] ACPI: IRQ0 used by override. [    0.000000] ACPI: IRQ2 used by override. [    0.000000] ACPI: IRQ9 used by override. [    0.000000] Using ACPI (MADT) for SMP configuration information [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000 [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs [    0.000000] nr_irqs_gsi: 40 [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000 [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000 [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000 [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000 [    0.000000] PM: Registered nosave memory: 00000000ddc0f000 - 00000000ddfd9000 [    0.000000] PM: Registered nosave memory: 00000000ddfdb000 - 00000000de5e0000 [    0.000000] PM: Registered nosave memory: 00000000de5e0000 - 00000000de834000 [    0.000000] PM: Registered nosave memory: 00000000de834000 - 00000000de841000 [    0.000000] PM: Registered nosave memory: 00000000de841000 - 00000000de860000 [    0.000000] PM: Registered nosave memory: 00000000de860000 - 00000000de865000 [    0.000000] PM: Registered nosave memory: 00000000de865000 - 00000000de8a8000 [    0.000000] PM: Registered nosave memory: 00000000decb8000 - 00000000deff4000 [    0.000000] PM: Registered nosave memory: 00000000df000000 - 00000000f8000000 [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000 [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000 [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000 [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000 [    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000 [    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000 [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000 [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000 [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000 [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000 [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000 [    0.000000] Allocating PCI resources starting at df000000 (gap: df000000:19000000) [    0.000000] Booting paravirtualized kernel on bare hardware [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1 [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019ec00000 s83136 r8192 d23360 u524288 [    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152 [    0.000000] pcpu-alloc: [0] 0 1 2 3  [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1533941 [    0.000000] Policy zone: Normal [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=4cd0557b-8f88-403a-a559-f8135e4acb9e ro quiet splash vt.handoff=7 [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes) [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340 [    0.000000] Checking aperture... [    0.000000] No AGP bridge found [    0.000000] Calgary: detecting Calgary via BIOS EBDA area [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing! [    0.000000] Memory: 6041400k/6799360k available (6558k kernel code, 557336k absent, 200624k reserved, 6642k data, 920k init) [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1 [    0.000000] Hierarchical RCU implementation. [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled. [    0.000000] NR_IRQS:16640 nr_irqs:712 16 [    0.000000] Extended CMOS year: 2000 [    0.000000] vt handoff: transparent VT on vt#7 [    0.000000] Console: colour dummy device 80x25 [    0.000000] console [tty0] enabled [    0.000000] allocated 50331648 bytes of page_cgroup [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups [    0.000000] hpet clockevent registered [    0.000000] Fast TSC calibration using PIT [    0.004000] Detected 3410.097 MHz processor. [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6820.19 BogoMIPS (lpj=13640388) [    0.000004] pid_max: default: 32768 minimum: 301 [    0.000019] Security Framework initialized [    0.000027] AppArmor: AppArmor initialized [    0.000028] Yama: becoming mindful. [    0.000389] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes) [    0.001811] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes) [    0.002434] Mount-cache hash table entries: 256 [    0.002501] Initializing cgroup subsys cpuacct [    0.002503] Initializing cgroup subsys memory [    0.002508] Initializing cgroup subsys devices [    0.002509] Initializing cgroup subsys freezer [    0.002511] Initializing cgroup subsys blkio [    0.002514] Initializing cgroup subsys perf_event [    0.002532] CPU: Physical Processor ID: 0 [    0.002532] CPU: Processor Core ID: 0 [    0.002536] ENERGY_PERF_BIAS: Set to 'normal', was 'performance' [    0.002537] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8) [    0.002795] mce: CPU supports 9 MCE banks [    0.002805] CPU0: Thermal monitoring enabled (TM1) [    0.002810] using mwait in idle threads. [    0.004229] ACPI: Core revision 20110623 [    0.073824] ftrace: allocating 27008 entries in 106 pages [    0.080254] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 [    0.119900] CPU0: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz stepping 09 [    0.224577] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver. [    0.224581] ... version:                3 [    0.224582] ... bit width:              48 [    0.224582] ... generic registers:      8 [    0.224583] ... value mask:             0000ffffffffffff [    0.224584] ... max period:             000000007fffffff [    0.224585] ... fixed-purpose events:   3 [    0.224585] ... event mask:             00000007000000ff [    0.224664] NMI watchdog enabled, takes one hw-pmu counter. [    0.224714] Booting Node   0, Processors  #1 [    0.224715] smpboot cpu 1: start_ip = 98000 [    0.332832] NMI watchdog enabled, takes one hw-pmu counter. [    0.332890]  #2 [    0.332891] smpboot cpu 2: start_ip = 98000 [    0.440705] NMI watchdog enabled, takes one hw-pmu counter. [    0.440759]  #3 Ok. [    0.440760] smpboot cpu 3: start_ip = 98000 [    0.548674] NMI watchdog enabled, takes one hw-pmu counter. [    0.548696] Brought up 4 CPUs [    0.548698] Total of 4 processors activated (27279.89 BogoMIPS). [    0.551322] devtmpfs: initialized [    0.551807] EVM: security.selinux [    0.551808] EVM: security.SMACK64 [    0.551809] EVM: security.capability [    0.551823] PM: Registering ACPI NVS region at de5e0000 (2441216 bytes) [    0.551845] PM: Registering ACPI NVS region at de841000 (126976 bytes) [    0.551847] PM: Registering ACPI NVS region at de865000 (274432 bytes) [    0.552338] print_constraints: dummy:  [    0.552364] RTC time: 15:20:51, date: 09/27/12 [    0.552382] NET: Registered protocol family 16 [    0.552440] Trying to unpack rootfs image as initramfs... [    0.552444] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it [    0.552445] ACPI: bus type pci registered [    0.552482] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000) [    0.552483] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820 [    0.562620] PCI: Using configuration type 1 for base access [    0.563115] bio: create slab <bio-0> at 0 [    0.563157] ACPI: Added _OSI(Module Device) [    0.563158] ACPI: Added _OSI(Processor Device) [    0.563159] ACPI: Added _OSI(3.0 _SCP Extensions) [    0.563160] ACPI: Added _OSI(Processor Aggregator Device) [    0.564094] ACPI: EC: Look up EC in DSDT [    0.565157] ACPI: Executed 1 blocks of module-level executable AML code [    0.596472] ACPI: SSDT 00000000de58d018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117) [    0.596707] ACPI: Dynamic OEM Table Load: [    0.596709] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117) [    0.620324] ACPI: SSDT 00000000de58ea98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117) [    0.620575] ACPI: Dynamic OEM Table Load: [    0.620577] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117) [    0.644222] ACPI: SSDT 00000000de58fc18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117) [    0.644453] ACPI: Dynamic OEM Table Load: [    0.644455] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117) [    0.668501] ACPI: Interpreter enabled [    0.668504] ACPI: (supports S0 S1 S3 S4 S5) [    0.668519] ACPI: Using IOAPIC for interrupt routing [    0.671657] ACPI: Power Resource [FN00] (off) [    0.671704] ACPI: Power Resource [FN01] (off) [    0.671746] ACPI: Power Resource [FN02] (off) [    0.671789] ACPI: Power Resource [FN03] (off) [    0.671831] ACPI: Power Resource [FN04] (off) [    0.672119] ACPI: No dock devices found. [    0.672120] HEST: Table not found. [    0.672122] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug [    0.672315] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e]) [    0.672587] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] [    0.672588] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] [    0.672590] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] [    0.672591] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] [    0.672592] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] [    0.672594] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] [    0.672595] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] [    0.672596] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff] [    0.672597] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff] [    0.672599] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfeafffff] [    0.672607] pci 0000:00:00.0: [8086:0150] type 0 class 0x000600 [    0.672633] pci 0000:00:01.0: [8086:0151] type 1 class 0x000604 [    0.672654] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold [    0.672656] pci 0000:00:01.0: PME# disabled [    0.672692] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03 [    0.672712] pci 0000:00:14.0: reg 10: [mem 0xf7200000-0xf720ffff 64bit] [    0.672777] pci 0000:00:14.0: PME# supported from D3hot D3cold [    0.672780] pci 0000:00:14.0: PME# disabled [    0.672797] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780 [    0.672818] pci 0000:00:16.0: reg 10: [mem 0xf721a000-0xf721a00f 64bit] [    0.672885] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold [    0.672887] pci 0000:00:16.0: PME# disabled [    0.672914] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03 [    0.672933] pci 0000:00:1a.0: reg 10: [mem 0xf7218000-0xf72183ff] [    0.673016] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold [    0.673019] pci 0000:00:1a.0: PME# disabled [    0.673039] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403 [    0.673052] pci 0000:00:1b.0: reg 10: [mem 0xf7210000-0xf7213fff 64bit] [    0.673113] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold [    0.673115] pci 0000:00:1b.0: PME# disabled [    0.673138] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604 [    0.673264] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold [    0.673268] pci 0000:00:1c.0: PME# disabled [    0.673297] pci 0000:00:1c.4: [8086:1e18] type 1 class 0x000604 [    0.673369] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold [    0.673372] pci 0000:00:1c.4: PME# disabled [    0.673391] pci 0000:00:1c.5: [8086:244e] type 1 class 0x000604 [    0.673463] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold [    0.673466] pci 0000:00:1c.5: PME# disabled [    0.673486] pci 0000:00:1c.7: [8086:1e1e] type 1 class 0x000604 [    0.673558] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold [    0.673561] pci 0000:00:1c.7: PME# disabled [    0.673585] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03 [    0.673604] pci 0000:00:1d.0: reg 10: [mem 0xf7217000-0xf72173ff] [    0.673686] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold [    0.673690] pci 0000:00:1d.0: PME# disabled [    0.673709] pci 0000:00:1f.0: [8086:1e44] type 0 class 0x000601 [    0.673823] pci 0000:00:1f.2: [8086:1e02] type 0 class 0x000106 [    0.673839] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077] [    0.673845] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063] [    0.673852] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057] [    0.673858] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043] [    0.673865] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f] [    0.673871] pci 0000:00:1f.2: reg 24: [mem 0xf7216000-0xf72167ff] [    0.673911] pci 0000:00:1f.2: PME# supported from D3hot [    0.673913] pci 0000:00:1f.2: PME# disabled [    0.673926] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05 [    0.673939] pci 0000:00:1f.3: reg 10: [mem 0xf7215000-0xf72150ff 64bit] [    0.673958] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f] [    0.674002] pci 0000:01:00.0: [10de:104a] type 0 class 0x000300 [    0.674008] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff] [    0.674016] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref] [    0.674023] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref] [    0.674028] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f] [    0.674033] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref] [    0.674072] pci 0000:01:00.1: [10de:0e08] type 0 class 0x000403 [    0.674078] pci 0000:01:00.1: reg 10: [mem 0xf7080000-0xf7083fff] [    0.680133] pci 0000:00:01.0: PCI bridge to [bus 01-01] [    0.680135] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff] [    0.680137] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff] [    0.680140] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref] [    0.680208] pci 0000:00:1c.0: PCI bridge to [bus 02-02] [    0.680280] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200 [    0.680299] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff] [    0.680331] pci 0000:03:00.0: reg 18: [mem 0xf2104000-0xf2104fff 64bit pref] [    0.680351] pci 0000:03:00.0: reg 20: [mem 0xf2100000-0xf2103fff 64bit pref] [    0.680439] pci 0000:03:00.0: supports D1 D2 [    0.680440] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold [    0.680444] pci 0000:03:00.0: PME# disabled [    0.688129] pci 0000:00:1c.4: PCI bridge to [bus 03-03] [    0.688132] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff] [    0.688139] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref] [    0.688192] pci 0000:04:00.0: [1b21:1080] type 1 class 0x000604 [    0.688307] pci 0000:00:1c.5: PCI bridge to [bus 04-05] (subtractive decode) [    0.688317] pci 0000:00:1c.5:   bridge window [io  0x0000-0x0cf7] (subtractive decode) [    0.688318] pci 0000:00:1c.5:   bridge window [io  0x0d00-0xffff] (subtractive decode) [    0.688319] pci 0000:00:1c.5:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode) [    0.688321] pci 0000:00:1c.5:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode) [    0.688322] pci 0000:00:1c.5:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode) [    0.688323] pci 0000:00:1c.5:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode) [    0.688324] pci 0000:00:1c.5:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode) [    0.688326] pci 0000:00:1c.5:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode) [    0.688327] pci 0000:00:1c.5:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode) [    0.688328] pci 0000:00:1c.5:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode) [    0.688438] pci 0000:04:00.0: PCI bridge to [bus 05-05] (subtractive decode) [    0.688458] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode) [    0.688460] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode) [    0.688461] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode) [    0.688462] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode) [    0.688463] pci 0000:04:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode) [    0.688465] pci 0000:04:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode) [    0.688466] pci 0000:04:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode) [    0.688467] pci 0000:04:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode) [    0.688469] pci 0000:04:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode) [    0.688470] pci 0000:04:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode) [    0.688471] pci 0000:04:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode) [    0.688472] pci 0000:04:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode) [    0.688474] pci 0000:04:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode) [    0.688475] pci 0000:04:00.0:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode) [    0.688551] pci 0000:06:00.0: [1b21:1042] type 0 class 0x000c03 [    0.688578] pci 0000:06:00.0: reg 10: [mem 0xf7100000-0xf7107fff 64bit] [    0.688719] pci 0000:06:00.0: PME# supported from D3hot D3cold [    0.688724] pci 0000:06:00.0: PME# disabled [    0.696120] pci 0000:00:1c.7: PCI bridge to [bus 06-06] [    0.696125] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff] [    0.696152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] [    0.696220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT] [    0.696243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT] [    0.696263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT] [    0.696282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06.P9PE._PRT] [    0.696305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT] [    0.696327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT] [    0.696403]  pci0000:00: Requesting ACPI _OSC control (0x1d) [    0.696517]  pci0000:00: ACPI _OSC control (0x18) granted [    0.698685] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15) [    0.698714] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15) [    0.698741] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 10 11 12 14 15) [    0.698767] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15) [    0.698793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled. [    0.698822] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 *15) [    0.698848] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 *14 15) [    0.698873] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15) [    0.698940] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none [    0.698942] vgaarb: loaded [    0.698943] vgaarb: bridge control possible 0000:01:00.0 [    0.698994] i2c-core: driver [aat2870] using legacy suspend method [    0.698995] i2c-core: driver [aat2870] using legacy resume method [    0.699029] SCSI subsystem initialized [    0.699057] libata version 3.00 loaded. [    0.699082] usbcore: registered new interface driver usbfs [    0.699088] usbcore: registered new interface driver hub [    0.699099] usbcore: registered new device driver usb [    0.699141] PCI: Using ACPI for IRQ routing [    0.700494] PCI: pci_cache_line_size set to 64 bytes [    0.700549] reserve RAM buffer: 000000000009d800 - 000000000009ffff  [    0.700551] reserve RAM buffer: 00000000ddc0f000 - 00000000dfffffff  [    0.700552] reserve RAM buffer: 00000000ddfdb000 - 00000000dfffffff  [    0.700554] reserve RAM buffer: 00000000decb8000 - 00000000dfffffff  [    0.700555] reserve RAM buffer: 00000000df000000 - 00000000dfffffff  [    0.700556] reserve RAM buffer: 000000019f000000 - 000000019fffffff  [    0.700610] NetLabel: Initializing [    0.700611] NetLabel:  domain hash size = 128 [    0.700612] NetLabel:  protocols = UNLABELED CIPSOv4 [    0.700618] NetLabel:  unlabeled traffic allowed by default [    0.700647] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0 [    0.700650] hpet0: 8 comparators, 64-bit 14.318180 MHz counter [    0.702659] Switching to clocksource hpet [    0.706096] AppArmor: AppArmor Filesystem Enabled [    0.706106] pnp: PnP ACPI init [    0.706114] ACPI: bus type pnp registered [    0.706270] pnp 00:00: [bus 00-3e] [    0.706272] pnp 00:00: [io  0x0000-0x0cf7 window] [    0.706273] pnp 00:00: [io  0x0cf8-0x0cff] [    0.706274] pnp 00:00: [io  0x0d00-0xffff window] [    0.706275] pnp 00:00: [mem 0x000a0000-0x000bffff window] [    0.706276] pnp 00:00: [mem 0x000c0000-0x000c3fff window] [    0.706278] pnp 00:00: [mem 0x000c4000-0x000c7fff window] [    0.706279] pnp 00:00: [mem 0x000c8000-0x000cbfff window] [    0.706280] pnp 00:00: [mem 0x000cc000-0x000cffff window] [    0.706281] pnp 00:00: [mem 0x000d0000-0x000d3fff window] [    0.706282] pnp 00:00: [mem 0x000d4000-0x000d7fff window] [    0.706284] pnp 00:00: [mem 0x000d8000-0x000dbfff window] [    0.706285] pnp 00:00: [mem 0x000dc000-0x000dffff window] [    0.706286] pnp 00:00: [mem 0x000e0000-0x000e3fff window] [    0.706287] pnp 00:00: [mem 0x000e4000-0x000e7fff window] [    0.706288] pnp 00:00: [mem 0x000e8000-0x000ebfff window] [    0.706289] pnp 00:00: [mem 0x000ec000-0x000effff window] [    0.706291] pnp 00:00: [mem 0x000f0000-0x000fffff window] [    0.706292] pnp 00:00: [mem 0xe0000000-0xfeafffff window] [    0.706293] pnp 00:00: [mem 0x00010000-0x0001ffff window] [    0.706329] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active) [    0.706345] pnp 00:01: [mem 0xfed40000-0xfed44fff] [    0.706368] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved [    0.706370] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active) [    0.706378] pnp 00:02: [io  0x0000-0x001f] [    0.706379] pnp 00:02: [io  0x0081-0x0091] [    0.706380] pnp 00:02: [io  0x0093-0x009f] [    0.706380] pnp 00:02: [io  0x00c0-0x00df] [    0.706382] pnp 00:02: [dma 4] [    0.706393] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active) [    0.706397] pnp 00:03: [mem 0xff000000-0xffffffff] [    0.706408] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active) [    0.706452] pnp 00:04: [mem 0xfed00000-0xfed003ff] [    0.706464] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active) [    0.706470] pnp 00:05: [io  0x002e-0x002f] [    0.706471] pnp 00:05: [io  0x004e-0x004f] [    0.706472] pnp 00:05: [io  0x0061] [    0.706473] pnp 00:05: [io  0x0063] [    0.706474] pnp 00:05: [io  0x0065] [    0.706475] pnp 00:05: [io  0x0067] [    0.706476] pnp 00:05: [io  0x0070] [    0.706476] pnp 00:05: [io  0x0080] [    0.706477] pnp 00:05: [io  0x0092] [    0.706478] pnp 00:05: [io  0x00b2-0x00b3] [    0.706479] pnp 00:05: [io  0x0680-0x069f] [    0.706480] pnp 00:05: [io  0x0200-0x020f] [    0.706481] pnp 00:05: [io  0xffff] [    0.706482] pnp 00:05: [io  0xffff] [    0.706483] pnp 00:05: [io  0x0400-0x0453] [    0.706484] pnp 00:05: [io  0x0458-0x047f] [    0.706484] pnp 00:05: [io  0x0500-0x057f] [    0.706485] pnp 00:05: [io  0x164e-0x164f] [    0.706508] system 00:05: [io  0x0680-0x069f] has been reserved [    0.706509] system 00:05: [io  0x0200-0x020f] has been reserved [    0.706510] system 00:05: [io  0xffff] has been reserved [    0.706512] system 00:05: [io  0xffff] has been reserved [    0.706514] system 00:05: [io  0x0400-0x0453] has been reserved [    0.706515] system 00:05: [io  0x0458-0x047f] has been reserved [    0.706516] system 00:05: [io  0x0500-0x057f] has been reserved [    0.706517] system 00:05: [io  0x164e-0x164f] has been reserved [    0.706519] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active) [    0.706524] pnp 00:06: [io  0x0070-0x0077] [    0.706531] pnp 00:06: [irq 8] [    0.706542] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active) [    0.706557] pnp 00:07: [io  0x0454-0x0457] [    0.706576] system 00:07: [io  0x0454-0x0457] has been reserved [    0.706578] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active) [    0.706611] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled] [    0.706613] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled] [    0.706614] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled] [    0.706615] pnp 00:08: [io  0x0290-0x029f] [    0.706616] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled] [    0.706636] system 00:08: [io  0x0290-0x029f] has been reserved [    0.706638] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active) [    0.706650] pnp 00:09: [io  0x0010-0x001f] [    0.706651] pnp 00:09: [io  0x0022-0x003f] [    0.706652] pnp 00:09: [io  0x0044-0x005f] [    0.706653] pnp 00:09: [io  0x0062-0x0063] [    0.706654] pnp 00:09: [io  0x0065-0x006f] [    0.706655] pnp 00:09: [io  0x0072-0x007f] [    0.706655] pnp 00:09: [io  0x0080] [    0.706656] pnp 00:09: [io  0x0084-0x0086] [    0.706657] pnp 00:09: [io  0x0088] [    0.706658] pnp 00:09: [io  0x008c-0x008e] [    0.706660] pnp 00:09: [io  0x0090-0x009f] [    0.706661] pnp 00:09: [io  0x00a2-0x00bf] [    0.706662] pnp 00:09: [io  0x00e0-0x00ef] [    0.706663] pnp 00:09: [io  0x04d0-0x04d1] [    0.706690] system 00:09: [io  0x04d0-0x04d1] has been reserved [    0.706692] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active) [    0.706697] pnp 00:0a: [io  0x00f0-0x00ff] [    0.706701] pnp 00:0a: [irq 13] [    0.706712] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active) [    0.706848] pnp 00:0b: [io  0x03f8-0x03ff] [    0.706852] pnp 00:0b: [irq 4] [    0.706853] pnp 00:0b: [dma 0 disabled] [    0.706885] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active) [    0.707001] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff] [    0.707002] pnp 00:0c: [mem 0xfed10000-0xfed17fff] [    0.707003] pnp 00:0c: [mem 0xfed18000-0xfed18fff] [    0.707004] pnp 00:0c: [mem 0xfed19000-0xfed19fff] [    0.707005] pnp 00:0c: [mem 0xf8000000-0xfbffffff] [    0.707006] pnp 00:0c: [mem 0xfed20000-0xfed3ffff] [    0.707007] pnp 00:0c: [mem 0xfed90000-0xfed93fff] [    0.707008] pnp 00:0c: [mem 0xfed45000-0xfed8ffff] [    0.707009] pnp 00:0c: [mem 0xff000000-0xffffffff] [    0.707010] pnp 00:0c: [mem 0xfee00000-0xfeefffff] [    0.707011] pnp 00:0c: [mem 0xe0000000-0xe0000fff] [    0.707044] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved [    0.707046] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved [    0.707047] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved [    0.707048] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved [    0.707050] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved [    0.707051] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved [    0.707052] system 00:0c: [mem 0xfed90000-0xfed93fff] has been reserved [    0.707054] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved [    0.707055] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved [    0.707057] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved [    0.707058] system 00:0c: [mem 0xe0000000-0xe0000fff] has been reserved [    0.707060] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active) [    0.707135] pnp: PnP ACPI: found 13 devices [    0.707136] ACPI: ACPI bus type pnp unregistered [    0.712844] PCI: max bus depth: 2 pci_try_num: 3 [    0.712890] pci 0000:00:01.0: PCI bridge to [bus 01-01] [    0.712892] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff] [    0.712894] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff] [    0.712896] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref] [    0.712899] pci 0000:00:1c.0: PCI bridge to [bus 02-02] [    0.712914] pci 0000:00:1c.4: PCI bridge to [bus 03-03] [    0.712916] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff] [    0.712922] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref] [    0.712927] pci 0000:04:00.0: PCI bridge to [bus 05-05] [    0.712945] pci 0000:00:1c.5: PCI bridge to [bus 04-05] [    0.712955] pci 0000:00:1c.7: PCI bridge to [bus 06-06] [    0.712958] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff] [    0.712972] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    0.712974] pci 0000:00:01.0: setting latency timer to 64 [    0.712979] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    0.712983] pci 0000:00:1c.0: setting latency timer to 64 [    0.712987] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    0.712990] pci 0000:00:1c.4: setting latency timer to 64 [    0.712996] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17 [    0.712999] pci 0000:00:1c.5: setting latency timer to 64 [    0.713005] pci 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 [    0.713009] pci 0000:04:00.0: setting latency timer to 64 [    0.713018] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19 [    0.713021] pci 0000:00:1c.7: setting latency timer to 64 [    0.713023] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7] [    0.713025] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff] [    0.713026] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff] [    0.713027] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff] [    0.713028] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff] [    0.713029] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff] [    0.713030] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff] [    0.713032] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff] [    0.713033] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff] [    0.713034] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff] [    0.713035] pci_bus 0000:01: resource 0 [io  0xe000-0xefff] [    0.713036] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff] [    0.713038] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref] [    0.713039] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff] [    0.713040] pci_bus 0000:03: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref] [    0.713042] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7] [    0.713043] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff] [    0.713044] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff] [    0.713045] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000d3fff] [    0.713046] pci_bus 0000:04: resource 8 [mem 0x000d4000-0x000d7fff] [    0.713047] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000dbfff] [    0.713049] pci_bus 0000:04: resource 10 [mem 0x000dc000-0x000dffff] [    0.713050] pci_bus 0000:04: resource 11 [mem 0x000e0000-0x000e3fff] [    0.713051] pci_bus 0000:04: resource 12 [mem 0x000e4000-0x000e7fff] [    0.713052] pci_bus 0000:04: resource 13 [mem 0xe0000000-0xfeafffff] [    0.713054] pci_bus 0000:05: resource 8 [io  0x0000-0x0cf7] [    0.713055] pci_bus 0000:05: resource 9 [io  0x0d00-0xffff] [    0.713056] pci_bus 0000:05: resource 10 [mem 0x000a0000-0x000bffff] [    0.713057] pci_bus 0000:05: resource 11 [mem 0x000d0000-0x000d3fff] [    0.713058] pci_bus 0000:05: resource 12 [mem 0x000d4000-0x000d7fff] [    0.713059] pci_bus 0000:05: resource 13 [mem 0x000d8000-0x000dbfff] [    0.713060] pci_bus 0000:05: resource 14 [mem 0x000dc000-0x000dffff] [    0.713062] pci_bus 0000:05: resource 15 [mem 0x000e0000-0x000e3fff] [    0.713063] pci_bus 0000:05: resource 16 [mem 0x000e4000-0x000e7fff] [    0.713064] pci_bus 0000:05: resource 17 [mem 0xe0000000-0xfeafffff] [    0.713065] pci_bus 0000:06: resource 1 [mem 0xf7100000-0xf71fffff] [    0.713083] NET: Registered protocol family 2 [    0.713191] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes) [    0.713671] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) [    0.714577] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) [    0.714704] TCP: Hash tables configured (established 524288 bind 65536) [    0.714705] TCP reno registered [    0.714715] UDP hash table entries: 4096 (order: 5, 131072 bytes) [    0.714736] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes) [    0.714793] NET: Registered protocol family 1 [    0.714806] pci 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    0.714854] pci 0000:00:14.0: PCI INT A disabled [    0.714865] pci 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 [    0.734666] pci 0000:00:1a.0: PCI INT A disabled [    0.734681] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 [    0.754646] pci 0000:00:1d.0: PCI INT A disabled [    0.754661] pci 0000:01:00.0: Boot video device [    0.754679] pci 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 [    0.754713] pci 0000:06:00.0: PCI INT A disabled [    0.754716] PCI: CLS 64 bytes, default 64 [    0.754717] PCI-DMA: Using software bounce buffering for IO (SWIOTLB) [    0.754719] Placing 64MB software IO TLB between ffff8800d9c0f000 - ffff8800ddc0f000 [    0.754720] software IO TLB at phys 0xd9c0f000 - 0xddc0f000 [    0.754992] audit: initializing netlink socket (disabled) [    0.754997] type=2000 audit(1348759251.536:1): initialized [    0.770742] HugeTLB registered 2 MB page size, pre-allocated 0 pages [    0.771870] VFS: Disk quotas dquot_6.5.2 [    0.771897] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) [    0.772143] fuse init (API version 7.17) [    0.772189] msgmni has been set to 11799 [    0.772370] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) [    0.772385] io scheduler noop registered [    0.772386] io scheduler deadline registered [    0.772402] io scheduler cfq registered (default) [    0.772452] pcieport 0000:00:01.0: setting latency timer to 64 [    0.772469] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X [    0.772647] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 [    0.772659] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 [    0.772686] intel_idle: MWAIT substates: 0x1120 [    0.772687] intel_idle: does not run on family 6 model 58 [    0.772736] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0 [    0.772740] ACPI: Power Button [PWRB] [    0.772764] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1 [    0.772766] ACPI: Power Button [PWRF] [    0.772813] ACPI: Fan [FAN0] (off) [    0.772830] ACPI: Fan [FAN1] (off) [    0.772846] ACPI: Fan [FAN2] (off) [    0.772862] ACPI: Fan [FAN3] (off) [    0.772878] ACPI: Fan [FAN4] (off) [    0.779978] Freeing initrd memory: 19976k freed [    0.838789] Monitor-Mwait will be used to enter C-1 state [    0.838809] Monitor-Mwait will be used to enter C-2 state [    0.838826] Monitor-Mwait will be used to enter C-3 state [    0.838837] ACPI: acpi_idle registered with cpuidle [    0.858721] thermal LNXTHERM:00: registered as thermal_zone0 [    0.858722] ACPI: Thermal Zone [TZ00] (28 C) [    0.858820] thermal LNXTHERM:01: registered as thermal_zone1 [    0.858821] ACPI: Thermal Zone [TZ01] (30 C) [    0.858843] ERST: Table is not found! [    0.858844] GHES: HEST is not enabled! [    0.858884] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled [    0.879257] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A [    1.010886] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A [    1.046538] Linux agpgart interface v0.103 [    1.047279] brd: module loaded [    1.047653] loop: module loaded [    1.047717] ahci 0000:00:1f.2: version 3.0 [    1.047724] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 [    1.047756] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X [    1.062356] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x24 impl SATA mode [    1.062361] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst  [    1.062366] ahci 0000:00:1f.2: setting latency timer to 64 [    1.070612] scsi0 : ahci [    1.070656] scsi1 : ahci [    1.070692] scsi2 : ahci [    1.070728] scsi3 : ahci [    1.070762] scsi4 : ahci [    1.070796] scsi5 : ahci [    1.070938] ata1: DUMMY [    1.070939] ata2: DUMMY [    1.070941] ata3: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216200 irq 41 [    1.070942] ata4: DUMMY [    1.070942] ata5: DUMMY [    1.070944] ata6: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216380 irq 41 [    1.071119] Fixed MDIO Bus: probed [    1.071128] tun: Universal TUN/TAP device driver, 1.6 [    1.071129] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> [    1.071153] PPP generic driver version 2.4.2 [    1.071201] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver [    1.071211] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 [    1.071221] ehci_hcd 0000:00:1a.0: setting latency timer to 64 [    1.071223] ehci_hcd 0000:00:1a.0: EHCI Host Controller [    1.071247] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1 [    1.071266] ehci_hcd 0000:00:1a.0: debug port 2 [    1.075149] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported [    1.075160] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xf7218000 [    1.090318] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00 [    1.090423] hub 1-0:1.0: USB hub found [    1.090425] hub 1-0:1.0: 2 ports detected [    1.090458] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 [    1.090468] ehci_hcd 0000:00:1d.0: setting latency timer to 64 [    1.090470] ehci_hcd 0000:00:1d.0: EHCI Host Controller [    1.090494] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 [    1.090510] ehci_hcd 0000:00:1d.0: debug port 2 [    1.094388] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported [    1.094390] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7217000 [    1.106301] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00 [    1.106399] hub 2-0:1.0: USB hub found [    1.106400] hub 2-0:1.0: 2 ports detected [    1.106433] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver [    1.106439] uhci_hcd: USB Universal Host Controller Interface driver [    1.106454] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    1.106472] xhci_hcd 0000:00:14.0: setting latency timer to 64 [    1.106474] xhci_hcd 0000:00:14.0: xHCI Host Controller [    1.106499] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3 [    1.106568] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported [    1.106577] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf7200000 [    1.106616] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X [    1.106684] xHCI xhci_add_endpoint called for root hub [    1.106685] xHCI xhci_check_bandwidth called for root hub [    1.106699] hub 3-0:1.0: USB hub found [    1.106704] hub 3-0:1.0: 4 ports detected [    1.106739] xhci_hcd 0000:00:14.0: xHCI Host Controller [    1.106760] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4 [    1.106805] xHCI xhci_add_endpoint called for root hub [    1.106806] xHCI xhci_check_bandwidth called for root hub [    1.106818] hub 4-0:1.0: USB hub found [    1.106823] hub 4-0:1.0: 4 ports detected [    1.158262] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 [    1.158291] xhci_hcd 0000:06:00.0: setting latency timer to 64 [    1.158295] xhci_hcd 0000:06:00.0: xHCI Host Controller [    1.158342] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 5 [    1.219440] xhci_hcd 0000:06:00.0: irq 19, io mem 0xf7100000 [    1.219491] xhci_hcd 0000:06:00.0: irq 43 for MSI/MSI-X [    1.219494] xhci_hcd 0000:06:00.0: irq 44 for MSI/MSI-X [    1.219497] xhci_hcd 0000:06:00.0: irq 45 for MSI/MSI-X [    1.219499] xhci_hcd 0000:06:00.0: irq 46 for MSI/MSI-X [    1.219501] xhci_hcd 0000:06:00.0: irq 47 for MSI/MSI-X [    1.219615] xHCI xhci_add_endpoint called for root hub [    1.219616] xHCI xhci_check_bandwidth called for root hub [    1.219631] hub 5-0:1.0: USB hub found [    1.219636] hub 5-0:1.0: 2 ports detected [    1.219670] xhci_hcd 0000:06:00.0: xHCI Host Controller [    1.219692] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 6 [    1.219748] xHCI xhci_add_endpoint called for root hub [    1.219749] xHCI xhci_check_bandwidth called for root hub [    1.219763] hub 6-0:1.0: USB hub found [    1.219769] hub 6-0:1.0: 2 ports detected [    1.254232] usbcore: registered new interface driver libusual [    1.254253] i8042: PNP: No PS/2 controller found. Probing ports directly. [    1.256519] serio: i8042 KBD port at 0x60,0x64 irq 1 [    1.256522] serio: i8042 AUX port at 0x60,0x64 irq 12 [    1.256590] mousedev: PS/2 mouse device common for all mice [    1.256665] rtc_cmos 00:06: RTC can wake from S4 [    1.256747] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 [    1.256770] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs [    1.256809] device-mapper: uevent: version 1.0.3 [    1.256846] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com [    1.256897] cpuidle: using governor ladder [    1.256972] cpuidle: using governor menu [    1.256973] EFI Variables Facility v0.08 2004-May-17 [    1.257079] TCP cubic registered [    1.257132] NET: Registered protocol family 10 [    1.257353] NET: Registered protocol family 17 [    1.257355] Registering the dns_resolver key type [    1.257480] PM: Hibernation image not present or could not be loaded. [    1.257488] registered taskstats version 1 [    1.262398]   Magic number: 12:908:336 [    1.262410] tty tty57: hash matches [    1.262493] rtc_cmos 00:06: setting system clock to 2012-09-27 15:20:52 UTC (1348759252) [    1.262993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found [    1.262994] EDD information not available. [    1.390050] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) [    1.390075] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) [    1.390990] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359) [    1.390999] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff88019405eed8), AE_NOT_FOUND (20110623/psparse-536) [    1.391213] ata3.00: ATA-8: WDC WD5000AADS-00S9B0, 01.00A01, max UDMA/133 [    1.391218] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA [    1.392244] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359) [    1.392253] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff88019405eed8), AE_NOT_FOUND (20110623/psparse-536) [    1.392546] ata3.00: configured for UDMA/133 [    1.392766] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AADS-0 01.0 PQ: 0 ANSI: 5 [    1.392855] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359) [    1.392859] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff880194072050), AE_NOT_FOUND (20110623/psparse-536) [    1.392874] ata6.00: ATAPI: HL-DT-ST BD-RE  WH12LS30, 1.00, max UDMA/133 [    1.392905] sd 2:0:0:0: Attached scsi generic sg0 type 0 [    1.392940] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB) [    1.393122] sd 2:0:0:0: [sda] Write Protect is off [    1.393124] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 [    1.393220] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA [    1.396986] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359) [    1.396994] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff880194072050), AE_NOT_FOUND (20110623/psparse-536) [    1.397009] ata6.00: configured for UDMA/133 [    1.402669] scsi 5:0:0:0: CD-ROM            HL-DT-ST BD-RE  WH12LS30  1.00 PQ: 0 ANSI: 5 [    1.406809] sr0: scsi3-mmc drive: 94x/94x writer dvd-ram cd/rw xa/form2 cdda tray [    1.406813] cdrom: Uniform CD-ROM driver Revision: 3.20 [    1.406971] sr 5:0:0:0: Attached scsi CD-ROM sr0 [    1.407055] sr 5:0:0:0: Attached scsi generic sg1 type 5 [    1.430003] usb 1-1: new high-speed USB device number 2 using ehci_hcd [    1.434099]  sda: sda1 sda2 < sda5 > [    1.434923] sd 2:0:0:0: [sda] Attached SCSI disk [    1.435859] Freeing unused kernel memory: 920k freed [    1.435926] Write protecting the kernel read-only data: 12288k [    1.438837] Freeing unused kernel memory: 1616k freed [    1.441009] Freeing unused kernel memory: 1200k freed [    1.451286] udevd[118]: starting version 175 [    1.461847] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded [    1.461863] r8169 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    1.461897] r8169 0000:03:00.0: setting latency timer to 64 [    1.463369] r8169 0000:03:00.0: irq 48 for MSI/MSI-X [    1.463598] r8169 0000:03:00.0: eth0: RTL8168f/8111f at 0xffffc90000c7a000, 30:85:a9:8e:8b:ba, XID 08000800 IRQ 48 [    1.463600] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko] [    1.562558] hub 1-1:1.0: USB hub found [    1.562632] hub 1-1:1.0: 6 ports detected [    1.673780] usb 2-1: new high-speed USB device number 2 using ehci_hcd [    1.753685] Refined TSC clocksource calibration: 3410.013 MHz. [    1.753691] Switching to clocksource tsc [    1.806309] hub 2-1:1.0: USB hub found [    1.806391] hub 2-1:1.0: 8 ports detected [    1.973476] usb 3-1: new high-speed USB device number 2 using xhci_hcd [    2.001181] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes [    2.001183] usb 3-1: ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes [    2.007026] Initializing USB Mass Storage driver... [    2.007035] usbcore: registered new interface driver uas [    2.007078] scsi6 : usb-storage 3-1:1.0 [    2.007121] usbcore: registered new interface driver usb-storage [    2.007122] USB Mass Storage support registered. [    2.117333] usb 3-2: new low-speed USB device number 3 using xhci_hcd [    2.171042] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes [    2.337120] usb 5-2: new high-speed USB device number 2 using xhci_hcd [    2.359346] hub 5-2:1.0: USB hub found [    2.359619] hub 5-2:1.0: 4 ports detected [    2.405258] generic-usb 0003:051D:0002.0001: hiddev0,hidraw0: USB HID v1.10 Device [APC Back-UPS ES 550 FW:843.K2 .D USB FW:K2 ] on usb-0000:00:14.0-2/input0 [    2.405277] usbcore: registered new interface driver usbhid [    2.405278] usbhid: USB HID core driver [    2.433170] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd [    2.601005] usb 2-1.6: new full-speed USB device number 4 using ehci_hcd [    2.768935] usb 5-2.1: new high-speed USB device number 3 using xhci_hcd [    2.826038] vesafb: mode is 1280x1024x32, linelength=5120, pages=0 [    2.826040] vesafb: scrolling: redraw [    2.826041] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0 [    2.828577] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90005800000, using 5120k, total 5120k [    2.828708] Console: switching to colour frame buffer device 160x64 [    2.828722] fb0: VESA VGA frame buffer device [    2.860837] usb 5-2.2: new high-speed USB device number 4 using xhci_hcd [    2.877220] usb 5-2.2: ep 0x83 - rounding interval to 32768 microframes, ep desc says 0 microframes [    3.007388] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent        102C PQ: 0 ANSI: 4 [    3.007635] sd 6:0:0:0: Attached scsi generic sg2 type 0 [    3.009411] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB) [    3.010573] sd 6:0:0:0: [sdb] Write Protect is off [    3.010578] sd 6:0:0:0: [sdb] Mode Sense: 1c 00 00 00 [    3.011820] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA [    3.016407]  sdb: sdb1 [    3.026429] sd 6:0:0:0: [sdb] Attached SCSI disk [    3.141302] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null) [   13.419024] ADDRCONF(NETDEV_UP): eth0: link is not ready [   13.580950] udevd[383]: starting version 175 [   13.981310] Adding 5974012k swap on /dev/sda5.  Priority:-1 extents:1 across:5974012k  [   16.106464] lp: driver loaded but no devices found [   16.355786] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro [   16.500582] wmi: Mapper loaded [   16.540873] mei: module is from the staging directory, the quality is unknown, you have been warned. [   16.541081] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 [   16.541085] mei 0000:00:16.0: setting latency timer to 64 [   16.541135] mei 0000:00:16.0: irq 49 for MSI/MSI-X [   16.580502] asus_wmi: ASUS WMI generic driver loaded [   16.632013] asus_wmi: Initialization: 0x0 [   16.632027] asus_wmi: BIOS WMI version: 0.9 [   16.632049] asus_wmi: SFUN value: 0x0 [   16.632195] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input2 [   17.474672] nvidia: module license 'NVIDIA' taints kernel. [   17.474676] Disabling lock debugging due to kernel taint [   17.509303] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [   17.509309] nvidia 0000:01:00.0: setting latency timer to 64 [   17.509312] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem [   17.509367] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012 [   17.778857] Bluetooth: Core ver 2.16 [   17.778868] NET: Registered protocol family 31 [   17.778869] Bluetooth: HCI device and connection manager initialized [   17.778870] Bluetooth: HCI socket layer initialized [   17.778871] Bluetooth: L2CAP socket layer initialized [   17.778873] Bluetooth: SCO socket layer initialized [   17.797317] Bluetooth: Generic Bluetooth USB driver ver 0.6 [   17.797424] usbcore: registered new interface driver btusb [   17.873118] logitech-djreceiver 0003:046D:C52B.0004: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.6/input2 [   17.876021] input: Logitech Unifying Device. Wireless PID:1025 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0004/input/input3 [   17.876091] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1025] on usb-0000:00:1d.0-1.6:1 [   17.878069] input: Logitech Unifying Device. Wireless PID:200a as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0004/input/input4 [   17.878114] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:200a] on usb-0000:00:1d.0-1.6:2 [   17.988553] Linux video capture interface: v2.00 [   17.997862] uvcvideo: Found UVC 1.00 device USB 2.0 CAMERA (1c4f:3002) [   17.998907] input: USB 2.0 CAMERA as /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2/5-2.1/5-2.1:1.0/input/input5 [   17.998945] usbcore: registered new interface driver uvcvideo [   17.998946] USB Video Class driver (1.1.1) [   18.034004] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 [   18.034051] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X [   18.034077] snd_hda_intel 0000:00:1b.0: setting latency timer to 64 [   18.064385] usbcore: registered new interface driver snd-usb-audio [   18.194496] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6 [   18.194562] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7 [   18.194598] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8 [   18.194631] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9 [   18.194661] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 [   18.194693] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11 [   18.194723] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12 [   18.194761] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13 [   18.194900] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 [   18.194902] hda_intel: Disabling MSI [   18.194934] snd_hda_intel 0000:01:00.1: setting latency timer to 64 [   18.908987] HDMI status: Codec=0 Pin=4 Presence_Detect=0 ELD_Valid=0 [   18.916969] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0 [   18.917064] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input14 [   18.917189] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input15 [   19.787412] type=1400 audit(1348759271.038:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=980 comm="apparmor_parser" [   19.787460] type=1400 audit(1348759271.038:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=979 comm="apparmor_parser" [   19.787471] type=1400 audit(1348759271.038:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1050 comm="apparmor_parser" [   19.787622] type=1400 audit(1348759271.038:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser" [   19.787670] type=1400 audit(1348759271.038:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser" [   19.787682] type=1400 audit(1348759271.038:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1050 comm="apparmor_parser" [   19.787740] type=1400 audit(1348759271.038:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser" [   19.787789] type=1400 audit(1348759271.038:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser" [   19.787802] type=1400 audit(1348759271.038:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1050 comm="apparmor_parser" [   20.032224] init: failsafe main process (1076) killed by TERM signal [   20.570971] type=1400 audit(1348759271.822:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1153 comm="apparmor_parser" [   20.846798] ppdev: user-space parallel port driver [   21.136820] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 [   21.136822] Bluetooth: BNEP filters: protocol multicast [   21.347729] Bluetooth: RFCOMM TTY layer initialized [   21.347732] Bluetooth: RFCOMM socket layer initialized [   21.347733] Bluetooth: RFCOMM ver 1.11 [   22.918258] r8169 0000:03:00.0: eth0: link down [   22.918263] r8169 0000:03:00.0: eth0: link down [   22.918627] ADDRCONF(NETDEV_UP): eth0: link is not ready [   22.918781] ADDRCONF(NETDEV_UP): eth0: link is not ready [   23.650689] kvm: disabled by bios [   23.717361] init: qemu-kvm pre-start process (1233) terminated with status 1 [   23.868069] vboxdrv: Found 4 processor cores. [   23.868146] vboxdrv: fAsync=0 offMin=0x1f4 offMax=0x29f5 [   23.868184] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'. [   23.868185] vboxdrv: Successfully loaded version 4.2.0 (interface 0x001a0004). [   24.218068] vboxpci: IOMMU not found (not registered) [   24.557075] r8169 0000:03:00.0: eth0: link up [   24.702103] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready [   25.653735] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0 [   25.658389] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0 [   25.672495] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=1 [   25.678369] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1 [   26.445659] HDMI: detected monitor H233H [   26.445661]         at connection type HDMI [   26.445664] HDMI: available speakers: FL/FR [   26.445669] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24 [   35.253288] eth0: no IPv6 routers present [   98.698463] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -32 (exp. 1). [   98.699397] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -32 (exp. 2). [   98.699807] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -32 (exp. 2). [   98.700686] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -32 (exp. 2). [  101.711838] UDF-fs: Partition marked readonly; forcing readonly mount [  101.766345] UDF-fs: INFO Mounting volume 'RICHARD_JENI_A_BIG_STEAMING', timestamp 2005/04/13 17:53 (1f10) [  374.863281] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0 [  374.868605] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0 [  375.911550] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0 [  375.916141] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0 [  375.930904] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=1 [  375.936090] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1 [  376.727754] HDMI: detected monitor H233H [  376.727756]         at connection type HDMI [  376.727759] HDMI: available speakers: FL/FR [  376.727763] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24 [  421.927329] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -32 (exp. 1). [  421.927658] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -32 (exp. 2). [  421.927981] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -32 (exp. 2). [  421.928314] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -32 (exp. 2). [  918.075802] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)  

```

---

### Post by Rexilion on 2012-09-28
Could you post it @ [www.pastebin.com](www.pastebin.com), the one-line dmesg is kinda hard to read :lolflag:

---

### Post by netopalis45 on 2012-09-28
Not sure why that happened and don't have a pastbin account so I'm going to try this again

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic 3.2.28)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=4cd0557b-8f88-403a-a559-f8135e4acb9e ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000ddc0f000 (usable)
[    0.000000]  BIOS-e820: 00000000ddc0f000 - 00000000ddfd9000 (reserved)
[    0.000000]  BIOS-e820: 00000000ddfd9000 - 00000000ddfdb000 (usable)
[    0.000000]  BIOS-e820: 00000000ddfdb000 - 00000000de5e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000de5e0000 - 00000000de834000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000de834000 - 00000000de841000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000de841000 - 00000000de860000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000de860000 - 00000000de865000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000de865000 - 00000000de8a8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000de8a8000 - 00000000decb8000 (usable)
[    0.000000]  BIOS-e820: 00000000decb8000 - 00000000deff4000 (reserved)
[    0.000000]  BIOS-e820: 00000000deff4000 - 00000000df000000 (usable)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000019f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: System manufacturer System Product Name/P8Z77-V LK, BIOS 0404 05/23/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x19f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask F80000000 write-back
[    0.000000]   2 base 180000000 mask FF0000000 write-back
[    0.000000]   3 base 190000000 mask FF8000000 write-back
[    0.000000]   4 base 198000000 mask FFC000000 write-back
[    0.000000]   5 base 19C000000 mask FFE000000 write-back
[    0.000000]   6 base 19E000000 mask FFF000000 write-back
[    0.000000]   7 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 2GB, type WB
[    0.000000] reg 2, base: 6GB, range: 256MB, type WB
[    0.000000] reg 3, base: 6400MB, range: 128MB, type WB
[    0.000000] reg 4, base: 6528MB, range: 64MB, type WB
[    0.000000] reg 5, base: 6592MB, range: 32MB, type WB
[    0.000000] reg 6, base: 6624MB, range: 16MB, type WB
[    0.000000] reg 7, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 6128M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 32M         num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 2GB, type WB
[    0.000000] reg 4, base: 6GB, range: 512MB, type WB
[    0.000000] reg 5, base: 6640MB, range: 16MB, type UC
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcd00] fcd00
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000df000000
[    0.000000]  0000000000 - 00df000000 page 2M
[    0.000000] kernel direct mapping tables up to df000000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000019f000000
[    0.000000]  0100000000 - 019f000000 page 2M
[    0.000000] kernel direct mapping tables up to 19f000000 @ deff8000-df000000
[    0.000000] RAMDISK: 358ec000 - 36c6e000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000de834070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000de83e9a8 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000de834168 0A83E (v02 ALASKA    A M I 00000015 INTL 20051117)
[    0.000000] ACPI: FACS 00000000de85ef80 00040
[    0.000000] ACPI: APIC 00000000de83eaa0 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000de83eb18 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000de83eb58 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000de83eb90 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000de83ef00 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000de83f8b0 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 00000000de840348 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000019f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000019f000000
[    0.000000]   NODE_DATA [000000019effb000 - 000000019effffff]
[    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880198600000-ffff88019e5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0019f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000ddc0f
[    0.000000]     0: 0x000ddfd9 -> 0x000ddfdb
[    0.000000]     0: 0x000de8a8 -> 0x000decb8
[    0.000000]     0: 0x000deff4 -> 0x000df000
[    0.000000]     0: 0x00100000 -> 0x0019f000
[    0.000000] On node 0 totalpages: 1560506
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 888941 pages, LIFO batch:31
[    0.000000]   Normal zone: 10176 pages used for memmap
[    0.000000]   Normal zone: 641088 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000ddc0f000 - 00000000ddfd9000
[    0.000000] PM: Registered nosave memory: 00000000ddfdb000 - 00000000de5e0000
[    0.000000] PM: Registered nosave memory: 00000000de5e0000 - 00000000de834000
[    0.000000] PM: Registered nosave memory: 00000000de834000 - 00000000de841000
[    0.000000] PM: Registered nosave memory: 00000000de841000 - 00000000de860000
[    0.000000] PM: Registered nosave memory: 00000000de860000 - 00000000de865000
[    0.000000] PM: Registered nosave memory: 00000000de865000 - 00000000de8a8000
[    0.000000] PM: Registered nosave memory: 00000000decb8000 - 00000000deff4000
[    0.000000] PM: Registered nosave memory: 00000000df000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at df000000 (gap: df000000:19000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019ec00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1533941
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=4cd0557b-8f88-403a-a559-f8135e4acb9e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 6041400k/6799360k available (6558k kernel code, 557336k absent, 200624k reserved, 6642k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 50331648 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3410.097 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6820.19 BogoMIPS (lpj=13640388)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000019] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000028] Yama: becoming mindful.
[    0.000389] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001811] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002434] Mount-cache hash table entries: 256
[    0.002501] Initializing cgroup subsys cpuacct
[    0.002503] Initializing cgroup subsys memory
[    0.002508] Initializing cgroup subsys devices
[    0.002509] Initializing cgroup subsys freezer
[    0.002511] Initializing cgroup subsys blkio
[    0.002514] Initializing cgroup subsys perf_event
[    0.002532] CPU: Physical Processor ID: 0
[    0.002532] CPU: Processor Core ID: 0
[    0.002536] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002537] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002795] mce: CPU supports 9 MCE banks
[    0.002805] CPU0: Thermal monitoring enabled (TM1)
[    0.002810] using mwait in idle threads.
[    0.004229] ACPI: Core revision 20110623
[    0.073824] ftrace: allocating 27008 entries in 106 pages
[    0.080254] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.119900] CPU0: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz stepping 09
[    0.224577] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.224581] ... version:                3
[    0.224582] ... bit width:              48
[    0.224582] ... generic registers:      8
[    0.224583] ... value mask:             0000ffffffffffff
[    0.224584] ... max period:             000000007fffffff
[    0.224585] ... fixed-purpose events:   3
[    0.224585] ... event mask:             00000007000000ff
[    0.224664] NMI watchdog enabled, takes one hw-pmu counter.
[    0.224714] Booting Node   0, Processors  #1
[    0.224715] smpboot cpu 1: start_ip = 98000
[    0.332832] NMI watchdog enabled, takes one hw-pmu counter.
[    0.332890]  #2
[    0.332891] smpboot cpu 2: start_ip = 98000
[    0.440705] NMI watchdog enabled, takes one hw-pmu counter.
[    0.440759]  #3 Ok.
[    0.440760] smpboot cpu 3: start_ip = 98000
[    0.548674] NMI watchdog enabled, takes one hw-pmu counter.
[    0.548696] Brought up 4 CPUs
[    0.548698] Total of 4 processors activated (27279.89 BogoMIPS).
[    0.551322] devtmpfs: initialized
[    0.551807] EVM: security.selinux
[    0.551808] EVM: security.SMACK64
[    0.551809] EVM: security.capability
[    0.551823] PM: Registering ACPI NVS region at de5e0000 (2441216 bytes)
[    0.551845] PM: Registering ACPI NVS region at de841000 (126976 bytes)
[    0.551847] PM: Registering ACPI NVS region at de865000 (274432 bytes)
[    0.552338] print_constraints: dummy: 
[    0.552364] RTC time: 15:20:51, date: 09/27/12
[    0.552382] NET: Registered protocol family 16
[    0.552440] Trying to unpack rootfs image as initramfs...
[    0.552444] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.552445] ACPI: bus type pci registered
[    0.552482] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.552483] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.562620] PCI: Using configuration type 1 for base access
[    0.563115] bio: create slab <bio-0> at 0
[    0.563157] ACPI: Added _OSI(Module Device)
[    0.563158] ACPI: Added _OSI(Processor Device)
[    0.563159] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.563160] ACPI: Added _OSI(Processor Aggregator Device)
[    0.564094] ACPI: EC: Look up EC in DSDT
[    0.565157] ACPI: Executed 1 blocks of module-level executable AML code
[    0.596472] ACPI: SSDT 00000000de58d018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.596707] ACPI: Dynamic OEM Table Load:
[    0.596709] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.620324] ACPI: SSDT 00000000de58ea98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.620575] ACPI: Dynamic OEM Table Load:
[    0.620577] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.644222] ACPI: SSDT 00000000de58fc18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.644453] ACPI: Dynamic OEM Table Load:
[    0.644455] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.668501] ACPI: Interpreter enabled
[    0.668504] ACPI: (supports S0 S1 S3 S4 S5)
[    0.668519] ACPI: Using IOAPIC for interrupt routing
[    0.671657] ACPI: Power Resource [FN00] (off)
[    0.671704] ACPI: Power Resource [FN01] (off)
[    0.671746] ACPI: Power Resource [FN02] (off)
[    0.671789] ACPI: Power Resource [FN03] (off)
[    0.671831] ACPI: Power Resource [FN04] (off)
[    0.672119] ACPI: No dock devices found.
[    0.672120] HEST: Table not found.
[    0.672122] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.672315] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.672587] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.672588] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.672590] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.672591] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.672592] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.672594] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.672595] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.672596] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.672597] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.672599] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfeafffff]
[    0.672607] pci 0000:00:00.0: [8086:0150] type 0 class 0x000600
[    0.672633] pci 0000:00:01.0: [8086:0151] type 1 class 0x000604
[    0.672654] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.672656] pci 0000:00:01.0: PME# disabled
[    0.672692] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
[    0.672712] pci 0000:00:14.0: reg 10: [mem 0xf7200000-0xf720ffff 64bit]
[    0.672777] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.672780] pci 0000:00:14.0: PME# disabled
[    0.672797] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
[    0.672818] pci 0000:00:16.0: reg 10: [mem 0xf721a000-0xf721a00f 64bit]
[    0.672885] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.672887] pci 0000:00:16.0: PME# disabled
[    0.672914] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
[    0.672933] pci 0000:00:1a.0: reg 10: [mem 0xf7218000-0xf72183ff]
[    0.673016] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.673019] pci 0000:00:1a.0: PME# disabled
[    0.673039] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
[    0.673052] pci 0000:00:1b.0: reg 10: [mem 0xf7210000-0xf7213fff 64bit]
[    0.673113] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.673115] pci 0000:00:1b.0: PME# disabled
[    0.673138] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
[    0.673264] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.673268] pci 0000:00:1c.0: PME# disabled
[    0.673297] pci 0000:00:1c.4: [8086:1e18] type 1 class 0x000604
[    0.673369] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.673372] pci 0000:00:1c.4: PME# disabled
[    0.673391] pci 0000:00:1c.5: [8086:244e] type 1 class 0x000604
[    0.673463] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.673466] pci 0000:00:1c.5: PME# disabled
[    0.673486] pci 0000:00:1c.7: [8086:1e1e] type 1 class 0x000604
[    0.673558] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.673561] pci 0000:00:1c.7: PME# disabled
[    0.673585] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
[    0.673604] pci 0000:00:1d.0: reg 10: [mem 0xf7217000-0xf72173ff]
[    0.673686] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.673690] pci 0000:00:1d.0: PME# disabled
[    0.673709] pci 0000:00:1f.0: [8086:1e44] type 0 class 0x000601
[    0.673823] pci 0000:00:1f.2: [8086:1e02] type 0 class 0x000106
[    0.673839] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.673845] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.673852] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.673858] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.673865] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.673871] pci 0000:00:1f.2: reg 24: [mem 0xf7216000-0xf72167ff]
[    0.673911] pci 0000:00:1f.2: PME# supported from D3hot
[    0.673913] pci 0000:00:1f.2: PME# disabled
[    0.673926] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05
[    0.673939] pci 0000:00:1f.3: reg 10: [mem 0xf7215000-0xf72150ff 64bit]
[    0.673958] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.674002] pci 0000:01:00.0: [10de:104a] type 0 class 0x000300
[    0.674008] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.674016] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
[    0.674023] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.674028] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.674033] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
[    0.674072] pci 0000:01:00.1: [10de:0e08] type 0 class 0x000403
[    0.674078] pci 0000:01:00.1: reg 10: [mem 0xf7080000-0xf7083fff]
[    0.680133] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.680135] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.680137] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.680140] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.680208] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.680280] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.680299] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff]
[    0.680331] pci 0000:03:00.0: reg 18: [mem 0xf2104000-0xf2104fff 64bit pref]
[    0.680351] pci 0000:03:00.0: reg 20: [mem 0xf2100000-0xf2103fff 64bit pref]
[    0.680439] pci 0000:03:00.0: supports D1 D2
[    0.680440] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.680444] pci 0000:03:00.0: PME# disabled
[    0.688129] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.688132] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.688139] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.688192] pci 0000:04:00.0: [1b21:1080] type 1 class 0x000604
[    0.688307] pci 0000:00:1c.5: PCI bridge to [bus 04-05] (subtractive decode)
[    0.688317] pci 0000:00:1c.5:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.688318] pci 0000:00:1c.5:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.688319] pci 0000:00:1c.5:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.688321] pci 0000:00:1c.5:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.688322] pci 0000:00:1c.5:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.688323] pci 0000:00:1c.5:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.688324] pci 0000:00:1c.5:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.688326] pci 0000:00:1c.5:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.688327] pci 0000:00:1c.5:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.688328] pci 0000:00:1c.5:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.688438] pci 0000:04:00.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.688458] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.688460] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.688461] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.688462] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.688463] pci 0000:04:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.688465] pci 0000:04:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.688466] pci 0000:04:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.688467] pci 0000:04:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.688469] pci 0000:04:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.688470] pci 0000:04:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.688471] pci 0000:04:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.688472] pci 0000:04:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.688474] pci 0000:04:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.688475] pci 0000:04:00.0:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.688551] pci 0000:06:00.0: [1b21:1042] type 0 class 0x000c03
[    0.688578] pci 0000:06:00.0: reg 10: [mem 0xf7100000-0xf7107fff 64bit]
[    0.688719] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.688724] pci 0000:06:00.0: PME# disabled
[    0.696120] pci 0000:00:1c.7: PCI bridge to [bus 06-06]
[    0.696125] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.696152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.696220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.696243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.696263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.696282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06.P9PE._PRT]
[    0.696305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.696327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    0.696403]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.696517]  pci0000:00: ACPI _OSC control (0x18) granted
[    0.698685] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.698714] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.698741] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 10 11 12 14 15)
[    0.698767] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.698793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.698822] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 *15)
[    0.698848] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 *14 15)
[    0.698873] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.698940] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.698942] vgaarb: loaded
[    0.698943] vgaarb: bridge control possible 0000:01:00.0
[    0.698994] i2c-core: driver [aat2870] using legacy suspend method
[    0.698995] i2c-core: driver [aat2870] using legacy resume method
[    0.699029] SCSI subsystem initialized
[    0.699057] libata version 3.00 loaded.
[    0.699082] usbcore: registered new interface driver usbfs
[    0.699088] usbcore: registered new interface driver hub
[    0.699099] usbcore: registered new device driver usb
[    0.699141] PCI: Using ACPI for IRQ routing
[    0.700494] PCI: pci_cache_line_size set to 64 bytes
[    0.700549] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.700551] reserve RAM buffer: 00000000ddc0f000 - 00000000dfffffff 
[    0.700552] reserve RAM buffer: 00000000ddfdb000 - 00000000dfffffff 
[    0.700554] reserve RAM buffer: 00000000decb8000 - 00000000dfffffff 
[    0.700555] reserve RAM buffer: 00000000df000000 - 00000000dfffffff 
[    0.700556] reserve RAM buffer: 000000019f000000 - 000000019fffffff 
[    0.700610] NetLabel: Initializing
[    0.700611] NetLabel:  domain hash size = 128
[    0.700612] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.700618] NetLabel:  unlabeled traffic allowed by default
[    0.700647] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.700650] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.702659] Switching to clocksource hpet
[    0.706096] AppArmor: AppArmor Filesystem Enabled
[    0.706106] pnp: PnP ACPI init
[    0.706114] ACPI: bus type pnp registered
[    0.706270] pnp 00:00: [bus 00-3e]
[    0.706272] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.706273] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.706274] pnp 00:00: [io  0x0d00-0xffff window]
[    0.706275] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.706276] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.706278] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.706279] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.706280] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.706281] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.706282] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.706284] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.706285] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.706286] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.706287] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.706288] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.706289] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.706291] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.706292] pnp 00:00: [mem 0xe0000000-0xfeafffff window]
[    0.706293] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    0.706329] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.706345] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.706368] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.706370] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.706378] pnp 00:02: [io  0x0000-0x001f]
[    0.706379] pnp 00:02: [io  0x0081-0x0091]
[    0.706380] pnp 00:02: [io  0x0093-0x009f]
[    0.706380] pnp 00:02: [io  0x00c0-0x00df]
[    0.706382] pnp 00:02: [dma 4]
[    0.706393] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.706397] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.706408] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.706452] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.706464] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.706470] pnp 00:05: [io  0x002e-0x002f]
[    0.706471] pnp 00:05: [io  0x004e-0x004f]
[    0.706472] pnp 00:05: [io  0x0061]
[    0.706473] pnp 00:05: [io  0x0063]
[    0.706474] pnp 00:05: [io  0x0065]
[    0.706475] pnp 00:05: [io  0x0067]
[    0.706476] pnp 00:05: [io  0x0070]
[    0.706476] pnp 00:05: [io  0x0080]
[    0.706477] pnp 00:05: [io  0x0092]
[    0.706478] pnp 00:05: [io  0x00b2-0x00b3]
[    0.706479] pnp 00:05: [io  0x0680-0x069f]
[    0.706480] pnp 00:05: [io  0x0200-0x020f]
[    0.706481] pnp 00:05: [io  0xffff]
[    0.706482] pnp 00:05: [io  0xffff]
[    0.706483] pnp 00:05: [io  0x0400-0x0453]
[    0.706484] pnp 00:05: [io  0x0458-0x047f]
[    0.706484] pnp 00:05: [io  0x0500-0x057f]
[    0.706485] pnp 00:05: [io  0x164e-0x164f]
[    0.706508] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.706509] system 00:05: [io  0x0200-0x020f] has been reserved
[    0.706510] system 00:05: [io  0xffff] has been reserved
[    0.706512] system 00:05: [io  0xffff] has been reserved
[    0.706514] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.706515] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.706516] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.706517] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.706519] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.706524] pnp 00:06: [io  0x0070-0x0077]
[    0.706531] pnp 00:06: [irq 8]
[    0.706542] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.706557] pnp 00:07: [io  0x0454-0x0457]
[    0.706576] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.706578] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.706611] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.706613] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.706614] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.706615] pnp 00:08: [io  0x0290-0x029f]
[    0.706616] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.706636] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.706638] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.706650] pnp 00:09: [io  0x0010-0x001f]
[    0.706651] pnp 00:09: [io  0x0022-0x003f]
[    0.706652] pnp 00:09: [io  0x0044-0x005f]
[    0.706653] pnp 00:09: [io  0x0062-0x0063]
[    0.706654] pnp 00:09: [io  0x0065-0x006f]
[    0.706655] pnp 00:09: [io  0x0072-0x007f]
[    0.706655] pnp 00:09: [io  0x0080]
[    0.706656] pnp 00:09: [io  0x0084-0x0086]
[    0.706657] pnp 00:09: [io  0x0088]
[    0.706658] pnp 00:09: [io  0x008c-0x008e]
[    0.706660] pnp 00:09: [io  0x0090-0x009f]
[    0.706661] pnp 00:09: [io  0x00a2-0x00bf]
[    0.706662] pnp 00:09: [io  0x00e0-0x00ef]
[    0.706663] pnp 00:09: [io  0x04d0-0x04d1]
[    0.706690] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.706692] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.706697] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.706701] pnp 00:0a: [irq 13]
[    0.706712] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.706848] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.706852] pnp 00:0b: [irq 4]
[    0.706853] pnp 00:0b: [dma 0 disabled]
[    0.706885] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.707001] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff]
[    0.707002] pnp 00:0c: [mem 0xfed10000-0xfed17fff]
[    0.707003] pnp 00:0c: [mem 0xfed18000-0xfed18fff]
[    0.707004] pnp 00:0c: [mem 0xfed19000-0xfed19fff]
[    0.707005] pnp 00:0c: [mem 0xf8000000-0xfbffffff]
[    0.707006] pnp 00:0c: [mem 0xfed20000-0xfed3ffff]
[    0.707007] pnp 00:0c: [mem 0xfed90000-0xfed93fff]
[    0.707008] pnp 00:0c: [mem 0xfed45000-0xfed8ffff]
[    0.707009] pnp 00:0c: [mem 0xff000000-0xffffffff]
[    0.707010] pnp 00:0c: [mem 0xfee00000-0xfeefffff]
[    0.707011] pnp 00:0c: [mem 0xe0000000-0xe0000fff]
[    0.707044] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.707046] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.707047] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.707048] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.707050] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.707051] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.707052] system 00:0c: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.707054] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.707055] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.707057] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.707058] system 00:0c: [mem 0xe0000000-0xe0000fff] has been reserved
[    0.707060] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.707135] pnp: PnP ACPI: found 13 devices
[    0.707136] ACPI: ACPI bus type pnp unregistered
[    0.712844] PCI: max bus depth: 2 pci_try_num: 3
[    0.712890] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.712892] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.712894] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.712896] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.712899] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.712914] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.712916] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.712922] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.712927] pci 0000:04:00.0: PCI bridge to [bus 05-05]
[    0.712945] pci 0000:00:1c.5: PCI bridge to [bus 04-05]
[    0.712955] pci 0000:00:1c.7: PCI bridge to [bus 06-06]
[    0.712958] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.712972] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712974] pci 0000:00:01.0: setting latency timer to 64
[    0.712979] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712983] pci 0000:00:1c.0: setting latency timer to 64
[    0.712987] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712990] pci 0000:00:1c.4: setting latency timer to 64
[    0.712996] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.712999] pci 0000:00:1c.5: setting latency timer to 64
[    0.713005] pci 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.713009] pci 0000:04:00.0: setting latency timer to 64
[    0.713018] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.713021] pci 0000:00:1c.7: setting latency timer to 64
[    0.713023] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.713025] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.713026] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.713027] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.713028] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.713029] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.713030] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.713032] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.713033] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.713034] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.713035] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.713036] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.713038] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.713039] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.713040] pci_bus 0000:03: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.713042] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.713043] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.713044] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.713045] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.713046] pci_bus 0000:04: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.713047] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.713049] pci_bus 0000:04: resource 10 [mem 0x000dc000-0x000dffff]
[    0.713050] pci_bus 0000:04: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.713051] pci_bus 0000:04: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.713052] pci_bus 0000:04: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.713054] pci_bus 0000:05: resource 8 [io  0x0000-0x0cf7]
[    0.713055] pci_bus 0000:05: resource 9 [io  0x0d00-0xffff]
[    0.713056] pci_bus 0000:05: resource 10 [mem 0x000a0000-0x000bffff]
[    0.713057] pci_bus 0000:05: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.713058] pci_bus 0000:05: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.713059] pci_bus 0000:05: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.713060] pci_bus 0000:05: resource 14 [mem 0x000dc000-0x000dffff]
[    0.713062] pci_bus 0000:05: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.713063] pci_bus 0000:05: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.713064] pci_bus 0000:05: resource 17 [mem 0xe0000000-0xfeafffff]
[    0.713065] pci_bus 0000:06: resource 1 [mem 0xf7100000-0xf71fffff]
[    0.713083] NET: Registered protocol family 2
[    0.713191] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.713671] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.714577] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.714704] TCP: Hash tables configured (established 524288 bind 65536)
[    0.714705] TCP reno registered
[    0.714715] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.714736] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.714793] NET: Registered protocol family 1
[    0.714806] pci 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.714854] pci 0000:00:14.0: PCI INT A disabled
[    0.714865] pci 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.734666] pci 0000:00:1a.0: PCI INT A disabled
[    0.734681] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.754646] pci 0000:00:1d.0: PCI INT A disabled
[    0.754661] pci 0000:01:00.0: Boot video device
[    0.754679] pci 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.754713] pci 0000:06:00.0: PCI INT A disabled
[    0.754716] PCI: CLS 64 bytes, default 64
[    0.754717] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.754719] Placing 64MB software IO TLB between ffff8800d9c0f000 - ffff8800ddc0f000
[    0.754720] software IO TLB at phys 0xd9c0f000 - 0xddc0f000
[    0.754992] audit: initializing netlink socket (disabled)
[    0.754997] type=2000 audit(1348759251.536:1): initialized
[    0.770742] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.771870] VFS: Disk quotas dquot_6.5.2
[    0.771897] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.772143] fuse init (API version 7.17)
[    0.772189] msgmni has been set to 11799
[    0.772370] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.772385] io scheduler noop registered
[    0.772386] io scheduler deadline registered
[    0.772402] io scheduler cfq registered (default)
[    0.772452] pcieport 0000:00:01.0: setting latency timer to 64
[    0.772469] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.772647] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.772659] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.772686] intel_idle: MWAIT substates: 0x1120
[    0.772687] intel_idle: does not run on family 6 model 58
[    0.772736] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.772740] ACPI: Power Button [PWRB]
[    0.772764] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.772766] ACPI: Power Button [PWRF]
[    0.772813] ACPI: Fan [FAN0] (off)
[    0.772830] ACPI: Fan [FAN1] (off)
[    0.772846] ACPI: Fan [FAN2] (off)
[    0.772862] ACPI: Fan [FAN3] (off)
[    0.772878] ACPI: Fan [FAN4] (off)
[    0.779978] Freeing initrd memory: 19976k freed
[    0.838789] Monitor-Mwait will be used to enter C-1 state
[    0.838809] Monitor-Mwait will be used to enter C-2 state
[    0.838826] Monitor-Mwait will be used to enter C-3 state
[    0.838837] ACPI: acpi_idle registered with cpuidle
[    0.858721] thermal LNXTHERM:00: registered as thermal_zone0
[    0.858722] ACPI: Thermal Zone [TZ00] (28 C)
[    0.858820] thermal LNXTHERM:01: registered as thermal_zone1
[    0.858821] ACPI: Thermal Zone [TZ01] (30 C)
[    0.858843] ERST: Table is not found!
[    0.858844] GHES: HEST is not enabled!
[    0.858884] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.879257] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.010886] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.046538] Linux agpgart interface v0.103
[    1.047279] brd: module loaded
[    1.047653] loop: module loaded
[    1.047717] ahci 0000:00:1f.2: version 3.0
[    1.047724] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.047756] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.062356] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x24 impl SATA mode
[    1.062361] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.062366] ahci 0000:00:1f.2: setting latency timer to 64
[    1.070612] scsi0 : ahci
[    1.070656] scsi1 : ahci
[    1.070692] scsi2 : ahci
[    1.070728] scsi3 : ahci
[    1.070762] scsi4 : ahci
[    1.070796] scsi5 : ahci
[    1.070938] ata1: DUMMY
[    1.070939] ata2: DUMMY
[    1.070941] ata3: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216200 irq 41
[    1.070942] ata4: DUMMY
[    1.070942] ata5: DUMMY
[    1.070944] ata6: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216380 irq 41
[    1.071119] Fixed MDIO Bus: probed
[    1.071128] tun: Universal TUN/TAP device driver, 1.6
[    1.071129] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.071153] PPP generic driver version 2.4.2
[    1.071201] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.071211] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.071221] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.071223] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.071247] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.071266] ehci_hcd 0000:00:1a.0: debug port 2
[    1.075149] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.075160] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xf7218000
[    1.090318] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.090423] hub 1-0:1.0: USB hub found
[    1.090425] hub 1-0:1.0: 2 ports detected
[    1.090458] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.090468] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.090470] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.090494] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.090510] ehci_hcd 0000:00:1d.0: debug port 2
[    1.094388] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.094390] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7217000
[    1.106301] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.106399] hub 2-0:1.0: USB hub found
[    1.106400] hub 2-0:1.0: 2 ports detected
[    1.106433] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.106439] uhci_hcd: USB Universal Host Controller Interface driver
[    1.106454] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.106472] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.106474] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.106499] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.106568] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.106577] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf7200000
[    1.106616] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    1.106684] xHCI xhci_add_endpoint called for root hub
[    1.106685] xHCI xhci_check_bandwidth called for root hub
[    1.106699] hub 3-0:1.0: USB hub found
[    1.106704] hub 3-0:1.0: 4 ports detected
[    1.106739] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.106760] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.106805] xHCI xhci_add_endpoint called for root hub
[    1.106806] xHCI xhci_check_bandwidth called for root hub
[    1.106818] hub 4-0:1.0: USB hub found
[    1.106823] hub 4-0:1.0: 4 ports detected
[    1.158262] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.158291] xhci_hcd 0000:06:00.0: setting latency timer to 64
[    1.158295] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.158342] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 5
[    1.219440] xhci_hcd 0000:06:00.0: irq 19, io mem 0xf7100000
[    1.219491] xhci_hcd 0000:06:00.0: irq 43 for MSI/MSI-X
[    1.219494] xhci_hcd 0000:06:00.0: irq 44 for MSI/MSI-X
[    1.219497] xhci_hcd 0000:06:00.0: irq 45 for MSI/MSI-X
[    1.219499] xhci_hcd 0000:06:00.0: irq 46 for MSI/MSI-X
[    1.219501] xhci_hcd 0000:06:00.0: irq 47 for MSI/MSI-X
[    1.219615] xHCI xhci_add_endpoint called for root hub
[    1.219616] xHCI xhci_check_bandwidth called for root hub
[    1.219631] hub 5-0:1.0: USB hub found
[    1.219636] hub 5-0:1.0: 2 ports detected
[    1.219670] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.219692] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 6
[    1.219748] xHCI xhci_add_endpoint called for root hub
[    1.219749] xHCI xhci_check_bandwidth called for root hub
[    1.219763] hub 6-0:1.0: USB hub found
[    1.219769] hub 6-0:1.0: 2 ports detected
[    1.254232] usbcore: registered new interface driver libusual
[    1.254253] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.256519] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.256522] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.256590] mousedev: PS/2 mouse device common for all mice
[    1.256665] rtc_cmos 00:06: RTC can wake from S4
[    1.256747] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.256770] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.256809] device-mapper: uevent: version 1.0.3
[    1.256846] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.256897] cpuidle: using governor ladder
[    1.256972] cpuidle: using governor menu
[    1.256973] EFI Variables Facility v0.08 2004-May-17
[    1.257079] TCP cubic registered
[    1.257132] NET: Registered protocol family 10
[    1.257353] NET: Registered protocol family 17
[    1.257355] Registering the dns_resolver key type
[    1.257480] PM: Hibernation image not present or could not be loaded.
[    1.257488] registered taskstats version 1
[    1.262398]   Magic number: 12:908:336
[    1.262410] tty tty57: hash matches
[    1.262493] rtc_cmos 00:06: setting system clock to 2012-09-27 15:20:52 UTC (1348759252)
[    1.262993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.262994] EDD information not available.
[    1.390050] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.390075] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.390990] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.390999] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff88019405eed8), AE_NOT_FOUND (20110623/psparse-536)
[    1.391213] ata3.00: ATA-8: WDC WD5000AADS-00S9B0, 01.00A01, max UDMA/133
[    1.391218] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.392244] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.392253] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff88019405eed8), AE_NOT_FOUND (20110623/psparse-536)
[    1.392546] ata3.00: configured for UDMA/133
[    1.392766] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AADS-0 01.0 PQ: 0 ANSI: 5
[    1.392855] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.392859] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff880194072050), AE_NOT_FOUND (20110623/psparse-536)
[    1.392874] ata6.00: ATAPI: HL-DT-ST BD-RE  WH12LS30, 1.00, max UDMA/133
[    1.392905] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.392940] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.393122] sd 2:0:0:0: [sda] Write Protect is off
[    1.393124] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.393220] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.396986] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.396994] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff880194072050), AE_NOT_FOUND (20110623/psparse-536)
[    1.397009] ata6.00: configured for UDMA/133
[    1.402669] scsi 5:0:0:0: CD-ROM            HL-DT-ST BD-RE  WH12LS30  1.00 PQ: 0 ANSI: 5
[    1.406809] sr0: scsi3-mmc drive: 94x/94x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.406813] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.406971] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.407055] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    1.430003] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.434099]  sda: sda1 sda2 < sda5 >
[    1.434923] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.435859] Freeing unused kernel memory: 920k freed
[    1.435926] Write protecting the kernel read-only data: 12288k
[    1.438837] Freeing unused kernel memory: 1616k freed
[    1.441009] Freeing unused kernel memory: 1200k freed
[    1.451286] udevd[118]: starting version 175
[    1.461847] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.461863] r8169 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.461897] r8169 0000:03:00.0: setting latency timer to 64
[    1.463369] r8169 0000:03:00.0: irq 48 for MSI/MSI-X
[    1.463598] r8169 0000:03:00.0: eth0: RTL8168f/8111f at 0xffffc90000c7a000, 30:85:a9:8e:8b:ba, XID 08000800 IRQ 48
[    1.463600] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.562558] hub 1-1:1.0: USB hub found
[    1.562632] hub 1-1:1.0: 6 ports detected
[    1.673780] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.753685] Refined TSC clocksource calibration: 3410.013 MHz.
[    1.753691] Switching to clocksource tsc
[    1.806309] hub 2-1:1.0: USB hub found
[    1.806391] hub 2-1:1.0: 8 ports detected
[    1.973476] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[    2.001181] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[    2.001183] usb 3-1: ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[    2.007026] Initializing USB Mass Storage driver...
[    2.007035] usbcore: registered new interface driver uas
[    2.007078] scsi6 : usb-storage 3-1:1.0
[    2.007121] usbcore: registered new interface driver usb-storage
[    2.007122] USB Mass Storage support registered.
[    2.117333] usb 3-2: new low-speed USB device number 3 using xhci_hcd
[    2.171042] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.337120] usb 5-2: new high-speed USB device number 2 using xhci_hcd
[    2.359346] hub 5-2:1.0: USB hub found
[    2.359619] hub 5-2:1.0: 4 ports detected
[    2.405258] generic-usb 0003:051D:0002.0001: hiddev0,hidraw0: USB HID v1.10 Device [APC Back-UPS ES 550 FW:843.K2 .D USB FW:K2 ] on usb-0000:00:14.0-2/input0
[    2.405277] usbcore: registered new interface driver usbhid
[    2.405278] usbhid: USB HID core driver
[    2.433170] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
[    2.601005] usb 2-1.6: new full-speed USB device number 4 using ehci_hcd
[    2.768935] usb 5-2.1: new high-speed USB device number 3 using xhci_hcd
[    2.826038] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    2.826040] vesafb: scrolling: redraw
[    2.826041] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.828577] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90005800000, using 5120k, total 5120k
[    2.828708] Console: switching to colour frame buffer device 160x64
[    2.828722] fb0: VESA VGA frame buffer device
[    2.860837] usb 5-2.2: new high-speed USB device number 4 using xhci_hcd
[    2.877220] usb 5-2.2: ep 0x83 - rounding interval to 32768 microframes, ep desc says 0 microframes
[    3.007388] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent        102C PQ: 0 ANSI: 4
[    3.007635] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.009411] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.010573] sd 6:0:0:0: [sdb] Write Protect is off
[    3.010578] sd 6:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[    3.011820] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.016407]  sdb: sdb1
[    3.026429] sd 6:0:0:0: [sdb] Attached SCSI disk
[    3.141302] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.419024] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.580950] udevd[383]: starting version 175
[   13.981310] Adding 5974012k swap on /dev/sda5.  Priority:-1 extents:1 across:5974012k 
[   16.106464] lp: driver loaded but no devices found
[   16.355786] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.500582] wmi: Mapper loaded
[   16.540873] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   16.541081] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.541085] mei 0000:00:16.0: setting latency timer to 64
[   16.541135] mei 0000:00:16.0: irq 49 for MSI/MSI-X
[   16.580502] asus_wmi: ASUS WMI generic driver loaded
[   16.632013] asus_wmi: Initialization: 0x0
[   16.632027] asus_wmi: BIOS WMI version: 0.9
[   16.632049] asus_wmi: SFUN value: 0x0
[   16.632195] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input2
[   17.474672] nvidia: module license 'NVIDIA' taints kernel.
[   17.474676] Disabling lock debugging due to kernel taint
[   17.509303] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.509309] nvidia 0000:01:00.0: setting latency timer to 64
[   17.509312] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.509367] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   17.778857] Bluetooth: Core ver 2.16
[   17.778868] NET: Registered protocol family 31
[   17.778869] Bluetooth: HCI device and connection manager initialized
[   17.778870] Bluetooth: HCI socket layer initialized
[   17.778871] Bluetooth: L2CAP socket layer initialized
[   17.778873] Bluetooth: SCO socket layer initialized
[   17.797317] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   17.797424] usbcore: registered new interface driver btusb
[   17.873118] logitech-djreceiver 0003:046D:C52B.0004: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.6/input2
[   17.876021] input: Logitech Unifying Device. Wireless PID:1025 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0004/input/input3
[   17.876091] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1025] on usb-0000:00:1d.0-1.6:1
[   17.878069] input: Logitech Unifying Device. Wireless PID:200a as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0004/input/input4
[   17.878114] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:200a] on usb-0000:00:1d.0-1.6:2
[   17.988553] Linux video capture interface: v2.00
[   17.997862] uvcvideo: Found UVC 1.00 device USB 2.0 CAMERA (1c4f:3002)
[   17.998907] input: USB 2.0 CAMERA as /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2/5-2.1/5-2.1:1.0/input/input5
[   17.998945] usbcore: registered new interface driver uvcvideo
[   17.998946] USB Video Class driver (1.1.1)
[   18.034004] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.034051] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   18.034077] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   18.064385] usbcore: registered new interface driver snd-usb-audio
[   18.194496] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.194562] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.194598] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.194631] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.194661] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.194693] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.194723] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.194761] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.194900] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.194902] hda_intel: Disabling MSI
[   18.194934] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   18.908987] HDMI status: Codec=0 Pin=4 Presence_Detect=0 ELD_Valid=0
[   18.916969] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.917064] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input14
[   18.917189] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input15
[   19.787412] type=1400 audit(1348759271.038:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=980 comm="apparmor_parser"
[   19.787460] type=1400 audit(1348759271.038:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=979 comm="apparmor_parser"
[   19.787471] type=1400 audit(1348759271.038:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1050 comm="apparmor_parser"
[   19.787622] type=1400 audit(1348759271.038:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   19.787670] type=1400 audit(1348759271.038:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser"
[   19.787682] type=1400 audit(1348759271.038:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1050 comm="apparmor_parser"
[   19.787740] type=1400 audit(1348759271.038:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser"
[   19.787789] type=1400 audit(1348759271.038:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser"
[   19.787802] type=1400 audit(1348759271.038:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1050 comm="apparmor_parser"
[   20.032224] init: failsafe main process (1076) killed by TERM signal
[   20.570971] type=1400 audit(1348759271.822:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1153 comm="apparmor_parser"
[   20.846798] ppdev: user-space parallel port driver
[   21.136820] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.136822] Bluetooth: BNEP filters: protocol multicast
[   21.347729] Bluetooth: RFCOMM TTY layer initialized
[   21.347732] Bluetooth: RFCOMM socket layer initialized
[   21.347733] Bluetooth: RFCOMM ver 1.11
[   22.918258] r8169 0000:03:00.0: eth0: link down
[   22.918263] r8169 0000:03:00.0: eth0: link down
[   22.918627] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.918781] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.650689] kvm: disabled by bios
[   23.717361] init: qemu-kvm pre-start process (1233) terminated with status 1
[   23.868069] vboxdrv: Found 4 processor cores.
[   23.868146] vboxdrv: fAsync=0 offMin=0x1f4 offMax=0x29f5
[   23.868184] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.868185] vboxdrv: Successfully loaded version 4.2.0 (interface 0x001a0004).
[   24.218068] vboxpci: IOMMU not found (not registered)
[   24.557075] r8169 0000:03:00.0: eth0: link up
[   24.702103] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.653735] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[   25.658389] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[   25.672495] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=1
[   25.678369] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1
[   26.445659] HDMI: detected monitor H233H
[   26.445661]         at connection type HDMI
[   26.445664] HDMI: available speakers: FL/FR
[   26.445669] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   35.253288] eth0: no IPv6 routers present
[   98.698463] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -32 (exp. 1).
[   98.699397] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -32 (exp. 2).
[   98.699807] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -32 (exp. 2).
[   98.700686] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -32 (exp. 2).
[  101.711838] UDF-fs: Partition marked readonly; forcing readonly mount
[  101.766345] UDF-fs: INFO Mounting volume 'RICHARD_JENI_A_BIG_STEAMING', timestamp 2005/04/13 17:53 (1f10)
[  374.863281] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[  374.868605] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[  375.911550] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[  375.916141] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[  375.930904] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=1
[  375.936090] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1
[  376.727754] HDMI: detected monitor H233H
[  376.727756]         at connection type HDMI
[  376.727759] HDMI: available speakers: FL/FR
[  376.727763] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[  421.927329] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -32 (exp. 1).
[  421.927658] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -32 (exp. 2).
[  421.927981] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -32 (exp. 2).
[  421.928314] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -32 (exp. 2).
[  918.075802] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
```

---

### Post by Rexilion on 2012-09-29
> **netopalis45 said:**
> Not sure why that happened and don't have a pastbin account so I'm going to try this again

You don't need an account to create a pastebin.com link ;)

I guess this is not the dmesg from the moment you left on the computer and discovered the morning after that things are ok? Would be interesting.

I don't see anything here...

---

### Post by netopalis45 on 2012-11-23
I think I finally know whats going on. For some reason all my applications have about 10 threads so they use up a lot of RAM and then force some of it into swap, even though it doesn't show the swap being used. I have 6 GB of RAM so I don't know why it would be using that. Is there any reason why everything has so many threads?

---

### Post by Rexilion on 2012-11-23
> **netopalis45 said:**
> I think I finally know whats going on. For some reason all my applications have about 10 threads so they use up a lot of RAM and then force some of it into swap, even though it doesn't show the swap being used. I have 6 GB of RAM so I don't know why it would be using that. Is there any reason why everything has so many threads?

Many threads does not imply high RAM usage. If an app is using much RAM, then this is either intentional or a bug.

Care to show the output of 'top'?

---

### Post by netopalis45 on 2012-11-23
The best I can do is a screenshot since "top" and "htop" don't seem to want to output to a text file, is that alright?

---

### Post by Wim Sturkenboom on 2012-11-23
You can drag the mouse over top output in the terminal and that way select a part of the top output. Next press <ctrl><shift>c to copy and after that you can paste.

PS
You can sort the top output by memory usage by pressing capital M.

---

### Post by Rexilion on 2012-11-23
I'm sorry, I didn't think this through as in taking a snapshot of top...

> top -b -n1 > top.log

Paste top.log at [www.pastebin.com](www.pastebin.com) and paste te link here.

---

### Post by netopalis45 on 2012-11-23
I am unable to create the top.log file. Whenever I use the command to make it it looks like it works but when I try to view the file I get the error "E297: Write error in swap file top.log OL, OC" in vim.

---

### Post by Rexilion on 2012-11-24
Try doing this:

> top -b -n1

And copy the output to pastebin.com

---

### Post by netopalis45 on 2012-11-24
I did that and when I try to open t the file I get the error I posted above

---

### Post by Wim Sturkenboom on 2012-11-24
_top -b -n1_ does not output to file ;)

---

### Post by Rexilion on 2012-11-26
> **netopalis45 said:**
> I did that and when I try to open t the file I get the error I posted above

I said to copy _the output_ (which all happens in memory). Creating the file apparently fails since your disk is full...

---

### Post by philinux on 2012-11-26
Have a look at this.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by netopalis45 on 2012-11-27
Thanks philinux, I took a look at that and it seems to have done some good but not enough. This has happened several times even after reinstalling, but only on this machine. I have a laptop that is set up almost the same and it doesn't have this problem at all. This computer is set up as a small web server but I don't think anybody knows its here and I'm the only one who accesses it to work on the pages. 
It only seems to happen after installing updates for certain packages (sorry, don't know which ones) or installing one package (at one point it was nexuiz) and all of a sudden it is out of room. I have over 1.5TB of space so there is no way it should be filling up like that.

---

### Post by philinux on 2012-11-27
> **netopalis45 said:**
> Thanks philinux, I took a look at that and it seems to have done some good but not enough. This has happened several times even after reinstalling, but only on this machine. I have a laptop that is set up almost the same and it doesn't have this problem at all. This computer is set up as a small web server but I don't think anybody knows its here and I'm the only one who accesses it to work on the pages. 
It only seems to happen after installing updates for certain packages (sorry, don't know which ones) or installing one package (at one point it was nexuiz) and all of a sudden it is out of room. I have over 1.5TB of space so there is no way it should be filling up like that.

Could be log files. Check in /var/log or your home folder logs.

Or old backup files. If you follow that guide it should reveal all large files.

---

### Post by netopalis45 on 2012-11-27
I already did that and I don't have any large backup files on my main drive.  Would it be bad if I deleted all the log files?

---

### Post by philinux on 2012-11-27
> **netopalis45 said:**
> I already did that and I don't have any large backup files on my main drive.  Would it be bad if I deleted all the log files?

Log files should rotate. The app logrotate looks after that. 

No harm deleting log files though. However just be aware that they'll end up in roots trash from /var/log if you just delete them normally.

You can then see which one or more is the culprit by checking /var/log routinely.

---

