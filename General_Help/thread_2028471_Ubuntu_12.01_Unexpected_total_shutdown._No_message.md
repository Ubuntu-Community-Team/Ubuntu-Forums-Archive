---
title: "Ubuntu 12.01 Unexpected total shutdown. No message or anything.."
date: 2012-07-18
forum: General Help
---

### Post by tijnh on 2012-07-18
[B][SIZE=3]Bug/Error Description
[/SIZE][/B][SIZE=3][SIZE=2]My Ubuntu machine spontaneously shuts down a lot of times. Sometimes after 1 minute another time after half an hour. No message or anythink, just a total shutdown (blackscreen) So i've been to my computer mechanic to checkout my hardware (PC is just 3 months old) I thought it would be something there that would overheat it and the motherboard would shut it down, but this was not the case. It's absolutely in the Ubuntu system. I have no clue what to do and where to look. I tried reinstalling my video drivers, updating my hardware. I even bought a new video card, because i thought it was in there. 

Anyone an idea what I can do, I have serval pc's running Ubuntu with no problems at all. Only this thing, I thought maybe i have the wrong kernel for the AMD 8-core?   
[/SIZE][/SIZE][B][SIZE=3]
Sample movie what happends:
[/SIZE][/B][SIZE=3][SIZE=2]This example video was in an update, but this happens all the time.
[http://www.youtube.com/watch?v=MDXOBOjS3bc&feature=youtube_gdata_player](http://www.youtube.com/watch?v=MDXOBOjS3bc&feature=youtube_gdata_player)[/SIZE]
[/SIZE][B][SIZE=3]
System specs[/SIZE]
Ubuntu 12.04 LTS[/B]
Memory **11.7 GiB**
Processor** AMD FX(tm)-8120 Eight-Core Processor x 8**
OS type** 64-bit**

[B]
[SIZE=3]System logfile[/SIZE] (/var/log/syslog)[/B]
```

Jul 18 13:52:39 tijn-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="805" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jul 18 13:52:39 tijn-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="805" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jul 18 13:52:52 tijn-desktop kernel: [  344.525680] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:52:52 tijn-desktop kernel: [  344.525689] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:52:52 tijn-desktop kernel: [  344.556797] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:52:52 tijn-desktop kernel: [  344.556805] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:06 tijn-desktop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul 18 13:55:06 tijn-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="859" x-info="http://www.rsyslog.com"] start
Jul 18 13:55:06 tijn-desktop rsyslogd: rsyslogd's groupid changed to 103
Jul 18 13:55:06 tijn-desktop rsyslogd: rsyslogd's userid changed to 101
Jul 18 13:55:06 tijn-desktop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Linux version 3.2.0-26-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 (Ubuntu 3.2.0-26.41-generic 3.2.19)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=eee1e085-6a87-46ed-8764-c2caf5a5d531 ro quiet splash vt.handoff=7
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] KERNEL supported cpus:
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   Intel GenuineIntel
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dff90000 (usable)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000dff90000 - 00000000dff9e000 (ACPI data)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000dff9e000 - 00000000dffe0000 (ACPI NVS)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000dffe0000 - 00000000e0000000 (reserved)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000320000000 (usable)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] DMI present.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] DMI: MICRO-STAR INTERNATIONAL CO.,LTD MS-7596/760GM-E51(MS-7596), BIOS V3.1 09/29/2011
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] No AGP bridge found
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] last_pfn = 0x320000 max_arch_pfn = 0x400000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] MTRR default type: uncachable
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   00000-9FFFF write-back
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   A0000-EFFFF uncachable
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   3 disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   4 disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   5 disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   6 disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   7 disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] TOM2: 0000000320000000 aka 12800M
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] last_pfn = 0xdff90 max_arch_pfn = 0x400000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Using GB pages for direct mapping
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dff90000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  00c0000000 - 00dfe00000 page 2M
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  00dfe00000 - 00dff90000 page 4k
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] kernel direct mapping tables up to dff90000 @ 1fffd000-20000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000320000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  0100000000 - 0300000000 page 1G
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  0300000000 - 0320000000 page 2M
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] kernel direct mapping tables up to 320000000 @ dff8e000-dff90000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] RAMDISK: 3584a000 - 36c1d000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f8f20 00014 (v00 ACPIAM)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: RSDT 00000000dff90000 0003C (v01 7596MS A7596100 20110929 MSFT 00000097)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: FACP 00000000dff90200 00084 (v01 7596MS A7596100 20110929 MSFT 00000097)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: DSDT 00000000dff90660 0941A (v01  A7596 A7596100 00000100 INTL 20051117)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: FACS 00000000dff9e000 00040
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: APIC 00000000dff90390 0010C (v01 7596MS A7596100 20110929 MSFT 00000097)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: MCFG 00000000dff904a0 0003C (v01 7596MS OEMMCFG  20110929 MSFT 00000097)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: OEMB 00000000dff9e040 00072 (v01 7596MS A7596100 20110929 MSFT 00000097)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: HPET 00000000dff9a660 00038 (v01 7596MS OEMHPET  20110929 MSFT 00000097)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: SSDT 00000000dff9a6a0 01714 (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] No NUMA configuration found
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000320000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000320000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   NODE_DATA [000000031fffb000 - 000000031fffffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea000c7fffff] PMD -> [ffff880313600000-ffff88031f5fffff] on node 0
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00320000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000dff90
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00320000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] On node 0 totalpages: 3145503
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA zone: 5 pages reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   DMA32 zone: 896976 pages, LIFO batch:31
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   Normal zone: 34816 pages used for memmap
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]   Normal zone: 2193408 pages, LIFO batch:31
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] enabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x11] lapic_id[0x90] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x12] lapic_id[0x91] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x13] lapic_id[0x92] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x14] lapic_id[0x93] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x15] lapic_id[0x94] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x16] lapic_id[0x95] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x17] lapic_id[0x96] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x18] lapic_id[0x97] disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x18] address[0xfec00000] gsi_base[0])
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 24, version 33, address 0xfec00000, GSI 0-23
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] SMP: Allowing 24 CPUs, 16 hotplug CPUs
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] nr_irqs_gsi: 40
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dff90000 - 00000000dff9e000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dff9e000 - 00000000dffe0000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dffe0000 - 00000000e0000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000ffe00000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1fe00000)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:24 nr_node_ids:1
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880313200000 s83072 r8192 d23424 u131072
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u131072 alloc=1*2097152
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] pcpu-alloc: [0] 16 17 18 19 20 21 22 23 -- -- -- -- -- -- -- -- 
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3094298
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Policy zone: Normal
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=eee1e085-6a87-46ed-8764-c2caf5a5d531 ro quiet splash vt.handoff=7
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Checking aperture...
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] No AGP bridge found
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Node 0: aperture @ 0 size 32 MB
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] This costs you 64 MB of RAM
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ d4000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000d4000000 - 00000000d8000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Memory: 12215000k/13107200k available (6555k kernel code, 525188k absent, 367012k reserved, 6645k data, 920k init)
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=24, Nodes=1
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] NR_IRQS:16640 nr_irqs:872 16
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Console: colour dummy device 80x25
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] console [tty0] enabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] allocated 100663296 bytes of page_cgroup
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] hpet clockevent registered
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 18 13:55:06 tijn-desktop kernel: [    0.000000] Detected 3100.167 MHz processor.
Jul 18 13:55:06 tijn-desktop kernel: [    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6200.33 BogoMIPS (lpj=12400668)
Jul 18 13:55:06 tijn-desktop kernel: [    0.008010] pid_max: default: 32768 minimum: 301
Jul 18 13:55:06 tijn-desktop kernel: [    0.008049] Security Framework initialized
Jul 18 13:55:06 tijn-desktop kernel: [    0.008060] AppArmor: AppArmor initialized
Jul 18 13:55:06 tijn-desktop kernel: [    0.008061] Yama: becoming mindful.
Jul 18 13:55:06 tijn-desktop kernel: [    0.009632] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    0.016359] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    0.018571] Mount-cache hash table entries: 256
Jul 18 13:55:06 tijn-desktop kernel: [    0.018730] Initializing cgroup subsys cpuacct
Jul 18 13:55:06 tijn-desktop kernel: [    0.018738] Initializing cgroup subsys memory
Jul 18 13:55:06 tijn-desktop kernel: [    0.018749] Initializing cgroup subsys devices
Jul 18 13:55:06 tijn-desktop kernel: [    0.018751] Initializing cgroup subsys freezer
Jul 18 13:55:06 tijn-desktop kernel: [    0.018752] Initializing cgroup subsys blkio
Jul 18 13:55:06 tijn-desktop kernel: [    0.018758] Initializing cgroup subsys perf_event
Jul 18 13:55:06 tijn-desktop kernel: [    0.018786] tseg: 0000000000
Jul 18 13:55:06 tijn-desktop kernel: [    0.018798] CPU: Physical Processor ID: 0
Jul 18 13:55:06 tijn-desktop kernel: [    0.018800] CPU: Processor Core ID: 0
Jul 18 13:55:06 tijn-desktop kernel: [    0.018801] mce: CPU supports 7 MCE banks
Jul 18 13:55:06 tijn-desktop kernel: [    0.020238] ACPI: Core revision 20110623
Jul 18 13:55:06 tijn-desktop kernel: [    0.024015] ftrace: allocating 26991 entries in 106 pages
Jul 18 13:55:06 tijn-desktop kernel: [    0.028064] Switched APIC routing to physical flat.
Jul 18 13:55:06 tijn-desktop kernel: [    0.028421] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 18 13:55:06 tijn-desktop kernel: [    0.068357] CPU0: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] Performance Events: AMD Family 15h PMU driver.
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... version:                0
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... bit width:              48
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... generic registers:      6
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... value mask:             0000ffffffffffff
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... max period:             00007fffffffffff
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... fixed-purpose events:   0
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] ... event mask:             000000000000003f
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] Booting Node   0, Processors  #1
Jul 18 13:55:06 tijn-desktop kernel: [    0.072003] smpboot cpu 1: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.160031] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.160130]  #2
Jul 18 13:55:06 tijn-desktop kernel: [    0.160132] smpboot cpu 2: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.252028] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.252096]  #3
Jul 18 13:55:06 tijn-desktop kernel: [    0.252097] smpboot cpu 3: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.344032] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.344097]  #4
Jul 18 13:55:06 tijn-desktop kernel: [    0.344098] smpboot cpu 4: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.436039] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.436110]  #5
Jul 18 13:55:06 tijn-desktop kernel: [    0.436112] smpboot cpu 5: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.528044] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.528114]  #6
Jul 18 13:55:06 tijn-desktop kernel: [    0.528115] smpboot cpu 6: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.620050] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.620123]  #7
Jul 18 13:55:06 tijn-desktop kernel: [    0.620124] smpboot cpu 7: start_ip = 9a000
Jul 18 13:55:06 tijn-desktop kernel: [    0.712055] NMI watchdog enabled, takes one hw-pmu counter.
Jul 18 13:55:06 tijn-desktop kernel: [    0.712073] Brought up 8 CPUs
Jul 18 13:55:06 tijn-desktop kernel: [    0.712076] Total of 8 processors activated (49601.07 BogoMIPS).
Jul 18 13:55:06 tijn-desktop kernel: [    0.716271] devtmpfs: initialized
Jul 18 13:55:06 tijn-desktop kernel: [    0.720640] EVM: security.selinux
Jul 18 13:55:06 tijn-desktop kernel: [    0.720641] EVM: security.SMACK64
Jul 18 13:55:06 tijn-desktop kernel: [    0.720643] EVM: security.capability
Jul 18 13:55:06 tijn-desktop kernel: [    0.720679] PM: Registering ACPI NVS region at dff9e000 (270336 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    0.720787] print_constraints: dummy: 
Jul 18 13:55:06 tijn-desktop kernel: [    0.720818] RTC time: 11:54:44, date: 07/18/12
Jul 18 13:55:06 tijn-desktop kernel: [    0.720856] NET: Registered protocol family 16
Jul 18 13:55:06 tijn-desktop kernel: [    0.720980] Extended Config Space enabled on 1 nodes
Jul 18 13:55:06 tijn-desktop kernel: [    0.721419] Trying to unpack rootfs image as initramfs...
Jul 18 13:55:06 tijn-desktop kernel: [    0.721006] ACPI: bus type pci registered
Jul 18 13:55:06 tijn-desktop kernel: [    0.721074] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 18 13:55:06 tijn-desktop kernel: [    0.721076] PCI: not using MMCONFIG
Jul 18 13:55:06 tijn-desktop kernel: [    0.721078] PCI: Using configuration type 1 for base access
Jul 18 13:55:06 tijn-desktop kernel: [    0.721080] PCI: Using configuration type 1 for extended access
Jul 18 13:55:06 tijn-desktop kernel: [    0.722134] bio: create slab <bio-0> at 0
Jul 18 13:55:06 tijn-desktop kernel: [    0.722134] ACPI: Added _OSI(Module Device)
Jul 18 13:55:06 tijn-desktop kernel: [    0.722134] ACPI: Added _OSI(Processor Device)
Jul 18 13:55:06 tijn-desktop kernel: [    0.722134] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 18 13:55:06 tijn-desktop kernel: [    0.722134] ACPI: Added _OSI(Processor Aggregator Device)
Jul 18 13:55:06 tijn-desktop kernel: [    0.724075] ACPI: EC: Detected MSI hardware, enabling workarounds.
Jul 18 13:55:06 tijn-desktop kernel: [    0.724077] ACPI: EC: Look up EC in DSDT
Jul 18 13:55:06 tijn-desktop kernel: [    0.725774] ACPI: Executed 4 blocks of module-level executable AML code
Jul 18 13:55:06 tijn-desktop kernel: [    0.760428] ACPI: Interpreter enabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.760432] ACPI: (supports S0 S1 S4 S5)
Jul 18 13:55:06 tijn-desktop kernel: [    0.760455] ACPI: Using IOAPIC for interrupt routing
Jul 18 13:55:06 tijn-desktop kernel: [    0.760482] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 18 13:55:06 tijn-desktop kernel: [    0.761514] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jul 18 13:55:06 tijn-desktop kernel: [    0.953173] ACPI: No dock devices found.
Jul 18 13:55:06 tijn-desktop kernel: [    0.953176] HEST: Table not found.
Jul 18 13:55:06 tijn-desktop kernel: [    0.953180] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 18 13:55:06 tijn-desktop kernel: [    0.953291] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 18 13:55:06 tijn-desktop kernel: [    0.953506] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953508] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953511] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953513] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953516] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953530] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.953587] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jul 18 13:55:06 tijn-desktop kernel: [    0.953624] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jul 18 13:55:06 tijn-desktop kernel: [    0.953627] pci 0000:00:02.0: PME# disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.953644] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
Jul 18 13:55:06 tijn-desktop kernel: [    0.953679] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 18 13:55:06 tijn-desktop kernel: [    0.953682] pci 0000:00:05.0: PME# disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.953721] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jul 18 13:55:06 tijn-desktop kernel: [    0.953743] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953753] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953763] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953773] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953783] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953793] pci 0000:00:11.0: reg 24: [mem 0xfcfffc00-0xfcffffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953814] pci 0000:00:11.0: set SATA to AHCI mode
Jul 18 13:55:06 tijn-desktop kernel: [    0.953873] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.953887] pci 0000:00:12.0: reg 10: [mem 0xfcffe000-0xfcffefff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.953954] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.953967] pci 0000:00:12.1: reg 10: [mem 0xfcffd000-0xfcffdfff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954040] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.954060] pci 0000:00:12.2: reg 10: [mem 0xfcfff800-0xfcfff8ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954145] pci 0000:00:12.2: supports D1 D2
Jul 18 13:55:06 tijn-desktop kernel: [    0.954147] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 18 13:55:06 tijn-desktop kernel: [    0.954151] pci 0000:00:12.2: PME# disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.954175] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.954189] pci 0000:00:13.0: reg 10: [mem 0xfcffc000-0xfcffcfff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954255] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.954269] pci 0000:00:13.1: reg 10: [mem 0xfcffb000-0xfcffbfff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954341] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.954361] pci 0000:00:13.2: reg 10: [mem 0xfcfff400-0xfcfff4ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954446] pci 0000:00:13.2: supports D1 D2
Jul 18 13:55:06 tijn-desktop kernel: [    0.954448] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 18 13:55:06 tijn-desktop kernel: [    0.954452] pci 0000:00:13.2: PME# disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.954477] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jul 18 13:55:06 tijn-desktop kernel: [    0.954580] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jul 18 13:55:06 tijn-desktop kernel: [    0.954597] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954606] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954616] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954626] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954636] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954696] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jul 18 13:55:06 tijn-desktop kernel: [    0.954718] pci 0000:00:14.2: reg 10: [mem 0xfcff4000-0xfcff7fff 64bit]
Jul 18 13:55:06 tijn-desktop kernel: [    0.954786] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 18 13:55:06 tijn-desktop kernel: [    0.954790] pci 0000:00:14.2: PME# disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.954803] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jul 18 13:55:06 tijn-desktop kernel: [    0.954881] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jul 18 13:55:06 tijn-desktop kernel: [    0.954927] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jul 18 13:55:06 tijn-desktop kernel: [    0.954941] pci 0000:00:14.5: reg 10: [mem 0xfcffa000-0xfcffafff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.955011] pci 0000:00:18.0: [1022:1600] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.955031] pci 0000:00:18.1: [1022:1601] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.955046] pci 0000:00:18.2: [1022:1602] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.955061] pci 0000:00:18.3: [1022:1603] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.955081] pci 0000:00:18.4: [1022:1604] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.955096] pci 0000:00:18.5: [1022:1605] type 0 class 0x000600
Jul 18 13:55:06 tijn-desktop kernel: [    0.955155] pci 0000:01:00.0: [10de:0de1] type 0 class 0x000300
Jul 18 13:55:06 tijn-desktop kernel: [    0.955165] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.955176] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.955187] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.955195] pci 0000:01:00.0: reg 24: [io  0xd800-0xd87f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.955202] pci 0000:01:00.0: reg 30: [mem 0xfea80000-0xfeafffff pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.955261] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
Jul 18 13:55:06 tijn-desktop kernel: [    0.955271] pci 0000:01:00.1: reg 10: [mem 0xfea7c000-0xfea7ffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960077] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960081] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960084] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfeafffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960088] pci 0000:00:02.0:   bridge window [mem 0xf0000000-0xf9ffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960127] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
Jul 18 13:55:06 tijn-desktop kernel: [    0.960140] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960162] pci 0000:02:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960177] pci 0000:02:00.0: reg 20: [mem 0xfbff8000-0xfbffbfff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960186] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.960235] pci 0000:02:00.0: supports D1 D2
Jul 18 13:55:06 tijn-desktop kernel: [    0.960236] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 18 13:55:06 tijn-desktop kernel: [    0.960241] pci 0000:02:00.0: PME# disabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.968074] pci 0000:00:05.0: PCI bridge to [bus 02-02]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968078] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968081] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968085] pci 0000:00:05.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968148] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968158] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968162] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968165] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968167] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968170] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968412] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jul 18 13:55:06 tijn-desktop kernel: [    0.968577]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul 18 13:55:06 tijn-desktop kernel: [    0.968580]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jul 18 13:55:06 tijn-desktop kernel: [    0.968582] ACPI _OSC control for PCIe not granted, disabling ASPM
Jul 18 13:55:06 tijn-desktop kernel: [    0.974030] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
Jul 18 13:55:06 tijn-desktop kernel: [    0.974072] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
Jul 18 13:55:06 tijn-desktop kernel: [    0.974112] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
Jul 18 13:55:06 tijn-desktop kernel: [    0.974158] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
Jul 18 13:55:06 tijn-desktop kernel: [    0.974197] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 18 13:55:06 tijn-desktop kernel: [    0.974236] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 18 13:55:06 tijn-desktop kernel: [    0.974276] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *10 11 12 14 15)
Jul 18 13:55:06 tijn-desktop kernel: [    0.974315] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jul 18 13:55:06 tijn-desktop kernel: [    0.974404] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 18 13:55:06 tijn-desktop kernel: [    0.974404] vgaarb: loaded
Jul 18 13:55:06 tijn-desktop kernel: [    0.974404] vgaarb: bridge control possible 0000:01:00.0
Jul 18 13:55:06 tijn-desktop kernel: [    0.974404] i2c-core: driver [aat2870] using legacy suspend method
Jul 18 13:55:06 tijn-desktop kernel: [    0.974404] i2c-core: driver [aat2870] using legacy resume method
Jul 18 13:55:06 tijn-desktop kernel: [    0.974404] SCSI subsystem initialized
Jul 18 13:55:06 tijn-desktop kernel: [    0.974504] libata version 3.00 loaded.
Jul 18 13:55:06 tijn-desktop kernel: [    0.974504] usbcore: registered new interface driver usbfs
Jul 18 13:55:06 tijn-desktop kernel: [    0.974504] usbcore: registered new interface driver hub
Jul 18 13:55:06 tijn-desktop kernel: [    0.974504] usbcore: registered new device driver usb
Jul 18 13:55:06 tijn-desktop kernel: [    0.974504] PCI: Using ACPI for IRQ routing
Jul 18 13:55:06 tijn-desktop kernel: [    0.983722] PCI: pci_cache_line_size set to 64 bytes
Jul 18 13:55:06 tijn-desktop kernel: [    0.983797] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jul 18 13:55:06 tijn-desktop kernel: [    0.983800] reserve RAM buffer: 00000000dff90000 - 00000000dfffffff 
Jul 18 13:55:06 tijn-desktop kernel: [    0.983892] NetLabel: Initializing
Jul 18 13:55:06 tijn-desktop kernel: [    0.983893] NetLabel:  domain hash size = 128
Jul 18 13:55:06 tijn-desktop kernel: [    0.983895] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 18 13:55:06 tijn-desktop kernel: [    0.983905] NetLabel:  unlabeled traffic allowed by default
Jul 18 13:55:06 tijn-desktop kernel: [    0.983929] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 18 13:55:06 tijn-desktop kernel: [    0.983929] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 18 13:55:06 tijn-desktop kernel: [    0.985096] Switching to clocksource hpet
Jul 18 13:55:06 tijn-desktop kernel: [    0.990855] AppArmor: AppArmor Filesystem Enabled
Jul 18 13:55:06 tijn-desktop kernel: [    0.990871] pnp: PnP ACPI init
Jul 18 13:55:06 tijn-desktop kernel: [    0.990885] ACPI: bus type pnp registered
Jul 18 13:55:06 tijn-desktop kernel: [    0.991006] pnp 00:00: [bus 00-ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991009] pnp 00:00: [io  0x0cf8-0x0cff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991011] pnp 00:00: [io  0x0000-0x0cf7 window]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991013] pnp 00:00: [io  0x0d00-0xffff window]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991015] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991017] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991019] pnp 00:00: [mem 0xe0000000-0xdfffffff window disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991021] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991067] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.991157] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991160] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991206] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.991251] pnp 00:02: [dma 4]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991252] pnp 00:02: [io  0x0000-0x000f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991254] pnp 00:02: [io  0x0081-0x0083]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991256] pnp 00:02: [io  0x0087]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991258] pnp 00:02: [io  0x0089-0x008b]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991259] pnp 00:02: [io  0x008f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991261] pnp 00:02: [io  0x00c0-0x00df]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991291] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.991301] pnp 00:03: [io  0x0070-0x0071]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991312] pnp 00:03: [irq 8]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991342] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.991350] pnp 00:04: [io  0x0061]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991378] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.991386] pnp 00:05: [io  0x00f0-0x00ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991394] pnp 00:05: [irq 13]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991424] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.991677] pnp 00:06: [io  0x03f8-0x03ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991681] pnp 00:06: [irq 4]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991683] pnp 00:06: [dma 0 disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.991745] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.992199] pnp 00:07: [io  0x0378-0x037f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992203] pnp 00:07: [irq 7]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992205] pnp 00:07: [dma 0 disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992335] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.992360] pnp 00:08: [mem 0xfed00000-0xfed003ff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992392] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.992482] pnp 00:09: [io  0x0060]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992484] pnp 00:09: [io  0x0064]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992486] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992488] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992538] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992541] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992544] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.992720] pnp 00:0a: [io  0x0010-0x001f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992721] pnp 00:0a: [io  0x0022-0x003f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992723] pnp 00:0a: [io  0x0062-0x0063]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992725] pnp 00:0a: [io  0x0065-0x006f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992726] pnp 00:0a: [io  0x0072-0x007f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992728] pnp 00:0a: [io  0x0080]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992730] pnp 00:0a: [io  0x0084-0x0086]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992731] pnp 00:0a: [io  0x0088]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992733] pnp 00:0a: [io  0x008c-0x008e]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992735] pnp 00:0a: [io  0x0090-0x009f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992736] pnp 00:0a: [io  0x00a2-0x00bf]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992738] pnp 00:0a: [io  0x00b1]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992739] pnp 00:0a: [io  0x00e0-0x00ef]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992741] pnp 00:0a: [io  0x04d0-0x04d1]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992743] pnp 00:0a: [io  0x040b]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992744] pnp 00:0a: [io  0x04d6]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992746] pnp 00:0a: [io  0x0c00-0x0c01]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992748] pnp 00:0a: [io  0x0c14]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992749] pnp 00:0a: [io  0x0c50-0x0c51]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992751] pnp 00:0a: [io  0x0c52]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992752] pnp 00:0a: [io  0x0c6c]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992754] pnp 00:0a: [io  0x0c6f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992757] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992759] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992761] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992762] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992764] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992766] pnp 00:0a: [io  0x0800-0x089f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992767] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992769] pnp 00:0a: [io  0x0b00-0x0b0f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992771] pnp 00:0a: [io  0x0b20-0x0b3f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992773] pnp 00:0a: [io  0x0900-0x090f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992774] pnp 00:0a: [io  0x0910-0x091f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992776] pnp 00:0a: [io  0xfe00-0xfefe]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992778] pnp 00:0a: [io  0x0060]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992779] pnp 00:0a: [io  0x0064]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992781] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992783] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.992856] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992859] system 00:0a: [io  0x040b] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992861] system 00:0a: [io  0x04d6] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992863] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992865] system 00:0a: [io  0x0c14] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992868] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992870] system 00:0a: [io  0x0c52] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992872] system 00:0a: [io  0x0c6c] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992874] system 00:0a: [io  0x0c6f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992876] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992878] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992881] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992885] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992887] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992890] system 00:0a: [io  0x0800-0x089f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992892] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992894] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992897] system 00:0a: [io  0x0900-0x090f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992899] system 00:0a: [io  0x0910-0x091f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992901] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992904] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992906] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.992909] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.993056] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jul 18 13:55:06 tijn-desktop kernel: [    0.993058] pnp 00:0b: [io  0x0e80-0x0f5f]
Jul 18 13:55:06 tijn-desktop kernel: [    0.993059] pnp 00:0b: [io  0x0ae0-0x0aef]
Jul 18 13:55:06 tijn-desktop kernel: [    0.993105] system 00:0b: [io  0x0e80-0x0f5f] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.993108] system 00:0b: [io  0x0ae0-0x0aef] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.993110] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    0.993158] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jul 18 13:55:06 tijn-desktop kernel: [    0.993204] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jul 18 13:55:06 tijn-desktop kernel: [    0.993207] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    1.032506] Freeing initrd memory: 20300k freed
Jul 18 13:55:06 tijn-desktop kernel: [    1.092522] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.092526] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.092528] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.092530] pnp 00:0d: [mem 0x00100000-0xdfffffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.092532] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.092625] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jul 18 13:55:06 tijn-desktop kernel: [    1.092628] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jul 18 13:55:06 tijn-desktop kernel: [    1.092631] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jul 18 13:55:06 tijn-desktop kernel: [    1.092633] system 00:0d: [mem 0x00100000-0xdfffffff] could not be reserved
Jul 18 13:55:06 tijn-desktop kernel: [    1.092636] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jul 18 13:55:06 tijn-desktop kernel: [    1.092639] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 18 13:55:06 tijn-desktop kernel: [    1.092751] pnp: PnP ACPI: found 14 devices
Jul 18 13:55:06 tijn-desktop kernel: [    1.092753] ACPI: ACPI bus type pnp unregistered
Jul 18 13:55:06 tijn-desktop kernel: [    1.099699] PCI: max bus depth: 1 pci_try_num: 2
Jul 18 13:55:06 tijn-desktop kernel: [    1.099714] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099717] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099720] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfeafffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099723] pci 0000:00:02.0:   bridge window [mem 0xf0000000-0xf9ffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099727] pci 0000:00:05.0: PCI bridge to [bus 02-02]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099730] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099733] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099736] pci 0000:00:05.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099739] pci 0000:00:14.4: PCI bridge to [bus 03-03]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099763] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    1.099767] pci 0000:00:02.0: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    1.099777] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 18 13:55:06 tijn-desktop kernel: [    1.099780] pci 0000:00:05.0: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    1.099788] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099790] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099792] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099794] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099797] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfebfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099799] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099801] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfeafffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099803] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf9ffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099806] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099808] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099810] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099812] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099814] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099816] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099819] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099821] pci_bus 0000:03: resource 8 [mem 0xf0000000-0xfebfffff]
Jul 18 13:55:06 tijn-desktop kernel: [    1.099856] NET: Registered protocol family 2
Jul 18 13:55:06 tijn-desktop kernel: [    1.100360] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    1.102091] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    1.104225] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    1.104473] TCP: Hash tables configured (established 524288 bind 65536)
Jul 18 13:55:06 tijn-desktop kernel: [    1.104475] TCP reno registered
Jul 18 13:55:06 tijn-desktop kernel: [    1.104504] UDP hash table entries: 8192 (order: 6, 262144 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    1.104595] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    1.104779] NET: Registered protocol family 1
Jul 18 13:55:06 tijn-desktop kernel: [    1.104822] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 13:55:06 tijn-desktop kernel: [    1.208032] pci 0000:00:12.0: PCI INT A disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.208042] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 13:55:06 tijn-desktop kernel: [    1.288029] pci 0000:00:12.1: PCI INT A disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.288039] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 18 13:55:06 tijn-desktop kernel: [    1.288085] pci 0000:00:12.2: PCI INT B disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.288092] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    1.368029] pci 0000:00:13.0: PCI INT A disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.368037] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    1.448031] pci 0000:00:13.1: PCI INT A disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.448046] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 18 13:55:06 tijn-desktop kernel: [    1.448092] pci 0000:00:13.2: PCI INT B disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.448109] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    1.528031] pci 0000:00:14.5: PCI INT C disabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.528057] pci 0000:01:00.0: Boot video device
Jul 18 13:55:06 tijn-desktop kernel: [    1.528070] PCI: CLS 64 bytes, default 64
Jul 18 13:55:06 tijn-desktop kernel: [    1.528582] PCI-DMA: Disabling AGP.
Jul 18 13:55:06 tijn-desktop kernel: [    1.528704] PCI-DMA: aperture base @ d4000000 size 65536 KB
Jul 18 13:55:06 tijn-desktop kernel: [    1.528705] PCI-DMA: using GART IOMMU.
Jul 18 13:55:06 tijn-desktop kernel: [    1.528708] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jul 18 13:55:06 tijn-desktop kernel: [    1.533794] perf: AMD IBS detected (0x000000ff)
Jul 18 13:55:06 tijn-desktop kernel: [    1.533985] audit: initializing netlink socket (disabled)
Jul 18 13:55:06 tijn-desktop kernel: [    1.533994] type=2000 audit(1342612484.528:1): initialized
Jul 18 13:55:06 tijn-desktop kernel: [    1.572313] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 18 13:55:06 tijn-desktop kernel: [    1.614690] VFS: Disk quotas dquot_6.5.2
Jul 18 13:55:06 tijn-desktop kernel: [    1.614749] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 18 13:55:06 tijn-desktop kernel: [    1.615274] fuse init (API version 7.17)
Jul 18 13:55:06 tijn-desktop kernel: [    1.615367] msgmni has been set to 24025
Jul 18 13:55:06 tijn-desktop kernel: [    1.615831] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 18 13:55:06 tijn-desktop kernel: [    1.615880] io scheduler noop registered
Jul 18 13:55:06 tijn-desktop kernel: [    1.615882] io scheduler deadline registered
Jul 18 13:55:06 tijn-desktop kernel: [    1.615913] io scheduler cfq registered (default)
Jul 18 13:55:06 tijn-desktop kernel: [    1.616034] pcieport 0000:00:02.0: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    1.616064] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jul 18 13:55:06 tijn-desktop kernel: [    1.616104] pcieport 0000:00:05.0: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    1.616128] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
Jul 18 13:55:06 tijn-desktop kernel: [    1.616186] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 18 13:55:06 tijn-desktop kernel: [    1.616210] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 18 13:55:06 tijn-desktop kernel: [    1.616322] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jul 18 13:55:06 tijn-desktop kernel: [    1.616327] ACPI: Power Button [PWRB]
Jul 18 13:55:06 tijn-desktop kernel: [    1.616363] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 18 13:55:06 tijn-desktop kernel: [    1.616366] ACPI: Power Button [PWRF]
Jul 18 13:55:06 tijn-desktop kernel: [    1.616443] ACPI: acpi_idle registered with cpuidle
Jul 18 13:55:06 tijn-desktop kernel: [    1.824343] ERST: Table is not found!
Jul 18 13:55:06 tijn-desktop kernel: [    1.824345] GHES: HEST is not enabled!
Jul 18 13:55:06 tijn-desktop kernel: [    1.824424] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 18 13:55:06 tijn-desktop kernel: [    1.844899] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 18 13:55:06 tijn-desktop kernel: [    1.952598] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 18 13:55:06 tijn-desktop kernel: [    1.988284] Linux agpgart interface v0.103
Jul 18 13:55:06 tijn-desktop kernel: [    1.989792] brd: module loaded
Jul 18 13:55:06 tijn-desktop kernel: [    1.990578] loop: module loaded
Jul 18 13:55:06 tijn-desktop kernel: [    1.990703] ahci 0000:00:11.0: version 3.0
Jul 18 13:55:06 tijn-desktop kernel: [    1.990725] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 18 13:55:06 tijn-desktop kernel: [    1.990796] ahci 0000:00:11.0: irq 42 for MSI/MSI-X
Jul 18 13:55:06 tijn-desktop kernel: [    1.990873] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 18 13:55:06 tijn-desktop kernel: [    1.990876] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Jul 18 13:55:06 tijn-desktop kernel: [    1.991360] scsi0 : ahci
Jul 18 13:55:06 tijn-desktop kernel: [    1.991449] scsi1 : ahci
Jul 18 13:55:06 tijn-desktop kernel: [    1.991517] scsi2 : ahci
Jul 18 13:55:06 tijn-desktop kernel: [    1.991587] scsi3 : ahci
Jul 18 13:55:06 tijn-desktop kernel: [    1.991702] ata1: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd00 irq 42
Jul 18 13:55:06 tijn-desktop kernel: [    1.991705] ata2: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd80 irq 42
Jul 18 13:55:06 tijn-desktop kernel: [    1.991708] ata3: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe00 irq 42
Jul 18 13:55:06 tijn-desktop kernel: [    1.991712] ata4: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe80 irq 42
Jul 18 13:55:06 tijn-desktop kernel: [    1.991799] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 13:55:06 tijn-desktop kernel: [    1.991821] pata_acpi 0000:00:14.1: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    1.992116] Fixed MDIO Bus: probed
Jul 18 13:55:06 tijn-desktop kernel: [    1.992132] tun: Universal TUN/TAP device driver, 1.6
Jul 18 13:55:06 tijn-desktop kernel: [    1.992134] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 18 13:55:06 tijn-desktop kernel: [    1.992184] PPP generic driver version 2.4.2
Jul 18 13:55:06 tijn-desktop kernel: [    1.992269] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 18 13:55:06 tijn-desktop kernel: [    1.992283] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 18 13:55:06 tijn-desktop kernel: [    1.992295] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    1.992341] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 18 13:55:06 tijn-desktop kernel: [    1.992349] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 18 13:55:06 tijn-desktop kernel: [    1.992372] ehci_hcd 0000:00:12.2: debug port 1
Jul 18 13:55:06 tijn-desktop kernel: [    1.992390] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfcfff800
Jul 18 13:55:06 tijn-desktop kernel: [    2.004035] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 18 13:55:06 tijn-desktop kernel: [    2.004149] hub 1-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.004153] hub 1-0:1.0: 6 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.004235] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 18 13:55:06 tijn-desktop kernel: [    2.004249] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    2.004290] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 18 13:55:06 tijn-desktop kernel: [    2.004297] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 18 13:55:06 tijn-desktop kernel: [    2.004315] ehci_hcd 0000:00:13.2: debug port 1
Jul 18 13:55:06 tijn-desktop kernel: [    2.004334] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfcfff400
Jul 18 13:55:06 tijn-desktop kernel: [    2.016027] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 18 13:55:06 tijn-desktop kernel: [    2.016133] hub 2-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.016136] hub 2-0:1.0: 6 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.016209] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 18 13:55:06 tijn-desktop kernel: [    2.016224] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 13:55:06 tijn-desktop kernel: [    2.016238] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    2.016278] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 18 13:55:06 tijn-desktop kernel: [    2.016299] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfcffe000
Jul 18 13:55:06 tijn-desktop kernel: [    2.076119] hub 3-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.076129] hub 3-0:1.0: 3 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.076192] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 13:55:06 tijn-desktop kernel: [    2.076205] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    2.076248] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 18 13:55:06 tijn-desktop kernel: [    2.076261] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfcffd000
Jul 18 13:55:06 tijn-desktop kernel: [    2.136118] hub 4-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.136127] hub 4-0:1.0: 3 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.136190] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    2.136204] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    2.136246] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 18 13:55:06 tijn-desktop kernel: [    2.136266] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfcffc000
Jul 18 13:55:06 tijn-desktop kernel: [    2.196122] hub 5-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.196132] hub 5-0:1.0: 3 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.196195] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    2.196209] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    2.196254] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 18 13:55:06 tijn-desktop kernel: [    2.196269] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfcffb000
Jul 18 13:55:06 tijn-desktop kernel: [    2.256123] hub 6-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.256133] hub 6-0:1.0: 3 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.256196] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    2.256210] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jul 18 13:55:06 tijn-desktop kernel: [    2.256253] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Jul 18 13:55:06 tijn-desktop kernel: [    2.256267] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfcffa000
Jul 18 13:55:06 tijn-desktop kernel: [    2.308082] ata4: SATA link down (SStatus 0 SControl 300)
Jul 18 13:55:06 tijn-desktop kernel: [    2.308116] ata3: SATA link down (SStatus 0 SControl 300)
Jul 18 13:55:06 tijn-desktop kernel: [    2.316035] usb 1-3: new high-speed USB device number 2 using ehci_hcd
Jul 18 13:55:06 tijn-desktop kernel: [    2.316127] hub 7-0:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.316134] hub 7-0:1.0: 2 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.316187] uhci_hcd: USB Universal Host Controller Interface driver
Jul 18 13:55:06 tijn-desktop kernel: [    2.316261] usbcore: registered new interface driver libusual
Jul 18 13:55:06 tijn-desktop kernel: [    2.316296] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jul 18 13:55:06 tijn-desktop kernel: [    2.316653] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 18 13:55:06 tijn-desktop kernel: [    2.316660] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 18 13:55:06 tijn-desktop kernel: [    2.316796] mousedev: PS/2 mouse device common for all mice
Jul 18 13:55:06 tijn-desktop kernel: [    2.316929] rtc_cmos 00:03: RTC can wake from S4
Jul 18 13:55:06 tijn-desktop kernel: [    2.317027] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 18 13:55:06 tijn-desktop kernel: [    2.317052] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul 18 13:55:06 tijn-desktop kernel: [    2.317122] device-mapper: uevent: version 1.0.3
Jul 18 13:55:06 tijn-desktop kernel: [    2.317189] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jul 18 13:55:06 tijn-desktop kernel: [    2.317331] cpuidle: using governor ladder
Jul 18 13:55:06 tijn-desktop kernel: [    2.317573] cpuidle: using governor menu
Jul 18 13:55:06 tijn-desktop kernel: [    2.317575] EFI Variables Facility v0.08 2004-May-17
Jul 18 13:55:06 tijn-desktop kernel: [    2.317773] TCP cubic registered
Jul 18 13:55:06 tijn-desktop kernel: [    2.317872] NET: Registered protocol family 10
Jul 18 13:55:06 tijn-desktop kernel: [    2.318324] NET: Registered protocol family 17
Jul 18 13:55:06 tijn-desktop kernel: [    2.318327] Registering the dns_resolver key type
Jul 18 13:55:06 tijn-desktop kernel: [    2.318468] PM: Hibernation image not present or could not be loaded.
Jul 18 13:55:06 tijn-desktop kernel: [    2.318477] registered taskstats version 1
Jul 18 13:55:06 tijn-desktop kernel: [    2.345498]   Magic number: 4:415:934
Jul 18 13:55:06 tijn-desktop kernel: [    2.345606] rtc_cmos 00:03: setting system clock to 2012-07-18 11:54:46 UTC (1342612486)
Jul 18 13:55:06 tijn-desktop kernel: [    2.345673] powernow-k8: Found 1 AMD FX(tm)-8120 Eight-Core Processor            (8 cpu cores) (version 2.20.00)
Jul 18 13:55:06 tijn-desktop kernel: [    2.345718] powernow-k8: Core Performance Boosting: on.
Jul 18 13:55:06 tijn-desktop kernel: [    2.345774] powernow-k8:    0 : pstate 0 (3100 MHz)
Jul 18 13:55:06 tijn-desktop kernel: [    2.345775] powernow-k8:    1 : pstate 1 (2800 MHz)
Jul 18 13:55:06 tijn-desktop kernel: [    2.345777] powernow-k8:    2 : pstate 2 (2300 MHz)
Jul 18 13:55:06 tijn-desktop kernel: [    2.345779] powernow-k8:    3 : pstate 3 (1900 MHz)
Jul 18 13:55:06 tijn-desktop kernel: [    2.345780] powernow-k8:    4 : pstate 4 (1400 MHz)
Jul 18 13:55:06 tijn-desktop kernel: [    2.346631] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 18 13:55:06 tijn-desktop kernel: [    2.346634] EDD information not available.
Jul 18 13:55:06 tijn-desktop kernel: [    2.449476] hub 1-3:1.0: USB hub found
Jul 18 13:55:06 tijn-desktop kernel: [    2.449573] hub 1-3:1.0: 4 ports detected
Jul 18 13:55:06 tijn-desktop kernel: [    2.480061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 18 13:55:06 tijn-desktop kernel: [    2.480087] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 18 13:55:06 tijn-desktop kernel: [    2.481267] ata1.00: ATA-8: ST500DM002-1BD142, KC44, max UDMA/133
Jul 18 13:55:06 tijn-desktop kernel: [    2.481270] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 18 13:55:06 tijn-desktop kernel: [    2.482538] ata2.00: ATAPI: ATAPI   iHAS122, ZL0F, max UDMA/100
Jul 18 13:55:06 tijn-desktop kernel: [    2.482759] ata1.00: configured for UDMA/133
Jul 18 13:55:06 tijn-desktop kernel: [    2.482922] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC44 PQ: 0 ANSI: 5
Jul 18 13:55:06 tijn-desktop kernel: [    2.483074] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 18 13:55:06 tijn-desktop kernel: [    2.483078] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 18 13:55:06 tijn-desktop kernel: [    2.483082] sd 0:0:0:0: [sda] 4096-byte physical blocks
Jul 18 13:55:06 tijn-desktop kernel: [    2.483119] sd 0:0:0:0: [sda] Write Protect is off
Jul 18 13:55:06 tijn-desktop kernel: [    2.483122] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 18 13:55:06 tijn-desktop kernel: [    2.483146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 18 13:55:06 tijn-desktop kernel: [    2.483338] ata2.00: configured for UDMA/100
Jul 18 13:55:06 tijn-desktop kernel: [    2.485267] scsi 1:0:0:0: CD-ROM            ATAPI    iHAS122          ZL0F PQ: 0 ANSI: 5
Jul 18 13:55:06 tijn-desktop kernel: [    2.488608] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 18 13:55:06 tijn-desktop kernel: [    2.488612] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 18 13:55:06 tijn-desktop kernel: [    2.488724] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 18 13:55:06 tijn-desktop kernel: [    2.488804] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 18 13:55:06 tijn-desktop kernel: [    2.524418]  sda: sda1 sda2 < sda5 >
Jul 18 13:55:06 tijn-desktop kernel: [    2.524736] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 18 13:55:06 tijn-desktop kernel: [    2.527171] Freeing unused kernel memory: 920k freed
Jul 18 13:55:06 tijn-desktop kernel: [    2.527361] Write protecting the kernel read-only data: 12288k
Jul 18 13:55:06 tijn-desktop kernel: [    2.532059] Refined TSC clocksource calibration: 3100.127 MHz.
Jul 18 13:55:06 tijn-desktop kernel: [    2.532064] Switching to clocksource tsc
Jul 18 13:55:06 tijn-desktop kernel: [    2.535027] Freeing unused kernel memory: 1616k freed
Jul 18 13:55:06 tijn-desktop kernel: [    2.540796] Freeing unused kernel memory: 1200k freed
Jul 18 13:55:06 tijn-desktop kernel: [    2.579043] wmi: Mapper loaded
Jul 18 13:55:06 tijn-desktop kernel: [    2.580983] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 18 13:55:06 tijn-desktop kernel: [    2.581017] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 18 13:55:06 tijn-desktop kernel: [    2.581049] r8169 0000:02:00.0: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    2.581102] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
Jul 18 13:55:06 tijn-desktop kernel: [    2.584765] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc900125ca000, 8c:89:a5:81:ce:04, XID 081000c0 IRQ 43
Jul 18 13:55:06 tijn-desktop kernel: [    2.584770] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jul 18 13:55:06 tijn-desktop kernel: [    2.587069] [drm] Initialized drm 1.1.0 20060810
Jul 18 13:55:06 tijn-desktop kernel: [    2.592869] nouveau 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 13:55:06 tijn-desktop kernel: [    2.592876] nouveau 0000:01:00.0: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [    2.593197] scsi4 : pata_atiixp
Jul 18 13:55:06 tijn-desktop kernel: [    2.593273] scsi5 : pata_atiixp
Jul 18 13:55:06 tijn-desktop kernel: [    2.593410] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jul 18 13:55:06 tijn-desktop kernel: [    2.593413] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jul 18 13:55:06 tijn-desktop kernel: [    2.594224] [drm] nouveau 0000:01:00.0: Detected an NVc0 generation card (0x0c1080a1)
Jul 18 13:55:06 tijn-desktop kernel: [    2.598562] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Jul 18 13:55:06 tijn-desktop kernel: [    2.665380] [drm] nouveau 0000:01:00.0: ... appears to be valid
Jul 18 13:55:06 tijn-desktop kernel: [    2.665383] [drm] nouveau 0000:01:00.0: BIT BIOS found
Jul 18 13:55:06 tijn-desktop kernel: [    2.665386] [drm] nouveau 0000:01:00.0: Bios version 70.08.29.00
Jul 18 13:55:06 tijn-desktop kernel: [    2.665389] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
Jul 18 13:55:06 tijn-desktop kernel: [    2.665391] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Jul 18 13:55:06 tijn-desktop kernel: [    2.665394] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000302 00020030
Jul 18 13:55:06 tijn-desktop kernel: [    2.665397] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02000300 00000000
Jul 18 13:55:06 tijn-desktop kernel: [    2.665399] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 08011392 00020020
Jul 18 13:55:06 tijn-desktop kernel: [    2.665401] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 04022310 00000000
Jul 18 13:55:06 tijn-desktop kernel: [    2.665404] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Jul 18 13:55:06 tijn-desktop kernel: [    2.665406] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Jul 18 13:55:06 tijn-desktop kernel: [    2.665409] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
Jul 18 13:55:06 tijn-desktop kernel: [    2.665411] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
Jul 18 13:55:06 tijn-desktop kernel: [    2.665415] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x6BB6
Jul 18 13:55:06 tijn-desktop kernel: [    2.685418] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x71FC
Jul 18 13:55:06 tijn-desktop kernel: [    2.692421] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x8391
Jul 18 13:55:06 tijn-desktop kernel: [    2.692423] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x8395
Jul 18 13:55:06 tijn-desktop kernel: [    2.692474] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x847D
Jul 18 13:55:06 tijn-desktop kernel: [    2.692476] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x84E2
Jul 18 13:55:06 tijn-desktop kernel: [    2.712323] [drm] nouveau 0000:01:00.0: 0x6B29: Condition still not met after 20ms, skipping following opcodes
Jul 18 13:55:06 tijn-desktop kernel: [    2.828030] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jul 18 13:55:06 tijn-desktop kernel: [    3.005217] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input2
Jul 18 13:55:06 tijn-desktop kernel: [    3.005313] generic-usb 0003:04F2:0760.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony USB Keyboard] on usb-0000:00:12.1-1/input0
Jul 18 13:55:06 tijn-desktop kernel: [    3.016074] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input3
Jul 18 13:55:06 tijn-desktop kernel: [    3.016212] generic-usb 0003:04F2:0760.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony USB Keyboard] on usb-0000:00:12.1-1/input1
Jul 18 13:55:06 tijn-desktop kernel: [    3.016225] usbcore: registered new interface driver usbhid
Jul 18 13:55:06 tijn-desktop kernel: [    3.016227] usbhid: USB HID core driver
Jul 18 13:55:06 tijn-desktop kernel: [    3.192061] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
Jul 18 13:55:06 tijn-desktop kernel: [    3.192066] [drm] nouveau 0000:01:00.0: 0: core 50MHz shader 101MHz memory 135MHz timing 0 voltage 880mV
Jul 18 13:55:06 tijn-desktop kernel: [    3.192070] [drm] nouveau 0000:01:00.0: 1: core 405MHz shader 810MHz memory 324MHz timing 1 voltage 900mV
Jul 18 13:55:06 tijn-desktop kernel: [    3.192074] [drm] nouveau 0000:01:00.0: 3: core 700MHz shader 1400MHz memory 800MHz timing 2 voltage 1080mV
Jul 18 13:55:06 tijn-desktop kernel: [    3.192156] [drm] nouveau 0000:01:00.0: c: core 405MHz shader 810MHz memory 324MHz voltage 900mV
Jul 18 13:55:06 tijn-desktop kernel: [    3.193902] [TTM] Zone  kernel: Available graphics memory: 6152494 kiB.
Jul 18 13:55:06 tijn-desktop kernel: [    3.193904] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
Jul 18 13:55:06 tijn-desktop kernel: [    3.193906] [TTM] Initializing pool allocator.
Jul 18 13:55:06 tijn-desktop kernel: [    3.193915] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
Jul 18 13:55:06 tijn-desktop kernel: [    3.208183] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Jul 18 13:55:06 tijn-desktop kernel: [    3.239596] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul 18 13:55:06 tijn-desktop kernel: [    3.239599] [drm] No driver support for vblank timestamp query.
Jul 18 13:55:06 tijn-desktop kernel: [    3.264020] usb 5-2: new low-speed USB device number 2 using ohci_hcd
Jul 18 13:55:06 tijn-desktop kernel: [    3.449206] input: MLK Trust Deskset 16593 as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
Jul 18 13:55:06 tijn-desktop kernel: [    3.449330] sunplus 0003:04FC:05D8.0003: input,hidraw2: USB HID v1.00 Keyboard [MLK Trust Deskset 16593] on usb-0000:00:13.0-2/input0
Jul 18 13:55:06 tijn-desktop kernel: [    3.456004] sunplus 0003:04FC:05D8.0004: fixing up Sunplus Wireless Desktop report descriptor
Jul 18 13:55:06 tijn-desktop kernel: [    3.456620] input: MLK Trust Deskset 16593 as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input5
Jul 18 13:55:06 tijn-desktop kernel: [    3.456795] sunplus 0003:04FC:05D8.0004: input,hiddev0,hidraw3: USB HID v1.00 Mouse [MLK Trust Deskset 16593] on usb-0000:00:13.0-2/input1
Jul 18 13:55:06 tijn-desktop kernel: [    3.507551] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x1a0000, bo ffff880305040c00
Jul 18 13:55:06 tijn-desktop kernel: [    3.507616] fbcon: nouveaufb (fb0) is primary device
Jul 18 13:55:06 tijn-desktop kernel: [    3.507674] Console: switching to colour frame buffer device 240x67
Jul 18 13:55:06 tijn-desktop kernel: [    3.507712] fb0: nouveaufb frame buffer device
Jul 18 13:55:06 tijn-desktop kernel: [    3.507714] drm: registered panic notifier
Jul 18 13:55:06 tijn-desktop kernel: [    3.507719] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
Jul 18 13:55:06 tijn-desktop kernel: [    3.889639] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jul 18 13:55:06 tijn-desktop kernel: [    3.889642] EXT4-fs (sda1): write access will be enabled during recovery
Jul 18 13:55:06 tijn-desktop kernel: [    8.106055] EXT4-fs (sda1): orphan cleanup on readonly fs
Jul 18 13:55:06 tijn-desktop kernel: [    8.106063] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3014817
Jul 18 13:55:06 tijn-desktop kernel: [    8.106139] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 24119040
Jul 18 13:55:06 tijn-desktop kernel: [    8.152518] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 26738705
Jul 18 13:55:06 tijn-desktop kernel: [    8.152547] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10495785
Jul 18 13:55:06 tijn-desktop kernel: [    8.152562] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10495784
Jul 18 13:55:06 tijn-desktop kernel: [    8.152574] EXT4-fs (sda1): 5 orphan inodes deleted
Jul 18 13:55:06 tijn-desktop kernel: [    8.152576] EXT4-fs (sda1): recovery complete
Jul 18 13:55:06 tijn-desktop kernel: [    8.196540] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul 18 13:55:06 tijn-desktop kernel: [   20.998846] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 18 13:55:06 tijn-desktop kernel: [   21.092335] Adding 19802108k swap on /dev/sda5.  Priority:-1 extents:1 across:19802108k 
Jul 18 13:55:06 tijn-desktop kernel: [   21.321151] lp: driver loaded but no devices found
Jul 18 13:55:06 tijn-desktop kernel: [   21.423353] f71882fg: Found f71889fg chip at 0xe80, revision 21
Jul 18 13:55:06 tijn-desktop kernel: [   21.423453] f71882fg f71882fg.3712: Fan: 1 is in duty-cycle mode
Jul 18 13:55:06 tijn-desktop kernel: [   21.423472] f71882fg f71882fg.3712: Fan: 2 is in duty-cycle mode
Jul 18 13:55:06 tijn-desktop kernel: [   21.423491] f71882fg f71882fg.3712: Fan: 3 is in duty-cycle mode
Jul 18 13:55:06 tijn-desktop kernel: [   22.064458] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul 18 13:55:06 tijn-desktop kernel: [   22.140398] parport_pc 00:07: reported by Plug and Play ACPI
Jul 18 13:55:06 tijn-desktop kernel: [   22.140463] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 18 13:55:06 tijn-desktop kernel: [   22.158020] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 13:55:06 tijn-desktop kernel: [   22.188043] MCE: In-kernel MCE decoding enabled.
Jul 18 13:55:06 tijn-desktop kernel: [   22.188890] EDAC MC: Ver: 2.1.0
Jul 18 13:55:06 tijn-desktop kernel: [   22.192484] AMD64 EDAC driver v3.4.0
Jul 18 13:55:06 tijn-desktop kernel: [   22.194972] hda_codec: ALC889: BIOS auto-probing.
Jul 18 13:55:06 tijn-desktop kernel: [   22.206228] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jul 18 13:55:06 tijn-desktop kernel: [   22.206436] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jul 18 13:55:06 tijn-desktop kernel: [   22.206526] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jul 18 13:55:06 tijn-desktop kernel: [   22.206647] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jul 18 13:55:06 tijn-desktop kernel: [   22.206728] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jul 18 13:55:06 tijn-desktop kernel: [   22.207066] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jul 18 13:55:06 tijn-desktop kernel: [   22.207178] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jul 18 13:55:06 tijn-desktop kernel: [   22.207274] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
Jul 18 13:55:06 tijn-desktop kernel: [   22.207746] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 18 13:55:06 tijn-desktop kernel: [   22.207749] hda_intel: Disabling MSI
Jul 18 13:55:06 tijn-desktop kernel: [   22.207784] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jul 18 13:55:06 tijn-desktop kernel: [   22.208767] EDAC amd64: DRAM ECC disabled.
Jul 18 13:55:06 tijn-desktop kernel: [   22.208785] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jul 18 13:55:06 tijn-desktop kernel: [   22.208787]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jul 18 13:55:06 tijn-desktop kernel: [   22.208788]  (Note that use of the override may cause unknown side effects.)
Jul 18 13:55:06 tijn-desktop kernel: [   22.228158] lp0: using parport0 (interrupt-driven).
Jul 18 13:55:06 tijn-desktop kernel: [   22.234555] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
Jul 18 13:55:06 tijn-desktop kernel: [   22.234558] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 18 13:55:06 tijn-desktop kernel: [   22.260448] type=1400 audit(1342612506.411:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=692 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.260460] type=1400 audit(1342612506.411:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=767 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.260909] type=1400 audit(1342612506.411:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=692 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.260923] type=1400 audit(1342612506.411:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=767 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.261171] type=1400 audit(1342612506.411:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=692 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.261187] type=1400 audit(1342612506.411:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=767 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.278296] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jul 18 13:55:06 tijn-desktop kernel: [   22.278378] SP5100 TCO timer: mmio address 0xfec000f0 already in use
Jul 18 13:55:06 tijn-desktop kernel: [   22.312501] init: failsafe main process (832) killed by TERM signal
Jul 18 13:55:06 tijn-desktop kernel: [   22.361561] type=1400 audit(1342612506.511:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=890 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.361761] type=1400 audit(1342612506.511:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=892 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.361884] type=1400 audit(1342612506.511:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=891 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop kernel: [   22.362605] type=1400 audit(1342612506.511:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=895 comm="apparmor_parser"
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  ModemManager (version 0.5.2.0) starting...
Jul 18 13:55:06 tijn-desktop bluetoothd[934]: Bluetooth daemon 4.98
Jul 18 13:55:06 tijn-desktop kernel: [   22.394539] ppdev: user-space parallel port driver
Jul 18 13:55:06 tijn-desktop kernel: [   22.399513] Bluetooth: Core ver 2.16
Jul 18 13:55:06 tijn-desktop kernel: [   22.399535] NET: Registered protocol family 31
Jul 18 13:55:06 tijn-desktop kernel: [   22.399538] Bluetooth: HCI device and connection manager initialized
Jul 18 13:55:06 tijn-desktop kernel: [   22.399540] Bluetooth: HCI socket layer initialized
Jul 18 13:55:06 tijn-desktop kernel: [   22.399543] Bluetooth: L2CAP socket layer initialized
Jul 18 13:55:06 tijn-desktop kernel: [   22.399556] Bluetooth: SCO socket layer initialized
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> NetworkManager (version 0.9.4.0) is starting...
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Huawei
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Longcheer
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin ZTE
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Novatel
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Ericsson MBM
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin SimTech
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin MotoC
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Option
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Nokia
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Generic
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Gobi
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Option High-Speed
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Wavecom
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin AnyData
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Sierra
Jul 18 13:55:06 tijn-desktop kernel: [   22.401680] Bluetooth: RFCOMM TTY layer initialized
Jul 18 13:55:06 tijn-desktop kernel: [   22.401686] Bluetooth: RFCOMM socket layer initialized
Jul 18 13:55:06 tijn-desktop kernel: [   22.401689] Bluetooth: RFCOMM ver 1.11
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Samsung
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin Linktop
Jul 18 13:55:06 tijn-desktop modem-manager[929]: <info>  Loaded plugin X22X
Jul 18 13:55:06 tijn-desktop bluetoothd[934]: Starting SDP server
Jul 18 13:55:06 tijn-desktop bluetoothd[934]: Failed to init alert plugin
Jul 18 13:55:06 tijn-desktop bluetoothd[934]: Failed to init time plugin
Jul 18 13:55:06 tijn-desktop bluetoothd[934]: Failed to init proximity plugin
Jul 18 13:55:06 tijn-desktop bluetoothd[934]: Failed to init gatt_example plugin
Jul 18 13:55:06 tijn-desktop kernel: [   22.411030] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 18 13:55:06 tijn-desktop kernel: [   22.411034] Bluetooth: BNEP filters: protocol multicast
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Successfully dropped root privileges.
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: avahi-daemon 0.6.30 starting up.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Successfully called chroot().
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Successfully dropped remaining capabilities.
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Loading service file /services/udisks.service.
Jul 18 13:55:06 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul 18 13:55:06 tijn-desktop polkitd[977]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jul 18 13:55:06 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: init!
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: update_system_hostname
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPluginIfupdown: management mode: unmanaged
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth0, iface: eth0)
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: end _init.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    Ifupdown: get unmanaged devices count: 0
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: (27877168) ... get_connections.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    SCPlugin-Ifupdown: (27877168) ... get_connections (managed=false): return empty list.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    keyfile: parsing Auto eth0 ... 
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    keyfile:     read connection 'Auto eth0'
Jul 18 13:55:06 tijn-desktop NetworkManager[941]:    Ifupdown: get unmanaged devices count: 0
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> modem-manager is now available
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> Networking is enabled by state file
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <warn> failed to allocate link cache: (-10) Operation not supported
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): carrier is OFF
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): now managed
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): bringing up device.
Jul 18 13:55:06 tijn-desktop cron[1012]: (CRON) INFO (pidfile fd = 3)
Jul 18 13:55:06 tijn-desktop kernel: [   22.642789] r8169 0000:02:00.0: eth0: link down
Jul 18 13:55:06 tijn-desktop kernel: [   22.642800] r8169 0000:02:00.0: eth0: link down
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Network interface enumeration completed.
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): preparing device.
Jul 18 13:55:06 tijn-desktop NetworkManager[941]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Server startup complete. Host name is tijn-desktop.local. Local service cookie is 703876988.
Jul 18 13:55:06 tijn-desktop avahi-daemon[965]: Service "tijn-desktop" (/services/udisks.service) successfully established.
Jul 18 13:55:06 tijn-desktop acpid: starting up with proc fs
Jul 18 13:55:06 tijn-desktop acpid: 35 rules loaded
Jul 18 13:55:06 tijn-desktop acpid: waiting for events: event logging is off
Jul 18 13:55:06 tijn-desktop anacron[1055]: Anacron 2.3 started on 2012-07-18
Jul 18 13:55:06 tijn-desktop kernel: [   22.644751] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 18 13:55:06 tijn-desktop kernel: [   22.645216] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 18 13:55:06 tijn-desktop kernel: [   22.650131] init: gdm main process (1054) killed by TERM signal
Jul 18 13:55:06 tijn-desktop cron[1079]: (CRON) STARTUP (fork ok)
Jul 18 13:55:06 tijn-desktop cron[1079]: (CRON) INFO (Running @reboot jobs)
Jul 18 13:55:06 tijn-desktop acpid: client connected from 1080[0:0]
Jul 18 13:55:06 tijn-desktop acpid: 1 client rule loaded
Jul 18 13:55:07 tijn-desktop udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Jul 18 13:55:07 tijn-desktop udev-configure-printer: Failed to get parent
Jul 18 13:55:07 tijn-desktop udev-configure-printer: add /module/lp
Jul 18 13:55:07 tijn-desktop udev-configure-printer: Failed to get parent
Jul 18 13:55:07 tijn-desktop anacron[1055]: Normal exit (0 jobs run)
Jul 18 13:55:07 tijn-desktop kernel: [   23.052042] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jul 18 13:55:07 tijn-desktop kernel: [   23.076023] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jul 18 13:55:07 tijn-desktop kernel: [   23.076488] vboxdrv: Found 8 processor cores.
Jul 18 13:55:07 tijn-desktop kernel: [   23.076911] vboxdrv: fAsync=0 offMin=0x307 offMax=0x7a90
Jul 18 13:55:07 tijn-desktop kernel: [   23.076998] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 18 13:55:07 tijn-desktop kernel: [   23.077000] vboxdrv: Successfully loaded version 4.1.10 (interface 0x00190000).
Jul 18 13:55:07 tijn-desktop kernel: [   23.100022] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jul 18 13:55:07 tijn-desktop kernel: [   23.124029] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jul 18 13:55:07 tijn-desktop kernel: [   23.124104] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jul 18 13:55:07 tijn-desktop kernel: [   23.124192] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jul 18 13:55:07 tijn-desktop kernel: [   23.124264] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jul 18 13:55:07 tijn-desktop kernel: [   23.124340] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input17
Jul 18 13:55:07 tijn-desktop kernel: [   23.284240] vboxpci: IOMMU not found (not registered)
Jul 18 13:55:07 tijn-desktop anacron[1259]: Anacron 2.3 started on 2012-07-18
Jul 18 13:55:07 tijn-desktop anacron[1259]: Normal exit (0 jobs run)
Jul 18 13:55:08 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul 18 13:55:08 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul 18 13:55:08 tijn-desktop accounts-daemon[1398]: started daemon version 0.6.15
Jul 18 13:55:08 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jul 18 13:55:08 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jul 18 13:55:09 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul 18 13:55:09 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul 18 13:55:09 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul 18 13:55:09 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Successfully called chroot.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Successfully dropped privileges.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Successfully limited resources.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Running.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Canary thread running.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Watchdog thread running.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1580 of process 1580 (n/a) owned by '115' high priority at nice level -11.
Jul 18 13:55:09 tijn-desktop rtkit-daemon[1582]: Supervising 1 threads of 1 processes of 1 users.
Jul 18 13:55:09 tijn-desktop anacron[1616]: Anacron 2.3 started on 2012-07-18
Jul 18 13:55:09 tijn-desktop anacron[1616]: Normal exit (0 jobs run)
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): carrier now ON (device state 20)
Jul 18 13:55:09 tijn-desktop kernel: [   25.710037] r8169 0000:02:00.0: eth0: link up
Jul 18 13:55:09 tijn-desktop kernel: [   25.711477] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Auto-activating connection 'Auto eth0'.
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) starting connection 'Auto eth0'
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> dhclient started with pid 1654
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 18 13:55:09 tijn-desktop dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jul 18 13:55:09 tijn-desktop dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jul 18 13:55:09 tijn-desktop dhclient: All rights reserved.
Jul 18 13:55:09 tijn-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 18 13:55:09 tijn-desktop dhclient: 
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 18 13:55:09 tijn-desktop dhclient: Listening on LPF/eth0/8c:89:a5:81:ce:04
Jul 18 13:55:09 tijn-desktop dhclient: Sending on   LPF/eth0/8c:89:a5:81:ce:04
Jul 18 13:55:09 tijn-desktop dhclient: Sending on   Socket/fallback
Jul 18 13:55:09 tijn-desktop dhclient: DHCPREQUEST of 10.0.0.133 on eth0 to 255.255.255.255 port 67
Jul 18 13:55:09 tijn-desktop dhclient: DHCPACK of 10.0.0.133 from 10.0.0.1
Jul 18 13:55:09 tijn-desktop dhclient: bound to 10.0.0.133 -- renewal in 40843 seconds.
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info>   address 10.0.0.133
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info>   prefix 24 (255.255.255.0)
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info>   gateway 10.0.0.1
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info>   hostname 'tijn-desktop'
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info>   nameserver '10.0.0.1'
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 18 13:55:09 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jul 18 13:55:09 tijn-desktop avahi-daemon[965]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.133.
Jul 18 13:55:09 tijn-desktop avahi-daemon[965]: New relevant interface eth0.IPv4 for mDNS.
Jul 18 13:55:09 tijn-desktop avahi-daemon[965]: Registering new address record for 10.0.0.133 on eth0.IPv4.
Jul 18 13:55:09 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul 18 13:55:09 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1720 of process 1580 (n/a) owned by '115' RT at priority 5.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Supervising 2 threads of 1 processes of 1 users.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1721 of process 1580 (n/a) owned by '115' RT at priority 5.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Supervising 3 threads of 1 processes of 1 users.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1722 of process 1580 (n/a) owned by '115' RT at priority 5.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Supervising 4 threads of 1 processes of 1 users.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1725 of process 1725 (n/a) owned by '115' high priority at nice level -11.
Jul 18 13:55:10 tijn-desktop rtkit-daemon[1582]: Supervising 5 threads of 2 processes of 1 users.
Jul 18 13:55:10 tijn-desktop pulseaudio[1725]: [pulseaudio] pid.c: Daemon already running.
Jul 18 13:55:10 tijn-desktop kernel: [   26.608461] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0040
Jul 18 13:55:10 tijn-desktop kernel: [   26.608465] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0040
Jul 18 13:55:10 tijn-desktop NetworkManager[941]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jul 18 13:55:10 tijn-desktop NetworkManager[941]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 18 13:55:11 tijn-desktop NetworkManager[941]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jul 18 13:55:11 tijn-desktop NetworkManager[941]: <info> Activation (eth0) successful, device activated.
Jul 18 13:55:11 tijn-desktop NetworkManager[941]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 18 13:55:11 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 18 13:55:11 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 18 13:55:11 tijn-desktop avahi-daemon[965]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::8e89:a5ff:fe81:ce04.
Jul 18 13:55:11 tijn-desktop avahi-daemon[965]: New relevant interface eth0.IPv6 for mDNS.
Jul 18 13:55:11 tijn-desktop avahi-daemon[965]: Registering new address record for fe80::8e89:a5ff:fe81:ce04 on eth0.*.
Jul 18 13:55:18 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jul 18 13:55:18 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jul 18 13:55:18 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1994 of process 1994 (n/a) owned by '1000' high priority at nice level -11.
Jul 18 13:55:18 tijn-desktop rtkit-daemon[1582]: Supervising 5 threads of 2 processes of 2 users.
Jul 18 13:55:19 tijn-desktop kernel: [   34.867509] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0040
Jul 18 13:55:19 tijn-desktop kernel: [   34.867514] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0040
Jul 18 13:55:13 tijn-desktop ntpdate[1799]: step time server 91.189.94.4 offset -5.815568 sec
Jul 18 13:55:13 tijn-desktop rtkit-daemon[1582]: Successfully made thread 1997 of process 1994 (n/a) owned by '1000' RT at priority 5.
Jul 18 13:55:13 tijn-desktop rtkit-daemon[1582]: Supervising 6 threads of 2 processes of 2 users.
Jul 18 13:55:13 tijn-desktop rtkit-daemon[1582]: Successfully made thread 2000 of process 1994 (n/a) owned by '1000' RT at priority 5.
Jul 18 13:55:13 tijn-desktop rtkit-daemon[1582]: Supervising 7 threads of 2 processes of 2 users.
Jul 18 13:55:13 tijn-desktop rtkit-daemon[1582]: Successfully made thread 2001 of process 1994 (n/a) owned by '1000' RT at priority 5.
Jul 18 13:55:13 tijn-desktop rtkit-daemon[1582]: Supervising 8 threads of 2 processes of 2 users.
Jul 18 13:55:14 tijn-desktop kernel: [   36.376018] eth0: no IPv6 routers present
Jul 18 13:55:16 tijn-desktop kernel: [   38.284408] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:16 tijn-desktop kernel: [   38.284414] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:16 tijn-desktop kernel: [   38.284433] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:16 tijn-desktop kernel: [   38.284437] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:55:16 tijn-desktop kernel: [   38.303423] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:16 tijn-desktop kernel: [   38.303428] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:23 tijn-desktop kernel: [   45.253504] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:23 tijn-desktop kernel: [   45.253509] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:23 tijn-desktop kernel: [   45.550885] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:23 tijn-desktop kernel: [   45.550889] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:24 tijn-desktop kernel: [   45.729825] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:24 tijn-desktop kernel: [   45.729830] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:25 tijn-desktop kernel: [   46.928912] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:25 tijn-desktop kernel: [   46.928916] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:55:25 tijn-desktop kernel: [   47.262934] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0040
Jul 18 13:55:25 tijn-desktop kernel: [   47.262938] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0040
Jul 18 13:55:26 tijn-desktop kernel: [   48.189225] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:26 tijn-desktop kernel: [   48.189230] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:26 tijn-desktop kernel: [   48.438184] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:26 tijn-desktop kernel: [   48.438189] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:55:26 tijn-desktop kernel: [   48.438210] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:26 tijn-desktop kernel: [   48.438214] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:26 tijn-desktop kernel: [   48.451806] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:26 tijn-desktop kernel: [   48.451810] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:27 tijn-desktop kernel: [   48.863997] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:27 tijn-desktop kernel: [   48.864001] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:27 tijn-desktop kernel: [   49.502715] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:27 tijn-desktop kernel: [   49.502720] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:27 tijn-desktop kernel: [   49.652858] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0040
Jul 18 13:55:27 tijn-desktop kernel: [   49.652862] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0040
Jul 18 13:55:30 tijn-desktop goa[2216]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jul 18 13:55:30 tijn-desktop kernel: [   52.427497] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:30 tijn-desktop kernel: [   52.427502] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:31 tijn-desktop kernel: [   52.666933] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:31 tijn-desktop kernel: [   52.666937] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:55:31 tijn-desktop kernel: [   53.356603] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:31 tijn-desktop kernel: [   53.356608] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:55:32 tijn-desktop kernel: [   54.404633] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:55:32 tijn-desktop kernel: [   54.404638] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:55:33 tijn-desktop kernel: [   55.168861] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:55:33 tijn-desktop kernel: [   55.168866] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:56:16 tijn-desktop dbus[906]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jul 18 13:56:18 tijn-desktop AptDaemon: INFO: Initializing daemon
Jul 18 13:56:18 tijn-desktop AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jul 18 13:56:18 tijn-desktop dbus[906]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jul 18 13:56:18 tijn-desktop AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jul 18 13:56:18 tijn-desktop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/240959a482014821801314e2c5232ce3
Jul 18 13:56:18 tijn-desktop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/240959a482014821801314e2c5232ce3
Jul 18 13:56:21 tijn-desktop AptDaemon.PackageKit: INFO: Get updates()
Jul 18 13:56:22 tijn-desktop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/240959a482014821801314e2c5232ce3
Jul 18 13:56:33 tijn-desktop kernel: [  115.253134] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:56:33 tijn-desktop kernel: [  115.253142] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:56:35 tijn-desktop kernel: [  116.960967] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 13:56:35 tijn-desktop kernel: [  116.960971] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 13:56:41 tijn-desktop kernel: [  122.827334] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:56:41 tijn-desktop kernel: [  122.827343] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:57:25 tijn-desktop kernel: [  166.886449] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 13:57:25 tijn-desktop kernel: [  166.886457] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 13:59:38 tijn-desktop kernel: [  299.816023] [Hardware Error]: Machine check events logged
Jul 18 14:00:26 tijn-desktop kernel: [  348.361606] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 14:00:26 tijn-desktop kernel: [  348.361614] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 14:00:26 tijn-desktop kernel: [  348.361677] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 14:00:26 tijn-desktop kernel: [  348.361683] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000
Jul 18 14:00:34 tijn-desktop kernel: [  356.397505] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 14:00:34 tijn-desktop kernel: [  356.397513] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 14:00:39 tijn-desktop kernel: [  360.849830] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0000
Jul 18 14:00:39 tijn-desktop kernel: [  360.849838] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0010
Jul 18 14:01:04 tijn-desktop kernel: [  385.984716] [drm] nouveau 0000:01:00.0: PMFB0_SUBP0: 0x037f0010
Jul 18 14:01:04 tijn-desktop kernel: [  385.984725] [drm] nouveau 0000:01:00.0: PMFB0_SUBP1: 0x037f0000

```

---

### Post by matt_symes on 2012-07-18
Hi

Is there anything in  /var/crash ?

Do you have the same issue if you boot a different kernel ?

What are your hardware specs ?

```
sudo lshw
```

Kind regards

---

### Post by tijnh on 2012-07-18
[SIZE=3][SIZE=2]Hi matt_symes,

Thank you, for your response! I don't know so much about this kernel think, so never really tried. I have no clue how it works or what to do. I actually thought that Ubuntu would pick the right kernel for me..

[/SIZE][B]ls -al /var/crash
[/B][/SIZE]```

root@tijn-desktop:/var/crash# ls -al
total 644
drwxrwsrwt  2 root      whoopsie   4096 Jul 18 13:52 .
drwxr-xr-x 13 root      root       4096 Jul 14 22:36 ..
-rw-r-----  1 tijn whoopsie  51709 Jul 18 13:52 _usr_bin_glipper.1000.crash
-rw-------  1 whoopsie  whoopsie      0 Jul 18 13:47 _usr_bin_glipper.1000.uploaded
-rw-r-----  1 colord    whoopsie 597613 Jul 14 18:35 _usr_lib_x86_64-linux-gnu_colord_colord.116.crash
-rw-r--r--  1 root      whoopsie      0 Jul 14 18:35 _usr_lib_x86_64-linux-gnu_colord_colord.116.upload
-rw-------  1 whoopsie  whoopsie      0 Jul 18 15:55 _usr_lib_x86_64-linux-gnu_colord_colord.116.uploaded

```[SIZE=3]**sudo lshw**[/SIZE]
```

tijn-desktop         
    description: Desktop Computer
    product: MS-7596 (To Be Filled By O.E.M.)
    vendor: MICRO-STAR INTERNATIONAL CO.,LTD
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00000000-0000-0000-0000-8C89A581CE04
  *-core
       description: Motherboard
       product: 760GM-E51(MS-7596)
       vendor: MICRO-STAR INTERNATIONAL CO.,LTD
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V3.1
          date: 09/29/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-8120 Eight-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-8120 Eight-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU1
          size: 1400MHz
          capacity: 3100MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=8 enabledcores=8 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM4
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fd000000-feafffff ioport:f0000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF108 [GeForce GT 430]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:d800(size=128) memory:fea80000-feafffff
           *-multimedia
                description: Audio device
                product: GF108 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:fea7c000-fea7ffff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fbf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 8c:89:a5:81:ce:04
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=10.0.0.133 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:43 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbff8000-fbffbfff memory:febe0000-febfffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fcfffc00-fcffffff
           *-disk
                description: ATA Disk
                product: ST500DM002-1BD14
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: KC44
                serial: S2A19P2F
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00056d5b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: eee1e085-6a87-46ed-8764-c2caf5a5d531
                   size: 446GiB
                   capacity: 446GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-03-28 09:46:21 filesystem=ext4 lastmountpoint=/ modified=2012-07-13 12:49:57 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-07-18 13:55:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 18GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: iHAS122
                vendor: ATAPI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: ZL0F
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fcffe000-fcffefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fcffd000-fcffdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fcfff800-fcfff8ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fcffc000-fcffcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fcffb000-fcffbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fcfff400-fcfff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:fcff4000-fcff7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fcffa000-fcffafff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by tijnh on 2012-07-21
Anyone suggestions? 

How can I find out which kernel is the right one for me, what can I do so this problem stops. Maybe I can search for a certain thing or.. :( Look for other logs?

---

### Post by matt_symes on 2012-07-22
Hi

Nothing untoward in /var/crash.

You should be ale to select another kernel from the GRUB menu (assuming you have other kernels installed).

Not much information in dmesg. I think syslog may be better.

Directly after a crash, boot into Ubuntu. 

Open a terminal and

```
sudo apt-get install pastebinit
```Enter your password. It will not be echoed to the screen.

Then type

```
tail -n 1500 /var/log/syslog | pastebinit
```Hopefully 1500 lines will be enough.

Copy and paste the URL into your next post.

Also post the output of

```
lsmod
```Kind regards

---

### Post by tijnh on 2012-08-04
Thank you very much, I was on holiday.. so I didn't see the message yet. 
Next week I'll be at my PC and do that! You'll hear from me.

Kind regards

---

### Post by Cheesemill on 2012-08-04
What version of Ubuntu are you using, there is no such thing as 12.01

If you are using 12.10 then please bear in mind that it is still under development and hasn't been officially released yet, bugs and crashes are to be expected.

If you are unsure then the following command will tell you:
```
lsb_release -a
```

---

### Post by tijnh on 2012-08-09
Hi!

Ok, my PC just crashed.. (great..) 

Heres the output of the serval commands:

[SIZE=3]tail -n 1500 /var/log/syslog | pastebinit[/SIZE]
[http://paste.ubuntu.com/1137729/](http://paste.ubuntu.com/1137729/)

i've had it twice so heres a second one
[http://paste.ubuntu.com/1137768/](http://paste.ubuntu.com/1137768/)

[SIZE=3]lsmod[/SIZE]
```

Module                  Size  Used by
dm_crypt               23125  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     32474  4 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
ppdev                  17113  0 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
snd_hda_intel          33773  5 
snd_seq_midi           13324  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
k10temp                13166  0 
fam15h_power           13115  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32866  1 
mac_hid                13253  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
f71882fg               36101  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
hid_sunplus            12619  0 
usbhid                 47199  0 
hid                    99559  2 hid_sunplus,usbhid
nouveau               774571  3 
pata_atiixp            13204  0 
ttm                    76949  1 nouveau
r8169                  62099  0 
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
video                  19596  1 nouveau
wmi                    19256  1 mxm_wmi

```[SIZE=3]
lsb_release -a[/SIZE]
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

```Thank you so much for helping!

Kind regards,
Tijn

---

### Post by tijnh on 2012-08-09
Sorry i've made a typo in the title 12.01 should be 12.04 LTS

---

### Post by tijnh on 2012-08-26
Any Suggestions?

---

### Post by matt_symes on 2012-08-31
Hi

There's not really anything in the logs to suggest what the problem may be. That *may* point to a hardware problem.

Some things to check.

1. Check the temperature using sensors. Make sure the shutdown is not due to overheating.

```
sudo apt-get install lm-sensors
```

```
sensors-detect
```

```
sensors
```

you can also install the sensors daemon to log the temp data.

```
sudo apt-get install sensord
```

then to get the temps

```
grep sensord /var/log/syslog
```

2 Run a memory test to make sure the problem is not with bad memory. Run the test overnight.

Run this from the GRUB menu.

3. Run a SMART test on your hard drive and check the SMART status after.

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sdX
```

where X is the drive letter.

After it has finished - it can take a while:

```
sudo smartctl -a /dev/sdX
```

4. Try using the nvidia drivers instead of the nouveau drivers.

You can do this from the additional drivers window.

Kind regards

---

### Post by tijnh on 2012-09-02
Thankyou im going to try it. So its no kernel problem? I think its inside the video drivers, so first try that. Its not a heat problem i checked that. Ram should be fine did a test before. Ill let you know what haappends. Ill install windows too to see what happends if it has the same problem. Than it would definetly be a hardware issue. You have any idea how i can check if my power supply is strong enough, has enough watts.

---

### Post by matt_symes on 2012-09-04
Hi

I do suspect hardware at the moment as nothing is being written to any logs.

> **tijnh said:**
> You have any idea how i can check if my power supply is strong enough, has enough watts.

I would use a standard multimeter to check the voltages of the power supply.

Can you swap out components looking for one that may be causing you the problem

Kind regards

---

### Post by tijnh on 2012-10-05
Found some errors, that may cause the problem:
When I was working in **console**:

[U][[IMG]http://s12.postimage.org/bmqhwvlrt/foto.jpg[/IMG]]("http://postimage.org/image/bmqhwvlrt")

[/U][http://postimage.org/image/bmqhwvlrt](http://postimage.org/image/bmqhwvlrt)

Found a similair threat: [http://ubuntuforums.org/showthread.php?t=2010489](http://ubuntuforums.org/showthread.php?t=2010489)[B] with the same hardware!
[/B]

---

