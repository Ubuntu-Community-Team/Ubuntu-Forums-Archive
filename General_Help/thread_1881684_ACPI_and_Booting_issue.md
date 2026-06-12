---
title: "ACPI and Booting issue"
date: 2011-11-16
forum: General Help
---

### Post by WinterMadness on 2011-11-16
Hello, in order to boot my computer acpi has to be set to nothing or off however when its set to nothing, it only boots sometimes.

Off turns my fan off and I cant tell the state of the battery.

How can I fix this?

my computer is the asus u46

---

### Post by WinterMadness on 2011-11-16
anyone?

---

### Post by Cyclane on 2011-11-16
Well I don't think I can help you because I'm no expert on ACPI. BUT I in order to help you the community will need some information. Like what computer do you use, maybe the output of 'lspci'.

---

### Post by WinterMadness on 2011-11-16
> **WinterMadness said:**
> my computer is the asus u46

```
joe@joe-U46:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

```

im using intel core i7
64bit, oneric

---

### Post by WinterMadness on 2011-11-16
shameless bump

---

### Post by WinterMadness on 2011-11-16
still need help on this issue. i just want it to boot consistently when acpi is set to nothing.

---

### Post by WinterMadness on 2011-11-16
few more bumps left in me

---

### Post by WinterMadness on 2011-11-17
last bump

---

### Post by matt_symes on 2011-11-17
Hi 

I suppose the first question should be - is your BIOS up to date ? 

ACPI issues are generally caused when the ACPI code in  the BIOS is not doing what the OS expects.

You need to boot into Ubuntu *without* the acpi=off command and post back the contents of

```
dmesg > log.txt
```

That may yield some clues.

Kind regards

---

### Post by WinterMadness on 2011-11-18
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=045c2fcc-6261-4e76-9597-7e7b94ddbc4a ro quiet splash acpi= vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000babcd000 (usable)
[    0.000000]  BIOS-e820: 00000000babcd000 - 00000000bacf4000 (reserved)
[    0.000000]  BIOS-e820: 00000000bacf4000 - 00000000bacf6000 (usable)
[    0.000000]  BIOS-e820: 00000000bacf6000 - 00000000bade8000 (reserved)
[    0.000000]  BIOS-e820: 00000000bade8000 - 00000000baf29000 (usable)
[    0.000000]  BIOS-e820: 00000000baf29000 - 00000000bafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bafe8000 - 00000000baffd000 (usable)
[    0.000000]  BIOS-e820: 00000000baffd000 - 00000000bb000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bb000000 - 00000000bfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff980000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000023fe00000 (usable)
[    0.000000] Malformed early option 'acpi'
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: ASUSTeK Computer Inc. U46E/U46E, BIOS U46E.205 07/20/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x23fe00 max_arch_pfn = 0x400000000
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
[    0.000000]   2 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   3 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   4 base 100000000 mask F00000000 write-back
[    0.000000]   5 base 200000000 mask FC0000000 write-back
[    0.000000]   6 base 23FE00000 mask FFFE00000 uncachable
[    0.000000]   7 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbaffd max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcc20] fcc20
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000baffd000
[    0.000000]  0000000000 - 00bae00000 page 2M
[    0.000000]  00bae00000 - 00baffd000 page 4k
[    0.000000] kernel direct mapping tables up to baffd000 @ baff8000-baffd000
[    0.000000] init_memory_mapping: 0000000100000000-000000023fe00000
[    0.000000]  0100000000 - 023fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 23fe00000 @ 23fdf6000-23fe00000
[    0.000000] RAMDISK: 359ec000 - 36cee000
[    0.000000] ACPI: RSDP 00000000000f0430 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000baffee18 0007C (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000baf9bd98 000F4 (v04 _ASUS_ NoteBook 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xBAFE5E40/0x00000000BAFE5D40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000baf7c018 0DBD1 (v01 _ASUS_ NoteBook 00000000 INTL 20091112)
[    0.000000] ACPI: FACS 00000000bafe5e40 00040
[    0.000000] ACPI: APIC 00000000baffdf18 000CC (v02 _ASUS_ NoteBook 06222004 MSFT 00010013)
[    0.000000] ACPI: HPET 00000000bafe6d18 00038 (v01 _ASUS_ NoteBook 06222004 AMI. 00000003)
[    0.000000] ACPI: ECDT 00000000bafe5b18 000C1 (v01 _ASUS_ NoteBook 06222004 AMI  00000000)
[    0.000000] ACPI: MCFG 00000000bafe6c98 0003C (v01 _ASUS_ NoteBook 06222004 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000baf7b018 0081D (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000baf7a018 00996 (v01  PmRef    CpuPm 00003000 INTL 20091112)
[    0.000000] ACPI: SLIC 00000000baf9cc18 00176 (v01 _ASUS_ Notebook 06222004 ASUS 00000001)
[    0.000000] ACPI: DMAR 00000000baf9bc18 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 00000000baf6ea98 002EF (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: ASF! 00000000bafe5a18 000A0 (v32 INTEL   HCG568D 00000001 MSFT 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000023fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000023fe00000
[    0.000000]   NODE_DATA [000000023fdfb000 - 000000023fdfffff]
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880237400000-ffff88023e3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0023fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000babcd
[    0.000000]     0: 0x000bacf4 -> 0x000bacf6
[    0.000000]     0: 0x000bade8 -> 0x000baf29
[    0.000000]     0: 0x000bafe8 -> 0x000baffd
[    0.000000]     0: 0x00100000 -> 0x0023fe00
[    0.000000] On node 0 totalpages: 2074291
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 745821 pages, LIFO batch:31
[    0.000000]   Normal zone: 17913 pages used for memmap
[    0.000000]   Normal zone: 1292295 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000babcd000 - 00000000bacf4000
[    0.000000] PM: Registered nosave memory: 00000000bacf6000 - 00000000bade8000
[    0.000000] PM: Registered nosave memory: 00000000baf29000 - 00000000bafe8000
[    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
[    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff980000
[    0.000000] PM: Registered nosave memory: 00000000ff980000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:20600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88023fa00000 s79616 r8192 d22784 u131072
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2042037
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=045c2fcc-6261-4e76-9597-7e7b94ddbc4a ro quiet splash acpi= vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.000000] Memory: 8081640k/9435136k available (6104k kernel code, 1137972k absent, 215524k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:808 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2693.684 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.36 BogoMIPS (lpj=10774736)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000038] AppArmor: AppArmor initialized
[    0.000039] Yama: becoming mindful.
[    0.000705] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002260] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002889] Mount-cache hash table entries: 256
[    0.002980] Initializing cgroup subsys cpuacct
[    0.002984] Initializing cgroup subsys memory
[    0.002990] Initializing cgroup subsys devices
[    0.002991] Initializing cgroup subsys freezer
[    0.002993] Initializing cgroup subsys net_cls
[    0.002994] Initializing cgroup subsys blkio
[    0.002998] Initializing cgroup subsys perf_event
[    0.003021] CPU: Physical Processor ID: 0
[    0.003022] CPU: Processor Core ID: 0
[    0.003026] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003027] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003029] mce: CPU supports 7 MCE banks
[    0.003039] CPU0: Thermal monitoring enabled (TM1)
[    0.003045] using mwait in idle threads.
[    0.005273] ACPI: Core revision 20110413
[    0.157419] ftrace: allocating 25651 entries in 101 pages
[    0.165896] DMAR: Host address width 36
[    0.165899] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.165904] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.165906] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.165911] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.165912] DMAR: RMRR base: 0x000000badce000 end: 0x000000bade4fff
[    0.165913] DMAR: RMRR base: 0x000000bb800000 end: 0x000000bf9fffff
[    0.165915] DMAR: No ATSR found
[    0.165984] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.165985] HPET id 0 under DRHD base 0xfed91000
[    0.165986] HPET id 0 under DRHD base 0xfed91000
[    0.165987] HPET id 0 under DRHD base 0xfed91000
[    0.165988] HPET id 0 under DRHD base 0xfed91000
[    0.165989] HPET id 0 under DRHD base 0xfed91000
[    0.165990] HPET id 0 under DRHD base 0xfed91000
[    0.165991] HPET id 0 under DRHD base 0xfed91000
[    0.165992] HPET id 0 under DRHD base 0xfed91000
[    0.166156] Enabled IRQ remapping in x2apic mode
[    0.166157] Enabling x2apic
[    0.166158] Enabled x2apic
[    0.166163] Switched APIC routing to cluster x2apic.
[    0.166534] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.206202] CPU0: Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz stepping 07
[    0.312283] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.312289] ... version:                3
[    0.312290] ... bit width:              48
[    0.312291] ... generic registers:      4
[    0.312292] ... value mask:             0000ffffffffffff
[    0.312293] ... max period:             000000007fffffff
[    0.312294] ... fixed-purpose events:   3
[    0.312295] ... event mask:             000000070000000f
[    0.312622] Booting Node   0, Processors  #1
[    0.312624] smpboot cpu 1: start_ip = 99000
[    0.420370]  #2
[    0.420372] smpboot cpu 2: start_ip = 99000
[    0.528390]  #3
[    0.528392] smpboot cpu 3: start_ip = 99000
[    0.636294] Brought up 4 CPUs
[    0.636297] Total of 4 processors activated (21550.56 BogoMIPS).
[    0.638903] devtmpfs: initialized
[    0.639008] PM: Registering ACPI NVS region at baf29000 (782336 bytes)
[    0.640101] print_constraints: dummy: 
[    0.640126] Time: 17:03:07  Date: 11/17/11
[    0.640153] NET: Registered protocol family 16
[    0.640232] Trying to unpack rootfs image as initramfs...
[    0.640244] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.640246] ACPI: bus type pci registered
[    0.640299] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.640302] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.653108] PCI: Using configuration type 1 for base access
[    0.653661] bio: create slab <bio-0> at 0
[    0.655284] ACPI: EC: EC description table is found, configuring boot EC
[    0.655289] ACPI: EC: Look up EC in DSDT
[    0.656932] ACPI: Executed 1 blocks of module-level executable AML code
[    0.692207] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.692585] ACPI: SSDT 00000000badbc718 00694 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.692982] ACPI: Dynamic OEM Table Load:
[    0.692984] ACPI: SSDT           (null) 00694 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.712369] ACPI: SSDT 00000000badbda98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.712793] ACPI: Dynamic OEM Table Load:
[    0.712795] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.740248] ACPI: SSDT 00000000badbbd98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.740645] ACPI: Dynamic OEM Table Load:
[    0.740647] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.796274] ACPI: Interpreter enabled
[    0.796278] ACPI: (supports S0 S1 S3 S4 S5)
[    0.796299] ACPI: Using IOAPIC for interrupt routing
[    0.801104] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.801272] ACPI: No dock devices found.
[    0.801273] HEST: Table not found.
[    0.801275] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.801453] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.801790] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.801792] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.801794] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.801796] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.801798] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.801799] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.801801] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.801803] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.801804] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.801806] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xfeafffff]
[    0.801808] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.801818] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.801849] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    0.801858] pci 0000:00:02.0: reg 10: [mem 0xdd000000-0xdd3fffff 64bit]
[    0.801864] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.801868] pci 0000:00:02.0: reg 20: [io  0xe000-0xe03f]
[    0.801914] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.801936] pci 0000:00:16.0: reg 10: [mem 0xdfc0b000-0xdfc0b00f 64bit]
[    0.801997] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.802001] pci 0000:00:16.0: PME# disabled
[    0.802031] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.802051] pci 0000:00:1a.0: reg 10: [mem 0xdfc08000-0xdfc083ff]
[    0.802122] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.802126] pci 0000:00:1a.0: PME# disabled
[    0.802148] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.802163] pci 0000:00:1b.0: reg 10: [mem 0xdfc00000-0xdfc03fff 64bit]
[    0.802216] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.802220] pci 0000:00:1b.0: PME# disabled
[    0.802240] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.802300] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.802304] pci 0000:00:1c.0: PME# disabled
[    0.802325] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.802385] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.802388] pci 0000:00:1c.1: PME# disabled
[    0.802411] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    0.802471] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.802475] pci 0000:00:1c.3: PME# disabled
[    0.802497] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    0.802557] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.802561] pci 0000:00:1c.5: PME# disabled
[    0.802590] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.802611] pci 0000:00:1d.0: reg 10: [mem 0xdfc07000-0xdfc073ff]
[    0.802681] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.802685] pci 0000:00:1d.0: PME# disabled
[    0.802708] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    0.802968] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.802985] pci 0000:00:1f.2: reg 10: [io  0xe0b0-0xe0b7]
[    0.802993] pci 0000:00:1f.2: reg 14: [io  0xe0a0-0xe0a3]
[    0.803001] pci 0000:00:1f.2: reg 18: [io  0xe090-0xe097]
[    0.803009] pci 0000:00:1f.2: reg 1c: [io  0xe080-0xe083]
[    0.803017] pci 0000:00:1f.2: reg 20: [io  0xe060-0xe07f]
[    0.803025] pci 0000:00:1f.2: reg 24: [mem 0xdfc06000-0xdfc067ff]
[    0.803056] pci 0000:00:1f.2: PME# supported from D3hot
[    0.803060] pci 0000:00:1f.2: PME# disabled
[    0.803077] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.803092] pci 0000:00:1f.3: reg 10: [mem 0xdfc05000-0xdfc050ff 64bit]
[    0.803113] pci 0000:00:1f.3: reg 20: [io  0xe040-0xe05f]
[    0.803180] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.803184] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.803188] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdfbfffff]
[    0.803194] pci 0000:00:1c.0:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.803272] pci 0000:02:00.0: [8086:0885] type 0 class 0x000280
[    0.803316] pci 0000:02:00.0: reg 10: [mem 0xde800000-0xde801fff 64bit]
[    0.803487] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.803494] pci 0000:02:00.0: PME# disabled
[    0.803555] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.803559] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.803563] pci 0000:00:1c.1:   bridge window [mem 0xde800000-0xdf1fffff]
[    0.803569] pci 0000:00:1c.1:   bridge window [mem 0xd1600000-0xd1ffffff 64bit pref]
[    0.803635] pci 0000:03:00.0: [1b73:1000] type 0 class 0x000c03
[    0.803659] pci 0000:03:00.0: reg 10: [mem 0xdde00000-0xdde0ffff]
[    0.803803] pci 0000:03:00.0: PME# supported from D0 D3hot
[    0.803808] pci 0000:03:00.0: PME# disabled
[    0.803842] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.803846] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
[    0.803850] pci 0000:00:1c.3:   bridge window [mem 0xdde00000-0xde7fffff]
[    0.803856] pci 0000:00:1c.3:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.803920] pci 0000:04:00.0: [1969:1083] type 0 class 0x000200
[    0.803948] pci 0000:04:00.0: reg 10: [mem 0xdd400000-0xdd43ffff 64bit]
[    0.803963] pci 0000:04:00.0: reg 18: [io  0xa000-0xa07f]
[    0.804058] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.804063] pci 0000:04:00.0: PME# disabled
[    0.804101] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.804105] pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
[    0.804109] pci 0000:00:1c.5:   bridge window [mem 0xdd400000-0xdddfffff]
[    0.804115] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.804140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.804256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.804283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.804313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.804341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.804382]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.804384]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.804386] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.807787] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.807825] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 10 11 12 14 15)
[    0.807861] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.807896] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.807931] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.807966] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.808001] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 10 11 12 14 15)
[    0.808036] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 *4 5 6 10 11 12 14 15)
[    0.808101] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.808106] vgaarb: loaded
[    0.808107] vgaarb: bridge control possible 0000:00:02.0
[    0.808229] SCSI subsystem initialized
[    0.808280] libata version 3.00 loaded.
[    0.808311] usbcore: registered new interface driver usbfs
[    0.808317] usbcore: registered new interface driver hub
[    0.808339] usbcore: registered new device driver usb
[    0.808398] PCI: Using ACPI for IRQ routing
[    0.809882] PCI: pci_cache_line_size set to 64 bytes
[    0.809957] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.809959] reserve RAM buffer: 00000000babcd000 - 00000000bbffffff 
[    0.809961] reserve RAM buffer: 00000000bacf6000 - 00000000bbffffff 
[    0.809963] reserve RAM buffer: 00000000baf29000 - 00000000bbffffff 
[    0.809965] reserve RAM buffer: 00000000baffd000 - 00000000bbffffff 
[    0.809967] reserve RAM buffer: 000000023fe00000 - 000000023fffffff 
[    0.810042] NetLabel: Initializing
[    0.810044] NetLabel:  domain hash size = 128
[    0.810045] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.810052] NetLabel:  unlabeled traffic allowed by default
[    0.810086] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.810091] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.812103] Switching to clocksource hpet
[    0.812126] Switched to NOHz mode on CPU #0
[    0.812185] Switched to NOHz mode on CPU #1
[    0.812241] Switched to NOHz mode on CPU #3
[    0.812243] Switched to NOHz mode on CPU #2
[    0.816037] AppArmor: AppArmor Filesystem Enabled
[    0.816056] pnp: PnP ACPI init
[    0.816069] ACPI: bus type pnp registered
[    0.816286] pnp 00:00: [bus 00-3e]
[    0.816288] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.816289] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.816291] pnp 00:00: [io  0x0d00-0xffff window]
[    0.816292] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.816294] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.816295] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.816297] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.816298] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.816301] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.816302] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.816304] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.816305] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.816307] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.816308] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.816309] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.816311] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.816312] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.816314] pnp 00:00: [mem 0xbfa00000-0xfeafffff window]
[    0.816315] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.816381] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.816391] pnp 00:01: [io  0x0000-0x001f]
[    0.816393] pnp 00:01: [io  0x0081-0x0091]
[    0.816394] pnp 00:01: [io  0x0093-0x009f]
[    0.816395] pnp 00:01: [io  0x00c0-0x00df]
[    0.816397] pnp 00:01: [dma 4]
[    0.816410] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.816416] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.816430] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.816491] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.816505] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.816512] pnp 00:04: [io  0x00f0]
[    0.816523] pnp 00:04: [irq 13]
[    0.816536] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.816544] pnp 00:05: [io  0x002e-0x002f]
[    0.816545] pnp 00:05: [io  0x004e-0x004f]
[    0.816546] pnp 00:05: [io  0x0061]
[    0.816548] pnp 00:05: [io  0x0063]
[    0.816549] pnp 00:05: [io  0x0065]
[    0.816550] pnp 00:05: [io  0x0067]
[    0.816551] pnp 00:05: [io  0x0070]
[    0.816552] pnp 00:05: [io  0x0080]
[    0.816553] pnp 00:05: [io  0x0092]
[    0.816554] pnp 00:05: [io  0x00b2-0x00b3]
[    0.816556] pnp 00:05: [io  0x0680-0x069f]
[    0.816557] pnp 00:05: [io  0x1000-0x100f]
[    0.816558] pnp 00:05: [io  0xffff]
[    0.816559] pnp 00:05: [io  0xffff]
[    0.816560] pnp 00:05: [io  0x0400-0x0453]
[    0.816561] pnp 00:05: [io  0x0458-0x047f]
[    0.816563] pnp 00:05: [io  0x0500-0x057f]
[    0.816564] pnp 00:05: [io  0x164e-0x164f]
[    0.816597] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.816599] system 00:05: [io  0x1000-0x100f] has been reserved
[    0.816600] system 00:05: [io  0xffff] has been reserved
[    0.816602] system 00:05: [io  0xffff] has been reserved
[    0.816604] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.816605] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.816607] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.816609] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.816611] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.816617] pnp 00:06: [io  0x0070-0x0077]
[    0.816623] pnp 00:06: [irq 8]
[    0.816636] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.816651] pnp 00:07: [io  0x0454-0x0457]
[    0.816673] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.816675] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.816695] pnp 00:08: [io  0x0060]
[    0.816698] pnp 00:08: [io  0x0064]
[    0.816704] pnp 00:08: [irq 1]
[    0.816719] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.816749] pnp 00:09: [irq 12]
[    0.816767] pnp 00:09: Plug and Play ACPI device, IDs SYN0a17 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.816966] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    0.816967] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    0.816968] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    0.816970] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    0.816971] pnp 00:0a: [mem 0xe0000000-0xe3ffffff]
[    0.816972] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    0.816974] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    0.816975] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    0.816976] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    0.816978] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    0.816979] pnp 00:0a: [mem 0xbfa00000-0xbfa00fff]
[    0.817026] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.817029] system 00:0a: [mem 0xfed10000-0xfed17fff] could not be reserved
[    0.817030] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.817032] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.817034] system 00:0a: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.817036] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.817038] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.817040] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.817041] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    0.817043] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.817045] system 00:0a: [mem 0xbfa00000-0xbfa00fff] has been reserved
[    0.817047] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.817069] pnp 00:0b: [mem 0xbfa00000-0xbfa00fff]
[    0.817107] system 00:0b: [mem 0xbfa00000-0xbfa00fff] has been reserved
[    0.817109] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.817198] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    0.817200] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    0.817243] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.817245] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    0.817247] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.817257] pnp: PnP ACPI: found 13 devices
[    0.817258] ACPI: ACPI bus type pnp unregistered
[    0.822619] PCI: max bus depth: 1 pci_try_num: 2
[    0.822651] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.822655] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.822660] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdfbfffff]
[    0.822664] pci 0000:00:1c.0:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.822671] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.822674] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.822679] pci 0000:00:1c.1:   bridge window [mem 0xde800000-0xdf1fffff]
[    0.822683] pci 0000:00:1c.1:   bridge window [mem 0xd1600000-0xd1ffffff 64bit pref]
[    0.822689] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.822692] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
[    0.822697] pci 0000:00:1c.3:   bridge window [mem 0xdde00000-0xde7fffff]
[    0.822701] pci 0000:00:1c.3:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.822707] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.822711] pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
[    0.822716] pci 0000:00:1c.5:   bridge window [mem 0xdd400000-0xdddfffff]
[    0.822720] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.822739] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.822745] pci 0000:00:1c.0: setting latency timer to 64
[    0.822756] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.822760] pci 0000:00:1c.1: setting latency timer to 64
[    0.822770] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.822773] pci 0000:00:1c.3: setting latency timer to 64
[    0.822780] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.822784] pci 0000:00:1c.5: setting latency timer to 64
[    0.822788] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.822789] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.822791] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.822792] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.822794] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.822795] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.822797] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.822798] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.822800] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.822802] pci_bus 0000:00: resource 13 [mem 0xbfa00000-0xfeafffff]
[    0.822803] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    0.822805] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.822806] pci_bus 0000:01: resource 1 [mem 0xdf200000-0xdfbfffff]
[    0.822808] pci_bus 0000:01: resource 2 [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.822810] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.822811] pci_bus 0000:02: resource 1 [mem 0xde800000-0xdf1fffff]
[    0.822813] pci_bus 0000:02: resource 2 [mem 0xd1600000-0xd1ffffff 64bit pref]
[    0.822814] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.822816] pci_bus 0000:03: resource 1 [mem 0xdde00000-0xde7fffff]
[    0.822817] pci_bus 0000:03: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.822819] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    0.822821] pci_bus 0000:04: resource 1 [mem 0xdd400000-0xdddfffff]
[    0.822822] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.822846] NET: Registered protocol family 2
[    0.823042] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.823844] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.825006] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.825128] TCP: Hash tables configured (established 524288 bind 65536)
[    0.825130] TCP reno registered
[    0.825142] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.825173] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.825274] NET: Registered protocol family 1
[    0.825285] pci 0000:00:02.0: Boot video device
[    1.076113] PCI: CLS 64 bytes, default 64
[    1.076122] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.076124] Placing 64MB software IO TLB between ffff8800b6bcd000 - ffff8800babcd000
[    1.076125] software IO TLB at phys 0xb6bcd000 - 0xbabcd000
[    1.076469] audit: initializing netlink socket (disabled)
[    1.076476] type=2000 audit(1321549386.772:1): initialized
[    1.100690] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.116936] VFS: Disk quotas dquot_6.5.2
[    1.116980] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.117393] fuse init (API version 7.16)
[    1.117454] msgmni has been set to 15784
[    1.117743] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.117766] io scheduler noop registered
[    1.117769] io scheduler deadline registered
[    1.117795] io scheduler cfq registered (default)
[    1.118030] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.118045] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.118072] intel_idle: MWAIT substates: 0x21120
[    1.118074] intel_idle: v0.4 model 0x2A
[    1.118075] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.118134] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.118162] ACPI: AC Adapter [AC0] (off-line)
[    1.118236] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.119526] ACPI: Lid Switch [LID]
[    1.119552] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.119555] ACPI: Sleep Button [SLPB]
[    1.119579] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.119581] ACPI: Power Button [PWRF]
[    1.119601] ACPI: acpi_idle yielding to intel_idle
[    1.121525] thermal LNXTHERM:00: registered as thermal_zone0
[    1.121527] ACPI: Thermal Zone [TZ00] (48 C)
[    1.121539] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.121559] ERST: Table is not found!
[    1.121613] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.122171] ACPI: Battery Slot [BAT0] (battery present)
[    1.163217] Freeing initrd memory: 19464k freed
[    1.328392] Linux agpgart interface v0.103
[    1.328450] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.328572] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.329801] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.329889] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.330575] brd: module loaded
[    1.330889] loop: module loaded
[    1.331154] Fixed MDIO Bus: probed
[    1.331169] PPP generic driver version 2.4.2
[    1.331189] tun: Universal TUN/TAP device driver, 1.6
[    1.331190] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.331236] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.331251] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.331267] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.331270] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.331291] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.331313] ehci_hcd 0000:00:1a.0: debug port 2
[    1.335186] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.335200] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xdfc08000
[    1.347937] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.348099] hub 1-0:1.0: USB hub found
[    1.348102] hub 1-0:1.0: 2 ports detected
[    1.348151] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.348161] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.348164] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.348187] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.348208] ehci_hcd 0000:00:1d.0: debug port 2
[    1.352087] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.352097] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xdfc07000
[    1.367931] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.368083] hub 2-0:1.0: USB hub found
[    1.368085] hub 2-0:1.0: 2 ports detected
[    1.368120] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.368127] uhci_hcd: USB Universal Host Controller Interface driver
[    1.368168] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.369625] i8042: Detected active multiplexing controller, rev 1.1
[    1.370434] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.370439] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.370459] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.370472] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.370486] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.370544] mousedev: PS/2 mouse device common for all mice
[    1.370633] rtc_cmos 00:06: RTC can wake from S4
[    1.370713] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.370738] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.370803] device-mapper: uevent: version 1.0.3
[    1.370847] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.370921] cpuidle: using governor ladder
[    1.371038] cpuidle: using governor menu
[    1.371040] EFI Variables Facility v0.08 2004-May-17
[    1.371182] TCP cubic registered
[    1.371260] NET: Registered protocol family 10
[    1.371553] NET: Registered protocol family 17
[    1.371562] Registering the dns_resolver key type
[    1.371623] PM: Hibernation image not present or could not be loaded.
[    1.371630] registered taskstats version 1
[    1.384181]   Magic number: 3:624:87
[    1.384209] button LNXPWRBN:00: hash matches
[    1.384288] rtc_cmos 00:06: setting system clock to 2011-11-17 17:03:07 UTC (1321549387)
[    1.384891] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.384892] EDD information not available.
[    1.386035] Freeing unused kernel memory: 984k freed
[    1.386124] Write protecting the kernel read-only data: 10240k
[    1.386336] Freeing unused kernel memory: 20k freed
[    1.389146] Freeing unused kernel memory: 1400k freed
[    1.399785] udevd[91]: starting version 173
[    1.404566] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.417198] atl1c 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.417212] atl1c 0000:04:00.0: setting latency timer to 64
[    1.417444] ahci 0000:00:1f.2: version 3.0
[    1.417454] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.417488] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.417511] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.417521] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    1.417525] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.417578] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    1.420674] [drm] Initialized drm 1.1.0 20060810
[    1.431938] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.431943] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.431949] ahci 0000:00:1f.2: setting latency timer to 64
[    1.435932] wmi: Mapper loaded
[    1.440639] scsi0 : ahci
[    1.440768] scsi1 : ahci
[    1.440836] scsi2 : ahci
[    1.440893] scsi3 : ahci
[    1.440956] scsi4 : ahci
[    1.441021] scsi5 : ahci
[    1.441295] ata1: SATA max UDMA/133 abar m2048@0xdfc06000 port 0xdfc06100 irq 42
[    1.441297] ata2: DUMMY
[    1.441299] ata3: SATA max UDMA/133 abar m2048@0xdfc06000 port 0xdfc06200 irq 42
[    1.441301] ata4: DUMMY
[    1.441302] ata5: DUMMY
[    1.441304] ata6: DUMMY
[    1.441368] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.441372] i915 0000:00:02.0: setting latency timer to 64
[    1.553012] xhci_hcd 0000:03:00.0: irq 19, io mem 0xdde00000
[    1.553155] xHCI xhci_add_endpoint called for root hub
[    1.553157] xHCI xhci_check_bandwidth called for root hub
[    1.553184] hub 3-0:1.0: USB hub found
[    1.553191] hub 3-0:1.0: 1 port detected
[    1.553240] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.553271] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
[    1.553317] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    1.553321] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.553323] [drm] Driver supports precise vblank timestamp query.
[    1.553336] xHCI xhci_add_endpoint called for root hub
[    1.553337] xHCI xhci_check_bandwidth called for root hub
[    1.553357] hub 4-0:1.0: USB hub found
[    1.553363] hub 4-0:1.0: 1 port detected
[    1.553394] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    1.553409] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.584351] atl1c 0000:04:00.0: version 1.0.1.0-NAPI
[    1.735723] fbcon: inteldrmfb (fb0) is primary device
[    1.736183] Console: switching to colour frame buffer device 170x48
[    1.736195] fb0: inteldrmfb frame buffer device
[    1.736196] drm: registered panic notifier
[    1.759852] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.763849] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.763891] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.805017] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[    1.805224] ata3.00: ACPI cmd ef/90:06:00:00:00:00 (SET FEATURES) succeeded
[    1.805228] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.805242] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.805276] acpi device:4e: registered as cooling_device4
[    1.805468] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    1.805490] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.805519] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.806991] ata3.00: ATAPI: MATSHITADVD-RAM UJ8A2ASW, 1.00, max UDMA/100
[    1.810648] ata3.00: ACPI cmd ef/90:06:00:00:00:00 (SET FEATURES) succeeded
[    1.810659] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.810668] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.812608] ata3.00: configured for UDMA/100
[    1.814341] ata1.00: ACPI cmd ef/90:06:00:00:00:00 (SET FEATURES) succeeded
[    1.814353] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.814361] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.823516] ata1.00: ATA-8: ST9750420AS, 0002SDM1, max UDMA/133
[    1.823525] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.863902] ata1.00: ACPI cmd ef/90:06:00:00:00:00 (SET FEATURES) succeeded
[    1.863914] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.863922] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.864748] ata1.00: configured for UDMA/133
[    1.864977] scsi 0:0:0:0: Direct-Access     ATA      ST9750420AS      0002 PQ: 0 ANSI: 5
[    1.865105] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.865141] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.865144] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.865193] sd 0:0:0:0: [sda] Write Protect is off
[    1.865196] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.865225] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.868081] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8A2ASW 1.00 PQ: 0 ANSI: 5
[    1.872326] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.872336] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.872475] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.872506] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.896528] hub 1-1:1.0: USB hub found
[    1.896570] hub 1-1:1.0: 6 ports detected
[    1.937796]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.938144] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.007754] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.075744] Refined TSC clocksource calibration: 2693.880 MHz.
[    2.075756] Switching to clocksource tsc
[    2.140286] hub 2-1:1.0: USB hub found
[    2.140363] hub 2-1:1.0: 6 ports detected
[    2.211738] usb 1-1.1: new high speed USB device number 3 using ehci_hcd
[    2.375854] usb 1-1.2: new high speed USB device number 4 using ehci_hcd
[    3.006616] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   13.395155] udevd[382]: starting version 173
[   13.426934] lp: driver loaded but no devices found
[   13.430100] cfg80211: Calling CRDA to update world regulatory domain
[   13.432920] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   13.436942] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.436946] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   13.436998] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.437009] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.437041] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   13.446691] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.446701] mei 0000:00:16.0: setting latency timer to 64
[   13.447664] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   13.447667] iwlagn 0000:02:00.0: Device SKU: 0X9
[   13.447669] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.447697] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.447791] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[   13.467777] type=1400 audit(1321567399.580:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[   13.468076] type=1400 audit(1321567399.584:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[   13.468262] type=1400 audit(1321567399.584:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[   13.470446] Adding 8295420k swap on /dev/sda6.  Priority:-1 extents:1 across:8295420k 
[   13.489706] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.490072] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.490097] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.569163] asus_wmi: ASUS WMI generic driver loaded
[   13.569409] asus_wmi: Initialization: 0x1
[   13.569568] asus_wmi: SFUN value: 0x1a0af7
[   13.570095] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input5
[   13.575395] cfg80211: World regulatory domain updated:
[   13.575397] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.575400] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.575403] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.575405] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.575407] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.575409] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.586318] asus_wmi: Backlight controlled by ACPI video driver
[   13.613543] Linux video capture interface: v2.00
[   13.613990] uvcvideo: Found UVC 1.00 device ASUS USB2.0 WebCam (058f:a014)
[   13.616814] input: ASUS USB2.0 WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6
[   13.616851] usbcore: registered new interface driver uvcvideo
[   13.616852] USB Video Class driver (v1.1.0)
[   13.621911] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   13.622052] Registered led device: phy0-led
[   13.622075] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.624245] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.030510] hda_codec: ALC269VB: BIOS auto-probing.
[   14.036234] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   14.036393] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.036545] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.036596] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.210975] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.213065] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[   14.244737] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   14.542603] ppdev: user-space parallel port driver
[   14.548027] type=1400 audit(1321567400.664:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=981 comm="apparmor_parser"
[   14.548406] type=1400 audit(1321567400.664:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=981 comm="apparmor_parser"
[   14.601119] type=1400 audit(1321567400.716:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1001 comm="apparmor_parser"
[   14.601171] type=1400 audit(1321567400.716:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=998 comm="apparmor_parser"
[   14.601202] type=1400 audit(1321567400.716:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=999 comm="apparmor_parser"
[   14.601510] type=1400 audit(1321567400.716:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=999 comm="apparmor_parser"
[   14.602230] type=1400 audit(1321567400.716:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1000 comm="apparmor_parser"
[   14.669364] init: failsafe main process (914) killed by TERM signal
[   14.669985] init: apport pre-start process (1035) terminated with status 1
[   14.680405] init: apport post-stop process (1064) terminated with status 1
[   14.823532] Bluetooth: Core ver 2.16
[   14.823552] NET: Registered protocol family 31
[   14.823553] Bluetooth: HCI device and connection manager initialized
[   14.823555] Bluetooth: HCI socket layer initialized
[   14.823556] Bluetooth: L2CAP socket layer initialized
[   14.823598] Bluetooth: SCO socket layer initialized
[   14.825009] Bluetooth: RFCOMM TTY layer initialized
[   14.825013] Bluetooth: RFCOMM socket layer initialized
[   14.825015] Bluetooth: RFCOMM ver 1.11
[   14.825550] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.825552] Bluetooth: BNEP filters: protocol multicast
[   14.850157] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.856999] atl1c 0000:04:00.0: irq 46 for MSI/MSI-X
[   14.940496] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.954239] init: anacron main process (1052) killed by TERM signal
[   20.741052] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   21.733815] init: plymouth-stop pre-start process (1350) terminated with status 1
[   25.173492] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   28.005671] CPU2: Package power limit notification (total events = 1)
[   28.005675] CPU3: Package power limit notification (total events = 1)
[   28.005678] CPU1: Package power limit notification (total events = 1)
[   28.005681] CPU0: Package power limit notification (total events = 1)
[   28.016675] CPU1: Package power limit normal
[   28.016678] CPU3: Package power limit normal
[   28.016681] CPU2: Package power limit normal
[   28.016683] CPU0: Package power limit normal
[   33.265025] wlan0: authenticate with e0:91:f5:fd:1f:8e (try 1)
[   33.270527] wlan0: authenticated
[   33.271150] wlan0: associate with e0:91:f5:fd:1f:8e (try 1)
[   33.275062] wlan0: RX AssocResp from e0:91:f5:fd:1f:8e (capab=0x411 status=0 aid=1)
[   33.275072] wlan0: associated
[   33.283804] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.670458] wlan0: no IPv6 routers present
[   43.875392] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 4
[   47.401062] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = e0:91:f5:fd:1f:8e tid = 0

```

Kernel Log as requested

---

### Post by WinterMadness on 2011-11-18
more bumps for obvious reasons

---

### Post by WinterMadness on 2011-11-19
bump

---

### Post by matt_symes on 2011-11-21
Hi

> Hello, in order to boot my computer acpi has to be set to nothing or off  however when its set to nothing, it only boots sometimes.When it is not booting, what exactly is happening ?
[FONT=monospace]
[/FONT]> [    0.000000] Malformed early option 'acpi'I assume you had the *acpi=* kernel parameter set when you booted ?
[FONT=monospace]
[/FONT]> [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignoredHave you tried booting with *acpi=linux* as a kernel parameter ?

Is your BIOS up to date ?

Try some of the acpi boot options here

[http://www.lesswatts.org/projects/acpi/debug.php](http://www.lesswatts.org/projects/acpi/debug.php)

Kind regards

---

### Post by WinterMadness on 2011-11-21
I dont know if my BIOS is up to date,the laptop is new, so I imagine so, but I can find out.

"If "acpi=off" makes the failure goes away, then it is likely an ACPI bug. But if a different failure occurs with ACPI disabled, then the test was inconclusive."

^That sounds like my problem

So this is how it works when it doesnt boot:

First time: In grub, I select ubuntu, and then its just a blue screen (because grub is blue, if grub is black for you, I imagine it would just be purely black)

Second time: Blinking cursor

On average, I have to boot it about 4 times before I can actually get into the OS.

---

### Post by WinterMadness on 2011-11-21
I seemed to have found the solution

go into the bios, and turn off vt-d. everything boots normally. 

this of course probably only applies to the asus u46-bal6

---

