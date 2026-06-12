---
title: "[Jaunty]Memory missing"
date: 2010-02-23
forum: General Help
---

### Post by richard_tsai on 2010-02-23
Hi there,
    I used 9.04 for months and it work fine before restarting my PC.
After I restarted my PC, the memory consumption takes up to 4.2 GB after login. 
However, I cannot find any process that consume such large number of memory.
It's appreciated for your suggestions. 
Thank you very much!

%uname -a
Linux 105538-pc1 2.6.28-18-server #59-Ubuntu SMP Thu Jan 28 02:23:52 UTC 2010 i686 GNU/Linux

%top
top - 08:28:50 up 3 min,  2 users,  load average: 0.44, 0.38, 0.16
Tasks: 134 total,   2 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.0%us,  0.3%sy,  0.0%ni, 92.5%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7150216k total,  4741728k used,  2408488k free,    16416k buffers
Swap:  6385796k total,        0k used,  6385796k free,   222540k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2741 root      20   0  445m  33m 5812 S    7  0.5   0:33.36 Xorg               
 3502 richard   20   0 34112  18m  13m S    7  0.3   0:09.46 gnome-system-mo    
 3466 richard   20   0 22268 9144 7520 S    0  0.1   0:00.28 multiload-apple    
 3572 richard   20   0  2448 1200  912 R    0  0.0   0:00.25 top                
    1 root      20   0  3084 1884  564 S    0  0.0   0:01.30 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0              
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1              
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
   26 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod            
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd              
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn          
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn          
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
   32 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0            
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea    
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0     

%cat /proc/meminfo
MemTotal:        7150216 kB
MemFree:         2523120 kB
Buffers:           13452 kB
Cached:           142944 kB
SwapCached:            0 kB
Active:           190084 kB
Inactive:          90320 kB
Active(anon):     126684 kB
Inactive(anon):        8 kB
Active(file):      63400 kB
Inactive(file):    90312 kB
Unevictable:           8 kB
Mlocked:               8 kB
HighTotal:       6355464 kB
HighFree:        1883680 kB
LowTotal:         794752 kB
LowFree:          639440 kB
SwapTotal:       6385796 kB
SwapFree:        6385796 kB
Dirty:               136 kB
Writeback:             0 kB
AnonPages:        124016 kB
Mapped:            43452 kB
Slab:              16116 kB
SReclaimable:       7700 kB
SUnreclaim:         8416 kB
PageTables:         3940 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7863752 kB
Committed_AS:     401672 kB
VmallocTotal:     122880 kB
VmallocUsed:        9256 kB
VmallocChunk:     111092 kB
HugePages_Total:    2048
HugePages_Free:     2048
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      131064 kB
DirectMap2M:      778240 kB

---

### Post by dcstar on 2010-02-24
> **richard_tsai said:**
> Hi there,
    I used 9.04 for months and it work fine before restarting my PC.
After I restarted my PC, the memory consumption takes up to 4.2 GB after login. 
However, I cannot find any process that consume such large number of memory.
It's appreciated for your suggestions. 
.........

Boot off the previous kernel and see what happens.

You are using 32-bit Ubuntu which uses PAE to access RAM > 4GB, any process in a PAE environment can still only access 4GB of RAM maximum, other processes can use what remains up to the same limit.

You would probably be better off using a native 64-bit release (assuming your CPU supports it).

---

### Post by richard_tsai on 2010-02-24
Hi David,
    Thanks for your reply. 
Currently, I am using kernel 2.6.28-18-server.
I boot off the previous kernel 2.6.28-17-server and the situation is the same.
However, when I boot off kernel 2.6.28-11-server, I couldn't see gdm login screen.
I just wonder I could access 5GB memory before that restart. Could it be PAE's problem on kernel 2.6.28-18-server?

> **dcstar said:**
> Boot off the previous kernel and see what happens.

You are using 32-bit Ubuntu which uses PAE to access RAM > 4GB, any process in a PAE environment can still only access 4GB of RAM maximum, other processes can use what remains up to the same limit.

You would probably be better off using a native 64-bit release (assuming your CPU supports it).

---

### Post by richard_tsai on 2010-02-24
Hi there,
    I checked out boot up message and found there're two usable pieces of memory.
However, it looks I can only use the second piece of memory. Please advise any suggestions.
    Your help is appreciated.
   
[B][COLOR=Red][    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf680000 (usable)
[/COLOR][/B][COLOR=Red][COLOR=Black]>>About 3 GB[/COLOR][/COLOR][B][COLOR=Red]

[/COLOR][/B][COLOR=Red]**[    0.000000]  BIOS-e820: 0000000100000000 - 00000001fc000000 (usable)**[/COLOR]
>>About 4 GB



%dmesg | more
.......
[    0.000000] Linux version 2.6.28-18-server (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) 
#59-Ubuntu SMP Thu Jan 28 02:23:52 UTC 2010 (Ubuntu 2.6.28-18.59-server)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000094800 (usable)
[    0.000000]  BIOS-e820: 0000000000094800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
**[COLOR=Red][    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf680000 (usable)[/COLOR]**
[    0.000000]  BIOS-e820: 00000000bf680000 - 00000000bf68e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf68e000 - 00000000bf6e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e0000 - 00000000bf6ee000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf6f0000 - 00000000bf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[COLOR=Red]**[    0.000000]  BIOS-e820: 0000000100000000 - 00000001fc000000 (usable)**[/COLOR]
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1fc000 max_arch_pfn = 0x1000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000094800 (usable)
[    0.000000]  modified: 0000000000094800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
**[COLOR=Red][    0.000000]  modified: 0000000000100000 - 00000000bf680000 (usable)[/COLOR]**
[    0.000000]  modified: 00000000bf680000 - 00000000bf68e000 (ACPI data)
[    0.000000]  modified: 00000000bf68e000 - 00000000bf6e0000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6e0000 - 00000000bf6ee000 (reserved)
[    0.000000]  modified: 00000000bf6f0000 - 00000000bf700000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
**[COLOR=Red][    0.000000]  modified: 0000000100000000 - 00000001fc000000 (usable)[/COLOR]**
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-16000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] RAMDISK: 378b9000 - 37fef342
[    0.000000] Allocated new RAMDISK: 008ac000 - 00fe2342
[    0.000000] Move RAMDISK from 00000000378b9000 - 0000000037fef341 to 008ac000 - 00fe2341
[    0.000000] ACPI: RSDP 000F9E60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT BF680000, 0050 (r1 ACRSYS ACRPRDCT 20070830 MSFT       97)
[    0.000000] ACPI: FACP BF680200, 0084 (r1 ACRSYS FACP0423 20070830 MSFT       97)
[    0.000000] ACPI: DSDT BF6805C0, 6287 (r1  1AAAA 1AAAA000        0 INTL 20051117)
[    0.000000] ACPI: FACS BF68E000, 0040
[    0.000000] ACPI: APIC BF680390, 006C (r1 ACRSYS APIC0423 20070830 MSFT       97)
[    0.000000] ACPI: MCFG BF680400, 003C (r1 ACRSYS OEMMCFG  20070830 MSFT       97)
[    0.000000] ACPI: SLIC BF680440, 0176 (r1 ACRSYS ACRPRDCT 20070830 MSFT       97)
[    0.000000] ACPI: OEMB BF68E040, 0071 (r1 ACRSYS OEMB0423 20070830 MSFT       97)
[    0.000000] ACPI: HPET BF686850, 0038 (r1 ACRSYS OEMHPET  20070830 MSFT       97)
[    0.000000] ACPI: ASF! BF686888, 0099 (r32 LEGEND I865PASF        1 INTL 20051117)
[    0.000000] ACPI: GSCI BF68E0C0, 2024 (r1 ACRSYS GMCHSCI  20070830 MSFT       97)
[    0.000000] ACPI: iEIT BF6900F0, 00B0 (r1 ACRSYS EITTABLE 20070830 MSFT       97)
[    0.000000] ACPI: TCPA BF686930, 0032 (r1 ACRSYS TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: SSDT BF6B2D10, 082F (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 7240MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 00000000 - 377fe000
[    0.000000]   bootmap 00013000 - 00019f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a29ac]    TEXT DATA BSS ==> [0000100000 - 00008a29ac]
[    0.000000]   #4 [00008a3000 - 00008ac000]    INIT_PG_TABLE ==> [00008a3000 - 00008ac000]
[    0.000000]   #5 [0000094800 - 0000100000]    BIOS reserved ==> [0000094800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [00008ac000 - 0000fe2342]      NEW RAMDISK ==> [00008ac000 - 0000fe2342]
[    0.000000]   #8 [0000013000 - 000001a000]          BOOTMAP ==> [0000013000 - 000001a000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x001fc000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000094
[    0.000000]     0: 0x00000100 -> 0x000bf680
[    0.000000]     0: 0x00100000 -> 0x001fc000
[    0.000000] On node 0 totalpages: 1816068
[    0.000000] free_area_init_node: node 0, pgdat c06ded00, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3940 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 14481 pages used for memmap
[    0.000000]   HighMem zone: 1574385 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
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
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000094000 - 0000000000095000
[    0.000000] PM: Registered nosave memory: 0000000000095000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bf700000:3f700000)
[    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1799811
[    0.000000] Kernel command line: root=UUID=a8d7c09b-18d9-48ae-8fb7-6225c01c597d ro  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2327.477 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.010000] allocated 41615040 bytes of page_cgroup
[    0.010000] please try cgroup_disable=memory option if you don't want
[    0.010000] Scanning for low memory corruption every 60 seconds
[    0.010000] Memory: 7141412k/8323072k available (4170k kernel code, 121992k reserved, 2237k data, 548k in
it, 6355464k highmem)
[    0.010000] virtual kernel memory layout:
[    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
[    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
[    0.010000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.010000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.010000]       .init : 0xc0749000 - 0xc07d2000   ( 548 kB)
[    0.010000]       .data : 0xc0512985 - 0xc0741fc0   (2237 kB)
[    0.010000]       .text : 0xc0100000 - 0xc0512985   (4170 kB)
[    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4654.95 BogoMIPS (
lpj=23274770)
[    0.010000] Security Framework initialized
[    0.010000] SELinux:  Disabled at boot.
....

---

