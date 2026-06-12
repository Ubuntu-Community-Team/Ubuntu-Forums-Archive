---
title: "&quot;Suspend&quot; causes white screen..."
date: 2012-04-10
forum: General Help
---

### Post by Eirreann on 2012-04-10
Okay, just got Ubuntu installed full on my laptop as the only present OS.  Anyway, I have it set to "suspend" when I close the lid, however, whenever I do so and open the lid again, I'm presented with a blank, white screen, except for the bottom which has short black vertical lines on it.  After waiting for a bit the screen starts flashing random colours (orange, green, blue, white, red, etc...) until I finally just have to force it to shut down and reboot.
Anyone know a fix for this?

---

### Post by abyrne on 2012-04-10
I can't put my finger on it, but it seems like we've met before. :tongue:

Suspend on Ubuntu hasn't always been 100% solid. But the flashing colors scenario leads me to believe that it's a graphics card issue. What graphics card are you using?

---

### Post by Eirreann on 2012-04-11
> **abyrne said:**
> I can't put my finger on it, but it seems like we've met before. :tongue:

Suspend on Ubuntu hasn't always been 100% solid. But the flashing colors scenario leads me to believe that it's a graphics card issue. What graphics card are you using?

I'm using an Nvidia GeForce FX Go5200.  And now the white screen happens whenever I start up, shut down, or hibernate (although when I start up or shut down it will eventually sort itself out)

---

### Post by Runthantrip on 2012-04-11
There seems to be some issues with the latest 11.10 kernel and Nvidiea drivers. make sure that the video card driver is up to date. that might fix your problem.

---

### Post by Eirreann on 2012-04-11
> **Runthantrip said:**
> There seems to be some issues with the latest 11.10 kernel and Nvidiea drivers. make sure that the video card driver is up to date. that might fix your problem.

I tried installing each of the drivers available in the Additional Drivers section of Settings, and had the same problem with all of them.
Now, I only just installed Ubuntu on here so I don't have many programmes installed yet; do you think that the problem would be resolved if I just stuck in the disc again and re-installed it?

---

### Post by Eirreann on 2012-04-11
It's amazing how fast my threads fall off of the front page... Still experiencing white screens!  I'm going to try re-installing Ubuntu tonight to see if that helps (it didn't used to white screen all the time, so I'm thinking that it was a bug from when I installed it on this new hard drive)

---

### Post by abyrne on 2012-04-12
I assume the reinstall didn't work. Nvidia drivers have always been notoriously buggy in Linux, and suspend/hibernation functions have been buggy by themselves sometimes as well. I think your problem has been replicated by another user in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/361853"). 

You wouldn't happen to be using a Dell Inspiron 8600, are you?

Also, could you post the output of the command
```
dmesg
```
and install a tool called tree and post the output of the second command
```

sudo apt-get install tree 
tree /usr/share/hal/

```

---

### Post by Eirreann on 2012-04-12
> **abyrne said:**
> I assume the reinstall didn't work. Nvidia drivers have always been notoriously buggy in Linux, and suspend/hibernation functions have been buggy by themselves sometimes as well. I think your problem has been replicated by another user in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/361853"). 

You wouldn't happen to be using a Dell Inspiron 8600, are you?

Also, could you post the output of the command
```
dmesg
```
I am, actually.... so you are guessing it is a motherboard problem?
Also, when you wanted the output of that command, did you want the huge wall of text that appeared after I typed it in?  (And yeah, reinstalling did absolutely nothing but knock out my boot logo)
And I looked at that link and it seems like they were able to figure it out somehow, but little of what the author says makes sense to me (utter noob here...) could you possibly explain it to me?

---

### Post by abyrne on 2012-04-12
> Also, when you wanted the output of that command, did you want the huge wall of text that appeared after I typed it in?

Yeah, in retrospect, it might be better to output the command into a txt file
```
dmesg > dmesg.txt
```
The resulting txt file will be located in your home folder. Just attach that file to a post. Also, could you install the "tree" tool with the 1st following command and post the output of the second following command.
```
sudo apt-get install tree 
tree /usr/share/hal/
```

---

### Post by Eirreann on 2012-04-12
Okay, here's the output of the tree command:
```
/usr/share/hal/
&#9492;&#9472;&#9472; fdi
    &#9500;&#9472;&#9472; information
    &#9474;   &#9492;&#9472;&#9472; 20thirdparty
    &#9474;       &#9500;&#9472;&#9472; 20-libmtp9.fdi
    &#9474;       &#9492;&#9472;&#9472; 31-apple-mobile-device.fdi
    &#9500;&#9472;&#9472; policy
    &#9474;   &#9492;&#9472;&#9472; 10osvendor
    &#9474;       &#9492;&#9472;&#9472; 25-ntfs-3g-policy.fdi
    &#9492;&#9472;&#9472; preprobe
        &#9492;&#9472;&#9472; 10osvendor
            &#9492;&#9472;&#9472; 20-libsane.fdi

7 directories, 4 files

```

And the .txt file from the dmesg command was too big to attach, so here it is, pasted:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 (Ubuntu 3.0.0-17.30-generic 3.0.22)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  BIOS-e820: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Dell Computer Corporation Inspiron 8600                   /0Y4572, BIOS A08 04/26/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365ec000 - 372ee000
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7fff0000 00028 (v01 DELL    CPi R   27D4041A ASL  00000061)
[    0.000000] ACPI: FACP 7fff0400 00074 (v01 DELL    CPi R   27D4041A ASL  00000061)
[    0.000000] ACPI: DSDT 7fff0c00 02D70 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 7ffff800 00040
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffae
[    0.000000] On node 0 totalpages: 524093
[    0.000000] free_area_init_node: node 0, pgdat c17b54c0, node_mem_map f55ec200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294560 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7eda0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5000000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519997
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=e37bb348-ae78-4c2d-a665-8a7657fe93c5 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8387040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffae)
[    0.000000] Memory: 2048024k/2096824k available (5340k kernel code, 48348k reserved, 2595k data, 696k init, 1187520k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc15371c4 - 0xc17c0140   (2595 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15371c4   (5340 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f4406000 soft=f4408000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 599.484 MHz processor.
[    0.008008] Calibrating delay loop (skipped), value calculated using timer frequency.. 1198.96 BogoMIPS (lpj=2397936)
[    0.008025] pid_max: default: 32768 minimum: 301
[    0.008099] Security Framework initialized
[    0.008162] AppArmor: AppArmor initialized
[    0.008169] Yama: becoming mindful.
[    0.008356] Mount-cache hash table entries: 512
[    0.008777] Initializing cgroup subsys cpuacct
[    0.008798] Initializing cgroup subsys memory
[    0.008832] Initializing cgroup subsys devices
[    0.008840] Initializing cgroup subsys freezer
[    0.008848] Initializing cgroup subsys net_cls
[    0.008855] Initializing cgroup subsys blkio
[    0.008882] Initializing cgroup subsys perf_event
[    0.008968] Disabled fast string operations
[    0.008989] mce: CPU supports 5 MCE banks
[    0.009579] SMP alternatives: switching to UP code
[    0.032456] Freeing SMP alternatives: 24k freed
[    0.032479] ACPI: Core revision 20110413
[    0.038289] ACPI: setting ELCR to 0200 (from 0800)
[    0.040030] ftrace: allocating 24903 entries in 49 pages
[    0.044129] weird, boot CPU (#0) not listed by the BIOS.
[    0.044137] SMP motherboard not detected.
[    0.044144] Local APIC not detected. Using dummy APIC emulation.
[    0.044150] SMP disabled
[    0.044156] Performance Events: 
[    0.044163] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.044170] no hardware sampling interrupt available.
[    0.044178] p6 PMU driver.
[    0.044189] ... version:                0
[    0.044195] ... bit width:              32
[    0.044201] ... generic registers:      2
[    0.044207] ... value mask:             00000000ffffffff
[    0.044214] ... max period:             000000007fffffff
[    0.044220] ... fixed-purpose events:   0
[    0.044226] ... event mask:             0000000000000003
[    0.045333] Brought up 1 CPUs
[    0.045341] Total of 1 processors activated (1198.96 BogoMIPS).
[    0.045621] devtmpfs: initialized
[    0.054464] print_constraints: dummy: 
[    0.054503] Time: 13:07:22  Date: 04/12/12
[    0.054625] NET: Registered protocol family 16
[    0.055004] EISA bus registered
[    0.055032] ACPI: bus type pci registered
[    0.089197] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.089205] PCI: Using configuration type 1 for base access
[    0.092804] bio: create slab <bio-0> at 0
[    0.095076] ACPI: EC: Look up EC in DSDT
[    0.103952] ACPI: Interpreter enabled
[    0.103989] ACPI: (supports S0 S1 S3 S4 S5)
[    0.104077] ACPI: Using PIC for interrupt routing
[    0.133074] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.133083] HEST: Table not found.
[    0.133101] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.139866] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.153253] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.153266] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.153277] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.153288] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.153299] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xfed9ffff] (ignored)
[    0.153310] pci_root PNP0A03:00: host bridge window [mem 0xfee00000-0xffafffff] (ignored)
[    0.153342] pci 0000:00:00.0: [8086:3340] type 0 class 0x000600
[    0.153363] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
[    0.153452] pci 0000:00:01.0: [8086:3341] type 1 class 0x000604
[    0.153552] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
[    0.153620] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.153679] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
[    0.153746] pci 0000:00:1d.1: reg 20: [io  0xbf40-0xbf5f]
[    0.153809] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
[    0.153877] pci 0000:00:1d.2: reg 20: [io  0xbf20-0xbf3f]
[    0.153951] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
[    0.153987] pci 0000:00:1d.7: reg 10: [mem 0xf4fffc00-0xf4ffffff]
[    0.154120] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.154133] pci 0000:00:1d.7: PME# disabled
[    0.154165] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.154237] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
[    0.154359] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
[    0.154385] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.154404] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.154424] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.154443] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.154463] pci 0000:00:1f.1: reg 20: [io  0xbfa0-0xbfaf]
[    0.154483] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.154542] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
[    0.154571] pci 0000:00:1f.5: reg 10: [io  0xb800-0xb8ff]
[    0.154590] pci 0000:00:1f.5: reg 14: [io  0xbc40-0xbc7f]
[    0.154609] pci 0000:00:1f.5: reg 18: [mem 0xf4fff800-0xf4fff9ff]
[    0.154628] pci 0000:00:1f.5: reg 1c: [mem 0xf4fff400-0xf4fff4ff]
[    0.154701] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.154712] pci 0000:00:1f.5: PME# disabled
[    0.154744] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
[    0.154772] pci 0000:00:1f.6: reg 10: [io  0xb400-0xb4ff]
[    0.154791] pci 0000:00:1f.6: reg 14: [io  0xb080-0xb0ff]
[    0.154883] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.154894] pci 0000:00:1f.6: PME# disabled
[    0.154943] pci 0000:01:00.0: [10de:0324] type 0 class 0x000300
[    0.154971] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfcffffff]
[    0.154989] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff pref]
[    0.155039] pci 0000:01:00.0: reg 30: [mem 0x80000000-0x8001ffff pref]
[    0.155139] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.155150] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.155162] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.155174] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.155222] pci 0000:02:00.0: [14e4:4401] type 0 class 0x000200
[    0.155251] pci 0000:02:00.0: reg 10: [mem 0xfaffe000-0xfaffffff]
[    0.155351] pci 0000:02:00.0: supports D1 D2
[    0.155359] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155371] pci 0000:02:00.0: PME# disabled
[    0.155404] pci 0000:02:01.0: [104c:ac44] type 2 class 0x000607
[    0.155434] pci 0000:02:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.155479] pci 0000:02:01.0: supports D1 D2
[    0.155487] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155499] pci 0000:02:01.0: PME# disabled
[    0.155532] pci 0000:02:01.1: [104c:8029] type 0 class 0x000c00
[    0.155562] pci 0000:02:01.1: reg 10: [mem 0xfaffd800-0xfaffdfff]
[    0.155582] pci 0000:02:01.1: reg 14: [mem 0xfaff8000-0xfaffbfff]
[    0.155677] pci 0000:02:01.1: supports D1 D2
[    0.155685] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot
[    0.155697] pci 0000:02:01.1: PME# disabled
[    0.155741] pci 0000:02:03.0: [8086:4220] type 0 class 0x000280
[    0.155771] pci 0000:02:03.0: reg 10: [mem 0xfaffc000-0xfaffcfff]
[    0.155877] pci 0000:02:03.0: PME# supported from D0 D3hot D3cold
[    0.155889] pci 0000:02:03.0: PME# disabled
[    0.155951] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.155964] pci 0000:00:1e.0:   bridge window [io  0xd000-0xefff]
[    0.155977] pci 0000:00:1e.0:   bridge window [mem 0xf6000000-0xfbffffff]
[    0.155990] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.156001] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.156019] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.156083] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.156109] pci_bus 0000:00: on NUMA node 0
[    0.156120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.156812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.156948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.157421]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.183152] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.183403] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.183646] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.183889] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.184110] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.184369] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.184692] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.184706] vgaarb: loaded
[    0.184712] vgaarb: bridge control possible 0000:01:00.0
[    0.185496] SCSI subsystem initialized
[    0.185618] libata version 3.00 loaded.
[    0.185775] usbcore: registered new interface driver usbfs
[    0.185816] usbcore: registered new interface driver hub
[    0.185899] usbcore: registered new device driver usb
[    0.186184] PCI: Using ACPI for IRQ routing
[    0.186195] PCI: pci_cache_line_size set to 64 bytes
[    0.186313] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.186323] reserve RAM buffer: 000000007ffae000 - 000000007fffffff 
[    0.186644] NetLabel: Initializing
[    0.186651] NetLabel:  domain hash size = 128
[    0.186657] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.186690] NetLabel:  unlabeled traffic allowed by default
[    0.186852] Switching to clocksource pit
[    0.207179] AppArmor: AppArmor Filesystem Enabled
[    0.207261] pnp: PnP ACPI init
[    0.207310] ACPI: bus type pnp registered
[    0.214291] pnp 00:00: [mem 0x00000000-0x0009fbff]
[    0.214302] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
[    0.214311] pnp 00:00: [mem 0x000c0000-0x000cffff]
[    0.214319] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.214329] pnp 00:00: [mem 0x00100000-0x7ffeffff]
[    0.214338] pnp 00:00: [mem 0x7fff0000-0x7fffffff]
[    0.214346] pnp 00:00: [mem 0xfeda0000-0xfedfffff]
[    0.214355] pnp 00:00: [mem 0xffb00000-0xffbfffff]
[    0.214525] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.214538] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.214550] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.214561] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.214573] system 00:00: [mem 0x00100000-0x7ffeffff] could not be reserved
[    0.214584] system 00:00: [mem 0x7fff0000-0x7fffffff] has been reserved
[    0.214596] system 00:00: [mem 0xfeda0000-0xfedfffff] has been reserved
[    0.214607] system 00:00: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.214620] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.221306] pnp 00:01: [bus 00-ff]
[    0.221317] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.221326] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.221335] pnp 00:01: [io  0x0d00-0xffff window]
[    0.221344] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.221354] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.221364] pnp 00:01: [mem 0x80000000-0xfed9ffff window]
[    0.221373] pnp 00:01: [mem 0xfee00000-0xffafffff window]
[    0.221535] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.221599] pnp 00:02: [io  0x0092]
[    0.221607] pnp 00:02: [io  0x00b2]
[    0.221615] pnp 00:02: [io  0x0020-0x0021]
[    0.221623] pnp 00:02: [io  0x00a0-0x00a1]
[    0.221633] pnp 00:02: [irq 2 disabled]
[    0.221641] pnp 00:02: [io  0x04d0-0x04d1]
[    0.221657] pnp 00:02: [io  0x0800-0x0805]
[    0.221665] pnp 00:02: [io  0x0808-0x080f]
[    0.221804] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.221815] system 00:02: [io  0x0800-0x0805] has been reserved
[    0.221826] system 00:02: [io  0x0808-0x080f] has been reserved
[    0.221839] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.221900] pnp 00:03: [io  0xf400-0xf4fe]
[    0.221909] pnp 00:03: [io  0x0086]
[    0.221916] pnp 00:03: [io  0x00b3]
[    0.221924] pnp 00:03: [io  0x0806-0x0807]
[    0.221933] pnp 00:03: [io  0x0810-0x085f]
[    0.221941] pnp 00:03: [io  0x0860-0x087f]
[    0.221949] pnp 00:03: [io  0x0880-0x08bf]
[    0.221957] pnp 00:03: [io  0x08c0-0x08df]
[    0.221965] pnp 00:03: [io  0x08e0-0x08ff]
[    0.222106] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.222117] system 00:03: [io  0x0806-0x0807] has been reserved
[    0.222128] system 00:03: [io  0x0810-0x085f] has been reserved
[    0.222139] system 00:03: [io  0x0860-0x087f] has been reserved
[    0.222149] system 00:03: [io  0x0880-0x08bf] has been reserved
[    0.222160] system 00:03: [io  0x08c0-0x08df] has been reserved
[    0.222170] system 00:03: [io  0x08e0-0x08ff] has been reserved
[    0.222182] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.222247] pnp 00:04: [irq 12]
[    0.222337] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.222401] pnp 00:05: [io  0x0060]
[    0.222410] pnp 00:05: [io  0x0064]
[    0.222418] pnp 00:05: [irq 1]
[    0.222509] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.222564] pnp 00:06: [io  0x0070-0x0071]
[    0.222573] pnp 00:06: [irq 8]
[    0.222581] pnp 00:06: [io  0x0072-0x0077]
[    0.222672] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.222764] pnp 00:07: [io  0x0061]
[    0.222773] pnp 00:07: [io  0x0063]
[    0.222780] pnp 00:07: [io  0x0065]
[    0.222788] pnp 00:07: [io  0x0067]
[    0.222881] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.222936] pnp 00:08: [io  0x002e-0x002f]
[    0.222945] pnp 00:08: [io  0x004e-0x004f]
[    0.222953] pnp 00:08: [io  0x0900-0x097f]
[    0.223086] system 00:08: [io  0x0900-0x097f] has been reserved
[    0.223099] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.223175] pnp 00:09: [dma 4]
[    0.223184] pnp 00:09: [io  0x0000-0x000f]
[    0.223192] pnp 00:09: [io  0x0080-0x0085]
[    0.223200] pnp 00:09: [io  0x0087-0x008f]
[    0.223208] pnp 00:09: [io  0x00c0-0x00df]
[    0.223216] pnp 00:09: [io  0x0010-0x001f]
[    0.223224] pnp 00:09: [io  0x0090-0x0091]
[    0.223232] pnp 00:09: [io  0x0093-0x009f]
[    0.223329] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.223383] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.223393] pnp 00:0a: [irq 13]
[    0.223490] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.230861] pnp: PnP ACPI: found 11 devices
[    0.230869] ACPI: ACPI bus type pnp unregistered
[    0.230883] PnPBIOS: Disabled by ACPI PNP
[    0.271151] Switching to clocksource acpi_pm
[    0.271206] pci 0000:01:00.0: no compatible bridge window for [mem 0x80000000-0x8001ffff pref]
[    0.271224] PCI: max bus depth: 2 pci_try_num: 3
[    0.271264] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.271277] pci 0000:00:1f.1: BAR 5: assigned [mem 0x84000000-0x840003ff]
[    0.271293] pci 0000:00:1f.1: BAR 5: set to [mem 0x84000000-0x840003ff] (PCI address [0x84000000-0x840003ff])
[    0.271309] pci 0000:01:00.0: BAR 6: assigned [mem 0xfd000000-0xfd01ffff pref]
[    0.271319] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.271330] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.271343] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.271355] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.271373] pci 0000:02:01.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.271388] pci 0000:02:01.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.271398] pci 0000:02:01.0: BAR 0: assigned [mem 0xf6000000-0xf6000fff]
[    0.271413] pci 0000:02:01.0: BAR 0: set to [mem 0xf6000000-0xf6000fff] (PCI address [0xf6000000-0xf6000fff])
[    0.271425] pci 0000:02:01.0: BAR 13: assigned [io  0xd000-0xd0ff]
[    0.271436] pci 0000:02:01.0: BAR 14: assigned [io  0xd400-0xd4ff]
[    0.271446] pci 0000:02:01.0: CardBus bridge to [bus 03-06]
[    0.271455] pci 0000:02:01.0:   bridge window [io  0xd000-0xd0ff]
[    0.271467] pci 0000:02:01.0:   bridge window [io  0xd400-0xd4ff]
[    0.271479] pci 0000:02:01.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.271492] pci 0000:02:01.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.271504] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.271514] pci 0000:00:1e.0:   bridge window [io  0xd000-0xefff]
[    0.271528] pci 0000:00:1e.0:   bridge window [mem 0xf6000000-0xfbffffff]
[    0.271540] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.271573] pci 0000:00:1e.0: setting latency timer to 64
[    0.271589] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.271927] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.271936] PCI: setting IRQ 11 as level-triggered
[    0.271950] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.271968] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.271978] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.271988] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.271998] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfdffffff]
[    0.272008] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.272018] pci_bus 0000:02: resource 0 [io  0xd000-0xefff]
[    0.272028] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xfbffffff]
[    0.272038] pci_bus 0000:02: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.272048] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.272057] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.272067] pci_bus 0000:03: resource 0 [io  0xd000-0xd0ff]
[    0.272077] pci_bus 0000:03: resource 1 [io  0xd400-0xd4ff]
[    0.272087] pci_bus 0000:03: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.272097] pci_bus 0000:03: resource 3 [mem 0x88000000-0x8bffffff]
[    0.272215] NET: Registered protocol family 2
[    0.272420] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.273146] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.273188] Switched to NOHz mode on CPU #0
[    0.275228] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.276288] TCP: Hash tables configured (established 131072 bind 65536)
[    0.276297] TCP reno registered
[    0.276309] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.276349] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.276660] NET: Registered protocol family 1
[    0.276841] pci 0000:01:00.0: Boot video device
[    0.276871] PCI: CLS 32 bytes, default 64
[    0.277715] audit: initializing netlink socket (disabled)
[    0.277741] type=2000 audit(1334236042.271:1): initialized
[    0.355191] Trying to unpack rootfs image as initramfs...
[    0.461151] highmem bounce pool size: 64 pages
[    0.461171] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.513133] VFS: Disk quotas dquot_6.5.2
[    0.513370] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.515893] fuse init (API version 7.16)
[    0.516264] msgmni has been set to 1680
[    0.528838] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.532847] io scheduler noop registered
[    0.532856] io scheduler deadline registered
[    0.532913] io scheduler cfq registered (default)
[    0.533357] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533442] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.533749] efifb: probing for efifb
[    0.533758] efifb: cannot reserve video memory at 0xa0000
[    0.533770] efifb: framebuffer at 0xa0000, mapped to 0xc00a0000, using 56k, total 64k
[    0.533781] efifb: mode is 640x350x1, linelength=80, pages=1
[    0.533787] efifb: scrolling: redraw
[    0.533796] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.534055] Console: switching to colour frame buffer device 80x43
[    0.534124] fb0: EFI VGA frame buffer device
[    0.534669] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.535115] ACPI: AC Adapter [AC] (on-line)
[    0.536380] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.536845] ACPI: Lid Switch [LID]
[    0.537006] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.537022] ACPI: Power Button [PBTN]
[    0.537171] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.537185] ACPI: Sleep Button [SBTN]
[    0.537275] ACPI: acpi_idle registered with cpuidle
[    0.537735] Marking TSC unstable due to TSC halts in idle
[    0.568658] thermal LNXTHERM:00: registered as thermal_zone0
[    0.568669] ACPI: Thermal Zone [THM] (25 C)
[    0.568727] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.572477] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.572545] ERST: Table is not found!
[    0.572727] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.584130] isapnp: Scanning for PnP cards...
[    0.672996] ACPI: Battery Slot [BAT1] (battery absent)
[    0.673241] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    0.673251] PCI: setting IRQ 7 as level-triggered
[    0.673266] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    0.673286] serial 0000:00:1f.6: PCI INT B disabled
[    0.673692] Linux agpgart interface v0.103
[    0.673997] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    0.693369] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    0.702661] brd: module loaded
[    0.709838] loop: module loaded
[    0.710259] ata_piix 0000:00:1f.1: version 2.13
[    0.710287] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.710645] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.710661] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.710748] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.711689] scsi0 : ata_piix
[    0.716677] scsi1 : ata_piix
[    0.718074] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.718085] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.719588] Fixed MDIO Bus: probed
[    0.719678] PPP generic driver version 2.4.2
[    0.719813] tun: Universal TUN/TAP device driver, 1.6
[    0.719821] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.720250] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.720606] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.720621] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.720652] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.720663] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.720786] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.720853] ehci_hcd 0000:00:1d.7: debug port 1
[    0.724743] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.728158] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    0.780267] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.780668] hub 1-0:1.0: USB hub found
[    0.780684] hub 1-0:1.0: 6 ports detected
[    0.780895] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.780936] uhci_hcd: USB Universal Host Controller Interface driver
[    0.781020] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.781039] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.781049] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.781163] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.781206] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.781600] hub 2-0:1.0: USB hub found
[    0.781614] hub 2-0:1.0: 2 ports detected
[    0.781788] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.781806] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.781816] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.781927] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.781968] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.782357] hub 3-0:1.0: USB hub found
[    0.782370] hub 3-0:1.0: 2 ports detected
[    0.782863] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.782878] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.782895] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.782905] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.783052] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.783094] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.783495] hub 4-0:1.0: USB hub found
[    0.783509] hub 4-0:1.0: 2 ports detected
[    0.783863] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.873681] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.873701] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.874033] mousedev: PS/2 mouse device common for all mice
[    0.874723] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.874756] rtc0: alarms up to one day, 114 bytes nvram
[    0.875118] device-mapper: uevent: version 1.0.3
[    0.875383] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.875489] EISA: Probing bus 0 at eisa.0
[    0.875540] EISA: Detected 0 cards.
[    0.875563] cpufreq-nforce2: No nForce2 chipset.
[    0.875743] cpuidle: using governor ladder
[    0.875975] cpuidle: using governor menu
[    0.875982] EFI Variables Facility v0.08 2004-May-17
[    0.876653] ata2.00: ATAPI: SAMSUNG CDRW/DVD SN-324F, U203, max UDMA/33
[    0.877754] TCP cubic registered
[    0.879714] NET: Registered protocol family 10
[    0.881725] ata1.00: ATA-6: HTS548060M9AT00, MGBOA53A, max UDMA/100
[    0.881737] ata1.00: 117210240 sectors, multi 8: LBA48 
[    0.882128] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.888445] NET: Registered protocol family 17
[    0.888510] Registering the dns_resolver key type
[    0.888555] Using IPI No-Shortcut mode
[    0.888809] PM: Hibernation image not present or could not be loaded.
[    0.888851] registered taskstats version 1
[    0.900507] ata2.00: configured for UDMA/33
[    0.901881] ata1.00: configured for UDMA/100
[    0.987062] ACPI: Battery Slot [BAT0] (battery present)
[    1.295780] isapnp: No Plug & Play device found
[    1.296204] scsi 0:0:0:0: Direct-Access     ATA      HTS548060M9AT00  MGBO PQ: 0 ANSI: 5
[    1.296739] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.297124] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.297286] sd 0:0:0:0: [sda] Write Protect is off
[    1.297297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.297369] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.317985] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324F U203 PQ: 0 ANSI: 5
[    1.322422] sr0: scsi3-mmc drive: 2x/24x writer cd/rw xa/form2 cdda tray
[    1.322433] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.322766] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.322956] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.339884]  sda: sda1 sda2 < sda5 >
[    1.340834] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.019985] Freeing initrd memory: 13320k freed
[    2.061127]   Magic number: 8:331:129
[    2.061298] acpi device:04: hash matches
[    2.061368] rtc_cmos 00:06: setting system clock to 2012-04-12 13:07:24 UTC (1334236044)
[    2.129258] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.129266] EDD information not available.
[    2.129570] Freeing unused kernel memory: 696k freed
[    2.130313] Write protecting the kernel text: 5344k
[    2.130448] Write protecting the kernel read-only data: 2192k
[    2.181803] udevd[84]: starting version 173
[    2.687966] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.704476] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    2.704494] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    2.704507] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    2.744231] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.744298] b44: b44.c:v2.0
[    2.744370] firewire_ohci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.765919] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:1c:93:e9
[    2.800504] firewire_ohci: Added fw-ohci device 0000:02:01.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.924452] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.300312] firewire_core: created device fw0: GUID 424fc0003be120a1, S400
[    5.851480] udevd[268]: starting version 173
[    6.185637] Adding 2095100k swap on /dev/sda5.  Priority:-1 extents:1 across:2095100k 
[    7.294164] lp: driver loaded but no devices found
[    8.533873] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.795119] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.161745] lib80211: common routines for IEEE802.11 drivers
[    9.161757] lib80211_crypt: registered algorithm 'NULL'
[    9.220848] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/LNXVIDEO:00/input/input4
[    9.221115] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    9.225381] intel_rng: FWH not detected
[    9.243399] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:0191]
[    9.243429] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[    9.243438] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[    9.243452] yenta_cardbus 0000:02:01.0: TI: mfunc 0x012c1202, devctl 0x64
[    9.467867] cfg80211: Calling CRDA to update world regulatory domain
[    9.472723] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0478, PCI irq 11
[    9.472736] yenta_cardbus 0000:02:01.0: Socket status: 30000086
[    9.472749] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[    9.472771] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [io  0xd000-0xefff]
[    9.472783] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: excluding 0xd000-0xd0ff 0xd400-0xd4ff
[    9.519080] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xf6000000-0xfbffffff]
[    9.519097] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff
[    9.519142] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[    9.519154] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[    9.537275] libipw: 802.11 data/management/control stack, git-1.1.13
[    9.537286] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    9.643951] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input5
[    9.662409] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[    9.884726] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.929626] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    9.929638] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    9.929885] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    9.929927] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   10.292724] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.292740] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292750] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.292761] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292770] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.292781] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292790] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.292801] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292811] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.292821] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292831] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.292842] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292851] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.292862] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292871] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.292882] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292891] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.292902] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292911] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.292922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.292932] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.292943] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   10.295478] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   10.782876] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   10.784245] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   10.784886] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   10.785092] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   10.785683] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xf0000-0xfffff
[   10.785867] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   10.786049] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   10.786234] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.885787] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.885803] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885813] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.885824] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885834] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.885845] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885854] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.885865] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885874] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.885885] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885894] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.885905] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885914] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.885925] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885935] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.885946] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885955] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.885966] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885975] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.885986] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.885995] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.886006] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.886017] cfg80211: World regulatory domain updated:
[   12.886024] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.886035] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.886046] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.886056] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.886066] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.886076] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.415046] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[   13.415103] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   13.989482] nvidia: module license 'NVIDIA' taints kernel.
[   13.989494] Disabling lock debugging due to kernel taint
[   15.463210] intel8x0_measure_ac97_clock: measured 252589 usecs (12134 samples)
[   15.463222] intel8x0: clocking to 48000
[   15.463495] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.463519] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.464069] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   17.095431] type=1400 audit(1334236059.532:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=605 comm="apparmor_parser"
[   17.096197] type=1400 audit(1334236059.532:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=610 comm="apparmor_parser"
[   17.097803] type=1400 audit(1334236059.532:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=610 comm="apparmor_parser"
[   17.098838] type=1400 audit(1334236059.532:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=610 comm="apparmor_parser"
[   17.100675] type=1400 audit(1334236059.536:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=607 comm="apparmor_parser"
[   17.102275] type=1400 audit(1334236059.536:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=607 comm="apparmor_parser"
[   17.103310] type=1400 audit(1334236059.536:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=607 comm="apparmor_parser"
[   17.105700] type=1400 audit(1334236059.540:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=605 comm="apparmor_parser"
[   17.106777] type=1400 audit(1334236059.540:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=605 comm="apparmor_parser"
[   19.045308] init: failsafe main process (699) killed by TERM signal
[   19.659492] ppdev: user-space parallel port driver
[   20.052196] type=1400 audit(1334236062.488:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=780 comm="apparmor_parser"
[   23.010546] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.513614] init: apport pre-start process (848) terminated with status 1
[   23.526027] init: apport post-stop process (874) terminated with status 1
[   30.148583] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   30.148618] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   30.148683] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   33.268616] Bluetooth: Core ver 2.16
[   33.268690] NET: Registered protocol family 31
[   33.268697] Bluetooth: HCI device and connection manager initialized
[   33.268705] Bluetooth: HCI socket layer initialized
[   33.268711] Bluetooth: L2CAP socket layer initialized
[   33.276155] Bluetooth: SCO socket layer initialized
[   33.468694] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.468704] Bluetooth: BNEP filters: protocol multicast
[   33.469145] Bluetooth: RFCOMM TTY layer initialized
[   33.469157] Bluetooth: RFCOMM socket layer initialized
[   33.469164] Bluetooth: RFCOMM ver 1.11
[   37.047770] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   37.640035] eth1: no IPv6 routers present
[   38.161361] init: plymouth-stop pre-start process (1198) terminated with status 1
[   45.528638] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  294.116683] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[  294.116717] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[  294.116782] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[  475.272260] usb 1-1: new high speed USB device number 2 using ehci_hcd
[ 1499.457511] audit_printk_skb: 39 callbacks suppressed
[ 1499.457524] type=1400 audit(1334237541.894:25): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=5680 comm="apparmor_parser"
[ 1499.458535] type=1400 audit(1334237541.894:26): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=5680 comm="apparmor_parser"
[ 2491.747651] usb 1-1: USB disconnect, device number 2
```

---

### Post by abyrne on 2012-04-12
Alright, thanks for the info. So allow me to answer a few of your questions before we move on.

> I am, actually.... so you are guessing it is a motherboard problem?
No, not your motherboard. Specifically, it's your video card. I asked if you were using an Inspiron because that's the same model as the user in the bug report. 

> And I looked at that link and it seems like they were able to figure it out somehow, but little of what the author says makes sense to me (utter noob here...) could you possibly explain it to me?
(Trust me, if you know how to run commands, you're not as nooby as you think). Anyway, remember when I mentioned that suspend functions have been buggy in Linux? Well, in response to that, a team of software developers from the HAL (**H**ardware **A**bstraction **L**ayer) project created some fixes for the suspend functions called "quirks", designed to handle the quirks in certain machine configurations. Ironically, the system that automatically controls whether these quirks should be used or not is buggy on your model of the Inspiron. 

It seems that users have been able to successfully run a suspend/resume cycle be completely disabling these quirks. So, try running the following command, which should manually cause the system to suspend without using the default quirks and without shutting the lid. 
```
sudo pm-suspend --quirk-dpms-on
```
Wait a minute before touching your computer. Then, try to resume it by hitting a key or the power button. If it resumes correctly, then we've got a good sign. If not (and your have to force power off), then we'll keep trying. Either way, after your done, post the output of the following command
```
cat /var/log/pm-suspend.log
```

---

### Post by Eirreann on 2012-04-12
Nope, didn't work.... not surprised, personally, but I was kind of hoping...

Anyway, here's the output of that command:
```
Initial commandline parameters: --quirk-dpms-on
Thu Apr 12 11:18:16 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux eirreann-Inspiron-8600 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
nvidia               7098131  26 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
joydev                 17393  0 
ipw2200               146148  0 
pcmcia                 39822  0 
dcdbas                 14098  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
libipw                 46701  1 ipw2200
cfg80211              172427  2 ipw2200,libipw
psmouse                73673  0 
serio_raw              12990  0 
yenta_socket           27428  0 
video                  18908  0 
lib80211               14570  2 ipw2200,libipw
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
b44                    31443  0 
ssb                    50682  1 b44
crc_itu_t              12627  1 firewire_core
             total       used       free     shared    buffers     cached
Mem:       2062064    1521240     540824          0      81052     909052
-/+ buffers/cache:     531136    1530928
Swap:      2095100        592    2094508

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'eth1'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Apr 12 11:18:22 EDT 2012: performing suspend
Thu Apr 12 11:18:40 EDT 2012: Awake.
Thu Apr 12 11:18:41 EDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'eth1'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:

```

Oh, and when booting back up again I noticed that my BIOS are revision A08, while the newest revision is A15.  Would upgrading the BIOS help at all?

---

### Post by abyrne on 2012-04-12
[COLOR="Red"]**_EDIT: DON'T USE THE METHOD I POSTED EARLIER!_** My mistake: I misformatted the section. I'll come out with a fix soon. If I borked anyone's XOrg during the 30 minutes before this edit, switch to TTY1 by pressing Ctrl-Alt-F1, login normally, and use the command
```
sudo rm /usr/share/X11/xorg.conf.d/50-nvidia-suspend-fix.conf
```
and reboot
I'm really sorry about this[/COLOR]
I deleted the tutorial to prevent confusion. I'll be rewriting it as soon as possible.

---

### Post by abyrne on 2012-04-12
*Note to Eirreann: The following is a request for help from the community. There's no solutions that you should use that are contained in this post.*

I'm hitting roadblocks when trying to write this solution. We could use a little help from the rest of the community, maybe someone with a little more knowledge on XOrg and Nvidia drivers.

Important bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433177/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433177/comments/6)
Attempting to adapt his solution to 11.10. Haven't had much luck so far. So far, disabling the quirks is the easy part
Quote from my original tutorial:
> 
Run
```
gksudo gedit /usr/lib/pm-utils/video-quirks/20-video-quirk-pm-dell.quirkdb
```
which should bring up a text editor. Now find the section that looks like 
```

   match system.hardware.product regex 1501|8600
    addquirk --quirk-s3-bios
    addquirk --quirk-s3-mode
    match system.hardware.primary_video.vendor numeric_compare_eq 0x1002
     addquirk --quirk-radeon-off
    endmatch
   endmatch

```
and disable that section by adding a pound sign (#) before each line. The result should look like
```

#   match system.hardware.product regex 1501|8600
#    addquirk --quirk-s3-bios
#    addquirk --quirk-s3-mode
#    match system.hardware.primary_video.vendor numeric_compare_eq 0x1002
#     addquirk --quirk-radeon-off
#    endmatch
#   endmatch

```
But enabling the Option "NvAGP" "1" in the xorg conf has proven more difficult than I thought, given the removal of an xorg.conf in recent versions of Ubuntu.

If anyone has anything to contribute, please do. I'm going to look at this again with a fresh set of eyes later today. Thanks in advanced.

---

### Post by Eirreann on 2012-04-12
> **abyrne said:**
> [COLOR="Red"]**_EDIT: DON'T USE THE METHOD I POSTED EARLIER!_** My mistake: I misformatted the section. I'll come out with a fix soon. If I borked anyone's XOrg during the 30 minutes before this edit, switch to TTY1 by pressing Ctrl-Alt-F1, login normally, and use the command
```
sudo rm /usr/share/X11/xorg.conf.d/50-nvidia-suspend-fix.conf
```
and reboot
I'm really sorry about this[/COLOR]
I deleted the tutorial to prevent confusion. I'll be rewriting it as soon as possible.

Dangit why didn't I see this sooner?  I'm currently repairing the last installation of Ubuntu with the disk because what you told me to do caused the white screen on boot and it wouldn't go to the login page...
*Sigh*

---

### Post by abyrne on 2012-04-12
I'm really sorry about that. It was hastily written, and I should have tested more thoroughly. :(

Anyway, I'm in debt to you now. Let's take one more whack at this: it looks pretty promising.

[COLOR="Blue"][B]_In case you can't get to the login screen during this process, have the following instructions ready! Write them down if you have to!_
[LIST=1]
[*]At the blank screen, press Ctrl-Alt-F1, and login with your normal credentials.
[*]Run ```
sudo rm /usr/share/X11/xorg.conf.d/50-nvidia-suspend-fix.conf
```
[*]Reboot with ```
sudo reboot
```
[/LIST][/B][/COLOR]

All we have to do is run
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-nvidia-suspend-fix.conf
```
and paste in
```

Section "Device"
Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"
Driver         "nvidia"
Option         "NvAgp"      "1"
EndSection

```
and save and reboot. Pray, my friend. Pray.

Again, I feel horrible about the bad tutorial earlier. Let's hope we can finally get this fixed.

---

### Post by Eirreann on 2012-04-12
It's not a problem!  I've had to reinstall Ubuntu quite a few times, so it's not a first for me!  I'm giving your newest method a try right now.

---

### Post by Eirreann on 2012-04-12
> **abyrne said:**
> I'm really sorry about that. It was hastily written, and I should have tested more thoroughly. :(

Anyway, I'm in debt to you now. Let's take one more whack at this: it looks pretty promising.

[COLOR=Blue][B]_In case you can't get to the login screen during this process, have the following instructions ready! Write them down if you have to!_
[LIST=1]
[*]At the blank screen, press Ctrl-Alt-F1, and login with your normal credentials.
[*]Run ```
sudo rm /usr/share/X11/xorg.conf.d/50-nvidia-suspend-fix.conf
```
[*]Reboot with ```
sudo reboot
```
[/LIST]
[/B][/COLOR]

All we have to do is run
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-nvidia-suspend-fix.conf
```and paste in
```

Section "Device"
Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"
Driver         "nvidia"
Option         "NvAgp"      "1"
EndSection

```and save and reboot. Pray, my friend. Pray.

Again, I feel horrible about the bad tutorial earlier. Let's hope we can finally get this fixed.

IT WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I put it on suspend, then brought it back, and it has worked perfectly!

Now, will this also fix the issue with Hibernate?  It was doing it with hibernate as well...

But thank you so much for sticking it out until we were able to fix it!  You, sir, are awesome!  +1 from me!

---

### Post by wojox on 2012-04-12
Which driver version are you running for nvidia?

Edit: To late. :)

---

### Post by abyrne on 2012-04-13
> IT WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! !!!!!!!

I put it on suspend, then brought it back, and it has worked perfectly!
Thank God. I'm glad we finally got this fixed!

> Now, will this also fix the issue with Hibernate? It was doing it with hibernate as well...
I'm not sure actually. This bug report leads me to believe that the hibernation process was suffering from the same issue as the suspend process, but hibernation has a lot of key differences from suspension. Try it, and post the results.

---

### Post by Eirreann on 2012-04-13
> **abyrne said:**
> 


I'm not sure actually. This bug report leads me to believe that the hibernation process was suffering from the same issue as the suspend process, but hibernation has a lot of key differences from suspension. Try it, and post the results.

I *think* that it fixed hibernate as well; what happens with hibernate is when I click on it the screen will go black, then flicker that annoying white screen, then all of the lights on my computer will shut off and it looks like it has completely powered down.  But when I hit the power button it just takes me to the lock screen, where I can login and lo and behold there's my desktop and all the programmes I had open are still up and running...

---

### Post by abyrne on 2012-04-13
> I *think* that it fixed hibernate as well; what happens with hibernate is when I click on it the screen will go black, then flicker that annoying white screen, then all of the lights on my computer will shut off and it looks like it has completely powered down. But when I hit the power button it just takes me to the lock screen, where I can login and lo and behold there's my desktop and all the programmes I had open are still up and running...
Yup, that's hibernate. You got it. I wouldn't worry about the white screen; as long as it hibernates and resumes correctly, you should be all set.

---

### Post by Eirreann on 2012-04-13
> **abyrne said:**
> Yup, that's hibernate. You got it. I wouldn't worry about the white screen; as long as it hibernates and resumes correctly, you should be all set.

*Phew*, good!  Well, that's one less Ubuntu bug that I have to worry about, haha!  Now I just need to figure out how to install Xubuntu without completely screwing up NotifyOSD...

---

### Post by theOGRE on 2013-01-10
This worked for me as well on Xubuntu 12.04 on the same computer.  Thank you for the solution!

---

