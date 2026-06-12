---
title: "Quite long boot on new machine"
date: 2010-07-12
forum: General Help
---

### Post by teo_rossi on 2010-07-12
Hi all,
considering the claims on the ultra-fast-boot in new Ubuntu versions, I think my 1-2 minutes boot on a brand-new laptop (SONY Vaio CW2C5E) is quite slowish.

I noticed that before the Ubuntu splash screen comes up, the screens stays black for 30 seconds with a blinking cursor. I also found a 20-second gap in dmesg which I can't explain:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-7-generic (buildd@crested) (gcc version 4.4.4 (Ubuntu 4.4.4-6ubuntu2) ) #12-Ubuntu SMP Fri Jul 9 21:54:03 UTC 2010 (Ubuntu 2.6.35-7.12-generic 2.6.35-rc4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-7-generic root=UUID=fe1a051b-27ef-43bd-88c8-fbfd8f3d4e7f ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cee7a000 (usable)
[    0.000000]  BIOS-e820: 00000000cee7a000 - 00000000ceeba000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ceeba000 - 00000000ceecb000 (reserved)
[    0.000000]  BIOS-e820: 00000000ceecb000 - 00000000ceee1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ceee1000 - 00000000cef10000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef10000 - 00000000cef11000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cef11000 - 00000000cef14000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef14000 - 00000000cef16000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cef16000 - 00000000cef1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef1a000 - 00000000cef1d000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cef1d000 - 00000000cef21000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef21000 - 00000000cef30000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cef30000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012c000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x12c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 120000000 mask FF0000000 write-back
[    0.000000]   5 base 12C000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcee7a max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cee7a000 (usable)
[    0.000000]  modified: 00000000cee7a000 - 00000000ceeba000 (ACPI NVS)
[    0.000000]  modified: 00000000ceeba000 - 00000000ceecb000 (reserved)
[    0.000000]  modified: 00000000ceecb000 - 00000000ceee1000 (ACPI NVS)
[    0.000000]  modified: 00000000ceee1000 - 00000000cef10000 (reserved)
[    0.000000]  modified: 00000000cef10000 - 00000000cef11000 (ACPI NVS)
[    0.000000]  modified: 00000000cef11000 - 00000000cef14000 (reserved)
[    0.000000]  modified: 00000000cef14000 - 00000000cef16000 (ACPI NVS)
[    0.000000]  modified: 00000000cef16000 - 00000000cef1a000 (reserved)
[    0.000000]  modified: 00000000cef1a000 - 00000000cef1d000 (ACPI data)
[    0.000000]  modified: 00000000cef1d000 - 00000000cef21000 (reserved)
[    0.000000]  modified: 00000000cef21000 - 00000000cef30000 (ACPI NVS)
[    0.000000]  modified: 00000000cef30000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 000000012c000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000fc980] fc980
[    0.000000] init_memory_mapping: 0000000000000000-00000000cee7a000
[    0.000000]  0000000000 - 00cee00000 page 2M
[    0.000000]  00cee00000 - 00cee7a000 page 4k
[    0.000000] kernel direct mapping tables up to cee7a000 @ 16000-1c000
[    0.000000] init_memory_mapping: 0000000100000000-000000012c000000
[    0.000000]  0100000000 - 012c000000 page 2M
[    0.000000] kernel direct mapping tables up to 12c000000 @ 1a000-20000
[    0.000000] RAMDISK: 37599000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000cef1be18 0005C (v01   Sony     VAIO 20100514 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000cef14d98 000F4 (v04   Sony     VAIO 20100514 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20100428/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCEF2CF40/0x00000000CEF2FD40, using 32 (20100428/tbfadt-486)
[    0.000000] ACPI: DSDT 00000000ceecb018 0A3D8 (v01   Sony     VAIO 20100514 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cef2cf40 00040
[    0.000000] ACPI: APIC 00000000cef1af18 0008C (v02   Sony     VAIO 20100514 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000cef2ed18 0003C (v01   Sony     VAIO 20100514 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cef2ec98 00038 (v01   Sony     VAIO 20100514 MSFT 00000003)
[    0.000000] ACPI: SLIC 00000000cef27a18 00176 (v01   Sony     VAIO 20100514 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000cef15018 009F1 (v01   Sony     VAIO 20100514 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cef14c18 0011D (v01   Sony     VAIO 20100514 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000012c000000
[    0.000000] Initmem setup node 0 0000000000000000-000000012c000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0012c000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cee7a
[    0.000000]     0: 0x00100000 -> 0x0012c000
[    0.000000] On node 0 totalpages: 1027592
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 829106 pages, LIFO batch:31
[    0.000000]   Normal zone: 2464 pages used for memmap
[    0.000000]   Normal zone: 177760 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1b000 - 1b7ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cee7a000 - 00000000ceeba000
[    0.000000] PM: Registered nosave memory: 00000000ceeba000 - 00000000ceecb000
[    0.000000] PM: Registered nosave memory: 00000000ceecb000 - 00000000ceee1000
[    0.000000] PM: Registered nosave memory: 00000000ceee1000 - 00000000cef10000
[    0.000000] PM: Registered nosave memory: 00000000cef10000 - 00000000cef11000
[    0.000000] PM: Registered nosave memory: 00000000cef11000 - 00000000cef14000
[    0.000000] PM: Registered nosave memory: 00000000cef14000 - 00000000cef16000
[    0.000000] PM: Registered nosave memory: 00000000cef16000 - 00000000cef1a000
[    0.000000] PM: Registered nosave memory: 00000000cef1a000 - 00000000cef1d000
[    0.000000] PM: Registered nosave memory: 00000000cef1d000 - 00000000cef21000
[    0.000000] PM: Registered nosave memory: 00000000cef21000 - 00000000cef30000
[    0.000000] PM: Registered nosave memory: 00000000cef30000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [1b800 - 1c7ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91456 r8192 d23232 u262144
[    0.000000] pcpu-alloc: s91456 r8192 d23232 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1010792
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-7-generic root=UUID=fe1a051b-27ef-43bd-88c8-fbfd8f3d4e7f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (75 early reservations)
[    0.000000]   #1 [0001000000 - 0001d20b14]   TEXT DATA BSS
[    0.000000]   #2 [0037599000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d21000 - 0001d21210]             BRK
[    0.000000]   #4 [00000fc990 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000fc980 - 00000fc990]    MP-table mpf
[    0.000000]   #6 [000009e800 - 00000fc6f0]   BIOS reserved
[    0.000000]   #7 [00000fc910 - 00000fc980]   BIOS reserved
[    0.000000]   #8 [00000fc6f0 - 00000fc910]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #12 [000001a000 - 000001b000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d21240 - 0001d22240]         BOOTMEM
[    0.000000]   #15 [0001d20b40 - 0001d20e40]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103c00000]        MEMMAP 0
[    0.000000]   #19 [0001d20e40 - 0001d20fc0]         BOOTMEM
[    0.000000]   #20 [0001d22240 - 0001d3a240]         BOOTMEM
[    0.000000]   #21 [0001d3a240 - 0001d40240]         BOOTMEM
[    0.000000]   #22 [0001d41000 - 0001d42000]         BOOTMEM
[    0.000000]   #23 [0001d40240 - 0001d40281]         BOOTMEM
[    0.000000]   #24 [0001d402c0 - 0001d40303]         BOOTMEM
[    0.000000]   #25 [0001d40340 - 0001d408f0]         BOOTMEM
[    0.000000]   #26 [0001d40900 - 0001d40968]         BOOTMEM
[    0.000000]   #27 [0001d40980 - 0001d409e8]         BOOTMEM
[    0.000000]   #28 [0001d40a00 - 0001d40a68]         BOOTMEM
[    0.000000]   #29 [0001d40a80 - 0001d40ae8]         BOOTMEM
[    0.000000]   #30 [0001d40b00 - 0001d40b68]         BOOTMEM
[    0.000000]   #31 [0001d40b80 - 0001d40be8]         BOOTMEM
[    0.000000]   #32 [0001d40c00 - 0001d40c68]         BOOTMEM
[    0.000000]   #33 [0001d40c80 - 0001d40ce8]         BOOTMEM
[    0.000000]   #34 [0001d40d00 - 0001d40d68]         BOOTMEM
[    0.000000]   #35 [0001d40d80 - 0001d40de8]         BOOTMEM
[    0.000000]   #36 [0001d40e00 - 0001d40e68]         BOOTMEM
[    0.000000]   #37 [0001d40e80 - 0001d40ee8]         BOOTMEM
[    0.000000]   #38 [0001d40f00 - 0001d40f68]         BOOTMEM
[    0.000000]   #39 [0001d40f80 - 0001d40fe8]         BOOTMEM
[    0.000000]   #40 [0001d42000 - 0001d42068]         BOOTMEM
[    0.000000]   #41 [0001d42080 - 0001d420e8]         BOOTMEM
[    0.000000]   #42 [0001d42100 - 0001d42168]         BOOTMEM
[    0.000000]   #43 [0001d42180 - 0001d421e8]         BOOTMEM
[    0.000000]   #44 [0001d42200 - 0001d42268]         BOOTMEM
[    0.000000]   #45 [0001d42280 - 0001d422e8]         BOOTMEM
[    0.000000]   #46 [0001d42300 - 0001d42368]         BOOTMEM
[    0.000000]   #47 [0001d42380 - 0001d423e8]         BOOTMEM
[    0.000000]   #48 [0001d42400 - 0001d42468]         BOOTMEM
[    0.000000]   #49 [0001d42480 - 0001d424e8]         BOOTMEM
[    0.000000]   #50 [0001d42500 - 0001d42568]         BOOTMEM
[    0.000000]   #51 [0001d20fc0 - 0001d20fe0]         BOOTMEM
[    0.000000]   #52 [0001d42580 - 0001d425a0]         BOOTMEM
[    0.000000]   #53 [0001d425c0 - 0001d42629]         BOOTMEM
[    0.000000]   #54 [0001d42640 - 0001d426a9]         BOOTMEM
[    0.000000]   #55 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #56 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #57 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #58 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #59 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #60 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #61 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #62 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #63 [0001d446c0 - 0001d446c8]         BOOTMEM
[    0.000000]   #64 [0001d44700 - 0001d44708]         BOOTMEM
[    0.000000]   #65 [0001d44740 - 0001d44760]         BOOTMEM
[    0.000000]   #66 [0001d44780 - 0001d447c0]         BOOTMEM
[    0.000000]   #67 [0001d447c0 - 0001d448e0]         BOOTMEM
[    0.000000]   #68 [0001d44900 - 0001d44948]         BOOTMEM
[    0.000000]   #69 [0001d44980 - 0001d449c8]         BOOTMEM
[    0.000000]   #70 [0001d44a00 - 0001d4ca00]         BOOTMEM
[    0.000000]   #71 [0001fde000 - 0005fde000]         BOOTMEM
[    0.000000]   #72 [0001d4ca00 - 0001d6ca00]         BOOTMEM
[    0.000000]   #73 [0001d6ca00 - 0001daca00]         BOOTMEM
[    0.000000]   #74 [000001c800 - 0000024800]         BOOTMEM
[    0.000000] Memory: 3959784k/4915200k available (5707k kernel code, 804832k absent, 150584k reserved, 5421k data, 904k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2393.674 MHz processor.
[    0.000008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.34 BogoMIPS (lpj=23936740)
[    0.000015] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000047] AppArmor: AppArmor initialized
[    0.000048] Yama: becoming mindful.
[    0.000376] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001293] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001685] Mount-cache hash table entries: 256
[    0.001783] Initializing cgroup subsys ns
[    0.001786] Initializing cgroup subsys cpuacct
[    0.001789] Initializing cgroup subsys memory
[    0.001795] Initializing cgroup subsys devices
[    0.001797] Initializing cgroup subsys freezer
[    0.001798] Initializing cgroup subsys net_cls
[    0.001817] CPU: Physical Processor ID: 0
[    0.001818] CPU: Processor Core ID: 0
[    0.001823] mce: CPU supports 9 MCE banks
[    0.001831] CPU0: Thermal monitoring handled by SMI
[    0.001838] using mwait in idle threads.
[    0.001840] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.001845] ... version:                3
[    0.001846] ... bit width:              48
[    0.001847] ... generic registers:      4
[    0.001849] ... value mask:             0000ffffffffffff
[    0.001850] ... max period:             000000007fffffff
[    0.001851] ... fixed-purpose events:   3
[    0.001852] ... event mask:             000000070000000f
[    0.003633] ACPI: Core revision 20100428
[    0.025026] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.025030] ftrace: allocating 22646 entries in 89 pages
[    0.031123] Setting APIC routing to flat
[    0.031439] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.131260] CPU0: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz stepping 02
[    0.242868] Booting Node   0, Processors  #1
[    0.402508] CPU1: Thermal monitoring handled by SMI
[    0.422605]  #2
[    0.582198] CPU2: Thermal monitoring handled by SMI
[    0.602359]  #3
[    0.761884] CPU3: Thermal monitoring handled by SMI
[    0.781922] Brought up 4 CPUs
[    0.781925] Total of 4 processors activated (19151.28 BogoMIPS).
[    0.783527] devtmpfs: initialized
[    0.784359] regulator: core version 0.5
[    0.784387] Time: 13:30:16  Date: 07/12/10
[    0.784415] NET: Registered protocol family 16
[    0.784497] Trying to unpack rootfs image as initramfs...
[    0.784505] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.784507] ACPI: bus type pci registered
[    0.784569] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.784572] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.793822] PCI: Using configuration type 1 for base access
[    0.794419] bio: create slab <bio-0> at 0
[    0.796066] ACPI: EC: Look up EC in DSDT
[    0.797544] ACPI: Executed 1 blocks of module-level executable AML code
[    0.802089] ACPI: BIOS _OSI(Linux) query ignored
[    0.806929] ACPI: SSDT 00000000cef19918 003E2 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.807347] ACPI: Dynamic OEM Table Load:
[    0.807350] ACPI: SSDT (null) 003E2 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.807639] ACPI: SSDT 00000000cef17618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.808042] ACPI: Dynamic OEM Table Load:
[    0.808044] ACPI: SSDT (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.808561] ACPI: SSDT 00000000cef18a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.809038] ACPI: Dynamic OEM Table Load:
[    0.809040] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.809208] ACPI: SSDT 00000000cef16d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.809651] ACPI: Dynamic OEM Table Load:
[    0.809654] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.980387] Freeing initrd memory: 10588k freed
[    1.211403] ACPI: Interpreter enabled
[    1.211408] ACPI: (supports S0 S3 S4 S5)
[    1.211433] ACPI: Using IOAPIC for interrupt routing
[    1.232578] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.232851] ACPI: No dock devices found.
[    1.232854] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.233584] \_SB_.PCI0:_OSC invalid UUID
[    1.233586] _OSC request data:1 8 1f 
[    1.233589] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.234637] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.234639] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.234642] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.234644] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.234646] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.234647] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.234649] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.234651] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    1.234653] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    1.234655] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xfeafffff]
[    1.234712] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.234715] pci 0000:00:01.0: PME# disabled
[    1.234786] pci 0000:00:1a.0: reg 10: [mem 0xe8e08000-0xe8e083ff]
[    1.234848] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.234853] pci 0000:00:1a.0: PME# disabled
[    1.234896] pci 0000:00:1b.0: reg 10: [mem 0xe8e00000-0xe8e03fff 64bit]
[    1.234952] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.234956] pci 0000:00:1b.0: PME# disabled
[    1.235046] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.235050] pci 0000:00:1c.0: PME# disabled
[    1.235141] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.235145] pci 0000:00:1c.1: PME# disabled
[    1.235235] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.235239] pci 0000:00:1c.2: PME# disabled
[    1.235332] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.235336] pci 0000:00:1c.5: PME# disabled
[    1.235391] pci 0000:00:1d.0: reg 10: [mem 0xe8e07000-0xe8e073ff]
[    1.235454] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.235458] pci 0000:00:1d.0: PME# disabled
[    1.235651] pci 0000:00:1f.2: reg 10: [io  0xe070-0xe077]
[    1.235658] pci 0000:00:1f.2: reg 14: [io  0xe060-0xe063]
[    1.235665] pci 0000:00:1f.2: reg 18: [io  0xe050-0xe057]
[    1.235672] pci 0000:00:1f.2: reg 1c: [io  0xe040-0xe043]
[    1.235679] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    1.235686] pci 0000:00:1f.2: reg 24: [mem 0xe8e06000-0xe8e067ff]
[    1.235728] pci 0000:00:1f.2: PME# supported from D3hot
[    1.235732] pci 0000:00:1f.2: PME# disabled
[    1.235768] pci 0000:00:1f.3: reg 10: [mem 0xe8e05000-0xe8e050ff 64bit]
[    1.235785] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    1.235844] pci 0000:00:1f.6: reg 10: [mem 0xe8e04000-0xe8e04fff 64bit]
[    1.235947] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    1.235957] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.235967] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit pref]
[    1.235973] pci 0000:01:00.0: reg 24: [io  0xd000-0xd07f]
[    1.235979] pci 0000:01:00.0: reg 30: [mem 0xe3000000-0xe307ffff pref]
[    1.236040] pci 0000:01:00.1: reg 10: [mem 0xe3080000-0xe3083fff]
[    1.236105] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.236107] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    1.236110] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    1.236113] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.236201] pci 0000:02:00.0: reg 10: [mem 0xe7a00000-0xe7a0ffff 64bit]
[    1.236263] pci 0000:02:00.0: supports D1
[    1.236264] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    1.236269] pci 0000:02:00.0: PME# disabled
[    1.236295] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.236299] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    1.236304] pci 0000:00:1c.0:   bridge window [mem 0xe7a00000-0xe8dfffff]
[    1.236311] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.236433] pci 0000:03:00.0: reg 10: [mem 0xe6603000-0xe66030ff]
[    1.236530] pci 0000:03:00.0: supports D1 D2
[    1.236532] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.236538] pci 0000:03:00.0: PME# disabled
[    1.236601] pci 0000:03:00.1: reg 10: [mem 0xe6602000-0xe66020ff]
[    1.236698] pci 0000:03:00.1: supports D1 D2
[    1.236699] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.236705] pci 0000:03:00.1: PME# disabled
[    1.236765] pci 0000:03:00.3: reg 10: [mem 0xe6601000-0xe66017ff]
[    1.236862] pci 0000:03:00.3: supports D1 D2
[    1.236864] pci 0000:03:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.236870] pci 0000:03:00.3: PME# disabled
[    1.236928] pci 0000:03:00.4: reg 10: [mem 0xe6600000-0xe66000ff]
[    1.237025] pci 0000:03:00.4: supports D1 D2
[    1.237026] pci 0000:03:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    1.237032] pci 0000:03:00.4: PME# disabled
[    1.237066] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.237070] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    1.237075] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe79fffff]
[    1.237082] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.237338] pci 0000:04:00.0: reg 10: [mem 0xe5220000-0xe5223fff 64bit]
[    1.237389] pci 0000:04:00.0: reg 18: [io  0xa000-0xa0ff]
[    1.237532] pci 0000:04:00.0: reg 30: [mem 0xe5200000-0xe521ffff pref]
[    1.237725] pci 0000:04:00.0: supports D1 D2
[    1.237726] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.237749] pci 0000:04:00.0: PME# disabled
[    1.237856] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.237860] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    1.237865] pci 0000:00:1c.2:   bridge window [mem 0xe5200000-0xe65fffff]
[    1.237872] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.237927] pci 0000:00:1c.5: PCI bridge to [bus 05-0c]
[    1.237931] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    1.237936] pci 0000:00:1c.5:   bridge window [mem 0xe3200000-0xe51fffff]
[    1.237943] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.238015] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d] (subtractive decode)
[    1.238020] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.238025] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.238032] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.238034] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.238036] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.238038] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.238040] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.238042] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.238044] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.238045] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.238047] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    1.238049] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    1.238051] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    1.238086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.238321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.238448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.238587] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.238745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.238869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    1.239223] \_SB_.PCI0:_OSC invalid UUID
[    1.239225] _OSC request data:1 19 1f 
[    1.247120] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    1.247538] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.247651] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    1.247761] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    1.247871] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.247981] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.248091] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.248201] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.248311] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.248362] HEST: Table is not found!
[    1.248433] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.248439] vgaarb: loaded
[    1.248549] SCSI subsystem initialized
[    1.248639] libata version 3.00 loaded.
[    1.248687] usbcore: registered new interface driver usbfs
[    1.248694] usbcore: registered new interface driver hub
[    1.248714] usbcore: registered new device driver usb
[    1.248839] ACPI: WMI: Mapper loaded
[    1.248840] PCI: Using ACPI for IRQ routing
[    1.248843] PCI: pci_cache_line_size set to 64 bytes
[    1.249047] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    1.249049] reserve RAM buffer: 00000000cee7a000 - 00000000cfffffff 
[    1.249123] NetLabel: Initializing
[    1.249124] NetLabel:  domain hash size = 128
[    1.249125] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.249136] NetLabel:  unlabeled traffic allowed by default
[    1.249171] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.249176] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.251195] Switching to clocksource tsc
[    1.257509] AppArmor: AppArmor Filesystem Enabled
[    1.257524] pnp: PnP ACPI init
[    1.257542] ACPI: bus type pnp registered
[    1.262194] pnp: PnP ACPI: found 11 devices
[    1.262196] ACPI: ACPI bus type pnp unregistered
[    1.262208] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.262211] system 00:05: [io  0xff00-0xff0f] has been reserved
[    1.262213] system 00:05: [io  0xff10-0xff13] has been reserved
[    1.262215] system 00:05: [io  0x0800-0x0803] has been reserved
[    1.262217] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.262219] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.262221] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.262226] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.262228] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.262231] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.262234] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.262237] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.262239] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.262241] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.262243] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    1.262245] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.262247] system 00:09: [mem 0xf7fff000-0xf7ffffff] has been reserved
[    1.266962] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe8f00000-0xe90fffff 64bit pref]
[    1.266966] pci 0000:00:1c.1: BAR 15: assigned [mem 0xe9100000-0xe92fffff 64bit pref]
[    1.266969] pci 0000:00:1c.2: BAR 15: assigned [mem 0xe9300000-0xe94fffff 64bit pref]
[    1.266971] pci 0000:00:1c.5: BAR 15: assigned [mem 0xe9500000-0xe96fffff 64bit pref]
[    1.266974] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.266976] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    1.266979] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    1.266981] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    1.266984] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.266987] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    1.266993] pci 0000:00:1c.0:   bridge window [mem 0xe7a00000-0xe8dfffff]
[    1.266998] pci 0000:00:1c.0:   bridge window [mem 0xe8f00000-0xe90fffff 64bit pref]
[    1.267006] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.267009] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    1.267014] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe79fffff]
[    1.267019] pci 0000:00:1c.1:   bridge window [mem 0xe9100000-0xe92fffff 64bit pref]
[    1.267026] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.267029] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    1.267034] pci 0000:00:1c.2:   bridge window [mem 0xe5200000-0xe65fffff]
[    1.267038] pci 0000:00:1c.2:   bridge window [mem 0xe9300000-0xe94fffff 64bit pref]
[    1.267046] pci 0000:00:1c.5: PCI bridge to [bus 05-0c]
[    1.267049] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    1.267055] pci 0000:00:1c.5:   bridge window [mem 0xe3200000-0xe51fffff]
[    1.267059] pci 0000:00:1c.5:   bridge window [mem 0xe9500000-0xe96fffff 64bit pref]
[    1.267067] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d]
[    1.267068] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.267073] pci 0000:00:1e.0:   bridge window [mem disabled]
[    1.267078] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.267092]   alloc irq_desc for 16 on node -1
[    1.267093]   alloc kstat_irqs on node -1
[    1.267098] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.267102] pci 0000:00:01.0: setting latency timer to 64
[    1.267110] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.267115] pci 0000:00:1c.0: setting latency timer to 64
[    1.267124]   alloc irq_desc for 17 on node -1
[    1.267125]   alloc kstat_irqs on node -1
[    1.267128] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.267133] pci 0000:00:1c.1: setting latency timer to 64
[    1.267142]   alloc irq_desc for 18 on node -1
[    1.267143]   alloc kstat_irqs on node -1
[    1.267146] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.267151] pci 0000:00:1c.2: setting latency timer to 64
[    1.267159] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.267164] pci 0000:00:1c.5: setting latency timer to 64
[    1.267172] pci 0000:00:1e.0: setting latency timer to 64
[    1.267176] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.267178] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.267180] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.267181] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.267183] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.267185] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.267186] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.267188] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.267190] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.267191] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    1.267193] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    1.267195] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xe30fffff]
[    1.267197] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    1.267198] pci_bus 0000:02: resource 1 [mem 0xe7a00000-0xe8dfffff]
[    1.267200] pci_bus 0000:02: resource 2 [mem 0xe8f00000-0xe90fffff 64bit pref]
[    1.267202] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    1.267204] pci_bus 0000:03: resource 1 [mem 0xe6600000-0xe79fffff]
[    1.267205] pci_bus 0000:03: resource 2 [mem 0xe9100000-0xe92fffff 64bit pref]
[    1.267207] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    1.267209] pci_bus 0000:04: resource 1 [mem 0xe5200000-0xe65fffff]
[    1.267211] pci_bus 0000:04: resource 2 [mem 0xe9300000-0xe94fffff 64bit pref]
[    1.267212] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    1.267214] pci_bus 0000:05: resource 1 [mem 0xe3200000-0xe51fffff]
[    1.267216] pci_bus 0000:05: resource 2 [mem 0xe9500000-0xe96fffff 64bit pref]
[    1.267218] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
[    1.267219] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
[    1.267221] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
[    1.267223] pci_bus 0000:0d: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.267224] pci_bus 0000:0d: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.267226] pci_bus 0000:0d: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.267227] pci_bus 0000:0d: resource 10 [mem 0x000dc000-0x000dffff]
[    1.267229] pci_bus 0000:0d: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.267231] pci_bus 0000:0d: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.267233] pci_bus 0000:0d: resource 13 [mem 0xd0000000-0xfeafffff]
[    1.267261] NET: Registered protocol family 2
[    1.267386] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.268269] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.270620] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.270902] TCP: Hash tables configured (established 524288 bind 65536)
[    1.270904] TCP reno registered
[    1.270913] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.270944] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.271059] NET: Registered protocol family 1
[    1.611853] pci 0000:01:00.0: Boot video device
[    1.611957] PCI: CLS 64 bytes, default 64
[    1.611959] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.611962] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    1.611964] software IO TLB at phys 0x1fde000 - 0x5fde000
[    1.612206] Scanning for low memory corruption every 60 seconds
[    1.612295] audit: initializing netlink socket (disabled)
[    1.612303] type=2000 audit(1278941416.480:1): initialized
[    1.624209] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.625262] VFS: Disk quotas dquot_6.5.2
[    1.625305] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.625723] fuse init (API version 7.14)
[    1.625786] msgmni has been set to 7754
[    1.625966] alg: No test for stdrng (krng)
[    1.626013] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.626015] io scheduler noop registered
[    1.626017] io scheduler deadline registered
[    1.626044] io scheduler cfq registered (default)
[    1.626125] pcieport 0000:00:01.0: setting latency timer to 64
[    1.626144]   alloc irq_desc for 40 on node -1
[    1.626145]   alloc kstat_irqs on node -1
[    1.626154] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.626196] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.626236]   alloc irq_desc for 41 on node -1
[    1.626237]   alloc kstat_irqs on node -1
[    1.626245] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.626321] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.626361]   alloc irq_desc for 42 on node -1
[    1.626362]   alloc kstat_irqs on node -1
[    1.626370] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.626443] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.626483]   alloc irq_desc for 43 on node -1
[    1.626485]   alloc kstat_irqs on node -1
[    1.626492] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    1.626566] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.626606]   alloc irq_desc for 44 on node -1
[    1.626607]   alloc kstat_irqs on node -1
[    1.626615] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    1.626697] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.626841] \_SB_.PCI0:_OSC invalid UUID
[    1.626842] _OSC request data:1 0 1f 
[    1.626937] \_SB_.PCI0:_OSC invalid UUID
[    1.626939] _OSC request data:1 0 1f 
[    1.627031] \_SB_.PCI0:_OSC invalid UUID
[    1.627032] _OSC request data:1 0 1f 
[    1.627123] \_SB_.PCI0:_OSC invalid UUID
[    1.627124] _OSC request data:1 0 1f 
[    1.627227] \_SB_.PCI0:_OSC invalid UUID
[    1.627228] _OSC request data:1 0 1f 
[    1.627319] \_SB_.PCI0:_OSC invalid UUID
[    1.627320] _OSC request data:1 0 1f 
[    1.627410] \_SB_.PCI0:_OSC invalid UUID
[    1.627411] _OSC request data:1 0 1f 
[    1.627502] \_SB_.PCI0:_OSC invalid UUID
[    1.627503] _OSC request data:1 0 1f 
[    1.627519] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.628280] ACPI: AC Adapter [ADP1] (off-line)
[    1.628347] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.629335] ACPI: Lid Switch [LID0]
[    1.629368] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.629375] ACPI: Power Button [PWRB]
[    1.630065] ACPI: acpi_idle registered with cpuidle
[    1.630279] Monitor-Mwait will be used to enter C-1 state
[    1.630296] Monitor-Mwait will be used to enter C-2 state
[    1.630314] Monitor-Mwait will be used to enter C-3 state
[    1.644346] thermal LNXTHERM:01: registered as thermal_zone0
[    1.644352] ACPI: Thermal Zone [TZ00] (47 C)
[    1.646357] thermal LNXTHERM:02: registered as thermal_zone1
[    1.646364] ACPI: Thermal Zone [TZ01] (47 C)
[    1.646444] ERST: Table is not found!
[    1.647402] Linux agpgart interface v0.103
[    1.647469] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.648331] brd: module loaded
[    1.648650] loop: module loaded
[    1.648951] Fixed MDIO Bus: probed
[    1.648976] PPP generic driver version 2.4.2
[    1.648998] tun: Universal TUN/TAP device driver, 1.6
[    1.649000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.649047] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.649067] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.649083] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.649087] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.649108] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.649140] ehci_hcd 0000:00:1a.0: debug port 2
[    1.653030] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.653050] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe8e08000
[    1.672359] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.672466] hub 1-0:1.0: USB hub found
[    1.672470] hub 1-0:1.0: 2 ports detected
[    1.672518]   alloc irq_desc for 23 on node -1
[    1.672519]   alloc kstat_irqs on node -1
[    1.672524] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.672536] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.672539] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.672595] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.672628] ehci_hcd 0000:00:1d.0: debug port 2
[    1.676518] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.676539] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xe8e07000
[    1.686608] ACPI: Battery Slot [BAT0] (battery present)
[    1.702257] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.702373] hub 2-0:1.0: USB hub found
[    1.702375] hub 2-0:1.0: 2 ports detected
[    1.702417] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.702425] uhci_hcd: USB Universal Host Controller Interface driver
[    1.702497] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.707679] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.711543] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.711549] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.711552] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.711554] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.711557] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.711608] mice: PS/2 mouse device common for all mice
[    1.711679] rtc_cmos 00:06: RTC can wake from S4
[    1.711707] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.711737] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.711803] device-mapper: uevent: version 1.0.3
[    1.711859] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.711925] device-mapper: multipath: version 1.1.1 loaded
[    1.711928] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.712152] cpuidle: using governor ladder
[    1.712264] cpuidle: using governor menu
[    1.712463] TCP cubic registered
[    1.712552] NET: Registered protocol family 10
[    1.712832] lo: Disabled Privacy Extensions
[    1.712980] NET: Registered protocol family 17
[    1.715545] PM: Resume from disk failed.
[    1.715554] registered taskstats version 1
[    1.716024]   Magic number: 2:762:533
[    1.716030] bdi 1:11: hash matches
[    1.716192] rtc_cmos 00:06: setting system clock to 2010-07-12 13:30:17 UTC (1278941417)
[    1.716197] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.716200] EDD information not available.
[    1.716283] Freeing unused kernel memory: 904k freed
[    1.716433] Write protecting the kernel read-only data: 10240k
[    1.716686] Freeing unused kernel memory: 416k freed
[    1.716949] Freeing unused kernel memory: 1604k freed
[    1.735249] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.736247] udev: starting version 151
[    1.759009] sky2: driver version 1.28
[    1.759088] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.759138] sky2 0000:04:00.0: setting latency timer to 64
[    1.759244] sky2 0000:04:00.0: Yukon-2 UL 2 chip revision 0
[    1.759646]   alloc irq_desc for 45 on node -1
[    1.759649]   alloc kstat_irqs on node -1
[    1.759699] sky2 0000:04:00.0: irq 45 for MSI/MSI-X
[    1.763799] sky2 0000:04:00.0: eth0: addr 00:24:be:b5:c3:de
[    1.766888] sdhci: Secure Digital Host Controller Interface driver
[    1.766892] sdhci: Copyright(c) Pierre Ossman
[    1.768611] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
[    1.768640] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.769755] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.769797] sdhci-pci 0000:03:00.0: setting latency timer to 64
[    1.788878] ahci 0000:00:1f.2: version 3.0
[    1.788901]   alloc irq_desc for 19 on node -1
[    1.788903]   alloc kstat_irqs on node -1
[    1.788912] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.788980]   alloc irq_desc for 46 on node -1
[    1.788982]   alloc kstat_irqs on node -1
[    1.788994] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.789075] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3 impl SATA mode
[    1.789079] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part apst 
[    1.789085] ahci 0000:00:1f.2: setting latency timer to 64
[    1.798098] Registered led device: mmc0::
[    1.798170] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    1.798236] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
[    1.798264] sdhci-pci 0000:03:00.4: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.798338] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.798347] sdhci-pci 0000:03:00.4: setting latency timer to 64
[    1.799468] Registered led device: mmc1::
[    1.800614] mmc1: SDHCI controller on PCI [0000:03:00.4] using DMA
[    1.800860] firewire_ohci 0000:03:00.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.800899] firewire_ohci 0000:03:00.3: setting latency timer to 64
[    1.807019] scsi0 : ahci
[    1.810930] scsi1 : ahci
[    1.814127] scsi2 : ahci
[    1.816235] scsi3 : ahci
[    1.818259] scsi4 : ahci
[    1.818687] scsi5 : ahci
[    1.818888] ata1: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06100 irq 46
[    1.818892] ata2: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06180 irq 46
[    1.818894] ata3: DUMMY
[    1.818895] ata4: DUMMY
[    1.818896] ata5: DUMMY
[    1.818897] ata6: DUMMY
[    1.969947] firewire_ohci: Added fw-ohci device 0000:03:00.3, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
[    1.990541] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.151745] hub 1-1:1.0: USB hub found
[    2.151891] hub 1-1:1.0: 6 ports detected
[    2.161536] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.161582] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.162556] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.163013] ata1.00: ATA-8: Hitachi HTS545032B9SA00, PB3OC64G, max UDMA/133
[    2.163017] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.164185] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.164635] ata1.00: configured for UDMA/133
[    2.165680] ata2.00: ATAPI: HL-DT-ST DVDRAM GT20N, CL08, max UDMA/133
[    2.170534] ata2.00: configured for UDMA/133
[    2.179749] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54503 PB3O PQ: 0 ANSI: 5
[    2.179885] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.179966] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.180025] sd 0:0:0:0: [sda] Write Protect is off
[    2.180027] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.180049] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.180161]  sda:
[    2.193367] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20N     CL08 PQ: 0 ANSI: 5
[    2.201184]  sda1 sda2 sda3 sda4 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.204689] Uniform CD-ROM driver Revision: 3.20
[    2.204832] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.204880] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.226992]  sda5 sda6 >
[    2.247937] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.269345] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.421059] hub 2-1:1.0: USB hub found
[    2.421143] hub 2-1:1.0: 8 ports detected
[    2.440358] firewire_core: created device fw0: GUID 08004603032ba43e, S400
[    2.500509] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
[    2.699423] usb 2-1.5: new low speed USB device using ehci_hcd and address 3
[    2.827215] usbcore: registered new interface driver hiddev
[    2.831404] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3
[    2.831474] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-1.5/input0
[    2.831486] usbcore: registered new interface driver usbhid
[    2.831487] usbhid: USB HID core driver
[    2.856742] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   21.369658] udev: starting version 151
[   21.377041] Adding 1309260k swap on /dev/sda6.  Priority:-1 extents:1 across:1309260k 
[   21.388273] lp: driver loaded but no devices found
[   21.446824] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS
[   21.447327] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:4b/LNXVIDEO:01/input/input4
[   21.447412] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   21.450075] vga16fb: initializing
[   21.450080] vga16fb: mapped to 0xffff8800000a0000
[   21.496277] sony-laptop: Sony Notebook Control Driver v0.6.
[   21.541093] cfg80211: Calling CRDA to update world regulatory domain
[   21.542502] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input5
[   21.542593] input: Sony Vaio Jogdial as /devices/virtual/input/input6
[   21.586150] cfg80211: World regulatory domain updated:
[   21.586153]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.586156]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.586159]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.586162]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.586164]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.586167]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.620250] Linux video capture interface: v2.00
[   21.628349] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.628367] ath9k 0000:02:00.0: setting latency timer to 64
[   21.635647] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:18b5)
[   21.637343] input: UVC Camera (05ca:18b5) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7
[   21.637440] usbcore: registered new interface driver uvcvideo
[   21.637442] USB Video Class driver (v0.1.0)
[   21.681228] ath: EEPROM regdomain: 0x65
[   21.681230] ath: EEPROM indicates we should expect a direct regpair map
[   21.681233] ath: Country alpha2 being used: 00
[   21.681235] ath: Regpair used: 0x65
[   21.687537]   alloc irq_desc for 22 on node -1
[   21.687539]   alloc kstat_irqs on node -1
[   21.687548] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.687664]   alloc irq_desc for 47 on node -1
[   21.687666]   alloc kstat_irqs on node -1
[   21.687687] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   21.687749] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.690626] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   21.691127] Registered led device: ath9k-phy0::radio
[   21.691142] Registered led device: ath9k-phy0::assoc
[   21.691157] Registered led device: ath9k-phy0::tx
[   21.691174] Registered led device: ath9k-phy0::rx
[   21.691180] phy0: Atheros AR9285 Rev:2 mem=0xffffc90005180000, irq=16
[   21.769784] Console: switching to colour frame buffer device 80x30
[   21.776101] fb0: VGA16 VGA frame buffer device
[   21.808681] nvidia: module license 'NVIDIA' taints kernel.
[   21.808684] Disabling lock debugging due to kernel taint
[   21.809924] hda_codec: ALC262: SKU not ready 0x411111f0
[   21.809988] hda_codec: ALC262: BIOS auto-probing.
[   21.815847] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.815851] hda_intel: Disable MSI for Nvidia chipset
[   21.815915] HDA Intel 0000:01:00.1: setting latency timer to 64
[   21.830124] type=1400 audit(1278934237.635:2):  operation="profile_load" pid=906 name="/sbin/dhclient3" pid=906 comm="apparmor_parser"
[   21.830576] type=1400 audit(1278934237.635:3):  operation="profile_load" pid=906 name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=906 comm="apparmor_parser"
[   21.830836] type=1400 audit(1278934237.635:4):  operation="profile_load" pid=906 name="/usr/lib/connman/scripts/dhclient-script" pid=906 comm="apparmor_parser"
[   22.084604] usb 1-1.6: new full speed USB device using ehci_hcd and address 4
[   22.215633] Bluetooth: Core ver 2.15
[   22.215686] NET: Registered protocol family 31
[   22.215688] Bluetooth: HCI device and connection manager initialized
[   22.215690] Bluetooth: HCI socket layer initialized
[   22.218561] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   22.218960] usbcore: registered new interface driver btusb
[   22.355849] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
[   22.404450] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   22.567017] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   23.388085] type=1400 audit(1278934239.195:5):  operation="profile_load" pid=1154 name="/usr/share/gdm/guest-session/Xsession" pid=1154 comm="apparmor_parser"
[   23.389210] type=1400 audit(1278934239.195:6):  operation="profile_replace" pid=1155 name="/sbin/dhclient3" pid=1155 comm="apparmor_parser"
[   23.389614] type=1400 audit(1278934239.195:7):  operation="profile_replace" pid=1155 name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1155 comm="apparmor_parser"
[   23.389831] type=1400 audit(1278934239.195:8):  operation="profile_replace" pid=1155 name="/usr/lib/connman/scripts/dhclient-script" pid=1155 comm="apparmor_parser"
[   23.391728] type=1400 audit(1278934239.205:9):  operation="profile_load" pid=1156 name="/usr/bin/evince" pid=1156 comm="apparmor_parser"
[   23.396676] type=1400 audit(1278934239.205:10):  operation="profile_load" pid=1156 name="/usr/bin/evince-previewer" pid=1156 comm="apparmor_parser"
[   23.399845] type=1400 audit(1278934239.205:11):  operation="profile_load" pid=1156 name="/usr/bin/evince-thumbnailer" pid=1156 comm="apparmor_parser"
[   23.473242] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.517214] sky2 0000:04:00.0: eth0: enabling interface
[   23.517584] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.706118] Bluetooth: L2CAP ver 2.14
[   23.706122] Bluetooth: L2CAP socket layer initialized
[   23.712962] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.712966] Bluetooth: BNEP filters: protocol multicast
```

I'm running maverik Alpha 2, but with lucid the result was the same (or even worse). Is there any problem with my config?

---

### Post by J@n on 2010-08-13
Hi,

Same here. I have two Ubuntu machines both setup using Ext4. I get exactly the same message in the logs as you have. My delay typically is 10 to 13 seconds.

I have had no such issues with earlier versions of Ubuntu setup with Ext3. Is there any solution to this?

Greetz,

J@n

---

### Post by mastablasta on 2010-08-13
system log will tell you if there is any errors.
 
perhaps with audio as in my case?! Ubuntu starts very similar to yours, only still faster :-)

---

### Post by J@n on 2010-08-13
Hi,

Thanks for your reply. I checked but the problem does not seem to originate from sound. I have attached the log snippets from today. I have booted twice today and I noticed another strange thing.

At first boot my root partition was SDA5. At second boot my root partition was SDB5. It almost looks like I have MBR's at both disks. I am not sure if that causes problems, though. Note: I have a 160GB IDE drive and a 160 GB SATA drive in my system.

**First boot:**
```
Aug 13 06:53:11 Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 13 06:53:11 Ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="903" x-info="http://www.rsyslog.com"] (re)start
Aug 13 06:53:11 Ubuntu rsyslogd: rsyslogd's groupid changed to 103
Aug 13 06:53:11 Ubuntu rsyslogd: rsyslogd's userid changed to 101
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] KERNEL supported cpus:
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   Intel GenuineIntel
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   NSC Geode by NSC
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] DMI 2.4 present.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] modified physical RAM map:
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] RAMDISK: 37856000 - 37fef935
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 01079935
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Move RAMDISK from 0000000037856000 - 0000000037fef934 to 008e0000 - 01079934
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: RSDP 000f6a90 00024 (v02 Nvidia)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: XSDT 7fee3100 00054 (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: FACP 7feea400 000F4 (v03 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: DSDT 7fee3280 0710A (v01 _ASUS_ Notebook 00001000 MSFT 03000000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: FACS 7fee0000 00040
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: SLIC 7feea600 00176 (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: SSDT 7feea7c0 00248 (v01 _ASUS_ Notebook 00000001  LTP 00000001)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: HPET 7feeaa80 00038 (v01 _ASUS_ Notebook 42302E31 AWRD 00000098)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: MCFG 7feeab00 0003C (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: APIC 7feea540 0007C (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] 1158MB HIGHMEM available.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #5 [00008dc000 - 00008df158]              BRK ==> [00008dc000 - 00008df158]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #7 [00008e0000 - 0001079935]      NEW RAMDISK ==> [00008e0000 - 0001079935]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] found SMP MP-table at [c00f4f10] f4f10
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Zone PFN ranges:
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fee0
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Using APIC driver default
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-24-generic root=UUID=807b3ae9-559d-417d-825a-24a93ddf1e6f ro quiet splash
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Initializing CPU#0
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] allocated 10479680 bytes of page_cgroup
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Memory: 2051124k/2096000k available (4679k kernel code, 43440k reserved, 2116k data, 660k init, 1186696k highmem)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] virtual kernel memory layout:
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] console [tty0] enabled
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Aug 13 06:53:11 Ubuntu kernel: [    0.000000] Detected 2410.908 MHz processor.
Aug 13 06:53:11 Ubuntu kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4821.81 BogoMIPS (lpj=9643632)
Aug 13 06:53:11 Ubuntu kernel: [    0.004019] Security Framework initialized
Aug 13 06:53:11 Ubuntu kernel: [    0.004035] AppArmor: AppArmor initialized
Aug 13 06:53:11 Ubuntu kernel: [    0.004042] Mount-cache hash table entries: 512
Aug 13 06:53:11 Ubuntu kernel: [    0.004146] Initializing cgroup subsys ns
Aug 13 06:53:11 Ubuntu kernel: [    0.004149] Initializing cgroup subsys cpuacct
Aug 13 06:53:11 Ubuntu kernel: [    0.004153] Initializing cgroup subsys memory
Aug 13 06:53:11 Ubuntu kernel: [    0.004159] Initializing cgroup subsys devices
Aug 13 06:53:11 Ubuntu kernel: [    0.004161] Initializing cgroup subsys freezer
Aug 13 06:53:11 Ubuntu kernel: [    0.004163] Initializing cgroup subsys net_cls
Aug 13 06:53:11 Ubuntu kernel: [    0.004178] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 13 06:53:11 Ubuntu kernel: [    0.004181] CPU: L2 Cache: 512K (64 bytes/line)
Aug 13 06:53:11 Ubuntu kernel: [    0.004183] CPU: Physical Processor ID: 0
Aug 13 06:53:11 Ubuntu kernel: [    0.004184] CPU: Processor Core ID: 0
Aug 13 06:53:11 Ubuntu kernel: [    0.004187] mce: CPU supports 5 MCE banks
Aug 13 06:53:11 Ubuntu kernel: [    0.004197] using C1E aware idle routine
Aug 13 06:53:11 Ubuntu kernel: [    0.004203] Performance Events: AMD PMU driver.
Aug 13 06:53:11 Ubuntu kernel: [    0.004209] ... version:                0
Aug 13 06:53:11 Ubuntu kernel: [    0.004210] ... bit width:              48
Aug 13 06:53:11 Ubuntu kernel: [    0.004212] ... generic registers:      4
Aug 13 06:53:11 Ubuntu kernel: [    0.004214] ... value mask:             0000ffffffffffff
Aug 13 06:53:11 Ubuntu kernel: [    0.004216] ... max period:             00007fffffffffff
Aug 13 06:53:11 Ubuntu kernel: [    0.004217] ... fixed-purpose events:   0
Aug 13 06:53:11 Ubuntu kernel: [    0.004219] ... event mask:             000000000000000f
Aug 13 06:53:11 Ubuntu kernel: [    0.004223] Checking 'hlt' instruction... OK.
Aug 13 06:53:11 Ubuntu kernel: [    0.021882] ACPI: Core revision 20090903
Aug 13 06:53:11 Ubuntu kernel: [    0.032023] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug 13 06:53:11 Ubuntu kernel: [    0.032032] ftrace: allocating 21780 entries in 43 pages
Aug 13 06:53:11 Ubuntu kernel: [    0.036073] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 13 06:53:11 Ubuntu kernel: [    0.036530] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 13 06:53:11 Ubuntu kernel: [    0.078127] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Aug 13 06:53:11 Ubuntu kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Aug 13 06:53:11 Ubuntu kernel: [    0.008000] Initializing CPU#1
Aug 13 06:53:11 Ubuntu kernel: [    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 13 06:53:11 Ubuntu kernel: [    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
Aug 13 06:53:11 Ubuntu kernel: [    0.008000] CPU: Physical Processor ID: 0
Aug 13 06:53:11 Ubuntu kernel: [    0.008000] CPU: Processor Core ID: 1
Aug 13 06:53:11 Ubuntu kernel: [    0.164036] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Aug 13 06:53:11 Ubuntu kernel: [    0.164059] Brought up 2 CPUs
Aug 13 06:53:11 Ubuntu kernel: [    0.164061] Total of 2 processors activated (9643.96 BogoMIPS).
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] devtmpfs: initialized
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] regulator: core version 0.5
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] Time:  4:52:50  Date: 08/13/10
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] NET: Registered protocol family 16
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] Trying to unpack rootfs image as initramfs...
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] EISA bus registered
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] ACPI: bus type pci registered
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] PCI: MCFG area at f0000000 reserved in E820
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] PCI: Using MMCONFIG for extended config space
Aug 13 06:53:11 Ubuntu kernel: [    0.164317] PCI: Using configuration type 1 for base access
Aug 13 06:53:11 Ubuntu kernel: [    0.168092] bio: create slab <bio-0> at 0
Aug 13 06:53:11 Ubuntu kernel: [    0.176225] ACPI: Interpreter enabled
Aug 13 06:53:11 Ubuntu kernel: [    0.176236] ACPI: (supports S0 S1 S3 S4 S5)
Aug 13 06:53:11 Ubuntu kernel: [    0.176260] ACPI: Using IOAPIC for interrupt routing
Aug 13 06:53:11 Ubuntu kernel: [    0.183791] ACPI: No dock devices found.
Aug 13 06:53:11 Ubuntu kernel: [    0.184600] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 13 06:53:11 Ubuntu kernel: [    0.184837] pci 0000:00:01.1: PME# supported from D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.184842] pci 0000:00:01.1: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.184911] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.184914] pci 0000:00:02.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.184963] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.184966] pci 0000:00:02.1: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185050] pci 0000:00:05.0: PME# supported from D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.185053] pci 0000:00:05.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185181] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.185184] pci 0000:00:09.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185217] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.185220] pci 0000:00:0b.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185251] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.185254] pci 0000:00:0c.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185394] pci 0000:01:07.0: PME# supported from D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.185398] pci 0000:01:07.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185463] pci 0000:01:09.0: PME# supported from D1 D2 D3hot D3cold
Aug 13 06:53:11 Ubuntu kernel: [    0.185467] pci 0000:01:09.0: PME# disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.185491] pci 0000:00:04.0: transparent bridge
Aug 13 06:53:11 Ubuntu kernel: [    0.220831] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.220962] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.221094] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
Aug 13 06:53:11 Ubuntu kernel: [    0.221225] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.221357] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Aug 13 06:53:11 Ubuntu kernel: [    0.221486] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.221615] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.221747] ACPI: PCI Interrupt Link [LNK8] (IRQs *5 7 9 10 11 14 15)
Aug 13 06:53:11 Ubuntu kernel: [    0.221876] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222006] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222137] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222267] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222398] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
Aug 13 06:53:11 Ubuntu kernel: [    0.222528] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222658] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222789] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.222920] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.223051] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Aug 13 06:53:11 Ubuntu kernel: [    0.223215] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.223377] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.223538] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Aug 13 06:53:11 Ubuntu kernel: [    0.223698] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.223858] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Aug 13 06:53:11 Ubuntu kernel: [    0.224028] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.224189] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.224349] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Aug 13 06:53:11 Ubuntu kernel: [    0.224509] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.224670] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.224831] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.224992] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.225153] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
Aug 13 06:53:11 Ubuntu kernel: [    0.225313] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.225474] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.225635] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.225798] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
Aug 13 06:53:11 Ubuntu kernel: [    0.225959] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
Aug 13 06:53:11 Ubuntu kernel: [    0.226067] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 13 06:53:11 Ubuntu kernel: [    0.226071] vgaarb: loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.226168] SCSI subsystem initialized
Aug 13 06:53:11 Ubuntu kernel: [    0.226313] usbcore: registered new interface driver usbfs
Aug 13 06:53:11 Ubuntu kernel: [    0.226324] usbcore: registered new interface driver hub
Aug 13 06:53:11 Ubuntu kernel: [    0.226349] usbcore: registered new device driver usb
Aug 13 06:53:11 Ubuntu kernel: [    0.226465] ACPI: WMI: Mapper loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.226467] PCI: Using ACPI for IRQ routing
Aug 13 06:53:11 Ubuntu kernel: [    0.226592] NetLabel: Initializing
Aug 13 06:53:11 Ubuntu kernel: [    0.226594] NetLabel:  domain hash size = 128
Aug 13 06:53:11 Ubuntu kernel: [    0.226595] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 13 06:53:11 Ubuntu kernel: [    0.226607] NetLabel:  unlabeled traffic allowed by default
Aug 13 06:53:11 Ubuntu kernel: [    0.226637] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
Aug 13 06:53:11 Ubuntu kernel: [    0.226642] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Aug 13 06:53:11 Ubuntu kernel: [    0.232114] Switching to clocksource hpet
Aug 13 06:53:11 Ubuntu kernel: [    0.233633] AppArmor: AppArmor Filesystem Enabled
Aug 13 06:53:11 Ubuntu kernel: [    0.233652] pnp: PnP ACPI init
Aug 13 06:53:11 Ubuntu kernel: [    0.233668] ACPI: bus type pnp registered
Aug 13 06:53:11 Ubuntu kernel: [    0.238163] pnp: PnP ACPI: found 12 devices
Aug 13 06:53:11 Ubuntu kernel: [    0.238165] ACPI: ACPI bus type pnp unregistered
Aug 13 06:53:11 Ubuntu kernel: [    0.238168] PnPBIOS: Disabled by ACPI PNP
Aug 13 06:53:11 Ubuntu kernel: [    0.238179] system 00:01: ioport range 0x1000-0x107f has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238183] system 00:01: ioport range 0x1080-0x10ff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238186] system 00:01: ioport range 0x1400-0x147f has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238189] system 00:01: ioport range 0x1480-0x14ff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238192] system 00:01: ioport range 0x1800-0x187f has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238195] system 00:01: ioport range 0x1880-0x18ff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238201] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238204] system 00:02: ioport range 0x800-0x87f has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238207] system 00:02: ioport range 0x290-0x297 has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238215] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238221] system 00:0b: iomem range 0xcf200-0xcffff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238224] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238228] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238231] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238235] system 00:0b: iomem range 0xfefff000-0xfefff0ff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238238] system 00:0b: iomem range 0x7fee0000-0x7fefffff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238242] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238245] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238248] system 00:0b: iomem range 0x100000-0x7fedffff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238252] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238256] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238259] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238263] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238266] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.238270] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
Aug 13 06:53:11 Ubuntu kernel: [    0.272959] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Aug 13 06:53:11 Ubuntu kernel: [    0.272962] pci 0000:00:04.0:   IO window: 0xc000-0xcfff
Aug 13 06:53:11 Ubuntu kernel: [    0.272966] pci 0000:00:04.0:   MEM window: 0xfdf00000-0xfdffffff
Aug 13 06:53:11 Ubuntu kernel: [    0.272969] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
Aug 13 06:53:11 Ubuntu kernel: [    0.272974] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Aug 13 06:53:11 Ubuntu kernel: [    0.272977] pci 0000:00:09.0:   IO window: 0xb000-0xbfff
Aug 13 06:53:11 Ubuntu kernel: [    0.272980] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff
Aug 13 06:53:11 Ubuntu kernel: [    0.272984] pci 0000:00:09.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Aug 13 06:53:11 Ubuntu kernel: [    0.272988] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Aug 13 06:53:11 Ubuntu kernel: [    0.272990] pci 0000:00:0b.0:   IO window: 0xa000-0xafff
Aug 13 06:53:11 Ubuntu kernel: [    0.272994] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Aug 13 06:53:11 Ubuntu kernel: [    0.272997] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Aug 13 06:53:11 Ubuntu kernel: [    0.273001] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Aug 13 06:53:11 Ubuntu kernel: [    0.273004] pci 0000:00:0c.0:   IO window: 0x9000-0x9fff
Aug 13 06:53:11 Ubuntu kernel: [    0.273007] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Aug 13 06:53:11 Ubuntu kernel: [    0.273011] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Aug 13 06:53:11 Ubuntu kernel: [    0.273112] NET: Registered protocol family 2
Aug 13 06:53:11 Ubuntu kernel: [    0.273193] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.273493] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.274060] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.274346] TCP: Hash tables configured (established 131072 bind 65536)
Aug 13 06:53:11 Ubuntu kernel: [    0.274348] TCP reno registered
Aug 13 06:53:11 Ubuntu kernel: [    0.274431] NET: Registered protocol family 1
Aug 13 06:53:11 Ubuntu kernel: [    0.288084] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 06:53:11 Ubuntu kernel: [    0.288132] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 06:53:11 Ubuntu kernel: [    0.288186] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 06:53:11 Ubuntu kernel: [    0.288240] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 06:53:11 Ubuntu kernel: [    0.288297] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 06:53:11 Ubuntu kernel: [    0.288359] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 06:53:11 Ubuntu kernel: [    0.288536] cpufreq-nforce2: No nForce2 chipset.
Aug 13 06:53:11 Ubuntu kernel: [    0.288559] Scanning for low memory corruption every 60 seconds
Aug 13 06:53:11 Ubuntu kernel: [    0.288647] audit: initializing netlink socket (disabled)
Aug 13 06:53:11 Ubuntu kernel: [    0.288658] type=2000 audit(1281675170.288:1): initialized
Aug 13 06:53:11 Ubuntu kernel: [    0.297150] highmem bounce pool size: 64 pages
Aug 13 06:53:11 Ubuntu kernel: [    0.297154] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 13 06:53:11 Ubuntu kernel: [    0.298436] VFS: Disk quotas dquot_6.5.2
Aug 13 06:53:11 Ubuntu kernel: [    0.298484] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 13 06:53:11 Ubuntu kernel: [    0.298960] fuse init (API version 7.13)
Aug 13 06:53:11 Ubuntu kernel: [    0.299032] msgmni has been set to 1690
Aug 13 06:53:11 Ubuntu kernel: [    0.299212] alg: No test for stdrng (krng)
Aug 13 06:53:11 Ubuntu kernel: [    0.299259] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 13 06:53:11 Ubuntu kernel: [    0.299262] io scheduler noop registered
Aug 13 06:53:11 Ubuntu kernel: [    0.299264] io scheduler anticipatory registered
Aug 13 06:53:11 Ubuntu kernel: [    0.299266] io scheduler deadline registered
Aug 13 06:53:11 Ubuntu kernel: [    0.299300] io scheduler cfq registered (default)
Aug 13 06:53:11 Ubuntu kernel: [    0.299610] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 13 06:53:11 Ubuntu kernel: [    0.299631] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 13 06:53:11 Ubuntu kernel: [    0.299721] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug 13 06:53:11 Ubuntu kernel: [    0.299724] ACPI: Power Button [PWRB]
Aug 13 06:53:11 Ubuntu kernel: [    0.299780] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug 13 06:53:11 Ubuntu kernel: [    0.299783] ACPI: Power Button [PWRF]
Aug 13 06:53:11 Ubuntu kernel: [    0.299827] fan PNP0C0B:00: registered as cooling_device0
Aug 13 06:53:11 Ubuntu kernel: [    0.299834] ACPI: Fan [FAN] (on)
Aug 13 06:53:11 Ubuntu kernel: [    0.300210] processor LNXCPU:00: registered as cooling_device1
Aug 13 06:53:11 Ubuntu kernel: [    0.300238] processor LNXCPU:01: registered as cooling_device2
Aug 13 06:53:11 Ubuntu kernel: [    0.304252] thermal LNXTHERM:01: registered as thermal_zone0
Aug 13 06:53:11 Ubuntu kernel: [    0.304258] ACPI: Thermal Zone [THRM] (40 C)
Aug 13 06:53:11 Ubuntu kernel: [    0.305630] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 13 06:53:11 Ubuntu kernel: [    0.305751] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 13 06:53:11 Ubuntu kernel: [    0.305999] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 13 06:53:11 Ubuntu kernel: [    0.306964] brd: module loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.307394] loop: module loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.307479] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Aug 13 06:53:11 Ubuntu kernel: [    0.307960] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Aug 13 06:53:11 Ubuntu kernel: [    0.307977] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Aug 13 06:53:11 Ubuntu kernel: [    0.308025] pata_acpi 0000:00:08.0: PCI INT A disabled
Aug 13 06:53:11 Ubuntu kernel: [    0.308300] Fixed MDIO Bus: probed
Aug 13 06:53:11 Ubuntu kernel: [    0.308329] PPP generic driver version 2.4.2
Aug 13 06:53:11 Ubuntu kernel: [    0.308367] tun: Universal TUN/TAP device driver, 1.6
Aug 13 06:53:11 Ubuntu kernel: [    0.308369] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 13 06:53:11 Ubuntu kernel: [    0.308443] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 13 06:53:11 Ubuntu kernel: [    0.308731] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Aug 13 06:53:11 Ubuntu kernel: [    0.308743] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
Aug 13 06:53:11 Ubuntu kernel: [    0.308759] ehci_hcd 0000:00:02.1: EHCI Host Controller
Aug 13 06:53:11 Ubuntu kernel: [    0.308789] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Aug 13 06:53:11 Ubuntu kernel: [    0.308807] ehci_hcd 0000:00:02.1: debug port 1
Aug 13 06:53:11 Ubuntu kernel: [    0.308834] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
Aug 13 06:53:11 Ubuntu kernel: [    0.308877] isapnp: Scanning for PnP cards...
Aug 13 06:53:11 Ubuntu kernel: [    0.356512] Freeing initrd memory: 7782k freed
Aug 13 06:53:11 Ubuntu kernel: [    0.357724] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Aug 13 06:53:11 Ubuntu kernel: [    0.357808] usb usb1: configuration #1 chosen from 1 choice
Aug 13 06:53:11 Ubuntu kernel: [    0.357836] hub 1-0:1.0: USB hub found
Aug 13 06:53:11 Ubuntu kernel: [    0.357845] hub 1-0:1.0: 8 ports detected
Aug 13 06:53:11 Ubuntu kernel: [    0.357906] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 13 06:53:11 Ubuntu kernel: [    0.358203] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Aug 13 06:53:11 Ubuntu kernel: [    0.358216] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
Aug 13 06:53:11 Ubuntu kernel: [    0.358229] ohci_hcd 0000:00:02.0: OHCI Host Controller
Aug 13 06:53:11 Ubuntu kernel: [    0.358260] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Aug 13 06:53:11 Ubuntu kernel: [    0.358283] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfe02f000
Aug 13 06:53:11 Ubuntu kernel: [    0.415136] usb usb2: configuration #1 chosen from 1 choice
Aug 13 06:53:11 Ubuntu kernel: [    0.415163] hub 2-0:1.0: USB hub found
Aug 13 06:53:11 Ubuntu kernel: [    0.415175] hub 2-0:1.0: 8 ports detected
Aug 13 06:53:11 Ubuntu kernel: [    0.415233] uhci_hcd: USB Universal Host Controller Interface driver
Aug 13 06:53:11 Ubuntu kernel: [    0.415318] PNP: No PS/2 controller found. Probing ports directly.
Aug 13 06:53:11 Ubuntu kernel: [    0.415730] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 13 06:53:11 Ubuntu kernel: [    0.415737] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 13 06:53:11 Ubuntu kernel: [    0.415802] mice: PS/2 mouse device common for all mice
Aug 13 06:53:11 Ubuntu kernel: [    0.415889] rtc_cmos 00:05: RTC can wake from S4
Aug 13 06:53:11 Ubuntu kernel: [    0.415926] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug 13 06:53:11 Ubuntu kernel: [    0.415963] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Aug 13 06:53:11 Ubuntu kernel: [    0.416048] device-mapper: uevent: version 1.0.3
Aug 13 06:53:11 Ubuntu kernel: [    0.416147] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug 13 06:53:11 Ubuntu kernel: [    0.416206] device-mapper: multipath: version 1.1.0 loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.416209] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.416306] EISA: Probing bus 0 at eisa.0
Aug 13 06:53:11 Ubuntu kernel: [    0.416312] Cannot allocate resource for EISA slot 1
Aug 13 06:53:11 Ubuntu kernel: [    0.416329] EISA: Detected 0 cards.
Aug 13 06:53:11 Ubuntu kernel: [    0.416393] cpuidle: using governor ladder
Aug 13 06:53:11 Ubuntu kernel: [    0.416395] cpuidle: using governor menu
Aug 13 06:53:11 Ubuntu kernel: [    0.416773] TCP cubic registered
Aug 13 06:53:11 Ubuntu kernel: [    0.416898] NET: Registered protocol family 10
Aug 13 06:53:11 Ubuntu kernel: [    0.417296] lo: Disabled Privacy Extensions
Aug 13 06:53:11 Ubuntu kernel: [    0.417567] NET: Registered protocol family 17
Aug 13 06:53:11 Ubuntu kernel: [    0.417595] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (2 cpu cores) (version 2.20.00)
Aug 13 06:53:11 Ubuntu kernel: [    0.417639] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0xc
Aug 13 06:53:11 Ubuntu kernel: [    0.417641] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xe
Aug 13 06:53:11 Ubuntu kernel: [    0.417643] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x10
Aug 13 06:53:11 Ubuntu kernel: [    0.417645] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x10
Aug 13 06:53:11 Ubuntu kernel: [    0.417647] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
Aug 13 06:53:11 Ubuntu kernel: [    0.445104] Using IPI No-Shortcut mode
Aug 13 06:53:11 Ubuntu kernel: [    0.445177] registered taskstats version 1
Aug 13 06:53:11 Ubuntu kernel: [    0.445420]   Magic number: 6:748:868
Aug 13 06:53:11 Ubuntu kernel: [    0.445508] rtc_cmos 00:05: setting system clock to 2010-08-13 04:52:51 UTC (1281675171)
Aug 13 06:53:11 Ubuntu kernel: [    0.445511] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 13 06:53:11 Ubuntu kernel: [    0.445513] EDD information not available.
Aug 13 06:53:11 Ubuntu kernel: [    0.662119] isapnp: No Plug & Play device found
Aug 13 06:53:11 Ubuntu kernel: [    0.662132] Freeing unused kernel memory: 660k freed
Aug 13 06:53:11 Ubuntu kernel: [    0.662530] Write protecting the kernel text: 4680k
Aug 13 06:53:11 Ubuntu kernel: [    0.662562] Write protecting the kernel read-only data: 1840k
Aug 13 06:53:11 Ubuntu kernel: [    0.678624] udev: starting version 151
Aug 13 06:53:11 Ubuntu kernel: [    0.685039] usb 1-1: new high speed USB device using ehci_hcd and address 2
Aug 13 06:53:11 Ubuntu kernel: [    0.765720] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug 13 06:53:11 Ubuntu kernel: [    0.766042] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Aug 13 06:53:11 Ubuntu kernel: [    0.766060] r8169 0000:01:09.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Aug 13 06:53:11 Ubuntu kernel: [    0.766083] r8169 0000:01:09.0: no PCI Express capability
Aug 13 06:53:11 Ubuntu kernel: [    0.766618] eth0: RTL8169sb/8110sb at 0xf80ba000, 00:06:4f:76:bd:32, XID 10000000 IRQ 18
Aug 13 06:53:11 Ubuntu kernel: [    0.782145] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Aug 13 06:53:11 Ubuntu kernel: [    0.782162] ohci1394 0000:01:07.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Aug 13 06:53:11 Ubuntu kernel: [    0.783269] scsi0 : pata_amd
Aug 13 06:53:11 Ubuntu kernel: [    0.791637] scsi1 : pata_amd
Aug 13 06:53:11 Ubuntu kernel: [    0.792398] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Aug 13 06:53:11 Ubuntu kernel: [    0.792401] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Aug 13 06:53:11 Ubuntu kernel: [    0.792545] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Aug 13 06:53:11 Ubuntu kernel: [    0.795994] scsi2 : sata_nv
Aug 13 06:53:11 Ubuntu kernel: [    0.796114] scsi3 : sata_nv
Aug 13 06:53:11 Ubuntu kernel: [    0.796282] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 20
Aug 13 06:53:11 Ubuntu kernel: [    0.796285] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 20
Aug 13 06:53:11 Ubuntu kernel: [    0.816692] usb 1-1: configuration #1 chosen from 1 choice
Aug 13 06:53:11 Ubuntu kernel: [    0.816761] hub 1-1:1.0: USB hub found
Aug 13 06:53:11 Ubuntu kernel: [    0.816858] hub 1-1:1.0: 4 ports detected
Aug 13 06:53:11 Ubuntu kernel: [    0.842030] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 13 06:53:11 Ubuntu kernel: [    1.020312] ata1.00: ATAPI: _NEC DVD_RW ND-4570A, 1.02, max UDMA/33
Aug 13 06:53:11 Ubuntu kernel: [    1.020739] ata1.01: ATA-6: ST3160023A, 8.16, max UDMA/100
Aug 13 06:53:11 Ubuntu kernel: [    1.020742] ata1.01: 312581808 sectors, multi 16: LBA48 
Aug 13 06:53:11 Ubuntu kernel: [    1.036271] ata1.00: configured for UDMA/33
Aug 13 06:53:11 Ubuntu kernel: [    1.052388] ata1.01: configured for UDMA/100
Aug 13 06:53:11 Ubuntu kernel: [    1.053707] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-4570A  1.02 PQ: 0 ANSI: 5
Aug 13 06:53:11 Ubuntu kernel: [    1.056689] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 13 06:53:11 Ubuntu kernel: [    1.056692] Uniform CD-ROM driver Revision: 3.20
Aug 13 06:53:11 Ubuntu kernel: [    1.056837] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 13 06:53:11 Ubuntu kernel: [    1.057002] scsi 0:0:1:0: Direct-Access     ATA      ST3160023A       8.16 PQ: 0 ANSI: 5
Aug 13 06:53:11 Ubuntu kernel: [    1.057119] sd 0:0:1:0: Attached scsi generic sg1 type 0
Aug 13 06:53:11 Ubuntu kernel: [    1.057221] sd 0:0:1:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug 13 06:53:11 Ubuntu kernel: [    1.057258] sd 0:0:1:0: [sda] Write Protect is off
Aug 13 06:53:11 Ubuntu kernel: [    1.057279] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 13 06:53:11 Ubuntu kernel: [    1.057400]  sda: sda1 sda2 < sda5 sda6 sda7 >
Aug 13 06:53:11 Ubuntu kernel: [    1.087245] sd 0:0:1:0: [sda] Attached SCSI disk
Aug 13 06:53:11 Ubuntu kernel: [    1.176013] usb 2-2: new low speed USB device using ohci_hcd and address 2
Aug 13 06:53:11 Ubuntu kernel: [    1.264031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 13 06:53:11 Ubuntu kernel: [    1.272215] ata3.00: ATA-7: WDC WD1600JS-55MHB0, 02.01C03, max UDMA/133
Aug 13 06:53:11 Ubuntu kernel: [    1.272218] ata3.00: 312581808 sectors, multi 16: LBA48 
Aug 13 06:53:11 Ubuntu kernel: [    1.280226] ata3.00: configured for UDMA/133
Aug 13 06:53:11 Ubuntu kernel: [    1.280300] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JS-55M 02.0 PQ: 0 ANSI: 5
Aug 13 06:53:11 Ubuntu kernel: [    1.280435] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug 13 06:53:11 Ubuntu kernel: [    1.280459] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug 13 06:53:11 Ubuntu kernel: [    1.280540] sd 2:0:0:0: [sdb] Write Protect is off
Aug 13 06:53:11 Ubuntu kernel: [    1.280562] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 13 06:53:11 Ubuntu kernel: [    1.280674]  sdb: sdb1
Aug 13 06:53:11 Ubuntu kernel: [    1.290729] sd 2:0:0:0: [sdb] Attached SCSI disk
Aug 13 06:53:11 Ubuntu kernel: [    1.390102] usb 2-2: configuration #1 chosen from 1 choice
Aug 13 06:53:11 Ubuntu kernel: [    1.402966] usbcore: registered new interface driver hiddev
Aug 13 06:53:11 Ubuntu kernel: [    1.409288] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
Aug 13 06:53:11 Ubuntu kernel: [    1.409366] generic-usb 0003:03F0:0F0C.0001: input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:02.0-2/input0
Aug 13 06:53:11 Ubuntu kernel: [    1.419489] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input4
Aug 13 06:53:11 Ubuntu kernel: [    1.419594] generic-usb 0003:03F0:0F0C.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:02.0-2/input1
Aug 13 06:53:11 Ubuntu kernel: [    1.419614] usbcore: registered new interface driver usbhid
Aug 13 06:53:11 Ubuntu kernel: [    1.419617] usbhid: v2.6:USB HID core driver
Aug 13 06:53:11 Ubuntu kernel: [    1.464115] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
Aug 13 06:53:11 Ubuntu kernel: [    1.556667] usb 1-1.2: configuration #1 chosen from 1 choice
Aug 13 06:53:11 Ubuntu kernel: [    1.556783] hub 1-1.2:1.0: USB hub found
Aug 13 06:53:11 Ubuntu kernel: [    1.556861] hub 1-1.2:1.0: 4 ports detected
Aug 13 06:53:11 Ubuntu kernel: [    1.602235] ata4: SATA link down (SStatus 0 SControl 300)
Aug 13 06:53:11 Ubuntu kernel: [    1.945857] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Aug 13 06:53:11 Ubuntu kernel: [    1.945862] EXT4-fs (sda5): write access will be enabled during recovery
Aug 13 06:53:11 Ubuntu kernel: [    5.643475] EXT4-fs (sda5): recovery complete
[COLOR="Red"]Aug 13 06:53:11 Ubuntu kernel: [    5.656632] EXT4-fs (sda5): mounted filesystem with ordered data mode
Aug 13 06:53:11 Ubuntu kernel: [   17.975353] Adding 3998712k swap on /dev/sda6.  Priority:-1 extents:1 across:3998712k 
[/COLOR]Aug 13 06:53:11 Ubuntu kernel: [   17.998362] udev: starting version 151
Aug 13 06:53:11 Ubuntu kernel: [   18.031474] ACPI: resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
Aug 13 06:53:11 Ubuntu kernel: [   18.031478] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Aug 13 06:53:11 Ubuntu kernel: [   18.031566] i2c i2c-0: nForce2 SMBus adapter at 0x1c40
Aug 13 06:53:11 Ubuntu kernel: [   18.043339] lp: driver loaded but no devices found
```

**Second boot:**
```
Aug 13 12:33:00 Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 13 12:33:00 Ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="852" x-info="http://www.rsyslog.com"] (re)start
Aug 13 12:33:00 Ubuntu rsyslogd: rsyslogd's groupid changed to 103
Aug 13 12:33:00 Ubuntu rsyslogd: rsyslogd's userid changed to 101
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] KERNEL supported cpus:
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   Intel GenuineIntel
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   NSC Geode by NSC
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] DMI 2.4 present.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] modified physical RAM map:
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] RAMDISK: 37856000 - 37fef935
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 01079935
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Move RAMDISK from 0000000037856000 - 0000000037fef934 to 008e0000 - 01079934
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: RSDP 000f6a90 00024 (v02 Nvidia)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: XSDT 7fee3100 00054 (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: FACP 7feea400 000F4 (v03 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: DSDT 7fee3280 0710A (v01 _ASUS_ Notebook 00001000 MSFT 03000000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: FACS 7fee0000 00040
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: SLIC 7feea600 00176 (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: SSDT 7feea7c0 00248 (v01 _ASUS_ Notebook 00000001  LTP 00000001)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: HPET 7feeaa80 00038 (v01 _ASUS_ Notebook 42302E31 AWRD 00000098)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: MCFG 7feeab00 0003C (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: APIC 7feea540 0007C (v01 _ASUS_ Notebook 42302E31 AWRD 00000000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] 1158MB HIGHMEM available.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #5 [00008dc000 - 00008df158]              BRK ==> [00008dc000 - 00008df158]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #7 [00008e0000 - 0001079935]      NEW RAMDISK ==> [00008e0000 - 0001079935]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] found SMP MP-table at [c00f4f10] f4f10
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Zone PFN ranges:
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fee0
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Using APIC driver default
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-24-generic root=UUID=807b3ae9-559d-417d-825a-24a93ddf1e6f ro quiet splash
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Initializing CPU#0
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] allocated 10479680 bytes of page_cgroup
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Memory: 2051124k/2096000k available (4679k kernel code, 43440k reserved, 2116k data, 660k init, 1186696k highmem)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] virtual kernel memory layout:
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] console [tty0] enabled
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Aug 13 12:33:00 Ubuntu kernel: [    0.000000] Detected 2410.974 MHz processor.
Aug 13 12:33:00 Ubuntu kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4821.94 BogoMIPS (lpj=9643896)
Aug 13 12:33:00 Ubuntu kernel: [    0.004019] Security Framework initialized
Aug 13 12:33:00 Ubuntu kernel: [    0.004035] AppArmor: AppArmor initialized
Aug 13 12:33:00 Ubuntu kernel: [    0.004042] Mount-cache hash table entries: 512
Aug 13 12:33:00 Ubuntu kernel: [    0.004147] Initializing cgroup subsys ns
Aug 13 12:33:00 Ubuntu kernel: [    0.004150] Initializing cgroup subsys cpuacct
Aug 13 12:33:00 Ubuntu kernel: [    0.004154] Initializing cgroup subsys memory
Aug 13 12:33:00 Ubuntu kernel: [    0.004160] Initializing cgroup subsys devices
Aug 13 12:33:00 Ubuntu kernel: [    0.004162] Initializing cgroup subsys freezer
Aug 13 12:33:00 Ubuntu kernel: [    0.004164] Initializing cgroup subsys net_cls
Aug 13 12:33:00 Ubuntu kernel: [    0.004179] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 13 12:33:00 Ubuntu kernel: [    0.004181] CPU: L2 Cache: 512K (64 bytes/line)
Aug 13 12:33:00 Ubuntu kernel: [    0.004183] CPU: Physical Processor ID: 0
Aug 13 12:33:00 Ubuntu kernel: [    0.004185] CPU: Processor Core ID: 0
Aug 13 12:33:00 Ubuntu kernel: [    0.004188] mce: CPU supports 5 MCE banks
Aug 13 12:33:00 Ubuntu kernel: [    0.004197] using C1E aware idle routine
Aug 13 12:33:00 Ubuntu kernel: [    0.004204] Performance Events: AMD PMU driver.
Aug 13 12:33:00 Ubuntu kernel: [    0.004209] ... version:                0
Aug 13 12:33:00 Ubuntu kernel: [    0.004211] ... bit width:              48
Aug 13 12:33:00 Ubuntu kernel: [    0.004212] ... generic registers:      4
Aug 13 12:33:00 Ubuntu kernel: [    0.004214] ... value mask:             0000ffffffffffff
Aug 13 12:33:00 Ubuntu kernel: [    0.004216] ... max period:             00007fffffffffff
Aug 13 12:33:00 Ubuntu kernel: [    0.004218] ... fixed-purpose events:   0
Aug 13 12:33:00 Ubuntu kernel: [    0.004219] ... event mask:             000000000000000f
Aug 13 12:33:00 Ubuntu kernel: [    0.004223] Checking 'hlt' instruction... OK.
Aug 13 12:33:00 Ubuntu kernel: [    0.021882] ACPI: Core revision 20090903
Aug 13 12:33:00 Ubuntu kernel: [    0.032023] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug 13 12:33:00 Ubuntu kernel: [    0.032032] ftrace: allocating 21780 entries in 43 pages
Aug 13 12:33:00 Ubuntu kernel: [    0.036073] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 13 12:33:00 Ubuntu kernel: [    0.036529] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 13 12:33:00 Ubuntu kernel: [    0.078128] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Aug 13 12:33:00 Ubuntu kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Aug 13 12:33:00 Ubuntu kernel: [    0.008000] Initializing CPU#1
Aug 13 12:33:00 Ubuntu kernel: [    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 13 12:33:00 Ubuntu kernel: [    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
Aug 13 12:33:00 Ubuntu kernel: [    0.008000] CPU: Physical Processor ID: 0
Aug 13 12:33:00 Ubuntu kernel: [    0.008000] CPU: Processor Core ID: 1
Aug 13 12:33:00 Ubuntu kernel: [    0.164034] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Aug 13 12:33:00 Ubuntu kernel: [    0.164058] Brought up 2 CPUs
Aug 13 12:33:00 Ubuntu kernel: [    0.164060] Total of 2 processors activated (9644.19 BogoMIPS).
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] devtmpfs: initialized
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] regulator: core version 0.5
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] Time: 10:32:46  Date: 08/13/10
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] NET: Registered protocol family 16
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] Trying to unpack rootfs image as initramfs...
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] EISA bus registered
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] ACPI: bus type pci registered
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] PCI: MCFG area at f0000000 reserved in E820
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] PCI: Using MMCONFIG for extended config space
Aug 13 12:33:00 Ubuntu kernel: [    0.164315] PCI: Using configuration type 1 for base access
Aug 13 12:33:00 Ubuntu kernel: [    0.168093] bio: create slab <bio-0> at 0
Aug 13 12:33:00 Ubuntu kernel: [    0.176222] ACPI: Interpreter enabled
Aug 13 12:33:00 Ubuntu kernel: [    0.176233] ACPI: (supports S0 S1 S3 S4 S5)
Aug 13 12:33:00 Ubuntu kernel: [    0.176258] ACPI: Using IOAPIC for interrupt routing
Aug 13 12:33:00 Ubuntu kernel: [    0.183788] ACPI: No dock devices found.
Aug 13 12:33:00 Ubuntu kernel: [    0.184597] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 13 12:33:00 Ubuntu kernel: [    0.184834] pci 0000:00:01.1: PME# supported from D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.184840] pci 0000:00:01.1: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.184908] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.184911] pci 0000:00:02.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.184960] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.184963] pci 0000:00:02.1: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185047] pci 0000:00:05.0: PME# supported from D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.185050] pci 0000:00:05.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185179] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.185182] pci 0000:00:09.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185214] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.185217] pci 0000:00:0b.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185248] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.185251] pci 0000:00:0c.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185392] pci 0000:01:07.0: PME# supported from D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.185396] pci 0000:01:07.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185460] pci 0000:01:09.0: PME# supported from D1 D2 D3hot D3cold
Aug 13 12:33:00 Ubuntu kernel: [    0.185464] pci 0000:01:09.0: PME# disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.185488] pci 0000:00:04.0: transparent bridge
Aug 13 12:33:00 Ubuntu kernel: [    0.220816] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.220948] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.221080] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
Aug 13 12:33:00 Ubuntu kernel: [    0.221209] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.221340] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Aug 13 12:33:00 Ubuntu kernel: [    0.221469] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.221599] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.221730] ACPI: PCI Interrupt Link [LNK8] (IRQs *5 7 9 10 11 14 15)
Aug 13 12:33:00 Ubuntu kernel: [    0.221859] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.221989] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.222119] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.222249] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.222380] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
Aug 13 12:33:00 Ubuntu kernel: [    0.222510] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.222640] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.222770] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.222901] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.223032] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Aug 13 12:33:00 Ubuntu kernel: [    0.223196] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.223358] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.223520] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Aug 13 12:33:00 Ubuntu kernel: [    0.223681] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.223842] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Aug 13 12:33:00 Ubuntu kernel: [    0.224011] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.224172] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.224332] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Aug 13 12:33:00 Ubuntu kernel: [    0.224491] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.224652] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.224813] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.224974] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.225134] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
Aug 13 12:33:00 Ubuntu kernel: [    0.225294] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.225455] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.225616] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.225779] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
Aug 13 12:33:00 Ubuntu kernel: [    0.225940] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
Aug 13 12:33:00 Ubuntu kernel: [    0.226047] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 13 12:33:00 Ubuntu kernel: [    0.226050] vgaarb: loaded
Aug 13 12:33:00 Ubuntu kernel: [    0.226148] SCSI subsystem initialized
Aug 13 12:33:00 Ubuntu kernel: [    0.226293] usbcore: registered new interface driver usbfs
Aug 13 12:33:00 Ubuntu kernel: [    0.226304] usbcore: registered new interface driver hub
Aug 13 12:33:00 Ubuntu kernel: [    0.226331] usbcore: registered new device driver usb
Aug 13 12:33:00 Ubuntu kernel: [    0.226448] ACPI: WMI: Mapper loaded
Aug 13 12:33:00 Ubuntu kernel: [    0.226450] PCI: Using ACPI for IRQ routing
Aug 13 12:33:00 Ubuntu kernel: [    0.226575] NetLabel: Initializing
Aug 13 12:33:00 Ubuntu kernel: [    0.226577] NetLabel:  domain hash size = 128
Aug 13 12:33:00 Ubuntu kernel: [    0.226578] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 13 12:33:00 Ubuntu kernel: [    0.226590] NetLabel:  unlabeled traffic allowed by default
Aug 13 12:33:00 Ubuntu kernel: [    0.226620] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
Aug 13 12:33:00 Ubuntu kernel: [    0.226624] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Aug 13 12:33:00 Ubuntu kernel: [    0.232120] Switching to clocksource hpet
Aug 13 12:33:00 Ubuntu kernel: [    0.233631] AppArmor: AppArmor Filesystem Enabled
Aug 13 12:33:00 Ubuntu kernel: [    0.233649] pnp: PnP ACPI init
Aug 13 12:33:00 Ubuntu kernel: [    0.233665] ACPI: bus type pnp registered
Aug 13 12:33:00 Ubuntu kernel: [    0.238159] pnp: PnP ACPI: found 12 devices
Aug 13 12:33:00 Ubuntu kernel: [    0.238161] ACPI: ACPI bus type pnp unregistered
Aug 13 12:33:00 Ubuntu kernel: [    0.238164] PnPBIOS: Disabled by ACPI PNP
Aug 13 12:33:00 Ubuntu kernel: [    0.238175] system 00:01: ioport range 0x1000-0x107f has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238178] system 00:01: ioport range 0x1080-0x10ff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238181] system 00:01: ioport range 0x1400-0x147f has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238185] system 00:01: ioport range 0x1480-0x14ff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238188] system 00:01: ioport range 0x1800-0x187f has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238191] system 00:01: ioport range 0x1880-0x18ff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238197] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238200] system 00:02: ioport range 0x800-0x87f has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238203] system 00:02: ioport range 0x290-0x297 has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238211] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238216] system 00:0b: iomem range 0xcf200-0xcffff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238220] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238223] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238227] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238230] system 00:0b: iomem range 0xfefff000-0xfefff0ff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238234] system 00:0b: iomem range 0x7fee0000-0x7fefffff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238237] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238241] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238244] system 00:0b: iomem range 0x100000-0x7fedffff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238248] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238251] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238255] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238258] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238262] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.238265] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
Aug 13 12:33:00 Ubuntu kernel: [    0.272953] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Aug 13 12:33:00 Ubuntu kernel: [    0.272956] pci 0000:00:04.0:   IO window: 0xc000-0xcfff
Aug 13 12:33:00 Ubuntu kernel: [    0.272960] pci 0000:00:04.0:   MEM window: 0xfdf00000-0xfdffffff
Aug 13 12:33:00 Ubuntu kernel: [    0.272963] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
Aug 13 12:33:00 Ubuntu kernel: [    0.272968] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Aug 13 12:33:00 Ubuntu kernel: [    0.272971] pci 0000:00:09.0:   IO window: 0xb000-0xbfff
Aug 13 12:33:00 Ubuntu kernel: [    0.272974] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff
Aug 13 12:33:00 Ubuntu kernel: [    0.272978] pci 0000:00:09.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Aug 13 12:33:00 Ubuntu kernel: [    0.272982] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Aug 13 12:33:00 Ubuntu kernel: [    0.272984] pci 0000:00:0b.0:   IO window: 0xa000-0xafff
Aug 13 12:33:00 Ubuntu kernel: [    0.272988] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Aug 13 12:33:00 Ubuntu kernel: [    0.272991] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Aug 13 12:33:00 Ubuntu kernel: [    0.272995] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Aug 13 12:33:00 Ubuntu kernel: [    0.272998] pci 0000:00:0c.0:   IO window: 0x9000-0x9fff
Aug 13 12:33:00 Ubuntu kernel: [    0.273001] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Aug 13 12:33:00 Ubuntu kernel: [    0.273005] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Aug 13 12:33:00 Ubuntu kernel: [    0.273106] NET: Registered protocol family 2
Aug 13 12:33:00 Ubuntu kernel: [    0.273187] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.273489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.274058] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.274342] TCP: Hash tables configured (established 131072 bind 65536)
Aug 13 12:33:00 Ubuntu kernel: [    0.274344] TCP reno registered
Aug 13 12:33:00 Ubuntu kernel: [    0.274428] NET: Registered protocol family 1
Aug 13 12:33:00 Ubuntu kernel: [    0.288084] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 12:33:00 Ubuntu kernel: [    0.288133] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 12:33:00 Ubuntu kernel: [    0.288186] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 12:33:00 Ubuntu kernel: [    0.288240] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 12:33:00 Ubuntu kernel: [    0.288298] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 12:33:00 Ubuntu kernel: [    0.288359] pci 0000:00:00.0: Found enabled HT MSI Mapping
Aug 13 12:33:00 Ubuntu kernel: [    0.288538] cpufreq-nforce2: No nForce2 chipset.
Aug 13 12:33:00 Ubuntu kernel: [    0.288560] Scanning for low memory corruption every 60 seconds
Aug 13 12:33:00 Ubuntu kernel: [    0.288649] audit: initializing netlink socket (disabled)
Aug 13 12:33:00 Ubuntu kernel: [    0.288659] type=2000 audit(1281695565.288:1): initialized
Aug 13 12:33:00 Ubuntu kernel: [    0.297153] highmem bounce pool size: 64 pages
Aug 13 12:33:00 Ubuntu kernel: [    0.297158] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 13 12:33:00 Ubuntu kernel: [    0.298443] VFS: Disk quotas dquot_6.5.2
Aug 13 12:33:00 Ubuntu kernel: [    0.298490] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 13 12:33:00 Ubuntu kernel: [    0.298968] fuse init (API version 7.13)
Aug 13 12:33:00 Ubuntu kernel: [    0.299040] msgmni has been set to 1690
Aug 13 12:33:00 Ubuntu kernel: [    0.299223] alg: No test for stdrng (krng)
Aug 13 12:33:00 Ubuntu kernel: [    0.299272] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 13 12:33:00 Ubuntu kernel: [    0.299275] io scheduler noop registered
Aug 13 12:33:00 Ubuntu kernel: [    0.299277] io scheduler anticipatory registered
Aug 13 12:33:00 Ubuntu kernel: [    0.299279] io scheduler deadline registered
Aug 13 12:33:00 Ubuntu kernel: [    0.299312] io scheduler cfq registered (default)
Aug 13 12:33:00 Ubuntu kernel: [    0.299622] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 13 12:33:00 Ubuntu kernel: [    0.299643] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 13 12:33:00 Ubuntu kernel: [    0.299732] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug 13 12:33:00 Ubuntu kernel: [    0.299736] ACPI: Power Button [PWRB]
Aug 13 12:33:00 Ubuntu kernel: [    0.299792] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug 13 12:33:00 Ubuntu kernel: [    0.299795] ACPI: Power Button [PWRF]
Aug 13 12:33:00 Ubuntu kernel: [    0.299840] fan PNP0C0B:00: registered as cooling_device0
Aug 13 12:33:00 Ubuntu kernel: [    0.299846] ACPI: Fan [FAN] (on)
Aug 13 12:33:00 Ubuntu kernel: [    0.300225] processor LNXCPU:00: registered as cooling_device1
Aug 13 12:33:00 Ubuntu kernel: [    0.300252] processor LNXCPU:01: registered as cooling_device2
Aug 13 12:33:00 Ubuntu kernel: [    0.304268] thermal LNXTHERM:01: registered as thermal_zone0
Aug 13 12:33:00 Ubuntu kernel: [    0.304275] ACPI: Thermal Zone [THRM] (40 C)
Aug 13 12:33:00 Ubuntu kernel: [    0.305647] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 13 12:33:00 Ubuntu kernel: [    0.305769] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 13 12:33:00 Ubuntu kernel: [    0.306017] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 13 12:33:00 Ubuntu kernel: [    0.306978] brd: module loaded
Aug 13 12:33:00 Ubuntu kernel: [    0.307407] loop: module loaded
Aug 13 12:33:00 Ubuntu kernel: [    0.307492] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Aug 13 12:33:00 Ubuntu kernel: [    0.307970] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Aug 13 12:33:00 Ubuntu kernel: [    0.307986] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Aug 13 12:33:00 Ubuntu kernel: [    0.308032] pata_acpi 0000:00:08.0: PCI INT A disabled
Aug 13 12:33:00 Ubuntu kernel: [    0.308306] Fixed MDIO Bus: probed
Aug 13 12:33:00 Ubuntu kernel: [    0.308336] PPP generic driver version 2.4.2
Aug 13 12:33:00 Ubuntu kernel: [    0.308374] tun: Universal TUN/TAP device driver, 1.6
Aug 13 12:33:00 Ubuntu kernel: [    0.308376] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 13 12:33:00 Ubuntu kernel: [    0.308449] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 13 12:33:00 Ubuntu kernel: [    0.308738] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Aug 13 12:33:00 Ubuntu kernel: [    0.308750] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
Aug 13 12:33:00 Ubuntu kernel: [    0.308766] ehci_hcd 0000:00:02.1: EHCI Host Controller
Aug 13 12:33:00 Ubuntu kernel: [    0.308795] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Aug 13 12:33:00 Ubuntu kernel: [    0.308814] ehci_hcd 0000:00:02.1: debug port 1
Aug 13 12:33:00 Ubuntu kernel: [    0.308840] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
Aug 13 12:33:00 Ubuntu kernel: [    0.308883] isapnp: Scanning for PnP cards...
Aug 13 12:33:00 Ubuntu kernel: [    0.356488] Freeing initrd memory: 7782k freed
Aug 13 12:33:00 Ubuntu kernel: [    0.357730] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Aug 13 12:33:00 Ubuntu kernel: [    0.357815] usb usb1: configuration #1 chosen from 1 choice
Aug 13 12:33:00 Ubuntu kernel: [    0.357844] hub 1-0:1.0: USB hub found
Aug 13 12:33:00 Ubuntu kernel: [    0.357852] hub 1-0:1.0: 8 ports detected
Aug 13 12:33:00 Ubuntu kernel: [    0.357915] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 13 12:33:00 Ubuntu kernel: [    0.358214] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Aug 13 12:33:00 Ubuntu kernel: [    0.358227] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
Aug 13 12:33:00 Ubuntu kernel: [    0.358240] ohci_hcd 0000:00:02.0: OHCI Host Controller
Aug 13 12:33:00 Ubuntu kernel: [    0.358271] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Aug 13 12:33:00 Ubuntu kernel: [    0.358294] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfe02f000
Aug 13 12:33:00 Ubuntu kernel: [    0.415135] usb usb2: configuration #1 chosen from 1 choice
Aug 13 12:33:00 Ubuntu kernel: [    0.415163] hub 2-0:1.0: USB hub found
Aug 13 12:33:00 Ubuntu kernel: [    0.415175] hub 2-0:1.0: 8 ports detected
Aug 13 12:33:00 Ubuntu kernel: [    0.415232] uhci_hcd: USB Universal Host Controller Interface driver
Aug 13 12:33:00 Ubuntu kernel: [    0.415317] PNP: No PS/2 controller found. Probing ports directly.
Aug 13 12:33:00 Ubuntu kernel: [    0.415726] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 13 12:33:00 Ubuntu kernel: [    0.415732] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 13 12:33:00 Ubuntu kernel: [    0.415797] mice: PS/2 mouse device common for all mice
Aug 13 12:33:00 Ubuntu kernel: [    0.415885] rtc_cmos 00:05: RTC can wake from S4
Aug 13 12:33:00 Ubuntu kernel: [    0.415922] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug 13 12:33:00 Ubuntu kernel: [    0.415959] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Aug 13 12:33:00 Ubuntu kernel: [    0.416045] device-mapper: uevent: version 1.0.3
Aug 13 12:33:00 Ubuntu kernel: [    0.416145] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug 13 12:33:00 Ubuntu kernel: [    0.416204] device-mapper: multipath: version 1.1.0 loaded
Aug 13 12:33:00 Ubuntu kernel: [    0.416207] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 13 12:33:00 Ubuntu kernel: [    0.416304] EISA: Probing bus 0 at eisa.0
Aug 13 12:33:00 Ubuntu kernel: [    0.416309] Cannot allocate resource for EISA slot 1
Aug 13 12:33:00 Ubuntu kernel: [    0.416327] EISA: Detected 0 cards.
Aug 13 12:33:00 Ubuntu kernel: [    0.416391] cpuidle: using governor ladder
Aug 13 12:33:00 Ubuntu kernel: [    0.416393] cpuidle: using governor menu
Aug 13 12:33:00 Ubuntu kernel: [    0.416772] TCP cubic registered
Aug 13 12:33:00 Ubuntu kernel: [    0.416897] NET: Registered protocol family 10
Aug 13 12:33:00 Ubuntu kernel: [    0.417295] lo: Disabled Privacy Extensions
Aug 13 12:33:00 Ubuntu kernel: [    0.417566] NET: Registered protocol family 17
Aug 13 12:33:00 Ubuntu kernel: [    0.417594] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (2 cpu cores) (version 2.20.00)
Aug 13 12:33:00 Ubuntu kernel: [    0.417637] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0xc
Aug 13 12:33:00 Ubuntu kernel: [    0.417639] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xe
Aug 13 12:33:00 Ubuntu kernel: [    0.417641] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x10
Aug 13 12:33:00 Ubuntu kernel: [    0.417643] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x10
Aug 13 12:33:00 Ubuntu kernel: [    0.417646] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
Aug 13 12:33:00 Ubuntu kernel: [    0.445115] Using IPI No-Shortcut mode
Aug 13 12:33:00 Ubuntu kernel: [    0.445189] registered taskstats version 1
Aug 13 12:33:00 Ubuntu kernel: [    0.445430]   Magic number: 6:525:527
Aug 13 12:33:00 Ubuntu kernel: [    0.445517] rtc_cmos 00:05: setting system clock to 2010-08-13 10:32:46 UTC (1281695566)
Aug 13 12:33:00 Ubuntu kernel: [    0.445521] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 13 12:33:00 Ubuntu kernel: [    0.445522] EDD information not available.
Aug 13 12:33:00 Ubuntu kernel: [    0.662149] isapnp: No Plug & Play device found
Aug 13 12:33:00 Ubuntu kernel: [    0.662167] Freeing unused kernel memory: 660k freed
Aug 13 12:33:00 Ubuntu kernel: [    0.662572] Write protecting the kernel text: 4680k
Aug 13 12:33:00 Ubuntu kernel: [    0.662605] Write protecting the kernel read-only data: 1840k
Aug 13 12:33:00 Ubuntu kernel: [    0.678734] udev: starting version 151
Aug 13 12:33:00 Ubuntu kernel: [    0.684053] usb 1-1: new high speed USB device using ehci_hcd and address 2
Aug 13 12:33:00 Ubuntu kernel: [    0.747810] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Aug 13 12:33:00 Ubuntu kernel: [    0.769681] scsi0 : sata_nv
Aug 13 12:33:00 Ubuntu kernel: [    0.784806] scsi1 : sata_nv
Aug 13 12:33:00 Ubuntu kernel: [    0.785008] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 20
Aug 13 12:33:00 Ubuntu kernel: [    0.785011] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 20
Aug 13 12:33:00 Ubuntu kernel: [    0.787454] scsi2 : pata_amd
Aug 13 12:33:00 Ubuntu kernel: [    0.788526] scsi3 : pata_amd
Aug 13 12:33:00 Ubuntu kernel: [    0.789219] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Aug 13 12:33:00 Ubuntu kernel: [    0.789222] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Aug 13 12:33:00 Ubuntu kernel: [    0.816696] usb 1-1: configuration #1 chosen from 1 choice
Aug 13 12:33:00 Ubuntu kernel: [    0.816778] hub 1-1:1.0: USB hub found
Aug 13 12:33:00 Ubuntu kernel: [    0.816862] hub 1-1:1.0: 4 ports detected
Aug 13 12:33:00 Ubuntu kernel: [    1.016321] ata3.00: ATAPI: _NEC DVD_RW ND-4570A, 1.02, max UDMA/33
Aug 13 12:33:00 Ubuntu kernel: [    1.016717] ata3.01: ATA-6: ST3160023A, 8.16, max UDMA/100
Aug 13 12:33:00 Ubuntu kernel: [    1.016720] ata3.01: 312581808 sectors, multi 16: LBA48 
Aug 13 12:33:00 Ubuntu kernel: [    1.032276] ata3.00: configured for UDMA/33
Aug 13 12:33:00 Ubuntu kernel: [    1.048406] ata3.01: configured for UDMA/100
Aug 13 12:33:00 Ubuntu kernel: [    1.176014] usb 2-2: new low speed USB device using ohci_hcd and address 2
Aug 13 12:33:00 Ubuntu kernel: [    1.252032] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 13 12:33:00 Ubuntu kernel: [    1.260210] ata1.00: ATA-7: WDC WD1600JS-55MHB0, 02.01C03, max UDMA/133
Aug 13 12:33:00 Ubuntu kernel: [    1.260213] ata1.00: 312581808 sectors, multi 16: LBA48 
Aug 13 12:33:00 Ubuntu kernel: [    1.268226] ata1.00: configured for UDMA/133
Aug 13 12:33:00 Ubuntu kernel: [    1.268323] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-55M 02.0 PQ: 0 ANSI: 5
Aug 13 12:33:00 Ubuntu kernel: [    1.268469] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 13 12:33:00 Ubuntu kernel: [    1.268572] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug 13 12:33:00 Ubuntu kernel: [    1.268609] sd 0:0:0:0: [sda] Write Protect is off
Aug 13 12:33:00 Ubuntu kernel: [    1.268630] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 13 12:33:00 Ubuntu kernel: [    1.268755]  sda: sda1
Aug 13 12:33:00 Ubuntu kernel: [    1.272954] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 13 12:33:00 Ubuntu kernel: [    1.390100] usb 2-2: configuration #1 chosen from 1 choice
Aug 13 12:33:00 Ubuntu kernel: [    1.402928] usbcore: registered new interface driver hiddev
Aug 13 12:33:00 Ubuntu kernel: [    1.409276] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
Aug 13 12:33:00 Ubuntu kernel: [    1.409352] generic-usb 0003:03F0:0F0C.0001: input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:02.0-2/input0
Aug 13 12:33:00 Ubuntu kernel: [    1.419489] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input4
Aug 13 12:33:00 Ubuntu kernel: [    1.419683] generic-usb 0003:03F0:0F0C.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:02.0-2/input1
Aug 13 12:33:00 Ubuntu kernel: [    1.419701] usbcore: registered new interface driver usbhid
Aug 13 12:33:00 Ubuntu kernel: [    1.419704] usbhid: v2.6:USB HID core driver
Aug 13 12:33:00 Ubuntu kernel: [    1.464121] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
Aug 13 12:33:00 Ubuntu kernel: [    1.556672] usb 1-1.2: configuration #1 chosen from 1 choice
Aug 13 12:33:00 Ubuntu kernel: [    1.556790] hub 1-1.2:1.0: USB hub found
Aug 13 12:33:00 Ubuntu kernel: [    1.556868] hub 1-1.2:1.0: 4 ports detected
Aug 13 12:33:00 Ubuntu kernel: [    1.590231] ata2: SATA link down (SStatus 0 SControl 300)
Aug 13 12:33:00 Ubuntu kernel: [    1.591359] scsi 2:0:0:0: CD-ROM            _NEC     DVD_RW ND-4570A  1.02 PQ: 0 ANSI: 5
Aug 13 12:33:00 Ubuntu kernel: [    1.594183] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 13 12:33:00 Ubuntu kernel: [    1.594186] Uniform CD-ROM driver Revision: 3.20
Aug 13 12:33:00 Ubuntu kernel: [    1.594338] sr 2:0:0:0: Attached scsi generic sg1 type 5
Aug 13 12:33:00 Ubuntu kernel: [    1.594493] scsi 2:0:1:0: Direct-Access     ATA      ST3160023A       8.16 PQ: 0 ANSI: 5
Aug 13 12:33:00 Ubuntu kernel: [    1.594597] sd 2:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug 13 12:33:00 Ubuntu kernel: [    1.594635] sd 2:0:1:0: [sdb] Write Protect is off
Aug 13 12:33:00 Ubuntu kernel: [    1.594657] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 13 12:33:00 Ubuntu kernel: [    1.594760]  sdb:
Aug 13 12:33:00 Ubuntu kernel: [    1.594867] sd 2:0:1:0: Attached scsi generic sg2 type 0
Aug 13 12:33:00 Ubuntu kernel: [    1.601947]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
Aug 13 12:33:00 Ubuntu kernel: [    1.628453] sd 2:0:1:0: [sdb] Attached SCSI disk
Aug 13 12:33:00 Ubuntu kernel: [    1.631452] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Aug 13 12:33:00 Ubuntu kernel: [    1.631468] ohci1394 0000:01:07.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Aug 13 12:33:00 Ubuntu kernel: [    1.690034] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 13 12:33:00 Ubuntu kernel: [    1.695085] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug 13 12:33:00 Ubuntu kernel: [    1.695401] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Aug 13 12:33:00 Ubuntu kernel: [    1.695417] r8169 0000:01:09.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Aug 13 12:33:00 Ubuntu kernel: [    1.695445] r8169 0000:01:09.0: no PCI Express capability
Aug 13 12:33:00 Ubuntu kernel: [    1.695992] eth0: RTL8169sb/8110sb at 0xf8180000, 00:06:4f:76:bd:32, XID 10000000 IRQ 18
[COLOR="Red"]Aug 13 12:33:00 Ubuntu kernel: [    1.981258] EXT4-fs (sdb5): mounted filesystem with ordered data mode
Aug 13 12:33:00 Ubuntu kernel: [   12.994922] Adding 3998712k swap on /dev/sdb6.  Priority:-1 extents:1 across:3998712k 
[/COLOR]Aug 13 12:33:00 Ubuntu kernel: [   13.014932] udev: starting version 151
Aug 13 12:33:00 Ubuntu kernel: [   13.060823] ACPI: resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
Aug 13 12:33:00 Ubuntu kernel: [   13.060827] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Aug 13 12:33:00 Ubuntu kernel: [   13.061108] i2c i2c-0: nForce2 SMBus adapter at 0x1c40
Aug 13 12:33:00 Ubuntu kernel: [   13.095706] lp: driver loaded but no devices found
```

Any help truly appreciated:)

Greetz,

J@n

---

### Post by philinux on 2010-08-13
If the machines have NO floppy drive then disable it it the bios.

Check the General Help forum Sticky, although a fix may have been released for this. I'm not sure.

---

### Post by J@n on 2010-08-14
Hi Philinux,

Thanks for your interest:)

I checked the BIOS and the floppy was already disabled on both machines.

I suspect EXT4 being the reason of the delay. But I am too big a noob to have the answer. Searched quite some time on this forum but have not found a solution yet.

Hope you can help some more!

Edit: Read the sticky but could not find anything related to my problems:(

Greetz,

J@n

---

