---
title: "Random freezing in 9.10 karmic"
date: 2009-11-01
forum: General Help
---

### Post by Andreas1 on 2009-11-01
hi, i am quite lost here and i need your help:

i keep getting random freezes since i installed 9.10 karmic koala. these freezes start off partially, with typically one application becoming unresponsive, then extending (compiz, gnome panel) until the whole desktop is frozen. i use alt + print + (r,e,i,s,u,b) to bring the system down.

that mentioned application to become unresponsive at first can be, as far as i have seen, any, including gnome-terminal, firefox, hydrogen

as to when this happens, there are two patterns, i think:
-it only happens after having resumed from suspend at least once in that session, never after a fresh reboot. can be an hour after resuming though, not necessarily directly after.
-it happens while i am interacting with the computer, upon input, but i am not sure about that, maybe that is just when i notice.

i had one suspect for a moment, because the only extra program in my autostart is mail-notification, and i remembered it hogging 100%cpu after resume from suspend on a few occasions in jaunty, but i just experienced the first freeze after disabling it, so i guess that was not it.

so, how do i proceed, which log files do i read, what do i do?

---

### Post by philippe_carlo on 2009-11-01
Can you post the contents of your /var/log/syslog right after a freeze?

---

### Post by DeMus on 2009-11-01
Try running for a while without Compiz just as a test to see if that is causing the problems you have.
It wouldn't be the first time Compiz is causing this.

---

### Post by Andreas1 on 2009-11-01
> **philippe_carlo said:**
> Can you post the contents of your /var/log/syslog right after a freeze?

this is out of syslog.1, this time, untypically, the freeze happened directly upon resume, just black screen instead of unlock prompt.
i searched for the suspend event and included everything in syslog.1 from then.

```
Nov  1 07:43:56 aspire kernel: [  116.889154] PM: Syncing filesystems ... done.
Nov  1 07:43:56 aspire kernel: [  116.891425] PM: Preparing system for mem sleep
Nov  1 07:43:56 aspire kernel: [  116.891430] Freezing user space processes ... (elapsed 0.00 seconds) done.
Nov  1 07:43:56 aspire kernel: [  116.892384] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov  1 07:43:56 aspire kernel: [  116.892436] PM: Entering mem sleep
Nov  1 07:43:56 aspire kernel: [  116.892452] Suspending console(s) (use no_console_suspend to debug)
Nov  1 07:43:56 aspire kernel: [  117.196141] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  1 07:43:56 aspire kernel: [  117.196360] sd 0:0:0:0: [sda] Stopping disk
Nov  1 07:43:56 aspire kernel: [  119.716381] ACPI handle has no context!
Nov  1 07:43:56 aspire kernel: [  119.716498] ACPI handle has no context!
Nov  1 07:43:56 aspire kernel: [  119.716506] sdhci-pci 0000:06:04.4: PME# disabled
Nov  1 07:43:56 aspire kernel: [  119.716513] sdhci-pci 0000:06:04.4: PCI INT B disabled
Nov  1 07:43:56 aspire kernel: [  119.716521] ACPI handle has no context!
Nov  1 07:43:56 aspire kernel: [  119.732196] ACPI handle has no context!
Nov  1 07:43:56 aspire kernel: [  119.732206] sdhci-pci 0000:06:04.2: PME# disabled
Nov  1 07:43:56 aspire kernel: [  119.732215] sdhci-pci 0000:06:04.2: PCI INT B disabled
Nov  1 07:43:56 aspire kernel: [  119.732226] ACPI handle has no context!
Nov  1 07:43:56 aspire kernel: [  119.748184] b44 0000:06:01.0: PCI INT A disabled
Nov  1 07:43:56 aspire kernel: [  119.780225] ata2: port disabled. ignoring.
Nov  1 07:43:56 aspire kernel: [  119.780315] ata_piix 0000:00:1f.1: PCI INT B disabled
Nov  1 07:43:56 aspire kernel: [  119.780334] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Nov  1 07:43:56 aspire kernel: [  119.780348] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Nov  1 07:43:56 aspire kernel: [  119.780360] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Nov  1 07:43:56 aspire kernel: [  119.780374] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Nov  1 07:43:56 aspire kernel: [  119.780386] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Nov  1 07:43:56 aspire kernel: [  119.884178] HDA Intel 0000:00:1b.0: PCI INT A disabled
Nov  1 07:43:56 aspire kernel: [  119.930451] i915 0000:00:02.0: PCI INT A disabled
Nov  1 07:43:56 aspire kernel: [  119.945199] PM: suspend devices took 3.052 seconds
Nov  1 07:43:56 aspire kernel: [  119.945653] ehci_hcd 0000:00:1d.7: PME# disabled
Nov  1 07:43:56 aspire kernel: [  119.960740] ACPI: Preparing to enter system sleep state S3
Nov  1 07:43:56 aspire kernel: [  120.003057] Disabling non-boot CPUs ...
Nov  1 07:43:56 aspire kernel:Nov  1 07:45:01 aspire kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov  1 07:45:01 aspire rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="794" x-info="http://www.rsyslog.com"] (re)start
Nov  1 07:45:01 aspire rsyslogd: rsyslogd's groupid changed to 102
Nov  1 07:45:01 aspire rsyslogd: rsyslogd's userid changed to 101
Nov  1 07:45:01 aspire rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Nov  1 07:45:01 aspire kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  1 07:45:01 aspire kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  1 07:45:01 aspire kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Nov  1 07:45:01 aspire kernel: [    0.000000] KERNEL supported cpus:
Nov  1 07:45:01 aspire kernel: [    0.000000]   Intel GenuineIntel
Nov  1 07:45:01 aspire kernel: [    0.000000]   AMD AuthenticAMD
Nov  1 07:45:01 aspire kernel: [    0.000000]   NSC Geode by NSC
Nov  1 07:45:01 aspire kernel: [    0.000000]   Cyrix CyrixInstead
Nov  1 07:45:01 aspire kernel: [    0.000000]   Centaur CentaurHauls
Nov  1 07:45:01 aspire kernel: [    0.000000]   Transmeta GenuineTMx86
Nov  1 07:45:01 aspire kernel: [    0.000000]   Transmeta TransmetaCPU
Nov  1 07:45:01 aspire kernel: [    0.000000]   UMC UMC UMC UMC
Nov  1 07:45:01 aspire kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f680000 (usable)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 000000007f680000 - 000000007f700000 (ACPI NVS)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000] DMI present.
Nov  1 07:45:01 aspire kernel: [    0.000000] last_pfn = 0x7f680 max_arch_pfn = 0x100000
Nov  1 07:45:01 aspire kernel: [    0.000000] MTRR default type: uncachable
Nov  1 07:45:01 aspire kernel: [    0.000000] MTRR fixed ranges enabled:
Nov  1 07:45:01 aspire kernel: [    0.000000]   00000-9FFFF write-back
Nov  1 07:45:01 aspire kernel: [    0.000000]   A0000-BFFFF uncachable
Nov  1 07:45:01 aspire kernel: [    0.000000]   C0000-CFFFF write-protect
Nov  1 07:45:01 aspire kernel: [    0.000000]   D0000-DFFFF uncachable
Nov  1 07:45:01 aspire kernel: [    0.000000]   E0000-FFFFF write-protect
Nov  1 07:45:01 aspire kernel: [    0.000000] MTRR variable ranges enabled:
Nov  1 07:45:01 aspire kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Nov  1 07:45:01 aspire kernel: [    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
Nov  1 07:45:01 aspire kernel: [    0.000000]   2 base 07F800000 mask FFF800000 uncachable
Nov  1 07:45:01 aspire kernel: [    0.000000]   3 disabled
Nov  1 07:45:01 aspire kernel: [    0.000000]   4 disabled
Nov  1 07:45:01 aspire kernel: [    0.000000]   5 disabled
Nov  1 07:45:01 aspire kernel: [    0.000000]   6 disabled
Nov  1 07:45:01 aspire kernel: [    0.000000]   7 disabled
Nov  1 07:45:01 aspire kernel: [    0.000000] PAT not supported by CPU.
Nov  1 07:45:01 aspire kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov  1 07:45:01 aspire kernel: [    0.000000] modified physical RAM map:
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 0000000000100000 - 000000007f680000 (usable)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 000000007f680000 - 000000007f700000 (ACPI NVS)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 000000007f700000 - 0000000080000000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Nov  1 07:45:01 aspire kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Nov  1 07:45:01 aspire kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Nov  1 07:45:01 aspire kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Nov  1 07:45:01 aspire kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Nov  1 07:45:01 aspire kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Nov  1 07:45:01 aspire kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Nov  1 07:45:01 aspire kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Nov  1 07:45:01 aspire kernel: [    0.000000] RAMDISK: 378a5000 - 37fef866
Nov  1 07:45:01 aspire kernel: [    0.000000] Allocated new RAMDISK: 008ad000 - 00ff7866
Nov  1 07:45:01 aspire kernel: [    0.000000] Move RAMDISK from 00000000378a5000 - 0000000037fef865 to 008ad000 - 00ff7865
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: RSDP 000f64e0 00014 (v00 PTLTD )
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: RSDT 7f686010 00048 (v01 PTLTD  Capell00 06040000  LTP 00000000)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: FACP 7f68ce20 00074 (v01 Acer   Grape    06040000 LOHR 0000005A)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: DSDT 7f68708a 05D96 (v01 Acer   CALISTGA 06040000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: FACS 7f68dfc0 00040
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: APIC 7f68ce94 00068 (v01 Acer   Grape    06040000 LOHR 0000005A)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: HPET 7f68cefc 00038 (v01 Acer   Grape    06040000 LOHR 0000005A)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: MCFG 7f68cf34 0003C (v01 Acer   Grape    06040000 LOHR 0000005A)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: APIC 7f68cf70 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: BOOT 7f68cfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: SSDT 7f6865e4 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: SSDT 7f68653e 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: SSDT 7f686058 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  1 07:45:01 aspire kernel: [    0.000000] 1150MB HIGHMEM available.
Nov  1 07:45:01 aspire kernel: [    0.000000] 887MB LOWMEM available.
Nov  1 07:45:01 aspire kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Nov  1 07:45:01 aspire kernel: [    0.000000]   low ram: 0 - 377fe000
Nov  1 07:45:01 aspire kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Nov  1 07:45:01 aspire kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Nov  1 07:45:01 aspire kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #5 [00008a9000 - 00008ac0f9]              BRK ==> [00008a9000 - 00008ac0f9]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #7 [00008ad000 - 0000ff7866]      NEW RAMDISK ==> [00008ad000 - 0000ff7866]
Nov  1 07:45:01 aspire kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Nov  1 07:45:01 aspire kernel: [    0.000000] found SMP MP-table at [c00f6510] f6510
Nov  1 07:45:01 aspire kernel: [    0.000000] Zone PFN ranges:
Nov  1 07:45:01 aspire kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov  1 07:45:01 aspire kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Nov  1 07:45:01 aspire kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f680
Nov  1 07:45:01 aspire kernel: [    0.000000] Movable zone start PFN for each node
Nov  1 07:45:01 aspire kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov  1 07:45:01 aspire kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Nov  1 07:45:01 aspire kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Nov  1 07:45:01 aspire kernel: [    0.000000]     0: 0x00000100 -> 0x0007f680
Nov  1 07:45:01 aspire kernel: [    0.000000] On node 0 totalpages: 521755
Nov  1 07:45:01 aspire kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
Nov  1 07:45:01 aspire kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  1 07:45:01 aspire kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  1 07:45:01 aspire kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Nov  1 07:45:01 aspire kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Nov  1 07:45:01 aspire kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Nov  1 07:45:01 aspire kernel: [    0.000000]   HighMem zone: 2302 pages used for memmap
Nov  1 07:45:01 aspire kernel: [    0.000000]   HighMem zone: 292228 pages, LIFO batch:31
Nov  1 07:45:01 aspire kernel: [    0.000000] Using APIC driver default
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov  1 07:45:01 aspire kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  1 07:45:01 aspire kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  1 07:45:01 aspire kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  1 07:45:01 aspire kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov  1 07:45:01 aspire kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Nov  1 07:45:01 aspire kernel: [    0.000000] nr_irqs_gsi: 24
Nov  1 07:45:01 aspire kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Nov  1 07:45:01 aspire kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  1 07:45:01 aspire kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov  1 07:45:01 aspire kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  1 07:45:01 aspire kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
Nov  1 07:45:01 aspire kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Nov  1 07:45:01 aspire kernel: [    0.000000] PERCPU: Embedded 14 pages at c1ffa000, static data 35612 bytes
Nov  1 07:45:01 aspire kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517677
Nov  1 07:45:01 aspire kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=86add2c8-9d34-42b9-8ac1-70ebf4824e89 ro quiet splash
Nov  1 07:45:01 aspire kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  1 07:45:01 aspire kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  1 07:45:01 aspire kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  1 07:45:01 aspire kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  1 07:45:01 aspire kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  1 07:45:01 aspire kernel: [    0.000000] Initializing CPU#0
Nov  1 07:45:01 aspire kernel: [    0.000000] allocated 10437120 bytes of page_cgroup
Nov  1 07:45:01 aspire kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov  1 07:45:01 aspire kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f680)
Nov  1 07:45:01 aspire kernel: [    0.000000] Memory: 2043276k/2087424k available (4565k kernel code, 42816k reserved, 2143k data, 540k init, 1178120k highmem)
Nov  1 07:45:01 aspire kernel: [    0.000000] virtual kernel memory layout:
Nov  1 07:45:01 aspire kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Nov  1 07:45:01 aspire kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  1 07:45:01 aspire kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Nov  1 07:45:01 aspire kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Nov  1 07:45:01 aspire kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Nov  1 07:45:01 aspire kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Nov  1 07:45:01 aspire kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Nov  1 07:45:01 aspire kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov  1 07:45:01 aspire kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov  1 07:45:01 aspire kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Nov  1 07:45:01 aspire kernel: [    0.000000] Fast TSC calibration using PIT
Nov  1 07:45:01 aspire kernel: [    0.000000] Detected 1595.999 MHz processor.
Nov  1 07:45:01 aspire kernel: [    0.001664] Console: colour VGA+ 80x25
Nov  1 07:45:01 aspire kernel: [    0.001671] console [tty0] enabled
Nov  1 07:45:01 aspire kernel: [    0.001927] hpet clockevent registered
Nov  1 07:45:01 aspire kernel: [    0.001937] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Nov  1 07:45:01 aspire kernel: [    0.001949] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.99 BogoMIPS (lpj=6383996)
Nov  1 07:45:01 aspire kernel: [    0.001987] Security Framework initialized
Nov  1 07:45:01 aspire kernel: [    0.002027] AppArmor: AppArmor initialized
Nov  1 07:45:01 aspire kernel: [    0.002042] Mount-cache hash table entries: 512
Nov  1 07:45:01 aspire kernel: [    0.002300] Initializing cgroup subsys ns
Nov  1 07:45:01 aspire kernel: [    0.002310] Initializing cgroup subsys cpuacct
Nov  1 07:45:01 aspire kernel: [    0.002320] Initializing cgroup subsys memory
Nov  1 07:45:01 aspire kernel: [    0.002334] Initializing cgroup subsys freezer
Nov  1 07:45:01 aspire kernel: [    0.002340] Initializing cgroup subsys net_cls
Nov  1 07:45:01 aspire kernel: [    0.002368] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  1 07:45:01 aspire kernel: [    0.002375] CPU: L2 cache: 2048K
Nov  1 07:45:01 aspire kernel: [    0.002383] CPU: Physical Processor ID: 0
Nov  1 07:45:01 aspire kernel: [    0.002387] CPU: Processor Core ID: 0
Nov  1 07:45:01 aspire kernel: [    0.002396] mce: CPU supports 6 MCE banks
Nov  1 07:45:01 aspire kernel: [    0.002418] CPU0: Thermal monitoring enabled (TM1)
Nov  1 07:45:01 aspire kernel: [    0.002426] using mwait in idle threads.
Nov  1 07:45:01 aspire kernel: [    0.002439] Performance Counters: no PMU driver, software counters only.
Nov  1 07:45:01 aspire kernel: [    0.002450] Checking 'hlt' instruction... OK.
Nov  1 07:45:01 aspire kernel: [    0.020008] ACPI: Core revision 20090521
Nov  1 07:45:01 aspire kernel: [    0.044524] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  1 07:45:01 aspire kernel: [    0.085976] CPU0: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
Nov  1 07:45:01 aspire kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Nov  1 07:45:01 aspire kernel: [    0.004000] Initializing CPU#1
Nov  1 07:45:01 aspire kernel: [    0.004000] Calibrating delay using timer specific routine.. 3192.09 BogoMIPS (lpj=6384182)
Nov  1 07:45:01 aspire kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  1 07:45:01 aspire kernel: [    0.004000] CPU: L2 cache: 2048K
Nov  1 07:45:01 aspire kernel: [    0.004000] CPU: Physical Processor ID: 0
Nov  1 07:45:01 aspire kernel: [    0.004000] CPU: Processor Core ID: 1
Nov  1 07:45:01 aspire kernel: [    0.004000] mce: CPU supports 6 MCE banks
Nov  1 07:45:01 aspire kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM1)
Nov  1 07:45:01 aspire kernel: [    0.172965] CPU1: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
Nov  1 07:45:01 aspire kernel: [    0.172999] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  1 07:45:01 aspire kernel: [    0.176036] Brought up 2 CPUs
Nov  1 07:45:01 aspire kernel: [    0.176044] Total of 2 processors activated (6384.08 BogoMIPS).
Nov  1 07:45:01 aspire kernel: [    0.176119] CPU0 attaching sched-domain:
Nov  1 07:45:01 aspire kernel: [    0.176127]  domain 0: span 0-1 level MC
Nov  1 07:45:01 aspire kernel: [    0.176134]   groups: 0 1
Nov  1 07:45:01 aspire kernel: [    0.176147] CPU1 attaching sched-domain:
Nov  1 07:45:01 aspire kernel: [    0.176153]  domain 0: span 0-1 level MC
Nov  1 07:45:01 aspire kernel: [    0.176159]   groups: 1 0
Nov  1 07:45:01 aspire kernel: [    0.176328] Booting paravirtualized kernel on bare hardware
Nov  1 07:45:01 aspire kernel: [    0.176554] regulator: core version 0.5
Nov  1 07:45:01 aspire kernel: [    0.176554] Time:  7:44:49  Date: 11/01/09
Nov  1 07:45:01 aspire kernel: [    0.176554] NET: Registered protocol family 16
Nov  1 07:45:01 aspire kernel: [    0.176554] EISA bus registered
Nov  1 07:45:01 aspire kernel: [    0.176554] ACPI: bus type pci registered
Nov  1 07:45:01 aspire kernel: [    0.176664] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Nov  1 07:45:01 aspire kernel: [    0.176672] PCI: MCFG area at e0000000 reserved in E820
Nov  1 07:45:01 aspire kernel: [    0.176677] PCI: Using MMCONFIG for extended config space
Nov  1 07:45:01 aspire kernel: [    0.176683] PCI: Using configuration type 1 for base access
Nov  1 07:45:01 aspire kernel: [    0.181650] bio: create slab <bio-0> at 0
Nov  1 07:45:01 aspire kernel: [    0.184254] ACPI: EC: Look up EC in DSDT
Nov  1 07:45:01 aspire kernel: [    0.193418] ACPI: BIOS _OSI(Linux) query ignored
Nov  1 07:45:01 aspire kernel: [    0.195055] ACPI: Interpreter enabled
Nov  1 07:45:01 aspire kernel: [    0.195070] ACPI: (supports S0 S3 S4 S5)
Nov  1 07:45:01 aspire kernel: [    0.195119] ACPI: Using IOAPIC for interrupt routing
Nov  1 07:45:01 aspire kernel: [    0.202622] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  1 07:45:01 aspire kernel: [    0.228183] ACPI: EC: GPE storm detected, transactions will use polling mode
Nov  1 07:45:01 aspire kernel: [    0.728013] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  1 07:45:01 aspire kernel: [    0.758755] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Nov  1 07:45:01 aspire kernel: [    0.758762] ACPI: EC: driver started in poll mode
Nov  1 07:45:01 aspire kernel: [    0.759350] ACPI: No dock devices found.
Nov  1 07:45:01 aspire kernel: [    0.760402] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  1 07:45:01 aspire kernel: [    0.760595] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0200000-0xd027ffff]
Nov  1 07:45:01 aspire kernel: [    0.760609] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
Nov  1 07:45:01 aspire kernel: [    0.760621] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
Nov  1 07:45:01 aspire kernel: [    0.760634] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd0300000-0xd033ffff]
Nov  1 07:45:01 aspire kernel: [    0.760718] pci 0000:00:02.1: reg 10 32bit mmio: [0xd0280000-0xd02fffff]
Nov  1 07:45:01 aspire kernel: [    0.760907] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd0340000-0xd0343fff]
Nov  1 07:45:01 aspire kernel: [    0.760999] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.761009] pci 0000:00:1b.0: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.761138] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.761148] pci 0000:00:1c.0: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.761280] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.761291] pci 0000:00:1c.1: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.761423] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.761433] pci 0000:00:1c.2: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.761567] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.761577] pci 0000:00:1c.3: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.761677] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
Nov  1 07:45:01 aspire kernel: [    0.761775] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
Nov  1 07:45:01 aspire kernel: [    0.761873] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
Nov  1 07:45:01 aspire kernel: [    0.761971] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
Nov  1 07:45:01 aspire kernel: [    0.762076] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0544000-0xd05443ff]
Nov  1 07:45:01 aspire kernel: [    0.762170] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.762181] pci 0000:00:1d.7: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.762424] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Nov  1 07:45:01 aspire kernel: [    0.762434] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Nov  1 07:45:01 aspire kernel: [    0.762444] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0230 (mask 000f)
Nov  1 07:45:01 aspire kernel: [    0.762454] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff20 (mask 000f)
Nov  1 07:45:01 aspire kernel: [    0.762537] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Nov  1 07:45:01 aspire kernel: [    0.762552] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Nov  1 07:45:01 aspire kernel: [    0.762567] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Nov  1 07:45:01 aspire kernel: [    0.762582] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Nov  1 07:45:01 aspire kernel: [    0.762597] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
Nov  1 07:45:01 aspire kernel: [    0.762713] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]
Nov  1 07:45:01 aspire kernel: [    0.762852] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
Nov  1 07:45:01 aspire kernel: [    0.762862] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
Nov  1 07:45:01 aspire kernel: [    0.763238] pci 0000:05:00.0: reg 10 32bit mmio: [0xd0100000-0xd0100fff]
Nov  1 07:45:01 aspire kernel: [    0.763515] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.763533] pci 0000:05:00.0: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.763685] pci 0000:00:1c.3: bridge 32bit mmio: [0xd0100000-0xd01fffff]
Nov  1 07:45:01 aspire kernel: [    0.763762] pci 0000:06:01.0: reg 10 32bit mmio: [0xd0000000-0xd0001fff]
Nov  1 07:45:01 aspire kernel: [    0.763847] pci 0000:06:01.0: supports D1 D2
Nov  1 07:45:01 aspire kernel: [    0.763853] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.763864] pci 0000:06:01.0: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.763939] pci 0000:06:04.0: reg 10 32bit mmio: [0xd0002000-0xd0002fff]
Nov  1 07:45:01 aspire kernel: [    0.763980] pci 0000:06:04.0: supports D1 D2
Nov  1 07:45:01 aspire kernel: [    0.763987] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  1 07:45:01 aspire kernel: [    0.764009] pci 0000:06:04.0: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.764082] pci 0000:06:04.1: reg 10 32bit mmio: [0xd0003000-0xd000307f]
Nov  1 07:45:01 aspire kernel: [    0.764180] pci 0000:06:04.1: supports D1 D2
Nov  1 07:45:01 aspire kernel: [    0.764186] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
Nov  1 07:45:01 aspire kernel: [    0.764197] pci 0000:06:04.1: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.764268] pci 0000:06:04.2: reg 10 32bit mmio: [0xd0003400-0xd00034ff]
Nov  1 07:45:01 aspire kernel: [    0.764366] pci 0000:06:04.2: supports D1 D2
Nov  1 07:45:01 aspire kernel: [    0.764372] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
Nov  1 07:45:01 aspire kernel: [    0.764383] pci 0000:06:04.2: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.764454] pci 0000:06:04.3: reg 10 32bit mmio: [0xd0003800-0xd000387f]
Nov  1 07:45:01 aspire kernel: [    0.764552] pci 0000:06:04.3: supports D1 D2
Nov  1 07:45:01 aspire kernel: [    0.764558] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
Nov  1 07:45:01 aspire kernel: [    0.764569] pci 0000:06:04.3: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.764640] pci 0000:06:04.4: reg 10 32bit mmio: [0x000000-0x0000ff]
Nov  1 07:45:01 aspire kernel: [    0.764738] pci 0000:06:04.4: supports D1 D2
Nov  1 07:45:01 aspire kernel: [    0.764744] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
Nov  1 07:45:01 aspire kernel: [    0.764754] pci 0000:06:04.4: PME# disabled
Nov  1 07:45:01 aspire kernel: [    0.764843] pci 0000:00:1e.0: transparent bridge
Nov  1 07:45:01 aspire kernel: [    0.764858] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd00fffff]
Nov  1 07:45:01 aspire kernel: [    0.764948] pci_bus 0000:00: on NUMA node 0
Nov  1 07:45:01 aspire kernel: [    0.764959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  1 07:45:01 aspire kernel: [    0.765462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Nov  1 07:45:01 aspire kernel: [    0.765647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Nov  1 07:45:01 aspire kernel: [    0.765826] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Nov  1 07:45:01 aspire kernel: [    0.766005] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Nov  1 07:45:01 aspire kernel: [    0.766247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Nov  1 07:45:01 aspire kernel: [    0.774584] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 5 *6 10 12 14 15)
Nov  1 07:45:01 aspire kernel: [    0.774823] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 5 6 *11 12 14 15)
Nov  1 07:45:01 aspire kernel: [    0.775057] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 5 6 10 12 14 15) *11
Nov  1 07:45:01 aspire kernel: [    0.775293] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 5 6 11 12 14 15) *10
Nov  1 07:45:01 aspire kernel: [    0.775529] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 10 12 14 15) *0, disabled.
Nov  1 07:45:01 aspire kernel: [    0.775775] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 5 6 11 12 14 15) *10
Nov  1 07:45:01 aspire kernel: [    0.776024] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 5 6 *10 12 14 15)
Nov  1 07:45:01 aspire kernel: [    0.776262] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *5 6 11 12 14 15)
Nov  1 07:45:01 aspire kernel: [    0.776697] SCSI subsystem initialized
Nov  1 07:45:01 aspire kernel: [    0.776746] libata version 3.00 loaded.
Nov  1 07:45:01 aspire kernel: [    0.776746] usbcore: registered new interface driver usbfs
Nov  1 07:45:01 aspire kernel: [    0.776746] usbcore: registered new interface driver hub
Nov  1 07:45:01 aspire kernel: [    0.776746] usbcore: registered new device driver usb
Nov  1 07:45:01 aspire kernel: [    0.776746] ACPI: WMI: Mapper loaded
Nov  1 07:45:01 aspire kernel: [    0.776746] PCI: Using ACPI for IRQ routing
Nov  1 07:45:01 aspire kernel: [    0.776746] pci 0000:00:1c.0: BAR 13: can't allocate resource
Nov  1 07:45:01 aspire kernel: [    0.776746] pci 0000:00:1c.0: BAR 14: can't allocate resource
Nov  1 07:45:01 aspire kernel: [    0.788020] Bluetooth: Core ver 2.15
Nov  1 07:45:01 aspire kernel: [    0.788057] NET: Registered protocol family 31
Nov  1 07:45:01 aspire kernel: [    0.788057] Bluetooth: HCI device and connection manager initialized
Nov  1 07:45:01 aspire kernel: [    0.788057] Bluetooth: HCI socket layer initialized
Nov  1 07:45:01 aspire kernel: [    0.788057] NetLabel: Initializing
Nov  1 07:45:01 aspire kernel: [    0.788057] NetLabel:  domain hash size = 128
Nov  1 07:45:01 aspire kernel: [    0.788057] NetLabel:  protocols = UNLABELED CIPSOv4
Nov  1 07:45:01 aspire kernel: [    0.788093] NetLabel:  unlabeled traffic allowed by default
Nov  1 07:45:01 aspire kernel: [    0.788165] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov  1 07:45:01 aspire kernel: [    0.788179] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Nov  1 07:45:01 aspire kernel: [    0.796029] Switched to high resolution mode on CPU 0
Nov  1 07:45:01 aspire kernel: [    0.797051] Switched to high resolution mode on CPU 1
Nov  1 07:45:01 aspire kernel: [    0.808025] pnp: PnP ACPI init
Nov  1 07:45:01 aspire kernel: [    0.808050] ACPI: bus type pnp registered
Nov  1 07:45:01 aspire kernel: [    0.885702] pnp: PnP ACPI: found 10 devices
Nov  1 07:45:01 aspire kernel: [    0.885709] ACPI: ACPI bus type pnp unregistered
Nov  1 07:45:01 aspire kernel: [    0.885716] PnPBIOS: Disabled by ACPI PNP
Nov  1 07:45:01 aspire kernel: [    0.885741] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885749] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885758] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885767] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885775] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885784] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885802] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885819] system 00:06: ioport range 0x800-0x80f has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885828] system 00:06: ioport range 0x1000-0x107f has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885836] system 00:06: ioport range 0x1180-0x11bf has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885844] system 00:06: ioport range 0x1640-0x164f has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885853] system 00:06: ioport range 0xfe00-0xfefe has been reserved
Nov  1 07:45:01 aspire kernel: [    0.885861] system 00:06: ioport range 0xff2c-0xff2f has been reserved
Nov  1 07:45:01 aspire kernel: [    0.920757] AppArmor: AppArmor Filesystem Enabled
Nov  1 07:45:01 aspire kernel: [    0.920892] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Nov  1 07:45:01 aspire kernel: [    0.920898] pci 0000:00:1c.0:   IO window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920910] pci 0000:00:1c.0:   MEM window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920919] pci 0000:00:1c.0:   PREFETCH window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920929] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Nov  1 07:45:01 aspire kernel: [    0.920935] pci 0000:00:1c.1:   IO window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920946] pci 0000:00:1c.1:   MEM window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920955] pci 0000:00:1c.1:   PREFETCH window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920965] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Nov  1 07:45:01 aspire kernel: [    0.920971] pci 0000:00:1c.2:   IO window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920981] pci 0000:00:1c.2:   MEM window: disabled
Nov  1 07:45:01 aspire kernel: [    0.920991] pci 0000:00:1c.2:   PREFETCH window: disabled
Nov  1 07:45:01 aspire kernel: [    0.921001] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
Nov  1 07:45:01 aspire kernel: [    0.921007] pci 0000:00:1c.3:   IO window: disabled
Nov  1 07:45:01 aspire kernel: [    0.921019] pci 0000:00:1c.3:   MEM window: 0xd0100000-0xd01fffff
Nov  1 07:45:01 aspire kernel: [    0.921029] pci 0000:00:1c.3:   PREFETCH window: disabled
Nov  1 07:45:01 aspire kernel: [    0.921052] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
Nov  1 07:45:01 aspire kernel: [    0.921059] pci 0000:06:04.0:   IO window: 0x002000-0x0020ff
Nov  1 07:45:01 aspire kernel: [    0.921071] pci 0000:06:04.0:   IO window: 0x002400-0x0024ff
Nov  1 07:45:01 aspire kernel: [    0.921082] pci 0000:06:04.0:   PREFETCH window: 0x80000000-0x83ffffff
Nov  1 07:45:01 aspire kernel: [    0.921094] pci 0000:06:04.0:   MEM window: 0x84000000-0x87ffffff
Nov  1 07:45:01 aspire kernel: [    0.921106] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
Nov  1 07:45:01 aspire kernel: [    0.921114] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
Nov  1 07:45:01 aspire kernel: [    0.921127] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Nov  1 07:45:01 aspire kernel: [    0.921138] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
Nov  1 07:45:01 aspire kernel: [    0.921163]   alloc irq_desc for 17 on node -1
Nov  1 07:45:01 aspire kernel: [    0.921168]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    0.921181] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov  1 07:45:01 aspire kernel: [    0.921194] pci 0000:00:1c.0: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    0.921210]   alloc irq_desc for 16 on node -1
Nov  1 07:45:01 aspire kernel: [    0.921215]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    0.921224] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Nov  1 07:45:01 aspire kernel: [    0.921235] pci 0000:00:1c.1: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    0.921250]   alloc irq_desc for 18 on node -1
Nov  1 07:45:01 aspire kernel: [    0.921255]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    0.921265] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  1 07:45:01 aspire kernel: [    0.921275] pci 0000:00:1c.2: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    0.921290]   alloc irq_desc for 19 on node -1
Nov  1 07:45:01 aspire kernel: [    0.921295]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    0.921304] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov  1 07:45:01 aspire kernel: [    0.921315] pci 0000:00:1c.3: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    0.921327] pci 0000:00:1e.0: enabling device (0004 -> 0007)
Nov  1 07:45:01 aspire kernel: [    0.921339] pci 0000:00:1e.0: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    0.921358] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  1 07:45:01 aspire kernel: [    0.921372] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Nov  1 07:45:01 aspire kernel: [    0.921380] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Nov  1 07:45:01 aspire kernel: [    0.921387] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
Nov  1 07:45:01 aspire kernel: [    0.921394] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
Nov  1 07:45:01 aspire kernel: [    0.921403] pci_bus 0000:05: resource 1 mem: [0xd0100000-0xd01fffff]
Nov  1 07:45:01 aspire kernel: [    0.921410] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
Nov  1 07:45:01 aspire kernel: [    0.921418] pci_bus 0000:06: resource 1 mem: [0xd0000000-0xd00fffff]
Nov  1 07:45:01 aspire kernel: [    0.921425] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x83ffffff]
Nov  1 07:45:01 aspire kernel: [    0.921433] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
Nov  1 07:45:01 aspire kernel: [    0.921440] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
Nov  1 07:45:01 aspire kernel: [    0.921448] pci_bus 0000:07: resource 0 io:  [0x2000-0x20ff]
Nov  1 07:45:01 aspire kernel: [    0.921455] pci_bus 0000:07: resource 1 io:  [0x2400-0x24ff]
Nov  1 07:45:01 aspire kernel: [    0.921462] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
Nov  1 07:45:01 aspire kernel: [    0.921470] pci_bus 0000:07: resource 3 mem: [0x84000000-0x87ffffff]
Nov  1 07:45:01 aspire kernel: [    0.921548] NET: Registered protocol family 2
Nov  1 07:45:01 aspire kernel: [    0.921776] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  1 07:45:01 aspire kernel: [    0.922488] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov  1 07:45:01 aspire kernel: [    0.924088] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  1 07:45:01 aspire kernel: [    0.924865] TCP: Hash tables configured (established 131072 bind 65536)
Nov  1 07:45:01 aspire kernel: [    0.924872] TCP reno registered
Nov  1 07:45:01 aspire kernel: [    0.925055] NET: Registered protocol family 1
Nov  1 07:45:01 aspire kernel: [    0.925196] Trying to unpack rootfs image as initramfs...
Nov  1 07:45:01 aspire kernel: [    1.427720] Freeing initrd memory: 7466k freed
Nov  1 07:45:01 aspire kernel: [    1.434110] Simple Boot Flag at 0x36 set to 0x1
Nov  1 07:45:01 aspire kernel: [    1.434542] cpufreq-nforce2: No nForce2 chipset.
Nov  1 07:45:01 aspire kernel: [    1.434608] Scanning for low memory corruption every 60 seconds
Nov  1 07:45:01 aspire kernel: [    1.434842] audit: initializing netlink socket (disabled)
Nov  1 07:45:01 aspire kernel: [    1.434871] type=2000 audit(1257061490.432:1): initialized
Nov  1 07:45:01 aspire kernel: [    1.456770] highmem bounce pool size: 64 pages
Nov  1 07:45:01 aspire kernel: [    1.456783] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov  1 07:45:01 aspire kernel: [    1.460829] VFS: Disk quotas dquot_6.5.2
Nov  1 07:45:01 aspire kernel: [    1.460984] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  1 07:45:01 aspire kernel: [    1.462449] fuse init (API version 7.12)
Nov  1 07:45:01 aspire kernel: [    1.462665] msgmni has been set to 1706
Nov  1 07:45:01 aspire kernel: [    1.463186] alg: No test for stdrng (krng)
Nov  1 07:45:01 aspire kernel: [    1.463214] io scheduler noop registered
Nov  1 07:45:01 aspire kernel: [    1.463220] io scheduler anticipatory registered
Nov  1 07:45:01 aspire kernel: [    1.463226] io scheduler deadline registered
Nov  1 07:45:01 aspire kernel: [    1.463335] io scheduler cfq registered (default)
Nov  1 07:45:01 aspire kernel: [    1.463360] pci 0000:00:02.0: Boot video device
Nov  1 07:45:01 aspire kernel: [    1.463802]   alloc irq_desc for 24 on node -1
Nov  1 07:45:01 aspire kernel: [    1.463808]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    1.463829] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
Nov  1 07:45:01 aspire kernel: [    1.463849] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    1.464139]   alloc irq_desc for 25 on node -1
Nov  1 07:45:01 aspire kernel: [    1.464145]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    1.464162] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
Nov  1 07:45:01 aspire kernel: [    1.464180] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    1.464453]   alloc irq_desc for 26 on node -1
Nov  1 07:45:01 aspire kernel: [    1.464459]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    1.464475] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
Nov  1 07:45:01 aspire kernel: [    1.464493] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    1.464750]   alloc irq_desc for 27 on node -1
Nov  1 07:45:01 aspire kernel: [    1.464756]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    1.464772] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
Nov  1 07:45:01 aspire kernel: [    1.464790] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    1.465000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  1 07:45:01 aspire kernel: [    1.465302] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov  1 07:45:01 aspire kernel: [    1.520144] ACPI: AC Adapter [ACAD] (on-line)
Nov  1 07:45:01 aspire kernel: [    1.520297] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Nov  1 07:45:01 aspire kernel: [    1.520306] ACPI: Power Button [PWRF]
Nov  1 07:45:01 aspire kernel: [    1.520433] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Nov  1 07:45:01 aspire kernel: [    1.520520] ACPI: Lid Switch [LID]
Nov  1 07:45:01 aspire kernel: [    1.520636] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Nov  1 07:45:01 aspire kernel: [    1.520644] ACPI: Sleep Button [SLPB]
Nov  1 07:45:01 aspire kernel: [    1.520755] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov  1 07:45:01 aspire kernel: [    1.520763] ACPI: Power Button [PWRB]
Nov  1 07:45:01 aspire kernel: [    1.522289] ACPI: SSDT 7f686d8a 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    1.523458] ACPI: SSDT 7f686843 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    1.529015] Marking TSC unstable due to TSC halts in idle
Nov  1 07:45:01 aspire kernel: [    1.529056] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Nov  1 07:45:01 aspire kernel: [    1.529119] processor LNXCPU:00: registered as cooling_device0
Nov  1 07:45:01 aspire kernel: [    1.529130] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov  1 07:45:01 aspire kernel: [    1.529964] ACPI: SSDT 7f686fc2 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    1.530833] ACPI: SSDT 7f686d05 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
Nov  1 07:45:01 aspire kernel: [    1.532552] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Nov  1 07:45:01 aspire kernel: [    1.532614] processor LNXCPU:01: registered as cooling_device1
Nov  1 07:45:01 aspire kernel: [    1.532625] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov  1 07:45:01 aspire kernel: [    1.720132] thermal LNXTHERM:01: registered as thermal_zone0
Nov  1 07:45:01 aspire kernel: [    1.720154] ACPI: Thermal Zone [TZ00] (34 C)
Nov  1 07:45:01 aspire kernel: [    1.832134] thermal LNXTHERM:02: registered as thermal_zone1
Nov  1 07:45:01 aspire kernel: [    1.832155] ACPI: Thermal Zone [TZ01] (34 C)
Nov  1 07:45:01 aspire kernel: [    1.832297] isapnp: Scanning for PnP cards...
Nov  1 07:45:01 aspire kernel: [    2.186966] isapnp: No Plug & Play device found
Nov  1 07:45:01 aspire kernel: [    3.100212] ACPI: Battery Slot [BAT1] (battery present)
Nov  1 07:45:01 aspire kernel: [    3.100487] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov  1 07:45:01 aspire kernel: [    3.103801] brd: module loaded
Nov  1 07:45:01 aspire kernel: [    3.104983] loop: module loaded
Nov  1 07:45:01 aspire kernel: [    3.105190] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Nov  1 07:45:01 aspire kernel: [    3.105467] ata_piix 0000:00:1f.1: version 2.13
Nov  1 07:45:01 aspire kernel: [    3.105492] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov  1 07:45:01 aspire kernel: [    3.105572] ata_piix 0000:00:1f.1: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.105726] scsi0 : ata_piix
Nov  1 07:45:01 aspire kernel: [    3.105924] scsi1 : ata_piix
Nov  1 07:45:01 aspire kernel: [    3.107317] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Nov  1 07:45:01 aspire kernel: [    3.107325] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Nov  1 07:45:01 aspire kernel: [    3.107601] ata2: port disabled. ignoring.
Nov  1 07:45:01 aspire kernel: [    3.109683] Fixed MDIO Bus: probed
Nov  1 07:45:01 aspire kernel: [    3.109773] PPP generic driver version 2.4.2
Nov  1 07:45:01 aspire kernel: [    3.109985] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov  1 07:45:01 aspire kernel: [    3.110026]   alloc irq_desc for 23 on node -1
Nov  1 07:45:01 aspire kernel: [    3.110032]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    3.110045] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  1 07:45:01 aspire kernel: [    3.110066] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.110075] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  1 07:45:01 aspire kernel: [    3.110182] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Nov  1 07:45:01 aspire kernel: [    3.114131] ehci_hcd 0000:00:1d.7: debug port 1
Nov  1 07:45:01 aspire kernel: [    3.114144] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Nov  1 07:45:01 aspire kernel: [    3.114173] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000
Nov  1 07:45:01 aspire kernel: [    3.128040] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov  1 07:45:01 aspire kernel: [    3.128217] usb usb1: configuration #1 chosen from 1 choice
Nov  1 07:45:01 aspire kernel: [    3.128292] hub 1-0:1.0: USB hub found
Nov  1 07:45:01 aspire kernel: [    3.128310] hub 1-0:1.0: 8 ports detected
Nov  1 07:45:01 aspire kernel: [    3.128460] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov  1 07:45:01 aspire kernel: [    3.128506] uhci_hcd: USB Universal Host Controller Interface driver
Nov  1 07:45:01 aspire kernel: [    3.128557] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  1 07:45:01 aspire kernel: [    3.128570] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.128578] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  1 07:45:01 aspire kernel: [    3.128653] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Nov  1 07:45:01 aspire kernel: [    3.128694] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Nov  1 07:45:01 aspire kernel: [    3.128878] usb usb2: configuration #1 chosen from 1 choice
Nov  1 07:45:01 aspire kernel: [    3.128947] hub 2-0:1.0: USB hub found
Nov  1 07:45:01 aspire kernel: [    3.128963] hub 2-0:1.0: 2 ports detected
Nov  1 07:45:01 aspire kernel: [    3.129091] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov  1 07:45:01 aspire kernel: [    3.129105] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.129113] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  1 07:45:01 aspire kernel: [    3.129199] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Nov  1 07:45:01 aspire kernel: [    3.129258] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
Nov  1 07:45:01 aspire kernel: [    3.129442] usb usb3: configuration #1 chosen from 1 choice
Nov  1 07:45:01 aspire kernel: [    3.129511] hub 3-0:1.0: USB hub found
Nov  1 07:45:01 aspire kernel: [    3.129526] hub 3-0:1.0: 2 ports detected
Nov  1 07:45:01 aspire kernel: [    3.129640] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  1 07:45:01 aspire kernel: [    3.129654] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.129662] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  1 07:45:01 aspire kernel: [    3.129738] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Nov  1 07:45:01 aspire kernel: [    3.129792] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Nov  1 07:45:01 aspire kernel: [    3.129975] usb usb4: configuration #1 chosen from 1 choice
Nov  1 07:45:01 aspire kernel: [    3.130049] hub 4-0:1.0: USB hub found
Nov  1 07:45:01 aspire kernel: [    3.130064] hub 4-0:1.0: 2 ports detected
Nov  1 07:45:01 aspire kernel: [    3.130168] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Nov  1 07:45:01 aspire kernel: [    3.130182] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.130190] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov  1 07:45:01 aspire kernel: [    3.130264] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Nov  1 07:45:01 aspire kernel: [    3.130317] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Nov  1 07:45:01 aspire kernel: [    3.130501] usb usb5: configuration #1 chosen from 1 choice
Nov  1 07:45:01 aspire kernel: [    3.130575] hub 5-0:1.0: USB hub found
Nov  1 07:45:01 aspire kernel: [    3.130590] hub 5-0:1.0: 2 ports detected
Nov  1 07:45:01 aspire kernel: [    3.130819] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Nov  1 07:45:01 aspire kernel: [    3.131250] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov  1 07:45:01 aspire kernel: [    3.131360] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  1 07:45:01 aspire kernel: [    3.131373] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov  1 07:45:01 aspire kernel: [    3.131382] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov  1 07:45:01 aspire kernel: [    3.131390] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov  1 07:45:01 aspire kernel: [    3.131398] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov  1 07:45:01 aspire kernel: [    3.131550] mice: PS/2 mouse device common for all mice
Nov  1 07:45:01 aspire kernel: [    3.131891] rtc_cmos 00:07: RTC can wake from S4
Nov  1 07:45:01 aspire kernel: [    3.131971] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Nov  1 07:45:01 aspire kernel: [    3.132038] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Nov  1 07:45:01 aspire kernel: [    3.132312] device-mapper: uevent: version 1.0.3
Nov  1 07:45:01 aspire kernel: [    3.132543] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov  1 07:45:01 aspire kernel: [    3.132694] device-mapper: multipath: version 1.1.0 loaded
Nov  1 07:45:01 aspire kernel: [    3.132701] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov  1 07:45:01 aspire kernel: [    3.132994] EISA: Probing bus 0 at eisa.0
Nov  1 07:45:01 aspire kernel: [    3.133007] Cannot allocate resource for EISA slot 1
Nov  1 07:45:01 aspire kernel: [    3.133014] Cannot allocate resource for EISA slot 2
Nov  1 07:45:01 aspire kernel: [    3.133056] EISA: Detected 0 cards.
Nov  1 07:45:01 aspire kernel: [    3.133475] cpuidle: using governor ladder
Nov  1 07:45:01 aspire kernel: [    3.133796] cpuidle: using governor menu
Nov  1 07:45:01 aspire kernel: [    3.134490] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Nov  1 07:45:01 aspire kernel: [    3.135124] TCP cubic registered
Nov  1 07:45:01 aspire kernel: [    3.135538] NET: Registered protocol family 10
Nov  1 07:45:01 aspire kernel: [    3.136679] lo: Disabled Privacy Extensions
Nov  1 07:45:01 aspire kernel: [    3.137541] NET: Registered protocol family 17
Nov  1 07:45:01 aspire kernel: [    3.137587] Bluetooth: L2CAP ver 2.13
Nov  1 07:45:01 aspire kernel: [    3.137592] Bluetooth: L2CAP socket layer initialized
Nov  1 07:45:01 aspire kernel: [    3.137599] Bluetooth: SCO (Voice Link) ver 0.6
Nov  1 07:45:01 aspire kernel: [    3.137604] Bluetooth: SCO socket layer initialized
Nov  1 07:45:01 aspire kernel: [    3.137689] Bluetooth: RFCOMM TTY layer initialized
Nov  1 07:45:01 aspire kernel: [    3.137697] Bluetooth: RFCOMM socket layer initialized
Nov  1 07:45:01 aspire kernel: [    3.137702] Bluetooth: RFCOMM ver 1.11
Nov  1 07:45:01 aspire kernel: [    3.138515] Using IPI No-Shortcut mode
Nov  1 07:45:01 aspire kernel: [    3.138647] PM: Resume from disk failed.
Nov  1 07:45:01 aspire kernel: [    3.138664] registered taskstats version 1
Nov  1 07:45:01 aspire kernel: [    3.138804]   Magic number: 1:529:722
Nov  1 07:45:01 aspire kernel: [    3.138814] block loop2: hash matches
Nov  1 07:45:01 aspire kernel: [    3.138914] rtc_cmos 00:07: setting system clock to 2009-11-01 07:44:52 UTC (1257061492)
Nov  1 07:45:01 aspire kernel: [    3.138919] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  1 07:45:01 aspire kernel: [    3.138921] EDD information not available.
Nov  1 07:45:01 aspire kernel: [    3.276743] ata1.00: ATA-6: ST9160821A, 3.ALD, max UDMA/100
Nov  1 07:45:01 aspire kernel: [    3.276748] ata1.00: 312581808 sectors, multi 16: LBA48 
Nov  1 07:45:01 aspire kernel: [    3.276794] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PP02, max UDMA/33
Nov  1 07:45:01 aspire kernel: [    3.292669] ata1.00: configured for UDMA/100
Nov  1 07:45:01 aspire kernel: [    3.308452] ata1.01: configured for UDMA/33
Nov  1 07:45:01 aspire kernel: [    3.310982] scsi 0:0:0:0: Direct-Access     ATA      ST9160821A       3.AL PQ: 0 ANSI: 5
Nov  1 07:45:01 aspire kernel: [    3.311206] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  1 07:45:01 aspire kernel: [    3.312894] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Nov  1 07:45:01 aspire kernel: [    3.314708] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PP02 PQ: 0 ANSI: 5
Nov  1 07:45:01 aspire kernel: [    3.314767] sd 0:0:0:0: [sda] Write Protect is off
Nov  1 07:45:01 aspire kernel: [    3.314775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  1 07:45:01 aspire kernel: [    3.314840] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  1 07:45:01 aspire kernel: [    3.326669] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Nov  1 07:45:01 aspire kernel: [    3.326677] Uniform CD-ROM driver Revision: 3.20
Nov  1 07:45:01 aspire kernel: [    3.326796]  sda:
Nov  1 07:45:01 aspire kernel: [    3.326870] sr 0:0:1:0: Attached scsi CD-ROM sr0
Nov  1 07:45:01 aspire kernel: [    3.326971] sr 0:0:1:0: Attached scsi generic sg1 type 5
Nov  1 07:45:01 aspire kernel: [    3.341838]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
Nov  1 07:45:01 aspire kernel: [    3.401527] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  1 07:45:01 aspire kernel: [    3.500093] Clocksource tsc unstable (delta = -186892146 ns)
Nov  1 07:45:01 aspire kernel: [    3.624173] usb 4-1: new low speed USB device using uhci_hcd and address 2
Nov  1 07:45:01 aspire kernel: [    3.668493] Freeing unused kernel memory: 540k freed
Nov  1 07:45:01 aspire kernel: [    3.668931] Write protecting the kernel text: 4568k
Nov  1 07:45:01 aspire kernel: [    3.669000] Write protecting the kernel read-only data: 1836k
Nov  1 07:45:01 aspire kernel: [    3.805429] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input6
Nov  1 07:45:01 aspire kernel: [    3.805486] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Nov  1 07:45:01 aspire kernel: [    3.812742] usb 4-1: configuration #1 chosen from 1 choice
Nov  1 07:45:01 aspire kernel: [    3.817694] Linux agpgart interface v0.103
Nov  1 07:45:01 aspire kernel: [    3.822035] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Nov  1 07:45:01 aspire kernel: [    3.822821] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Nov  1 07:45:01 aspire kernel: [    3.852559] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Nov  1 07:45:01 aspire kernel: [    3.938953] [drm] Initialized drm 1.1.0 20060810
Nov  1 07:45:01 aspire kernel: [    3.956593] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  1 07:45:01 aspire kernel: [    3.956603] i915 0000:00:02.0: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    3.961876]   alloc irq_desc for 21 on node -1
Nov  1 07:45:01 aspire kernel: [    3.961881]   alloc kstat_irqs on node -1
Nov  1 07:45:01 aspire kernel: [    3.961890] b44 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Nov  1 07:45:01 aspire kernel: [    3.961901] b44 0000:06:01.0: setting latency timer to 64
Nov  1 07:45:01 aspire kernel: [    4.021076] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
Nov  1 07:45:01 aspire kernel: [    4.021103] b44.c:v2.0
Nov  1 07:45:01 aspire kernel: [    4.041922] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:16:d4:4e:fe:31
Nov  1 07:45:01 aspire kernel: [    4.067130] usbcore: registered new interface driver hiddev
Nov  1 07:45:01 aspire kernel: [    4.081410] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input7
Nov  1 07:45:01 aspire kernel: [    4.081516] generic-usb 0003:046D:C045.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-1/input0
Nov  1 07:45:01 aspire kernel: [    4.081536] usbcore: registered new interface driver usbhid
Nov  1 07:45:01 aspire kernel: [    4.081540] usbhid: v2.6:USB HID core driver
Nov  1 07:45:01 aspire kernel: [    4.477197] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:01 aspire kernel: [    4.603793] [drm] fb0: inteldrmfb frame buffer device
Nov  1 07:45:01 aspire kernel: [    4.603806] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov  1 07:45:01 aspire kernel: [    4.672104] [drm] LVDS-8: set mode 1280x800 17
Nov  1 07:45:01 aspire kernel: [    4.939513] Console: switching to colour frame buffer device 160x50
Nov  1 07:45:01 aspire kernel: [    5.382339] PM: Starting manual resume from disk
Nov  1 07:45:01 aspire kernel: [    5.382345] PM: Resume from partition 8:8
Nov  1 07:45:01 aspire kernel: [    5.382348] PM: Checking hibernation image.
Nov  1 07:45:01 aspire kernel: [    5.382555] PM: Resume from disk failed.
Nov  1 07:45:01 aspire kernel: [    5.395844] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Nov  1 07:45:01 aspire kernel: [    5.395856] EXT4-fs (sda5): write access will be enabled during recovery
Nov  1 07:45:01 aspire kernel: [    5.400067] EXT4-fs (sda5): barriers enabled
Nov  1 07:45:01 aspire kernel: [    5.754739] kjournald2 starting: pid 394, dev sda5:8, commit interval 5 seconds
Nov  1 07:45:01 aspire kernel: [    5.754767] EXT4-fs (sda5): delayed allocation enabled
Nov  1 07:45:01 aspire kernel: [    5.754772] EXT4-fs: file extents enabled
Nov  1 07:45:01 aspire kernel: [    5.755885] EXT4-fs: mballoc enabled
Nov  1 07:45:01 aspire kernel: [    5.755903] EXT4-fs (sda5): recovery complete
Nov  1 07:45:01 aspire kernel: [    5.756362] EXT4-fs (sda5): mounted filesystem with ordered data mode
Nov  1 07:45:01 aspire kernel: [    6.376451] type=1505 audit(1257061495.737:2): operation="profile_load" pid=417 name=/usr/share/gdm/guest-session/Xsession
Nov  1 07:45:01 aspire kernel: [    6.379949] type=1505 audit(1257061495.737:3): operation="profile_load" pid=418 name=/sbin/dhclient3
Nov  1 07:45:01 aspire kernel: [    6.380767] type=1505 audit(1257061495.741:4): operation="profile_load" pid=418 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov  1 07:45:01 aspire kernel: [    6.381227] type=1505 audit(1257061495.741:5): operation="profile_load" pid=418 name=/usr/lib/connman/scripts/dhclient-script
Nov  1 07:45:01 aspire kernel: [    6.408494] type=1505 audit(1257061495.769:6): operation="profile_load" pid=419 name=/usr/bin/evince
Nov  1 07:45:01 aspire kernel: [    6.421186] type=1505 audit(1257061495.781:7): operation="profile_load" pid=419 name=/usr/bin/evince-previewer
Nov  1 07:45:01 aspire kernel: [    6.428754] type=1505 audit(1257061495.789:8): operation="profile_load" pid=419 name=/usr/bin/evince-thumbnailer
Nov  1 07:45:01 aspire kernel: [    6.461254] type=1505 audit(1257061495.821:9): operation="profile_load" pid=421 name=/usr/lib/cups/backend/cups-pdf
Nov  1 07:45:01 aspire kernel: [    6.462258] type=1505 audit(1257061495.821:10): operation="profile_load" pid=421 name=/usr/sbin/cupsd
Nov  1 07:45:01 aspire kernel: [    6.465539] type=1505 audit(1257061495.825:11): operation="profile_load" pid=422 name=/usr/sbin/tcpdump
Nov  1 07:45:01 aspire kernel: [    7.436604] Adding 2096440k swap on /dev/sda8.  Priority:-1 extents:1 across:2096440k 
Nov  1 07:45:01 aspire kernel: [    7.648836] udev: starting version 147
Nov  1 07:45:01 aspire kernel: [    7.898646] EXT4-fs (sda5): internal journal on sda5:8
Nov  1 07:45:01 aspire kernel: [    9.026497] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  1 07:45:01 aspire kernel: [    9.055989] intel_rng: FWH not detected
Nov  1 07:45:01 aspire kernel: [    9.484147] cfg80211: Calling CRDA to update world regulatory domain
Nov  1 07:45:01 aspire kernel: [    9.826574] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
Nov  1 07:45:01 aspire kernel: [    9.857857] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Nov  1 07:45:01 aspire kernel: [   11.484639] kjournald starting.  Commit interval 5 seconds
Nov  1 07:45:01 aspire kernel: [   11.485023] EXT3 FS on sda9, internal journal
Nov  1 07:45:01 aspire kernel: [   11.485036] EXT3-fs: mounted filesystem with writeback data mode.
Nov  1 07:45:01 aspire kernel: [   11.530492] lp: driver loaded but no devices found
Nov  1 07:45:01 aspire kernel: [   11.891913] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:0090]
Nov  1 07:45:01 aspire kernel: [   11.891941] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
Nov  1 07:45:01 aspire kernel: [   11.891944] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
Nov  1 07:45:01 aspire kernel: [   11.891952] yenta_cardbus 0000:06:04.0: TI: mfunc 0x90501212, devctl 0x44
Nov  1 07:45:01 aspire kernel: [   12.120831] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
Nov  1 07:45:01 aspire kernel: [   12.120838] yenta_cardbus 0000:06:04.0: Socket status: 30000006
Nov  1 07:45:01 aspire kernel: [   12.120844] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Nov  1 07:45:01 aspire kernel: [   12.120855] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Nov  1 07:45:01 aspire kernel: [   12.120860] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
Nov  1 07:45:01 aspire kernel: [   12.121144] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Nov  1 07:45:01 aspire kernel: [   12.121148] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
Nov  1 07:45:02 aspire kernel: [   12.975742] type=1505 audit(1257057902.333:12): operation="profile_replace" pid=842 name=/usr/share/gdm/guest-session/Xsession
Nov  1 07:45:02 aspire kernel: [   12.977989] type=1505 audit(1257057902.337:13): operation="profile_replace" pid=843 name=/sbin/dhclient3
Nov  1 07:45:02 aspire kernel: [   12.978818] type=1505 audit(1257057902.337:14): operation="profile_replace" pid=843 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov  1 07:45:02 aspire kernel: [   12.979272] type=1505 audit(1257057902.337:15): operation="profile_replace" pid=843 name=/usr/lib/connman/scripts/dhclient-script
Nov  1 07:45:02 aspire kernel: [   12.984465] type=1505 audit(1257057902.345:16): operation="profile_replace" pid=844 name=/usr/bin/evince
Nov  1 07:45:02 aspire kernel: [   12.997424] type=1505 audit(1257057902.357:17): operation="profile_replace" pid=844 name=/usr/bin/evince-previewer
Nov  1 07:45:02 aspire kernel: [   13.006448] type=1505 audit(1257057902.365:18): operation="profile_replace" pid=844 name=/usr/bin/evince-thumbnailer
Nov  1 07:45:02 aspire kernel: [   13.017254] type=1505 audit(1257057902.377:19): operation="profile_replace" pid=846 name=/usr/lib/cups/backend/cups-pdf
Nov  1 07:45:02 aspire kernel: [   13.018219] type=1505 audit(1257057902.377:20): operation="profile_replace" pid=846 name=/usr/sbin/cupsd
Nov  1 07:45:02 aspire kernel: [   13.021115] type=1505 audit(1257057902.381:21): operation="profile_replace" pid=847 name=/usr/sbin/tcpdump
Nov  1 07:45:02 aspire kernel: [   13.104223] cfg80211: World regulatory domain updated:
Nov  1 07:45:02 aspire kernel: [   13.104228] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  1 07:45:02 aspire kernel: [   13.104233] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 07:45:02 aspire kernel: [   13.104237] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  1 07:45:02 aspire kernel: [   13.104240] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  1 07:45:02 aspire kernel: [   13.104244] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 07:45:02 aspire kernel: [   13.104248] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  1 07:45:02 aspire kernel: [   13.305267] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Nov  1 07:45:02 aspire kernel: [   13.305273] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Nov  1 07:45:02 aspire kernel: [   13.305371] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov  1 07:45:02 aspire kernel: [   13.305387] iwl3945 0000:05:00.0: setting latency timer to 64
Nov  1 07:45:02 aspire kernel: [   13.325090] sdhci: Secure Digital Host Controller Interface driver
Nov  1 07:45:02 aspire kernel: [   13.325094] sdhci: Copyright(c) Pierre Ossman
Nov  1 07:45:02 aspire kernel: [   13.327027] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
Nov  1 07:45:02 aspire kernel: [   13.327045] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
Nov  1 07:45:02 aspire kernel: [   13.327056] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  1 07:45:02 aspire kernel: [   13.327145] Registered led device: mmc0::
Nov  1 07:45:02 aspire kernel: [   13.327189] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
Nov  1 07:45:02 aspire kernel: [   13.327203] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
Nov  1 07:45:02 aspire kernel: [   13.327217] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
Nov  1 07:45:02 aspire kernel: [   13.327224] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  1 07:45:02 aspire kernel: [   13.327273] Registered led device: mmc1::
Nov  1 07:45:02 aspire kernel: [   13.327307] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
Nov  1 07:45:02 aspire kernel: [   13.389570] acer-wmi: Acer Laptop ACPI-WMI Extras
Nov  1 07:45:02 aspire kernel: [   13.389711] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Nov  1 07:45:02 aspire kernel: [   13.389716] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
Nov  1 07:45:02 aspire kernel: [   13.389837]   alloc irq_desc for 28 on node -1
Nov  1 07:45:02 aspire kernel: [   13.389840]   alloc kstat_irqs on node -1
Nov  1 07:45:02 aspire kernel: [   13.389875] iwl3945 0000:05:00.0: irq 28 for MSI/MSI-X
Nov  1 07:45:02 aspire kernel: [   13.500453] Registered led device: acer-wmi::mail
Nov  1 07:45:02 aspire anacron[951]: Anacron 2.3 started on 2009-11-01
Nov  1 07:45:03 aspire kernel: [   13.670181] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Nov  1 07:45:03 aspire kernel: [   13.672311] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Nov  1 07:45:03 aspire kernel: [   13.673205] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Nov  1 07:45:03 aspire kernel: [   13.673930] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Nov  1 07:45:03 aspire kernel: [   13.674858] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Nov  1 07:45:03 aspire init: apport pre-start process (921) terminated with status 1
Nov  1 07:45:03 aspire init: apport post-stop process (955) terminated with status 1
Nov  1 07:45:03 aspire kernel: [   14.002097]   alloc irq_desc for 22 on node -1
Nov  1 07:45:03 aspire kernel: [   14.002102]   alloc kstat_irqs on node -1
Nov  1 07:45:03 aspire kernel: [   14.002112] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov  1 07:45:03 aspire kernel: [   14.002158] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov  1 07:45:03 aspire anacron[951]: Will run job `cron.daily' in 5 min.
Nov  1 07:45:03 aspire anacron[951]: Jobs will be executed sequentially
Nov  1 07:45:03 aspire cron[942]: (CRON) INFO (pidfile fd = 3)
Nov  1 07:45:03 aspire cron[1012]: (CRON) STARTUP (fork ok)
Nov  1 07:45:03 aspire cron[1012]: (CRON) INFO (Running @reboot jobs)
Nov  1 07:45:03 aspire kernel: [   14.320702] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
Nov  1 07:45:03 aspire kernel: [   14.517071] phy0: Selected rate control algorithm 'iwl-3945-rs'
Nov  1 07:45:04 aspire kernel: [   14.942673] ppdev: user-space parallel port driver
Nov  1 07:45:04 aspire udev-configure-printer: add /module/lp
Nov  1 07:45:04 aspire udev-configure-printer: Failed to get parent
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2
Nov  1 07:45:05 aspire udev-configure-printer: Failed to get parent
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 1D6B:0001
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4/4-1
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.3/usb5
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1
Nov  1 07:45:05 aspire udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 1D6B:0001
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire udev-configure-printer: Failed to get parent
Nov  1 07:45:05 aspire udev-configure-printer: Failed to get parent
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb4
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 1D6B:0001
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb4
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 1D6B:0001
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb4/4-1
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 046D:C045
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire udev-configure-printer: Failed to get parent
Nov  1 07:45:05 aspire udev-configure-printer: Failed to get parent
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.3/usb5
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 1D6B:0001
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Nov  1 07:45:05 aspire udev-configure-printer: Device vendor/product is 1D6B:0002
Nov  1 07:45:05 aspire udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  1 07:45:05 aspire NetworkManager: <info>  starting...
Nov  1 07:45:05 aspire NetworkManager: <info>  Trying to start the modem-manager...
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: init!
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Nov  1 07:45:05 aspire NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/wlan0, iface: wlan0)
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/wmaster0, iface: wmaster0)
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/ssb0:0/net/eth0, iface: eth0)
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/ssb0:0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: end _init.
Nov  1 07:45:05 aspire NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  1 07:45:05 aspire NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  1 07:45:05 aspire NetworkManager: <info>  Found radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Nov  1 07:45:05 aspire NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/platform/acer-wmi/rfkill/rfkill1) (driver acer-wmi)
Nov  1 07:45:05 aspire NetworkManager: <info>  Wireless now enabled by radio killswitch
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: (152144624) ... get_connections.
Nov  1 07:45:05 aspire NetworkManager:    SCPlugin-Ifupdown: (152144624) ... get_connections (managed=false): return empty list.
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Gobi
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Generic
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Nokia
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Huawei
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Novatel
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Sierra
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Option
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Ericsson MBM
Nov  1 07:45:06 aspire modem-manager: Loaded plugin ZTE
Nov  1 07:45:06 aspire modem-manager: Loaded plugin MotoC
Nov  1 07:45:06 aspire modem-manager: Loaded plugin Option High-Speed
Nov  1 07:45:06 aspire NetworkManager:    Ifupdown: get unmanaged devices count: 0
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945')
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): now managed
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): bringing up device.
Nov  1 07:45:06 aspire kernel: [   17.012622] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-2.ucode
Nov  1 07:45:06 aspire kernel: [   17.060198] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
Nov  1 07:45:06 aspire kernel: [   17.130054] Registered led device: iwl-phy0::radio
Nov  1 07:45:06 aspire kernel: [   17.130146] Registered led device: iwl-phy0::assoc
Nov  1 07:45:06 aspire kernel: [   17.130189] Registered led device: iwl-phy0::RX
Nov  1 07:45:06 aspire kernel: [   17.130234] Registered led device: iwl-phy0::TX
Nov  1 07:45:06 aspire kernel: [   17.149253] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): preparing device.
Nov  1 07:45:06 aspire kernel: [   17.154569] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov  1 07:45:06 aspire NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): carrier is OFF
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): new Ethernet device (driver: 'b44')
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): now managed
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): bringing up device.
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): preparing device.
Nov  1 07:45:06 aspire NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  1 07:45:06 aspire NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/ssb0:0/net/eth0
Nov  1 07:45:06 aspire NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov  1 07:45:06 aspire NetworkManager: <info>  modem-manager is now available
Nov  1 07:45:06 aspire NetworkManager: <info>  Trying to start the supplicant...
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Nov  1 07:45:06 aspire NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov  1 07:45:08 aspire gdm-binary[796]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov  1 07:45:09 aspire gdm-binary[796]: WARNING: Unable to find users: no seat-id found
Nov  1 07:45:09 aspire gdm-simple-slave[1360]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov  1 07:45:09 aspire wpa_supplicant[1246]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 07:45:09 aspire wpa_supplicant[1246]: WPS-AP-AVAILABLE 
Nov  1 07:45:09 aspire acpid: client connected from 1381[107:114]
Nov  1 07:45:09 aspire acpid: client connected from 1364[0:0]
Nov  1 07:45:09 aspire kernel: [   20.459523] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:09 aspire kernel: [   20.600530] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:10 aspire kernel: [   20.816179] b44: eth0: Link is up at 100 Mbps, full duplex.
Nov  1 07:45:10 aspire kernel: [   20.816183] b44: eth0: Flow control is off for TX and off for RX.
Nov  1 07:45:10 aspire NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Nov  1 07:45:10 aspire NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov  1 07:45:10 aspire NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov  1 07:45:10 aspire NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov  1 07:45:10 aspire kernel: [   20.849208] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov  1 07:45:10 aspire kernel: [   20.916718] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  1 07:45:10 aspire NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov  1 07:45:10 aspire kernel: [   21.059879] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:10 aspire NetworkManager: <info>  dhclient started with pid 1404
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  1 07:45:10 aspire dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  1 07:45:10 aspire dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  1 07:45:10 aspire dhclient: All rights reserved.
Nov  1 07:45:10 aspire dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  1 07:45:10 aspire dhclient: 
Nov  1 07:45:10 aspire NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Nov  1 07:45:10 aspire dhclient: Listening on LPF/eth0/00:16:d4:4e:fe:31
Nov  1 07:45:10 aspire dhclient: Sending on   LPF/eth0/00:16:d4:4e:fe:31
Nov  1 07:45:10 aspire dhclient: Sending on   Socket/fallback
Nov  1 07:45:10 aspire dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  1 07:45:10 aspire dhclient: DHCPOFFER of 192.168.0.119 from 192.168.0.1
Nov  1 07:45:10 aspire dhclient: DHCPREQUEST of 192.168.0.119 on eth0 to 255.255.255.255 port 67
Nov  1 07:45:10 aspire dhclient: DHCPACK of 192.168.0.119 from 192.168.0.1
Nov  1 07:45:10 aspire dhclient: bound to 192.168.0.119 -- renewal in 231788 seconds.
Nov  1 07:45:10 aspire NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  1 07:45:10 aspire NetworkManager: <info>    address 192.168.0.119
Nov  1 07:45:10 aspire NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov  1 07:45:10 aspire NetworkManager: <info>    gateway 192.168.0.1
Nov  1 07:45:10 aspire NetworkManager: <info>    nameserver '10.10.0.1'
Nov  1 07:45:10 aspire NetworkManager: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed
Nov  1 07:45:10 aspire NetworkManager: <info>    nameserver '10.10.0.1'
Nov  1 07:45:10 aspire NetworkManager: <info>    domain name 'studnet.europahaus.sth.ac.at'
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  1 07:45:10 aspire NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov  1 07:45:11 aspire NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Nov  1 07:45:11 aspire NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  1 07:45:11 aspire NetworkManager: <info>  Activation (eth0) successful, device activated.
Nov  1 07:45:11 aspire NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  1 07:45:13 aspire ntpdate[1481]: step time server 91.189.94.4 offset 0.531818 sec
Nov  1 07:45:13 aspire console-kit-daemon[1149]: WARNING: Couldn't read /proc/800/environ: Failed to open file '/proc/800/environ': No such file or directory
Nov  1 07:45:15 aspire kernel: [   25.772763] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:15 aspire kernel: [   25.913102] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:16 aspire kernel: [   26.193031] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:16 aspire kernel: [   26.334020] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:16 aspire kernel: [   26.639840] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:16 aspire kernel: [   26.780651] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:20 aspire kernel: [   30.880039] eth0: no IPv6 routers present
Nov  1 07:45:25 aspire NetworkManager: <info>  Wireless now disabled by radio killswitch
Nov  1 07:45:25 aspire NetworkManager: <info>  (wlan0): device state change: 3 -> 2 (reason 0)
Nov  1 07:45:25 aspire NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Nov  1 07:45:25 aspire kernel: [   35.508081] iwl3945 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD
Nov  1 07:45:25 aspire NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  1 07:45:31 aspire kernel: [   41.989256] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:32 aspire kernel: [   42.134071] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:32 aspire kernel: [   42.425613] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:32 aspire kernel: [   42.570058] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:32 aspire kernel: [   42.848742] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:32 aspire kernel: [   42.991721] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:33 aspire kernel: [   44.040866] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:45:34 aspire kernel: [   44.182220] [drm] TV-14: set mode NTSC 480i 0
Nov  1 07:50:02 aspire anacron[951]: Job `cron.daily' started
Nov  1 07:50:02 aspire anacron[1960]: Updated timestamp for job `cron.daily' to 2009-11-01
Nov  1 07:50:37 aspire kernel: [  347.122485] CE: hpet increasing min_delta_ns to 15000 nsec
```

---

### Post by Andreas1 on 2009-11-01
> **DeMus said:**
> Try running for a while without Compiz just as a test to see if that is causing the problems you have.
It wouldn't be the first time Compiz is causing this.

i think i will do that, also on that topic, i just found [this]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze"), and from the look of it i would say these are X freezes.

one question though: does is fit in the profile of an X freeze, that one application becomes unresponsive and i am getting the "force quit now?" dialog window when i try to close it? because that sometimes happens.

---

### Post by philippe_carlo on 2009-11-01
I used to have a similar problem when the cron would run. Disabling cron did fix the issue. You may want to verify if that helps for you.

---

### Post by Andreas1 on 2009-11-01
> **philippe_carlo said:**
> I used to have a similar problem when the cron would run. Disabling cron did fix the issue. You may want to verify if that helps for you.

did you find indications towards that in the log?

---

### Post by Andreas1 on 2009-11-01
ok, news

fist, i found that if i suspend the computer while playing audio (rhythmbox) it is likely (but not certain) to freeze shortly after resume (in 2 cases i only got a black screen, in 1 case rhythmbox froze shortly after unlocking the screen, then everything else froze)

second, compiz was deactivated in those mentioned 2 cases


unless... the freezing related to playing audio is yet another bug, then things would get complicated...

EDIT: now i'm gonna check how many times i can provoke freezing with audio playback, also outside rhythmbox

EDIT: managed to provoke another freeze with totem, none with vlc and youtube in firefox so far, don't rhythmbox and totem have the gstreamer backend in common? unfortunately i cannot remember if i had rhythmbox playing in all of the cases but i guess it is possible

---

### Post by wayneox on 2009-11-01
i was talking on msn earlier n ended up having my whole system freeze [but not freeze] - messages were coming up on empathy, but nothing would respond... - i did "killall empathy"  on TTY1 [CTRL ALT F1] - logged in, sudo bash... killall .... - and there we go - only thing running was empathy n a terminal n a gedit... so i thought "dont see a txt file or non-running terminal doing it, so empathy it is... :P - were u running it... 

i never had this in 9.04, just a cpl times since im using empathy.. [never used pidgen messenger - didnt like it..., since empathy was bundled i decided to try this...

---

### Post by kvmapr on 2009-11-01
Lots of folks are reporting system crashes when running Firefox (myself included). Try working without starting Firefox, see if you system's stability improves.

---

### Post by Andreas1 on 2009-11-02
> **wayneox said:**
> i was talking on msn earlier n ended up having my whole system freeze [but not freeze] - messages were coming up on empathy, but nothing would respond... - i did "killall empathy"  on TTY1 [CTRL ALT F1] - logged in, sudo bash... killall .... - and there we go - only thing running was empathy n a terminal n a gedit... so i thought "dont see a txt file or non-running terminal doing it, so empathy it is... :P - were u running it... 

i never had this in 9.04, just a cpl times since im using empathy.. [never used pidgen messenger - didnt like it..., since empathy was bundled i decided to try this...

no, empathy was not running


> **kvmapr said:**
> Lots of folks are reporting system crashes when running Firefox (myself included). Try working without starting Firefox, see if you system's stability improves.

possible, because firefox is almost always running on my system, will try without


also, my audio playback suspicion has been refuted by another freeze without any audio playing. and i found this in my pm-suspend.log (i did not cut off the end, that's where it froze i guess):

```
Mon Nov  2 09:33:32 CET 2009: performing suspend
Mon Nov  2 09:59:46 CET 2009: Awake.
Mon Nov  2 09:59:46 CET 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils
```

does the exit code 1 from the video mean anything?

---

### Post by woohhaa on 2009-11-02
Mine is freezing as well. It seems to freeze after the the monitor power saver kicks in. I will close firefox to see if mine does it w/o the browser opened. Like Andreas1 said my fire fox is almost always opened.

---

### Post by Andreas1 on 2009-11-02
> **philippe_carlo said:**
> I used to have a similar problem when the cron would run. Disabling cron did fix the issue. You may want to verify if that helps for you.

was that in karmic? also, how do i disable cron and what is it running for anyway?

---

### Post by Andreas1 on 2009-11-02
ok, it's not firefox either, this time i had no extra application running at all, system froze upon alt+f2 dialog after resume from suspend

---

### Post by woohhaa on 2009-11-02
I disabled the power save function so that the computer and the monitor never go to sleep and made sure to close fire fox. Came home 13 hours later and my system hadn't frozen. Tomorrow I will re-enable the power save function and see what happens then post my results.

---

### Post by ceruleanchalice on 2009-11-03
Bump bump! I have the same problem. Thought it had to do with Ext4 as I soon got hard drive errors on mounting Karmic, but that was just a coincidence. Reinstalled using Ext3 format for my file system and after a few hours, the freezes started again. I was running nothing! I close firefox and use Rhythmbox and still get the freeze after a while. The timings seem random and come for about a minute and then go. This could pose a serious problem for some users and I think it really needs to be addresses, especially if it could be linked with ruining the file system and integrity of Karmic.

Subscribing and awaiting a response!

Cheers

CC):P

---

### Post by Andreas1 on 2009-11-03
> **ceruleanchalice said:**
> Bump bump! I have the same problem. Thought it had to do with Ext4 as I soon got hard drive errors on mounting Karmic, but that was just a coincidence. Reinstalled using Ext3 format for my file system and after a few hours, the freezes started again. I was running nothing! I close firefox and use Rhythmbox and still get the freeze after a while. The timings seem random and come for about a minute and then go. This could pose a serious problem for some users and I think it really needs to be addresses, especially if it could be linked with ruining the file system and integrity of Karmic.

Subscribing and awaiting a response!

Cheers

CC):P


is your freezing appearing exclusively after the system has been suspended at least once? if not, you might be dealing with another bug.

---

### Post by PokeParadox on 2009-11-03
This is also occurring for me. I'm using Xubuntu 9.10.

---

### Post by woohhaa on 2009-11-03
Set power saver on monitor for 10 minutes. Came home from work to a non-frozen system. So far that's two days in a row of no freezes. I did all the updates today and will try leaving fire fox opened tonight and see what it does.

---

### Post by Teyphas on 2009-11-04
My system freeze too. Was testing Empathy IM. Logged on with Gmail account, and while talking, i just moved mouse on "Contact" menu. Grey square closed half of Empathy window, however i saw messages from my friend still comming. O_O

---

### Post by Andreas1 on 2009-11-04
> **Teyphas said:**
> My system freeze too. Was testing Empathy IM. Logged on with Gmail account, and while talking, i just moved mouse on "Contact" menu. Grey square closed half of Empathy window, however i saw messages from my friend still comming. O_O

if your freezing is related to empathy i suggest you open an own thread.

---

### Post by Andreas1 on 2009-11-04
ok, i just hastily learned how to ssh so i can retrieve some data for a bug report as described [here]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze"), now it just won't freeze, argh!

could someome please look at my pm-suspend.log i posted above and tell me if that exit code 1 means anything?

---

### Post by Andreas1 on 2009-11-04
ok, system froze again, ssh (which previously worked) did not respond after the password prompt.

if collecting data via ssh is recommended for x freezes, i take it as implied that ssh should still be possible in that case. so does that mean it is not an x freeze?

---

### Post by PokeParadox on 2009-11-04
I turned off power management... still getting random freeze.
I did a complete fresh install... it lasted overnight. Then later it froze while editing a forum post.
I installed the Nvidia drivers in the morning... so maybe they are what caused the instability... but I am not sure.

Regadless I'm now back with Jaunty as that was stable for me.

---

### Post by Andreas1 on 2009-11-05
bump. i would appreciate some expert input here, i am willing to keep on trying but i really need some direction.

---

### Post by Andreas1 on 2009-11-09
maybe it's too soon to say something but i tried disabling a few xorg options and after disabling mtrr i have only had like 1 freeze in 2 days. not a fix but maybe it interferes with whatever is causing the freezes?
unless it's just coincidence...
anyway, here's my xorg, anyone else confirm that observation?
```
Section "Device"
    Identifier "Intel GMA 950"
    Driver     "intel"
#    Option "AccelMethod" "XAA" #- Try "XAA", "EXA", and (on recent -intel) "UXA"
#    Option "Accel" "Off"       #- turns off the 2D acceleration
#    Option "DRI" "Off"         #- turns off the 3D acceleration
#    Option "AIGLX" "Off"       #- turns off OpenGL indirect rendering acceleration
#    Option "PM" "Off"          #- turns off power management events
    Option "NoMTRR"            #- turns off Memory Type Range Register support, which greatly improves performance so is usually on, but some hardware has buggy support for it 
EndSection

```


EDIT:forget what i said, it *was* coincidence

---

### Post by butters stotch on 2009-11-09
I have the same problem in Thinkpad T40, with ATI radeon 7500.
Everything works perfect in 9.04.
It may freeze 3-4 times in a week, no response at all (ctrl+alt+F?)

---

### Post by michaelzap on 2009-11-09
I had constant (as in every few minutes) freezing and crashing on my Lenovo Y530 running a clean install of Karmic x64 until I started using the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

If you want to see if this helps you as well, just download three .deb files from the latest (RC6) folder: The headers and kernel file for your architecture (i386 or amd64), and the "all" headers file (you don't need the "source" file). Then double-click on them to install (if you get dependency errors that just means you need to install them in the right order). After that reboot and choose the new kernel from the grub menu.

If it doesn't work better for you, just reboot again and choose the older kernel. You can remove it if you like using Synaptic, but it doesn't hurt anything to leave it there.

---

### Post by gpstar on 2009-11-09
I also get random freezes with karmic 64bit install, where the entire system locks up. Usually the system will seem sluggish at first with mouse lag and program lag. Things from simple scrolling webpages in firefox will lag, etc. Then the computer will freeze while sitting idle for awhile sometimes. I have a feeling it may be linked to pulse audio. My log file gets filled with alot of

ubuntu pulseaudio[1441]: ratelimit.c: 109 events suppressed

type messages after a few hours when I do a fresh boot up.

---

### Post by Andreas1 on 2009-11-09
> **butters stotch said:**
> I have the same problem in Thinkpad T40, with ATI radeon 7500.
Everything works perfect in 9.04.
It may freeze 3-4 times in a week, no response at all (ctrl+alt+F?)

> **michaelzap said:**
> I had constant (as in every few minutes) freezing and crashing on my Lenovo Y530 running a clean install of Karmic x64 until I started using the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

If you want to see if this helps you as well, just download three .deb files from the latest (RC6) folder: The headers and kernel file for your architecture (i386 or amd64), and the "all" headers file (you don't need the "source" file). Then double-click on them to install (if you get dependency errors that just means you need to install them in the right order). After that reboot and choose the new kernel from the grub menu.

If it doesn't work better for you, just reboot again and choose the older kernel. You can remove it if you like using Synaptic, but it doesn't hurt anything to leave it there.

> **gpstar said:**
> I also get random freezes with karmic 64bit install, where the entire system locks up. Usually the system will seem sluggish at first with mouse lag and program lag. Things from simple scrolling webpages in firefox will lag, etc. Then the computer will freeze while sitting idle for awhile sometimes. I have a feeling it may be linked to pulse audio. My log file gets filled with alot of

ubuntu pulseaudio[1441]: ratelimit.c: 109 events suppressed

type messages after a few hours when I do a fresh boot up.


are any of your freezings related to the computer being suspended at least once before?
also, did anyone successfully try to ssh into the frozen system as described above?

and thanks, michaelzap, for the idea with the rc kernel, i will try it!

---

### Post by butters stotch on 2009-11-09
> **Andreas1 said:**
> are any of your freezings related to the computer being suspended at least once before?
also, did anyone successfully try to ssh into the frozen system as described above?

and thanks, michaelzap, for the idea with the rc kernel, i will try it!

No, since I always shutdown recently instead of suspend.
I never know how to ssh my own laptop...

I didn't feel any abnormal before the freeze.
It happens in a sudden, with a normal cpu temp.

---

### Post by gpstar on 2009-11-09
none are mine related to suspending.

---

### Post by RochJer on 2009-11-09
I am experiencing unusual freezing like previous users mentioned about audio, firefox, etc. I was running Synaptic updates with Firefox opened, Synaptic then all of a sudden my CPU kept running without stopping even though all of the installations are done.

---

### Post by gpstar on 2009-11-09
new screenshot, with just over 6hours uptime today, pulse audio is hogging up all my system memory. Probably wont be much longer now until the system freezes up again.

---

### Post by gpstar on 2009-11-09
So I killed pulseaudio and restarted it.

I'm sitting here watching it in the system monitor right now, and it is slowly eating up memory, just idling. Eating Up/Counting up at about a rate of 1mb in 10secs.

---

### Post by butters stotch on 2009-11-09
> **michaelzap said:**
> I had constant (as in every few minutes) freezing and crashing on my Lenovo Y530 running a clean install of Karmic x64 until I started using the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

If you want to see if this helps you as well, just download three .deb files from the latest (RC6) folder: The headers and kernel file for your architecture (i386 or amd64), and the "all" headers file (you don't need the "source" file). Then double-click on them to install (if you get dependency errors that just means you need to install them in the right order). After that reboot and choose the new kernel from the grub menu.

If it doesn't work better for you, just reboot again and choose the older kernel. You can remove it if you like using Synaptic, but it doesn't hurt anything to leave it there.

Has anyone tried this?
The new kernel is said to be released on Nov 9 on kernel.org.
I'll just wait to see what will happen after next update.
If still not good, I have to go back to 9.04.
I got 5 freeze today!!!!

BTW, nice system, GPStar

---

### Post by gpstar on 2009-11-09
hmmm, the pulseaudio memory issue seems to have been known and a bug has been filed for it

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)

dunno if this is the same problem others are having in this thread, but seems to be the major issue with my system at the moment which causes slowdown and eventual freezing.

---

### Post by michaelzap on 2009-11-09
> **butters stotch said:**
> Has anyone tried this?
The new kernel is said to be released on Nov 9 on kernel.org.
I'll just wait to see what will happen after next update.
If still not good, I have to go back to 9.04.
I got 5 freeze today!!!!

BTW, nice system, GPStar

Well, I've tried it. ;)

My Karmic laptop was completely unusable before I did this, and now it's pretty darn good.

---

### Post by butters stotch on 2009-11-09
> **michaelzap said:**
> Well, I've tried it. ;)

My Karmic laptop was completely unusable before I did this, and now it's pretty darn good.

...Of course you did.
I learned this from you...

---

### Post by michaelzap on 2009-11-09
> **butters stotch said:**
> ...Of course you did.
I learned this from you...

That's why I winked, Butters!

It's a harmless thing to try out, so give it a shot and see if it works for you.

---

### Post by UranUtan on 2009-11-09
Hi,

I created a post "9.10 various stability issues with Gnome ?" Requoted here for convenience.

In short: Xubuntu 9.10 works flawlessly. Ubuntu has various minor issues. The most annoying one is the random freezing on one of the Ubuntu machine. Compiz is turned off, the freezing occurs randomly and I don't know yet the pattern that trigger the freezing (has ruled out Empathy and Screen saver).

> Hi,

Since the 9.10 release, I have made 6 fresh installations on machines which were running Ubuntu 9.04 perfectly. Xubuntu 9.10 x32 was installed on two machines. It works beautifully.

On the other two machines (a laptop and a desktop, both about 4 or 5 years old). Ubuntu 9.10 x32 didn't go very well. Each of these machines, Ubuntu 9.10 x32 had to be installed twice.

The laptop had some weird issues such as flash plugin cannot be installed, wireless not recognized, impossible to save Firefox bookmark, etc. After various reinstall, reboot, system updates, etc. It works almost OK. For now only the wireless is not working, hope it will be fixed a few weeks later.

The desktop is, on the other hand catastrophic. It runs OK for about a few hours and the desktop just freezes with no warning. Only the mouse can move. The Menu items lose their icon, clicking anything will end up with a message like 'gnome cannot start Terminal' (I forgot the exact message).

Ctrl-Alt-Fx sometimes clear the GUI but displays a totally black screen, no input is echoed. Sometimes, this key Ctrl-Alt-Fx doesn't work. The only possible action is power off and on again, and after a few hours, the freezing cycle repeat itself. I have no idea what is the triggering factor. As the instability issues only show up in Ubuntu machines and not the Xubuntu ones, I must assume that this comes from Gnome. I wish to supply more debug info to the experts in the forum, but I don't know what to look for. The only things running is Firefox, Empathy.

Can you please give me some hints to investigate further?

Thanks in advance for any help.

---

### Post by boot_sectorz on 2009-11-10
I'm just downloading the new kernel and I hope it sorts out all the freezing. Not thinking of downgrading any sooner, but this freezing may not be good for me.

---

### Post by Andreas1 on 2009-11-10
my system keeps freezing also with the new kernel. also, since none of your freezes are related to suspend, i would say we are dealing with different problems here. i'm out of this thread now, making a bug report and then installing debian...

..or maybe i will try kubuntu first to see if the freezing is desktop-environment-related

---

### Post by ronmon on 2009-11-10
Someone gave me an old laptop with a dead HDD, so I replaced that and decided to install karmic on it just to try it out. I'm a long time Gentoo user, but compiling an entire system would be too much for for this machine.

At first, I tried ubuntu-9.10 and I was getting these random lockups. So I did another clean install, this time xubuntu-9.10 (which I like better than GNOME anyway). Much to my chagrin, I had the same problem. Sometimes it would run for hours on end with lots of activity going on. Other times, it would die at startup or shortly thereafter with practically no activity. It seems to be a truly random problem and difficult to diagnose.

Now, I am trying the 2.6.32-rc6 kernel. That seems to have pulled in a few more upgrades, including a new xorg-server and xorg-input drivers. So far so good, but it has only been 30 minutes or so. I'm keeping my fingers crossed.

---

### Post by ronmon on 2009-11-10
Well, it lasted about an hour this time, then it went to a black screen. Only the cursor was visible, and I could move it with the trackpad.

Fortunately, I had spent that time getting ssh up and running. I logged in from my desktop and found a long series of this error message in /var/log/syslog:
```

drm:i915_gem_execbuffer ERROR Execbuf while wedged

```

The only difference between my earlier freezes was that I was able to drop to a console using Ctl+Alt+Fn and reboot from there. Previously, even keyboard input was dead. So that was some improvement.

It's back up and running again, but for how long remains to be seen. This is getting to be very frustrating.

---

### Post by ronmon on 2009-11-11
Along with the 2.6.32-r6 kernel, [the nomodeset GRUB option]("http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS") for my intel graphics chip seems to have helped. No freezes in one whole day.

---

### Post by bt107 on 2009-11-11
I'm getting hard freeze ups with a clean install of Karmic 9.10. It runs fine until I activate the restricted driver (nvidia 96. for GeForce4 MX) then it begins to randomly lock up. I have to power down to reboot.

---

### Post by caligoanimus on 2009-11-11
I just want to confirm that I have also been experiencing random freezes. Only output in logs directly related to the freezes (every time) is the "pulseaudio[20946]: ratelimit.c 426 events suppressed" (not always 426 obviously, but large numbers)
Lose complete mouse/keyboard functionality so can't drop into the console/tty8 either...

---

### Post by ngtc32 on 2009-11-12
> **michaelzap said:**
> I had constant (as in every few minutes) freezing and crashing on my Lenovo Y530 running a clean install of Karmic x64 until I started using the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

If you want to see if this helps you as well, just download three .deb files from the latest (RC6) folder: The headers and kernel file for your architecture (i386 or amd64), and the "all" headers file (you don't need the "source" file). Then double-click on them to install (if you get dependency errors that just means you need to install them in the right order). After that reboot and choose the new kernel from the grub menu.

If it doesn't work better for you, just reboot again and choose the older kernel. You can remove it if you like using Synaptic, but it doesn't hurt anything to leave it there.


I've been having random freezes as well (seemed to be due to instances of high graphics/memory or "doing too many things at once," though given Linux's multitasking abilities that was hard to believe, but sometimes it would just happen when I would move the mouse suddenly). I couldn't do anything, even ssh into it, and had to do a hard reboot each time. I tried updating the kernel and it hasn't become frozen yet, so I'm giving a tentative thanks for this idea.

---

### Post by michaelzap on 2009-11-12
> **ngtc32 said:**
> I've been having random freezes as well (seemed to be due to instances of high graphics/memory or "doing too many things at once," though given Linux's multitasking abilities that was hard to believe, but sometimes it would just happen when I would move the mouse suddenly). I couldn't do anything, even ssh into it, and had to do a hard reboot each time. I tried updating the kernel and it hasn't become frozen yet, so I'm giving a tentative thanks for this idea.

Then I'll say a tentative "You're welcome!" and hope that we can make it definitive soon. ;)

---

### Post by butters stotch on 2009-11-12
I have (kinda of) confirmed that my freeze is due to deluge.

---

### Post by luke0927 on 2009-11-12
I upgraded the kernel and it took a lot more to get it to freeze but it still froze.....

---

### Post by michaelzap on 2009-11-12
Did you verify that you're running the new kernel?

uname -v
(or just open up the System Monitor and look in the System tab)

You should see the new kernel as an option in your Grub menu when you boot up.

---

### Post by michaelzap on 2009-11-12
> **butters stotch said:**
> I have (kinda of) confirmed that my freeze is due to deluge.

There are ext4 issues with the Karmic kernel that might be related to that (or might not be).

---

### Post by luke0927 on 2009-11-12
I found that command thats what i used to check it....its is 632rc6...but on boot up it went by so fast i didn't see it at first i had to hit esc to see the choices...that was the first one so it booted to it after the upgrade....so far it has only locked up once...I was hammering it pretty good but nothing that didnt' run at 9.04

---

### Post by michaelzap on 2009-11-12
> **luke0927 said:**
> I found that command thats what i used to check it....its is 632rc6...but on boot up it went by so fast i didn't see it at first i had to hit esc to see the choices...that was the first one so it booted to it after the upgrade....so far it has only locked up once...I was hammering it pretty good but nothing that didnt' run at 9.04

Is one crash a lot less than before? One crash is too many, but I suppose it could have been due to something else. Try it for a while and see how it goes, I guess.

---

### Post by luke0927 on 2009-11-13
> **michaelzap said:**
> Is one crash a lot less than before? One crash is too many, but I suppose it could have been due to something else. Try it for a while and see how it goes, I guess.

Yes...i had about 5 all day then about an hour before posting i was running running more apps and it was freezing bad...probably antother 3 or 4 times before i upgraded the kernel.  I need to set up SSH so i can pull the syslog if it happens again...I think i will be able to pull it becasue its just like the desktop freezes but i can still move the cursor but no functions.

---

### Post by luke0927 on 2009-11-13
Just died when launching firefox....so who knows I'll try to stick it out i hate to reinstall 9.04

---

### Post by michaelzap on 2009-11-13
> **luke0927 said:**
> Just died when launching firefox....so who knows I'll try to stick it out i hate to reinstall 9.04

Are you getting Apport pop-ups after restarting telling you that there was a kernel error and asking you to report it? That would be one way to know for sure that these are kernel panics and not something else (such as a bad Flash installation). Anything interesting in var/syslog?

---

### Post by luke0927 on 2009-11-13
No don't get any errors...I'll pull the syslog and see what it says....when i check early yestreday it was saying something about pulseaudio.

---

### Post by boot_sectorz on 2009-11-13
I dual-boot, hate windows but some funny programs never work even in crossover! I couldn't stand the freezing, so I deleted the partition (i can't believe in more than 3 years i had to lose my ubuntu partition!!), clean installed 9.10 and updated all updates. Like a usual XP ritual i have to go through every 4 months.
Installed my programs without using my old stuff. 6hrs on and had my first freeze! 2 hrs later the second one.
I have no idea why. And it seems this time i had no idea it would happen.

My System:

Dell Latitude D630
4GB Ram
250GB HDD
HD Decoder Card
Nvidia 135M graphics
Exaile, aMSN, Pidgin, Firefox and Opera were running.

What is going on with 9.10??!!

---

### Post by gachora on 2009-11-14
Am hooked to Firefox but if this were to be the cause of the crash what is the alternative?

---

### Post by GerdS on 2009-11-14
I have a similar problem with my Samsung P40 laptop.
Ubuntu 9.10 can run for hours and then just freeze from one second to the other without detectable reason.
After freezing the screen contents are intact, the mouse cursor does not work any longer, there is no more hard disk activity and no reaction to any key presses. So I can just press the power button...

After rebooting all works well again, no error message, no hint in log files.

Today I had two freezes, one after the other. After rebooting from the first freeze and restarting firefox the system freezed again while firefox was restoring previously open windows.

Latest news:
While I was away from the PC there was a further freeze, the third for today. The CPU was running so hot that I was not able to reboot the system for several minutes, it shut down itself by BIOS because of overheat. Means the problem overrides all protection schemes of the CPU for preventing overheating!

Regards, Gerd

---

### Post by crjackson on 2009-11-14
> **woohhaa said:**
> Mine is freezing as well. It seems to freeze after the the monitor power saver kicks in. I will close firefox to see if mine does it w/o the browser opened. Like Andreas1 said my fire fox is almost always opened.

I was getting this too, I disabled everything under power saving and it helped, but it eventually still freezes anyway.  Just at longer intervals..

---

### Post by crjackson on 2009-11-14
I've got one desktop and one laptop that are going back to Jaunty.  My wife uses these 2 machines and I'm tired of hearing about Ubuntu instability.

---

### Post by teh603 on 2009-11-14
> **crjackson said:**
> I've got one desktop and one laptop that are going back to Jaunty.  My wife uses these 2 machines and I'm tired of hearing about Ubuntu instability.
That's pretty much what I did. I'm not sure what happened, but its possible that something in Karmic was simply rushed and needed to be tested better.

---

### Post by crjackson on 2009-11-15
Not really rushed, but sometimes when new innovations are implemented unplanned problems come up.  Not many people alpha / beta test (as compared to USERS trying a released distro), so the problems don't really seem so wide spread during the testing phase.  When everyone upgrades and installs however, massive problems rear their ugly heads.

If I were to make a WAG, I'd say it's kernel related or video related.

---

### Post by SuaSwe on 2009-11-15
I had the same problem following upgrading to Karmic - managed to get the most recent kernel to boot into the GUI after quite a bit of tinkering, only to find it freezing after five minutes regardless what I was doing on it (as described in the OP, it would start with one app slowly followed by the rest). Syslog gave no indications of what the problem might be, with the final entry simply listing the last manual input before the freeze. 

In the end I lost patience with it and reverted back to Jaunty - I'm suspecting graphics issues (I'm running the somewhat unfortunate ATI Radeon 200M) and will not attempt upgrading again until I can verify full functionality using the LiveCD, something I should really have done to begin with!

---

### Post by Andreas1 on 2009-11-15
Do any of you have the following wireless device?

```
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection
```

---

### Post by crjackson on 2009-11-15
I can't be 100% sure right now but all indications are that I've solved the problem on one of the desktops.

I installed an older nVidia GeeForce2 card.  I'll know for sue in the next day or so, but it's looking good now.  Also it had nothing to do with Karmic.  I reinstalled Jaunty and got the same results.

---

### Post by crjackson on 2009-11-15
well I spoke too soon.  Locking up again...  I know it's a hardware issue but I having a problem nailing it down.  I feel like there could be a problem with the memory, but it passes memtest86+.

---

### Post by kaarecc on 2009-11-16
Hi,

I'm having a lot of trouble trying to get Karmic to run without freezing. In fact both 9.04 and 9.10 freezes randomly. It seems to be videorelated. When a freeze accurs there are blue dotted lines on the screen, as if it was trying to open a new window and gut stuck in the proces. I have tried disabling compiz, reinstalling video driver, disabling, acpi, installing with ext3. Nothing works. 

It is not at hardware error. XP, suse 11.1, ubuntu 8.04 runs really well on the laptop. No freezes, no crashes whatsoever. On suse it runs with the full eyecandy package, turning cubes and the lot. No problems, except form the fact that i really like Ubuntu...

For now i have reverted to 8.04. it's very stable, but it's not so cool being without openoffice 3.1 and other updated program.

I'm trying to make it work on a Dell Latitude 620, 1,8 ghz core 2 duo, 2 gb ram, 60 mb hd, intel graphics (945 I think), intel wireless (3945), Dell Bluetooth,

Any similar problems on similar hardware out there, anyone? And just as relevant, any fixes, please? :-D

It's just soooooo frustrating.

Kaare

---

### Post by GerdS on 2009-11-17
Maybe I found a hint at least for my system.
Last freeze occured when clicking a button within a website displayed in Firefox starting a Java/Ajax based web chat.
I got the feeling for a Java problem already before and I am now almost sure about it.

It's independent from the actual Java engine installed, so it happens both with Sun Java and the opensource variant.

Not sure yet if it's a pure Java problem or if it is also related to Firefox.

Regards, Gerd

---

### Post by anubhavrocks on 2009-11-17
My computer freezes only after it has woken up from suspend.That too it  does not freeze immediately but it definitely freezes if i use firefox for a while.Somehow SUSPEND+Firefox causes something to trigger the freeze.A cleanly booted up system never froze on me.The other weird thing is that sometime even though the GUI is completely frozen the mouse pointer still responds.I think i need to try ssh'ing into the system once this happens.Will see  the logs and try to make out whats happening.

---

### Post by boot_sectorz on 2009-11-17
Ok what can I be doing to narrow down the problem. I think it really is killing me. 3 freezes a day!!!

---

### Post by kaarecc on 2009-11-17
Well, one thing that works is to get another laptop ;-) I "borrowed" my sons laptop yesterday, a Dell Inspiron 6400. It has a smaller cpu, though, else the rest of the hardware is almost similar. I'm not quite sure it's the same intel grahics chipset. Will check tonight.
 
But, on the Inspiron everything works flawlessly. Full compiz, installing a lot of programs, no crashes while testing (on my latitude, I get a crash within an hour form booting)
 
Just to test some more I downloaded the latest OpenSuse 11.2 and installed it om my crash-ridden latitude 620. No crashes. I will test it further during the next couple of days.
 
If Suse (and Hardy) can do it on my Latitude, why can't Karmic?
 
Regards
 
Kaare

---

### Post by boot_sectorz on 2009-11-17
> **kaarecc said:**
> WIf Suse (and Hardy) can do it on my Latitude, why can't Karmic?

I have been asking myself that the whole week. What seems different? My wife's Latitude D630 seems not to be crushing, and the can't use it to test. It has an Intel graphics and I have Nvidia. So maybe that could be it.

I have had 2 crushes since my last post and all the time I had firefox running. The last crushed was after firefox killed itself. So I wont run firefox for as long as I can and see what really happens. Maybe Shiretoko could be called upon to replace if firefox wont work.

---

### Post by J V on 2009-11-17
> **wayneox said:**
> i was talking on msn earlier n ended up having my whole system freeze [but not freeze] - messages were coming up on empathy, but nothing would respond...
UNR karmic here... Unplugging the LAN pops up a message all right, but all control is gone... from hitting numlock to CTRL+ALT+F1, to CTRL+ALT+Bcksp (Yes its enabled)

controls just stop responding... Karmic is alpha because of this one bug... Canonical needs to stop rushing its 6 month releases and take some time to pick up the slack they created in their mad dash...

---

### Post by kaarecc on 2009-11-17
I have updated the BIOS on my Dell Latitude d620 from A08 to A10. What a difference an upgrade makes... ;)

I can enable all the advanced features in Compiz. The first time ever... No Crashes so far. Will test as much as possible tonight and the next couple of days. I just hope this solves the freeze-thing for me.

I hope it can prove useful for somebody.

Regards

Kaare

---

### Post by boot_sectorz on 2009-11-17
I'm officially lost now. I had firefox totally kicked out. I worked for a straight 3hours with no freeze. My first click on a torrent to run Transmission froze the system. So what is casuing it now, is officially unknown!
I'll keep trying to find one thing and disable it to check if the crush will continue. Not sure how my hard drive will handle it - looks like windoze blue infecting Karmic! :(

---

### Post by groveborn on 2009-11-17
IPv6.  That're was a message about it when I froze. I'm wondering if that's the problem.  Also, I freeze most often when either Empathy or Pidgin are up.  I typically freeze when reading a particular website, but it's not always up, nor has it always even been launched yet.

---

### Post by boot_sectorz on 2009-11-17
I have the latest bios version for Dell Latitude D630. Nothing on that area. The only difference between the laptop I use and the one my partner uses is the Intel Graphics chip - and the fact that I have 4GB ram and she has 2GB! I would actually expect mine to work much better than the other one.

---

### Post by kaarecc on 2009-11-17
#"¤%&%¤#"(/&   nope, bios upgrade only enables compiz-functionality... Just had two crashes after several hours. Not really possible to use it for any kind of production. Maybe the only solution is to buy another laptop... ;)

Regards

Kaare

---

### Post by gpstar on 2009-11-18
mine was freezing all the time. I think I found the problem and tracked it down to the Terminal Screenlets I was using. I've since turned them off and my system has been rock solid so far with no more freezing since.

---

### Post by gpstar on 2009-11-18
well i spoke a bit too soon. system just froze up on me again.

tried the ALT + SysRq + R E I S U B and that did not do anything.

last thing in my syslog to show before the freeze was

```
Nov 18 10:45:01 michael-laptop CRON[11890]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
```

---

### Post by wolfier on 2009-11-19
Similar kind of crashes here.  I wonder if there's an issue opened at launchpad.net.  I came across this very similar issue ([https://bugs.launchpad.net/ubuntu/+bug/479296](https://bugs.launchpad.net/ubuntu/+bug/479296)) but it seems not related, as people here are seeing crashes even without audio played.

Hardware (new stock laptop): Acer Aspire Timeline 1810TZ (Intel Pentium Dual Core SU4100, 4GB DDR2 800, 200GB Ubuntu Karmic partition, Intel 4500MHD graphics, external Dell LCD monitor plugged in through VGA port, external mouse/keyboard plugged into a shared USB port.

Software: Ubuntu Karmic 64-bit stock installation.

Custom setting: I have "xrandr --output LVDS1 --auto --output VGA1 --auto" run once per hour in my crontab.  Reason is, "Display setting" can never set my display properly - I want it mirrored, but use the larger resolution of the external monitor.  The Display setting only allows mirror such that both monitors show the entire desktop.  It's not what I want because the laptop lid will be kept closed whenever it's plugged in.  xrandr gives me that.  (which I think is related)  Putting it in a crontab because before I disabled power saving, I had my laptop set to turning off the screen after some idle time, but the setting is stupid enough to turn off my external monitor, too.

What happened during the hangs: external screen goes to power-saving mode (even though I have it turned OFF in the power setting), and then even if I open the laptop lid, only the mouse pointer can move, but it cannot click on anything.  Both the laptop and the external keyboards are totally unresponsive - NumLock LED doesn't flip, CTRL-ALT-BS (I enabled that) and CTRL-ALT-DEL don't work, CTRL-ALT-F1 doesn't work.  Even when I tried ssh in (have sshd installed and started) it couldn't connect.  No HDD activity.  So the only resolution is to bounce the machine.

Post-mortem inspection shows nothing suspicious in the logs except these:

Xorg.0.log:

(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 65.5 MHz   Image Size:  256 x 144 mm
(II) intel(0): h_active: 1366  h_sync: 1390  h_sync_end 1406 h_blank_end 1406 h_border: 0
(II) intel(0): v_active: 768  v_sync: 770  v_sync_end 774 v_blanking: 776 v_border: 0
**(WW) intel(0): Unknown vendor-specific block f**
(II) intel(0):  AUO

kern.log:

 kernel: [10101.081668] i2c-adapter i2c-2: unable to read EDID block.
 kernel: [10101.081679] i915 0000:00:02.0: HDMI Type A-1: no EDID data
 kernel: [10101.086451] i2c-adapter i2c-2: unable to read EDID block.
 kernel: [10101.086461] i915 0000:00:02.0: HDMI Type A-1: no EDID data
 kernel: [10101.091877] i2c-adapter i2c-4: unable to read EDID block.
 kernel: [10101.091885] i915 0000:00:02.0: HDMI Type A-2: no EDID data
 kernel: [10101.096691] i2c-adapter i2c-4: unable to read EDID block.
 kernel: [10101.096702] i915 0000:00:02.0: HDMI Type A-2: no EDID data
 kernel: [10101.784193] [drm] LVDS-8: set mode  27
 kernel: [10102.123680] [drm] DAC-6: set mode  2c
 kernel: [10102.433082] i2c-adapter i2c-2: unable to read EDID block.
 kernel: [10102.433090] i915 0000:00:02.0: HDMI Type A-1: no EDID data
 kernel: [10102.437587] i2c-adapter i2c-2: unable to read EDID block.
 kernel: [10102.437593] i915 0000:00:02.0: HDMI Type A-1: no EDID data
 kernel: [10102.443133] i2c-adapter i2c-4: unable to read EDID block.
 kernel: [10102.443143] i915 0000:00:02.0: HDMI Type A-2: no EDID data
 kernel: [10102.447622] i2c-adapter i2c-4: unable to read EDID block.
 kernel: [10102.447626] i915 0000:00:02.0: HDMI Type A-2: no EDID data
 kernel: [10102.705620] [drm] DAC-6: set mode  2b
 kernel: [10103.159525] [drm] LVDS-8: set mode  30
 kernel: [10108.507900] i2c-adapter i2c-2: unable to read EDID block.
 kernel: [10108.507906] i915 0000:00:02.0: HDMI Type A-1: no EDID data
 kernel: [10108.525177] i2c-adapter i2c-2: unable to read EDID block.
 kernel: [10108.525186] i915 0000:00:02.0: HDMI Type A-1: no EDID data
 kernel: [10108.529792] i2c-adapter i2c-4: unable to read EDID block.
 kernel: [10108.529796] i915 0000:00:02.0: HDMI Type A-2: no EDID data
 kernel: [10108.541150] i2c-adapter i2c-4: unable to read EDID block.
 kernel: [10108.541159] i915 0000:00:02.0: HDMI Type A-2: no EDID data

and a couple of "pulseaudio: ratelimit.c XX events suppressed", but I don't think it's relevant, as during all the crashes I have not been playing audio.

pm-powersave.log: (i don't think it's relevant, but what do I know)

/usr/lib/pm-utils/power.d/95hdparm-apm false: 
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
success.
/usr/lib/pm-utils/power.d/anacron false: success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.
/usr/lib/pm-utils/power.d/95hdparm-apm false: 
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
success.
/usr/lib/pm-utils/power.d/anacron false: start: Job is already running: anacron
success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.
/usr/lib/pm-utils/power.d/95hdparm-apm false: 
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
success.

syslog (these messages weren't logged around the time of the crashes, but still suspicious):
 pulseaudio[1757]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
 pulseaudio[1757]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
 pulseaudio[1757]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

lsmod output:
Module                  Size  Used by
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
cryptd                  8008  0 
aes_x86_64              8992  0 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
ppdev                   8232  0 
snd_hda_codec_intelhdmi    14880  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  4 
snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
arc4                    2144  2 
ecb                     3296  2 
joydev                 13088  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
iwlagn                124832  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore               133248  1 iwlagn
snd_timer              26992  2 snd_pcm,snd_seq
psmouse                57124  0 
serio_raw               6596  0 
acer_wmi               18504  0 
lp                     11908  0 
uvcvideo               65260  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              210104  2 iwlagn,iwlcore
videodev               43360  1 uvcvideo
led_class               5256  2 iwlcore,acer_wmi
snd                    77096  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
atl1c                  36516  0 
v4l1_compat            16804  2 uvcvideo,videodev
soundcore               9088  1 snd
iptable_filter          3872  0 
btusb                  14260  2 
v4l2_compat_ioctl32    13344  1 videodev
parport                40528  2 ppdev,lp
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
ip_tables              21200  1 iptable_filter
cfg80211              109144  3 iwlagn,iwlcore,mac80211
x_tables               25832  1 ip_tables
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
usb_storage            65952  1 
i915                  246984  3 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
usbhid                 43968  0 
video                  23612  1 i915
output                  3680  1 video
intel_agp              32816  2 i915


Hope it's helpful.  On the old Socket 754 machine I upgraded from, even with Nvidia's proprietary drivers, it was rock solid from Edgy to Jaunty.  It's a sad day to see Ubuntu stability has stooped to this level.

---

### Post by wolfier on 2009-11-19
Another instance - I opened the laptop lid quickly enough to prevent another freeze.

Here's the log:

i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
ACPI Error (dswload-0790): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog 20090521 psloop-227
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.WMID.WMBA] (Node ffff88013ba4f180), AE_ALREADY_EXISTS
ACPI: Marking method WMBA as Serialized because of AE_ALREADY_EXISTS error
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] DAC-6: set mode  2d
[drm] LVDS-8: set mode  34
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] DAC-6: set mode  33
[drm] LVDS-8: set mode  38
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] DAC-6: set mode  39
pulseaudio[1757]: ratelimit.c: 1 events suppressed
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] LVDS-8: set mode  3b
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] DAC-6: set mode  35
[drm] LVDS-8: set mode  3d
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] DAC-6: set mode  3c
[drm] LVDS-8: set mode  41
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.WMID.WGDS] (Node ffff88013ba4ee40), AE_TIME
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.WMID.WMBA] (Node ffff88013ba4f180), AE_TIME
[drm] DAC-6: set mode  3e
[drm] LVDS-8: set mode  43
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
[drm] DAC-6: set mode  42
[drm] LVDS-8: set mode  47
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-2: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-1: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
i2c-adapter i2c-4: unable to read EDID block.
i915 0000:00:02.0: HDMI Type A-2: no EDID data
pulseaudio[1757]: ratelimit.c: 4 events suppressed

---

### Post by boot_sectorz on 2009-11-19
Almost 24hrs without a crush. I did not change anything mahor apart from using chrome-browser and not firefox and using VLC Media Player and not Exaile. But I did this same thing some days ago and it still crushed/ froze!
Has any one been able to isolate the problem? I'm sure we can work from that isolation or anything close to find our way back to Ubuntu's stability. I dread moving backwards.

---

### Post by timgood on 2009-11-19
> **boot_sectorz said:**
> Almost 24hrs without a crush. I did not change anything mahor apart from using chrome-browser and not firefox and using VLC Media Player and not Exaile. But I did this same thing some days ago and it still crushed/ froze!
Has any one been able to isolate the problem? I'm sure we can work from that isolation or anything close to find our way back to Ubuntu's stability. I dread moving backwards.

No able to isolate but maybe to point out that this must be a hardware related problem - running Karmic on 2 machines here, mine is a fairly recent AMD Quadcore Machine with 4GB RAM and fairly recent NVidia Graphics and the system is very stable and I'm not experiencing any freezing. However my wife's machine, older AMD 64 processor, 1GB RAM and older NVidia card (using driver 173) now freezes several times per day (was rock solid under 9.04). So must be hardware related in some way?

---

### Post by boot_sectorz on 2009-11-19
> **timgood said:**
> No able to isolate but maybe to point out that this must be a hardware related problem - running Karmic on 2 machines here, mine is a fairly recent AMD Quadcore Machine with 4GB RAM and fairly recent NVidia Graphics and the system is very stable and I'm not experiencing any freezing. However my wife's machine, older AMD 64 processor, 1GB RAM and older NVidia card (using driver 173) now freezes several times per day (was rock solid under 9.04). So must be hardware related in some way?

Would be easier to isolate hardware in my case then. The differences on the two machines that I use are fairly easy to find.

Wife and I both use Dell Latitude D630 laptops.

Hers:
Intel Graphics (X3100)
2GB Ram
160GB Hard drive

Mine:
Nvidia 135M graphics
4GB Ram
250GB Hard drive
Broadcom BCM70012 Video Decoder card

So could it be nvidia, or the broadcom hd card?

---

### Post by michaelzap on 2009-11-19
How many of you have tried running the new kernel, as explained here?
[http://ubuntuforums.org/showpost.php?p=8279042&postcount=28](http://ubuntuforums.org/showpost.php?p=8279042&postcount=28)

---

### Post by kaarecc on 2009-11-19
So far I have been running Karmic for almost 2 days without crashes. As mentioned earlier upgrading the bios made it possible to enable compiz. But it still crashed but not quite so often.

Since then I've done only two things. Disabled anything not needed in bios, like modem, serial and parallel ports and been aware of possible overheating. (though the latter might be far fetched... I know) 

thinking about it, I'm quite sure that some of the crashes happened either when lying on the couch or in bed. Both cases includes not so good cooling and ventilation compared to using the laptop on a table. I came across the possibility after installing Gkrellm and enabling the temperature sensor. Just prior to a freeze the temperature rose very quickly to way above 75 C and it froze. A reboot resulted in a freeze within minutes. 

Just an idea, but it is possible that more processes run on karmic compared to Hardy and thus forces the cpu to work harder = getting warmer?

All in all, no crashes so far, despite stresstesting with lots of videos, gaming and so on...

Regards 

Kaare (hoping for the crash-free state to last long :))

---

### Post by luke0927 on 2009-11-19
I'm running the new kernel and still freezing...i hate to blow everything away and go to 9.04 but its almost unbearable

---

### Post by michaelzap on 2009-11-19
> **luke0927 said:**
> I'm running the new kernel and still freezing...i hate to blow everything away and go to 9.04 but its almost unbearable

I remembered that you'd tried it and it didn't fix your problems, so there are obviously more than one cause for this. Seems like it would be helpful to eliminate the folks for whom the new kernel fixes everything (like me). Who else has tried the new kernel and still has frequent kernel panic crashes?

---

### Post by karlkuehn on 2009-11-19
> **luke0927 said:**
> I'm running the new kernel and still freezing...i hate to blow everything away and go to 9.04 but its almost unbearable

Same here. I'm about done waiting for a fix on this one. I haven't changed a thing on my system since upgrading to Karmic, aside from shutting down every power-saving feature I can find, and the thing is randomly locking on me while I'm using it as well.

As much as I hate the idea, I'm going to upgrade back to Jaunty. This is a fairly serious bug, IMO, as we're now having to resort to possible/probable hardware damage to reboot the frozen machine all the time.

I was happy and super stable with Jaunty, so I've got to go back to it, this machine is too important in my work flow.

*crosses fingers for 10.04*

I was reading a bunch of bragging about how fast the boot time was going to be in the next version. I'd be happy to see it stay where it was in Jaunty. Any boot time we've saved has been lost in the frequency of reboots.

Still love Canonical, though! Keep it up, guys. :D

---

### Post by michaelzap on 2009-11-19
@luke0927 and karlkuehn: What video cards are you using?

---

### Post by karlkuehn on 2009-11-19
> **michaelzap said:**
> @luke0927 and karlkuehn: What video cards are you using?

 

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
**[COLOR=DarkRed]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)[/COLOR]**
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)

---

### Post by boot_sectorz on 2009-11-20
I have upgraded to the new kernal (2.6.32-020632rc7-generic) release candidate 7 to see what will result regarding the random freezing. So far it seems ok (5hrs and counting)

---

### Post by boot_sectorz on 2009-11-20
In the end, all comes down to one thing - Ubuntu 9.10 is just freezing regardless of which kernal I use. :(

---

### Post by boot_sectorz on 2009-11-20
Can we all list our hardware so that we can at least have an idea what we have in common so that we can narrow down as to what we think is freezing the system.

I suspect Nvidia Graphics and BCM70012 Video Decoder as my wife's laptop does not have these and it does not freeze.

Output of lshw is:
```
xxx-linux                 
    description: Portable Computer
    product: Latitude D630
    vendor: Dell Inc.
    serial: XXXXXXX
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-3100-1054-8058-C8C04F393258
  *-core
       description: Motherboard
       vendor: Dell Inc.
       physical id: 0
       serial: XXXXXXX              .
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A16 (07/14/2009)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 0000000000000000
             physical id: 0
             serial: 00000000
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 0000000000000000
             physical id: 1
             serial: 00000000
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:f2000000-f6efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Quadro NVS 135M
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff(prefetchable) memory:f2000000-f3ffffff ioport:ef00(size=128) memory:f4000000-f401ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f20(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:f6ffc000-f6ffffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f1b00000-f1ffffff memory:f0000000-f01fffff(prefetchable)
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: BCM70012 Video Decoder [Crystal HD]
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f1bf0000-f1bfffff memory:f1c00000-f1ffffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096) memory:f1a00000-f1afffff memory:f0200000-f03fffff(prefetchable)
           *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth2
                version: 01
                serial: 00:1f:3a:18:f9:27
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f1afc000-f1afffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:4000(size=4096) memory:f1900000-f19fffff memory:f0400000-f05fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:1c:96:12
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:29 memory:f19f0000-f19fffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f80(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f60(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:5000(size=4096) memory:f1800000-f18fffff
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:f1800000-f1800fff ioport:5000(size=256) ioport:5400(size=256) memory:f0800000-f0bfffff memory:f0c00000-f0ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64
                resources: irq:19 memory:f18ff000-f18fffff memory:f18fe800-f18fefff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)
           *-cdrom
                description: DVD writer
                product: DVD+-RW DS-8W1P
                vendor: PBDS
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BD1C
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=32) memory:f6ffb800-f6ffbfff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54252
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BBFO
                serial: 080401BB0F00WDD63PTC
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cce6cce6
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c606ee0a-df06-1d47-bdf1-b5292aceddb3
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-06-17 21:11:39 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/B88895F08895AD7E
                   version: 3.1
                   serial: 80772367-5df8-6441-821a-3e82d6773ac9
                   size: 137GiB
                   capacity: 137GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-04-22 07:24:57 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 35GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1584MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6ffb700-f6ffb7ff ioport:10c0(size=32)
  *-battery
       product: DELL PC76485
       vendor: Samsung SDI
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V
```

---

### Post by michaelzap on 2009-11-20
Here's what I get:
```
vitxo                     
    description: Notebook
    product: INVALID
    vendor: Lenovo
    version: Lenovo IdeaPad Y530
    serial: xxx
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=00F2B6DD-2749-DE81-2A4A-00248C6F4516
  *-core
       description: Motherboard
       product: INVALID
       vendor: Lenovo
       physical id: 0
       version: 10CN41WW
       serial: xxx
       slot: Lenovo
     *-firmware
          description: BIOS
          vendor: Lenovo
          physical id: 0
          version: 10CN41WW (02/25/2009)
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GH
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:d3c00000-d3ffffff memory:c0000000-cfffffff(prefetchable) ioport:d120(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d4100000-d41fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d0c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:d0a0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d080(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:d4204c00-d4204fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d4200000-d4203fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:c000(size=4096) memory:d2800000-d3bfffff memory:9c000000-9c1fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:24:8c:6f:45:16
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:30 memory:d2800000-d280ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:b000(size=4096) memory:d1400000-d27fffff memory:9c200000-9c3fffff(prefetchable)
           *-network
                description: Wireless interface
                product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:fa:ce:85:44
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.151 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:29 memory:d1400000-d1401fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:a000(size=4096) memory:d0000000-d13fffff memory:9c400000-9c5fffff(prefetchable)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d060(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d040(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d020(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d4204800-d4204bff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:d4000000-d40fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 3
                bus info: pci@0000:06:03.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:20 memory:d4000000-d40007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 3.1
                bus info: pci@0000:06:03.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:21 memory:d4000a00-d4000aff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 3.2
                bus info: pci@0000:06:03.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:d4000900-d40009ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 3.3
                bus info: pci@0000:06:03.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:d4000800-d40008ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:d110(size=8) ioport:d100(size=4) ioport:d0f0(size=8) ioport:d0e0(size=4) ioport:d000(size=32) memory:d4204000-d42047ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54323
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FB4O
                serial: 090422FB6432CEG16W4A
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c3ffc3ff
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: fc213242-97c3-9542-b379-b57bb41f98dd
                   size: 156GiB
                   capacity: 156GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-05-25 17:58:15 filesystem=ntfs state=clean
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: dde54b5f-5e4a-4532-a426-14015bc515e7
                   size: 97GiB
                   capacity: 127GiB
                   capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-06-20 17:07:27 filesystem=ext4 label=ubuntu modified=2009-10-29 19:30:15 mounted=2009-10-28 11:59:37 state=clean
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 29GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 93GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4118MiB
                      capabilities: nofs
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 38c5a814-fe4c-eb4b-a815-fdd8ba0aaa3d
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-05-25 18:12:43 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: S805
                capabilities: removable audio cd-r cd-rw dvd
```

---

### Post by boot_sectorz on 2009-11-21
Seems you have Intel graphics and I have Nvidia which I suspected would be the problem. 

Can we have more people please posting their hardware so we can rule out hardware or pin-point the hardware which could be causing this.

Thanx

---

### Post by boot_sectorz on 2009-11-21
Ok. Windows will do for now. Need this sorted out urgently. Anyone with hints should post

---

### Post by GerdS on 2009-11-21
I found a solution for my problem. It's really related to Firefox. I installed and used Opera for several days now, also with Java and no further freezes.
Also Flash video performance is dramatically better there compared to Firefox, although it is the same plugin version from Adobe.

Regards, Gerd

---

### Post by gupi-gupi on 2009-11-21
Hi I'm having the random issue too,9.10 32 bit. what I get is after suspend the gdm screen comes back showing the desktop background clear and simple, without icons or anything else, no chance to restart X have to do a hard shat down each time. I'm wandering if other have this isuue with the desktop image showing up?
anyway here is my hardware:
nVidia Corporation NV43 [GeForce 6600] (rev a2)
driver: Nvidia 173.14.20
I can post xorg.conf if needed
anyone with similar issues solved?

---

### Post by Andreas1 on 2009-11-21
> **boot_sectorz said:**
> Can we have more people please posting their hardware so we can rule out hardware or pin-point the hardware which could be causing this.

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

---

### Post by groveborn on 2009-11-21
I always have "eth0: no IPv6 routers present" right before I freeze. I'm really starting to suspect that's the culprit.  I've set my IPv6 to be local only, hoping that will fix it.

---

### Post by elventear on 2009-11-24
In my case, every time I plug an external USB drive, the system will freeze.

---

### Post by kaarecc on 2009-11-24
I've tracked my freezing problem down to an overheating issue. Haven't been able to solve it, but it is described here:
 
[http://ubuntuforums.org/showthread.php?t=1315065&page=2](http://ubuntuforums.org/showthread.php?t=1315065&page=2)
 
and here
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
 
Until it's solved I switch laptop with my son, though his Inspiron is a bit bulkier than my Latitude.
 
Regards
 
Kaare

---

### Post by Terrydlm on 2009-11-25
> **GerdS said:**
> I found a solution for my problem. It's really related to Firefox. I installed and used Opera for several days now, also with Java and no further freezes.
Also Flash video performance is dramatically better there compared to Firefox, although it is the same plugin version from Adobe.

Regards, Gerd

I agree that this seems to be a Firefox issue. I have done the same as you, i used Firefox & after a few minutes i get a complete system freeze. The only way to recover is to switch off the server and restart it. I tried using Opera and no problem. The server is absolutely fine. 

Installed some updates, tried Firefox again and bang, system freeze!

---

### Post by boot_sectorz on 2009-11-25
> **kaarecc said:**
> I've tracked my freezing problem down to an overheating issue. Haven't been able to solve it, but it is described here:
 
[http://ubuntuforums.org/showthread.php?t=1315065&page=2](http://ubuntuforums.org/showthread.php?t=1315065&page=2)
 
and here
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
 
Until it's solved I switch laptop with my son, though his Inspiron is a bit bulkier than my Latitude.
 
Regards
 
Kaare

My fan is working properly. So I will uninstall firfox completely and see how it goes.

---

### Post by komserbash on 2009-11-25
i think i solved this problem 
first:
we remove the networkmanager and then install wicd
while you are installing wicd you need this package :[http://packages.ubuntu.com/karmic/python-urwid](http://packages.ubuntu.com/karmic/python-urwid)
download on the desktop these files
```
sudo aptitude remove network-manager
cd Desktop
sudo dpkg -i <python......>
sudo dpkg -i <wic.....>
```then reboot.

---

### Post by the-spear on 2009-11-25
how does network-manager have anything to do with the random freezing?

i'm downloading [this patched kernel]("http://people.canonical.com/%7Eapw/lp451337-karmic/"), which according to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337") has seen the problem fixed for some people.

_** UPDATE:**_

I downloaded the patched kernel, and i am pleased to report that so far it has fixed my problem. I was just able to watch a youtube video in fullscreen without it hanging the comp. I'm still testing and will report back.

```
lshw output:

longspear
    description: Notebook
    product: HP Compaq nc6400 (399279R-999)
    vendor: Hewlett-Packard
    version: F.0B
    serial: USH65100MB
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=1DF89452-0092-DB11-0084-98B70C5AAD29
  *-core
       description: Motherboard
       product: 30AD
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 56.34
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68YCU Ver. F.0B (09/05/2007)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2500  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U10
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: 0000000000000000
             physical id: 0
             serial: 00000000
             slot: DIMM #1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T6554CZ3-CE6
             vendor: CE00000000000000
             physical id: 1
             serial: F54A02E7
             slot: DIMM #2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f4600000-f467ffff ioport:4000(size=8) memory:e0000000-efffffff(prefetchable) memory:f4680000-f46bffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f4700000-f477ffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:f4780000-f4783fff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:5000(size=4096) memory:f4100000-f41fffff memory:64000000-641fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 21
                serial: 00:16:d4:99:4d:6b
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5753m-v3.56 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:f4100000-f410ffff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:6000(size=4096) memory:f4000000-f40fffff memory:64200000-643fffff(prefetchable)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wlan0
                version: 02
                serial: 00:18:de:7a:40:e7
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=10.198.0.199 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:27 memory:f4000000-f4000fff
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=8192) memory:f0000000-f3ffffff memory:64400000-645fffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:4020(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:4040(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4060(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4080(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:f4784000-f47843ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:7000(size=4096) memory:f4200000-f45fffff memory:60000000-63ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:f4200000-f4200fff ioport:7000(size=256) ioport:7400(size=256) memory:60000000-63ffffff(prefetchable) memory:68000000-6bffffff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:18 memory:f4201000-f4201fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:22 memory:f4202000-f42020ff
           *-communication UNCLAIMED
                description: Communication controller
                product: PCIxx12 GemCore based SmartCard controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:f4203000-f4203fff memory:f4204000-f4204fff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:40a0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8032GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AS11
                serial: 76FV5227S
                size: 74GiB (79GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8f8002b1
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 2999db77-3ffd-4a6d-8b61-65f85bda4d9e
                   size: 47MiB
                   capacity: 47MiB
                   capabilities: primary journaled extended_attributes ext3 ext2 initialized
                   configuration: created=2009-11-25 01:49:45 filesystem=ext3 modified=2009-11-25 21:37:16 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback mounted=2009-11-25 21:31:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 45GiB
                   capacity: 45GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3812MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 13GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 27GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 2a4e017d-e2d9-894a-a980-6ba85dc3842e
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-09-29 17:53:38 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4083N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HP13
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 5000BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.75
             serial: WD-WXA0A59R0457
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=44fdfe06
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/BIBLIOTECA
                version: FAT32
                serial: 3a17-6d40
                size: 465GiB
                capacity: 465GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
```

---

### Post by komserbash on 2009-11-25
i don't know patch i didn't try it

---

### Post by a6jarvi on 2009-11-26
My comp, too, has been randomly freezing. I'm using Kubuntu 9.10 (with some added repositories).

When the machine freezes, there's absolutely nothing you can do: mouse doesn't move, keyboard does nothing, if I was playing music it will loop last 0,1 seconds, on screen there is no any tearing or glitches. It's just totally frozen.

I usually don't play music on background, and Kubuntu has frozen while not using Firefox. I have desktop effects disabled. I don't have an Intel graphic chip or wlan cards, but I do connect to internet via my Nokia 5800 (using USB cable).

lspci:
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
```

I just updated to the latest RC kernel (2.6.32-rc8 ). I will be reporting back whether Kubuntu is still freezing or not.

---

### Post by boot_sectorz on 2009-11-29
I have had the laptop working without freezing for 3 days. Only froze once since i removed firefox. Thinking I should try the patched kernal, but only if google chrome wont perform as good as firefox.
I can see that people are slowly sorting the problem but without pin-pointing to the exact problem. Thats strange!

---

### Post by wolfier on 2009-12-01
From my symptoms, it looked like a power management issue, so I used acpi_listen to see what goes on.

It turned out that with the lid closed, my notebook keeps sending the LID event to acpid randomly.

Knowing this, the fix is easy:  sudo chmod -x /etc/acpi/lid.sh

A few hours and no sudden blank screen yet.

Will see how it goes.

---

### Post by cyb3rkn19ht on 2009-12-03
I am having random freezes too. There is no pattern, it can happen right when I power up the computer or after it has been on for hours.
When it freezes the screen turns into a picture, all input and output stops, music stops. I can't even ssh into my machine.
I was having problems with Banshee using all the cpu. I would ssh in and kill Banshee to get my computer back.

I am running on:
Karmic Kernel 2.6.31-15-generic
GNOME 2.28.1
AMD Athlon XP1600+
xfce session with Compositor

---

### Post by Zenguy on 2009-12-03
I installed Karmic 64 bit and had three hangs on the first day. I figured it was a 64 bit issue, so I dropped back to Karmic 32 and have experienced at least one hang.

Intel Quad Core Q6600
3 GB RAM
EXT4 on / and home

When my system hangs up, the mouse pointer moves just fine, but it does not respond to mouse clicks. The keyboard is also non-functional. I have to kill the power to shutdown the system.

---

### Post by 0xCAFE on 2009-12-04
Maybe I've something what will help you. Some of you, I new in Linux, but I read tons articles and forums about this issue. It seems that different things cause this problem on different computers. Mine probably was related to... Flash plug-in to Firefox. So it seemed to related fo Firefox itself or network. 

My configuration is:
Kubuntu 9.10 x64 using ext4
Core 2 2.5Ghz, GeForce 8600GS, 4GB RAM
There's no way to freezing my notebook by crontab or something similar. And I Firefox is running almost always. 

For me works simply: installing Gnash through Software Manager, uninstalling... Gnash, uninstalling Flash-nonfree with Mozilla plugin for it, installing Flash-nonfree again. That's it. I'm working for a couple of hours and I haven't freezing at all. Before I had it more often one per hour. I supposed my problem it solved, although I'm not sure in 100%.

Try it. If it would work somebody of you, maybe somebody who knows Linux better could analyze this :) Maybe same reinstalling of Flash-nonfree could solve problem? Maybe it's about Klash (I've no idea what's that)?

Long description what I did.
I've tried many ideas to solve issue with freezing. But nothing wasn't work, Ii gave up and begun to solve problem with... flash plug-in. Youtube HD and some embedded flash movies wasn't work. Also more sophisticated flash apps, i.e. [www.scribd.com](www.scribd.com) sometimes didn't "let to launch" me PDF viewer or recognize my notebook as... mobile phone. Chrome/Opera hasn't this problems. Some guy Polish forum indicate that using some alternate Flas plug-in could solve the problem, i.e Gnash. I'm new in Linux and was really, really suprised. Why the hell I supposed use sth alternative? Especially sth like Gnash that support fully only SWF7 and even not all ActionScript 2... But I was a lil bit desperated. 

I launched Software Manager, installed Gnash. "Installer" removed a few thing: gstreamer(something), Klash and sth more. After that I launched YouTube HD, but I wasn't work to well, notified errors - lack of codecs... I was really dissapointed, so uninstall it. Again installer removed Klash. I removed Flash and installed again. Now everything works: YT HD, Scribd.com, flash games. No freezing.

---

### Post by alanjohnsmith on 2009-12-04
Just adding my name to the "please create a proper fix for this" list. It's logging off about every ten minutes at the moment!
Unlike my netbook, using the Karmic netbook remix, has no such problems.
(Sorry, am too technically ignorant to list the useful stuff about what hardware I'm using!)

---

### Post by boot_sectorz on 2009-12-06
I have been away from ubuntu for some days now. I saw 2.6.31-16-generic (#52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009) kernel so updated it and have not seen a freeze for almost a day of non-stop running.
I have even re-installed firefox which I removed to see if any improvement will come out of it.
Will report how it goes ...

---

### Post by ghlargh on 2009-12-07
I had severe problems with freezing in 9.10, for me it seems pretty clearly linked to wireless internet connection activity.

If i use internet "normally" it can work for half an hour or an hour, but the computer freezes almost instantly (within a couple of minutes, several tries) if i try to download a large file while i have been running the same large download for an hour with wired internet now.


So another temp-fix in the list of fixes might be to turn off wireless internet and see if that works...

Unless a permanent fix is provided in the next few days though, i am probably going to have to install 9.04 again.

Edit: It's now been going for 5 hours with no problems, so i'd say it's probably the wlan for me.

---

### Post by boot_sectorz on 2009-12-09
Its almost 3 days without a freeze since I upgraded the kernel. Hope all goes well from here.:)

---

### Post by Lyleb on 2009-12-09
The sure-cure that I implimented was to re-install 9.04.

Worked like a charm.

---

### Post by damipereira on 2009-12-21
Hi
I'm an arch user and I was having the same issue

[drm:i915_gem_execbuffer] *ERROR* Execbuf while wedged
this seems to be the problem

I've read somewhere that it might be caused by xf86-video-intel 2.9.99.902 (don't know how the ubuntu package is called) so I've downgraded to 2.9.1 and I don't see any freeze yet since a few hours ( it happened every hour to me).
Up to a few days ago I'd been using chakra (arch with kdemod and other stuff) which has the same repository than arch. Everything was working ok. I decided to go back to pure arch and formatted and when I got everything up and running this problem started.
I had the same versions of packages installed, except for the xf86-video-intel of which I installed the testing version by mistake. downgrading it solved my problem in arch I hope this helps someone even if it's in ubuntu.
This post has also been useful to me, thanks :)
PD:sorry for my english, specially typos hehe

---

### Post by rockyjones on 2009-12-26
I upgraded to 2.6.31-16-generic and still had freezes on my Thinkpad T-60.  Tried many things and finally decided to update to the 2.6.32 kernel and it seems to have completely eliminated the freezes for me.  I used the following info to update:

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

I've run for three days with no freezes and before I did the upgrade, I couldn't use the machine over an hour without having to reboot.  Everything seems to work fine with this kernel.

---

### Post by pompiuses on 2009-12-29
> **rockyjones said:**
> I upgraded to 2.6.31-16-generic and still had freezes on my Thinkpad T-60.  Tried many things and finally decided to update to the 2.6.32 kernel and it seems to have completely eliminated the freezes for me.

Unfortunately it did not fix the freeze problems on my computer :(. Perhaps improved it a bit, but it still freezes after about an hour.

---

### Post by pompiuses on 2009-12-29
> **pompiuses said:**
> Unfortunately it did not fix the freeze problems on my computer :(. Perhaps improved it a bit, but it still freezes after about an hour.

Looks like there's a cure afterall :). Disabling Compiz and installing the Xorg intel driver to 2.4 fixed it completely. So at least on my Dell Dimension 2400 the problem was graphics related.

Following this post:
[http://ubuntuforums.org/showpost.php?p=8341830&postcount=15](http://ubuntuforums.org/showpost.php?p=8341830&postcount=15)

---

### Post by boot_sectorz on 2009-12-29
> **rockyjones said:**
> I upgraded to 2.6.31-16-generic and still had freezes on my Thinkpad T-60.  Tried many things and finally decided to update to the 2.6.32 kernel and it seems to have completely eliminated the freezes for me.  I used the following info to update:

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

I've run for three days with no freezes and before I did the upgrade, I couldn't use the machine over an hour without having to reboot.  Everything seems to work fine with this kernel.

Been 24hrs without a freeze. Hope i can now work without worries.

Thanx!!!

---

### Post by Reno II on 2009-12-29
> **elventear said:**
> In my case, every time I plug an external USB drive, the system will freeze.

similar for me, repeated freeze when I plugged my usb camara in.

---

### Post by boot_sectorz on 2009-12-30
> **boot_sectorz said:**
> Been 24hrs without a freeze. Hope i can now work without worries.

Thanx!!!

Hopeless... froze 3 times in the last one hour. Removed Nvidia 185 and gone back to 173!

Getting used to 7 now and hoping it is fixed soon.

---

### Post by rockyjones on 2009-12-30
Did you try 2.6.32 or just change out your video card?



Quote:
Originally Posted by boot_sectorz View Post
Been 24hrs without a freeze. Hope i can now work without worries.

Thanx!!!
Hopeless... froze 3 times in the last one hour. Removed Nvidia 185 and gone back to 173!

Getting used to 7 now and hoping it is fixed soon.

---

### Post by gr3gwood on 2009-12-30
Struggled with freezes for a few weeks now. Could not isolate cause. Switching off compiz did not help. No meaningful log data (seemingly random). Even seemed to freeze in grub! or soon after. 

Changed software sources to pre-release updates and updated kernel to 2.6.31-**17** and no freezes in 6 hours.  Hurray!

Update notes list a fix to wobbly windows that cause a freeze but I dont know if that is related???

Hope this helps someone

---

### Post by boot_sectorz on 2009-12-31
> **rockyjones said:**
> Did you try 2.6.32 or just change out your video card?


I have 2.6.32-020632-generic. Which started freezing after 24hrs. So I removed the graphic drivers, and it still freezes. I have no idea what else I should try. I'm worried the Hard drive may be spoilt but cold-booting every time it freezes.

I would have loved to remain on 9.04 if i knew it would be this much a pain! I had no problems in beta versions of 9.10 and that really has confused me.

Thanx for your concern and I appreciate any help.

Thanx

---

### Post by boot_sectorz on 2009-12-31
Maybe its the software I'm running...

I have CrossOver 8 with MS Office 2007, PhotoShop and IE. I get flash video errors in Google Chrome browser, but have not paid much attention to them till now. Has anyone running these experienced any of the freezing episodes?

Thanx

---

### Post by rockyjones on 2009-12-31
This does seem to be a difficult bug to understand.  I still have not had any freezes after updating to 2.6.32 (almost a week now) so that definitely fixed the problem for me but it doesn't seem to fix the problem for everyone.  

Additionally, since I have only had to "fix" one of my four machines (1 laptop (the problem machine), 1 netbook, and two desktops - all running either Mint 8 or Ubuntu 9.10), the bug certainly seems to be related to a particular hardware configuration.


> **boot_sectorz said:**
> Maybe its the software I'm running...

I have CrossOver 8 with MS Office 2007, PhotoShop and IE. I get flash video errors in Google Chrome browser, but have not paid much attention to them till now. Has anyone running these experienced any of the freezing episodes?

Thanx

---

### Post by boot_sectorz on 2010-01-14
Ok realized my hard drive might be in trouble due to the constant cold-boot after every freeze. So I formatted the ubuntu partition and re-installed 9.10 (after a 10.04 failure to boot). Its been 4 days without a freeze. I'm running 2.6.31-18-generic.
Will keep informed if I run into trouble.

Thanks for all the help - keeping my fingers crossed

---

### Post by PokeParadox on 2010-01-14
Well I'm now back in Karmic.
What fixed my random crashing was reverting to the 173.14.20 Nvidia drivers.

---

### Post by boot_sectorz on 2010-01-17
7 Days and no freeze. So I think I have sorted out my problem. What did I do?

- Formated the partition
- Re-installed Karmic Kaola
- Installed Nvidia 173 (not 185)
- Removed Cairo-Dock (safety and scared to install it)
- The rest is the same!

---

### Post by woodmaster on 2010-01-23
> **pompiuses said:**
> Looks like there's a cure afterall :). Disabling Compiz and installing the Xorg intel driver to 2.4 fixed it completely. So at least on my Dell Dimension 2400 the problem was graphics related.

Following this post:
[http://ubuntuforums.org/showpost.php?p=8341830&postcount=15](http://ubuntuforums.org/showpost.php?p=8341830&postcount=15)

+1  Everything works great now.  Full Compiz effect, using my swap, RAM, and CPU properly and :DNO MORE RANDOM CRASHES!!!!!:D  I almost gave up on Ubuntu till this.  It is a great OS.  Does all I need and more now.  I am really overjoyed to have it fixed!!!  This should have a HowTo.  What was really tough was figuring out what was causing the crashes.  It seems indeed, they were graphics related.  What told me this for sure was that I could ssh and ```
/etc/init.d/gdm restart
```would restart gnome like nothing ever happened.  Now on to playing with my new desktop effects I knew my computer should've been able to utilize.  Dell Dim 2400 here also.  P4 2.66GHz-2Gig DDR SDRAM([www.memory-up.com](www.memory-up.com)) VGA Intel82845GL integrated chipset.

---

### Post by a6jarvi on 2010-01-24
The freezes have gotten a little less frequent, but every now and then they still happen. I'm currently using kernel 2.6.32-020632rc8-generic (and I have the KDE 4.4 beta packages installed), and Kubuntu has frozen a couple of times while watching videos on Youtube.

It would be understandable that with beta kernel, flash and KDE, there would be problems. But I have a Kubuntu server with only the default repositories enabled and it's freezing, too...

---

### Post by ThinkEntropy on 2010-01-26
I think its kind of interesting that so many people could have random freezes for so many different reasons.  I've been following this thread since its inception and I was sure everyone was suffering from more or less the same demons...not so apparently.

I installed Karmic on my desktop (x64) as soon as it came out and my computer would freeze constantly.  Sometimes it'd stay alive for an hour or so, other times it'd freeze just minutes after booting.  Then I decided to try installing Karmic on my Dell Latitude E5400 (also x64) and zero problems.  None.  I mean, everything worked right out of the box which I thought was amazing.

But my desktop still doesn't work with 9.10.  I can get the thing into a hard freeze just moving the mouse around with nothing else open.  I've tried disabling Compiz, closing all unnecessary programs, upgrading to the newer 2.6.32 kernel, turning off wireless, and nothing works.  The only evidence I've found that indicates there a problem (aside from the freezing, lol) is my /var/log/syslog reported, "Clocksource tsc unstable".  I know this has to do with frequency scaling, but beyond that I'm lost.  

Anyway, I don't expect anyone to have any miraculous input, but I wanted to at least voice my experiences here with the rest of you.  I'm really bummed too because from what I saw I really liked this new release :(

---

### Post by robbielink on 2010-01-27
I've also been following this for a while - various threads and bug reports and have tried various proposed remedies on my Dell Dimension 2400 to no avail. Recently [**this bug report**]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/456902") has generated a lot of activity and a new PPA with video driver roll-backs has been set up that some folks are having success with (I just added the PPA and updated yesterday and so far, so good). Post #29 in the bug report has the new PPA which apparently is for Intel drivers although it looks like other folks are using it, too. Basically they've rolled the drivers back several versions and as users of the PPA report success they move them forward again to the next change to try and see where the bug crops up.
Read the bug report at the top of the page - it seems to cover a lot of the symptoms folks in this thread are seeing. While the solution may not be for everyone this is the most forward motion I've seen on this issue so far.

---

### Post by the grey side on 2010-01-28
Add my name to those that solved their problems by using a version of kernel 2.6.32. Thanks to rockyjones, who posted this as a possible solution [some weeks ago]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8562693&postcount=127").
I just can't understand this problem. [Nothing I've done](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948) gives my any clue as to what the cause could be.

---

### Post by trash on 2010-01-30
This is totally weird, i had freezes in jaunty and stopped using it till karmic 9.10 was released. For a month now karmic has been great without a single freeze till tonight just before i was notified of a huge amount of updates.
I am using 2.6.31-17-generic
and i was not doing anything but chatting on Emesene when my screen went black aside from an undercore dash flashing in the upper left corner and only the caplock flashing, requiring a hard restart.
No settings were changed in at least a week so this is indeed quite a random freeze.
I am to tired to do anything about it tonight but will probably upgrade kernel tomorrow...

---

### Post by bingobingo on 2010-02-01
> **pompiuses said:**
> Looks like there's a cure afterall :). Disabling Compiz and installing the Xorg intel driver to 2.4 fixed it completely. So at least on my Dell Dimension 2400 the problem was graphics related.

Following this post:
[http://ubuntuforums.org/showpost.php?p=8341830&postcount=15](http://ubuntuforums.org/showpost.php?p=8341830&postcount=15)

Great, since I do not have intel chip set, does someone have a solution for ATI Radeon chip set? I completely delete compix, since I can not benefit from it with this computer. Some other quirks I have with 9.10 
- 15 minute start-up
- wifi tools, does not work
- even though I have it set to never power down or sleep, it goes to sleep after 5 minutes.

---

### Post by TheCat on 2010-02-02
I had this problem and tried many of the fixes listed here to no avail, including updating the kernel.  Then on a whim I enabled the Pre-released updates (karmic-propopsed) repository and the freeze-crashes have disappeared.  My computer was hard crashing 10+ times per day before.  Rock solid since I enabled pre-released.

---

### Post by archish on 2010-02-07
I tried updating to 2.6.32.7 but still facing the same problems :/
I am actually pretty sick of this now. The Launchpad bug is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498495)

---

### Post by PokeParadox on 2010-02-07
Downgrading the Nvidia drivers only reduced the frequency of system freezes.
It seems I will get a freeze during or after listening to music in Banshee.
This bug is soooo annoying.

---

### Post by NNing on 2010-02-23
> **archish said:**
> I tried updating to 2.6.32.7 but still facing the same problems :/
I am actually pretty sick of this now. The Launchpad bug is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498495)


i've finally decided to give up on Ubuntu -- back to Windows :( if anyone knows of a fix that finally comes up (eg. fingers crossed in 10.04 release), could you please post and mark this solved?

in case anyone's working on it, FYI my desktop uses Asus P5NSLI motherboard with NVIDIA (nFORCE) graphics and intel chips. 

the problem didn't surface the first few weeks, then suddenly the mouse would freeze randomly (sometimes after an hour). lately, both the mouse and keyboard have frozen. i also have a laptop (HP Mini) and karmic netbook remix has so far worked fine with that. 

here are some things that i've tried but they don't work. Note: i'm a total newbie at Ubuntu (& messing with systems in general) so it's possible i made some mistakes:

**1.** the ppa from here:
[https://launchpad.net/~brian-rogers/+archive/graphics-testing](https://launchpad.net/~brian-rogers/+archive/graphics-testing)
result: couldn't boot into 2.6.31-19-generic at next boot. got into 2.6.31-14-generic after following prompts after this message:

Ubuntu is running in low graphics mode. The following error was encountered. You may need to update your configuration to solve this.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screens found, but none have a usable configuration.

I tried downloading Nvidia drivers for Linux from their site after that but not possible. So I tried getting them via Synaptic. ...now i can't even get past this message in 2.6.31-14, but I can get back into Ubuntu via 2.6.31-19 again. 

**2.** the ppa from here:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-retro](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-retro)

**3.** sudo dpkg-reconfigure xorg-driver-synaptics
[http://ubuntuforums.org/archive/index.php/t-75713.html](http://ubuntuforums.org/archive/index.php/t-75713.html)

**4.** echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
[http://danilogurovich.wordpress.com/2009/10/17/ubuntu-karmic-koala-9-10-beta-buggy-touchpad-behavior/](http://danilogurovich.wordpress.com/2009/10/17/ubuntu-karmic-koala-9-10-beta-buggy-touchpad-behavior/)
[http://ubuntuforums.org/showthread.php?t=1308931&highlight=mouse+freeze](http://ubuntuforums.org/showthread.php?t=1308931&highlight=mouse+freeze)
[http://ubuntuforums.org/archive/index.php/t-75713.html](http://ubuntuforums.org/archive/index.php/t-75713.html)
result: permission denied, presumably cos i'm not root, altho i put sudo su <username> before the command. (I am a total newbie at all this! dunno that i want to mess around as root. dunno what the hell i'm doing trying to fix this stuff without hardly knowing ubuntu in the first place!)

anyway, that's just some trial & error data for anyone who's interested. such a pity that would-be converts like me can't quite make the jump.

---

### Post by rockyjones on 2010-02-23
I finally solved the freezing by disabling wpa2 on my wireless router and connecting to it with no encryption.  This has completely stopped the problem.  I don't know if the problem is in wpa_supplicant or another area having to do with wpa2 encryption/connection or not.  All I know is it has worked now for two weeks and no problems.  I can now run any kernel without problems.

---

### Post by draco31.fr on 2010-02-23
@ NNing,
try using this command line :
echo 'options psmouse proto=exps' | sudo tee -a /etc/modprobe.d/psmouse.modprobe

You could see if this works fine by using :
cat /etc/modprobe.d/psmouse.modprobe

It should print "options psmouse proto=exps" on the screen.

You have to reboot to see if it is better or worse.


@ Every body having freezes
Does someone have seen some related error in dmesg or a common thing between all people having freezes ?
Is it due to some hardware or just the cause of some change in Karmic ?

For my part, installing kernel 2.6.32.2 and disabling some ACPI stuff from the BIOS preserve my desktop for freezing during 15 days non stop !! (about 2 freezes per day with the default kernel)

---

### Post by michaelzap on 2010-02-23
> **draco31.fr said:**
> @ Every body having freezes
Does someone have seen some related error in dmesg or a common thing between all people having freezes ?
Is it due to some hardware or just the cause of some change in Karmic ?

For my part, installing kernel 2.6.32.2 and disabling some ACPI stuff from the BIOS preserve my desktop for freezing during 15 days non stop !! (about 2 freezes per day with the default kernel)

Installing kernel 2.6.32.x was the magic bullet for me also.

---

### Post by Tal Amir on 2010-02-25
Hi everyone.

I've just opened a new[ LaunchPad bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/527149") for this bug. Please go there and add your experience - Tell what you tried to do and whether it worked or didn't work, specify the version numbers of Kernel and NVIDIA drivers, tell whether you're using 32 / 64 bit Ubuntu, etc.

Also, I saw that there are some people here who experience this bug with video cards other than NVIDIA. If you guys will report it there, we can change the bug description to indicate that this is something more general than just NVIDIA, and is probably related to the kernel or Xorg.

Also, I need some advice - I reported the bug as related to the 'xorg' and 'nvidia-graphics-drivers' packages. Does anyone have ideas for more packages which might be responsible for this?

Let's hope that they will manage to solve this bug until Lucid comes out, otherwise that's the end of Ubuntu for quite a few of us.

---

### Post by draco31.fr on 2010-02-25
I think the kernel is involved too.
So, you can add the package "linux-image".

---

### Post by Tal Amir on 2010-02-25
Done.
I added the "linux-image" package but launchpad changed it to "[linux-ports-meta ]("https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta")" instead. I guess it's ok. Now let's hope they'll find the cause for this problem.

Thanks, Tal

---

### Post by Mike BFD on 2010-02-26
Hi everyone.

I followed this thread... And not only this one actually.
I'm not a programmer - and I'm new to Ubuntu (and Linux in general).
However, I got a couple of thoughts regarding all that... From a "stupid logic" point of view.

1. People having these problems (random freeze, bootup freeze) use different video chipsets and different CPUs
2. In some cases UPgrading kernel and/or DOWNgrading video driver helps, in some cases not (from own experience: one of my laptops works perfectly with both Jaunty and Karmic, another one freezes randomly with Jaunty and freezes at bootup with Karmic or with Jaunty w/new kernel "younger" than 2.6.28)
3. The entire freezing seems to be "video-related" (a comp doesn't "hang" completely, it keeps on working, but stops communicating with the outer world)

That, I guess, means the problem is in bad handling the "bus" (or "protocol" or whatever) responsible for connection between videocard and CPU... Just because this seems to be the only thing ALL affected computers have!!

Any further ideas?..

---

### Post by draco31.fr on 2010-02-27
This is a good analyses, but it might not be enough accurate.
1. That's a fact. We can consider that there is a common broken feature used by all of us, or there is differents problems with the same resulting bug : freeze.
2. Kernel branch 2.6.2 is very old, on Jaunty the kernel is 2.6.29.x ; on Karmic the kernel is 2.6.31.x and on Lucid is will be 2.6.32.x. There is also a 2.6.33 version that have been released few days ago.
3. If you got a Kernel Panic, I can ensure that you get a total computer freeze. The computer will "hang" completely.

I think that :
- if you can switch to a tty terminal, while only X is freezed.
The problem can be Xorg itself, graphic driver or graphic kernel module, or some bus communication (like D-bus) or HAL or something like related ... and so on.
- if your keyboard and/or mouse won't respond.
The problem should be related to Xorg, with a bad handling of external device, or kernel related if it is hardware related.

This can also be side effect : using beta or bugged drivers with an unstable kernel for you hardware. (This is my case with Intel Core i5-750 and kernel 2.6.26 to 2.6.31)

One thing is sure : if everybody can tell how he/she have solved his/her problem, we could make a real conclusion about what is the key of all this mess !!
And if there is still some people with freeze, we can make a cross analyses with their hardware and driver configuration.

---

### Post by StuartN on 2010-02-28
Does your root filesystem go read-only during these freezes, requiring a fsck after rebooting, with orphaned inodes?

I have just installed Ubuntu 9.10 on a Dell Inspiron 1501 that was running 8.10 very well, and have constant lock-ups - sometimes after suspend and resume, sometimes apparently randomly. If I happen to have a terminal open, then I can see that my / partition has gone readonly and dmesg shows some disk io errors (which are obviously not written to the readonly log!).

(I also installed 9.10 on an outwardly identical Dell Inspiron 1501 that has a dual-core AMD and a different hard disk with no problems. I also have it on a couple of desktops also with no problems.)

I am wondering if I should a) go back to an earlier Ubuntu (9.04?), b) add the Karmic Proposed repository or c) try 10.04.

---

### Post by draco31.fr on 2010-02-28
Have you installed your system on a ext4 partition ?
If yes, try to use a newer kernel, because there is some problem with 2.6.31 and earlier kernel while flushing the cache of pending operations to the drive when using ext4 partition.
You can also format to ext3, but you will loose the data, and of course you will have to reinstall all the system if this was your root partition.

---

### Post by StuartN on 2010-02-28
> **draco31.fr said:**
> Have you installed your system on a ext4 partition ?

No. I first installed one single ext3 partition for everything, but the remount readonly meant no applications could save data to my home when this event occurred. I reinstalled using a 10 GB ext3 root partition and the rest of the disk is an ext3 /home partition.

With a separate system partition these lock-ups are less frequent (I have not had one yet today, and have suspended several times), and my applications can save before I hard reboot.

At present I am choosing to believe that this is a software problem in handling my laptop hardware design, and that it is not a failing hard drive.

---

### Post by kyalpani on 2010-03-01
Hi I had the same problem after I upgraded to the latest kernel, so I edited  /boot/grub/menu.lst and reverted to  'Ubuntu 9.10, kernel 2.6.31-17-generic' and since then the problem seems gone.

---

### Post by go2dell on 2010-03-01
> **StuartN said:**
> Does your root filesystem go read-only during these freezes, requiring a fsck after rebooting, with orphaned inodes?

YES!  I have exactly the same problem with 9.10.  I was hoping it was some sort of strange kernel bug, but it still exists in 10.04.  I've also tried using the mainline kernel -- available from the Kernel Team -- and the corruption seems less frequent and less severe, but it's still happening.  Like you, all my other systems run fine.

The symptoms seem almost identical to the filesystem corruption that 64-bit users were experiencing, but I'm using 32-bit.  Right now I'm stuck with 9.04, with no hopes of ever using a newer Ubuntu because the filesystem is corrupted within minutes of installation, so even something like compiling my own kernel to install isn't guaranteed to work.

The Launchpad bug I opened is [528981]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981") if you're interested in looking at/adding information.

---

### Post by draco31.fr on 2010-03-01
Did you try the new 2.6.33 kernel from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I also found 2 bug reports that may be similar :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502318)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509938](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509938)

I suggest you try installing on an other filesystem (like ReiserFS), or try using changing the parameters in the BIOS for the hard drive (AHCI SATA / PATA emulation ...).
Did you try booting on Karmic using the kernel of Jaunty ? (I don't know if this is possible)

---

### Post by StuartN on 2010-03-01
> **draco31.fr said:**
> I also found 2 bug reports that may be similar

Yes, I think that there is probably a hardware management issue that leads to so many different symptoms that these bugs have the same cause. I found other forum threads that sound like the same problem, but no solutions.

Are your computers able to hibernate? I can create a very similar situation by attempting to hibernate, with the same readonly filesystem recovery on restarting (with both ext3 and ext4 filesystems).

---

### Post by go2dell on 2010-03-01
Thanks for the investigation, draco31.  LP #509938 appears to be an overheating issue, which is probably not the case since the hardware thermal throttling would be logged before the corruption.  My heatsink has a nice coating of Arctic Silver under it... which is apparently what it left the factory with, except in a ridiculously thick layer.  This is one of those ridiculously hot P4 systems only a couple of steps below the desktop versions that literally melted down.  They put a heatsink in this notebook that's the size of some server heatsinks I've used.  No wimpy heatpipes here!

LP #502318 is an AMD 64-bit machine, and there have definitely been problems with 64-bit installs and filesystem corruption.  This doesn't really affect me since I have a 32-bit system, but I subscribed anyway to watch what happens there.

I didn't run a 33 mainline kernel, but I ran the 32.8.  Same problems.  This means the problem has persisted through two kernel numbers, which is probably 20 or so releases.  My head starts to swim when I count them off the Mainline mapping table.

My only real BIOS options related to the drive controller is to change geometry reporting from DOS to Other, and both Windows and Linux completely ignore this setting.  I'm not even sure FreeDOS bothers to honor it these days, but I can't remember the last time I even checked what it did.

Oh, and ReiserFS?  Are you trying to put me in the hospital?  I've experienced the joys of ReiserFS, and I wouldn't be able to tell if the corruption was a kernel problem or a Reiser problem.  The best move I ever made was to rescue all my data on all my systems from the ravages of Reiser.  I might try XFS and JFS just to be thorough, but that will be of dubious value since the machine will be running either ext3 or ext4.

StuartN, I can hibernate beautifully under Jaunty, but I can't keep anything newer running long enough to try it.  Maybe one day soon....

Now I'm off to start a nice, long memtest before Leann catches me filing bugs without doing my homework!  :lolflag:

---

### Post by mutantcookie on 2010-03-02
Hi, first post here, and Im new to ubuntu. 

Anyway, i have the freeze problem like many others. My screen freezes, but i still have control of the mouse, and if I play music, the music continues but nothing else happens. Then after about 30 seconds, everything returns to normal. The funny thing is, it does this almost always on the same second. Every to minutes or so, for example 21:50:06, it freezes, then again at 21:52:06. 

Anyone else have this problem? Read through some of this thread, but not everything, so I don't know. 

Using, Ubuntu 9.10.

Thanks guys.

---

### Post by StuartN on 2010-03-02
> **mutantcookie said:**
> The funny thing is, it does this almost always on the same second. Every to minutes or so, for example 21:50:06, it freezes, then again at 21:52:06.

The command **dmesg** typed in a terminal will print a list of recent kernel messages, since the last boot. The end of this list should explain what was happening during the hiccups.

---

### Post by go2dell on 2010-03-08
Update: Tried the March 7 build of 2.6.33 and... no corruption whatsoever.  It works magically well.

On a possibly related note, the latest 2.6.32 (16) build failed to replay the journal when I rebooted to it from 2.6.33, but it's been pretty solid since then.  I'm a little worried about the journal replay, since the system had a clean shutdown and shouldn't have called for a journal replay, but I'm keeping my fingers crossed that a patch has been integrated to let me use Lucid with confidence.

If not, then at least I know there's a pretty good chance that I can use Mangy Mongoose.

---

### Post by StuartN on 2010-03-09
> **go2dell said:**
> Update: Tried the March 7 build of 2.6.33 and... no corruption whatsoever.

Just for clarification (especially for people like me who use just the standard installs), this kernel version is NOT in the regular Ubuntu 9.10 updates but IS going to be in the standard install of 10.04?

---

### Post by go2dell on 2010-03-09
Unless something magical happens, 2.6.33 will not be  in any standard install of any Ubuntu variant.  The only way to get 2.6.33+ in a standard installation will be to wait for 10.10.

On a positive note, I've been having success with the latest -16 update of 2.6.32.  Although my system has locked up a few times, I haven't had any real data loss at all.  Unlike with 2.6.33, it does require about three reboots for fsck to get the disk in a bootable state, but it does happen.

edit: For the greatest success, I've used the Alternate Install to install a command-line only system, then performed a full update immediately after installation.  A reboot after that and I can use Tasksel to install the Kubuntu-desktop (or Ubuntu-desktop).  This process will become less complex when we get another working daily CD, but that may not happen until Beta.

---

### Post by pterosky on 2010-04-05
I also get a randomly freeze on my laptop, but perhaps more when opening nautilus or firefox...? It started during the last week. I can still move the mouse, but the rest is solid frozen.

Anyway, if the laptop is connected to the internet (I use cable) the freeze doesn't seem to happen. Perhaps a connection there? I am using 9.10 Karmic Koala.

---

### Post by the-spear on 2010-04-06
2.6.33 is smoooth and so far stable. i actually think my system's faster too.

---

### Post by draco31.fr on 2010-04-07
Does anyone know how to install nVidia proprietary driver for 2.6.33 kernel mainline ?
I read some library path have been changed, but I can't achieve to reinstall the package.

---

### Post by TheCat on 2010-04-24
With the updates that Synaptic downloaded and installed yesterday, my problem has returned with a vengeance.  Firefox freezes my system approximately every five minutes.

---

### Post by StuartN on 2010-04-24
> **TheCat said:**
> With the updates that Synaptic downloaded and installed yesterday, my problem has returned with a vengeance.  Firefox freezes my system approximately every five minutes.

Certainly not every five minutes on my laptop, but three times since the update. Cursor and keyboard are non-responsive, no access to terminal etc. The only action available seems to be a power-cycle reboot - and there is absolutely nothing written to any log that I can see (presumably because / was remounted readonly). I do not know if this is the original problem introduced in Ubuntu 9.10 or a new problem introduced in Firefox 3.6.3.

I don't have the link to hand, but someone claimed that creating and switching to a new user account completely solves this problem - presumably because there is a permission problem with the account created during operating system installation. I have not tested it.

---

### Post by swwb on 2010-04-24
I'm having trouble with my system freezing right after I boot. I actually just built the computer from all new parts this afternoon and installed Ubuntu 9.10 (no problems) but when I power up I get to the desktop and I have about 10 seconds before both the mouse (usb) and keyboard (ps/2) become unresponsive and the screen itself freezes. It actually froze as I was right clicking and the menu was semi transparent suggesting it might not just be the peripherals (?)  I have a feeling it might be due to the hardware, but I don't see why that would cause this kind of problem. I can post the specs if they're relevant.  edit: I should mention that I have somewhat limited liunx experience. I've been using Mint on my netbook for a month or so and am familiar with the command line from when I used a mac.

---

### Post by swwb on 2010-04-25
I was wondering if anyone had any insight into this since the problem is persisting.   I can log in using failsafe gnome and experience no problems, but it still freezes whenever I use normal gnome.

---

### Post by tperwez on 2010-04-25
> **swwb said:**
> I'm having trouble with my system freezing right after I boot. I actually just built the computer from all new parts this afternoon and installed Ubuntu 9.10 (no problems) but when I power up I get to the desktop and I have about 10 seconds before both the mouse (usb) and keyboard (ps/2) become unresponsive and the screen itself freezes. It actually froze as I was right clicking and the menu was semi transparent suggesting it might not just be the peripherals (?)  I have a feeling it might be due to the hardware, but I don't see why that would cause this kind of problem. I can post the specs if they're relevant.  edit: I should mention that I have somewhat limited liunx experience. I've been using Mint on my netbook for a month or so and am familiar with the command line from when I used a mac.

Sorry to see that you have the very same problem that I am having. I upgraded to 9.10 about a week ago and have been having the system crashes ever since. I have ran Memtest and there are no errors. I have twice clean installed 9.10 just to make sure there was nothing funky in the installation itself. I ran the Update Manager to make sure I have installed the latest update but the problem persists. In my case, I could be using any application (Firefox, Emacs, pdf viewer, or even just the desktop) and the system suddenly freezes. There is no response even with any keyboard combination. Seems like the X Server is frozen. I always have do hard boot. Today, I had to reboot three times already. Finally I booted with the 2.31.14 kernel (the latest on my system is 2.31.20). So far, it has been running ok for the last three hours or so. You can also try to boot using the older kernel and see if that helps.

As far as I know, no one has been upcoming with any solution to this problem (or even the root cause of this). I am just waiting until 10.04 becomes stably available and would like to do a clean install.

Good luck.

---

### Post by StuartN on 2010-04-26
> **tperwez said:**
> I am just waiting until 10.04 becomes stably available and would like to do a clean install.

As far as I can tell, this problem persists in 10.04. I did a clean install of the beta and a clean install of the release candidate, and I have random freezes.

This may be a different problem (in 9.10 my / partition was remounted readonly, now I get a complete freeze of display, mouse and keyboard), but I am disappointed because versions up to 8.10 have run absolutely perfectly. I have the exact same symptoms on another laptop identical to this one, but not on desktop machines.

---

