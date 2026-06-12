---
title: "codec failed, cannot boot into normal mode"
date: 2010-12-22
forum: General Help
---

### Post by yuler on 2010-12-22
Shut down the machine yesterday, got an error booting today.  Since I'm new to Ubuntu (been using it for about a month now), I don't know what logs to check, what utilities to run, where to find bootup error message so I can copy here.  I am now using it in recovery/low-graphics mode.

---

### Post by yuler on 2010-12-22
I don't know how to access the logs from the CLI, but I found it in the GUI.

System > admin > Log Viewer > filters > manage filters > codec

From syslog (search for the word "codec"):
```

Dec 22 00:37:41 masterblaster kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 22 00:37:41 masterblaster rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="759" x-info="http://www.rsyslog.com"] (re)start
Dec 22 00:37:41 masterblaster rsyslogd: rsyslogd's groupid changed to 103
Dec 22 00:37:41 masterblaster rsyslogd: rsyslogd's userid changed to 101
Dec 22 00:37:41 masterblaster rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> NetworkManager (version 0.8.1) is starting...
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Successfully dropped root privileges.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Linux version 2.6.35-23-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
Dec 22 00:37:41 masterblaster avahi-daemon[809]: avahi-daemon 0.6.27 starting up.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffa0000 (usable)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 000000003ffa0000 - 000000003ffb0000 (ACPI data)
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> trying to start the modem manager...
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003fff0000 (ACPI NVS)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Dec 22 00:37:41 masterblaster kernel: [    0.000000] DMI 2.3 present.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] last_pfn = 0x3ffa0 max_arch_pfn = 0x100000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] MTRR default type: uncachable
Dec 22 00:37:41 masterblaster kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   00000-9FFFF write-back
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   A0000-EFFFF uncachable
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 22 00:37:41 masterblaster kernel: [    0.000000] MTRR variable ranges enabled:
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   1 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   2 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   3 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   4 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   5 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   6 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   7 disabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec 22 00:37:41 masterblaster kernel: [    0.000000] modified physical RAM map:
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 0000000000100000 - 000000003ffa0000 (usable)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 000000003ffa0000 - 000000003ffb0000 (ACPI data)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 000000003ffb0000 - 000000003fff0000 (ACPI NVS)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Dec 22 00:37:41 masterblaster kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Dec 22 00:37:41 masterblaster kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Dec 22 00:37:41 masterblaster kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] RAMDISK: 2f5b4000 - 2fff8000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: RSDP 000faa00 00021 (v02 ACPIAM)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: XSDT 3ffa0100 0003C (v01 A M I  OEMXSDT  10000514 MSFT 00000097)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: FACP 3ffa0290 000F4 (v03 A M I  OEMFACP  10000514 MSFT 00000097)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: DSDT 3ffa03e0 042E1 (v01  A0310 A0310001 00000001 MSFT 0100000D)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: FACS 3ffb0000 00040
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: APIC 3ffa0390 0004A (v01 A M I  OEMAPIC  10000514 MSFT 00000097)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: OEMB 3ffb0040 0003F (v01 A M I  OEMBIOS  10000514 MSFT 00000097)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] 135MB HIGHMEM available.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] 887MB LOWMEM available.
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   low ram: 0 - 377fe000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Zone PFN ranges:
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003ffa0
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Movable zone start PFN for each node
Dec 22 00:37:41 masterblaster kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     0: 0x00000100 -> 0x0003ffa0
Dec 22 00:37:41 masterblaster kernel: [    0.000000] On node 0 totalpages: 261935
Dec 22 00:37:41 masterblaster kernel: [    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c1001200
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   HighMem zone: 272 pages used for memmap
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   HighMem zone: 34450 pages, LIFO batch:7
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Using APIC driver default
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 22 00:37:41 masterblaster kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 22 00:37:41 masterblaster kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Dec 22 00:37:41 masterblaster kernel: [    0.000000] nr_irqs_gsi: 40
Dec 22 00:37:41 masterblaster kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Dec 22 00:37:41 masterblaster kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf780000)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 22 00:37:41 masterblaster kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Dec 22 00:37:41 masterblaster kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36416 r0 d20928 u4194304
Dec 22 00:37:41 masterblaster kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
Dec 22 00:37:41 masterblaster kernel: [    0.000000] pcpu-alloc: [0] 0 
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259887
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single
Dec 22 00:37:41 masterblaster kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Initializing CPU#0
Dec 22 00:37:41 masterblaster kernel: [    0.000000] allocated 5240640 bytes of page_cgroup
Dec 22 00:37:41 masterblaster kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Subtract (45 early reservations)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #3 [002f5b4000 - 002fff8000]         RAMDISK
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #4 [00009a1000 - 00009a420c]             BRK
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #7 [000009fc00 - 00000e0250]   BIOS reserved
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #8 [00000e0380 - 00000ff780]   BIOS reserved
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #9 [00000e0250 - 00000e0380]    MP-table mpc
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Successfully called chroot().
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Successfully dropped remaining capabilities.
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #14 [0001001000 - 0001801000]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #15 [0001801000 - 0001801004]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #16 [0001801040 - 0001801100]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #17 [0001801100 - 0001801154]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #18 [0001801180 - 0001804180]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #19 [0001804180 - 0001804190]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #20 [00018041c0 - 0001804dc0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #21 [0001804dc0 - 0001804de7]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #22 [0001804e00 - 0001804efc]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #23 [0001804f00 - 0001804f40]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #24 [0001804f40 - 0001804f80]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #25 [0001804f80 - 0001804fc0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #26 [0001804fc0 - 0001805000]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #27 [0001805000 - 0001805040]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #28 [0001805040 - 0001805080]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #29 [0001805080 - 00018050c0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #30 [00018050c0 - 0001805100]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #31 [0001805100 - 0001805110]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #32 [0001805140 - 00018051a4]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #33 [00018051c0 - 0001805224]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #34 [0001c00000 - 0001c0e000]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #35 [0001807240 - 0001807244]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #36 [0001807280 - 0001807284]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #37 [00018072c0 - 00018072c4]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #38 [0001807300 - 0001807304]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #39 [0001807340 - 00018073f0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #40 [0001807400 - 00018074a8]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #41 [00018074c0 - 000180b4c0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #42 [000180b4c0 - 000188b4c0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #43 [000188b4c0 - 00018cb4c0]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000]   #44 [0001c0e000 - 000210d740]         BOOTMEM
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003ffa0)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Memory: 1014172k/1048192k available (4930k kernel code, 33568k reserved, 2334k data, 684k init, 138888k highmem)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] virtual kernel memory layout:
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]       .data : 0xc05d0bee - 0xc0818628   (2334 kB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d0bee   (4930 kB)
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Hierarchical RCU implementation.
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Extended CMOS year: 2000
Dec 22 00:37:41 masterblaster kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 22 00:37:41 masterblaster kernel: [    0.000000] console [tty0] enabled
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Fast TSC calibration using PIT
Dec 22 00:37:41 masterblaster kernel: [    0.000000] Detected 1599.774 MHz processor.
Dec 22 00:37:41 masterblaster kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.54 BogoMIPS (lpj=6399096)
Dec 22 00:37:41 masterblaster kernel: [    0.004150] pid_max: default: 32768 minimum: 301
Dec 22 00:37:41 masterblaster kernel: [    0.004255] Security Framework initialized
Dec 22 00:37:41 masterblaster kernel: [    0.004355] AppArmor: AppArmor initialized
Dec 22 00:37:41 masterblaster kernel: [    0.004425] Yama: becoming mindful.
Dec 22 00:37:41 masterblaster kernel: [    0.004582] Mount-cache hash table entries: 512
Dec 22 00:37:41 masterblaster kernel: [    0.004829] Initializing cgroup subsys ns
Dec 22 00:37:41 masterblaster kernel: [    0.004901] Initializing cgroup subsys cpuacct
Dec 22 00:37:41 masterblaster kernel: [    0.004976] Initializing cgroup subsys memory
Dec 22 00:37:41 masterblaster kernel: [    0.005056] Initializing cgroup subsys devices
Dec 22 00:37:41 masterblaster kernel: [    0.005128] Initializing cgroup subsys freezer
Dec 22 00:37:41 masterblaster kernel: [    0.005199] Initializing cgroup subsys net_cls
Dec 22 00:37:41 masterblaster kernel: [    0.005302] mce: CPU supports 5 MCE banks
Dec 22 00:37:41 masterblaster kernel: [    0.005389] Performance Events: AMD PMU driver.
Dec 22 00:37:41 masterblaster kernel: [    0.005519] ... version:                0
Dec 22 00:37:41 masterblaster kernel: [    0.005589] ... bit width:              48
Dec 22 00:37:41 masterblaster kernel: [    0.005659] ... generic registers:      4
Dec 22 00:37:41 masterblaster kernel: [    0.005729] ... value mask:             0000ffffffffffff
Dec 22 00:37:41 masterblaster kernel: [    0.005800] ... max period:             00007fffffffffff
Dec 22 00:37:41 masterblaster kernel: [    0.005872] ... fixed-purpose events:   0
Dec 22 00:37:41 masterblaster kernel: [    0.005942] ... event mask:             000000000000000f
Dec 22 00:37:41 masterblaster kernel: [    0.008883] SMP alternatives: switching to UP code
Dec 22 00:37:41 masterblaster kernel: [    0.018717] Freeing SMP alternatives: 24k freed
Dec 22 00:37:41 masterblaster kernel: [    0.018816] ACPI: Core revision 20100428
Dec 22 00:37:41 masterblaster kernel: [    0.026370] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 22 00:37:41 masterblaster kernel: [    0.026447] ftrace: allocating 21766 entries in 43 pages
Dec 22 00:37:41 masterblaster kernel: [    0.028105] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 22 00:37:41 masterblaster kernel: [    0.028932] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Dec 22 00:37:41 masterblaster kernel: [    0.070267] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
Dec 22 00:37:41 masterblaster kernel: [    0.072000] Brought up 1 CPUs
Dec 22 00:37:41 masterblaster kernel: [    0.072000] Total of 1 processors activated (3199.54 BogoMIPS).
Dec 22 00:37:41 masterblaster kernel: [    0.072000] devtmpfs: initialized
Dec 22 00:37:41 masterblaster kernel: [    0.072000] regulator: core version 0.5
Dec 22 00:37:41 masterblaster kernel: [    0.072000] Time:  0:37:24  Date: 12/22/10
Dec 22 00:37:41 masterblaster kernel: [    0.072000] NET: Registered protocol family 16
Dec 22 00:37:41 masterblaster kernel: [    0.072000] EISA bus registered
Dec 22 00:37:41 masterblaster kernel: [    0.072000] node 0 link 0: io port [1000, ffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.072000] TOM: 0000000040000000 aka 1024M
Dec 22 00:37:41 masterblaster kernel: [    0.072000] node 0 link 0: mmio [a0000, bffff]
Dec 22 00:37:41 masterblaster kernel: [    0.072000] node 0 link 0: mmio [40000000, ffffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.072000] bus: [00, ff] on node 0 link 0
Dec 22 00:37:41 masterblaster kernel: [    0.072000] bus: 00 index 0 [io  0x0000-0xffff]
Dec 22 00:37:41 masterblaster kernel: [    0.072000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Dec 22 00:37:41 masterblaster kernel: [    0.072000] bus: 00 index 2 [mem 0x40000000-0xffffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.072000] ACPI: bus type pci registered
Dec 22 00:37:41 masterblaster kernel: [    0.072000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Dec 22 00:37:41 masterblaster kernel: [    0.072000] PCI: Using configuration type 1 for base access
Dec 22 00:37:41 masterblaster kernel: [    0.073301] bio: create slab <bio-0> at 0
Dec 22 00:37:41 masterblaster kernel: [    0.074329] ACPI: EC: Look up EC in DSDT
Dec 22 00:37:41 masterblaster kernel: [    0.075626] ACPI: Executed 1 blocks of module-level executable AML code
Dec 22 00:37:41 masterblaster kernel: [    0.080558] ACPI: Interpreter enabled
Dec 22 00:37:41 masterblaster kernel: [    0.082224] ACPI: (supports S0 S1 S3 S4 S5)
Dec 22 00:37:41 masterblaster kernel: [    0.082577] ACPI: Using IOAPIC for interrupt routing
Dec 22 00:37:41 masterblaster kernel: [    0.091198] ACPI Warning: Incorrect checksum in table [OEMB] - 0xE9, should be 0xE3 (20100428/tbutils-314)
Dec 22 00:37:41 masterblaster kernel: [    0.091516] ACPI: No dock devices found.
Dec 22 00:37:41 masterblaster kernel: [    0.091587] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Dec 22 00:37:41 masterblaster kernel: [    0.091809] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 22 00:37:41 masterblaster kernel: [    0.092162] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Dec 22 00:37:41 masterblaster kernel: [    0.092166] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Dec 22 00:37:41 masterblaster kernel: [    0.092170] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Dec 22 00:37:41 masterblaster kernel: [    0.092174] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
Dec 22 00:37:41 masterblaster kernel: [    0.092204] pci 0000:00:00.0: reg 10: [mem 0xde000000-0xdfffffff pref]
Dec 22 00:37:41 masterblaster kernel: [    0.092482] pci 0000:00:01.0: supports D1
Dec 22 00:37:41 masterblaster kernel: [    0.092522] pci 0000:00:0c.0: reg 10: [mem 0xf9e00000-0xf9e007ff]
Dec 22 00:37:41 masterblaster kernel: [    0.092529] pci 0000:00:0c.0: reg 14: [mem 0xf9d00000-0xf9d03fff]
Dec 22 00:37:41 masterblaster kernel: [    0.092566] pci 0000:00:0c.0: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.092569] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot
Dec 22 00:37:41 masterblaster kernel: [    0.092574] pci 0000:00:0c.0: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.092604] pci 0000:00:0f.0: reg 10: [io  0xe800-0xe807]
Dec 22 00:37:41 masterblaster kernel: [    0.092612] pci 0000:00:0f.0: reg 14: [io  0xe400-0xe403]
Dec 22 00:37:41 masterblaster kernel: [    0.092619] pci 0000:00:0f.0: reg 18: [io  0xe000-0xe007]
Dec 22 00:37:41 masterblaster kernel: [    0.092626] pci 0000:00:0f.0: reg 1c: [io  0xd800-0xd803]
Dec 22 00:37:41 masterblaster kernel: [    0.092633] pci 0000:00:0f.0: reg 20: [io  0xd400-0xd40f]
Dec 22 00:37:41 masterblaster kernel: [    0.092640] pci 0000:00:0f.0: reg 24: [io  0xd000-0xd0ff]
Dec 22 00:37:41 masterblaster kernel: [    0.092703] pci 0000:00:0f.1: reg 20: [io  0xfc00-0xfc0f]
Dec 22 00:37:41 masterblaster kernel: [    0.092775] pci 0000:00:10.0: reg 20: [io  0xb800-0xb81f]
Dec 22 00:37:41 masterblaster kernel: [    0.092800] pci 0000:00:10.0: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.092803] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 22 00:37:41 masterblaster kernel: [    0.092807] pci 0000:00:10.0: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.092850] pci 0000:00:10.1: reg 20: [io  0xc000-0xc01f]
Dec 22 00:37:41 masterblaster kernel: [    0.092874] pci 0000:00:10.1: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.092877] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 22 00:37:41 masterblaster kernel: [    0.092882] pci 0000:00:10.1: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.092923] pci 0000:00:10.2: reg 20: [io  0xc400-0xc41f]
Dec 22 00:37:41 masterblaster kernel: [    0.092948] pci 0000:00:10.2: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.092951] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec 22 00:37:41 masterblaster kernel: [    0.092955] pci 0000:00:10.2: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.092999] pci 0000:00:10.3: reg 20: [io  0xc800-0xc81f]
Dec 22 00:37:41 masterblaster kernel: [    0.093023] pci 0000:00:10.3: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.093026] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Dec 22 00:37:41 masterblaster kernel: [    0.093031] pci 0000:00:10.3: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.093058] pci 0000:00:10.4: reg 10: [mem 0xf9b00000-0xf9b000ff]
Dec 22 00:37:41 masterblaster kernel: [    0.093097] pci 0000:00:10.4: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.093100] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Dec 22 00:37:41 masterblaster kernel: [    0.093105] pci 0000:00:10.4: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.093160] HPET not enabled in BIOS. You might try hpet=force boot option
Dec 22 00:37:41 masterblaster kernel: [    0.093236] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
Dec 22 00:37:41 masterblaster kernel: [    0.093350] pci 0000:00:11.5: reg 10: [io  0xb400-0xb4ff]
Dec 22 00:37:41 masterblaster kernel: [    0.093391] pci 0000:00:11.5: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.093419] pci 0000:00:11.6: reg 10: [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.093487] pci 0000:00:12.0: reg 10: [io  0xb000-0xb0ff]
Dec 22 00:37:41 masterblaster kernel: [    0.093494] pci 0000:00:12.0: reg 14: [mem 0xf9a00000-0xf9a000ff]
Dec 22 00:37:41 masterblaster kernel: [    0.093530] pci 0000:00:12.0: supports D1 D2
Dec 22 00:37:41 masterblaster kernel: [    0.093533] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 22 00:37:41 masterblaster kernel: [    0.093538] pci 0000:00:12.0: PME# disabled
Dec 22 00:37:41 masterblaster kernel: [    0.093633] PCI: peer root bus 00 res updated from pci conf
Dec 22 00:37:41 masterblaster kernel: [    0.093675] pci 0000:01:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.093681] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff pref]
Dec 22 00:37:41 masterblaster kernel: [    0.093687] pci 0000:01:00.0: reg 18: [mem 0xfa000000-0xfaffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.093700] pci 0000:01:00.0: reg 30: [mem 0xf9f00000-0xf9f1ffff pref]
Dec 22 00:37:41 masterblaster kernel: [    0.093741] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 22 00:37:41 masterblaster kernel: [    0.093813] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 22 00:37:41 masterblaster kernel: [    0.093819] pci 0000:00:01.0:   bridge window [mem 0xf9f00000-0xfbffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.093824] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf8ffffff pref]
Dec 22 00:37:41 masterblaster kernel: [    0.093832] pci_bus 0000:00: on NUMA node 0
Dec 22 00:37:41 masterblaster kernel: [    0.093837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 22 00:37:41 masterblaster kernel: [    0.094061] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec 22 00:37:41 masterblaster kernel: [    0.105635] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
Dec 22 00:37:41 masterblaster kernel: [    0.106331] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
Dec 22 00:37:41 masterblaster kernel: [    0.107020] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
Dec 22 00:37:41 masterblaster kernel: [    0.107713] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.108491] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.109294] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.110097] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.110900] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Dec 22 00:37:41 masterblaster kernel: [    0.111638] HEST: Table is not found!
Dec 22 00:37:41 masterblaster kernel: [    0.111829] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 22 00:37:41 masterblaster kernel: [    0.111913] vgaarb: loaded
Dec 22 00:37:41 masterblaster kernel: [    0.112217] SCSI subsystem initialized
Dec 22 00:37:41 masterblaster kernel: [    0.112369] libata version 3.00 loaded.
Dec 22 00:37:41 masterblaster kernel: [    0.112439] usbcore: registered new interface driver usbfs
Dec 22 00:37:41 masterblaster kernel: [    0.112523] usbcore: registered new interface driver hub
Dec 22 00:37:41 masterblaster kernel: [    0.112621] usbcore: registered new device driver usb
Dec 22 00:37:41 masterblaster kernel: [    0.112866] ACPI: WMI: Mapper loaded
Dec 22 00:37:41 masterblaster kernel: [    0.112934] PCI: Using ACPI for IRQ routing
Dec 22 00:37:41 masterblaster kernel: [    0.113005] PCI: pci_cache_line_size set to 64 bytes
Dec 22 00:37:41 masterblaster kernel: [    0.113100] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Dec 22 00:37:41 masterblaster kernel: [    0.113104] reserve RAM buffer: 000000003ffa0000 - 000000003fffffff 
Dec 22 00:37:41 masterblaster kernel: [    0.113231] NetLabel: Initializing
Dec 22 00:37:41 masterblaster kernel: [    0.113299] NetLabel:  domain hash size = 128
Dec 22 00:37:41 masterblaster kernel: [    0.113367] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 22 00:37:41 masterblaster kernel: [    0.113451] NetLabel:  unlabeled traffic allowed by default
Dec 22 00:37:41 masterblaster kernel: [    0.113600] Switching to clocksource tsc
Dec 22 00:37:41 masterblaster kernel: [    0.124885] AppArmor: AppArmor Filesystem Enabled
Dec 22 00:37:41 masterblaster kernel: [    0.124981] pnp: PnP ACPI init
Dec 22 00:37:41 masterblaster kernel: [    0.125071] ACPI: bus type pnp registered
Dec 22 00:37:41 masterblaster kernel: [    0.126391] pnp 00:08: disabling [io  0x0010-0x001f] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.126481] pnp 00:08: disabling [io  0x0022-0x003f] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.126569] pnp 00:08: disabling [io  0x0044-0x005f] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.126657] pnp 00:08: disabling [io  0x0062-0x0063] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.126745] pnp 00:08: disabling [io  0x0065-0x006f] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.126833] pnp 00:08: disabling [io  0x0072-0x007f] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.126920] pnp 00:08: disabling [io  0x0080] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.127007] pnp 00:08: disabling [io  0x0084-0x0086] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.127095] pnp 00:08: disabling [io  0x0088] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.127182] pnp 00:08: disabling [io  0x008c-0x008e] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.127269] pnp 00:08: disabling [io  0x0090-0x009f] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.127357] pnp 00:08: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.127445] pnp 00:08: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:11.6 BAR 0 [io  0x0000-0x00ff]
Dec 22 00:37:41 masterblaster kernel: [    0.129955] pnp: PnP ACPI: found 13 devices
Dec 22 00:37:41 masterblaster kernel: [    0.130024] ACPI: ACPI bus type pnp unregistered
Dec 22 00:37:41 masterblaster kernel: [    0.130095] PnPBIOS: Disabled by ACPI PNP
Dec 22 00:37:41 masterblaster kernel: [    0.130177] system 00:07: [io  0x0290-0x0297] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130254] system 00:08: [io  0x03e1-0x03e7] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130331] system 00:08: [io  0x04d0-0x04d1] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130403] system 00:08: [io  0x0800-0x087f] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130474] system 00:08: [io  0x0400-0x041f] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130550] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130623] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130696] system 00:09: [mem 0xfff80000-0xffffffff] has been reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130773] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130846] system 00:0c: [mem 0x000c0000-0x000dffff] could not be reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130919] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 22 00:37:41 masterblaster kernel: [    0.130992] system 00:0c: [mem 0x00100000-0x3ffeffff] could not be reserved
Dec 22 00:37:41 masterblaster kernel: [    0.167472] pci 0000:00:11.6: BAR 0: assigned [io  0x1000-0x10ff]
Dec 22 00:37:41 masterblaster kernel: [    0.167550] pci 0000:00:11.6: BAR 0: set to [io  0x1000-0x10ff] (PCI address [0x1000-0x10ff]
Dec 22 00:37:41 masterblaster kernel: [    0.167636] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 22 00:37:41 masterblaster kernel: [    0.167706] pci 0000:00:01.0:   bridge window [io  disabled]
Dec 22 00:37:41 masterblaster kernel: [    0.167779] pci 0000:00:01.0:   bridge window [mem 0xf9f00000-0xfbffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.167854] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf8ffffff pref]
Dec 22 00:37:41 masterblaster kernel: [    0.167952] pci 0000:00:01.0: setting latency timer to 64
Dec 22 00:37:41 masterblaster kernel: [    0.167957] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Dec 22 00:37:41 masterblaster kernel: [    0.167960] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Dec 22 00:37:41 masterblaster kernel: [    0.167964] pci_bus 0000:00: resource 6 [mem 0x40000000-0xffffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.167968] pci_bus 0000:01: resource 1 [mem 0xf9f00000-0xfbffffff]
Dec 22 00:37:41 masterblaster kernel: [    0.167971] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf8ffffff pref]
Dec 22 00:37:41 masterblaster kernel: [    0.168021] NET: Registered protocol family 2
Dec 22 00:37:41 masterblaster kernel: [    0.168168] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 22 00:37:41 masterblaster kernel: [    0.168624] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: init!
Dec 22 00:37:41 masterblaster kernel: [    0.169679] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.170239] TCP: Hash tables configured (established 131072 bind 65536)
Dec 22 00:37:41 masterblaster kernel: [    0.170313] TCP reno registered
Dec 22 00:37:41 masterblaster kernel: [    0.170403] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.170490] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.170674] NET: Registered protocol family 1
Dec 22 00:37:41 masterblaster kernel: [    0.170755] pci 0000:00:00.0: MSI quirk detected; MSI disabled
Dec 22 00:37:41 masterblaster kernel: [    0.170842] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Dec 22 00:37:41 masterblaster kernel: [    0.171023] pci 0000:01:00.0: Boot video device
Dec 22 00:37:41 masterblaster kernel: [    0.171027] PCI: CLS 32 bytes, default 64
Dec 22 00:37:41 masterblaster kernel: [    0.171282] cpufreq-nforce2: No nForce2 chipset.
Dec 22 00:37:41 masterblaster kernel: [    0.171387] Scanning for low memory corruption every 60 seconds
Dec 22 00:37:41 masterblaster kernel: [    0.171591] audit: initializing netlink socket (disabled)
Dec 22 00:37:41 masterblaster kernel: [    0.171673] type=2000 audit(1292978243.168:1): initialized
Dec 22 00:37:41 masterblaster kernel: [    0.185824] Trying to unpack rootfs image as initramfs...
Dec 22 00:37:41 masterblaster kernel: [    0.202524] highmem bounce pool size: 64 pages
Dec 22 00:37:41 masterblaster kernel: [    0.202603] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 22 00:37:41 masterblaster kernel: [    0.208184] VFS: Disk quotas dquot_6.5.2
Dec 22 00:37:41 masterblaster kernel: [    0.208330] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 22 00:37:41 masterblaster kernel: [    0.214650] fuse init (API version 7.14)
Dec 22 00:37:41 masterblaster kernel: [    0.214881] msgmni has been set to 1709
Dec 22 00:37:41 masterblaster kernel: [    0.218696] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 22 00:37:41 masterblaster kernel: [    0.218784] io scheduler noop registered
Dec 22 00:37:41 masterblaster kernel: [    0.218853] io scheduler deadline registered
Dec 22 00:37:41 masterblaster kernel: [    0.218937] io scheduler cfq registered (default)
Dec 22 00:37:41 masterblaster kernel: [    0.219176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 22 00:37:41 masterblaster kernel: [    0.219276] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 22 00:37:41 masterblaster kernel: [    0.219593] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 22 00:37:41 masterblaster kernel: [    0.219688] ACPI: Power Button [PWRB]
Dec 22 00:37:41 masterblaster kernel: [    0.219810] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 22 00:37:41 masterblaster kernel: [    0.219894] ACPI: Power Button [PWRF]
Dec 22 00:37:41 masterblaster kernel: [    0.220160] ACPI: acpi_idle registered with cpuidle
Dec 22 00:37:41 masterblaster kernel: [    0.227657] ERST: Table is not found!
Dec 22 00:37:41 masterblaster kernel: [    0.227986] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 22 00:37:41 masterblaster kernel: [    0.228209] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 22 00:37:41 masterblaster kernel: [    0.228641] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 22 00:37:41 masterblaster kernel: [    0.230168] brd: module loaded
Dec 22 00:37:41 masterblaster kernel: [    0.230407] isapnp: Scanning for PnP cards...
Dec 22 00:37:41 masterblaster kernel: [    0.238966] loop: module loaded
Dec 22 00:37:41 masterblaster kernel: [    0.239378]   alloc irq_desc for 20 on node -1
Dec 22 00:37:41 masterblaster kernel: [    0.239382]   alloc kstat_irqs on node -1
Dec 22 00:37:41 masterblaster kernel: [    0.239391] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Dec 22 00:37:41 masterblaster kernel: [    0.239538] pata_acpi 0000:00:0f.0: PCI INT B disabled
Dec 22 00:37:41 masterblaster kernel: [    0.239622] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 22 00:37:41 masterblaster kernel: [    0.239725] pata_acpi 0000:00:0f.1: PCI INT A disabled
Dec 22 00:37:41 masterblaster kernel: [    0.240244] Fixed MDIO Bus: probed
Dec 22 00:37:41 masterblaster kernel: [    0.240360] PPP generic driver version 2.4.2
Dec 22 00:37:41 masterblaster kernel: [    0.240491] tun: Universal TUN/TAP device driver, 1.6
Dec 22 00:37:41 masterblaster kernel: [    0.240561] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 22 00:37:41 masterblaster kernel: [    0.240727] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 22 00:37:41 masterblaster kernel: [    0.240816]   alloc irq_desc for 21 on node -1
Dec 22 00:37:41 masterblaster kernel: [    0.240818]   alloc kstat_irqs on node -1
Dec 22 00:37:41 masterblaster kernel: [    0.240825] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Dec 22 00:37:41 masterblaster kernel: [    0.240917] ehci_hcd 0000:00:10.4: EHCI Host Controller
Dec 22 00:37:41 masterblaster kernel: [    0.241027] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
Dec 22 00:37:41 masterblaster kernel: [    0.241179] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf9b00000
Dec 22 00:37:41 masterblaster kernel: [    0.289960] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
Dec 22 00:37:41 masterblaster kernel: [    0.290241] hub 1-0:1.0: USB hub found
Dec 22 00:37:41 masterblaster kernel: [    0.290314] hub 1-0:1.0: 8 ports detected
Dec 22 00:37:41 masterblaster kernel: [    0.290483] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 22 00:37:41 masterblaster kernel: [    0.290574] uhci_hcd: USB Universal Host Controller Interface driver
Dec 22 00:37:41 masterblaster kernel: [    0.290701] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 22 00:37:41 masterblaster kernel: [    0.290781] uhci_hcd 0000:00:10.0: UHCI Host Controller
Dec 22 00:37:41 masterblaster kernel: [    0.290910] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Dec 22 00:37:41 masterblaster kernel: [    0.291017] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b800
Dec 22 00:37:41 masterblaster kernel: [    0.291233] hub 2-0:1.0: USB hub found
Dec 22 00:37:41 masterblaster kernel: [    0.291305] hub 2-0:1.0: 2 ports detected
Dec 22 00:37:41 masterblaster kernel: [    0.291438] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 22 00:37:41 masterblaster kernel: [    0.291515] uhci_hcd 0000:00:10.1: UHCI Host Controller
Dec 22 00:37:41 masterblaster kernel: [    0.291622] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Dec 22 00:37:41 masterblaster kernel: [    0.291723] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c000
Dec 22 00:37:41 masterblaster kernel: [    0.291944] hub 3-0:1.0: USB hub found
Dec 22 00:37:41 masterblaster kernel: [    0.292015] hub 3-0:1.0: 2 ports detected
Dec 22 00:37:41 masterblaster kernel: [    0.292147] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 22 00:37:41 masterblaster kernel: [    0.292224] uhci_hcd 0000:00:10.2: UHCI Host Controller
Dec 22 00:37:41 masterblaster kernel: [    0.292335] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Dec 22 00:37:41 masterblaster kernel: [    0.292439] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c400
Dec 22 00:37:41 masterblaster kernel: [    0.292655] hub 4-0:1.0: USB hub found
Dec 22 00:37:41 masterblaster kernel: [    0.292726] hub 4-0:1.0: 2 ports detected
Dec 22 00:37:41 masterblaster kernel: [    0.292861] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 22 00:37:41 masterblaster kernel: [    0.292937] uhci_hcd 0000:00:10.3: UHCI Host Controller
Dec 22 00:37:41 masterblaster kernel: [    0.293045] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Dec 22 00:37:41 masterblaster kernel: [    0.298450] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c800
Dec 22 00:37:41 masterblaster kernel: [    0.298743] hub 5-0:1.0: USB hub found
Dec 22 00:37:41 masterblaster kernel: [    0.298815] hub 5-0:1.0: 2 ports detected
Dec 22 00:37:41 masterblaster kernel: [    0.299030] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 22 00:37:41 masterblaster kernel: [    0.302559] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 22 00:37:41 masterblaster kernel: [    0.302643] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 22 00:37:41 masterblaster kernel: [    0.302894] mice: PS/2 mouse device common for all mice
Dec 22 00:37:41 masterblaster kernel: [    0.303132] rtc_cmos 00:02: RTC can wake from S4
Dec 22 00:37:41 masterblaster kernel: [    0.303249] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Dec 22 00:37:41 masterblaster kernel: [    0.303376] rtc0: alarms up to one year, y3k, 114 bytes nvram
Dec 22 00:37:41 masterblaster kernel: [    0.303603] device-mapper: uevent: version 1.0.3
Dec 22 00:37:41 masterblaster kernel: [    0.303817] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Dec 22 00:37:41 masterblaster kernel: [    0.309142] device-mapper: multipath: version 1.1.1 loaded
Dec 22 00:37:41 masterblaster kernel: [    0.309219] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 22 00:37:41 masterblaster kernel: [    0.313788] EISA: Probing bus 0 at eisa.0
Dec 22 00:37:41 masterblaster kernel: [    0.313864] EISA: Cannot allocate resource for mainboard
Dec 22 00:37:41 masterblaster kernel: [    0.313934] Cannot allocate resource for EISA slot 1
Dec 22 00:37:41 masterblaster kernel: [    0.314004] Cannot allocate resource for EISA slot 2
Dec 22 00:37:41 masterblaster kernel: [    0.314074] Cannot allocate resource for EISA slot 3
Dec 22 00:37:41 masterblaster kernel: [    0.314144] Cannot allocate resource for EISA slot 4
Dec 22 00:37:41 masterblaster kernel: [    0.314214] Cannot allocate resource for EISA slot 5
Dec 22 00:37:41 masterblaster kernel: [    0.314283] Cannot allocate resource for EISA slot 6
Dec 22 00:37:41 masterblaster kernel: [    0.314353] Cannot allocate resource for EISA slot 7
Dec 22 00:37:41 masterblaster kernel: [    0.314438] Cannot allocate resource for EISA slot 8
Dec 22 00:37:41 masterblaster kernel: [    0.314508] EISA: Detected 0 cards.
Dec 22 00:37:41 masterblaster kernel: [    0.316803] cpuidle: using governor ladder
Dec 22 00:37:41 masterblaster kernel: [    0.316876] cpuidle: using governor menu
Dec 22 00:37:41 masterblaster kernel: [    0.317326] TCP cubic registered
Dec 22 00:37:41 masterblaster kernel: [    0.317571] NET: Registered protocol family 10
Dec 22 00:37:41 masterblaster kernel: [    0.318086] lo: Disabled Privacy Extensions
Dec 22 00:37:41 masterblaster kernel: [    0.318433] NET: Registered protocol family 17
Dec 22 00:37:41 masterblaster kernel: [    0.318544] powernow-k8: Power state transitions not supported
Dec 22 00:37:41 masterblaster kernel: [    0.318636] Using IPI No-Shortcut mode
Dec 22 00:37:41 masterblaster kernel: [    0.318837] PM: Resume from disk failed.
Dec 22 00:37:41 masterblaster kernel: [    0.318856] registered taskstats version 1
Dec 22 00:37:41 masterblaster kernel: [    0.319191]   Magic number: 6:268:608
Dec 22 00:37:41 masterblaster kernel: [    0.319372] rtc_cmos 00:02: setting system clock to 2010-12-22 00:37:24 UTC (1292978244)
Dec 22 00:37:41 masterblaster kernel: [    0.319457] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 22 00:37:41 masterblaster kernel: [    0.319527] EDD information not available.
Dec 22 00:37:41 masterblaster kernel: [    0.328243] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Dec 22 00:37:41 masterblaster kernel: [    0.650396] usb 1-1: new high speed USB device using ehci_hcd and address 2
Dec 22 00:37:41 masterblaster kernel: [    0.914116] isapnp: No Plug & Play device found
Dec 22 00:37:41 masterblaster kernel: [    0.953120] Freeing initrd memory: 10512k freed
Dec 22 00:37:41 masterblaster kernel: [    0.963780] Freeing unused kernel memory: 684k freed
Dec 22 00:37:41 masterblaster kernel: [    0.964644] Write protecting the kernel text: 4932k
Dec 22 00:37:41 masterblaster kernel: [    0.964752] Write protecting the kernel read-only data: 1976k
Dec 22 00:37:41 masterblaster kernel: [    0.992021] udev[63]: starting version 163
Dec 22 00:37:41 masterblaster kernel: [    1.273407] pata_via 0000:00:0f.1: version 0.3.4
Dec 22 00:37:41 masterblaster kernel: [    1.273428] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 22 00:37:41 masterblaster kernel: [    1.312834] scsi0 : pata_via
Dec 22 00:37:41 masterblaster kernel: [    1.335508] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Dec 22 00:37:41 masterblaster kernel: [    1.338276] scsi1 : pata_via
Dec 22 00:37:41 masterblaster kernel: [    1.343401] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Dec 22 00:37:41 masterblaster kernel: [    1.343479] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Dec 22 00:37:41 masterblaster kernel: [    1.347128] sata_via 0000:00:0f.0: version 2.6
Dec 22 00:37:41 masterblaster kernel: [    1.347149] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Dec 22 00:37:41 masterblaster kernel: [    1.347274] sata_via 0000:00:0f.0: routed to hard irq line 10
Dec 22 00:37:41 masterblaster kernel: [    1.347728] scsi2 : sata_via
Dec 22 00:37:41 masterblaster kernel: [    1.347953] scsi3 : sata_via
Dec 22 00:37:41 masterblaster kernel: [    1.349759] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd400 irq 20
Dec 22 00:37:41 masterblaster kernel: [    1.349834] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xd408 irq 20
Dec 22 00:37:41 masterblaster kernel: [    1.350039]   alloc irq_desc for 23 on node -1
Dec 22 00:37:41 masterblaster kernel: [    1.350042]   alloc kstat_irqs on node -1
Dec 22 00:37:41 masterblaster kernel: [    1.350052] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 22 00:37:41 masterblaster kernel: [    1.350804] eth0: VIA Rhine II at 0xf9a00000, 00:15:f2:4c:35:9c, IRQ 23.
Dec 22 00:37:41 masterblaster kernel: [    1.351585] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
Dec 22 00:37:41 masterblaster kernel: [    1.351800]   alloc irq_desc for 17 on node -1
Dec 22 00:37:41 masterblaster kernel: [    1.351803]   alloc kstat_irqs on node -1
Dec 22 00:37:41 masterblaster kernel: [    1.351810] firewire_ohci 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 22 00:37:41 masterblaster kernel: [    1.404073] firewire_ohci: Added fw-ohci device 0000:00:0c.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Dec 22 00:37:41 masterblaster kernel: [    1.540961] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
Dec 22 00:37:41 masterblaster kernel: [    1.541038] ata1.00: 976773168 sectors, multi 16: LBA48 
Dec 22 00:37:41 masterblaster kernel: [    1.541134] ata1.00: limited to UDMA/33 due to 40-wire cable
Dec 22 00:37:41 masterblaster kernel: [    1.556013] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Dec 22 00:37:41 masterblaster kernel: [    1.567989] ata1.00: configured for UDMA/33
Dec 22 00:37:41 masterblaster kernel: [    1.568198] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKB-0 05.0 PQ: 0 ANSI: 5
Dec 22 00:37:41 masterblaster kernel: [    1.568481] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 22 00:37:41 masterblaster kernel: [    1.568961] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec 22 00:37:41 masterblaster kernel: [    1.569102] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 00:37:41 masterblaster kernel: [    1.569172] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 22 00:37:41 masterblaster kernel: [    1.569198] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 00:37:41 masterblaster kernel: [    1.569453]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
Dec 22 00:37:41 masterblaster kernel: [    1.649911] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 22 00:37:41 masterblaster kernel: [    1.852557] ata2.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
Dec 22 00:37:41 masterblaster kernel: [    1.852630] ata2.00: 320173056 sectors, multi 16: LBA48 
Dec 22 00:37:41 masterblaster kernel: [    1.852735] ata2.01: ATAPI: LITE-ON DVDRW SOHW-812S, US0Q, max UDMA/33
Dec 22 00:37:41 masterblaster kernel: [    1.852832] ata2.00: limited to UDMA/33 due to 40-wire cable
Dec 22 00:37:41 masterblaster kernel: [    1.868412] ata2.00: configured for UDMA/33
Dec 22 00:37:41 masterblaster kernel: [    1.884249] ata2.01: configured for UDMA/33
Dec 22 00:37:41 masterblaster kernel: [    1.884855] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
Dec 22 00:37:41 masterblaster kernel: [    1.885127] sd 1:0:0:0: Attached scsi generic sg1 type 0
Dec 22 00:37:41 masterblaster kernel: [    1.886268] scsi 1:0:1:0: CD-ROM            LITE-ON  DVDRW SOHW-812S  US0Q PQ: 0 ANSI: 5
Dec 22 00:37:41 masterblaster kernel: [    1.886912] sd 1:0:0:0: [sdb] 320173056 512-byte logical blocks: (163 GB/152 GiB)
Dec 22 00:37:41 masterblaster kernel: [    1.890639] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Dec 22 00:37:41 masterblaster kernel: [    1.890713] Uniform CD-ROM driver Revision: 3.20
Dec 22 00:37:41 masterblaster kernel: [    1.891283] sr 1:0:1:0: Attached scsi CD-ROM sr0
Dec 22 00:37:41 masterblaster kernel: [    1.891454] sr 1:0:1:0: Attached scsi generic sg2 type 5
Dec 22 00:37:41 masterblaster kernel: [    1.891699] sd 1:0:0:0: [sdb] Write Protect is off
Dec 22 00:37:41 masterblaster kernel: [    1.891773] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Dec 22 00:37:41 masterblaster kernel: [    1.891798] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 00:37:41 masterblaster kernel: [    1.892069]  sdb:
Dec 22 00:37:41 masterblaster kernel: [    1.904108] firewire_core: created device fw0: GUID 660050c50000c746, S400
Dec 22 00:37:41 masterblaster kernel: [    1.909016]  sdb1 < sdb5 >
Dec 22 00:37:41 masterblaster kernel: [    1.914787] sd 1:0:0:0: [sdb] Attached SCSI disk
Dec 22 00:37:41 masterblaster kernel: [    2.092017] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Dec 22 00:37:41 masterblaster kernel: [    2.910893] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Dec 22 00:37:41 masterblaster kernel: [    2.911076] EXT4-fs (sda5): write access will be enabled during recovery
Dec 22 00:37:41 masterblaster kernel: [    2.934386] EXT4-fs (sda5): recovery complete
Dec 22 00:37:41 masterblaster kernel: [    2.934926] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Dec 22 00:37:41 masterblaster kernel: [   14.359951] Adding 33554428k swap on /dev/sda10.  Priority:-1 extents:1 across:33554428k 
Dec 22 00:37:41 masterblaster kernel: [   14.403168] udev[347]: starting version 163
Dec 22 00:37:41 masterblaster kernel: [   14.610294] lp: driver loaded but no devices found
Dec 22 00:37:41 masterblaster kernel: [   14.668176] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 22 00:37:41 masterblaster kernel: [   14.715976] ACPI: resource vt596_smbus [io  0x0400-0x0407] conflicts with ACPI region SMRG [??? 0x00000400-0x0000040f flags 0x47]
Dec 22 00:37:41 masterblaster kernel: [   14.715983] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec 22 00:37:41 masterblaster kernel: [   14.717784] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Dec 22 00:37:41 masterblaster kernel: [   15.088196] Linux agpgart interface v0.103
Dec 22 00:37:41 masterblaster kernel: [   15.116407] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
Dec 22 00:37:41 masterblaster kernel: [   15.176511] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xde000000
Dec 22 00:37:41 masterblaster kernel: [   15.177140] parport_pc 00:0b: reported by Plug and Play ACPI
Dec 22 00:37:41 masterblaster kernel: [   15.177187] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 22 00:37:41 masterblaster kernel: [   15.250064] type=1400 audit(1293007059.425:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=592 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster kernel: [   15.280569] lp0: using parport0 (interrupt-driven).
Dec 22 00:37:41 masterblaster kernel: [   15.291917] type=1400 audit(1293007059.465:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=592 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster kernel: [   15.292177] type=1400 audit(1293007059.469:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=592 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster kernel: [   15.317324] psmouse serio1: ID: 10 00 64
Dec 22 00:37:41 masterblaster kernel: [   15.343181] ppdev: user-space parallel port driver
Dec 22 00:37:41 masterblaster kernel: [   15.408697] cfg80211: Calling CRDA to update world regulatory domain
Dec 22 00:37:41 masterblaster kernel: [   15.491749] cfg80211: World regulatory domain updated:
Dec 22 00:37:41 masterblaster kernel: [   15.491756]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 22 00:37:41 masterblaster kernel: [   15.491761]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:41 masterblaster kernel: [   15.491765]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:41 masterblaster kernel: [   15.491769]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:41 masterblaster kernel: [   15.491772]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:41 masterblaster kernel: [   15.491776]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:41 masterblaster kernel: [   15.643197] nvidia: module license 'NVIDIA' taints kernel.
Dec 22 00:37:41 masterblaster kernel: [   15.643204] Disabling lock debugging due to kernel taint
Dec 22 00:37:41 masterblaster kernel: [   17.210191] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
Dec 22 00:37:41 masterblaster kernel: [   17.252090] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Dec 22 00:37:41 masterblaster kernel: [   17.358572] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Dec 22 00:37:41 masterblaster kernel: [   17.358583]   alloc irq_desc for 22 on node -1
Dec 22 00:37:41 masterblaster kernel: [   17.358586]   alloc kstat_irqs on node -1
Dec 22 00:37:41 masterblaster kernel: [   17.358596] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec 22 00:37:41 masterblaster modem-manager: ModemManager (version 0.4) starting...
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: update_system_hostname
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPluginIfupdown: management mode: unmanaged
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 22 00:37:41 masterblaster avahi-daemon[809]: No service file found in /etc/avahi/services.
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: end _init.
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Network interface enumeration completed.
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 22 00:37:41 masterblaster avahi-daemon[809]: Server startup complete. Host name is masterblaster.local. Local service cookie is 521021128.
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 22 00:37:41 masterblaster NetworkManager[804]:    Ifupdown: get unmanaged devices count: 0
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: (154299216) ... get_connections.
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: (154299216) ... get_connections (managed=false): return empty list.
Dec 22 00:37:41 masterblaster NetworkManager[804]:    Ifupdown: get unmanaged devices count: 0
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:10.4/usb1/1-1/1-1:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Novatel
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Huawei
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> Networking is enabled by state file
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin MotoC
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Sierra
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Longcheer
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Nokia
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Generic
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Option High-Speed
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin SimTech
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin ZTE
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): carrier is OFF
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): new Ethernet device (driver: 'via-rhine' ifindex: 2)
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): now managed
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): bringing up device.
Dec 22 00:37:41 masterblaster kernel: [   17.510450] eth0: link down
Dec 22 00:37:41 masterblaster kernel: [   17.514542] type=1400 audit(1293007061.689:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=838 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): preparing device.
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (eth0): deactivating device (reason: 2).
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Ericsson MBM
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin AnyData
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Option
Dec 22 00:37:41 masterblaster modem-manager: Loaded plugin Gobi
Dec 22 00:37:41 masterblaster kernel: [   17.516415] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
Dec 22 00:37:41 masterblaster modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> modem-manager is now available
Dec 22 00:37:41 masterblaster kernel: [   17.543872] type=1400 audit(1293007061.717:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=842 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster kernel: [   17.544606] type=1400 audit(1293007061.721:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=842 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster kernel: [   17.544839] type=1400 audit(1293007061.721:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=842 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster NetworkManager[804]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> Trying to start the supplicant...
Dec 22 00:37:41 masterblaster modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Dec 22 00:37:41 masterblaster modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Dec 22 00:37:41 masterblaster modem-manager: (tty/ttyS1): could not get port's parent device
Dec 22 00:37:41 masterblaster kernel: [   17.581554] phy0: Selected rate control algorithm 'minstrel'
Dec 22 00:37:41 masterblaster kernel: [   17.582347] zd1211rw 1-1:1.0: phy0
Dec 22 00:37:41 masterblaster kernel: [   17.582377] usbcore: registered new interface driver zd1211rw
Dec 22 00:37:41 masterblaster kernel: [   17.619477] type=1400 audit(1293007061.793:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=849 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Dec 22 00:37:41 masterblaster NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (wlan0): new 802.11 WiFi device (driver: 'zd1211rw' ifindex: 3)
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (wlan0): now managed
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Dec 22 00:37:41 masterblaster NetworkManager[804]: <info> (wlan0): bringing up device.
Dec 22 00:37:41 masterblaster kernel: [   17.664784] type=1400 audit(1293007061.841:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=849 comm="apparmor_parser"
Dec 22 00:37:41 masterblaster kernel: [   17.668234] type=1400 audit(1293007061.845:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=849 comm="apparmor_parser"
Dec 22 00:37:42 masterblaster kernel: [   18.013867] zd1211rw 1-1:1.0: firmware version 4605
Dec 22 00:37:42 masterblaster kernel: [   18.052966] zd1211rw 1-1:1.0: zd1211 chip 0ace:1211 v4330 high 00-0e-3b AL2230_RF pa0 -----
Dec 22 00:37:42 masterblaster kernel: [   18.055323] cfg80211: Calling CRDA for country: US
Dec 22 00:37:42 masterblaster NetworkManager[804]: <info> (wlan0): preparing device.
Dec 22 00:37:42 masterblaster NetworkManager[804]: <info> (wlan0): deactivating device (reason: 2).
Dec 22 00:37:42 masterblaster kernel: [   18.069488] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 00:37:42 masterblaster kernel: [   18.077074] cfg80211: Regulatory domain changed to country: US
Dec 22 00:37:42 masterblaster kernel: [   18.077080]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 22 00:37:42 masterblaster kernel: [   18.077085]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec 22 00:37:42 masterblaster kernel: [   18.077089]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Dec 22 00:37:42 masterblaster kernel: [   18.077093]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:42 masterblaster kernel: [   18.077097]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:42 masterblaster kernel: [   18.077100]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 22 00:37:42 masterblaster kernel: [   18.077104]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Dec 22 00:37:42 masterblaster NetworkManager[804]: <info> (wlan0): supplicant interface state:  starting -> ready
Dec 22 00:37:42 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Dec 22 00:37:42 masterblaster kernel: [   18.112082] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
Dec 22 00:37:42 masterblaster kernel: [   18.234010]   alloc irq_desc for 16 on node -1
Dec 22 00:37:42 masterblaster kernel: [   18.234016]   alloc kstat_irqs on node -1
Dec 22 00:37:42 masterblaster kernel: [   18.234026] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 22 00:37:42 masterblaster kernel: [   18.234039] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 22 00:37:42 masterblaster kernel: [   18.235671] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Dec 22 00:37:42 masterblaster kernel: [   18.616252] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
Dec 22 00:37:42 masterblaster kernel: [   18.616271] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
Dec 22 00:37:42 masterblaster kernel: [   18.616496] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec 22 00:37:42 masterblaster kernel: [   18.616652] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Dec 22 00:37:43 masterblaster kernel: [   19.131449] codec_read: codec 0 is not valid [0xfe0000]
Dec 22 00:37:43 masterblaster kernel: [   19.138373] codec_read: codec 0 is not valid [0xfe0000]
Dec 22 00:37:43 masterblaster kernel: [   19.146977] codec_read: codec 0 is not valid [0xfe0000]
Dec 22 00:37:43 masterblaster kernel: [   19.153893] codec_read: codec 0 is not valid [0xfe0000]
Dec 22 00:37:43 masterblaster init: plymouth-splash main process (987) terminated with status 1
Dec 22 00:39:33 masterblaster gdm-binary[1153]: WARNING: Unable to find users: no seat-id found
Dec 22 00:39:34 masterblaster gdm-binary[1153]: WARNING: GdmDisplay: display lasted 0.074761 seconds
Dec 22 00:39:34 masterblaster gdm-session-worker[1238]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Dec 22 00:39:35 masterblaster polkitd[1325]: started daemon version 0.96 using authority implementation `local' version `0.96'
Dec 22 00:39:35 masterblaster anacron[1374]: Anacron 2.3 started on 2010-12-22
Dec 22 00:39:35 masterblaster anacron[1374]: Will run job `cron.daily' in 5 min.
Dec 22 00:39:35 masterblaster anacron[1374]: Jobs will be executed sequentially
Dec 22 00:39:36 masterblaster kernel: [  132.701432] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Successfully called chroot.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Successfully dropped privileges.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Successfully limited resources.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Running.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Watchdog thread running.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Canary thread running.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Successfully made thread 1399 of process 1399 (n/a) owned by '1000' high priority at nice level -11.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Supervising 1 threads of 1 processes of 1 users.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Successfully made thread 1408 of process 1399 (n/a) owned by '1000' RT at priority 5.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Supervising 2 threads of 1 processes of 1 users.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Successfully made thread 1409 of process 1399 (n/a) owned by '1000' RT at priority 5.
Dec 22 00:39:37 masterblaster rtkit-daemon[1403]: Supervising 3 threads of 1 processes of 1 users.
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) starting connection 'Auto instadeth'
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0/wireless): access point 'Auto instadeth' has security, but secrets are required.
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Dec 22 00:39:39 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 22 00:39:40 masterblaster nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Dec 22 00:39:40 masterblaster nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0/wireless): connection 'Auto instadeth' has security, and secrets exist.  No new secrets needed.
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Config: added 'ssid' value 'instadeth'
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Config: added 'scan_ssid' value '1'
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Config: added 'psk' value '<omitted>'
Dec 22 00:39:46 masterblaster NetworkManager[804]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 22 00:39:46 masterblaster NetworkManager[804]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> Config: set interface ap_scan to 1
Dec 22 00:39:46 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Dec 22 00:39:47 masterblaster wpa_supplicant[854]: Trying to associate with 00:14:bf:29:5e:66 (SSID='instadeth' freq=2457 MHz)
Dec 22 00:39:47 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec 22 00:39:47 masterblaster kernel: [  143.406659] wlan0: authenticate with 00:14:bf:29:5e:66 (try 1)
Dec 22 00:39:47 masterblaster wpa_supplicant[854]: Associated with 00:14:bf:29:5e:66
Dec 22 00:39:47 masterblaster kernel: [  143.408287] wlan0: authenticated
Dec 22 00:39:47 masterblaster kernel: [  143.408310] wlan0: associate with 00:14:bf:29:5e:66 (try 1)
Dec 22 00:39:47 masterblaster kernel: [  143.410524] wlan0: RX AssocResp from 00:14:bf:29:5e:66 (capab=0x411 status=0 aid=1)
Dec 22 00:39:47 masterblaster kernel: [  143.410529] wlan0: associated
Dec 22 00:39:47 masterblaster kernel: [  143.411378] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 22 00:39:47 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  associating -> associated
Dec 22 00:39:47 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec 22 00:39:47 masterblaster kernel: [  143.430424] padlock: VIA PadLock not detected.
Dec 22 00:39:47 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec 22 00:39:48 masterblaster wpa_supplicant[854]: WPA: Key negotiation completed with 00:14:bf:29:5e:66 [PTK=CCMP GTK=CCMP]
Dec 22 00:39:48 masterblaster wpa_supplicant[854]: CTRL-EVENT-CONNECTED - Connection to 00:14:bf:29:5e:66 completed (auth) [id=0 id_str=]
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'instadeth'.
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> dhclient started with pid 1559
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 22 00:39:48 masterblaster dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 22 00:39:48 masterblaster dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 22 00:39:48 masterblaster dhclient: All rights reserved.
Dec 22 00:39:48 masterblaster dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 22 00:39:48 masterblaster dhclient: 
Dec 22 00:39:48 masterblaster NetworkManager[804]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 22 00:39:48 masterblaster dhclient: Listening on LPF/wlan0/00:0e:3b:06:40:0d
Dec 22 00:39:48 masterblaster dhclient: Sending on   LPF/wlan0/00:0e:3b:06:40:0d
Dec 22 00:39:48 masterblaster dhclient: Sending on   Socket/fallback
Dec 22 00:39:48 masterblaster dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Dec 22 00:39:49 masterblaster avahi-daemon[809]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::20e:3bff:fe06:400d.
Dec 22 00:39:49 masterblaster avahi-daemon[809]: New relevant interface wlan0.IPv6 for mDNS.
Dec 22 00:39:49 masterblaster avahi-daemon[809]: Registering new address record for fe80::20e:3bff:fe06:400d on wlan0.*.
Dec 22 00:39:49 masterblaster dhclient: DHCPOFFER of 10.0.0.101 from 10.0.0.1
Dec 22 00:39:49 masterblaster dhclient: DHCPREQUEST of 10.0.0.101 on wlan0 to 255.255.255.255 port 67
Dec 22 00:39:49 masterblaster dhclient: DHCPACK of 10.0.0.101 from 10.0.0.1
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   address 10.0.0.101
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   prefix 24 (255.255.255.0)
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   gateway 10.0.0.1
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   nameserver '208.67.222.222'
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   nameserver '208.67.220.220'
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   nameserver '4.2.2.2'
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info>   domain name 'wildblue.com'
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 22 00:39:49 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 22 00:39:49 masterblaster avahi-daemon[809]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.101.
Dec 22 00:39:49 masterblaster avahi-daemon[809]: New relevant interface wlan0.IPv4 for mDNS.
Dec 22 00:39:49 masterblaster avahi-daemon[809]: Registering new address record for 10.0.0.101 on wlan0.IPv4.
Dec 22 00:39:49 masterblaster dhclient: bound to 10.0.0.101 -- renewal in 43190 seconds.
Dec 22 00:39:50 masterblaster NetworkManager[804]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Dec 22 00:39:50 masterblaster NetworkManager[804]: <info> Policy set 'Auto instadeth' (wlan0) as default for IPv4 routing and DNS.
Dec 22 00:39:50 masterblaster NetworkManager[804]: <info> Activation (wlan0) successful, device activated.
Dec 22 00:39:50 masterblaster NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 22 00:39:58 masterblaster kernel: [  154.128014] wlan0: no IPv6 routers present
Dec 22 00:40:04 masterblaster ntpdate[1613]: no server suitable for synchronization found
Dec 22 00:44:35 masterblaster anacron[1374]: Job `cron.daily' started
Dec 22 00:44:36 masterblaster anacron[1701]: Updated timestamp for job `cron.daily' to 2010-12-22
Dec 22 01:13:11 masterblaster wpa_supplicant[854]: WPA: Group rekeying completed with 00:14:bf:29:5e:66 [GTK=CCMP]
Dec 22 01:13:11 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  completed -> group handshake
Dec 22 01:13:11 masterblaster NetworkManager[804]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Dec 22 01:15:06 masterblaster rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="759" x-info="http://www.rsyslog.com"] rsyslogd

```

Went to System > Admin > NVIDIA XServer settings:

```

You do not appear to be using the NVIDIA X Driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root and restart the X server.
```

Of course, I knew I wasn't running the NVIDIA driver, being in recovery > low-graphics mode, so I brought up the terminal and ran:

```
sudo nvidia-xconfig
```

Gave the password, got:

```

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

Great, I think.  How do I restart the X server?

---

### Post by yuler on 2010-12-22
I'll try to log my results upon following the suggestions from this thread (found by search > restart X server)

[http://ubuntuforums.org/showthread.php?t=1648076&highlight=restart+server](http://ubuntuforums.org/showthread.php?t=1648076&highlight=restart+server)

```

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

```

glxinfo | grep vendor
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils

```

```

cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "GatewayVX1120"
    HorizSync       30.0 - 121.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x1024_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024_85 +0+0; 1280x1024_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by yuler on 2010-12-22
I wasn't sure how to restart the X server, so I restarted the OS from the GUI, knowing it'd have to restart X Server in the process.  

Selected normal boot.  Saw the "codec 0" error flash, but the desktop came up.  Went to System > Admin > NVIDA X Server settings.  Got no error, saw the normal specs, and assume it solved itself with the "nvidia-xconfig" command.

---

