---
title: "Creative Live! Cam IM Pro (VFD0230)"
date: 2011-04-13
forum: General Help
---

### Post by nikio on 2011-04-13
Hello,
I plugged in the usb webcam but nothing happened,
lsusb output is
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4055 Creative Technology, Ltd Live! Cam Video IM Pro
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I suppose that I need a driver and browsing around I found this m5602 driver that should work on sourceforge.
in the downloaded file there was a README with this message

> I) M5602

The developpment for the m5602 have moved to the v4l_dvb repository

[http://linuxtv.org/hg/~eandren/gspca-m5602/](http://linuxtv.org/hg/~eandren/gspca-m5602/)
It is a subdriver in the gspcav2 project.

Everything here about m5602 is obsolete.

Maybe because of my english, surely because of my linux-ignorance, I got there but have no idea of how to get the driver, I suppose I have to add a repository and I don't know how to do.... HELP!

---

### Post by no2498 on 2011-04-13
? how did you try to see the cam what program 

open a terminal type sudo apt-get install cheese click enter
it aks for your pass word you do not see anything you type click enter

cheese webcam booth comes up in sound and video
try the cam in cheese

---

### Post by nikio on 2011-04-13
I forgot to to say that: I've tried to install skype and zoneminder (a video-surveillance software) and none of them found a video device.
Now I've tried cheese, but neither that worked.

---

### Post by no2498 on 2011-04-14
ok try this

open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find the cam

---

### Post by nikio on 2011-04-14
Sadly, in both cases, "cannot identify device '/dev/video0' "

---

### Post by no2498 on 2011-04-15
open a terminal type dmesg click enter

did it say anything about the cam

---

### Post by nikio on 2011-04-15
In the meantime I've upgraded to 11.04 beta2 hoping that the new kernel would do some difference... failure!

I've tried dmesg,
the output is endless, I've managed to send it into a text file and to search the lines beginning with "input:"
the only one that seems possible is
> [   22.337877] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:00/input/input/input4

I'll post the whole output, most of it is quite cryptic!

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=26ffb1d2-fa65-4fe5-a1f8-fba4d787c2d9 ro quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./K10N78, BIOS P1.90 12/30/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000120000000 aka 4608M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ cff8a000-cff90000
[    0.000000] RAMDISK: 366e0000 - 37368000
[    0.000000] ACPI: RSDP 00000000000fc050 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff90000 00044 (v01 123009 RSDT1419 20091230 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90200 00084 (v01 A M I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff90450 08791 (v01  AS158 AS158183 00000183 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffa0000 00040
[    0.000000] ACPI: APIC 00000000cff90390 00080 (v01 123009 APIC1419 20091230 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90410 0003C (v01 123009 OEMMCFG  20091230 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa0040 00073 (v01 123009 OEMB1419 20091230 MSFT 00000097)
[    0.000000] ACPI: AAFT 00000000cff98bf0 00027 (v01 123009 OEMAAFT  20091230 MSFT 00000097)
[    0.000000] ACPI: INFO 00000000cffa00c0 00124 (v01 123009 AMDINFO  20091230 MSFT 00000097)
[    0.000000] ACPI: NVHD 00000000cffa01f0 00284 (v01 123009  NVHDCP  20091230 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff98c20 0028A (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011c200000-ffff88011f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982815
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x2008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa0000
[    0.000000] PM: Registered nosave memory: 00000000cffa0000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cfc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966681
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=26ffb1d2-fa65-4fe5-a1f8-fba4d787c2d9 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 10000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3717656k/4718592k available (5940k kernel code, 787332k absent, 213604k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2499.791 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.58 BogoMIPS (lpj=24997910)
[    0.010010] pid_max: default: 32768 minimum: 301
[    0.010037] Security Framework initialized
[    0.010054] AppArmor: AppArmor initialized
[    0.010055] Yama: becoming mindful.
[    0.010501] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012847] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013825] Mount-cache hash table entries: 256
[    0.013969] Initializing cgroup subsys ns
[    0.013973] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.013976] Initializing cgroup subsys cpuacct
[    0.013980] Initializing cgroup subsys memory
[    0.013989] Initializing cgroup subsys devices
[    0.013992] Initializing cgroup subsys freezer
[    0.013994] Initializing cgroup subsys net_cls
[    0.013996] Initializing cgroup subsys blkio
[    0.014028] tseg: 0000000000
[    0.014043] CPU: Physical Processor ID: 0
[    0.014044] CPU: Processor Core ID: 0
[    0.014046] mce: CPU supports 5 MCE banks
[    0.014057] using C1E aware idle routine
[    0.015492] ACPI: Core revision 20110112
[    0.023714] ftrace: allocating 24314 entries in 96 pages
[    0.030093] Setting APIC routing to flat
[    0.030566] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.130664] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    0.140000] Performance Events: AMD PMU driver.
[    0.140000] ... version:                0
[    0.140000] ... bit width:              48
[    0.140000] ... generic registers:      4
[    0.140000] ... value mask:             0000ffffffffffff
[    0.140000] ... max period:             00007fffffffffff
[    0.140000] ... fixed-purpose events:   0
[    0.140000] ... event mask:             000000000000000f
[    0.140000] Booting Node   0, Processors  #1
[    0.290077] Brought up 2 CPUs
[    0.290079] Total of 2 processors activated (9999.64 BogoMIPS).
[    0.290323] devtmpfs: initialized
[    0.290968] print_constraints: dummy: 
[    0.291027] Time: 14:56:19  Date: 04/15/11
[    0.291068] NET: Registered protocol family 16
[    0.291109] Trying to unpack rootfs image as initramfs...
[    0.291195] node 0 link 0: io port [1000, ffffff]
[    0.291199] TOM: 00000000e0000000 aka 3584M
[    0.291201] node 0 link 0: mmio [e0000000, efffffff]
[    0.291204] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.291206] node 0 link 0: mmio [a0000, bffff]
[    0.291209] TOM2: 0000000120000000 aka 4608M
[    0.291211] bus: [00, 07] on node 0 link 0
[    0.291213] bus: 00 index 0 [io  0x0000-0xffff]
[    0.291215] bus: 00 index 1 [mem 0xe0000000-0xffffffff]
[    0.291217] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.291219] bus: 00 index 3 [mem 0x120000000-0xfcffffffff]
[    0.291230] ACPI: bus type pci registered
[    0.291303] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.291307] PCI: not using MMCONFIG
[    0.291308] PCI: Using configuration type 1 for base access
[    0.292075] bio: create slab <bio-0> at 0
[    0.293443] ACPI: EC: Look up EC in DSDT
[    0.295174] ACPI: Executed 1 blocks of module-level executable AML code
[    0.298506] ACPI: Interpreter enabled
[    0.298510] ACPI: (supports S0 S1 S4 S5)
[    0.298528] ACPI: Using IOAPIC for interrupt routing
[    0.298551] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.300196] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.330963] ACPI: No dock devices found.
[    0.330966] HEST: Table not found.
[    0.330971] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.331216] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.331426] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.331429] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.331431] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.331433] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.331436] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.331474] pci 0000:00:00.0: [10de:0754] type 0 class 0x000500
[    0.331697] pci 0000:00:01.0: [10de:075c] type 0 class 0x000601
[    0.331704] pci 0000:00:01.0: reg 10: [io  0x2f00-0x2fff]
[    0.331741] pci 0000:00:01.1: [10de:0752] type 0 class 0x000c05
[    0.331753] pci 0000:00:01.1: reg 10: [io  0x2900-0x293f]
[    0.331769] pci 0000:00:01.1: reg 20: [io  0x2d00-0x2d3f]
[    0.331775] pci 0000:00:01.1: reg 24: [io  0x2e00-0x2e3f]
[    0.331796] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.331802] pci 0000:00:01.1: PME# disabled
[    0.331814] pci 0000:00:01.2: [10de:0751] type 0 class 0x000500
[    0.331862] pci 0000:00:01.3: [10de:0753] type 0 class 0x000b40
[    0.331879] pci 0000:00:01.3: reg 10: [mem 0xfcf80000-0xfcffffff]
[    0.331987] pci 0000:00:01.4: [10de:0568] type 0 class 0x000500
[    0.332060] pci 0000:00:02.0: [10de:077b] type 0 class 0x000c03
[    0.332069] pci 0000:00:02.0: reg 10: [mem 0xfcf7f000-0xfcf7ffff]
[    0.332101] pci 0000:00:02.0: supports D1 D2
[    0.332103] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332106] pci 0000:00:02.0: PME# disabled
[    0.332119] pci 0000:00:02.1: [10de:077c] type 0 class 0x000c03
[    0.332130] pci 0000:00:02.1: reg 10: [mem 0xfcf7ec00-0xfcf7ecff]
[    0.332166] pci 0000:00:02.1: supports D1 D2
[    0.332168] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332171] pci 0000:00:02.1: PME# disabled
[    0.332191] pci 0000:00:04.0: [10de:077d] type 0 class 0x000c03
[    0.332200] pci 0000:00:04.0: reg 10: [mem 0xfcf7d000-0xfcf7dfff]
[    0.332232] pci 0000:00:04.0: supports D1 D2
[    0.332234] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332237] pci 0000:00:04.0: PME# disabled
[    0.332250] pci 0000:00:04.1: [10de:077e] type 0 class 0x000c03
[    0.332260] pci 0000:00:04.1: reg 10: [mem 0xfcf7e800-0xfcf7e8ff]
[    0.332297] pci 0000:00:04.1: supports D1 D2
[    0.332299] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332302] pci 0000:00:04.1: PME# disabled
[    0.332322] pci 0000:00:06.0: [10de:0759] type 0 class 0x000101
[    0.332345] pci 0000:00:06.0: reg 20: [io  0xffa0-0xffaf]
[    0.332374] pci 0000:00:07.0: [10de:0774] type 0 class 0x000403
[    0.332386] pci 0000:00:07.0: reg 10: [mem 0xfcf78000-0xfcf7bfff]
[    0.332422] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.332425] pci 0000:00:07.0: PME# disabled
[    0.332439] pci 0000:00:08.0: [10de:075a] type 1 class 0x000604
[    0.332476] pci 0000:00:09.0: [10de:0ad0] type 0 class 0x000101
[    0.332486] pci 0000:00:09.0: reg 10: [io  0xd480-0xd487]
[    0.332490] pci 0000:00:09.0: reg 14: [io  0xd400-0xd403]
[    0.332495] pci 0000:00:09.0: reg 18: [io  0xd080-0xd087]
[    0.332500] pci 0000:00:09.0: reg 1c: [io  0xd000-0xd003]
[    0.332504] pci 0000:00:09.0: reg 20: [io  0xcc00-0xcc0f]
[    0.332509] pci 0000:00:09.0: reg 24: [mem 0xfcf76000-0xfcf77fff]
[    0.332540] pci 0000:00:0a.0: [10de:0760] type 0 class 0x000200
[    0.332550] pci 0000:00:0a.0: reg 10: [mem 0xfcf7c000-0xfcf7cfff]
[    0.332555] pci 0000:00:0a.0: reg 14: [io  0xc880-0xc887]
[    0.332560] pci 0000:00:0a.0: reg 18: [mem 0xfcf7e400-0xfcf7e4ff]
[    0.332565] pci 0000:00:0a.0: reg 1c: [mem 0xfcf7e000-0xfcf7e00f]
[    0.332589] pci 0000:00:0a.0: supports D1 D2
[    0.332591] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332595] pci 0000:00:0a.0: PME# disabled
[    0.332609] pci 0000:00:0b.0: [10de:0569] type 1 class 0x000604
[    0.332631] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332634] pci 0000:00:0b.0: PME# disabled
[    0.332688] pci 0000:00:10.0: [10de:0778] type 1 class 0x000604
[    0.332856] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332864] pci 0000:00:10.0: PME# disabled
[    0.332949] pci 0000:00:12.0: [10de:075b] type 1 class 0x000604
[    0.333117] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.333125] pci 0000:00:12.0: PME# disabled
[    0.333208] pci 0000:00:13.0: [10de:077a] type 1 class 0x000604
[    0.333376] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.333384] pci 0000:00:13.0: PME# disabled
[    0.333467] pci 0000:00:14.0: [10de:077a] type 1 class 0x000604
[    0.333635] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.333643] pci 0000:00:14.0: PME# disabled
[    0.333689] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.333706] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.333722] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.333737] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.333804] pci 0000:00:08.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.333808] pci 0000:00:08.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.333812] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.333815] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.333818] pci 0000:00:08.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.333821] pci 0000:00:08.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.333823] pci 0000:00:08.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.333826] pci 0000:00:08.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.333829] pci 0000:00:08.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.333852] pci 0000:02:00.0: [10de:0849] type 0 class 0x000300
[    0.333860] pci 0000:02:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.333867] pci 0000:02:00.0: reg 14: [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.333873] pci 0000:02:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.333878] pci 0000:02:00.0: reg 24: [io  0xec00-0xec7f]
[    0.333883] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
[    0.333908] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.333912] pci 0000:00:0b.0:   bridge window [io  0xe000-0xefff]
[    0.333914] pci 0000:00:0b.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.333918] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf9ffffff 64bit pref]
[    0.334069] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.334083] pci 0000:00:10.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.334091] pci 0000:00:10.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.334104] pci 0000:00:10.0:   bridge window [mem 0xfbc00000-0xfbcfffff 64bit pref]
[    0.334257] pci 0000:00:12.0: PCI bridge to [bus 04-04]
[    0.334271] pci 0000:00:12.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.334279] pci 0000:00:12.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.334292] pci 0000:00:12.0:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.334446] pci 0000:00:13.0: PCI bridge to [bus 05-05]
[    0.334459] pci 0000:00:13.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.334467] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.334481] pci 0000:00:13.0:   bridge window [mem 0xfbe00000-0xfbefffff 64bit pref]
[    0.334634] pci 0000:00:14.0: PCI bridge to [bus 06-06]
[    0.334647] pci 0000:00:14.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.334655] pci 0000:00:14.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.334669] pci 0000:00:14.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.334722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.334997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.335098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.335139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.335186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.335230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.335274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.335439]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.346608] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.346728] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.346851] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.346969] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.347089] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.347206] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.347323] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.347441] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.347558] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.347679] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.347798] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.347916] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.348037] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
[    0.348155] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.348273] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.348391] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.348512] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *15
[    0.348629] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.348747] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.348866] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.348987] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *7
[    0.349105] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.349223] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.349342] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.349462] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.349583] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.349703] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.349828] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.349952] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.350099] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.350218] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.350337] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.350455] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.350574] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.350693] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.350812] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.350934] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.351055] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.351176] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.351297] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.351419] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.351541] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.351662] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *15
[    0.351783] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.351916] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.352039] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.352161] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *15
[    0.352297] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.352299] vgaarb: loaded
[    0.352501] SCSI subsystem initialized
[    0.352577] libata version 3.00 loaded.
[    0.352624] usbcore: registered new interface driver usbfs
[    0.352636] usbcore: registered new interface driver hub
[    0.352666] usbcore: registered new device driver usb
[    0.352868] wmi: Mapper loaded
[    0.352870] PCI: Using ACPI for IRQ routing
[    0.352874] PCI: pci_cache_line_size set to 64 bytes
[    0.352975] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.352977] reserve RAM buffer: 00000000cff90000 - 00000000cfffffff 
[    0.353081] NetLabel: Initializing
[    0.353082] NetLabel:  domain hash size = 128
[    0.353084] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.353098] NetLabel:  unlabeled traffic allowed by default
[    0.360572] AppArmor: AppArmor Filesystem Enabled
[    0.360605] pnp: PnP ACPI init
[    0.360624] ACPI: bus type pnp registered
[    0.360767] pnp 00:00: [bus 00-ff]
[    0.360769] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.360772] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.360774] pnp 00:00: [io  0x0d00-0xffff window]
[    0.360776] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.360778] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.360781] pnp 00:00: [mem 0xe0000000-0xdfffffff window disabled]
[    0.360783] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.360877] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.360912] pnp 00:01: [dma 4]
[    0.360914] pnp 00:01: [io  0x0000-0x000f]
[    0.360916] pnp 00:01: [io  0x0081-0x0083]
[    0.360918] pnp 00:01: [io  0x0087]
[    0.360920] pnp 00:01: [io  0x0089-0x008b]
[    0.360922] pnp 00:01: [io  0x008f]
[    0.360923] pnp 00:01: [io  0x00c0-0x00df]
[    0.360947] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.360955] pnp 00:02: [io  0x0061]
[    0.360980] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.360989] pnp 00:03: [io  0x00f0-0x00ff]
[    0.361004] pnp 00:03: [irq 13]
[    0.361027] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.361556] pnp 00:04: [mem 0x000d0000-0x000d3fff window]
[    0.361558] pnp 00:04: [mem 0x000d4000-0x000d7fff window]
[    0.361560] pnp 00:04: [mem 0x000de000-0x000dffff window]
[    0.361563] pnp 00:04: [io  0x0010-0x001f]
[    0.361564] pnp 00:04: [io  0x0022-0x003f]
[    0.361566] pnp 00:04: [io  0x0044-0x004d]
[    0.361568] pnp 00:04: [io  0x0050-0x005f]
[    0.361570] pnp 00:04: [io  0x0062-0x0063]
[    0.361572] pnp 00:04: [io  0x0065-0x006f]
[    0.361574] pnp 00:04: [io  0x0072-0x007f]
[    0.361576] pnp 00:04: [io  0x0080]
[    0.361577] pnp 00:04: [io  0x0084-0x0086]
[    0.361579] pnp 00:04: [io  0x0088]
[    0.361581] pnp 00:04: [io  0x008c-0x008e]
[    0.361583] pnp 00:04: [io  0x0090-0x009f]
[    0.361585] pnp 00:04: [io  0x00a2-0x00bf]
[    0.361587] pnp 00:04: [io  0x00e0-0x00ef]
[    0.361589] pnp 00:04: [io  0x04d0-0x04d1]
[    0.361591] pnp 00:04: [io  0x0800-0x080f]
[    0.361592] pnp 00:04: [io  0x2000-0x207f]
[    0.361594] pnp 00:04: [io  0x2080-0x20ff]
[    0.361596] pnp 00:04: [io  0x2400-0x247f]
[    0.361598] pnp 00:04: [io  0x2480-0x24ff]
[    0.361600] pnp 00:04: [io  0x2800-0x287f]
[    0.361602] pnp 00:04: [io  0x2880-0x28ff]
[    0.361604] pnp 00:04: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.361607] pnp 00:04: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.361609] pnp 00:04: [mem 0xfed04000-0xfed04fff]
[    0.361611] pnp 00:04: [mem 0xfee01000-0xfeefffff]
[    0.361705] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.361707] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.361710] system 00:04: [io  0x2000-0x207f] has been reserved
[    0.361713] system 00:04: [io  0x2080-0x20ff] has been reserved
[    0.361716] system 00:04: [io  0x2400-0x247f] has been reserved
[    0.361718] system 00:04: [io  0x2480-0x24ff] has been reserved
[    0.361721] system 00:04: [io  0x2800-0x287f] has been reserved
[    0.361723] system 00:04: [io  0x2880-0x28ff] has been reserved
[    0.361726] system 00:04: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.361729] system 00:04: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.361732] system 00:04: [mem 0x000de000-0x000dffff window] has been reserved
[    0.361735] system 00:04: [mem 0xfed04000-0xfed04fff] has been reserved
[    0.361738] system 00:04: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.361741] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.361794] pnp 00:05: [io  0x0070-0x0071]
[    0.361803] pnp 00:05: [irq 8]
[    0.361827] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.361907] pnp 00:06: [mem 0xfec00000-0xfec00fff]
[    0.361913] pnp 00:06: [mem 0xfee00000-0xfee00fff]
[    0.361958] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.361961] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.361964] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.361996] pnp 00:07: [io  0x0060]
[    0.361998] pnp 00:07: [io  0x0064]
[    0.362006] pnp 00:07: [irq 1]
[    0.362031] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.362080] pnp 00:08: [irq 12]
[    0.362107] pnp 00:08: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.362354] pnp 00:09: [io  0x03f8-0x03ff]
[    0.362362] pnp 00:09: [irq 4]
[    0.362364] pnp 00:09: [dma 0 disabled]
[    0.362422] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.362486] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.362489] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.362491] pnp 00:0a: [io  0x0290-0x029f]
[    0.362537] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.362540] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.362587] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.362636] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.362640] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.362812] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.362814] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.362816] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.362818] pnp 00:0c: [mem 0x00100000-0xdfffffff]
[    0.362820] pnp 00:0c: [mem 0xfec00000-0xffffffff]
[    0.362884] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.362887] system 00:0c: [mem 0x000c0000-0x000cffff] has been reserved
[    0.362890] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.362893] system 00:0c: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.362895] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.362898] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.363543] pnp: PnP ACPI: found 13 devices
[    0.363545] ACPI: ACPI bus type pnp unregistered
[    0.369702] Switching to clocksource acpi_pm
[    0.369867] pci 0000:00:08.0: PCI bridge to [bus 01-01]
[    0.369869] pci 0000:00:08.0:   bridge window [io  disabled]
[    0.369873] pci 0000:00:08.0:   bridge window [mem disabled]
[    0.369875] pci 0000:00:08.0:   bridge window [mem pref disabled]
[    0.369880] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.369883] pci 0000:00:0b.0:   bridge window [io  0xe000-0xefff]
[    0.369886] pci 0000:00:0b.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.369889] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf9ffffff 64bit pref]
[    0.369893] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.369895] pci 0000:00:10.0:   bridge window [io  disabled]
[    0.369904] pci 0000:00:10.0:   bridge window [mem disabled]
[    0.369912] pci 0000:00:10.0:   bridge window [mem 0xfbc00000-0xfbcfffff 64bit pref]
[    0.369924] pci 0000:00:12.0: PCI bridge to [bus 04-04]
[    0.369926] pci 0000:00:12.0:   bridge window [io  disabled]
[    0.369935] pci 0000:00:12.0:   bridge window [mem disabled]
[    0.369943] pci 0000:00:12.0:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.369955] pci 0000:00:13.0: PCI bridge to [bus 05-05]
[    0.369957] pci 0000:00:13.0:   bridge window [io  disabled]
[    0.369967] pci 0000:00:13.0:   bridge window [mem disabled]
[    0.369974] pci 0000:00:13.0:   bridge window [mem 0xfbe00000-0xfbefffff 64bit pref]
[    0.369974] Switched to NOHz mode on CPU #0
[    0.369974] pci 0000:00:14.0: PCI bridge to [bus 06-06]
[    0.369974] pci 0000:00:14.0:   bridge window [io  disabled]
[    0.369728] Switched to NOHz mode on CPU #1
[    0.369974] pci 0000:00:14.0:   bridge window [mem disabled]
[    0.369974] pci 0000:00:14.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.369974] pci 0000:00:08.0: setting latency timer to 64
[    0.369974] pci 0000:00:0b.0: setting latency timer to 64
[    0.369974] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.369974] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.369974] pci 0000:00:10.0: setting latency timer to 64
[    0.369974] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.369974] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.369974] pci 0000:00:12.0: setting latency timer to 64
[    0.369974] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
[    0.369974] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    0.369974] pci 0000:00:13.0: setting latency timer to 64
[    0.369974] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 16
[    0.369974] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
[    0.369974] pci 0000:00:14.0: setting latency timer to 64
[    0.369974] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.369974] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.369974] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.369974] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.369974] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfebfffff]
[    0.369974] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.369974] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.369974] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.369974] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.369974] pci_bus 0000:01: resource 8 [mem 0xf0000000-0xfebfffff]
[    0.369974] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.369974] pci_bus 0000:02: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.369974] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf9ffffff 64bit pref]
[    0.369974] pci_bus 0000:03: resource 2 [mem 0xfbc00000-0xfbcfffff 64bit pref]
[    0.369974] pci_bus 0000:04: resource 2 [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.369974] pci_bus 0000:05: resource 2 [mem 0xfbe00000-0xfbefffff 64bit pref]
[    0.369974] pci_bus 0000:06: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.369974] NET: Registered protocol family 2
[    0.369974] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.369974] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.369974] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.369974] TCP: Hash tables configured (established 524288 bind 65536)
[    0.369974] TCP reno registered
[    0.369974] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.369974] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.369974] NET: Registered protocol family 1
[    0.440145] pci 0000:00:07.0: Enabling HT MSI Mapping
[    0.440245] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.440350] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.440462] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    0.440573] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.440814] pci 0000:02:00.0: Boot video device
[    0.440817] PCI: CLS 64 bytes, default 64
[    0.441792] PCI-DMA: Disabling AGP.
[    0.441891] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.441893] PCI-DMA: using GART IOMMU.
[    0.441897] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.445196] audit: initializing netlink socket (disabled)
[    0.445209] type=2000 audit(1302879379.439:1): initialized
[    0.458547] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.460444] VFS: Disk quotas dquot_6.5.2
[    0.460502] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.461167] fuse init (API version 7.16)
[    0.461259] msgmni has been set to 7389
[    0.461514] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.461542] io scheduler noop registered
[    0.461544] io scheduler deadline registered
[    0.461584] io scheduler cfq registered (default)
[    0.462293] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.462316] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.462481] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.462487] ACPI: Power Button [PWRB]
[    0.462542] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.462545] ACPI: Power Button [PWRF]
[    0.462746] ACPI: acpi_idle registered with cpuidle
[    0.465339] ERST: Table is not found!
[    0.465425] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.485970] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.595258] Freeing initrd memory: 12832k freed
[    1.030682] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.040244] Linux agpgart interface v0.103
[    1.041486] brd: module loaded
[    1.042077] loop: module loaded
[    1.042190] i2c-core: driver [adp5520] using legacy suspend method
[    1.042192] i2c-core: driver [adp5520] using legacy resume method
[    1.042439] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.042759] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.042777] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.042793] pata_acpi 0000:00:09.0: setting latency timer to 64
[    1.042800] pata_acpi 0000:00:09.0: PCI INT A disabled
[    1.043269] Fixed MDIO Bus: probed
[    1.043302] PPP generic driver version 2.4.2
[    1.043369] tun: Universal TUN/TAP device driver, 1.6
[    1.043371] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.043478] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.043694] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    1.043705] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.043725] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.043728] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.043789] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.070058] ehci_hcd 0000:00:02.1: debug port 1
[    1.070065] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.070091] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfcf7ec00
[    1.090026] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.090155] hub 1-0:1.0: USB hub found
[    1.090159] hub 1-0:1.0: 6 ports detected
[    1.090461] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    1.090474] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    1.090489] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.090491] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.090537] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.090588] ehci_hcd 0000:00:04.1: debug port 1
[    1.090596] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.090615] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfcf7e800
[    1.110025] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.110134] hub 2-0:1.0: USB hub found
[    1.110138] hub 2-0:1.0: 6 ports detected
[    1.110231] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.110453] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    1.110465] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    1.110478] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.110480] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.110525] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.110579] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfcf7f000
[    1.172130] hub 3-0:1.0: USB hub found
[    1.172135] hub 3-0:1.0: 6 ports detected
[    1.172432] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    1.172435] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    1.172448] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.172451] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.172493] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.172546] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfcf7d000
[    1.232124] hub 4-0:1.0: USB hub found
[    1.232129] hub 4-0:1.0: 6 ports detected
[    1.232215] uhci_hcd: USB Universal Host Controller Interface driver
[    1.250053] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.253159] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.253166] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.253297] mousedev: PS/2 mouse device common for all mice
[    1.253424] rtc_cmos 00:05: RTC can wake from S4
[    1.271711] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.290093] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.290143] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.290243] device-mapper: uevent: version 1.0.3
[    1.290316] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.290414] device-mapper: multipath: version 1.2.0 loaded
[    1.290416] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.290556] cpuidle: using governor ladder
[    1.290558] cpuidle: using governor menu
[    1.290840] TCP cubic registered
[    1.290971] NET: Registered protocol family 10
[    1.291466] NET: Registered protocol family 17
[    1.291485] Registering the dns_resolver key type
[    1.291511] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e (2 cpu cores) (version 2.20.00)
[    1.291556] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[    1.291558] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[    1.291560] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[    1.291561] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[    1.291563] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[    1.291565] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[    1.291719] PM: Hibernation image not present or could not be loaded.
[    1.291739] registered taskstats version 1
[    1.292140]   Magic number: 7:489:940
[    1.292279] rtc_cmos 00:05: setting system clock to 2011-04-15 14:56:20 UTC (1302879380)
[    1.292282] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.292284] EDD information not available.
[    1.294002] Freeing unused kernel memory: 956k freed
[    1.294442] Write protecting the kernel read-only data: 10240k
[    1.295178] Freeing unused kernel memory: 184k freed
[    1.299966] Freeing unused kernel memory: 1444k freed
[    1.323518] <30>udev[102]: starting version 167
[    1.452707] pata_amd 0000:00:06.0: version 0.4.1
[    1.452753] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.455364] scsi0 : pata_amd
[    1.457027] scsi1 : pata_amd
[    1.458461] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.458464] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.461508] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.461740] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.461746] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.461750] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.541270] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:19:66:94:14:d3
[    1.541274] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.541368] ahci 0000:00:09.0: version 3.0
[    1.541383] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.541439] ahci 0000:00:09.0: irq 40 for MSI/MSI-X
[    1.541445] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    1.541519] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.541522] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio sxs boh 
[    1.541526] ahci 0000:00:09.0: setting latency timer to 64
[    1.542684] scsi2 : ahci
[    1.542781] scsi3 : ahci
[    1.542872] scsi4 : ahci
[    1.542957] scsi5 : ahci
[    1.543043] scsi6 : ahci
[    1.543132] scsi7 : ahci
[    1.543286] ata3: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76100 irq 40
[    1.543289] ata4: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76180 irq 40
[    1.543292] ata5: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76200 irq 40
[    1.543295] ata6: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76280 irq 40
[    1.543297] ata7: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76300 irq 40
[    1.543300] ata8: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76380 irq 40
[    1.630351] ata1.00: ATAPI: MAD DOG MD-16XDVD9A2, 1.F3, max UDMA/33
[    1.630359] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)
[    1.670318] ata1.00: configured for UDMA/33
[    1.671784] scsi 0:0:0:0: CD-ROM            MAD DOG  MD-16XDVD9A2     1.F3 PQ: 0 ANSI: 5
[    1.673150] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.673153] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.673297] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.673368] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.673457] ata2: port disabled. ignoring.
[    1.690038] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.890034] ata7: SATA link down (SStatus 0 SControl 300)
[    1.890049] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.890060] ata5: SATA link down (SStatus 0 SControl 300)
[    1.890071] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.890079] ata6: SATA link down (SStatus 0 SControl 300)
[    1.890089] ata8: SATA link down (SStatus 0 SControl 300)
[    1.891567] ata3.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[    1.891570] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.891960] ata4.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    1.891963] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.893496] ata3.00: configured for UDMA/133
[    1.893608] scsi 2:0:0:0: Direct-Access     ATA      ST31000340AS     SD15 PQ: 0 ANSI: 5
[    1.893795] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.893801] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.893859] sd 2:0:0:0: [sda] Write Protect is off
[    1.893862] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.893885] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.894018] ata4.00: configured for UDMA/133
[    1.894213] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    1.894359] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.894367] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.894409] sd 3:0:0:0: [sdb] Write Protect is off
[    1.894412] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.894437] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.936652]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.937108] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.946531]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    1.946861] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.963361] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input3
[    1.963489] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:02.0-2/input0
[    1.963513] usbcore: registered new interface driver usbhid
[    1.963515] usbhid: USB HID core driver
[    2.040044] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.328018] EXT3-fs: barriers not enabled
[    2.337565] kjournald starting.  Commit interval 5 seconds
[    2.337597] EXT3-fs (sdb6): mounted filesystem with ordered data mode
[   21.920786] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
[   21.935579] <30>udev[373]: starting version 167
[   21.989825] lp: driver loaded but no devices found
[   22.032231] EXT3-fs (sdb6): using internal journal
[   22.239762] type=1400 audit(1302872201.437:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=599 comm="apparmor_parser"
[   22.240164] type=1400 audit(1302872201.447:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=599 comm="apparmor_parser"
[   22.240377] type=1400 audit(1302872201.447:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=599 comm="apparmor_parser"
[   22.240931] i2c i2c-0: nForce2 SMBus adapter at 0x2d00
[   22.240935] ACPI: resource nForce2_smbus [io  0x2e00-0x2e3f] conflicts with ACPI region SM00 [io 0x2e00-0x2e3f]
[   22.240938] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.328941] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[   22.335382] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.337877] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:00/input/input4
[   22.337973] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[   22.369139] forcedeth 0000:00:0a.0: irq 41 for MSI/MSI-X
[   22.406189] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   22.406274] MCE: In-kernel MCE decoding enabled.
[   22.426991] EDAC MC: Ver: 2.1.0 Apr 11 2011
[   22.443230] EDAC amd64_edac: v3.3.0
[   22.449729] EDAC amd64: DRAM ECC disabled.
[   22.449739] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   22.449741]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   22.449742]  (Note that use of the override may cause unknown side effects.)
[   22.476352] nvidia: module license 'NVIDIA' taints kernel.
[   22.476358] Disabling lock debugging due to kernel taint
[   23.151674] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   23.362846] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21
[   23.362854] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 21 (level, low) -> IRQ 21
[   23.362864] nvidia 0000:02:00.0: setting latency timer to 64
[   23.362869] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   23.364200] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.03  Sat Apr  9 00:06:19 PDT 2011
[   23.377214] type=1400 audit(1302872202.577:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=879 comm="apparmor_parser"
[   23.378814] type=1400 audit(1302872202.577:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=879 comm="apparmor_parser"
[   23.379037] type=1400 audit(1302872202.577:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=879 comm="apparmor_parser"
[   23.389053] type=1400 audit(1302872202.587:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=883 comm="apparmor_parser"
[   23.395364] type=1400 audit(1302872202.597:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=883 comm="apparmor_parser"
[   23.398257] type=1400 audit(1302872202.597:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=883 comm="apparmor_parser"
[   23.404321] type=1400 audit(1302872202.607:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=888 comm="apparmor_parser"
[   23.444105] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   23.444111] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   23.444301] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   23.444306] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   23.444310] hda_intel: msi for device 1849:0888 set to 0
[   23.444312] hda_intel: position_fix set to 1 for device 1849:0888
[   23.444342] HDA Intel 0000:00:07.0: setting latency timer to 64
[   24.990092] hda_codec: ALC888: BIOS auto-probing.
[   24.990098] hda_codec: ALC888: SKU not ready 0x411111f0
[   26.510440] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input6
[   27.671706] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90012380000, using 1216k, total 1216k
[   27.671710] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   27.671713] vesafb: scrolling: redraw
[   27.671715] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   27.671894] Console: switching to colour frame buffer device 80x30
[   27.671907] fb0: VESA VGA frame buffer device
[   27.714778] ppdev: user-space parallel port driver
[   27.731349] audit_printk_skb: 12 callbacks suppressed
[   27.731353] type=1400 audit(1302872206.937:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1434 comm="apparmor_parser"
[   27.732969] type=1400 audit(1302872206.937:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1434 comm="apparmor_parser"
[   32.900018] eth0: no IPv6 routers present
```

---

### Post by no2498 on 2011-04-16
is your cam plugged in to a hub if yes it needs to be plugged in to the computer

---

### Post by nikio on 2011-04-16
Directly plugged into the computer,
and the cam works normally under Win...

I think that the problem must be the driver. :(

EDIT: I've just had a reply from the developer of the m5602 driver, saying it is not supporting my cam... so back to sourceforge!

---

### Post by no2498 on 2011-04-16
retry gstreamer-properties
just for me

---

### Post by nikio on 2011-04-17
:)
the output on the terminal is
> ~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

in Video - Default input
Plugin:  the only choices for are now
Test Input
Video for Linux 2 (vfl2)
Custom

(V4L has disappeared by updating)

Source is set to "none" and greyed out

Pipeline (activated only when I chose "custom" from the Plugin menu) has a default value v4l2src

TEST:

Test Input gives a square window with multicolor bands on screen.

with v4l2 in plugin I get
> Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

with: custom v4l2src
> Custom: Cannot identify device '/dev/video0'.

I guessed: custom v4lsrc
> Custom: no element "v4lsrc"

---

### Post by no2498 on 2011-04-17
odd the cam is over 3 years old and not working yet

---

### Post by nikio on 2011-04-18
Yep, odd, I suppose my cam is too "out of standard"

strangely I found a cam from the dark side (M$) that works in linux... the temptation is strong. ;)

no2498, thank you for trying.

---

### Post by BicyclerBoy on 2011-04-18
If you do want to build dvb-v4l...
You could try a more up-to-date libv4l package..

[https://launchpad.net/~libv4l/+archive/ppa]("https://launchpad.net/%7Elibv4l/+archive/ppa")

Not sure if this will help..as this package looks like an abstraction layer & not device drivers..

---

### Post by nikio on 2011-04-18
Oh, an abstraction layer, of course... :confused: :)
Do you mean that I should install all those things?

> debhelper 	7.0.13ubuntu1~hhwkt1
gtk-v4l 	0.3-0~mmv4l1 
gtk-v4l 	0.3-0~llv4l1 
gtk-v4l 	0.1-1 
libv4l 	0.6.4-1+hg20100214~jjv4l1
libv4l 	0.6.3-1~iiv4l1 
libv4l 	0.6.3-1~hhv4l1 
v4l-utils 	0.8.3-0~nnv4l1 (Newer version available) 
v4l-utils 	0.8.3-0~mmv4l1 
v4l-utils 	0.8.3-0~llv4l1 
v4l-utils 	0.8.2-0~kkv4l2 
v4l2ucp 	2.0.2-1~kkv4l1 
v4l2ucp 	1.4-0ubuntu1~jjv4l1
v4l2ucp 	1.3-2.1~iiv4l1 
v4l2ucp 	1.3-2.1~hhv4l1 

---

### Post by BicyclerBoy on 2011-04-18
Worth a try..but I doubt it will solve your problem..
Can't do any harm as this is via package manager so you can always just un-install package, reload & update & remove ppa..

dvb-v4l package:
I have not found a recent dvb-v4l ppa so compiling from source is the only option (apart from waiting).

---

### Post by nikio on 2011-04-19
I think I managed to install the package but didn't help.
Thank you anyway.

---

### Post by nikio on 2011-04-29
I finally got the webcam to work somehow,
the developer of the driver has opened an other thread in this forum.
[That's]("http://ubuntuforums.org/showthread.php?t=1629175") the best place to post!

---

### Post by no2498 on 2011-04-29
if the cam is still dark install v4l2ucp

it comes up in system prefrences as video4linux control panel 

you can set the cam in it

---

### Post by nikio on 2011-05-03
I've tried v4l2ucp, it looks a little buggy, in crashes if I use the "brightness" control, making cheese crash too,
gamma correction gives a usable image though.
Thank you!

---

