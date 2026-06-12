---
title: "system freezes with a black screen and a message"
date: 2010-09-10
forum: General Help
---

### Post by Mushfekur Rahman on 2010-09-10
I'm using ubuntu 10.04 and it worked fine but recently I'm getting the following message -
> 
(process:343) GLib_Warning** : getpwuid_r(): failed due to unknown user id(0).

this message comes with a black screen and then no key stroke works and everything totally freezes. then I've to force restart using power switch. this message appears when I'm using internet. I'm using pppoe broadband connection. without internet it works fine. anyone plz help why this happening???? and how to fix this prob. I'm getting the same prob in Linux Mint 9.
I've googled for this problem and almost everywhere it is said that this message appears in booting time and after a few moments everything becomes quite ok but my problem doesn't match with them. I don't get this message in booting time. I get this message when I'm on internet.
I'm in so trouble .... so plz help me guys .... :((

---

### Post by Rubi1200 on 2010-09-10
It could be a graphics issue: post the output of this ```
lspci | grep VGA
```

Also, post the output of this: ```
ifconfig
```

---

### Post by Mushfekur Rahman on 2010-09-10
output for lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

```

output for ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:24:1d:36:c3:87
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:26 Base address:0xa000 

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6448 (6.4 KB)  TX bytes:6448 (6.4 KB)


```

---

### Post by absolutezero1287 on 2010-09-10
The strange thing is that Ubuntu has always given me this error but it never stopped me from doing anything. I don't think that a Glib error has anything to do with your internet connection, though. Post the output of the following command:
```

dmesg

```

EDIT: Be sure to try and replicate the error BEFORE you get the output of dmesg.

---

### Post by Mushfekur Rahman on 2010-09-10
though it is strange but I'm sure about the error. and I've checked unpluging my network cable. then it works pretty fine but with internet it shows this message.

however output of dmesg
```

[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f600000 (gap: 3f600000:80a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u1048576
[    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257423
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/linuxmint/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5191040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f5e0)
[    0.000000] Memory: 1001276k/1038208k available (4673k kernel code, 35704k reserved, 2122k data, 656k init, 128904k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2499.877 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.75 BogoMIPS (lpj=9999508)
[    0.004021] Security Framework initialized
[    0.004038] AppArmor: AppArmor initialized
[    0.004045] Mount-cache hash table entries: 512
[    0.004162] Initializing cgroup subsys ns
[    0.004166] Initializing cgroup subsys cpuacct
[    0.004171] Initializing cgroup subsys memory
[    0.004177] Initializing cgroup subsys devices
[    0.004180] Initializing cgroup subsys freezer
[    0.004183] Initializing cgroup subsys net_cls
[    0.004203] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004206] CPU: L2 cache: 2048K
[    0.004209] CPU: Physical Processor ID: 0
[    0.004210] CPU: Processor Core ID: 0
[    0.004214] mce: CPU supports 6 MCE banks
[    0.004222] CPU0: Thermal monitoring enabled (TM2)
[    0.004225] using mwait in idle threads.
[    0.004230] Performance Events: Core2 events, Intel PMU driver.
[    0.004239] ... version:                2
[    0.004240] ... bit width:              40
[    0.004243] ... generic registers:      2
[    0.004245] ... value mask:             000000ffffffffff
[    0.004247] ... max period:             000000007fffffff
[    0.004249] ... fixed-purpose events:   3
[    0.004251] ... event mask:             0000000700000003
[    0.004255] Checking 'hlt' instruction... OK.
[    0.023236] ACPI: Core revision 20090903
[    0.029952] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.029960] ftrace: allocating 21771 entries in 43 pages
[    0.032053] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032365] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073215] CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.160103] CPU1: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06
[    0.160119] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164019] Brought up 2 CPUs
[    0.164022] Total of 2 processors activated (9999.61 BogoMIPS).
[    0.164576] CPU0 attaching sched-domain:
[    0.164579]  domain 0: span 0-1 level MC
[    0.164582]   groups: 0 1
[    0.164589] CPU1 attaching sched-domain:
[    0.164591]  domain 0: span 0-1 level MC
[    0.164594]   groups: 1 0
[    0.164696] devtmpfs: initialized
[    0.164696] regulator: core version 0.5
[    0.164696] Time: 16:37:07  Date: 09/10/10
[    0.164696] NET: Registered protocol family 16
[    0.164696] Trying to unpack rootfs image as initramfs...
[    0.164696] EISA bus registered
[    0.164696] ACPI: bus type pci registered
[    0.164696] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.164696] PCI: MCFG area at c0000000 reserved in E820
[    0.164696] PCI: Using MMCONFIG for extended config space
[    0.164696] PCI: Using configuration type 1 for base access
[    0.168104] bio: create slab <bio-0> at 0
[    0.168806] ACPI: EC: Look up EC in DSDT
[    0.174188] ACPI: Interpreter enabled
[    0.174207] ACPI: (supports S0 S3 S4 S5)
[    0.174234] ACPI: Using IOAPIC for interrupt routing
[    0.179237] ACPI: No dock devices found.
[    0.179334] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.179429] pci 0000:00:02.0: reg 10 32bit mmio: [0xe1200000-0xe127ffff]
[    0.179435] pci 0000:00:02.0: reg 14 io port: [0xe000-0xe007]
[    0.179440] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.179446] pci 0000:00:02.0: reg 1c 32bit mmio: [0xe1000000-0xe10fffff]
[    0.179529] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe1280000-0xe1283fff]
[    0.179574] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.179579] pci 0000:00:1b.0: PME# disabled
[    0.179646] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.179650] pci 0000:00:1c.0: PME# disabled
[    0.179720] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.179724] pci 0000:00:1c.1: PME# disabled
[    0.179776] pci 0000:00:1d.0: reg 20 io port: [0xe100-0xe11f]
[    0.179827] pci 0000:00:1d.1: reg 20 io port: [0xe200-0xe21f]
[    0.179877] pci 0000:00:1d.2: reg 20 io port: [0xe300-0xe31f]
[    0.179928] pci 0000:00:1d.3: reg 20 io port: [0xe400-0xe41f]
[    0.179976] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe1284000-0xe12843ff]
[    0.180165] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.180170] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.180174] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.180178] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.180230] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.180236] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.180243] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.180249] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.180255] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.180281] pci 0000:00:1f.2: PME# supported from D3hot
[    0.180285] pci 0000:00:1f.2: PME# disabled
[    0.180334] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.180401] pci 0000:00:1c.0: bridge io port: [0xc000-0xcfff]
[    0.180458] pci 0000:02:00.0: reg 10 io port: [0xd000-0xd0ff]
[    0.180479] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xe1110000-0xe1110fff]
[    0.180495] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xe1100000-0xe110ffff]
[    0.180504] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.180546] pci 0000:02:00.0: supports D1 D2
[    0.180548] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.180554] pci 0000:02:00.0: PME# disabled
[    0.180615] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.180619] pci 0000:00:1c.1: bridge 32bit mmio: [0xe0000000-0xe0ffffff]
[    0.180626] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xe1100000-0xe11fffff]
[    0.180677] pci 0000:00:1e.0: transparent bridge
[    0.180682] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.180703] pci_bus 0000:00: on NUMA node 0
[    0.180708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.180961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.181035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.192798] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.192903] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.193005] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.193111] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.193215] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.193317] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.193419] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.193523] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.193635] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.193646] vgaarb: loaded
[    0.193775] SCSI subsystem initialized
[    0.193875] libata version 3.00 loaded.
[    0.193952] usbcore: registered new interface driver usbfs
[    0.193968] usbcore: registered new interface driver hub
[    0.193996] usbcore: registered new device driver usb
[    0.194136] ACPI: WMI: Mapper loaded
[    0.194138] PCI: Using ACPI for IRQ routing
[    0.194289] NetLabel: Initializing
[    0.194291] NetLabel:  domain hash size = 128
[    0.194293] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.194306] NetLabel:  unlabeled traffic allowed by default
[    0.194340] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.194345] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200115] Switching to clocksource tsc
[    0.202301] AppArmor: AppArmor Filesystem Enabled
[    0.202317] pnp: PnP ACPI init
[    0.202333] ACPI: bus type pnp registered
[    0.205232] pnp: PnP ACPI: found 15 devices
[    0.205235] ACPI: ACPI bus type pnp unregistered
[    0.205242] PnPBIOS: Disabled by ACPI PNP
[    0.205254] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.205257] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.205261] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.205264] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.205267] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.205277] system 00:0b: ioport range 0x400-0x4cf could not be reserved
[    0.205283] system 00:0c: iomem range 0xc0000000-0xcfffffff has been reserved
[    0.205290] system 00:0d: iomem range 0xcb400-0xcbfff has been reserved
[    0.205293] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.205296] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.205299] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.205303] system 00:0d: iomem range 0x3f5e0000-0x3f5fffff could not be reserved
[    0.205306] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.205309] system 00:0d: iomem range 0x100000-0x3f5dffff could not be reserved
[    0.205312] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.205315] system 00:0d: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.205319] system 00:0d: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.205322] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.205325] system 00:0d: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.205328] system 00:0d: iomem range 0xfff00000-0xffffffff has been reserved
[    0.205331] system 00:0d: iomem range 0xe0000-0xeffff has been reserved
[    0.240063] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.240068] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
[    0.240074] pci 0000:00:1c.0:   MEM window: 0x40000000-0x401fffff
[    0.240079] pci 0000:00:1c.0:   PREFETCH window: 0x00000040200000-0x000000403fffff
[    0.240087] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.240090] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.240096] pci 0000:00:1c.1:   MEM window: 0xe0000000-0xe0ffffff
[    0.240100] pci 0000:00:1c.1:   PREFETCH window: 0x000000e1100000-0x000000e11fffff
[    0.240107] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.240110] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.240115] pci 0000:00:1e.0:   MEM window: disabled
[    0.240119] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.240140]   alloc irq_desc for 16 on node -1
[    0.240142]   alloc kstat_irqs on node -1
[    0.240150] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.240155] pci 0000:00:1c.0: setting latency timer to 64
[    0.240164]   alloc irq_desc for 17 on node -1
[    0.240166]   alloc kstat_irqs on node -1
[    0.240170] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.240174] pci 0000:00:1c.1: setting latency timer to 64
[    0.240181] pci 0000:00:1e.0: setting latency timer to 64
[    0.240186] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.240189] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.240192] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.240195] pci_bus 0000:01: resource 1 mem: [0x40000000-0x401fffff]
[    0.240198] pci_bus 0000:01: resource 2 pref mem [0x40200000-0x403fffff]
[    0.240200] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.240203] pci_bus 0000:02: resource 1 mem: [0xe0000000-0xe0ffffff]
[    0.240206] pci_bus 0000:02: resource 2 pref mem [0xe1100000-0xe11fffff]
[    0.240209] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.240212] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.240215] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.240256] NET: Registered protocol family 2
[    0.240374] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.240733] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.241248] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.241479] TCP: Hash tables configured (established 131072 bind 65536)
[    0.241481] TCP reno registered
[    0.241570] NET: Registered protocol family 1
[    0.241592] pci 0000:00:02.0: Boot video device
[    0.241894] cpufreq-nforce2: No nForce2 chipset.
[    0.241926] Scanning for low memory corruption every 60 seconds
[    0.242050] audit: initializing netlink socket (disabled)
[    0.242061] type=2000 audit(1284136626.239:1): initialized
[    0.253172] highmem bounce pool size: 64 pages
[    0.253178] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.254854] VFS: Disk quotas dquot_6.5.2
[    0.254918] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.255574] fuse init (API version 7.13)
[    0.255666] msgmni has been set to 1705
[    0.255902] alg: No test for stdrng (krng)
[    0.255959] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.255963] io scheduler noop registered
[    0.255965] io scheduler anticipatory registered
[    0.255967] io scheduler deadline registered
[    0.256010] io scheduler cfq registered (default)
[    0.256145]   alloc irq_desc for 24 on node -1
[    0.256147]   alloc kstat_irqs on node -1
[    0.256159] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.256168] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.256295]   alloc irq_desc for 25 on node -1
[    0.256297]   alloc kstat_irqs on node -1
[    0.256305] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.256313] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.256402] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.256484] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.256583] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.256587] ACPI: Power Button [PWRB]
[    0.256646] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.256649] ACPI: Power Button [PWRF]
[    0.257147] ACPI: SSDT 3f5e74c0 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.257364] processor LNXCPU:00: registered as cooling_device0
[    0.257564] ACPI: SSDT 3f5e7980 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.258083] processor LNXCPU:01: registered as cooling_device1
[    0.261571] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.261675] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.262075] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.263287] brd: module loaded
[    0.263821] loop: module loaded
[    0.263903] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.264003] ata_piix 0000:00:1f.2: version 2.13
[    0.264021]   alloc irq_desc for 19 on node -1
[    0.264023]   alloc kstat_irqs on node -1
[    0.264030] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.264035] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.264077] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.264152] scsi0 : ata_piix
[    0.264224] scsi1 : ata_piix
[    0.264924] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.264927] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.265285] Fixed MDIO Bus: probed
[    0.265327] PPP generic driver version 2.4.2
[    0.265365] tun: Universal TUN/TAP device driver, 1.6
[    0.265367] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.265455] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.265474]   alloc irq_desc for 23 on node -1
[    0.265476]   alloc kstat_irqs on node -1
[    0.265481] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.265494] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.265498] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.265535] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.265554] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.269449] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.269464] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe1284000
[    0.273609] isapnp: Scanning for PnP cards...
[    0.283487] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.283610] usb usb1: configuration #1 chosen from 1 choice
[    0.283642] hub 1-0:1.0: USB hub found
[    0.283651] hub 1-0:1.0: 8 ports detected
[    0.283721] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.283739] uhci_hcd: USB Universal Host Controller Interface driver
[    0.283779] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.283786] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.283790] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.283830] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.283854] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e100
[    0.283947] usb usb2: configuration #1 chosen from 1 choice
[    0.283975] hub 2-0:1.0: USB hub found
[    0.283982] hub 2-0:1.0: 2 ports detected
[    0.284027] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.284033] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.284036] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.284073] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.284103] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e200
[    0.284197] usb usb3: configuration #1 chosen from 1 choice
[    0.284224] hub 3-0:1.0: USB hub found
[    0.284231] hub 3-0:1.0: 2 ports detected
[    0.284276]   alloc irq_desc for 18 on node -1
[    0.284279]   alloc kstat_irqs on node -1
[    0.284285] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.284291] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.284294] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.284329] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.284358] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e300
[    0.284459] usb usb4: configuration #1 chosen from 1 choice
[    0.284487] hub 4-0:1.0: USB hub found
[    0.284494] hub 4-0:1.0: 2 ports detected
[    0.284539] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.284545] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.284548] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.284583] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.284612] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e400
[    0.284700] usb usb5: configuration #1 chosen from 1 choice
[    0.284727] hub 5-0:1.0: USB hub found
[    0.284734] hub 5-0:1.0: 2 ports detected
[    0.284836] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.284838] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.285016] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.285121] mice: PS/2 mouse device common for all mice
[    0.285253] rtc_cmos 00:04: RTC can wake from S4
[    0.285297] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.285321] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.285430] device-mapper: uevent: version 1.0.3
[    0.285524] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.285588] device-mapper: multipath: version 1.1.0 loaded
[    0.285590] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.285703] EISA: Probing bus 0 at eisa.0
[    0.285731] EISA: Detected 0 cards.
[    0.285804] cpuidle: using governor ladder
[    0.285806] cpuidle: using governor menu
[    0.286293] TCP cubic registered
[    0.286462] NET: Registered protocol family 10
[    0.286971] lo: Disabled Privacy Extensions
[    0.287342] NET: Registered protocol family 17
[    0.289126] Using IPI No-Shortcut mode
[    0.289273] PM: Resume from disk failed.
[    0.289286] registered taskstats version 1
[    0.289547]   Magic number: 10:48:641
[    0.289616] rtc_cmos 00:04: setting system clock to 2010-09-10 16:37:07 UTC (1284136627)
[    0.289619] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.289621] EDD information not available.
[    0.305441] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.455782] ata2.01: NODEV after polling detection
[    0.463894] ata2.00: ATAPI: TSSTcorpDVD-ROM SH-D163B, SB03, max UDMA/33
[    0.463986] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    0.463992] ata1.00: ATA-8: Hitachi HDP725025GLA380, GM2OA5CA, max UDMA/133
[    0.463995] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.479975] ata2.00: configured for UDMA/33
[    0.480558] ata1.00: configured for UDMA/133
[    0.547814] Freeing initrd memory: 13377k freed
[    0.627830] isapnp: No Plug & Play device found
[    0.627979] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72502 GM2O PQ: 0 ANSI: 5
[    0.628133] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.628168] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.628186] sd 0:0:0:0: [sda] Write Protect is off
[    0.628189] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.628215] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.628465]  sda:
[    0.629397] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD-ROM SH-D163B SB03 PQ: 0 ANSI: 5
[    0.635118] sr0: scsi3-mmc drive: 4x/32x cd/rw xa/form2 cdda tray
[    0.635122] Uniform CD-ROM driver Revision: 3.20
[    0.635250] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.635301] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.638909]  sda1 sda2 < sda5 sda6 sda7 >
[    0.686035] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.686052] Freeing unused kernel memory: 656k freed
[    0.686480] Write protecting the kernel text: 4676k
[    0.686524] Write protecting the kernel read-only data: 1840k
[    0.705583] udev: starting version 151
[    0.796377] Linux agpgart interface v0.103
[    0.799968] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.799988] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.800024] r8169 0000:02:00.0: setting latency timer to 64
[    0.800068]   alloc irq_desc for 26 on node -1
[    0.800071]   alloc kstat_irqs on node -1
[    0.800086] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.800797] eth0: RTL8102e at 0xf8090000, 00:24:1d:36:c3:87, XID 14a00000 IRQ 26
[    0.826075] [drm] Initialized drm 1.1.0 20060810
[    0.829268] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.830019] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[    0.841332] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.844245] Floppy drive(s): fd0 is 1.44M
[    0.863024] FDC 0 is a post-1991 82077
[    0.895557] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    0.963835] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.963840] i915 0000:00:02.0: setting latency timer to 64
[    0.967643]   alloc irq_desc for 27 on node -1
[    0.967646]   alloc kstat_irqs on node -1
[    0.967657] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    0.967663] [drm] set up 7M of stolen space
[    0.968056] [drm] initialized overlay support
[    1.073494] usb 4-1: configuration #1 chosen from 1 choice
[    1.097943] usbcore: registered new interface driver hiddev
[    1.098183] usbcore: registered new interface driver usbhid
[    1.098272] usbhid: v2.6:USB HID core driver
[    1.112785] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[    1.113000] a4tech 0003:09DA:000A.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.2-1/input0
[    1.131971] fb0: inteldrmfb frame buffer device
[    1.131975] registered panic notifier
[    1.131992] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.133964] vga16fb: initializing
[    1.133968] vga16fb: mapped to 0xc00a0000
[    1.133971] vga16fb: not registering due to another framebuffer present
[    1.242009] Console: switching to colour frame buffer device 160x64
[    1.760260] xor: automatically using best checksumming function: pIII_sse
[    1.780004]    pIII_sse  :  6686.000 MB/sec
[    1.780006] xor: using function: pIII_sse (6686.000 MB/sec)
[    1.787373] device-mapper: dm-raid45: initialized v0.2594b
[    2.194626] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    8.192608] udev: starting version 151
[    8.423533] lp: driver loaded but no devices found
[    8.425846] intel_rng: FWH not detected
[    8.438780] parport_pc 00:09: reported by Plug and Play ACPI
[    8.438827] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.536384] lp0: using parport0 (interrupt-driven).
[    8.567207] ppdev: user-space parallel port driver
[    9.073450] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.073655] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.193936] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   10.182094] Adding 261112k swap on /host/linuxmint/disks/swap.disk.  Priority:-1 extents:1 across:261112k 
[   10.310363] r8169: eth0: link up
[   10.310367] r8169: eth0: link up
[   10.568576] NET: Registered protocol family 24
[   11.887281] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.204008] eth0: no IPv6 routers present
[   29.249046] end_request: I/O error, dev fd0, sector 0
[   41.412381] end_request: I/O error, dev fd0, sector 0


```

---

### Post by absolutezero1287 on 2010-09-11
This part of the dmesg is most interesting.
> 
[   29.249046] end_request: I/O error, dev fd0, sector 0
[   41.412381] end_request: I/O error, dev fd0, sector 0


/dev/fd0 is a floppy disk. Are you using a floppy disk at all? Does your machine even have a floppy drive? If the answer is no then try changing some options in your BIOS. Disable the floppy disk. Once you do this try and boot into Ubuntu. If you still have difficulties then once again replicate the error and get the output of dmesg.

---

### Post by Mushfekur Rahman on 2010-09-13
no I've no floppy disk drives on my PC. though I tried to disable floppy drive from BIOS but I couldn't find any option about floppy. Besides I've tried with different mechine here is also I'm facing the same prob. But here it doesn't show the error message. just freezes with the current screne. now I think there might be some problem in the CD from where I install. But here is also a question that I've used that CD several times and no other time it caused any prob. if it is because of this copy of ubuntu it would cause problem earlier. isn't it ?? so now I'm in great trouble. I love ubuntu so much but now using windos. so thnx buddy for trying to help me and if any suggestion further tell me what can I do ???

---

### Post by Rubi1200 on 2010-09-13
Hi,
you have an Intel chipset:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Read the information carefully because there are a number of different options available and you would need to find the right one for your hardware.

Hope this helps.

---

### Post by Mushfekur Rahman on 2010-09-14
thnx :)

---

