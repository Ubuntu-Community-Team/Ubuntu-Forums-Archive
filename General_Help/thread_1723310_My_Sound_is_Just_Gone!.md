---
title: "My Sound is Just Gone!?"
date: 2011-04-06
forum: General Help
---

### Post by sponsoredwalk on 2011-04-06
Hi I'm on Xubuntu (10.4 I think) using Xfce 4 & my sound just went & I've been unable to get it back, trying a lot of things I've read on fora in 
the process, basically I think I'll have to start a new post giving you
my info to find out what the problem is. The sound originally worked fine
& it disappearing randomly like this is strange :(

My lspci output is:

> 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)


If I type 

aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
uname -a

I get:

> 
c@ubuntu:~$ aplay -l
aplay: device_list:235: no soundcards found...
c@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
c@ubuntu:~$ aplay -l
aplay: device_list:235: no soundcards found...
c@ubuntu:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
c@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
c@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux


If I type 

grub-install -v 

I get:
> grub-install -v
grub-install.real (GRUB) 1.98+20100804-5ubuntu3


& If I type dmesg I get:

> c@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-28-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
[    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
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
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ffae000 (usable)
[    0.000000]  modified: 000000001ffae000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ffae000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ffae000 page 4k
[    0.000000] kernel direct mapping tables up to 1ffae000 @ 15000-1a000
[    0.000000] RAMDISK: 175bc000 - 18003000
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 1fff0000 00030 (v01 DELL    CPi R   27D40709 ASL  00000061)
[    0.000000] ACPI: FACP 1fff0400 00074 (v01 DELL    CPi R   27D40709 ASL  00000061)
[    0.000000] ACPI: DSDT 1fff0c00 02E0B (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 1ffff800 00040
[    0.000000] ACPI: ASF! 1fff0800 0005B (v16 DELL    CPi R   27D40709 ASL  00000061)
[    0.000000] ACPI: BOOT 1fff07c0 00028 (v01 DELL    CPi R   27D40709 ASL  00000061)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ffae000
[    0.000000]   low ram: 0 - 1ffae000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ffae
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ffae
[    0.000000] On node 0 totalpages: 130878
[    0.000000] free_area_init_node: node 0, pgdat c0801fc0, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125902 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:deda0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129854
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2619780 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (37 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [00175bc000 - 0018003000]         RAMDISK
[    0.000000]   #4 [000009f000 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a5000 - 00009a8198]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001401000]         BOOTMEM
[    0.000000]   #11 [0001401000 - 0001401004]         BOOTMEM
[    0.000000]   #12 [0001401040 - 0001401100]         BOOTMEM
[    0.000000]   #13 [0001401100 - 0001401130]         BOOTMEM
[    0.000000]   #14 [0001401140 - 0001402940]         BOOTMEM
[    0.000000]   #15 [0001402940 - 0001402a3c]         BOOTMEM
[    0.000000]   #16 [0001402a40 - 0001402a80]         BOOTMEM
[    0.000000]   #17 [0001402a80 - 0001402ac0]         BOOTMEM
[    0.000000]   #18 [0001402ac0 - 0001402b00]         BOOTMEM
[    0.000000]   #19 [0001402b00 - 0001402b40]         BOOTMEM
[    0.000000]   #20 [0001402b40 - 0001402b80]         BOOTMEM
[    0.000000]   #21 [0001402b80 - 0001402bc0]         BOOTMEM
[    0.000000]   #22 [0001402bc0 - 0001402bd0]         BOOTMEM
[    0.000000]   #23 [0001402c00 - 0001402c10]         BOOTMEM
[    0.000000]   #24 [0001402c40 - 0001402ca7]         BOOTMEM
[    0.000000]   #25 [0001402cc0 - 0001402d27]         BOOTMEM
[    0.000000]   #26 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #27 [0001404d40 - 0001404d44]         BOOTMEM
[    0.000000]   #28 [0001404d80 - 0001404d84]         BOOTMEM
[    0.000000]   #29 [0001404dc0 - 0001404dc4]         BOOTMEM
[    0.000000]   #30 [0001404e00 - 0001404e04]         BOOTMEM
[    0.000000]   #31 [0001404e40 - 0001404ef0]         BOOTMEM
[    0.000000]   #32 [0001404f00 - 0001404fa8]         BOOTMEM
[    0.000000]   #33 [0001402d40 - 0001404d40]         BOOTMEM
[    0.000000]   #34 [0001404fc0 - 0001444fc0]         BOOTMEM
[    0.000000]   #35 [0001444fc0 - 0001464fc0]         BOOTMEM
[    0.000000]   #36 [0001465000 - 00016e4984]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 496976k/523960k available (4935k kernel code, 26536k reserved, 2337k data, 688k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07ae000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d1fde - 0xc081a7a8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d1fde   (4935 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 599.364 MHz processor.
[    0.008010] Calibrating delay loop (skipped), value calculated using timer frequency.. 1198.72 BogoMIPS (lpj=2397456)
[    0.008027] pid_max: default: 32768 minimum: 301
[    0.008077] Security Framework initialized
[    0.008135] AppArmor: AppArmor initialized
[    0.008142] Yama: becoming mindful.
[    0.008315] Mount-cache hash table entries: 512
[    0.008661] Initializing cgroup subsys ns
[    0.008672] Initializing cgroup subsys cpuacct
[    0.008686] Initializing cgroup subsys memory
[    0.008717] Initializing cgroup subsys devices
[    0.008725] Initializing cgroup subsys freezer
[    0.008733] Initializing cgroup subsys net_cls
[    0.008813] mce: CPU supports 5 MCE banks
[    0.008846] Performance Events: 
[    0.008853] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008861] no hardware sampling interrupt available.
[    0.008868] p6 PMU driver.
[    0.008914] ... version:                0
[    0.008920] ... bit width:              32
[    0.008927] ... generic registers:      2
[    0.008934] ... value mask:             00000000ffffffff
[    0.008942] ... max period:             000000007fffffff
[    0.008949] ... fixed-purpose events:   0
[    0.008956] ... event mask:             0000000000000003
[    0.013127] SMP alternatives: switching to UP code
[    0.035245] Freeing SMP alternatives: 24k freed
[    0.035271] ACPI: Core revision 20100428
[    0.044790] ACPI: setting ELCR to 0200 (from 0800)
[    0.047187] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.047201] ftrace: allocating 21762 entries in 43 pages
[    0.048132] weird, boot CPU (#0) not listed by the BIOS.
[    0.048140] SMP motherboard not detected.
[    0.048147] Local APIC not detected. Using dummy APIC emulation.
[    0.048153] SMP disabled
[    0.048453] Brought up 1 CPUs
[    0.048461] Total of 1 processors activated (1198.72 BogoMIPS).
[    0.050619] devtmpfs: initialized
[    0.055623] regulator: core version 0.5
[    0.055663] Time:  1:54:32  Date: 04/07/11
[    0.055764] NET: Registered protocol family 16
[    0.056152] EISA bus registered
[    0.056176] ACPI: bus type pci registered
[    0.090275] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.090283] PCI: Using configuration type 1 for base access
[    0.093483] bio: create slab <bio-0> at 0
[    0.095787] ACPI: EC: Look up EC in DSDT
[    0.108887] ACPI: Interpreter enabled
[    0.108911] ACPI: (supports S0 S1 S3 S4 S5)
[    0.108987] ACPI: Using PIC for interrupt routing
[    0.157231] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.157249] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.169447] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.193747] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.193759] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.193769] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.193779] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.193789] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xfed9ffff] (ignored)
[    0.193800] pci_root PNP0A03:00: host bridge window [mem 0xfee00000-0xffafffff] (ignored)
[    0.193841] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
[    0.194034] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.194116] pci 0000:00:1d.1: reg 20: [io  0xbf40-0xbf5f]
[    0.194196] pci 0000:00:1d.2: reg 20: [io  0xbf20-0xbf3f]
[    0.194283] pci 0000:00:1d.7: reg 10: [mem 0xf4fffc00-0xf4ffffff]
[    0.194365] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.194377] pci 0000:00:1d.7: PME# disabled
[    0.194509] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH4 ACPI/GPIO/TCO
[    0.194521] pci 0000:00:1f.0: quirk: [io  0x0880-0x08bf] claimed by ICH4 GPIO
[    0.194562] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.194577] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.194591] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.194605] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.194620] pci 0000:00:1f.1: reg 20: [io  0xbfa0-0xbfaf]
[    0.194634] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.194721] pci 0000:01:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.194735] pci 0000:01:00.0: reg 14: [io  0xc000-0xc0ff]
[    0.194749] pci 0000:01:00.0: reg 18: [mem 0xfcff0000-0xfcffffff]
[    0.194777] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.194812] pci 0000:01:00.0: supports D1 D2
[    0.194872] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.194883] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.194894] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.194905] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xefffffff pref]
[    0.194986] pci 0000:02:00.0: reg 10: [mem 0xfaff0000-0xfaffffff 64bit]
[    0.195064] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.195074] pci 0000:02:00.0: PME# disabled
[    0.195125] pci 0000:02:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.195156] pci 0000:02:01.0: supports D1 D2
[    0.195164] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195175] pci 0000:02:01.0: PME# disabled
[    0.195223] pci 0000:02:01.1: reg 10: [mem 0x00000000-0x00000fff]
[    0.195254] pci 0000:02:01.1: supports D1 D2
[    0.195262] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195273] pci 0000:02:01.1: PME# disabled
[    0.195335] pci 0000:02:03.0: reg 10: [mem 0xfafef000-0xfafeffff]
[    0.195456] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.195469] pci 0000:00:1e.0:   bridge window [io  0xd000-0xefff]
[    0.195480] pci 0000:00:1e.0:   bridge window [mem 0xf6000000-0xfbffffff]
[    0.195493] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.195503] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.195513] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.195582] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.195635] pci_bus 0000:07: [bus 07-0a] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.195659] pci_bus 0000:00: on NUMA node 0
[    0.195673] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.196511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.196700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.230350] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.230706] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.231056] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.231404] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.231700] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.232086] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.232243] HEST: Table is not found!
[    0.232455] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.232470] vgaarb: loaded
[    0.232996] SCSI subsystem initialized
[    0.233107] libata version 3.00 loaded.
[    0.233264] usbcore: registered new interface driver usbfs
[    0.233305] usbcore: registered new interface driver hub
[    0.233392] usbcore: registered new device driver usb
[    0.233771] ACPI: WMI: Mapper loaded
[    0.233777] PCI: Using ACPI for IRQ routing
[    0.233787] PCI: pci_cache_line_size set to 64 bytes
[    0.233893] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.233903] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.233912] reserve RAM buffer: 000000001ffae000 - 000000001fffffff 
[    0.234183] NetLabel: Initializing
[    0.234191] NetLabel:  domain hash size = 128
[    0.234196] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.234233] NetLabel:  unlabeled traffic allowed by default
[    0.234348] Switching to clocksource tsc
[    0.264777] AppArmor: AppArmor Filesystem Enabled
[    0.264826] pnp: PnP ACPI init
[    0.264886] ACPI: bus type pnp registered
[    0.289243] pnp 00:02: disabling [io  0x0800-0x0805] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.289258] pnp 00:02: disabling [io  0x0808-0x080f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.289475] pnp 00:03: disabling [io  0x0806-0x0807] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.289489] pnp 00:03: disabling [io  0x0810-0x085f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.289501] pnp 00:03: disabling [io  0x0860-0x087f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x0800-0x087f]
[    0.289701] ERROR: Unable to locate IOAPIC for GSI 12
[    0.289876] ERROR: Unable to locate IOAPIC for GSI 1
[    0.290038] ERROR: Unable to locate IOAPIC for GSI 8
[    0.290734] ERROR: Unable to locate IOAPIC for GSI 13
[    0.305779] ERROR: Unable to locate IOAPIC for GSI 4
[    0.327599] ERROR: Unable to locate IOAPIC for GSI 7
[    0.333219] pnp: PnP ACPI: found 13 devices
[    0.333227] ACPI: ACPI bus type pnp unregistered
[    0.333241] PnPBIOS: Disabled by ACPI PNP
[    0.333277] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.333289] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.333301] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.333312] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.333323] system 00:00: [mem 0x00100000-0x1ffeffff] could not be reserved
[    0.333334] system 00:00: [mem 0x1fff0000-0x1fffffff] has been reserved
[    0.333344] system 00:00: [mem 0xfeda0000-0xfedfffff] has been reserved
[    0.333355] system 00:00: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.333377] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.333396] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.333407] system 00:03: [io  0x0880-0x08bf] has been reserved
[    0.333417] system 00:03: [io  0x08c0-0x08df] has been reserved
[    0.333427] system 00:03: [io  0x08e0-0x08ff] has been reserved
[    0.333448] system 00:08: [io  0x0900-0x097f] has been reserved
[    0.373075] pci 0000:00:1e.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.373088] pci 0000:00:1f.1: BAR 5: assigned [mem 0x28000000-0x280003ff]
[    0.373104] pci 0000:00:1f.1: BAR 5: set to [mem 0x28000000-0x280003ff] (PCI address [0x28000000-0x280003ff]
[    0.373117] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc000000-0xfc01ffff pref]
[    0.373127] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.373137] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.373149] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.373160] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xefffffff pref]
[    0.373180] pci 0000:02:01.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.373191] pci 0000:02:01.0: BAR 16: assigned [mem 0x2c000000-0x2fffffff]
[    0.373201] pci 0000:02:01.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.373213] pci 0000:02:01.1: BAR 16: assigned [mem 0x30000000-0x33ffffff]
[    0.373223] pci 0000:02:01.0: BAR 0: assigned [mem 0xf6000000-0xf6000fff]
[    0.373237] pci 0000:02:01.0: BAR 0: set to [mem 0xf6000000-0xf6000fff] (PCI address [0xf6000000-0xf6000fff]
[    0.373248] pci 0000:02:01.1: BAR 0: assigned [mem 0xf6001000-0xf6001fff]
[    0.373262] pci 0000:02:01.1: BAR 0: set to [mem 0xf6001000-0xf6001fff] (PCI address [0xf6001000-0xf6001fff]
[    0.373273] pci 0000:02:01.0: BAR 13: assigned [io  0xd000-0xd0ff]
[    0.373283] pci 0000:02:01.0: BAR 14: assigned [io  0xd400-0xd4ff]
[    0.373293] pci 0000:02:01.1: BAR 13: assigned [io  0xd800-0xd8ff]
[    0.373302] pci 0000:02:01.1: BAR 14: assigned [io  0xdc00-0xdcff]
[    0.373312] pci 0000:02:01.0: CardBus bridge to [bus 03-06]
[    0.373320] pci 0000:02:01.0:   bridge window [io  0xd000-0xd0ff]
[    0.373331] pci 0000:02:01.0:   bridge window [io  0xd400-0xd4ff]
[    0.373343] pci 0000:02:01.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.373355] pci 0000:02:01.0:   bridge window [mem 0x2c000000-0x2fffffff]
[    0.373367] pci 0000:02:01.1: CardBus bridge to [bus 07-0a]
[    0.373375] pci 0000:02:01.1:   bridge window [io  0xd800-0xd8ff]
[    0.373386] pci 0000:02:01.1:   bridge window [io  0xdc00-0xdcff]
[    0.373398] pci 0000:02:01.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.373410] pci 0000:02:01.1:   bridge window [mem 0x30000000-0x33ffffff]
[    0.373421] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.373431] pci 0000:00:1e.0:   bridge window [io  0xd000-0xefff]
[    0.373444] pci 0000:00:1e.0:   bridge window [mem 0xf6000000-0xfbffffff]
[    0.373456] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.373489] pci 0000:00:1e.0: setting latency timer to 64
[    0.373510] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.374023] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.374032] PCI: setting IRQ 11 as level-triggered
[    0.374045] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.374070] pci 0000:02:01.1: enabling device (0000 -> 0003)
[    0.374084] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.374101] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.374110] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.374119] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.374128] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfdffffff]
[    0.374138] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xefffffff pref]
[    0.374147] pci_bus 0000:02: resource 0 [io  0xd000-0xefff]
[    0.374156] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xfbffffff]
[    0.374165] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.374175] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.374183] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.374193] pci_bus 0000:03: resource 0 [io  0xd000-0xd0ff]
[    0.374201] pci_bus 0000:03: resource 1 [io  0xd400-0xd4ff]
[    0.374210] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.374220] pci_bus 0000:03: resource 3 [mem 0x2c000000-0x2fffffff]
[    0.374229] pci_bus 0000:07: resource 0 [io  0xd800-0xd8ff]
[    0.374237] pci_bus 0000:07: resource 1 [io  0xdc00-0xdcff]
[    0.374246] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.374256] pci_bus 0000:07: resource 3 [mem 0x30000000-0x33ffffff]
[    0.374364] NET: Registered protocol family 2
[    0.374559] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.375170] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.375439] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.375699] TCP: Hash tables configured (established 16384 bind 16384)
[    0.375707] TCP reno registered
[    0.375716] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.375739] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.375933] NET: Registered protocol family 1
[    0.376088] pci 0000:01:00.0: Boot video device
[    0.376120] PCI: CLS 32 bytes, default 64
[    0.376274] Simple Boot Flag at 0x79 set to 0x1
[    0.376489] cpufreq-nforce2: No nForce2 chipset.
[    0.376562] Scanning for low memory corruption every 60 seconds
[    0.376990] audit: initializing netlink socket (disabled)
[    0.377016] type=2000 audit(1302141272.372:1): initialized
[    0.415357] Trying to unpack rootfs image as initramfs...
[    0.454826] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.467118] VFS: Disk quotas dquot_6.5.2
[    0.467335] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.475184] fuse init (API version 7.14)
[    0.475505] msgmni has been set to 970
[    1.457517] Freeing initrd memory: 10524k freed
[    1.483842] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.483854] io scheduler noop registered
[    1.483861] io scheduler deadline registered
[    1.483913] io scheduler cfq registered (default)
[    1.484367] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.484442] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.485534] ACPI: AC Adapter [AC] (off-line)
[    1.485812] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.486443] ACPI: Lid Switch [LID]
[    1.486604] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.486620] ACPI: Power Button [PBTN]
[    1.486781] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.486794] ACPI: Sleep Button [SBTN]
[    1.487309] ACPI: acpi_idle registered with cpuidle
[    1.487912] Marking TSC unstable due to TSC halts in idle
[    1.492059] Switching to clocksource acpi_pm
[    1.513741] thermal LNXTHERM:01: registered as thermal_zone0
[    1.513770] ACPI: Thermal Zone [THM] (29 C)
[    1.520238] ERST: Table is not found!
[    1.520634] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.520798] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521925] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.529893] brd: module loaded
[    1.531683] loop: module loaded
[    1.532082] isapnp: Scanning for PnP cards...
[    1.540266] ata_piix 0000:00:1f.1: version 2.13
[    1.540293] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.609932] ACPI: Battery Slot [BAT1] (battery absent)
[    1.610280] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    1.610295] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.610386] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.614896] scsi0 : ata_piix
[    1.615138] scsi1 : ata_piix
[    1.616950] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.616961] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.618171] Fixed MDIO Bus: probed
[    1.618297] PPP generic driver version 2.4.2
[    1.618434] tun: Universal TUN/TAP device driver, 1.6
[    1.618441] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.618676] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.619185] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    1.619199] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    1.619230] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.619240] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.619350] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.619414] ehci_hcd 0000:00:1d.7: debug port 1
[    1.623296] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.632080] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    1.636753] ACPI: Battery Slot [BAT0] (battery present)
[    1.680263] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.680638] hub 1-0:1.0: USB hub found
[    1.680654] hub 1-0:1.0: 6 ports detected
[    1.680848] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.680890] uhci_hcd: USB Universal Host Controller Interface driver
[    1.680952] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.680969] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.680979] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.681088] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.681127] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    1.681487] hub 2-0:1.0: USB hub found
[    1.681501] hub 2-0:1.0: 2 ports detected
[    1.681648] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.681664] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.681673] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.681791] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.681832] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    1.682181] hub 3-0:1.0: USB hub found
[    1.682194] hub 3-0:1.0: 2 ports detected
[    1.682817] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    1.682831] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.682847] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.682857] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.682964] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.683004] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    1.683406] hub 4-0:1.0: USB hub found
[    1.683420] hub 4-0:1.0: 2 ports detected
[    1.683780] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.732052] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.732073] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.732404] mice: PS/2 mouse device common for all mice
[    1.732955] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.732987] rtc0: alarms up to one day, 114 bytes nvram
[    1.733372] device-mapper: uevent: version 1.0.3
[    1.821641] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX830E, KDK3, max UDMA/33
[    1.821876] ata1.00: ATA-6: HTS726060M9AT00, MH4OA60A, max UDMA/100
[    1.821887] ata1.00: 117210240 sectors, multi 8: LBA48 
[    1.822475] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.866434] ata2.00: configured for UDMA/33
[    1.866506] device-mapper: multipath: version 1.1.1 loaded
[    1.866515] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.866892] EISA: Probing bus 0 at eisa.0
[    1.866942] EISA: Detected 0 cards.
[    1.910644] cpuidle: using governor ladder
[    1.910880] cpuidle: using governor menu
[    1.911768] TCP cubic registered
[    1.912270] NET: Registered protocol family 10
[    1.913358] lo: Disabled Privacy Extensions
[    1.914054] NET: Registered protocol family 17
[    1.944691] ata1.00: configured for UDMA/100
[    1.946091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.003507] isapnp: No Plug & Play device found
[    2.003820] scsi 0:0:0:0: Direct-Access     ATA      HTS726060M9AT00  MH4O PQ: 0 ANSI: 5
[    2.004273] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.004649] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.005019] sd 0:0:0:0: [sda] Write Protect is off
[    2.005030] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.005104] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.005396] scsi 1:0:0:0: CD-ROM            SONY     CDRW/DVD CRX830E KDK3 PQ: 0 ANSI: 5
[    2.006075]  sda:sr0: scsi3-mmc drive: 15x/24x writer cd/rw xa/form2 cdda tray
[    2.007061] Uniform CD-ROM driver Revision: 3.20
[    2.007332] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.007489] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.031399]  sda1
[    2.031971] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.059552] Using IPI No-Shortcut mode
[    2.059791] PM: Resume from disk failed.
[    2.059821] registered taskstats version 1
[    2.060200]   Magic number: 7:505:912
[    2.060355] rtc_cmos 00:06: setting system clock to 2011-04-07 01:54:34 UTC (1302141274)
[    2.060365] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.060372] EDD information not available.
[    2.060536] Freeing unused kernel memory: 688k freed
[    2.061503] Write protecting the kernel text: 4936k
[    2.061626] Write protecting the kernel read-only data: 1980k
[    2.105465] udev[68]: starting version 163
[    2.802621] tg3.c:v3.110 (April 9, 2010)
[    2.802663] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.851928] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95705A50) rev 3001] (PCI:33MHz:32-bit) MAC address 00:0f:1f:bf:ed:55
[    2.851943] tg3 0000:02:00.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.851955] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.851965] tg3 0000:02:00.0: eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    3.263615] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[   20.873146] udev[329]: starting version 163
[   21.682221] lp: driver loaded but no devices found
[   21.735705] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.859934] parport_pc 00:0c: reported by Plug and Play ACPI
[   21.859988] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   21.956227] lp0: using parport0 (interrupt-driven).
[   21.966378] ppdev: user-space parallel port driver
[   22.064672] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.220896] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1d/LNXVIDEO:00/input/input4
[   22.221068] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.386289] Linux agpgart interface v0.103
[   22.422402] intel_rng: FWH not detected
[   22.619644] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   22.628911] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   22.851100] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input5
[   22.872315] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input6
[   22.896683] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:011d]
[   22.896708] yenta_cardbus 0000:02:01.0: O2: enabling read prefetch/write burst
[   22.917068] cfg80211: Calling CRDA to update world regulatory domain
[   23.024756] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0438, PCI irq 11
[   23.024762] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   23.024768] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   23.024782] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [io  0xd000-0xefff]
[   23.024787] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: excluding 0xd000-0xd0ff 0xd400-0xd4ff 0xd800-0xd8ff 0xdc00-0xdcff
[   23.031046] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xf6000000-0xfbffffff]
[   23.031051] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff
[   23.031070] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   23.031075] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   23.031754] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:011d]
[   23.047887] lib80211: common routines for IEEE802.11 drivers
[   23.047893] lib80211_crypt: registered algorithm 'NULL'
[   23.156771] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0438, PCI irq 11
[   23.156778] yenta_cardbus 0000:02:01.1: Socket status: 30000410
[   23.156784] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   23.156802] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge window: [io  0xd000-0xefff]
[   23.156807] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xd000-0xefff: excluding 0xd000-0xd0ff 0xd400-0xd4ff 0xd800-0xd8ff 0xdc00-0xdcff
[   23.162806] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge window: [mem 0xf6000000-0xfbffffff]
[   23.162811] pcmcia_socket pcmcia_socket1: cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff
[   23.162830] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   23.162834] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   23.338302] [drm] Initialized drm 1.1.0 20060810
[   23.645832] libipw: 802.11 data/management/control stack, git-1.1.13
[   23.645838] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.779467] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   23.779473] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   23.779956] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   23.779961] PCI: setting IRQ 5 as level-triggered
[   23.779968] ipw2100 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   23.781473] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   23.964966] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   23.966015] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   23.966478] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   23.966566] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.967002] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xf0000-0xfffff
[   23.967083] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   23.967166] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   23.967249] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.056079] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
[   24.056093] pcmcia_socket pcmcia_socket1: cs: memory probe 0xfb400000-0xfbffffff:
[   24.062280] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   24.063333] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   24.063790] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   24.063871] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   24.064327] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xf0000-0xfffff
[   24.064400] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   24.064472] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   24.064547] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   24.082887]  clean.
[   24.083476] pcmcia 1.0: pcmcia: registering new device pcmcia1.0 (IRQ: 3)
[   24.141350] cfg80211: World regulatory domain updated:
[   24.141359]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.141363]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.141367]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.141371]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.141374]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.141378]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.360790] [drm] radeon defaulting to kernel modesetting.
[   24.360795] [drm] radeon kernel modesetting enabled.
[   24.360881] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   24.364948] [drm] initializing kernel modesetting (RV250 0x1002:0x4C66).
[   24.365369] [drm] register mmio base: 0xFCFF0000
[   24.365372] [drm] register mmio size: 65536
[   24.365650] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   24.365669] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   24.365698] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   24.365730] radeon 0000:01:00.0: GTT: 128M 0xE0000000 - 0xE7FFFFFF
[   24.365741] radeon 0000:01:00.0: VRAM: 128M 0xE8000000 - 0xEFFFFFFF (32M used)
[   24.365782] [drm] radeon: irq initialized.
[   24.366928] [drm] Detected VRAM RAM=128M, BAR=128M
[   24.366934] [drm] RAM width 64bits DDR
[   24.367048] [TTM] Zone  kernel: Available graphics memory: 254106 kiB.
[   24.367051] [TTM] Initializing pool allocator.
[   24.367079] [drm] radeon: 32M of VRAM memory ready
[   24.367082] [drm] radeon: 128M of GTT memory ready.
[   24.367189] [drm] Loading R200 Microcode
[   24.492544] [drm] radeon: ring at 0x00000000E0000000
[   24.492568] [drm] ring test succeeded in 1 usecs
[   24.492837] [drm] radeon: ib pool ready.
[   24.492953] [drm] ib test succeeded in 0 usecs
[   24.494095] [drm] DFP table revision: 3
[   24.494940] [drm] Panel ID String: 6J5644141XB
[   24.494942]             
[   24.494945] [drm] Panel Size 1024x768
[   24.495128] [drm] Default TV standard: NTSC
[   24.495131] [drm] 27.000000000 MHz TV ref clk
[   24.495134] [drm] Default TV standard: NTSC
[   24.495136] [drm] 27.000000000 MHz TV ref clk
[   24.495293] [drm] Radeon Display Connectors
[   24.495296] [drm] Connector 0:
[   24.495298] [drm]   VGA
[   24.495301] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   24.495304] [drm]   Encoders:
[   24.495306] [drm]     CRT1: INTERNAL_DAC1
[   24.495308] [drm] Connector 1:
[   24.495310] [drm]   DVI-D
[   24.495312] [drm]   HPD1
[   24.495315] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   24.495317] [drm]   Encoders:
[   24.495319] [drm]     DFP1: INTERNAL_TMDS1
[   24.495321] [drm] Connector 2:
[   24.495323] [drm]   LVDS
[   24.495325] [drm]   Encoders:
[   24.495327] [drm]     LCD1: INTERNAL_LVDS
[   24.495329] [drm] Connector 3:
[   24.495331] [drm]   S-video
[   24.495333] [drm]   Encoders:
[   24.495335] [drm]     TV1: INTERNAL_DAC2
[   24.509395] [drm] radeon: power management initialized
[   24.551772] [drm] fb mappable at 0xE8040000
[   24.551777] [drm] vram apper at 0xE8000000
[   24.551779] [drm] size 786432
[   24.551781] [drm] fb depth is 8
[   24.551783] [drm]    pitch is 1024
[   24.587040] [drm] crtc 1 is connected to a TV
[   24.642632] Console: switching to colour frame buffer device 100x37
[   24.645630] fb0: radeondrmfb frame buffer device
[   24.645633] drm: registered panic notifier
[   24.646829] Slow work thread pool: Starting up
[   24.646886] Slow work thread pool: Ready
[   24.646898] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   24.695323] type=1400 audit(1302137697.133:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=559 comm="apparmor_parser"
[   24.696164] type=1400 audit(1302137697.133:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=559 comm="apparmor_parser"
[   24.696609] type=1400 audit(1302137697.133:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=559 comm="apparmor_parser"
[   24.697284] type=1400 audit(1302137697.133:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=586 comm="apparmor_parser"
[   24.698084] type=1400 audit(1302137697.133:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=586 comm="apparmor_parser"
[   24.698530] type=1400 audit(1302137697.133:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=586 comm="apparmor_parser"
[   24.699316] type=1400 audit(1302137697.133:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=685 comm="apparmor_parser"
[   24.700140] type=1400 audit(1302137697.137:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[   24.700579] type=1400 audit(1302137697.137:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[   26.718876] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
[   26.875749] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   27.683168] type=1400 audit(1302137700.117:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=802 comm="apparmor_parser"
[   29.498928] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.513741] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.537409] [drm] crtc 1 is connected to a TV
[   32.375595] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
[   40.611291] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
[  153.312430] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  163.464045] eth1: no IPv6 routers present


Hopefully that's enough, thanks for any possible help! :P

---

### Post by sponsoredwalk on 2011-04-08
Bump? :(

---

### Post by mariost on 2011-04-29
Can't help you much, but take a look at my [sound problem thread]("http://ubuntuforums.org/showthread.php?t=1603735") , maybe it can help you somehow.

---

### Post by KegHead on 2011-04-29
Hi!

Have you upgraded recently;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Also:

system..admin..additional drivers  

and

system..preferences..sound

KegHead

---

