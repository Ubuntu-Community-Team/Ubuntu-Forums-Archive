---
title: "Ubuntu Freezes after random amount of time"
date: 2009-10-09
forum: General Help
---

### Post by sshaikh on 2009-10-09
Running Ubuntu 9.04, all latest patches.

I just run postgresql and memcached (both latest and so not from Synaptic) on top of a fresh install, sometimes I remote in via VNC to configure, otherwise I use PuTTY from a windows client. Most other accesses are from client applications. I have mounted a windows share, and also share a directory to windows, both directions using SMB/CIFs.

After random amounts of uptime, Ubuntu simply freezes/hangs. All my PuTTY sessions quit, I can no longer ping the machine and there is no display. Power cycling brings it all back with no apparent harm; I suspect I've been lucky though! There are times when it will stay up for at least a day before I power it down myself, but usually it'll die between 30 mins and 4 hours.

Any ideas how to investigate and hopefully even fix this? I think it began to happen only after I updated my install to the latest updates, but rebuilding fresh (including an update) repeats this behaviour. I've tested my RAM with Memtest and seen that the CPU temperature doesn't break 40C.

The lines in my syslog around the crash are:
```

Oct  9 16:30:01 serverTest /USR/SBIN/CRON[4963]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  9 16:40:01 serverTest /USR/SBIN/CRON[5033]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  9 16:47:00 serverTest syslogd 1.5.0#5ubuntu3: restart.
Oct  9 16:47:00 serverTest kernel: Inspecting /boot/System.map-2.6.28-15-generic
Oct  9 16:47:00 serverTest kernel: Cannot find map file.
Oct  9 16:47:00 serverTest kernel: Loaded 57599 symbols from 68 modules.
Oct  9 16:47:00 serverTest kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Oct  9 16:47:00 serverTest kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  9 16:47:00 serverTest kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  9 16:47:00 serverTest kernel: [    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) 

```

My dmesg is as follows:

```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x5fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  modified: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  modified: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fefe49
[    0.000000] Allocated new RAMDISK: 0087d000 - 00faee49
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefe48 to 0087d000 - 00faee48
[    0.000000] ACPI: RSDP 000F6A90, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 5FFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5FFF30C0, 40BF (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FFF0000, 0040
[    0.000000] ACPI: APIC 5FFF7180, 0068 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 651MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000faee49]      NEW RAMDISK ==> [000087d000 - 0000faee49]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f5020] 000f5020
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0005fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005fff0
[    0.000000] On node 0 totalpages: 393087
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1304 pages used for memmap
[    0.000000]   HighMem zone: 165594 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390015
[    0.000000] Kernel command line: root=UUID=8a101c58-7d50-401e-ab16-06286d029bb6 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2992.453 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 7863680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1535452k/1572800k available (4116k kernel code, 35940k reserved, 2199k data, 532k init, 667592k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.90 BogoMIPS (lpj=11969812)
[    0.004036] Security Framework initialized
[    0.004048] SELinux:  Disabled at boot.
[    0.004071] AppArmor: AppArmor initialized
[    0.004086] Mount-cache hash table entries: 512
[    0.004265] Initializing cgroup subsys ns
[    0.004270] Initializing cgroup subsys cpuacct
[    0.004273] Initializing cgroup subsys memory
[    0.004278] Initializing cgroup subsys freezer
[    0.004296] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004300] CPU: L2 cache: 512K
[    0.004303] CPU: Physical Processor ID: 0
[    0.004306] CPU: Processor Core ID: 0
[    0.004323] Checking 'hlt' instruction... OK.
[    0.022814] ACPI: Core revision 20080926
[    0.024861] ACPI: Checking initramfs for custom DSDT
[    0.307277] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.346966] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.348001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5985.47 BogoMIPS (lpj=11970956)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.432176] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.432199] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.436066] Brought up 2 CPUs
[    0.436071] Total of 2 processors activated (11970.38 BogoMIPS).
[    0.436120] CPU0 attaching sched-domain:
[    0.436124]  domain 0: span 0-1 level SIBLING
[    0.436127]   groups: 0 1
[    0.436136] CPU1 attaching sched-domain:
[    0.436138]  domain 0: span 0-1 level SIBLING
[    0.436141]   groups: 1 0
[    0.436239] net_namespace: 776 bytes
[    0.436250] Booting paravirtualized kernel on bare hardware
[    0.436480] Time: 15:46:43  Date: 10/09/09
[    0.436480] regulator: core version 0.5
[    0.436480] NET: Registered protocol family 16
[    0.436480] EISA bus registered
[    0.436480] ACPI: bus type pci registered
[    0.464238] PCI: PCI BIOS revision 2.10 entry at 0xfb270, last bus=2
[    0.464242] PCI: Using configuration type 1 for base access
[    0.465450] ACPI: EC: Look up EC in DSDT
[    0.473243] ACPI: Interpreter enabled
[    0.473250] ACPI: (supports S0 S3 S4 S5)
[    0.473275] ACPI: Using IOAPIC for interrupt routing
[    0.478189] ACPI: No dock devices found.
[    0.478204] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.478263] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.478389] pci 0000:00:1d.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.478440] pci 0000:00:1d.1: reg 20 io port: [0xc000-0xc01f]
[    0.478491] pci 0000:00:1d.2: reg 20 io port: [0xc400-0xc41f]
[    0.478542] pci 0000:00:1d.3: reg 20 io port: [0xc800-0xc81f]
[    0.478596] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfa800000-0xfa8003ff]
[    0.478640] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.478646] pci 0000:00:1d.7: PME# disabled
[    0.478728] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.478735] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.478740] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.478760] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.478768] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.478775] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.478782] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.478790] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.478797] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.478846] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.478887] pci 0000:00:1f.5: reg 10 io port: [0xd400-0xd4ff]
[    0.478894] pci 0000:00:1f.5: reg 14 io port: [0xd800-0xd83f]
[    0.478901] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfa801000-0xfa8011ff]
[    0.478909] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfa802000-0xfa8020ff]
[    0.478931] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.478936] pci 0000:00:1f.5: PME# disabled
[    0.478975] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.478981] pci 0000:01:00.0: reg 14 io port: [0xa000-0xa0ff]
[    0.478988] pci 0000:01:00.0: reg 18 32bit mmio: [0xf9000000-0xf900ffff]
[    0.479005] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.479015] pci 0000:01:00.0: supports D1 D2
[    0.479043] pci 0000:01:00.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.479049] pci 0000:01:00.1: reg 14 32bit mmio: [0xf9010000-0xf901ffff]
[    0.479076] pci 0000:01:00.1: supports D1 D2
[    0.479118] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.479122] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.479127] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xf7ffffff]
[    0.479162] pci 0000:02:00.0: reg 10 32bit mmio: [0xfa400000-0xfa401fff]
[    0.479198] pci 0000:02:00.0: supports D1 D2
[    0.479201] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.479206] pci 0000:02:00.0: PME# disabled
[    0.479238] pci 0000:02:02.0: reg 10 32bit mmio: [0xfa402000-0xfa4023ff]
[    0.479274] pci 0000:02:02.0: supports D1 D2
[    0.479307] pci 0000:02:04.0: reg 10 32bit mmio: [0xfa000000-0xfa3fffff]
[    0.479344] pci 0000:02:04.0: supports D2
[    0.479347] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.479351] pci 0000:02:04.0: PME# disabled
[    0.479388] pci 0000:02:09.0: reg 10 io port: [0xb000-0xb0ff]
[    0.479395] pci 0000:02:09.0: reg 14 32bit mmio: [0xfa403000-0xfa4030ff]
[    0.479428] pci 0000:02:09.0: supports D1 D2
[    0.479431] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.479435] pci 0000:02:09.0: PME# disabled
[    0.479468] pci 0000:02:0a.0: reg 10 32bit mmio: [0xfa404000-0xfa4047ff]
[    0.479475] pci 0000:02:0a.0: reg 14 io port: [0xb400-0xb47f]
[    0.479507] pci 0000:02:0a.0: supports D2
[    0.479510] pci 0000:02:0a.0: PME# supported from D2 D3hot D3cold
[    0.479515] pci 0000:02:0a.0: PME# disabled
[    0.479545] pci 0000:00:1e.0: transparent bridge
[    0.479550] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.479556] pci 0000:00:1e.0: bridge 32bit mmio: [0xfa000000-0xfa7fffff]
[    0.479570] bus 00 -> node 0
[    0.479579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.479760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.488898] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.489037] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.489177] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.489314] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.489453] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.489591] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.489729] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.489868] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.490034] ACPI: WMI: Mapper loaded
[    0.490120] SCSI subsystem initialized
[    0.490120] libata version 3.00 loaded.
[    0.490120] usbcore: registered new interface driver usbfs
[    0.490120] usbcore: registered new interface driver hub
[    0.490120] usbcore: registered new device driver usb
[    0.490120] PCI: Using ACPI for IRQ routing
[    0.496014] Bluetooth: Core ver 2.13
[    0.496042] NET: Registered protocol family 31
[    0.496042] Bluetooth: HCI device and connection manager initialized
[    0.496042] Bluetooth: HCI socket layer initialized
[    0.496042] NET: Registered protocol family 8
[    0.496042] NET: Registered protocol family 20
[    0.496052] NetLabel: Initializing
[    0.496055] NetLabel:  domain hash size = 128
[    0.496057] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.496074] NetLabel:  unlabeled traffic allowed by default
[    0.496177] hpet clockevent registered
[    0.496182] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.496189] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.496196] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.500098] AppArmor: AppArmor Filesystem Enabled
[    0.508013] pnp: PnP ACPI init
[    0.508029] ACPI: bus type pnp registered
[    0.510578] pnp: PnP ACPI: found 9 devices
[    0.510581] ACPI: ACPI bus type pnp unregistered
[    0.510587] PnPBIOS: Disabled by ACPI PNP
[    0.510605] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.510609] system 00:01: ioport range 0x200-0x200 has been reserved
[    0.510612] system 00:01: ioport range 0x202-0x208 has been reserved
[    0.510615] system 00:01: ioport range 0x320-0x32f has been reserved
[    0.510618] system 00:01: ioport range 0x295-0x296 has been reserved
[    0.510632] system 00:07: ioport range 0x400-0x4bf could not be reserved
[    0.510640] system 00:08: iomem range 0xcc000-0xcffff has been reserved
[    0.510643] system 00:08: iomem range 0xf0000-0xf7fff could not be reserved
[    0.510646] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
[    0.510650] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
[    0.510653] system 00:08: iomem range 0x5fff0000-0x5fffffff could not be reserved
[    0.510656] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.510659] system 00:08: iomem range 0x100000-0x5ffeffff could not be reserved
[    0.510663] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.510666] system 00:08: iomem range 0xfec01000-0xfed8ffff has been reserved
[    0.510669] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.510673] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.510676] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.510679] system 00:08: iomem range 0xe0000-0xeffff has been reserved
[    0.545428] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.545432] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.545437] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf9ffffff
[    0.545442] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000f7ffffff
[    0.545449] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.545453] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.545459] pci 0000:00:1e.0:   MEM window: 0xfa000000-0xfa7fffff
[    0.545464] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.545481] pci 0000:00:1e.0: setting latency timer to 64
[    0.545486] bus: 00 index 0 io port: [0x00-0xffff]
[    0.545489] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.545492] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.545495] bus: 01 index 1 mmio: [0xf8000000-0xf9ffffff]
[    0.545497] bus: 01 index 2 mmio: [0xe8000000-0xf7ffffff]
[    0.545500] bus: 01 index 3 mmio: [0x0-0x0]
[    0.545503] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.545506] bus: 02 index 1 mmio: [0xfa000000-0xfa7fffff]
[    0.545508] bus: 02 index 2 mmio: [0x0-0x0]
[    0.545511] bus: 02 index 3 io port: [0x00-0xffff]
[    0.545513] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.545524] NET: Registered protocol family 2
[    0.560076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.560465] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.561324] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.561905] TCP: Hash tables configured (established 131072 bind 65536)
[    0.561909] TCP reno registered
[    0.568130] NET: Registered protocol family 1
[    0.568300] checking if image is initramfs... it is
[    0.996311] Switched to high resolution mode on CPU 1
[    1.000047] Switched to high resolution mode on CPU 0
[    1.155671] Freeing initrd memory: 7367k freed
[    1.155745] cpufreq: No nForce2 chipset.
[    1.155921] audit: initializing netlink socket (disabled)
[    1.155943] type=2000 audit(1255103203.153:1): initialized
[    1.162428] highmem bounce pool size: 64 pages
[    1.162435] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.163985] VFS: Disk quotas dquot_6.5.1
[    1.164075] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.164863] fuse init (API version 7.10)
[    1.164968] msgmni has been set to 1711
[    1.165269] alg: No test for stdrng (krng)
[    1.165303] io scheduler noop registered
[    1.165307] io scheduler anticipatory registered
[    1.165311] io scheduler deadline registered
[    1.165361] io scheduler cfq registered (default)
[    1.165480] pci 0000:01:00.0: Boot video device
[    1.168950] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.168962] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.169159] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.169163] ACPI: Power Button (FF) [PWRF]
[    1.169219] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.169223] ACPI: Power Button (CM) [PWRB]
[    1.169277] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.169285] ACPI: Sleep Button (CM) [SLPB]
[    1.169356] fan PNP0C0B:00: registered as cooling_device0
[    1.169364] ACPI: Fan [FAN] (on)
[    1.169606] processor ACPI_CPU:00: registered as cooling_device1
[    1.169656] processor ACPI_CPU:01: registered as cooling_device2
[    1.172455] thermal LNXTHERM:01: registered as thermal_zone0
[    1.172815] ACPI: Thermal Zone [THRM] (40 C)
[    1.172878] isapnp: Scanning for PnP cards...
[    1.526500] isapnp: No Plug & Play device found
[    1.537177] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.538393] brd: module loaded
[    1.538814] loop: module loaded
[    1.538912] Fixed MDIO Bus: probed
[    1.538919] PPP generic driver version 2.4.2
[    1.539004] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.539046] Driver 'sd' needs updating - please use bus_type methods
[    1.539058] Driver 'sr' needs updating - please use bus_type methods
[    1.539147] ata_piix 0000:00:1f.1: version 2.12
[    1.539167] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.539226] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.539353] scsi0 : ata_piix
[    1.539488] scsi1 : ata_piix
[    1.540339] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.540342] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.768272] ata1.00: HPA unlocked: 390719855 -> 390721968, native 390721968
[    1.768278] ata1.00: ATA-6: ST3200021A, 3.01, max UDMA/100
[    1.768281] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.784416] ata1.00: configured for UDMA/100
[    1.956296] ata2.01: ATAPI: PIONEER DVD RW  DVR-107D, 1.20, max UDMA/33
[    1.964239] ata2.01: configured for UDMA/33
[    1.964678] scsi 0:0:0:0: Direct-Access     ATA      ST3200021A       3.01 PQ: 0 ANSI: 5
[    1.964806] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    1.964828] sd 0:0:0:0: [sda] Write Protect is off
[    1.964831] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.964865] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.964953] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    1.964972] sd 0:0:0:0: [sda] Write Protect is off
[    1.964975] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.965016] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.965021]  sda: sda1 sda2 < sda5 > sda3
[    2.000808] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.000874] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.007578] scsi 1:0:1:0: CD-ROM            PIONEER  DVD RW  DVR-107D 1.20 PQ: 0 ANSI: 5
[    2.025912] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.025916] Uniform CD-ROM driver Revision: 3.20
[    2.026048] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    2.026105] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    2.026977] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.027009] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.027044] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.027049] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.027132] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.031035] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.031054] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa800000
[    2.044013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.044108] usb usb1: configuration #1 chosen from 1 choice
[    2.044146] hub 1-0:1.0: USB hub found
[    2.044157] hub 1-0:1.0: 8 ports detected
[    2.044315] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.044340] uhci_hcd: USB Universal Host Controller Interface driver
[    2.044387] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.044397] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.044402] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.044462] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.044493] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[    2.044586] usb usb2: configuration #1 chosen from 1 choice
[    2.044619] hub 2-0:1.0: USB hub found
[    2.044627] hub 2-0:1.0: 2 ports detected
[    2.044734] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.044742] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.044745] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.044802] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.044830] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c000
[    2.044917] usb usb3: configuration #1 chosen from 1 choice
[    2.044948] hub 3-0:1.0: USB hub found
[    2.044958] hub 3-0:1.0: 2 ports detected
[    2.045068] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.045075] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.045079] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.045132] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.045159] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c400
[    2.045256] usb usb4: configuration #1 chosen from 1 choice
[    2.045288] hub 4-0:1.0: USB hub found
[    2.045298] hub 4-0:1.0: 2 ports detected
[    2.045399] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.045406] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.045409] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.045471] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.045491] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c800
[    2.045580] usb usb5: configuration #1 chosen from 1 choice
[    2.045613] hub 5-0:1.0: USB hub found
[    2.045622] hub 5-0:1.0: 2 ports detected
[    2.045792] PNP: No PS/2 controller found. Probing ports directly.
[    2.047738] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.047747] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.048058] mice: PS/2 mouse device common for all mice
[    2.064079] rtc_cmos 00:03: RTC can wake from S4
[    2.064127] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.064152] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.064243] device-mapper: uevent: version 1.0.3
[    2.064383] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.064513] device-mapper: multipath: version 1.0.5 loaded
[    2.064518] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.064635] EISA: Probing bus 0 at eisa.0
[    2.064681] EISA: Detected 0 cards.
[    2.064758] cpuidle: using governor ladder
[    2.064762] cpuidle: using governor menu
[    2.065471] TCP cubic registered
[    2.065563] NET: Registered protocol family 10
[    2.066126] lo: Disabled Privacy Extensions
[    2.066591] NET: Registered protocol family 17
[    2.066619] Bluetooth: L2CAP ver 2.11
[    2.066622] Bluetooth: L2CAP socket layer initialized
[    2.066625] Bluetooth: SCO (Voice Link) ver 0.6
[    2.066627] Bluetooth: SCO socket layer initialized
[    2.066687] Bluetooth: RFCOMM socket layer initialized
[    2.066703] Bluetooth: RFCOMM TTY layer initialized
[    2.066707] Bluetooth: RFCOMM ver 1.10
[    2.066784] Using IPI No-Shortcut mode
[    2.066906] registered taskstats version 1
[    2.067060]   Magic number: 13:526:790
[    2.067148] rtc_cmos 00:03: setting system clock to 2009-10-09 15:46:45 UTC (1255103205)
[    2.067152] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.067154] EDD information not available.
[    2.067699] Freeing unused kernel memory: 532k freed
[    2.067881] Write protecting the kernel text: 4120k
[    2.067949] Write protecting the kernel read-only data: 1524k
[    2.441057] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    2.517616] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.517624] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    2.517687] via-rhine 0000:02:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.524502] eth0: VIA Rhine III at 0xfa403000, 00:0c:76:a8:82:92, IRQ 20.
[    2.525219] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    2.576377] usb 1-3: configuration #1 chosen from 1 choice
[    2.583973] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.636991] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fa404000-fa4047ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.884084] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.030040] Initializing USB Mass Storage driver...
[    3.049489] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.056082] usb-storage: device found at 3
[    3.056086] usb-storage: waiting for device to settle before scanning
[    3.056105] usbcore: registered new interface driver usb-storage
[    3.056114] USB Mass Storage support registered.
[    3.114048] usb 2-1: configuration #1 chosen from 1 choice
[    3.129278] usbcore: registered new interface driver hiddev
[    3.161933] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[    3.164860] generic-usb 0003:04F2:0200.0001: input,hidraw0: USB HID v1.10 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input0
[    3.276451] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input5
[    3.276786] generic-usb 0003:04F2:0200.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input1
[    3.301660] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.2/input/input6
[    3.302051] generic-usb 0003:04F2:0200.0003: input,hidraw2: USB HID v1.10 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input2
[    3.302077] usbcore: registered new interface driver usbhid
[    3.302082] usbhid: v2.6:USB HID core driver
[    3.356026] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    3.480456] PM: Starting manual resume from disk
[    3.480462] PM: Resume from partition 8:5
[    3.480464] PM: Checking hibernation image.
[    3.480691] PM: Resume from disk failed.
[    3.485146] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.485151] EXT3-fs: write access will be enabled during recovery.
[    3.533103] usb 3-2: configuration #1 chosen from 1 choice
[    3.549313] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input7
[    3.553086] generic-usb 0003:046D:C00E.0004: input,hidraw3: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
[    3.932175] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000537c54]
[    5.691425] kjournald starting.  Commit interval 5 seconds
[    5.691442] EXT3-fs: recovery complete.
[    5.692065] EXT3-fs: mounted filesystem with ordered data mode.
[    8.056252] usb-storage: device scan complete
[    8.058093] scsi 2:0:0:0: Direct-Access     Generic  CF Card       CF 1.4B PQ: 0 ANSI: 0 CCS
[    8.059960] scsi 2:0:0:1: Direct-Access     Generic  MS Card       MS 1.4B PQ: 0 ANSI: 0 CCS
[    8.061710] scsi 2:0:0:2: Direct-Access     Generic  SD Card   MMC/SD 1.4B PQ: 0 ANSI: 0 CCS
[    8.063592] scsi 2:0:0:3: Direct-Access     Generic  SM/XD Card    SM 1.4B PQ: 0 ANSI: 0 CCS
[    8.065306] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.065385] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    8.066401] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    8.066470] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    8.067546] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    8.067610] sd 2:0:0:2: Attached scsi generic sg4 type 0
[    8.068656] sd 2:0:0:3: [sde] Attached SCSI removable disk
[    8.068714] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   10.743295] udev: starting version 141
[   10.863267] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.899329] Linux agpgart interface v0.103
[   10.913986] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   10.920292] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   11.133752] intel_rng: FWH not detected
[   11.256171] cfg80211: Calling CRDA to update world regulatory domain
[   11.650598] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   11.764892] iTCO_vendor_support: vendor-support=0
[   11.767405] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.767533] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   11.767661] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.868679] cfg80211: World regulatory domain updated:
[   11.868684] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.868688] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.868691] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.868694] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.868697] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.868700] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.021794] Linux video capture interface: v2.00
[   12.047344] p54pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.047606] p54pci 0000:02:00.0: firmware: requesting isl3886
[   12.179033] p54: LM86 firmware
[   12.179040] p54: FW rev 2.7.0.0 - Softmac protocol 4.1
[   12.307616] saa7130/34: v4l2 driver version 0.2.14 loaded
[   12.482867] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.483012] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.804014] intel8x0_measure_ac97_clock: measured 55089 usecs
[   12.804018] intel8x0: clocking to 48000
[   13.033033] p54: unknown eeprom code : 0x1
[   13.033039] p54: unknown eeprom code : 0x1007
[   13.033043] p54: unknown eeprom code : 0x1008
[   13.033048] p54: unknown eeprom code : 0x1100
[   13.033052] p54: unknown eeprom code : 0x3
[   13.033056] p54: unknown eeprom code : 0x1905
[   13.033069] phy0: hwaddr 00:60:b3:92:13:75, MAC:isl3890 RF:Frisbee
[   13.035075] phy0: Selected rate control algorithm 'pid'
[   13.105414] saa7134 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.105427] saa7134[0]: found at 0000:02:02.0, rev: 1, irq: 18, latency: 32, mmio: 0xfa402000
[   13.105438] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   13.105580] saa7134[0]: board init: gpio is 0
[   13.256049] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   13.256074] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[   13.256097] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256120] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256142] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256165] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256187] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256210] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256233] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256256] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256281] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256304] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256326] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256348] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256370] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.256392] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.392118] tuner' 0-0043: chip found @ 0x86 (saa7134[0])
[   13.400154] tda9887 0-0043: creating new instance
[   13.400159] tda9887 0-0043: tda988[5/6/7] found
[   13.432016] All bytes are equal. It is not a TEA5767
[   13.432124] tuner' 0-0060: chip found @ 0xc0 (saa7134[0])
[   13.452013] saa7134[0] Tuner type is 38
[   13.468017] tuner-simple 0-0060: creating new instance
[   13.468022] tuner-simple 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   13.524188] saa7134[0]: registered device video0 [v4l2]
[   13.524239] saa7134[0]: registered device vbi0
[   13.524284] saa7134[0]: registered device radio0
[   13.553902] saa7134 ALSA driver for DMA sound loaded
[   13.554162] saa7134[0]/alsa: saa7134[0] at 0xfa402000 irq 18 registered as card -2
[   13.573191] dvb_init() allocating 1 frontend
[   13.606295] tda10046: chip is not answering. Giving up.
[   13.606454] saa7134[0]/dvb: frontend initialization failed
[   13.802755] lp: driver loaded but no devices found
[   13.922284] Adding 4522256k swap on /dev/sda5.  Priority:-1 extents:1 across:4522256k
[   14.480353] EXT3 FS on sda1, internal journal
[   15.436311] kjournald starting.  Commit interval 5 seconds
[   15.444228] EXT3 FS on sda3, internal journal
[   15.444236] EXT3-fs: mounted filesystem with ordered data mode.
[   15.703584] type=1505 audit(1255103219.132:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2375
[   15.757120] type=1505 audit(1255103219.188:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2379
[   15.757367] type=1505 audit(1255103219.188:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2379
[   15.757448] type=1505 audit(1255103219.188:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2379
[   15.757502] type=1505 audit(1255103219.188:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2379
[   15.901191] type=1505 audit(1255103219.332:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2384
[   15.901455] type=1505 audit(1255103219.332:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2384
[   15.936052] type=1505 audit(1255103219.368:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2388
[   25.165689] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.165695] Bluetooth: BNEP filters: protocol multicast
[   25.180132] Bridge firewalling registered
[   26.154989] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.308435] ppdev: user-space parallel port driver
[   26.401975] [drm] Initialized drm 1.1.0 20060810
[   26.440205] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   26.655677] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   26.655699] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   26.655738] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   26.930543] [drm] Setting GART location based on new memory map
[   26.930552] [drm] Loading R300 Microcode
[   26.930586] [drm] Num pipes: 2
[   26.930595] [drm] writeback test succeeded in 1 usecs
[   30.567031] eth0: link down
[   30.567280] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.569089] p54pci 0000:02:00.0: firmware: requesting isl3886
[   30.693379] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.336431] wlan0: direct probe to AP 00:16:01:b0:43:12 try 1
[   58.342874] wlan0 direct probe responded
[   58.342881] wlan0: authenticate with AP 00:16:01:b0:43:12
[   58.344921] wlan0: authenticated
[   58.344926] wlan0: associate with AP 00:16:01:b0:43:12
[   58.347179] wlan0: RX AssocResp from 00:16:01:b0:43:12 (capab=0x411 status=0 aid=2)
[   58.347182] wlan0: associated
[   58.350904] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.365786] padlock: VIA PadLock not detected.
[   68.760009] wlan0: no IPv6 routers present

```

---

### Post by sshaikh on 2009-10-12
Anyone? Perhaps even a log setting I can use in order to have *something* to search onwards for in Google?

---

### Post by sshaikh on 2009-10-13
Really sorry to nag, but if this is the wrong place to ask about this problem could someone point me in the right direction? Excuse the impatience but I was actually expecting a bit more of a response from a community which is vocal about wanting to help new people utilise the platform...

---

### Post by karamu on 2009-10-13
You could try this thread:

[http://ubuntuforums.org/showthread.php?p=8089461#post8089461](http://ubuntuforums.org/showthread.php?p=8089461#post8089461)

Not sure if it's the same issue but it's worth a look.

---

### Post by Kevbert on 2009-10-13
How long have you run memtest for ? You'll probably need to run it for two or three passes.
Is the PC dusty inside ? You may need to clean out any excess dust (as this may become conductive over a period of time).
Do you only get the CPU reading 40C ? This is the default reading.
Also check all extension boards are properly seated into the motherboard.

---

### Post by sshaikh on 2009-10-13
Well I've updated my kernel (eep) and will report back if my server lasts more than a day. Thanks for the various pointers.

---

### Post by sshaikh on 2009-10-15
The updated kernel lasted until I resumed from hibernation after which it hard crashed taking my HD with it. The reinstall didn't take long, but this time I've not applied any of the latest updates.

It's been working for around 24 hours straight. Good enough for my purposes I think!

Thanks for all the help.

---

### Post by gazizn on 2009-11-19
Hi,

I would share my experience with Ubuntu Desktops.

My ubuntu32 on AMD64 was randomly freezing for long time. I started with version 6.x and currently I am on  9.10. I tried ATI proprietary and freeware drivers, all kind of kernel boot options, bios settings for power management, etc  but nothing helped. I also had a mac laptop so ubuntu problems was not the high priority for troubleshooting.

2 weeks ago I switched to console mode (alt-ctrl-f1) from gdm and machine is still running stable under pretty heavy load.

I suspect something is wrong in X or GNOME code that is upsetting kernel that much. If I have sometime I would try to analyze the kernel dump and post the results here.


Gaziz

---

