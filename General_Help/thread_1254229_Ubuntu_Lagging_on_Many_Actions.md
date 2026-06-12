---
title: "Ubuntu Lagging on Many Actions"
date: 2009-08-31
forum: General Help
---

### Post by lwadurnew on 2009-08-31
Hello,

Ubuntu 9.04 Desktop's running extremely slow for certain activities.  It's most noticable when, say, I pull down a menu on Gnome and the icons always take a second or two to load.  Or when I roll over code in Eclipse and the code detail popup takes several (upwards of 3 or 4) seconds while to appear, while in the mean time my machine completely stalls.  My initial instinct was that perhaps it was a lack of memory, so I upgraded to 4GB, and that didn't solve it.  My laptop is 1.6ghz Core 2 Duo, and although it's not top of the line, I certainly feel like it should be fast enough for it not to lag like this.  What might the issue be, and how might I remedy it?  Perhaps there's something amiss with the hard drive or its settings?  I've disabled all but the most essentially background processes, and there are no other processes hogging resources while this lagging occurs.

Thanks!

---

### Post by Kristofer Van Orton on 2009-08-31
Are you running screenlets? I had it for a bit but noticed just by running certain screenlets it used a lot of the memory
also maybe try running update manager, maybe you need some driver updates

sorry i wish i could be of more help but im trying :D

---

### Post by P4man on 2009-08-31
does it always happen, even after a fresh boot, or is something that gets progressively worse ? (ie, a memory leak somewhere?).

Is there a lot of harddisk activity ? Is your harddisk performing normally ? If in doubt, try copying some large folder and see if you get a transfer rate > 20 MB/s. Or run "bonnie" to actually benchmark it.

---

### Post by lwadurnew on 2009-08-31
Krisofer: Not running screenlets.  Thanks for your response though.

P4man:  Here's the output for bonnie:

Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
lwadurneww-lapt 6G 21639  62 21862  12 12944   8 31381  78 33165  11  95.6   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
lwadurneww-laptop,6G,21639,62,21862,12,12944,8,31381,78,33165,11,95.6,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

It does indeed appear fairly slow, though I don't quite know how to remedy it.  Might I also add that while Bonnie was running, the rest of my system essentially locked up.  For instance, Firefox froze, and it took 20-30 seconds even to open a new terminal.

---

### Post by 00arthuryu on 2009-08-31
My guess is you're using your SWAP partition instead of your RAM?
if you open gnome-system-monitor and look at the swap and RAM usage.
In which case, delete the SWAP partition since you have about 4GB RAM

---

### Post by lwadurnew on 2009-08-31
Arthury:  Appreciate the response.  System monitor suggests that 0 of my swap is being used/has been used.

---

### Post by P4man on 2009-08-31
hmm.. your throughput seems rather normal (its a laptop after all and you ran other stuff at the same time)
What is less normal is that I/O would hang your system like that. When I run it, I do notice it, things slow down, and it has trouble even keeping up with my typing, but I can still surf and launch apps.

Can you run iotop and check if something is hammering your disk all the time?  Also post your dmesg perhaps, maybe we can see something in there that gives a clue.

---

### Post by lwadurnew on 2009-08-31
iotop isn't raising any alarms.  It's essentially all 0's except for the occasional Firefox i/o or kjournald i/o.  I'm not really sure what DMA is, but I know lack of it can really impact performance.  Could that be at play here?  Here's my dmesg output:

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
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe70000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe70000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe70 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe70000 (usable)
[    0.000000]  modified: 00000000bfe70000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  modified: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bb000 - 37fefafe
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb1afe
[    0.000000] Move RAMDISK from 00000000378bb000 - 0000000037fefafd to 0087d000 - 00fb1afd
[    0.000000] ACPI: RSDP 000F7D20, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT BFE7DE9A, 0044 (r1 HP     30BC      6040000  LTP        0)
[    0.000000] ACPI: FACP BFE85DEE, 0074 (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: DSDT BFE7EABC, 7332 (r1 HP     30BC      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS BFE86FC0, 0040
[    0.000000] ACPI: APIC BFE85E62, 0068 (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: HPET BFE85ECA, 0038 (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BFE85F02, 003C (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: BOOT BFE85FD8, 0028 (r1 HP     30BC      6040000  LTP        1)
[    0.000000] ACPI: APIC BFE85F70, 0068 (r1 HP     30BC      6040000  LTP        0)
[    0.000000] ACPI: SSDT BFE7E8AE, 020A (r1  HP    30BC         1000 INTL 20050624)
[    0.000000] ACPI: SSDT BFE7DEDE, 04F6 (r1 HP     30BC         3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2186MB HIGHMEM available.
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
[    0.000000]   #7 [000087d000 - 0000fb1afe]      NEW RAMDISK ==> [000087d000 - 0000fb1afe]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f7dd0] 000f7dd0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bfe70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000bfe70
[    0.000000] On node 0 totalpages: 785909
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4373 pages used for memmap
[    0.000000]   HighMem zone: 555357 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779768
[    0.000000] Kernel command line: root=UUID=8f58f0ce-7eea-4672-81fe-04f7eb446364 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.218 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15720640 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3086748k/3144128k available (4115k kernel code, 55960k reserved, 2199k data, 532k init, 2238920k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.43 BogoMIPS (lpj=6384872)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018913] ACPI: Core revision 20080926
[    0.021924] ACPI: Checking initramfs for custom DSDT
[    0.392506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.435184] CPU0: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz stepping 06
[    0.436001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3192.94 BogoMIPS (lpj=6385892)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.520544] CPU1: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz stepping 06
[    0.520563] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524047] Brought up 2 CPUs
[    0.524050] Total of 2 processors activated (6385.38 BogoMIPS).
[    0.524110] CPU0 attaching sched-domain:
[    0.524114]  domain 0: span 0-1 level MC
[    0.524117]   groups: 0 1
[    0.524124] CPU1 attaching sched-domain:
[    0.524127]  domain 0: span 0-1 level MC
[    0.524130]   groups: 1 0
[    0.524213] net_namespace: 776 bytes
[    0.524213] Booting paravirtualized kernel on bare hardware
[    0.524396] Time: 15:00:40  Date: 08/31/09
[    0.524396] regulator: core version 0.5
[    0.524396] NET: Registered protocol family 16
[    0.524396] EISA bus registered
[    0.524396] ACPI: bus type pci registered
[    0.524396] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.524396] PCI: MCFG area at e0000000 reserved in E820
[    0.524396] PCI: Using MMCONFIG for extended config space
[    0.524396] PCI: Using configuration type 1 for base access
[    0.525400] ACPI: EC: Look up EC in DSDT
[    0.531231] ACPI: BIOS _OSI(Linux) query ignored
[    0.532012] ACPI: Interpreter enabled
[    0.532019] ACPI: (supports S0 S3 S4 S5)
[    0.532041] ACPI: Using IOAPIC for interrupt routing
[    0.532464] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.544631] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.544634] ACPI: EC: driver started in interrupt mode
[    0.544805] ACPI: No dock devices found.
[    0.544823] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.544946] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.544951] pci 0000:00:01.0: PME# disabled
[    0.545055] pci 0000:00:1b.0: reg 10 64bit mmio: [0xde300000-0xde303fff]
[    0.545102] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.545108] pci 0000:00:1b.0: PME# disabled
[    0.545184] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.545189] pci 0000:00:1c.0: PME# disabled
[    0.545268] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.545274] pci 0000:00:1c.1: PME# disabled
[    0.545354] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.545359] pci 0000:00:1c.2: PME# disabled
[    0.545435] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.545506] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.545576] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.545647] pci 0000:00:1d.3: reg 20 io port: [0x1860-0x187f]
[    0.545723] pci 0000:00:1d.7: reg 10 32bit mmio: [0xde304000-0xde3043ff]
[    0.545776] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.545783] pci 0000:00:1d.7: PME# disabled
[    0.545960] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.545965] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.546006] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.546015] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.546025] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.546034] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.546043] pci 0000:00:1f.1: reg 20 io port: [0x1880-0x188f]
[    0.546114] pci 0000:00:1f.2: reg 10 io port: [0x18c8-0x18cf]
[    0.546123] pci 0000:00:1f.2: reg 14 io port: [0x18ac-0x18af]
[    0.546132] pci 0000:00:1f.2: reg 18 io port: [0x18c0-0x18c7]
[    0.546142] pci 0000:00:1f.2: reg 1c io port: [0x18a8-0x18ab]
[    0.546151] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.546160] pci 0000:00:1f.2: reg 24 32bit mmio: [0xde304400-0xde3047ff]
[    0.546184] pci 0000:00:1f.2: PME# supported from D3hot
[    0.546190] pci 0000:00:1f.2: PME# disabled
[    0.546262] pci 0000:00:1f.3: reg 20 io port: [0x18e0-0x18ff]
[    0.546333] pci 0000:01:00.0: reg 10 32bit mmio: [0xdd000000-0xddffffff]
[    0.546344] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.546356] pci 0000:01:00.0: reg 1c 64bit mmio: [0xdc000000-0xdcffffff]
[    0.546368] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.546445] pci 0000:00:01.0: bridge 32bit mmio: [0xdc000000-0xddffffff]
[    0.546452] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.546643] pci 0000:02:00.0: reg 10 32bit mmio: [0xd8000000-0xd8000fff]
[    0.546814] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.546828] pci 0000:02:00.0: PME# disabled
[    0.546942] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.546948] pci 0000:00:1c.0: bridge 32bit mmio: [0xd8000000-0xd9ffffff]
[    0.546957] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd2000000-0xd3ffffff]
[    0.547027] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.547033] pci 0000:00:1c.1: bridge 32bit mmio: [0xd6000000-0xd7ffffff]
[    0.547042] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xd0000000-0xd1ffffff]
[    0.547131] pci 0000:05:00.0: reg 10 32bit mmio: [0xda000000-0xda01ffff]
[    0.547158] pci 0000:05:00.0: reg 18 io port: [0x4000-0x401f]
[    0.547228] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.547236] pci 0000:05:00.0: PME# disabled
[    0.547325] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.547331] pci 0000:00:1c.2: bridge 32bit mmio: [0xda000000-0xdbffffff]
[    0.547341] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xd4000000-0xd5ffffff]
[    0.547401] pci 0000:07:05.0: reg 10 32bit mmio: [0xde000000-0xde0007ff]
[    0.547456] pci 0000:07:05.0: supports D1 D2
[    0.547459] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.547464] pci 0000:07:05.0: PME# disabled
[    0.547514] pci 0000:07:05.1: reg 10 32bit mmio: [0xde000800-0xde0008ff]
[    0.548038] pci 0000:07:05.1: supports D1 D2
[    0.548040] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.548046] pci 0000:07:05.1: PME# disabled
[    0.548094] pci 0000:07:05.2: reg 10 32bit mmio: [0xde000c00-0xde000cff]
[    0.548149] pci 0000:07:05.2: supports D1 D2
[    0.548152] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.548158] pci 0000:07:05.2: PME# disabled
[    0.548207] pci 0000:07:05.3: reg 10 32bit mmio: [0xde001000-0xde0010ff]
[    0.548261] pci 0000:07:05.3: supports D1 D2
[    0.548264] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.548270] pci 0000:07:05.3: PME# disabled
[    0.548318] pci 0000:07:05.4: reg 10 32bit mmio: [0xde001400-0xde0014ff]
[    0.548373] pci 0000:07:05.4: supports D1 D2
[    0.548375] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.548381] pci 0000:07:05.4: PME# disabled
[    0.548451] pci 0000:00:1e.0: transparent bridge
[    0.548461] pci 0000:00:1e.0: bridge 32bit mmio: [0xde000000-0xde0fffff]
[    0.548502] bus 00 -> node 0
[    0.548510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.548932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.549105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.549269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.549428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.549604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.556599] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.556759] ACPI: PCI Interrupt Link [LNKB] (IRQs *3)
[    0.556918] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[    0.557078] ACPI: PCI Interrupt Link [LNKD] (IRQs *4)
[    0.557236] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.557392] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[    0.557551] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    0.557708] ACPI: PCI Interrupt Link [LNKH] (IRQs *7)
[    0.558049] ACPI: WMI: Mapper loaded
[    0.558093] SCSI subsystem initialized
[    0.558093] libata version 3.00 loaded.
[    0.558093] usbcore: registered new interface driver usbfs
[    0.558093] usbcore: registered new interface driver hub
[    0.558093] usbcore: registered new device driver usb
[    0.558093] PCI: Using ACPI for IRQ routing
[    0.564012] Bluetooth: Core ver 2.13
[    0.564029] NET: Registered protocol family 31
[    0.564029] Bluetooth: HCI device and connection manager initialized
[    0.564029] Bluetooth: HCI socket layer initialized
[    0.564029] NET: Registered protocol family 8
[    0.564029] NET: Registered protocol family 20
[    0.564042] NetLabel: Initializing
[    0.564044] NetLabel:  domain hash size = 128
[    0.564046] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564062] NetLabel:  unlabeled traffic allowed by default
[    0.564080] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.564086] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.568072] AppArmor: AppArmor Filesystem Enabled
[    0.572014] Switched to high resolution mode on CPU 0
[    0.572605] Switched to high resolution mode on CPU 1
[    0.576014] pnp: PnP ACPI init
[    0.576024] ACPI: bus type pnp registered
[    0.580202] pnp: PnP ACPI: found 10 devices
[    0.580205] ACPI: ACPI bus type pnp unregistered
[    0.580209] PnPBIOS: Disabled by ACPI PNP
[    0.580223] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.580226] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.580230] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.580233] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.580237] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.580240] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.580244] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.580247] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.580255] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.580263] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.580267] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.580270] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.580273] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.580276] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.580279] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.580286] system 00:06: ioport range 0x6a0-0x6af has been reserved
[    0.580289] system 00:06: ioport range 0x6b0-0x6ff has been reserved
[    0.615055] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    0.615059] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.615061] pci 0000:00:01.0:   IO window: disabled
[    0.615067] pci 0000:00:01.0:   MEM window: 0xdc000000-0xddffffff
[    0.615071] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.615077] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.615082] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.615089] pci 0000:00:1c.0:   MEM window: 0xd8000000-0xd9ffffff
[    0.615095] pci 0000:00:1c.0:   PREFETCH window: 0x000000d2000000-0x000000d3ffffff
[    0.615104] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.615108] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.615116] pci 0000:00:1c.1:   MEM window: 0xd6000000-0xd7ffffff
[    0.615121] pci 0000:00:1c.1:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.615131] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.615135] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.615142] pci 0000:00:1c.2:   MEM window: 0xda000000-0xdbffffff
[    0.615148] pci 0000:00:1c.2:   PREFETCH window: 0x000000d4000000-0x000000d5ffffff
[    0.615158] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.615160] pci 0000:00:1e.0:   IO window: disabled
[    0.615168] pci 0000:00:1e.0:   MEM window: 0xde000000-0xde0fffff
[    0.615174] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.615191] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.615196] pci 0000:00:01.0: setting latency timer to 64
[    0.615207] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.615213] pci 0000:00:1c.0: setting latency timer to 64
[    0.615223] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.615229] pci 0000:00:1c.1: setting latency timer to 64
[    0.615241] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.615247] pci 0000:00:1c.2: setting latency timer to 64
[    0.615253] pci 0000:00:1e.0: enabling device (0004 -> 0006)
[    0.615261] pci 0000:00:1e.0: setting latency timer to 64
[    0.615266] bus: 00 index 0 io port: [0x00-0xffff]
[    0.615268] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.615271] bus: 01 index 0 mmio: [0x0-0x0]
[    0.615273] bus: 01 index 1 mmio: [0xdc000000-0xddffffff]
[    0.615276] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.615278] bus: 01 index 3 mmio: [0x0-0x0]
[    0.615281] bus: 02 index 0 io port: [0x2000-0x2fff]
[    0.615283] bus: 02 index 1 mmio: [0xd8000000-0xd9ffffff]
[    0.615286] bus: 02 index 2 mmio: [0xd2000000-0xd3ffffff]
[    0.615288] bus: 02 index 3 mmio: [0x0-0x0]
[    0.615291] bus: 03 index 0 io port: [0x3000-0x3fff]
[    0.615293] bus: 03 index 1 mmio: [0xd6000000-0xd7ffffff]
[    0.615296] bus: 03 index 2 mmio: [0xd0000000-0xd1ffffff]
[    0.615298] bus: 03 index 3 mmio: [0x0-0x0]
[    0.615301] bus: 05 index 0 io port: [0x4000-0x4fff]
[    0.615304] bus: 05 index 1 mmio: [0xda000000-0xdbffffff]
[    0.615306] bus: 05 index 2 mmio: [0xd4000000-0xd5ffffff]
[    0.615309] bus: 05 index 3 mmio: [0x0-0x0]
[    0.615311] bus: 07 index 0 mmio: [0x0-0x0]
[    0.615313] bus: 07 index 1 mmio: [0xde000000-0xde0fffff]
[    0.615316] bus: 07 index 2 mmio: [0x0-0x0]
[    0.615318] bus: 07 index 3 io port: [0x00-0xffff]
[    0.615321] bus: 07 index 4 mmio: [0x000000-0xffffffff]
[    0.615330] NET: Registered protocol family 2
[    0.628061] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.628347] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.628782] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.629017] TCP: Hash tables configured (established 131072 bind 65536)
[    0.629020] TCP reno registered
[    0.636085] NET: Registered protocol family 1
[    0.636227] checking if image is initramfs... it is
[    1.390759] Freeing initrd memory: 7378k freed
[    1.390806] Simple Boot Flag at 0x35 set to 0x1
[    1.391056] cpufreq: No nForce2 chipset.
[    1.391228] audit: initializing netlink socket (disabled)
[    1.391258] type=2000 audit(1251730840.389:1): initialized
[    1.400195] highmem bounce pool size: 64 pages
[    1.400201] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.401855] VFS: Disk quotas dquot_6.5.1
[    1.401927] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.402676] fuse init (API version 7.10)
[    1.402777] msgmni has been set to 1672
[    1.403001] alg: No test for stdrng (krng)
[    1.403017] io scheduler noop registered
[    1.403020] io scheduler anticipatory registered
[    1.403023] io scheduler deadline registered
[    1.403039] io scheduler cfq registered (default)
[    1.403176] pci 0000:01:00.0: Boot video device
[    1.408956] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.409012] pcieport-driver 0000:00:01.0: found MSI capability
[    1.409043] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.409056] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.409074] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.409137] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.409193] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.409231] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.409249] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.409265] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.409280] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.409365] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.409420] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.409458] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.409476] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.409492] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.409510] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.409595] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.409650] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.409688] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.409706] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.409722] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.409737] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.409836] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.409944] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.410724] ACPI: AC Adapter [ACAD] (off-line)
[    1.487317] ACPI: Battery Slot [BAT0] (battery present)
[    1.487415] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.487418] ACPI: Power Button (FF) [PWRF]
[    1.487468] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.487471] ACPI: Power Button (CM) [PWRB]
[    1.487524] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.487527] ACPI: Sleep Button (CM) [SLPB]
[    1.487577] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.488340] ACPI: Lid Switch [LID]
[    1.489030] ACPI: SSDT BFE7E635, 01E5 (r1 HP     30BC         3000 INTL 20050624)
[    1.489454] ACPI: SSDT BFE7E3D4, 01DC (r1 HP     30BC         3001 INTL 20050624)
[    1.489978] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.490008] processor ACPI_CPU:00: registered as cooling_device0
[    1.490013] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.490467] ACPI: SSDT BFE7E81A, 0094 (r1 HP     30BC         3000 INTL 20050624)
[    1.490899] ACPI: SSDT BFE7E5B0, 0085 (r1 HP     30BC         3000 INTL 20050624)
[    1.491430] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.491454] processor ACPI_CPU:01: registered as cooling_device1
[    1.491459] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.506096] thermal LNXTHERM:01: registered as thermal_zone0
[    1.515486] ACPI: Thermal Zone [THR1] (1 C)
[    1.515554] isapnp: Scanning for PnP cards...
[    1.869562] isapnp: No Plug & Play device found
[    1.881274] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.882531] brd: module loaded
[    1.882897] loop: module loaded
[    1.882979] Fixed MDIO Bus: probed
[    1.882985] PPP generic driver version 2.4.2
[    1.883059] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.883093] Driver 'sd' needs updating - please use bus_type methods
[    1.883104] Driver 'sr' needs updating - please use bus_type methods
[    1.883149] ahci 0000:00:1f.2: version 3.0
[    1.883167] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.883215] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.883301] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.883306] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.883312] ahci 0000:00:1f.2: setting latency timer to 64
[    1.883529] scsi0 : ahci
[    1.883641] scsi1 : ahci
[    1.883717] scsi2 : ahci
[    1.883792] scsi3 : ahci
[    1.883903] ata1: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304500 irq 2299
[    1.883906] ata2: DUMMY
[    1.883909] ata3: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304600 irq 2299
[    1.883911] ata4: DUMMY
[    2.200026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.200610] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.200616] ata1.00: ATA-7: FUJITSU MHV2080BH PL, 892C, max UDMA/100
[    2.200619] ata1.00: 156301488 sectors, multi 16: LBA48 
[    2.203216] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.203251] ata1.00: configured for UDMA/100
[    2.536023] ata3: SATA link down (SStatus 0 SControl 300)
[    2.552140] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 892C PQ: 0 ANSI: 5
[    2.552249] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.552269] sd 0:0:0:0: [sda] Write Protect is off
[    2.552272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.552303] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.552378] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.552395] sd 0:0:0:0: [sda] Write Protect is off
[    2.552398] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.552429] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.552433]  sda: sda1 sda2 < sda5 sda6 >
[    2.607871] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.607924] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.607984] ata_piix 0000:00:1f.1: version 2.12
[    2.607992] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.608042] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.608127] scsi4 : ata_piix
[    2.608208] scsi5 : ata_piix
[    2.608830] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    2.608833] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    2.772508] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PC05, max MWDMA2
[    2.788442] ata5.00: configured for MWDMA2
[    2.790787] ata6: port disabled. ignoring.
[    2.794124] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PC05 PQ: 0 ANSI: 5
[    2.805874] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.805878] Uniform CD-ROM driver Revision: 3.20
[    2.805985] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.806033] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.806855] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.806879] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.806895] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.806900] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.806972] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.810891] ehci_hcd 0000:00:1d.7: debug port 1
[    2.810899] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.810914] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xde304000
[    2.824013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.824107] usb usb1: configuration #1 chosen from 1 choice
[    2.824140] hub 1-0:1.0: USB hub found
[    2.824152] hub 1-0:1.0: 8 ports detected
[    2.824288] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.824308] uhci_hcd: USB Universal Host Controller Interface driver
[    2.824333] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.824340] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.824344] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.824395] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.824424] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    2.824508] usb usb2: configuration #1 chosen from 1 choice
[    2.824541] hub 2-0:1.0: USB hub found
[    2.824549] hub 2-0:1.0: 2 ports detected
[    2.824645] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.824653] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.824657] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.824705] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.824741] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    2.824830] usb usb3: configuration #1 chosen from 1 choice
[    2.824860] hub 3-0:1.0: USB hub found
[    2.824871] hub 3-0:1.0: 2 ports detected
[    2.824968] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.824975] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.824979] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.825032] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.825069] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    2.825156] usb usb4: configuration #1 chosen from 1 choice
[    2.825186] hub 4-0:1.0: USB hub found
[    2.825194] hub 4-0:1.0: 2 ports detected
[    2.825297] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.825304] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.825308] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.825357] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.825394] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.825479] usb usb5: configuration #1 chosen from 1 choice
[    2.825512] hub 5-0:1.0: USB hub found
[    2.825520] hub 5-0:1.0: 2 ports detected
[    2.825689] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.842581] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.842588] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.844047] mice: PS/2 mouse device common for all mice
[    2.864090] rtc_cmos 00:07: RTC can wake from S4
[    2.864130] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.864164] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.864232] device-mapper: uevent: version 1.0.3
[    2.864332] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.864432] device-mapper: multipath: version 1.0.5 loaded
[    2.864435] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.864528] EISA: Probing bus 0 at eisa.0
[    2.864536] Cannot allocate resource for EISA slot 1
[    2.864539] Cannot allocate resource for EISA slot 2
[    2.864542] Cannot allocate resource for EISA slot 3
[    2.864544] Cannot allocate resource for EISA slot 4
[    2.864565] EISA: Detected 0 cards.
[    2.864710] cpuidle: using governor ladder
[    2.864854] cpuidle: using governor menu
[    2.865464] TCP cubic registered
[    2.865576] NET: Registered protocol family 10
[    2.866081] lo: Disabled Privacy Extensions
[    2.866485] NET: Registered protocol family 17
[    2.866507] Bluetooth: L2CAP ver 2.11
[    2.866509] Bluetooth: L2CAP socket layer initialized
[    2.866513] Bluetooth: SCO (Voice Link) ver 0.6
[    2.866515] Bluetooth: SCO socket layer initialized
[    2.866559] Bluetooth: RFCOMM socket layer initialized
[    2.866567] Marking TSC unstable due to TSC halts in idle
[    2.866573] Bluetooth: RFCOMM TTY layer initialized
[    2.866577] Bluetooth: RFCOMM ver 1.10
[    2.867044] Using IPI No-Shortcut mode
[    2.867123] registered taskstats version 1
[    2.867264]   Magic number: 5:893:33
[    2.867359] rtc_cmos 00:07: setting system clock to 2009-08-31 15:00:43 UTC (1251730843)
[    2.867363] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.867365] EDD information not available.
[    2.867694] Freeing unused kernel memory: 532k freed
[    2.867881] Write protecting the kernel text: 4116k
[    2.867952] Write protecting the kernel read-only data: 1528k
[    2.889130] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.130388] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    3.130392] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.130475] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.130489] e1000e 0000:05:00.0: setting latency timer to 64
[    3.130727] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[    3.141192] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    3.199066] ohci1394 0000:07:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.199077] ohci1394 0000:07:05.0: setting latency timer to 64
[    3.249058] 0000:05:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:36:b7:65:03
[    3.249061] 0000:05:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.249138] 0000:05:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    3.250848] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.341720] usb 1-4: configuration #1 chosen from 1 choice
[    3.547990] PM: Starting manual resume from disk
[    3.547994] PM: Resume from partition 8:6
[    3.547996] PM: Checking hibernation image.
[    3.548214] PM: Resume from disk failed.
[    3.598568] kjournald starting.  Commit interval 5 seconds
[    3.598615] EXT3-fs: mounted filesystem with ordered data mode.
[    4.532286] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0007155ce00]
[    9.691026] udev: starting version 141
[   10.601061] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   10.623868] Linux video capture interface: v2.00
[   10.644663] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input7
[   10.652792] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.664611] Linux agpgart interface v0.103
[   10.697837] intel_rng: FWH not detected
[   10.714455] cfg80211: Calling CRDA to update world regulatory domain
[   10.795887] cfg80211: World regulatory domain updated:
[   10.795891] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.795894] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.795897] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.795900] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.795903] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.795905] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.814708] sdhci: Secure Digital Host Controller Interface driver
[   10.814711] sdhci: Copyright(c) Pierre Ossman
[   10.816476] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   10.816491] sdhci-pci 0000:07:05.1: enabling device (0000 -> 0002)
[   10.816499] sdhci-pci 0000:07:05.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.818621] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   10.848625] ricoh-mmc: Ricoh MMC Controller disabling driver
[   10.848628] ricoh-mmc: Copyright(c) Philip Langdale
[   10.848657] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   10.848676] ricoh-mmc: Controller is now disabled.
[   10.982106] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.277453] nvidia: module license 'NVIDIA' taints kernel.
[   11.308790] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   11.317700] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input8
[   11.532740] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   11.532752] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.532761] nvidia 0000:01:00.0: setting latency timer to 64
[   11.533946] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   11.535513] usbcore: registered new interface driver uvcvideo
[   11.535543] USB Video Class driver (v0.1.0)
[   11.542946] iTCO_vendor_support: vendor-support=0
[   11.566699] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   11.566703] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   11.566823] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.566838] iwl3945 0000:02:00.0: setting latency timer to 64
[   11.566897] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   11.567989] iwl3945 0000:02:00.0: irq 2297 for MSI/MSI-X
[   11.569358] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.569518] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   11.569632] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.609689] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   11.614884] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   11.799401] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.799501] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.972373] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   12.034985] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   12.095000] lp: driver loaded but no devices found
[   12.181954] Adding 5887780k swap on /dev/sda6.  Priority:-1 extents:1 across:5887780k
[   12.202906] EXT3 FS on sda1, internal journal
[   12.572088] kjournald starting.  Commit interval 5 seconds
[   12.572523] EXT3 FS on sda5, internal journal
[   12.572534] EXT3-fs: mounted filesystem with ordered data mode.
[   12.904068] type=1505 audit(1251730853.533:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2029
[   12.959403] type=1505 audit(1251730853.589:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2033
[   12.959528] type=1505 audit(1251730853.589:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2033
[   12.959582] type=1505 audit(1251730853.589:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2033
[   12.959625] type=1505 audit(1251730853.589:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2033
[   13.113042] type=1505 audit(1251730853.744:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2038
[   13.113254] type=1505 audit(1251730853.744:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2038
[   13.159833] type=1505 audit(1251730853.789:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2042
[   13.191444] type=1505 audit(1251730853.821:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2046
[   18.125160] ppdev: user-space parallel port driver
[   21.401336] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[   21.457137] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[   21.458459] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.459715] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   22.663035] Registered led device: iwl-phy0:radio
[   22.663058] Registered led device: iwl-phy0:assoc
[   22.663115] Registered led device: iwl-phy0:RX
[   22.663134] Registered led device: iwl-phy0:TX
[   22.669777] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6204.829397] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

---

### Post by P4man on 2009-08-31
> **lwadurnew said:**
> iotop isn't raising any alarms.  It's essentially all 0's except for the occasional Firefox i/o or kjournald i/o.  I'm not really sure what DMA is, but I know lack of it can really impact performance.  Could that be at play here? 

AFAICT from that log, u(dma) is enabled as it should be. If you got a harddisk that for some reason is not using dma (direct memory access) but PIO, then the performance impact is not big, its monumental. Its simply unusable, its not what you're having.

I cant see anything wrong in that log, other than the last line, but i doubt thats a clue to help solve your stuttering.. although, perhaps, can you post the output of ```
cat /proc/interrupts
``` ?

---

### Post by lwadurnew on 2009-08-31
Output of /proc/interrupts:

           CPU0       CPU1       
  0:    2436455          0   IO-APIC-edge      timer
  1:      27838          0   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:     131080          4   IO-APIC-fasteoi   acpi
 12:    1426493          1   IO-APIC-edge      i8042
 14:     121274          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:     105033          0   IO-APIC-fasteoi   uhci_hcd:usb5, ohci1394, nvidia
 17:          0          0   IO-APIC-fasteoi   mmc0
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:      51066          0   IO-APIC-fasteoi   HDA Intel
 23:         19          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
2297:     370323          0   PCI-MSI-edge      iwl3945
2298:       6071          0   PCI-MSI-edge      eth0
2299:     335797          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     651623    1660673   Local timer interrupts
RES:     349912     540849   Rescheduling interrupts
CAL:         67       1191   Function call interrupts
TLB:       3515       4018   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

---

### Post by lwadurnew on 2009-08-31
I'd like to also add that during the Bonnie HD benchmark, one of the cores constantly sits 100% usage.  Is this normal?

---

### Post by P4man on 2009-09-01
Yeah its close to 100% on one core for me as well, at least during the sequential tests. So for nothing looks really wrong, your harddisk is slow though, but Im not sure that alone explains it.

Are you running visual effects ?  What videocard and drivers do you have?

---

