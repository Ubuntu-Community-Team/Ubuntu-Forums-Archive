---
title: "Desktop resume from STR crashes karmic"
date: 2010-02-23
forum: General Help
---

### Post by Byb on 2010-02-23
Hi forum users
Could I get help here for the issue in title? Thank you for any help you could provide to me.
I have a lot of data to post (I hope useful)
My first newborn koala hangs upon resume from suspend to ram.
THe motherboard is DFI AD73Pro Athlon XP 2000+ with BIOS set to S3 (STR) + MSI/nVidia gForce4 MX4000-T64 AGP4x video
On  resume the PC makes a long beep (~1s) then remains hanged (e.g. keyboard numlock led won't go On<->Off which is my favorite test to first diagnose PC health).
I added in xorg.conf ```
Option      "NvAGP" "1"
Option        "NoLogo" "true"
```as advised in this (french) post [http://doc.ubuntu-fr.org/veille_et_hibernation](http://doc.ubuntu-fr.org/veille_et_hibernation) but it doesn't help (nVidia driver reports the video is on PCI bus... is it intended?
Inside the PC I have also a PCI  VIA VT6421 SATA board with a SATA HD (for /var /home /svr /swap) and a SATA DVD burner.

I found also info [here]("http://www.******************/ubuntu-user/325140-dell-inspiron-5150-suspend-ram-not-working-still-part-one.html") on Linux Archive (**Dell Inspiron 5150 - Suspend to RAM not working... still (part	one))**.

I changed the MB jumpers so that all USB and PS2 ports are powered by 5VSB instead of default 5V because my PS2 keyboard/mouse won't wake the PC. Keyboard still won't wake the PC, but the mouse will since I inserted a PS2 to USB adapter and set the BIOS to resume on USB events.
Also, the Power button awakes the PC with same crash. I have to power off (long pressure) to restart.
The nVidia driver installed by Jockey is 93.43.13 (I followed the Ubuntu install advise to first update the packages list before I install it)
I also disabled the so called visual effects in System/Preferences/Apparence* (set to "None", as even set to "Normal" it prevents Vino to refresh remote screens.
*My system (and I) is french, so maybe my retro-translation of menu items is not very accurate.
The above post on ArchiveLinux does not speak about option Option        "NoLogo" "true"
What does it do? Should I remove nVidia driver advised by Jockey?
If this can help, here is the output of lsmod | grep "agp":
```
~$ lsmod | grep "agp"
via_agp 7932 1
agpgart 34988 2 nvidia,via_agp
```Some more lsmod, dmesg and cat/proc...
```
bybeu@Linux:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_wavefront          37332  0 
snd_cs4236             29620  0 
snd_wss_lib            26012  2 snd_wavefront,snd_cs4236
snd_via82xx            23576  2 
snd_opl3_lib           10396  2 snd_wavefront,snd_cs4236
snd_ac97_codec        101216  1 snd_via82xx
snd_hwdep               7200  2 snd_wavefront,snd_opl3_lib
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_cs4236,snd_wss_lib,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_mpu401              7016  0 
snd_page_alloc          9156  3 snd_wss_lib,snd_via82xx,snd_pcm
snd_mpu401_uart         6940  4 snd_wavefront,snd_cs4236,snd_via82xx,snd_mpu401
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
i2c_viapro              7344  0 
ip_tables              11692  1 iptable_filter
snd_seq_midi            6432  0 
nvidia               4704212  22 
via_ircc               24016  0 
snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
irda                  189564  1 via_ircc
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 32272  0 
crc_ccitt               1852  1 irda
snd                    59204  21 snd_wavefront,snd_cs4236,snd_wss_lib,snd_via82xx,snd_opl3_lib,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ns558                   5404  0 
ppdev                   6688  0 
soundcore               7264  1 snd
parport_pc             31940  1 
gameport               11368  3 snd_via82xx,ns558
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
via_agp                 7932  1 
floppy                 54916  0 
agpgart                34988  2 nvidia,via_agp
sata_via                9120  4 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
usbhid                 38208  0 

bybeu@Linux:~$ 
bybeu@Linux:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-19-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000bfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff3000 - 00000000c0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] last_pfn = 0xbfff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-protect
[    0.000000]   F0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0E8000000 mask FFC000000 write-combining
[    0.000000]   3 base 0E8000000 mask FFC000000 write-combining
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfff0000 (usable)
[    0.000000]  modified: 00000000bfff0000 - 00000000bfff3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfff3000 - 00000000c0000000 (ACPI data)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37869000 - 37fefbd6
[    0.000000] Allocated new RAMDISK: 008ad000 - 01033bd6
[    0.000000] Move RAMDISK from 0000000037869000 - 0000000037fefbd5 to 008ad000 - 01033bd5
[    0.000000] ACPI: RSDP 000f6590 00014 (v00 VIA694)
[    0.000000] ACPI: RSDT bfff3000 00028 (v01 VIA694 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP bfff3040 00074 (v01 VIA694 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT bfff30c0 02C1A (v01 VIA694 AWRDACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS bfff0000 00040
[    0.000000] 2183MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac0a8]              BRK ==> [00008a9000 - 00008ac0a8]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0001033bd6]      NEW RAMDISK ==> [00008ad000 - 0001033bd6]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x000bfff0
[    0.000000] On node 0 totalpages: 786316
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1034000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4368 pages used for memmap
[    0.000000]   HighMem zone: 554722 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3fff0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2844000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780172
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=ab78dd83-1986-49c1-ad6d-e89567bd7f71 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15728320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfff0)
[    0.000000] Memory: 3088016k/3145664k available (4567k kernel code, 56448k reserved, 2141k data, 540k init, 2236360k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575c48 - 0xc078d408   (2141 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575c48   (4567 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.806 MHz processor.
[    0.001463] Console: colour VGA+ 80x25
[    0.001469] console [tty0] enabled
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.61 BogoMIPS (lpj=6651224)
[    0.004055] Security Framework initialized
[    0.004107] AppArmor: AppArmor initialized
[    0.004118] Mount-cache hash table entries: 512
[    0.004349] Initializing cgroup subsys ns
[    0.004357] Initializing cgroup subsys cpuacct
[    0.004363] Initializing cgroup subsys memory
[    0.004377] Initializing cgroup subsys freezer
[    0.004381] Initializing cgroup subsys net_cls
[    0.004403] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004408] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004414] mce: CPU supports 4 MCE banks
[    0.004445] Performance Counters: AMD PMU driver.
[    0.004452] ------------[ cut here ]------------
[    0.004471] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
[    0.004475] Hardware name: VT8366-8233
[    0.004478] Modules linked in:
[    0.004485] Pid: 0, comm: swapper Not tainted 2.6.31-19-generic #56-Ubuntu
[    0.004488] Call Trace:
[    0.004504]  [<c014503d>] warn_slowpath_common+0x6d/0xa0
[    0.004510]  [<c011d6a3>] ? native_apic_write_dummy+0x33/0x40
[    0.004515]  [<c011d6a3>] ? native_apic_write_dummy+0x33/0x40
[    0.004521]  [<c0145085>] warn_slowpath_null+0x15/0x20
[    0.004526]  [<c011d6a3>] native_apic_write_dummy+0x33/0x40
[    0.004534]  [<c010dc3c>] perf_counters_lapic_init+0x2c/0x30
[    0.004544]  [<c0795aff>] init_hw_perf_counters+0x159/0x21c
[    0.004549]  [<c0795746>] identify_boot_cpu+0x21/0x23
[    0.004554]  [<c07958c8>] check_bugs+0xb/0xe9
[    0.004564]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
[    0.004569]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[    0.004575]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[    0.004588] ---[ end trace a7919e7f17c0a725 ]---
[    0.004594] ... version:                 0
[    0.004597] ... bit width:               48
[    0.004600] ... generic counters:        4
[    0.004602] ... value mask:              0000ffffffffffff
[    0.004605] ... max period:              00007fffffffffff
[    0.004608] ... fixed-purpose counters:  0
[    0.004610] ... counter mask:            000000000000000f
[    0.004617] Checking 'hlt' instruction... OK.
[    0.020666] SMP alternatives: switching to UP code
[    0.027891] Freeing SMP alternatives: 19k freed
[    0.027942] ACPI: Core revision 20090521
[    0.033774] ACPI: setting ELCR to 0200 (from 9a20)
[    0.035482] weird, boot CPU (#0) not listed by the BIOS.
[    0.035489] SMP motherboard not detected.
[    0.035493] Local APIC not detected. Using dummy APIC emulation.
[    0.035495] SMP disabled
[    0.035760] Brought up 1 CPUs
[    0.035764] Total of 1 processors activated (3325.61 BogoMIPS).
[    0.035782] CPU0 attaching NULL sched-domain.
[    0.036130] Booting paravirtualized kernel on bare hardware
[    0.036424] regulator: core version 0.5
[    0.036457] Time: 23:00:34  Date: 02/20/10
[    0.036548] NET: Registered protocol family 16
[    0.036745] EISA bus registered
[    0.036775] ACPI: bus type pci registered
[    0.037717] PCI: PCI BIOS revision 2.10 entry at 0xfb460, last bus=1
[    0.037721] PCI: Using configuration type 1 for base access
[    0.039020] bio: create slab <bio-0> at 0
[    0.039583] ACPI: EC: Look up EC in DSDT
[    0.044078] ACPI: Interpreter enabled
[    0.044086] ACPI: (supports S0 S3 S4 S5)
[    0.044117] ACPI: Using PIC for interrupt routing
[    0.048099] ACPI: No dock devices found.
[    0.048224] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.048289] pci 0000:00:00.0: reg 10 32bit mmio: [0xe8000000-0xebffffff]
[    0.048383] pci 0000:00:01.0: supports D1
[    0.048426] pci 0000:00:0a.0: reg 10 io port: [0xc000-0xc00f]
[    0.048434] pci 0000:00:0a.0: reg 14 io port: [0xc400-0xc40f]
[    0.048442] pci 0000:00:0a.0: reg 18 io port: [0xc800-0xc80f]
[    0.048450] pci 0000:00:0a.0: reg 1c io port: [0xcc00-0xcc0f]
[    0.048457] pci 0000:00:0a.0: reg 20 io port: [0xd000-0xd01f]
[    0.048465] pci 0000:00:0a.0: reg 24 io port: [0xd400-0xd4ff]
[    0.048473] pci 0000:00:0a.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.048522] pci 0000:00:0b.0: reg 10 io port: [0xd800-0xd8ff]
[    0.048530] pci 0000:00:0b.0: reg 14 32bit mmio: [0xef000000-0xef0000ff]
[    0.048567] pci 0000:00:0b.0: supports D1 D2
[    0.048571] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.048577] pci 0000:00:0b.0: PME# disabled
[    0.048702] pci 0000:00:11.1: reg 20 io port: [0xdc00-0xdc0f]
[    0.048780] pci 0000:00:11.2: reg 20 io port: [0xe000-0xe01f]
[    0.048851] pci 0000:00:11.3: reg 20 io port: [0xe400-0xe41f]
[    0.048908] pci 0000:00:11.5: reg 10 io port: [0xe800-0xe8ff]
[    0.049003] pci 0000:01:00.0: reg 10 32bit mmio: [0xec000000-0xecffffff]
[    0.049010] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.049029] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.049080] pci 0000:00:01.0: bridge 32bit mmio: [0xec000000-0xedffffff]
[    0.049086] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.049095] pci_bus 0000:00: on NUMA node 0
[    0.049101] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.063083] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 11 12 14 *15)
[    0.063284] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.063487] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[    0.063690] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.063985] SCSI subsystem initialized
[    0.064149] libata version 3.00 loaded.
[    0.064286] usbcore: registered new interface driver usbfs
[    0.064317] usbcore: registered new interface driver hub
[    0.064359] usbcore: registered new device driver usb
[    0.064544] ACPI: WMI: Mapper loaded
[    0.064548] PCI: Using ACPI for IRQ routing
[    0.064736] Bluetooth: Core ver 2.15
[    0.064781] NET: Registered protocol family 31
[    0.064784] Bluetooth: HCI device and connection manager initialized
[    0.064789] Bluetooth: HCI socket layer initialized
[    0.064792] NetLabel: Initializing
[    0.064795] NetLabel:  domain hash size = 128
[    0.064797] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.064818] NetLabel:  unlabeled traffic allowed by default
[    0.068114] pnp: PnP ACPI init
[    0.068151] ACPI: bus type pnp registered
[    0.072347] pnp: PnP ACPI: found 14 devices
[    0.072351] ACPI: ACPI bus type pnp unregistered
[    0.072356] PnPBIOS: Disabled by ACPI PNP
[    0.072374] system 00:00: iomem range 0xd5000-0xd7fff has been reserved
[    0.072379] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.072383] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.072387] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.072392] system 00:00: iomem range 0xbfff0000-0xbfffffff could not be reserved
[    0.072396] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.072401] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.072405] system 00:00: iomem range 0x100000-0xbffeffff could not be reserved
[    0.072410] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.072414] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.072423] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.072428] system 00:02: ioport range 0x294-0x297 has been reserved
[    0.107155] AppArmor: AppArmor Filesystem Enabled
[    0.107184] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.107187] pci 0000:00:01.0:   IO window: disabled
[    0.107194] pci 0000:00:01.0:   MEM window: 0xec000000-0xedffffff
[    0.107200] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.107217] pci 0000:00:01.0: setting latency timer to 64
[    0.107224] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.107228] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.107233] pci_bus 0000:01: resource 1 mem: [0xec000000-0xedffffff]
[    0.107237] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.107294] NET: Registered protocol family 2
[    0.107436] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.108033] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.110198] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.111281] TCP: Hash tables configured (established 131072 bind 65536)
[    0.111286] TCP reno registered
[    0.111457] NET: Registered protocol family 1
[    0.111573] Trying to unpack rootfs image as initramfs...
[    0.402804] Freeing initrd memory: 7706k freed
[    0.419060] cpufreq-nforce2: No nForce2 chipset.
[    0.419097] Scanning for low memory corruption every 60 seconds
[    0.419290] audit: initializing netlink socket (disabled)
[    0.419320] type=2000 audit(1266706834.416:1): initialized
[    0.430649] highmem bounce pool size: 64 pages
[    0.430658] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.432736] VFS: Disk quotas dquot_6.5.2
[    0.432820] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.433586] fuse init (API version 7.12)
[    0.433704] msgmni has been set to 1680
[    0.434032] alg: No test for stdrng (krng)
[    0.434052] io scheduler noop registered
[    0.434056] io scheduler anticipatory registered
[    0.434059] io scheduler deadline registered
[    0.434124] io scheduler cfq registered (default)
[    0.434144] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.434194] pci 0000:01:00.0: Boot video device
[    0.434299] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.434332] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.434511] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.434518] ACPI: Power Button [PWRF]
[    0.434589] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.434593] ACPI: Power Button [PWRB]
[    0.434658] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.434666] ACPI: Sleep Button [SLPB]
[    0.434727] fan PNP0C0B:00: registered as cooling_device0
[    0.434734] ACPI: Fan [FAN] (on)
[    0.434983] Marking TSC unstable due to TSC halts in idle
[    0.435006] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.435029] processor LNXCPU:00: registered as cooling_device1
[    0.435034] ACPI: Processor [CPU0] (supports 2 throttling states)
[    0.436055] Switched to high resolution mode on CPU 0
[    0.437728] thermal LNXTHERM:01: registered as thermal_zone0
[    0.437738] ACPI: Thermal Zone [THRM] (32 C)
[    0.437798] isapnp: Scanning for PnP cards...
[    0.791529] isapnp: No Plug & Play device found
[    0.793043] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.793167] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.793255] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.793566] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.793690] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.795112] brd: module loaded
[    0.795718] loop: module loaded
[    0.795872] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.796658] pata_via 0000:00:11.1: version 0.3.4
[    0.797276] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 15
[    0.797281] PCI: setting IRQ 15 as level-triggered
[    0.797289] pata_via 0000:00:11.1: PCI INT A -> Link[LNKA] -> GSI 15 (level, low) -> IRQ 15
[    0.797296] pata_via 0000:00:11.1: VIA VLink IRQ fixup, from 255 to 15
[    0.797573] scsi0 : pata_via
[    0.797740] scsi1 : pata_via
[    0.797791] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xdc00 irq 14
[    0.797796] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xdc08 irq 15
[    0.798275] Fixed MDIO Bus: probed
[    0.798324] PPP generic driver version 2.4.2
[    0.798502] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.798526] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.798543] uhci_hcd: USB Universal Host Controller Interface driver
[    0.799027] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[    0.799032] PCI: setting IRQ 5 as level-triggered
[    0.799040] uhci_hcd 0000:00:11.2: PCI INT D -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[    0.799053] uhci_hcd 0000:00:11.2: UHCI Host Controller
[    0.799140] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[    0.799173] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000e000
[    0.799316] usb usb1: configuration #1 chosen from 1 choice
[    0.799360] hub 1-0:1.0: USB hub found
[    0.799377] hub 1-0:1.0: 2 ports detected
[    0.799444] uhci_hcd 0000:00:11.3: PCI INT D -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[    0.799453] uhci_hcd 0000:00:11.3: UHCI Host Controller
[    0.799511] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[    0.799533] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000e400
[    0.799662] usb usb2: configuration #1 chosen from 1 choice
[    0.799698] hub 2-0:1.0: USB hub found
[    0.799711] hub 2-0:1.0: 2 ports detected
[    0.799836] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.799840] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.799933] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.800356] mice: PS/2 mouse device common for all mice
[    0.800577] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.800604] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.800752] device-mapper: uevent: version 1.0.3
[    0.800905] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.800985] device-mapper: multipath: version 1.1.0 loaded
[    0.800990] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.801178] EISA: Probing bus 0 at eisa.0
[    0.801199] Cannot allocate resource for EISA slot 4
[    0.801216] EISA: Detected 0 cards.
[    0.801336] cpuidle: using governor ladder
[    0.801398] cpuidle: using governor menu
[    0.802097] TCP cubic registered
[    0.802311] NET: Registered protocol family 10
[    0.802936] lo: Disabled Privacy Extensions
[    0.803388] NET: Registered protocol family 17
[    0.803420] Bluetooth: L2CAP ver 2.13
[    0.803422] Bluetooth: L2CAP socket layer initialized
[    0.803427] Bluetooth: SCO (Voice Link) ver 0.6
[    0.803429] Bluetooth: SCO socket layer initialized
[    0.803506] Bluetooth: RFCOMM TTY layer initialized
[    0.803510] Bluetooth: RFCOMM socket layer initialized
[    0.803513] Bluetooth: RFCOMM ver 1.11
[    0.803539] powernow-k8: Processor cpuid 680 not supported
[    0.803572] Using IPI No-Shortcut mode
[    0.803693] PM: Resume from disk failed.
[    0.803717] registered taskstats version 1
[    0.803846]   Magic number: 14:878:49
[    0.803990] rtc_cmos 00:04: setting system clock to 2010-02-20 23:00:35 UTC (1266706835)
[    0.803995] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.803998] EDD information not available.
[    0.820067] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.007962] ata1.00: ATA-7: MAXTOR STM3160215A, 3.AAD, max UDMA/100
[    1.007967] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.082866] ata1.00: configured for UDMA/100
[    1.083058] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM316021 3.AA PQ: 0 ANSI: 5
[    1.083238] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.083300] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.083374] sd 0:0:0:0: [sda] Write Protect is off
[    1.083379] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.083417] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.083627]  sda:
[    1.083794] ata2: port disabled. ignoring.
[    1.108054] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    1.130791]  sda1 sda2
[    1.131166] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.131191] Freeing unused kernel memory: 540k freed
[    1.132289] Write protecting the kernel text: 4568k
[    1.132333] Write protecting the kernel read-only data: 1836k
[    1.304245] usb 1-2: configuration #1 chosen from 1 choice
[    1.346896] usbcore: registered new interface driver hiddev
[    1.361760] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2:1.0/input/input5
[    1.361872] generic-usb 0003:0A81:0205.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:11.2-2/input0
[    1.389841] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2:1.1/input/input6
[    1.389978] generic-usb 0003:0A81:0205.0002: input,hidraw1: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:11.2-2/input1
[    1.390009] usbcore: registered new interface driver usbhid
[    1.390015] usbhid: v2.6:USB HID core driver
[    1.396677] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.396730] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.401030] 8139too Fast Ethernet driver 0.9.28
[    1.401645] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[    1.401650] PCI: setting IRQ 12 as level-triggered
[    1.401659] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    1.402816] eth0: RealTek RTL8139 at 0xd800, 00:17:3f:9b:62:92, IRQ 12
[    1.406421] sata_via 0000:00:0a.0: version 2.4
[    1.406955] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    1.406960] PCI: setting IRQ 11 as level-triggered
[    1.406968] sata_via 0000:00:0a.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.407063] sata_via 0000:00:0a.0: routed to hard irq line 11
[    1.407202] scsi2 : sata_via
[    1.407316] scsi3 : sata_via
[    1.407399] scsi4 : sata_via
[    1.407465] ata3: SATA max UDMA/133 port i16@0xc000 bmdma 0xd000 irq 11
[    1.407470] ata4: SATA max UDMA/133 port i16@0xc400 bmdma 0xd008 irq 11
[    1.407474] ata5: PATA max UDMA/133 port i16@0xc800 bmdma 0xd010 irq 11
[    1.484670] Linux agpgart interface v0.103
[    1.488000] Floppy drive(s): fd0 is 1.44M
[    1.588682] FDC 0 is a post-1991 82077
[    1.736088] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.744343] ata3.00: ATA-8: SAMSUNG HD321KJ, CP100-10, max UDMA7
[    1.744348] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.752389] ata3.00: configured for UDMA/133
[    1.752563] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD321KJ  CP10 PQ: 0 ANSI: 5
[    1.752811] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.752879] sd 2:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.752952] sd 2:0:0:0: [sdb] Write Protect is off
[    1.752957] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.752995] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.753206]  sdb: sdb1 sdb2 sdb3 sdb4
[    1.797085] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.072087] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.080246] ata4.00: ATAPI: PIONEER DVD-RW  DVR-215, 1.22, max UDMA/66
[    2.096246] ata4.00: configured for UDMA/66
[    2.120615] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-215  1.22 PQ: 0 ANSI: 5
[    2.162686] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.162695] Uniform CD-ROM driver Revision: 3.20
[    2.162884] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.162995] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    2.340387] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[    2.347938] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[    3.171839] xor: automatically using best checksumming function: pIII_sse
[    3.188025]    pIII_sse  :  2275.000 MB/sec
[    3.188029] xor: using function: pIII_sse (2275.000 MB/sec)
[    3.192794] device-mapper: dm-raid45: initialized v0.2594b
[    3.670824] PM: Starting manual resume from disk
[    3.670834] PM: Resume from partition 8:20
[    3.670836] PM: Checking hibernation image.
[    3.671134] PM: Resume from disk failed.
[    3.688486] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.688496] EXT4-fs (sda1): write access will be enabled during recovery
[    3.697758] EXT4-fs (sda1): barriers enabled
[    3.721019] kjournald2 starting: pid 356, dev sda1:8, commit interval 5 seconds
[    3.721056] EXT4-fs (sda1): delayed allocation enabled
[    3.721061] EXT4-fs: file extents enabled
[    3.748759] EXT4-fs: mballoc enabled
[    3.748789] EXT4-fs (sda1): recovery complete
[    3.749207] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.520903] type=1505 audit(1266706839.216:2): operation="profile_load" pid=379 name=/usr/share/gdm/guest-session/Xsession
[    4.531328] type=1505 audit(1266706839.224:3): operation="profile_load" pid=380 name=/sbin/dhclient3
[    4.531734] type=1505 audit(1266706839.224:4): operation="profile_load" pid=380 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.531963] type=1505 audit(1266706839.224:5): operation="profile_load" pid=380 name=/usr/lib/connman/scripts/dhclient-script
[    4.591871] type=1505 audit(1266706839.284:6): operation="profile_load" pid=381 name=/usr/bin/evince
[    4.599657] type=1505 audit(1266706839.292:7): operation="profile_load" pid=381 name=/usr/bin/evince-previewer
[    4.605444] type=1505 audit(1266706839.300:8): operation="profile_load" pid=381 name=/usr/bin/evince-thumbnailer
[    4.636465] type=1505 audit(1266706839.332:9): operation="profile_load" pid=383 name=/usr/lib/cups/backend/cups-pdf
[    4.636983] type=1505 audit(1266706839.332:10): operation="profile_load" pid=383 name=/usr/sbin/cupsd
[    5.527860] Adding 3100536k swap on /dev/sdb4.  Priority:-1 extents:1 across:3100536k 
[    6.121139] EXT4-fs (sda1): internal journal on sda1:8
[    6.243394] EXT4-fs (sdb1): barriers enabled
[    6.244854] kjournald2 starting: pid 435, dev sdb1:8, commit interval 5 seconds
[    6.245129] EXT4-fs (sdb1): internal journal on sdb1:8
[    6.245135] EXT4-fs (sdb1): delayed allocation enabled
[    6.245140] EXT4-fs: file extents enabled
[    6.253339] EXT4-fs: mballoc enabled
[    6.253365] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    6.968149] udev: starting version 147
[    7.339445] EXT4-fs (sda2): barriers enabled
[    7.546735] kjournald2 starting: pid 598, dev sda2:8, commit interval 5 seconds
[    7.685427] EXT4-fs (sda2): internal journal on sda2:8
[    7.685439] EXT4-fs (sda2): delayed allocation enabled
[    7.685443] EXT4-fs: file extents enabled
[    7.686999] EXT4-fs: mballoc enabled
[    7.687024] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    8.525805] lp: driver loaded but no devices found
[    8.622964] parport_pc 00:0a: reported by Plug and Play ACPI
[    8.623057] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    8.703997] ppdev: user-space parallel port driver
[    8.712340] lp0: using parport0 (interrupt-driven).
[    8.780571] gameport: NS558 PnP Gameport is pnp00:0c/gameport0, io 0x201, speed 994kHz
[    8.884354] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.138995] irda_init()
[    9.139024] NET: Registered protocol family 23
[   10.568253] nvidia: module license 'NVIDIA' taints kernel.
[   10.568262] Disabling lock debugging due to kernel taint
[   10.885686] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.209127] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[   11.209271] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   11.456309] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 15 (level, low) -> IRQ 15
[   11.456964] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   13.858550] EXT4-fs (sdb2): barriers enabled
[   13.867413] kjournald2 starting: pid 809, dev sdb2:8, commit interval 5 seconds
[   13.867709] EXT4-fs (sdb2): internal journal on sdb2:8
[   13.867715] EXT4-fs (sdb2): delayed allocation enabled
[   13.867719] EXT4-fs: file extents enabled
[   13.875011] EXT4-fs: mballoc enabled
[   13.875038] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[   14.063347] EXT4-fs (sdb3): barriers enabled
[   14.063635] kjournald2 starting: pid 836, dev sdb3:8, commit interval 5 seconds
[   14.063859] EXT4-fs (sdb3): internal journal on sdb3:8
[   14.063864] EXT4-fs (sdb3): delayed allocation enabled
[   14.063869] EXT4-fs: file extents enabled
[   14.113606] EXT4-fs: mballoc enabled
[   14.113649] EXT4-fs (sdb3): mounted filesystem with ordered data mode
[   15.641646] __ratelimit: 3 callbacks suppressed
[   15.641653] type=1505 audit(1266703250.336:12): operation="profile_replace" pid=961 name=/usr/share/gdm/guest-session/Xsession
[   15.644865] type=1505 audit(1266703250.340:13): operation="profile_replace" pid=962 name=/sbin/dhclient3
[   15.645273] type=1505 audit(1266703250.340:14): operation="profile_replace" pid=962 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.645504] type=1505 audit(1266703250.340:15): operation="profile_replace" pid=962 name=/usr/lib/connman/scripts/dhclient-script
[   15.659393] type=1505 audit(1266703250.352:16): operation="profile_replace" pid=963 name=/usr/bin/evince
[   15.668333] type=1505 audit(1266703250.364:17): operation="profile_replace" pid=963 name=/usr/bin/evince-previewer
[   15.674166] type=1505 audit(1266703250.368:18): operation="profile_replace" pid=963 name=/usr/bin/evince-thumbnailer
[   15.684072] type=1505 audit(1266703250.380:19): operation="profile_replace" pid=965 name=/usr/lib/cups/backend/cups-pdf
[   15.684592] type=1505 audit(1266703250.380:20): operation="profile_replace" pid=965 name=/usr/sbin/cupsd
[   15.688302] type=1505 audit(1266703250.384:21): operation="profile_replace" pid=966 name=/usr/sbin/tcpdump
[   16.201189] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   18.979449] NVRM: not using NVAGP, an AGPGART backend is loaded!
[   26.608058] eth0: no IPv6 routers present

bybeu@Linux:~$ cat  /proc/driver/nvidia/agp/status
Status:      Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.        
bybeu@Linux:~$
```Blacklisting via_agp in modprobe.conf won't work
Just tried: ```

> # mv /lib/modules/'uname -r'/kernel/drivers/char/agp/via-agp.ko /root
> # depmod -a
> # update-initramfs -u
```reboot, same  :cry:

Is it risky to leave the PC in this state? If I disable the nvidia driver now, I won't get no screen?
Now cat  /proc/driver/nvidia/agp/status says 
Status: enabled
Driver: NVIDIA
AGP rate 4x
Fast writes disabled
sba disabled

Should I revert this last change?
I am not really sure this is a video issue.

---

