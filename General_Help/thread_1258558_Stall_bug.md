---
title: "Stall bug"
date: 2009-09-05
forum: General Help
---

### Post by superstalker on 2009-09-05
Hi all,

I've got a mayor irritating bug:

Everytime I'm installing something, or starting up Ubuntu, or do an action what takes some time for Ubuntu, it stalls after a few minutes (or seconds) untill I move my mouse, or hit a key. And repeats it all over again untill it's finished with the action.

This is extremely irritating, when I'm using the partitioning program which takes a heck of a long time without the bug. Or when I'm just reinstalling Ubuntu, when Windows messes up my Grub loader again. And I want to get rid of it asap.

I'm using Ubuntu 9.04 on a Fujitsu Siemens Amilo XI 2528 Laptop.
And every driver has been installed.


Thank you in advance

---

### Post by Liolikas on 2009-09-05
>when Windows messes up my Grub loader again
You can fix grub with install-grub command from live cd quickly.

And your main problem very strange... I saw something like that with heavy-customized Linux kernel you use stock kernel or maybe compiled your custom one?

---

### Post by superstalker on 2009-09-05
I'm pretty new when it comes to Ubuntu, and have it for a week now.
I've done nothing, as far as I know, to change the kernel.

But when I installed openSUSE, bout 6 months ago, I also got this bug. Eventually I deleted it, because I couldn't connect it to the Windows based Wireless Network at school.

Unless Windows XP, Vista, or 7 can change the kernel, the answer is no.

---

### Post by Liolikas on 2009-09-05
show otput of dmesg after you wait few times like this.

---

### Post by superstalker on 2009-09-05
How? Again, I'm a newb :)
And there is no error msg. It just freezes, untill I move my mouse.

---

### Post by Liolikas on 2009-09-05
Start up terminal from menu.
And type:
```

dmesg

```
So it shows tons of generally boring and even unimportant errors (like hei internet is working). But we may se something interesting post it here.

---

### Post by superstalker on 2009-09-05
**dmesg.txt**:
		Your file of 47.7 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.

---

### Post by Liolikas on 2009-09-05
pastebin.com etc.

---

### Post by superstalker on 2009-09-05
[ 0.000000] BIOS EBDA/lowmem at: 0009b800/0009b800

[ 0.000000] Initializing cgroup subsys cpuset

[ 0.000000] Initializing cgroup subsys cpu

[ 0.000000] Linux version 2.6.28-15-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 (Ubuntu 2.6.28-15.49-generic)

[ 0.000000] Command line: root=UUID=a500ecc3-6299-41f7-8f1c-8d7a7959a659 ro quiet splash

[ 0.000000] KERNEL supported cpus:

[ 0.000000] Intel GenuineIntel

[ 0.000000] AMD AuthenticAMD

[ 0.000000] Centaur CentaurHauls

[ 0.000000] BIOS-provided physical RAM map:

[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009b800 (usable)

[ 0.000000] BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)

[ 0.000000] BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

[ 0.000000] BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)

[ 0.000000] BIOS-e820: 00000000bfed0000 - 00000000bfedc000 (ACPI NVS)

[ 0.000000] BIOS-e820: 00000000bfedc000 - 00000000c0000000 (reserved)

[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)

[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)

[ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)

[ 0.000000] BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)

[ 0.000000] BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)

[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)

[ 0.000000] BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)

[ 0.000000] DMI present.

[ 0.000000] last_pfn = 0xbfed0 max_arch_pfn = 0x3ffffffff

[ 0.000000] Scanning 2 areas for low memory corruption

[ 0.000000] modified physical RAM map:

[ 0.000000] modified: 0000000000000000 - 0000000000001000 (usable)

[ 0.000000] modified: 0000000000001000 - 0000000000006000 (reserved)

[ 0.000000] modified: 0000000000006000 - 0000000000008000 (usable)

[ 0.000000] modified: 0000000000008000 - 0000000000010000 (reserved)

[ 0.000000] modified: 0000000000010000 - 000000000008e800 (usable)

[ 0.000000] modified: 000000000009b800 - 00000000000a0000 (reserved)

[ 0.000000] modified: 00000000000e0000 - 0000000000100000 (reserved)

[ 0.000000] modified: 0000000000100000 - 00000000bfed0000 (usable)

[ 0.000000] modified: 00000000bfed0000 - 00000000bfedc000 (ACPI NVS)

[ 0.000000] modified: 00000000bfedc000 - 00000000c0000000 (reserved)

[ 0.000000] modified: 00000000e0000000 - 00000000f0000000 (reserved)

[ 0.000000] modified: 00000000fec00000 - 00000000fec10000 (reserved)

[ 0.000000] modified: 00000000fed00000 - 00000000fed00400 (reserved)

[ 0.000000] modified: 00000000fed14000 - 00000000fed1a000 (reserved)

[ 0.000000] modified: 00000000fed1c000 - 00000000fed90000 (reserved)

[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)

[ 0.000000] modified: 00000000ff000000 - 0000000100000000 (reserved)

[ 0.000000] init_memory_mapping: 0000000000000000-00000000bfed0000

[ 0.000000] 0000000000 - 00bfe00000 page 2M

[ 0.000000] 00bfe00000 - 00bfed0000 page 4k

[ 0.000000] kernel direct mapping tables up to bfed0000 @ 10000-15000

[ 0.000000] last_map_addr: bfed0000 end: bfed0000

[ 0.000000] RAMDISK: 37858000 - 37fefe26

[ 0.000000] ACPI: RSDP 000F8000, 0024 (r2 PTLTD )

[ 0.000000] ACPI: XSDT BFED2518, 007C (r1 FSC PC 6040000 LTP 0)

[ 0.000000] ACPI: FACP BFED8C6C, 00F4 (r3 INTEL CRESTLNE 6040000 ALAN 1)

[ 0.000000] ACPI: DSDT BFED3AE1, 5117 (r2 ECS F41 6040000 INTL 20050624)

[ 0.000000] ACPI: FACS BFEDBFC0, 0040

[ 0.000000] ACPI: HPET BFED8D60, 0038 (r1 INTEL CRESTLNE 6040000 LOHR 5A)

[ 0.000000] ACPI: MCFG BFED8D98, 003C (r1 INTEL CRESTLNE 6040000 LOHR 5A)

[ 0.000000] ACPI: TMOR BFED8DD4, 0026 (r1 PTLTD 6040000 PTL 3)

[ 0.000000] ACPI: APIC BFED8DFA, 0068 (r1 PTLTD APIC 6040000 LTP 0)

[ 0.000000] ACPI: BOOT BFED8E62, 0028 (r1 PTLTD $SBFTBL$ 6040000 LTP 1)

[ 0.000000] ACPI: SLIC BFED8E8A, 0176 (r1 FSC PC 6040000 LTP 0)

[ 0.000000] ACPI: SSDT BFED3804, 02DD (r1 SataRe SataAhci 1000 INTL 20050624)

[ 0.000000] ACPI: SSDT BFED2B50, 025F (r1 PmRef Cpu0Tst 3000 INTL 20050624)

[ 0.000000] ACPI: SSDT BFED2AAA, 00A6 (r1 PmRef Cpu1Tst 3000 INTL 20050624)

[ 0.000000] ACPI: SSDT BFED2594, 0516 (r1 PmRef CpuPm 3000 INTL 20050624)

[ 0.000000] ACPI: Local APIC address 0xfee00000

[ 0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bfed0000]

[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]

[ 0.000000] #1 [0000006000 - 0000008000] TRAMPOLINE ==> [0000006000 - 0000008000]

[ 0.000000] #2 [0000200000 - 0000b7bbb0] TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]

[ 0.000000] #3 [0037858000 - 0037fefe26] RAMDISK ==> [0037858000 - 0037fefe26]

[ 0.000000] #4 [000009b800 - 0000100000] BIOS reserved ==> [000009b800 - 0000100000]

[ 0.000000] #5 [0000010000 - 0000013000] PGTABLE ==> [0000010000 - 0000013000]

[ 0.000000] found SMP MP-table at [ffff8800000f8030] 000f8030

[ 0.000000] [ffffe20000000000-ffffe200029fffff] PMD -> [ffff880001200000-ffff880003bfffff] on node 0

[ 0.000000] Zone PFN ranges:

[ 0.000000] DMA 0x00000000 -> 0x00001000

[ 0.000000] DMA32 0x00001000 -> 0x00100000

[ 0.000000] Normal 0x00100000 -> 0x00100000

[ 0.000000] Movable zone start PFN for each node

[ 0.000000] early_node_map[4] active PFN ranges

[ 0.000000] 0: 0x00000000 -> 0x00000001

[ 0.000000] 0: 0x00000006 -> 0x00000008

[ 0.000000] 0: 0x00000010 -> 0x0000008e

[ 0.000000] 0: 0x00000100 -> 0x000bfed0

[ 0.000000] On node 0 totalpages: 786001

[ 0.000000] DMA zone: 56 pages used for memmap

[ 0.000000] DMA zone: 2535 pages reserved

[ 0.000000] DMA zone: 1378 pages, LIFO batch:0

[ 0.000000] DMA32 zone: 10692 pages used for memmap

[ 0.000000] DMA32 zone: 771340 pages, LIFO batch:31

[ 0.000000] Normal zone: 0 pages used for memmap

[ 0.000000] Movable zone: 0 pages used for memmap

[ 0.000000] ACPI: PM-Timer IO Port: 0x1008

[ 0.000000] ACPI: Local APIC address 0xfee00000

[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)

[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])

[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])

[ 0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23

[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)

[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

[ 0.000000] ACPI: IRQ0 used by override.

[ 0.000000] ACPI: IRQ2 used by override.

[ 0.000000] ACPI: IRQ9 used by override.

[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000

[ 0.000000] Using ACPI (MADT) for SMP configuration information

[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs

[ 0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000

[ 0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000

[ 0.000000] PM: Registered nosave memory: 000000000008e000 - 000000000009c000

[ 0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000

[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000

[ 0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000

[ 0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)

[ 0.000000] PERCPU: Allocating 69632 bytes of per cpu data

[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1

[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 772718

[ 0.000000] Kernel command line: root=UUID=a500ecc3-6299-41f7-8f1c-8d7a7959a659 ro quiet splash

[ 0.000000] Initializing CPU#0

[ 0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)

[ 0.000000] Extended CMOS year: 2000

[ 0.000000] Fast TSC calibration using PIT

[ 0.000000] Detected 2094.880 MHz processor.

[ 0.004000] Console: colour VGA+ 80x25

[ 0.004000] console [tty0] enabled

[ 0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)

[ 0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)

[ 0.004000] allocated 31457280 bytes of page_cgroup

[ 0.004000] please try cgroup_disable=memory option if you don't want

[ 0.004000] Scanning for low memory corruption every 60 seconds

[ 0.004000] Checking aperture...

[ 0.004000] No AGP bridge found

[ 0.004000] Calgary: detecting Calgary via BIOS EBDA area

[ 0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!

[ 0.004000] Memory: 3045612k/3144512k available (4749k kernel code, 508k absent, 97700k reserved, 2523k data, 532k init)

[ 0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1

[ 0.004000] hpet clockevent registered

[ 0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer

[ 0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.76 BogoMIPS (lpj=8379520)

[ 0.004000] Security Framework initialized

[ 0.004000] SELinux: Disabled at boot.

[ 0.004000] AppArmor: AppArmor initialized

[ 0.004000] Mount-cache hash table entries: 256

[ 0.004000] Initializing cgroup subsys ns

[ 0.004000] Initializing cgroup subsys cpuacct

[ 0.004000] Initializing cgroup subsys memory

[ 0.004000] Initializing cgroup subsys freezer

[ 0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K

[ 0.004000] CPU: L2 cache: 3072K

[ 0.004000] CPU: Physical Processor ID: 0

[ 0.004000] CPU: Processor Core ID: 0

[ 0.004000] using mwait in idle threads.

[ 0.004000] ACPI: Core revision 20080926

[ 0.004128] ACPI: Checking initramfs for custom DSDT

[ 0.296046] Setting APIC routing to flat

[ 0.296445] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1

[ 0.336888] CPU0: Intel(R) Core(TM)2 Duo CPU T8100 @ 2.10GHz stepping 06

[ 0.340001] Booting processor 1 APIC 0x1 ip 0x6000

[ 0.004000] Initializing CPU#1

[ 0.004000] Calibrating delay using timer specific routine.. 4189.46 BogoMIPS (lpj=8378929)

[ 0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K

[ 0.004000] CPU: L2 cache: 3072K

[ 0.004000] CPU: Physical Processor ID: 0

[ 0.004000] CPU: Processor Core ID: 1

[ 0.424569] CPU1: Intel(R) Core(TM)2 Duo CPU T8100 @ 2.10GHz stepping 06

[ 0.424591] checking TSC synchronization [CPU#0 -> CPU#1]: passed.

[ 0.428040] Brought up 2 CPUs

[ 0.428043] Total of 2 processors activated (8379.22 BogoMIPS).

[ 0.428089] CPU0 attaching sched-domain:

[ 0.428091] domain 0: span 0-1 level MC

[ 0.428093] groups: 0 1

[ 0.428098] CPU1 attaching sched-domain:

[ 0.428099] domain 0: span 0-1 level MC

[ 0.428101] groups: 1 0

[ 0.428164] net_namespace: 1400 bytes

[ 0.428164] Booting paravirtualized kernel on bare hardware

[ 0.428260] Time: 12:58:21 Date: 09/05/09

[ 0.428260] regulator: core version 0.5

[ 0.428260] NET: Registered protocol family 16

[ 0.428260] ACPI: bus type pci registered

[ 0.428260] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255

[ 0.428260] PCI: MCFG area at e0000000 reserved in E820

[ 0.439296] PCI: Using MMCONFIG at e0000000 - efffffff

[ 0.439297] PCI: Using configuration type 1 for base access

[ 0.440663] ACPI: EC: Look up EC in DSDT

[ 0.443072] ACPI: BIOS _OSI(Linux) query ignored

[ 0.460019] ACPI: EC: non-query interrupt received, switching to interrupt mode

[ 0.520051] ACPI: Interpreter enabled

[ 0.520054] ACPI: (supports S0 S3 S4 S5)

[ 0.520071] ACPI: Using IOAPIC for interrupt routing

[ 0.564305] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62

[ 0.564307] ACPI: EC: driver started in interrupt mode

[ 0.564461] ACPI: No dock devices found.

[ 0.564472] ACPI: PCI Root Bridge [PCI0] (0000:00)

[ 0.564555] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold

[ 0.564558] pci 0000:00:01.0: PME# disabled

[ 0.564644] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]

[ 0.564707] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]

[ 0.564777] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf0704800-0xf0704bff]

[ 0.564825] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold

[ 0.564830] pci 0000:00:1a.7: PME# disabled

[ 0.564883] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0700000-0xf0703fff]

[ 0.564923] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold

[ 0.564928] pci 0000:00:1b.0: PME# disabled

[ 0.564993] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold

[ 0.564997] pci 0000:00:1c.0: PME# disabled

[ 0.565066] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold

[ 0.565069] pci 0000:00:1c.1: PME# disabled

[ 0.565139] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold

[ 0.565143] pci 0000:00:1c.2: PME# disabled

[ 0.565211] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold

[ 0.565215] pci 0000:00:1c.3: PME# disabled

[ 0.565283] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold

[ 0.565288] pci 0000:00:1c.4: PME# disabled

[ 0.565350] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]

[ 0.565412] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]

[ 0.565474] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]

[ 0.565541] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf0704c00-0xf0704fff]

[ 0.565590] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold

[ 0.565595] pci 0000:00:1d.7: PME# disabled

[ 0.565747] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO

[ 0.565751] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO

[ 0.565786] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]

[ 0.565794] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]

[ 0.565801] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]

[ 0.565809] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]

[ 0.565816] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]

[ 0.565888] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]

[ 0.565896] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]

[ 0.565903] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]

[ 0.565910] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]

[ 0.565917] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]

[ 0.565924] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf0704000-0xf07047ff]

[ 0.565944] pci 0000:00:1f.2: PME# supported from D3hot

[ 0.565948] pci 0000:00:1f.2: PME# disabled

[ 0.565980] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]

[ 0.566005] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]

[ 0.566079] pci 0000:01:00.0: reg 10 32bit mmio: [0xce000000-0xceffffff]

[ 0.566094] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]

[ 0.566109] pci 0000:01:00.0: reg 1c 64bit mmio: [0xcc000000-0xcdffffff]

[ 0.566118] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]

[ 0.566127] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]

[ 0.566205] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]

[ 0.566208] pci 0000:00:01.0: bridge 32bit mmio: [0xcc000000-0xceffffff]

[ 0.566212] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]

[ 0.566272] pci 0000:00:1c.0: bridge io port: [0xf000-0xffff]

[ 0.566276] pci 0000:00:1c.0: bridge 32bit mmio: [0xfb000000-0xfcffffff]

[ 0.566345] pci 0000:04:00.0: reg 10 32bit mmio: [0xf0300000-0xf03003ff]

[ 0.566364] pci 0000:04:00.0: reg 18 io port: [0x3000-0x307f]

[ 0.566401] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]

[ 0.566485] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]

[ 0.566489] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0300000-0xf03fffff]

[ 0.566587] pci 0000:05:00.0: reg 10 64bit mmio: [0xf0200000-0xf0201fff]

[ 0.566664] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold

[ 0.566671] pci 0000:05:00.0: PME# disabled

[ 0.566754] pci 0000:00:1c.2: bridge 32bit mmio: [0xf0200000-0xf02fffff]

[ 0.566831] pci 0000:06:00.0: reg 10 io port: [0x4000-0x40ff]

[ 0.566859] pci 0000:06:00.0: reg 18 64bit mmio: [0xf0500000-0xf0500fff]

[ 0.566887] pci 0000:06:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]

[ 0.566902] pci 0000:06:00.0: supports D1 D2

[ 0.566903] pci 0000:06:00.0: PME# supported from D1 D2 D3hot D3cold

[ 0.566909] pci 0000:06:00.0: PME# disabled

[ 0.566976] pci 0000:00:1c.3: bridge io port: [0x4000-0x4fff]

[ 0.566981] pci 0000:00:1c.3: bridge 32bit mmio: [0xf0500000-0xf05fffff]

[ 0.567061] pci 0000:07:00.0: reg 10 64bit mmio: [0xf0402000-0xf040207f]

[ 0.567081] pci 0000:07:00.0: reg 18 64bit mmio: [0xf0400000-0xf0401fff]

[ 0.567092] pci 0000:07:00.0: reg 20 io port: [0x5000-0x507f]

[ 0.567125] pci 0000:07:00.0: supports D1 D2

[ 0.567196] pci 0000:00:1c.4: bridge io port: [0x5000-0x5fff]

[ 0.567200] pci 0000:00:1c.4: bridge 32bit mmio: [0xf0400000-0xf04fffff]

[ 0.567254] pci 0000:08:04.0: reg 10 32bit mmio: [0xf0600000-0xf0600fff]

[ 0.567262] pci 0000:08:04.0: reg 14 32bit mmio: [0xf0602000-0xf06027ff]

[ 0.567304] pci 0000:08:04.0: supports D1 D2

[ 0.567305] pci 0000:08:04.0: PME# supported from D0 D1 D2 D3hot D3cold

[ 0.567309] pci 0000:08:04.0: PME# disabled

[ 0.567373] pci 0000:00:1e.0: transparent bridge

[ 0.567380] pci 0000:00:1e.0: bridge 32bit mmio: [0xf0600000-0xf06fffff]

[ 0.567426] bus 00 -> node 0

[ 0.567432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[ 0.567782] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]

[ 0.567913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]

[ 0.568050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]

[ 0.568177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]

[ 0.568304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]

[ 0.568432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]

[ 0.568576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]

[ 0.578784] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)

[ 0.578895] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10

[ 0.579004] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)

[ 0.579114] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10

[ 0.579222] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11

[ 0.579329] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)

[ 0.579436] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11

[ 0.579544] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10

[ 0.579807] ACPI: WMI: Mapper loaded

[ 0.580083] SCSI subsystem initialized

[ 0.580088] libata version 3.00 loaded.

[ 0.580088] usbcore: registered new interface driver usbfs

[ 0.580088] usbcore: registered new interface driver hub

[ 0.580088] usbcore: registered new device driver usb

[ 0.580088] PCI: Using ACPI for IRQ routing

[ 0.592008] Bluetooth: Core ver 2.13

[ 0.592012] NET: Registered protocol family 31

[ 0.592012] Bluetooth: HCI device and connection manager initialized

[ 0.592013] Bluetooth: HCI socket layer initialized

[ 0.592015] NET: Registered protocol family 8

[ 0.592016] NET: Registered protocol family 20

[ 0.592027] NetLabel: Initializing

[ 0.592029] NetLabel: domain hash size = 128

[ 0.592030] NetLabel: protocols = UNLABELED CIPSOv4

[ 0.592042] NetLabel: unlabeled traffic allowed by default

[ 0.592070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0

[ 0.592073] hpet0: 3 comparators, 64-bit 14.318180 MHz counter

[ 0.596060] AppArmor: AppArmor Filesystem Enabled

[ 0.600009] Switched to high resolution mode on CPU 0

[ 0.600625] Switched to high resolution mode on CPU 1

[ 0.609007] pnp: PnP ACPI init

[ 0.609014] ACPI: bus type pnp registered

[ 0.629564] pnp 00:07: io resource (0xfe00-0xfe00) overlaps 0000:00:1c.0 BAR 7 (0xf000-0xffff), disabling

[ 0.629872] pnp: PnP ACPI: found 11 devices

[ 0.629874] ACPI: ACPI bus type pnp unregistered

[ 0.629881] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved

[ 0.629884] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved

[ 0.629886] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved

[ 0.629888] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved

[ 0.629889] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved

[ 0.629891] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved

[ 0.629893] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved

[ 0.629895] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved

[ 0.629902] system 00:05: iomem range 0xfed00000-0xfed003ff has been reserved

[ 0.629907] system 00:07: ioport range 0x680-0x69f has been reserved

[ 0.629909] system 00:07: ioport range 0x800-0x80f has been reserved

[ 0.629911] system 00:07: ioport range 0x1000-0x107f has been reserved

[ 0.629913] system 00:07: ioport range 0x1180-0x11bf has been reserved

[ 0.629914] system 00:07: ioport range 0x1640-0x164f has been reserved

[ 0.634595] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]

[ 0.634598] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01

[ 0.634600] pci 0000:00:01.0: IO window: 0x2000-0x2fff

[ 0.634603] pci 0000:00:01.0: MEM window: 0xcc000000-0xceffffff

[ 0.634606] pci 0000:00:01.0: PREFETCH window: 0x000000d0000000-0x000000dfffffff

[ 0.634610] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02

[ 0.634613] pci 0000:00:1c.0: IO window: 0xf000-0xffff

[ 0.634618] pci 0000:00:1c.0: MEM window: 0xfb000000-0xfcffffff

[ 0.634622] pci 0000:00:1c.0: PREFETCH window: disabled

[ 0.634630] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04

[ 0.634633] pci 0000:00:1c.1: IO window: 0x3000-0x3fff

[ 0.634638] pci 0000:00:1c.1: MEM window: 0xf0300000-0xf03fffff

[ 0.634642] pci 0000:00:1c.1: PREFETCH window: 0x000000c2000000-0x000000c20fffff

[ 0.634650] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05

[ 0.634651] pci 0000:00:1c.2: IO window: disabled

[ 0.634657] pci 0000:00:1c.2: MEM window: 0xf0200000-0xf02fffff

[ 0.634661] pci 0000:00:1c.2: PREFETCH window: disabled

[ 0.634668] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06

[ 0.634671] pci 0000:00:1c.3: IO window: 0x4000-0x4fff

[ 0.634676] pci 0000:00:1c.3: MEM window: 0xf0500000-0xf05fffff

[ 0.634680] pci 0000:00:1c.3: PREFETCH window: 0x000000c2100000-0x000000c21fffff

[ 0.634688] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07

[ 0.634691] pci 0000:00:1c.4: IO window: 0x5000-0x5fff

[ 0.634696] pci 0000:00:1c.4: MEM window: 0xf0400000-0xf04fffff

[ 0.634700] pci 0000:00:1c.4: PREFETCH window: disabled

[ 0.634707] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08

[ 0.634708] pci 0000:00:1e.0: IO window: disabled

[ 0.634714] pci 0000:00:1e.0: MEM window: 0xf0600000-0xf06fffff

[ 0.634718] pci 0000:00:1e.0: PREFETCH window: disabled

[ 0.634732] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[ 0.634735] pci 0000:00:01.0: setting latency timer to 64

[ 0.634743] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[ 0.634748] pci 0000:00:1c.0: setting latency timer to 64

[ 0.634755] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16

[ 0.634759] pci 0000:00:1c.1: setting latency timer to 64

[ 0.634768] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[ 0.634772] pci 0000:00:1c.2: setting latency timer to 64

[ 0.634781] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19

[ 0.634785] pci 0000:00:1c.3: setting latency timer to 64

[ 0.634793] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[ 0.634797] pci 0000:00:1c.4: setting latency timer to 64

[ 0.634805] pci 0000:00:1e.0: setting latency timer to 64

[ 0.634808] bus: 00 index 0 io port: [0x00-0xffff]

[ 0.634809] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]

[ 0.634811] bus: 01 index 0 io port: [0x2000-0x2fff]

[ 0.634813] bus: 01 index 1 mmio: [0xcc000000-0xceffffff]

[ 0.634814] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]

[ 0.634815] bus: 01 index 3 mmio: [0x0-0x0]

[ 0.634817] bus: 02 index 0 io port: [0xf000-0xffff]

[ 0.634818] bus: 02 index 1 mmio: [0xfb000000-0xfcffffff]

[ 0.634820] bus: 02 index 2 mmio: [0x0-0x0]

[ 0.634821] bus: 02 index 3 mmio: [0x0-0x0]

[ 0.634822] bus: 04 index 0 io port: [0x3000-0x3fff]

[ 0.634824] bus: 04 index 1 mmio: [0xf0300000-0xf03fffff]

[ 0.634825] bus: 04 index 2 mmio: [0xc2000000-0xc20fffff]

[ 0.634827] bus: 04 index 3 mmio: [0x0-0x0]

[ 0.634828] bus: 05 index 0 mmio: [0x0-0x0]

[ 0.634829] bus: 05 index 1 mmio: [0xf0200000-0xf02fffff]

[ 0.634831] bus: 05 index 2 mmio: [0x0-0x0]

[ 0.634832] bus: 05 index 3 mmio: [0x0-0x0]

[ 0.634833] bus: 06 index 0 io port: [0x4000-0x4fff]

[ 0.634835] bus: 06 index 1 mmio: [0xf0500000-0xf05fffff]

[ 0.634836] bus: 06 index 2 mmio: [0xc2100000-0xc21fffff]

[ 0.634838] bus: 06 index 3 mmio: [0x0-0x0]

[ 0.634839] bus: 07 index 0 io port: [0x5000-0x5fff]

[ 0.634840] bus: 07 index 1 mmio: [0xf0400000-0xf04fffff]

[ 0.634842] bus: 07 index 2 mmio: [0x0-0x0]

[ 0.634843] bus: 07 index 3 mmio: [0x0-0x0]

[ 0.634844] bus: 08 index 0 mmio: [0x0-0x0]

[ 0.634846] bus: 08 index 1 mmio: [0xf0600000-0xf06fffff]

[ 0.634847] bus: 08 index 2 mmio: [0x0-0x0]

[ 0.634848] bus: 08 index 3 io port: [0x00-0xffff]

[ 0.634850] bus: 08 index 4 mmio: [0x000000-0xffffffffffffffff]

[ 0.634857] NET: Registered protocol family 2

[ 0.668047] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)

[ 0.668597] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)

[ 0.670767] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)

[ 0.671411] TCP: Hash tables configured (established 262144 bind 65536)

[ 0.671413] TCP reno registered

[ 0.680109] NET: Registered protocol family 1

[ 0.680232] checking if image is initramfs... it is

[ 1.322382] Freeing initrd memory: 7775k freed

[ 1.325922] Simple Boot Flag at 0x36 set to 0x1

[ 1.326221] audit: initializing netlink socket (disabled)

[ 1.326237] type=2000 audit(1252155502.324:1): initialized

[ 1.334076] HugeTLB registered 2 MB page size, pre-allocated 0 pages

[ 1.335144] VFS: Disk quotas dquot_6.5.1

[ 1.335189] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)

[ 1.335669] fuse init (API version 7.10)

[ 1.335736] msgmni has been set to 5965

[ 1.335880] alg: No test for stdrng (krng)

[ 1.335888] io scheduler noop registered

[ 1.335890] io scheduler anticipatory registered

[ 1.335892] io scheduler deadline registered

[ 1.335925] io scheduler cfq registered (default)

[ 1.336088] pci 0000:01:00.0: Boot video device

[ 1.376733] pcieport-driver 0000:00:01.0: setting latency timer to 64

[ 1.376764] pcieport-driver 0000:00:01.0: found MSI capability

[ 1.376785] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X

[ 1.376793] pci_express 0000:00:01.0cie00: allocate port service

[ 1.376805] pci_express 0000:00:01.0cie02: allocate port service

[ 1.376815] pci_express 0000:00:01.0cie03: allocate port service

[ 1.376859] pcieport-driver 0000:00:1c.0: setting latency timer to 64

[ 1.376907] pcieport-driver 0000:00:1c.0: found MSI capability

[ 1.376939] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X

[ 1.376955] pci_express 0000:00:1c.0cie00: allocate port service

[ 1.376968] pci_express 0000:00:1c.0cie02: allocate port service

[ 1.376977] pci_express 0000:00:1c.0cie03: allocate port service

[ 1.377054] pcieport-driver 0000:00:1c.1: setting latency timer to 64

[ 1.377101] pcieport-driver 0000:00:1c.1: found MSI capability

[ 1.377133] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X

[ 1.377148] pci_express 0000:00:1c.1cie00: allocate port service

[ 1.377159] pci_express 0000:00:1c.1cie02: allocate port service

[ 1.377168] pci_express 0000:00:1c.1cie03: allocate port service

[ 1.377238] pcieport-driver 0000:00:1c.2: setting latency timer to 64

[ 1.377286] pcieport-driver 0000:00:1c.2: found MSI capability

[ 1.377318] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X

[ 1.377333] pci_express 0000:00:1c.2cie00: allocate port service

[ 1.377343] pci_express 0000:00:1c.2cie02: allocate port service

[ 1.377355] pci_express 0000:00:1c.2cie03: allocate port service

[ 1.377426] pcieport-driver 0000:00:1c.3: setting latency timer to 64

[ 1.377473] pcieport-driver 0000:00:1c.3: found MSI capability

[ 1.377505] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X

[ 1.377520] pci_express 0000:00:1c.3cie00: allocate port service

[ 1.377530] pci_express 0000:00:1c.3cie02: allocate port service

[ 1.377541] pci_express 0000:00:1c.3cie03: allocate port service

[ 1.377612] pcieport-driver 0000:00:1c.4: setting latency timer to 64

[ 1.377659] pcieport-driver 0000:00:1c.4: found MSI capability

[ 1.377691] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X

[ 1.377706] pci_express 0000:00:1c.4cie00: allocate port service

[ 1.377716] pci_express 0000:00:1c.4cie02: allocate port service

[ 1.377726] pci_express 0000:00:1c.4cie03: allocate port service

[ 1.377804] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[ 1.378258] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[ 1.378740] ACPI: AC Adapter [AC0] (on-line)

[ 1.425399] ACPI: Battery Slot [BAT0] (battery present)

[ 1.425471] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0

[ 1.425473] ACPI: Power Button (FF) [PWRF]

[ 1.425511] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1

[ 1.425552] ACPI: Lid Switch [LID0]

[ 1.425589] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2

[ 1.425591] ACPI: Power Button (CM) [PWRB]

[ 1.425626] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3

[ 1.425628] ACPI: Sleep Button (CM) [SLPB]

[ 1.426230] ACPI: SSDT BFED3440, 02FC (r1 PmRef Cpu0Ist 3000 INTL 20050624)

[ 1.426646] ACPI: SSDT BFED2DAF, 060C (r1 PmRef Cpu0Cst 3001 INTL 20050624)

[ 1.428826] Monitor-Mwait will be used to enter C-1 state

[ 1.428828] Monitor-Mwait will be used to enter C-3 state

[ 1.428842] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])

[ 1.428862] processor ACPI_CPU:00: registered as cooling_device0

[ 1.428865] ACPI: Processor [CPU0] (supports 8 throttling states)

[ 1.429211] ACPI: SSDT BFED373C, 00C8 (r1 PmRef Cpu1Ist 3000 INTL 20050624)

[ 1.429502] ACPI: SSDT BFED33BB, 0085 (r1 PmRef Cpu1Cst 3000 INTL 20050624)

[ 1.431173] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])

[ 1.431188] processor ACPI_CPU:01: registered as cooling_device1

[ 1.431191] ACPI: Processor [CPU1] (supports 8 throttling states)

[ 1.454245] thermal LNXTHERM:01: registered as thermal_zone0

[ 1.455749] ACPI: Thermal Zone [THRM] (28 C)

[ 1.492201] Linux agpgart interface v0.103

[ 1.492208] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

[ 1.493045] brd: module loaded

[ 1.493308] loop: module loaded

[ 1.493362] Fixed MDIO Bus: probed

[ 1.493367] PPP generic driver version 2.4.2

[ 1.493412] input: Macintosh mouse button emulation as /devices/virtual/input/input4

[ 1.493436] Driver 'sd' needs updating - please use bus_type methods

[ 1.493443] Driver 'sr' needs updating - please use bus_type methods

[ 1.493477] ahci 0000:00:1f.2: version 3.0

[ 1.493488] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[ 1.493524] ahci 0000:00:1f.2: irq 2297 for MSI/MSI-X

[ 1.493587] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode

[ 1.493590] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part

[ 1.493595] ahci 0000:00:1f.2: setting latency timer to 64

[ 1.493814] scsi0 : ahci

[ 1.493883] scsi1 : ahci

[ 1.493931] scsi2 : ahci

[ 1.494013] ata1: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704100 irq 2297

[ 1.494016] ata2: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704180 irq 2297

[ 1.494019] ata3: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704200 irq 2297

[ 1.812020] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

[ 1.812798] ACPI Warning (nspredef-0852): \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]

[ 1.812804] ata1.00: _GTF unexpected object type 0x1

[ 1.838711] ata1.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133

[ 1.838713] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)

[ 1.839585] ata1.00: _GTF unexpected object type 0x1

[ 1.839726] ata1.00: configured for UDMA/133

[ 2.172017] ata2: SATA link down (SStatus 0 SControl 300)

[ 2.508015] ata3: SATA link down (SStatus 0 SControl 300)

[ 2.524088] scsi 0:0:0:0: Direct-Access ATA WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5

[ 2.524161] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)

[ 2.524175] sd 0:0:0:0: [sda] Write Protect is off

[ 2.524177] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[ 2.524200] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[ 2.524251] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)

[ 2.524264] sd 0:0:0:0: [sda] Write Protect is off

[ 2.524266] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[ 2.524287] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[ 2.524290] sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >

[ 2.650611] sd 0:0:0:0: [sda] Attached SCSI disk

[ 2.650647] sd 0:0:0:0: Attached scsi generic sg0 type 0

[ 2.650689] ata_piix 0000:00:1f.1: version 2.12

[ 2.650696] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[ 2.650726] ata_piix 0000:00:1f.1: setting latency timer to 64

[ 2.650791] scsi3 : ata_piix

[ 2.650838] scsi4 : ata_piix

[ 2.651419] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14

[ 2.651421] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15

[ 2.812412] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WW01, max UDMA/33

[ 2.828362] ata4.00: configured for UDMA/33

[ 2.995168] isa bounce pool size: 16 pages

[ 2.998670] scsi 3:0:0:0: CD-ROM HL-DT-ST DVDRAM GSA-T20N WW01 PQ: 0 ANSI: 5

[ 3.009575] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

[ 3.009578] Uniform CD-ROM driver Revision: 3.20

[ 3.009651] sr 3:0:0:0: Attached scsi CD-ROM sr0

[ 3.009681] sr 3:0:0:0: Attached scsi generic sg1 type 5

[ 3.009739] sata_sil24 0000:07:00.0: version 1.1

[ 3.009751] sata_sil24 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[ 3.009810] sata_sil24 0000:07:00.0: setting latency timer to 64

[ 3.009901] scsi5 : sata_sil24

[ 3.009933] ata6: SATA max UDMA/100 host m128@0xf0402000 port 0xf0400000 irq 16

[ 5.088022] ata6: SATA link down (SStatus 0 SControl 0)

[ 5.088486] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[ 5.088502] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[ 5.088511] ehci_hcd 0000:00:1a.7: setting latency timer to 64

[ 5.088514] ehci_hcd 0000:00:1a.7: EHCI Host Controller

[ 5.088560] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1

[ 5.092471] ehci_hcd 0000:00:1a.7: debug port 1

[ 5.092477] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported

[ 5.092488] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800

[ 5.104007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00

[ 5.104062] usb usb1: configuration #1 chosen from 1 choice

[ 5.104084] hub 1-0:1.0: USB hub found

[ 5.104090] hub 1-0:1.0: 4 ports detected

[ 5.104180] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23

[ 5.104189] ehci_hcd 0000:00:1d.7: setting latency timer to 64

[ 5.104192] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[ 5.104230] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2

[ 5.108124] ehci_hcd 0000:00:1d.7: debug port 1

[ 5.108130] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported

[ 5.108141] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00

[ 5.120006] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00

[ 5.120062] usb usb2: configuration #1 chosen from 1 choice

[ 5.120081] hub 2-0:1.0: USB hub found

[ 5.120087] hub 2-0:1.0: 6 ports detected

[ 5.120166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[ 5.120180] uhci_hcd: USB Universal Host Controller Interface driver

[ 5.120196] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[ 5.120202] uhci_hcd 0000:00:1a.0: setting latency timer to 64

[ 5.120205] uhci_hcd 0000:00:1a.0: UHCI Host Controller

[ 5.120238] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3

[ 5.120264] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800

[ 5.120328] usb usb3: configuration #1 chosen from 1 choice

[ 5.120348] hub 3-0:1.0: USB hub found

[ 5.120353] hub 3-0:1.0: 2 ports detected

[ 5.120424] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21

[ 5.120430] uhci_hcd 0000:00:1a.1: setting latency timer to 64

[ 5.120433] uhci_hcd 0000:00:1a.1: UHCI Host Controller

[ 5.120468] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4

[ 5.120501] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820

[ 5.120563] usb usb4: configuration #1 chosen from 1 choice

[ 5.120584] hub 4-0:1.0: USB hub found

[ 5.120589] hub 4-0:1.0: 2 ports detected

[ 5.120665] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23

[ 5.120671] uhci_hcd 0000:00:1d.0: setting latency timer to 64

[ 5.120674] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[ 5.120706] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5

[ 5.120731] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840

[ 5.120793] usb usb5: configuration #1 chosen from 1 choice

[ 5.120812] hub 5-0:1.0: USB hub found

[ 5.120817] hub 5-0:1.0: 2 ports detected

[ 5.120889] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[ 5.120895] uhci_hcd 0000:00:1d.1: setting latency timer to 64

[ 5.120898] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[ 5.120933] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6

[ 5.120966] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860

[ 5.121034] usb usb6: configuration #1 chosen from 1 choice

[ 5.121056] hub 6-0:1.0: USB hub found

[ 5.121061] hub 6-0:1.0: 2 ports detected

[ 5.121136] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[ 5.121142] uhci_hcd 0000:00:1d.2: setting latency timer to 64

[ 5.121145] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[ 5.121181] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7

[ 5.121208] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880

[ 5.121270] usb usb7: configuration #1 chosen from 1 choice

[ 5.121290] hub 7-0:1.0: USB hub found

[ 5.121296] hub 7-0:1.0: 2 ports detected

[ 5.121410] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12

[ 5.124768] i8042.c: Detected active multiplexing controller, rev 1.1.

[ 5.126105] serio: i8042 KBD port at 0x60,0x64 irq 1

[ 5.126109] serio: i8042 AUX0 port at 0x60,0x64 irq 12

[ 5.126111] serio: i8042 AUX1 port at 0x60,0x64 irq 12

[ 5.126112] serio: i8042 AUX2 port at 0x60,0x64 irq 12

[ 5.126114] serio: i8042 AUX3 port at 0x60,0x64 irq 12

[ 5.136032] mice: PS/2 mouse device common for all mice

[ 5.196083] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0

[ 5.196114] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs

[ 5.196159] device-mapper: uevent: version 1.0.3

[ 5.196233] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]

[ 5.196285] device-mapper: multipath: version 1.0.5 loaded

[ 5.196288] device-mapper: multipath round-robin: version 1.0.0 loaded

[ 5.196405] cpuidle: using governor ladder

[ 5.196492] cpuidle: using governor menu

[ 5.196831] TCP cubic registered

[ 5.196892] NET: Registered protocol family 10

[ 5.197212] lo: Disabled Privacy Extensions

[ 5.197448] NET: Registered protocol family 17

[ 5.197465] Bluetooth: L2CAP ver 2.11

[ 5.197466] Bluetooth: L2CAP socket layer initialized

[ 5.197469] Bluetooth: SCO (Voice Link) ver 0.6

[ 5.197470] Bluetooth: SCO socket layer initialized

[ 5.197497] Bluetooth: RFCOMM socket layer initialized

[ 5.197503] Bluetooth: RFCOMM TTY layer initialized

[ 5.197505] Bluetooth: RFCOMM ver 1.10

[ 5.197545] Marking TSC unstable due to TSC halts in idle

[ 5.198181] registered taskstats version 1

[ 5.198299] Magic number: 9:108:986

[ 5.198410] rtc_cmos 00:08: setting system clock to 2009-09-05 12:58:26 UTC (1252155506)

[ 5.198413] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[ 5.198414] EDD information not available.

[ 5.198455] Freeing unused kernel memory: 532k freed

[ 5.198660] Write protecting the kernel read-only data: 6688k

[ 5.233009] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5

[ 5.453275] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

[ 5.453301] r8169 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[ 5.453330] r8169 0000:06:00.0: setting latency timer to 64

[ 5.453517] r8169 0000:06:00.0: irq 2296 for MSI/MSI-X

[ 5.454045] eth0: RTL8168b/8111b at 0xffffc20010082000, 00:03:0d:81:14:f8, XID 38000000 IRQ 2296

[ 5.490294] ohci1394 0000:08:04.0: enabling device (0195 -> 0197)

[ 5.490308] ohci1394 0000:08:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20

[ 5.541056] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20] MMIO=[f0600000-f06007ff] Max Packet=[2048] IR/IT contexts=[8/8]

[ 5.848133] usb 3-1: new full speed USB device using uhci_hcd and address 2

[ 6.038412] usb 3-1: configuration #1 chosen from 1 choice

[ 6.281070] usb 5-2: new low speed USB device using uhci_hcd and address 2

[ 6.352898] PM: Starting manual resume from disk

[ 6.352902] PM: Resume from partition 8:10

[ 6.352903] PM: Checking hibernation image.

[ 6.353165] PM: Resume from disk failed.

[ 6.373375] EXT3-fs: INFO: recovery required on readonly filesystem.

[ 6.373377] EXT3-fs: write access will be enabled during recovery.

[ 6.457494] usb 5-2: configuration #1 chosen from 1 choice

[ 6.463776] usbcore: registered new interface driver hiddev

[ 6.480072] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6

[ 6.500062] Clocksource tsc unstable (delta = -129473662 ns)

[ 6.501096] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0

[ 6.501110] usbcore: registered new interface driver usbhid

[ 6.501112] usbhid: v2.6:USB HID core driver

[ 6.852634] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00030d0055012906]

[ 24.348145] kjournald starting. Commit interval 5 seconds

[ 24.348164] EXT3-fs: recovery complete.

[ 24.427923] EXT3-fs: mounted filesystem with ordered data mode.

[ 183.191357] udev: starting version 141

[ 184.748960] nvidia: module license 'NVIDIA' taints kernel.

[ 184.851468] Bluetooth: Generic Bluetooth USB driver ver 0.3

[ 184.851558] usbcore: registered new interface driver btusb

[ 184.879882] input: PC Speaker as /devices/platform/pcspkr/input/input7

[ 185.001115] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[ 185.001124] nvidia 0000:01:00.0: setting latency timer to 64

[ 185.001449] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 180.44 Tue Mar 24 05:46:32 PST 2009

[ 185.013214] cfg80211: Calling CRDA to update world regulatory domain

[ 185.052976] iTCO_vendor_support: vendor-support=0

[ 185.348808] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05

[ 185.348961] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)

[ 185.349048] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

[ 185.512288] acpi device:05: registered as cooling_device2

[ 185.512332] ACPI: Cant attach device<6>input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input8

[ 185.537115] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)

[ 185.571472] cfg80211: World regulatory domain updated:

[ 185.571474] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)

[ 185.571476] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[ 185.571478] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

[ 185.571480] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

[ 185.571481] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[ 185.571483] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[ 185.582117] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume

[ 185.916696] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks

[ 185.916698] iwlagn: Copyright(c) 2003-2008 Intel Corporation

[ 185.916839] iwlagn 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[ 185.916848] iwlagn 0000:05:00.0: setting latency timer to 64

[ 185.916900] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4

[ 185.955808] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels

[ 185.955877] iwlagn 0000:05:00.0: irq 2295 for MSI/MSI-X

[ 185.956680] phy0: Selected rate control algorithm 'iwl-agn-rs'

[ 186.323730] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

[ 186.323810] HDA Intel 0000:00:1b.0: setting latency timer to 64

[ 186.459372] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa0b1, caps: 0xa04713/0x20040a

[ 186.502850] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9

[ 186.650431] lp: driver loaded but no devices found

[ 186.710549] Adding 2457904k swap on /dev/sda10. Priority:-1 extents:1 across:2457904k

[ 187.557071] EXT3 FS on sda9, internal journal

[ 188.745270] type=1505 audit(1252148490.045:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2176

[ 188.776331] type=1505 audit(1252148490.077:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2180

[ 188.776433] type=1505 audit(1252148490.077:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2180

[ 188.776467] type=1505 audit(1252148490.077:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2180

[ 188.776498] type=1505 audit(1252148490.077:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2180

[ 188.862858] type=1505 audit(1252148490.161:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2185

[ 188.862997] type=1505 audit(1252148490.161:: operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2185

[ 188.882639] type=1505 audit(1252148490.181:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2189

[ 194.582471] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[ 194.582473] Bluetooth: BNEP filters: protocol multicast

[ 194.615324] Bridge firewalling registered

[ 199.299347] ppdev: user-space parallel port driver

[ 202.698957] r8169: eth0: link down

[ 202.699529] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 202.700125] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-4965-2.ucode

[ 203.520339] Registered led device: iwl-phy0:radio

[ 203.520926] Registered led device: iwl-phy0:assoc

[ 203.520943] Registered led device: iwl-phy0:RX

[ 203.520956] Registered led device: iwl-phy0:TX

[ 203.760666] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[ 203.929331] NVRM : nv_acpi_nvif_method : NVIF data invalid. function d subFunction 0

[ 215.762027] NVRM : nv_acpi_nvif_method : NVIF data invalid. function d subFunction 0

---

### Post by ftabor on 2009-09-05
Take a look at this thread, [http://ubuntuforums.org/showthread.php?t=1037264](http://ubuntuforums.org/showthread.php?t=1037264) and pay attention to the posts from 67GTA.   His solution fixed my installation and continues to do so after each kernel update.

---

### Post by Liolikas on 2009-09-05
Interesting info here:
[https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/330606](https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/330606)
maybe you simple do not have latest updates?

---

### Post by superstalker on 2009-09-05
ftabor: Everything has been installed correctly, and I have no MSFT/MFST msg.

Liolikas: Update manager: Your system is up-to-date. You have installed package information 1 day ago.

---

### Post by Liolikas on 2009-09-05
uname -a?

---

### Post by superstalker on 2009-09-05
Linux ***-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

---

### Post by Liolikas on 2009-09-05
Try 2.6.28-11.37

---

### Post by superstalker on 2009-09-05
Downgrading? Okay, but how?

---

### Post by Liolikas on 2009-09-05
With synaptic search for kernel and install. You can have few kernels at same time and boot to only one with grub.

---

### Post by superstalker on 2009-09-05
I suppose I have to install:

- kerneloops
- kerneltop
- liblinux-kernelsort-perl
- kernel-package

I'd rather doublecheck, then screw up.

---

### Post by Liolikas on 2009-09-05
Yes for sure install all deps.

---

### Post by superstalker on 2009-09-05
Okay, installed it, this should clear the bug?

---

### Post by superstalker on 2009-09-05
If so, I'm now doing a small test with partition manager, I it stalls again, I'll let you know.

---

### Post by superstalker on 2009-09-05
It works! Partition manager took 20 minutes, no stalling! Thanks!

---

### Post by superstalker on 2009-11-10
Hmmm... how do you apply this with a live CD? Changing the kernel works, but only after I restarted ubuntu. With a live CD I can't restart, because it'll discard all my changes.

I've finally made the decisioned to completely run my laptop on Ubuntu. So I'm resizing and moving my partitions with Gparted. And the only way do that is with live CD. I changed it with the 9.10 live CD, but still I have the same (really annoying) bug.

Actually last time I used live CD I have to tie my mouse to a moving object so it could take the whole night to copy paste data...

---

### Post by superstalker on 2009-11-10
Or is there a way to let the PC think my mouse is moving? Because restarting isn't an option, I'm now using GParted....


Solved: I recorded, saved, played and repeated the recording, the stalling does not occur after it.

---

### Post by Billy71 on 2010-12-07
Does anybody know what it was? Kernel 2.6.28-15 bug?

If so, is it fixed in Lucid and Maverick?

---

