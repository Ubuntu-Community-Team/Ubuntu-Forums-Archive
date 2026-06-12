---
title: "I'm new to Ubuntu"
date: 2011-10-20
forum: General Help
---

### Post by Aligore on 2011-10-20
I have just bought a western digital 2tb hard drive firstly my BIOS wouldn't see it so i installed a SATA controller card. Device manager knows the card is installed in the computer but the drive still won't show up is there anything else I should be doing first

---

### Post by sg1efc on 2011-10-20
> **Aligore said:**
> Device manager knows the card is installed in the computer but the drive still won't show up is there anything else I should be doing first

When you have clicked on the Computer icon (or click on Computer under the Places tab at the top), do you see your drive listed there?  Along with Home, Desktop, File System, etc.?   If not, did you click on the drive in the left pane?   When you have a drive listed, it seems you must click on it, so that Ubuntu will Mount it first.  Once it is mounted, you should then be able to see the contents.

I am no expert, but hope this might help.  :)

---

### Post by decrepit on 2011-10-20
Have you tried,
```
sudo fdisk-l
```
?

---

### Post by Aligore on 2011-10-20
No the drive is not listed in "my computer". And sudo -l gives me the file info for the boot drive, thi s 2tb drive will be data

Although it does list /dev/sda1,2 and 5

---

### Post by kaldor on 2011-10-20
That shouldn't be. Whenever I plug in an external drive it shows up for me instantly.

What filesystem is on the external? Whenever I get a new USB drive I always reformat it and make it NTFS.

Edit: Does it show up in the *Disk Utility* application?

---

### Post by Aligore on 2011-10-20
It's a brand new drive so no file system

No it doesn't show in disk utility

---

### Post by kaldor on 2011-10-20
Just to troubleshoot...

Does the drive work on other computers or on Windows? Do other USB drives work on your computer?

Just want to rule out the possibility of a faulty drive/computer.

---

### Post by Aligore on 2011-10-20
Already tried that drive works fine in a windows box

---

### Post by kaldor on 2011-10-20
Just a shot here, but I might be wrong.

Try installing the ntfs-3g package on Ubuntu. Do this via the Software Centre **or** by pasting this command in a Terminal:

```
sudo apt-get install ntfs-3g
```

---

### Post by Aligore on 2011-10-20
I tried ls /dev/sd*

And no /dev/sdb showed up

Nods-3g latest version already

---

### Post by kaldor on 2011-10-20
This isn't making sense to me. Granted, I haven't had enough coffee yet today.

Check to see if any of this [_here_]("https://help.ubuntu.com/community/Mount/USB#Manually_Mounting") will help. I've never had any problems with external drives on Linux before, so I'm pretty confused as to why it's not working, since you seem to be doing everything correctly.

Are you running the latest Ubuntu release? Currently that's 11.10 (Oneiric Ocelot).

---

### Post by WorMzy on 2011-10-20
If the drive is blank, what exactly are you expecting to see? You can't mount and browse a filesystem that isn't there.

You'll need to open up a partition editor, like gparted, and create at least one filesystem on it. Depending on the manufacturer, you might need to create a partition table first.

---

### Post by kaldor on 2011-10-20
> **WorMzy said:**
> If the drive is blank, what exactly are you expecting to see? You can't mount and browse a filesystem that isn't there.

You'll need to open up a partition editor, like gparted, and create at least one filesystem on it. Depending on the manufacturer, you might need to create a partition table first.

In that case, should it not be showing up in the Disk Utility program?

---

### Post by Aligore on 2011-10-20
I'm actually just doing the upgrade to  11.10

In the disk utility the sata controller card shows up just not the drive. 

After upgrade I'll post back

---

### Post by WorMzy on 2011-10-20
> **kaldor said:**
> In that case, should it not be showing up in the Disk Utility program?

Dunno, never used it. If the disk doesn't have a partition table on it, then perhaps not?

---

### Post by kaldor on 2011-10-20
> **WorMzy said:**
> Dunno, never used it. If the disk doesn't have a partition table on it, then perhaps not?

It should still show up in the device list. You can create/remove partitions and such in it also and it feels a bit friendlier than Gparted.

---

### Post by Aligore on 2011-10-20
It's nearly finished the update, so I'll check in a bit

---

### Post by WorMzy on 2011-10-20
If it's still not showing up after the update, could you install xsel, then run this command:

```
sudo parted -l | xsel -ib
```

(substitute xsel with xclip if you already xclip installed)

then start writing a new reply, click the hash tag (#) and paste (Ctrl+V) the contents of your clipboard in-between the CODE tags, then post the reply.

---

### Post by Aligore on 2011-10-20
No mate its still not showing up in 'computer' or disk util

```

Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system     Flags
 1      1049kB  120GB  120GB  primary   ext4            boot
 2      120GB   120GB  467MB  extended
 5      120GB   120GB  467MB  logical   linux-swap(v1)

```Theres what I got from the last command

Thats the root drive 120gb

But the 2tb will be the data only drive

In disk util the SATA VIA6421 card shows up, but no drive, the drive works in a windows box so I know its not the drive

---

### Post by WorMzy on 2011-10-20
It seems to me that the kernel isn't recognising it, or else isn't compiled with the right driver for it. Can you do the same as before, only this time, with the following command:

```
dmesg | xsel -ib
```

---

### Post by Aligore on 2011-10-20
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005bff0000 (usable)
[    0.000000]  BIOS-e820: 000000005bff0000 - 000000005bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005bff3000 - 000000005c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI:    /K8M800-M2, BIOS 6.00 PG 12/20/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x5bff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CBFFF uncachable
[    0.000000]   CC000-D3FFF write-back
[    0.000000]   D4000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 0040000000 mask FFE0000000 write-back
[    0.000000]   2 base 005C000000 mask FFFC000000 uncachable
[    0.000000]   3 base 00E0000000 mask FFF8000000 write-combining
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f3d40] f3d40
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365f6000 - 372f3000
[    0.000000] ACPI: RSDP 000f57a0 00014 (v00 VIAK8M)
[    0.000000] ACPI: RSDT 5bff3000 0002C (v01 VIAK8M AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 5bff3040 00074 (v01 VIAK8M AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 5bff30c0 05308 (v01 VIAK8M AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 5bff0000 00040
[    0.000000] ACPI: APIC 5bff8400 0005A (v01 VIAK8M AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 583MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005bff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005bff0
[    0.000000] On node 0 totalpages: 376703
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f5a76200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1168 pages used for memmap
[    0.000000]   HighMem zone: 148322 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 5c000000 (gap: 5c000000:a2c00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5400000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373759
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=aa0dab11-98cb-4161-bd5d-bfe89a3ad348 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6028800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005bff0)
[    0.000000] Memory: 1465428k/1507264k available (5329k kernel code, 41384k reserved, 2589k data, 696k init, 597960k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1599.680 MHz processor.
[    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.36 BogoMIPS (lpj=6398720)
[    0.008013] pid_max: default: 32768 minimum: 301
[    0.008049] Security Framework initialized
[    0.008085] AppArmor: AppArmor initialized
[    0.008088] Yama: becoming mindful.
[    0.008178] Mount-cache hash table entries: 512
[    0.008376] Initializing cgroup subsys cpuacct
[    0.008385] Initializing cgroup subsys memory
[    0.008400] Initializing cgroup subsys devices
[    0.008405] Initializing cgroup subsys freezer
[    0.008409] Initializing cgroup subsys net_cls
[    0.008413] Initializing cgroup subsys blkio
[    0.008425] Initializing cgroup subsys perf_event
[    0.008466] mce: CPU supports 5 MCE banks
[    0.008750] SMP alternatives: switching to UP code
[    0.019214] Freeing SMP alternatives: 24k freed
[    0.019246] ACPI: Core revision 20110413
[    0.032031] ftrace: allocating 24885 entries in 49 pages
[    0.036120] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036940] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.077371] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[    0.080004] Performance Events: AMD PMU driver.
[    0.080004] ... version:                0
[    0.080004] ... bit width:              48
[    0.080004] ... generic registers:      4
[    0.080004] ... value mask:             0000ffffffffffff
[    0.080004] ... max period:             00007fffffffffff
[    0.080004] ... fixed-purpose events:   0
[    0.080004] ... event mask:             000000000000000f
[    0.080004] Brought up 1 CPUs
[    0.080004] Total of 1 processors activated (3199.36 BogoMIPS).
[    0.080004] devtmpfs: initialized
[    0.080004] PM: Registering ACPI NVS region at 5bff0000 (12288 bytes)
[    0.080189] print_constraints: dummy: 
[    0.080231] Time: 18:50:10  Date: 10/20/11
[    0.080282] NET: Registered protocol family 16
[    0.080457] EISA bus registered
[    0.080464] node 0 link 0: io port [1000, fffff]
[    0.080469] TOM: 0000000060000000 aka 1536M
[    0.080472] node 0 link 0: mmio [60000000, e7ffffff]
[    0.080477] node 0 link 0: mmio [e8000000, ebffffff]
[    0.080481] node 0 link 0: mmio [ec000000, ecffffff]
[    0.080484] node 0 link 0: mmio [ed000000, ff70ffff]
[    0.080489] node 0 link 0: mmio [a0000, bffff]
[    0.080493] bus: [00, ff] on node 0 link 0
[    0.080497] bus: 00 index 0 [io  0x0000-0xffff]
[    0.080500] bus: 00 index 1 [mem 0x60000000-0xffffffff]
[    0.080503] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.080514] ACPI: bus type pci registered
[    0.085758] PCI: PCI BIOS revision 2.10 entry at 0xfb820, last bus=1
[    0.085761] PCI: Using configuration type 1 for base access
[    0.087331] bio: create slab <bio-0> at 0
[    0.088333] ACPI: EC: Look up EC in DSDT
[    0.093638] ACPI: Interpreter enabled
[    0.093646] ACPI: (supports S0 S3 S4 S5)
[    0.093675] ACPI: Using IOAPIC for interrupt routing
[    0.099430] ACPI: No dock devices found.
[    0.099433] HEST: Table not found.
[    0.099439] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.099523] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.099701] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.099705] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.099710] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.099714] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.099718] pci_root PNP0A03:00: host bridge window [mem 0x60000000-0xfebfffff] (ignored)
[    0.099741] pci 0000:00:00.0: [1106:0204] type 0 class 0x000600
[    0.099752] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
[    0.099822] pci 0000:00:00.1: [1106:1204] type 0 class 0x000600
[    0.099864] pci 0000:00:00.2: [1106:2204] type 0 class 0x000600
[    0.099905] pci 0000:00:00.3: [1106:3204] type 0 class 0x000600
[    0.099948] pci 0000:00:00.4: [1106:4204] type 0 class 0x000600
[    0.099991] pci 0000:00:00.7: [1106:7204] type 0 class 0x000600
[    0.100050] pci 0000:00:01.0: [1106:b188] type 1 class 0x000604
[    0.100091] pci 0000:00:01.0: supports D1
[    0.100119] pci 0000:00:0a.0: [1106:1249] type 0 class 0x000104
[    0.100136] pci 0000:00:0a.0: reg 10: [io  0xa000-0xa00f]
[    0.100146] pci 0000:00:0a.0: reg 14: [io  0xa400-0xa40f]
[    0.100157] pci 0000:00:0a.0: reg 18: [io  0xa800-0xa80f]
[    0.100167] pci 0000:00:0a.0: reg 1c: [io  0xac00-0xac0f]
[    0.100177] pci 0000:00:0a.0: reg 20: [io  0xb000-0xb01f]
[    0.100188] pci 0000:00:0a.0: reg 24: [io  0xb400-0xb4ff]
[    0.100198] pci 0000:00:0a.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.100237] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000101
[    0.100254] pci 0000:00:0f.0: reg 10: [io  0xb800-0xb807]
[    0.100264] pci 0000:00:0f.0: reg 14: [io  0xbc00-0xbc03]
[    0.100275] pci 0000:00:0f.0: reg 18: [io  0xc000-0xc007]
[    0.100285] pci 0000:00:0f.0: reg 1c: [io  0xc400-0xc403]
[    0.100295] pci 0000:00:0f.0: reg 20: [io  0xc800-0xc80f]
[    0.100306] pci 0000:00:0f.0: reg 24: [io  0xcc00-0xccff]
[    0.100346] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.100390] pci 0000:00:0f.1: reg 20: [io  0xd000-0xd00f]
[    0.100446] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.100489] pci 0000:00:10.0: reg 20: [io  0xd400-0xd41f]
[    0.100519] pci 0000:00:10.0: supports D1 D2
[    0.100523] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.100529] pci 0000:00:10.0: PME# disabled
[    0.100547] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.100590] pci 0000:00:10.1: reg 20: [io  0xd800-0xd81f]
[    0.100621] pci 0000:00:10.1: supports D1 D2
[    0.100624] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.100629] pci 0000:00:10.1: PME# disabled
[    0.100649] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.100692] pci 0000:00:10.2: reg 20: [io  0xdc00-0xdc1f]
[    0.100723] pci 0000:00:10.2: supports D1 D2
[    0.100726] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.100731] pci 0000:00:10.2: PME# disabled
[    0.100749] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.100793] pci 0000:00:10.3: reg 20: [io  0xe000-0xe01f]
[    0.100823] pci 0000:00:10.3: supports D1 D2
[    0.100827] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.100832] pci 0000:00:10.3: PME# disabled
[    0.100850] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.100867] pci 0000:00:10.4: reg 10: [mem 0xee010000-0xee0100ff]
[    0.100924] pci 0000:00:10.4: supports D1 D2
[    0.100928] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.100933] pci 0000:00:10.4: PME# disabled
[    0.100955] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
[    0.101013] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.101052] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
[    0.101069] pci 0000:00:11.5: reg 10: [io  0xe400-0xe4ff]
[    0.101128] pci 0000:00:11.5: supports D1 D2
[    0.101149] pci 0000:00:12.0: [1106:3065] type 0 class 0x000200
[    0.101167] pci 0000:00:12.0: reg 10: [io  0xec00-0xecff]
[    0.101177] pci 0000:00:12.0: reg 14: [mem 0xee011000-0xee0110ff]
[    0.101229] pci 0000:00:12.0: supports D1 D2
[    0.101232] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101238] pci 0000:00:12.0: PME# disabled
[    0.101257] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.101283] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.101306] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.101327] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.101353] PCI: peer root bus 00 res updated from pci conf
[    0.101389] pci 0000:01:00.0: [1106:3108] type 0 class 0x000300
[    0.101403] pci 0000:01:00.0: reg 10: [mem 0xe8000000-0xebffffff pref]
[    0.101412] pci 0000:01:00.0: reg 14: [mem 0xec000000-0xecffffff]
[    0.101438] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.101454] pci 0000:01:00.0: supports D1 D2
[    0.101483] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.101488] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.101494] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff]
[    0.101500] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xebffffff pref]
[    0.101509] pci_bus 0000:00: on NUMA node 0
[    0.101513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.101842]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.149122] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.149244] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.149368] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.149469] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.149562] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.149651] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.149738] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.149825] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.149952] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.150066] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.150179] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.150323] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.150463] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.150467] vgaarb: loaded
[    0.150469] vgaarb: bridge control possible 0000:01:00.0
[    0.150812] SCSI subsystem initialized
[    0.150906] libata version 3.00 loaded.
[    0.150988] usbcore: registered new interface driver usbfs
[    0.151005] usbcore: registered new interface driver hub
[    0.151045] usbcore: registered new device driver usb
[    0.151171] PCI: Using ACPI for IRQ routing
[    0.151177] PCI: pci_cache_line_size set to 64 bytes
[    0.151259] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.151263] reserve RAM buffer: 000000005bff0000 - 000000005bffffff 
[    0.151412] NetLabel: Initializing
[    0.151415] NetLabel:  domain hash size = 128
[    0.151417] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.151433] NetLabel:  unlabeled traffic allowed by default
[    0.160978] AppArmor: AppArmor Filesystem Enabled
[    0.161026] pnp: PnP ACPI init
[    0.161050] ACPI: bus type pnp registered
[    0.161318] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.161323] pnp 00:00: [mem 0x000f0000-0x000f7fff]
[    0.161326] pnp 00:00: [mem 0x000f8000-0x000fbfff]
[    0.161329] pnp 00:00: [mem 0x000fc000-0x000fffff]
[    0.161333] pnp 00:00: [mem 0x5bff0000-0x5bffffff]
[    0.161336] pnp 00:00: [mem 0xffff0000-0xffffffff]
[    0.161339] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.161343] pnp 00:00: [mem 0x00100000-0x5bfeffff]
[    0.161346] pnp 00:00: [mem 0x5c000000-0x5fffffff]
[    0.161349] pnp 00:00: [mem 0xfec00000-0xfec00fff]
[    0.161353] pnp 00:00: [mem 0xfee00000-0xfee00fff]
[    0.161356] pnp 00:00: [mem 0xfff80000-0xfffeffff]
[    0.161433] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.161438] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.161442] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.161447] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.161451] system 00:00: [mem 0x5bff0000-0x5bffffff] could not be reserved
[    0.161455] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
[    0.161460] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.161464] system 00:00: [mem 0x00100000-0x5bfeffff] could not be reserved
[    0.161468] system 00:00: [mem 0x5c000000-0x5fffffff] has been reserved
[    0.161473] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.161477] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.161481] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.161487] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.161573] pnp 00:01: [bus 00-ff]
[    0.161577] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.161580] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.161584] pnp 00:01: [io  0x0d00-0xffff window]
[    0.161587] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.161591] pnp 00:01: [mem 0x000c0000-0x000dffff window]
[    0.161595] pnp 00:01: [mem 0x60000000-0xfebfffff window]
[    0.161646] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.161672] pnp 00:02: [io  0x4000-0x407f]
[    0.161675] pnp 00:02: [io  0x5000-0x500f]
[    0.161725] system 00:02: [io  0x4000-0x407f] has been reserved
[    0.161729] system 00:02: [io  0x5000-0x500f] has been reserved
[    0.161733] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.162528] pnp 00:03: [io  0x0010-0x001f]
[    0.162531] pnp 00:03: [io  0x0022-0x003f]
[    0.162534] pnp 00:03: [io  0x0044-0x005f]
[    0.162537] pnp 00:03: [io  0x0062-0x0063]
[    0.162540] pnp 00:03: [io  0x0065-0x006f]
[    0.162544] pnp 00:03: [io  0x0074-0x007f]
[    0.162547] pnp 00:03: [io  0x0091-0x0093]
[    0.162550] pnp 00:03: [io  0x00a2-0x00bf]
[    0.162553] pnp 00:03: [io  0x00e0-0x00ef]
[    0.162556] pnp 00:03: [io  0x04d0-0x04d1]
[    0.162559] pnp 00:03: [io  0x0290-0x029f]
[    0.162562] pnp 00:03: [io  0x0800-0x0805]
[    0.162632] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.162636] system 00:03: [io  0x0290-0x029f] has been reserved
[    0.162640] system 00:03: [io  0x0800-0x0805] has been reserved
[    0.162645] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.162661] pnp 00:04: [dma 4]
[    0.162664] pnp 00:04: [io  0x0000-0x000f]
[    0.162667] pnp 00:04: [io  0x0080-0x0090]
[    0.162671] pnp 00:04: [io  0x0094-0x009f]
[    0.162674] pnp 00:04: [io  0x00c0-0x00df]
[    0.162716] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.162731] pnp 00:05: [io  0x0070-0x0073]
[    0.162745] pnp 00:05: [irq 8]
[    0.162784] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.162796] pnp 00:06: [io  0x0061]
[    0.162835] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.162848] pnp 00:07: [io  0x00f0-0x00ff]
[    0.162854] pnp 00:07: [irq 13]
[    0.162895] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.163088] pnp 00:08: [io  0x03f0-0x03f5]
[    0.163092] pnp 00:08: [io  0x03f7]
[    0.163098] pnp 00:08: [irq 6]
[    0.163101] pnp 00:08: [dma 2]
[    0.163159] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.163418] pnp 00:09: [io  0x03f8-0x03ff]
[    0.163425] pnp 00:09: [irq 4]
[    0.163508] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.163783] pnp 00:0a: [io  0x02f8-0x02ff]
[    0.163790] pnp 00:0a: [irq 3]
[    0.163870] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.164445] pnp 00:0b: [io  0x0378-0x037f]
[    0.164449] pnp 00:0b: [io  0x0778-0x077b]
[    0.164455] pnp 00:0b: [irq 7]
[    0.164458] pnp 00:0b: [dma 3]
[    0.164543] pnp 00:0b: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.164613] pnp: PnP ACPI: found 12 devices
[    0.164615] ACPI: ACPI bus type pnp unregistered
[    0.164620] PnPBIOS: Disabled by ACPI PNP
[    0.201385] Switching to clocksource acpi_pm
[    0.201420] PCI: max bus depth: 1 pci_try_num: 2
[    0.201444] pci 0000:00:0a.0: BAR 6: assigned [mem 0x60000000-0x6000ffff pref]
[    0.201450] pci 0000:01:00.0: BAR 6: assigned [mem 0xed000000-0xed00ffff pref]
[    0.201454] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.201457] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.201464] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff]
[    0.201469] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xebffffff pref]
[    0.201484] pci 0000:00:01.0: setting latency timer to 64
[    0.201490] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.201493] pci_bus 0000:00: resource 5 [mem 0x60000000-0xffffffff]
[    0.201497] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.201501] pci_bus 0000:01: resource 1 [mem 0xec000000-0xedffffff]
[    0.201505] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xebffffff pref]
[    0.201569] NET: Registered protocol family 2
[    0.201651] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.202021] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.203214] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.203836] TCP: Hash tables configured (established 131072 bind 65536)
[    0.203841] TCP reno registered
[    0.203847] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.203867] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.204009] NET: Registered protocol family 1
[    0.204009] Switched to NOHz mode on CPU #0
[    0.204009] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.204009] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.204009] pci 0000:01:00.0: Boot video device
[    0.204009] PCI: CLS 32 bytes, default 64
[    0.204009] audit: initializing netlink socket (disabled)
[    0.204009] type=2000 audit(1319136610.200:1): initialized
[    0.232929] Trying to unpack rootfs image as initramfs...
[    0.280250] highmem bounce pool size: 64 pages
[    0.280261] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.304535] VFS: Disk quotas dquot_6.5.2
[    0.304639] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.305632] fuse init (API version 7.16)
[    0.305772] msgmni has been set to 1694
[    0.316586] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.320119] io scheduler noop registered
[    0.320124] io scheduler deadline registered
[    0.320182] io scheduler cfq registered (default)
[    0.320390] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.320429] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.320604] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.320612] ACPI: Power Button [PWRB]
[    0.320681] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.320685] ACPI: Power Button [PWRF]
[    0.320716] ACPI: acpi_idle registered with cpuidle
[    0.400493] thermal LNXTHERM:00: registered as thermal_zone0
[    0.400499] ACPI: Thermal Zone [THRM] (40 C)
[    0.400563] ERST: Table is not found!
[    0.400689] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.421000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.424082] isapnp: Scanning for PnP cards...
[    0.512540] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.554109] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.636672] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.660471] Linux agpgart interface v0.103
[    0.660507] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
[    0.668419] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    0.670101] brd: module loaded
[    0.670897] loop: module loaded
[    0.671382] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.671404] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.671475] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.671493] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.671518] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.676418] Fixed MDIO Bus: probed
[    0.676471] PPP generic driver version 2.4.2
[    0.676563] tun: Universal TUN/TAP device driver, 1.6
[    0.676566] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.676679] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.676888] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.676911] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.676933] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.676982] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.677060] ehci_hcd 0000:00:10.4: irq 21, io mem 0xee010000
[    0.720611] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.720802] hub 1-0:1.0: USB hub found
[    0.720809] hub 1-0:1.0: 8 ports detected
[    0.720911] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.720931] uhci_hcd: USB Universal Host Controller Interface driver
[    0.720992] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.721004] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.721058] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.721087] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    0.721254] hub 2-0:1.0: USB hub found
[    0.721260] hub 2-0:1.0: 2 ports detected
[    0.721338] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.721346] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.721392] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.721416] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    0.721578] hub 3-0:1.0: USB hub found
[    0.721583] hub 3-0:1.0: 2 ports detected
[    0.721654] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.721662] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.721708] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.721731] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.721900] hub 4-0:1.0: USB hub found
[    0.721905] hub 4-0:1.0: 2 ports detected
[    0.721976] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.721984] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.722033] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.722057] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e000
[    0.722220] hub 5-0:1.0: USB hub found
[    0.722225] hub 5-0:1.0: 2 ports detected
[    0.722374] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.800536] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.800555] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.800774] mousedev: PS/2 mouse device common for all mice
[    0.800935] rtc_cmos 00:05: RTC can wake from S4
[    0.801095] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.801150] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.801314] device-mapper: uevent: version 1.0.3
[    0.801421] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.801469] EISA: Probing bus 0 at eisa.0
[    0.801472] EISA: Cannot allocate resource for mainboard
[    0.801476] Cannot allocate resource for EISA slot 1
[    0.801479] Cannot allocate resource for EISA slot 2
[    0.801482] Cannot allocate resource for EISA slot 3
[    0.801486] Cannot allocate resource for EISA slot 4
[    0.801489] Cannot allocate resource for EISA slot 5
[    0.801492] Cannot allocate resource for EISA slot 6
[    0.801495] Cannot allocate resource for EISA slot 7
[    0.801498] Cannot allocate resource for EISA slot 8
[    0.801501] EISA: Detected 0 cards.
[    0.801515] cpufreq-nforce2: No nForce2 chipset.
[    0.801518] cpuidle: using governor ladder
[    0.801521] cpuidle: using governor menu
[    0.801524] EFI Variables Facility v0.08 2004-May-17
[    0.801866] TCP cubic registered
[    0.802056] NET: Registered protocol family 10
[    0.802766] NET: Registered protocol family 17
[    0.802795] Registering the dns_resolver key type
[    0.802824] Using IPI No-Shortcut mode
[    0.802956] PM: Hibernation image not present or could not be loaded.
[    0.802970] registered taskstats version 1
[    1.088017] isapnp: No Plug & Play device found
[    1.158296] Freeing initrd memory: 13300k freed
[    1.183116]   Magic number: 15:225:848
[    1.183250] rtc_cmos 00:05: setting system clock to 2011-10-20 18:50:11 UTC (1319136611)
[    1.183254] powernow-k8: Power state transitions not supported
[    1.183287] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20110413/processor_perflib-318)
[    1.183298] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.183301] EDD information not available.
[    1.183449] Freeing unused kernel memory: 696k freed
[    1.184219] Write protecting the kernel text: 5332k
[    1.184266] Write protecting the kernel read-only data: 2188k
[    1.214566] udevd[77]: starting version 173
[    1.232085] Refined TSC clocksource calibration: 1599.818 MHz.
[    1.232096] Switching to clocksource tsc
[    1.296077] usb 5-1: new low speed USB device number 2 using uhci_hcd
[    1.400250] FDC 0 is a post-1991 82077
[    1.410504] sata_via 0000:00:0f.0: version 2.6
[    1.410527] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.410576] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.431004] scsi0 : sata_via
[    1.434629] scsi1 : sata_via
[    1.434729] ata1: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 20
[    1.434734] ata2: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 20
[    1.435305] pata_via 0000:00:0f.1: version 0.3.4
[    1.435329] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.438136] scsi2 : pata_via
[    1.440062] scsi3 : pata_via
[    1.441521] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    1.441525] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    1.458391] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    1.458398] via_rhine: Broken BIOS detected, avoid_D3 enabled
[    1.458606] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.458624] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.488402] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xee011000, 00:16:ec:17:2d:19, IRQ 23
[    1.489116] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link cde1
[    1.636015] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.648450] usbcore: registered new interface driver usbhid
[    1.648455] usbhid: USB HID core driver
[    1.800188] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7BP, max UDMA/100
[    1.800193] ata1.00: 234441648 sectors, multi 16: LBA48 
[    1.816186] ata1.00: configured for UDMA/100
[    1.816327] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    1.816563] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.816705] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.816770] sd 0:0:0:0: [sda] Write Protect is off
[    1.816774] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.816801] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.861513]  sda: sda1 sda2 < sda5 >
[    1.861908] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.020014] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.223605] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.0/input/input2
[    2.223740] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:10.3-1/input0
[    2.320058] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.1/input/input3
[    2.320450] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:10.3-1/input1
[    2.536978] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.536985] EXT4-fs (sda1): write access will be enabled during recovery
[    8.836797] EXT4-fs (sda1): orphan cleanup on readonly fs
[    8.836812] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729714
[    8.836910] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4728205
[    8.836931] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4719388
[    8.837015] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4719033
[    8.837035] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729583
[    8.837054] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729527
[    8.837119] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4727957
[    8.865288] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 655632
[    8.892751] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4721835
[    8.892779] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4718854
[    8.892799] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7082187
[    8.892845] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729629
[    8.892898] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729627
[    8.892916] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729577
[    8.892934] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729575
[    8.892952] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729574
[    8.892970] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729568
[    8.892989] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729545
[    8.893016] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729520
[    8.893038] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729516
[    8.910607] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4728494
[    8.921061] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4718804
[    8.921085] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729524
[    8.921103] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729517
[    8.921121] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7081229
[    8.921139] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7081228
[    8.937651] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4729221
[    8.937675] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4721951
[    8.937695] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4728244
[    8.938646] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4727844
[    8.938668] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4727918
[    8.952514] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4726788
[    8.952537] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4721796
[    8.952555] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4718688
[    8.952573] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4727065
[    8.967431] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4721462
[    8.967507] EXT4-fs (sda1): 36 orphan inodes deleted
[    8.967510] EXT4-fs (sda1): recovery complete
[    9.331365] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   37.503936] udevd[299]: starting version 173
[   37.553580] lp: driver loaded but no devices found
[   37.636357] Adding 455676k swap on /dev/sda5.  Priority:-1 extents:1 across:455676k 
[   37.720628] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   37.794917] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.898472] parport_pc 00:0b: reported by Plug and Play ACPI
[   37.898557] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.040406] lp0: using parport0 (interrupt-driven).
[   38.062087] type=1400 audit(1319136648.374:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=505 comm="apparmor_parser"
[   38.076927] type=1400 audit(1319136648.390:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=505 comm="apparmor_parser"
[   38.077316] type=1400 audit(1319136648.390:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=505 comm="apparmor_parser"
[   38.431248] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   39.385311] type=1400 audit(1319136649.698:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=787 comm="apparmor_parser"
[   39.389296] type=1400 audit(1319136649.702:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=791 comm="apparmor_parser"
[   39.397420] type=1400 audit(1319136649.710:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=792 comm="apparmor_parser"
[   39.405801] type=1400 audit(1319136649.718:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=792 comm="apparmor_parser"
[   39.406222] type=1400 audit(1319136649.718:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=792 comm="apparmor_parser"
[   39.445165] type=1400 audit(1319136649.758:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=796 comm="apparmor_parser"
[   39.463391] type=1400 audit(1319136649.774:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=796 comm="apparmor_parser"
[   39.513323] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   39.513346] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   39.513512] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   39.707192] ppdev: user-space parallel port driver
[   39.858650] init: failsafe main process (710) killed by TERM signal
[   39.868946] init: apport pre-start process (856) terminated with status 1
[   39.873595] init: alsa-restore main process (863) terminated with status 19
[   39.932566] init: apport post-stop process (896) terminated with status 1
[   40.239403] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   40.239409] vesafb: scrolling: redraw
[   40.239413] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   40.239667] vesafb: framebuffer at 0xe8000000, mapped to 0xf8380000, using 1216k, total 1216k
[   40.239806] fbcon: VESA VGA (fb0) is primary device
[   40.239957] Console: switching to colour frame buffer device 80x30
[   40.239978] fb0: VESA VGA frame buffer device
[   40.386479] init: gdm main process (1096) killed by TERM signal
[   40.802884] Bluetooth: Core ver 2.16
[   40.802942] NET: Registered protocol family 31
[   40.802945] Bluetooth: HCI device and connection manager initialized
[   40.802949] Bluetooth: HCI socket layer initialized
[   40.802952] Bluetooth: L2CAP socket layer initialized
[   40.809029] Bluetooth: SCO socket layer initialized
[   40.816093] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.816099] Bluetooth: BNEP filters: protocol multicast
[   40.849141] Bluetooth: RFCOMM TTY layer initialized
[   40.849156] Bluetooth: RFCOMM socket layer initialized
[   40.849160] Bluetooth: RFCOMM ver 1.11
[   40.868160] [drm] Initialized drm 1.1.0 20060810
[   40.870086] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.873249] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   40.873256] [drm] No driver support for vblank timestamp query.
[   40.873262] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   40.904809] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   40.904832] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   40.904909] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   43.204109] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   43.720431] init: plymouth-stop pre-start process (1414) terminated with status 1
[   46.352232] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   49.440015] eth0: no IPv6 routers present


```

---

### Post by WorMzy on 2011-10-20
Hm, alright. Can you post the output of this command now:

```
zgrep "SATA_VIA\|VIA_RHINE\|PATA_VIA\|CONFIG_SATA_PMP" /proc/config.gz
```

---

### Post by Aligore on 2011-10-20
I just get gzip: /proc/config.gz: No such file or directory

---

### Post by Aligore on 2011-10-21
Ok ive just installed the sata controller card in a windows box attached the hard drive and it works fine. But I want it in my server running Ubuntu does this mean I'm going to go back to the dark side of MS?

---

### Post by WorMzy on 2011-10-21
Possibly, unless someone else can think of something.

I must say that it's a poor show by Ubuntu that they don't enable IKCONFIG_PROC (which creates /proc/config.gz). I'm fairly sure they used to.

As it stands, I'm out of ideas. I don't want to send you down the route of kernel compilation without knowing for sure that the kernel drivers are the problem.

---

### Post by Aligore on 2011-10-21
Thx for your help anyway. I am installing windows on a spare drive for now, at some point I would like to do the Linux root again but there's not much point ATM if I can't get the drive to work

---

### Post by WorMzy on 2011-10-21
I recommend that you try some LiveCDs of other distributions. I know Ubuntu has let you down, but there's plenty of other distributions out there that might support your controller+disk right out of the box. Mint and Debian are in the same family as Ubuntu, so you might want to give them a try first. If neither of those are any good, then try OpenSUSE.

---

### Post by kaldor on 2011-10-21
> **WorMzy said:**
> I recommend that you try some LiveCDs of other distributions. I know Ubuntu has let you down, but there's plenty of other distributions out there that might support your controller+disk right out of the box. Mint and Debian are in the same family as Ubuntu, so you might want to give them a try first. If neither of those are any good, then try OpenSUSE.

I agree with this, except I'd recommend a different system.

Mint is just Ubuntu with a different UI- problems on Ubuntu will likely transfer over to Mint. Debian has this annoying "free only" policy, which tends to cause headaches when working with certain hardware. OpenSUSE might work, but I hate its package management.

If you want a very stable setup, check the Scientific Linux link in my sig. SL 6 is a very robust desktop (based on [_RHEL_]("http://en.wikipedia.org/wiki/RHEL")) and aimed towards enterprise and university users. The desktop version has a very easy installer, and I can't say enough good about the distro as a whole. It's definitely one of the gems of Linux :KS

---

