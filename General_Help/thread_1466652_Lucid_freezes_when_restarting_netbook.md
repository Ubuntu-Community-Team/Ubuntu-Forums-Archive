---
title: "Lucid freezes when restarting netbook"
date: 2010-04-30
forum: General Help
---

### Post by Marblemike on 2010-04-30
Hi,

I just finished a fresh install of Lucid netbook remix on my new Sony Vaio netbook. Everything seemed to go fine until a restart was required after installation was complete, when the monitor went black and the netbook just hung.

The only way I could restart was to manually power off and on again. The installation seems to have completed fine and everything works after boot up.

However, the netbook continues to freeze if I select restart from the power options.

I know its not critical, but it is annoying. Does anyone have any ideas on how to solve this?

---

### Post by koanhead on 2010-04-30
Try booting from a livecd. Mount the lappy's disk (this should happen automagically) and post the contents of /var/log/messages - this will help in diagnosis.

---

### Post by Marblemike on 2010-04-30
My /var/log/messages:

Apr 30 16:23:45 ubuntu kernel: [    0.000000] Zone PFN ranges:
Apr 30 16:23:45 ubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr 30 16:23:45 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr 30 16:23:45 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f600
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 16:23:45 ubuntu kernel: [    0.000000] early_node_map[6] active PFN ranges
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007f494
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     0: 0x0007f4bf -> 0x0007f577
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     0: 0x0007f5bf -> 0x0007f5f0
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     0: 0x0007f5ff -> 0x0007f600
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Using APIC driver default
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr 30 16:23:45 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 16:23:45 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 16:23:45 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr 30 16:23:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr 30 16:23:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 30 16:23:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 30 16:23:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 30 16:23:45 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Apr 30 16:23:45 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u1048576
Apr 30 16:23:45 ubuntu kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
Apr 30 16:23:45 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517420
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu-netbook.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Apr 30 16:23:45 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Initializing CPU#0
Apr 30 16:23:45 ubuntu kernel: [    0.000000] allocated 10434560 bytes of page_cgroup
Apr 30 16:23:45 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f600)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Memory: 2039952k/2086912k available (4673k kernel code, 44808k reserved, 2122k data, 656k init, 1177088k highmem)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 30 16:23:45 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Apr 30 16:23:45 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Apr 30 16:23:45 ubuntu kernel: [    0.000000] console [tty0] enabled
Apr 30 16:23:45 ubuntu kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Apr 30 16:23:45 ubuntu kernel: [    0.000000] Detected 1662.526 MHz processor.
Apr 30 16:23:45 ubuntu kernel: [    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.05 BogoMIPS (lpj=6650104)
Apr 30 16:23:45 ubuntu kernel: [    0.004045] Security Framework initialized
Apr 30 16:23:45 ubuntu kernel: [    0.004085] AppArmor: AppArmor initialized
Apr 30 16:23:45 ubuntu kernel: [    0.004101] Mount-cache hash table entries: 512
Apr 30 16:23:45 ubuntu kernel: [    0.004331] Initializing cgroup subsys ns
Apr 30 16:23:45 ubuntu kernel: [    0.004342] Initializing cgroup subsys cpuacct
Apr 30 16:23:45 ubuntu kernel: [    0.004352] Initializing cgroup subsys memory
Apr 30 16:23:45 ubuntu kernel: [    0.004365] Initializing cgroup subsys devices
Apr 30 16:23:45 ubuntu kernel: [    0.004371] Initializing cgroup subsys freezer
Apr 30 16:23:45 ubuntu kernel: [    0.004376] Initializing cgroup subsys net_cls
Apr 30 16:23:45 ubuntu kernel: [    0.004413] CPU: L1 I cache: 32K, L1 D cache: 24K
Apr 30 16:23:45 ubuntu kernel: [    0.004420] CPU: L2 cache: 512K
Apr 30 16:23:45 ubuntu kernel: [    0.004426] CPU: Physical Processor ID: 0
Apr 30 16:23:45 ubuntu kernel: [    0.004430] CPU: Processor Core ID: 0
Apr 30 16:23:45 ubuntu kernel: [    0.004437] mce: CPU supports 5 MCE banks
Apr 30 16:23:45 ubuntu kernel: [    0.004450] CPU0: Thermal monitoring enabled (TM2)
Apr 30 16:23:45 ubuntu kernel: [    0.004457] using mwait in idle threads.
Apr 30 16:23:45 ubuntu kernel: [    0.004469] Performance Events: Atom events, Intel PMU driver.
Apr 30 16:23:45 ubuntu kernel: [    0.004485] ... version:                3
Apr 30 16:23:45 ubuntu kernel: [    0.004490] ... bit width:              40
Apr 30 16:23:45 ubuntu kernel: [    0.004494] ... generic registers:      2
Apr 30 16:23:45 ubuntu kernel: [    0.004499] ... value mask:             000000ffffffffff
Apr 30 16:23:45 ubuntu kernel: [    0.004504] ... max period:             000000007fffffff
Apr 30 16:23:45 ubuntu kernel: [    0.004509] ... fixed-purpose events:   3
Apr 30 16:23:45 ubuntu kernel: [    0.004513] ... event mask:             0000000700000003
Apr 30 16:23:45 ubuntu kernel: [    0.004522] Checking 'hlt' instruction... OK.
Apr 30 16:23:45 ubuntu kernel: [    0.020007] Disabling 4MB page tables to avoid TLB bug
Apr 30 16:23:45 ubuntu kernel: [    0.024301] ACPI: Core revision 20090903
Apr 30 16:23:45 ubuntu kernel: [    0.044018] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr 30 16:23:45 ubuntu kernel: [    0.044030] ftrace: allocating 21771 entries in 43 pages
Apr 30 16:23:45 ubuntu kernel: [    0.048101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 16:23:45 ubuntu kernel: [    0.048510] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 16:23:45 ubuntu kernel: [    0.088410] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
Apr 30 16:23:45 ubuntu kernel: [    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 30 16:23:45 ubuntu kernel: [    0.008000] Initializing CPU#1
Apr 30 16:23:45 ubuntu kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
Apr 30 16:23:45 ubuntu kernel: [    0.008000] CPU: L2 cache: 512K
Apr 30 16:23:45 ubuntu kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr 30 16:23:45 ubuntu kernel: [    0.008000] CPU: Processor Core ID: 0
Apr 30 16:23:45 ubuntu kernel: [    0.008000] CPU1: Thermal monitoring enabled (TM2)
Apr 30 16:23:45 ubuntu kernel: [    0.176130] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
Apr 30 16:23:45 ubuntu kernel: [    0.176157] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 30 16:23:45 ubuntu kernel: [    0.180034] Brought up 2 CPUs
Apr 30 16:23:45 ubuntu kernel: [    0.180041] Total of 2 processors activated (6650.06 BogoMIPS).
Apr 30 16:23:45 ubuntu kernel: [    0.180576] devtmpfs: initialized
Apr 30 16:23:45 ubuntu kernel: [    0.180576] regulator: core version 0.5
Apr 30 16:23:45 ubuntu kernel: [    0.180576] Time: 16:23:00  Date: 04/30/10
Apr 30 16:23:45 ubuntu kernel: [    0.180576] NET: Registered protocol family 16
Apr 30 16:23:45 ubuntu kernel: [    0.180576] Trying to unpack rootfs image as initramfs...
Apr 30 16:23:45 ubuntu kernel: [    0.180576] EISA bus registered
Apr 30 16:23:45 ubuntu kernel: [    0.180584] ACPI: bus type pci registered
Apr 30 16:23:45 ubuntu kernel: [    0.180752] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr 30 16:23:45 ubuntu kernel: [    0.180761] PCI: MCFG area at e0000000 reserved in E820
Apr 30 16:23:45 ubuntu kernel: [    0.180767] PCI: Using MMCONFIG for extended config space
Apr 30 16:23:45 ubuntu kernel: [    0.180773] PCI: Using configuration type 1 for base access
Apr 30 16:23:45 ubuntu kernel: [    0.185562] bio: create slab <bio-0> at 0
Apr 30 16:23:45 ubuntu kernel: [    0.193420] ACPI: Executed 1 blocks of module-level executable AML code
Apr 30 16:23:45 ubuntu kernel: [    0.196569] ACPI: BIOS _OSI(Linux) query ignored
Apr 30 16:23:45 ubuntu kernel: [    0.198054] ACPI: Interpreter enabled
Apr 30 16:23:45 ubuntu kernel: [    0.198054] ACPI: (supports S0 S3 S4 S5)
Apr 30 16:23:45 ubuntu kernel: [    0.198054] ACPI: Using IOAPIC for interrupt routing
Apr 30 16:23:45 ubuntu kernel: [    0.215628] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Apr 30 16:23:45 ubuntu kernel: [    0.216268] ACPI: No dock devices found.
Apr 30 16:23:45 ubuntu kernel: [    0.217937] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    0.217958] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    0.217984] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Apr 30 16:23:45 ubuntu kernel: [    0.218067] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 16:23:45 ubuntu kernel: [    0.218622] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.218634] pci 0000:00:1b.0: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.218770] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.218781] pci 0000:00:1c.0: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.218922] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.218933] pci 0000:00:1c.1: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.219073] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.219085] pci 0000:00:1c.2: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.219689] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.219700] pci 0000:00:1d.7: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.220163] pci 0000:00:1f.2: PME# supported from D3hot
Apr 30 16:23:45 ubuntu kernel: [    0.220173] pci 0000:00:1f.2: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.220500] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.220512] pci 0000:01:00.0: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.220840] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.220851] pci 0000:02:00.0: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.221281] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.221324] pci 0000:03:00.0: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.221603] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.221646] pci 0000:03:00.1: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.221958] pci 0000:03:00.4: PME# supported from D0 D1 D2 D3hot D3cold
Apr 30 16:23:45 ubuntu kernel: [    0.222001] pci 0000:03:00.4: PME# disabled
Apr 30 16:23:45 ubuntu kernel: [    0.222261] pci 0000:00:1e.0: transparent bridge
Apr 30 16:23:45 ubuntu kernel: [    0.224371] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    0.224391] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    0.246475] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Apr 30 16:23:45 ubuntu kernel: [    0.246823] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
Apr 30 16:23:45 ubuntu kernel: [    0.247168] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Apr 30 16:23:45 ubuntu kernel: [    0.247512] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Apr 30 16:23:45 ubuntu kernel: [    0.247857] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Apr 30 16:23:45 ubuntu kernel: [    0.248230] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Apr 30 16:23:45 ubuntu kernel: [    0.248579] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Apr 30 16:23:45 ubuntu kernel: [    0.248925] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Apr 30 16:23:45 ubuntu kernel: [    0.249304] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Apr 30 16:23:45 ubuntu kernel: [    0.249340] vgaarb: loaded
Apr 30 16:23:45 ubuntu kernel: [    0.249693] SCSI subsystem initialized
Apr 30 16:23:45 ubuntu kernel: [    0.250131] usbcore: registered new interface driver usbfs
Apr 30 16:23:45 ubuntu kernel: [    0.250176] usbcore: registered new interface driver hub
Apr 30 16:23:45 ubuntu kernel: [    0.250260] usbcore: registered new device driver usb
Apr 30 16:23:45 ubuntu kernel: [    0.250671] ACPI: WMI: Mapper loaded
Apr 30 16:23:45 ubuntu kernel: [    0.250678] PCI: Using ACPI for IRQ routing
Apr 30 16:23:45 ubuntu kernel: [    0.251151] NetLabel: Initializing
Apr 30 16:23:45 ubuntu kernel: [    0.251158] NetLabel:  domain hash size = 128
Apr 30 16:23:45 ubuntu kernel: [    0.251163] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 30 16:23:45 ubuntu kernel: [    0.251196] NetLabel:  unlabeled traffic allowed by default
Apr 30 16:23:45 ubuntu kernel: [    0.251303] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 16:23:45 ubuntu kernel: [    0.251319] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr 30 16:23:45 ubuntu kernel: [    4.636173] Switching to clocksource tsc
Apr 30 16:23:45 ubuntu kernel: [    4.641321] AppArmor: AppArmor Filesystem Enabled
Apr 30 16:23:45 ubuntu kernel: [    4.641375] pnp: PnP ACPI init
Apr 30 16:23:45 ubuntu kernel: [    4.641420] ACPI: bus type pnp registered
Apr 30 16:23:45 ubuntu kernel: [    4.647082] pnp: PnP ACPI: found 9 devices
Apr 30 16:23:45 ubuntu kernel: [    4.647093] ACPI: ACPI bus type pnp unregistered
Apr 30 16:23:45 ubuntu kernel: [    4.647104] PnPBIOS: Disabled by ACPI PNP
Apr 30 16:23:45 ubuntu kernel: [    4.647150] system 00:01: ioport range 0x164e-0x164f has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647164] system 00:01: ioport range 0x200-0x20f has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647173] system 00:01: ioport range 0x600-0x60f has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647182] system 00:01: ioport range 0x610-0x610 has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647191] system 00:01: ioport range 0x800-0x80f has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647201] system 00:01: ioport range 0x810-0x817 has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647210] system 00:01: ioport range 0x400-0x47f has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647220] system 00:01: ioport range 0x500-0x53f has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647233] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647244] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647255] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647268] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647282] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647297] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Apr 30 16:23:45 ubuntu kernel: [    4.647310] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 30 16:23:45 ubuntu kernel: [    4.682628] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Apr 30 16:23:45 ubuntu kernel: [    4.682643] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
Apr 30 16:23:45 ubuntu kernel: [    4.682658] pci 0000:00:1c.0:   MEM window: 0x95000000-0x95ffffff
Apr 30 16:23:45 ubuntu kernel: [    4.682671] pci 0000:00:1c.0:   PREFETCH window: 0x00000090000000-0x00000090ffffff
Apr 30 16:23:45 ubuntu kernel: [    4.682689] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Apr 30 16:23:45 ubuntu kernel: [    4.682699] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Apr 30 16:23:45 ubuntu kernel: [    4.682713] pci 0000:00:1c.1:   MEM window: 0x94000000-0x94ffffff
Apr 30 16:23:45 ubuntu kernel: [    4.682726] pci 0000:00:1c.1:   PREFETCH window: 0x00000091000000-0x00000091ffffff
Apr 30 16:23:45 ubuntu kernel: [    4.682744] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
Apr 30 16:23:45 ubuntu kernel: [    4.682755] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
Apr 30 16:23:45 ubuntu kernel: [    4.682769] pci 0000:00:1c.2:   MEM window: 0x93000000-0x93ffffff
Apr 30 16:23:45 ubuntu kernel: [    4.682781] pci 0000:00:1c.2:   PREFETCH window: 0x00000092000000-0x00000092ffffff
Apr 30 16:23:45 ubuntu kernel: [    4.682798] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
Apr 30 16:23:45 ubuntu kernel: [    4.682805] pci 0000:00:1e.0:   IO window: disabled
Apr 30 16:23:45 ubuntu kernel: [    4.682817] pci 0000:00:1e.0:   MEM window: disabled
Apr 30 16:23:45 ubuntu kernel: [    4.682827] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr 30 16:23:45 ubuntu kernel: [    4.682906] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:45 ubuntu kernel: [    4.682966] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 30 16:23:45 ubuntu kernel: [    4.683017] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 30 16:23:45 ubuntu kernel: [    4.683276] NET: Registered protocol family 2
Apr 30 16:23:45 ubuntu kernel: [    4.683563] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 16:23:45 ubuntu kernel: [    4.684558] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 16:23:45 ubuntu kernel: [    4.685708] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 16:23:45 ubuntu kernel: [    4.686295] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 16:23:45 ubuntu kernel: [    4.686309] TCP reno registered
Apr 30 16:23:45 ubuntu kernel: [    4.686594] NET: Registered protocol family 1
Apr 30 16:23:45 ubuntu kernel: [    4.700702] Simple Boot Flag at 0x44 set to 0x1
Apr 30 16:23:45 ubuntu kernel: [    4.701247] cpufreq-nforce2: No nForce2 chipset.
Apr 30 16:23:45 ubuntu kernel: [    4.701346] Scanning for low memory corruption every 60 seconds
Apr 30 16:23:45 ubuntu kernel: [    4.701749] audit: initializing netlink socket (disabled)
Apr 30 16:23:45 ubuntu kernel: [    4.701781] type=2000 audit(1272644583.700:1): initialized
Apr 30 16:23:45 ubuntu kernel: [    4.723121] highmem bounce pool size: 64 pages
Apr 30 16:23:45 ubuntu kernel: [    4.723141] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 30 16:23:45 ubuntu kernel: [    4.728279] VFS: Disk quotas dquot_6.5.2
Apr 30 16:23:45 ubuntu kernel: [    4.728462] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 16:23:45 ubuntu kernel: [    4.730424] fuse init (API version 7.13)
Apr 30 16:23:45 ubuntu kernel: [    4.730704] msgmni has been set to 1687
Apr 30 16:23:45 ubuntu kernel: [    4.730752] Freeing initrd memory: 9145k freed
Apr 30 16:23:45 ubuntu kernel: [    4.732022] alg: No test for stdrng (krng)
Apr 30 16:23:45 ubuntu kernel: [    4.732364] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr 30 16:23:45 ubuntu kernel: [    4.732378] io scheduler noop registered
Apr 30 16:23:45 ubuntu kernel: [    4.732385] io scheduler anticipatory registered
Apr 30 16:23:45 ubuntu kernel: [    4.732391] io scheduler deadline registered
Apr 30 16:23:45 ubuntu kernel: [    4.732780] io scheduler cfq registered (default)
Apr 30 16:23:45 ubuntu kernel: [    4.735036] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 16:23:45 ubuntu kernel: [    4.735462] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.735500] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.736115] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.736145] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.736827] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.736861] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.737614] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.737652] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.738280] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.738315] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.738820] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.738836] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7015750), AE_ALREADY_EXISTS
Apr 30 16:23:45 ubuntu kernel: [    4.738967] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 30 16:23:45 ubuntu kernel: [    4.739175] ACPI: AC Adapter [AC] (on-line)
Apr 30 16:23:45 ubuntu kernel: [    4.739373] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Apr 30 16:23:45 ubuntu kernel: [    4.739388] ACPI: Power Button [PWRB]
Apr 30 16:23:45 ubuntu kernel: [    4.739483] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Apr 30 16:23:45 ubuntu kernel: [    4.739574] ACPI: Lid Switch [LID0]
Apr 30 16:23:45 ubuntu kernel: [    4.739694] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Apr 30 16:23:45 ubuntu kernel: [    4.739701] ACPI: Power Button [PWRF]
Apr 30 16:23:45 ubuntu kernel: [    4.741059] ACPI: SSDT 7f497c90 001F7 (v02   Sony     VAIO 20091207 INTL 20061109)
Apr 30 16:23:45 ubuntu kernel: [    4.741845] ACPI: SSDT 7f496e10 001C1 (v02   Sony     VAIO 20091207 INTL 20061109)
Apr 30 16:23:45 ubuntu kernel: [    4.742581] Marking TSC unstable due to TSC halts in idle
Apr 30 16:23:45 ubuntu kernel: [    4.742695] Switching to clocksource hpet
Apr 30 16:23:45 ubuntu kernel: [    4.742734] processor LNXCPU:00: registered as cooling_device0
Apr 30 16:23:45 ubuntu kernel: [    4.743611] ACPI: SSDT 7f497f10 000D0 (v02   Sony     VAIO 20091207 INTL 20061109)
Apr 30 16:23:45 ubuntu kernel: [    4.744366] ACPI: SSDT 7f495f10 00083 (v02   Sony     VAIO 20091207 INTL 20061109)
Apr 30 16:23:45 ubuntu kernel: [    4.745261] processor LNXCPU:01: registered as cooling_device1
Apr 30 16:23:45 ubuntu kernel: [    4.750527] thermal LNXTHERM:01: registered as thermal_zone0
Apr 30 16:23:45 ubuntu kernel: [    4.750545] ACPI: Thermal Zone [THRM] (64 C)
Apr 30 16:23:45 ubuntu kernel: [    4.751008] isapnp: Scanning for PnP cards...
Apr 30 16:23:45 ubuntu kernel: [    4.755302] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 30 16:23:45 ubuntu kernel: [    4.755478] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 30 16:23:45 ubuntu kernel: [    4.759061] brd: module loaded
Apr 30 16:23:45 ubuntu kernel: [    4.760466] loop: module loaded
Apr 30 16:23:45 ubuntu kernel: [    4.760742] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr 30 16:23:45 ubuntu kernel: [    4.761020] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 30 16:23:45 ubuntu kernel: [    4.761032] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Apr 30 16:23:45 ubuntu kernel: [    4.916914] scsi0 : ata_piix
Apr 30 16:23:45 ubuntu kernel: [    4.917179] scsi1 : ata_piix
Apr 30 16:23:45 ubuntu kernel: [    4.918340] ata1: SATA max UDMA/133 cmd 0x50b8 ctl 0x50cc bmdma 0x50a0 irq 17
Apr 30 16:23:45 ubuntu kernel: [    4.918350] ata2: SATA max UDMA/133 cmd 0x50b0 ctl 0x50c8 bmdma 0x50a8 irq 17
Apr 30 16:23:45 ubuntu kernel: [    4.919379] Fixed MDIO Bus: probed
Apr 30 16:23:45 ubuntu kernel: [    4.919485] PPP generic driver version 2.4.2
Apr 30 16:23:45 ubuntu kernel: [    4.919610] tun: Universal TUN/TAP device driver, 1.6
Apr 30 16:23:45 ubuntu kernel: [    4.919616] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 30 16:23:45 ubuntu kernel: [    4.919862] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 30 16:23:45 ubuntu kernel: [    4.919909] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:45 ubuntu kernel: [    4.919948] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 16:23:45 ubuntu kernel: [    4.920082] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Apr 30 16:23:45 ubuntu kernel: [    4.920125] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Apr 30 16:23:45 ubuntu kernel: [    4.920148] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 16:23:45 ubuntu kernel: [    4.924101] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x96204400
Apr 30 16:23:45 ubuntu kernel: [    4.936042] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr 30 16:23:45 ubuntu kernel: [    4.936290] usb usb1: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    4.936381] hub 1-0:1.0: USB hub found
Apr 30 16:23:45 ubuntu kernel: [    4.936409] hub 1-0:1.0: 8 ports detected
Apr 30 16:23:45 ubuntu kernel: [    4.936573] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 30 16:23:45 ubuntu kernel: [    4.936616] uhci_hcd: USB Universal Host Controller Interface driver
Apr 30 16:23:45 ubuntu kernel: [    4.936688] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:45 ubuntu kernel: [    4.936715] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 16:23:45 ubuntu kernel: [    4.936815] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Apr 30 16:23:45 ubuntu kernel: [    4.936859] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00005080
Apr 30 16:23:45 ubuntu kernel: [    4.937162] usb usb2: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    4.937240] hub 2-0:1.0: USB hub found
Apr 30 16:23:45 ubuntu kernel: [    4.937260] hub 2-0:1.0: 2 ports detected
Apr 30 16:23:45 ubuntu kernel: [    4.937368] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 30 16:23:45 ubuntu kernel: [    4.937391] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 16:23:45 ubuntu kernel: [    4.937483] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Apr 30 16:23:45 ubuntu kernel: [    4.937525] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005060
Apr 30 16:23:45 ubuntu kernel: [    4.937776] usb usb3: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    4.937853] hub 3-0:1.0: USB hub found
Apr 30 16:23:45 ubuntu kernel: [    4.937872] hub 3-0:1.0: 2 ports detected
Apr 30 16:23:45 ubuntu kernel: [    4.937981] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 30 16:23:45 ubuntu kernel: [    4.938003] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 16:23:45 ubuntu kernel: [    4.938090] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Apr 30 16:23:45 ubuntu kernel: [    4.938147] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005040
Apr 30 16:23:45 ubuntu kernel: [    4.938383] usb usb4: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    4.938459] hub 4-0:1.0: USB hub found
Apr 30 16:23:45 ubuntu kernel: [    4.938478] hub 4-0:1.0: 2 ports detected
Apr 30 16:23:45 ubuntu kernel: [    4.938603] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Apr 30 16:23:45 ubuntu kernel: [    4.938626] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 16:23:45 ubuntu kernel: [    4.938716] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Apr 30 16:23:45 ubuntu kernel: [    4.938770] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00005020
Apr 30 16:23:45 ubuntu kernel: [    4.939012] usb usb5: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    4.939089] hub 5-0:1.0: USB hub found
Apr 30 16:23:45 ubuntu kernel: [    4.939108] hub 5-0:1.0: 2 ports detected
Apr 30 16:23:45 ubuntu kernel: [    4.939337] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
Apr 30 16:23:45 ubuntu kernel: [    4.943082] i8042.c: Detected active multiplexing controller, rev 1.1.
Apr 30 16:23:45 ubuntu kernel: [    4.944468] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 16:23:45 ubuntu kernel: [    4.944489] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr 30 16:23:45 ubuntu kernel: [    4.944568] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr 30 16:23:45 ubuntu kernel: [    4.944639] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr 30 16:23:45 ubuntu kernel: [    4.944708] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr 30 16:23:45 ubuntu kernel: [    4.945113] mice: PS/2 mouse device common for all mice
Apr 30 16:23:45 ubuntu kernel: [    4.945468] rtc_cmos 00:03: RTC can wake from S4
Apr 30 16:23:45 ubuntu kernel: [    4.945573] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Apr 30 16:23:45 ubuntu kernel: [    4.945623] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Apr 30 16:23:45 ubuntu kernel: [    4.945929] device-mapper: uevent: version 1.0.3
Apr 30 16:23:45 ubuntu kernel: [    4.946220] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr 30 16:23:45 ubuntu kernel: [    4.946407] device-mapper: multipath: version 1.1.0 loaded
Apr 30 16:23:45 ubuntu kernel: [    4.946415] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 30 16:23:45 ubuntu kernel: [    4.946741] EISA: Probing bus 0 at eisa.0
Apr 30 16:23:45 ubuntu kernel: [    4.946759] Cannot allocate resource for EISA slot 2
Apr 30 16:23:45 ubuntu kernel: [    4.946766] Cannot allocate resource for EISA slot 3
Apr 30 16:23:45 ubuntu kernel: [    4.946772] Cannot allocate resource for EISA slot 4
Apr 30 16:23:45 ubuntu kernel: [    4.946778] Cannot allocate resource for EISA slot 5
Apr 30 16:23:45 ubuntu kernel: [    4.946801] EISA: Detected 0 cards.
Apr 30 16:23:45 ubuntu kernel: [    4.947210] cpuidle: using governor ladder
Apr 30 16:23:45 ubuntu kernel: [    4.947536] cpuidle: using governor menu
Apr 30 16:23:45 ubuntu kernel: [    4.948783] TCP cubic registered
Apr 30 16:23:45 ubuntu kernel: [    4.949264] NET: Registered protocol family 10
Apr 30 16:23:45 ubuntu kernel: [    4.950497] lo: Disabled Privacy Extensions
Apr 30 16:23:45 ubuntu kernel: [    4.951374] NET: Registered protocol family 17
Apr 30 16:23:45 ubuntu kernel: [    4.952562] Using IPI No-Shortcut mode
Apr 30 16:23:45 ubuntu kernel: [    4.952830] registered taskstats version 1
Apr 30 16:23:45 ubuntu kernel: [    4.953702]   Magic number: 6:761:389
Apr 30 16:23:45 ubuntu kernel: [    4.953835] rtc_cmos 00:03: setting system clock to 2010-04-30 16:23:04 UTC (1272644584)
Apr 30 16:23:45 ubuntu kernel: [    4.953844] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 16:23:45 ubuntu kernel: [    4.953850] EDD information not available.
Apr 30 16:23:45 ubuntu kernel: [    4.980311] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr 30 16:23:45 ubuntu kernel: [    5.098589] ata1.00: ATA-8: SAMSUNG HM320II, 2AC101C4, max UDMA/133
Apr 30 16:23:45 ubuntu kernel: [    5.098599] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 30 16:23:45 ubuntu kernel: [    5.105582] isapnp: No Plug & Play device found
Apr 30 16:23:45 ubuntu kernel: [    5.120731] ata1.00: configured for UDMA/133
Apr 30 16:23:45 ubuntu kernel: [    5.121017] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM320II  2AC1 PQ: 0 ANSI: 5
Apr 30 16:23:45 ubuntu kernel: [    5.121324] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Apr 30 16:23:45 ubuntu kernel: [    5.121369] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 16:23:45 ubuntu kernel: [    5.121500] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 16:23:45 ubuntu kernel: [    5.121593] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 16:23:45 ubuntu kernel: [    5.121939]  sda:
Apr 30 16:23:45 ubuntu kernel: [    5.202765] ACPI: Battery Slot [BAT1] (battery present)
Apr 30 16:23:45 ubuntu kernel: [    5.248083] usb 1-1: new high speed USB device using ehci_hcd and address 2
Apr 30 16:23:45 ubuntu kernel: [    5.382496] usb 1-1: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    5.492084] usb 1-8: new high speed USB device using ehci_hcd and address 3
Apr 30 16:23:45 ubuntu kernel: [    5.560447]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
Apr 30 16:23:45 ubuntu kernel: [    5.611735] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 16:23:45 ubuntu kernel: [    5.611807] Freeing unused kernel memory: 656k freed
Apr 30 16:23:45 ubuntu kernel: [    5.612366] Write protecting the kernel text: 4676k
Apr 30 16:23:45 ubuntu kernel: [    5.612439] Write protecting the kernel read-only data: 1840k
Apr 30 16:23:45 ubuntu kernel: [    5.629175] usb 1-8: configuration #1 chosen from 1 choice
Apr 30 16:23:45 ubuntu kernel: [    5.658324] udev: starting version 151
Apr 30 16:23:45 ubuntu kernel: [    5.982712] Linux agpgart interface v0.103
Apr 30 16:23:45 ubuntu kernel: [    6.028227] agpgart-intel 0000:00:00.0: Intel IGD Chipset
Apr 30 16:23:45 ubuntu kernel: [    6.028661] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
Apr 30 16:23:45 ubuntu kernel: [    6.050108] Initializing USB Mass Storage driver...
Apr 30 16:23:45 ubuntu kernel: [    6.050305] usbcore: registered new interface driver usb-storage
Apr 30 16:23:45 ubuntu kernel: [    6.050316] USB Mass Storage support registered.
Apr 30 16:23:45 ubuntu kernel: [    6.055263] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
Apr 30 16:23:45 ubuntu kernel: [    6.055760] scsi2 : SCSI emulation for USB Mass Storage devices
Apr 30 16:23:45 ubuntu kernel: [    6.056106] usbcore: registered new interface driver ums-cypress
Apr 30 16:23:45 ubuntu kernel: [    6.146608] [drm] Initialized drm 1.1.0 20060810
Apr 30 16:23:45 ubuntu kernel: [    6.209548] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:45 ubuntu kernel: [    6.223209] [drm] set up 7M of stolen space
Apr 30 16:23:45 ubuntu kernel: [    6.228713] [drm] initialized overlay support
Apr 30 16:23:45 ubuntu kernel: [    6.584856] fb0: inteldrmfb frame buffer device
Apr 30 16:23:45 ubuntu kernel: [    6.584863] registered panic notifier
Apr 30 16:23:45 ubuntu kernel: [    6.586401] ACPI Warning: _BQC returned an invalid level (20090903/video-631)
Apr 30 16:23:45 ubuntu kernel: [    6.587875] acpi device:22: registered as cooling_device2
Apr 30 16:23:45 ubuntu kernel: [    6.588854] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Apr 30 16:23:45 ubuntu kernel: [    6.588987] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
Apr 30 16:23:45 ubuntu kernel: [    6.589042] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 30 16:23:45 ubuntu kernel: [    6.595374] vga16fb: mapped to 0xc00a0000
Apr 30 16:23:45 ubuntu kernel: [    6.595383] vga16fb: not registering due to another framebuffer present
Apr 30 16:23:45 ubuntu kernel: [    6.612203] [drm] Big FIFO is enabled
Apr 30 16:23:45 ubuntu kernel: [    6.680080] [drm] Big FIFO is enabled
Apr 30 16:23:45 ubuntu kernel: [    6.680103] [drm] Big FIFO is enabled
Apr 30 16:23:45 ubuntu kernel: [    6.972082] [drm] Big FIFO is enabled
Apr 30 16:23:45 ubuntu kernel: [    7.004741] Console: switching to colour frame buffer device 170x48
Apr 30 16:23:45 ubuntu kernel: [    7.357858] [drm] Big FIFO is enabled
Apr 30 16:23:45 ubuntu kernel: [    7.380348] [drm] Big FIFO is enabled
Apr 30 16:23:45 ubuntu kernel: [    7.630726] xor: automatically using best checksumming function: pIII_sse
Apr 30 16:23:45 ubuntu kernel: [    7.648509]    pIII_sse  :  4889.000 MB/sec
Apr 30 16:23:45 ubuntu kernel: [    7.648516] xor: using function: pIII_sse (4889.000 MB/sec)
Apr 30 16:23:45 ubuntu kernel: [    7.657339] device-mapper: dm-raid45: initialized v0.2594b
Apr 30 16:23:45 ubuntu kernel: [    8.820627] EXT4-fs (sda5): mounted filesystem with ordered data mode
Apr 30 16:23:45 ubuntu kernel: [    9.103362] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 30 16:23:45 ubuntu kernel: [   11.059712] scsi 2:0:0:0: Direct-Access     ST96812A                  0000 PQ: 0 ANSI: 0
Apr 30 16:23:45 ubuntu kernel: [   11.061954] sd 2:0:0:0: Attached scsi generic sg1 type 0
Apr 30 16:23:45 ubuntu kernel: [   11.062988] sd 2:0:0:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
Apr 30 16:23:45 ubuntu kernel: [   11.063947] sd 2:0:0:0: [sdb] Write Protect is off
Apr 30 16:23:45 ubuntu kernel: [   11.066081]  sdb: sdb1
Apr 30 16:23:45 ubuntu kernel: [   11.086854] sd 2:0:0:0: [sdb] Attached SCSI disk
Apr 30 16:23:45 ubuntu kernel: [   12.706569] aufs 2-standalone.tree-20091207
Apr 30 16:23:45 ubuntu kernel: [   12.742917] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Apr 30 16:23:45 ubuntu kernel: [   46.019071] Adding 3903752k swap on /dev/sda6.  Priority:-1 extents:1 across:3903752k 
Apr 30 16:23:45 ubuntu kernel: [   46.286621] udev: starting version 151
Apr 30 16:23:46 ubuntu kernel: [   46.897616] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:46 ubuntu kernel: [   46.973528] sdhci: Secure Digital Host Controller Interface driver
Apr 30 16:23:46 ubuntu kernel: [   46.973538] sdhci: Copyright(c) Pierre Ossman
Apr 30 16:23:46 ubuntu kernel: [   47.021957] atl1c 0000:01:00.0: version 1.0.0.1-NAPI
Apr 30 16:23:46 ubuntu kernel: [   47.121465] cfg80211: Calling CRDA to update world regulatory domain
Apr 30 16:23:46 ubuntu kernel: [   47.137851] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
Apr 30 16:23:46 ubuntu kernel: [   47.137984] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 30 16:23:46 ubuntu kernel: [   47.138075] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 30 16:23:46 ubuntu kernel: [   47.139642] Registered led device: mmc0::
Apr 30 16:23:46 ubuntu kernel: [   47.141127] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
Apr 30 16:23:46 ubuntu kernel: [   47.141693] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
Apr 30 16:23:46 ubuntu kernel: [   47.141765] sdhci-pci 0000:03:00.4: PCI INT C -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:46 ubuntu kernel: [   47.141897] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 30 16:23:46 ubuntu kernel: [   47.147220] Linux video capture interface: v2.00
Apr 30 16:23:46 ubuntu kernel: [   47.149424] Registered led device: mmc1::
Apr 30 16:23:46 ubuntu kernel: [   47.151545] mmc1: SDHCI controller on PCI [0000:03:00.4] using DMA
Apr 30 16:23:46 ubuntu kernel: [   47.336688] uvcvideo: Found UVC 1.00 device <unnamed> (04f2:b15c)
Apr 30 16:23:46 ubuntu kernel: [   47.364986] input: UVC Camera (04f2:b15c) as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
Apr 30 16:23:46 ubuntu kernel: [   47.365635] usbcore: registered new interface driver uvcvideo
Apr 30 16:23:46 ubuntu kernel: [   47.365912] USB Video Class driver (v0.1.0)
Apr 30 16:23:47 ubuntu kernel: [   47.691374] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 30 16:23:47 ubuntu kernel: [   47.785005] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04751/0xa00000
Apr 30 16:23:47 ubuntu kernel: [   47.797602] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Apr 30 16:23:47 ubuntu kernel: [   47.797620] Descriptor sense data with sense descriptors (in hex):
Apr 30 16:23:47 ubuntu kernel: [   47.797628]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Apr 30 16:23:47 ubuntu kernel: [   47.797658]         00 00 00 00 e0 50 
Apr 30 16:23:47 ubuntu kernel: [   47.797673] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
Apr 30 16:23:47 ubuntu kernel: [   47.816197] cfg80211: World regulatory domain updated:
Apr 30 16:23:47 ubuntu kernel: [   47.816207] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 30 16:23:47 ubuntu kernel: [   47.816217] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 30 16:23:47 ubuntu kernel: [   47.816226] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 30 16:23:47 ubuntu kernel: [   47.816235] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 30 16:23:47 ubuntu kernel: [   47.816243] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 30 16:23:47 ubuntu kernel: [   47.816251] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 30 16:23:47 ubuntu kernel: [   47.836656] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Apr 30 16:23:47 ubuntu kernel: [   47.885933] sony-laptop: Sony Notebook Control Driver v0.6.
Apr 30 16:23:47 ubuntu kernel: [   47.943673] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input8
Apr 30 16:23:47 ubuntu kernel: [   47.945992] input: Sony Vaio Jogdial as /devices/virtual/input/input9
Apr 30 16:23:47 ubuntu kernel: [   47.946293] sony-laptop: brightness ignored, must be controlled by ACPI video driver
Apr 30 16:23:47 ubuntu kernel: [   48.067777] Registered led device: ath9k-phy0::radio
Apr 30 16:23:47 ubuntu kernel: [   48.067841] Registered led device: ath9k-phy0::assoc
Apr 30 16:23:47 ubuntu kernel: [   48.067902] Registered led device: ath9k-phy0::tx
Apr 30 16:23:47 ubuntu kernel: [   48.067965] Registered led device: ath9k-phy0::rx
Apr 30 16:23:47 ubuntu kernel: [   48.068080] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8ac0000, irq=17
Apr 30 16:23:47 ubuntu kernel: [   48.251148] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 16:23:47 ubuntu kernel: [   48.422689] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 30 16:23:48 ubuntu kernel: [   48.520134] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Apr 30 16:23:48 ubuntu kernel: [   48.520718] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 30 16:23:48 ubuntu kernel: [   48.932937] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 30 16:23:48 ubuntu kernel: [   49.082424] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Apr 30 16:23:50 ubuntu kernel: [   50.495001] lp: driver loaded but no devices found
Apr 30 16:23:50 ubuntu kernel: [   50.623298] ppdev: user-space parallel port driver
Apr 30 14:23:59 ubuntu ubiquity[2828]: Ubiquity 2.2.24
Apr 30 14:24:03 ubuntu ubiquity[2828]: log-output -t ubiquity laptop-detect
Apr 30 14:24:07 ubuntu ubiquity[2828]: log-output -t ubiquity laptop-detect
Apr 30 14:24:12 ubuntu ubiquity[2828]: switched to page language
Apr 30 14:24:16 ubuntu ubiquity[2828]: switched to page language
Apr 30 14:24:27 ubuntu localechooser: info: Language = 'en'
Apr 30 14:24:27 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Apr 30 14:24:27 ubuntu localechooser: info: Set debian-installer/language = 'en'
Apr 30 14:24:27 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 14:24:27 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Apr 30 14:24:27 ubuntu localechooser: info: Default country = 'US'
Apr 30 14:24:27 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Apr 30 14:24:27 ubuntu localechooser: info: Set debian-installer/country = 'US'
Apr 30 14:24:27 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 14:24:27 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Apr 30 14:24:44 ubuntu ubiquity[2828]: log-output -t ubiquity setupcon --save-only
Apr 30 14:24:44 ubuntu ubiquity[2828]: log-output -t ubiquity udevadm trigger --subsystem-match=input --action=change
Apr 30 14:24:44 ubuntu ubiquity[2828]: log-output -t ubiquity udevadm settle
Apr 30 14:24:45 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Apr 30 14:24:45 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Apr 30 14:24:46 ubuntu kernel: [  105.983413] [drm] Big FIFO is enabled
Apr 30 14:24:48 ubuntu kernel: [  108.649858] [drm] Big FIFO is enabled
Apr 30 14:25:08 ubuntu kernel: [  128.485579] EXT4-fs (sda5): mounted filesystem with ordered data mode

---

