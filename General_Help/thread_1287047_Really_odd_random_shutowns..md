---
title: "Really odd random shutowns."
date: 2009-10-09
forum: General Help
---

### Post by puffinator on 2009-10-09
Ok, I'm running 9.04 on a dell inspiron 1525 and I've got a problem with random shut-downs. what happens is the brightness of the screen is set down to 50(ish)% then back up to the 70% I like, then about 20 seconds later (thankfully time to save) it undergoes what appears to be a completely standard shut-down.
I am aware that it could be to do with a power cord that comes out very easyly and it could be damage done by multiple power-outs but don't know how i whould test this.
As you cant probably tell im a giant ubuntu noob, but i have got a log file, as i know it probably whould help you guys.
I really hope this dosent display the whole thing, i think the code tag should shorten it if not sorry, also i may have put way to much in but i think load time are slightly longer after an unuseuall shutdown.
Thanks for the help.
```


	 	 	 	 	  Oct  9 21:14:33 ianmartin-laptop -- MARK -- 
 Oct  9 21:32:48 ianmartin-laptop exiting on signal 15 
 Oct  9 21:33:21 ianmartin-laptop syslogd 1.5.0#5ubuntu3: restart. 
 Oct  9 21:33:21 ianmartin-laptop kernel: Inspecting /boot/System.map-2.6.28-14-generic 
 Oct  9 21:33:21 ianmartin-laptop kernel: Cannot find map file. 
 Oct  9 21:33:21 ianmartin-laptop kernel: Loaded 55680 symbols from 52 modules. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Initializing cgroup subsys cpu 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Linux version 2.6.28-14-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 (Ubuntu 2.6.28-14.47-generic) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] KERNEL supported cpus: 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   Intel GenuineIntel 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   AMD AuthenticAMD 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   NSC Geode by NSC 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   Cyrix CyrixInstead 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   Centaur CentaurHauls 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   Transmeta GenuineTMx86 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   Transmeta TransmetaCPU 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   UMC UMC UMC UMC 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] BIOS-provided physical RAM map: 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf66d800 (usable) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf66d800 - 00000000c0000000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] DMI 2.4 present. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] last_pfn = 0xbf66d max_arch_pfn = 0x100000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Scanning 2 areas for low memory corruption 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] modified physical RAM map: 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bf66d800 (usable) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000bf66d800 - 00000000c0000000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] RAMDISK: 378b8000 - 37fef5f2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Allocated new RAMDISK: 0087b000 - 00fb25f2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Move RAMDISK from 00000000378b8000 - 0000000037fef5f1 to 0087b000 - 00fb25f1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: RSDP 000FBCB0, 0024 (r2 DELL  ) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: XSDT BF66F200, 0064 (r1 DELL    M08     27D80107 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: FACP BF66F09C, 00F4 (r4 DELL    M08     27D80107 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: DSDT BF66F800, 53D4 (r2 INT430 SYSFexxx     1001 INTL 20050624) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: FACS BF67E000, 0040 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: HPET BF66F300, 0038 (r1 DELL    M08            1 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: APIC BF66F400, 0068 (r1 DELL    M08     27D80107 ASL        47) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: MCFG BF66F3C0, 003E (r16 DELL    M08     27D80107 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: SLIC BF66F49C, 0176 (r1 DELL    M08     27D80107 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: OSFR BF66EA00, 002C (r1 DELL    M08     27D80107 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: BOOT BF66EFC0, 0028 (r1 DELL    M08     27D80107 ASL        61) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: SSDT BF66D9C0, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] 2178MB HIGHMEM available. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] 883MB LOWMEM available. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   mapped low ram: 0 - 373fe000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   low ram: 00000000 - 373fe000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   bootmap 00012000 - 00018e80 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #7 [000087b000 - 0000fb25f2]      NEW RAMDISK ==> [000087b000 - 0000fb25f2] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Zone PFN ranges: 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]   HighMem  0x000373fe -> 0x000bf66d 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Movable zone start PFN for each node 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] early_node_map[4] active PFN ranges 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x00000007 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x00000092 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bf66d 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1]) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1]) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:38000000) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777733 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Kernel command line: root=UUID=561370e2-09e4-4480-ac0d-31c71f439f94 ro quiet splash  
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Initializing CPU#0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Extended CMOS year: 2000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Fast TSC calibration using PIT 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.000000] Detected 1995.134 MHz processor. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Console: colour VGA+ 80x25 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] console [tty0] enabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] allocated 15679620 bytes of page_cgroup 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Memory: 3078688k/3135924k available (4115k kernel code, 55860k reserved, 2196k data, 532k init, 2230716k highmem) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] virtual kernel memory layout: 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]       .data : 0xc0504def - 0xc0729e60   (2196 kB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc0504def   (4115 kB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.26 BogoMIPS (lpj=7980536) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Security Framework initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] SELinux:  Disabled at boot. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] AppArmor: AppArmor initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Mount-cache hash table entries: 512 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Initializing cgroup subsys ns 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Initializing cgroup subsys memory 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Initializing cgroup subsys freezer 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: L2 cache: 2048K 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: Processor Core ID: 0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] using mwait in idle threads. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.018342] ACPI: Core revision 20080926 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.020286] ACPI: Checking initramfs for custom DSDT 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.316479] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.358574] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.360001] Booting processor 1 APIC 0x1 ip 0x6000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Initializing CPU#1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3989.97 BogoMIPS (lpj=7979948) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: L2 cache: 2048K 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.004000] CPU: Processor Core ID: 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.444441] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.444457] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448033] Brought up 2 CPUs 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448036] Total of 2 processors activated (7980.24 BogoMIPS). 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448173] net_namespace: 776 bytes 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448173] Booting paravirtualized kernel on bare hardware 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] Time: 20:33:07  Date: 10/09/09 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] regulator: core version 0.5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] NET: Registered protocol family 16 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] EISA bus registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] ACPI: bus type pci registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] PCI: MCFG area at f8000000 reserved in E820 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] PCI: Using MMCONFIG for extended config space 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.448319] PCI: Using configuration type 1 for base access 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.479223] ACPI: Interpreter enabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.479227] ACPI: (supports S0 S3 S4 S5) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.479244] ACPI: Using IOAPIC for interrupt routing 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.522928] ACPI: No dock devices found. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.522938] ACPI: PCI Root Bridge [PCI0] (0000:00) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523383] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523389] pci 0000:00:1a.7: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523494] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523499] pci 0000:00:1b.0: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523573] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523578] pci 0000:00:1c.0: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523653] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523658] pci 0000:00:1c.1: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523737] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.523742] pci 0000:00:1c.4: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524075] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524080] pci 0000:00:1d.7: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524250] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524255] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524469] pci 0000:00:1f.2: PME# supported from D3hot 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524474] pci 0000:00:1f.2: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524717] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.524724] pci 0000:09:00.0: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525172] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525185] pci 0000:0b:00.0: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525507] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525512] pci 0000:02:09.0: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525612] pci 0000:02:09.1: PME# supported from D0 D1 D2 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525617] pci 0000:02:09.1: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525719] pci 0000:02:09.2: PME# supported from D0 D1 D2 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525724] pci 0000:02:09.2: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525825] pci 0000:02:09.3: PME# supported from D0 D1 D2 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525830] pci 0000:02:09.3: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525930] pci 0000:02:09.4: PME# supported from D0 D1 D2 D3hot D3cold 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525935] pci 0000:02:09.4: PME# disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.525992] pci 0000:00:1e.0: transparent bridge 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.538677] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.538811] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.538944] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539065] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539202] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539337] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539472] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539593] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539829] ACPI: WMI: Mapper loaded 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.539864] SCSI subsystem initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.540032] usbcore: registered new interface driver usbfs 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.540047] usbcore: registered new interface driver hub 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.540061] usbcore: registered new device driver usb 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.540061] PCI: Using ACPI for IRQ routing 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544010] Bluetooth: Core ver 2.13 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544023] NET: Registered protocol family 31 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544023] Bluetooth: HCI device and connection manager initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544023] Bluetooth: HCI socket layer initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544023] NET: Registered protocol family 8 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544023] NET: Registered protocol family 20 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544032] NetLabel: Initializing 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544033] NetLabel:  domain hash size = 128 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544035] NetLabel:  protocols = UNLABELED CIPSOv4 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544047] NetLabel:  unlabeled traffic allowed by default 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544062] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.544067] hpet0: 3 comparators, 64-bit 14.318180 MHz counter 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.548057] AppArmor: AppArmor Filesystem Enabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.556009] pnp: PnP ACPI init 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.556017] ACPI: bus type pnp registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.576908] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.576911] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.577008] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.577011] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.577014] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.577017] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600097] pnp: PnP ACPI: found 13 devices 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600099] ACPI: ACPI bus type pnp unregistered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600102] PnPBIOS: Disabled by ACPI PNP 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600111] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600114] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600122] system 00:06: ioport range 0xc80-0xcff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600128] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600134] system 00:0a: ioport range 0x900-0x97f has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600137] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600142] system 00:0b: ioport range 0xf400-0xf4fe has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600145] system 00:0b: ioport range 0x1080-0x10bf has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600148] system 00:0b: ioport range 0x10c0-0x10df has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600150] system 00:0b: ioport range 0x809-0x809 has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600156] system 00:0c: iomem range 0x0-0x9efff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600159] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600161] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600164] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600167] system 00:0c: iomem range 0x100000-0xbf66d7ff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600169] system 00:0c: iomem range 0xbf66d800-0xbf6fffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600172] system 00:0c: iomem range 0xbf700000-0xbf7fffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600175] system 00:0c: iomem range 0xbf700000-0xbfefffff could not be reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600177] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600180] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600183] system 00:0c: iomem range 0xfec00000-0xfec0ffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600185] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600188] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600190] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600193] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600195] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600198] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600200] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.600203] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634909] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634913] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634920] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe8fffff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634925] pci 0000:00:1c.0:   PREFETCH window: disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634933] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634935] pci 0000:00:1c.1:   IO window: disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634941] pci 0000:00:1c.1:   MEM window: 0xfe700000-0xfe7fffff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634946] pci 0000:00:1c.1:   PREFETCH window: disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634955] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634958] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634965] pci 0000:00:1c.4:   MEM window: 0xfe400000-0xfe6fffff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634970] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634979] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634981] pci 0000:00:1e.0:   IO window: disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634987] pci 0000:00:1e.0:   MEM window: 0xfe300000-0xfe3fffff 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.634993] pci 0000:00:1e.0:   PREFETCH window: disabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635011] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635027] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635042] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635060] bus: 00 index 0 io port: [0x00-0xffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635062] bus: 00 index 1 mmio: [0x000000-0xffffffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635064] bus: 09 index 0 io port: [0xd000-0xdfff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635067] bus: 09 index 1 mmio: [0xfe800000-0xfe8fffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635069] bus: 09 index 2 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635070] bus: 09 index 3 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635072] bus: 0b index 0 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635074] bus: 0b index 1 mmio: [0xfe700000-0xfe7fffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635076] bus: 0b index 2 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635078] bus: 0b index 3 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635080] bus: 0c index 0 io port: [0xc000-0xcfff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635082] bus: 0c index 1 mmio: [0xfe400000-0xfe6fffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635084] bus: 0c index 2 mmio: [0xf0000000-0xf01fffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635086] bus: 0c index 3 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635088] bus: 02 index 0 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635089] bus: 02 index 1 mmio: [0xfe300000-0xfe3fffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635091] bus: 02 index 2 mmio: [0x0-0x0] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635093] bus: 02 index 3 io port: [0x00-0xffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635095] bus: 02 index 4 mmio: [0x000000-0xffffffff] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.635103] NET: Registered protocol family 2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.648049] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.648274] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.648598] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.648773] TCP: Hash tables configured (established 131072 bind 65536) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.648776] TCP reno registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.652061] NET: Registered protocol family 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    0.652174] checking if image is initramfs... it is 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.254385] Freeing initrd memory: 7389k freed 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.254423] Simple Boot Flag at 0x79 set to 0x1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.254599] cpufreq: No nForce2 chipset. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.254730] audit: initializing netlink socket (disabled) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.254753] type=2000 audit(1255120387.252:1): initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.261817] highmem bounce pool size: 64 pages 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.261821] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263094] VFS: Disk quotas dquot_6.5.1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263150] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263733] fuse init (API version 7.10) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263813] msgmni has been set to 1672 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263975] alg: No test for stdrng (krng) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263984] io scheduler noop registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263986] io scheduler anticipatory registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.263988] io scheduler deadline registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.264001] io scheduler cfq registered (default) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.266098] pcieport-driver 0000:00:1c.0: found MSI capability 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.266309] pcieport-driver 0000:00:1c.1: found MSI capability 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.266514] pcieport-driver 0000:00:1c.4: found MSI capability 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.266677] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.266757] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.266889] ACPI: AC Adapter [AC] (on-line) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.296399] ACPI: Battery Slot [BAT0] (battery present) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.296471] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.297109] ACPI: Lid Switch [LID] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.297151] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.297157] ACPI: Power Button (CM) [PBTN] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.297196] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.297198] ACPI: Sleep Button (CM) [SBTN] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.297730] ACPI: SSDT BF66E4F6, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.298092] ACPI: SSDT BF66DE8C, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.298489] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.298513] processor ACPI_CPU:00: registered as cooling_device0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.298517] ACPI: Processor [CPU0] (supports 8 throttling states) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.298834] ACPI: SSDT BF66E77C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.299159] ACPI: SSDT BF66E471, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.299579] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3]) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.299597] processor ACPI_CPU:01: registered as cooling_device1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.299600] ACPI: Processor [CPU1] (supports 8 throttling states) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.301327] thermal LNXTHERM:01: registered as thermal_zone0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.301525] ACPI: Thermal Zone [THM] (83 C) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.301579] isapnp: Scanning for PnP cards... 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.655589] isapnp: No Plug & Play device found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.665166] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666171] brd: module loaded 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666461] loop: module loaded 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666523] Fixed MDIO Bus: probed 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666528] PPP generic driver version 2.4.2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666582] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666610] Driver 'sd' needs updating - please use bus_type methods 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666618] Driver 'sr' needs updating - please use bus_type methods 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666668] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666781] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666784] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems  
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.666960] scsi0 : ahci 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.667042] scsi1 : ahci 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.667097] scsi2 : ahci 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.667336] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 2300 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.667338] ata2: DUMMY 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    1.667341] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 2300 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.208021] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.576569] ata1.00: ATA-8: TOSHIBA MK2546GSX, LB013D, max UDMA/100 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.576571] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.577413] ata1.00: configured for UDMA/100 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.912020] ata3: SATA link down (SStatus 0 SControl 300) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928102] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2546GS LB01 PQ: 0 ANSI: 5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928192] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928207] sd 0:0:0:0: [sda] Write Protect is off 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928234] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928290] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928304] sd 0:0:0:0: [sda] Write Protect is off 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928330] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    2.928333]  sda: sda1 sda2 < sda5 sda6 sda7 > 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.039103] sd 0:0:0:0: [sda] Attached SCSI disk 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.039140] sd 0:0:0:0: Attached scsi generic sg0 type 0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.039192] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.039293] scsi3 : ata_piix 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.039347] scsi4 : ata_piix 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.040007] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.040010] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.204502] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.220461] ata4.00: configured for UDMA/33 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.228886] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.239816] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.239818] Uniform CD-ROM driver Revision: 3.20 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.239934] sr 3:0:0:0: Attached scsi generic sg1 type 5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.240596] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.240616] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.240633] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.240688] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.244604] ehci_hcd 0000:00:1a.7: debug port 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.244624] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260070] usb usb1: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260095] hub 1-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260102] hub 1-0:1.0: 4 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260203] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260217] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.260260] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.264165] ehci_hcd 0000:00:1d.7: debug port 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.264185] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280070] usb usb2: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280093] hub 2-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280100] hub 2-0:1.0: 6 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280196] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280212] uhci_hcd: USB Universal Host Controller Interface driver 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280231] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280241] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280280] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280308] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280381] usb usb3: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280404] hub 3-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280411] hub 3-0:1.0: 2 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280489] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280499] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280539] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280574] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280647] usb usb4: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280670] hub 4-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280676] hub 4-0:1.0: 2 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280756] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280768] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280806] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280833] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280900] usb usb5: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280925] hub 5-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.280931] hub 5-0:1.0: 2 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281008] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281019] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281061] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281089] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281162] usb usb6: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281185] hub 6-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281191] hub 6-0:1.0: 2 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281274] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281286] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281324] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281350] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281417] usb usb7: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281440] hub 7-0:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281446] hub 7-0:1.0: 2 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.281586] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.302357] i8042.c: Detected active multiplexing controller, rev 1.1. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.314192] serio: i8042 KBD port at 0x60,0x64 irq 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.314197] serio: i8042 AUX0 port at 0x60,0x64 irq 12 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.314200] serio: i8042 AUX1 port at 0x60,0x64 irq 12 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.314202] serio: i8042 AUX2 port at 0x60,0x64 irq 12 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.314204] serio: i8042 AUX3 port at 0x60,0x64 irq 12 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.316037] mice: PS/2 mouse device common for all mice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332066] rtc_cmos 00:04: RTC can wake from S4 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332095] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332128] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332185] device-mapper: uevent: version 1.0.3 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332260] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332327] device-mapper: multipath: version 1.0.5 loaded 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332330] device-mapper: multipath round-robin: version 1.0.0 loaded 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332397] EISA: Probing bus 0 at eisa.0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332404] Cannot allocate resource for EISA slot 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332435] EISA: Detected 0 cards. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332544] cpuidle: using governor ladder 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.332657] cpuidle: using governor menu 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333138] TCP cubic registered 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333228] NET: Registered protocol family 10 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333629] lo: Disabled Privacy Extensions 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333948] NET: Registered protocol family 17 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333963] Bluetooth: L2CAP ver 2.11 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333965] Bluetooth: L2CAP socket layer initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333968] Bluetooth: SCO (Voice Link) ver 0.6 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333970] Bluetooth: SCO socket layer initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.333998] Bluetooth: RFCOMM socket layer initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334004] Bluetooth: RFCOMM TTY layer initialized 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334006] Bluetooth: RFCOMM ver 1.10 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334012] Marking TSC unstable due to TSC halts in idle 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334627] Using IPI No-Shortcut mode 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334690] registered taskstats version 1 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334816]   Magic number: 13:850:598 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334911] rtc_cmos 00:04: setting system clock to 2009-10-09 20:33:10 UTC (1255120390) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334914] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.334916] EDD information not available. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.335182] Freeing unused kernel memory: 532k freed 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.335335] Write protecting the kernel text: 4116k 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.335395] Write protecting the kernel read-only data: 1524k 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.371163] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.518346] sky2 driver version 1.22 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.518399] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.518471] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.520241] sky2 eth0: addr 00:1d:09:40:db:cf 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.593024] usb 1-1: new high speed USB device using ehci_hcd and address 2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.715367] ohci1394 0000:02:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.766156] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    3.782611] usb 1-1: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.029422] PM: Starting manual resume from disk 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.085311] kjournald starting.  Commit interval 5 seconds 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.085326] EXT3-fs: mounted filesystem with ordered data mode. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.189049] usb 6-2: new low speed USB device using uhci_hcd and address 2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.342285] usb 6-2: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.584078] usb 7-2: new full speed USB device using uhci_hcd and address 2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.756513] usb 7-2: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.758469] hub 7-2:1.0: USB hub found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    4.760429] hub 7-2:1.0: 3 ports detected 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    5.041432] usb 7-2.2: new full speed USB device using uhci_hcd and address 3 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    5.171485] usb 7-2.2: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    5.249428] usb 7-2.3: new full speed USB device using uhci_hcd and address 4 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    5.379518] usb 7-2.3: configuration #1 chosen from 1 choice 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.492469] udev: starting version 141 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.753175] cfg80211: Calling CRDA to update world regulatory domain 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.829967] sdhci: Secure Digital Host Controller Interface driver 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.829970] sdhci: Copyright(c) Pierre Ossman 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.845232] usbcore: registered new interface driver hiddev 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.858482] input: HID 062a:0000 as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input5 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.860142] generic-usb 0003:062A:0000.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.1-2/input0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.863816] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input6 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.864312] iTCO_vendor_support: vendor-support=0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.864877] ricoh-mmc: Ricoh MMC Controller disabling driver 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.864880] ricoh-mmc: Copyright(c) Philip Langdale 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.864913] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.864932] ricoh-mmc: Controller is now disabled. 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.866224] sdhci-pci 0000:02:09.1: SDHCI controller found [1180:0822] (rev 22) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.866247] sdhci-pci 0000:02:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.869523] mmc0: SDHCI controller on PCI [0000:02:09.1] using DMA 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.873832] Linux agpgart interface v0.103 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.874508] generic-usb 0003:0A5C:4502.0002: input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2/input0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.879849] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input7 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.887695] agpgart-intel 0000:00:00.0: Intel 965GM Chipset 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.889424] agpgart-intel 0000:00:00.0: detected 7676K stolen memory 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.893466] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.894174] generic-usb 0003:0A5C:4503.0003: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.894195] usbcore: registered new interface driver usbhid 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.894217] usbhid: v2.6:USB HID core driver 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.920234] acpi device:31: registered as cooling_device2 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.920719] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/input/input8 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.928204] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.928322] ACPI Warning (nspredef-0357): \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) [20080926] 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.928431] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:33/input/input9 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.931294] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.943205] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.943353] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.943485] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [    9.946620] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027796] cfg80211: World regulatory domain updated: 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027800] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027802] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027804] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027806] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027808] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.027810] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.130475] Linux video capture interface: v2.00 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.165454] input: PC Speaker as /devices/platform/pcspkr/input/input10 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.246915] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.247963] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input11 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.249182] usbcore: registered new interface driver uvcvideo 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.249220] USB Video Class driver (v0.1.0) 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.387996] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.650399] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.650402] iwl3945: Copyright(c) 2003-2008 Intel Corporation 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.650506] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.650640] iwl3945: Detected Intel Wireless WiFi Link 3945ABG 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.702419] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   10.707234] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   11.099768] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input12 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   11.129782] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input13 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   11.305738] lp: driver loaded but no devices found 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   11.440556] Adding 9044552k swap on /dev/sda5.  Priority:-1 extents:1 across:9044552k 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   11.974796] EXT3 FS on sda1, internal journal 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.113067] type=1505 audit(1255120400.278:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2233 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.153880] type=1505 audit(1255120400.318:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2237 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.153975] type=1505 audit(1255120400.318:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2237 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.154011] type=1505 audit(1255120400.318:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2237 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.154043] type=1505 audit(1255120400.318:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2237 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.282758] type=1505 audit(1255120400.445:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2242 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.282923] type=1505 audit(1255120400.445:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2242 
 Oct  9 21:33:21 ianmartin-laptop kernel: [   13.312086] type=1505 audit(1255120400.474:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2246 
 Oct  9 21:33:27 ianmartin-laptop kernel: [   20.275201] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x23b4 
 Oct  9 21:33:27 ianmartin-laptop kernel: [   20.275245] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'. 
 Oct  9 21:33:29 ianmartin-laptop kernel: [   22.127172] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 Oct  9 21:33:29 ianmartin-laptop kernel: [   22.127175] Bluetooth: BNEP filters: protocol multicast 
 Oct  9 21:33:29 ianmartin-laptop kernel: [   22.178620] Bridge firewalling registered 
 Oct  9 21:33:30 ianmartin-laptop kernel: [   23.329187] ppdev: user-space parallel port driver 
 Oct  9 21:33:32 ianmartin-laptop kernel: [   25.396343] [drm] Initialized drm 1.1.0 20060810 
 Oct  9 21:33:32 ianmartin-laptop kernel: [   25.427691] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Oct  9 21:33:32 ianmartin-laptop kernel: [   25.427902] [drm] Initialized i915 1.6.0 20080730 on minor 0 
 Oct  9 21:33:33 ianmartin-laptop kernel: [   26.122418] vloopback: Video4linux loopback driver v1.1.5 
 Oct  9 21:33:33 ianmartin-laptop kernel: [   26.122490] vloopback: Loopback 0 registered, input: video2, output: video1 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   26.839250] sky2 eth0: enabling interface 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   26.839431] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   26.840041] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   27.020251] Registered led device: iwl-phy0:radio 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   27.020268] Registered led device: iwl-phy0:assoc 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   27.020282] Registered led device: iwl-phy0:RX 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   27.020304] Registered led device: iwl-phy0:TX 
 Oct  9 21:33:34 ianmartin-laptop kernel: [   27.028161] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 Oct  9 21:34:33 ianmartin-laptop kernel: [   86.500157] Clocksource tsc unstable (delta = -252310737 ns) 
 Oct  9 21:34:42 ianmartin-laptop kernel: [   95.589866] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
 Oct  9 21:53:22 ianmartin-laptop -- MARK --
 
```

---

### Post by puffinator on 2009-10-10
please help- data loss with slow saveing programs is really getting bad.

---

### Post by puffinator on 2009-10-10
re-bump

---

### Post by ragtag on 2009-10-11
I've been having a similar problem today, and I think I figured out why.

I have a HP TC4400 TabletPC running Ubuntu 9.04 32bit. And I've been drawing in GIMP all day in full screen mode (open an image, hit F11 and draw something). When doing that I flip the screen around to tablet mode, and use a pen. I also tend to rotate the laptop quite a bit around for more convenient angles to draw at.

Now here comes the silly bit. The screen has a single button at the edge of it for ctrl-alt-del. In windows, this would bring up the task manager. In Ubuntu, it brings up the Shut Down window. Since I'm running GIMP in full screen, the Shut Down window generally shows up BEHIND the GIMP, and I never see it. The shut down window has a 60 sec timer, so if you don't hit cancel within those 60 sec, your machine will shut down. I've now changed the Log Out shortcut in System>Preferences>Keyboard Shortcuts to Shift+Ctrl+Alt+Del, so hopefully that solves my problem.  :)

I don't know if your Dell laptop has a similar button, but the same thing can also happen when you press the power button...depending on your Power Settings. You can go into System>Preferences>Power Management under the General tab, to see what your Power button is set to do. It might be set to simply shut down your computer straight away.

Cheers...

---

### Post by puffinator on 2009-10-11
thanks, but i think this may be a different thing, as none of my shutdown methods include changeing screen brightness to 50%. im going to try a fresh install tommorow so hopefully that should cleen it, also i have had this happening while one small window only was open. I also tryed a memtest 86+ based on advise from irc, and although no errors were found the same thing happened. all in all, im glad i have a warrenty for this.

---

### Post by tgalati4 on 2009-10-11
Check and clean your battery contacts.  Also, a defective battery will drop voltage (~10 VDC) which causes APCI to issue an immediate (and hidden) shutdown command.  All it takes is one cell (out of 6 or 9) to go bad and it will trigger the low-voltage shutdown.

Pull the battery after the next shutdown and measure the voltage with a meter.  Anything less than 11 VDC means a possibly defective (or worn-out) battery.

Modern laptop batteries are only good for 300 cycles and they start showing their age at 200 cycles.  How many cycles on yours?

---

### Post by puffinator on 2009-10-12
i haven't been able to use the battery for quite some time, its only working on ac power now. so this sounds like it could be the issue. will test it asap. thanks for the help.

---

### Post by tgalati4 on 2009-10-13
Well, if your battery is bad, it will pull excessive amperage trying to charge with one or more cells shorted.  The power supply has a resetable fuse that lets go when too much current is pulled.

Without a working battery, when the AC adapter lets go, you have no options except immediate power off.

---

### Post by puffinator on 2009-10-13
reinstalled and problemwent away, no idea why but hey it works. \\:D/
thanks for the help everyone.

---

