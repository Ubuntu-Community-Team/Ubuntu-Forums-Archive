---
title: "Speed trouble with 10.10"
date: 2011-02-15
forum: General Help
---

### Post by dvdfilmbuff on 2011-02-15
Hi,
 
I have been using 10.04 LTS since it was released on an HP super slim 7600 desktop with 2GB ram and 256 MB Nvidia FX5200 gfx card and a Pentium D (dual core) 2.8Ghz CPU - All was sweet and bang tidy fast! :)
 
This machine died so now I have sourced a Dell Precision 380 Workstation which I have added 2 x 250GB Sata Drives (configured in normal SATA mode and not raid) in place of the original 80gb ones. Memory is still 2GB but now I have a 128MB Nvidia Quadro FX540 gfs card and Pentium D (dual core) 3.0 Ghz
 
My problem is that since installing 10.10 the machine performs like a dog! :( - The little HP machine was much quicker!!
 
What is going on? - Do I need a better Video card? More memory? Faster drives?
 
I would have thought, nay hoped that a Workstation class machine would be quicker than a normal desktop based machine?
 
Do I need to install 64bit Ubuntu to get the speed back?
 
I have checked for hardware driver requirements and the only ones that show up are for the Nvidia (Which I have installed).
 
Non of the flashy screen effects are turned on, but everything seems laggy.
 
Opening windows in Ubuntu there is a delay. Accessing the HDs is laggy, copying to and from USB devices is slower than before.
 
Any advice to make this as quick as it should be?
 
Cheers
 
 
(When I installed W7 Pro 32bit and all the driver updates, it was super speedy. I dont really want to use Wind*ws if I dont have to, but at these reduced speeds I may have to)

---

### Post by dvdfilmbuff on 2011-02-19
> **dvdfilmbuff said:**
> Hi,
 
I have been using 10.04 LTS since it was released on an HP super slim 7600 desktop with 2GB ram and 256 MB Nvidia FX5200 gfx card and a Pentium D (dual core) 2.8Ghz CPU - All was sweet and bang tidy fast! :)
 
This machine died so now I have sourced a Dell Precision 380 Workstation which I have added 2 x 250GB Sata Drives (configured in normal SATA mode and not raid) in place of the original 80gb ones. Memory is still 2GB but now I have a 128MB Nvidia Quadro FX540 gfs card and Pentium D (dual core) 3.0 Ghz
 
My problem is that since installing 10.10 the machine performs like a dog! :( - The little HP machine was much quicker!!
 
What is going on? - Do I need a better Video card? More memory? Faster drives?
 
I would have thought, nay hoped that a Workstation class machine would be quicker than a normal desktop based machine?
 
Do I need to install 64bit Ubuntu to get the speed back?
 
I have checked for hardware driver requirements and the only ones that show up are for the Nvidia (Which I have installed).
 
Non of the flashy screen effects are turned on, but everything seems laggy.
 
Opening windows in Ubuntu there is a delay. Accessing the HDs is laggy, copying to and from USB devices is slower than before.
 
Any advice to make this as quick as it should be?
 
Cheers
 
 
(When I installed W7 Pro 32bit and all the driver updates, it was super speedy. I dont really want to use Wind*ws if I dont have to, but at these reduced speeds I may have to)


So plenty of reads but no replies! gggrrr

I have now updated to Ubuntu Studio 10.10 64bit, installed 8GB ram and a Quadro FX 370 (The only other card I had lying around)

Blender rendering has reduced from 2:34:12 on 32bit Ubuntu 10.10 with 2GB Ram to 2:15:19

Not much of a difference for 4x the ram and 2.5x the GFX processing!!!

Ubuntu itself now runs like a dream again, very fast GUI, speeds applications etc.

Is there a way of optimizing apps to use the CPU capabilities without re-compiling them?

Cheers

---

### Post by dvdfilmbuff on 2011-02-23
> **dvdfilmbuff said:**
> So plenty of reads but no replies! gggrrr
I have now updated to Ubuntu Studio 10.10 64bit, installed 8GB ram and a Quadro FX 370 (The only other card I had lying around)
Blender rendering has reduced from 2:34:12 on 32bit Ubuntu 10.10 with 2GB Ram to 2:15:19
Not much of a difference for 4x the ram and 2.5x the GFX processing!!!
Ubuntu itself now runs like a dream again, very fast GUI, speeds applications etc.
Is there a way of optimizing apps to use the CPU capabilities without re-compiling them?
Cheers
&#12288;
So I'm back again. With the same question.
 
I have done some tests on another system which is twice the speed, but on paper only has half the spec of my workstation.
 
Test 1: Dell Precision Workstaion 380. Pentium D 3.00ghz Dual Core. 8GB 667 RAM, PCI-e Quadro FX 370 with 256MB Ram, 2 x Segate Barracuda 250GB Sata Drives in Raid 1 stripe, Onboard Sound Driver, Ubuntu Studio 64bit
 
Test 2: Dell Poweredge T105 MiniServer, AMD Opteron 64 Dual Core, 2GB 533 RAM, 256, PCI geForce FX5200 with 256MB Ram, 1 x Segate Barracuda 250GB Sata Drive, USB 5.1 Sound card, Ubuntu Studio 64bit
 
(As much information on each test machine as possible)
 
So I downloaded the test.blend file from [www.eofw.org/bench/test.blend]("http://www.eofw.org/bench/test.blend")
 
I have made sure that Threads is set to 2 on both machines (Both have dual cores so this should be right)
 
Hit F12 to render the 1 static image
 
Results (Including CPUINFO/MEMINFO/DEMSG/LSPCI)
 
Speed test info for Dell Precision Workstation 380
 
```
 
cat /proc/cpuinfo
 
processor : 0
vendor_id : GenuineIntel
cpu family : 15
model : 4
model name : Intel(R) Pentium(R) D CPU 3.00GHz
stepping : 4
cpu MHz : 2992.269
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 2
apicid : 0
initial apicid : 0
fpu : yes
fpu_exception : yes
cpuid level : 5
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
bogomips : 5984.53
clflush size : 64
cache_alignment : 128
address sizes : 36 bits physical, 48 bits virtual
power management:
 
processor : 1
vendor_id : GenuineIntel
cpu family : 15
model : 4
model name : Intel(R) Pentium(R) D CPU 3.00GHz
stepping : 4
cpu MHz : 2992.269
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 1
cpu cores : 2
apicid : 1
initial apicid : 1
fpu : yes
fpu_exception : yes
cpuid level : 5
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
bogomips : 5985.09
clflush size : 64
cache_alignment : 128
address sizes : 36 bits physical, 48 bits virtual
power management:

```&#12288;
 
```

cat /proc/meminfo
 
MemTotal: 8127160 kB
MemFree: 7109324 kB
Buffers: 122072 kB
Cached: 445628 kB
SwapCached: 0 kB
Active: 386128 kB
Inactive: 350444 kB
Active(anon): 169312 kB
Inactive(anon): 3440 kB
Active(file): 216816 kB
Inactive(file): 347004 kB
Unevictable: 0 kB
Mlocked: 0 kB
SwapTotal: 19803644 kB
SwapFree: 19803644 kB
Dirty: 72 kB
Writeback: 0 kB
AnonPages: 169048 kB
Mapped: 63204 kB
Shmem: 3876 kB
Slab: 63600 kB
SReclaimable: 45584 kB
SUnreclaim: 18016 kB
KernelStack: 2080 kB
PageTables: 16292 kB
NFS_Unstable: 0 kB
Bounce: 0 kB
WritebackTmp: 0 kB
CommitLimit: 23867224 kB
Committed_AS: 734852 kB
VmallocTotal: 34359738367 kB
VmallocUsed: 138632 kB
VmallocChunk: 34359583228 kB
HardwareCorrupted: 0 kB
HugePages_Total: 0
HugePages_Free: 0
HugePages_Rsvd: 0
HugePages_Surp: 0
Hugepagesize: 2048 kB
DirectMap4k: 64040 kB
DirectMap2M: 8257536 kB

```
 
```

dmesg
 
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.35-25-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 (Ubuntu 2.6.35-25.44-generic 2.6.35.10)
[ 0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=d9e5773e-b956-40b6-acb5-a41750a1a99d ro quiet splash
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 00000000dfe8ac00 (usable)
[ 0.000000] BIOS-e820: 00000000dfe8ac00 - 00000000dfe8cc00 (ACPI NVS)
[ 0.000000] BIOS-e820: 00000000dfe8cc00 - 00000000dfe8ec00 (ACPI data)
[ 0.000000] BIOS-e820: 00000000dfe8ec00 - 00000000e0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] BIOS-e820: 0000000100000000 - 000000021c000000 (usable)
[ 0.000000] NX (Execute Disable) protection: active
[ 0.000000] DMI 2.3 present.
[ 0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[ 0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[ 0.000000] No AGP bridge found
[ 0.000000] last_pfn = 0x21c000 max_arch_pfn = 0x400000000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-D7FFF write-protect
[ 0.000000] D8000-EFFFF uncachable
[ 0.000000] F0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask F80000000 write-back
[ 0.000000] 1 base 080000000 mask FC0000000 write-back
[ 0.000000] 2 base 0C0000000 mask FE0000000 write-back
[ 0.000000] 3 base 0DFF00000 mask FFFF00000 uncachable
[ 0.000000] 4 base 100000000 mask F00000000 write-back
[ 0.000000] 5 base 200000000 mask FE0000000 write-back
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
[ 0.000000] last_pfn = 0xdfe8a max_arch_pfn = 0x400000000
[ 0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] Scanning 1 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 00000000000a0000 (usable)
[ 0.000000] modified: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 00000000dfe8ac00 (usable)
[ 0.000000] modified: 00000000dfe8ac00 - 00000000dfe8cc00 (ACPI NVS)
[ 0.000000] modified: 00000000dfe8cc00 - 00000000dfe8ec00 (ACPI data)
[ 0.000000] modified: 00000000dfe8ec00 - 00000000e0000000 (reserved)
[ 0.000000] modified: 00000000f0000000 - 00000000f4000000 (reserved)
[ 0.000000] modified: 00000000fec00000 - 00000000fed00400 (reserved)
[ 0.000000] modified: 00000000fed20000 - 00000000feda0000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fef00000 (reserved)
[ 0.000000] modified: 00000000ffb00000 - 0000000100000000 (reserved)
[ 0.000000] modified: 0000000100000000 - 000000021c000000 (usable)
[ 0.000000] initial memory mapped : 0 - 20000000
[ 0.000000] found SMP MP-table at [ffff8800000fe710] fe710
[ 0.000000] init_memory_mapping: 0000000000000000-00000000dfe8a000
[ 0.000000] 0000000000 - 00dfe00000 page 2M
[ 0.000000] 00dfe00000 - 00dfe8a000 page 4k
[ 0.000000] kernel direct mapping tables up to dfe8a000 @ 16000-1c000
[ 0.000000] init_memory_mapping: 0000000100000000-000000021c000000
[ 0.000000] 0100000000 - 021c000000 page 2M
[ 0.000000] kernel direct mapping tables up to 21c000000 @ 1a000-24000
[ 0.000000] RAMDISK: 37536000 - 37ff0000
[ 0.000000] ACPI: RSDP 00000000000feb00 00024 (v02 DELL )
[ 0.000000] ACPI: XSDT 00000000000fd25e 0005C (v01 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: FACP 00000000000fd356 000F4 (v03 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: DSDT 00000000fffcbc59 03112 (v01 DELL dt_ex 00001000 INTL 20050309)
[ 0.000000] ACPI: FACS 00000000dfe8ac00 00040
[ 0.000000] ACPI: SSDT 00000000fffcee8c 000AC (v01 DELL st_ex 00001000 INTL 20050309)
[ 0.000000] ACPI: APIC 00000000000fd44a 00072 (v01 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: BOOT 00000000000fd4bc 00028 (v01 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: ASF! 00000000000fd4e4 00067 (v16 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: MCFG 00000000000fd54b 0003E (v01 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: HPET 00000000000fd589 00038 (v01 DELL WS 380 00000007 ASL 00000061)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] No NUMA configuration found
[ 0.000000] Faking a node at 0000000000000000-000000021c000000
[ 0.000000] Initmem setup node 0 0000000000000000-000000021c000000
[ 0.000000] NODE_DATA [0000000100000000 - 0000000100004fff]
[ 0.000000] [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880100200000-ffff8801073fffff] on node 0
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] DMA32 0x00001000 -> 0x00100000
[ 0.000000] Normal 0x00100000 -> 0x0021c000
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[3] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x000000a0
[ 0.000000] 0: 0x00000100 -> 0x000dfe8a
[ 0.000000] 0: 0x00100000 -> 0x0021c000
[ 0.000000] On node 0 totalpages: 2080282
[ 0.000000] DMA zone: 56 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3928 pages, LIFO batch:0
[ 0.000000] DMA32 zone: 14280 pages used for memmap
[ 0.000000] DMA32 zone: 898754 pages, LIFO batch:31
[ 0.000000] Normal zone: 15904 pages used for memmap
[ 0.000000] Normal zone: 1147360 pages, LIFO batch:31
[ 0.000000] ACPI: PM-Timer IO Port: 0x808
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 40
[ 0.000000] early_res array is doubled to 64 at [1f000 - 1f7ff]
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[ 0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[ 0.000000] PM: Registered nosave memory: 00000000dfe8a000 - 00000000dfe8b000
[ 0.000000] PM: Registered nosave memory: 00000000dfe8b000 - 00000000dfe8c000
[ 0.000000] PM: Registered nosave memory: 00000000dfe8c000 - 00000000dfe8d000
[ 0.000000] PM: Registered nosave memory: 00000000dfe8d000 - 00000000dfe8e000
[ 0.000000] PM: Registered nosave memory: 00000000dfe8e000 - 00000000dfe8f000
[ 0.000000] PM: Registered nosave memory: 00000000dfe8f000 - 00000000e0000000
[ 0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[ 0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[ 0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[ 0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fed00000
[ 0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed20000
[ 0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000feda0000
[ 0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000fee00000
[ 0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[ 0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ffb00000
[ 0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
[ 0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:10000000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[ 0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[ 0.000000] pcpu-alloc: [0] 0 1 2 3
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 2050042
[ 0.000000] Policy zone: Normal
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=d9e5773e-b956-40b6-acb5-a41750a1a99d ro quiet splash
[ 0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[ 0.000000] Checking aperture...
[ 0.000000] No AGP bridge found
[ 0.000000] Calgary: detecting Calgary via BIOS EBDA area
[ 0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[ 0.000000] early_res array is doubled to 128 at [1f800 - 207ff]
[ 0.000000] Subtract (58 early reservations)
[ 0.000000] #1 [0001000000 - 0001d17114] TEXT DATA BSS
[ 0.000000] #2 [0037536000 - 0037ff0000] RAMDISK
[ 0.000000] #3 [0001d18000 - 0001d181d8] BRK
[ 0.000000] #4 [00000fe720 - 0000100000] BIOS reserved
[ 0.000000] #5 [00000fe710 - 00000fe720] MP-table mpf
[ 0.000000] #6 [0000099000 - 00000f0000] BIOS reserved
[ 0.000000] #7 [00000f02b4 - 00000fe710] BIOS reserved
[ 0.000000] #8 [00000f0000 - 00000f02b4] MP-table mpc
[ 0.000000] #9 [0000010000 - 0000012000] TRAMPOLINE
[ 0.000000] #10 [0000012000 - 0000016000] ACPI WAKEUP
[ 0.000000] #11 [0000016000 - 000001a000] PGTABLE
[ 0.000000] #12 [000001a000 - 000001f000] PGTABLE
[ 0.000000] #13 [0100000000 - 0100005000] NODE_DATA
[ 0.000000] #14 [0001d18200 - 0001d19200] BOOTMEM
[ 0.000000] #15 [0001d17140 - 0001d17740] BOOTMEM
[ 0.000000] #16 [0100005000 - 0100006000] BOOTMEM
[ 0.000000] #17 [0100006000 - 0100007000] BOOTMEM
[ 0.000000] #18 [0100200000 - 0107400000] MEMMAP 0
[ 0.000000] #19 [0001d17740 - 0001d178c0] BOOTMEM
[ 0.000000] #20 [0001d19200 - 0001d31200] BOOTMEM
[ 0.000000] #21 [0001d31200 - 0001d49200] BOOTMEM
[ 0.000000] #22 [0001d4a000 - 0001d4b000] BOOTMEM
[ 0.000000] #23 [0001d178c0 - 0001d17901] BOOTMEM
[ 0.000000] #24 [0001d17940 - 0001d17983] BOOTMEM
[ 0.000000] #25 [0001d179c0 - 0001d17c98] BOOTMEM
[ 0.000000] #26 [0001d17cc0 - 0001d17d28] BOOTMEM
[ 0.000000] #27 [0001d17d40 - 0001d17da8] BOOTMEM
[ 0.000000] #28 [0001d17dc0 - 0001d17e28] BOOTMEM
[ 0.000000] #29 [0001d17e40 - 0001d17ea8] BOOTMEM
[ 0.000000] #30 [0001d17ec0 - 0001d17f28] BOOTMEM
[ 0.000000] #31 [0001d17f40 - 0001d17fa8] BOOTMEM
[ 0.000000] #32 [0001d49200 - 0001d49268] BOOTMEM
[ 0.000000] #33 [0001d49280 - 0001d492e8] BOOTMEM
[ 0.000000] #34 [0001d49300 - 0001d49368] BOOTMEM
[ 0.000000] #35 [0001d49380 - 0001d493e8] BOOTMEM
[ 0.000000] #36 [0001d49400 - 0001d49468] BOOTMEM
[ 0.000000] #37 [0001d49480 - 0001d494e8] BOOTMEM
[ 0.000000] #38 [0001d17fc0 - 0001d17fe0] BOOTMEM
[ 0.000000] #39 [0001d49500 - 0001d49520] BOOTMEM
[ 0.000000] #40 [0001d49540 - 0001d495aa] BOOTMEM
[ 0.000000] #41 [0001d495c0 - 0001d4962a] BOOTMEM
[ 0.000000] #42 [0001e00000 - 0001e1e000] BOOTMEM
[ 0.000000] #43 [0001e80000 - 0001e9e000] BOOTMEM
[ 0.000000] #44 [0001f00000 - 0001f1e000] BOOTMEM
[ 0.000000] #45 [0001f80000 - 0001f9e000] BOOTMEM
[ 0.000000] #46 [0001d49640 - 0001d49648] BOOTMEM
[ 0.000000] #47 [0001d49680 - 0001d49688] BOOTMEM
[ 0.000000] #48 [0001d496c0 - 0001d496d0] BOOTMEM
[ 0.000000] #49 [0001d49700 - 0001d49720] BOOTMEM
[ 0.000000] #50 [0001d49740 - 0001d49870] BOOTMEM
[ 0.000000] #51 [0001d49880 - 0001d498d0] BOOTMEM
[ 0.000000] #52 [0001d49900 - 0001d49950] BOOTMEM
[ 0.000000] #53 [0001d4b000 - 0001d53000] BOOTMEM
[ 0.000000] #54 [0001f9e000 - 0005f9e000] BOOTMEM
[ 0.000000] #55 [0001d53000 - 0001d73000] BOOTMEM
[ 0.000000] #56 [0001d73000 - 0001db3000] BOOTMEM
[ 0.000000] #57 [0000020800 - 0000028800] BOOTMEM
[ 0.000000] Memory: 8113212k/8847360k available (5714k kernel code, 526232k absent, 207916k reserved, 5377k data, 908k init)
[ 0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] RCU dyntick-idle grace-period acceleration is enabled.
[ 0.000000] RCU-based detection of stalled CPUs is disabled.
[ 0.000000] Verbose stalled-CPUs detection is disabled.
[ 0.000000] NR_IRQS:4352 nr_irqs:712
[ 0.000000] Console: colour VGA+ 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] allocated 83886080 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] hpet clockevent registered
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 2992.269 MHz processor.
[ 0.010011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.53 BogoMIPS (lpj=29922690)
[ 0.010017] pid_max: default: 32768 minimum: 301
[ 0.010048] Security Framework initialized
[ 0.010075] AppArmor: AppArmor initialized
[ 0.010078] Yama: becoming mindful.
[ 0.012089] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[ 0.022905] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[ 0.024665] Mount-cache hash table entries: 256
[ 0.024860] Initializing cgroup subsys ns
[ 0.024867] Initializing cgroup subsys cpuacct
[ 0.024872] Initializing cgroup subsys memory
[ 0.024883] Initializing cgroup subsys devices
[ 0.024887] Initializing cgroup subsys freezer
[ 0.024890] Initializing cgroup subsys net_cls
[ 0.024933] CPU: Physical Processor ID: 0
[ 0.024936] CPU: Processor Core ID: 0
[ 0.024939] mce: CPU supports 4 MCE banks
[ 0.024954] CPU0: Thermal monitoring enabled (TM1)
[ 0.024960] using mwait in idle threads.
[ 0.024963] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[ 0.024971] ... version: 0
[ 0.024974] ... bit width: 40
[ 0.024976] ... generic registers: 18
[ 0.024978] ... value mask: 000000ffffffffff
[ 0.024981] ... max period: 0000007fffffffff
[ 0.024983] ... fixed-purpose events: 0
[ 0.024985] ... event mask: 000000000003ffff
[ 0.028020] ACPI: Core revision 20100428
[ 0.100702] ftrace: converting mcount calls to 0f 1f 44 00 00
[ 0.100709] ftrace: allocating 22681 entries in 89 pages
[ 0.110075] Setting APIC routing to flat
[ 0.110405] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.215009] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 04
[ 0.220000] Booting Node 0, Processors #1
[ 0.380015] Brought up 2 CPUs
[ 0.380020] Total of 2 processors activated (11969.63 BogoMIPS).
[ 0.380454] devtmpfs: initialized
[ 0.381071] regulator: core version 0.5
[ 0.381099] Time: 7:03:17 Date: 02/23/11
[ 0.381152] NET: Registered protocol family 16
[ 0.381193] Trying to unpack rootfs image as initramfs...
[ 0.381373] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[ 0.381377] ACPI: bus type pci registered
[ 0.381461] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[ 0.381466] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[ 0.394906] PCI: Using configuration type 1 for base access
[ 0.410349] bio: create slab <bio-0> at 0
[ 0.411169] ACPI: EC: Look up EC in DSDT
[ 0.429451] ACPI: BIOS _OSI(Linux) query ignored
[ 0.441297] ACPI: Interpreter enabled
[ 0.441302] ACPI: (supports S0 S1 S3 S4 S5)
[ 0.441333] ACPI: Using IOAPIC for interrupt routing
[ 0.502486] ACPI: No dock devices found.
[ 0.502492] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[ 0.507974] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[ 0.518919] pci_root PNP0A03:00: host bridge window [io 0x0000-0x0cf7] (ignored)
[ 0.518923] pci_root PNP0A03:00: host bridge window [io 0x0d00-0xffff] (ignored)
[ 0.518927] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[ 0.518931] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000effff] (ignored)
[ 0.518934] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[ 0.518938] pci_root PNP0A03:00: host bridge window [mem 0xdff00000-0xefffffff] (ignored)
[ 0.518941] pci_root PNP0A03:00: host bridge window [mem 0xf4000000-0xfebfffff] (ignored)
[ 0.518944] pci_root PNP0A03:00: host bridge window [mem 0xffa80800-0xffa80bff] (ignored)
[ 0.518948] pci_root PNP0A03:00: host bridge window [mem 0xffa7c000-0xffa7ffff] (ignored)
[ 0.519050] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[ 0.519055] pci 0000:00:01.0: PME# disabled
[ 0.519127] pci 0000:00:1b.0: reg 10: [mem 0xfebfc000-0xfebfffff 64bit]
[ 0.519179] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.519184] pci 0000:00:1b.0: PME# disabled
[ 0.519264] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.519269] pci 0000:00:1c.0: PME# disabled
[ 0.519351] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[ 0.519356] pci 0000:00:1c.4: PME# disabled
[ 0.519435] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[ 0.519440] pci 0000:00:1c.5: PME# disabled
[ 0.519494] pci 0000:00:1d.0: reg 20: [io 0xff80-0xff9f]
[ 0.519552] pci 0000:00:1d.1: reg 20: [io 0xff60-0xff7f]
[ 0.519607] pci 0000:00:1d.2: reg 20: [io 0xff40-0xff5f]
[ 0.519662] pci 0000:00:1d.3: reg 20: [io 0xff20-0xff3f]
[ 0.519722] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[ 0.519782] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.519788] pci 0000:00:1d.7: PME# disabled
[ 0.519921] pci 0000:00:1f.0: quirk: [io 0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[ 0.519926] pci 0000:00:1f.0: quirk: [io 0x0880-0x08bf] claimed by ICH6 GPIO
[ 0.519931] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0c00 (mask 007f)
[ 0.519936] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 00e0 (mask 0007)
[ 0.519984] pci 0000:00:1f.1: reg 10: [io 0x01f0-0x01f7]
[ 0.520007] pci 0000:00:1f.1: reg 14: [io 0x03f4-0x03f7]
[ 0.520015] pci 0000:00:1f.1: reg 18: [io 0x0170-0x0177]
[ 0.520023] pci 0000:00:1f.1: reg 1c: [io 0x0374-0x0377]
[ 0.520031] pci 0000:00:1f.1: reg 20: [io 0xffa0-0xffaf]
[ 0.520083] pci 0000:00:1f.2: reg 10: [io 0xfe00-0xfe07]
[ 0.520091] pci 0000:00:1f.2: reg 14: [io 0xfe10-0xfe13]
[ 0.520097] pci 0000:00:1f.2: reg 18: [io 0xfe20-0xfe27]
[ 0.520104] pci 0000:00:1f.2: reg 1c: [io 0xfe30-0xfe33]
[ 0.520110] pci 0000:00:1f.2: reg 20: [io 0xfea0-0xfeaf]
[ 0.520117] pci 0000:00:1f.2: reg 24: [mem 0xfebfbc00-0xfebfbfff]
[ 0.520147] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.520151] pci 0000:00:1f.2: PME# disabled
[ 0.520203] pci 0000:00:1f.3: reg 20: [io 0xece0-0xecff]
[ 0.520291] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[ 0.520302] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[ 0.520313] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[ 0.520321] pci 0000:01:00.0: reg 24: [io 0xdc80-0xdcff]
[ 0.520328] pci 0000:01:00.0: reg 30: [mem 0xfea00000-0xfea1ffff pref]
[ 0.520372] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[ 0.520377] pci 0000:00:01.0: bridge window [io 0xd000-0xdfff]
[ 0.520382] pci 0000:00:01.0: bridge window [mem 0xfa000000-0xfeafffff]
[ 0.520388] pci 0000:00:01.0: bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[ 0.520437] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[ 0.520443] pci 0000:00:1c.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.520448] pci 0000:00:1c.0: bridge window [mem 0xf9f00000-0xf9ffffff]
[ 0.520456] pci 0000:00:1c.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.520504] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[ 0.520509] pci 0000:00:1c.4: bridge window [io 0xf000-0x0000] (disabled)
[ 0.520514] pci 0000:00:1c.4: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.520522] pci 0000:00:1c.4: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.520614] pci 0000:04:00.0: reg 10: [mem 0xf9ef0000-0xf9efffff 64bit]
[ 0.520695] pci 0000:04:00.0: PME# supported from D3hot D3cold
[ 0.520701] pci 0000:04:00.0: PME# disabled
[ 0.520720] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device. You can enable it with 'pcie_aspm=force'
[ 0.520725] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[ 0.520731] pci 0000:00:1c.5: bridge window [io 0xf000-0x0000] (disabled)
[ 0.520736] pci 0000:00:1c.5: bridge window [mem 0xf9e00000-0xf9efffff]
[ 0.520743] pci 0000:00:1c.5: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.520817] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[ 0.520822] pci 0000:00:1e.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.520827] pci 0000:00:1e.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.520835] pci 0000:00:1e.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.520838] pci 0000:00:1e.0: bridge window [io 0x0000-0xffff] (subtractive decode)
[ 0.520841] pci 0000:00:1e.0: bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[ 0.520870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.521287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[ 0.521707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[ 0.521998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[ 0.522236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[ 0.522497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI6._PRT]
[ 1.024169] Freeing initrd memory: 10984k freed
[ 1.102331] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[ 1.102757] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[ 1.103201] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[ 1.103642] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[ 1.104066] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[ 1.104531] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[ 1.104960] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[ 1.105393] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[ 1.105526] HEST: Table is not found!
[ 1.105646] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[ 1.105651] vgaarb: loaded
[ 1.105845] SCSI subsystem initialized
[ 1.105897] libata version 3.00 loaded.
[ 1.105897] usbcore: registered new interface driver usbfs
[ 1.105897] usbcore: registered new interface driver hub
[ 1.105897] usbcore: registered new device driver usb
[ 1.105897] ACPI: WMI: Mapper loaded
[ 1.105897] PCI: Using ACPI for IRQ routing
[ 1.105897] PCI: pci_cache_line_size set to 64 bytes
[ 1.105897] reserve RAM buffer: 00000000dfe8ac00 - 00000000dfffffff
[ 1.105897] NetLabel: Initializing
[ 1.105897] NetLabel: domain hash size = 128
[ 1.105897] NetLabel: protocols = UNLABELED CIPSOv4
[ 1.105897] NetLabel: unlabeled traffic allowed by default
[ 1.105897] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 1.105897] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 1.105897] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 1.110024] Switching to clocksource tsc
[ 1.122336] AppArmor: AppArmor Filesystem Enabled
[ 1.122358] pnp: PnP ACPI init
[ 1.122381] ACPI: bus type pnp registered
[ 1.130551] pnp 00:01: disabling [io 0x0800-0x085f] because it overlaps 0000:00:1f.0 BAR 13 [io 0x0800-0x087f]
[ 1.130556] pnp 00:01: disabling [io 0x0860-0x08ff] because it overlaps 0000:00:1f.0 BAR 13 [io 0x0800-0x087f]
[ 1.159727] pnp: PnP ACPI: found 11 devices
[ 1.159730] ACPI: ACPI bus type pnp unregistered
[ 1.159746] system 00:01: [io 0x0c00-0x0c7f] has been reserved
[ 1.159758] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[ 1.159762] system 00:09: [mem 0x00100000-0x00ffffff] could not be reserved
[ 1.159766] system 00:09: [mem 0x01000000-0xdfe8abff] could not be reserved
[ 1.159770] system 00:09: [mem 0x000f0000-0x000fffff] could not be reserved
[ 1.159773] system 00:09: [mem 0x000c0000-0x000d7fff] has been reserved
[ 1.159777] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[ 1.159781] system 00:09: [mem 0xfee00000-0xfeefffff] has been reserved
[ 1.159784] system 00:09: [mem 0xfed20000-0xfed9ffff] has been reserved
[ 1.159788] system 00:09: [mem 0xffb00000-0xffbfffff] has been reserved
[ 1.159791] system 00:09: [mem 0xffc00000-0xffffffff] has been reserved
[ 1.159798] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[ 1.159802] system 00:0a: [mem 0xfeda0000-0xfedacfff] has been reserved
[ 1.166440] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf4000000-0xf41fffff 64bit pref]
[ 1.166446] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf4200000-0xf43fffff]
[ 1.166451] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf4400000-0xf45fffff 64bit pref]
[ 1.166455] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf4600000-0xf47fffff 64bit pref]
[ 1.166459] pci 0000:00:1c.0: BAR 13: assigned [io 0x1000-0x1fff]
[ 1.166462] pci 0000:00:1c.4: BAR 13: assigned [io 0x2000-0x2fff]
[ 1.166466] pci 0000:00:1c.5: BAR 13: assigned [io 0x3000-0x3fff]
[ 1.166470] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[ 1.166473] pci 0000:00:01.0: bridge window [io 0xd000-0xdfff]
[ 1.166479] pci 0000:00:01.0: bridge window [mem 0xfa000000-0xfeafffff]
[ 1.166483] pci 0000:00:01.0: bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[ 1.166489] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[ 1.166493] pci 0000:00:1c.0: bridge window [io 0x1000-0x1fff]
[ 1.166499] pci 0000:00:1c.0: bridge window [mem 0xf9f00000-0xf9ffffff]
[ 1.166504] pci 0000:00:1c.0: bridge window [mem 0xf4000000-0xf41fffff 64bit pref]
[ 1.166511] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[ 1.166515] pci 0000:00:1c.4: bridge window [io 0x2000-0x2fff]
[ 1.166521] pci 0000:00:1c.4: bridge window [mem 0xf4200000-0xf43fffff]
[ 1.166526] pci 0000:00:1c.4: bridge window [mem 0xf4400000-0xf45fffff 64bit pref]
[ 1.166533] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[ 1.166537] pci 0000:00:1c.5: bridge window [io 0x3000-0x3fff]
[ 1.166542] pci 0000:00:1c.5: bridge window [mem 0xf9e00000-0xf9efffff]
[ 1.166548] pci 0000:00:1c.5: bridge window [mem 0xf4600000-0xf47fffff 64bit pref]
[ 1.166555] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[ 1.166557] pci 0000:00:1e.0: bridge window [io disabled]
[ 1.166563] pci 0000:00:1e.0: bridge window [mem disabled]
[ 1.166568] pci 0000:00:1e.0: bridge window [mem pref disabled]
[ 1.166585] alloc irq_desc for 16 on node -1
[ 1.166588] alloc kstat_irqs on node -1
[ 1.166597] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.166603] pci 0000:00:01.0: setting latency timer to 64
[ 1.166615] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.166620] pci 0000:00:1c.0: setting latency timer to 64
[ 1.166629] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.166634] pci 0000:00:1c.4: setting latency timer to 64
[ 1.166644] alloc irq_desc for 17 on node -1
[ 1.166646] alloc kstat_irqs on node -1
[ 1.166652] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 1.166657] pci 0000:00:1c.5: setting latency timer to 64
[ 1.166665] pci 0000:00:1e.0: setting latency timer to 64
[ 1.166670] pci_bus 0000:00: resource 0 [io 0x0000-0xffff]
[ 1.166674] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[ 1.166677] pci_bus 0000:01: resource 0 [io 0xd000-0xdfff]
[ 1.166680] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
[ 1.166683] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[ 1.166687] pci_bus 0000:02: resource 0 [io 0x1000-0x1fff]
[ 1.166689] pci_bus 0000:02: resource 1 [mem 0xf9f00000-0xf9ffffff]
[ 1.166692] pci_bus 0000:02: resource 2 [mem 0xf4000000-0xf41fffff 64bit pref]
[ 1.166696] pci_bus 0000:03: resource 0 [io 0x2000-0x2fff]
[ 1.166699] pci_bus 0000:03: resource 1 [mem 0xf4200000-0xf43fffff]
[ 1.166702] pci_bus 0000:03: resource 2 [mem 0xf4400000-0xf45fffff 64bit pref]
[ 1.166705] pci_bus 0000:04: resource 0 [io 0x3000-0x3fff]
[ 1.166708] pci_bus 0000:04: resource 1 [mem 0xf9e00000-0xf9efffff]
[ 1.166711] pci_bus 0000:04: resource 2 [mem 0xf4600000-0xf47fffff 64bit pref]
[ 1.166714] pci_bus 0000:05: resource 4 [io 0x0000-0xffff]
[ 1.166717] pci_bus 0000:05: resource 5 [mem 0x00000000-0xffffffffffffffff]
[ 1.166762] NET: Registered protocol family 2
[ 1.167277] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[ 1.170172] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[ 1.173826] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[ 1.174256] TCP: Hash tables configured (established 524288 bind 65536)
[ 1.174260] TCP reno registered
[ 1.174305] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[ 1.174393] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[ 1.174583] NET: Registered protocol family 1
[ 1.174744] pci 0000:01:00.0: Boot video device
[ 1.174753] PCI: CLS 64 bytes, default 64
[ 1.174756] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[ 1.174760] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[ 1.174763] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[ 1.174809] Simple Boot Flag at 0x7a set to 0x1
[ 1.175034] Scanning for low memory corruption every 60 seconds
[ 1.175238] audit: initializing netlink socket (disabled)
[ 1.175251] type=2000 audit(1298444597.170:1): initialized
[ 1.189337] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[ 1.191197] VFS: Disk quotas dquot_6.5.2
[ 1.191276] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[ 1.192141] fuse init (API version 7.14)
[ 1.192254] msgmni has been set to 15867
[ 1.195766] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 1.195771] io scheduler noop registered
[ 1.195774] io scheduler deadline registered
[ 1.195830] io scheduler cfq registered (default)
[ 1.195965] pcieport 0000:00:01.0: setting latency timer to 64
[ 1.195998] alloc irq_desc for 40 on node -1
[ 1.196000] alloc kstat_irqs on node -1
[ 1.196013] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[ 1.196095] pcieport 0000:00:1c.0: setting latency timer to 64
[ 1.196132] alloc irq_desc for 41 on node -1
[ 1.196134] alloc kstat_irqs on node -1
[ 1.196143] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[ 1.196244] pcieport 0000:00:1c.4: setting latency timer to 64
[ 1.196280] alloc irq_desc for 42 on node -1
[ 1.196282] alloc kstat_irqs on node -1
[ 1.196291] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[ 1.196398] pcieport 0000:00:1c.5: setting latency timer to 64
[ 1.196434] alloc irq_desc for 43 on node -1
[ 1.196436] alloc kstat_irqs on node -1
[ 1.196445] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[ 1.196573] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.196696] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.196924] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[ 1.196932] ACPI: Power Button [VBTN]
[ 1.197000] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[ 1.197005] ACPI: Power Button [PWRF]
[ 1.197826] ACPI: acpi_idle registered with cpuidle
[ 1.247596] ERST: Table is not found!
[ 1.247756] Linux agpgart interface v0.103
[ 1.247787] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 1.247904] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.248308] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.249767] brd: module loaded
[ 1.250456] loop: module loaded
[ 1.250714] ata_piix 0000:00:1f.1: version 2.13
[ 1.250730] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.250775] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 1.250898] scsi0 : ata_piix
[ 1.251000] scsi1 : ata_piix
[ 1.251053] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 1.251057] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[ 1.251249] ata2: port disabled. ignoring.
[ 1.251536] Fixed MDIO Bus: probed
[ 1.251581] PPP generic driver version 2.4.2
[ 1.251651] tun: Universal TUN/TAP device driver, 1.6
[ 1.251654] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1.251774] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.251798] alloc irq_desc for 21 on node -1
[ 1.251801] alloc kstat_irqs on node -1
[ 1.251810] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 1.251845] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 1.251850] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 1.251893] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 1.251919] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[ 1.251931] ehci_hcd 0000:00:1d.7: debug port 1
[ 1.255829] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[ 1.255851] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[ 1.270015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 1.270179] hub 1-0:1.0: USB hub found
[ 1.270186] hub 1-0:1.0: 8 ports detected
[ 1.270287] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.270305] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.270384] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 1.270394] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1.270398] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 1.270451] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1.270477] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[ 1.270629] hub 2-0:1.0: USB hub found
[ 1.270636] hub 2-0:1.0: 2 ports detected
[ 1.270708] alloc irq_desc for 22 on node -1
[ 1.270711] alloc kstat_irqs on node -1
[ 1.270717] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[ 1.270728] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1.270732] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 1.270777] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 1.270812] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[ 1.270959] hub 3-0:1.0: USB hub found
[ 1.270965] hub 3-0:1.0: 2 ports detected
[ 1.271037] alloc irq_desc for 18 on node -1
[ 1.271040] alloc kstat_irqs on node -1
[ 1.271046] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1.271053] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1.271057] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 1.271104] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 1.271138] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[ 1.271282] hub 4-0:1.0: USB hub found
[ 1.271288] hub 4-0:1.0: 2 ports detected
[ 1.271361] alloc irq_desc for 23 on node -1
[ 1.271364] alloc kstat_irqs on node -1
[ 1.271370] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 1.271377] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 1.271381] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 1.271425] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 1.271460] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[ 1.271607] hub 5-0:1.0: USB hub found
[ 1.271613] hub 5-0:1.0: 2 ports detected
[ 1.271761] PNP: No PS/2 controller found. Probing ports directly.
[ 1.274530] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.274539] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.274652] mice: PS/2 mouse device common for all mice
[ 1.274794] rtc_cmos 00:05: RTC can wake from S4
[ 1.274844] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[ 1.274871] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[ 1.275016] device-mapper: uevent: version 1.0.3
[ 1.275120] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 1.275228] device-mapper: multipath: version 1.1.1 loaded
[ 1.275232] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 1.275497] cpuidle: using governor ladder
[ 1.275500] cpuidle: using governor menu
[ 1.275905] TCP cubic registered
[ 1.276081] NET: Registered protocol family 10
[ 1.276542] lo: Disabled Privacy Extensions
[ 1.276820] NET: Registered protocol family 17
[ 1.276995] PM: Resume from disk failed.
[ 1.277010] registered taskstats version 1
[ 1.277274] Magic number: 15:954:66
[ 1.277363] rtc_cmos 00:05: setting system clock to 2011-02-23 07:03:17 UTC (1298444597)
[ 1.277367] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.277369] EDD information not available.
[ 1.450408] ata1.00: ATAPI: HL-DT-STDVD+-RW GSA-H21L, W516, max UDMA/44
[ 1.450438] ata1.01: ATAPI: PHILIPS DVD+/-RW DVD8701, 5D24, max UDMA/33
[ 1.490311] ata1.00: configured for UDMA/44
[ 1.530616] ata1.01: configured for UDMA/33
[ 1.534111] scsi 0:0:0:0: CD-ROM HL-DT-ST DVD+-RW GSA-H21L W516 PQ: 0 ANSI: 5
[ 1.539227] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[ 1.539232] Uniform CD-ROM driver Revision: 3.20
[ 1.539373] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 1.539446] sr 0:0:0:0: Attached scsi generic sg0 type 5
[ 1.541712] scsi 0:0:1:0: CD-ROM PHILIPS DVD+-RW DVD8701 5D24 PQ: 0 ANSI: 5
[ 1.549220] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[ 1.549338] sr 0:0:1:0: Attached scsi CD-ROM sr1
[ 1.549400] sr 0:0:1:0: Attached scsi generic sg1 type 5
[ 1.549479] Freeing unused kernel memory: 908k freed
[ 1.549869] Write protecting the kernel read-only data: 10240k
[ 1.550094] Freeing unused kernel memory: 412k freed
[ 1.550478] Freeing unused kernel memory: 1644k freed
[ 1.575744] udev[77]: starting version 163
[ 1.664091] tg3.c:v3.110 (April 9, 2010)
[ 1.664115] tg3 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1.664127] tg3 0000:04:00.0: setting latency timer to 64
[ 1.700663] ahci 0000:00:1f.2: version 3.0
[ 1.700686] alloc irq_desc for 20 on node -1
[ 1.700689] alloc kstat_irqs on node -1
[ 1.700700] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[ 1.700765] alloc irq_desc for 44 on node -1
[ 1.700768] alloc kstat_irqs on node -1
[ 1.700779] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[ 1.700854] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[ 1.700859] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
[ 1.700866] ahci 0000:00:1f.2: setting latency timer to 64
[ 1.704705] scsi2 : ahci
[ 1.704911] scsi3 : ahci
[ 1.705069] scsi4 : ahci
[ 1.705200] scsi5 : ahci
[ 1.705265] ata3: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd00 irq 44
[ 1.705270] ata4: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd80 irq 44
[ 1.705274] ata5: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbe00 irq 44
[ 1.705278] ata6: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbe80 irq 44
[ 1.708425] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM5751PKFBG) rev 4001] (PCI Express) MAC address 00:12:3f:73:06:a8
[ 1.708432] tg3 0000:04:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[ 1.708437] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[ 1.708441] tg3 0000:04:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[ 1.711486] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 1.721660] Floppy drive(s): fd0 is 1.44M
[ 1.723831] xor: automatically using best checksumming function: generic_sse
[ 1.770008] generic_sse: 4608.000 MB/sec
[ 1.770011] xor: using function: generic_sse (4608.000 MB/sec)
[ 1.772055] FDC 0 is a post-1991 82077
[ 1.860837] hub 1-5:1.0: USB hub found
[ 1.860949] hub 1-5:1.0: 4 ports detected
[ 1.980020] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 2.050034] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2.050059] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2.050076] ata4: SATA link down (SStatus 0 SControl 300)
[ 2.050098] ata6: SATA link down (SStatus 0 SControl 300)
[ 2.050864] ata5.00: ATA-8: ST3250318AS, HP34, max UDMA/100
[ 2.050868] ata5.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[ 2.050918] ata3.00: ATA-8: ST3250318AS, HP34, max UDMA/100
[ 2.050926] ata3.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[ 2.051906] ata5.00: configured for UDMA/100
[ 2.051972] ata3.00: configured for UDMA/100
[ 2.070159] scsi 2:0:0:0: Direct-Access ATA ST3250318AS HP34 PQ: 0 ANSI: 5
[ 2.070363] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 2.070572] scsi 4:0:0:0: Direct-Access ATA ST3250318AS HP34 PQ: 0 ANSI: 5
[ 2.070738] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 2.070848] sd 4:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 2.070893] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 2.070941] sd 4:0:0:0: [sdb] Write Protect is off
[ 2.070945] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 2.070984] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.070996] sd 2:0:0:0: [sda] Write Protect is off
[ 2.071001] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.071039] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.071338] sda:
[ 2.071657] sdb: sda1 sda2 < >
[ 2.082115] sda: partition table partially beyond EOD, enabling native capacity
[ 2.082327] sda: sdb1
[ 2.082761] sda1 sda2 < >
[ 2.082768] sda: partition table partially beyond EOD, truncated
[ 2.082775] sda: p1 size 937175552 extends beyond EOD, truncated
[ 2.082836] sda: p2 start 937176574 is beyond EOD, truncated
[ 2.083090] sd 2:0:0:0: [sda] Attached SCSI disk
[ 2.083225] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 2.089847] device-mapper: dm-raid45: initialized v0.2594b
[ 2.420096] usb 2-1: new low speed USB device using uhci_hcd and address 2
[ 2.631575] usbcore: registered new interface driver hiddev
[ 2.646978] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
[ 2.647161] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1/input0
[ 2.647257] usbcore: registered new interface driver usbhid
[ 2.647260] usbhid: USB HID core driver
[ 2.713505] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[ 2.890078] usb 2-2: new low speed USB device using uhci_hcd and address 3
[ 3.092889] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
[ 3.093011] generic-usb 0003:046D:C016.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-2/input0
[ 3.170194] usb 1-5.3: new high speed USB device using ehci_hcd and address 6
[ 3.280971] hub 1-5.3:1.0: USB hub found
[ 3.281057] hub 1-5.3:1.0: 4 ports detected
[ 3.360070] usb 1-5.4: new high speed USB device using ehci_hcd and address 7
[ 3.470738] hub 1-5.4:1.0: USB hub found
[ 3.470822] hub 1-5.4:1.0: 4 ports detected
[ 3.560095] usb 1-5.3.3: new high speed USB device using ehci_hcd and address 8
[ 8.849527] udev[385]: starting version 163
[ 8.946059] intel_rng: Firmware space is locked read-only. If you can't or
[ 8.946062] intel_rng: don't want to disable this in firmware setup, and if
[ 8.946063] intel_rng: you are certain that your system has a functional
[ 8.946065] intel_rng: RNG, try using the 'no_fwh_detect' option.
[ 8.994438] leds_ss4200: no LED devices found
[ 9.013193] lp: driver loaded but no devices found
[ 9.016529] Adding 19803644k swap on /dev/mapper/isw_echfagdbdc_CGIStripe5. Priority:-1 extents:1 across:19803644k
[ 9.212173] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[ 9.213196] dell-wmi-aio: No known WMI GUID found
[ 9.226101] parport_pc 00:07: reported by Plug and Play ACPI
[ 9.226161] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[ 9.227906] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[ 9.269011] type=1400 audit(1298444605.480:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=587 comm="apparmor_parser"
[ 9.269725] type=1400 audit(1298444605.480:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=587 comm="apparmor_parser"
[ 9.270219] type=1400 audit(1298444605.480:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=587 comm="apparmor_parser"
[ 9.275251] Linux video capture interface: v2.00
[ 9.279912] uvcvideo: Found UVC 1.00 device MicrosoftÂ® LifeCam Cinema(TM) (045e:075d)
[ 9.293190] input: MicrosoftÂ® LifeCam Cinema(TM) as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input4
[ 9.293761] usbcore: registered new interface driver uvcvideo
[ 9.293766] USB Video Class driver (v0.1.0)
[ 9.301122] Initializing USB Mass Storage driver...
[ 9.301512] lp0: using parport0 (interrupt-driven).
[ 9.340967] nvidia: module license 'NVIDIA' taints kernel.
[ 9.340972] Disabling lock debugging due to kernel taint
[ 9.342830] scsi6 : usb-storage 1-5.3.3:1.0
[ 9.377393] usbcore: registered new interface driver usb-storage
[ 9.377398] USB Mass Storage support registered.
[ 9.573647] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 9.573737] alloc irq_desc for 45 on node -1
[ 9.573740] alloc kstat_irqs on node -1
[ 9.573754] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[ 9.573785] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 9.791668] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[ 9.791777] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[ 9.791854] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[ 9.791931] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[ 9.792011] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[ 9.802086] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9.922766] ppdev: user-space parallel port driver
[ 9.989321] type=1400 audit(1298444606.200:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=882 comm="apparmor_parser"
[ 9.999869] type=1400 audit(1298444606.210:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=884 comm="apparmor_parser"
[ 10.008949] type=1400 audit(1298444606.220:7): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=884 comm="apparmor_parser"
[ 10.014632] type=1400 audit(1298444606.230:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=884 comm="apparmor_parser"
[ 10.025430] type=1400 audit(1298444606.240:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=886 comm="apparmor_parser"
[ 10.026297] type=1400 audit(1298444606.240:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=886 comm="apparmor_parser"
[ 10.030155] type=1400 audit(1298444606.240:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=887 comm="apparmor_parser"
[ 10.382650] scsi 6:0:0:0: Direct-Access USB2.0 CardReader CF 0100 PQ: 0 ANSI: 0
[ 10.398279] scsi 6:0:0:1: Direct-Access USB2.0 CardReader SM XD 0100 PQ: 0 ANSI: 0
[ 10.398753] scsi 6:0:0:2: Direct-Access USB2.0 CardReader MS 0100 PQ: 0 ANSI: 0
[ 10.399126] scsi 6:0:0:3: Direct-Access USB2.0 CardReader SD 0100 PQ: 0 ANSI: 0
[ 10.399710] sd 6:0:0:0: Attached scsi generic sg4 type 0
[ 10.399890] sd 6:0:0:1: Attached scsi generic sg5 type 0
[ 10.400065] sd 6:0:0:2: Attached scsi generic sg6 type 0
[ 10.400240] sd 6:0:0:3: Attached scsi generic sg7 type 0
[ 10.407561] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 10.407574] nvidia 0000:01:00.0: setting latency timer to 64
[ 10.407581] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[ 10.407994] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 260.19.06 Mon Sep 13 04:29:19 PDT 2010
[ 10.415905] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 10.421520] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[ 10.422263] sd 6:0:0:2: [sde] Attached SCSI removable disk
[ 10.423000] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[ 10.791409] 5:3:1: cannot get freq at ep 0x82
[ 10.796755] usbcore: registered new interface driver snd-usb-audio
[ 11.460789] tg3 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex
[ 11.460794] tg3 0000:04:00.0: eth0: Flow control is on for TX and on for RX
[ 11.461783] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 12.287995] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[ 16.055506] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[ 16.060189] 5:3:1: cannot get freq at ep 0x82
[ 17.190144] 5:3:1: cannot get freq at ep 0x82
[ 22.260008] eth0: no IPv6 routers present
[ 48.700091] 5:3:1: cannot get freq at ep 0x82
[ 49.830184] 5:3:1: cannot get freq at ep 0x82
[ 97.660046] usb 1-8: new high speed USB device using ehci_hcd and address 9
[ 97.811428] scsi7 : usb-storage 1-8:1.0
[ 98.810875] scsi 7:0:0:0: Direct-Access Seagate Portable 0130 PQ: 0 ANSI: 4
[ 98.813291] sd 7:0:0:0: Attached scsi generic sg8 type 0
[ 98.814101] sd 7:0:0:0: [sdg] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 98.814719] sd 7:0:0:0: [sdg] Write Protect is off
[ 98.814724] sd 7:0:0:0: [sdg] Mode Sense: 2f 08 00 00
[ 98.814728] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 98.817233] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 98.817245] sdg: sdg1
[ 98.890362] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 98.890369] sd 7:0:0:0: [sdg] Attached SCSI disk
[ 563.977068] usb 1-8: USB disconnect, address 9
[ 827.890024] usb 1-8: new high speed USB device using ehci_hcd and address 10
[ 828.041748] scsi8 : usb-storage 1-8:1.0
[ 829.040606] scsi 8:0:0:0: Direct-Access Seagate Portable 0130 PQ: 0 ANSI: 4
[ 829.041437] sd 8:0:0:0: Attached scsi generic sg8 type 0
[ 829.042852] sd 8:0:0:0: [sdg] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 829.044501] sd 8:0:0:0: [sdg] Write Protect is off
[ 829.044507] sd 8:0:0:0: [sdg] Mode Sense: 2f 08 00 00
[ 829.044510] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 829.046605] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 829.046615] sdg: sdg1
[ 829.119988] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 829.119995] sd 8:0:0:0: [sdg] Attached SCSI disk

```
 
```

lspci
 
00:00.0 Host bridge: Intel Corporation 82955X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82955X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G84 [Quadro FX 370] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

```
&#12288;
```

Blender test:
 
Threads = 2
Test.Blend: 02:12:64
 
Threads = 1
Test.Blend: 04:09:32
 
Blender System Info
 
=====================================
= Blender 2.49 System Information =
=====================================
&#12288;
Built on 2010-09-04 06:52:05, Rev- Version linux2 dynamic
Platform: linux2
========
Python:
======
- Version: 2.6.6 (r266:84292, Sep 15 2010, 16:41:53)
[GCC 4.4.5]
- Paths:
/usr/lib/python2.6
/usr/lib/python2.6/plat-linux2
/usr/lib/python2.6/lib-tk
/usr/lib/python2.6/lib-old
/usr/lib/python2.6/lib-dynload
/usr/local/lib/python2.6/dist-packages
/usr/lib/python2.6/dist-packages
/usr/lib/python2.6/dist-packages/PIL
/usr/lib/python2.6/dist-packages/gst-0.10
/usr/lib/pymodules/python2.6
/usr/lib/pymodules/python2.6/gtk-2.0
/usr/bin
/home/mike/.blender/scripts
/home/mike/.blender/scripts/bpymodules
- Directories:
Blender home dir:
/home/mike/.blender
Default dir for scripts:
/home/mike/.blender/scripts
Default "bpydata/" data dir for scripts:
/home/mike/.blender/scripts/bpydata
User defined dir for scripts:
<NOTICE> -- not found
Data dir "bpydata/" inside user defined dir:
<NOTICE> -- not found
Default config data "bpydata/config/" dir:
/home/mike/.blender/scripts/bpydata/config
- Modules: all basic ones were found.
OpenGL:
======
- Renderer: Quadro FX 370/PCI/SSE2
- Vendor: NVIDIA Corporation
- Version: 3.3.0 NVIDIA 260.19.06
- Extensions:
GL_ARB_blend_func_extended GL_ARB_color_buffer_float
GL_ARB_compatibility GL_ARB_copy_buffer GL_ARB_depth_buffer_float
GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers
GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced
GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location
GL_ARB_fragment_coord_conventions GL_ARB_fragment_program
GL_ARB_fragment_program_shadow GL_ARB_fragment_shader
GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB
GL_ARB_geometry_shader4 GL_ARB_get_program_binary
GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging
GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample
GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2
GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite
GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects
GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects
GL_ARB_shader_bit_encoding GL_ARB_shader_objects
GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync
GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object
GL_ARB_texture_compression GL_ARB_texture_compression_rgtc
GL_ARB_texture_cube_map GL_ARB_texture_env_add
GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar
GL_ARB_texture_env_dot3 GL_ARB_texture_float
GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample
GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle
GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_swizzle
GL_ARB_timer_query GL_ARB_transpose_matrix
GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra
GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object
GL_ARB_vertex_program GL_ARB_vertex_shader
GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array
GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float
GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add
GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color
GL_EXT_blend_equation_separate GL_EXT_blend_func_separate
GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array
GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access
GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements
GL_EXT_fog_coord GL_EXT_framebuffer_blit
GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats
GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB
GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters
GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays
GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels
GL_EXT_pixel_buffer_object GL_EXT_point_parameters
GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color
GL_EXT_separate_shader_objects GL_EXT_separate_specular_color
GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap
GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object
GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc
GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map
GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine
GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic
GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias
GL_EXT_texture_mirror_clamp GL_EXT_texture_object
GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB
GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_vertex_array
GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip
GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square
GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image
GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_explicit_multisample
GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance
GL_NV_fragment_program GL_NV_fragment_program_option
GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage
GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float
GL_NV_light_max_exponent GL_NV_multisample_coverage
GL_NV_multisample_filter_hint GL_NV_occlusion_query
GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object
GL_NV_parameter_buffer_object2 GL_NV_pixel_data_range
GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners
GL_NV_register_combiners2 GL_NV_shader_buffer_load
GL_NV_texgen_reflection GL_NV_texture_barrier
GL_NV_texture_compression_vtc GL_NV_texture_env_combine4
GL_NV_texture_expand_normal GL_NV_texture_multisample
GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2
GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vdpau_interop
GL_NV_vertex_array_range GL_NV_vertex_array_range2
GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program
GL_NV_vertex_program1_1 GL_NV_vertex_program2
GL_NV_vertex_program2_option GL_NV_vertex_program3
GL_NVX_conditional_render GL_NVX_gpu_memory_info
GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture
GL_SGIX_shadow GL_SUN_slice_accum
&#12288;
- Simplistic almost useless benchmark:
Redrawing all areas 10 times took 0.4345 seconds.
..
(*) Found 2 notices, documented in the text above.
&#12288;

```
 
Speed test info for Dell PowerEdge T105
 
```

cat /proc/cpuinfo
 
processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 67
model name : Dual-Core AMD Opteron(tm) Processor 1214
stepping : 3
cpu MHz : 1000.000
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 2
apicid : 0
initial apicid : 0
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips : 2009.59
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
 
processor : 1
vendor_id : AuthenticAMD
cpu family : 15
model : 67
model name : Dual-Core AMD Opteron(tm) Processor 1214
stepping : 3
cpu MHz : 1000.000
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 1
cpu cores : 2
apicid : 1
initial apicid : 1
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips : 2009.59
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```
 
```

cat /proc/meminfo
 
MemTotal: 2055968 kB
MemFree: 1259028 kB
Buffers: 172000 kB
Cached: 269700 kB
SwapCached: 0 kB
Active: 414072 kB
Inactive: 251512 kB
Active(anon): 224108 kB
Inactive(anon): 13976 kB
Active(file): 189964 kB
Inactive(file): 237536 kB
Unevictable: 0 kB
Mlocked: 0 kB
SwapTotal: 6019068 kB
SwapFree: 6019068 kB
Dirty: 128 kB
Writeback: 0 kB
AnonPages: 224004 kB
Mapped: 69028 kB
Shmem: 14204 kB
Slab: 47028 kB
SReclaimable: 33116 kB
SUnreclaim: 13912 kB
KernelStack: 1928 kB
PageTables: 14340 kB
NFS_Unstable: 0 kB
Bounce: 0 kB
WritebackTmp: 0 kB
CommitLimit: 7047052 kB
Committed_AS: 781848 kB
VmallocTotal: 34359738367 kB
VmallocUsed: 26188 kB
VmallocChunk: 34359708764 kB
HardwareCorrupted: 0 kB
HugePages_Total: 0
HugePages_Free: 0
HugePages_Rsvd: 0
HugePages_Surp: 0
Hugepagesize: 2048 kB
DirectMap4k: 6976 kB
DirectMap2M: 2088960 kB

```
 
```
&#12288;
dmesg
 
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.35-25-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 (Ubuntu 2.6.35-25.44-generic 2.6.35.10)
[ 0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=5b3327fb-4235-4408-8167-7b359689cc6c ro quiet splash
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[ 0.000000] BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000ca000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[ 0.000000] BIOS-e820: 000000007fed0000 - 000000007fee4000 (ACPI data)
[ 0.000000] BIOS-e820: 000000007fee4000 - 000000007ff5d000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007ff5d000 - 000000007ff6e000 (reserved)
[ 0.000000] BIOS-e820: 000000007ff6e000 - 000000007ff7f000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007ff80000 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[ 0.000000] NX (Execute Disable) protection: active
[ 0.000000] DMI present.
[ 0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[ 0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[ 0.000000] No AGP bridge found
[ 0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x400000000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-C8FFF write-protect
[ 0.000000] C9000-DFFFF uncachable
[ 0.000000] E0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 0000000000 mask FF80000000 write-back
[ 0.000000] 1 disabled
[ 0.000000] 2 disabled
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] Scanning 1 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 000000000009dc00 (usable)
[ 0.000000] modified: 000000000009dc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000ca000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000007fed0000 (usable)
[ 0.000000] modified: 000000007fed0000 - 000000007fee4000 (ACPI data)
[ 0.000000] modified: 000000007fee4000 - 000000007ff5d000 (ACPI NVS)
[ 0.000000] modified: 000000007ff5d000 - 000000007ff6e000 (reserved)
[ 0.000000] modified: 000000007ff6e000 - 000000007ff7f000 (ACPI NVS)
[ 0.000000] modified: 000000007ff80000 - 0000000080000000 (reserved)
[ 0.000000] modified: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] modified: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000fff80000 - 0000000100000000 (reserved)
[ 0.000000] initial memory mapped : 0 - 20000000
[ 0.000000] found SMP MP-table at [ffff8800000f7a70] f7a70
[ 0.000000] init_memory_mapping: 0000000000000000-000000007fed0000
[ 0.000000] 0000000000 - 007fe00000 page 2M
[ 0.000000] 007fe00000 - 007fed0000 page 4k
[ 0.000000] kernel direct mapping tables up to 7fed0000 @ 16000-1a000
[ 0.000000] RAMDISK: 37573000 - 37ff0000
[ 0.000000] ACPI: RSDP 00000000000f79b0 00024 (v02 PTLTD )
[ 0.000000] ACPI: XSDT 000000007fedfd42 0009C (v01 DELL PE_SC3 06040000 DELL 00000000)
[ 0.000000] ACPI: FACP 000000007fee34ed 000F4 (v03 DELL PE_SC3 06040000 DELL 000F4240)
[ 0.000000] ACPI: DSDT 000000007fedfdde 0369B (v01 DELL PE_SC3 06040000 MSFT 0100000E)
[ 0.000000] ACPI: FACS 000000007fee4fc0 00040
[ 0.000000] ACPI: TCPA 000000007fee35e1 00032 (v01 Phoeni x 06040000 TL 00000000)
[ 0.000000] ACPI: SLIC 000000007fee3613 00024 (v01 DELL PE_SC3 06040000 PTL 00000001)
[ 0.000000] ACPI: SPCR 000000007fee3637 00050 (v01 DELL PE_SC3 06040000 PTL 00000001)
[ 0.000000] ACPI: EINJ 000000007fee3687 001B0 (v01 PTL WHEAPTL 06040000 PTL 00000001)
[ 0.000000] ACPI: HEST 000000007fee3837 000A8 (v01 PTL WHEAPTL 06040000 PTL 00000001)
[ 0.000000] ACPI: BERT 000000007fee38df 00030 (v01 PTL WHEAPTL 06040000 PTL 00000001)
[ 0.000000] ACPI: SSDT 000000007fee390f 000E1 (v01 wheaos wheaosc 06040000 INTL 20050624)
[ 0.000000] ACPI: ERST 000000007fee39f0 00270 (v01 PTL WHEAPTL 06040000 PTL 00000001)
[ 0.000000] ACPI: SRAT 000000007fee3c60 000A0 (v01 AMD FAM_F_10 06040000 AMD 00000001)
[ 0.000000] ACPI: SSDT 000000007fee3d00 00206 (v01 AMD POWERNOW 06040000 AMD 00000001)
[ 0.000000] ACPI: MCFG 000000007fee3f06 0003C (v01 PTLTD MCFG 06040000 LTP 00000000)
[ 0.000000] ACPI: HPET 000000007fee3f42 00038 (v01 PTLTD HPETTBL 06040000 LTP 00000001)
[ 0.000000] ACPI: APIC 000000007fee3f7a 0005E (v01 PTLTD ? APIC 06040000 LTP 00000000)
[ 0.000000] ACPI: BOOT 000000007fee3fd8 00028 (v01 PTLTD $SBFTBL$ 06040000 LTP 00000001)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[ 0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[ 0.000000] SRAT: Node 0 PXM 0 0-a0000
[ 0.000000] SRAT: Node 0 PXM 0 100000-80000000
[ 0.000000] SRAT: Node 0 [0,a0000) + [100000,80000000) -> [0,80000000)
[ 0.000000] NUMA: Using 63 for the hash shift.
[ 0.000000] Initmem setup node 0 0000000000000000-000000007fed0000
[ 0.000000] NODE_DATA [0000000001d18100 - 0000000001d1d0ff]
[ 0.000000] [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002600000-ffff8800041fffff] on node 0
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] DMA32 0x00001000 -> 0x00100000
[ 0.000000] Normal empty
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x0000009d
[ 0.000000] 0: 0x00000100 -> 0x0007fed0
[ 0.000000] On node 0 totalpages: 523869
[ 0.000000] DMA zone: 56 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3925 pages, LIFO batch:0
[ 0.000000] DMA32 zone: 7108 pages used for memmap
[ 0.000000] DMA32 zone: 512780 pages, LIFO batch:31
[ 0.000000] Detected use of extended apic ids on hypertransport bus
[ 0.000000] ACPI: PM-Timer IO Port: 0x8008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 40
[ 0.000000] early_res array is doubled to 64 at [18000 - 187ff]
[ 0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[ 0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ca000
[ 0.000000] PM: Registered nosave memory: 00000000000ca000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u1048576
[ 0.000000] pcpu-alloc: s91520 r8192 d23168 u1048576 alloc=1*2097152
[ 0.000000] pcpu-alloc: [0] 0 1
[ 0.000000] Built 1 zonelists in Node order, mobility grouping on. Total pages: 516705
[ 0.000000] Policy zone: DMA32
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=5b3327fb-4235-4408-8167-7b359689cc6c ro quiet splash
[ 0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[ 0.000000] Checking aperture...
[ 0.000000] No AGP bridge found
[ 0.000000] Node 0: aperture @ 3f70000000 size 32 MB
[ 0.000000] Aperture beyond 4GB. Ignoring.
[ 0.000000] Subtract (50 early reservations)
[ 0.000000] #1 [0001000000 - 0001d17114] TEXT DATA BSS
[ 0.000000] #2 [0037573000 - 0037ff0000] RAMDISK
[ 0.000000] #3 [0001d18000 - 0001d180f8] BRK
[ 0.000000] #4 [00000f7a80 - 0000100000] BIOS reserved
[ 0.000000] #5 [00000f7a70 - 00000f7a80] MP-table mpf
[ 0.000000] #6 [000009dc00 - 000009e171] BIOS reserved
[ 0.000000] #7 [000009e27d - 00000f7a70] BIOS reserved
[ 0.000000] #8 [000009e171 - 000009e27d] MP-table mpc
[ 0.000000] #9 [0000010000 - 0000012000] TRAMPOLINE
[ 0.000000] #10 [0000012000 - 0000016000] ACPI WAKEUP
[ 0.000000] #11 [0000016000 - 0000018000] PGTABLE
[ 0.000000] #12 [0001d18100 - 0001d1d100] NODE_DATA
[ 0.000000] #13 [0001d1d100 - 0001d1e100] BOOTMEM
[ 0.000000] #14 [0001d17140 - 0001d172c0] BOOTMEM
[ 0.000000] #15 [000251f000 - 0002520000] BOOTMEM
[ 0.000000] #16 [0002520000 - 0002521000] BOOTMEM
[ 0.000000] #17 [0002600000 - 0004200000] MEMMAP 0
[ 0.000000] #18 [0001d172c0 - 0001d17440] BOOTMEM
[ 0.000000] #19 [0001d1e100 - 0001d2a100] BOOTMEM
[ 0.000000] #20 [0001d2b000 - 0001d2c000] BOOTMEM
[ 0.000000] #21 [0001d17440 - 0001d17481] BOOTMEM
[ 0.000000] #22 [0001d174c0 - 0001d17503] BOOTMEM
[ 0.000000] #23 [0001d17540 - 0001d17850] BOOTMEM
[ 0.000000] #24 [0001d17880 - 0001d178e8] BOOTMEM
[ 0.000000] #25 [0001d17900 - 0001d17968] BOOTMEM
[ 0.000000] #26 [0001d17980 - 0001d179e8] BOOTMEM
[ 0.000000] #27 [0001d17a00 - 0001d17a68] BOOTMEM
[ 0.000000] #28 [0001d17a80 - 0001d17ae8] BOOTMEM
[ 0.000000] #29 [0001d17b00 - 0001d17b68] BOOTMEM
[ 0.000000] #30 [0001d17b80 - 0001d17be8] BOOTMEM
[ 0.000000] #31 [0001d17c00 - 0001d17c68] BOOTMEM
[ 0.000000] #32 [0001d17c80 - 0001d17ce8] BOOTMEM
[ 0.000000] #33 [0001d17d00 - 0001d17d68] BOOTMEM
[ 0.000000] #34 [0001d17d80 - 0001d17de8] BOOTMEM
[ 0.000000] #35 [0001d17e00 - 0001d17e68] BOOTMEM
[ 0.000000] #36 [0001d17e80 - 0001d17ee8] BOOTMEM
[ 0.000000] #37 [0001d17f00 - 0001d17f20] BOOTMEM
[ 0.000000] #38 [0001d17f40 - 0001d17faa] BOOTMEM
[ 0.000000] #39 [0001d2a100 - 0001d2a16a] BOOTMEM
[ 0.000000] #40 [0001e00000 - 0001e1e000] BOOTMEM
[ 0.000000] #41 [0001f00000 - 0001f1e000] BOOTMEM
[ 0.000000] #42 [0001d17fc0 - 0001d17fc8] BOOTMEM
[ 0.000000] #43 [0001d2a180 - 0001d2a188] BOOTMEM
[ 0.000000] #44 [0001d2a1c0 - 0001d2a1c8] BOOTMEM
[ 0.000000] #45 [0001d2a200 - 0001d2a210] BOOTMEM
[ 0.000000] #46 [0001d2a240 - 0001d2a380] BOOTMEM
[ 0.000000] #47 [0001d2a380 - 0001d2a3e0] BOOTMEM
[ 0.000000] #48 [0001d2a400 - 0001d2a460] BOOTMEM
[ 0.000000] #49 [0001d2c000 - 0001d34000] BOOTMEM
[ 0.000000] Memory: 2042264k/2095936k available (5714k kernel code, 460k absent, 53212k reserved, 5377k data, 908k init)
[ 0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] RCU dyntick-idle grace-period acceleration is enabled.
[ 0.000000] RCU-based detection of stalled CPUs is disabled.
[ 0.000000] Verbose stalled-CPUs detection is disabled.
[ 0.000000] NR_IRQS:4352 nr_irqs:512
[ 0.000000] Extended CMOS year: 2000
[ 0.000000] spurious 8259A interrupt: IRQ7.
[ 0.000000] Console: colour VGA+ 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] allocated 20971520 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] hpet clockevent registered
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 2210.553 MHz processor.
[ 0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4421.10 BogoMIPS (lpj=22105530)
[ 0.000010] pid_max: default: 32768 minimum: 301
[ 0.000035] Security Framework initialized
[ 0.000054] AppArmor: AppArmor initialized
[ 0.000056] Yama: becoming mindful.
[ 0.000334] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[ 0.011014] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.011765] Mount-cache hash table entries: 256
[ 0.011915] Initializing cgroup subsys ns
[ 0.011919] Initializing cgroup subsys cpuacct
[ 0.011923] Initializing cgroup subsys memory
[ 0.011934] Initializing cgroup subsys devices
[ 0.011936] Initializing cgroup subsys freezer
[ 0.011938] Initializing cgroup subsys net_cls
[ 0.011965] tseg: 007ff80000
[ 0.011967] CPU: Physical Processor ID: 0
[ 0.011969] CPU: Processor Core ID: 0
[ 0.011971] mce: CPU supports 5 MCE banks
[ 0.011982] using C1E aware idle routine
[ 0.011984] Performance Events: AMD PMU driver.
[ 0.011989] ... version: 0
[ 0.011991] ... bit width: 48
[ 0.011992] ... generic registers: 4
[ 0.011994] ... value mask: 0000ffffffffffff
[ 0.011996] ... max period: 00007fffffffffff
[ 0.011998] ... fixed-purpose events: 0
[ 0.012000] ... event mask: 000000000000000f
[ 0.013576] ACPI: Core revision 20100428
[ 0.017750] ftrace: converting mcount calls to 0f 1f 44 00 00
[ 0.017756] ftrace: allocating 22681 entries in 89 pages
[ 0.020104] Setting APIC routing to flat
[ 0.020386] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.125446] CPU0: Dual-Core AMD Opteron(tm) Processor 1214 stepping 03
[ 0.130000] Booting Node 0, Processors #1 Ok.
[ 0.280114] Brought up 2 CPUs
[ 0.280116] Total of 2 processors activated (8841.47 BogoMIPS).
[ 0.280343] devtmpfs: initialized
[ 0.280852] regulator: core version 0.5
[ 0.280882] Time: 10:43:49 Date: 02/21/11
[ 0.280927] NET: Registered protocol family 16
[ 0.281051] node 0 link 0: io port [1000, 3fff]
[ 0.281054] node 0 link 0: io port [4000, fffff]
[ 0.281057] TOM: 0000000080000000 aka 2048M
[ 0.281060] node 0 link 0: mmio [d0000000, d04fffff]
[ 0.281063] node 0 link 0: mmio [fed00000, fed0ffff]
[ 0.281065] node 0 link 0: mmio [d8000000, dfffffff]
[ 0.281068] node 0 link 0: mmio [fec00000, fec0ffff]
[ 0.281071] node 0 link 0: mmio [e0000000, efffffff]
[ 0.281074] node 0 link 0: mmio [a0000, bffff]
[ 0.281076] node 0 link 0: mmio [f0000000, fe0bffff]
[ 0.281080] bus: [00, ff] on node 0 link 0
[ 0.281082] bus: 00 index 0 [io 0x0000-0xffff]
[ 0.281085] bus: 00 index 1 [mem 0x80000000-0xd7ffffff]
[ 0.281087] bus: 00 index 2 [mem 0xfec10000-0xfcffffffff]
[ 0.281089] bus: 00 index 3 [mem 0xd8000000-0xfebfffff]
[ 0.281091] bus: 00 index 4 [mem 0xfec00000-0xfec0ffff]
[ 0.281094] bus: 00 index 5 [mem 0x000a0000-0x000bffff]
[ 0.281101] ACPI: bus type pci registered
[ 0.281168] PCI: MMCONFIG for domain 0000 [bus 00-04] at [mem 0xe0000000-0xe04fffff] (base 0xe0000000)
[ 0.281171] PCI: MMCONFIG at [mem 0xe0000000-0xe04fffff] reserved in E820
[ 0.281564] PCI: Using configuration type 1 for base access
[ 0.282279] Trying to unpack rootfs image as initramfs...
[ 0.282279] bio: create slab <bio-0> at 0
[ 0.282279] ACPI: EC: Look up EC in DSDT
[ 0.282279] \_SB_:_OSC evaluation returned wrong type
[ 0.282279] _OSC request data:1 7
[ 0.282810] ACPI: BIOS _OSI(Linux) query ignored
[ 0.283259] ACPI: Interpreter enabled
[ 0.283261] ACPI: (supports S0 S4 S5)
[ 0.283277] ACPI: Using IOAPIC for interrupt routing
[ 0.291089] ACPI: No dock devices found.
[ 0.291093] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[ 0.291195] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[ 0.291364] pci_root PNP0A08:00: host bridge window [io 0x0000-0x0cf7]
[ 0.291367] pci_root PNP0A08:00: host bridge window [io 0x0d00-0xffff]
[ 0.291370] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[ 0.291373] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c0000-0x000dffff] conflicts with reserved [mem 0x000ca000-0x000fffff]
[ 0.291377] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
[ 0.291379] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed8ffff]
[ 0.291442] pci 0000:00:01.0: reg 10: [io 0x8c00-0x8fff]
[ 0.291464] pci 0000:00:01.1: reg 10: [io 0x2080-0x209f]
[ 0.291472] pci 0000:00:01.1: reg 20: [io 0x2040-0x207f]
[ 0.291475] pci 0000:00:01.1: reg 24: [io 0x2000-0x203f]
[ 0.291485] pci 0000:00:01.1: PME# supported from D3hot D3cold
[ 0.291488] pci 0000:00:01.1: PME# disabled
[ 0.291504] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd0000fff]
[ 0.291520] pci 0000:00:02.0: supports D1 D2
[ 0.291522] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.291525] pci 0000:00:02.0: PME# disabled
[ 0.291543] pci 0000:00:02.1: reg 10: [mem 0xd0001000-0xd00010ff]
[ 0.291562] pci 0000:00:02.1: supports D1 D2
[ 0.291564] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.291567] pci 0000:00:02.1: PME# disabled
[ 0.291589] pci 0000:00:07.0: reg 10: [io 0x20f0-0x20f7]
[ 0.291593] pci 0000:00:07.0: reg 14: [io 0x20e0-0x20e3]
[ 0.291596] pci 0000:00:07.0: reg 18: [io 0x20d0-0x20d7]
[ 0.291600] pci 0000:00:07.0: reg 1c: [io 0x20c0-0x20c3]
[ 0.291603] pci 0000:00:07.0: reg 20: [io 0x20b0-0x20bf]
[ 0.291607] pci 0000:00:07.0: reg 24: [mem 0xd0002000-0xd0002fff]
[ 0.291634] pci 0000:00:08.0: reg 10: [io 0x2440-0x2447]
[ 0.291637] pci 0000:00:08.0: reg 14: [io 0x2430-0x2433]
[ 0.291641] pci 0000:00:08.0: reg 18: [io 0x2420-0x2427]
[ 0.291644] pci 0000:00:08.0: reg 1c: [io 0x2410-0x2413]
[ 0.291648] pci 0000:00:08.0: reg 20: [io 0x2400-0x240f]
[ 0.291651] pci 0000:00:08.0: reg 24: [mem 0xd0003000-0xd0003fff]
[ 0.291700] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.291703] pci 0000:00:0b.0: PME# disabled
[ 0.291731] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.291733] pci 0000:00:0c.0: PME# disabled
[ 0.291761] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.291764] pci 0000:00:0d.0: PME# disabled
[ 0.291791] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.291794] pci 0000:00:0e.0: PME# disabled
[ 0.291896] pci 0000:01:08.0: reg 10: [mem 0xd8000000-0xdfffffff pref]
[ 0.291901] pci 0000:01:08.0: reg 14: [io 0x3000-0x30ff]
[ 0.291907] pci 0000:01:08.0: reg 18: [mem 0xd0100000-0xd010ffff]
[ 0.291920] pci 0000:01:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[ 0.291932] pci 0000:01:08.0: supports D1 D2
[ 0.291954] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[ 0.291958] pci 0000:00:09.0: bridge window [io 0x3000-0x3fff]
[ 0.291961] pci 0000:00:09.0: bridge window [mem 0xd0100000-0xd01fffff]
[ 0.291964] pci 0000:00:09.0: bridge window [mem 0xd8000000-0xdfffffff pref]
[ 0.292009] pci 0000:02:00.0: reg 10: [mem 0xd0200000-0xd020ffff 64bit]
[ 0.292056] pci 0000:02:00.0: PME# supported from D3hot D3cold
[ 0.292060] pci 0000:02:00.0: PME# disabled
[ 0.310011] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[ 0.310015] pci 0000:00:0b.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.310018] pci 0000:00:0b.0: bridge window [mem 0xd0200000-0xd02fffff]
[ 0.310022] pci 0000:00:0b.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.310040] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[ 0.310044] pci 0000:00:0c.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.310047] pci 0000:00:0c.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.310050] pci 0000:00:0c.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.310072] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[ 0.310075] pci 0000:00:0d.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.310078] pci 0000:00:0d.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.310082] pci 0000:00:0d.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.310099] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[ 0.310102] pci 0000:00:0e.0: bridge window [io 0xf000-0x0000] (disabled)
[ 0.310105] pci 0000:00:0e.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)
[ 0.310109] pci 0000:00:0e.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[ 0.310120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.310184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[ 0.310225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[ 0.310247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[ 0.310269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[ 0.310291] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR3._PRT]
[ 0.326661] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19) *0
[ 0.326791] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19) *0
[ 0.326923] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19) *0, disabled.
[ 0.327052] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 17 18 19) *0, disabled.
[ 0.327180] ACPI: PCI Interrupt Link [LNK5] (IRQs 16 17 18 19) *0, disabled.
[ 0.327309] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *0
[ 0.327437] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22 23) *0
[ 0.327565] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22 23) *0, disabled.
[ 0.327693] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
[ 0.327821] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[ 0.327949] ACPI: PCI Interrupt Link [LMCI] (IRQs 20 21 22 23) *0, disabled.
[ 0.328077] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22 23) *0, disabled.
[ 0.328215] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22 23) *0
[ 0.328355] ACPI: PCI Interrupt Link [LSI1] (IRQs 20 21 22 23) *0
[ 0.328491] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[ 0.328536] HEST: HEST table parsing is initialized.
[ 0.328627] vgaarb: device added: PCI:0000:01:08.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.328630] vgaarb: loaded
[ 0.328770] SCSI subsystem initialized
[ 0.328879] libata version 3.00 loaded.
[ 0.328912] usbcore: registered new interface driver usbfs
[ 0.328923] usbcore: registered new interface driver hub
[ 0.328958] usbcore: registered new device driver usb
[ 0.329095] ACPI: WMI: Mapper loaded
[ 0.329097] PCI: Using ACPI for IRQ routing
[ 0.329099] PCI: pci_cache_line_size set to 64 bytes
[ 0.329143] reserve RAM buffer: 000000000009dc00 - 000000000009ffff
[ 0.329146] reserve RAM buffer: 000000007fed0000 - 000000007fffffff
[ 0.329240] NetLabel: Initializing
[ 0.329242] NetLabel: domain hash size = 128
[ 0.329243] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.329257] NetLabel: unlabeled traffic allowed by default
[ 0.329290] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.329295] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[ 0.329300] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[ 0.350033] Switching to clocksource hpet
[ 0.361393] AppArmor: AppArmor Filesystem Enabled
[ 0.361411] pnp: PnP ACPI init
[ 0.361432] ACPI: bus type pnp registered
[ 0.363695] pnp: PnP ACPI: found 12 devices
[ 0.363697] ACPI: ACPI bus type pnp unregistered
[ 0.363710] system 00:00: [mem 0xffc00000-0xffffffff] could not be reserved
[ 0.363713] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[ 0.363716] system 00:00: [mem 0xfee00000-0xfeefffff] could not be reserved
[ 0.363719] system 00:00: [mem 0xfed00000-0xfed00fff] has been reserved
[ 0.363725] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
[ 0.363731] system 00:03: [io 0x8000-0x807f] has been reserved
[ 0.363734] system 00:03: [io 0x8080-0x80ff] has been reserved
[ 0.363737] system 00:03: [io 0x8400-0x847f] has been reserved
[ 0.363739] system 00:03: [io 0x8480-0x84ff] has been reserved
[ 0.363742] system 00:03: [io 0x8800-0x887f] has been reserved
[ 0.363745] system 00:03: [io 0x8880-0x88ff] has been reserved
[ 0.363748] system 00:03: [io 0x2040-0x207f] has been reserved
[ 0.363750] system 00:03: [io 0x2000-0x203f] has been reserved
[ 0.363757] system 00:05: [io 0x04d0-0x04d1] has been reserved
[ 0.363763] system 00:0a: [io 0x0c00-0x0c7f] has been reserved
[ 0.369814] pci 0000:01:08.0: BAR 6: assigned [mem 0xd0120000-0xd013ffff pref]
[ 0.369818] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[ 0.369821] pci 0000:00:09.0: bridge window [io 0x3000-0x3fff]
[ 0.369824] pci 0000:00:09.0: bridge window [mem 0xd0100000-0xd01fffff]
[ 0.369827] pci 0000:00:09.0: bridge window [mem 0xd8000000-0xdfffffff pref]
[ 0.369831] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[ 0.369833] pci 0000:00:0b.0: bridge window [io disabled]
[ 0.369836] pci 0000:00:0b.0: bridge window [mem 0xd0200000-0xd02fffff]
[ 0.369839] pci 0000:00:0b.0: bridge window [mem pref disabled]
[ 0.369842] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[ 0.369844] pci 0000:00:0c.0: bridge window [io disabled]
[ 0.369846] pci 0000:00:0c.0: bridge window [mem disabled]
[ 0.369849] pci 0000:00:0c.0: bridge window [mem pref disabled]
[ 0.369852] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[ 0.369854] pci 0000:00:0d.0: bridge window [io disabled]
[ 0.369857] pci 0000:00:0d.0: bridge window [mem disabled]
[ 0.369859] pci 0000:00:0d.0: bridge window [mem pref disabled]
[ 0.369862] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[ 0.369864] pci 0000:00:0e.0: bridge window [io disabled]
[ 0.369867] pci 0000:00:0e.0: bridge window [mem disabled]
[ 0.369869] pci 0000:00:0e.0: bridge window [mem pref disabled]
[ 0.369877] pci 0000:00:09.0: setting latency timer to 64
[ 0.369882] pci 0000:00:0b.0: setting latency timer to 64
[ 0.369887] pci 0000:00:0c.0: setting latency timer to 64
[ 0.369891] pci 0000:00:0d.0: setting latency timer to 64
[ 0.369896] pci 0000:00:0e.0: setting latency timer to 64
[ 0.369899] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7]
[ 0.369906] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff]
[ 0.369908] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[ 0.369911] pci_bus 0000:00: resource 7 [mem 0x80000000-0xfebfffff]
[ 0.369913] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed8ffff]
[ 0.369916] pci_bus 0000:01: resource 0 [io 0x3000-0x3fff]
[ 0.369918] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd01fffff]
[ 0.369921] pci_bus 0000:01: resource 2 [mem 0xd8000000-0xdfffffff pref]
[ 0.369923] pci_bus 0000:02: resource 1 [mem 0xd0200000-0xd02fffff]
[ 0.369964] NET: Registered protocol family 2
[ 0.370099] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.371197] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[ 0.374232] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[ 0.374964] TCP: Hash tables configured (established 262144 bind 65536)
[ 0.374967] TCP reno registered
[ 0.374979] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[ 0.375011] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[ 0.375132] NET: Registered protocol family 1
[ 0.375212] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375239] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375271] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375276] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[ 0.375282] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375316] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375321] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[ 0.375328] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375364] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375369] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[ 0.375375] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375415] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375419] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[ 0.375426] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 0.375443] pci 0000:01:08.0: Boot video device
[ 0.375449] PCI: CLS 64 bytes, default 64
[ 0.450252] Simple Boot Flag at 0x62 set to 0x1
[ 0.450452] Scanning for low memory corruption every 60 seconds
[ 0.450576] audit: initializing netlink socket (disabled)
[ 0.450586] type=2000 audit(1298285029.450:1): initialized
[ 0.464056] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[ 0.465753] VFS: Disk quotas dquot_6.5.2
[ 0.465814] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[ 0.466515] fuse init (API version 7.14)
[ 0.466610] msgmni has been set to 3988
[ 0.466900] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.466903] io scheduler noop registered
[ 0.466905] io scheduler deadline registered
[ 0.466950] io scheduler cfq registered (default)
[ 0.470219] pcieport 0000:00:0b.0: setting latency timer to 64
[ 0.470236] alloc irq_desc for 40 on node 0
[ 0.470238] alloc kstat_irqs on node 0
[ 0.470247] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[ 0.472683] pcieport 0000:00:0c.0: setting latency timer to 64
[ 0.472695] alloc irq_desc for 41 on node 0
[ 0.472697] alloc kstat_irqs on node 0
[ 0.472702] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[ 0.472831] pcieport 0000:00:0d.0: setting latency timer to 64
[ 0.472842] alloc irq_desc for 42 on node 0
[ 0.472844] alloc kstat_irqs on node 0
[ 0.472849] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[ 0.472936] pcieport 0000:00:0e.0: setting latency timer to 64
[ 0.472948] alloc irq_desc for 43 on node 0
[ 0.472949] alloc kstat_irqs on node 0
[ 0.472954] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[ 0.473037] aer 0000:00:0b.0:pcie02: AER service couldn't init device: no _OSC support
[ 0.473046] aer 0000:00:0c.0:pcie02: AER service couldn't init device: no _OSC support
[ 0.473053] aer 0000:00:0d.0:pcie02: AER service couldn't init device: no _OSC support
[ 0.473060] aer 0000:00:0e.0:pcie02: AER service couldn't init device: no _OSC support
[ 0.473080] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.473102] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.473295] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[ 0.473301] ACPI: Power Button [PWRB]
[ 0.473359] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[ 0.473362] ACPI: Power Button [PWRF]
[ 0.473667] ACPI: acpi_idle registered with cpuidle
[ 0.475600] [Firmware Bug]: ERST: ERST table is invalid
[ 0.475828] Linux agpgart interface v0.103
[ 0.475832] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.475928] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.476239] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.477291] brd: module loaded
[ 0.477779] loop: module loaded
[ 0.478048] pata_acpi 0000:00:07.0: enabling device (0005 -> 0007)
[ 0.478339] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[ 0.478344] alloc irq_desc for 23 on node 0
[ 0.478346] alloc kstat_irqs on node 0
[ 0.478353] pata_acpi 0000:00:07.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
[ 0.478387] pata_acpi 0000:00:07.0: setting latency timer to 64
[ 0.478399] pata_acpi 0000:00:07.0: PCI INT A disabled
[ 0.478694] ACPI: PCI Interrupt Link [LSI1] enabled at IRQ 22
[ 0.478696] alloc irq_desc for 22 on node 0
[ 0.478698] alloc kstat_irqs on node 0
[ 0.478702] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSI1] -> GSI 22 (level, low) -> IRQ 22
[ 0.478726] pata_acpi 0000:00:08.0: setting latency timer to 64
[ 0.478732] pata_acpi 0000:00:08.0: PCI INT A disabled
[ 0.479058] Fixed MDIO Bus: probed
[ 0.479092] PPP generic driver version 2.4.2
[ 0.479126] tun: Universal TUN/TAP device driver, 1.6
[ 0.479128] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 0.479195] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.479421] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[ 0.479424] alloc irq_desc for 21 on node 0
[ 0.479425] alloc kstat_irqs on node 0
[ 0.479430] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[ 0.479448] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 0.479450] ehci_hcd 0000:00:02.1: EHCI Host Controller
[ 0.479485] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[ 0.479511] ehci_hcd 0000:00:02.1: debug port 1
[ 0.479516] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[ 0.479532] ehci_hcd 0000:00:02.1: irq 21, io mem 0xd0001000
[ 0.490023] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[ 0.490141] hub 1-0:1.0: USB hub found
[ 0.490146] hub 1-0:1.0: 10 ports detected
[ 0.490227] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.490475] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[ 0.490478] alloc irq_desc for 20 on node 0
[ 0.490479] alloc kstat_irqs on node 0
[ 0.490483] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[ 0.490493] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 0.490495] ohci_hcd 0000:00:02.0: OHCI Host Controller
[ 0.490528] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[ 0.490547] ohci_hcd 0000:00:02.0: irq 20, io mem 0xd0000000
[ 0.546632] Freeing initrd memory: 10740k freed
[ 0.552118] hub 2-0:1.0: USB hub found
[ 0.552123] hub 2-0:1.0: 10 ports detected
[ 0.552198] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.552334] PNP: No PS/2 controller found. Probing ports directly.
[ 0.555097] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.555108] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.555258] mice: PS/2 mouse device common for all mice
[ 0.555382] rtc_cmos 00:08: RTC can wake from S4
[ 0.555424] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[ 0.555447] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[ 0.555572] device-mapper: uevent: version 1.0.3
[ 0.555666] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 0.555784] device-mapper: multipath: version 1.1.1 loaded
[ 0.555786] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.556045] cpuidle: using governor ladder
[ 0.556077] cpuidle: using governor menu
[ 0.556378] TCP cubic registered
[ 0.556516] NET: Registered protocol family 10
[ 0.556914] lo: Disabled Privacy Extensions
[ 0.557136] NET: Registered protocol family 17
[ 0.557174] powernow-k8: Found 1 Dual-Core AMD Opteron(tm) Processor 1214 (2 cpu cores) (version 2.20.00)
[ 0.557226] powernow-k8: 0 : fid 0xe (2200 MHz), vid 0x8
[ 0.557229] powernow-k8: 1 : fid 0xc (2000 MHz), vid 0xa
[ 0.557231] powernow-k8: 2 : fid 0xa (1800 MHz), vid 0xc
[ 0.557233] powernow-k8: 3 : fid 0x2 (1000 MHz), vid 0x12
[ 0.557386] PM: Resume from disk failed.
[ 0.557398] registered taskstats version 1
[ 0.557570] Magic number: 15:296:730
[ 0.557669] rtc_cmos 00:08: setting system clock to 2011-02-21 10:43:49 UTC (1298285029)
[ 0.557672] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.557673] EDD information not available.
[ 0.557768] Freeing unused kernel memory: 908k freed
[ 0.558143] Write protecting the kernel read-only data: 10240k
[ 0.558304] Freeing unused kernel memory: 412k freed
[ 0.558674] Freeing unused kernel memory: 1644k freed
[ 0.577486] udev[103]: starting version 163
[ 0.658933] sata_nv 0000:00:07.0: version 3.5
[ 0.658949] sata_nv 0000:00:07.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
[ 0.658999] sata_nv 0000:00:07.0: setting latency timer to 64
[ 0.659543] scsi0 : sata_nv
[ 0.659705] tg3.c:v3.110 (April 9, 2010)
[ 0.659981] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 19
[ 0.659984] alloc irq_desc for 19 on node 0
[ 0.659986] alloc kstat_irqs on node 0
[ 0.659994] tg3 0000:02:00.0: PCI INT A -> Link[LNK2] -> GSI 19 (level, low) -> IRQ 19
[ 0.660072] tg3 0000:02:00.0: setting latency timer to 64
[ 0.661510] scsi1 : sata_nv
[ 0.661702] ata1: SATA max UDMA/133 cmd 0x20f0 ctl 0x20e0 bmdma 0x20b0 irq 23
[ 0.661705] ata2: SATA max UDMA/133 cmd 0x20d0 ctl 0x20c0 bmdma 0x20b8 irq 23
[ 0.668113] sata_nv 0000:00:08.0: PCI INT A -> Link[LSI1] -> GSI 22 (level, low) -> IRQ 22
[ 0.668180] sata_nv 0000:00:08.0: setting latency timer to 64
[ 0.684175] scsi2 : sata_nv
[ 0.687630] scsi3 : sata_nv
[ 0.687854] ata3: SATA max UDMA/133 cmd 0x2440 ctl 0x2430 bmdma 0x2400 irq 22
[ 0.687858] ata4: SATA max UDMA/133 cmd 0x2420 ctl 0x2410 bmdma 0x2408 irq 22
[ 0.705786] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95722) rev a200] (PCI Express) MAC address 00:1d:09:33:f5:57
[ 0.705791] tg3 0000:02:00.0: eth0: attached PHY is 5722/5756 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[ 0.705794] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[ 0.705797] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[ 1.150020] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.150139] usb 2-1: new low speed USB device using ohci_hcd and address 2
[ 1.170199] ata1.00: ATA-7: SAMSUNG HE160HJ, JF800-24, max UDMA7
[ 1.170204] ata1.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 1.180017] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1.190197] ata1.00: configured for UDMA/133
[ 1.190222] ata3.00: ATAPI: TSSTcorp CD-RW/DVD-ROM TS-H493B, D200, max UDMA/33
[ 1.190311] scsi 0:0:0:0: Direct-Access ATA SAMSUNG HE160HJ JF80 PQ: 0 ANSI: 5
[ 1.190487] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.190591] sd 0:0:0:0: [sda] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[ 1.190645] sd 0:0:0:0: [sda] Write Protect is off
[ 1.190648] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.190672] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.191316] sda: sda1 sda2 < sda5 >
[ 1.221726] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.230139] ata3.00: configured for UDMA/33
[ 1.397233] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[ 1.397239] EXT4-fs (sda1): write access will be enabled during recovery
[ 1.681779] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1.703682] ata2.00: ATA-6: WDC WD800GD-75FLC3, 32.08G32, max UDMA/133
[ 1.703685] ata2.00: 156250000 sectors, multi 16: LBA48
[ 1.722515] usb 2-2: new low speed USB device using ohci_hcd and address 3
[ 1.741195] ata2.00: configured for UDMA/133
[ 1.741314] scsi 1:0:0:0: Direct-Access ATA WDC WD800GD-75FL 32.0 PQ: 0 ANSI: 5
[ 1.741513] sd 1:0:0:0: Attached scsi generic sg1 type 0
[ 1.741686] sd 1:0:0:0: [sdb] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[ 1.741737] sd 1:0:0:0: [sdb] Write Protect is off
[ 1.741740] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1.741762] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.742351] scsi 2:0:0:0: CD-ROM TSSTcorp CDRWDVD TS-H493B D200 PQ: 0 ANSI: 5
[ 1.742824] sdb:sr0: scsi3-mmc drive: 8x/48x writer cd/rw xa/form2 cdda tray
[ 1.745612] Uniform CD-ROM driver Revision: 3.20
[ 1.745745] sr 2:0:0:0: Attached scsi CD-ROM sr0
[ 1.745809] sr 2:0:0:0: Attached scsi generic sg2 type 5
[ 1.756341] unknown partition table
[ 1.756491] sd 1:0:0:0: [sdb] Attached SCSI disk
[ 1.959468] usbcore: registered new interface driver hiddev
[ 1.967343] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2
[ 1.967444] generic-usb 0003:03F0:0024.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:02.0-1/input0
[ 1.972393] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
[ 1.972488] generic-usb 0003:045E:0039.0002: input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2/input0
[ 1.972525] usbcore: registered new interface driver usbhid
[ 1.972527] usbhid: USB HID core driver
[ 2.070016] ata4: SATA link down (SStatus 0 SControl 300)
[ 4.699388] EXT4-fs (sda1): orphan cleanup on readonly fs
[ 4.699399] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2883626
[ 4.699478] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262150
[ 4.699539] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262181
[ 4.699559] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262180
[ 4.699579] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262178
[ 4.699597] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262176
[ 4.699617] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262175
[ 4.699637] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262169
[ 4.699659] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262167
[ 4.699708] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262162
[ 4.699725] EXT4-fs (sda1): 10 orphan inodes deleted
[ 4.699728] EXT4-fs (sda1): recovery complete
[ 5.006635] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[ 6.797474] Adding 6019068k swap on /dev/sda5. Priority:-1 extents:1 across:6019068k
[ 7.479183] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 8.042253] udev[382]: starting version 163
[ 10.089855] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[ 10.321776] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 10.474709] dell-wmi-aio: No known WMI GUID found
[ 10.603511] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[ 10.633622] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[ 10.633716] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[ 10.769793] lp: driver loaded but no devices found
[ 10.890453] EDAC MC: Ver: 2.1.0 Jan 21 2011
[ 10.978714] EDAC amd64_edac: Ver: 3.3.0 Jan 21 2011
[ 10.978845] EDAC amd64: ECC is enabled by BIOS.
[ 10.979047] EDAC MC: Rev F or later detected
[ 10.979063] EDAC MC: DCT0 chip selects:
[ 10.979065] EDAC MC: 0: 0MB 1: 0MB
[ 10.979067] EDAC MC: 2: 1024MB 3: 1024MB
[ 10.979069] EDAC MC: 4: 0MB 5: 0MB
[ 10.979071] EDAC MC: 6: 0MB 7: 0MB
[ 10.979128] EDAC MC0: Giving out device to 'amd64_edac' 'RevF': DEV 0000:00:18.2
[ 10.979154] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
[ 11.198651] type=1400 audit(1298285040.127:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=541 comm="apparmor_parser"
[ 11.198930] type=1400 audit(1298285040.127:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=541 comm="apparmor_parser"
[ 11.199088] type=1400 audit(1298285040.127:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=541 comm="apparmor_parser"
[ 11.199452] type=1400 audit(1298285040.127:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=513 comm="apparmor_parser"
[ 11.199722] type=1400 audit(1298285040.127:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=513 comm="apparmor_parser"
[ 11.199875] type=1400 audit(1298285040.127:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=513 comm="apparmor_parser"
[ 11.203371] [drm] Initialized drm 1.1.0 20060810
[ 11.372959] [drm] radeon defaulting to kernel modesetting.
[ 11.372964] [drm] radeon kernel modesetting enabled.
[ 11.373350] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 18
[ 11.373355] alloc irq_desc for 18 on node 0
[ 11.373357] alloc kstat_irqs on node 0
[ 11.373366] radeon 0000:01:08.0: PCI INT A -> Link[LNK1] -> GSI 18 (level, low) -> IRQ 18
[ 11.376451] [drm] initializing kernel modesetting (RV100 0x1002:0x515E).
[ 11.376575] [drm] register mmio base: 0xD0100000
[ 11.376577] [drm] register mmio size: 65536
[ 11.376707] radeon 0000:01:08.0: VRAM: 128M 0xD8000000 - 0xDFFFFFFF (32M used)
[ 11.376710] radeon 0000:01:08.0: GTT: 512M 0xB8000000 - 0xD7FFFFFF
[ 11.406864] [drm] radeon: irq initialized.
[ 11.407375] [drm] Detected VRAM RAM=128M, BAR=128M
[ 11.407380] [drm] RAM width 16bits DDR
[ 11.407483] [TTM] Zone kernel: Available graphics memory: 1027984 kiB.
[ 11.407486] [TTM] Initializing pool allocator.
[ 11.407513] [drm] radeon: 32M of VRAM memory ready
[ 11.407515] [drm] radeon: 512M of GTT memory ready.
[ 11.407543] [drm] GART: num cpu pages 131072, num gpu pages 131072
[ 11.430240] [drm] Loading R100 Microcode
[ 12.226068] [drm] radeon: ring at 0x00000000B8000000
[ 12.226090] [drm] ring test succeeded in 1 usecs
[ 12.226259] [drm] radeon: ib pool ready.
[ 12.226574] [drm] ib test succeeded in 0 usecs
[ 12.226687] [drm] Radeon Display Connectors
[ 12.226689] [drm] Connector 0:
[ 12.226691] [drm] VGA
[ 12.226693] [drm] DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[ 12.226695] [drm] Encoders:
[ 12.226697] [drm] CRT1: INTERNAL_DAC1
[ 12.354876] [drm] fb mappable at 0xD8040000
[ 12.354878] [drm] vram apper at 0xD8000000
[ 12.354879] [drm] size 1998848
[ 12.354881] [drm] fb depth is 8
[ 12.354882] [drm] pitch is 1664
[ 12.524738] Console: switching to colour frame buffer device 200x75
[ 12.542838] fb0: radeondrmfb frame buffer device
[ 12.542840] drm: registered panic notifier
[ 12.542843] Slow work thread pool: Starting up
[ 12.542915] Slow work thread pool: Ready
[ 12.542921] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:08.0 on minor 0
[ 13.190430] type=1400 audit(1298285042.117:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=748 comm="apparmor_parser"
[ 13.190795] type=1400 audit(1298285042.117:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=748 comm="apparmor_parser"
[ 13.460721] ppdev: user-space parallel port driver
[ 13.928411] type=1400 audit(1298285042.857:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=850 comm="apparmor_parser"
[ 13.928685] type=1400 audit(1298285042.857:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=850 comm="apparmor_parser"
[ 14.367970] alloc irq_desc for 44 on node 0
[ 14.367974] alloc kstat_irqs on node 0
[ 14.367987] tg3 0000:02:00.0: irq 44 for MSI/MSI-X
[ 14.401044] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 14.526642] [drm:r100_bandwidth_update] *ERROR* You may not have enough display bandwidth for current mode
[ 14.526645] If you have flickering problem, try to lower resolution, refresh rate, or color depth
[ 14.552057] [drm:r100_bandwidth_update] *ERROR* You may not have enough display bandwidth for current mode
[ 14.552060] If you have flickering problem, try to lower resolution, refresh rate, or color depth
[ 18.033930] [drm:r100_bandwidth_update] *ERROR* You may not have enough display bandwidth for current mode
[ 18.033933] If you have flickering problem, try to lower resolution, refresh rate, or color depth
[ 18.979412] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 26.904407] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 79.500017] Clocksource tsc unstable (delta = -110323773 ns)
[ 103.620041] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 103.864523] Initializing USB Mass Storage driver...
[ 103.864767] scsi4 : usb-storage 1-5:1.0
[ 103.865068] usbcore: registered new interface driver usb-storage
[ 103.865074] USB Mass Storage support registered.
[ 104.861829] scsi 4:0:0:0: Direct-Access Seagate Portable 0130 PQ: 0 ANSI: 4
[ 104.862986] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 104.871119] sd 4:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 104.872684] sd 4:0:0:0: [sdc] Write Protect is off
[ 104.872691] sd 4:0:0:0: [sdc] Mode Sense: 2f 08 00 00
[ 104.872698] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 104.875680] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 104.875693] sdc: sdc1
[ 104.946702] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 104.946713] sd 4:0:0:0: [sdc] Attached SCSI disk
[ 1030.263815] sd 4:0:0:0: [sdc] Unhandled error code
[ 1030.263822] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
[ 1030.263830] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 01 59 82 bf 00 00 20 00
[ 1030.263847] end_request: I/O error, dev sdc, sector 22643391

```
 
```

lspci
 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express

```
 
```
&#12288;
Blender test:
 
Threads = 2
Test.Blend: 1:35:59
 
Threads = 1
Test.Blend: 3:00:04
&#12288;
Blender System Info
 
=====================================
= Blender 2.49 System Information =
=====================================
&#12288;
Built on 2010-09-04 06:52:05, Rev- Version linux2 dynamic
Platform: linux2
========
Python:
======
- Version: 2.6.6 (r266:84292, Sep 15 2010, 16:41:53)
[GCC 4.4.5]
- Paths:
/usr/lib/python2.6
/usr/lib/python2.6/plat-linux2
/usr/lib/python2.6/lib-tk
/usr/lib/python2.6/lib-old
/usr/lib/python2.6/lib-dynload
/usr/local/lib/python2.6/dist-packages
/usr/lib/python2.6/dist-packages
/usr/lib/python2.6/dist-packages/PIL
/usr/lib/python2.6/dist-packages/gst-0.10
/usr/lib/pymodules/python2.6
/usr/lib/pymodules/python2.6/gtk-2.0
/usr/bin
/home/user/.blender/scripts
/home/user/.blender/scripts/bpymodules
- Directories:
Blender home dir:
/home/user/.blender
Default dir for scripts:
/home/user/.blender/scripts
Default "bpydata/" data dir for scripts:
/home/user/.blender/scripts/bpydata
User defined dir for scripts:
<NOTICE> -- not found
Data dir "bpydata/" inside user defined dir:
<NOTICE> -- not found
Default config data "bpydata/config/" dir:
/home/user/.blender/scripts/bpydata/config
- Modules: all basic ones were found.
OpenGL:
======
- Renderer: Software Rasterizer
- Vendor: Mesa Project
- Version: 2.1 Mesa 7.9-devel
- Extensions:
GL_ARB_copy_buffer GL_ARB_depth_clamp GL_ARB_depth_texture
GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex
GL_ARB_fragment_coord_conventions GL_ARB_fragment_program
GL_ARB_fragment_program_shadow GL_ARB_fragment_shader
GL_ARB_framebuffer_object GL_ARB_half_float_pixel
GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_map_buffer_range
GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query
GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite
GL_ARB_provoking_vertex GL_ARB_shader_objects
GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient
GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression
GL_ARB_texture_cube_map GL_ARB_texture_env_add
GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar
GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat
GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle
GL_ARB_texture_swizzle GL_ARB_transpose_matrix
GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object
GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader
GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color
GL_EXT_blend_equation_separate GL_EXT_blend_func_separate
GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract
GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture
GL_EXT_depth_bounds_test GL_EXT_draw_buffers2
GL_EXT_draw_range_elements GL_EXT_framebuffer_blit
GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object
GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram
GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil
GL_EXT_packed_pixels GL_EXT_paletted_texture
GL_EXT_pixel_buffer_object GL_EXT_point_parameters
GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal
GL_EXT_secondary_color GL_EXT_separate_specular_color
GL_EXT_shadow_funcs GL_EXT_shared_texture_palette
GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture
GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_array
GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp
GL_EXT_texture_env_add GL_EXT_texture_env_combine
GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
GL_EXT_texture_mirror_clamp GL_EXT_texture_object
GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_swizzle
GL_EXT_vertex_array GL_EXT_vertex_array_bgra
GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels
GL_APPLE_vertex_array_object GL_APPLE_object_purgeable
GL_ATI_blend_equation_separate GL_ATI_envmap_bumpmap
GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once
GL_ATI_fragment_shader GL_ATI_separate_stencil
GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip
GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate
GL_MESA_pack_invert GL_MESA_resize_buffers GL_MESA_texture_array
GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square
GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fragment_program
GL_NV_fragment_program_option GL_NV_light_max_exponent
GL_NV_packed_depth_stencil GL_NV_point_sprite GL_NV_texgen_reflection
GL_NV_texture_env_combine4 GL_NV_texture_rectangle
GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format
GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table
GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp
GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
GL_SUN_multi_draw_arrays
&#12288;
- Simplistic almost useless benchmark:
 
Redrawing all areas 10 times took 1.8664 seconds.
 

```
 
&#12288;
A lot of information I know, but I really want to get to the bottom of this so I can use my Workstation to its full potential.
 
Is it CPU type? - The board supports the 3.2ghz Pentium D840 EE CPU which I can get cheaply or the P4 7.73Ghz EE which is even cheaper! - Would either of these make a difference?
 
 
Cheers (Fingers crossed that someone eventually replies)
&#12288;

---

### Post by clhsharky on 2011-02-23
dvdfilmbuff

Would you please Wrap[Quote] or [Code].
Thankyou,

I get lost with all the scrolling.


Sharky

---

### Post by dvdfilmbuff on 2011-02-23
> **clhsharky said:**
> dvdfilmbuff
 
Would you please Wrap[Quote] or [Code].
Thankyou,
 
 
Sharky
 
 
eh? - can I do what?

---

### Post by clhsharky on 2011-02-23
dvdfilmbuff



Your Welcome.



Sharky

---

### Post by dvdfilmbuff on 2011-02-23
Oh i see - Sorry. Thats cool :)
 
Thanks
 
Can you delete your post now? I have modified my original post with Code: blocks.

---

### Post by clhsharky on 2011-02-23
dvdfilmbuff

> Is there a way of optimizing apps to use the CPU capabilities without re-compiling them?
Some what.

cgroups patch might be of some use to you, depending on your needs.
Its in the latest kernels, but non on Ubuntu release kernels, yet.

"200 Lines Kernel Patch That Does Wonders"
[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)


Sharky

---

### Post by dvdfilmbuff on 2011-02-23
> **clhsharky said:**
> dvdfilmbuff


Some what.

cgroups patch might be of some use to you, depending on your needs.
Its in the latest kernels, but non on Ubuntu release kernels, yet.

"200 Lines Kernel Patch That Does Wonders"
[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)


Sharky

Many thanks.

I have run the 200-line patch, but it did not seem to make any difference in Blender. Still over 02 mins to render test.blend.

Incidentally, I have just downloaded the 2.5b 64bit release of blender from graphicall.org and the test scene now renders in 43 seconds. ?????

I guess I need the 64bit optimised version of 2.49????

My system is quick then! woo hoo

---

### Post by dvdfilmbuff on 2011-03-05
So, disappointment again now.

I have just taken receipt of a replacement CPU for  my Dell Precision 380 Workstation.

A Pentium D 840 Extreme Edition. 2 cores at 3.2Ghz, each with 2 threads (So thats 2 cores and 4 threads in total)

How come blender is the same speed? - in fact the extra 200mhz on each core has not made much difference to Ubuntu GUI either! Gggrrr

The bios recognises the CPU as 3.2Ghz, Dual Core, HT capable (where as the old cpu did not show HT capable and 3.0Ghz) 

Do I need to re-load Ubuntu 10.10? or is there something I can do to make it recognise the HT and 4 threads?

Ta.

---

