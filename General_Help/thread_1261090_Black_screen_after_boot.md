---
title: "Black screen after boot"
date: 2009-09-08
forum: General Help
---

### Post by roadkill_cr on 2009-09-08
I've had this problem for quite a while now wherein I start up my computer and it black screens me some random percentage of the time after booting up.  It shows me the Ubuntu loading splash screen, and the progress bar, but when the screen goes black before showing the login screen it just stays there.  I've left it sitting there for 5-10 minutes and nothing happens, and so far the only solution is to hard reset and try again.  Sometimes it boots just fine, other times it takes me one restart, other times (like today) it takes me 10 restarts for Ubuntu to work.

I don't know why I've decided to take so long to actually deal with it (more than a year), but any help would be appreciated, as I could never figure out what was going wrong some random percent of the time.

I'm running Hardy Heron (LTS).  I don't really want to upgrade to a non-LTS version, as this is my work computer (and I'd like it to remain stable) but if this problem has been definitively fixed in later versions I would go for it.

Here's the contents of my syslog on an unsuccessful boot:

```
Sep  8 09:34:31 hopo syslogd 1.5.0#1ubuntu1: restart.
Sep  8 09:34:31 hopo kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep  8 09:34:31 hopo kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep  8 09:34:31 hopo kernel: Symbols match kernel version 2.6.24.
Sep  8 09:34:31 hopo kernel: Loaded 15112 symbols from 77 modules.
Sep  8 09:34:31 hopo kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  8 09:34:31 hopo kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  8 09:34:31 hopo kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep  8 09:34:31 hopo kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5ffc00 (usable)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 000000007f5ffc00 - 000000007f601c00 (ACPI NVS)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 000000007f603c00 - 000000007f653c00 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 000000007f653c00 - 000000007f655c00 (ACPI data)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 000000007f655c00 - 0000000080000000 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep  8 09:34:31 hopo kernel: [    0.000000] 1141MB HIGHMEM available.
Sep  8 09:34:31 hopo kernel: [    0.000000] 896MB LOWMEM available.
Sep  8 09:34:31 hopo kernel: [    0.000000] found SMP MP-table at 000fe710
Sep  8 09:34:31 hopo kernel: [    0.000000] Entering add_active_range(0, 0, 521727) 0 entries of 256 used
Sep  8 09:34:31 hopo kernel: [    0.000000] Zone PFN ranges:
Sep  8 09:34:31 hopo kernel: [    0.000000]   DMA             0 ->     4096
Sep  8 09:34:31 hopo kernel: [    0.000000]   Normal       4096 ->   229376
Sep  8 09:34:31 hopo kernel: [    0.000000]   HighMem    229376 ->   521727
Sep  8 09:34:31 hopo kernel: [    0.000000] Movable zone start PFN for each node
Sep  8 09:34:31 hopo kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  8 09:34:31 hopo kernel: [    0.000000]     0:        0 ->   521727
Sep  8 09:34:31 hopo kernel: [    0.000000] On node 0 totalpages: 521727
Sep  8 09:34:31 hopo kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep  8 09:34:31 hopo kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  8 09:34:31 hopo kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep  8 09:34:31 hopo kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Sep  8 09:34:31 hopo kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Sep  8 09:34:31 hopo kernel: [    0.000000]   HighMem zone: 2283 pages used for memmap
Sep  8 09:34:31 hopo kernel: [    0.000000]   HighMem zone: 290068 pages, LIFO batch:31
Sep  8 09:34:31 hopo kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep  8 09:34:31 hopo kernel: [    0.000000] DMI 2.3 present.
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FEBF0 checksum 0
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: XSDT 000FCE99, 006C (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: FACP 000FCFC1, 00F4 (r3 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: DSDT FFF6A119, 473C (r1   DELL    dt_ex     1000 INTL 20050624)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: FACS 7F5FFC00, 0040
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: SSDT FFF6E974, 00AA (r1   DELL    st_ex     1000 INTL 20050624)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: APIC 000FD0B5, 0092 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: BOOT 000FD147, 0028 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: ASF! 000FD16F, 0092 (r32 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: MCFG 000FD201, 003E (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: HPET 000FD23F, 0038 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: TCPA 000FD49B, 0032 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: SLIC 000FD277, 0176 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] Processor #0 6:15 APIC version 20
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] Processor #1 6:15 APIC version 20
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Sep  8 09:34:31 hopo kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  8 09:34:31 hopo kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  8 09:34:31 hopo kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Sep  8 09:34:31 hopo kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  8 09:34:31 hopo kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep  8 09:34:31 hopo kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000f0000
Sep  8 09:34:31 hopo kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Sep  8 09:34:31 hopo kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517652
Sep  8 09:34:31 hopo kernel: [    0.000000] Kernel command line: root=UUID=a45e6f05-9d59-432a-b705-4a6c8eff02aa ro quiet splash
Sep  8 09:34:31 hopo kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Sep  8 09:34:31 hopo kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Sep  8 09:34:31 hopo kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep  8 09:34:31 hopo kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep  8 09:34:31 hopo kernel: [    0.000000] Initializing CPU#0
Sep  8 09:34:31 hopo kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  8 09:34:31 hopo kernel: [    0.000000] Detected 2128.038 MHz processor.
Sep  8 09:34:31 hopo kernel: [   12.232535] Console: colour VGA+ 80x25
Sep  8 09:34:31 hopo kernel: [   12.232537] console [tty0] enabled
Sep  8 09:34:31 hopo kernel: [   12.232804] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  8 09:34:31 hopo kernel: [   12.233063] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  8 09:34:31 hopo kernel: [   12.306589] Memory: 2056888k/2086908k available (2181k kernel code, 28796k reserved, 1006k data, 368k init, 1169404k highmem)
Sep  8 09:34:31 hopo kernel: [   12.306594] virtual kernel memory layout:
Sep  8 09:34:31 hopo kernel: [   12.306595]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep  8 09:34:31 hopo kernel: [   12.306596]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  8 09:34:31 hopo kernel: [   12.306597]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  8 09:34:31 hopo kernel: [   12.306598]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  8 09:34:31 hopo kernel: [   12.306599]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep  8 09:34:31 hopo kernel: [   12.306600]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep  8 09:34:31 hopo kernel: [   12.306600]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep  8 09:34:31 hopo kernel: [   12.306603] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  8 09:34:31 hopo kernel: [   12.306638] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Sep  8 09:34:31 hopo kernel: [   12.306754] hpet clockevent registered
Sep  8 09:34:31 hopo kernel: [   12.386725] Calibrating delay using timer specific routine.. 4259.16 BogoMIPS (lpj=8518331)
Sep  8 09:34:31 hopo kernel: [   12.386744] Security Framework initialized
Sep  8 09:34:31 hopo kernel: [   12.386749] SELinux:  Disabled at boot.
Sep  8 09:34:31 hopo kernel: [   12.386760] AppArmor: AppArmor initialized
Sep  8 09:34:31 hopo kernel: [   12.386763] Failure registering capabilities with primary security module.
Sep  8 09:34:31 hopo kernel: [   12.386770] Mount-cache hash table entries: 512
Sep  8 09:34:31 hopo kernel: [   12.386871] Initializing cgroup subsys ns
Sep  8 09:34:31 hopo kernel: [   12.386876] Initializing cgroup subsys cpuacct
Sep  8 09:34:31 hopo kernel: [   12.386885] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
Sep  8 09:34:31 hopo kernel: [   12.386890] monitor/mwait feature present.
Sep  8 09:34:31 hopo kernel: [   12.386892] using mwait in idle threads.
Sep  8 09:34:31 hopo kernel: [   12.386896] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  8 09:34:31 hopo kernel: [   12.386898] CPU: L2 cache: 2048K
Sep  8 09:34:31 hopo kernel: [   12.386900] CPU: Physical Processor ID: 0
Sep  8 09:34:31 hopo kernel: [   12.386901] CPU: Processor Core ID: 0
Sep  8 09:34:31 hopo kernel: [   12.386903] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000000
Sep  8 09:34:31 hopo kernel: [   12.386911] Compat vDSO mapped to ffffe000.
Sep  8 09:34:31 hopo kernel: [   12.386922] Checking 'hlt' instruction... OK.
Sep  8 09:34:31 hopo kernel: [   12.403748] SMP alternatives: switching to UP code
Sep  8 09:34:31 hopo kernel: [   12.405095] Early unpacking initramfs... done
Sep  8 09:34:31 hopo kernel: [   12.677367] ACPI: Core revision 20070126
Sep  8 09:34:31 hopo kernel: [   12.752698] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep  8 09:34:31 hopo kernel: [   12.879040] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 02
Sep  8 09:34:31 hopo kernel: [   12.879055] SMP alternatives: switching to SMP code
Sep  8 09:34:31 hopo kernel: [   12.879647] Booting processor 1/1 eip 3000
Sep  8 09:34:31 hopo kernel: [   12.889786] Initializing CPU#1
Sep  8 09:34:31 hopo kernel: [   12.970469] Calibrating delay using timer specific routine.. 4256.02 BogoMIPS (lpj=8512052)
Sep  8 09:34:31 hopo kernel: [   12.970475] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
Sep  8 09:34:31 hopo kernel: [   12.970479] monitor/mwait feature present.
Sep  8 09:34:31 hopo kernel: [   12.970482] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  8 09:34:31 hopo kernel: [   12.970483] CPU: L2 cache: 2048K
Sep  8 09:34:31 hopo kernel: [   12.970485] CPU: Physical Processor ID: 0
Sep  8 09:34:31 hopo kernel: [   12.970486] CPU: Processor Core ID: 1
Sep  8 09:34:31 hopo kernel: [   12.970488] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000000
Sep  8 09:34:31 hopo kernel: [   12.970915] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 02
Sep  8 09:34:31 hopo kernel: [   12.970932] Total of 2 processors activated (8515.19 BogoMIPS).
Sep  8 09:34:31 hopo kernel: [   12.971071] ENABLING IO-APIC IRQs
Sep  8 09:34:31 hopo kernel: [   12.971233] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  8 09:34:31 hopo kernel: [   13.118496] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep  8 09:34:31 hopo kernel: [   13.138501] Brought up 2 CPUs
Sep  8 09:34:31 hopo kernel: [   13.138522] CPU0 attaching sched-domain:
Sep  8 09:34:31 hopo kernel: [   13.138524]  domain 0: span 03
Sep  8 09:34:31 hopo kernel: [   13.138525]   groups: 01 02
Sep  8 09:34:31 hopo kernel: [   13.138528] CPU1 attaching sched-domain:
Sep  8 09:34:31 hopo kernel: [   13.138529]  domain 0: span 03
Sep  8 09:34:31 hopo kernel: [   13.138530]   groups: 02 01
Sep  8 09:34:31 hopo kernel: [   13.138721] net_namespace: 64 bytes
Sep  8 09:34:31 hopo kernel: [   13.138731] Booting paravirtualized kernel on bare hardware
Sep  8 09:34:31 hopo kernel: [   13.139092] Time:  9:34:03  Date: 09/08/09
Sep  8 09:34:31 hopo kernel: [   13.139114] NET: Registered protocol family 16
Sep  8 09:34:31 hopo kernel: [   13.139281] EISA bus registered
Sep  8 09:34:31 hopo kernel: [   13.139284] ACPI: bus type pci registered
Sep  8 09:34:31 hopo kernel: [   13.173146] PCI: PCI BIOS revision 2.10 entry at 0xfb578, last bus=4
Sep  8 09:34:31 hopo kernel: [   13.173148] PCI: Using configuration type 1
Sep  8 09:34:31 hopo kernel: [   13.173168] Setting up standard PCI resources
Sep  8 09:34:31 hopo kernel: [   13.185305] ACPI: EC: Look up EC in DSDT
Sep  8 09:34:31 hopo kernel: [   13.235192] ACPI: BIOS _OSI(Linux) query ignored
Sep  8 09:34:31 hopo kernel: [   13.235194] ACPI: DMI System Vendor: Dell Inc.                
Sep  8 09:34:31 hopo kernel: [   13.235196] ACPI: DMI Product Name: OptiPlex 745                 
Sep  8 09:34:31 hopo kernel: [   13.235197] ACPI: DMI Product Version: 
Sep  8 09:34:31 hopo kernel: [   13.235199] ACPI: DMI Board Name: 0MM599
Sep  8 09:34:31 hopo kernel: [   13.235200] ACPI: DMI BIOS Vendor: Dell Inc.                
Sep  8 09:34:31 hopo kernel: [   13.235201] ACPI: DMI BIOS Date: 05/21/2007
Sep  8 09:34:31 hopo kernel: [   13.235202] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
Sep  8 09:34:31 hopo kernel: [   13.235204] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
Sep  8 09:34:31 hopo kernel: [   13.254563] ACPI: Interpreter enabled
Sep  8 09:34:31 hopo kernel: [   13.254566] ACPI: (supports S0 S1 S3 S4 S5)
Sep  8 09:34:31 hopo kernel: [   13.254579] ACPI: Using IOAPIC for interrupt routing
Sep  8 09:34:31 hopo kernel: [   13.350947] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  8 09:34:31 hopo kernel: [   13.351575] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Sep  8 09:34:31 hopo kernel: [   13.351579] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
Sep  8 09:34:31 hopo kernel: [   13.352013] PCI: Transparent bridge - 0000:00:1e.0
Sep  8 09:34:31 hopo kernel: [   13.352038] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  8 09:34:31 hopo kernel: [   13.352770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
Sep  8 09:34:31 hopo kernel: [   13.353409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Sep  8 09:34:31 hopo kernel: [   13.353879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Sep  8 09:34:31 hopo kernel: [   13.354351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
Sep  8 09:34:31 hopo kernel: [   14.497849] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Sep  8 09:34:31 hopo kernel: [   14.498606] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Sep  8 09:34:31 hopo kernel: [   14.499372] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
Sep  8 09:34:31 hopo kernel: [   14.500121] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Sep  8 09:34:31 hopo kernel: [   14.500870] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Sep  8 09:34:31 hopo kernel: [   14.501625] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Sep  8 09:34:31 hopo kernel: [   14.502384] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Sep  8 09:34:31 hopo kernel: [   14.503148] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Sep  8 09:34:31 hopo kernel: [   14.503534] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 89 [20070126]
Sep  8 09:34:31 hopo kernel: [   14.503540] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  8 09:34:31 hopo kernel: [   14.503565] pnp: PnP ACPI init
Sep  8 09:34:31 hopo kernel: [   14.503571] ACPI: bus type pnp registered
Sep  8 09:34:31 hopo kernel: [   14.559707] pnpacpi: exceeded the max number of IO resources: 40 
Sep  8 09:34:31 hopo kernel: [   14.559972] pnp: PnP ACPI: found 11 devices
Sep  8 09:34:31 hopo kernel: [   14.559974] ACPI: ACPI bus type pnp unregistered
Sep  8 09:34:31 hopo kernel: [   14.559977] PnPBIOS: Disabled by ACPI PNP
Sep  8 09:34:31 hopo kernel: [   14.560156] PCI: Using ACPI for IRQ routing
Sep  8 09:34:31 hopo kernel: [   14.560159] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  8 09:34:31 hopo kernel: [   14.602013] NET: Registered protocol family 8
Sep  8 09:34:31 hopo kernel: [   14.602015] NET: Registered protocol family 20
Sep  8 09:34:31 hopo kernel: [   14.602049] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep  8 09:34:31 hopo kernel: [   14.602053] hpet0: 3 64-bit timers, 14318180 Hz
Sep  8 09:34:31 hopo kernel: [   14.603078] AppArmor: AppArmor Filesystem Enabled
Sep  8 09:34:31 hopo kernel: [   14.605935] Time: tsc clocksource has been installed.
Sep  8 09:34:31 hopo kernel: [   14.605946] Switched to high resolution mode on CPU 0
Sep  8 09:34:31 hopo kernel: [   14.606029] Switched to high resolution mode on CPU 1
Sep  8 09:34:31 hopo kernel: [   14.618885] system 00:01: ioport range 0x800-0x85f has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618889] system 00:01: ioport range 0xc00-0xc7f has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618892] system 00:01: ioport range 0x860-0x8ff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618902] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618905] system 00:08: iomem range 0x100000-0xffffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618908] system 00:08: iomem range 0x1000000-0x7f5ffbff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618911] system 00:08: iomem range 0xf0000-0xfffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618914] system 00:08: iomem range 0xc0000-0xcffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618917] system 00:08: iomem range 0xfec00000-0xfecfffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618920] system 00:08: iomem range 0xfee00000-0xfeefffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618923] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618926] system 00:08: iomem range 0xffc00000-0xffffffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618932] system 00:09: ioport range 0x100-0x1fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618934] system 00:09: ioport range 0x200-0x277 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618937] system 00:09: ioport range 0x280-0x2e7 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618940] system 00:09: ioport range 0x2f0-0x2f7 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618942] system 00:09: ioport range 0x300-0x377 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618945] system 00:09: ioport range 0x380-0x3bb has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618948] system 00:09: ioport range 0x3c0-0x3e7 could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.618950] system 00:09: ioport range 0x3f6-0x3f7 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618953] system 00:09: ioport range 0x400-0x4cf has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618956] system 00:09: ioport range 0x4d2-0x57f has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618958] system 00:09: ioport range 0x580-0x677 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618961] system 00:09: ioport range 0x680-0x777 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618963] system 00:09: ioport range 0x780-0x7bb has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618966] system 00:09: ioport range 0x7c0-0x7ff has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618969] system 00:09: ioport range 0x8e0-0x8ff has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618971] system 00:09: ioport range 0x900-0x9fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618974] system 00:09: ioport range 0xa00-0xafe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618977] system 00:09: ioport range 0xb00-0xbfe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618979] system 00:09: ioport range 0xc80-0xcaf has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618982] system 00:09: ioport range 0xcc0-0xcf7 has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618985] system 00:09: ioport range 0xd00-0xdfe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618987] system 00:09: ioport range 0xe00-0xefe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618990] system 00:09: ioport range 0xf00-0xffe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618993] system 00:09: ioport range 0x2000-0x20fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618996] system 00:09: ioport range 0x2100-0x21fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.618998] system 00:09: ioport range 0x2200-0x22fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619001] system 00:09: ioport range 0x2300-0x23fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619004] system 00:09: ioport range 0x2400-0x24fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619006] system 00:09: ioport range 0x2500-0x25fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619009] system 00:09: ioport range 0x2600-0x26fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619012] system 00:09: ioport range 0x2700-0x27fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619015] system 00:09: ioport range 0x2800-0x28fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619017] system 00:09: ioport range 0x2900-0x29fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619020] system 00:09: ioport range 0x2a00-0x2afe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619023] system 00:09: ioport range 0x2b00-0x2bfe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619026] system 00:09: ioport range 0x2c00-0x2cfe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619028] system 00:09: ioport range 0x2d00-0x2dfe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619031] system 00:09: ioport range 0x2e00-0x2efe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619034] system 00:09: ioport range 0x2f00-0x2ffe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619037] system 00:09: ioport range 0x5000-0x50fe has been reserved
Sep  8 09:34:31 hopo kernel: [   14.619040] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
Sep  8 09:34:31 hopo kernel: [   14.619043] system 00:09: iomem range 0xfeda0000-0xfedacfff has been reserved
Sep  8 09:34:31 hopo kernel: [   14.649401] PCI: Bridge: 0000:00:01.0
Sep  8 09:34:31 hopo kernel: [   14.649402]   IO window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649405]   MEM window: dfc00000-dfcfffff
Sep  8 09:34:31 hopo kernel: [   14.649407]   PREFETCH window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649410] PCI: Bridge: 0000:00:1c.0
Sep  8 09:34:31 hopo kernel: [   14.649411]   IO window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649415]   MEM window: dfb00000-dfbfffff
Sep  8 09:34:31 hopo kernel: [   14.649418]   PREFETCH window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649421] PCI: Bridge: 0000:00:1c.4
Sep  8 09:34:31 hopo kernel: [   14.649422]   IO window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649426]   MEM window: dfa00000-dfafffff
Sep  8 09:34:31 hopo kernel: [   14.649429]   PREFETCH window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649432] PCI: Bridge: 0000:00:1e.0
Sep  8 09:34:31 hopo kernel: [   14.649433]   IO window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649437]   MEM window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649439]   PREFETCH window: disabled.
Sep  8 09:34:31 hopo kernel: [   14.649452] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:34:31 hopo kernel: [   14.649456] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  8 09:34:31 hopo kernel: [   14.649470] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:34:31 hopo kernel: [   14.649474] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  8 09:34:31 hopo kernel: [   14.649488] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:34:31 hopo kernel: [   14.649492] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  8 09:34:31 hopo kernel: [   14.649500] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep  8 09:34:31 hopo kernel: [   14.649508] NET: Registered protocol family 2
Sep  8 09:34:31 hopo kernel: [   14.686877] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  8 09:34:31 hopo kernel: [   14.687100] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  8 09:34:31 hopo kernel: [   14.687442] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  8 09:34:31 hopo kernel: [   14.687618] TCP: Hash tables configured (established 131072 bind 65536)
Sep  8 09:34:31 hopo kernel: [   14.687620] TCP reno registered
Sep  8 09:34:31 hopo kernel: [   14.698944] checking if image is initramfs... it is
Sep  8 09:34:31 hopo kernel: [   15.236787] Freeing initrd memory: 7471k freed
Sep  8 09:34:31 hopo kernel: [   15.236917] Simple Boot Flag at 0x7a set to 0x1
Sep  8 09:34:31 hopo kernel: [   15.237461] audit: initializing netlink socket (disabled)
Sep  8 09:34:31 hopo kernel: [   15.237472] audit(1252402444.804:1): initialized
Sep  8 09:34:31 hopo kernel: [   15.237652] highmem bounce pool size: 64 pages
Sep  8 09:34:31 hopo kernel: [   15.239304] VFS: Disk quotas dquot_6.5.1
Sep  8 09:34:31 hopo kernel: [   15.239367] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  8 09:34:31 hopo kernel: [   15.239474] io scheduler noop registered
Sep  8 09:34:31 hopo kernel: [   15.239475] io scheduler anticipatory registered
Sep  8 09:34:31 hopo kernel: [   15.239477] io scheduler deadline registered
Sep  8 09:34:31 hopo kernel: [   15.239485] io scheduler cfq registered (default)
Sep  8 09:34:31 hopo kernel: [   15.239495] Boot video device is 0000:00:02.0
Sep  8 09:34:31 hopo kernel: [   15.239669] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  8 09:34:31 hopo kernel: [   15.239697] assign_interrupt_mode Found MSI capability
Sep  8 09:34:31 hopo kernel: [   15.239721] Allocate Port Service[0000:00:01.0:pcie00]
Sep  8 09:34:31 hopo kernel: [   15.239784] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  8 09:34:31 hopo kernel: [   15.239817] assign_interrupt_mode Found MSI capability
Sep  8 09:34:31 hopo kernel: [   15.239844] Allocate Port Service[0000:00:1c.0:pcie00]
Sep  8 09:34:31 hopo kernel: [   15.239870] Allocate Port Service[0000:00:1c.0:pcie02]
Sep  8 09:34:31 hopo kernel: [   15.239939] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  8 09:34:31 hopo kernel: [   15.239973] assign_interrupt_mode Found MSI capability
Sep  8 09:34:31 hopo kernel: [   15.240000] Allocate Port Service[0000:00:1c.4:pcie00]
Sep  8 09:34:31 hopo kernel: [   15.240026] Allocate Port Service[0000:00:1c.4:pcie02]
Sep  8 09:34:31 hopo kernel: [   15.240224] isapnp: Scanning for PnP cards...
Sep  8 09:34:31 hopo kernel: [   15.593126] isapnp: No Plug & Play device found
Sep  8 09:34:31 hopo kernel: [   15.613633] Real Time Clock Driver v1.12ac
Sep  8 09:34:31 hopo kernel: [   15.613925] hpet_resources: 0xfed00000 is busy
Sep  8 09:34:31 hopo kernel: [   15.613939] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  8 09:34:31 hopo kernel: [   15.614050] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  8 09:34:31 hopo kernel: [   15.614567] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  8 09:34:31 hopo kernel: [   15.615195] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  8 09:34:31 hopo kernel: [   15.615250] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep  8 09:34:31 hopo kernel: [   15.615363] PNP: No PS/2 controller found. Probing ports directly.
Sep  8 09:34:31 hopo kernel: [   15.617899] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  8 09:34:31 hopo kernel: [   15.617904] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  8 09:34:31 hopo kernel: [   15.634628] mice: PS/2 mouse device common for all mice
Sep  8 09:34:31 hopo kernel: [   15.634724] EISA: Probing bus 0 at eisa.0
Sep  8 09:34:31 hopo kernel: [   15.634726] EISA: Cannot allocate resource for mainboard
Sep  8 09:34:31 hopo kernel: [   15.634731] Cannot allocate resource for EISA slot 2
Sep  8 09:34:31 hopo kernel: [   15.634739] Cannot allocate resource for EISA slot 5
Sep  8 09:34:31 hopo kernel: [   15.634750] EISA: Detected 0 cards.
Sep  8 09:34:31 hopo kernel: [   15.634752] cpuidle: using governor ladder
Sep  8 09:34:31 hopo kernel: [   15.634753] cpuidle: using governor menu
Sep  8 09:34:31 hopo kernel: [   15.634818] NET: Registered protocol family 1
Sep  8 09:34:31 hopo kernel: [   15.634843] Using IPI No-Shortcut mode
Sep  8 09:34:31 hopo kernel: [   15.634864] registered taskstats version 1
Sep  8 09:34:31 hopo kernel: [   15.634950]   Magic number: 9:600:575
Sep  8 09:34:31 hopo kernel: [   15.634970]   hash matches device ptyb7
Sep  8 09:34:31 hopo kernel: [   15.634994] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  8 09:34:31 hopo kernel: [   15.634995] EDD information not available.
Sep  8 09:34:31 hopo kernel: [   15.635169] Freeing unused kernel memory: 368k freed
Sep  8 09:34:31 hopo kernel: [   15.635189] Write protecting the kernel read-only data: 802k
Sep  8 09:34:31 hopo kernel: [   16.816036] fuse init (API version 7.9)
Sep  8 09:34:31 hopo kernel: [   16.833711] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep  8 09:34:31 hopo kernel: [   16.833721] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep  8 09:34:31 hopo kernel: [   17.098668] usbcore: registered new interface driver usbfs
Sep  8 09:34:31 hopo kernel: [   17.098690] usbcore: registered new interface driver hub
Sep  8 09:34:31 hopo kernel: [   17.098714] usbcore: registered new device driver usb
Sep  8 09:34:31 hopo kernel: [   17.107627] tg3.c:v3.86 (November 9, 2007)
Sep  8 09:34:31 hopo kernel: [   17.107647] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:34:31 hopo kernel: [   17.107655] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep  8 09:34:31 hopo kernel: [   17.115597] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 17
Sep  8 09:34:31 hopo kernel: [   17.115607] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Sep  8 09:34:31 hopo kernel: [   17.115610] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.115803] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Sep  8 09:34:31 hopo kernel: [   17.119719] ehci_hcd 0000:00:1a.7: debug port 1
Sep  8 09:34:31 hopo kernel: [   17.119724] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Sep  8 09:34:31 hopo kernel: [   17.119732] ehci_hcd 0000:00:1a.7: irq 17, io mem 0xdfdfbc00
Sep  8 09:34:31 hopo kernel: [   17.123628] USB Universal Host Controller Interface driver v3.0
Sep  8 09:34:31 hopo kernel: [   17.129059] eth0: Tigon3 [partno(BCM95754) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:19:b9:48:ca:0d
Sep  8 09:34:31 hopo kernel: [   17.129064] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Sep  8 09:34:31 hopo kernel: [   17.129066] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Sep  8 09:34:31 hopo kernel: [   17.139005] SCSI subsystem initialized
Sep  8 09:34:31 hopo kernel: [   17.144820] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  8 09:34:31 hopo kernel: [   17.144936] usb usb1: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.144958] hub 1-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.144963] hub 1-0:1.0: 4 ports detected
Sep  8 09:34:31 hopo kernel: [   17.173391] libata version 3.00 loaded.
Sep  8 09:34:31 hopo kernel: [   17.248734] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
Sep  8 09:34:31 hopo kernel: [   17.248747] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep  8 09:34:31 hopo kernel: [   17.248750] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.248771] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Sep  8 09:34:31 hopo kernel: [   17.252658] ehci_hcd 0000:00:1d.7: debug port 1
Sep  8 09:34:31 hopo kernel: [   17.252663] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Sep  8 09:34:31 hopo kernel: [   17.252671] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xff980800
Sep  8 09:34:31 hopo kernel: [   17.268613] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  8 09:34:31 hopo kernel: [   17.268707] usb usb2: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.268727] hub 2-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.268731] hub 2-0:1.0: 6 ports detected
Sep  8 09:34:31 hopo kernel: [   17.372719] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:34:31 hopo kernel: [   17.372730] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Sep  8 09:34:31 hopo kernel: [   17.372733] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.372754] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Sep  8 09:34:31 hopo kernel: [   17.372779] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
Sep  8 09:34:31 hopo kernel: [   17.372881] usb usb3: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.372902] hub 3-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.372907] hub 3-0:1.0: 2 ports detected
Sep  8 09:34:31 hopo kernel: [   17.473602] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 19
Sep  8 09:34:31 hopo kernel: [   17.473612] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Sep  8 09:34:31 hopo kernel: [   17.473615] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.473634] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Sep  8 09:34:31 hopo kernel: [   17.473658] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000ff00
Sep  8 09:34:31 hopo kernel: [   17.473750] usb usb4: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.473769] hub 4-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.473773] hub 4-0:1.0: 2 ports detected
Sep  8 09:34:31 hopo kernel: [   17.576603] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
Sep  8 09:34:31 hopo kernel: [   17.576614] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep  8 09:34:31 hopo kernel: [   17.576619] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.576646] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Sep  8 09:34:31 hopo kernel: [   17.576669] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
Sep  8 09:34:31 hopo kernel: [   17.576781] usb usb5: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.576801] hub 5-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.576805] hub 5-0:1.0: 2 ports detected
Sep  8 09:34:31 hopo kernel: [   17.680511] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 19
Sep  8 09:34:31 hopo kernel: [   17.680519] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep  8 09:34:31 hopo kernel: [   17.680522] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.680545] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Sep  8 09:34:31 hopo kernel: [   17.680566] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Sep  8 09:34:31 hopo kernel: [   17.680684] usb usb6: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.680702] hub 6-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.680706] hub 6-0:1.0: 2 ports detected
Sep  8 09:34:31 hopo kernel: [   17.784485] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Sep  8 09:34:31 hopo kernel: [   17.784493] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep  8 09:34:31 hopo kernel: [   17.784497] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep  8 09:34:31 hopo kernel: [   17.784520] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Sep  8 09:34:31 hopo kernel: [   17.784545] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
Sep  8 09:34:31 hopo kernel: [   17.784661] usb usb7: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   17.784680] hub 7-0:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   17.784683] hub 7-0:1.0: 2 ports detected
Sep  8 09:34:31 hopo kernel: [   17.891255] ata_piix 0000:00:1f.2: version 2.12
Sep  8 09:34:31 hopo kernel: [   17.891261] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Sep  8 09:34:31 hopo kernel: [   17.913336] usb 3-2: new full speed USB device using uhci_hcd and address 2
Sep  8 09:34:31 hopo kernel: [   18.045326] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
Sep  8 09:34:31 hopo kernel: [   18.045359] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep  8 09:34:31 hopo kernel: [   18.045417] scsi0 : ata_piix
Sep  8 09:34:31 hopo kernel: [   18.045574] scsi1 : ata_piix
Sep  8 09:34:31 hopo kernel: [   18.051404] ata1: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfec0 irq 21
Sep  8 09:34:31 hopo kernel: [   18.051407] ata2: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfec8 irq 21
Sep  8 09:34:31 hopo kernel: [   18.082602] usb 3-2: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   18.088534] hub 3-2:1.0: USB hub found
Sep  8 09:34:31 hopo kernel: [   18.089506] hub 3-2:1.0: 3 ports detected
Sep  8 09:34:31 hopo kernel: [   18.254219] ata1.00: ATA-7: ST3250820AS, 3.ADG, max UDMA/133
Sep  8 09:34:31 hopo kernel: [   18.254224] ata1.00: 488281250 sectors, multi 8: LBA48 NCQ (depth 0/32)
Sep  8 09:34:31 hopo kernel: [   18.320834] ata1.00: configured for UDMA/133
Sep  8 09:34:31 hopo kernel: [   18.440117] usb 6-1: new low speed USB device using uhci_hcd and address 2
Sep  8 09:34:31 hopo kernel: [   18.613305] usb 6-1: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   18.632114] ata2.01: NODEV after polling detection
Sep  8 09:34:31 hopo kernel: [   18.796133] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653A, D500, max UDMA/33
Sep  8 09:34:31 hopo kernel: [   18.796137] ata2.00: applying bridge limits
Sep  8 09:34:31 hopo kernel: [   18.821198] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
Sep  8 09:34:31 hopo kernel: [   18.961237] usb 3-2.1: configuration #1 chosen from 1 choice
Sep  8 09:34:31 hopo kernel: [   18.969075] ata2.00: configured for UDMA/33
Sep  8 09:34:31 hopo kernel: [   18.969176] scsi 0:0:0:0: Direct-Access     ATA      ST3250820AS      3.AD PQ: 0 ANSI: 5
Sep  8 09:34:31 hopo kernel: [   18.970034] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D500 PQ: 0 ANSI: 5
Sep  8 09:34:31 hopo kernel: [   18.970088] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Sep  8 09:34:31 hopo kernel: [   18.974143] usbcore: registered new interface driver hiddev
Sep  8 09:34:31 hopo kernel: [   18.987263] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input1
Sep  8 09:34:31 hopo kernel: [   19.015909] input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.1-1
Sep  8 09:34:31 hopo kernel: [   19.018362] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.1/3-2.1:1.0/input/input2
Sep  8 09:34:31 hopo kernel: [   19.031889] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.0-2.1
Sep  8 09:34:31 hopo kernel: [   19.036163] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.1/3-2.1:1.1/input/input3
Sep  8 09:34:31 hopo kernel: [   19.063847] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1a.0-2.1
Sep  8 09:34:31 hopo kernel: [   19.063860] usbcore: registered new interface driver usbhid
Sep  8 09:34:31 hopo kernel: [   19.063864] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Sep  8 09:34:31 hopo kernel: [   19.123801] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 21
Sep  8 09:34:31 hopo kernel: [   19.123835] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Sep  8 09:34:31 hopo kernel: [   19.123873] scsi2 : ata_piix
Sep  8 09:34:31 hopo kernel: [   19.124033] scsi3 : ata_piix
Sep  8 09:34:31 hopo kernel: [   19.124057] ata3: SATA max UDMA/133 cmd 0xfe40 ctl 0xfe50 bmdma 0xfed0 irq 21
Sep  8 09:34:31 hopo kernel: [   19.124059] ata4: SATA max UDMA/133 cmd 0xfe60 ctl 0xfe70 bmdma 0xfed8 irq 21
Sep  8 09:34:31 hopo kernel: [   20.786025] Driver 'sd' needs updating - please use bus_type methods
Sep  8 09:34:31 hopo kernel: [   20.786090] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Sep  8 09:34:31 hopo kernel: [   20.786099] sd 0:0:0:0: [sda] Write Protect is off
Sep  8 09:34:31 hopo kernel: [   20.786101] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  8 09:34:31 hopo kernel: [   20.786115] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  8 09:34:31 hopo kernel: [   20.786151] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Sep  8 09:34:31 hopo kernel: [   20.786159] sd 0:0:0:0: [sda] Write Protect is off
Sep  8 09:34:31 hopo kernel: [   20.786161] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  8 09:34:31 hopo kernel: [   20.786174] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  8 09:34:31 hopo kernel: [   20.786177]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep  8 09:34:31 hopo kernel: [   20.800038]  sda1 sda2 sda3 sda4
Sep  8 09:34:31 hopo kernel: [   20.820880] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  8 09:34:31 hopo kernel: [   20.824333] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  8 09:34:31 hopo kernel: [   20.824350] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  8 09:34:31 hopo kernel: [   20.829280] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Sep  8 09:34:31 hopo kernel: [   20.829284] Uniform CD-ROM driver Revision: 3.20
Sep  8 09:34:31 hopo kernel: [   20.829323] sr 1:0:0:0: Attached scsi CD-ROM sr0
Sep  8 09:34:31 hopo kernel: [   21.098575] Attempting manual resume
Sep  8 09:34:31 hopo kernel: [   21.098577] swsusp: Resume From Partition 8:4
Sep  8 09:34:31 hopo kernel: [   21.098579] PM: Checking swsusp image.
Sep  8 09:34:31 hopo kernel: [   21.098692] PM: Resume from disk failed.
Sep  8 09:34:31 hopo kernel: [   21.107872] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  8 09:34:31 hopo kernel: [   21.107874] EXT3-fs: write access will be enabled during recovery.
Sep  8 09:34:31 hopo kernel: [   21.198823] kjournald starting.  Commit interval 5 seconds
Sep  8 09:34:31 hopo kernel: [   21.198830] EXT3-fs: sda3: orphan cleanup on readonly fs
Sep  8 09:34:31 hopo kernel: [   21.198835] ext3_orphan_cleanup: deleting unreferenced inode 2546206
Sep  8 09:34:31 hopo kernel: [   21.198858] EXT3-fs: sda3: 1 orphan inode deleted
Sep  8 09:34:31 hopo kernel: [   21.198859] EXT3-fs: recovery complete.
Sep  8 09:34:31 hopo kernel: [   21.205232] EXT3-fs: mounted filesystem with ordered data mode.
Sep  8 09:34:31 hopo kernel: [   31.319585] input: PC Speaker as /devices/platform/pcspkr/input/input4
Sep  8 09:34:31 hopo kernel: [   31.848081] Linux agpgart interface v0.102
Sep  8 09:34:31 hopo kernel: [   31.890418] parport_pc 00:06: reported by Plug and Play ACPI
Sep  8 09:34:31 hopo kernel: [   31.890470] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Sep  8 09:34:31 hopo kernel: [   31.910422] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  8 09:34:31 hopo kernel: [   31.915498] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  8 09:34:31 hopo kernel: [   31.948095] iTCO_vendor_support: vendor-support=0
Sep  8 09:34:31 hopo kernel: [   31.965644] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep  8 09:34:31 hopo kernel: [   31.965711] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
Sep  8 09:34:31 hopo kernel: [   31.965720] iTCO_wdt: No card detected
Sep  8 09:34:31 hopo kernel: [   31.981978] input: Power Button (FF) as /devices/virtual/input/input5
Sep  8 09:34:31 hopo kernel: [   32.018000] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep  8 09:34:31 hopo kernel: [   32.033905] ACPI: Power Button (FF) [PWRF]
Sep  8 09:34:31 hopo kernel: [   32.033961] input: Power Button (CM) as /devices/virtual/input/input6
Sep  8 09:34:31 hopo kernel: [   32.057853] agpgart: Detected an Intel 965Q Chipset.
Sep  8 09:34:31 hopo kernel: [   32.058681] agpgart: Detected 7676K stolen memory.
Sep  8 09:34:31 hopo kernel: [   32.070220] agpgart: AGP aperture is 256M @ 0xc0000000
Sep  8 09:34:31 hopo kernel: [   32.109809] ACPI: Power Button (CM) [VBTN]
Sep  8 09:34:31 hopo kernel: [   32.848312] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:34:31 hopo kernel: [   32.848327] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep  8 09:34:31 hopo kernel: [   33.286861] lp0: using parport0 (interrupt-driven).
Sep  8 09:34:31 hopo kernel: [   33.322604] Adding 2000084k swap on /dev/sda4.  Priority:-1 extents:1 across:2000084k
Sep  8 09:34:31 hopo kernel: [   33.861092] EXT3 FS on sda3, internal journal
Sep  8 09:34:31 hopo kernel: [   39.267839] kjournald starting.  Commit interval 5 seconds
Sep  8 09:34:31 hopo kernel: [   39.267843] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Sep  8 09:34:31 hopo kernel: [   39.268031] EXT3 FS on sda2, internal journal
Sep  8 09:34:31 hopo kernel: [   39.268035] EXT3-fs: mounted filesystem with ordered data mode.
Sep  8 09:34:31 hopo kernel: [   39.951830] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep  8 09:34:31 hopo kernel: [   41.587429] No dock devices found.
Sep  8 09:34:31 hopo kernel: [   41.588307] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1: found ejectable bay
Sep  8 09:34:31 hopo kernel: [   41.588311] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1: Adding notify handler
Sep  8 09:34:31 hopo kernel: [   41.588339] ACPI: Error installing bay notify handler
Sep  8 09:34:31 hopo kernel: [   41.588341] ACPI: Bay [\_SB_.PCI0.IDE1.PRI1.MAS1] Added
Sep  8 09:34:32 hopo NetworkManager: <info>  starting... 
Sep  8 09:34:32 hopo avahi-daemon[5070]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep  8 09:34:32 hopo avahi-daemon[5070]: Successfully dropped root privileges.
Sep  8 09:34:32 hopo avahi-daemon[5070]: avahi-daemon 0.6.22 starting up.
Sep  8 09:34:32 hopo avahi-daemon[5070]: Successfully called chroot().
Sep  8 09:34:32 hopo avahi-daemon[5070]: Successfully dropped remaining capabilities.
Sep  8 09:34:32 hopo avahi-daemon[5070]: No service file found in /etc/avahi/services.
Sep  8 09:34:32 hopo avahi-daemon[5070]: Network interface enumeration completed.
Sep  8 09:34:32 hopo avahi-daemon[5070]: Registering HINFO record with values 'I686'/'LINUX'.
Sep  8 09:34:32 hopo avahi-daemon[5070]: Server startup complete. Host name is hopo.local. Local service cookie is 1654119478.
Sep  8 09:34:32 hopo kernel: [   42.508850] ppdev: user-space parallel port driver
Sep  8 09:34:32 hopo kernel: [   42.788961] audit(1252420472.586:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5124 profile="/usr/sbin/cupsd" namespace="default"
Sep  8 09:34:32 hopo kernel: [   42.789054] audit(1252420472.586:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=5124 profile="/usr/sbin/cupsd" namespace="default"
Sep  8 09:34:32 hopo slapd[5134]: @(#) $OpenLDAP: slapd 2.4.9 (Mar 31 2009 07:12:16) $ ^Ibuildd@rothera:/build/buildd/openldap2.3-2.4.9/debian/build/servers/slapd 
Sep  8 09:34:32 hopo slapd[5134]: daemon: IPv6 socket() failed errno=97 (Address family not supported by protocol) 
Sep  8 09:34:33 hopo slapd[5139]: hdb_db_open: database "dc=hopo,dc=local": unclean shutdown detected; attempting recovery. 
Sep  8 09:34:33 hopo slapd[5139]: slapd starting 
Sep  8 09:34:33 hopo kernel: [   43.640115] /dev/vmmon[5150]: Module vmmon: registered with major=10 minor=165
Sep  8 09:34:33 hopo kernel: [   43.640126] /dev/vmmon[5150]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Sep  8 09:34:33 hopo kernel: [   43.640130] /dev/vmmon[5150]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Sep  8 09:34:33 hopo kernel: [   43.640132] /dev/vmmon[5150]: Module vmmon: initialized
Sep  8 09:34:33 hopo kernel: [   43.714182] /dev/vmci[5162]: VMCI: Driver initialized.
Sep  8 09:34:33 hopo kernel: [   43.714214] /dev/vmci[5162]: Module vmci: registered with major=10 minor=63
Sep  8 09:34:33 hopo kernel: [   43.714216] /dev/vmci[5162]: Module vmci: initialized
Sep  8 09:34:33 hopo vmnetBridge: Daemon created. 
Sep  8 09:34:33 hopo vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001002 
Sep  8 09:34:33 hopo vmnetBridge: Can't remove interface eth0 2 (does not exist). 
Sep  8 09:34:41 hopo vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Sep  8 09:34:41 hopo vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Sep  8 09:34:41 hopo vmnet-dhcpd: All rights reserved.
Sep  8 09:34:41 hopo vmnet-dhcpd: 
Sep  8 09:34:41 hopo vmnet-dhcpd: Please contribute if you find this software useful.
Sep  8 09:34:41 hopo vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Sep  8 09:34:41 hopo vmnet-dhcpd: 
Sep  8 09:34:41 hopo vmnet-dhcpd: Configured subnet: 192.168.72.0
Sep  8 09:34:41 hopo vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.72.254
Sep  8 09:34:41 hopo vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.72.0
Sep  8 09:34:41 hopo vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.72.0
Sep  8 09:34:41 hopo kernel: [   52.110337] /dev/vmnet: open called by PID 5722 (vmnet-dhcpd)
Sep  8 09:34:41 hopo kernel: [   52.110345] /dev/vmnet: hub 1 does not exist, allocating memory.
Sep  8 09:34:41 hopo kernel: [   52.110353] /dev/vmnet: port on hub 1 successfully opened
Sep  8 09:34:41 hopo kernel: [   52.166501] /dev/vmnet: open called by PID 5726 (vmnet-netifup)
Sep  8 09:34:41 hopo kernel: [   52.166512] /dev/vmnet: port on hub 1 successfully opened
Sep  8 09:34:41 hopo avahi-daemon[5070]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.72.1.
Sep  8 09:34:41 hopo avahi-daemon[5070]: New relevant interface vmnet1.IPv4 for mDNS.
Sep  8 09:34:41 hopo avahi-daemon[5070]: Registering new address record for 192.168.72.1 on vmnet1.IPv4.
Sep  8 09:34:41 hopo vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Sep  8 09:34:41 hopo vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Sep  8 09:34:41 hopo vmnet-dhcpd: All rights reserved.
Sep  8 09:34:41 hopo vmnet-dhcpd: 
Sep  8 09:34:41 hopo vmnet-dhcpd: Please contribute if you find this software useful.
Sep  8 09:34:41 hopo vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Sep  8 09:34:41 hopo vmnet-dhcpd: 
Sep  8 09:34:41 hopo vmnet-dhcpd: Configured subnet: 192.168.71.0
Sep  8 09:34:41 hopo vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.71.254
Sep  8 09:34:41 hopo vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.71.0
Sep  8 09:34:41 hopo vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.71.0
Sep  8 09:34:41 hopo kernel: [   52.198231] /dev/vmnet: open called by PID 5729 (vmnet-dhcpd)
Sep  8 09:34:41 hopo kernel: [   52.198239] /dev/vmnet: hub 8 does not exist, allocating memory.
Sep  8 09:34:41 hopo kernel: [   52.198247] /dev/vmnet: port on hub 8 successfully opened
Sep  8 09:34:42 hopo kernel: [   52.256062] /dev/vmnet: open called by PID 5731 (vmnet-natd)
Sep  8 09:34:42 hopo kernel: [   52.256072] /dev/vmnet: port on hub 8 successfully opened
Sep  8 09:34:42 hopo kernel: [   52.304859] /dev/vmnet: open called by PID 5735 (vmnet-netifup)
Sep  8 09:34:42 hopo kernel: [   52.304871] /dev/vmnet: port on hub 8 successfully opened
Sep  8 09:34:42 hopo avahi-daemon[5070]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.71.1.
Sep  8 09:34:42 hopo avahi-daemon[5070]: New relevant interface vmnet8.IPv4 for mDNS.
Sep  8 09:34:42 hopo avahi-daemon[5070]: Registering new address record for 192.168.71.1 on vmnet8.IPv4.
Sep  8 09:34:42 hopo vmnet-detect[5739]: NetDetectDaemonInit: No host policy file found. Not initializing filter. 
Sep  8 09:34:42 hopo vmnet-detect[5739]: Unable to initialize the daemon 
Sep  8 09:34:42 hopo kernel: [   52.607449] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Sep  8 09:34:42 hopo kernel: [   52.607452] apm: disabled - APM is not SMP safe.
Sep  8 09:34:42 hopo kernel: [   52.779975] RPC: Registered udp transport module.
Sep  8 09:34:42 hopo kernel: [   52.779979] RPC: Registered tcp transport module.
Sep  8 09:34:42 hopo kernel: [   52.857236] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Sep  8 09:34:42 hopo kernel: [   52.896877] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep  8 09:34:42 hopo kernel: [   52.910240] NFSD: starting 90-second grace period
```

By comparison, here's a successful boot (not sure where to stop pasting, if you need more to be helpful just ask):

```
Sep  8 09:49:51 hopo syslogd 1.5.0#1ubuntu1: restart.
Sep  8 09:49:51 hopo kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep  8 09:49:51 hopo kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep  8 09:49:51 hopo kernel: Symbols match kernel version 2.6.24.
Sep  8 09:49:51 hopo kernel: Loaded 15112 symbols from 77 modules.
Sep  8 09:49:51 hopo kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  8 09:49:51 hopo kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  8 09:49:51 hopo kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep  8 09:49:51 hopo kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5ffc00 (usable)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 000000007f5ffc00 - 000000007f601c00 (ACPI NVS)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 000000007f603c00 - 000000007f653c00 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 000000007f653c00 - 000000007f655c00 (ACPI data)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 000000007f655c00 - 0000000080000000 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep  8 09:49:51 hopo kernel: [    0.000000] 1141MB HIGHMEM available.
Sep  8 09:49:51 hopo kernel: [    0.000000] 896MB LOWMEM available.
Sep  8 09:49:51 hopo kernel: [    0.000000] found SMP MP-table at 000fe710
Sep  8 09:49:51 hopo kernel: [    0.000000] Entering add_active_range(0, 0, 521727) 0 entries of 256 used
Sep  8 09:49:51 hopo kernel: [    0.000000] Zone PFN ranges:
Sep  8 09:49:51 hopo kernel: [    0.000000]   DMA             0 ->     4096
Sep  8 09:49:51 hopo kernel: [    0.000000]   Normal       4096 ->   229376
Sep  8 09:49:51 hopo kernel: [    0.000000]   HighMem    229376 ->   521727
Sep  8 09:49:51 hopo kernel: [    0.000000] Movable zone start PFN for each node
Sep  8 09:49:51 hopo kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  8 09:49:51 hopo kernel: [    0.000000]     0:        0 ->   521727
Sep  8 09:49:51 hopo kernel: [    0.000000] On node 0 totalpages: 521727
Sep  8 09:49:51 hopo kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep  8 09:49:51 hopo kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  8 09:49:51 hopo kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep  8 09:49:51 hopo kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Sep  8 09:49:51 hopo kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Sep  8 09:49:51 hopo kernel: [    0.000000]   HighMem zone: 2283 pages used for memmap
Sep  8 09:49:51 hopo kernel: [    0.000000]   HighMem zone: 290068 pages, LIFO batch:31
Sep  8 09:49:51 hopo kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep  8 09:49:51 hopo kernel: [    0.000000] DMI 2.3 present.
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FEBF0 checksum 0
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: XSDT 000FCE99, 006C (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: FACP 000FCFC1, 00F4 (r3 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: DSDT FFF6A119, 473C (r1   DELL    dt_ex     1000 INTL 20050624)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: FACS 7F5FFC00, 0040
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: SSDT FFF6E974, 00AA (r1   DELL    st_ex     1000 INTL 20050624)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: APIC 000FD0B5, 0092 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: BOOT 000FD147, 0028 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: ASF! 000FD16F, 0092 (r32 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: MCFG 000FD201, 003E (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: HPET 000FD23F, 0038 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: TCPA 000FD49B, 0032 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: SLIC 000FD277, 0176 (r1 DELL    B8K           14 ASL        61)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] Processor #0 6:15 APIC version 20
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] Processor #1 6:15 APIC version 20
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Sep  8 09:49:51 hopo kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  8 09:49:51 hopo kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  8 09:49:51 hopo kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Sep  8 09:49:51 hopo kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  8 09:49:51 hopo kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep  8 09:49:51 hopo kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000f0000
Sep  8 09:49:51 hopo kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Sep  8 09:49:51 hopo kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517652
Sep  8 09:49:51 hopo kernel: [    0.000000] Kernel command line: root=UUID=a45e6f05-9d59-432a-b705-4a6c8eff02aa ro quiet splash
Sep  8 09:49:51 hopo kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Sep  8 09:49:51 hopo kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Sep  8 09:49:51 hopo kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep  8 09:49:51 hopo kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep  8 09:49:51 hopo kernel: [    0.000000] Initializing CPU#0
Sep  8 09:49:51 hopo kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  8 09:49:51 hopo kernel: [    0.000000] Detected 2128.062 MHz processor.
Sep  8 09:49:51 hopo kernel: [    9.782735] Console: colour VGA+ 80x25
Sep  8 09:49:51 hopo kernel: [    9.782738] console [tty0] enabled
Sep  8 09:49:51 hopo kernel: [    9.783004] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  8 09:49:51 hopo kernel: [    9.783262] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  8 09:49:51 hopo kernel: [    9.856689] Memory: 2056888k/2086908k available (2181k kernel code, 28796k reserved, 1006k data, 368k init, 1169404k highmem)
Sep  8 09:49:51 hopo kernel: [    9.856694] virtual kernel memory layout:
Sep  8 09:49:51 hopo kernel: [    9.856695]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep  8 09:49:51 hopo kernel: [    9.856696]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  8 09:49:51 hopo kernel: [    9.856697]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  8 09:49:51 hopo kernel: [    9.856698]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  8 09:49:51 hopo kernel: [    9.856698]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep  8 09:49:51 hopo kernel: [    9.856699]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep  8 09:49:51 hopo kernel: [    9.856700]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep  8 09:49:51 hopo kernel: [    9.856703] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  8 09:49:51 hopo kernel: [    9.856737] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Sep  8 09:49:51 hopo kernel: [    9.856853] hpet clockevent registered
Sep  8 09:49:51 hopo kernel: [    9.936823] Calibrating delay using timer specific routine.. 4259.15 BogoMIPS (lpj=8518311)
Sep  8 09:49:51 hopo kernel: [    9.936841] Security Framework initialized
Sep  8 09:49:51 hopo kernel: [    9.936847] SELinux:  Disabled at boot.
Sep  8 09:49:51 hopo kernel: [    9.936858] AppArmor: AppArmor initialized
Sep  8 09:49:51 hopo kernel: [    9.936861] Failure registering capabilities with primary security module.
Sep  8 09:49:51 hopo kernel: [    9.936868] Mount-cache hash table entries: 512
Sep  8 09:49:51 hopo kernel: [    9.936969] Initializing cgroup subsys ns
Sep  8 09:49:51 hopo kernel: [    9.936975] Initializing cgroup subsys cpuacct
Sep  8 09:49:51 hopo kernel: [    9.936983] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
Sep  8 09:49:51 hopo kernel: [    9.936989] monitor/mwait feature present.
Sep  8 09:49:51 hopo kernel: [    9.936990] using mwait in idle threads.
Sep  8 09:49:51 hopo kernel: [    9.936993] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  8 09:49:51 hopo kernel: [    9.936995] CPU: L2 cache: 2048K
Sep  8 09:49:51 hopo kernel: [    9.936997] CPU: Physical Processor ID: 0
Sep  8 09:49:51 hopo kernel: [    9.936999] CPU: Processor Core ID: 0
Sep  8 09:49:51 hopo kernel: [    9.937001] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000000
Sep  8 09:49:51 hopo kernel: [    9.937009] Compat vDSO mapped to ffffe000.
Sep  8 09:49:51 hopo kernel: [    9.937020] Checking 'hlt' instruction... OK.
Sep  8 09:49:51 hopo kernel: [    9.953195] SMP alternatives: switching to UP code
Sep  8 09:49:51 hopo kernel: [    9.954544] Early unpacking initramfs... done
Sep  8 09:49:51 hopo kernel: [   10.226641] ACPI: Core revision 20070126
Sep  8 09:49:51 hopo kernel: [   10.302141] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep  8 09:49:51 hopo kernel: [   10.429422] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 02
Sep  8 09:49:51 hopo kernel: [   10.429435] SMP alternatives: switching to SMP code
Sep  8 09:49:51 hopo kernel: [   10.430029] Booting processor 1/1 eip 3000
Sep  8 09:49:51 hopo kernel: [   10.440167] Initializing CPU#1
Sep  8 09:49:51 hopo kernel: [   10.520567] Calibrating delay using timer specific routine.. 4256.00 BogoMIPS (lpj=8512019)
Sep  8 09:49:51 hopo kernel: [   10.520573] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
Sep  8 09:49:51 hopo kernel: [   10.520577] monitor/mwait feature present.
Sep  8 09:49:51 hopo kernel: [   10.520580] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  8 09:49:51 hopo kernel: [   10.520582] CPU: L2 cache: 2048K
Sep  8 09:49:51 hopo kernel: [   10.520584] CPU: Physical Processor ID: 0
Sep  8 09:49:51 hopo kernel: [   10.520585] CPU: Processor Core ID: 1
Sep  8 09:49:51 hopo kernel: [   10.520586] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000000
Sep  8 09:49:51 hopo kernel: [   10.521014] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 02
Sep  8 09:49:51 hopo kernel: [   10.521030] Total of 2 processors activated (8515.16 BogoMIPS).
Sep  8 09:49:51 hopo kernel: [   10.521169] ENABLING IO-APIC IRQs
Sep  8 09:49:51 hopo kernel: [   10.521329] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  8 09:49:51 hopo kernel: [   10.668593] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep  8 09:49:51 hopo kernel: [   10.688599] Brought up 2 CPUs
Sep  8 09:49:51 hopo kernel: [   10.688620] CPU0 attaching sched-domain:
Sep  8 09:49:51 hopo kernel: [   10.688622]  domain 0: span 03
Sep  8 09:49:51 hopo kernel: [   10.688623]   groups: 01 02
Sep  8 09:49:51 hopo kernel: [   10.688626] CPU1 attaching sched-domain:
Sep  8 09:49:51 hopo kernel: [   10.688627]  domain 0: span 03
Sep  8 09:49:51 hopo kernel: [   10.688628]   groups: 02 01
Sep  8 09:49:51 hopo kernel: [   10.688816] net_namespace: 64 bytes
Sep  8 09:49:51 hopo kernel: [   10.688827] Booting paravirtualized kernel on bare hardware
Sep  8 09:49:51 hopo kernel: [   10.689186] Time:  9:49:27  Date: 09/08/09
Sep  8 09:49:51 hopo kernel: [   10.689208] NET: Registered protocol family 16
Sep  8 09:49:51 hopo kernel: [   10.689370] EISA bus registered
Sep  8 09:49:51 hopo kernel: [   10.689373] ACPI: bus type pci registered
Sep  8 09:49:51 hopo kernel: [   10.723304] PCI: PCI BIOS revision 2.10 entry at 0xfb578, last bus=4
Sep  8 09:49:51 hopo kernel: [   10.723305] PCI: Using configuration type 1
Sep  8 09:49:51 hopo kernel: [   10.723325] Setting up standard PCI resources
Sep  8 09:49:51 hopo kernel: [   10.735487] ACPI: EC: Look up EC in DSDT
Sep  8 09:49:51 hopo kernel: [   10.785522] ACPI: BIOS _OSI(Linux) query ignored
Sep  8 09:49:51 hopo kernel: [   10.785524] ACPI: DMI System Vendor: Dell Inc.                
Sep  8 09:49:51 hopo kernel: [   10.785525] ACPI: DMI Product Name: OptiPlex 745                 
Sep  8 09:49:51 hopo kernel: [   10.785527] ACPI: DMI Product Version: 
Sep  8 09:49:51 hopo kernel: [   10.785528] ACPI: DMI Board Name: 0MM599
Sep  8 09:49:51 hopo kernel: [   10.785529] ACPI: DMI BIOS Vendor: Dell Inc.                
Sep  8 09:49:51 hopo kernel: [   10.785530] ACPI: DMI BIOS Date: 05/21/2007
Sep  8 09:49:51 hopo kernel: [   10.785531] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
Sep  8 09:49:51 hopo kernel: [   10.785533] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
Sep  8 09:49:51 hopo kernel: [   10.804809] ACPI: Interpreter enabled
Sep  8 09:49:51 hopo kernel: [   10.804811] ACPI: (supports S0 S1 S3 S4 S5)
Sep  8 09:49:51 hopo kernel: [   10.804824] ACPI: Using IOAPIC for interrupt routing
Sep  8 09:49:51 hopo kernel: [   10.901009] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  8 09:49:51 hopo kernel: [   10.901636] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Sep  8 09:49:51 hopo kernel: [   10.901640] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
Sep  8 09:49:51 hopo kernel: [   10.902073] PCI: Transparent bridge - 0000:00:1e.0
Sep  8 09:49:51 hopo kernel: [   10.902098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  8 09:49:51 hopo kernel: [   10.902829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
Sep  8 09:49:51 hopo kernel: [   10.903469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Sep  8 09:49:51 hopo kernel: [   10.903939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Sep  8 09:49:51 hopo kernel: [   10.904412] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
Sep  8 09:49:51 hopo kernel: [   12.048125] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Sep  8 09:49:51 hopo kernel: [   12.048883] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Sep  8 09:49:51 hopo kernel: [   12.049650] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
Sep  8 09:49:51 hopo kernel: [   12.050400] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Sep  8 09:49:51 hopo kernel: [   12.051151] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Sep  8 09:49:51 hopo kernel: [   12.051910] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Sep  8 09:49:51 hopo kernel: [   12.052667] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Sep  8 09:49:51 hopo kernel: [   12.053432] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Sep  8 09:49:51 hopo kernel: [   12.053820] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 89 [20070126]
Sep  8 09:49:51 hopo kernel: [   12.053826] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  8 09:49:51 hopo kernel: [   12.053850] pnp: PnP ACPI init
Sep  8 09:49:51 hopo kernel: [   12.053855] ACPI: bus type pnp registered
Sep  8 09:49:51 hopo kernel: [   12.110057] pnpacpi: exceeded the max number of IO resources: 40 
Sep  8 09:49:51 hopo kernel: [   12.110323] pnp: PnP ACPI: found 11 devices
Sep  8 09:49:51 hopo kernel: [   12.110325] ACPI: ACPI bus type pnp unregistered
Sep  8 09:49:51 hopo kernel: [   12.110328] PnPBIOS: Disabled by ACPI PNP
Sep  8 09:49:51 hopo kernel: [   12.110505] PCI: Using ACPI for IRQ routing
Sep  8 09:49:51 hopo kernel: [   12.110508] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  8 09:49:51 hopo kernel: [   12.152111] NET: Registered protocol family 8
Sep  8 09:49:51 hopo kernel: [   12.152113] NET: Registered protocol family 20
Sep  8 09:49:51 hopo kernel: [   12.152147] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep  8 09:49:51 hopo kernel: [   12.152152] hpet0: 3 64-bit timers, 14318180 Hz
Sep  8 09:49:51 hopo kernel: [   12.153177] AppArmor: AppArmor Filesystem Enabled
Sep  8 09:49:51 hopo kernel: [   12.156032] Time: tsc clocksource has been installed.
Sep  8 09:49:51 hopo kernel: [   12.156043] Switched to high resolution mode on CPU 0
Sep  8 09:49:51 hopo kernel: [   12.156127] Switched to high resolution mode on CPU 1
Sep  8 09:49:51 hopo kernel: [   12.168982] system 00:01: ioport range 0x800-0x85f has been reserved
Sep  8 09:49:51 hopo kernel: [   12.168985] system 00:01: ioport range 0xc00-0xc7f has been reserved
Sep  8 09:49:51 hopo kernel: [   12.168988] system 00:01: ioport range 0x860-0x8ff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.168998] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169002] system 00:08: iomem range 0x100000-0xffffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169005] system 00:08: iomem range 0x1000000-0x7f5ffbff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169008] system 00:08: iomem range 0xf0000-0xfffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169010] system 00:08: iomem range 0xc0000-0xcffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169014] system 00:08: iomem range 0xfec00000-0xfecfffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169017] system 00:08: iomem range 0xfee00000-0xfeefffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169020] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169023] system 00:08: iomem range 0xffc00000-0xffffffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169028] system 00:09: ioport range 0x100-0x1fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169031] system 00:09: ioport range 0x200-0x277 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169034] system 00:09: ioport range 0x280-0x2e7 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169036] system 00:09: ioport range 0x2f0-0x2f7 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169039] system 00:09: ioport range 0x300-0x377 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169042] system 00:09: ioport range 0x380-0x3bb has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169044] system 00:09: ioport range 0x3c0-0x3e7 could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169047] system 00:09: ioport range 0x3f6-0x3f7 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169050] system 00:09: ioport range 0x400-0x4cf has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169052] system 00:09: ioport range 0x4d2-0x57f has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169055] system 00:09: ioport range 0x580-0x677 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169058] system 00:09: ioport range 0x680-0x777 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169060] system 00:09: ioport range 0x780-0x7bb has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169063] system 00:09: ioport range 0x7c0-0x7ff has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169066] system 00:09: ioport range 0x8e0-0x8ff has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169068] system 00:09: ioport range 0x900-0x9fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169071] system 00:09: ioport range 0xa00-0xafe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169073] system 00:09: ioport range 0xb00-0xbfe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169076] system 00:09: ioport range 0xc80-0xcaf has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169079] system 00:09: ioport range 0xcc0-0xcf7 has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169081] system 00:09: ioport range 0xd00-0xdfe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169084] system 00:09: ioport range 0xe00-0xefe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169087] system 00:09: ioport range 0xf00-0xffe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169090] system 00:09: ioport range 0x2000-0x20fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169092] system 00:09: ioport range 0x2100-0x21fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169095] system 00:09: ioport range 0x2200-0x22fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169098] system 00:09: ioport range 0x2300-0x23fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169100] system 00:09: ioport range 0x2400-0x24fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169103] system 00:09: ioport range 0x2500-0x25fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169106] system 00:09: ioport range 0x2600-0x26fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169109] system 00:09: ioport range 0x2700-0x27fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169111] system 00:09: ioport range 0x2800-0x28fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169114] system 00:09: ioport range 0x2900-0x29fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169117] system 00:09: ioport range 0x2a00-0x2afe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169120] system 00:09: ioport range 0x2b00-0x2bfe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169122] system 00:09: ioport range 0x2c00-0x2cfe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169125] system 00:09: ioport range 0x2d00-0x2dfe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169128] system 00:09: ioport range 0x2e00-0x2efe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169131] system 00:09: ioport range 0x2f00-0x2ffe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169133] system 00:09: ioport range 0x5000-0x50fe has been reserved
Sep  8 09:49:51 hopo kernel: [   12.169136] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
Sep  8 09:49:51 hopo kernel: [   12.169139] system 00:09: iomem range 0xfeda0000-0xfedacfff has been reserved
Sep  8 09:49:51 hopo kernel: [   12.199494] PCI: Bridge: 0000:00:01.0
Sep  8 09:49:51 hopo kernel: [   12.199496]   IO window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199499]   MEM window: dfc00000-dfcfffff
Sep  8 09:49:51 hopo kernel: [   12.199501]   PREFETCH window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199504] PCI: Bridge: 0000:00:1c.0
Sep  8 09:49:51 hopo kernel: [   12.199505]   IO window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199508]   MEM window: dfb00000-dfbfffff
Sep  8 09:49:51 hopo kernel: [   12.199511]   PREFETCH window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199515] PCI: Bridge: 0000:00:1c.4
Sep  8 09:49:51 hopo kernel: [   12.199516]   IO window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199519]   MEM window: dfa00000-dfafffff
Sep  8 09:49:51 hopo kernel: [   12.199522]   PREFETCH window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199526] PCI: Bridge: 0000:00:1e.0
Sep  8 09:49:51 hopo kernel: [   12.199527]   IO window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199530]   MEM window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199533]   PREFETCH window: disabled.
Sep  8 09:49:51 hopo kernel: [   12.199545] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:49:51 hopo kernel: [   12.199549] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  8 09:49:51 hopo kernel: [   12.199563] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:49:51 hopo kernel: [   12.199567] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  8 09:49:51 hopo kernel: [   12.199581] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:49:51 hopo kernel: [   12.199585] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  8 09:49:51 hopo kernel: [   12.199594] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep  8 09:49:51 hopo kernel: [   12.199602] NET: Registered protocol family 2
Sep  8 09:49:51 hopo kernel: [   12.236972] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  8 09:49:51 hopo kernel: [   12.237196] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  8 09:49:51 hopo kernel: [   12.237540] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  8 09:49:51 hopo kernel: [   12.237720] TCP: Hash tables configured (established 131072 bind 65536)
Sep  8 09:49:51 hopo kernel: [   12.237722] TCP reno registered
Sep  8 09:49:51 hopo kernel: [   12.249045] checking if image is initramfs... it is
Sep  8 09:49:51 hopo kernel: [   12.786850] Freeing initrd memory: 7471k freed
Sep  8 09:49:51 hopo kernel: [   12.786979] Simple Boot Flag at 0x7a set to 0x1
Sep  8 09:49:51 hopo kernel: [   12.787515] audit: initializing netlink socket (disabled)
Sep  8 09:49:51 hopo kernel: [   12.787526] audit(1252403368.804:1): initialized
Sep  8 09:49:51 hopo kernel: [   12.787712] highmem bounce pool size: 64 pages
Sep  8 09:49:51 hopo kernel: [   12.789365] VFS: Disk quotas dquot_6.5.1
Sep  8 09:49:51 hopo kernel: [   12.789427] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  8 09:49:51 hopo kernel: [   12.789532] io scheduler noop registered
Sep  8 09:49:51 hopo kernel: [   12.789534] io scheduler anticipatory registered
Sep  8 09:49:51 hopo kernel: [   12.789535] io scheduler deadline registered
Sep  8 09:49:51 hopo kernel: [   12.789543] io scheduler cfq registered (default)
Sep  8 09:49:51 hopo kernel: [   12.789554] Boot video device is 0000:00:02.0
Sep  8 09:49:51 hopo kernel: [   12.789729] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  8 09:49:51 hopo kernel: [   12.789757] assign_interrupt_mode Found MSI capability
Sep  8 09:49:51 hopo kernel: [   12.789782] Allocate Port Service[0000:00:01.0:pcie00]
Sep  8 09:49:51 hopo kernel: [   12.789845] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  8 09:49:51 hopo kernel: [   12.789879] assign_interrupt_mode Found MSI capability
Sep  8 09:49:51 hopo kernel: [   12.789906] Allocate Port Service[0000:00:1c.0:pcie00]
Sep  8 09:49:51 hopo kernel: [   12.789932] Allocate Port Service[0000:00:1c.0:pcie02]
Sep  8 09:49:51 hopo kernel: [   12.789999] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  8 09:49:51 hopo kernel: [   12.790033] assign_interrupt_mode Found MSI capability
Sep  8 09:49:51 hopo kernel: [   12.790060] Allocate Port Service[0000:00:1c.4:pcie00]
Sep  8 09:49:51 hopo kernel: [   12.790086] Allocate Port Service[0000:00:1c.4:pcie02]
Sep  8 09:49:51 hopo kernel: [   12.790289] isapnp: Scanning for PnP cards...
Sep  8 09:49:51 hopo kernel: [   13.143191] isapnp: No Plug & Play device found
Sep  8 09:49:51 hopo kernel: [   13.163508] Real Time Clock Driver v1.12ac
Sep  8 09:49:51 hopo kernel: [   13.163802] hpet_resources: 0xfed00000 is busy
Sep  8 09:49:51 hopo kernel: [   13.163815] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  8 09:49:51 hopo kernel: [   13.163927] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  8 09:49:51 hopo kernel: [   13.164438] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  8 09:49:51 hopo kernel: [   13.165062] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  8 09:49:51 hopo kernel: [   13.165119] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep  8 09:49:51 hopo kernel: [   13.165233] PNP: No PS/2 controller found. Probing ports directly.
Sep  8 09:49:51 hopo kernel: [   13.167763] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  8 09:49:51 hopo kernel: [   13.167766] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  8 09:49:51 hopo kernel: [   13.184594] mice: PS/2 mouse device common for all mice
Sep  8 09:49:51 hopo kernel: [   13.184715] EISA: Probing bus 0 at eisa.0
Sep  8 09:49:51 hopo kernel: [   13.184717] EISA: Cannot allocate resource for mainboard
Sep  8 09:49:51 hopo kernel: [   13.184723] Cannot allocate resource for EISA slot 2
Sep  8 09:49:51 hopo kernel: [   13.184742] Cannot allocate resource for EISA slot 5
Sep  8 09:49:51 hopo kernel: [   13.184752] EISA: Detected 0 cards.
Sep  8 09:49:51 hopo kernel: [   13.184755] cpuidle: using governor ladder
Sep  8 09:49:51 hopo kernel: [   13.184756] cpuidle: using governor menu
Sep  8 09:49:51 hopo kernel: [   13.184820] NET: Registered protocol family 1
Sep  8 09:49:51 hopo kernel: [   13.184844] Using IPI No-Shortcut mode
Sep  8 09:49:51 hopo kernel: [   13.184868] registered taskstats version 1
Sep  8 09:49:51 hopo kernel: [   13.184953]   Magic number: 9:359:828
Sep  8 09:49:51 hopo kernel: [   13.184977]   hash matches device ptyt8
Sep  8 09:49:51 hopo kernel: [   13.184981]   hash matches device ptyqb
Sep  8 09:49:51 hopo kernel: [   13.184994] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  8 09:49:51 hopo kernel: [   13.184996] EDD information not available.
Sep  8 09:49:51 hopo kernel: [   13.185165] Freeing unused kernel memory: 368k freed
Sep  8 09:49:51 hopo kernel: [   13.185185] Write protecting the kernel read-only data: 802k
Sep  8 09:49:51 hopo kernel: [   14.365791] fuse init (API version 7.9)
Sep  8 09:49:51 hopo kernel: [   14.383816] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep  8 09:49:51 hopo kernel: [   14.383828] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep  8 09:49:51 hopo kernel: [   14.572938] usbcore: registered new interface driver usbfs
Sep  8 09:49:51 hopo kernel: [   14.572957] usbcore: registered new interface driver hub
Sep  8 09:49:51 hopo kernel: [   14.573242] usbcore: registered new device driver usb
Sep  8 09:49:51 hopo kernel: [   14.574391] USB Universal Host Controller Interface driver v3.0
Sep  8 09:49:51 hopo kernel: [   14.574427] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:49:51 hopo kernel: [   14.574436] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Sep  8 09:49:51 hopo kernel: [   14.574439] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   14.574618] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Sep  8 09:49:51 hopo kernel: [   14.574643] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
Sep  8 09:49:51 hopo kernel: [   14.574750] usb usb1: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   14.574769] hub 1-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   14.574774] hub 1-0:1.0: 2 ports detected
Sep  8 09:49:51 hopo kernel: [   14.674899] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
Sep  8 09:49:51 hopo kernel: [   14.674910] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Sep  8 09:49:51 hopo kernel: [   14.674913] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   14.674938] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Sep  8 09:49:51 hopo kernel: [   14.674962] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
Sep  8 09:49:51 hopo kernel: [   14.675058] usb usb2: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   14.675078] hub 2-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   14.675083] hub 2-0:1.0: 2 ports detected
Sep  8 09:49:51 hopo kernel: [   14.678098] SCSI subsystem initialized
Sep  8 09:49:51 hopo kernel: [   14.687176] libata version 3.00 loaded.
Sep  8 09:49:51 hopo kernel: [   14.778844] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
Sep  8 09:49:51 hopo kernel: [   14.778856] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep  8 09:49:51 hopo kernel: [   14.778859] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   14.778880] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Sep  8 09:49:51 hopo kernel: [   14.778904] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
Sep  8 09:49:51 hopo kernel: [   14.779000] usb usb3: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   14.779019] hub 3-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   14.779023] hub 3-0:1.0: 2 ports detected
Sep  8 09:49:51 hopo kernel: [   14.882793] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
Sep  8 09:49:51 hopo kernel: [   14.882802] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep  8 09:49:51 hopo kernel: [   14.882806] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   14.882826] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Sep  8 09:49:51 hopo kernel: [   14.882848] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
Sep  8 09:49:51 hopo kernel: [   14.882950] usb usb4: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   14.882969] hub 4-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   14.882973] hub 4-0:1.0: 2 ports detected
Sep  8 09:49:51 hopo kernel: [   14.914705] usb 1-2: new full speed USB device using uhci_hcd and address 2
Sep  8 09:49:51 hopo kernel: [   14.986744] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Sep  8 09:49:51 hopo kernel: [   14.986755] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep  8 09:49:51 hopo kernel: [   14.986758] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   14.986778] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Sep  8 09:49:51 hopo kernel: [   14.986802] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
Sep  8 09:49:51 hopo kernel: [   14.986900] usb usb5: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   14.986919] hub 5-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   14.986923] hub 5-0:1.0: 2 ports detected
Sep  8 09:49:51 hopo kernel: [   15.085550] usb 1-2: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   15.090915] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
Sep  8 09:49:51 hopo kernel: [   15.090926] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Sep  8 09:49:51 hopo kernel: [   15.090929] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   15.090955] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Sep  8 09:49:51 hopo kernel: [   15.094855] ehci_hcd 0000:00:1a.7: debug port 1
Sep  8 09:49:51 hopo kernel: [   15.094860] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Sep  8 09:49:51 hopo kernel: [   15.094868] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xdfdfbc00
Sep  8 09:49:51 hopo kernel: [   15.099513] hub 1-2:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   15.102448] hub 1-2:1.0: config failed, can't read hub descriptor (err -22)
Sep  8 09:49:51 hopo kernel: [   15.110614] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  8 09:49:51 hopo kernel: [   15.110710] usb usb6: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   15.110730] hub 6-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   15.110735] hub 6-0:1.0: 4 ports detected
Sep  8 09:49:51 hopo kernel: [   15.214671] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
Sep  8 09:49:51 hopo kernel: [   15.214684] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep  8 09:49:51 hopo kernel: [   15.214688] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep  8 09:49:51 hopo kernel: [   15.214715] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Sep  8 09:49:51 hopo kernel: [   15.218612] ehci_hcd 0000:00:1d.7: debug port 1
Sep  8 09:49:51 hopo kernel: [   15.218616] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Sep  8 09:49:51 hopo kernel: [   15.218621] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xff980800
Sep  8 09:49:51 hopo kernel: [   15.230585] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  8 09:49:51 hopo kernel: [   15.230697] usb usb7: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   15.230723] hub 7-0:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   15.230728] hub 7-0:1.0: 6 ports detected
Sep  8 09:49:51 hopo kernel: [   15.334631] tg3.c:v3.86 (November 9, 2007)
Sep  8 09:49:51 hopo kernel: [   15.334651] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:49:51 hopo kernel: [   15.334659] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep  8 09:49:51 hopo kernel: [   15.355966] eth0: Tigon3 [partno(BCM95754) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:19:b9:48:ca:0d
Sep  8 09:49:51 hopo kernel: [   15.355972] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Sep  8 09:49:51 hopo kernel: [   15.355974] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Sep  8 09:49:51 hopo kernel: [   15.358973] ata_piix 0000:00:1f.2: version 2.12
Sep  8 09:49:51 hopo kernel: [   15.358978] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Sep  8 09:49:51 hopo kernel: [   15.514473] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
Sep  8 09:49:51 hopo kernel: [   15.514505] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep  8 09:49:51 hopo kernel: [   15.514561] scsi0 : ata_piix
Sep  8 09:49:51 hopo kernel: [   15.514715] scsi1 : ata_piix
Sep  8 09:49:51 hopo kernel: [   15.519446] ata1: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfec0 irq 21
Sep  8 09:49:51 hopo kernel: [   15.519448] ata2: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfec8 irq 21
Sep  8 09:49:51 hopo kernel: [   15.724093] ata1.00: ATA-7: ST3250820AS, 3.ADG, max UDMA/133
Sep  8 09:49:51 hopo kernel: [   15.724097] ata1.00: 488281250 sectors, multi 8: LBA48 NCQ (depth 0/32)
Sep  8 09:49:51 hopo kernel: [   15.782357] usb 1-2: USB disconnect, address 2
Sep  8 09:49:51 hopo kernel: [   15.790712] ata1.00: configured for UDMA/133
Sep  8 09:49:51 hopo kernel: [   16.022213] usb 1-2: new full speed USB device using uhci_hcd and address 3
Sep  8 09:49:51 hopo kernel: [   16.102265] ata2.01: NODEV after polling detection
Sep  8 09:49:51 hopo kernel: [   16.193079] usb 1-2: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   16.199009] hub 1-2:1.0: USB hub found
Sep  8 09:49:51 hopo kernel: [   16.199985] hub 1-2:1.0: 3 ports detected
Sep  8 09:49:51 hopo kernel: [   16.267312] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653A, D500, max UDMA/33
Sep  8 09:49:51 hopo kernel: [   16.267317] ata2.00: applying bridge limits
Sep  8 09:49:51 hopo kernel: [   16.438251] ata2.00: configured for UDMA/33
Sep  8 09:49:51 hopo kernel: [   16.438367] scsi 0:0:0:0: Direct-Access     ATA      ST3250820AS      3.AD PQ: 0 ANSI: 5
Sep  8 09:49:51 hopo kernel: [   16.439254] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D500 PQ: 0 ANSI: 5
Sep  8 09:49:51 hopo kernel: [   16.439324] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Sep  8 09:49:51 hopo kernel: [   16.545986] usb 4-1: new low speed USB device using uhci_hcd and address 2
Sep  8 09:49:51 hopo kernel: [   16.593981] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 21
Sep  8 09:49:51 hopo kernel: [   16.594012] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Sep  8 09:49:51 hopo kernel: [   16.594047] scsi2 : ata_piix
Sep  8 09:49:51 hopo kernel: [   16.594209] scsi3 : ata_piix
Sep  8 09:49:51 hopo kernel: [   16.594234] ata3: SATA max UDMA/133 cmd 0xfe40 ctl 0xfe50 bmdma 0xfed0 irq 21
Sep  8 09:49:51 hopo kernel: [   16.594237] ata4: SATA max UDMA/133 cmd 0xfe60 ctl 0xfe70 bmdma 0xfed8 irq 21
Sep  8 09:49:51 hopo kernel: [   16.719198] usb 4-1: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   16.923681] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
Sep  8 09:49:51 hopo kernel: [   17.059730] usb 1-2.1: configuration #1 chosen from 1 choice
Sep  8 09:49:51 hopo kernel: [   17.072628] usbcore: registered new interface driver hiddev
Sep  8 09:49:51 hopo kernel: [   17.085161] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input1
Sep  8 09:49:51 hopo kernel: [   17.105795] input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.1-1
Sep  8 09:49:51 hopo kernel: [   17.108841] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.1/1-2.1:1.0/input/input2
Sep  8 09:49:51 hopo kernel: [   17.121766] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.0-2.1
Sep  8 09:49:51 hopo kernel: [   17.126654] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.1/1-2.1:1.1/input/input3
Sep  8 09:49:51 hopo kernel: [   17.137757] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1a.0-2.1
Sep  8 09:49:51 hopo kernel: [   17.137771] usbcore: registered new interface driver usbhid
Sep  8 09:49:51 hopo kernel: [   17.137774] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Sep  8 09:49:51 hopo kernel: [   18.256223] Driver 'sd' needs updating - please use bus_type methods
Sep  8 09:49:51 hopo kernel: [   18.256287] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Sep  8 09:49:51 hopo kernel: [   18.256298] sd 0:0:0:0: [sda] Write Protect is off
Sep  8 09:49:51 hopo kernel: [   18.256300] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  8 09:49:51 hopo kernel: [   18.256314] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  8 09:49:51 hopo kernel: [   18.256354] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Sep  8 09:49:51 hopo kernel: [   18.256362] sd 0:0:0:0: [sda] Write Protect is off
Sep  8 09:49:51 hopo kernel: [   18.256364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  8 09:49:51 hopo kernel: [   18.256377] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  8 09:49:51 hopo kernel: [   18.256380]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep  8 09:49:51 hopo kernel: [   18.269916]  sda1 sda2 sda3 sda4
Sep  8 09:49:51 hopo kernel: [   18.290752] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  8 09:49:51 hopo kernel: [   18.294234] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  8 09:49:51 hopo kernel: [   18.294251] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  8 09:49:51 hopo kernel: [   18.299724] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Sep  8 09:49:51 hopo kernel: [   18.299727] Uniform CD-ROM driver Revision: 3.20
Sep  8 09:49:51 hopo kernel: [   18.299766] sr 1:0:0:0: Attached scsi CD-ROM sr0
Sep  8 09:49:51 hopo kernel: [   18.696338] Attempting manual resume
Sep  8 09:49:51 hopo kernel: [   18.696341] swsusp: Resume From Partition 8:4
Sep  8 09:49:51 hopo kernel: [   18.696342] PM: Checking swsusp image.
Sep  8 09:49:51 hopo kernel: [   18.696617] PM: Resume from disk failed.
Sep  8 09:49:51 hopo kernel: [   18.718747] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  8 09:49:51 hopo kernel: [   18.718750] EXT3-fs: write access will be enabled during recovery.
Sep  8 09:49:51 hopo kernel: [   19.054427] kjournald starting.  Commit interval 5 seconds
Sep  8 09:49:51 hopo kernel: [   19.054435] EXT3-fs: sda3: orphan cleanup on readonly fs
Sep  8 09:49:51 hopo kernel: [   19.054440] ext3_orphan_cleanup: deleting unreferenced inode 2548525
Sep  8 09:49:51 hopo kernel: [   19.054463] EXT3-fs: sda3: 1 orphan inode deleted
Sep  8 09:49:51 hopo kernel: [   19.054465] EXT3-fs: recovery complete.
Sep  8 09:49:51 hopo kernel: [   19.058648] EXT3-fs: mounted filesystem with ordered data mode.
Sep  8 09:49:51 hopo kernel: [   29.413996] input: PC Speaker as /devices/platform/pcspkr/input/input4
Sep  8 09:49:51 hopo kernel: [   29.532996] parport_pc 00:06: reported by Plug and Play ACPI
Sep  8 09:49:51 hopo kernel: [   29.533050] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Sep  8 09:49:51 hopo kernel: [   29.593170] Linux agpgart interface v0.102
Sep  8 09:49:51 hopo kernel: [   29.709095] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  8 09:49:51 hopo kernel: [   29.739823] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  8 09:49:51 hopo kernel: [   29.837135] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep  8 09:49:51 hopo kernel: [   29.873161] iTCO_vendor_support: vendor-support=0
Sep  8 09:49:51 hopo kernel: [   29.897022] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep  8 09:49:51 hopo kernel: [   29.897096] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
Sep  8 09:49:51 hopo kernel: [   29.897105] iTCO_wdt: No card detected
Sep  8 09:49:51 hopo kernel: [   29.927591] input: Power Button (FF) as /devices/virtual/input/input5
Sep  8 09:49:51 hopo kernel: [   30.020937] ACPI: Power Button (FF) [PWRF]
Sep  8 09:49:51 hopo kernel: [   30.020988] input: Power Button (CM) as /devices/virtual/input/input6
Sep  8 09:49:51 hopo kernel: [   30.084931] ACPI: Power Button (CM) [VBTN]
Sep  8 09:49:51 hopo kernel: [   30.209184] agpgart: Detected an Intel 965Q Chipset.
Sep  8 09:49:51 hopo kernel: [   30.210018] agpgart: Detected 7676K stolen memory.
Sep  8 09:49:51 hopo kernel: [   30.250215] agpgart: AGP aperture is 256M @ 0xc0000000
Sep  8 09:49:51 hopo kernel: [   30.635793] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:49:51 hopo kernel: [   30.635810] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep  8 09:49:51 hopo kernel: [   31.023190] lp0: using parport0 (interrupt-driven).
Sep  8 09:49:51 hopo kernel: [   31.059042] Adding 2000084k swap on /dev/sda4.  Priority:-1 extents:1 across:2000084k
Sep  8 09:49:51 hopo kernel: [   31.597821] EXT3 FS on sda3, internal journal
Sep  8 09:49:51 hopo kernel: [   32.574699] kjournald starting.  Commit interval 5 seconds
Sep  8 09:49:51 hopo kernel: [   32.574891] EXT3 FS on sda2, internal journal
Sep  8 09:49:51 hopo kernel: [   32.574895] EXT3-fs: mounted filesystem with ordered data mode.
Sep  8 09:49:51 hopo kernel: [   33.233739] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep  8 09:49:51 hopo kernel: [   34.966593] No dock devices found.
Sep  8 09:49:51 hopo kernel: [   34.967528] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1: found ejectable bay
Sep  8 09:49:51 hopo kernel: [   34.967532] ACPI: \_SB_.PCI0.IDE1.PRI1.MAS1: Adding notify handler
Sep  8 09:49:51 hopo kernel: [   34.967559] ACPI: Error installing bay notify handler
Sep  8 09:49:51 hopo kernel: [   34.967561] ACPI: Bay [\_SB_.PCI0.IDE1.PRI1.MAS1] Added
Sep  8 09:49:51 hopo NetworkManager: <info>  starting... 
Sep  8 09:49:51 hopo avahi-daemon[5039]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep  8 09:49:51 hopo avahi-daemon[5039]: Successfully dropped root privileges.
Sep  8 09:49:51 hopo avahi-daemon[5039]: avahi-daemon 0.6.22 starting up.
Sep  8 09:49:51 hopo avahi-daemon[5039]: Successfully called chroot().
Sep  8 09:49:51 hopo avahi-daemon[5039]: Successfully dropped remaining capabilities.
Sep  8 09:49:51 hopo avahi-daemon[5039]: No service file found in /etc/avahi/services.
Sep  8 09:49:51 hopo avahi-daemon[5039]: Network interface enumeration completed.
Sep  8 09:49:51 hopo avahi-daemon[5039]: Registering HINFO record with values 'I686'/'LINUX'.
Sep  8 09:49:51 hopo avahi-daemon[5039]: Server startup complete. Host name is hopo.local. Local service cookie is 2286957461.
Sep  8 09:49:51 hopo kernel: [   35.907272] ppdev: user-space parallel port driver
Sep  8 09:49:52 hopo kernel: [   36.187416] audit(1252421392.245:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5093 profile="/usr/sbin/cupsd" namespace="default"
Sep  8 09:49:52 hopo kernel: [   36.187502] audit(1252421392.245:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=5093 profile="/usr/sbin/cupsd" namespace="default"
Sep  8 09:49:52 hopo slapd[5103]: @(#) $OpenLDAP: slapd 2.4.9 (Mar 31 2009 07:12:16) $ ^Ibuildd@rothera:/build/buildd/openldap2.3-2.4.9/debian/build/servers/slapd 
Sep  8 09:49:52 hopo slapd[5103]: daemon: IPv6 socket() failed errno=97 (Address family not supported by protocol) 
Sep  8 09:49:52 hopo slapd[5108]: hdb_db_open: database "dc=hopo,dc=local": unclean shutdown detected; attempting recovery. 
Sep  8 09:49:52 hopo slapd[5108]: slapd starting 
Sep  8 09:49:52 hopo kernel: [   36.922020] /dev/vmmon[5119]: Module vmmon: registered with major=10 minor=165
Sep  8 09:49:52 hopo kernel: [   36.922031] /dev/vmmon[5119]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Sep  8 09:49:52 hopo kernel: [   36.922035] /dev/vmmon[5119]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Sep  8 09:49:52 hopo kernel: [   36.922037] /dev/vmmon[5119]: Module vmmon: initialized
Sep  8 09:49:53 hopo kernel: [   36.971168] /dev/vmci[5131]: VMCI: Driver initialized.
Sep  8 09:49:53 hopo kernel: [   36.971199] /dev/vmci[5131]: Module vmci: registered with major=10 minor=63
Sep  8 09:49:53 hopo kernel: [   36.971201] /dev/vmci[5131]: Module vmci: initialized
Sep  8 09:49:53 hopo vmnetBridge: Daemon created. 
Sep  8 09:49:53 hopo vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001002 
Sep  8 09:49:53 hopo vmnetBridge: Can't remove interface eth0 2 (does not exist). 
Sep  8 09:50:01 hopo vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Sep  8 09:50:01 hopo vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Sep  8 09:50:01 hopo vmnet-dhcpd: All rights reserved.
Sep  8 09:50:01 hopo vmnet-dhcpd: 
Sep  8 09:50:01 hopo vmnet-dhcpd: Please contribute if you find this software useful.
Sep  8 09:50:01 hopo vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Sep  8 09:50:01 hopo vmnet-dhcpd: 
Sep  8 09:50:01 hopo vmnet-dhcpd: Configured subnet: 192.168.72.0
Sep  8 09:50:01 hopo vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.72.254
Sep  8 09:50:01 hopo vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.72.0
Sep  8 09:50:01 hopo vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.72.0
Sep  8 09:50:01 hopo kernel: [   45.418762] /dev/vmnet: open called by PID 5691 (vmnet-dhcpd)
Sep  8 09:50:01 hopo kernel: [   45.418770] /dev/vmnet: hub 1 does not exist, allocating memory.
Sep  8 09:50:01 hopo kernel: [   45.418778] /dev/vmnet: port on hub 1 successfully opened
Sep  8 09:50:01 hopo kernel: [   45.473403] /dev/vmnet: open called by PID 5695 (vmnet-netifup)
Sep  8 09:50:01 hopo kernel: [   45.473414] /dev/vmnet: port on hub 1 successfully opened
Sep  8 09:50:01 hopo avahi-daemon[5039]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.72.1.
Sep  8 09:50:01 hopo avahi-daemon[5039]: New relevant interface vmnet1.IPv4 for mDNS.
Sep  8 09:50:01 hopo avahi-daemon[5039]: Registering new address record for 192.168.72.1 on vmnet1.IPv4.
Sep  8 09:50:01 hopo vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Sep  8 09:50:01 hopo vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Sep  8 09:50:01 hopo vmnet-dhcpd: All rights reserved.
Sep  8 09:50:01 hopo vmnet-dhcpd: 
Sep  8 09:50:01 hopo vmnet-dhcpd: Please contribute if you find this software useful.
Sep  8 09:50:01 hopo vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Sep  8 09:50:01 hopo vmnet-dhcpd: 
Sep  8 09:50:01 hopo vmnet-dhcpd: Configured subnet: 192.168.71.0
Sep  8 09:50:01 hopo vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.71.254
Sep  8 09:50:01 hopo vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.71.0
Sep  8 09:50:01 hopo vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.71.0
Sep  8 09:50:01 hopo kernel: [   45.506808] /dev/vmnet: open called by PID 5698 (vmnet-dhcpd)
Sep  8 09:50:01 hopo kernel: [   45.506816] /dev/vmnet: hub 8 does not exist, allocating memory.
Sep  8 09:50:01 hopo kernel: [   45.506826] /dev/vmnet: port on hub 8 successfully opened
Sep  8 09:50:01 hopo kernel: [   45.571307] /dev/vmnet: open called by PID 5700 (vmnet-natd)
Sep  8 09:50:01 hopo kernel: [   45.571317] /dev/vmnet: port on hub 8 successfully opened
Sep  8 09:50:01 hopo kernel: [   45.620216] /dev/vmnet: open called by PID 5704 (vmnet-netifup)
Sep  8 09:50:01 hopo kernel: [   45.620227] /dev/vmnet: port on hub 8 successfully opened
Sep  8 09:50:01 hopo avahi-daemon[5039]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.71.1.
Sep  8 09:50:01 hopo avahi-daemon[5039]: New relevant interface vmnet8.IPv4 for mDNS.
Sep  8 09:50:01 hopo avahi-daemon[5039]: Registering new address record for 192.168.71.1 on vmnet8.IPv4.
Sep  8 09:50:01 hopo vmnet-detect[5708]: NetDetectDaemonInit: No host policy file found. Not initializing filter. 
Sep  8 09:50:01 hopo vmnet-detect[5708]: Unable to initialize the daemon 
Sep  8 09:50:01 hopo kernel: [   45.922646] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Sep  8 09:50:01 hopo kernel: [   45.922650] apm: disabled - APM is not SMP safe.
Sep  8 09:50:02 hopo kernel: [   46.078551] RPC: Registered udp transport module.
Sep  8 09:50:02 hopo kernel: [   46.078554] RPC: Registered tcp transport module.
Sep  8 09:50:02 hopo kernel: [   46.155812] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Sep  8 09:50:02 hopo kernel: [   46.212112] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep  8 09:50:02 hopo kernel: [   46.225465] NFSD: starting 90-second grace period
Sep  8 09:50:02 hopo dhcdbd: Started up.
Sep  8 09:50:03 hopo vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001043 
Sep  8 09:50:03 hopo kernel: [   47.713267] /dev/vmnet: open called by PID 5174 (vmnet-bridge)
Sep  8 09:50:03 hopo kernel: [   47.713275] /dev/vmnet: hub 0 does not exist, allocating memory.
Sep  8 09:50:03 hopo kernel: [   47.713283] /dev/vmnet: port on hub 0 successfully opened
Sep  8 09:50:03 hopo kernel: [   47.713294] bridge-eth0: up
Sep  8 09:50:03 hopo hcid[6071]: Bluetooth HCI daemon
Sep  8 09:50:03 hopo vmnetBridge: Started bridge eth0 to virtual network 0. 
Sep  8 09:50:03 hopo vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001003 
Sep  8 09:50:03 hopo kernel: [   47.749412] bridge-eth0: attached
Sep  8 09:50:03 hopo kernel: [   47.749468] bridge-eth0: disabling the bridge
Sep  8 09:50:03 hopo NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Sep  8 09:50:03 hopo NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep  8 09:50:03 hopo NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep  8 09:50:03 hopo NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Sep  8 09:50:03 hopo NetworkManager: <info>  Deactivating device eth0. 
Sep  8 09:50:03 hopo NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep  8 09:50:03 hopo NetworkManager: <debug> [1252421403.845559] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_H653A'). 
Sep  8 09:50:03 hopo vmnetBridge: Stopped bridge eth0 to virtual network 0. 
Sep  8 09:50:03 hopo kernel: [   47.788912] bridge-eth0: down
Sep  8 09:50:03 hopo kernel: [   47.788919] bridge-eth0: detached
Sep  8 09:50:03 hopo kernel: [   47.821008] Bluetooth: Core ver 2.11
Sep  8 09:50:03 hopo kernel: [   47.821079] NET: Registered protocol family 31
Sep  8 09:50:03 hopo kernel: [   47.821081] Bluetooth: HCI device and connection manager initialized
Sep  8 09:50:03 hopo kernel: [   47.821085] Bluetooth: HCI socket layer initialized
Sep  8 09:50:03 hopo hcid[6071]: Starting SDP server
Sep  8 09:50:03 hopo kernel: [   47.846627] Bluetooth: L2CAP ver 2.9
Sep  8 09:50:03 hopo kernel: [   47.846631] Bluetooth: L2CAP socket layer initialized
Sep  8 09:50:03 hopo hcid[6071]: Created local server at unix:abstract=/var/run/dbus-wBI5fq2TtJ,guid=3964bf1c3acbfce69721eb8c4aa66f1b
Sep  8 09:50:03 hopo NetworkManager: <debug> [1252421403.921728] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep  8 09:50:03 hopo audio[6109]: Bluetooth Audio daemon
Sep  8 09:50:03 hopo audio[6109]: Unix socket created: 5
Sep  8 09:50:03 hopo audio[6109]: audio.conf: Key file does not have key 'Enable'
Sep  8 09:50:03 hopo audio[6109]: audio.conf: Key file does not have key 'Disable'
Sep  8 09:50:03 hopo input[6112]: Bluetooth Input daemon
Sep  8 09:50:03 hopo input[6112]: Registered input manager path:/org/bluez/input
Sep  8 09:50:03 hopo kernel: [   47.916691] Bluetooth: RFCOMM socket layer initialized
Sep  8 09:50:03 hopo kernel: [   47.916700] Bluetooth: RFCOMM TTY layer initialized
Sep  8 09:50:03 hopo kernel: [   47.916702] Bluetooth: RFCOMM ver 1.8
Sep  8 09:50:03 hopo audio[6109]: add_service_record: got record id 0x10000
Sep  8 09:50:03 hopo audio[6109]: audio.conf: Key file does not have key 'Disable'
Sep  8 09:50:03 hopo audio[6109]: audio.conf: Key file does not have group 'A2DP'
Sep  8 09:50:03 hopo last message repeated 3 times
Sep  8 09:50:03 hopo audio[6109]: SEP 0x806d118 registered: type:0 codec:0 seid:1
Sep  8 09:50:03 hopo audio[6109]: add_service_record: got record id 0x10001
Sep  8 09:50:03 hopo audio[6109]: add_service_record: got record id 0x10002
Sep  8 09:50:03 hopo audio[6109]: add_service_record: got record id 0x10003
Sep  8 09:50:03 hopo audio[6109]: Registered manager path:/org/bluez/audio
Sep  8 09:50:06 hopo kernel: [   50.424336] [drm] Initialized drm 1.1.0 20060810
Sep  8 09:50:06 hopo kernel: [   50.447568] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  8 09:50:06 hopo kernel: [   50.447577] PCI: Setting latency timer of device 0000:00:02.0 to 64
Sep  8 09:50:06 hopo kernel: [   50.447623] [drm] Initialized i915 1.6.0 20060119 on minor 0
Sep  8 09:50:06 hopo NetworkManager: <debug> [1252421406.521569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2992_drm_i915_card0'). 
Sep  8 09:50:06 hopo kernel: [   50.461922] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Sep  8 09:50:07 hopo kernel: [   51.056056] tg3: eth0: Link is up at 100 Mbps, full duplex.
Sep  8 09:50:07 hopo kernel: [   51.056061] tg3: eth0: Flow control is off for TX and off for RX.
Sep  8 09:50:07 hopo vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00011043 
Sep  8 09:50:07 hopo vmnetBridge: Started bridge eth0 to virtual network 0. 
Sep  8 09:50:07 hopo NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep  8 09:50:07 hopo NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep  8 09:50:07 hopo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep  8 09:50:07 hopo kernel: [   51.057739] /dev/vmnet: open called by PID 5174 (vmnet-bridge)
Sep  8 09:50:07 hopo kernel: [   51.057747] /dev/vmnet: hub 0 does not exist, allocating memory.
Sep  8 09:50:07 hopo kernel: [   51.057755] /dev/vmnet: port on hub 0 successfully opened
Sep  8 09:50:07 hopo kernel: [   51.057763] bridge-eth0: up
Sep  8 09:50:07 hopo kernel: [   51.057766] bridge-eth0: attached

```

---

### Post by GregIthaca on 2009-10-22
I was trying to post this in another thread that seemed more appropriate, but it seems to be locked.  New to forum, so don't know the etiquette around this...

I am trying to bring up a *very old* (11 years) server (Dell PowerEdge 2200) with a modern Linux.  Worked okay with RedHat 6.x (not sure which version) but that didn't have support for a lot of things I need today.  Was unable to get Fedora11 to install at all -- tried about 10 times with different sorts of crashes and hangs.

Xubuntu 8.04 Hardy *installed* very nicely.  But that's about as far as I get.

1. Any time X gets started (normal boot, startx, gdm) it just goes to a blank screen.  Reading the logs it detected an ATI 264VT (Mach64 VT) rev 64, with 1MB video memory (it's on the motherboard).  I'm kind of guessing here, but I think it's not finding enough memory for any of its video modes.  I can't figure out the commands needed to force it into 8bpp, which would certainly help; the quote-unquote config file it points to (/etc/X11/xorg.conf) is a joke -- there are no *settings* in it, and I have no idea where the actual settings have been moved to.

2. The virtual consoles don't work -- blinking cursor in the upper left corner, which doesn't respond to anything. None of the usual explanations (vga=xxx boot argument, NVidia card, Intel card) seem to explain it.  It may be worth noting that they don't work but I get a change of scenery when I drop back to a root prompt without the X server running; with the X server running the screen just stays black no matter what I do.

3. Can't exit the X server with Ctrl-Alt-Backspace either.  There's nothing in the log to suggest it crashed or failed... the last line is just 'I2C bus "Mach64" initialized.'

Getting to the point where I've spent so much time on this I should have just bought a new machine, but it feels like I'm *so* close right now...

Any suggestions?

---

