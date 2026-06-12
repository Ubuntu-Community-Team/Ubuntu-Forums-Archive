---
title: "Hard Drive Failure"
date: 2010-02-21
forum: General Help
---

### Post by davey98 on 2010-02-21
Hello,
The old HDD on my computer was failing, so I used a Ubuntu Live CD to copy many files to my second HDD. Later I repeated the process with the intention of copying the remainder of the files from the old HDD, but Ubuntu could no longer "see" the HDD. The Disk Editor of Ubuntu found the HDD but showed it as unallocated.

Windows XP is installed on the old HDD and the file system is NTFS.

Is there any way of getting the remainder of the files? They aren't really important so I wouldn't pay to have it done.

Is it true that putting the HDD in a freezer for a while might help?


Thank you for any help you are able to offer.

Here is the log from the Ubuntu Live Session (sorry that it's so long): 


Feb 22 02:43:17 ubuntu syslogd 1.4.1#21ubuntu3: restart.
Feb 22 02:43:18 ubuntu kernel: Inspecting /boot/System.map-2.6.22-14-generic
Feb 22 02:43:19 ubuntu kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Feb 22 02:43:19 ubuntu kernel: Symbols match kernel version 2.6.22.
Feb 22 02:43:19 ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-provided physical RAM map:
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 0000000000100000 - 000000007bff0000 (usable)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 000000007bff0000 - 000000007bff3000 (ACPI NVS)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 000000007bff3000 - 000000007c000000 (ACPI data)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] 1087MB HIGHMEM available.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] 896MB LOWMEM available.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] found SMP MP-table at 000f48e0
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Zone PFN ranges:
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] DMA 0 -> 4096
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Normal 4096 -> 229376
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] HighMem 229376 -> 507888
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] early_node_map[1] active PFN ranges
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] 0: 0 -> 507888
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] DMI 2.4 present.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: RSDP signature @ 0xC00F62B0 checksum 0
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: RSDP 000F62B0, 0014 (r0 GBT )
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: RSDT 7BFF3000, 0034 (r1 GBT NVDAACPI 42302E31 NVDA 1010101)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: FACP 7BFF3040, 0074 (r1 GBT NVDAACPI 42302E31 NVDA 1010101)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: DSDT 7BFF30C0, 43ED (r1 GBT NVDAACPI 1000 MSFT 3000000)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: FACS 7BFF0000, 0040
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: SSDT 7BFF7580, 02CC (r1 PTLTD POWERNOW 1 LTP 1)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: MCFG 7BFF78C0, 003C (r1 GBT NVDAACPI 42302E31 NVDA 1010101)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: APIC 7BFF74C0, 0098 (r1 GBT NVDAACPI 42302E31 NVDA 1010101)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] If you got timer trouble try acpi_use_timer_override
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Processor #0 15:11 APIC version 16
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Processor #1 15:11 APIC version 16
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Using ACPI (MADT) for SMP configuration information
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Built 1 zonelists. Total pages: 503921
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Enabling fast FPU save and restore... done.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Initializing CPU#0
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Detected 2712.488 MHz processor.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Console: colour VGA+ 80x25
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Memory: 2002368k/2031552k available (2015k kernel code, 27916k reserved, 916k data, 364k init, 1114048k highmem)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] virtual kernel memory layout:
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] fixmap : 0xfff4d000 - 0xfffff000 ( 712 kB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] .init : 0xc03e3000 - 0xc043e000 ( 364 kB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] .data : 0xc02f7d26 - 0xc03dce84 ( 916 kB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] .text : 0xc0100000 - 0xc02f7d26 (2015 kB)
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb 22 02:43:19 ubuntu kernel: [ 0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] Calibrating delay using timer specific routine.. 5430.16 BogoMIPS (lpj=10860322)
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] Security Framework v1.0.0 initialized
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] SELinux: Disabled at boot.
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] Mount-cache hash table entries: 512
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] CPU: L2 Cache: 512K (64 bytes/line)
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] CPU 0(2) -> Core 0
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] Compat vDSO mapped to ffffe000.
Feb 22 02:43:19 ubuntu kernel: [ 0.084000] Checking 'hlt' instruction... OK.
Feb 22 02:43:19 ubuntu kernel: [ 0.100000] SMP alternatives: switching to UP code
Feb 22 02:43:19 ubuntu kernel: [ 0.100000] Early unpacking initramfs... done
Feb 22 02:43:19 ubuntu kernel: [ 0.320000] ACPI: Core revision 20070126
Feb 22 02:43:19 ubuntu kernel: [ 0.320000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Feb 22 02:43:19 ubuntu kernel: [ 0.324000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
Feb 22 02:43:19 ubuntu kernel: [ 0.324000] SMP alternatives: switching to SMP code
Feb 22 02:43:19 ubuntu kernel: [ 0.324000] Booting processor 1/1 eip 3000
Feb 22 02:43:19 ubuntu kernel: [ 0.332000] Initializing CPU#1
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] Calibrating delay using timer specific routine.. 5425.03 BogoMIPS (lpj=10850076)
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] CPU: L2 Cache: 512K (64 bytes/line)
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] CPU 1(2) -> Core 1
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] Total of 2 processors activated (10855.19 BogoMIPS).
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] ENABLING IO-APIC IRQs
Feb 22 02:43:19 ubuntu kernel: [ 0.412000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Feb 22 02:43:19 ubuntu kernel: [ 0.456000] Brought up 2 CPUs
Feb 22 02:43:19 ubuntu kernel: [ 0.508000] migration_cost=0
Feb 22 02:43:19 ubuntu kernel: [ 0.508000] Booting paravirtualized kernel on bare hardware
Feb 22 02:43:19 ubuntu kernel: [ 0.508000] Time: 2:34:35 Date: 01/22/110
Feb 22 02:43:19 ubuntu kernel: [ 0.508000] NET: Registered protocol family 16
Feb 22 02:43:19 ubuntu kernel: [ 0.508000] EISA bus registered
Feb 22 02:43:19 ubuntu kernel: [ 0.508000] ACPI: bus type pci registered
Feb 22 02:43:19 ubuntu kernel: [ 0.512000] PCI: PCI BIOS revision 3.00 entry at 0xfafb0, last bus=1
Feb 22 02:43:19 ubuntu kernel: [ 0.512000] PCI: Using configuration type 1
Feb 22 02:43:19 ubuntu kernel: [ 0.512000] Setting up standard PCI resources
Feb 22 02:43:19 ubuntu kernel: [ 0.520000] ACPI: Interpreter enabled
Feb 22 02:43:19 ubuntu kernel: [ 0.520000] ACPI: (supports S0 S3 S4 S5)
Feb 22 02:43:19 ubuntu kernel: [ 0.520000] ACPI: Using IOAPIC for interrupt routing
Feb 22 02:43:19 ubuntu kernel: [ 0.524000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 22 02:43:19 ubuntu kernel: [ 0.524000] PCI: Transparent bridge - 0000:00:04.0
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC3] (IRQs 1 *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.548000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] pnp: PnP ACPI init
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: bus type pnp registered
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] pnp: PnP ACPI: found 14 devices
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] ACPI: ACPI bus type pnp unregistered
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] PnPBIOS: Disabled by ACPI PNP
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] PCI: Using ACPI for IRQ routing
Feb 22 02:43:19 ubuntu kernel: [ 0.552000] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] NET: Registered protocol family 8
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] NET: Registered protocol family 20
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:01: iomem range 0x7c000000-0x7fffffff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:0c: iomem range 0xf0000000-0xf7ffffff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:0d: iomem range 0xcec00-0xcffff has been reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.568000] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
Feb 22 02:43:19 ubuntu kernel: [ 0.600000] PCI: Bridge: 0000:00:04.0
Feb 22 02:43:19 ubuntu kernel: [ 0.600000] IO window: b000-bfff
Feb 22 02:43:19 ubuntu kernel: [ 0.600000] MEM window: fb000000-fb0fffff
Feb 22 02:43:19 ubuntu kernel: [ 0.600000] PREFETCH window: disabled.
Feb 22 02:43:19 ubuntu kernel: [ 0.600000] NET: Registered protocol family 2
Feb 22 02:43:19 ubuntu kernel: [ 0.604000] Time: acpi_pm clocksource has been installed.
Feb 22 02:43:19 ubuntu kernel: [ 0.604000] Switched to high resolution mode on CPU 0
Feb 22 02:43:19 ubuntu kernel: [ 0.604000] Switched to high resolution mode on CPU 1
Feb 22 02:43:19 ubuntu kernel: [ 0.648000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 0.648000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 0.648000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 0.648000] TCP: Hash tables configured (established 131072 bind 65536)
Feb 22 02:43:19 ubuntu kernel: [ 0.648000] TCP reno registered
Feb 22 02:43:19 ubuntu kernel: [ 0.660000] checking if image is initramfs... it is
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] Freeing initrd memory: 7305k freed
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] audit: initializing netlink socket (disabled)
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] audit(1266806075.604:1): initialized
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] highmem bounce pool size: 64 pages
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] VFS: Disk quotas dquot_6.5.1
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] io scheduler noop registered
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] io scheduler anticipatory registered
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] io scheduler deadline registered
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] io scheduler cfq registered (default)
Feb 22 02:43:19 ubuntu kernel: [ 1.092000] isapnp: Scanning for PnP cards...
Feb 22 02:43:19 ubuntu kernel: [ 1.444000] isapnp: No Plug & Play device found
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] Real Time Clock Driver v1.12ac
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] input: Macintosh mouse button emulation as /class/input/input0
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] mice: PS/2 mouse device common for all mice
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] EISA: Probing bus 0 at eisa.0
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] Cannot allocate resource for EISA slot 1
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] EISA: Detected 0 cards.
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] TCP cubic registered
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] NET: Registered protocol family 1
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] Using IPI No-Shortcut mode
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] Magic number: 14:864:561
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] hash matches device ptya7
Feb 22 02:43:19 ubuntu kernel: [ 1.464000] Freeing unused kernel memory: 364k freed
Feb 22 02:43:19 ubuntu kernel: [ 1.484000] input: AT Translated Set 2 keyboard as /class/input/input1
Feb 22 02:43:19 ubuntu kernel: [ 2.628000] AppArmor: AppArmor initialized<5>audit(1266806077.604:2): type=1505 info="AppArmor initialized" pid=1237
Feb 22 02:43:19 ubuntu kernel: [ 2.636000] fuse init (API version 7.
Feb 22 02:43:19 ubuntu kernel: [ 2.640000] Failure registering capabilities with primary security module.
Feb 22 02:43:19 ubuntu kernel: [ 2.672000] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Feb 22 02:43:19 ubuntu kernel: [ 2.672000] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] NFORCE-MCP61: chipset revision 162
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] NFORCE-MCP61: not 100%% native mode: will probe irqs later
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
Feb 22 02:43:19 ubuntu kernel: [ 3.104000] ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hdaMA, hdbMA
Feb 22 02:43:19 ubuntu kernel: [ 3.128000] Floppy drive(s): fd0 is 1.44M
Feb 22 02:43:19 ubuntu kernel: [ 3.140000] usbcore: registered new interface driver usbfs
Feb 22 02:43:19 ubuntu kernel: [ 3.140000] usbcore: registered new interface driver hub
Feb 22 02:43:19 ubuntu kernel: [ 3.140000] usbcore: registered new device driver usb
Feb 22 02:43:19 ubuntu kernel: [ 3.152000] SCSI subsystem initialized
Feb 22 02:43:19 ubuntu kernel: [ 3.156000] FDC 0 is a post-1991 82077
Feb 22 02:43:19 ubuntu kernel: [ 3.156000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
Feb 22 02:43:19 ubuntu kernel: [ 3.396000] hda: Maxtor 6E040L0, ATA DISK drive
Feb 22 02:43:19 ubuntu kernel: [ 4.068000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb 22 02:43:19 ubuntu kernel: [ 4.084000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Feb 22 02:43:19 ubuntu kernel: [ 4.084000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Feb 22 02:43:19 ubuntu kernel: [ 4.084000] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb 22 02:43:19 ubuntu kernel: [ 4.084000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Feb 22 02:43:19 ubuntu kernel: [ 4.084000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfb104000
Feb 22 02:43:19 ubuntu kernel: [ 4.140000] usb usb1: configuration #1 chosen from 1 choice
Feb 22 02:43:19 ubuntu kernel: [ 4.140000] hub 1-0:1.0: USB hub found
Feb 22 02:43:19 ubuntu kernel: [ 4.140000] hub 1-0:1.0: 10 ports detected
Feb 22 02:43:19 ubuntu kernel: [ 4.244000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Feb 22 02:43:19 ubuntu kernel: [ 4.244000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 17
Feb 22 02:43:19 ubuntu kernel: [ 4.244000] forcedeth: using HIGHDMA
Feb 22 02:43:19 ubuntu kernel: [ 4.548000] usb 1-4: new full speed USB device using ohci_hcd and address 2
Feb 22 02:43:19 ubuntu kernel: [ 4.760000] usb 1-4: configuration #1 chosen from 1 choice
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:07.0
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 18
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ehci_hcd 0000:00:02.1: debug port 1
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ehci_hcd 0000:00:02.1: irq 18, io mem 0xfb105000
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] usb usb2: configuration #1 chosen from 1 choice
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] hub 2-0:1.0: USB hub found
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] hub 2-0:1.0: 10 ports detected
Feb 22 02:43:19 ubuntu kernel: [ 4.764000] usb 1-4: USB disconnect, address 2
Feb 22 02:43:19 ubuntu kernel: [ 4.868000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Feb 22 02:43:19 ubuntu kernel: [ 4.868000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
Feb 22 02:43:19 ubuntu kernel: [ 4.868000] scsi0 : sata_nv
Feb 22 02:43:19 ubuntu kernel: [ 4.868000] scsi1 : sata_nv
Feb 22 02:43:19 ubuntu kernel: [ 4.868000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 19
Feb 22 02:43:19 ubuntu kernel: [ 4.868000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 19
Feb 22 02:43:19 ubuntu kernel: [ 4.872000] hda: max request size: 128KiB
Feb 22 02:43:19 ubuntu kernel: [ 4.876000] hda: Host Protected Area detected.
Feb 22 02:43:19 ubuntu kernel: [ 4.876000] ^Icurrent capacity is 80291135 sectors (41109 MB)
Feb 22 02:43:19 ubuntu kernel: [ 4.876000] ^Inative capacity is 80293248 sectors (41110 MB)
Feb 22 02:43:19 ubuntu kernel: [ 4.880000] hda: Host Protected Area disabled.
Feb 22 02:43:19 ubuntu kernel: [ 4.880000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
Feb 22 02:43:19 ubuntu kernel: [ 4.880000] hda: cache flushes supported
Feb 22 02:43:19 ubuntu kernel: [ 4.880000] hda: hda1 hda2 <<6>ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 22 02:43:19 ubuntu kernel: [ 5.440000] usb 1-4: new full speed USB device using ohci_hcd and address 3
Feb 22 02:43:19 ubuntu kernel: [ 5.500000] ata1.00: ATAPI: PIONEER DVD-RW DVR-216D, 1.07, max UDMA/66
Feb 22 02:43:19 ubuntu kernel: [ 5.652000] usb 1-4: configuration #1 chosen from 1 choice
Feb 22 02:43:19 ubuntu kernel: [ 5.672000] ata1.00: configured for UDMA/66
Feb 22 02:43:19 ubuntu kernel: [ 6.140000] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 22 02:43:19 ubuntu kernel: [ 6.148000] ata2.00: ATA-7: MAXTOR STM3250310AS, 3.AAF, max UDMA/133
Feb 22 02:43:19 ubuntu kernel: [ 6.148000] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb 22 02:43:19 ubuntu kernel: [ 6.164000] ata2.00: configured for UDMA/133
Feb 22 02:43:19 ubuntu kernel: [ 6.164000] scsi 0:0:0:0: CD-ROM PIONEER DVD-RW DVR-216D 1.07 PQ: 0 ANSI: 5
Feb 22 02:43:19 ubuntu kernel: [ 6.164000] scsi 1:0:0:0: Direct-Access ATA MAXTOR STM325031 3.AA PQ: 0 ANSI: 5
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] Uniform CD-ROM driver Revision: 3.20
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sd 1:0:0:0: [sda] Write Protect is off
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sd 1:0:0:0: [sda] Write Protect is off
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 22 02:43:19 ubuntu kernel: [ 6.172000] sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Feb 22 02:43:19 ubuntu kernel: [ 6.176000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Feb 22 02:43:19 ubuntu kernel: [ 6.196000] sda1 < sda5 > sda2 sda3 sda4
Feb 22 02:43:19 ubuntu kernel: [ 6.204000] sd 1:0:0:0: [sda] Attached SCSI disk
Feb 22 02:43:19 ubuntu kernel: [ 14.732000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 14.732000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 02:43:19 ubuntu kernel: [ 14.732000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 14.732000] end_request: I/O error, dev hda, sector 80260736
Feb 22 02:43:19 ubuntu kernel: [ 16.316000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:43:19 ubuntu kernel: [ 22.548000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 22.548000] hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=80260740, sector=80260736
Feb 22 02:43:19 ubuntu kernel: [ 22.548000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 28.484000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:43:19 ubuntu kernel: [ 29.472000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 29.472000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 02:43:19 ubuntu kernel: [ 29.472000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 29.472000] end_request: I/O error, dev hda, sector 80260736
Feb 22 02:43:19 ubuntu kernel: [ 29.472000] >
Feb 22 02:43:19 ubuntu kernel: [ 40.644000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:43:19 ubuntu kernel: [ 46.056000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 46.056000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 46.056000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 46.056000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 52.232000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 52.232000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 52.232000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 52.232000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 53.828000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:43:19 ubuntu kernel: [ 58.356000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 58.356000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 58.356000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 58.356000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 61.048000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 61.048000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 61.048000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 61.048000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 66.000000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:43:19 ubuntu kernel: [ 75.464000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 75.464000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 75.464000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 75.464000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 78.168000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:43:19 ubuntu kernel: [ 79.920000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 79.920000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 79.920000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 79.920000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 84.436000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 84.436000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 84.436000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 84.436000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 96.336000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 96.336000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 96.336000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 96.336000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 102.520000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 102.520000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 102.520000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 102.520000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 110.460000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 110.460000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 110.460000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 110.460000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 117.124000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 117.124000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 117.124000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 117.124000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 121.576000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 121.576000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 121.576000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 121.576000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 131.340000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 131.340000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 131.340000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 131.340000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 141.040000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 141.040000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 141.040000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 141.040000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 143.756000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 143.756000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 143.756000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 143.756000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 153.472000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 153.472000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 153.472000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 153.472000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 160.704000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 160.704000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 160.704000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 160.704000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 165.164000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 165.164000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 165.164000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 165.164000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 168.264000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 168.264000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 168.264000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 168.264000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 170.980000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 170.980000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 170.980000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 170.980000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 178.372000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 178.372000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 178.372000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 178.372000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 182.828000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 182.828000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 182.828000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 182.828000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 192.844000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 192.844000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 192.844000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 192.844000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 199.036000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 199.036000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 199.036000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 199.036000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 201.868000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 201.868000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 201.868000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 201.868000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 206.276000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 206.276000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 206.276000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 206.276000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 209.076000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 209.076000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 209.076000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 209.076000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 211.984000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 211.984000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 211.984000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 211.984000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 215.116000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 215.116000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 215.116000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 215.116000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 219.540000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 219.540000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 219.540000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 219.540000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 221.740000] Registering unionfs 1.4
Feb 22 02:43:19 ubuntu kernel: [ 221.740000] unionfs: debugging is not enabled
Feb 22 02:43:19 ubuntu kernel: [ 221.744000] loop: module loaded
Feb 22 02:43:19 ubuntu kernel: [ 222.084000] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
Feb 22 02:43:19 ubuntu kernel: [ 287.616000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 287.616000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 287.616000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 287.616000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 290.300000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 290.300000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 290.300000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 290.300000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 293.768000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 293.768000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 293.768000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 293.768000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 298.208000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 298.208000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 298.208000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 298.208000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 302.924000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 302.924000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 302.924000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 302.924000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 305.580000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 305.580000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 305.580000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 305.580000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 308.324000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 308.324000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 308.324000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 308.324000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 311.232000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 311.232000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 311.232000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 311.232000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 313.920000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 313.920000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 313.920000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 313.920000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 316.596000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 316.596000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 316.596000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 316.596000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 319.312000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 319.312000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 319.312000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 319.312000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 324.188000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 324.188000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 324.188000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 324.188000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 328.660000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 328.660000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 328.660000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 328.660000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 331.328000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 331.328000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 331.328000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 331.328000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 335.760000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 335.760000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 335.760000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 335.760000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 340.584000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 340.584000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 340.584000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 340.584000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 343.600000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 343.600000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 343.600000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 343.600000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 346.608000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 346.608000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 346.608000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 346.608000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 349.624000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 349.624000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 349.624000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 349.624000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 352.292000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 352.292000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 352.292000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 352.292000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 354.984000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 354.984000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 354.984000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 354.984000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 357.640000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 357.640000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 357.640000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 357.640000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 363.816000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 363.816000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 363.816000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 363.816000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 366.472000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 366.472000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 366.472000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 366.472000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 369.140000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 369.140000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 369.140000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 369.140000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 371.840000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 371.840000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 371.840000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 371.840000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 376.256000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 376.256000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 376.256000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 376.256000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 379.272000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 379.272000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 379.272000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 379.272000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 402.724000] Linux agpgart interface v0.102 (c) Dave Jones
Feb 22 02:43:19 ubuntu kernel: [ 402.776000] input: PC Speaker as /class/input/input2
Feb 22 02:43:19 ubuntu kernel: [ 403.580000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Feb 22 02:43:19 ubuntu kernel: [ 403.584000] parport_pc 00:09: reported by Plug and Play ACPI
Feb 22 02:43:19 ubuntu kernel: [ 403.584000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb 22 02:43:19 ubuntu kernel: [ 403.592000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Feb 22 02:43:19 ubuntu kernel: [ 403.592000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xc400
Feb 22 02:43:19 ubuntu kernel: [ 403.980000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
Feb 22 02:43:19 ubuntu kernel: [ 403.980000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 16
Feb 22 02:43:19 ubuntu kernel: [ 404.188000] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
Feb 22 02:43:19 ubuntu kernel: [ 418.208000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 418.208000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 418.208000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 418.208000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 420.872000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 420.872000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 420.872000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 420.872000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 425.356000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 425.356000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 425.356000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 425.356000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 428.024000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 428.024000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 428.024000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 428.024000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 430.704000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 430.704000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 430.704000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 430.704000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 433.380000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 433.380000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 433.380000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 433.380000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 436.072000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 436.072000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 436.072000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 436.072000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 440.564000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 440.564000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 440.564000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 440.564000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 443.252000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 443.252000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 443.252000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 443.252000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 447.760000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 447.760000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 447.760000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 447.760000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 450.452000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 450.452000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 450.452000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 450.452000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 455.104000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 455.104000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 455.104000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 455.104000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 457.820000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 457.820000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 457.820000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 457.820000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 460.476000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 460.476000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 460.476000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 460.476000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 462.916000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 462.916000] hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 462.916000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 465.576000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 465.576000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 465.576000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 465.576000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 468.240000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 468.240000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 468.240000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 468.240000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 472.684000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 472.684000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 472.684000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 472.684000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 475.340000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 475.340000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 475.340000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 475.340000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 477.780000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 477.780000] hda: dma_intr: error=0x01 { AddrMarkNotFound }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 477.780000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 480.448000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 480.448000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 480.448000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 480.448000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 484.956000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 484.956000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 484.956000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 484.956000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 489.428000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 489.428000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 489.428000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 489.428000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 494.236000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 494.236000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 494.236000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 494.236000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 497.252000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 497.252000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 497.252000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 497.252000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 499.912000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 499.912000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 499.912000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 499.912000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 504.376000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 504.376000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 504.376000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 504.376000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 507.036000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 507.036000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 507.036000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 507.036000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 511.992000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 511.992000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 511.992000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 511.992000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 511.992000] printk: 1 messages suppressed.
Feb 22 02:43:19 ubuntu kernel: [ 516.760000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:19 ubuntu kernel: [ 516.760000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:19 ubuntu kernel: [ 516.760000] ide: failed opcode was: unknown
Feb 22 02:43:19 ubuntu kernel: [ 516.760000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:19 ubuntu kernel: [ 521.100000] No dock devices found.
Feb 22 02:43:19 ubuntu kernel: [ 521.424000] input: Power Button (FF) as /class/input/input4
Feb 22 02:43:19 ubuntu kernel: [ 521.424000] ACPI: Power Button (FF) [PWRF]
Feb 22 02:43:19 ubuntu kernel: [ 521.424000] input: Power Button (CM) as /class/input/input5
Feb 22 02:43:19 ubuntu kernel: [ 521.424000] ACPI: Power Button (CM) [PWRB]
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (version 2.00.00)
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 0 : fid 0x13 (2700 MHz), vid 0x8
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 1 : fid 0x12 (2600 MHz), vid 0x9
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 2 : fid 0x10 (2400 MHz), vid 0xb
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 3 : fid 0xe (2200 MHz), vid 0xd
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 4 : fid 0xc (2000 MHz), vid 0xf
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 5 : fid 0xa (1800 MHz), vid 0x11
Feb 22 02:43:19 ubuntu kernel: [ 522.424000] powernow-k8: 6 : fid 0x2 (1000 MHz), vid 0x12
Feb 22 02:43:25 ubuntu kernel: [ 530.364000] lp0: using parport0 (interrupt-driven).
Feb 22 02:43:26 ubuntu kernel: [ 530.752000] ppdev: user-space parallel port driver
Feb 22 02:43:27 ubuntu kernel: [ 532.020000] eth0: no link during initialization.
Feb 22 02:43:29 ubuntu kernel: [ 534.008000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Feb 22 02:43:29 ubuntu kernel: [ 534.008000] apm: disabled - APM is not SMP safe.
Feb 22 02:43:29 ubuntu kernel: [ 534.252000] Failure registering capabilities with primary security module.
Feb 22 02:43:29 ubuntu kernel: [ 534.600000] Clocksource tsc unstable (delta = -80460975 ns)
Feb 22 02:43:30 ubuntu dhcdbd: Started up.
Feb 22 02:43:30 ubuntu kernel: [ 535.264000] Bluetooth: Core ver 2.11
Feb 22 02:43:30 ubuntu kernel: [ 535.264000] NET: Registered protocol family 31
Feb 22 02:43:30 ubuntu kernel: [ 535.264000] Bluetooth: HCI device and connection manager initialized
Feb 22 02:43:30 ubuntu kernel: [ 535.264000] Bluetooth: HCI socket layer initialized
Feb 22 02:43:30 ubuntu kernel: [ 535.420000] Bluetooth: L2CAP ver 2.8
Feb 22 02:43:30 ubuntu kernel: [ 535.420000] Bluetooth: L2CAP socket layer initialized
Feb 22 02:43:30 ubuntu kernel: [ 535.464000] Bluetooth: RFCOMM socket layer initialized
Feb 22 02:43:30 ubuntu kernel: [ 535.464000] Bluetooth: RFCOMM TTY layer initialized
Feb 22 02:43:30 ubuntu kernel: [ 535.464000] Bluetooth: RFCOMM ver 1.8
Feb 22 02:43:42 ubuntu kernel: [ 547.164000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:42 ubuntu kernel: [ 547.164000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:42 ubuntu kernel: [ 547.164000] ide: failed opcode was: unknown
Feb 22 02:43:42 ubuntu kernel: [ 547.164000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:47 ubuntu kernel: [ 551.936000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:47 ubuntu kernel: [ 551.936000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:47 ubuntu kernel: [ 551.936000] ide: failed opcode was: unknown
Feb 22 02:43:47 ubuntu kernel: [ 551.936000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:43:50 ubuntu kernel: [ 555.004000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:43:50 ubuntu kernel: [ 555.004000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260740
Feb 22 02:43:50 ubuntu kernel: [ 555.004000] ide: failed opcode was: unknown
Feb 22 02:43:50 ubuntu kernel: [ 555.004000] end_request: I/O error, dev hda, sector 80260740
Feb 22 02:50:29 ubuntu kernel: [ 954.684000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
Feb 22 02:50:42 ubuntu kernel: [ 966.876000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:50:54 ubuntu kernel: [ 979.040000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:51:06 ubuntu kernel: [ 991.208000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:51:18 ubuntu kernel: [ 1003.376000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:51:30 ubuntu kernel: [ 1015.540000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:51:42 ubuntu kernel: [ 1027.712000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:51:55 ubuntu kernel: [ 1039.884000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:52:07 ubuntu kernel: [ 1052.056000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:52:19 ubuntu kernel: [ 1064.224000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:52:31 ubuntu kernel: [ 1076.396000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:52:43 ubuntu kernel: [ 1088.568000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:52:56 ubuntu kernel: [ 1100.736000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:53:08 ubuntu kernel: [ 1112.904000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:53:20 ubuntu kernel: [ 1125.076000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:53:32 ubuntu kernel: [ 1137.240000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:53:44 ubuntu kernel: [ 1149.400000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:53:56 ubuntu kernel: [ 1161.564000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:54:09 ubuntu kernel: [ 1173.728000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:54:21 ubuntu kernel: [ 1185.900000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:54:33 ubuntu kernel: [ 1198.076000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:54:45 ubuntu kernel: [ 1210.244000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:54:57 ubuntu kernel: [ 1222.404000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:55:09 ubuntu kernel: [ 1234.576000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:55:22 ubuntu kernel: [ 1246.748000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:55:34 ubuntu kernel: [ 1258.912000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:55:37 ubuntu kernel: [ 1262.036000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:55:37 ubuntu kernel: [ 1262.036000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 02:55:37 ubuntu kernel: [ 1262.036000] ide: failed opcode was: unknown
Feb 22 02:55:37 ubuntu kernel: [ 1262.036000] end_request: I/O error, dev hda, sector 80260736
Feb 22 02:55:40 ubuntu kernel: [ 1264.904000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 02:55:40 ubuntu kernel: [ 1264.904000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 02:55:40 ubuntu kernel: [ 1264.904000] ide: failed opcode was: unknown
Feb 22 02:55:40 ubuntu kernel: [ 1264.904000] end_request: I/O error, dev hda, sector 80260736
Feb 22 02:57:28 ubuntu kernel: [ 1373.052000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
Feb 22 02:57:40 ubuntu kernel: [ 1385.244000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:57:52 ubuntu kernel: [ 1397.404000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:58:04 ubuntu kernel: [ 1409.572000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:58:17 ubuntu kernel: [ 1421.740000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:58:29 ubuntu kernel: [ 1433.908000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:58:41 ubuntu kernel: [ 1446.072000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:58:52 ubuntu kernel: [ 1457.268000] NET: Registered protocol family 10
Feb 22 02:58:52 ubuntu kernel: [ 1457.268000] lo: Disabled Privacy Extensions
Feb 22 02:58:52 ubuntu kernel: [ 1457.268000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 22 02:58:53 ubuntu kernel: [ 1458.236000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:59:05 ubuntu kernel: [ 1470.408000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:59:17 ubuntu kernel: [ 1482.580000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:59:30 ubuntu kernel: [ 1494.752000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:59:42 ubuntu kernel: [ 1506.920000] end_request: I/O error, dev fd0, sector 0
Feb 22 02:59:54 ubuntu kernel: [ 1519.088000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:00:06 ubuntu kernel: [ 1531.260000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:00:18 ubuntu kernel: [ 1543.436000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:00:30 ubuntu kernel: [ 1555.604000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:00:43 ubuntu kernel: [ 1567.772000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:00:55 ubuntu kernel: [ 1579.936000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:01:07 ubuntu kernel: [ 1592.108000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:01:19 ubuntu kernel: [ 1604.276000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:01:31 ubuntu kernel: [ 1616.452000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:01:43 ubuntu kernel: [ 1628.624000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:01:56 ubuntu kernel: [ 1640.792000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:02:08 ubuntu kernel: [ 1652.964000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:02:20 ubuntu kernel: [ 1665.128000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:02:32 ubuntu kernel: [ 1677.288000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:02:35 ubuntu kernel: [ 1680.036000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 03:02:35 ubuntu kernel: [ 1680.036000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 03:02:35 ubuntu kernel: [ 1680.036000] ide: failed opcode was: unknown
Feb 22 03:02:35 ubuntu kernel: [ 1680.036000] end_request: I/O error, dev hda, sector 80260736
Feb 22 03:02:37 ubuntu kernel: [ 1682.728000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 03:02:37 ubuntu kernel: [ 1682.728000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 03:02:37 ubuntu kernel: [ 1682.728000] ide: failed opcode was: unknown
Feb 22 03:02:37 ubuntu kernel: [ 1682.728000] end_request: I/O error, dev hda, sector 80260736
Feb 22 03:04:02 ubuntu kernel: [ 1767.280000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
Feb 22 03:04:14 ubuntu kernel: [ 1779.472000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:04:26 ubuntu kernel: [ 1791.636000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:04:39 ubuntu kernel: [ 1803.796000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:04:40 ubuntu kernel: [ 1804.908000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
Feb 22 03:04:51 ubuntu kernel: [ 1815.960000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:05:03 ubuntu kernel: [ 1828.136000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:05:15 ubuntu kernel: [ 1840.300000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:05:27 ubuntu kernel: [ 1852.464000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:05:39 ubuntu kernel: [ 1864.632000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:05:52 ubuntu kernel: [ 1876.792000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:06:04 ubuntu kernel: [ 1888.964000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:06:16 ubuntu kernel: [ 1901.136000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:06:28 ubuntu kernel: [ 1913.304000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:06:40 ubuntu kernel: [ 1925.464000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:06:52 ubuntu kernel: [ 1937.632000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:07:05 ubuntu kernel: [ 1949.796000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:07:17 ubuntu kernel: [ 1961.968000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:07:29 ubuntu kernel: [ 1974.140000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:07:41 ubuntu kernel: [ 1986.304000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:07:53 ubuntu kernel: [ 1998.476000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:08:05 ubuntu kernel: [ 2010.644000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:08:18 ubuntu kernel: [ 2022.812000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:08:30 ubuntu kernel: [ 2034.976000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:08:42 ubuntu kernel: [ 2047.148000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:08:54 ubuntu kernel: [ 2059.316000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:09:06 ubuntu kernel: [ 2071.488000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:09:18 ubuntu kernel: [ 2083.660000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:09:31 ubuntu kernel: [ 2095.828000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:09:43 ubuntu kernel: [ 2107.996000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:09:55 ubuntu kernel: [ 2120.168000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:10:07 ubuntu kernel: [ 2132.336000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:10:19 ubuntu kernel: [ 2144.504000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:10:31 ubuntu kernel: [ 2156.668000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:10:44 ubuntu kernel: [ 2168.840000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:10:56 ubuntu kernel: [ 2181.008000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:11:08 ubuntu kernel: [ 2193.176000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:11:20 ubuntu kernel: [ 2205.336000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:11:32 ubuntu kernel: [ 2217.504000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:11:44 ubuntu kernel: [ 2229.676000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:11:57 ubuntu kernel: [ 2241.844000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:12:09 ubuntu kernel: [ 2254.012000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:12:21 ubuntu kernel: [ 2266.180000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:12:33 ubuntu kernel: [ 2278.348000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:12:45 ubuntu kernel: [ 2290.516000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:12:57 ubuntu kernel: [ 2302.680000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:13:10 ubuntu kernel: [ 2314.852000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:13:22 ubuntu kernel: [ 2327.020000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:13:34 ubuntu kernel: [ 2339.184000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:13:40 ubuntu kernel: [ 2345.404000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 03:13:40 ubuntu kernel: [ 2345.404000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 03:13:40 ubuntu kernel: [ 2345.404000] ide: failed opcode was: unknown
Feb 22 03:13:40 ubuntu kernel: [ 2345.404000] end_request: I/O error, dev hda, sector 80260736
Feb 22 03:13:43 ubuntu kernel: [ 2348.428000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 03:13:43 ubuntu kernel: [ 2348.428000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 03:13:43 ubuntu kernel: [ 2348.428000] ide: failed opcode was: unknown
Feb 22 03:13:43 ubuntu kernel: [ 2348.428000] end_request: I/O error, dev hda, sector 80260736
Feb 22 03:13:46 ubuntu kernel: [ 2351.356000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:13:58 ubuntu kernel: [ 2363.528000] end_request: I/O error, dev fd0, sector 0
Feb 22 03:14:01 ubuntu kernel: [ 2366.288000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 03:14:01 ubuntu kernel: [ 2366.288000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 03:14:01 ubuntu kernel: [ 2366.288000] ide: failed opcode was: unknown
Feb 22 03:14:01 ubuntu kernel: [ 2366.288000] end_request: I/O error, dev hda, sector 80260736
Feb 22 03:14:08 ubuntu kernel: [ 2372.744000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 22 03:14:08 ubuntu kernel: [ 2372.744000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=80260740, sector=80260736
Feb 22 03:14:08 ubuntu kernel: [ 2372.744000] ide: failed opcode was: unknown
Feb 22 03:14:08 ubuntu kernel: [ 2372.744000] end_request: I/O error, dev hda, sector 80260736

---

### Post by JackRock on 2010-02-21
I've never heard of the freezer trick, and I'd be suspect to trust it.

At this point, I believe your files to be lost without paying a few thousand dollars.

---

### Post by davey98 on 2010-02-22
Thanks. I think you're probably right. Luckily I got most of them, and of those that Ubuntu tried to copy only 2 couldn't be copied and one of them was just Thumbs.db :D

---

### Post by POWMS on 2010-02-22
Davey
I have had a few hard drives fail at work. Out of curiosity, I opened up the last failed drive and found the bearings the disc spins on failed causing the disc to stop spinning. This seems to be the magority of hard drive failures (except for dropped drives!). The info would still be undamaged on the disc itself. I did try our tech support on one hard drive and they said 'too hard'. I gave it to my 'computer geek' brother-in-law and all data was transferred in a couple of hours.
I don't think putting the drive in the freezer would free up the damaged bearings.
But it looks like you got most of the data you wanted.

---

### Post by davey98 on 2010-02-22
I had another attempt with the Ubuntu Live CD, and it was able to see the HDD. All the files that I wanted have been copied to the other HDD.

Thanks JackRock and POWMS.

---

### Post by egalvan on 2010-02-23
The "freezer trick" only works if the part is failing for heat-related reasons.
Freezing the part can cool it down to let it to work long enough to attempt recovery.

And yes, I've done it a time or two, with drives, RAM, CPU, etc...

---

