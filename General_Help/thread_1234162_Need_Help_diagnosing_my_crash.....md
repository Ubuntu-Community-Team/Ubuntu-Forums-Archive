---
title: "Need Help diagnosing my crash...."
date: 2009-08-07
forum: General Help
---

### Post by dblagbro on 2009-08-07
I've pulled out these logs (dmesg & /var/log/messages) but I don't know what I'm looking at.

My Ubuntu Server 8.04 is crashing daily - it's running VMWare and I'm starting to think that it's something with VMServer2.0 that's causing this.  


Please help!!
-d

DMESG:



[    0.000000] ACPI: SSDT DBF7F040, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20060113)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000200000000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 900976) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 2097152) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000200000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  2097152
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   900976
[    0.000000]     0:  1048576 ->  2097152
[    0.000000] On node 0 totalpages: 1949453
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1332 pages reserved
[    0.000000]   DMA zone: 2609 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 882600 pages, LIFO batch:31
[    0.000000]   Normal zone: 14336 pages used for memmap
[    0.000000]   Normal zone: 1034240 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000dbf70000 - 00000000dbf7e000
[    0.000000] swsusp: Registered nosave memory region: 00000000dbf7e000 - 00000000dbfd0000
[    0.000000] swsusp: Registered nosave memory region: 00000000dbfd0000 - 00000000dc000000
[    0.000000] swsusp: Registered nosave memory region: 00000000dc000000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ffe00000
[    0.000000] swsusp: Registered nosave memory region: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dc000000:22e00000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41952 bytes of per cpu data
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1919449
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=1907041a-19c1-45fc-ac59-d49c3b805a86 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   94.232069] time.c: Detected 2833.012 MHz processor.
[   94.234073] Console: colour VGA+ 80x25
[   94.234076] console [tty0] enabled
[   94.234088] Checking aperture...
[   94.234094] Calgary: detecting Calgary via BIOS EBDA area
[   94.234095] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   94.234097] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   94.254903] Placing software IO TLB between 0x1067000 - 0x5067000
[   94.297689] Memory: 7604048k/8388608k available (2529k kernel code, 193764k reserved, 1331k data, 328k init)
[   94.297713] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   94.441797] Calibrating delay using timer specific routine.. 5668.96 BogoMIPS (lpj=28344820)
[   94.441816] Security Framework initialized
[   94.441820] SELinux:  Disabled at boot.
[   94.441827] AppArmor: AppArmor initialized
[   94.441830] Failure registering capabilities with primary security module.
[   94.442303] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[   94.445041] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   94.446325] Mount-cache hash table entries: 256
[   94.446412] Initializing cgroup subsys ns
[   94.446415] Initializing cgroup subsys cpuacct
[   94.446425] CPU: L1 I cache: 32K, L1 D cache: 32K
[   94.446427] CPU 0/0 -> Node 0
[   94.446428] using mwait in idle threads.
[   94.446429] CPU: Physical Processor ID: 0
[   94.446430] CPU: Processor Core ID: 0
[   94.446435] CPU0: Thermal monitoring enabled (TM2)
[   94.446444] SMP alternatives: switching to UP code
[   94.447043] Early unpacking initramfs... done
[   94.681054] ACPI: Core revision 20070126
[   94.681089] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   94.783584] Using local APIC timer interrupts.
[   94.818841] APIC timer calibration result 20830959
[   94.818842] Detected 20.830 MHz APIC timer.
[   94.818891] SMP alternatives: switching to SMP code
[   94.819423] Booting processor 1/4 APIC 0x1
[   94.830000] Initializing CPU#1
[   94.978644] Calibrating delay using timer specific routine.. 5666.03 BogoMIPS (lpj=28330181)
[   94.978649] CPU: L1 I cache: 32K, L1 D cache: 32K
[   94.978650] CPU 1/1 -> Node 0
[   94.978651] CPU: Physical Processor ID: 0
[   94.978652] CPU: Processor Core ID: 0
[   94.978657] CPU1: Thermal monitoring enabled (TM2)
[   94.979297] Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz stepping 0a
[   94.979363] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   94.999398] SMP alternatives: switching to SMP code
[   94.999947] Booting processor 2/4 APIC 0x2
[   95.010519] Initializing CPU#2
[   95.158418] Calibrating delay using timer specific routine.. 5666.06 BogoMIPS (lpj=28330301)
[   95.158423] CPU: L1 I cache: 32K, L1 D cache: 32K
[   95.158424] CPU 2/2 -> Node 0
[   95.158425] CPU: Physical Processor ID: 0
[   95.158426] CPU: Processor Core ID: 0
[   95.158431] CPU2: Thermal monitoring enabled (TM2)
[   95.159071] Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz stepping 0a
[   95.159088] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   95.179111] SMP alternatives: switching to SMP code
[   95.179496] Booting processor 3/4 APIC 0x3
[   95.190067] Initializing CPU#3
[   95.338192] Calibrating delay using timer specific routine.. 5666.06 BogoMIPS (lpj=28330309)
[   95.338197] CPU: L1 I cache: 32K, L1 D cache: 32K
[   95.338198] CPU 3/3 -> Node 0
[   95.338199] CPU: Physical Processor ID: 0
[   95.338200] CPU: Processor Core ID: 0
[   95.338205] CPU3: Thermal monitoring enabled (TM2)
[   95.338845] Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz stepping 0a
[   95.338936] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   95.358927] Brought up 4 CPUs
[   95.359003] CPU0 attaching sched-domain:
[   95.359005]  domain 0: span 00000000,0000000f
[   95.359006]   groups: 00000000,00000001 00000000,00000002 00000000,00000004 00000000,00000008
[   95.359009]   domain 1: span 00000000,0000000f
[   95.359010]    groups: 00000000,0000000f
[   95.359012]    domain 2: span 00000000,0000000f
[   95.359013]     groups: 00000000,0000000f
[   95.359015] CPU1 attaching sched-domain:
[   95.359016]  domain 0: span 00000000,0000000f
[   95.359017]   groups: 00000000,00000002 00000000,00000004 00000000,00000008 00000000,00000001
[   95.359020]   domain 1: span 00000000,0000000f
[   95.359021]    groups: 00000000,0000000f
[   95.359022]    domain 2: span 00000000,0000000f
[   95.359023]     groups: 00000000,0000000f
[   95.359025] CPU2 attaching sched-domain:
[   95.359026]  domain 0: span 00000000,0000000f
[   95.359027]   groups: 00000000,00000004 00000000,00000008 00000000,00000001 00000000,00000002
[   95.359030]   domain 1: span 00000000,0000000f
[   95.359031]    groups: 00000000,0000000f
[   95.359032]    domain 2: span 00000000,0000000f
[   95.359033]     groups: 00000000,0000000f
[   95.359035] CPU3 attaching sched-domain:
[   95.359036]  domain 0: span 00000000,0000000f
[   95.359037]   groups: 00000000,00000008 00000000,00000001 00000000,00000002 00000000,00000004
[   95.359040]   domain 1: span 00000000,0000000f
[   95.359041]    groups: 00000000,0000000f
[   95.359042]    domain 2: span 00000000,0000000f
[   95.359043]     groups: 00000000,0000000f
[   95.359397] net_namespace: 120 bytes
[   95.359695] Time: 14:12:19  Date: 08/07/09
[   95.359713] NET: Registered protocol family 16
[   95.360001] ACPI: bus type pci registered
[   95.360102] PCI: Using configuration type 1
[   95.363243] ACPI: EC: Look up EC in DSDT
[   95.369803] ACPI: Interpreter enabled
[   95.369805] ACPI: (supports S0 S1 S3 S4 S5)
[   95.369820] ACPI: Using IOAPIC for interrupt routing
[   95.370045] Error attaching device data
[   95.370096] Error attaching device data
[   95.370146] Error attaching device data
[   95.370196] Error attaching device data
[   95.374942] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   95.376342] PCI: Transparent bridge - 0000:00:1e.0
[   95.376365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   95.376479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   95.376540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   95.376624] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   95.376683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   95.376753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   95.379178] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   95.379262] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   95.379345] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   95.379427] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   95.379510] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   95.379595] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   95.379678] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   95.379761] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   95.379888] Linux Plug and Play Support v0.97 (c) Adam Belay
[   95.379929] pnp: PnP ACPI init
[   95.379933] ACPI: bus type pnp registered
[   95.382040] pnp: PnP ACPI: found 15 devices
[   95.382041] ACPI: ACPI bus type pnp unregistered
[   95.382440] PCI: Using ACPI for IRQ routing
[   95.382442] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   95.428067] NET: Registered protocol family 8
[   95.428068] NET: Registered protocol family 20
[   95.428094] NetLabel: Initializing
[   95.428095] NetLabel:  domain hash size = 128
[   95.428096] NetLabel:  protocols = UNLABELED CIPSOv4
[   95.428108] NetLabel:  unlabeled traffic allowed by default
[   95.428114] PCI-GART: No AMD northbridge found.
[   95.428118] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   95.428122] hpet0: 4 64-bit timers, 14318180 Hz
[   95.429148] AppArmor: AppArmor Filesystem Enabled
[   95.437306] Time: tsc clocksource has been installed.
[   95.437312] Switched to high resolution mode on CPU 0
[   95.438044] Switched to high resolution mode on CPU 2
[   95.438046] Switched to high resolution mode on CPU 1
[   95.438121] Switched to high resolution mode on CPU 3
[   95.459802] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   95.459808] system 00:06: ioport range 0x290-0x29f has been reserved
[   95.459812] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   95.459815] system 00:07: ioport range 0x800-0x87f has been reserved
[   95.459817] system 00:07: ioport range 0x500-0x57f has been reserved
[   95.459819] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[   95.459821] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   95.459824] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[   95.459826] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[   95.459831] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[   95.459835] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   95.459838] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   95.459843] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   95.459847] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   95.459850] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   95.459852] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   95.459854] system 00:0e: iomem range 0x100000-0xdbffffff could not be reserved
[   95.459857] system 00:0e: iomem range 0xe0000000-0xffffffff could not be reserved
[   95.460389] PCI: Bridge: 0000:01:00.0
[   95.460390]   IO window: disabled.
[   95.460392]   MEM window: fe800000-fe8fffff
[   95.460394]   PREFETCH window: dff00000-dfffffff
[   95.460397] PCI: Bridge: 0000:01:00.2
[   95.460398]   IO window: disabled.
[   95.460400]   MEM window: disabled.
[   95.460402]   PREFETCH window: disabled.
[   95.460405] PCI: Bridge: 0000:00:01.0
[   95.460405]   IO window: disabled.
[   95.460407]   MEM window: fe800000-fe8fffff
[   95.460409]   PREFETCH window: dff00000-dfffffff
[   95.460411] PCI: Bridge: 0000:00:1c.0
[   95.460411]   IO window: disabled.
[   95.460414]   MEM window: disabled.
[   95.460416]   PREFETCH window: eff00000-efffffff
[   95.460419] PCI: Bridge: 0000:00:1c.4
[   95.460421]   IO window: d000-dfff
[   95.460423]   MEM window: fea00000-feafffff
[   95.460426]   PREFETCH window: disabled.
[   95.460428] PCI: Bridge: 0000:00:1c.5
[   95.460430]   IO window: c000-cfff
[   95.460433]   MEM window: fe900000-fe9fffff
[   95.460435]   PREFETCH window: disabled.
[   95.460439] PCI: Bridge: 0000:00:1e.0
[   95.460440]   IO window: e000-efff
[   95.460443]   MEM window: feb00000-febfffff
[   95.460446]   PREFETCH window: f0000000-f7ffffff
[   95.460455] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   95.460457] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   95.460466] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   95.460476] PCI: Setting latency timer of device 0000:01:00.2 to 64
[   95.460487] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   95.460490] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   95.460502] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   95.460505] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   95.460516] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   95.460519] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   95.460525] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   95.460531] NET: Registered protocol family 2
[   95.569845] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   95.570681] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   95.572738] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   95.573061] TCP: Hash tables configured (established 524288 bind 65536)
[   95.573063] TCP reno registered
[   95.599738] checking if image is initramfs... it is
[   96.060862] Freeing initrd memory: 7347k freed
[   96.063253] audit: initializing netlink socket (disabled)
[   96.063262] audit(1249654339.781:1): initialized
[   96.063798] Total HugeTLB memory allocated, 0
[   96.066062] VFS: Disk quotas dquot_6.5.1
[   96.066125] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   96.066281] io scheduler noop registered
[   96.066282] io scheduler anticipatory registered
[   96.066283] io scheduler deadline registered (default)
[   96.066392] io scheduler cfq registered
[   96.071480] Boot video device is 0000:07:00.0
[   96.071634] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   96.071652] assign_interrupt_mode Found MSI capability
[   96.071668] Allocate Port Service[0000:00:01.0:pcie00]
[   96.071736] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   96.071763] assign_interrupt_mode Found MSI capability
[   96.071785] Allocate Port Service[0000:00:1c.0:pcie00]
[   96.071828] Allocate Port Service[0000:00:1c.0:pcie02]
[   96.071904] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   96.071932] assign_interrupt_mode Found MSI capability
[   96.071954] Allocate Port Service[0000:00:1c.4:pcie00]
[   96.071997] Allocate Port Service[0000:00:1c.4:pcie02]
[   96.072072] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   96.072099] assign_interrupt_mode Found MSI capability
[   96.072122] Allocate Port Service[0000:00:1c.5:pcie00]
[   96.072163] Allocate Port Service[0000:00:1c.5:pcie02]
[   96.100442] Real Time Clock Driver v1.12ac
[   96.100586] hpet_resources: 0xfed00000 is busy
[   96.100617] Linux agpgart interface v0.102
[   96.100619] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   96.101828] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   96.101888] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   96.101986] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   96.101988] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   96.102508] serio: i8042 KBD port at 0x60,0x64 irq 1
[   96.166504] mice: PS/2 mouse device common for all mice
[   96.166571] cpuidle: using governor ladder
[   96.166572] cpuidle: using governor menu
[   96.166677] NET: Registered protocol family 1
[   96.166762] registered taskstats version 1
[   96.166822]   Magic number: 5:190:232
[   96.166827]   hash matches device ttyv2
[   96.166842] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   96.166844] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   96.167132] Freeing unused kernel memory: 328k freed
[   96.168560] Write protecting the kernel read-only data: 1044k
[   96.194079] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   96.258339] fuse init (API version 7.9)
[   96.267668] ACPI: SSDT DBF7E0D0, 0235 (r1 DpgPmm  P001Ist       11 INTL 20060113)
[   96.267829] ACPI: SSDT DBF7E9D0, 04B2 (r1  PmRef  P001Cst     3001 INTL 20060113)
[   96.268357] ACPI: SSDT DBF7E310, 0235 (r1 DpgPmm  P002Ist       12 INTL 20060113)
[   96.268509] ACPI: SSDT DBF7EE90, 0085 (r1  PmRef  P002Cst     3000 INTL 20060113)
[   96.269070] ACPI: SSDT DBF7E550, 0235 (r1 DpgPmm  P003Ist       12 INTL 20060113)
[   96.269222] ACPI: SSDT DBF7EF20, 0085 (r1  PmRef  P003Cst     3000 INTL 20060113)
[   96.269776] ACPI: SSDT DBF7E790, 0235 (r1 DpgPmm  P004Ist       12 INTL 20060113)
[   96.269930] ACPI: SSDT DBF7EFB0, 0085 (r1  PmRef  P004Cst     3000 INTL 20060113)
[   96.363996] usbcore: registered new interface driver usbfs
[   96.364010] usbcore: registered new interface driver hub
[   96.367846] usbcore: registered new device driver usb
[   96.382392] SCSI subsystem initialized
[   96.382950] USB Universal Host Controller Interface driver v3.0
[   96.382975] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   96.382982] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   96.382985] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   96.383112] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   96.383134] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[   96.383211] usb usb1: configuration #1 chosen from 1 choice
[   96.383225] hub 1-0:1.0: USB hub found
[   96.383228] hub 1-0:1.0: 2 ports detected
[   96.389181] libata version 3.00 loaded.
[   96.400565] megasas: 00.00.03.10-rc5 Thu May 17 10:09:32 PDT 2007
[   96.496042] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   96.496050] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   96.496052] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   96.496066] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   96.496087] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[   96.496149] usb usb2: configuration #1 chosen from 1 choice
[   96.496163] hub 2-0:1.0: USB hub found
[   96.496167] hub 2-0:1.0: 2 ports detected
[   96.615865] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   96.615871] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   96.615873] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   96.615886] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   96.615906] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[   96.615964] usb usb3: configuration #1 chosen from 1 choice
[   96.615977] hub 3-0:1.0: USB hub found
[   96.615980] hub 3-0:1.0: 2 ports detected
[   96.725781] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   96.727223] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   96.727227] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   96.727269] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[   96.731174] ehci_hcd 0000:00:1a.7: debug port 1
[   96.731178] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   96.731182] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[   96.749537] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   96.749602] usb usb4: configuration #1 chosen from 1 choice
[   96.749616] hub 4-0:1.0: USB hub found
[   96.749620] hub 4-0:1.0: 6 ports detected
[   96.855574] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   96.856976] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   96.856980] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   96.857024] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   96.860925] ehci_hcd 0000:00:1d.7: debug port 1
[   96.860929] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   96.860936] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[   96.879228] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   96.879303] usb usb5: configuration #1 chosen from 1 choice
[   96.879321] hub 5-0:1.0: USB hub found
[   96.879325] hub 5-0:1.0: 6 ports detected
[   96.985464] ACPI: PCI Interrupt 0000:07:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   96.986644] skge 1.13 addr 0xfebec000 irq 18 chip Yukon-Lite rev 9
[   96.986823] skge eth0: addr 00:23:54:27:4d:fb
[   96.986865] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   96.986888] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   96.986897] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   96.986924] megasas: 0x1028:0x0015:0x1028:0x1f03: bus 3:slot 14:func 0
[   96.986942] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
[   96.987647] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   96.987656] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   96.987658] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   96.987690] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[   96.987712] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[   96.987782] usb usb6: configuration #1 chosen from 1 choice
[   96.987796] hub 6-0:1.0: USB hub found
[   96.987800] hub 6-0:1.0: 2 ports detected
[   96.988174] megasas: FW now in Ready state
[   97.057796] scsi0 : LSI Logic SAS based MegaRAID driver
[   97.059792] scsi 0:0:0:0: Direct-Access     ATA      WL500GSA1672     1C02 PQ: 0 ANSI: 5
[   97.061723] scsi 0:0:1:0: Direct-Access     ATA      WL500GSA1672     1C02 PQ: 0 ANSI: 5
[   97.063755] scsi 0:0:3:0: Direct-Access     ATA      WL500GSA1672     1C02 PQ: 0 ANSI: 5
[   97.065677] scsi 0:0:4:0: Direct-Access     ATA      WL500GSA1672     1C02 PQ: 0 ANSI: 5
[   97.067626] scsi 0:0:5:0: Direct-Access     ATA      WL500GSA1672     4C05 PQ: 0 ANSI: 5
[   97.082051] scsi 0:0:6:0: Direct-Access     ATA      HDS725050KLA360  AB5A PQ: 0 ANSI: 5
[   97.097471] scsi 0:2:0:0: Direct-Access     DELL     PERC 5/i         1.12 PQ: 0 ANSI: 5
[   97.097623] scsi 0:2:1:0: Direct-Access     DELL     PERC 5/i         1.12 PQ: 0 ANSI: 5
[   97.105269] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   97.105275] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   97.105278] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   97.105298] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[   97.105321] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[   97.105408] usb usb7: configuration #1 chosen from 1 choice
[   97.105422] hub 7-0:1.0: USB hub found
[   97.105426] hub 7-0:1.0: 2 ports detected
[   97.109240] Driver 'sd' needs updating - please use bus_type methods
[   97.109342] sd 0:2:0:0: [sda] 409600000 512-byte hardware sectors (209715 MB)
[   97.109392] sd 0:2:0:0: [sda] Write Protect is off
[   97.109393] sd 0:2:0:0: [sda] Mode Sense: 1f 00 00 08
[   97.109468] sd 0:2:0:0: [sda] Write cache: enabled, read cache: disabled, doesn't support DPO or FUA
[   97.109552] sd 0:2:0:0: [sda] 409600000 512-byte hardware sectors (209715 MB)
[   97.109591] sd 0:2:0:0: [sda] Write Protect is off
[   97.109592] sd 0:2:0:0: [sda] Mode Sense: 1f 00 00 08
[   97.109677] sd 0:2:0:0: [sda] Write cache: enabled, read cache: disabled, doesn't support DPO or FUA
[   97.109680]  sda: sda1 sda2 < sda5 >
[   97.127937] sd 0:2:0:0: [sda] Attached SCSI disk
[   97.128022] sd 0:2:1:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[   97.128059] sd 0:2:1:0: [sdb] 4468899840 512-byte hardware sectors (2288077 MB)
[   97.128114] sd 0:2:1:0: [sdb] Write Protect is off
[   97.128116] sd 0:2:1:0: [sdb] Mode Sense: 1f 00 00 08
[   97.128194] sd 0:2:1:0: [sdb] Write cache: enabled, read cache: disabled, doesn't support DPO or FUA
[   97.128289] sd 0:2:1:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[   97.128331] sd 0:2:1:0: [sdb] 4468899840 512-byte hardware sectors (2288077 MB)
[   97.128371] sd 0:2:1:0: [sdb] Write Protect is off
[   97.128373] sd 0:2:1:0: [sdb] Mode Sense: 1f 00 00 08
[   97.128447] sd 0:2:1:0: [sdb] Write cache: enabled, read cache: disabled, doesn't support DPO or FUA
[   97.128450]  sdb: sdb1
[   97.154298] sd 0:2:1:0: [sdb] Attached SCSI disk
[   97.156355] sd 0:2:0:0: Attached scsi generic sg0 type 0
[   97.156366] sd 0:2:1:0: Attached scsi generic sg1 type 0
[   97.215139] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   97.215146] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   97.215148] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   97.215164] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[   97.215185] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[   97.215250] usb usb8: configuration #1 chosen from 1 choice
[   97.215263] hub 8-0:1.0: USB hub found
[   97.215267] hub 8-0:1.0: 2 ports detected
[   97.327696] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   97.327720] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   97.327756] scsi1 : pata_marvell
[   97.327782] scsi2 : pata_marvell
[   97.327799] ata1: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[   97.327800] ata2: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[   97.328994] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00
[   97.684860] ata1.01: ATAPI: TOSHIBA CD-ROM XM-7002B, 1005, max UDMA/33
[   97.884607] ata1.01: configured for UDMA/33
[   97.885802] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00
[   98.071115] scsi 1:0:1:0: CD-ROM            TOSHIBA  CD-ROM XM-7002B  1005 PQ: 0 ANSI: 5
[   98.071179] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   98.075098] Driver 'sr' needs updating - please use bus_type methods
[   98.082789] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   98.082791] Uniform CD-ROM driver Revision: 3.20
[   98.082820] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   98.139455] Attempting manual resume
[   98.139457] swsusp: Resume From Partition 8:5
[   98.139458] PM: Checking swsusp image.
[   98.139533] PM: Resume from disk failed.
[   98.145543] EXT3-fs: INFO: recovery required on readonly filesystem.
[   98.145544] EXT3-fs: write access will be enabled during recovery.
[   98.296809] kjournald starting.  Commit interval 5 seconds
[   98.296815] EXT3-fs: sda1: orphan cleanup on readonly fs
[   98.296820] ext3_orphan_cleanup: deleting unreferenced inode 9756685
[   98.297324] ext3_orphan_cleanup: deleting unreferenced inode 9756688
[   98.297329] ext3_orphan_cleanup: deleting unreferenced inode 9609222
[   98.297334] ext3_orphan_cleanup: deleting unreferenced inode 9609221
[   98.297337] ext3_orphan_cleanup: deleting unreferenced inode 9609220
[   98.297340] ext3_orphan_cleanup: deleting unreferenced inode 9609219
[   98.297343] ext3_orphan_cleanup: deleting unreferenced inode 9609218
[   98.297346] EXT3-fs: sda1: 7 orphan inodes deleted
[   98.297347] EXT3-fs: recovery complete.
[   98.297984] EXT3-fs: mounted filesystem with ordered data mode.
[  100.038558] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  100.052872] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  100.139410] input: Power Button (FF) as /devices/virtual/input/input2
[  100.165871] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  100.165885] PCI: Setting latency timer of device 0000:04:00.0 to 64
[  100.167098] sky2 0000:04:00.0: v1.20 addr 0xfe9fc000 irq 17 Yukon-EC Ultra (0xb4) rev 3
[  100.167479] sky2 eth1: addr 00:23:54:27:46:7f
[  100.184633] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  100.202527] ACPI: Power Button (FF) [PWRF]
[  100.202586] input: Power Button (CM) as /devices/virtual/input/input4
[  100.523529] udev: renamed network interface eth1 to eth0
[  100.526317] sky2 eth0: enabling interface
[  100.542096] ACPI: Power Button (CM) [PWRB]
[  100.588763] udev: renamed network interface eth0_rename to eth1
[  100.809832] NET: Registered protocol family 10
[  100.809953] lo: Disabled Privacy Extensions
[  100.810248] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  102.072785] loop: module loaded
[  102.173957] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  102.180367] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  102.265583] lp: driver loaded but no devices found
[  102.510526] Adding 8345728k swap on /dev/sda5.  Priority:-1 extents:1 across:8345728k
[  102.945429] EXT3 FS on sda1, internal journal
[  103.210044] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[  103.210058] ReiserFS: sdb1: using ordered data mode
[  103.219008] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  103.219298] ReiserFS: sdb1: checking transaction log (sdb1)
[  103.231395] ReiserFS: sdb1: replayed 2 transactions in 0 seconds
[  103.266302] ReiserFS: sdb1: Using r5 hash to sort names
[  103.717940] ip_tables: (C) 2000-2006 Netfilter Core Team
[  105.243792] audit(1249668749.699:2): type=1503 operation="capable" name="sys_resource" pid=4447 profile="/usr/sbin/named" namespace="default"
[  107.575522] /dev/vmmon[4724]: Module vmmon: registered with major=10 minor=165
[  107.575535] /dev/vmmon[4724]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[  107.575540] /dev/vmmon[4724]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[  107.575541] /dev/vmmon[4724]: Module vmmon: initialized
[  107.595346] /dev/vmci[4738]: VMCI: Driver initialized.
[  107.595370] /dev/vmci[4738]: Module vmci: registered with major=10 minor=63
[  107.595374] /dev/vmci[4738]: Module vmci: initialized
[  107.603844] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
[  108.860401] /dev/vmnet: open called by PID 4800 (vmnet-bridge)
[  108.860406] /dev/vmnet: hub 0 does not exist, allocating memory.
[  108.860415] /dev/vmnet: port on hub 0 successfully opened
[  108.860423] bridge-eth0: up
[  108.860425] bridge-eth0: attached
[  113.137345] eth0: no IPv6 routers present
[  113.934357] /dev/vmmon[5286]: PTSC: initialized at 2832970000 Hz using TSC
[  113.935270] /dev/vmmon[5286]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  113.935273] /dev/vmmon[5286]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  113.935281] /dev/vmmon[4421]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  113.935283] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  113.935285] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  113.935287] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  113.935288] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  113.935296] /dev/vmmon[4421]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  114.343650] /dev/vmnet: open called by PID 5289 (vmware-vmx)
[  114.343665] device eth0 entered promiscuous mode
[  114.343669] audit(1249668758.822:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  114.343673] bridge-eth0: enabled promiscuous mode
[  114.343675] /dev/vmnet: port on hub 0 successfully opened
[  142.284358] device eth0 left promiscuous mode
[  142.284368] audit(1249668786.802:4): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  142.284374] bridge-eth0: disabled promiscuous mode
[  142.284422] /dev/vmnet: open called by PID 5294 (vmware-vmx)
[  142.284427] device eth0 entered promiscuous mode
[  142.284429] audit(1249668786.802:5): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  142.284436] bridge-eth0: enabled promiscuous mode
[  142.284437] /dev/vmnet: port on hub 0 successfully opened
[  233.586176] /dev/vmmon[5342]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  233.586181] /dev/vmmon[5342]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  233.586188] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  233.586189] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  233.586192] /dev/vmmon[4421]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  233.586194] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  233.586195] /dev/vmmon[4421]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  233.586199] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  239.003296] vmmon: Had to deallocate locked 1538 pages from vm driver ffff8101a5c8f400
[  239.003356] vmmon: Had to deallocate AWE 16 pages from vm driver ffff8101a5c8f400
[  239.595044] /dev/vmmon[5345]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  239.595048] /dev/vmmon[5345]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  239.595056] /dev/vmmon[4421]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  239.595058] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  239.595061] /dev/vmmon[0]: INTELRDMSR(0x8b) = 0x00000a0700000000
[  239.595063] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  239.595064] /dev/vmmon[0]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  239.595071] /dev/vmmon[4421]: INTELRDMSR(0x17) = 0x0810000088c4c81f
[  239.955645] /dev/vmnet: open called by PID 5348 (vmware-vmx)
[  239.955658] /dev/vmnet: port on hub 0 successfully opened
[  282.666909] /dev/vmnet: open called by PID 5349 (vmware-vmx)
[  282.666917] /dev/vmnet: port on hub 0 successfully opened
[  625.010006] do_IRQ: 3.153 No irq handler for vector
[  625.247732] do_IRQ: 3.129 No irq handler for vector
[  625.288874] do_IRQ: 3.129 No irq handler for vector
[  625.337561] do_IRQ: 3.129 No irq handler for vector
[  625.366595] do_IRQ: 3.129 No irq handler for vector
[  625.370751] do_IRQ: 3.129 No irq handler for vector
[  625.372117] do_IRQ: 3.129 No irq handler for vector
[  625.373477] do_IRQ: 3.129 No irq handler for vector
[  625.374858] do_IRQ: 3.129 No irq handler for vector
[  625.376285] do_IRQ: 3.129 No irq handler for vector
[  630.001917] printk: 241 messages suppressed.
[  630.001920] do_IRQ: 3.129 No irq handler for vector
[  635.762075] printk: 367 messages suppressed.
[  635.762077] do_IRQ: 3.153 No irq handler for vector
[  636.514457] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  636.514512] CPU 3:
[  636.514513] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  636.514543] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  636.514550] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  636.514556] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  636.514557] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  636.514563] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  636.514564] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  636.514566] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  636.514567] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  636.514568] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  636.514574] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  636.514575] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  636.514576] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  636.514577] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  636.514579]
[  636.514579] Call Trace:
[  636.514581]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  636.514590]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  636.514598]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  636.514601]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  636.514610]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  636.514613]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  636.514621]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  636.514624]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  636.514626]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  636.514633]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  636.514636]  [<ffffffff80472589>] error_exit+0x0/0x51
[  636.514643]
[  640.745026] printk: 12 messages suppressed.
[  640.745028] do_IRQ: 3.153 No irq handler for vector
[  644.982329] printk: 253 messages suppressed.
[  644.982337] do_IRQ: 3.129 No irq handler for vector
[  648.309490] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  648.309545] CPU 3:
[  648.309546] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  648.309571] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  648.309572] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  648.309582] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  648.309583] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  648.309584] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  648.309586] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  648.309587] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  648.309588] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  648.309590] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  648.309592] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  648.309593] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  648.309594] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  648.309596] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  648.309597]
[  648.309597] Call Trace:
[  648.309599]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  648.309607]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  648.309611]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  648.309617]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  648.309621]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  648.309625]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  648.309627]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  648.309634]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  648.309636]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  648.309638]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  648.309644]  [<ffffffff80472589>] error_exit+0x0/0x51
[  648.309647]
[  650.977072] printk: 216 messages suppressed.
[  650.977074] do_IRQ: 3.153 No irq handler for vector
[  654.972127] printk: 4 messages suppressed.
[  654.972129] do_IRQ: 3.153 No irq handler for vector
[  660.104629] printk: 9 messages suppressed.
[  660.104631] do_IRQ: 3.153 No irq handler for vector
[  660.114509] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  660.114564] CPU 3:
[  660.114565] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  660.114592] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  660.114593] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  660.114600] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  660.114602] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  660.114603] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  660.114604] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  660.114605] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  660.114610] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  660.114611] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  660.114613] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  660.114614] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  660.114615] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  660.114620] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  660.114621]
[  660.114622] Call Trace:
[  660.114624]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  660.114627]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  660.114635]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  660.114637]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  660.114645]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  660.114648]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  660.114651]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  660.114658]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  660.114660]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  660.114662]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  660.114668]  [<ffffffff80472589>] error_exit+0x0/0x51
[  660.114672]
[  664.959627] printk: 24 messages suppressed.
[  664.959630] do_IRQ: 3.153 No irq handler for vector
[  671.015075] printk: 45 messages suppressed.
[  671.015078] do_IRQ: 3.153 No irq handler for vector
[  671.909542] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  671.909598] CPU 3:
[  671.909603] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  671.909631] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  671.909633] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  671.909638] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  671.909640] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  671.909642] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  671.909644] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  671.909646] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  671.909648] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  671.909649] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  671.909651] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  671.909652] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  671.909654] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  671.909657] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  671.909659]
[  671.909659] Call Trace:
[  671.909661]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  671.909666]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  671.909669]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  671.909672]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  671.909677]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  671.909681]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  671.909684]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  671.909688]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  671.909690]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  671.909692]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  671.909694]  [<ffffffff80472589>] error_exit+0x0/0x51
[  671.909698]
[  675.062094] printk: 12 messages suppressed.
[  675.062096] do_IRQ: 3.153 No irq handler for vector
[  680.314251] printk: 5 messages suppressed.
[  680.314253] do_IRQ: 3.129 No irq handler for vector
[  683.704575] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  683.704630] CPU 3:
[  683.704636] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  683.704665] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  683.704668] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  683.704672] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  683.704673] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  683.704675] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  683.704677] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  683.704679] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  683.704681] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  683.704683] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  683.704685] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  683.704687] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  683.704689] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  683.704691] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  683.704692]
[  683.704693] Call Trace:
[  683.704695]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  683.704700]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  683.704703]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  683.704706]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  683.704710]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  683.704714]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  683.704717]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  683.704720]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  683.704722]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  683.704725]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  683.704729]  [<ffffffff80472589>] error_exit+0x0/0x51
[  683.704732]
[  684.934760] printk: 10 messages suppressed.
[  684.934763] do_IRQ: 3.153 No irq handler for vector
[  690.907974] printk: 10 messages suppressed.
[  690.907977] do_IRQ: 3.153 No irq handler for vector
[  694.923936] printk: 5 messages suppressed.
[  694.923938] do_IRQ: 3.153 No irq handler for vector
[  695.499607] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  695.499636] CPU 3:
[  695.499642] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  695.499664] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  695.499666] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  695.499670] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  695.499672] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  695.499675] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  695.499677] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  695.499679] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  695.499681] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  695.499683] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  695.499685] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  695.499687] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  695.499688] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  695.499689] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  695.499691]
[  695.499692] Call Trace:
[  695.499694]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  695.499698]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  695.499700]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  695.499704]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  695.499708]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  695.499712]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  695.499716]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  695.499719]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  695.499721]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  695.499725]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  695.499728]  [<ffffffff80472589>] error_exit+0x0/0x51
[  695.499732]
[  700.495320] printk: 36 messages suppressed.
[  700.495322] do_IRQ: 3.153 No irq handler for vector
[  705.489942] printk: 13 messages suppressed.
[  705.489945] do_IRQ: 3.153 No irq handler for vector
[  707.294640] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  707.294669] CPU 3:
[  707.294675] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  707.294700] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  707.294701] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  707.294708] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  707.294710] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  707.294712] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  707.294714] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  707.294716] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  707.294718] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  707.294720] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  707.294723] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  707.294724] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  707.294725] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  707.294727] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  707.294729]
[  707.294729] Call Trace:
[  707.294732]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  707.294736]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  707.294740]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  707.294742]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  707.294747]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  707.294751]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  707.294754]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  707.294758]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  707.294760]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  707.294763]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  707.294766]  [<ffffffff80472589>] error_exit+0x0/0x51
[  707.294770]
[  710.049688] printk: 12 messages suppressed.
[  710.049690] do_IRQ: 3.153 No irq handler for vector
[  715.325811] printk: 6 messages suppressed.
[  715.325813] do_IRQ: 3.153 No irq handler for vector
[  719.089673] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  719.089701] CPU 3:
[  719.089707] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  719.089732] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  719.089735] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  719.089740] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  719.089742] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  719.089744] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  719.089746] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  719.089749] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  719.089751] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  719.089753] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  719.089755] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  719.089757] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  719.089759] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  719.089761] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  719.089763]
[  719.089763] Call Trace:
[  719.089765]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  719.089769]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  719.089772]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  719.089775]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  719.089779]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  719.089782]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  719.089786]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  719.089789]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  719.089792]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  719.089794]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  719.089798]  [<ffffffff80472589>] error_exit+0x0/0x51
[  719.089802]
[  720.469963] printk: 22 messages suppressed.
[  720.469966] do_IRQ: 3.153 No irq handler for vector
[  725.466531] printk: 15 messages suppressed.
[  725.466533] do_IRQ: 3.153 No irq handler for vector
[  730.264298] printk: 10 messages suppressed.
[  730.264305] do_IRQ: 3.129 No irq handler for vector
[  730.884707] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  730.884737] CPU 3:
[  730.884737] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  730.884755] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  730.884756] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  730.884761] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  730.884762] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  730.884763] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  730.884764] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  730.884766] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  730.884767] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  730.884769] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  730.884770] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  730.884771] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  730.884773] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  730.884774] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  730.884775]
[  730.884775] Call Trace:
[  730.884777]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  730.884781]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  730.884784]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  730.884787]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  730.884791]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  730.884794]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  730.884797]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  730.884800]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  730.884801]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  730.884804]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  730.884806]  [<ffffffff80472589>] error_exit+0x0/0x51
[  730.884810]
[  735.646476] printk: 36 messages suppressed.
[  735.646478] do_IRQ: 3.153 No irq handler for vector
[  740.865530] printk: 8 messages suppressed.
[  740.865533] do_IRQ: 3.153 No irq handler for vector
[  742.679739] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  742.679768] CPU 3:
[  742.679774] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  742.679803] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  742.679806] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  742.679812] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  742.679814] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  742.679816] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  742.679818] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  742.679819] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  742.679821] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  742.679824] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  742.679826] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  742.679828] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  742.679830] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  742.679832] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  742.679834]
[  742.679834] Call Trace:
[  742.679837]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  742.679841]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  742.679844]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  742.679847]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  742.679852]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  742.679856]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  742.679858]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  742.679862]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  742.679865]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  742.679868]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  742.679871]  [<ffffffff80472589>] error_exit+0x0/0x51
[  742.679875]
[  746.039841] printk: 14 messages suppressed.
[  746.039844] do_IRQ: 3.153 No irq handler for vector
[  750.333357] printk: 9 messages suppressed.
[  750.333365] do_IRQ: 3.129 No irq handler for vector
[  754.484759] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  754.484787] CPU 3:
[  754.484793] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  754.484819] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  754.484821] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  754.484826] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  754.484828] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  754.484830] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  754.484832] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  754.484834] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  754.484836] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  754.484838] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  754.484841] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  754.484843] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  754.484845] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  754.484847] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  754.484849]
[  754.484849] Call Trace:
[  754.484851]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  754.484855]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  754.484857]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  754.484860]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  754.484864]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  754.484867]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  754.484870]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  754.484873]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  754.484875]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  754.484877]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  754.484880]  [<ffffffff80472589>] error_exit+0x0/0x51
[  754.484884]
[  754.848077] printk: 12 messages suppressed.
[  754.848080] do_IRQ: 3.153 No irq handler for vector
[  760.035692] printk: 8 messages suppressed.
[  760.035695] do_IRQ: 3.153 No irq handler for vector
[  765.138201] printk: 22 messages suppressed.
[  765.138203] do_IRQ: 3.153 No irq handler for vector
[  766.279791] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  766.279820] CPU 3:
[  766.279825] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  766.279853] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  766.279855] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  766.279859] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  766.279861] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  766.279863] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  766.279865] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  766.279867] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  766.279869] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  766.279871] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  766.279873] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  766.279876] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  766.279878] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  766.279880] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  766.279882]
[  766.279882] Call Trace:
[  766.279884]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  766.279889]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  766.279892]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  766.279896]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  766.279899]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  766.279902]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  766.279905]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  766.279908]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  766.279911]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  766.279914]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  766.279918]  [<ffffffff80472589>] error_exit+0x0/0x51
[  766.279922]
[  769.824390] printk: 12 messages suppressed.
[  769.824398] do_IRQ: 3.129 No irq handler for vector
[  774.822609] printk: 12 messages suppressed.
[  774.822611] do_IRQ: 3.153 No irq handler for vector
[  778.074824] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  778.074853] CPU 3:
[  778.074858] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  778.074882] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  778.074884] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  778.074889] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  778.074891] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  778.074893] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  778.074895] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  778.074897] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  778.074899] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  778.074901] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  778.074903] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  778.074904] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  778.074906] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  778.074907] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  778.074909]
[  778.074910] Call Trace:
[  778.074912]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  778.074916]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  778.074918]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  778.074921]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  778.074926]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  778.074929]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  778.074932]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  778.074935]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  778.074938]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  778.074940]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  778.074944]  [<ffffffff80472589>] error_exit+0x0/0x51
[  778.074948]
[  780.096632] printk: 17 messages suppressed.
[  780.096634] do_IRQ: 3.153 No irq handler for vector
[  785.145076] printk: 7 messages suppressed.
[  785.145078] do_IRQ: 3.129 No irq handler for vector
[  789.869857] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  789.869886] CPU 3:
[  789.869887] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  789.869916] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  789.869919] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  789.869923] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  789.869925] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  789.869927] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  789.869929] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  789.869931] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  789.869933] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  789.869936] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  789.869938] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  789.869940] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  789.869942] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  789.869945] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  789.869946]
[  789.869947] Call Trace:
[  789.869948]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  789.869952]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  789.869954]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  789.869958]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  789.869962]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  789.869966]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  789.869968]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  789.869971]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  789.869974]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  789.869977]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  789.869980]  [<ffffffff80472589>] error_exit+0x0/0x51
[  789.869984]
[  789.973820] printk: 17 messages suppressed.
[  789.973823] do_IRQ: 3.153 No irq handler for vector
[  795.378070] printk: 14 messages suppressed.
[  795.378072] do_IRQ: 3.153 No irq handler for vector
[  800.790262] printk: 8 messages suppressed.
[  800.790264] do_IRQ: 3.153 No irq handler for vector
[  801.664889] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  801.664918] CPU 3:
[  801.664923] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  801.664948] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  801.664951] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  801.664955] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  801.664958] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  801.664960] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  801.664961] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  801.664963] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  801.664965] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  801.664968] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  801.664970] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  801.664972] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  801.664974] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  801.664976] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  801.664978]
[  801.664978] Call Trace:
[  801.664980]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  801.664984]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  801.664987]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  801.664991]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  801.664994]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  801.664998]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  801.665001]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  801.665004]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  801.665007]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  801.665010]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  801.665013]  [<ffffffff80472589>] error_exit+0x0/0x51
[  801.665017]
[  805.119781] printk: 6 messages suppressed.
[  805.119789] do_IRQ: 3.129 No irq handler for vector
[  810.095114] printk: 21 messages suppressed.
[  810.095116] do_IRQ: 3.153 No irq handler for vector
[  813.459922] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  813.459951] CPU 3:
[  813.459957] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  813.459985] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  813.459987] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  813.459992] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  813.459994] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  813.459996] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  813.459998] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  813.460000] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  813.460003] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  813.460005] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  813.460007] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  813.460009] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  813.460011] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  813.460013] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  813.460015]
[  813.460015] Call Trace:
[  813.460017]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  813.460020]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  813.460024]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  813.460028]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  813.460032]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  813.460035]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  813.460039]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  813.460042]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  813.460044]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  813.460047]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  813.460051]  [<ffffffff80472589>] error_exit+0x0/0x51
[  813.460055]
[  815.369661] printk: 10 messages suppressed.
[  815.369663] do_IRQ: 3.153 No irq handler for vector
[  820.607651] printk: 17 messages suppressed.
[  820.607653] do_IRQ: 3.153 No irq handler for vector
[  825.254955] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  825.254984] CPU 3:
[  825.254989] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  825.255017] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  825.255019] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  825.255024] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  825.255026] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  825.255028] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  825.255030] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  825.255032] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  825.255035] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  825.255037] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  825.255038] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  825.255039] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  825.255042] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  825.255044] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  825.255045]
[  825.255045] Call Trace:
[  825.255047]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  825.255052]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  825.255055]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  825.255058]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  825.255063]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  825.255066]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  825.255070]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  825.255073]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  825.255076]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  825.255079]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  825.255083]  [<ffffffff80472589>] error_exit+0x0/0x51
[  825.255086]
[  825.348546] printk: 13 messages suppressed.
[  825.348548] do_IRQ: 3.153 No irq handler for vector
[  830.346237] printk: 10 messages suppressed.
[  830.346239] do_IRQ: 3.153 No irq handler for vector
[  835.121809] printk: 6 messages suppressed.
[  835.121811] do_IRQ: 3.129 No irq handler for vector
[  837.049988] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  837.050016] CPU 3:
[  837.050022] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  837.050050] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  837.050052] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  837.050057] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  837.050059] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  837.050061] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  837.050062] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  837.050064] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  837.050067] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  837.050069] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  837.050071] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  837.050072] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  837.050074] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  837.050077] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  837.050078]
[  837.050079] Call Trace:
[  837.050081]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  837.050084]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  837.050087]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  837.050090]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  837.050094]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  837.050098]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  837.050101]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  837.050105]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  837.050107]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  837.050109]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  837.050113]  [<ffffffff80472589>] error_exit+0x0/0x51
[  837.050117]
[  840.115650] printk: 7 messages suppressed.
[  840.115658] do_IRQ: 3.129 No irq handler for vector
[  845.308444] printk: 12 messages suppressed.
[  845.308448] do_IRQ: 3.153 No irq handler for vector
[  848.845021] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  848.845049] CPU 3:
[  848.845055] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  848.845082] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  848.845083] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  848.845088] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  848.845090] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  848.845092] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  848.845094] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  848.845096] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  848.845098] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  848.845101] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  848.845103] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  848.845104] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  848.845107] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  848.845109] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  848.845111]
[  848.845111] Call Trace:
[  848.845113]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  848.845116]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  848.845119]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  848.845122]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  848.845126]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  848.845130]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  848.845133]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  848.845136]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  848.845139]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  848.845142]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  848.845145]  [<ffffffff80472589>] error_exit+0x0/0x51
[  848.845149]
[  850.302152] printk: 4 messages suppressed.
[  850.302155] do_IRQ: 3.129 No irq handler for vector
[  855.295393] printk: 15 messages suppressed.
[  855.295395] do_IRQ: 3.129 No irq handler for vector
[  860.289724] printk: 13 messages suppressed.
[  860.289726] do_IRQ: 3.129 No irq handler for vector
[  860.650040] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  860.650069] CPU 3:
[  860.650075] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  860.650104] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  860.650106] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  860.650111] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  860.650112] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  860.650113] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  860.650115] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  860.650117] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  860.650119] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  860.650122] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  860.650123] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  860.650124] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  860.650126] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  860.650128] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  860.650130]
[  860.650130] Call Trace:
[  860.650133]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  860.650137]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  860.650139]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  860.650143]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  860.650147]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  860.650151]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  860.650154]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  860.650158]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  860.650160]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  860.650163]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  860.650166]  [<ffffffff80472589>] error_exit+0x0/0x51
[  860.650169]
[  865.283500] printk: 15 messages suppressed.
[  865.283508] do_IRQ: 3.129 No irq handler for vector
[  870.276860] printk: 11 messages suppressed.
[  870.276863] do_IRQ: 3.129 No irq handler for vector
[  872.445073] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  872.445102] CPU 3:
[  872.445108] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  872.445131] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  872.445133] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  872.445138] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  872.445139] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  872.445141] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  872.445143] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  872.445145] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  872.445147] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  872.445150] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  872.445152] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  872.445154] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  872.445156] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  872.445158] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  872.445160]
[  872.445160] Call Trace:
[  872.445162]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  872.445166]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  872.445169]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  872.445172]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  872.445176]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  872.445180]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  872.445183]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  872.445186]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  872.445188]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  872.445190]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  872.445194]  [<ffffffff80472589>] error_exit+0x0/0x51
[  872.445198]
[  875.279918] printk: 7 messages suppressed.
[  875.279926] do_IRQ: 3.129 No irq handler for vector
[  880.266910] printk: 15 messages suppressed.
[  880.266912] do_IRQ: 3.153 No irq handler for vector
[  884.240106] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  884.240135] CPU 3:
[  884.240141] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  884.240170] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  884.240172] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  884.240177] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  884.240178] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  884.240180] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  884.240182] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  884.240184] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  884.240186] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  884.240188] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  884.240190] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  884.240192] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  884.240194] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  884.240196] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  884.240198]
[  884.240198] Call Trace:
[  884.240200]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  884.240203]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  884.240206]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  884.240209]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  884.240214]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  884.240218]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  884.240221]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  884.240224]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  884.240227]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  884.240230]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  884.240233]  [<ffffffff80472589>] error_exit+0x0/0x51
[  884.240236]
[  885.258610] printk: 16 messages suppressed.
[  885.258612] do_IRQ: 3.153 No irq handler for vector
[  890.254187] printk: 28 messages suppressed.
[  890.254189] do_IRQ: 3.153 No irq handler for vector
[  895.263926] printk: 8 messages suppressed.
[  895.263929] do_IRQ: 3.129 No irq handler for vector
[  896.035139] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  896.035167] CPU 3:
[  896.035173] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  896.035199] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  896.035202] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  896.035206] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  896.035208] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  896.035210] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  896.035212] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  896.035214] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  896.035215] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  896.035218] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  896.035220] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  896.035222] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  896.035224] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  896.035226] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  896.035227]
[  896.035227] Call Trace:
[  896.035229]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  896.035232]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  896.035236]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  896.035239]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  896.035243]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  896.035247]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  896.035250]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  896.035253]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  896.035256]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  896.035258]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  896.035262]  [<ffffffff80472589>] error_exit+0x0/0x51
[  896.035266]
[  900.243355] printk: 16 messages suppressed.
[  900.243357] do_IRQ: 3.153 No irq handler for vector
[  905.236791] printk: 14 messages suppressed.
[  905.236794] do_IRQ: 3.153 No irq handler for vector
[  907.830172] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  907.830200] CPU 3:
[  907.830206] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  907.830233] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  907.830235] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  907.830239] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  907.830241] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  907.830243] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  907.830245] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  907.830247] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  907.830248] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  907.830250] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  907.830253] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  907.830254] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  907.830256] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  907.830259] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  907.830260]
[  907.830261] Call Trace:
[  907.830262]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  907.830266]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  907.830269]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  907.830272]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  907.830275]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  907.830278]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  907.830282]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  907.830285]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  907.830287]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  907.830290]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  907.830294]  [<ffffffff80472589>] error_exit+0x0/0x51
[  907.830297]
[  910.228696] printk: 11 messages suppressed.
[  910.228699] do_IRQ: 3.153 No irq handler for vector
[  915.220282] printk: 29 messages suppressed.
[  915.220284] do_IRQ: 3.129 No irq handler for vector
[  919.625205] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  919.625233] CPU 3:
[  919.625239] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  919.625266] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  919.625268] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  919.625273] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  919.625275] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  919.625277] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  919.625280] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  919.625281] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  919.625283] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  919.625285] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  919.625287] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  919.625289] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  919.625291] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  919.625294] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  919.625295]
[  919.625296] Call Trace:
[  919.625298]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  919.625302]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  919.625305]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  919.625309]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  919.625313]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  919.625317]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  919.625320]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  919.625324]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  919.625327]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  919.625330]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  919.625334]  [<ffffffff80472589>] error_exit+0x0/0x51
[  919.625337]
[  920.214486] printk: 16 messages suppressed.
[  920.214488] do_IRQ: 3.153 No irq handler for vector
[  925.212842] printk: 10 messages suppressed.
[  925.212845] do_IRQ: 3.153 No irq handler for vector
[  930.206585] printk: 7 messages suppressed.
[  930.206587] do_IRQ: 3.153 No irq handler for vector
[  931.420237] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  931.420266] CPU 3:
[  931.420271] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  931.420298] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  931.420300] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  931.420305] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  931.420307] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  931.420309] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  931.420311] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  931.420313] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  931.420314] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  931.420316] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  931.420317] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  931.420319] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  931.420320] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  931.420322] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  931.420324]
[  931.420324] Call Trace:
[  931.420327]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  931.420331]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  931.420334]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  931.420337]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  931.420341]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  931.420346]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  931.420348]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  931.420352]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  931.420354]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  931.420356]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  931.420360]  [<ffffffff80472589>] error_exit+0x0/0x51
[  931.420364]
[  935.213263] printk: 5 messages suppressed.
[  935.213265] do_IRQ: 3.153 No irq handler for vector
[  940.106039] printk: 6 messages suppressed.
[  940.106041] do_IRQ: 3.129 No irq handler for vector
[  943.215270] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  943.215298] CPU 3:
[  943.215299] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  943.215331] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  943.215333] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  943.215337] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  943.215339] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  943.215341] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  943.215342] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  943.215344] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  943.215346] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  943.215349] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  943.215351] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  943.215353] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  943.215355] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  943.215357] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  943.215358]
[  943.215358] Call Trace:
[  943.215360]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  943.215364]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  943.215368]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  943.215371]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  943.215375]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  943.215379]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  943.215383]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  943.215387]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  943.215388]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  943.215391]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  943.215393]  [<ffffffff80472589>] error_exit+0x0/0x51
[  943.215397]
[  945.109803] printk: 17 messages suppressed.
[  945.109806] do_IRQ: 3.129 No irq handler for vector
[  950.103350] printk: 6 messages suppressed.
[  950.103352] do_IRQ: 3.129 No irq handler for vector
[  955.020290] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  955.020318] CPU 3:
[  955.020319] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  955.020346] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  955.020348] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  955.020353] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  955.020355] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  955.020357] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  955.020359] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  955.020361] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  955.020363] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  955.020365] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  955.020366] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  955.020368] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  955.020370] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  955.020372] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  955.020374]
[  955.020375] Call Trace:
[  955.020377]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  955.020381]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  955.020384]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  955.020387]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  955.020392]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  955.020395]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  955.020397]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  955.020400]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  955.020403]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  955.020406]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  955.020409]  [<ffffffff80472589>] error_exit+0x0/0x51
[  955.020412]
[  955.096994] printk: 6 messages suppressed.
[  955.097002] do_IRQ: 3.129 No irq handler for vector
[  960.163330] printk: 19 messages suppressed.
[  960.163338] do_IRQ: 3.129 No irq handler for vector
[  965.172587] printk: 19 messages suppressed.
[  965.172590] do_IRQ: 3.153 No irq handler for vector
[  966.815323] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  966.815351] CPU 3:
[  966.815357] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  966.815383] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  966.815385] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  966.815388] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  966.815390] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  966.815392] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  966.815394] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  966.815396] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  966.815398] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  966.815400] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  966.815402] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  966.815404] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  966.815407] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  966.815409] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  966.815410]
[  966.815411] Call Trace:
[  966.815413]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  966.815417]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  966.815419]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  966.815422]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  966.815426]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  966.815430]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  966.815433]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  966.815437]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  966.815439]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  966.815442]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  966.815446]  [<ffffffff80472589>] error_exit+0x0/0x51
[  966.815450]
[  970.153033] printk: 10 messages suppressed.
[  970.153035] do_IRQ: 3.153 No irq handler for vector
[  975.146610] printk: 14 messages suppressed.
[  975.146612] do_IRQ: 3.153 No irq handler for vector
[  978.610355] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  978.610384] CPU 3:
[  978.610390] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  978.610414] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  978.610417] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[  978.610421] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  978.610423] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  978.610425] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  978.610427] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  978.610429] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  978.610431] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  978.610433] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  978.610435] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  978.610437] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  978.610439] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  978.610441] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  978.610443]
[  978.610443] Call Trace:
[  978.610445]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  978.610448]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  978.610451]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  978.610455]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  978.610458]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  978.610462]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  978.610465]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  978.610468]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  978.610471]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  978.610473]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  978.610476]  [<ffffffff80472589>] error_exit+0x0/0x51
[  978.610480]
[  980.140606] printk: 8 messages suppressed.
[  980.140608] do_IRQ: 3.153 No irq handler for vector
[  985.134444] printk: 5 messages suppressed.
[  985.134446] do_IRQ: 3.153 No irq handler for vector
[  990.126946] printk: 8 messages suppressed.
[  990.126949] do_IRQ: 3.153 No irq handler for vector
[  990.405388] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[  990.405417] CPU 3:
[  990.405423] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  990.405446] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[  990.405448] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[  990.405453] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[  990.405455] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[  990.405457] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[  990.405459] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[  990.405461] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[  990.405462] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[  990.405464] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[  990.405466] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  990.405468] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[  990.405469] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  990.405471] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  990.405473]
[  990.405473] Call Trace:
[  990.405476]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[  990.405479]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[  990.405482]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[  990.405484]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[  990.405488]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[  990.405492]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[  990.405495]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[  990.405499]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[  990.405502]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[  990.405504]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[  990.405508]  [<ffffffff80472589>] error_exit+0x0/0x51
[  990.405512]
[  995.171425] printk: 10 messages suppressed.
[  995.171427] do_IRQ: 3.153 No irq handler for vector
[ 1000.111972] printk: 7 messages suppressed.
[ 1000.111974] do_IRQ: 3.153 No irq handler for vector
[ 1002.200421] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[ 1002.200449] CPU 3:
[ 1002.200455] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 1002.200481] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[ 1002.200483] RIP: 0010:[<ffffffff8021ea28>]  [<ffffffff8021ea28>] flush_tlb_others+0x88/0xd0
[ 1002.200487] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[ 1002.200488] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[ 1002.200490] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[ 1002.200493] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[ 1002.200495] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[ 1002.200496] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[ 1002.200498] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[ 1002.200500] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 1002.200502] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[ 1002.200504] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1002.200506] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1002.200508]
[ 1002.200508] Call Trace:
[ 1002.200510]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[ 1002.200514]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[ 1002.200517]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[ 1002.200520]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[ 1002.200523]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[ 1002.200528]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[ 1002.200531]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[ 1002.200533]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[ 1002.200535]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[ 1002.200538]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[ 1002.200541]  [<ffffffff80472589>] error_exit+0x0/0x51
[ 1002.200545]
[ 1005.108965] printk: 13 messages suppressed.
[ 1005.108968] do_IRQ: 3.153 No irq handler for vector
[ 1010.057214] printk: 5 messages suppressed.
[ 1010.057216] do_IRQ: 3.129 No irq handler for vector
[ 1013.995454] BUG: soft lockup - CPU#3 stuck for 11s! [vmware-vmx:5289]
[ 1013.995483] CPU 3:
[ 1013.995488] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 evdev pcspkr sky2 button shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom pata_marvell sg sd_mod ata_generic pata_acpi megaraid_sas ehci_hcd libata skge uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 1013.995518] Pid: 5289, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
[ 1013.995520] RIP: 0010:[<ffffffff8021ea2d>]  [<ffffffff8021ea2d>] flush_tlb_others+0x8d/0xd0
[ 1013.995525] RSP: 0000:ffff8101f3557d18  EFLAGS: 00003286
[ 1013.995527] RAX: 00000000000008f3 RBX: ffff810001053500 RCX: ffff810000011000
[ 1013.995529] RDX: 0000000000000003 RSI: 00000000000000f3 RDI: 0000000000000006
[ 1013.995531] RBP: 000000004a7c7096 R08: ffff8101f75945f0 R09: ffff8101ff84cff8
[ 1013.995532] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000100000000
[ 1013.995534] R13: ffff8101f61aa180 R14: ffffffff882a2d3f R15: 0000000000000000
[ 1013.995537] FS:  0000000042358950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
[ 1013.995539] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 1013.995541] CR2: 00007fd197d88000 CR3: 00000001f4d4b000 CR4: 00000000000006e0
[ 1013.995542] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1013.995544] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1013.995546]
[ 1013.995546] Call Trace:
[ 1013.995549]  [<ffffffff8021ea1f>] flush_tlb_others+0x7f/0xd0
[ 1013.995552]  [<ffffffff8021edbc>] flush_tlb_page+0x4c/0xa0
[ 1013.995555]  [<ffffffff8029549c>] do_wp_page+0x38c/0x510
[ 1013.995558]  [<ffffffff80296e83>] handle_mm_fault+0x5a3/0x800
[ 1013.995563]  [<ffffffff8047418b>] do_page_fault+0x1ab/0x840
[ 1013.995567]  [<ffffffff804705a0>] thread_return+0x3a/0x59a
[ 1013.995570]  [<ffffffff80236510>] default_wake_function+0x0/0x10
[ 1013.995574]  [<ffffffff802c30a4>] do_ioctl+0x84/0xa0
[ 1013.995576]  [<ffffffff802c32e0>] vfs_ioctl+0x220/0x2c0
[ 1013.995579]  [<ffffffff802b5c8e>] vfs_read+0x14e/0x190
[ 1013.995583]  [<ffffffff80472589>] error_exit+0x0/0x51
[ 1013.995586]
[ 1015.052281] printk: 5 messages suppressed.
[ 1015.052283] do_IRQ: 3.129 No irq handler for vector


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

VAR/LOG/MESSAGE:

Aug  7 13:36:34 ubuntu kernel: [  186.992007] CPU 2
Aug  7 13:36:34 ubuntu kernel: [  186.992083] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 sky2 button evdev shpchp pci_hotplug pcspkr ext3 jbd mbcache sr_mod cdrom sg sd_mod pata_marvell ata_generic ehci_hcd megaraid_sas skge pata_acpi uhci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Aug  7 13:36:34 ubuntu kernel: [  186.993577] Pid: 5302, comm: vmware-vmx Tainted: GF       2.6.24-24-server #1
Aug  7 13:36:34 ubuntu kernel: [  186.993632] RIP: 0010:[find_vma+0x34/0x70]  [find_vma+0x34/0x70] find_vma+0x34/0x70
Aug  7 13:36:34 ubuntu kernel: [  186.993735] RSP: 0018:ffff8101d7e1d870  EFLAGS: 00010206
Aug  7 13:36:34 ubuntu kernel: [  186.993788] RAX: ffff8101f6c166e0 RBX: 0000000000000001 RCX: ffff8101f6c166e0
Aug  7 13:36:34 ubuntu kernel: [  186.993843] RDX: 00ff8101f757bb30 RSI: 00000000000000b8 RDI: ffff8101f5113040
Aug  7 13:36:34 ubuntu kernel: [  186.993899] RBP: ffff8101f51130a0 R08: 0000000000000001 R09: 0000000000001000
Aug  7 13:36:34 ubuntu kernel: [  186.993955] R10: 0000000000000400 R11: 0000000000000000 R12: 0000000000000001
Aug  7 13:36:34 ubuntu kernel: [  186.994011] R13: 0000000000000002 R14: ffff8101f5113040 R15: ffff8101d7e1d978
Aug  7 13:36:34 ubuntu kernel: [  186.994067] FS:  00000000436c1950(0063) GS:ffff8101f8c01b80(0000) knlGS:0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  186.994138] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug  7 13:36:34 ubuntu kernel: [  186.994191] CR2: 00000000000000b8 CR3: 00000001f6955000 CR4: 00000000000006e0
Aug  7 13:36:34 ubuntu kernel: [  186.994247] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  186.994303] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug  7 13:36:34 ubuntu kernel: [  186.994359] Process vmware-vmx (pid: 5302, threadinfo ffff8101d7e1c000, task ffff8101f4d5c000)
Aug  7 13:36:34 ubuntu kernel: [  186.994431] Stack:  ffffffff80474140 00000000000009c0 0000000000000003 ffff8101f48537d0
Aug  7 13:36:34 ubuntu kernel: [  186.994647]  0000000000000002 00000000000101b8 0000000000000000 ffff8101f4d5c000
Aug  7 13:36:34 ubuntu kernel: [  186.994833]  00000000000000b8 000000000021e68c 0000000000030001 000000040104fc00
Aug  7 13:36:34 ubuntu kernel: [  186.994976] Call Trace:
Aug  7 13:36:34 ubuntu kernel: [  186.995067]  [do_page_fault+0x160/0x840] do_page_fault+0x160/0x840
Aug  7 13:36:34 ubuntu kernel: [  186.995125]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Aug  7 13:36:34 ubuntu kernel: [  186.995180]  [mpage_alloc+0x4/0xa0] mpage_alloc+0x4/0xa0
Aug  7 13:36:34 ubuntu kernel: [  186.995234]  [do_mpage_readpage+0x2d0/0x540] do_mpage_readpage+0x2d0/0x540
Aug  7 13:36:34 ubuntu kernel: [  186.995293]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  186.995351]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  186.995405]  [add_to_page_cache+0xb9/0xd0] add_to_page_cache+0xb9/0xd0
Aug  7 13:36:34 ubuntu kernel: [  186.995463]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  186.995517]  [reiserfs:mpage_readpages+0xbb/0xd8d0] mpage_readpages+0xbb/0x100
Aug  7 13:36:34 ubuntu kernel: [  186.995573]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  186.995628]  [__alloc_pages+0x9d/0x3d0] __alloc_pages+0x9d/0x3d0
Aug  7 13:36:34 ubuntu kernel: [  186.995684]  [__do_page_cache_readahead+0x154/0x210] __do_page_cache_readahead+0x154/0x210
Aug  7 13:36:34 ubuntu kernel: [  186.995741]  [ondemand_readahead+0x117/0x1c0] ondemand_readahead+0x117/0x1c0
Aug  7 13:36:34 ubuntu kernel: [  186.995796]  [do_generic_mapping_read+0x13d/0x3c0] do_generic_mapping_read+0x13d/0x3c0
Aug  7 13:36:34 ubuntu kernel: [  186.995851]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Aug  7 13:36:34 ubuntu kernel: [  186.995906]  [reiserfs:generic_file_aio_read+0xff/0x18d0] generic_file_aio_read+0xff/0x1b0
Aug  7 13:36:34 ubuntu kernel: [  186.995963]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Aug  7 13:36:34 ubuntu kernel: [  186.996018]  [<ffffffff80254510>] autoremove_wake_function+0x0/0x30
Aug  7 13:36:34 ubuntu kernel: [  186.996073]  [group_send_sig_info+0x25/0x90] group_send_sig_info+0x25/0x90
Aug  7 13:36:34 ubuntu kernel: [  186.996128]  [kill_pid_info+0x51/0x90] kill_pid_info+0x51/0x90
Aug  7 13:36:34 ubuntu kernel: [  186.996182]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Aug  7 13:36:34 ubuntu kernel: [  186.996234]  [fget_light+0x5e/0xa0] fget_light+0x5e/0xa0
Aug  7 13:36:34 ubuntu kernel: [  186.996287]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Aug  7 13:36:34 ubuntu kernel: [  186.996341]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug  7 13:36:34 ubuntu kernel: [  186.996395]
Aug  7 13:36:34 ubuntu kernel: [  186.996440]
Aug  7 13:36:34 ubuntu kernel: [  186.996440] Code: 48 3b 72 e0 48 8d 42 d0 72 e4 48 8b 52 08 48 85 d2 75 ed 48
Aug  7 13:36:34 ubuntu kernel: [  186.997243]  RSP <ffff8101d7e1d870>
Aug  7 13:36:34 ubuntu kernel: [  186.997295] ---[ end trace 9bbdba5fbd953b83 ]---
Aug  7 13:36:34 ubuntu kernel: [  186.997474] CPU 2
Aug  7 13:36:34 ubuntu kernel: [  186.997553] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 sky2 button evdev shpchp pci_hotplug pcspkr ext3 jbd mbcache sr_mod cdrom sg sd_mod pata_marvell ata_generic ehci_hcd megaraid_sas skge pata_acpi uhci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Aug  7 13:36:34 ubuntu kernel: [  186.999142] Pid: 5302, comm: vmware-vmx Tainted: GF     D 2.6.24-24-server #1
Aug  7 13:36:34 ubuntu kernel: [  186.999201] RIP: 0010:[find_vma+0x34/0x70]  [find_vma+0x34/0x70] find_vma+0x34/0x70
Aug  7 13:36:34 ubuntu kernel: [  186.999306] RSP: 0018:ffff8101d7e1d4b0  EFLAGS: 00010202
Aug  7 13:36:34 ubuntu kernel: [  186.999360] RAX: ffff8101f6c166e0 RBX: ffff8101d7e1d518 RCX: ffff8101f55bef20
Aug  7 13:36:34 ubuntu kernel: [  186.999418] RDX: 00ff8101f78339d0 RSI: 00000000436c1000 RDI: ffff8101f5113040
Aug  7 13:36:34 ubuntu kernel: [  186.999477] RBP: 00000000436c1000 R08: 0000000000000000 R09: 0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  186.999536] R10: 0000000000000000 R11: ffffffff80372e20 R12: ffff8101f5113040
Aug  7 13:36:34 ubuntu kernel: [  186.999594] R13: ffff8101f51130a0 R14: 0000000000000000 R15: 0000000000000001
Aug  7 13:36:34 ubuntu kernel: [  186.999652] FS:  0000000000000000(0000) GS:ffff8101f8c01b80(0000) knlGS:0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  186.999726] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug  7 13:36:34 ubuntu kernel: [  186.999782] CR2: 00000000000000b8 CR3: 00000001f6955000 CR4: 00000000000006e0
Aug  7 13:36:34 ubuntu kernel: [  186.999840] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  186.999899] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug  7 13:36:34 ubuntu kernel: [  186.999957] Process vmware-vmx (pid: 5302, threadinfo ffff8101d7e1c000, task ffff8101f4d5c000)
Aug  7 13:36:34 ubuntu kernel: [  187.000032] Stack:  ffffffff8029a504 ffff8101d7e1d518 00000000436c1000 ffff8101f5113040
Aug  7 13:36:34 ubuntu kernel: [  187.000260]  ffffffff8025e933 0000000000000006 ffffffff80354251 ffffffff00000001
Aug  7 13:36:34 ubuntu kernel: [  187.000457]  20c49ba5e353f7cf 00000000436c19e0 0000000000000000 0000000000000001
Aug  7 13:36:34 ubuntu kernel: [  187.000608] Call Trace:
Aug  7 13:36:34 ubuntu kernel: [  187.000702]  [find_extend_vma+0x24/0x80] find_extend_vma+0x24/0x80
Aug  7 13:36:34 ubuntu kernel: [  187.000759]  [get_futex_key+0x53/0x160] get_futex_key+0x53/0x160
Aug  7 13:36:34 ubuntu kernel: [  187.000815]  [vsnprintf+0x331/0x6e0] vsnprintf+0x331/0x6e0
Aug  7 13:36:34 ubuntu kernel: [  187.000871]  [futex_wake+0x32/0xf0] futex_wake+0x32/0xf0
Aug  7 13:36:34 ubuntu kernel: [  187.000927]  [vgacon_scroll+0x12a/0x210] vgacon_scroll+0x12a/0x210
Aug  7 13:36:34 ubuntu kernel: [  187.000984]  [do_futex+0xb8/0xbd0] do_futex+0xb8/0xbd0
Aug  7 13:36:34 ubuntu kernel: [  187.001041]  [vt_console_print+0x208/0x2f0] vt_console_print+0x208/0x2f0
Aug  7 13:36:34 ubuntu kernel: [  187.001098]  [vgacon_cursor+0x0/0x1f0] vgacon_cursor+0x0/0x1f0
Aug  7 13:36:34 ubuntu kernel: [  187.001155]  [ext3:vprintk+0x2a5/0x370] vprintk+0x2a5/0x370
Aug  7 13:36:34 ubuntu kernel: [  187.001212]  [sys_futex+0xab/0x140] sys_futex+0xab/0x140
Aug  7 13:36:34 ubuntu kernel: [  187.001268]  [reiserfs:kmem_cache_alloc+0x67/0xa0] kmem_cache_alloc+0x67/0xa0
Aug  7 13:36:34 ubuntu kernel: [  187.001326]  [exit_mm+0x16/0x110] exit_mm+0x16/0x110
Aug  7 13:36:34 ubuntu kernel: [  187.001380]  [do_exit+0x1c0/0x940] do_exit+0x1c0/0x940
Aug  7 13:36:34 ubuntu kernel: [  187.001435]  [oops_end+0x34/0x60] oops_end+0x34/0x60
Aug  7 13:36:34 ubuntu kernel: [  187.001489]  [die+0x52/0x70] die+0x52/0x70
Aug  7 13:36:34 ubuntu kernel: [  187.001542]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Aug  7 13:36:34 ubuntu kernel: [  187.001597]  [find_vma+0x34/0x70] find_vma+0x34/0x70
Aug  7 13:36:34 ubuntu kernel: [  187.001651]  [do_page_fault+0x160/0x840] do_page_fault+0x160/0x840
Aug  7 13:36:34 ubuntu kernel: [  187.001708]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Aug  7 13:36:34 ubuntu kernel: [  187.001763]  [mpage_alloc+0x4/0xa0] mpage_alloc+0x4/0xa0
Aug  7 13:36:34 ubuntu kernel: [  187.001818]  [do_mpage_readpage+0x2d0/0x540] do_mpage_readpage+0x2d0/0x540
Aug  7 13:36:34 ubuntu kernel: [  187.001876]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.001935]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.001990]  [add_to_page_cache+0xb9/0xd0] add_to_page_cache+0xb9/0xd0
Aug  7 13:36:34 ubuntu kernel: [  187.002048]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.002103]  [reiserfs:mpage_readpages+0xbb/0xd8d0] mpage_readpages+0xbb/0x100
Aug  7 13:36:34 ubuntu kernel: [  187.002160]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.002216]  [__alloc_pages+0x9d/0x3d0] __alloc_pages+0x9d/0x3d0
Aug  7 13:36:34 ubuntu kernel: [  187.002272]  [__do_page_cache_readahead+0x154/0x210] __do_page_cache_readahead+0x154/0x210
Aug  7 13:36:34 ubuntu kernel: [  187.002330]  [ondemand_readahead+0x117/0x1c0] ondemand_readahead+0x117/0x1c0
Aug  7 13:36:34 ubuntu kernel: [  187.002385]  [do_generic_mapping_read+0x13d/0x3c0] do_generic_mapping_read+0x13d/0x3c0
Aug  7 13:36:34 ubuntu kernel: [  187.002442]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Aug  7 13:36:34 ubuntu kernel: [  187.002498]  [reiserfs:generic_file_aio_read+0xff/0x18d0] generic_file_aio_read+0xff/0x1b0
Aug  7 13:36:34 ubuntu kernel: [  187.002554]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.002610]  [<ffffffff80254510>] autoremove_wake_function+0x0/0x30
Aug  7 13:36:34 ubuntu kernel: [  187.002665]  [group_send_sig_info+0x25/0x90] group_send_sig_info+0x25/0x90
Aug  7 13:36:34 ubuntu kernel: [  187.002720]  [kill_pid_info+0x51/0x90] kill_pid_info+0x51/0x90
Aug  7 13:36:34 ubuntu kernel: [  187.002776]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Aug  7 13:36:34 ubuntu kernel: [  187.002829]  [fget_light+0x5e/0xa0] fget_light+0x5e/0xa0
Aug  7 13:36:34 ubuntu kernel: [  187.002882]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Aug  7 13:36:34 ubuntu kernel: [  187.002936]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug  7 13:36:34 ubuntu kernel: [  187.002991]
Aug  7 13:36:34 ubuntu kernel: [  187.003037]
Aug  7 13:36:34 ubuntu kernel: [  187.003037] Code: 48 3b 72 e0 48 8d 42 d0 72 e4 48 8b 52 08 48 85 d2 75 ed 48
Aug  7 13:36:34 ubuntu kernel: [  187.003855]  RSP <ffff8101d7e1d4b0>
Aug  7 13:36:34 ubuntu kernel: [  187.003909] ---[ end trace 9bbdba5fbd953b83 ]---
Aug  7 13:36:34 ubuntu kernel: [  187.010313] CPU 3
Aug  7 13:36:34 ubuntu kernel: [  187.010388] Modules linked in: vmnet vsock(F) vmci vmmon iptable_filter ip_tables x_tables reiserfs parport_pc lp parport loop ipv6 sky2 button evdev shpchp pci_hotplug pcspkr ext3 jbd mbcache sr_mod cdrom sg sd_mod pata_marvell ata_generic ehci_hcd megaraid_sas skge pata_acpi uhci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Aug  7 13:36:34 ubuntu kernel: [  187.011878] Pid: 5307, comm: vmware-vmx Tainted: GF     D 2.6.24-24-server #1
Aug  7 13:36:34 ubuntu kernel: [  187.011934] RIP: 0010:[find_vma+0x34/0x70]  [find_vma+0x34/0x70] find_vma+0x34/0x70
Aug  7 13:36:34 ubuntu kernel: [  187.012034] RSP: 0018:ffff8101b41bd870  EFLAGS: 00010206
Aug  7 13:36:34 ubuntu kernel: [  187.012087] RAX: ffff8101f6c166e0 RBX: 0000000000000001 RCX: ffff8101f6c166e0
Aug  7 13:36:34 ubuntu kernel: [  187.012143] RDX: 00ff8101f757bb30 RSI: 00000000000000b8 RDI: ffff8101f5113040
Aug  7 13:36:34 ubuntu kernel: [  187.012199] RBP: ffff8101f51130a0 R08: 0000000000000001 R09: 0000000000001000
Aug  7 13:36:34 ubuntu kernel: [  187.012254] R10: 0000000000000400 R11: 0000000000000020 R12: 0000000000000001
Aug  7 13:36:34 ubuntu kernel: [  187.012310] R13: 0000000000000002 R14: ffff8101f5113040 R15: ffff8101b41bd978
Aug  7 13:36:34 ubuntu kernel: [  187.012366] FS:  0000000045ec6950(0063) GS:ffff8101f8c01f00(0000) knlGS:0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  187.012438] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug  7 13:36:34 ubuntu kernel: [  187.012491] CR2: 00000000000000b8 CR3: 00000001f6955000 CR4: 00000000000006e0
Aug  7 13:36:34 ubuntu kernel: [  187.012547] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug  7 13:36:34 ubuntu kernel: [  187.012602] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug  7 13:36:34 ubuntu kernel: [  187.012658] Process vmware-vmx (pid: 5307, threadinfo ffff8101b41bc000, task ffff8101f79c17d0)
Aug  7 13:36:34 ubuntu kernel: [  187.012730] Stack:  ffffffff80474140 ffff8101f754b7d0 0000000000000003 0000000000000001
Aug  7 13:36:34 ubuntu kernel: [  187.012946]  0000000000000002 00000000000101b8 0000000000000000 ffff8101f79c17d0
Aug  7 13:36:34 ubuntu kernel: [  187.013132]  00000000000000b8 000000000021e69b 0000000000030001 0000000401039c00
Aug  7 13:36:34 ubuntu kernel: [  187.013275] Call Trace:
Aug  7 13:36:34 ubuntu kernel: [  187.013366]  [do_page_fault+0x160/0x840] do_page_fault+0x160/0x840
Aug  7 13:36:34 ubuntu kernel: [  187.013423]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Aug  7 13:36:34 ubuntu kernel: [  187.013477]  [mpage_alloc+0x4/0xa0] mpage_alloc+0x4/0xa0
Aug  7 13:36:34 ubuntu kernel: [  187.013531]  [do_mpage_readpage+0x2d0/0x540] do_mpage_readpage+0x2d0/0x540
Aug  7 13:36:34 ubuntu kernel: [  187.013589]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.013647]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.013701]  [add_to_page_cache+0xb9/0xd0] add_to_page_cache+0xb9/0xd0
Aug  7 13:36:34 ubuntu kernel: [  187.013758]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.013813]  [reiserfs:mpage_readpages+0xbb/0xd8d0] mpage_readpages+0xbb/0x100
Aug  7 13:36:34 ubuntu kernel: [  187.013869]  [ext3:ext3_get_block+0x0/0x120] :ext3:ext3_get_block+0x0/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.013924]  [__alloc_pages+0x9d/0x3d0] __alloc_pages+0x9d/0x3d0
Aug  7 13:36:34 ubuntu kernel: [  187.013979]  [__do_page_cache_readahead+0x154/0x210] __do_page_cache_readahead+0x154/0x210
Aug  7 13:36:34 ubuntu kernel: [  187.014036]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Aug  7 13:36:34 ubuntu kernel: [  187.014090]  [do_generic_mapping_read+0x21b/0x3c0] do_generic_mapping_read+0x21b/0x3c0
Aug  7 13:36:34 ubuntu kernel: [  187.014146]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Aug  7 13:36:34 ubuntu kernel: [  187.014201]  [reiserfs:generic_file_aio_read+0xff/0x18d0] generic_file_aio_read+0xff/0x1b0
Aug  7 13:36:34 ubuntu kernel: [  187.014257]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Aug  7 13:36:34 ubuntu kernel: [  187.014311]  [__up_read+0x21/0xb0] __up_read+0x21/0xb0
Aug  7 13:36:34 ubuntu kernel: [  187.014364]  [<ffffffff80254510>] autoremove_wake_function+0x0/0x30
Aug  7 13:36:34 ubuntu kernel: [  187.014419]  [group_send_sig_info+0x25/0x90] group_send_sig_info+0x25/0x90
Aug  7 13:36:34 ubuntu kernel: [  187.014473]  [kill_pid_info+0x51/0x90] kill_pid_info+0x51/0x90
Aug  7 13:36:34 ubuntu kernel: [  187.014528]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Aug  7 13:36:34 ubuntu kernel: [  187.014580]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Aug  7 13:36:34 ubuntu kernel: [  187.014634]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug  7 13:36:34 ubuntu kernel: [  187.014687]
Aug  7 13:36:34 ubuntu kernel: [  187.014732]
Aug  7 13:36:34 ubuntu kernel: [  187.014733] Code: 48 3b 72 e0 48 8d 42 d0 72 e4 48 8b 52 08 48 85 d2 75 ed 48
Aug  7 13:36:34 ubuntu kernel: [  187.015536]  RSP <ffff8101b41bd870>
Aug  7 13:36:34 ubuntu kernel: [  187.015586] ---[ end trace 9bbdba5fbd953b83 ]---

---

