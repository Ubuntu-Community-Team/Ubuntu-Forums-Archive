---
title: "Ubuntu 8.04 LTS crashing with vertical lines down the screen"
date: 2009-10-24
forum: General Help
---

### Post by AgentY on 2009-10-24
I've recently installed a clean version of Ubuntu 8.04. Everything works fine apart from I've had 3 or 4 system crashes now. I've looked trhough the system log and cannot really tell what is happening;

Oct 24 12:08:15 yusuf-laptop -- MARK --
Oct 24 12:24:24 yusuf-laptop kernel: [ 8082.395071] usb 2-2: USB disconnect, address 2
Oct 24 12:25:40 yusuf-laptop syslogd 1.5.0#1ubuntu1: restart.
Oct 24 12:25:40 yusuf-laptop kernel: Inspecting /boot/System.map-2.6.24-25-generic
Oct 24 12:25:40 yusuf-laptop kernel: Loaded 27929 symbols from /boot/System.map-2.6.24-25-generic.
Oct 24 12:25:40 yusuf-laptop kernel: Symbols match kernel version 2.6.24.
Oct 24 12:25:40 yusuf-laptop kernel: Loaded 24248 symbols from 95 modules.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Linux version 2.6.24-25-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Oct 20 07:31:10 UTC 2009 (Ubuntu 2.6.24-25.63-generic)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ea0000 (usable)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 0000000077ea0000 - 0000000077eac000 (ACPI data)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 0000000077eac000 - 0000000077f00000 (ACPI NVS)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] 1022MB HIGHMEM available.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] 896MB LOWMEM available.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] found SMP MP-table at 000f7c70
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]   HighMem    229376 ->   491168
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Movable zone start PFN for each node
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000]     0:        0 ->   491168
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] DMI present.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7C40 checksum 0
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 PTLTD )
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: RSDT 77EA474D, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: FACP 77EABE3B, 0074 (r1 HP     Piranha   6040000 ATI     F4240)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: DSDT 77EA4781, 76BA (r1     HP     309B  6040000 MSFT  100000E)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: FACS 77EACFC0, 0040
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: SSDT 77EABEAF, 00CF (r1 PTLTD  POWERNOW  6040000  LTP        1)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: APIC 77EABF7E, 0046 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: MCFG 77EABFC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Processor #0 15:4 APIC version 16
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487331
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Kernel command line: root=UUID=d49dd3f8-107d-4559-a825-c6ceacc2867a ro quiet splash
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Initializing CPU#0
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    0.000000] Detected 1790.897 MHz processor.
Oct 24 12:25:40 yusuf-laptop kernel: [    6.239414] Console: colour VGA+ 80x25
Oct 24 12:25:40 yusuf-laptop kernel: [    6.239418] console [tty0] enabled
Oct 24 12:25:40 yusuf-laptop kernel: [    6.239861] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.240353] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322724] Memory: 1935776k/1964672k available (2181k kernel code, 27644k reserved, 1005k data, 368k init, 1047168k highmem)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322732] virtual kernel memory layout:
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322734]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322735]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322736]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322737]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322739]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322740]       .data : 0xc03216a6 - 0xc041cdc4   (1005 kB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322741]       .text : 0xc0100000 - 0xc03216a6   (2181 kB)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322744] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322787] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322835] Calibrating delay loop (skipped), using tsc calculated value.. 3581.79 BogoMIPS (lpj=7163588)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322868] Security Framework initialized
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322875] SELinux:  Disabled at boot.
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322893] AppArmor: AppArmor initialized
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322897] Failure registering capabilities with primary security module.
Oct 24 12:25:40 yusuf-laptop kernel: [    6.322906] Mount-cache hash table entries: 512
Oct 24 12:25:40 yusuf-laptop kernel: [    6.323039] Initializing cgroup subsys ns
Oct 24 12:25:40 yusuf-laptop kernel: [    6.323043] Initializing cgroup subsys cpuacct
Oct 24 12:25:40 yusuf-laptop kernel: [    6.323062] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.323065] CPU: L2 Cache: 512K (64 bytes/line)
Oct 24 12:25:40 yusuf-laptop kernel: [    6.323079] Compat vDSO mapped to ffffe000.
Oct 24 12:25:40 yusuf-laptop kernel: [    6.323092] Checking 'hlt' instruction... OK.
Oct 24 12:25:40 yusuf-laptop kernel: [    6.339095] SMP alternatives: switching to UP code
Oct 24 12:25:40 yusuf-laptop kernel: [    6.340224] Freeing SMP alternatives: 11k freed
Oct 24 12:25:40 yusuf-laptop kernel: [    6.340346] Early unpacking initramfs... done
Oct 24 12:25:40 yusuf-laptop kernel: [    6.683734] ACPI: Core revision 20070126
Oct 24 12:25:40 yusuf-laptop kernel: [    6.683822] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.325495] CPU0: AMD Turion(tm) 64 Mobile Technology ML-32 stepping 02
Oct 24 12:25:40 yusuf-laptop kernel: [    7.325509] Total of 1 processors activated (3581.79 BogoMIPS).
Oct 24 12:25:40 yusuf-laptop kernel: [    7.325680] ENABLING IO-APIC IRQs
Oct 24 12:25:40 yusuf-laptop kernel: [    7.325863] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Oct 24 12:25:40 yusuf-laptop kernel: [    7.473316] Brought up 1 CPUs
Oct 24 12:25:40 yusuf-laptop kernel: [    7.473502] net_namespace: 64 bytes
Oct 24 12:25:40 yusuf-laptop kernel: [    7.473510] Booting paravirtualized kernel on bare hardware
Oct 24 12:25:40 yusuf-laptop kernel: [    7.473966] Time: 12:25:14  Date: 10/24/09
Oct 24 12:25:40 yusuf-laptop kernel: [    7.473991] NET: Registered protocol family 16
Oct 24 12:25:40 yusuf-laptop kernel: [    7.474154] EISA bus registered
Oct 24 12:25:40 yusuf-laptop kernel: [    7.474177] ACPI: bus type pci registered
Oct 24 12:25:40 yusuf-laptop kernel: [    7.474379] PCI: PCI BIOS revision 2.10 entry at 0xfd86c, last bus=8
Oct 24 12:25:40 yusuf-laptop kernel: [    7.474381] PCI: Using configuration type 1
Oct 24 12:25:40 yusuf-laptop kernel: [    7.474389] Setting up standard PCI resources
Oct 24 12:25:40 yusuf-laptop kernel: [    7.477508] ACPI: Interpreter enabled
Oct 24 12:25:40 yusuf-laptop kernel: [    7.477511] ACPI: (supports S0 S3 S4 S5)
Oct 24 12:25:40 yusuf-laptop kernel: [    7.477521] ACPI: Using IOAPIC for interrupt routing
Oct 24 12:25:40 yusuf-laptop kernel: [    7.480626] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 24 12:25:40 yusuf-laptop kernel: [    7.525691] ACPI: EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
Oct 24 12:25:40 yusuf-laptop kernel: [    7.525693] ACPI: EC: driver started in interrupt mode
Oct 24 12:25:40 yusuf-laptop kernel: [    7.525730] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 24 12:25:40 yusuf-laptop kernel: [    7.527283] PCI: Transparent bridge - 0000:00:14.4
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529389] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529487] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529583] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529678] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529773] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529867] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.529962] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.530057] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.530164] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 24 12:25:40 yusuf-laptop kernel: [    7.530190] pnp: PnP ACPI init
Oct 24 12:25:40 yusuf-laptop kernel: [    7.530197] ACPI: bus type pnp registered
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553224] pnp: PnP ACPI: found 10 devices
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553226] ACPI: ACPI bus type pnp unregistered
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553230] PnPBIOS: Disabled by ACPI PNP
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553408] PCI: Using ACPI for IRQ routing
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553411] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553417] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
Oct 24 12:25:40 yusuf-laptop kernel: [    7.553419] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
Oct 24 12:25:40 yusuf-laptop kernel: [    7.593123] NET: Registered protocol family 8
Oct 24 12:25:40 yusuf-laptop kernel: [    7.593125] NET: Registered protocol family 20
Oct 24 12:25:40 yusuf-laptop kernel: [    7.593185] AppArmor: AppArmor Filesystem Enabled
Oct 24 12:25:40 yusuf-laptop kernel: [    7.597110] Time: tsc clocksource has been installed.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605129] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605133] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605136] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605143] system 00:08: ioport range 0x1080-0x1080 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605146] system 00:08: ioport range 0x40b-0x40b has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605149] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605151] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605154] system 00:08: ioport range 0x870-0x87f has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605156] system 00:08: ioport range 0xc00-0xc01 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605159] system 00:08: ioport range 0xc14-0xc14 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605161] system 00:08: ioport range 0xc50-0xc52 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605164] system 00:08: ioport range 0xc6c-0xc6c has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605167] system 00:08: ioport range 0xc6f-0xc6f has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605169] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605172] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605174] system 00:08: ioport range 0xcd8-0xcdf has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605177] system 00:08: ioport range 0x8000-0x805f has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605180] system 00:08: ioport range 0xf40-0xf47 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605182] system 00:08: ioport range 0x280-0x293 has been reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605188] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605191] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.605194] system 00:09: iomem range 0x0-0xfff could not be reserved
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635515] PCI: Bridge: 0000:00:01.0
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635517]   IO window: 9000-9fff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635521]   MEM window: b0100000-b01fffff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635523]   PREFETCH window: c0000000-cfffffff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635526] PCI: Bridge: 0000:00:05.0
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635527]   IO window: disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635530]   MEM window: disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635532]   PREFETCH window: disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635538] PCI: Bus 7, cardbus bridge: 0000:06:04.0
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635540]   IO window: 0000a400-0000a4ff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635545]   IO window: 0000a800-0000a8ff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635551]   PREFETCH window: 88000000-8bffffff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635557]   MEM window: 8c000000-8fffffff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635562] PCI: Bridge: 0000:00:14.4
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635565]   IO window: a000-afff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635571]   MEM window: b0200000-b02fffff
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635576]   PREFETCH window: disabled.
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635625] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 16
Oct 24 12:25:40 yusuf-laptop kernel: [    7.635640] NET: Registered protocol family 2
Oct 24 12:25:40 yusuf-laptop kernel: [    7.673092] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    7.673397] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    7.674408] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    7.674939] TCP: Hash tables configured (established 131072 bind 65536)
Oct 24 12:25:40 yusuf-laptop kernel: [    7.674942] TCP reno registered
Oct 24 12:25:40 yusuf-laptop kernel: [    7.685136] checking if image is initramfs... it is
Oct 24 12:25:40 yusuf-laptop kernel: [    8.343593] Freeing initrd memory: 7327k freed
Oct 24 12:25:40 yusuf-laptop kernel: [    8.344177] audit: initializing netlink socket (disabled)
Oct 24 12:25:40 yusuf-laptop kernel: [    8.344191] audit(1256387114.284:1): initialized
Oct 24 12:25:40 yusuf-laptop kernel: [    8.344360] highmem bounce pool size: 64 pages
Oct 24 12:25:40 yusuf-laptop kernel: [    8.345975] VFS: Disk quotas dquot_6.5.1
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346040] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346165] io scheduler noop registered
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346167] io scheduler anticipatory registered
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346169] io scheduler deadline registered
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346179] io scheduler cfq registered (default)
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346186] PCI: MSI quirk detected. MSI deactivated.
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346356] assign_interrupt_mode Found MSI capability
Oct 24 12:25:40 yusuf-laptop kernel: [    8.346549] isapnp: Scanning for PnP cards...
Oct 24 12:25:40 yusuf-laptop kernel: [    8.700230] isapnp: No Plug & Play device found
Oct 24 12:25:40 yusuf-laptop kernel: [    8.724777] Real Time Clock Driver v1.12ac
Oct 24 12:25:40 yusuf-laptop kernel: [    8.724869] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 24 12:25:40 yusuf-laptop kernel: [    8.725342] ACPI: PCI Interrupt 0000:00:14.6[b] -> GSI 17 (level, low) -> IRQ 17
Oct 24 12:25:40 yusuf-laptop kernel: [    8.725351] ACPI: PCI interrupt for device 0000:00:14.6 disabled
Oct 24 12:25:40 yusuf-laptop kernel: [    8.725914] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 24 12:25:40 yusuf-laptop kernel: [    8.725981] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 24 12:25:40 yusuf-laptop kernel: [    8.726060] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Oct 24 12:25:40 yusuf-laptop kernel: [    8.744883] i8042.c: Detected active multiplexing controller, rev 1.1.
Oct 24 12:25:40 yusuf-laptop kernel: [    8.760725] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 24 12:25:40 yusuf-laptop kernel: [    8.760729] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct 24 12:25:40 yusuf-laptop kernel: [    8.760732] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct 24 12:25:40 yusuf-laptop kernel: [    8.760734] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct 24 12:25:40 yusuf-laptop kernel: [    8.760737] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771491] mice: PS/2 mouse device common for all mice
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771590] EISA: Probing bus 0 at eisa.0
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771598] Cannot allocate resource for EISA slot 1
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771628] Cannot allocate resource for EISA slot 8
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771630] EISA: Detected 0 cards.
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771633] cpuidle: using governor ladder
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771635] cpuidle: using governor menu
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771723] NET: Registered protocol family 1
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771746] Using IPI No-Shortcut mode
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771775] registered taskstats version 1
Oct 24 12:25:40 yusuf-laptop kernel: [    8.771884]   Magic number: 13:474:431
Oct 24 12:25:40 yusuf-laptop kernel: [    8.772070] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 24 12:25:40 yusuf-laptop kernel: [    8.772072] EDD information not available.
Oct 24 12:25:40 yusuf-laptop kernel: [    8.772349] Freeing unused kernel memory: 368k freed
Oct 24 12:25:40 yusuf-laptop kernel: [    8.772372] Write protecting the kernel read-only data: 803k
Oct 24 12:25:40 yusuf-laptop kernel: [    8.791443] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct 24 12:25:40 yusuf-laptop kernel: [    9.983065] fuse init (API version 7.9)
Oct 24 12:25:40 yusuf-laptop kernel: [   10.017810] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 24 12:25:40 yusuf-laptop kernel: [   10.017818] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 24 12:25:40 yusuf-laptop kernel: [   10.034734] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Oct 24 12:25:40 yusuf-laptop kernel: [   10.041593] ACPI: Thermal Zone [THRM] (0 C)
Oct 24 12:25:40 yusuf-laptop kernel: [   10.567030] usbcore: registered new interface driver usbfs
Oct 24 12:25:40 yusuf-laptop kernel: [   10.567052] usbcore: registered new interface driver hub
Oct 24 12:25:40 yusuf-laptop kernel: [   10.572933] usbcore: registered new device driver usb
Oct 24 12:25:40 yusuf-laptop kernel: [   10.584965] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
Oct 24 12:25:40 yusuf-laptop kernel: [   10.584980] ohci_hcd 0000:00:13.0: OHCI Host Controller
Oct 24 12:25:40 yusuf-laptop kernel: [   10.585226] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Oct 24 12:25:40 yusuf-laptop kernel: [   10.585247] ohci_hcd 0000:00:13.0: irq 18, io mem 0xb0000000
Oct 24 12:25:40 yusuf-laptop kernel: [   10.612869] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 24 12:25:40 yusuf-laptop kernel: [   10.612876] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 24 12:25:40 yusuf-laptop kernel: [   10.644914] usb usb1: configuration #1 chosen from 1 choice
Oct 24 12:25:40 yusuf-laptop kernel: [   10.644941] hub 1-0:1.0: USB hub found
Oct 24 12:25:40 yusuf-laptop kernel: [   10.644952] hub 1-0:1.0: 4 ports detected
Oct 24 12:25:40 yusuf-laptop kernel: [   10.710105] 8139too Fast Ethernet driver 0.9.28
Oct 24 12:25:40 yusuf-laptop kernel: [   10.748763] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
Oct 24 12:25:40 yusuf-laptop kernel: [   10.748780] ohci_hcd 0000:00:13.1: OHCI Host Controller
Oct 24 12:25:40 yusuf-laptop kernel: [   10.748805] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Oct 24 12:25:40 yusuf-laptop kernel: [   10.748822] ohci_hcd 0000:00:13.1: irq 18, io mem 0xb0001000
Oct 24 12:25:40 yusuf-laptop kernel: [   10.808679] usb usb2: configuration #1 chosen from 1 choice
Oct 24 12:25:40 yusuf-laptop kernel: [   10.808710] hub 2-0:1.0: USB hub found
Oct 24 12:25:40 yusuf-laptop kernel: [   10.808721] hub 2-0:1.0: 4 ports detected
Oct 24 12:25:40 yusuf-laptop kernel: [   10.912616] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
Oct 24 12:25:40 yusuf-laptop kernel: [   10.912633] ehci_hcd 0000:00:13.2: EHCI Host Controller
Oct 24 12:25:40 yusuf-laptop kernel: [   10.912657] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Oct 24 12:25:40 yusuf-laptop kernel: [   10.912713] ehci_hcd 0000:00:13.2: irq 18, io mem 0xb0002000
Oct 24 12:25:40 yusuf-laptop kernel: [   10.924411] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 24 12:25:40 yusuf-laptop kernel: [   10.924530] usb usb3: configuration #1 chosen from 1 choice
Oct 24 12:25:40 yusuf-laptop kernel: [   10.924552] hub 3-0:1.0: USB hub found
Oct 24 12:25:40 yusuf-laptop kernel: [   10.924559] hub 3-0:1.0: 8 ports detected
Oct 24 12:25:40 yusuf-laptop kernel: [   11.028512] ATIIXP: IDE controller (0x1002:0x4376 rev 0x00) at  PCI slot 0000:00:14.1
Oct 24 12:25:40 yusuf-laptop kernel: [   11.028535] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
Oct 24 12:25:40 yusuf-laptop kernel: [   11.028544] ATIIXP: not 100% native mode: will probe irqs later
Oct 24 12:25:40 yusuf-laptop kernel: [   11.028554]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
Oct 24 12:25:40 yusuf-laptop kernel: [   11.028568]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
Oct 24 12:25:40 yusuf-laptop kernel: [   11.987317] hda: WDC WD1600BEVE-00UYT0, ATA DISK drive
Oct 24 12:25:40 yusuf-laptop kernel: [   11.988333] hda: UDMA/100 mode selected
Oct 24 12:25:40 yusuf-laptop kernel: [   11.988438] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 24 12:25:40 yusuf-laptop kernel: [   13.101735] hdc: HL-DT-ST DVDRAM GSA-4082N, ATAPI CD/DVD-ROM drive
Oct 24 12:25:40 yusuf-laptop kernel: [   13.102813] hdc: MWDMA2 mode selected
Oct 24 12:25:40 yusuf-laptop kernel: [   13.103329] ide1 at 0x170-0x177,0x376 on irq 15
Oct 24 12:25:40 yusuf-laptop kernel: [   13.115217] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 20
Oct 24 12:25:40 yusuf-laptop kernel: [   13.115844] SCSI subsystem initialized
Oct 24 12:25:40 yusuf-laptop kernel: [   13.133278] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
Oct 24 12:25:40 yusuf-laptop kernel: [   13.133290] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
Oct 24 12:25:40 yusuf-laptop kernel: [   13.133300] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
Oct 24 12:25:40 yusuf-laptop kernel: [   13.133309] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
Oct 24 12:25:40 yusuf-laptop kernel: [   13.173246] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
Oct 24 12:25:40 yusuf-laptop kernel: [   13.173553] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 21
Oct 24 12:25:40 yusuf-laptop kernel: [   13.174727] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:c7:23:ed, IRQ 21
Oct 24 12:25:40 yusuf-laptop kernel: [   13.176369] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 23 (level, low) -> IRQ 22
Oct 24 12:25:40 yusuf-laptop kernel: [   13.226070] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[b0209000-b02097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Oct 24 12:25:40 yusuf-laptop kernel: [   13.235257] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Oct 24 12:25:40 yusuf-laptop kernel: [   13.252625] hda: max request size: 512KiB
Oct 24 12:25:40 yusuf-laptop kernel: [   13.303291] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63
Oct 24 12:25:40 yusuf-laptop kernel: [   13.303446] hda: cache flushes supported
Oct 24 12:25:40 yusuf-laptop kernel: [   13.303486]  hda: hda1 hda2 hda3 hda4
Oct 24 12:25:40 yusuf-laptop kernel: [   13.348932] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Oct 24 12:25:40 yusuf-laptop kernel: [   13.348941] Uniform CD-ROM driver Revision: 3.20
Oct 24 12:25:40 yusuf-laptop kernel: [   13.811889] Attempting manual resume
Oct 24 12:25:40 yusuf-laptop kernel: [   13.824921] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 24 12:25:40 yusuf-laptop kernel: [   13.824926] EXT3-fs: write access will be enabled during recovery.
Oct 24 12:25:40 yusuf-laptop kernel: [   16.647797] kjournald starting.  Commit interval 5 seconds
Oct 24 12:25:40 yusuf-laptop kernel: [   16.647816] EXT3-fs: hda2: orphan cleanup on readonly fs
Oct 24 12:25:40 yusuf-laptop kernel: [   16.647856] EXT3-fs: hda2: 2 orphan inodes deleted
Oct 24 12:25:40 yusuf-laptop kernel: [   16.647858] EXT3-fs: recovery complete.
Oct 24 12:25:40 yusuf-laptop kernel: [   16.650658] EXT3-fs: mounted filesystem with ordered data mode.
Oct 24 12:25:40 yusuf-laptop kernel: [   24.344537] input: PC Speaker as /devices/platform/pcspkr/input/input2
Oct 24 12:25:40 yusuf-laptop kernel: [   25.652642] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 24 12:25:40 yusuf-laptop kernel: [   25.683485] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 24 12:25:40 yusuf-laptop kernel: [   25.807229] Linux agpgart interface v0.102
Oct 24 12:25:40 yusuf-laptop kernel: [   25.927876] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Oct 24 12:25:40 yusuf-laptop kernel: [   26.214869] input: Power Button (FF) as /devices/virtual/input/input3
Oct 24 12:25:40 yusuf-laptop kernel: [   26.242664] ACPI: Power Button (FF) [PWRF]
Oct 24 12:25:40 yusuf-laptop kernel: [   26.242768] input: Sleep Button (FF) as /devices/virtual/input/input4
Oct 24 12:25:40 yusuf-laptop kernel: [   26.266607] ACPI: Sleep Button (FF) [SLPF]
Oct 24 12:25:40 yusuf-laptop kernel: [   26.266705] input: Lid Switch as /devices/virtual/input/input5
Oct 24 12:25:40 yusuf-laptop kernel: [   26.278708] ACPI: Lid Switch [LID]
Oct 24 12:25:40 yusuf-laptop kernel: [   26.278794] input: Power Button (CM) as /devices/virtual/input/input6
Oct 24 12:25:40 yusuf-laptop kernel: [   26.306508] ACPI: Power Button (CM) [PWRB]
Oct 24 12:25:40 yusuf-laptop kernel: [   26.603607] ACPI: WMI-Acer: Mapper loaded
Oct 24 12:25:40 yusuf-laptop kernel: [   26.733969] Yenta: CardBus bridge found at 0000:06:04.0 [103c:30a4]
Oct 24 12:25:40 yusuf-laptop kernel: [   26.734005] Yenta: Enabling burst memory read transactions
Oct 24 12:25:40 yusuf-laptop kernel: [   26.734016] Yenta: Using INTVAL to route CSC interrupts to PCI
Oct 24 12:25:40 yusuf-laptop kernel: [   26.734017] Yenta: Routing CardBus interrupts to ISA
Oct 24 12:25:40 yusuf-laptop kernel: [   26.734024] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
Oct 24 12:25:40 yusuf-laptop kernel: [   26.966367] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Oct 24 12:25:40 yusuf-laptop kernel: [   26.966378] Socket status: 30000006
Oct 24 12:25:40 yusuf-laptop kernel: [   26.966381] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Oct 24 12:25:40 yusuf-laptop kernel: [   26.966384] cs: IO port probe 0xa000-0xafff: clean.
Oct 24 12:25:40 yusuf-laptop kernel: [   26.966667] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
Oct 24 12:25:40 yusuf-laptop kernel: [   26.997567] ACPI: PCI Interrupt 0000:06:04.3[b] -> GSI 23 (level, low) -> IRQ 22
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305090] sdhci: Secure Digital Host Controller Interface driver
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305094] sdhci: Copyright(c) Pierre Ossman
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305169] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305199] ACPI: PCI Interrupt 0000:06:04.4[A] -> GSI 20 (level, low) -> IRQ 16
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305231] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305296] mmc0: SDHCI at 0xb020a000 irq 16 DMA
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305312] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305350] mmc1: SDHCI at 0xb0209c00 irq 16 DMA
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305366] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
Oct 24 12:25:40 yusuf-laptop kernel: [   27.305399] mmc2: SDHCI at 0xb0209800 irq 16 DMA
Oct 24 12:25:40 yusuf-laptop kernel: [   27.795403] ACPI: AC Adapter [ACAD] (off-line)
Oct 24 12:25:40 yusuf-laptop kernel: [   27.866310] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
Oct 24 12:25:40 yusuf-laptop kernel: [   27.909247] ACPI: PCI Interrupt 0000:00:14.5[b] -> GSI 17 (level, low) -> IRQ 17
Oct 24 12:25:40 yusuf-laptop kernel: [   27.933599] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Oct 24 12:25:40 yusuf-laptop kernel: [   27.940850] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Oct 24 12:25:40 yusuf-laptop kernel: [   28.435508] [fglrx] Maximum main memory to use for locked dma buffers: 1776 MBytes.
Oct 24 12:25:40 yusuf-laptop kernel: [   28.435552] [fglrx] ASYNCIO init succeed!
Oct 24 12:25:40 yusuf-laptop kernel: [   28.435703] [fglrx] PAT is enabled successfully!
Oct 24 12:25:40 yusuf-laptop kernel: [   28.436253] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Oct 24 12:25:40 yusuf-laptop kernel: [   28.573904] ACPI: Battery Slot [BAT1] (battery present)
Oct 24 12:25:40 yusuf-laptop kernel: [   28.728799] ACPI: PCI Interrupt 0000:00:14.6[b] -> GSI 17 (level, low) -> IRQ 17
Oct 24 12:25:40 yusuf-laptop kernel: [   28.787615] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/LNXVIDEO:00/input/input8
Oct 24 12:25:40 yusuf-laptop kernel: [   28.815051] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct 24 12:25:40 yusuf-laptop kernel: [   28.838920] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 0 converters and GPIO not ready (0x1)
Oct 24 12:25:40 yusuf-laptop kernel: [   30.565963] cs: IO port probe 0x100-0x3af: clean.
Oct 24 12:25:40 yusuf-laptop kernel: [   30.569042] cs: IO port probe 0x3e0-0x4ff: clean.
Oct 24 12:25:40 yusuf-laptop kernel: [   30.570328] cs: IO port probe 0x820-0x8ff: clean.
Oct 24 12:25:40 yusuf-laptop kernel: [   30.571347] cs: IO port probe 0xc00-0xcf7: clean.
Oct 24 12:25:40 yusuf-laptop kernel: [   30.572471] cs: IO port probe 0xa00-0xaff: clean.
Oct 24 12:25:40 yusuf-laptop kernel: [   30.954312] lp: driver loaded but no devices found
Oct 24 12:25:40 yusuf-laptop kernel: [   31.095688] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Oct 24 12:25:40 yusuf-laptop kernel: [   31.188485] usbcore: registered new interface driver ndiswrapper
Oct 24 12:25:40 yusuf-laptop kernel: [   31.259639] Adding 1951888k swap on /dev/hda3.  Priority:-1 extents:1 across:1951888k
Oct 24 12:25:40 yusuf-laptop kernel: [   31.294410] EXT3 FS on hda2, internal journal
Oct 24 12:25:40 yusuf-laptop kernel: [   31.995192] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 24 12:25:40 yusuf-laptop kernel: [   32.580431] No dock devices found.
Oct 24 12:25:40 yusuf-laptop kernel: [   32.866160] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (1 cpu cores) (version 2.20.00)
Oct 24 12:25:40 yusuf-laptop kernel: [   32.866215] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
Oct 24 12:25:40 yusuf-laptop kernel: [   32.866217] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
Oct 24 12:25:40 yusuf-laptop kernel: [   32.866226] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
Oct 24 12:25:40 yusuf-laptop kernel: [   37.031736] Time: acpi_pm clocksource has been installed.
Oct 24 12:25:41 yusuf-laptop kernel: [   38.053448] apm: BIOS not found.
Oct 24 12:25:41 yusuf-laptop kernel: [   38.323297] ppdev: user-space parallel port driver
Oct 24 12:25:41 yusuf-laptop kernel: [   38.424431] audit(1256383541.535:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4936 profile="/usr/sbin/cupsd" namespace="default"
Oct 24 12:25:42 yusuf-laptop kernel: [   39.094691] ACPI: PCI interrupt for device 0000:06:02.0 disabled
Oct 24 12:25:42 yusuf-laptop kernel: [   39.242036] usbcore: deregistering interface driver ndiswrapper
Oct 24 12:25:42 yusuf-laptop kernel: [   39.280788] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Oct 24 12:25:42 yusuf-laptop kernel: [   78.696860] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Oct 24 12:25:42 yusuf-laptop kernel: [   78.698201] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 20
Oct 24 12:25:42 yusuf-laptop kernel: [   78.709296] ndiswrapper: using IRQ 20
Oct 24 12:25:42 yusuf-laptop kernel: [   79.082939] wlan0: ethernet device 00:14:a5:73:20:c4 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
Oct 24 12:25:42 yusuf-laptop kernel: [   79.084195] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 24 12:25:42 yusuf-laptop kernel: [   79.085130] usbcore: registered new interface driver ndiswrapper
Oct 24 12:25:42 yusuf-laptop kernel: [   79.089282] Clocksource tsc unstable (delta = -231546648 ns)
Oct 24 12:25:43 yusuf-laptop dhcdbd: Started up.


Above is the system log prior to the system crash. 

The only thing that I have "played around with" is XRandR (which caused resolution problems, so xrandr may be the issue, although I believe it has been disabled).

Any help would be appreciated - Otherwise I may have to try another clean install and not use randr (I've rerad since I used randr that it's not a wise move to be using it!).

Once the veritcal lines appear on the screen, I have to power the machine off to get Ubuntu working again.

I have an ATI 200M Radeon Xpress built-in GPU.

If more detail is needed, please let me know.

It may also be worth mentioning that EVERY time I have crashed, RhythmBox Music Player has been running. (All music files are stored on a NTFS partition so both Linux and Windows can use the music collection. Im not sure if this is relevant info but thought I'd keep it as detailed as possible for the best feedback.)

Thanks in advance,

Y.

---

### Post by izg on 2009-10-24
The quickest solution is to go into recovery mode and do "xfix" just to get past blank screens. Of course, you won't have a properly functioning video driver.

I'm experiencing video driver problems after updating 8.04 also.

I've downloaded the latest ATI drivers and followed these instructions (perhaps I'll try again), which are very comprehensive with no luck:
[http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)

good luck.

---

