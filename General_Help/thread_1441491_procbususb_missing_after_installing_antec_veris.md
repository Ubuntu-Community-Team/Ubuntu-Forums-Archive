---
title: "/proc/bus/usb missing after installing antec veris"
date: 2010-03-28
forum: General Help
---

### Post by renfrew on 2010-03-28
I recently installed an Antec Veris basic IR receiver which as caused me a host of problems.  Mainly I now have no /proc/bus/usb directory. I can see no strange behaviour from lsusb and my usb devices seem to be working fine, I can plug in a thumb-drive and it works fine, my bluetooth usb adapter is working, etc.   The new hardware also seems to work fine and when running from a live-cd I can see /proc/bus/usb and the devices file which normally resides there.   I've re-installed Ubuntu 9.10 about 6 times now with no luck, the IR remote seems to work, at least the enter button does. I did have to mess with the lirc rules as mentioned in other posts in order to get that some-what working.  I should maybe mention I have an ASUS P4S800D-X mobo and the IR recevier is an Antec Veris Basic


Here's the output from lsusb:
Bus 003 Device 002: ID 15c2:0043 SoundGraph Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1019:0c55 Elitegroup Computer Systems (ECS) Flash Reader, Desknote UCR-61S2B
Bus 002 Device 003: ID 0a5c:2045 Broadcom Corp. Bluetooth Controller
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the IR receiver is on Bus 3, Device 2 FWIW

and here's the output from lsmod | grep usb
btusb                  11856  2 
usb_storage            52768  0 
usbhid                 38208  0 

If I try to mount -t usbfs none /proc/bus/usb in order to cat /proc/bus/usb/devices I of course get an error saying it doesn't exist.  
 Unless it's been deprecated I should be able to see /proc/bus/usb shouldn't I? or somehow re-create it?... Any ideas? anyone?

---

### Post by renfrew on 2010-03-29
After looking at this a little further I realized that my thumb drives are not being mounted under USB but seem to now show up as SCSI disks.  

Up 'til I installed the new hardware I had never looked in /proc/bus/usb, has it been abandoned in favour of something else (in the same fashion as grub, for example)? 

Nothing in var/log/messages indicates a problem, at least to me, nor does the output from dmesg.  I've attached both here in the hope that someone else with a keener eye and more experience can tell me what's happening and how to recover /proc/bus/usb

dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 base 0E0000000 mask FF0000000 write-combining
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  modified: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  modified: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f858000 - 300036d0
[    0.000000] ACPI: RSDP 000fb470 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 3ffb0100 0003C (v01 A M I  OEMXSDT  06000615 MSFT 00000097)
[    0.000000] ACPI: FACP 3ffb0290 000F4 (v03 A M I  OEMFACP  06000615 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ffb03f0 03391 (v01  A0149 A0149001 00000001 INTL 02002026)
[    0.000000] ACPI: FACS 3ffc0000 00040
[    0.000000] ACPI: APIC 3ffb0390 0005C (v01 A M I  OEMAPIC  06000615 MSFT 00000097)
[    0.000000] ACPI: OEMB 3ffc0040 00040 (v01 A M I  AMI_OEM  06000615 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ae160]    TEXT DATA BSS ==> [0000100000 - 00008ae160]
[    0.000000]   #4 [002f858000 - 00300036d0]          RAMDISK ==> [002f858000 - 00300036d0]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008af000 - 00008b222c]              BRK ==> [00008af000 - 00008b222c]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffb0
[    0.000000] On node 0 totalpages: 261951
[    0.000000] free_area_init_node: node 0, pgdat c0788d40, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34466 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf780000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259903
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=5021019d-82eb-4a23-bc8e-d09da0c0dd99 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5240960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ffb0)
[    0.000000] Memory: 1017220k/1048256k available (4583k kernel code, 29996k reserved, 2142k data, 544k init, 138952k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc081a000   ( 544 kB)
[    0.000000]       .data : 0xc0579d78 - 0xc0791848   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0579d78   (4583 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2400.899 MHz processor.
[    0.001484] Console: colour VGA+ 80x25
[    0.001489] console [tty0] enabled
[    0.001549] Calibrating delay loop (skipped), value calculated using timer frequency.. 4801.79 BogoMIPS (lpj=9603596)
[    0.001580] Security Framework initialized
[    0.001609] AppArmor: AppArmor initialized
[    0.001621] Mount-cache hash table entries: 512
[    0.001827] Initializing cgroup subsys ns
[    0.001837] Initializing cgroup subsys cpuacct
[    0.001844] Initializing cgroup subsys memory
[    0.001854] Initializing cgroup subsys devices
[    0.001858] Initializing cgroup subsys freezer
[    0.001862] Initializing cgroup subsys net_cls
[    0.001890] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.001895] CPU: L2 cache: 256K
[    0.001899] CPU: Hyper-Threading is disabled
[    0.001905] mce: CPU supports 4 MCE banks
[    0.001922] CPU0: Thermal monitoring enabled (TM1)
[    0.001929] using mwait in idle threads.
[    0.001939] Performance Counters: no PMU driver, software counters only.
[    0.001950] Checking 'hlt' instruction... OK.
[    0.017243] SMP alternatives: switching to UP code
[    0.028017] ACPI: Core revision 20090521
[    0.040910] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080608] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 04
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (4801.79 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] ASUS P4S800 series board detected. Selecting BIOS-method for reboots.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 15:04:42  Date: 03/29/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084687] bio: create slab <bio-0> at 0
[    0.085542] ACPI: EC: Look up EC in DSDT
[    0.097218] ACPI: Interpreter enabled
[    0.097240] ACPI: (supports S0 S1 S3 S4 S5)
[    0.097281] ACPI: Using IOAPIC for interrupt routing
[    0.107798] ACPI Warning: Incorrect checksum in table [OEMB] - E7, should be DE 20090521 tbutils-246
[    0.107927] ACPI: No dock devices found.
[    0.108169] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.108251] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.108470] pci 0000:00:02.5: reg 10 io port: [0x00-0x07]
[    0.108482] pci 0000:00:02.5: reg 14 io port: [0x00-0x03]
[    0.108491] pci 0000:00:02.5: reg 18 io port: [0x00-0x07]
[    0.108500] pci 0000:00:02.5: reg 1c io port: [0x00-0x03]
[    0.108510] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
[    0.108548] pci 0000:00:02.5: PME# supported from D3cold
[    0.108555] pci 0000:00:02.5: PME# disabled
[    0.108602] pci 0000:00:02.7: reg 10 io port: [0xe800-0xe8ff]
[    0.108612] pci 0000:00:02.7: reg 14 io port: [0xec00-0xec7f]
[    0.108666] pci 0000:00:02.7: supports D1 D2
[    0.108670] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.108676] pci 0000:00:02.7: PME# disabled
[    0.108708] pci 0000:00:03.0: reg 10 32bit mmio: [0xfebfc000-0xfebfcfff]
[    0.108776] pci 0000:00:03.1: reg 10 32bit mmio: [0xfebfd000-0xfebfdfff]
[    0.108845] pci 0000:00:03.2: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.108927] pci 0000:00:03.3: reg 10 32bit mmio: [0xfebff000-0xfebfffff]
[    0.108987] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.108994] pci 0000:00:03.3: PME# disabled
[    0.109046] pci 0000:00:04.0: reg 10 io port: [0xe400-0xe4ff]
[    0.109056] pci 0000:00:04.0: reg 14 32bit mmio: [0xfebfb000-0xfebfbfff]
[    0.109088] pci 0000:00:04.0: reg 30 32bit mmio: [0xfebc0000-0xfebdffff]
[    0.109113] pci 0000:00:04.0: supports D1 D2
[    0.109118] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109124] pci 0000:00:04.0: PME# disabled
[    0.109155] pci 0000:00:05.0: reg 10 io port: [0xeff0-0xeff7]
[    0.109164] pci 0000:00:05.0: reg 14 io port: [0xefe4-0xefe7]
[    0.109173] pci 0000:00:05.0: reg 18 io port: [0xefa8-0xefaf]
[    0.109182] pci 0000:00:05.0: reg 1c io port: [0xefe0-0xefe3]
[    0.109191] pci 0000:00:05.0: reg 20 io port: [0xef90-0xef9f]
[    0.109268] pci 0000:00:0c.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.109429] pci 0000:01:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.109441] pci 0000:01:00.0: reg 14 io port: [0xd000-0xd0ff]
[    0.109450] pci 0000:01:00.0: reg 18 32bit mmio: [0xf6af0000-0xf6afffff]
[    0.109476] pci 0000:01:00.0: reg 30 32bit mmio: [0xf6ac0000-0xf6adffff]
[    0.109510] pci 0000:01:00.0: supports D1 D2
[    0.109566] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.109573] pci 0000:00:01.0: bridge 32bit mmio: [0xf6a00000-0xf6afffff]
[    0.109579] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbff00000-0xdfefffff]
[    0.109592] pci_bus 0000:00: on NUMA node 0
[    0.109601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.118509] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.118698] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.118869] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.119040] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.119211] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.119384] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.119557] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.119730] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.120088] SCSI subsystem initialized
[    0.120200] libata version 3.00 loaded.
[    0.120356] usbcore: registered new interface driver usbfs
[    0.120378] usbcore: registered new interface driver hub
[    0.120430] usbcore: registered new device driver usb
[    0.120683] ACPI: WMI: Mapper loaded
[    0.120687] PCI: Using ACPI for IRQ routing
[    0.120911] Bluetooth: Core ver 2.15
[    0.120997] NET: Registered protocol family 31
[    0.121001] Bluetooth: HCI device and connection manager initialized
[    0.121005] Bluetooth: HCI socket layer initialized
[    0.121009] NetLabel: Initializing
[    0.121011] NetLabel:  domain hash size = 128
[    0.121013] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.121035] NetLabel:  unlabeled traffic allowed by default
[    0.123977] pnp: PnP ACPI init
[    0.124049] ACPI: bus type pnp registered
[    0.129158] pnp: PnP ACPI: found 13 devices
[    0.129163] ACPI: ACPI bus type pnp unregistered
[    0.129171] PnPBIOS: Disabled by ACPI PNP
[    0.129197] system 00:08: ioport range 0x680-0x6ff has been reserved
[    0.129202] system 00:08: ioport range 0x290-0x297 has been reserved
[    0.129212] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.129217] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.129221] system 00:09: ioport range 0x800-0x8df has been reserved
[    0.129225] system 00:09: ioport range 0x8e0-0x8ff has been reserved
[    0.129231] system 00:09: iomem range 0xffe80000-0xffefffff has been reserved
[    0.129241] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.129246] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.129250] system 00:0a: iomem range 0xfff80000-0xffffffff has been reserved
[    0.129259] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.129264] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[    0.129268] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.129273] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.164037] AppArmor: AppArmor Filesystem Enabled
[    0.164073] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.164079] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.164088] pci 0000:00:01.0:   MEM window: 0xf6a00000-0xf6afffff
[    0.164094] pci 0000:00:01.0:   PREFETCH window: 0xbff00000-0xdfefffff
[    0.164116] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.164120] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.164124] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.164128] pci_bus 0000:01: resource 1 mem: [0xf6a00000-0xf6afffff]
[    0.164131] pci_bus 0000:01: resource 2 pref mem [0xbff00000-0xdfefffff]
[    0.164192] NET: Registered protocol family 2
[    0.164344] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.164869] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.165676] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.166094] TCP: Hash tables configured (established 131072 bind 65536)
[    0.166101] TCP reno registered
[    0.166292] NET: Registered protocol family 1
[    0.166401] Trying to unpack rootfs image as initramfs...
[    0.501423] Freeing initrd memory: 7853k freed
[    0.509380] cpufreq-nforce2: No nForce2 chipset.
[    0.509428] Scanning for low memory corruption every 60 seconds
[    0.509590] audit: initializing netlink socket (disabled)
[    0.509615] type=2000 audit(1269875082.507:1): initialized
[    0.520891] highmem bounce pool size: 64 pages
[    0.520905] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.523001] VFS: Disk quotas dquot_6.5.2
[    0.523113] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.524037] fuse init (API version 7.12)
[    0.524195] msgmni has been set to 1731
[    0.524587] alg: No test for stdrng (krng)
[    0.524617] io scheduler noop registered
[    0.524620] io scheduler anticipatory registered
[    0.524623] io scheduler deadline registered
[    0.524724] io scheduler cfq registered (default)
[    0.595998] pci 0000:01:00.0: Boot video device
[    0.596141] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.596180] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.596386] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.596394] ACPI: Power Button [PWRF]
[    0.596487] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.596493] ACPI: Power Button [PWRB]
[    0.597062] processor LNXCPU:00: registered as cooling_device0
[    0.597071] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.600692] isapnp: Scanning for PnP cards...
[    0.675975] Switched to high resolution mode on CPU 0
[    0.954617] isapnp: No Plug & Play device found
[    0.956572] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.956728] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.957340] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.958874] brd: module loaded
[    0.959584] loop: module loaded
[    0.959746] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.960075] sata_sis 0000:00:05.0: version 1.0
[    0.960099]   alloc irq_desc for 17 on node -1
[    0.960103]   alloc kstat_irqs on node -1
[    0.960114] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.960122] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[    0.960295] scsi0 : sata_sis
[    0.960480] scsi1 : sata_sis
[    0.960555] ata1: SATA max UDMA/133 cmd 0xeff0 ctl 0xefe4 bmdma 0xef90 irq 17
[    0.960564] ata2: SATA max UDMA/133 cmd 0xefa8 ctl 0xefe0 bmdma 0xef98 irq 17
[    0.961229] pata_sis 0000:00:02.5: version 0.5.2
[    0.961250]   alloc irq_desc for 16 on node -1
[    0.961253]   alloc kstat_irqs on node -1
[    0.961264] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.961530] scsi2 : pata_sis
[    0.961670] scsi3 : pata_sis
[    0.962837] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.962843] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.963404] Fixed MDIO Bus: probed
[    0.963476] PPP generic driver version 2.4.2
[    0.963655] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.963704]   alloc irq_desc for 23 on node -1
[    0.963708]   alloc kstat_irqs on node -1
[    0.963718] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.963743] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.963809] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.963855] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    0.963879] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfebff000
[    0.972014] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.972179] usb usb1: configuration #1 chosen from 1 choice
[    0.972232] hub 1-0:1.0: USB hub found
[    0.972248] hub 1-0:1.0: 8 ports detected
[    0.972346] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.972391]   alloc irq_desc for 20 on node -1
[    0.972395]   alloc kstat_irqs on node -1
[    0.972405] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.972428] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.972513] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.972549] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfebfc000
[    1.030130] usb usb2: configuration #1 chosen from 1 choice
[    1.030186] hub 2-0:1.0: USB hub found
[    1.030202] hub 2-0:1.0: 3 ports detected
[    1.030276]   alloc irq_desc for 21 on node -1
[    1.030281]   alloc kstat_irqs on node -1
[    1.030291] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.030313] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.030399] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.030433] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfebfd000
[    1.086125] usb usb3: configuration #1 chosen from 1 choice
[    1.086173] hub 3-0:1.0: USB hub found
[    1.086190] hub 3-0:1.0: 3 ports detected
[    1.086261]   alloc irq_desc for 22 on node -1
[    1.086265]   alloc kstat_irqs on node -1
[    1.086275] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.086297] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    1.086371] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    1.086406] ohci_hcd 0000:00:03.2: irq 22, io mem 0xfebfe000
[    1.128484] ata3.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    1.128489] ata3.00: 160086528 sectors, multi 16: LBA 
[    1.128529] ata3.00: limited to UDMA/33 due to 40-wire cable
[    1.142144] usb usb4: configuration #1 chosen from 1 choice
[    1.142195] hub 4-0:1.0: USB hub found
[    1.142217] hub 4-0:1.0: 2 ports detected
[    1.142296] uhci_hcd: USB Universal Host Controller Interface driver
[    1.142459] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.142804] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.142816] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.142930] mice: PS/2 mouse device common for all mice
[    1.143099] rtc_cmos 00:02: RTC can wake from S4
[    1.143166] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.143199] rtc0: alarms up to one month, 114 bytes nvram
[    1.143385] device-mapper: uevent: version 1.0.3
[    1.143581] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.143745] device-mapper: multipath: version 1.1.0 loaded
[    1.143751] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.144071] EISA: Probing bus 0 at eisa.0
[    1.144113] EISA: Detected 0 cards.
[    1.144542] cpuidle: using governor ladder
[    1.144547] cpuidle: using governor menu
[    1.145367] TCP cubic registered
[    1.145578] NET: Registered protocol family 10
[    1.146327] lo: Disabled Privacy Extensions
[    1.146837] NET: Registered protocol family 17
[    1.146893] Bluetooth: L2CAP ver 2.13
[    1.146896] Bluetooth: L2CAP socket layer initialized
[    1.146900] Bluetooth: SCO (Voice Link) ver 0.6
[    1.146903] Bluetooth: SCO socket layer initialized
[    1.146977] ata3.00: configured for UDMA/33
[    1.147067] Bluetooth: RFCOMM TTY layer initialized
[    1.147074] Bluetooth: RFCOMM socket layer initialized
[    1.147077] Bluetooth: RFCOMM ver 1.11
[    1.147134] Using IPI No-Shortcut mode
[    1.147269] PM: Resume from disk failed.
[    1.147292] registered taskstats version 1
[    1.147425]   Magic number: 2:265:84
[    1.147516] rtc_cmos 00:02: setting system clock to 2010-03-29 15:04:43 UTC (1269875083)
[    1.147523] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.147525] EDD information not available.
[    1.159368] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.280065] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.288581] ata1.00: ATA-8: WDC WD5000AAKS-22A7B0, 01.03B01, max UDMA/133
[    1.288587] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.304667] ata1.00: configured for UDMA/133
[    1.304853] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
[    1.305090] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.305190] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.305279] sd 0:0:0:0: [sda] Write Protect is off
[    1.305285] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.305328] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.305593]  sda: sda1 sda2
[    1.317608] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.624077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.632241] ata2.00: ATA-7: WDC WD2000JS-00MHB0, 02.01C03, max UDMA/133
[    1.632246] ata2.00: 390721968 sectors, multi 16: LBA48 
[    1.640289] ata2.00: configured for UDMA/133
[    1.640452] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2000JS-00M 02.0 PQ: 0 ANSI: 5
[    1.640669] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.640763] sd 1:0:0:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.640857] sd 1:0:0:0: [sdb] Write Protect is off
[    1.640862] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.640910] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.641171]  sdb:
[    1.641417] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    1.641623] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.641714] sd 2:0:0:0: [sdc] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.641807] sd 2:0:0:0: [sdc] Write Protect is off
[    1.641812] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.641863] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.642136]  sdc:
[    1.644038] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.654325]  sdc1 sdc3
[    1.654804] sd 2:0:0:0: [sdc] Attached SCSI disk
[    1.661351]  sdb1 sdb2 < sdb5 >
[    1.679248] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.812274] ata4.00: ATAPI: HL-DT-ST RW/DVD GCC-4521B, 1.05, max UDMA/33
[    1.812334] ata4.01: ATAPI: HL-DT-ST DVDRAM GSA-H10A, JL01, max UDMA/33
[    1.828301] ata4.00: configured for UDMA/33
[    1.844301] ata4.01: configured for UDMA/33
[    1.847194] scsi 3:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4521B 1.05 PQ: 0 ANSI: 5
[    1.848931] usb 3-2: configuration #1 chosen from 1 choice
[    1.849213] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    1.849220] Uniform CD-ROM driver Revision: 3.20
[    1.849395] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.849489] sr 3:0:0:0: Attached scsi generic sg3 type 5
[    1.853261] scsi 3:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL01 PQ: 0 ANSI: 5
[    1.865673] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.865842] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.865940] sr 3:0:1:0: Attached scsi generic sg4 type 5
[    1.865993] Freeing unused kernel memory: 544k freed
[    1.866514] Write protecting the kernel text: 4584k
[    1.866554] Write protecting the kernel read-only data: 1840k
[    2.170503] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    2.190533] Linux agpgart interface v0.103
[    2.195118] agpgart-sis 0000:00:00.0: SiS chipset [1039/0655]
[    2.215804] Floppy drive(s): fd0 is 1.44M
[    2.268535] FDC 0 is a post-1991 82077
[    2.417218] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    2.444060] usb 2-2: configuration #1 chosen from 1 choice
[    2.446914] hub 2-2:1.0: USB hub found
[    2.448478] [drm] Initialized drm 1.1.0 20060810
[    2.456131] hub 2-2:1.0: 4 ports detected
[    2.524698] [drm] radeon default to kernel modesetting DISABLED.
[    2.525077] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.525329] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    2.531559] sis900.c: v1.08.10 Apr. 2 2006
[    2.531623]   alloc irq_desc for 19 on node -1
[    2.531628]   alloc kstat_irqs on node -1
[    2.531639] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.541806] usbcore: registered new interface driver hiddev
[    2.541884] usbcore: registered new interface driver usbhid
[    2.541890] usbhid: v2.6:USB HID core driver
[    2.542976] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    2.554814] 0000:00:04.0: Using transceiver found at address 1 as default
[    2.558155] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:11:d8:f7:64:17
[    2.792037] usb 2-2.1: new full speed USB device using ohci_hcd and address 3
[    3.008181] usb 2-2.1: configuration #1 chosen from 1 choice
[    3.108018] usb 2-2.3: new full speed USB device using ohci_hcd and address 4
[    3.243501] usb 2-2.3: configuration #1 chosen from 1 choice
[    3.256932] Initializing USB Mass Storage driver...
[    3.259398] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.259755] usbcore: registered new interface driver usb-storage
[    3.259762] USB Mass Storage support registered.
[    3.260332] usb-storage: device found at 4
[    3.260347] usb-storage: waiting for device to settle before scanning
[    3.319137] xor: automatically using best checksumming function: pIII_sse
[    3.336009]    pIII_sse  :  3649.000 MB/sec
[    3.336014] xor: using function: pIII_sse (3649.000 MB/sec)
[    3.341048] device-mapper: dm-raid45: initialized v0.2594b
[    4.126839] PM: Starting manual resume from disk
[    4.126847] PM: Resume from partition 8:21
[    4.126850] PM: Checking hibernation image.
[    4.127089] PM: Resume from disk failed.
[    4.208118] kjournald starting.  Commit interval 5 seconds
[    4.208146] EXT3-fs: mounted filesystem with ordered data mode.
[    5.608450] type=1505 audit(1269875087.960:2): operation="profile_load" pid=384 name=/usr/share/gdm/guest-session/Xsession
[    5.631614] type=1505 audit(1269875087.980:3): operation="profile_load" pid=385 name=/sbin/dhclient3
[    5.632624] type=1505 audit(1269875087.984:4): operation="profile_load" pid=385 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.633133] type=1505 audit(1269875087.984:5): operation="profile_load" pid=385 name=/usr/lib/connman/scripts/dhclient-script
[    5.683899] type=1505 audit(1269875088.032:6): operation="profile_load" pid=386 name=/usr/bin/evince
[    5.699118] type=1505 audit(1269875088.048:7): operation="profile_load" pid=386 name=/usr/bin/evince-previewer
[    5.715095] type=1505 audit(1269875088.064:8): operation="profile_load" pid=386 name=/usr/bin/evince-thumbnailer
[    5.739166] type=1505 audit(1269875088.088:9): operation="profile_load" pid=388 name=/usr/bin/freshclam
[    5.752885] type=1505 audit(1269875088.104:10): operation="profile_load" pid=389 name=/usr/lib/cups/backend/cups-pdf
[    5.753985] type=1505 audit(1269875088.104:11): operation="profile_load" pid=389 name=/usr/sbin/cupsd
[    6.953996] Adding 2104472k swap on /dev/sdb5.  Priority:-1 extents:1 across:2104472k 
[    7.652523] EXT3 FS on sdc1, internal journal
[    8.261856] usb-storage: device scan complete
[    8.276840] scsi 4:0:0:0: Direct-Access     IC       USB Storage-CFC  322E PQ: 0 ANSI: 0 CCS
[    8.283821] scsi 4:0:0:1: Direct-Access     IC       USB Storage-SMC  322E PQ: 0 ANSI: 0 CCS
[    8.289634] udev: starting version 147
[    8.291893] scsi 4:0:0:2: Direct-Access     IC       USB Storage-MMC  322E PQ: 0 ANSI: 0 CCS
[    8.298926] scsi 4:0:0:3: Direct-Access     IC       USB Storage-MSC  322E PQ: 0 ANSI: 0 CCS
[    8.299700] sd 4:0:0:0: Attached scsi generic sg5 type 0
[    8.299890] sd 4:0:0:1: Attached scsi generic sg6 type 0
[    8.300096] sd 4:0:0:2: Attached scsi generic sg7 type 0
[    8.300274] sd 4:0:0:3: Attached scsi generic sg8 type 0
[    8.368792] sd 4:0:0:2: [sdf] Attached SCSI removable disk
[    8.382828] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[    8.393801] sd 4:0:0:1: [sde] Attached SCSI removable disk
[    8.404768] sd 4:0:0:3: [sdg] Attached SCSI removable disk
[    8.650309] kjournald starting.  Commit interval 5 seconds
[    8.651066] EXT3 FS on sda1, internal journal
[    8.651079] EXT3-fs: mounted filesystem with ordered data mode.
[    8.709682] kjournald starting.  Commit interval 5 seconds
[    8.715131] EXT3 FS on sdb1, internal journal
[    8.715145] EXT3-fs: mounted filesystem with ordered data mode.
[    9.793163] kjournald starting.  Commit interval 5 seconds
[    9.793526] EXT3 FS on sda2, internal journal
[    9.793537] EXT3-fs: mounted filesystem with ordered data mode.
[   10.248316] lp: driver loaded but no devices found
[   10.521717] psmouse serio1: ID: 10 00 64
[   10.579528] logips2pp: Detected unknown logitech mouse model 127
[   10.765526] lirc_dev: IR Remote Control driver registered, major 61 
[   11.050192] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
[   11.050237] lirc_dev: lirc_register_driver: sample_rate: 0
[   11.050330] lirc_imon: Registered iMON driver (lirc minor: 0)
[   11.050410] input: iMON PAD IR Mouse (15c2:0043) as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input4
[   11.069122] lirc_imon: iMON device (15c2:0043, intf0) on usb<3:2> initialized
[   11.072314] lirc_imon: iMON device (15c2:0043, intf1) on usb<3:2> initialized
[   11.072394] usbcore: registered new interface driver lirc_imon
[   11.080166] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.092763] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   11.455782] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.113249] kjournald starting.  Commit interval 5 seconds
[   12.113650] EXT3 FS on sdc3, internal journal
[   12.113660] EXT3-fs: mounted filesystem with ordered data mode.
[   12.132717] Linux video capture interface: v2.00
[   12.736499] cx18:  Start initialization, version 1.2.0
[   12.736566] cx18-0: Initializing card 0
[   12.736573] cx18-0: Autodetected Hauppauge card
[   12.736720] cx18 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.738160] cx18-0: cx23418 revision 01010000 (B)
[   12.963786] tveeprom 0-0050: Hauppauge model 74541, rev C6B6, serial# 3432282
[   12.963793] tveeprom 0-0050: MAC address is 00-0D-FE-34-5F-5A
[   12.963798] tveeprom 0-0050: tuner model is Philips FM1236 MK5 (idx 116, type 43)
[   12.963803] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   12.963807] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   12.963811] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   12.963814] tveeprom 0-0050: has radio
[   12.963818] cx18-0: Autodetected Hauppauge HVR-1600
[   12.963822] cx18-0: Simultaneous Digital and Analog TV capture supported
[   13.061060] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.564747] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   13.742055] tda9887 1-0043: creating new instance
[   13.742061] tda9887 1-0043: tda988[5/6/7] found
[   13.746617] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   13.938116] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   14.156756] tuner-simple 1-0061: creating new instance
[   14.156764] tuner-simple 1-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   14.158885] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   14.158893] DVB: registering new adapter (cx18)
[   14.753244] MXL5005S: Attached at address 0x63
[   14.753256] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   14.753418] cx18-0: DVB Frontend registered
[   14.753424] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   14.753481] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   14.753532] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   14.753583] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   14.753639] cx18-0: Registered device radio0 for encoder radio
[   14.753645] cx18-0: Initialized card: Hauppauge HVR-1600
[   14.753699] cx18:  End initialization
[   14.755981]   alloc irq_desc for 18 on node -1
[   14.755987]   alloc kstat_irqs on node -1
[   14.756037] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   14.932065] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-cpu.fw
[   15.263451] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   15.284992] intel8x0_measure_ac97_clock: measured 161189 usecs (7743 samples)
[   15.284998] intel8x0: clocking to 48000
[   15.324747] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-apu.fw
[   15.899365] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   15.905713] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   16.140116] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-cpu.fw
[   16.270058] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-apu.fw
[   16.573915] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-dig.fw
[   16.961936] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   16.980212] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   20.173721] __ratelimit: 9 callbacks suppressed
[   20.173727] type=1505 audit(1269875102.524:15): operation="profile_replace" pid=1070 name=/usr/share/gdm/guest-session/Xsession
[   20.178290] type=1505 audit(1269875102.528:16): operation="profile_replace" pid=1071 name=/sbin/dhclient3
[   20.179235] type=1505 audit(1269875102.528:17): operation="profile_replace" pid=1071 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   20.179741] type=1505 audit(1269875102.528:18): operation="profile_replace" pid=1071 name=/usr/lib/connman/scripts/dhclient-script
[   20.192205] type=1505 audit(1269875102.544:19): operation="profile_replace" pid=1072 name=/usr/bin/evince
[   20.208242] type=1505 audit(1269875102.560:20): operation="profile_replace" pid=1072 name=/usr/bin/evince-previewer
[   20.218224] type=1505 audit(1269875102.568:21): operation="profile_replace" pid=1072 name=/usr/bin/evince-thumbnailer
[   20.235726] type=1505 audit(1269875102.584:22): operation="profile_replace" pid=1074 name=/usr/bin/freshclam
[   20.240244] type=1505 audit(1269875102.592:23): operation="profile_replace" pid=1075 name=/usr/lib/cups/backend/cups-pdf
[   20.241358] type=1505 audit(1269875102.592:24): operation="profile_replace" pid=1075 name=/usr/sbin/cupsd
[   22.129151] eth0: Media Link On 100mbps full-duplex 
[   22.775008] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   22.775249] usbcore: registered new interface driver btusb
[   23.365464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.365472] Bluetooth: BNEP filters: protocol multicast
[   23.436630] Bridge firewalling registered
[   26.016742] __ratelimit: 9 callbacks suppressed
[   26.016748] type=1503 audit(1269875108.368:28): operation="open" pid=1330 parent=1329 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.735506] type=1503 audit(1269875110.084:29): operation="open" pid=1389 parent=1388 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.095246] type=1503 audit(1269875111.444:30): operation="open" pid=1545 parent=1399 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.242244] type=1503 audit(1269875111.592:31): operation="open" pid=1555 parent=1554 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   30.196018] eth0: no IPv6 routers present
[   30.271015] type=1503 audit(1269875112.620:32): operation="open" pid=1591 parent=1590 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   31.319359] type=1503 audit(1269875113.668:33): operation="open" pid=1611 parent=1610 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.356882] type=1503 audit(1269875114.708:34): operation="open" pid=1654 parent=1653 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   33.383970] type=1503 audit(1269875115.732:35): operation="open" pid=1675 parent=1674 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   34.563382] type=1503 audit(1269875116.912:36): operation="open" pid=1694 parent=1693 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   34.735867] type=1503 audit(1269875117.084:37): operation="open" pid=1705 parent=1704 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   36.802842] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   36.802871] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[   36.802883] agpgart-sis 0000:00:00.0: putting AGP V3 device into 8x mode
[   36.804906] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   37.017757] [drm] Setting GART location based on new memory map
[   37.032656] [drm] Loading RV670 CP Microcode
[   37.032980] [drm] Loading RV670 PFP Microcode
[   37.047929] [drm] Resetting GPU
[   37.047990] [drm] writeback test succeeded in 1 usecs
[   40.321131] ppdev: user-space parallel port driver
[   53.909503] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[   61.889859] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[   69.889247] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[   77.889635] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[   85.890024] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[   93.889413] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[  101.889802] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[  109.889192] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
[16651.556019] usb 1-7: new high speed USB device using ehci_hcd and address 4
[16651.689965] usb 1-7: configuration #1 chosen from 1 choice
[16651.692557] scsi5 : SCSI emulation for USB Mass Storage devices
[16651.692790] usb-storage: device found at 4
[16651.692794] usb-storage: waiting for device to settle before scanning
[16656.692628] usb-storage: device scan complete
[16656.693357] scsi 5:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
[16656.694168] sd 5:0:0:0: Attached scsi generic sg9 type 0
[16656.720104] sd 5:0:0:0: [sdh] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[16656.720690] sd 5:0:0:0: [sdh] Write Protect is off
[16656.720695] sd 5:0:0:0: [sdh] Mode Sense: 00 00 00 00
[16656.720699] sd 5:0:0:0: [sdh] Assuming drive cache: write through
[16656.725973] sd 5:0:0:0: [sdh] Assuming drive cache: write through
[16656.725986]  sdh: sdh1
[16656.999895] sd 5:0:0:0: [sdh] Assuming drive cache: write through
[16656.999907] sd 5:0:0:0: [sdh] Attached SCSI removable disk
[16734.786807] usb 1-7: USB disconnect, address 4
```

/var/log/messages

```
Mar 29 11:00:55 ATG-Prime kernel: Kernel logging (proc) stopped.
Mar 29 11:04:56 ATG-Prime kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 29 11:04:56 ATG-Prime rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="812" x-info="http://www.rsyslog.com"] (re)start
Mar 29 11:04:56 ATG-Prime rsyslogd: rsyslogd's groupid changed to 102
Mar 29 11:04:57 ATG-Prime rsyslogd: rsyslogd's userid changed to 101
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] KERNEL supported cpus:
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   Intel GenuineIntel
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   AMD AuthenticAMD
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   NSC Geode by NSC
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   Cyrix CyrixInstead
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   Centaur CentaurHauls
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   UMC UMC UMC UMC
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] DMI 2.3 present.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] last_pfn = 0x3ffb0 max_arch_pfn = 0x100000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] modified physical RAM map:
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 0000000000100000 - 000000003ffb0000 (usable)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] RAMDISK: 2f858000 - 300036d0
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: RSDP 000fb470 00021 (v02 ACPIAM)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: XSDT 3ffb0100 0003C (v01 A M I  OEMXSDT  06000615 MSFT 00000097)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: FACP 3ffb0290 000F4 (v03 A M I  OEMFACP  06000615 MSFT 00000097)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: DSDT 3ffb03f0 03391 (v01  A0149 A0149001 00000001 INTL 02002026)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: FACS 3ffc0000 00040
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: APIC 3ffb0390 0005C (v01 A M I  OEMAPIC  06000615 MSFT 00000097)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: OEMB 3ffc0040 00040 (v01 A M I  AMI_OEM  06000615 MSFT 00000097)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] 135MB HIGHMEM available.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] 887MB LOWMEM available.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #3 [0000100000 - 00008ae160]    TEXT DATA BSS ==> [0000100000 - 00008ae160]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #4 [002f858000 - 00300036d0]          RAMDISK ==> [002f858000 - 00300036d0]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #6 [00008af000 - 00008b222c]              BRK ==> [00008af000 - 00008b222c]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Zone PFN ranges:
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003ffb0
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Movable zone start PFN for each node
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]     0: 0x00000100 -> 0x0003ffb0
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Using APIC driver default
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf780000)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259903
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=5021019d-82eb-4a23-bc8e-d09da0c0dd99 ro quiet splash
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Initializing CPU#0
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] allocated 5240960 bytes of page_cgroup
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003ffb0)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Memory: 1017220k/1048256k available (4583k kernel code, 29996k reserved, 2142k data, 544k init, 138952k highmem)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] virtual kernel memory layout:
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]       .init : 0xc0792000 - 0xc081a000   ( 544 kB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]       .data : 0xc0579d78 - 0xc0791848   (2142 kB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000]       .text : 0xc0100000 - 0xc0579d78   (4583 kB)
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Fast TSC calibration using PIT
Mar 29 11:04:57 ATG-Prime kernel: [    0.000000] Detected 2400.899 MHz processor.
Mar 29 11:04:57 ATG-Prime kernel: [    0.001484] Console: colour VGA+ 80x25
Mar 29 11:04:57 ATG-Prime kernel: [    0.001489] console [tty0] enabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.001549] Calibrating delay loop (skipped), value calculated using timer frequency.. 4801.79 BogoMIPS (lpj=9603596)
Mar 29 11:04:57 ATG-Prime kernel: [    0.001580] Security Framework initialized
Mar 29 11:04:57 ATG-Prime kernel: [    0.001609] AppArmor: AppArmor initialized
Mar 29 11:04:57 ATG-Prime kernel: [    0.001621] Mount-cache hash table entries: 512
Mar 29 11:04:57 ATG-Prime kernel: [    0.001827] Initializing cgroup subsys ns
Mar 29 11:04:57 ATG-Prime kernel: [    0.001837] Initializing cgroup subsys cpuacct
Mar 29 11:04:57 ATG-Prime kernel: [    0.001844] Initializing cgroup subsys memory
Mar 29 11:04:57 ATG-Prime kernel: [    0.001854] Initializing cgroup subsys devices
Mar 29 11:04:57 ATG-Prime kernel: [    0.001858] Initializing cgroup subsys freezer
Mar 29 11:04:57 ATG-Prime kernel: [    0.001862] Initializing cgroup subsys net_cls
Mar 29 11:04:57 ATG-Prime kernel: [    0.001890] CPU: Trace cache: 12K uops, L1 D cache: 16K
Mar 29 11:04:57 ATG-Prime kernel: [    0.001895] CPU: L2 cache: 256K
Mar 29 11:04:57 ATG-Prime kernel: [    0.001899] CPU: Hyper-Threading is disabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.001905] mce: CPU supports 4 MCE banks
Mar 29 11:04:57 ATG-Prime kernel: [    0.001922] CPU0: Thermal monitoring enabled (TM1)
Mar 29 11:04:57 ATG-Prime kernel: [    0.001929] using mwait in idle threads.
Mar 29 11:04:57 ATG-Prime kernel: [    0.001939] Performance Counters: no PMU driver, software counters only.
Mar 29 11:04:57 ATG-Prime kernel: [    0.001950] Checking 'hlt' instruction... OK.
Mar 29 11:04:57 ATG-Prime kernel: [    0.017243] SMP alternatives: switching to UP code
Mar 29 11:04:57 ATG-Prime kernel: [    0.028017] ACPI: Core revision 20090521
Mar 29 11:04:57 ATG-Prime kernel: [    0.040910] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 29 11:04:57 ATG-Prime kernel: [    0.080608] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 04
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] Brought up 1 CPUs
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] Total of 1 processors activated (4801.79 BogoMIPS).
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] ASUS P4S800 series board detected. Selecting BIOS-method for reboots.
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] Booting paravirtualized kernel on bare hardware
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] regulator: core version 0.5
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] Time: 15:04:42  Date: 03/29/10
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] NET: Registered protocol family 16
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] EISA bus registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] ACPI: bus type pci registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Mar 29 11:04:57 ATG-Prime kernel: [    0.084001] PCI: Using configuration type 1 for base access
Mar 29 11:04:57 ATG-Prime kernel: [    0.084687] bio: create slab <bio-0> at 0
Mar 29 11:04:57 ATG-Prime kernel: [    0.097218] ACPI: Interpreter enabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.097240] ACPI: (supports S0 S1 S3 S4 S5)
Mar 29 11:04:57 ATG-Prime kernel: [    0.097281] ACPI: Using IOAPIC for interrupt routing
Mar 29 11:04:57 ATG-Prime kernel: [    0.107798] ACPI Warning: Incorrect checksum in table [OEMB] - E7, should be DE 20090521 tbutils-246
Mar 29 11:04:57 ATG-Prime kernel: [    0.107927] ACPI: No dock devices found.
Mar 29 11:04:57 ATG-Prime kernel: [    0.108169] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 29 11:04:57 ATG-Prime kernel: [    0.108548] pci 0000:00:02.5: PME# supported from D3cold
Mar 29 11:04:57 ATG-Prime kernel: [    0.108555] pci 0000:00:02.5: PME# disabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.108670] pci 0000:00:02.7: PME# supported from D3hot D3cold
Mar 29 11:04:57 ATG-Prime kernel: [    0.108676] pci 0000:00:02.7: PME# disabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.108987] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Mar 29 11:04:57 ATG-Prime kernel: [    0.108994] pci 0000:00:03.3: PME# disabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.109118] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 29 11:04:57 ATG-Prime kernel: [    0.109124] pci 0000:00:04.0: PME# disabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.118509] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.118698] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.118869] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.119040] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.119211] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.119384] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.119557] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.119730] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
Mar 29 11:04:57 ATG-Prime kernel: [    0.120088] SCSI subsystem initialized
Mar 29 11:04:57 ATG-Prime kernel: [    0.120356] usbcore: registered new interface driver usbfs
Mar 29 11:04:57 ATG-Prime kernel: [    0.120378] usbcore: registered new interface driver hub
Mar 29 11:04:57 ATG-Prime kernel: [    0.120430] usbcore: registered new device driver usb
Mar 29 11:04:57 ATG-Prime kernel: [    0.120683] ACPI: WMI: Mapper loaded
Mar 29 11:04:57 ATG-Prime kernel: [    0.120687] PCI: Using ACPI for IRQ routing
Mar 29 11:04:57 ATG-Prime kernel: [    0.120911] Bluetooth: Core ver 2.15
Mar 29 11:04:57 ATG-Prime kernel: [    0.120997] NET: Registered protocol family 31
Mar 29 11:04:57 ATG-Prime kernel: [    0.121001] Bluetooth: HCI device and connection manager initialized
Mar 29 11:04:57 ATG-Prime kernel: [    0.121005] Bluetooth: HCI socket layer initialized
Mar 29 11:04:57 ATG-Prime kernel: [    0.121009] NetLabel: Initializing
Mar 29 11:04:57 ATG-Prime kernel: [    0.121011] NetLabel:  domain hash size = 128
Mar 29 11:04:57 ATG-Prime kernel: [    0.121013] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 29 11:04:57 ATG-Prime kernel: [    0.121035] NetLabel:  unlabeled traffic allowed by default
Mar 29 11:04:57 ATG-Prime kernel: [    0.123977] pnp: PnP ACPI init
Mar 29 11:04:57 ATG-Prime kernel: [    0.124049] ACPI: bus type pnp registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.129158] pnp: PnP ACPI: found 13 devices
Mar 29 11:04:57 ATG-Prime kernel: [    0.129163] ACPI: ACPI bus type pnp unregistered
Mar 29 11:04:57 ATG-Prime kernel: [    0.129171] PnPBIOS: Disabled by ACPI PNP
Mar 29 11:04:57 ATG-Prime kernel: [    0.129197] system 00:08: ioport range 0x680-0x6ff has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129202] system 00:08: ioport range 0x290-0x297 has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129212] system 00:09: ioport range 0x480-0x48f has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129217] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129221] system 00:09: ioport range 0x800-0x8df has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129225] system 00:09: ioport range 0x8e0-0x8ff has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129231] system 00:09: iomem range 0xffe80000-0xffefffff has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129241] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129246] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129250] system 00:0a: iomem range 0xfff80000-0xffffffff has been reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129259] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129264] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129268] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.129273] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
Mar 29 11:04:57 ATG-Prime kernel: [    0.164037] AppArmor: AppArmor Filesystem Enabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.164073] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 29 11:04:57 ATG-Prime kernel: [    0.164079] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
Mar 29 11:04:57 ATG-Prime kernel: [    0.164088] pci 0000:00:01.0:   MEM window: 0xf6a00000-0xf6afffff
Mar 29 11:04:57 ATG-Prime kernel: [    0.164094] pci 0000:00:01.0:   PREFETCH window: 0xbff00000-0xdfefffff
Mar 29 11:04:57 ATG-Prime kernel: [    0.164192] NET: Registered protocol family 2
Mar 29 11:04:57 ATG-Prime kernel: [    0.164344] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.164869] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.165676] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.166094] TCP: Hash tables configured (established 131072 bind 65536)
Mar 29 11:04:57 ATG-Prime kernel: [    0.166101] TCP reno registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.166292] NET: Registered protocol family 1
Mar 29 11:04:57 ATG-Prime kernel: [    0.166401] Trying to unpack rootfs image as initramfs...
Mar 29 11:04:57 ATG-Prime kernel: [    0.501423] Freeing initrd memory: 7853k freed
Mar 29 11:04:57 ATG-Prime kernel: [    0.509380] cpufreq-nforce2: No nForce2 chipset.
Mar 29 11:04:57 ATG-Prime kernel: [    0.509428] Scanning for low memory corruption every 60 seconds
Mar 29 11:04:57 ATG-Prime kernel: [    0.509590] audit: initializing netlink socket (disabled)
Mar 29 11:04:57 ATG-Prime kernel: [    0.509615] type=2000 audit(1269875082.507:1): initialized
Mar 29 11:04:57 ATG-Prime kernel: [    0.520891] highmem bounce pool size: 64 pages
Mar 29 11:04:57 ATG-Prime kernel: [    0.520905] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 29 11:04:57 ATG-Prime kernel: [    0.523001] VFS: Disk quotas dquot_6.5.2
Mar 29 11:04:57 ATG-Prime kernel: [    0.523113] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [    0.524037] fuse init (API version 7.12)
Mar 29 11:04:57 ATG-Prime kernel: [    0.524195] msgmni has been set to 1731
Mar 29 11:04:57 ATG-Prime kernel: [    0.524587] alg: No test for stdrng (krng)
Mar 29 11:04:57 ATG-Prime kernel: [    0.524617] io scheduler noop registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.524620] io scheduler anticipatory registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.524623] io scheduler deadline registered
Mar 29 11:04:57 ATG-Prime kernel: [    0.524724] io scheduler cfq registered (default)
Mar 29 11:04:57 ATG-Prime kernel: [    0.596141] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 29 11:04:57 ATG-Prime kernel: [    0.596180] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 29 11:04:57 ATG-Prime kernel: [    0.596386] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 29 11:04:57 ATG-Prime kernel: [    0.596394] ACPI: Power Button [PWRF]
Mar 29 11:04:57 ATG-Prime kernel: [    0.596487] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Mar 29 11:04:57 ATG-Prime kernel: [    0.596493] ACPI: Power Button [PWRB]
Mar 29 11:04:57 ATG-Prime kernel: [    0.597062] processor LNXCPU:00: registered as cooling_device0
Mar 29 11:04:57 ATG-Prime kernel: [    0.597071] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 29 11:04:57 ATG-Prime kernel: [    0.600692] isapnp: Scanning for PnP cards...
Mar 29 11:04:57 ATG-Prime kernel: [    0.954617] isapnp: No Plug & Play device found
Mar 29 11:04:57 ATG-Prime kernel: [    0.956572] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 29 11:04:57 ATG-Prime kernel: [    0.956728] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 29 11:04:57 ATG-Prime kernel: [    0.957340] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 29 11:04:57 ATG-Prime kernel: [    0.958874] brd: module loaded
Mar 29 11:04:57 ATG-Prime kernel: [    0.959584] loop: module loaded
Mar 29 11:04:57 ATG-Prime kernel: [    0.959746] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Mar 29 11:04:57 ATG-Prime kernel: [    0.960075] sata_sis 0000:00:05.0: version 1.0
Mar 29 11:04:57 ATG-Prime kernel: [    0.960114] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 29 11:04:57 ATG-Prime kernel: [    0.960122] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
Mar 29 11:04:57 ATG-Prime kernel: [    0.960295] scsi0 : sata_sis
Mar 29 11:04:57 ATG-Prime kernel: [    0.960480] scsi1 : sata_sis
Mar 29 11:04:57 ATG-Prime kernel: [    0.960555] ata1: SATA max UDMA/133 cmd 0xeff0 ctl 0xefe4 bmdma 0xef90 irq 17
Mar 29 11:04:57 ATG-Prime kernel: [    0.960564] ata2: SATA max UDMA/133 cmd 0xefa8 ctl 0xefe0 bmdma 0xef98 irq 17
Mar 29 11:04:57 ATG-Prime kernel: [    0.961264] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 11:04:57 ATG-Prime kernel: [    0.961530] scsi2 : pata_sis
Mar 29 11:04:57 ATG-Prime kernel: [    0.961670] scsi3 : pata_sis
Mar 29 11:04:57 ATG-Prime kernel: [    0.962837] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Mar 29 11:04:57 ATG-Prime kernel: [    0.962843] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Mar 29 11:04:57 ATG-Prime kernel: [    0.963404] Fixed MDIO Bus: probed
Mar 29 11:04:57 ATG-Prime kernel: [    0.963476] PPP generic driver version 2.4.2
Mar 29 11:04:57 ATG-Prime kernel: [    0.963655] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 29 11:04:57 ATG-Prime kernel: [    0.963718] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Mar 29 11:04:57 ATG-Prime kernel: [    0.963743] ehci_hcd 0000:00:03.3: EHCI Host Controller
Mar 29 11:04:57 ATG-Prime kernel: [    0.963809] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Mar 29 11:04:57 ATG-Prime kernel: [    0.963879] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfebff000
Mar 29 11:04:57 ATG-Prime kernel: [    0.972014] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Mar 29 11:04:57 ATG-Prime kernel: [    0.972179] usb usb1: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    0.972232] hub 1-0:1.0: USB hub found
Mar 29 11:04:57 ATG-Prime kernel: [    0.972248] hub 1-0:1.0: 8 ports detected
Mar 29 11:04:57 ATG-Prime kernel: [    0.972346] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 29 11:04:57 ATG-Prime kernel: [    0.972405] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar 29 11:04:57 ATG-Prime kernel: [    0.972428] ohci_hcd 0000:00:03.0: OHCI Host Controller
Mar 29 11:04:57 ATG-Prime kernel: [    0.972513] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Mar 29 11:04:57 ATG-Prime kernel: [    0.972549] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfebfc000
Mar 29 11:04:57 ATG-Prime kernel: [    1.030130] usb usb2: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    1.030186] hub 2-0:1.0: USB hub found
Mar 29 11:04:57 ATG-Prime kernel: [    1.030202] hub 2-0:1.0: 3 ports detected
Mar 29 11:04:57 ATG-Prime kernel: [    1.030291] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 29 11:04:57 ATG-Prime kernel: [    1.030313] ohci_hcd 0000:00:03.1: OHCI Host Controller
Mar 29 11:04:57 ATG-Prime kernel: [    1.030399] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Mar 29 11:04:57 ATG-Prime kernel: [    1.030433] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfebfd000
Mar 29 11:04:57 ATG-Prime kernel: [    1.086125] usb usb3: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    1.086173] hub 3-0:1.0: USB hub found
Mar 29 11:04:57 ATG-Prime kernel: [    1.086190] hub 3-0:1.0: 3 ports detected
Mar 29 11:04:57 ATG-Prime kernel: [    1.086275] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Mar 29 11:04:57 ATG-Prime kernel: [    1.086297] ohci_hcd 0000:00:03.2: OHCI Host Controller
Mar 29 11:04:57 ATG-Prime kernel: [    1.086371] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
Mar 29 11:04:57 ATG-Prime kernel: [    1.086406] ohci_hcd 0000:00:03.2: irq 22, io mem 0xfebfe000
Mar 29 11:04:57 ATG-Prime kernel: [    1.128484] ata3.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
Mar 29 11:04:57 ATG-Prime kernel: [    1.128489] ata3.00: 160086528 sectors, multi 16: LBA 
Mar 29 11:04:57 ATG-Prime kernel: [    1.128529] ata3.00: limited to UDMA/33 due to 40-wire cable
Mar 29 11:04:57 ATG-Prime kernel: [    1.142144] usb usb4: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    1.142195] hub 4-0:1.0: USB hub found
Mar 29 11:04:57 ATG-Prime kernel: [    1.142217] hub 4-0:1.0: 2 ports detected
Mar 29 11:04:57 ATG-Prime kernel: [    1.142296] uhci_hcd: USB Universal Host Controller Interface driver
Mar 29 11:04:57 ATG-Prime kernel: [    1.142459] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Mar 29 11:04:57 ATG-Prime kernel: [    1.142804] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 29 11:04:57 ATG-Prime kernel: [    1.142816] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 29 11:04:57 ATG-Prime kernel: [    1.142930] mice: PS/2 mouse device common for all mice
Mar 29 11:04:57 ATG-Prime kernel: [    1.143099] rtc_cmos 00:02: RTC can wake from S4
Mar 29 11:04:57 ATG-Prime kernel: [    1.143166] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Mar 29 11:04:57 ATG-Prime kernel: [    1.143199] rtc0: alarms up to one month, 114 bytes nvram
Mar 29 11:04:57 ATG-Prime kernel: [    1.143385] device-mapper: uevent: version 1.0.3
Mar 29 11:04:57 ATG-Prime kernel: [    1.143581] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Mar 29 11:04:57 ATG-Prime kernel: [    1.143745] device-mapper: multipath: version 1.1.0 loaded
Mar 29 11:04:57 ATG-Prime kernel: [    1.143751] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 29 11:04:57 ATG-Prime kernel: [    1.144071] EISA: Probing bus 0 at eisa.0
Mar 29 11:04:57 ATG-Prime kernel: [    1.144113] EISA: Detected 0 cards.
Mar 29 11:04:57 ATG-Prime kernel: [    1.144542] cpuidle: using governor ladder
Mar 29 11:04:57 ATG-Prime kernel: [    1.144547] cpuidle: using governor menu
Mar 29 11:04:57 ATG-Prime kernel: [    1.145367] TCP cubic registered
Mar 29 11:04:57 ATG-Prime kernel: [    1.145578] NET: Registered protocol family 10
Mar 29 11:04:57 ATG-Prime kernel: [    1.146327] lo: Disabled Privacy Extensions
Mar 29 11:04:57 ATG-Prime kernel: [    1.146837] NET: Registered protocol family 17
Mar 29 11:04:57 ATG-Prime kernel: [    1.146893] Bluetooth: L2CAP ver 2.13
Mar 29 11:04:57 ATG-Prime kernel: [    1.146896] Bluetooth: L2CAP socket layer initialized
Mar 29 11:04:57 ATG-Prime kernel: [    1.146900] Bluetooth: SCO (Voice Link) ver 0.6
Mar 29 11:04:57 ATG-Prime kernel: [    1.146903] Bluetooth: SCO socket layer initialized
Mar 29 11:04:57 ATG-Prime kernel: [    1.146977] ata3.00: configured for UDMA/33
Mar 29 11:04:57 ATG-Prime kernel: [    1.147067] Bluetooth: RFCOMM TTY layer initialized
Mar 29 11:04:57 ATG-Prime kernel: [    1.147074] Bluetooth: RFCOMM socket layer initialized
Mar 29 11:04:57 ATG-Prime kernel: [    1.147077] Bluetooth: RFCOMM ver 1.11
Mar 29 11:04:57 ATG-Prime kernel: [    1.147134] Using IPI No-Shortcut mode
Mar 29 11:04:57 ATG-Prime kernel: [    1.147292] registered taskstats version 1
Mar 29 11:04:57 ATG-Prime kernel: [    1.147425]   Magic number: 2:265:84
Mar 29 11:04:57 ATG-Prime kernel: [    1.147516] rtc_cmos 00:02: setting system clock to 2010-03-29 15:04:43 UTC (1269875083)
Mar 29 11:04:57 ATG-Prime kernel: [    1.147523] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 29 11:04:57 ATG-Prime kernel: [    1.147525] EDD information not available.
Mar 29 11:04:57 ATG-Prime kernel: [    1.159368] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Mar 29 11:04:57 ATG-Prime kernel: [    1.280065] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 29 11:04:57 ATG-Prime kernel: [    1.288581] ata1.00: ATA-8: WDC WD5000AAKS-22A7B0, 01.03B01, max UDMA/133
Mar 29 11:04:57 ATG-Prime kernel: [    1.288587] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 29 11:04:57 ATG-Prime kernel: [    1.304667] ata1.00: configured for UDMA/133
Mar 29 11:04:57 ATG-Prime kernel: [    1.304853] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.305090] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    1.305190] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Mar 29 11:04:57 ATG-Prime kernel: [    1.305279] sd 0:0:0:0: [sda] Write Protect is off
Mar 29 11:04:57 ATG-Prime kernel: [    1.305328] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 29 11:04:57 ATG-Prime kernel: [    1.305593]  sda: sda1 sda2
Mar 29 11:04:57 ATG-Prime kernel: [    1.317608] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 29 11:04:57 ATG-Prime kernel: [    1.624077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 29 11:04:57 ATG-Prime kernel: [    1.632241] ata2.00: ATA-7: WDC WD2000JS-00MHB0, 02.01C03, max UDMA/133
Mar 29 11:04:57 ATG-Prime kernel: [    1.632246] ata2.00: 390721968 sectors, multi 16: LBA48 
Mar 29 11:04:57 ATG-Prime kernel: [    1.640289] ata2.00: configured for UDMA/133
Mar 29 11:04:57 ATG-Prime kernel: [    1.640452] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2000JS-00M 02.0 PQ: 0 ANSI: 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.640669] sd 1:0:0:0: Attached scsi generic sg1 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    1.640763] sd 1:0:0:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
Mar 29 11:04:57 ATG-Prime kernel: [    1.640857] sd 1:0:0:0: [sdb] Write Protect is off
Mar 29 11:04:57 ATG-Prime kernel: [    1.640910] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 29 11:04:57 ATG-Prime kernel: [    1.641171]  sdb:
Mar 29 11:04:57 ATG-Prime kernel: [    1.641417] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.641623] sd 2:0:0:0: Attached scsi generic sg2 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    1.641714] sd 2:0:0:0: [sdc] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
Mar 29 11:04:57 ATG-Prime kernel: [    1.641807] sd 2:0:0:0: [sdc] Write Protect is off
Mar 29 11:04:57 ATG-Prime kernel: [    1.641863] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 29 11:04:57 ATG-Prime kernel: [    1.642136]  sdc:
Mar 29 11:04:57 ATG-Prime kernel: [    1.644038] usb 3-2: new low speed USB device using ohci_hcd and address 2
Mar 29 11:04:57 ATG-Prime kernel: [    1.654325]  sdc1 sdc3
Mar 29 11:04:57 ATG-Prime kernel: [    1.654804] sd 2:0:0:0: [sdc] Attached SCSI disk
Mar 29 11:04:57 ATG-Prime kernel: [    1.661351]  sdb1 sdb2 < sdb5 >
Mar 29 11:04:57 ATG-Prime kernel: [    1.679248] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar 29 11:04:57 ATG-Prime kernel: [    1.812274] ata4.00: ATAPI: HL-DT-ST RW/DVD GCC-4521B, 1.05, max UDMA/33
Mar 29 11:04:57 ATG-Prime kernel: [    1.812334] ata4.01: ATAPI: HL-DT-ST DVDRAM GSA-H10A, JL01, max UDMA/33
Mar 29 11:04:57 ATG-Prime kernel: [    1.828301] ata4.00: configured for UDMA/33
Mar 29 11:04:57 ATG-Prime kernel: [    1.844301] ata4.01: configured for UDMA/33
Mar 29 11:04:57 ATG-Prime kernel: [    1.847194] scsi 3:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4521B 1.05 PQ: 0 ANSI: 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.848931] usb 3-2: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    1.849213] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
Mar 29 11:04:57 ATG-Prime kernel: [    1.849220] Uniform CD-ROM driver Revision: 3.20
Mar 29 11:04:57 ATG-Prime kernel: [    1.849489] sr 3:0:0:0: Attached scsi generic sg3 type 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.853261] scsi 3:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL01 PQ: 0 ANSI: 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.865673] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 29 11:04:57 ATG-Prime kernel: [    1.865940] sr 3:0:1:0: Attached scsi generic sg4 type 5
Mar 29 11:04:57 ATG-Prime kernel: [    1.865993] Freeing unused kernel memory: 544k freed
Mar 29 11:04:57 ATG-Prime kernel: [    1.866514] Write protecting the kernel text: 4584k
Mar 29 11:04:57 ATG-Prime kernel: [    1.866554] Write protecting the kernel read-only data: 1840k
Mar 29 11:04:57 ATG-Prime kernel: [    2.170503] usb 2-2: new full speed USB device using ohci_hcd and address 2
Mar 29 11:04:57 ATG-Prime kernel: [    2.190533] Linux agpgart interface v0.103
Mar 29 11:04:57 ATG-Prime kernel: [    2.195118] agpgart-sis 0000:00:00.0: SiS chipset [1039/0655]
Mar 29 11:04:57 ATG-Prime kernel: [    2.215804] Floppy drive(s): fd0 is 1.44M
Mar 29 11:04:57 ATG-Prime kernel: [    2.268535] FDC 0 is a post-1991 82077
Mar 29 11:04:57 ATG-Prime kernel: [    2.417218] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Mar 29 11:04:57 ATG-Prime kernel: [    2.444060] usb 2-2: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    2.446914] hub 2-2:1.0: USB hub found
Mar 29 11:04:57 ATG-Prime kernel: [    2.448478] [drm] Initialized drm 1.1.0 20060810
Mar 29 11:04:57 ATG-Prime kernel: [    2.456131] hub 2-2:1.0: 4 ports detected
Mar 29 11:04:57 ATG-Prime kernel: [    2.524698] [drm] radeon default to kernel modesetting DISABLED.
Mar 29 11:04:57 ATG-Prime kernel: [    2.525077] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 11:04:57 ATG-Prime kernel: [    2.525329] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
Mar 29 11:04:57 ATG-Prime kernel: [    2.531559] sis900.c: v1.08.10 Apr. 2 2006
Mar 29 11:04:57 ATG-Prime kernel: [    2.531639] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 29 11:04:57 ATG-Prime kernel: [    2.541806] usbcore: registered new interface driver hiddev
Mar 29 11:04:57 ATG-Prime kernel: [    2.541884] usbcore: registered new interface driver usbhid
Mar 29 11:04:57 ATG-Prime kernel: [    2.541890] usbhid: v2.6:USB HID core driver
Mar 29 11:04:57 ATG-Prime kernel: [    2.542976] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
Mar 29 11:04:57 ATG-Prime kernel: [    2.554814] 0000:00:04.0: Using transceiver found at address 1 as default
Mar 29 11:04:57 ATG-Prime kernel: [    2.558155] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:11:d8:f7:64:17
Mar 29 11:04:57 ATG-Prime kernel: [    2.792037] usb 2-2.1: new full speed USB device using ohci_hcd and address 3
Mar 29 11:04:57 ATG-Prime kernel: [    3.008181] usb 2-2.1: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    3.108018] usb 2-2.3: new full speed USB device using ohci_hcd and address 4
Mar 29 11:04:57 ATG-Prime kernel: [    3.243501] usb 2-2.3: configuration #1 chosen from 1 choice
Mar 29 11:04:57 ATG-Prime kernel: [    3.256932] Initializing USB Mass Storage driver...
Mar 29 11:04:57 ATG-Prime kernel: [    3.259398] scsi4 : SCSI emulation for USB Mass Storage devices
Mar 29 11:04:57 ATG-Prime kernel: [    3.259755] usbcore: registered new interface driver usb-storage
Mar 29 11:04:57 ATG-Prime kernel: [    3.259762] USB Mass Storage support registered.
Mar 29 11:04:57 ATG-Prime kernel: [    3.319137] xor: automatically using best checksumming function: pIII_sse
Mar 29 11:04:57 ATG-Prime kernel: [    3.336009]    pIII_sse  :  3649.000 MB/sec
Mar 29 11:04:57 ATG-Prime kernel: [    3.336014] xor: using function: pIII_sse (3649.000 MB/sec)
Mar 29 11:04:57 ATG-Prime kernel: [    3.341048] device-mapper: dm-raid45: initialized v0.2594b
Mar 29 11:04:57 ATG-Prime kernel: [    4.126839] PM: Starting manual resume from disk
Mar 29 11:04:57 ATG-Prime kernel: [    4.208118] kjournald starting.  Commit interval 5 seconds
Mar 29 11:04:57 ATG-Prime kernel: [    4.208146] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 11:04:57 ATG-Prime kernel: [    5.608450] type=1505 audit(1269875087.960:2): operation="profile_load" pid=384 name=/usr/share/gdm/guest-session/Xsession
Mar 29 11:04:57 ATG-Prime kernel: [    5.631614] type=1505 audit(1269875087.980:3): operation="profile_load" pid=385 name=/sbin/dhclient3
Mar 29 11:04:57 ATG-Prime kernel: [    5.632624] type=1505 audit(1269875087.984:4): operation="profile_load" pid=385 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 29 11:04:57 ATG-Prime kernel: [    5.633133] type=1505 audit(1269875087.984:5): operation="profile_load" pid=385 name=/usr/lib/connman/scripts/dhclient-script
Mar 29 11:04:57 ATG-Prime kernel: [    5.683899] type=1505 audit(1269875088.032:6): operation="profile_load" pid=386 name=/usr/bin/evince
Mar 29 11:04:57 ATG-Prime kernel: [    5.699118] type=1505 audit(1269875088.048:7): operation="profile_load" pid=386 name=/usr/bin/evince-previewer
Mar 29 11:04:57 ATG-Prime kernel: [    5.715095] type=1505 audit(1269875088.064:8): operation="profile_load" pid=386 name=/usr/bin/evince-thumbnailer
Mar 29 11:04:57 ATG-Prime kernel: [    5.739166] type=1505 audit(1269875088.088:9): operation="profile_load" pid=388 name=/usr/bin/freshclam
Mar 29 11:04:57 ATG-Prime kernel: [    5.752885] type=1505 audit(1269875088.104:10): operation="profile_load" pid=389 name=/usr/lib/cups/backend/cups-pdf
Mar 29 11:04:57 ATG-Prime kernel: [    5.753985] type=1505 audit(1269875088.104:11): operation="profile_load" pid=389 name=/usr/sbin/cupsd
Mar 29 11:04:57 ATG-Prime kernel: [    6.953996] Adding 2104472k swap on /dev/sdb5.  Priority:-1 extents:1 across:2104472k 
Mar 29 11:04:57 ATG-Prime kernel: [    7.652523] EXT3 FS on sdc1, internal journal
Mar 29 11:04:57 ATG-Prime kernel: [    8.276840] scsi 4:0:0:0: Direct-Access     IC       USB Storage-CFC  322E PQ: 0 ANSI: 0 CCS
Mar 29 11:04:57 ATG-Prime kernel: [    8.283821] scsi 4:0:0:1: Direct-Access     IC       USB Storage-SMC  322E PQ: 0 ANSI: 0 CCS
Mar 29 11:04:57 ATG-Prime kernel: [    8.289634] udev: starting version 147
Mar 29 11:04:57 ATG-Prime kernel: [    8.291893] scsi 4:0:0:2: Direct-Access     IC       USB Storage-MMC  322E PQ: 0 ANSI: 0 CCS
Mar 29 11:04:57 ATG-Prime kernel: [    8.298926] scsi 4:0:0:3: Direct-Access     IC       USB Storage-MSC  322E PQ: 0 ANSI: 0 CCS
Mar 29 11:04:57 ATG-Prime kernel: [    8.299700] sd 4:0:0:0: Attached scsi generic sg5 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    8.299890] sd 4:0:0:1: Attached scsi generic sg6 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    8.300096] sd 4:0:0:2: Attached scsi generic sg7 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    8.300274] sd 4:0:0:3: Attached scsi generic sg8 type 0
Mar 29 11:04:57 ATG-Prime kernel: [    8.368792] sd 4:0:0:2: [sdf] Attached SCSI removable disk
Mar 29 11:04:57 ATG-Prime kernel: [    8.382828] sd 4:0:0:0: [sdd] Attached SCSI removable disk
Mar 29 11:04:57 ATG-Prime kernel: [    8.393801] sd 4:0:0:1: [sde] Attached SCSI removable disk
Mar 29 11:04:57 ATG-Prime kernel: [    8.404768] sd 4:0:0:3: [sdg] Attached SCSI removable disk
Mar 29 11:04:57 ATG-Prime kernel: [    8.650309] kjournald starting.  Commit interval 5 seconds
Mar 29 11:04:57 ATG-Prime kernel: [    8.651066] EXT3 FS on sda1, internal journal
Mar 29 11:04:57 ATG-Prime kernel: [    8.651079] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 11:04:57 ATG-Prime kernel: [    8.709682] kjournald starting.  Commit interval 5 seconds
Mar 29 11:04:57 ATG-Prime kernel: [    8.715131] EXT3 FS on sdb1, internal journal
Mar 29 11:04:57 ATG-Prime kernel: [    8.715145] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 11:04:57 ATG-Prime kernel: [    9.793163] kjournald starting.  Commit interval 5 seconds
Mar 29 11:04:57 ATG-Prime kernel: [    9.793526] EXT3 FS on sda2, internal journal
Mar 29 11:04:57 ATG-Prime kernel: [    9.793537] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 11:04:57 ATG-Prime kernel: [   10.248316] lp: driver loaded but no devices found
Mar 29 11:04:57 ATG-Prime kernel: [   10.579528] logips2pp: Detected unknown logitech mouse model 127
Mar 29 11:04:57 ATG-Prime kernel: [   10.765526] lirc_dev: IR Remote Control driver registered, major 61 
Mar 29 11:04:57 ATG-Prime kernel: [   11.050192] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
Mar 29 11:04:57 ATG-Prime kernel: [   11.050237] lirc_dev: lirc_register_driver: sample_rate: 0
Mar 29 11:04:57 ATG-Prime kernel: [   11.050330] lirc_imon: Registered iMON driver (lirc minor: 0)
Mar 29 11:04:57 ATG-Prime kernel: [   11.050410] input: iMON PAD IR Mouse (15c2:0043) as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input4
Mar 29 11:04:57 ATG-Prime kernel: [   11.069122] lirc_imon: iMON device (15c2:0043, intf0) on usb<3:2> initialized
Mar 29 11:04:57 ATG-Prime kernel: [   11.072314] lirc_imon: iMON device (15c2:0043, intf1) on usb<3:2> initialized
Mar 29 11:04:57 ATG-Prime kernel: [   11.072394] usbcore: registered new interface driver lirc_imon
Mar 29 11:04:57 ATG-Prime kernel: [   11.080166] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 29 11:04:57 ATG-Prime kernel: [   11.092763] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
Mar 29 11:04:57 ATG-Prime kernel: [   11.455782] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 29 11:04:57 ATG-Prime kernel: [   12.113249] kjournald starting.  Commit interval 5 seconds
Mar 29 11:04:57 ATG-Prime kernel: [   12.113650] EXT3 FS on sdc3, internal journal
Mar 29 11:04:57 ATG-Prime kernel: [   12.113660] EXT3-fs: mounted filesystem with ordered data mode.
Mar 29 11:04:57 ATG-Prime kernel: [   12.132717] Linux video capture interface: v2.00
Mar 29 11:04:57 ATG-Prime kernel: [   12.736499] cx18:  Start initialization, version 1.2.0
Mar 29 11:04:57 ATG-Prime kernel: [   12.736566] cx18-0: Initializing card 0
Mar 29 11:04:57 ATG-Prime kernel: [   12.736573] cx18-0: Autodetected Hauppauge card
Mar 29 11:04:57 ATG-Prime kernel: [   12.736720] cx18 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 29 11:04:57 ATG-Prime kernel: [   12.738160] cx18-0: cx23418 revision 01010000 (B)
Mar 29 11:04:57 ATG-Prime kernel: [   12.963786] tveeprom 0-0050: Hauppauge model 74541, rev C6B6, serial# 3432282
Mar 29 11:04:57 ATG-Prime kernel: [   12.963793] tveeprom 0-0050: MAC address is 00-0D-FE-34-5F-5A
Mar 29 11:04:57 ATG-Prime kernel: [   12.963798] tveeprom 0-0050: tuner model is Philips FM1236 MK5 (idx 116, type 43)
Mar 29 11:04:57 ATG-Prime kernel: [   12.963803] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
Mar 29 11:04:57 ATG-Prime kernel: [   12.963807] tveeprom 0-0050: audio processor is CX23418 (idx 38)
Mar 29 11:04:57 ATG-Prime kernel: [   12.963811] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
Mar 29 11:04:57 ATG-Prime kernel: [   12.963814] tveeprom 0-0050: has radio
Mar 29 11:04:57 ATG-Prime kernel: [   12.963818] cx18-0: Autodetected Hauppauge HVR-1600
Mar 29 11:04:57 ATG-Prime kernel: [   12.963822] cx18-0: Simultaneous Digital and Analog TV capture supported
Mar 29 11:04:57 ATG-Prime kernel: [   13.061060] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
Mar 29 11:04:57 ATG-Prime kernel: [   13.564747] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
Mar 29 11:04:57 ATG-Prime kernel: [   13.742055] tda9887 1-0043: creating new instance
Mar 29 11:04:57 ATG-Prime kernel: [   13.742061] tda9887 1-0043: tda988[5/6/7] found
Mar 29 11:04:57 ATG-Prime kernel: [   13.746617] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
Mar 29 11:04:57 ATG-Prime kernel: [   13.938116] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
Mar 29 11:04:57 ATG-Prime kernel: [   14.156756] tuner-simple 1-0061: creating new instance
Mar 29 11:04:57 ATG-Prime kernel: [   14.156764] tuner-simple 1-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
Mar 29 11:04:57 ATG-Prime kernel: [   14.158885] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
Mar 29 11:04:57 ATG-Prime kernel: [   14.158893] DVB: registering new adapter (cx18)
Mar 29 11:04:57 ATG-Prime kernel: [   14.753244] MXL5005S: Attached at address 0x63
Mar 29 11:04:57 ATG-Prime kernel: [   14.753256] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Mar 29 11:04:57 ATG-Prime kernel: [   14.753418] cx18-0: DVB Frontend registered
Mar 29 11:04:57 ATG-Prime kernel: [   14.753424] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
Mar 29 11:04:57 ATG-Prime kernel: [   14.753481] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
Mar 29 11:04:57 ATG-Prime kernel: [   14.753532] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [   14.753583] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
Mar 29 11:04:57 ATG-Prime kernel: [   14.753639] cx18-0: Registered device radio0 for encoder radio
Mar 29 11:04:57 ATG-Prime kernel: [   14.753645] cx18-0: Initialized card: Hauppauge HVR-1600
Mar 29 11:04:57 ATG-Prime kernel: [   14.753699] cx18:  End initialization
Mar 29 11:04:57 ATG-Prime kernel: [   14.756037] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 29 11:04:57 ATG-Prime kernel: [   14.932065] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-cpu.fw
Mar 29 11:04:57 ATG-Prime kernel: [   15.263451] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
Mar 29 11:04:57 ATG-Prime kernel: [   15.284992] intel8x0_measure_ac97_clock: measured 161189 usecs (7743 samples)
Mar 29 11:04:57 ATG-Prime kernel: [   15.284998] intel8x0: clocking to 48000
Mar 29 11:04:57 ATG-Prime kernel: [   15.324747] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-apu.fw
Mar 29 11:04:58 ATG-Prime kernel: [   15.899365] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
Mar 29 11:04:58 ATG-Prime kernel: [   15.905713] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
Mar 29 11:04:58 ATG-Prime kernel: [   16.140116] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-cpu.fw
Mar 29 11:04:58 ATG-Prime kernel: [   16.270058] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-apu.fw
Mar 29 11:04:58 ATG-Prime kernel: [   16.573915] cx18 0000:00:0c.0: firmware: requesting v4l-cx23418-dig.fw
Mar 29 11:04:59 ATG-Prime kernel: [   16.961936] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
Mar 29 11:04:59 ATG-Prime kernel: [   16.980212] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
Mar 29 11:05:02 ATG-Prime kernel: [   20.173721] __ratelimit: 9 callbacks suppressed
Mar 29 11:05:02 ATG-Prime kernel: [   20.173727] type=1505 audit(1269875102.524:15): operation="profile_replace" pid=1070 name=/usr/share/gdm/guest-session/Xsession
Mar 29 11:05:02 ATG-Prime kernel: [   20.178290] type=1505 audit(1269875102.528:16): operation="profile_replace" pid=1071 name=/sbin/dhclient3
Mar 29 11:05:02 ATG-Prime kernel: [   20.179235] type=1505 audit(1269875102.528:17): operation="profile_replace" pid=1071 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 29 11:05:02 ATG-Prime kernel: [   20.179741] type=1505 audit(1269875102.528:18): operation="profile_replace" pid=1071 name=/usr/lib/connman/scripts/dhclient-script
Mar 29 11:05:02 ATG-Prime kernel: [   20.192205] type=1505 audit(1269875102.544:19): operation="profile_replace" pid=1072 name=/usr/bin/evince
Mar 29 11:05:02 ATG-Prime kernel: [   20.208242] type=1505 audit(1269875102.560:20): operation="profile_replace" pid=1072 name=/usr/bin/evince-previewer
Mar 29 11:05:02 ATG-Prime kernel: [   20.218224] type=1505 audit(1269875102.568:21): operation="profile_replace" pid=1072 name=/usr/bin/evince-thumbnailer
Mar 29 11:05:02 ATG-Prime kernel: [   20.235726] type=1505 audit(1269875102.584:22): operation="profile_replace" pid=1074 name=/usr/bin/freshclam
Mar 29 11:05:02 ATG-Prime kernel: [   20.240244] type=1505 audit(1269875102.592:23): operation="profile_replace" pid=1075 name=/usr/lib/cups/backend/cups-pdf
Mar 29 11:05:02 ATG-Prime kernel: [   20.241358] type=1505 audit(1269875102.592:24): operation="profile_replace" pid=1075 name=/usr/sbin/cupsd
Mar 29 11:05:04 ATG-Prime kernel: [   22.129151] eth0: Media Link On 100mbps full-duplex 
Mar 29 11:05:05 ATG-Prime kernel: [   22.775008] Bluetooth: Generic Bluetooth USB driver ver 0.5
Mar 29 11:05:05 ATG-Prime kernel: [   22.775249] usbcore: registered new interface driver btusb
Mar 29 11:05:05 ATG-Prime kernel: [   23.365464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 29 11:05:05 ATG-Prime kernel: [   23.365472] Bluetooth: BNEP filters: protocol multicast
Mar 29 11:05:05 ATG-Prime kernel: [   23.436630] Bridge firewalling registered
Mar 29 11:05:08 ATG-Prime kernel: [   26.016742] __ratelimit: 9 callbacks suppressed
Mar 29 11:05:08 ATG-Prime kernel: [   26.016748] type=1503 audit(1269875108.368:28): operation="open" pid=1330 parent=1329 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:10 ATG-Prime kernel: [   27.735506] type=1503 audit(1269875110.084:29): operation="open" pid=1389 parent=1388 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:11 ATG-Prime kernel: [   29.095246] type=1503 audit(1269875111.444:30): operation="open" pid=1545 parent=1399 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:11 ATG-Prime kernel: [   29.242244] type=1503 audit(1269875111.592:31): operation="open" pid=1555 parent=1554 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:12 ATG-Prime kernel: [   30.271015] type=1503 audit(1269875112.620:32): operation="open" pid=1591 parent=1590 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:13 ATG-Prime kernel: [   31.319359] type=1503 audit(1269875113.668:33): operation="open" pid=1611 parent=1610 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:14 ATG-Prime kernel: [   32.356882] type=1503 audit(1269875114.708:34): operation="open" pid=1654 parent=1653 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:15 ATG-Prime kernel: [   33.383970] type=1503 audit(1269875115.732:35): operation="open" pid=1675 parent=1674 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:16 ATG-Prime kernel: [   34.563382] type=1503 audit(1269875116.912:36): operation="open" pid=1694 parent=1693 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:17 ATG-Prime kernel: [   34.735867] type=1503 audit(1269875117.084:37): operation="open" pid=1705 parent=1704 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 29 11:05:19 ATG-Prime kernel: [   36.802842] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
Mar 29 11:05:19 ATG-Prime kernel: [   36.802871] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Mar 29 11:05:19 ATG-Prime kernel: [   36.802883] agpgart-sis 0000:00:00.0: putting AGP V3 device into 8x mode
Mar 29 11:05:19 ATG-Prime kernel: [   36.804906] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Mar 29 11:05:19 ATG-Prime kernel: [   37.017757] [drm] Setting GART location based on new memory map
Mar 29 11:05:19 ATG-Prime kernel: [   37.032656] [drm] Loading RV670 CP Microcode
Mar 29 11:05:19 ATG-Prime kernel: [   37.032980] [drm] Loading RV670 PFP Microcode
Mar 29 11:05:19 ATG-Prime kernel: [   37.047929] [drm] Resetting GPU
Mar 29 11:05:19 ATG-Prime kernel: [   37.047990] [drm] writeback test succeeded in 1 usecs
Mar 29 11:05:22 ATG-Prime kernel: [   40.321131] ppdev: user-space parallel port driver
Mar 29 11:05:36 ATG-Prime kernel: [   53.909503] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:05:44 ATG-Prime kernel: [   61.889859] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:05:52 ATG-Prime kernel: [   69.889247] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:06:00 ATG-Prime kernel: [   77.889635] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:06:08 ATG-Prime kernel: [   85.890024] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:06:16 ATG-Prime kernel: [   93.889413] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:06:24 ATG-Prime kernel: [  101.889802] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:06:32 ATG-Prime kernel: [  109.889192] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
Mar 29 11:36:14 ATG-Prime pulseaudio[2506]: ratelimit.c: 3 events suppressed
Mar 29 12:50:50 ATG-Prime pulseaudio[2506]: ratelimit.c: 3 events suppressed
Mar 29 13:42:55 ATG-Prime pulseaudio[2506]: ratelimit.c: 132 events suppressed
Mar 29 15:42:13 ATG-Prime kernel: [16651.556019] usb 1-7: new high speed USB device using ehci_hcd and address 4
Mar 29 15:42:14 ATG-Prime kernel: [16651.689965] usb 1-7: configuration #1 chosen from 1 choice
Mar 29 15:42:14 ATG-Prime kernel: [16651.692557] scsi5 : SCSI emulation for USB Mass Storage devices
Mar 29 15:42:19 ATG-Prime kernel: [16656.693357] scsi 5:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
Mar 29 15:42:19 ATG-Prime kernel: [16656.694168] sd 5:0:0:0: Attached scsi generic sg9 type 0
Mar 29 15:42:19 ATG-Prime kernel: [16656.720104] sd 5:0:0:0: [sdh] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
Mar 29 15:42:19 ATG-Prime kernel: [16656.720690] sd 5:0:0:0: [sdh] Write Protect is off
Mar 29 15:42:19 ATG-Prime kernel: [16656.725986]  sdh: sdh1
Mar 29 15:42:19 ATG-Prime kernel: [16656.999907] sd 5:0:0:0: [sdh] Attached SCSI removable disk
Mar 29 15:42:31 ATG-Prime pulseaudio[2506]: ratelimit.c: 3 events suppressed
Mar 29 15:43:37 ATG-Prime kernel: [16734.786807] usb 1-7: USB disconnect, address 4
```

---

### Post by renfrew on 2010-03-30
Having searched the forums here and googled for occurences of /proc/bus/usb I still am no closer to a solution.  I've attached copies of the /proc/bus/usb directory tree that I get when I'm running a live cd, which has everything neatly in the right places. I really don't know what further information would be useful at this point.

I've thought about rsynching the live cd's proc/bus/usb tree into my drive but am under the impression that proc should be empty prior to boot time.

I'd really appreciate any insight that anyone might have into the problem of /proc/bus/usb not existing on a running 9.10 system.

---

### Post by smoats on 2010-04-01
Recent kernel updates have disabled the usbfs feature.  Apparently it is deprecated.  If you check the kernel versions of the live CD and your running system with 'uname -r', they will likely be different.    

If you need it, you will either have to boot to an older kernel or compile a custom kernel with usbfs enabled.  I know that 2.6.31-17 still has usbfs support.  See [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile") for more info on building your own kernel.  Unfortunately, usbfs can not be built as a module.

---

### Post by renfrew on 2010-04-05
Thanks for the info smoats, I have been unable to get online earlier to say thanks and get a fresh view of the thread.  I'm still confured though in that during the instalion of the new hardware (week of March 15th) I was running the, then,  latest kernel version of 2.6.31.20.  With that kernel running I had a full proc/bus/usb directory tree.  I'm going to consider this closed for now in that I did get an answer...

---

