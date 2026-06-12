---
title: "slow boot with udev"
date: 2010-11-06
forum: General Help
---

### Post by xxxYURAxxx on 2010-11-06
my ubuntu wait about 25 seconds on boot
dmesg:
```

[    0.815389] udev[90]: starting version 163
[    0.904058] sky2: driver version 1.28
[    0.904111] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.904125] sky2 0000:01:00.0: setting latency timer to 64
[    0.904161] sky2 0000:01:00.0: Yukon-2 EC chip revision 2
[    0.904269]   alloc irq_desc for 42 on node -1
[    0.904271]   alloc kstat_irqs on node -1
[    0.904289] sky2 0000:01:00.0: irq 42 for MSI/MSI-X
[    0.908050] sky2 0000:01:00.0: eth0: addr 00:1b:63:38:38:71
[    0.937638] firewire_ohci 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.993090] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.072046] firewire_ohci: Added fw-ohci device 0000:03:03.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    1.543633] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    1.565267] firewire_core: created device fw0: GUID 001d4ffffe72a1c0, S400
[    1.588057] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.024057] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.444054] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   25.427982] udev[364]: starting version 163

```

How can I speed up boot?

---

### Post by samee.zahur on 2010-11-27
I am having the exact same problems. I could be wrong about the timing, but I don't think this problem was here before upgrading to Maverick
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-23-generic-pae (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #40-Ubuntu SMP Wed Nov 17 22:32:51 UTC 2010 (Ubuntu 2.6.35-23.40-generic-pae 2.6.35.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7d9f000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7d9f000 - 00000000b7de0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7de0000 - 00000000b7e00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   4 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000b7e00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  modified: 00000000b7d90000 - 00000000b7d9f000 (ACPI data)
[    0.000000]  modified: 00000000b7d9f000 - 00000000b7de0000 (ACPI NVS)
[    0.000000]  modified: 00000000b7de0000 - 00000000b7e00000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 375b4000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a04000 - 0143f972
[    0.000000] Move RAMDISK from 00000000375b4000 - 0000000037fef971 to 00a04000 - 0143f971
[    0.000000] ACPI: RSDP 000f93d0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT b7d90100 00084 (v01 091009 XSDT1611 20090910 MSFT 00000097)
[    0.000000] ACPI: FACP b7d90290 000F4 (v03 _ASUS_ FACP1611 20090910 MSFT 00000097)
[    0.000000] ACPI: DSDT b7d90680 0C6AB (v01 _ASUS_ UL80A001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS b7d9f000 00040
[    0.000000] ACPI: APIC b7d90390 0005C (v01 _ASUS_ APIC1611 20090910 MSFT 00000097)
[    0.000000] ACPI: MCFG b7d90430 0003C (v01 _ASUS_ OEMMCFG  20090910 MSFT 00000097)
[    0.000000] ACPI: OEMX b7d90470 00176 (v01 _ASUS_ OEMX1611 20090910 MSFT 00000097)
[    0.000000] ACPI: ECDT b7d90620 00054 (v01 _ASUS_ OEMECDT  20090910 MSFT 00000097)
[    0.000000] ACPI: DBGP b7d903f0 00034 (v01 _ASUS_ DBGP1611 20090910 MSFT 00000097)
[    0.000000] ACPI: BOOT b7d905f0 00028 (v01 _ASUS_ BOOT1611 20090910 MSFT 00000097)
[    0.000000] ACPI: OEMB b7d9f040 00071 (v01 _ASUS_ OEMB1611 20090910 MSFT 00000097)
[    0.000000] ACPI: HPET b7d9cd30 00038 (v01 _ASUS_ OEMHPET  20090910 MSFT 00000097)
[    0.000000] ACPI: GSCI b7d9f0c0 02024 (v01 _ASUS_ GMCHSCI  20090910 MSFT 00000097)
[    0.000000] ACPI: ATKG b7da12f0 08024 (v01 _ASUS_  OEMATKG 20090910 MSFT 00000097)
[    0.000000] ACPI: SSDT b7da9dc0 004F0 (v01 _ASUS_    CpuPm 00003000 INTL 20051117)
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
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1015071
[    0.000000] free_area_init_node: node 0, pgdat c0840a00, node_mem_map c1441200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 778377 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
[    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b7e00000 (gap: b7e00000:47000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3e00000 s39872 r0 d21568 u1048576
[    0.000000] pcpu-alloc: s39872 r0 d21568 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1004830
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=964aea9d-17f5-4e28-9d6a-03a394e8d03d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 26214080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (46 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009fb65c]   TEXT DATA BSS
[    0.000000]   #3 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #4 [00009fc000 - 0000a03204]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [0000a04000 - 0001440000]     NEW RAMDISK
[    0.000000]   #9 [0001440000 - 0001441000]         BOOTMEM
[    0.000000]   #10 [0001441000 - 0003c41000]         BOOTMEM
[    0.000000]   #11 [0003c41000 - 0003c41004]         BOOTMEM
[    0.000000]   #12 [0003c41040 - 0003c41100]         BOOTMEM
[    0.000000]   #13 [0003c41100 - 0003c411a8]         BOOTMEM
[    0.000000]   #14 [0003c411c0 - 0003c441c0]         BOOTMEM
[    0.000000]   #15 [0003c441c0 - 0003c444dc]         BOOTMEM
[    0.000000]   #16 [0003c44500 - 0003c50500]         BOOTMEM
[    0.000000]   #17 [0003c50500 - 0003c5052d]         BOOTMEM
[    0.000000]   #18 [0003c50540 - 0003c5056f]         BOOTMEM
[    0.000000]   #19 [0003c50580 - 0003c5070c]         BOOTMEM
[    0.000000]   #20 [0003c50740 - 0003c50780]         BOOTMEM
[    0.000000]   #21 [0003c50780 - 0003c507c0]         BOOTMEM
[    0.000000]   #22 [0003c507c0 - 0003c50800]         BOOTMEM
[    0.000000]   #23 [0003c50800 - 0003c50840]         BOOTMEM
[    0.000000]   #24 [0003c50840 - 0003c50880]         BOOTMEM
[    0.000000]   #25 [0003c50880 - 0003c508c0]         BOOTMEM
[    0.000000]   #26 [0003c508c0 - 0003c50900]         BOOTMEM
[    0.000000]   #27 [0003c50900 - 0003c50940]         BOOTMEM
[    0.000000]   #28 [0003c50940 - 0003c50980]         BOOTMEM
[    0.000000]   #29 [0003c50980 - 0003c509c0]         BOOTMEM
[    0.000000]   #30 [0003c509c0 - 0003c509d0]         BOOTMEM
[    0.000000]   #31 [0003c50a00 - 0003c50a6e]         BOOTMEM
[    0.000000]   #32 [0003c50a80 - 0003c50aee]         BOOTMEM
[    0.000000]   #33 [0003e00000 - 0003e0f000]         BOOTMEM
[    0.000000]   #34 [0003f00000 - 0003f0f000]         BOOTMEM
[    0.000000]   #35 [0003c52b00 - 0003c52b04]         BOOTMEM
[    0.000000]   #36 [0003c52b40 - 0003c52b44]         BOOTMEM
[    0.000000]   #37 [0003c52b80 - 0003c52b88]         BOOTMEM
[    0.000000]   #38 [0003c52bc0 - 0003c52bc8]         BOOTMEM
[    0.000000]   #39 [0003c52c00 - 0003c52ca0]         BOOTMEM
[    0.000000]   #40 [0003c52cc0 - 0003c52d08]         BOOTMEM
[    0.000000]   #41 [0003c52d40 - 0003c56d40]         BOOTMEM
[    0.000000]   #42 [0003c56d40 - 0003cd6d40]         BOOTMEM
[    0.000000]   #43 [0003cd6d40 - 0003d16d40]         BOOTMEM
[    0.000000]   #44 [0003c50b00 - 0003c50d40]         BOOTMEM
[    0.000000]   #45 [0003f0f000 - 000580eec0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 3973012k/5242880k available (5087k kernel code, 87272k reserved, 2438k data, 704k init, 3147336k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc085a000 - 0xc090a000   ( 704 kB)
[    0.000000]       .data : 0xc05f7e2a - 0xc0859788   (2438 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f7e2a   (5087 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1297.346 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 2594.69 BogoMIPS (lpj=5189384)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004043] Security Framework initialized
[    0.004066] AppArmor: AppArmor initialized
[    0.004069] Yama: becoming mindful.
[    0.004152] Mount-cache hash table entries: 512
[    0.008059] Initializing cgroup subsys ns
[    0.008065] Initializing cgroup subsys cpuacct
[    0.008072] Initializing cgroup subsys memory
[    0.008086] Initializing cgroup subsys devices
[    0.008089] Initializing cgroup subsys freezer
[    0.008092] Initializing cgroup subsys net_cls
[    0.008133] CPU: Physical Processor ID: 0
[    0.008136] CPU: Processor Core ID: 0
[    0.008141] mce: CPU supports 6 MCE banks
[    0.008153] CPU0: Thermal monitoring handled by SMI
[    0.008158] using mwait in idle threads.
[    0.008167] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.008178] ... version:                2
[    0.008181] ... bit width:              40
[    0.008184] ... generic registers:      2
[    0.008187] ... value mask:             000000ffffffffff
[    0.008190] ... max period:             000000007fffffff
[    0.008193] ... fixed-purpose events:   3
[    0.008196] ... event mask:             0000000700000003
[    0.013248] ACPI: Core revision 20100428
[    0.036013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036021] ftrace: allocating 22402 entries in 44 pages
[    0.040061] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040446] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083812] CPU0: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
[    0.084000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.172018] Brought up 2 CPUs
[    0.172023] Total of 2 processors activated (5189.32 BogoMIPS).
[    0.173100] devtmpfs: initialized
[    0.173705] regulator: core version 0.5
[    0.173743] Time:  7:42:45  Date: 11/27/10
[    0.173808] NET: Registered protocol family 16
[    0.173842] Trying to unpack rootfs image as initramfs...
[    0.174010] EISA bus registered
[    0.174022] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.174026] ACPI: bus type pci registered
[    0.174144] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.174149] PCI: not using MMCONFIG
[    0.176176] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.176180] PCI: Using configuration type 1 for base access
[    0.180525] bio: create slab <bio-0> at 0
[    0.186242] ACPI: EC: EC description table is found, configuring boot EC
[    0.197986] ACPI: Executed 1 blocks of module-level executable AML code
[    0.204985] ACPI: BIOS _OSI(Linux) query ignored
[    0.216097] ACPI: SSDT b7da93f0 001C4 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.217420] ACPI: Dynamic OEM Table Load:
[    0.217426] ACPI: SSDT (null) 001C4 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.217987] ACPI: SSDT b7da9650 00765 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.219270] ACPI: Dynamic OEM Table Load:
[    0.219276] ACPI: SSDT (null) 00765 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.220029] ACPI: SSDT b7da9320 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.221332] ACPI: Dynamic OEM Table Load:
[    0.221338] ACPI: SSDT (null) 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.221614] ACPI: SSDT b7da95c0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.222900] ACPI: Dynamic OEM Table Load:
[    0.222906] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.223101] ACPI: Interpreter enabled
[    0.223111] ACPI: (supports S0 S3 S4 S5)
[    0.223159] ACPI: Using IOAPIC for interrupt routing
[    0.223336] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.228455] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.228460] PCI: Using MMCONFIG for extended config space
[    0.252829] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.253606] ACPI: No dock devices found.
[    0.253614] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.254600] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.255206] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.255212] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.255217] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.255222] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.255227] pci_root PNP0A08:00: host bridge window [mem 0xb7e00000-0xffffffff]
[    0.255325] pci 0000:00:02.0: reg 10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.255337] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.255345] pci 0000:00:02.0: reg 20: [io  0xdc00-0xdc07]
[    0.255404] pci 0000:00:02.1: reg 10: [mem 0xfe800000-0xfe8fffff 64bit]
[    0.255569] pci 0000:00:1a.0: reg 20: [io  0xd880-0xd89f]
[    0.255690] pci 0000:00:1a.1: reg 20: [io  0xd800-0xd81f]
[    0.255808] pci 0000:00:1a.7: reg 10: [mem 0xfe9fbc00-0xfe9fbfff]
[    0.255901] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.255908] pci 0000:00:1a.7: PME# disabled
[    0.255973] pci 0000:00:1b.0: reg 10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.256063] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.256071] pci 0000:00:1b.0: PME# disabled
[    0.256200] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.256208] pci 0000:00:1c.0: PME# disabled
[    0.256341] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.256348] pci 0000:00:1c.1: PME# disabled
[    0.256487] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.256494] pci 0000:00:1c.5: PME# disabled
[    0.256590] pci 0000:00:1d.0: reg 20: [io  0xd480-0xd49f]
[    0.256711] pci 0000:00:1d.1: reg 20: [io  0xd400-0xd41f]
[    0.256835] pci 0000:00:1d.2: reg 20: [io  0xd080-0xd09f]
[    0.256958] pci 0000:00:1d.3: reg 20: [io  0xd000-0xd01f]
[    0.257071] pci 0000:00:1d.7: reg 10: [mem 0xfe9fb800-0xfe9fbbff]
[    0.257164] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.257171] pci 0000:00:1d.7: PME# disabled
[    0.257452] pci 0000:00:1f.2: reg 10: [io  0xcc00-0xcc07]
[    0.257463] pci 0000:00:1f.2: reg 14: [io  0xc880-0xc883]
[    0.257474] pci 0000:00:1f.2: reg 18: [io  0xc800-0xc807]
[    0.257485] pci 0000:00:1f.2: reg 1c: [io  0xc480-0xc483]
[    0.257497] pci 0000:00:1f.2: reg 20: [io  0xc400-0xc40f]
[    0.257508] pci 0000:00:1f.2: reg 24: [io  0xc080-0xc08f]
[    0.257613] pci 0000:00:1f.5: reg 10: [io  0xbc00-0xbc07]
[    0.257624] pci 0000:00:1f.5: reg 14: [io  0xb880-0xb883]
[    0.257636] pci 0000:00:1f.5: reg 18: [io  0xb800-0xb807]
[    0.257647] pci 0000:00:1f.5: reg 1c: [io  0xb480-0xb483]
[    0.257658] pci 0000:00:1f.5: reg 20: [io  0xb400-0xb40f]
[    0.257669] pci 0000:00:1f.5: reg 24: [io  0xb080-0xb08f]
[    0.257811] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.257819] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.257827] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.257840] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.258130] pci 0000:02:00.0: reg 10: [mem 0xfeafe000-0xfeafffff 64bit]
[    0.258480] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.258502] pci 0000:02:00.0: PME# disabled
[    0.258586] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.258594] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.258602] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.258614] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.258752] pci 0000:03:00.0: reg 10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.258766] pci 0000:03:00.0: reg 18: [io  0xec00-0xec7f]
[    0.258868] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.258877] pci 0000:03:00.0: PME# disabled
[    0.258914] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.258922] pci 0000:00:1c.5:   bridge window [io  0xe000-0xefff]
[    0.258930] pci 0000:00:1c.5:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.258941] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.259052] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.259060] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.259068] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.259080] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.259085] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.259089] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.259094] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.259099] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.259103] pci 0000:00:1e.0:   bridge window [mem 0xb7e00000-0xffffffff] (subtractive decode)
[    0.259140] pci_bus 0000:00: on NUMA node 0
[    0.259150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.259616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.259771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.259931] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.260072] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.308450] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.308730] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.309001] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.309271] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
[    0.309543] ACPI: PCI Interrupt Link [LNKE] (IRQs 6) *0, disabled.
[    0.309814] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    0.310088] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    0.310363] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.310478] HEST: Table is not found!
[    0.310593] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.310620] vgaarb: loaded
[    0.310887] SCSI subsystem initialized
[    0.312056] libata version 3.00 loaded.
[    0.312109] usbcore: registered new interface driver usbfs
[    0.312109] usbcore: registered new interface driver hub
[    0.312109] usbcore: registered new device driver usb
[    0.312318] ACPI: WMI: Mapper loaded
[    0.312322] PCI: Using ACPI for IRQ routing
[    0.312328] PCI: pci_cache_line_size set to 64 bytes
[    0.312525] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.312530] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.312682] NetLabel: Initializing
[    0.312685] NetLabel:  domain hash size = 128
[    0.312688] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.312707] NetLabel:  unlabeled traffic allowed by default
[    0.312757] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.312768] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.312777] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.320041] Switching to clocksource tsc
[    0.338176] AppArmor: AppArmor Filesystem Enabled
[    0.338198] pnp: PnP ACPI init
[    0.338233] ACPI: bus type pnp registered
[    0.343320] pnp: PnP ACPI: found 15 devices
[    0.343325] ACPI: ACPI bus type pnp unregistered
[    0.343330] PnPBIOS: Disabled by ACPI PNP
[    0.343350] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.343366] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.343371] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.343376] system 00:08: [io  0x0400-0x041f] has been reserved
[    0.343381] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.343387] system 00:08: [mem 0xfe9fb400-0xfe9fb4ff window] has been reserved
[    0.343393] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.343398] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.343403] system 00:08: [mem 0xfed45000-0xfed89fff] has been reserved
[    0.343408] system 00:08: [mem 0xfed90000-0xfed90fff] has been reserved
[    0.343413] system 00:08: [mem 0xfed91000-0xfed91fff] has been reserved
[    0.343419] system 00:08: [mem 0xfed92000-0xfed92fff] has been reserved
[    0.343424] system 00:08: [mem 0xfed93000-0xfed93fff] has been reserved
[    0.343429] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.343434] system 00:08: [mem 0xfff00000-0xffffffff] has been reserved
[    0.343445] system 00:0a: [mem 0xffa00000-0xffbfffff] could not be reserved
[    0.343450] system 00:0a: [mem 0xffe00000-0xffffffff] could not be reserved
[    0.343460] system 00:0b: [mem 0xffc00000-0xffdfffff] has been reserved
[    0.343469] system 00:0c: [io  0x0250-0x0253] has been reserved
[    0.343474] system 00:0c: [io  0x0256-0x025f] has been reserved
[    0.343479] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.343484] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.343489] system 00:0c: [mem 0xfec18000-0xfec1ffff] has been reserved
[    0.343494] system 00:0c: [mem 0xfec38000-0xfec3ffff] has been reserved
[    0.343503] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.343518] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.343523] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.343528] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.343533] system 00:0e: [mem 0x00100000-0xb7dfffff] could not be reserved
[    0.380689] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.380694] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.380704] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.380711] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.380722] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.380725] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.380735] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.380742] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.380754] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.380760] pci 0000:00:1c.5:   bridge window [io  0xe000-0xefff]
[    0.380769] pci 0000:00:1c.5:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.380776] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    0.380788] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.380791] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.380799] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.380806] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.380834]   alloc irq_desc for 16 on node -1
[    0.380837]   alloc kstat_irqs on node -1
[    0.380848] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.380857] pci 0000:00:1c.0: setting latency timer to 64
[    0.380877]   alloc irq_desc for 17 on node -1
[    0.380880]   alloc kstat_irqs on node -1
[    0.380887] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.380894] pci 0000:00:1c.1: setting latency timer to 64
[    0.380911] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.380918] pci 0000:00:1c.5: setting latency timer to 64
[    0.380932] pci 0000:00:1e.0: setting latency timer to 64
[    0.380941] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.380945] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.380949] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.380953] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.380957] pci_bus 0000:00: resource 8 [mem 0xb7e00000-0xffffffff]
[    0.380962] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.380966] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.380970] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.380974] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.380978] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.380982] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.380986] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.380990] pci_bus 0000:04: resource 8 [mem 0xb7e00000-0xffffffff]
[    0.381048] NET: Registered protocol family 2
[    0.381149] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.381536] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.382095] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.382361] TCP: Hash tables configured (established 131072 bind 65536)
[    0.382365] TCP reno registered
[    0.382370] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.382382] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.382495] NET: Registered protocol family 1
[    0.382517] pci 0000:00:02.0: Boot video device
[    0.382762] PCI: CLS 32 bytes, default 64
[    0.382794] Simple Boot Flag at 0x51 set to 0x1
[    0.383056] cpufreq-nforce2: No nForce2 chipset.
[    0.383102] Scanning for low memory corruption every 60 seconds
[    0.383271] audit: initializing netlink socket (disabled)
[    0.383284] type=2000 audit(1290843765.376:1): initialized
[    0.402584] highmem bounce pool size: 64 pages
[    0.402592] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.405102] VFS: Disk quotas dquot_6.5.2
[    0.405210] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.406220] fuse init (API version 7.14)
[    0.406370] msgmni has been set to 1612
[    0.406784] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.406789] io scheduler noop registered
[    0.406792] io scheduler deadline registered
[    0.406814] io scheduler cfq registered (default)
[    0.406998] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.407062]   alloc irq_desc for 40 on node -1
[    0.407066]   alloc kstat_irqs on node -1
[    0.407082] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.407215] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.407277]   alloc irq_desc for 41 on node -1
[    0.407280]   alloc kstat_irqs on node -1
[    0.407293] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.407419] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.407480]   alloc irq_desc for 42 on node -1
[    0.407484]   alloc kstat_irqs on node -1
[    0.407496] pcieport 0000:00:1c.5: irq 42 for MSI/MSI-X
[    0.407654] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.407693] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.407863] intel_idle: MWAIT substates: 0x3122220
[    0.407867] intel_idle: does not run on family 6 model 23
[    0.408164] ACPI: AC Adapter [AC0] (on-line)
[    0.408303] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.408319] ACPI: Sleep Button [SLPB]
[    0.408396] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.409782] ACPI: Lid Switch [LID]
[    0.409909] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.409915] ACPI: Power Button [PWRF]
[    0.410712] ACPI: acpi_idle registered with cpuidle
[    0.411866] Monitor-Mwait will be used to enter C-1 state
[    0.411943] Monitor-Mwait will be used to enter C-3 state
[    0.411960] Marking TSC unstable due to TSC halts in idle
[    0.413306] Switching to clocksource hpet
[    0.432480] thermal LNXTHERM:01: registered as thermal_zone0
[    0.432495] ACPI: Thermal Zone [THRM] (30 C)
[    0.432683] ERST: Table is not found!
[    0.433107] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.435821] brd: module loaded
[    0.436785] loop: module loaded
[    0.437122] ata_piix 0000:00:1f.2: version 2.13
[    0.437147]   alloc irq_desc for 19 on node -1
[    0.437151]   alloc kstat_irqs on node -1
[    0.437161] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.437170] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.437239] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.441094] isapnp: Scanning for PnP cards...
[    0.460378] scsi0 : ata_piix
[    0.491123] scsi1 : ata_piix
[    0.493626] ata1: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
[    0.493635] ata2: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
[    0.493720] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.493729] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.493781] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    0.493801] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.502576] scsi2 : ata_piix
[    0.507548] scsi3 : ata_piix
[    0.507616] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
[    0.507621] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
[    0.508253] Fixed MDIO Bus: probed
[    0.508311] PPP generic driver version 2.4.2
[    0.508391] tun: Universal TUN/TAP device driver, 1.6
[    0.508395] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.508542] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.508571]   alloc irq_desc for 18 on node -1
[    0.508575]   alloc kstat_irqs on node -1
[    0.508585] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.508610] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.508616] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.508670] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.508709] ehci_hcd 0000:00:1a.7: debug port 1
[    0.512590] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.512661] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9fbc00
[    0.518132] ACPI: Battery Slot [BAT0] (battery present)
[    0.528087] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.528282] hub 1-0:1.0: USB hub found
[    0.528290] hub 1-0:1.0: 4 ports detected
[    0.528405]   alloc irq_desc for 23 on node -1
[    0.528409]   alloc kstat_irqs on node -1
[    0.528417] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.528437] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.528443] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.528501] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.528540] ehci_hcd 0000:00:1d.7: debug port 1
[    0.532427] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.532450] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9fb800
[    0.556022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.556210] hub 2-0:1.0: USB hub found
[    0.556217] hub 2-0:1.0: 8 ports detected
[    0.556349] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.556376] uhci_hcd: USB Universal Host Controller Interface driver
[    0.556425] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.556437] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.556445] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.556503] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.556551] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d880
[    0.556738] hub 3-0:1.0: USB hub found
[    0.556745] hub 3-0:1.0: 2 ports detected
[    0.556844]   alloc irq_desc for 21 on node -1
[    0.556848]   alloc kstat_irqs on node -1
[    0.556857] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.556866] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.556872] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.556926] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.556970] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d800
[    0.557166] hub 4-0:1.0: USB hub found
[    0.557173] hub 4-0:1.0: 2 ports detected
[    0.557276] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.557286] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.557291] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.557346] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.557378] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d480
[    0.557569] hub 5-0:1.0: USB hub found
[    0.557576] hub 5-0:1.0: 2 ports detected
[    0.557676] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.557686] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.557691] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.557747] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.557779] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d400
[    0.557969] hub 6-0:1.0: USB hub found
[    0.557976] hub 6-0:1.0: 2 ports detected
[    0.558074] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.558084] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.558089] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.558142] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.558175] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d080
[    0.558364] hub 7-0:1.0: USB hub found
[    0.558371] hub 7-0:1.0: 2 ports detected
[    0.558472] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.558482] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.558487] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.558540] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.558572] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d000
[    0.558764] hub 8-0:1.0: USB hub found
[    0.558771] hub 8-0:1.0: 2 ports detected
[    0.559010] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.562239] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.572233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.572244] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.572250] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.572255] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.572260] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.572374] mice: PS/2 mouse device common for all mice
[    0.572604] rtc_cmos 00:03: RTC can wake from S4
[    0.572665] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.572703] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.572883] device-mapper: uevent: version 1.0.3
[    0.573054] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.588473] device-mapper: multipath: version 1.1.1 loaded
[    0.588478] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.592926] EISA: Probing bus 0 at eisa.0
[    0.592931] EISA: Cannot allocate resource for mainboard
[    0.592935] Cannot allocate resource for EISA slot 1
[    0.592939] Cannot allocate resource for EISA slot 2
[    0.592942] Cannot allocate resource for EISA slot 3
[    0.592946] Cannot allocate resource for EISA slot 4
[    0.592949] Cannot allocate resource for EISA slot 5
[    0.592952] Cannot allocate resource for EISA slot 6
[    0.592956] Cannot allocate resource for EISA slot 7
[    0.592959] Cannot allocate resource for EISA slot 8
[    0.592962] EISA: Detected 0 cards.
[    0.612132] cpuidle: using governor ladder
[    0.612272] cpuidle: using governor menu
[    0.612816] TCP cubic registered
[    0.613042] NET: Registered protocol family 10
[    0.613658] lo: Disabled Privacy Extensions
[    0.614067] NET: Registered protocol family 17
[    0.615429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.615752] Using IPI No-Shortcut mode
[    0.615870] PM: Resume from disk failed.
[    0.615885] registered taskstats version 1
[    0.616356]   Magic number: 2:485:724
[    0.616375] block loop4: hash matches
[    0.616473] rtc_cmos 00:03: setting system clock to 2010-11-27 07:42:46 UTC (1290843766)
[    0.616478] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.616480] EDD information not available.
[    0.684689] Freeing initrd memory: 10480k freed
[    0.796357] isapnp: No Plug & Play device found
[    0.836065] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.996095] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.054369] ata1.00: ATA-8: ST9500325AS, 0002SDM1, max UDMA/133
[    1.054375] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.068690] ata1.00: configured for UDMA/133
[    1.068920] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0002 PQ: 0 ANSI: 5
[    1.069129] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.069144] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.069214] sd 0:0:0:0: [sda] Write Protect is off
[    1.069218] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.069294] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.069661]  sda: sda1 sda2 < sda5 sda6 sda7
[    1.124077] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.132096] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.137137]  sda8
[    1.141233] ata2.00: ATAPI: HL-DT-ST DVDRAM GU10N, MR03, max UDMA/133
[    1.151167]  sda9 >
[    1.151946] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.157268] ata2.00: configured for UDMA/133
[    1.162775] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GU10N     MR03 PQ: 0 ANSI: 5
[    1.174293] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.174298] Uniform CD-ROM driver Revision: 3.20
[    1.174423] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.174495] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.174600] Freeing unused kernel memory: 704k freed
[    1.175179] Write protecting the kernel text: 5088k
[    1.175337] Write protecting the kernel read-only data: 2020k
[    1.201538] udev[88]: starting version 163
[    1.345547] atl1c 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.345565] atl1c 0000:03:00.0: setting latency timer to 64
[    1.417583] Initializing USB Mass Storage driver...
[    1.458305] scsi4 : usb-storage 2-6:1.0
[    1.458562] usbcore: registered new interface driver usb-storage
[    1.458566] USB Mass Storage support registered.
[    1.462084] atl1c 0000:03:00.0: version 1.0.0.2-NAPI
[    1.632063] usb 8-1: new full speed USB device using uhci_hcd and address 2
[    2.468924] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.584948] scsi 4:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[    2.585851] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.964154] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   23.179276] udev[411]: starting version 163
[   23.226635] lp: driver loaded but no devices found
[   23.267942] Adding 4883724k swap on /dev/sda9.  Priority:-1 extents:1 across:4883724k 
[   23.411007] asus_laptop: Asus Laptop Support version 0.42
[   23.588031] asus_laptop:   UL80AG model detected
[   23.589287] asus_laptop: Backlight controlled by ACPI video driver
[   23.589369] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input4
[   23.628054] Linux agpgart interface v0.103
[   23.730268] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[   23.732147] agpgart-intel 0000:00:00.0: detected 131068K stolen memory, trimming to 32768K
[   23.735246] Linux video capture interface: v2.00
[   23.779706] Bluetooth: Core ver 2.15
[   23.779771] NET: Registered protocol family 31
[   23.779774] Bluetooth: HCI device and connection manager initialized
[   23.779777] Bluetooth: HCI socket layer initialized
[   23.788104] uvcvideo: Found UVC 1.00 device USB 2.0 UVC 0.3M Webcam (064e:a136)
[   23.788193] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   23.797507] cfg80211: Calling CRDA to update world regulatory domain
[   23.810784] usbcore: registered new interface driver btusb
[   23.821339] input: USB 2.0 UVC 0.3M Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input5
[   23.821429] usbcore: registered new interface driver uvcvideo
[   23.821433] USB Video Class driver (v0.1.0)
[   23.850097] cfg80211: World regulatory domain updated:
[   23.850102]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.850107]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.850111]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.850115]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.850119]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.850123]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.914140] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   23.966213] type=1400 audit(1290861789.843:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=762 comm="apparmor_parser"
[   23.967325] type=1400 audit(1290861789.843:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=762 comm="apparmor_parser"
[   23.967932] type=1400 audit(1290861789.843:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=762 comm="apparmor_parser"
[   24.008151] psmouse serio4: ID: 10 00 64
[   24.008738] [drm] Initialized drm 1.1.0 20060810
[   24.057398] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   24.057403] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   24.057526] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.057566] iwlagn 0000:02:00.0: setting latency timer to 64
[   24.057633] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   24.087169] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   24.087376]   alloc irq_desc for 43 on node -1
[   24.087380]   alloc kstat_irqs on node -1
[   24.087433] iwlagn 0000:02:00.0: irq 43 for MSI/MSI-X
[   24.102472] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.102480] i915 0000:00:02.0: setting latency timer to 64
[   24.105086] elantech: assuming hardware version 2, firmware version 4.1.1
[   24.132127] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
[   24.137142] elantech: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
[   24.159035] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   24.159041] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   24.159047] [drm] detected 127M stolen memory, trimming to 32M
[   24.161166]   alloc irq_desc for 44 on node -1
[   24.161170]   alloc kstat_irqs on node -1
[   24.161184] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   24.161200] [drm] set up 32M of stolen space
[   24.161393] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[   24.161449] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[   24.185418] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   24.218750] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input6
[   24.300368] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   24.612113] Skipping EDID probe due to cached edid
[   24.980419] Console: switching to colour frame buffer device 170x48
[   24.986623] fb0: inteldrmfb frame buffer device
[   24.986626] drm: registered panic notifier
[   24.986637] Slow work thread pool: Starting up
[   24.986721] Slow work thread pool: Ready
[   24.994634] acpi device:3b: registered as cooling_device2
[   24.995700] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   24.995872] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.996270] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.996326]   alloc irq_desc for 22 on node -1
[   24.996330]   alloc kstat_irqs on node -1
[   24.996339] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.996402]   alloc irq_desc for 45 on node -1
[   24.996405]   alloc kstat_irqs on node -1
[   24.996420] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   24.996462] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.096039] Skipping EDID probe due to cached edid
[   26.505174] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   27.585521] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   31.352627] type=1400 audit(1290861797.231:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1165 comm="apparmor_parser"
[   31.352929] type=1400 audit(1290861797.231:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1166 comm="apparmor_parser"
[   31.354065] type=1400 audit(1290861797.231:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1166 comm="apparmor_parser"
[   31.354948] type=1400 audit(1290861797.231:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1166 comm="apparmor_parser"
[   31.363360] type=1400 audit(1290861797.239:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1171 comm="apparmor_parser"
[   31.365895] type=1400 audit(1290861797.243:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1167 comm="apparmor_parser"
[   31.370086] type=1400 audit(1290861797.247:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1171 comm="apparmor_parser"
[   31.374970] type=1400 audit(1290861797.251:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1173 comm="apparmor_parser"
[   31.377897] ppdev: user-space parallel port driver
[   31.382588] type=1400 audit(1290861797.259:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1167 comm="apparmor_parser"
[   31.385481] type=1400 audit(1290861797.263:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1175 comm="apparmor_parser"
[   31.557990] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.571350]   alloc irq_desc for 46 on node -1
[   31.571357]   alloc kstat_irqs on node -1
[   31.571379] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[   31.571952] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.841131] Skipping EDID probe due to cached edid
[   31.877216] Skipping EDID probe due to cached edid
[   32.788716] wlan0: authenticate with 94:44:52:74:95:82 (try 1)
[   32.791740] wlan0: authenticated
[   32.791793] wlan0: associate with 94:44:52:74:95:82 (try 1)
[   32.794570] wlan0: RX AssocResp from 94:44:52:74:95:82 (capab=0x411 status=0 aid=1)
[   32.794575] wlan0: associated
[   32.799934] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.839821] padlock: VIA PadLock not detected.
[   34.824405] Skipping EDID probe due to cached edid
[   34.856188] Skipping EDID probe due to cached edid
[   34.892060] Skipping EDID probe due to cached edid
[   36.260173] Skipping EDID probe due to cached edid
[   36.417378] Bluetooth: L2CAP ver 2.14
[   36.417383] Bluetooth: L2CAP socket layer initialized
[   36.477171] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.477177] Bluetooth: BNEP filters: protocol multicast
[   36.521060] Bluetooth: SCO (Voice Link) ver 0.6
[   36.521064] Bluetooth: SCO socket layer initialized
[   36.736757] Bluetooth: RFCOMM TTY layer initialized
[   36.736765] Bluetooth: RFCOMM socket layer initialized
[   36.736770] Bluetooth: RFCOMM ver 1.11
[   40.409061] Skipping EDID probe due to cached edid
[   41.511410] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   42.198105] EXT4-fs (sda8): re-mounted. Opts: commit=0
[   43.040018] wlan0: no IPv6 routers present
[   52.356822] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[   52.396130] Skipping EDID probe due to cached edid
[  189.536111] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1904.337085] Skipping EDID probe due to cached edid
```

---

### Post by &lt;mike&gt; on 2010-12-29
Hi.
Mine's slower again
```

...

[    2.715618] Uniform CD-ROM driver Revision: 3.20
[    2.715783] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.715871] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.715981] ata4: port disabled. ignoring.
[    3.528234] kjournald starting.  Commit interval 5 seconds
[    3.528254] EXT3-fs: mounted filesystem with ordered data mode.
[   50.620215] udev: starting version 151
[   50.829441] lp: driver loaded but no devices found
[   50.917913] acpi device:22: registered as cooling_device2
[   50.918114] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   50.918191] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   51.019969] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   51.061798] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   51.061828] i2c i2c-1: nForce2 SMBus adapter at 0x3000

```

Any ideas?? Full dmesg output attached.

---

### Post by ruben_linux on 2010-12-29
in my dmseg.log

[    0.929955] udev: starting version 151

but im usig ubuntu 10.04lts 2.6.32-24-generic

did you apdate your SO?

---

### Post by proycon on 2011-01-01
I have the same problem and no idea what's causing the delay. I don't know if it's got something to do with udev, but that's the first message that appears after a long 20+ sec wait in which I see only a blinking cursor in the left-top of my screen. This all happens before even plymouth shows. 

I'm running Ubuntu Maverick 10.10 on a Macbook Pro 5,3 with nvidia card.

```

Jan  1 23:30:17 aurora kernel: [    2.158643] Console: switching to colour frame buffer device 180x56
Jan  1 23:30:17 aurora kernel: [    2.162236] uvesafb: framebuffer at 0xe3000000, mapped to 0xffffc90
005100000, using 10125k, total 14336k
Jan  1 23:30:17 aurora kernel: [    2.162238] fb0: VESA VGA frame buffer device
Jan  1 23:30:17 aurora kernel: [    2.189071] hub 4-1:1.0: USB hub found
Jan  1 23:30:17 aurora kernel: [    2.192034] hub 4-1:1.0: 3 ports detected
Jan  1 23:30:17 aurora kernel: [    2.218261] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
Jan  1 23:30:17 aurora kernel: [    2.550033] usb 3-5: new low speed USB device using ohci_hcd and address 2
Jan  1 23:30:17 aurora kernel: [    2.622319] scsi 6:0:0:0: Direct-Access     APPLE    SD Card Reader   1.00 PQ: 0 ANSI: 0
Jan  1 23:30:17 aurora kernel: [    2.622843] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jan  1 23:30:17 aurora kernel: [    2.624154] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jan  1 23:30:17 aurora kernel: [    3.120097] usb 3-6: new full speed USB device using ohci_hcd and address 3
Jan  1 23:30:17 aurora kernel: [    3.452108] usb 4-1.1: new full speed USB device using ohci_hcd and address 3
Jan  1 23:30:17 aurora kernel: [   26.522708] udev[439]: starting version 163
Jan  1 23:30:17 aurora kernel: [   26.619709] lib80211: common routines for IEEE802.11 drivers
Jan  1 23:30:17 aurora kernel: [   26.658481] wl: module license 'MIXED/Proprietary' taints kernel.
Jan  1 23:30:17 aurora kernel: [   26.658484] Disabling lock debugging due to kernel taint
Jan  1 23:30:17 aurora kernel: [   26.661957] wl 0000:04:00.0: power state changed by ACPI to D0
Jan  1 23:30:17 aurora kernel: [   26.662187] wl 0000:04:00.0: power state changed by ACPI to D0
Jan  1 23:30:17 aurora kernel: [   26.662197] wl 0000:04:00.0: PCI INT A -> Link[Z00F] -> GSI 22 (level, low) -> IRQ 22

```

---

### Post by dsjstc on 2011-01-15
Known issue.  Be sure to click "this affects me" in launchpad, so it gets attention.

---

### Post by dsjstc on 2011-01-15
Known issue.  Be sure to click "this affects me" in launchpad, so it gets attention.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395)

---

### Post by dsjstc on 2011-01-15
Known issue.  Be sure to click "this affects me" in launchpad, so it gets attention.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395)

---

### Post by dsjstc on 2011-01-15
Known issue.  Be sure to click "this affects me" in launchpad, so it gets attention.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395)

---

