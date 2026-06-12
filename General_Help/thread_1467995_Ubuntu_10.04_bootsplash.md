---
title: "Ubuntu 10.04 bootsplash"
date: 2010-05-01
forum: General Help
---

### Post by dioxip on 2010-05-01
Hello everyone!

Yesterday I updated from 9.10 karmic to 10.04 LTS. Everything worked fine until, I restarted. Upon logout there are no splash screen like I had before in the 9.10, and my fan on my gfx are going crazy, spining at 100%.

Well then I got to the grub loader, and discovered my boot splash was gone to. The only thing which is displayed on the screen are:
mount dev /dev failed device71......
Starting up..

Then 10 seconds later alot of texts shows up and I get the login screen.

I've looked around on the forum and other sites for a solution, but with no luck. 

I hope one of you have a solution, cause I miss my bootscreen :(

//dioxip

---

### Post by P4man on 2010-05-01
its trying to mount something and failing.
Can you give us the output of

```
cat /etc/fstab
```

and 

```
sudo fdisk -l
```
(FDISK -L in lowercase)

---

### Post by dioxip on 2010-05-01
Here you go. :)




```
klim@klim-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=6fd235c2-453a-4d83-bd13-c5a7163311e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=7cb22370-b01f-4afc-8248-bd62df0ebf11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5       /media/500GB ntfs-3g  defaults  0   0
/dev/sdc2	/media/iPod vfat	nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8	0 0

```

```
klim@klim-desktop:~$ sudo fdisk -l
[sudo] password for klim: 

Disk /dev/sda: 164.7 Gb, 164696555520 byte
255 heads, 63 sectors/track, 20023 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd6dcd6d

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14        1566    12474472+  83  Linux
/dev/sda3   *        1567        4116    20481024    7  HPFS/NTFS
/dev/sda4            4117       20023   127772977+   5  Udvidet
/dev/sda5            4117        5391    10241406    7  HPFS/NTFS
/dev/sda6            5392        5515      995998+  82  Linux swap / Solaris
/dev/sda7            5516       11924    51480261   83  Linux
/dev/sda8           11925       20023    65055186    7  HPFS/NTFS

Disk /dev/sdb: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93f043d3

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sdb2               2       60801   488376000    f  w95 udvidet (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 Gb, 203928109056 byte
255 heads, 63 sectors/track, 24792 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003197b

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sdc2   *           2       24792   199133707+   5  Udvidet
/dev/sdc5               2        8925    71681998+   7  HPFS/NTFS
/dev/sdc6            8926       24792   127451646    7  HPFS/NTFS

```

---

### Post by P4man on 2010-05-01
try commenting out the line mounting the cdrom (/dev/scd0). I dont think its necessary. Could also be the ipod I guess.

---

### Post by dioxip on 2010-05-01
I've tried to uncomment the ipod now, but the mount /dev failed still show up. 

Well, lets forget about that cause I think it always have been like that. The one thing im missing is the bootsplash, like this [http://n00bsonubuntu.com/system/files/boot10.04.png]("http://n00bsonubuntu.com/system/files/boot10.04.png")

and the same for the logout/shutdown screen. Are there a way to check if it's installed or reinstall it?

---

### Post by P4man on 2010-05-01
Try this:

```

sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit


```

May slow your boot by half a second or so, but may well enable the splash screen (although it may not look pretty with the mount error, try removing the cd entry)

---

### Post by WorMzy on 2010-05-01
I don't know whether your comments are obsolete, or your UUIDs are wrong, but your fstab says swap was on /dev/sda8, but according to your fdisk, that partition is an NTFS partition. Same with your /, /dev/sda9 doesn't exist, although you must have altered the UUID for that disk since you're able to boot.

Could you do 'sudo blkid' and post the results here?

As for the boot splash, Lucid uses Plymouth to display a boot splash, so try running 'sudo dpkg-reconfigure plymouth'.

---

### Post by dioxip on 2010-05-01
> **P4man said:**
> Try this:

```

sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit


```

May slow your boot by half a second or so, but may well enable the splash screen (although it may not look pretty with the mount error, try removing the cd entry)

I didnt solve the problem with the boot splash :(

WorMzy

Here is the blkid, Im trying your suggestion with the boot splash in a sec.

```
klim@klim-desktop:~$ sudo blkid
/dev/sda1: UUID="32db9ecf-4946-4fd0-adb6-b7edbaab28b8" TYPE="ext4" 
/dev/sda2: UUID="210333c9-72da-4392-b17a-23662cfd31a6" TYPE="ext4" 
/dev/sda3: UUID="B47E8A987E8A52D2" TYPE="ntfs" 
/dev/sda5: LABEL="Musik" UUID="A690ACB090AC887F" TYPE="ntfs" 
/dev/sda6: UUID="7cb22370-b01f-4afc-8248-bd62df0ebf11" TYPE="swap" 
/dev/sda7: UUID="6fd235c2-453a-4d83-bd13-c5a7163311e2" TYPE="ext4" 
/dev/sda8: LABEL="Spil" UUID="4864ED6C64ED5CE6" TYPE="ntfs" 
/dev/sdb5: LABEL="500GB" UUID="9979365EFA924345" TYPE="ntfs" 
/dev/sdc5: LABEL="Film" UUID="130692D7A26F2591" TYPE="ntfs" 
/dev/sdc6: LABEL="Ekstra" UUID="02052EA38E982310" TYPE="ntfs" 

```

From the numbers after sda7 c5a7163311e2 at the end, something similar are the mount failed displaying at bootup.

EDIT:

It changed the bootup screen a bit, but not as it should be. The text are just scrolling down now, and displaying Ubuntu 10.04 with 4 dots below half a second after. Then the login screen appears. 

At the top it says Mount: mouting none on /dev failed: No such devicea7163311e2

---

### Post by WorMzy on 2010-05-01
There doesn't appear to be anything wrong with your fstab, all the UUIDs are correct, and compared to my fstab the only difference is: instead of proc having default options, mine has nodev,noexec,nosuid. I doubt that changing yours to the same would make any difference.

Oh, mine doesn't have a cdrom entry either. Just proc, / and swap (and then my main storage partition). You might want to remove the "defaults" from the list of options for /media/iPod, and I'm not sure why you're mounting it as FAT.

I'm not sure what else to do with your boot splash. I've set my grub entry to not use splash since it looks hideous and deformed when you have nVidia drivers enabled.

---

### Post by P4man on 2010-05-01
> **dioxip said:**
> 
At the top it says Mount: mouting none on /dev failed: No such devicea7163311e2

Is that an exact message or you doing your best catching it, remembering it and typing it?
Can we see the ouput of dmesg ?

---

### Post by dioxip on 2010-05-01
> **P4man said:**
> Is that an exact message or you doing your best catching it, remembering it and typing it?
Can we see the ouput of dmesg ?

Thats the exact message, I took a picture of it.

Here the full output from /var/log/dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff70000 (usable)
[    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff7e000 - 000000007ffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
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
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff70000 (usable)
[    0.000000]  modified: 000000007ff70000 - 000000007ff7e000 (ACPI data)
[    0.000000]  modified: 000000007ff7e000 - 000000007ffd0000 (ACPI NVS)
[    0.000000]  modified: 000000007ffd0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 378a5000 - 37fef9ce
[    0.000000] Allocated new RAMDISK: 008b2000 - 00ffc9ce
[    0.000000] Move RAMDISK from 00000000378a5000 - 0000000037fef9cd to 008b2000 - 00ffc9cd
[    0.000000] ACPI: RSDP 000fb410 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ff70000 0003C (v01 A_M_I_ OEMRSDT  12000811 MSFT 00000097)
[    0.000000] ACPI: FACP 7ff70200 00084 (v02 A_M_I_ OEMFACP  12000811 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ff70440 096D5 (v01  A0999 A0999001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 7ff7e000 00040
[    0.000000] ACPI: APIC 7ff70390 0006C (v01 A_M_I_ OEMAPIC  12000811 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ff70400 0003C (v01 A_M_I_ OEMMCFG  12000811 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ff7e040 00089 (v01 A_M_I_ AMI_OEM  12000811 MSFT 00000097)
[    0.000000] ACPI: HPET 7ff79b20 00038 (v01 A_M_I_ OEMHPET  12000811 MSFT 00000097)
[    0.000000] ACPI: OSFR 7ff79b60 000B0 (v01 A_M_I_ OEMOSFR  12000811 MSFT 00000097)
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
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b1224]              BRK ==> [00008ae000 - 00008b1224]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008b2000 - 0000ffc9ce]      NEW RAMDISK ==> [00008b2000 - 0000ffc9ce]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007ff70
[    0.000000] On node 0 totalpages: 524029
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2319 pages used for memmap
[    0.000000]   HighMem zone: 294499 pages, LIFO batch:31
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
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519934
[    0.000000] Kernel command line: root=UUID=6fd235c2-453a-4d83-bd13-c5a7163311e2 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10482560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ff70)
[    0.000000] Memory: 2052132k/2096576k available (4578k kernel code, 43048k reserved, 2146k data, 540k init, 1187272k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 4724.873 MHz processor.
[    0.000990] Console: colour VGA+ 80x25
[    0.000991] console [tty0] enabled
[    0.001065] hpet clockevent registered
[    0.001067] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001070] Calibrating delay loop (skipped), value calculated using timer frequency.. 9449.74 BogoMIPS (lpj=18899492)
[    0.001079] Security Framework initialized
[    0.001089] AppArmor: AppArmor initialized
[    0.001092] Mount-cache hash table entries: 512
[    0.001154] Initializing cgroup subsys ns
[    0.001157] Initializing cgroup subsys cpuacct
[    0.001159] Initializing cgroup subsys memory
[    0.001162] Initializing cgroup subsys freezer
[    0.001163] Initializing cgroup subsys net_cls
[    0.001170] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001171] CPU: L2 cache: 6144K
[    0.001173] CPU: Physical Processor ID: 0
[    0.001173] CPU: Processor Core ID: 0
[    0.001176] mce: CPU supports 6 MCE banks
[    0.001180] CPU0: Thermal monitoring enabled (TM1)
[    0.001181] using mwait in idle threads.
[    0.001184] Performance Counters: Core2 events, Intel PMU driver.
[    0.001188] ... version:                 2
[    0.001189] ... bit width:               40
[    0.001190] ... generic counters:        2
[    0.001191] ... value mask:              000000ffffffffff
[    0.001192] ... max period:              000000007fffffff
[    0.001192] ... fixed-purpose counters:  3
[    0.001193] ... counter mask:            0000000700000003
[    0.001195] Checking 'hlt' instruction... OK.
[    0.017343] ACPI: Core revision 20090521
[    0.024313] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066351] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 9449.89 BogoMIPS (lpj=18899796)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.153187] CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.153194] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.156013] Brought up 2 CPUs
[    0.156014] Total of 2 processors activated (18899.64 BogoMIPS).
[    0.156051] CPU0 attaching sched-domain:
[    0.156052]  domain 0: span 0-1 level MC
[    0.156053]   groups: 0 1
[    0.156056] CPU1 attaching sched-domain:
[    0.156057]  domain 0: span 0-1 level MC
[    0.156058]   groups: 1 0
[    0.156097] Booting paravirtualized kernel on bare hardware
[    0.156101] regulator: core version 0.5
[    0.156101] Time: 17:40:42  Date: 05/01/10
[    0.156101] NET: Registered protocol family 16
[    0.156104] EISA bus registered
[    0.156108] ACPI: bus type pci registered
[    0.156142] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.156143] PCI: Not using MMCONFIG.
[    0.156178] PCI: BIOS BUG #b1[49435000] found
[    0.156179] PCI: Using configuration type 1 for base access
[    0.156652] bio: create slab <bio-0> at 0
[    0.156652] ACPI: EC: Look up EC in DSDT
[    0.165701] ACPI: Interpreter enabled
[    0.165705] ACPI: (supports S0 S1 S3 S4 S5)
[    0.165715] ACPI: Using IOAPIC for interrupt routing
[    0.165740] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.167092] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.167093] PCI: Using MMCONFIG for extended config space
[    0.170790] ACPI Warning: Incorrect checksum in table [OEMB] - 2F, should be 2E 20090521 tbutils-246
[    0.170861] ACPI: No dock devices found.
[    0.170939] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.170986] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.170988] pci 0000:00:01.0: PME# disabled
[    0.171033] pci 0000:00:1a.0: reg 20 io port: [0xa800-0xa81f]
[    0.171080] pci 0000:00:1a.1: reg 20 io port: [0xa880-0xa89f]
[    0.171126] pci 0000:00:1a.2: reg 20 io port: [0xac00-0xac1f]
[    0.171176] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfbfffc00-0xfbffffff]
[    0.171215] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.171217] pci 0000:00:1a.7: PME# disabled
[    0.171244] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbff8000-0xfbffbfff]
[    0.171271] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.171274] pci 0000:00:1b.0: PME# disabled
[    0.171311] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.171313] pci 0000:00:1c.0: PME# disabled
[    0.171353] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.171355] pci 0000:00:1c.4: PME# disabled
[    0.171394] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.171396] pci 0000:00:1c.5: PME# disabled
[    0.171432] pci 0000:00:1d.0: reg 20 io port: [0xa080-0xa09f]
[    0.171480] pci 0000:00:1d.1: reg 20 io port: [0xa400-0xa41f]
[    0.171526] pci 0000:00:1d.2: reg 20 io port: [0xa480-0xa49f]
[    0.171576] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfbfff800-0xfbfffbff]
[    0.171614] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.171617] pci 0000:00:1d.7: PME# disabled
[    0.171700] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.171703] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.171705] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.171708] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
[    0.171744] pci 0000:00:1f.2: reg 10 io port: [0x9000-0x9007]
[    0.171747] pci 0000:00:1f.2: reg 14 io port: [0x8c00-0x8c03]
[    0.171751] pci 0000:00:1f.2: reg 18 io port: [0x8880-0x8887]
[    0.171754] pci 0000:00:1f.2: reg 1c io port: [0x8800-0x8803]
[    0.171757] pci 0000:00:1f.2: reg 20 io port: [0x8480-0x848f]
[    0.171761] pci 0000:00:1f.2: reg 24 io port: [0x8400-0x840f]
[    0.171790] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfbfff400-0xfbfff4ff]
[    0.171799] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.171827] pci 0000:00:1f.5: reg 10 io port: [0xa000-0xa007]
[    0.171830] pci 0000:00:1f.5: reg 14 io port: [0x9c00-0x9c03]
[    0.171834] pci 0000:00:1f.5: reg 18 io port: [0x9880-0x9887]
[    0.171837] pci 0000:00:1f.5: reg 1c io port: [0x9800-0x9803]
[    0.171841] pci 0000:00:1f.5: reg 20 io port: [0x9480-0x948f]
[    0.171844] pci 0000:00:1f.5: reg 24 io port: [0x9400-0x940f]
[    0.171879] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.171884] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.171889] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.171892] pci 0000:01:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.171896] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe8e0000-0xfe8fffff]
[    0.171932] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.171934] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfe8fffff]
[    0.171936] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.171964] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfaf00000-0xfaffffff]
[    0.172013] pci 0000:03:00.0: reg 10 io port: [0xdc00-0xdc07]
[    0.172019] pci 0000:03:00.0: reg 14 io port: [0xd880-0xd883]
[    0.172025] pci 0000:03:00.0: reg 18 io port: [0xd800-0xd807]
[    0.172030] pci 0000:03:00.0: reg 1c io port: [0xd480-0xd483]
[    0.172036] pci 0000:03:00.0: reg 20 io port: [0xd400-0xd40f]
[    0.172042] pci 0000:03:00.0: reg 24 32bit mmio: [0xfeaffc00-0xfeafffff]
[    0.172073] pci 0000:03:00.0: supports D1
[    0.172074] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.172077] pci 0000:03:00.0: PME# disabled
[    0.172109] pci 0000:00:1c.4: bridge io port: [0xd000-0xdfff]
[    0.172111] pci 0000:00:1c.4: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.172159] pci 0000:02:00.0: reg 10 64bit mmio: [0xfe9fc000-0xfe9fffff]
[    0.172165] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.172185] pci 0000:02:00.0: reg 30 32bit mmio: [0xfe9c0000-0xfe9dffff]
[    0.172216] pci 0000:02:00.0: supports D1 D2
[    0.172217] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172220] pci 0000:02:00.0: PME# disabled
[    0.172249] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.172251] pci 0000:00:1c.5: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.172276] pci 0000:05:00.0: reg 10 io port: [0xec00-0xec1f]
[    0.172309] pci 0000:05:00.0: supports D1 D2
[    0.172339] pci 0000:05:02.0: reg 10 32bit mmio: [0xfebfc000-0xfebfffff]
[    0.172344] pci 0000:05:02.0: reg 14 io port: [0xe800-0xe8ff]
[    0.172362] pci 0000:05:02.0: reg 30 32bit mmio: [0xfebc0000-0xfebdffff]
[    0.172379] pci 0000:05:02.0: supports D1 D2
[    0.172380] pci 0000:05:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172383] pci 0000:05:02.0: PME# disabled
[    0.172407] pci 0000:05:03.0: reg 10 32bit mmio: [0xfebfb000-0xfebfbfff]
[    0.172440] pci 0000:05:03.0: supports D1 D2
[    0.172441] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.172443] pci 0000:05:03.0: PME# disabled
[    0.172474] pci 0000:00:1e.0: transparent bridge
[    0.172476] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.172478] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.172493] pci_bus 0000:00: on NUMA node 0
[    0.172496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.172580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.172610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.172666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.172694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.172735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.180618] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.180675] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.180731] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.180787] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.180843] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.180899] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.180955] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.181011] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.181097] SCSI subsystem initialized
[    0.181105] libata version 3.00 loaded.
[    0.181105] usbcore: registered new interface driver usbfs
[    0.181105] usbcore: registered new interface driver hub
[    0.181105] usbcore: registered new device driver usb
[    0.181105] ACPI: WMI: Mapper loaded
[    0.181105] PCI: Using ACPI for IRQ routing
[    0.192004] Bluetooth: Core ver 2.15
[    0.192010] NET: Registered protocol family 31
[    0.192010] Bluetooth: HCI device and connection manager initialized
[    0.192010] Bluetooth: HCI socket layer initialized
[    0.192010] NetLabel: Initializing
[    0.192010] NetLabel:  domain hash size = 128
[    0.192010] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192016] NetLabel:  unlabeled traffic allowed by default
[    0.192030] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.192032] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.208004] pnp: PnP ACPI init
[    0.208008] ACPI: bus type pnp registered
[    0.209521] pnp: PnP ACPI: found 15 devices
[    0.209522] ACPI: ACPI bus type pnp unregistered
[    0.209524] PnPBIOS: Disabled by ACPI PNP
[    0.209528] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.209532] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.209535] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.209536] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.209537] system 00:07: ioport range 0x500-0x57f could not be reserved
[    0.209539] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.209540] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.209541] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.209543] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.209546] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.209548] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.209550] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.209552] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.209555] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.209556] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.209558] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.209559] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.209560] system 00:0e: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.244122] AppArmor: AppArmor Filesystem Enabled
[    0.244131] pci 0000:05:02.0: BAR 6: address space collision on of device [0xfebc0000-0xfebdffff]
[    0.244152] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.244154] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.244156] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfe8fffff
[    0.244158] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.244160] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.244161] pci 0000:00:1c.0:   IO window: disabled
[    0.244163] pci 0000:00:1c.0:   MEM window: disabled
[    0.244166] pci 0000:00:1c.0:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.244169] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.244171] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.244174] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.244176] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.244178] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.244180] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.244183] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.244185] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.244187] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.244189] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.244192] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.244194] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x800fffff
[    0.244199]   alloc irq_desc for 16 on node -1
[    0.244200]   alloc kstat_irqs on node -1
[    0.244202] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.244204] pci 0000:00:01.0: setting latency timer to 64
[    0.244207]   alloc irq_desc for 17 on node -1
[    0.244208]   alloc kstat_irqs on node -1
[    0.244210] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.244212] pci 0000:00:1c.0: setting latency timer to 64
[    0.244216] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.244218] pci 0000:00:1c.4: setting latency timer to 64
[    0.244222] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.244224] pci 0000:00:1c.5: setting latency timer to 64
[    0.244228] pci 0000:00:1e.0: setting latency timer to 64
[    0.244230] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.244231] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.244232] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.244233] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfe8fffff]
[    0.244235] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.244236] pci_bus 0000:04: resource 2 pref mem [0xfaf00000-0xfaffffff]
[    0.244237] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.244239] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.244240] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.244241] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.244242] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.244243] pci_bus 0000:05: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.244245] pci_bus 0000:05: resource 2 pref mem [0x80000000-0x800fffff]
[    0.244246] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.244247] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.244261] NET: Registered protocol family 2
[    0.244303] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.244431] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.244613] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.244690] TCP: Hash tables configured (established 131072 bind 65536)
[    0.244691] TCP reno registered
[    0.244721] NET: Registered protocol family 1
[    0.244744] Trying to unpack rootfs image as initramfs...
[    0.332732] Freeing initrd memory: 7466k freed
[    0.334278] cpufreq-nforce2: No nForce2 chipset.
[    0.334293] Scanning for low memory corruption every 60 seconds
[    0.334350] audit: initializing netlink socket (disabled)
[    0.334359] type=2000 audit(1272735641.332:1): initialized
[    0.338511] highmem bounce pool size: 64 pages
[    0.338513] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.339200] VFS: Disk quotas dquot_6.5.2
[    0.339228] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.339486] fuse init (API version 7.12)
[    0.339523] msgmni has been set to 1705
[    0.339629] alg: No test for stdrng (krng)
[    0.339636] io scheduler noop registered
[    0.339637] io scheduler anticipatory registered
[    0.339638] io scheduler deadline registered
[    0.339657] io scheduler cfq registered (default)
[    0.339755] pci 0000:01:00.0: Boot video device
[    0.339812]   alloc irq_desc for 24 on node -1
[    0.339813]   alloc kstat_irqs on node -1
[    0.339818] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.339821] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.339874]   alloc irq_desc for 25 on node -1
[    0.339875]   alloc kstat_irqs on node -1
[    0.339879] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.339884] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.339949]   alloc irq_desc for 26 on node -1
[    0.339950]   alloc kstat_irqs on node -1
[    0.339954] pcieport-driver 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.339958] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.340029]   alloc irq_desc for 27 on node -1
[    0.340029]   alloc kstat_irqs on node -1
[    0.340033] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.340038] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.340086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.340136] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.340202] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.340204] ACPI: Power Button [PWRF]
[    0.340233] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.340235] ACPI: Power Button [PWRB]
[    0.340389] processor LNXCPU:00: registered as cooling_device0
[    0.340408] processor LNXCPU:01: registered as cooling_device1
[    0.341556] isapnp: Scanning for PnP cards...
[    0.501217] Switched to high resolution mode on CPU 1
[    0.504005] Switched to high resolution mode on CPU 0
[    0.694171] isapnp: No Plug & Play device found
[    0.694687] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.694764] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.694995] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.695470] brd: module loaded
[    0.695676] loop: module loaded
[    0.695708] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.695742] ahci 0000:03:00.0: version 3.0
[    0.695764] ata_piix 0000:00:1f.2: version 2.13
[    0.695771]   alloc irq_desc for 19 on node -1
[    0.695772]   alloc kstat_irqs on node -1
[    0.695774] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.695777] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.695802] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.695843] scsi0 : ata_piix
[    0.695875] scsi1 : ata_piix
[    0.696544] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
[    0.696547] ata2: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
[    0.696558] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.696562] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.696582] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.696602] scsi2 : ata_piix
[    0.696629] scsi3 : ata_piix
[    0.697227] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
[    0.697230] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
[    0.697432] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.697447] pata_marvell 0000:03:00.0: setting latency timer to 64
[    0.697480] scsi4 : pata_marvell
[    0.697515] scsi5 : pata_marvell
[    0.697534] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    0.697535] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    0.697762] Fixed MDIO Bus: probed
[    0.697778] PPP generic driver version 2.4.2
[    0.697816] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.697824]   alloc irq_desc for 18 on node -1
[    0.697825]   alloc kstat_irqs on node -1
[    0.697827] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.697832] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.697834] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.697847] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.701739] ehci_hcd 0000:00:1a.7: debug port 1
[    0.701742] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.701749] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbfffc00
[    0.716003] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.716036] usb usb1: configuration #1 chosen from 1 choice
[    0.716050] hub 1-0:1.0: USB hub found
[    0.716053] hub 1-0:1.0: 6 ports detected
[    0.716082]   alloc irq_desc for 23 on node -1
[    0.716083]   alloc kstat_irqs on node -1
[    0.716085] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.716090] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.716092] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.716105] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.719979] ehci_hcd 0000:00:1d.7: debug port 1
[    0.719982] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.720005] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbfff800
[    0.732004] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.732038] usb usb2: configuration #1 chosen from 1 choice
[    0.732049] hub 2-0:1.0: USB hub found
[    0.732054] hub 2-0:1.0: 6 ports detected
[    0.732082] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732089] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732098] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.732101] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.732102] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.732119] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.732135] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    0.732169] usb usb3: configuration #1 chosen from 1 choice
[    0.732181] hub 3-0:1.0: USB hub found
[    0.732184] hub 3-0:1.0: 2 ports detected
[    0.732205]   alloc irq_desc for 21 on node -1
[    0.732206]   alloc kstat_irqs on node -1
[    0.732208] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.732211] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.732213] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.732227] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.732248] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    0.732283] usb usb4: configuration #1 chosen from 1 choice
[    0.732295] hub 4-0:1.0: USB hub found
[    0.732297] hub 4-0:1.0: 2 ports detected
[    0.732319] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.732323] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.732324] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.732336] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.732352] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    0.732387] usb usb5: configuration #1 chosen from 1 choice
[    0.732398] hub 5-0:1.0: USB hub found
[    0.732401] hub 5-0:1.0: 2 ports detected
[    0.732423] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.732427] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.732428] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.732441] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.732457] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    0.732491] usb usb6: configuration #1 chosen from 1 choice
[    0.732503] hub 6-0:1.0: USB hub found
[    0.732505] hub 6-0:1.0: 2 ports detected
[    0.732529] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.732532] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.732534] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.732549] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.732565] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    0.732600] usb usb7: configuration #1 chosen from 1 choice
[    0.732614] hub 7-0:1.0: USB hub found
[    0.732617] hub 7-0:1.0: 2 ports detected
[    0.732637] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.732640] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.732642] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.732655] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.732670] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    0.732705] usb usb8: configuration #1 chosen from 1 choice
[    0.732717] hub 8-0:1.0: USB hub found
[    0.732720] hub 8-0:1.0: 2 ports detected
[    0.732767] PNP: No PS/2 controller found. Probing ports directly.
[    0.735349] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.735351] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.735377] mice: PS/2 mouse device common for all mice
[    0.735424] rtc_cmos 00:03: RTC can wake from S4
[    0.735438] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.735455] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.735500] device-mapper: uevent: version 1.0.3
[    0.735544] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.735574] device-mapper: multipath: version 1.1.0 loaded
[    0.735576] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.735623] EISA: Probing bus 0 at eisa.0
[    0.735639] Cannot allocate resource for EISA slot 8
[    0.735640] EISA: Detected 0 cards.
[    0.735670] cpuidle: using governor ladder
[    0.735671] cpuidle: using governor menu
[    0.735896] TCP cubic registered
[    0.735967] NET: Registered protocol family 10
[    0.736179] lo: Disabled Privacy Extensions
[    0.736334] NET: Registered protocol family 17
[    0.736342] Bluetooth: L2CAP ver 2.13
[    0.736343] Bluetooth: L2CAP socket layer initialized
[    0.736344] Bluetooth: SCO (Voice Link) ver 0.6
[    0.736345] Bluetooth: SCO socket layer initialized
[    0.736359] Bluetooth: RFCOMM TTY layer initialized
[    0.736360] Bluetooth: RFCOMM socket layer initialized
[    0.736361] Bluetooth: RFCOMM ver 1.11
[    0.736377] Using IPI No-Shortcut mode
[    0.736402] PM: Resume from disk failed.
[    0.736407] registered taskstats version 1
[    0.736468]   Magic number: 10:4:693
[    0.736503] rtc_cmos 00:03: setting system clock to 2010-05-01 17:40:42 UTC (1272735642)
[    0.736504] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.736505] EDD information not available.
[    0.869892] ata5.00: ATA-7: Maxtor 6B200P0, BAH41BY0, max UDMA/133
[    0.869893] ata5.00: 398297088 sectors, multi 0: LBA48 
[    0.885878] ata5.00: configured for UDMA/100
[    1.026452] ata3: SATA link down (SStatus 0 SControl 300)
[    1.180030] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.188155] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB02, max UDMA/100
[    1.204166] ata4.00: configured for UDMA/100
[    1.384003] usb 8-1: new full speed USB device using uhci_hcd and address 2
[    1.492043] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.492051] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.492199] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.492206] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.500301] ata2.00: ATA-8: WDC WD5000AAKS-65YGA0, 12.01C02, max UDMA/133
[    1.500302] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.500612] ata1.00: ATA-7: Hitachi HDS721616PLA380, P22OA70A, max UDMA/133
[    1.500613] ata1.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.516287] ata2.00: configured for UDMA/133
[    1.516475] ata1.00: configured for UDMA/133
[    1.516530] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[    1.516582] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.516599] sd 0:0:0:0: [sda] 321672960 512-byte logical blocks: (164 GB/153 GiB)
[    1.516619] sd 0:0:0:0: [sda] Write Protect is off
[    1.516621] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.516632] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.516687]  sda:
[    1.516784] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[    1.516829] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.516843] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.516862] sd 1:0:0:0: [sdb] Write Protect is off
[    1.516864] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.516874] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.516923]  sdb:
[    1.517525] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB02 PQ: 0 ANSI: 5
[    1.522103] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.522105] Uniform CD-ROM driver Revision: 3.20
[    1.522137] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.522154] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.522190] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 6B200P0   BAH4 PQ: 0 ANSI: 5
[    1.522235] sd 4:0:0:0: [sdc] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[    1.522238] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    1.522256] sd 4:0:0:0: [sdc] Write Protect is off
[    1.522257] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.522267] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.522317]  sdc: sda1 sda2 sda3 sda4 < sdb2 < sdc2 < sdb5 >
[    1.542249] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.542604]  sda5
[    1.545732] usb 8-1: configuration #1 chosen from 1 choice
[    1.545914]  sdc5
[    1.548724] hub 8-1:1.0: USB hub found
[    1.550313]  sda6
[    1.550713] hub 8-1:1.0: 4 ports detected
[    1.556246]  sda7 sdc6 >
[    1.561543] sd 4:0:0:0: [sdc] Attached SCSI disk
[    1.565890]  sda8 >
[    1.566046] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.686973] Freeing unused kernel memory: 540k freed
[    1.687113] Write protecting the kernel text: 4580k
[    1.687133] Write protecting the kernel read-only data: 1840k
[    1.729864] sky2 driver version 1.23
[    1.729889] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.729898] sky2 0000:02:00.0: setting latency timer to 64
[    1.729913] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
[    1.729981]   alloc irq_desc for 28 on node -1
[    1.729982]   alloc kstat_irqs on node -1
[    1.729991] sky2 0000:02:00.0: irq 28 for MSI/MSI-X
[    1.729991] xor: automatically using best checksumming function: pIII_sse
[    1.730332] sky2 eth0: addr 00:22:15:17:10:18
[    1.748499]    pIII_sse  : 15605.000 MB/sec
[    1.748501] xor: using function: pIII_sse (15605.000 MB/sec)
[    1.753679] device-mapper: dm-raid45: initialized v0.2594b
[    1.755439] skge 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.755467] skge 1.13 addr 0xfebfc000 irq 18 chip Yukon-Lite rev 9
[    1.755813] skge eth1: addr 00:22:15:17:27:dc
[    1.761893] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.796507] usb 8-2: new low speed USB device using uhci_hcd and address 3
[    1.818018] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febfb000-febfb7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.982760] usb 8-2: configuration #1 chosen from 1 choice
[    1.988089] usbcore: registered new interface driver hiddev
[    2.002833] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input3
[    2.002865] generic-usb 0003:045E:0047.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2/input0
[    2.002871] usbcore: registered new interface driver usbhid
[    2.002872] usbhid: v2.6:USB HID core driver
[    2.061728] usb 8-1.4: new full speed USB device using uhci_hcd and address 4
[    2.199757] usb 8-1.4: configuration #1 chosen from 1 choice
[    2.205832] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.4/8-1.4:1.0/input/input4
[    2.205855] generic-usb 0003:1532:0102.0002: input,hidraw1: USB HID v1.00 Keyboard [Razer Razer Tarantula Keyboard] on usb-0000:00:1d.2-1.4/input0
[    2.209768] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.4/8-1.4:1.1/input/input5
[    2.209790] generic-usb 0003:1532:0102.0003: input,hidraw2: USB HID v1.00 Device [Razer Razer Tarantula Keyboard] on usb-0000:00:1d.2-1.4/input1
[    3.104045] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00014cbbc9]
[    3.149814] EXT4-fs (sda7): barriers enabled
[    3.160513] kjournald2 starting: pid 355, dev sda7:8, commit interval 5 seconds
[    3.160536] EXT4-fs (sda7): delayed allocation enabled
[    3.160537] EXT4-fs: file extents enabled
[    3.161477] EXT4-fs: mballoc enabled
[    3.161483] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   18.693057] udev: starting version 151
[   18.709176] Adding 995988k swap on /dev/sda6.  Priority:-1 extents:1 across:995988k 
[   18.713224] Linux agpgart interface v0.103
[   18.732685] lp: driver loaded but no devices found
[   18.736319] nvidia: module license 'NVIDIA' taints kernel.
[   18.736322] Disabling lock debugging due to kernel taint
[   18.806517] udev: renamed network interface eth1 to eth0
[   18.825239] udev: renamed network interface eth0_rename to eth1
[   18.852554] CA0106 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.852565] snd-ca0106: Model 1013 Rev 00000000 Serial 10131102
[   18.862589] type=1505 audit(1272728460.623:2): operation="profile_load" pid=3168 name=/sbin/dhclient3
[   18.862920] type=1505 audit(1272728460.623:3): operation="profile_load" pid=3168 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.863089] type=1505 audit(1272728460.623:4): operation="profile_load" pid=3168 name=/usr/lib/connman/scripts/dhclient-script
[   19.022030]   alloc irq_desc for 22 on node -1
[   19.022031]   alloc kstat_irqs on node -1
[   19.022035] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.022053] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.023642] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.023645] nvidia 0000:01:00.0: setting latency timer to 64
[   19.023704] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   19.036020] usbcore: deregistering interface driver usbhid
[   19.116576] usbcore: deregistering interface driver hiddev
[   19.119958] usbcore: registered new interface driver hiddev
[   19.134292] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input6
[   19.134329] generic-usb 0003:045E:0047.0004: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2/input0
[   19.137288] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.4/8-1.4:1.0/input/input7
[   19.137313] generic-usb 0003:1532:0102.0005: input,hidraw1: USB HID v1.00 Keyboard [Razer Razer Tarantula Keyboard] on usb-0000:00:1d.2-1.4/input0
[   19.141221] input: Razer Razer Tarantula Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.4/8-1.4:1.1/input/input8
[   19.141246] generic-usb 0003:1532:0102.0006: input,hidraw2: USB HID v1.00 Device [Razer Razer Tarantula Keyboard] on usb-0000:00:1d.2-1.4/input1
[   19.141253] usbcore: registered new interface driver usbhid
[   19.141254] usbhid: v2.6:USB HID core driver
[   19.161647] EXT4-fs (sda7): internal journal on sda7:8
[   19.439359] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   19.615375] type=1505 audit(1272728461.375:5): operation="profile_load" pid=3422 name=/usr/share/gdm/guest-session/Xsession
[   19.616317] type=1505 audit(1272728461.379:6): operation="profile_replace" pid=3423 name=/sbin/dhclient3
[   19.616669] type=1505 audit(1272728461.379:7): operation="profile_replace" pid=3423 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.616870] type=1505 audit(1272728461.379:8): operation="profile_replace" pid=3423 name=/usr/lib/connman/scripts/dhclient-script
[   19.618570] type=1505 audit(1272728461.379:9): operation="profile_load" pid=3424 name=/usr/bin/evince
[   19.622638] type=1505 audit(1272728461.383:10): operation="profile_load" pid=3424 name=/usr/bin/evince-previewer
[   19.625153] type=1505 audit(1272728461.387:11): operation="profile_load" pid=3424 name=/usr/bin/evince-thumbnailer
[   19.641649] sky2 eth1: enabling interface
[   19.641765] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.642698] skge eth0: enabling interface
[   19.645762] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by P4man on 2010-05-01
> **dioxip said:**
> Thats the exact message, I took a picture of it.


Clever :). But worrisome and puzzling as that number corresponds to a part of the uuid of your root partition. 

Anyway, shouldnt have asked dmesg, but 

```
cat /var/log/syslog
```

i suppose.

---

### Post by dioxip on 2010-05-01
> **P4man said:**
> Clever :). But worrisome and puzzling as that number corresponds to a part of the uuid of your root partition. 

Anyway, shouldnt have asked dmesg, but 

```
cat /var/log/syslog
```

i suppose.

Well, its just as long as the other one :P
But here you go

```
Apr 30 12:30:35 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="971" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 30 12:31:57 klim-desktop anacron[1921]: Job `cron.daily' terminated
Apr 30 12:31:57 klim-desktop anacron[1921]: Job `cron.weekly' started
Apr 30 12:31:57 klim-desktop anacron[3898]: Updated timestamp for job `cron.weekly' to 2010-04-30
Apr 30 12:32:30 klim-desktop anacron[1921]: Job `cron.weekly' terminated
Apr 30 12:32:30 klim-desktop anacron[1921]: Normal exit (2 jobs run)
Apr 30 12:32:49 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:33:20 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:34:48 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:37:28 klim-desktop udevd[12595]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10
Apr 30 12:37:55 klim-desktop udevd[12595]: last message repeated 2 times
Apr 30 12:37:55 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:39:05 klim-desktop dbus-daemon: last message repeated 2 times
Apr 30 12:41:48 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:42:46 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:42:54 klim-desktop udevd[12595]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10
Apr 30 12:44:05 klim-desktop udevd[12595]: last message repeated 13 times
Apr 30 12:44:19 klim-desktop acpid: exiting
Apr 30 12:48:45 klim-desktop anacron[12761]: Anacron 2.3 started on 2010-04-30
Apr 30 12:48:45 klim-desktop anacron[12761]: Normal exit (0 jobs run)
Apr 30 12:48:45 klim-desktop kernel: [ 3057.143938] CPU0 attaching NULL sched-domain.
Apr 30 12:48:45 klim-desktop kernel: [ 3057.143941] CPU1 attaching NULL sched-domain.
Apr 30 12:48:45 klim-desktop kernel: [ 3057.156527] CPU0 attaching sched-domain:
Apr 30 12:48:45 klim-desktop kernel: [ 3057.156529]  domain 0: span 0-1 level MC
Apr 30 12:48:45 klim-desktop kernel: [ 3057.156530]   groups: 0 1
Apr 30 12:48:45 klim-desktop kernel: [ 3057.156532] CPU1 attaching sched-domain:
Apr 30 12:48:45 klim-desktop kernel: [ 3057.156533]  domain 0: span 0-1 level MC
Apr 30 12:48:45 klim-desktop kernel: [ 3057.156534]   groups: 1 0
Apr 30 12:51:43 klim-desktop udevd[12595]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10
Apr 30 12:52:06 klim-desktop udevd[12595]: last message repeated 2 times
Apr 30 12:52:06 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:52:08 klim-desktop udevd[12595]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10
Apr 30 12:55:40 klim-desktop init: cron main process (23618) killed by TERM signal
Apr 30 12:57:50 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:58:01 klim-desktop avahi-daemon[981]: Files changed, reloading.
Apr 30 12:58:01 klim-desktop avahi-daemon[981]: No service file found in /etc/avahi/services.
Apr 30 12:58:02 klim-desktop avahi-daemon[981]: Got SIGTERM, quitting.
Apr 30 12:58:02 klim-desktop avahi-daemon[981]: Leaving mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
Apr 30 12:58:02 klim-desktop init: avahi-daemon main process (981) terminated with status 255
Apr 30 12:58:02 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 12:59:06 klim-desktop dbus-daemon: last message repeated 2 times
Apr 30 13:04:28 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:05:30 klim-desktop dbus-daemon: last message repeated 2 times
Apr 30 13:07:55 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:09:06 klim-desktop dbus-daemon: last message repeated 4 times
Apr 30 13:11:14 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:12:27 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:15:28 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:16:37 klim-desktop dbus-daemon: last message repeated 2 times
Apr 30 13:17:37 klim-desktop dbus-daemon: last message repeated 5 times
Apr 30 13:18:06 klim-desktop dbus-daemon: last message repeated 5 times
Apr 30 13:18:06 klim-desktop acpid: starting up with proc fs
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-media-eject.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/sony-volume-up.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/ac.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-www.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-stop.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-battery.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/sleepbtn.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/sony-sleep.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-hibernate.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/lenovo-touchpad.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-rotate.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-video.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/sony-volume-down.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-wireless-off.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/panasonic-lockbtn.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-wireless-on.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/ibm-wireless.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-next.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/battery.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-touchpad.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/sony-mute.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/videobtn.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-f8sv-touchpad.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-play.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/lenovo-undock.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-media.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-brightness-down.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-wireless.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/lidbtn.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-lock.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-mail.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/asus-brightness-up.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-ibutton.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/tosh-prev.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: ignoring conf file /etc/acpi/events/thinkpad-cmos.dpkg-new
Apr 30 13:18:06 klim-desktop acpid: 35 rules loaded
Apr 30 13:18:06 klim-desktop acpid: waiting for events: event logging is off
Apr 30 13:18:07 klim-desktop acpid: client connected from 1337[0:0]
Apr 30 13:18:07 klim-desktop acpid: 1 client rule loaded
Apr 30 13:18:08 klim-desktop polkitd[31692]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 30 13:18:09 klim-desktop acpid: client connected from 1337[0:0]
Apr 30 13:18:09 klim-desktop acpid: 1 client rule loaded
Apr 30 13:19:21 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:20:18 klim-desktop cron[20486]: (CRON) INFO (pidfile fd = 3)
Apr 30 13:20:18 klim-desktop cron[20487]: (CRON) STARTUP (fork ok)
Apr 30 13:20:18 klim-desktop cron[20487]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Apr 30 13:20:18 klim-desktop kernel: [ 4950.216770] type=1505 audit(1272626418.975:22): operation="profile_replace" pid=20500 name=/sbin/dhclient3
Apr 30 13:20:18 klim-desktop kernel: [ 4950.217114] type=1505 audit(1272626418.975:23): operation="profile_replace" pid=20500 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 30 13:20:18 klim-desktop kernel: [ 4950.217301] type=1505 audit(1272626418.975:24): operation="profile_replace" pid=20500 name=/usr/lib/connman/scripts/dhclient-script
Apr 30 13:20:22 klim-desktop kernel: Kernel logging (proc) stopped.
Apr 30 13:20:22 klim-desktop kernel: imklog: Cannot read proc file system, 1.
Apr 30 13:20:22 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="20648" x-info="http://www.rsyslog.com"] (re)start
Apr 30 13:20:22 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
Apr 30 13:20:22 klim-desktop rsyslogd: rsyslogd's userid changed to 101
Apr 30 13:20:22 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Apr 30 13:20:27 klim-desktop init: rsyslog-kmsg main process (967) killed by PIPE signal
Apr 30 13:20:27 klim-desktop init: rsyslog-kmsg main process ended, respawning
Apr 30 13:20:47 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Successfully dropped root privileges.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: avahi-daemon 0.6.25 starting up.
Apr 30 13:20:47 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Successfully called chroot().
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Successfully dropped remaining capabilities.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: No service file found in /etc/avahi/services.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Network interface enumeration completed.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Registering new address record for 62.107.77.166 on eth1.IPv4.
Apr 30 13:20:47 klim-desktop avahi-daemon[21266]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 13:20:48 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:20:48 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:20:48 klim-desktop avahi-daemon[21266]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 3764416712.
Apr 30 13:20:49 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:20:49 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:21:48 klim-desktop dbus-daemon: last message repeated 5 times
Apr 30 13:21:48 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Apr 30 13:22:32 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Apr 30 13:22:32 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Apr 30 13:22:32 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Apr 30 13:22:39 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:22:50 klim-desktop dbus-daemon: last message repeated 7 times
Apr 30 13:22:50 klim-desktop init: apport pre-start process (26845) terminated with status 1
Apr 30 13:22:50 klim-desktop init: apport post-stop process (26846) terminated with status 1
Apr 30 13:23:07 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:24:14 klim-desktop dbus-daemon: last message repeated 3 times
Apr 30 13:24:58 klim-desktop acpid: exiting
Apr 30 13:24:58 klim-desktop acpid: starting up with proc fs
Apr 30 13:24:58 klim-desktop acpid: 36 rules loaded
Apr 30 13:24:58 klim-desktop acpid: waiting for events: event logging is off
Apr 30 13:24:59 klim-desktop acpid: client connected from 1337[0:0]
Apr 30 13:24:59 klim-desktop acpid: 1 client rule loaded
Apr 30 13:25:01 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:25:03 klim-desktop acpid: client connected from 1337[0:0]
Apr 30 13:25:03 klim-desktop acpid: 1 client rule loaded
Apr 30 13:26:00 klim-desktop dbus-daemon: Reloaded configuration
Apr 30 13:27:22 klim-desktop dbus-daemon: last message repeated 4 times
Apr 30 13:32:02 klim-desktop init: tty4 main process (1172) killed by TERM signal
Apr 30 13:32:02 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="20648" x-info="http://www.rsyslog.com"] exiting on signal 15.
Apr 30 13:32:48 klim-desktop kernel: imklog: Cannot read proc file system, 1.
Apr 30 13:32:48 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3218" x-info="http://www.rsyslog.com"] (re)start
Apr 30 13:32:48 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
Apr 30 13:32:48 klim-desktop rsyslogd: rsyslogd's userid changed to 101
Apr 30 13:32:48 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Apr 30 13:32:49 klim-desktop udev-configure-printer: add /module/lp
Apr 30 13:32:49 klim-desktop udev-configure-printer: Failed to get parent
Apr 30 13:32:51 klim-desktop avahi-daemon[3400]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Apr 30 13:32:51 klim-desktop avahi-daemon[3400]: Successfully dropped root privileges.
Apr 30 13:32:51 klim-desktop avahi-daemon[3400]: avahi-daemon 0.6.25 starting up.
Apr 30 13:32:51 klim-desktop NetworkManager: <info>  starting...
Apr 30 13:32:51 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Nokia
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Ericsson MBM
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Option High-Speed
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Longcheer
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Generic
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin MotoC
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Huawei
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin AnyData
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Novatel
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Sierra
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Gobi
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin Option
Apr 30 13:32:52 klim-desktop modem-manager: Loaded plugin ZTE
Apr 30 13:32:52 klim-desktop avahi-daemon[3400]: Successfully called chroot().
Apr 30 13:32:52 klim-desktop avahi-daemon[3400]: Successfully dropped remaining capabilities.
Apr 30 13:32:52 klim-desktop avahi-daemon[3400]: No service file found in /etc/avahi/services.
Apr 30 13:32:52 klim-desktop avahi-daemon[3400]: Network interface enumeration completed.
Apr 30 13:32:52 klim-desktop avahi-daemon[3400]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 13:32:52 klim-desktop avahi-daemon[3400]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 3760904206.
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 30 13:32:52 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 30 13:32:52 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (144752464) ... get_connections.
Apr 30 13:32:52 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (144752464) ... get_connections (managed=false): return empty list.
Apr 30 13:32:52 klim-desktop gdm-binary[3394]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 30 13:32:52 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): now managed
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): preparing device.
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Apr 30 13:32:52 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): now managed
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): preparing device.
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 30 13:32:52 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  modem-manager is now available
Apr 30 13:32:52 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 30 13:32:52 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
Apr 30 13:32:53 klim-desktop gdm-binary[3394]: WARNING: Unable to find users: no seat-id found
Apr 30 13:32:53 klim-desktop gdm-simple-slave[3493]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  dhclient started with pid 3513
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 30 13:32:54 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 30 13:32:54 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 30 13:32:54 klim-desktop dhclient: All rights reserved.
Apr 30 13:32:54 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 30 13:32:54 klim-desktop dhclient: 
Apr 30 13:32:54 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
Apr 30 13:32:54 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
Apr 30 13:32:54 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
Apr 30 13:32:54 klim-desktop dhclient: Sending on   Socket/fallback
Apr 30 13:32:55 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 30 13:32:55 klim-desktop avahi-daemon[3400]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
Apr 30 13:32:55 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
Apr 30 13:32:55 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
Apr 30 13:32:55 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
Apr 30 13:32:55 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
Apr 30 13:32:55 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 30 13:32:55 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Apr 30 13:32:55 klim-desktop NetworkManager: <info>    address 62.107.77.166
Apr 30 13:32:55 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
Apr 30 13:32:55 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
Apr 30 13:32:55 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
Apr 30 13:32:55 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
Apr 30 13:32:55 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 30 13:32:55 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 30 13:32:55 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Apr 30 13:32:55 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 13564 seconds.
Apr 30 13:32:55 klim-desktop avahi-daemon[3400]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
Apr 30 13:32:55 klim-desktop avahi-daemon[3400]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 13:32:55 klim-desktop avahi-daemon[3400]: Registering new address record for 62.107.77.166 on eth1.IPv4.
Apr 30 13:32:56 klim-desktop cron[3552]: (CRON) INFO (pidfile fd = 3)
Apr 30 13:32:56 klim-desktop acpid: starting up with proc fs
Apr 30 13:32:56 klim-desktop anacron[3563]: Anacron 2.3 started on 2010-04-30
Apr 30 13:32:56 klim-desktop cron[3564]: (CRON) STARTUP (fork ok)
Apr 30 13:32:56 klim-desktop init: apport pre-start process (3547) terminated with status 1
Apr 30 13:32:56 klim-desktop init: apport post-stop process (3566) terminated with status 1
Apr 30 13:32:56 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Apr 30 13:32:56 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
Apr 30 13:32:56 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
Apr 30 13:32:56 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Apr 30 13:32:56 klim-desktop anacron[3563]: Normal exit (0 jobs run)
Apr 30 13:32:56 klim-desktop cron[3564]: (CRON) INFO (Running @reboot jobs)
Apr 30 13:32:56 klim-desktop acpid: 36 rules loaded
Apr 30 13:32:56 klim-desktop acpid: waiting for events: event logging is off
Apr 30 13:32:56 klim-desktop acpid: client connected from 3511[0:0]
Apr 30 13:32:56 klim-desktop acpid: 1 client rule loaded
Apr 30 13:32:56 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Apr 30 13:32:56 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Apr 30 13:32:56 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Apr 30 13:33:01 klim-desktop ntpdate[3704]: step time server 91.189.94.4 offset 2.539475 sec
Apr 30 13:33:01 klim-desktop anacron[3803]: Anacron 2.3 started on 2010-04-30
Apr 30 13:33:01 klim-desktop anacron[3803]: Normal exit (0 jobs run)
Apr 30 13:33:02 klim-desktop init: plymouth-stop pre-start process (3833) terminated with status 1
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Sucessfully called chroot.
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Sucessfully dropped privileges.
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Sucessfully limited resources.
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Canary thread running.
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Failed to make ourselves RT: Invalid argument
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Watchdog thread running.
Apr 30 13:33:03 klim-desktop rtkit-daemon[3858]: Running.
Apr 30 13:33:03 klim-desktop gdm-session-worker[3863]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 30 13:33:04 klim-desktop polkitd[3862]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 30 13:33:04 klim-desktop anacron[3916]: Anacron 2.3 started on 2010-04-30
Apr 30 13:33:04 klim-desktop anacron[3916]: Normal exit (0 jobs run)
Apr 30 13:33:04 klim-desktop rtkit-daemon[3858]: Failed to make ourselves RT: Invalid argument
Apr 30 13:33:05 klim-desktop rtkit-daemon[3858]: last message repeated 10 times
Apr 30 13:33:05 klim-desktop gdm-simple-greeter[3848]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Apr 30 13:33:06 klim-desktop acpid: client connected from 3976[107:114]
Apr 30 13:33:06 klim-desktop acpid: 1 client rule loaded
Apr 30 13:33:06 klim-desktop rtkit-daemon[3858]: Failed to make ourselves RT: Invalid argument
Apr 30 13:33:09 klim-desktop rtkit-daemon[3858]: last message repeated 7 times
Apr 30 13:33:09 klim-desktop gdm-session-worker[3863]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 30 13:33:14 klim-desktop rtkit-daemon[3858]: Failed to make ourselves RT: Invalid argument
Apr 30 13:33:20 klim-desktop rtkit-daemon[3858]: last message repeated 16 times
Apr 30 13:33:20 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Apr 30 13:33:21 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Apr 30 13:34:18 klim-desktop AptDaemon: INFO: Initializing daemon
Apr 30 13:39:19 klim-desktop AptDaemon: INFO: Quiting due to inactivity
Apr 30 13:39:19 klim-desktop AptDaemon: INFO: Shutdown was requested
Apr 30 13:39:52 klim-desktop pulseaudio[4071]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Apr 30 13:39:52 klim-desktop pulseaudio[4071]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ca0106'. Please report this issue to the ALSA developers.
Apr 30 13:39:52 klim-desktop pulseaudio[4071]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Apr 30 13:39:58 klim-desktop pulseaudio[4071]: ratelimit.c: 3 events suppressed
Apr 30 14:15:15 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Apr 30 14:15:15 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Apr 30 14:17:01 klim-desktop CRON[4965]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 15:17:02 klim-desktop CRON[5156]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 16:16:04 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Apr 30 16:16:04 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Apr 30 16:17:01 klim-desktop CRON[6019]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 16:35:48 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Apr 30 16:35:48 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Apr 30 17:17:01 klim-desktop CRON[8478]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 17:18:59 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 212.10.10.20 port 67
Apr 30 17:18:59 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 212.10.10.20
Apr 30 17:18:59 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 12474 seconds.
Apr 30 17:18:59 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed bound -> renew
Apr 30 17:18:59 klim-desktop NetworkManager: <info>    address 62.107.77.166
Apr 30 17:18:59 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
Apr 30 17:18:59 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
Apr 30 17:18:59 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
Apr 30 17:18:59 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
Apr 30 18:17:01 klim-desktop CRON[10477]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 18:53:55 klim-desktop ntfs-3g[12086]: Version 2010.3.6 external FUSE 28
Apr 30 18:53:55 klim-desktop ntfs-3g[12086]: Mounted /dev/sda8 (Read-Write, label "Spil", NTFS 3.1)
Apr 30 18:53:55 klim-desktop ntfs-3g[12086]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Apr 30 18:53:55 klim-desktop ntfs-3g[12086]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sda8,blkdev,blksize=4096,default_permissions
Apr 30 18:53:55 klim-desktop ntfs-3g[12086]: Global ownership and permissions enforced, configuration type 1
Apr 30 19:05:00 klim-desktop ntfs-3g[13539]: Version 2010.3.6 external FUSE 28
Apr 30 19:05:00 klim-desktop ntfs-3g[13539]: Mounted /dev/sda3 (Read-Write, label "", NTFS 3.1)
Apr 30 19:05:00 klim-desktop ntfs-3g[13539]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Apr 30 19:05:00 klim-desktop ntfs-3g[13539]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sda3,blkdev,blksize=4096,default_permissions
Apr 30 19:05:00 klim-desktop ntfs-3g[13539]: Global ownership and permissions enforced, configuration type 1
Apr 30 19:17:01 klim-desktop CRON[15263]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 20:17:01 klim-desktop CRON[15323]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 20:46:53 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 212.10.10.20 port 67
Apr 30 20:46:53 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 212.10.10.20
Apr 30 20:46:53 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 14041 seconds.
Apr 30 21:17:01 klim-desktop CRON[16471]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 21:29:27 klim-desktop pulseaudio[4071]: ratelimit.c: 1 events suppressed
Apr 30 21:38:28 klim-desktop pulseaudio[4071]: ratelimit.c: 1 events suppressed
Apr 30 22:17:02 klim-desktop CRON[16898]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 23:17:01 klim-desktop CRON[16989]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 00:17:01 klim-desktop CRON[17885]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 00:37:53 klim-desktop gnome-session[4009]: WARNING: Unable to load desktop file '/usr/bin/kglobalaccel.desktop': No such file or directory
May  1 00:37:53 klim-desktop gnome-session[4009]: WARNING: Unable to find desktop file 'kglobalaccel.desktop': Gyldig nøglefil blev ikke fundet i søgekatalogerne
May  1 00:37:53 klim-desktop gnome-session[4009]: WARNING: Unable to find desktop file 'gnome-/usr/bin/kglobalaccel.desktop': Gyldig nøglefil blev ikke fundet i søgekatalogerne
May  1 00:37:58 klim-desktop init: tty4 main process (3546) killed by TERM signal
May  1 00:37:58 klim-desktop init: tty5 main process (3549) killed by TERM signal
May  1 00:37:58 klim-desktop init: tty2 main process (3557) killed by TERM signal
May  1 00:37:58 klim-desktop init: tty3 main process (3558) killed by TERM signal
May  1 00:37:58 klim-desktop init: tty6 main process (3560) killed by TERM signal
May  1 00:37:58 klim-desktop init: cron main process (3564) killed by TERM signal
May  1 00:37:58 klim-desktop init: tty1 main process (3834) killed by TERM signal
May  1 00:37:58 klim-desktop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
May  1 00:37:59 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3218" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  1 11:12:29 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 11:12:29 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3428" x-info="http://www.rsyslog.com"] (re)start
May  1 11:12:29 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 11:12:29 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 11:12:29 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Successfully dropped root privileges.
May  1 11:12:29 klim-desktop avahi-daemon[3452]: avahi-daemon 0.6.25 starting up.
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Successfully called chroot().
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Successfully dropped remaining capabilities.
May  1 11:12:29 klim-desktop avahi-daemon[3452]: No service file found in /etc/avahi/services.
May  1 11:12:29 klim-desktop gdm-binary[3446]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:12:29 klim-desktop gdm-simple-slave[3549]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:12:29 klim-desktop gdm-binary[3446]: WARNING: Unable to find users: no seat-id found
May  1 11:12:29 klim-desktop NetworkManager: <info>  starting...
May  1 11:12:29 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 11:12:29 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 11:12:29 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 11:12:29 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Nokia
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Generic
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin MotoC
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Huawei
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin AnyData
May  1 11:12:29 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 11:12:29 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (164692208) ... get_connections.
May  1 11:12:29 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (164692208) ... get_connections (managed=false): return empty list.
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Novatel
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Sierra
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Gobi
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin Option
May  1 11:12:29 klim-desktop modem-manager: Loaded plugin ZTE
May  1 11:12:29 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 11:12:29 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 11:12:29 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 11:12:29 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Network interface enumeration completed.
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 11:12:29 klim-desktop avahi-daemon[3452]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 2418180588.
May  1 11:12:29 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 11:12:29 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 11:12:29 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 11:12:30 klim-desktop cron[3599]: (CRON) INFO (pidfile fd = 3)
May  1 11:12:30 klim-desktop init: apport pre-start process (3593) terminated with status 1
May  1 11:12:30 klim-desktop init: apport post-stop process (3611) terminated with status 1
May  1 11:12:30 klim-desktop acpid: starting up with proc fs
May  1 11:12:30 klim-desktop acpid: 36 rules loaded
May  1 11:12:30 klim-desktop acpid: waiting for events: event logging is off
May  1 11:12:30 klim-desktop anacron[3628]: Anacron 2.3 started on 2010-05-01
May  1 11:12:30 klim-desktop cron[3631]: (CRON) STARTUP (fork ok)
May  1 11:12:30 klim-desktop cron[3631]: (CRON) INFO (Running @reboot jobs)
May  1 11:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 11:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 11:12:30 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 11:12:31 klim-desktop anacron[3628]: Will run job `cron.daily' in 5 min.
May  1 11:12:31 klim-desktop anacron[3628]: Jobs will be executed sequentially
May  1 11:12:31 klim-desktop init: plymouth-stop pre-start process (3814) terminated with status 1
May  1 11:12:31 klim-desktop gdm-session-worker[3824]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Sucessfully called chroot.
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Sucessfully dropped privileges.
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Sucessfully limited resources.
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Canary thread running.
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Watchdog thread running.
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Running.
May  1 11:12:31 klim-desktop polkitd[3836]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 11:12:31 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 11:12:31 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 11:12:31 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 11:12:31 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 11:12:31 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 11:12:31 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 11:12:31 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 11:12:31 klim-desktop dhclient: All rights reserved.
May  1 11:12:31 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 11:12:31 klim-desktop dhclient: 
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:31 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 11:12:31 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 11:12:31 klim-desktop dhclient: Sending on   Socket/fallback
May  1 11:12:31 klim-desktop NetworkManager: <info>  dhclient started with pid 3839
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 11:12:31 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 11:12:31 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:31 klim-desktop rtkit-daemon[3830]: last message repeated 8 times
May  1 11:12:31 klim-desktop gdm-simple-greeter[3823]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 11:12:32 klim-desktop acpid: client connected from 3941[107:114]
May  1 11:12:32 klim-desktop acpid: 1 client rule loaded
May  1 11:12:32 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:32 klim-desktop rtkit-daemon[3830]: last message repeated 7 times
May  1 11:12:32 klim-desktop avahi-daemon[3452]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 11:12:34 klim-desktop gdm-session-worker[3824]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 11:12:35 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
May  1 11:12:35 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 11:12:35 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 11:12:35 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 11:12:35 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 14325 seconds.
May  1 11:12:35 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 11:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 11:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 11:12:35 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 11:12:35 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 11:12:35 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 11:12:35 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 11:12:35 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 11:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 11:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 11:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 11:12:35 klim-desktop avahi-daemon[3452]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 11:12:35 klim-desktop avahi-daemon[3452]: New relevant interface eth1.IPv4 for mDNS.
May  1 11:12:35 klim-desktop avahi-daemon[3452]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 11:12:36 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 11:12:36 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 11:12:36 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 11:12:36 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 11:12:38 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:38 klim-desktop rtkit-daemon[3830]: last message repeated 10 times
May  1 11:12:38 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 11:12:38 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 11:12:39 klim-desktop rtkit-daemon[3830]: Failed to make ourselves RT: Invalid argument
May  1 11:12:41 klim-desktop rtkit-daemon[3830]: last message repeated 5 times
May  1 11:12:41 klim-desktop ntpdate[4011]: no server suitable for synchronization found
May  1 11:13:41 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 11:17:01 klim-desktop CRON[4808]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 11:17:30 klim-desktop anacron[3628]: Job `cron.daily' started
May  1 11:17:30 klim-desktop anacron[4832]: Updated timestamp for job `cron.daily' to 2010-05-01
May  1 11:19:41 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 11:19:41 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 11:23:04 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 11:23:04 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3378" x-info="http://www.rsyslog.com"] (re)start
May  1 11:23:04 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 11:23:04 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Successfully dropped root privileges.
May  1 11:23:04 klim-desktop avahi-daemon[3399]: avahi-daemon 0.6.25 starting up.
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Successfully called chroot().
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Successfully dropped remaining capabilities.
May  1 11:23:04 klim-desktop gdm-binary[3396]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:23:04 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 11:23:04 klim-desktop avahi-daemon[3399]: No service file found in /etc/avahi/services.
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Network interface enumeration completed.
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 11:23:04 klim-desktop avahi-daemon[3399]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 4024916938.
May  1 11:23:04 klim-desktop NetworkManager: <info>  starting...
May  1 11:23:04 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 11:23:04 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 11:23:04 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 11:23:04 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 11:23:04 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 11:23:04 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (165347568) ... get_connections.
May  1 11:23:04 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (165347568) ... get_connections (managed=false): return empty list.
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Nokia
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Generic
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin MotoC
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Huawei
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin AnyData
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Novatel
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Sierra
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Gobi
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin Option
May  1 11:23:04 klim-desktop modem-manager: Loaded plugin ZTE
May  1 11:23:04 klim-desktop gdm-simple-slave[3496]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:23:04 klim-desktop gdm-binary[3396]: WARNING: Unable to find users: no seat-id found
May  1 11:23:04 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 11:23:04 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 11:23:04 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 11:23:04 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 11:23:04 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 11:23:04 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 11:23:04 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 11:23:05 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 11:23:05 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 11:23:05 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 11:23:05 klim-desktop cron[3596]: (CRON) INFO (pidfile fd = 3)
May  1 11:23:05 klim-desktop init: apport pre-start process (3553) terminated with status 1
May  1 11:23:05 klim-desktop acpid: starting up with proc fs
May  1 11:23:05 klim-desktop acpid: 36 rules loaded
May  1 11:23:05 klim-desktop acpid: waiting for events: event logging is off
May  1 11:23:05 klim-desktop init: apport post-stop process (3610) terminated with status 1
May  1 11:23:05 klim-desktop anacron[3622]: Anacron 2.3 started on 2010-05-01
May  1 11:23:05 klim-desktop cron[3624]: (CRON) STARTUP (fork ok)
May  1 11:23:05 klim-desktop cron[3624]: (CRON) INFO (Running @reboot jobs)
May  1 11:23:05 klim-desktop anacron[3622]: Normal exit (0 jobs run)
May  1 11:23:05 klim-desktop anacron[3720]: Anacron 2.3 started on 2010-05-01
May  1 11:23:05 klim-desktop anacron[3720]: Normal exit (0 jobs run)
May  1 11:23:06 klim-desktop init: plymouth-stop pre-start process (3759) terminated with status 1
May  1 11:23:06 klim-desktop gdm-session-worker[3777]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:23:06 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 11:23:06 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 11:23:06 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 11:23:06 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 11:23:06 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 11:23:06 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 11:23:06 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 11:23:06 klim-desktop dhclient: All rights reserved.
May  1 11:23:06 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 11:23:06 klim-desktop dhclient: 
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Sucessfully called chroot.
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Sucessfully dropped privileges.
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Sucessfully limited resources.
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Running.
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Failed to make ourselves RT: Invalid argument
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Watchdog thread running.
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Canary thread running.
May  1 11:23:06 klim-desktop NetworkManager: <info>  dhclient started with pid 3781
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 11:23:06 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 11:23:06 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 11:23:06 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 11:23:06 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 11:23:06 klim-desktop dhclient: Sending on   Socket/fallback
May  1 11:23:06 klim-desktop polkitd[3788]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: Failed to make ourselves RT: Invalid argument
May  1 11:23:06 klim-desktop rtkit-daemon[3783]: last message repeated 10 times
May  1 11:23:06 klim-desktop gdm-simple-greeter[3775]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 11:23:06 klim-desktop anacron[3852]: Anacron 2.3 started on 2010-05-01
May  1 11:23:06 klim-desktop anacron[3852]: Normal exit (0 jobs run)
May  1 11:23:07 klim-desktop acpid: client connected from 3895[107:114]
May  1 11:23:07 klim-desktop acpid: 1 client rule loaded
May  1 11:23:07 klim-desktop rtkit-daemon[3783]: Failed to make ourselves RT: Invalid argument
May  1 11:23:08 klim-desktop rtkit-daemon[3783]: last message repeated 7 times
May  1 11:23:08 klim-desktop avahi-daemon[3399]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 11:23:09 klim-desktop gdm-session-worker[3777]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 11:23:10 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
May  1 11:23:10 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 11:23:10 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 11:23:10 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 11:23:10 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 11:23:10 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 11:23:10 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 11:23:10 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 11:23:10 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 11:23:10 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 11:23:10 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 11:23:10 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 11:23:10 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 11:23:10 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 11:23:10 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 11:23:10 klim-desktop avahi-daemon[3399]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 11:23:10 klim-desktop avahi-daemon[3399]: New relevant interface eth1.IPv4 for mDNS.
May  1 11:23:10 klim-desktop avahi-daemon[3399]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 11:23:10 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 13186 seconds.
May  1 11:23:11 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 11:23:11 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 11:23:11 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 11:23:11 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 11:23:11 klim-desktop ntpdate[3990]: adjust time server 91.189.94.4 offset -0.446407 sec
May  1 11:23:12 klim-desktop rtkit-daemon[3783]: Failed to make ourselves RT: Invalid argument
May  1 11:23:12 klim-desktop rtkit-daemon[3783]: last message repeated 10 times
May  1 11:23:12 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 11:23:12 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 11:23:13 klim-desktop rtkit-daemon[3783]: Failed to make ourselves RT: Invalid argument
May  1 11:24:04 klim-desktop rtkit-daemon[3783]: last message repeated 5 times
May  1 11:24:15 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 11:27:56 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 11:27:56 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 11:29:15 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 11:29:15 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 11:37:57 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3378" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  1 11:38:45 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 11:38:45 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3307" x-info="http://www.rsyslog.com"] (re)start
May  1 11:38:45 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 11:38:45 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 11:38:45 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Successfully dropped root privileges.
May  1 11:38:45 klim-desktop avahi-daemon[3327]: avahi-daemon 0.6.25 starting up.
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Successfully called chroot().
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Successfully dropped remaining capabilities.
May  1 11:38:45 klim-desktop NetworkManager: <info>  starting...
May  1 11:38:45 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 11:38:45 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 11:38:45 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 11:38:45 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 11:38:45 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 11:38:45 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (163107056) ... get_connections.
May  1 11:38:45 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (163107056) ... get_connections (managed=false): return empty list.
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Nokia
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Generic
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin MotoC
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Huawei
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin AnyData
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Novatel
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Sierra
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Gobi
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin Option
May  1 11:38:45 klim-desktop modem-manager: Loaded plugin ZTE
May  1 11:38:45 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 11:38:45 klim-desktop avahi-daemon[3327]: No service file found in /etc/avahi/services.
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 11:38:45 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 11:38:45 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 11:38:45 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 11:38:45 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 11:38:45 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 11:38:45 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Network interface enumeration completed.
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 11:38:45 klim-desktop avahi-daemon[3327]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 3279859383.
May  1 11:38:45 klim-desktop gdm-binary[3373]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:38:45 klim-desktop gdm-binary[3373]: WARNING: Unable to find users: no seat-id found
May  1 11:38:45 klim-desktop gdm-simple-slave[3447]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:38:47 klim-desktop cron[3520]: (CRON) INFO (pidfile fd = 3)
May  1 11:38:47 klim-desktop init: apport pre-start process (3511) terminated with status 1
May  1 11:38:47 klim-desktop acpid: starting up with proc fs
May  1 11:38:47 klim-desktop acpid: 36 rules loaded
May  1 11:38:47 klim-desktop acpid: waiting for events: event logging is off
May  1 11:38:47 klim-desktop anacron[3546]: Anacron 2.3 started on 2010-05-01
May  1 11:38:47 klim-desktop init: apport post-stop process (3531) terminated with status 1
May  1 11:38:47 klim-desktop cron[3548]: (CRON) STARTUP (fork ok)
May  1 11:38:47 klim-desktop cron[3548]: (CRON) INFO (Running @reboot jobs)
May  1 11:38:47 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 11:38:47 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 11:38:47 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 11:38:47 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 11:38:47 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 11:38:47 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 11:38:47 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 11:38:47 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 11:38:47 klim-desktop NetworkManager: <info>  dhclient started with pid 3602
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 11:38:47 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 11:38:47 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 11:38:47 klim-desktop dhclient: All rights reserved.
May  1 11:38:47 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 11:38:47 klim-desktop dhclient: 
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 11:38:47 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 11:38:47 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 11:38:47 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 11:38:47 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 11:38:47 klim-desktop dhclient: Sending on   Socket/fallback
May  1 11:38:47 klim-desktop gdm-session-worker[3619]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:38:47 klim-desktop anacron[3546]: Normal exit (0 jobs run)
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Sucessfully called chroot.
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Sucessfully dropped privileges.
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Sucessfully limited resources.
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Running.
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Failed to make ourselves RT: Invalid argument
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Watchdog thread running.
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Canary thread running.
May  1 11:38:47 klim-desktop polkitd[3647]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: Failed to make ourselves RT: Invalid argument
May  1 11:38:47 klim-desktop rtkit-daemon[3640]: last message repeated 10 times
May  1 11:38:47 klim-desktop init: plymouth-stop pre-start process (3702) terminated with status 1
May  1 11:38:47 klim-desktop gdm-simple-greeter[3614]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 11:38:47 klim-desktop anacron[3762]: Anacron 2.3 started on 2010-05-01
May  1 11:38:47 klim-desktop anacron[3762]: Normal exit (0 jobs run)
May  1 11:38:48 klim-desktop acpid: client connected from 3805[107:114]
May  1 11:38:48 klim-desktop acpid: 1 client rule loaded
May  1 11:38:48 klim-desktop rtkit-daemon[3640]: Failed to make ourselves RT: Invalid argument
May  1 11:38:48 klim-desktop rtkit-daemon[3640]: last message repeated 7 times
May  1 11:38:48 klim-desktop avahi-daemon[3327]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 11:38:49 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
May  1 11:38:49 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 11:38:49 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 11:38:49 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 11:38:49 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 13163 seconds.
May  1 11:38:49 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 11:38:49 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 11:38:49 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 11:38:49 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 11:38:49 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 11:38:49 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 11:38:49 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 11:38:49 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 11:38:49 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 11:38:49 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 11:38:49 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 11:38:49 klim-desktop avahi-daemon[3327]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 11:38:49 klim-desktop avahi-daemon[3327]: New relevant interface eth1.IPv4 for mDNS.
May  1 11:38:49 klim-desktop avahi-daemon[3327]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 11:38:50 klim-desktop gdm-session-worker[3619]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 11:38:50 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 11:38:50 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 11:38:50 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 11:38:50 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 11:38:51 klim-desktop ntpdate[3875]: adjust time server 91.189.94.4 offset 0.239728 sec
May  1 11:38:53 klim-desktop rtkit-daemon[3640]: Failed to make ourselves RT: Invalid argument
May  1 11:38:53 klim-desktop rtkit-daemon[3640]: last message repeated 10 times
May  1 11:38:53 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 11:38:53 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 11:38:54 klim-desktop rtkit-daemon[3640]: Failed to make ourselves RT: Invalid argument
May  1 11:39:14 klim-desktop rtkit-daemon[3640]: last message repeated 5 times
May  1 11:39:14 klim-desktop pulseaudio[3972]: ratelimit.c: 2 events suppressed
May  1 11:39:56 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 11:44:57 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 11:44:57 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 11:50:42 klim-desktop init: tty1 main process (3703) killed by TERM signal
May  1 11:51:32 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 11:51:32 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3363" x-info="http://www.rsyslog.com"] (re)start
May  1 11:51:32 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 11:51:32 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 11:51:32 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 11:51:32 klim-desktop avahi-daemon[3377]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 11:51:32 klim-desktop avahi-daemon[3377]: Successfully dropped root privileges.
May  1 11:51:32 klim-desktop avahi-daemon[3377]: avahi-daemon 0.6.25 starting up.
May  1 11:51:32 klim-desktop avahi-daemon[3377]: Successfully called chroot().
May  1 11:51:32 klim-desktop avahi-daemon[3377]: Successfully dropped remaining capabilities.
May  1 11:51:32 klim-desktop gdm-binary[3371]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:51:33 klim-desktop NetworkManager: <info>  starting...
May  1 11:51:33 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 11:51:33 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 11:51:33 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 11:51:33 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Nokia
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Generic
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin MotoC
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Huawei
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin AnyData
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Novatel
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Sierra
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Gobi
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin Option
May  1 11:51:33 klim-desktop modem-manager: Loaded plugin ZTE
May  1 11:51:33 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 11:51:33 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (145281264) ... get_connections.
May  1 11:51:33 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (145281264) ... get_connections (managed=false): return empty list.
May  1 11:51:33 klim-desktop avahi-daemon[3377]: No service file found in /etc/avahi/services.
May  1 11:51:33 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 11:51:33 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 11:51:33 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 11:51:33 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 11:51:33 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 11:51:33 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 11:51:33 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 11:51:33 klim-desktop avahi-daemon[3377]: Network interface enumeration completed.
May  1 11:51:33 klim-desktop avahi-daemon[3377]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 11:51:33 klim-desktop avahi-daemon[3377]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 2459013154.
May  1 11:51:33 klim-desktop gdm-simple-slave[3473]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:51:33 klim-desktop gdm-binary[3371]: WARNING: Unable to find users: no seat-id found
May  1 11:51:34 klim-desktop init: apport pre-start process (3524) terminated with status 1
May  1 11:51:34 klim-desktop init: apport post-stop process (3535) terminated with status 1
May  1 11:51:34 klim-desktop cron[3528]: (CRON) INFO (pidfile fd = 3)
May  1 11:51:34 klim-desktop acpid: starting up with proc fs
May  1 11:51:34 klim-desktop acpid: 36 rules loaded
May  1 11:51:34 klim-desktop acpid: waiting for events: event logging is off
May  1 11:51:34 klim-desktop anacron[3540]: Anacron 2.3 started on 2010-05-01
May  1 11:51:34 klim-desktop cron[3542]: (CRON) STARTUP (fork ok)
May  1 11:51:34 klim-desktop cron[3542]: (CRON) INFO (Running @reboot jobs)
May  1 11:51:34 klim-desktop acpid: client connected from 3488[0:0]
May  1 11:51:34 klim-desktop acpid: 1 client rule loaded
May  1 11:51:34 klim-desktop anacron[3540]: Normal exit (0 jobs run)
May  1 11:51:34 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 11:51:34 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 11:51:34 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 11:51:34 klim-desktop anacron[3688]: Anacron 2.3 started on 2010-05-01
May  1 11:51:34 klim-desktop anacron[3688]: Normal exit (0 jobs run)
May  1 11:51:34 klim-desktop init: plymouth-stop pre-start process (3736) terminated with status 1
May  1 11:51:34 klim-desktop gdm-session-worker[3751]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Sucessfully called chroot.
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Sucessfully dropped privileges.
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Sucessfully limited resources.
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Running.
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Failed to make ourselves RT: Invalid argument
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Watchdog thread running.
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Canary thread running.
May  1 11:51:34 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 11:51:34 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 11:51:34 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 11:51:34 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 11:51:34 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 11:51:34 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 11:51:34 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 11:51:34 klim-desktop dhclient: All rights reserved.
May  1 11:51:34 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 11:51:34 klim-desktop dhclient: 
May  1 11:51:34 klim-desktop NetworkManager: <info>  dhclient started with pid 3764
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 11:51:34 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 11:51:34 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 11:51:34 klim-desktop polkitd[3763]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 11:51:34 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 11:51:34 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 11:51:34 klim-desktop dhclient: Sending on   Socket/fallback
May  1 11:51:34 klim-desktop rtkit-daemon[3759]: Failed to make ourselves RT: Invalid argument
May  1 11:51:35 klim-desktop rtkit-daemon[3759]: last message repeated 10 times
May  1 11:51:35 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
May  1 11:51:35 klim-desktop anacron[3822]: Anacron 2.3 started on 2010-05-01
May  1 11:51:35 klim-desktop anacron[3822]: Normal exit (0 jobs run)
May  1 11:51:35 klim-desktop gdm-simple-greeter[3750]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 11:51:35 klim-desktop acpid: client connected from 3879[107:114]
May  1 11:51:35 klim-desktop acpid: 1 client rule loaded
May  1 11:51:35 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 11:51:35 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 11:51:35 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 11:51:35 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 13196 seconds.
May  1 11:51:35 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 11:51:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 11:51:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 11:51:35 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 11:51:35 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 11:51:35 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 11:51:35 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 11:51:35 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 11:51:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 11:51:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 11:51:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 11:51:35 klim-desktop avahi-daemon[3377]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 11:51:35 klim-desktop avahi-daemon[3377]: New relevant interface eth1.IPv4 for mDNS.
May  1 11:51:35 klim-desktop avahi-daemon[3377]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 11:51:35 klim-desktop rtkit-daemon[3759]: Failed to make ourselves RT: Invalid argument
May  1 11:51:36 klim-desktop rtkit-daemon[3759]: last message repeated 7 times
May  1 11:51:36 klim-desktop avahi-daemon[3377]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 11:51:36 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 11:51:36 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 11:51:36 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 11:51:36 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 11:51:37 klim-desktop ntpdate[3939]: adjust time server 91.189.94.4 offset 0.377056 sec
May  1 11:51:37 klim-desktop gdm-session-worker[3751]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 11:51:40 klim-desktop rtkit-daemon[3759]: Failed to make ourselves RT: Invalid argument
May  1 11:51:40 klim-desktop rtkit-daemon[3759]: last message repeated 10 times
May  1 11:51:40 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 11:51:40 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 11:51:41 klim-desktop rtkit-daemon[3759]: Failed to make ourselves RT: Invalid argument
May  1 11:52:32 klim-desktop rtkit-daemon[3759]: last message repeated 5 times
May  1 11:52:43 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 11:57:44 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 11:57:44 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 12:08:35 klim-desktop pulseaudio[4041]: ratelimit.c: 10 events suppressed
May  1 12:17:01 klim-desktop CRON[10585]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 13:17:01 klim-desktop CRON[10728]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 14:02:43 klim-desktop pulseaudio[4041]: ratelimit.c: 2 events suppressed
May  1 14:17:01 klim-desktop CRON[11751]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 15:17:01 klim-desktop CRON[11830]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 15:31:31 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 212.10.10.20 port 67
May  1 15:31:31 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 212.10.10.20
May  1 15:31:31 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 12335 seconds.
May  1 15:31:31 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed bound -> renew
May  1 15:31:31 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 15:31:31 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 15:31:31 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 15:31:31 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 15:31:31 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 16:11:20 klim-desktop pulseaudio[4041]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
May  1 16:11:20 klim-desktop pulseaudio[4041]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ca0106'. Please report this issue to the ALSA developers.
May  1 16:11:20 klim-desktop pulseaudio[4041]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
May  1 16:17:01 klim-desktop CRON[12667]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 17:11:37 klim-desktop acpid: exiting
May  1 17:12:30 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 17:12:30 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3405" x-info="http://www.rsyslog.com"] (re)start
May  1 17:12:30 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 17:12:30 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 17:12:30 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Successfully dropped root privileges.
May  1 17:12:30 klim-desktop avahi-daemon[3427]: avahi-daemon 0.6.25 starting up.
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Successfully called chroot().
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Successfully dropped remaining capabilities.
May  1 17:12:30 klim-desktop gdm-binary[3421]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:12:30 klim-desktop gdm-simple-slave[3526]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:12:30 klim-desktop gdm-binary[3421]: WARNING: Unable to find users: no seat-id found
May  1 17:12:30 klim-desktop NetworkManager: <info>  starting...
May  1 17:12:30 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 17:12:30 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 17:12:30 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 17:12:30 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 17:12:30 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 17:12:30 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (167182576) ... get_connections.
May  1 17:12:30 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (167182576) ... get_connections (managed=false): return empty list.
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Nokia
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Generic
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin MotoC
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Huawei
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin AnyData
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Novatel
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Sierra
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Gobi
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin Option
May  1 17:12:30 klim-desktop modem-manager: Loaded plugin ZTE
May  1 17:12:30 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 17:12:30 klim-desktop avahi-daemon[3427]: No service file found in /etc/avahi/services.
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 17:12:30 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 17:12:30 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 17:12:30 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 17:12:30 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 17:12:30 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 17:12:30 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Network interface enumeration completed.
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 17:12:30 klim-desktop avahi-daemon[3427]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 2642414104.
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Sucessfully called chroot.
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Sucessfully dropped privileges.
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Sucessfully limited resources.
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Running.
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Failed to make ourselves RT: Invalid argument
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Watchdog thread running.
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Canary thread running.
May  1 17:12:31 klim-desktop gdm-session-worker[3578]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:12:31 klim-desktop polkitd[3586]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 17:12:31 klim-desktop rtkit-daemon[3582]: Failed to make ourselves RT: Invalid argument
May  1 17:12:32 klim-desktop rtkit-daemon[3582]: last message repeated 10 times
May  1 17:12:32 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 17:12:32 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 17:12:32 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 17:12:32 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 17:12:32 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 17:12:32 klim-desktop init: apport pre-start process (3621) terminated with status 1
May  1 17:12:32 klim-desktop cron[3627]: (CRON) INFO (pidfile fd = 3)
May  1 17:12:32 klim-desktop acpid: starting up with proc fs
May  1 17:12:32 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 17:12:32 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 17:12:32 klim-desktop dhclient: All rights reserved.
May  1 17:12:32 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 17:12:32 klim-desktop dhclient: 
May  1 17:12:32 klim-desktop acpid: 36 rules loaded
May  1 17:12:32 klim-desktop acpid: waiting for events: event logging is off
May  1 17:12:32 klim-desktop NetworkManager: <info>  dhclient started with pid 3640
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 17:12:32 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 17:12:32 klim-desktop init: apport post-stop process (3641) terminated with status 1
May  1 17:12:32 klim-desktop anacron[3658]: Anacron 2.3 started on 2010-05-01
May  1 17:12:32 klim-desktop cron[3661]: (CRON) STARTUP (fork ok)
May  1 17:12:32 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 17:12:32 klim-desktop cron[3661]: (CRON) INFO (Running @reboot jobs)
May  1 17:12:32 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 17:12:32 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 17:12:32 klim-desktop dhclient: Sending on   Socket/fallback
May  1 17:12:32 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 17:12:32 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 17:12:32 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 17:12:32 klim-desktop anacron[3658]: Normal exit (0 jobs run)
May  1 17:12:32 klim-desktop gdm-simple-greeter[3576]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 17:12:32 klim-desktop anacron[3776]: Anacron 2.3 started on 2010-05-01
May  1 17:12:32 klim-desktop anacron[3776]: Normal exit (0 jobs run)
May  1 17:12:32 klim-desktop init: plymouth-stop pre-start process (3879) terminated with status 1
May  1 17:12:32 klim-desktop acpid: client connected from 3892[107:114]
May  1 17:12:32 klim-desktop acpid: 1 client rule loaded
May  1 17:12:32 klim-desktop rtkit-daemon[3582]: Failed to make ourselves RT: Invalid argument
May  1 17:12:33 klim-desktop rtkit-daemon[3582]: last message repeated 7 times
May  1 17:12:33 klim-desktop avahi-daemon[3427]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 17:12:34 klim-desktop gdm-session-worker[3578]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 17:12:35 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
May  1 17:12:35 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 17:12:35 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 17:12:35 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 17:12:35 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 13025 seconds.
May  1 17:12:35 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 17:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 17:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 17:12:35 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 17:12:35 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 17:12:35 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 17:12:35 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 17:12:35 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 17:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 17:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 17:12:35 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 17:12:35 klim-desktop avahi-daemon[3427]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 17:12:35 klim-desktop avahi-daemon[3427]: New relevant interface eth1.IPv4 for mDNS.
May  1 17:12:35 klim-desktop avahi-daemon[3427]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 17:12:36 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 17:12:36 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 17:12:36 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 17:12:36 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 17:12:37 klim-desktop rtkit-daemon[3582]: Failed to make ourselves RT: Invalid argument
May  1 17:12:39 klim-desktop rtkit-daemon[3582]: last message repeated 10 times
May  1 17:12:39 klim-desktop ntpdate[4033]: step time server 91.189.94.4 offset 2.068006 sec
May  1 17:12:39 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 17:12:39 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 17:12:40 klim-desktop rtkit-daemon[3582]: Failed to make ourselves RT: Invalid argument
May  1 17:13:25 klim-desktop rtkit-daemon[3582]: last message repeated 5 times
May  1 17:13:25 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 17:13:25 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 17:13:41 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 17:17:01 klim-desktop CRON[4433]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 17:18:42 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 17:18:42 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 17:22:11 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 17:22:49 klim-desktop AptDaemon: INFO: InstallPackages() was called: dbus.Array([dbus.String(u'playonlinux')], signature=dbus.Signature('s'))
May  1 17:22:54 klim-desktop AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/1183ba8faab941f0984e8576067dce09
May  1 17:22:54 klim-desktop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/1183ba8faab941f0984e8576067dce09
May  1 17:23:51 klim-desktop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/1183ba8faab941f0984e8576067dce09
May  1 17:29:12 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 17:29:12 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 17:35:54 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3405" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  1 17:36:35 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 17:36:35 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3163" x-info="http://www.rsyslog.com"] (re)start
May  1 17:36:35 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 17:36:35 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 17:36:35 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 17:36:35 klim-desktop udev-configure-printer: add /module/lp
May  1 17:36:35 klim-desktop udev-configure-printer: Failed to get parent
May  1 17:36:36 klim-desktop avahi-daemon[3333]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 17:36:36 klim-desktop avahi-daemon[3333]: Successfully dropped root privileges.
May  1 17:36:36 klim-desktop avahi-daemon[3333]: avahi-daemon 0.6.25 starting up.
May  1 17:36:37 klim-desktop avahi-daemon[3333]: Successfully called chroot().
May  1 17:36:37 klim-desktop avahi-daemon[3333]: Successfully dropped remaining capabilities.
May  1 17:36:37 klim-desktop avahi-daemon[3333]: No service file found in /etc/avahi/services.
May  1 17:36:37 klim-desktop avahi-daemon[3333]: Network interface enumeration completed.
May  1 17:36:37 klim-desktop avahi-daemon[3333]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 17:36:37 klim-desktop avahi-daemon[3333]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 1711911344.
May  1 17:36:38 klim-desktop NetworkManager: <info>  starting...
May  1 17:36:38 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Nokia
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Generic
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin MotoC
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Huawei
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin AnyData
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Novatel
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Sierra
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Gobi
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin Option
May  1 17:36:38 klim-desktop modem-manager: Loaded plugin ZTE
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 17:36:38 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 17:36:38 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 17:36:38 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 17:36:38 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 17:36:38 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (138383600) ... get_connections.
May  1 17:36:38 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (138383600) ... get_connections (managed=false): return empty list.
May  1 17:36:39 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 17:36:39 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 17:36:39 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 17:36:39 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 17:36:39 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 17:36:39 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 17:36:39 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 17:36:39 klim-desktop gdm-binary[3355]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:36:40 klim-desktop gdm-binary[3355]: WARNING: Unable to find users: no seat-id found
May  1 17:36:40 klim-desktop gdm-simple-slave[3477]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:36:40 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 17:36:40 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 17:36:40 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 17:36:40 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 17:36:40 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 17:36:40 klim-desktop NetworkManager: <info>  dhclient started with pid 3487
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 17:36:40 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 17:36:40 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 17:36:40 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 17:36:40 klim-desktop dhclient: All rights reserved.
May  1 17:36:40 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 17:36:40 klim-desktop dhclient: 
May  1 17:36:41 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 17:36:41 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 17:36:41 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 17:36:41 klim-desktop dhclient: Sending on   Socket/fallback
May  1 17:36:41 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
May  1 17:36:41 klim-desktop cron[3508]: (CRON) INFO (pidfile fd = 3)
May  1 17:36:41 klim-desktop acpid: starting up with proc fs
May  1 17:36:41 klim-desktop cron[3521]: (CRON) STARTUP (fork ok)
May  1 17:36:41 klim-desktop anacron[3522]: Anacron 2.3 started on 2010-05-01
May  1 17:36:41 klim-desktop init: apport pre-start process (3504) terminated with status 1
May  1 17:36:41 klim-desktop init: apport post-stop process (3524) terminated with status 1
May  1 17:36:41 klim-desktop cron[3521]: (CRON) INFO (Running @reboot jobs)
May  1 17:36:41 klim-desktop anacron[3522]: Normal exit (0 jobs run)
May  1 17:36:41 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 17:36:41 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 17:36:41 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 17:36:41 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 14011 seconds.
May  1 17:36:41 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 17:36:41 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 17:36:41 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 17:36:41 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 17:36:41 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 17:36:41 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 17:36:41 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 17:36:41 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 17:36:41 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 17:36:41 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 17:36:41 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 17:36:41 klim-desktop avahi-daemon[3333]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 17:36:41 klim-desktop avahi-daemon[3333]: New relevant interface eth1.IPv4 for mDNS.
May  1 17:36:41 klim-desktop avahi-daemon[3333]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 17:36:41 klim-desktop acpid: 36 rules loaded
May  1 17:36:41 klim-desktop acpid: waiting for events: event logging is off
May  1 17:36:41 klim-desktop avahi-daemon[3333]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 17:36:42 klim-desktop acpid: client connected from 3531[0:0]
May  1 17:36:42 klim-desktop acpid: 1 client rule loaded
May  1 17:36:42 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 17:36:42 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 17:36:42 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 17:36:42 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 17:36:42 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 17:36:42 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 17:36:42 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 17:36:45 klim-desktop acpid: client connected from 3531[0:0]
May  1 17:36:45 klim-desktop acpid: 1 client rule loaded
May  1 17:36:46 klim-desktop ntpdate[3713]: step time server 91.189.94.4 offset 0.610241 sec
May  1 17:36:46 klim-desktop anacron[3756]: Anacron 2.3 started on 2010-05-01
May  1 17:36:46 klim-desktop anacron[3756]: Normal exit (0 jobs run)
May  1 17:36:46 klim-desktop init: plymouth-stop pre-start process (3793) terminated with status 1
May  1 17:36:49 klim-desktop gdm-session-worker[3831]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Sucessfully called chroot.
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Sucessfully dropped privileges.
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Sucessfully limited resources.
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Canary thread running.
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Failed to make ourselves RT: Invalid argument
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Watchdog thread running.
May  1 17:36:49 klim-desktop rtkit-daemon[3828]: Running.
May  1 17:36:49 klim-desktop polkitd[3835]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 17:36:50 klim-desktop rtkit-daemon[3828]: Failed to make ourselves RT: Invalid argument
May  1 17:36:50 klim-desktop rtkit-daemon[3828]: last message repeated 4 times
May  1 17:36:50 klim-desktop anacron[3889]: Anacron 2.3 started on 2010-05-01
May  1 17:36:50 klim-desktop anacron[3889]: Normal exit (0 jobs run)
May  1 17:36:50 klim-desktop rtkit-daemon[3828]: Failed to make ourselves RT: Invalid argument
May  1 17:36:51 klim-desktop rtkit-daemon[3828]: last message repeated 5 times
May  1 17:36:51 klim-desktop gdm-simple-greeter[3824]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 17:36:52 klim-desktop acpid: client connected from 3944[107:114]
May  1 17:36:52 klim-desktop acpid: 1 client rule loaded
May  1 17:36:52 klim-desktop rtkit-daemon[3828]: Failed to make ourselves RT: Invalid argument
May  1 17:36:53 klim-desktop rtkit-daemon[3828]: last message repeated 7 times
May  1 17:36:53 klim-desktop gdm-session-worker[3831]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 17:37:00 klim-desktop rtkit-daemon[3828]: Failed to make ourselves RT: Invalid argument
May  1 17:37:05 klim-desktop rtkit-daemon[3828]: last message repeated 16 times
May  1 17:37:05 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 17:37:07 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 17:38:04 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 17:41:01 klim-desktop kernel: imklog: Cannot read proc file system, 1.
May  1 17:41:01 klim-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3384" x-info="http://www.rsyslog.com"] (re)start
May  1 17:41:01 klim-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 17:41:01 klim-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 17:41:01 klim-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  1 17:41:01 klim-desktop NetworkManager: <info>  starting...
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Successfully dropped root privileges.
May  1 17:41:01 klim-desktop avahi-daemon[3407]: avahi-daemon 0.6.25 starting up.
May  1 17:41:01 klim-desktop NetworkManager: <info>  Trying to start the modem-manager...
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Nokia
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Ericsson MBM
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Option High-Speed
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Longcheer
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Generic
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: init!
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin MotoC
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Huawei
May  1 17:41:01 klim-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin AnyData
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Novatel
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Sierra
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Gobi
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1)
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin Option
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0)
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
May  1 17:41:01 klim-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  1 17:41:01 klim-desktop modem-manager: Loaded plugin ZTE
May  1 17:41:01 klim-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Successfully called chroot().
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Successfully dropped remaining capabilities.
May  1 17:41:01 klim-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May  1 17:41:01 klim-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (157241584) ... get_connections.
May  1 17:41:01 klim-desktop NetworkManager:    SCPlugin-Ifupdown: (157241584) ... get_connections (managed=false): return empty list.
May  1 17:41:01 klim-desktop avahi-daemon[3407]: No service file found in /etc/avahi/services.
May  1 17:41:01 klim-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): carrier is OFF
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'sky2')
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): now managed
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): bringing up device.
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): preparing device.
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  1 17:41:01 klim-desktop NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): carrier is OFF
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'skge')
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): now managed
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): bringing up device.
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): preparing device.
May  1 17:41:01 klim-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  1 17:41:01 klim-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:02.0/net/eth0
May  1 17:41:01 klim-desktop NetworkManager: <info>  modem-manager is now available
May  1 17:41:01 klim-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May  1 17:41:01 klim-desktop NetworkManager: <info>  Trying to start the supplicant...
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Network interface enumeration completed.
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Registering HINFO record with values 'I686'/'LINUX'.
May  1 17:41:01 klim-desktop avahi-daemon[3407]: Server startup complete. Host name is klim-desktop.local. Local service cookie is 1653972955.
May  1 17:41:01 klim-desktop gdm-binary[3451]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:41:01 klim-desktop gdm-simple-slave[3523]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:41:01 klim-desktop gdm-binary[3451]: WARNING: Unable to find users: no seat-id found
May  1 17:41:02 klim-desktop init: apport pre-start process (3561) terminated with status 1
May  1 17:41:02 klim-desktop init: apport post-stop process (3572) terminated with status 1
May  1 17:41:02 klim-desktop cron[3565]: (CRON) INFO (pidfile fd = 3)
May  1 17:41:02 klim-desktop acpid: starting up with proc fs
May  1 17:41:02 klim-desktop acpid: 36 rules loaded
May  1 17:41:02 klim-desktop acpid: waiting for events: event logging is off
May  1 17:41:02 klim-desktop cron[3579]: (CRON) STARTUP (fork ok)
May  1 17:41:02 klim-desktop cron[3579]: (CRON) INFO (Running @reboot jobs)
May  1 17:41:02 klim-desktop anacron[3577]: Anacron 2.3 started on 2010-05-01
May  1 17:41:02 klim-desktop anacron[3577]: Normal exit (0 jobs run)
May  1 17:41:02 klim-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  1 17:41:02 klim-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  1 17:41:02 klim-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  1 17:41:02 klim-desktop anacron[3766]: Anacron 2.3 started on 2010-05-01
May  1 17:41:02 klim-desktop anacron[3766]: Normal exit (0 jobs run)
May  1 17:41:03 klim-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May  1 17:41:03 klim-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May  1 17:41:03 klim-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  1 17:41:03 klim-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  1 17:41:03 klim-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May  1 17:41:03 klim-desktop init: plymouth-stop pre-start process (3793) terminated with status 1
May  1 17:41:03 klim-desktop NetworkManager: <info>  dhclient started with pid 3795
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May  1 17:41:03 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 17:41:03 klim-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May  1 17:41:03 klim-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May  1 17:41:03 klim-desktop dhclient: All rights reserved.
May  1 17:41:03 klim-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 17:41:03 klim-desktop dhclient: 
May  1 17:41:03 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May  1 17:41:03 klim-desktop dhclient: Listening on LPF/eth1/00:22:15:17:10:18
May  1 17:41:03 klim-desktop dhclient: Sending on   LPF/eth1/00:22:15:17:10:18
May  1 17:41:03 klim-desktop dhclient: Sending on   Socket/fallback
May  1 17:41:03 klim-desktop gdm-session-worker[3809]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Sucessfully called chroot.
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Sucessfully dropped privileges.
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Sucessfully limited resources.
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Running.
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Failed to make ourselves RT: Invalid argument
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Watchdog thread running.
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Canary thread running.
May  1 17:41:03 klim-desktop polkitd[3821]: started daemon version 0.96 using authority implementation `local' version `0.96'
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: Failed to make ourselves RT: Invalid argument
May  1 17:41:03 klim-desktop rtkit-daemon[3815]: last message repeated 10 times
May  1 17:41:03 klim-desktop anacron[3882]: Anacron 2.3 started on 2010-05-01
May  1 17:41:03 klim-desktop anacron[3882]: Normal exit (0 jobs run)
May  1 17:41:03 klim-desktop gdm-simple-greeter[3808]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  1 17:41:03 klim-desktop acpid: client connected from 3933[107:114]
May  1 17:41:03 klim-desktop acpid: 1 client rule loaded
May  1 17:41:04 klim-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
May  1 17:41:04 klim-desktop rtkit-daemon[3815]: Failed to make ourselves RT: Invalid argument
May  1 17:41:04 klim-desktop rtkit-daemon[3815]: last message repeated 7 times
May  1 17:41:04 klim-desktop dhclient: DHCPOFFER of 62.107.77.166 from 10.8.255.254
May  1 17:41:04 klim-desktop dhclient: DHCPREQUEST of 62.107.77.166 on eth1 to 255.255.255.255 port 67
May  1 17:41:04 klim-desktop dhclient: DHCPACK of 62.107.77.166 from 10.8.255.254
May  1 17:41:04 klim-desktop dhclient: bound to 62.107.77.166 -- renewal in 12192 seconds.
May  1 17:41:04 klim-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May  1 17:41:04 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 17:41:04 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
May  1 17:41:04 klim-desktop NetworkManager: <info>    address 62.107.77.166
May  1 17:41:04 klim-desktop NetworkManager: <info>    prefix 18 (255.255.192.0)
May  1 17:41:04 klim-desktop NetworkManager: <info>    gateway 62.107.127.254
May  1 17:41:04 klim-desktop NetworkManager: <info>    nameserver '212.10.10.4'
May  1 17:41:04 klim-desktop NetworkManager: <info>    nameserver '212.10.10.5'
May  1 17:41:04 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 17:41:04 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 17:41:04 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May  1 17:41:04 klim-desktop avahi-daemon[3407]: Joining mDNS multicast group on interface eth1.IPv4 with address 62.107.77.166.
May  1 17:41:04 klim-desktop avahi-daemon[3407]: New relevant interface eth1.IPv4 for mDNS.
May  1 17:41:04 klim-desktop avahi-daemon[3407]: Registering new address record for 62.107.77.166 on eth1.IPv4.
May  1 17:41:04 klim-desktop avahi-daemon[3407]: Registering new address record for fe80::222:15ff:fe17:1018 on eth1.*.
May  1 17:41:05 klim-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
May  1 17:41:05 klim-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May  1 17:41:05 klim-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
May  1 17:41:05 klim-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May  1 17:41:06 klim-desktop ntpdate[3994]: adjust time server 91.189.94.4 offset 0.311272 sec
May  1 17:41:07 klim-desktop gdm-session-worker[3809]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 17:41:13 klim-desktop rtkit-daemon[3815]: Failed to make ourselves RT: Invalid argument
May  1 17:41:13 klim-desktop rtkit-daemon[3815]: last message repeated 10 times
May  1 17:41:13 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 17:41:13 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 17:41:14 klim-desktop rtkit-daemon[3815]: Failed to make ourselves RT: Invalid argument
May  1 17:42:01 klim-desktop rtkit-daemon[3815]: last message repeated 5 times
May  1 17:42:16 klim-desktop AptDaemon: INFO: Initializing daemon
May  1 17:44:13 klim-desktop pulseaudio[4097]: ratelimit.c: 8 events suppressed
May  1 17:47:17 klim-desktop AptDaemon: INFO: Quiting due to inactivity
May  1 17:47:17 klim-desktop AptDaemon: INFO: Shutdown was requested
May  1 17:53:02 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 17:53:02 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 17:53:48 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 17:53:48 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 18:10:30 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 18:10:31 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 18:17:01 klim-desktop CRON[12053]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 18:24:31 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 18:24:31 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May  1 18:27:27 klim-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May  1 18:27:27 klim-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
```

---

### Post by P4man on 2010-05-01
I dont see the mount error in there either. I guess i gotta read up on log files lol. maybe you can search a bit yourself in system > adminstration > log file viewer, see if you can find a reference to that error. i cant see it in those 2.

BTW, you did try commenting out the cd/dvd line in fstab, right?

---

### Post by dioxip on 2010-05-01
> **P4man said:**
> I dont see the mount error in there either. I guess i gotta read up on log files lol. maybe you can search a bit yourself in system > adminstration > log file viewer, see if you can find a reference to that error. i cant see it in those 2.

BTW, you did try commenting out the cd/dvd line in fstab, right?

Yes I've tried to outcomment the cdrom/dvd drive aswell. 

Doesnt ubuntu use usplash for showing the bootsplash?

Cause when I searh for the usplash in the package manager it isnt installed, and when Im trying to install it, it just give me this error message [http://kl1m.dk/stuff/Screenshot.png]("http://kl1m.dk/stuff/Screenshot.png")

I've also looked every logfile in the logfileviewer for devicea7163311e2 nothing found..

---

### Post by P4man on 2010-05-01
10.04 doesnt use usplash, it uses plymouth

---

### Post by dioxip on 2010-05-01
> **P4man said:**
> 10.04 doesnt use usplash, it uses plymouth

Oh, well. I just think I will do a fresh install of ubuntu tomorrow, and see if that helps.

or just a thought. 

can I remove plymouth and use usplash instead?

---

### Post by P4man on 2010-05-01
AFAIK, no you cant.

---

### Post by dioxip on 2010-05-01
> **P4man said:**
> AFAIK, no you cant.

Damn, but thanks for the patience and help. :)
I would try reinstall ubuntu tomorrow, since it had been acting a little bit strange in other circumstances.

---

