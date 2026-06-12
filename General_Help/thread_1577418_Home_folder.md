---
title: "Home folder"
date: 2010-09-18
forum: General Help
---

### Post by johnson094 on 2010-09-18
Hi,
 
Don't know if I'm in the correct forum area, and I did search for a similar problem without success.  Anyway, I am running Ubuntu 10.04.1 on a separate drive, and thus far everything seems to be running well.  I enabled the sound which accompanies clicks of the mouse, etc.  Whenever I try to open "Places" "home", I suddenly get a cycling black screen and I hear the Ubuntu drums" off and on until the computer locks up.  I cannot get the computer to reset, and I have to turn the CPU off and on again to reboot.  If I wait too long the only way to reboot is to disconnect power source then reboot.  Anyone have any help for a newbie.  I knew the "proud peacock" would be tucking his tail.
 
Thanks in advance
:confused:David

---

### Post by andrewthomas on 2010-09-19
Are you sure that enabling system sounds is all the changes that you made?

---

### Post by johnson094 on 2010-09-19
Well I had just gotten Ubuntu up and working and I was kind of browsing around..yeah I know what you are thinking...another newbie just looking around, but for the most part I did just open look and close areas related to printers, hardware, networking.  I decided to look at sound since I had experienced graphics card problems in the early days of install.  So I selected "Ubuntu" as theme sound and selected my alert tone and closed.  
 
I also made some changes to my graphics...System-Preferences-Appearance.
 
Theme-new wave
Bacground -universe
Fonts-default
Visual effects-none
 
My screen now cycles through various awsome pictures of the universe like a slide show.
 
I have reviewed everything under applications, places, and administration and found nothing else I made changes to.  Here's what happens:
 
From desktop each time:
 
1.  Select Places>Home folder>computer locks up
2.  Select Places>Desktop>Open parent folder>computer locks up
3.  Select places>Desktop>Open personal folder>computer locks up
4.  Select places>any of the personal folders listed below "desktop">no problem, can view any one of these folders, but when I try to go to the root folder "david" in order to change personal folder,  computer locks up.
 
I am going to reproduce this a couple of times and then paste my activity log,  maybe that will tell you what's going on.  Never done this before so bear with me as I figure out how to do it.
 
David

---

### Post by johnson094 on 2010-09-19
I attempted to access my home folder 3 times as described in previous post.  I am attaching the log event which starts 9/19/10 @10:15 am. I apologize because there is so much, but I had to reboot 3 times.

Sep 19 10:15:22 david-pc pulseaudio[1378]: pid.c: Stale PID file, overwriting.
Sep 19 10:15:22 david-pc pulseaudio[1378]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socSep 19 10:16:35 david-pc kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 19 10:16:35 david-pc rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="608" x-info="http://www.rsyslog.com"] (re)start
Sep 19 10:16:35 david-pc rsyslogd: rsyslogd's groupid changed to 103
Sep 19 10:16:35 david-pc rsyslogd: rsyslogd's userid changed to 101
Sep 19 10:16:35 david-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 19 10:16:35 david-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 19 10:16:35 david-pc kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 (Ubuntu 2.6.32-24.43-generic 2.6.32.15+drm33.5)
Sep 19 10:16:35 david-pc kernel: [    0.000000] KERNEL supported cpus:
Sep 19 10:16:35 david-pc kernel: [    0.000000]   Intel GenuineIntel
Sep 19 10:16:35 david-pc kernel: [    0.000000]   AMD AuthenticAMD
Sep 19 10:16:35 david-pc kernel: [    0.000000]   NSC Geode by NSC
Sep 19 10:16:35 david-pc kernel: [    0.000000]   Cyrix CyrixInstead
Sep 19 10:16:35 david-pc kernel: [    0.000000]   Centaur CentaurHauls
Sep 19 10:16:35 david-pc kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 19 10:16:35 david-pc kernel: [    0.000000]   Transmeta TransmetaCPU
Sep 19 10:16:35 david-pc kernel: [    0.000000]   UMC UMC UMC UMC
Sep 19 10:16:35 david-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7f0000 (usable)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 000000003f7f3000 - 000000003f800000 (ACPI data)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000] DMI 2.3 present.
Sep 19 10:16:35 david-pc kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Sep 19 10:16:35 david-pc kernel: [    0.000000] last_pfn = 0x3f7f0 max_arch_pfn = 0x100000
Sep 19 10:16:35 david-pc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep 19 10:16:35 david-pc kernel: [    0.000000] Scanning 0 areas for low memory corruption
Sep 19 10:16:35 david-pc kernel: [    0.000000] modified physical RAM map:
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 0000000000100000 - 000000003f7f0000 (usable)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 000000003f7f3000 - 000000003f800000 (ACPI data)
Sep 19 10:16:35 david-pc kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Sep 19 10:16:35 david-pc kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Sep 19 10:16:35 david-pc kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Sep 19 10:16:35 david-pc kernel: [    0.000000] RAMDISK: 2f29b000 - 2fa33bf0
Sep 19 10:16:35 david-pc kernel: [    0.000000] ACPI Error: A valid RSDP was not found (20090903/tbxfroot-219)
Sep 19 10:16:35 david-pc kernel: [    0.000000] 127MB HIGHMEM available.
Sep 19 10:16:35 david-pc kernel: [    0.000000] 887MB LOWMEM available.
Sep 19 10:16:35 david-pc kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Sep 19 10:16:35 david-pc kernel: [    0.000000]   low ram: 0 - 377fe000
Sep 19 10:16:35 david-pc kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Sep 19 10:16:35 david-pc kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Sep 19 10:16:35 david-pc kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #4 [002f29b000 - 002fa33bf0]          RAMDISK ==> [002f29b000 - 002fa33bf0]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #6 [00008de000 - 00008e1194]              BRK ==> [00008de000 - 00008e1194]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Sep 19 10:16:35 david-pc kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Sep 19 10:16:35 david-pc kernel: [    0.000000] found SMP MP-table at [c00f5f00] f5f00
Sep 19 10:16:35 david-pc kernel: [    0.000000] Zone PFN ranges:
Sep 19 10:16:35 david-pc kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 19 10:16:35 david-pc kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Sep 19 10:16:35 david-pc kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f7f0
Sep 19 10:16:35 david-pc kernel: [    0.000000] Movable zone start PFN for each node
Sep 19 10:16:35 david-pc kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep 19 10:16:35 david-pc kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep 19 10:16:35 david-pc kernel: [    0.000000]     0: 0x00000100 -> 0x0003f7f0
Sep 19 10:16:35 david-pc kernel: [    0.000000] Using APIC driver default
Sep 19 10:16:35 david-pc kernel: [    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Sep 19 10:16:35 david-pc kernel: [    0.000000]     Virtual Wire compatibility mode.
Sep 19 10:16:35 david-pc kernel: [    0.000000] MPTABLE: OEM ID: OEM00000
Sep 19 10:16:35 david-pc kernel: [    0.000000] MPTABLE: Product ID: PROD00000000
Sep 19 10:16:35 david-pc kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Sep 19 10:16:35 david-pc kernel: [    0.000000] Processor #0 (Bootup-CPU)
Sep 19 10:16:35 david-pc kernel: [    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
Sep 19 10:16:35 david-pc kernel: [    0.000000] Processors: 1
Sep 19 10:16:35 david-pc kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Sep 19 10:16:35 david-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 10:16:35 david-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Sep 19 10:16:35 david-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Sep 19 10:16:35 david-pc kernel: [    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf400000)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 19 10:16:35 david-pc kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Sep 19 10:16:35 david-pc kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
Sep 19 10:16:35 david-pc kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
Sep 19 10:16:35 david-pc kernel: [    0.000000] pcpu-alloc: [0] 0 
Sep 19 10:16:35 david-pc kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257935
Sep 19 10:16:35 david-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=444cbddf-4be0-403f-8197-ad0432f5e984 ro quiet splash
Sep 19 10:16:35 david-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 19 10:16:35 david-pc kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 19 10:16:35 david-pc kernel: [    0.000000] Initializing CPU#0
Sep 19 10:16:35 david-pc kernel: [    0.000000] allocated 5201280 bytes of page_cgroup
Sep 19 10:16:35 david-pc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep 19 10:16:35 david-pc kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f7f0)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Memory: 1009368k/1040320k available (4679k kernel code, 29952k reserved, 2124k data, 660k init, 131016k highmem)
Sep 19 10:16:35 david-pc kernel: [    0.000000] virtual kernel memory layout:
Sep 19 10:16:35 david-pc kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Sep 19 10:16:35 david-pc kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 19 10:16:35 david-pc kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Sep 19 10:16:35 david-pc kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Sep 19 10:16:35 david-pc kernel: [    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
Sep 19 10:16:35 david-pc kernel: [    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
Sep 19 10:16:35 david-pc kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
Sep 19 10:16:35 david-pc kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep 19 10:16:35 david-pc kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Sep 19 10:16:35 david-pc kernel: [    0.000000] Hierarchical RCU implementation.
Sep 19 10:16:35 david-pc kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Sep 19 10:16:35 david-pc kernel: [    0.000000] Console: colour VGA+ 80x25
Sep 19 10:16:35 david-pc kernel: [    0.000000] console [tty0] enabled
Sep 19 10:16:35 david-pc kernel: [    0.000000] Fast TSC calibration using PIT
Sep 19 10:16:35 david-pc kernel: [    0.000000] Detected 2932.858 MHz processor.
Sep 19 10:16:35 david-pc kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5865.71 BogoMIPS (lpj=11731432)
Sep 19 10:16:35 david-pc kernel: [    0.004035] Security Framework initialized
Sep 19 10:16:35 david-pc kernel: [    0.004072] AppArmor: AppArmor initialized
Sep 19 10:16:35 david-pc kernel: [    0.004083] Mount-cache hash table entries: 512
Sep 19 10:16:35 david-pc kernel: [    0.004263] Initializing cgroup subsys ns
Sep 19 10:16:35 david-pc kernel: [    0.004270] Initializing cgroup subsys cpuacct
Sep 19 10:16:35 david-pc kernel: [    0.004276] Initializing cgroup subsys memory
Sep 19 10:16:35 david-pc kernel: [    0.004289] Initializing cgroup subsys devices
Sep 19 10:16:35 david-pc kernel: [    0.004292] Initializing cgroup subsys freezer
Sep 19 10:16:35 david-pc kernel: [    0.004295] Initializing cgroup subsys net_cls
Sep 19 10:16:35 david-pc kernel: [    0.004332] CPU: Trace cache: 12K uops, L1 D cache: 16K
Sep 19 10:16:35 david-pc kernel: [    0.004336] CPU: L2 cache: 256K
Sep 19 10:16:35 david-pc kernel: [    0.004340] CPU: Hyper-Threading is disabled
Sep 19 10:16:35 david-pc kernel: [    0.004346] mce: CPU supports 4 MCE banks
Sep 19 10:16:35 david-pc kernel: [    0.004362] CPU0: Thermal monitoring enabled (TM1)
Sep 19 10:16:35 david-pc kernel: [    0.004370] using mwait in idle threads.
Sep 19 10:16:35 david-pc kernel: [    0.004381] Performance Events: no PMU driver, software events only.
Sep 19 10:16:35 david-pc kernel: [    0.004391] Checking 'hlt' instruction... OK.
Sep 19 10:16:35 david-pc kernel: [    0.021211] SMP alternatives: switching to UP code
Sep 19 10:16:35 david-pc kernel: [    0.034645] Freeing SMP alternatives: 19k freed
Sep 19 10:16:35 david-pc kernel: [    0.034677] ftrace: converting mcount calls to 0f 1f 44 00 00
Sep 19 10:16:35 david-pc kernel: [    0.034688] ftrace: allocating 21780 entries in 43 pages
Sep 19 10:16:35 david-pc kernel: [    0.036136] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 19 10:16:35 david-pc kernel: [    0.036197] ExtINT not setup in hardware but reported by MP table
Sep 19 10:16:35 david-pc kernel: [    0.036466] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Sep 19 10:16:35 david-pc kernel: [    0.076821] CPU0: Intel(R) Celeron(R) CPU 2.93GHz stepping 04
Sep 19 10:16:35 david-pc kernel: [    0.184270] Brought up 1 CPUs
Sep 19 10:16:35 david-pc kernel: [    0.184274] Total of 1 processors activated (5865.71 BogoMIPS).
Sep 19 10:16:35 david-pc kernel: [    0.184559] devtmpfs: initialized
Sep 19 10:16:35 david-pc kernel: [    0.185139] regulator: core version 0.5
Sep 19 10:16:35 david-pc kernel: [    0.185167] Time: 10:16:23  Date: 09/19/10
Sep 19 10:16:35 david-pc kernel: [    0.185244] NET: Registered protocol family 16
Sep 19 10:16:35 david-pc kernel: [    0.185426] EISA bus registered
Sep 19 10:16:35 david-pc kernel: [    0.213105] PCI: PCI BIOS revision 2.10 entry at 0xfb9b0, last bus=1
Sep 19 10:16:35 david-pc kernel: [    0.213108] PCI: Using configuration type 1 for base access
Sep 19 10:16:35 david-pc kernel: [    0.214476] bio: create slab <bio-0> at 0
Sep 19 10:16:35 david-pc kernel: [    0.214576] ACPI: Interpreter disabled.
Sep 19 10:16:35 david-pc kernel: [    0.214674] vgaarb: loaded
Sep 19 10:16:35 david-pc kernel: [    0.214850] SCSI subsystem initialized
Sep 19 10:16:35 david-pc kernel: [    0.215073] usbcore: registered new interface driver usbfs
Sep 19 10:16:35 david-pc kernel: [    0.215091] usbcore: registered new interface driver hub
Sep 19 10:16:35 david-pc kernel: [    0.215141] usbcore: registered new device driver usb
Sep 19 10:16:35 david-pc kernel: [    0.215328] PCI: Probing PCI hardware
Sep 19 10:16:35 david-pc kernel: [    0.215826] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Sep 19 10:16:35 david-pc kernel: [    0.215832] pci 0000:00:1d.7: PME# disabled
Sep 19 10:16:35 david-pc kernel: [    0.215887] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Sep 19 10:16:35 david-pc kernel: [    0.215889] * this clock source is slow. If you are sure your timer does not have
Sep 19 10:16:35 david-pc kernel: [    0.215890] * this bug, please use "acpi_pm_good" to disable the workaround
Sep 19 10:16:35 david-pc kernel: [    0.215937] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Sep 19 10:16:35 david-pc kernel: [    0.215942] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Sep 19 10:16:35 david-pc kernel: [    0.216186] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Sep 19 10:16:35 david-pc kernel: [    0.216191] pci 0000:00:1f.5: PME# disabled
Sep 19 10:16:35 david-pc kernel: [    0.216307] pci 0000:01:0b.0: PME# supported from D2 D3hot D3cold
Sep 19 10:16:35 david-pc kernel: [    0.216311] pci 0000:01:0b.0: PME# disabled
Sep 19 10:16:35 david-pc kernel: [    0.216403] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
Sep 19 10:16:35 david-pc kernel: [    0.216407] pci 0000:01:0c.0: PME# disabled
Sep 19 10:16:35 david-pc kernel: [    0.216438] pci 0000:00:1e.0: transparent bridge
Sep 19 10:16:35 david-pc kernel: [    0.216519] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Sep 19 10:16:35 david-pc kernel: [    0.216875] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:24c0]
Sep 19 10:16:35 david-pc kernel: [    0.217078] NetLabel: Initializing
Sep 19 10:16:35 david-pc kernel: [    0.217082] NetLabel:  domain hash size = 128
Sep 19 10:16:35 david-pc kernel: [    0.217084] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 19 10:16:35 david-pc kernel: [    0.217102] NetLabel:  unlabeled traffic allowed by default
Sep 19 10:16:35 david-pc kernel: [    0.217182] Switching to clocksource tsc
Sep 19 10:16:35 david-pc kernel: [    0.219785] AppArmor: AppArmor Filesystem Enabled
Sep 19 10:16:35 david-pc kernel: [    0.219794] pnp: PnP ACPI: disabled
Sep 19 10:16:35 david-pc kernel: [    0.219801] PnPBIOS: Scanning system for PnP BIOS support...
Sep 19 10:16:35 david-pc kernel: [    0.219850] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc3b0
Sep 19 10:16:35 david-pc kernel: [    0.219854] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc3e0, dseg 0xf0000
Sep 19 10:16:35 david-pc kernel: [    0.219998] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:08: iomem range 0xffb00000-0xffb7ffff has been reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:08: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:08: iomem range 0xfee00000-0xfee0ffff has been reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:08: iomem range 0x100000-0xffffff could not be reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:09: iomem range 0xf8000-0xfffff could not be reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] system 00:09: iomem range 0xcc000-0xcffff has been reserved
Sep 19 10:16:35 david-pc kernel: [    0.219998] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Sep 19 10:16:35 david-pc kernel: [    0.219998] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Sep 19 10:16:35 david-pc kernel: [    0.219998] pci 0000:00:1e.0:   MEM window: 0xec000000-0xedffffff
Sep 19 10:16:35 david-pc kernel: [    0.219998] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x400fffff
Sep 19 10:16:35 david-pc kernel: [    0.219998] NET: Registered protocol family 2
Sep 19 10:16:35 david-pc kernel: [    0.219998] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.220278] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.221518] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.222233] TCP: Hash tables configured (established 131072 bind 65536)
Sep 19 10:16:35 david-pc kernel: [    0.222241] TCP reno registered
Sep 19 10:16:35 david-pc kernel: [    0.222455] NET: Registered protocol family 1
Sep 19 10:16:35 david-pc kernel: [    0.222904] cpufreq-nforce2: No nForce2 chipset.
Sep 19 10:16:35 david-pc kernel: [    0.222947] Scanning for low memory corruption every 60 seconds
Sep 19 10:16:35 david-pc kernel: [    0.223103] audit: initializing netlink socket (disabled)
Sep 19 10:16:35 david-pc kernel: [    0.223123] type=2000 audit(1284891382.222:1): initialized
Sep 19 10:16:35 david-pc kernel: [    0.232452] Trying to unpack rootfs image as initramfs...
Sep 19 10:16:35 david-pc kernel: [    0.243193] highmem bounce pool size: 64 pages
Sep 19 10:16:35 david-pc kernel: [    0.243203] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep 19 10:16:35 david-pc kernel: [    0.250926] VFS: Disk quotas dquot_6.5.2
Sep 19 10:16:35 david-pc kernel: [    0.251062] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 19 10:16:35 david-pc kernel: [    0.251947] fuse init (API version 7.13)
Sep 19 10:16:35 david-pc kernel: [    0.252094] msgmni has been set to 1716
Sep 19 10:16:35 david-pc kernel: [    0.252456] alg: No test for stdrng (krng)
Sep 19 10:16:35 david-pc kernel: [    0.252575] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep 19 10:16:35 david-pc kernel: [    0.252580] io scheduler noop registered
Sep 19 10:16:35 david-pc kernel: [    0.252583] io scheduler anticipatory registered
Sep 19 10:16:35 david-pc kernel: [    0.252585] io scheduler deadline registered
Sep 19 10:16:35 david-pc kernel: [    0.252637] io scheduler cfq registered (default)
Sep 19 10:16:35 david-pc kernel: [    0.252780] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 19 10:16:35 david-pc kernel: [    0.252815] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 19 10:16:35 david-pc kernel: [    0.261073] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Sep 19 10:16:35 david-pc kernel: [    0.261190] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 19 10:16:35 david-pc kernel: [    0.261752] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 19 10:16:35 david-pc kernel: [    0.262820] isapnp: Scanning for PnP cards...
Sep 19 10:16:35 david-pc kernel: [    0.268853] brd: module loaded
Sep 19 10:16:35 david-pc kernel: [    0.269530] loop: module loaded
Sep 19 10:16:35 david-pc kernel: [    0.269701] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 19 10:16:35 david-pc kernel: [    0.269893] ata_piix 0000:00:1f.1: PCI->APIC IRQ transform: INT A -> IRQ 16
Sep 19 10:16:35 david-pc kernel: [    0.270108] scsi0 : ata_piix
Sep 19 10:16:35 david-pc kernel: [    0.275130] scsi1 : ata_piix
Sep 19 10:16:35 david-pc kernel: [    0.275232] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Sep 19 10:16:35 david-pc kernel: [    0.275237] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Sep 19 10:16:35 david-pc kernel: [    0.275743] Fixed MDIO Bus: probed
Sep 19 10:16:35 david-pc kernel: [    0.275797] PPP generic driver version 2.4.2
Sep 19 10:16:35 david-pc kernel: [    0.275904] tun: Universal TUN/TAP device driver, 1.6
Sep 19 10:16:35 david-pc kernel: [    0.275908] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 19 10:16:35 david-pc kernel: [    0.276061] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 19 10:16:35 david-pc kernel: [    0.276108] ehci_hcd 0000:00:1d.7: PCI->APIC IRQ transform: INT D -> IRQ 23
Sep 19 10:16:35 david-pc kernel: [    0.276142] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 19 10:16:35 david-pc kernel: [    0.276215] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Sep 19 10:16:35 david-pc kernel: [    0.324091] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee080000
Sep 19 10:16:35 david-pc kernel: [    0.342780] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Sep 19 10:16:35 david-pc kernel: [    0.343003] usb usb1: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    0.343046] hub 1-0:1.0: USB hub found
Sep 19 10:16:35 david-pc kernel: [    0.343063] hub 1-0:1.0: 6 ports detected
Sep 19 10:16:35 david-pc kernel: [    0.343154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 19 10:16:35 david-pc kernel: [    0.343178] uhci_hcd: USB Universal Host Controller Interface driver
Sep 19 10:16:35 david-pc kernel: [    0.343241] uhci_hcd 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 16
Sep 19 10:16:35 david-pc kernel: [    0.343257] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 19 10:16:35 david-pc kernel: [    0.343345] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Sep 19 10:16:35 david-pc kernel: [    0.343383] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Sep 19 10:16:35 david-pc kernel: [    0.343542] usb usb2: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    0.343583] hub 2-0:1.0: USB hub found
Sep 19 10:16:35 david-pc kernel: [    0.343597] hub 2-0:1.0: 2 ports detected
Sep 19 10:16:35 david-pc kernel: [    0.343670] uhci_hcd 0000:00:1d.1: PCI->APIC IRQ transform: INT B -> IRQ 19
Sep 19 10:16:35 david-pc kernel: [    0.343685] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 19 10:16:35 david-pc kernel: [    0.343756] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Sep 19 10:16:35 david-pc kernel: [    0.343791] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Sep 19 10:16:35 david-pc kernel: [    0.343943] usb usb3: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    0.343982] hub 3-0:1.0: USB hub found
Sep 19 10:16:35 david-pc kernel: [    0.343994] hub 3-0:1.0: 2 ports detected
Sep 19 10:16:35 david-pc kernel: [    0.344062] uhci_hcd 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18
Sep 19 10:16:35 david-pc kernel: [    0.344078] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 19 10:16:35 david-pc kernel: [    0.344154] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Sep 19 10:16:35 david-pc kernel: [    0.344189] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Sep 19 10:16:35 david-pc kernel: [    0.344343] usb usb4: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    0.344383] hub 4-0:1.0: USB hub found
Sep 19 10:16:35 david-pc kernel: [    0.344396] hub 4-0:1.0: 2 ports detected
Sep 19 10:16:35 david-pc kernel: [    0.344535] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
Sep 19 10:16:35 david-pc kernel: [    0.344538] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep 19 10:16:35 david-pc kernel: [    0.345126] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 19 10:16:35 david-pc kernel: [    0.345352] mice: PS/2 mouse device common for all mice
Sep 19 10:16:35 david-pc kernel: [    0.351137] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Sep 19 10:16:35 david-pc kernel: [    0.351170] rtc0: alarms up to one day, 114 bytes nvram
Sep 19 10:16:35 david-pc kernel: [    0.351365] device-mapper: uevent: version 1.0.3
Sep 19 10:16:35 david-pc kernel: [    0.351607] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Sep 19 10:16:35 david-pc kernel: [    0.351721] device-mapper: multipath: version 1.1.0 loaded
Sep 19 10:16:35 david-pc kernel: [    0.351725] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 19 10:16:35 david-pc kernel: [    0.351925] EISA: Probing bus 0 at eisa.0
Sep 19 10:16:35 david-pc kernel: [    0.351965] EISA: Detected 0 cards.
Sep 19 10:16:35 david-pc kernel: [    0.355120] cpuidle: using governor ladder
Sep 19 10:16:35 david-pc kernel: [    0.355126] cpuidle: using governor menu
Sep 19 10:16:35 david-pc kernel: [    0.355743] TCP cubic registered
Sep 19 10:16:35 david-pc kernel: [    0.355928] NET: Registered protocol family 10
Sep 19 10:16:35 david-pc kernel: [    0.356567] lo: Disabled Privacy Extensions
Sep 19 10:16:35 david-pc kernel: [    0.356998] NET: Registered protocol family 17
Sep 19 10:16:35 david-pc kernel: [    0.357072] Using IPI No-Shortcut mode
Sep 19 10:16:35 david-pc kernel: [    0.357241] registered taskstats version 1
Sep 19 10:16:35 david-pc kernel: [    0.357441]   Magic number: 10:225:275
Sep 19 10:16:35 david-pc kernel: [    0.357478] tty tty12: hash matches
Sep 19 10:16:35 david-pc kernel: [    0.357522] rtc_cmos 00:03: setting system clock to 2010-09-19 10:16:23 UTC (1284891383)
Sep 19 10:16:35 david-pc kernel: [    0.357526] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 19 10:16:35 david-pc kernel: [    0.357528] EDD information not available.
Sep 19 10:16:35 david-pc kernel: [    0.506610] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
Sep 19 10:16:35 david-pc kernel: [    0.506615] ata1.00: 488397168 sectors, multi 16: LBA48 
Sep 19 10:16:35 david-pc kernel: [    0.506984] ata1.01: ATA-6: WDC WD3000JB-00KFA0, 08.05J08, max UDMA/100
Sep 19 10:16:35 david-pc kernel: [    0.506989] ata1.01: 586072368 sectors, multi 16: LBA48 
Sep 19 10:16:35 david-pc kernel: [    0.515712] ata2.00: ATAPI: TSST CDW/DVD TS-H492A, HP02, max UDMA/33
Sep 19 10:16:35 david-pc kernel: [    0.515762] ata2.01: ATAPI: DVD RW DRU-820A, 1.0b, max UDMA/66
Sep 19 10:16:35 david-pc kernel: [    0.515795] ata2.01: limited to UDMA/33 due to 40-wire cable
Sep 19 10:16:35 david-pc kernel: [    0.523543] ata1.00: configured for UDMA/100
Sep 19 10:16:35 david-pc kernel: [    0.539318] ata1.01: configured for UDMA/100
Sep 19 10:16:35 david-pc kernel: [    0.686579] usb 1-1: new high speed USB device using ehci_hcd and address 2
Sep 19 10:16:35 david-pc kernel: [    0.686958] ata2.00: configured for UDMA/33
Sep 19 10:16:35 david-pc kernel: [    0.703225] ata2.01: configured for UDMA/33
Sep 19 10:16:35 david-pc kernel: [    0.803081] Freeing initrd memory: 7778k freed
Sep 19 10:16:35 david-pc kernel: [    0.902382] isapnp: No Plug & Play device found
Sep 19 10:16:35 david-pc kernel: [    0.902622] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
Sep 19 10:16:35 david-pc kernel: [    0.902899] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 19 10:16:35 david-pc kernel: [    0.903122] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Sep 19 10:16:35 david-pc kernel: [    0.903210] sd 0:0:0:0: [sda] Write Protect is off
Sep 19 10:16:35 david-pc kernel: [    0.903254] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 10:16:35 david-pc kernel: [    0.903510]  sda: sda1 sda2
Sep 19 10:16:35 david-pc kernel: [    0.905956] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3000JB-00K 08.0 PQ: 0 ANSI: 5
Sep 19 10:16:35 david-pc kernel: [    0.906179] sd 0:0:1:0: Attached scsi generic sg1 type 0
Sep 19 10:16:35 david-pc kernel: [    0.906701] sd 0:0:1:0: [sdb] 586072368 512-byte logical blocks: (300 GB/279 GiB)
Sep 19 10:16:35 david-pc kernel: [    0.906864] scsi 1:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-H492A HP02 PQ: 0 ANSI: 5
Sep 19 10:16:35 david-pc kernel: [    0.907232] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 19 10:16:35 david-pc kernel: [    0.907296] sd 0:0:1:0: [sdb] Write Protect is off
Sep 19 10:16:35 david-pc kernel: [    0.907437] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 10:16:35 david-pc kernel: [    0.907982]  sdb:sr0: scsi3-mmc drive: 5x/48x writer cd/rw xa/form2 cdda tray
Sep 19 10:16:35 david-pc kernel: [    0.909200] Uniform CD-ROM driver Revision: 3.20
Sep 19 10:16:35 david-pc kernel: [    0.909459] sr 1:0:0:0: Attached scsi generic sg2 type 5
Sep 19 10:16:35 david-pc kernel: [    0.910849] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ: 0 ANSI: 5
Sep 19 10:16:35 david-pc kernel: [    0.915269] usb 1-1: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    0.915436] hub 1-1:1.0: USB hub found
Sep 19 10:16:35 david-pc kernel: [    0.915520] hub 1-1:1.0: 4 ports detected
Sep 19 10:16:35 david-pc kernel: [    0.917111]  sdb1 sdb2 <sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 19 10:16:35 david-pc kernel: [    0.918515] sr 1:0:1:0: Attached scsi generic sg3 type 5
Sep 19 10:16:35 david-pc kernel: [    0.938584]  sdb5 >
Sep 19 10:16:35 david-pc kernel: [    0.939068] sd 0:0:1:0: [sdb] Attached SCSI disk
Sep 19 10:16:35 david-pc kernel: [    0.939088] Freeing unused kernel memory: 660k freed
Sep 19 10:16:35 david-pc kernel: [    0.940032] Write protecting the kernel text: 4680k
Sep 19 10:16:35 david-pc kernel: [    0.940067] Write protecting the kernel read-only data: 1844k
Sep 19 10:16:35 david-pc kernel: [    0.978439] udev: starting version 151
Sep 19 10:16:35 david-pc kernel: [    1.138835] usb 1-4: new high speed USB device using ehci_hcd and address 5
Sep 19 10:16:35 david-pc kernel: [    1.207704] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 19 10:16:35 david-pc kernel: [    1.207742] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Sep 19 10:16:35 david-pc kernel: [    1.240766] 8139too Fast Ethernet driver 0.9.28
Sep 19 10:16:35 david-pc kernel: [    1.240827] 8139too 0000:01:0c.0: PCI->APIC IRQ transform: INT A -> IRQ 23
Sep 19 10:16:35 david-pc kernel: [    1.242149] eth0: RealTek RTL8139 at 0xc800, 00:11:09:72:9c:4a, IRQ 23
Sep 19 10:16:35 david-pc kernel: [    1.272517] usb 1-4: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    1.318003] Initializing USB Mass Storage driver...
Sep 19 10:16:35 david-pc kernel: [    1.318191] scsi2 : SCSI emulation for USB Mass Storage devices
Sep 19 10:16:35 david-pc kernel: [    1.318521] usbcore: registered new interface driver usb-storage
Sep 19 10:16:35 david-pc kernel: [    1.318526] USB Mass Storage support registered.
Sep 19 10:16:35 david-pc kernel: [    1.527522] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Sep 19 10:16:35 david-pc kernel: [    1.527531] EXT4-fs (sdb1): write access will be enabled during recovery
Sep 19 10:16:35 david-pc kernel: [    1.622795] usb 2-2: new low speed USB device using uhci_hcd and address 2
Sep 19 10:16:35 david-pc kernel: [    1.758884] EXT4-fs (sdb1): recovery complete
Sep 19 10:16:35 david-pc kernel: [    1.759388] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Sep 19 10:16:35 david-pc kernel: [    1.807333] usb 2-2: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    2.046804] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 19 10:16:35 david-pc kernel: [    2.246657] usb 3-1: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    2.486831] usb 4-1: new full speed USB device using uhci_hcd and address 2
Sep 19 10:16:35 david-pc kernel: [    2.664997] usb 4-1: configuration #1 chosen from 1 choice
Sep 19 10:16:35 david-pc kernel: [    2.668095] scsi3 : SCSI emulation for USB Mass Storage devices
Sep 19 10:16:35 david-pc kernel: [    6.319706] scsi 2:0:0:0: Direct-Access     HP       Photosmart D110  1.00 PQ: 0 ANSI: 5
Sep 19 10:16:35 david-pc kernel: [    6.320514] sd 2:0:0:0: Attached scsi generic sg4 type 0
Sep 19 10:16:35 david-pc kernel: [    6.322178] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Sep 19 10:16:35 david-pc kernel: [    7.671938] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Sep 19 10:16:35 david-pc kernel: [    7.674934] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Sep 19 10:16:35 david-pc kernel: [    7.677940] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Sep 19 10:16:35 david-pc kernel: [    7.680932] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Sep 19 10:16:35 david-pc kernel: [    7.681740] sd 3:0:0:0: Attached scsi generic sg5 type 0
Sep 19 10:16:35 david-pc kernel: [    7.681995] sd 3:0:0:1: Attached scsi generic sg6 type 0
Sep 19 10:16:35 david-pc kernel: [    7.682234] sd 3:0:0:2: Attached scsi generic sg7 type 0
Sep 19 10:16:35 david-pc kernel: [    7.682469] sd 3:0:0:3: Attached scsi generic sg8 type 0
Sep 19 10:16:35 david-pc kernel: [    7.859898] sd 3:0:0:0: [sdd] Attached SCSI removable disk
Sep 19 10:16:35 david-pc kernel: [    7.864885] sd 3:0:0:1: [sde] Attached SCSI removable disk
Sep 19 10:16:35 david-pc kernel: [    7.869888] sd 3:0:0:2: [sdf] Attached SCSI removable disk
Sep 19 10:16:35 david-pc kernel: [    7.874883] sd 3:0:0:3: [sdg] Attached SCSI removable disk
Sep 19 10:16:35 david-pc kernel: [   10.157508] udev: starting version 151
Sep 19 10:16:35 david-pc kernel: [   10.211320] Adding 2980856k swap on /dev/sdb5.  Priority:-1 extents:1 across:2980856k 
Sep 19 10:16:35 david-pc kernel: [   10.321186] lp: driver loaded but no devices found
Sep 19 10:16:35 david-pc kernel: [   10.341485] Linux agpgart interface v0.103
Sep 19 10:16:35 david-pc kernel: [   10.361040] vga16fb: mapped to 0xc00a0000
Sep 19 10:16:35 david-pc kernel: [   10.361146] fb0: VGA16 VGA frame buffer device
Sep 19 10:16:35 david-pc kernel: [   10.523247] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 19 10:16:35 david-pc kernel: [   10.523326] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Sep 19 10:16:35 david-pc kernel: [   10.523637] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
Sep 19 10:16:35 david-pc kernel: [   10.575528] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
Sep 19 10:16:35 david-pc kernel: [   10.594611] intel_rng: FWH not detected
Sep 19 10:16:35 david-pc kernel: [   10.600607] usbcore: registered new interface driver hiddev
Sep 19 10:16:35 david-pc kernel: [   10.863196] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8D11
Sep 19 10:16:35 david-pc kernel: [   10.863234] usbcore: registered new interface driver usblp
Sep 19 10:16:35 david-pc kernel: [   10.989151] generic-usb 0003:051D:0002.0003: hiddev96,hidraw0: USB HID v1.10 Device [APC Back-UPS NS 600 FW:818.w1 .D USB FW:w1 ] on usb-0000:00:1d.1-1/input0
Sep 19 10:16:35 david-pc kernel: [   10.989209] usbcore: registered new interface driver usbhid
Sep 19 10:16:35 david-pc kernel: [   10.989214] usbhid: v2.6:USB HID core driver
Sep 19 10:16:35 david-pc kernel: [   11.191960] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input1
Sep 19 10:16:35 david-pc kernel: [   11.192158] microsoft 0003:045E:00F9.0001: input,hidraw1: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2/input0
Sep 19 10:16:35 david-pc kernel: [   11.282496] microsoft 0003:045E:00F9.0002: fixing up Microsoft Wireless Receiver Model 1028 report descriptor
Sep 19 10:16:35 david-pc kernel: [   11.332976] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input2
Sep 19 10:16:35 david-pc kernel: [   11.333187] microsoft 0003:045E:00F9.0002: input,hidraw2: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2/input1
Sep 19 10:16:35 david-pc kernel: [   11.611185] Console: switching to colour frame buffer device 80x30
Sep 19 10:16:35 david-pc kernel: [   11.703526] Intel ICH 0000:00:1f.5: PCI->APIC IRQ transform: INT B -> IRQ 17
Sep 19 10:16:35 david-pc kernel: [   11.706639] type=1505 audit(1284905794.845:2):  operation="profile_load" pid=555 name="/sbin/dhclient3"
Sep 19 10:16:35 david-pc kernel: [   11.707449] type=1505 audit(1284905794.849:3):  operation="profile_load" pid=555 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 19 10:16:35 david-pc kernel: [   11.707840] type=1505 audit(1284905794.849:4):  operation="profile_load" pid=555 name="/usr/lib/connman/scripts/dhclient-script"
Sep 19 10:16:35 david-pc kernel: [   12.059139] intel8x0_measure_ac97_clock: measured 53554 usecs (2581 samples)
Sep 19 10:16:35 david-pc kernel: [   12.059144] intel8x0: clocking to 48000
Sep 19 10:16:35 david-pc kernel: [   12.109441] type=1505 audit(1284905795.249:5):  operation="profile_load" pid=656 name="/usr/share/gdm/guest-session/Xsession"
Sep 19 10:16:35 david-pc kernel: [   12.150886] type=1505 audit(1284905795.289:6):  operation="profile_replace" pid=660 name="/sbin/dhclient3"
Sep 19 10:16:35 david-pc kernel: [   12.152171] type=1505 audit(1284905795.293:7):  operation="profile_replace" pid=660 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 19 10:16:35 david-pc kernel: [   12.152577] type=1505 audit(1284905795.293:8):  operation="profile_replace" pid=660 name="/usr/lib/connman/scripts/dhclient-script"
Sep 19 10:16:35 david-pc kernel: [   12.206929] type=1505 audit(1284905795.345:9):  operation="profile_load" pid=665 name="/usr/bin/evince"
Sep 19 10:16:35 david-pc kernel: [   12.291834] type=1505 audit(1284905795.433:10):  operation="profile_load" pid=665 name="/usr/bin/evince-previewer"
Sep 19 10:16:35 david-pc kernel: [   12.308038] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep 19 10:16:35 david-pc kernel: [   12.318141] type=1505 audit(1284905795.457:11):  operation="profile_load" pid=665 name="/usr/bin/evince-thumbnailer"
Sep 19 10:16:36 david-pc kernel: [   12.997312] ppdev: user-space parallel port driver
Sep 19 10:16:37 david-pc kernel: [   14.208331] usb 1-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Sep 19 10:16:39 david-pc pulseaudio[1109]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:16:39 david-pc pulseaudio[1109]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:16:41 david-pc python: hp-systray[1120]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Sep 19 10:17:05 david-pc pulseaudio[1351]: pid.c: Stale PID file, overwriting.
Sep 19 10:17:05 david-pc pulseaudio[1351]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-mkvJWIIOYq: Connection refused
Sep 19 10:17:09 david-pc pulseaudio[1401]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:17:09 david-pc pulseaudio[1401]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:17:12 david-pc pulseaudio[1401]: alsa-util.c: Unable to set sw params: Permission denied
Sep 19 10:18:27 david-pc kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 19 10:18:27 david-pc rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="588" x-info="http://www.rsyslog.com"] (re)start
Sep 19 10:18:27 david-pc rsyslogd: rsyslogd's groupid changed to 103
Sep 19 10:18:27 david-pc rsyslogd: rsyslogd's userid changed to 101
Sep 19 10:18:27 david-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 19 10:18:27 david-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 19 10:18:27 david-pc kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 (Ubuntu 2.6.32-24.43-generic 2.6.32.15+drm33.5)
Sep 19 10:18:27 david-pc kernel: [    0.000000] KERNEL supported cpus:
Sep 19 10:18:27 david-pc kernel: [    0.000000]   Intel GenuineIntel
Sep 19 10:18:27 david-pc kernel: [    0.000000]   AMD AuthenticAMD
Sep 19 10:18:27 david-pc kernel: [    0.000000]   NSC Geode by NSC
Sep 19 10:18:27 david-pc kernel: [    0.000000]   Cyrix CyrixInstead
Sep 19 10:18:27 david-pc kernel: [    0.000000]   Centaur CentaurHauls
Sep 19 10:18:27 david-pc kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 19 10:18:27 david-pc kernel: [    0.000000]   Transmeta TransmetaCPU
Sep 19 10:18:27 david-pc kernel: [    0.000000]   UMC UMC UMC UMC
Sep 19 10:18:27 david-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7f0000 (usable)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 000000003f7f3000 - 000000003f800000 (ACPI data)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000] DMI 2.3 present.
Sep 19 10:18:27 david-pc kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Sep 19 10:18:27 david-pc kernel: [    0.000000] last_pfn = 0x3f7f0 max_arch_pfn = 0x100000
Sep 19 10:18:27 david-pc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep 19 10:18:27 david-pc kernel: [    0.000000] Scanning 0 areas for low memory corruption
Sep 19 10:18:27 david-pc kernel: [    0.000000] modified physical RAM map:
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 0000000000100000 - 000000003f7f0000 (usable)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 000000003f7f3000 - 000000003f800000 (ACPI data)
Sep 19 10:18:27 david-pc kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Sep 19 10:18:27 david-pc kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Sep 19 10:18:27 david-pc kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Sep 19 10:18:27 david-pc kernel: [    0.000000] RAMDISK: 2f29b000 - 2fa33bf0
Sep 19 10:18:27 david-pc kernel: [    0.000000] ACPI Error: A valid RSDP was not found (20090903/tbxfroot-219)
Sep 19 10:18:27 david-pc kernel: [    0.000000] 127MB HIGHMEM available.
Sep 19 10:18:27 david-pc kernel: [    0.000000] 887MB LOWMEM available.
Sep 19 10:18:27 david-pc kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Sep 19 10:18:27 david-pc kernel: [    0.000000]   low ram: 0 - 377fe000
Sep 19 10:18:27 david-pc kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Sep 19 10:18:27 david-pc kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Sep 19 10:18:27 david-pc kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #4 [002f29b000 - 002fa33bf0]          RAMDISK ==> [002f29b000 - 002fa33bf0]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #6 [00008de000 - 00008e1194]              BRK ==> [00008de000 - 00008e1194]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Sep 19 10:18:27 david-pc kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Sep 19 10:18:27 david-pc kernel: [    0.000000] found SMP MP-table at [c00f5f00] f5f00
Sep 19 10:18:27 david-pc kernel: [    0.000000] Zone PFN ranges:
Sep 19 10:18:27 david-pc kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 19 10:18:27 david-pc kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Sep 19 10:18:27 david-pc kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f7f0
Sep 19 10:18:27 david-pc kernel: [    0.000000] Movable zone start PFN for each node
Sep 19 10:18:27 david-pc kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep 19 10:18:27 david-pc kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep 19 10:18:27 david-pc kernel: [    0.000000]     0: 0x00000100 -> 0x0003f7f0
Sep 19 10:18:27 david-pc kernel: [    0.000000] Using APIC driver default
Sep 19 10:18:27 david-pc kernel: [    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Sep 19 10:18:27 david-pc kernel: [    0.000000]     Virtual Wire compatibility mode.
Sep 19 10:18:27 david-pc kernel: [    0.000000] MPTABLE: OEM ID: OEM00000
Sep 19 10:18:27 david-pc kernel: [    0.000000] MPTABLE: Product ID: PROD00000000
Sep 19 10:18:27 david-pc kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Sep 19 10:18:27 david-pc kernel: [    0.000000] Processor #0 (Bootup-CPU)
Sep 19 10:18:27 david-pc kernel: [    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
Sep 19 10:18:27 david-pc kernel: [    0.000000] Processors: 1
Sep 19 10:18:27 david-pc kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Sep 19 10:18:27 david-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 10:18:27 david-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Sep 19 10:18:27 david-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Sep 19 10:18:27 david-pc kernel: [    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf400000)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 19 10:18:27 david-pc kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Sep 19 10:18:27 david-pc kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
Sep 19 10:18:27 david-pc kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
Sep 19 10:18:27 david-pc kernel: [    0.000000] pcpu-alloc: [0] 0 
Sep 19 10:18:27 david-pc kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257935
Sep 19 10:18:27 david-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=444cbddf-4be0-403f-8197-ad0432f5e984 ro quiet splash
Sep 19 10:18:27 david-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 19 10:18:27 david-pc kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 19 10:18:27 david-pc kernel: [    0.000000] Initializing CPU#0
Sep 19 10:18:27 david-pc kernel: [    0.000000] allocated 5201280 bytes of page_cgroup
Sep 19 10:18:27 david-pc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep 19 10:18:27 david-pc kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f7f0)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Memory: 1009368k/1040320k available (4679k kernel code, 29952k reserved, 2124k data, 660k init, 131016k highmem)
Sep 19 10:18:27 david-pc kernel: [    0.000000] virtual kernel memory layout:
Sep 19 10:18:27 david-pc kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Sep 19 10:18:27 david-pc kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 19 10:18:27 david-pc kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Sep 19 10:18:27 david-pc kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Sep 19 10:18:27 david-pc kernel: [    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
Sep 19 10:18:27 david-pc kernel: [    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
Sep 19 10:18:27 david-pc kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
Sep 19 10:18:27 david-pc kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep 19 10:18:27 david-pc kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Sep 19 10:18:27 david-pc kernel: [    0.000000] Hierarchical RCU implementation.
Sep 19 10:18:27 david-pc kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Sep 19 10:18:27 david-pc kernel: [    0.000000] Console: colour VGA+ 80x25
Sep 19 10:18:27 david-pc kernel: [    0.000000] console [tty0] enabled
Sep 19 10:18:27 david-pc kernel: [    0.000000] Fast TSC calibration using PIT
Sep 19 10:18:27 david-pc kernel: [    0.000000] Detected 2932.508 MHz processor.
Sep 19 10:18:27 david-pc kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5865.01 BogoMIPS (lpj=11730032)
Sep 19 10:18:27 david-pc kernel: [    0.004034] Security Framework initialized
Sep 19 10:18:27 david-pc kernel: [    0.004072] AppArmor: AppArmor initialized
Sep 19 10:18:27 david-pc kernel: [    0.004083] Mount-cache hash table entries: 512
Sep 19 10:18:27 david-pc kernel: [    0.004264] Initializing cgroup subsys ns
Sep 19 10:18:27 david-pc kernel: [    0.004272] Initializing cgroup subsys cpuacct
Sep 19 10:18:27 david-pc kernel: [    0.004278] Initializing cgroup subsys memory
Sep 19 10:18:27 david-pc kernel: [    0.004290] Initializing cgroup subsys devices
Sep 19 10:18:27 david-pc kernel: [    0.004294] Initializing cgroup subsys freezer
Sep 19 10:18:27 david-pc kernel: [    0.004297] Initializing cgroup subsys net_cls
Sep 19 10:18:27 david-pc kernel: [    0.004332] CPU: Trace cache: 12K uops, L1 D cache: 16K
Sep 19 10:18:27 david-pc kernel: [    0.004336] CPU: L2 cache: 256K
Sep 19 10:18:27 david-pc kernel: [    0.004341] CPU: Hyper-Threading is disabled
Sep 19 10:18:27 david-pc kernel: [    0.004346] mce: CPU supports 4 MCE banks
Sep 19 10:18:27 david-pc kernel: [    0.004362] CPU0: Thermal monitoring enabled (TM1)
Sep 19 10:18:27 david-pc kernel: [    0.004370] using mwait in idle threads.
Sep 19 10:18:27 david-pc kernel: [    0.004380] Performance Events: no PMU driver, software events only.
Sep 19 10:18:27 david-pc kernel: [    0.004390] Checking 'hlt' instruction... OK.
Sep 19 10:18:27 david-pc kernel: [    0.021212] SMP alternatives: switching to UP code
Sep 19 10:18:27 david-pc kernel: [    0.034202] Freeing SMP alternatives: 19k freed
Sep 19 10:18:27 david-pc kernel: [    0.034234] ftrace: converting mcount calls to 0f 1f 44 00 00
Sep 19 10:18:27 david-pc kernel: [    0.034245] ftrace: allocating 21780 entries in 43 pages
Sep 19 10:18:27 david-pc kernel: [    0.036136] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 19 10:18:27 david-pc kernel: [    0.036198] ExtINT not setup in hardware but reported by MP table
Sep 19 10:18:27 david-pc kernel: [    0.036467] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Sep 19 10:18:27 david-pc kernel: [    0.076371] CPU0: Intel(R) Celeron(R) CPU 2.93GHz stepping 04
Sep 19 10:18:27 david-pc kernel: [    0.184270] Brought up 1 CPUs
Sep 19 10:18:27 david-pc kernel: [    0.184276] Total of 1 processors activated (5865.01 BogoMIPS).
Sep 19 10:18:27 david-pc kernel: [    0.184561] devtmpfs: initialized
Sep 19 10:18:27 david-pc kernel: [    0.185141] regulator: core version 0.5
Sep 19 10:18:27 david-pc kernel: [    0.185169] Time: 10:18:16  Date: 09/19/10
Sep 19 10:18:27 david-pc kernel: [    0.185247] NET: Registered protocol family 16
Sep 19 10:18:27 david-pc kernel: [    0.185430] EISA bus registered
Sep 19 10:18:27 david-pc kernel: [    0.213108] PCI: PCI BIOS revision 2.10 entry at 0xfb9b0, last bus=1
Sep 19 10:18:27 david-pc kernel: [    0.213111] PCI: Using configuration type 1 for base access
Sep 19 10:18:27 david-pc kernel: [    0.214465] bio: create slab <bio-0> at 0
Sep 19 10:18:27 david-pc kernel: [    0.214564] ACPI: Interpreter disabled.
Sep 19 10:18:27 david-pc kernel: [    0.214659] vgaarb: loaded
Sep 19 10:18:27 david-pc kernel: [    0.214837] SCSI subsystem initialized
Sep 19 10:18:27 david-pc kernel: [    0.215059] usbcore: registered new interface driver usbfs
Sep 19 10:18:27 david-pc kernel: [    0.215077] usbcore: registered new interface driver hub
Sep 19 10:18:27 david-pc kernel: [    0.215126] usbcore: registered new device driver usb
Sep 19 10:18:27 david-pc kernel: [    0.215314] PCI: Probing PCI hardware
Sep 19 10:18:27 david-pc kernel: [    0.215812] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Sep 19 10:18:27 david-pc kernel: [    0.215818] pci 0000:00:1d.7: PME# disabled
Sep 19 10:18:27 david-pc kernel: [    0.215873] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Sep 19 10:18:27 david-pc kernel: [    0.215875] * this clock source is slow. If you are sure your timer does not have
Sep 19 10:18:27 david-pc kernel: [    0.215877] * this bug, please use "acpi_pm_good" to disable the workaround
Sep 19 10:18:27 david-pc kernel: [    0.215924] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Sep 19 10:18:27 david-pc kernel: [    0.215929] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Sep 19 10:18:27 david-pc kernel: [    0.216173] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Sep 19 10:18:27 david-pc kernel: [    0.216178] pci 0000:00:1f.5: PME# disabled
Sep 19 10:18:27 david-pc kernel: [    0.216293] pci 0000:01:0b.0: PME# supported from D2 D3hot D3cold
Sep 19 10:18:27 david-pc kernel: [    0.216298] pci 0000:01:0b.0: PME# disabled
Sep 19 10:18:27 david-pc kernel: [    0.216390] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
Sep 19 10:18:27 david-pc kernel: [    0.216395] pci 0000:01:0c.0: PME# disabled
Sep 19 10:18:27 david-pc kernel: [    0.216426] pci 0000:00:1e.0: transparent bridge
Sep 19 10:18:27 david-pc kernel: [    0.216506] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Sep 19 10:18:27 david-pc kernel: [    0.216859] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:24c0]
Sep 19 10:18:27 david-pc kernel: [    0.217061] NetLabel: Initializing
Sep 19 10:18:27 david-pc kernel: [    0.217065] NetLabel:  domain hash size = 128
Sep 19 10:18:27 david-pc kernel: [    0.217067] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 19 10:18:27 david-pc kernel: [    0.217085] NetLabel:  unlabeled traffic allowed by default
Sep 19 10:18:27 david-pc kernel: [    0.217162] Switching to clocksource tsc
Sep 19 10:18:27 david-pc kernel: [    0.219775] AppArmor: AppArmor Filesystem Enabled
Sep 19 10:18:27 david-pc kernel: [    0.219785] pnp: PnP ACPI: disabled
Sep 19 10:18:27 david-pc kernel: [    0.219792] PnPBIOS: Scanning system for PnP BIOS support...
Sep 19 10:18:27 david-pc kernel: [    0.219842] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc3b0
Sep 19 10:18:27 david-pc kernel: [    0.219846] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc3e0, dseg 0xf0000
Sep 19 10:18:27 david-pc kernel: [    0.219999] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:08: iomem range 0xffb00000-0xffb7ffff has been reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:08: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:08: iomem range 0xfee00000-0xfee0ffff has been reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:08: iomem range 0x100000-0xffffff could not be reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:09: iomem range 0xf8000-0xfffff could not be reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] system 00:09: iomem range 0xcc000-0xcffff has been reserved
Sep 19 10:18:27 david-pc kernel: [    0.219999] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Sep 19 10:18:27 david-pc kernel: [    0.219999] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Sep 19 10:18:27 david-pc kernel: [    0.219999] pci 0000:00:1e.0:   MEM window: 0xec000000-0xedffffff
Sep 19 10:18:27 david-pc kernel: [    0.219999] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x400fffff
Sep 19 10:18:27 david-pc kernel: [    0.219999] NET: Registered protocol family 2
Sep 19 10:18:27 david-pc kernel: [    0.219999] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.220298] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.221545] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.222257] TCP: Hash tables configured (established 131072 bind 65536)
Sep 19 10:18:27 david-pc kernel: [    0.222264] TCP reno registered
Sep 19 10:18:27 david-pc kernel: [    0.222476] NET: Registered protocol family 1
Sep 19 10:18:27 david-pc kernel: [    0.222924] cpufreq-nforce2: No nForce2 chipset.
Sep 19 10:18:27 david-pc kernel: [    0.222966] Scanning for low memory corruption every 60 seconds
Sep 19 10:18:27 david-pc kernel: [    0.223123] audit: initializing netlink socket (disabled)
Sep 19 10:18:27 david-pc kernel: [    0.223143] type=2000 audit(1284891496.222:1): initialized
Sep 19 10:18:27 david-pc kernel: [    0.232485] Trying to unpack rootfs image as initramfs...
Sep 19 10:18:27 david-pc kernel: [    0.243257] highmem bounce pool size: 64 pages
Sep 19 10:18:27 david-pc kernel: [    0.243266] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep 19 10:18:27 david-pc kernel: [    0.251017] VFS: Disk quotas dquot_6.5.2
Sep 19 10:18:27 david-pc kernel: [    0.251155] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 19 10:18:27 david-pc kernel: [    0.252049] fuse init (API version 7.13)
Sep 19 10:18:27 david-pc kernel: [    0.252198] msgmni has been set to 1716
Sep 19 10:18:27 david-pc kernel: [    0.252567] alg: No test for stdrng (krng)
Sep 19 10:18:27 david-pc kernel: [    0.252686] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep 19 10:18:27 david-pc kernel: [    0.252691] io scheduler noop registered
Sep 19 10:18:27 david-pc kernel: [    0.252694] io scheduler anticipatory registered
Sep 19 10:18:27 david-pc kernel: [    0.252696] io scheduler deadline registered
Sep 19 10:18:27 david-pc kernel: [    0.252748] io scheduler cfq registered (default)
Sep 19 10:18:27 david-pc kernel: [    0.252889] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 19 10:18:27 david-pc kernel: [    0.252923] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 19 10:18:27 david-pc kernel: [    0.261178] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Sep 19 10:18:27 david-pc kernel: [    0.261294] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 19 10:18:27 david-pc kernel: [    0.261856] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 19 10:18:27 david-pc kernel: [    0.262836] isapnp: Scanning for PnP cards...
Sep 19 10:18:27 david-pc kernel: [    0.268949] brd: module loaded
Sep 19 10:18:27 david-pc kernel: [    0.269622] loop: module loaded
Sep 19 10:18:27 david-pc kernel: [    0.269794] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 19 10:18:27 david-pc kernel: [    0.269986] ata_piix 0000:00:1f.1: PCI->APIC IRQ transform: INT A -> IRQ 16
Sep 19 10:18:27 david-pc kernel: [    0.270202] scsi0 : ata_piix
Sep 19 10:18:27 david-pc kernel: [    0.274842] scsi1 : ata_piix
Sep 19 10:18:27 david-pc kernel: [    0.274939] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Sep 19 10:18:27 david-pc kernel: [    0.274944] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Sep 19 10:18:27 david-pc kernel: [    0.275452] Fixed MDIO Bus: probed
Sep 19 10:18:27 david-pc kernel: [    0.275507] PPP generic driver version 2.4.2
Sep 19 10:18:27 david-pc kernel: [    0.275616] tun: Universal TUN/TAP device driver, 1.6
Sep 19 10:18:27 david-pc kernel: [    0.275620] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 19 10:18:27 david-pc kernel: [    0.275771] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 19 10:18:27 david-pc kernel: [    0.275817] ehci_hcd 0000:00:1d.7: PCI->APIC IRQ transform: INT D -> IRQ 23
Sep 19 10:18:27 david-pc kernel: [    0.275850] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 19 10:18:27 david-pc kernel: [    0.275924] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Sep 19 10:18:27 david-pc kernel: [    0.323782] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee080000
Sep 19 10:18:27 david-pc kernel: [    0.342810] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Sep 19 10:18:27 david-pc kernel: [    0.343024] usb usb1: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    0.343068] hub 1-0:1.0: USB hub found
Sep 19 10:18:27 david-pc kernel: [    0.343085] hub 1-0:1.0: 6 ports detected
Sep 19 10:18:27 david-pc kernel: [    0.343180] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 19 10:18:27 david-pc kernel: [    0.343205] uhci_hcd: USB Universal Host Controller Interface driver
Sep 19 10:18:27 david-pc kernel: [    0.343267] uhci_hcd 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 16
Sep 19 10:18:27 david-pc kernel: [    0.343284] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 19 10:18:27 david-pc kernel: [    0.343371] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Sep 19 10:18:27 david-pc kernel: [    0.343409] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Sep 19 10:18:27 david-pc kernel: [    0.343568] usb usb2: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    0.343611] hub 2-0:1.0: USB hub found
Sep 19 10:18:27 david-pc kernel: [    0.343626] hub 2-0:1.0: 2 ports detected
Sep 19 10:18:27 david-pc kernel: [    0.343699] uhci_hcd 0000:00:1d.1: PCI->APIC IRQ transform: INT B -> IRQ 19
Sep 19 10:18:27 david-pc kernel: [    0.343714] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 19 10:18:27 david-pc kernel: [    0.343785] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Sep 19 10:18:27 david-pc kernel: [    0.343820] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Sep 19 10:18:27 david-pc kernel: [    0.343970] usb usb3: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    0.344009] hub 3-0:1.0: USB hub found
Sep 19 10:18:27 david-pc kernel: [    0.344021] hub 3-0:1.0: 2 ports detected
Sep 19 10:18:27 david-pc kernel: [    0.344090] uhci_hcd 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18
Sep 19 10:18:27 david-pc kernel: [    0.344104] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 19 10:18:27 david-pc kernel: [    0.344177] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Sep 19 10:18:27 david-pc kernel: [    0.344212] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Sep 19 10:18:27 david-pc kernel: [    0.344367] usb usb4: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    0.344407] hub 4-0:1.0: USB hub found
Sep 19 10:18:27 david-pc kernel: [    0.344421] hub 4-0:1.0: 2 ports detected
Sep 19 10:18:27 david-pc kernel: [    0.344560] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
Sep 19 10:18:27 david-pc kernel: [    0.344564] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep 19 10:18:27 david-pc kernel: [    0.345149] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 19 10:18:27 david-pc kernel: [    0.345381] mice: PS/2 mouse device common for all mice
Sep 19 10:18:27 david-pc kernel: [    0.351180] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Sep 19 10:18:27 david-pc kernel: [    0.351214] rtc0: alarms up to one day, 114 bytes nvram
Sep 19 10:18:27 david-pc kernel: [    0.351410] device-mapper: uevent: version 1.0.3
Sep 19 10:18:27 david-pc kernel: [    0.351654] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Sep 19 10:18:27 david-pc kernel: [    0.351766] device-mapper: multipath: version 1.1.0 loaded
Sep 19 10:18:27 david-pc kernel: [    0.351771] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 19 10:18:27 david-pc kernel: [    0.351971] EISA: Probing bus 0 at eisa.0
Sep 19 10:18:27 david-pc kernel: [    0.352010] EISA: Detected 0 cards.
Sep 19 10:18:27 david-pc kernel: [    0.355179] cpuidle: using governor ladder
Sep 19 10:18:27 david-pc kernel: [    0.355185] cpuidle: using governor menu
Sep 19 10:18:27 david-pc kernel: [    0.355809] TCP cubic registered
Sep 19 10:18:27 david-pc kernel: [    0.355998] NET: Registered protocol family 10
Sep 19 10:18:27 david-pc kernel: [    0.356636] lo: Disabled Privacy Extensions
Sep 19 10:18:27 david-pc kernel: [    0.357075] NET: Registered protocol family 17
Sep 19 10:18:27 david-pc kernel: [    0.357149] Using IPI No-Shortcut mode
Sep 19 10:18:27 david-pc kernel: [    0.357318] registered taskstats version 1
Sep 19 10:18:27 david-pc kernel: [    0.357519]   Magic number: 10:775:325
Sep 19 10:18:27 david-pc kernel: [    0.357598] rtc_cmos 00:03: setting system clock to 2010-09-19 10:18:16 UTC (1284891496)
Sep 19 10:18:27 david-pc kernel: [    0.357603] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 19 10:18:27 david-pc kernel: [    0.357605] EDD information not available.
Sep 19 10:18:27 david-pc kernel: [    0.506720] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
Sep 19 10:18:27 david-pc kernel: [    0.506726] ata1.00: 488397168 sectors, multi 16: LBA48 
Sep 19 10:18:27 david-pc kernel: [    0.507095] ata1.01: ATA-6: WDC WD3000JB-00KFA0, 08.05J08, max UDMA/100
Sep 19 10:18:27 david-pc kernel: [    0.507099] ata1.01: 586072368 sectors, multi 16: LBA48 
Sep 19 10:18:27 david-pc kernel: [    0.515843] ata2.00: ATAPI: TSST CDW/DVD TS-H492A, HP02, max UDMA/33
Sep 19 10:18:27 david-pc kernel: [    0.515892] ata2.01: ATAPI: DVD RW DRU-820A, 1.0b, max UDMA/66
Sep 19 10:18:27 david-pc kernel: [    0.515925] ata2.01: limited to UDMA/33 due to 40-wire cable
Sep 19 10:18:27 david-pc kernel: [    0.523284] ata1.00: configured for UDMA/100
Sep 19 10:18:27 david-pc kernel: [    0.539412] ata1.01: configured for UDMA/100
Sep 19 10:18:27 david-pc kernel: [    0.686622] usb 1-1: new high speed USB device using ehci_hcd and address 2
Sep 19 10:18:27 david-pc kernel: [    0.695088] ata2.00: configured for UDMA/33
Sep 19 10:18:27 david-pc kernel: [    0.711365] ata2.01: configured for UDMA/33
Sep 19 10:18:27 david-pc kernel: [    0.803105] Freeing initrd memory: 7778k freed
Sep 19 10:18:27 david-pc kernel: [    0.902330] isapnp: No Plug & Play device found
Sep 19 10:18:27 david-pc kernel: [    0.902572] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
Sep 19 10:18:27 david-pc kernel: [    0.902828] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 19 10:18:27 david-pc kernel: [    0.903089] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Sep 19 10:18:27 david-pc kernel: [    0.903180] sd 0:0:0:0: [sda] Write Protect is off
Sep 19 10:18:27 david-pc kernel: [    0.903225] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 10:18:27 david-pc kernel: [    0.903485]  sda: sda1 sda2
Sep 19 10:18:27 david-pc kernel: [    0.908402] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3000JB-00K 08.0 PQ: 0 ANSI: 5
Sep 19 10:18:27 david-pc kernel: [    0.908626] sd 0:0:1:0: Attached scsi generic sg1 type 0
Sep 19 10:18:27 david-pc kernel: [    0.909152] sd 0:0:1:0: [sdb] 586072368 512-byte logical blocks: (300 GB/279 GiB)
Sep 19 10:18:27 david-pc kernel: [    0.909285] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 19 10:18:27 david-pc kernel: [    0.909321] scsi 1:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-H492A HP02 PQ: 0 ANSI: 5
Sep 19 10:18:27 david-pc kernel: [    0.909687] sd 0:0:1:0: [sdb] Write Protect is off
Sep 19 10:18:27 david-pc kernel: [    0.909855] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 10:18:27 david-pc kernel: [    0.910398]  sdb:sr0: scsi3-mmc drive: 5x/48x writer cd/rw xa/form2 cdda tray
Sep 19 10:18:27 david-pc kernel: [    0.911640] Uniform CD-ROM driver Revision: 3.20
Sep 19 10:18:27 david-pc kernel: [    0.911907] sr 1:0:0:0: Attached scsi generic sg2 type 5
Sep 19 10:18:27 david-pc kernel: [    0.913394] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ: 0 ANSI: 5
Sep 19 10:18:27 david-pc kernel: [    0.915319] usb 1-1: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    0.915468] hub 1-1:1.0: USB hub found
Sep 19 10:18:27 david-pc kernel: [    0.915537] hub 1-1:1.0: 4 ports detected
Sep 19 10:18:27 david-pc kernel: [    0.921059] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 19 10:18:27 david-pc kernel: [    0.921327] sr 1:0:1:0: Attached scsi generic sg3 type 5
Sep 19 10:18:27 david-pc kernel: [    0.921901]  sdb1 sdb2 < sdb5 >
Sep 19 10:18:27 david-pc kernel: [    0.943830] sd 0:0:1:0: [sdb] Attached SCSI disk
Sep 19 10:18:27 david-pc kernel: [    0.943851] Freeing unused kernel memory: 660k freed
Sep 19 10:18:27 david-pc kernel: [    0.944793] Write protecting the kernel text: 4680k
Sep 19 10:18:27 david-pc kernel: [    0.944826] Write protecting the kernel read-only data: 1844k
Sep 19 10:18:27 david-pc kernel: [    0.983194] udev: starting version 151
Sep 19 10:18:27 david-pc kernel: [    1.138942] usb 1-4: new high speed USB device using ehci_hcd and address 5
Sep 19 10:18:27 david-pc kernel: [    1.214483] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 19 10:18:27 david-pc kernel: [    1.214519] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Sep 19 10:18:27 david-pc kernel: [    1.243274] 8139too Fast Ethernet driver 0.9.28
Sep 19 10:18:27 david-pc kernel: [    1.243332] 8139too 0000:01:0c.0: PCI->APIC IRQ transform: INT A -> IRQ 23
Sep 19 10:18:27 david-pc kernel: [    1.251806] eth0: RealTek RTL8139 at 0xc800, 00:11:09:72:9c:4a, IRQ 23
Sep 19 10:18:27 david-pc kernel: [    1.273411] usb 1-4: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    1.319456] Initializing USB Mass Storage driver...
Sep 19 10:18:27 david-pc kernel: [    1.319651] scsi2 : SCSI emulation for USB Mass Storage devices
Sep 19 10:18:27 david-pc kernel: [    1.319997] usbcore: registered new interface driver usb-storage
Sep 19 10:18:27 david-pc kernel: [    1.320003] USB Mass Storage support registered.
Sep 19 10:18:27 david-pc kernel: [    1.611786] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Sep 19 10:18:27 david-pc kernel: [    1.611796] EXT4-fs (sdb1): write access will be enabled during recovery
Sep 19 10:18:27 david-pc kernel: [    1.622972] usb 2-2: new low speed USB device using uhci_hcd and address 2
Sep 19 10:18:27 david-pc kernel: [    1.807582] usb 2-2: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    1.833174] EXT4-fs (sdb1): recovery complete
Sep 19 10:18:27 david-pc kernel: [    1.841771] usbcore: registered new interface driver hiddev
Sep 19 10:18:27 david-pc kernel: [    1.842742] usbcore: registered new interface driver usbhid
Sep 19 10:18:27 david-pc kernel: [    1.842966] usbhid: v2.6:USB HID core driver
Sep 19 10:18:27 david-pc kernel: [    1.843626] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Sep 19 10:18:27 david-pc kernel: [    1.867894] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input1
Sep 19 10:18:27 david-pc kernel: [    1.868063] microsoft 0003:045E:00F9.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2/input0
Sep 19 10:18:27 david-pc kernel: [    1.957393] microsoft 0003:045E:00F9.0002: fixing up Microsoft Wireless Receiver Model 1028 report descriptor
Sep 19 10:18:27 david-pc kernel: [    2.006643] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input2
Sep 19 10:18:27 david-pc kernel: [    2.006838] microsoft 0003:045E:00F9.0002: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2/input1
Sep 19 10:18:27 david-pc kernel: [    2.047033] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 19 10:18:27 david-pc kernel: [    2.244919] usb 3-1: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    2.636938] generic-usb 0003:051D:0002.0003: hiddev96,hidraw2: USB HID v1.10 Device [APC Back-UPS NS 600 FW:818.w1 .D USB FW:w1 ] on usb-0000:00:1d.1-1/input0
Sep 19 10:18:27 david-pc kernel: [    2.875164] usb 4-1: new full speed USB device using uhci_hcd and address 2
Sep 19 10:18:27 david-pc kernel: [    3.052287] usb 4-1: configuration #1 chosen from 1 choice
Sep 19 10:18:27 david-pc kernel: [    3.055338] scsi3 : SCSI emulation for USB Mass Storage devices
Sep 19 10:18:27 david-pc kernel: [    6.320497] scsi 2:0:0:0: Direct-Access     HP       Photosmart D110  1.00 PQ: 0 ANSI: 5
Sep 19 10:18:27 david-pc kernel: [    6.321292] sd 2:0:0:0: Attached scsi generic sg4 type 0
Sep 19 10:18:27 david-pc kernel: [    6.322967] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Sep 19 10:18:27 david-pc kernel: [    8.060817] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Sep 19 10:18:27 david-pc kernel: [    8.063866] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Sep 19 10:18:27 david-pc kernel: [    8.066819] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Sep 19 10:18:27 david-pc kernel: [    8.069815] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Sep 19 10:18:27 david-pc kernel: [    8.070754] sd 3:0:0:0: Attached scsi generic sg5 type 0
Sep 19 10:18:27 david-pc kernel: [    8.071021] sd 3:0:0:1: Attached scsi generic sg6 type 0
Sep 19 10:18:27 david-pc kernel: [    8.071256] sd 3:0:0:2: Attached scsi generic sg7 type 0
Sep 19 10:18:27 david-pc kernel: [    8.071485] sd 3:0:0:3: Attached scsi generic sg8 type 0
Sep 19 10:18:27 david-pc kernel: [    8.248793] sd 3:0:0:0: [sdd] Attached SCSI removable disk
Sep 19 10:18:27 david-pc kernel: [    8.253783] sd 3:0:0:1: [sde] Attached SCSI removable disk
Sep 19 10:18:27 david-pc kernel: [    8.258793] sd 3:0:0:2: [sdf] Attached SCSI removable disk
Sep 19 10:18:27 david-pc kernel: [    8.263780] sd 3:0:0:3: [sdg] Attached SCSI removable disk
Sep 19 10:18:27 david-pc kernel: [   10.072187] udev: starting version 151
Sep 19 10:18:27 david-pc kernel: [   10.112836] Adding 2980856k swap on /dev/sdb5.  Priority:-1 extents:1 across:2980856k 
Sep 19 10:18:27 david-pc kernel: [   10.225736] lp: driver loaded but no devices found
Sep 19 10:18:27 david-pc kernel: [   10.253393] Linux agpgart interface v0.103
Sep 19 10:18:27 david-pc kernel: [   10.360565] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Sep 19 10:18:27 david-pc kernel: [   10.360822] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
Sep 19 10:18:27 david-pc kernel: [   10.362913] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
Sep 19 10:18:27 david-pc kernel: [   10.391106] vga16fb: mapped to 0xc00a0000
Sep 19 10:18:27 david-pc kernel: [   10.391212] fb0: VGA16 VGA frame buffer device
Sep 19 10:18:27 david-pc kernel: [   10.395203] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 19 10:18:27 david-pc kernel: [   10.429908] intel_rng: FWH not detected
Sep 19 10:18:27 david-pc kernel: [   10.960925] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8D11
Sep 19 10:18:27 david-pc kernel: [   10.960962] usbcore: registered new interface driver usblp
Sep 19 10:18:27 david-pc kernel: [   11.480060] Console: switching to colour frame buffer device 80x30
Sep 19 10:18:27 david-pc kernel: [   11.532620] Intel ICH 0000:00:1f.5: PCI->APIC IRQ transform: INT B -> IRQ 17
Sep 19 10:18:27 david-pc kernel: [   11.554659] type=1505 audit(1284905907.694:2):  operation="profile_load" pid=556 name="/sbin/dhclient3"
Sep 19 10:18:27 david-pc kernel: [   11.555395] type=1505 audit(1284905907.694:3):  operation="profile_load" pid=556 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 19 10:18:27 david-pc kernel: [   11.555788] type=1505 audit(1284905907.694:4):  operation="profile_load" pid=556 name="/usr/lib/connman/scripts/dhclient-script"
Sep 19 10:18:28 david-pc kernel: [   11.896595] intel8x0_measure_ac97_clock: measured 55383 usecs (2668 samples)
Sep 19 10:18:28 david-pc kernel: [   11.896601] intel8x0: clocking to 48000
Sep 19 10:18:28 david-pc kernel: [   11.934796] type=1505 audit(1284905908.074:5):  operation="profile_load" pid=650 name="/usr/share/gdm/guest-session/Xsession"
Sep 19 10:18:28 david-pc kernel: [   11.953990] type=1505 audit(1284905908.094:6):  operation="profile_replace" pid=653 name="/sbin/dhclient3"
Sep 19 10:18:28 david-pc kernel: [   11.954749] type=1505 audit(1284905908.094:7):  operation="profile_replace" pid=653 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 19 10:18:28 david-pc kernel: [   11.955165] type=1505 audit(1284905908.094:8):  operation="profile_replace" pid=653 name="/usr/lib/connman/scripts/dhclient-script"
Sep 19 10:18:28 david-pc kernel: [   12.003445] type=1505 audit(1284905908.142:9):  operation="profile_load" pid=655 name="/usr/bin/evince"
Sep 19 10:18:28 david-pc kernel: [   12.084775] type=1505 audit(1284905908.226:10):  operation="profile_load" pid=655 name="/usr/bin/evince-previewer"
Sep 19 10:18:28 david-pc kernel: [   12.128018] type=1505 audit(1284905908.266:11):  operation="profile_load" pid=655 name="/usr/bin/evince-thumbnailer"
Sep 19 10:18:28 david-pc kernel: [   12.162327] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep 19 10:18:28 david-pc kernel: [   12.775180] ppdev: user-space parallel port driver
Sep 19 10:18:30 david-pc kernel: [   13.999781] usb 1-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Sep 19 10:18:32 david-pc pulseaudio[1053]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:18:32 david-pc pulseaudio[1053]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:18:35 david-pc python: hp-systray[1101]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Sep 19 10:18:59 david-pc pulseaudio[1345]: pid.c: Stale PID file, overwriting.
Sep 19 10:18:59 david-pc pulseaudio[1345]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-iHGHeLEm0i: Connection refused
Sep 19 10:19:03 david-pc pulseaudio[1394]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:19:47 david-pc kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 19 10:19:47 david-pc rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="592" x-info="http://www.rsyslog.com"] (re)start
Sep 19 10:19:47 david-pc rsyslogd: rsyslogd's groupid changed to 103
Sep 19 10:19:47 david-pc rsyslogd: rsyslogd's userid changed to 101
Sep 19 10:19:47 david-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 19 10:19:47 david-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 19 10:19:47 david-pc kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 (Ubuntu 2.6.32-24.43-generic 2.6.32.15+drm33.5)
Sep 19 10:19:47 david-pc kernel: [    0.000000] KERNEL supported cpus:
Sep 19 10:19:47 david-pc kernel: [    0.000000]   Intel GenuineIntel
Sep 19 10:19:47 david-pc kernel: [    0.000000]   AMD AuthenticAMD
Sep 19 10:19:47 david-pc kernel: [    0.000000]   NSC Geode by NSC
Sep 19 10:19:47 david-pc kernel: [    0.000000]   Cyrix CyrixInstead
Sep 19 10:19:47 david-pc kernel: [    0.000000]   Centaur CentaurHauls
Sep 19 10:19:47 david-pc kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 19 10:19:47 david-pc kernel: [    0.000000]   Transmeta TransmetaCPU
Sep 19 10:19:47 david-pc kernel: [    0.000000]   UMC UMC UMC UMC
Sep 19 10:19:47 david-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7f0000 (usable)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 000000003f7f3000 - 000000003f800000 (ACPI data)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000] DMI 2.3 present.
Sep 19 10:19:47 david-pc kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Sep 19 10:19:47 david-pc kernel: [    0.000000] last_pfn = 0x3f7f0 max_arch_pfn = 0x100000
Sep 19 10:19:47 david-pc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep 19 10:19:47 david-pc kernel: [    0.000000] Scanning 0 areas for low memory corruption
Sep 19 10:19:47 david-pc kernel: [    0.000000] modified physical RAM map:
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 0000000000100000 - 000000003f7f0000 (usable)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 000000003f7f3000 - 000000003f800000 (ACPI data)
Sep 19 10:19:47 david-pc kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Sep 19 10:19:47 david-pc kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Sep 19 10:19:47 david-pc kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Sep 19 10:19:47 david-pc kernel: [    0.000000] RAMDISK: 2f29b000 - 2fa33bf0
Sep 19 10:19:47 david-pc kernel: [    0.000000] ACPI Error: A valid RSDP was not found (20090903/tbxfroot-219)
Sep 19 10:19:47 david-pc kernel: [    0.000000] 127MB HIGHMEM available.
Sep 19 10:19:47 david-pc kernel: [    0.000000] 887MB LOWMEM available.
Sep 19 10:19:47 david-pc kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Sep 19 10:19:47 david-pc kernel: [    0.000000]   low ram: 0 - 377fe000
Sep 19 10:19:47 david-pc kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Sep 19 10:19:47 david-pc kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Sep 19 10:19:47 david-pc kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #4 [002f29b000 - 002fa33bf0]          RAMDISK ==> [002f29b000 - 002fa33bf0]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #6 [00008de000 - 00008e1194]              BRK ==> [00008de000 - 00008e1194]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Sep 19 10:19:47 david-pc kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Sep 19 10:19:47 david-pc kernel: [    0.000000] found SMP MP-table at [c00f5f00] f5f00
Sep 19 10:19:47 david-pc kernel: [    0.000000] Zone PFN ranges:
Sep 19 10:19:47 david-pc kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 19 10:19:47 david-pc kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Sep 19 10:19:47 david-pc kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f7f0
Sep 19 10:19:47 david-pc kernel: [    0.000000] Movable zone start PFN for each node
Sep 19 10:19:47 david-pc kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep 19 10:19:47 david-pc kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep 19 10:19:47 david-pc kernel: [    0.000000]     0: 0x00000100 -> 0x0003f7f0
Sep 19 10:19:47 david-pc kernel: [    0.000000] Using APIC driver default
Sep 19 10:19:47 david-pc kernel: [    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Sep 19 10:19:47 david-pc kernel: [    0.000000]     Virtual Wire compatibility mode.
Sep 19 10:19:47 david-pc kernel: [    0.000000] MPTABLE: OEM ID: OEM00000
Sep 19 10:19:47 david-pc kernel: [    0.000000] MPTABLE: Product ID: PROD00000000
Sep 19 10:19:47 david-pc kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Sep 19 10:19:47 david-pc kernel: [    0.000000] Processor #0 (Bootup-CPU)
Sep 19 10:19:47 david-pc kernel: [    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
Sep 19 10:19:47 david-pc kernel: [    0.000000] Processors: 1
Sep 19 10:19:47 david-pc kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Sep 19 10:19:47 david-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 10:19:47 david-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Sep 19 10:19:47 david-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Sep 19 10:19:47 david-pc kernel: [    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf400000)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 19 10:19:47 david-pc kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Sep 19 10:19:47 david-pc kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
Sep 19 10:19:47 david-pc kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
Sep 19 10:19:47 david-pc kernel: [    0.000000] pcpu-alloc: [0] 0 
Sep 19 10:19:47 david-pc kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257935
Sep 19 10:19:47 david-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=444cbddf-4be0-403f-8197-ad0432f5e984 ro quiet splash
Sep 19 10:19:47 david-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 19 10:19:47 david-pc kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 19 10:19:47 david-pc kernel: [    0.000000] Initializing CPU#0
Sep 19 10:19:47 david-pc kernel: [    0.000000] allocated 5201280 bytes of page_cgroup
Sep 19 10:19:47 david-pc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep 19 10:19:47 david-pc kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f7f0)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Memory: 1009368k/1040320k available (4679k kernel code, 29952k reserved, 2124k data, 660k init, 131016k highmem)
Sep 19 10:19:47 david-pc kernel: [    0.000000] virtual kernel memory layout:
Sep 19 10:19:47 david-pc kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Sep 19 10:19:47 david-pc kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 19 10:19:47 david-pc kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Sep 19 10:19:47 david-pc kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Sep 19 10:19:47 david-pc kernel: [    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
Sep 19 10:19:47 david-pc kernel: [    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
Sep 19 10:19:47 david-pc kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
Sep 19 10:19:47 david-pc kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep 19 10:19:47 david-pc kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Sep 19 10:19:47 david-pc kernel: [    0.000000] Hierarchical RCU implementation.
Sep 19 10:19:47 david-pc kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Sep 19 10:19:47 david-pc kernel: [    0.000000] Console: colour VGA+ 80x25
Sep 19 10:19:47 david-pc kernel: [    0.000000] console [tty0] enabled
Sep 19 10:19:47 david-pc kernel: [    0.000000] Fast TSC calibration using PIT
Sep 19 10:19:47 david-pc kernel: [    0.000000] Detected 2932.764 MHz processor.
Sep 19 10:19:47 david-pc kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5865.52 BogoMIPS (lpj=11731056)
Sep 19 10:19:47 david-pc kernel: [    0.004035] Security Framework initialized
Sep 19 10:19:47 david-pc kernel: [    0.004072] AppArmor: AppArmor initialized
Sep 19 10:19:47 david-pc kernel: [    0.004084] Mount-cache hash table entries: 512
Sep 19 10:19:47 david-pc kernel: [    0.004265] Initializing cgroup subsys ns
Sep 19 10:19:47 david-pc kernel: [    0.004273] Initializing cgroup subsys cpuacct
Sep 19 10:19:47 david-pc kernel: [    0.004279] Initializing cgroup subsys memory
Sep 19 10:19:47 david-pc kernel: [    0.004292] Initializing cgroup subsys devices
Sep 19 10:19:47 david-pc kernel: [    0.004295] Initializing cgroup subsys freezer
Sep 19 10:19:47 david-pc kernel: [    0.004298] Initializing cgroup subsys net_cls
Sep 19 10:19:47 david-pc kernel: [    0.004333] CPU: Trace cache: 12K uops, L1 D cache: 16K
Sep 19 10:19:47 david-pc kernel: [    0.004338] CPU: L2 cache: 256K
Sep 19 10:19:47 david-pc kernel: [    0.004341] CPU: Hyper-Threading is disabled
Sep 19 10:19:47 david-pc kernel: [    0.004347] mce: CPU supports 4 MCE banks
Sep 19 10:19:47 david-pc kernel: [    0.004363] CPU0: Thermal monitoring enabled (TM1)
Sep 19 10:19:47 david-pc kernel: [    0.004371] using mwait in idle threads.
Sep 19 10:19:47 david-pc kernel: [    0.004383] Performance Events: no PMU driver, software events only.
Sep 19 10:19:47 david-pc kernel: [    0.004393] Checking 'hlt' instruction... OK.
Sep 19 10:19:47 david-pc kernel: [    0.021215] SMP alternatives: switching to UP code
Sep 19 10:19:47 david-pc kernel: [    0.034199] Freeing SMP alternatives: 19k freed
Sep 19 10:19:47 david-pc kernel: [    0.034230] ftrace: converting mcount calls to 0f 1f 44 00 00
Sep 19 10:19:47 david-pc kernel: [    0.034242] ftrace: allocating 21780 entries in 43 pages
Sep 19 10:19:47 david-pc kernel: [    0.036134] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 19 10:19:47 david-pc kernel: [    0.036196] ExtINT not setup in hardware but reported by MP table
Sep 19 10:19:47 david-pc kernel: [    0.036465] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Sep 19 10:19:47 david-pc kernel: [    0.076376] CPU0: Intel(R) Celeron(R) CPU 2.93GHz stepping 04
Sep 19 10:19:47 david-pc kernel: [    0.184269] Brought up 1 CPUs
Sep 19 10:19:47 david-pc kernel: [    0.184276] Total of 1 processors activated (5865.52 BogoMIPS).
Sep 19 10:19:47 david-pc kernel: [    0.184563] devtmpfs: initialized
Sep 19 10:19:47 david-pc kernel: [    0.185140] regulator: core version 0.5
Sep 19 10:19:47 david-pc kernel: [    0.185168] Time: 10:19:35  Date: 09/19/10
Sep 19 10:19:47 david-pc kernel: [    0.185246] NET: Registered protocol family 16
Sep 19 10:19:47 david-pc kernel: [    0.185429] EISA bus registered
Sep 19 10:19:47 david-pc kernel: [    0.213104] PCI: PCI BIOS revision 2.10 entry at 0xfb9b0, last bus=1
Sep 19 10:19:47 david-pc kernel: [    0.213107] PCI: Using configuration type 1 for base access
Sep 19 10:19:47 david-pc kernel: [    0.214456] bio: create slab <bio-0> at 0
Sep 19 10:19:47 david-pc kernel: [    0.214558] ACPI: Interpreter disabled.
Sep 19 10:19:47 david-pc kernel: [    0.214653] vgaarb: loaded
Sep 19 10:19:47 david-pc kernel: [    0.214828] SCSI subsystem initialized
Sep 19 10:19:47 david-pc kernel: [    0.215047] usbcore: registered new interface driver usbfs
Sep 19 10:19:47 david-pc kernel: [    0.215065] usbcore: registered new interface driver hub
Sep 19 10:19:47 david-pc kernel: [    0.215113] usbcore: registered new device driver usb
Sep 19 10:19:47 david-pc kernel: [    0.215300] PCI: Probing PCI hardware
Sep 19 10:19:47 david-pc kernel: [    0.215799] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Sep 19 10:19:47 david-pc kernel: [    0.215804] pci 0000:00:1d.7: PME# disabled
Sep 19 10:19:47 david-pc kernel: [    0.215860] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Sep 19 10:19:47 david-pc kernel: [    0.215862] * this clock source is slow. If you are sure your timer does not have
Sep 19 10:19:47 david-pc kernel: [    0.215863] * this bug, please use "acpi_pm_good" to disable the workaround
Sep 19 10:19:47 david-pc kernel: [    0.215911] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Sep 19 10:19:47 david-pc kernel: [    0.215915] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Sep 19 10:19:47 david-pc kernel: [    0.216163] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Sep 19 10:19:47 david-pc kernel: [    0.216168] pci 0000:00:1f.5: PME# disabled
Sep 19 10:19:47 david-pc kernel: [    0.216285] pci 0000:01:0b.0: PME# supported from D2 D3hot D3cold
Sep 19 10:19:47 david-pc kernel: [    0.216289] pci 0000:01:0b.0: PME# disabled
Sep 19 10:19:47 david-pc kernel: [    0.216382] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
Sep 19 10:19:47 david-pc kernel: [    0.216387] pci 0000:01:0c.0: PME# disabled
Sep 19 10:19:47 david-pc kernel: [    0.216417] pci 0000:00:1e.0: transparent bridge
Sep 19 10:19:47 david-pc kernel: [    0.216497] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Sep 19 10:19:47 david-pc kernel: [    0.216857] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:24c0]
Sep 19 10:19:47 david-pc kernel: [    0.217061] NetLabel: Initializing
Sep 19 10:19:47 david-pc kernel: [    0.217065] NetLabel:  domain hash size = 128
Sep 19 10:19:47 david-pc kernel: [    0.217066] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 19 10:19:47 david-pc kernel: [    0.217084] NetLabel:  unlabeled traffic allowed by default
Sep 19 10:19:47 david-pc kernel: [    0.217161] Switching to clocksource tsc
Sep 19 10:19:47 david-pc kernel: [    0.219771] AppArmor: AppArmor Filesystem Enabled
Sep 19 10:19:47 david-pc kernel: [    0.219780] pnp: PnP ACPI: disabled
Sep 19 10:19:47 david-pc kernel: [    0.219787] PnPBIOS: Scanning system for PnP BIOS support...
Sep 19 10:19:47 david-pc kernel: [    0.219837] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc3b0
Sep 19 10:19:47 david-pc kernel: [    0.219840] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc3e0, dseg 0xf0000
Sep 19 10:19:47 david-pc kernel: [    0.220001] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:08: iomem range 0xffb00000-0xffb7ffff has been reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:08: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:08: iomem range 0xfee00000-0xfee0ffff has been reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:08: iomem range 0x100000-0xffffff could not be reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:09: iomem range 0xf8000-0xfffff could not be reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] system 00:09: iomem range 0xcc000-0xcffff has been reserved
Sep 19 10:19:47 david-pc kernel: [    0.220001] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Sep 19 10:19:47 david-pc kernel: [    0.220001] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Sep 19 10:19:47 david-pc kernel: [    0.220001] pci 0000:00:1e.0:   MEM window: 0xec000000-0xedffffff
Sep 19 10:19:47 david-pc kernel: [    0.220001] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x400fffff
Sep 19 10:19:47 david-pc kernel: [    0.220001] NET: Registered protocol family 2
Sep 19 10:19:47 david-pc kernel: [    0.220001] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.220304] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.221538] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.222249] TCP: Hash tables configured (established 131072 bind 65536)
Sep 19 10:19:47 david-pc kernel: [    0.222256] TCP reno registered
Sep 19 10:19:47 david-pc kernel: [    0.222467] NET: Registered protocol family 1
Sep 19 10:19:47 david-pc kernel: [    0.222918] cpufreq-nforce2: No nForce2 chipset.
Sep 19 10:19:47 david-pc kernel: [    0.222961] Scanning for low memory corruption every 60 seconds
Sep 19 10:19:47 david-pc kernel: [    0.223118] audit: initializing netlink socket (disabled)
Sep 19 10:19:47 david-pc kernel: [    0.223138] type=2000 audit(1284891575.222:1): initialized
Sep 19 10:19:47 david-pc kernel: [    0.232432] Trying to unpack rootfs image as initramfs...
Sep 19 10:19:47 david-pc kernel: [    0.243218] highmem bounce pool size: 64 pages
Sep 19 10:19:47 david-pc kernel: [    0.243228] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep 19 10:19:47 david-pc kernel: [    0.250963] VFS: Disk quotas dquot_6.5.2
Sep 19 10:19:47 david-pc kernel: [    0.251099] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 19 10:19:47 david-pc kernel: [    0.251983] fuse init (API version 7.13)
Sep 19 10:19:47 david-pc kernel: [    0.252133] msgmni has been set to 1716
Sep 19 10:19:47 david-pc kernel: [    0.252500] alg: No test for stdrng (krng)
Sep 19 10:19:47 david-pc kernel: [    0.252618] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep 19 10:19:47 david-pc kernel: [    0.252624] io scheduler noop registered
Sep 19 10:19:47 david-pc kernel: [    0.252626] io scheduler anticipatory registered
Sep 19 10:19:47 david-pc kernel: [    0.252629] io scheduler deadline registered
Sep 19 10:19:47 david-pc kernel: [    0.252682] io scheduler cfq registered (default)
Sep 19 10:19:47 david-pc kernel: [    0.252826] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 19 10:19:47 david-pc kernel: [    0.252860] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 19 10:19:47 david-pc kernel: [    0.261126] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Sep 19 10:19:47 david-pc kernel: [    0.261242] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 19 10:19:47 david-pc kernel: [    0.261806] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 19 10:19:47 david-pc kernel: [    0.262839] isapnp: Scanning for PnP cards...
Sep 19 10:19:47 david-pc kernel: [    0.268902] brd: module loaded
Sep 19 10:19:47 david-pc kernel: [    0.269585] loop: module loaded
Sep 19 10:19:47 david-pc kernel: [    0.269753] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 19 10:19:47 david-pc kernel: [    0.269946] ata_piix 0000:00:1f.1: PCI->APIC IRQ transform: INT A -> IRQ 16
Sep 19 10:19:47 david-pc kernel: [    0.270162] scsi0 : ata_piix
Sep 19 10:19:47 david-pc kernel: [    0.270335] scsi1 : ata_piix
Sep 19 10:19:47 david-pc kernel: [    0.270389] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Sep 19 10:19:47 david-pc kernel: [    0.270394] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Sep 19 10:19:47 david-pc kernel: [    0.270911] Fixed MDIO Bus: probed
Sep 19 10:19:47 david-pc kernel: [    0.270963] PPP generic driver version 2.4.2
Sep 19 10:19:47 david-pc kernel: [    0.271053] tun: Universal TUN/TAP device driver, 1.6
Sep 19 10:19:47 david-pc kernel: [    0.271056] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 19 10:19:47 david-pc kernel: [    0.271212] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 19 10:19:47 david-pc kernel: [    0.271257] ehci_hcd 0000:00:1d.7: PCI->APIC IRQ transform: INT D -> IRQ 23
Sep 19 10:19:47 david-pc kernel: [    0.271292] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 19 10:19:47 david-pc kernel: [    0.271362] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Sep 19 10:19:47 david-pc kernel: [    0.322862] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee080000
Sep 19 10:19:47 david-pc kernel: [    0.342801] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Sep 19 10:19:47 david-pc kernel: [    0.343015] usb usb1: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    0.343060] hub 1-0:1.0: USB hub found
Sep 19 10:19:47 david-pc kernel: [    0.343076] hub 1-0:1.0: 6 ports detected
Sep 19 10:19:47 david-pc kernel: [    0.343168] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 19 10:19:47 david-pc kernel: [    0.343193] uhci_hcd: USB Universal Host Controller Interface driver
Sep 19 10:19:47 david-pc kernel: [    0.343256] uhci_hcd 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 16
Sep 19 10:19:47 david-pc kernel: [    0.343273] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 19 10:19:47 david-pc kernel: [    0.343364] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Sep 19 10:19:47 david-pc kernel: [    0.343401] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Sep 19 10:19:47 david-pc kernel: [    0.343551] usb usb2: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    0.343596] hub 2-0:1.0: USB hub found
Sep 19 10:19:47 david-pc kernel: [    0.343611] hub 2-0:1.0: 2 ports detected
Sep 19 10:19:47 david-pc kernel: [    0.343681] uhci_hcd 0000:00:1d.1: PCI->APIC IRQ transform: INT B -> IRQ 19
Sep 19 10:19:47 david-pc kernel: [    0.343696] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 19 10:19:47 david-pc kernel: [    0.343770] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Sep 19 10:19:47 david-pc kernel: [    0.343805] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Sep 19 10:19:47 david-pc kernel: [    0.343953] usb usb3: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    0.343994] hub 3-0:1.0: USB hub found
Sep 19 10:19:47 david-pc kernel: [    0.344006] hub 3-0:1.0: 2 ports detected
Sep 19 10:19:47 david-pc kernel: [    0.344074] uhci_hcd 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18
Sep 19 10:19:47 david-pc kernel: [    0.344089] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 19 10:19:47 david-pc kernel: [    0.344168] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Sep 19 10:19:47 david-pc kernel: [    0.344204] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Sep 19 10:19:47 david-pc kernel: [    0.344357] usb usb4: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    0.344398] hub 4-0:1.0: USB hub found
Sep 19 10:19:47 david-pc kernel: [    0.344411] hub 4-0:1.0: 2 ports detected
Sep 19 10:19:47 david-pc kernel: [    0.344548] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
Sep 19 10:19:47 david-pc kernel: [    0.344552] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep 19 10:19:47 david-pc kernel: [    0.345138] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 19 10:19:47 david-pc kernel: [    0.345360] mice: PS/2 mouse device common for all mice
Sep 19 10:19:47 david-pc kernel: [    0.351140] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Sep 19 10:19:47 david-pc kernel: [    0.351173] rtc0: alarms up to one day, 114 bytes nvram
Sep 19 10:19:47 david-pc kernel: [    0.351373] device-mapper: uevent: version 1.0.3
Sep 19 10:19:47 david-pc kernel: [    0.351613] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Sep 19 10:19:47 david-pc kernel: [    0.351726] device-mapper: multipath: version 1.1.0 loaded
Sep 19 10:19:47 david-pc kernel: [    0.351731] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 19 10:19:47 david-pc kernel: [    0.351930] EISA: Probing bus 0 at eisa.0
Sep 19 10:19:47 david-pc kernel: [    0.351970] EISA: Detected 0 cards.
Sep 19 10:19:47 david-pc kernel: [    0.355128] cpuidle: using governor ladder
Sep 19 10:19:47 david-pc kernel: [    0.355134] cpuidle: using governor menu
Sep 19 10:19:47 david-pc kernel: [    0.355758] TCP cubic registered
Sep 19 10:19:47 david-pc kernel: [    0.355944] NET: Registered protocol family 10
Sep 19 10:19:47 david-pc kernel: [    0.356571] lo: Disabled Privacy Extensions
Sep 19 10:19:47 david-pc kernel: [    0.357003] NET: Registered protocol family 17
Sep 19 10:19:47 david-pc kernel: [    0.357076] Using IPI No-Shortcut mode
Sep 19 10:19:47 david-pc kernel: [    0.357246] registered taskstats version 1
Sep 19 10:19:47 david-pc kernel: [    0.357448]   Magic number: 10:775:325
Sep 19 10:19:47 david-pc kernel: [    0.357526] rtc_cmos 00:03: setting system clock to 2010-09-19 10:19:35 UTC (1284891575)
Sep 19 10:19:47 david-pc kernel: [    0.357530] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 19 10:19:47 david-pc kernel: [    0.357532] EDD information not available.
Sep 19 10:19:47 david-pc kernel: [    0.506626] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
Sep 19 10:19:47 david-pc kernel: [    0.506631] ata1.00: 488397168 sectors, multi 16: LBA48 
Sep 19 10:19:47 david-pc kernel: [    0.507000] ata1.01: ATA-6: WDC WD3000JB-00KFA0, 08.05J08, max UDMA/100
Sep 19 10:19:47 david-pc kernel: [    0.507004] ata1.01: 586072368 sectors, multi 16: LBA48 
Sep 19 10:19:47 david-pc kernel: [    0.515727] ata2.00: ATAPI: TSST CDW/DVD TS-H492A, HP02, max UDMA/33
Sep 19 10:19:47 david-pc kernel: [    0.515777] ata2.01: ATAPI: DVD RW DRU-820A, 1.0b, max UDMA/66
Sep 19 10:19:47 david-pc kernel: [    0.515810] ata2.01: limited to UDMA/33 due to 40-wire cable
Sep 19 10:19:47 david-pc kernel: [    0.523272] ata1.00: configured for UDMA/100
Sep 19 10:19:47 david-pc kernel: [    0.539321] ata1.01: configured for UDMA/100
Sep 19 10:19:47 david-pc kernel: [    0.686566] usb 1-1: new high speed USB device using ehci_hcd and address 2
Sep 19 10:19:47 david-pc kernel: [    0.691434] ata2.00: configured for UDMA/33
Sep 19 10:19:47 david-pc kernel: [    0.707518] ata2.01: configured for UDMA/33
Sep 19 10:19:47 david-pc kernel: [    0.803257] Freeing initrd memory: 7778k freed
Sep 19 10:19:47 david-pc kernel: [    0.902504] isapnp: No Plug & Play device found
Sep 19 10:19:47 david-pc kernel: [    0.902742] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
Sep 19 10:19:47 david-pc kernel: [    0.903017] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 19 10:19:47 david-pc kernel: [    0.903247] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Sep 19 10:19:47 david-pc kernel: [    0.903333] sd 0:0:0:0: [sda] Write Protect is off
Sep 19 10:19:47 david-pc kernel: [    0.903376] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 10:19:47 david-pc kernel: [    0.903633]  sda: sda1 sda2
Sep 19 10:19:47 david-pc kernel: [    0.911412] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3000JB-00K 08.0 PQ: 0 ANSI: 5
Sep 19 10:19:47 david-pc kernel: [    0.911634] sd 0:0:1:0: Attached scsi generic sg1 type 0
Sep 19 10:19:47 david-pc kernel: [    0.912180] sd 0:0:1:0: [sdb] 586072368 512-byte logical blocks: (300 GB/279 GiB)
Sep 19 10:19:47 david-pc kernel: [    0.912265] sd 0:0:1:0: [sdb] Write Protect is off
Sep 19 10:19:47 david-pc kernel: [    0.912331] scsi 1:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-H492A HP02 PQ: 0 ANSI: 5
Sep 19 10:19:47 david-pc kernel: [    0.912697] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 19 10:19:47 david-pc kernel: [    0.912987] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 19 10:19:47 david-pc kernel: [    0.913301]  sdb:sr0: scsi3-mmc drive: 5x/48x writer cd/rw xa/form2 cdda tray
Sep 19 10:19:47 david-pc kernel: [    0.914720] Uniform CD-ROM driver Revision: 3.20
Sep 19 10:19:47 david-pc kernel: [    0.915015] sr 1:0:0:0: Attached scsi generic sg2 type 5
Sep 19 10:19:47 david-pc kernel: [    0.915759] usb 1-1: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    0.915969] hub 1-1:1.0: USB hub found
Sep 19 10:19:47 david-pc kernel: [    0.916077] hub 1-1:1.0: 4 ports detected
Sep 19 10:19:47 david-pc kernel: [    0.916489] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ: 0 ANSI: 5
Sep 19 10:19:47 david-pc kernel: [    0.923928] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 19 10:19:47 david-pc kernel: [    0.924205] sr 1:0:1:0: Attached scsi generic sg3 type 5
Sep 19 10:19:47 david-pc kernel: [    0.927010]  sdb1 sdb2 < sdb5 >
Sep 19 10:19:47 david-pc kernel: [    0.948932] sd 0:0:1:0: [sdb] Attached SCSI disk
Sep 19 10:19:47 david-pc kernel: [    0.948954] Freeing unused kernel memory: 660k freed
Sep 19 10:19:47 david-pc kernel: [    0.949902] Write protecting the kernel text: 4680k
Sep 19 10:19:47 david-pc kernel: [    0.949937] Write protecting the kernel read-only data: 1844k
Sep 19 10:19:47 david-pc kernel: [    0.988255] udev: starting version 151
Sep 19 10:19:47 david-pc kernel: [    1.138926] usb 1-4: new high speed USB device using ehci_hcd and address 5
Sep 19 10:19:47 david-pc kernel: [    1.213425] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 19 10:19:47 david-pc kernel: [    1.213460] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Sep 19 10:19:47 david-pc kernel: [    1.237973] 8139too Fast Ethernet driver 0.9.28
Sep 19 10:19:47 david-pc kernel: [    1.238032] 8139too 0000:01:0c.0: PCI->APIC IRQ transform: INT A -> IRQ 23
Sep 19 10:19:47 david-pc kernel: [    1.245583] eth0: RealTek RTL8139 at 0xc800, 00:11:09:72:9c:4a, IRQ 23
Sep 19 10:19:47 david-pc kernel: [    1.272665] usb 1-4: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    1.327556] Initializing USB Mass Storage driver...
Sep 19 10:19:47 david-pc kernel: [    1.327751] scsi2 : SCSI emulation for USB Mass Storage devices
Sep 19 10:19:47 david-pc kernel: [    1.328098] usbcore: registered new interface driver usb-storage
Sep 19 10:19:47 david-pc kernel: [    1.328103] USB Mass Storage support registered.
Sep 19 10:19:47 david-pc kernel: [    1.554220] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Sep 19 10:19:47 david-pc kernel: [    1.554229] EXT4-fs (sdb1): write access will be enabled during recovery
Sep 19 10:19:47 david-pc kernel: [    1.622860] usb 2-2: new low speed USB device using uhci_hcd and address 2
Sep 19 10:19:47 david-pc kernel: [    1.721292] EXT4-fs (sdb1): recovery complete
Sep 19 10:19:47 david-pc kernel: [    1.721980] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Sep 19 10:19:47 david-pc kernel: [    1.811388] usb 2-2: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    2.050890] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 19 10:19:47 david-pc kernel: [    2.249739] usb 3-1: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    2.546922] usb 4-1: new full speed USB device using uhci_hcd and address 2
Sep 19 10:19:47 david-pc kernel: [    2.724096] usb 4-1: configuration #1 chosen from 1 choice
Sep 19 10:19:47 david-pc kernel: [    2.727130] scsi3 : SCSI emulation for USB Mass Storage devices
Sep 19 10:19:47 david-pc kernel: [    6.327936] scsi 2:0:0:0: Direct-Access     HP       Photosmart D110  1.00 PQ: 0 ANSI: 5
Sep 19 10:19:47 david-pc kernel: [    6.328740] sd 2:0:0:0: Attached scsi generic sg4 type 0
Sep 19 10:19:47 david-pc kernel: [    6.330405] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Sep 19 10:19:47 david-pc kernel: [    7.732183] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Sep 19 10:19:47 david-pc kernel: [    7.735178] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Sep 19 10:19:47 david-pc kernel: [    7.738178] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Sep 19 10:19:47 david-pc kernel: [    7.741176] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Sep 19 10:19:47 david-pc kernel: [    7.741954] sd 3:0:0:0: Attached scsi generic sg5 type 0
Sep 19 10:19:47 david-pc kernel: [    7.742210] sd 3:0:0:1: Attached scsi generic sg6 type 0
Sep 19 10:19:47 david-pc kernel: [    7.742451] sd 3:0:0:2: Attached scsi generic sg7 type 0
Sep 19 10:19:47 david-pc kernel: [    7.742674] sd 3:0:0:3: Attached scsi generic sg8 type 0
Sep 19 10:19:47 david-pc kernel: [    7.920143] sd 3:0:0:0: [sdd] Attached SCSI removable disk
Sep 19 10:19:47 david-pc kernel: [    7.925133] sd 3:0:0:1: [sde] Attached SCSI removable disk
Sep 19 10:19:47 david-pc kernel: [    7.930130] sd 3:0:0:2: [sdf] Attached SCSI removable disk
Sep 19 10:19:47 david-pc kernel: [    7.935130] sd 3:0:0:3: [sdg] Attached SCSI removable disk
Sep 19 10:19:47 david-pc kernel: [   10.277507] udev: starting version 151
Sep 19 10:19:47 david-pc kernel: [   10.330715] Adding 2980856k swap on /dev/sdb5.  Priority:-1 extents:1 across:2980856k 
Sep 19 10:19:47 david-pc kernel: [   10.422988] lp: driver loaded but no devices found
Sep 19 10:19:47 david-pc kernel: [   10.475859] Linux agpgart interface v0.103
Sep 19 10:19:47 david-pc kernel: [   10.498146] vga16fb: mapped to 0xc00a0000
Sep 19 10:19:47 david-pc kernel: [   10.498259] fb0: VGA16 VGA frame buffer device
Sep 19 10:19:47 david-pc kernel: [   10.505653] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 19 10:19:47 david-pc kernel: [   10.599540] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Sep 19 10:19:47 david-pc kernel: [   10.599799] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
Sep 19 10:19:47 david-pc kernel: [   10.601891] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
Sep 19 10:19:47 david-pc kernel: [   10.616038] intel_rng: FWH not detected
Sep 19 10:19:47 david-pc kernel: [   10.867176] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8D11
Sep 19 10:19:47 david-pc kernel: [   10.867215] usbcore: registered new interface driver usblp
Sep 19 10:19:47 david-pc kernel: [   10.896103] usbcore: registered new interface driver hiddev
Sep 19 10:19:47 david-pc kernel: [   11.285468] generic-usb 0003:051D:0002.0003: hiddev96,hidraw0: USB HID v1.10 Device [APC Back-UPS NS 600 FW:818.w1 .D USB FW:w1 ] on usb-0000:00:1d.1-1/input0
Sep 19 10:19:47 david-pc kernel: [   11.285514] usbcore: registered new interface driver usbhid
Sep 19 10:19:47 david-pc kernel: [   11.285518] usbhid: v2.6:USB HID core driver
Sep 19 10:19:47 david-pc kernel: [   11.332300] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input1
Sep 19 10:19:47 david-pc kernel: [   11.332507] microsoft 0003:045E:00F9.0001: input,hidraw1: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2/input0
Sep 19 10:19:47 david-pc kernel: [   11.424842] microsoft 0003:045E:00F9.0002: fixing up Microsoft Wireless Receiver Model 1028 report descriptor
Sep 19 10:19:47 david-pc kernel: [   11.473087] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input2
Sep 19 10:19:47 david-pc kernel: [   11.473311] microsoft 0003:045E:00F9.0002: input,hidraw2: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.0-2/input1
Sep 19 10:19:47 david-pc kernel: [   11.697488] Console: switching to colour frame buffer device 80x30
Sep 19 10:19:47 david-pc kernel: [   11.775293] type=1505 audit(1284905986.913:2):  operation="profile_load" pid=556 name="/sbin/dhclient3"
Sep 19 10:19:47 david-pc kernel: [   11.776077] type=1505 audit(1284905986.917:3):  operation="profile_load" pid=556 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 19 10:19:47 david-pc kernel: [   11.776467] type=1505 audit(1284905986.917:4):  operation="profile_load" pid=556 name="/usr/lib/connman/scripts/dhclient-script"
Sep 19 10:19:47 david-pc kernel: [   11.810486] Intel ICH 0000:00:1f.5: PCI->APIC IRQ transform: INT B -> IRQ 17
Sep 19 10:19:47 david-pc kernel: [   12.147560] intel8x0_measure_ac97_clock: measured 54613 usecs (2631 samples)
Sep 19 10:19:47 david-pc kernel: [   12.147566] intel8x0: clocking to 48000
Sep 19 10:19:47 david-pc kernel: [   12.233841] type=1505 audit(1284905987.373:5):  operation="profile_load" pid=658 name="/usr/share/gdm/guest-session/Xsession"
Sep 19 10:19:47 david-pc kernel: [   12.249479] type=1505 audit(1284905987.389:6):  operation="profile_replace" pid=661 name="/sbin/dhclient3"
Sep 19 10:19:47 david-pc kernel: [   12.250247] type=1505 audit(1284905987.389:7):  operation="profile_replace" pid=661 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 19 10:19:47 david-pc kernel: [   12.250659] type=1505 audit(1284905987.389:8):  operation="profile_replace" pid=661 name="/usr/lib/connman/scripts/dhclient-script"
Sep 19 10:19:47 david-pc kernel: [   12.316657] type=1505 audit(1284905987.457:9):  operation="profile_load" pid=664 name="/usr/bin/evince"
Sep 19 10:19:47 david-pc kernel: [   12.388652] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep 19 10:19:47 david-pc kernel: [   12.391389] type=1505 audit(1284905987.529:10):  operation="profile_load" pid=664 name="/usr/bin/evince-previewer"
Sep 19 10:19:47 david-pc kernel: [   12.434991] type=1505 audit(1284905987.573:11):  operation="profile_load" pid=664 name="/usr/bin/evince-thumbnailer"
Sep 19 10:19:48 david-pc kernel: [   13.061717] ppdev: user-space parallel port driver
Sep 19 10:19:49 david-pc kernel: [   14.285206] usb 1-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Sep 19 10:19:51 david-pc pulseaudio[1058]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:19:51 david-pc pulseaudio[1058]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:19:54 david-pc python: hp-systray[1070]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.

Thanks for your response.  BTW what's with the smilies in the log?

David

---

### Post by Rubi1200 on 2010-09-19
Could this be the source of the problem?

> The chipset may have PM-Timer Bug

---

### Post by johnson094 on 2010-09-19
I really have no clue, know nothing about code.  Newbie here.
 
The computer lockup occurs the instant I click on "Home folder" as shown below:
 
Here I selected Places>home folder:
 
Sep 19 10:15:22 david-pc pulseaudio[1378]: pid.c: Stale PID file, overwriting.
Sep 19 10:15:22 david-pc pulseaudio[1378]: main.c: Unable to contact D-Bus: 
 
Here I selected Places>Desktop>personal folder>
Sep 19 10:16:39 david-pc pulseaudio[1109]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:16:39 david-pc pulseaudio[1109]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Sep 19 10:16:41 david-pc python: hp-systray[1120]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.

and here I selected Places>Downloads>then try to go to root folder "david"
 
Not knowing what I'm looking at, it does seem from this log that I have several issues going on.
 
Thanks again.
 
David

---

### Post by Rubi1200 on 2010-09-19
Ok, what graphics card do you have installed and did you make any changes to it such as updates etc.?

---

### Post by johnson094 on 2010-09-19
Initially I had what myself and others thought were graphics issues when I tried to boot Ubuntu it would lock up and cycle "Ubuntu logo page> blank screen>Ubuntu logo page" until I rebooted.  You might want to review my thread "Advice for newbies".  Anyway I was running off the Vision Tek Radeon X1300 Graphics card but since the problems initially, I took it out and am running "onboard" which is Intel 82845G/GL/PE/GV Graphics Controller.  I have not made any changes.  Just before Ubuntu finally installed and began working, I scanned my computer for driver updates and downloaded all that were advised using "Driver MD"
 
Here is "lspci" (before driver updates)
 
david@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0a.0 PCI bridge: PLX Technology, Inc. PEX 8111 PCI Express-to-PCI Bridge (rev 21)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
[EMAIL="david@ubuntu:~$"]david@ubuntu:~$[/EMAIL] 

Thanks again.

---

### Post by johnson094 on 2010-09-19
Here is my lspci just obtained.  As you can see the Radeon 1300 has been removed.  I checked CMOS and I have "onboard" selected.

david@david-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thanks,

David

---

### Post by Rubi1200 on 2010-09-19
Hi,
you have an Intel chipset:

```
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics 
```

Look here for workarounds (I believe your specific chipset is mentioned):
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by johnson094 on 2010-09-19
Ok, I see your point.  Now, should I install the patch..try to access the folder, and if no success start working thru the workarounds one at the time?:confused:

---

### Post by Rubi1200 on 2010-09-19
Yes and no; what I am suggesting is that the source of your problems such as black screens, lockups etc. may have to do with the unpatched chipset. 

On my test laptop, I applied the Glasen PPA and everything works like a charm.

---

### Post by johnson094 on 2010-09-19
All right, I see where Workaround "G" has been tested on my chipset.  So I should perform workaround "A" and reboot.  I did that and tested.  No change.
 
Now I go to workaround "E" which disables DRI.  I opened terminal and entered:
 
[FONT=Courier New]/etc/X11/xorg.conf[/FONT]: 
 
I get "command not found".  So undoubtedly it wasn't meant to be entered as a command.  How do I open this conf file in order to paste the information?
 
Sorry to be such a noob.

---

### Post by johnson094 on 2010-09-19
Been trying to find this file "xorg.conf" .  Terminal recognizes the dir /etc/X11/  but can't find the file.
Searching for file "xorg.conf  I get 2 files.  /usr/lib/X11/xorg.conf.d  and  /usr/share/man/man5/xorg.conf.5.gz.

Still reading.

Thanks

---

### Post by Rubi1200 on 2010-09-19
So, it seems that xorg.conf is not really used anymore; hence the empty file.

But, I did find this and it should help you get moving along:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by scorchgeek on 2010-09-19
You need to put a text editor and 'sudo' before that path (although in this case it seems you don't need to use that file), like so:
```
sudo vim /etc/X11/xorg.conf
```

Other common text editors are gedit, nano, and emacs (which isn't installed by default). Nano and gedit are the easiest for new users.

---

### Post by johnson094 on 2010-09-19
Ok, I'll give that a try.  I just ran a system check on my video from inside Ubuntu and everything was fine until I got to the xrander cycle test (whatever that is) It started out at the higher resolutions and cycled through down toward what seemed to be the lower ends.  It locked up when it got down about what I would guess by screen appearance to be about the 800 x 600 area (just guessing).  Locked up just like it does when I try to open "home folder".
 
I just don't understand why a problem with the video/monitor would affect just that one folder.  I can open and view every other folder I wish to open without a hitch.
 
I'll keep digging.:(

---

### Post by johnson094 on 2010-09-19
UPDATE:
 
Have read all kinds of remedies for my problem, but I don't understand 10% of what I read. After several hours of making changes (keeping notes of all I did) and then undoing all of them, I am left with graphics that look like Windows 101. 
I can however open my personal folder from the desktop. I did away with all the backgrounds, etc. If I even open the backgrounds folder under "Appearance" the program locks up. BTW what is the "drum" sound actually alerting me to?
 
Appreciate you hanging in there with me. I'm mentally exhausted and about ready to cave in. maybe after a little rest, I'll hit it again tomorrow.
 
Later :(
 
Just a thought, what would be the optimum setup for a computer that would run 10.04.1 and eventually 10.10 without all these conflicts.  I am about to go shopping.

---

