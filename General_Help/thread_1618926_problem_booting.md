---
title: "problem booting"
date: 2010-11-11
forum: General Help
---

### Post by cry8wolf9 on 2010-11-11
rm: cannot remove 'var/lib/urandom/random-seed' : read-only file system

this is what i get every time i try to boot. right now im in the live cd looking for the read-only system so i can remove it but i cant seem to find it mounted any where the only system i see besides my two hdds is 
/dev/loop0 and i cant do anythign with the drive because its busy

---

### Post by Vigh on 2010-11-11
could be ubuntu update regression, I am having a similar problem, for me- turns out the bios wasn't configured properly, what computer system are using in terms of hardware? i was having problems mounting USB-devices, due to a "CRAPPY DEFAULT" bios, i temporarily got around it by formating the USB drives to FAT, ext4 wouldn't work, fingers crossed the bios update i am about to implement fixes the problem, the entire OS keeps crashing etc. due to the pathetic-ness of the bios, and it not being able to support 64-bit although the CPU is actually 64-bit capable, good-luck

kind regards

---

### Post by cry8wolf9 on 2010-11-11
ext4 is my main drive >_< ill try changing it mayby that will work i hope
also what fat did u use?

---

### Post by cry8wolf9 on 2010-11-11
anyone know how to switch from ext4 to ext3?
also heres a copy of my dmesg if that helps at all (i hope it does >_< )

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-AFFFF uncachable
[    0.000000]   B0000-BFFFF write-combining
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 0D0000000 mask FF8000000 write-combining
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  modified: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  modified: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000002fff0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002fc00000 page 2M
[    0.000000]  002fc00000 - 002fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 2fff0000 @ 15000-1a000
[    0.000000] RAMDISK: 2f50e000 - 2fff0000
[    0.000000] ACPI: RSDP 000f6f10 00014 (v00 KT400 )
[    0.000000] ACPI: RSDT 2fff3000 00028 (v01 KT400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 2fff3040 00074 (v01 KT400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 2fff30c0 034CC (v01 KT400  AWRDACPI 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 2fff0000 00040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2fff0000
[    0.000000]   low ram: 0 - 2fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002fff0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0002fff0
[    0.000000] On node 0 totalpages: 196480
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 190992 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:cfff0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194944
[    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3931520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (36 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [002f50e000 - 002fff0000]         RAMDISK
[    0.000000]   #4 [000009f000 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a1000 - 00009a406e]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001601000]         BOOTMEM
[    0.000000]   #11 [0001601000 - 0001601004]         BOOTMEM
[    0.000000]   #12 [0001601040 - 0001601100]         BOOTMEM
[    0.000000]   #13 [0001601100 - 0001601148]         BOOTMEM
[    0.000000]   #14 [0001601180 - 0001604180]         BOOTMEM
[    0.000000]   #15 [0001604180 - 0001604244]         BOOTMEM
[    0.000000]   #16 [0001604280 - 00016042c0]         BOOTMEM
[    0.000000]   #17 [00016042c0 - 0001604300]         BOOTMEM
[    0.000000]   #18 [0001604300 - 0001604340]         BOOTMEM
[    0.000000]   #19 [0001604340 - 0001604380]         BOOTMEM
[    0.000000]   #20 [0001604380 - 00016043c0]         BOOTMEM
[    0.000000]   #21 [00016043c0 - 0001604400]         BOOTMEM
[    0.000000]   #22 [0001604400 - 0001604410]         BOOTMEM
[    0.000000]   #23 [0001604440 - 00016044a4]         BOOTMEM
[    0.000000]   #24 [00016044c0 - 0001604524]         BOOTMEM
[    0.000000]   #25 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #26 [0001606540 - 0001606544]         BOOTMEM
[    0.000000]   #27 [0001606580 - 0001606584]         BOOTMEM
[    0.000000]   #28 [00016065c0 - 00016065c4]         BOOTMEM
[    0.000000]   #29 [0001606600 - 0001606604]         BOOTMEM
[    0.000000]   #30 [0001606640 - 00016066f0]         BOOTMEM
[    0.000000]   #31 [0001606700 - 00016067a8]         BOOTMEM
[    0.000000]   #32 [00016067c0 - 000160a7c0]         BOOTMEM
[    0.000000]   #33 [000160a7c0 - 000168a7c0]         BOOTMEM
[    0.000000]   #34 [000168a7c0 - 00016ca7c0]         BOOTMEM
[    0.000000]   #35 [000180e000 - 0001bcdd80]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 755048k/786368k available (4928k kernel code, 30872k reserved, 2336k data, 684k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf07f0000 - 0xff7fe000   ( 240 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1643.094 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3286.18 BogoMIPS (lpj=6572376)
[    0.004018] pid_max: default: 32768 minimum: 301
[    0.004067] Security Framework initialized
[    0.004113] AppArmor: AppArmor initialized
[    0.004117] Yama: becoming mindful.
[    0.008094] Mount-cache hash table entries: 512
[    0.008346] Initializing cgroup subsys ns
[    0.008356] Initializing cgroup subsys cpuacct
[    0.008364] Initializing cgroup subsys memory
[    0.008380] Initializing cgroup subsys devices
[    0.008386] Initializing cgroup subsys freezer
[    0.008390] Initializing cgroup subsys net_cls
[    0.008440] mce: CPU supports 4 MCE banks
[    0.008474] Performance Events: 
[    0.008479] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008484] no hardware sampling interrupt available.
[    0.008488] AMD PMU driver.
[    0.008501] ... version:                0
[    0.008504] ... bit width:              48
[    0.008507] ... generic registers:      4
[    0.008511] ... value mask:             0000ffffffffffff
[    0.008515] ... max period:             00007fffffffffff
[    0.008519] ... fixed-purpose events:   0
[    0.008522] ... event mask:             000000000000000f
[    0.009502] SMP alternatives: switching to UP code
[    0.019898] Freeing SMP alternatives: 24k freed
[    0.019951] ACPI: Core revision 20100428
[    0.026929] ACPI: setting ELCR to 0200 (from 1a20)
[    0.028052] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028074] ftrace: allocating 21758 entries in 43 pages
[    0.032163] weird, boot CPU (#0) not listed by the BIOS.
[    0.032168] SMP motherboard not detected.
[    0.032173] Local APIC not detected. Using dummy APIC emulation.
[    0.032175] SMP disabled
[    0.032602] Brought up 1 CPUs
[    0.032609] Total of 1 processors activated (3286.18 BogoMIPS).
[    0.033121] devtmpfs: initialized
[    0.037340] regulator: core version 0.5
[    0.037393] Time: 21:36:08  Date: 11/11/10
[    0.037476] NET: Registered protocol family 16
[    0.037700] EISA bus registered
[    0.037723] ACPI: bus type pci registered
[    0.046011] PCI: PCI BIOS revision 2.10 entry at 0xfb3d0, last bus=1
[    0.046015] PCI: Using configuration type 1 for base access
[    0.047643] bio: create slab <bio-0> at 0
[    0.048668] ACPI: EC: Look up EC in DSDT
[    0.053825] ACPI: Interpreter enabled
[    0.053833] ACPI: (supports S0 S1 S4 S5)
[    0.053869] ACPI: Using PIC for interrupt routing
[    0.061019] ACPI: No dock devices found.
[    0.061029] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.061231] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.061540] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.061545] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.061549] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.061554] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.061558] pci_root PNP0A03:00: host bridge window [mem 0x30000000-0xffefffff] (ignored)
[    0.061593] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.061691] pci 0000:00:01.0: supports D1
[    0.061730] pci 0000:00:09.0: reg 10: [mem 0xe3000000-0xe300ffff]
[    0.061801] pci 0000:00:0a.0: reg 10: [io  0xd000-0xd0ff]
[    0.061809] pci 0000:00:0a.0: reg 14: [mem 0xe3010000-0xe30100ff]
[    0.061833] pci 0000:00:0a.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.061851] pci 0000:00:0a.0: supports D1 D2
[    0.061855] pci 0000:00:0a.0: PME# supported from D1 D2 D3hot D3cold
[    0.061861] pci 0000:00:0a.0: PME# disabled
[    0.061913] pci 0000:00:10.0: reg 20: [io  0xd400-0xd41f]
[    0.061938] pci 0000:00:10.0: supports D1 D2
[    0.061942] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.061947] pci 0000:00:10.0: PME# disabled
[    0.062000] pci 0000:00:10.1: reg 20: [io  0xd800-0xd81f]
[    0.062026] pci 0000:00:10.1: supports D1 D2
[    0.062029] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062034] pci 0000:00:10.1: PME# disabled
[    0.062079] pci 0000:00:10.2: reg 20: [io  0xdc00-0xdc1f]
[    0.062105] pci 0000:00:10.2: supports D1 D2
[    0.062108] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062113] pci 0000:00:10.2: PME# disabled
[    0.062144] pci 0000:00:10.3: reg 10: [mem 0xe3011000-0xe30110ff]
[    0.062185] pci 0000:00:10.3: supports D1 D2
[    0.062188] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062193] pci 0000:00:10.3: PME# disabled
[    0.062254] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.062264] pci 0000:00:11.0: quirk: [io  0x4000-0x407f] claimed by vt8235 PM
[    0.062270] pci 0000:00:11.0: quirk: [io  0x5000-0x500f] claimed by vt8235 SMB
[    0.062331] pci 0000:00:11.1: reg 20: [io  0xe000-0xe00f]
[    0.062392] pci 0000:00:11.5: reg 10: [io  0xe400-0xe4ff]
[    0.062435] pci 0000:00:11.5: supports D1 D2
[    0.062504] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xe0ffffff]
[    0.062512] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff pref]
[    0.062531] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.062580] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.062586] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.062593] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe1ffffff]
[    0.062599] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xdfffffff pref]
[    0.062608] pci_bus 0000:00: on NUMA node 0
[    0.062616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.089904] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.090144] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.090381] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[    0.090617] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.090693] HEST: Table is not found!
[    0.090863] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.090867] vgaarb: loaded
[    0.091170] SCSI subsystem initialized
[    0.091317] libata version 3.00 loaded.
[    0.091435] usbcore: registered new interface driver usbfs
[    0.091456] usbcore: registered new interface driver hub
[    0.091520] usbcore: registered new device driver usb
[    0.091801] ACPI: WMI: Mapper loaded
[    0.091807] PCI: Using ACPI for IRQ routing
[    0.091815] PCI: pci_cache_line_size set to 32 bytes
[    0.091885] reserve RAM buffer: 000000002fff0000 - 000000002fffffff 
[    0.092113] NetLabel: Initializing
[    0.092117] NetLabel:  domain hash size = 128
[    0.092119] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.092155] NetLabel:  unlabeled traffic allowed by default
[    0.092254] Switching to clocksource tsc
[    0.109194] AppArmor: AppArmor Filesystem Enabled
[    0.109231] pnp: PnP ACPI init
[    0.109267] ACPI: bus type pnp registered
[    0.110526] ERROR: Unable to locate IOAPIC for GSI 8
[    0.110628] ERROR: Unable to locate IOAPIC for GSI 13
[    0.111090] ERROR: Unable to locate IOAPIC for GSI 6
[    0.111672] ERROR: Unable to locate IOAPIC for GSI 4
[    0.112378] ERROR: Unable to locate IOAPIC for GSI 3
[    0.113199] ERROR: Unable to locate IOAPIC for GSI 7
[    0.114193] ERROR: Unable to locate IOAPIC for GSI 10
[    0.114543] pnp: PnP ACPI: found 15 devices
[    0.114548] ACPI: ACPI bus type pnp unregistered
[    0.114554] PnPBIOS: Disabled by ACPI PNP
[    0.114579] system 00:00: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.114584] system 00:00: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.114589] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.114593] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.114598] system 00:00: [mem 0x2fff0000-0x2fffffff] could not be reserved
[    0.114603] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
[    0.114607] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.114612] system 00:00: [mem 0x00100000-0x2ffeffff] could not be reserved
[    0.114617] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.114621] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.114632] system 00:02: [io  0x4000-0x407f] has been reserved
[    0.114637] system 00:02: [io  0x5000-0x500f] has been reserved
[    0.114646] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.114650] system 00:03: [io  0x0800-0x0805] has been reserved
[    0.114654] system 00:03: [io  0x0290-0x0297] has been reserved
[    0.151713] pci 0000:00:0a.0: BAR 6: assigned [mem 0x30000000-0x3001ffff pref]
[    0.151722] pci 0000:01:00.0: BAR 6: assigned [mem 0xe1000000-0xe100ffff pref]
[    0.151727] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.151731] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.151739] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe1ffffff]
[    0.151744] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xdfffffff pref]
[    0.151764] pci 0000:00:01.0: setting latency timer to 64
[    0.151771] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.151774] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.151779] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xe1ffffff]
[    0.151783] pci_bus 0000:01: resource 2 [mem 0xd8000000-0xdfffffff pref]
[    0.151866] NET: Registered protocol family 2
[    0.151967] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.152607] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.154660] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.155682] TCP: Hash tables configured (established 131072 bind 65536)
[    0.155688] TCP reno registered
[    0.155732] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.155764] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.155933] NET: Registered protocol family 1
[    0.155961] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.156067] pci 0000:01:00.0: Boot video device
[    0.156073] PCI: CLS 32 bytes, default 32
[    0.156441] cpufreq-nforce2: No nForce2 chipset.
[    0.156485] Scanning for low memory corruption every 60 seconds
[    0.156710] audit: initializing netlink socket (disabled)
[    0.156733] type=2000 audit(1289511368.152:1): initialized
[    0.170081] Trying to unpack rootfs image as initramfs...
[    3.493543] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.495796] VFS: Disk quotas dquot_6.5.2
[    3.495917] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.497026] fuse init (API version 7.14)
[    3.497218] msgmni has been set to 1474
[    3.497913] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.497920] io scheduler noop registered
[    3.497923] io scheduler deadline registered
[    3.497942] io scheduler cfq registered (default)
[    3.498145] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.498183] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.498490] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.498502] ACPI: Power Button [PWRB]
[    3.498576] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    3.498589] ACPI: Sleep Button [SLPB]
[    3.498669] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.498675] ACPI: Power Button [PWRF]
[    3.498763] ACPI: Fan [FAN] (on)
[    3.499069] ACPI: acpi_idle registered with cpuidle
[    3.499123] Marking TSC unstable due to TSC halts in idle
[    3.502835] thermal LNXTHERM:01: registered as thermal_zone0
[    3.502851] ACPI: Thermal Zone [THRM] (40 C)
[    3.502944] ERST: Table is not found!
[    3.503385] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.503528] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.503661] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.504159] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.504360] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.506212] brd: module loaded
[    3.507065] loop: module loaded
[    3.508151] isapnp: Scanning for PnP cards...
[    3.513668] Switching to clocksource acpi_pm
[    3.513870] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    3.513876] PCI: setting IRQ 5 as level-triggered
[    3.513885] pata_acpi 0000:00:11.1: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    3.513894] pata_acpi 0000:00:11.1: VIA VLink IRQ fixup, from 255 to 5
[    3.514012] pata_acpi 0000:00:11.1: PCI INT A disabled
[    3.514600] Fixed MDIO Bus: probed
[    3.514661] PPP generic driver version 2.4.2
[    3.514804] tun: Universal TUN/TAP device driver, 1.6
[    3.514808] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.514961] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.515688] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.515694] PCI: setting IRQ 11 as level-triggered
[    3.515704] ehci_hcd 0000:00:10.3: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.515749] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    3.515876] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    3.515951] ehci_hcd 0000:00:10.3: irq 11, io mem 0xe3011000
[    3.559547] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    3.559820] hub 1-0:1.0: USB hub found
[    3.559833] hub 1-0:1.0: 6 ports detected
[    3.559951] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.559977] uhci_hcd: USB Universal Host Controller Interface driver
[    3.560150] uhci_hcd 0000:00:10.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    3.560169] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.560292] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    3.560331] uhci_hcd 0000:00:10.0: irq 5, io base 0x0000d400
[    3.560593] hub 2-0:1.0: USB hub found
[    3.560604] hub 2-0:1.0: 2 ports detected
[    3.561408] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    3.561417] uhci_hcd 0000:00:10.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.561436] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.561575] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    3.561614] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000d800
[    3.561873] hub 3-0:1.0: USB hub found
[    3.561885] hub 3-0:1.0: 2 ports detected
[    3.562718] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[    3.562725] PCI: setting IRQ 12 as level-triggered
[    3.562734] uhci_hcd 0000:00:10.2: PCI INT C -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    3.562752] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.562882] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    3.562924] uhci_hcd 0000:00:10.2: irq 12, io base 0x0000dc00
[    3.563227] hub 4-0:1.0: USB hub found
[    3.563239] hub 4-0:1.0: 2 ports detected
[    3.563435] PNP: No PS/2 controller found. Probing ports directly.
[    3.824954] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.825147] mice: PS/2 mouse device common for all mice
[    3.825367] rtc_cmos 00:05: RTC can wake from S4
[    3.825444] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.825478] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    3.825676] device-mapper: uevent: version 1.0.3
[    3.826133] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    3.826276] device-mapper: multipath: version 1.1.1 loaded
[    3.826282] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.826534] EISA: Probing bus 0 at eisa.0
[    3.826564] Cannot allocate resource for EISA slot 4
[    3.826568] Cannot allocate resource for EISA slot 5
[    3.826585] EISA: Detected 0 cards.
[    3.826759] cpuidle: using governor ladder
[    3.826834] cpuidle: using governor menu
[    3.827280] TCP cubic registered
[    3.827524] NET: Registered protocol family 10
[    3.828138] lo: Disabled Privacy Extensions
[    3.828446] NET: Registered protocol family 17
[    3.828533] powernow-k8: Processor cpuid 681 not supported
[    3.828570] Using IPI No-Shortcut mode
[    3.828774] PM: Resume from disk failed.
[    3.828804] registered taskstats version 1
[    3.829027]   Magic number: 2:666:651
[    3.829148] pci_root PNP0A03:00: hash matches
[    3.829204] rtc_cmos 00:05: setting system clock to 2010-11-11 21:36:12 UTC (1289511372)
[    3.829210] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.829212] EDD information not available.
[    3.872909] isapnp: No Plug & Play device found
[    4.442905] Freeing initrd memory: 11144k freed
[    4.463238] Freeing unused kernel memory: 684k freed
[    4.464653] Write protecting the kernel text: 4932k
[    4.464700] Write protecting the kernel read-only data: 1976k
[    4.520317] udev[70]: starting version 163
[    4.528158] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    4.854551] Floppy drive(s): fd0 is 1.44M
[    4.900161] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.964850] FDC 0 is a post-1991 82077
[    4.975188] pata_via 0000:00:11.1: version 0.3.4
[    4.975220] pata_via 0000:00:11.1: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    4.975228] pata_via 0000:00:11.1: VIA VLink IRQ fixup, from 255 to 5
[    5.000231] scsi0 : pata_via
[    5.000620] Linux agpgart interface v0.103
[    5.022531] scsi1 : pata_via
[    5.028225] Initializing USB Mass Storage driver...
[    5.064933] scsi2 : usb-storage 1-5:1.0
[    5.066325] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[    5.066333] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[    5.066640] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.066680] r8169 0000:00:0a.0: PCI INT A -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.066729] r8169 0000:00:0a.0: (unregistered net_device): no PCI Express capability
[    5.067500] r8169 0000:00:0a.0: eth0: RTL8110s at 0xf0960000, 00:1e:2a:c0:44:41, XID 04000000 IRQ 12
[    5.075379] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[    5.087369] usbcore: registered new interface driver usb-storage
[    5.087376] USB Mass Storage support registered.
[    5.178173] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[    5.204931] [drm] Initialized drm 1.1.0 20060810
[    5.236542] ata1.00: ATA-6: WDC WD800BB-00JHC0, 05.01C05, max UDMA/100
[    5.236547] ata1.00: 156301488 sectors, multi 0: LBA 
[    5.236718] ata1.01: ATA-6: WDC WD800BB-75JHC0, 06.01C06, max UDMA/100
[    5.236722] ata1.01: 156250000 sectors, multi 0: LBA 
[    5.244432] ata1.00: configured for UDMA/100
[    5.252444] ata1.01: configured for UDMA/100
[    5.252669] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-00JH 05.0 PQ: 0 ANSI: 5
[    5.253003] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.253714] scsi 0:0:1:0: Direct-Access     ATA      WDC WD800BB-75JH 06.0 PQ: 0 ANSI: 5
[    5.254584] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    5.255155] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    5.255249] sd 0:0:0:0: [sda] Write Protect is off
[    5.255255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.255294] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.255641]  sda: sda1 sda2 < sda5 >
[    5.282362] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.282416] sd 0:0:1:0: [sdb] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    5.282501] sd 0:0:1:0: [sdb] Write Protect is off
[    5.282507] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.282542] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.282893]  sdb: sdb1
[    5.296116] sd 0:0:1:0: [sdb] Attached SCSI disk
[    5.356069] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    5.570599] scsi3 : usb-storage 2-2:1.3
[    5.592656] ata2.00: ATAPI: ATAPI   DVD LS 8X16X8X16, GCGB, max UDMA/33
[    5.592701] ata2.01: ATAPI: SONY    CD-RW  CRX230ED, 4YS1, max UDMA/33
[    5.608596] ata2.00: configured for UDMA/33
[    5.624289] ata2.01: configured for UDMA/33
[    5.627712] scsi 1:0:0:0: CD-ROM            ATAPI    DVD LS 8X16X8X16 GCGB PQ: 0 ANSI: 5
[    5.637278] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.637287] Uniform CD-ROM driver Revision: 3.20
[    5.638503] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.639011] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    5.640257] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX230ED  4YS1 PQ: 0 ANSI: 5
[    5.643684] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    5.644980] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.645465] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    5.723786] usbcore: registered new interface driver hiddev
[    5.739151] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input3
[    5.739848] generic-usb 0003:046D:C044.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1/input0
[    5.740551] usbcore: registered new interface driver usbhid
[    5.740561] usbhid: USB HID core driver
[    5.820897] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.823897] nouveau 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    5.832541] [drm] nouveau 0000:01:00.0: Detected an NV10 generation card (0x011000b2)
[    5.832822] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    5.870669] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    5.870945] [drm] nouveau 0000:01:00.0: BMP BIOS found
[    5.870950] [drm] nouveau 0000:01:00.0: BMP version 5.17
[    5.870955] [drm] nouveau 0000:01:00.0: Bios version 03.11.00.18
[    5.870961] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 1.2
[    5.870965] [drm] nouveau 0000:01:00.0: No useful information in BIOS output table; adding all possible outputs
[    5.870970] [drm] nouveau 0000:01:00.0: Probing TV encoders on I2C bus: 1
[    5.876509] [drm] nouveau 0000:01:00.0: No TV encoders found.
[    5.876807] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x07FE
[    5.876827] [drm] nouveau 0000:01:00.0: 0x0818: Failed parsing init table opcode: INIT_CONFIGURE_PREINIT -19
[    5.876831] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x0EA7
[    5.876840] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x0819
[    5.876861] [drm] nouveau 0000:01:00.0: 0x08AB: Failed parsing init table opcode: INIT_CONFIGURE_CLK -19
[    5.876865] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x0E4E
[    5.876876] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x08AC
[    5.876881] [drm] nouveau 0000:01:00.0: 0x08D9: Failed parsing init table opcode: INIT_CONFIGURE_MEM -19
[    5.876885] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0x09BB
[    5.876908] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0x08DA
[    5.876927] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 7 at offset 0x0956
[    5.876938] [drm] nouveau 0000:01:00.0: Detected 32MiB VRAM
[    5.893282] [TTM] Zone  kernel: Available graphics memory: 383450 kiB.
[    5.893288] [TTM] Initializing pool allocator.
[    5.893922] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[    5.893946] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[    5.893955] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[    5.894017] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[    5.894022] [drm] nouveau 0000:01:00.0: 128 MiB GART (aperture)
[    5.895444] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[    5.897093] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[    5.897114] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[    5.897127] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[    5.938153] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    5.938612] [drm] nouveau 0000:01:00.0: Detected a DVI-D connector
[    5.940887] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[    5.940896] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[    6.024587] input: HID 0b38:0010 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input4
[    6.026236] generic-usb 0003:0B38:0010.0002: input,hidraw1: USB HID v1.10 Keyboard [HID 0b38:0010] on usb-0000:00:10.1-1/input0
[    6.049724] input: HID 0b38:0010 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/input/input5
[    6.049919] generic-usb 0003:0B38:0010.0003: input,hidraw2: USB HID v1.10 Device [HID 0b38:0010] on usb-0000:00:10.1-1/input1
[    6.088790] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 2
[    6.092276] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    6.092476] sd 2:0:0:0: [sdc] 7837696 512-byte logical blocks: (4.01 GB/3.73 GiB)
[    6.093973] sd 2:0:0:0: [sdc] Write Protect is off
[    6.093981] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    6.093986] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.096735] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.096765]  sdc: sdc1
[    6.107630] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.107642] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[    6.184603] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x49000, bo ef3ee000
[    6.197045] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[    6.197053] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output @
[    6.218994] Console: switching to colour frame buffer device 160x64
[    6.235272] fb0: nouveaufb frame buffer device
[    6.235276] drm: registered panic notifier
[    6.236394] Slow work thread pool: Starting up
[    6.236815] Slow work thread pool: Ready
[    6.236838] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    6.578625] scsi 3:0:0:0: Direct-Access     HP       Officejet 7210   1.00 PQ: 0 ANSI: 2
[    6.579758] sd 3:0:0:0: Attached scsi generic sg5 type 0
[    6.593653] sd 3:0:0:0: [sdd] Attached SCSI removable disk
[    6.931324] Btrfs loaded
[    6.945559] xor: automatically using best checksumming function: pIII_sse
[    6.964038]    pIII_sse  :  1315.000 MB/sec
[    6.964042] xor: using function: pIII_sse (1315.000 MB/sec)
[    6.971113] device-mapper: dm-raid45: initialized v0.2594b
[    7.375114] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.719716] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    8.788845] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.788856] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    8.788863] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    8.788877] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    8.788889] end_request: I/O error, dev sr1, sector 1419584
[    8.788897] Buffer I/O error on device sr1, logical block 177448
[    8.834191] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.834201] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    8.834208] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    8.834222] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    8.834234] end_request: I/O error, dev sr1, sector 1419584
[    8.834241] Buffer I/O error on device sr1, logical block 177448
[    8.879513] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.879524] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    8.879530] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    8.879544] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    8.879556] end_request: I/O error, dev sr1, sector 1419584
[    8.879563] Buffer I/O error on device sr1, logical block 177448
[    8.924730] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.924740] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    8.924746] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    8.924759] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    8.924771] end_request: I/O error, dev sr1, sector 1419584
[    8.924778] Buffer I/O error on device sr1, logical block 177448
[    8.969921] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.969931] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    8.969937] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    8.969951] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    8.969962] end_request: I/O error, dev sr1, sector 1419584
[    8.969969] Buffer I/O error on device sr1, logical block 177448
[    9.015106] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.015116] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    9.015122] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    9.015136] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    9.015148] end_request: I/O error, dev sr1, sector 1419584
[    9.015155] Buffer I/O error on device sr1, logical block 177448
[    9.060242] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.060252] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    9.060258] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    9.060272] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    9.060284] end_request: I/O error, dev sr1, sector 1419584
[    9.060291] Buffer I/O error on device sr1, logical block 177448
[    9.135341] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.135352] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    9.135358] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    9.135372] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    9.135385] end_request: I/O error, dev sr1, sector 1419584
[    9.135392] Buffer I/O error on device sr1, logical block 177448
[    9.180265] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.180275] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    9.180281] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    9.180295] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    9.180306] end_request: I/O error, dev sr1, sector 1419584
[    9.180313] Buffer I/O error on device sr1, logical block 177448
[    9.224930] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.224940] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[    9.224947] sr 1:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[    9.224961] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 05 6a 50 00 00 02 00
[    9.224973] end_request: I/O error, dev sr1, sector 1419584
[    9.224980] Buffer I/O error on device sr1, logical block 177448
[    9.600288] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.625032] ISO 9660 Extensions: RRIP_1991A
[    9.749603] aufs 2-standalone.tree-35-rcN-20100705
[    9.827340] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   54.718096] Adding 2301948k swap on /dev/sda5.  Priority:-1 extents:1 across:2301948k 
[   56.332698] udev[1331]: starting version 163
[   60.443434] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.463309] irda_init()
[   61.463355] NET: Registered protocol family 23
[   61.465096] cfg80211: Calling CRDA to update world regulatory domain
[   61.648733] parport_pc 00:0b: reported by Plug and Play ACPI
[   61.648789] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   62.102484] ns558 00:0e: activated
[   62.172738] gameport gameport0: NS558 PnP Gameport is pnp00:0e/gameport0, io 0x201, speed 852kHz
[   62.322279] ppdev: user-space parallel port driver
[   63.865040] cfg80211: World regulatory domain updated:
[   63.865051]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   63.865057]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   63.865061]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   63.865065]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   63.865069]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   63.865073]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.190773] ath5k 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   65.190893] ath5k 0000:00:09.0: registered as 'phy0'
[   65.784547] ath: EEPROM regdomain: 0x10
[   65.784554] ath: EEPROM indicates we should expect a direct regpair map
[   65.784560] ath: Country alpha2 being used: CO
[   65.784562] ath: Regpair used: 0x10
[   66.750172] r8169 0000:00:0a.0: eth0: link up
[   66.856768] phy0: Selected rate control algorithm 'minstrel'
[   66.857996] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   66.858015] cfg80211: Calling CRDA for country: CO
[   66.858141] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[   66.858295] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   66.885025] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4111
[   66.885080] usbcore: registered new interface driver usblp
[   67.039687] cfg80211: Regulatory domain changed to country: CO
[   67.039697]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   67.039702]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   67.039706]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   67.039711]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   67.039715]     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   67.553919] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.577871] lp0: using parport0 (interrupt-driven).
[   77.504038] eth0: no IPv6 routers present
[   77.586279] usb 2-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   79.921005] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   79.921844] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   80.879447] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   80.899521] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   80.899528] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output @
[  172.619004] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 1
[  172.622839] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[  172.642906] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[  172.642912] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output @
[  174.637739] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[  174.638563] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[  174.689810] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[  174.709881] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[  174.709887] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output @
[  248.220913] usb 2-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 4251.071864] wlan0: authenticate with 00:13:10:1a:7c:68 (try 1)
[ 4251.075220] wlan0: authenticated
[ 4251.075295] wlan0: associate with 00:13:10:1a:7c:68 (try 1)
[ 4251.077233] wlan0: RX AssocResp from 00:13:10:1a:7c:68 (capab=0x401 status=0 aid=1)
[ 4251.077242] wlan0: associated
[ 4251.078856] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4261.840069] wlan0: no IPv6 routers present
[ 4299.297947] No probe response from AP 00:13:10:1a:7c:68 after 500ms, disconnecting.
[ 4299.298658] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4299.298670] cfg80211: Restoring regulatory settings
[ 4299.298677] cfg80211: Calling CRDA to update world regulatory domain
[ 4300.177011] wlan0: authenticate with 00:13:10:1a:7c:68 (try 1)
[ 4300.178543] wlan0: authenticated
[ 4300.178596] wlan0: associate with 00:13:10:1a:7c:68 (try 1)
[ 4300.183453] wlan0: RX AssocResp from 00:13:10:1a:7c:68 (capab=0x401 status=0 aid=1)
[ 4300.183462] wlan0: associated
[ 4300.266473] cfg80211: World regulatory domain updated:
[ 4300.266483]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4300.266489]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4300.266493]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4300.266498]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4300.266502]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4300.266506]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4309.574694] wlan0: deauthenticating from 00:13:10:1a:7c:68 by local choice (reason=3)
[ 4309.576147] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4309.576160] cfg80211: Restoring regulatory settings
[ 4309.576167] cfg80211: Calling CRDA to update world regulatory domain
[ 4309.806340] cfg80211: World regulatory domain updated:
[ 4309.806351]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4309.806357]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4309.806361]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4309.806366]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4309.806370]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4309.806374]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9480.666814] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

```

---

