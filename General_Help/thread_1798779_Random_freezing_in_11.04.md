---
title: "Random freezing in 11.04"
date: 2011-07-06
forum: General Help
---

### Post by FruG3rT on 2011-07-06
Gotta rewrite everything i just wrote, because it actuall froze while i was typing this. Anyways, recently installed Ubuntu 11.04 and its had nasty freezing issues from the start. When it freezes, i cant move the mouse, none of the cap locks, number lock or scroll locks work. It will put any sounds playing into a small loop, and my mouse freezes. im forced to hard reset my computer everytime. Its 100% random too, not caused by a program, as far as i know.
Anyone experienced this and have a solution?
Thanks in Advanced!

---

### Post by wildmanne39 on 2011-07-07
> **FruG3rT said:**
> Gotta rewrite everything i just wrote, because it actuall froze while i was typing this. Anyways, recently installed Ubuntu 11.04 and its had nasty freezing issues from the start. When it freezes, i cant move the mouse, none of the cap locks, number lock or scroll locks work. It will put any sounds playing into a small loop, and my mouse freezes. im forced to hard reset my computer everytime. Its 100% random too, not caused by a program, as far as i know.
Anyone experienced this and have a solution?
Thanks in Advanced!Hi, here is a link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by FruG3rT on 2011-07-08
I checked out your link, it doesn't really state my problem in there, when my computer freezes, theres no error message, no warning, no nothing. Its just working one minute, frozen the next. I actually left my computer on right after logging on, and let it sit, before it even hit the screen saver, it froze. And i have built on video (Nvidia) and a video card (also, Nvidia, with the add on to use the full effects of it) and ive tried both with the same results. Luckly, this session so far, i havnt had it freeze, yet. Thanks for the reply tho :)

---

### Post by wildmanne39 on 2011-07-08
> **FruG3rT said:**
> I checked out your link, it doesn't really state my problem in there, when my computer freezes, theres no error message, no warning, no nothing. Its just working one minute, frozen the next. I actually left my computer on right after logging on, and let it sit, before it even hit the screen saver, it froze. And i have built on video (Nvidia) and a video card (also, Nvidia, with the add on to use the full effects of it) and ive tried both with the same results. Luckly, this session so far, i havnt had it freeze, yet. Thanks for the reply tho :)Hi, you can look at your log file with log file viewer, see what dmesg and xorg log says.

---

### Post by kanishkdudeja on 2011-07-08
also when you get the feeling that its just going to freeze..

type ```
top
```

in the terminal..

and post its output here..

even my system was freezing like this...eventually found out that it was some nasty printer service which was using up all the memory.

---

### Post by vamped on 2011-07-08
> **kanishkdudeja said:**
> also when you get the feeling that its just going to freeze..

type ```
top
```

I had freezing problems (Kubuntu) too, and the "top" command never showed a thing. I traced it to a Nvidia driver issue that is well documented. I wasn't clear whether you tried turning all the effects off to see if it helped. That's just another possibility for you to look into.

Also rather than hard-resetting, have you tried: <alt><sysrq> <r><e><i><s><u><b> to shutdown cleaner?

---

### Post by FrozenFlame22 on 2011-07-20
I have had this problem too since I upgraded to 11.04 in early July. These freezes are exactly as stated by the OP. They happen at completely random and unrelated times. I've had freezes in the middle of something, right after I've walked away from the computer (but before it should go to screensaver), and when I've just been using it but paused to read something on the screen. The program seems to be irrelevant since this has occurred when I have been using Firefox, Chrome, LibreOffice, the Software Center, and simply only having my home folder open. Any music/sound is looped. No inputs from mouse or keyboard appear to be registering. Since this has been an ongoing issue, I cannot use Ubuntu for any serious work, so none of these times have been under any significant processor load. Beyond it happening as frequently as 3-4 times a day, I cannot duplicate the error. Unfortunately, I am not a knowledgeable enough user to know what error logs to post, but I do follow directions very well if someone wants to ask for more information.

ETA: I have tried REISUB, but the keyboard doesn't respond. Nothing beyond a hard reset appears to work. I hate doing this to my computer.

Also there never is any indication that a freeze is imminent. No lagging, nothing. Just cruising along fine and then dead in the water.

---

### Post by FrozenFlame22 on 2011-07-20
As per the earlier poster, here's the contents of those logs:

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ed15000 (usable)
[    0.000000]  BIOS-e820: 000000007ed15000 - 000000007ed17000 (reserved)
[    0.000000]  BIOS-e820: 000000007ed17000 - 000000007ee06000 (usable)
[    0.000000]  BIOS-e820: 000000007ee06000 - 000000007eeea000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007eeea000 - 000000007eef3000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eef3000 - 000000007eef4000 (usable)
[    0.000000]  BIOS-e820: 000000007eef4000 - 000000007eeff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeff000 - 000000007ef00000 (usable)
[    0.000000]  BIOS-e820: 000000007ef00000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI:                  /DP35DP, BIOS DPP3510J.86A.0276.2007.0903.1413 09/03/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ef00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F000000 mask FFF000000 uncachable
[    0.000000]   2 base 07EF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00fe200] fe200
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35d30000 - 36e90000
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 7eefd038 0005C (v01 INTEL  DP35DP   00000114      01000013)
[    0.000000] ACPI: FACP 7eefc000 00074 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: DSDT 7eef8000 03D01 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: FACS 7eea0000 00040
[    0.000000] ACPI: APIC 7eef7000 00078 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: WDDT 7eef6000 00040 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: MCFG 7eef5000 0003C (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: ASF! 7eef4000 000A6 (v32 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eef2000 00204 (v01 INTEL     CpuPm 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eef1000 00175 (v01 INTEL   Cpu0Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eef0000 00175 (v01 INTEL   Cpu1Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeef000 00175 (v01 INTEL   Cpu2Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeee000 00175 (v01 INTEL   Cpu3Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeed000 000DD (v01 INTEL   Cpu0Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeec000 000DD (v01 INTEL   Cpu1Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeeb000 000DD (v01 INTEL   Cpu2Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeea000 000DD (v01 INTEL   Cpu3Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ef00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ed15
[    0.000000]     0: 0x0007ed17 -> 0x0007ee06
[    0.000000]     0: 0x0007eef3 -> 0x0007eef4
[    0.000000]     0: 0x0007eeff -> 0x0007ef00
[    0.000000] On node 0 totalpages: 519573
[    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d50200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2287 pages used for memmap
[    0.000000]   HighMem zone: 290073 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f000000 (gap: 7f000000:71000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 515510
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b85b7d91-de93-4555-8471-0b85661eb988 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10398400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ef00)
[    0.000000] Memory: 2023668k/2079744k available (5190k kernel code, 54624k reserved, 2539k data, 700k init, 1169440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2999.582 MHz processor.
[    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.16 BogoMIPS (lpj=11998328)
[    0.008006] pid_max: default: 32768 minimum: 301
[    0.008023] Security Framework initialized
[    0.008035] AppArmor: AppArmor initialized
[    0.008036] Yama: becoming mindful.
[    0.008078] Mount-cache hash table entries: 512
[    0.008174] Initializing cgroup subsys ns
[    0.008177] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008179] Initializing cgroup subsys cpuacct
[    0.008183] Initializing cgroup subsys memory
[    0.008189] Initializing cgroup subsys devices
[    0.008191] Initializing cgroup subsys freezer
[    0.008192] Initializing cgroup subsys net_cls
[    0.008194] Initializing cgroup subsys blkio
[    0.008219] CPU: Physical Processor ID: 0
[    0.008220] CPU: Processor Core ID: 0
[    0.008223] mce: CPU supports 6 MCE banks
[    0.008229] CPU0: Thermal monitoring enabled (TM2)
[    0.008231] using mwait in idle threads.
[    0.009997] ACPI: Core revision 20110112
[    0.016009] ftrace: allocating 23648 entries in 47 pages
[    0.020038] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020331] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060166] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] CPU 1 irqstacks, hard=f3cb2000 soft=f3cb4000
[    0.064003] Booting Node   0, Processors  #1
[    0.012000] Initializing CPU#1
[    0.152022] Brought up 2 CPUs
[    0.152024] Total of 2 processors activated (11998.81 BogoMIPS).
[    0.152985] devtmpfs: initialized
[    0.152985] print_constraints: dummy: 
[    0.152985] Time: 14:39:33  Date: 07/20/11
[    0.152985] NET: Registered protocol family 16
[    0.152985] Trying to unpack rootfs image as initramfs...
[    0.153006] EISA bus registered
[    0.153012] ACPI: bus type pci registered
[    0.153066] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.153069] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.153070] PCI: Using MMCONFIG for extended config space
[    0.153072] PCI: Using configuration type 1 for base access
[    0.168064] bio: create slab <bio-0> at 0
[    0.168911] ACPI: EC: Look up EC in DSDT
[    0.170681] ACPI: Interpreter enabled
[    0.170686] ACPI: (supports S0 S1 S3 S4 S5)
[    0.170704] ACPI: Using IOAPIC for interrupt routing
[    0.204116] ACPI: No dock devices found.
[    0.204120] HEST: Table not found.
[    0.204123] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.204767] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.205990] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.205992] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.205994] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.205996] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff] (ignored)
[    0.205998] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfeafffff] (ignored)
[    0.206000] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
[    0.206009] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
[    0.206044] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
[    0.206072] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.206074] pci 0000:00:01.0: PME# disabled
[    0.206089] pci 0000:00:03.0: [8086:29c4] type 0 class 0x000780
[    0.206100] pci 0000:00:03.0: reg 10: [mem 0x93125900-0x9312590f 64bit]
[    0.206130] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.206132] pci 0000:00:03.0: PME# disabled
[    0.206169] pci 0000:00:19.0: [8086:294c] type 0 class 0x000200
[    0.206185] pci 0000:00:19.0: reg 10: [mem 0x93100000-0x9311ffff]
[    0.206192] pci 0000:00:19.0: reg 14: [mem 0x93124000-0x93124fff]
[    0.206199] pci 0000:00:19.0: reg 18: [io  0x40e0-0x40ff]
[    0.206241] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.206244] pci 0000:00:19.0: PME# disabled
[    0.206260] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.206297] pci 0000:00:1a.0: reg 20: [io  0x40c0-0x40df]
[    0.206335] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.206372] pci 0000:00:1a.1: reg 20: [io  0x40a0-0x40bf]
[    0.206409] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.206446] pci 0000:00:1a.2: reg 20: [io  0x4080-0x409f]
[    0.206491] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.206510] pci 0000:00:1a.7: reg 10: [mem 0x93125400-0x931257ff]
[    0.206575] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.206578] pci 0000:00:1a.7: PME# disabled
[    0.206600] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.206613] pci 0000:00:1b.0: reg 10: [mem 0x93120000-0x93123fff 64bit]
[    0.206659] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.206662] pci 0000:00:1b.0: PME# disabled
[    0.206678] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.206726] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.206729] pci 0000:00:1c.0: PME# disabled
[    0.206747] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.206793] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.206796] pci 0000:00:1c.1: PME# disabled
[    0.206813] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.206860] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.206863] pci 0000:00:1c.2: PME# disabled
[    0.206880] pci 0000:00:1c.3: [8086:2946] type 1 class 0x000604
[    0.206927] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.206930] pci 0000:00:1c.3: PME# disabled
[    0.206950] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.206997] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.207000] pci 0000:00:1c.4: PME# disabled
[    0.207020] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.207057] pci 0000:00:1d.0: reg 20: [io  0x4060-0x407f]
[    0.207094] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.207132] pci 0000:00:1d.1: reg 20: [io  0x4040-0x405f]
[    0.207170] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.207206] pci 0000:00:1d.2: reg 20: [io  0x4020-0x403f]
[    0.207251] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.207270] pci 0000:00:1d.7: reg 10: [mem 0x93125000-0x931253ff]
[    0.207335] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.207339] pci 0000:00:1d.7: PME# disabled
[    0.207355] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.207402] pci 0000:00:1f.0: [8086:2916] type 0 class 0x000601
[    0.207480] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.207491] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.207494] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0810 (mask 007f)
[    0.207527] pci 0000:00:1f.2: [8086:2920] type 0 class 0x000101
[    0.207539] pci 0000:00:1f.2: reg 10: [io  0x4458-0x445f]
[    0.207546] pci 0000:00:1f.2: reg 14: [io  0x446c-0x446f]
[    0.207554] pci 0000:00:1f.2: reg 18: [io  0x4450-0x4457]
[    0.207561] pci 0000:00:1f.2: reg 1c: [io  0x4468-0x446b]
[    0.207568] pci 0000:00:1f.2: reg 20: [io  0x4430-0x443f]
[    0.207575] pci 0000:00:1f.2: reg 24: [io  0x4420-0x442f]
[    0.207605] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.207618] pci 0000:00:1f.3: reg 10: [mem 0x93125800-0x931258ff 64bit]
[    0.207636] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    0.207662] pci 0000:00:1f.5: [8086:2926] type 0 class 0x000101
[    0.207675] pci 0000:00:1f.5: reg 10: [io  0x4448-0x444f]
[    0.207682] pci 0000:00:1f.5: reg 14: [io  0x4464-0x4467]
[    0.207689] pci 0000:00:1f.5: reg 18: [io  0x4440-0x4447]
[    0.207695] pci 0000:00:1f.5: reg 1c: [io  0x4460-0x4463]
[    0.207702] pci 0000:00:1f.5: reg 20: [io  0x4410-0x441f]
[    0.207709] pci 0000:00:1f.5: reg 24: [io  0x4400-0x440f]
[    0.207765] pci 0000:01:00.0: [10de:0421] type 0 class 0x000300
[    0.207774] pci 0000:01:00.0: reg 10: [mem 0x92000000-0x92ffffff]
[    0.207783] pci 0000:01:00.0: reg 14: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.207793] pci 0000:01:00.0: reg 1c: [mem 0x90000000-0x91ffffff 64bit]
[    0.207799] pci 0000:01:00.0: reg 24: [io  0x3000-0x307f]
[    0.207807] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.207845] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.207847] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.207850] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x92ffffff]
[    0.207854] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.207887] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.207890] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.207894] pci 0000:00:1c.0:   bridge window [mem 0x93200000-0x932fffff]
[    0.207899] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.207949] pci 0000:03:00.0: [11ab:6101] type 0 class 0x000101
[    0.207964] pci 0000:03:00.0: reg 10: [io  0x2018-0x201f]
[    0.207975] pci 0000:03:00.0: reg 14: [io  0x2024-0x2027]
[    0.207985] pci 0000:03:00.0: reg 18: [io  0x2010-0x2017]
[    0.207996] pci 0000:03:00.0: reg 1c: [io  0x2020-0x2023]
[    0.208007] pci 0000:03:00.0: reg 20: [io  0x2000-0x200f]
[    0.208024] pci 0000:03:00.0: reg 24: [mem 0x93000000-0x930001ff]
[    0.208064] pci 0000:03:00.0: supports D1
[    0.208066] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.208070] pci 0000:03:00.0: PME# disabled
[    0.208086] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.208094] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.208098] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.208101] pci 0000:00:1c.1:   bridge window [mem 0x93000000-0x930fffff]
[    0.208106] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208140] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.208143] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208146] pci 0000:00:1c.2:   bridge window [mem 0x93300000-0x933fffff]
[    0.208151] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208184] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.208187] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208191] pci 0000:00:1c.3:   bridge window [mem 0x93400000-0x934fffff]
[    0.208195] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208229] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.208232] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208235] pci 0000:00:1c.4:   bridge window [mem 0x93500000-0x935fffff]
[    0.208240] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208267] pci 0000:07:01.0: [1102:0007] type 0 class 0x000401
[    0.208282] pci 0000:07:01.0: reg 10: [io  0x1000-0x101f]
[    0.208340] pci 0000:07:01.0: supports D1 D2
[    0.208380] pci 0000:00:1e.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.208383] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.208386] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.208391] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208393] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.208395] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.208418] pci_bus 0000:00: on NUMA node 0
[    0.208421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.208605] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.208732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.208774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.208814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.208854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.208894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.208971]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.214397] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214447] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
[    0.214494] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.214543] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214590] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
[    0.214637] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214684] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.214730] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214824] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.214826] vgaarb: loaded
[    0.214989] SCSI subsystem initialized
[    0.215039] libata version 3.00 loaded.
[    0.215076] usbcore: registered new interface driver usbfs
[    0.215087] usbcore: registered new interface driver hub
[    0.215107] usbcore: registered new device driver usb
[    0.215187] wmi: Mapper loaded
[    0.215188] PCI: Using ACPI for IRQ routing
[    0.215190] PCI: pci_cache_line_size set to 64 bytes
[    0.215272] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.215274] reserve RAM buffer: 000000007ed15000 - 000000007fffffff 
[    0.215277] reserve RAM buffer: 000000007ee06000 - 000000007fffffff 
[    0.215280] reserve RAM buffer: 000000007eef4000 - 000000007fffffff 
[    0.215282] reserve RAM buffer: 000000007ef00000 - 000000007fffffff 
[    0.215359] NetLabel: Initializing
[    0.215360] NetLabel:  domain hash size = 128
[    0.215361] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.215370] NetLabel:  unlabeled traffic allowed by default
[    0.215474] hpet clockevent registered
[    0.215477] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.215482] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.215486] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.220051] Switching to clocksource hpet
[    0.223795] Switched to NOHz mode on CPU #0
[    0.223872] Switched to NOHz mode on CPU #1
[    0.226032] AppArmor: AppArmor Filesystem Enabled
[    0.226058] pnp: PnP ACPI init
[    0.226075] ACPI: bus type pnp registered
[    0.226714] pnp 00:00: [bus 00-ff]
[    0.226717] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.226719] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.226721] pnp 00:00: [io  0x0d00-0xffff window]
[    0.226723] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.226724] pnp 00:00: [mem 0x000e0000-0x000effff window]
[    0.226726] pnp 00:00: [mem 0xf8000000-0xfeafffff window]
[    0.226728] pnp 00:00: [mem 0x80000000-0xefffffff window]
[    0.226782] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.226792] pnp 00:01: [mem 0xf0000000-0xf7ffffff]
[    0.226793] pnp 00:01: [mem 0xfeb00000-0xfeb03fff]
[    0.226795] pnp 00:01: [mem 0xfed13000-0xfed13fff]
[    0.226797] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.226799] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.226800] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.226802] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.226804] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.226805] pnp 00:01: [mem 0xfed45000-0xfed99fff]
[    0.226807] pnp 00:01: [mem 0x000c0000-0x000dffff]
[    0.226808] pnp 00:01: [mem 0x000e0000-0x000fffff]
[    0.226810] pnp 00:01: [mem 0xffc00000-0xffffffff]
[    0.226863] system 00:01: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.226866] system 00:01: [mem 0xfeb00000-0xfeb03fff] has been reserved
[    0.226868] system 00:01: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.226870] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.226872] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.226874] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.226876] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.226879] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.226881] system 00:01: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.226883] system 00:01: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.226885] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.226888] system 00:01: [mem 0xffc00000-0xffffffff] could not be reserved
[    0.226890] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.226991] pnp 00:02: [io  0x0000-0x000f]
[    0.226992] pnp 00:02: [io  0x0081-0x0083]
[    0.226994] pnp 00:02: [io  0x0087]
[    0.226995] pnp 00:02: [io  0x0089-0x008b]
[    0.226997] pnp 00:02: [io  0x008f]
[    0.226998] pnp 00:02: [io  0x00c0-0x00df]
[    0.227000] pnp 00:02: [dma 4]
[    0.227024] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.227034] pnp 00:03: [io  0x0070-0x0071]
[    0.227036] pnp 00:03: [io  0x0074-0x0077]
[    0.227045] pnp 00:03: [irq 8]
[    0.227070] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.227079] pnp 00:04: [io  0x00f0]
[    0.227083] pnp 00:04: [irq 13]
[    0.227107] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.227115] pnp 00:05: [io  0x0061]
[    0.227139] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.227148] pnp 00:06: [io  0x0500-0x053f]
[    0.227149] pnp 00:06: [io  0x0400-0x047f]
[    0.227151] pnp 00:06: [io  0x0092]
[    0.227152] pnp 00:06: [io  0x0680-0x06ff]
[    0.227154] pnp 00:06: [io  0x0010-0x001f]
[    0.227155] pnp 00:06: [io  0x0072-0x0073]
[    0.227157] pnp 00:06: [io  0x0080]
[    0.227158] pnp 00:06: [io  0x0084-0x0086]
[    0.227160] pnp 00:06: [io  0x0088]
[    0.227161] pnp 00:06: [io  0x008c-0x008e]
[    0.227163] pnp 00:06: [io  0x0090-0x009f]
[    0.227213] system 00:06: [io  0x0500-0x053f] has been reserved
[    0.227216] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.227218] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.227220] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.227256] pnp 00:07: [io  0x0060]
[    0.227258] pnp 00:07: [io  0x0064]
[    0.227300] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.227532] pnp 00:08: [mem 0xfec00000-0xfec000ff]
[    0.227560] pnp 00:08: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.227606] pnp: PnP ACPI: found 9 devices
[    0.227607] ACPI: ACPI bus type pnp unregistered
[    0.227610] PnPBIOS: Disabled by ACPI PNP
[    0.263537] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.263588] pci 0000:00:1c.0: BAR 15: assigned [mem 0x93600000-0x937fffff 64bit pref]
[    0.263593] pci 0000:00:1c.1: BAR 15: assigned [mem 0x93800000-0x939fffff 64bit pref]
[    0.263597] pci 0000:00:1c.2: BAR 15: assigned [mem 0x93a00000-0x93bfffff 64bit pref]
[    0.263601] pci 0000:00:1c.3: BAR 15: assigned [mem 0x93c00000-0x93dfffff 64bit pref]
[    0.263605] pci 0000:00:1c.4: BAR 15: assigned [mem 0x93e00000-0x93ffffff 64bit pref]
[    0.263608] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.263610] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    0.263612] pci 0000:00:1c.3: BAR 13: assigned [io  0x7000-0x7fff]
[    0.263615] pci 0000:00:1c.4: BAR 13: assigned [io  0x8000-0x8fff]
[    0.263618] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.263620] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.263622] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.263625] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x92ffffff]
[    0.263628] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.263631] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.263634] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.263638] pci 0000:00:1c.0:   bridge window [mem 0x93200000-0x932fffff]
[    0.263641] pci 0000:00:1c.0:   bridge window [mem 0x93600000-0x937fffff 64bit pref]
[    0.263646] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.263648] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.263652] pci 0000:00:1c.1:   bridge window [mem 0x93000000-0x930fffff]
[    0.263655] pci 0000:00:1c.1:   bridge window [mem 0x93800000-0x939fffff 64bit pref]
[    0.263660] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.263662] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    0.263666] pci 0000:00:1c.2:   bridge window [mem 0x93300000-0x933fffff]
[    0.263669] pci 0000:00:1c.2:   bridge window [mem 0x93a00000-0x93bfffff 64bit pref]
[    0.263674] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.263677] pci 0000:00:1c.3:   bridge window [io  0x7000-0x7fff]
[    0.263681] pci 0000:00:1c.3:   bridge window [mem 0x93400000-0x934fffff]
[    0.263684] pci 0000:00:1c.3:   bridge window [mem 0x93c00000-0x93dfffff 64bit pref]
[    0.263689] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.263691] pci 0000:00:1c.4:   bridge window [io  0x8000-0x8fff]
[    0.263695] pci 0000:00:1c.4:   bridge window [mem 0x93500000-0x935fffff]
[    0.263698] pci 0000:00:1c.4:   bridge window [mem 0x93e00000-0x93ffffff 64bit pref]
[    0.263703] pci 0000:00:1e.0: PCI bridge to [bus 07-07]
[    0.263705] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.263709] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.263712] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.263732] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.263735] pci 0000:00:01.0: setting latency timer to 64
[    0.263740] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.263745] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.263749] pci 0000:00:1c.0: setting latency timer to 64
[    0.263756] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.263759] pci 0000:00:1c.1: setting latency timer to 64
[    0.263764] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.263769] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.263773] pci 0000:00:1c.2: setting latency timer to 64
[    0.263778] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.263783] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.263787] pci 0000:00:1c.3: setting latency timer to 64
[    0.263792] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.263794] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.263798] pci 0000:00:1c.4: setting latency timer to 64
[    0.263804] pci 0000:00:1e.0: setting latency timer to 64
[    0.263807] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.263809] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.263810] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.263812] pci_bus 0000:01: resource 1 [mem 0x90000000-0x92ffffff]
[    0.263814] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
[    0.263816] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.263818] pci_bus 0000:02: resource 1 [mem 0x93200000-0x932fffff]
[    0.263820] pci_bus 0000:02: resource 2 [mem 0x93600000-0x937fffff 64bit pref]
[    0.263822] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.263823] pci_bus 0000:03: resource 1 [mem 0x93000000-0x930fffff]
[    0.263825] pci_bus 0000:03: resource 2 [mem 0x93800000-0x939fffff 64bit pref]
[    0.263827] pci_bus 0000:04: resource 0 [io  0x6000-0x6fff]
[    0.263829] pci_bus 0000:04: resource 1 [mem 0x93300000-0x933fffff]
[    0.263831] pci_bus 0000:04: resource 2 [mem 0x93a00000-0x93bfffff 64bit pref]
[    0.263833] pci_bus 0000:05: resource 0 [io  0x7000-0x7fff]
[    0.263835] pci_bus 0000:05: resource 1 [mem 0x93400000-0x934fffff]
[    0.263837] pci_bus 0000:05: resource 2 [mem 0x93c00000-0x93dfffff 64bit pref]
[    0.263838] pci_bus 0000:06: resource 0 [io  0x8000-0x8fff]
[    0.263840] pci_bus 0000:06: resource 1 [mem 0x93500000-0x935fffff]
[    0.263842] pci_bus 0000:06: resource 2 [mem 0x93e00000-0x93ffffff 64bit pref]
[    0.263844] pci_bus 0000:07: resource 0 [io  0x1000-0x1fff]
[    0.263846] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.263847] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffff]
[    0.263879] NET: Registered protocol family 2
[    0.263937] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.264123] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.264469] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.264632] TCP: Hash tables configured (established 131072 bind 65536)
[    0.264633] TCP reno registered
[    0.264635] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.264642] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.264711] NET: Registered protocol family 1
[    0.265063] pci 0000:01:00.0: Boot video device
[    0.265070] PCI: CLS 64 bytes, default 64
[    0.265231] cpufreq-nforce2: No nForce2 chipset.
[    0.265333] audit: initializing netlink socket (disabled)
[    0.265340] type=2000 audit(1311172772.260:1): initialized
[    0.272196] highmem bounce pool size: 64 pages
[    0.272200] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.273568] VFS: Disk quotas dquot_6.5.2
[    0.273615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.274120] fuse init (API version 7.16)
[    0.274194] msgmni has been set to 1668
[    0.274373] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.274391] io scheduler noop registered
[    0.274393] io scheduler deadline registered
[    0.274404] io scheduler cfq registered (default)
[    0.274496] pcieport 0000:00:01.0: setting latency timer to 64
[    0.274521] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.274560] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.274592] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.274639] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.274669] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.274718] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.274748] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.274797] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.274829] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.274876] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.274906] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.274971] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.274992] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.275038] intel_idle: MWAIT substates: 0x220
[    0.275039] intel_idle: does not run on family 6 model 15
[    0.275109] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.308016] ACPI: Sleep Button [SLPB]
[    0.308087] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.308092] ACPI: Power Button [PWRF]
[    0.308253] ACPI: acpi_idle registered with cpuidle
[    0.316040] Monitor-Mwait will be used to enter C-1 state
[    0.317114] ERST: Table is not found!
[    0.317179] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.317501] isapnp: Scanning for PnP cards...
[    0.443354] Freeing initrd memory: 17792k freed
[    0.456096] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    0.670335] isapnp: No Plug & Play device found
[    0.673367] Linux agpgart interface v0.103
[    0.674486] brd: module loaded
[    0.674951] loop: module loaded
[    0.675022] i2c-core: driver [adp5520] using legacy suspend method
[    0.675023] i2c-core: driver [adp5520] using legacy resume method
[    0.675107] ata_piix 0000:00:1f.2: version 2.13
[    0.675127] ata_piix 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.675131] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.675168] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.675430] scsi0 : ata_piix
[    0.675504] scsi1 : ata_piix
[    0.675641] ata1: SATA max UDMA/133 cmd 0x4458 ctl 0x446c bmdma 0x4430 irq 21
[    0.675645] ata2: SATA max UDMA/133 cmd 0x4450 ctl 0x4468 bmdma 0x4438 irq 21
[    0.675665] ata_piix 0000:00:1f.5: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.675670] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.675698] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.675872] scsi2 : ata_piix
[    0.675922] scsi3 : ata_piix
[    0.676015] ata3: SATA max UDMA/133 cmd 0x4448 ctl 0x4464 bmdma 0x4410 irq 21
[    0.676018] ata4: SATA max UDMA/133 cmd 0x4440 ctl 0x4460 bmdma 0x4418 irq 21
[    0.676072] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.676092] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.676103] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.676359] Fixed MDIO Bus: probed
[    0.676388] PPP generic driver version 2.4.2
[    0.676421] tun: Universal TUN/TAP device driver, 1.6
[    0.676422] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.676488] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.676500] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.676515] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.676518] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.676545] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.688056] ehci_hcd 0000:00:1a.7: debug port 1
[    0.691945] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.691957] ehci_hcd 0000:00:1a.7: irq 17, io mem 0x93125400
[    0.704012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.704155] hub 1-0:1.0: USB hub found
[    0.704160] hub 1-0:1.0: 6 ports detected
[    0.704241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.704250] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.704253] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.704282] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.704316] ehci_hcd 0000:00:1d.7: debug port 1
[    0.708185] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.708196] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x93125000
[    0.724023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.724154] hub 2-0:1.0: USB hub found
[    0.724158] hub 2-0:1.0: 6 ports detected
[    0.724236] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.724249] uhci_hcd: USB Universal Host Controller Interface driver
[    0.724267] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.724271] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.724274] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.724303] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.724339] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000040c0
[    0.724432] hub 3-0:1.0: USB hub found
[    0.724435] hub 3-0:1.0: 2 ports detected
[    0.724494] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.724499] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.724501] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.724528] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.724558] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040a0
[    0.724649] hub 4-0:1.0: USB hub found
[    0.724652] hub 4-0:1.0: 2 ports detected
[    0.724705] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.724709] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.724711] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.724739] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.728045] uhci_hcd 0000:00:1a.2: irq 17, io base 0x00004080
[    0.728175] hub 5-0:1.0: USB hub found
[    0.728179] hub 5-0:1.0: 2 ports detected
[    0.728242] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.728246] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.728248] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.728277] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.728306] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00004060
[    0.728398] hub 6-0:1.0: USB hub found
[    0.728401] hub 6-0:1.0: 2 ports detected
[    0.728453] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.728457] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.728459] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.728486] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.728524] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004040
[    0.728613] hub 7-0:1.0: USB hub found
[    0.728616] hub 7-0:1.0: 2 ports detected
[    0.728668] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.728672] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.728674] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.728701] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.728730] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004020
[    0.728821] hub 8-0:1.0: USB hub found
[    0.728823] hub 8-0:1.0: 2 ports detected
[    0.728917] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.731986] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.731990] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.732088] mousedev: PS/2 mouse device common for all mice
[    0.732186] rtc_cmos 00:03: RTC can wake from S4
[    0.736074] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.736097] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.736182] device-mapper: uevent: version 1.0.3
[    0.736255] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.736299] device-mapper: multipath: version 1.2.0 loaded
[    0.736301] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.736357] EISA: Probing bus 0 at eisa.0
[    0.736361] Cannot allocate resource for EISA slot 1
[    0.736363] Cannot allocate resource for EISA slot 2
[    0.736364] Cannot allocate resource for EISA slot 3
[    0.736366] Cannot allocate resource for EISA slot 4
[    0.736367] Cannot allocate resource for EISA slot 5
[    0.736369] Cannot allocate resource for EISA slot 6
[    0.736370] Cannot allocate resource for EISA slot 7
[    0.736371] Cannot allocate resource for EISA slot 8
[    0.736373] EISA: Detected 0 cards.
[    0.736411] cpuidle: using governor ladder
[    0.736413] cpuidle: using governor menu
[    0.736630] TCP cubic registered
[    0.736726] NET: Registered protocol family 10
[    0.737168] NET: Registered protocol family 17
[    0.737180] Registering the dns_resolver key type
[    0.737383] Using IPI No-Shortcut mode
[    0.737447] PM: Hibernation image not present or could not be loaded.
[    0.737456] registered taskstats version 1
[    0.737713]   Magic number: 3:127:688
[    0.737772] rtc_cmos 00:03: setting system clock to 2011-07-20 14:39:33 UTC (1311172773)
[    0.737774] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.737775] EDD information not available.
[    1.006531] ata4: SATA link down (SStatus 0 SControl 300)
[    1.017054] ata3: SATA link down (SStatus 0 SControl 300)
[    1.264022] Refined TSC clocksource calibration: 2999.658 MHz.
[    1.264026] Switching to clocksource tsc
[    1.312092] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.472096] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.472107] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.472218] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.472235] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.488309] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OABEA, max UDMA/133
[    1.488312] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.488471] ata1.01: ATA-8: WDC WD3200AAKS-00UU3A0, 01.03B01, max UDMA/133
[    1.488475] ata1.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.501237] ata2.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[    1.501240] ata2.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.504329] ata1.00: configured for UDMA/133
[    1.509090] ata2.00: configured for UDMA/133
[    1.512307] ata1.01: configured for UDMA/133
[    1.512422] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[    1.512576] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.512581] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.512641] sd 0:0:0:0: [sda] Write Protect is off
[    1.512643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.512665] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.512693] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.512796] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.512937] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[    1.513037] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.513085] sd 1:0:0:0: [sdc] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    1.513130] sd 1:0:0:0: [sdc] Write Protect is off
[    1.513132] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.513151] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.517431]  sdc: sdc1
[    1.517614] sd 1:0:0:0: [sdc] Attached SCSI disk
[    1.522831] sd 0:0:1:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.538424]  sda: sda1 sda2 < sda5 >
[    1.538467] sd 0:0:1:0: [sdb] Write Protect is off
[    1.538470] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.538495] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.557273] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.557334]  sdb: sdb1
[    1.557512] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.557535] Freeing unused kernel memory: 700k freed
[    1.557706] Write protecting the kernel text: 5192k
[    1.557739] Write protecting the kernel read-only data: 2148k
[    1.573500] <30>udev[77]: starting version 167
[    1.620047] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.649536] pata_marvell 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.649560] pata_marvell 0000:03:00.0: setting latency timer to 64
[    1.651354] scsi4 : pata_marvell
[    1.653740] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.653741] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.653761] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.653768] e1000e 0000:00:19.0: setting latency timer to 64
[    1.653855] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    1.654287] scsi5 : pata_marvell
[    1.654336] ata5: PATA max UDMA/100 cmd 0x2018 ctl 0x2024 bmdma 0x2000 irq 17
[    1.654338] ata6: DUMMY
[    1.757618] usbcore: registered new interface driver uas
[    1.824403] ata5.00: ATAPI: IDE-DVD ROM 16x, HD08, max UDMA/33
[    1.824406] ata5.01: ATAPI:         48X12X50 CD-RW    1.02 20021009, 1.02, max UDMA/33
[    1.840410] ata5.00: configured for UDMA/33
[    1.856364] ata5.01: configured for UDMA/33
[    1.857235] scsi 4:0:0:0: CD-ROM            IDE-DVD  ROM 16x          HD08 PQ: 0 ANSI: 5
[    1.859442] sr0: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    1.859445] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.859575] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.859645] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    1.861740] scsi 4:0:1:0: CD-ROM                     48X12X50 CD-RW   1.02 PQ: 0 ANSI: 5
[    1.863287] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.863360] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    1.863401] sr 4:0:1:0: Attached scsi generic sg4 type 5
[    1.867850] Initializing USB Mass Storage driver...
[    1.867919] scsi6 : usb-storage 2-6:1.0
[    1.868136] usbcore: registered new interface driver usb-storage
[    1.868138] USB Mass Storage support registered.
[    1.992013] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.014221] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:fa:f2:59
[    2.014223] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.014244] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    2.242479] generic-usb 0003:051D:0002.0001: hiddev0,hidraw0: USB HID v1.10 Device [APC Back-UPS ES 550 FW:843.K2 .D USB FW:K2 ] on usb-0000:00:1a.0-1/input0
[    2.242497] usbcore: registered new interface driver usbhid
[    2.242499] usbhid: USB HID core driver
[    2.329434] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.329437] EXT4-fs (sda1): write access will be enabled during recovery
[    2.336232] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input2
[    2.336308] generic-usb 0003:06A3:8021.0002: input,hidraw1: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:1a.2-1/input0
[    2.479141] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/input/input3
[    2.479261] generic-usb 0003:06A3:8021.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:1a.2-1/input1
[    2.651274] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.651280] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 528031
[    2.666007] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 921500
[    2.666032] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2099770
[    2.683208] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2099738
[    2.716104] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    2.718784] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3543112
[    2.718963] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3543090
[    2.718979] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2100057
[    2.733153] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2100060
[    2.742621] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2099579
[    2.751803] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 528026
[    2.801729] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919548
[    2.801748] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919511
[    2.801764] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919499
[    2.801779] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919498
[    2.801794] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919497
[    2.801808] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919495
[    2.801822] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919494
[    2.852304] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2101345
[    2.868769] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.869398] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.870021] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.870646] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.871036] sd 6:0:0:0: Attached scsi generic sg5 type 0
[    2.871711] sd 6:0:0:1: Attached scsi generic sg6 type 0
[    2.871845] sd 6:0:0:2: Attached scsi generic sg7 type 0
[    2.871962] sd 6:0:0:3: Attached scsi generic sg8 type 0
[    2.877506] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[    2.878129] sd 6:0:0:1: [sde] Attached SCSI removable disk
[    2.879378] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[    2.880015] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[    2.889109] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2102672
[    2.899232] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2101109
[    2.899262] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2101338
[    2.909486] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4
[    2.909570] generic-usb 0003:046D:C044.0004: input,hidraw3: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.2-2/input0
[    2.949674] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 528010
[    2.949698] EXT4-fs (sda1): 22 orphan inodes deleted
[    2.949701] EXT4-fs (sda1): recovery complete
[    3.103818] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.525343] <30>udev[408]: starting version 167
[   11.556848] lp: driver loaded but no devices found
[   11.656248] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.752081] type=1400 audit(1311190784.510:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=646 comm="apparmor_parser"
[   11.752725] type=1400 audit(1311190784.510:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=646 comm="apparmor_parser"
[   11.753130] type=1400 audit(1311190784.510:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=646 comm="apparmor_parser"
[   11.754402] type=1400 audit(1311190784.510:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=684 comm="apparmor_parser"
[   11.755041] type=1400 audit(1311190784.510:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=684 comm="apparmor_parser"
[   11.755443] type=1400 audit(1311190784.510:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=684 comm="apparmor_parser"
[   11.860805] nvidia: module license 'NVIDIA' taints kernel.
[   11.860809] Disabling lock debugging due to kernel taint
[   11.920952] type=1400 audit(1311190784.678:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=840 comm="apparmor_parser"
[   11.924643] type=1400 audit(1311190784.682:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=841 comm="apparmor_parser"
[   11.925285] type=1400 audit(1311190784.682:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=841 comm="apparmor_parser"
[   11.925689] type=1400 audit(1311190784.682:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=841 comm="apparmor_parser"
[   12.092797] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.092835] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   12.092855] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.328156] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   12.380246] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   12.380420] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   12.380571] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.380715] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.380856] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.380995] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.381137] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.384118] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   12.384295] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.833285] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.833292] nvidia 0000:01:00.0: setting latency timer to 64
[   12.833296] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.833748] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   12.865339] CA0106 0000:07:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.865362] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102

```

dmesg.0
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ed15000 (usable)
[    0.000000]  BIOS-e820: 000000007ed15000 - 000000007ed17000 (reserved)
[    0.000000]  BIOS-e820: 000000007ed17000 - 000000007ee06000 (usable)
[    0.000000]  BIOS-e820: 000000007ee06000 - 000000007eeea000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007eeea000 - 000000007eef3000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eef3000 - 000000007eef4000 (usable)
[    0.000000]  BIOS-e820: 000000007eef4000 - 000000007eeff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeff000 - 000000007ef00000 (usable)
[    0.000000]  BIOS-e820: 000000007ef00000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI:                  /DP35DP, BIOS DPP3510J.86A.0276.2007.0903.1413 09/03/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ef00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F000000 mask FFF000000 uncachable
[    0.000000]   2 base 07EF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00fe200] fe200
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35d30000 - 36e90000
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 7eefd038 0005C (v01 INTEL  DP35DP   00000114      01000013)
[    0.000000] ACPI: FACP 7eefc000 00074 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: DSDT 7eef8000 03D01 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: FACS 7eea0000 00040
[    0.000000] ACPI: APIC 7eef7000 00078 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: WDDT 7eef6000 00040 (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: MCFG 7eef5000 0003C (v01 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: ASF! 7eef4000 000A6 (v32 INTEL  DP35DP   00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eef2000 00204 (v01 INTEL     CpuPm 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eef1000 00175 (v01 INTEL   Cpu0Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eef0000 00175 (v01 INTEL   Cpu1Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeef000 00175 (v01 INTEL   Cpu2Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeee000 00175 (v01 INTEL   Cpu3Ist 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeed000 000DD (v01 INTEL   Cpu0Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeec000 000DD (v01 INTEL   Cpu1Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeeb000 000DD (v01 INTEL   Cpu2Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: SSDT 7eeea000 000DD (v01 INTEL   Cpu3Cst 00000114 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ef00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ed15
[    0.000000]     0: 0x0007ed17 -> 0x0007ee06
[    0.000000]     0: 0x0007eef3 -> 0x0007eef4
[    0.000000]     0: 0x0007eeff -> 0x0007ef00
[    0.000000] On node 0 totalpages: 519573
[    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d50200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2287 pages used for memmap
[    0.000000]   HighMem zone: 290073 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f000000 (gap: 7f000000:71000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 515510
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b85b7d91-de93-4555-8471-0b85661eb988 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10398400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ef00)
[    0.000000] Memory: 2023668k/2079744k available (5190k kernel code, 54624k reserved, 2539k data, 700k init, 1169440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2999.732 MHz processor.
[    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.46 BogoMIPS (lpj=11998928)
[    0.008006] pid_max: default: 32768 minimum: 301
[    0.008022] Security Framework initialized
[    0.008036] AppArmor: AppArmor initialized
[    0.008037] Yama: becoming mindful.
[    0.008078] Mount-cache hash table entries: 512
[    0.008174] Initializing cgroup subsys ns
[    0.008177] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008180] Initializing cgroup subsys cpuacct
[    0.008183] Initializing cgroup subsys memory
[    0.008189] Initializing cgroup subsys devices
[    0.008191] Initializing cgroup subsys freezer
[    0.008193] Initializing cgroup subsys net_cls
[    0.008194] Initializing cgroup subsys blkio
[    0.008220] CPU: Physical Processor ID: 0
[    0.008221] CPU: Processor Core ID: 0
[    0.008223] mce: CPU supports 6 MCE banks
[    0.008229] CPU0: Thermal monitoring enabled (TM2)
[    0.008232] using mwait in idle threads.
[    0.009999] ACPI: Core revision 20110112
[    0.016009] ftrace: allocating 23648 entries in 47 pages
[    0.020038] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020332] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060184] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] CPU 1 irqstacks, hard=f3cb2000 soft=f3cb4000
[    0.064003] Booting Node   0, Processors  #1
[    0.012000] Initializing CPU#1
[    0.152021] Brought up 2 CPUs
[    0.152024] Total of 2 processors activated (11999.13 BogoMIPS).
[    0.152983] devtmpfs: initialized
[    0.152983] print_constraints: dummy: 
[    0.152983] Time: 13:36:14  Date: 07/20/11
[    0.152983] NET: Registered protocol family 16
[    0.152983] Trying to unpack rootfs image as initramfs...
[    0.153006] EISA bus registered
[    0.153012] ACPI: bus type pci registered
[    0.153066] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.153069] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.153070] PCI: Using MMCONFIG for extended config space
[    0.153072] PCI: Using configuration type 1 for base access
[    0.168067] bio: create slab <bio-0> at 0
[    0.168912] ACPI: EC: Look up EC in DSDT
[    0.170682] ACPI: Interpreter enabled
[    0.170687] ACPI: (supports S0 S1 S3 S4 S5)
[    0.170705] ACPI: Using IOAPIC for interrupt routing
[    0.204115] ACPI: No dock devices found.
[    0.204119] HEST: Table not found.
[    0.204123] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.204773] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.205996] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.205998] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.206000] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.206002] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff] (ignored)
[    0.206004] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfeafffff] (ignored)
[    0.206006] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
[    0.206015] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
[    0.206053] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
[    0.206079] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.206081] pci 0000:00:01.0: PME# disabled
[    0.206094] pci 0000:00:03.0: [8086:29c4] type 0 class 0x000780
[    0.206106] pci 0000:00:03.0: reg 10: [mem 0x93125900-0x9312590f 64bit]
[    0.206135] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.206138] pci 0000:00:03.0: PME# disabled
[    0.206175] pci 0000:00:19.0: [8086:294c] type 0 class 0x000200
[    0.206190] pci 0000:00:19.0: reg 10: [mem 0x93100000-0x9311ffff]
[    0.206198] pci 0000:00:19.0: reg 14: [mem 0x93124000-0x93124fff]
[    0.206205] pci 0000:00:19.0: reg 18: [io  0x40e0-0x40ff]
[    0.206247] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.206250] pci 0000:00:19.0: PME# disabled
[    0.206266] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.206304] pci 0000:00:1a.0: reg 20: [io  0x40c0-0x40df]
[    0.206342] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.206379] pci 0000:00:1a.1: reg 20: [io  0x40a0-0x40bf]
[    0.206416] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.206454] pci 0000:00:1a.2: reg 20: [io  0x4080-0x409f]
[    0.206500] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.206518] pci 0000:00:1a.7: reg 10: [mem 0x93125400-0x931257ff]
[    0.206582] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.206586] pci 0000:00:1a.7: PME# disabled
[    0.206608] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.206621] pci 0000:00:1b.0: reg 10: [mem 0x93120000-0x93123fff 64bit]
[    0.206667] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.206670] pci 0000:00:1b.0: PME# disabled
[    0.206686] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.206735] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.206738] pci 0000:00:1c.0: PME# disabled
[    0.206755] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.206802] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.206805] pci 0000:00:1c.1: PME# disabled
[    0.206822] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.206869] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.206872] pci 0000:00:1c.2: PME# disabled
[    0.206892] pci 0000:00:1c.3: [8086:2946] type 1 class 0x000604
[    0.206939] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.206942] pci 0000:00:1c.3: PME# disabled
[    0.206961] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.207008] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.207011] pci 0000:00:1c.4: PME# disabled
[    0.207031] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.207068] pci 0000:00:1d.0: reg 20: [io  0x4060-0x407f]
[    0.207106] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.207145] pci 0000:00:1d.1: reg 20: [io  0x4040-0x405f]
[    0.207182] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.207219] pci 0000:00:1d.2: reg 20: [io  0x4020-0x403f]
[    0.207264] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.207283] pci 0000:00:1d.7: reg 10: [mem 0x93125000-0x931253ff]
[    0.207349] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.207353] pci 0000:00:1d.7: PME# disabled
[    0.207369] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.207417] pci 0000:00:1f.0: [8086:2916] type 0 class 0x000601
[    0.207496] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.207507] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.207510] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0810 (mask 007f)
[    0.207542] pci 0000:00:1f.2: [8086:2920] type 0 class 0x000101
[    0.207555] pci 0000:00:1f.2: reg 10: [io  0x4458-0x445f]
[    0.207562] pci 0000:00:1f.2: reg 14: [io  0x446c-0x446f]
[    0.207569] pci 0000:00:1f.2: reg 18: [io  0x4450-0x4457]
[    0.207576] pci 0000:00:1f.2: reg 1c: [io  0x4468-0x446b]
[    0.207582] pci 0000:00:1f.2: reg 20: [io  0x4430-0x443f]
[    0.207589] pci 0000:00:1f.2: reg 24: [io  0x4420-0x442f]
[    0.207620] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.207633] pci 0000:00:1f.3: reg 10: [mem 0x93125800-0x931258ff 64bit]
[    0.207651] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    0.207678] pci 0000:00:1f.5: [8086:2926] type 0 class 0x000101
[    0.207691] pci 0000:00:1f.5: reg 10: [io  0x4448-0x444f]
[    0.207697] pci 0000:00:1f.5: reg 14: [io  0x4464-0x4467]
[    0.207704] pci 0000:00:1f.5: reg 18: [io  0x4440-0x4447]
[    0.207711] pci 0000:00:1f.5: reg 1c: [io  0x4460-0x4463]
[    0.207718] pci 0000:00:1f.5: reg 20: [io  0x4410-0x441f]
[    0.207726] pci 0000:00:1f.5: reg 24: [io  0x4400-0x440f]
[    0.207788] pci 0000:01:00.0: [10de:0421] type 0 class 0x000300
[    0.207797] pci 0000:01:00.0: reg 10: [mem 0x92000000-0x92ffffff]
[    0.207806] pci 0000:01:00.0: reg 14: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.207815] pci 0000:01:00.0: reg 1c: [mem 0x90000000-0x91ffffff 64bit]
[    0.207822] pci 0000:01:00.0: reg 24: [io  0x3000-0x307f]
[    0.207829] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.207866] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.207869] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.207872] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x92ffffff]
[    0.207875] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.207909] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.207912] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.207916] pci 0000:00:1c.0:   bridge window [mem 0x93200000-0x932fffff]
[    0.207921] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.207971] pci 0000:03:00.0: [11ab:6101] type 0 class 0x000101
[    0.207986] pci 0000:03:00.0: reg 10: [io  0x2018-0x201f]
[    0.207997] pci 0000:03:00.0: reg 14: [io  0x2024-0x2027]
[    0.208015] pci 0000:03:00.0: reg 18: [io  0x2010-0x2017]
[    0.208026] pci 0000:03:00.0: reg 1c: [io  0x2020-0x2023]
[    0.208036] pci 0000:03:00.0: reg 20: [io  0x2000-0x200f]
[    0.208047] pci 0000:03:00.0: reg 24: [mem 0x93000000-0x930001ff]
[    0.208087] pci 0000:03:00.0: supports D1
[    0.208089] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.208093] pci 0000:03:00.0: PME# disabled
[    0.208109] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.208117] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.208120] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.208123] pci 0000:00:1c.1:   bridge window [mem 0x93000000-0x930fffff]
[    0.208128] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208162] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.208165] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208168] pci 0000:00:1c.2:   bridge window [mem 0x93300000-0x933fffff]
[    0.208173] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208207] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.208210] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208214] pci 0000:00:1c.3:   bridge window [mem 0x93400000-0x934fffff]
[    0.208219] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208253] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.208256] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208260] pci 0000:00:1c.4:   bridge window [mem 0x93500000-0x935fffff]
[    0.208264] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208292] pci 0000:07:01.0: [1102:0007] type 0 class 0x000401
[    0.208307] pci 0000:07:01.0: reg 10: [io  0x1000-0x101f]
[    0.208364] pci 0000:07:01.0: supports D1 D2
[    0.208403] pci 0000:00:1e.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.208406] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.208410] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.208415] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208417] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.208419] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.208442] pci_bus 0000:00: on NUMA node 0
[    0.208445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.208628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.208755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.208796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.208836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.208876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.208917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.208993]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.214412] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214461] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
[    0.214509] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.214557] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214605] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
[    0.214652] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214698] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.214745] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.214838] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.214841] vgaarb: loaded
[    0.215005] SCSI subsystem initialized
[    0.215061] libata version 3.00 loaded.
[    0.215098] usbcore: registered new interface driver usbfs
[    0.215109] usbcore: registered new interface driver hub
[    0.215130] usbcore: registered new device driver usb
[    0.215210] wmi: Mapper loaded
[    0.215212] PCI: Using ACPI for IRQ routing
[    0.215215] PCI: pci_cache_line_size set to 64 bytes
[    0.215295] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.215297] reserve RAM buffer: 000000007ed15000 - 000000007fffffff 
[    0.215300] reserve RAM buffer: 000000007ee06000 - 000000007fffffff 
[    0.215302] reserve RAM buffer: 000000007eef4000 - 000000007fffffff 
[    0.215304] reserve RAM buffer: 000000007ef00000 - 000000007fffffff 
[    0.215382] NetLabel: Initializing
[    0.215383] NetLabel:  domain hash size = 128
[    0.215385] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.215393] NetLabel:  unlabeled traffic allowed by default
[    0.215498] hpet clockevent registered
[    0.215501] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.215506] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.215510] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.224060] Switching to clocksource hpet
[    0.227883] Switched to NOHz mode on CPU #0
[    0.227963] Switched to NOHz mode on CPU #1
[    0.230048] AppArmor: AppArmor Filesystem Enabled
[    0.230074] pnp: PnP ACPI init
[    0.230090] ACPI: bus type pnp registered
[    0.230730] pnp 00:00: [bus 00-ff]
[    0.230732] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.230734] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.230736] pnp 00:00: [io  0x0d00-0xffff window]
[    0.230738] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.230740] pnp 00:00: [mem 0x000e0000-0x000effff window]
[    0.230742] pnp 00:00: [mem 0xf8000000-0xfeafffff window]
[    0.230744] pnp 00:00: [mem 0x80000000-0xefffffff window]
[    0.230797] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.230807] pnp 00:01: [mem 0xf0000000-0xf7ffffff]
[    0.230809] pnp 00:01: [mem 0xfeb00000-0xfeb03fff]
[    0.230810] pnp 00:01: [mem 0xfed13000-0xfed13fff]
[    0.230812] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.230814] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.230815] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.230817] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.230818] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.230820] pnp 00:01: [mem 0xfed45000-0xfed99fff]
[    0.230821] pnp 00:01: [mem 0x000c0000-0x000dffff]
[    0.230823] pnp 00:01: [mem 0x000e0000-0x000fffff]
[    0.230824] pnp 00:01: [mem 0xffc00000-0xffffffff]
[    0.230877] system 00:01: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.230879] system 00:01: [mem 0xfeb00000-0xfeb03fff] has been reserved
[    0.230881] system 00:01: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.230884] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.230886] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.230888] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.230890] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.230892] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.230895] system 00:01: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.230897] system 00:01: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.230899] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.230901] system 00:01: [mem 0xffc00000-0xffffffff] could not be reserved
[    0.230904] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231004] pnp 00:02: [io  0x0000-0x000f]
[    0.231005] pnp 00:02: [io  0x0081-0x0083]
[    0.231007] pnp 00:02: [io  0x0087]
[    0.231009] pnp 00:02: [io  0x0089-0x008b]
[    0.231010] pnp 00:02: [io  0x008f]
[    0.231011] pnp 00:02: [io  0x00c0-0x00df]
[    0.231013] pnp 00:02: [dma 4]
[    0.231037] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.231046] pnp 00:03: [io  0x0070-0x0071]
[    0.231048] pnp 00:03: [io  0x0074-0x0077]
[    0.231057] pnp 00:03: [irq 8]
[    0.231083] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.231092] pnp 00:04: [io  0x00f0]
[    0.231096] pnp 00:04: [irq 13]
[    0.231119] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.231128] pnp 00:05: [io  0x0061]
[    0.231152] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.231160] pnp 00:06: [io  0x0500-0x053f]
[    0.231162] pnp 00:06: [io  0x0400-0x047f]
[    0.231163] pnp 00:06: [io  0x0092]
[    0.231165] pnp 00:06: [io  0x0680-0x06ff]
[    0.231166] pnp 00:06: [io  0x0010-0x001f]
[    0.231168] pnp 00:06: [io  0x0072-0x0073]
[    0.231169] pnp 00:06: [io  0x0080]
[    0.231170] pnp 00:06: [io  0x0084-0x0086]
[    0.231172] pnp 00:06: [io  0x0088]
[    0.231173] pnp 00:06: [io  0x008c-0x008e]
[    0.231175] pnp 00:06: [io  0x0090-0x009f]
[    0.231226] system 00:06: [io  0x0500-0x053f] has been reserved
[    0.231229] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.231231] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.231233] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231270] pnp 00:07: [io  0x0060]
[    0.231271] pnp 00:07: [io  0x0064]
[    0.231313] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231545] pnp 00:08: [mem 0xfec00000-0xfec000ff]
[    0.231574] pnp 00:08: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.231619] pnp: PnP ACPI: found 9 devices
[    0.231621] ACPI: ACPI bus type pnp unregistered
[    0.231624] PnPBIOS: Disabled by ACPI PNP
[    0.267550] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.267602] pci 0000:00:1c.0: BAR 15: assigned [mem 0x93600000-0x937fffff 64bit pref]
[    0.267606] pci 0000:00:1c.1: BAR 15: assigned [mem 0x93800000-0x939fffff 64bit pref]
[    0.267610] pci 0000:00:1c.2: BAR 15: assigned [mem 0x93a00000-0x93bfffff 64bit pref]
[    0.267614] pci 0000:00:1c.3: BAR 15: assigned [mem 0x93c00000-0x93dfffff 64bit pref]
[    0.267619] pci 0000:00:1c.4: BAR 15: assigned [mem 0x93e00000-0x93ffffff 64bit pref]
[    0.267621] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.267624] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    0.267626] pci 0000:00:1c.3: BAR 13: assigned [io  0x7000-0x7fff]
[    0.267629] pci 0000:00:1c.4: BAR 13: assigned [io  0x8000-0x8fff]
[    0.267632] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.267634] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.267636] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.267639] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x92ffffff]
[    0.267642] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.267645] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.267647] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.267651] pci 0000:00:1c.0:   bridge window [mem 0x93200000-0x932fffff]
[    0.267655] pci 0000:00:1c.0:   bridge window [mem 0x93600000-0x937fffff 64bit pref]
[    0.267660] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.267662] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.267666] pci 0000:00:1c.1:   bridge window [mem 0x93000000-0x930fffff]
[    0.267669] pci 0000:00:1c.1:   bridge window [mem 0x93800000-0x939fffff 64bit pref]
[    0.267674] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.267676] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    0.267680] pci 0000:00:1c.2:   bridge window [mem 0x93300000-0x933fffff]
[    0.267684] pci 0000:00:1c.2:   bridge window [mem 0x93a00000-0x93bfffff 64bit pref]
[    0.267688] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.267691] pci 0000:00:1c.3:   bridge window [io  0x7000-0x7fff]
[    0.267695] pci 0000:00:1c.3:   bridge window [mem 0x93400000-0x934fffff]
[    0.267698] pci 0000:00:1c.3:   bridge window [mem 0x93c00000-0x93dfffff 64bit pref]
[    0.267703] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.267705] pci 0000:00:1c.4:   bridge window [io  0x8000-0x8fff]
[    0.267709] pci 0000:00:1c.4:   bridge window [mem 0x93500000-0x935fffff]
[    0.267712] pci 0000:00:1c.4:   bridge window [mem 0x93e00000-0x93ffffff 64bit pref]
[    0.267717] pci 0000:00:1e.0: PCI bridge to [bus 07-07]
[    0.267719] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.267723] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.267726] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.267747] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.267751] pci 0000:00:01.0: setting latency timer to 64
[    0.267756] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.267762] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.267766] pci 0000:00:1c.0: setting latency timer to 64
[    0.267773] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.267776] pci 0000:00:1c.1: setting latency timer to 64
[    0.267781] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.267786] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.267790] pci 0000:00:1c.2: setting latency timer to 64
[    0.267794] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.267799] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.267803] pci 0000:00:1c.3: setting latency timer to 64
[    0.267807] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.267810] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.267814] pci 0000:00:1c.4: setting latency timer to 64
[    0.267819] pci 0000:00:1e.0: setting latency timer to 64
[    0.267822] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.267824] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.267826] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.267828] pci_bus 0000:01: resource 1 [mem 0x90000000-0x92ffffff]
[    0.267830] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
[    0.267832] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.267833] pci_bus 0000:02: resource 1 [mem 0x93200000-0x932fffff]
[    0.267835] pci_bus 0000:02: resource 2 [mem 0x93600000-0x937fffff 64bit pref]
[    0.267837] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.267839] pci_bus 0000:03: resource 1 [mem 0x93000000-0x930fffff]
[    0.267841] pci_bus 0000:03: resource 2 [mem 0x93800000-0x939fffff 64bit pref]
[    0.267843] pci_bus 0000:04: resource 0 [io  0x6000-0x6fff]
[    0.267844] pci_bus 0000:04: resource 1 [mem 0x93300000-0x933fffff]
[    0.267846] pci_bus 0000:04: resource 2 [mem 0x93a00000-0x93bfffff 64bit pref]
[    0.267848] pci_bus 0000:05: resource 0 [io  0x7000-0x7fff]
[    0.267850] pci_bus 0000:05: resource 1 [mem 0x93400000-0x934fffff]
[    0.267852] pci_bus 0000:05: resource 2 [mem 0x93c00000-0x93dfffff 64bit pref]
[    0.267854] pci_bus 0000:06: resource 0 [io  0x8000-0x8fff]
[    0.267855] pci_bus 0000:06: resource 1 [mem 0x93500000-0x935fffff]
[    0.267857] pci_bus 0000:06: resource 2 [mem 0x93e00000-0x93ffffff 64bit pref]
[    0.267859] pci_bus 0000:07: resource 0 [io  0x1000-0x1fff]
[    0.267861] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.267863] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffff]
[    0.267894] NET: Registered protocol family 2
[    0.267952] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.268142] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.268482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.268647] TCP: Hash tables configured (established 131072 bind 65536)
[    0.268648] TCP reno registered
[    0.268650] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.268658] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.268725] NET: Registered protocol family 1
[    0.269074] pci 0000:01:00.0: Boot video device
[    0.269081] PCI: CLS 64 bytes, default 64
[    0.269241] cpufreq-nforce2: No nForce2 chipset.
[    0.269343] audit: initializing netlink socket (disabled)
[    0.269351] type=2000 audit(1311168973.264:1): initialized
[    0.276200] highmem bounce pool size: 64 pages
[    0.276204] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.277572] VFS: Disk quotas dquot_6.5.2
[    0.277619] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.278122] fuse init (API version 7.16)
[    0.278197] msgmni has been set to 1668
[    0.278374] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.278394] io scheduler noop registered
[    0.278396] io scheduler deadline registered
[    0.278407] io scheduler cfq registered (default)
[    0.278500] pcieport 0000:00:01.0: setting latency timer to 64
[    0.278526] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.278563] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.278594] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.278643] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.278674] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.278722] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.278752] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.278802] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.278833] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.278881] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.278911] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.278977] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.278997] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.279043] intel_idle: MWAIT substates: 0x220
[    0.279045] intel_idle: does not run on family 6 model 15
[    0.279115] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.312016] ACPI: Sleep Button [SLPB]
[    0.312085] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.312089] ACPI: Power Button [PWRF]
[    0.312247] ACPI: acpi_idle registered with cpuidle
[    0.320040] Monitor-Mwait will be used to enter C-1 state
[    0.321119] ERST: Table is not found!
[    0.321185] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.321298] isapnp: Scanning for PnP cards...
[    0.447608] Freeing initrd memory: 17792k freed
[    0.460104] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    0.674134] isapnp: No Plug & Play device found
[    0.677373] Linux agpgart interface v0.103
[    0.678492] brd: module loaded
[    0.678960] loop: module loaded
[    0.679028] i2c-core: driver [adp5520] using legacy suspend method
[    0.679029] i2c-core: driver [adp5520] using legacy resume method
[    0.679110] ata_piix 0000:00:1f.2: version 2.13
[    0.679131] ata_piix 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.679135] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.679172] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.679432] scsi0 : ata_piix
[    0.679503] scsi1 : ata_piix
[    0.679640] ata1: SATA max UDMA/133 cmd 0x4458 ctl 0x446c bmdma 0x4430 irq 21
[    0.679644] ata2: SATA max UDMA/133 cmd 0x4450 ctl 0x4468 bmdma 0x4438 irq 21
[    0.679665] ata_piix 0000:00:1f.5: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.679670] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.679699] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.679877] scsi2 : ata_piix
[    0.679931] scsi3 : ata_piix
[    0.680022] ata3: SATA max UDMA/133 cmd 0x4448 ctl 0x4464 bmdma 0x4410 irq 21
[    0.680025] ata4: SATA max UDMA/133 cmd 0x4440 ctl 0x4460 bmdma 0x4418 irq 21
[    0.680071] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.680091] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.680101] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.680357] Fixed MDIO Bus: probed
[    0.680386] PPP generic driver version 2.4.2
[    0.680417] tun: Universal TUN/TAP device driver, 1.6
[    0.680418] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.680485] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.680496] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.680512] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.680515] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.680542] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.688064] ehci_hcd 0000:00:1a.7: debug port 1
[    0.691941] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.691952] ehci_hcd 0000:00:1a.7: irq 17, io mem 0x93125400
[    0.704012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.704143] hub 1-0:1.0: USB hub found
[    0.704148] hub 1-0:1.0: 6 ports detected
[    0.704233] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.704241] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.704244] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.704272] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.704307] ehci_hcd 0000:00:1d.7: debug port 1
[    0.708180] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.708191] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x93125000
[    0.724022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.724139] hub 2-0:1.0: USB hub found
[    0.724144] hub 2-0:1.0: 6 ports detected
[    0.724229] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.724240] uhci_hcd: USB Universal Host Controller Interface driver
[    0.724258] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.724262] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.724265] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.724294] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.724331] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000040c0
[    0.724425] hub 3-0:1.0: USB hub found
[    0.724429] hub 3-0:1.0: 2 ports detected
[    0.724485] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.724489] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.724492] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.724520] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.724550] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040a0
[    0.724638] hub 4-0:1.0: USB hub found
[    0.724641] hub 4-0:1.0: 2 ports detected
[    0.724694] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.724698] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.724700] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.724727] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.728046] uhci_hcd 0000:00:1a.2: irq 17, io base 0x00004080
[    0.728174] hub 5-0:1.0: USB hub found
[    0.728178] hub 5-0:1.0: 2 ports detected
[    0.728242] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.728247] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.728249] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.728276] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.728305] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00004060
[    0.728395] hub 6-0:1.0: USB hub found
[    0.728398] hub 6-0:1.0: 2 ports detected
[    0.728451] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.728455] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.728458] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.728486] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.728522] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004040
[    0.728611] hub 7-0:1.0: USB hub found
[    0.728614] hub 7-0:1.0: 2 ports detected
[    0.728668] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.728672] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.728675] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.728702] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.728731] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004020
[    0.728821] hub 8-0:1.0: USB hub found
[    0.728823] hub 8-0:1.0: 2 ports detected
[    0.728916] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.731991] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.731995] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.732098] mousedev: PS/2 mouse device common for all mice
[    0.732200] rtc_cmos 00:03: RTC can wake from S4
[    0.732247] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.732267] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.732327] device-mapper: uevent: version 1.0.3
[    0.732390] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.732436] device-mapper: multipath: version 1.2.0 loaded
[    0.732438] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.732492] EISA: Probing bus 0 at eisa.0
[    0.732496] Cannot allocate resource for EISA slot 1
[    0.732498] Cannot allocate resource for EISA slot 2
[    0.732499] Cannot allocate resource for EISA slot 3
[    0.732501] Cannot allocate resource for EISA slot 4
[    0.732502] Cannot allocate resource for EISA slot 5
[    0.732504] Cannot allocate resource for EISA slot 6
[    0.732505] Cannot allocate resource for EISA slot 7
[    0.732506] Cannot allocate resource for EISA slot 8
[    0.732508] EISA: Detected 0 cards.
[    0.732545] cpuidle: using governor ladder
[    0.732546] cpuidle: using governor menu
[    0.732762] TCP cubic registered
[    0.732860] NET: Registered protocol family 10
[    0.733306] NET: Registered protocol family 17
[    0.733317] Registering the dns_resolver key type
[    0.733514] Using IPI No-Shortcut mode
[    0.733584] PM: Hibernation image not present or could not be loaded.
[    0.733592] registered taskstats version 1
[    0.733847]   Magic number: 3:468:635
[    0.733903] rtc_cmos 00:03: setting system clock to 2011-07-20 13:36:14 UTC (1311168974)
[    0.733906] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.733907] EDD information not available.
[    1.010536] ata4: SATA link down (SStatus 0 SControl 300)
[    1.021063] ata3: SATA link down (SStatus 0 SControl 300)
[    1.188024] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.268053] Refined TSC clocksource calibration: 2999.658 MHz.
[    1.268058] Switching to clocksource tsc
[    1.476065] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.476076] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.476188] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.476205] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.492301] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OABEA, max UDMA/133
[    1.492304] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.492477] ata1.01: ATA-8: WDC WD3200AAKS-00UU3A0, 01.03B01, max UDMA/133
[    1.492480] ata1.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.506250] ata2.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[    1.506253] ata2.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.508309] ata1.00: configured for UDMA/133
[    1.512900] ata2.00: configured for UDMA/133
[    1.516563] ata1.01: configured for UDMA/133
[    1.516682] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[    1.516809] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.516812] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.516849] sd 0:0:0:0: [sda] Write Protect is off
[    1.516851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.516873] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.516901] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.517004] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.517129] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[    1.517223] sd 1:0:0:0: [sdc] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    1.517228] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.517259] sd 1:0:0:0: [sdc] Write Protect is off
[    1.517261] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.517278] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.522439]  sdc: sdc1
[    1.522603] sd 1:0:0:0: [sdc] Attached SCSI disk
[    1.525008] sd 0:0:1:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.525064] sd 0:0:1:0: [sdb] Write Protect is off
[    1.525068] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.540701]  sda: sda1 sda2 < sda5 >
[    1.540882] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.540946] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.552819]  sdb: sdb1
[    1.553000] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.553024] Freeing unused kernel memory: 700k freed
[    1.553200] Write protecting the kernel text: 5192k
[    1.553233] Write protecting the kernel read-only data: 2148k
[    1.560026] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.569006] <30>udev[77]: starting version 167
[    1.639492] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.639494] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.639519] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.639526] e1000e 0000:00:19.0: setting latency timer to 64
[    1.639614] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    1.656548] pata_marvell 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.656572] pata_marvell 0000:03:00.0: setting latency timer to 64
[    1.657140] usbcore: registered new interface driver uas
[    1.660843] scsi4 : pata_marvell
[    1.661217] Initializing USB Mass Storage driver...
[    1.662746] scsi5 : pata_marvell
[    1.662789] ata5: PATA max UDMA/100 cmd 0x2018 ctl 0x2024 bmdma 0x2000 irq 17
[    1.662791] ata6: DUMMY
[    1.662901] scsi6 : usb-storage 2-6:1.0
[    1.664023] usbcore: registered new interface driver usb-storage
[    1.664024] USB Mass Storage support registered.
[    1.832402] ata5.00: ATAPI: IDE-DVD ROM 16x, HD08, max UDMA/33
[    1.832406] ata5.01: ATAPI:         48X12X50 CD-RW    1.02 20021009, 1.02, max UDMA/33
[    1.848439] ata5.00: configured for UDMA/33
[    1.864336] ata5.01: configured for UDMA/33
[    1.865180] scsi 4:0:0:0: CD-ROM            IDE-DVD  ROM 16x          HD08 PQ: 0 ANSI: 5
[    1.867402] sr0: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    1.867405] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.867534] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.867604] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    1.869806] scsi 4:0:1:0: CD-ROM                     48X12X50 CD-RW   1.02 PQ: 0 ANSI: 5
[    1.871325] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.871436] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    1.871509] sr 4:0:1:0: Attached scsi generic sg4 type 5
[    2.000043] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.010226] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:fa:f2:59
[    2.010229] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.010249] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    2.243555] generic-usb 0003:051D:0002.0001: hiddev0,hidraw0: USB HID v1.10 Device [APC Back-UPS ES 550 FW:843.K2 .D USB FW:K2 ] on usb-0000:00:1a.0-1/input0
[    2.243568] usbcore: registered new interface driver usbhid
[    2.243569] usbhid: USB HID core driver
[    2.344111] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input2
[    2.344180] generic-usb 0003:06A3:8021.0002: input,hidraw1: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:1a.2-1/input0
[    2.389194] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.389197] EXT4-fs (sda1): write access will be enabled during recovery
[    2.487147] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/input/input3
[    2.487281] generic-usb 0003:06A3:8021.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:1a.2-1/input1
[    2.664762] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.665391] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.666015] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.666640] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.667045] sd 6:0:0:0: Attached scsi generic sg5 type 0
[    2.668208] sd 6:0:0:1: Attached scsi generic sg6 type 0
[    2.669183] sd 6:0:0:2: Attached scsi generic sg7 type 0
[    2.669424] sd 6:0:0:3: Attached scsi generic sg8 type 0
[    2.671995] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[    2.673250] sd 6:0:0:1: [sde] Attached SCSI removable disk
[    2.674495] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[    2.675125] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[    2.780033] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    2.973488] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4
[    2.973570] generic-usb 0003:046D:C044.0004: input,hidraw3: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.2-2/input0
[    4.980322] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.980328] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 528032
[    4.980439] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2101050
[    4.980470] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2101345
[    4.980492] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2104815
[    4.980510] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2104374
[    4.980521] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2102675
[    4.980531] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2102672
[    4.980541] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2101302
[    4.980596] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 921500
[    4.980603] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919548
[    4.980614] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919511
[    4.980624] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919499
[    4.980634] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919498
[    4.980644] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919497
[    4.980653] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919495
[    4.980663] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 919470
[    4.980669] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 527997
[    4.980679] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2104068
[    4.980703] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2099563
[    4.980714] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 528004
[    4.980724] EXT4-fs (sda1): 20 orphan inodes deleted
[    4.980725] EXT4-fs (sda1): recovery complete
[    5.297593] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.667810] <30>udev[424]: starting version 167
[   13.697319] lp: driver loaded but no devices found
[   13.799948] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.892802] type=1400 audit(1311186987.657:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=682 comm="apparmor_parser"
[   13.893437] type=1400 audit(1311186987.657:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=682 comm="apparmor_parser"
[   13.893840] type=1400 audit(1311186987.657:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=682 comm="apparmor_parser"
[   13.996886] type=1400 audit(1311186987.761:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=763 comm="apparmor_parser"
[   13.997994] type=1400 audit(1311186987.761:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=764 comm="apparmor_parser"
[   13.998865] type=1400 audit(1311186987.761:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=764 comm="apparmor_parser"
[   13.999269] type=1400 audit(1311186987.761:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=764 comm="apparmor_parser"
[   14.014117] type=1400 audit(1311186987.777:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=765 comm="apparmor_parser"
[   14.024796] type=1400 audit(1311186987.789:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=770 comm="apparmor_parser"
[   14.027837] type=1400 audit(1311186987.789:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=770 comm="apparmor_parser"
[   14.094675] nvidia: module license 'NVIDIA' taints kernel.
[   14.094677] Disabling lock debugging due to kernel taint

```

Xorg.0.log
```
[    13.769] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.769] X Protocol Version 11, Revision 0
[    13.769] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    13.769] Current Operating System: Linux Erebor 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    13.769] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b85b7d91-de93-4555-8471-0b85661eb988 ro quiet splash vt.handoff=7
[    13.769] Build Date: 21 May 2011  11:38:35AM
[    13.769] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    13.769] Current version of pixman: 0.20.2
[    13.769] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    13.769] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.769] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 20 14:39:46 2011
[    13.770] (==) Using config file: "/etc/X11/xorg.conf"
[    13.770] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.770] (==) No Layout section.  Using the first Screen section.
[    13.770] (==) No screen section available. Using defaults.
[    13.770] (**) |-->Screen "Default Screen Section" (0)
[    13.770] (**) |   |-->Monitor "<default monitor>"
[    13.770] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    13.770] (**) |   |-->Device "Default Device"
[    13.770] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    13.770] (==) Automatically adding devices
[    13.770] (==) Automatically enabling devices
[    13.770] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.770] 	Entry deleted from font path.
[    13.770] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.770] 	Entry deleted from font path.
[    13.770] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.770] 	Entry deleted from font path.
[    13.770] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.770] 	Entry deleted from font path.
[    13.770] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.770] 	Entry deleted from font path.
[    13.770] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    13.770] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.770] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.770] (II) Loader magic: 0x81ffde0
[    13.770] (II) Module ABI versions:
[    13.770] 	X.Org ANSI C Emulation: 0.4
[    13.770] 	X.Org Video Driver: 10.0
[    13.770] 	X.Org XInput driver : 12.3
[    13.770] 	X.Org Server Extension : 5.0
[    13.771] (--) PCI:*(0:1:0:0) 10de:0421:3842:c747 rev 161, Mem @ 0x92000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00003000/128
[    13.771] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.771] (II) LoadModule: "extmod"
[    13.928] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.928] (II) Module extmod: vendor="X.Org Foundation"
[    13.928] 	compiled for 1.10.1, module version = 1.0.0
[    13.928] 	Module class: X.Org Server Extension
[    13.928] 	ABI class: X.Org Server Extension, version 5.0
[    13.928] (II) Loading extension MIT-SCREEN-SAVER
[    13.928] (II) Loading extension XFree86-VidModeExtension
[    13.928] (II) Loading extension XFree86-DGA
[    13.928] (II) Loading extension DPMS
[    13.928] (II) Loading extension XVideo
[    13.928] (II) Loading extension XVideo-MotionCompensation
[    13.928] (II) Loading extension X-Resource
[    13.928] (II) LoadModule: "dbe"
[    13.928] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.928] (II) Module dbe: vendor="X.Org Foundation"
[    13.928] 	compiled for 1.10.1, module version = 1.0.0
[    13.929] 	Module class: X.Org Server Extension
[    13.929] 	ABI class: X.Org Server Extension, version 5.0
[    13.929] (II) Loading extension DOUBLE-BUFFER
[    13.929] (II) LoadModule: "glx"
[    13.929] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    13.946] (II) Module glx: vendor="NVIDIA Corporation"
[    13.946] 	compiled for 4.0.2, module version = 1.0.0
[    13.946] 	Module class: X.Org Server Extension
[    13.946] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    13.947] (II) Loading extension GLX
[    13.947] (II) LoadModule: "record"
[    13.947] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.947] (II) Module record: vendor="X.Org Foundation"
[    13.947] 	compiled for 1.10.1, module version = 1.13.0
[    13.947] 	Module class: X.Org Server Extension
[    13.947] 	ABI class: X.Org Server Extension, version 5.0
[    13.947] (II) Loading extension RECORD
[    13.947] (II) LoadModule: "dri"
[    13.947] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.947] (II) Module dri: vendor="X.Org Foundation"
[    13.947] 	compiled for 1.10.1, module version = 1.0.0
[    13.947] 	ABI class: X.Org Server Extension, version 5.0
[    13.947] (II) Loading extension XFree86-DRI
[    13.947] (II) LoadModule: "dri2"
[    13.947] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.947] (II) Module dri2: vendor="X.Org Foundation"
[    13.947] 	compiled for 1.10.1, module version = 1.2.0
[    13.948] 	ABI class: X.Org Server Extension, version 5.0
[    13.948] (II) Loading extension DRI2
[    13.948] (==) Matched nvidia as autoconfigured driver 0
[    13.948] (==) Matched nouveau as autoconfigured driver 1
[    13.948] (==) Matched nv as autoconfigured driver 2
[    13.948] (==) Matched vesa as autoconfigured driver 3
[    13.948] (==) Matched fbdev as autoconfigured driver 4
[    13.948] (==) Assigned the driver to the xf86ConfigLayout
[    13.948] (II) LoadModule: "nvidia"
[    13.948] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    13.948] (II) Module nvidia: vendor="NVIDIA Corporation"
[    13.948] 	compiled for 4.0.2, module version = 1.0.0
[    13.948] 	Module class: X.Org Video Driver
[    13.948] (II) LoadModule: "nouveau"
[    13.948] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    13.948] (II) Module nouveau: vendor="X.Org Foundation"
[    13.948] 	compiled for 1.10.0, module version = 0.0.16
[    13.948] 	Module class: X.Org Video Driver
[    13.948] 	ABI class: X.Org Video Driver, version 10.0
[    13.949] (II) LoadModule: "nv"
[    13.949] (WW) Warning, couldn't open module nv
[    13.949] (II) UnloadModule: "nv"
[    13.949] (II) Unloading nv
[    13.949] (EE) Failed to load module "nv" (module does not exist, 0)
[    13.949] (II) LoadModule: "vesa"
[    13.949] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.949] (II) Module vesa: vendor="X.Org Foundation"
[    13.949] 	compiled for 1.10.0, module version = 2.3.0
[    13.949] 	Module class: X.Org Video Driver
[    13.949] 	ABI class: X.Org Video Driver, version 10.0
[    13.949] (II) LoadModule: "fbdev"
[    13.950] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.950] (II) Module fbdev: vendor="X.Org Foundation"
[    13.950] 	compiled for 1.10.0, module version = 0.4.2
[    13.950] 	ABI class: X.Org Video Driver, version 10.0
[    13.950] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    13.950] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    13.950] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    13.950] (II) NOUVEAU driver for NVIDIA chipset families :
[    13.950] 	RIVA TNT    (NV04)
[    13.950] 	RIVA TNT2   (NV05)
[    13.950] 	GeForce 256 (NV10)
[    13.950] 	GeForce 2   (NV11, NV15)
[    13.950] 	GeForce 4MX (NV17, NV18)
[    13.950] 	GeForce 3   (NV20)
[    13.950] 	GeForce 4Ti (NV25, NV28)
[    13.950] 	GeForce FX  (NV3x)
[    13.950] 	GeForce 6   (NV4x)
[    13.950] 	GeForce 7   (G7x)
[    13.950] 	GeForce 8   (G8x)
[    13.950] (II) VESA: driver for VESA chipsets: vesa
[    13.950] (II) FBDEV: driver for framebuffer: fbdev
[    13.950] (++) using VT number 7

[    13.950] (II) Loading sub module "fb"
[    13.950] (II) LoadModule: "fb"
[    13.950] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.950] (II) Module fb: vendor="X.Org Foundation"
[    13.950] 	compiled for 1.10.1, module version = 1.0.0
[    13.950] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.950] (II) Loading sub module "wfb"
[    13.950] (II) LoadModule: "wfb"
[    13.951] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.951] (II) Module wfb: vendor="X.Org Foundation"
[    13.951] 	compiled for 1.10.1, module version = 1.0.0
[    13.951] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.951] (II) Loading sub module "ramdac"
[    13.951] (II) LoadModule: "ramdac"
[    13.951] (II) Module "ramdac" already built-in
[    13.951] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    13.951] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.951] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.951] (WW) Falling back to old probe method for vesa
[    13.951] (WW) Falling back to old probe method for fbdev
[    13.951] (II) Loading sub module "fbdevhw"
[    13.951] (II) LoadModule: "fbdevhw"
[    13.951] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.951] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.951] 	compiled for 1.10.1, module version = 0.0.2
[    13.951] 	ABI class: X.Org Video Driver, version 10.0
[    13.951] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    13.951] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    13.951] (==) NVIDIA(0): RGB weight 888
[    13.951] (==) NVIDIA(0): Default visual is TrueColor
[    13.951] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.951] (**) NVIDIA(0): Option "NoLogo" "True"
[    14.781] (II) NVIDIA(GPU-0): Display (hp f1503 (CRT-1)) does not support NVIDIA 3D Vision
[    14.781] (II) NVIDIA(GPU-0):     stereo.
[    14.783] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[    14.783] (--) NVIDIA(0): Memory: 524288 kBytes
[    14.783] (--) NVIDIA(0): VideoBIOS: 60.86.41.00.27
[    14.783] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    14.783] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    14.783] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[    14.783] (--) NVIDIA(0):     hp f1503 (CRT-1)
[    14.783] (--) NVIDIA(0): hp f1503 (CRT-1): 400.0 MHz maximum pixel clock
[    14.843] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    14.843] (==) NVIDIA(0): 
[    14.843] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    14.843] (==) NVIDIA(0):     will be used as the requested mode.
[    14.843] (==) NVIDIA(0): 
[    14.843] (II) NVIDIA(0): Validated modes:
[    14.843] (II) NVIDIA(0):     "nvidia-auto-select"
[    14.843] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    14.874] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[    14.874] (--) NVIDIA(0):     option
[    14.874] (II) UnloadModule: "nouveau"
[    14.874] (II) Unloading nouveau
[    14.874] (II) UnloadModule: "vesa"
[    14.874] (II) Unloading vesa
[    14.875] (II) UnloadModule: "fbdev"
[    14.875] (II) Unloading fbdev
[    14.875] (II) UnloadModule: "fbdevhw"
[    14.875] (II) Unloading fbdevhw
[    14.875] (--) Depth 24 pixmap format is 32 bpp
[    14.875] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    14.882] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    14.903] (II) Loading extension NV-GLX
[    14.934] (==) NVIDIA(0): Disabling shared memory pixmaps
[    14.934] (==) NVIDIA(0): Backing store disabled
[    14.934] (==) NVIDIA(0): Silken mouse enabled
[    14.935] (==) NVIDIA(0): DPMS enabled
[    14.935] (II) Loading extension NV-CONTROL
[    14.935] (II) Loading extension XINERAMA
[    14.935] (II) Loading sub module "dri2"
[    14.935] (II) LoadModule: "dri2"
[    14.935] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.935] (II) Module dri2: vendor="X.Org Foundation"
[    14.935] 	compiled for 1.10.1, module version = 1.2.0
[    14.935] 	ABI class: X.Org Server Extension, version 5.0
[    14.935] (II) NVIDIA(0): [DRI2] Setup complete
[    14.935] (==) RandR enabled
[    14.935] (II) Initializing built-in extension Generic Event Extension
[    14.935] (II) Initializing built-in extension SHAPE
[    14.935] (II) Initializing built-in extension MIT-SHM
[    14.935] (II) Initializing built-in extension XInputExtension
[    14.935] (II) Initializing built-in extension XTEST
[    14.935] (II) Initializing built-in extension BIG-REQUESTS
[    14.935] (II) Initializing built-in extension SYNC
[    14.935] (II) Initializing built-in extension XKEYBOARD
[    14.935] (II) Initializing built-in extension XC-MISC
[    14.935] (II) Initializing built-in extension SECURITY
[    14.935] (II) Initializing built-in extension XINERAMA
[    14.935] (II) Initializing built-in extension XFIXES
[    14.935] (II) Initializing built-in extension RENDER
[    14.935] (II) Initializing built-in extension RANDR
[    14.935] (II) Initializing built-in extension COMPOSITE
[    14.935] (II) Initializing built-in extension DAMAGE
[    14.935] (II) Initializing built-in extension GESTURE
[    14.938] (II) Initializing extension GLX
[    14.958] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.966] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.966] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.967] (II) LoadModule: "evdev"
[    14.967] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.967] (II) Module evdev: vendor="X.Org Foundation"
[    14.967] 	compiled for 1.10.0.902, module version = 2.6.0
[    14.967] 	Module class: X.Org XInput Driver
[    14.967] 	ABI class: X.Org XInput driver, version 12.3
[    14.967] (II) Using input driver 'evdev' for 'Power Button'
[    14.967] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.967] (**) Power Button: always reports core events
[    14.967] (**) Power Button: Device: "/dev/input/event1"
[    14.967] (--) Power Button: Found keys
[    14.967] (II) Power Button: Configuring as keyboard
[    14.967] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.967] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.967] (**) Option "xkb_rules" "evdev"
[    14.967] (**) Option "xkb_model" "pc105"
[    14.967] (**) Option "xkb_layout" "us"
[    14.969] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    14.969] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.969] (II) Using input driver 'evdev' for 'Sleep Button'
[    14.969] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.969] (**) Sleep Button: always reports core events
[    14.969] (**) Sleep Button: Device: "/dev/input/event0"
[    14.970] (--) Sleep Button: Found keys
[    14.970] (II) Sleep Button: Configuring as keyboard
[    14.970] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    14.970] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    14.970] (**) Option "xkb_rules" "evdev"
[    14.970] (**) Option "xkb_model" "pc105"
[    14.970] (**) Option "xkb_layout" "us"
[    14.971] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event2)
[    14.971] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.972] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    14.972] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event2"
[    14.972] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    14.972] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    14.972] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input2/event2"
[    14.972] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    14.972] (**) Option "xkb_rules" "evdev"
[    14.972] (**) Option "xkb_model" "pc105"
[    14.972] (**) Option "xkb_layout" "us"
[    14.972] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event3)
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.972] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    14.972] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event3"
[    14.972] (--) Chicony Saitek Eclipse II Keyboard: Found 8 mouse buttons
[    14.972] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    14.972] (II) Chicony Saitek Eclipse II Keyboard: Configuring as mouse
[    14.972] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: YAxisMapping: buttons 4 and 5
[    14.972] (**) Chicony Saitek Eclipse II Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.972] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/input/input3/event3"
[    14.972] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    14.972] (**) Option "xkb_rules" "evdev"
[    14.972] (**) Option "xkb_model" "pc105"
[    14.972] (**) Option "xkb_layout" "us"
[    14.973] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[    14.973] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.973] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    14.973] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.973] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    14.973] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[    14.976] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    14.976] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    14.976] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    14.976] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    14.976] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    14.976] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    14.976] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.976] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.976] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4/event4"
[    14.976] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    14.976] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    14.976] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    14.976] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    14.976] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    14.976] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    14.976] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    14.976] (II) No input driver/identifier specified (ignoring)
[    14.977] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event10)
[    14.977] (II) No input driver/identifier specified (ignoring)
[    14.977] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event11)
[    14.977] (II) No input driver/identifier specified (ignoring)
[    14.977] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event5)
[    14.977] (II) No input driver/identifier specified (ignoring)
[    14.977] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event6)
[    14.977] (II) No input driver/identifier specified (ignoring)
[    14.977] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event7)
[    14.977] (II) No input driver/identifier specified (ignoring)
[    14.978] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
[    14.978] (II) No input driver/identifier specified (ignoring)
[    14.978] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9)
[    14.978] (II) No input driver/identifier specified (ignoring)

```

Xorg.1.log
```
[ 37542.897] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[ 37542.897] X Protocol Version 11, Revision 0
[ 37542.897] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[ 37542.897] Current Operating System: Linux Erebor 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[ 37542.897] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b85b7d91-de93-4555-8471-0b85661eb988 ro quiet splash vt.handoff=7
[ 37542.897] Build Date: 21 May 2011  11:38:35AM
[ 37542.897] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[ 37542.897] Current version of pixman: 0.20.2
[ 37542.897] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 37542.897] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 37542.897] (==) Log file: "/var/log/Xorg.1.log", Time: Sun Jul 17 09:43:08 2011
[ 37542.897] (==) Using config file: "/etc/X11/xorg.conf"
[ 37542.897] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 37542.897] (==) No Layout section.  Using the first Screen section.
[ 37542.897] (==) No screen section available. Using defaults.
[ 37542.897] (**) |-->Screen "Default Screen Section" (0)
[ 37542.897] (**) |   |-->Monitor "<default monitor>"
[ 37542.897] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[ 37542.897] (**) |   |-->Device "Default Device"
[ 37542.897] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[ 37542.897] (==) Automatically adding devices
[ 37542.897] (==) Automatically enabling devices
[ 37542.898] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 37542.898] 	Entry deleted from font path.
[ 37542.898] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 37542.898] 	Entry deleted from font path.
[ 37542.898] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 37542.898] 	Entry deleted from font path.
[ 37542.898] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 37542.898] 	Entry deleted from font path.
[ 37542.898] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 37542.898] 	Entry deleted from font path.
[ 37542.898] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 37542.898] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 37542.898] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 37542.898] (II) Loader magic: 0x81ffde0
[ 37542.898] (II) Module ABI versions:
[ 37542.898] 	X.Org ANSI C Emulation: 0.4
[ 37542.898] 	X.Org Video Driver: 10.0
[ 37542.898] 	X.Org XInput driver : 12.3
[ 37542.898] 	X.Org Server Extension : 5.0
[ 37542.898] (--) PCI:*(0:1:0:0) 10de:0421:3842:c747 rev 161, Mem @ 0x92000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00003000/128
[ 37542.898] (II) Open ACPI successful (/var/run/acpid.socket)
[ 37542.898] (II) LoadModule: "extmod"
[ 37542.899] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 37542.899] (II) Module extmod: vendor="X.Org Foundation"
[ 37542.899] 	compiled for 1.10.1, module version = 1.0.0
[ 37542.899] 	Module class: X.Org Server Extension
[ 37542.899] 	ABI class: X.Org Server Extension, version 5.0
[ 37542.899] (II) Loading extension MIT-SCREEN-SAVER
[ 37542.899] (II) Loading extension XFree86-VidModeExtension
[ 37542.899] (II) Loading extension XFree86-DGA
[ 37542.899] (II) Loading extension DPMS
[ 37542.899] (II) Loading extension XVideo
[ 37542.899] (II) Loading extension XVideo-MotionCompensation
[ 37542.899] (II) Loading extension X-Resource
[ 37542.899] (II) LoadModule: "dbe"
[ 37542.899] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 37542.899] (II) Module dbe: vendor="X.Org Foundation"
[ 37542.899] 	compiled for 1.10.1, module version = 1.0.0
[ 37542.899] 	Module class: X.Org Server Extension
[ 37542.899] 	ABI class: X.Org Server Extension, version 5.0
[ 37542.899] (II) Loading extension DOUBLE-BUFFER
[ 37542.899] (II) LoadModule: "glx"
[ 37542.899] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[ 37542.917] (II) Module glx: vendor="NVIDIA Corporation"
[ 37542.917] 	compiled for 4.0.2, module version = 1.0.0
[ 37542.917] 	Module class: X.Org Server Extension
[ 37542.917] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[ 37542.917] (II) Loading extension GLX
[ 37542.917] (II) LoadModule: "record"
[ 37542.917] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 37542.917] (II) Module record: vendor="X.Org Foundation"
[ 37542.917] 	compiled for 1.10.1, module version = 1.13.0
[ 37542.917] 	Module class: X.Org Server Extension
[ 37542.917] 	ABI class: X.Org Server Extension, version 5.0
[ 37542.917] (II) Loading extension RECORD
[ 37542.917] (II) LoadModule: "dri"
[ 37542.918] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 37542.918] (II) Module dri: vendor="X.Org Foundation"
[ 37542.918] 	compiled for 1.10.1, module version = 1.0.0
[ 37542.918] 	ABI class: X.Org Server Extension, version 5.0
[ 37542.918] (II) Loading extension XFree86-DRI
[ 37542.918] (II) LoadModule: "dri2"
[ 37542.918] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 37542.918] (II) Module dri2: vendor="X.Org Foundation"
[ 37542.918] 	compiled for 1.10.1, module version = 1.2.0
[ 37542.918] 	ABI class: X.Org Server Extension, version 5.0
[ 37542.918] (II) Loading extension DRI2
[ 37542.918] (==) Matched nvidia as autoconfigured driver 0
[ 37542.918] (==) Matched nouveau as autoconfigured driver 1
[ 37542.918] (==) Matched nv as autoconfigured driver 2
[ 37542.918] (==) Matched vesa as autoconfigured driver 3
[ 37542.918] (==) Matched fbdev as autoconfigured driver 4
[ 37542.918] (==) Assigned the driver to the xf86ConfigLayout
[ 37542.918] (II) LoadModule: "nvidia"
[ 37542.918] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 37542.918] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 37542.918] 	compiled for 4.0.2, module version = 1.0.0
[ 37542.918] 	Module class: X.Org Video Driver
[ 37542.918] (II) LoadModule: "nouveau"
[ 37542.919] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 37542.919] (II) Module nouveau: vendor="X.Org Foundation"
[ 37542.919] 	compiled for 1.10.0, module version = 0.0.16
[ 37542.919] 	Module class: X.Org Video Driver
[ 37542.919] 	ABI class: X.Org Video Driver, version 10.0
[ 37542.919] (II) LoadModule: "nv"
[ 37542.919] (WW) Warning, couldn't open module nv
[ 37542.919] (II) UnloadModule: "nv"
[ 37542.919] (II) Unloading nv
[ 37542.919] (EE) Failed to load module "nv" (module does not exist, 0)
[ 37542.919] (II) LoadModule: "vesa"
[ 37542.920] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 37542.920] (II) Module vesa: vendor="X.Org Foundation"
[ 37542.920] 	compiled for 1.10.0, module version = 2.3.0
[ 37542.920] 	Module class: X.Org Video Driver
[ 37542.920] 	ABI class: X.Org Video Driver, version 10.0
[ 37542.920] (II) LoadModule: "fbdev"
[ 37542.920] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 37542.920] (II) Module fbdev: vendor="X.Org Foundation"
[ 37542.920] 	compiled for 1.10.0, module version = 0.4.2
[ 37542.920] 	ABI class: X.Org Video Driver, version 10.0
[ 37542.920] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[ 37542.920] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 37542.920] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[ 37542.920] (II) NOUVEAU driver for NVIDIA chipset families :
[ 37542.920] 	RIVA TNT    (NV04)
[ 37542.920] 	RIVA TNT2   (NV05)
[ 37542.920] 	GeForce 256 (NV10)
[ 37542.920] 	GeForce 2   (NV11, NV15)
[ 37542.920] 	GeForce 4MX (NV17, NV18)
[ 37542.920] 	GeForce 3   (NV20)
[ 37542.920] 	GeForce 4Ti (NV25, NV28)
[ 37542.920] 	GeForce FX  (NV3x)
[ 37542.920] 	GeForce 6   (NV4x)
[ 37542.920] 	GeForce 7   (G7x)
[ 37542.920] 	GeForce 8   (G8x)
[ 37542.920] (II) VESA: driver for VESA chipsets: vesa
[ 37542.920] (II) FBDEV: driver for framebuffer: fbdev
[ 37542.920] (--) using VT number 8

[ 37543.292] (II) Loading sub module "fb"
[ 37543.292] (II) LoadModule: "fb"
[ 37543.292] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 37543.293] (II) Module fb: vendor="X.Org Foundation"
[ 37543.293] 	compiled for 1.10.1, module version = 1.0.0
[ 37543.293] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 37543.293] (II) Loading sub module "wfb"
[ 37543.293] (II) LoadModule: "wfb"
[ 37543.293] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 37543.293] (II) Module wfb: vendor="X.Org Foundation"
[ 37543.293] 	compiled for 1.10.1, module version = 1.0.0
[ 37543.293] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 37543.293] (II) Loading sub module "ramdac"
[ 37543.293] (II) LoadModule: "ramdac"
[ 37543.293] (II) Module "ramdac" already built-in
[ 37543.293] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 37543.293] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 37543.293] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 37543.293] (WW) Falling back to old probe method for vesa
[ 37543.293] (WW) Falling back to old probe method for fbdev
[ 37543.293] (II) Loading sub module "fbdevhw"
[ 37543.293] (II) LoadModule: "fbdevhw"
[ 37543.293] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 37543.293] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 37543.293] 	compiled for 1.10.1, module version = 0.0.2
[ 37543.293] 	ABI class: X.Org Video Driver, version 10.0
[ 37543.293] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[ 37543.293] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[ 37543.293] (==) NVIDIA(0): RGB weight 888
[ 37543.293] (==) NVIDIA(0): Default visual is TrueColor
[ 37543.293] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 37543.293] (**) NVIDIA(0): Option "NoLogo" "True"
[ 37543.377] (II) NVIDIA(GPU-0): Display (hp f1503 (CRT-1)) does not support NVIDIA 3D Vision
[ 37543.377] (II) NVIDIA(GPU-0):     stereo.
[ 37543.379] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[ 37543.379] (--) NVIDIA(0): Memory: 524288 kBytes
[ 37543.379] (--) NVIDIA(0): VideoBIOS: 60.86.41.00.27
[ 37543.379] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 37543.379] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 37543.379] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[ 37543.379] (--) NVIDIA(0):     hp f1503 (CRT-1)
[ 37543.379] (--) NVIDIA(0): hp f1503 (CRT-1): 400.0 MHz maximum pixel clock
[ 37543.439] (II) NVIDIA(0): Assigned Display Device: CRT-1
[ 37543.439] (==) NVIDIA(0): 
[ 37543.439] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[ 37543.439] (==) NVIDIA(0):     will be used as the requested mode.
[ 37543.439] (==) NVIDIA(0): 
[ 37543.439] (II) NVIDIA(0): Validated modes:
[ 37543.439] (II) NVIDIA(0):     "nvidia-auto-select"
[ 37543.439] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[ 37543.461] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[ 37543.461] (--) NVIDIA(0):     option
[ 37543.461] (II) UnloadModule: "nouveau"
[ 37543.461] (II) Unloading nouveau
[ 37543.461] (II) UnloadModule: "vesa"
[ 37543.461] (II) Unloading vesa
[ 37543.461] (II) UnloadModule: "fbdev"
[ 37543.461] (II) Unloading fbdev
[ 37543.461] (II) UnloadModule: "fbdevhw"
[ 37543.461] (II) Unloading fbdevhw
[ 37543.461] (--) Depth 24 pixmap format is 32 bpp
[ 37543.461] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[ 37543.468] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[ 37543.490] (II) Loading extension NV-GLX
[ 37543.521] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 37543.521] (==) NVIDIA(0): Backing store disabled
[ 37543.521] (==) NVIDIA(0): Silken mouse enabled
[ 37543.522] (==) NVIDIA(0): DPMS enabled
[ 37543.522] (II) Loading extension NV-CONTROL
[ 37543.522] (II) Loading extension XINERAMA
[ 37543.522] (II) Loading sub module "dri2"
[ 37543.522] (II) LoadModule: "dri2"
[ 37543.522] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 37543.522] (II) Module dri2: vendor="X.Org Foundation"
[ 37543.522] 	compiled for 1.10.1, module version = 1.2.0
[ 37543.522] 	ABI class: X.Org Server Extension, version 5.0
[ 37543.522] (II) NVIDIA(0): [DRI2] Setup complete
[ 37543.522] (==) RandR enabled
[ 37543.522] (II) Initializing built-in extension Generic Event Extension
[ 37543.522] (II) Initializing built-in extension SHAPE
[ 37543.522] (II) Initializing built-in extension MIT-SHM
[ 37543.522] (II) Initializing built-in extension XInputExtension
[ 37543.522] (II) Initializing built-in extension XTEST
[ 37543.522] (II) Initializing built-in extension BIG-REQUESTS
[ 37543.522] (II) Initializing built-in extension SYNC
[ 37543.522] (II) Initializing built-in extension XKEYBOARD
[ 37543.522] (II) Initializing built-in extension XC-MISC
[ 37543.522] (II) Initializing built-in extension SECURITY
[ 37543.522] (II) Initializing built-in extension XINERAMA
[ 37543.522] (II) Initializing built-in extension XFIXES
[ 37543.522] (II) Initializing built-in extension RENDER
[ 37543.522] (II) Initializing built-in extension RANDR
[ 37543.522] (II) Initializing built-in extension COMPOSITE
[ 37543.522] (II) Initializing built-in extension DAMAGE
[ 37543.522] (II) Initializing built-in extension GESTURE
[ 37543.525] (II) Initializing extension GLX
[ 37543.542] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 37543.551] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 37543.551] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 37543.551] (II) LoadModule: "evdev"
[ 37543.551] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 37543.551] (II) Module evdev: vendor="X.Org Foundation"
[ 37543.551] 	compiled for 1.10.0.902, module version = 2.6.0
[ 37543.551] 	Module class: X.Org XInput Driver
[ 37543.551] 	ABI class: X.Org XInput driver, version 12.3
[ 37543.551] (II) Using input driver 'evdev' for 'Power Button'
[ 37543.551] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 37543.551] (**) Power Button: always reports core events
[ 37543.551] (**) Power Button: Device: "/dev/input/event1"
[ 37543.551] (--) Power Button: Found keys
[ 37543.552] (II) Power Button: Configuring as keyboard
[ 37543.552] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 37543.552] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 37543.552] (**) Option "xkb_rules" "evdev"
[ 37543.552] (**) Option "xkb_model" "pc105"
[ 37543.552] (**) Option "xkb_layout" "us"
[ 37543.554] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[ 37543.554] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 37543.554] (II) Using input driver 'evdev' for 'Sleep Button'
[ 37543.554] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 37543.554] (**) Sleep Button: always reports core events
[ 37543.554] (**) Sleep Button: Device: "/dev/input/event0"
[ 37543.554] (--) Sleep Button: Found keys
[ 37543.554] (II) Sleep Button: Configuring as keyboard
[ 37543.554] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[ 37543.554] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 37543.554] (**) Option "xkb_rules" "evdev"
[ 37543.554] (**) Option "xkb_model" "pc105"
[ 37543.554] (**) Option "xkb_layout" "us"
[ 37543.555] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event2)
[ 37543.555] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[ 37543.555] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[ 37543.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event2"
[ 37543.556] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[ 37543.556] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[ 37543.556] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2/event2"
[ 37543.556] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[ 37543.556] (**) Option "xkb_rules" "evdev"
[ 37543.556] (**) Option "xkb_model" "pc105"
[ 37543.556] (**) Option "xkb_layout" "us"
[ 37543.556] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event3)
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[ 37543.556] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[ 37543.556] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event3"
[ 37543.556] (--) Chicony Saitek Eclipse II Keyboard: Found 8 mouse buttons
[ 37543.556] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[ 37543.556] (II) Chicony Saitek Eclipse II Keyboard: Configuring as mouse
[ 37543.556] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: YAxisMapping: buttons 4 and 5
[ 37543.556] (**) Chicony Saitek Eclipse II Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 37543.556] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input3/event3"
[ 37543.556] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[ 37543.556] (**) Option "xkb_rules" "evdev"
[ 37543.556] (**) Option "xkb_model" "pc105"
[ 37543.556] (**) Option "xkb_layout" "us"
[ 37543.558] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[ 37543.558] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 37543.558] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[ 37543.558] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 37543.558] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[ 37543.558] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[ 37543.560] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[ 37543.560] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[ 37543.560] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[ 37543.560] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[ 37543.560] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[ 37543.560] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[ 37543.560] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[ 37543.560] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 37543.560] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4/event4"
[ 37543.560] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[ 37543.560] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[ 37543.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[ 37543.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[ 37543.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[ 37543.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[ 37543.560] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[ 37543.560] (II) No input driver/identifier specified (ignoring)
[ 37543.561] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event10)
[ 37543.561] (II) No input driver/identifier specified (ignoring)
[ 37543.561] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event11)
[ 37543.561] (II) No input driver/identifier specified (ignoring)
[ 37543.562] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event5)
[ 37543.562] (II) No input driver/identifier specified (ignoring)
[ 37543.562] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event6)
[ 37543.562] (II) No input driver/identifier specified (ignoring)
[ 37543.562] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event7)
[ 37543.562] (II) No input driver/identifier specified (ignoring)
[ 37543.563] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
[ 37543.563] (II) No input driver/identifier specified (ignoring)
[ 37543.563] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9)
[ 37543.563] (II) No input driver/identifier specified (ignoring)

```

Xorg.2.log
```
[ 85042.160] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[ 85042.160] X Protocol Version 11, Revision 0
[ 85042.160] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[ 85042.160] Current Operating System: Linux Erebor 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[ 85042.160] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=b85b7d91-de93-4555-8471-0b85661eb988 ro quiet splash vt.handoff=7
[ 85042.160] Build Date: 21 May 2011  11:38:35AM
[ 85042.160] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[ 85042.160] Current version of pixman: 0.20.2
[ 85042.160] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 85042.160] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 85042.160] (==) Log file: "/var/log/Xorg.2.log", Time: Sat Jul 16 15:22:29 2011
[ 85042.190] (==) Using config file: "/etc/X11/xorg.conf"
[ 85042.190] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 85042.256] (==) No Layout section.  Using the first Screen section.
[ 85042.256] (==) No screen section available. Using defaults.
[ 85042.256] (**) |-->Screen "Default Screen Section" (0)
[ 85042.256] (**) |   |-->Monitor "<default monitor>"
[ 85042.256] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[ 85042.256] (**) |   |-->Device "Default Device"
[ 85042.256] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[ 85042.256] (==) Automatically adding devices
[ 85042.256] (==) Automatically enabling devices
[ 85042.293] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 85042.293] 	Entry deleted from font path.
[ 85042.293] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 85042.293] 	Entry deleted from font path.
[ 85042.293] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 85042.293] 	Entry deleted from font path.
[ 85042.293] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 85042.293] 	Entry deleted from font path.
[ 85042.293] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 85042.293] 	Entry deleted from font path.
[ 85042.314] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 85042.314] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 85042.314] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 85042.314] (II) Loader magic: 0x81ffde0
[ 85042.314] (II) Module ABI versions:
[ 85042.314] 	X.Org ANSI C Emulation: 0.4
[ 85042.314] 	X.Org Video Driver: 10.0
[ 85042.314] 	X.Org XInput driver : 12.3
[ 85042.314] 	X.Org Server Extension : 5.0
[ 85042.315] (--) PCI:*(0:1:0:0) 10de:0421:3842:c747 rev 161, Mem @ 0x92000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00003000/128
[ 85042.315] (II) Open ACPI successful (/var/run/acpid.socket)
[ 85042.315] (II) LoadModule: "extmod"
[ 85042.371] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 85042.390] (II) Module extmod: vendor="X.Org Foundation"
[ 85042.390] 	compiled for 1.10.1, module version = 1.0.0
[ 85042.390] 	Module class: X.Org Server Extension
[ 85042.390] 	ABI class: X.Org Server Extension, version 5.0
[ 85042.390] (II) Loading extension MIT-SCREEN-SAVER
[ 85042.390] (II) Loading extension XFree86-VidModeExtension
[ 85042.390] (II) Loading extension XFree86-DGA
[ 85042.390] (II) Loading extension DPMS
[ 85042.390] (II) Loading extension XVideo
[ 85042.390] (II) Loading extension XVideo-MotionCompensation
[ 85042.390] (II) Loading extension X-Resource
[ 85042.390] (II) LoadModule: "dbe"
[ 85042.390] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 85042.408] (II) Module dbe: vendor="X.Org Foundation"
[ 85042.408] 	compiled for 1.10.1, module version = 1.0.0
[ 85042.408] 	Module class: X.Org Server Extension
[ 85042.408] 	ABI class: X.Org Server Extension, version 5.0
[ 85042.408] (II) Loading extension DOUBLE-BUFFER
[ 85042.408] (II) LoadModule: "glx"
[ 85042.408] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[ 85042.880] (II) Module glx: vendor="NVIDIA Corporation"
[ 85042.880] 	compiled for 4.0.2, module version = 1.0.0
[ 85042.880] 	Module class: X.Org Server Extension
[ 85042.880] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[ 85042.880] (II) Loading extension GLX
[ 85042.880] (II) LoadModule: "record"
[ 85042.880] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 85042.891] (II) Module record: vendor="X.Org Foundation"
[ 85042.891] 	compiled for 1.10.1, module version = 1.13.0
[ 85042.891] 	Module class: X.Org Server Extension
[ 85042.891] 	ABI class: X.Org Server Extension, version 5.0
[ 85042.891] (II) Loading extension RECORD
[ 85042.891] (II) LoadModule: "dri"
[ 85042.891] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 85042.907] (II) Module dri: vendor="X.Org Foundation"
[ 85042.907] 	compiled for 1.10.1, module version = 1.0.0
[ 85042.907] 	ABI class: X.Org Server Extension, version 5.0
[ 85042.907] (II) Loading extension XFree86-DRI
[ 85042.907] (II) LoadModule: "dri2"
[ 85042.907] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 85042.907] (II) Module dri2: vendor="X.Org Foundation"
[ 85042.907] 	compiled for 1.10.1, module version = 1.2.0
[ 85042.907] 	ABI class: X.Org Server Extension, version 5.0
[ 85042.907] (II) Loading extension DRI2
[ 85042.907] (==) Matched nvidia as autoconfigured driver 0
[ 85042.907] (==) Matched nouveau as autoconfigured driver 1
[ 85042.907] (==) Matched nv as autoconfigured driver 2
[ 85042.907] (==) Matched vesa as autoconfigured driver 3
[ 85042.907] (==) Matched fbdev as autoconfigured driver 4
[ 85042.907] (==) Assigned the driver to the xf86ConfigLayout
[ 85042.907] (II) LoadModule: "nvidia"
[ 85042.908] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 85042.946] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 85042.946] 	compiled for 4.0.2, module version = 1.0.0
[ 85042.946] 	Module class: X.Org Video Driver
[ 85042.971] (II) LoadModule: "nouveau"
[ 85042.987] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 85043.002] (II) Module nouveau: vendor="X.Org Foundation"
[ 85043.002] 	compiled for 1.10.0, module version = 0.0.16
[ 85043.002] 	Module class: X.Org Video Driver
[ 85043.002] 	ABI class: X.Org Video Driver, version 10.0
[ 85043.002] (II) LoadModule: "nv"
[ 85043.019] (WW) Warning, couldn't open module nv
[ 85043.019] (II) UnloadModule: "nv"
[ 85043.019] (II) Unloading nv
[ 85043.019] (EE) Failed to load module "nv" (module does not exist, 0)
[ 85043.019] (II) LoadModule: "vesa"
[ 85043.019] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 85043.033] (II) Module vesa: vendor="X.Org Foundation"
[ 85043.033] 	compiled for 1.10.0, module version = 2.3.0
[ 85043.033] 	Module class: X.Org Video Driver
[ 85043.033] 	ABI class: X.Org Video Driver, version 10.0
[ 85043.033] (II) LoadModule: "fbdev"
[ 85043.034] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 85043.043] (II) Module fbdev: vendor="X.Org Foundation"
[ 85043.043] 	compiled for 1.10.0, module version = 0.4.2
[ 85043.043] 	ABI class: X.Org Video Driver, version 10.0
[ 85043.043] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[ 85043.060] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 85043.061] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[ 85043.061] (II) NOUVEAU driver for NVIDIA chipset families :
[ 85043.061] 	RIVA TNT    (NV04)
[ 85043.061] 	RIVA TNT2   (NV05)
[ 85043.061] 	GeForce 256 (NV10)
[ 85043.061] 	GeForce 2   (NV11, NV15)
[ 85043.061] 	GeForce 4MX (NV17, NV18)
[ 85043.061] 	GeForce 3   (NV20)
[ 85043.061] 	GeForce 4Ti (NV25, NV28)
[ 85043.061] 	GeForce FX  (NV3x)
[ 85043.061] 	GeForce 6   (NV4x)
[ 85043.061] 	GeForce 7   (G7x)
[ 85043.061] 	GeForce 8   (G8x)
[ 85043.061] (II) VESA: driver for VESA chipsets: vesa
[ 85043.061] (II) FBDEV: driver for framebuffer: fbdev
[ 85043.061] (--) using VT number 9

[ 85043.583] (II) Loading sub module "fb"
[ 85043.583] (II) LoadModule: "fb"
[ 85043.583] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 85043.667] (II) Module fb: vendor="X.Org Foundation"
[ 85043.667] 	compiled for 1.10.1, module version = 1.0.0
[ 85043.667] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 85043.667] (II) Loading sub module "wfb"
[ 85043.667] (II) LoadModule: "wfb"
[ 85043.667] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 85043.676] (II) Module wfb: vendor="X.Org Foundation"
[ 85043.676] 	compiled for 1.10.1, module version = 1.0.0
[ 85043.676] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 85043.676] (II) Loading sub module "ramdac"
[ 85043.676] (II) LoadModule: "ramdac"
[ 85043.676] (II) Module "ramdac" already built-in
[ 85043.676] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 85043.676] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 85043.676] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 85043.744] (WW) Falling back to old probe method for vesa
[ 85043.744] (WW) Falling back to old probe method for fbdev
[ 85043.744] (II) Loading sub module "fbdevhw"
[ 85043.744] (II) LoadModule: "fbdevhw"
[ 85043.744] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 85043.771] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 85043.771] 	compiled for 1.10.1, module version = 0.0.2
[ 85043.771] 	ABI class: X.Org Video Driver, version 10.0
[ 85043.771] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[ 85043.771] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[ 85043.771] (==) NVIDIA(0): RGB weight 888
[ 85043.771] (==) NVIDIA(0): Default visual is TrueColor
[ 85043.771] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 85043.771] (**) NVIDIA(0): Option "NoLogo" "True"
[ 85043.917] (II) NVIDIA(GPU-0): Display (hp f1503 (CRT-1)) does not support NVIDIA 3D Vision
[ 85043.917] (II) NVIDIA(GPU-0):     stereo.
[ 85043.920] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[ 85043.920] (--) NVIDIA(0): Memory: 524288 kBytes
[ 85043.920] (--) NVIDIA(0): VideoBIOS: 60.86.41.00.27
[ 85043.920] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 85043.920] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 85043.920] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[ 85043.920] (--) NVIDIA(0):     hp f1503 (CRT-1)
[ 85043.920] (--) NVIDIA(0): hp f1503 (CRT-1): 400.0 MHz maximum pixel clock
[ 85043.984] (II) NVIDIA(0): Assigned Display Device: CRT-1
[ 85043.984] (==) NVIDIA(0): 
[ 85043.984] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[ 85043.984] (==) NVIDIA(0):     will be used as the requested mode.
[ 85043.984] (==) NVIDIA(0): 
[ 85043.984] (II) NVIDIA(0): Validated modes:
[ 85043.984] (II) NVIDIA(0):     "nvidia-auto-select"
[ 85043.984] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[ 85044.018] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[ 85044.018] (--) NVIDIA(0):     option
[ 85044.034] (II) UnloadModule: "nouveau"
[ 85044.034] (II) Unloading nouveau
[ 85044.034] (II) UnloadModule: "vesa"
[ 85044.034] (II) Unloading vesa
[ 85044.034] (II) UnloadModule: "fbdev"
[ 85044.034] (II) Unloading fbdev
[ 85044.034] (II) UnloadModule: "fbdevhw"
[ 85044.034] (II) Unloading fbdevhw
[ 85044.034] (--) Depth 24 pixmap format is 32 bpp
[ 85044.034] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[ 85044.050] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[ 85044.083] (II) Loading extension NV-GLX
[ 85044.124] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 85044.124] (==) NVIDIA(0): Backing store disabled
[ 85044.124] (==) NVIDIA(0): Silken mouse enabled
[ 85044.124] (==) NVIDIA(0): DPMS enabled
[ 85044.124] (II) Loading extension NV-CONTROL
[ 85044.125] (II) Loading extension XINERAMA
[ 85044.125] (II) Loading sub module "dri2"
[ 85044.125] (II) LoadModule: "dri2"
[ 85044.125] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 85044.125] (II) Module dri2: vendor="X.Org Foundation"
[ 85044.125] 	compiled for 1.10.1, module version = 1.2.0
[ 85044.125] 	ABI class: X.Org Server Extension, version 5.0
[ 85044.125] (II) NVIDIA(0): [DRI2] Setup complete
[ 85044.125] (==) RandR enabled
[ 85044.125] (II) Initializing built-in extension Generic Event Extension
[ 85044.125] (II) Initializing built-in extension SHAPE
[ 85044.125] (II) Initializing built-in extension MIT-SHM
[ 85044.125] (II) Initializing built-in extension XInputExtension
[ 85044.125] (II) Initializing built-in extension XTEST
[ 85044.125] (II) Initializing built-in extension BIG-REQUESTS
[ 85044.125] (II) Initializing built-in extension SYNC
[ 85044.125] (II) Initializing built-in extension XKEYBOARD
[ 85044.125] (II) Initializing built-in extension XC-MISC
[ 85044.125] (II) Initializing built-in extension SECURITY
[ 85044.125] (II) Initializing built-in extension XINERAMA
[ 85044.125] (II) Initializing built-in extension XFIXES
[ 85044.125] (II) Initializing built-in extension RENDER
[ 85044.125] (II) Initializing built-in extension RANDR
[ 85044.125] (II) Initializing built-in extension COMPOSITE
[ 85044.125] (II) Initializing built-in extension DAMAGE
[ 85044.125] (II) Initializing built-in extension GESTURE
[ 85044.128] (II) Initializing extension GLX
[ 85044.263] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 85044.297] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 85044.297] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 85044.297] (II) LoadModule: "evdev"
[ 85044.297] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 85044.337] (II) Module evdev: vendor="X.Org Foundation"
[ 85044.337] 	compiled for 1.10.0.902, module version = 2.6.0
[ 85044.337] 	Module class: X.Org XInput Driver
[ 85044.337] 	ABI class: X.Org XInput driver, version 12.3
[ 85044.337] (II) Using input driver 'evdev' for 'Power Button'
[ 85044.337] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 85044.337] (**) Power Button: always reports core events
[ 85044.337] (**) Power Button: Device: "/dev/input/event1"
[ 85044.352] (--) Power Button: Found keys
[ 85044.352] (II) Power Button: Configuring as keyboard
[ 85044.352] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 85044.352] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 85044.352] (**) Option "xkb_rules" "evdev"
[ 85044.352] (**) Option "xkb_model" "pc105"
[ 85044.352] (**) Option "xkb_layout" "us"
[ 85044.354] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[ 85044.354] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 85044.354] (II) Using input driver 'evdev' for 'Sleep Button'
[ 85044.354] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 85044.354] (**) Sleep Button: always reports core events
[ 85044.354] (**) Sleep Button: Device: "/dev/input/event0"
[ 85044.372] (--) Sleep Button: Found keys
[ 85044.372] (II) Sleep Button: Configuring as keyboard
[ 85044.372] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[ 85044.372] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 85044.372] (**) Option "xkb_rules" "evdev"
[ 85044.372] (**) Option "xkb_model" "pc105"
[ 85044.372] (**) Option "xkb_layout" "us"
[ 85044.373] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event2)
[ 85044.373] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[ 85044.373] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[ 85044.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 85044.373] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[ 85044.373] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event2"
[ 85044.388] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[ 85044.388] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[ 85044.388] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2/event2"
[ 85044.388] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[ 85044.388] (**) Option "xkb_rules" "evdev"
[ 85044.388] (**) Option "xkb_model" "pc105"
[ 85044.388] (**) Option "xkb_layout" "us"
[ 85044.388] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event3)
[ 85044.388] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[ 85044.388] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[ 85044.388] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 85044.388] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[ 85044.388] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event3"
[ 85044.404] (--) Chicony Saitek Eclipse II Keyboard: Found 8 mouse buttons
[ 85044.404] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[ 85044.404] (II) Chicony Saitek Eclipse II Keyboard: Configuring as mouse
[ 85044.404] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[ 85044.404] (**) Chicony Saitek Eclipse II Keyboard: YAxisMapping: buttons 4 and 5
[ 85044.404] (**) Chicony Saitek Eclipse II Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 85044.404] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input3/event3"
[ 85044.404] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[ 85044.404] (**) Option "xkb_rules" "evdev"
[ 85044.404] (**) Option "xkb_model" "pc105"
[ 85044.404] (**) Option "xkb_layout" "us"
[ 85044.405] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[ 85044.405] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 85044.405] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[ 85044.405] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 85044.405] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[ 85044.405] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[ 85044.428] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[ 85044.428] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[ 85044.428] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[ 85044.428] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[ 85044.428] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[ 85044.428] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[ 85044.428] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[ 85044.428] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 85044.428] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4/event4"
[ 85044.428] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[ 85044.428] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[ 85044.428] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[ 85044.428] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[ 85044.428] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[ 85044.428] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[ 85044.428] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[ 85044.428] (II) No input driver/identifier specified (ignoring)
[ 85044.429] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event10)
[ 85044.429] (II) No input driver/identifier specified (ignoring)
[ 85044.429] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event11)
[ 85044.429] (II) No input driver/identifier specified (ignoring)
[ 85044.429] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event5)
[ 85044.429] (II) No input driver/identifier specified (ignoring)
[ 85044.429] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event6)
[ 85044.429] (II) No input driver/identifier specified (ignoring)
[ 85044.430] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event7)
[ 85044.430] (II) No input driver/identifier specified (ignoring)
[ 85044.430] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
[ 85044.430] (II) No input driver/identifier specified (ignoring)
[ 85044.430] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9)
[ 85044.430] (II) No input driver/identifier specified (ignoring)

```

I have entries for Xorg.3.log, Xorg.4.log, and Xorg.5.log, but they are all blank. What are you looking for in these logs? What does this tell you, or not?

---

### Post by deespeg on 2011-07-21
I have also just installed 11.04 and get the random freezing, but it also happens every time I access the wireless network app.  I am new at this Ubuntu operating system and installed the OP-SYSTEM new, overwriting the old Windows XP OP-SYSTEM that crashed on me. Any help on how to get the system to stop freezing would be great.

---

### Post by FruG3rT on 2011-07-21
Alright, heres my logs:
```
Xorg0 log:
[    27.239] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    27.239] X Protocol Version 11, Revision 0
[    27.239] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    27.239] Current Operating System: Linux Blubber 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    27.239] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=d7cd7dda-6470-4214-8b1a-b6b100be7a6e ro quiet splash vt.handoff=7
[    27.239] Build Date: 21 May 2011  11:38:35AM
[    27.239] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    27.239] Current version of pixman: 0.20.2
[    27.239]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.239] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.239] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 21 19:05:35 2011
[    27.240] (==) Using config file: "/etc/X11/xorg.conf"
[    27.240] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.240] (==) ServerLayout "Layout0"
[    27.240] (**) |-->Screen "Screen0" (0)
[    27.240] (**) |   |-->Monitor "Monitor0"
[    27.240] (**) |   |-->Device "Device0"
[    27.240] (**) |-->Input Device "Keyboard0"
[    27.240] (**) |-->Input Device "Mouse0"
[    27.240] (==) Automatically adding devices
[    27.240] (==) Automatically enabling devices
[    27.240] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    27.240] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.240] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    27.240] (WW) Disabling Keyboard0
[    27.240] (WW) Disabling Mouse0
[    27.240] (II) Loader magic: 0x81ffde0
[    27.240] (II) Module ABI versions:
[    27.240]     X.Org ANSI C Emulation: 0.4
[    27.240]     X.Org Video Driver: 10.0
[    27.240]     X.Org XInput driver : 12.3
[    27.240]     X.Org Server Extension : 5.0
[    27.241] (--) PCI:*(0:2:0:0) 10de:0ca3:3842:1236 rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xee000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
[    27.241] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.241] (II) LoadModule: "extmod"
[    27.241] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.241] (II) Module extmod: vendor="X.Org Foundation"
[    27.241]     compiled for 1.10.1, module version = 1.0.0
[    27.241]     Module class: X.Org Server Extension
[    27.241]     ABI class: X.Org Server Extension, version 5.0
[    27.242] (II) Loading extension MIT-SCREEN-SAVER
[    27.242] (II) Loading extension XFree86-VidModeExtension
[    27.242] (II) Loading extension XFree86-DGA
[    27.242] (II) Loading extension DPMS
[    27.242] (II) Loading extension XVideo
[    27.242] (II) Loading extension XVideo-MotionCompensation
[    27.242] (II) Loading extension X-Resource
[    27.242] (II) LoadModule: "dbe"
[    27.242] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.242] (II) Module dbe: vendor="X.Org Foundation"
[    27.242]     compiled for 1.10.1, module version = 1.0.0
[    27.242]     Module class: X.Org Server Extension
[    27.242]     ABI class: X.Org Server Extension, version 5.0
[    27.242] (II) Loading extension DOUBLE-BUFFER
[    27.242] (II) LoadModule: "glx"
[    27.242] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    27.260] (II) Module glx: vendor="NVIDIA Corporation"
[    27.261]     compiled for 4.0.2, module version = 1.0.0
[    27.261]     Module class: X.Org Server Extension
[    27.261] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    27.261] (II) Loading extension GLX
[    27.261] (II) LoadModule: "record"
[    27.261] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    27.261] (II) Module record: vendor="X.Org Foundation"
[    27.261]     compiled for 1.10.1, module version = 1.13.0
[    27.261]     Module class: X.Org Server Extension
[    27.261]     ABI class: X.Org Server Extension, version 5.0
[    27.261] (II) Loading extension RECORD
[    27.261] (II) LoadModule: "dri"
[    27.261] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.261] (II) Module dri: vendor="X.Org Foundation"
[    27.261]     compiled for 1.10.1, module version = 1.0.0
[    27.261]     ABI class: X.Org Server Extension, version 5.0
[    27.261] (II) Loading extension XFree86-DRI
[    27.261] (II) LoadModule: "dri2"
[    27.261] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.261] (II) Module dri2: vendor="X.Org Foundation"
[    27.261]     compiled for 1.10.1, module version = 1.2.0
[    27.261]     ABI class: X.Org Server Extension, version 5.0
[    27.261] (II) Loading extension DRI2
[    27.261] (II) LoadModule: "nvidia"
[    27.261] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    27.262] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.262]     compiled for 4.0.2, module version = 1.0.0
[    27.262]     Module class: X.Org Video Driver
[    27.262] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    27.262] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    27.262] (++) using VT number 7

[    27.262] (II) Loading sub module "fb"
[    27.262] (II) LoadModule: "fb"
[    27.262] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.262] (II) Module fb: vendor="X.Org Foundation"
[    27.262]     compiled for 1.10.1, module version = 1.0.0
[    27.262]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.262] (II) Loading sub module "wfb"
[    27.262] (II) LoadModule: "wfb"
[    27.263] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.263] (II) Module wfb: vendor="X.Org Foundation"
[    27.263]     compiled for 1.10.1, module version = 1.0.0
[    27.263]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.263] (II) Loading sub module "ramdac"
[    27.263] (II) LoadModule: "ramdac"
[    27.263] (II) Module "ramdac" already built-in
[    27.263] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    27.263] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.263] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.263] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    27.263] (==) NVIDIA(0): RGB weight 888
[    27.263] (==) NVIDIA(0): Default visual is TrueColor
[    27.263] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.813] (II) NVIDIA(GPU-0): Display (Acer V173 (CRT-1)) does not support NVIDIA 3D Vision
[    27.813] (II) NVIDIA(GPU-0):     stereo.
[    27.814] (II) NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:2:0:0 (GPU-0)
[    27.814] (--) NVIDIA(0): Memory: 1048576 kBytes
[    27.814] (--) NVIDIA(0): VideoBIOS: 70.15.20.00.32
[    27.814] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    27.814] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    27.814] (--) NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:2:0:0
[    27.814] (--) NVIDIA(0):     Acer V173 (CRT-1)
[    27.814] (--) NVIDIA(0): Acer V173 (CRT-1): 400.0 MHz maximum pixel clock
[    27.842] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    27.842] (==) NVIDIA(0): 
[    27.842] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    27.842] (==) NVIDIA(0):     will be used as the requested mode.
[    27.843] (==) NVIDIA(0): 
[    27.843] (II) NVIDIA(0): Validated modes:
[    27.843] (II) NVIDIA(0):     "nvidia-auto-select"
[    27.843] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    27.872] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[    27.877] (--) NVIDIA(0):     option
[    27.878] (--) Depth 24 pixmap format is 32 bpp
[    27.878] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    27.881] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    28.077] (II) Loading extension NV-GLX
[    28.096] (==) NVIDIA(0): Disabling shared memory pixmaps
[    28.096] (==) NVIDIA(0): Backing store disabled
[    28.096] (==) NVIDIA(0): Silken mouse enabled
[    28.097] (**) NVIDIA(0): DPMS enabled
[    28.097] (II) Loading extension NV-CONTROL
[    28.097] (II) Loading extension XINERAMA
[    28.097] (II) Loading sub module "dri2"
[    28.097] (II) LoadModule: "dri2"
[    28.097] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.097] (II) Module dri2: vendor="X.Org Foundation"
[    28.097]     compiled for 1.10.1, module version = 1.2.0
[    28.097]     ABI class: X.Org Server Extension, version 5.0
[    28.097] (II) NVIDIA(0): [DRI2] Setup complete
[    28.097] (==) RandR enabled
[    28.097] (II) Initializing built-in extension Generic Event Extension
[    28.097] (II) Initializing built-in extension SHAPE
[    28.097] (II) Initializing built-in extension MIT-SHM
[    28.097] (II) Initializing built-in extension XInputExtension
[    28.097] (II) Initializing built-in extension XTEST
[    28.097] (II) Initializing built-in extension BIG-REQUESTS
[    28.097] (II) Initializing built-in extension SYNC
[    28.097] (II) Initializing built-in extension XKEYBOARD
[    28.097] (II) Initializing built-in extension XC-MISC
[    28.097] (II) Initializing built-in extension SECURITY
[    28.097] (II) Initializing built-in extension XINERAMA
[    28.097] (II) Initializing built-in extension XFIXES
[    28.097] (II) Initializing built-in extension RENDER
[    28.097] (II) Initializing built-in extension RANDR
[    28.097] (II) Initializing built-in extension COMPOSITE
[    28.097] (II) Initializing built-in extension DAMAGE
[    28.097] (II) Initializing built-in extension GESTURE
[    28.100] (II) Initializing extension GLX
[    28.119] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.126] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.126] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.126] (II) LoadModule: "evdev"
[    28.126] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.126] (II) Module evdev: vendor="X.Org Foundation"
[    28.126]     compiled for 1.10.0.902, module version = 2.6.0
[    28.127]     Module class: X.Org XInput Driver
[    28.127]     ABI class: X.Org XInput driver, version 12.3
[    28.127] (II) Using input driver 'evdev' for 'Power Button'
[    28.127] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.127] (**) Power Button: always reports core events
[    28.127] (**) Power Button: Device: "/dev/input/event1"
[    28.127] (--) Power Button: Found keys
[    28.127] (II) Power Button: Configuring as keyboard
[    28.127] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    28.127] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.127] (**) Option "xkb_rules" "evdev"
[    28.127] (**) Option "xkb_model" "pc105"
[    28.127] (**) Option "xkb_layout" "us"
[    28.130] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    28.130] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.130] (II) Using input driver 'evdev' for 'Power Button'
[    28.130] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.130] (**) Power Button: always reports core events
[    28.130] (**) Power Button: Device: "/dev/input/event0"
[    28.130] (--) Power Button: Found keys
[    28.130] (II) Power Button: Configuring as keyboard
[    28.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    28.130] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.130] (**) Option "xkb_rules" "evdev"
[    28.130] (**) Option "xkb_model" "pc105"
[    28.130] (**) Option "xkb_layout" "us"
[    28.132] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event2)
[    28.132] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    28.132] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    28.132] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.132] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    28.132] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event2"
[    28.132] (--) Microsoft Comfort Curve Keyboard 2000: Found keys
[    28.132] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    28.132] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input2/event2"
[    28.132] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[    28.132] (**) Option "xkb_rules" "evdev"
[    28.132] (**) Option "xkb_model" "pc105"
[    28.132] (**) Option "xkb_layout" "us"
[    28.133] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    28.133] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    28.133] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found relative axes
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[    28.133] (II) evdev-grail: failed to open grail, no gesture support
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found keys
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.133] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.1/input/input3/event3"
[    28.133] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[    28.133] (**) Option "xkb_rules" "evdev"
[    28.133] (**) Option "xkb_model" "pc105"
[    28.133] (**) Option "xkb_layout" "us"
[    28.133] (EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: initialized for absolute axes.
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[    28.134] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event4)
[    28.134] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    28.134] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[    28.134] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.134] (**) Logitech USB Trackball: always reports core events
[    28.134] (**) Logitech USB Trackball: Device: "/dev/input/event4"
[    28.148] (--) Logitech USB Trackball: Found 9 mouse buttons
[    28.148] (--) Logitech USB Trackball: Found relative axes
[    28.148] (--) Logitech USB Trackball: Found x and y relative axes
[    28.148] (II) Logitech USB Trackball: Configuring as mouse
[    28.148] (**) Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    28.148] (**) Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.148] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4/event4"
[    28.148] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE)
[    28.148] (II) Logitech USB Trackball: initialized for relative axes.
[    28.148] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    28.148] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    28.148] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    28.148] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    28.148] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    28.148] (II) No input driver/identifier specified (ignoring)


Dmesg log:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.5 present.
[    0.000000] DMI: BIOSTAR Group N61PC-M2S/N61PC-M2S, BIOS 6.00 PG 07/31/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f3a00] f3a00
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35d2a000 - 36e8d000
[    0.000000] ACPI: RSDP 000f7e30 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 7fee3000 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 7fee3080 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110112/tbfadt-557)
[    0.000000] ACPI: DSDT 7fee3100 058B6 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 7fee0000 00040
[    0.000000] ACPI: SSDT 7fee8a80 008F5 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 7fee9380 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: MCFG 7fee93c0 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 7fee89c0 00098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d2a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294356 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=d7cd7dda-6470-4214-8b1a-b6b100be7a6e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
[    0.000000] Memory: 2040704k/2096000k available (5190k kernel code, 54844k reserved, 2539k data, 700k init, 1186696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2712.498 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5424.99 BogoMIPS (lpj=10849992)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004050] Yama: becoming mindful.
[    0.004107] Mount-cache hash table entries: 512
[    0.004223] Initializing cgroup subsys ns
[    0.004226] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004230] Initializing cgroup subsys cpuacct
[    0.004235] Initializing cgroup subsys memory
[    0.004242] Initializing cgroup subsys devices
[    0.004245] Initializing cgroup subsys freezer
[    0.004247] Initializing cgroup subsys net_cls
[    0.004250] Initializing cgroup subsys blkio
[    0.004278] CPU: Physical Processor ID: 0
[    0.004280] CPU: Processor Core ID: 0
[    0.004283] mce: CPU supports 6 MCE banks
[    0.004292] using C1E aware idle routine
[    0.006357] ACPI: Core revision 20110112
[    0.012013] ftrace: allocating 23648 entries in 47 pages
[    0.016062] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059038] CPU0: AMD Athlon(tm) II X2 215 Processor stepping 02
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] CPU 1 irqstacks, hard=f3cb2000 soft=f3cb4000
[    0.060003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.148017] Brought up 2 CPUs
[    0.148020] Total of 2 processors activated (10849.98 BogoMIPS).
[    0.148413] devtmpfs: initialized
[    0.148963] print_constraints: dummy: 
[    0.148995] Time:  2:05:08  Date: 07/22/11
[    0.149025] NET: Registered protocol family 16
[    0.149120] EISA bus registered
[    0.149124] node 0 link 0: io port [9000, ffff]
[    0.149073] Trying to unpack rootfs image as initramfs...
[    0.149130] TOM: 0000000080000000 aka 2048M
[    0.149132] Fam 10h mmconf [f0000000, f00fffff]
[    0.149134] node 0 link 0: mmio [a0000, bffff]
[    0.149137] node 0 link 0: mmio [80000000, efffffff]
[    0.149140] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.149142] node 0 link 0: mmio [f0000000, f03fffff] ==> [f0100000, f03fffff]
[    0.149146] bus: [00, 04] on node 0 link 0
[    0.149148] bus: 00 index 0 [io  0x0000-0xffff]
[    0.149150] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.149152] bus: 00 index 2 [mem 0x80000000-0xefffffff]
[    0.149153] bus: 00 index 3 [mem 0xf0400000-0xffffffff]
[    0.149155] bus: 00 index 4 [mem 0xf0100000-0xf03fffff]
[    0.149162] Extended Config Space enabled on 1 nodes
[    0.149170] ACPI: bus type pci registered
[    0.149228] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.149231] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.149232] PCI: Using MMCONFIG for extended config space
[    0.149234] PCI: Using configuration type 1 for base access
[    0.164115] bio: create slab <bio-0> at 0
[    0.165136] ACPI: EC: Look up EC in DSDT
[    0.168023] ACPI: Interpreter enabled
[    0.168027] ACPI: (supports S0 S1 S4 S5)
[    0.168041] ACPI: Using IOAPIC for interrupt routing
[    0.172066] ACPI: No dock devices found.
[    0.172068] HEST: Table not found.
[    0.172071] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.172632] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
[    0.173608] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
[    0.173611] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
[    0.173613] pci_root PNP0A08:00: host bridge window [io  0x9000-0xffff]
[    0.173615] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df]
[    0.173617] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80]
[    0.173619] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff]
[    0.173621] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.173623] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xefffffff]
[    0.173625] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff]
[    0.173650] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
[    0.173800] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
[    0.173813] pci 0000:00:01.0: reg 18: [io  0x1d00-0x1dff]
[    0.173839] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
[    0.173850] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
[    0.173865] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
[    0.173870] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
[    0.173889] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.173895] pci 0000:00:01.1: PME# disabled
[    0.173905] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
[    0.173943] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
[    0.173952] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
[    0.173980] pci 0000:00:02.0: supports D1 D2
[    0.173982] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.173985] pci 0000:00:02.0: PME# disabled
[    0.173995] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
[    0.174005] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
[    0.174038] pci 0000:00:02.1: supports D1 D2
[    0.174040] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174043] pci 0000:00:02.1: PME# disabled
[    0.174059] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
[    0.174092] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
[    0.174103] pci 0000:00:05.0: reg 10: [mem 0xfe028000-0xfe02bfff]
[    0.174136] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.174138] pci 0000:00:05.0: PME# disabled
[    0.174155] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
[    0.174176] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
[    0.174201] pci 0000:00:07.0: [10de:03ef] type 0 class 0x000680
[    0.174210] pci 0000:00:07.0: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.174214] pci 0000:00:07.0: reg 14: [io  0xec00-0xec07]
[    0.174240] pci 0000:00:07.0: supports D1 D2
[    0.174241] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174245] pci 0000:00:07.0: PME# disabled
[    0.174256] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
[    0.174264] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
[    0.174268] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.174273] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
[    0.174277] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
[    0.174281] pci 0000:00:08.0: reg 20: [io  0xd800-0xd80f]
[    0.174285] pci 0000:00:08.0: reg 24: [mem 0xfe02c000-0xfe02cfff]
[    0.174312] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
[    0.174333] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174335] pci 0000:00:09.0: PME# disabled
[    0.174348] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
[    0.174367] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174370] pci 0000:00:0b.0: PME# disabled
[    0.174383] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
[    0.174402] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174404] pci 0000:00:0c.0: PME# disabled
[    0.174422] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.174437] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.174450] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.174462] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.174477] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.174534] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.174537] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.174540] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.174543] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.174545] pci 0000:00:04.0:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.174548] pci 0000:00:04.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.174550] pci 0000:00:04.0:   bridge window [io  0x9000-0xffff] (subtractive decode)
[    0.174552] pci 0000:00:04.0:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.174554] pci 0000:00:04.0:   bridge window [io  0x1c00-0x1c80] (subtractive decode)
[    0.174556] pci 0000:00:04.0:   bridge window [mem 0xfec80000-0xfecbffff] (subtractive decode)
[    0.174559] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.174561] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xefffffff] (subtractive decode)
[    0.174563] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xfe02ffff] (subtractive decode)
[    0.174591] pci 0000:02:00.0: [10de:0ca3] type 0 class 0x000300
[    0.174599] pci 0000:02:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.174608] pci 0000:02:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.174616] pci 0000:02:00.0: reg 1c: [mem 0xee000000-0xefffffff 64bit pref]
[    0.174622] pci 0000:02:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.174628] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.174661] pci 0000:02:00.1: [10de:0be4] type 0 class 0x000403
[    0.174669] pci 0000:02:00.1: reg 10: [mem 0xfcffc000-0xfcffffff]
[    0.180040] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.180045] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.180048] pci 0000:00:09.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.180052] pci 0000:00:09.0:   bridge window [mem 0xd0000000-0xefffffff 64bit pref]
[    0.180077] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.180080] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.180083] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.180086] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.180106] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.180109] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.180111] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.180114] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.180123] pci_bus 0000:00: on NUMA node 0
[    0.180129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.180383]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.193411] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193443] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193474] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193504] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193535] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
[    0.193565] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193597] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193629] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[    0.193659] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193689] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193720] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.193750] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.193781] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.193811] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193842] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.193880] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.193915] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193946] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.193980] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.194037] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.194091] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.194141] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.194191] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.194241] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.194291] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.194341] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.194390] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[    0.194440] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0, disabled.
[    0.194491] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.194541] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.194592] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
[    0.194643] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[    0.194693] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[    0.194743] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.194794] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.194845] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.194896] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[    0.194946] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0, disabled.
[    0.195032] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.195035] vgaarb: loaded
[    0.195182] SCSI subsystem initialized
[    0.195235] libata version 3.00 loaded.
[    0.195271] usbcore: registered new interface driver usbfs
[    0.195280] usbcore: registered new interface driver hub
[    0.195300] usbcore: registered new device driver usb
[    0.195376] wmi: Mapper loaded
[    0.195378] PCI: Using ACPI for IRQ routing
[    0.195381] PCI: pci_cache_line_size set to 64 bytes
[    0.195393] pci 0000:00:01.0: no compatible bridge window for [io  0x1d00-0x1dff]
[    0.195433] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.195435] reserve RAM buffer: 000000007fee0000 - 000000007fffffff 
[    0.195513] NetLabel: Initializing
[    0.195514] NetLabel:  domain hash size = 128
[    0.195515] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195524] NetLabel:  unlabeled traffic allowed by default
[    0.195550] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.195555] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.195559] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.200081] Switching to clocksource hpet
[    0.203711] Switched to NOHz mode on CPU #0
[    0.203811] Switched to NOHz mode on CPU #1
[    0.205172] AppArmor: AppArmor Filesystem Enabled
[    0.205201] pnp: PnP ACPI init
[    0.205217] ACPI: bus type pnp registered
[    0.205753] pnp 00:00: [bus 00-04]
[    0.205755] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.205758] pnp 00:00: [io  0x0000-0x03af window]
[    0.205761] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.205763] pnp 00:00: [io  0x9000-0xffff window]
[    0.205765] pnp 00:00: [io  0x03b0-0x03df window]
[    0.205767] pnp 00:00: [io  0x1c00-0x1c80 window]
[    0.205769] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
[    0.205771] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.205773] pnp 00:00: [mem 0x80000000-0xefffffff window]
[    0.205774] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
[    0.205776] pnp 00:00: [mem 0x00000000 window]
[    0.205834] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.205880] pnp 00:01: [io  0x1000-0x107f]
[    0.205881] pnp 00:01: [io  0x1080-0x10ff]
[    0.205883] pnp 00:01: [io  0x1400-0x147f]
[    0.205885] pnp 00:01: [io  0x1480-0x14ff]
[    0.205886] pnp 00:01: [io  0x1800-0x187f]
[    0.205888] pnp 00:01: [io  0x1880-0x18ff]
[    0.205890] pnp 00:01: [mem 0x00000000-0xffffffff disabled]
[    0.205892] pnp 00:01: [io  0x2000-0x207f]
[    0.205893] pnp 00:01: [io  0x2080-0x20ff]
[    0.205939] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.205942] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.205944] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.205947] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.205949] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.205951] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.205953] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.205955] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.205958] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.205994] pnp 00:02: [io  0x0010-0x001f]
[    0.205996] pnp 00:02: [io  0x0022-0x003f]
[    0.205997] pnp 00:02: [io  0x0044-0x005f]
[    0.205999] pnp 00:02: [io  0x0062-0x0063]
[    0.206001] pnp 00:02: [io  0x0065-0x006f]
[    0.206002] pnp 00:02: [io  0x0074-0x007f]
[    0.206004] pnp 00:02: [io  0x0091-0x0093]
[    0.206005] pnp 00:02: [io  0x00a2-0x00bf]
[    0.206007] pnp 00:02: [io  0x00e0-0x00ef]
[    0.206009] pnp 00:02: [io  0x04d0-0x04d1]
[    0.206010] pnp 00:02: [io  0x0800-0x087f]
[    0.206012] pnp 00:02: [io  0x0290-0x029f]
[    0.206013] pnp 00:02: [io  0x0290-0x0297]
[    0.206018] pnp 00:02: disabling [io  0x0010-0x001f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206021] pnp 00:02: disabling [io  0x0022-0x003f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206023] pnp 00:02: disabling [io  0x0044-0x005f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206026] pnp 00:02: disabling [io  0x0062-0x0063] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206029] pnp 00:02: disabling [io  0x0065-0x006f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206032] pnp 00:02: disabling [io  0x0074-0x007f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206035] pnp 00:02: disabling [io  0x0091-0x0093] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206037] pnp 00:02: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206040] pnp 00:02: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206079] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.206081] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.206084] system 00:02: [io  0x0290-0x029f] has been reserved
[    0.206086] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.206089] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.206098] pnp 00:03: [dma 4]
[    0.206099] pnp 00:03: [io  0x0000-0x000f]
[    0.206101] pnp 00:03: [io  0x0080-0x0090]
[    0.206102] pnp 00:03: [io  0x0094-0x009f]
[    0.206104] pnp 00:03: [io  0x00c0-0x00df]
[    0.206128] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.206164] pnp 00:04: [irq 0 disabled]
[    0.206177] pnp 00:04: [irq 8]
[    0.206179] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
[    0.206202] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.206221] pnp 00:05: [io  0x0070-0x0073]
[    0.206244] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.206250] pnp 00:06: [io  0x0061]
[    0.206272] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.206278] pnp 00:07: [io  0x00f0-0x00ff]
[    0.206285] pnp 00:07: [irq 13]
[    0.206310] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.206432] pnp 00:08: [io  0x03f0-0x03f5]
[    0.206434] pnp 00:08: [io  0x03f7]
[    0.206441] pnp 00:08: [irq 6]
[    0.206442] pnp 00:08: [dma 2]
[    0.206479] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.206655] pnp 00:09: [io  0x0378-0x037f]
[    0.206662] pnp 00:09: [irq 7]
[    0.206699] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.207158] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
[    0.207202] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.207205] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207259] pnp 00:0b: [mem 0x000f0000-0x000fffff]
[    0.207261] pnp 00:0b: [mem 0xfeff0000-0xfeff00ff]
[    0.207263] pnp 00:0b: [mem 0x7fee0000-0x7fefffff]
[    0.207264] pnp 00:0b: [mem 0xffff0000-0xffffffff]
[    0.207268] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.207270] pnp 00:0b: [mem 0x00100000-0x7fedffff]
[    0.207272] pnp 00:0b: [mem 0x00000000-0xffffffff disabled]
[    0.207274] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.207275] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.207277] pnp 00:0b: [mem 0xfefff000-0xfeffffff]
[    0.207279] pnp 00:0b: [mem 0xfff80000-0xfff80fff]
[    0.207281] pnp 00:0b: [mem 0xfff90000-0xfffbffff]
[    0.207282] pnp 00:0b: [mem 0xfffed000-0xfffeffff]
[    0.207333] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.207336] system 00:0b: [mem 0xfeff0000-0xfeff00ff] has been reserved
[    0.207338] system 00:0b: [mem 0x7fee0000-0x7fefffff] could not be reserved
[    0.207341] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.207343] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.207345] system 00:0b: [mem 0x00100000-0x7fedffff] could not be reserved
[    0.207348] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.207350] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.207353] system 00:0b: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.207355] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.207357] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.207359] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.207362] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.207370] pnp: PnP ACPI: found 12 devices
[    0.207372] ACPI: ACPI bus type pnp unregistered
[    0.207374] PnPBIOS: Disabled by ACPI PNP
[    0.243202] pci 0000:00:01.0: BAR 2: assigned [io  0xd000-0xd0ff]
[    0.243206] pci 0000:00:01.0: BAR 2: set to [io  0xd000-0xd0ff] (PCI address [0xd000-0xd0ff])
[    0.243209] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.243211] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.243216] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.243219] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.243224] pci 0000:02:00.0: BAR 6: assigned [mem 0xe0000000-0xe007ffff pref]
[    0.243226] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.243228] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.243231] pci 0000:00:09.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.243234] pci 0000:00:09.0:   bridge window [mem 0xd0000000-0xefffffff 64bit pref]
[    0.243237] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.243239] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.243242] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.243244] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.243248] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.243250] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.243252] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.243255] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.243263] pci 0000:00:04.0: setting latency timer to 64
[    0.243267] pci 0000:00:09.0: setting latency timer to 64
[    0.243270] pci 0000:00:0b.0: setting latency timer to 64
[    0.243274] pci 0000:00:0c.0: setting latency timer to 64
[    0.243277] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.243279] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.243281] pci_bus 0000:00: resource 6 [io  0x9000-0xffff]
[    0.243282] pci_bus 0000:00: resource 7 [io  0x03b0-0x03df]
[    0.243284] pci_bus 0000:00: resource 8 [io  0x1c00-0x1c80]
[    0.243287] pci_bus 0000:00: resource 9 [mem 0xfec80000-0xfecbffff]
[    0.243289] pci_bus 0000:00: resource 10 [mem 0x000a0000-0x000bffff]
[    0.243291] pci_bus 0000:00: resource 11 [mem 0x80000000-0xefffffff]
[    0.243293] pci_bus 0000:00: resource 12 [mem 0xf4000000-0xfe02ffff]
[    0.243295] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.243297] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.243299] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
[    0.243301] pci_bus 0000:01: resource 4 [io  0x0000-0x03af]
[    0.243303] pci_bus 0000:01: resource 5 [io  0x03e0-0x0cf7]
[    0.243305] pci_bus 0000:01: resource 6 [io  0x9000-0xffff]
[    0.243307] pci_bus 0000:01: resource 7 [io  0x03b0-0x03df]
[    0.243309] pci_bus 0000:01: resource 8 [io  0x1c00-0x1c80]
[    0.243311] pci_bus 0000:01: resource 9 [mem 0xfec80000-0xfecbffff]
[    0.243313] pci_bus 0000:01: resource 10 [mem 0x000a0000-0x000bffff]
[    0.243315] pci_bus 0000:01: resource 11 [mem 0x80000000-0xefffffff]
[    0.243317] pci_bus 0000:01: resource 12 [mem 0xf4000000-0xfe02ffff]
[    0.243320] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.243322] pci_bus 0000:02: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.243324] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xefffffff 64bit pref]
[    0.243326] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.243328] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.243330] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.243332] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.243334] pci_bus 0000:04: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.243336] pci_bus 0000:04: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.243368] NET: Registered protocol family 2
[    0.243421] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.243601] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.244081] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.244305] TCP: Hash tables configured (established 131072 bind 65536)
[    0.244307] TCP reno registered
[    0.244310] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.244318] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.244401] NET: Registered protocol family 1
[    0.260113] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260162] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260218] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260273] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260332] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260394] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260461] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260476] pci 0000:02:00.0: Boot video device
[    0.260484] PCI: CLS 64 bytes, default 64
[    0.260664] cpufreq-nforce2: No nForce2 chipset.
[    0.260764] audit: initializing netlink socket (disabled)
[    0.260773] type=2000 audit(1311300308.260:1): initialized
[    0.268604] highmem bounce pool size: 64 pages
[    0.268608] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.269869] VFS: Disk quotas dquot_6.5.2
[    0.269912] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.270419] fuse init (API version 7.16)
[    0.270486] msgmni has been set to 1667
[    0.270667] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.270686] io scheduler noop registered
[    0.270688] io scheduler deadline registered
[    0.270701] io scheduler cfq registered (default)
[    0.270788] pcieport 0000:00:09.0: setting latency timer to 64
[    0.270813] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.270847] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.270864] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.270892] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.270908] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.270956] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.270976] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.271087] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.271093] ACPI: Power Button [PWRB]
[    0.271139] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.271142] ACPI: Power Button [PWRF]
[    0.271182] ACPI: Fan [FAN] (on)
[    0.271304] ACPI: acpi_idle registered with cpuidle
[    0.272637] ACPI Warning: For \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference (20110112/nspredef-1059)
[    0.272643] ACPI: Expecting a [Reference] package element, found type 0
[    0.272644] ACPI: Invalid passive threshold
[    0.272752] thermal LNXTHERM:00: registered as thermal_zone0
[    0.272755] ACPI: Thermal Zone [THRM] (40 C)
[    0.272790] ERST: Table is not found!
[    0.272894] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.273181] isapnp: Scanning for PnP cards...
[    0.506831] Freeing initrd memory: 17804k freed
[    0.625983] isapnp: No Plug & Play device found
[    0.688393] Linux agpgart interface v0.103
[    0.689394] brd: module loaded
[    0.689803] loop: module loaded
[    0.689880] i2c-core: driver [adp5520] using legacy suspend method
[    0.689881] i2c-core: driver [adp5520] using legacy resume method
[    0.690007] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.690148] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.690163] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.690174] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.690179] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.690416] Fixed MDIO Bus: probed
[    0.690444] PPP generic driver version 2.4.2
[    0.690474] tun: Universal TUN/TAP device driver, 1.6
[    0.690476] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.690538] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.690636] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.690645] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.690657] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.690659] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.690686] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.690773] ehci_hcd 0000:00:02.1: debug port 1
[    0.690782] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.690805] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.700050] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.700194] hub 1-0:1.0: USB hub found
[    0.700198] hub 1-0:1.0: 8 ports detected
[    0.700264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.700409] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.700425] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.700438] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.700441] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.700476] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.700545] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    0.758166] hub 2-0:1.0: USB hub found
[    0.758171] hub 2-0:1.0: 8 ports detected
[    0.758236] uhci_hcd: USB Universal Host Controller Interface driver
[    0.758307] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.791712] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.791713] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.012052] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.040145] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.040272] mousedev: PS/2 mouse device common for all mice
[    1.040375] rtc_cmos 00:05: RTC can wake from S4
[    1.044153] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.044193] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.044278] device-mapper: uevent: version 1.0.3
[    1.044342] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.044438] device-mapper: multipath: version 1.2.0 loaded
[    1.044442] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.044539] EISA: Probing bus 0 at eisa.0
[    1.044541] EISA: Cannot allocate resource for mainboard
[    1.044543] Cannot allocate resource for EISA slot 1
[    1.044544] Cannot allocate resource for EISA slot 2
[    1.044557] EISA: Detected 0 cards.
[    1.044632] cpuidle: using governor ladder
[    1.044634] cpuidle: using governor menu
[    1.044843] TCP cubic registered
[    1.044940] NET: Registered protocol family 10
[    1.045376] NET: Registered protocol family 17
[    1.045390] Registering the dns_resolver key type
[    1.045421] powernow-k8: Found 1 AMD Athlon(tm) II X2 215 Processor (2 cpu cores) (version 2.20.00)
[    1.045458] powernow-k8:    0 : pstate 0 (2700 MHz)
[    1.045460] powernow-k8:    1 : pstate 1 (2100 MHz)
[    1.045461] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.045463] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.045595] Using IPI No-Shortcut mode
[    1.045683] PM: Hibernation image not present or could not be loaded.
[    1.045692] registered taskstats version 1
[    1.045864]   Magic number: 3:381:56
[    1.045868] input mice: hash matches
[    1.045964] rtc_cmos 00:05: setting system clock to 2011-07-22 02:05:09 UTC (1311300309)
[    1.045966] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.045968] EDD information not available.
[    1.046042] Freeing unused kernel memory: 700k freed
[    1.046254] Write protecting the kernel text: 5192k
[    1.046288] Write protecting the kernel read-only data: 2148k
[    1.066009] <30>udev[66]: starting version 167
[    1.126659] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.137688] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    1.137710] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    1.137716] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.145721] hub 1-2:1.0: USB hub found
[    1.146070] hub 1-2:1.0: 4 ports detected
[    1.154391] Floppy drive(s): fd0 is 1.44M
[    1.172054] FDC 0 is a post-1991 82077
[    1.260049] Refined TSC clocksource calibration: 2712.499 MHz.
[    1.260063] Switching to clocksource tsc
[    1.416339] usb 1-2.1: new high speed USB device using ehci_hcd and address 3
[    1.660878] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:30:67:24:ae:45
[    1.660882] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.660913] pata_amd 0000:00:06.0: version 0.4.1
[    1.660954] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.661271] scsi0 : pata_amd
[    1.661402] scsi1 : pata_amd
[    1.661740] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.661743] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.661779] sata_nv 0000:00:08.0: version 3.5
[    1.661794] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.661833] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.662132] scsi2 : sata_nv
[    1.662245] scsi3 : sata_nv
[    1.662339] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.662342] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    1.764334] usb 1-2.2: new low speed USB device using ehci_hcd and address 4
[    1.824324] ata1.00: ATAPI: LITE-ON DVD+RW LDW-401S, ES0E, max UDMA/33
[    1.824331] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    1.840273] ata1.00: configured for UDMA/33
[    1.841166] scsi 0:0:0:0: CD-ROM            LITE-ON  DVD+RW LDW-401S  ES0E PQ: 0 ANSI: 5
[    1.843025] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.843030] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.843186] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.843253] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.843391] ata2: port disabled. ignoring.
[    1.916145] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[    1.916247] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.1-2.2/input0
[    1.927117] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.1/input/input3
[    1.927212] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.1-2.2/input1
[    1.927229] usbcore: registered new interface driver usbhid
[    1.927230] usbhid: USB HID core driver
[    1.948337] usb 1-2.3: new low speed USB device using ehci_hcd and address 5
[    2.048521] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4
[    2.048624] generic-usb 0003:046D:C408.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:02.1-2.3/input0
[    2.128073] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.137196] ata3.00: ATA-8: WDC WD3200AAJS-22L7A0, 01.03E01, max UDMA/133
[    2.137200] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.153201] ata3.00: configured for UDMA/133
[    2.153355] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 01.0 PQ: 0 ANSI: 5
[    2.153519] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.153523] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.153560] sd 2:0:0:0: [sda] Write Protect is off
[    2.153563] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.153578] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.184566]  sda: sda1 sda2 < sda5 >
[    2.184843] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.474302] ata4: SATA link down (SStatus 0 SControl 300)
[    2.895920] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.189996] <30>udev[392]: starting version 167
[   11.293857] type=1400 audit(1311300319.743:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=495 comm="apparmor_parser"
[   11.294156] type=1400 audit(1311300319.743:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=495 comm="apparmor_parser"
[   11.294348] type=1400 audit(1311300319.743:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=495 comm="apparmor_parser"
[   11.553199] parport_pc 00:09: reported by Plug and Play ACPI
[   11.553244] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.654584] lp0: using parport0 (interrupt-driven).
[   11.672822] ppdev: user-space parallel port driver
[   11.675897] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   11.675950] i2c i2c-1: nForce2 SMBus adapter at 0xf400
[   11.870254] Disabling lock debugging due to kernel taint
[   11.874551] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   11.968340] usb 1-2.1: reset high speed USB device using ehci_hcd and address 3
[   12.540365] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   12.540383] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[   12.540390] nvidia 0000:02:00.0: setting latency timer to 64
[   12.540394] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.540641] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   12.557869] ndiswrapper: driver rt2500usb (Linksys,10/17/2005, 2.01.00.0000) loaded
[   12.620710] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   12.620716] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.620719] hda_intel: Disable MSI for Nvidia chipset
[   12.620743] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.168505] wlan0: ethernet device 00:12:17:8f:be:4e using NDIS driver: rt2500usb, version: 0x20000, NDIS version: 0x500, vendor: 'Linksys Wireless-G USB Network A', 13B1:000D.F.conf
[   13.168867] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.169627] usbcore: registered new interface driver ndiswrapper
[   13.516420] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   13.516426] HDA Intel 0000:02:00.1: PCI INT B -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   13.516429] hda_intel: Disable MSI for Nvidia chipset
[   13.516467] HDA Intel 0000:02:00.1: setting latency timer to 64
[   15.347946] vesafb: framebuffer at 0xef000000, mapped to 0xf8780000, using 1216k, total 1216k
[   15.347950] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   15.347952] vesafb: scrolling: redraw
[   15.347955] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.348105] Console: switching to colour frame buffer device 80x30
[   15.351879] fb0: VESA VGA frame buffer device
[   16.054565] Intel AES-NI instructions are not detected.
[   16.099914] padlock_aes: VIA PadLock not detected.
[   16.259126] padlock_sha: VIA PadLock Hash Engine not detected.
[   17.840226] Adding 2094076k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2094076k 
[   26.991896] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   27.045783] type=1400 audit(1311300335.495:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=950 comm="apparmor_parser"
[   27.046095] type=1400 audit(1311300335.495:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=950 comm="apparmor_parser"
[   27.046132] type=1400 audit(1311300335.495:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=949 comm="apparmor_parser"
[   27.046292] type=1400 audit(1311300335.495:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=950 comm="apparmor_parser"
[   27.060652] type=1400 audit(1311300335.511:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=966 comm="apparmor_parser"
[   27.062850] type=1400 audit(1311300335.511:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=957 comm="apparmor_parser"
[   27.063244] type=1400 audit(1311300335.511:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=966 comm="apparmor_parser"
[   27.064514] type=1400 audit(1311300335.515:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=953 comm="apparmor_parser"
[   27.068567] type=1400 audit(1311300335.519:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=957 comm="apparmor_parser"
[   27.069721] type=1400 audit(1311300335.519:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=953 comm="apparmor_parser"

```

---

### Post by wildmanne39 on 2011-07-21
> **FruG3rT said:**
> Alright, heres my logs:
```
Xorg0 log:
[    27.239] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    27.239] X Protocol Version 11, Revision 0
[    27.239] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    27.239] Current Operating System: Linux Blubber 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    27.239] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=d7cd7dda-6470-4214-8b1a-b6b100be7a6e ro quiet splash vt.handoff=7
[    27.239] Build Date: 21 May 2011  11:38:35AM
[    27.239] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    27.239] Current version of pixman: 0.20.2
[    27.239]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.239] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.239] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 21 19:05:35 2011
[    27.240] (==) Using config file: "/etc/X11/xorg.conf"
[    27.240] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.240] (==) ServerLayout "Layout0"
[    27.240] (**) |-->Screen "Screen0" (0)
[    27.240] (**) |   |-->Monitor "Monitor0"
[    27.240] (**) |   |-->Device "Device0"
[    27.240] (**) |-->Input Device "Keyboard0"
[    27.240] (**) |-->Input Device "Mouse0"
[    27.240] (==) Automatically adding devices
[    27.240] (==) Automatically enabling devices
[    27.240] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.240]     Entry deleted from font path.
[    27.240] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    27.240] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.240] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    27.240] (WW) Disabling Keyboard0
[    27.240] (WW) Disabling Mouse0
[    27.240] (II) Loader magic: 0x81ffde0
[    27.240] (II) Module ABI versions:
[    27.240]     X.Org ANSI C Emulation: 0.4
[    27.240]     X.Org Video Driver: 10.0
[    27.240]     X.Org XInput driver : 12.3
[    27.240]     X.Org Server Extension : 5.0
[    27.241] (--) PCI:*(0:2:0:0) 10de:0ca3:3842:1236 rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xee000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
[    27.241] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.241] (II) LoadModule: "extmod"
[    27.241] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.241] (II) Module extmod: vendor="X.Org Foundation"
[    27.241]     compiled for 1.10.1, module version = 1.0.0
[    27.241]     Module class: X.Org Server Extension
[    27.241]     ABI class: X.Org Server Extension, version 5.0
[    27.242] (II) Loading extension MIT-SCREEN-SAVER
[    27.242] (II) Loading extension XFree86-VidModeExtension
[    27.242] (II) Loading extension XFree86-DGA
[    27.242] (II) Loading extension DPMS
[    27.242] (II) Loading extension XVideo
[    27.242] (II) Loading extension XVideo-MotionCompensation
[    27.242] (II) Loading extension X-Resource
[    27.242] (II) LoadModule: "dbe"
[    27.242] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.242] (II) Module dbe: vendor="X.Org Foundation"
[    27.242]     compiled for 1.10.1, module version = 1.0.0
[    27.242]     Module class: X.Org Server Extension
[    27.242]     ABI class: X.Org Server Extension, version 5.0
[    27.242] (II) Loading extension DOUBLE-BUFFER
[    27.242] (II) LoadModule: "glx"
[    27.242] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    27.260] (II) Module glx: vendor="NVIDIA Corporation"
[    27.261]     compiled for 4.0.2, module version = 1.0.0
[    27.261]     Module class: X.Org Server Extension
[    27.261] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    27.261] (II) Loading extension GLX
[    27.261] (II) LoadModule: "record"
[    27.261] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    27.261] (II) Module record: vendor="X.Org Foundation"
[    27.261]     compiled for 1.10.1, module version = 1.13.0
[    27.261]     Module class: X.Org Server Extension
[    27.261]     ABI class: X.Org Server Extension, version 5.0
[    27.261] (II) Loading extension RECORD
[    27.261] (II) LoadModule: "dri"
[    27.261] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.261] (II) Module dri: vendor="X.Org Foundation"
[    27.261]     compiled for 1.10.1, module version = 1.0.0
[    27.261]     ABI class: X.Org Server Extension, version 5.0
[    27.261] (II) Loading extension XFree86-DRI
[    27.261] (II) LoadModule: "dri2"
[    27.261] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.261] (II) Module dri2: vendor="X.Org Foundation"
[    27.261]     compiled for 1.10.1, module version = 1.2.0
[    27.261]     ABI class: X.Org Server Extension, version 5.0
[    27.261] (II) Loading extension DRI2
[    27.261] (II) LoadModule: "nvidia"
[    27.261] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    27.262] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.262]     compiled for 4.0.2, module version = 1.0.0
[    27.262]     Module class: X.Org Video Driver
[    27.262] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    27.262] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    27.262] (++) using VT number 7

[    27.262] (II) Loading sub module "fb"
[    27.262] (II) LoadModule: "fb"
[    27.262] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.262] (II) Module fb: vendor="X.Org Foundation"
[    27.262]     compiled for 1.10.1, module version = 1.0.0
[    27.262]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.262] (II) Loading sub module "wfb"
[    27.262] (II) LoadModule: "wfb"
[    27.263] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.263] (II) Module wfb: vendor="X.Org Foundation"
[    27.263]     compiled for 1.10.1, module version = 1.0.0
[    27.263]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.263] (II) Loading sub module "ramdac"
[    27.263] (II) LoadModule: "ramdac"
[    27.263] (II) Module "ramdac" already built-in
[    27.263] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    27.263] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.263] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.263] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    27.263] (==) NVIDIA(0): RGB weight 888
[    27.263] (==) NVIDIA(0): Default visual is TrueColor
[    27.263] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.813] (II) NVIDIA(GPU-0): Display (Acer V173 (CRT-1)) does not support NVIDIA 3D Vision
[    27.813] (II) NVIDIA(GPU-0):     stereo.
[    27.814] (II) NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:2:0:0 (GPU-0)
[    27.814] (--) NVIDIA(0): Memory: 1048576 kBytes
[    27.814] (--) NVIDIA(0): VideoBIOS: 70.15.20.00.32
[    27.814] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    27.814] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    27.814] (--) NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:2:0:0
[    27.814] (--) NVIDIA(0):     Acer V173 (CRT-1)
[    27.814] (--) NVIDIA(0): Acer V173 (CRT-1): 400.0 MHz maximum pixel clock
[    27.842] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    27.842] (==) NVIDIA(0): 
[    27.842] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    27.842] (==) NVIDIA(0):     will be used as the requested mode.
[    27.843] (==) NVIDIA(0): 
[    27.843] (II) NVIDIA(0): Validated modes:
[    27.843] (II) NVIDIA(0):     "nvidia-auto-select"
[    27.843] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    27.872] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[    27.877] (--) NVIDIA(0):     option
[    27.878] (--) Depth 24 pixmap format is 32 bpp
[    27.878] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    27.881] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    28.077] (II) Loading extension NV-GLX
[    28.096] (==) NVIDIA(0): Disabling shared memory pixmaps
[    28.096] (==) NVIDIA(0): Backing store disabled
[    28.096] (==) NVIDIA(0): Silken mouse enabled
[    28.097] (**) NVIDIA(0): DPMS enabled
[    28.097] (II) Loading extension NV-CONTROL
[    28.097] (II) Loading extension XINERAMA
[    28.097] (II) Loading sub module "dri2"
[    28.097] (II) LoadModule: "dri2"
[    28.097] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.097] (II) Module dri2: vendor="X.Org Foundation"
[    28.097]     compiled for 1.10.1, module version = 1.2.0
[    28.097]     ABI class: X.Org Server Extension, version 5.0
[    28.097] (II) NVIDIA(0): [DRI2] Setup complete
[    28.097] (==) RandR enabled
[    28.097] (II) Initializing built-in extension Generic Event Extension
[    28.097] (II) Initializing built-in extension SHAPE
[    28.097] (II) Initializing built-in extension MIT-SHM
[    28.097] (II) Initializing built-in extension XInputExtension
[    28.097] (II) Initializing built-in extension XTEST
[    28.097] (II) Initializing built-in extension BIG-REQUESTS
[    28.097] (II) Initializing built-in extension SYNC
[    28.097] (II) Initializing built-in extension XKEYBOARD
[    28.097] (II) Initializing built-in extension XC-MISC
[    28.097] (II) Initializing built-in extension SECURITY
[    28.097] (II) Initializing built-in extension XINERAMA
[    28.097] (II) Initializing built-in extension XFIXES
[    28.097] (II) Initializing built-in extension RENDER
[    28.097] (II) Initializing built-in extension RANDR
[    28.097] (II) Initializing built-in extension COMPOSITE
[    28.097] (II) Initializing built-in extension DAMAGE
[    28.097] (II) Initializing built-in extension GESTURE
[    28.100] (II) Initializing extension GLX
[    28.119] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.126] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.126] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.126] (II) LoadModule: "evdev"
[    28.126] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.126] (II) Module evdev: vendor="X.Org Foundation"
[    28.126]     compiled for 1.10.0.902, module version = 2.6.0
[    28.127]     Module class: X.Org XInput Driver
[    28.127]     ABI class: X.Org XInput driver, version 12.3
[    28.127] (II) Using input driver 'evdev' for 'Power Button'
[    28.127] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.127] (**) Power Button: always reports core events
[    28.127] (**) Power Button: Device: "/dev/input/event1"
[    28.127] (--) Power Button: Found keys
[    28.127] (II) Power Button: Configuring as keyboard
[    28.127] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    28.127] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.127] (**) Option "xkb_rules" "evdev"
[    28.127] (**) Option "xkb_model" "pc105"
[    28.127] (**) Option "xkb_layout" "us"
[    28.130] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    28.130] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.130] (II) Using input driver 'evdev' for 'Power Button'
[    28.130] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.130] (**) Power Button: always reports core events
[    28.130] (**) Power Button: Device: "/dev/input/event0"
[    28.130] (--) Power Button: Found keys
[    28.130] (II) Power Button: Configuring as keyboard
[    28.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    28.130] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.130] (**) Option "xkb_rules" "evdev"
[    28.130] (**) Option "xkb_model" "pc105"
[    28.130] (**) Option "xkb_layout" "us"
[    28.132] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event2)
[    28.132] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    28.132] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    28.132] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.132] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    28.132] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event2"
[    28.132] (--) Microsoft Comfort Curve Keyboard 2000: Found keys
[    28.132] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    28.132] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input2/event2"
[    28.132] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[    28.132] (**) Option "xkb_rules" "evdev"
[    28.132] (**) Option "xkb_model" "pc105"
[    28.132] (**) Option "xkb_layout" "us"
[    28.133] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    28.133] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    28.133] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found relative axes
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[    28.133] (II) evdev-grail: failed to open grail, no gesture support
[    28.133] (--) Microsoft Comfort Curve Keyboard 2000: Found keys
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.133] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.1/input/input3/event3"
[    28.133] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[    28.133] (**) Option "xkb_rules" "evdev"
[    28.133] (**) Option "xkb_model" "pc105"
[    28.133] (**) Option "xkb_layout" "us"
[    28.133] (EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
[    28.133] (II) Microsoft Comfort Curve Keyboard 2000: initialized for absolute axes.
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[    28.133] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[    28.134] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event4)
[    28.134] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    28.134] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[    28.134] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.134] (**) Logitech USB Trackball: always reports core events
[    28.134] (**) Logitech USB Trackball: Device: "/dev/input/event4"
[    28.148] (--) Logitech USB Trackball: Found 9 mouse buttons
[    28.148] (--) Logitech USB Trackball: Found relative axes
[    28.148] (--) Logitech USB Trackball: Found x and y relative axes
[    28.148] (II) Logitech USB Trackball: Configuring as mouse
[    28.148] (**) Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    28.148] (**) Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.148] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4/event4"
[    28.148] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE)
[    28.148] (II) Logitech USB Trackball: initialized for relative axes.
[    28.148] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    28.148] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    28.148] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    28.148] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    28.148] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    28.148] (II) No input driver/identifier specified (ignoring)


Dmesg log:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.5 present.
[    0.000000] DMI: BIOSTAR Group N61PC-M2S/N61PC-M2S, BIOS 6.00 PG 07/31/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f3a00] f3a00
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35d2a000 - 36e8d000
[    0.000000] ACPI: RSDP 000f7e30 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 7fee3000 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 7fee3080 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110112/tbfadt-557)
[    0.000000] ACPI: DSDT 7fee3100 058B6 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 7fee0000 00040
[    0.000000] ACPI: SSDT 7fee8a80 008F5 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 7fee9380 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: MCFG 7fee93c0 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 7fee89c0 00098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c1784140, node_mem_map f4d2a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294356 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=d7cd7dda-6470-4214-8b1a-b6b100be7a6e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
[    0.000000] Memory: 2040704k/2096000k available (5190k kernel code, 54844k reserved, 2539k data, 700k init, 1186696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511841 - 0xc178c4c0   (2539 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511841   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2712.498 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5424.99 BogoMIPS (lpj=10849992)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004050] Yama: becoming mindful.
[    0.004107] Mount-cache hash table entries: 512
[    0.004223] Initializing cgroup subsys ns
[    0.004226] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004230] Initializing cgroup subsys cpuacct
[    0.004235] Initializing cgroup subsys memory
[    0.004242] Initializing cgroup subsys devices
[    0.004245] Initializing cgroup subsys freezer
[    0.004247] Initializing cgroup subsys net_cls
[    0.004250] Initializing cgroup subsys blkio
[    0.004278] CPU: Physical Processor ID: 0
[    0.004280] CPU: Processor Core ID: 0
[    0.004283] mce: CPU supports 6 MCE banks
[    0.004292] using C1E aware idle routine
[    0.006357] ACPI: Core revision 20110112
[    0.012013] ftrace: allocating 23648 entries in 47 pages
[    0.016062] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059038] CPU0: AMD Athlon(tm) II X2 215 Processor stepping 02
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] CPU 1 irqstacks, hard=f3cb2000 soft=f3cb4000
[    0.060003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.148017] Brought up 2 CPUs
[    0.148020] Total of 2 processors activated (10849.98 BogoMIPS).
[    0.148413] devtmpfs: initialized
[    0.148963] print_constraints: dummy: 
[    0.148995] Time:  2:05:08  Date: 07/22/11
[    0.149025] NET: Registered protocol family 16
[    0.149120] EISA bus registered
[    0.149124] node 0 link 0: io port [9000, ffff]
[    0.149073] Trying to unpack rootfs image as initramfs...
[    0.149130] TOM: 0000000080000000 aka 2048M
[    0.149132] Fam 10h mmconf [f0000000, f00fffff]
[    0.149134] node 0 link 0: mmio [a0000, bffff]
[    0.149137] node 0 link 0: mmio [80000000, efffffff]
[    0.149140] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.149142] node 0 link 0: mmio [f0000000, f03fffff] ==> [f0100000, f03fffff]
[    0.149146] bus: [00, 04] on node 0 link 0
[    0.149148] bus: 00 index 0 [io  0x0000-0xffff]
[    0.149150] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.149152] bus: 00 index 2 [mem 0x80000000-0xefffffff]
[    0.149153] bus: 00 index 3 [mem 0xf0400000-0xffffffff]
[    0.149155] bus: 00 index 4 [mem 0xf0100000-0xf03fffff]
[    0.149162] Extended Config Space enabled on 1 nodes
[    0.149170] ACPI: bus type pci registered
[    0.149228] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.149231] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.149232] PCI: Using MMCONFIG for extended config space
[    0.149234] PCI: Using configuration type 1 for base access
[    0.164115] bio: create slab <bio-0> at 0
[    0.165136] ACPI: EC: Look up EC in DSDT
[    0.168023] ACPI: Interpreter enabled
[    0.168027] ACPI: (supports S0 S1 S4 S5)
[    0.168041] ACPI: Using IOAPIC for interrupt routing
[    0.172066] ACPI: No dock devices found.
[    0.172068] HEST: Table not found.
[    0.172071] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.172632] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
[    0.173608] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
[    0.173611] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
[    0.173613] pci_root PNP0A08:00: host bridge window [io  0x9000-0xffff]
[    0.173615] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df]
[    0.173617] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80]
[    0.173619] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff]
[    0.173621] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.173623] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xefffffff]
[    0.173625] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff]
[    0.173650] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
[    0.173800] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
[    0.173813] pci 0000:00:01.0: reg 18: [io  0x1d00-0x1dff]
[    0.173839] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
[    0.173850] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
[    0.173865] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
[    0.173870] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
[    0.173889] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.173895] pci 0000:00:01.1: PME# disabled
[    0.173905] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
[    0.173943] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
[    0.173952] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
[    0.173980] pci 0000:00:02.0: supports D1 D2
[    0.173982] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.173985] pci 0000:00:02.0: PME# disabled
[    0.173995] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
[    0.174005] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
[    0.174038] pci 0000:00:02.1: supports D1 D2
[    0.174040] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174043] pci 0000:00:02.1: PME# disabled
[    0.174059] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
[    0.174092] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
[    0.174103] pci 0000:00:05.0: reg 10: [mem 0xfe028000-0xfe02bfff]
[    0.174136] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.174138] pci 0000:00:05.0: PME# disabled
[    0.174155] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
[    0.174176] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
[    0.174201] pci 0000:00:07.0: [10de:03ef] type 0 class 0x000680
[    0.174210] pci 0000:00:07.0: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.174214] pci 0000:00:07.0: reg 14: [io  0xec00-0xec07]
[    0.174240] pci 0000:00:07.0: supports D1 D2
[    0.174241] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174245] pci 0000:00:07.0: PME# disabled
[    0.174256] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
[    0.174264] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
[    0.174268] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.174273] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
[    0.174277] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
[    0.174281] pci 0000:00:08.0: reg 20: [io  0xd800-0xd80f]
[    0.174285] pci 0000:00:08.0: reg 24: [mem 0xfe02c000-0xfe02cfff]
[    0.174312] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
[    0.174333] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174335] pci 0000:00:09.0: PME# disabled
[    0.174348] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
[    0.174367] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174370] pci 0000:00:0b.0: PME# disabled
[    0.174383] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
[    0.174402] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174404] pci 0000:00:0c.0: PME# disabled
[    0.174422] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.174437] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.174450] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.174462] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.174477] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.174534] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.174537] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.174540] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.174543] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.174545] pci 0000:00:04.0:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.174548] pci 0000:00:04.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.174550] pci 0000:00:04.0:   bridge window [io  0x9000-0xffff] (subtractive decode)
[    0.174552] pci 0000:00:04.0:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.174554] pci 0000:00:04.0:   bridge window [io  0x1c00-0x1c80] (subtractive decode)
[    0.174556] pci 0000:00:04.0:   bridge window [mem 0xfec80000-0xfecbffff] (subtractive decode)
[    0.174559] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.174561] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xefffffff] (subtractive decode)
[    0.174563] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xfe02ffff] (subtractive decode)
[    0.174591] pci 0000:02:00.0: [10de:0ca3] type 0 class 0x000300
[    0.174599] pci 0000:02:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.174608] pci 0000:02:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.174616] pci 0000:02:00.0: reg 1c: [mem 0xee000000-0xefffffff 64bit pref]
[    0.174622] pci 0000:02:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.174628] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.174661] pci 0000:02:00.1: [10de:0be4] type 0 class 0x000403
[    0.174669] pci 0000:02:00.1: reg 10: [mem 0xfcffc000-0xfcffffff]
[    0.180040] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.180045] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.180048] pci 0000:00:09.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.180052] pci 0000:00:09.0:   bridge window [mem 0xd0000000-0xefffffff 64bit pref]
[    0.180077] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.180080] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.180083] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.180086] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.180106] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.180109] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.180111] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.180114] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.180123] pci_bus 0000:00: on NUMA node 0
[    0.180129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.180383]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.193411] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193443] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193474] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193504] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193535] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
[    0.193565] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193597] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193629] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[    0.193659] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193689] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193720] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.193750] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.193781] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.193811] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193842] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.193880] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.193915] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.193946] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.193980] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.194037] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.194091] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.194141] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.194191] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.194241] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.194291] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.194341] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.194390] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[    0.194440] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0, disabled.
[    0.194491] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.194541] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.194592] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
[    0.194643] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[    0.194693] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[    0.194743] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.194794] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.194845] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.194896] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[    0.194946] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0, disabled.
[    0.195032] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.195035] vgaarb: loaded
[    0.195182] SCSI subsystem initialized
[    0.195235] libata version 3.00 loaded.
[    0.195271] usbcore: registered new interface driver usbfs
[    0.195280] usbcore: registered new interface driver hub
[    0.195300] usbcore: registered new device driver usb
[    0.195376] wmi: Mapper loaded
[    0.195378] PCI: Using ACPI for IRQ routing
[    0.195381] PCI: pci_cache_line_size set to 64 bytes
[    0.195393] pci 0000:00:01.0: no compatible bridge window for [io  0x1d00-0x1dff]
[    0.195433] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.195435] reserve RAM buffer: 000000007fee0000 - 000000007fffffff 
[    0.195513] NetLabel: Initializing
[    0.195514] NetLabel:  domain hash size = 128
[    0.195515] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195524] NetLabel:  unlabeled traffic allowed by default
[    0.195550] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.195555] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.195559] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.200081] Switching to clocksource hpet
[    0.203711] Switched to NOHz mode on CPU #0
[    0.203811] Switched to NOHz mode on CPU #1
[    0.205172] AppArmor: AppArmor Filesystem Enabled
[    0.205201] pnp: PnP ACPI init
[    0.205217] ACPI: bus type pnp registered
[    0.205753] pnp 00:00: [bus 00-04]
[    0.205755] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.205758] pnp 00:00: [io  0x0000-0x03af window]
[    0.205761] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.205763] pnp 00:00: [io  0x9000-0xffff window]
[    0.205765] pnp 00:00: [io  0x03b0-0x03df window]
[    0.205767] pnp 00:00: [io  0x1c00-0x1c80 window]
[    0.205769] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
[    0.205771] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.205773] pnp 00:00: [mem 0x80000000-0xefffffff window]
[    0.205774] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
[    0.205776] pnp 00:00: [mem 0x00000000 window]
[    0.205834] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.205880] pnp 00:01: [io  0x1000-0x107f]
[    0.205881] pnp 00:01: [io  0x1080-0x10ff]
[    0.205883] pnp 00:01: [io  0x1400-0x147f]
[    0.205885] pnp 00:01: [io  0x1480-0x14ff]
[    0.205886] pnp 00:01: [io  0x1800-0x187f]
[    0.205888] pnp 00:01: [io  0x1880-0x18ff]
[    0.205890] pnp 00:01: [mem 0x00000000-0xffffffff disabled]
[    0.205892] pnp 00:01: [io  0x2000-0x207f]
[    0.205893] pnp 00:01: [io  0x2080-0x20ff]
[    0.205939] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.205942] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.205944] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.205947] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.205949] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.205951] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.205953] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.205955] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.205958] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.205994] pnp 00:02: [io  0x0010-0x001f]
[    0.205996] pnp 00:02: [io  0x0022-0x003f]
[    0.205997] pnp 00:02: [io  0x0044-0x005f]
[    0.205999] pnp 00:02: [io  0x0062-0x0063]
[    0.206001] pnp 00:02: [io  0x0065-0x006f]
[    0.206002] pnp 00:02: [io  0x0074-0x007f]
[    0.206004] pnp 00:02: [io  0x0091-0x0093]
[    0.206005] pnp 00:02: [io  0x00a2-0x00bf]
[    0.206007] pnp 00:02: [io  0x00e0-0x00ef]
[    0.206009] pnp 00:02: [io  0x04d0-0x04d1]
[    0.206010] pnp 00:02: [io  0x0800-0x087f]
[    0.206012] pnp 00:02: [io  0x0290-0x029f]
[    0.206013] pnp 00:02: [io  0x0290-0x0297]
[    0.206018] pnp 00:02: disabling [io  0x0010-0x001f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206021] pnp 00:02: disabling [io  0x0022-0x003f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206023] pnp 00:02: disabling [io  0x0044-0x005f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206026] pnp 00:02: disabling [io  0x0062-0x0063] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206029] pnp 00:02: disabling [io  0x0065-0x006f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206032] pnp 00:02: disabling [io  0x0074-0x007f] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206035] pnp 00:02: disabling [io  0x0091-0x0093] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206037] pnp 00:02: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206040] pnp 00:02: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:01.0 BAR 2 [io  0x0000-0x00ff]
[    0.206079] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.206081] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.206084] system 00:02: [io  0x0290-0x029f] has been reserved
[    0.206086] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.206089] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.206098] pnp 00:03: [dma 4]
[    0.206099] pnp 00:03: [io  0x0000-0x000f]
[    0.206101] pnp 00:03: [io  0x0080-0x0090]
[    0.206102] pnp 00:03: [io  0x0094-0x009f]
[    0.206104] pnp 00:03: [io  0x00c0-0x00df]
[    0.206128] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.206164] pnp 00:04: [irq 0 disabled]
[    0.206177] pnp 00:04: [irq 8]
[    0.206179] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
[    0.206202] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.206221] pnp 00:05: [io  0x0070-0x0073]
[    0.206244] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.206250] pnp 00:06: [io  0x0061]
[    0.206272] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.206278] pnp 00:07: [io  0x00f0-0x00ff]
[    0.206285] pnp 00:07: [irq 13]
[    0.206310] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.206432] pnp 00:08: [io  0x03f0-0x03f5]
[    0.206434] pnp 00:08: [io  0x03f7]
[    0.206441] pnp 00:08: [irq 6]
[    0.206442] pnp 00:08: [dma 2]
[    0.206479] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.206655] pnp 00:09: [io  0x0378-0x037f]
[    0.206662] pnp 00:09: [irq 7]
[    0.206699] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.207158] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
[    0.207202] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.207205] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207259] pnp 00:0b: [mem 0x000f0000-0x000fffff]
[    0.207261] pnp 00:0b: [mem 0xfeff0000-0xfeff00ff]
[    0.207263] pnp 00:0b: [mem 0x7fee0000-0x7fefffff]
[    0.207264] pnp 00:0b: [mem 0xffff0000-0xffffffff]
[    0.207268] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.207270] pnp 00:0b: [mem 0x00100000-0x7fedffff]
[    0.207272] pnp 00:0b: [mem 0x00000000-0xffffffff disabled]
[    0.207274] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.207275] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.207277] pnp 00:0b: [mem 0xfefff000-0xfeffffff]
[    0.207279] pnp 00:0b: [mem 0xfff80000-0xfff80fff]
[    0.207281] pnp 00:0b: [mem 0xfff90000-0xfffbffff]
[    0.207282] pnp 00:0b: [mem 0xfffed000-0xfffeffff]
[    0.207333] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.207336] system 00:0b: [mem 0xfeff0000-0xfeff00ff] has been reserved
[    0.207338] system 00:0b: [mem 0x7fee0000-0x7fefffff] could not be reserved
[    0.207341] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.207343] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.207345] system 00:0b: [mem 0x00100000-0x7fedffff] could not be reserved
[    0.207348] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.207350] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.207353] system 00:0b: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.207355] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.207357] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.207359] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.207362] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.207370] pnp: PnP ACPI: found 12 devices
[    0.207372] ACPI: ACPI bus type pnp unregistered
[    0.207374] PnPBIOS: Disabled by ACPI PNP
[    0.243202] pci 0000:00:01.0: BAR 2: assigned [io  0xd000-0xd0ff]
[    0.243206] pci 0000:00:01.0: BAR 2: set to [io  0xd000-0xd0ff] (PCI address [0xd000-0xd0ff])
[    0.243209] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.243211] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.243216] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.243219] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.243224] pci 0000:02:00.0: BAR 6: assigned [mem 0xe0000000-0xe007ffff pref]
[    0.243226] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.243228] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.243231] pci 0000:00:09.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.243234] pci 0000:00:09.0:   bridge window [mem 0xd0000000-0xefffffff 64bit pref]
[    0.243237] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.243239] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.243242] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.243244] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.243248] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.243250] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.243252] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.243255] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.243263] pci 0000:00:04.0: setting latency timer to 64
[    0.243267] pci 0000:00:09.0: setting latency timer to 64
[    0.243270] pci 0000:00:0b.0: setting latency timer to 64
[    0.243274] pci 0000:00:0c.0: setting latency timer to 64
[    0.243277] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.243279] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.243281] pci_bus 0000:00: resource 6 [io  0x9000-0xffff]
[    0.243282] pci_bus 0000:00: resource 7 [io  0x03b0-0x03df]
[    0.243284] pci_bus 0000:00: resource 8 [io  0x1c00-0x1c80]
[    0.243287] pci_bus 0000:00: resource 9 [mem 0xfec80000-0xfecbffff]
[    0.243289] pci_bus 0000:00: resource 10 [mem 0x000a0000-0x000bffff]
[    0.243291] pci_bus 0000:00: resource 11 [mem 0x80000000-0xefffffff]
[    0.243293] pci_bus 0000:00: resource 12 [mem 0xf4000000-0xfe02ffff]
[    0.243295] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.243297] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.243299] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
[    0.243301] pci_bus 0000:01: resource 4 [io  0x0000-0x03af]
[    0.243303] pci_bus 0000:01: resource 5 [io  0x03e0-0x0cf7]
[    0.243305] pci_bus 0000:01: resource 6 [io  0x9000-0xffff]
[    0.243307] pci_bus 0000:01: resource 7 [io  0x03b0-0x03df]
[    0.243309] pci_bus 0000:01: resource 8 [io  0x1c00-0x1c80]
[    0.243311] pci_bus 0000:01: resource 9 [mem 0xfec80000-0xfecbffff]
[    0.243313] pci_bus 0000:01: resource 10 [mem 0x000a0000-0x000bffff]
[    0.243315] pci_bus 0000:01: resource 11 [mem 0x80000000-0xefffffff]
[    0.243317] pci_bus 0000:01: resource 12 [mem 0xf4000000-0xfe02ffff]
[    0.243320] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.243322] pci_bus 0000:02: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.243324] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xefffffff 64bit pref]
[    0.243326] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.243328] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.243330] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.243332] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.243334] pci_bus 0000:04: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.243336] pci_bus 0000:04: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.243368] NET: Registered protocol family 2
[    0.243421] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.243601] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.244081] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.244305] TCP: Hash tables configured (established 131072 bind 65536)
[    0.244307] TCP reno registered
[    0.244310] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.244318] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.244401] NET: Registered protocol family 1
[    0.260113] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260162] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260218] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260273] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260332] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260394] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260461] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260476] pci 0000:02:00.0: Boot video device
[    0.260484] PCI: CLS 64 bytes, default 64
[    0.260664] cpufreq-nforce2: No nForce2 chipset.
[    0.260764] audit: initializing netlink socket (disabled)
[    0.260773] type=2000 audit(1311300308.260:1): initialized
[    0.268604] highmem bounce pool size: 64 pages
[    0.268608] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.269869] VFS: Disk quotas dquot_6.5.2
[    0.269912] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.270419] fuse init (API version 7.16)
[    0.270486] msgmni has been set to 1667
[    0.270667] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.270686] io scheduler noop registered
[    0.270688] io scheduler deadline registered
[    0.270701] io scheduler cfq registered (default)
[    0.270788] pcieport 0000:00:09.0: setting latency timer to 64
[    0.270813] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.270847] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.270864] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.270892] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.270908] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.270956] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.270976] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.271087] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.271093] ACPI: Power Button [PWRB]
[    0.271139] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.271142] ACPI: Power Button [PWRF]
[    0.271182] ACPI: Fan [FAN] (on)
[    0.271304] ACPI: acpi_idle registered with cpuidle
[    0.272637] ACPI Warning: For \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference (20110112/nspredef-1059)
[    0.272643] ACPI: Expecting a [Reference] package element, found type 0
[    0.272644] ACPI: Invalid passive threshold
[    0.272752] thermal LNXTHERM:00: registered as thermal_zone0
[    0.272755] ACPI: Thermal Zone [THRM] (40 C)
[    0.272790] ERST: Table is not found!
[    0.272894] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.273181] isapnp: Scanning for PnP cards...
[    0.506831] Freeing initrd memory: 17804k freed
[    0.625983] isapnp: No Plug & Play device found
[    0.688393] Linux agpgart interface v0.103
[    0.689394] brd: module loaded
[    0.689803] loop: module loaded
[    0.689880] i2c-core: driver [adp5520] using legacy suspend method
[    0.689881] i2c-core: driver [adp5520] using legacy resume method
[    0.690007] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.690148] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.690163] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.690174] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.690179] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.690416] Fixed MDIO Bus: probed
[    0.690444] PPP generic driver version 2.4.2
[    0.690474] tun: Universal TUN/TAP device driver, 1.6
[    0.690476] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.690538] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.690636] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.690645] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.690657] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.690659] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.690686] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.690773] ehci_hcd 0000:00:02.1: debug port 1
[    0.690782] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.690805] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.700050] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.700194] hub 1-0:1.0: USB hub found
[    0.700198] hub 1-0:1.0: 8 ports detected
[    0.700264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.700409] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.700425] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.700438] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.700441] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.700476] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.700545] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    0.758166] hub 2-0:1.0: USB hub found
[    0.758171] hub 2-0:1.0: 8 ports detected
[    0.758236] uhci_hcd: USB Universal Host Controller Interface driver
[    0.758307] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.791712] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.791713] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.012052] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.040145] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.040272] mousedev: PS/2 mouse device common for all mice
[    1.040375] rtc_cmos 00:05: RTC can wake from S4
[    1.044153] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.044193] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.044278] device-mapper: uevent: version 1.0.3
[    1.044342] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.044438] device-mapper: multipath: version 1.2.0 loaded
[    1.044442] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.044539] EISA: Probing bus 0 at eisa.0
[    1.044541] EISA: Cannot allocate resource for mainboard
[    1.044543] Cannot allocate resource for EISA slot 1
[    1.044544] Cannot allocate resource for EISA slot 2
[    1.044557] EISA: Detected 0 cards.
[    1.044632] cpuidle: using governor ladder
[    1.044634] cpuidle: using governor menu
[    1.044843] TCP cubic registered
[    1.044940] NET: Registered protocol family 10
[    1.045376] NET: Registered protocol family 17
[    1.045390] Registering the dns_resolver key type
[    1.045421] powernow-k8: Found 1 AMD Athlon(tm) II X2 215 Processor (2 cpu cores) (version 2.20.00)
[    1.045458] powernow-k8:    0 : pstate 0 (2700 MHz)
[    1.045460] powernow-k8:    1 : pstate 1 (2100 MHz)
[    1.045461] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.045463] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.045595] Using IPI No-Shortcut mode
[    1.045683] PM: Hibernation image not present or could not be loaded.
[    1.045692] registered taskstats version 1
[    1.045864]   Magic number: 3:381:56
[    1.045868] input mice: hash matches
[    1.045964] rtc_cmos 00:05: setting system clock to 2011-07-22 02:05:09 UTC (1311300309)
[    1.045966] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.045968] EDD information not available.
[    1.046042] Freeing unused kernel memory: 700k freed
[    1.046254] Write protecting the kernel text: 5192k
[    1.046288] Write protecting the kernel read-only data: 2148k
[    1.066009] <30>udev[66]: starting version 167
[    1.126659] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.137688] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    1.137710] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    1.137716] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.145721] hub 1-2:1.0: USB hub found
[    1.146070] hub 1-2:1.0: 4 ports detected
[    1.154391] Floppy drive(s): fd0 is 1.44M
[    1.172054] FDC 0 is a post-1991 82077
[    1.260049] Refined TSC clocksource calibration: 2712.499 MHz.
[    1.260063] Switching to clocksource tsc
[    1.416339] usb 1-2.1: new high speed USB device using ehci_hcd and address 3
[    1.660878] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:30:67:24:ae:45
[    1.660882] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.660913] pata_amd 0000:00:06.0: version 0.4.1
[    1.660954] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.661271] scsi0 : pata_amd
[    1.661402] scsi1 : pata_amd
[    1.661740] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.661743] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.661779] sata_nv 0000:00:08.0: version 3.5
[    1.661794] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.661833] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.662132] scsi2 : sata_nv
[    1.662245] scsi3 : sata_nv
[    1.662339] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.662342] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    1.764334] usb 1-2.2: new low speed USB device using ehci_hcd and address 4
[    1.824324] ata1.00: ATAPI: LITE-ON DVD+RW LDW-401S, ES0E, max UDMA/33
[    1.824331] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    1.840273] ata1.00: configured for UDMA/33
[    1.841166] scsi 0:0:0:0: CD-ROM            LITE-ON  DVD+RW LDW-401S  ES0E PQ: 0 ANSI: 5
[    1.843025] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.843030] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.843186] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.843253] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.843391] ata2: port disabled. ignoring.
[    1.916145] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[    1.916247] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.1-2.2/input0
[    1.927117] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2:1.1/input/input3
[    1.927212] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.1-2.2/input1
[    1.927229] usbcore: registered new interface driver usbhid
[    1.927230] usbhid: USB HID core driver
[    1.948337] usb 1-2.3: new low speed USB device using ehci_hcd and address 5
[    2.048521] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4
[    2.048624] generic-usb 0003:046D:C408.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:02.1-2.3/input0
[    2.128073] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.137196] ata3.00: ATA-8: WDC WD3200AAJS-22L7A0, 01.03E01, max UDMA/133
[    2.137200] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.153201] ata3.00: configured for UDMA/133
[    2.153355] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 01.0 PQ: 0 ANSI: 5
[    2.153519] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.153523] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.153560] sd 2:0:0:0: [sda] Write Protect is off
[    2.153563] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.153578] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.184566]  sda: sda1 sda2 < sda5 >
[    2.184843] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.474302] ata4: SATA link down (SStatus 0 SControl 300)
[    2.895920] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.189996] <30>udev[392]: starting version 167
[   11.293857] type=1400 audit(1311300319.743:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=495 comm="apparmor_parser"
[   11.294156] type=1400 audit(1311300319.743:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=495 comm="apparmor_parser"
[   11.294348] type=1400 audit(1311300319.743:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=495 comm="apparmor_parser"
[   11.553199] parport_pc 00:09: reported by Plug and Play ACPI
[   11.553244] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.654584] lp0: using parport0 (interrupt-driven).
[   11.672822] ppdev: user-space parallel port driver
[   11.675897] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   11.675950] i2c i2c-1: nForce2 SMBus adapter at 0xf400
[   11.870254] Disabling lock debugging due to kernel taint
[   11.874551] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   11.968340] usb 1-2.1: reset high speed USB device using ehci_hcd and address 3
[   12.540365] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   12.540383] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[   12.540390] nvidia 0000:02:00.0: setting latency timer to 64
[   12.540394] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.540641] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   12.557869] ndiswrapper: driver rt2500usb (Linksys,10/17/2005, 2.01.00.0000) loaded
[   12.620710] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   12.620716] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.620719] hda_intel: Disable MSI for Nvidia chipset
[   12.620743] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.168505] wlan0: ethernet device 00:12:17:8f:be:4e using NDIS driver: rt2500usb, version: 0x20000, NDIS version: 0x500, vendor: 'Linksys Wireless-G USB Network A', 13B1:000D.F.conf
[   13.168867] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.169627] usbcore: registered new interface driver ndiswrapper
[   13.516420] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   13.516426] HDA Intel 0000:02:00.1: PCI INT B -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   13.516429] hda_intel: Disable MSI for Nvidia chipset
[   13.516467] HDA Intel 0000:02:00.1: setting latency timer to 64
[   15.347946] vesafb: framebuffer at 0xef000000, mapped to 0xf8780000, using 1216k, total 1216k
[   15.347950] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   15.347952] vesafb: scrolling: redraw
[   15.347955] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.348105] Console: switching to colour frame buffer device 80x30
[   15.351879] fb0: VESA VGA frame buffer device
[   16.054565] Intel AES-NI instructions are not detected.
[   16.099914] padlock_aes: VIA PadLock not detected.
[   16.259126] padlock_sha: VIA PadLock Hash Engine not detected.
[   17.840226] Adding 2094076k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2094076k 
[   26.991896] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   27.045783] type=1400 audit(1311300335.495:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=950 comm="apparmor_parser"
[   27.046095] type=1400 audit(1311300335.495:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=950 comm="apparmor_parser"
[   27.046132] type=1400 audit(1311300335.495:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=949 comm="apparmor_parser"
[   27.046292] type=1400 audit(1311300335.495:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=950 comm="apparmor_parser"
[   27.060652] type=1400 audit(1311300335.511:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=966 comm="apparmor_parser"
[   27.062850] type=1400 audit(1311300335.511:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=957 comm="apparmor_parser"
[   27.063244] type=1400 audit(1311300335.511:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=966 comm="apparmor_parser"
[   27.064514] type=1400 audit(1311300335.515:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=953 comm="apparmor_parser"
[   27.068567] type=1400 audit(1311300335.519:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=957 comm="apparmor_parser"
[   27.069721] type=1400 audit(1311300335.519:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=953 comm="apparmor_parser"

```
Hi, I am just on to post this one message and it is going to be short because I have been up all night with my wife in the hospital and she is home now but has been unable to stand or walk so I will not be back on until tomorrow.

I hope someone else will jump in here and help out tonight or tomorrow before I get back on.

The thing that sticks out in your xorg file is this.
> [    28.133] (EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.

Also when you read your logs make sure the ones you post are as soon as you boot back up after a freeze, not before or two hours later but as soon as you get back into ubuntu.

Also run this command and post the results here please.
```
lsmod
```

I am sorry that I do not have the time to help more tonight, also I am not an expert with these problems, I can only make suggestions based on experience and the logs.

---

