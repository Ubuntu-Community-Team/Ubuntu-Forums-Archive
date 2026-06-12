---
title: "Problem with TeeWorlds in Xubuntu"
date: 2011-01-08
forum: General Help
---

### Post by faiface on 2011-01-08
Hi everyone! I have one problem with TeeWorlds, the linux native game. I'm using Xubuntu 10.10 on my computer. I have Pentium III, 1.2 GHz, 512 MB RAM. Every time I try to run the game It outputs this:

[4d283831][engine]: running on unix-linux-ia32
[4d283831][engine]: arch is little endian
[4d283831][binds]: bound f1 (282) = toggle_local_console
[4d283831][binds]: bound f2 (283) = toggle_remote_console
[4d283831][binds]: bound tab (9) = +scoreboard
[4d283831][binds]: bound f10 (291) = screenshot
[4d283831][binds]: bound a (97) = +left
[4d283831][binds]: bound d (100) = +right
[4d283831][binds]: bound space (32) = +jump
[4d283831][binds]: bound mouse1 (323) = +fire
[4d283831][binds]: bound mouse2 (324) = +hook
[4d283831][binds]: bound lshift (304) = +emote
[4d283831][binds]: bound 1 (49) = +weapon1
[4d283831][binds]: bound 2 (50) = +weapon2
[4d283831][binds]: bound 3 (51) = +weapon3
[4d283831][binds]: bound 4 (52) = +weapon4
[4d283831][binds]: bound 5 (53) = +weapon5
[4d283831][binds]: bound mousewheelup (331) = +prevweapon
[4d283831][binds]: bound mousewheeldown (332) = +nextweapon
[4d283831][binds]: bound t (116) = chat all
[4d283831][binds]: bound y (121) = chat team
[4d283831][binds]: bound f3 (284) = vote yes
[4d283831][binds]: bound f4 (285) = vote no
[4d283831][engine/datadir]: paths used:
[4d283831][engine/datadir]: 	.
[4d283831][engine/datadir]: 	/home/faiface/.teeworlds
[4d283831][engine/datadir]: 	/usr/share/games/teeworlds/data
[4d283831][engine/datadir]: saving files to: /home/faiface/.teeworlds
[4d283831][console]: failed to open 'autoexec.cfg'
[4d283831][console]: failed to open 'settings.cfg'
[4d283833][engine/mastersrv]: refreshing master server addresses
[4d283833][client/sound]: sound init successful
[4d283835][font]: gfx memory used for font textures: 3058288
*********************************WARN_ONCE*********************************
File radeon_swtcl.c function r100_swtcl_flush line 325
Rendering was 10 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
[4d283835][game]: load skin default
[4d283835][game]: load skin redbopp
[4d283835][game]: load skin warpaint
[4d283835][game]: load skin toptri
[4d283836][game]: load skin redstripe
[4d283836][game]: load skin bluekitty
[4d283836][game]: load skin twinbop
[4d283836][game]: load skin cammo
[4d283836][game]: load skin cammostripes
[4d283836][game]: load skin pinky
[4d283836][game]: load skin coala
[4d283836][game]: load skin bluestripe
[4d283836][game]: load skin twintri
[4d283836][game]: load skin brownbear
[4d283836][game]: load skin saddo
[4d283836][game]: load skin x_ninja
[4d283836][game]: load skin limekitty
[4d283838][]: 4646.235000.2ms
[4d283838][client]: version 0.5 b67d1f1a1eea234e
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

And close (or probably crash).
I ran dmesg "for more info" and it outputs this:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001fff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000001fff0c00 - 000000001fffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fffc000 - 0000000020000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ffd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  modified: 000000001ffd0000 - 000000001fff0c00 (reserved)
[    0.000000]  modified: 000000001fff0c00 - 000000001fffc000 (ACPI NVS)
[    0.000000]  modified: 000000001fffc000 - 0000000020000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ffd0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ffd0000 page 4k
[    0.000000] kernel direct mapping tables up to 1ffd0000 @ 15000-1a000
[    0.000000] RAMDISK: 175da000 - 1801c000
[    0.000000] ACPI: RSDP 000f9970 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 1fff0c84 00030 (v01 COMPAQ CPQ0030  31120320 CPQ  00000001)
[    0.000000] ACPI: FACP 1fff0c00 00084 (v02 COMPAQ CPQ0030  00000002 CPQ  00000001)
[    0.000000] ACPI: DSDT 1fff0cb4 06F17 (v01 COMPAQ EVON600C 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 1fffbe80 00040
[    0.000000] ACPI: SSDT 1fff7bcb 0004B (v01 COMPAQ   CPQCPU 00001001 MSFT 0100000E)
[    0.000000] ACPI: SSDT 1fff7c16 0010E (v01 COMPAQ  CPQGysr 00001001 MSFT 0100000E)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ffd0000
[    0.000000]   low ram: 0 - 1ffd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ffd0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ffd0
[    0.000000] On node 0 totalpages: 130912
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125936 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:e0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129888
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=2128e0ad-ec30-449b-adae-6e7ac51cee81 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2620460 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (38 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [00175da000 - 001801c000]         RAMDISK
[    0.000000]   #4 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a3000 - 00009a6108]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001401000]         BOOTMEM
[    0.000000]   #11 [0001401000 - 0001401004]         BOOTMEM
[    0.000000]   #12 [0001401040 - 0001401100]         BOOTMEM
[    0.000000]   #13 [0001401100 - 0001401130]         BOOTMEM
[    0.000000]   #14 [0001401140 - 0001402940]         BOOTMEM
[    0.000000]   #15 [0001402940 - 0001402a58]         BOOTMEM
[    0.000000]   #16 [0001402a80 - 0001402ac0]         BOOTMEM
[    0.000000]   #17 [0001402ac0 - 0001402b00]         BOOTMEM
[    0.000000]   #18 [0001402b00 - 0001402b40]         BOOTMEM
[    0.000000]   #19 [0001402b40 - 0001402b80]         BOOTMEM
[    0.000000]   #20 [0001402b80 - 0001402bc0]         BOOTMEM
[    0.000000]   #21 [0001402bc0 - 0001402c00]         BOOTMEM
[    0.000000]   #22 [0001402c00 - 0001402c40]         BOOTMEM
[    0.000000]   #23 [0001402c40 - 0001402c50]         BOOTMEM
[    0.000000]   #24 [0001402c80 - 0001402c90]         BOOTMEM
[    0.000000]   #25 [0001402cc0 - 0001402d2a]         BOOTMEM
[    0.000000]   #26 [0001402d40 - 0001402daa]         BOOTMEM
[    0.000000]   #27 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #28 [0001404dc0 - 0001404dc4]         BOOTMEM
[    0.000000]   #29 [0001404e00 - 0001404e04]         BOOTMEM
[    0.000000]   #30 [0001404e40 - 0001404e44]         BOOTMEM
[    0.000000]   #31 [0001404e80 - 0001404e84]         BOOTMEM
[    0.000000]   #32 [0001404ec0 - 0001404f70]         BOOTMEM
[    0.000000]   #33 [0001404f80 - 0001405028]         BOOTMEM
[    0.000000]   #34 [0001402dc0 - 0001404dc0]         BOOTMEM
[    0.000000]   #35 [0001405040 - 0001445040]         BOOTMEM
[    0.000000]   #36 [0001445040 - 0001465040]         BOOTMEM
[    0.000000]   #37 [0001466000 - 00016e5c2c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 497136k/524096k available (4931k kernel code, 26512k reserved, 2333k data, 688k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07d0000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0ebe   (4931 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1195.942 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 2391.88 BogoMIPS (lpj=4783768)
[    0.004019] pid_max: default: 32768 minimum: 301
[    0.004063] Security Framework initialized
[    0.004109] AppArmor: AppArmor initialized
[    0.004113] Yama: becoming mindful.
[    0.008017] Mount-cache hash table entries: 512
[    0.008263] Initializing cgroup subsys ns
[    0.008271] Initializing cgroup subsys cpuacct
[    0.008281] Initializing cgroup subsys memory
[    0.008299] Initializing cgroup subsys devices
[    0.008305] Initializing cgroup subsys freezer
[    0.008310] Initializing cgroup subsys net_cls
[    0.008368] mce: CPU supports 5 MCE banks
[    0.008396] Performance Events: 
[    0.008402] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008407] no hardware sampling interrupt available.
[    0.008411] p6 PMU driver.
[    0.008438] ... version:                0
[    0.008442] ... bit width:              32
[    0.008446] ... generic registers:      2
[    0.008451] ... value mask:             00000000ffffffff
[    0.008456] ... max period:             000000007fffffff
[    0.008460] ... fixed-purpose events:   0
[    0.008465] ... event mask:             0000000000000003
[    0.009750] SMP alternatives: switching to UP code
[    0.020954] Freeing SMP alternatives: 24k freed
[    0.020982] ACPI: Core revision 20100428
[    0.033528] ACPI: setting ELCR to 0200 (from 0800)
[    0.036013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036025] ftrace: allocating 21756 entries in 43 pages
[    0.044245] weird, boot CPU (#0) not listed by the BIOS.
[    0.044257] SMP motherboard not detected.
[    0.044262] Local APIC not detected. Using dummy APIC emulation.
[    0.044266] SMP disabled
[    0.044679] Brought up 1 CPUs
[    0.044692] Total of 1 processors activated (2391.88 BogoMIPS).
[    0.046512] devtmpfs: initialized
[    0.050083] regulator: core version 0.5
[    0.050116] Time:  9:47:25  Date: 01/08/11
[    0.050198] NET: Registered protocol family 16
[    0.050450] EISA bus registered
[    0.050472] ACPI: bus type pci registered
[    0.051809] PCI: PCI BIOS revision 2.10 entry at 0xf04dd, last bus=4
[    0.051814] PCI: Using configuration type 1 for base access
[    0.053979] bio: create slab <bio-0> at 0
[    0.056339] ACPI: EC: Look up EC in DSDT
[    0.081189] ACPI: Interpreter enabled
[    0.081197] ACPI: (supports S0 S1 S3 S4 S5)
[    0.081244] ACPI: Using PIC for interrupt routing
[    0.102479] ACPI: Power Resource [C14E] (on)
[    0.102636] ACPI: Power Resource [C162] (on)
[    0.102791] ACPI: Power Resource [C167] (on)
[    0.102962] ACPI: Power Resource [C16B] (on)
[    0.103035] ACPI: Power Resource [C174] (on)
[    0.103179] ACPI: Power Resource [C1F3] (off)
[    0.103317] ACPI: Power Resource [C1F4] (off)
[    0.103454] ACPI: Power Resource [C1F5] (off)
[    0.105316] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.105329] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.113908] ACPI: PCI Root Bridge [C03E] (domain 0000 [bus 00-ff])
[    0.131060] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.131067] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.131074] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.131080] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xffffffff] (ignored)
[    0.131086] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.131120] pci 0000:00:00.0: reg 10: [mem 0x60000000-0x6fffffff pref]
[    0.131248] pci 0000:00:1d.0: reg 20: [io  0x4000-0x401f]
[    0.131304] pci 0000:00:1d.1: reg 20: [io  0x4020-0x403f]
[    0.131360] pci 0000:00:1d.2: reg 20: [io  0x4040-0x405f]
[    0.131472] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
[    0.131481] pci 0000:00:1f.0: quirk: [io  0x1100-0x113f] claimed by ICH4 GPIO
[    0.131511] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.131521] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.131531] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.131540] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.131550] pci 0000:00:1f.1: reg 20: [io  0x4060-0x406f]
[    0.131560] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.131618] pci 0000:01:00.0: reg 10: [mem 0x48000000-0x4fffffff pref]
[    0.131627] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
[    0.131636] pci 0000:01:00.0: reg 18: [mem 0x40200000-0x4020ffff]
[    0.131653] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.131674] pci 0000:01:00.0: supports D1 D2
[    0.131710] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.131718] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.131726] pci 0000:00:01.0:   bridge window [mem 0x40200000-0x402fffff]
[    0.131733] pci 0000:00:01.0:   bridge window [mem 0x48000000-0x4fffffff pref]
[    0.131778] pci 0000:02:03.0: reg 10: [mem 0x40000000-0x40000fff]
[    0.131800] pci 0000:02:03.0: supports D1 D2
[    0.131805] pci 0000:02:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.131813] pci 0000:02:03.0: PME# disabled
[    0.131846] pci 0000:02:03.1: reg 10: [mem 0x40080000-0x40080fff]
[    0.131867] pci 0000:02:03.1: supports D1 D2
[    0.131872] pci 0000:02:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.131879] pci 0000:02:03.1: PME# disabled
[    0.131918] pci 0000:02:04.0: reg 10: [mem 0x40180000-0x401800ff]
[    0.131928] pci 0000:02:04.0: reg 14: [io  0x2840-0x2847]
[    0.131938] pci 0000:02:04.0: reg 18: [io  0x2000-0x20ff]
[    0.131973] pci 0000:02:04.0: supports D2
[    0.131978] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.131985] pci 0000:02:04.0: PME# disabled
[    0.132033] pci 0000:02:08.0: reg 10: [mem 0x40100000-0x40100fff]
[    0.132044] pci 0000:02:08.0: reg 14: [io  0x2800-0x283f]
[    0.132081] pci 0000:02:08.0: supports D1 D2
[    0.132086] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.132093] pci 0000:02:08.0: PME# disabled
[    0.132128] pci 0000:02:09.0: reg 10: [io  0x2400-0x24ff]
[    0.132175] pci 0000:02:09.0: supports D1 D2
[    0.132180] pci 0000:02:09.0: PME# supported from D1 D2 D3hot
[    0.132187] pci 0000:02:09.0: PME# disabled
[    0.132220] pci 0000:00:1e.0: PCI bridge to [bus 02-04] (subtractive decode)
[    0.132228] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.132236] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.132245] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.132251] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.132258] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.132329] pci_bus 0000:04: [bus 04-07] partially hidden behind transparent bridge 0000:02 [bus 02-04]
[    0.132344] pci_bus 0000:00: on NUMA node 0
[    0.132354] ACPI: PCI Interrupt Routing Table [\_SB_.C03E._PRT]
[    0.132457] ACPI: PCI Interrupt Routing Table [\_SB_.C03E.C03F._PRT]
[    0.132517] ACPI: PCI Interrupt Routing Table [\_SB_.C03E.C052._PRT]
[    0.151144] ACPI: PCI Interrupt Link [C0BA] (IRQs 5 10 *11)
[    0.151492] ACPI: PCI Interrupt Link [C0BB] (IRQs 5 10 *11)
[    0.151838] ACPI: PCI Interrupt Link [C0BC] (IRQs 5 10 *11)
[    0.152198] ACPI: PCI Interrupt Link [C0BD] (IRQs 5 10 *11)
[    0.152544] ACPI: PCI Interrupt Link [C0BE] (IRQs 5 10 *11)
[    0.152895] ACPI: PCI Interrupt Link [C0BF] (IRQs 5 10 *11)
[    0.153242] ACPI: PCI Interrupt Link [C0C0] (IRQs 5 10 *11)
[    0.153569] ACPI: PCI Interrupt Link [C0C1] (IRQs 5 10 11) *0, disabled.
[    0.153730] HEST: Table is not found!
[    0.153919] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.153930] vgaarb: loaded
[    0.154303] SCSI subsystem initialized
[    0.154487] libata version 3.00 loaded.
[    0.154605] usbcore: registered new interface driver usbfs
[    0.154636] usbcore: registered new interface driver hub
[    0.154699] usbcore: registered new device driver usb
[    0.154998] ACPI: WMI: Mapper loaded
[    0.155003] PCI: Using ACPI for IRQ routing
[    0.155012] PCI: pci_cache_line_size set to 32 bytes
[    0.155089] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.155096] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.155101] reserve RAM buffer: 000000001ffd0000 - 000000001fffffff 
[    0.155327] NetLabel: Initializing
[    0.155332] NetLabel:  domain hash size = 128
[    0.155336] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.155363] NetLabel:  unlabeled traffic allowed by default
[    0.155465] Switching to clocksource tsc
[    0.178495] AppArmor: AppArmor Filesystem Enabled
[    0.178567] pnp: PnP ACPI init
[    0.178635] ACPI: bus type pnp registered
[    0.191387] ERROR: Unable to locate IOAPIC for GSI 4
[    0.194948] ERROR: Unable to locate IOAPIC for GSI 6
[    0.199407] ERROR: Unable to locate IOAPIC for GSI 3
[    0.203032] ERROR: Unable to locate IOAPIC for GSI 7
[    0.203292] ERROR: Unable to locate IOAPIC for GSI 13
[    0.203531] ERROR: Unable to locate IOAPIC for GSI 8
[    0.203616] ERROR: Unable to locate IOAPIC for GSI 1
[    0.203706] ERROR: Unable to locate IOAPIC for GSI 12
[    0.206930] pnp: PnP ACPI: found 15 devices
[    0.206936] ACPI: ACPI bus type pnp unregistered
[    0.206945] PnPBIOS: Disabled by ACPI PNP
[    0.206974] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.206982] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.206989] system 00:00: [mem 0x00100000-0x1fffffff] could not be reserved
[    0.207009] system 00:0c: [io  0x0140-0x014f] has been reserved
[    0.207017] system 00:0c: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.207024] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.207037] system 00:0d: [io  0x04d0-0x04d1] has been reserved
[    0.207044] system 00:0d: [io  0x1000-0x1087] could not be reserved
[    0.207050] system 00:0d: [io  0x1100-0x113f] has been reserved
[    0.207057] system 00:0d: [io  0x1200-0x121f] has been reserved
[    0.207064] system 00:0d: [mem 0xffc00000-0xffc003ff] has been reserved
[    0.207076] system 00:0e: [mem 0x000cf000-0x000cffff] has been reserved
[    0.245510] pci 0000:00:1e.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.245521] pci 0000:00:1f.1: BAR 5: assigned [mem 0x28000000-0x280003ff]
[    0.245534] pci 0000:00:1f.1: BAR 5: set to [mem 0x28000000-0x280003ff] (PCI address [0x28000000-0x280003ff]
[    0.245543] pci 0000:01:00.0: BAR 6: assigned [mem 0x40220000-0x4023ffff pref]
[    0.245550] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.245557] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.245565] pci 0000:00:01.0:   bridge window [mem 0x40200000-0x402fffff]
[    0.245572] pci 0000:00:01.0:   bridge window [mem 0x48000000-0x4fffffff pref]
[    0.245584] pci 0000:02:03.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.245592] pci 0000:02:03.0: BAR 16: assigned [mem 0x2c000000-0x2fffffff]
[    0.245599] pci 0000:02:03.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.245607] pci 0000:02:03.1: BAR 16: assigned [mem 0x30000000-0x33ffffff]
[    0.245614] pci 0000:02:03.0: BAR 13: assigned [io  0x2c00-0x2cff]
[    0.245622] pci 0000:02:03.0: BAR 14: assigned [io  0x1400-0x14ff]
[    0.245629] pci 0000:02:03.1: BAR 13: assigned [io  0x1800-0x18ff]
[    0.245637] pci 0000:02:03.1: BAR 14: assigned [io  0x1c00-0x1cff]
[    0.245643] pci 0000:02:03.0: CardBus bridge to [bus 03-03]
[    0.245648] pci 0000:02:03.0:   bridge window [io  0x2c00-0x2cff]
[    0.245656] pci 0000:02:03.0:   bridge window [io  0x1400-0x14ff]
[    0.245664] pci 0000:02:03.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.245672] pci 0000:02:03.0:   bridge window [mem 0x2c000000-0x2fffffff]
[    0.245680] pci 0000:02:03.1: CardBus bridge to [bus 04-07]
[    0.245685] pci 0000:02:03.1:   bridge window [io  0x1800-0x18ff]
[    0.245692] pci 0000:02:03.1:   bridge window [io  0x1c00-0x1cff]
[    0.245700] pci 0000:02:03.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.245708] pci 0000:02:03.1:   bridge window [mem 0x30000000-0x33ffffff]
[    0.245716] pci 0000:00:1e.0: PCI bridge to [bus 02-04]
[    0.245722] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.245731] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.245739] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.245769] pci 0000:00:1e.0: setting latency timer to 64
[    0.246387] ACPI: PCI Interrupt Link [C0C0] enabled at IRQ 11
[    0.246394] PCI: setting IRQ 11 as level-triggered
[    0.246403] pci 0000:02:03.0: PCI INT A -> Link[C0C0] -> GSI 11 (level, low) -> IRQ 11
[    0.246423] pci 0000:02:03.1: PCI INT A -> Link[C0C0] -> GSI 11 (level, low) -> IRQ 11
[    0.246434] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.246440] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.246447] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.246453] pci_bus 0000:01: resource 1 [mem 0x40200000-0x402fffff]
[    0.246459] pci_bus 0000:01: resource 2 [mem 0x48000000-0x4fffffff pref]
[    0.246465] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.246471] pci_bus 0000:02: resource 1 [mem 0x40000000-0x401fffff]
[    0.246477] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.246483] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.246489] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.246495] pci_bus 0000:03: resource 0 [io  0x2c00-0x2cff]
[    0.246500] pci_bus 0000:03: resource 1 [io  0x1400-0x14ff]
[    0.246506] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.246512] pci_bus 0000:03: resource 3 [mem 0x2c000000-0x2fffffff]
[    0.246518] pci_bus 0000:04: resource 0 [io  0x1800-0x18ff]
[    0.246524] pci_bus 0000:04: resource 1 [io  0x1c00-0x1cff]
[    0.246530] pci_bus 0000:04: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.246536] pci_bus 0000:04: resource 3 [mem 0x30000000-0x33ffffff]
[    0.246636] NET: Registered protocol family 2
[    0.246787] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.247265] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.247580] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.247939] TCP: Hash tables configured (established 16384 bind 16384)
[    0.247946] TCP reno registered
[    0.247957] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.247983] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.248266] NET: Registered protocol family 1
[    0.248378] pci 0000:01:00.0: Boot video device
[    0.248429] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.248445] PCI: CLS 32 bytes, default 32
[    0.248988] speedstep-lib: frequency transition measured seems out of range (4800 nSec), falling back to a safe one of500000 nSec.
[    0.249049] cpufreq-nforce2: No nForce2 chipset.
[    0.249105] Scanning for low memory corruption every 60 seconds
[    0.249620] audit: initializing netlink socket (disabled)
[    0.249654] type=2000 audit(1294480045.248:1): initialized
[    0.268731] Trying to unpack rootfs image as initramfs...
[    0.292779] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.300879] VFS: Disk quotas dquot_6.5.2
[    0.301117] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.302975] fuse init (API version 7.14)
[    0.303235] msgmni has been set to 971
[    0.318020] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.318030] io scheduler noop registered
[    0.318035] io scheduler deadline registered
[    0.318083] io scheduler cfq registered (default)
[    0.318365] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.318416] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.319146] ACPI: AC Adapter [C1A2] (on-line)
[    0.319356] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.319380] ACPI: Sleep Button [C1A3]
[    0.319474] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.319610] ACPI: Lid Switch [C1A4]
[    0.319717] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.319726] ACPI: Power Button [PWRF]
[    0.320097] ACPI: Fan [C1F6] (off)
[    0.320490] ACPI: Fan [C1F7] (off)
[    0.320784] ACPI: Fan [C1F8] (off)
[    0.321196] ACPI: acpi_idle registered with cpuidle
[    0.321423] Marking TSC unstable due to TSC halts in idle
[    0.324219] Switching to clocksource acpi_pm
[    0.359111] thermal LNXTHERM:01: registered as thermal_zone0
[    0.359141] ACPI: Thermal Zone [TZ1] (65 C)
[    0.364875] ERST: Table is not found!
[    0.365293] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.365434] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.365619] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.366013] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.370345] ACPI: Battery Slot [C1A0] (battery absent)
[    0.370384] isapnp: Scanning for PnP cards...
[    0.381501] brd: module loaded
[    0.382823] loop: module loaded
[    0.383371] ata_piix 0000:00:1f.1: version 2.13
[    0.383399] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.388585] ACPI: PCI Interrupt Link [C0BC] enabled at IRQ 11
[    0.388601] ata_piix 0000:00:1f.1: PCI INT A -> Link[C0BC] -> GSI 11 (level, low) -> IRQ 11
[    0.388708] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.436055] scsi0 : ata_piix
[    0.444381] scsi1 : ata_piix
[    0.446021] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4060 irq 14
[    0.446028] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4068 irq 15
[    0.446931] Fixed MDIO Bus: probed
[    0.447021] PPP generic driver version 2.4.2
[    0.447202] tun: Universal TUN/TAP device driver, 1.6
[    0.447207] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.447412] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.447460] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.447490] uhci_hcd: USB Universal Host Controller Interface driver
[    0.448233] ACPI: PCI Interrupt Link [C0BA] enabled at IRQ 11
[    0.448245] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[C0BA] -> GSI 11 (level, low) -> IRQ 11
[    0.448266] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.448274] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.448384] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.448427] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00004000
[    0.448745] hub 1-0:1.0: USB hub found
[    0.448758] hub 1-0:1.0: 2 ports detected
[    0.449375] ACPI: PCI Interrupt Link [C0BD] enabled at IRQ 11
[    0.449384] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[C0BD] -> GSI 11 (level, low) -> IRQ 11
[    0.449397] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.449403] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.449477] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    0.449509] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00004020
[    0.449787] hub 2-0:1.0: USB hub found
[    0.449798] hub 2-0:1.0: 2 ports detected
[    0.449905] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[C0BC] -> GSI 11 (level, low) -> IRQ 11
[    0.449917] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.449923] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.450009] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    0.450038] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00004040
[    0.450298] hub 3-0:1.0: USB hub found
[    0.450308] hub 3-0:1.0: 2 ports detected
[    0.450563] PNP: PS/2 Controller [PNP0303:C171,PNP0f0e:C172] at 0x60,0x64 irq 1,12
[    0.451995] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.453260] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.453275] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.453338] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.453403] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.453459] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.453745] mice: PS/2 mouse device common for all mice
[    0.454051] rtc_cmos 00:09: RTC can wake from S4
[    0.454141] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.454177] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.454504] device-mapper: uevent: version 1.0.3
[    0.463985] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.468881] device-mapper: multipath: version 1.1.1 loaded
[    0.468894] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.469370] EISA: Probing bus 0 at eisa.0
[    0.469384] Cannot allocate resource for EISA slot 1
[    0.469390] Cannot allocate resource for EISA slot 2
[    0.469395] Cannot allocate resource for EISA slot 3
[    0.469400] Cannot allocate resource for EISA slot 4
[    0.469417] EISA: Detected 0 cards.
[    0.476809] cpuidle: using governor ladder
[    0.476927] cpuidle: using governor menu
[    0.477702] TCP cubic registered
[    0.478116] NET: Registered protocol family 10
[    0.478956] lo: Disabled Privacy Extensions
[    0.479482] NET: Registered protocol family 17
[    0.479590] Using IPI No-Shortcut mode
[    0.479853] PM: Resume from disk failed.
[    0.479882] registered taskstats version 1
[    0.481373] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.483460]   Magic number: 11:756:777
[    0.483565] misc rfkill: hash matches
[    0.483671] rtc_cmos 00:09: setting system clock to 2011-01-08 09:47:25 UTC (1294480045)
[    0.483678] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.483682] EDD information not available.
[    0.656609] ata1.00: ATA-7: SAMSUNG MP0402H, YQ200-06, max UDMA/100
[    0.656618] ata1.00: 78242976 sectors, multi 16: LBA48 
[    0.676272] ata1.00: configured for UDMA/100
[    0.681019] ata2.00: ATAPI: SD-R2312, 1A08, max MWDMA2
[    0.686777] ACPI: Battery Slot [C19F] (battery present)
[    0.696510] ata2.00: configured for MWDMA2
[    0.764181] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    1.104002] isapnp: No Plug & Play device found
[    1.104482] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0402H  YQ20 PQ: 0 ANSI: 5
[    1.104921] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.105297] sd 0:0:0:0: [sda] 78242976 512-byte logical blocks: (40.0 GB/37.3 GiB)
[    1.105442] sd 0:0:0:0: [sda] Write Protect is off
[    1.105449] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.105511] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.105877]  sda: sda1 sda2 <
[    1.150400] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2312 1A08 PQ: 0 ANSI: 5
[    1.152827]  sda5 >
[    1.153884] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.160531] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.161267] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.161275] Uniform CD-ROM driver Revision: 3.20
[    1.161610] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.161783] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.342932] Freeing initrd memory: 10504k freed
[    1.371320] Freeing unused kernel memory: 688k freed
[    1.373265] Write protecting the kernel text: 4932k
[    1.373349] Write protecting the kernel read-only data: 1980k
[    1.411317] udev[69]: starting version 163
[    2.069952] Floppy drive(s): fd0 is 1.44M
[    2.103828] FDC 0 is a post-1991 82077
[    2.157690] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.157699] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.158415] ACPI: PCI Interrupt Link [C0BE] enabled at IRQ 11
[    2.158426] e100 0000:02:08.0: PCI INT A -> Link[C0BE] -> GSI 11 (level, low) -> IRQ 11
[    2.246125] e100 0000:02:08.0: PME# disabled
[    2.286888] usbcore: registered new interface driver hiddev
[    2.288549] e100 0000:02:08.0: eth0: addr 0x40100000, irq 11, MAC addr 00:02:a5:bd:68:49
[    2.291301] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input4
[    2.291574] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.301535] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input5
[    2.303504] generic-usb 0003:046D:C52F.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.303823] usbcore: registered new interface driver usbhid
[    2.303828] usbhid: USB HID core driver
[    2.322831] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.859628] Adding 1568764k swap on /dev/sda5.  Priority:-1 extents:1 across:1568764k 
[   16.949991] udev[343]: starting version 163
[   17.107839] lp: driver loaded but no devices found
[   17.428937] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.763464] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.826319] intel_rng: FWH not detected
[   17.893710] parport_pc 00:05: reported by Plug and Play ACPI
[   17.893748] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   18.070936] lp0: using parport0 (interrupt-driven).
[   18.379766] Linux agpgart interface v0.103
[   18.590809] yenta_cardbus 0000:02:03.0: CardBus bridge found [0e11:004e]
[   18.590830] yenta_cardbus 0000:02:03.0: Enabling burst memory read transactions
[   18.590837] yenta_cardbus 0000:02:03.0: Using CSCINT to route CSC interrupts to PCI
[   18.590842] yenta_cardbus 0000:02:03.0: Routing CardBus interrupts to PCI
[   18.590850] yenta_cardbus 0000:02:03.0: TI: mfunc 0x01001002, devctl 0x64
[   18.694828] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   18.768405] ppdev: user-space parallel port driver
[   18.803297] irda_init()
[   18.803335] NET: Registered protocol family 23
[   18.820513] yenta_cardbus 0000:02:03.0: ISA IRQ mask 0x0438, PCI irq 11
[   18.820523] yenta_cardbus 0000:02:03.0: Socket status: 30000006
[   18.820546] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[   18.820555] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff 0x2800-0x2847 0x2c00-0x2cff
[   18.823373] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x401fffff]
[   18.823381] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x401fffff: excluding 0x40000000-0x4001ffff 0x40080000-0x4009ffff 0x40100000-0x4011ffff 0x40180000-0x4019ffff
[   18.823414] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   18.823422] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   18.900299] yenta_cardbus 0000:02:03.1: CardBus bridge found [0e11:004e]
[   18.900326] yenta_cardbus 0000:02:03.1: Using CSCINT to route CSC interrupts to PCI
[   18.900331] yenta_cardbus 0000:02:03.1: Routing CardBus interrupts to PCI
[   18.900340] yenta_cardbus 0000:02:03.1: TI: mfunc 0x01001002, devctl 0x64
[   18.922220] found SMC SuperIO Chip (devid=0x0e rev=01 base=0x002e): LPC47N252
[   18.922250] smsc_ircc_present: can't get sir_base of 0x3e8
[   18.924857] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x60000000
[   19.019111] cfg80211: Calling CRDA to update world regulatory domain
[   19.132525] yenta_cardbus 0000:02:03.1: ISA IRQ mask 0x0438, PCI irq 11
[   19.132535] yenta_cardbus 0000:02:03.1: Socket status: 30000006
[   19.132544] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   19.132567] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[   19.132575] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff 0x2800-0x2847 0x2c00-0x2cff
[   19.136091] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge window: [mem 0x40000000-0x401fffff]
[   19.136100] pcmcia_socket pcmcia_socket1: cs: memory probe 0x40000000-0x401fffff: excluding 0x40000000-0x4001ffff 0x40080000-0x4009ffff 0x40100000-0x4011ffff 0x40180000-0x4019ffff
[   19.136134] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   19.136141] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   19.202522] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9b48b1, caps: 0x884793/0x0/0x0
[   19.202537] serio: Synaptics pass-through port at isa0060/serio4/input0
[   19.211533] type=1400 audit(1294480064.222:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=667 comm="apparmor_parser"
[   19.215558] type=1400 audit(1294480064.226:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=667 comm="apparmor_parser"
[   19.216332] type=1400 audit(1294480064.230:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=667 comm="apparmor_parser"
[   19.243025] cfg80211: World regulatory domain updated:
[   19.243036]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.243043]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.243050]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.243056]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.243063]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.243069]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.259738] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   19.262997] [drm] Initialized drm 1.1.0 20060810
[   19.302852] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x140-0x14f 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   19.303785] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x4d0-0x4d7
[   19.304309] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   19.304703] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   19.305420] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x140-0x14f 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   19.306341] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x4d0-0x4d7
[   19.306784] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.307178] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.307600] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   19.307725] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   19.307850] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   19.307979] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   19.330787] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   19.330981] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   19.331107] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   19.331241] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   19.355241]  clean.
[   20.109324] type=1400 audit(1294480065.122:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=797 comm="apparmor_parser"
[   20.128532] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.131647] type=1400 audit(1294480065.142:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=797 comm="apparmor_parser"
[   20.132783] type=1400 audit(1294480065.146:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=797 comm="apparmor_parser"
[   20.290237] Maestro3 0000:02:09.0: PCI INT A -> Link[C0BA] -> GSI 11 (level, low) -> IRQ 11
[   20.298666] type=1400 audit(1294480065.310:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=805 comm="apparmor_parser"
[   20.381906] type=1400 audit(1294480065.394:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=805 comm="apparmor_parser"
[   20.403042] type=1400 audit(1294480065.414:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=805 comm="apparmor_parser"
[   20.421208] [drm] radeon defaulting to kernel modesetting.
[   20.421220] [drm] radeon kernel modesetting enabled.
[   20.421940] ACPI: PCI Interrupt Link [C0BB] enabled at IRQ 11
[   20.421951] radeon 0000:01:00.0: PCI INT A -> Link[C0BB] -> GSI 11 (level, low) -> IRQ 11
[   20.460845] [drm] initializing kernel modesetting (RV100 0x1002:0x4C59).
[   20.463625] type=1400 audit(1294480065.474:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=831 comm="apparmor_parser"
[   20.468211] [drm] register mmio base: 0x40200000
[   20.468220] [drm] register mmio size: 65536
[   20.468624] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   20.468650] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   20.468676] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   20.468712] radeon 0000:01:00.0: GTT: 256M 0x60000000 - 0x6FFFFFFF
[   20.468726] radeon 0000:01:00.0: VRAM: 64M 0x48000000 - 0x4BFFFFFF (32M used)
[   20.541037] [drm] radeon: irq initialized.
[   20.541530] [drm] Detected VRAM RAM=64M, BAR=128M
[   20.541540] [drm] RAM width 64bits DDR
[   20.546194] [TTM] Zone  kernel: Available graphics memory: 254176 kiB.
[   20.546203] [TTM] Initializing pool allocator.
[   20.546259] [drm] radeon: 32M of VRAM memory ready
[   20.546264] [drm] radeon: 256M of GTT memory ready.
[   20.582917] [drm] Loading R100 Microcode
[   20.593557] [drm] radeon: ring at 0x0000000060000000
[   20.593586] [drm] ring test succeeded in 1 usecs
[   20.594021] [drm] radeon: ib pool ready.
[   20.594191] [drm] ib test succeeded in 0 usecs
[   20.594434] [drm] Panel ID String: 1024x768                
[   20.594439] [drm] Panel Size 1024x768
[   20.594519] [drm] Default TV standard: NTSC
[   20.594523] [drm] 27.000000000 MHz TV ref clk
[   20.594529] [drm] Default TV standard: NTSC
[   20.594533] [drm] 27.000000000 MHz TV ref clk
[   20.594616] [drm] Radeon Display Connectors
[   20.594621] [drm] Connector 0:
[   20.594624] [drm]   VGA
[   20.594630] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   20.594635] [drm]   Encoders:
[   20.594638] [drm]     CRT1: INTERNAL_DAC1
[   20.594642] [drm] Connector 1:
[   20.594646] [drm]   LVDS
[   20.594649] [drm]   Encoders:
[   20.594652] [drm]     LCD1: INTERNAL_LVDS
[   20.594656] [drm] Connector 2:
[   20.594659] [drm]   S-video
[   20.594662] [drm]   Encoders:
[   20.594666] [drm]     TV1: INTERNAL_DAC2
[   20.698132] [drm] fb mappable at 0x48040000
[   20.698140] [drm] vram apper at 0x48000000
[   20.698144] [drm] size 786432
[   20.698147] [drm] fb depth is 8
[   20.698151] [drm]    pitch is 1024
[   20.797980] Console: switching to colour frame buffer device 128x48
[   20.802495] fb0: radeondrmfb frame buffer device
[   20.802500] drm: registered panic notifier
[   20.810940] Slow work thread pool: Starting up
[   20.824005] Slow work thread pool: Ready
[   20.824101] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   20.875408] usb 1-1: ath9k_htc: Transferred FW: ar9271.fw, size: 51280
[   21.347581] input: Allegro as /devices/pci0000:00/0000:00:1e.0/0000:02:09.0/input/input7
[   22.770082] psmouse serio5: ID: 10 00 64
[   22.826951] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.531917] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.587526] ath: EEPROM regdomain: 0x809c
[   26.587536] ath: EEPROM indicates we should expect a country code
[   26.587541] ath: doing EEPROM country->regdmn map search
[   26.587546] ath: country maps to regdmn code: 0x52
[   26.587551] ath: Country alpha2 being used: CN
[   26.587555] ath: Regpair used: 0x52
[   26.797201] cfg80211: Calling CRDA for country: CN
[   26.815592] Registered led device: ath9k-phy0::radio
[   26.815648] Registered led device: ath9k-phy0::assoc
[   26.815691] Registered led device: ath9k-phy0::tx
[   26.815733] Registered led device: ath9k-phy0::rx
[   26.815741] usb 1-1: ath9k_htc: USB layer initialized
[   26.815793] usbcore: registered new interface driver ath9k_hif_usb
[   26.837079] cfg80211: Regulatory domain changed to country: CN
[   26.837090]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.837097]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   26.837103]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   26.992244] audit_printk_skb: 6 callbacks suppressed
[   26.992253] type=1400 audit(1294480072.006:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1325 comm="apparmor_parser"
[   27.006562] type=1400 audit(1294480072.018:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1325 comm="apparmor_parser"
[   27.331848] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[   27.625450] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input8
[   29.626247] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.722658] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   46.867742] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   48.137597] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   68.971236] wlan0: authenticate with 00:24:01:93:27:a4 (try 1)
[   68.975234] wlan0: authenticated
[   69.063953] wlan0: associate with 00:24:01:93:27:a4 (try 1)
[   70.285789] wlan0: associate with 00:24:01:93:27:a4 (try 2)
[   70.289016] wlan0: RX AssocResp from 00:24:01:93:27:a4 (capab=0x421 status=0 aid=3)
[   70.289027] wlan0: associated
[   70.392889] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.472050] wlan0: no IPv6 routers present
[  153.850736] lo: Disabled Privacy Extensions
[ 1418.128397] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[ 1418.128411] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

Does anyone know how to fix this problem??? Thanks for answers!

---

