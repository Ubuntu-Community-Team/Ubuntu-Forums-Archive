---
title: "Trouble Viewing a NTFS External Drive in UBuntu"
date: 2009-08-24
forum: General Help
---

### Post by avacomputers on 2009-08-24
I have some files on a NTFS MYBOOK, that I would like to view on my UBuntu laptop, it shows up under places, but I can't open it. Can someone offer some advice.

---

### Post by Rocket2DMn on 2009-08-24
Can you please tell us what the error is?  Feel free to take a screenshot if that is easier.

Also, can you please post the output of:
```
sudo fdisk -l
mount
cat /etc/fstab
```

Thanks.

---

### Post by avacomputers on 2009-08-24
The error is unable to mount drive.

THis is the results.> aalexander@aalexander-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7671d59c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS
aalexander@aalexander-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aalexander/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aalexander)
aalexander@aalexander-laptop:~$ cat /etc/fstab


---

### Post by Rocket2DMn on 2009-08-24
Did nothing spit out after the last command?
```
cat /etc/fstab
```
Can you also please post the output of
```
dmesg
```
That's a big one, you can attach the output as a file if you'd like:
```
dmesg > dmesg.txt
```
(and attach the dmesg.txt file in your home folder)

---

### Post by avacomputers on 2009-08-24
> **Rocket2DMn said:**
> Did nothing spit out after the last command?
```
cat /etc/fstab
```
Can you also please post the output of
```
dmesg
```
That's a big one, you can attach the output as a file if you'd like:
```
dmesg > dmesg.txt
```
(and attach the dmesg.txt file in your home folder)

cat /etc/fstab
> aalexander@aalexander-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5def422-2306-4745-aa8c-130779067370 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c7d314ce-397d-4b2a-94ce-e4a280c42c68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
aalexander@aalexander-laptop:~$ 


The text doc exceeds forum limit.

---

### Post by avacomputers on 2009-08-24
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Aug 18 16:25:45 UTC 2009 (Ubuntu 2.6.27-14.39-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000004f7d0000 - 000000004f7efc00 (reserved)
[    0.000000]  BIOS-e820: 000000004f7efc00 - 000000004f7fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004f7fb000 - 000000004f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x4f7d0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781c000 - 37feff0c
[    0.000000] ACPI: RSDP 000FE270, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 4F7EFC84, 0034 (r1 HP     099C     21110520 HP          1)
[    0.000000] ACPI: FACP 4F7EFC00, 0084 (r2 HP     099C            2 HP          1)
[    0.000000] ACPI: DSDT 4F7EFD50, 7D58 (r1 HP       DAU00     10000 MSFT  100000E)
[    0.000000] ACPI: FACS 4F7FAE80, 0040
[    0.000000] ACPI: APIC 4F7EFCB8, 005A (r1 HP     099C            1 HP          1)
[    0.000000] ACPI: MCFG 4F7EFD14, 003C (r1 HP     099C            1 HP          1)
[    0.000000] ACPI: SSDT 4F7F7AA8, 0371 (r1 HP       HPQPpc     1001 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 375MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
[    0.000000]   #4 [003781c000 - 0037feff0c]          RAMDISK ==> [003781c000 - 0037feff0c]
[    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0004f7d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004f7d0
[    0.000000] On node 0 totalpages: 325487
[    0.000000] free_area_init_node: node 0, pgdat c048d700, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 95362 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fec01000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 4f800000:90800000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322625
[    0.000000] Kernel command line: root=UUID=c5def422-2306-4745-aa8c-130779067370 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1728.993 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1275724k/1302336k available (2581k kernel code, 25252k reserved, 1163k data, 428k init, 384832k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
[    0.004000]       .data : 0xc038570a - 0xc04a8680   (1163 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038570a   (2581 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.98 BogoMIPS (lpj=6915972)
[    0.004043] Security Framework initialized
[    0.004057] SELinux:  Disabled at boot.
[    0.004088] AppArmor: AppArmor initialized
[    0.004099] Mount-cache hash table entries: 512
[    0.004333] Initializing cgroup subsys ns
[    0.004340] Initializing cgroup subsys cpuacct
[    0.004343] Initializing cgroup subsys memory
[    0.004366] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004369] CPU: L2 cache: 2048K
[    0.004387] Checking 'hlt' instruction... OK.
[    0.020573] SMP alternatives: switching to UP code
[    0.026734] Freeing SMP alternatives: 11k freed
[    0.026737] ACPI: Core revision 20080609
[    0.030269] ACPI: Checking initramfs for custom DSDT
[    0.424294] ENABLING IO-APIC IRQs
[    0.424492] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.467509] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.468029] Brought up 1 CPUs
[    0.468029] Total of 1 processors activated (3457.98 BogoMIPS).
[    0.468029] CPU0 attaching NULL sched-domain.
[    0.468029] net_namespace: 840 bytes
[    0.468029] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.468029] Booting paravirtualized kernel on bare hardware
[    0.468029] Time:  0:16:58  Date: 08/25/09
[    0.468029] NET: Registered protocol family 16
[    0.468029] EISA bus registered
[    0.468029] ACPI: bus type pci registered
[    0.468029] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.468029] PCI: MCFG area at e0000000 reserved in E820
[    0.468029] PCI: Using MMCONFIG for extended config space
[    0.468029] PCI: Using configuration type 1 for base access
[    0.468029] ACPI: EC: Look up EC in DSDT
[    0.492512] ACPI: Interpreter enabled
[    0.492519] ACPI: (supports S0 S3 S4 S5)
[    0.492536] ACPI: Using IOAPIC for interrupt routing
[    0.493696] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.519699] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.519703] ACPI: EC: driver started in interrupt mode
[    0.519778] ACPI: PCI Root Bridge [C002] (0000:00)
[    0.519884] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0400000, d047ffff]
[    0.519891] PCI: 0000:00:02.0 reg 14 io port: [7000, 7007]
[    0.519896] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff]
[    0.519901] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d0480000, d04bffff]
[    0.519935] PCI: 0000:00:02.1 reg 10 32bit mmio: [d0500000, d057ffff]
[    0.520047] PCI: 0000:00:1d.0 reg 20 io port: [2000, 201f]
[    0.520109] PCI: 0000:00:1d.1 reg 20 io port: [2020, 203f]
[    0.520171] PCI: 0000:00:1d.2 reg 20 io port: [2040, 205f]
[    0.520233] PCI: 0000:00:1d.3 reg 20 io port: [2060, 207f]
[    0.520297] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d0580000, d05803ff]
[    0.520367] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.520374] pci 0000:00:1d.7: PME# disabled
[    0.520468] PCI: 0000:00:1e.2 reg 10 io port: [2100, 21ff]
[    0.520476] PCI: 0000:00:1e.2 reg 14 io port: [2200, 223f]
[    0.520484] PCI: 0000:00:1e.2 reg 18 32bit mmio: [d0581000, d05811ff]
[    0.520492] PCI: 0000:00:1e.2 reg 1c 32bit mmio: [d0582000, d05820ff]
[    0.520537] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.520542] pci 0000:00:1e.2: PME# disabled
[    0.520575] PCI: 0000:00:1e.3 reg 10 io port: [2400, 24ff]
[    0.520583] PCI: 0000:00:1e.3 reg 14 io port: [2500, 257f]
[    0.520638] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.520643] pci 0000:00:1e.3: PME# disabled
[    0.520728] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.520735] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.520740] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
[    0.520766] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.520774] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.520782] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.520790] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.520797] PCI: 0000:00:1f.1 reg 20 io port: [2580, 258f]
[    0.520880] PCI: 0000:02:04.0 reg 10 32bit mmio: [d0000000, d0000fff]
[    0.520956] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.520962] pci 0000:02:04.0: PME# disabled
[    0.521005] PCI: 0000:02:06.0 reg 10 32bit mmio: [d0001000, d0001fff]
[    0.521039] pci 0000:02:06.0: supports D1
[    0.521041] pci 0000:02:06.0: supports D2
[    0.521043] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521049] pci 0000:02:06.0: PME# disabled
[    0.521091] PCI: 0000:02:06.2 reg 10 32bit mmio: [d0002000, d00027ff]
[    0.521101] PCI: 0000:02:06.2 reg 14 32bit mmio: [d0004000, d0007fff]
[    0.521172] pci 0000:02:06.2: supports D1
[    0.521174] pci 0000:02:06.2: supports D2
[    0.521177] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.521183] pci 0000:02:06.2: PME# disabled
[    0.521236] PCI: 0000:02:0e.0 reg 10 32bit mmio: [d000e000, d000ffff]
[    0.521301] pci 0000:02:0e.0: supports D1
[    0.521303] pci 0000:02:0e.0: supports D2
[    0.521305] pci 0000:02:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521310] pci 0000:02:0e.0: PME# disabled
[    0.521342] pci 0000:00:1e.0: transparent bridge
[    0.521350] PCI: bridge 0000:00:1e.0 32bit mmio: [d0000000, d03fffff]
[    0.521387] bus 00 -> node 0
[    0.521396] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.521867] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C068._PRT]
[    0.560770] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)
[    0.561068] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)
[    0.561366] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.561659] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)
[    0.561953] ACPI: PCI Interrupt Link [C0EE] (IRQs *10 11)
[    0.562244] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 *11)
[    0.562541] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.562828] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
[    0.563074] ACPI: Power Resource [C1C5] (on)
[    0.563229] ACPI: Power Resource [C244] (off)
[    0.563361] ACPI: Power Resource [C245] (off)
[    0.563493] ACPI: Power Resource [C246] (off)
[    0.563624] ACPI: Power Resource [C247] (off)
[    0.563705] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.563743] pnp: PnP ACPI init
[    0.563753] ACPI: bus type pnp registered
[    0.575421] pnp: PnP ACPI: found 11 devices
[    0.575424] ACPI: ACPI bus type pnp unregistered
[    0.575428] PnPBIOS: Disabled by ACPI PNP
[    0.575775] PCI: Using ACPI for IRQ routing
[    0.575898] NET: Registered protocol family 8
[    0.575898] NET: Registered protocol family 20
[    0.575898] NetLabel: Initializing
[    0.575898] NetLabel:  domain hash size = 128
[    0.575898] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.575898] NetLabel:  unlabeled traffic allowed by default
[    0.576131] hpet clockevent registered
[    0.576137] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.576143] hpet0: 3 64-bit timers, 14318180 Hz
[    0.577450] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.577453]    actual entries 65620
[    0.577549] AppArmor: AppArmor Filesystem Enabled
[    0.577572] ACPI: RTC can wake from S4
[    0.577579] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.577579] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.577579] system 00:00: iomem range 0x100000-0x4f7fffff could not be reserved
[    0.577579] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.577579] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.577579] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.577579] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.577579] system 00:09: ioport range 0x1000-0x107f has been reserved
[    0.577579] system 00:09: ioport range 0x1100-0x113f has been reserved
[    0.577579] system 00:09: ioport range 0x1200-0x121f has been reserved
[    0.577579] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.577579] system 00:09: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.577579] system 00:09: iomem range 0xfed20000-0xff41ffff could not be reserved
[    0.577579] system 00:09: iomem range 0xfed90000-0xfed9afff could not be reserved
[    0.577579] system 00:0a: iomem range 0xfeda0000-0xfedbffff could not be reserved
[    0.577579] system 00:0a: iomem range 0xfec01000-0xfec01fff could not be reserved
[    0.612769] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.612772] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.612778] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.612785] pci 0000:02:06.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.612793] pci 0000:02:06.0:   MEM window: 0x54000000-0x57ffffff
[    0.612799] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.612803] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.612810] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd03fffff
[    0.612815] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.612832] pci 0000:00:1e.0: setting latency timer to 64
[    0.612844] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.612851] bus: 00 index 0 io port: [0, ffff]
[    0.612854] bus: 00 index 1 mmio: [0, ffffffff]
[    0.612856] bus: 02 index 0 io port: [3000, 3fff]
[    0.612859] bus: 02 index 1 mmio: [d0000000, d03fffff]
[    0.612861] bus: 02 index 2 mmio: [50000000, 53ffffff]
[    0.612864] bus: 02 index 3 io port: [0, ffff]
[    0.612866] bus: 02 index 4 mmio: [0, ffffffff]
[    0.612869] bus: 03 index 0 io port: [3000, 30ff]
[    0.612871] bus: 03 index 1 io port: [3400, 34ff]
[    0.612873] bus: 03 index 2 mmio: [50000000, 53ffffff]
[    0.612876] bus: 03 index 3 mmio: [54000000, 57ffffff]
[    0.612885] NET: Registered protocol family 2
[    0.613011] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.613280] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.614075] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.614655] TCP: Hash tables configured (established 131072 bind 65536)
[    0.614659] TCP reno registered
[    0.614817] NET: Registered protocol family 1
[    0.614974] checking if image is initramfs... it is
[    1.080081] Switched to high resolution mode on CPU 0
[    1.412461] Freeing initrd memory: 8015k freed
[    1.413277] audit: initializing netlink socket (disabled)
[    1.413302] type=2000 audit(1251159418.412:1): initialized
[    1.419390] highmem bounce pool size: 64 pages
[    1.419398] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.421937] VFS: Disk quotas dquot_6.5.1
[    1.422034] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.422146] msgmni has been set to 1757
[    1.422288] io scheduler noop registered
[    1.422291] io scheduler anticipatory registered
[    1.422294] io scheduler deadline registered
[    1.422307] io scheduler cfq registered (default)
[    1.422326] pci 0000:00:02.0: Boot video device
[    1.422765] isapnp: Scanning for PnP cards...
[    1.776588] isapnp: No Plug & Play device found
[    1.814028] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.814724] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.814734] serial 0000:00:1e.3: PCI INT B disabled
[    1.816395] brd: module loaded
[    1.816475] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.816603] PNP: PS/2 Controller [PNP0303:C1C2,PNP0f13:C1C3] at 0x60,0x64 irq 1,12
[    1.818477] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.819221] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.819226] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.819229] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.819232] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.819235] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.819673] mice: PS/2 mouse device common for all mice
[    1.819822] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.819853] rtc0: alarms up to one month, y3k, hpet irqs
[    1.819974] EISA: Probing bus 0 at eisa.0
[    1.819982] Cannot allocate resource for EISA slot 1
[    1.819985] Cannot allocate resource for EISA slot 2
[    1.819987] Cannot allocate resource for EISA slot 3
[    1.820009] Cannot allocate resource for EISA slot 7
[    1.820015] EISA: Detected 0 cards.
[    1.820019] cpuidle: using governor ladder
[    1.820022] cpuidle: using governor menu
[    1.820593] TCP cubic registered
[    1.820627] Using IPI No-Shortcut mode
[    1.820827] registered taskstats version 1
[    1.820942]   Magic number: 5:606:254
[    1.820985] tty ttytd: hash matches
[    1.821087] pci 0000:00:1d.2: hash matches
[    1.821138] rtc_cmos 00:05: setting system clock to 2009-08-25 00:16:59 UTC (1251159419)
[    1.821142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.821144] EDD information not available.
[    1.821430] Freeing unused kernel memory: 428k freed
[    1.821487] Write protecting the kernel text: 2584k
[    1.821520] Write protecting the kernel read-only data: 940k
[    1.844375] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.080037] fuse init (API version 7.9)
[    2.284407] ACPI: Transitioning device [C248] to D3
[    2.292013] fan PNP0C0B:00: registered as cooling_device0
[    2.292020] ACPI: Fan [C248] (off)
[    2.292279] ACPI: Transitioning device [C249] to D3
[    2.300012] fan PNP0C0B:01: registered as cooling_device1
[    2.300024] ACPI: Fan [C249] (off)
[    2.300285] ACPI: Transitioning device [C24A] to D3
[    2.308013] fan PNP0C0B:02: registered as cooling_device2
[    2.308020] ACPI: Fan [C24A] (off)
[    2.308272] ACPI: Transitioning device [C24B] to D3
[    2.316012] fan PNP0C0B:03: registered as cooling_device3
[    2.316019] ACPI: Fan [C24B] (off)
[    2.350640] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.350691] processor ACPI0007:00: registered as cooling_device4
[    2.350696] ACPI: Processor [C000] (supports 8 throttling states)
[    2.366109] thermal LNXTHERM:01: registered as thermal_zone0
[    2.375198] Marking TSC unstable due to TSC halts in idle
[    2.380311] ACPI: Thermal Zone [TZ1] (70 C)
[    2.391117] thermal LNXTHERM:02: registered as thermal_zone1
[    2.399237] ACPI: Thermal Zone [TZ2] (55 C)
[    2.406274] thermal LNXTHERM:03: registered as thermal_zone2
[    2.418630] ACPI: Thermal Zone [TZ3] (31 C)
[    2.421460] thermal LNXTHERM:04: registered as thermal_zone3
[    2.427363] ACPI: Thermal Zone [TZ4] (59 C)
[    3.198660] usbcore: registered new interface driver usbfs
[    3.198690] usbcore: registered new interface driver hub
[    3.198731] usbcore: registered new device driver usb
[    3.208111] USB Universal Host Controller Interface driver v3.0
[    3.211355] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.211366] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.211370] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.211422] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.211461] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002000
[    3.211675] usb usb1: configuration #1 chosen from 1 choice
[    3.211707] hub 1-0:1.0: USB hub found
[    3.211715] hub 1-0:1.0: 2 ports detected
[    3.228086] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.328264] No dock devices found.
[    3.388462] SCSI subsystem initialized
[    3.416693] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.416706] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.416711] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.416738] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.416777] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[    3.416891] usb usb2: configuration #1 chosen from 1 choice
[    3.416922] hub 2-0:1.0: USB hub found
[    3.416931] hub 2-0:1.0: 2 ports detected
[    3.462108] libata version 3.00 loaded.
[    3.520380] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.520393] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.520397] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.520424] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.520463] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    3.520576] usb usb3: configuration #1 chosen from 1 choice
[    3.520606] hub 3-0:1.0: USB hub found
[    3.520613] hub 3-0:1.0: 2 ports detected
[    3.528023] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.624362] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.624374] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.624379] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.624404] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.624441] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00002060
[    3.624550] usb usb4: configuration #1 chosen from 1 choice
[    3.624581] hub 4-0:1.0: USB hub found
[    3.624588] hub 4-0:1.0: 2 ports detected
[    3.691636] usb 1-2: configuration #1 chosen from 1 choice
[    3.728273] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.728292] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.728297] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.728324] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.732242] ehci_hcd 0000:00:1d.7: debug port 1
[    3.732250] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.732259] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0580000
[    3.748037] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.748169] usb usb5: configuration #1 chosen from 1 choice
[    3.748200] hub 5-0:1.0: USB hub found
[    3.748208] hub 5-0:1.0: 8 ports detected
[    3.872123] usb 1-2: USB disconnect, address 2
[    3.960932] ohci1394 0000:02:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.010689] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.010748] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.010783] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.010799] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    4.015967] b44 0000:02:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.072082] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[    4.076013] Clocksource tsc unstable (delta = -113416845 ns)
[    4.076957] b44.c:v2.0
[    4.077055] ata_piix 0000:00:1f.1: version 2.12
[    4.077069] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.077110] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.084849] scsi0 : ata_piix
[    4.084960] scsi1 : ata_piix
[    4.085747] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14
[    4.085751] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15
[    4.096444] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:60:b7:8d:51
[    4.152079] usb 5-2: new high speed USB device using ehci_hcd and address 2
[    4.285654] usb 5-2: configuration #1 chosen from 1 choice
[    4.286730] usbcore: registered new interface driver libusual
[    4.300345] Initializing USB Mass Storage driver...
[    4.304995] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.306799] usbcore: registered new interface driver usb-storage
[    4.306804] USB Mass Storage support registered.
[    4.306892] usb-storage: device found at 2
[    4.306894] usb-storage: waiting for device to settle before scanning
[    4.312465] ata1.00: ATA-6: ST9408114A, 3.02, max UDMA/100
[    4.312469] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.312501] ata1.01: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max MWDMA2
[    4.328402] ata1.00: configured for UDMA/100
[    4.344412] ata1.01: configured for MWDMA2
[    4.344464] ata2: port disabled. ignoring.
[    4.344589] scsi 0:0:0:0: Direct-Access     ATA      ST9408114A       3.02 PQ: 0 ANSI: 5
[    4.344805] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.348790] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.02 PQ: 0 ANSI: 5
[    4.348890] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.374520] Driver 'sd' needs updating - please use bus_type methods
[    4.374635] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.374653] sd 0:0:0:0: [sda] Write Protect is off
[    4.374657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.376717] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.376792] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.376808] sd 0:0:0:0: [sda] Write Protect is off
[    4.376811] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.376838] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.376842]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.401648]  sda1 sda2 < sda5 >
[    4.435079] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.446207] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.446212] Uniform CD-ROM driver Revision: 3.20
[    4.446311] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.738738] PM: Starting manual resume from disk
[    4.738742] PM: Resume from partition 8:5
[    4.738745] PM: Checking hibernation image.
[    4.738930] PM: Resume from disk failed.
[    4.762694] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.762699] EXT3-fs: write access will be enabled during recovery.
[    9.304171] usb-storage: device scan complete
[    9.304653] scsi 2:0:0:0: Direct-Access     WD       3200AAV External 1.65 PQ: 0 ANSI: 4
[    9.312501] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    9.313242] sd 2:0:0:0: [sdb] Write Protect is off
[    9.313245] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    9.313249] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.313864] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    9.314614] sd 2:0:0:0: [sdb] Write Protect is off
[    9.314617] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    9.314619] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.314624]  sdb: sdb1
[   14.709948] sd 2:0:0:0: [sdb] Attached SCSI disk
[   14.710197] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.200578] kjournald starting.  Commit interval 5 seconds
[   17.200598] EXT3-fs: sda1: orphan cleanup on readonly fs
[   17.200606] ext3_orphan_cleanup: deleting unreferenced inode 1278096
[   17.236848] ext3_orphan_cleanup: deleting unreferenced inode 1482827
[   17.236864] EXT3-fs: sda1: 2 orphan inodes deleted
[   17.236866] EXT3-fs: recovery complete.
[   17.337820] EXT3-fs: mounted filesystem with ordered data mode.
[   25.015820] udevd version 124 started
[   26.111753] Linux agpgart interface v0.103
[   26.161790] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   26.162197] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   26.165393] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   26.441846] intel_rng: FWH not detected
[   26.481146] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   26.492624] ACPI: Power Button (FF) [PWRF]
[   26.492764] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   26.504020] ACPI: Sleep Button (CM) [C1E8]
[   26.504121] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   26.504249] ACPI: Lid Switch [C1E9]
[   26.624690] iTCO_vendor_support: vendor-support=0
[   26.640719] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   26.640836] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   26.640992] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.678631] ACPI: AC Adapter [C172] (on-line)
[   26.792874] ACPI: Battery Slot [C174] (battery present)
[   26.793194] ACPI: Battery Slot [C173] (battery absent)
[   26.836257] ACPI: WMI: Mapper loaded
[   27.336147] ieee80211_crypt: registered algorithm 'NULL'
[   27.408133] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   27.408137] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   27.608208] Yenta: CardBus bridge found at 0000:02:06.0 [103c:099c]
[   27.608233] Yenta: Enabling burst memory read transactions
[   27.608239] Yenta: Using INTVAL to route CSC interrupts to PCI
[   27.608241] Yenta: Routing CardBus interrupts to PCI
[   27.608248] Yenta TI: socket 0000:02:06.0, mfunc 0x01aa1b22, devctl 0x64
[   27.692191] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   27.692196] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   27.840808] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   27.840814] Socket status: 30000006
[   27.840818] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   27.840827] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   27.840830] cs: IO port probe 0x3000-0x3fff: clean.
[   27.841079] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   27.841082] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   27.896332] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   27.896399] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   27.896454] firmware: requesting ipw2200-bss.fw
[   28.640882] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
[   28.656017] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)
[   30.295581] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   30.615309] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[   30.615317] serio: Synaptics pass-through port at isa0060/serio4/input0
[   30.655735] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   31.490045] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   31.496062] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   31.496089] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   31.838369] cs: IO port probe 0x100-0x3af: clean.
[   31.840086] cs: IO port probe 0x3e0-0x4ff: clean.
[   31.840817] cs: IO port probe 0x820-0x8ff: clean.
[   31.841411] cs: IO port probe 0xc00-0xcf7: clean.
[   31.842168] cs: IO port probe 0xa00-0xaff: clean.
[   32.420028] intel8x0_measure_ac97_clock: measured 55399 usecs
[   32.420032] intel8x0: clocking to 48000
[   33.025246] lp: driver loaded but no devices found
[   33.292528] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   33.832014] EXT3 FS on sda1, internal journal
[   34.691029] type=1505 audit(1251159452.837:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4104
[   34.910719] type=1505 audit(1251159453.057:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4109
[   34.911042] type=1505 audit(1251159453.057:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4109
[   35.073696] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.573855] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   36.670168] apm: BIOS not found.
[   36.831536] ppdev: user-space parallel port driver
[   38.478688] Bluetooth: Core ver 2.13
[   38.480394] NET: Registered protocol family 31
[   38.480399] Bluetooth: HCI device and connection manager initialized
[   38.480404] Bluetooth: HCI socket layer initialized
[   38.517688] Bluetooth: L2CAP ver 2.11
[   38.517694] Bluetooth: L2CAP socket layer initialized
[   38.549592] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.549599] Bluetooth: BNEP filters: protocol multicast
[   38.639291] Bridge firewalling registered
[   38.668518] Bluetooth: RFCOMM socket layer initialized
[   38.672040] Bluetooth: RFCOMM TTY layer initialized
[   38.672045] Bluetooth: RFCOMM ver 1.10
[   38.674776] Bluetooth: SCO (Voice Link) ver 0.6
[   38.674782] Bluetooth: SCO socket layer initialized
[   42.599639] [drm] Initialized drm 1.1.0 20060810
[   42.605814] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.605825] pci 0000:00:02.0: setting latency timer to 64
[   42.606974] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   42.824088] NET: Registered protocol family 17
[   84.909716] ieee80211_crypt: registered algorithm 'WEP'
[   88.607334] NET: Registered protocol family 10
[   88.609646] lo: Disabled Privacy Extensions
[   88.611826] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   99.260026] eth1: no IPv6 routers present

---

### Post by Rocket2DMn on 2009-08-24
> **avacomputers said:**
> cat /etc/fstab


The text doc exceeds forum limit.

Heh, OK, can you just post the last 30 or 40 lines of the output of dmesg?  Run the command after you try to access the drive (i.e. unplug it and plug it back in, then try to open it).

---

### Post by avacomputers on 2009-08-24
> **Rocket2DMn said:**
> Heh, OK, can you just post the last 30 or 40 lines of the output of dmesg?  Run the command after you try to access the drive (i.e. unplug it and plug it back in, then try to open it).

I unplugged in and tried again. Same thing. Unable to Mount My Book.

---

### Post by Rocket2DMn on 2009-08-24
I figured as much, can you please post the last 40 or so lines of dmesg for me?  The graphical error you're getting isn't very helpful, so hopefully there is something from the dmesg log that will help us.

---

### Post by avacomputers on 2009-08-24
> **Rocket2DMn said:**
> I figured as much, can you please post the last 40 or so lines of dmesg for me?  The graphical error you're getting isn't very helpful, so hopefully there is something from the dmesg log that will help us.

This is the entire log.

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Aug 18 16:25:45 UTC 2009 (Ubuntu 2.6.27-14.39-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000004f7d0000 - 000000004f7efc00 (reserved)
[    0.000000]  BIOS-e820: 000000004f7efc00 - 000000004f7fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004f7fb000 - 000000004f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)[http://www.phonespell.org/phoneSpell.html](http://www.phonespell.org/phoneSpell.html)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x4f7d0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781c000 - 37feff0c
[    0.000000] ACPI: RSDP 000FE270, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 4F7EFC84, 0034 (r1 HP     099C     21110520 HP          1)
[    0.000000] ACPI: FACP 4F7EFC00, 0084 (r2 HP     099C            2 HP          1)
[    0.000000] ACPI: DSDT 4F7EFD50, 7D58 (r1 HP       DAU00     10000 MSFT  100000E)
[    0.000000] ACPI: FACS 4F7FAE80, 0040
[    0.000000] ACPI: APIC 4F7EFCB8, 005A (r1 HP     099C            1 HP          1)
[    0.000000] ACPI: MCFG 4F7EFD14, 003C (r1 HP     099C            1 HP          1)
[    0.000000] ACPI: SSDT 4F7F7AA8, 0371 (r1 HP       HPQPpc     1001 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 375MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
[    0.000000]   #4 [003781c000 - 0037feff0c]          RAMDISK ==> [003781c000 - 0037feff0c]
[    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0004f7d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004f7d0
[    0.000000] On node 0 totalpages: 325487
[    0.000000] free_area_init_node: node 0, pgdat c048d700, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 95362 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fec01000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 4f800000:90800000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322625
[    0.000000] Kernel command line: root=UUID=c5def422-2306-4745-aa8c-130779067370 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1728.993 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1275724k/1302336k available (2581k kernel code, 25252k reserved, 1163k data, 428k init, 384832k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
[    0.004000]       .data : 0xc038570a - 0xc04a8680   (1163 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038570a   (2581 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.98 BogoMIPS (lpj=6915972)
[    0.004043] Security Framework initialized
[    0.004057] SELinux:  Disabled at boot.
[    0.004088] AppArmor: AppArmor initialized
[    0.004099] Mount-cache hash table entries: 512
[    0.004333] Initializing cgroup subsys ns
[    0.004340] Initializing cgroup subsys cpuacct
[    0.004343] Initializing cgroup subsys memory
[    0.004366] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004369] CPU: L2 cache: 2048K
[    0.004387] Checking 'hlt' instruction... OK.
[    0.020573] SMP alternatives: switching to UP code
[    0.026734] Freeing SMP alternatives: 11k freed
[    0.026737] ACPI: Core revision 20080609
[    0.030269] ACPI: Checking initramfs for custom DSDT
[    0.424294] ENABLING IO-APIC IRQs
[    0.424492] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.467509] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.468029] Brought up 1 CPUs
[    0.468029] Total of 1 processors activated (3457.98 BogoMIPS).
[    0.468029] CPU0 attaching NULL sched-domain.
[    0.468029] net_namespace: 840 bytes
[    0.468029] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.468029] Booting paravirtualized kernel on bare hardware
[    0.468029] Time:  0:16:58  Date: 08/25/09
[    0.468029] NET: Registered protocol family 16
[    0.468029] EISA bus registered
[    0.468029] ACPI: bus type pci registered
[    0.468029] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.468029] PCI: MCFG area at e0000000 reserved in E820
[    0.468029] PCI: Using MMCONFIG for extended config space
[    0.468029] PCI: Using configuration type 1 for base access
[    0.468029] ACPI: EC: Look up EC in DSDT
[    0.492512] ACPI: Interpreter enabled
[    0.492519] ACPI: (supports S0 S3 S4 S5)
[    0.492536] ACPI: Using IOAPIC for interrupt routing
[    0.493696] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.519699] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.519703] ACPI: EC: driver started in interrupt mode
[    0.519778] ACPI: PCI Root Bridge [C002] (0000:00)
[    0.519884] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0400000, d047ffff]
[    0.519891] PCI: 0000:00:02.0 reg 14 io port: [7000, 7007]
[    0.519896] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff]
[    0.519901] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d0480000, d04bffff]
[    0.519935] PCI: 0000:00:02.1 reg 10 32bit mmio: [d0500000, d057ffff]
[    0.520047] PCI: 0000:00:1d.0 reg 20 io port: [2000, 201f]
[    0.520109] PCI: 0000:00:1d.1 reg 20 io port: [2020, 203f]
[    0.520171] PCI: 0000:00:1d.2 reg 20 io port: [2040, 205f]
[    0.520233] PCI: 0000:00:1d.3 reg 20 io port: [2060, 207f]
[    0.520297] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d0580000, d05803ff]
[    0.520367] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.520374] pci 0000:00:1d.7: PME# disabled
[    0.520468] PCI: 0000:00:1e.2 reg 10 io port: [2100, 21ff]
[    0.520476] PCI: 0000:00:1e.2 reg 14 io port: [2200, 223f]
[    0.520484] PCI: 0000:00:1e.2 reg 18 32bit mmio: [d0581000, d05811ff]
[    0.520492] PCI: 0000:00:1e.2 reg 1c 32bit mmio: [d0582000, d05820ff]
[    0.520537] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.520542] pci 0000:00:1e.2: PME# disabled
[    0.520575] PCI: 0000:00:1e.3 reg 10 io port: [2400, 24ff]
[    0.520583] PCI: 0000:00:1e.3 reg 14 io port: [2500, 257f]
[    0.520638] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.520643] pci 0000:00:1e.3: PME# disabled
[    0.520728] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.520735] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.520740] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
[    0.520766] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.520774] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.520782] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.520790] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.520797] PCI: 0000:00:1f.1 reg 20 io port: [2580, 258f]
[    0.520880] PCI: 0000:02:04.0 reg 10 32bit mmio: [d0000000, d0000fff]
[    0.520956] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.520962] pci 0000:02:04.0: PME# disabled
[    0.521005] PCI: 0000:02:06.0 reg 10 32bit mmio: [d0001000, d0001fff]
[    0.521039] pci 0000:02:06.0: supports D1
[    0.521041] pci 0000:02:06.0: supports D2
[    0.521043] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521049] pci 0000:02:06.0: PME# disabled
[    0.521091] PCI: 0000:02:06.2 reg 10 32bit mmio: [d0002000, d00027ff]
[    0.521101] PCI: 0000:02:06.2 reg 14 32bit mmio: [d0004000, d0007fff]
[    0.521172] pci 0000:02:06.2: supports D1
[    0.521174] pci 0000:02:06.2: supports D2
[    0.521177] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.521183] pci 0000:02:06.2: PME# disabled
[    0.521236] PCI: 0000:02:0e.0 reg 10 32bit mmio: [d000e000, d000ffff]
[    0.521301] pci 0000:02:0e.0: supports D1
[    0.521303] pci 0000:02:0e.0: supports D2
[    0.521305] pci 0000:02:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521310] pci 0000:02:0e.0: PME# disabled
[    0.521342] pci 0000:00:1e.0: transparent bridge
[    0.521350] PCI: bridge 0000:00:1e.0 32bit mmio: [d0000000, d03fffff]
[    0.521387] bus 00 -> node 0
[    0.521396] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.521867] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C068._PRT]
[    0.560770] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)
[    0.561068] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)
[    0.561366] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.561659] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)
[    0.561953] ACPI: PCI Interrupt Link [C0EE] (IRQs *10 11)
[    0.562244] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 *11)
[    0.562541] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.562828] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
[    0.563074] ACPI: Power Resource [C1C5] (on)
[    0.563229] ACPI: Power Resource [C244] (off)
[    0.563361] ACPI: Power Resource [C245] (off)
[    0.563493] ACPI: Power Resource [C246] (off)
[    0.563624] ACPI: Power Resource [C247] (off)
[    0.563705] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.563743] pnp: PnP ACPI init
[    0.563753] ACPI: bus type pnp registered
[    0.575421] pnp: PnP ACPI: found 11 devices
[    0.575424] ACPI: ACPI bus type pnp unregistered
[    0.575428] PnPBIOS: Disabled by ACPI PNP
[    0.575775] PCI: Using ACPI for IRQ routing
[    0.575898] NET: Registered protocol family 8
[    0.575898] NET: Registered protocol family 20
[    0.575898] NetLabel: Initializing
[    0.575898] NetLabel:  domain hash size = 128
[    0.575898] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.575898] NetLabel:  unlabeled traffic allowed by default
[    0.576131] hpet clockevent registered
[    0.576137] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.576143] hpet0: 3 64-bit timers, 14318180 Hz
[    0.577450] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.577453]    actual entries 65620
[    0.577549] AppArmor: AppArmor Filesystem Enabled
[    0.577572] ACPI: RTC can wake from S4
[    0.577579] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.577579] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.577579] system 00:00: iomem range 0x100000-0x4f7fffff could not be reserved
[    0.577579] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.577579] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.577579] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.577579] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.577579] system 00:09: ioport range 0x1000-0x107f has been reserved
[    0.577579] system 00:09: ioport range 0x1100-0x113f has been reserved
[    0.577579] system 00:09: ioport range 0x1200-0x121f has been reserved
[    0.577579] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.577579] system 00:09: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.577579] system 00:09: iomem range 0xfed20000-0xff41ffff could not be reserved
[    0.577579] system 00:09: iomem range 0xfed90000-0xfed9afff could not be reserved
[    0.577579] system 00:0a: iomem range 0xfeda0000-0xfedbffff could not be reserved
[    0.577579] system 00:0a: iomem range 0xfec01000-0xfec01fff could not be reserved
[    0.612769] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.612772] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.612778] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.612785] pci 0000:02:06.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.612793] pci 0000:02:06.0:   MEM window: 0x54000000-0x57ffffff
[    0.612799] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.612803] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.612810] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd03fffff
[    0.612815] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.612832] pci 0000:00:1e.0: setting latency timer to 64
[    0.612844] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.612851] bus: 00 index 0 io port: [0, ffff]
[    0.612854] bus: 00 index 1 mmio: [0, ffffffff]
[    0.612856] bus: 02 index 0 io port: [3000, 3fff]
[    0.612859] bus: 02 index 1 mmio: [d0000000, d03fffff]
[    0.612861] bus: 02 index 2 mmio: [50000000, 53ffffff]
[    0.612864] bus: 02 index 3 io port: [0, ffff]
[    0.612866] bus: 02 index 4 mmio: [0, ffffffff]
[    0.612869] bus: 03 index 0 io port: [3000, 30ff]
[    0.612871] bus: 03 index 1 io port: [3400, 34ff]
[    0.612873] bus: 03 index 2 mmio: [50000000, 53ffffff]
[    0.612876] bus: 03 index 3 mmio: [54000000, 57ffffff]
[    0.612885] NET: Registered protocol family 2
[    0.613011] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.613280] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.614075] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.614655] TCP: Hash tables configured (established 131072 bind 65536)
[    0.614659] TCP reno registered
[    0.614817] NET: Registered protocol family 1
[    0.614974] checking if image is initramfs... it is
[    1.080081] Switched to high resolution mode on CPU 0
[    1.412461] Freeing initrd memory: 8015k freed
[    1.413277] audit: initializing netlink socket (disabled)
[    1.413302] type=2000 audit(1251159418.412:1): initialized
[    1.419390] highmem bounce pool size: 64 pages
[    1.419398] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.421937] VFS: Disk quotas dquot_6.5.1
[    1.422034] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.422146] msgmni has been set to 1757
[    1.422288] io scheduler noop registered
[    1.422291] io scheduler anticipatory registered
[    1.422294] io scheduler deadline registered
[    1.422307] io scheduler cfq registered (default)
[    1.422326] pci 0000:00:02.0: Boot video device
[    1.422765] isapnp: Scanning for PnP cards...
[    1.776588] isapnp: No Plug & Play device found
[    1.814028] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.814724] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.814734] serial 0000:00:1e.3: PCI INT B disabled
[    1.816395] brd: module loaded
[    1.816475] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.816603] PNP: PS/2 Controller [PNP0303:C1C2,PNP0f13:C1C3] at 0x60,0x64 irq 1,12
[    1.818477] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.819221] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.819226] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.819229] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.819232] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.819235] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.819673] mice: PS/2 mouse device common for all mice
[    1.819822] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.819853] rtc0: alarms up to one month, y3k, hpet irqs
[    1.819974] EISA: Probing bus 0 at eisa.0
[    1.819982] Cannot allocate resource for EISA slot 1
[    1.819985] Cannot allocate resource for EISA slot 2
[    1.819987] Cannot allocate resource for EISA slot 3
[    1.820009] Cannot allocate resource for EISA slot 7
[    1.820015] EISA: Detected 0 cards.
[    1.820019] cpuidle: using governor ladder
[    1.820022] cpuidle: using governor menu
[    1.820593] TCP cubic registered
[    1.820627] Using IPI No-Shortcut mode
[    1.820827] registered taskstats version 1
[    1.820942]   Magic number: 5:606:254
[    1.820985] tty ttytd: hash matches
[    1.821087] pci 0000:00:1d.2: hash matches
[    1.821138] rtc_cmos 00:05: setting system clock to 2009-08-25 00:16:59 UTC (1251159419)
[    1.821142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.821144] EDD information not available.
[    1.821430] Freeing unused kernel memory: 428k freed
[    1.821487] Write protecting the kernel text: 2584k
[    1.821520] Write protecting the kernel read-only data: 940k
[    1.844375] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.080037] fuse init (API version 7.9)
[    2.284407] ACPI: Transitioning device [C248] to D3
[    2.292013] fan PNP0C0B:00: registered as cooling_device0
[    2.292020] ACPI: Fan [C248] (off)
[    2.292279] ACPI: Transitioning device [C249] to D3
[    2.300012] fan PNP0C0B:01: registered as cooling_device1
[    2.300024] ACPI: Fan [C249] (off)
[    2.300285] ACPI: Transitioning device [C24A] to D3
[    2.308013] fan PNP0C0B:02: registered as cooling_device2
[    2.308020] ACPI: Fan [C24A] (off)
[    2.308272] ACPI: Transitioning device [C24B] to D3
[    2.316012] fan PNP0C0B:03: registered as cooling_device3
[    2.316019] ACPI: Fan [C24B] (off)
[    2.350640] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.350691] processor ACPI0007:00: registered as cooling_device4
[    2.350696] ACPI: Processor [C000] (supports 8 throttling states)
[    2.366109] thermal LNXTHERM:01: registered as thermal_zone0
[    2.375198] Marking TSC unstable due to TSC halts in idle
[    2.380311] ACPI: Thermal Zone [TZ1] (70 C)
[    2.391117] thermal LNXTHERM:02: registered as thermal_zone1
[    2.399237] ACPI: Thermal Zone [TZ2] (55 C)
[    2.406274] thermal LNXTHERM:03: registered as thermal_zone2
[    2.418630] ACPI: Thermal Zone [TZ3] (31 C)
[    2.421460] thermal LNXTHERM:04: registered as thermal_zone3
[    2.427363] ACPI: Thermal Zone [TZ4] (59 C)
[    3.198660] usbcore: registered new interface driver usbfs
[    3.198690] usbcore: registered new interface driver hub
[    3.198731] usbcore: registered new device driver usb
[    3.208111] USB Universal Host Controller Interface driver v3.0
[    3.211355] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.211366] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.211370] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.211422] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.211461] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002000
[    3.211675] usb usb1: configuration #1 chosen from 1 choice
[    3.211707] hub 1-0:1.0: USB hub found
[    3.211715] hub 1-0:1.0: 2 ports detected
[    3.228086] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.328264] No dock devices found.
[    3.388462] SCSI subsystem initialized
[    3.416693] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.416706] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.416711] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.416738] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.416777] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[    3.416891] usb usb2: configuration #1 chosen from 1 choice
[    3.416922] hub 2-0:1.0: USB hub found
[    3.416931] hub 2-0:1.0: 2 ports detected
[    3.462108] libata version 3.00 loaded.
[    3.520380] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.520393] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.520397] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.520424] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.520463] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    3.520576] usb usb3: configuration #1 chosen from 1 choice
[    3.520606] hub 3-0:1.0: USB hub found
[    3.520613] hub 3-0:1.0: 2 ports detected
[    3.528023] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.624362] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.624374] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.624379] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.624404] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.624441] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00002060
[    3.624550] usb usb4: configuration #1 chosen from 1 choice
[    3.624581] hub 4-0:1.0: USB hub found
[    3.624588] hub 4-0:1.0: 2 ports detected
[    3.691636] usb 1-2: configuration #1 chosen from 1 choice
[    3.728273] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.728292] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.728297] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.728324] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.732242] ehci_hcd 0000:00:1d.7: debug port 1
[    3.732250] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.732259] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0580000
[    3.748037] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.748169] usb usb5: configuration #1 chosen from 1 choice
[    3.748200] hub 5-0:1.0: USB hub found
[    3.748208] hub 5-0:1.0: 8 ports detected
[    3.872123] usb 1-2: USB disconnect, address 2
[    3.960932] ohci1394 0000:02:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.010689] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.010748] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.010783] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.010799] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    4.015967] b44 0000:02:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.072082] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[    4.076013] Clocksource tsc unstable (delta = -113416845 ns)
[    4.076957] b44.c:v2.0
[    4.077055] ata_piix 0000:00:1f.1: version 2.12
[    4.077069] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.077110] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.084849] scsi0 : ata_piix
[    4.084960] scsi1 : ata_piix
[    4.085747] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14
[    4.085751] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15
[    4.096444] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:60:b7:8d:51
[    4.152079] usb 5-2: new high speed USB device using ehci_hcd and address 2
[    4.285654] usb 5-2: configuration #1 chosen from 1 choice
[    4.286730] usbcore: registered new interface driver libusual
[    4.300345] Initializing USB Mass Storage driver...
[    4.304995] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.306799] usbcore: registered new interface driver usb-storage
[    4.306804] USB Mass Storage support registered.
[    4.306892] usb-storage: device found at 2
[    4.306894] usb-storage: waiting for device to settle before scanning
[    4.312465] ata1.00: ATA-6: ST9408114A, 3.02, max UDMA/100
[    4.312469] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.312501] ata1.01: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max MWDMA2
[    4.328402] ata1.00: configured for UDMA/100
[    4.344412] ata1.01: configured for MWDMA2
[    4.344464] ata2: port disabled. ignoring.
[    4.344589] scsi 0:0:0:0: Direct-Access     ATA      ST9408114A       3.02 PQ: 0 ANSI: 5
[    4.344805] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.348790] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.02 PQ: 0 ANSI: 5
[    4.348890] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.374520] Driver 'sd' needs updating - please use bus_type methods
[    4.374635] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.374653] sd 0:0:0:0: [sda] Write Protect is off
[    4.374657] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.376717] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.376792] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.376808] sd 0:0:0:0: [sda] Write Protect is off
[    4.376811] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.376838] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.376842]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.401648]  sda1 sda2 < sda5 >
[    4.435079] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.446207] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.446212] Uniform CD-ROM driver Revision: 3.20
[    4.446311] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.738738] PM: Starting manual resume from disk
[    4.738742] PM: Resume from partition 8:5
[    4.738745] PM: Checking hibernation image.
[    4.738930] PM: Resume from disk failed.
[    4.762694] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.762699] EXT3-fs: write access will be enabled during recovery.
[    9.304171] usb-storage: device scan complete
[    9.304653] scsi 2:0:0:0: Direct-Access     WD       3200AAV External 1.65 PQ: 0 ANSI: 4
[    9.312501] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    9.313242] sd 2:0:0:0: [sdb] Write Protect is off
[    9.313245] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    9.313249] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.313864] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    9.314614] sd 2:0:0:0: [sdb] Write Protect is off
[    9.314617] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    9.314619] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.314624]  sdb: sdb1
[   14.709948] sd 2:0:0:0: [sdb] Attached SCSI disk
[   14.710197] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.200578] kjournald starting.  Commit interval 5 seconds
[   17.200598] EXT3-fs: sda1: orphan cleanup on readonly fs
[   17.200606] ext3_orphan_cleanup: deleting unreferenced inode 1278096
[   17.236848] ext3_orphan_cleanup: deleting unreferenced inode 1482827
[   17.236864] EXT3-fs: sda1: 2 orphan inodes deleted
[   17.236866] EXT3-fs: recovery complete.
[   17.337820] EXT3-fs: mounted filesystem with ordered data mode.
[   25.015820] udevd version 124 started
[   26.111753] Linux agpgart interface v0.103
[   26.161790] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   26.162197] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   26.165393] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   26.441846] intel_rng: FWH not detected
[   26.481146] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   26.492624] ACPI: Power Button (FF) [PWRF]
[   26.492764] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   26.504020] ACPI: Sleep Button (CM) [C1E8]
[   26.504121] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   26.504249] ACPI: Lid Switch [C1E9]
[   26.624690] iTCO_vendor_support: vendor-support=0
[   26.640719] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   26.640836] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   26.640992] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.678631] ACPI: AC Adapter [C172] (on-line)
[   26.792874] ACPI: Battery Slot [C174] (battery present)
[   26.793194] ACPI: Battery Slot [C173] (battery absent)
[   26.836257] ACPI: WMI: Mapper loaded
[   27.336147] ieee80211_crypt: registered algorithm 'NULL'
[   27.408133] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   27.408137] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   27.608208] Yenta: CardBus bridge found at 0000:02:06.0 [103c:099c]
[   27.608233] Yenta: Enabling burst memory read transactions
[   27.608239] Yenta: Using INTVAL to route CSC interrupts to PCI
[   27.608241] Yenta: Routing CardBus interrupts to PCI
[   27.608248] Yenta TI: socket 0000:02:06.0, mfunc 0x01aa1b22, devctl 0x64
[   27.692191] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   27.692196] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   27.840808] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   27.840814] Socket status: 30000006
[   27.840818] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   27.840827] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   27.840830] cs: IO port probe 0x3000-0x3fff: clean.
[   27.841079] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   27.841082] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   27.896332] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   27.896399] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   27.896454] firmware: requesting ipw2200-bss.fw
[   28.640882] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
[   28.656017] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)
[   30.295581] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   30.615309] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[   30.615317] serio: Synaptics pass-through port at isa0060/serio4/input0
[   30.655735] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   31.490045] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   31.496062] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   31.496089] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   31.838369] cs: IO port probe 0x100-0x3af: clean.
[   31.840086] cs: IO port probe 0x3e0-0x4ff: clean.
[   31.840817] cs: IO port probe 0x820-0x8ff: clean.
[   31.841411] cs: IO port probe 0xc00-0xcf7: clean.
[   31.842168] cs: IO port probe 0xa00-0xaff: clean.
[   32.420028] intel8x0_measure_ac97_clock: measured 55399 usecs
[   32.420032] intel8x0: clocking to 48000
[   33.025246] lp: driver loaded but no devices found
[   33.292528] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   33.832014] EXT3 FS on sda1, internal journal
[   34.691029] type=1505 audit(1251159452.837:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4104
[   34.910719] type=1505 audit(1251159453.057:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4109
[   34.911042] type=1505 audit(1251159453.057:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4109
[   35.073696] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.573855] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   36.670168] apm: BIOS not found.
[   36.831536] ppdev: user-space parallel port driver
[   38.478688] Bluetooth: Core ver 2.13
[   38.480394] NET: Registered protocol family 31
[   38.480399] Bluetooth: HCI device and connection manager initialized
[   38.480404] Bluetooth: HCI socket layer initialized
[   38.517688] Bluetooth: L2CAP ver 2.11
[   38.517694] Bluetooth: L2CAP socket layer initialized
[   38.549592] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.549599] Bluetooth: BNEP filters: protocol multicast
[   38.639291] Bridge firewalling registered
[   38.668518] Bluetooth: RFCOMM socket layer initialized
[   38.672040] Bluetooth: RFCOMM TTY layer initialized
[   38.672045] Bluetooth: RFCOMM ver 1.10
[   38.674776] Bluetooth: SCO (Voice Link) ver 0.6
[   38.674782] Bluetooth: SCO socket layer initialized
[   42.599639] [drm] Initialized drm 1.1.0 20060810
[   42.605814] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.605825] pci 0000:00:02.0: setting latency timer to 64
[   42.606974] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   42.824088] NET: Registered protocol family 17
[   84.909716] ieee80211_crypt: registered algorithm 'WEP'
[   88.607334] NET: Registered protocol family 10
[   88.609646] lo: Disabled Privacy Extensions
[   88.611826] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   99.260026] eth1: no IPv6 routers present

---

### Post by Rocket2DMn on 2009-08-24
Hmm, it seems to look OK, let's try mounting the disk manually.  First we'll create a mount point, then mount it
```
sudo mkdir /media/ntfs-drive
sudo mount -t ntfs-3g /dev/sdb1 /media/ntfs-drive
```
Are you able to access the drive now?  There should be a shortcut on your desktop, but if not, navigate in nautilus to /media/ntfs-drive and you should see your files.

Although having spaces in the name of a drive isn't typically a problem, I have seen issues with MY BOOK drives before.  If you want, you can change the label of the drive to something more useful, and without spaces in it.  Have a look at [uhelp]community/RenameUSBDrive[/uhelp] if you're interested.
EDIT: help.ubuntu.com/community isn't responding for me right now, perhaps try later if you can't access that page either.

---

### Post by avacomputers on 2009-08-24
I get this upon running the second command.

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/ntfs-drive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/ntfs-drive ntfs-3g force 0 0
aalexander@aalexander-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/ntfs-drive


---

### Post by Rocket2DMn on 2009-08-24
Ah hah!  Ok, you have two options then.  The first, and preferred option is to connect the drive to a Windows computer, then Safely Remove it from the system tray.  Then when you plug it back into Ubuntu, it should work.  If you don't have access to a Windows system, we can force the mount by resetting the NTFS logfile using the command it gave us:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/ntfs-drive -o force
```
Then you can manually unmount it and remove the directory we made:
```
sudo umount /dev/sdb1
sudo rmdir /media/ntfs-drive
```
Then unplug the drive and plug it back in, and it should automount normally.

---

### Post by avacomputers on 2009-08-24
I did a force mount and it works. THanks for all you help.

---

