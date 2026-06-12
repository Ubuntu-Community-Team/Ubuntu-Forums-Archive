---
title: "SDHC errors..."
date: 2009-10-18
forum: General Help
---

### Post by infinitelink on 2009-10-18
So I insert an SDHC and nothing happens, doesn't show on desktop, nor in the filesystem at the place an SD would usually show; dmesg gives the following,

> [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517957
[    0.000000] Kernel command line: root=UUID=48e02f3f-d8bd-4f10-9858-bd52e0fff871 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1197.019 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10443200 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2044660k/2088640k available (4116k kernel code, 42564k reserved, 2199k data, 532k init, 1183432k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 2394.03 BogoMIPS (lpj=4788076)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.019753] ACPI: Core revision 20080926
[    0.028327] ACPI: Checking initramfs for custom DSDT
[    0.556520] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.597963] CPU0: Intel(R) Core(TM)2 Duo CPU     U7600  @ 1.20GHz stepping 0d
[    0.600002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 2393.98 BogoMIPS (lpj=4787962)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.684606] CPU1: Intel(R) Core(TM)2 Duo CPU     U7600  @ 1.20GHz stepping 0d
[    0.684629] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.688050] Brought up 2 CPUs
[    0.688054] Total of 2 processors activated (4788.01 BogoMIPS).
[    0.688122] CPU0 attaching sched-domain:
[    0.688126]  domain 0: span 0-1 level MC
[    0.688130]   groups: 0 1
[    0.688140] CPU1 attaching sched-domain:
[    0.688143]  domain 0: span 0-1 level MC
[    0.688147]   groups: 1 0
[    0.688249] net_namespace: 776 bytes
[    0.688249] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.688249] Booting paravirtualized kernel on bare hardware
[    0.688495] Time: 14:24:35  Date: 10/18/09
[    0.688495] regulator: core version 0.5
[    0.688495] NET: Registered protocol family 16
[    0.688495] EISA bus registered
[    0.688495] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.688495] ACPI: bus type pci registered
[    0.688495] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.688495] PCI: Not using MMCONFIG.
[    0.689687] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=16
[    0.689690] PCI: Using configuration type 1 for base access
[    0.694468] ACPI: EC: Look up EC in DSDT
[    0.740024] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.772269] ACPI: Interpreter enabled
[    0.772279] ACPI: (supports S0 S3 S4 S5)
[    0.772305] ACPI: Using IOAPIC for interrupt routing
[    0.772410] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.786173] PCI: MCFG area at f8000000 reserved in ACPI motherboard resources
[    0.786177] PCI: Using MMCONFIG for extended config space
[    0.806010] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.806014] ACPI: EC: driver started in interrupt mode
[    0.806422] ACPI: No dock devices found.
[    0.806439] ACPI: PCI Root Bridge [C003] (0000:00)
[    0.806581] pci 0000:00:02.0: reg 10 64bit mmio: [0xe0400000-0xe04fffff]
[    0.806593] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.806602] pci 0000:00:02.0: reg 20 io port: [0x2000-0x2007]
[    0.806657] pci 0000:00:02.1: reg 10 64bit mmio: [0xe0500000-0xe05fffff]
[    0.806807] pci 0000:00:19.0: reg 10 32bit mmio: [0xe0600000-0xe061ffff]
[    0.806818] pci 0000:00:19.0: reg 14 32bit mmio: [0xe0620000-0xe0620fff]
[    0.806830] pci 0000:00:19.0: reg 18 io port: [0x2020-0x203f]
[    0.806877] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.806884] pci 0000:00:19.0: PME# disabled
[    0.806959] pci 0000:00:1a.0: reg 20 io port: [0x2040-0x205f]
[    0.807043] pci 0000:00:1a.1: reg 20 io port: [0x2060-0x207f]
[    0.807137] pci 0000:00:1a.7: reg 10 32bit mmio: [0xe0621000-0xe06213ff]
[    0.807201] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.807209] pci 0000:00:1a.7: PME# disabled
[    0.807285] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe0624000-0xe0627fff]
[    0.807340] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.807347] pci 0000:00:1b.0: PME# disabled
[    0.807437] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.807444] pci 0000:00:1c.0: PME# disabled
[    0.807539] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.807546] pci 0000:00:1c.1: PME# disabled
[    0.807637] pci 0000:00:1d.0: reg 20 io port: [0x2080-0x209f]
[    0.807722] pci 0000:00:1d.1: reg 20 io port: [0x20a0-0x20bf]
[    0.807806] pci 0000:00:1d.2: reg 20 io port: [0x20c0-0x20df]
[    0.807898] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0628000-0xe06283ff]
[    0.807961] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.807968] pci 0000:00:1d.7: PME# disabled
[    0.808183] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.808190] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
[    0.808239] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.808249] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.808260] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.808271] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.808283] pci 0000:00:1f.1: reg 20 io port: [0x20e0-0x20ef]
[    0.808648] pci 0000:10:00.0: reg 10 64bit mmio: [0xe0000000-0xe0001fff]
[    0.808851] pci 0000:10:00.0: PME# supported from D0 D3hot D3cold
[    0.808883] pci 0000:10:00.0: PME# disabled
[    0.809040] pci 0000:00:1c.1: bridge 32bit mmio: [0xe0000000-0xe00fffff]
[    0.809134] pci 0000:02:06.0: reg 10 32bit mmio: [0xe0100000-0xe0100fff]
[    0.809152] pci 0000:02:06.0: supports D1 D2
[    0.809156] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.809164] pci 0000:02:06.0: PME# disabled
[    0.809230] pci 0000:02:06.1: reg 10 32bit mmio: [0xe0101000-0xe01017ff]
[    0.809306] pci 0000:02:06.1: supports D1 D2
[    0.809309] pci 0000:02:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.809317] pci 0000:02:06.1: PME# disabled
[    0.809383] pci 0000:02:06.2: reg 10 32bit mmio: [0xe0102000-0xe01020ff]
[    0.809459] pci 0000:02:06.2: supports D1 D2
[    0.809462] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.809470] pci 0000:02:06.2: PME# disabled
[    0.809536] pci 0000:02:06.3: reg 10 32bit mmio: [0xe0103000-0xe01030ff]
[    0.809612] pci 0000:02:06.3: supports D1 D2
[    0.809615] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.809623] pci 0000:02:06.3: PME# disabled
[    0.809709] pci 0000:00:1e.0: transparent bridge
[    0.809720] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0100000-0xe03fffff]
[    0.809788] bus 00 -> node 0
[    0.809797] ACPI: PCI Interrupt Routing Table [\_SB_.C003._PRT]
[    0.810600] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C0B2._PRT]
[    0.810900] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C11F._PRT]
[    0.811163] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C133._PRT]
[    0.884772] ACPI: PCI Interrupt Link [C12F] (IRQs *10 11)
[    0.885186] ACPI: PCI Interrupt Link [C130] (IRQs *10 11)
[    0.885595] ACPI: PCI Interrupt Link [C131] (IRQs 10 *11)
[    0.886004] ACPI: PCI Interrupt Link [C132] (IRQs 10 11) *5
[    0.886413] ACPI: PCI Interrupt Link [C142] (IRQs *10 11)
[    0.886807] ACPI: PCI Interrupt Link [C143] (IRQs 10 11) *0, disabled.
[    0.887217] ACPI: PCI Interrupt Link [C144] (IRQs 10 *11)
[    0.887411] ACPI Exception (pci_link-0189): AE_NOT_FOUND, Evaluating _PRS [20080926]
[    0.887714] ACPI: Power Resource [C29F] (on)
[    0.887813] ACPI: Power Resource [C1C7] (off)
[    0.888018] ACPI: Power Resource [C3AD] (off)
[    0.888208] ACPI: Power Resource [C3B0] (off)
[    0.888397] ACPI: Power Resource [C3C3] (off)
[    0.888595] ACPI: Power Resource [C3C4] (off)
[    0.888783] ACPI: Power Resource [C3C5] (off)
[    0.888970] ACPI: Power Resource [C3C6] (off)
[    0.889158] ACPI: Power Resource [C3C7] (off)
[    0.889548] ACPI: WMI: Mapper loaded
[    0.889606] SCSI subsystem initialized
[    0.889606] libata version 3.00 loaded.
[    0.889606] usbcore: registered new interface driver usbfs
[    0.889606] usbcore: registered new interface driver hub
[    0.889606] usbcore: registered new device driver usb
[    0.889606] PCI: Using ACPI for IRQ routing
[    0.896014] Bluetooth: Core ver 2.13
[    0.896036] NET: Registered protocol family 31
[    0.896036] Bluetooth: HCI device and connection manager initialized
[    0.896036] Bluetooth: HCI socket layer initialized
[    0.896036] NET: Registered protocol family 8
[    0.896036] NET: Registered protocol family 20
[    0.896052] NetLabel: Initializing
[    0.896055] NetLabel:  domain hash size = 128
[    0.896058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.896079] NetLabel:  unlabeled traffic allowed by default
[    0.896100] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.896108] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.900093] AppArmor: AppArmor Filesystem Enabled
[    0.904013] Switched to high resolution mode on CPU 0
[    0.904677] Switched to high resolution mode on CPU 1
[    0.908016] pnp: PnP ACPI init
[    0.908028] ACPI: bus type pnp registered
[    0.924346] pnp: PnP ACPI: found 14 devices
[    0.924350] ACPI: ACPI bus type pnp unregistered
[    0.924356] PnPBIOS: Disabled by ACPI PNP
[    0.924369] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.924374] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.924378] system 00:00: iomem range 0x100000-0x7f7fffff could not be reserved
[    0.924394] system 00:0a: ioport range 0x500-0x55f has been reserved
[    0.924399] system 00:0a: ioport range 0x800-0x80f has been reserved
[    0.924403] system 00:0a: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.924408] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.924417] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.924421] system 00:0c: ioport range 0x2f8-0x2ff has been reserved
[    0.924425] system 00:0c: ioport range 0x3f8-0x3ff has been reserved
[    0.924429] system 00:0c: ioport range 0x1000-0x107f has been reserved
[    0.924433] system 00:0c: ioport range 0x1100-0x113f has been reserved
[    0.924437] system 00:0c: ioport range 0x1200-0x121f has been reserved
[    0.924441] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.924446] system 00:0c: iomem range 0xfec00000-0xfec000ff has been reserved
[    0.924450] system 00:0c: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.924454] system 00:0c: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.924458] system 00:0c: iomem range 0xfed90000-0xfed99fff has been reserved
[    0.924467] system 00:0d: iomem range 0xcee00-0xcffff has been reserved
[    0.924471] system 00:0d: iomem range 0xd2000-0xd3fff has been reserved
[    0.924475] system 00:0d: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.924479] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.959308] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:08
[    0.959312] pci 0000:00:1c.0:   IO window: disabled
[    0.959320] pci 0000:00:1c.0:   MEM window: disabled
[    0.959327] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.959338] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:10
[    0.959341] pci 0000:00:1c.1:   IO window: disabled
[    0.959350] pci 0000:00:1c.1:   MEM window: 0xe0000000-0xe00fffff
[    0.959357] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.959372] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.959375] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.959383] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.959391] pci 0000:02:06.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.959399] pci 0000:02:06.0:   MEM window: 0x8c000000-0x8fffffff
[    0.959407] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.959413] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.959422] pci 0000:00:1e.0:   MEM window: 0xe0100000-0xe03fffff
[    0.959429] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.959454] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.959462] pci 0000:00:1c.0: setting latency timer to 64
[    0.959477] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.959484] pci 0000:00:1c.1: setting latency timer to 64
[    0.959496] pci 0000:00:1e.0: setting latency timer to 64
[    0.959512] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.959522] bus: 00 index 0 io port: [0x00-0xffff]
[    0.959526] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.959529] bus: 08 index 0 mmio: [0x0-0x0]
[    0.959532] bus: 08 index 1 mmio: [0x0-0x0]
[    0.959535] bus: 08 index 2 mmio: [0x0-0x0]
[    0.959538] bus: 08 index 3 mmio: [0x0-0x0]
[    0.959541] bus: 10 index 0 mmio: [0x0-0x0]
[    0.959545] bus: 10 index 1 mmio: [0xe0000000-0xe00fffff]
[    0.959548] bus: 10 index 2 mmio: [0x0-0x0]
[    0.959551] bus: 10 index 3 mmio: [0x0-0x0]
[    0.959554] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.959558] bus: 02 index 1 mmio: [0xe0100000-0xe03fffff]
[    0.959561] bus: 02 index 2 mmio: [0x88000000-0x8bffffff]
[    0.959564] bus: 02 index 3 io port: [0x00-0xffff]
[    0.959567] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.959571] bus: 03 index 0 io port: [0x3000-0x30ff]
[    0.959574] bus: 03 index 1 io port: [0x3400-0x34ff]
[    0.959577] bus: 03 index 2 mmio: [0x88000000-0x8bffffff]
[    0.959581] bus: 03 index 3 mmio: [0x8c000000-0x8fffffff]
[    0.959593] NET: Registered protocol family 2
[    0.972082] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.972455] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.972975] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.973238] TCP: Hash tables configured (established 131072 bind 65536)
[    0.973241] TCP reno registered
[    0.980108] NET: Registered protocol family 1
[    0.980288] checking if image is initramfs... it is
[    2.029393] Freeing initrd memory: 7416k freed
[    2.029670] cpufreq: No nForce2 chipset.
[    2.029874] audit: initializing netlink socket (disabled)
[    2.029908] type=2000 audit(1255875876.028:1): initialized
[    2.041603] highmem bounce pool size: 64 pages
[    2.041610] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.043722] VFS: Disk quotas dquot_6.5.1
[    2.043813] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.044762] fuse init (API version 7.10)
[    2.044894] msgmni has been set to 1698
[    2.045163] alg: No test for stdrng (krng)
[    2.045181] io scheduler noop registered
[    2.045185] io scheduler anticipatory registered
[    2.045188] io scheduler deadline registered
[    2.045209] io scheduler cfq registered (default)
[    2.045226] pci 0000:00:02.0: Boot video device
[    2.059819] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.059887] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.059938] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    2.059960] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.059983] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.060087] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.060151] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.060196] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    2.060218] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.060238] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.060353] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.060367] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.064742] ACPI: AC Adapter [C23B] (on-line)
[    2.108078] ACPI: Battery Slot [C23D] (battery present)
[    2.108187] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.108191] ACPI: Power Button (FF) [PWRF]
[    2.108286] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    2.108290] ACPI: Sleep Button (CM) [C2BF]
[    2.108371] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.108913] ACPI: Lid Switch [C155]
[    2.109370] fan PNP0C0B:00: registered as cooling_device0
[    2.109379] ACPI: Fan [C3B1] (off)
[    2.109760] fan PNP0C0B:01: registered as cooling_device1
[    2.109769] ACPI: Fan [C3B2] (off)
[    2.110151] fan PNP0C0B:02: registered as cooling_device2
[    2.110162] ACPI: Fan [C3C8] (off)
[    2.110545] fan PNP0C0B:03: registered as cooling_device3
[    2.110554] ACPI: Fan [C3C9] (off)
[    2.110931] fan PNP0C0B:04: registered as cooling_device4
[    2.110940] ACPI: Fan [C3CA] (off)
[    2.111324] fan PNP0C0B:05: registered as cooling_device5
[    2.111333] ACPI: Fan [C3CB] (off)
[    2.111710] fan PNP0C0B:06: registered as cooling_device6
[    2.111718] ACPI: Fan [C3CC] (off)
[    2.112487] ACPI: SSDT 7F7DBCCA, 023D (r1 HP      Cpu0Ist     3000 INTL 20060317)
[    2.113316] ACPI: SSDT 7F7DBF8C, 05FA (r1 HP      Cpu0Cst     3001 INTL 20060317)
[    2.117232] Monitor-Mwait will be used to enter C-1 state
[    2.117237] Monitor-Mwait will be used to enter C-2 state
[    2.117257] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.117287] processor ACPI_CPU:00: registered as cooling_device7
[    2.117293] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.117778] ACPI: SSDT 7F7DBC02, 00C8 (r1 HP      Cpu1Ist     3000 INTL 20060317)
[    2.118537] ACPI: SSDT 7F7DBF07, 0085 (r1 HP      Cpu1Cst     3000 INTL 20060317)
[    2.120342] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.120373] processor ACPI_CPU:01: registered as cooling_device8
[    2.120378] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.131775] thermal LNXTHERM:01: registered as thermal_zone0
[    2.132730] ACPI: Thermal Zone [TZ6] (25 C)
[    2.145857] thermal LNXTHERM:02: registered as thermal_zone1
[    2.153854] ACPI: Thermal Zone [TZ0] (60 C)
[    2.158014] thermal LNXTHERM:03: registered as thermal_zone2
[    2.160469] ACPI: Thermal Zone [TZ1] (62 C)
[    2.164983] thermal LNXTHERM:04: registered as thermal_zone3
[    2.167242] ACPI: Thermal Zone [TZ3] (50 C)
[    2.172503] thermal LNXTHERM:05: registered as thermal_zone4
[    2.180979] ACPI: Thermal Zone [TZ4] (27 C)
[    2.182657] thermal LNXTHERM:06: registered as thermal_zone5
[    2.186619] ACPI: Thermal Zone [TZ5] (69 C)
[    2.186721] isapnp: Scanning for PnP cards...
[    2.541312] isapnp: No Plug & Play device found
[    2.549442] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.551141] brd: module loaded
[    2.551613] loop: module loaded
[    2.551712] Fixed MDIO Bus: probed
[    2.551721] PPP generic driver version 2.4.2
[    2.551815] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.551859] Driver 'sd' needs updating - please use bus_type methods
[    2.551874] Driver 'sr' needs updating - please use bus_type methods
[    2.551987] ata_piix 0000:00:1f.1: version 2.12
[    2.552001] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.552056] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.552157] scsi0 : ata_piix
[    2.552276] scsi1 : ata_piix
[    2.553016] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20e0 irq 14
[    2.553021] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20e8 irq 15
[    2.724555] ata1.00: ATA-7: TOSHIBA MK8009GAH, BS021C, max UDMA/100
[    2.724560] ata1.00: 156301488 sectors, multi 16: LBA 
[    2.724614] ata1.01: ATAPI: MATSHITADVD-RAM UJ-852S, 1.02, max MWDMA2
[    2.732502] ata1.00: configured for UDMA/100
[    2.748620] ata1.01: configured for MWDMA2
[    2.749047] ata2: port disabled. ignoring.
[    2.749201] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8009GA BS02 PQ: 0 ANSI: 5
[    2.749339] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.749365] sd 0:0:0:0: [sda] Write Protect is off
[    2.749368] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.749408] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.749501] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.749524] sd 0:0:0:0: [sda] Write Protect is off
[    2.749528] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.749568] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.749573]  sda: sda1 sda2 sda3 sda4
[    2.800813] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.800873] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.802677] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-852S  1.02 PQ: 0 ANSI: 5
[    2.808174] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.808179] Uniform CD-ROM driver Revision: 3.20
[    2.808313] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.808368] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.809388] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.809415] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.809445] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.809451] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.809533] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.813452] ehci_hcd 0000:00:1a.7: debug port 1
[    2.813461] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.813482] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe0621000
[    2.828013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.828110] usb usb1: configuration #1 chosen from 1 choice
[    2.828151] hub 1-0:1.0: USB hub found
[    2.828163] hub 1-0:1.0: 4 ports detected
[    2.828319] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.828335] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.828341] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.828412] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.832342] ehci_hcd 0000:00:1d.7: debug port 1
[    2.832351] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.832369] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe0628000
[    2.848014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.848100] usb usb2: configuration #1 chosen from 1 choice
[    2.848146] hub 2-0:1.0: USB hub found
[    2.848156] hub 2-0:1.0: 6 ports detected
[    2.848300] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.848326] uhci_hcd: USB Universal Host Controller Interface driver
[    2.848356] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.848365] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.848370] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.848439] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.848482] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00002040
[    2.848589] usb usb3: configuration #1 chosen from 1 choice
[    2.848630] hub 3-0:1.0: USB hub found
[    2.848640] hub 3-0:1.0: 2 ports detected
[    2.848763] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.848772] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.848778] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.848838] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.848880] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00002060
[    2.848989] usb usb4: configuration #1 chosen from 1 choice
[    2.849042] hub 4-0:1.0: USB hub found
[    2.849051] hub 4-0:1.0: 2 ports detected
[    2.849177] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.849186] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.849191] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.849253] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.849285] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002080
[    2.849389] usb usb5: configuration #1 chosen from 1 choice
[    2.849428] hub 5-0:1.0: USB hub found
[    2.849437] hub 5-0:1.0: 2 ports detected
[    2.849567] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.849577] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.849582] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.849645] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.849685] uhci_hcd 0000:00:1d.1: irq 22, io base 0x000020a0
[    2.849792] usb usb6: configuration #1 chosen from 1 choice
[    2.849831] hub 6-0:1.0: USB hub found
[    2.849839] hub 6-0:1.0: 2 ports detected
[    2.849969] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.849979] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.849984] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.850046] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.850077] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000020c0
[    2.850189] usb usb7: configuration #1 chosen from 1 choice
[    2.850228] hub 7-0:1.0: USB hub found
[    2.850236] hub 7-0:1.0: 2 ports detected
[    2.850457] PNP: PS/2 Controller [PNP0303:C29C,PNP0f13:C29D] at 0x60,0x64 irq 1,12
[    2.852356] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.853035] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.853042] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.853047] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.853051] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.853054] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.857059] mice: PS/2 mouse device common for all mice
[    2.873104] rtc_cmos 00:06: RTC can wake from S4
[    2.873158] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.873197] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.873287] device-mapper: uevent: version 1.0.3
[    2.873424] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.873532] device-mapper: multipath: version 1.0.5 loaded
[    2.873536] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.873653] EISA: Probing bus 0 at eisa.0
[    2.873662] Cannot allocate resource for EISA slot 1
[    2.873666] Cannot allocate resource for EISA slot 2
[    2.873670] Cannot allocate resource for EISA slot 3
[    2.873701] EISA: Detected 0 cards.
[    2.873852] cpuidle: using governor ladder
[    2.873992] cpuidle: using governor menu
[    2.874802] TCP cubic registered
[    2.874950] NET: Registered protocol family 10
[    2.875626] lo: Disabled Privacy Extensions
[    2.876162] NET: Registered protocol family 17
[    2.876187] Bluetooth: L2CAP ver 2.11
[    2.876190] Bluetooth: L2CAP socket layer initialized
[    2.876194] Bluetooth: SCO (Voice Link) ver 0.6
[    2.876196] Bluetooth: SCO socket layer initialized
[    2.876239] Bluetooth: RFCOMM socket layer initialized
[    2.876242] Marking TSC unstable due to TSC halts in idle
[    2.876253] Bluetooth: RFCOMM TTY layer initialized
[    2.876256] Bluetooth: RFCOMM ver 1.10
[    2.877223] Using IPI No-Shortcut mode
[    2.877321] registered taskstats version 1
[    2.877478]   Magic number: 13:236:435
[    2.877581] rtc_cmos 00:06: setting system clock to 2009-10-18 14:24:37 UTC (1255875877)
[    2.877586] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.877589] EDD information not available.
[    2.877967] Freeing unused kernel memory: 532k freed
[    2.878191] Write protecting the kernel text: 4120k
[    2.878274] Write protecting the kernel read-only data: 1524k
[    2.894453] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.167029] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    3.167034] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.167123] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.167141] e1000e 0000:00:19.0: setting latency timer to 64
[    3.167455] e1000e 0000:00:19.0: irq 2301 for MSI/MSI-X
[    3.349170] ohci1394 0000:02:06.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.375208] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1e:68:19:c6:1a
[    3.375213] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.375249] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: ffffff-0ff
[    3.402038] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e0101000-e01017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.406314] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    3.573148] usb 5-2: configuration #1 chosen from 1 choice
[    3.845093] PM: Starting manual resume from disk
[    3.845099] PM: Resume from partition 8:3
[    3.845101] PM: Checking hibernation image.
[    3.845396] PM: Resume from disk failed.
[    3.887933] kjournald starting.  Commit interval 5 seconds
[    3.887953] EXT3-fs: mounted filesystem with ordered data mode.
[    4.736493] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b249929fd1310]
[   13.534289] udev: starting version 141
[   14.806265] cfg80211: Calling CRDA to update world regulatory domain
[   14.977740] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   15.114817] cfg80211: World regulatory domain updated:
[   15.114822] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.114826] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.114830] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.114833] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.114837] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.114840] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.228342] ricoh-mmc: Ricoh MMC Controller disabling driver
[   15.228346] ricoh-mmc: Copyright(c) Philip Langdale
[   15.228396] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.3 [1180:0843] (rev 11)
[   15.228425] ricoh-mmc: Controller is now disabled.
[   15.425696] sdhci: Secure Digital Host Controller Interface driver
[   15.425701] sdhci: Copyright(c) Pierre Ossman
[   15.460896] sdhci-pci 0000:02:06.2: SDHCI controller found [1180:0822] (rev 21)
[   15.460918] sdhci-pci 0000:02:06.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[   15.464239] mmc0: SDHCI controller on PCI [0000:02:06.2] using PIO
[   15.584892] mmc0: new SDHC card at address 8fcf
[   15.898166] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:30c9]
[   16.025461] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0cb8, PCI irq 18
[   16.025467] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   16.025472] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   16.025482] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   16.025487] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   16.025880] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe03fffff
[   16.025885] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   16.120141] Linux agpgart interface v0.103
[   16.145155] lis3lv02d: hardware type NC2510 found.
[   16.162073] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   16.165900] lis3lv02d driver loaded.
[   16.166206] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   16.205666] iTCO_vendor_support: vendor-support=0
[   16.207873] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   16.208033] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   16.208114] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.255533] tpm_inf_pnp 00:02: Found C284 with ID IFX0102
[   16.255597] tpm_inf_pnp 00:02: TPM found: config base 0x560, data base 0x570, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   16.313883] mmcblk0: mmc0:8fcf SD04G 3.69 GiB 
[   16.313953]  mmcblk0:<3>mmcblk0: error -84 transferring data
[   16.318454] end_request: I/O error, dev mmcblk0, sector 0
[   16.318461] Buffer I/O error on device mmcblk0, logical block 0
[   16.322982] mmcblk0: error -84 transferring data
[   16.322986] end_request: I/O error, dev mmcblk0, sector 0
[   16.322991] Buffer I/O error on device mmcblk0, logical block 0
[   16.327485] mmcblk0: error -84 transferring data
[   16.327489] end_request: I/O error, dev mmcblk0, sector 0
[   16.327494] Buffer I/O error on device mmcblk0, logical block 0
[   16.332034] mmcblk0: error -84 transferring data
[   16.332038] end_request: I/O error, dev mmcblk0, sector 0
[   16.332042] Buffer I/O error on device mmcblk0, logical block 0
[   16.337028] mmcblk0: error -84 transferring data
[   16.337033] end_request: I/O error, dev mmcblk0, sector 0
[   16.337038] Buffer I/O error on device mmcblk0, logical block 0
[   16.337053] ldm_validate_partition_table(): Disk read failed.
[   16.341537] mmcblk0: error -84 transferring data
[   16.341543] end_request: I/O error, dev mmcblk0, sector 0
[   16.341548] Buffer I/O error on device mmcblk0, logical block 0
[   16.343985] acpi device:02: registered as cooling_device9
[   16.345361] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[   16.345833] mmcblk0: error -84 transferring data
[   16.345839] end_request: I/O error, dev mmcblk0, sector 0
[   16.345843] Buffer I/O error on device mmcblk0, logical block 0
[   16.350332] mmcblk0: error -84 transferring data
[   16.350338] end_request: I/O error, dev mmcblk0, sector 0
[   16.350343] Buffer I/O error on device mmcblk0, logical block 0
[   16.354866] mmcblk0: error -84 transferring data
[   16.354872] end_request: I/O error, dev mmcblk0, sector 0
[   16.354877] Buffer I/O error on device mmcblk0, logical block 0
[   16.354891] Dev mmcblk0: unable to read RDB block 0
[   16.359366] mmcblk0: error -84 transferring data
[   16.359371] end_request: I/O error, dev mmcblk0, sector 0
[   16.359377] Buffer I/O error on device mmcblk0, logical block 0
[   16.362899] mmcblk0: error -84 transferring data
[   16.362904] end_request: I/O error, dev mmcblk0, sector 0
[   16.363020] ACPI: Video Device [C09A] (multi-head: yes  rom: no  post: no)
[   16.367569] mmcblk0: error -84 transferring data
[   16.367574] end_request: I/O error, dev mmcblk0, sector 24
[   16.376261] mmcblk0: error -84 transferring data
[   16.376267] end_request: I/O error, dev mmcblk0, sector 24
[   16.380806] mmcblk0: error -84 transferring data
[   16.380811] end_request: I/O error, dev mmcblk0, sector 0
[   16.385358] mmcblk0: error -84 transferring data
[   16.385362] end_request: I/O error, dev mmcblk0, sector 0
[   16.385394]  unable to read partition table
[   16.425147] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   16.426085] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   16.430079] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   16.620910] psmouse serio1: ID: 10 00 64<3>mmcblk0: error -84 transferring data
[   16.625414] end_request: I/O error, dev mmcblk0, sector 0
[   16.625426] end_request: I/O error, dev mmcblk0, sector 8
[   16.625431] end_request: I/O error, dev mmcblk0, sector 16
[   16.625436] end_request: I/O error, dev mmcblk0, sector 24
[   16.628036] mmcblk0: error -84 transferring data
[   16.628040] end_request: I/O error, dev mmcblk0, sector 0
[   16.631555] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.658443] leds-hp-disk driver loaded.
[   16.945366] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   16.945371] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   16.945503] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.945540] iwlagn 0000:10:00.0: setting latency timer to 64
[   16.945667] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   16.984987] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.985085] iwlagn 0000:10:00.0: irq 2300 for MSI/MSI-X
[   16.986690] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.077525] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.080007] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.081063] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.081942] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.083095] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.115080] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input8
[   17.203090] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   17.304654] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.305029] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   17.305033] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   17.305037] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   17.972885] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   17.972901] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.973069] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.089553] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   18.129880] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   18.332046] lp: driver loaded but no devices found
[   18.444315] Adding 2048276k swap on /dev/sda3.  Priority:-1 extents:1 across:2048276k
[   19.000038] Clocksource tsc unstable (delta = -94935116 ns)
[   19.001575] EXT3 FS on sda2, internal journal
[   20.108169] kjournald starting.  Commit interval 5 seconds
[   20.116384] EXT3 FS on sda4, internal journal
[   20.116392] EXT3-fs: mounted filesystem with ordered data mode.
[   21.642338] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   29.291652] RPC: Registered udp transport module.
[   29.291657] RPC: Registered tcp transport module.
[   29.531289] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   29.725256] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   29.747332] NFSD: starting 90-second grace period
[   36.568328] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   36.568333] vboxdrv: Successfully done.
[   36.568336] vboxdrv: Found 2 processor cores.
[   36.568442] vboxdrv: fAsync=0 offMin=0x1b0 offMax=0x76b
[   36.568504] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   36.568508] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   37.693733] mmcblk0: error -84 transferring data
[   37.693741] end_request: I/O error, dev mmcblk0, sector 0
[   37.693747] __ratelimit: 34 callbacks suppressed
[   37.693752] Buffer I/O error on device mmcblk0, logical block 0
[   37.693764] end_request: I/O error, dev mmcblk0, sector 8
[   37.693768] Buffer I/O error on device mmcblk0, logical block 1
[   37.693773] end_request: I/O error, dev mmcblk0, sector 16
[   37.693777] Buffer I/O error on device mmcblk0, logical block 2
[   37.693781] end_request: I/O error, dev mmcblk0, sector 24
[   37.693785] Buffer I/O error on device mmcblk0, logical block 3
[   37.700371] mmcblk0: error -84 transferring data
[   37.700379] end_request: I/O error, dev mmcblk0, sector 0
[   37.700385] Buffer I/O error on device mmcblk0, logical block 0
[   38.048039] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.048043] Bluetooth: BNEP filters: protocol multicast
[   38.110348] Bridge firewalling registered
[   40.202257] ppdev: user-space parallel port driver
[   41.523259] [drm] Initialized drm 1.1.0 20060810
[   41.551475] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   41.551484] pci 0000:00:02.0: setting latency timer to 64
[   41.551712] pci 0000:00:02.0: irq 2299 for MSI/MSI-X
[   41.551840] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   41.557611] [drm:i915_setparam] *ERROR* unknown parameter 4
[   43.516346] e1000e 0000:00:19.0: irq 2301 for MSI/MSI-X
[   43.572130] e1000e 0000:00:19.0: irq 2301 for MSI/MSI-X
[   43.572595] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.574466] iwlagn 0000:10:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   43.903386] Registered led device: iwl-phy0:radio
[   43.903681] Registered led device: iwl-phy0:assoc
[   43.905298] Registered led device: iwl-phy0:RX
[   43.905334] Registered led device: iwl-phy0:TX
[   44.130664] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.424948] wlan0: authenticate with AP 00:23:69:66:dd:66
[   45.426914] wlan0: authenticated
[   45.426920] wlan0: associate with AP 00:23:69:66:dd:66
[   45.430804] wlan0: RX AssocResp from 00:23:69:66:dd:66 (capab=0x401 status=0 aid=1)
[   45.430809] wlan0: associated
[   45.455353] wlan0: disassociating by local choice (reason=3)
[  168.646424] wlan0: authenticate with AP 00:23:69:66:dd:66
[  168.659055] wlan0: authenticate with AP 00:23:69:66:dd:66
[  168.659075] wlan0: authenticated
[  168.659081] wlan0: associate with AP 00:23:69:66:dd:66
[  168.664828] wlan0: RX ReassocResp from 00:23:69:66:dd:66 (capab=0x401 status=0 aid=1)
[  168.664835] wlan0: associated
[  168.688017] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  179.220331] wlan0: no IPv6 routers present
[  225.261049] mmc0: card 8fcf removed
[  246.079093] mmc0: new SDHC card at address 8fcf
[  246.105937] mmcblk0: mmc0:8fcf SD04G 3.69 GiB 
[  246.106024]  mmcblk0:<3>mmcblk0: error -84 transferring data
[  246.110695] end_request: I/O error, dev mmcblk0, sector 0
[  246.110704] Buffer I/O error on device mmcblk0, logical block 0
[  246.115568] mmcblk0: error -84 transferring data
[  246.115576] end_request: I/O error, dev mmcblk0, sector 0
[  246.115582] Buffer I/O error on device mmcblk0, logical block 0
[  246.120428] mmcblk0: error -84 transferring data
[  246.120434] end_request: I/O error, dev mmcblk0, sector 0
[  246.120439] Buffer I/O error on device mmcblk0, logical block 0
[  246.122928] mmc0: Got data interrupt 0x00200000 even though no data operation was in progress.
[  246.122933] sdhci: ============== REGISTER DUMP ==============
[  246.122939] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[  246.122944] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000006
[  246.122950] sdhci: Argument: 0x00000000 | Trn mode: 0x00000032
[  246.122956] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000003
[  246.122961] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[  246.122967] sdhci: Wake-up:  0x00000000 | Clock:    0x00000107
[  246.122972] sdhci: Timeout:  0x00000009 | Int stat: 0x00000003
[  246.122979] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[  246.122984] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[  246.122990] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[  246.122993] sdhci: ===========================================
[  246.125025] mmcblk0: error -84 transferring data
[  246.125031] end_request: I/O error, dev mmcblk0, sector 0
[  246.125038] Buffer I/O error on device mmcblk0, logical block 0
[  246.129567] mmcblk0: error -84 transferring data
[  246.129573] end_request: I/O error, dev mmcblk0, sector 0
[  246.129578] Buffer I/O error on device mmcblk0, logical block 0
[  246.129597] ldm_validate_partition_table(): Disk read failed.
[  246.134257] mmcblk0: error -84 transferring data
[  246.134263] end_request: I/O error, dev mmcblk0, sector 0
[  246.134269] Buffer I/O error on device mmcblk0, logical block 0
[  246.138815] mmcblk0: error -84 transferring data
[  246.138821] end_request: I/O error, dev mmcblk0, sector 0
[  246.138826] Buffer I/O error on device mmcblk0, logical block 0
[  246.143366] mmcblk0: error -84 transferring data
[  246.143372] end_request: I/O error, dev mmcblk0, sector 0
[  246.143378] Buffer I/O error on device mmcblk0, logical block 0
[  246.147920] mmcblk0: error -84 transferring data
[  246.147927] end_request: I/O error, dev mmcblk0, sector 0
[  246.147932] Buffer I/O error on device mmcblk0, logical block 0
[  246.147952] Dev mmcblk0: unable to read RDB block 0
[  246.150406] mmc0: Got data interrupt 0x00200000 even though no data operation was in progress.
[  246.150411] sdhci: ============== REGISTER DUMP ==============
[  246.150417] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[  246.150423] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000006
[  246.150428] sdhci: Argument: 0x00000000 | Trn mode: 0x00000032
[  246.150434] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000003
[  246.150440] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[  246.150445] sdhci: Wake-up:  0x00000000 | Clock:    0x00000107
[  246.150451] sdhci: Timeout:  0x00000009 | Int stat: 0x00000003
[  246.150456] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[  246.150462] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[  246.150467] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[  246.150471] sdhci: ===========================================
[  246.152500] mmcblk0: error -84 transferring data
[  246.152506] end_request: I/O error, dev mmcblk0, sector 0
[  246.152513] Buffer I/O error on device mmcblk0, logical block 0
[  246.156982] mmcblk0: error -84 transferring data
[  246.156988] end_request: I/O error, dev mmcblk0, sector 0
[  246.161477] mmcblk0: error -84 transferring data
[  246.161484] end_request: I/O error, dev mmcblk0, sector 24
[  246.165954] mmcblk0: error -84 transferring data
[  246.165960] end_request: I/O error, dev mmcblk0, sector 24
[  246.170450] mmcblk0: error -84 transferring data
[  246.170456] end_request: I/O error, dev mmcblk0, sector 0
[  246.172940] mmcblk0: error -84 transferring data
[  246.172945] end_request: I/O error, dev mmcblk0, sector 0
[  246.172960]  unable to read partition table
[  246.194697] mmcblk0: error -84 transferring data
[  246.194705] end_request: I/O error, dev mmcblk0, sector 0
[  246.194719] end_request: I/O error, dev mmcblk0, sector 8
[  246.194724] end_request: I/O error, dev mmcblk0, sector 16
[  246.194729] end_request: I/O error, dev mmcblk0, sector 24
[  246.197202] mmc0: Got data interrupt 0x00200000 even though no data operation was in progress.
[  246.197208] sdhci: ============== REGISTER DUMP ==============
[  246.197214] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[  246.197220] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000006
[  246.197225] sdhci: Argument: 0x00000000 | Trn mode: 0x00000032
[  246.197231] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000003
[  246.197237] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[  246.197243] sdhci: Wake-up:  0x00000000 | Clock:    0x00000107
[  246.197248] sdhci: Timeout:  0x00000009 | Int stat: 0x00000003
[  246.197254] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[  246.197260] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[  246.197266] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[  246.197269] sdhci: ===========================================
[  246.199286] mmcblk0: error -84 transferring data
[  246.199293] end_request: I/O error, dev mmcblk0, sector 0
[  246.217510] mmcblk0: error -84 transferring data
[  246.217519] end_request: I/O error, dev mmcblk0, sector 0
[  246.217531] end_request: I/O error, dev mmcblk0, sector 8
[  246.217536] end_request: I/O error, dev mmcblk0, sector 16
[  246.217541] end_request: I/O error, dev mmcblk0, sector 24
[  246.222326] mmcblk0: error -84 transferring data
[  246.222334] end_request: I/O error, dev mmcblk0, sector 0
[  280.137443] mmc0: card 8fcf removed
[  903.424187] mmc0: new SDHC card at address 8fcf
[  903.424818] mmcblk0: mmc0:8fcf SD04G 3.69 GiB 
[  903.424910]  mmcblk0:<3>mmcblk0: error -84 transferring data
[  903.429463] end_request: I/O error, dev mmcblk0, sector 0
[  903.429473] __ratelimit: 15 callbacks suppressed
[  903.429479] Buffer I/O error on device mmcblk0, logical block 0
[  903.434321] mmcblk0: error -84 transferring data
[  903.434328] end_request: I/O error, dev mmcblk0, sector 0
[  903.434335] Buffer I/O error on device mmcblk0, logical block 0
[  903.440585] mmcblk0: error -84 transferring data
[  903.440595] end_request: I/O error, dev mmcblk0, sector 0
[  903.440604] Buffer I/O error on device mmcblk0, logical block 0
[  903.445216] mmcblk0: error -84 transferring data
[  903.445224] end_request: I/O error, dev mmcblk0, sector 0
[  903.445231] Buffer I/O error on device mmcblk0, logical block 0
[  903.450977] mmcblk0: error -84 transferring data
[  903.450986] end_request: I/O error, dev mmcblk0, sector 0
[  903.450995] Buffer I/O error on device mmcblk0, logical block 0
[  903.451023] ldm_validate_partition_table(): Disk read failed.
[  903.455526] mmcblk0: error -84 transferring data
[  903.455534] end_request: I/O error, dev mmcblk0, sector 0
[  903.455541] Buffer I/O error on device mmcblk0, logical block 0
[  903.459091] mmcblk0: error -84 transferring data
[  903.459099] end_request: I/O error, dev mmcblk0, sector 0
[  903.459106] Buffer I/O error on device mmcblk0, logical block 0
[  903.464606] mmcblk0: error -84 transferring data
[  903.464613] end_request: I/O error, dev mmcblk0, sector 0
[  903.464620] Buffer I/O error on device mmcblk0, logical block 0
[  903.469153] mmcblk0: error -84 transferring data
[  903.469161] end_request: I/O error, dev mmcblk0, sector 0
[  903.469167] Buffer I/O error on device mmcblk0, logical block 0
[  903.469187] Dev mmcblk0: unable to read RDB block 0
[  903.474975] mmcblk0: error -84 transferring data
[  903.474982] end_request: I/O error, dev mmcblk0, sector 0
[  903.474989] Buffer I/O error on device mmcblk0, logical block 0
[  903.479489] mmcblk0: error -84 transferring data
[  903.479495] end_request: I/O error, dev mmcblk0, sector 0
[  903.483994] mmcblk0: error -84 transferring data
[  903.484001] end_request: I/O error, dev mmcblk0, sector 24
[  903.488508] mmcblk0: error -84 transferring data
[  903.488516] end_request: I/O error, dev mmcblk0, sector 24
[  903.492779] mmcblk0: error -84 transferring data
[  903.492787] end_request: I/O error, dev mmcblk0, sector 0
[  903.499717] mmcblk0: error -84 transferring data
[  903.499728] end_request: I/O error, dev mmcblk0, sector 0
[  903.499763]  unable to read partition table
[  903.515116] mmcblk0: error -84 transferring data
[  903.515127] end_request: I/O error, dev mmcblk0, sector 0
[  903.515140] end_request: I/O error, dev mmcblk0, sector 8
[  903.515147] end_request: I/O error, dev mmcblk0, sector 16
[  903.515153] end_request: I/O error, dev mmcblk0, sector 24
[  903.519681] mmcblk0: error -84 transferring data
[  903.519689] end_request: I/O error, dev mmcblk0, sector 0
[  903.532441] mmcblk0: error -84 transferring data
[  903.532451] end_request: I/O error, dev mmcblk0, sector 0
[  903.532465] end_request: I/O error, dev mmcblk0, sector 8
[  903.532472] end_request: I/O error, dev mmcblk0, sector 16
[  903.532479] end_request: I/O error, dev mmcblk0, sector 24
[  903.537039] mmcblk0: error -84 transferring data
[  903.537045] end_request: I/O error, dev mmcblk0, sector 0
[  915.160102] mmc0: card 8fcf removed
[  915.593188] mmc0: new SDHC card at address 8fcf
[  915.594203] mmcblk0: mmc0:8fcf SD04G 3.69 GiB 
[  915.594301]  mmcblk0:<3>mmcblk0: error -84 transferring data
[  915.598836] end_request: I/O error, dev mmcblk0, sector 0
[  915.598846] __ratelimit: 15 callbacks suppressed
[  915.598852] Buffer I/O error on device mmcblk0, logical block 0
[  915.603357] mmcblk0: error -84 transferring data
[  915.603364] end_request: I/O error, dev mmcblk0, sector 0
[  915.603373] Buffer I/O error on device mmcblk0, logical block 0
[  915.607880] mmcblk0: error -84 transferring data
[  915.607887] end_request: I/O error, dev mmcblk0, sector 0
[  915.607894] Buffer I/O error on device mmcblk0, logical block 0
[  915.618868] mmcblk0: error -84 transferring data
[  915.618879] end_request: I/O error, dev mmcblk0, sector 0
[  915.618889] Buffer I/O error on device mmcblk0, logical block 0
[  915.629074] mmcblk0: error -84 transferring data
[  915.629086] end_request: I/O error, dev mmcblk0, sector 0
[  915.629096] Buffer I/O error on device mmcblk0, logical block 0
[  915.629139] ldm_validate_partition_table(): Disk read failed.
[  915.635118] mmcblk0: error -84 transferring data
[  915.635127] end_request: I/O error, dev mmcblk0, sector 0
[  915.635135] Buffer I/O error on device mmcblk0, logical block 0
[  915.638402] mmcblk0: error -84 transferring data
[  915.638410] end_request: I/O error, dev mmcblk0, sector 0
[  915.638417] Buffer I/O error on device mmcblk0, logical block 0
[  915.643521] mmcblk0: error -84 transferring data
[  915.643529] end_request: I/O error, dev mmcblk0, sector 0
[  915.643536] Buffer I/O error on device mmcblk0, logical block 0
[  915.650184] mmcblk0: error -84 transferring data
[  915.650191] end_request: I/O error, dev mmcblk0, sector 0
[  915.650198] Buffer I/O error on device mmcblk0, logical block 0
[  915.650322] Dev mmcblk0: unable to read RDB block 0
[  915.655217] mmcblk0: error -84 transferring data
[  915.655224] end_request: I/O error, dev mmcblk0, sector 0
[  915.655232] Buffer I/O error on device mmcblk0, logical block 0
[  915.659788] mmcblk0: error -84 transferring data
[  915.659795] end_request: I/O error, dev mmcblk0, sector 0
[  915.664511] mmcblk0: error -84 transferring data
[  915.664511] end_request: I/O error, dev mmcblk0, sector 24
[  915.669068] mmcblk0: error -84 transferring data
[  915.669076] end_request: I/O error, dev mmcblk0, sector 24
[  915.673611] mmcblk0: error -84 transferring data
[  915.673617] end_request: I/O error, dev mmcblk0, sector 0
[  915.678494] mmcblk0: error -84 transferring data
[  915.678501] end_request: I/O error, dev mmcblk0, sector 0
[  915.678551]  unable to read partition table
[  915.701382] mmcblk0: error -84 transferring data
[  915.701392] end_request: I/O error, dev mmcblk0, sector 0
[  915.701406] end_request: I/O error, dev mmcblk0, sector 8
[  915.701413] end_request: I/O error, dev mmcblk0, sector 16
[  915.701420] end_request: I/O error, dev mmcblk0, sector 24
[  915.705929] mmcblk0: error -84 transferring data
[  915.705935] end_request: I/O error, dev mmcblk0, sector 0
[  915.719792] mmcblk0: error -84 transferring data
[  915.719803] end_request: I/O error, dev mmcblk0, sector 0
[  915.719818] end_request: I/O error, dev mmcblk0, sector 8
[  915.719826] end_request: I/O error, dev mmcblk0, sector 16
[  915.719833] end_request: I/O error, dev mmcblk0, sector 24
[  915.724342] mmcblk0: error -84 transferring data
[  915.724351] end_request: I/O error, dev mmcblk0, sector 0


Any clues? eep!

---

### Post by infinitelink on 2009-10-18
More info / another question: SDs supposed to be mounting under /dev/mmcblk0 as it is? I have a regular SD which is also mounting there, which usually works, but now isn't (though I haven't tested either in a while), and this one (the SDHC) is new, and yes, the hardware supports it. 

What's going on???

---

### Post by infinitelink on 2009-10-18
More info:

Taking it in/out a bunch would change the results of dmesg, (eventually); this, however, is much more interesting (a different message than was being outputted); at one point (just for the info, don't know that it matters), I did try to reformat the SDHC using mkfs.ntfs by the way. Anway,

> [ 1539.799473] end_request: I/O error, dev mmcblk0, sector 2103503
[ 1539.799488] end_request: I/O error, dev mmcblk0, sector 2103504
[ 1539.799500] end_request: I/O error, dev mmcblk0, sector 2103505
[ 1539.799513] end_request: I/O error, dev mmcblk0, sector 2103506
[ 1539.799526] end_request: I/O error, dev mmcblk0, sector 2103507
[ 1539.799539] end_request: I/O error, dev mmcblk0, sector 2103508
[ 1539.799552] end_request: I/O error, dev mmcblk0, sector 2103509
[ 1539.799564] end_request: I/O error, dev mmcblk0, sector 2103510
[ 1539.799577] end_request: I/O error, dev mmcblk0, sector 2103511
[ 1539.799590] end_request: I/O error, dev mmcblk0, sector 2103512
[ 1539.799602] end_request: I/O error, dev mmcblk0, sector 2103513
[ 1539.799615] end_request: I/O error, dev mmcblk0, sector 2103514
[ 1539.799628] end_request: I/O error, dev mmcblk0, sector 2103515
[ 1539.799640] end_request: I/O error, dev mmcblk0, sector 2103516
[ 1539.799652] end_request: I/O error, dev mmcblk0, sector 2103517
[ 1539.799665] end_request: I/O error, dev mmcblk0, sector 2103518
[ 1539.799678] end_request: I/O error, dev mmcblk0, sector 2103519
[ 1539.799691] end_request: I/O error, dev mmcblk0, sector 2103520
[ 1539.799702] end_request: I/O error, dev mmcblk0, sector 2103521
[ 1539.799714] end_request: I/O error, dev mmcblk0, sector 2103522
[ 1539.799726] end_request: I/O error, dev mmcblk0, sector 2103523
[ 1539.799739] end_request: I/O error, dev mmcblk0, sector 2103524
[ 1539.799750] end_request: I/O error, dev mmcblk0, sector 2103525
[ 1539.799763] end_request: I/O error, dev mmcblk0, sector 2103526
[ 1539.799775] end_request: I/O error, dev mmcblk0, sector 2103527
[ 1539.799788] end_request: I/O error, dev mmcblk0, sector 2103528
[ 1539.799800] end_request: I/O error, dev mmcblk0, sector 2103529
[ 1539.799812] end_request: I/O error, dev mmcblk0, sector 2103530
[ 1539.799824] end_request: I/O error, dev mmcblk0, sector 2103531
[ 1539.799836] end_request: I/O error, dev mmcblk0, sector 2103532
[ 1539.799848] end_request: I/O error, dev mmcblk0, sector 2103533
[ 1539.799860] end_request: I/O error, dev mmcblk0, sector 2103534
[ 1539.799871] end_request: I/O error, dev mmcblk0, sector 2103535
[ 1539.799884] end_request: I/O error, dev mmcblk0, sector 2103536
[ 1539.799896] end_request: I/O error, dev mmcblk0, sector 2103537
[ 1539.799907] end_request: I/O error, dev mmcblk0, sector 2103538
[ 1539.799919] end_request: I/O error, dev mmcblk0, sector 2103539
[ 1539.799931] end_request: I/O error, dev mmcblk0, sector 2103540
[ 1539.799942] end_request: I/O error, dev mmcblk0, sector 2103541
[ 1539.799953] end_request: I/O error, dev mmcblk0, sector 2103542
[ 1539.799965] end_request: I/O error, dev mmcblk0, sector 2103543
[ 1539.799977] end_request: I/O error, dev mmcblk0, sector 2103544
[ 1539.799988] end_request: I/O error, dev mmcblk0, sector 2103545
[ 1539.799999] end_request: I/O error, dev mmcblk0, sector 2103546
[ 1539.800008] end_request: I/O error, dev mmcblk0, sector 2103547
[ 1539.800017] end_request: I/O error, dev mmcblk0, sector 2103548
[ 1539.800028] end_request: I/O error, dev mmcblk0, sector 2103549
[ 1539.800040] end_request: I/O error, dev mmcblk0, sector 2103550
[ 1539.800051] end_request: I/O error, dev mmcblk0, sector 2103551
[ 1539.800063] end_request: I/O error, dev mmcblk0, sector 2103552
[ 1539.800075] end_request: I/O error, dev mmcblk0, sector 2103553
[ 1539.800085] end_request: I/O error, dev mmcblk0, sector 2103554
[ 1539.800096] end_request: I/O error, dev mmcblk0, sector 2103555
[ 1539.800106] end_request: I/O error, dev mmcblk0, sector 2103556
[ 1539.800116] end_request: I/O error, dev mmcblk0, sector 2103557
[ 1539.800127] end_request: I/O error, dev mmcblk0, sector 2103558
[ 1539.800137] end_request: I/O error, dev mmcblk0, sector 2103559
[ 1539.800148] end_request: I/O error, dev mmcblk0, sector 2103560
[ 1539.800159] end_request: I/O error, dev mmcblk0, sector 2103561
[ 1539.800170] end_request: I/O error, dev mmcblk0, sector 2103562
[ 1539.800180] end_request: I/O error, dev mmcblk0, sector 2103563
[ 1539.800190] end_request: I/O error, dev mmcblk0, sector 2103564
[ 1539.800200] end_request: I/O error, dev mmcblk0, sector 2103565
[ 1539.800210] end_request: I/O error, dev mmcblk0, sector 2103566
[ 1539.800220] end_request: I/O error, dev mmcblk0, sector 2103567
[ 1539.800231] end_request: I/O error, dev mmcblk0, sector 2103568
[ 1539.800241] end_request: I/O error, dev mmcblk0, sector 2103569
[ 1539.800250] end_request: I/O error, dev mmcblk0, sector 2103570
[ 1539.800259] end_request: I/O error, dev mmcblk0, sector 2103571
[ 1539.800269] end_request: I/O error, dev mmcblk0, sector 2103572
[ 1539.800278] end_request: I/O error, dev mmcblk0, sector 2103573
[ 1539.800287] end_request: I/O error, dev mmcblk0, sector 2103574
[ 1539.800296] end_request: I/O error, dev mmcblk0, sector 2103575
[ 1539.800306] end_request: I/O error, dev mmcblk0, sector 2103576
[ 1539.800316] end_request: I/O error, dev mmcblk0, sector 2103577
[ 1539.800325] end_request: I/O error, dev mmcblk0, sector 2103578
[ 1539.800334] end_request: I/O error, dev mmcblk0, sector 2103579
[ 1539.800343] end_request: I/O error, dev mmcblk0, sector 2103580
[ 1539.800352] end_request: I/O error, dev mmcblk0, sector 2103581
[ 1539.800361] end_request: I/O error, dev mmcblk0, sector 2103582
[ 1539.800371] end_request: I/O error, dev mmcblk0, sector 2103583
[ 1539.800382] end_request: I/O error, dev mmcblk0, sector 2103584
[ 1539.800391] end_request: I/O error, dev mmcblk0, sector 2103585
[ 1539.800401] end_request: I/O error, dev mmcblk0, sector 2103586
[ 1539.800410] end_request: I/O error, dev mmcblk0, sector 2103587
[ 1539.800419] end_request: I/O error, dev mmcblk0, sector 2103588
[ 1539.800428] end_request: I/O error, dev mmcblk0, sector 2103589
[ 1539.800437] end_request: I/O error, dev mmcblk0, sector 2103590
[ 1539.800447] end_request: I/O error, dev mmcblk0, sector 2103591
[ 1539.800457] end_request: I/O error, dev mmcblk0, sector 2103592
[ 1539.800466] end_request: I/O error, dev mmcblk0, sector 2103593
[ 1539.800475] end_request: I/O error, dev mmcblk0, sector 2103594
[ 1539.800484] end_request: I/O error, dev mmcblk0, sector 2103595
[ 1539.800493] end_request: I/O error, dev mmcblk0, sector 2103596
[ 1539.800502] end_request: I/O error, dev mmcblk0, sector 2103597
[ 1539.800511] end_request: I/O error, dev mmcblk0, sector 2103598
[ 1539.800520] end_request: I/O error, dev mmcblk0, sector 2103599
[ 1539.800529] end_request: I/O error, dev mmcblk0, sector 2103600
[ 1539.800538] end_request: I/O error, dev mmcblk0, sector 2103601
[ 1539.800547] end_request: I/O error, dev mmcblk0, sector 2103602
[ 1539.800555] end_request: I/O error, dev mmcblk0, sector 2103603
[ 1539.800564] end_request: I/O error, dev mmcblk0, sector 2103604
[ 1539.800572] end_request: I/O error, dev mmcblk0, sector 2103605
[ 1539.800581] end_request: I/O error, dev mmcblk0, sector 2103606
[ 1539.800590] end_request: I/O error, dev mmcblk0, sector 2103607
[ 1549.797019] mmc0: Timeout waiting for hardware interrupt.
[ 1549.797030] sdhci: ============== REGISTER DUMP ==============
[ 1549.797038] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1549.797046] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1549.797053] sdhci: Argument: 0x00201938 | Trn mode: 0x00000022
[ 1549.797060] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1549.797067] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1549.797075] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1549.797082] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1549.797089] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1549.797096] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1549.797103] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1549.797107] sdhci: ===========================================
[ 1549.799129] ------------[ cut here ]------------
[ 1549.799134] WARNING: at /build/buildd/linux-2.6.28/drivers/mmc/host/sdhci.c:786 sdhci_send_command+0x1e8/0x220 [sdhci]()
[ 1549.799140] Modules linked in: ipt_MASQUERADE xt_DSCP binfmt_misc i915 drm ppdev bridge stp bnep vboxnetflt vboxdrv nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_conntrack_ftp lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi iptable_nat snd_rawmidi arc4 nf_nat mmc_block ecb snd_seq_midi_event nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 pcmcia snd_seq snd_timer iptable_mangle iwlagn snd_seq_device iwlcore iptable_filter leds_hp_disk ip_tables snd led_class mac80211 yenta_socket rsrc_nonstatic x_tables soundcore joydev psmouse pcmcia_core ricoh_mmc video sdhci_pci sdhci iTCO_wdt iTCO_vendor_support intel_agp agpgart snd_page_alloc cfg80211 lis3lv02d pcspkr serio_raw output tpm_infineon tpm tpm_bios ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 1549.799312] Pid: 5592, comm: firefox Tainted: G        W  2.6.28-11-generic #42-Ubuntu
[ 1549.799317] Call Trace:
[ 1549.799332]  [<c0500ac6>] ? printk+0x18/0x1a
[ 1549.799341]  [<c0139b24>] warn_on_slowpath+0x54/0x80
[ 1549.799365]  [<f7d3dbc8>] sdhci_send_command+0x1e8/0x220 [sdhci]
[ 1549.799381]  [<f7d3dd72>] sdhci_finish_data+0xa2/0xe0 [sdhci]
[ 1549.799395]  [<f7d3c275>] ? sdhci_dumpregs+0x1b5/0x1c0 [sdhci]
[ 1549.799414]  [<f7d3dede>] sdhci_timeout_timer+0x6e/0xa0 [sdhci]
[ 1549.799427]  [<c0143b00>] run_timer_softirq+0x130/0x200
[ 1549.799442]  [<f7d3de70>] ? sdhci_timeout_timer+0x0/0xa0 [sdhci]
[ 1549.799456]  [<f7d3de70>] ? sdhci_timeout_timer+0x0/0xa0 [sdhci]
[ 1549.799465]  [<c013f197>] __do_softirq+0x97/0x170
[ 1549.799473]  [<c0152ca6>] ? hrtimer_interrupt+0x186/0x1b0
[ 1549.799481]  [<c017eab9>] ? handle_IRQ_event+0x39/0x70
[ 1549.799489]  [<c013f2cd>] do_softirq+0x5d/0x60
[ 1549.799497]  [<c013f445>] irq_exit+0x55/0x90
[ 1549.799505]  [<c011a07b>] smp_apic_timer_interrupt+0x5b/0x90
[ 1549.799512]  [<c0105318>] apic_timer_interrupt+0x28/0x30
[ 1549.799518] ---[ end trace 29731e0c7fe974a3 ]---
[ 1549.801562] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1549.801568] sdhci: ============== REGISTER DUMP ==============
[ 1549.801577] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1549.801584] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1549.801591] sdhci: Argument: 0x00000000 | Trn mode: 0x00000022
[ 1549.801599] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1549.801608] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1549.801615] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1549.801622] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1549.801629] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1549.801636] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1549.801643] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1549.801649] sdhci: ===========================================
[ 1549.801730] mmcblk0: error -110 transferring data
[ 1549.801737] mmcblk0: error -110 sending stop command
[ 1559.801068] mmc0: Timeout waiting for hardware interrupt.
[ 1559.801077] sdhci: ============== REGISTER DUMP ==============
[ 1559.801085] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1559.801093] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1559.801100] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1559.801107] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1559.801114] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1559.801122] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1559.801129] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1559.801136] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1559.801143] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1559.801151] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1559.801155] sdhci: ===========================================
[ 1559.803160] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1559.803167] sdhci: ============== REGISTER DUMP ==============
[ 1559.803174] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1559.803181] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1559.803189] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1559.803195] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1559.803203] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1559.803210] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1559.803217] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1559.803225] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1559.803232] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1559.803239] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1559.803244] sdhci: ===========================================
[ 1569.800187] mmc0: Timeout waiting for hardware interrupt.
[ 1569.800197] sdhci: ============== REGISTER DUMP ==============
[ 1569.800207] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1569.800215] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1569.800222] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1569.800229] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1569.800237] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1569.800244] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1569.800251] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1569.800258] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1569.800265] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1569.800273] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1569.800277] sdhci: ===========================================
[ 1569.802283] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1569.802294] sdhci: ============== REGISTER DUMP ==============
[ 1569.802302] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1569.802309] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1569.802316] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1569.802323] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1569.802330] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1569.802338] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1569.802344] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1569.802352] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1569.802359] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1569.802365] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1569.802370] sdhci: ===========================================
[ 1579.800068] mmc0: Timeout waiting for hardware interrupt.
[ 1579.800078] sdhci: ============== REGISTER DUMP ==============
[ 1579.800085] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1579.800092] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1579.800100] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1579.800107] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1579.800114] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1579.800122] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1579.800129] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1579.800136] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1579.800144] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1579.800151] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1579.800155] sdhci: ===========================================
[ 1579.802157] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1579.802164] sdhci: ============== REGISTER DUMP ==============
[ 1579.802172] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1579.802179] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1579.802186] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1579.802193] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1579.802200] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1579.802207] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1579.802214] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1579.802221] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1579.802228] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1579.802235] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1579.802239] sdhci: ===========================================
[ 1589.800071] mmc0: Timeout waiting for hardware interrupt.
[ 1589.800082] sdhci: ============== REGISTER DUMP ==============
[ 1589.800090] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1589.800097] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1589.800105] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1589.800112] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1589.800119] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1589.800126] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1589.800133] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1589.800140] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1589.800147] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1589.800155] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1589.800159] sdhci: ===========================================
[ 1589.802161] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1589.802169] sdhci: ============== REGISTER DUMP ==============
[ 1589.802176] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1589.802183] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1589.802190] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1589.802198] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1589.802204] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1589.802211] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1589.802218] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1589.802225] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1589.802232] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1589.802239] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1589.802244] sdhci: ===========================================
[ 1599.800913] mmc0: Timeout waiting for hardware interrupt.
[ 1599.800923] sdhci: ============== REGISTER DUMP ==============
[ 1599.800931] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1599.800938] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1599.800946] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1599.800953] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1599.800960] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1599.800967] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1599.800974] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1599.800981] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1599.800988] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1599.800996] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1599.801000] sdhci: ===========================================
[ 1599.803028] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1599.803036] sdhci: ============== REGISTER DUMP ==============
[ 1599.803043] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1599.803050] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1599.803058] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1599.803065] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1599.803072] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1599.803079] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1599.803086] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1599.803094] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1599.803101] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1599.803108] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1599.803113] sdhci: ===========================================
[ 1609.801066] mmc0: Timeout waiting for hardware interrupt.
[ 1609.801076] sdhci: ============== REGISTER DUMP ==============
[ 1609.801083] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1609.801090] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1609.801098] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1609.801105] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1609.801112] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1609.801119] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1609.801126] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1609.801133] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1609.801140] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1609.801147] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1609.801152] sdhci: ===========================================
[ 1609.803153] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1609.803162] mmcblk0: error -110 requesting status
[ 1609.803167] sdhci: ============== REGISTER DUMP ==============
[ 1609.803176] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1609.803184] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1609.803191] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1609.803198] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1609.803205] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1609.803212] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1609.803219] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1609.803226] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1609.803233] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1609.803240] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1609.803244] sdhci: ===========================================
[ 1619.800068] mmc0: Timeout waiting for hardware interrupt.
[ 1619.800078] sdhci: ============== REGISTER DUMP ==============
[ 1619.800086] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1619.800093] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1619.800100] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1619.800107] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1619.800115] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1619.800122] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1619.800129] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1619.800136] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1619.800144] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1619.800151] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1619.800155] sdhci: ===========================================
[ 1619.802156] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1619.802164] sdhci: ============== REGISTER DUMP ==============
[ 1619.802171] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1619.802178] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1619.802186] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1619.802193] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1619.802201] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1619.802209] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1619.802217] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1619.802224] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1619.802231] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1619.802238] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1619.802243] sdhci: ===========================================
[ 1619.802377] end_request: I/O error, dev mmcblk0, sector 2103608
[ 1619.802388] __ratelimit: 118 callbacks suppressed
[ 1619.802394] Buffer I/O error on device mmcblk0, logical block 2103608
[ 1619.802400] lost page write due to I/O error on mmcblk0
[ 1619.802426] end_request: I/O error, dev mmcblk0, sector 2103609
[ 1619.802432] Buffer I/O error on device mmcblk0, logical block 2103609
[ 1619.802437] lost page write due to I/O error on mmcblk0
[ 1619.802448] end_request: I/O error, dev mmcblk0, sector 2103610
[ 1619.802454] Buffer I/O error on device mmcblk0, logical block 2103610
[ 1619.802459] lost page write due to I/O error on mmcblk0
[ 1619.802471] end_request: I/O error, dev mmcblk0, sector 2103611
[ 1619.802477] Buffer I/O error on device mmcblk0, logical block 2103611
[ 1619.802481] lost page write due to I/O error on mmcblk0
[ 1619.802492] end_request: I/O error, dev mmcblk0, sector 2103612
[ 1619.802498] Buffer I/O error on device mmcblk0, logical block 2103612
[ 1619.802503] lost page write due to I/O error on mmcblk0
[ 1619.802514] end_request: I/O error, dev mmcblk0, sector 2103613
[ 1619.802520] Buffer I/O error on device mmcblk0, logical block 2103613
[ 1619.802525] lost page write due to I/O error on mmcblk0
[ 1619.802536] end_request: I/O error, dev mmcblk0, sector 2103614
[ 1619.802542] Buffer I/O error on device mmcblk0, logical block 2103614
[ 1619.802547] lost page write due to I/O error on mmcblk0
[ 1619.802558] end_request: I/O error, dev mmcblk0, sector 2103615
[ 1619.802563] Buffer I/O error on device mmcblk0, logical block 2103615
[ 1619.802569] lost page write due to I/O error on mmcblk0
[ 1619.802586] end_request: I/O error, dev mmcblk0, sector 2103616
[ 1619.802591] Buffer I/O error on device mmcblk0, logical block 2103616
[ 1619.802596] lost page write due to I/O error on mmcblk0
[ 1619.802608] end_request: I/O error, dev mmcblk0, sector 2103617
[ 1619.802614] Buffer I/O error on device mmcblk0, logical block 2103617
[ 1619.802619] lost page write due to I/O error on mmcblk0
[ 1619.802630] end_request: I/O error, dev mmcblk0, sector 2103618
[ 1619.802641] end_request: I/O error, dev mmcblk0, sector 2103619
[ 1619.802653] end_request: I/O error, dev mmcblk0, sector 2103620
[ 1619.802664] end_request: I/O error, dev mmcblk0, sector 2103621
[ 1619.802675] end_request: I/O error, dev mmcblk0, sector 2103622
[ 1619.802687] end_request: I/O error, dev mmcblk0, sector 2103623
[ 1619.802700] end_request: I/O error, dev mmcblk0, sector 2103624
[ 1619.802711] end_request: I/O error, dev mmcblk0, sector 2103625
[ 1619.802723] end_request: I/O error, dev mmcblk0, sector 2103626
[ 1619.802733] end_request: I/O error, dev mmcblk0, sector 2103627
[ 1619.802745] end_request: I/O error, dev mmcblk0, sector 2103628
[ 1619.802756] end_request: I/O error, dev mmcblk0, sector 2103629
[ 1619.802767] end_request: I/O error, dev mmcblk0, sector 2103630
[ 1619.802778] end_request: I/O error, dev mmcblk0, sector 2103631
[ 1619.802790] end_request: I/O error, dev mmcblk0, sector 2103632
[ 1619.802801] end_request: I/O error, dev mmcblk0, sector 2103633
[ 1619.802811] end_request: I/O error, dev mmcblk0, sector 2103634
[ 1619.802822] end_request: I/O error, dev mmcblk0, sector 2103635
[ 1619.802834] end_request: I/O error, dev mmcblk0, sector 2103636
[ 1619.802845] end_request: I/O error, dev mmcblk0, sector 2103637
[ 1619.802855] end_request: I/O error, dev mmcblk0, sector 2103638
[ 1619.802866] end_request: I/O error, dev mmcblk0, sector 2103639
[ 1619.802877] end_request: I/O error, dev mmcblk0, sector 2103640
[ 1619.802888] end_request: I/O error, dev mmcblk0, sector 2103641
[ 1619.802898] end_request: I/O error, dev mmcblk0, sector 2103642
[ 1619.802909] end_request: I/O error, dev mmcblk0, sector 2103643
[ 1619.802919] end_request: I/O error, dev mmcblk0, sector 2103644
[ 1619.802929] end_request: I/O error, dev mmcblk0, sector 2103645
[ 1619.802939] end_request: I/O error, dev mmcblk0, sector 2103646
[ 1619.802951] end_request: I/O error, dev mmcblk0, sector 2103647
[ 1619.802963] end_request: I/O error, dev mmcblk0, sector 2103648
[ 1619.802973] end_request: I/O error, dev mmcblk0, sector 2103649
[ 1619.802983] end_request: I/O error, dev mmcblk0, sector 2103650
[ 1619.802994] end_request: I/O error, dev mmcblk0, sector 2103651
[ 1619.803004] end_request: I/O error, dev mmcblk0, sector 2103652
[ 1619.803014] end_request: I/O error, dev mmcblk0, sector 2103653
[ 1619.803025] end_request: I/O error, dev mmcblk0, sector 2103654
[ 1619.803034] end_request: I/O error, dev mmcblk0, sector 2103655
[ 1619.803045] end_request: I/O error, dev mmcblk0, sector 2103656
[ 1619.803055] end_request: I/O error, dev mmcblk0, sector 2103657
[ 1619.803066] end_request: I/O error, dev mmcblk0, sector 2103658
[ 1619.803075] end_request: I/O error, dev mmcblk0, sector 2103659
[ 1619.803085] end_request: I/O error, dev mmcblk0, sector 2103660
[ 1619.803094] end_request: I/O error, dev mmcblk0, sector 2103661
[ 1619.803104] end_request: I/O error, dev mmcblk0, sector 2103662
[ 1619.803114] end_request: I/O error, dev mmcblk0, sector 2103663
[ 1619.803124] end_request: I/O error, dev mmcblk0, sector 2103664
[ 1619.803133] end_request: I/O error, dev mmcblk0, sector 2103665
[ 1619.803142] end_request: I/O error, dev mmcblk0, sector 2103666
[ 1619.803152] end_request: I/O error, dev mmcblk0, sector 2103667
[ 1619.803161] end_request: I/O error, dev mmcblk0, sector 2103668
[ 1619.803170] end_request: I/O error, dev mmcblk0, sector 2103669
[ 1619.803179] end_request: I/O error, dev mmcblk0, sector 2103670
[ 1619.803188] end_request: I/O error, dev mmcblk0, sector 2103671
[ 1619.803198] end_request: I/O error, dev mmcblk0, sector 2103672
[ 1619.803207] end_request: I/O error, dev mmcblk0, sector 2103673
[ 1619.803217] end_request: I/O error, dev mmcblk0, sector 2103674
[ 1619.803225] end_request: I/O error, dev mmcblk0, sector 2103675
[ 1619.803234] end_request: I/O error, dev mmcblk0, sector 2103676
[ 1619.803243] end_request: I/O error, dev mmcblk0, sector 2103677
[ 1619.803252] end_request: I/O error, dev mmcblk0, sector 2103678
[ 1619.803261] end_request: I/O error, dev mmcblk0, sector 2103679
[ 1619.803271] end_request: I/O error, dev mmcblk0, sector 2103680
[ 1619.803280] end_request: I/O error, dev mmcblk0, sector 2103681
[ 1619.803289] end_request: I/O error, dev mmcblk0, sector 2103682
[ 1619.803298] end_request: I/O error, dev mmcblk0, sector 2103683
[ 1619.803306] end_request: I/O error, dev mmcblk0, sector 2103684
[ 1619.803315] end_request: I/O error, dev mmcblk0, sector 2103685
[ 1619.803323] end_request: I/O error, dev mmcblk0, sector 2103686
[ 1619.803332] end_request: I/O error, dev mmcblk0, sector 2103687
[ 1619.803341] end_request: I/O error, dev mmcblk0, sector 2103688
[ 1619.803350] end_request: I/O error, dev mmcblk0, sector 2103689
[ 1619.803358] end_request: I/O error, dev mmcblk0, sector 2103690
[ 1619.803367] end_request: I/O error, dev mmcblk0, sector 2103691
[ 1619.803375] end_request: I/O error, dev mmcblk0, sector 2103692
[ 1619.803383] end_request: I/O error, dev mmcblk0, sector 2103693
[ 1619.803391] end_request: I/O error, dev mmcblk0, sector 2103694
[ 1619.803400] end_request: I/O error, dev mmcblk0, sector 2103695
[ 1619.803409] end_request: I/O error, dev mmcblk0, sector 2103696
[ 1619.803418] end_request: I/O error, dev mmcblk0, sector 2103697
[ 1619.803426] end_request: I/O error, dev mmcblk0, sector 2103698
[ 1619.803434] end_request: I/O error, dev mmcblk0, sector 2103699
[ 1619.803442] end_request: I/O error, dev mmcblk0, sector 2103700
[ 1619.803451] end_request: I/O error, dev mmcblk0, sector 2103701
[ 1619.803459] end_request: I/O error, dev mmcblk0, sector 2103702
[ 1619.803467] end_request: I/O error, dev mmcblk0, sector 2103703
[ 1619.803475] end_request: I/O error, dev mmcblk0, sector 2103704
[ 1619.803483] end_request: I/O error, dev mmcblk0, sector 2103705
[ 1619.803491] end_request: I/O error, dev mmcblk0, sector 2103706
[ 1619.803499] end_request: I/O error, dev mmcblk0, sector 2103707
[ 1619.803506] end_request: I/O error, dev mmcblk0, sector 2103708
[ 1619.803514] end_request: I/O error, dev mmcblk0, sector 2103709
[ 1619.803522] end_request: I/O error, dev mmcblk0, sector 2103710
[ 1619.803530] end_request: I/O error, dev mmcblk0, sector 2103711
[ 1619.803539] end_request: I/O error, dev mmcblk0, sector 2103712
[ 1619.803547] end_request: I/O error, dev mmcblk0, sector 2103713
[ 1619.803555] end_request: I/O error, dev mmcblk0, sector 2103714
[ 1619.803562] end_request: I/O error, dev mmcblk0, sector 2103715
[ 1619.803569] end_request: I/O error, dev mmcblk0, sector 2103716
[ 1619.803577] end_request: I/O error, dev mmcblk0, sector 2103717
[ 1619.803584] end_request: I/O error, dev mmcblk0, sector 2103718
[ 1619.803591] end_request: I/O error, dev mmcblk0, sector 2103719
[ 1619.803599] end_request: I/O error, dev mmcblk0, sector 2103720
[ 1619.803607] end_request: I/O error, dev mmcblk0, sector 2103721
[ 1619.803614] end_request: I/O error, dev mmcblk0, sector 2103722
[ 1619.803621] end_request: I/O error, dev mmcblk0, sector 2103723
[ 1619.803628] end_request: I/O error, dev mmcblk0, sector 2103724
[ 1619.803634] end_request: I/O error, dev mmcblk0, sector 2103725
[ 1619.803641] end_request: I/O error, dev mmcblk0, sector 2103726
[ 1619.803648] end_request: I/O error, dev mmcblk0, sector 2103727
[ 1619.803655] end_request: I/O error, dev mmcblk0, sector 2103728
[ 1619.803663] end_request: I/O error, dev mmcblk0, sector 2103729
[ 1619.803669] end_request: I/O error, dev mmcblk0, sector 2103730
[ 1619.803676] end_request: I/O error, dev mmcblk0, sector 2103731
[ 1619.803683] end_request: I/O error, dev mmcblk0, sector 2103732
[ 1619.803689] end_request: I/O error, dev mmcblk0, sector 2103733
[ 1619.803696] end_request: I/O error, dev mmcblk0, sector 2103734
[ 1619.803702] end_request: I/O error, dev mmcblk0, sector 2103735
[ 1629.801023] mmc0: Timeout waiting for hardware interrupt.
[ 1629.801033] sdhci: ============== REGISTER DUMP ==============
[ 1629.801041] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1629.801048] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1629.801056] sdhci: Argument: 0x002019b8 | Trn mode: 0x00000022
[ 1629.801063] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1629.801070] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1629.801078] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1629.801085] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1629.801092] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1629.801099] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1629.801106] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1629.801111] sdhci: ===========================================
[ 1629.803132] ------------[ cut here ]------------
[ 1629.803138] WARNING: at /build/buildd/linux-2.6.28/drivers/mmc/host/sdhci.c:786 sdhci_send_command+0x1e8/0x220 [sdhci]()
[ 1629.803143] Modules linked in: ipt_MASQUERADE xt_DSCP binfmt_misc i915 drm ppdev bridge stp bnep vboxnetflt vboxdrv nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_conntrack_ftp lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi iptable_nat snd_rawmidi arc4 nf_nat mmc_block ecb snd_seq_midi_event nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 pcmcia snd_seq snd_timer iptable_mangle iwlagn snd_seq_device iwlcore iptable_filter leds_hp_disk ip_tables snd led_class mac80211 yenta_socket rsrc_nonstatic x_tables soundcore joydev psmouse pcmcia_core ricoh_mmc video sdhci_pci sdhci iTCO_wdt iTCO_vendor_support intel_agp agpgart snd_page_alloc cfg80211 lis3lv02d pcspkr serio_raw output tpm_infineon tpm tpm_bios ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 1629.803317] Pid: 6705, comm: polkit-read-aut Tainted: G        W  2.6.28-11-generic #42-Ubuntu
[ 1629.803322] Call Trace:
[ 1629.803336]  [<c0500ac6>] ? printk+0x18/0x1a
[ 1629.803345]  [<c0139b24>] warn_on_slowpath+0x54/0x80
[ 1629.803369]  [<f7d3dbc8>] sdhci_send_command+0x1e8/0x220 [sdhci]
[ 1629.803384]  [<f7d3dd72>] sdhci_finish_data+0xa2/0xe0 [sdhci]
[ 1629.803399]  [<f7d3c275>] ? sdhci_dumpregs+0x1b5/0x1c0 [sdhci]
[ 1629.803418]  [<f7d3dede>] sdhci_timeout_timer+0x6e/0xa0 [sdhci]
[ 1629.803430]  [<c0143b00>] run_timer_softirq+0x130/0x200
[ 1629.803445]  [<f7d3de70>] ? sdhci_timeout_timer+0x0/0xa0 [sdhci]
[ 1629.803460]  [<f7d3de70>] ? sdhci_timeout_timer+0x0/0xa0 [sdhci]
[ 1629.803470]  [<c013f197>] __do_softirq+0x97/0x170
[ 1629.803478]  [<c0152ca6>] ? hrtimer_interrupt+0x186/0x1b0
[ 1629.803486]  [<c013f2cd>] do_softirq+0x5d/0x60
[ 1629.803493]  [<c013f445>] irq_exit+0x55/0x90
[ 1629.803501]  [<c011a07b>] smp_apic_timer_interrupt+0x5b/0x90
[ 1629.803509]  [<c0105318>] apic_timer_interrupt+0x28/0x30
[ 1629.803519]  [<c01a3838>] ? find_vma+0x28/0x80
[ 1629.803526]  [<c01a3a7d>] arch_get_unmapped_area_topdown+0x8d/0x170
[ 1629.803534]  [<c01a39f0>] ? arch_get_unmapped_area_topdown+0x0/0x170
[ 1629.803542]  [<c01a37b7>] get_unmapped_area+0x47/0xa0
[ 1629.803549]  [<c01a5b97>] do_mmap_pgoff+0xf7/0x360
[ 1629.803557]  [<c01084bd>] sys_mmap2+0xad/0xc0
[ 1629.803564]  [<c0104062>] syscall_call+0x7/0xb
[ 1629.803573]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[ 1629.803578] ---[ end trace 29731e0c7fe974a3 ]---
[ 1629.805608] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1629.805617] sdhci: ============== REGISTER DUMP ==============
[ 1629.805625] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1629.805634] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1629.805641] sdhci: Argument: 0x00000000 | Trn mode: 0x00000022
[ 1629.805648] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1629.805655] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1629.805663] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1629.805670] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1629.805677] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1629.805684] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1629.805693] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1629.805697] sdhci: ===========================================
[ 1629.805769] mmcblk0: error -110 transferring data
[ 1629.805774] mmcblk0: error -110 sending stop command
[ 1639.804070] mmc0: Timeout waiting for hardware interrupt.
[ 1639.804079] sdhci: ============== REGISTER DUMP ==============
[ 1639.804087] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1639.804094] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1639.804102] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1639.804109] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1639.804116] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1639.804124] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1639.804131] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1639.804139] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1639.804146] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1639.804153] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1639.804157] sdhci: ===========================================
[ 1639.806168] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1639.806176] sdhci: ============== REGISTER DUMP ==============
[ 1639.806183] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1639.806191] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1639.806198] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1639.806205] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1639.806212] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1639.806220] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1639.806227] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1639.806234] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1639.806241] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1639.806248] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1639.806253] sdhci: ===========================================
[ 1649.804090] mmc0: Timeout waiting for hardware interrupt.
[ 1649.804099] sdhci: ============== REGISTER DUMP ==============
[ 1649.804107] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1649.804114] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1649.804121] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1649.804129] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1649.804136] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1649.804143] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1649.804150] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1649.804158] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1649.804165] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1649.804172] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1649.804176] sdhci: ===========================================
[ 1649.806186] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1649.806191] sdhci: ============== REGISTER DUMP ==============
[ 1649.806198] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1649.806206] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1649.806213] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1649.806219] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1649.806226] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1649.806234] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1649.806241] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1649.806248] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1649.806256] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1649.806263] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1649.806267] sdhci: ===========================================
[ 1659.804035] mmc0: Timeout waiting for hardware interrupt.
[ 1659.804046] sdhci: ============== REGISTER DUMP ==============
[ 1659.804054] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1659.804061] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1659.804068] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1659.804075] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1659.804082] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1659.804089] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1659.804096] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1659.804103] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1659.804110] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1659.804117] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1659.804121] sdhci: ===========================================
[ 1659.806127] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1659.806133] sdhci: ============== REGISTER DUMP ==============
[ 1659.806140] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1659.806148] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1659.806155] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1659.806163] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1659.806170] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1659.806177] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1659.806184] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1659.806192] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1659.806199] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1659.806206] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1659.806210] sdhci: ===========================================
[ 1669.807100] mmc0: Timeout waiting for hardware interrupt.
[ 1669.807110] sdhci: ============== REGISTER DUMP ==============
[ 1669.807118] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1669.807125] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1669.807132] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1669.807140] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1669.807146] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1669.807154] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1669.807161] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1669.807168] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1669.807175] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1669.807182] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1669.807186] sdhci: ===========================================
[ 1669.809188] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1669.809196] sdhci: ============== REGISTER DUMP ==============
[ 1669.809204] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1669.809212] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1669.809219] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1669.809226] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1669.809233] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1669.809241] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1669.809247] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1669.809255] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1669.809262] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1669.809269] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1669.809273] sdhci: ===========================================
[ 1679.808058] mmc0: Timeout waiting for hardware interrupt.
[ 1679.808066] sdhci: ============== REGISTER DUMP ==============
[ 1679.808071] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1679.808076] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1679.808081] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1679.808087] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1679.808092] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1679.808098] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1679.808103] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1679.808109] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1679.808114] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1679.808120] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1679.808122] sdhci: ===========================================
[ 1679.810122] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1679.810127] sdhci: ============== REGISTER DUMP ==============
[ 1679.810132] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1679.810138] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1679.810144] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1679.810149] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1679.810154] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1679.810159] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1679.810165] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1679.810171] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1679.810176] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1679.810181] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1679.810184] sdhci: ===========================================
[ 1689.812035] mmc0: Timeout waiting for hardware interrupt.
[ 1689.812042] sdhci: ============== REGISTER DUMP ==============
[ 1689.812048] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1689.812054] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1689.812059] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1689.812065] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1689.812070] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1689.812075] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1689.812081] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1689.812087] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1689.812092] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1689.812098] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1689.812101] sdhci: ===========================================
[ 1689.814107] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1689.814111] sdhci: ============== REGISTER DUMP ==============
[ 1689.814116] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1689.814122] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1689.814128] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1689.814133] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1689.814138] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1689.814144] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1689.814149] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1689.814155] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1689.814161] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1689.814167] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1689.814170] sdhci: ===========================================
[ 1689.814186] mmcblk0: error -110 requesting status
[ 1699.812068] mmc0: Timeout waiting for hardware interrupt.
[ 1699.812078] sdhci: ============== REGISTER DUMP ==============
[ 1699.812086] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1699.812094] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1699.812101] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1699.812109] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1699.812116] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1699.812124] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1699.812131] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1699.812138] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1699.812145] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1699.812152] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1699.812157] sdhci: ===========================================
[ 1699.814158] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1699.814166] sdhci: ============== REGISTER DUMP ==============
[ 1699.814174] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1699.814181] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1699.814187] end_request: I/O error, dev mmcblk0, sector 2103736
[ 1699.814197] __ratelimit: 118 callbacks suppressed
[ 1699.814202] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1699.814210] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1699.814216] Buffer I/O error on device mmcblk0, logical block 2103736
[ 1699.814222] lost page write due to I/O error on mmcblk0
[ 1699.814230] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1699.814237] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1699.814245] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1699.814251] end_request: I/O error, dev mmcblk0, sector 2103737
[ 1699.814257] Buffer I/O error on device mmcblk0, logical block 2103737
[ 1699.814263] lost page write due to I/O error on mmcblk0
[ 1699.814272] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1699.814276] end_request: I/O error, dev mmcblk0, sector 2103738
[ 1699.814282] Buffer I/O error on device mmcblk0, logical block 2103738
[ 1699.814288] lost page write due to I/O error on mmcblk0
[ 1699.814297] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1699.814301] end_request: I/O error, dev mmcblk0, sector 2103739
[ 1699.814307] Buffer I/O error on device mmcblk0, logical block 2103739
[ 1699.814313] lost page write due to I/O error on mmcblk0
[ 1699.814322] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1699.814326] end_request: I/O error, dev mmcblk0, sector 2103740
[ 1699.814333] Buffer I/O error on device mmcblk0, logical block 2103740
[ 1699.814338] lost page write due to I/O error on mmcblk0
[ 1699.814344] sdhci: ===========================================
[ 1699.814350] end_request: I/O error, dev mmcblk0, sector 2103741
[ 1699.814357] Buffer I/O error on device mmcblk0, logical block 2103741
[ 1699.814362] lost page write due to I/O error on mmcblk0
[ 1699.814373] end_request: I/O error, dev mmcblk0, sector 2103742
[ 1699.814379] Buffer I/O error on device mmcblk0, logical block 2103742
[ 1699.814384] lost page write due to I/O error on mmcblk0
[ 1699.814397] end_request: I/O error, dev mmcblk0, sector 2103743
[ 1699.814403] Buffer I/O error on device mmcblk0, logical block 2103743
[ 1699.814408] lost page write due to I/O error on mmcblk0
[ 1699.814425] end_request: I/O error, dev mmcblk0, sector 2103744
[ 1699.814431] Buffer I/O error on device mmcblk0, logical block 2103744
[ 1699.814435] lost page write due to I/O error on mmcblk0
[ 1699.814447] end_request: I/O error, dev mmcblk0, sector 2103745
[ 1699.814452] Buffer I/O error on device mmcblk0, logical block 2103745
[ 1699.814457] lost page write due to I/O error on mmcblk0
[ 1699.814468] end_request: I/O error, dev mmcblk0, sector 2103746
[ 1699.814479] end_request: I/O error, dev mmcblk0, sector 2103747
[ 1699.814491] end_request: I/O error, dev mmcblk0, sector 2103748
[ 1699.814502] end_request: I/O error, dev mmcblk0, sector 2103749
[ 1699.814514] end_request: I/O error, dev mmcblk0, sector 2103750
[ 1699.814525] end_request: I/O error, dev mmcblk0, sector 2103751
[ 1699.814538] end_request: I/O error, dev mmcblk0, sector 2103752
[ 1699.814549] end_request: I/O error, dev mmcblk0, sector 2103753
[ 1699.814560] end_request: I/O error, dev mmcblk0, sector 2103754
[ 1699.814571] end_request: I/O error, dev mmcblk0, sector 2103755
[ 1699.814583] end_request: I/O error, dev mmcblk0, sector 2103756
[ 1699.814594] end_request: I/O error, dev mmcblk0, sector 2103757
[ 1699.814605] end_request: I/O error, dev mmcblk0, sector 2103758
[ 1699.814616] end_request: I/O error, dev mmcblk0, sector 2103759
[ 1699.814627] end_request: I/O error, dev mmcblk0, sector 2103760
[ 1699.814638] end_request: I/O error, dev mmcblk0, sector 2103761
[ 1699.814649] end_request: I/O error, dev mmcblk0, sector 2103762
[ 1699.814660] end_request: I/O error, dev mmcblk0, sector 2103763
[ 1699.814671] end_request: I/O error, dev mmcblk0, sector 2103764
[ 1699.814682] end_request: I/O error, dev mmcblk0, sector 2103765
[ 1699.814693] end_request: I/O error, dev mmcblk0, sector 2103766
[ 1699.814703] end_request: I/O error, dev mmcblk0, sector 2103767
[ 1699.814715] end_request: I/O error, dev mmcblk0, sector 2103768
[ 1699.814725] end_request: I/O error, dev mmcblk0, sector 2103769
[ 1699.814736] end_request: I/O error, dev mmcblk0, sector 2103770
[ 1699.814746] end_request: I/O error, dev mmcblk0, sector 2103771
[ 1699.814757] end_request: I/O error, dev mmcblk0, sector 2103772
[ 1699.814767] end_request: I/O error, dev mmcblk0, sector 2103773
[ 1699.814778] end_request: I/O error, dev mmcblk0, sector 2103774
[ 1699.814789] end_request: I/O error, dev mmcblk0, sector 2103775
[ 1699.814801] end_request: I/O error, dev mmcblk0, sector 2103776
[ 1699.814811] end_request: I/O error, dev mmcblk0, sector 2103777
[ 1699.814821] end_request: I/O error, dev mmcblk0, sector 2103778
[ 1699.814832] end_request: I/O error, dev mmcblk0, sector 2103779
[ 1699.814842] end_request: I/O error, dev mmcblk0, sector 2103780
[ 1699.814852] end_request: I/O error, dev mmcblk0, sector 2103781
[ 1699.814862] end_request: I/O error, dev mmcblk0, sector 2103782
[ 1699.814871] end_request: I/O error, dev mmcblk0, sector 2103783
[ 1699.814882] end_request: I/O error, dev mmcblk0, sector 2103784
[ 1699.814892] end_request: I/O error, dev mmcblk0, sector 2103785
[ 1699.814902] end_request: I/O error, dev mmcblk0, sector 2103786
[ 1699.814912] end_request: I/O error, dev mmcblk0, sector 2103787
[ 1699.814921] end_request: I/O error, dev mmcblk0, sector 2103788
[ 1699.814931] end_request: I/O error, dev mmcblk0, sector 2103789
[ 1699.814940] end_request: I/O error, dev mmcblk0, sector 2103790
[ 1699.814949] end_request: I/O error, dev mmcblk0, sector 2103791
[ 1699.814959] end_request: I/O error, dev mmcblk0, sector 2103792
[ 1699.814969] end_request: I/O error, dev mmcblk0, sector 2103793
[ 1699.814978] end_request: I/O error, dev mmcblk0, sector 2103794
[ 1699.814987] end_request: I/O error, dev mmcblk0, sector 2103795
[ 1699.814996] end_request: I/O error, dev mmcblk0, sector 2103796
[ 1699.815005] end_request: I/O error, dev mmcblk0, sector 2103797
[ 1699.815015] end_request: I/O error, dev mmcblk0, sector 2103798
[ 1699.815024] end_request: I/O error, dev mmcblk0, sector 2103799
[ 1699.815034] end_request: I/O error, dev mmcblk0, sector 2103800
[ 1699.815043] end_request: I/O error, dev mmcblk0, sector 2103801
[ 1699.815052] end_request: I/O error, dev mmcblk0, sector 2103802
[ 1699.815061] end_request: I/O error, dev mmcblk0, sector 2103803
[ 1699.815070] end_request: I/O error, dev mmcblk0, sector 2103804
[ 1699.815079] end_request: I/O error, dev mmcblk0, sector 2103805
[ 1699.815087] end_request: I/O error, dev mmcblk0, sector 2103806
[ 1699.815097] end_request: I/O error, dev mmcblk0, sector 2103807
[ 1699.815106] end_request: I/O error, dev mmcblk0, sector 2103808
[ 1699.815115] end_request: I/O error, dev mmcblk0, sector 2103809
[ 1699.815124] end_request: I/O error, dev mmcblk0, sector 2103810
[ 1699.815132] end_request: I/O error, dev mmcblk0, sector 2103811
[ 1699.815141] end_request: I/O error, dev mmcblk0, sector 2103812
[ 1699.815150] end_request: I/O error, dev mmcblk0, sector 2103813
[ 1699.815158] end_request: I/O error, dev mmcblk0, sector 2103814
[ 1699.815166] end_request: I/O error, dev mmcblk0, sector 2103815
[ 1699.815175] end_request: I/O error, dev mmcblk0, sector 2103816
[ 1699.815184] end_request: I/O error, dev mmcblk0, sector 2103817
[ 1699.815192] end_request: I/O error, dev mmcblk0, sector 2103818
[ 1699.815201] end_request: I/O error, dev mmcblk0, sector 2103819
[ 1699.815209] end_request: I/O error, dev mmcblk0, sector 2103820
[ 1699.815217] end_request: I/O error, dev mmcblk0, sector 2103821
[ 1699.815226] end_request: I/O error, dev mmcblk0, sector 2103822
[ 1699.815234] end_request: I/O error, dev mmcblk0, sector 2103823
[ 1699.815243] end_request: I/O error, dev mmcblk0, sector 2103824
[ 1699.815251] end_request: I/O error, dev mmcblk0, sector 2103825
[ 1699.815259] end_request: I/O error, dev mmcblk0, sector 2103826
[ 1699.815267] end_request: I/O error, dev mmcblk0, sector 2103827
[ 1699.815275] end_request: I/O error, dev mmcblk0, sector 2103828
[ 1699.815283] end_request: I/O error, dev mmcblk0, sector 2103829
[ 1699.815291] end_request: I/O error, dev mmcblk0, sector 2103830
[ 1699.815298] end_request: I/O error, dev mmcblk0, sector 2103831
[ 1699.815307] end_request: I/O error, dev mmcblk0, sector 2103832
[ 1699.815315] end_request: I/O error, dev mmcblk0, sector 2103833
[ 1699.815323] end_request: I/O error, dev mmcblk0, sector 2103834
[ 1699.815331] end_request: I/O error, dev mmcblk0, sector 2103835
[ 1699.815338] end_request: I/O error, dev mmcblk0, sector 2103836
[ 1699.815346] end_request: I/O error, dev mmcblk0, sector 2103837
[ 1699.815354] end_request: I/O error, dev mmcblk0, sector 2103838
[ 1699.815362] end_request: I/O error, dev mmcblk0, sector 2103839
[ 1699.815370] end_request: I/O error, dev mmcblk0, sector 2103840
[ 1699.815378] end_request: I/O error, dev mmcblk0, sector 2103841
[ 1699.815385] end_request: I/O error, dev mmcblk0, sector 2103842
[ 1699.815392] end_request: I/O error, dev mmcblk0, sector 2103843
[ 1699.815400] end_request: I/O error, dev mmcblk0, sector 2103844
[ 1699.815407] end_request: I/O error, dev mmcblk0, sector 2103845
[ 1699.815414] end_request: I/O error, dev mmcblk0, sector 2103846
[ 1699.815421] end_request: I/O error, dev mmcblk0, sector 2103847
[ 1699.815429] end_request: I/O error, dev mmcblk0, sector 2103848
[ 1699.815435] end_request: I/O error, dev mmcblk0, sector 2103849
[ 1699.815443] end_request: I/O error, dev mmcblk0, sector 2103850
[ 1699.815450] end_request: I/O error, dev mmcblk0, sector 2103851
[ 1699.815456] end_request: I/O error, dev mmcblk0, sector 2103852
[ 1699.815463] end_request: I/O error, dev mmcblk0, sector 2103853
[ 1699.815470] end_request: I/O error, dev mmcblk0, sector 2103854
[ 1699.815477] end_request: I/O error, dev mmcblk0, sector 2103855
[ 1699.815484] end_request: I/O error, dev mmcblk0, sector 2103856
[ 1699.815490] end_request: I/O error, dev mmcblk0, sector 2103857
[ 1699.815497] end_request: I/O error, dev mmcblk0, sector 2103858
[ 1699.815504] end_request: I/O error, dev mmcblk0, sector 2103859
[ 1699.815510] end_request: I/O error, dev mmcblk0, sector 2103860
[ 1699.815517] end_request: I/O error, dev mmcblk0, sector 2103861
[ 1699.815523] end_request: I/O error, dev mmcblk0, sector 2103862
[ 1699.815530] end_request: I/O error, dev mmcblk0, sector 2103863
[ 1709.816023] mmc0: Timeout waiting for hardware interrupt.
[ 1709.816033] sdhci: ============== REGISTER DUMP ==============
[ 1709.816041] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1709.816048] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1709.816056] sdhci: Argument: 0x00201a38 | Trn mode: 0x00000022
[ 1709.816063] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1709.816070] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1709.816077] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1709.816084] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1709.816092] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1709.816098] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1709.816106] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1709.816111] sdhci: ===========================================
[ 1709.818131] ------------[ cut here ]------------
[ 1709.818137] WARNING: at /build/buildd/linux-2.6.28/drivers/mmc/host/sdhci.c:786 sdhci_send_command+0x1e8/0x220 [sdhci]()
[ 1709.818143] Modules linked in: ipt_MASQUERADE xt_DSCP binfmt_misc i915 drm ppdev bridge stp bnep vboxnetflt vboxdrv nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_conntrack_ftp lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi iptable_nat snd_rawmidi arc4 nf_nat mmc_block ecb snd_seq_midi_event nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 pcmcia snd_seq snd_timer iptable_mangle iwlagn snd_seq_device iwlcore iptable_filter leds_hp_disk ip_tables snd led_class mac80211 yenta_socket rsrc_nonstatic x_tables soundcore joydev psmouse pcmcia_core ricoh_mmc video sdhci_pci sdhci iTCO_wdt iTCO_vendor_support intel_agp agpgart snd_page_alloc cfg80211 lis3lv02d pcspkr serio_raw output tpm_infineon tpm tpm_bios ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 1709.818315] Pid: 5592, comm: firefox Tainted: G        W  2.6.28-11-generic #42-Ubuntu
[ 1709.818321] Call Trace:
[ 1709.818335]  [<c0500ac6>] ? printk+0x18/0x1a
[ 1709.818344]  [<c0139b24>] warn_on_slowpath+0x54/0x80
[ 1709.818369]  [<f7d3dbc8>] sdhci_send_command+0x1e8/0x220 [sdhci]
[ 1709.818384]  [<f7d3dd72>] sdhci_finish_data+0xa2/0xe0 [sdhci]
[ 1709.818399]  [<f7d3c275>] ? sdhci_dumpregs+0x1b5/0x1c0 [sdhci]
[ 1709.818418]  [<f7d3dede>] sdhci_timeout_timer+0x6e/0xa0 [sdhci]
[ 1709.818430]  [<c0143b00>] run_timer_softirq+0x130/0x200
[ 1709.818445]  [<f7d3de70>] ? sdhci_timeout_timer+0x0/0xa0 [sdhci]
[ 1709.818459]  [<f7d3de70>] ? sdhci_timeout_timer+0x0/0xa0 [sdhci]
[ 1709.818469]  [<c013f197>] __do_softirq+0x97/0x170
[ 1709.818476]  [<c0152ca6>] ? hrtimer_interrupt+0x186/0x1b0
[ 1709.818484]  [<c013f2cd>] do_softirq+0x5d/0x60
[ 1709.818491]  [<c013f445>] irq_exit+0x55/0x90
[ 1709.818499]  [<c011a07b>] smp_apic_timer_interrupt+0x5b/0x90
[ 1709.818507]  [<c0105318>] apic_timer_interrupt+0x28/0x30
[ 1709.818512] ---[ end trace 29731e0c7fe974a3 ]---
[ 1709.820534] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1709.820542] sdhci: ============== REGISTER DUMP ==============
[ 1709.820551] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1709.820560] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1709.820567] sdhci: Argument: 0x00000000 | Trn mode: 0x00000022
[ 1709.820575] mmcblk0: error -110 transferring data
[ 1709.820579] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1709.820587] mmcblk0: error -110 sending stop command
[ 1709.820591] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1709.820599] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1709.820606] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1709.820614] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1709.820621] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1709.820628] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1709.820633] sdhci: ===========================================
[ 1719.816017] mmc0: Timeout waiting for hardware interrupt.
[ 1719.816025] sdhci: ============== REGISTER DUMP ==============
[ 1719.816032] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1719.816037] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1719.816043] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1719.816048] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1719.816054] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1719.816059] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1719.816064] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1719.816070] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1719.816075] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1719.816081] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1719.816084] sdhci: ===========================================
[ 1719.818083] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1719.818088] sdhci: ============== REGISTER DUMP ==============
[ 1719.818093] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1719.818099] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1719.818104] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1719.818110] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1719.818114] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1719.818120] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1719.818125] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1719.818130] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1719.818136] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1719.818141] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1719.818144] sdhci: ===========================================
[ 1729.816085] mmc0: Timeout waiting for hardware interrupt.
[ 1729.816094] sdhci: ============== REGISTER DUMP ==============
[ 1729.816103] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1729.816110] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1729.816117] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1729.816124] sdhci: Present:  0x01ff0001 | Host ctl: 0x00000003
[ 1729.816131] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1729.816139] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1729.816146] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1729.816153] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1729.816160] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1729.816167] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1729.816171] sdhci: ===========================================
[ 1729.818178] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[ 1729.818184] sdhci: ============== REGISTER DUMP ==============
[ 1729.818191] sdhci: Sys addr: 0x00000000 | Version:  0x00000400
[ 1729.818199] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000080
[ 1729.818206] sdhci: Argument: 0x8fcf0000 | Trn mode: 0x00000022
[ 1729.818213] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000002
[ 1729.818220] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
[ 1729.818228] sdhci: Wake-up:  0x00000000 | Clock:    0x00000103
[ 1729.818235] sdhci: Timeout:  0x0000000b | Int stat: 0x00000000
[ 1729.818242] sdhci: Int enab: 0x02ff00fb | Sig enab: 0x02ff00fb
[ 1729.818250] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[ 1729.818257] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[ 1729.818261] sdhci: ===========================================


---

