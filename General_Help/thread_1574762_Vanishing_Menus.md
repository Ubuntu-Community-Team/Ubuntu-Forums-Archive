---
title: "Vanishing Menus"
date: 2010-09-14
forum: General Help
---

### Post by swatsbiz on 2010-09-14
This problem appeared a couple of weeks ago, at some point during use the menu's stop dropping down and input boxes become unresponsive, and I have to reboot.

The keyboard appears to not work, but pressing ctrl-alt-del brings up the shutdown menu.

Any reason for this to happen?

---

### Post by robsoles on 2010-09-14
To get help with this problem you will most likely need to supply more info.

Which flavor of Ubuntu are you running? Have you been playing with compiz? Have you added cairo dock or other similar launcher?

I haven't seen this behaviour in several installations of 10.04 LTS - it is likely that log entries around the time of the menus becoming unresponsive will be the most telling.

---

### Post by swatsbiz on 2010-09-15
I'm running 10.04.1 - just installed, and have the problem - randomly.

It appeared in 10.04 (which I managed to screw up and spit out last week!) yes, around the time I had been playing with some compiz and AWN settings.

BUT the problem also appeared while trying to install 10.04.1 from the live CD.  It would let me get through to the partitioning section and the drop down menus wouldn't drop.  At which point I wouldn't be able to input text into text boxes either.

This is frustrating, obviously, what log's do you wnt me to post?

---

### Post by robsoles on 2010-09-17
It sounds like a hardware failure to me but we should be able to prove that.


If booting from the LiveCD it may be difficult to get logs that are worth a look - please check if /var/log/messages and /var/log/Xorg.0.log have entries and post them as attachments if they do.

---

### Post by swatsbiz on 2010-09-18
You could be right there, it could also be fixed with the latest kernel updates ... Next time it happens I'll search those logs out and post them for the time stamp.

Thanks!

---

### Post by swatsbiz on 2010-09-18
Here's the /var/log/messages

It died sometime in the last boot I used it for a while and left running, at 12:56 I switched it down as the keyboard/menu bug had occured

```
Sep 18 12:35:29 david-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 18 12:35:29 david-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="984" x-info="http://www.rsyslog.com"] (re)start
Sep 18 12:35:29 david-desktop rsyslogd: rsyslogd's groupid changed to 103
Sep 18 12:35:29 david-desktop rsyslogd: rsyslogd's userid changed to 101
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=9c1df3a6-818d-48c7-a420-f99be7fcd105 ro quiet splash
Sep 18 12:35:29 david-desktop kernel: [    0.000000] KERNEL supported cpus:
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   Intel GenuineIntel
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   AMD AuthenticAMD
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   Centaur CentaurHauls
Sep 18 12:35:29 david-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] DMI 2.4 present.
Sep 18 12:35:29 david-desktop kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep 18 12:35:29 david-desktop kernel: [    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x400000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Sep 18 12:35:29 david-desktop kernel: [    0.000000] modified physical RAM map:
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfee0000 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 00000000cfef0000 - 00000000cff00000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Sep 18 12:35:29 david-desktop kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Using GB pages for direct mapping
Sep 18 12:35:29 david-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfee0000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Sep 18 12:35:29 david-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Sep 18 12:35:29 david-desktop kernel: [    0.000000] RAMDISK: 377fb000 - 37fefc1b
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f6060 00014 (v00 GBT   )
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: RSDT 00000000cfee3000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: FACP 00000000cfee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: DSDT 00000000cfee30c0 071C9 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: FACS 00000000cfee0000 00040
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: SSDT 00000000cfeea380 0088C (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: HPET 00000000cfeeac40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: MCFG 00000000cfeeac80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: TAMG 00000000cfeeacc0 0039A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: APIC 00000000cfeea2c0 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Sep 18 12:35:29 david-desktop kernel: [    0.000000] No NUMA configuration found
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   bootmap [0000000000010000 -  0000000000035fff] pages 26
Sep 18 12:35:29 david-desktop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #3 [00377fb000 - 0037fefc1b]          RAMDISK ==> [00377fb000 - 0037fefc1b]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #5 [0001a2d000 - 0001a2d0fe]              BRK ==> [0001a2d000 - 0001a2d0fe]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
Sep 18 12:35:29 david-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f4650] f4650
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Zone PFN ranges:
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Sep 18 12:35:29 david-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Movable zone start PFN for each node
Sep 18 12:35:29 david-desktop kernel: [    0.000000] early_node_map[4] active PFN ranges
Sep 18 12:35:29 david-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Sep 18 12:35:29 david-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Sep 18 12:35:29 david-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000cfee0
Sep 18 12:35:29 david-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 18 12:35:29 david-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 18 12:35:29 david-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 18 12:35:29 david-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u262144
Sep 18 12:35:29 david-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
Sep 18 12:35:29 david-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031060
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Policy zone: Normal
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=9c1df3a6-818d-48c7-a420-f99be7fcd105 ro quiet splash
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Initializing CPU#0
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Checking aperture...
Sep 18 12:35:29 david-desktop kernel: [    0.000000] No AGP bridge found
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Node 0: aperture @ 600000000 size 32 MB
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Sep 18 12:35:29 david-desktop kernel: [    0.000000] This costs you 64 MB of RAM
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Memory: 4048028k/4980736k available (5419k kernel code, 787992k absent, 144716k reserved, 2974k data, 872k init)
Sep 18 12:35:29 david-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Sep 18 12:35:29 david-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:472
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Sep 18 12:35:29 david-desktop kernel: [    0.000000] console [tty0] enabled
Sep 18 12:35:29 david-desktop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Sep 18 12:35:29 david-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep 18 12:35:29 david-desktop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Sep 18 12:35:29 david-desktop kernel: [    0.000000] Detected 2812.079 MHz processor.
Sep 18 12:35:29 david-desktop kernel: [    0.030006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5624.15 BogoMIPS (lpj=28120750)
Sep 18 12:35:29 david-desktop kernel: [    0.030020] Security Framework initialized
Sep 18 12:35:29 david-desktop kernel: [    0.030032] AppArmor: AppArmor initialized
Sep 18 12:35:29 david-desktop kernel: [    0.030281] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.031323] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.031786] Mount-cache hash table entries: 256
Sep 18 12:35:29 david-desktop kernel: [    0.031878] Initializing cgroup subsys ns
Sep 18 12:35:29 david-desktop kernel: [    0.031880] Initializing cgroup subsys cpuacct
Sep 18 12:35:29 david-desktop kernel: [    0.031883] Initializing cgroup subsys memory
Sep 18 12:35:29 david-desktop kernel: [    0.031888] Initializing cgroup subsys devices
Sep 18 12:35:29 david-desktop kernel: [    0.031890] Initializing cgroup subsys freezer
Sep 18 12:35:29 david-desktop kernel: [    0.031892] Initializing cgroup subsys net_cls
Sep 18 12:35:29 david-desktop kernel: [    0.031905] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.031907] CPU: L2 Cache: 512K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.031908] CPU 0/0x0 -> Node 0
Sep 18 12:35:29 david-desktop kernel: [    0.031912] CPU: Physical Processor ID: 0
Sep 18 12:35:29 david-desktop kernel: [    0.031913] CPU: Processor Core ID: 0
Sep 18 12:35:29 david-desktop kernel: [    0.031915] mce: CPU supports 6 MCE banks
Sep 18 12:35:29 david-desktop kernel: [    0.031923] Performance Events: AMD PMU driver.
Sep 18 12:35:29 david-desktop kernel: [    0.031926] ... version:                0
Sep 18 12:35:29 david-desktop kernel: [    0.031927] ... bit width:              48
Sep 18 12:35:29 david-desktop kernel: [    0.031928] ... generic registers:      4
Sep 18 12:35:29 david-desktop kernel: [    0.031929] ... value mask:             0000ffffffffffff
Sep 18 12:35:29 david-desktop kernel: [    0.031931] ... max period:             00007fffffffffff
Sep 18 12:35:29 david-desktop kernel: [    0.031932] ... fixed-purpose events:   0
Sep 18 12:35:29 david-desktop kernel: [    0.031933] ... event mask:             000000000000000f
Sep 18 12:35:29 david-desktop kernel: [    0.033183] ACPI: Core revision 20090903
Sep 18 12:35:29 david-desktop kernel: [    0.050020] ftrace: converting mcount calls to 0f 1f 44 00 00
Sep 18 12:35:29 david-desktop kernel: [    0.050028] ftrace: allocating 22538 entries in 89 pages
Sep 18 12:35:29 david-desktop kernel: [    0.055031] Setting APIC routing to flat
Sep 18 12:35:29 david-desktop kernel: [    0.055504] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 18 12:35:29 david-desktop kernel: [    0.159356] CPU0: AMD Phenom(tm) II X4 925 Processor stepping 02
Sep 18 12:35:29 david-desktop kernel: [    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
Sep 18 12:35:29 david-desktop kernel: [    0.040000] Initializing CPU#1
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU 1/0x1 -> Node 0
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: Physical Processor ID: 0
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: Processor Core ID: 1
Sep 18 12:35:29 david-desktop kernel: [    0.310036] CPU1: AMD Phenom(tm) II X4 925 Processor stepping 02
Sep 18 12:35:29 david-desktop kernel: [    0.310042] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep 18 12:35:29 david-desktop kernel: [    0.320048] Booting processor 2 APIC 0x2 ip 0x6000
Sep 18 12:35:29 david-desktop kernel: [    0.040000] Initializing CPU#2
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU 2/0x2 -> Node 0
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: Physical Processor ID: 0
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: Processor Core ID: 3
Sep 18 12:35:29 david-desktop kernel: [    0.480111] CPU2: AMD Phenom(tm) II X4 925 Processor stepping 02
Sep 18 12:35:29 david-desktop kernel: [    0.480116] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Sep 18 12:35:29 david-desktop kernel: [    0.490046] Booting processor 3 APIC 0x3 ip 0x6000
Sep 18 12:35:29 david-desktop kernel: [    0.040000] Initializing CPU#3
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU 3/0x3 -> Node 0
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: Physical Processor ID: 0
Sep 18 12:35:29 david-desktop kernel: [    0.040000] CPU: Processor Core ID: 2
Sep 18 12:35:29 david-desktop kernel: [    0.650083] CPU3: AMD Phenom(tm) II X4 925 Processor stepping 02
Sep 18 12:35:29 david-desktop kernel: [    0.650088] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Sep 18 12:35:29 david-desktop kernel: [    0.660008] Brought up 4 CPUs
Sep 18 12:35:29 david-desktop kernel: [    0.660010] Total of 4 processors activated (22498.97 BogoMIPS).
Sep 18 12:35:29 david-desktop kernel: [    0.661918] devtmpfs: initialized
Sep 18 12:35:29 david-desktop kernel: [    0.661918] regulator: core version 0.5
Sep 18 12:35:29 david-desktop kernel: [    0.661918] Time: 12:35:17  Date: 09/18/10
Sep 18 12:35:29 david-desktop kernel: [    0.661918] NET: Registered protocol family 16
Sep 18 12:35:29 david-desktop kernel: [    0.661918] Trying to unpack rootfs image as initramfs...
Sep 18 12:35:29 david-desktop kernel: [    0.661918] TOM: 00000000d0000000 aka 3328M
Sep 18 12:35:29 david-desktop kernel: [    0.661918] TOM2: 0000000130000000 aka 4864M
Sep 18 12:35:29 david-desktop kernel: [    0.661918] ACPI: bus type pci registered
Sep 18 12:35:29 david-desktop kernel: [    0.661918] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep 18 12:35:29 david-desktop kernel: [    0.661918] PCI: MCFG area at e0000000 reserved in E820
Sep 18 12:35:29 david-desktop kernel: [    0.667127] PCI: Using MMCONFIG at e0000000 - efffffff
Sep 18 12:35:29 david-desktop kernel: [    0.667129] PCI: Using configuration type 1 for base access
Sep 18 12:35:29 david-desktop kernel: [    0.670011] bio: create slab <bio-0> at 0
Sep 18 12:35:29 david-desktop kernel: [    0.677461] ACPI: Interpreter enabled
Sep 18 12:35:29 david-desktop kernel: [    0.677464] ACPI: (supports S0 S3 S4 S5)
Sep 18 12:35:29 david-desktop kernel: [    0.677480] ACPI: Using IOAPIC for interrupt routing
Sep 18 12:35:29 david-desktop kernel: [    0.680945] ACPI: No dock devices found.
Sep 18 12:35:29 david-desktop kernel: [    0.681026] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 18 12:35:29 david-desktop kernel: [    0.681103] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.681106] pci 0000:00:02.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681134] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.681137] pci 0000:00:05.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681163] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.681165] pci 0000:00:06.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681191] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.681193] pci 0000:00:07.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681221] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.681223] pci 0000:00:0a.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681312] pci 0000:00:11.0: set SATA to AHCI mode
Sep 18 12:35:29 david-desktop kernel: [    0.681517] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Sep 18 12:35:29 david-desktop kernel: [    0.681520] pci 0000:00:12.2: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681711] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Sep 18 12:35:29 david-desktop kernel: [    0.681714] pci 0000:00:13.2: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.681940] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.681944] pci 0000:00:14.2: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.682402] pci 0000:02:00.0: PME# supported from D3hot
Sep 18 12:35:29 david-desktop kernel: [    0.682406] pci 0000:02:00.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.682550] pci 0000:03:00.0: PME# supported from D3hot
Sep 18 12:35:29 david-desktop kernel: [    0.682554] pci 0000:03:00.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.682773] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.682776] pci 0000:04:00.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.682917] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 18 12:35:29 david-desktop kernel: [    0.682921] pci 0000:05:00.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.683200] pci 0000:06:0e.0: PME# supported from D0 D1 D2 D3hot
Sep 18 12:35:29 david-desktop kernel: [    0.683204] pci 0000:06:0e.0: PME# disabled
Sep 18 12:35:29 david-desktop kernel: [    0.683236] pci 0000:00:14.4: transparent bridge
Sep 18 12:35:29 david-desktop kernel: [    0.698232] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698305] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698377] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698448] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698590] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698661] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698731] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Sep 18 12:35:29 david-desktop kernel: [    0.698817] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Sep 18 12:35:29 david-desktop kernel: [    0.698821] vgaarb: loaded
Sep 18 12:35:29 david-desktop kernel: [    0.698897] SCSI subsystem initialized
Sep 18 12:35:29 david-desktop kernel: [    0.698914] usbcore: registered new interface driver usbfs
Sep 18 12:35:29 david-desktop kernel: [    0.698914] usbcore: registered new interface driver hub
Sep 18 12:35:29 david-desktop kernel: [    0.698914] usbcore: registered new device driver usb
Sep 18 12:35:29 david-desktop kernel: [    0.698914] ACPI: WMI: Mapper loaded
Sep 18 12:35:29 david-desktop kernel: [    0.698914] PCI: Using ACPI for IRQ routing
Sep 18 12:35:29 david-desktop kernel: [    0.698914] pci 0000:00:00.0: BAR 3: can't allocate resource
Sep 18 12:35:29 david-desktop kernel: [    0.698914] NetLabel: Initializing
Sep 18 12:35:29 david-desktop kernel: [    0.698914] NetLabel:  domain hash size = 128
Sep 18 12:35:29 david-desktop kernel: [    0.698914] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 18 12:35:29 david-desktop kernel: [    0.698914] NetLabel:  unlabeled traffic allowed by default
Sep 18 12:35:29 david-desktop kernel: [    0.698914] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Sep 18 12:35:29 david-desktop kernel: [    0.698914] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Sep 18 12:35:29 david-desktop kernel: [    0.701031] Switching to clocksource tsc
Sep 18 12:35:29 david-desktop kernel: [    0.701622] AppArmor: AppArmor Filesystem Enabled
Sep 18 12:35:29 david-desktop kernel: [    0.701622] pnp: PnP ACPI init
Sep 18 12:35:29 david-desktop kernel: [    0.701622] ACPI: bus type pnp registered
Sep 18 12:35:29 david-desktop kernel: [    0.702818] pnp 00:0b: mem resource (0xd3000-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Sep 18 12:35:29 david-desktop kernel: [    0.702821] pnp 00:0b: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Sep 18 12:35:29 david-desktop kernel: [    0.702823] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Sep 18 12:35:29 david-desktop kernel: [    0.702826] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Sep 18 12:35:29 david-desktop kernel: [    0.702828] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Sep 18 12:35:29 david-desktop kernel: [    0.702831] pnp 00:0b: mem resource (0x100000-0xcfedffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Sep 18 12:35:29 david-desktop kernel: [    0.702901] pnp: PnP ACPI: found 12 devices
Sep 18 12:35:29 david-desktop kernel: [    0.702903] ACPI: ACPI bus type pnp unregistered
Sep 18 12:35:29 david-desktop kernel: [    0.702909] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702911] system 00:01: ioport range 0x220-0x225 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702913] system 00:01: ioport range 0x290-0x294 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702917] system 00:02: ioport range 0x4100-0x411f has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702919] system 00:02: ioport range 0x228-0x22f has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702923] system 00:02: ioport range 0x40b-0x40b has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702924] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702926] system 00:02: ioport range 0xc00-0xc01 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702928] system 00:02: ioport range 0xc14-0xc14 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702930] system 00:02: ioport range 0xc50-0xc52 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702932] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702934] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702935] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702937] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702939] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702941] system 00:02: ioport range 0x4000-0x40fe has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702943] system 00:02: ioport range 0x4210-0x4217 has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702945] system 00:02: ioport range 0xb00-0xb0f has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702947] system 00:02: ioport range 0xb10-0xb1f has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702949] system 00:02: ioport range 0xb20-0xb3f has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702953] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702957] system 00:0b: iomem range 0xcfee0000-0xcfeeffff could not be reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702959] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702962] system 00:0b: iomem range 0xcfef0000-0xcfefffff has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702964] system 00:0b: iomem range 0xcff00000-0xcfffffff could not be reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702966] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702968] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.702970] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
Sep 18 12:35:29 david-desktop kernel: [    0.707619] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Sep 18 12:35:29 david-desktop kernel: [    0.707621] pci 0000:00:02.0:   IO window: 0xa000-0xafff
Sep 18 12:35:29 david-desktop kernel: [    0.707623] pci 0000:00:02.0:   MEM window: 0xfdf00000-0xfdffffff
Sep 18 12:35:29 david-desktop kernel: [    0.707626] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Sep 18 12:35:29 david-desktop kernel: [    0.707629] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
Sep 18 12:35:29 david-desktop kernel: [    0.707631] pci 0000:00:05.0:   IO window: 0xe000-0xefff
Sep 18 12:35:29 david-desktop kernel: [    0.707634] pci 0000:00:05.0:   MEM window: 0xfde00000-0xfdefffff
Sep 18 12:35:29 david-desktop kernel: [    0.707636] pci 0000:00:05.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Sep 18 12:35:29 david-desktop kernel: [    0.707639] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
Sep 18 12:35:29 david-desktop kernel: [    0.707641] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Sep 18 12:35:29 david-desktop kernel: [    0.707643] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Sep 18 12:35:29 david-desktop kernel: [    0.707646] pci 0000:00:06.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Sep 18 12:35:29 david-desktop kernel: [    0.707649] pci 0000:00:07.0: PCI bridge, secondary bus 0000:04
Sep 18 12:35:29 david-desktop kernel: [    0.707650] pci 0000:00:07.0:   IO window: 0xc000-0xcfff
Sep 18 12:35:29 david-desktop kernel: [    0.707653] pci 0000:00:07.0:   MEM window: 0xfda00000-0xfdafffff
Sep 18 12:35:29 david-desktop kernel: [    0.707655] pci 0000:00:07.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Sep 18 12:35:29 david-desktop kernel: [    0.707658] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:05
Sep 18 12:35:29 david-desktop kernel: [    0.707660] pci 0000:00:0a.0:   IO window: 0xb000-0xbfff
Sep 18 12:35:29 david-desktop kernel: [    0.707663] pci 0000:00:0a.0:   MEM window: 0xfd800000-0xfd8fffff
Sep 18 12:35:29 david-desktop kernel: [    0.707665] pci 0000:00:0a.0:   PREFETCH window: 0x000000fd500000-0x000000fd5fffff
Sep 18 12:35:29 david-desktop kernel: [    0.707668] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06
Sep 18 12:35:29 david-desktop kernel: [    0.707671] pci 0000:00:14.4:   IO window: 0x9000-0x9fff
Sep 18 12:35:29 david-desktop kernel: [    0.707675] pci 0000:00:14.4:   MEM window: 0xfd700000-0xfd7fffff
Sep 18 12:35:29 david-desktop kernel: [    0.707679] pci 0000:00:14.4:   PREFETCH window: 0xfd600000-0xfd6fffff
Sep 18 12:35:29 david-desktop kernel: [    0.707697] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    0.707711] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep 18 12:35:29 david-desktop kernel: [    0.707717] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    0.707730] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 18 12:35:29 david-desktop kernel: [    0.707736] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    0.707806] NET: Registered protocol family 2
Sep 18 12:35:29 david-desktop kernel: [    0.707923] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.708735] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.710821] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.711083] TCP: Hash tables configured (established 524288 bind 65536)
Sep 18 12:35:29 david-desktop kernel: [    0.711085] TCP reno registered
Sep 18 12:35:29 david-desktop kernel: [    0.711170] NET: Registered protocol family 1
Sep 18 12:35:29 david-desktop kernel: [    0.859285] PCI-DMA: Disabling AGP.
Sep 18 12:35:29 david-desktop kernel: [    0.859351] PCI-DMA: aperture base @ 20000000 size 65536 KB
Sep 18 12:35:29 david-desktop kernel: [    0.859352] PCI-DMA: using GART IOMMU.
Sep 18 12:35:29 david-desktop kernel: [    0.859355] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Sep 18 12:35:29 david-desktop kernel: [    0.861065] Scanning for low memory corruption every 60 seconds
Sep 18 12:35:29 david-desktop kernel: [    0.861171] audit: initializing netlink socket (disabled)
Sep 18 12:35:29 david-desktop kernel: [    0.861179] type=2000 audit(1284813316.858:1): initialized
Sep 18 12:35:29 david-desktop kernel: [    0.862635] Freeing initrd memory: 8147k freed
Sep 18 12:35:29 david-desktop kernel: [    0.867574] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep 18 12:35:29 david-desktop kernel: [    0.868525] VFS: Disk quotas dquot_6.5.2
Sep 18 12:35:29 david-desktop kernel: [    0.868560] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep 18 12:35:29 david-desktop kernel: [    0.868966] fuse init (API version 7.13)
Sep 18 12:35:29 david-desktop kernel: [    0.869019] msgmni has been set to 7922
Sep 18 12:35:29 david-desktop kernel: [    0.869210] alg: No test for stdrng (krng)
Sep 18 12:35:29 david-desktop kernel: [    0.869248] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep 18 12:35:29 david-desktop kernel: [    0.869250] io scheduler noop registered
Sep 18 12:35:29 david-desktop kernel: [    0.869251] io scheduler anticipatory registered
Sep 18 12:35:29 david-desktop kernel: [    0.869253] io scheduler deadline registered
Sep 18 12:35:29 david-desktop kernel: [    0.869275] io scheduler cfq registered (default)
Sep 18 12:35:29 david-desktop kernel: [    0.869756] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 18 12:35:29 david-desktop kernel: [    0.869771] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 18 12:35:29 david-desktop kernel: [    0.869831] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Sep 18 12:35:29 david-desktop kernel: [    0.869834] ACPI: Power Button [PWRB]
Sep 18 12:35:29 david-desktop kernel: [    0.869869] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep 18 12:35:29 david-desktop kernel: [    0.869871] ACPI: Power Button [PWRF]
Sep 18 12:35:29 david-desktop kernel: [    0.870105] processor LNXCPU:00: registered as cooling_device0
Sep 18 12:35:29 david-desktop kernel: [    0.870131] processor LNXCPU:01: registered as cooling_device1
Sep 18 12:35:29 david-desktop kernel: [    0.870161] processor LNXCPU:02: registered as cooling_device2
Sep 18 12:35:29 david-desktop kernel: [    0.870191] processor LNXCPU:03: registered as cooling_device3
Sep 18 12:35:29 david-desktop kernel: [    0.872383] Linux agpgart interface v0.103
Sep 18 12:35:29 david-desktop kernel: [    0.872405] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Sep 18 12:35:29 david-desktop kernel: [    0.872503] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 18 12:35:29 david-desktop kernel: [    0.872741] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 18 12:35:29 david-desktop kernel: [    0.873338] brd: module loaded
Sep 18 12:35:29 david-desktop kernel: [    0.873619] loop: module loaded
Sep 18 12:35:29 david-desktop kernel: [    0.873669] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Sep 18 12:35:29 david-desktop kernel: [    0.873793] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 18 12:35:29 david-desktop kernel: [    0.873852] pata_acpi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep 18 12:35:29 david-desktop kernel: [    0.873874] pata_acpi 0000:02:00.0: PCI INT A disabled
Sep 18 12:35:29 david-desktop kernel: [    0.873902] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
Sep 18 12:35:29 david-desktop kernel: [    0.873905] pata_acpi 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 18 12:35:29 david-desktop kernel: [    0.873927] pata_acpi 0000:03:00.1: PCI INT B disabled
Sep 18 12:35:29 david-desktop kernel: [    0.874161] Fixed MDIO Bus: probed
Sep 18 12:35:29 david-desktop kernel: [    0.874181] PPP generic driver version 2.4.2
Sep 18 12:35:29 david-desktop kernel: [    0.874203] tun: Universal TUN/TAP device driver, 1.6
Sep 18 12:35:29 david-desktop kernel: [    0.874205] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 18 12:35:29 david-desktop kernel: [    0.874249] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 18 12:35:29 david-desktop kernel: [    0.874275] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Sep 18 12:35:29 david-desktop kernel: [    0.874301] ehci_hcd 0000:00:12.2: EHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    0.874322] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Sep 18 12:35:29 david-desktop kernel: [    0.874350] ehci_hcd 0000:00:12.2: debug port 1
Sep 18 12:35:29 david-desktop kernel: [    0.874374] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Sep 18 12:35:29 david-desktop kernel: [    0.888407] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Sep 18 12:35:29 david-desktop kernel: [    0.888473] usb usb1: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    0.888496] hub 1-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    0.888501] hub 1-0:1.0: 6 ports detected
Sep 18 12:35:29 david-desktop kernel: [    0.888575] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 18 12:35:29 david-desktop kernel: [    0.888586] ehci_hcd 0000:00:13.2: EHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    0.888608] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Sep 18 12:35:29 david-desktop kernel: [    0.888631] ehci_hcd 0000:00:13.2: debug port 1
Sep 18 12:35:29 david-desktop kernel: [    0.888655] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Sep 18 12:35:29 david-desktop kernel: [    0.908451] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Sep 18 12:35:29 david-desktop kernel: [    0.908514] usb usb2: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    0.908533] hub 2-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    0.908537] hub 2-0:1.0: 6 ports detected
Sep 18 12:35:29 david-desktop kernel: [    0.908583] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 18 12:35:29 david-desktop kernel: [    0.908620] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 18 12:35:29 david-desktop kernel: [    0.908633] ohci_hcd 0000:00:12.0: OHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    0.908657] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Sep 18 12:35:29 david-desktop kernel: [    0.908684] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Sep 18 12:35:29 david-desktop kernel: [    0.972479] usb usb3: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    0.972498] hub 3-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    0.972505] hub 3-0:1.0: 3 ports detected
Sep 18 12:35:29 david-desktop kernel: [    0.972575] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 18 12:35:29 david-desktop kernel: [    0.972585] ohci_hcd 0000:00:12.1: OHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    0.972605] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Sep 18 12:35:29 david-desktop kernel: [    0.972620] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Sep 18 12:35:29 david-desktop kernel: [    1.032490] usb usb4: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    1.032511] hub 4-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    1.032518] hub 4-0:1.0: 3 ports detected
Sep 18 12:35:29 david-desktop kernel: [    1.032588] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    1.032600] ohci_hcd 0000:00:13.0: OHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    1.032620] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Sep 18 12:35:29 david-desktop kernel: [    1.032646] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Sep 18 12:35:29 david-desktop kernel: [    1.094087] usb usb5: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    1.094103] hub 5-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    1.094109] hub 5-0:1.0: 3 ports detected
Sep 18 12:35:29 david-desktop kernel: [    1.094181] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    1.094193] ohci_hcd 0000:00:13.1: OHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    1.094213] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Sep 18 12:35:29 david-desktop kernel: [    1.094228] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Sep 18 12:35:29 david-desktop kernel: [    1.154089] usb usb6: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    1.154105] hub 6-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    1.154112] hub 6-0:1.0: 3 ports detected
Sep 18 12:35:29 david-desktop kernel: [    1.154185] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    1.154197] ohci_hcd 0000:00:14.5: OHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    1.154220] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Sep 18 12:35:29 david-desktop kernel: [    1.154236] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Sep 18 12:35:29 david-desktop kernel: [    1.214086] usb usb7: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    1.214102] hub 7-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    1.214109] hub 7-0:1.0: 2 ports detected
Sep 18 12:35:29 david-desktop kernel: [    1.214148] uhci_hcd: USB Universal Host Controller Interface driver
Sep 18 12:35:29 david-desktop kernel: [    1.214190] PNP: No PS/2 controller found. Probing ports directly.
Sep 18 12:35:29 david-desktop kernel: [    1.247860] Failed to disable AUX port, but continuing anyway... Is this a SiS?
Sep 18 12:35:29 david-desktop kernel: [    1.247862] If AUX port is really absent please use the 'i8042.noaux' option.
Sep 18 12:35:29 david-desktop kernel: [    1.247928] usb 2-1: new high speed USB device using ehci_hcd and address 2
Sep 18 12:35:29 david-desktop kernel: [    1.395346] usb 2-1: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    1.490110] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 18 12:35:29 david-desktop kernel: [    1.490180] mice: PS/2 mouse device common for all mice
Sep 18 12:35:29 david-desktop kernel: [    1.490252] rtc_cmos 00:05: RTC can wake from S4
Sep 18 12:35:29 david-desktop kernel: [    1.490273] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Sep 18 12:35:29 david-desktop kernel: [    1.490303] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Sep 18 12:35:29 david-desktop kernel: [    1.490378] device-mapper: uevent: version 1.0.3
Sep 18 12:35:29 david-desktop kernel: [    1.490449] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Sep 18 12:35:29 david-desktop kernel: [    1.490528] device-mapper: multipath: version 1.1.0 loaded
Sep 18 12:35:29 david-desktop kernel: [    1.490530] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 18 12:35:29 david-desktop kernel: [    1.490701] cpuidle: using governor ladder
Sep 18 12:35:29 david-desktop kernel: [    1.490703] cpuidle: using governor menu
Sep 18 12:35:29 david-desktop kernel: [    1.490945] TCP cubic registered
Sep 18 12:35:29 david-desktop kernel: [    1.491039] NET: Registered protocol family 10
Sep 18 12:35:29 david-desktop kernel: [    1.491353] lo: Disabled Privacy Extensions
Sep 18 12:35:29 david-desktop kernel: [    1.491538] NET: Registered protocol family 17
Sep 18 12:35:29 david-desktop kernel: [    1.491580] powernow-k8: Found 1 AMD Phenom(tm) II X4 925 Processor processors (4 cpu cores) (version 2.20.00)
Sep 18 12:35:29 david-desktop kernel: [    1.491608] powernow-k8:    0 : pstate 0 (2800 MHz)
Sep 18 12:35:29 david-desktop kernel: [    1.491609] powernow-k8:    1 : pstate 1 (2100 MHz)
Sep 18 12:35:29 david-desktop kernel: [    1.491610] powernow-k8:    2 : pstate 2 (1600 MHz)
Sep 18 12:35:29 david-desktop kernel: [    1.491611] powernow-k8:    3 : pstate 3 (800 MHz)
Sep 18 12:35:29 david-desktop kernel: [    1.491925] registered taskstats version 1
Sep 18 12:35:29 david-desktop kernel: [    1.492317]   Magic number: 10:671:582
Sep 18 12:35:29 david-desktop kernel: [    1.492332] pci_bus 0000:03: hash matches
Sep 18 12:35:29 david-desktop kernel: [    1.492335] pcieport 0000:00:06.0: hash matches
Sep 18 12:35:29 david-desktop kernel: [    1.492384] rtc_cmos 00:05: setting system clock to 2010-09-18 12:35:18 UTC (1284813318)
Sep 18 12:35:29 david-desktop kernel: [    1.492386] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 18 12:35:29 david-desktop kernel: [    1.492387] EDD information not available.
Sep 18 12:35:29 david-desktop kernel: [    1.492420] Freeing unused kernel memory: 872k freed
Sep 18 12:35:29 david-desktop kernel: [    1.492597] Write protecting the kernel read-only data: 7692k
Sep 18 12:35:29 david-desktop kernel: [    1.503975] udev: starting version 151
Sep 18 12:35:29 david-desktop kernel: [    1.524895] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Sep 18 12:35:29 david-desktop kernel: [    1.525000] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Sep 18 12:35:29 david-desktop kernel: [    1.525003] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Sep 18 12:35:29 david-desktop kernel: [    1.527334] scsi0 : ahci
Sep 18 12:35:29 david-desktop kernel: [    1.527533] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 18 12:35:29 david-desktop kernel: [    1.528286] scsi2 : pata_jmicron
Sep 18 12:35:29 david-desktop kernel: [    1.528902] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep 18 12:35:29 david-desktop kernel: [    1.528916] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    1.529427] eth0: RTL8168d/8111d at 0xffffc9000065e000, 6c:f0:49:55:fd:cc, XID 083000c0 IRQ 30
Sep 18 12:35:29 david-desktop kernel: [    1.536387] Initializing USB Mass Storage driver...
Sep 18 12:35:29 david-desktop kernel: [    1.547098] Floppy drive(s): fd0 is 1.44M
Sep 18 12:35:29 david-desktop kernel: [    1.547159] scsi4 : SCSI emulation for USB Mass Storage devices
Sep 18 12:35:29 david-desktop kernel: [    1.548394] usbcore: registered new interface driver usb-storage
Sep 18 12:35:29 david-desktop kernel: [    1.548396] USB Mass Storage support registered.
Sep 18 12:35:29 david-desktop kernel: [    1.565660] FDC 0 is a post-1991 82077
Sep 18 12:35:29 david-desktop kernel: [    1.567360] scsi1 : ahci
Sep 18 12:35:29 david-desktop kernel: [    1.567415] scsi3 : pata_jmicron
Sep 18 12:35:29 david-desktop kernel: [    1.567446] ata5: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 19
Sep 18 12:35:29 david-desktop kernel: [    1.567448] ata6: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 19
Sep 18 12:35:29 david-desktop kernel: [    1.567469] scsi5 : ahci
Sep 18 12:35:29 david-desktop kernel: [    1.567522] ohci1394 0000:06:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Sep 18 12:35:29 david-desktop kernel: [    1.567532] scsi6 : ahci
Sep 18 12:35:29 david-desktop kernel: [    1.567618] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Sep 18 12:35:29 david-desktop kernel: [    1.567621] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Sep 18 12:35:29 david-desktop kernel: [    1.567624] ata3: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 22
Sep 18 12:35:29 david-desktop kernel: [    1.567627] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Sep 18 12:35:29 david-desktop kernel: [    1.567750] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    1.567873] scsi7 : pata_atiixp
Sep 18 12:35:29 david-desktop kernel: [    1.567919] scsi8 : pata_atiixp
Sep 18 12:35:29 david-desktop kernel: [    1.568672] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Sep 18 12:35:29 david-desktop kernel: [    1.568674] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Sep 18 12:35:29 david-desktop kernel: [    1.590055] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Sep 18 12:35:29 david-desktop kernel: [    1.590058] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Sep 18 12:35:29 david-desktop kernel: [    1.590172] scsi9 : ahci
Sep 18 12:35:29 david-desktop kernel: [    1.590225] scsi10 : ahci
Sep 18 12:35:29 david-desktop kernel: [    1.590254] ata9: SATA max UDMA/133 abar m8192@0xfdcfe000 port 0xfdcfe100 irq 18
Sep 18 12:35:29 david-desktop kernel: [    1.590257] ata10: SATA max UDMA/133 abar m8192@0xfdcfe000 port 0xfdcfe180 irq 18
Sep 18 12:35:29 david-desktop kernel: [    1.630052] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fd7ff000-fd7ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Sep 18 12:35:29 david-desktop kernel: [    1.760449] ata7.00: HPA unlocked: 312573551 -> 312581808, native 312581808
Sep 18 12:35:29 david-desktop kernel: [    1.760453] ata7.00: ATA-7: Hitachi HDS721616PLAT80, P22OA8BA, max UDMA/133
Sep 18 12:35:29 david-desktop kernel: [    1.760455] ata7.00: 312581808 sectors, multi 16: LBA48 
Sep 18 12:35:29 david-desktop kernel: [    1.800611] ata7.00: configured for UDMA/100
Sep 18 12:35:29 david-desktop kernel: [    1.910052] ata4: SATA link down (SStatus 0 SControl 300)
Sep 18 12:35:29 david-desktop kernel: [    1.930045] ata10: SATA link down (SStatus 0 SControl 300)
Sep 18 12:35:29 david-desktop kernel: [    1.930049] ata9: SATA link down (SStatus 0 SControl 300)
Sep 18 12:35:29 david-desktop kernel: [    1.940021] usb 6-1: new full speed USB device using ohci_hcd and address 2
Sep 18 12:35:29 david-desktop kernel: [    2.090055] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep 18 12:35:29 david-desktop kernel: [    2.090059] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 18 12:35:29 david-desktop kernel: [    2.090222] ata2.00: ATAPI: ASUS    DRW-2014L1T, 1.01, max UDMA/66
Sep 18 12:35:29 david-desktop kernel: [    2.090536] ata2.00: configured for UDMA/66
Sep 18 12:35:29 david-desktop kernel: [    2.091054] ata1.00: ATA-8: STM3500418AS, CC38, max UDMA/133
Sep 18 12:35:29 david-desktop kernel: [    2.091057] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Sep 18 12:35:29 david-desktop kernel: [    2.092243] ata1.00: configured for UDMA/133
Sep 18 12:35:29 david-desktop kernel: [    2.110130] scsi 0:0:0:0: Direct-Access     ATA      STM3500418AS     CC38 PQ: 0 ANSI: 5
Sep 18 12:35:29 david-desktop kernel: [    2.110251] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Sep 18 12:35:29 david-desktop kernel: [    2.110254] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 18 12:35:29 david-desktop kernel: [    2.110277] sd 0:0:0:0: [sda] Write Protect is off
Sep 18 12:35:29 david-desktop kernel: [    2.110335] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 18 12:35:29 david-desktop kernel: [    2.110415]  sda:
Sep 18 12:35:29 david-desktop kernel: [    2.110672] scsi 1:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.01 PQ: 0 ANSI: 5
Sep 18 12:35:29 david-desktop kernel: [    2.113477] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 18 12:35:29 david-desktop kernel: [    2.113480] Uniform CD-ROM driver Revision: 3.20
Sep 18 12:35:29 david-desktop kernel: [    2.113579] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep 18 12:35:29 david-desktop kernel: [    2.118934]  sda1 < sda5 sda6
Sep 18 12:35:29 david-desktop kernel: [    2.140227] usb 6-1: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    2.146037]  sda7 > sda2
Sep 18 12:35:29 david-desktop kernel: [    2.146343] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 18 12:35:29 david-desktop kernel: [    2.148990] usbcore: registered new interface driver hiddev
Sep 18 12:35:29 david-desktop kernel: [    2.152311] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input3
Sep 18 12:35:29 david-desktop kernel: [    2.152356] generic-usb 0003:1532:0109.0001: input,hidraw0: USB HID v1.10 Keyboard [Razer Razer Lycosa] on usb-0000:00:13.1-1/input0
Sep 18 12:35:29 david-desktop kernel: [    2.160223] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input4
Sep 18 12:35:29 david-desktop kernel: [    2.160269] generic-usb 0003:1532:0109.0002: input,hidraw1: USB HID v1.10 Device [Razer Razer Lycosa] on usb-0000:00:13.1-1/input1
Sep 18 12:35:29 david-desktop kernel: [    2.160284] usbcore: registered new interface driver usbhid
Sep 18 12:35:29 david-desktop kernel: [    2.160286] usbhid: v2.6:USB HID core driver
Sep 18 12:35:29 david-desktop kernel: [    2.450028] usb 6-2: new full speed USB device using ohci_hcd and address 3
Sep 18 12:35:29 david-desktop kernel: [    2.490030] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep 18 12:35:29 david-desktop kernel: [    2.490554] ata3.00: ATAPI: Optiarc DVD RW AD-7170S, 1.00, max UDMA/66
Sep 18 12:35:29 david-desktop kernel: [    2.491303] ata3.00: configured for UDMA/66
Sep 18 12:35:29 david-desktop kernel: [    2.510888] scsi 5:0:0:0: CD-ROM            Optiarc  DVD RW AD-7170S  1.00 PQ: 0 ANSI: 5
Sep 18 12:35:29 david-desktop kernel: [    2.514784] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 18 12:35:29 david-desktop kernel: [    2.514893] sr 5:0:0:0: Attached scsi generic sg2 type 5
Sep 18 12:35:29 david-desktop kernel: [    2.514997] scsi 7:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
Sep 18 12:35:29 david-desktop kernel: [    2.515093] sd 7:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Sep 18 12:35:29 david-desktop kernel: [    2.515110] sd 7:0:0:0: Attached scsi generic sg3 type 0
Sep 18 12:35:29 david-desktop kernel: [    2.515118] sd 7:0:0:0: [sdb] Write Protect is off
Sep 18 12:35:29 david-desktop kernel: [    2.515134] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 18 12:35:29 david-desktop kernel: [    2.515227]  sdb: sdb1 sdb2 < sdb5 >
Sep 18 12:35:29 david-desktop kernel: [    2.537029] sd 7:0:0:0: [sdb] Attached SCSI disk
Sep 18 12:35:29 david-desktop kernel: [    2.647278] usb 6-2: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    2.660708] input: Microsoft SideWinder™ Mouse as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input5
Sep 18 12:35:29 david-desktop kernel: [    2.660764] generic-usb 0003:045E:0724.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft SideWinder™ Mouse] on usb-0000:00:13.1-2/input0
Sep 18 12:35:29 david-desktop kernel: [    2.691771] ata8.00: ATA-6: WDC WD1200JD-00GBB0, 02.05D02, max UDMA/100
Sep 18 12:35:29 david-desktop kernel: [    2.691774] ata8.00: 234441648 sectors, multi 16: LBA48 
Sep 18 12:35:29 david-desktop kernel: [    2.731752] ata8.00: configured for UDMA/100
Sep 18 12:35:29 david-desktop kernel: [    2.731811] scsi 8:0:0:0: Direct-Access     ATA      WDC WD1200JD-00G 02.0 PQ: 0 ANSI: 5
Sep 18 12:35:29 david-desktop kernel: [    2.731909] sd 8:0:0:0: [sdc] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 18 12:35:29 david-desktop kernel: [    2.731923] sd 8:0:0:0: Attached scsi generic sg4 type 0
Sep 18 12:35:29 david-desktop kernel: [    2.731934] sd 8:0:0:0: [sdc] Write Protect is off
Sep 18 12:35:29 david-desktop kernel: [    2.731953] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 18 12:35:29 david-desktop kernel: [    2.732033]  sdc: sdc1
Sep 18 12:35:29 david-desktop kernel: [    2.754012] sd 8:0:0:0: [sdc] Attached SCSI disk
Sep 18 12:35:29 david-desktop kernel: [    3.052210] EXT4-fs (sda5): mounted filesystem with ordered data mode
Sep 18 12:35:29 david-desktop kernel: [    6.541564] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader CF RW 0814 PQ: 0 ANSI: 0
Sep 18 12:35:29 david-desktop kernel: [    6.542561] scsi 4:0:0:1: Direct-Access     USB2.0   CardReader Combo 0814 PQ: 0 ANSI: 0
Sep 18 12:35:29 david-desktop kernel: [    6.542890] sd 4:0:0:0: Attached scsi generic sg5 type 0
Sep 18 12:35:29 david-desktop kernel: [    6.542972] sd 4:0:0:1: Attached scsi generic sg6 type 0
Sep 18 12:35:29 david-desktop kernel: [    6.547054] sd 4:0:0:0: [sdd] Attached SCSI removable disk
Sep 18 12:35:29 david-desktop kernel: [    6.548425] sd 4:0:0:1: [sde] Attached SCSI removable disk
Sep 18 12:35:29 david-desktop kernel: [    9.363144] udev: starting version 151
Sep 18 12:35:29 david-desktop kernel: [    9.397694] Adding 5116660k swap on /dev/sda7.  Priority:-1 extents:1 across:5116660k 
Sep 18 12:35:29 david-desktop kernel: [    9.436592] type=1505 audit(1284809726.438:2):  operation="profile_load" pid=656 name="/sbin/dhclient3"
Sep 18 12:35:29 david-desktop kernel: [    9.436791] type=1505 audit(1284809726.438:3):  operation="profile_load" pid=656 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 18 12:35:29 david-desktop kernel: [    9.436903] type=1505 audit(1284809726.438:4):  operation="profile_load" pid=656 name="/usr/lib/connman/scripts/dhclient-script"
Sep 18 12:35:29 david-desktop kernel: [    9.527367] vga16fb: mapped to 0xffff8800000a0000
Sep 18 12:35:29 david-desktop kernel: [    9.527415] fb0: VGA16 VGA frame buffer device
Sep 18 12:35:29 david-desktop kernel: [    9.541916] EDAC MC: Ver: 2.1.0 Sep 17 2010
Sep 18 12:35:29 david-desktop kernel: [    9.542790] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 18 12:35:29 david-desktop kernel: [    9.542817] xhci_hcd 0000:04:00.0: xHCI Host Controller
Sep 18 12:35:29 david-desktop kernel: [    9.542926] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
Sep 18 12:35:29 david-desktop kernel: [    9.543027] xhci_hcd 0000:04:00.0: irq 19, io mem 0xfdafe000
Sep 18 12:35:29 david-desktop kernel: [    9.546932] usb usb8: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor
Sep 18 12:35:29 david-desktop kernel: [    9.546998] usb usb8: configuration #1 chosen from 1 choice
Sep 18 12:35:29 david-desktop kernel: [    9.547025] hub 8-0:1.0: USB hub found
Sep 18 12:35:29 david-desktop kernel: [    9.547031] hub 8-0:1.0: 4 ports detected
Sep 18 12:35:29 david-desktop kernel: [    9.623139] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Sep 18 12:35:29 david-desktop kernel: [    9.623143] Disabling lock debugging due to kernel taint
Sep 18 12:35:29 david-desktop kernel: [    9.670673] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
Sep 18 12:35:29 david-desktop kernel: [    9.670708] [fglrx]   vendor: 1002 device: 68f9 count: 1
Sep 18 12:35:29 david-desktop kernel: [    9.671352] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
Sep 18 12:35:29 david-desktop kernel: [    9.671354] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 18 12:35:29 david-desktop kernel: [    9.672249] [fglrx] ioport: bar 4, base 0xae00, size: 0x100
Sep 18 12:35:29 david-desktop kernel: [    9.672261] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 12:35:29 david-desktop kernel: [    9.672537] [fglrx] Kernel PAT support is enabled
Sep 18 12:35:29 david-desktop kernel: [    9.672550] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
Sep 18 12:35:29 david-desktop kernel: [    9.673410] EDAC amd64_edac:  Ver: 3.2.0 Sep 17 2010
Sep 18 12:35:29 david-desktop kernel: [    9.680736] cfg80211: Calling CRDA to update world regulatory domain
Sep 18 12:35:29 david-desktop kernel: [    9.680806] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Sep 18 12:35:29 david-desktop kernel: [    9.680812] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Sep 18 12:35:29 david-desktop kernel: [    9.680813]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Sep 18 12:35:29 david-desktop kernel: [    9.680814]  (Note that use of the override may cause unknown side effects.)
Sep 18 12:35:29 david-desktop kernel: [    9.680952] amd64_edac: probe of 0000:00:18.2 failed with error -22
Sep 18 12:35:29 david-desktop kernel: [    9.681649] lp: driver loaded but no devices found
Sep 18 12:35:29 david-desktop kernel: [    9.699170] cfg80211: World regulatory domain updated:
Sep 18 12:35:29 david-desktop kernel: [    9.699172] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 18 12:35:29 david-desktop kernel: [    9.699174] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 18 12:35:29 david-desktop kernel: [    9.699176] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 18 12:35:29 david-desktop kernel: [    9.699178] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 18 12:35:29 david-desktop kernel: [    9.699179] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 18 12:35:29 david-desktop kernel: [    9.699181] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 18 12:35:29 david-desktop kernel: [    9.770949] ath5k 0000:06:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Sep 18 12:35:29 david-desktop kernel: [    9.771007] ath5k 0000:06:07.0: registered as 'phy0'
Sep 18 12:35:29 david-desktop kernel: [    9.824769] Console: switching to colour frame buffer device 80x30
Sep 18 12:35:29 david-desktop kernel: [   10.298360] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 18 12:35:29 david-desktop kernel: [   10.353697] EXT4-fs (sda6): mounted filesystem with ordered data mode
Sep 18 12:35:29 david-desktop kernel: [   12.325343] hda_codec: ALC889: BIOS auto-probing.
Sep 18 12:35:29 david-desktop kernel: [   12.326865] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
Sep 18 12:35:29 david-desktop kernel: [   12.337165] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Sep 18 12:35:29 david-desktop kernel: [   12.337176] cfg80211: Calling CRDA for country: CN
Sep 18 12:35:29 david-desktop kernel: [   12.337203] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 18 12:35:29 david-desktop kernel: [   12.338452] cfg80211: Regulatory domain changed to country: CN
Sep 18 12:35:29 david-desktop kernel: [   12.338455] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 18 12:35:29 david-desktop kernel: [   12.338457] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 18 12:35:29 david-desktop kernel: [   12.338459] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Sep 18 12:35:29 david-desktop kernel: [   12.371665] type=1505 audit(1284809729.377:5):  operation="profile_load" pid=1093 name="/usr/share/gdm/guest-session/Xsession"
Sep 18 12:35:29 david-desktop kernel: [   12.372664] type=1505 audit(1284809729.377:6):  operation="profile_replace" pid=1095 name="/sbin/dhclient3"
Sep 18 12:35:29 david-desktop kernel: [   12.372864] type=1505 audit(1284809729.377:7):  operation="profile_replace" pid=1095 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 18 12:35:29 david-desktop kernel: [   12.372978] type=1505 audit(1284809729.377:8):  operation="profile_replace" pid=1095 name="/usr/lib/connman/scripts/dhclient-script"
Sep 18 12:35:29 david-desktop kernel: [   12.374814] type=1505 audit(1284809729.377:9):  operation="profile_load" pid=1096 name="/usr/bin/evince"
Sep 18 12:35:29 david-desktop kernel: [   12.377285] type=1505 audit(1284809729.377:10):  operation="profile_load" pid=1096 name="/usr/bin/evince-previewer"
Sep 18 12:35:29 david-desktop kernel: [   12.378846] type=1505 audit(1284809729.377:11):  operation="profile_load" pid=1096 name="/usr/bin/evince-thumbnailer"
Sep 18 12:35:29 david-desktop kernel: [   12.389079] r8169: eth0: link down
Sep 18 12:35:29 david-desktop kernel: [   12.389414] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 18 12:35:29 david-desktop kernel: [   12.467911] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 18 12:35:29 david-desktop kernel: [   12.647040] ppdev: user-space parallel port driver
Sep 18 12:35:29 david-desktop kernel: [   12.710370] [fglrx] Firegl kernel thread PID: 1256
Sep 18 12:35:29 david-desktop kernel: [   12.710561] [fglrx] IRQ 31 Enabled
Sep 18 12:35:29 david-desktop kernel: [   12.852326] [fglrx] Gart USWC size:1236 M.
Sep 18 12:35:29 david-desktop kernel: [   12.852328] [fglrx] Gart cacheable size:491 M.
Sep 18 12:35:29 david-desktop kernel: [   12.852333] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep 18 12:35:29 david-desktop kernel: [   12.852335] [fglrx] Reserved FB block: Unshared offset:f91f000, size:3e1000 
Sep 18 12:35:29 david-desktop kernel: [   12.852337] [fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 
Sep 18 12:35:32 david-desktop kernel: [   15.923814] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Sep 18 12:35:37 david-desktop pulseaudio[1439]: ratelimit.c: 6 events suppressed
Sep 18 12:38:06 david-desktop kernel: [  169.783001] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 18 12:38:47 david-desktop kernel: [  210.179053] lo: Disabled Privacy Extensions
Sep 18 12:56:23 david-desktop kernel: Kernel logging (proc) stopped.
```


And here is the Xorg.0.log

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux david-desktop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=9c1df3a6-818d-48c7-a420-f99be7fcd105 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 18 12:57:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:68f9:174b:e153 ATI Technologies Inc rev 0, Mem @ 0xd0000000/268435456, 0xfdfc0000/131072, I/O @ 0x0000ae00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x68F9) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:5:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0xcce7a0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Radeon HD 5400 Series" (Chipset = 0x68f9)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe153)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfdfc0000
(--) fglrx(0): I/O port at 0x0000ae00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 12.15
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: 1
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
(II) fglrx(0): Interrupt handler installed at IRQ 31.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: CRT on secondary DAC [crt2]
(II) fglrx(0):  Display0: Failed to get EDID information. 
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output CRT2 connected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output CRT2 using initial mode 1600x1200
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 5400 Series has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f08b1cb9000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.11
(II) fglrx(0):     Date: Apr  8 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-25-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010a8000
(II) fglrx(0): FBMM initialized for area (0,0)-(1664,2624)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1664 x 960
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 423 x 317
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) XKB: reuse xkmfile /var/lib/xkb/server-1529D616753195EAEFADABC0A5076611C127C014.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) config/udev: Adding input device Razer Razer Lycosa (/dev/input/event3)
(**) Razer Razer Lycosa: Applying InputClass "evdev keyboard catchall"
(**) Razer Razer Lycosa: always reports core events
(**) Razer Razer Lycosa: Device: "/dev/input/event3"
(II) Razer Razer Lycosa: Found keys
(II) Razer Razer Lycosa: Configuring as keyboard
(II) XINPUT: Adding extended input device "Razer Razer Lycosa" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) config/udev: Adding input device Razer Razer Lycosa (/dev/input/event4)
(**) Razer Razer Lycosa: Applying InputClass "evdev keyboard catchall"
(**) Razer Razer Lycosa: always reports core events
(**) Razer Razer Lycosa: Device: "/dev/input/event4"
(II) Razer Razer Lycosa: Found 1 mouse buttons
(II) Razer Razer Lycosa: Found scroll wheel(s)
(II) Razer Razer Lycosa: Found relative axes
(II) Razer Razer Lycosa: Found absolute axes
(II) Razer Razer Lycosa: Found keys
(II) Razer Razer Lycosa: Configuring as mouse
(II) Razer Razer Lycosa: Configuring as keyboard
(**) Razer Razer Lycosa: YAxisMapping: buttons 4 and 5
(**) Razer Razer Lycosa: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Razer Razer Lycosa" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(EE) Razer Razer Lycosa: failed to initialize for relative axes.
(II) Razer Razer Lycosa: initialized for absolute axes.
(II) config/udev: Adding input device Microsoft SideWinder™ Mouse (/dev/input/event5)
(**) Microsoft SideWinder™ Mouse: Applying InputClass "evdev pointer catchall"
(**) Microsoft SideWinder™ Mouse: Applying InputClass "evdev keyboard catchall"
(**) Microsoft SideWinder™ Mouse: always reports core events
(**) Microsoft SideWinder™ Mouse: Device: "/dev/input/event5"
(II) Microsoft SideWinder™ Mouse: Found 9 mouse buttons
(II) Microsoft SideWinder™ Mouse: Found scroll wheel(s)
(II) Microsoft SideWinder™ Mouse: Found relative axes
(II) Microsoft SideWinder™ Mouse: Found x and y relative axes
(II) Microsoft SideWinder™ Mouse: Found absolute axes
(II) Microsoft SideWinder™ Mouse: Found x and y absolute axes
(II) Microsoft SideWinder™ Mouse: Found keys
(II) Microsoft SideWinder™ Mouse: Configuring as mouse
(II) Microsoft SideWinder™ Mouse: Configuring as keyboard
(**) Microsoft SideWinder™ Mouse: YAxisMapping: buttons 4 and 5
(**) Microsoft SideWinder™ Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft SideWinder™ Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "extd"
(II) Microsoft SideWinder™ Mouse: initialized for relative axes.
(WW) Microsoft SideWinder™ Mouse: ignoring absolute axes.
(II) config/udev: Adding input device Microsoft SideWinder™ Mouse (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft SideWinder™ Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
```

I hope that reveals something :-D

---

### Post by swatsbiz on 2010-09-22
bump, still having problems with it, and there's no apparent reason it just happens randomly making browsing hopeless.

---

### Post by robsoles on 2010-09-22
these may help perhaps:

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

[http://ubuntuforums.org/showthread.php?t=1471349&page=3](http://ubuntuforums.org/showthread.php?t=1471349&page=3)

---

### Post by Unterseeboot_234 on 2010-09-23
I had a similar glitch. I changed the interface language and suddenly the next day I'm missing the Shutdown button on the top panel on the far right. Also, my drop-down menus would hesitate before appearing.

I happened to see "cryllic" in your xorg.conf dump. So, maybe the gnome restore could help, like it did for me.

**[Restore top panel]("http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/")**

Be extra cautious about the commands. I was on an unfamiliar language keyboard and failed to notice I had omitted ~ (tilde) on a rm. Wiped out the Home folder. Pity too, I had Lucid just perfect with the proprietary Radeon driver.

Maybe I'm wrong. I'm no expert. But I found your post looking for insight on getting my Radeon driver running again after a reformat / install for Lucid.

---

