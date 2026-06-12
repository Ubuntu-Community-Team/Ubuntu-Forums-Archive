---
title: "Karmic Freezes, where can I find the logs?"
date: 2010-04-06
forum: General Help
---

### Post by RJ12 on 2010-04-06
Well, I installed Karmic no problems with drivers or malfunctioning hardware. The problem is I get random freezes where the computer will stop doing what I ask it to do. Num Lock Key does not respond, neither does anything else but the mouse. Where would I find the logs to know what is happening?

---

### Post by cjhabs on 2010-04-06
> **RJ12 said:**
> Well, I installed Karmic no problems with drivers or malfunctioning hardware. The problem is I get random freezes where the computer will stop doing what I ask it to do. Num Lock Key does not respond, neither does anything else but the mouse. Where would I find the logs to know what is happening?

/var/log contains various log files.
The "message" and "syslog" files should be a good starting point.

---

### Post by RJ12 on 2010-04-06
Umm... found the logs, don't really understand them. Do you think I could post it and someone could analyse it?

---

### Post by Yvan300 on 2010-04-06
Yeah, knock yourself out!

---

### Post by RJ12 on 2010-04-06
Everything from today in messages

```
Apr  6 06:55:09 ubuntu-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  6 06:55:09 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="813" x-info="http://www.rsyslog.com"] (re)start
Apr  6 06:55:09 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 102
Apr  6 06:55:09 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] KERNEL supported cpus:
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   Intel GenuineIntel
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   AMD AuthenticAMD
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   NSC Geode by NSC
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   Centaur CentaurHauls
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe74000 (usable)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000002fe74000 - 000000002fe76000 (ACPI NVS)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000002fe76000 - 000000002fe97000 (ACPI data)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000002fe97000 - 000000002ff00000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] DMI 2.3 present.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] last_pfn = 0x2fe74 max_arch_pfn = 0x100000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] modified physical RAM map:
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000002fe74000 (usable)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 000000002fe74000 - 000000002fe76000 (ACPI NVS)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 000000002fe76000 - 000000002fe97000 (ACPI data)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 000000002fe97000 - 000000002ff00000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000002fe74000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] RAMDISK: 237ca000 - 23f16502
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: RSDP 000feb80 00014 (v00 DELL  )
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: RSDT 000fd22a 00034 (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: FACP 000fd25e 00074 (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: DSDT fffcc0f1 02404 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: FACS 2fe74000 00040
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: SSDT fffce632 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: APIC 000fd2d2 0006C (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: BOOT 000fd33e 00028 (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] 766MB LOWMEM available.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   mapped low ram: 0 - 2fe74000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   low ram: 0 - 2fe74000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 2fe74000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000dfd0
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fe74000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #4 [00237ca000 - 0023f16502]          RAMDISK ==> [00237ca000 - 0023f16502]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #6 [00008a9000 - 00008ac1c4]              BRK ==> [00008a9000 - 00008ac1c4]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   #8 [0000008000 - 000000e000]          BOOTMAP ==> [0000008000 - 000000e000]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Zone PFN ranges:
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fe74
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]   HighMem  0x0002fe74 -> 0x0002fe74
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Movable zone start PFN for each node
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x000000a0
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0002fe74
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Using APIC driver default
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Allocating PCI resources starting at 2ff00000 (gap: 2ff00000:ced00000)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages at c1604000, static data 35612 bytes
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194579
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=3b668ef7-e422-4a2e-bb76-5639ae3dccfe ro quiet splash
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Initializing CPU#0
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] allocated 3924240 bytes of page_cgroup
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Memory: 757780k/784848k available (4565k kernel code, 26380k reserved, 2143k data, 540k init, 0k highmem)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] virtual kernel memory layout:
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     vmalloc : 0xf0674000 - 0xff7fe000   ( 241 MB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xefe74000   ( 766 MB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.000000] Detected 2392.223 MHz processor.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.001497] Console: colour VGA+ 80x25
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.001505] console [tty0] enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.44 BogoMIPS (lpj=9568892)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004056] Security Framework initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004094] AppArmor: AppArmor initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004113] Mount-cache hash table entries: 512
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004410] Initializing cgroup subsys ns
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004424] Initializing cgroup subsys cpuacct
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004433] Initializing cgroup subsys memory
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004448] Initializing cgroup subsys freezer
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004453] Initializing cgroup subsys net_cls
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004488] CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004495] CPU: L2 cache: 128K
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004500] CPU: Hyper-Threading is disabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004507] mce: CPU supports 4 MCE banks
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004524] CPU0: Thermal monitoring enabled (TM1)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004545] Performance Counters: no PMU driver, software counters only.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.004558] Checking 'hlt' instruction... OK.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.021106] SMP alternatives: switching to UP code
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.032027] ACPI: Core revision 20090521
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.069388] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.109088] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] Brought up 1 CPUs
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] Total of 1 processors activated (4784.44 BogoMIPS).
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] Booting paravirtualized kernel on bare hardware
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] regulator: core version 0.5
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] Time:  6:54:58  Date: 04/06/10
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] NET: Registered protocol family 16
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] EISA bus registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] ACPI: bus type pci registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112001] PCI: Using configuration type 1 for base access
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.112661] bio: create slab <bio-0> at 0
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.143602] ACPI: Interpreter enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.143619] ACPI: (supports S0 S1 S3 S4 S5)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.143675] ACPI: Using IOAPIC for interrupt routing
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.179799] ACPI: No dock devices found.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.181442] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182072] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182080] pci 0000:00:1d.7: PME# disabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182144] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182146] * this clock source is slow. If you are sure your timer does not have
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182148] * this bug, please use "acpi_pm_good" to disable the workaround
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182202] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182209] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182488] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182495] pci 0000:00:1f.5: PME# disabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182616] pci 0000:01:05.0: PME# supported from D3hot D3cold
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182622] pci 0000:01:05.0: PME# disabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182730] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182736] pci 0000:01:09.0: PME# disabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.182774] pci 0000:00:1e.0: transparent bridge
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.350804] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.351200] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.351587] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.351972] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.352388] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.352774] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.353162] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.353556] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.354024] SCSI subsystem initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.354468] usbcore: registered new interface driver usbfs
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.354525] usbcore: registered new interface driver hub
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.354644] usbcore: registered new device driver usb
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355062] ACPI: WMI: Mapper loaded
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355069] PCI: Using ACPI for IRQ routing
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355361] Bluetooth: Core ver 2.15
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355517] NET: Registered protocol family 31
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355521] Bluetooth: HCI device and connection manager initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355527] Bluetooth: HCI socket layer initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355531] NetLabel: Initializing
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355534] NetLabel:  domain hash size = 128
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355537] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.355565] NetLabel:  unlabeled traffic allowed by default
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.358668] pnp: PnP ACPI init
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.358713] ACPI: bus type pnp registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.382137] pnp 00:09: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.382147] pnp 00:09: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383038] pnp: PnP ACPI: found 10 devices
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383045] ACPI: ACPI bus type pnp unregistered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383053] PnPBIOS: Disabled by ACPI PNP
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383082] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383089] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383094] system 00:00: iomem range 0x1000000-0x2fe73fff could not be reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383100] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383106] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383112] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383118] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383123] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383129] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.383150] system 00:09: ioport range 0xc00-0xc7f has been reserved
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418062] AppArmor: AppArmor Filesystem Enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418125] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418131] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418140] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418147] pci 0000:00:1e.0:   PREFETCH window: 0x30000000-0x300fffff
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418266] NET: Registered protocol family 2
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.418444] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.419093] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.420813] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.421725] TCP: Hash tables configured (established 131072 bind 65536)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.421736] TCP reno registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.422015] NET: Registered protocol family 1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.422139] Trying to unpack rootfs image as initramfs...
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.761857] Freeing initrd memory: 7473k freed
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.777317] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.777325] Simple Boot Flag at 0x7a set to 0x1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.777501] cpufreq-nforce2: No nForce2 chipset.
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.777567] Scanning for low memory corruption every 60 seconds
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.777793] audit: initializing netlink socket (disabled)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.777827] type=2000 audit(1270536898.776:1): initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.787574] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.789953] VFS: Disk quotas dquot_6.5.2
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.790083] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.791297] fuse init (API version 7.12)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.791513] msgmni has been set to 1495
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792199] alg: No test for stdrng (krng)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792251] io scheduler noop registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792255] io scheduler anticipatory registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792259] io scheduler deadline registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792392] io scheduler cfq registered (default)
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792680] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792731] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792971] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.792980] ACPI: Power Button [PWRF]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.793076] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.793090] ACPI: Power Button [VBTN]
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.793575] processor LNXCPU:00: registered as cooling_device0
Apr  6 06:55:09 ubuntu-desktop kernel: [    0.820332] isapnp: Scanning for PnP cards...
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.174478] isapnp: No Plug & Play device found
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.177510] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.177688] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.178282] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.180668] brd: module loaded
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.181865] loop: module loaded
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.182096] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.182384] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.182681] scsi0 : ata_piix
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.182947] scsi1 : ata_piix
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.183044] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.183051] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.185065] Fixed MDIO Bus: probed
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.185148] PPP generic driver version 2.4.2
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.185411] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.185495] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.185533] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.185699] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.189652] ehci_hcd 0000:00:1d.7: debug port 1
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.190088] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204215] usb usb1: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204297] hub 1-0:1.0: USB hub found
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204323] hub 1-0:1.0: 6 ports detected
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204481] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204533] uhci_hcd: USB Universal Host Controller Interface driver
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204648] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204670] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204791] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.204849] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205053] usb usb2: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205127] hub 2-0:1.0: USB hub found
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205154] hub 2-0:1.0: 2 ports detected
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205310] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205332] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205444] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205501] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205702] usb usb3: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205780] hub 3-0:1.0: USB hub found
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205808] hub 3-0:1.0: 2 ports detected
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205940] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.205966] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.206074] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.206133] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.206354] usb usb4: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.206427] hub 4-0:1.0: USB hub found
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.206454] hub 4-0:1.0: 2 ports detected
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.206720] PNP: No PS/2 controller found. Probing ports directly.
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.209749] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.209765] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.209949] mice: PS/2 mouse device common for all mice
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.210191] rtc_cmos 00:05: RTC can wake from S4
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.210292] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.210331] rtc0: alarms up to one day, 242 bytes nvram
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.210588] device-mapper: uevent: version 1.0.3
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.210891] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.211192] device-mapper: multipath: version 1.1.0 loaded
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.211199] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.211572] EISA: Probing bus 0 at eisa.0
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.211613] EISA: Detected 0 cards.
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.211800] cpuidle: using governor ladder
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.211805] cpuidle: using governor menu
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.212709] TCP cubic registered
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.213022] NET: Registered protocol family 10
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.213878] lo: Disabled Privacy Extensions
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214329] NET: Registered protocol family 17
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214395] Bluetooth: L2CAP ver 2.13
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214399] Bluetooth: L2CAP socket layer initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214404] Bluetooth: SCO (Voice Link) ver 0.6
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214407] Bluetooth: SCO socket layer initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214540] Bluetooth: RFCOMM TTY layer initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214550] Bluetooth: RFCOMM socket layer initialized
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214553] Bluetooth: RFCOMM ver 1.11
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214645] Using IPI No-Shortcut mode
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.214897] registered taskstats version 1
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.215106]   Magic number: 6:960:922
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.215226] rtc_cmos 00:05: setting system clock to 2010-04-06 06:54:59 UTC (1270536899)
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.215233] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.215236] EDD information not available.
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.368328] ata2.00: ATAPI: TSST CD-RW/DVD-ROM TSH492B, TB06, max UDMA/33
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.400444] ata2.00: configured for UDMA/33
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.408595] ata1.00: ATA-6: ST380011A, 8.16, max UDMA/100
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.408603] ata1.00: 156250000 sectors, multi 8: LBA48 
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.424442] ata1.00: configured for UDMA/100
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.424702] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.16 PQ: 0 ANSI: 5
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.424994] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.425168] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.425376] sd 0:0:0:0: [sda] Write Protect is off
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.425488] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.426014]  sda:
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.426889] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSH492B TB06 PQ: 0 ANSI: 5
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.429501] sr0: scsi3-mmc drive: 5x/48x writer cd/rw xa/form2 cdda tray
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.429510] Uniform CD-ROM driver Revision: 3.20
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.429849] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.449044]  sda1 sda2 < sda5 sda6 >
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.491900] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.491939] Freeing unused kernel memory: 540k freed
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.493032] Write protecting the kernel text: 4568k
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.493074] Write protecting the kernel read-only data: 1836k
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.576071] usb 1-3: new high speed USB device using ehci_hcd and address 3
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.919969] usb 1-3: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.924643] Linux agpgart interface v0.103
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.929820] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.929997] agpgart-intel 0000:00:00.0: detected 892K stolen memory
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.935561] Floppy drive(s): fd0 is 1.44M
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.964619] FDC 0 is a post-1991 82077
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.968749] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
Apr  6 06:55:09 ubuntu-desktop kernel: [    1.985830] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.220467] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.220518] b44.c:v2.0
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.243264] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:43:7f:05:03
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.244622] [drm] Initialized drm 1.1.0 20060810
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.267291] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.410099] usb 2-2: new low speed USB device using uhci_hcd and address 2
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.444632] [drm] fb0: inteldrmfb frame buffer device
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.444655] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.556273] [drm] DAC-5: set mode 1280x1024 10
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.566875] Console: switching to colour frame buffer device 160x64
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.646901] usb 2-2: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.664162] usbcore: registered new interface driver hiddev
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.679636] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.679872] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.0-2/input0
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.679922] usbcore: registered new interface driver usbhid
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.679931] usbhid: v2.6:USB HID core driver
Apr  6 06:55:09 ubuntu-desktop kernel: [    2.888049] usb 3-2: new low speed USB device using uhci_hcd and address 2
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.090785] usb 3-2: configuration #1 chosen from 1 choice
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.119573] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.119860] generic-usb 0003:093A:2510.0002: input,hidraw1: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-2/input0
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.444153] PM: Starting manual resume from disk
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.481635] EXT4-fs (sda5): barriers enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.499531] kjournald2 starting: pid 316, dev sda5:8, commit interval 5 seconds
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.499579] EXT4-fs (sda5): delayed allocation enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.499586] EXT4-fs: file extents enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.503681] EXT4-fs: mballoc enabled
Apr  6 06:55:09 ubuntu-desktop kernel: [    3.503730] EXT4-fs (sda5): mounted filesystem with ordered data mode
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.152138] type=1505 audit(1270536902.436:2): operation="profile_load" pid=339 name=/usr/share/gdm/guest-session/Xsession
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.158202] type=1505 audit(1270536902.440:3): operation="profile_load" pid=340 name=/sbin/dhclient3
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.158990] type=1505 audit(1270536902.440:4): operation="profile_load" pid=340 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.159443] type=1505 audit(1270536902.440:5): operation="profile_load" pid=340 name=/usr/lib/connman/scripts/dhclient-script
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.205262] type=1505 audit(1270536902.488:6): operation="profile_load" pid=341 name=/usr/bin/evince
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.217479] type=1505 audit(1270536902.500:7): operation="profile_load" pid=341 name=/usr/bin/evince-previewer
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.224913] type=1505 audit(1270536902.508:8): operation="profile_load" pid=341 name=/usr/bin/evince-thumbnailer
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.245672] type=1505 audit(1270536902.528:9): operation="profile_load" pid=343 name=/usr/lib/cups/backend/cups-pdf
Apr  6 06:55:09 ubuntu-desktop kernel: [    4.246677] type=1505 audit(1270536902.528:10): operation="profile_load" pid=343 name=/usr/sbin/cupsd
Apr  6 06:55:09 ubuntu-desktop kernel: [    5.659508] Adding 1285160k swap on /dev/sda6.  Priority:-1 extents:1 across:1285160k 
Apr  6 06:55:09 ubuntu-desktop kernel: [    5.963014] EXT4-fs (sda5): internal journal on sda5:8
Apr  6 06:55:09 ubuntu-desktop kernel: [    5.963949] udev: starting version 147
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.383918] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.612413] cfg80211: Calling CRDA to update world regulatory domain
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.620342] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.635057] intel_rng: FWH not detected
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.974338] parport_pc 00:08: reported by Plug and Play ACPI
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.974399] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Apr  6 06:55:09 ubuntu-desktop kernel: [    7.994011] lp: driver loaded but no devices found
Apr  6 06:55:09 ubuntu-desktop kernel: [    8.072355] lp0: using parport0 (interrupt-driven).
Apr  6 06:55:09 ubuntu-desktop kernel: [    8.341389] dell-wmi: No known WMI GUID found
Apr  6 06:55:09 ubuntu-desktop kernel: [    8.360110] ppdev: user-space parallel port driver
Apr  6 06:55:09 ubuntu-desktop kernel: [    8.428842] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.251607] Registered led device: rt73usb-phy0::radio
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.251676] Registered led device: rt73usb-phy0::assoc
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.251724] Registered led device: rt73usb-phy0::quality
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.253095] usbcore: registered new interface driver rt73usb
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.429152] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.709108] __ratelimit: 3 callbacks suppressed
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.709116] type=1505 audit(1270554907.992:12): operation="profile_replace" pid=688 name=/usr/share/gdm/guest-session/Xsession
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.714565] type=1505 audit(1270554907.996:13): operation="profile_replace" pid=689 name=/sbin/dhclient3
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.715401] type=1505 audit(1270554907.996:14): operation="profile_replace" pid=689 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.716964] type=1505 audit(1270554908.000:15): operation="profile_replace" pid=689 name=/usr/lib/connman/scripts/dhclient-script
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.728996] type=1505 audit(1270554908.012:16): operation="profile_replace" pid=690 name=/usr/bin/evince
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.742222] type=1505 audit(1270554908.024:17): operation="profile_replace" pid=690 name=/usr/bin/evince-previewer
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.749981] type=1505 audit(1270554908.032:18): operation="profile_replace" pid=690 name=/usr/bin/evince-thumbnailer
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.766299] type=1505 audit(1270554908.048:19): operation="profile_replace" pid=692 name=/usr/lib/cups/backend/cups-pdf
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.767342] type=1505 audit(1270554908.048:20): operation="profile_replace" pid=692 name=/usr/sbin/cupsd
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.773788] type=1505 audit(1270554908.056:21): operation="profile_replace" pid=693 name=/usr/sbin/tcpdump
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.852392] intel8x0_measure_ac97_clock: measured 53646 usecs (2585 samples)
Apr  6 06:55:09 ubuntu-desktop kernel: [    9.852401] intel8x0: clocking to 48000
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812951] cfg80211: World regulatory domain updated:
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812961] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812967] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812972] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812977] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812982] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  6 06:55:11 ubuntu-desktop kernel: [   12.812988] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  6 06:55:15 ubuntu-desktop kernel: [   16.908181] rt73usb 1-3:1.0: firmware: requesting rt73.bin
Apr  6 06:55:16 ubuntu-desktop kernel: [   17.965453] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  6 06:55:16 ubuntu-desktop kernel: [   18.056886] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  6 06:56:03 ubuntu-desktop pulseaudio[1382]: ratelimit.c: 3 events suppressed
Apr  6 06:56:04 ubuntu-desktop kernel: [   65.880844] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  6 06:56:41 ubuntu-desktop kernel: [  104.208067] usb 1-6: new high speed USB device using ehci_hcd and address 5
Apr  6 06:56:41 ubuntu-desktop kernel: [  104.341677] usb 1-6: configuration #1 chosen from 2 choices
Apr  6 06:56:41 ubuntu-desktop kernel: [  104.411397] Initializing USB Mass Storage driver...
Apr  6 06:56:41 ubuntu-desktop kernel: [  104.415237] scsi2 : SCSI emulation for USB Mass Storage devices
Apr  6 06:56:41 ubuntu-desktop kernel: [  104.415877] usbcore: registered new interface driver usb-storage
Apr  6 06:56:41 ubuntu-desktop kernel: [  104.415890] USB Mass Storage support registered.
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.419170] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.70 PQ: 0 ANSI: 0
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.420797] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.435427] sd 2:0:0:0: [sdb] 1926080 4096-byte logical blocks: (7.88 GB/7.34 GiB)
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.438250] sd 2:0:0:0: [sdb] Write Protect is off
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.445565] sd 2:0:0:0: [sdb] 1926080 4096-byte logical blocks: (7.88 GB/7.34 GiB)
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.447496]  sdb: sdb1
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.476882] sd 2:0:0:0: [sdb] 1926080 4096-byte logical blocks: (7.88 GB/7.34 GiB)
Apr  6 06:56:46 ubuntu-desktop kernel: [  109.479052] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Apr  6 07:11:41 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="813" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788060] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788071]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788088]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788103]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788118] Call Trace:
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788134]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788142]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788186]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788201]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788227]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788238]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788248]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788256]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788263]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788270]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:14:57 ubuntu-desktop kernel: [ 8400.788278]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788056] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788065]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788081]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788096]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788111] Call Trace:
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788129]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788137]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788183]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788198]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788225]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788236]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788245]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788254]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788261]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788268]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:16:57 ubuntu-desktop kernel: [ 8520.788276]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788054] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788064]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788080]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788096]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788111] Call Trace:
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788129]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788137]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788181]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788195]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788222]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788233]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788243]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788251]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788259]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788266]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:18:57 ubuntu-desktop kernel: [ 8640.788274]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788057] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788067]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788083]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788099]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788114] Call Trace:
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788132]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788140]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788186]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788200]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788227]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788239]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788248]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788256]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788263]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788270]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:20:57 ubuntu-desktop kernel: [ 8760.788278]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788056] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788066]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788082]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788096]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788111] Call Trace:
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788128]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788136]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788179]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788193]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788220]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788231]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788241]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788249]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788257]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788264]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:22:57 ubuntu-desktop kernel: [ 8880.788272]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788052] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788062]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788078]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788093]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788108] Call Trace:
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788126]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788134]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788178]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788193]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788220]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788231]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788241]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788249]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788256]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788263]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:24:57 ubuntu-desktop kernel: [ 9000.788271]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788050] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788060]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788077]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788092]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788107] Call Trace:
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788125]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788133]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788177]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788192]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788219]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788230]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788239]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788248]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788255]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788261]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:26:57 ubuntu-desktop kernel: [ 9120.788270]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788050] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788060]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788075]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788090]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788105] Call Trace:
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788123]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788131]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788173]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788187]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788215]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788226]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788236]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788245]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788252]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788259]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:28:57 ubuntu-desktop kernel: [ 9240.788269]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788058] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788069]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788087]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788102]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788116] Call Trace:
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788134]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788141]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788185]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788199]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788226]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788237]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788246]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788254]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788261]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788268]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:30:57 ubuntu-desktop kernel: [ 9360.788276]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788056] i915/0        D c08145c0     0   232      2 0x00000000
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788066]  e35b5f04 00000046 e3878cbc c08145c0 e3878f28 c08145c0 d1a7a393 0000076f
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788084]  c08145c0 c08145c0 e3878f28 c08145c0 d1a76967 0000076f c08145c0 ee39ba00
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788098]  e3878c90 e38ac814 e38ac818 ffffffff e35b5f30 c056f776 ee1b7110 e38ac81c
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788114] Call Trace:
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788132]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788140]  [<c056f690>] mutex_lock+0x20/0x40
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788184]  [<f08abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788197]  [<c0157a7e>] run_workqueue+0x6e/0x140
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788224]  [<f08abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788236]  [<c0157bd8>] worker_thread+0x88/0xe0
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788245]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788253]  [<c0157b50>] ? worker_thread+0x0/0xe0
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788260]  [<c015bf8c>] kthread+0x7c/0x90
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788267]  [<c015bf10>] ? kthread+0x0/0x90
Apr  6 09:32:57 ubuntu-desktop kernel: [ 9480.788275]  [<c0104007>] kernel_thread_helper+0x7/0x10
Apr  6 16:01:30 ubuntu-desktop kernel: [32793.826127] SysRq : Keyboard mode set to system default
Apr  6 16:01:32 ubuntu-desktop kernel: Kernel logging (proc) stopped.
Apr  6 16:01:33 ubuntu-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  6 16:01:33 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="2237" x-info="http://www.rsyslog.com"] (re)start
Apr  6 16:01:33 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 102
Apr  6 16:01:33 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Apr  6 16:01:33 ubuntu-desktop kernel: 6>[32795.665832] SysRq : Terminate All Tasks
Apr  6 16:01:33 ubuntu-desktop kernel: [32796.051737] udev: starting version 147
Apr  6 16:01:33 ubuntu-desktop kernel: [32796.083208] b44: eth0: powering down PHY
Apr  6 16:01:34 ubuntu-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  6 16:01:34 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="2283" x-info="http://www.rsyslog.com"] (re)start
Apr  6 16:01:34 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 102
Apr  6 16:01:34 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Apr  6 16:01:34 ubuntu-desktop kernel: 6>[32797.337560] SysRq : Kill All Tasks
Apr  6 16:01:34 ubuntu-desktop kernel: [32797.690551] [drm] DAC-5: set mode 1280x1024 10
Apr  6 16:01:34 ubuntu-desktop kernel: [32797.768438] udev: starting version 147
Apr  6 16:01:36 ubuntu-desktop kernel: [32799.817146] SysRq : Emergency Sync
Apr  6 16:01:36 ubuntu-desktop kernel: [32799.819523] Emergency Sync complete
Apr  6 16:01:38 ubuntu-desktop kernel: [32801.752829] SysRq : Emergency Remount R/O
Apr  6 16:02:05 ubuntu-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  6 16:02:05 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="697" x-info="http://www.rsyslog.com"] (re)start
Apr  6 16:02:05 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 102
Apr  6 16:02:05 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] KERNEL supported cpus:
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   Intel GenuineIntel
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   AMD AuthenticAMD
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   NSC Geode by NSC
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   Centaur CentaurHauls
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe74000 (usable)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000002fe74000 - 000000002fe76000 (ACPI NVS)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000002fe76000 - 000000002fe97000 (ACPI data)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000002fe97000 - 000000002ff00000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] DMI 2.3 present.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] last_pfn = 0x2fe74 max_arch_pfn = 0x100000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] modified physical RAM map:
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000002fe74000 (usable)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 000000002fe74000 - 000000002fe76000 (ACPI NVS)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 000000002fe76000 - 000000002fe97000 (ACPI data)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 000000002fe97000 - 000000002ff00000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000002fe74000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] RAMDISK: 237ca000 - 23f16502
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: RSDP 000feb80 00014 (v00 DELL  )
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: RSDT 000fd22a 00034 (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: FACP 000fd25e 00074 (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: DSDT fffcc0f1 02404 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: FACS 2fe74000 00040
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: SSDT fffce632 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: APIC 000fd2d2 0006C (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: BOOT 000fd33e 00028 (v01 DELL    2400    00000007 ASL  00000061)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] 766MB LOWMEM available.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   mapped low ram: 0 - 2fe74000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   low ram: 0 - 2fe74000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 2fe74000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000dfd0
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fe74000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #4 [00237ca000 - 0023f16502]          RAMDISK ==> [00237ca000 - 0023f16502]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #6 [00008a9000 - 00008ac1c4]              BRK ==> [00008a9000 - 00008ac1c4]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   #8 [0000008000 - 000000e000]          BOOTMAP ==> [0000008000 - 000000e000]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] fe710
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Zone PFN ranges:
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0002fe74
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]   HighMem  0x0002fe74 -> 0x0002fe74
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Movable zone start PFN for each node
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x000000a0
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0002fe74
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Using APIC driver default
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Allocating PCI resources starting at 2ff00000 (gap: 2ff00000:ced00000)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages at c1604000, static data 35612 bytes
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194579
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=3b668ef7-e422-4a2e-bb76-5639ae3dccfe ro quiet splash
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Initializing CPU#0
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] allocated 3924240 bytes of page_cgroup
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Memory: 757780k/784848k available (4565k kernel code, 26380k reserved, 2143k data, 540k init, 0k highmem)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] virtual kernel memory layout:
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     vmalloc : 0xf0674000 - 0xff7fe000   ( 241 MB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xefe74000   ( 766 MB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.000000] Detected 2392.434 MHz processor.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.001491] Console: colour VGA+ 80x25
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.001499] console [tty0] enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.86 BogoMIPS (lpj=9569736)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004055] Security Framework initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004095] AppArmor: AppArmor initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004113] Mount-cache hash table entries: 512
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004409] Initializing cgroup subsys ns
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004423] Initializing cgroup subsys cpuacct
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004433] Initializing cgroup subsys memory
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004447] Initializing cgroup subsys freezer
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004452] Initializing cgroup subsys net_cls
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004488] CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004495] CPU: L2 cache: 128K
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004499] CPU: Hyper-Threading is disabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004507] mce: CPU supports 4 MCE banks
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004525] CPU0: Thermal monitoring enabled (TM1)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004545] Performance Counters: no PMU driver, software counters only.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.004558] Checking 'hlt' instruction... OK.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.021096] SMP alternatives: switching to UP code
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.032026] ACPI: Core revision 20090521
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.069365] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.109067] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] Brought up 1 CPUs
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] Total of 1 processors activated (4784.86 BogoMIPS).
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] Booting paravirtualized kernel on bare hardware
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] regulator: core version 0.5
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] Time: 16:01:56  Date: 04/06/10
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] NET: Registered protocol family 16
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] EISA bus registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] ACPI: bus type pci registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112001] PCI: Using configuration type 1 for base access
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.112670] bio: create slab <bio-0> at 0
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.143599] ACPI: Interpreter enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.143616] ACPI: (supports S0 S1 S3 S4 S5)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.143672] ACPI: Using IOAPIC for interrupt routing
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.179773] ACPI: No dock devices found.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.181419] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182047] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182055] pci 0000:00:1d.7: PME# disabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182119] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182122] * this clock source is slow. If you are sure your timer does not have
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182124] * this bug, please use "acpi_pm_good" to disable the workaround
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182178] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182184] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182462] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182468] pci 0000:00:1f.5: PME# disabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182590] pci 0000:01:05.0: PME# supported from D3hot D3cold
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182597] pci 0000:01:05.0: PME# disabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182703] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182710] pci 0000:01:09.0: PME# disabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.182748] pci 0000:00:1e.0: transparent bridge
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.350460] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.350857] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.351250] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.351638] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.352193] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.352581] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.352970] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.353364] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.353832] SCSI subsystem initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.354274] usbcore: registered new interface driver usbfs
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.354329] usbcore: registered new interface driver hub
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.354446] usbcore: registered new device driver usb
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.354866] ACPI: WMI: Mapper loaded
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.354871] PCI: Using ACPI for IRQ routing
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355162] Bluetooth: Core ver 2.15
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355317] NET: Registered protocol family 31
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355322] Bluetooth: HCI device and connection manager initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355327] Bluetooth: HCI socket layer initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355332] NetLabel: Initializing
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355335] NetLabel:  domain hash size = 128
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355338] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.355366] NetLabel:  unlabeled traffic allowed by default
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.358470] pnp: PnP ACPI init
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.358515] ACPI: bus type pnp registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.381929] pnp 00:09: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.381938] pnp 00:09: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382831] pnp: PnP ACPI: found 10 devices
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382838] ACPI: ACPI bus type pnp unregistered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382846] PnPBIOS: Disabled by ACPI PNP
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382876] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382882] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382888] system 00:00: iomem range 0x1000000-0x2fe73fff could not be reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382893] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382900] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382905] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382911] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382917] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382922] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.382943] system 00:09: ioport range 0xc00-0xc7f has been reserved
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.417856] AppArmor: AppArmor Filesystem Enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.417918] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.417924] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.417933] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.417940] pci 0000:00:1e.0:   PREFETCH window: 0x30000000-0x300fffff
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.418059] NET: Registered protocol family 2
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.418235] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.418898] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.420588] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.421501] TCP: Hash tables configured (established 131072 bind 65536)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.421512] TCP reno registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.421792] NET: Registered protocol family 1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.421915] Trying to unpack rootfs image as initramfs...
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.761627] Freeing initrd memory: 7473k freed
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.777056] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.777063] Simple Boot Flag at 0x7a set to 0x1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.777236] cpufreq-nforce2: No nForce2 chipset.
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.777301] Scanning for low memory corruption every 60 seconds
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.777526] audit: initializing netlink socket (disabled)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.777558] type=2000 audit(1270569715.775:1): initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.787307] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.789696] VFS: Disk quotas dquot_6.5.2
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.789833] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.791040] fuse init (API version 7.12)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.791248] msgmni has been set to 1495
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.791878] alg: No test for stdrng (krng)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.791928] io scheduler noop registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.791932] io scheduler anticipatory registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.791936] io scheduler deadline registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792113] io scheduler cfq registered (default)
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792406] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792457] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792698] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792707] ACPI: Power Button [PWRF]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792804] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.792816] ACPI: Power Button [VBTN]
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.793303] processor LNXCPU:00: registered as cooling_device0
Apr  6 16:02:05 ubuntu-desktop kernel: [    0.820231] isapnp: Scanning for PnP cards...
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.174223] isapnp: No Plug & Play device found
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.177241] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.177417] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.178015] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.180408] brd: module loaded
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.181605] loop: module loaded
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.181835] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.182123] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.182418] scsi0 : ata_piix
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.182686] scsi1 : ata_piix
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.182785] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.182791] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.184810] Fixed MDIO Bus: probed
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.184893] PPP generic driver version 2.4.2
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.185159] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.185242] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.185281] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.185446] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.189398] ehci_hcd 0000:00:1d.7: debug port 1
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.189835] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204213] usb usb1: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204297] hub 1-0:1.0: USB hub found
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204323] hub 1-0:1.0: 6 ports detected
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204480] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204531] uhci_hcd: USB Universal Host Controller Interface driver
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204646] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204670] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204786] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.204844] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205037] usb usb2: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205111] hub 2-0:1.0: USB hub found
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205139] hub 2-0:1.0: 2 ports detected
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205293] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205316] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205427] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205484] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205685] usb usb3: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205761] hub 3-0:1.0: USB hub found
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205789] hub 3-0:1.0: 2 ports detected
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205918] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.205944] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.206053] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.206111] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.206328] usb usb4: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.206401] hub 4-0:1.0: USB hub found
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.206429] hub 4-0:1.0: 2 ports detected
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.206694] PNP: No PS/2 controller found. Probing ports directly.
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.209726] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.209741] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.209926] mice: PS/2 mouse device common for all mice
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.210167] rtc_cmos 00:05: RTC can wake from S4
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.210269] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.210308] rtc0: alarms up to one day, 242 bytes nvram
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.210566] device-mapper: uevent: version 1.0.3
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.210871] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.211172] device-mapper: multipath: version 1.1.0 loaded
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.211179] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.211552] EISA: Probing bus 0 at eisa.0
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.211595] EISA: Detected 0 cards.
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.211782] cpuidle: using governor ladder
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.211787] cpuidle: using governor menu
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.212686] TCP cubic registered
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.212999] NET: Registered protocol family 10
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.213854] lo: Disabled Privacy Extensions
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214301] NET: Registered protocol family 17
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214368] Bluetooth: L2CAP ver 2.13
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214372] Bluetooth: L2CAP socket layer initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214377] Bluetooth: SCO (Voice Link) ver 0.6
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214381] Bluetooth: SCO socket layer initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214512] Bluetooth: RFCOMM TTY layer initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214521] Bluetooth: RFCOMM socket layer initialized
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214525] Bluetooth: RFCOMM ver 1.11
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214618] Using IPI No-Shortcut mode
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.214870] registered taskstats version 1
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.215081]   Magic number: 6:96:34
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.215202] rtc_cmos 00:05: setting system clock to 2010-04-06 16:01:57 UTC (1270569717)
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.215209] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.215213] EDD information not available.
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.368326] ata2.00: ATAPI: TSST CD-RW/DVD-ROM TSH492B, TB06, max UDMA/33
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.400444] ata2.00: configured for UDMA/33
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.408600] ata1.00: ATA-6: ST380011A, 8.16, max UDMA/100
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.408607] ata1.00: 156250000 sectors, multi 8: LBA48 
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.424441] ata1.00: configured for UDMA/100
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.424699] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.16 PQ: 0 ANSI: 5
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.424993] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.425166] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.425372] sd 0:0:0:0: [sda] Write Protect is off
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.425483] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.426000]  sda:
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.426875] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSH492B TB06 PQ: 0 ANSI: 5
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.429457] sr0: scsi3-mmc drive: 5x/48x writer cd/rw xa/form2 cdda tray
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.429466] Uniform CD-ROM driver Revision: 3.20
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.429802] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.446298]  sda1 sda2 < sda5 sda6 >
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.489125] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.489162] Freeing unused kernel memory: 540k freed
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.490173] Write protecting the kernel text: 4568k
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.490215] Write protecting the kernel read-only data: 1836k
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.576092] usb 1-3: new high speed USB device using ehci_hcd and address 3
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.868545] Linux agpgart interface v0.103
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.874165] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.874335] agpgart-intel 0000:00:00.0: detected 892K stolen memory
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.876944] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
Apr  6 16:02:05 ubuntu-desktop kernel: [    1.909584] usb 1-3: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.186677] [drm] Initialized drm 1.1.0 20060810
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.205107] usb 2-2: new low speed USB device using uhci_hcd and address 2
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.232321] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.239825] Floppy drive(s): fd0 is 1.44M
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.254760] FDC 0 is a post-1991 82077
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.267372] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.433719] [drm] fb0: inteldrmfb frame buffer device
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.433740] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.436216] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.436269] b44.c:v2.0
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.524688] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:43:7f:05:03
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.554945] [drm] DAC-5: set mode 1280x1024 10
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.565275] Console: switching to colour frame buffer device 160x64
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.565537] usb 2-2: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.591347] usbcore: registered new interface driver hiddev
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.606301] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.606525] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.0-2/input0
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.606571] usbcore: registered new interface driver usbhid
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.606580] usbhid: v2.6:USB HID core driver
Apr  6 16:02:05 ubuntu-desktop kernel: [    2.808055] usb 3-2: new low speed USB device using uhci_hcd and address 2
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.008284] usb 3-2: configuration #1 chosen from 1 choice
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.047084] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.047362] generic-usb 0003:093A:2510.0002: input,hidraw1: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-2/input0
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.348697] PM: Starting manual resume from disk
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.386175] EXT4-fs (sda5): barriers enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.404107] kjournald2 starting: pid 314, dev sda5:8, commit interval 5 seconds
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.404158] EXT4-fs (sda5): delayed allocation enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.404165] EXT4-fs: file extents enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.408353] EXT4-fs: mballoc enabled
Apr  6 16:02:05 ubuntu-desktop kernel: [    3.408399] EXT4-fs (sda5): mounted filesystem with ordered data mode
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.056401] type=1505 audit(1270569720.340:2): operation="profile_load" pid=337 name=/usr/share/gdm/guest-session/Xsession
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.062435] type=1505 audit(1270569720.344:3): operation="profile_load" pid=338 name=/sbin/dhclient3
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.063230] type=1505 audit(1270569720.344:4): operation="profile_load" pid=338 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.063695] type=1505 audit(1270569720.344:5): operation="profile_load" pid=338 name=/usr/lib/connman/scripts/dhclient-script
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.109590] type=1505 audit(1270569720.392:6): operation="profile_load" pid=339 name=/usr/bin/evince
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.121867] type=1505 audit(1270569720.404:7): operation="profile_load" pid=339 name=/usr/bin/evince-previewer
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.129278] type=1505 audit(1270569720.412:8): operation="profile_load" pid=339 name=/usr/bin/evince-thumbnailer
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.149867] type=1505 audit(1270569720.432:9): operation="profile_load" pid=341 name=/usr/lib/cups/backend/cups-pdf
Apr  6 16:02:05 ubuntu-desktop kernel: [    4.150882] type=1505 audit(1270569720.432:10): operation="profile_load" pid=341 name=/usr/sbin/cupsd
Apr  6 16:02:05 ubuntu-desktop kernel: [    5.363101] Adding 1285160k swap on /dev/sda6.  Priority:-1 extents:1 across:1285160k 
Apr  6 16:02:05 ubuntu-desktop kernel: [    5.773607] EXT4-fs (sda5): internal journal on sda5:8
Apr  6 16:02:05 ubuntu-desktop kernel: [    5.977700] udev: starting version 147
Apr  6 16:02:05 ubuntu-desktop kernel: [    7.705928] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  6 16:02:05 ubuntu-desktop kernel: [    7.882983] cfg80211: Calling CRDA to update world regulatory domain
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.346909] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.693337] __ratelimit: 3 callbacks suppressed
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.693345] type=1505 audit(1270587724.976:12): operation="profile_replace" pid=649 name=/usr/share/gdm/guest-session/Xsession
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.699215] type=1505 audit(1270587724.980:13): operation="profile_replace" pid=650 name=/sbin/dhclient3
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.700540] type=1505 audit(1270587724.984:14): operation="profile_replace" pid=650 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.701020] type=1505 audit(1270587724.984:15): operation="profile_replace" pid=650 name=/usr/lib/connman/scripts/dhclient-script
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.723329] type=1505 audit(1270587725.004:16): operation="profile_replace" pid=651 name=/usr/bin/evince
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.738160] type=1505 audit(1270587725.020:17): operation="profile_replace" pid=651 name=/usr/bin/evince-previewer
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.745792] type=1505 audit(1270587725.028:18): operation="profile_replace" pid=651 name=/usr/bin/evince-thumbnailer
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.761495] type=1505 audit(1270587725.044:19): operation="profile_replace" pid=653 name=/usr/lib/cups/backend/cups-pdf
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.762537] type=1505 audit(1270587725.044:20): operation="profile_replace" pid=653 name=/usr/sbin/cupsd
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.768240] type=1505 audit(1270587725.052:21): operation="profile_replace" pid=654 name=/usr/sbin/tcpdump
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.780974] intel8x0_measure_ac97_clock: measured 55255 usecs (2662 samples)
Apr  6 16:02:05 ubuntu-desktop kernel: [    8.780981] intel8x0: clocking to 48000
Apr  6 16:02:06 ubuntu-desktop kernel: [    9.958144] parport_pc 00:08: reported by Plug and Play ACPI
Apr  6 16:02:06 ubuntu-desktop kernel: [    9.958214] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Apr  6 16:02:06 ubuntu-desktop kernel: [    9.968531] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  6 16:02:06 ubuntu-desktop kernel: [    9.979645] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.012635] intel_rng: FWH not detected
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.013471] lp: driver loaded but no devices found
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.048335] lp0: using parport0 (interrupt-driven).
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.083730] ppdev: user-space parallel port driver
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.092877] dell-wmi: No known WMI GUID found
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.513275] Registered led device: rt73usb-phy0::radio
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.513324] Registered led device: rt73usb-phy0::assoc
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.513372] Registered led device: rt73usb-phy0::quality
Apr  6 16:02:06 ubuntu-desktop kernel: [   10.514567] usbcore: registered new interface driver rt73usb
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504271] cfg80211: World regulatory domain updated:
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504280] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504286] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504291] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504296] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504301] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  6 16:02:07 ubuntu-desktop kernel: [   11.504306] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  6 16:02:12 ubuntu-desktop kernel: [   16.464391] rt73usb 1-3:1.0: firmware: requesting rt73.bin
Apr  6 16:02:13 ubuntu-desktop kernel: [   17.061666] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  6 16:02:13 ubuntu-desktop kernel: [   17.076197] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  6 16:02:29 ubuntu-desktop pulseaudio[1302]: ratelimit.c: 1 events suppressed
Apr  6 16:02:40 ubuntu-desktop pulseaudio[1390]: ratelimit.c: 3 events suppressed
Apr  6 16:02:47 ubuntu-desktop pulseaudio[1390]: ratelimit.c: 3 events suppressed
Apr  6 16:02:47 ubuntu-desktop kernel: [   50.913904] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  6 16:26:12 ubuntu-desktop pulseaudio[1390]: ratelimit.c: 2 events suppressed
```




If you need syslog, let me know

---

### Post by RJ12 on 2010-04-06
Anyone

---

### Post by djoxyk on 2010-04-06
you have these lines in log:

> Apr  6 16:01:36 ubuntu-desktop kernel: [32799.817146] SysRq : Emergency Sync
Apr  6 16:01:36 ubuntu-desktop kernel: [32799.819523] Emergency Sync complete
Apr  6 16:01:38 ubuntu-desktop kernel: [32801.752829] SysRq : Emergency Remount R/O

are you doing background backups or something? have you checked your CPU and memory load at the time it start to freeze?

---

### Post by RJ12 on 2010-04-06
Oh, when it freezes I use the Alt+SysRq+R+E+I+S+U+B to prevent damage to the Filesystem. I can't check the CPU because its frozen. So thats where the emergency sync and stuff came from.

---

