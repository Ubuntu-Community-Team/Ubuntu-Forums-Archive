---
title: "Ubuntu server - kernel error"
date: 2012-09-17
forum: General Help
---

### Post by jdawgvh on 2012-09-17
I get this when I check my logs.  Can anyone point me in the direction to troubleshoot this?  I am running Ubuntu Server edition 12.04.

```
--------------------- Kernel Begin ------------------------ 

 
 WARNING:  Kernel Errors Present
    EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro ...:  1 Time(s)
 
 1 Time(s): ... bit width:              40
 1 Time(s): ... event mask:             000000000003ffff
 1 Time(s): ... fixed-purpose events:   0
 1 Time(s): ... generic registers:      18
 1 Time(s): ... max period:             0000007fffffffff
 1 Time(s): ... value mask:             000000ffffffffff
 1 Time(s): ... version:                0
 1 Time(s): ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
 1 Time(s): .data : 0xc15ae87c - 0xc1876280   (2846 kB)
 1 Time(s): .init : 0xc1877000 - 0xc1930000   ( 740 kB)
 1 Time(s): .text : 0xc1000000 - 0xc15ae87c   (5818 kB)
 1 Time(s): 0 base 000000000 mask FE0000000 write-back
 1 Time(s): 00000-9FFFF write-back
 1 Time(s): 0000000000 - 0000200000 page 4k
 1 Time(s): 0000200000 - 001f600000 page 2M
 1 Time(s): 001f600000 - 001f688000 page 4k
 1 Time(s): 0: 0x00000010 -> 0x000000a0
 1 Time(s): 0: 0x00000100 -> 0x0001f688
 1 Time(s): 0MB HIGHMEM available.
 1 Time(s): 1 base 01F800000 mask FFF800000 uncachable
 1 Time(s): 2 base 01F700000 mask FFFF00000 uncachable
 1 Time(s): 3 disabled
 1 Time(s): 4 disabled
 1 Time(s): 5 disabled
 1 Time(s): 502MB LOWMEM available.
 1 Time(s): 6 disabled
 1 Time(s): 7 disabled
 1 Time(s): A0000-BFFFF uncachable
 1 Time(s): ACPI _OSC control for PCIe not granted, disabling ASPM
 1 Time(s): ACPI: (supports S0 S1 S3 S4 S5)
 1 Time(s): ACPI: ACPI bus type pnp unregistered
 1 Time(s): ACPI: APIC 000fccff 00092 (v01 DELL    DV051   00000007 ASL  00000061)
 1 Time(s): ACPI: Added _OSI(3.0 _SCP Extensions)
 1 Time(s): ACPI: Added _OSI(Module Device)
 1 Time(s): ACPI: Added _OSI(Processor Aggregator Device)
 1 Time(s): ACPI: Added _OSI(Processor Device)
 1 Time(s): ACPI: BOOT 000fcd91 00028 (v01 DELL    DV051   00000007 ASL  00000061)
 1 Time(s): ACPI: Core revision 20110623
 1 Time(s): ACPI: DSDT fffc487f 02D5F (v01   DELL    dt_ex 00001000 MSFT 0100000D)
 1 Time(s): ACPI: EC: Look up EC in DSDT
 1 Time(s): ACPI: FACP 000fcc8b 00074 (v01 DELL    DV051   00000007 ASL  00000061)
 1 Time(s): ACPI: FACS 1f688c00 00040
 1 Time(s): ACPI: HPET 000fcdf7 00038 (v01 DELL    DV051   00000007 ASL  00000061)
 1 Time(s): ACPI: HPET id: 0x8086a201 base: 0xfed00000
 1 Time(s): ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
 1 Time(s): ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
 1 Time(s): ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
 1 Time(s): ACPI: IRQ0 used by override.
 1 Time(s): ACPI: IRQ2 used by override.
 1 Time(s): ACPI: IRQ9 used by override.
 1 Time(s): ACPI: Interpreter enabled
 1 Time(s): ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] disabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x05] lapic_id[0x06] disabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x06] lapic_id[0x07] disabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x08] lapic_id[0x01] disabled)
 1 Time(s): ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
 2 Time(s): ACPI: Local APIC address 0xfee00000
 1 Time(s): ACPI: MCFG 000fcdb9 0003E (v01 DELL    DV051   00000007 ASL  00000061)
 1 Time(s): ACPI: No dock devices found.
 1 Time(s): ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
 1 Time(s): ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
 1 Time(s): ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12 15)
 1 Time(s): ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
 1 Time(s): ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
 1 Time(s): ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
 1 Time(s): ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
 1 Time(s): ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
 1 Time(s): ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
 1 Time(s): ACPI: PM-Timer IO Port: 0x808
 1 Time(s): ACPI: Power Button [PWRF]
 1 Time(s): ACPI: Power Button [VBTN]
 1 Time(s): ACPI: RSDP 000fec00 00014 (v00 DELL  )
 1 Time(s): ACPI: RSDT 000fcc4f 0003C (v01 DELL    DV051   00000007 ASL  00000061)
 1 Time(s): ACPI: SSDT fffc771b 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
 1 Time(s): ACPI: Using IOAPIC for interrupt routing
 1 Time(s): ACPI: bus type pci registered
 1 Time(s): ACPI: bus type pnp registered
 1 Time(s): ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
 1 Time(s): ADDRCONF(NETDEV_UP): eth0: link is not ready
 2 Time(s): ADDRCONF(NETDEV_UP): eth1: link is not ready
 1 Time(s): AMD AuthenticAMD
 1 Time(s): Adding 513020k swap on /dev/sda5.  Priority:-1 extents:1 across:513020k 
 1 Time(s): Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
 1 Time(s): AppArmor: AppArmor Filesystem Enabled
 1 Time(s): AppArmor: AppArmor initialized
 1 Time(s): BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
 1 Time(s): BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 1 Time(s): BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 1 Time(s): BIOS-e820: 0000000000100000 - 000000001f688c00 (usable)
 1 Time(s): BIOS-e820: 000000001f688c00 - 000000001f68ac00 (ACPI NVS)
 1 Time(s): BIOS-e820: 000000001f68ac00 - 000000001f68cc00 (ACPI data)
 1 Time(s): BIOS-e820: 000000001f68cc00 - 0000000020000000 (reserved)
 1 Time(s): BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 1 Time(s): BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
 1 Time(s): BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
 1 Time(s): BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
 1 Time(s): BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
 1 Time(s): BIOS-provided physical RAM map:
 1 Time(s): Base memory trampoline at [c009b000] 9b000 size 16384
 1 Time(s): Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
 1 Time(s): Booting Node   0, Processors  #1
 1 Time(s): Booting paravirtualized kernel on bare hardware
 1 Time(s): Brought up 2 CPUs
 1 Time(s): Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127530
 1 Time(s): C0000-FFFFF write-protect
 1 Time(s): CPU 0 irqstacks, hard=dd80a000 soft=dd80c000
 1 Time(s): CPU 1 irqstacks, hard=dd8ba000 soft=dd8bc000
 1 Time(s): CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
 1 Time(s): CPU0: Thermal monitoring enabled (TM1)
 1 Time(s): CPU: Physical Processor ID: 0
 1 Time(s): CPU: Processor Core ID: 0
 1 Time(s): Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.89 BogoMIPS (lpj=11171796)
 1 Time(s): Cannot allocate resource for EISA slot 1
 1 Time(s): Cannot allocate resource for EISA slot 2
 1 Time(s): Cannot allocate resource for EISA slot 5
 1 Time(s): Cannot allocate resource for EISA slot 6
 1 Time(s): Centaur CentaurHauls
 1 Time(s): Checking if this processor honours the WP bit even in supervisor mode...Ok.
 1 Time(s): Console: colour dummy device 80x25
 1 Time(s): Console: switching to colour frame buffer device 128x48
 1 Time(s): Cyrix CyrixInstead
 1 Time(s): DMA      0x00000010 -> 0x00001000
 1 Time(s): DMA zone: 0 pages reserved
 1 Time(s): DMA zone: 32 pages used for memmap
 1 Time(s): DMA zone: 3952 pages, LIFO batch:0
 1 Time(s): DMI 2.3 present.
 1 Time(s): DMI: Dell Inc.                 Dell DV051                   /0JC474, BIOS A03 10/08/2005
 1 Time(s): Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
 1 Time(s): Detected 2792.949 MHz processor.
 1 Time(s): Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 1 Time(s): EDD information not available.
 1 Time(s): EFI Variables Facility v0.08 2004-May-17
 1 Time(s): EISA bus registered
 1 Time(s): EISA: Cannot allocate resource for mainboard
 1 Time(s): EISA: Detected 0 cards.
 1 Time(s): EISA: Probing bus 0 at eisa.0
 1 Time(s): ERST: Table is not found!
 1 Time(s): EVM: security.SMACK64
 1 Time(s): EVM: security.capability
 1 Time(s): EVM: security.selinux
 1 Time(s): EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
 1 Time(s): EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
 1 Time(s): EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
 1 Time(s): EXT4-fs (sdb7): mounted filesystem with ordered data mode. Opts: (null)
 1 Time(s): EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
 1 Time(s): Enabling APIC mode:  Flat.  Using 1 I/O APICs
 1 Time(s): FS-Cache: Loaded
 1 Time(s): FS-Cache: Netfs 'nfs' registered for caching
 1 Time(s): Fast TSC calibration using PIT
 1 Time(s): Fixed MDIO Bus: probed
 1 Time(s): Found optimal setting for mtrr clean up
 1 Time(s): Freeing initrd memory: 13824k freed
 1 Time(s): Freeing unused kernel memory: 740k freed
 1 Time(s): GHES: HEST is not enabled!
 1 Time(s): HEST: Table not found.
 1 Time(s): HPET: 3 timers in total, 0 timers will be used for per-cpu timer
 1 Time(s): Hierarchical RCU implementation.
 1 Time(s): HighMem  empty
 1 Time(s): HugeTLB registered 2 MB page size, pre-allocated 0 pages
 1 Time(s): IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
 1 Time(s): IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
 1 Time(s): Initializing CPU#0
 1 Time(s): Initializing CPU#1
 1 Time(s): Initializing HighMem for node 0 (00000000:00000000)
 1 Time(s): Initializing USB Mass Storage driver...
 1 Time(s): Initializing cgroup subsys blkio
 1 Time(s): Initializing cgroup subsys cpu
 1 Time(s): Initializing cgroup subsys cpuacct
 1 Time(s): Initializing cgroup subsys cpuset
 1 Time(s): Initializing cgroup subsys devices
 1 Time(s): Initializing cgroup subsys freezer
 1 Time(s): Initializing cgroup subsys memory
 1 Time(s): Initializing cgroup subsys perf_event
 1 Time(s): Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
 1 Time(s): Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
 1 Time(s): Intel GenuineIntel
 1 Time(s): KERNEL supported cpus:
 1 Time(s): Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=b87cb13b-181b-491d-ac04-2f3aea0bc11c ro resume=/dev/sdb5
 1 Time(s): Kernel logging (proc) stopped.
 1 Time(s): Linux agpgart interface v0.103
 1 Time(s): Linux version 3.2.0-30-generic-pae (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 (Ubuntu 3.2.0-30.48-generic-pae 3.2.27)
 1 Time(s): MTRR default type: uncachable
 1 Time(s): MTRR fixed ranges enabled:
 1 Time(s): MTRR variable ranges enabled:
 1 Time(s): Magic number: 12:516:47
 1 Time(s): Memory: 483032k/514592k available (5818k kernel code, 31112k reserved, 2846k data, 740k init, 0k highmem)
 1 Time(s): Mount-cache hash table entries: 512
 1 Time(s): Movable zone start PFN for each node
 1 Time(s): NET: Registered protocol family 1
 1 Time(s): NET: Registered protocol family 10
 1 Time(s): NET: Registered protocol family 16
 1 Time(s): NET: Registered protocol family 17
 1 Time(s): NET: Registered protocol family 2
 1 Time(s): NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
 1 Time(s): NFSD: starting 90-second grace period
 2 Time(s): NMI watchdog enabled, takes one hw-pmu counter.
 1 Time(s): NR_IRQS:2304 nr_irqs:744 16
 1 Time(s): NSC Geode by NSC
 1 Time(s): NX (Execute Disable) protection: active
 1 Time(s): NX-protecting the kernel data: 4420k
 1 Time(s): NetLabel:  domain hash size = 128
 1 Time(s): NetLabel:  protocols = UNLABELED CIPSOv4
 1 Time(s): NetLabel:  unlabeled traffic allowed by default
 1 Time(s): NetLabel: Initializing
 1 Time(s): New variable MTRRs
 1 Time(s): No connectors reported connected with modes
 1 Time(s): Normal   0x00001000 -> 0x0001f688
 1 Time(s): Normal zone: 123578 pages, LIFO batch:31
 1 Time(s): Normal zone: 974 pages used for memmap
 1 Time(s): On node 0 totalpages: 128536
 1 Time(s): PCI: CLS 64 bytes, default 64
 1 Time(s): PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
 1 Time(s): PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
 1 Time(s): PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
 1 Time(s): PCI: Using ACPI for IRQ routing
 1 Time(s): PCI: Using MMCONFIG for extended config space
 1 Time(s): PCI: Using configuration type 1 for base access
 1 Time(s): PCI: max bus depth: 1 pci_try_num: 2
 1 Time(s): PCI: pci_cache_line_size set to 64 bytes
 1 Time(s): PERCPU: Embedded 14 pages/cpu @df223000 s34240 r0 d23104 u57344
 1 Time(s): PID hash table entries: 2048 (order: 1, 8192 bytes)
 1 Time(s): PM: Checking hibernation image partition /dev/sdb5
 1 Time(s): PM: Hibernation image not present or could not be loaded.
 1 Time(s): PM: Hibernation image partition 8:21 present
 1 Time(s): PM: Image not found (code -22)
 1 Time(s): PM: Looking for hibernation image.
 1 Time(s): PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
 1 Time(s): PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
 1 Time(s): PM: Registering ACPI NVS region at 1f688c00 (8192 bytes)
 1 Time(s): PPP generic driver version 2.4.2
 1 Time(s): Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
 1 Time(s): PnPBIOS: Disabled by ACPI PNP
 1 Time(s): RAMDISK: 1dd3d000 - 1eabd000
 1 Time(s): RCU dyntick-idle grace-period acceleration is enabled.
 1 Time(s): RPC: Registered named UNIX socket transport module.
 1 Time(s): RPC: Registered tcp NFSv4.1 backchannel transport module.
 1 Time(s): RPC: Registered tcp transport module.
 1 Time(s): RPC: Registered udp transport module.
 1 Time(s): RTC time: 22:02:07, date: 09/16/12
 1 Time(s): Refined TSC clocksource calibration: 2792.999 MHz.
 1 Time(s): Registering the dns_resolver key type
 1 Time(s): SCSI subsystem initialized
 1 Time(s): SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
 1 Time(s): SMP: Allowing 8 CPUs, 6 hotplug CPUs
 1 Time(s): Security Framework initialized
 1 Time(s): Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
 1 Time(s): Simple Boot Flag at 0x7a set to 0x1
 1 Time(s): Switching to clocksource hpet
 1 Time(s): Switching to clocksource tsc
 1 Time(s): TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
 1 Time(s): TCP cubic registered
 1 Time(s): TCP established hash table entries: 16384 (order: 5, 131072 bytes)
 1 Time(s): TCP reno registered
 1 Time(s): TCP: Hash tables configured (established 16384 bind 16384)
 1 Time(s): Total of 2 processors activated (11171.87 BogoMIPS).
 1 Time(s): Transmeta GenuineTMx86
 1 Time(s): Transmeta TransmetaCPU
 1 Time(s): Trying to unpack rootfs image as initramfs...
 1 Time(s): UDP hash table entries: 256 (order: 1, 8192 bytes)
 1 Time(s): UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
 1 Time(s): UMC UMC UMC UMC
 1 Time(s): USB Mass Storage support registered.
 1 Time(s): Using ACPI (MADT) for SMP configuration information
 1 Time(s): Using APIC driver default
 1 Time(s): Using IPI No-Shortcut mode
 1 Time(s): VFS: Disk quotas dquot_6.5.2
 1 Time(s): Write protecting the kernel read-only data: 2376k
 1 Time(s): Write protecting the kernel text: 5820k
 1 Time(s): Yama: becoming mindful.
 1 Time(s): Zone PFN ranges:
 1 Time(s): [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
 1 Time(s): [drm] Cannot find any crtc or sizes - going 1024x768
 1 Time(s): [drm] Driver supports precise vblank timestamp query.
 1 Time(s): [drm] Initialized drm 1.1.0 20060810
 1 Time(s): [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
 1 Time(s): [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
 1 Time(s): [drm] initialized overlay support
 1 Time(s): agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
 1 Time(s): agpgart-intel 0000:00:00.0: Intel 915G Chipset
 1 Time(s): agpgart-intel 0000:00:00.0: detected 8192K stolen memory
 1 Time(s): agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
 1 Time(s): ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
 1 Time(s): ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
 1 Time(s): ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
 1 Time(s): ahci 0000:00:1f.2: setting latency timer to 64
 1 Time(s): ahci 0000:00:1f.2: version 3.0
 1 Time(s): allocated 2058112 bytes of page_cgroup
 1 Time(s): ata1.00: 156250000 sectors, multi 8: LBA48 NCQ (depth 31/32)
 1 Time(s): ata1.00: ATA-7: ST380819AS, 8.04, max UDMA/133
 1 Time(s): ata1.00: configured for UDMA/133
 1 Time(s): ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 1 Time(s): ata1: SATA max UDMA/133 abar m1024@0xdff3bc00 port 0xdff3bd00 irq 20
 1 Time(s): ata2: SATA link down (SStatus 0 SControl 300)
 1 Time(s): ata2: SATA max UDMA/133 abar m1024@0xdff3bc00 port 0xdff3bd80 irq 20
 1 Time(s): ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
 1 Time(s): ata3.00: ATA-8: ST2000DM001-9YN164, CC46, max UDMA/133
 1 Time(s): ata3.00: configured for UDMA/133
 1 Time(s): ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 1 Time(s): ata3: SATA max UDMA/133 abar m1024@0xdff3bc00 port 0xdff3be00 irq 20
 1 Time(s): ata4: SATA link down (SStatus 0 SControl 300)
 1 Time(s): ata4: SATA max UDMA/133 abar m1024@0xdff3bc00 port 0xdff3be80 irq 20
 1 Time(s): ata5.00: ATAPI: TSSTcorp CD-RW/DVD-ROM TS-H492C, DE02, max UDMA/33
 1 Time(s): ata5.00: configured for UDMA/33
 1 Time(s): ata5.01: 625142448 sectors, multi 0: LBA48 
 1 Time(s): ata5.01: ATA-7: ST3320620A, 3.AAE, max UDMA/100
 1 Time(s): ata5.01: configured for UDMA/100
 1 Time(s): ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
 1 Time(s): ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
 1 Time(s): ata6: port disabled--ignoring
 1 Time(s): ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 1 Time(s): ata_piix 0000:00:1f.1: setting latency timer to 64
 1 Time(s): ata_piix 0000:00:1f.1: version 2.13
 1 Time(s): audit: initializing netlink socket (disabled)
 1 Time(s): bio: create slab <bio-0> at 0
 1 Time(s): brd: module loaded
 1 Time(s): cdrom: Uniform CD-ROM driver Revision: 3.20
 1 Time(s): console [tty0] enabled
 1 Time(s): cpufreq-nforce2: No nForce2 chipset.
 1 Time(s): cpuidle: using governor ladder
 1 Time(s): cpuidle: using governor menu
 1 Time(s): dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
 1 Time(s): device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
 1 Time(s): device-mapper: uevent: version 1.0.3
 1 Time(s): devtmpfs: initialized
 1 Time(s): drm: registered panic notifier
 1 Time(s): e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
 1 Time(s): e100 0000:03:08.0: PME# disabled
 1 Time(s): e100 0000:03:08.0: eth1: addr 0xdfbef000, irq 20, MAC addr 00:13:20:d2:71:89
 1 Time(s): e100: Copyright(c) 1999-2006 Intel Corporation
 1 Time(s): e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
 1 Time(s): e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
 1 Time(s): e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
 1 Time(s): early_node_map[2] active PFN ranges
 1 Time(s): ehci_hcd 0000:00:1d.7: EHCI Host Controller
 1 Time(s): ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
 1 Time(s): ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
 1 Time(s): ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
 1 Time(s): ehci_hcd 0000:00:1d.7: debug port 1
 1 Time(s): ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
 1 Time(s): ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
 1 Time(s): ehci_hcd 0000:00:1d.7: setting latency timer to 64
 1 Time(s): ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
 1 Time(s): eth1: no IPv6 routers present
 1 Time(s): fb0: inteldrmfb frame buffer device
 1 Time(s): fbcon: inteldrmfb (fb0) is primary device
 1 Time(s): fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
 1 Time(s): found SMP MP-table at [c00fe710] fe710
 1 Time(s): free_area_init_node: node 0, pgdat c1868a80, node_mem_map df297200
 1 Time(s): ftrace: allocating 26555 entries in 52 pages
 1 Time(s): fuse init (API version 7.17)
 1 Time(s): gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
 1 Time(s): hpet clockevent registered
 1 Time(s): hpet0: 3 comparators, 64-bit 14.318180 MHz counter
 1 Time(s): hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
 1 Time(s): hub 1-0:1.0: 8 ports detected
 1 Time(s): hub 1-0:1.0: USB hub found
 1 Time(s): hub 2-0:1.0: 2 ports detected
 1 Time(s): hub 2-0:1.0: USB hub found
 1 Time(s): hub 3-0:1.0: 2 ports detected
 1 Time(s): hub 3-0:1.0: USB hub found
 1 Time(s): hub 4-0:1.0: 2 ports detected
 1 Time(s): hub 4-0:1.0: USB hub found
 1 Time(s): hub 5-0:1.0: 2 ports detected
 1 Time(s): hub 5-0:1.0: USB hub found
 1 Time(s): i2c-core: driver [aat2870] using legacy resume method
 1 Time(s): i2c-core: driver [aat2870] using legacy suspend method
 1 Time(s): i8042: PNP: No PS/2 controller found. Probing ports directly.
 1 Time(s): i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 1 Time(s): i915 0000:00:02.0: setting latency timer to 64
 1 Time(s): imklog 5.8.6, log source = /proc/kmsg started.
 1 Time(s): init: Failed to spawn nmbd main process: unable to execute: No such file or directory
 1 Time(s): init: Failed to spawn smbd main process: unable to execute: No such file or directory
 1 Time(s): init: failsafe main process (859) killed by TERM signal
 1 Time(s): init_memory_mapping: 0000000000000000-000000001f688000
 1 Time(s): initial memory mapped : 0 - 02000000
 1 Time(s): input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
 1 Time(s): input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input2
 1 Time(s): input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
 1 Time(s): input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
 1 Time(s): input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
 1 Time(s): input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
 1 Time(s): intel_rng: Firmware space is locked read-only. If you can't or
 1 Time(s): intel_rng: RNG, try using the 'no_fwh_detect' option.
 1 Time(s): intel_rng: don't want to disable this in firmware setup, and if
 1 Time(s): intel_rng: you are certain that your system has a functional
 1 Time(s): io scheduler cfq registered (default)
 1 Time(s): io scheduler deadline registered
 1 Time(s): io scheduler noop registered
 1 Time(s): ip6_tables: (C) 2000-2006 Netfilter Core Team
 1 Time(s): ip_tables: (C) 2000-2006 Netfilter Core Team
 1 Time(s): isapnp: No Plug & Play device found
 1 Time(s): isapnp: Scanning for PnP cards...
 1 Time(s): kernel direct mapping tables up to 1f688000 @ 1ffb000-2000000
 1 Time(s): last_pfn = 0x1f688 max_arch_pfn = 0x1000000
 1 Time(s): libata version 3.00 loaded.
 1 Time(s): loop: module loaded
 1 Time(s): low ram: 0 - 1f688000
 1 Time(s): lowmem  : 0xc0000000 - 0xdf688000   ( 502 MB)
 1 Time(s): lp: driver loaded but no devices found
 1 Time(s): mapped low ram: 0 - 1f688000
 1 Time(s): mce: CPU supports 4 MCE banks
 1 Time(s): mousedev: PS/2 mouse device common for all mice
 1 Time(s): msgmni has been set to 943
 1 Time(s): nr_irqs_gsi: 40
 1 Time(s): ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 1 Time(s): original variable MTRRs
 1 Time(s): pci 0000:00:00.0: [8086:2580] type 0 class 0x000600
 1 Time(s): pci 0000:00:02.0: Boot video device
 1 Time(s): pci 0000:00:02.0: [8086:2582] type 0 class 0x000300
 1 Time(s): pci 0000:00:02.0: reg 10: [mem 0xdff80000-0xdfffffff]
 1 Time(s): pci 0000:00:02.0: reg 14: [io  0xecd8-0xecdf]
 1 Time(s): pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
 1 Time(s): pci 0000:00:02.0: reg 1c: [mem 0xdff40000-0xdff7ffff]
 1 Time(s): pci 0000:00:1b.0: PME# disabled
 1 Time(s): pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:1b.0: [8086:2668] type 0 class 0x000403
 1 Time(s): pci 0000:00:1b.0: reg 10: [mem 0xdff3c000-0xdff3ffff 64bit]
 1 Time(s): pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
 1 Time(s): pci 0000:00:1c.0:   bridge window [mem 0x20000000-0x201fffff 64bit pref]
 2 Time(s): pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfefffff]
 1 Time(s): pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
 1 Time(s): pci 0000:00:1c.0: BAR 15: assigned [mem 0x20000000-0x201fffff 64bit pref]
 1 Time(s): pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 2 Time(s): pci 0000:00:1c.0: PCI bridge to [bus 01-01]
 1 Time(s): pci 0000:00:1c.0: PME# disabled
 1 Time(s): pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:1c.0: [8086:2660] type 1 class 0x000604
 1 Time(s): pci 0000:00:1c.0: setting latency timer to 64
 2 Time(s): pci 0000:00:1c.1:   bridge window [mem 0xdfd00000-0xdfdfffff]
 1 Time(s): pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
 2 Time(s): pci 0000:00:1c.1: PCI bridge to [bus 02-02]
 1 Time(s): pci 0000:00:1c.1: PME# disabled
 1 Time(s): pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:1c.1: [8086:2662] type 1 class 0x000604
 1 Time(s): pci 0000:00:1c.1: setting latency timer to 64
 1 Time(s): pci 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
 1 Time(s): pci 0000:00:1d.0: PCI INT A disabled
 1 Time(s): pci 0000:00:1d.0: [8086:2658] type 0 class 0x000c03
 1 Time(s): pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]
 1 Time(s): pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
 1 Time(s): pci 0000:00:1d.1: PCI INT B disabled
 1 Time(s): pci 0000:00:1d.1: [8086:2659] type 0 class 0x000c03
 1 Time(s): pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]
 1 Time(s): pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
 1 Time(s): pci 0000:00:1d.2: PCI INT C disabled
 1 Time(s): pci 0000:00:1d.2: [8086:265a] type 0 class 0x000c03
 1 Time(s): pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]
 1 Time(s): pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
 1 Time(s): pci 0000:00:1d.3: PCI INT D disabled
 1 Time(s): pci 0000:00:1d.3: [8086:265b] type 0 class 0x000c03
 1 Time(s): pci 0000:00:1d.3: reg 20: [io  0xff20-0xff3f]
 1 Time(s): pci 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
 1 Time(s): pci 0000:00:1d.7: PCI INT A disabled
 1 Time(s): pci 0000:00:1d.7: PME# disabled
 1 Time(s): pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:1d.7: [8086:265c] type 0 class 0x000c03
 1 Time(s): pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
 1 Time(s): pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
 2 Time(s): pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
 1 Time(s): pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
 2 Time(s): pci 0000:00:1e.0:   bridge window [mem 0xdfb00000-0xdfcfffff]
 1 Time(s): pci 0000:00:1e.0: PCI bridge to [bus 03-03]
 1 Time(s): pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
 1 Time(s): pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
 1 Time(s): pci 0000:00:1e.0: setting latency timer to 64
 1 Time(s): pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0c00-0c7f
 1 Time(s): pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 00e0-00ef
 1 Time(s): pci 0000:00:1f.0: [8086:2640] type 0 class 0x000601
 1 Time(s): pci 0000:00:1f.1: [8086:266f] type 0 class 0x000101
 1 Time(s): pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
 1 Time(s): pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
 1 Time(s): pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
 1 Time(s): pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
 1 Time(s): pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
 1 Time(s): pci 0000:00:1f.2: PME# disabled
 1 Time(s): pci 0000:00:1f.2: PME# supported from D3hot
 1 Time(s): pci 0000:00:1f.2: [8086:2652] type 0 class 0x000101
 1 Time(s): pci 0000:00:1f.2: reg 10: [io  0xfe00-0xfe07]
 1 Time(s): pci 0000:00:1f.2: reg 14: [io  0xfe10-0xfe13]
 1 Time(s): pci 0000:00:1f.2: reg 18: [io  0xfe20-0xfe27]
 1 Time(s): pci 0000:00:1f.2: reg 1c: [io  0xfe30-0xfe33]
 1 Time(s): pci 0000:00:1f.2: reg 20: [io  0xfea0-0xfeaf]
 1 Time(s): pci 0000:00:1f.2: reg 24: [mem 0xdff3bc00-0xdff3bfff]
 1 Time(s): pci 0000:00:1f.3: [8086:266a] type 0 class 0x000c05
 1 Time(s): pci 0000:00:1f.3: reg 20: [io  0xece0-0xecff]
 1 Time(s): pci 0000:03:01.0: PME# disabled
 1 Time(s): pci 0000:03:01.0: PME# supported from D1 D2 D3hot D3cold
 1 Time(s): pci 0000:03:01.0: [10ec:8169] type 0 class 0x000200
 1 Time(s): pci 0000:03:01.0: reg 10: [io  0xdc00-0xdcff]
 1 Time(s): pci 0000:03:01.0: reg 14: [mem 0xdfbeef00-0xdfbeefff]
 1 Time(s): pci 0000:03:01.0: reg 30: [mem 0xdfc00000-0xdfc1ffff pref]
 1 Time(s): pci 0000:03:01.0: supports D1 D2
 1 Time(s): pci 0000:03:02.0: PME# disabled
 1 Time(s): pci 0000:03:02.0: PME# supported from D3hot D3cold
 1 Time(s): pci 0000:03:02.0: [14f1:2f20] type 0 class 0x000780
 1 Time(s): pci 0000:03:02.0: reg 10: [mem 0xdfbf0000-0xdfbfffff]
 1 Time(s): pci 0000:03:02.0: reg 14: [io  0xd8b8-0xd8bf]
 1 Time(s): pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
 1 Time(s): pci 0000:03:08.0: PME# disabled
 1 Time(s): pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot D3cold
 1 Time(s): pci 0000:03:08.0: [8086:1064] type 0 class 0x000200
 1 Time(s): pci 0000:03:08.0: reg 10: [mem 0xdfbef000-0xdfbeffff]
 1 Time(s): pci 0000:03:08.0: reg 14: [io  0xd8c0-0xd8ff]
 1 Time(s): pci 0000:03:08.0: supports D1 D2
 1 Time(s): pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
 1 Time(s): pci0000:00: Requesting ACPI _OSC control (0x1d)
 1 Time(s): pci_bus 0000:00: on NUMA node 0
 1 Time(s): pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
 1 Time(s): pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
 1 Time(s): pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
 1 Time(s): pci_bus 0000:01: resource 1 [mem 0xdfe00000-0xdfefffff]
 1 Time(s): pci_bus 0000:01: resource 2 [mem 0x20000000-0x201fffff 64bit pref]
 1 Time(s): pci_bus 0000:02: resource 1 [mem 0xdfd00000-0xdfdfffff]
 1 Time(s): pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
 1 Time(s): pci_bus 0000:03: resource 1 [mem 0xdfb00000-0xdfcfffff]
 1 Time(s): pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
 1 Time(s): pci_bus 0000:03: resource 5 [mem 0x00000000-0xfffffffff]
 1 Time(s): pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 1 Time(s): pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
 1 Time(s): pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
 1 Time(s): pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
 1 Time(s): pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
 1 Time(s): pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
 1 Time(s): pciehp: PCI Express Hot Plug Controller Driver version: 0.4
 1 Time(s): pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
 1 Time(s): pcieport 0000:00:1c.0: setting latency timer to 64
 1 Time(s): pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
 1 Time(s): pcieport 0000:00:1c.1: setting latency timer to 64
 1 Time(s): pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
 1 Time(s): pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
 1 Time(s): pid_max: default: 32768 minimum: 301
 1 Time(s): pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
 1 Time(s): please try 'cgroup_disable=memory' option if you don't want memory cgroups
 1 Time(s): pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
 1 Time(s): pnp 00:00: [bus 00-ff]
 1 Time(s): pnp 00:00: [io  0x0000-0x0cf7 window]
 1 Time(s): pnp 00:00: [io  0x0cf8-0x0cff]
 1 Time(s): pnp 00:00: [io  0x0d00-0xffff window]
 1 Time(s): pnp 00:00: [mem 0x00000000 window]
 1 Time(s): pnp 00:00: [mem 0x000a0000-0x000bffff window]
 1 Time(s): pnp 00:00: [mem 0x80000000-0xdfffffff window]
 1 Time(s): pnp 00:00: [mem 0xf0000000-0xfebfffff window]
 1 Time(s): pnp 00:01: [io  0x0060]
 1 Time(s): pnp 00:01: [io  0x0062-0x0063]
 1 Time(s): pnp 00:01: [io  0x0064]
 1 Time(s): pnp 00:01: [io  0x0065-0x006f]
 1 Time(s): pnp 00:01: [io  0x00e0-0x00ef]
 1 Time(s): pnp 00:01: [io  0x0800-0x085f]
 1 Time(s): pnp 00:01: [io  0x0860-0x08ff]
 1 Time(s): pnp 00:01: [io  0x0c00-0x0c7f]
 1 Time(s): pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
 1 Time(s): pnp 00:02: [dma 4]
 1 Time(s): pnp 00:02: [io  0x0000-0x001f]
 1 Time(s): pnp 00:02: [io  0x0080-0x009f]
 1 Time(s): pnp 00:02: [io  0x00c0-0x00df]
 1 Time(s): pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
 1 Time(s): pnp 00:03: [io  0x00f0-0x00ff]
 1 Time(s): pnp 00:03: [irq 13]
 1 Time(s): pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
 1 Time(s): pnp 00:04: [io  0x0061]
 1 Time(s): pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
 1 Time(s): pnp 00:05: [io  0x0070-0x007f]
 1 Time(s): pnp 00:05: [irq 8]
 1 Time(s): pnp 00:06: [mem 0x00000000-0x0009ffff]
 1 Time(s): pnp 00:06: [mem 0x000c0000-0x000fffff]
 1 Time(s): pnp 00:06: [mem 0x00100000-0x00ffffff]
 1 Time(s): pnp 00:06: [mem 0x01000000-0x1f688bff]
 1 Time(s): pnp 00:06: [mem 0xfec00000-0xfecfffff]
 1 Time(s): pnp 00:06: [mem 0xfed20000-0xfed9ffff]
 1 Time(s): pnp 00:06: [mem 0xfee00000-0xfeefffff]
 1 Time(s): pnp 00:06: [mem 0xffb00000-0xffbfffff]
 1 Time(s): pnp 00:06: [mem 0xffc00000-0xffffffff]
 1 Time(s): pnp 00:07: [io  0x0100-0x01fe]
 1 Time(s): pnp 00:07: [io  0x0200-0x0277]
 1 Time(s): pnp 00:07: [io  0x0280-0x02e7]
 1 Time(s): pnp 00:07: [io  0x02e8-0x02ef]
 1 Time(s): pnp 00:07: [io  0x02f0-0x02f7]
 1 Time(s): pnp 00:07: [io  0x02f8-0x02ff]
 1 Time(s): pnp 00:07: [io  0x0300-0x0377]
 1 Time(s): pnp 00:07: [io  0x0380-0x03bb]
 1 Time(s): pnp 00:07: [io  0x03c0-0x03e7]
 1 Time(s): pnp 00:07: [io  0x03f6-0x03f7]
 1 Time(s): pnp 00:07: [io  0x0400-0x04cf]
 1 Time(s): pnp 00:07: [io  0x04d2-0x057f]
 1 Time(s): pnp 00:07: [io  0x0580-0x0677]
 1 Time(s): pnp 00:07: [io  0x0680-0x0777]
 1 Time(s): pnp 00:07: [io  0x0780-0x07bb]
 1 Time(s): pnp 00:07: [io  0x07c0-0x07ff]
 1 Time(s): pnp 00:07: [io  0x08e0-0x08ff]
 1 Time(s): pnp 00:07: [io  0x0900-0x09fe]
 1 Time(s): pnp 00:07: [io  0x0a00-0x0afe]
 1 Time(s): pnp 00:07: [io  0x0b00-0x0bfe]
 1 Time(s): pnp 00:07: [io  0x0c80-0x0caf]
 1 Time(s): pnp 00:07: [io  0x0cb0-0x0cbf]
 1 Time(s): pnp 00:07: [io  0x0cc0-0x0cf7]
 1 Time(s): pnp 00:07: [io  0x0d00-0x0dfe]
 1 Time(s): pnp 00:07: [io  0x0e00-0x0efe]
 1 Time(s): pnp 00:07: [io  0x0f00-0x0ffe]
 1 Time(s): pnp 00:07: [io  0x2000-0x20fe]
 1 Time(s): pnp 00:07: [io  0x2100-0x21fe]
 1 Time(s): pnp 00:07: [io  0x2200-0x22fe]
 1 Time(s): pnp 00:07: [io  0x2300-0x23fe]
 1 Time(s): pnp 00:07: [io  0x2400-0x24fe]
 1 Time(s): pnp 00:07: [io  0x2500-0x25fe]
 1 Time(s): pnp 00:07: [io  0x2600-0x26fe]
 1 Time(s): pnp 00:07: [io  0x2700-0x27fe]
 1 Time(s): pnp 00:07: [io  0x2800-0x28fe]
 1 Time(s): pnp 00:07: [io  0x2900-0x29fe]
 1 Time(s): pnp 00:07: [io  0x2a00-0x2afe]
 1 Time(s): pnp 00:07: [io  0x2b00-0x2bfe]
 1 Time(s): pnp 00:07: [io  0x2c00-0x2cfe]
 1 Time(s): pnp 00:07: [io  0x2d00-0x2dfe]
 1 Time(s): pnp 00:07: [io  0x2e00-0x2efe]
 1 Time(s): pnp 00:07: [io  0x2f00-0x2ffe]
 1 Time(s): pnp 00:07: [io  0x5000-0x50fe]
 1 Time(s): pnp 00:07: [io  0x5100-0x51fe]
 1 Time(s): pnp 00:07: [io  0x5200-0x52fe]
 1 Time(s): pnp 00:07: [io  0x5300-0x53fe]
 1 Time(s): pnp 00:07: [io  0x5400-0x54fe]
 1 Time(s): pnp 00:07: [io  0x5500-0x55fe]
 1 Time(s): pnp 00:07: [io  0x5600-0x56fe]
 1 Time(s): pnp 00:07: [io  0x5700-0x57fe]
 1 Time(s): pnp 00:07: [io  0x5800-0x58fe]
 1 Time(s): pnp 00:07: [io  0x5900-0x59fe]
 1 Time(s): pnp 00:07: [io  0x5a00-0x5afe]
 1 Time(s): pnp 00:07: [io  0x5b00-0x5bfe]
 1 Time(s): pnp 00:07: [io  0x5c00-0x5cfe]
 1 Time(s): pnp 00:07: [io  0x5d00-0x5dfe]
 1 Time(s): pnp 00:07: [io  0x5e00-0x5efe]
 1 Time(s): pnp 00:07: [io  0x5f00-0x5ffe]
 1 Time(s): pnp 00:07: [io  0x6000-0x60fe]
 1 Time(s): pnp 00:07: [io  0x6100-0x61fe]
 1 Time(s): pnp 00:07: [io  0x6200-0x62fe]
 1 Time(s): pnp 00:07: [io  0x6300-0x63fe]
 1 Time(s): pnp 00:07: [io  0x6400-0x64fe]
 1 Time(s): pnp 00:07: [io  0x6500-0x65fe]
 1 Time(s): pnp 00:07: [io  0x6600-0x66fe]
 1 Time(s): pnp 00:07: [io  0x6700-0x67fe]
 1 Time(s): pnp 00:07: [io  0x6800-0x68fe]
 1 Time(s): pnp 00:07: [io  0x6900-0x69fe]
 1 Time(s): pnp 00:07: [io  0x6a00-0x6afe]
 1 Time(s): pnp 00:07: [io  0x6b00-0x6bfe]
 1 Time(s): pnp 00:07: [io  0x6c00-0x6cfe]
 1 Time(s): pnp 00:07: [io  0x6d00-0x6dfe]
 1 Time(s): pnp 00:07: [io  0x6e00-0x6efe]
 1 Time(s): pnp 00:07: [io  0x6f00-0x6ffe]
 1 Time(s): pnp 00:07: [io  0xa000-0xa0fe]
 1 Time(s): pnp 00:07: [io  0xa100-0xa1fe]
 1 Time(s): pnp 00:07: [io  0xa200-0xa2fe]
 1 Time(s): pnp 00:07: [io  0xa300-0xa3fe]
 1 Time(s): pnp 00:07: [io  0xa400-0xa4fe]
 1 Time(s): pnp 00:07: [io  0xa500-0xa5fe]
 1 Time(s): pnp 00:07: [io  0xa600-0xa6fe]
 1 Time(s): pnp 00:07: [io  0xa700-0xa7fe]
 1 Time(s): pnp 00:07: [io  0xa800-0xa8fe]
 1 Time(s): pnp 00:07: [io  0xa900-0xa9fe]
 1 Time(s): pnp 00:07: [io  0xaa00-0xaafe]
 1 Time(s): pnp 00:07: [io  0xab00-0xabfe]
 1 Time(s): pnp 00:07: [io  0xac00-0xacfe]
 1 Time(s): pnp 00:07: [io  0xad00-0xadfe]
 1 Time(s): pnp 00:07: [io  0xae00-0xaefe]
 1 Time(s): pnp 00:07: [io  0xaf00-0xaffe]
 1 Time(s): pnp 00:07: [mem 0xe0000000-0xefffffff]
 1 Time(s): pnp 00:07: [mem 0xfeda0000-0xfedacfff]
 1 Time(s): pnp: PnP ACPI init
 1 Time(s): pnp: PnP ACPI: found 8 devices
 1 Time(s): ppdev: user-space parallel port driver
 1 Time(s): print_constraints: dummy: 
 1 Time(s): r8169 0000:03:01.0: (unregistered net_device): not PCI Express
 1 Time(s): r8169 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
 1 Time(s): r8169 0000:03:01.0: eth0: RTL8169sc/8110sc at 0xdfebaf00, 00:0a:cd:1e:77:7d, XID 18000000 IRQ 17
 1 Time(s): r8169 0000:03:01.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
 2 Time(s): r8169 0000:03:01.0: eth1: link down
 1 Time(s): r8169 0000:03:01.0: eth1: link up
 1 Time(s): r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
 2 Time(s): reg 0, base: 0GB, range: 512MB, type WB
 1 Time(s): reg 1, base: 503MB, range: 1MB, type UC
 1 Time(s): reg 1, base: 504MB, range: 8MB, type UC
 1 Time(s): reg 2, base: 503MB, range: 1MB, type UC
 1 Time(s): reg 2, base: 504MB, range: 8MB, type UC
 1 Time(s): registered taskstats version 1
 1 Time(s): reserve RAM buffer: 000000001f688c00 - 000000001fffffff 
 1 Time(s): rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
 1 Time(s): rtc_cmos 00:05: RTC can wake from S4
 1 Time(s): rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
 1 Time(s): rtc_cmos 00:05: setting system clock to 2012-09-16 22:02:09 UTC (1347832929)
 1 Time(s): scsi 0:0:0:0: Direct-Access     ATA      ST380819AS       8.04 PQ: 0 ANSI: 5
 1 Time(s): scsi 2:0:0:0: Direct-Access     ATA      ST2000DM001-9YN1 CC46 PQ: 0 ANSI: 5
 1 Time(s): scsi 4:0:0:0: CD-ROM            TSSTcorp CDRWDVD TS-H492C DE02 PQ: 0 ANSI: 5
 1 Time(s): scsi 4:0:1:0: Direct-Access     ATA      ST3320620A       3.AA PQ: 0 ANSI: 5
 1 Time(s): scsi 6:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.00 PQ: 0 ANSI: 0
 1 Time(s): scsi 6:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.00 PQ: 0 ANSI: 0
 1 Time(s): scsi 6:0:0:2: Direct-Access     TEAC     USB   HS-MS Card 4.00 PQ: 0 ANSI: 0
 1 Time(s): scsi 6:0:0:3: Direct-Access     TEAC     USB   HS-SD Card 4.00 PQ: 0 ANSI: 0
 1 Time(s): scsi0 : ahci
 1 Time(s): scsi1 : ahci
 1 Time(s): scsi2 : ahci
 1 Time(s): scsi3 : ahci
 1 Time(s): scsi4 : ata_piix
 1 Time(s): scsi5 : ata_piix
 1 Time(s): scsi6 : usb-storage 1-7:1.0
 1 Time(s): sd 0:0:0:0: Attached scsi generic sg0 type 0
 1 Time(s): sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
 1 Time(s): sd 0:0:0:0: [sda] Attached SCSI disk
 1 Time(s): sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
 1 Time(s): sd 0:0:0:0: [sda] Write Protect is off
 1 Time(s): sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 1 Time(s): sd 2:0:0:0: Attached scsi generic sg1 type 0
 1 Time(s): sd 2:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
 1 Time(s): sd 2:0:0:0: [sdb] 4096-byte physical blocks
 1 Time(s): sd 2:0:0:0: [sdb] Attached SCSI disk
 1 Time(s): sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
 1 Time(s): sd 2:0:0:0: [sdb] Write Protect is off
 1 Time(s): sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 1 Time(s): sd 4:0:1:0: Attached scsi generic sg3 type 0
 1 Time(s): sd 4:0:1:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
 1 Time(s): sd 4:0:1:0: [sdc] Attached SCSI disk
 1 Time(s): sd 4:0:1:0: [sdc] Mode Sense: 00 3a 00 00
 1 Time(s): sd 4:0:1:0: [sdc] Write Protect is off
 1 Time(s): sd 4:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 1 Time(s): sd 6:0:0:0: Attached scsi generic sg4 type 0
 1 Time(s): sd 6:0:0:0: [sdd] Attached SCSI removable disk
 1 Time(s): sd 6:0:0:1: Attached scsi generic sg5 type 0
 1 Time(s): sd 6:0:0:1: [sde] Attached SCSI removable disk
 1 Time(s): sd 6:0:0:2: Attached scsi generic sg6 type 0
 1 Time(s): sd 6:0:0:2: [sdf] Attached SCSI removable disk
 1 Time(s): sd 6:0:0:3: Attached scsi generic sg7 type 0
 1 Time(s): sd 6:0:0:3: [sdg] Attached SCSI removable disk
 1 Time(s): sda: sda1 sda2 < sda5 >
 1 Time(s): sdb: sdb1 < sdb5 sdb6 sdb7 >
 1 Time(s): sdc: sdc1
 1 Time(s): serio: i8042 AUX port at 0x60,0x64 irq 12
 1 Time(s): serio: i8042 KBD port at 0x60,0x64 irq 1
 1 Time(s): setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
 1 Time(s): smpboot cpu 1: start_ip = 9b000
 1 Time(s): snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 1 Time(s): snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
 1 Time(s): snd_hda_intel 0000:00:1b.0: setting latency timer to 64
 1 Time(s): sr 4:0:0:0: Attached scsi CD-ROM sr0
 1 Time(s): sr 4:0:0:0: Attached scsi generic sg2 type 5
 1 Time(s): sr0: scsi3-mmc drive: 8x/48x writer cd/rw xa/form2 cdda tray
 1 Time(s): system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
 1 Time(s): system 00:01: [io  0x0800-0x085f] has been reserved
 1 Time(s): system 00:01: [io  0x0860-0x08ff] has been reserved
 1 Time(s): system 00:01: [io  0x0c00-0x0c7f] has been reserved
 1 Time(s): system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
 1 Time(s): system 00:06: [mem 0x00000000-0x0009ffff] could not be reserved
 1 Time(s): system 00:06: [mem 0x000c0000-0x000fffff] could not be reserved
 1 Time(s): system 00:06: [mem 0x00100000-0x00ffffff] could not be reserved
 1 Time(s): system 00:06: [mem 0x01000000-0x1f688bff] could not be reserved
 1 Time(s): system 00:06: [mem 0xfec00000-0xfecfffff] could not be reserved
 1 Time(s): system 00:06: [mem 0xfed20000-0xfed9ffff] has been reserved
 1 Time(s): system 00:06: [mem 0xfee00000-0xfeefffff] has been reserved
 1 Time(s): system 00:06: [mem 0xffb00000-0xffbfffff] has been reserved
 1 Time(s): system 00:06: [mem 0xffc00000-0xffffffff] has been reserved
 1 Time(s): system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
 1 Time(s): system 00:07: [io  0x0100-0x01fe] could not be reserved
 1 Time(s): system 00:07: [io  0x0200-0x0277] has been reserved
 1 Time(s): system 00:07: [io  0x0280-0x02e7] has been reserved
 1 Time(s): system 00:07: [io  0x02e8-0x02ef] has been reserved
 1 Time(s): system 00:07: [io  0x02f0-0x02f7] has been reserved
 1 Time(s): system 00:07: [io  0x02f8-0x02ff] has been reserved
 1 Time(s): system 00:07: [io  0x0300-0x0377] could not be reserved
 1 Time(s): system 00:07: [io  0x0380-0x03bb] has been reserved
 1 Time(s): system 00:07: [io  0x03c0-0x03e7] has been reserved
 1 Time(s): system 00:07: [io  0x03f6-0x03f7] could not be reserved
 1 Time(s): system 00:07: [io  0x0400-0x04cf] has been reserved
 1 Time(s): system 00:07: [io  0x04d2-0x057f] has been reserved
 1 Time(s): system 00:07: [io  0x0580-0x0677] has been reserved
 1 Time(s): system 00:07: [io  0x0680-0x0777] has been reserved
 1 Time(s): system 00:07: [io  0x0780-0x07bb] has been reserved
 1 Time(s): system 00:07: [io  0x07c0-0x07ff] has been reserved
 1 Time(s): system 00:07: [io  0x08e0-0x08ff] has been reserved
 1 Time(s): system 00:07: [io  0x0900-0x09fe] has been reserved
 1 Time(s): system 00:07: [io  0x0a00-0x0afe] has been reserved
 1 Time(s): system 00:07: [io  0x0b00-0x0bfe] has been reserved
 1 Time(s): system 00:07: [io  0x0c80-0x0caf] has been reserved
 1 Time(s): system 00:07: [io  0x0cb0-0x0cbf] has been reserved
 1 Time(s): system 00:07: [io  0x0cc0-0x0cf7] has been reserved
 1 Time(s): system 00:07: [io  0x0d00-0x0dfe] has been reserved
 1 Time(s): system 00:07: [io  0x0e00-0x0efe] has been reserved
 1 Time(s): system 00:07: [io  0x0f00-0x0ffe] has been reserved
 1 Time(s): system 00:07: [io  0x2000-0x20fe] has been reserved
 1 Time(s): system 00:07: [io  0x2100-0x21fe] has been reserved
 1 Time(s): system 00:07: [io  0x2200-0x22fe] has been reserved
 1 Time(s): system 00:07: [io  0x2300-0x23fe] has been reserved
 1 Time(s): system 00:07: [io  0x2400-0x24fe] has been reserved
 1 Time(s): system 00:07: [io  0x2500-0x25fe] has been reserved
 1 Time(s): system 00:07: [io  0x2600-0x26fe] has been reserved
 1 Time(s): system 00:07: [io  0x2700-0x27fe] has been reserved
 1 Time(s): system 00:07: [io  0x2800-0x28fe] has been reserved
 1 Time(s): system 00:07: [io  0x2900-0x29fe] has been reserved
 1 Time(s): system 00:07: [io  0x2a00-0x2afe] has been reserved
 1 Time(s): system 00:07: [io  0x2b00-0x2bfe] has been reserved
 1 Time(s): system 00:07: [io  0x2c00-0x2cfe] has been reserved
 1 Time(s): system 00:07: [io  0x2d00-0x2dfe] has been reserved
 1 Time(s): system 00:07: [io  0x2e00-0x2efe] has been reserved
 1 Time(s): system 00:07: [io  0x2f00-0x2ffe] has been reserved
 1 Time(s): system 00:07: [io  0x5000-0x50fe] has been reserved
 1 Time(s): system 00:07: [io  0x5100-0x51fe] has been reserved
 1 Time(s): system 00:07: [io  0x5200-0x52fe] has been reserved
 1 Time(s): system 00:07: [io  0x5300-0x53fe] has been reserved
 1 Time(s): system 00:07: [io  0x5400-0x54fe] has been reserved
 1 Time(s): system 00:07: [io  0x5500-0x55fe] has been reserved
 1 Time(s): system 00:07: [io  0x5600-0x56fe] has been reserved
 1 Time(s): system 00:07: [io  0x5700-0x57fe] has been reserved
 1 Time(s): system 00:07: [io  0x5800-0x58fe] has been reserved
 1 Time(s): system 00:07: [io  0x5900-0x59fe] has been reserved
 1 Time(s): system 00:07: [io  0x5a00-0x5afe] has been reserved
 1 Time(s): system 00:07: [io  0x5b00-0x5bfe] has been reserved
 1 Time(s): system 00:07: [io  0x5c00-0x5cfe] has been reserved
 1 Time(s): system 00:07: [io  0x5d00-0x5dfe] has been reserved
 1 Time(s): system 00:07: [io  0x5e00-0x5efe] has been reserved
 1 Time(s): system 00:07: [io  0x5f00-0x5ffe] has been reserved
 1 Time(s): system 00:07: [io  0x6000-0x60fe] has been reserved
 1 Time(s): system 00:07: [io  0x6100-0x61fe] has been reserved
 1 Time(s): system 00:07: [io  0x6200-0x62fe] has been reserved
 1 Time(s): system 00:07: [io  0x6300-0x63fe] has been reserved
 1 Time(s): system 00:07: [io  0x6400-0x64fe] has been reserved
 1 Time(s): system 00:07: [io  0x6500-0x65fe] has been reserved
 1 Time(s): system 00:07: [io  0x6600-0x66fe] has been reserved
 1 Time(s): system 00:07: [io  0x6700-0x67fe] has been reserved
 1 Time(s): system 00:07: [io  0x6800-0x68fe] has been reserved
 1 Time(s): system 00:07: [io  0x6900-0x69fe] has been reserved
 1 Time(s): system 00:07: [io  0x6a00-0x6afe] has been reserved
 1 Time(s): system 00:07: [io  0x6b00-0x6bfe] has been reserved
 1 Time(s): system 00:07: [io  0x6c00-0x6cfe] has been reserved
 1 Time(s): system 00:07: [io  0x6d00-0x6dfe] has been reserved
 1 Time(s): system 00:07: [io  0x6e00-0x6efe] has been reserved
 1 Time(s): system 00:07: [io  0x6f00-0x6ffe] has been reserved
 1 Time(s): system 00:07: [io  0xa000-0xa0fe] has been reserved
 1 Time(s): system 00:07: [io  0xa100-0xa1fe] has been reserved
 1 Time(s): system 00:07: [io  0xa200-0xa2fe] has been reserved
 1 Time(s): system 00:07: [io  0xa300-0xa3fe] has been reserved
 1 Time(s): system 00:07: [io  0xa400-0xa4fe] has been reserved
 1 Time(s): system 00:07: [io  0xa500-0xa5fe] has been reserved
 1 Time(s): system 00:07: [io  0xa600-0xa6fe] has been reserved
 1 Time(s): system 00:07: [io  0xa700-0xa7fe] has been reserved
 1 Time(s): system 00:07: [io  0xa800-0xa8fe] has been reserved
 1 Time(s): system 00:07: [io  0xa900-0xa9fe] has been reserved
 1 Time(s): system 00:07: [io  0xaa00-0xaafe] has been reserved
 1 Time(s): system 00:07: [io  0xab00-0xabfe] has been reserved
 1 Time(s): system 00:07: [io  0xac00-0xacfe] has been reserved
 1 Time(s): system 00:07: [io  0xad00-0xadfe] has been reserved
 1 Time(s): system 00:07: [io  0xae00-0xaefe] has been reserved
 1 Time(s): system 00:07: [io  0xaf00-0xaffe] has been reserved
 1 Time(s): system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
 1 Time(s): system 00:07: [mem 0xfeda0000-0xfedacfff] has been reserved
 1 Time(s): total RAM covered: 503M
 1 Time(s): tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
 1 Time(s): tun: Universal TUN/TAP device driver, 1.6
 1 Time(s): uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
 1 Time(s): uhci_hcd 0000:00:1d.0: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
 1 Time(s): uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
 1 Time(s): uhci_hcd 0000:00:1d.0: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
 1 Time(s): uhci_hcd 0000:00:1d.1: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
 1 Time(s): uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
 1 Time(s): uhci_hcd 0000:00:1d.1: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
 1 Time(s): uhci_hcd 0000:00:1d.2: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
 1 Time(s): uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
 1 Time(s): uhci_hcd 0000:00:1d.2: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
 1 Time(s): uhci_hcd 0000:00:1d.3: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
 1 Time(s): uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
 1 Time(s): uhci_hcd 0000:00:1d.3: setting latency timer to 64
 1 Time(s): uhci_hcd: USB Universal Host Controller Interface driver
 1 Time(s): usb 1-7: new high-speed USB device number 2 using ehci_hcd
 1 Time(s): usbcore: registered new device driver usb
 1 Time(s): usbcore: registered new interface driver hub
 1 Time(s): usbcore: registered new interface driver libusual
 1 Time(s): usbcore: registered new interface driver usb-storage
 1 Time(s): usbcore: registered new interface driver usbfs
 1 Time(s): using mwait in idle threads.
 1 Time(s): vgaarb: bridge control possible 0000:00:02.0
 1 Time(s): vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
 1 Time(s): vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
 1 Time(s): vgaarb: loaded
 1 Time(s): virtual kernel memory layout:
 1 Time(s): vmalloc : 0xdfe88000 - 0xffbfe000   ( 509 MB)
 1 Time(s): x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
 
 ---------------------- Kernel End ------------------------- 
```

---

### Post by bobstuff on 2012-11-18
I am getting a similar report in my logwatch. This is a new problem, this appeared only yesterday after updates. There are no pending updates listed. Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-33-generic-pae i686)

In the **Unmatched Entries ** section I am getting 7 of the first entry with different 'sender' numbers. I have removed the remaining 6 of to conserve space:

         [FONT=&quot][B]**Unmatched Entries** 

  dbus: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.23" (uid=104 pid=1791 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1504 comm="/usr/sbin/console-kit-daemon --no-daemon "): 1 Time(s) 

  lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0: 7 Time(s) 

  lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob": 5 Time(s) 

  polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.42 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8): 1 Time(s) 

  polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.45 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8): 1 Time(s) 

  polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.42, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus): 1 Time(s) [/B][/FONT]
        
Any suggestion on how to investigate this problem?

---

