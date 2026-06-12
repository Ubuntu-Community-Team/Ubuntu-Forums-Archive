---
title: "full memory not detected"
date: 2011-07-06
forum: General Help
---

### Post by rng on 2011-07-06
I have 4gb memory on my computer (correctly detected by windows) but only 3.3 gb is detected by ubuntu. What could be the reason and how to sort this out? Please help.

---

### Post by oldos2er on 2011-07-06
One reason would be you installed a 32-bit OS. You can either install a 64-bit OS, or the PAE kernel. Which version of Ubuntu did you install?

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by dFlyer on 2011-07-06
If you have a 32bit system you need to install the pae kernel

---

### Post by psusi on 2011-07-06
32bit Windows also will not see the full ram.  Depending on which screen you look at though, it may claim to.  I don't remember which one it was, but one of the screens reports that you have 4gb of ram installed, but if you look at the total in the task manager it will usually be 3.2 gb.  Microshaft also won't allow you to enable PAE on Windows 7 except on server edition.

---

### Post by rng on 2011-07-07
Thanks for your replies and links. 

I am using ubuntu 10.04 LTS 32bit version. My win7 is 64 bit version. Should I try ubuntu 64-bit version or enable PAE in my current system? I am otherwise very happy with my current installation of ubuntu.

---

### Post by Mr Nemo on 2011-07-07
If youre happy with your current system, I say just install the PAE kernel.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) - here's how

---

### Post by wildmanne39 on 2011-07-07
> **rng said:**
> Thanks for your replies and links. 

I am using ubuntu 10.04 LTS 32bit version. My win7 is 64 bit version. Should I try ubuntu 64-bit version or enable PAE in my current system? I am otherwise very happy with my current installation of ubuntu.
Hi, it is up to you, whichever you think is easier, I have used 64 bit for more then four years now and I like it, but if you install 64 bit you can not upgrade you have to do a clean install. It has been a long time since I updated a kernel so I do not remember how much trouble that will be.

---

### Post by rng on 2011-07-07
Thanks. I will enable PAE later today and report back.

---

### Post by holadebob on 2011-07-07
Just read the post, have identical situation with 3.2gB ram showing, so installed the pae kernal. Everything seems fine and the system monitor shows the pae kernal, but it still shows 3.2 gB available. Any suggestions?

---

### Post by psusi on 2011-07-07
> **holadebob said:**
> Just read the post, have identical situation with 3.2gB ram showing, so installed the pae kernal. Everything seems fine and the system monitor shows the pae kernal, but it still shows 3.2 gB available. Any suggestions?

Most likely your motherboard/bios don't support it.  You can take a look at the bios e820 memory map in the output of dmesg to confirm.

---

### Post by holadebob on 2011-07-07
psusi, thanks for your time....

I can't find the reference e820 mem map. Interesting read, though. 

I did find something strange, though, probably of no consequence on line 1.492948 says stolen memory?



[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at cf800000 (gap: cf800000:20800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36312 r0 d21032 u2097152
[    0.000000] pcpu-alloc: s36312 r0 d21032 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 843163
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=16151e43-880b-4a30-a022-3733aced5a8b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 16998080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000cf7f0)
[    0.000000] Memory: 3332628k/3399616k available (4674k kernel code, 65544k reserved, 2120k data, 668k init, 2490312k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc084a000   ( 668 kB)
[    0.000000]       .data : 0xc0590ad7 - 0xc07a2d88   (2120 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590ad7   (4674 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2799.946 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.89 BogoMIPS (lpj=11199784)
[    0.004030] Security Framework initialized
[    0.004057] AppArmor: AppArmor initialized
[    0.004069] Mount-cache hash table entries: 512
[    0.004248] Initializing cgroup subsys ns
[    0.004255] Initializing cgroup subsys cpuacct
[    0.004261] Initializing cgroup subsys memory
[    0.004271] Initializing cgroup subsys devices
[    0.004274] Initializing cgroup subsys freezer
[    0.004278] Initializing cgroup subsys net_cls
[    0.004314] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004319] CPU: L2 cache: 256K
[    0.004322] CPU: Hyper-Threading is disabled
[    0.004327] mce: CPU supports 4 MCE banks
[    0.004344] CPU0: Thermal monitoring enabled (TM2)
[    0.004350] using mwait in idle threads.
[    0.004359] Performance Events: no PMU driver, software events only.
[    0.004368] Checking 'hlt' instruction... OK.
[    0.021233] SMP alternatives: switching to UP code
[    0.034858] ACPI: Core revision 20090903
[    0.044015] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044024] ftrace: allocating 21723 entries in 43 pages
[    0.048100] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088720] CPU0: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (5599.89 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  8:19:39  Date: 07/07/11
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.092001] PCI: MCFG area at f0000000 reserved in E820
[    0.092001] PCI: Using MMCONFIG for extended config space
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092001] bio: create slab <bio-0> at 0
[    0.092001] ACPI: EC: Look up EC in DSDT
[    0.097772] ACPI: Interpreter enabled
[    0.097781] ACPI: (supports S0 S1 S4 S5)
[    0.097813] ACPI: Using IOAPIC for interrupt routing
[    0.103811] ACPI: No dock devices found.
[    0.103964] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.104126] pci 0000:00:02.0: reg 10 32bit mmio: [0xe2000000-0xe207ffff]
[    0.104134] pci 0000:00:02.0: reg 14 io port: [0xc000-0xc007]
[    0.104141] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.104147] pci 0000:00:02.0: reg 1c 32bit mmio: [0xe2080000-0xe20bffff]
[    0.104278] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.104283] pci 0000:00:1c.0: PME# disabled
[    0.104366] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.104371] pci 0000:00:1c.1: PME# disabled
[    0.104434] pci 0000:00:1d.0: reg 20 io port: [0xb000-0xb01f]
[    0.104495] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.104556] pci 0000:00:1d.2: reg 20 io port: [0xb800-0xb81f]
[    0.104616] pci 0000:00:1d.3: reg 20 io port: [0xbc00-0xbc1f]
[    0.104673] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe20c0000-0xe20c03ff]
[    0.104878] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.104883] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.104946] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.104954] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.104962] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.104969] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.104977] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.105008] pci 0000:00:1f.2: PME# supported from D3hot
[    0.105012] pci 0000:00:1f.2: PME# disabled
[    0.105066] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.105146] pci 0000:00:1c.0: bridge io port: [0x8000-0x8fff]
[    0.105228] pci 0000:02:00.0: reg 10 io port: [0x9000-0x90ff]
[    0.105255] pci 0000:02:00.0: reg 18 64bit mmio: [0xe1000000-0xe1000fff]
[    0.105282] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.105337] pci 0000:02:00.0: supports D1 D2
[    0.105340] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.105346] pci 0000:02:00.0: PME# disabled
[    0.105410] pci 0000:00:1c.1: bridge io port: [0x9000-0x9fff]
[    0.105415] pci 0000:00:1c.1: bridge 32bit mmio: [0xe0000000-0xe1ffffff]
[    0.105467] pci 0000:03:01.0: reg 10 io port: [0xa000-0xa01f]
[    0.105523] pci 0000:03:01.0: supports D1 D2
[    0.105575] pci 0000:00:1e.0: transparent bridge
[    0.105580] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.105606] pci_bus 0000:00: on NUMA node 0
[    0.105616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.105867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.105955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.106055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.117307] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.117448] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.117582] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.117715] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.117849] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.117985] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.118124] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.118262] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.118425] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.118437] vgaarb: loaded
[    0.118618] SCSI subsystem initialized
[    0.118714] libata version 3.00 loaded.
[    0.118840] usbcore: registered new interface driver usbfs
[    0.118859] usbcore: registered new interface driver hub
[    0.118906] usbcore: registered new device driver usb
[    0.119145] ACPI: WMI: Mapper loaded
[    0.119149] PCI: Using ACPI for IRQ routing
[    0.119349] NetLabel: Initializing
[    0.119353] NetLabel:  domain hash size = 128
[    0.119355] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.119372] NetLabel:  unlabeled traffic allowed by default
[    0.119429] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.119437] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.119444] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.124031] Switching to clocksource tsc
[    0.126442] AppArmor: AppArmor Filesystem Enabled
[    0.126468] pnp: PnP ACPI init
[    0.126494] ACPI: bus type pnp registered
[    0.129999] pnp: PnP ACPI: found 13 devices
[    0.130003] ACPI: ACPI bus type pnp unregistered
[    0.130010] PnPBIOS: Disabled by ACPI PNP
[    0.130027] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.130032] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.130035] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.130039] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.130043] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.130055] system 00:09: ioport range 0x400-0x4bf has been reserved
[    0.130064] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.130072] system 00:0b: iomem range 0xca800-0xcbfff has been reserved
[    0.130077] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.130081] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.130085] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.130089] system 00:0b: iomem range 0xcf7f0000-0xcf7fffff could not be reserved
[    0.130093] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.130097] system 00:0b: iomem range 0x100000-0xcf7effff could not be reserved
[    0.130101] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.130105] system 00:0b: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.130109] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.130113] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.130117] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.130125] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.130129] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.164944] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.164950] pci 0000:00:1c.0:   IO window: 0x8000-0x8fff
[    0.164957] pci 0000:00:1c.0:   MEM window: 0xe2100000-0xe22fffff
[    0.164963] pci 0000:00:1c.0:   PREFETCH window: 0x000000e2300000-0x000000e24fffff
[    0.164972] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.164976] pci 0000:00:1c.1:   IO window: 0x9000-0x9fff
[    0.164982] pci 0000:00:1c.1:   MEM window: 0xe0000000-0xe1ffffff
[    0.164987] pci 0000:00:1c.1:   PREFETCH window: 0xe2500000-0xe26fffff
[    0.164995] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.164999] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.165005] pci 0000:00:1e.0:   MEM window: disabled
[    0.165010] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.165034]   alloc irq_desc for 16 on node -1
[    0.165037]   alloc kstat_irqs on node -1
[    0.165045] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.165052] pci 0000:00:1c.0: setting latency timer to 64
[    0.165063]   alloc irq_desc for 17 on node -1
[    0.165065]   alloc kstat_irqs on node -1
[    0.165070] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.165075] pci 0000:00:1c.1: setting latency timer to 64
[    0.165084] pci 0000:00:1e.0: setting latency timer to 64
[    0.165090] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.165093] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.165098] pci_bus 0000:01: resource 0 io:  [0x8000-0x8fff]
[    0.165101] pci_bus 0000:01: resource 1 mem: [0xe2100000-0xe22fffff]
[    0.165104] pci_bus 0000:01: resource 2 pref mem [0xe2300000-0xe24fffff]
[    0.165107] pci_bus 0000:02: resource 0 io:  [0x9000-0x9fff]
[    0.165110] pci_bus 0000:02: resource 1 mem: [0xe0000000-0xe1ffffff]
[    0.165114] pci_bus 0000:02: resource 2 pref mem [0xe2500000-0xe26fffff]
[    0.165117] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.165120] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.165123] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.165173] NET: Registered protocol family 2
[    0.165303] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.165748] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.166404] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.166740] TCP: Hash tables configured (established 131072 bind 65536)
[    0.166746] TCP reno registered
[    0.166885] NET: Registered protocol family 1
[    0.166920] pci 0000:00:02.0: Boot video device
[    0.167258] cpufreq-nforce2: No nForce2 chipset.
[    0.167299] Scanning for low memory corruption every 60 seconds
[    0.167466] audit: initializing netlink socket (disabled)
[    0.167482] type=2000 audit(1310026779.163:1): initialized
[    0.176911] Trying to unpack rootfs image as initramfs...
[    0.188257] highmem bounce pool size: 64 pages
[    0.188268] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.196326] VFS: Disk quotas dquot_6.5.2
[    0.196442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.197295] fuse init (API version 7.13)
[    0.197448] msgmni has been set to 1647
[    0.197786] alg: No test for stdrng (krng)
[    0.197894] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.197899] io scheduler noop registered
[    0.197901] io scheduler anticipatory registered
[    0.197904] io scheduler deadline registered
[    0.197968] io scheduler cfq registered (default)
[    0.198146]   alloc irq_desc for 24 on node -1
[    0.198150]   alloc kstat_irqs on node -1
[    0.198163] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.198174] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.198334]   alloc irq_desc for 25 on node -1
[    0.198338]   alloc kstat_irqs on node -1
[    0.198349] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.198359] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.198489] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.198596] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.198717] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.198723] ACPI: Power Button [PWRB]
[    0.198794] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.198798] ACPI: Power Button [PWRF]
[    0.199162] processor LNXCPU:00: registered as cooling_device0
[    0.201496] isapnp: Scanning for PnP cards...
[    0.212381] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.212503] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.212992] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.214457] brd: module loaded
[    0.215125] loop: module loaded
[    0.215273] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.215420] ata_piix 0000:00:1f.2: version 2.13
[    0.215448]   alloc irq_desc for 19 on node -1
[    0.215451]   alloc kstat_irqs on node -1
[    0.215459] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.215467] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.215520] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.220050] scsi0 : ata_piix
[    0.263705] scsi1 : ata_piix
[    0.264778] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.264783] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.265312] Fixed MDIO Bus: probed
[    0.265363] PPP generic driver version 2.4.2
[    0.265453] tun: Universal TUN/TAP device driver, 1.6
[    0.265457] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.265607] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.265647]   alloc irq_desc for 23 on node -1
[    0.265650]   alloc kstat_irqs on node -1
[    0.265659] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.265680] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.265685] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.265748] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.265781] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.269664] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.275963] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe20c0000
[    0.288106] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.288293] usb usb1: configuration #1 chosen from 1 choice
[    0.288338] hub 1-0:1.0: USB hub found
[    0.288352] hub 1-0:1.0: 8 ports detected
[    0.288440] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.288463] uhci_hcd: USB Universal Host Controller Interface driver
[    0.288519] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.288530] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.288535] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.288612] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.288645] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b000
[    0.288791] usb usb2: configuration #1 chosen from 1 choice
[    0.288830] hub 2-0:1.0: USB hub found
[    0.288843] hub 2-0:1.0: 2 ports detected
[    0.288910] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.288920] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.288925] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.288983] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.289024] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.289163] usb usb3: configuration #1 chosen from 1 choice
[    0.289202] hub 3-0:1.0: USB hub found
[    0.289213] hub 3-0:1.0: 2 ports detected
[    0.289281]   alloc irq_desc for 18 on node -1
[    0.289284]   alloc kstat_irqs on node -1
[    0.289293] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.289304] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.289309] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.289376] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.289417] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    0.289565] usb usb4: configuration #1 chosen from 1 choice
[    0.289605] hub 4-0:1.0: USB hub found
[    0.289617] hub 4-0:1.0: 2 ports detected
[    0.289688] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.289699] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.289703] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.289779] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.289821] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bc00
[    0.289968] usb usb5: configuration #1 chosen from 1 choice
[    0.290009] hub 5-0:1.0: USB hub found
[    0.290020] hub 5-0:1.0: 2 ports detected
[    0.290158] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.290161] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.290375] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.290580] mice: PS/2 mouse device common for all mice
[    0.290786] rtc_cmos 00:03: RTC can wake from S4
[    0.290868] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.290901] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.291065] device-mapper: uevent: version 1.0.3
[    0.293823] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.295467] device-mapper: multipath: version 1.1.0 loaded
[    0.295474] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.298178] EISA: Probing bus 0 at eisa.0
[    0.298210] Cannot allocate resource for EISA slot 8
[    0.298214] EISA: Detected 0 cards.
[    0.298317] cpuidle: using governor ladder
[    0.298322] cpuidle: using governor menu
[    0.298851] TCP cubic registered
[    0.299032] NET: Registered protocol family 10
[    0.299631] lo: Disabled Privacy Extensions
[    0.300071] NET: Registered protocol family 17
[    0.300151] Using IPI No-Shortcut mode
[    0.300303] PM: Resume from disk failed.
[    0.300320] registered taskstats version 1
[    0.300605]   Magic number: 3:648:320
[    0.300633] tty tty45: hash matches
[    0.300700] rtc_cmos 00:03: setting system clock to 2011-07-07 08:19:40 UTC (1310026780)
[    0.300706] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.300708] EDD information not available.
[    0.310083] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.455789] ata1.01: NODEV after polling detection
[    0.460444] ata1.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL00, max UDMA/100
[    0.461116] ata2.00: ATA-8: WDC WD3200AAJS-00YZCA0, 01.03B01, max UDMA/133
[    0.461122] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.476528] ata1.00: configured for UDMA/100
[    0.477149] ata2.00: configured for UDMA/133
[    0.719667] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    0.891610] isapnp: No Plug & Play device found
[    0.895157] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
[    0.910769] usb 1-8: configuration #1 chosen from 1 choice
[    0.910798] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.910803] Uniform CD-ROM driver Revision: 3.20
[    0.910960] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.911059] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.911296] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 01.0 PQ: 0 ANSI: 5
[    0.911501] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    0.911765] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.911852] sd 1:0:0:0: [sda] Write Protect is off
[    0.911856] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.911930] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.912181]  sda: sda1 sda2 < sda5 sda6 >
[    0.946154] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.013110] Freeing initrd memory: 13303k freed
[    1.022717] Freeing unused kernel memory: 668k freed
[    1.023295] Write protecting the kernel text: 4676k
[    1.023328] Write protecting the kernel read-only data: 1844k
[    1.062816] ramzswap: disk size set to 1673816 kB
[    1.075857] udev: starting version 151
[    1.148055] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.185631] Adding 1673812k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1673812k SS
[    1.322056] usb 5-1: configuration #1 chosen from 1 choice
[    1.415667] Linux agpgart interface v0.103
[    1.427536] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.427567] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.427631] r8169 0000:02:00.0: setting latency timer to 64
[    1.427698]   alloc irq_desc for 26 on node -1
[    1.427701]   alloc kstat_irqs on node -1
[    1.427719] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.430068] eth0: RTL8101e at 0xf84d4000, 00:1d:7d:c4:0d:77, XID 94200000 IRQ 26
[    1.492702] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    1.492948] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.513882] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.537744] [drm] Initialized drm 1.1.0 20060810
[    1.546065] usbcore: registered new interface driver hiddev
[    1.572187] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input4
[    1.572368] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.3-1/input0
[    1.572406] usbcore: registered new interface driver usbhid
[    1.572410] usbhid: v2.6:USB HID core driver
[    1.576073] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.576081] i915 0000:00:02.0: setting latency timer to 64
[    1.594742] [drm] set up 7M of stolen space
[    1.595555] [drm] initialized overlay support
[    1.760136] fb0: inteldrmfb frame buffer device
[    1.760140] registered panic notifier
[    1.760152] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.763814] vga16fb: initializing
[    1.763822] vga16fb: mapped to 0xc00a0000
[    1.763829] vga16fb: not registering due to another framebuffer present
[    1.829778] Console: switching to colour frame buffer device 180x56
[    2.318824] xor: automatically using best checksumming function: pIII_sse
[    2.336008]    pIII_sse  :  4309.000 MB/sec
[    2.336011] xor: using function: pIII_sse (4309.000 MB/sec)
[    2.346062] device-mapper: dm-raid45: initialized v0.2594b
[    2.493134] kjournald starting.  Commit interval 5 seconds
[    2.493154] EXT3-fs: mounted filesystem with ordered data mode.
[   12.113280] udev: starting version 151
[   12.159553] Adding 4881400k swap on /dev/sda5.  Priority:-1 extents:1 across:4881400k 
[   12.359635] lp: driver loaded but no devices found
[   12.504142] intel_rng: FWH not detected
[   12.573413] parport_pc 00:07: reported by Plug and Play ACPI
[   12.573465] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.666961] lp0: using parport0 (interrupt-driven).
[   12.793821] EXT3 FS on sda1, internal journal
[   12.934158] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04E8 pid 0x328D
[   12.934191] usbcore: registered new interface driver usblp
[   12.950551] ppdev: user-space parallel port driver
[   13.099883] type=1505 audit(1310026793.295:2):  operation="profile_load" pid=566 name="/sbin/dhclient3"
[   13.100728] type=1505 audit(1310026793.299:3):  operation="profile_load" pid=566 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.101164] type=1505 audit(1310026793.299:4):  operation="profile_load" pid=566 name="/usr/lib/connman/scripts/dhclient-script"
[   13.397561] CA0106 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.397589] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   13.519886] kjournald starting.  Commit interval 5 seconds
[   13.520366] EXT3 FS on sda6, internal journal
[   13.520375] EXT3-fs: mounted filesystem with ordered data mode.
[   18.115034] type=1505 audit(1310026798.311:5):  operation="profile_load" pid=730 name="/usr/share/gdm/guest-session/Xsession"
[   18.127448] type=1505 audit(1310026798.323:6):  operation="profile_replace" pid=731 name="/sbin/dhclient3"
[   18.146394] type=1505 audit(1310026798.343:7):  operation="profile_replace" pid=731 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.146844] type=1505 audit(1310026798.343:8):  operation="profile_replace" pid=731 name="/usr/lib/connman/scripts/dhclient-script"

---

### Post by psusi on 2011-07-07
It looks like the top part of it got cut off ( filled up your terminal scrollback buffer? ).  Try dmesg | less and then search ( type / to start a search, then the word to search for, then enter ) for e820.

---

### Post by holadebob on 2011-07-07
Here's e820....


[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf7f0000 (usable)
[    0.000000]  BIOS-e820: 00000000cf7f0000 - 00000000cf7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf7f3000 - 00000000cf800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xcf7f0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C9FFF write-protect
[    0.000000]   CA000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 0CF800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
:

---

### Post by holadebob on 2011-07-07
psusi, forgot to include, if you need it, mb info.

gigabyte GA-945GCM-S2C with Award Version F4 11/08/07

---

### Post by psusi on 2011-07-07
Yep, it is either a bios bug, misconfiguration, or hardware limit.  Look for an option in the bios to enable memory hoisting or hole remapping.

---

### Post by Perfect Storm on 2011-07-07
onboard video card do take some of your RAM for its own. It may be this.

---

### Post by holadebob on 2011-07-07
That's true, but it's not that much compared to the 800mb that doesn't show up. I believe it's less than a mb.

---

### Post by holadebob on 2011-07-07
psusi, thank you-I'm happy that there is a problem that might be solvable.

Gigabyte's book only says one thing on memory...These fields are read-only and are determined by the BIOS POST.

Base Memory and extende memory (the old MS-Dos parameters.


One other thing, there's a No-Execute Memory Protect which Enables or disables Intel Execute Disable Bit function, reducing exposure to viruses and malicious buffer overflow attacks when working with it's supporting software and system. Default enabled. 

I'm only running Ubuntu 10.04.

The Gigabyte book says it's mb will handle 2ea 2gb ddr2's, so maybe hardware limitation possibility can be eliminated?

Can you tell me what to do about checking configuration? 

Thank you

---

### Post by holadebob on 2011-07-07
To psusi and anyone else out there interested in this reduced memory available problem. After scanning the net, I saw many sources of info on how Gigabyte and other mbs with intel chipsets that don't have the number of address lines it takes to access 4gb. 

Using the pae kernal with it's additional address bus configuration won't work because apparently Gigabyte et al didn't wire in the (4?) address bus lines to access the full 4gb. 

Hope I'm right on this.

Looks like we (some of us) have to live with it.

---

