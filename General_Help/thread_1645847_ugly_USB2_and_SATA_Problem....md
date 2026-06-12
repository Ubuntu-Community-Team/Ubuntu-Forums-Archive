---
title: "ugly USB2 and SATA Problem..."
date: 2010-12-15
forum: General Help
---

### Post by ansi_lady on 2010-12-15
Hi there,
i just bought a new Mainboard for my MediaCenter, its a 
ASUS AT5NM10-I with DualCore Intel-Atom.

To run this Board as a Router i added a Davicom DM9601 USB-NIC (10/100) and for my Files i added a VT6421 IDE/SATA PCI-RAID-Controller-Card.

I already tried Ubuntu 10.10 and i compiled the newest Kernel too, ... 
now iam back on Lucid but i cant solve my Problems...

my external USB-Ports are all 1.1 (damn).
my PCI SATA-Controller cant enable 32Bit mode (doubledamn), but the onboard SATA provides 32Bit mode and have it enabled by automatic...

OK, there are 2 Problems, but i think they have all the same source... ?

```

root@execute:~# uname -a
Linux execute 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux

```dmesg :
```

root@execute:~# dmesg | grep usb
[    0.433711] usbcore: registered new interface driver usbfs
[    0.433711] usbcore: registered new interface driver hub
[    0.433711] usbcore: registered new device driver usb
[    1.145308] usb 3-1: new full speed USB device using uhci_hcd and address 2

``````

root@execute:~# dmesg | grep sata
[    1.144638] sata_via 0000:01:00.0: version 2.6
[    1.144673] sata_via 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.144751] sata_via 0000:01:00.0: routed to hard irq line 10
[    1.144956] scsi0 : sata_via
[    1.145352] scsi1 : sata_via
[    1.145567] scsi2 : sata_via

```

```

root@execute:/# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic-pae (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 (Ubuntu 2.6.35-22.35-generic-pae 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6a0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6a0000 - 000000007f6ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f6ae000 - 000000007f6e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e0000 - 000000007f700000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f6a0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6a0000 (usable)
[    0.000000]  modified: 000000007f6a0000 - 000000007f6ae000 (ACPI data)
[    0.000000]  modified: 000000007f6ae000 - 000000007f6e0000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e0000 - 000000007f700000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 375b4000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a02000 - 0143d4d9
[    0.000000] Move RAMDISK from 00000000375b4000 - 0000000037fef4d8 to 00a02000 - 0143d4d8
[    0.000000] ACPI: RSDP 000fb360 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7f6a0100 00054 (v01 120109 XSDT2200 20091201 MSFT 00000097)
[    0.000000] ACPI: FACP 7f6a0290 000F4 (v03 120109 FACP2200 20091201 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f6a0440 06D41 (v01  A1413 A1413000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 7f6ae000 00040
[    0.000000] ACPI: APIC 7f6a0390 0006C (v01 120109 APIC2200 20091201 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f6a0400 0003C (v01 120109 OEMMCFG  20091201 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f6ae040 00072 (v01 120109 OEMB2200 20091201 MSFT 00000097)
[    0.000000] ACPI: HPET 7f6aa440 00038 (v01 120109 OEMHPET  20091201 MSFT 00000097)
[    0.000000] ACPI: GSCI 7f6ae0c0 02024 (v01 120109 GMCHSCI  20091201 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1146MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007f6a0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6a0
[    0.000000] On node 0 totalpages: 521775
[    0.000000] free_area_init_node: node 0, pgdat c083ea40, node_mem_map c143f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2294 pages used for memmap
[    0.000000]   HighMem zone: 291244 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f700000 (gap: 7f700000:7f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c2600000 s39872 r0 d21568 u524288
[    0.000000] pcpu-alloc: s39872 r0 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517697
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=8b12b1e9-36db-44db-8e90-48a335aff600 ro quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10437440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009f965c]   TEXT DATA BSS
[    0.000000]   #3 [00009fa000 - 0000a01227]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009fc00 - 00000f0ef0]   BIOS reserved
[    0.000000]   #7 [00000f1034 - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000f0ef0 - 00000f1034]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [0000a02000 - 000143e000]     NEW RAMDISK
[    0.000000]   #13 [000143e000 - 000143f000]         BOOTMEM
[    0.000000]   #14 [000143f000 - 000242f000]         BOOTMEM
[    0.000000]   #15 [000242f000 - 000242f004]         BOOTMEM
[    0.000000]   #16 [000242f040 - 000242f100]         BOOTMEM
[    0.000000]   #17 [000242f100 - 000242f1a8]         BOOTMEM
[    0.000000]   #18 [000242f1c0 - 00024321c0]         BOOTMEM
[    0.000000]   #19 [00024321c0 - 0002432298]         BOOTMEM
[    0.000000]   #20 [00024322c0 - 00024382c0]         BOOTMEM
[    0.000000]   #21 [00024382c0 - 00024382ed]         BOOTMEM
[    0.000000]   #22 [0002438300 - 000243832f]         BOOTMEM
[    0.000000]   #23 [0002438340 - 00024384a8]         BOOTMEM
[    0.000000]   #24 [00024384c0 - 0002438500]         BOOTMEM
[    0.000000]   #25 [0002438500 - 0002438540]         BOOTMEM
[    0.000000]   #26 [0002438540 - 0002438580]         BOOTMEM
[    0.000000]   #27 [0002438580 - 00024385c0]         BOOTMEM
[    0.000000]   #28 [00024385c0 - 0002438600]         BOOTMEM
[    0.000000]   #29 [0002438600 - 0002438640]         BOOTMEM
[    0.000000]   #30 [0002438640 - 0002438680]         BOOTMEM
[    0.000000]   #31 [0002438680 - 00024386c0]         BOOTMEM
[    0.000000]   #32 [00024386c0 - 0002438700]         BOOTMEM
[    0.000000]   #33 [0002438700 - 0002438710]         BOOTMEM
[    0.000000]   #34 [0002438740 - 00024387a7]         BOOTMEM
[    0.000000]   #35 [00024387c0 - 0002438827]         BOOTMEM
[    0.000000]   #36 [0002600000 - 000260f000]         BOOTMEM
[    0.000000]   #37 [0002680000 - 000268f000]         BOOTMEM
[    0.000000]   #38 [0002700000 - 000270f000]         BOOTMEM
[    0.000000]   #39 [0002780000 - 000278f000]         BOOTMEM
[    0.000000]   #40 [000243a840 - 000243a844]         BOOTMEM
[    0.000000]   #41 [000243a880 - 000243a884]         BOOTMEM
[    0.000000]   #42 [000243a8c0 - 000243a8d0]         BOOTMEM
[    0.000000]   #43 [000243a900 - 000243a910]         BOOTMEM
[    0.000000]   #44 [000243a940 - 000243a9d8]         BOOTMEM
[    0.000000]   #45 [000243aa00 - 000243aa38]         BOOTMEM
[    0.000000]   #46 [000243aa40 - 000243ea40]         BOOTMEM
[    0.000000]   #47 [000243ea40 - 00024bea40]         BOOTMEM
[    0.000000]   #48 [00024bea40 - 00024fea40]         BOOTMEM
[    0.000000]   #49 [000278f000 - 0003183340]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007f6a0)
[    0.000000] Memory: 2039784k/2087552k available (5085k kernel code, 47316k reserved, 2432k data, 704k init, 1174152k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc0858000 - 0xc0908000   ( 704 kB)
[    0.000000]       .data : 0xc05f750a - 0xc0857768   (2432 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f750a   (5085 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1682.160 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3364.32 BogoMIPS (lpj=6728640)
[    0.004020] pid_max: default: 32768 minimum: 301
[    0.004056] Security Framework initialized
[    0.004090] AppArmor: AppArmor initialized
[    0.004095] Yama: becoming mindful.
[    0.004215] Mount-cache hash table entries: 512
[    0.004451] Initializing cgroup subsys ns
[    0.004461] Initializing cgroup subsys cpuacct
[    0.004472] Initializing cgroup subsys memory
[    0.004490] Initializing cgroup subsys devices
[    0.004496] Initializing cgroup subsys freezer
[    0.004501] Initializing cgroup subsys net_cls
[    0.004551] CPU: Physical Processor ID: 0
[    0.004556] CPU: Processor Core ID: 0
[    0.004562] mce: CPU supports 5 MCE banks
[    0.004574] CPU0: Thermal monitoring enabled (TM1)
[    0.004583] using mwait in idle threads.
[    0.004596] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.004609] ... version:                3
[    0.004614] ... bit width:              40
[    0.004619] ... generic registers:      2
[    0.004623] ... value mask:             000000ffffffffff
[    0.004628] ... max period:             000000007fffffff
[    0.004633] ... fixed-purpose events:   3
[    0.004638] ... event mask:             0000000700000003
[    0.011045] ACPI: Core revision 20100428
[    0.024018] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024028] ftrace: allocating 22394 entries in 44 pages
[    0.028094] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028430] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068563] CPU0: Intel(R) Atom(TM) CPU D510   @ 1.66GHz stepping 0a
[    0.072000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.160155]  #2
[    0.008000] Initializing CPU#2
[    0.252202]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.344000] TSC synchronization [CPU#0 -> CPU#3]:
[    0.344000] Measured 10 cycles TSC warp between CPUs, turning off TSC clock.
[    0.344000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.344017] Brought up 4 CPUs
[    0.344023] Total of 4 processors activated (13458.70 BogoMIPS).
[    0.345670] devtmpfs: initialized
[    0.349112] regulator: core version 0.5
[    0.349144] Time:  9:06:32  Date: 12/15/10
[    0.349222] NET: Registered protocol family 16
[    0.349246] Trying to unpack rootfs image as initramfs...
[    0.349486] EISA bus registered
[    0.349507] ACPI: bus type pci registered
[    0.349650] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.349657] PCI: not using MMCONFIG
[    0.349879] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.349884] PCI: Using configuration type 1 for base access
[    0.352051] bio: create slab <bio-0> at 0
[    0.354574] ACPI: EC: Look up EC in DSDT
[    0.360205] ACPI: Executed 1 blocks of module-level executable AML code
[    0.372760] ACPI: Interpreter enabled
[    0.372769] ACPI: (supports S0 S3 S4 S5)
[    0.372813] ACPI: Using IOAPIC for interrupt routing
[    0.372913] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.380247] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.380254] PCI: Using MMCONFIG for extended config space
[    0.403357] ACPI Warning: Incorrect checksum in table [OEMB] - 0x71, should be 0x6A (20100428/tbutils-314)
[    0.404511] ACPI: No dock devices found.
[    0.404521] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.404837] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.405486] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.405494] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.405501] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.405508] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.405515] pci_root PNP0A08:00: host bridge window [mem 0x7f700000-0xdfffffff]
[    0.405522] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.405611] pci 0000:00:02.0: reg 10: [mem 0xfbc80000-0xfbcfffff]
[    0.405620] pci 0000:00:02.0: reg 14: [io  0xb800-0xb807]
[    0.405628] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.405636] pci 0000:00:02.0: reg 1c: [mem 0xfbb00000-0xfbbfffff]
[    0.405683] pci 0000:00:02.1: reg 10: [mem 0xfbd00000-0xfbd7ffff]
[    0.405775] pci 0000:00:1b.0: reg 10: [mem 0xfbdf8000-0xfbdfbfff 64bit]
[    0.405823] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.405830] pci 0000:00:1b.0: PME# disabled
[    0.405906] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.405913] pci 0000:00:1c.0: PME# disabled
[    0.405990] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.405997] pci 0000:00:1c.1: PME# disabled
[    0.406053] pci 0000:00:1d.0: reg 20: [io  0xb880-0xb89f]
[    0.406110] pci 0000:00:1d.1: reg 20: [io  0xbc00-0xbc1f]
[    0.406167] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.406224] pci 0000:00:1d.3: reg 20: [io  0xc080-0xc09f]
[    0.406282] pci 0000:00:1d.7: reg 10: [mem 0xfbdff800-0xfbdffbff]
[    0.406337] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.406345] pci 0000:00:1d.7: PME# disabled
[    0.406524] pci 0000:00:1f.2: reg 10: [io  0xcc00-0xcc07]
[    0.406533] pci 0000:00:1f.2: reg 14: [io  0xc880-0xc883]
[    0.406543] pci 0000:00:1f.2: reg 18: [io  0xc800-0xc807]
[    0.406552] pci 0000:00:1f.2: reg 1c: [io  0xc480-0xc483]
[    0.406561] pci 0000:00:1f.2: reg 20: [io  0xc400-0xc41f]
[    0.406570] pci 0000:00:1f.2: reg 24: [mem 0xfbdffc00-0xfbdfffff]
[    0.406603] pci 0000:00:1f.2: PME# supported from D3hot
[    0.406609] pci 0000:00:1f.2: PME# disabled
[    0.406664] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.406740] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.406748] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.406757] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.406766] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.406847] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.406871] pci 0000:02:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
[    0.406891] pci 0000:02:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
[    0.406904] pci 0000:02:00.0: reg 30: [mem 0xfbff0000-0xfbffffff pref]
[    0.406948] pci 0000:02:00.0: supports D1 D2
[    0.406953] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.406961] pci 0000:02:00.0: PME# disabled
[    0.412032] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.412041] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.412049] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.412059] pci 0000:00:1c.1:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.412122] pci 0000:01:00.0: reg 10: [io  0xdc00-0xdc0f]
[    0.412132] pci 0000:01:00.0: reg 14: [io  0xd880-0xd88f]
[    0.412143] pci 0000:01:00.0: reg 18: [io  0xd800-0xd80f]
[    0.412153] pci 0000:01:00.0: reg 1c: [io  0xd480-0xd48f]
[    0.412163] pci 0000:01:00.0: reg 20: [io  0xd400-0xd41f]
[    0.412174] pci 0000:01:00.0: reg 24: [io  0xd000-0xd0ff]
[    0.412185] pci 0000:01:00.0: reg 30: [mem 0xfbef0000-0xfbefffff pref]
[    0.412257] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.412265] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.412273] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.412283] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412289] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.412296] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.412302] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.412309] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.412315] pci 0000:00:1e.0:   bridge window [mem 0x7f700000-0xdfffffff] (subtractive decode)
[    0.412322] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.412342] pci_bus 0000:00: on NUMA node 0
[    0.412353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.412579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.412785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.431422] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.431646] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.431865] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 *14 15)
[    0.432108] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.432329] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.432551] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.432772] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.432993] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.433099] HEST: Table is not found!
[    0.433281] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.433302] vgaarb: loaded
[    0.433682] SCSI subsystem initialized
[    0.433711] libata version 3.00 loaded.
[    0.433711] usbcore: registered new interface driver usbfs
[    0.433711] usbcore: registered new interface driver hub
[    0.433711] usbcore: registered new device driver usb
[    0.433711] ACPI: WMI: Mapper loaded
[    0.433711] PCI: Using ACPI for IRQ routing
[    0.433711] PCI: pci_cache_line_size set to 64 bytes
[    0.433711] reserve RAM buffer: 000000000009fc00 - 000000000009ffff
[    0.433711] reserve RAM buffer: 000000007f6a0000 - 000000007fffffff
[    0.433711] NetLabel: Initializing
[    0.433711] NetLabel:  domain hash size = 128
[    0.433711] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.433711] NetLabel:  unlabeled traffic allowed by default
[    0.433711] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.433711] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.433711] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.448041] Switching to clocksource hpet
[    0.467864] AppArmor: AppArmor Filesystem Enabled
[    0.467903] pnp: PnP ACPI init
[    0.467940] ACPI: bus type pnp registered
[    0.480184] pnp: PnP ACPI: found 17 devices
[    0.480191] ACPI: ACPI bus type pnp unregistered
[    0.480198] PnPBIOS: Disabled by ACPI PNP
[    0.480226] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.480234] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.480250] system 00:06: [io  0x0a00-0x0a0f] has been reserved
[    0.480258] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.480265] system 00:06: [io  0x0a20-0x0a2f] has been reserved
[    0.480271] system 00:06: [io  0x0a30-0x0a3f] has been reserved
[    0.480285] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.480292] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.480299] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.480307] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.480314] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.480328] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.480335] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.480360] system 00:0f: [mem 0xe0000000-0xefffffff] has been reserved
[    0.480374] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.480382] system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.480389] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.480396] system 00:10: [mem 0x00100000-0x7f6fffff] could not be reserved
[    0.480404] system 00:10: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.518542] pci 0000:00:1c.0: BAR 14: assigned [mem 0x7f700000-0x7f8fffff]
[    0.518553] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.518563] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.518569] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.518576] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.518584] pci 0000:00:1c.0:   bridge window [mem 0x7f700000-0x7f8fffff]
[    0.518593] pci 0000:00:1c.0:   bridge window [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.518603] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.518609] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.518618] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.518626] pci 0000:00:1c.1:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.518636] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.518642] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.518651] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.518657] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.518677] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.518689]   alloc irq_desc for 16 on node -1
[    0.518694]   alloc kstat_irqs on node -1
[    0.518709] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.518717] pci 0000:00:1c.0: setting latency timer to 64
[    0.518731]   alloc irq_desc for 17 on node -1
[    0.518735]   alloc kstat_irqs on node -1
[    0.518744] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.518752] pci 0000:00:1c.1: setting latency timer to 64
[    0.518763] pci 0000:00:1e.0: setting latency timer to 64
[    0.518772] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.518778] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.518783] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.518789] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.518796] pci_bus 0000:00: resource 8 [mem 0x7f700000-0xdfffffff]
[    0.518802] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.518808] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.518813] pci_bus 0000:03: resource 1 [mem 0x7f700000-0x7f8fffff]
[    0.518820] pci_bus 0000:03: resource 2 [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.518826] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.518832] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.518838] pci_bus 0000:02: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.518844] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.518850] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.518856] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.518862] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.518867] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.518873] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.518879] pci_bus 0000:01: resource 8 [mem 0x7f700000-0xdfffffff]
[    0.518885] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.518953] NET: Registered protocol family 2
[    0.519094] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.519565] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.520541] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.521008] TCP: Hash tables configured (established 131072 bind 65536)
[    0.521016] TCP reno registered
[    0.521033] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.521065] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.521292] NET: Registered protocol family 1
[    0.521328] pci 0000:00:02.0: Boot video device
[    0.521473] PCI: CLS 32 bytes, default 64
[    0.522073] cpufreq-nforce2: No nForce2 chipset.
[    0.522133] Scanning for low memory corruption every 60 seconds
[    0.522374] audit: initializing netlink socket (disabled)
[    0.522395] type=2000 audit(1292403991.520:1): initialized
[    0.541698] highmem bounce pool size: 64 pages
[    0.541710] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.545130] VFS: Disk quotas dquot_6.5.2
[    0.545270] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.546622] fuse init (API version 7.14)
[    0.546849] msgmni has been set to 1690
[    0.551988] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.551997] io scheduler noop registered
[    0.552002] io scheduler deadline registered
[    0.552052] io scheduler cfq registered (default)
[    0.552267] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.552313]   alloc irq_desc for 40 on node -1
[    0.552318]   alloc kstat_irqs on node -1
[    0.552335] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.552494] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.552538]   alloc irq_desc for 41 on node -1
[    0.552543]   alloc kstat_irqs on node -1
[    0.552555] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.552755] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.552913] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.553157] intel_idle: MWAIT substates: 0x10
[    0.553162] intel_idle: v0.4 model 0x1C
[    0.553166] intel_idle: lapic_timer_reliable_states 0x6
[    0.553444] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.553455] ACPI: Power Button [PWRB]
[    0.553563] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.553572] ACPI: Power Button [PWRF]
[    0.554021] ACPI: acpi_idle yielding to intel_idle
[    0.562723] ERST: Table is not found!
[    0.562986] isapnp: Scanning for PnP cards...
[    0.563311] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.563455] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.563603] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.564198] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.564408] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.567195] brd: module loaded
[    0.568487] loop: module loaded
[    0.569898] Fixed MDIO Bus: probed
[    0.569997] PPP generic driver version 2.4.2
[    0.570094] tun: Universal TUN/TAP device driver, 1.6
[    0.570099] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.570299] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.570344]   alloc irq_desc for 23 on node -1
[    0.570349]   alloc kstat_irqs on node -1
[    0.570364] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.570398] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.570405] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.570488] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.570528] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.570543] ehci_hcd 0000:00:1d.7: debug port 1
[    0.574435] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.574468] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbdff800
[    0.589023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.589281] hub 1-0:1.0: USB hub found
[    0.589294] hub 1-0:1.0: 8 ports detected
[    0.589438] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.589474] uhci_hcd: USB Universal Host Controller Interface driver
[    0.589534] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.589548] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.589554] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.589638] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.589673] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b880
[    0.589944] hub 2-0:1.0: USB hub found
[    0.589956] hub 2-0:1.0: 2 ports detected
[    0.590068]   alloc irq_desc for 19 on node -1
[    0.590073]   alloc kstat_irqs on node -1
[    0.590087] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.590099] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.590105] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.590191] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.590238] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bc00
[    0.590512] hub 3-0:1.0: USB hub found
[    0.590523] hub 3-0:1.0: 2 ports detected
[    0.590630]   alloc irq_desc for 18 on node -1
[    0.590635]   alloc kstat_irqs on node -1
[    0.590647] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.590660] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.590666] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.590753] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.590801] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.591065] hub 4-0:1.0: USB hub found
[    0.591076] hub 4-0:1.0: 2 ports detected
[    0.591182] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.591194] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.591200] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.591292] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.591340] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c080
[    0.591598] hub 5-0:1.0: USB hub found
[    0.591609] hub 5-0:1.0: 2 ports detected
[    0.591868] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.592324] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.592344] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.592540] mice: PS/2 mouse device common for all mice
[    0.592800] rtc_cmos 00:03: RTC can wake from S4
[    0.592892] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.592927] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.593233] device-mapper: uevent: version 1.0.3
[    0.593504] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.593755] device-mapper: multipath: version 1.1.1 loaded
[    0.593763] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.594063] EISA: Probing bus 0 at eisa.0
[    0.594069] EISA: Cannot allocate resource for mainboard
[    0.594075] Cannot allocate resource for EISA slot 1
[    0.594079] Cannot allocate resource for EISA slot 2
[    0.594084] Cannot allocate resource for EISA slot 3
[    0.594088] Cannot allocate resource for EISA slot 4
[    0.594093] Cannot allocate resource for EISA slot 5
[    0.594097] Cannot allocate resource for EISA slot 6
[    0.594102] Cannot allocate resource for EISA slot 7
[    0.594106] Cannot allocate resource for EISA slot 8
[    0.594111] EISA: Detected 0 cards.
[    0.594598] cpuidle: using governor ladder
[    0.594813] cpuidle: using governor menu
[    0.595432] TCP cubic registered
[    0.595765] NET: Registered protocol family 10
[    0.596531] lo: Disabled Privacy Extensions
[    0.596993] NET: Registered protocol family 17
[    0.597127] Using IPI No-Shortcut mode
[    0.597352] PM: Resume from disk failed.
[    0.597379] registered taskstats version 1
[    0.597767]   Magic number: 6:182:121
[    0.597897] rtc_cmos 00:03: setting system clock to 2010-12-15 09:06:32 UTC (1292403992)
[    0.597904] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.597908] EDD information not available.
[    0.614097] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.870364] Freeing initrd memory: 10480k freed
[    0.916202] isapnp: No Plug & Play device found
[    0.916238] Freeing unused kernel memory: 704k freed
[    0.916835] Write protecting the kernel text: 5088k
[    0.916981] Write protecting the kernel read-only data: 2012k
[    0.955497] udev[99]: starting version 163
[    1.035910] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.035964] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.036039] r8169 0000:02:00.0: setting latency timer to 64
[    1.036099]   alloc irq_desc for 42 on node -1
[    1.036107]   alloc kstat_irqs on node -1
[    1.036133] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.037742] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf845e000, e0:cb:4e:d6:8a:14, XID 083000c0 IRQ 42
[    1.144638] sata_via 0000:01:00.0: version 2.6
[    1.144673] sata_via 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.144751] sata_via 0000:01:00.0: routed to hard irq line 10
[    1.144956] scsi0 : sata_via
[    1.145308] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.145352] scsi1 : sata_via
[    1.145567] scsi2 : sata_via
[    1.145705] ata1: SATA max UDMA/133 port i16@0xdc00 bmdma 0xd400 irq 17
[    1.145716] ata2: SATA max UDMA/133 port i16@0xd880 bmdma 0xd408 irq 17
[    1.145724] ata3: PATA max UDMA/133 port i16@0xd800 bmdma 0xd410 irq 17
[    1.148375] ahci 0000:00:1f.2: version 3.0
[    1.148404] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.148473]   alloc irq_desc for 43 on node -1
[    1.148478]   alloc kstat_irqs on node -1
[    1.148497] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.148594] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.148603] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
[    1.148611] ahci 0000:00:1f.2: setting latency timer to 64
[    1.149105] scsi3 : ahci
[    1.149347] scsi4 : ahci
[    1.149522] scsi5 : ahci
[    1.149711] scsi6 : ahci
[    1.150064] ata4: SATA max UDMA/133 abar m1024@0xfbdffc00 port 0xfbdffd00 irq 43
[    1.150072] ata5: SATA max UDMA/133 abar m1024@0xfbdffc00 port 0xfbdffd80 irq 43
[    1.150078] ata6: DUMMY
[    1.150081] ata7: DUMMY
[    1.464069] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.468033] ata5: SATA link down (SStatus 0 SControl 300)
[    1.468060] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.468719] ata4.00: ATA-7: Maxtor 7Y250M0, YAR51HW0, max UDMA/133
[    1.468728] ata4.00: 488281250 sectors, multi 0: LBA48
[    1.469556] ata4.00: configured for UDMA/133
[    1.680601] ata1.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
[    1.680609] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.688652] ata1.00: configured for UDMA/133
[    1.688914] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
[    1.689472] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.689490] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.689740] sd 0:0:0:0: [sda] Write Protect is off
[    1.689747] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.689816] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.690212]  sda: sda1
[    1.709323] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.008068] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.016408] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    2.016416] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.024454] ata2.00: configured for UDMA/133
[    2.024697] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    2.025126] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.025206] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.025327] sd 1:0:0:0: [sdb] Write Protect is off
[    2.025336] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.025429] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.025932]  sdb: sdb1 sdb2 < sdb5 >
[    2.065592] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.196447] ata3.00: CFA: SanDisk SDCFB-128, Vdg 8.21, max PIO1
[    2.196456] ata3.00: 250880 sectors, multi 0: LBA
[    2.204425] ata3.00: configured for PIO1
[    2.220422] ata3.00: configured for PIO1
[    2.220430] ata3: EH complete
[    2.220680] scsi 2:0:0:0: Direct-Access     ATA      SanDisk SDCFB-12 Vdg  PQ: 0 ANSI: 5
[    2.221090] sd 2:0:0:0: [sdc] 250880 512-byte logical blocks: (128 MB/122 MiB)
[    2.221175] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.221315] sd 2:0:0:0: [sdc] Write Protect is off
[    2.221325] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.221432] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.221569] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 7Y250M0   YAR5 PQ: 0 ANSI: 5
[    2.221914] sd 3:0:0:0: [sdd] 488281250 512-byte logical blocks: (250 GB/232 GiB)
[    2.222056] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.222136] sd 3:0:0:0: [sdd] Write Protect is off
[    2.222146] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.222208]  sdc:
[    2.222246] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.222651]  sdd: sdc1
[    2.227229] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[    2.234346]  sdd1 sdd2 < sdd5 >
[    2.255247] sd 3:0:0:0: [sdd] Attached SCSI disk
[    2.519604] EXT4-fs (sdd1): INFO: recovery required on readonly filesystem
[    2.519616] EXT4-fs (sdd1): write access will be enabled during recovery
[    4.642977] EXT4-fs (sdd1): orphan cleanup on readonly fs
[    4.643000] EXT4-fs (sdd1): ext4_orphan_cleanup: deleting unreferenced inode 8126476
[    4.643064] EXT4-fs (sdd1): ext4_orphan_cleanup: deleting unreferenced inode 8126475
[    4.643087] EXT4-fs (sdd1): ext4_orphan_cleanup: deleting unreferenced inode 8126472
[    4.643107] EXT4-fs (sdd1): ext4_orphan_cleanup: deleting unreferenced inode 8126471
[    4.643127] EXT4-fs (sdd1): ext4_orphan_cleanup: deleting unreferenced inode 8126468
[    4.643144] EXT4-fs (sdd1): 5 orphan inodes deleted
[    4.643150] EXT4-fs (sdd1): recovery complete
[    5.073077] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[    6.844414] Adding 6142972k swap on /dev/sdd5.  Priority:-1 extents:1 across:6142972k
[    8.013569] udev[376]: starting version 163
[    8.311399] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
[    8.689894] parport_pc 00:0e: reported by Plug and Play ACPI
[    8.689974] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.103148] psmouse serio1: ID: 10 00 64
[    9.218926] lp0: using parport0 (interrupt-driven).
[    9.226654] ppdev: user-space parallel port driver
[    9.243792] dm9601: Unknown parameter `mode'
[    9.351331] Linux agpgart interface v0.103
[    9.649570] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    9.650619] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[    9.664771] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    9.665575] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.665667]   alloc irq_desc for 44 on node -1
[    9.665676]   alloc kstat_irqs on node -1
[    9.665701] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    9.665784] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.728047] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    9.834305] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    9.834664] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    9.835007] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   10.019104] [drm] Initialized drm 1.1.0 20060810
[   10.515389] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.515403] i915 0000:00:02.0: setting latency timer to 64
[   10.555482]   alloc irq_desc for 45 on node -1
[   10.555490]   alloc kstat_irqs on node -1
[   10.555507] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   10.555526] [drm] set up 7M of stolen space
[   10.561207] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.561559] [drm] initialized overlay support
[   10.755891] type=1400 audit(1292404002.653:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=571 comm="apparmor_parser"
[   10.756447] type=1400 audit(1292404002.653:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=571 comm="apparmor_parser"
[   10.756805] type=1400 audit(1292404002.657:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=571 comm="apparmor_parser"
[   10.825717] [drm] Big FIFO is disabled
[   10.896535] [drm] Big FIFO is disabled
[   10.896547] [drm] Big FIFO is disabled
[   10.905817] Console: switching to colour frame buffer device 128x48
[   10.914841] fb0: inteldrmfb frame buffer device
[   10.914846] drm: registered panic notifier
[   10.914855] Slow work thread pool: Starting up
[   10.914996] Slow work thread pool: Ready
[   10.915059] No ACPI video bus found
[   10.915166] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.181970] r8169 0000:02:00.0: eth0: link up
[   11.181984] r8169 0000:02:00.0: eth0: link up
[   12.497840] type=1400 audit(1292404004.397:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=796 comm="apparmor_parser"
[   12.498396] type=1400 audit(1292404004.397:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=796 comm="apparmor_parser"
[   12.498716] type=1400 audit(1292404004.397:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=796 comm="apparmor_parser"
[   12.534338] type=1400 audit(1292404004.433:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/named" pid=798 comm="apparmor_parser"
[   12.631241] type=1400 audit(1292404004.529:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=797 comm="apparmor_parser"
[   12.672573] type=1400 audit(1292404004.573:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=799 comm="apparmor_parser"
[   15.078126] type=1400 audit(1292403999.096:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=897 comm="apparmor_parser"
[   21.504015] eth0: no IPv6 routers present
[  600.000077] [drm] Big FIFO is disabled
[  600.271646] [drm] Big FIFO is disabled
[ 1170.909177] dm9601: Unknown parameter `mode'
[ 1361.946495] dm9601: Unknown parameter `mode'
[ 1503.543729] dm9601 3-1:1.0: usb0: register 'dm9601' at usb-0000:00:1d.1-1, Davicom DM9601 USB Ethernet, 7e:10:ad:91:6f:4a
[ 1503.544085] usbcore: registered new interface driver dm9601
[ 1516.908102] usb0: link up, 10Mbps, full-duplex, lpa 0xCC61
[ 1527.152015] usb0: no IPv6 routers present
[ 2718.093047] usbcore: deregistering interface driver dm9601
[ 2718.098374] dm9601 3-1:1.0: usb0: unregister 'dm9601' usb-0000:00:1d.1-1, Davicom DM9601 USB Ethernet

```
lspci :
```

root@execute:~# lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```lsusb :
```

root@execute:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a46:9601 Davicom Semiconductor, Inc. DM9601 Fast Ethernet Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```i already enabled USB2 as HighSpeed in the BIOS. 

```

root@execute:~# lsmod
Module                  Size  Used by
dm9601                  6413  0
i915                  291659  1
drm_kms_helper         30200  1 i915
drm                   168726  2 i915,drm_kms_helper
snd_hda_codec_idt      54887  1
snd_hda_intel          22203  0
i2c_algo_bit            5168  1 i915
intel_agp              26720  2 i915
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71571  2 snd_hda_intel,snd_hda_codec
agpgart                32075  2 drm,intel_agp
video                  18712  1 i915
snd_timer              19067  1 snd_pcm
ppdev                   5556  0
lp                      7342  0
output                  1883  1 video
usbnet                 17312  1 dm9601
snd                    49006  6 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
psmouse                59033  0
serio_raw               4022  0
asus_atk0110           11423  0
parport_pc             26378  1
parport                31492  3 ppdev,lp,parport_pc
ahci                   19013  0
sata_via                7472  0
libahci                21731  3 ahci
r8169                  36777  0
mii                     4425  3 dm9601,usbnet,r8169

```Have anybody a idea ?

---

