---
title: "init ureadahead error and no splash screen"
date: 2010-06-08
forum: General Help
---

### Post by trpnblies7 on 2010-06-08
**UPDATE:** I solved it. Turns out it was a combination of installing the newest kernel (2.6.34) and the Plymouth/boot issue listed in the common fixes thread. That also explains why I've had such an ugly splash screen since installing 10.04.

---------------------------------------

I turned on my computer yesterday and out of nowhere I've been getting this message before the 10.04 splash/loading screen:

"init ureadahead main process (321) terminated with status 5"

Additionally, I'm no longer getting the Ubuntu logo on the splash screen. Instead it's just the purple background and shows the text of what's loading. The same thing happens when I shutdown, I get lines of text of all the processes that are closing rather than the typical splash screen.

I searched for the ureadahead issue, and from what I read, people seem to get that kind of message when /var is on a separate partition. I only have one partition on my hard drive, though, so that's not my issue. I can make that message go away by disabling ureadahead.conf, but I don't think that's actually solving whatever the problem is (plus, I still have the splash screen issue).

Any idea what's causing either or both of these problems?

Here's my syslog from when I turned on my computer a little while ago, if that helps at all:

```
Jun  8 16:49:13 brian-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun  8 16:49:13 brian-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="689" x-info="http://www.rsyslog.com"] (re)start
Jun  8 16:49:13 brian-desktop rsyslogd: rsyslogd's groupid changed to 103
Jun  8 16:49:13 brian-desktop rsyslogd: rsyslogd's userid changed to 101
Jun  8 16:49:13 brian-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Linux version 2.6.34-020634-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #020634 SMP Mon May 17 20:34:55 UTC 2010
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] DMI 2.4 present.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] last_pfn = 0xdfee0 max_arch_pfn = 0x100000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] MTRR default type: uncachable
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   00000-9FFFF write-back
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   C0000-CBFFF write-protect
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   CC000-EFFFF uncachable
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   F0000-FFFFF write-through
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   2 base 100000000 mask FE0000000 write-back
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   3 base 0DFF00000 mask FFFF00000 uncachable
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   4 disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   5 disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   6 disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   7 disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] modified physical RAM map:
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfee0000 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dff00000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] found SMP MP-table at [c00f5200] f5200
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] RAMDISK: 377dc000 - 37ff0000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Allocated new RAMDISK: 0091c000 - 0112f85a
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Move RAMDISK from 00000000377dc000 - 0000000037fef859 to 0091c000 - 0112f859
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: RSDP 000f6bc0 00014 (v00 GBT   )
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: RSDT dfee3040 00034 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: FACP dfee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: DSDT dfee3180 04B32 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: FACS dfee0000 00040
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: HPET dfee7e00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: MCFG dfee7e80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: APIC dfee7d00 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] 2694MB HIGHMEM available.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Zone PFN ranges:
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x000dfee0
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000dfee0
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] On node 0 totalpages: 917104
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c07c5200, node_mem_map c1131020
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   DMA zone: 3952 pages, LIFO batch:0
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   HighMem zone: 5390 pages used for memmap
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   HighMem zone: 684500 pages, LIFO batch:31
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Using APIC driver default
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] nr_irqs_gsi: 24
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Allocating PCI resources starting at dff00000 (gap: dff00000:10100000)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s35860 r0 d21484 u1048576
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] pcpu-alloc: s35860 r0 d21484 u1048576 alloc=1*4194304
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 909938
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634-generic root=UUID=999be7fc-e682-4c85-bfb6-366464b28d81 ro quiet splash
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Initializing CPU#0
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] allocated 18344300 bytes of page_cgroup
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Subtract (52 early reservations)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #2 [0000100000 - 0000917fbc]   TEXT DATA BSS
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #3 [0000918000 - 000091b0f6]             BRK
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #4 [00000f5210 - 0000100000]   BIOS reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #5 [00000f5200 - 00000f5210]    MP-table mpf
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #6 [000009f800 - 00000f0d00]   BIOS reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #7 [00000f0e94 - 00000f5200]   BIOS reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #8 [00000f0d00 - 00000f0e94]    MP-table mpc
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #12 [000091c000 - 0001130000]     NEW RAMDISK
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #13 [0001130000 - 0001131000]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #14 [0001131000 - 0002d31000]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #15 [0002d31000 - 0002d31004]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #16 [0002d31040 - 0002d31100]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #17 [0002d31100 - 0002d31154]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #18 [0002d31180 - 0002d34180]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #19 [0002d34180 - 0002d34280]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #20 [0002d34280 - 0002d40280]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #21 [0002d40280 - 0002d402a5]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #22 [0002d402c0 - 0002d402e7]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #23 [0002d40300 - 0002d4046c]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #24 [0002d40480 - 0002d404c0]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #25 [0002d404c0 - 0002d40500]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #26 [0002d40500 - 0002d40540]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #27 [0002d40540 - 0002d40580]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #28 [0002d40580 - 0002d405c0]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #29 [0002d405c0 - 0002d40600]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #30 [0002d40600 - 0002d40640]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #31 [0002d40640 - 0002d40680]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #32 [0002d40680 - 0002d406c0]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #33 [0002d406c0 - 0002d40700]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #34 [0002d40700 - 0002d40710]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #35 [0002d40740 - 0002d40750]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #36 [0002d40780 - 0002d407ee]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #37 [0002d40800 - 0002d4086e]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #38 [0003000000 - 000300e000]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #39 [0003100000 - 000310e000]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #40 [0003200000 - 000320e000]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #41 [0003300000 - 000330e000]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #42 [0002d42880 - 0002d42884]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #43 [0002d428c0 - 0002d428c4]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #44 [0002d42900 - 0002d42910]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #45 [0002d42940 - 0002d42950]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #46 [0002d42980 - 0002d42a20]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #47 [0002d42a40 - 0002d42a88]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #48 [0002d42ac0 - 0002d46ac0]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #49 [0002d46ac0 - 0002dc6ac0]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #50 [0002dc6ac0 - 0002e06ac0]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]   #51 [000330e000 - 000448c96c]         BOOTMEM
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000dfee0)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Memory: 3604144k/3668864k available (4751k kernel code, 64272k reserved, 2222k data, 712k init, 2759560k highmem)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] virtual kernel memory layout:
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]       .init : 0xc07d0000 - 0xc0882000   ( 712 kB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]       .data : 0xc05a3f6a - 0xc07cf788   (2222 kB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc05a3f6a   (4751 kB)
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] console [tty0] enabled
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] hpet clockevent registered
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jun  8 16:49:13 brian-desktop kernel: [    0.000000] Detected 3000.022 MHz processor.
Jun  8 16:49:13 brian-desktop kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.04 BogoMIPS (lpj=12000088)
Jun  8 16:49:13 brian-desktop kernel: [    0.004023] Security Framework initialized
Jun  8 16:49:13 brian-desktop kernel: [    0.004029] SELinux:  Disabled at boot.
Jun  8 16:49:13 brian-desktop kernel: [    0.004036] Mount-cache hash table entries: 512
Jun  8 16:49:13 brian-desktop kernel: [    0.004143] Initializing cgroup subsys ns
Jun  8 16:49:13 brian-desktop kernel: [    0.004146] Initializing cgroup subsys cpuacct
Jun  8 16:49:13 brian-desktop kernel: [    0.004150] Initializing cgroup subsys memory
Jun  8 16:49:13 brian-desktop kernel: [    0.004157] Initializing cgroup subsys devices
Jun  8 16:49:13 brian-desktop kernel: [    0.004159] Initializing cgroup subsys freezer
Jun  8 16:49:13 brian-desktop kernel: [    0.004160] Initializing cgroup subsys net_cls
Jun  8 16:49:13 brian-desktop kernel: [    0.004178] CPU: Physical Processor ID: 0
Jun  8 16:49:13 brian-desktop kernel: [    0.004180] CPU: Processor Core ID: 0
Jun  8 16:49:13 brian-desktop kernel: [    0.004183] mce: CPU supports 6 MCE banks
Jun  8 16:49:13 brian-desktop kernel: [    0.004190] CPU0: Thermal monitoring enabled (TM2)
Jun  8 16:49:13 brian-desktop kernel: [    0.004192] using mwait in idle threads.
Jun  8 16:49:13 brian-desktop kernel: [    0.004198] Performance Events: Core2 events, Intel PMU driver.
Jun  8 16:49:13 brian-desktop kernel: [    0.004204] ... version:                2
Jun  8 16:49:13 brian-desktop kernel: [    0.004206] ... bit width:              40
Jun  8 16:49:13 brian-desktop kernel: [    0.004207] ... generic registers:      2
Jun  8 16:49:13 brian-desktop kernel: [    0.004208] ... value mask:             000000ffffffffff
Jun  8 16:49:13 brian-desktop kernel: [    0.004210] ... max period:             000000007fffffff
Jun  8 16:49:13 brian-desktop kernel: [    0.004211] ... fixed-purpose events:   3
Jun  8 16:49:13 brian-desktop kernel: [    0.004213] ... event mask:             0000000700000003
Jun  8 16:49:13 brian-desktop kernel: [    0.004216] Checking 'hlt' instruction... OK.
Jun  8 16:49:13 brian-desktop kernel: [    0.022413] ACPI: Core revision 20100121
Jun  8 16:49:13 brian-desktop kernel: [    0.028019] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun  8 16:49:13 brian-desktop kernel: [    0.028025] ftrace: allocating 24557 entries in 49 pages
Jun  8 16:49:13 brian-desktop kernel: [    0.032030] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun  8 16:49:13 brian-desktop kernel: [    0.032330] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  8 16:49:13 brian-desktop kernel: [    0.074348] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
Jun  8 16:49:13 brian-desktop kernel: [    0.076000] Booting Node   0, Processors  #1
Jun  8 16:49:13 brian-desktop kernel: [    0.008000] Initializing CPU#1
Jun  8 16:49:13 brian-desktop kernel: [    0.164012] Brought up 2 CPUs
Jun  8 16:49:13 brian-desktop kernel: [    0.164014] Total of 2 processors activated (11999.99 BogoMIPS).
Jun  8 16:49:13 brian-desktop kernel: [    0.165002] devtmpfs: initialized
Jun  8 16:49:13 brian-desktop kernel: [    0.165211] regulator: core version 0.5
Jun  8 16:49:13 brian-desktop kernel: [    0.165232] Time: 20:48:59  Date: 06/08/10
Jun  8 16:49:13 brian-desktop kernel: [    0.165259] NET: Registered protocol family 16
Jun  8 16:49:13 brian-desktop kernel: [    0.165342] EISA bus registered
Jun  8 16:49:13 brian-desktop kernel: [    0.165350] ACPI: bus type pci registered
Jun  8 16:49:13 brian-desktop kernel: [    0.165402] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Jun  8 16:49:13 brian-desktop kernel: [    0.165404] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Jun  8 16:49:13 brian-desktop kernel: [    0.165406] PCI: Using MMCONFIG for extended config space
Jun  8 16:49:13 brian-desktop kernel: [    0.165408] PCI: Using configuration type 1 for base access
Jun  8 16:49:13 brian-desktop kernel: [    0.166016] bio: create slab <bio-0> at 0
Jun  8 16:49:13 brian-desktop kernel: [    0.166016] ACPI: EC: Look up EC in DSDT
Jun  8 16:49:13 brian-desktop kernel: [    0.171371] ACPI: Interpreter enabled
Jun  8 16:49:13 brian-desktop kernel: [    0.171388] ACPI: (supports S0 S3 S4 S5)
Jun  8 16:49:13 brian-desktop kernel: [    0.171407] ACPI: Using IOAPIC for interrupt routing
Jun  8 16:49:13 brian-desktop kernel: [    0.176339] ACPI: No dock devices found.
Jun  8 16:49:13 brian-desktop kernel: [    0.176343] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun  8 16:49:13 brian-desktop kernel: [    0.176419] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  8 16:49:13 brian-desktop kernel: [    0.176559] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun  8 16:49:13 brian-desktop kernel: [    0.176562] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.176564] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.176566] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.176568] pci_root PNP0A03:00: host bridge window [mem 0xdff00000-0xfebfffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.176627] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun  8 16:49:13 brian-desktop kernel: [    0.176629] pci 0000:00:01.0: PME# disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.176683] pci 0000:00:1a.0: reg 20: [io  0xd100-0xd11f]
Jun  8 16:49:13 brian-desktop kernel: [    0.176737] pci 0000:00:1a.1: reg 20: [io  0xd200-0xd21f]
Jun  8 16:49:13 brian-desktop kernel: [    0.176790] pci 0000:00:1a.2: reg 20: [io  0xd000-0xd01f]
Jun  8 16:49:13 brian-desktop kernel: [    0.176835] pci 0000:00:1a.7: reg 10: [mem 0xfb004000-0xfb0043ff]
Jun  8 16:49:13 brian-desktop kernel: [    0.176895] pci 0000:00:1b.0: reg 10: [mem 0xfb000000-0xfb003fff 64bit]
Jun  8 16:49:13 brian-desktop kernel: [    0.176930] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun  8 16:49:13 brian-desktop kernel: [    0.176933] pci 0000:00:1b.0: PME# disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.176987] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun  8 16:49:13 brian-desktop kernel: [    0.176990] pci 0000:00:1c.0: PME# disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.177046] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jun  8 16:49:13 brian-desktop kernel: [    0.177049] pci 0000:00:1c.3: PME# disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.177104] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun  8 16:49:13 brian-desktop kernel: [    0.177107] pci 0000:00:1c.4: PME# disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.177149] pci 0000:00:1d.0: reg 20: [io  0xd300-0xd31f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177202] pci 0000:00:1d.1: reg 20: [io  0xd400-0xd41f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177255] pci 0000:00:1d.2: reg 20: [io  0xd500-0xd51f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177301] pci 0000:00:1d.7: reg 10: [mem 0xfb005000-0xfb0053ff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177429] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
Jun  8 16:49:13 brian-desktop kernel: [    0.177433] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
Jun  8 16:49:13 brian-desktop kernel: [    0.177436] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
Jun  8 16:49:13 brian-desktop kernel: [    0.177439] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
Jun  8 16:49:13 brian-desktop kernel: [    0.177479] pci 0000:00:1f.2: reg 10: [io  0xd600-0xd607]
Jun  8 16:49:13 brian-desktop kernel: [    0.177483] pci 0000:00:1f.2: reg 14: [io  0xd700-0xd703]
Jun  8 16:49:13 brian-desktop kernel: [    0.177488] pci 0000:00:1f.2: reg 18: [io  0xd800-0xd807]
Jun  8 16:49:13 brian-desktop kernel: [    0.177492] pci 0000:00:1f.2: reg 1c: [io  0xd900-0xd903]
Jun  8 16:49:13 brian-desktop kernel: [    0.177497] pci 0000:00:1f.2: reg 20: [io  0xda00-0xda0f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177501] pci 0000:00:1f.2: reg 24: [io  0xdb00-0xdb0f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177538] pci 0000:00:1f.3: reg 10: [mem 0xfb006000-0xfb0060ff 64bit]
Jun  8 16:49:13 brian-desktop kernel: [    0.177548] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177579] pci 0000:00:1f.5: reg 10: [io  0xdd00-0xdd07]
Jun  8 16:49:13 brian-desktop kernel: [    0.177584] pci 0000:00:1f.5: reg 14: [io  0xde00-0xde03]
Jun  8 16:49:13 brian-desktop kernel: [    0.177588] pci 0000:00:1f.5: reg 18: [io  0xdf00-0xdf07]
Jun  8 16:49:13 brian-desktop kernel: [    0.177592] pci 0000:00:1f.5: reg 1c: [io  0xe000-0xe003]
Jun  8 16:49:13 brian-desktop kernel: [    0.177597] pci 0000:00:1f.5: reg 20: [io  0xe100-0xe10f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177602] pci 0000:00:1f.5: reg 24: [io  0xe200-0xe20f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177659] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177667] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.177674] pci 0000:01:00.0: reg 1c: [mem 0xf4000000-0xf5ffffff 64bit]
Jun  8 16:49:13 brian-desktop kernel: [    0.177678] pci 0000:01:00.0: reg 24: [io  0xa000-0xa07f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177683] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.177709] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun  8 16:49:13 brian-desktop kernel: [    0.177711] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177714] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177717] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.177750] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jun  8 16:49:13 brian-desktop kernel: [    0.177753] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177757] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.177762] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.177829] pci 0000:03:00.0: reg 10: [io  0xb000-0xb007]
Jun  8 16:49:13 brian-desktop kernel: [    0.177837] pci 0000:03:00.0: reg 14: [io  0xb100-0xb103]
Jun  8 16:49:13 brian-desktop kernel: [    0.177845] pci 0000:03:00.0: reg 18: [io  0xb200-0xb207]
Jun  8 16:49:13 brian-desktop kernel: [    0.177853] pci 0000:03:00.0: reg 1c: [io  0xb300-0xb303]
Jun  8 16:49:13 brian-desktop kernel: [    0.177861] pci 0000:03:00.0: reg 20: [io  0xb400-0xb40f]
Jun  8 16:49:13 brian-desktop kernel: [    0.177917] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Jun  8 16:49:13 brian-desktop kernel: [    0.177920] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177923] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf8ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.177928] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.177991] pci 0000:04:00.0: reg 10: [io  0xc000-0xc0ff]
Jun  8 16:49:13 brian-desktop kernel: [    0.178010] pci 0000:04:00.0: reg 18: [mem 0xfa000000-0xfa000fff 64bit]
Jun  8 16:49:13 brian-desktop kernel: [    0.178030] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.178072] pci 0000:04:00.0: supports D1 D2
Jun  8 16:49:13 brian-desktop kernel: [    0.178074] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
Jun  8 16:49:13 brian-desktop kernel: [    0.178078] pci 0000:04:00.0: PME# disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.178098] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
Jun  8 16:49:13 brian-desktop kernel: [    0.178101] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
Jun  8 16:49:13 brian-desktop kernel: [    0.178104] pci 0000:00:1c.4:   bridge window [mem 0xf9000000-0xfaffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.178109] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.178161] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
Jun  8 16:49:13 brian-desktop kernel: [    0.178165] pci 0000:00:1e.0:   bridge window [io  0x9000-0x9fff]
Jun  8 16:49:13 brian-desktop kernel: [    0.178168] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.178173] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.178175] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun  8 16:49:13 brian-desktop kernel: [    0.178177] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun  8 16:49:13 brian-desktop kernel: [    0.178179] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun  8 16:49:13 brian-desktop kernel: [    0.178181] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Jun  8 16:49:13 brian-desktop kernel: [    0.178183] pci 0000:00:1e.0:   bridge window [mem 0xdff00000-0xfebfffff] (subtractive decode)
Jun  8 16:49:13 brian-desktop kernel: [    0.178199] pci_bus 0000:00: on NUMA node 0
Jun  8 16:49:13 brian-desktop kernel: [    0.178202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  8 16:49:13 brian-desktop kernel: [    0.178359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jun  8 16:49:13 brian-desktop kernel: [    0.178416] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Jun  8 16:49:13 brian-desktop kernel: [    0.178478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Jun  8 16:49:13 brian-desktop kernel: [    0.178532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jun  8 16:49:13 brian-desktop kernel: [    0.192880] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun  8 16:49:13 brian-desktop kernel: [    0.192957] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  8 16:49:13 brian-desktop kernel: [    0.193033] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jun  8 16:49:13 brian-desktop kernel: [    0.193109] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
Jun  8 16:49:13 brian-desktop kernel: [    0.193186] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun  8 16:49:13 brian-desktop kernel: [    0.193261] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jun  8 16:49:13 brian-desktop kernel: [    0.193337] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun  8 16:49:13 brian-desktop kernel: [    0.193412] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
Jun  8 16:49:13 brian-desktop kernel: [    0.193503] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun  8 16:49:13 brian-desktop kernel: [    0.193507] vgaarb: loaded
Jun  8 16:49:13 brian-desktop kernel: [    0.193591] SCSI subsystem initialized
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] libata version 3.00 loaded.
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] usbcore: registered new interface driver usbfs
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] usbcore: registered new interface driver hub
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] usbcore: registered new device driver usb
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] ACPI: WMI: Mapper loaded
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] PCI: Using ACPI for IRQ routing
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] PCI: pci_cache_line_size set to 64 bytes
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] reserve RAM buffer: 00000000dfee0000 - 00000000dfffffff 
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] NetLabel: Initializing
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] NetLabel:  domain hash size = 128
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] NetLabel:  unlabeled traffic allowed by default
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun  8 16:49:13 brian-desktop kernel: [    0.193619] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jun  8 16:49:13 brian-desktop kernel: [    0.200020] Switching to clocksource tsc
Jun  8 16:49:13 brian-desktop kernel: [    0.201648] pnp: PnP ACPI init
Jun  8 16:49:13 brian-desktop kernel: [    0.201655] ACPI: bus type pnp registered
Jun  8 16:49:13 brian-desktop kernel: [    0.203850] pnp: PnP ACPI: found 15 devices
Jun  8 16:49:13 brian-desktop kernel: [    0.203852] ACPI: ACPI bus type pnp unregistered
Jun  8 16:49:13 brian-desktop kernel: [    0.203855] PnPBIOS: Disabled by ACPI PNP
Jun  8 16:49:13 brian-desktop kernel: [    0.203862] system 00:01: [io  0x04d0-0x04d1] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203864] system 00:01: [io  0x0290-0x029f] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203867] system 00:01: [io  0x0800-0x087f] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203876] system 00:01: [io  0x0290-0x0294] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203878] system 00:01: [io  0x0880-0x088f] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203885] system 00:0b: [io  0x0400-0x04bf] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203889] system 00:0c: [mem 0xf0000000-0xf3ffffff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203894] system 00:0d: [mem 0x000cce00-0x000cffff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203896] system 00:0d: [mem 0x000f0000-0x000f7fff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203898] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203900] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203903] system 00:0d: [mem 0xdfee0000-0xdfefffff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203905] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203907] system 00:0d: [mem 0x00100000-0xdfedffff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203910] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203912] system 00:0d: [mem 0xfed10000-0xfed1dfff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203914] system 00:0d: [mem 0xfed20000-0xfed8ffff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203917] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203919] system 00:0d: [mem 0xffb00000-0xffb7ffff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203921] system 00:0d: [mem 0xfff00000-0xffffffff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.203923] system 00:0d: [mem 0x000e0000-0x000effff] has been reserved
Jun  8 16:49:13 brian-desktop kernel: [    0.238573] pci 0000:00:1c.0: BAR 14: assigned [mem 0xfb100000-0xfb2fffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238576] pci 0000:00:1c.0: BAR 15: assigned [mem 0xfb300000-0xfb4fffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238579] pci 0000:00:1c.3: BAR 15: assigned [mem 0xfb500000-0xfb6fffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238582] pci 0000:00:1c.4: BAR 15: assigned [mem 0xfb700000-0xfb8fffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238585] pci 0000:01:00.0: BAR 6: assigned [mem 0xf7000000-0xf701ffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238587] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun  8 16:49:13 brian-desktop kernel: [    0.238589] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238592] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238595] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238599] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jun  8 16:49:13 brian-desktop kernel: [    0.238601] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238605] pci 0000:00:1c.0:   bridge window [mem 0xfb100000-0xfb2fffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238608] pci 0000:00:1c.0:   bridge window [mem 0xfb300000-0xfb4fffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238613] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Jun  8 16:49:13 brian-desktop kernel: [    0.238616] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238620] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf8ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238623] pci 0000:00:1c.3:   bridge window [mem 0xfb500000-0xfb6fffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238628] pci 0000:04:00.0: BAR 6: assigned [mem 0xfb700000-0xfb71ffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238630] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
Jun  8 16:49:13 brian-desktop kernel: [    0.238633] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238637] pci 0000:00:1c.4:   bridge window [mem 0xf9000000-0xfaffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238640] pci 0000:00:1c.4:   bridge window [mem 0xfb700000-0xfb8fffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238645] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
Jun  8 16:49:13 brian-desktop kernel: [    0.238647] pci 0000:00:1e.0:   bridge window [io  0x9000-0x9fff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238651] pci 0000:00:1e.0:   bridge window [mem disabled]
Jun  8 16:49:13 brian-desktop kernel: [    0.238654] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Jun  8 16:49:13 brian-desktop kernel: [    0.238662]   alloc irq_desc for 16 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.238664]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.238668] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 16:49:13 brian-desktop kernel: [    0.238671] pci 0000:00:01.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.238677] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 16:49:13 brian-desktop kernel: [    0.238681] pci 0000:00:1c.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.238686]   alloc irq_desc for 19 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.238688]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.238691] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun  8 16:49:13 brian-desktop kernel: [    0.238694] pci 0000:00:1c.3: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.238700] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 16:49:13 brian-desktop kernel: [    0.238703] pci 0000:00:1c.4: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.238708] pci 0000:00:1e.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.238711] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun  8 16:49:13 brian-desktop kernel: [    0.238714] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238716] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238718] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238721] pci_bus 0000:00: resource 8 [mem 0xdff00000-0xfebfffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238723] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238725] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf7ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238727] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238729] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238731] pci_bus 0000:02: resource 1 [mem 0xfb100000-0xfb2fffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238732] pci_bus 0000:02: resource 2 [mem 0xfb300000-0xfb4fffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238734] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238736] pci_bus 0000:03: resource 1 [mem 0xf8000000-0xf8ffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238738] pci_bus 0000:03: resource 2 [mem 0xfb500000-0xfb6fffff 64bit pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238740] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238742] pci_bus 0000:04: resource 1 [mem 0xf9000000-0xfaffffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238744] pci_bus 0000:04: resource 2 [mem 0xfb700000-0xfb8fffff pref]
Jun  8 16:49:13 brian-desktop kernel: [    0.238746] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238747] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun  8 16:49:13 brian-desktop kernel: [    0.238749] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238751] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238753] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238754] pci_bus 0000:05: resource 8 [mem 0xdff00000-0xfebfffff]
Jun  8 16:49:13 brian-desktop kernel: [    0.238772] NET: Registered protocol family 2
Jun  8 16:49:13 brian-desktop kernel: [    0.238821] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.238978] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.239217] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.239334] TCP: Hash tables configured (established 131072 bind 65536)
Jun  8 16:49:13 brian-desktop kernel: [    0.239336] TCP reno registered
Jun  8 16:49:13 brian-desktop kernel: [    0.239339] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.239344] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.239393] NET: Registered protocol family 1
Jun  8 16:49:13 brian-desktop kernel: [    0.239519] pci 0000:01:00.0: Boot video device
Jun  8 16:49:13 brian-desktop kernel: [    0.239526] PCI: CLS 32 bytes, default 64
Jun  8 16:49:13 brian-desktop kernel: [    0.239554] Trying to unpack rootfs image as initramfs...
Jun  8 16:49:13 brian-desktop kernel: [    0.406026] Freeing initrd memory: 8272k freed
Jun  8 16:49:13 brian-desktop kernel: [    0.408462] cpufreq-nforce2: No nForce2 chipset.
Jun  8 16:49:13 brian-desktop kernel: [    0.408484] Scanning for low memory corruption every 60 seconds
Jun  8 16:49:13 brian-desktop kernel: [    0.408598] audit: initializing netlink socket (disabled)
Jun  8 16:49:13 brian-desktop kernel: [    0.408609] type=2000 audit(1276030139.407:1): initialized
Jun  8 16:49:13 brian-desktop kernel: [    0.415461] highmem bounce pool size: 64 pages
Jun  8 16:49:13 brian-desktop kernel: [    0.415466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun  8 16:49:13 brian-desktop kernel: [    0.416580] VFS: Disk quotas dquot_6.5.2
Jun  8 16:49:13 brian-desktop kernel: [    0.416621] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun  8 16:49:13 brian-desktop kernel: [    0.417052] fuse init (API version 7.13)
Jun  8 16:49:13 brian-desktop kernel: [    0.417119] msgmni has been set to 1665
Jun  8 16:49:13 brian-desktop kernel: [    0.417277] alg: No test for stdrng (krng)
Jun  8 16:49:13 brian-desktop kernel: [    0.417319] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun  8 16:49:13 brian-desktop kernel: [    0.417321] io scheduler noop registered
Jun  8 16:49:13 brian-desktop kernel: [    0.417323] io scheduler deadline registered
Jun  8 16:49:13 brian-desktop kernel: [    0.417352] io scheduler cfq registered (default)
Jun  8 16:49:13 brian-desktop kernel: [    0.417438] pcieport 0000:00:01.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.417458]   alloc irq_desc for 24 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417460]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417467] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
Jun  8 16:49:13 brian-desktop kernel: [    0.417509] pcieport 0000:00:1c.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.417533]   alloc irq_desc for 25 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417535]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417540] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
Jun  8 16:49:13 brian-desktop kernel: [    0.417599] pcieport 0000:00:1c.3: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.417623]   alloc irq_desc for 26 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417625]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417630] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
Jun  8 16:49:13 brian-desktop kernel: [    0.417692] pcieport 0000:00:1c.4: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.417716]   alloc irq_desc for 27 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417718]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.417723] pcieport 0000:00:1c.4: irq 27 for MSI/MSI-X
Jun  8 16:49:13 brian-desktop kernel: [    0.417794] pcieport 0000:00:01.0: Requesting control of PCIe PME from ACPI BIOS
Jun  8 16:49:13 brian-desktop kernel: [    0.417803] pcieport 0000:00:01.0: Failed to receive control of PCIe PME service: no _OSC support
Jun  8 16:49:13 brian-desktop kernel: [    0.417806] pcie_pme: probe of 0000:00:01.0:pcie01 failed with error -13
Jun  8 16:49:13 brian-desktop kernel: [    0.417810] pcieport 0000:00:1c.0: Requesting control of PCIe PME from ACPI BIOS
Jun  8 16:49:13 brian-desktop kernel: [    0.417812] pcieport 0000:00:1c.0: Failed to receive control of PCIe PME service: no _OSC support
Jun  8 16:49:13 brian-desktop kernel: [    0.417814] pcie_pme: probe of 0000:00:1c.0:pcie01 failed with error -13
Jun  8 16:49:13 brian-desktop kernel: [    0.417818] pcieport 0000:00:1c.3: Requesting control of PCIe PME from ACPI BIOS
Jun  8 16:49:13 brian-desktop kernel: [    0.417820] pcieport 0000:00:1c.3: Failed to receive control of PCIe PME service: no _OSC support
Jun  8 16:49:13 brian-desktop kernel: [    0.417822] pcie_pme: probe of 0000:00:1c.3:pcie01 failed with error -13
Jun  8 16:49:13 brian-desktop kernel: [    0.417825] pcieport 0000:00:1c.4: Requesting control of PCIe PME from ACPI BIOS
Jun  8 16:49:13 brian-desktop kernel: [    0.417828] pcieport 0000:00:1c.4: Failed to receive control of PCIe PME service: no _OSC support
Jun  8 16:49:13 brian-desktop kernel: [    0.417830] pcie_pme: probe of 0000:00:1c.4:pcie01 failed with error -13
Jun  8 16:49:13 brian-desktop kernel: [    0.417845] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  8 16:49:13 brian-desktop kernel: [    0.417911] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  8 16:49:13 brian-desktop kernel: [    0.418018] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun  8 16:49:13 brian-desktop kernel: [    0.418021] ACPI: Power Button [PWRB]
Jun  8 16:49:13 brian-desktop kernel: [    0.418068] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun  8 16:49:13 brian-desktop kernel: [    0.418070] ACPI: Power Button [PWRF]
Jun  8 16:49:13 brian-desktop kernel: [    0.420154] isapnp: Scanning for PnP cards...
Jun  8 16:49:13 brian-desktop kernel: [    0.772921] isapnp: No Plug & Play device found
Jun  8 16:49:13 brian-desktop kernel: [    0.773977] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun  8 16:49:13 brian-desktop kernel: [    0.774064] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  8 16:49:13 brian-desktop kernel: [    0.774347] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  8 16:49:13 brian-desktop kernel: [    0.775278] brd: module loaded
Jun  8 16:49:13 brian-desktop kernel: [    0.775670] loop: module loaded
Jun  8 16:49:13 brian-desktop kernel: [    0.775762] ata_piix 0000:00:1f.2: version 2.13
Jun  8 16:49:13 brian-desktop kernel: [    0.775775] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  8 16:49:13 brian-desktop kernel: [    0.775779] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Jun  8 16:49:13 brian-desktop kernel: [    0.775811] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.775854] scsi0 : ata_piix
Jun  8 16:49:13 brian-desktop kernel: [    0.775905] scsi1 : ata_piix
Jun  8 16:49:13 brian-desktop kernel: [    0.776406] ata1: SATA max UDMA/133 cmd 0xd600 ctl 0xd700 bmdma 0xda00 irq 19
Jun  8 16:49:13 brian-desktop kernel: [    0.776410] ata2: SATA max UDMA/133 cmd 0xd800 ctl 0xd900 bmdma 0xda08 irq 19
Jun  8 16:49:13 brian-desktop kernel: [    0.776428] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  8 16:49:13 brian-desktop kernel: [    0.776432] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jun  8 16:49:13 brian-desktop kernel: [    0.776465] ata_piix 0000:00:1f.5: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.776491] scsi2 : ata_piix
Jun  8 16:49:13 brian-desktop kernel: [    0.776527] scsi3 : ata_piix
Jun  8 16:49:13 brian-desktop kernel: [    0.777012] ata3: SATA max UDMA/133 cmd 0xdd00 ctl 0xde00 bmdma 0xe100 irq 19
Jun  8 16:49:13 brian-desktop kernel: [    0.777015] ata4: SATA max UDMA/133 cmd 0xdf00 ctl 0xe000 bmdma 0xe108 irq 19
Jun  8 16:49:13 brian-desktop kernel: [    0.777069] pata_acpi 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  8 16:49:13 brian-desktop kernel: [    0.777091] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.777101] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun  8 16:49:13 brian-desktop kernel: [    0.777320] Fixed MDIO Bus: probed
Jun  8 16:49:13 brian-desktop kernel: [    0.777349] PPP generic driver version 2.4.2
Jun  8 16:49:13 brian-desktop kernel: [    0.777378] tun: Universal TUN/TAP device driver, 1.6
Jun  8 16:49:13 brian-desktop kernel: [    0.777379] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun  8 16:49:13 brian-desktop kernel: [    0.777434] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  8 16:49:13 brian-desktop kernel: [    0.777447]   alloc irq_desc for 18 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.777448]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.777452] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun  8 16:49:13 brian-desktop kernel: [    0.777460] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.777463] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.777491] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jun  8 16:49:13 brian-desktop kernel: [    0.781381] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Jun  8 16:49:13 brian-desktop kernel: [    0.781391] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb004000
Jun  8 16:49:13 brian-desktop kernel: [    0.795922] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jun  8 16:49:13 brian-desktop kernel: [    0.796028] hub 1-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.796032] hub 1-0:1.0: 6 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.796086]   alloc irq_desc for 23 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.796087]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.796091] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  8 16:49:13 brian-desktop kernel: [    0.796098] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.796101] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.796123] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jun  8 16:49:13 brian-desktop kernel: [    0.800027] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jun  8 16:49:13 brian-desktop kernel: [    0.800037] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb005000
Jun  8 16:49:13 brian-desktop kernel: [    0.815922] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun  8 16:49:13 brian-desktop kernel: [    0.816012] hub 2-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.816016] hub 2-0:1.0: 6 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.816068] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  8 16:49:13 brian-desktop kernel: [    0.816080] uhci_hcd: USB Universal Host Controller Interface driver
Jun  8 16:49:13 brian-desktop kernel: [    0.816093] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 16:49:13 brian-desktop kernel: [    0.816097] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.816100] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.816124] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jun  8 16:49:13 brian-desktop kernel: [    0.816149] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d100
Jun  8 16:49:13 brian-desktop kernel: [    0.816232] hub 3-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.816235] hub 3-0:1.0: 2 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.816282]   alloc irq_desc for 21 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.816283]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    0.816287] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun  8 16:49:13 brian-desktop kernel: [    0.816291] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.816294] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.816318] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun  8 16:49:13 brian-desktop kernel: [    0.816343] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d200
Jun  8 16:49:13 brian-desktop kernel: [    0.816432] hub 4-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.816436] hub 4-0:1.0: 2 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.816478] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun  8 16:49:13 brian-desktop kernel: [    0.816482] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.816484] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.816512] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jun  8 16:49:13 brian-desktop kernel: [    0.816530] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d000
Jun  8 16:49:13 brian-desktop kernel: [    0.816620] hub 5-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.816623] hub 5-0:1.0: 2 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.816665] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  8 16:49:13 brian-desktop kernel: [    0.816669] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.816672] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.816694] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jun  8 16:49:13 brian-desktop kernel: [    0.816714] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d300
Jun  8 16:49:13 brian-desktop kernel: [    0.816798] hub 6-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.816801] hub 6-0:1.0: 2 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.816846] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  8 16:49:13 brian-desktop kernel: [    0.816850] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.816852] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.816875] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jun  8 16:49:13 brian-desktop kernel: [    0.816893] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d400
Jun  8 16:49:13 brian-desktop kernel: [    0.816980] hub 7-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.816983] hub 7-0:1.0: 2 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.817027] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun  8 16:49:13 brian-desktop kernel: [    0.817032] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    0.817034] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun  8 16:49:13 brian-desktop kernel: [    0.817057] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jun  8 16:49:13 brian-desktop kernel: [    0.817076] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d500
Jun  8 16:49:13 brian-desktop kernel: [    0.817159] hub 8-0:1.0: USB hub found
Jun  8 16:49:13 brian-desktop kernel: [    0.817162] hub 8-0:1.0: 2 ports detected
Jun  8 16:49:13 brian-desktop kernel: [    0.817249] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun  8 16:49:13 brian-desktop kernel: [    0.817626] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  8 16:49:13 brian-desktop kernel: [    0.817633] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  8 16:49:13 brian-desktop kernel: [    0.817733] mice: PS/2 mouse device common for all mice
Jun  8 16:49:13 brian-desktop kernel: [    0.817824] rtc_cmos 00:04: RTC can wake from S4
Jun  8 16:49:13 brian-desktop kernel: [    0.817849] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jun  8 16:49:13 brian-desktop kernel: [    0.817870] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jun  8 16:49:13 brian-desktop kernel: [    0.817944] device-mapper: uevent: version 1.0.3
Jun  8 16:49:13 brian-desktop kernel: [    0.818010] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Jun  8 16:49:13 brian-desktop kernel: [    0.818055] device-mapper: multipath: version 1.1.1 loaded
Jun  8 16:49:13 brian-desktop kernel: [    0.818057] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun  8 16:49:13 brian-desktop kernel: [    0.818139] EISA: Probing bus 0 at eisa.0
Jun  8 16:49:13 brian-desktop kernel: [    0.818141] EISA: Cannot allocate resource for mainboard
Jun  8 16:49:13 brian-desktop kernel: [    0.818143] Cannot allocate resource for EISA slot 1
Jun  8 16:49:13 brian-desktop kernel: [    0.818145] Cannot allocate resource for EISA slot 2
Jun  8 16:49:13 brian-desktop kernel: [    0.818147] Cannot allocate resource for EISA slot 3
Jun  8 16:49:13 brian-desktop kernel: [    0.818149] Cannot allocate resource for EISA slot 4
Jun  8 16:49:13 brian-desktop kernel: [    0.818151] Cannot allocate resource for EISA slot 5
Jun  8 16:49:13 brian-desktop kernel: [    0.818153] Cannot allocate resource for EISA slot 6
Jun  8 16:49:13 brian-desktop kernel: [    0.818155] Cannot allocate resource for EISA slot 7
Jun  8 16:49:13 brian-desktop kernel: [    0.818156] Cannot allocate resource for EISA slot 8
Jun  8 16:49:13 brian-desktop kernel: [    0.818158] EISA: Detected 0 cards.
Jun  8 16:49:13 brian-desktop kernel: [    0.818211] cpuidle: using governor ladder
Jun  8 16:49:13 brian-desktop kernel: [    0.818213] cpuidle: using governor menu
Jun  8 16:49:13 brian-desktop kernel: [    0.818477] TCP cubic registered
Jun  8 16:49:13 brian-desktop kernel: [    0.818596] NET: Registered protocol family 10
Jun  8 16:49:13 brian-desktop kernel: [    0.818884] lo: Disabled Privacy Extensions
Jun  8 16:49:13 brian-desktop kernel: [    0.819074] NET: Registered protocol family 17
Jun  8 16:49:13 brian-desktop kernel: [    0.819104] Using IPI No-Shortcut mode
Jun  8 16:49:13 brian-desktop kernel: [    0.819154] PM: Resume from disk failed.
Jun  8 16:49:13 brian-desktop kernel: [    0.819162] registered taskstats version 1
Jun  8 16:49:13 brian-desktop kernel: [    0.819387]   Magic number: 14:509:851
Jun  8 16:49:13 brian-desktop kernel: [    0.819425] rtc_cmos 00:04: setting system clock to 2010-06-08 20:49:00 UTC (1276030140)
Jun  8 16:49:13 brian-desktop kernel: [    0.819427] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  8 16:49:13 brian-desktop kernel: [    0.819428] EDD information not available.
Jun  8 16:49:13 brian-desktop kernel: [    0.835958] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Jun  8 16:49:13 brian-desktop kernel: [    1.106658] ata2: SATA link down (SStatus 0 SControl 300)
Jun  8 16:49:13 brian-desktop kernel: [    1.117169] ata4: SATA link down (SStatus 0 SControl 300)
Jun  8 16:49:13 brian-desktop kernel: [    1.228010] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jun  8 16:49:13 brian-desktop kernel: [    1.252041] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  8 16:49:13 brian-desktop kernel: [    1.252139] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  8 16:49:13 brian-desktop kernel: [    1.260275] ata3.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
Jun  8 16:49:13 brian-desktop kernel: [    1.260278] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  8 16:49:13 brian-desktop kernel: [    1.268144] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
Jun  8 16:49:13 brian-desktop kernel: [    1.276319] ata3.00: configured for UDMA/133
Jun  8 16:49:13 brian-desktop kernel: [    1.300164] ata1.00: configured for UDMA/100
Jun  8 16:49:13 brian-desktop kernel: [    1.302037] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
Jun  8 16:49:13 brian-desktop kernel: [    1.307471] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun  8 16:49:13 brian-desktop kernel: [    1.307474] Uniform CD-ROM driver Revision: 3.20
Jun  8 16:49:13 brian-desktop kernel: [    1.307560] sr 0:0:0:0: Attached scsi CD-ROM sr0
Jun  8 16:49:13 brian-desktop kernel: [    1.307602] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jun  8 16:49:13 brian-desktop kernel: [    1.307697] scsi 2:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
Jun  8 16:49:13 brian-desktop kernel: [    1.307775] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jun  8 16:49:13 brian-desktop kernel: [    1.307822] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jun  8 16:49:13 brian-desktop kernel: [    1.307866] sd 2:0:0:0: [sda] Write Protect is off
Jun  8 16:49:13 brian-desktop kernel: [    1.307868] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  8 16:49:13 brian-desktop kernel: [    1.307887] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  8 16:49:13 brian-desktop kernel: [    1.307989]  sda: sda1 sda2 < sda5 >
Jun  8 16:49:13 brian-desktop kernel: [    1.356648] sd 2:0:0:0: [sda] Attached SCSI disk
Jun  8 16:49:13 brian-desktop kernel: [    1.356661] Freeing unused kernel memory: 712k freed
Jun  8 16:49:13 brian-desktop kernel: [    1.356906] Write protecting the kernel text: 4752k
Jun  8 16:49:13 brian-desktop kernel: [    1.356937] Write protecting the kernel read-only data: 1932k
Jun  8 16:49:13 brian-desktop kernel: [    1.367923] udev: starting version 151
Jun  8 16:49:13 brian-desktop kernel: [    1.403319] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  8 16:49:13 brian-desktop kernel: [    1.403352] pata_jmicron 0000:03:00.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    1.423709] scsi4 : pata_jmicron
Jun  8 16:49:13 brian-desktop kernel: [    1.431854] scsi5 : pata_jmicron
Jun  8 16:49:13 brian-desktop kernel: [    1.432571] ata5: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 19
Jun  8 16:49:13 brian-desktop kernel: [    1.432573] ata6: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 19
Jun  8 16:49:13 brian-desktop kernel: [    1.432926] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun  8 16:49:13 brian-desktop kernel: [    1.432941] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 16:49:13 brian-desktop kernel: [    1.432978] r8169 0000:04:00.0: setting latency timer to 64
Jun  8 16:49:13 brian-desktop kernel: [    1.433030]   alloc irq_desc for 28 on node -1
Jun  8 16:49:13 brian-desktop kernel: [    1.433032]   alloc kstat_irqs on node -1
Jun  8 16:49:13 brian-desktop kernel: [    1.433045] r8169 0000:04:00.0: irq 28 for MSI/MSI-X
Jun  8 16:49:13 brian-desktop kernel: [    1.433488] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xf805e000, 00:1d:7d:0c:39:3b, XID 18000000 IRQ 28
Jun  8 16:49:13 brian-desktop kernel: [    1.641495] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jun  8 16:49:13 brian-desktop kernel: [    1.641498] EXT4-fs (sda1): write access will be enabled during recovery
Jun  8 16:49:13 brian-desktop kernel: [    1.852511] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jun  8 16:49:13 brian-desktop kernel: [    2.031943] usbcore: registered new interface driver hiddev
Jun  8 16:49:13 brian-desktop kernel: [    2.031966] usbcore: registered new interface driver usbhid
Jun  8 16:49:13 brian-desktop kernel: [    2.031967] usbhid: USB HID core driver
Jun  8 16:49:13 brian-desktop kernel: [    2.264510] usb 5-1: new full speed USB device using uhci_hcd and address 2
Jun  8 16:49:13 brian-desktop kernel: [    8.919653] EXT4-fs (sda1): recovery complete
Jun  8 16:49:13 brian-desktop kernel: [    8.919904] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun  8 16:49:13 brian-desktop kernel: [   11.108402] Adding 9936892k swap on /dev/sda5.  Priority:-1 extents:1 across:9936892k 
Jun  8 16:49:13 brian-desktop kernel: [   11.451265] udev: starting version 151
Jun  8 16:49:13 brian-desktop kernel: [   12.491876] cfg80211: Calling CRDA to update world regulatory domain
Jun  8 16:49:13 brian-desktop kernel: [   12.567531] Linux agpgart interface v0.103
Jun  8 16:49:13 brian-desktop kernel: [   12.668305] parport_pc 00:08: reported by Plug and Play ACPI
Jun  8 16:49:13 brian-desktop kernel: [   12.668346] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun  8 16:49:13 brian-desktop kernel: [   12.837677] lp0: using parport0 (interrupt-driven).
Jun  8 16:49:13 brian-desktop kernel: [   13.226661] cfg80211: World regulatory domain updated:
Jun  8 16:49:13 brian-desktop kernel: [   13.226663]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  8 16:49:13 brian-desktop kernel: [   13.226666]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  8 16:49:13 brian-desktop kernel: [   13.226668]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  8 16:49:13 brian-desktop kernel: [   13.226670]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  8 16:49:13 brian-desktop kernel: [   13.226672]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  8 16:49:13 brian-desktop kernel: [   13.226674]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  8 16:49:13 brian-desktop kernel: [   13.716718] nvidia: module license 'NVIDIA' taints kernel.
Jun  8 16:49:13 brian-desktop kernel: [   13.716722] Disabling lock debugging due to kernel taint
Jun  8 16:49:14 brian-desktop kernel: [   14.326582] ppdev: user-space parallel port driver
Jun  8 16:49:14 brian-desktop kernel: [   14.331490] Linux video capture interface: v2.00
Jun  8 16:49:14 brian-desktop kernel: [   14.331726] input: Wacom Intuos3 4x5 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
Jun  8 16:49:14 brian-desktop kernel: [   14.335368] usbcore: registered new interface driver wacom
Jun  8 16:49:14 brian-desktop kernel: [   14.335370] wacom: v1.52:USB Wacom tablet driver
Jun  8 16:49:14 brian-desktop kernel: [   14.572945] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  8 16:49:14 brian-desktop kernel: [   14.572951] nvidia 0000:01:00.0: setting latency timer to 64
Jun  8 16:49:14 brian-desktop kernel: [   14.572954] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun  8 16:49:14 brian-desktop kernel: [   14.573068] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
Jun  8 16:49:14 brian-desktop udev-configure-printer: add /module/lp
Jun  8 16:49:14 brian-desktop udev-configure-printer: add /devices/pnp0/00:08/printer/lp0
Jun  8 16:49:14 brian-desktop udev-configure-printer: Failed to get parent
Jun  8 16:49:14 brian-desktop udev-configure-printer: Failed to get parent
Jun  8 16:49:14 brian-desktop kernel: [   14.810486] gspca: main v2.9.0 registered
Jun  8 16:49:14 brian-desktop kernel: [   14.815503] gspca: probing 046d:08d7
Jun  8 16:49:14 brian-desktop kernel: [   15.000320] psmouse serio1: ID: 10 00 64
Jun  8 16:49:15 brian-desktop kernel: [   15.370768] phy0: Selected rate control algorithm 'minstrel'
Jun  8 16:49:15 brian-desktop kernel: [   15.371249] Registered led device: rt73usb-phy0::radio
Jun  8 16:49:15 brian-desktop kernel: [   15.371265] Registered led device: rt73usb-phy0::assoc
Jun  8 16:49:15 brian-desktop kernel: [   15.371279] Registered led device: rt73usb-phy0::quality
Jun  8 16:49:15 brian-desktop kernel: [   15.371744] usbcore: registered new interface driver rt73usb
Jun  8 16:49:15 brian-desktop kernel: [   15.609807] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
Jun  8 16:49:15 brian-desktop kernel: [   15.660449]   alloc irq_desc for 22 on node -1
Jun  8 16:49:15 brian-desktop kernel: [   15.660452]   alloc kstat_irqs on node -1
Jun  8 16:49:15 brian-desktop kernel: [   15.660457] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun  8 16:49:15 brian-desktop kernel: [   15.660488]   alloc irq_desc for 29 on node -1
Jun  8 16:49:15 brian-desktop kernel: [   15.660490]   alloc kstat_irqs on node -1
Jun  8 16:49:15 brian-desktop kernel: [   15.660497] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X
Jun  8 16:49:15 brian-desktop kernel: [   15.660517] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  8 16:49:15 brian-desktop kernel: [   15.868445] zc3xx: probe 2wr ov vga 0x0000
Jun  8 16:49:15 brian-desktop kernel: [   15.870226] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Jun  8 16:49:15 brian-desktop kernel: [   15.904448] zc3xx: probe sensor -> 0011
Jun  8 16:49:15 brian-desktop kernel: [   15.904451] zc3xx: Find Sensor HV7131R(c)
Jun  8 16:49:15 brian-desktop kernel: [   15.906508] input: zc3xx as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/input/input6
Jun  8 16:49:15 brian-desktop kernel: [   15.906574] gspca: video0 created
Jun  8 16:49:15 brian-desktop kernel: [   15.906577] gspca: found int in endpoint: 0x82, buffer_len=8, interval=10
Jun  8 16:49:15 brian-desktop kernel: [   15.927713] usbcore: registered new interface driver zc3xx
Jun  8 16:49:15 brian-desktop kernel: [   15.927714] usbcore: registered new interface driver snd-usb-audio
Jun  8 16:49:15 brian-desktop kernel: [   15.927717] zc3xx: registered
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Successfully dropped root privileges.
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: avahi-daemon 0.6.25 starting up.
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Successfully called chroot().
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Successfully dropped remaining capabilities.
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: No service file found in /etc/avahi/services.
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Network interface enumeration completed.
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Registering HINFO record with values 'I686'/'LINUX'.
Jun  8 16:49:15 brian-desktop avahi-daemon[811]: Server startup complete. Host name is brian-desktop.local. Local service cookie is 3335552370.
Jun  8 16:49:16 brian-desktop NetworkManager: <info>  starting...
Jun  8 16:49:16 brian-desktop NetworkManager: <info>  Trying to start the modem-manager...
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Gobi
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Ericsson MBM
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Generic
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Longcheer
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Nokia
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Sierra
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Option
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Huawei
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin MotoC
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Novatel
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin Option High-Speed
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin AnyData
Jun  8 16:49:16 brian-desktop modem-manager: Loaded plugin ZTE
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan0, iface: wlan0)
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth0, iface: eth0)
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  8 16:49:16 brian-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun  8 16:49:16 brian-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  8 16:49:17 brian-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun  8 16:49:17 brian-desktop NetworkManager:    SCPlugin-Ifupdown: (144376560) ... get_connections.
Jun  8 16:49:17 brian-desktop NetworkManager:    SCPlugin-Ifupdown: (144376560) ... get_connections (managed=false): return empty list.
Jun  8 16:49:17 brian-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt73usb')
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): now managed
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): bringing up device.
Jun  8 16:49:17 brian-desktop kernel: [   17.708197] rt73usb 1-4:1.0: firmware: requesting rt73.bin
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): preparing device.
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun  8 16:49:17 brian-desktop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): now managed
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): bringing up device.
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): preparing device.
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun  8 16:49:17 brian-desktop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth0
Jun  8 16:49:17 brian-desktop kernel: [   17.942243] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  8 16:49:17 brian-desktop kernel: [   17.943259] r8169 0000:04:00.0: eth0: link down
Jun  8 16:49:17 brian-desktop kernel: [   17.943392] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  modem-manager is now available
Jun  8 16:49:17 brian-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  8 16:49:17 brian-desktop NetworkManager: <info>  Trying to start the supplicant...
Jun  8 16:49:18 brian-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jun  8 16:49:18 brian-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jun  8 16:49:18 brian-desktop gdm-binary[828]: WARNING: Unable to find users: no seat-id found
Jun  8 16:49:18 brian-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun  8 16:49:18 brian-desktop wpa_supplicant[866]: Failed to initiate AP scan.
Jun  8 16:49:18 brian-desktop wpa_supplicant[866]: Failed to initiate AP scan.
Jun  8 16:49:18 brian-desktop cron[962]: (CRON) INFO (pidfile fd = 3)
Jun  8 16:49:18 brian-desktop acpid: starting up with proc fs
Jun  8 16:49:18 brian-desktop anacron[976]: Anacron 2.3 started on 2010-06-08
Jun  8 16:49:18 brian-desktop init: apport pre-start process (957) terminated with status 1
Jun  8 16:49:18 brian-desktop init: apport post-stop process (979) terminated with status 1
Jun  8 16:49:19 brian-desktop cron[982]: (CRON) STARTUP (fork ok)
Jun  8 16:49:19 brian-desktop cron[982]: (CRON) INFO (Running @reboot jobs)
Jun  8 16:49:19 brian-desktop anacron[976]: Normal exit (0 jobs run)
Jun  8 16:49:19 brian-desktop acpid: 36 rules loaded
Jun  8 16:49:19 brian-desktop acpid: waiting for events: event logging is off
Jun  8 16:49:20 brian-desktop wpa_supplicant[866]: WPS-AP-AVAILABLE 
Jun  8 16:49:20 brian-desktop acpid: client connected from 969[0:0]
Jun  8 16:49:20 brian-desktop acpid: 1 client rule loaded
Jun  8 16:49:22 brian-desktop anacron[1100]: Anacron 2.3 started on 2010-06-08
Jun  8 16:49:22 brian-desktop anacron[1100]: Normal exit (0 jobs run)
Jun  8 16:49:23 brian-desktop acpid: client connected from 969[0:0]
Jun  8 16:49:23 brian-desktop acpid: 1 client rule loaded
Jun  8 16:49:23 brian-desktop gdm-session-worker[1132]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  8 16:49:27 brian-desktop rtkit-daemon[1216]: Sucessfully called chroot.
Jun  8 16:49:27 brian-desktop rtkit-daemon[1216]: Sucessfully dropped privileges.
Jun  8 16:49:27 brian-desktop rtkit-daemon[1216]: Sucessfully limited resources.
Jun  8 16:49:27 brian-desktop rtkit-daemon[1216]: Running.
Jun  8 16:49:27 brian-desktop rtkit-daemon[1216]: Watchdog thread running.
Jun  8 16:49:27 brian-desktop rtkit-daemon[1216]: Canary thread running.
Jun  8 16:49:27 brian-desktop polkitd[1220]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun  8 16:49:28 brian-desktop rtkit-daemon[1216]: Sucessfully made thread 1214 of process 1214 (n/a) owned by '1000' high priority at nice level -11.
Jun  8 16:49:28 brian-desktop rtkit-daemon[1216]: Supervising 1 threads of 1 processes of 1 users.
Jun  8 16:49:30 brian-desktop anacron[1265]: Anacron 2.3 started on 2010-06-08
Jun  8 16:49:30 brian-desktop anacron[1265]: Normal exit (0 jobs run)
Jun  8 16:49:30 brian-desktop rtkit-daemon[1216]: Sucessfully made thread 1277 of process 1214 (n/a) owned by '1000' RT at priority 5.
Jun  8 16:49:30 brian-desktop rtkit-daemon[1216]: Supervising 2 threads of 1 processes of 1 users.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 1908PineApt3'
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 1908PineApt3' has security, but secrets are required.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 1908PineApt3' has security, and secrets exist.  No new secrets needed.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Config: added 'ssid' value '1908PineApt3'
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  8 16:49:31 brian-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  8 16:49:31 brian-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  8 16:49:31 brian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jun  8 16:49:31 brian-desktop rtkit-daemon[1216]: Sucessfully made thread 1280 of process 1214 (n/a) owned by '1000' RT at priority 5.
Jun  8 16:49:31 brian-desktop rtkit-daemon[1216]: Supervising 3 threads of 1 processes of 1 users.
Jun  8 16:49:31 brian-desktop rtkit-daemon[1216]: Sucessfully made thread 1281 of process 1214 (n/a) owned by '1000' RT at priority 5.
Jun  8 16:49:31 brian-desktop rtkit-daemon[1216]: Supervising 4 threads of 1 processes of 1 users.
Jun  8 16:49:32 brian-desktop wpa_supplicant[866]: WPS-AP-AVAILABLE 
Jun  8 16:49:32 brian-desktop wpa_supplicant[866]: Trying to associate with 00:23:69:2e:b1:83 (SSID='1908PineApt3' freq=2437 MHz)
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  8 16:49:32 brian-desktop kernel: [   32.866485] wlan0: deauthenticating from 00:23:69:2e:b1:83 by local choice (reason=3)
Jun  8 16:49:32 brian-desktop kernel: [   32.871959] wlan0: authenticate with 00:23:69:2e:b1:83 (try 1)
Jun  8 16:49:32 brian-desktop kernel: [   32.873091] wlan0: authenticated
Jun  8 16:49:32 brian-desktop kernel: [   32.874584] wlan0: associate with 00:23:69:2e:b1:83 (try 1)
Jun  8 16:49:32 brian-desktop kernel: [   32.877214] wlan0: RX AssocResp from 00:23:69:2e:b1:83 (capab=0x411 status=0 aid=2)
Jun  8 16:49:32 brian-desktop kernel: [   32.877217] wlan0: associated
Jun  8 16:49:32 brian-desktop wpa_supplicant[866]: Associated with 00:23:69:2e:b1:83
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun  8 16:49:32 brian-desktop kernel: [   32.881716] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun  8 16:49:32 brian-desktop wpa_supplicant[866]: WPA: Key negotiation completed with 00:23:69:2e:b1:83 [PTK=TKIP GTK=TKIP]
Jun  8 16:49:32 brian-desktop wpa_supplicant[866]: CTRL-EVENT-CONNECTED - Connection to 00:23:69:2e:b1:83 completed (auth) [id=0 id_str=]
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '1908PineApt3'.
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun  8 16:49:32 brian-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun  8 16:49:33 brian-desktop NetworkManager: <info>  dhclient started with pid 1304
Jun  8 16:49:33 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun  8 16:49:33 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  8 16:49:33 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun  8 16:49:33 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun  8 16:49:34 brian-desktop avahi-daemon[811]: Registering new address record for fe80::21e:8cff:fed6:3795 on wlan0.*.
Jun  8 16:49:34 brian-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun  8 16:49:34 brian-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun  8 16:49:34 brian-desktop dhclient: All rights reserved.
Jun  8 16:49:34 brian-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  8 16:49:34 brian-desktop dhclient: 
Jun  8 16:49:34 brian-desktop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Jun  8 16:49:34 brian-desktop dhclient: Listening on LPF/wlan0/00:1e:8c:d6:37:95
Jun  8 16:49:34 brian-desktop dhclient: Sending on   LPF/wlan0/00:1e:8c:d6:37:95
Jun  8 16:49:34 brian-desktop dhclient: Sending on   Socket/fallback
Jun  8 16:49:34 brian-desktop acpid: client connected from 1324[108:114]
Jun  8 16:49:34 brian-desktop acpid: 1 client rule loaded
Jun  8 16:49:34 brian-desktop rtkit-daemon[1216]: Sucessfully made thread 1325 of process 1325 (n/a) owned by '1000' high priority at nice level -11.
Jun  8 16:49:34 brian-desktop rtkit-daemon[1216]: Supervising 5 threads of 2 processes of 1 users.
Jun  8 16:49:34 brian-desktop pulseaudio[1325]: pid.c: Daemon already running.
Jun  8 16:49:37 brian-desktop dhclient: DHCPREQUEST of 192.168.1.134 on wlan0 to 255.255.255.255 port 67
Jun  8 16:49:37 brian-desktop dhclient: DHCPACK of 192.168.1.134 from 192.168.1.1
Jun  8 16:49:37 brian-desktop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jun  8 16:49:37 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  8 16:49:37 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  8 16:49:37 brian-desktop NetworkManager: <info>    address 192.168.1.134
Jun  8 16:49:37 brian-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Jun  8 16:49:37 brian-desktop NetworkManager: <info>    gateway 192.168.1.1
Jun  8 16:49:37 brian-desktop NetworkManager: <info>    hostname 'brian-desktop'
Jun  8 16:49:37 brian-desktop NetworkManager: <info>    nameserver '192.168.1.1'
Jun  8 16:49:37 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  8 16:49:37 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun  8 16:49:37 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jun  8 16:49:37 brian-desktop avahi-daemon[811]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.134.
Jun  8 16:49:37 brian-desktop avahi-daemon[811]: New relevant interface wlan0.IPv4 for mDNS.
Jun  8 16:49:37 brian-desktop avahi-daemon[811]: Registering new address record for 192.168.1.134 on wlan0.IPv4.
Jun  8 16:49:37 brian-desktop dhclient: bound to 192.168.1.134 -- renewal in 40159 seconds.
Jun  8 16:49:38 brian-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jun  8 16:49:38 brian-desktop NetworkManager: <info>  Policy set 'Auto 1908PineApt3' (wlan0) as default for routing and DNS.
Jun  8 16:49:38 brian-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jun  8 16:49:38 brian-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jun  8 16:49:43 brian-desktop kernel: [   43.396505] wlan0: no IPv6 routers present
Jun  8 16:49:45 brian-desktop ntpdate[1416]: adjust time server 91.189.94.4 offset -0.029875 sec
Jun  8 16:50:32 brian-desktop AptDaemon: INFO: Initializing daemon
Jun  8 16:55:33 brian-desktop AptDaemon: INFO: Quiting due to inactivity
Jun  8 16:55:33 brian-desktop AptDaemon: INFO: Shutdown was requested
```

---

### Post by trpnblies7 on 2010-06-08
Anything?

---

### Post by trpnblies7 on 2010-06-10
Any ideas?

---

