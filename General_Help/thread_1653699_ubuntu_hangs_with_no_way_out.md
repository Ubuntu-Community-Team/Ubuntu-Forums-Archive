---
title: "ubuntu hangs with no way out"
date: 2010-12-27
forum: General Help
---

### Post by teknojunkey on 2010-12-27
Hi if anyone can help me i would appreciate it ...

I have been using the following :

10.04 
kernel 2.6.32-27-generic-pae 
gnome2.30.2

every so often the system freezes with no way out other than a reset.
as the system crashes i dont know whats going on, i initialy thought it was memory but this is not the case as it crashed while using 375MB of 3.7GB

is there a log file i can look at to find the problem source ?

thanks

---

### Post by davidmohammed on 2010-12-27
what is your graphics card?

type in a terminal

lspci | grep VGA

copy and paste the displayed output in a reply here.

---

### Post by teknojunkey on 2010-12-27
ah this is where it gets messy ... 

~$ lspci | grep VGA

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2) - (1 monitor attached)

01:05.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (- not in use but plugged in)

02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
 - (2 monitor attached)

thanks for your help

---

### Post by davidmohammed on 2010-12-27
hmmm - looks like a complicated setup.

I would recommend that you look at your kernel logs (System Administration - Log File Viewer).  They are time based so you can see what was happening around the time of the hang, just before you reboot.

Alternatively/additionally I would recommend you simplify your setup just for testing purposes - for example, pull out all your graphics cards and other hardware.  Then one by one add in each hardware - run for a while before plugging in the next hardware.  Hopefully you then find what hardware is causing the issue.

---

### Post by IWantFroyo on 2010-12-27
Check the CPU and chipset voltages in BIOS, if they're more than .3 volts away from the standard, that's probably the problem.

---

### Post by jumon on 2010-12-27
I had a similar problem once I was in the gnome GUI environment (not sure if you are crashing before that or what).  Turns out the video drivers are not quite stable for my system.  I had to turn off visual effects to keep it from crashing and this might be worth a try for you.

System > Preferences > Appearance -> Visual Effects (select "None" here)

After I did this the system/desktop stopped freezing up.

---

### Post by teknojunkey on 2010-12-29
hi,

visual effects are disabled

I checked the system log and see this ... 

Dec 29 13:29:21 HAL-9000 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 29 13:29:21 HAL-9000 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="714" x-info="http://www.rsyslog.com"] (re)start
Dec 29 13:29:21 HAL-9000 rsyslogd: rsyslogd's groupid changed to 103
Dec 29 13:29:21 HAL-9000 rsyslogd: rsyslogd's userid changed to 101
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Linux version 2.6.32-27-generic-pae (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 (Ubuntu 2.6.32-27.49-generic-pae 2.6.32.26+drm33.12)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] KERNEL supported cpus:
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   Intel GenuineIntel
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   AMD AuthenticAMD
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   NSC Geode by NSC
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   Cyrix CyrixInstead
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   Centaur CentaurHauls
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   UMC UMC UMC UMC
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000afee0000 (usable)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000afee0000 - 00000000afee3000 (ACPI NVS)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000afee3000 - 00000000afef0000 (ACPI data)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000afef0000 - 00000000aff00000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000b0000000 - 00000000c0000000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] DMI 2.4 present.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] modified physical RAM map:
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 0000000000100000 - 00000000afee0000 (usable)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000afee0000 - 00000000afee3000 (ACPI NVS)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000afee3000 - 00000000afef0000 (ACPI data)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000afef0000 - 00000000aff00000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000b0000000 - 00000000c0000000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] RAMDISK: 37821000 - 37fef9b6
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Allocated new RAMDISK: 0093e000 - 0110c9b6
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Move RAMDISK from 0000000037821000 - 0000000037fef9b5 to 0093e000 - 0110c9b5
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: RSDP 000f7a10 00014 (v00 Nvidia)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: RSDT afee3040 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: FACP afee30c0 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: DSDT afee3180 06395 (v01 NVIDIA NVDAACPI 00001000 MSFT 0100000E)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: FACS afee0000 00040
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: SSDT afee9640 00248 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: _HPT afee9900 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: MCFG afee9980 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: APIC afee9580 0007C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] 4230MB HIGHMEM available.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] 889MB LOWMEM available.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   low ram: 0 - 379fe000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   node 0 bootmap 00012000 - 00018f40
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #3 [0000100000 - 0000935818]    TEXT DATA BSS ==> [0000100000 - 0000935818]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #5 [0000936000 - 000093d11d]              BRK ==> [0000936000 - 000093d11d]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #7 [000093e000 - 000110c9b6]      NEW RAMDISK ==> [000093e000 - 000110c9b6]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] found SMP MP-table at [c00f3a00] f3a00
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Zone PFN ranges:
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]   HighMem  0x000379fe -> 0x00140000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Movable zone start PFN for each node
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] early_node_map[3] active PFN ranges
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     0: 0x00000100 -> 0x000afee0
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Using APIC driver default
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] PERCPU: Embedded 15 pages/cpu @c3a00000 s39480 r0 d21960 u1048576
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] pcpu-alloc: s39480 r0 d21960 u1048576 alloc=1*2097152
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 972398
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=9f3cf171-d6b6-4ab8-9912-4d6a5f13edeb ro quiet splash
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Initializing CPU#0
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] allocated 26214080 bytes of page_cgroup
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Memory: 3845560k/5242880k available (4835k kernel code, 84004k reserved, 2218k data, 672k init, 3019656k highmem)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] virtual kernel memory layout:
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]       .init : 0xc07e4000 - 0xc088c000   ( 672 kB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]       .data : 0xc05b8ebf - 0xc07e36e8   (2218 kB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05b8ebf   (4835 kB)
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Hierarchical RCU implementation.
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] console [tty0] enabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Fast TSC calibration using PIT
Dec 29 13:29:21 HAL-9000 kernel: [    0.000000] Detected 2440.872 MHz processor.
Dec 29 13:29:21 HAL-9000 kernel: [    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4881.74 BogoMIPS (lpj=9763488)
Dec 29 13:29:21 HAL-9000 kernel: [    0.008018] Security Framework initialized
Dec 29 13:29:21 HAL-9000 kernel: [    0.008034] AppArmor: AppArmor initialized
Dec 29 13:29:21 HAL-9000 kernel: [    0.008039] Mount-cache hash table entries: 512
Dec 29 13:29:21 HAL-9000 kernel: [    0.008137] Initializing cgroup subsys ns
Dec 29 13:29:21 HAL-9000 kernel: [    0.008140] Initializing cgroup subsys cpuacct
Dec 29 13:29:21 HAL-9000 kernel: [    0.008144] Initializing cgroup subsys memory
Dec 29 13:29:21 HAL-9000 kernel: [    0.008150] Initializing cgroup subsys devices
Dec 29 13:29:21 HAL-9000 kernel: [    0.008152] Initializing cgroup subsys freezer
Dec 29 13:29:21 HAL-9000 kernel: [    0.008154] Initializing cgroup subsys net_cls
Dec 29 13:29:21 HAL-9000 kernel: [    0.008168] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec 29 13:29:21 HAL-9000 kernel: [    0.008170] CPU: L2 Cache: 512K (64 bytes/line)
Dec 29 13:29:21 HAL-9000 kernel: [    0.008173] CPU: Physical Processor ID: 0
Dec 29 13:29:21 HAL-9000 kernel: [    0.008174] CPU: Processor Core ID: 0
Dec 29 13:29:21 HAL-9000 kernel: [    0.008177] mce: CPU supports 5 MCE banks
Dec 29 13:29:21 HAL-9000 kernel: [    0.008187] using C1E aware idle routine
Dec 29 13:29:21 HAL-9000 kernel: [    0.008193] Performance Events: AMD PMU driver.
Dec 29 13:29:21 HAL-9000 kernel: [    0.008196] ... version:                0
Dec 29 13:29:21 HAL-9000 kernel: [    0.008198] ... bit width:              48
Dec 29 13:29:21 HAL-9000 kernel: [    0.008199] ... generic registers:      4
Dec 29 13:29:21 HAL-9000 kernel: [    0.008201] ... value mask:             0000ffffffffffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.008203] ... max period:             00007fffffffffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.008205] ... fixed-purpose events:   0
Dec 29 13:29:21 HAL-9000 kernel: [    0.008206] ... event mask:             000000000000000f
Dec 29 13:29:21 HAL-9000 kernel: [    0.008210] Checking 'hlt' instruction... OK.
Dec 29 13:29:21 HAL-9000 kernel: [    0.025867] ACPI: Core revision 20090903
Dec 29 13:29:21 HAL-9000 kernel: [    0.034297] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 29 13:29:21 HAL-9000 kernel: [    0.034302] ftrace: allocating 22417 entries in 44 pages
Dec 29 13:29:21 HAL-9000 kernel: [    0.036079] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 29 13:29:21 HAL-9000 kernel: [    0.040303] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Dec 29 13:29:21 HAL-9000 kernel: [    0.079989] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Dec 29 13:29:21 HAL-9000 kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Dec 29 13:29:21 HAL-9000 kernel: [    0.012000] Initializing CPU#1
Dec 29 13:29:21 HAL-9000 kernel: [    0.012000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec 29 13:29:21 HAL-9000 kernel: [    0.012000] CPU: L2 Cache: 512K (64 bytes/line)
Dec 29 13:29:21 HAL-9000 kernel: [    0.012000] CPU: Physical Processor ID: 0
Dec 29 13:29:21 HAL-9000 kernel: [    0.012000] CPU: Processor Core ID: 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.164099] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Dec 29 13:29:21 HAL-9000 kernel: [    0.164122] Brought up 2 CPUs
Dec 29 13:29:21 HAL-9000 kernel: [    0.164124] Total of 2 processors activated (9764.56 BogoMIPS).
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] devtmpfs: initialized
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] regulator: core version 0.5
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] Time: 13:29:16  Date: 12/29/10
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] NET: Registered protocol family 16
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] EISA bus registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] ACPI: bus type pci registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] PCI: MCFG area at f0000000 reserved in E820
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] PCI: Using MMCONFIG for extended config space
Dec 29 13:29:21 HAL-9000 kernel: [    0.164378] PCI: Using configuration type 1 for base access
Dec 29 13:29:21 HAL-9000 kernel: [    0.165046] Trying to unpack rootfs image as initramfs...
Dec 29 13:29:21 HAL-9000 kernel: [    0.168058] bio: create slab <bio-0> at 0
Dec 29 13:29:21 HAL-9000 kernel: [    0.175029] ACPI: Interpreter enabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.175032] ACPI: (supports S0 S3 S4 S5)
Dec 29 13:29:21 HAL-9000 kernel: [    0.175051] ACPI: Using IOAPIC for interrupt routing
Dec 29 13:29:21 HAL-9000 kernel: [    0.182459] ACPI: No dock devices found.
Dec 29 13:29:21 HAL-9000 kernel: [    0.183233] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 29 13:29:21 HAL-9000 kernel: [    0.183466] pci 0000:00:01.1: PME# supported from D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183471] pci 0000:00:01.1: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.183617] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183620] pci 0000:00:02.0: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.183668] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183671] pci 0000:00:02.1: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.183753] pci 0000:00:05.0: PME# supported from D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183756] pci 0000:00:05.0: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.183882] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183885] pci 0000:00:09.0: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.183917] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183919] pci 0000:00:0b.0: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.183952] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.183954] pci 0000:00:0c.0: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.184131] pci 0000:01:08.0: PME# supported from D1 D2 D3hot D3cold
Dec 29 13:29:21 HAL-9000 kernel: [    0.184134] pci 0000:01:08.0: PME# disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.184158] pci 0000:00:04.0: transparent bridge
Dec 29 13:29:21 HAL-9000 kernel: [    0.220743] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.220860] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.220977] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.221092] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.221207] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.221323] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.221439] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.221556] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 *11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.221672] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.221787] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.221904] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.222019] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.222136] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.222252] ACPI: PCI Interrupt Link [LPMU] (IRQs *5 7 9 10 11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.222368] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.222484] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.222600] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.222716] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Dec 29 13:29:21 HAL-9000 kernel: [    0.222831] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.222986] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.223132] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.223280] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.223426] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.223573] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.223719] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.223865] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.224018] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.224164] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.224311] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.224458] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.224605] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.224752] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.224899] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.225046] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.225193] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.225341] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.225489] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Dec 29 13:29:21 HAL-9000 kernel: [    0.225638] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Dec 29 13:29:21 HAL-9000 kernel: [    0.225741] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=none,locks=none
Dec 29 13:29:21 HAL-9000 kernel: [    0.225747] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 29 13:29:21 HAL-9000 kernel: [    0.225749] vgaarb: loaded
Dec 29 13:29:21 HAL-9000 kernel: [    0.225839] SCSI subsystem initialized
Dec 29 13:29:21 HAL-9000 kernel: [    0.225983] usbcore: registered new interface driver usbfs
Dec 29 13:29:21 HAL-9000 kernel: [    0.225993] usbcore: registered new interface driver hub
Dec 29 13:29:21 HAL-9000 kernel: [    0.226015] usbcore: registered new device driver usb
Dec 29 13:29:21 HAL-9000 kernel: [    0.226125] ACPI: WMI: Mapper loaded
Dec 29 13:29:21 HAL-9000 kernel: [    0.226127] PCI: Using ACPI for IRQ routing
Dec 29 13:29:21 HAL-9000 kernel: [    0.226258] NetLabel: Initializing
Dec 29 13:29:21 HAL-9000 kernel: [    0.226259] NetLabel:  domain hash size = 128
Dec 29 13:29:21 HAL-9000 kernel: [    0.226261] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 29 13:29:21 HAL-9000 kernel: [    0.226273] NetLabel:  unlabeled traffic allowed by default
Dec 29 13:29:21 HAL-9000 kernel: [    0.227836] AppArmor: AppArmor Filesystem Enabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.227851] pnp: PnP ACPI init
Dec 29 13:29:21 HAL-9000 kernel: [    0.227863] ACPI: bus type pnp registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.232695] pnp: PnP ACPI: found 14 devices
Dec 29 13:29:21 HAL-9000 kernel: [    0.232697] ACPI: ACPI bus type pnp unregistered
Dec 29 13:29:21 HAL-9000 kernel: [    0.232700] PnPBIOS: Disabled by ACPI PNP
Dec 29 13:29:21 HAL-9000 kernel: [    0.232712] system 00:01: ioport range 0x1000-0x107f has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232715] system 00:01: ioport range 0x1080-0x10ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232718] system 00:01: ioport range 0x1400-0x147f has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232720] system 00:01: ioport range 0x1480-0x14ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232723] system 00:01: ioport range 0x1800-0x187f has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232726] system 00:01: ioport range 0x1880-0x18ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232729] system 00:01: ioport range 0x2000-0x207f has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232731] system 00:01: ioport range 0x2080-0x20ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232735] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232738] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232741] system 00:01: iomem range 0xb0000000-0xbfffffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232746] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232749] system 00:02: ioport range 0x800-0x87f has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232751] system 00:02: ioport range 0x290-0x297 has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232758] system 00:0c: iomem range 0xf0000000-0xf3ffffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232763] system 00:0d: iomem range 0xf0000-0xfffff could not be reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232766] system 00:0d: iomem range 0xfeff0000-0xfeff00ff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232768] system 00:0d: iomem range 0xafee0000-0xafefffff could not be reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232771] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232774] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232777] system 00:0d: iomem range 0x100000-0xafedffff could not be reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232779] system 00:0d: iomem range 0xaff00000-0xbfefffff could not be reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232782] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232785] system 00:0d: iomem range 0xfee00000-0xfeefffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232788] system 00:0d: iomem range 0xfefff000-0xfeffffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232791] system 00:0d: iomem range 0xfff80000-0xfff80fff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232794] system 00:0d: iomem range 0xfff90000-0xfffbffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.232797] system 00:0d: iomem range 0xfffed000-0xfffeffff has been reserved
Dec 29 13:29:21 HAL-9000 kernel: [    0.267431] Switching to clocksource acpi_pm
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:04.0:   IO window: 0xc000-0xcfff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:04.0:   MEM window: 0xfd900000-0xfd9fffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:09.0:   IO window: 0xb000-0xbfff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:09.0:   MEM window: 0xf8000000-0xfaffffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:09.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0b.0:   IO window: 0xa000-0xafff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0b.0:   MEM window: 0xfdd00000-0xfddfffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0c.0:   IO window: 0x9000-0x9fff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0c.0:   MEM window: 0xfdb00000-0xfdbfffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] pci 0000:00:0c.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] NET: Registered protocol family 2
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] TCP: Hash tables configured (established 131072 bind 65536)
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] TCP reno registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.267728] NET: Registered protocol family 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.284078] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 29 13:29:21 HAL-9000 kernel: [    0.284125] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 29 13:29:21 HAL-9000 kernel: [    0.284178] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 29 13:29:21 HAL-9000 kernel: [    0.284231] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 29 13:29:21 HAL-9000 kernel: [    0.284289] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 29 13:29:21 HAL-9000 kernel: [    0.284350] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 29 13:29:21 HAL-9000 kernel: [    0.284530] cpufreq-nforce2: No nForce2 chipset.
Dec 29 13:29:21 HAL-9000 kernel: [    0.284552] Scanning for low memory corruption every 60 seconds
Dec 29 13:29:21 HAL-9000 kernel: [    0.284637] audit: initializing netlink socket (disabled)
Dec 29 13:29:21 HAL-9000 kernel: [    0.284646] type=2000 audit(1293629356.284:1): initialized
Dec 29 13:29:21 HAL-9000 kernel: [    0.293411] highmem bounce pool size: 64 pages
Dec 29 13:29:21 HAL-9000 kernel: [    0.293415] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 29 13:29:21 HAL-9000 kernel: [    0.294553] VFS: Disk quotas dquot_6.5.2
Dec 29 13:29:21 HAL-9000 kernel: [    0.294600] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 29 13:29:21 HAL-9000 kernel: [    0.295044] fuse init (API version 7.13)
Dec 29 13:29:21 HAL-9000 kernel: [    0.295111] msgmni has been set to 1615
Dec 29 13:29:21 HAL-9000 kernel: [    0.295293] alg: No test for stdrng (krng)
Dec 29 13:29:21 HAL-9000 kernel: [    0.295338] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 29 13:29:21 HAL-9000 kernel: [    0.295341] io scheduler noop registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.295342] io scheduler anticipatory registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.295344] io scheduler deadline registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.295376] io scheduler cfq registered (default)
Dec 29 13:29:21 HAL-9000 kernel: [    0.295675] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 29 13:29:21 HAL-9000 kernel: [    0.295695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 29 13:29:21 HAL-9000 kernel: [    0.295782] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 29 13:29:21 HAL-9000 kernel: [    0.295785] ACPI: Power Button [PWRB]
Dec 29 13:29:21 HAL-9000 kernel: [    0.295837] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 29 13:29:21 HAL-9000 kernel: [    0.295840] ACPI: Power Button [PWRF]
Dec 29 13:29:21 HAL-9000 kernel: [    0.295883] fan PNP0C0B:00: registered as cooling_device0
Dec 29 13:29:21 HAL-9000 kernel: [    0.295887] ACPI: Fan [FAN] (on)
Dec 29 13:29:21 HAL-9000 kernel: [    0.296212] processor LNXCPU:00: registered as cooling_device1
Dec 29 13:29:21 HAL-9000 kernel: [    0.296243] processor LNXCPU:01: registered as cooling_device2
Dec 29 13:29:21 HAL-9000 kernel: [    0.300204] thermal LNXTHERM:01: registered as thermal_zone0
Dec 29 13:29:21 HAL-9000 kernel: [    0.300210] ACPI: Thermal Zone [THRM] (31 C)
Dec 29 13:29:21 HAL-9000 kernel: [    0.300466] isapnp: Scanning for PnP cards...
Dec 29 13:29:21 HAL-9000 kernel: [    0.301499] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.301591] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 29 13:29:21 HAL-9000 kernel: [    0.301854] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 29 13:29:21 HAL-9000 kernel: [    0.302732] brd: module loaded
Dec 29 13:29:21 HAL-9000 kernel: [    0.303112] loop: module loaded
Dec 29 13:29:21 HAL-9000 kernel: [    0.303196] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 29 13:29:21 HAL-9000 kernel: [    0.303650] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Dec 29 13:29:21 HAL-9000 kernel: [    0.303665] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Dec 29 13:29:21 HAL-9000 kernel: [    0.303685] pata_acpi 0000:00:08.0: PCI INT A disabled
Dec 29 13:29:21 HAL-9000 kernel: [    0.303939] Fixed MDIO Bus: probed
Dec 29 13:29:21 HAL-9000 kernel: [    0.303966] PPP generic driver version 2.4.2
Dec 29 13:29:21 HAL-9000 kernel: [    0.303993] tun: Universal TUN/TAP device driver, 1.6
Dec 29 13:29:21 HAL-9000 kernel: [    0.303995] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 29 13:29:21 HAL-9000 kernel: [    0.304097] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 29 13:29:21 HAL-9000 kernel: [    0.304336] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Dec 29 13:29:21 HAL-9000 kernel: [    0.304347] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Dec 29 13:29:21 HAL-9000 kernel: [    0.304363] ehci_hcd 0000:00:02.1: EHCI Host Controller
Dec 29 13:29:21 HAL-9000 kernel: [    0.304390] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.304410] ehci_hcd 0000:00:02.1: debug port 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.304436] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
Dec 29 13:29:21 HAL-9000 kernel: [    0.316039] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Dec 29 13:29:21 HAL-9000 kernel: [    0.316140] usb usb1: configuration #1 chosen from 1 choice
Dec 29 13:29:21 HAL-9000 kernel: [    0.316165] hub 1-0:1.0: USB hub found
Dec 29 13:29:21 HAL-9000 kernel: [    0.316174] hub 1-0:1.0: 8 ports detected
Dec 29 13:29:21 HAL-9000 kernel: [    0.316232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 29 13:29:21 HAL-9000 kernel: [    0.316520] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Dec 29 13:29:21 HAL-9000 kernel: [    0.316536] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Dec 29 13:29:21 HAL-9000 kernel: [    0.316554] ohci_hcd 0000:00:02.0: OHCI Host Controller
Dec 29 13:29:21 HAL-9000 kernel: [    0.316586] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Dec 29 13:29:21 HAL-9000 kernel: [    0.316614] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Dec 29 13:29:21 HAL-9000 kernel: [    0.359678] Freeing initrd memory: 7994k freed
Dec 29 13:29:21 HAL-9000 kernel: [    0.374116] usb usb2: configuration #1 chosen from 1 choice
Dec 29 13:29:21 HAL-9000 kernel: [    0.374142] hub 2-0:1.0: USB hub found
Dec 29 13:29:21 HAL-9000 kernel: [    0.374156] hub 2-0:1.0: 8 ports detected
Dec 29 13:29:21 HAL-9000 kernel: [    0.374215] uhci_hcd: USB Universal Host Controller Interface driver
Dec 29 13:29:21 HAL-9000 kernel: [    0.374297] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 29 13:29:21 HAL-9000 kernel: [    0.374713] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.374720] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 29 13:29:21 HAL-9000 kernel: [    0.374824] mice: PS/2 mouse device common for all mice
Dec 29 13:29:21 HAL-9000 kernel: [    0.374926] rtc_cmos 00:04: RTC can wake from S4
Dec 29 13:29:21 HAL-9000 kernel: [    0.374966] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Dec 29 13:29:21 HAL-9000 kernel: [    0.374998] rtc0: alarms up to one year, y3k, 242 bytes nvram
Dec 29 13:29:21 HAL-9000 kernel: [    0.375079] device-mapper: uevent: version 1.0.3
Dec 29 13:29:21 HAL-9000 kernel: [    0.375177] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Dec 29 13:29:21 HAL-9000 kernel: [    0.375242] device-mapper: multipath: version 1.1.0 loaded
Dec 29 13:29:21 HAL-9000 kernel: [    0.375245] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 29 13:29:21 HAL-9000 kernel: [    0.375335] EISA: Probing bus 0 at eisa.0
Dec 29 13:29:21 HAL-9000 kernel: [    0.375340] Cannot allocate resource for EISA slot 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.375343] Cannot allocate resource for EISA slot 2
Dec 29 13:29:21 HAL-9000 kernel: [    0.375359] EISA: Detected 0 cards.
Dec 29 13:29:21 HAL-9000 kernel: [    0.375422] cpuidle: using governor ladder
Dec 29 13:29:21 HAL-9000 kernel: [    0.375424] cpuidle: using governor menu
Dec 29 13:29:21 HAL-9000 kernel: [    0.375815] TCP cubic registered
Dec 29 13:29:21 HAL-9000 kernel: [    0.375937] NET: Registered protocol family 10
Dec 29 13:29:21 HAL-9000 kernel: [    0.376331] lo: Disabled Privacy Extensions
Dec 29 13:29:21 HAL-9000 kernel: [    0.376603] NET: Registered protocol family 17
Dec 29 13:29:21 HAL-9000 kernel: [    0.376632] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (2 cpu cores) (version 2.20.00)
Dec 29 13:29:21 HAL-9000 kernel: [    0.376673] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x8
Dec 29 13:29:21 HAL-9000 kernel: [    0.376675] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xa
Dec 29 13:29:21 HAL-9000 kernel: [    0.376678] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xc
Dec 29 13:29:21 HAL-9000 kernel: [    0.376680] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe
Dec 29 13:29:21 HAL-9000 kernel: [    0.376682] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
Dec 29 13:29:21 HAL-9000 kernel: [    0.376716] Using IPI No-Shortcut mode
Dec 29 13:29:21 HAL-9000 kernel: [    0.376792] registered taskstats version 1
Dec 29 13:29:21 HAL-9000 kernel: [    0.377027]   Magic number: 6:521:484
Dec 29 13:29:21 HAL-9000 kernel: [    0.377113] rtc_cmos 00:04: setting system clock to 2010-12-29 13:29:16 UTC (1293629356)
Dec 29 13:29:21 HAL-9000 kernel: [    0.377116] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 29 13:29:21 HAL-9000 kernel: [    0.377118] EDD information not available.
Dec 29 13:29:21 HAL-9000 kernel: [    0.398153] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Dec 29 13:29:21 HAL-9000 kernel: [    0.653164] isapnp: No Plug & Play device found
Dec 29 13:29:21 HAL-9000 kernel: [    0.653183] Freeing unused kernel memory: 672k freed
Dec 29 13:29:21 HAL-9000 kernel: [    0.653588] Write protecting the kernel text: 4836k
Dec 29 13:29:21 HAL-9000 kernel: [    0.653649] Write protecting the kernel read-only data: 1884k
Dec 29 13:29:21 HAL-9000 kernel: [    0.669686] udev: starting version 151
Dec 29 13:29:21 HAL-9000 kernel: [    0.711253] md: linear personality registered for level -1
Dec 29 13:29:21 HAL-9000 kernel: [    0.746819] scsi0 : pata_amd
Dec 29 13:29:21 HAL-9000 kernel: [    0.756913] md: multipath personality registered for level -4
Dec 29 13:29:21 HAL-9000 kernel: [    0.760156] scsi1 : pata_amd
Dec 29 13:29:21 HAL-9000 kernel: [    0.760723] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Dec 29 13:29:21 HAL-9000 kernel: [    0.760726] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Dec 29 13:29:21 HAL-9000 kernel: [    0.760879] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Dec 29 13:29:21 HAL-9000 kernel: [    0.770441] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Dec 29 13:29:21 HAL-9000 kernel: [    0.770464] 8139cp 0000:01:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Dec 29 13:29:21 HAL-9000 kernel: [    0.773497] scsi2 : sata_nv
Dec 29 13:29:21 HAL-9000 kernel: [    0.774249] scsi3 : sata_nv
Dec 29 13:29:21 HAL-9000 kernel: [    0.774433] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 23
Dec 29 13:29:21 HAL-9000 kernel: [    0.774436] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 23
Dec 29 13:29:21 HAL-9000 kernel: [    0.776439] md: raid0 personality registered for level 0
Dec 29 13:29:21 HAL-9000 kernel: [    0.791922] FDC 0 is a post-1991 82077
Dec 29 13:29:21 HAL-9000 kernel: [    1.044306] ata1.01: ATAPI: LITE-ON DVDRW LDW-811S, HS06, max UDMA/33
Dec 29 13:29:21 HAL-9000 kernel: [    1.060253] ata1.01: configured for UDMA/33
Dec 29 13:29:21 HAL-9000 kernel: [    1.061144] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW LDW-811S   HS06 PQ: 0 ANSI: 5
Dec 29 13:29:21 HAL-9000 kernel: [    1.064918] sr0: scsi3-mmc drive: 94x/40x writer cd/rw xa/form2 cdda tray
Dec 29 13:29:21 HAL-9000 kernel: [    1.064921] Uniform CD-ROM driver Revision: 3.20
Dec 29 13:29:21 HAL-9000 kernel: [    1.065084] sr 0:0:1:0: Attached scsi generic sg0 type 5
Dec 29 13:29:21 HAL-9000 kernel: [    1.240041] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 29 13:29:21 HAL-9000 kernel: [    1.248207] ata3.00: ATA-8: Patriot Zephyr 128GB SSD, 02.10104, max UDMA/133
Dec 29 13:29:21 HAL-9000 kernel: [    1.248210] ata3.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 29 13:29:21 HAL-9000 kernel: [    1.256219] ata3.00: configured for UDMA/133
Dec 29 13:29:21 HAL-9000 kernel: [    1.256323] scsi 2:0:0:0: Direct-Access     ATA      Patriot Zephyr 1 02.1 PQ: 0 ANSI: 5
Dec 29 13:29:21 HAL-9000 kernel: [    1.256460] sd 2:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
Dec 29 13:29:21 HAL-9000 kernel: [    1.256474] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec 29 13:29:21 HAL-9000 kernel: [    1.256498] sd 2:0:0:0: [sda] Write Protect is off
Dec 29 13:29:21 HAL-9000 kernel: [    1.256525] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 29 13:29:21 HAL-9000 kernel: [    1.256697]  sda: sda1 sda2 < sda5 > sda3
Dec 29 13:29:21 HAL-9000 kernel: [    1.257506] sd 2:0:0:0: [sda] Attached SCSI disk
Dec 29 13:29:21 HAL-9000 kernel: [    1.724041] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 29 13:29:21 HAL-9000 kernel: [    1.732230] ata4.00: ATA-7: WDC WD800JD-00MSA1, 10.01E01, max UDMA/133
Dec 29 13:29:21 HAL-9000 kernel: [    1.732233] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 29 13:29:21 HAL-9000 kernel: [    1.740241] ata4.00: configured for UDMA/133
Dec 29 13:29:21 HAL-9000 kernel: [    1.740314] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-00MS 10.0 PQ: 0 ANSI: 5
Dec 29 13:29:21 HAL-9000 kernel: [    1.740426] sd 3:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Dec 29 13:29:21 HAL-9000 kernel: [    1.740466] sd 3:0:0:0: [sdb] Write Protect is off
Dec 29 13:29:21 HAL-9000 kernel: [    1.740487] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 29 13:29:21 HAL-9000 kernel: [    1.740521] sd 3:0:0:0: Attached scsi generic sg2 type 0
Dec 29 13:29:21 HAL-9000 kernel: [    1.740618]  sdb: sdb1 sdb3 sdb4
Dec 29 13:29:21 HAL-9000 kernel: [    1.755012] sd 3:0:0:0: [sdb] Attached SCSI disk
Dec 29 13:29:21 HAL-9000 kernel: [    1.759342] 8139too Fast Ethernet driver 0.9.28
Dec 29 13:29:21 HAL-9000 kernel: [    1.759662] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Dec 29 13:29:21 HAL-9000 kernel: [    1.759679] 8139too 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Dec 29 13:29:21 HAL-9000 kernel: [    1.760631] eth0: RealTek RTL8139 at 0xcc00, 00:18:37:00:cc:73, IRQ 18
Dec 29 13:29:21 HAL-9000 kernel: [    1.765874] md: raid1 personality registered for level 1
Dec 29 13:29:21 HAL-9000 kernel: [    1.768717] async_tx: api initialized (async)
Dec 29 13:29:21 HAL-9000 kernel: [    1.769776] xor: automatically using best checksumming function: pIII_sse
Dec 29 13:29:21 HAL-9000 kernel: [    1.788018]    pIII_sse  :  7300.000 MB/sec
Dec 29 13:29:21 HAL-9000 kernel: [    1.788021] xor: using function: pIII_sse (7300.000 MB/sec)
Dec 29 13:29:21 HAL-9000 kernel: [    1.856012] raid6: int32x1   1072 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    1.924055] raid6: int32x2   1060 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    1.992039] raid6: int32x4    670 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.060076] raid6: int32x8    512 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.128032] raid6: mmxx1     2002 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.196006] raid6: mmxx2     3618 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.264025] raid6: sse1x1    1947 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.332017] raid6: sse1x2    3162 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.400014] raid6: sse2x1    3274 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.468012] raid6: sse2x2    4246 MB/s
Dec 29 13:29:21 HAL-9000 kernel: [    2.468013] raid6: using algorithm sse2x2 (4246 MB/s)
Dec 29 13:29:21 HAL-9000 kernel: [    2.473199] md: raid6 personality registered for level 6
Dec 29 13:29:21 HAL-9000 kernel: [    2.473202] md: raid5 personality registered for level 5
Dec 29 13:29:21 HAL-9000 kernel: [    2.473204] md: raid4 personality registered for level 4
Dec 29 13:29:21 HAL-9000 kernel: [    2.480177] md: raid10 personality registered for level 10
Dec 29 13:29:21 HAL-9000 kernel: [    2.497676] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Dec 29 13:29:21 HAL-9000 kernel: [    2.497681] EXT4-fs (sda1): write access will be enabled during recovery
Dec 29 13:29:21 HAL-9000 kernel: [    2.593382] EXT4-fs (sda1): orphan cleanup on readonly fs
Dec 29 13:29:21 HAL-9000 kernel: [    2.593628] EXT4-fs (sda1): 11 orphan inodes deleted
Dec 29 13:29:21 HAL-9000 kernel: [    2.593631] EXT4-fs (sda1): recovery complete
Dec 29 13:29:21 HAL-9000 kernel: [    3.937306] EXT4-fs (sda1): mounted filesystem with ordered data mode
Dec 29 13:29:21 HAL-9000 kernel: [    4.242552] Adding 9764856k swap on /dev/sda5.  Priority:-1 extents:1 across:9764856k SS
Dec 29 13:29:21 HAL-9000 kernel: [    4.299463] udev: starting version 151
Dec 29 13:29:21 HAL-9000 kernel: [    4.379687] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Dec 29 13:29:21 HAL-9000 kernel: [    4.379708] i2c i2c-1: nForce2 SMBus adapter at 0xf400
Dec 29 13:29:21 HAL-9000 kernel: [    4.383945] vga16fb: mapped to 0xc00a0000
Dec 29 13:29:21 HAL-9000 kernel: [    4.384027] fb0: VGA16 VGA frame buffer device
Dec 29 13:29:21 HAL-9000 kernel: [    4.418695] lp: driver loaded but no devices found
Dec 29 13:29:21 HAL-9000 kernel: [    4.430745] Linux agpgart interface v0.103
Dec 29 13:29:21 HAL-9000 kernel: [    4.456361] type=1505 audit(1293629360.575:2):  operation="profile_load" pid=565 name="/sbin/dhclient3"
Dec 29 13:29:21 HAL-9000 kernel: [    4.456608] type=1505 audit(1293629360.575:3):  operation="profile_load" pid=565 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 29 13:29:21 HAL-9000 kernel: [    4.456747] type=1505 audit(1293629360.575:4):  operation="profile_load" pid=565 name="/usr/lib/connman/scripts/dhclient-script"
Dec 29 13:29:21 HAL-9000 kernel: [    4.587114] nvidia: module license 'NVIDIA' taints kernel.
Dec 29 13:29:21 HAL-9000 kernel: [    4.587117] Disabling lock debugging due to kernel taint
Dec 29 13:29:21 HAL-9000 kernel: [    4.886964] eth0: link up, 100Mbps, half-duplex, lpa 0x40A1
Dec 29 13:29:21 HAL-9000 kernel: [    4.969460] type=1505 audit(1293629361.091:5):  operation="profile_load" pid=797 name="/usr/share/gdm/guest-session/Xsession"
Dec 29 13:29:21 HAL-9000 kernel: [    4.969942] type=1505 audit(1293629361.091:6):  operation="profile_replace" pid=798 name="/sbin/dhclient3"
Dec 29 13:29:21 HAL-9000 kernel: [    4.970200] type=1505 audit(1293629361.091:7):  operation="profile_replace" pid=798 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 29 13:29:21 HAL-9000 kernel: [    4.970871] type=1505 audit(1293629361.091:8):  operation="profile_replace" pid=798 name="/usr/lib/connman/scripts/dhclient-script"
Dec 29 13:29:21 HAL-9000 kernel: [    4.998881] type=1505 audit(1293629361.119:9):  operation="profile_load" pid=799 name="/usr/bin/evince"
Dec 29 13:29:21 HAL-9000 kernel: [    5.006657] type=1505 audit(1293629361.127:10):  operation="profile_load" pid=804 name="/usr/lib/cups/backend/cups-pdf"
Dec 29 13:29:21 HAL-9000 kernel: [    5.499933] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Dec 29 13:29:21 HAL-9000 kernel: [    5.589078] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
Dec 29 13:29:21 HAL-9000 kernel: [    5.589095] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
Dec 29 13:29:21 HAL-9000 kernel: [    5.589098] hda_intel: Disable MSI for Nvidia chipset
Dec 29 13:29:21 HAL-9000 kernel: [    5.592445] parport_pc 00:09: reported by Plug and Play ACPI
Dec 29 13:29:21 HAL-9000 kernel: [    5.592470] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Dec 29 13:29:21 HAL-9000 kernel: [    5.774678] vboxdrv: fAsync=1 offMin=0x1f94da offMax=0x1f94da
Dec 29 13:29:21 HAL-9000 kernel: [    5.775053] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Dec 29 13:29:21 HAL-9000 kernel: [    5.802935] lp0: using parport0 (interrupt-driven).
Dec 29 13:29:21 HAL-9000 kernel: [    5.808277] ppdev: user-space parallel port driver
Dec 29 13:29:21 HAL-9000 kernel: [    5.824198] Console: switching to colour frame buffer device 80x30
Dec 29 13:29:22 HAL-9000 kernel: [    6.341023] hda_codec: ALC662 rev1: BIOS auto-probing.
Dec 29 13:29:22 HAL-9000 kernel: [    6.566441] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
Dec 29 13:29:22 HAL-9000 kernel: [    6.628087] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
Dec 29 13:29:22 HAL-9000 kernel: [    6.832154] nvidia 0000:00:0d.0: enabling device (0000 -> 0002)
Dec 29 13:29:22 HAL-9000 kernel: [    6.832453] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 23
Dec 29 13:29:22 HAL-9000 kernel: [    6.832458] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 23 (level, low) -> IRQ 23
Dec 29 13:29:22 HAL-9000 kernel: [    6.832469] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=none
Dec 29 13:29:22 HAL-9000 kernel: [    6.832900] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
Dec 29 13:29:22 HAL-9000 kernel: [    6.832915] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
Dec 29 13:29:22 HAL-9000 kernel: [    6.832923] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 29 13:29:22 HAL-9000 kernel: [    6.833135] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010


this sort of stuff means nothing to me any advice is appreciated

thansk

---

### Post by teknojunkey on 2010-12-29
i turned the cpu frequency down ... that seems to have fixed it for now
thanks for the help

---

### Post by teknojunkey on 2011-01-03
Im still getting this hang / crash
its not so often but still happens every few hours.

Whats the story with unity ? worth a try or not ?

---

