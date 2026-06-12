---
title: "deleted inode reference: 16"
date: 2010-12-08
forum: General Help
---

### Post by enhu on 2010-12-08
been receiving this error in ubuntu these days,how can i fix this?

```

enhu@ubuntu$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@lakoocha) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33~lucid1-Ubuntu SMP Sat Sep 18 07:57:32 UTC 2010 (Ubuntu 2.6.35-22.33~lucid1-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7fc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7fc00 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  modified: 000000001ff70000 - 000000001ff7fc00 (ACPI data)
[    0.000000]  modified: 000000001ff7fc00 - 000000001ff80000 (ACPI NVS)
[    0.000000]  modified: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 15000-1a000
[    0.000000] RAMDISK: 1726a000 - 17fd4000
[    0.000000] ACPI: RSDP 000f65a0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 1ff7c715 00028 (v01 PTLTD  ? RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 1ff7fb8c 00074 (v01 INTEL  Solano   06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT 1ff7c73d 0344F (v01  INTEL   Solano 06040000 MSFT 0100000B)
[    0.000000] ACPI: FACS 1ff7ffc0 00040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c07fff40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dfb80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=79c7c6ab-7e62-4333-9ccf-01b4e5eedeac ro setkmap=fr splash vga=773 quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2618240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (39 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a085c]   TEXT DATA BSS
[    0.000000]   #3 [001726a000 - 0017fd4000]         RAMDISK
[    0.000000]   #4 [000009f800 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a1000 - 00009a4128]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001401000]         BOOTMEM
[    0.000000]   #11 [0001401000 - 0001401004]         BOOTMEM
[    0.000000]   #12 [0001401040 - 0001401100]         BOOTMEM
[    0.000000]   #13 [0001401100 - 0001401130]         BOOTMEM
[    0.000000]   #14 [0001401140 - 0001402940]         BOOTMEM
[    0.000000]   #15 [0001402940 - 0001402a58]         BOOTMEM
[    0.000000]   #16 [0001402a80 - 0001402ac0]         BOOTMEM
[    0.000000]   #17 [0001402ac0 - 0001402b00]         BOOTMEM
[    0.000000]   #18 [0001402b00 - 0001402b40]         BOOTMEM
[    0.000000]   #19 [0001402b40 - 0001402b80]         BOOTMEM
[    0.000000]   #20 [0001402b80 - 0001402bc0]         BOOTMEM
[    0.000000]   #21 [0001402bc0 - 0001402c00]         BOOTMEM
[    0.000000]   #22 [0001402c00 - 0001402c40]         BOOTMEM
[    0.000000]   #23 [0001402c40 - 0001402c80]         BOOTMEM
[    0.000000]   #24 [0001402c80 - 0001402cc0]         BOOTMEM
[    0.000000]   #25 [0001402cc0 - 0001402cd0]         BOOTMEM
[    0.000000]   #26 [0001402d00 - 0001402d84]         BOOTMEM
[    0.000000]   #27 [0001402dc0 - 0001402e44]         BOOTMEM
[    0.000000]   #28 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #29 [0001404e80 - 0001404e84]         BOOTMEM
[    0.000000]   #30 [0001404ec0 - 0001404ec4]         BOOTMEM
[    0.000000]   #31 [0001404f00 - 0001404f04]         BOOTMEM
[    0.000000]   #32 [0001404f40 - 0001404f44]         BOOTMEM
[    0.000000]   #33 [0001404f80 - 0001405030]         BOOTMEM
[    0.000000]   #34 [0001405040 - 00014050e8]         BOOTMEM
[    0.000000]   #35 [0001402e80 - 0001404e80]         BOOTMEM
[    0.000000]   #36 [0001405100 - 0001445100]         BOOTMEM
[    0.000000]   #37 [0001445100 - 0001465100]         BOOTMEM
[    0.000000]   #38 [0001466000 - 00016e5380]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 493528k/523712k available (4929k kernel code, 29732k reserved, 2336k data, 684k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d056e - 0xc0818868   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d056e   (4929 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 897.404 MHz processor.
[    0.008013] Calibrating delay loop (skipped), value calculated using timer frequency.. 1794.80 BogoMIPS (lpj=3589616)
[    0.008029] pid_max: default: 32768 minimum: 301
[    0.008106] Security Framework initialized
[    0.008177] AppArmor: AppArmor initialized
[    0.008183] Yama: becoming mindful.
[    0.008365] Mount-cache hash table entries: 512
[    0.008771] Initializing cgroup subsys ns
[    0.008789] Initializing cgroup subsys cpuacct
[    0.008804] Initializing cgroup subsys memory
[    0.008832] Initializing cgroup subsys devices
[    0.008842] Initializing cgroup subsys freezer
[    0.008849] Initializing cgroup subsys net_cls
[    0.008937] mce: CPU supports 5 MCE banks
[    0.008989] Performance Events: 
[    0.008997] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.009004] no hardware sampling interrupt available.
[    0.009011] p6 PMU driver.
[    0.009048] ... version:                0
[    0.009055] ... bit width:              32
[    0.009061] ... generic registers:      2
[    0.009068] ... value mask:             00000000ffffffff
[    0.009075] ... max period:             000000007fffffff
[    0.009081] ... fixed-purpose events:   0
[    0.009087] ... event mask:             0000000000000003
[    0.010803] SMP alternatives: switching to UP code
[    0.026349] Freeing SMP alternatives: 24k freed
[    0.026446] ACPI: Core revision 20100428
[    0.032852] ACPI: setting ELCR to 0200 (from 0e00)
[    0.032991] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033017] ftrace: allocating 21758 entries in 43 pages
[    0.036353] weird, boot CPU (#0) not listed by the BIOS.
[    0.036368] SMP motherboard not detected.
[    0.036376] Local APIC not detected. Using dummy APIC emulation.
[    0.036381] SMP disabled
[    0.037246] Brought up 1 CPUs
[    0.037264] Total of 1 processors activated (1794.80 BogoMIPS).
[    0.040517] devtmpfs: initialized
[    0.045853] regulator: core version 0.5
[    0.045914] Time:  2:27:58  Date: 12/09/10
[    0.046070] NET: Registered protocol family 16
[    0.046460] EISA bus registered
[    0.046510] ACPI: bus type pci registered
[    0.047943] PCI: PCI BIOS revision 2.10 entry at 0xfd981, last bus=2
[    0.047952] PCI: Using configuration type 1 for base access
[    0.051153] bio: create slab <bio-0> at 0
[    0.053132] ACPI: EC: Look up EC in DSDT
[    0.058162] ACPI: Interpreter enabled
[    0.058180] ACPI: (supports S0 S1 S5)
[    0.058227] ACPI: Using PIC for interrupt routing
[    0.068113] ACPI: No dock devices found.
[    0.068132] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.071210] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.077263] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.077277] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.077287] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.077296] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.077304] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.077314] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xfebfffff]
[    0.077322] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.077374] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.077642] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
[    0.077653] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
[    0.077716] pci 0000:00:1f.1: reg 20: [io  0x1800-0x180f]
[    0.077812] pci 0000:00:1f.2: reg 20: [io  0x1820-0x183f]
[    0.077904] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf4ffffff]
[    0.077918] pci 0000:01:00.0: reg 14: [mem 0xf6000000-0xf7ffffff pref]
[    0.077949] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.078034] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.078045] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.078056] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf4ffffff]
[    0.078066] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf7ffffff pref]
[    0.078138] pci 0000:02:08.0: reg 10: [mem 0xf5010000-0xf5010fff]
[    0.078151] pci 0000:02:08.0: reg 14: [mem 0xf5000000-0xf500ffff]
[    0.078207] pci 0000:02:08.0: supports D1 D2
[    0.078215] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot
[    0.078225] pci 0000:02:08.0: PME# disabled
[    0.078278] pci 0000:02:0d.0: reg 10: [io  0x2000-0x207f]
[    0.078292] pci 0000:02:0d.0: reg 14: [mem 0xf5011000-0xf501107f]
[    0.078326] pci 0000:02:0d.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.078354] pci 0000:02:0d.0: supports D1 D2
[    0.078361] pci 0000:02:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.078370] pci 0000:02:0d.0: PME# disabled
[    0.078411] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.078422] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.078433] pci 0000:00:1e.0:   bridge window [mem 0xf5000000-0xf50fffff]
[    0.078444] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.078453] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.078462] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.078470] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.078479] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.078488] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.078496] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0xfebfffff] (subtractive decode)
[    0.078505] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.078526] pci_bus 0000:00: on NUMA node 0
[    0.078549] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.078717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.078809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.081664] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.081913] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.082144] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.082379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.082577] HEST: Table is not found!
[    0.082862] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.082874] vgaarb: loaded
[    0.083429] SCSI subsystem initialized
[    0.083712] libata version 3.00 loaded.
[    0.083946] usbcore: registered new interface driver usbfs
[    0.084063] usbcore: registered new interface driver hub
[    0.084246] usbcore: registered new device driver usb
[    0.084841] ACPI: WMI: Mapper loaded
[    0.084852] PCI: Using ACPI for IRQ routing
[    0.084866] PCI: pci_cache_line_size set to 32 bytes
[    0.084959] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.084968] reserve RAM buffer: 000000001ff70000 - 000000001fffffff 
[    0.085339] NetLabel: Initializing
[    0.085349] NetLabel:  domain hash size = 128
[    0.085354] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.085406] NetLabel:  unlabeled traffic allowed by default
[    0.085607] Switching to clocksource tsc
[    0.121542] AppArmor: AppArmor Filesystem Enabled
[    0.121624] pnp: PnP ACPI init
[    0.121696] ACPI: bus type pnp registered
[    0.126608] ERROR: Unable to locate IOAPIC for GSI 13
[    0.126723] ERROR: Unable to locate IOAPIC for GSI 8
[    0.126932] ERROR: Unable to locate IOAPIC for GSI 1
[    0.128199] ERROR: Unable to locate IOAPIC for GSI 4
[    0.129270] ERROR: Unable to locate IOAPIC for GSI 3
[    0.130615] ERROR: Unable to locate IOAPIC for GSI 6
[    0.131620] ACPI Error: Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) (20100428/dsopcode-597)
[    0.131645] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node df81d228), AE_AML_BUFFER_LIMIT
[    0.131711] ACPI Error (uteval-0250): Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node df81d228), AE_AML_BUFFER_LIMIT
[    0.131732] pnp 00:0b: can't evaluate _CRS: 12298
[    0.132829] pnp: PnP ACPI: found 12 devices
[    0.132840] ACPI: ACPI bus type pnp unregistered
[    0.132853] PnPBIOS: Disabled by ACPI PNP
[    0.132912] system 00:02: [io  0x1000-0x107f] has been reserved
[    0.132922] system 00:02: [io  0x1180-0x11bf] has been reserved
[    0.132933] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.132945] system 00:02: [mem 0xff800000-0xffffffff] could not be reserved
[    0.173476] pci 0000:00:1e.0: BAR 15: assigned [mem 0x20000000-0x200fffff pref]
[    0.173493] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x10000)
[    0.173503] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.173509] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.173523] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf4ffffff]
[    0.173533] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf7ffffff pref]
[    0.173548] pci 0000:02:0d.0: BAR 6: assigned [mem 0x20000000-0x2001ffff pref]
[    0.173558] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.173566] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.173578] pci 0000:00:1e.0:   bridge window [mem 0xf5000000-0xf50fffff]
[    0.173589] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0x200fffff pref]
[    0.173631] pci 0000:00:1e.0: setting latency timer to 64
[    0.173644] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.173652] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.173660] pci_bus 0000:00: resource 6 [mem 0x000d4000-0x000d7fff]
[    0.173668] pci_bus 0000:00: resource 7 [mem 0x000d8000-0x000dbfff]
[    0.173676] pci_bus 0000:00: resource 8 [mem 0x000dc000-0x000dffff]
[    0.173684] pci_bus 0000:00: resource 9 [mem 0x20000000-0xfebfffff]
[    0.173691] pci_bus 0000:00: resource 10 [io  0x0d00-0xffff]
[    0.173700] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf4ffffff]
[    0.173708] pci_bus 0000:01: resource 2 [mem 0xf6000000-0xf7ffffff pref]
[    0.173716] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.173724] pci_bus 0000:02: resource 1 [mem 0xf5000000-0xf50fffff]
[    0.173732] pci_bus 0000:02: resource 2 [mem 0x20000000-0x200fffff pref]
[    0.173740] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.173748] pci_bus 0000:02: resource 5 [mem 0x000a0000-0x000bffff]
[    0.173755] pci_bus 0000:02: resource 6 [mem 0x000d4000-0x000d7fff]
[    0.173763] pci_bus 0000:02: resource 7 [mem 0x000d8000-0x000dbfff]
[    0.173771] pci_bus 0000:02: resource 8 [mem 0x000dc000-0x000dffff]
[    0.173779] pci_bus 0000:02: resource 9 [mem 0x20000000-0xfebfffff]
[    0.173787] pci_bus 0000:02: resource 10 [io  0x0d00-0xffff]
[    0.173935] NET: Registered protocol family 2
[    0.174148] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.174930] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.175390] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.176104] TCP: Hash tables configured (established 16384 bind 16384)
[    0.176115] TCP reno registered
[    0.176137] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.176191] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.176617] NET: Registered protocol family 1
[    0.176756] pci 0000:01:00.0: Boot video device
[    0.176776] PCI: CLS 32 bytes, default 32
[    0.177404] cpufreq-nforce2: No nForce2 chipset.
[    0.177483] Scanning for low memory corruption every 60 seconds
[    0.177949] audit: initializing netlink socket (disabled)
[    0.177992] type=2000 audit(1291861678.172:1): initialized
[    0.205671] Trying to unpack rootfs image as initramfs...
[    0.235620] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.248516] VFS: Disk quotas dquot_6.5.2
[    0.248810] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.254889] fuse init (API version 7.14)
[    0.255429] msgmni has been set to 963
[    0.264161] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.264176] io scheduler noop registered
[    0.264182] io scheduler deadline registered
[    0.264255] io scheduler cfq registered (default)
[    0.264626] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.264695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.265094] vesafb: framebuffer at 0xf6000000, mapped to 0xe0800000, using 768k, total 768k
[    0.265105] vesafb: mode is 1024x768x8, linelength=1024, pages=0
[    0.265111] vesafb: scrolling: redraw
[    0.265121] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
[    0.282365] Console: switching to colour frame buffer device 128x48
[    0.299118] fb0: VESA VGA frame buffer device
[    0.331428] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.331468] ACPI: Power Button [PWRB]
[    0.331632] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.331645] ACPI: Power Button [PWRF]
[    0.331943] ACPI: acpi_idle registered with cpuidle
[    0.332033] ACPI: Invalid PBLK length [5]
[    0.340555] ERST: Table is not found!
[    0.341373] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.341574] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.341822] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.342759] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.343118] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.350539] isapnp: Scanning for PnP cards...
[    0.360364] brd: module loaded
[    0.410598] loop: module loaded
[    0.411469] ata_piix 0000:00:1f.1: version 2.13
[    0.411899] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    0.412137] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    0.412296] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.418868] scsi0 : ata_piix
[    0.419454] scsi1 : ata_piix
[    0.421497] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[    0.421510] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[    0.422829] Fixed MDIO Bus: probed
[    0.422958] PPP generic driver version 2.4.2
[    0.423182] tun: Universal TUN/TAP device driver, 1.6
[    0.423190] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.423533] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.423632] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.423673] uhci_hcd: USB Universal Host Controller Interface driver
[    0.424366] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    0.424377] PCI: setting IRQ 9 as level-triggered
[    0.424389] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.424415] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    0.424424] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    0.424648] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.424710] uhci_hcd 0000:00:1f.2: irq 9, io base 0x00001820
[    0.425250] hub 1-0:1.0: USB hub found
[    0.425273] hub 1-0:1.0: 2 ports detected
[    0.425617] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
[    0.425627] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.430790] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.431372] mice: PS/2 mouse device common for all mice
[    0.432099] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.432147] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.432631] device-mapper: uevent: version 1.0.3
[    0.433505] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.438392] device-mapper: multipath: version 1.1.1 loaded
[    0.438411] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.446359] EISA: Probing bus 0 at eisa.0
[    0.446375] EISA: Cannot allocate resource for mainboard
[    0.446384] Cannot allocate resource for EISA slot 1
[    0.446390] Cannot allocate resource for EISA slot 2
[    0.446396] Cannot allocate resource for EISA slot 3
[    0.446402] Cannot allocate resource for EISA slot 4
[    0.446408] Cannot allocate resource for EISA slot 5
[    0.446414] Cannot allocate resource for EISA slot 6
[    0.446420] Cannot allocate resource for EISA slot 7
[    0.446426] Cannot allocate resource for EISA slot 8
[    0.446432] EISA: Detected 0 cards.
[    0.446778] cpuidle: using governor ladder
[    0.446787] cpuidle: using governor menu
[    0.447848] TCP cubic registered
[    0.448486] NET: Registered protocol family 10
[    0.449918] lo: Disabled Privacy Extensions
[    0.450740] NET: Registered protocol family 17
[    0.450941] Using IPI No-Shortcut mode
[    0.451347] PM: Resume from disk failed.
[    0.451407] registered taskstats version 1
[    0.451737]   Magic number: 6:846:459
[    0.455067] rtc_cmos 00:05: setting system clock to 2010-12-09 02:27:58 UTC (1291861678)
[    0.455137] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.455143] EDD information not available.
[    0.455459] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.615307] ata1.00: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/100
[    0.615322] ata1.00: 78165360 sectors, multi 16: LBA 
[    0.615387] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.622826] ata1.00: configured for UDMA/33
[    0.782651] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    0.954279] isapnp: No Plug & Play device found
[    0.954910] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    0.955512] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.955948] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.956187] sd 0:0:0:0: [sda] Write Protect is off
[    0.956197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.956302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.957108]  sda: sda1 sda2 sda3
[    1.015839] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.120729] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    1.925345] Freeing initrd memory: 13736k freed
[    2.001214] Freeing unused kernel memory: 684k freed
[    2.005320] Write protecting the kernel text: 4932k
[    2.005437] Write protecting the kernel read-only data: 1980k
[    2.096842] udev: starting version 151
[    2.860139] FDC 0 is a post-1991 82077
[    2.963320] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    2.963335] PCI: setting IRQ 10 as level-triggered
[    2.963347] 3c59x 0000:02:0d.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.963383] 3c59x: Donald Becker and others.
[    2.963404] 0000:02:0d.0: 3Com PCI 3c905C Tornado at e07fe000.
[    3.064836] Linux agpgart interface v0.103
[    3.121284] Initializing USB Mass Storage driver...
[    3.134008] scsi2 : usb-storage 1-2:1.0
[    3.135841] agpgart-intel 0000:00:00.0: Intel i815 Chipset
[    3.144878] usbcore: registered new interface driver usb-storage
[    3.144889] USB Mass Storage support registered.
[    3.263522] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    3.283545] usbcore: registered new interface driver hiddev
[    3.286619] [drm] Initialized drm 1.1.0 20060810
[    3.300321] input: OM as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input3
[    3.302256] generic-usb 0003:04F3:0232.0001: input,hidraw0: USB HID v1.11 Mouse [OM] on usb-0000:00:1f.2-1/input0
[    3.302931] usbcore: registered new interface driver usbhid
[    3.302946] usbhid: USB HID core driver
[    3.568885] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    3.568900] PCI: setting IRQ 11 as level-triggered
[    3.568914] nouveau 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.587356] [drm] nouveau 0000:01:00.0: Detected an NV 0 generation card (0x20154000)
[    3.587379] checking generic (f6000000 c0000) vs hw (f6000000 2000000)
[    3.587387] fb: conflicting fb hw usage nouveaufb vs VESA VGA - removing generic driver
[    3.587513] Console: switching to colour dummy device 80x25
[    3.590004] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    3.642820] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    3.643372] [drm] nouveau 0000:01:00.0: BMP BIOS found
[    3.643381] [drm] nouveau 0000:01:00.0: BMP version 2.1
[    3.643391] [drm] nouveau 0000:01:00.0: Bios version 02.05.13.04
[    3.643399] [drm] nouveau 0000:01:00.0: Assuming a CRT output exists
[    3.643407] [drm] nouveau 0000:01:00.0: Probing TV encoders on I2C bus: 1
[    3.648871] [drm] nouveau 0000:01:00.0: No TV encoders found.
[    3.649741] [drm] nouveau 0000:01:00.0: Detected 32MiB VRAM
[    3.660816] [TTM] Zone  kernel: Available graphics memory: 253986 kiB.
[    3.660826] [TTM] Initializing pool allocator.
[    3.661019] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[    3.661053] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[    3.661086] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[    3.661111] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[    3.661451] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[    3.663188] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[    3.663308] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    3.664701] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[    3.785735] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x45000, bo dfb84400
[    3.850618] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[    3.850633] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output @
[    3.851579] Console: switching to colour frame buffer device 128x48
[    3.854275] fb0: nouveaufb frame buffer device
[    3.854282] drm: registered panic notifier
[    3.854614] Slow work thread pool: Starting up
[    3.855391] Slow work thread pool: Ready
[    3.855424] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    4.155836] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler2.0  1.00 PQ: 0 ANSI: 2
[    4.161438] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.181766] sd 2:0:0:0: [sdb] 3903359 512-byte logical blocks: (1.99 GB/1.86 GiB)
[    4.184740] sd 2:0:0:0: [sdb] Write Protect is off
[    4.184753] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[    4.184761] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    4.200745] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    4.200790]  sdb: sdb1
[    4.251828] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    4.251851] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    4.691549] xor: automatically using best checksumming function: pIII_sse
[    4.708031]    pIII_sse  :  1822.000 MB/sec
[    4.708039] xor: using function: pIII_sse (1822.000 MB/sec)
[    4.726442] device-mapper: dm-raid45: initialized v0.2594b
[    5.161466] EXT3-fs: barriers not enabled
[    5.179974] kjournald starting.  Commit interval 5 seconds
[    5.180198] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   16.548574] Adding 1654688k swap on /dev/sda3.  Priority:-1 extents:1 across:1654688k 
[   16.648458] EXT3-fs (sda1): using internal journal
[   16.739273] udev: starting version 151
[   17.264423] intel_rng: FWH not detected
[   17.309452] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.659973] lp: driver loaded but no devices found
[   18.233363] parport_pc: probe of 00:0b failed with error -22
[   18.233682] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE]
[   18.234210] parport0: irq 7 detected
[   18.380650] lp0: using parport0 (polling).
[   18.848161] ppdev: user-space parallel port driver
[   21.605400] CS4281 0000:02:08.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[   22.312153] gameport gameport0: CS4281 Gameport is pci0000:02:08.0/gameport0, speed 1612kHz
[   22.663545] eth0:  setting full-duplex.
[   24.070542] [drm] nouveau 0000:01:00.0: Setting dpms mode 1 on vga encoder (output 0)
[   25.537946] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   33.024050] eth0: no IPv6 routers present
enhu@ubuntu ~ $ 

```

any suggestions?

---

### Post by dcstar on 2010-12-08
> **enhu said:**
> been receiving this error in ubuntu these days,how can i fix this?
.........

any suggestions?

What error?, I'm not going to trawl through all that just to try and find something you believe is a problem.

---

