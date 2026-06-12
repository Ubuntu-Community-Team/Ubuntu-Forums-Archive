---
title: "System unresponsive during I/O"
date: 2009-08-25
forum: General Help
---

### Post by shylent on 2009-08-25
I've run into the following problem while arranging my stuff - whenever there is a long i/o operation going on (copying some videos/music), the system becomes extremely unresponsive - it is impossible to do anything, - menus don't open, buttons don't get pressed, etc. This happens when I try to copy nautilus and via the command line as well (through mc or just cp) - so it is not related to the GUI, apparently.

The system runs on a Core2 Duo cpu. I have 4Gb RAM. So, clearly, it shouldn't lock up like that.

Don't know what info you might need, but here's some:

```
$ uname -a
Linux localhost 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
``````

$df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext3     19G  2.9G   15G  17% /
tmpfs        tmpfs    1.8G     0  1.8G   0% /lib/init/rw
varrun       tmpfs    1.8G   96K  1.8G   1% /var/run
varlock      tmpfs    1.8G     0  1.8G   0% /var/lock
udev         tmpfs    1.8G  160K  1.8G   1% /dev
tmpfs        tmpfs    1.8G  200K  1.8G   1% /dev/shm
lrm          tmpfs    1.8G  2.2M  1.8G   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5     ext3    441M   36M  383M   9% /boot
/dev/sda8     ext3    410G   83G  307G  22% /home

``````
$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by P4man on 2009-08-25
Hmm.. not sure at at all, but..
2 things come to mind. First, open a terminal and run "top". keep it open and visible while you copy something, and see what is eating your cpu cycles.

Second thing that comes to mind.. the times Ive seen this happen on windows, it was due to the harddrives being in PIO mode, rather than DMA. Perhaps you can attach the output of dmesg ?

Also, are the copies unusually slow or not ? What transfer rates are you getting?

---

### Post by nikhilk on 2009-08-25
It seems that you have a nvidia GPU viz. GeForce 8600 GTS and you are probably not using the nvidia drivers.

I am assuming you seeing a GUI slowdown instead of a overall system slowdown.

---

### Post by shylent on 2009-08-25
> **nikhilk said:**
> It seems that you have a nvidia GPU viz. GeForce 8600 GTS and you are probably not using the nvidia drivers.

I am assuming you seeing a GUI slowdown instead of a overall system slowdown.

That might be it, however I distinctly remember even the console stuff lagging like hell (like top not refreshing in time et cetera). I am using nvidia drivers (as indicated in System->Administration->Hardware Drivers, says, "this driver is activated and currently in use").

[quote=P4man]Hmm.. not sure at at all, but..
2 things come to mind. First, open a terminal and run "top". keep it open and visible while you copy something, and see what is eating your cpu cycles.

Second thing that comes to mind.. the times Ive seen this happen on windows, it was due to the harddrives being in PIO mode, rather than DMA. Perhaps you can attach the output of dmesg ?

Also, are the copies unusually slow or not ? What transfer rates are you getting? [/quote]

First of all, I've used top during the long i/o and it didn't show anything out of the ordinary. Anyway, since I have 2 cores, the copying process should not consume all CPU time. As for transfer rates, I was getting around 35-40 MB/sec, which is quite normal, I believe.

Thanks in advance, everyone. Your help is very appreciated.

Here is the output of dmesg (rather long-ish, I am afraid).

```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xdfee0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dfee0000 (usable)
[    0.000000]  modified: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  modified: 00000000dfef0000 - 00000000dff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378ba000 - 37fefebd
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb2ebd
[    0.000000] Move RAMDISK from 00000000378ba000 - 0000000037fefebc to 0087d000 - 00fb2ebc
[    0.000000] ACPI: RSDP 000F6FA0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT DFEE3040, 0034 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP DFEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT DFEE3180, 4A88 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS DFEE0000, 0040
[    0.000000] ACPI: HPET DFEE7D80, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG DFEE7E00, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC DFEE7C80, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2698MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb2ebd]      NEW RAMDISK ==> [000087d000 - 0000fb2ebd]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f55d0] 000f55d0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000dfee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000dfee0
[    0.000000] On node 0 totalpages: 917093
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 5398 pages used for memmap
[    0.000000]   HighMem zone: 685516 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 909927
[    0.000000] Kernel command line: root=UUID=5cce99a4-ca3e-4f24-904e-75911b832413 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2333.156 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 18344320 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3604728k/3668864k available (4115k kernel code, 62708k reserved, 2199k data, 532k init, 2763656k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4666.31 BogoMIPS (lpj=9332624)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017999] ACPI: Core revision 20080926
[    0.019472] ACPI: Checking initramfs for custom DSDT
[    0.271852] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.311541] CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[    0.312001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4666.64 BogoMIPS (lpj=9333293)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.396553] CPU1: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[    0.396566] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.400034] Brought up 2 CPUs
[    0.400036] Total of 2 processors activated (9332.95 BogoMIPS).
[    0.400080] CPU0 attaching sched-domain:
[    0.400083]  domain 0: span 0-1 level MC
[    0.400085]   groups: 0 1
[    0.400090] CPU1 attaching sched-domain:
[    0.400092]  domain 0: span 0-1 level MC
[    0.400094]   groups: 1 0
[    0.400153] net_namespace: 776 bytes
[    0.400153] Booting paravirtualized kernel on bare hardware
[    0.400280] Time: 10:32:04  Date: 08/25/09
[    0.400280] regulator: core version 0.5
[    0.400280] NET: Registered protocol family 16
[    0.400280] EISA bus registered
[    0.400280] ACPI: bus type pci registered
[    0.400280] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.400280] PCI: MCFG area at f0000000 reserved in E820
[    0.400280] PCI: Using MMCONFIG for extended config space
[    0.400280] PCI: Using configuration type 1 for base access
[    0.400280] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.400280] mtrr: probably your BIOS does not setup all CPUs.
[    0.400280] mtrr: corrected configuration.
[    0.400944] ACPI: EC: Look up EC in DSDT
[    0.407484] ACPI: Interpreter enabled
[    0.407492] ACPI: (supports S0 S3 S4 S5)
[    0.407509] ACPI: Using IOAPIC for interrupt routing
[    0.411724] ACPI: No dock devices found.
[    0.411734] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.411809] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.411811] pci 0000:00:01.0: PME# disabled
[    0.411873] pci 0000:00:1a.0: reg 20 io port: [0xe100-0xe11f]
[    0.411928] pci 0000:00:1a.1: reg 20 io port: [0xe200-0xe21f]
[    0.411982] pci 0000:00:1a.2: reg 20 io port: [0xe000-0xe01f]
[    0.412042] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfa205000-0xfa2053ff]
[    0.412106] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfa200000-0xfa203fff]
[    0.412131] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.412134] pci 0000:00:1b.0: PME# disabled
[    0.412173] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.412176] pci 0000:00:1c.0: PME# disabled
[    0.412221] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.412224] pci 0000:00:1c.4: PME# disabled
[    0.412265] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.412268] pci 0000:00:1c.5: PME# disabled
[    0.412315] pci 0000:00:1d.0: reg 20 io port: [0xe300-0xe31f]
[    0.412369] pci 0000:00:1d.1: reg 20 io port: [0xe400-0xe41f]
[    0.412423] pci 0000:00:1d.2: reg 20 io port: [0xe500-0xe51f]
[    0.412469] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfa204000-0xfa2043ff]
[    0.412597] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.412601] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.412636] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.412641] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.412646] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.412651] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.412656] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.412661] pci 0000:00:1f.2: reg 24 io port: [0xfc00-0xfc0f]
[    0.412692] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfa206000-0xfa2060ff]
[    0.412704] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.412740] pci 0000:00:1f.5: reg 10 io port: [0xe700-0xe707]
[    0.412745] pci 0000:00:1f.5: reg 14 io port: [0xe800-0xe803]
[    0.412750] pci 0000:00:1f.5: reg 18 io port: [0xe900-0xe907]
[    0.412755] pci 0000:00:1f.5: reg 1c io port: [0xea00-0xea03]
[    0.412760] pci 0000:00:1f.5: reg 20 io port: [0xeb00-0xeb0f]
[    0.412765] pci 0000:00:1f.5: reg 24 io port: [0xec00-0xec0f]
[    0.412806] pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.412814] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.412823] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.412828] pci 0000:01:00.0: reg 24 io port: [0xb000-0xb07f]
[    0.412833] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.412874] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.412877] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.412881] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.412915] pci 0000:00:1c.0: bridge io port: [0xa000-0xafff]
[    0.413004] pci 0000:03:00.0: reg 24 32bit mmio: [0xfa000000-0xfa001fff]
[    0.413023] pci 0000:03:00.0: PME# supported from D3hot
[    0.413027] pci 0000:03:00.0: PME# disabled
[    0.413077] pci 0000:03:00.1: reg 10 io port: [0xc000-0xc007]
[    0.413085] pci 0000:03:00.1: reg 14 io port: [0xc100-0xc103]
[    0.413093] pci 0000:03:00.1: reg 18 io port: [0xc200-0xc207]
[    0.413102] pci 0000:03:00.1: reg 1c io port: [0xc300-0xc303]
[    0.413110] pci 0000:03:00.1: reg 20 io port: [0xc400-0xc40f]
[    0.413180] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
[    0.413184] pci 0000:00:1c.4: bridge 32bit mmio: [0xfa000000-0xfa0fffff]
[    0.413240] pci 0000:04:00.0: reg 10 io port: [0xd000-0xd0ff]
[    0.413260] pci 0000:04:00.0: reg 18 64bit mmio: [0xf9000000-0xf9000fff]
[    0.413281] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.413293] pci 0000:04:00.0: supports D1 D2
[    0.413295] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.413299] pci 0000:04:00.0: PME# disabled
[    0.413342] pci 0000:00:1c.5: bridge io port: [0xd000-0xdfff]
[    0.413345] pci 0000:00:1c.5: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.413386] pci 0000:05:06.0: reg 10 32bit mmio: [0xfa104000-0xfa1047ff]
[    0.413392] pci 0000:05:06.0: reg 14 32bit mmio: [0xfa100000-0xfa103fff]
[    0.413424] pci 0000:05:06.0: supports D1 D2
[    0.413425] pci 0000:05:06.0: PME# supported from D0 D1 D2 D3hot
[    0.413429] pci 0000:05:06.0: PME# disabled
[    0.413464] pci 0000:00:1e.0: transparent bridge
[    0.413469] pci 0000:00:1e.0: bridge 32bit mmio: [0xfa100000-0xfa1fffff]
[    0.413491] bus 00 -> node 0
[    0.413496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.413754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.413843] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.413935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.414020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.427743] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.427838] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.427930] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.428034] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.428126] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.428218] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.428310] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.428402] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.428522] ACPI: WMI: Mapper loaded
[    0.428572] SCSI subsystem initialized
[    0.428572] libata version 3.00 loaded.
[    0.428572] usbcore: registered new interface driver usbfs
[    0.428572] usbcore: registered new interface driver hub
[    0.428572] usbcore: registered new device driver usb
[    0.428572] PCI: Using ACPI for IRQ routing
[    0.436008] Bluetooth: Core ver 2.13
[    0.436021] NET: Registered protocol family 31
[    0.436021] Bluetooth: HCI device and connection manager initialized
[    0.436021] Bluetooth: HCI socket layer initialized
[    0.436021] NET: Registered protocol family 8
[    0.436021] NET: Registered protocol family 20
[    0.436028] NetLabel: Initializing
[    0.436030] NetLabel:  domain hash size = 128
[    0.436031] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.436042] NetLabel:  unlabeled traffic allowed by default
[    0.436053] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.436057] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.440053] AppArmor: AppArmor Filesystem Enabled
[    0.448007] pnp: PnP ACPI init
[    0.448014] ACPI: bus type pnp registered
[    0.450333] pnp: PnP ACPI: found 14 devices
[    0.450335] ACPI: ACPI bus type pnp unregistered
[    0.450338] PnPBIOS: Disabled by ACPI PNP
[    0.450346] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.450348] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.450350] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.450352] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.450355] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.450362] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[    0.450367] system 00:0b: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.450372] system 00:0c: iomem range 0xcca00-0xcffff has been reserved
[    0.450374] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.450376] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.450379] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.450381] system 00:0c: iomem range 0xdfee0000-0xdfefffff could not be reserved
[    0.450383] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.450386] system 00:0c: iomem range 0x100000-0xdfedffff could not be reserved
[    0.450388] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.450390] system 00:0c: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.450393] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.450395] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.450397] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.450399] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.450402] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.485071] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.485074] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.485077] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.485080] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.485084] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.485087] pci 0000:00:1c.0:   IO window: 0xa000-0xafff
[    0.485091] pci 0000:00:1c.0:   MEM window: disabled
[    0.485094] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.485099] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.485102] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.485106] pci 0000:00:1c.4:   MEM window: 0xfa000000-0xfa0fffff
[    0.485109] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.485115] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.485117] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.485122] pci 0000:00:1c.5:   MEM window: 0xf8000000-0xf9ffffff
[    0.485125] pci 0000:00:1c.5:   PREFETCH window: 0x000000fa300000-0x000000fa3fffff
[    0.485131] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.485132] pci 0000:00:1e.0:   IO window: disabled
[    0.485136] pci 0000:00:1e.0:   MEM window: 0xfa100000-0xfa1fffff
[    0.485140] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.485150] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.485154] pci 0000:00:01.0: setting latency timer to 64
[    0.485159] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.485163] pci 0000:00:1c.0: setting latency timer to 64
[    0.485169] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.485172] pci 0000:00:1c.4: setting latency timer to 64
[    0.485179] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.485182] pci 0000:00:1c.5: setting latency timer to 64
[    0.485188] pci 0000:00:1e.0: setting latency timer to 64
[    0.485191] bus: 00 index 0 io port: [0x00-0xffff]
[    0.485193] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.485195] bus: 01 index 0 io port: [0xb000-0xbfff]
[    0.485196] bus: 01 index 1 mmio: [0xf4000000-0xf7ffffff]
[    0.485198] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.485200] bus: 01 index 3 mmio: [0x0-0x0]
[    0.485202] bus: 02 index 0 io port: [0xa000-0xafff]
[    0.485203] bus: 02 index 1 mmio: [0x0-0x0]
[    0.485205] bus: 02 index 2 mmio: [0x0-0x0]
[    0.485206] bus: 02 index 3 mmio: [0x0-0x0]
[    0.485208] bus: 03 index 0 io port: [0xc000-0xcfff]
[    0.485210] bus: 03 index 1 mmio: [0xfa000000-0xfa0fffff]
[    0.485211] bus: 03 index 2 mmio: [0x0-0x0]
[    0.485213] bus: 03 index 3 mmio: [0x0-0x0]
[    0.485214] bus: 04 index 0 io port: [0xd000-0xdfff]
[    0.485216] bus: 04 index 1 mmio: [0xf8000000-0xf9ffffff]
[    0.485218] bus: 04 index 2 mmio: [0xfa300000-0xfa3fffff]
[    0.485219] bus: 04 index 3 mmio: [0x0-0x0]
[    0.485221] bus: 05 index 0 mmio: [0x0-0x0]
[    0.485223] bus: 05 index 1 mmio: [0xfa100000-0xfa1fffff]
[    0.485224] bus: 05 index 2 mmio: [0x0-0x0]
[    0.485226] bus: 05 index 3 io port: [0x00-0xffff]
[    0.485228] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.485234] NET: Registered protocol family 2
[    0.500048] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.500231] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.500532] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.500601] Switched to high resolution mode on CPU 1
[    0.500678] TCP: Hash tables configured (established 131072 bind 65536)
[    0.500680] TCP reno registered
[    0.504008] Switched to high resolution mode on CPU 0
[    0.508062] NET: Registered protocol family 1
[    0.508155] checking if image is initramfs... it is
[    1.021708] Freeing initrd memory: 7383k freed
[    1.021884] cpufreq: No nForce2 chipset.
[    1.022002] audit: initializing netlink socket (disabled)
[    1.022021] type=2000 audit(1251196324.020:1): initialized
[    1.028144] highmem bounce pool size: 64 pages
[    1.028148] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.029267] VFS: Disk quotas dquot_6.5.1
[    1.029315] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.029819] fuse init (API version 7.10)
[    1.029888] msgmni has been set to 1658
[    1.030036] alg: No test for stdrng (krng)
[    1.030045] io scheduler noop registered
[    1.030047] io scheduler anticipatory registered
[    1.030049] io scheduler deadline registered
[    1.030059] io scheduler cfq registered (default)
[    1.030191] pci 0000:01:00.0: Boot video device
[    1.032169] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.032198] pcieport-driver 0000:00:01.0: found MSI capability
[    1.032217] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.032224] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.032236] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.032274] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.032303] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.032322] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.032332] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.032345] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.032354] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.032400] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.032428] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.032448] pcieport-driver 0000:00:1c.4: irq 2301 for MSI/MSI-X
[    1.032458] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.032468] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.032480] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.032535] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.032564] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.032584] pcieport-driver 0000:00:1c.5: irq 2300 for MSI/MSI-X
[    1.032593] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.032603] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.032613] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.032669] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.032906] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.033031] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.033034] ACPI: Power Button (FF) [PWRF]
[    1.033070] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.033072] ACPI: Power Button (CM) [PWRB]
[    1.033316] processor ACPI_CPU:00: registered as cooling_device0
[    1.033319] ACPI: Processor [CPU0] (supports 2 throttling states)
[    1.033362] processor ACPI_CPU:01: registered as cooling_device1
[    1.033365] ACPI: Processor [CPU1] (supports 2 throttling states)
[    1.034927] isapnp: Scanning for PnP cards...
[    1.387750] isapnp: No Plug & Play device found
[    1.396596] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.396678] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.396982] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.397637] brd: module loaded
[    1.397897] loop: module loaded
[    1.397949] Fixed MDIO Bus: probed
[    1.397954] PPP generic driver version 2.4.2
[    1.397999] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.398022] Driver 'sd' needs updating - please use bus_type methods
[    1.398030] Driver 'sr' needs updating - please use bus_type methods
[    1.398066] ahci 0000:03:00.0: version 3.0
[    1.398078] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.412031] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.412034] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.412039] ahci 0000:03:00.0: setting latency timer to 64
[    1.412191] scsi0 : ahci
[    1.412254] scsi1 : ahci
[    1.412311] ata1: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000100 irq 16
[    1.412314] ata2: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000180 irq 16
[    1.732022] ata1: SATA link down (SStatus 0 SControl 300)
[    2.068022] ata2: SATA link down (SStatus 0 SControl 300)
[    2.084040] ata_piix 0000:00:1f.2: version 2.12
[    2.084049] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.084053] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.084091] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.084136] scsi2 : ata_piix
[    2.084185] scsi3 : ata_piix
[    2.084691] ata3: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.084695] ata4: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.734561] ata3.00: SATA link down (SStatus 0 SControl 300)
[    2.734568] ata3.01: SATA link down (SStatus 0 SControl 300)
[    3.528050] ata4.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.528060] ata4.01: SATA link down (SStatus 0 SControl 300)
[    3.544163] ata4.00: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[    3.544167] ata4.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
[    3.544169] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.560537] ata4.00: configured for UDMA/133
[    3.560623] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    3.560698] sd 3:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.560711] sd 3:0:0:0: [sda] Write Protect is off
[    3.560713] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.560734] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.560784] sd 3:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.560797] sd 3:0:0:0: [sda] Write Protect is off
[    3.560799] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.560819] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.560822]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    3.597428] sd 3:0:0:0: [sda] Attached SCSI disk
[    3.597466] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    3.597481] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.597484] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.597517] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.597558] scsi4 : ata_piix
[    3.597602] scsi5 : ata_piix
[    3.598029] ata5: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    3.598032] ata6: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    3.926533] ata5: SATA link down (SStatus 0 SControl 300)
[    4.254532] ata6: SATA link down (SStatus 0 SControl 300)
[    4.254853] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    4.254858] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.254885] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    4.254932] scsi6 : pata_jmicron
[    4.254981] scsi7 : pata_jmicron
[    4.255486] ata7: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 17
[    4.255488] ata8: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 17
[    4.416523] ata7.00: ATAPI: Optiarc DVD RW AD-7173A, 1-02, max UDMA/66
[    4.432539] ata7.00: configured for UDMA/66
[    4.600204] scsi 6:0:0:0: CD-ROM            Optiarc  DVD RW AD-7173A  1-02 PQ: 0 ANSI: 5
[    4.602842] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.602845] Uniform CD-ROM driver Revision: 3.20
[    4.602913] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.602945] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    4.603197] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.603212] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.603222] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.603225] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.603268] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.607149] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.607159] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfa205000
[    4.620007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.620067] usb usb1: configuration #1 chosen from 1 choice
[    4.620089] hub 1-0:1.0: USB hub found
[    4.620095] hub 1-0:1.0: 6 ports detected
[    4.620184] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.620193] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.620195] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.620229] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.624124] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.624134] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa204000
[    4.640007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.640051] usb usb2: configuration #1 chosen from 1 choice
[    4.640071] hub 2-0:1.0: USB hub found
[    4.640076] hub 2-0:1.0: 6 ports detected
[    4.640153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.640166] uhci_hcd: USB Universal Host Controller Interface driver
[    4.640181] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.640186] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.640188] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.640221] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.640241] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[    4.640299] usb usb3: configuration #1 chosen from 1 choice
[    4.640322] hub 3-0:1.0: USB hub found
[    4.640327] hub 3-0:1.0: 2 ports detected
[    4.640392] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.640398] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.640401] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.640434] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.640458] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200
[    4.640518] usb usb4: configuration #1 chosen from 1 choice
[    4.640538] hub 4-0:1.0: USB hub found
[    4.640543] hub 4-0:1.0: 2 ports detected
[    4.640609] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.640614] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.640616] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.640654] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.640673] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[    4.640728] usb usb5: configuration #1 chosen from 1 choice
[    4.640748] hub 5-0:1.0: USB hub found
[    4.640753] hub 5-0:1.0: 2 ports detected
[    4.640821] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.640827] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.640829] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.640866] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.640884] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[    4.640939] usb usb6: configuration #1 chosen from 1 choice
[    4.640964] hub 6-0:1.0: USB hub found
[    4.640970] hub 6-0:1.0: 2 ports detected
[    4.641036] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.641041] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.641043] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.641075] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.641094] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    4.641150] usb usb7: configuration #1 chosen from 1 choice
[    4.641170] hub 7-0:1.0: USB hub found
[    4.641176] hub 7-0:1.0: 2 ports detected
[    4.641242] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.641247] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.641250] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.641282] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.641301] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[    4.641356] usb usb8: configuration #1 chosen from 1 choice
[    4.641381] hub 8-0:1.0: USB hub found
[    4.641386] hub 8-0:1.0: 2 ports detected
[    4.641494] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.641496] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.641579] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.644032] mice: PS/2 mouse device common for all mice
[    4.644143] rtc_cmos 00:03: RTC can wake from S4
[    4.644168] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.644189] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.644238] device-mapper: uevent: version 1.0.3
[    4.644301] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.644356] device-mapper: multipath: version 1.0.5 loaded
[    4.644358] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.644417] EISA: Probing bus 0 at eisa.0
[    4.644441] EISA: Detected 0 cards.
[    4.644481] cpuidle: using governor ladder
[    4.644483] cpuidle: using governor menu
[    4.644901] TCP cubic registered
[    4.644979] NET: Registered protocol family 10
[    4.645334] lo: Disabled Privacy Extensions
[    4.645611] NET: Registered protocol family 17
[    4.645626] Bluetooth: L2CAP ver 2.11
[    4.645627] Bluetooth: L2CAP socket layer initialized
[    4.645630] Bluetooth: SCO (Voice Link) ver 0.6
[    4.645631] Bluetooth: SCO socket layer initialized
[    4.645654] Bluetooth: RFCOMM socket layer initialized
[    4.645659] Bluetooth: RFCOMM TTY layer initialized
[    4.645660] Bluetooth: RFCOMM ver 1.10
[    4.645697] Using IPI No-Shortcut mode
[    4.645756] registered taskstats version 1
[    4.645862]   Magic number: 5:428:528
[    4.645913] rtc_cmos 00:03: setting system clock to 2009-08-25 10:32:08 UTC (1251196328)
[    4.645916] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.645918] EDD information not available.
[    4.646127] Freeing unused kernel memory: 532k freed
[    4.646231] Write protecting the kernel text: 4116k
[    4.646268] Write protecting the kernel read-only data: 1528k
[    4.673701] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.825838] Floppy drive(s): fd0 is 1.44M
[    4.843884] FDC 0 is a post-1991 82077
[    4.848853] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.848867] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.848881] r8169 0000:04:00.0: setting latency timer to 64
[    4.848974] r8169 0000:04:00.0: irq 2299 for MSI/MSI-X
[    4.849498] eth0: RTL8168b/8111b at 0xf7c56000, 00:1a:4d:48:a5:99, XID 38000000 IRQ 2299
[    4.944560] ohci1394 0000:05:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.994278] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fa104000-fa1047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.204511] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.404043] PM: Starting manual resume from disk
[    5.404045] PM: Resume from partition 8:7
[    5.404047] PM: Checking hibernation image.
[    5.404201] PM: Resume from disk failed.
[    5.422921] kjournald starting.  Commit interval 5 seconds
[    5.422928] EXT3-fs: mounted filesystem with ordered data mode.
[    5.552399] usb 3-1: configuration #1 chosen from 1 choice
[    6.312598] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c3e06800001a4d]
[    8.341502] udev: starting version 141
[    8.464936] parport_pc 00:08: reported by Plug and Play ACPI
[    8.464979] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.508472] usbcore: registered new interface driver hiddev
[    8.523833] input: Razer Razer 1600dpi 3 button optical mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input4
[    8.544087] generic-usb 0003:1532:0003.0001: input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi 3 button optical mouse] on usb-0000:00:1a.0-1/input0
[    8.544106] usbcore: registered new interface driver usbhid
[    8.544109] usbhid: v2.6:USB HID core driver
[    8.595409] ppdev: user-space parallel port driver
[    8.624268] Linux agpgart interface v0.103
[    8.725999] nvidia: module license 'NVIDIA' taints kernel.
[    8.978177] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.978183] nvidia 0000:01:00.0: setting latency timer to 64
[    8.979004] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.069124] iTCO_vendor_support: vendor-support=0
[    9.070281] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.070395] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[    9.070407] iTCO_wdt: No card detected
[    9.398001] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.398057] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.429913] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.533114] lp0: using parport0 (interrupt-driven).
[    9.609488] Adding 8000328k swap on /dev/sda7.  Priority:-1 extents:1 across:8000328k
[   10.137845] EXT3 FS on sda6, internal journal
[   10.867119] kjournald starting.  Commit interval 5 seconds
[   10.867317] EXT3 FS on sda5, internal journal
[   10.867321] EXT3-fs: mounted filesystem with ordered data mode.
[   10.881889] kjournald starting.  Commit interval 5 seconds
[   10.884182] EXT3 FS on sda8, internal journal
[   10.884185] EXT3-fs: mounted filesystem with ordered data mode.
[   11.078320] type=1505 audit(1251181934.930:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2055
[   11.116045] type=1505 audit(1251181934.966:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2059
[   11.116110] type=1505 audit(1251181934.966:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2059
[   11.116143] type=1505 audit(1251181934.966:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2059
[   11.116174] type=1505 audit(1251181934.966:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2059
[   11.219894] type=1505 audit(1251181935.070:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2064
[   11.220006] type=1505 audit(1251181935.070:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2064
[   11.242395] type=1505 audit(1251181935.094:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2068
[   13.927705] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.927708] Bluetooth: BNEP filters: protocol multicast
[   13.934805] Bridge firewalling registered
[   19.146742] r8169: eth0: link up
[   19.146747] r8169: eth0: link up
[   29.844004] eth0: no IPv6 routers present
```

---

### Post by P4man on 2009-08-25
I very much doubt it would be related to videodrivers. And you got the restricted drivers anyway.

I cant see anything wrong in your dmesg either. Looks like your sata drivers and opticals are all working at full speed, no PIO there (btw, trust me, if you would use PIO, not even a quad or octal core cpu would keep up with the drive speed, and it would hog all cores -assuming it threads well- and still produce terrible transfer rates).

Anyway, can you see something out of the ordinary in the log viewer while you are copying a large file?

Also, not too likely to shed much light on this, but try running iotop (its in the repo's) while doing a copy.

---

### Post by shylent on 2009-08-25
Yes, considering, that operating in programmed i/o involves so much  CPU overhead (are there even any devices left, that work in this mode?), it would surely kill the performance no matter what.  I will make some more testing when I have a free minute and get back with results.

  Thanks a lot for your help.

---

### Post by P4man on 2009-08-25
> **shylent said:**
> are there even any devices left, that work in this mode?

Yes,.. and no. If DMA fails for whatever reason, IDE (and I think, but not sure SATA) devices will fall back to PIO. Even today.  Only really happens when there is a problem with the drive, controller or BIOS. Or software.

---

### Post by shylent on 2009-09-04
Hmm, I've been checking, but really, I can see nothing wrong in iotop.  However, there is something I forgot to mention. When I've installed Ubuntu all went well, but I was greeted by grub error 18. I've switched the hard disk addressing method from CHS to LBA and it worked fine ever since. Maybe this slowdown is somehow caused by the addressing method?

---

### Post by P4man on 2009-09-04
Dont know.. it would surprise me. To be honest, im pretty stumped. But Id try narrowing it down further. For instance, see if its reading or writing or both that cause this. You could try writing with this:
```

dd if=/dev/random of=uselessfile
```

run it for a while and see if your pc slows down. Then stop it with control+C (and delete the uselessfile). This just generates a file with random contents.

For reading, try:

```
sudo dd if=/dev/sda1 of=/dev/null
```

That copies your harddisk to nowhere, and should be a good read test I think.

---

### Post by MMoudry on 2009-11-24
I suspect that your write cache is disabled....

---

### Post by MMoudry on 2009-11-24
or this : [http://ubuntuforums.org/showthread.php?t=1127485&highlight=slowdown+copy](http://ubuntuforums.org/showthread.php?t=1127485&highlight=slowdown+copy)

---

