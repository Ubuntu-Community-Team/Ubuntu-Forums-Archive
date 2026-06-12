---
title: "Ubuntu OS which crashes almost"
date: 2012-02-17
forum: General Help
---

### Post by naini on 2012-02-17
Hi i have Ubuntu OS which crashes almost at the same time ( + or - 20 min diff ) i have removed all the crons also on hosts , but still it gets rebooted every day , can some one help here how to get rid of this . I have got this installed on VIRTUAL box.
```

Linux vlsj-ss 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010
i686 GNU/Linux
root@vlsj-ss:/var/log#
Feb 15 06:50:45 vlsj-ss kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb 15 06:50:45 vlsj-ss rsyslogd: [origin software="rsyslogd" swVersion="4.2.0"
x-pid="704" x-info="[http://www.rsyslog.com]("http://www.rsyslog.com/")"] (re)start
Feb 15 06:50:45 vlsj-ss rsyslogd: rsyslogd's groupid changed to 103
Feb 15 06:50:45 vlsj-ss rsyslogd: rsyslogd's userid changed to 101
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Initializing cgroup subsys cpuset
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Initializing cgroup subsys cpu
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Linux version 2.6.32-24-generic-p
ae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP
Wed Jul 28 07:39:26 UTC 2010 (Ubuntu 2.6.32-24.39-generic-pae 2.6.32.15+drm33.5)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] KERNEL supported cpus:
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Intel GenuineIntel
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] AMD AuthenticAMD
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] NSC Geode by NSC
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Cyrix CyrixInstead
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Centaur CentaurHauls
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Transmeta GenuineTMx86
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Transmeta TransmetaCPU
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] UMC UMC UMC UMC
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] BIOS-provided physical RAM map:
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] BIOS-e820: 0000000000000000 - 00
0000000009f800 (usable)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] BIOS-e820: 000000000009f800 - 00
000000000a0000 (reserved)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] BIOS-e820: 00000000000ca000 - 00
000000000cc000 (reserved)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] BIOS-e820: 00000000000dc000 - 00
000000000e4000 (reserved)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] DMI present.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Phoenix BIOS detected: BIOS may c
orrupt low RAM, working around it.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] last_pfn = 0x7f800 max_arch_pfn =
0x1000000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] x86 PAT enabled: cpu 0, old 0x0,
new 0x7010600070106
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Scanning 0 areas for low memory c
orruption
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] modified physical RAM map:
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] modified: 0000000000000000 - 000
0000000010000 (reserved)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] modified: 0000000000010000 - 000
000000009f800 (usable)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] modified: 000000000009f800 - 000
00000000a0000 (reserved)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] modified: 00000000000ca000 - 000
00000000cc000 (reserved)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] modified: 00000000000dc000 - 000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] init_memory_mapping: 000000000000
0000-00000000379fe000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] NX (Execute Disable) protection:
active
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] RAMDISK: 37861000 - 37fef6dc
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Allocated new RAMDISK: 0093f000 -
010cd6dc
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Move RAMDISK from 000000003786100
0 - 0000000037fef6db to 0093f000 - 010cd6db
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: RSDP 000f6a40 00024 (v02 PT
LTD )
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: XSDT 7f6f0772 0004C (v01 IN
TEL 440BX 06040000 VMW 01324272)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: FACP 7f6fee98 000F4 (v04 IN
TEL 440BX 06040000 PTL 000F4240)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: DSDT 7f6f0938 0E560 (v01 PT
LTD Custom 06040000 MSFT 03000001)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: FACS 7f6fffc0 00040
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: BOOT 7f6f0910 00028 (v01 PT
LTD $SBFTBL$ 06040000 LTP 00000001)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: APIC 7f6f08b2 0005E (v01 PT
WARE MEMPLUG 06040000 VMW 00000001)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] 1150MB HIGHMEM available.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] 889MB LOWMEM available.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] mapped low ram: 0 - 379fe000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] low ram: 0 - 379fe000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] node 0 low ram: 00000000 - 379f
e000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] node 0 bootmap 00012000 - 00018
f40
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] (9 early reservations) ==> bootme
m [0000000000 - 00379fe000]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] #0 [0000000000 - 0000001000]
BIOS data page ==> [0000000000 - 0000001000]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] #1 [0000001000 - 0000002000]
EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] #2 [0000006000 - 0000007000]
TRAMPOLINE ==> [0000006000 - 0000007000]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] #3 [0000100000 - 00009367f8]
TEXT DATA BSS ==> [0000100000 - 00009367f8]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] #4 [000009f800 - 0000100000]
BIOS reserved ==> [000009f800 - 0000100000]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] found SMP MP-table at [c00f6ab0]
f6ab0
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Zone PFN ranges:
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] DMA 0x00000010 -> 0x000010
00
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Normal 0x00001000 -> 0x000379
fe
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] HighMem 0x000379fe -> 0x0007f8
00
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Movable zone start PFN for each n
ode
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] early_node_map[3] active PFN rang
es
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] 0: 0x00000010 -> 0x0000009f
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] 0: 0x00000100 -> 0x0007f6f0
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] 0: 0x0007f700 -> 0x0007f800
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Using APIC driver default
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_
id[0x00] enabled)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_
id[0x01] enabled)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] hi
gh edge lint[0x1])
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] hi
gh edge lint[0x1])
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: IOAPIC (id[0x02] address[0x
fec00000] gsi_base[0])
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] IOAPIC[0]: apic_id 2, version 17,
address 0xfec00000, GSI 0-23
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq
0 global_irq 2 high edge)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Using ACPI (MADT) for SMP configu
ration information
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug C
PUs
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
000000009f000 - 00000000000a0000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
00000000a0000 - 00000000000ca000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
00000000ca000 - 00000000000cc000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
00000000cc000 - 00000000000dc000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
00000000dc000 - 00000000000e4000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
00000000e4000 - 00000000000e8000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PM: Registered nosave memory: 000
00000000e8000 - 0000000000100000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Allocating PCI resources starting
at 7f800000 (gap: 7f800000:60800000)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Booting paravirtualized kernel on
bare hardware
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cp
u_ids:2 nr_node_ids:1
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PERCPU: Embedded 15 pages/cpu @c2
200000 s39480 r0 d21960 u1048576
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] pcpu-alloc: s39480 r0 d21960 u104
8576 alloc=1*2097152
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Built 1 zonelists in Zone order,
mobility grouping on. Total pages: 518030
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Kernel command line: BOOT_IMAGE=/
boot/vmlinuz-2.6.32-24-generic-pae root=UUID=952be5ae-fc6f-491e-982d-d338e9a6cce
1 ro quiet
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] PID hash table entries: 4096 (ord
er: 2, 16384 bytes)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Dentry cache hash table entries:
131072 (order: 7, 524288 bytes)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Inode-cache hash table entries: 6
5536 (order: 6, 262144 bytes)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Enabling fast FPU save and restor
e... done.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Enabling unmasked SIMD FPU except
ion support... done.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Initializing CPU#0
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] allocated 10444480 bytes of page_
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] please try 'cgroup_disable=memory
' option if you don't want memory cgroups
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Initializing HighMem for node 0 (
000379fe:0007f800)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Memory: 2043736k/2088960k availab
le (4832k kernel code, 43688k reserved, 2221k data, 676k init, 1177544k highmem)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] virtual kernel memory layout:
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] fixmap : 0xfff1d000 - 0xffff
f000 ( 904 kB)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] pkmap : 0xffa00000 - 0xffc0
0000 (2048 kB)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] vmalloc : 0xf81fe000 - 0xff9f
e000 ( 120 MB)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] lowmem : 0xc0000000 - 0xf79f
e000 ( 889 MB)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] .init : 0xc07e4000 - 0xc088
d000 ( 676 kB)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] .data : 0xc05b821b - 0xc07e
3828 (2221 kB)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] .text : 0xc0100000 - 0xc05b
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] SLUB: Genslabs=13, HWalign=64, Or
der=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Hierarchical RCU implementation.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] NR_IRQS:2304 nr_irqs:424
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Extended CMOS year: 2000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Console: colour VGA+ 80x25
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] console [tty0] enabled
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] TSC freq read from hypervisor : 2
926.000 MHz
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Detected 2926.000 MHz processor.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000004] Calibrating delay loop (skipped),
value calculated using timer frequency.. 5852.00 BogoMIPS (lpj=11704000)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000013] Security Framework initialized
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000029] AppArmor: AppArmor initialized
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000035] Mount-cache hash table entries: 5
12
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000481] Initializing cgroup subsys ns
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000486] Initializing cgroup subsys cpuacc
t
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000489] Initializing cgroup subsys memory
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000494] Initializing cgroup subsys device
s
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000495] Initializing cgroup subsys freeze
r
--More--
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] SLUB: Genslabs=13, HWalign=64, Or
der=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Hierarchical RCU implementation.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] NR_IRQS:2304 nr_irqs:424
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Extended CMOS year: 2000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Console: colour VGA+ 80x25
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] console [tty0] enabled
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] TSC freq read from hypervisor : 2
926.000 MHz
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000000] Detected 2926.000 MHz processor.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000004] Calibrating delay loop (skipped),
value calculated using timer frequency.. 5852.00 BogoMIPS (lpj=11704000)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000013] Security Framework initialized
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000029] AppArmor: AppArmor initialized
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000035] Mount-cache hash table entries: 5
12
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000481] Initializing cgroup subsys ns
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000486] Initializing cgroup subsys cpuacc
t
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000489] Initializing cgroup subsys memory
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000494] Initializing cgroup subsys device
s
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000495] Initializing cgroup subsys freeze
r
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000524] CPU: Physical Processor ID: 0
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000530] CPU: L1 I cache: 32K, L1 D cache:
32K
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000532] CPU: L2 cache: 256K
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000532] CPU: L3 cache: 8192K
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000537] mce: CPU supports 0 MCE banks
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000559] Performance Events: Nehalem/Corei
7 events, Intel PMU driver.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000580] ... version: 3
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000580] ... bit width: 48
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000581] ... generic registers: 4
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000582] ... value mask: 0000f
fffffffffff
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000583] ... max period: 00000
0007fffffff
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000584] ... fixed-purpose events: 3
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000585] ... event mask: 00000
0070000000f
Feb 15 06:50:45 vlsj-ss kernel: [ 0.000590] Checking 'hlt' instruction... OK.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.021737] ACPI: Core revision 20090903
Feb 15 06:50:45 vlsj-ss kernel: [ 0.029492] ftrace: converting mcount calls t
o 0f 1f 44 00 00
Feb 15 06:50:45 vlsj-ss kernel: [ 0.029501] ftrace: allocating 22411 entries
in 44 pages
Feb 15 06:50:45 vlsj-ss kernel: [ 0.047139] Enabling APIC mode: Flat. Using
1 I/O APICs
Feb 15 06:50:45 vlsj-ss kernel: [ 0.047628] ..TIMER: vector=0x30 apic1=0 pin1
=2 apic2=-1 pin2=-1
Feb 15 06:50:45 vlsj-ss kernel: [ 0.087204] CPU0: Intel(R) Xeon(R) CPU
X5570 @ 2.93GHz stepping 05
Feb 15 06:50:45 vlsj-ss kernel: [ 0.191700] Booting processor 1 APIC 0x1 ip 0
x6000
Feb 15 06:50:45 vlsj-ss kernel: [ 0.202989] Initializing CPU#1
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279274] CPU: Physical Processor ID: 1
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279279] CPU: L1 I cache: 32K, L1 D cache:
32K
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279280] CPU: L2 cache: 256K
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279280] CPU: L3 cache: 8192K
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279289] mce: CPU supports 0 MCE banks
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279364] CPU1: Intel(R) Xeon(R) CPU
X5570 @ 2.93GHz stepping 05
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279420] Skipping synchronization checks a
s TSC is reliable.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279509] Brought up 2 CPUs
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279511] Total of 2 processors activated (
11704.64 BogoMIPS).
Feb 15 06:50:45 vlsj-ss kernel: [ 0.279655] x86 PAT enabled: cpu 1, old 0x0,
new 0x7010600070106
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280031] devtmpfs: initialized
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280372] regulator: core version 0.5
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280429] Time: 14:50:37 Date: 02/15/12
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280460] NET: Registered protocol family 1
6
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280575] EISA bus registered
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280586] ACPI: bus type pci registered
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280616] Trying to unpack rootfs image as
initramfs...
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280747] PCI: MCFG configuration 0: base e
0000000 segment 0 buses 0 - 255
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280766] PCI: MCFG area at e0000000 reserv
ed in E820
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280767] PCI: Using MMCONFIG for extended
config space
Feb 15 06:50:45 vlsj-ss kernel: [ 0.280768] PCI: Using configuration type 1 f
or base access
Feb 15 06:50:45 vlsj-ss kernel: [ 0.287351] bio: create slab <bio-0> at 0
Feb 15 06:50:45 vlsj-ss kernel: [ 0.326153] ACPI: BIOS _OSI(Linux) query igno
red
Feb 15 06:50:45 vlsj-ss kernel: [ 0.330361] ACPI: Interpreter enabled
Feb 15 06:50:45 vlsj-ss kernel: [ 0.330368] ACPI: (supports S0 S1 S4 S5)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.330383] ACPI: Using IOAPIC for interrupt
routing
Feb 15 06:50:45 vlsj-ss kernel: [ 0.400649] ACPI: No dock devices found.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.401357] ACPI: PCI Root Bridge [PCI0] (000
0:00)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.402857] pci 0000:00:07.3: quirk: region 1
000-103f claimed by PIIX4 ACPI
Feb 15 06:50:45 vlsj-ss kernel: [ 0.442645] Freeing initrd memory: 7737k free
d
Feb 15 06:50:45 vlsj-ss kernel: [ 0.593860] ACPI: PCI Interrupt Link [LNKA] (
IRQs 3 4 5 6 7 *9 10 11 14 15)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594006] ACPI: PCI Interrupt Link [LNKB] (
IRQs 3 4 5 6 7 9 10 *11 14 15)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594126] ACPI: PCI Interrupt Link [LNKC] (
IRQs 3 4 5 6 7 9 *10 11 14 15)
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594244] ACPI: PCI Interrupt Link [LNKD] (
IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594384] vgaarb: device added: PCI:0000:00
:0f.0,decodes=io+mem,owns=io+mem,locks=none
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594400] vgaarb: loaded
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594522] SCSI subsystem initialized
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594749] usbcore: registered new interface
driver usbfs
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594756] usbcore: registered new interface
driver hub
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594789] usbcore: registered new device dr
iver usb
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594906] ACPI: WMI: Mapper loaded
Feb 15 06:50:45 vlsj-ss kernel: [ 0.594907] PCI: Using ACPI for IRQ routing
Feb 15 06:50:45 vlsj-ss kernel: [ 0.595555] NetLabel: Initializing
Feb 15 06:50:45 vlsj-ss kernel: [ 0.595556] NetLabel: domain hash size = 128
Feb 15 06:50:45 vlsj-ss kernel: [ 0.595557] NetLabel: protocols = UNLABELED
CIPSOv4
Feb 15 06:50:45 vlsj-ss kernel: [ 0.595571] NetLabel: unlabeled traffic allo
wed by default
Feb 15 06:50:45 vlsj-ss kernel: [ 0.595620] Switching to clocksource tsc
Feb 15 06:50:45 vlsj-ss kernel: [ 0.597731] AppArmor: AppArmor Filesystem Ena
bled
Feb 15 06:50:45 vlsj-ss kernel: [ 0.597738] pnp: PnP ACPI init
Feb 15 06:50:45 vlsj-ss kernel: [ 0.597744] ACPI: bus type pnp registered
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653880] pnp: PnP ACPI: found 13 devices
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653882] ACPI: ACPI bus type pnp unregiste
red
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653886] PnPBIOS: Disabled by ACPI PNP
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653896] system 00:01: ioport range 0x1000
-0x103f has been reserved
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653897] system 00:01: ioport range 0x1040
-0x104f has been reserved
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653899] system 00:01: ioport range 0xcf0-
0xcf1 has been reserved
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653904] system 00:0c: ioport range 0x1060
-0x107f has been reserved
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653907] system 00:0c: iomem range 0xe0000
000-0xefffffff has been reserved
Feb 15 06:50:45 vlsj-ss kernel: [ 0.653908] system 00:0c: iomem range 0xd8a00
000-0xd8bfffff has been reserved
Feb 15 06:50:45 vlsj-ss kernel: [ 0.689769] pci 0000:00:15.3: BAR 13: can't a
llocate I/O resource [0x10000-0xffff]
Feb 15 06:50:45 vlsj-ss kernel: [ 0.689773] pci 0000:00:15.4: BAR 13: can't a
llocate I/O resource [0x10000-0xffff]
--More--
--More--
--More--
--More--
```

---

### Post by overdrank on 2012-02-17
Hi and welcome, I have moved your post to it's own thread.

---

