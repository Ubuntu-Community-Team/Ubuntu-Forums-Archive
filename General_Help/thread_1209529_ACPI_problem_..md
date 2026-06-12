---
title: "ACPI problem ."
date: 2009-07-10
forum: General Help
---

### Post by rsiddharth on 2009-07-10
I first started a thread in Absolute Beginner Talk named ' ubuntu comes to a Standstill ' , here is the link to that thread to get a glimpse of how it ( the ACPI error  ) was inferred 

The Link - [http://ubuntuforums.org/showthread.php?t=1206250](http://ubuntuforums.org/showthread.php?t=1206250) 

 [nhasian]("http://ubuntuforums.org/member.php?u=566669") gave  solution  , this , the solution ,  I would only recover from the crash but not stop as it kept happening ( the crash ) . Many pointed to video driver problems  , but  when i uploaded the information from ' Log File Viewer '  , [change_mode]("http://ubuntuforums.org/member.php?u=602293") inferred ( after going through the log )  that a ACPI error should have caused the crash ( you may find log info in the #20 post in the thread ' ubuntu comes to a still ' posted by  [change_mode]("http://ubuntuforums.org/member.php?u=602293") ) . 


Can anyone help me with this problem . I have uploaded the log file , please view it for your perusal . though  [change_mode]("http://ubuntuforums.org/member.php?u=602293")  as pasted a  important snippet of the log information that may point to the error in his #20 in ' ubuntu comes to Stansdill ' under Absolute Beginner Talk '  

Note : The crash occured somwhere between 8:42AM and 10:33AM and the ACPI error as it seems occured ~10:32AM . 

My advance Thanks for your help . :p

---

### Post by change_mode on 2009-07-10
I don't think people are going to read the other topic, so here's the error:

```
Jul 9 10:32:26 innov kernel: [ 1094.652342] ACPI Error (psargs-0358): [\_TZ_.THRM] Namespace lookup
failure, AE_NOT_FOUND
Jul 9 10:32:26 innov kernel: [ 1094.652353] ACPI Error (psparse-0524): Method parse/execution failed
[\_GPE._L1C] (Node f6c1f468), AE_NOT_FOUND
Jul 9 10:32:26 innov kernel: [ 1094.652383] ACPI Exception (evgpe-0571): AE_NOT_FOUND, while
evaluating GPE method [_L1C] [20080926]
Jul 9 10:32:57 innov syslogd 1.5.0#5ubuntu3: restart.
```

---

### Post by rsiddharth on 2009-07-11
The crash happened again and this time I noted the time of the crash . It happened at**  9:23pm 11July 2009 **. I used Alt+prntscreen + REISUB to recover my system . 

Here is the Log taken from ' messages ' section in the Log viewer . 

```
Jul 11 21:13:19 innov kernel: [ 8066.214763] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 11 21:13:19 innov kernel: [ 8066.214961] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 11 21:13:33 innov kernel: [ 8080.823075] eth0: link down
Jul 11 21:13:35 innov kernel: [ 8082.465214] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 11 21:24:27 innov kernel: [ 8733.983728] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK aLlcpus showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks 
Jul 11 21:24:30 innov kernel: [ 8736.703408] SysRq : Keyboard mode set to system default
Jul 11 21:24:31 innov exiting on signal 15
Jul 11 21:25:06 innov syslogd 1.5.0#5ubuntu3: restart.
Jul 11 21:25:06 innov kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul 11 21:25:06 innov kernel: Cannot find map file.
Jul 11 21:25:06 innov kernel: Loaded 53928 symbols from 41 modules.
Jul 11 21:25:06 innov kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jul 11 21:25:06 innov kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 11 21:25:06 innov kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 11 21:25:06 innov kernel: [    0.000000] Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
Jul 11 21:25:06 innov kernel: [    0.000000] KERNEL supported cpus:
Jul 11 21:25:06 innov kernel: [    0.000000]   Intel GenuineIntel
Jul 11 21:25:06 innov kernel: [    0.000000]   AMD AuthenticAMD
Jul 11 21:25:06 innov kernel: [    0.000000]   NSC Geode by NSC
Jul 11 21:25:06 innov kernel: [    0.000000]   Cyrix CyrixInstead
Jul 11 21:25:06 innov kernel: [    0.000000]   Centaur CentaurHauls
Jul 11 21:25:06 innov kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 11 21:25:06 innov kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 11 21:25:06 innov kernel: [    0.000000]   UMC UMC UMC UMC
Jul 11 21:25:06 innov kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000004f7c0000 (usable)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 000000004f7c0000 - 000000004f7ce000 (ACPI data)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 000000004f7ce000 - 000000004f7f0000 (ACPI NVS)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 000000004f7f0000 - 000000004f800000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000] DMI 2.3 present.
Jul 11 21:25:06 innov kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
Jul 11 21:25:06 innov kernel: [    0.000000] last_pfn = 0x4f7c0 max_arch_pfn = 0x100000
Jul 11 21:25:06 innov kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jul 11 21:25:06 innov kernel: [    0.000000] modified physical RAM map:
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 0000000000100000 - 000000004f7c0000 (usable)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 000000004f7c0000 - 000000004f7ce000 (ACPI data)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 000000004f7ce000 - 000000004f7f0000 (ACPI NVS)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 000000004f7f0000 - 000000004f800000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000]  modified: 00000000ffb80000 - 0000000100000000 (reserved)
Jul 11 21:25:06 innov kernel: [    0.000000] RAMDISK: 378bc000 - 37fefc98
Jul 11 21:25:06 innov kernel: [    0.000000] Allocated new RAMDISK: 0087b000 - 00faec98
Jul 11 21:25:06 innov kernel: [    0.000000] Move RAMDISK from 00000000378bc000 - 0000000037fefc97 to 0087b000 - 00faec97
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: RSDP 000FB5E0, 0014 (r0 ACPIAM)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: RSDT 4F7C0000, 0034 (r1 A M I  OEMRSDT   4000529 MSFT       97)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: FACP 4F7C0200, 0081 (r1 A M I  OEMFACP   4000529 MSFT       97)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: DSDT 4F7C0400, 4403 (r1  A0005 A0005085       85 INTL  2002026)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: FACS 4F7CE000, 0040
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: APIC 4F7C0390, 0070 (r1 A M I  OEMAPIC   4000529 MSFT       97)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: OEMB 4F7CE040, 0059 (r1 A M I  AMI_OEM   4000529 MSFT       97)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: MCFG 4F7C4810, 003C (r1 A M I  OEMMCFG   4000529 MSFT       97)
Jul 11 21:25:06 innov kernel: [    0.000000] 387MB HIGHMEM available.
Jul 11 21:25:06 innov kernel: [    0.000000] 883MB LOWMEM available.
Jul 11 21:25:06 innov kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Jul 11 21:25:06 innov kernel: [    0.000000]   low ram: 00000000 - 373fe000
Jul 11 21:25:06 innov kernel: [    0.000000]   bootmap 00012000 - 00018e80
Jul 11 21:25:06 innov kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
Jul 11 21:25:06 innov kernel: [    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jul 11 21:25:06 innov kernel: [    0.000000]   #7 [000087b000 - 0000faec98]      NEW RAMDISK ==> [000087b000 - 0000faec98]
Jul 11 21:25:06 innov kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jul 11 21:25:06 innov kernel: [    0.000000] found SMP MP-table at [c00ff780] 000ff780
Jul 11 21:25:06 innov kernel: [    0.000000] Zone PFN ranges:
Jul 11 21:25:06 innov kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 11 21:25:06 innov kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Jul 11 21:25:06 innov kernel: [    0.000000]   HighMem  0x000373fe -> 0x0004f7c0
Jul 11 21:25:06 innov kernel: [    0.000000] Movable zone start PFN for each node
Jul 11 21:25:06 innov kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 11 21:25:06 innov kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 11 21:25:06 innov kernel: [    0.000000]     0: 0x00000100 -> 0x0004f7c0
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 11 21:25:06 innov kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 11 21:25:06 innov kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 11 21:25:06 innov kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 11 21:25:06 innov kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 11 21:25:06 innov kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jul 11 21:25:06 innov kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 11 21:25:06 innov kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Jul 11 21:25:06 innov kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jul 11 21:25:06 innov kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 4f800000:b0380000)
Jul 11 21:25:06 innov kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Jul 11 21:25:06 innov kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322911
Jul 11 21:25:06 innov kernel: [    0.000000] Kernel command line: root=UUID=badef8ef-3d86-428f-920c-9dfd9d92f36c ro quiet splash 
Jul 11 21:25:06 innov kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 11 21:25:06 innov kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 11 21:25:06 innov kernel: [    0.000000] Initializing CPU#0
Jul 11 21:25:06 innov kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 11 21:25:06 innov kernel: [    0.000000] Fast TSC calibration using PIT
Jul 11 21:25:06 innov kernel: [    0.000000] Detected 3065.463 MHz processor.
Jul 11 21:25:06 innov kernel: [    0.004000] Console: colour VGA+ 80x25
Jul 11 21:25:06 innov kernel: [    0.004000] console [tty0] enabled
Jul 11 21:25:06 innov kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 11 21:25:06 innov kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 11 21:25:06 innov kernel: [    0.004000] allocated 6511040 bytes of page_cgroup
Jul 11 21:25:06 innov kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Jul 11 21:25:06 innov kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Jul 11 21:25:06 innov kernel: [    0.004000] Memory: 1268464k/1302272k available (4110k kernel code, 32504k reserved, 2196k data, 532k init, 397064k highmem)
Jul 11 21:25:06 innov kernel: [    0.004000] virtual kernel memory layout:
Jul 11 21:25:06 innov kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jul 11 21:25:06 innov kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jul 11 21:25:06 innov kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Jul 11 21:25:06 innov kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Jul 11 21:25:06 innov kernel: [    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
Jul 11 21:25:06 innov kernel: [    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
Jul 11 21:25:06 innov kernel: [    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)
Jul 11 21:25:06 innov kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 11 21:25:06 innov kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jul 11 21:25:06 innov kernel: [    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 6130.92 BogoMIPS (lpj=12261852)
Jul 11 21:25:06 innov kernel: [    0.004039] Security Framework initialized
Jul 11 21:25:06 innov kernel: [    0.004050] SELinux:  Disabled at boot.
Jul 11 21:25:06 innov kernel: [    0.004074] AppArmor: AppArmor initialized
Jul 11 21:25:06 innov kernel: [    0.004087] Mount-cache hash table entries: 512
Jul 11 21:25:06 innov kernel: [    0.004257] Initializing cgroup subsys ns
Jul 11 21:25:06 innov kernel: [    0.004263] Initializing cgroup subsys cpuacct
Jul 11 21:25:06 innov kernel: [    0.004267] Initializing cgroup subsys memory
Jul 11 21:25:06 innov kernel: [    0.004272] Initializing cgroup subsys freezer
Jul 11 21:25:06 innov kernel: [    0.004293] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jul 11 21:25:06 innov kernel: [    0.004297] CPU: L2 cache: 1024K
Jul 11 21:25:06 innov kernel: [    0.004300] CPU: Hyper-Threading is disabled
Jul 11 21:25:06 innov kernel: [    0.004305] using mwait in idle threads.
Jul 11 21:25:06 innov kernel: [    0.004318] Checking 'hlt' instruction... OK.
Jul 11 21:25:06 innov kernel: [    0.020896] SMP alternatives: switching to UP code
Jul 11 21:25:06 innov kernel: [    0.144023] ACPI: Core revision 20080926
Jul 11 21:25:06 innov kernel: [    0.148484] ACPI: Checking initramfs for custom DSDT
Jul 11 21:25:06 innov kernel: [    0.432525] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 11 21:25:06 innov kernel: [    0.473675] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 01
Jul 11 21:25:06 innov kernel: [    0.476001] Brought up 1 CPUs
Jul 11 21:25:06 innov kernel: [    0.476001] Total of 1 processors activated (6130.92 BogoMIPS).
Jul 11 21:25:06 innov kernel: [    0.476001] net_namespace: 776 bytes
Jul 11 21:25:06 innov kernel: [    0.476001] Booting paravirtualized kernel on bare hardware
Jul 11 21:25:06 innov kernel: [    0.476001] Time: 21:24:55  Date: 07/11/09
Jul 11 21:25:06 innov kernel: [    0.476001] regulator: core version 0.5
Jul 11 21:25:06 innov kernel: [    0.476001] NET: Registered protocol family 16
Jul 11 21:25:06 innov kernel: [    0.476001] EISA bus registered
Jul 11 21:25:06 innov kernel: [    0.476001] ACPI: bus type pci registered
Jul 11 21:25:06 innov kernel: [    0.476001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 11 21:25:06 innov kernel: [    0.476001] PCI: Not using MMCONFIG.
Jul 11 21:25:06 innov kernel: [    0.476001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
Jul 11 21:25:06 innov kernel: [    0.476001] PCI: Using configuration type 1 for base access
Jul 11 21:25:06 innov kernel: [    0.484179] ACPI: Interpreter enabled
Jul 11 21:25:06 innov kernel: [    0.484185] ACPI: (supports S0 S1 S3 S4 S5)
Jul 11 21:25:06 innov kernel: [    0.484212] ACPI: Using IOAPIC for interrupt routing
Jul 11 21:25:06 innov kernel: [    0.484280] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 11 21:25:06 innov kernel: [    0.489440] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jul 11 21:25:06 innov kernel: [    0.489444] PCI: Using MMCONFIG for extended config space
Jul 11 21:25:06 innov kernel: [    0.496824] ACPI: No dock devices found.
Jul 11 21:25:06 innov kernel: [    0.496889] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 11 21:25:06 innov kernel: [    0.497112] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 11 21:25:06 innov kernel: [    0.497117] pci 0000:00:1b.0: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.497167] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 11 21:25:06 innov kernel: [    0.497172] pci 0000:00:1c.0: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.497478] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 11 21:25:06 innov kernel: [    0.497483] pci 0000:00:1d.7: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.497604] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Jul 11 21:25:06 innov kernel: [    0.497608] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Jul 11 21:25:06 innov kernel: [    0.497747] pci 0000:00:1f.2: PME# supported from D3hot
Jul 11 21:25:06 innov kernel: [    0.497752] pci 0000:00:1f.2: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.497962] pci 0000:02:01.0: PME# supported from D2 D3hot D3cold
Jul 11 21:25:06 innov kernel: [    0.497967] pci 0000:02:01.0: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.498051] pci 0000:02:02.0: PME# supported from D1 D2 D3hot D3cold
Jul 11 21:25:06 innov kernel: [    0.498056] pci 0000:02:02.0: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.498145] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
Jul 11 21:25:06 innov kernel: [    0.498150] pci 0000:02:04.0: PME# disabled
Jul 11 21:25:06 innov kernel: [    0.498194] pci 0000:00:1e.0: transparent bridge
Jul 11 21:25:06 innov kernel: [    0.501046] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.501198] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.501347] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.501499] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.501649] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.501800] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.501949] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 11 21:25:06 innov kernel: [    0.502100] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 11 21:25:06 innov kernel: [    0.502251] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - FC, should be F8 [20080926]
Jul 11 21:25:06 innov kernel: [    0.502278] ACPI: WMI: Mapper loaded
Jul 11 21:25:06 innov kernel: [    0.502490] SCSI subsystem initialized
Jul 11 21:25:06 innov kernel: [    0.502586] usbcore: registered new interface driver usbfs
Jul 11 21:25:06 innov kernel: [    0.502607] usbcore: registered new interface driver hub
Jul 11 21:25:06 innov kernel: [    0.502636] usbcore: registered new device driver usb
Jul 11 21:25:06 innov kernel: [    0.502768] PCI: Using ACPI for IRQ routing
Jul 11 21:25:06 innov kernel: [    0.502872] Bluetooth: Core ver 2.13
Jul 11 21:25:06 innov kernel: [    0.502872] NET: Registered protocol family 31
Jul 11 21:25:06 innov kernel: [    0.502872] Bluetooth: HCI device and connection manager initialized
Jul 11 21:25:06 innov kernel: [    0.502872] Bluetooth: HCI socket layer initialized
Jul 11 21:25:06 innov kernel: [    0.502872] NET: Registered protocol family 8
Jul 11 21:25:06 innov kernel: [    0.502872] NET: Registered protocol family 20
Jul 11 21:25:06 innov kernel: [    0.502872] NetLabel: Initializing
Jul 11 21:25:06 innov kernel: [    0.502872] NetLabel:  domain hash size = 128
Jul 11 21:25:06 innov kernel: [    0.502872] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 11 21:25:06 innov kernel: [    0.502872] NetLabel:  unlabeled traffic allowed by default
Jul 11 21:25:06 innov kernel: [    0.502872] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 11 21:25:06 innov kernel: [    0.502872] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 11 21:25:06 innov kernel: [    0.502872] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 11 21:25:06 innov kernel: [    0.508077] AppArmor: AppArmor Filesystem Enabled
Jul 11 21:25:06 innov kernel: [    0.508087] pnp: PnP ACPI init
Jul 11 21:25:06 innov kernel: [    0.508087] ACPI: bus type pnp registered
Jul 11 21:25:06 innov kernel: [    0.512786] pnp: PnP ACPI: found 17 devices
Jul 11 21:25:06 innov kernel: [    0.512789] ACPI: ACPI bus type pnp unregistered
Jul 11 21:25:06 innov kernel: [    0.512794] PnPBIOS: Disabled by ACPI PNP
Jul 11 21:25:06 innov kernel: [    0.512808] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512818] system 00:07: ioport range 0x680-0x6ff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512824] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Jul 11 21:25:06 innov kernel: [    0.512827] system 00:08: ioport range 0x800-0x87f has been reserved
Jul 11 21:25:06 innov kernel: [    0.512830] system 00:08: ioport range 0x480-0x4bf has been reserved
Jul 11 21:25:06 innov kernel: [    0.512833] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512836] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512842] system 00:0a: iomem range 0xffc00000-0xfff7ffff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512848] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512850] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512857] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512862] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
Jul 11 21:25:06 innov kernel: [    0.512869] system 00:10: iomem range 0x0-0x9ffff could not be reserved
Jul 11 21:25:06 innov kernel: [    0.512872] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
Jul 11 21:25:06 innov kernel: [    0.512875] system 00:10: iomem range 0x100000-0x4f7fffff could not be reserved
Jul 11 21:25:06 innov kernel: [    0.547581] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Jul 11 21:25:06 innov kernel: [    0.547586] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
Jul 11 21:25:06 innov kernel: [    0.547592] pci 0000:00:1c.0:   MEM window: disabled
Jul 11 21:25:06 innov kernel: [    0.547596] pci 0000:00:1c.0:   PREFETCH window: disabled
Jul 11 21:25:06 innov kernel: [    0.547603] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Jul 11 21:25:06 innov kernel: [    0.547606] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
Jul 11 21:25:06 innov kernel: [    0.547612] pci 0000:00:1e.0:   MEM window: 0xcff00000-0xcfffffff
Jul 11 21:25:06 innov kernel: [    0.547616] pci 0000:00:1e.0:   PREFETCH window: disabled
Jul 11 21:25:06 innov kernel: [    0.547634] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 21:25:06 innov kernel: [    0.547653] bus: 00 index 0 io port: [0x00-0xffff]
Jul 11 21:25:06 innov kernel: [    0.547655] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Jul 11 21:25:06 innov kernel: [    0.547657] bus: 01 index 0 io port: [0xc000-0xcfff]
Jul 11 21:25:06 innov kernel: [    0.547660] bus: 01 index 1 mmio: [0x0-0x0]
Jul 11 21:25:06 innov kernel: [    0.547663] bus: 01 index 2 mmio: [0x0-0x0]
Jul 11 21:25:06 innov kernel: [    0.547665] bus: 01 index 3 mmio: [0x0-0x0]
Jul 11 21:25:06 innov kernel: [    0.547667] bus: 02 index 0 io port: [0xd000-0xefff]
Jul 11 21:25:06 innov kernel: [    0.547670] bus: 02 index 1 mmio: [0xcff00000-0xcfffffff]
Jul 11 21:25:06 innov kernel: [    0.547672] bus: 02 index 2 mmio: [0x0-0x0]
Jul 11 21:25:06 innov kernel: [    0.547674] bus: 02 index 3 io port: [0x00-0xffff]
Jul 11 21:25:06 innov kernel: [    0.547676] bus: 02 index 4 mmio: [0x000000-0xffffffff]
Jul 11 21:25:06 innov kernel: [    0.547685] NET: Registered protocol family 2
Jul 11 21:25:06 innov kernel: [    0.547824] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 11 21:25:06 innov kernel: [    0.548166] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 11 21:25:06 innov kernel: [    0.548766] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 11 21:25:06 innov kernel: [    0.549209] TCP: Hash tables configured (established 131072 bind 65536)
Jul 11 21:25:06 innov kernel: [    0.549212] TCP reno registered
Jul 11 21:25:06 innov kernel: [    0.549377] NET: Registered protocol family 1
Jul 11 21:25:06 innov kernel: [    0.549526] checking if image is initramfs... it is
Jul 11 21:25:06 innov kernel: [    1.128379] Freeing initrd memory: 7375k freed
Jul 11 21:25:06 innov kernel: [    1.128494] cpufreq: No nForce2 chipset.
Jul 11 21:25:06 innov kernel: [    1.128647] audit: initializing netlink socket (disabled)
Jul 11 21:25:06 innov kernel: [    1.128666] type=2000 audit(1247347495.128:1): initialized
Jul 11 21:25:06 innov kernel: [    1.136515] highmem bounce pool size: 64 pages
Jul 11 21:25:06 innov kernel: [    1.136522] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 11 21:25:06 innov kernel: [    1.137773] VFS: Disk quotas dquot_6.5.1
Jul 11 21:25:06 innov kernel: [    1.137833] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 11 21:25:06 innov kernel: [    1.138481] fuse init (API version 7.10)
Jul 11 21:25:06 innov kernel: [    1.138569] msgmni has been set to 1718
Jul 11 21:25:06 innov kernel: [    1.138755] alg: No test for stdrng (krng)
Jul 11 21:25:06 innov kernel: [    1.138771] io scheduler noop registered
Jul 11 21:25:06 innov kernel: [    1.138774] io scheduler anticipatory registered
Jul 11 21:25:06 innov kernel: [    1.138776] io scheduler deadline registered
Jul 11 21:25:06 innov kernel: [    1.138792] io scheduler cfq registered (default)
Jul 11 21:25:06 innov kernel: [    1.142661] pcieport-driver 0000:00:1c.0: found MSI capability
Jul 11 21:25:06 innov kernel: [    1.142816] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 11 21:25:06 innov kernel: [    1.142993] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 11 21:25:06 innov kernel: [    1.143135] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jul 11 21:25:06 innov kernel: [    1.143139] ACPI: Power Button (FF) [PWRF]
Jul 11 21:25:06 innov kernel: [    1.143196] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jul 11 21:25:06 innov kernel: [    1.143199] ACPI: Power Button (CM) [PWRB]
Jul 11 21:25:06 innov kernel: [    1.143608] processor ACPI_CPU:00: registered as cooling_device0
Jul 11 21:25:06 innov kernel: [    1.143612] ACPI: Processor [CPU1] (supports 8 throttling states)
Jul 11 21:25:06 innov kernel: [    1.145998] isapnp: Scanning for PnP cards...
Jul 11 21:25:06 innov kernel: [    1.497637] isapnp: No Plug & Play device found
Jul 11 21:25:06 innov kernel: [    1.499040] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jul 11 21:25:06 innov kernel: [    1.500250] brd: module loaded
Jul 11 21:25:06 innov kernel: [    1.500610] loop: module loaded
Jul 11 21:25:06 innov kernel: [    1.500701] Fixed MDIO Bus: probed
Jul 11 21:25:06 innov kernel: [    1.500707] PPP generic driver version 2.4.2
Jul 11 21:25:06 innov kernel: [    1.500772] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 11 21:25:06 innov kernel: [    1.500805] Driver 'sd' needs updating - please use bus_type methods
Jul 11 21:25:06 innov kernel: [    1.500816] Driver 'sr' needs updating - please use bus_type methods
Jul 11 21:25:06 innov kernel: [    1.500909] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 21:25:06 innov kernel: [    1.501059] scsi0 : ata_piix
Jul 11 21:25:06 innov kernel: [    1.501159] scsi1 : ata_piix
Jul 11 21:25:06 innov kernel: [    1.502930] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jul 11 21:25:06 innov kernel: [    1.502934] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jul 11 21:25:06 innov kernel: [    1.680357] ata1.00: ATAPI: LITE-ON COMBO SOHC-4836K, SPK1, max UDMA/33
Jul 11 21:25:06 innov kernel: [    1.712306] ata1.00: configured for UDMA/33
Jul 11 21:25:06 innov kernel: [    1.714235] scsi 0:0:0:0: CD-ROM            LITE-ON  COMBO SOHC-4836K SPK1 PQ: 0 ANSI: 5
Jul 11 21:25:06 innov kernel: [    1.720084] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
Jul 11 21:25:06 innov kernel: [    1.720088] Uniform CD-ROM driver Revision: 3.20
Jul 11 21:25:06 innov kernel: [    1.720249] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jul 11 21:25:06 innov kernel: [    1.720274] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 11 21:25:06 innov kernel: [    1.720279] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jul 11 21:25:06 innov kernel: [    1.720387] scsi2 : ata_piix
Jul 11 21:25:06 innov kernel: [    1.720450] scsi3 : ata_piix
Jul 11 21:25:06 innov kernel: [    1.720494] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x8800 irq 19
Jul 11 21:25:06 innov kernel: [    1.720497] ata4: SATA max UDMA/133 cmd 0x9400 ctl 0x9000 bmdma 0x8808 irq 19
Jul 11 21:25:06 innov kernel: [    1.884219] ata3.00: ATA-7: WDC WD800JD-60LUA0, 07.01D07, max UDMA/100
Jul 11 21:25:06 innov kernel: [    1.884222] ata3.00: 156301488 sectors, multi 16: LBA48 
Jul 11 21:25:06 innov kernel: [    1.892247] ata3.00: configured for UDMA/100
Jul 11 21:25:06 innov kernel: [    2.058241] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800JD-60LU 07.0 PQ: 0 ANSI: 5
Jul 11 21:25:06 innov kernel: [    2.058348] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
Jul 11 21:25:06 innov kernel: [    2.058368] sd 2:0:0:0: [sda] Write Protect is off
Jul 11 21:25:06 innov kernel: [    2.058403] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 11 21:25:06 innov kernel: [    2.058468] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
Jul 11 21:25:06 innov kernel: [    2.058486] sd 2:0:0:0: [sda] Write Protect is off
Jul 11 21:25:06 innov kernel: [    2.058519] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 11 21:25:06 innov kernel: [    2.058523]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Jul 11 21:25:06 innov kernel: [    2.121601] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 11 21:25:06 innov kernel: [    2.121649] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jul 11 21:25:06 innov kernel: [    2.122270] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 11 21:25:06 innov kernel: [    2.122297] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul 11 21:25:06 innov kernel: [    2.122325] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 11 21:25:06 innov kernel: [    2.122398] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 11 21:25:06 innov kernel: [    2.126318] ehci_hcd 0000:00:1d.7: debug port 1
Jul 11 21:25:06 innov kernel: [    2.126342] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xcfe37c00
Jul 11 21:25:06 innov kernel: [    2.140012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 11 21:25:06 innov kernel: [    2.140094] usb usb1: configuration #1 chosen from 1 choice
Jul 11 21:25:06 innov kernel: [    2.140127] hub 1-0:1.0: USB hub found
Jul 11 21:25:06 innov kernel: [    2.140137] hub 1-0:1.0: 8 ports detected
Jul 11 21:25:06 innov kernel: [    2.140259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 11 21:25:06 innov kernel: [    2.140275] uhci_hcd: USB Universal Host Controller Interface driver
Jul 11 21:25:06 innov kernel: [    2.140309] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul 11 21:25:06 innov kernel: [    2.140319] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 11 21:25:06 innov kernel: [    2.140366] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 11 21:25:06 innov kernel: [    2.140389] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a400
Jul 11 21:25:06 innov kernel: [    2.140474] usb usb2: configuration #1 chosen from 1 choice
Jul 11 21:25:06 innov kernel: [    2.140503] hub 2-0:1.0: USB hub found
Jul 11 21:25:06 innov kernel: [    2.140512] hub 2-0:1.0: 2 ports detected
Jul 11 21:25:06 innov kernel: [    2.140608] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 11 21:25:06 innov kernel: [    2.140618] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 11 21:25:06 innov kernel: [    2.140663] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 11 21:25:06 innov kernel: [    2.140687] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a800
Jul 11 21:25:06 innov kernel: [    2.140763] usb usb3: configuration #1 chosen from 1 choice
Jul 11 21:25:06 innov kernel: [    2.140792] hub 3-0:1.0: USB hub found
Jul 11 21:25:06 innov kernel: [    2.140800] hub 3-0:1.0: 2 ports detected
Jul 11 21:25:06 innov kernel: [    2.140889] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 11 21:25:06 innov kernel: [    2.140899] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 11 21:25:06 innov kernel: [    2.140946] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 11 21:25:06 innov kernel: [    2.140979] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b000
Jul 11 21:25:06 innov kernel: [    2.141060] usb usb4: configuration #1 chosen from 1 choice
Jul 11 21:25:06 innov kernel: [    2.141088] hub 4-0:1.0: USB hub found
Jul 11 21:25:06 innov kernel: [    2.141096] hub 4-0:1.0: 2 ports detected
Jul 11 21:25:06 innov kernel: [    2.141183] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Jul 11 21:25:06 innov kernel: [    2.141193] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 11 21:25:06 innov kernel: [    2.141247] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 11 21:25:06 innov kernel: [    2.141277] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b400
Jul 11 21:25:06 innov kernel: [    2.141352] usb usb5: configuration #1 chosen from 1 choice
Jul 11 21:25:06 innov kernel: [    2.141380] hub 5-0:1.0: USB hub found
Jul 11 21:25:06 innov kernel: [    2.141388] hub 5-0:1.0: 2 ports detected
Jul 11 21:25:06 innov kernel: [    2.141542] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jul 11 21:25:06 innov kernel: [    2.144233] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 11 21:25:06 innov kernel: [    2.144239] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 11 21:25:06 innov kernel: [    2.144360] mice: PS/2 mouse device common for all mice
Jul 11 21:25:06 innov kernel: [    2.144501] rtc_cmos 00:03: RTC can wake from S4
Jul 11 21:25:06 innov kernel: [    2.144546] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 11 21:25:06 innov kernel: [    2.144572] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Jul 11 21:25:06 innov kernel: [    2.144646] device-mapper: uevent: version 1.0.3
Jul 11 21:25:06 innov kernel: [    2.144757] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Jul 11 21:25:06 innov kernel: [    2.144807] device-mapper: multipath: version 1.0.5 loaded
Jul 11 21:25:06 innov kernel: [    2.144810] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 11 21:25:06 innov kernel: [    2.144890] EISA: Probing bus 0 at eisa.0
Jul 11 21:25:06 innov kernel: [    2.144918] Cannot allocate resource for EISA slot 8
Jul 11 21:25:06 innov kernel: [    2.144920] EISA: Detected 0 cards.
Jul 11 21:25:06 innov kernel: [    2.144949] cpuidle: using governor ladder
Jul 11 21:25:06 innov kernel: [    2.144952] cpuidle: using governor menu
Jul 11 21:25:06 innov kernel: [    2.145555] TCP cubic registered
Jul 11 21:25:06 innov kernel: [    2.145633] NET: Registered protocol family 10
Jul 11 21:25:06 innov kernel: [    2.146105] lo: Disabled Privacy Extensions
Jul 11 21:25:06 innov kernel: [    2.146471] NET: Registered protocol family 17
Jul 11 21:25:06 innov kernel: [    2.146492] Bluetooth: L2CAP ver 2.11
Jul 11 21:25:06 innov kernel: [    2.146495] Bluetooth: L2CAP socket layer initialized
Jul 11 21:25:06 innov kernel: [    2.146497] Bluetooth: SCO (Voice Link) ver 0.6
Jul 11 21:25:06 innov kernel: [    2.146499] Bluetooth: SCO socket layer initialized
Jul 11 21:25:06 innov kernel: [    2.146525] Bluetooth: RFCOMM socket layer initialized
Jul 11 21:25:06 innov kernel: [    2.146533] Bluetooth: RFCOMM TTY layer initialized
Jul 11 21:25:06 innov kernel: [    2.146535] Bluetooth: RFCOMM ver 1.10
Jul 11 21:25:06 innov kernel: [    2.146580] Using IPI No-Shortcut mode
Jul 11 21:25:06 innov kernel: [    2.146662] registered taskstats version 1
Jul 11 21:25:06 innov kernel: [    2.146776]   Magic number: 1:435:449
Jul 11 21:25:06 innov kernel: [    2.146862] rtc_cmos 00:03: setting system clock to 2009-07-11 21:24:56 UTC (1247347496)
Jul 11 21:25:06 innov kernel: [    2.146865] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 11 21:25:06 innov kernel: [    2.146867] EDD information not available.
Jul 11 21:25:06 innov kernel: [    2.147312] Freeing unused kernel memory: 532k freed
Jul 11 21:25:06 innov kernel: [    2.147423] Write protecting the kernel text: 4112k
Jul 11 21:25:06 innov kernel: [    2.147462] Write protecting the kernel read-only data: 1524k
Jul 11 21:25:06 innov kernel: [    2.184214] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 11 21:25:06 innov kernel: [    2.689904] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 11 21:25:06 innov kernel: [    2.689939] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Jul 11 21:25:06 innov kernel: [    2.692809] 8139too Fast Ethernet driver 0.9.28
Jul 11 21:25:06 innov kernel: [    2.692852] 8139too 0000:02:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jul 11 21:25:06 innov kernel: [    2.694050] eth0: RealTek RTL8139 at 0xe400, 00:13:d4:86:54:21, IRQ 21
Jul 11 21:25:06 innov kernel: [    2.697273] ohci1394 0000:02:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul 11 21:25:06 innov kernel: [    2.750065] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[cffff800-cfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jul 11 21:25:06 innov kernel: [    2.900942] usb 5-1: new full speed USB device using uhci_hcd and address 2
Jul 11 21:25:06 innov kernel: [    3.077505] usb 5-1: configuration #1 chosen from 1 choice
Jul 11 21:25:06 innov kernel: [    3.091549] Initializing USB Mass Storage driver...
Jul 11 21:25:06 innov kernel: [    3.093413] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 11 21:25:06 innov kernel: [    3.093660] usbcore: registered new interface driver usb-storage
Jul 11 21:25:06 innov kernel: [    3.093665] USB Mass Storage support registered.
Jul 11 21:25:06 innov kernel: [    3.515975] PM: Starting manual resume from disk
Jul 11 21:25:06 innov kernel: [    3.542866] kjournald starting.  Commit interval 5 seconds
Jul 11 21:25:06 innov kernel: [    3.542878] EXT3-fs: mounted filesystem with ordered data mode.
Jul 11 21:25:06 innov kernel: [    8.098084] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Jul 11 21:25:06 innov kernel: [    8.101256] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Jul 11 21:25:06 innov kernel: [    8.104265] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Jul 11 21:25:06 innov kernel: [    8.106479] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Jul 11 21:25:06 innov kernel: [    8.112075] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 11 21:25:06 innov kernel: [    8.112151] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jul 11 21:25:06 innov kernel: [    8.116573] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jul 11 21:25:06 innov kernel: [    8.116644] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jul 11 21:25:06 innov kernel: [    8.121534] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jul 11 21:25:06 innov kernel: [    8.121585] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jul 11 21:25:06 innov kernel: [    8.126521] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jul 11 21:25:06 innov kernel: [    8.126577] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jul 11 21:25:06 innov kernel: [    8.261213] udev: starting version 141
Jul 11 21:25:06 innov kernel: [    8.452377] parport_pc 00:06: reported by Plug and Play ACPI
Jul 11 21:25:06 innov kernel: [    8.452434] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 11 21:25:06 innov kernel: [    8.759135] Linux agpgart interface v0.103
Jul 11 21:25:06 innov kernel: [    8.768434] intel_rng: FWH not detected
Jul 11 21:25:06 innov kernel: [    8.796938] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jul 11 21:25:06 innov kernel: [    8.813782] agpgart-intel 0000:00:00.0: Intel 915G Chipset
Jul 11 21:25:06 innov kernel: [    8.814050] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Jul 11 21:25:06 innov kernel: [    8.817612] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jul 11 21:25:06 innov kernel: [    8.869709] iTCO_vendor_support: vendor-support=0
Jul 11 21:25:06 innov kernel: [    8.871506] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Jul 11 21:25:06 innov kernel: [    8.871688] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
Jul 11 21:25:06 innov kernel: [    8.871783] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jul 11 21:25:06 innov kernel: [    8.947184] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Jul 11 21:25:06 innov kernel: [    9.042686] ppdev: user-space parallel port driver
Jul 11 21:25:06 innov kernel: [    9.144462] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 21:25:06 innov kernel: [    9.726761] Adding 771080k swap on /dev/sda6.  Priority:-1 extents:1 across:771080k
Jul 11 21:25:06 innov kernel: [   10.021011] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 11 21:25:06 innov kernel: [   10.277843] EXT3 FS on sda5, internal journal
Jul 11 21:25:06 innov kernel: [   11.275184] type=1505 audit(1247327705.625:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2009
Jul 11 21:25:06 innov kernel: [   11.325607] type=1505 audit(1247327705.677:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2013
Jul 11 21:25:06 innov kernel: [   11.325757] type=1505 audit(1247327705.677:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2013
Jul 11 21:25:06 innov kernel: [   11.325808] type=1505 audit(1247327705.677:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2013
Jul 11 21:25:06 innov kernel: [   11.325849] type=1505 audit(1247327705.677:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2013
Jul 11 21:25:06 innov kernel: [   11.466757] type=1505 audit(1247327705.817:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2018
Jul 11 21:25:06 innov kernel: [   11.466994] type=1505 audit(1247327705.817:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2018
Jul 11 21:25:06 innov kernel: [   11.497566] type=1505 audit(1247327705.849:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2022
Jul 11 21:25:07 innov kernel: [   13.561005] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 11 21:25:07 innov kernel: [   13.561009] Bluetooth: BNEP filters: protocol multicast
Jul 11 21:25:07 innov kernel: [   13.588363] Bridge firewalling registered
Jul 11 21:25:09 innov kernel: [   15.285228] [drm] Initialized drm 1.1.0 20060810
Jul 11 21:25:09 innov kernel: [   15.299370] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 21:25:09 innov kernel: [   15.299586] [drm] Initialized i915 1.6.0 20080730 on minor 0
Jul 11 21:25:13 innov kernel: [   18.649074] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```Since you know the exact time when the crash happened , it should not be tiring to rectify the error . 

My advance thanks for your help .  :p

---

### Post by rsiddharth on 2009-07-12
The system crashed again on 12th July 2009 at 12:18pm . This time I didn't abruptly type the REISUB magic to restart my comp but waited to observe what happened externally - The hardrive was apparently switched off since the hard drive light didn't blink at all  , I tried connecting to the Internet and it got connected ! , I tried  mounting my USB stick ( pen drive ) it got mounted ( If the USB stick gets mounted the light on the stick stops blinking and it indeed stopped blinking when inserted the stick after the crash . ) , my observation of the keyboard-  I tried toggling the Capslock key , while I toggled the light for the Capslock key didn't on/off . The mouse - I was able to only move the pointer with my mouse but could do nothing other than that and my desktop screen looked like a wallpaper with pointer that could be only be moved and do nothing other than that . 

I working with Firefox offline , cruising through the Page info dialog when the crash happened .  

Here is the Log again , this time I have sliced out snippets the logs from different sections of the Log File viewer .   

```

Taken from syslog
Jul 12 12:17:01 innov /USR/SBIN/CRON[17025]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 11 12:17:01 innov /USR/SBIN/CRON[5103]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 11 21:20:01 innov /USR/SBIN/CRON[9146]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

------------------------
Taken from auth.log

Jul 12 12:23:04 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.178" (uid=0 pid=17357 comm="/usr/lib/NetworkManager/nm-dispatcher.action "))


Jul 12 12:23:04 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.178" (uid=0 pid=17357 comm="/usr/lib/NetworkManager/nm-dispatcher.action "))


Jul 12 12:23:31 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.179" (uid=0 pid=17407 comm="/usr/lib/hal/hald-addon-storage "))


Jul 12 12:23:31 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.179" (uid=0 pid=17407 comm="/usr/lib/hal/hald-addon-storage "))


Jul 12 12:30:25 innov dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.13" (uid=0 pid=2626 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.11" (uid=0 pid=2623 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))


Jul 12 12:30:44 innov gdm[2597]: pam_unix(gdm:session): session opened for user siddharth by (uid=0)
----------------------------------------------------------------

```


Thank you for your help .

---

### Post by meditatingfrog on 2009-08-02
> **rsiddharth said:**
> The system crashed again on 12th July 2009 at 12:18pm . This time I didn't abruptly type the REISUB magic to restart my comp but waited to observe what happened externally - The hardrive was apparently switched off since the hard drive light didn't blink at all  , I tried connecting to the Internet and it got connected ! , I tried  mounting my USB stick ( pen drive ) it got mounted ( If the USB stick gets mounted the light on the stick stops blinking and it indeed stopped blinking when inserted the stick after the crash . ) , my observation of the keyboard-  I tried toggling the Capslock key , while I toggled the light for the Capslock key didn't on/off . The mouse - I was able to only move the pointer with my mouse but could do nothing other than that and my desktop screen looked like a wallpaper with pointer that could be only be moved and do nothing other than that . 

I working with Firefox offline , cruising through the Page info dialog when the crash happened .  

Here is the Log again , this time I have sliced out snippets the logs from different sections of the Log File viewer .   

```

Taken from syslog
Jul 12 12:17:01 innov /USR/SBIN/CRON[17025]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 11 12:17:01 innov /USR/SBIN/CRON[5103]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 11 21:20:01 innov /USR/SBIN/CRON[9146]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

------------------------
Taken from auth.log

Jul 12 12:23:04 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.178" (uid=0 pid=17357 comm="/usr/lib/NetworkManager/nm-dispatcher.action "))


Jul 12 12:23:04 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.178" (uid=0 pid=17357 comm="/usr/lib/NetworkManager/nm-dispatcher.action "))


Jul 12 12:23:31 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.179" (uid=0 pid=17407 comm="/usr/lib/hal/hald-addon-storage "))


Jul 12 12:23:31 innov dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3375 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.179" (uid=0 pid=17407 comm="/usr/lib/hal/hald-addon-storage "))


Jul 12 12:30:25 innov dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.13" (uid=0 pid=2626 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.11" (uid=0 pid=2623 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))


Jul 12 12:30:44 innov gdm[2597]: pam_unix(gdm:session): session opened for user siddharth by (uid=0)
----------------------------------------------------------------

```


Thank you for your help .

Hello rsiddhart:

I have the same error when I do dmesg | grep failure, but, I haven't found the failure message in my syslog.  I think it used to be there, but I suspended and resumed and the error was no longer in my syslog.

Perhaps you could do an lspci in the command line so that we know what hardware you have.  I have a Toshiba laptop that has built-in Intel graphics (G965/G960).  Maybe you have the same video adapter.  Is your system a desktop or a laptop?

Have you tried hibernating instead of suspending?  It takes a little bit longer to start up after a hibernate, but try it for a couple days and see if you still have the freeze problem.  If you don't, then it might be that your freezing is caused by the suspend/sleep.  I've had a freeze problem with suspend/sleep myself, and I'm not sure if I resolved the problem yet.  The Intel driver that comes with Jaunty doesn't work so well with Jaunty (used to work okay with Ibex).  I can't even enable desktop effects now, but I did recently follow an article online to hopefully get updated Intel drivers faster (assuming you have an Intel graphics chip):  [http://www.google.com/reader/view/#search/upd8%20intel/5](http://www.google.com/reader/view/#search/upd8%20intel/5)

---

### Post by rsiddharth on 2009-08-03
> **meditatingfrog said:**
> Hello rsiddhart:

I have the same error when I do dmesg | grep failure, but, I haven't found the failure message in my syslog.  I think it used to be there, but I suspended and resumed and the error was no longer in my syslog.

Perhaps you could do an lspci in the command line so that we know what hardware you have.  I have a Toshiba laptop that has built-in Intel graphics (G965/G960).  Maybe you have the same video adapter.  Is your system a desktop or a laptop?
I tried the lscpi command as you told and I get this following output . 

```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

02:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

```I use a desktop computer . 

Here are my System Specs in short  :
 Intel Pentium 4 processor 512K 3.06 GHz , 1 MB L2 Cache 
  1 GB DDR RAM  400Mhz 
Integrated Intel GMA 900 Graphics 
CD-RW/DVD Combo Drive.

> 
Have you tried hibernating instead of suspending? It takes a little bit longer to start up after a hibernate, but try it for a couple days and see if you still have the freeze problem. If you don't, then it might be that your freezing is caused by the suspend/sleep. I've had a freeze problem with suspend/sleep myself, and I'm not sure if I resolved the problem yet. The Intel driver that comes with Jaunty doesn't work so well with Jaunty (used to work okay with Ibex). I can't even enable desktop effects now, but I did recently follow an article online to hopefully get updated Intel drivers faster (assuming you have an Intel graphics chip): [http://www.google.com/reader/view/#search/upd8%20intel/5](http://www.google.com/reader/view/#search/upd8%20intel/5)Yeah , suspending was and is a problem in my comp , sometimes when I come out of suspend mode ,instead of resuming , the computer shuts down ! . 

Do you mean to say that I try hibernating my comp instead of shutting it down ?? . I will try doing that and see what happens from there . 

Though I have only a Integrated Intel GMA 900 Graphics in the Desktop that runs ubuntu , Visual Effects seems to work for me.  

I will also see if I can find anything useful from the link that you have provided .

Thank you ! :D meditatingfrog

---

### Post by trimmer on 2010-01-26
Has there been any attention from UBUNTU or Canonical at all on this thread or this error? My log file is laden with these erors, specifically:

[HTML]Jan 25 15:44:58 iforthen kernel: [60319.236131] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 15:44:58 iforthen kernel: [60319.236142] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 15:44:58 iforthen kernel: [60319.236174] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 15:47:39 iforthen kernel: [60480.680048] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:47:39 iforthen kernel: [60480.680054] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:47:39 iforthen kernel: [60480.680058] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:47:39 iforthen kernel: [60480.680064]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:47:39 iforthen kernel: [60480.680072]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:47:39 iforthen kernel: [60480.680080]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:47:39 iforthen kernel: [60480.680087] Call Trace:
Jan 25 15:47:39 iforthen kernel: [60480.680100]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:47:39 iforthen kernel: [60480.680107]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:47:39 iforthen kernel: [60480.680111]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:47:39 iforthen kernel: [60480.680115]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:47:39 iforthen kernel: [60480.680119]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:47:39 iforthen kernel: [60480.680123]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:47:39 iforthen kernel: [60480.680127]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:47:39 iforthen kernel: [60480.680131]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:47:39 iforthen kernel: [60480.680136]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:47:39 iforthen kernel: [60480.680140]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:47:39 iforthen kernel: [60480.680145]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:47:39 iforthen kernel: [60480.680149]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:47:39 iforthen kernel: [60480.680153]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:49:39 iforthen kernel: [60600.680047] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:49:39 iforthen kernel: [60600.680052] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:49:39 iforthen kernel: [60600.680056] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:49:39 iforthen kernel: [60600.680062]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:49:39 iforthen kernel: [60600.680071]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:49:39 iforthen kernel: [60600.680078]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:49:39 iforthen kernel: [60600.680086] Call Trace:
Jan 25 15:49:39 iforthen kernel: [60600.680097]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:49:39 iforthen kernel: [60600.680104]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:49:39 iforthen kernel: [60600.680108]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:49:39 iforthen kernel: [60600.680112]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:49:39 iforthen kernel: [60600.680116]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:49:39 iforthen kernel: [60600.680121]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:49:39 iforthen kernel: [60600.680125]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:49:39 iforthen kernel: [60600.680129]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:49:39 iforthen kernel: [60600.680134]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:49:39 iforthen kernel: [60600.680138]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:49:39 iforthen kernel: [60600.680143]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:49:39 iforthen kernel: [60600.680148]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:49:39 iforthen kernel: [60600.680152]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:51:39 iforthen kernel: [60720.680051] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:51:41 iforthen kernel: [60720.680056] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:51:41 iforthen kernel: [60720.680060] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:51:41 iforthen kernel: [60720.680067]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:51:41 iforthen kernel: [60720.680075]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:51:41 iforthen kernel: [60720.680082]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:51:41 iforthen kernel: [60720.680090] Call Trace:
Jan 25 15:51:41 iforthen kernel: [60720.680102]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:51:41 iforthen kernel: [60720.680108]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:51:41 iforthen kernel: [60720.680112]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:51:41 iforthen kernel: [60720.680116]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:51:41 iforthen kernel: [60720.680120]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:51:41 iforthen kernel: [60720.680125]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:51:41 iforthen kernel: [60720.680129]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:51:41 iforthen kernel: [60720.680133]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:51:41 iforthen kernel: [60720.680138]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:51:41 iforthen kernel: [60720.680142]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:51:41 iforthen kernel: [60720.680147]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:51:41 iforthen kernel: [60720.680151]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:51:41 iforthen kernel: [60720.680155]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:53:39 iforthen kernel: [60840.680050] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:53:41 iforthen kernel: [60840.680055] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:53:41 iforthen kernel: [60840.680059] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:53:41 iforthen kernel: [60840.680066]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:53:41 iforthen kernel: [60840.680074]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:53:41 iforthen kernel: [60840.680081]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:53:41 iforthen kernel: [60840.680087] Call Trace:
Jan 25 15:53:42 iforthen kernel: [60840.680099]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:53:42 iforthen kernel: [60840.680105]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:53:42 iforthen kernel: [60840.680109]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:53:42 iforthen kernel: [60840.680112]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:53:42 iforthen kernel: [60840.680116]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:53:42 iforthen kernel: [60840.680121]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:53:42 iforthen kernel: [60840.680125]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:53:42 iforthen kernel: [60840.680128]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:53:42 iforthen kernel: [60840.680133]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:53:42 iforthen kernel: [60840.680137]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:53:42 iforthen kernel: [60840.680141]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:53:42 iforthen kernel: [60840.680145]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:53:42 iforthen kernel: [60840.680149]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:55:39 iforthen kernel: [60960.680047] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:55:39 iforthen kernel: [60960.680053] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:55:39 iforthen kernel: [60960.680056] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:55:39 iforthen kernel: [60960.680063]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:55:39 iforthen kernel: [60960.680071]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:55:39 iforthen kernel: [60960.680078]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:55:39 iforthen kernel: [60960.680085] Call Trace:
Jan 25 15:55:39 iforthen kernel: [60960.680097]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:55:39 iforthen kernel: [60960.680103]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:55:39 iforthen kernel: [60960.680108]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:55:39 iforthen kernel: [60960.680112]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:55:39 iforthen kernel: [60960.680116]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:55:39 iforthen kernel: [60960.680121]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:55:39 iforthen kernel: [60960.680125]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:55:39 iforthen kernel: [60960.680129]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:55:39 iforthen kernel: [60960.680134]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:55:39 iforthen kernel: [60960.680138]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:55:39 iforthen kernel: [60960.680143]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:55:39 iforthen kernel: [60960.680148]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:55:39 iforthen kernel: [60960.680152]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:57:39 iforthen kernel: [61080.680050] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:57:43 iforthen kernel: [61080.680056] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:57:43 iforthen kernel: [61080.680060] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:57:43 iforthen kernel: [61080.680066]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:57:43 iforthen kernel: [61080.680075]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:57:43 iforthen kernel: [61080.680082]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:57:43 iforthen kernel: [61080.680090] Call Trace:
Jan 25 15:57:43 iforthen kernel: [61080.680102]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:57:43 iforthen kernel: [61080.680108]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:57:43 iforthen kernel: [61080.680112]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:57:43 iforthen kernel: [61080.680116]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:57:43 iforthen kernel: [61080.680120]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:57:43 iforthen kernel: [61080.680125]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:57:43 iforthen kernel: [61080.680130]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:57:43 iforthen kernel: [61080.680134]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:57:43 iforthen kernel: [61080.680138]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:57:43 iforthen kernel: [61080.680143]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:57:43 iforthen kernel: [61080.680148]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:57:43 iforthen kernel: [61080.680153]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:57:43 iforthen kernel: [61080.680157]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:59:39 iforthen kernel: [61200.680046] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:59:42 iforthen kernel: [61200.680051] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:59:42 iforthen kernel: [61200.680055] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:59:42 iforthen kernel: [61200.680061]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:59:42 iforthen kernel: [61200.680069]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:59:42 iforthen kernel: [61200.680077]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:59:42 iforthen kernel: [61200.680084] Call Trace:
Jan 25 15:59:42 iforthen kernel: [61200.680096]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:59:42 iforthen kernel: [61200.680102]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:59:42 iforthen kernel: [61200.680106]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:59:42 iforthen kernel: [61200.680110]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:59:42 iforthen kernel: [61200.680114]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:59:42 iforthen kernel: [61200.680120]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:59:42 iforthen kernel: [61200.680124]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:59:42 iforthen kernel: [61200.680128]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:59:42 iforthen kernel: [61200.680133]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:59:42 iforthen kernel: [61200.680137]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:59:42 iforthen kernel: [61200.680142]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:59:42 iforthen kernel: [61200.680146]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:59:42 iforthen kernel: [61200.680150]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:03:39 iforthen kernel: [61440.680056] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 16:03:40 iforthen kernel: [61440.680062] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 16:03:40 iforthen kernel: [61440.680066] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 16:03:40 iforthen kernel: [61440.680072]  d1dc5e3c 00000086 01412b9a c08145c0 d352e718 c08145c0 ccb49bc9 000037bc
Jan 25 16:03:40 iforthen kernel: [61440.680080]  c08145c0 c08145c0 d352e718 c08145c0 ccb38c52 000037bc c08145c0 dd71dc00
Jan 25 16:03:40 iforthen kernel: [61440.680088]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 16:03:40 iforthen kernel: [61440.680096] Call Trace:
Jan 25 16:03:40 iforthen kernel: [61440.680107]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 16:03:40 iforthen kernel: [61440.680114]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680118]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 16:03:40 iforthen kernel: [61440.680122]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680126]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 16:03:40 iforthen kernel: [61440.680131]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 16:03:40 iforthen kernel: [61440.680135]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 16:03:40 iforthen kernel: [61440.680139]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 16:03:40 iforthen kernel: [61440.680143]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 16:03:40 iforthen kernel: [61440.680148]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680153]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680157]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680161]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:03:40 iforthen kernel: [61440.680169] INFO: task tracker-indexer:1947 blocked for more than 120 seconds.
Jan 25 16:03:40 iforthen kernel: [61440.680171] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 16:03:40 iforthen kernel: [61440.680174] tracker-index D c08145c0     0  1947      1 0x00000000
Jan 25 16:03:40 iforthen kernel: [61440.680178]  d3485e3c 00000086 00a8501b c08145c0 dcf74168 c08145c0 129c65e1 000037b7
Jan 25 16:03:40 iforthen kernel: [61440.680185]  c08145c0 c08145c0 dcf74168 c08145c0 129b8ca5 000037b7 c08145c0 d3773800
Jan 25 16:03:40 iforthen kernel: [61440.680192]  dcf73ed0 c13fa5c0 00000002 d3485e84 d3485e48 c056f1ce d3485e7c d3485e50
Jan 25 16:03:40 iforthen kernel: [61440.680199] Call Trace:
Jan 25 16:03:40 iforthen kernel: [61440.680203]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 16:03:40 iforthen kernel: [61440.680207]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680210]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 16:03:40 iforthen kernel: [61440.680214]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680218]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 16:03:40 iforthen kernel: [61440.680222]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 16:03:40 iforthen kernel: [61440.680231]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 16:03:40 iforthen kernel: [61440.680235]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 16:03:40 iforthen kernel: [61440.680241]  [<c03b27c8>] ? scsi_finish_command+0x98/0x100
Jan 25 16:03:40 iforthen kernel: [61440.680246]  [<c03de105>] ? ata_sff_altstatus+0x25/0x30
Jan 25 16:03:40 iforthen kernel: [61440.680249]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 16:03:40 iforthen kernel: [61440.680254]  [<c013b47d>] ? update_curr+0x21d/0x230
Jan 25 16:03:40 iforthen kernel: [61440.680258]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680262]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680266]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680270]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:05:39 iforthen kernel: [61560.680045] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 16:05:39 iforthen kernel: [61560.680051] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 16:05:39 iforthen kernel: [61560.680054] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 16:05:39 iforthen kernel: [61560.680060]  d1dc5e3c 00000086 01412b9a c08145c0 d352e718 c08145c0 ccb49bc9 000037bc
Jan 25 16:05:39 iforthen kernel: [61560.680069]  c08145c0 c08145c0 d352e718 c08145c0 ccb38c52 000037bc c08145c0 dd71dc00
Jan 25 16:05:39 iforthen kernel: [61560.680076]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 16:05:39 iforthen kernel: [61560.680083] Call Trace:
Jan 25 16:05:39 iforthen kernel: [61560.680095]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 16:05:39 iforthen kernel: [61560.680101]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 16:05:39 iforthen kernel: [61560.680105]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 16:05:39 iforthen kernel: [61560.680109]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 16:05:39 iforthen kernel: [61560.680113]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 16:05:39 iforthen kernel: [61560.680118]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 16:05:39 iforthen kernel: [61560.680122]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 16:05:39 iforthen kernel: [61560.680126]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 16:05:39 iforthen kernel: [61560.680131]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 16:05:39 iforthen kernel: [61560.680135]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 16:05:39 iforthen kernel: [61560.680140]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 16:05:39 iforthen kernel: [61560.680145]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 16:05:39 iforthen kernel: [61560.680149]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:42:10 iforthen kernel: [63752.200112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 16:42:11 iforthen kernel: [63752.200124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 16:42:11 iforthen kernel: [63752.200156] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 16:43:05 iforthen kernel: [63806.616108] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 16:43:05 iforthen kernel: [63806.616119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 16:43:05 iforthen kernel: [63806.616151] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 17:53:49 iforthen kernel: [68050.797791] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 17:53:49 iforthen kernel: [68050.797798] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 17:53:49 iforthen kernel: [68050.797804] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
Jan 25 17:53:49 iforthen kernel: [68050.797811] end_request: I/O error, dev sr0, sector 0
Jan 25 17:53:49 iforthen kernel: [68050.797816] __ratelimit: 9 callbacks suppressed
Jan 25 17:53:49 iforthen kernel: [68050.797819] Buffer I/O error on device sr0, logical block 0
Jan 25 17:53:49 iforthen kernel: [68050.800466] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 17:53:49 iforthen kernel: [68050.800470] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 17:53:49 iforthen kernel: [68050.800475] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
Jan 25 17:53:49 iforthen kernel: [68050.800480] end_request: I/O error, dev sr0, sector 0
Jan 25 17:53:49 iforthen kernel: [68050.800484] Buffer I/O error on device sr0, logical block 0
Jan 25 17:53:49 iforthen kernel: [68051.222846] cdrom: This disc doesn't have any tracks I recognize!
Jan 25 17:54:03 iforthen kernel: [68065.164138] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 17:54:03 iforthen kernel: [68065.164149] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 17:54:03 iforthen kernel: [68065.164180] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 17:54:52 iforthen kernel: [68113.648110] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 17:54:52 iforthen kernel: [68113.648122] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 17:54:52 iforthen kernel: [68113.648155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:02:29 iforthen kernel: [68570.565661] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 25 18:02:29 iforthen kernel: [68570.829010] UDF-fs INFO UDF: Mounting volume 'DVDVIDEO', timestamp 2010/01/25 16:05 (1e98)
Jan 25 18:04:34 iforthen kernel: [68695.376620] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:04:34 iforthen kernel: [68695.376631] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:04:34 iforthen kernel: [68695.376663] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:05:46 iforthen kernel: [68767.588128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:05:46 iforthen kernel: [68767.588140] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:05:46 iforthen kernel: [68767.588172] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:07:39 iforthen kernel: [68880.412201] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:07:39 iforthen kernel: [68880.412213] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:07:39 iforthen kernel: [68880.412245] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:12:00 iforthen kernel: [69141.544103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:12:00 iforthen kernel: [69141.544115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:12:00 iforthen kernel: [69141.544147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:14:21 iforthen kernel: [69282.564181] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:14:21 iforthen kernel: [69282.564193] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:14:21 iforthen kernel: [69282.564225] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:14:49 iforthen kernel: [69310.878955] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jan 25 18:15:43 iforthen kernel: [69364.640141] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:15:43 iforthen kernel: [69364.640153] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:15:43 iforthen kernel: [69364.640184] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:24:20 iforthen kernel: [69881.564116] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:24:20 iforthen kernel: [69881.564127] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:24:20 iforthen kernel: [69881.564160] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:26:19 iforthen kernel: [70000.772118] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:26:19 iforthen kernel: [70000.772128] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:26:19 iforthen kernel: [70000.772160] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:31:23 iforthen kernel: [70304.992128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:31:23 iforthen kernel: [70304.992139] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:31:23 iforthen kernel: [70304.992170] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:32:43 iforthen kernel: [70385.144111] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:32:43 iforthen kernel: [70385.144122] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:32:43 iforthen kernel: [70385.144154] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:34:19 iforthen kernel: [70481.208163] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:34:19 iforthen kernel: [70481.208174] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:34:19 iforthen kernel: [70481.208206] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:35:57 iforthen kernel: [70579.044103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:35:57 iforthen kernel: [70579.044114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:35:57 iforthen kernel: [70579.044146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:36:33 iforthen kernel: [70615.192142] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:36:33 iforthen kernel: [70615.192154] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:36:33 iforthen kernel: [70615.192185] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:37:00 iforthen kernel: [70641.380120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:37:00 iforthen kernel: [70641.380131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:37:00 iforthen kernel: [70641.380162] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:38:00 iforthen kernel: [70701.700135] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:38:00 iforthen kernel: [70701.700146] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:38:00 iforthen kernel: [70701.700178] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:38:41 iforthen kernel: [70742.776102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:38:41 iforthen kernel: [70742.776113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:38:41 iforthen kernel: [70742.776146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:40:21 iforthen kernel: [70842.740142] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:40:21 iforthen kernel: [70842.740154] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:40:21 iforthen kernel: [70842.740185] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:46:55 iforthen kernel: [71236.948103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:46:55 iforthen kernel: [71236.948114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:46:55 iforthen kernel: [71236.948146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:48:42 iforthen kernel: [71343.308397] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:48:42 iforthen kernel: [71343.308408] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:48:42 iforthen kernel: [71343.308440] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:50:48 iforthen kernel: [71469.448106] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:50:48 iforthen kernel: [71469.448118] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:50:48 iforthen kernel: [71469.448150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:52:16 iforthen kernel: [71558.056996] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:52:16 iforthen kernel: [71558.057008] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:52:16 iforthen kernel: [71558.057039] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:54:09 iforthen kernel: [71670.764107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:54:09 iforthen kernel: [71670.764118] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:54:09 iforthen kernel: [71670.764150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:54:43 iforthen kernel: [71704.452161] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:54:43 iforthen kernel: [71704.452173] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:54:43 iforthen kernel: [71704.452203] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:55:58 iforthen kernel: [71779.588103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:55:58 iforthen kernel: [71779.588115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:55:58 iforthen kernel: [71779.588147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:00:13 iforthen kernel: [72034.826806] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:00:13 iforthen kernel: [72034.826818] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:00:13 iforthen kernel: [72034.826850] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:01:44 iforthen kernel: [72125.348105] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:01:44 iforthen kernel: [72125.348117] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:01:44 iforthen kernel: [72125.348147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:06:47 iforthen kernel: [72429.068104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:06:47 iforthen kernel: [72429.068116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:06:47 iforthen kernel: [72429.068149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:07:39 iforthen kernel: [72480.528156] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:07:39 iforthen kernel: [72480.528167] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:07:39 iforthen kernel: [72480.528200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:11:04 iforthen kernel: [72685.808200] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:11:04 iforthen kernel: [72685.808213] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:11:04 iforthen kernel: [72685.808246] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:11:47 iforthen kernel: [72728.844103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:11:47 iforthen kernel: [72728.844114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:11:47 iforthen kernel: [72728.844147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:14:47 iforthen kernel: [72908.476161] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:14:47 iforthen kernel: [72908.476173] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:14:47 iforthen kernel: [72908.476205] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:16:33 iforthen kernel: [73015.260105] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:16:33 iforthen kernel: [73015.260117] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:16:33 iforthen kernel: [73015.260149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:16:54 iforthen kernel: [73035.564164] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:16:54 iforthen kernel: [73035.564176] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:16:54 iforthen kernel: [73035.564207] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:20:30 iforthen kernel: [73251.708101] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:20:30 iforthen kernel: [73251.708113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:20:30 iforthen kernel: [73251.708145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:25:16 iforthen kernel: [73538.140102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:25:16 iforthen kernel: [73538.140113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:25:16 iforthen kernel: [73538.140145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:26:20 iforthen kernel: [73601.916121] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:26:20 iforthen kernel: [73601.916133] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:26:20 iforthen kernel: [73601.916165] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:31:29 iforthen kernel: [73910.596363] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:31:29 iforthen kernel: [73910.596375] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:31:29 iforthen kernel: [73910.596405] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:34:48 iforthen kernel: [74109.448120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:34:48 iforthen kernel: [74109.448131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:34:48 iforthen kernel: [74109.448163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:36:09 iforthen kernel: [74190.556392] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:36:09 iforthen kernel: [74190.556403] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:36:09 iforthen kernel: [74190.556435] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:38:34 iforthen kernel: [74335.508117] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:38:34 iforthen kernel: [74335.508129] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:38:34 iforthen kernel: [74335.508161] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:51:26 iforthen kernel: [75108.216158] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:51:26 iforthen kernel: [75108.216169] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:51:26 iforthen kernel: [75108.216200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:54:58 iforthen kernel: [75319.399881] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:54:58 iforthen kernel: [75319.399892] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:54:58 iforthen kernel: [75319.399924] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:02:37 iforthen kernel: [75778.404175] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:02:37 iforthen kernel: [75778.404188] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:02:37 iforthen kernel: [75778.404220] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:04:22 iforthen kernel: [75883.796134] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:04:22 iforthen kernel: [75883.796145] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:04:22 iforthen kernel: [75883.796180] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:06:08 iforthen kernel: [75990.196152] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:06:08 iforthen kernel: [75990.196164] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:06:08 iforthen kernel: [75990.196195] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:07:29 iforthen kernel: [76071.284106] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:07:29 iforthen kernel: [76071.284117] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:07:29 iforthen kernel: [76071.284149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:09:49 iforthen kernel: [76210.796134] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:09:49 iforthen kernel: [76210.796145] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:09:49 iforthen kernel: [76210.796176] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:11:51 iforthen kernel: [76332.460108] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:11:51 iforthen kernel: [76332.460120] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:11:51 iforthen kernel: [76332.460153] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:15:59 iforthen kernel: [76581.240107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:15:59 iforthen kernel: [76581.240119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:15:59 iforthen kernel: [76581.240152] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:17:02 iforthen kernel: [76644.105522] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:17:02 iforthen kernel: [76644.105533] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:17:02 iforthen kernel: [76644.105565] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:22:01 iforthen kernel: [76942.888155] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:22:01 iforthen kernel: [76942.888167] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:22:01 iforthen kernel: [76942.888198] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:24:18 iforthen kernel: [77079.400129] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:24:18 iforthen kernel: [77079.400141] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:24:18 iforthen kernel: [77079.400171] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:27:38 iforthen kernel: [77280.228105] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:27:38 iforthen kernel: [77280.228116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:27:38 iforthen kernel: [77280.228147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:29:13 iforthen kernel: [77374.720108] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:29:13 iforthen kernel: [77374.720119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:29:13 iforthen kernel: [77374.720150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:32:21 iforthen kernel: [77563.184170] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:32:21 iforthen kernel: [77563.184181] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:32:21 iforthen kernel: [77563.184213] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:33:21 iforthen kernel: [77622.540131] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:33:21 iforthen kernel: [77622.540143] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:33:21 iforthen kernel: [77622.540175] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:35:43 iforthen kernel: [77764.520104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:35:43 iforthen kernel: [77764.520116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:35:43 iforthen kernel: [77764.520149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:36:43 iforthen kernel: [77824.824120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:36:43 iforthen kernel: [77824.824131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:36:43 iforthen kernel: [77824.824163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:38:48 iforthen kernel: [77949.492122] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:38:48 iforthen kernel: [77949.492134] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:38:48 iforthen kernel: [77949.492166] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:40:21 iforthen kernel: [78042.509078] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:40:21 iforthen kernel: [78042.509089] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:40:21 iforthen kernel: [78042.509120] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:48:42 iforthen kernel: [78543.592164] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:48:42 iforthen kernel: [78543.592176] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:48:42 iforthen kernel: [78543.592208] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:53:44 iforthen kernel: [78845.836102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:53:44 iforthen kernel: [78845.836113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:53:44 iforthen kernel: [78845.836145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:54:40 iforthen kernel: [78901.704157] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:54:40 iforthen kernel: [78901.704168] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:54:40 iforthen kernel: [78901.704200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:55:47 iforthen kernel: [78969.016102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:55:47 iforthen kernel: [78969.016113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:55:47 iforthen kernel: [78969.016145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:57:12 iforthen kernel: [79053.612157] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:57:12 iforthen kernel: [79053.612168] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:57:12 iforthen kernel: [79053.612200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:59:08 iforthen kernel: [79169.351476] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:59:08 iforthen kernel: [79169.351487] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:59:08 iforthen kernel: [79169.351518] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:06:56 iforthen kernel: [79637.808112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:06:56 iforthen kernel: [79637.808123] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:06:56 iforthen kernel: [79637.808155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:08:10 iforthen kernel: [79712.000116] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:08:10 iforthen kernel: [79712.000127] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:08:10 iforthen kernel: [79712.000159] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:12:31 iforthen kernel: [79973.176101] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:12:31 iforthen kernel: [79973.176113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:12:31 iforthen kernel: [79973.176145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:13:59 iforthen kernel: [80061.220120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:13:59 iforthen kernel: [80061.220131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:13:59 iforthen kernel: [80061.220163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:18:44 iforthen kernel: [80346.148149] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:18:44 iforthen kernel: [80346.148161] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:18:44 iforthen kernel: [80346.148193] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:20:09 iforthen kernel: [80431.236118] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:20:09 iforthen kernel: [80431.236129] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:20:09 iforthen kernel: [80431.236161] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:26:19 iforthen kernel: [80801.244203] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:26:19 iforthen kernel: [80801.244215] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:26:19 iforthen kernel: [80801.244246] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:27:51 iforthen kernel: [80893.260119] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:27:51 iforthen kernel: [80893.260130] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:27:51 iforthen kernel: [80893.260161] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:30:22 iforthen kernel: [81044.124120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:30:22 iforthen kernel: [81044.124131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:30:22 iforthen kernel: [81044.124163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:31:49 iforthen kernel: [81131.176116] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:31:49 iforthen kernel: [81131.176127] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:31:49 iforthen kernel: [81131.176158] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:37:10 iforthen kernel: [81451.705403] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:37:10 iforthen kernel: [81451.705414] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:37:10 iforthen kernel: [81451.705446] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:37:57 iforthen kernel: [81499.208102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:37:57 iforthen kernel: [81499.208114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:37:57 iforthen kernel: [81499.208146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:42:16 iforthen kernel: [81757.453292] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:42:16 iforthen kernel: [81757.453303] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:42:16 iforthen kernel: [81757.453335] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:43:18 iforthen kernel: [81819.760113] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:43:18 iforthen kernel: [81819.760124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:43:18 iforthen kernel: [81819.760155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:44:27 iforthen kernel: [81889.080163] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:44:27 iforthen kernel: [81889.080175] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:44:27 iforthen kernel: [81889.080206] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:47:03 iforthen kernel: [82044.308237] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:47:03 iforthen kernel: [82044.308268] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:47:03 iforthen kernel: [82044.308511] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:50:55 iforthen kernel: [82277.280129] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:50:56 iforthen kernel: [82277.280141] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:50:56 iforthen kernel: [82277.280172] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:51:49 iforthen kernel: [82331.240107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:51:49 iforthen kernel: [82331.240119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:51:49 iforthen kernel: [82331.240150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:55:13 iforthen kernel: [82534.556103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:55:13 iforthen kernel: [82534.556115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:55:13 iforthen kernel: [82534.556146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:55:50 iforthen kernel: [82571.644104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:55:50 iforthen kernel: [82571.644115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:55:50 iforthen kernel: [82571.644148] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:02:15 iforthen kernel: [82957.008128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:02:15 iforthen kernel: [82957.008139] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:02:15 iforthen kernel: [82957.008174] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:03:16 iforthen kernel: [83017.336107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:03:16 iforthen kernel: [83017.336119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:03:16 iforthen kernel: [83017.336149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:11:26 iforthen kernel: [83508.036119] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:11:26 iforthen kernel: [83508.036131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:11:26 iforthen kernel: [83508.036162] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:12:23 iforthen kernel: [83564.436114] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:12:23 iforthen kernel: [83564.436125] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:12:23 iforthen kernel: [83564.436156] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:14:41 iforthen kernel: [83702.448169] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:14:41 iforthen kernel: [83702.448181] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:14:41 iforthen kernel: [83702.448213] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:17:18 iforthen kernel: [83860.248136] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:17:18 iforthen kernel: [83860.248147] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:17:18 iforthen kernel: [83860.248178] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:20:17 iforthen kernel: [84038.776153] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:20:17 iforthen kernel: [84038.776165] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:20:17 iforthen kernel: [84038.776196] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:22:31 iforthen kernel: [84172.368109] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:22:31 iforthen kernel: [84172.368121] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:22:31 iforthen kernel: [84172.368153] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:25:04 iforthen kernel: [84325.276150] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:25:04 iforthen kernel: [84325.276162] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:25:04 iforthen kernel: [84325.276194] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:27:38 iforthen kernel: [84479.548112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:27:38 iforthen kernel: [84479.548124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:27:38 iforthen kernel: [84479.548156] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:30:24 iforthen kernel: [84645.768649] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:30:24 iforthen kernel: [84645.768660] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:30:24 iforthen kernel: [84645.768692] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:33:13 iforthen kernel: [84814.432205] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:33:13 iforthen kernel: [84814.432217] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:33:13 iforthen kernel: [84814.432248] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:37:53 iforthen kernel: [85094.412128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:37:53 iforthen kernel: [85094.412140] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:37:53 iforthen kernel: [85094.412170] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:40:07 iforthen kernel: [85228.465100] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:40:07 iforthen kernel: [85228.465111] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:40:07 iforthen kernel: [85228.465143] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:52:08 iforthen kernel: [85949.748166] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:52:08 iforthen kernel: [85949.748178] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:52:08 iforthen kernel: [85949.748209] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:53:02 iforthen kernel: [86003.616110] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:53:02 iforthen kernel: [86003.616122] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:53:02 iforthen kernel: [86003.616154] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:17:30 iforthen kernel: [87471.744103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:17:30 iforthen kernel: [87471.744115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:17:30 iforthen kernel: [87471.744147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:18:22 iforthen kernel: [87523.708104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:18:22 iforthen kernel: [87523.708116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:18:22 iforthen kernel: [87523.708148] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:20:45 iforthen kernel: [87667.176137] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:20:45 iforthen kernel: [87667.176148] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:20:45 iforthen kernel: [87667.176180] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:25:04 iforthen kernel: [87925.384141] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:25:04 iforthen kernel: [87925.384152] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:25:04 iforthen kernel: [87925.384184] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:27:03 iforthen kernel: [88044.572183] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:27:03 iforthen kernel: [88044.572194] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:27:03 iforthen kernel: [88044.572225] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:28:48 iforthen kernel: [88149.472104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:28:48 iforthen kernel: [88149.472116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:28:48 iforthen kernel: [88149.472148] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:31:08 iforthen kernel: [88289.960148] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:31:08 iforthen kernel: [88289.960160] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:31:08 iforthen kernel: [88289.960191] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:33:08 iforthen kernel: [88410.168122] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:33:08 iforthen kernel: [88410.168133] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:33:08 iforthen kernel: [88410.168165] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:36:47 iforthen kernel: [88629.268120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:36:47 iforthen kernel: [88629.268131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:36:47 iforthen kernel: [88629.268164] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:38:21 iforthen kernel: [88723.264128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:38:21 iforthen kernel: [88723.264139] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:38:21 iforthen kernel: [88723.264171] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:40:17 iforthen kernel: [88838.488152] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:40:17 iforthen kernel: [88838.488164] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:40:17 iforthen kernel: [88838.488195] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:41:42 iforthen kernel: [88923.601198] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:41:42 iforthen kernel: [88923.601212] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:41:42 iforthen kernel: [88923.601243] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:48:22 iforthen kernel: [89323.308153] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:48:22 iforthen kernel: [89323.308164] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:48:22 iforthen kernel: [89323.308196] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:49:48 iforthen kernel: [89409.372121] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:49:48 iforthen kernel: [89409.372133] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:49:48 iforthen kernel: [89409.372164] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:54:50 iforthen kernel: [89712.172187] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:54:50 iforthen kernel: [89712.172199] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:54:50 iforthen kernel: [89712.172230] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:55:39 iforthen kernel: [89760.580112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:55:39 iforthen kernel: [89760.580124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:55:39 iforthen kernel: [89760.580155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:57:50 iforthen kernel: [89892.176129] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:57:50 iforthen kernel: [89892.176140] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:57:50 iforthen kernel: [89892.176171] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568[/HTML]

After this error @ 23:57 it did not occur again until 0900 this morning.

I am, somewhat, an advanced Linux user and my machine is running without crashes, but the process required for this can't be giving me optimum performance.


If there is another thread that will help solve this issue, please point me in the right direction. I have been looking for discussion on this for quite some time now.

---

### Post by rsiddharth on 2010-01-27
> **trimmer said:**
> Has there been any attention from UBUNTU or Canonical at all on this thread or this error? My log file is laden with these erors, specifically:

[HTML]Jan 25 15:44:58 iforthen kernel: [60319.236131] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 15:44:58 iforthen kernel: [60319.236142] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 15:44:58 iforthen kernel: [60319.236174] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 15:47:39 iforthen kernel: [60480.680048] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:47:39 iforthen kernel: [60480.680054] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:47:39 iforthen kernel: [60480.680058] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:47:39 iforthen kernel: [60480.680064]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:47:39 iforthen kernel: [60480.680072]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:47:39 iforthen kernel: [60480.680080]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:47:39 iforthen kernel: [60480.680087] Call Trace:
Jan 25 15:47:39 iforthen kernel: [60480.680100]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:47:39 iforthen kernel: [60480.680107]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:47:39 iforthen kernel: [60480.680111]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:47:39 iforthen kernel: [60480.680115]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:47:39 iforthen kernel: [60480.680119]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:47:39 iforthen kernel: [60480.680123]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:47:39 iforthen kernel: [60480.680127]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:47:39 iforthen kernel: [60480.680131]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:47:39 iforthen kernel: [60480.680136]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:47:39 iforthen kernel: [60480.680140]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:47:39 iforthen kernel: [60480.680145]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:47:39 iforthen kernel: [60480.680149]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:47:39 iforthen kernel: [60480.680153]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:49:39 iforthen kernel: [60600.680047] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:49:39 iforthen kernel: [60600.680052] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:49:39 iforthen kernel: [60600.680056] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:49:39 iforthen kernel: [60600.680062]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:49:39 iforthen kernel: [60600.680071]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:49:39 iforthen kernel: [60600.680078]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:49:39 iforthen kernel: [60600.680086] Call Trace:
Jan 25 15:49:39 iforthen kernel: [60600.680097]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:49:39 iforthen kernel: [60600.680104]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:49:39 iforthen kernel: [60600.680108]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:49:39 iforthen kernel: [60600.680112]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:49:39 iforthen kernel: [60600.680116]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:49:39 iforthen kernel: [60600.680121]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:49:39 iforthen kernel: [60600.680125]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:49:39 iforthen kernel: [60600.680129]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:49:39 iforthen kernel: [60600.680134]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:49:39 iforthen kernel: [60600.680138]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:49:39 iforthen kernel: [60600.680143]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:49:39 iforthen kernel: [60600.680148]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:49:39 iforthen kernel: [60600.680152]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:51:39 iforthen kernel: [60720.680051] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:51:41 iforthen kernel: [60720.680056] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:51:41 iforthen kernel: [60720.680060] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:51:41 iforthen kernel: [60720.680067]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:51:41 iforthen kernel: [60720.680075]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:51:41 iforthen kernel: [60720.680082]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:51:41 iforthen kernel: [60720.680090] Call Trace:
Jan 25 15:51:41 iforthen kernel: [60720.680102]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:51:41 iforthen kernel: [60720.680108]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:51:41 iforthen kernel: [60720.680112]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:51:41 iforthen kernel: [60720.680116]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:51:41 iforthen kernel: [60720.680120]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:51:41 iforthen kernel: [60720.680125]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:51:41 iforthen kernel: [60720.680129]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:51:41 iforthen kernel: [60720.680133]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:51:41 iforthen kernel: [60720.680138]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:51:41 iforthen kernel: [60720.680142]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:51:41 iforthen kernel: [60720.680147]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:51:41 iforthen kernel: [60720.680151]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:51:41 iforthen kernel: [60720.680155]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:53:39 iforthen kernel: [60840.680050] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:53:41 iforthen kernel: [60840.680055] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:53:41 iforthen kernel: [60840.680059] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:53:41 iforthen kernel: [60840.680066]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:53:41 iforthen kernel: [60840.680074]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:53:41 iforthen kernel: [60840.680081]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:53:41 iforthen kernel: [60840.680087] Call Trace:
Jan 25 15:53:42 iforthen kernel: [60840.680099]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:53:42 iforthen kernel: [60840.680105]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:53:42 iforthen kernel: [60840.680109]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:53:42 iforthen kernel: [60840.680112]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:53:42 iforthen kernel: [60840.680116]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:53:42 iforthen kernel: [60840.680121]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:53:42 iforthen kernel: [60840.680125]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:53:42 iforthen kernel: [60840.680128]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:53:42 iforthen kernel: [60840.680133]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:53:42 iforthen kernel: [60840.680137]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:53:42 iforthen kernel: [60840.680141]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:53:42 iforthen kernel: [60840.680145]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:53:42 iforthen kernel: [60840.680149]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:55:39 iforthen kernel: [60960.680047] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:55:39 iforthen kernel: [60960.680053] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:55:39 iforthen kernel: [60960.680056] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:55:39 iforthen kernel: [60960.680063]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:55:39 iforthen kernel: [60960.680071]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:55:39 iforthen kernel: [60960.680078]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:55:39 iforthen kernel: [60960.680085] Call Trace:
Jan 25 15:55:39 iforthen kernel: [60960.680097]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:55:39 iforthen kernel: [60960.680103]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:55:39 iforthen kernel: [60960.680108]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:55:39 iforthen kernel: [60960.680112]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:55:39 iforthen kernel: [60960.680116]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:55:39 iforthen kernel: [60960.680121]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:55:39 iforthen kernel: [60960.680125]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:55:39 iforthen kernel: [60960.680129]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:55:39 iforthen kernel: [60960.680134]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:55:39 iforthen kernel: [60960.680138]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:55:39 iforthen kernel: [60960.680143]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:55:39 iforthen kernel: [60960.680148]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:55:39 iforthen kernel: [60960.680152]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:57:39 iforthen kernel: [61080.680050] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:57:43 iforthen kernel: [61080.680056] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:57:43 iforthen kernel: [61080.680060] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:57:43 iforthen kernel: [61080.680066]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:57:43 iforthen kernel: [61080.680075]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:57:43 iforthen kernel: [61080.680082]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:57:43 iforthen kernel: [61080.680090] Call Trace:
Jan 25 15:57:43 iforthen kernel: [61080.680102]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:57:43 iforthen kernel: [61080.680108]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:57:43 iforthen kernel: [61080.680112]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:57:43 iforthen kernel: [61080.680116]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:57:43 iforthen kernel: [61080.680120]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:57:43 iforthen kernel: [61080.680125]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:57:43 iforthen kernel: [61080.680130]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:57:43 iforthen kernel: [61080.680134]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:57:43 iforthen kernel: [61080.680138]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:57:43 iforthen kernel: [61080.680143]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:57:43 iforthen kernel: [61080.680148]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:57:43 iforthen kernel: [61080.680153]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:57:43 iforthen kernel: [61080.680157]  [<c05710f3>] error_code+0x73/0x80
Jan 25 15:59:39 iforthen kernel: [61200.680046] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 15:59:42 iforthen kernel: [61200.680051] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:59:42 iforthen kernel: [61200.680055] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 15:59:42 iforthen kernel: [61200.680061]  d1dc5e3c 00000086 d1dc5e34 c08145c0 d352e718 c08145c0 4cbe6d68 000036e3
Jan 25 15:59:42 iforthen kernel: [61200.680069]  c08145c0 c08145c0 d352e718 c08145c0 4cbcd68b 000036e3 c08145c0 dd71dc00
Jan 25 15:59:42 iforthen kernel: [61200.680077]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 15:59:42 iforthen kernel: [61200.680084] Call Trace:
Jan 25 15:59:42 iforthen kernel: [61200.680096]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 15:59:42 iforthen kernel: [61200.680102]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 15:59:42 iforthen kernel: [61200.680106]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 15:59:42 iforthen kernel: [61200.680110]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 15:59:42 iforthen kernel: [61200.680114]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 15:59:42 iforthen kernel: [61200.680120]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 15:59:42 iforthen kernel: [61200.680124]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 15:59:42 iforthen kernel: [61200.680128]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 15:59:42 iforthen kernel: [61200.680133]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 15:59:42 iforthen kernel: [61200.680137]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 15:59:42 iforthen kernel: [61200.680142]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 15:59:42 iforthen kernel: [61200.680146]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 15:59:42 iforthen kernel: [61200.680150]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:03:39 iforthen kernel: [61440.680056] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 16:03:40 iforthen kernel: [61440.680062] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 16:03:40 iforthen kernel: [61440.680066] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 16:03:40 iforthen kernel: [61440.680072]  d1dc5e3c 00000086 01412b9a c08145c0 d352e718 c08145c0 ccb49bc9 000037bc
Jan 25 16:03:40 iforthen kernel: [61440.680080]  c08145c0 c08145c0 d352e718 c08145c0 ccb38c52 000037bc c08145c0 dd71dc00
Jan 25 16:03:40 iforthen kernel: [61440.680088]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 16:03:40 iforthen kernel: [61440.680096] Call Trace:
Jan 25 16:03:40 iforthen kernel: [61440.680107]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 16:03:40 iforthen kernel: [61440.680114]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680118]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 16:03:40 iforthen kernel: [61440.680122]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680126]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 16:03:40 iforthen kernel: [61440.680131]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 16:03:40 iforthen kernel: [61440.680135]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 16:03:40 iforthen kernel: [61440.680139]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 16:03:40 iforthen kernel: [61440.680143]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 16:03:40 iforthen kernel: [61440.680148]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680153]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680157]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680161]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:03:40 iforthen kernel: [61440.680169] INFO: task tracker-indexer:1947 blocked for more than 120 seconds.
Jan 25 16:03:40 iforthen kernel: [61440.680171] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 16:03:40 iforthen kernel: [61440.680174] tracker-index D c08145c0     0  1947      1 0x00000000
Jan 25 16:03:40 iforthen kernel: [61440.680178]  d3485e3c 00000086 00a8501b c08145c0 dcf74168 c08145c0 129c65e1 000037b7
Jan 25 16:03:40 iforthen kernel: [61440.680185]  c08145c0 c08145c0 dcf74168 c08145c0 129b8ca5 000037b7 c08145c0 d3773800
Jan 25 16:03:40 iforthen kernel: [61440.680192]  dcf73ed0 c13fa5c0 00000002 d3485e84 d3485e48 c056f1ce d3485e7c d3485e50
Jan 25 16:03:40 iforthen kernel: [61440.680199] Call Trace:
Jan 25 16:03:40 iforthen kernel: [61440.680203]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 16:03:40 iforthen kernel: [61440.680207]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680210]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 16:03:40 iforthen kernel: [61440.680214]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 16:03:40 iforthen kernel: [61440.680218]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 16:03:40 iforthen kernel: [61440.680222]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 16:03:40 iforthen kernel: [61440.680231]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 16:03:40 iforthen kernel: [61440.680235]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 16:03:40 iforthen kernel: [61440.680241]  [<c03b27c8>] ? scsi_finish_command+0x98/0x100
Jan 25 16:03:40 iforthen kernel: [61440.680246]  [<c03de105>] ? ata_sff_altstatus+0x25/0x30
Jan 25 16:03:40 iforthen kernel: [61440.680249]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 16:03:40 iforthen kernel: [61440.680254]  [<c013b47d>] ? update_curr+0x21d/0x230
Jan 25 16:03:40 iforthen kernel: [61440.680258]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680262]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680266]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 16:03:40 iforthen kernel: [61440.680270]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:05:39 iforthen kernel: [61560.680045] INFO: task trackerd:1896 blocked for more than 120 seconds.
Jan 25 16:05:39 iforthen kernel: [61560.680051] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 16:05:39 iforthen kernel: [61560.680054] trackerd      D c08145c0     0  1896   1795 0x00000000
Jan 25 16:05:39 iforthen kernel: [61560.680060]  d1dc5e3c 00000086 01412b9a c08145c0 d352e718 c08145c0 ccb49bc9 000037bc
Jan 25 16:05:39 iforthen kernel: [61560.680069]  c08145c0 c08145c0 d352e718 c08145c0 ccb38c52 000037bc c08145c0 dd71dc00
Jan 25 16:05:39 iforthen kernel: [61560.680076]  d352e480 c13fa5c0 00000002 d1dc5e84 d1dc5e48 c056f1ce d1dc5e7c d1dc5e50
Jan 25 16:05:39 iforthen kernel: [61560.680083] Call Trace:
Jan 25 16:05:39 iforthen kernel: [61560.680095]  [<c056f1ce>] io_schedule+0x1e/0x30
Jan 25 16:05:39 iforthen kernel: [61560.680101]  [<c01b2d75>] sync_page+0x35/0x40
Jan 25 16:05:39 iforthen kernel: [61560.680105]  [<c056f707>] __wait_on_bit_lock+0x47/0x90
Jan 25 16:05:39 iforthen kernel: [61560.680109]  [<c01b2d40>] ? sync_page+0x0/0x40
Jan 25 16:05:39 iforthen kernel: [61560.680113]  [<c01b2d29>] __lock_page+0x79/0x80
Jan 25 16:05:39 iforthen kernel: [61560.680118]  [<c015c1b0>] ? wake_bit_function+0x0/0x50
Jan 25 16:05:39 iforthen kernel: [61560.680122]  [<c01b46e1>] find_lock_page+0x51/0x70
Jan 25 16:05:39 iforthen kernel: [61560.680126]  [<c01b4921>] filemap_fault+0x181/0x340
Jan 25 16:05:39 iforthen kernel: [61560.680131]  [<c01caa8b>] __do_fault+0x3b/0x470
Jan 25 16:05:39 iforthen kernel: [61560.680135]  [<c01cc284>] handle_mm_fault+0x134/0x380
Jan 25 16:05:39 iforthen kernel: [61560.680140]  [<c0573208>] do_page_fault+0x148/0x380
Jan 25 16:05:39 iforthen kernel: [61560.680145]  [<c05730c0>] ? do_page_fault+0x0/0x380
Jan 25 16:05:39 iforthen kernel: [61560.680149]  [<c05710f3>] error_code+0x73/0x80
Jan 25 16:42:10 iforthen kernel: [63752.200112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 16:42:11 iforthen kernel: [63752.200124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 16:42:11 iforthen kernel: [63752.200156] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 16:43:05 iforthen kernel: [63806.616108] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 16:43:05 iforthen kernel: [63806.616119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 16:43:05 iforthen kernel: [63806.616151] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 17:53:49 iforthen kernel: [68050.797791] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 17:53:49 iforthen kernel: [68050.797798] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 17:53:49 iforthen kernel: [68050.797804] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
Jan 25 17:53:49 iforthen kernel: [68050.797811] end_request: I/O error, dev sr0, sector 0
Jan 25 17:53:49 iforthen kernel: [68050.797816] __ratelimit: 9 callbacks suppressed
Jan 25 17:53:49 iforthen kernel: [68050.797819] Buffer I/O error on device sr0, logical block 0
Jan 25 17:53:49 iforthen kernel: [68050.800466] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 25 17:53:49 iforthen kernel: [68050.800470] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 25 17:53:49 iforthen kernel: [68050.800475] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
Jan 25 17:53:49 iforthen kernel: [68050.800480] end_request: I/O error, dev sr0, sector 0
Jan 25 17:53:49 iforthen kernel: [68050.800484] Buffer I/O error on device sr0, logical block 0
Jan 25 17:53:49 iforthen kernel: [68051.222846] cdrom: This disc doesn't have any tracks I recognize!
Jan 25 17:54:03 iforthen kernel: [68065.164138] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 17:54:03 iforthen kernel: [68065.164149] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 17:54:03 iforthen kernel: [68065.164180] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 17:54:52 iforthen kernel: [68113.648110] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 17:54:52 iforthen kernel: [68113.648122] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 17:54:52 iforthen kernel: [68113.648155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:02:29 iforthen kernel: [68570.565661] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 25 18:02:29 iforthen kernel: [68570.829010] UDF-fs INFO UDF: Mounting volume 'DVDVIDEO', timestamp 2010/01/25 16:05 (1e98)
Jan 25 18:04:34 iforthen kernel: [68695.376620] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:04:34 iforthen kernel: [68695.376631] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:04:34 iforthen kernel: [68695.376663] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:05:46 iforthen kernel: [68767.588128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:05:46 iforthen kernel: [68767.588140] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:05:46 iforthen kernel: [68767.588172] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:07:39 iforthen kernel: [68880.412201] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:07:39 iforthen kernel: [68880.412213] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:07:39 iforthen kernel: [68880.412245] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:12:00 iforthen kernel: [69141.544103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:12:00 iforthen kernel: [69141.544115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:12:00 iforthen kernel: [69141.544147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:14:21 iforthen kernel: [69282.564181] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:14:21 iforthen kernel: [69282.564193] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:14:21 iforthen kernel: [69282.564225] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:14:49 iforthen kernel: [69310.878955] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Jan 25 18:15:43 iforthen kernel: [69364.640141] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:15:43 iforthen kernel: [69364.640153] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:15:43 iforthen kernel: [69364.640184] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:24:20 iforthen kernel: [69881.564116] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:24:20 iforthen kernel: [69881.564127] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:24:20 iforthen kernel: [69881.564160] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:26:19 iforthen kernel: [70000.772118] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:26:19 iforthen kernel: [70000.772128] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:26:19 iforthen kernel: [70000.772160] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:31:23 iforthen kernel: [70304.992128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:31:23 iforthen kernel: [70304.992139] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:31:23 iforthen kernel: [70304.992170] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:32:43 iforthen kernel: [70385.144111] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:32:43 iforthen kernel: [70385.144122] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:32:43 iforthen kernel: [70385.144154] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:34:19 iforthen kernel: [70481.208163] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:34:19 iforthen kernel: [70481.208174] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:34:19 iforthen kernel: [70481.208206] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:35:57 iforthen kernel: [70579.044103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:35:57 iforthen kernel: [70579.044114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:35:57 iforthen kernel: [70579.044146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:36:33 iforthen kernel: [70615.192142] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:36:33 iforthen kernel: [70615.192154] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:36:33 iforthen kernel: [70615.192185] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:37:00 iforthen kernel: [70641.380120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:37:00 iforthen kernel: [70641.380131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:37:00 iforthen kernel: [70641.380162] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:38:00 iforthen kernel: [70701.700135] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:38:00 iforthen kernel: [70701.700146] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:38:00 iforthen kernel: [70701.700178] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:38:41 iforthen kernel: [70742.776102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:38:41 iforthen kernel: [70742.776113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:38:41 iforthen kernel: [70742.776146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:40:21 iforthen kernel: [70842.740142] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:40:21 iforthen kernel: [70842.740154] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:40:21 iforthen kernel: [70842.740185] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:46:55 iforthen kernel: [71236.948103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:46:55 iforthen kernel: [71236.948114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:46:55 iforthen kernel: [71236.948146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:48:42 iforthen kernel: [71343.308397] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:48:42 iforthen kernel: [71343.308408] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:48:42 iforthen kernel: [71343.308440] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:50:48 iforthen kernel: [71469.448106] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:50:48 iforthen kernel: [71469.448118] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:50:48 iforthen kernel: [71469.448150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:52:16 iforthen kernel: [71558.056996] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:52:16 iforthen kernel: [71558.057008] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:52:16 iforthen kernel: [71558.057039] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:54:09 iforthen kernel: [71670.764107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:54:09 iforthen kernel: [71670.764118] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:54:09 iforthen kernel: [71670.764150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:54:43 iforthen kernel: [71704.452161] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:54:43 iforthen kernel: [71704.452173] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:54:43 iforthen kernel: [71704.452203] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 18:55:58 iforthen kernel: [71779.588103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 18:55:58 iforthen kernel: [71779.588115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 18:55:58 iforthen kernel: [71779.588147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:00:13 iforthen kernel: [72034.826806] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:00:13 iforthen kernel: [72034.826818] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:00:13 iforthen kernel: [72034.826850] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:01:44 iforthen kernel: [72125.348105] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:01:44 iforthen kernel: [72125.348117] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:01:44 iforthen kernel: [72125.348147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:06:47 iforthen kernel: [72429.068104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:06:47 iforthen kernel: [72429.068116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:06:47 iforthen kernel: [72429.068149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:07:39 iforthen kernel: [72480.528156] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:07:39 iforthen kernel: [72480.528167] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:07:39 iforthen kernel: [72480.528200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:11:04 iforthen kernel: [72685.808200] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:11:04 iforthen kernel: [72685.808213] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:11:04 iforthen kernel: [72685.808246] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:11:47 iforthen kernel: [72728.844103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:11:47 iforthen kernel: [72728.844114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:11:47 iforthen kernel: [72728.844147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:14:47 iforthen kernel: [72908.476161] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:14:47 iforthen kernel: [72908.476173] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:14:47 iforthen kernel: [72908.476205] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:16:33 iforthen kernel: [73015.260105] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:16:33 iforthen kernel: [73015.260117] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:16:33 iforthen kernel: [73015.260149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:16:54 iforthen kernel: [73035.564164] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:16:54 iforthen kernel: [73035.564176] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:16:54 iforthen kernel: [73035.564207] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:20:30 iforthen kernel: [73251.708101] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:20:30 iforthen kernel: [73251.708113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:20:30 iforthen kernel: [73251.708145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:25:16 iforthen kernel: [73538.140102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:25:16 iforthen kernel: [73538.140113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:25:16 iforthen kernel: [73538.140145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:26:20 iforthen kernel: [73601.916121] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:26:20 iforthen kernel: [73601.916133] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:26:20 iforthen kernel: [73601.916165] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:31:29 iforthen kernel: [73910.596363] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:31:29 iforthen kernel: [73910.596375] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:31:29 iforthen kernel: [73910.596405] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:34:48 iforthen kernel: [74109.448120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:34:48 iforthen kernel: [74109.448131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:34:48 iforthen kernel: [74109.448163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:36:09 iforthen kernel: [74190.556392] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:36:09 iforthen kernel: [74190.556403] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:36:09 iforthen kernel: [74190.556435] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:38:34 iforthen kernel: [74335.508117] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:38:34 iforthen kernel: [74335.508129] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:38:34 iforthen kernel: [74335.508161] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:51:26 iforthen kernel: [75108.216158] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:51:26 iforthen kernel: [75108.216169] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:51:26 iforthen kernel: [75108.216200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 19:54:58 iforthen kernel: [75319.399881] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 19:54:58 iforthen kernel: [75319.399892] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 19:54:58 iforthen kernel: [75319.399924] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:02:37 iforthen kernel: [75778.404175] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:02:37 iforthen kernel: [75778.404188] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:02:37 iforthen kernel: [75778.404220] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:04:22 iforthen kernel: [75883.796134] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:04:22 iforthen kernel: [75883.796145] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:04:22 iforthen kernel: [75883.796180] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:06:08 iforthen kernel: [75990.196152] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:06:08 iforthen kernel: [75990.196164] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:06:08 iforthen kernel: [75990.196195] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:07:29 iforthen kernel: [76071.284106] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:07:29 iforthen kernel: [76071.284117] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:07:29 iforthen kernel: [76071.284149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:09:49 iforthen kernel: [76210.796134] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:09:49 iforthen kernel: [76210.796145] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:09:49 iforthen kernel: [76210.796176] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:11:51 iforthen kernel: [76332.460108] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:11:51 iforthen kernel: [76332.460120] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:11:51 iforthen kernel: [76332.460153] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:15:59 iforthen kernel: [76581.240107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:15:59 iforthen kernel: [76581.240119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:15:59 iforthen kernel: [76581.240152] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:17:02 iforthen kernel: [76644.105522] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:17:02 iforthen kernel: [76644.105533] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:17:02 iforthen kernel: [76644.105565] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:22:01 iforthen kernel: [76942.888155] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:22:01 iforthen kernel: [76942.888167] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:22:01 iforthen kernel: [76942.888198] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:24:18 iforthen kernel: [77079.400129] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:24:18 iforthen kernel: [77079.400141] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:24:18 iforthen kernel: [77079.400171] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:27:38 iforthen kernel: [77280.228105] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:27:38 iforthen kernel: [77280.228116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:27:38 iforthen kernel: [77280.228147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:29:13 iforthen kernel: [77374.720108] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:29:13 iforthen kernel: [77374.720119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:29:13 iforthen kernel: [77374.720150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:32:21 iforthen kernel: [77563.184170] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:32:21 iforthen kernel: [77563.184181] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:32:21 iforthen kernel: [77563.184213] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:33:21 iforthen kernel: [77622.540131] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:33:21 iforthen kernel: [77622.540143] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:33:21 iforthen kernel: [77622.540175] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:35:43 iforthen kernel: [77764.520104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:35:43 iforthen kernel: [77764.520116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:35:43 iforthen kernel: [77764.520149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:36:43 iforthen kernel: [77824.824120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:36:43 iforthen kernel: [77824.824131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:36:43 iforthen kernel: [77824.824163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:38:48 iforthen kernel: [77949.492122] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:38:48 iforthen kernel: [77949.492134] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:38:48 iforthen kernel: [77949.492166] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:40:21 iforthen kernel: [78042.509078] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:40:21 iforthen kernel: [78042.509089] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:40:21 iforthen kernel: [78042.509120] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:48:42 iforthen kernel: [78543.592164] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:48:42 iforthen kernel: [78543.592176] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:48:42 iforthen kernel: [78543.592208] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:53:44 iforthen kernel: [78845.836102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:53:44 iforthen kernel: [78845.836113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:53:44 iforthen kernel: [78845.836145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:54:40 iforthen kernel: [78901.704157] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:54:40 iforthen kernel: [78901.704168] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:54:40 iforthen kernel: [78901.704200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:55:47 iforthen kernel: [78969.016102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:55:47 iforthen kernel: [78969.016113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:55:47 iforthen kernel: [78969.016145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:57:12 iforthen kernel: [79053.612157] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:57:12 iforthen kernel: [79053.612168] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:57:12 iforthen kernel: [79053.612200] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 20:59:08 iforthen kernel: [79169.351476] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 20:59:08 iforthen kernel: [79169.351487] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 20:59:08 iforthen kernel: [79169.351518] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:06:56 iforthen kernel: [79637.808112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:06:56 iforthen kernel: [79637.808123] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:06:56 iforthen kernel: [79637.808155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:08:10 iforthen kernel: [79712.000116] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:08:10 iforthen kernel: [79712.000127] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:08:10 iforthen kernel: [79712.000159] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:12:31 iforthen kernel: [79973.176101] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:12:31 iforthen kernel: [79973.176113] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:12:31 iforthen kernel: [79973.176145] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:13:59 iforthen kernel: [80061.220120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:13:59 iforthen kernel: [80061.220131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:13:59 iforthen kernel: [80061.220163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:18:44 iforthen kernel: [80346.148149] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:18:44 iforthen kernel: [80346.148161] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:18:44 iforthen kernel: [80346.148193] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:20:09 iforthen kernel: [80431.236118] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:20:09 iforthen kernel: [80431.236129] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:20:09 iforthen kernel: [80431.236161] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:26:19 iforthen kernel: [80801.244203] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:26:19 iforthen kernel: [80801.244215] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:26:19 iforthen kernel: [80801.244246] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:27:51 iforthen kernel: [80893.260119] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:27:51 iforthen kernel: [80893.260130] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:27:51 iforthen kernel: [80893.260161] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:30:22 iforthen kernel: [81044.124120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:30:22 iforthen kernel: [81044.124131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:30:22 iforthen kernel: [81044.124163] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:31:49 iforthen kernel: [81131.176116] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:31:49 iforthen kernel: [81131.176127] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:31:49 iforthen kernel: [81131.176158] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:37:10 iforthen kernel: [81451.705403] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:37:10 iforthen kernel: [81451.705414] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:37:10 iforthen kernel: [81451.705446] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:37:57 iforthen kernel: [81499.208102] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:37:57 iforthen kernel: [81499.208114] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:37:57 iforthen kernel: [81499.208146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:42:16 iforthen kernel: [81757.453292] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:42:16 iforthen kernel: [81757.453303] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:42:16 iforthen kernel: [81757.453335] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:43:18 iforthen kernel: [81819.760113] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:43:18 iforthen kernel: [81819.760124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:43:18 iforthen kernel: [81819.760155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:44:27 iforthen kernel: [81889.080163] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:44:27 iforthen kernel: [81889.080175] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:44:27 iforthen kernel: [81889.080206] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:47:03 iforthen kernel: [82044.308237] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:47:03 iforthen kernel: [82044.308268] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:47:03 iforthen kernel: [82044.308511] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:50:55 iforthen kernel: [82277.280129] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:50:56 iforthen kernel: [82277.280141] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:50:56 iforthen kernel: [82277.280172] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:51:49 iforthen kernel: [82331.240107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:51:49 iforthen kernel: [82331.240119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:51:49 iforthen kernel: [82331.240150] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:55:13 iforthen kernel: [82534.556103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:55:13 iforthen kernel: [82534.556115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:55:13 iforthen kernel: [82534.556146] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 21:55:50 iforthen kernel: [82571.644104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 21:55:50 iforthen kernel: [82571.644115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 21:55:50 iforthen kernel: [82571.644148] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:02:15 iforthen kernel: [82957.008128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:02:15 iforthen kernel: [82957.008139] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:02:15 iforthen kernel: [82957.008174] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:03:16 iforthen kernel: [83017.336107] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:03:16 iforthen kernel: [83017.336119] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:03:16 iforthen kernel: [83017.336149] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:11:26 iforthen kernel: [83508.036119] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:11:26 iforthen kernel: [83508.036131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:11:26 iforthen kernel: [83508.036162] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:12:23 iforthen kernel: [83564.436114] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:12:23 iforthen kernel: [83564.436125] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:12:23 iforthen kernel: [83564.436156] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:14:41 iforthen kernel: [83702.448169] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:14:41 iforthen kernel: [83702.448181] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:14:41 iforthen kernel: [83702.448213] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:17:18 iforthen kernel: [83860.248136] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:17:18 iforthen kernel: [83860.248147] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:17:18 iforthen kernel: [83860.248178] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:20:17 iforthen kernel: [84038.776153] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:20:17 iforthen kernel: [84038.776165] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:20:17 iforthen kernel: [84038.776196] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:22:31 iforthen kernel: [84172.368109] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:22:31 iforthen kernel: [84172.368121] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:22:31 iforthen kernel: [84172.368153] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:25:04 iforthen kernel: [84325.276150] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:25:04 iforthen kernel: [84325.276162] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:25:04 iforthen kernel: [84325.276194] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:27:38 iforthen kernel: [84479.548112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:27:38 iforthen kernel: [84479.548124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:27:38 iforthen kernel: [84479.548156] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:30:24 iforthen kernel: [84645.768649] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:30:24 iforthen kernel: [84645.768660] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:30:24 iforthen kernel: [84645.768692] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:33:13 iforthen kernel: [84814.432205] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:33:13 iforthen kernel: [84814.432217] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:33:13 iforthen kernel: [84814.432248] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:37:53 iforthen kernel: [85094.412128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:37:53 iforthen kernel: [85094.412140] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:37:53 iforthen kernel: [85094.412170] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:40:07 iforthen kernel: [85228.465100] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:40:07 iforthen kernel: [85228.465111] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:40:07 iforthen kernel: [85228.465143] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:52:08 iforthen kernel: [85949.748166] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:52:08 iforthen kernel: [85949.748178] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:52:08 iforthen kernel: [85949.748209] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 22:53:02 iforthen kernel: [86003.616110] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 22:53:02 iforthen kernel: [86003.616122] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 22:53:02 iforthen kernel: [86003.616154] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:17:30 iforthen kernel: [87471.744103] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:17:30 iforthen kernel: [87471.744115] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:17:30 iforthen kernel: [87471.744147] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:18:22 iforthen kernel: [87523.708104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:18:22 iforthen kernel: [87523.708116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:18:22 iforthen kernel: [87523.708148] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:20:45 iforthen kernel: [87667.176137] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:20:45 iforthen kernel: [87667.176148] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:20:45 iforthen kernel: [87667.176180] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:25:04 iforthen kernel: [87925.384141] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:25:04 iforthen kernel: [87925.384152] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:25:04 iforthen kernel: [87925.384184] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:27:03 iforthen kernel: [88044.572183] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:27:03 iforthen kernel: [88044.572194] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:27:03 iforthen kernel: [88044.572225] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:28:48 iforthen kernel: [88149.472104] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:28:48 iforthen kernel: [88149.472116] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:28:48 iforthen kernel: [88149.472148] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:31:08 iforthen kernel: [88289.960148] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:31:08 iforthen kernel: [88289.960160] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:31:08 iforthen kernel: [88289.960191] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:33:08 iforthen kernel: [88410.168122] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:33:08 iforthen kernel: [88410.168133] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:33:08 iforthen kernel: [88410.168165] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:36:47 iforthen kernel: [88629.268120] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:36:47 iforthen kernel: [88629.268131] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:36:47 iforthen kernel: [88629.268164] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:38:21 iforthen kernel: [88723.264128] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:38:21 iforthen kernel: [88723.264139] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:38:21 iforthen kernel: [88723.264171] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:40:17 iforthen kernel: [88838.488152] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:40:17 iforthen kernel: [88838.488164] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:40:17 iforthen kernel: [88838.488195] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:41:42 iforthen kernel: [88923.601198] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:41:42 iforthen kernel: [88923.601212] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:41:42 iforthen kernel: [88923.601243] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:48:22 iforthen kernel: [89323.308153] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:48:22 iforthen kernel: [89323.308164] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:48:22 iforthen kernel: [89323.308196] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:49:48 iforthen kernel: [89409.372121] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:49:48 iforthen kernel: [89409.372133] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:49:48 iforthen kernel: [89409.372164] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:54:50 iforthen kernel: [89712.172187] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:54:50 iforthen kernel: [89712.172199] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:54:50 iforthen kernel: [89712.172230] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:55:39 iforthen kernel: [89760.580112] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:55:39 iforthen kernel: [89760.580124] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:55:39 iforthen kernel: [89760.580155] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568
Jan 25 23:57:50 iforthen kernel: [89892.176129] ACPI Error (psargs-0359): [\_TZ_.THRM] Namespace lookup failure, AE_NOT_FOUND
Jan 25 23:57:50 iforthen kernel: [89892.176140] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L1C] (Node dec11468), AE_NOT_FOUND
Jan 25 23:57:50 iforthen kernel: [89892.176171] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L1C] 20090521 evgpe-568[/HTML]After this error @ 23:57 it did not occur again until 0900 this morning.

I am, somewhat, an advanced Linux user and my machine is running without crashes, but the process required for this can't be giving me optimum performance.


If there is another thread that will help solve this issue, please point me in the right direction. I have been looking for discussion on this for quite some time now.

Lately , I  stopped  putting my comp in standby ( suspend) mode and soon this system hang stopped and I never faced the 'hang' anymore . I am real GNU/Linux novice and my experience with this lovely system is only 6 months old . :D

---

