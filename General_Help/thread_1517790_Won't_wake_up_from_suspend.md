---
title: "Won't wake up from suspend"
date: 2010-06-25
forum: General Help
---

### Post by nbtrap on 2010-06-25
I'm running Linux Mint 9 (aka Ubuntu 10.04 + a couple of tweaks), and my machine won't wake up from suspend. It hasn't done so successfully since Ubuntu 8.04. I'm running the default graphics driver (not the proprietary NVidia one) on a quad-core Gateway FX. How can I go about figuring out the problem?

---

### Post by hal8000 on 2010-06-25
One place to check in /var/log/messages
Check that you have latest update for your laptop also, you may have to pass a boot parameter to grub.
Also have a read here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by nbtrap on 2010-06-25
Thanks, I'll take a look. Also, I'm running a desktop.

---

### Post by hal8000 on 2010-06-25
Have a look through the repos for all acpi and apm software and laptop packages. As its a desktop, you may be lacking some acpi feature that prevents suspend.

Personally Ubuntu 9.10 and 10.04 boot that quick about 20secs on my Intel P4 2.8GHz that I never bother with suspend (not on the dekstop machine) anyway.
If it doesnt wake from suspend, how do you get the computer to start?

Just one more thing, check in your Computer Bios, my Asus motherboard has some Power suspend and boot options, 1 including whether to use case switch,
or keyboard or mouse button to boot. My computer is about 6 years old, so things have moved on now.
HTH

---

### Post by nbtrap on 2010-06-25
To get the computer to start, I have to power off manually (hold down the power button). What's strange is when I do that, the next time I turn the computer on, the OS doesn't automatically connect to the internet, so I have to run:

```

sudo /etc/init.d/network-manager restart

```

---

### Post by nbtrap on 2010-06-25
Here's my /var/log/messages after erasing it and suspending:

```

Jun 25 16:19:14 Nathan-Linux kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 25 16:19:14 Nathan-Linux rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="867" x-info="http://www.rsyslog.com"] (re)start
Jun 25 16:19:14 Nathan-Linux rsyslogd: rsyslogd's groupid changed to 103
Jun 25 16:19:14 Nathan-Linux rsyslogd: rsyslogd's userid changed to 101
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] KERNEL supported cpus:
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   Intel GenuineIntel
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   AMD AuthenticAMD
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   NSC Geode by NSC
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   Cyrix CyrixInstead
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   Centaur CentaurHauls
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   UMC UMC UMC UMC
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfa59000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfa59000 - 00000000cfa5b000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfa5b000 - 00000000cfb29000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfb29000 - 00000000cfbe9000 (ACPI NVS)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfbe9000 - 00000000cfbf2000 (ACPI data)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfbf2000 - 00000000cfbf3000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfbf3000 - 00000000cfbff000 (ACPI data)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfbff000 - 00000000cfc00000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000cfc00000 - 00000000d0000000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000012c000000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] DMI 2.4 present.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] last_pfn = 0xcfc00 max_arch_pfn = 0x100000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] modified physical RAM map:
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfa59000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfa59000 - 00000000cfa5b000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfa5b000 - 00000000cfb29000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfb29000 - 00000000cfbe9000 (ACPI NVS)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfbe9000 - 00000000cfbf2000 (ACPI data)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfbf2000 - 00000000cfbf3000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfbf3000 - 00000000cfbff000 (ACPI data)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfbff000 - 00000000cfc00000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000cfc00000 - 00000000d0000000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f8000000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]  modified: 0000000100000000 - 000000012c000000 (usable)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] RAMDISK: 372db000 - 37fefa12
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Allocated new RAMDISK: 008de000 - 015f2a12
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Move RAMDISK from 00000000372db000 - 0000000037fefa11 to 008de000 - 015f2a11
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: RSDP 000fe020 00014 (v00 GATEWA)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: RSDT cfbfd038 00060 (v01 GATEWA SYSTEM   00000130      01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: FACP cfbfc000 00074 (v01 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: DSDT cfbf8000 03A83 (v01 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: FACS cfb9e000 00040
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: APIC cfbf7000 00078 (v01 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: WDDT cfbf6000 00040 (v01 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: MCFG cfbf5000 0003C (v01 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: ASF! cfbf4000 000A6 (v32 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SLIC cfbf3000 00176 (v01 GATEWA SYSTEM   00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbf1000 00204 (v01 GATEWA    CpuPm 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbf0000 00175 (v01 GATEWA  Cpu0Ist 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbef000 00175 (v01 GATEWA  Cpu1Ist 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbee000 00175 (v01 GATEWA  Cpu2Ist 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbed000 00175 (v01 GATEWA  Cpu3Ist 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbec000 000DD (v01 GATEWA  Cpu0Cst 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbeb000 000DD (v01 GATEWA  Cpu1Cst 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbea000 000DD (v01 GATEWA  Cpu2Cst 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: SSDT cfbe9000 000DD (v01 GATEWA  Cpu3Cst 00000130 MSFT 01000013)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] 2436MB HIGHMEM available.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] 887MB LOWMEM available.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   low ram: 0 - 377fe000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #5 [00008da000 - 00008dd15e]              BRK ==> [00008da000 - 00008dd15e]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #7 [00008de000 - 00015f2a12]      NEW RAMDISK ==> [00008de000 - 00015f2a12]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] found SMP MP-table at [c00fe200] fe200
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Zone PFN ranges:
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]   HighMem  0x000377fe -> 0x000cfc00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Movable zone start PFN for each node
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] early_node_map[6] active PFN ranges
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     0: 0x00000006 -> 0x0000009e
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     0: 0x00000100 -> 0x000cfa59
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     0: 0x000cfa5b -> 0x000cfb29
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     0: 0x000cfbf2 -> 0x000cfbf3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     0: 0x000cfbff -> 0x000cfc00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Using APIC driver default
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:20000000)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36024 r0 d21320 u1048576
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 843978
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=94dc042e-eb2f-4f98-9c0c-5407290de0df ro quiet splash
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Initializing CPU#0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] allocated 17018880 bytes of page_cgroup
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000cfc00)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Memory: 3335592k/3403776k available (4673k kernel code, 65780k reserved, 2121k data, 656k init, 2493612k highmem)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] virtual kernel memory layout:
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590663   (4673 kB)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Hierarchical RCU implementation.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] console [tty0] enabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Fast TSC calibration using PIT
Jun 25 16:19:14 Nathan-Linux kernel: [    0.000000] Detected 2499.632 MHz processor.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.26 BogoMIPS (lpj=9998528)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008018] Security Framework initialized
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008037] AppArmor: AppArmor initialized
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008042] Mount-cache hash table entries: 512
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008146] Initializing cgroup subsys ns
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008150] Initializing cgroup subsys cpuacct
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008154] Initializing cgroup subsys memory
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008159] Initializing cgroup subsys devices
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008161] Initializing cgroup subsys freezer
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008163] Initializing cgroup subsys net_cls
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008179] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008181] CPU: L2 cache: 3072K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008184] CPU: Physical Processor ID: 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008185] CPU: Processor Core ID: 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008188] mce: CPU supports 6 MCE banks
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008196] CPU0: Thermal monitoring enabled (TM2)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008198] using mwait in idle threads.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008204] Performance Events: Core2 events, Intel PMU driver.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008211] ... version:                2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008212] ... bit width:              40
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008214] ... generic registers:      2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008215] ... value mask:             000000ffffffffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008217] ... max period:             000000007fffffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008218] ... fixed-purpose events:   3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008220] ... event mask:             0000000700000003
Jun 25 16:19:14 Nathan-Linux kernel: [    0.008223] Checking 'hlt' instruction... OK.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.026407] ACPI: Core revision 20090903
Jun 25 16:19:14 Nathan-Linux kernel: [    0.033512] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.033517] ftrace: allocating 21771 entries in 43 pages
Jun 25 16:19:14 Nathan-Linux kernel: [    0.036044] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 25 16:19:14 Nathan-Linux kernel: [    0.036342] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.077687] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jun 25 16:19:14 Nathan-Linux kernel: [    0.080001] Booting processor 1 APIC 0x2 ip 0x6000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] Initializing CPU#1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: L2 cache: 3072K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: Physical Processor ID: 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: Processor Core ID: 2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU1: Thermal monitoring enabled (TM2)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.164067] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jun 25 16:19:14 Nathan-Linux kernel: [    0.164077] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.168065] Booting processor 2 APIC 0x1 ip 0x6000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] Initializing CPU#2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: L2 cache: 3072K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: Physical Processor ID: 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: Processor Core ID: 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU2: Thermal monitoring enabled (TM2)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.256078] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jun 25 16:19:14 Nathan-Linux kernel: [    0.256090] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.260094] Booting processor 3 APIC 0x3 ip 0x6000
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] Initializing CPU#3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: L2 cache: 3072K
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: Physical Processor ID: 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU: Processor Core ID: 3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.012000] CPU3: Thermal monitoring enabled (TM2)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.348120] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
Jun 25 16:19:14 Nathan-Linux kernel: [    0.348130] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.352014] Brought up 4 CPUs
Jun 25 16:19:14 Nathan-Linux kernel: [    0.352016] Total of 4 processors activated (19694.93 BogoMIPS).
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] devtmpfs: initialized
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] regulator: core version 0.5
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] Time: 20:19:02  Date: 06/25/10
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] NET: Registered protocol family 16
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] EISA bus registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] Trying to unpack rootfs image as initramfs...
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] ACPI: bus type pci registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] PCI: MCFG area at f0000000 reserved in E820
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] PCI: Using MMCONFIG for extended config space
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] PCI: Using configuration type 1 for base access
Jun 25 16:19:14 Nathan-Linux kernel: [    0.353995] bio: create slab <bio-0> at 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.358848] ACPI: Interpreter enabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.358854] ACPI: (supports S0 S1 S3 S4 S5)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.358872] ACPI: Using IOAPIC for interrupt routing
Jun 25 16:19:14 Nathan-Linux kernel: [    0.362243] ACPI: No dock devices found.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363013] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363098] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363101] pci 0000:00:01.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363152] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363155] pci 0000:00:03.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363257] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363260] pci 0000:00:19.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363533] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363537] pci 0000:00:1a.7: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363608] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363611] pci 0000:00:1b.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363664] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363668] pci 0000:00:1c.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363722] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363725] pci 0000:00:1c.1: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363780] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363783] pci 0000:00:1c.2: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363838] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363841] pci 0000:00:1c.3: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363896] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.363899] pci 0000:00:1c.4: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364189] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364193] pci 0000:00:1d.7: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364308] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364312] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364315] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364318] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0810 (mask 007f)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364425] pci 0000:00:1f.2: PME# supported from D3hot
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364428] pci 0000:00:1f.2: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364842] pci 0000:07:00.0: PME# supported from D3hot D3cold
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364845] pci 0000:07:00.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364994] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
Jun 25 16:19:14 Nathan-Linux kernel: [    0.364997] pci 0000:07:03.0: PME# disabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.365034] pci 0000:00:1e.0: transparent bridge
Jun 25 16:19:14 Nathan-Linux kernel: [    0.370647] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.370731] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.370812] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.370893] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.370974] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371055] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371135] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371217] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371314] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371317] vgaarb: loaded
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371407] SCSI subsystem initialized
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] usbcore: registered new interface driver usbfs
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] usbcore: registered new interface driver hub
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] usbcore: registered new device driver usb
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] ACPI: WMI: Mapper loaded
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] PCI: Using ACPI for IRQ routing
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] NetLabel: Initializing
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] NetLabel:  domain hash size = 128
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 25 16:19:14 Nathan-Linux kernel: [    0.371416] NetLabel:  unlabeled traffic allowed by default
Jun 25 16:19:14 Nathan-Linux kernel: [    0.372002] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jun 25 16:19:14 Nathan-Linux kernel: [    0.372002] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.372002] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jun 25 16:19:14 Nathan-Linux kernel: [    0.380141] Switching to clocksource tsc
Jun 25 16:19:14 Nathan-Linux kernel: [    0.382033] AppArmor: AppArmor Filesystem Enabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.382040] pnp: PnP ACPI init
Jun 25 16:19:14 Nathan-Linux kernel: [    0.382049] ACPI: bus type pnp registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383755] pnp: PnP ACPI: found 10 devices
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383757] ACPI: ACPI bus type pnp unregistered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383760] PnPBIOS: Disabled by ACPI PNP
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383768] system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383771] system 00:01: iomem range 0xfeb00000-0xfeb03fff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383773] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383776] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383778] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383780] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383782] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383785] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383787] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383789] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383792] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383794] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383800] system 00:06: ioport range 0x500-0x53f has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383802] system 00:06: ioport range 0x400-0x47f has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.383805] system 00:06: ioport range 0x680-0x6ff has been reserved
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418481] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418484] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418486] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418489] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe2ffffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418492] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418496] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418499] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418503] pci 0000:00:1c.0:   MEM window: 0xe3200000-0xe33fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418507] pci 0000:00:1c.0:   PREFETCH window: 0x000000e3400000-0x000000e35fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418512] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418515] pci 0000:00:1c.1:   IO window: 0x5000-0x5fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418520] pci 0000:00:1c.1:   MEM window: 0xe3600000-0xe37fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418523] pci 0000:00:1c.1:   PREFETCH window: 0x000000e3800000-0x000000e39fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418528] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418531] pci 0000:00:1c.2:   IO window: 0x6000-0x6fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418535] pci 0000:00:1c.2:   MEM window: 0xe3a00000-0xe3bfffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418538] pci 0000:00:1c.2:   PREFETCH window: 0x000000e3c00000-0x000000e3dfffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418543] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418546] pci 0000:00:1c.3:   IO window: 0x7000-0x7fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418550] pci 0000:00:1c.3:   MEM window: 0xe3e00000-0xe3ffffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418554] pci 0000:00:1c.3:   PREFETCH window: 0x000000e4000000-0x000000e41fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418559] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418561] pci 0000:00:1c.4:   IO window: 0x8000-0x8fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418565] pci 0000:00:1c.4:   MEM window: 0xe4200000-0xe43fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418569] pci 0000:00:1c.4:   PREFETCH window: 0x000000e4400000-0x000000e45fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418574] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418577] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418581] pci 0000:00:1e.0:   MEM window: 0xe3000000-0xe30fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418584] pci 0000:00:1e.0:   PREFETCH window: 0xe4600000-0xe46fffff
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418603] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418612] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418619] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418629] pci 0000:00:1c.1: enabling device (0000 -> 0003)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418636] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418647] pci 0000:00:1c.2: enabling device (0000 -> 0003)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418653] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418664] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418670] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418680] pci 0000:00:1c.4: enabling device (0000 -> 0003)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418683] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418770] NET: Registered protocol family 2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.418842] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.419075] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.419403] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.419565] TCP: Hash tables configured (established 131072 bind 65536)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.419566] TCP reno registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.419626] NET: Registered protocol family 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.420182] cpufreq-nforce2: No nForce2 chipset.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.420203] Scanning for low memory corruption every 60 seconds
Jun 25 16:19:14 Nathan-Linux kernel: [    0.420287] audit: initializing netlink socket (disabled)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.420294] type=2000 audit(1277497142.419:1): initialized
Jun 25 16:19:14 Nathan-Linux kernel: [    0.428396] highmem bounce pool size: 64 pages
Jun 25 16:19:14 Nathan-Linux kernel: [    0.428401] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun 25 16:19:14 Nathan-Linux kernel: [    0.429694] VFS: Disk quotas dquot_6.5.2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.429752] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430232] fuse init (API version 7.13)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430315] msgmni has been set to 1646
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430568] alg: No test for stdrng (krng)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430625] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430628] io scheduler noop registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430630] io scheduler anticipatory registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430632] io scheduler deadline registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.430671] io scheduler cfq registered (default)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431406] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431499] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431573] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431580] ACPI: Sleep Button [SLPB]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431624] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431626] ACPI: Power Button [PWRF]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.431950] processor LNXCPU:00: registered as cooling_device0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.432098] processor LNXCPU:01: registered as cooling_device1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.432533] processor LNXCPU:02: registered as cooling_device2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.432752] processor LNXCPU:03: registered as cooling_device3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.435375] isapnp: Scanning for PnP cards...
Jun 25 16:19:14 Nathan-Linux kernel: [    0.435466] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 25 16:19:14 Nathan-Linux kernel: [    0.435594] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
Jun 25 16:19:14 Nathan-Linux kernel: [    0.436843] brd: module loaded
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437305] loop: module loaded
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437383] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437794] Fixed MDIO Bus: probed
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437827] PPP generic driver version 2.4.2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437863] tun: Universal TUN/TAP device driver, 1.6
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437865] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437942] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437964] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 17 (level, low) -> IRQ 17
Jun 25 16:19:14 Nathan-Linux kernel: [    0.437985] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.438015] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.438039] ehci_hcd 0000:00:1a.7: debug port 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.441948] ehci_hcd 0000:00:1a.7: irq 17, io mem 0xe3125c00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455490] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455593] usb usb1: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455623] hub 1-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455631] hub 1-0:1.0: 6 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455703] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455723] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455757] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.455785] ehci_hcd 0000:00:1d.7: debug port 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.459693] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe3125800
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475493] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475594] usb usb2: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475627] hub 2-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475635] hub 2-0:1.0: 6 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475696] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475716] uhci_hcd: USB Universal Host Controller Interface driver
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475755] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475766] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475803] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475834] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000030e0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475918] usb usb3: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475948] hub 3-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.475954] hub 3-0:1.0: 2 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476004] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476013] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476042] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476069] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030c0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476154] usb usb4: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476179] hub 4-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476186] hub 4-0:1.0: 2 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476226] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476234] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476265] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476286] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000030a0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476367] usb usb5: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476391] hub 5-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476397] hub 5-0:1.0: 2 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476439] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476448] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476481] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476502] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476582] usb usb6: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476607] hub 6-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476613] hub 6-0:1.0: 2 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476654] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476663] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476692] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476720] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476804] usb usb7: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476828] hub 7-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476834] hub 7-0:1.0: 2 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476876] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476884] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476913] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jun 25 16:19:14 Nathan-Linux kernel: [    0.476934] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
Jun 25 16:19:14 Nathan-Linux kernel: [    0.477017] usb usb8: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.477041] hub 8-0:1.0: USB hub found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.477047] hub 8-0:1.0: 2 ports detected
Jun 25 16:19:14 Nathan-Linux kernel: [    0.477136] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480255] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480263] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480342] mice: PS/2 mouse device common for all mice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480442] rtc_cmos 00:03: RTC can wake from S4
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480480] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480503] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480609] device-mapper: uevent: version 1.0.3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480721] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480835] device-mapper: multipath: version 1.1.0 loaded
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480838] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480944] EISA: Probing bus 0 at eisa.0
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480948] Cannot allocate resource for EISA slot 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480950] Cannot allocate resource for EISA slot 2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480952] Cannot allocate resource for EISA slot 3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480955] Cannot allocate resource for EISA slot 4
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480957] Cannot allocate resource for EISA slot 5
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480959] Cannot allocate resource for EISA slot 6
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480961] Cannot allocate resource for EISA slot 7
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480963] Cannot allocate resource for EISA slot 8
Jun 25 16:19:14 Nathan-Linux kernel: [    0.480965] EISA: Detected 0 cards.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.481124] cpuidle: using governor ladder
Jun 25 16:19:14 Nathan-Linux kernel: [    0.481126] cpuidle: using governor menu
Jun 25 16:19:14 Nathan-Linux kernel: [    0.481568] TCP cubic registered
Jun 25 16:19:14 Nathan-Linux kernel: [    0.481721] NET: Registered protocol family 10
Jun 25 16:19:14 Nathan-Linux kernel: [    0.482183] lo: Disabled Privacy Extensions
Jun 25 16:19:14 Nathan-Linux kernel: [    0.482519] NET: Registered protocol family 17
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483029] Using IPI No-Shortcut mode
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483098] registered taskstats version 1
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483473]   Magic number: 14:272:347
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483511]  pci0000:00: hash matches
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483544] rtc_cmos 00:03: setting system clock to 2010-06-25 20:19:02 UTC (1277497142)
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483546] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.483548] EDD information not available.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.505051] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jun 25 16:19:14 Nathan-Linux kernel: [    0.640656] Freeing initrd memory: 13394k freed
Jun 25 16:19:14 Nathan-Linux kernel: [    0.767479] usb 1-4: new high speed USB device using ehci_hcd and address 2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.788251] isapnp: No Plug & Play device found
Jun 25 16:19:14 Nathan-Linux kernel: [    0.788280] Freeing unused kernel memory: 656k freed
Jun 25 16:19:14 Nathan-Linux kernel: [    0.788606] Write protecting the kernel text: 4676k
Jun 25 16:19:14 Nathan-Linux kernel: [    0.788650] Write protecting the kernel read-only data: 1840k
Jun 25 16:19:14 Nathan-Linux kernel: [    0.803983] udev: starting version 151
Jun 25 16:19:14 Nathan-Linux kernel: [    0.825003] Linux agpgart interface v0.103
Jun 25 16:19:14 Nathan-Linux kernel: [    0.833385] ahci 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jun 25 16:19:14 Nathan-Linux kernel: [    0.833517] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Jun 25 16:19:14 Nathan-Linux kernel: [    0.833520] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ccc ems 
Jun 25 16:19:14 Nathan-Linux kernel: [    0.854229] [drm] Initialized drm 1.1.0 20060810
Jun 25 16:19:14 Nathan-Linux kernel: [    0.856973] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Jun 25 16:19:14 Nathan-Linux kernel: [    0.856975] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.867139] pata_it821x 0000:07:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 25 16:19:14 Nathan-Linux kernel: [    0.867143] pata_it821x: controller in pass through mode.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.867225] scsi0 : pata_it821x
Jun 25 16:19:14 Nathan-Linux kernel: [    0.867326] scsi1 : pata_it821x
Jun 25 16:19:14 Nathan-Linux kernel: [    0.867357] ata1: PATA max UDMA/133 cmd 0x1018 ctl 0x102c bmdma 0x1000 irq 18
Jun 25 16:19:14 Nathan-Linux kernel: [    0.867359] ata2: PATA max UDMA/133 cmd 0x1010 ctl 0x1028 bmdma 0x1008 irq 18
Jun 25 16:19:14 Nathan-Linux kernel: [    0.872961] ohci1394 0000:07:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 25 16:19:14 Nathan-Linux kernel: [    0.879558] scsi2 : ahci
Jun 25 16:19:14 Nathan-Linux kernel: [    0.879652] scsi3 : ahci
Jun 25 16:19:14 Nathan-Linux kernel: [    0.879736] scsi4 : ahci
Jun 25 16:19:14 Nathan-Linux kernel: [    0.879816] scsi5 : ahci
Jun 25 16:19:14 Nathan-Linux kernel: [    0.879900] scsi6 : ahci
Jun 25 16:19:14 Nathan-Linux kernel: [    0.879970] scsi7 : ahci
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880093] ata3: SATA max UDMA/133 abar m2048@0xe3125000 port 0xe3125100 irq 30
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880096] ata4: SATA max UDMA/133 abar m2048@0xe3125000 port 0xe3125180 irq 30
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880098] ata5: SATA max UDMA/133 abar m2048@0xe3125000 port 0xe3125200 irq 30
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880101] ata6: SATA max UDMA/133 abar m2048@0xe3125000 port 0xe3125280 irq 30
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880103] ata7: SATA max UDMA/133 abar m2048@0xe3125000 port 0xe3125300 irq 30
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880105] ata8: SATA max UDMA/133 abar m2048@0xe3125000 port 0xe3125380 irq 30
Jun 25 16:19:14 Nathan-Linux kernel: [    0.880236] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 25 16:19:14 Nathan-Linux kernel: [    0.916825] usb 1-4: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    0.923259] Initializing USB Mass Storage driver...
Jun 25 16:19:14 Nathan-Linux kernel: [    0.923401] scsi8 : SCSI emulation for USB Mass Storage devices
Jun 25 16:19:14 Nathan-Linux kernel: [    0.923515] usbcore: registered new interface driver usb-storage
Jun 25 16:19:14 Nathan-Linux kernel: [    0.923518] USB Mass Storage support registered.
Jun 25 16:19:14 Nathan-Linux kernel: [    0.929510] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[e3010000-e30107ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Jun 25 16:19:14 Nathan-Linux kernel: [    0.986980] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:27:01:0e
Jun 25 16:19:14 Nathan-Linux kernel: [    0.986982] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
Jun 25 16:19:14 Nathan-Linux kernel: [    0.987003] 0000:00:19.0: eth0: MAC: 7, PHY: 7, PBA No: ffffff-0ff
Jun 25 16:19:14 Nathan-Linux kernel: [    1.034931] usb 1-6: new high speed USB device using ehci_hcd and address 3
Jun 25 16:19:14 Nathan-Linux kernel: [    1.180328] usb 1-6: configuration #1 chosen from 1 choice
Jun 25 16:19:14 Nathan-Linux kernel: [    1.186421] scsi9 : SCSI emulation for USB Mass Storage devices
Jun 25 16:19:14 Nathan-Linux kernel: [    1.207444] ata6: SATA link down (SStatus 0 SControl 300)
Jun 25 16:19:14 Nathan-Linux kernel: [    1.207457] ata7: SATA link down (SStatus 0 SControl 300)
Jun 25 16:19:14 Nathan-Linux kernel: [    1.207472] ata8: SATA link down (SStatus 0 SControl 300)
Jun 25 16:19:14 Nathan-Linux kernel: [    1.364012] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 25 16:19:14 Nathan-Linux kernel: [    1.364358] ata5.00: ATAPI: PLEXTOR DVDR   PX-850SA, 1.05, max UDMA/100
Jun 25 16:19:14 Nathan-Linux kernel: [    1.365329] ata5.00: configured for UDMA/100
Jun 25 16:19:14 Nathan-Linux kernel: [    1.368513] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 25 16:19:14 Nathan-Linux kernel: [    1.382623] ata3.00: ATA-8: WDC WD3200AAJS-22VWA0, 12.01B02, max UDMA/133
Jun 25 16:19:14 Nathan-Linux kernel: [    1.382626] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jun 25 16:19:14 Nathan-Linux kernel: [    1.383474] ata3.00: configured for UDMA/133
Jun 25 16:19:14 Nathan-Linux kernel: [    1.400119] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 12.0 PQ: 0 ANSI: 5
Jun 25 16:19:14 Nathan-Linux kernel: [    1.400254] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jun 25 16:19:14 Nathan-Linux kernel: [    1.400272] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    1.400296] sd 2:0:0:0: [sda] Write Protect is off
Jun 25 16:19:14 Nathan-Linux kernel: [    1.400341] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 25 16:19:14 Nathan-Linux kernel: [    1.400465]  sda: sda1 sda2 < sda5 >
Jun 25 16:19:14 Nathan-Linux kernel: [    1.419608] sd 2:0:0:0: [sda] Attached SCSI disk
Jun 25 16:19:14 Nathan-Linux kernel: [    2.152011] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 25 16:19:14 Nathan-Linux kernel: [    2.170546] ata4.00: ATA-8: WDC WD3200AAJS-22VWA0, 12.01B02, max UDMA/133
Jun 25 16:19:14 Nathan-Linux kernel: [    2.170550] ata4.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Jun 25 16:19:14 Nathan-Linux kernel: [    2.171409] ata4.00: configured for UDMA/133
Jun 25 16:19:14 Nathan-Linux kernel: [    2.184602] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 12.0 PQ: 0 ANSI: 5
Jun 25 16:19:14 Nathan-Linux kernel: [    2.184708] sd 3:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jun 25 16:19:14 Nathan-Linux kernel: [    2.184724] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.184750] sd 3:0:0:0: [sdb] Write Protect is off
Jun 25 16:19:14 Nathan-Linux kernel: [    2.184789] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 25 16:19:14 Nathan-Linux kernel: [    2.184910]  sdb:
Jun 25 16:19:14 Nathan-Linux kernel: [    2.186009] scsi 4:0:0:0: CD-ROM            PLEXTOR  DVDR   PX-850SA  1.05 PQ: 0 ANSI: 5
Jun 25 16:19:14 Nathan-Linux kernel: [    2.191447] 
Jun 25 16:19:14 Nathan-Linux kernel: [    2.191615] sd 3:0:0:0: [sdb] Attached SCSI disk
Jun 25 16:19:14 Nathan-Linux kernel: [    2.192481] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 25 16:19:14 Nathan-Linux kernel: [    2.192485] Uniform CD-ROM driver Revision: 3.20
Jun 25 16:19:14 Nathan-Linux kernel: [    2.192618] sr 4:0:0:0: Attached scsi generic sg2 type 5
Jun 25 16:19:14 Nathan-Linux kernel: [    2.212632] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 25 16:19:14 Nathan-Linux kernel: [    2.213969] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x092880a2)
Jun 25 16:19:14 Nathan-Linux kernel: [    2.214648] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267268] [drm] nouveau 0000:01:00.0: ... appears to be valid
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267271] [drm] nouveau 0000:01:00.0: BIT BIOS found
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267274] [drm] nouveau 0000:01:00.0: Bios version 62.92.24.00
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267277] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267280] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267283] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267285] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267287] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267290] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267292] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267294] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267297] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267299] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00000030
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267301] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267303] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00000030
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267305] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080
Jun 25 16:19:14 Nathan-Linux kernel: [    2.267313] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xC17F
Jun 25 16:19:14 Nathan-Linux kernel: [    2.308648] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xC530
Jun 25 16:19:14 Nathan-Linux kernel: [    2.324507] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD2AB
Jun 25 16:19:14 Nathan-Linux kernel: [    2.324516] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD3CD
Jun 25 16:19:14 Nathan-Linux kernel: [    2.332579] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xD5FD
Jun 25 16:19:14 Nathan-Linux kernel: [    2.332583] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xD662
Jun 25 16:19:14 Nathan-Linux kernel: [    2.356011] [drm] nouveau 0000:01:00.0: 0xD662: Condition still not met after 20ms, skipping following opcodes
Jun 25 16:19:14 Nathan-Linux kernel: [    2.356017] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.356020] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.356023] [drm] nouveau 0000:01:00.0: 0x9FAE: parsing output script 0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.434625] [TTM] Zone  kernel: Available graphics memory: 428582 kiB.
Jun 25 16:19:14 Nathan-Linux kernel: [    2.434627] [TTM] Zone highmem: Available graphics memory: 1675388 kiB.
Jun 25 16:19:14 Nathan-Linux kernel: [    2.434634] [drm] nouveau 0000:01:00.0: 512 MiB VRAM
Jun 25 16:19:14 Nathan-Linux kernel: [    2.448965] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Jun 25 16:19:14 Nathan-Linux kernel: [    2.450658] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454089] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454492] [drm] nouveau 0000:01:00.0: Detected a DAC output
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454495] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454497] [drm] nouveau 0000:01:00.0: Detected a DAC output
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454501] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454503] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454505] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Jun 25 16:19:14 Nathan-Linux kernel: [    2.454559] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Jun 25 16:19:14 Nathan-Linux kernel: [    2.626539] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x40250000, bo c1162c00
Jun 25 16:19:14 Nathan-Linux kernel: [    2.626593] fb0: nouveaufb frame buffer device
Jun 25 16:19:14 Nathan-Linux kernel: [    2.626595] registered panic notifier
Jun 25 16:19:14 Nathan-Linux kernel: [    2.626599] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.628021] vga16fb: mapped to 0xc00a0000
Jun 25 16:19:14 Nathan-Linux kernel: [    2.628023] vga16fb: not registering due to another framebuffer present
Jun 25 16:19:14 Nathan-Linux kernel: [    2.633854] [drm] nouveau 0000:01:00.0: 0x10DB: parsing clock script 0
Jun 25 16:19:14 Nathan-Linux kernel: [    2.635291] Console: switching to colour frame buffer device 240x67
Jun 25 16:19:14 Nathan-Linux kernel: [    2.890745] xor: automatically using best checksumming function: pIII_sse
Jun 25 16:19:14 Nathan-Linux kernel: [    2.908004]    pIII_sse  :  9288.000 MB/sec
Jun 25 16:19:14 Nathan-Linux kernel: [    2.908005] xor: using function: pIII_sse (9288.000 MB/sec)
Jun 25 16:19:14 Nathan-Linux kernel: [    2.910059] device-mapper: dm-raid45: initialized v0.2594b
Jun 25 16:19:14 Nathan-Linux kernel: [    3.062199] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jun 25 16:19:14 Nathan-Linux kernel: [    3.062203] EXT4-fs (sda1): write access will be enabled during recovery
Jun 25 16:19:14 Nathan-Linux kernel: [    3.605183] EXT4-fs (sda1): orphan cleanup on readonly fs
Jun 25 16:19:14 Nathan-Linux kernel: [    3.605309] EXT4-fs (sda1): 3 orphan inodes deleted
Jun 25 16:19:14 Nathan-Linux kernel: [    3.605312] EXT4-fs (sda1): recovery complete
Jun 25 16:19:14 Nathan-Linux kernel: [    4.061697] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 25 16:19:14 Nathan-Linux kernel: [    5.930433] scsi 8:0:0:0: Direct-Access     IOI-CFC                        PQ: 0 ANSI: 0 CCS
Jun 25 16:19:14 Nathan-Linux kernel: [    6.183078] scsi 9:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Jun 25 16:19:14 Nathan-Linux kernel: [    6.896714] scsi 8:0:0:1: Direct-Access     IOI-SMC                        PQ: 0 ANSI: 0 CCS
Jun 25 16:19:14 Nathan-Linux kernel: [    6.903087] scsi 8:0:0:2: Direct-Access     IOI-MMC                        PQ: 0 ANSI: 0 CCS
Jun 25 16:19:14 Nathan-Linux kernel: [    6.909591] scsi 8:0:0:3: Direct-Access     IOI-MSC                        PQ: 0 ANSI: 0 CCS
Jun 25 16:19:14 Nathan-Linux kernel: [    6.909952] sd 8:0:0:0: Attached scsi generic sg3 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    6.910061] sd 8:0:0:1: Attached scsi generic sg4 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    6.910178] sd 8:0:0:2: Attached scsi generic sg5 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    6.910303] sd 8:0:0:3: Attached scsi generic sg6 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    6.910471] sd 9:0:0:0: Attached scsi generic sg7 type 0
Jun 25 16:19:14 Nathan-Linux kernel: [    6.912344] sd 9:0:0:0: [sdg] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun 25 16:19:14 Nathan-Linux kernel: [    6.913712] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Jun 25 16:19:14 Nathan-Linux kernel: [    6.913837] sd 9:0:0:0: [sdg] Write Protect is off
Jun 25 16:19:14 Nathan-Linux kernel: [    6.914464] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Jun 25 16:19:14 Nathan-Linux kernel: [    6.915211] sd 8:0:0:2: [sde] Attached SCSI removable disk
Jun 25 16:19:14 Nathan-Linux kernel: [    6.915961] sd 8:0:0:3: [sdf] Attached SCSI removable disk
Jun 25 16:19:14 Nathan-Linux kernel: [    6.917341]  sdg: sdg1 sdg2
Jun 25 16:19:14 Nathan-Linux kernel: [    6.923336] sd 9:0:0:0: [sdg] Attached SCSI disk
Jun 25 16:19:14 Nathan-Linux kernel: [   12.018799] udev: starting version 151
Jun 25 16:19:14 Nathan-Linux kernel: [   12.022579] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Jun 25 16:19:14 Nathan-Linux kernel: [   12.022684] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Jun 25 16:19:14 Nathan-Linux kernel: [   12.022719] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Jun 25 16:19:14 Nathan-Linux kernel: [   12.025089] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Jun 25 16:19:14 Nathan-Linux kernel: [   12.025095] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Jun 25 16:19:14 Nathan-Linux kernel: [   12.025125] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Jun 25 16:19:14 Nathan-Linux kernel: [   12.028140] lp: driver loaded but no devices found
Jun 25 16:19:14 Nathan-Linux kernel: [   12.119512] Adding 9814008k swap on /dev/sda5.  Priority:-1 extents:1 across:9814008k 
Jun 25 16:19:14 Nathan-Linux kernel: [   12.211577] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 25 16:19:14 Nathan-Linux kernel: [   12.280294] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528633] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528703] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528752] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528804] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528854] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528903] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jun 25 16:19:14 Nathan-Linux kernel: [   12.528955] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Jun 25 16:19:14 Nathan-Linux kernel: [   12.756657] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input12
Jun 25 16:19:15 Nathan-Linux kernel: [   13.051033] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
Jun 25 16:19:15 Nathan-Linux kernel: [   13.054588] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
Jun 25 16:19:15 Nathan-Linux kernel: [   13.320926] ppdev: user-space parallel port driver
Jun 25 16:19:17 Nathan-Linux nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Jun 25 16:19:17 Nathan-Linux nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...

```

I don't believe there is anything in there until the time I turned it back on.

---

