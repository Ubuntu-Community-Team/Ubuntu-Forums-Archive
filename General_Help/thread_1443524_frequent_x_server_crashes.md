---
title: "frequent x server crashes"
date: 2010-03-31
forum: General Help
---

### Post by puphin on 2010-03-31
Hi,

i experience X crashes on a frequent level. First it happened with the current stable nvidia 180 driver, and the nonfree flash player (youtube, vimeo, etc). I replaced the stable nvidia driver with the 180-dev driver which fixed the flash problem.  However it still happens that the X chashes without any reason or pattern. One time it crashed the moment I wanted to save a PDF file to my HDD downloading it with Firefox, another time it crashed while idling.

I use an Alienware M15x with a nvidia 260M. Compiz is installed and active. Which other data or logs do you need? Is the problem known? Any possible way I can fix this?

cu Roman

---

### Post by francescogondolin on 2010-03-31
I was going to write a new question but I will post my question on this topic (since it's the same). I'm new to Ubuntu and I had a crash (not the first recently). Give you all the information I have and I think can be useful:

[SIZE=4]**Situation:**[/SIZE]
- Apache2 and MySQL where running in background (but not used at the time)
- Skype was opened (no windows)
- Firefox was on the youtube page
- Netbeans was opened (I was following a very cool course on youtube)

**[SIZE=4]Hardware and software:[/SIZE]**
- Aspire 5935G
- Nvidia GeForce GT 130M
- Intel Core 2 Duo Processor P8600

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 130M] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0200
    Flags: fast devsel, IRQ 11
    Memory at e2000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at e0000000 (64-bit, non-prefetchable) [disabled] [size=32M]
    I/O ports at 5000 [disabled] [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel modules: nvidiafb



[SIZE=4][B]Logs from var/log (Hoping they are useful...they are uncomplete but just think can give an idea to someone who understands.....). The system stopped at 1-59 and was rebooted at 2.01

Messages
[/B][SIZE=2]Apr  1 00:57:39 xxx-laptop kernel: [12585.309986] tg3: eth0: Link is up at 100 Mbps, full duplex.
Apr  1 00:57:39 xxx-laptop kernel: [12585.309990] tg3: eth0: Flow control is on for TX and on for RX.
Apr  1 01:48:24 xxx-laptop kernel: [15629.926437] atkbd.c: Unknown key pressed (translated set 2, code 0x92 on isa0060/serio0).
Apr  1 01:48:24 xxx-laptop kernel: [15629.926442] atkbd.c: Use 'setkeycodes e012 <keycode>' to make it known.
Apr  1 01:48:24 xxx-laptop kernel: [15629.934325] atkbd.c: Unknown key released (translated set 2, code 0x92 on isa0060/serio0).
Apr  1 01:48:24 xxx-laptop kernel: [15629.934329] atkbd.c: Use 'setkeycodes e012 <keycode>' to make it known.
Apr  1 02:01:01 xxx-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  1 02:01:01 xxx-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="549" x-info="http://www.rsyslog.com"] (re)start
Apr  1 02:01:01 xxx-laptop rsyslogd: rsyslogd's groupid changed to 102
Apr  1 02:01:01 xxx-laptop rsyslogd: rsyslogd's userid changed to 101
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Linux version 2.6.31-20-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 (Ubuntu 2.6.31-20.58-generic-pae)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] KERNEL supported cpus:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Intel GenuineIntel
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   AMD AuthenticAMD
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   NSC Geode by NSC
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Centaur CentaurHauls
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbb6c000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbb6c000 - 00000000bbbbf000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbbbf000 - 00000000bbc73000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbc73000 - 00000000bbcbf000 (ACPI NVS)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbcbf000 - 00000000bbce9000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbce9000 - 00000000bbcff000 (ACPI data)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbcff000 - 00000000bbd00000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbd00000 - 00000000c0000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] DMI 2.4 present.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] modified physical RAM map:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bbb6c000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbb6c000 - 00000000bbbbf000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbbbf000 - 00000000bbc73000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbc73000 - 00000000bbcbf000 (ACPI NVS)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbcbf000 - 00000000bbce9000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbce9000 - 00000000bbcff000 (ACPI data)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbcff000 - 00000000bbd00000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbd00000 - 00000000c0000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] RAMDISK: 3789e000 - 37fef03e
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Allocated new RAMDISK: 008ba000 - 0100b03e
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Move RAMDISK from 000000003789e000 - 0000000037fef03d to 008ba000 - 0100b03d
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: XSDT bbcfe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: FACP bbcfd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: DSDT bbceb000 0CA7E (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: FACS bbc80000 00040
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: HPET bbcfc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: APIC bbcfb000 0006C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: MCFG bbcfa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: ASF! bbcf9000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: SLIC bbcf8000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: BOOT bbcea000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: SSDT bbce9000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] 4230MB HIGHMEM available.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] 889MB LOWMEM available.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   low ram: 0 - 379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   node 0 bootmap 00009000 - 0000ff40
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #3 [0000100000 - 00008b2960]    TEXT DATA BSS ==> [0000100000 - 00008b2960]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #5 [00008b3000 - 00008b91b4]              BRK ==> [00008b3000 - 00008b91b4]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #7 [00008ba000 - 000100b03e]      NEW RAMDISK ==> [00008ba000 - 000100b03e]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Zone PFN ranges:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   HighMem  0x000379fe -> 0x00140000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] early_node_map[7] active PFN ranges
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bbb6c
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x000bbbbf -> 0x000bbc73
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x000bbcbf -> 0x000bbce9
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x000bbcff -> 0x000bbd00
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Using APIC driver default
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c381c000, static data 35612 bytes
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1020901
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=681e05bc-995b-4aa4-a1e0-d0bceb8bb884 ro quiet splash
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing CPU#0
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] allocated 26214400 bytes of page_cgroup
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Memory: 4040680k/5242880k available (4601k kernel code, 83080k reserved, 2152k data, 544k init, 3213620k highmem)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] virtual kernel memory layout:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]       .init : 0xc0799000 - 0xc0821000   ( 544 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]       .data : 0xc057e758 - 0xc0798828   (2152 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc057e758   (4601 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Detected 2393.840 MHz processor.
Apr  1 02:01:01 xxx-laptop kernel: [    0.001112] Console: colour VGA+ 80x25
Apr  1 02:01:01 xxx-laptop kernel: [    0.001115] console [tty0] enabled
Apr  1 02:01:01 xxx-laptop kernel: [    0.001255] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Apr  1 02:01:01 xxx-laptop kernel: [    0.001260] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.68 BogoMIPS (lpj=9575360)
Apr  1 02:01:01 xxx-laptop kernel: [    0.001275] Security Framework initialized
Apr  1 02:01:01 xxx-laptop kernel: [    0.001292] AppArmor: AppArmor initialized
Apr  1 02:01:01 xxx-laptop kernel: [    0.001298] Mount-cache hash table entries: 512
Apr  1 02:01:01 xxx-laptop kernel: [    0.001407] Initializing cgroup subsys ns
Apr  1 02:01:01 xxx-laptop kernel: [    0.001411] Initializing cgroup subsys cpuacct
Apr  1 02:01:01 xxx-laptop kernel: [    0.001414] Initializing cgroup subsys memory
Apr  1 02:01:01 xxx-laptop kernel: [    0.001420] Initializing cgroup subsys freezer
Apr  1 02:01:01 xxx-laptop kernel: [    0.001422] Initializing cgroup subsys net_cls
Apr  1 02:01:01 xxx-laptop kernel: [    0.001434] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 02:01:01 xxx-laptop kernel: [    0.001436] CPU: L2 cache: 3072K
Apr  1 02:01:01 xxx-laptop kernel: [    0.001438] CPU: Physical Processor ID: 0
Apr  1 02:01:01 xxx-laptop kernel: [    0.001440] CPU: Processor Core ID: 0
Apr  1 02:01:01 xxx-laptop kernel: [    0.001443] mce: CPU supports 6 MCE banks
Apr  1 02:01:01 xxx-laptop kernel: [    0.001450] CPU0: Thermal monitoring enabled (TM1)
Apr  1 02:01:01 xxx-laptop kernel: [    0.001453] using mwait in idle threads.
Apr  1 02:01:01 xxx-laptop kernel: [    0.001458] Performance Counters: Core2 events, Intel PMU driver.
Apr  1 02:01:01 xxx-laptop kernel: [    0.001463] ... version:                 2
Apr  1 02:01:01 xxx-laptop kernel: [    0.001464] ... bit width:               40
Apr  1 02:01:01 xxx-laptop kernel: [    0.001466] ... generic counters:        2
Apr  1 02:01:01 xxx-laptop kernel: [    0.001467] ... value mask:              000000ffffffffff
Apr  1 02:01:01 xxx-laptop kernel: [    0.001469] ... max period:              000000007fffffff
Apr  1 02:01:01 xxx-laptop kernel: [    0.001470] ... fixed-purpose counters:  3
Apr  1 02:01:01 xxx-laptop kernel: [    0.001471] ... counter mask:            0000000700000003
Apr  1 02:01:01 xxx-laptop kernel: [    0.001474] Checking 'hlt' instruction... OK.
Apr  1 02:01:01 xxx-laptop kernel: [    0.018385] ACPI: Core revision 20090521
Apr  1 02:01:01 xxx-laptop kernel: [    0.036359] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  1 02:01:01 xxx-laptop kernel: [    0.079568] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
Apr  1 02:01:01 xxx-laptop kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Apr  1 02:01:01 xxx-laptop kernel: [    0.004000] Initializing CPU#1
[/SIZE][/SIZE][SIZE=2][SIZE=4][B]
Daemon[/B][/SIZE]

[/SIZE]Apr  1 00:57:53 xxx-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr  1 00:57:53 xxx-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  1 00:58:45 xxx-laptop ntpdate[29812]: can't find host ntp.ubuntu.com
Apr  1 00:58:45 xxx-laptop ntpdate[29812]: no servers can be used, exiting
Apr  1 01:09:08 xxx-laptop avahi-daemon[640]: Invalid query packet.
Apr  1 01:10:28 xxx-laptop avahi-daemon[640]: last message repeated 2 times
Apr  1 01:48:21 xxx-laptop avahi-daemon[640]: Invalid query packet.
Apr  1 01:49:30 xxx-laptop avahi-daemon[640]: last message repeated 5 times
Apr  1 02:01:01 xxx-laptop NetworkManager: <info>  starting...
Apr  1 02:01:01 xxx-laptop NetworkManager: <info>  Trying to start the modem-manager...
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/eth0, iface: eth0)
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr  1 02:01:01 xxx-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr  1 02:01:01 xxx-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr  1 02:01:01 xxx-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Sierra
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Option
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Option High-Speed
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Gobi
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Generic
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Novatel
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin MotoC
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Huawei
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Ericsson MBM
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin ZTE
Apr  1 02:01:01 xxx-laptop modem-manager: Loaded plugin Nokia
Apr  1 02:01:01 xxx-laptop avahi-daemon[628]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Apr  1 02:01:01 xxx-laptop avahi-daemon[628]: Successfully dropped root privileges.
Apr  1 02:01:01 xxx-laptop avahi-daemon[628]: avahi-daemon 0.6.25 starting up.
Apr  1 02:01:01 xxx-laptop avahi-daemon[628]: Successfully called chroot().
Apr  1 02:01:01 xxx-laptop avahi-daemon[628]: Successfully dropped remaining capabilities.


[SIZE=4]**Syslog**[/SIZE]

axlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  1 01:48:21 xxx-laptop avahi-daemon[640]: Invalid query packet.
Apr  1 01:48:24 xxx-laptop avahi-daemon[640]: last message repeated 2 times
Apr  1 01:48:24 xxx-laptop kernel: [15629.926437] atkbd.c: Unknown key pressed (translated set 2, code 0x92 on isa0060/serio0).
Apr  1 01:48:24 xxx-laptop kernel: [15629.926442] atkbd.c: Use 'setkeycodes e012 <keycode>' to make it known.
Apr  1 01:48:24 xxx-laptop kernel: [15629.934325] atkbd.c: Unknown key released (translated set 2, code 0x92 on isa0060/serio0).
Apr  1 01:48:24 xxx-laptop kernel: [15629.934329] atkbd.c: Use 'setkeycodes e012 <keycode>' to make it known.
Apr  1 01:48:24 xxx-laptop avahi-daemon[640]: Invalid query packet.
Apr  1 01:49:30 xxx-laptop avahi-daemon[640]: last message repeated 2 times
Apr  1 02:01:01 xxx-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  1 02:01:01 xxx-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="549" x-info="http://www.rsyslog.com"] (re)start
Apr  1 02:01:01 xxx-laptop rsyslogd: rsyslogd's groupid changed to 102
Apr  1 02:01:01 xxx-laptop rsyslogd: rsyslogd's userid changed to 101
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Linux version 2.6.31-20-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 (Ubuntu 2.6.31-20.58-generic-pae)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] KERNEL supported cpus:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Intel GenuineIntel
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   AMD AuthenticAMD
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   NSC Geode by NSC
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Centaur CentaurHauls
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbb6c000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbb6c000 - 00000000bbbbf000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbbbf000 - 00000000bbc73000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbc73000 - 00000000bbcbf000 (ACPI NVS)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbcbf000 - 00000000bbce9000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbce9000 - 00000000bbcff000 (ACPI data)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbcff000 - 00000000bbd00000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000bbd00000 - 00000000c0000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] DMI 2.4 present.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] MTRR default type: uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   00000-9FFFF write-back
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   C0000-DFFFF write-protect
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   E0000-EFFFF uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   F0000-FFFFF write-protect
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   0 base 0FFF00000 mask FFFF00000 write-protect
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   1 base 0FFFC0000 mask FFFFE0000 uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   2 base 000000000 mask F80000000 write-back
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   3 base 080000000 mask FC0000000 write-back
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   4 base 0BC000000 mask FFC000000 uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   5 base 0BBE00000 mask FFFE00000 uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   6 base 0BBD00000 mask FFFF00000 uncachable
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   7 base 100000000 mask FC0000000 write-back
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] modified physical RAM map:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bbb6c000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbb6c000 - 00000000bbbbf000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbbbf000 - 00000000bbc73000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbc73000 - 00000000bbcbf000 (ACPI NVS)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbcbf000 - 00000000bbce9000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbce9000 - 00000000bbcff000 (ACPI data)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbcff000 - 00000000bbd00000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000bbd00000 - 00000000c0000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  0000200000 - 0037800000 page 2M
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]  0037800000 - 00379fe000 page 4k
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] RAMDISK: 3789e000 - 37fef03e
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Allocated new RAMDISK: 008ba000 - 0100b03e
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Move RAMDISK from 000000003789e000 - 0000000037fef03d to 008ba000 - 0100b03d
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: XSDT bbcfe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: FACP bbcfd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: DSDT bbceb000 0CA7E (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: FACS bbc80000 00040
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: HPET bbcfc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: APIC bbcfb000 0006C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: MCFG bbcfa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: ASF! bbcf9000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: SLIC bbcf8000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: BOOT bbcea000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: SSDT bbce9000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] 4230MB HIGHMEM available.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] 889MB LOWMEM available.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   low ram: 0 - 379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   node 0 bootmap 00009000 - 0000ff40
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #3 [0000100000 - 00008b2960]    TEXT DATA BSS ==> [0000100000 - 00008b2960]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #5 [00008b3000 - 00008b91b4]              BRK ==> [00008b3000 - 00008b91b4]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #7 [00008ba000 - 000100b03e]      NEW RAMDISK ==> [00008ba000 - 000100b03e]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Zone PFN ranges:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   HighMem  0x000379fe -> 0x00140000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] early_node_map[7] active PFN ranges
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bbb6c
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x000bbbbf -> 0x000bbc73
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x000bbcbf -> 0x000bbce9
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x000bbcff -> 0x000bbd00
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] On node 0 totalpages: 1031142
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c078fce0, node_mem_map c100c000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Normal zone: 1748 pages used for memmap
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   Normal zone: 221994 pages, LIFO batch:31
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   HighMem zone: 8461 pages used for memmap
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]   HighMem zone: 794944 pages, LIFO batch:31
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Using APIC driver default
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c381c000, static data 35612 bytes
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1020901
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=681e05bc-995b-4aa4-a1e0-d0bceb8bb884 ro quiet splash
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing CPU#0
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] allocated 26214400 bytes of page_cgroup
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Memory: 4040680k/5242880k available (4601k kernel code, 83080k reserved, 2152k data, 544k init, 3213620k highmem)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] virtual kernel memory layout:
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]       .init : 0xc0799000 - 0xc0821000   ( 544 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]       .data : 0xc057e758 - 0xc0798828   (2152 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc057e758   (4601 kB)
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Apr  1 02:01:01 xxx-laptop kernel: [    0.000000] Detected 2393.840 MHz processor.
Apr  1 02:01:01 xxx-laptop kernel: [    0.001112] Console: colour VGA+ 80x25
Apr  1 02:01:01 xxx-laptop kernel: [    0.001115] console [tty0] enabled
Apr  1 02:01:01 xxx-laptop kernel: [    0.001252] hpet clockevent registered
Apr  1 02:01:01 xxx-laptop kernel: [    0.001255] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Apr  1 02:01:01 xxx-laptop kernel: [    0.001260] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.68 BogoMIPS (lpj=9575360)
Apr  1 02:01:01 xxx-laptop kernel: [    0.001275] Security Framework initialized
Apr  1 02:01:01 xxx-laptop kernel: [    0.001292] AppArmor: AppArmor initialized
Apr  1 02:01:01 xxx-laptop kernel: [    0.001298] Mount-cache hash table entries: 512
Apr  1 02:01:01 xxx-laptop kernel: [    0.001407] Initializing cgroup subsys ns
Apr  1 02:01:01 xxx-laptop kernel: [    0.001411] Initializing cgroup subsys cpuacct
Apr  1 02:01:01 xxx-laptop kernel: [    0.001414] Initializing cgroup subsys memory
Apr  1 02:01:01 xxx-laptop kernel: [    0.001420] Initializing cgroup subsys freezer
Apr  1 02:01:01 xxx-laptop kernel: [    0.001422] Initializing cgroup subsys net_cls
Apr  1 02:01:01 xxx-laptop kernel: [    0.001434] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 02:01:01 xxx-laptop kernel: [    0.001436] CPU: L2 cache: 3072K
Apr  1 02:01:01 xxx-laptop kernel: [    0.001438] CPU: Physical Processor ID: 0
Apr  1 02:01:01 xxx-laptop kernel: [    0.001440] CPU: Processor Core ID: 0
Apr  1 02:01:01 xxx-laptop kernel: [    0.001443] mce: CPU supports 6 MCE banks
Apr  1 02:01:01 xxx-laptop kernel: [    0.001450] CPU0: Thermal monitoring enabled (TM1)
Apr  1 02:01:01 xxx-laptop kernel: [    0.001453] using mwait in idle threads.
Apr  1 02:01:01 xxx-laptop kernel: [    0.001458] Performance Counters: Core2 events, Intel PMU driver.
Apr  1 02:01:01 xxx-laptop kernel: [    0.001463] ... version:                 2
Apr  1 02:01:01 xxx-laptop kernel: [    0.001464] ... bit width:               40
Apr  1 02:01:01 xxx-laptop kernel: [    0.001466] ... generic counters:        2
Apr  1 02:01:01 xxx-laptop kernel: [    0.001467] ... value mask:              000000ffffffffff
Apr  1 02:01:01 xxx-laptop kernel: [    0.001469] ... max period:              000000007fffffff
Apr  1 02:01:01 xxx-laptop kernel: [    0.001470] ... fixed-purpose counters:  3
Apr  1 02:01:01 xxx-laptop kernel: [    0.001471] ... counter mask:            0000000700000003
Apr  1 02:01:01 xxx-laptop kernel: [    0.001474] Checking 'hlt' instruction... OK.

---

### Post by HermanAB on 2010-03-31
Hmm, I have given up with the crummy Nvidia drivers - they are all bad - so I now use the VESA driver.

---

### Post by puphin on 2010-04-04
well thats not an option to me.

I found this thread here which was interesting to read:
[http://www.nvnews.net/vbulletin/showthread.php?t=142946](http://www.nvnews.net/vbulletin/showthread.php?t=142946)

Will try the 32 bit version and see if that works. Installing the 195 driver requires some extra work. Find more about that here:

[http://www.webupd8.org/2009/12/try-out-new-nvidia-195xx-graphics.html](http://www.webupd8.org/2009/12/try-out-new-nvidia-195xx-graphics.html)

However the 195 driver did not help me. That is of course in its 64 bit version.

It seems like all Linux Distros are affected by this. So my original plan to try it with Gentoo is trashed for now. Yet there are drivers for FreeBSD and OpenSolaris, both of which are acceptable Unix systems which would do the trick. If everything else fails I might go for one of these systems.

Will do some experiments and tell you about the outcome.

cu

---

### Post by francescogondolin on 2010-04-04
Actually now it's a few days it hasn't crashed. I think it must be related to Youtube, or at least to Audio/Video problems. Anyhow the main problem is NVIDIA Drivers. Once I was going to lose all my data because of this: I don't use Ubuntu since a long a to recover data from the home directory using just the terminal wasn't the easiest thing.

Before doing anything remember that:
- Backup copy of your files
- Backup copy of X11 folder (so in case you can still overwrite and access the desktop enviroment)
- Pay attention to SUGGESTED NVIDIA DRIVER. If I "update" to the suggest driver it will just stop to work
- Make your GRUB loading time long enough (3-4 seconds).....because by default it's 0 seconds (I have only Ubuntu now) so it can be difficult to enter and painful

Let's keep this topic open untill we find a solution :)

---

