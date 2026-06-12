---
title: "CD/DVD rom won't mount"
date: 2009-08-25
forum: General Help
---

### Post by capinlarry on 2009-08-25
I just installed ubuntu on my desktop and i cannot get the CD or DVD rom to mount. PLACES>COMPUTER lists the floppy driave and the hard drive only. I've tried manually mounting it but it says device is not found. It does not mount when I put in a CD or DVD either. Its like the drives are not even there but I get lights on both drives when I insert a CD. Any ideas?

---

### Post by nikhilk on 2009-08-25
> **capinlarry said:**
> I just installed ubuntu on my desktop and i cannot get the CD or DVD rom to mount. PLACES>COMPUTER lists the floppy driave and the hard drive only. I've tried manually mounting it but it says device is not found. It does not mount when I put in a CD or DVD either. Its like the drives are not even there but I get lights on both drives when I insert a CD. Any ideas?

Have you checked whether all connections to the optical drive are OK?

Can you attach it to some other computer and check if the drive is functioning properly?

---

### Post by P4man on 2009-08-25
Does the bios find the drive ?
If you are certain its not a hardware/cabling problem, then attach the output of dmesg and lshw here.

---

### Post by capinlarry on 2009-08-27
> **P4man said:**
> Does the bios find the drive ?
If you are certain its not a hardware/cabling problem, then attach the output of dmesg and lshw here.

dmesg:

[    0.000000] ACPI: RSDT 0FF40000, 002C (r1 A M I  OEMRSDT   7000218 MSFT       97)
[    0.000000] ACPI: FACP 0FF40200, 0081 (r2 A M I  OEMFACP   7000218 MSFT       97)
[    0.000000] ACPI: DSDT 0FF40400, 39D5 (r1   DELL DIM 4500      10A MSFT  100000D)
[    0.000000] ACPI: FACS 0FF50000, 0040
[    0.000000] ACPI: APIC 0FF40300, 0054 (r1 A M I  OEMAPIC   7000218 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0ff40000
[    0.000000]   low ram: 00000000 - 0ff40000
[    0.000000]   bootmap 00012000 - 00013fe8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000ff40000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [000f7fc000 - 000ff2fde3]          RAMDISK ==> [000f7fc000 - 000ff2fde3]
[    0.000000]   #5 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000ff40
[    0.000000]   HighMem  0x0000ff40 -> 0x0000ff40
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0000ff40
[    0.000000] On node 0 totalpages: 65221
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60769 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:f0000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64710
[    0.000000] Kernel command line: root=UUID=76a2d45d-2b56-47cd-93e1-4fb43a457ab0 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1993.580 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1306880 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 242040k/261376k available (4115k kernel code, 18664k reserved, 2199k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0740000 - 0xff3fe000   ( 748 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcff40000   ( 255 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3987.16 BogoMIPS (lpj=7974320)
[    0.004042] Security Framework initialized
[    0.004053] SELinux:  Disabled at boot.
[    0.004079] AppArmor: AppArmor initialized
[    0.004096] Mount-cache hash table entries: 512
[    0.004298] Initializing cgroup subsys ns
[    0.004305] Initializing cgroup subsys cpuacct
[    0.004310] Initializing cgroup subsys memory
[    0.004317] Initializing cgroup subsys freezer
[    0.004340] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004345] CPU: L2 cache: 512K
[    0.004350] CPU: Hyper-Threading is disabled
[    0.004376] Checking 'hlt' instruction... OK.
[    0.021022] SMP alternatives: switching to UP code
[    0.161106] Freeing SMP alternatives: 18k freed
[    0.161113] ACPI: Core revision 20080926
[    0.165748] ACPI: Checking initramfs for custom DSDT
[    0.612879] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.652575] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[    0.656002] Brought up 1 CPUs
[    0.656002] Total of 1 processors activated (3987.16 BogoMIPS).
[    0.656002] CPU0 attaching NULL sched-domain.
[    0.656002] net_namespace: 776 bytes
[    0.656002] Booting paravirtualized kernel on bare hardware
[    0.656002] Time: 22:50:23  Date: 08/26/09
[    0.656002] regulator: core version 0.5
[    0.656002] NET: Registered protocol family 16
[    0.656002] EISA bus registered
[    0.656002] ACPI: bus type pci registered
[    0.656002] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.656002] PCI: Using configuration type 1 for base access
[    0.656206] ACPI: EC: Look up EC in DSDT
[    0.666479] ACPI: Interpreter enabled
[    0.666490] ACPI: (supports S0 S1 S3 S4 S5)
[    0.666522] ACPI: Using IOAPIC for interrupt routing
[    0.675583] ACPI: No dock devices found.
[    0.675599] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.675672] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.675814] pci 0000:00:1d.0: reg 20 io port: [0xe800-0xe81f]
[    0.675877] pci 0000:00:1d.1: reg 20 io port: [0xe880-0xe89f]
[    0.675940] pci 0000:00:1d.2: reg 20 io port: [0xec00-0xec1f]
[    0.676028] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffaffc00-0xffafffff]
[    0.676081] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.676088] pci 0000:00:1d.7: PME# disabled
[    0.676147] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.676149] * this clock source is slow. If you are sure your timer does not have
[    0.676151] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.676199] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.676208] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.676214] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.676242] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.676251] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.676259] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.676268] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.676277] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.676285] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.676345] pci 0000:00:1f.3: reg 20 io port: [0xe000-0xe01f]
[    0.676397] pci 0000:00:1f.5: reg 10 io port: [0xe400-0xe4ff]
[    0.676405] pci 0000:00:1f.5: reg 14 io port: [0xe080-0xe0bf]
[    0.676414] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffaff800-0xffaff9ff]
[    0.676423] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffaff400-0xffaff4ff]
[    0.676450] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.676456] pci 0000:00:1f.5: PME# disabled
[    0.676508] pci 0000:01:00.0: reg 10 32bit mmio: [0xf0000000-0xf3ffffff]
[    0.676517] pci 0000:01:00.0: reg 14 io port: [0xc800-0xc8ff]
[    0.676525] pci 0000:01:00.0: reg 18 32bit mmio: [0xff8fc000-0xff8fffff]
[    0.676547] pci 0000:01:00.0: reg 30 32bit mmio: [0xff8c0000-0xff8dffff]
[    0.676561] pci 0000:01:00.0: supports D1
[    0.676609] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.676614] pci 0000:00:01.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[    0.676620] pci 0000:00:01.0: bridge 32bit mmio pref: [0xee900000-0xf69fffff]
[    0.676661] pci 0000:02:01.0: reg 10 32bit mmio: [0xff9d0000-0xff9dffff]
[    0.676670] pci 0000:02:01.0: reg 14 io port: [0xdc00-0xdc07]
[    0.676708] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.676713] pci 0000:02:01.0: PME# disabled
[    0.676753] pci 0000:02:02.0: reg 10 io port: [0xd800-0xd8ff]
[    0.676762] pci 0000:02:02.0: reg 14 32bit mmio: [0xff9fec00-0xff9fecff]
[    0.676792] pci 0000:02:02.0: reg 30 32bit mmio: [0xff980000-0xff9bffff]
[    0.676804] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.676809] pci 0000:02:02.0: PME# disabled
[    0.676859] pci 0000:00:1e.0: transparent bridge
[    0.676865] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.676871] pci 0000:00:1e.0: bridge 32bit mmio: [0xff900000-0xff9fffff]
[    0.676877] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xf6a00000-0xf6afffff]
[    0.676892] bus 00 -> node 0
[    0.676900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.677137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.679150] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.679399] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.679644] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.679888] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.680147] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.680395] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.680641] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.680886] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.681060] ACPI: Power Resource [URP1] (off)
[    0.681116] ACPI: Power Resource [FDDP] (off)
[    0.681175] ACPI: Power Resource [LPTP] (off)
[    0.681289] ACPI: WMI: Mapper loaded
[    0.681626] SCSI subsystem initialized
[    0.681688] libata version 3.00 loaded.
[    0.681770] usbcore: registered new interface driver usbfs
[    0.681799] usbcore: registered new interface driver hub
[    0.681845] usbcore: registered new device driver usb
[    0.682030] PCI: Using ACPI for IRQ routing
[    0.682166] Bluetooth: Core ver 2.13
[    0.682166] NET: Registered protocol family 31
[    0.682166] Bluetooth: HCI device and connection manager initialized
[    0.682166] Bluetooth: HCI socket layer initialized
[    0.682166] NET: Registered protocol family 8
[    0.682166] NET: Registered protocol family 20
[    0.682166] NetLabel: Initializing
[    0.682166] NetLabel:  domain hash size = 128
[    0.682166] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.682166] NetLabel:  unlabeled traffic allowed by default
[    0.682166] AppArmor: AppArmor Filesystem Enabled
[    0.682166] pnp: PnP ACPI init
[    0.682166] ACPI: bus type pnp registered
[    0.689147] pnp: PnP ACPI: found 14 devices
[    0.689151] ACPI: ACPI bus type pnp unregistered
[    0.689157] PnPBIOS: Disabled by ACPI PNP
[    0.689178] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.689190] system 00:0c: ioport range 0x400-0x47f has been reserved
[    0.689194] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.689197] system 00:0c: ioport range 0x480-0x4bf has been reserved
[    0.689202] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.689206] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.689215] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.689219] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[    0.689223] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.689228] system 00:0d: iomem range 0x100000-0xfffffff could not be reserved
[    0.724075] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.724080] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.724086] pci 0000:00:01.0:   MEM window: 0xff800000-0xff8fffff
[    0.724091] pci 0000:00:01.0:   PREFETCH window: 0x000000ee900000-0x000000f69fffff
[    0.724101] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.724106] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.724113] pci 0000:00:1e.0:   MEM window: 0xff900000-0xff9fffff
[    0.724119] pci 0000:00:1e.0:   PREFETCH window: 0x000000f6a00000-0x000000f6afffff
[    0.724141] pci 0000:00:1e.0: setting latency timer to 64
[    0.724147] bus: 00 index 0 io port: [0x00-0xffff]
[    0.724150] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.724154] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.724157] bus: 01 index 1 mmio: [0xff800000-0xff8fffff]
[    0.724160] bus: 01 index 2 mmio: [0xee900000-0xf69fffff]
[    0.724163] bus: 01 index 3 mmio: [0x0-0x0]
[    0.724166] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.724169] bus: 02 index 1 mmio: [0xff900000-0xff9fffff]
[    0.724173] bus: 02 index 2 mmio: [0xf6a00000-0xf6afffff]
[    0.724175] bus: 02 index 3 io port: [0x00-0xffff]
[    0.724178] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.724191] NET: Registered protocol family 2
[    0.724381] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.724723] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.724785] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.724844] TCP: Hash tables configured (established 8192 bind 8192)
[    0.724847] TCP reno registered
[    0.724957] NET: Registered protocol family 1
[    0.725156] checking if image is initramfs... it is
[    1.228025] Switched to high resolution mode on CPU 0
[    1.650684] Freeing initrd memory: 7375k freed
[    1.650795] cpufreq: No nForce2 chipset.
[    1.651039] audit: initializing netlink socket (disabled)
[    1.651073] type=2000 audit(1251327024.648:1): initialized
[    1.660136] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.661959] VFS: Disk quotas dquot_6.5.1
[    1.662052] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.663027] fuse init (API version 7.10)
[    1.663151] msgmni has been set to 487
[    1.663451] alg: No test for stdrng (krng)
[    1.663472] io scheduler noop registered
[    1.663475] io scheduler anticipatory registered
[    1.663478] io scheduler deadline registered
[    1.663506] io scheduler cfq registered (default)
[    1.663616] pci 0000:01:00.0: Boot video device
[    1.667691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.667707] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.667899] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.667903] ACPI: Power Button (FF) [PWRF]
[    1.667983] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.667993] ACPI: Sleep Button (CM) [SLPB]
[    1.668238] processor ACPI_CPU:00: registered as cooling_device0
[    1.668244] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.670656] isapnp: Scanning for PnP cards...
[    2.024607] isapnp: No Plug & Play device found
[    2.026620] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.026733] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.027164] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.028426] brd: module loaded
[    2.028920] loop: module loaded
[    2.029052] Fixed MDIO Bus: probed
[    2.029063] PPP generic driver version 2.4.2
[    2.029161] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.029213] Driver 'sd' needs updating - please use bus_type methods
[    2.029228] Driver 'sr' needs updating - please use bus_type methods
[    2.029339] ata_piix 0000:00:1f.1: version 2.12
[    2.029355] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.029374] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.029453] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.029627] scsi0 : ata_piix
[    2.029785] scsi1 : ata_piix
[    2.031718] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.031722] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.192528] ata1.00: ATA-5: MAXTOR 6L020J1, A93.0500, max UDMA/133
[    2.192533] ata1.00: 40132503 sectors, multi 16: LBA 
[    2.208463] ata1.00: configured for UDMA/100
[    7.516010] ata2: link is slow to respond, please be patient (ready=0)
[   12.220010] ata2: SRST failed (errno=-16)
[   17.528010] ata2: link is slow to respond, please be patient (ready=0)
[   22.232010] ata2: SRST failed (errno=-16)
[   27.540010] ata2: link is slow to respond, please be patient (ready=0)
[   57.276009] ata2: SRST failed (errno=-16)
[   62.304010] ata2: SRST failed (errno=-16)
[   62.304054] ata2: reset failed, giving up
[   62.304258] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L020J1   A93. PQ: 0 ANSI: 5
[   62.304433] sd 0:0:0:0: [sda] 40132503 512-byte hardware sectors: (20.5 GB/19.1 GiB)
[   62.304459] sd 0:0:0:0: [sda] Write Protect is off
[   62.304463] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   62.304503] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   62.304601] sd 0:0:0:0: [sda] 40132503 512-byte hardware sectors: (20.5 GB/19.1 GiB)
[   62.304623] sd 0:0:0:0: [sda] Write Protect is off
[   62.304628] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   62.304665] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   62.304671]  sda: sda1 sda2 < sda5 >
[   62.350096] sd 0:0:0:0: [sda] Attached SCSI disk
[   62.350181] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   62.351109] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   62.351151] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   62.351186] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   62.351192] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   62.351299] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   62.355209] ehci_hcd 0000:00:1d.7: debug port 1
[   62.355218] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[   62.355239] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffaffc00
[   62.368014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   62.368116] usb usb1: configuration #1 chosen from 1 choice
[   62.368160] hub 1-0:1.0: USB hub found
[   62.368175] hub 1-0:1.0: 6 ports detected
[   62.368355] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   62.368384] uhci_hcd: USB Universal Host Controller Interface driver
[   62.368449] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   62.368461] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   62.368465] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   62.368532] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   62.368566] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[   62.368692] usb usb2: configuration #1 chosen from 1 choice
[   62.368733] hub 2-0:1.0: USB hub found
[   62.368746] hub 2-0:1.0: 2 ports detected
[   62.368870] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   62.368879] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   62.368884] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   62.368950] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   62.368984] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[   62.369094] usb usb3: configuration #1 chosen from 1 choice
[   62.369133] hub 3-0:1.0: USB hub found
[   62.369146] hub 3-0:1.0: 2 ports detected
[   62.369268] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   62.369277] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   62.369281] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   62.369346] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   62.369381] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[   62.369497] usb usb4: configuration #1 chosen from 1 choice
[   62.369541] hub 4-0:1.0: USB hub found
[   62.369555] hub 4-0:1.0: 2 ports detected
[   62.369764] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   62.372648] serio: i8042 KBD port at 0x60,0x64 irq 1
[   62.372658] serio: i8042 AUX port at 0x60,0x64 irq 12
[   62.372833] mice: PS/2 mouse device common for all mice
[   62.373036] rtc_cmos 00:02: RTC can wake from S4
[   62.373108] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[   62.373135] rtc0: alarms up to one month, 114 bytes nvram
[   62.373254] device-mapper: uevent: version 1.0.3
[   62.373435] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[   62.373518] device-mapper: multipath: version 1.0.5 loaded
[   62.373523] device-mapper: multipath round-robin: version 1.0.0 loaded
[   62.373661] EISA: Probing bus 0 at eisa.0
[   62.373712] EISA: Detected 0 cards.
[   62.373754] cpuidle: using governor ladder
[   62.373758] cpuidle: using governor menu
[   62.374553] TCP cubic registered
[   62.374670] NET: Registered protocol family 10
[   62.375292] lo: Disabled Privacy Extensions
[   62.375776] NET: Registered protocol family 17
[   62.375805] Bluetooth: L2CAP ver 2.11
[   62.375808] Bluetooth: L2CAP socket layer initialized
[   62.375813] Bluetooth: SCO (Voice Link) ver 0.6
[   62.375816] Bluetooth: SCO socket layer initialized
[   62.375871] Bluetooth: RFCOMM socket layer initialized
[   62.375885] Bluetooth: RFCOMM TTY layer initialized
[   62.375888] Bluetooth: RFCOMM ver 1.10
[   62.375957] Using IPI No-Shortcut mode
[   62.376136] registered taskstats version 1
[   62.376286]   Magic number: 5:90:857
[   62.376303] bdi 8:0: hash matches
[   62.376411] rtc_cmos 00:02: setting system clock to 2009-08-26 22:51:25 UTC (1251327085)
[   62.376416] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   62.376418] EDD information not available.
[   62.377311] Freeing unused kernel memory: 532k freed
[   62.377483] Write protecting the kernel text: 4116k
[   62.377538] Write protecting the kernel read-only data: 1528k
[   62.411370] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   62.870341] Floppy drive(s): fd0 is 1.44M
[   62.887843] FDC 0 is a post-1991 82077
[   63.014396] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[   63.014472] dmfe 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   63.045461] eth0: Davicom DM9102 at pci0000:02:02.0, 00:08:a1:04:6c:59, irq 18.
[   63.684284] PM: Starting manual resume from disk
[   63.684291] PM: Resume from partition 8:5
[   63.684293] PM: Checking hibernation image.
[   63.684604] PM: Resume from disk failed.
[   63.739837] kjournald starting.  Commit interval 5 seconds
[   63.739857] EXT3-fs: mounted filesystem with ordered data mode.
[   69.979745] udev: starting version 141
[   70.199319] parport_pc 00:07: reported by Plug and Play ACPI
[   70.199384] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   70.260921] Linux agpgart interface v0.103
[   70.274045] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.277273] intel_rng: Firmware space is locked read-only. If you can't or
[   70.277276] intel_rng: don't want to disable this in firmware setup, and if
[   70.277278] intel_rng: you are certain that your system has a functional
[   70.277280] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   70.294625] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   70.302046] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   70.497200] iTCO_vendor_support: vendor-support=0
[   70.500917] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   70.501101] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   70.501223] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   70.728459] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   70.902367] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   70.912989] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   71.003162] ppdev: user-space parallel port driver
[   71.235954] psmouse serio1: ID: 10 00 64<6>Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   71.433574] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   71.804087] intel8x0_measure_ac97_clock: measured 54914 usecs
[   71.804092] intel8x0: clocking to 48000
[   71.899334] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   72.038447] lp0: using parport0 (interrupt-driven).
[   72.178708] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k
[   72.751741] EXT3 FS on sda1, internal journal
[   74.043445] type=1505 audit(1251327097.163:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1813
[   74.120333] type=1505 audit(1251327097.243:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1817
[   74.120665] type=1505 audit(1251327097.243:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1817
[   74.120748] type=1505 audit(1251327097.243:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1817
[   74.120823] type=1505 audit(1251327097.243:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1817
[   74.334447] type=1505 audit(1251327097.455:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1822
[   74.334882] type=1505 audit(1251327097.455:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1822
[   74.382896] type=1505 audit(1251327097.503:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1826
[   77.271273] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   77.271278] Bluetooth: BNEP filters: protocol multicast
[   77.296802] Bridge firewalling registered
[   79.462927] mtrr: no MTRR for f0000000,2000000 found
[   79.782067] [drm] Initialized drm 1.1.0 20060810
[   79.841704] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   79.842037] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   79.847229] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   79.847256] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   79.847299] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[   82.879321] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   85.877801] dmfe: Change Speed to 100Mhz full duplex
[   85.877896] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   96.212033] eth0: no IPv6 routers present

lshw:

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.4
          size: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 Pro Ultra TF
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax/Voice/Spkp Modem
                vendor: Conexant Systems, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 31
                serial: 00:08:a1:04:6c:59
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.1.101 latency=64 maxlatency=40 mingnt=20 module=dmfe multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:a7:c8:52:2e:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by P4man on 2009-08-27
Here is your problem I think:

> [ 7.516010] ata2: link is slow to respond, please be patient (ready=0)
[ 12.220010] ata2: SRST failed (errno=-16)
[ 17.528010] ata2: link is slow to respond, please be patient (ready=0)
[ 22.232010] ata2: SRST failed (errno=-16)
[ 27.540010] ata2: link is slow to respond, please be patient (ready=0)
[ 57.276009] ata2: SRST failed (errno=-16)
[ 62.304010] ata2: SRST failed (errno=-16)
[ 62.304054] ata2: reset failed, giving up

Im not sure if thats a kernel bug, or a problem with the device. You might want to try another ide cable, or check master/slave settings. If that doesn't help, report a bug report. Does the drive work on another OS?

btw, please put such long entries between code tags, so its easier for everyone to navigate this thread.

---

### Post by careertargetph on 2009-08-27
I encountered same problem. Can you please help me?

[http://www.careertargetph.com](http://www.careertargetph.com)
Best Jobs and Careers Online

---

