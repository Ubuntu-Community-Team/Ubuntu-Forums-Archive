---
title: "Don't know what is wrong with my computer"
date: 2011-03-16
forum: General Help
---

### Post by Achilles124 on 2011-03-16
I have encountered problems when starting my computer.
I get a white screen like this. I restart. I get the same screen. I restart again and everything is fine.

Now I have a different problem. I have lines running over my screen.

I first thought it was my graphic card and I replaced it. It worked fine for a few weeks but the problems have returned.

---

### Post by cchhrriiss121212 on 2011-03-16
Could be any of these:
Motherboard
RAM - try running memtest which is in the repos
CPU
GPU

---

### Post by Grenage on 2011-03-16
It's also worth checking the monitor cable, and swapping out the monitor if you have a spare.  While not as likely to be at fault, they are the simplest to test.

---

### Post by Achilles124 on 2011-03-16
Okay, I will. In the meantime I have run a Ubuntu Live CD (ubuntu 9.10). Everything worked fine. What does that tell you?

And how do I run the memtest? I downloaded it from the repos. 

Can I test the system in any other way?

---

### Post by Grenage on 2011-03-16
Memtest is usually available from the Grub menu (hold down shift during boot).  As for the liveCD being ok, that does make hardware problems somewhat less likely.  If you continue to use the liveCD, or reboot with it a few times, does it stay 'ok'?

---

### Post by Achilles124 on 2011-03-16
I tried it two more times with the Live CD. It all worked perfectly. Moreover, booting in my own system worked fine too.

No more stripes. 

I forgot to mention one other thing: when closing down, I saw messages about apache appearing. Out of curiosity I installed apache, mysql and php in the past. 

So I have deinstalled these programs. I deinstalled Php just now. I deinstalled the NVdia driver. 

How is it possible that LAMP can cause problems when turning off your computer? (btw, I don't know a thing about LAMP. I was just trying it).

I will try the memtest now.

---

### Post by Grenage on 2011-03-16
> **Achilles124 said:**
> I tried it two more times with the Live CD. It all worked perfectly. Moreover, booting in my own system worked fine too.

No more stripes. 

I forgot to mention one other thing: when closing down, I saw messages about apache appearing. Out of curiosity I installed apache, mysql and php in the past. 

So I have deinstalled these programs. I deinstalled Php just now. I deinstalled the NVdia driver. 

How is it possible that LAMP can cause problems when turning off your computer? (btw, I don't know a thing about LAMP. I was just trying it).

I will try the memtest now.

I can't speak to LAMP, I've never used more than apache on its own.  You mentioned that you removed the Nvidia drivers; assuming that you have an nvidia card, you'll most likely now be using the opensource drivers.  If that works for you, then great; otherwise it might be worth trying to activate them again through *Administration/additional drivers*.

It sounds rather sporadic!

---

### Post by Achilles124 on 2011-03-16
I will let it rest now and hope for the best. 

Thank you for answering both of you.:D

---

### Post by Achilles124 on 2011-03-27
Sadly, the problems return. So I have run dmesg | less.

The problems don't appear when I am running Puppy Linux from USB-stick so it must be the software that is causing this.

Can someone take a look at the dmesg | less output?

---

### Post by Achilles124 on 2011-03-27
The dmesg-file isn't complete. This output is:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-30-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 (Ubuntu 2.6.32-30.59-generic 2.6.32.29+drm33.13)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fffe000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  modified: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 000000007fffe000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37856000 - 37fef7e4
[    0.000000] Allocated new RAMDISK: 008e6000 - 0107f7e4
[    0.000000] Move RAMDISK from 0000000037856000 - 0000000037fef7e3 to 008e6000 - 0107f7e3
[    0.000000] ACPI: RSDP 000f9a20 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 00034 (v01 111307 RSDT0859 20071113 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 00084 (v01 111307 FACP0859 20071113 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb0440 04B7C (v01  0AAAA 0AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7ffbe000 00040
[    0.000000] ACPI: APIC 7ffb0390 0006C (v01 111307 APIC0859 20071113 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 111307 OEMMCFG  20071113 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffbe040 00071 (v01 111307 OEMB0859 20071113 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e1ed8]    TEXT DATA BSS ==> [0000100000 - 00008e1ed8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008e2000 - 00008e515b]              BRK ==> [00008e2000 - 00008e515b]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e6000 - 000107f7e4]      NEW RAMDISK ==> [00008e6000 - 000107f7e4]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c079c940, node_mem_map c1081200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7fffe000 (gap: 7fffe000:7ee02000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=059e8ce6-a89d-48d9-a403-8578b50500d1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2051612k/2096832k available (4689k kernel code, 43580k reserved, 2122k data, 664k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084d000   ( 664 kB)
[    0.000000]       .data : 0xc0594467 - 0xc07a6f08   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0594467   (4689 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2399.606 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.21 BogoMIPS (lpj=9598424)
[    0.008020] Security Framework initialized
[    0.008041] AppArmor: AppArmor initialized
[    0.008047] Mount-cache hash table entries: 512
[    0.008160] Initializing cgroup subsys ns
[    0.008165] Initializing cgroup subsys cpuacct
[    0.008168] Initializing cgroup subsys memory
[    0.008174] Initializing cgroup subsys devices
[    0.008176] Initializing cgroup subsys freezer
[    0.008178] Initializing cgroup subsys net_cls
[    0.008196] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008199] CPU: L2 cache: 2048K
[    0.008201] CPU: Physical Processor ID: 0
[    0.008203] CPU: Processor Core ID: 0
[    0.008206] mce: CPU supports 6 MCE banks
[    0.008214] CPU0: Thermal monitoring enabled (TM2)
[    0.008217] using mwait in idle threads.
[    0.008223] Performance Events: Core2 events, Intel PMU driver.
[    0.008231] ... version:                2
[    0.008233] ... bit width:              40
[    0.008234] ... generic registers:      2
[    0.008235] ... value mask:             000000ffffffffff
[    0.008237] ... max period:             000000007fffffff
[    0.008239] ... fixed-purpose events:   3
[    0.008240] ... event mask:             0000000700000003
[    0.008244] Checking 'hlt' instruction... OK.
[    0.026396] ACPI: Core revision 20090903
[    0.036009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036014] ftrace: allocating 21799 entries in 43 pages
[    0.044054] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044361] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084537] CPU0: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz stepping 0d
[    0.088001] APIC calibration not consistent with PM-Timer: 116ms instead of 100ms
[    0.088001] APIC delta adjusted to PM-Timer: 1249952 (1450026)
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.012000] Initializing CPU#1
[    0.012000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.012000] CPU: L2 cache: 2048K
[    0.012000] CPU: Physical Processor ID: 0
[    0.012000] CPU: Processor Core ID: 1
[    0.012000] CPU1: Thermal monitoring enabled (TM2)
[    0.172080] CPU1: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz stepping 0d
[    0.172087] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176017] Brought up 2 CPUs
[    0.176020] Total of 2 processors activated (9599.07 BogoMIPS).
[    0.176441] CPU0 attaching sched-domain:
[    0.176444]  domain 0: span 0-1 level MC
[    0.176446]   groups: 0 1
[    0.176451] CPU1 attaching sched-domain:
[    0.176453]  domain 0: span 0-1 level MC
[    0.176455]   groups: 1 0
[    0.176512] devtmpfs: initialized
[    0.176512] regulator: core version 0.5
[    0.176512] Time:  7:32:57  Date: 03/27/11
[    0.176512] NET: Registered protocol family 16
[    0.176512] Trying to unpack rootfs image as initramfs...
[    0.176512] EISA bus registered
[    0.176512] ACPI: bus type pci registered
[    0.176512] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.176512] PCI: Not using MMCONFIG.
[    0.176512] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.176512] PCI: Using configuration type 1 for base access
[    0.184172] bio: create slab <bio-0> at 0
[    0.184794] ACPI: EC: Detected MSI hardware, enabling workarounds.
[    0.184797] ACPI: EC: Look up EC in DSDT
[    0.187155] ACPI: Executed 1 blocks of module-level executable AML code
[    0.191067] ACPI: Interpreter enabled
[    0.191074] ACPI: (supports S0 S1 S4 S5)
[    0.191093] ACPI: Using IOAPIC for interrupt routing
[    0.191141] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.193870] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.193872] PCI: Using MMCONFIG for extended config space
[    0.199680] ACPI Warning: Incorrect checksum in table [OEMB] - 0D, should be 08 (20090903/tbutils-314)
[    0.199776] ACPI: No dock devices found.
[    0.200059] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.200169] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.200172] pci 0000:00:01.0: PME# disabled
[    0.200234] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7ffc000-0xf7ffffff]
[    0.200275] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.200279] pci 0000:00:1b.0: PME# disabled
[    0.200342] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.200345] pci 0000:00:1c.0: PME# disabled
[    0.200412] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.200415] pci 0000:00:1c.2: PME# disabled
[    0.200463] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.200510] pci 0000:00:1d.1: reg 20 io port: [0xd880-0xd89f]
[    0.200557] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[    0.200604] pci 0000:00:1d.3: reg 20 io port: [0xd480-0xd49f]
[    0.200658] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf7ffbc00-0xf7ffbfff]
[    0.200707] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.200712] pci 0000:00:1d.7: PME# disabled
[    0.200833] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.200839] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.200842] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.200846] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.200887] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.200894] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.200901] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.200907] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.200914] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.200953] pci 0000:00:1f.2: reg 10 io port: [0xd400-0xd407]
[    0.200958] pci 0000:00:1f.2: reg 14 io port: [0xd080-0xd083]
[    0.200964] pci 0000:00:1f.2: reg 18 io port: [0xd000-0xd007]
[    0.200969] pci 0000:00:1f.2: reg 1c io port: [0xcc00-0xcc03]
[    0.200975] pci 0000:00:1f.2: reg 20 io port: [0xc880-0xc88f]
[    0.200998] pci 0000:00:1f.2: PME# supported from D3hot
[    0.201001] pci 0000:00:1f.2: PME# disabled
[    0.201046] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.201101] pci 0000:01:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.201109] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.201118] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfd000000-0xfdffffff]
[    0.201126] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeae0000-0xfeafffff]
[    0.201188] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xfeafffff]
[    0.201193] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.201293] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.201315] pci 0000:03:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.201337] pci 0000:03:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
[    0.201384] pci 0000:03:00.0: supports D1 D2
[    0.201386] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.201392] pci 0000:03:00.0: PME# disabled
[    0.201445] pci 0000:00:1c.2: bridge io port: [0xe000-0xefff]
[    0.201448] pci 0000:00:1c.2: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.201501] pci 0000:00:1e.0: transparent bridge
[    0.201525] pci_bus 0000:00: on NUMA node 0
[    0.201529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.201664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.201788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.201842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.204932] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.205024] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205114] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.205205] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.205293] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205383] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205474] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.205563] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.205674] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205677] vgaarb: loaded
[    0.205790] SCSI subsystem initialized
[    0.205871] libata version 3.00 loaded.
[    0.205935] usbcore: registered new interface driver usbfs
[    0.205945] usbcore: registered new interface driver hub
[    0.205967] usbcore: registered new device driver usb
[    0.206088] ACPI: WMI: Mapper loaded
[    0.206090] PCI: Using ACPI for IRQ routing
[    0.206228] NetLabel: Initializing
[    0.206230] NetLabel:  domain hash size = 128
[    0.206231] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206243] NetLabel:  unlabeled traffic allowed by default
[    0.206363] hpet clockevent registered
[    0.206366] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.206370] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.206375] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212023] Switching to clocksource tsc
[    0.213884] AppArmor: AppArmor Filesystem Enabled
[    0.213902] pnp: PnP ACPI init
[    0.213920] ACPI: bus type pnp registered
[    0.217153] pnp: PnP ACPI: found 17 devices
[    0.217155] ACPI: ACPI bus type pnp unregistered
[    0.217159] PnPBIOS: Disabled by ACPI PNP
[    0.217170] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.217179] system 00:0a: ioport range 0xa00-0xadf has been reserved
[    0.217181] system 00:0a: ioport range 0xae0-0xaef has been reserved
[    0.217186] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.217189] system 00:0b: ioport range 0x800-0x87f has been reserved
[    0.217191] system 00:0b: ioport range 0x480-0x4bf has been reserved
[    0.217194] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.217196] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.217202] system 00:0d: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.217206] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.217209] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.217214] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.217219] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.217221] system 00:10: iomem range 0xc0000-0xcffff could not be reserved
[    0.217224] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.217226] system 00:10: iomem range 0x100000-0x7fffffff could not be reserved
[    0.251934] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.251937] pci 0000:00:01.0:   IO window: disabled
[    0.251941] pci 0000:00:01.0:   MEM window: 0xf8000000-0xfeafffff
[    0.251945] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.251949] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.251952] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.251957] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
[    0.251961] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
[    0.251968] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.251971] pci 0000:00:1c.2:   IO window: 0xe000-0xefff
[    0.251975] pci 0000:00:1c.2:   MEM window: 0xfeb00000-0xfebfffff
[    0.251979] pci 0000:00:1c.2:   PREFETCH window: 0x00000080400000-0x000000805fffff
[    0.251985] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.251987] pci 0000:00:1e.0:   IO window: disabled
[    0.251991] pci 0000:00:1e.0:   MEM window: disabled
[    0.251994] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.252011]   alloc irq_desc for 16 on node -1
[    0.252013]   alloc kstat_irqs on node -1
[    0.252020] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.252024] pci 0000:00:01.0: setting latency timer to 64
[    0.252031] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.252035] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.252039] pci 0000:00:1c.0: setting latency timer to 64
[    0.252048]   alloc irq_desc for 18 on node -1
[    0.252050]   alloc kstat_irqs on node -1
[    0.252053] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.252057] pci 0000:00:1c.2: setting latency timer to 64
[    0.252063] pci 0000:00:1e.0: setting latency timer to 64
[    0.252067] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.252069] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.252072] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfeafffff]
[    0.252074] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.252076] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.252078] pci_bus 0000:02: resource 1 mem: [0x80000000-0x801fffff]
[    0.252080] pci_bus 0000:02: resource 2 pref mem [0x80200000-0x803fffff]
[    0.252082] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.252084] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.252087] pci_bus 0000:03: resource 2 pref mem [0x80400000-0x805fffff]
[    0.252089] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.252091] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.252127] NET: Registered protocol family 2
[    0.252222] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.252540] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.253063] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253302] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253305] TCP reno registered
[    0.253391] NET: Registered protocol family 1
[    0.253508] pci 0000:01:00.0: Boot video device
[    0.253678] cpufreq-nforce2: No nForce2 chipset.
[    0.253702] Scanning for low memory corruption every 60 seconds
[    0.253807] audit: initializing netlink socket (disabled)
[    0.253816] type=2000 audit(1301211176.251:1): initialized
[    0.262242] highmem bounce pool size: 64 pages
[    0.262247] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.263599] VFS: Disk quotas dquot_6.5.2
[    0.263651] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.264162] fuse init (API version 7.13)
[    0.264233] msgmni has been set to 1689
[    0.264431] alg: No test for stdrng (krng)
[    0.264477] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.264480] io scheduler noop registered
[    0.264482] io scheduler anticipatory registered
[    0.264483] io scheduler deadline registered
[    0.264518] io scheduler cfq registered (default)
[    0.264636]   alloc irq_desc for 24 on node -1
[    0.264638]   alloc kstat_irqs on node -1
[    0.264646] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.264652] pcieport 0000:00:01.0: setting latency timer to 64
[    0.264747]   alloc irq_desc for 25 on node -1
[    0.264748]   alloc kstat_irqs on node -1
[    0.264755] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.264762] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.264867]   alloc irq_desc for 26 on node -1
[    0.264868]   alloc kstat_irqs on node -1
[    0.264874] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.264882] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.264959] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.264976] Firmware did not grant requested _OSC control
[    0.264991] Firmware did not grant requested _OSC control
[    0.265015] Firmware did not grant requested _OSC control
[    0.265025] Firmware did not grant requested _OSC control
[    0.265037] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.265124] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.265127] ACPI: Power Button [PWRB]
[    0.265166] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.265168] ACPI: Power Button [PWRF]
[    0.265415] processor LNXCPU:00: registered as cooling_device0
[    0.265446] processor LNXCPU:01: registered as cooling_device1
[    0.267819] isapnp: Scanning for PnP cards...
[    0.268346] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.268436] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.268741] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.269757] brd: module loaded
[    0.270164] loop: module loaded
[    0.270230] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.270307] ata_piix 0000:00:1f.1: version 2.13
[    0.270320] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.270353] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.270418] scsi0 : ata_piix
[    0.270476] scsi1 : ata_piix
[    0.271593] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.271596] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.271615]   alloc irq_desc for 19 on node -1
[    0.271617]   alloc kstat_irqs on node -1
[    0.271622] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.271626] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.271656] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.271695] scsi2 : ata_piix
[    0.271738] scsi3 : ata_piix
[    0.272851] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 19
[    0.272854] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 19
[    0.273138] Fixed MDIO Bus: probed
[    0.273166] PPP generic driver version 2.4.2
[    0.273196] tun: Universal TUN/TAP device driver, 1.6
[    0.273197] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.273269] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.273285]   alloc irq_desc for 23 on node -1
[    0.273287]   alloc kstat_irqs on node -1
[    0.273291] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.273310] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.273313] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.273345] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.273368] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.273377] ehci_hcd 0000:00:1d.7: debug port 1
[    0.277264] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.277297] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7ffbc00
[    0.291865] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.291972] usb usb1: configuration #1 chosen from 1 choice
[    0.291998] hub 1-0:1.0: USB hub found
[    0.292006] hub 1-0:1.0: 8 ports detected
[    0.292068] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.292084] uhci_hcd: USB Universal Host Controller Interface driver
[    0.292123] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.292131] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.292134] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.292165] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.292189] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    0.292263] usb usb2: configuration #1 chosen from 1 choice
[    0.292290] hub 2-0:1.0: USB hub found
[    0.292296] hub 2-0:1.0: 2 ports detected
[    0.292337] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.292342] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.292345] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.292372] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.292392] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    0.292465] usb usb3: configuration #1 chosen from 1 choice
[    0.292486] hub 3-0:1.0: USB hub found
[    0.292492] hub 3-0:1.0: 2 ports detected
[    0.292529] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.292534] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.292537] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.292564] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.292591] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.292664] usb usb4: configuration #1 chosen from 1 choice
[    0.292685] hub 4-0:1.0: USB hub found
[    0.292691] hub 4-0:1.0: 2 ports detected
[    0.292729] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.292734] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.292737] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.292763] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.292789] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d480
[    0.292863] usb usb5: configuration #1 chosen from 1 choice
[    0.292884] hub 5-0:1.0: USB hub found
[    0.292890] hub 5-0:1.0: 2 ports detected
[    0.292979] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.295317] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.295323] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.295424] mice: PS/2 mouse device common for all mice
[    0.295537] rtc_cmos 00:03: RTC can wake from S4
[    0.295571] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.295593] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.295682] device-mapper: uevent: version 1.0.3
[    0.321027] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.323297] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.339864] device-mapper: multipath: version 1.1.0 loaded
[    0.339869] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.340022] EISA: Probing bus 0 at eisa.0
[    0.340028] Cannot allocate resource for EISA slot 1
[    0.340047] EISA: Detected 0 cards.
[    0.348082] cpuidle: using governor ladder
[    0.348085] cpuidle: using governor menu
[    0.348463] TCP cubic registered
[    0.348596] NET: Registered protocol family 10
[    0.349019] lo: Disabled Privacy Extensions
[    0.349316] NET: Registered protocol family 17
[    0.349364] Using IPI No-Shortcut mode
[    0.349441] PM: Resume from disk failed.
[    0.349452] registered taskstats version 1
[    0.349721]   Magic number: 3:229:522
[    0.349790] rtc_cmos 00:03: setting system clock to 2011-03-27 07:32:57 UTC (1301211177)
[    0.349793] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.349794] EDD information not available.
[    0.354094] Freeing initrd memory: 7781k freed
[    0.457813] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S202H, SB00, max UDMA/66
[    0.457836] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.471990] ata1.00: configured for UDMA/33
[    0.494333] ata3.00: ATA-7: MAXTOR STM3160215AS, 4.AAB, max UDMA/133
[    0.494335] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.561001] ata3.00: configured for UDMA/133
[    0.627165] isapnp: No Plug & Play device found
[    0.627880] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202H  SB00 PQ: 0 ANSI: 5
[    0.631518] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.631523] Uniform CD-ROM driver Revision: 3.20
[    0.631682] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.631740] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.631856] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM316021 4.AA PQ: 0 ANSI: 5
[    0.631948] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.631955] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.631995] sd 2:0:0:0: [sda] Write Protect is off
[    0.631997] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.632023] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.632144]  sda: sda1 sda2 < sda5 >
[    0.672274] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.672288] Freeing unused kernel memory: 664k freed
[    0.672674] Write protecting the kernel text: 4692k
[    0.672711] Write protecting the kernel read-only data: 1844k
[    0.686448] udev: starting version 151
[    0.717362] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    0.743196] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.743215] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.743256] r8169 0000:03:00.0: setting latency timer to 64
[    0.743314]   alloc irq_desc for 27 on node -1
[    0.743316]   alloc kstat_irqs on node -1
[    0.743330] r8169 0000:03:00.0: irq 27 for MSI/MSI-X
[    0.743909] eth0: RTL8168b/8111b at 0xf8058000, 00:1d:92:70:97:77, XID 18000000 IRQ 27
[    0.850429] usb 1-6: configuration #1 chosen from 1 choice
[    0.856494] Initializing USB Mass Storage driver...
[    0.856580] scsi4 : SCSI emulation for USB Mass Storage devices
[    0.856654] usbcore: registered new interface driver usb-storage
[    0.856657] USB Mass Storage support registered.
[    0.856720] usb-storage: device found at 3
[    0.856721] usb-storage: waiting for device to settle before scanning
[    1.052436] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.089370] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.297515] usb 2-1: configuration #1 chosen from 1 choice
[    5.856405] usb-storage: device scan complete
[    5.867771] scsi 4:0:0:0: Direct-Access     AVEX     AX1611        CF 1.9C PQ: 0 ANSI: 0 CCS
[    5.869018] scsi 4:0:0:1: Direct-Access     AVEX     AX1611        MS 1.9C PQ: 0 ANSI: 0 CCS
[    5.870266] scsi 4:0:0:2: Direct-Access     AVEX     AX1611    MMC/SD 1.9C PQ: 0 ANSI: 0 CCS
[    5.871514] scsi 4:0:0:3: Direct-Access     AVEX     AX1611        SM 1.9C PQ: 0 ANSI: 0 CCS
[    5.871879] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    5.872004] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    5.872129] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    5.872249] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    5.916378] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    5.917249] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    5.918123] sd 4:0:0:3: [sde] Attached SCSI removable disk
[    5.918998] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   12.512231] udev: starting version 151
[   12.565198] Adding 6037496k swap on /dev/sda5.  Priority:-1 extents:1 across:6037496k 
[   12.579429] Linux agpgart interface v0.103
[   12.595594] lp: driver loaded but no devices found
[   12.644110] intel_rng: FWH not detected
[   12.679866] vga16fb: initializing
[   12.679870] vga16fb: mapped to 0xc00a0000
[   12.679925] fb0: VGA16 VGA frame buffer device
[   12.723224] parport_pc 00:07: reported by Plug and Play ACPI
[   12.723265] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.747947] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0704
[   12.747965] usbcore: registered new interface driver usblp
[   12.755011] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.769468] ppdev: user-space parallel port driver
[   12.787527] type=1505 audit(1301211189.934:2):  operation="profile_load" pid=538 name="/sbin/dhclient3"
[   12.788148] type=1505 audit(1301211189.938:3):  operation="profile_load" pid=538 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.788484] type=1505 audit(1301211189.938:4):  operation="profile_load" pid=538 name="/usr/lib/connman/scripts/dhclient-script"
[   12.789835] type=1505 audit(1301211189.938:5):  operation="profile_replace" pid=590 name="/sbin/dhclient3"
[   12.790442] type=1505 audit(1301211189.938:6):  operation="profile_replace" pid=590 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.790777] type=1505 audit(1301211189.938:7):  operation="profile_replace" pid=590 name="/usr/lib/connman/scripts/dhclient-script"
[   12.791805] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   12.792269] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   12.792271] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   12.792272] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.846189] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   12.940717] lp0: using parport0 (interrupt-driven).
[   12.974098] psmouse serio1: ID: 10 00 64
[   13.015975] Console: switching to colour frame buffer device 80x30
[   13.579154] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   13.622797] nvidia: module license 'NVIDIA' taints kernel.
[   13.622800] Disabling lock debugging due to kernel taint
[   13.961914] type=1505 audit(1301211191.110:8):  operation="profile_load" pid=864 name="/usr/share/gdm/guest-session/Xsession"
[   13.969104] type=1505 audit(1301211191.118:9):  operation="profile_load" pid=866 name="/usr/bin/evince"
[   13.973990] type=1505 audit(1301211191.122:10):  operation="profile_replace" pid=865 name="/sbin/dhclient3"
[   13.974606] type=1505 audit(1301211191.122:11):  operation="profile_replace" pid=865 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.310378] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.310400] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.380969] hda_codec: ALC888: BIOS auto-probing.
[   14.382361] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   14.554246] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.554255] nvidia 0000:01:00.0: setting latency timer to 64
[   14.554259] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.554439] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   14.724960] r8169: eth0: link up
[   14.724964] r8169: eth0: link up
[   18.655928] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.655931] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   18.655932] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   18.655933] vboxdrv: the usage of hardware performance counters by
[   18.655934] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   18.655938] vboxdrv: Found 2 processor cores.
[   18.656222] vboxdrv: fAsync=0 offMin=0x1d4 offMax=0x1cc8
[   18.656452] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   18.656454] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   19.176643] CPU0 attaching NULL sched-domain.
[   19.176649] CPU1 attaching NULL sched-domain.
[   19.200142] CPU0 attaching sched-domain:
[   19.200149]  domain 0: span 0-1 level MC
[   19.200154]   groups: 0 1
[   19.200163] CPU1 attaching sched-domain:
[   19.200167]  domain 0: span 0-1 level MC
[   19.200171]   groups: 1 0
[   19.953598] CPU0 attaching NULL sched-domain.
[   19.953604] CPU1 attaching NULL sched-domain.
[   19.980082] CPU0 attaching sched-domain:
[   19.980086]  domain 0: span 0-1 level MC
[   19.980089]   groups: 0 1
[   19.980094] CPU1 attaching sched-domain:
[   19.980096]  domain 0: span 0-1 level MC
[   19.980098]   groups: 1 0
[   20.184995] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   22.649083] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:92:70:97:77:00:1a:92:9c:59:91:08:00 SRC=174.36.30.31 DST=192.168.1.6 LEN=250 TOS=0x00 PREC=0x00 TTL=49 ID=62630 DF PROTO=TCP SPT=80 DPT=60804 WINDOW=79 RES=0x00 ACK PSH URGP=0 
[   25.632042] eth0: no IPv6 routers present
[   34.806356] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:92:70:97:77:00:1a:92:9c:59:91:08:00 SRC=174.36.30.31 DST=192.168.1.6 LEN=250 TOS=0x00 PREC=0x00 TTL=49 ID=62631 DF PROTO=TCP SPT=80 DPT=60804 WINDOW=79 RES=0x00 ACK PSH URGP=0 
[   59.120387] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:92:70:97:77:00:1a:92:9c:59:91:08:00 SRC=174.36.30.31 DST=192.168.1.6 LEN=250 TOS=0x00 PREC=0x00 TTL=49 ID=62632 DF PROTO=TCP SPT=80 DPT=60804 WINDOW=79 RES=0x00 ACK PSH URGP=0 
[  107.748931] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:92:70:97:77:00:1a:92:9c:59:91:08:00 SRC=174.36.30.31 DST=192.168.1.6 LEN=250 TOS=0x00 PREC=0x00 TTL=49 ID=62633 DF PROTO=TCP SPT=80 DPT=60804 WINDOW=79 RES=0x00 ACK PSH URGP=0 
[ 1175.116044] usb 1-6: reset high speed USB device using ehci_hcd and address 3
[ 1292.102000] usb 1-6: reset high speed USB device using ehci_hcd and address 3
```

---

### Post by Achilles124 on 2011-04-01
Did a memtest and it gave 0 errors. So memory is okay.

---

### Post by Grenage on 2011-04-01
Does the problem appear after a certain amount of time, or under high load, or does it happen immediately after booting?

---

### Post by Achilles124 on 2011-04-02
I have done a memtest and there were no errors.

I have tried a different screen and that didn't work either.

---

### Post by Achilles124 on 2011-04-02
Immediately after booting, Grenage.

---

### Post by Grenage on 2011-04-04
Does the BIOS screen appear screwed up?  Were you able to swap out the monitor cable?  If so, have you tried double-checking the internal connections?

---

### Post by Achilles124 on 2011-04-05
The BIOS-screen is normal. I have changed the monitors (and the cables). With both monitors I have the same problem. 

Double-checked the internal connections? What do you mean by that?

---

### Post by Grenage on 2011-04-05
> **Achilles124 said:**
> Double-checked the internal connections? What do you mean by that?

Internal cables and card seating, clutching-at-straws stuff.

I'm at a loss, to be honest.  You've ruled out the monitor, cables and graphics card by swapping them out; and you're ruled out RAM with a memory test.  That basically leaves just the motherboard and CPU, and they aren't likely candidates for this kind of problem.

What drivers are you using for the graphics?

---

### Post by Achilles124 on 2011-04-05
A Nvidia driver.

Other options:
Can the boot-file be corrupt?
Can the Xorg-file be corrupt?

If so, how can I check that?

Live-cd's work perfectly. So maybe it is not even the hardware that is the culprit but the software.

---

### Post by Grenage on 2011-04-05
> **Achilles124 said:**
> A Nvidia driver.

Other options:
Can the boot-file be corrupt?
Can the Xorg-file be corrupt?

If so, how can I check that?

Live-cd's work perfectly. So maybe it is not even the hardware that is the culprit but the software.

It's possible, but you've reinstalled haven't you?  The nvidia driver, is it one from *Administration/Additional Drivers*?

Corrupt xorg/boot is very unlikely, I'd not worry about that.

---

### Post by alphaamanitin on 2011-04-05
> **Achilles124 said:**
> I have done a memtest and there were no errors.

I have tried a different screen and that didn't work either.


How long did you let the memtest run?  I have seen memtests return zero errors if it was ran for a short time, but when I ran the memtest overnight it found errors.  Buying new ram fixed the issue so the errors must have been real.

AlphaA

---

### Post by Achilles124 on 2011-04-05
I have used a Live Cd of Bodhi: an Ubuntu derivative with Enlightenment. It gives you the possibility of a memtest after booting.

I did so and it gave 0 errors. It only took a short time to run the test, so you could be right.

I use the Nvidia-driver as it can be found in the menu of Ubuntu. So from gui.

Furthermore. I have installed Puppy Linux on an USB-stick and I boot from this stick. As you probably know, Puppy Linux doesn't use the CPU but the memory. So....it could be that too.

Lastly, where to look for errors. The problem arises at startup. I already posted the outcome of dmesg | less. I didn't see any errors but then again, I am not really an expert. Can you take a look, Grenage? Or somebody else?

---

### Post by Grenage on 2011-04-05
While I am also no expert, nothing in that log jumps out at me.

---

