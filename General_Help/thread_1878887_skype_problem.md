---
title: "skype problem"
date: 2011-11-10
forum: General Help
---

### Post by nebula12 on 2011-11-10
hi!
i think my skype is problematic.. when i log in sometimes, it causes trouble to my system( gets very very slow) and i have to restart.. sometimes, it logs me out automatically when i sign in to skype.. i have ubuntu 11.10 and skype 2.2.035(beta).
does anyone know anything??

---

### Post by linuxwin2 on 2011-11-11
Run skype and type
```
$top 

```
Cat here the output

---

### Post by nebula12 on 2011-11-11
top - 10:31:57 up 25 min,  1 user,  load average: 0.31, 0.22, 0.18
Tasks: 164 total,   2 running, 162 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.3%us,  1.0%sy,  0.0%ni, 78.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3950552k total,  1728540k used,  2222012k free,   128448k buffers
Swap:  4085756k total,        0k used,  4085756k free,   866344k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3684 root      20   0  189m  92m  36m R   75  2.4   0:02.27 aptd               
 2981 root      20   0  177m  13m 6376 S    3  0.3   0:03.34 Xorg               
 3172 werecat   20   0  671m 106m  24m S    2  2.8   0:04.28 compiz             
 3578 werecat   20   0  310m  16m  11m S    2  0.4   0:00.78 gnome-terminal     
 3184 werecat   20   0  709m  73m  22m S    1  1.9   0:00.51 cairo-dock         
 1008 messageb  20   0 25216 2348 1088 S    1  0.1   0:02.62 dbus-daemon        
 3536 werecat   20   0  279m  83m  15m S    1  2.2   0:03.97 skype              
 3237 werecat   20   0  206m  24m  10m S    1  0.6   0:00.17 python             
  261 root      20   0     0    0    0 S    0  0.0   0:00.86 kworker/1:1        
  266 root      20   0     0    0    0 S    0  0.0   0:00.60 kworker/3:1        
 3136 werecat   20   0 27440 3084  868 S    0  0.1   0:01.43 dbus-daemon        
 3156 werecat   20   0  538m  19m  12m S    0  0.5   0:00.51 gnome-settings-    
 3292 werecat   20   0  371m  20m  10m S    0  0.5   0:00.70 unity-panel-ser    
 3321 werecat   20   0  254m 5820 4548 S    0  0.1   0:00.03 indicator-sessi    
    1 root      20   0 24184 2272 1344 S    0  0.1   0:00.78 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0   






i don't think that you 'll see an extraordinary usage of memory, as it does not do it avary time, but one in 10 let's say..and if it does it, i can't open anything, even the terminal..

---

### Post by nebula12 on 2011-12-15
anything new please? this annnoying thing is still happening

---

### Post by nebula12 on 2011-12-29
maybe dmesg could help?? well, this doesn't seem to happen to 
anyone else....:confused:


 dmesg

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=6ce07dc3-efdb-4e82-95de-616285d8e63c ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a800 (usable)
[    0.000000]  BIOS-e820: 000000000009a800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000caa85000 (usable)
[    0.000000]  BIOS-e820: 00000000caa85000 - 00000000caac9000 (reserved)
[    0.000000]  BIOS-e820: 00000000caac9000 - 00000000cadb7000 (usable)
[    0.000000]  BIOS-e820: 00000000cadb7000 - 00000000cade7000 (reserved)
[    0.000000]  BIOS-e820: 00000000cade7000 - 00000000cafe7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cafe7000 - 00000000cafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cafff000 - 00000000cb000000 (usable)
[    0.000000]  BIOS-e820: 00000000cb800000 - 00000000cfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 00000000ffc20000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Latitude E5420/0H5TG2, BIOS A01 04/20/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x12f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF8000000 write-back
[    0.000000]   3 base 0C8000000 mask FFC000000 write-back
[    0.000000]   4 base 0CB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask FE0000000 write-back
[    0.000000]   6 base 120000000 mask FF0000000 write-back
[    0.000000]   7 base 12F000000 mask FFF000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
[    0.000000] total RAM covered: 4000M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 8  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3248MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 7, base: 4848MB, range: 16MB, type UC
[    0.000000] e820 update range: 00000000cb000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f2000] f2000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000cb000000
[    0.000000]  0000000000 - 00cb000000 page 2M
[    0.000000] kernel direct mapping tables up to cb000000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000012f000000
[    0.000000]  0100000000 - 012f000000 page 2M
[    0.000000] kernel direct mapping tables up to 12f000000 @ cadb1000-cadb7000
[    0.000000] RAMDISK: 365ae000 - 372cf000
[    0.000000] ACPI: RSDP 00000000000fe300 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000caffde18 00074 (v01 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000caf87d98 000F4 (v04 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCAFE4E40/0x00000000CAFE4D40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000caf7e018 0864E (v02 INT430 SYSFexxx 00001001 INTL 20090903)
[    0.000000] ACPI: FACS 00000000cafe4e40 00040
[    0.000000] ACPI: APIC 00000000caffcf18 000CC (v02 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: TCPA 00000000cafe5d18 00032 (v02                 00000000      00000000)
[    0.000000] ACPI: MCFG 00000000cafe5c98 0003C (v01 DELL   SNDYBRDG 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cafe5c18 00038 (v01 A M I   PCHHPET 06222004 AMI. 00000003)
[    0.000000] ACPI: BOOT 00000000cafe5b98 00028 (v01 DELL   CBX3     06222004 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000caf7d818 007C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20090903)
[    0.000000] ACPI: SSDT 00000000caf7c018 00996 (v01  PmRef    CpuPm 00003000 INTL 20090903)
[    0.000000] ACPI: DMAR 00000000caf87c18 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: SLIC 00000000caf88a18 00176 (v03 DELL    CBX3    06222004 MSFT 00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000012f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000012f000000
[    0.000000]   NODE_DATA [000000012effb000 - 000000012effffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012a600000-ffff88012dffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0012f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000caa85
[    0.000000]     0: 0x000caac9 -> 0x000cadb7
[    0.000000]     0: 0x000cafff -> 0x000cb000
[    0.000000]     0: 0x00100000 -> 0x0012f000
[    0.000000] On node 0 totalpages: 1022206
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3917 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 811436 pages, LIFO batch:31
[    0.000000]   Normal zone: 2632 pages used for memmap
[    0.000000]   Normal zone: 189880 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000caa85000 - 00000000caac9000
[    0.000000] PM: Registered nosave memory: 00000000cadb7000 - 00000000cade7000
[    0.000000] PM: Registered nosave memory: 00000000cade7000 - 00000000cafe7000
[    0.000000] PM: Registered nosave memory: 00000000cafe7000 - 00000000cafff000
[    0.000000] PM: Registered nosave memory: 00000000cb000000 - 00000000cb800000
[    0.000000] PM: Registered nosave memory: 00000000cb800000 - 00000000cfa00000
[    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffc20000
[    0.000000] PM: Registered nosave memory: 00000000ffc20000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:2f31c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012ec00000 s79616 r8192 d22784 u131072
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1005233
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=6ce07dc3-efdb-4e82-95de-616285d8e63c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.000000] Memory: 3934704k/4964352k available (6109k kernel code, 875528k absent, 154120k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:808 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2494.240 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.48 BogoMIPS (lpj=9976960)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000411] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001258] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001592] Mount-cache hash table entries: 256
[    0.001691] Initializing cgroup subsys cpuacct
[    0.001695] Initializing cgroup subsys memory
[    0.001701] Initializing cgroup subsys devices
[    0.001703] Initializing cgroup subsys freezer
[    0.001704] Initializing cgroup subsys net_cls
[    0.001706] Initializing cgroup subsys blkio
[    0.001710] Initializing cgroup subsys perf_event
[    0.001734] CPU: Physical Processor ID: 0
[    0.001735] CPU: Processor Core ID: 0
[    0.001740] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001741] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001744] mce: CPU supports 7 MCE banks
[    0.001754] CPU0: Thermal monitoring enabled (TM1)
[    0.001761] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20110413
[    0.008922] ftrace: allocating 25647 entries in 101 pages
[    0.017925] DMAR: Host address width 36
[    0.017927] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.017934] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.017936] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.017941] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.017942] DMAR: RMRR base: 0x000000cadc6000 end: 0x000000cadd5fff
[    0.017944] DMAR: RMRR base: 0x000000cb800000 end: 0x000000cf9fffff
[    0.017945] DMAR: No ATSR found
[    0.018015] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.018017] HPET id 0 under DRHD base 0xfed91000
[    0.018018] HPET id 0 under DRHD base 0xfed91000
[    0.018019] HPET id 0 under DRHD base 0xfed91000
[    0.018020] HPET id 0 under DRHD base 0xfed91000
[    0.018021] HPET id 0 under DRHD base 0xfed91000
[    0.018022] HPET id 0 under DRHD base 0xfed91000
[    0.018023] HPET id 0 under DRHD base 0xfed91000
[    0.018024] HPET id 0 under DRHD base 0xfed91000
[    0.018205] Enabled IRQ remapping in x2apic mode
[    0.018207] Enabling x2apic
[    0.018208] Enabled x2apic
[    0.018214] Switched APIC routing to cluster x2apic.
[    0.018591] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058222] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
[    0.163742] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.163748] ... version:                3
[    0.163749] ... bit width:              48
[    0.163750] ... generic registers:      4
[    0.163752] ... value mask:             0000ffffffffffff
[    0.163753] ... max period:             000000007fffffff
[    0.163754] ... fixed-purpose events:   3
[    0.163755] ... event mask:             000000070000000f
[    0.164136] Booting Node   0, Processors  #1
[    0.164138] smpboot cpu 1: start_ip = 95000
[    0.271731]  #2
[    0.271733] smpboot cpu 2: start_ip = 95000
[    0.379606]  #3
[    0.379608] smpboot cpu 3: start_ip = 95000
[    0.487435] Brought up 4 CPUs
[    0.487438] Total of 4 processors activated (19953.80 BogoMIPS).
[    0.489893] devtmpfs: initialized
[    0.490005] PM: Registering ACPI NVS region at cade7000 (2097152 bytes)
[    0.490036] Dell Latitude E5420 series board detected. Selecting PCI-method for reboots.
[    0.491205] print_constraints: dummy: 
[    0.491231] Time: 10:30:48  Date: 12/29/11
[    0.491259] NET: Registered protocol family 16
[    0.491338] Trying to unpack rootfs image as initramfs...
[    0.491354] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.491356] ACPI: bus type pci registered
[    0.491419] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.491422] PCI: not using MMCONFIG
[    0.491423] PCI: Using configuration type 1 for base access
[    0.491429] dmi type 0xB1 record - unknown flag
[    0.492029] bio: create slab <bio-0> at 0
[    0.493306] ACPI: EC: Look up EC in DSDT
[    0.527306] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.701236] Freeing initrd memory: 13444k freed
[    0.711118] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.751306] ACPI: SSDT 00000000cadd7718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
[    0.751622] ACPI: Dynamic OEM Table Load:
[    0.751624] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20090903)
[    0.763189] ACPI: SSDT 00000000cadd8a98 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
[    0.763529] ACPI: Dynamic OEM Table Load:
[    0.763531] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20090903)
[    0.775060] ACPI: SSDT 00000000cadd6d98 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
[    0.775371] ACPI: Dynamic OEM Table Load:
[    0.775373] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20090903)
[    0.858912] ACPI: Interpreter enabled
[    0.858914] ACPI: (supports S0 S3 S4 S5)
[    0.858933] ACPI: Using IOAPIC for interrupt routing
[    0.858951] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.859289] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    1.410430] ACPI: EC: GPE = 0x10, I/O: command/status = 0x934, data = 0x930
[    1.434154] ACPI: No dock devices found.
[    1.434156] HEST: Table not found.
[    1.434159] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.434422] \_SB_.PCI0:_OSC invalid UUID
[    1.434423] _OSC request data:1 8 1f 
[    1.434426] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.434891] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.434893] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.434895] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.434898] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
[    1.434900] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    1.434910] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.434942] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    1.434952] pci 0000:00:02.0: reg 10: [mem 0xe1c00000-0xe1ffffff 64bit]
[    1.434958] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.434962] pci 0000:00:02.0: reg 20: [io  0x7000-0x703f]
[    1.435010] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.435034] pci 0000:00:16.0: reg 10: [mem 0xe3d80000-0xe3d8000f 64bit]
[    1.435095] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.435100] pci 0000:00:16.0: PME# disabled
[    1.435131] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.435152] pci 0000:00:1a.0: reg 10: [mem 0xe3d50000-0xe3d503ff]
[    1.435225] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.435229] pci 0000:00:1a.0: PME# disabled
[    1.435252] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.435267] pci 0000:00:1b.0: reg 10: [mem 0xe3d40000-0xe3d43fff 64bit]
[    1.435322] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.435325] pci 0000:00:1b.0: PME# disabled
[    1.435349] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.435449] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.435455] pci 0000:00:1c.0: PME# disabled
[    1.435487] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.435588] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.435593] pci 0000:00:1c.1: PME# disabled
[    1.435626] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    1.435726] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.435730] pci 0000:00:1c.2: PME# disabled
[    1.435765] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    1.435830] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.435834] pci 0000:00:1c.5: PME# disabled
[    1.435858] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    1.435924] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.435928] pci 0000:00:1c.6: PME# disabled
[    1.435959] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.435980] pci 0000:00:1d.0: reg 10: [mem 0xe3d30000-0xe3d303ff]
[    1.436052] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.436057] pci 0000:00:1d.0: PME# disabled
[    1.436080] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    1.436195] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    1.436214] pci 0000:00:1f.2: reg 10: [io  0x70b0-0x70b7]
[    1.436222] pci 0000:00:1f.2: reg 14: [io  0x70a0-0x70a3]
[    1.436230] pci 0000:00:1f.2: reg 18: [io  0x7090-0x7097]
[    1.436238] pci 0000:00:1f.2: reg 1c: [io  0x7080-0x7083]
[    1.436247] pci 0000:00:1f.2: reg 20: [io  0x7060-0x707f]
[    1.436255] pci 0000:00:1f.2: reg 24: [mem 0xe3d20000-0xe3d207ff]
[    1.436287] pci 0000:00:1f.2: PME# supported from D3hot
[    1.436291] pci 0000:00:1f.2: PME# disabled
[    1.436309] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.436324] pci 0000:00:1f.3: reg 10: [mem 0xe3d10000-0xe3d100ff 64bit]
[    1.436345] pci 0000:00:1f.3: reg 20: [io  0x7040-0x705f]
[    1.436442] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.436448] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.436454] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.436463] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.436685] pci 0000:02:00.0: [8086:0082] type 0 class 0x000280
[    1.436833] pci 0000:02:00.0: reg 10: [mem 0xe3c00000-0xe3c01fff 64bit]
[    1.437385] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.437420] pci 0000:02:00.0: PME# disabled
[    1.437607] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.437611] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    1.437616] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
[    1.437622] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.437667] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.437671] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    1.437675] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
[    1.437682] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.437764] pci 0000:09:00.0: [1217:13f7] type 0 class 0x000c00
[    1.437796] pci 0000:09:00.0: reg 10: [mem 0xe3b30000-0xe3b30fff]
[    1.437996] pci 0000:09:00.0: supports D1 D2
[    1.437997] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.438006] pci 0000:09:00.0: PME# disabled
[    1.438085] pci 0000:09:00.1: [1217:8321] type 0 class 0x000805
[    1.438119] pci 0000:09:00.1: reg 10: [mem 0xe3b20000-0xe3b201ff]
[    1.438320] pci 0000:09:00.1: supports D1 D2
[    1.438322] pci 0000:09:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.438330] pci 0000:09:00.1: PME# disabled
[    1.438400] pci 0000:09:00.2: [1217:8331] type 0 class 0x000180
[    1.438433] pci 0000:09:00.2: reg 10: [mem 0xe3b10000-0xe3b103ff]
[    1.438477] pci 0000:09:00.2: reg 18: [mem 0xe3b00000-0xe3b003ff]
[    1.438632] pci 0000:09:00.2: supports D1 D2
[    1.438633] pci 0000:09:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.438642] pci 0000:09:00.2: PME# disabled
[    1.438736] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    1.438740] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    1.438744] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
[    1.438751] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.438986] pci 0000:0a:00.0: [14e4:1681] type 0 class 0x000200
[    1.439025] pci 0000:0a:00.0: reg 10: [mem 0xe2010000-0xe201ffff 64bit]
[    1.439056] pci 0000:0a:00.0: reg 18: [mem 0xe2000000-0xe200ffff 64bit]
[    1.439188] pci 0000:0a:00.0: PME# supported from D3hot D3cold
[    1.439196] pci 0000:0a:00.0: PME# disabled
[    1.439250] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
[    1.439254] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
[    1.439258] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
[    1.439265] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.439290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.439394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.439422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.439451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.439478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    1.439510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.439573] \_SB_.PCI0:_OSC invalid UUID
[    1.439574] _OSC request data:1 1f 1f 
[    1.439577]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.439602] \_SB_.PCI0:_OSC invalid UUID
[    1.439603] _OSC request data:1 0 1d 
[    1.439606]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.439608] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.442081] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.442122] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.442158] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.442193] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.442228] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.442262] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.442297] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.442331] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.442401] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.442407] vgaarb: loaded
[    1.442408] vgaarb: bridge control possible 0000:00:02.0
[    1.442530] SCSI subsystem initialized
[    1.442575] libata version 3.00 loaded.
[    1.442603] usbcore: registered new interface driver usbfs
[    1.442612] usbcore: registered new interface driver hub
[    1.442631] usbcore: registered new device driver usb
[    1.442691] PCI: Using ACPI for IRQ routing
[    1.444433] PCI: pci_cache_line_size set to 64 bytes
[    1.444521] reserve RAM buffer: 000000000009a800 - 000000000009ffff 
[    1.444523] reserve RAM buffer: 00000000caa85000 - 00000000cbffffff 
[    1.444526] reserve RAM buffer: 00000000cadb7000 - 00000000cbffffff 
[    1.444528] reserve RAM buffer: 00000000cb000000 - 00000000cbffffff 
[    1.444530] reserve RAM buffer: 000000012f000000 - 000000012fffffff 
[    1.444598] NetLabel: Initializing
[    1.444599] NetLabel:  domain hash size = 128
[    1.444600] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.444609] NetLabel:  unlabeled traffic allowed by default
[    1.444641] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.444646] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.446660] Switching to clocksource hpet
[    1.450022] Switched to NOHz mode on CPU #0
[    1.450094] Switched to NOHz mode on CPU #1
[    1.450113] Switched to NOHz mode on CPU #2
[    1.450144] Switched to NOHz mode on CPU #3
[    1.450944] AppArmor: AppArmor Filesystem Enabled
[    1.450964] pnp: PnP ACPI init
[    1.450975] ACPI: bus type pnp registered
[    1.451247] pnp 00:00: [bus 00-3e]
[    1.451249] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.451251] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.451252] pnp 00:00: [io  0x0d00-0xffff window]
[    1.451254] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.451256] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.451258] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.451259] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.451261] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.451263] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.451264] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.451266] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.451267] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.451269] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.451271] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.451272] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.451274] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.451275] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.451277] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
[    1.451279] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.451331] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.451342] pnp 00:01: [io  0x0000-0x001f]
[    1.451344] pnp 00:01: [io  0x0081-0x0091]
[    1.451345] pnp 00:01: [io  0x0093-0x009f]
[    1.451347] pnp 00:01: [io  0x00c0-0x00df]
[    1.451348] pnp 00:01: [dma 4]
[    1.451365] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.451372] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.451386] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.451446] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.451477] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    1.451480] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    1.451488] pnp 00:04: [io  0x00f0]
[    1.451500] pnp 00:04: [irq 13]
[    1.451516] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.451524] pnp 00:05: [io  0x002e-0x002f]
[    1.451526] pnp 00:05: [io  0x004e-0x004f]
[    1.451527] pnp 00:05: [io  0x0061]
[    1.451528] pnp 00:05: [io  0x0063]
[    1.451530] pnp 00:05: [io  0x0065]
[    1.451531] pnp 00:05: [io  0x0067]
[    1.451534] pnp 00:05: [io  0x0070]
[    1.451535] pnp 00:05: [io  0x0080]
[    1.451536] pnp 00:05: [io  0x0092]
[    1.451537] pnp 00:05: [io  0x00b2-0x00b3]
[    1.451539] pnp 00:05: [io  0x0680-0x069f]
[    1.451540] pnp 00:05: [io  0x1000-0x100f]
[    1.451542] pnp 00:05: [io  0xffff]
[    1.451543] pnp 00:05: [io  0xffff]
[    1.451544] pnp 00:05: [io  0x0400-0x047f]
[    1.451545] pnp 00:05: [io  0x0500-0x057f]
[    1.451547] pnp 00:05: [io  0x164e-0x164f]
[    1.451574] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.451576] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.451578] system 00:05: [io  0xffff] has been reserved
[    1.451580] system 00:05: [io  0xffff] has been reserved
[    1.451582] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.451584] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.451586] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.451588] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.451594] pnp 00:06: [io  0x0070-0x0077]
[    1.451600] pnp 00:06: [irq 8]
[    1.451615] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.451622] pnp 00:07: [io  0x0060]
[    1.451623] pnp 00:07: [io  0x0064]
[    1.451629] pnp 00:07: [irq 1]
[    1.451645] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.458738] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    1.458751] pnp 00:09: [irq 12]
[    1.458770] pnp 00:09: Plug and Play ACPI device, IDs DLL049b PNP0f13 (active)
[    1.458877] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.458879] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.458880] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.458882] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.458883] pnp 00:0a: [mem 0xf8000000-0xfbffffff]
[    1.458885] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.458886] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.458888] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    1.458889] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.458890] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.458892] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.458894] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.458929] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.458931] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.458933] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.458935] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.458937] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.458939] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.458941] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.458943] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.458945] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.458947] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.458950] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.459008] pnp 00:0b: [irq 23]
[    1.459031] pnp 00:0b: Plug and Play ACPI device, IDs SMO8800 (active)
[    1.486696] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    1.486699] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    1.490668] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    1.490670] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    1.490673] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.490681] pnp: PnP ACPI: found 13 devices
[    1.490682] ACPI: ACPI bus type pnp unregistered
[    1.496121] PCI: max bus depth: 1 pci_try_num: 2
[    1.496164] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.496166] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.496171] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.496175] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.496182] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.496183] pci 0000:00:1c.1:   bridge window [io  disabled]
[    1.496189] pci 0000:00:1c.1:   bridge window [mem 0xe3c00000-0xe3cfffff]
[    1.496193] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    1.496199] pci 0000:00:1c.2: PCI bridge to [bus 03-08]
[    1.496202] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    1.496207] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe3afffff]
[    1.496212] pci 0000:00:1c.2:   bridge window [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.496219] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    1.496220] pci 0000:00:1c.5:   bridge window [io  disabled]
[    1.496226] pci 0000:00:1c.5:   bridge window [mem 0xe3b00000-0xe3bfffff]
[    1.496230] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    1.496236] pci 0000:00:1c.6: PCI bridge to [bus 0a-11]
[    1.496239] pci 0000:00:1c.6:   bridge window [io  0x2000-0x5fff]
[    1.496245] pci 0000:00:1c.6:   bridge window [mem 0xe2000000-0xe30fffff]
[    1.496249] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.496269] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.496275] pci 0000:00:1c.0: setting latency timer to 64
[    1.496286] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.496291] pci 0000:00:1c.1: setting latency timer to 64
[    1.496302] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.496305] pci 0000:00:1c.2: setting latency timer to 64
[    1.496312] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.496316] pci 0000:00:1c.5: setting latency timer to 64
[    1.496323] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.496327] pci 0000:00:1c.6: setting latency timer to 64
[    1.496331] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.496333] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.496335] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.496337] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xfeafffff]
[    1.496338] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.496340] pci_bus 0000:02: resource 1 [mem 0xe3c00000-0xe3cfffff]
[    1.496342] pci_bus 0000:03: resource 0 [io  0x6000-0x6fff]
[    1.496344] pci_bus 0000:03: resource 1 [mem 0xe3100000-0xe3afffff]
[    1.496346] pci_bus 0000:03: resource 2 [mem 0xe1100000-0xe1afffff 64bit pref]
[    1.496348] pci_bus 0000:09: resource 1 [mem 0xe3b00000-0xe3bfffff]
[    1.496350] pci_bus 0000:0a: resource 0 [io  0x2000-0x5fff]
[    1.496351] pci_bus 0000:0a: resource 1 [mem 0xe2000000-0xe30fffff]
[    1.496353] pci_bus 0000:0a: resource 2 [mem 0xe0000000-0xe10fffff 64bit pref]
[    1.496377] NET: Registered protocol family 2
[    1.496502] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.497302] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.498508] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.498657] TCP: Hash tables configured (established 524288 bind 65536)
[    1.498659] TCP reno registered
[    1.498668] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.498685] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.498781] NET: Registered protocol family 1
[    1.498793] pci 0000:00:02.0: Boot video device
[    1.498894] PCI: CLS 64 bytes, default 64
[    1.498898] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.498900] Placing 64MB software IO TLB between ffff8800c6a85000 - ffff8800caa85000
[    1.498902] software IO TLB at phys 0xc6a85000 - 0xcaa85000
[    1.498916] Simple Boot Flag at 0xf3 set to 0x1
[    1.499268] audit: initializing netlink socket (disabled)
[    1.499275] type=2000 audit(1325154649.340:1): initialized
[    1.520931] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.529752] VFS: Disk quotas dquot_6.5.2
[    1.529799] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.530233] fuse init (API version 7.16)
[    1.530298] msgmni has been set to 7711
[    1.530604] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.530629] io scheduler noop registered
[    1.530630] io scheduler deadline registered
[    1.530659] io scheduler cfq registered (default)
[    1.530949] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.530965] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.530993] intel_idle: MWAIT substates: 0x21120
[    1.530995] intel_idle: v0.4 model 0x2A
[    1.530996] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.531504] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.531790] ACPI: AC Adapter [AC] (off-line)
[    1.531925] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.532387] ACPI: Lid Switch [LID]
[    1.532444] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.532448] ACPI: Power Button [PBTN]
[    1.532606] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.532609] ACPI: Sleep Button [SBTN]
[    1.532637] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.532639] ACPI: Power Button [PWRF]
[    1.532659] ACPI: acpi_idle yielding to intel_idle
[    1.706363] thermal LNXTHERM:00: registered as thermal_zone0
[    1.706365] ACPI: Thermal Zone [THM] (25 C)
[    1.706382] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.706393] ERST: Table is not found!
[    1.706430] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.716062] ACPI: Battery Slot [BAT0] (battery present)
[    1.774481] Linux agpgart interface v0.103
[    1.774545] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.774668] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.775765] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.775856] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.776598] brd: module loaded
[    1.776936] loop: module loaded
[    1.777210] Fixed MDIO Bus: probed
[    1.777225] PPP generic driver version 2.4.2
[    1.777250] tun: Universal TUN/TAP device driver, 1.6
[    1.777251] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.777299] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.777315] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.777332] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.777335] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.777357] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.777380] ehci_hcd 0000:00:1a.0: debug port 2
[    1.781258] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.781272] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe3d50000
[    1.794164] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.794291] hub 1-0:1.0: USB hub found
[    1.794294] hub 1-0:1.0: 2 ports detected
[    1.794340] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.794351] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.794354] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.794380] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.794400] ehci_hcd 0000:00:1d.0: debug port 2
[    1.798293] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.798303] ehci_hcd 0000:00:1d.0: irq 17, io mem 0xe3d30000
[    1.814140] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.814254] hub 2-0:1.0: USB hub found
[    1.814257] hub 2-0:1.0: 2 ports detected
[    1.814296] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.814303] uhci_hcd: USB Universal Host Controller Interface driver
[    1.814345] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.814545] i8042: Warning: Keylock active
[    1.815875] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.815881] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.815952] mousedev: PS/2 mouse device common for all mice
[    1.816057] rtc_cmos 00:06: RTC can wake from S4
[    1.816153] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.816178] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.816273] device-mapper: uevent: version 1.0.3
[    1.816322] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.816422] cpuidle: using governor ladder
[    1.816564] cpuidle: using governor menu
[    1.816566] EFI Variables Facility v0.08 2004-May-17
[    1.816724] TCP cubic registered
[    1.816823] NET: Registered protocol family 10
[    1.816866] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.817270] NET: Registered protocol family 17
[    1.817280] Registering the dns_resolver key type
[    1.817343] PM: Hibernation image not present or could not be loaded.
[    1.817354] registered taskstats version 1
[    1.826830]   Magic number: 7:753:528
[    1.826909] rtc_cmos 00:06: setting system clock to 2011-12-29 10:30:50 UTC (1325154650)
[    1.827569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.827571] EDD information not available.
[    1.829296] Freeing unused kernel memory: 984k freed
[    1.829437] Write protecting the kernel read-only data: 10240k
[    1.829639] Freeing unused kernel memory: 16k freed
[    1.834330] Freeing unused kernel memory: 1396k freed
[    1.851663] udevd[87]: starting version 173
[    1.879856] sdhci: Secure Digital Host Controller Interface driver
[    1.879860] sdhci: Copyright(c) Pierre Ossman
[    1.880206] sdhci-pci 0000:09:00.1: SDHCI controller found [1217:8321] (rev 5)
[    1.880229] sdhci-pci 0000:09:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.880273] sdhci-pci 0000:09:00.1: Invalid iomem size. You may experience problems.
[    1.880317] sdhci-pci 0000:09:00.1: setting latency timer to 64
[    1.880348] mmc0: no vmmc regulator found
[    1.880388] Registered led device: mmc0::
[    1.880442] mmc0: SDHCI controller on PCI [0000:09:00.1] using DMA
[    1.882642] firewire_ohci 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.882652] firewire_ohci 0000:09:00.0: setting latency timer to 64
[    1.898920] ahci 0000:00:1f.2: version 3.0
[    1.898940] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.899022] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.899059] ahci: SSS flag set, parallel bus scan disabled
[    1.908742] tg3.c:v3.119 (May 18, 2011)
[    1.908765] tg3 0000:0a:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.908779] tg3 0000:0a:00.0: setting latency timer to 64
[    1.914064] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl SATA mode
[    1.914071] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.914080] ahci 0000:00:1f.2: setting latency timer to 64
[    1.946525] scsi0 : ahci
[    1.946699] scsi1 : ahci
[    1.946840] scsi2 : ahci
[    1.946979] scsi3 : ahci
[    1.947119] scsi4 : ahci
[    1.947258] scsi5 : ahci
[    1.947672] ata1: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20100 irq 42
[    1.947677] ata2: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20180 irq 42
[    1.947679] ata3: DUMMY
[    1.947682] ata4: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20280 irq 42
[    1.947685] ata5: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20300 irq 42
[    1.947689] ata6: SATA max UDMA/133 abar m2048@0xe3d20000 port 0xe3d20380 irq 42
[    1.954047] firewire_ohci: Register access failure - please notify [email]linux1394-devel@lists.sf.net[/email]
[    1.954110] firewire_ohci: Added fw-ohci device 0000:09:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x10
[    1.954746] tg3 0000:0a:00.0: eth0: Tigon3 [partno(BCM95761) rev 5761100] (PCI Express) MAC address d0:67:e5:32:66:73
[    1.954751] tg3 0000:0a:00.0: eth0: attached PHY is 5761 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.954754] tg3 0000:0a:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.954757] tg3 0000:0a:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.105847] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.238529] hub 1-1:1.0: USB hub found
[    2.238611] hub 1-1:1.0: 6 ports detected
[    2.269632] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.349521] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.453578] firewire_core: created device fw0: GUID 07364ec1324fc000, S400
[    2.457210] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.466936] ata1.00: ATA-8: ST9500423AS, 0001DEM1, max UDMA/133
[    2.466940] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.482102] hub 2-1:1.0: USB hub found
[    2.482174] hub 2-1:1.0: 6 ports detected
[    2.497330] Refined TSC clocksource calibration: 2494.333 MHz.
[    2.497337] Switching to clocksource tsc
[    2.553391] usb 1-1.4: new high speed USB device number 3 using ehci_hcd
[    2.682015] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.682334] ata1.00: configured for UDMA/133
[    2.689261] scsi 0:0:0:0: Direct-Access     ATA      ST9500423AS      0001 PQ: 0 ANSI: 5
[    2.689422] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.689427] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.689432] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.689502] sd 0:0:0:0: [sda] Write Protect is off
[    2.689507] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.689534] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.754389]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.754914] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.008679] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.020274] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633J, D500, max UDMA/100
[    3.035069] ata2.00: configured for UDMA/100
[    3.049961] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633J D500 PQ: 0 ANSI: 5
[    3.059652] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.059657] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.059847] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.059976] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.096693] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
[    3.376204] ata4: SATA link down (SStatus 0 SControl 300)
[    3.695789] ata5: SATA link down (SStatus 0 SControl 300)
[    4.015380] ata6: SATA link down (SStatus 0 SControl 300)
[    4.692662] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.244089] udevd[325]: starting version 173
[   15.269442] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   15.269640] lp: driver loaded but no devices found
[   15.271354] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.271362] mei 0000:00:16.0: setting latency timer to 64
[   15.275340] wmi: Mapper loaded
[   15.276423] [drm] Initialized drm 1.1.0 20060810
[   15.280369] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.280374] i915 0000:00:02.0: setting latency timer to 64
[   15.316298] cfg80211: Calling CRDA to update world regulatory domain
[   15.349418] Bluetooth: Core ver 2.16
[   15.349440] NET: Registered protocol family 31
[   15.349442] Bluetooth: HCI device and connection manager initialized
[   15.349444] Bluetooth: HCI socket layer initialized
[   15.349446] Bluetooth: L2CAP socket layer initialized
[   15.350113] Linux video capture interface: v2.00
[   15.350581] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (1bcf:280b)
[   15.353046] Bluetooth: SCO socket layer initialized
[   15.353572] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   15.353576] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.353578] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.353580] [drm] Driver supports precise vblank timestamp query.
[   15.353616] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.353722] usbcore: registered new interface driver btusb
[   15.355032] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.355035] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   15.355087] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.355095] iwlagn 0000:02:00.0: setting latency timer to 64
[   15.355128] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   15.364954] parport_pc 00:08: [io  0x0378-0x037b]
[   15.364974] parport_pc 00:08: [io  0x0278-0x027b]
[   15.364991] parport_pc 00:08: [io  0x03bc-0x03bf]
[   15.365004] parport_pc 00:08: [io  0x0378-0x037b]
[   15.365106] parport_pc 00:08: [irq 7]
[   15.371283] iwlagn 0000:02:00.0: device EEPROM VER=0x715, CALIB=0x6
[   15.371286] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   15.371288] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   15.371667] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.371754] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[   15.382853] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5
[   15.382917] usbcore: registered new interface driver uvcvideo
[   15.382919] USB Video Class driver (v1.1.0)
[   15.385482] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.394597] Adding 4085756k swap on /dev/sda7.  Priority:-1 extents:1 across:4085756k 
[   15.400662] type=1400 audit(1325147464.089:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=473 comm="apparmor_parser"
[   15.400936] type=1400 audit(1325147464.089:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=473 comm="apparmor_parser"
[   15.401112] type=1400 audit(1325147464.089:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=473 comm="apparmor_parser"
[   15.488393] alps.c: E6 report: 00 00 64
[   15.491925] cfg80211: World regulatory domain updated:
[   15.491928] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.491931] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.491934] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.491936] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.491939] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.491941] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.497192] ppdev: user-space parallel port driver
[   15.507695] alps.c: E7 report: 73 02 64
[   15.513400] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.3 build 42301
[   15.513547] Registered led device: phy0-led
[   15.513574] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.515594] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.624860] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   15.688497] fbcon: inteldrmfb (fb0) is primary device
[   15.688568] Console: switching to colour frame buffer device 200x56
[   15.688587] fb0: inteldrmfb frame buffer device
[   15.688588] drm: registered panic notifier
[   15.951783] alps.c: E6 report: 00 00 64
[   15.971473] alps.c: E7 report: 73 02 64
[   15.987959] parport_pc 00:08: activated
[   15.987963] parport_pc 00:08: reported by Plug and Play ACPI
[   16.038031] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr
[   16.055976] parport_pc 00:08: disabled
[   16.322667] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[   16.335189] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input8
[   16.562397] type=1400 audit(1325147465.249:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=881 comm="apparmor_parser"
[   16.562596] type=1400 audit(1325147465.249:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=882 comm="apparmor_parser"
[   16.562923] type=1400 audit(1325147465.249:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=882 comm="apparmor_parser"
[   16.563346] type=1400 audit(1325147465.253:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=882 comm="apparmor_parser"
[   16.563560] type=1400 audit(1325147465.253:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=885 comm="apparmor_parser"
[   16.563904] type=1400 audit(1325147465.253:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=885 comm="apparmor_parser"
[   16.564810] type=1400 audit(1325147465.253:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=886 comm="apparmor_parser"
[   16.620874] init: failsafe main process (824) killed by TERM signal
[   16.621230] init: apport pre-start process (919) terminated with status 1
[   16.621390] init: alsa-restore main process (926) terminated with status 19
[   16.625723] init: apport post-stop process (943) terminated with status 1
[   16.699363] acpi device:36: registered as cooling_device4
[   16.766404] Bluetooth: RFCOMM TTY layer initialized
[   16.766414] Bluetooth: RFCOMM socket layer initialized
[   16.766416] Bluetooth: RFCOMM ver 1.11
[   16.768318] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.768321] Bluetooth: BNEP filters: protocol multicast
[   16.834907] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   16.834959] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.850846] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.882712] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.882782] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.882803] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.140756] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.142887] tg3 0000:0a:00.0: irq 46 for MSI/MSI-X
[   17.220406] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.439182] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.439303] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   17.439427] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   17.439668] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.439749] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.439804] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.439861] input: HDA Intel PCH Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   17.439915] input: HDA Intel PCH Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   17.439968] input: HDA Intel PCH Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   17.440020] input: HDA Intel PCH HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   17.577382] init: anacron main process (950) killed by TERM signal
[   21.516618] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr,commit=600
[   21.886742] init: plymouth-stop pre-start process (1377) terminated with status 1
[   24.621875] wlan0: authenticate with 00:1f:9f:8e:7f:07 (try 1)
[   24.625892] wlan0: authenticated
[   24.632729] wlan0: associate with 00:1f:9f:8e:7f:07 (try 1)
[   24.635098] wlan0: RX AssocResp from 00:1f:9f:8e:7f:07 (capab=0x401 status=0 aid=1)
[   24.635101] wlan0: associated
[   24.637883] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.639024] wlan0: no IPv6 routers present
[   90.975387] usb 2-1.2: new low speed USB device number 4 using ehci_hcd
[   91.251464] usbcore: registered new interface driver usbhid
[   91.251468] usbhid: USB HID core driver
[   91.289018] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input17
[   91.289264] a4tech 0003:09DA:000A.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.0-1.2/input0
[  174.315956] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

---

