---
title: "Ubunu Slow-Boot Process? Please help!"
date: 2010-04-12
forum: General Help
---

### Post by rocket16 on 2010-04-12
Hello all. I recently install Ubuntu-studio Desktop and some other packages. And, I upgraded my System. But since then, the Grub has started to display (I have only 9.10 installed, using the entire Disk). Also, unless I select the entry, Grub does not automatically start. The startup takes nearly 1.5 minutes. And, the Login screen, after the installation of Ubuntu Studio GDM, is much slower. I removed the Ubuntu-studio GDM package, still it takes about 20 seconds to allow me to enter Username and password. Any idea?

```
Apr 11 14:53:52 anirban-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="800" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 11 15:02:12 anirban-laptop kernel: [ 3433.989079] ata4: lost interrupt (Status 0x58)
Apr 11 15:02:12 anirban-laptop kernel: [ 3434.105754] ata4: soft resetting link
Apr 11 15:02:12 anirban-laptop kernel: [ 3434.332328] ata4.00: configured for MWDMA2
Apr 11 15:02:12 anirban-laptop kernel: [ 3434.347778] ata4: EH complete
Apr 11 15:16:05 anirban-laptop kernel: [ 4267.009013] ata4: lost interrupt (Status 0x58)
Apr 11 15:16:05 anirban-laptop kernel: [ 4267.125752] ata4: soft resetting link
Apr 11 15:16:05 anirban-laptop kernel: [ 4267.352331] ata4.00: configured for MWDMA2
Apr 11 15:16:05 anirban-laptop kernel: [ 4267.367740] ata4: EH complete
Apr 11 17:34:07 anirban-laptop pppd[1937]: Terminating on signal 15
Apr 11 17:34:24 anirban-laptop kernel: Kernel logging (proc) stopped.
Apr 11 19:31:38 anirban-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr 11 19:31:38 anirban-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="819" x-info="http://www.rsyslog.com"] (re)start
Apr 11 19:31:38 anirban-laptop rsyslogd: rsyslogd's groupid changed to 102
Apr 11 19:31:38 anirban-laptop rsyslogd: rsyslogd's userid changed to 101
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] KERNEL supported cpus:
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   Intel GenuineIntel
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   AMD AuthenticAMD
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   NSC Geode by NSC
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   Centaur CentaurHauls
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7b0000 (usable)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7b0000 - 000000001f7c5400 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7c5400 - 000000001f7e7fb8 (ACPI NVS)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7e7fb8 - 0000000020000000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9a000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] DMI 2.4 present.
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] last_pfn = 0x1f7b0 max_arch_pfn = 0x100000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] modified physical RAM map:
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000001f7b0000 (usable)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 000000001f7b0000 - 000000001f7c5400 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 000000001f7c5400 - 000000001f7e7fb8 (ACPI NVS)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 000000001f7e7fb8 - 0000000020000000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed9a000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f7b0000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] RAMDISK: 172ba000 - 17a03e54
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: RSDP 000fc600 00024 (v02 HP    )
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: XSDT 1f7c81c8 0007C (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: FACP 1f7c8084 000F4 (v04 HP     30C0     00000003 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: DSDT 1f7c84cc 12C10 (v01 HP       nc75xx 00010000 MSFT 03000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: FACS 1f7e7d80 00040
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: SLIC 1f7c8244 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: HPET 1f7c83bc 00038 (v01 HP     30C0     00000001 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: APIC 1f7c83f4 00068 (v01 HP     30C0     00000001 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: MCFG 1f7c845c 0003C (v01 HP     30C0     00000001 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: TCPA 1f7c8498 00032 (v02 HP     30C0     00000001 HP   00000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7db0dc 00059 (v01 HP       HPQNLP 00000001 MSFT 03000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7db135 00328 (v01 HP       HPQSAT 00000001 MSFT 03000001)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbca1 0025F (v01 HP      Cpu0Tst 00003000 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbf00 000A6 (v01 HP      Cpu1Tst 00003000 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbfa6 004D7 (v01 HP        CpuPm 00003000 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] 503MB LOWMEM available.
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   mapped low ram: 0 - 1f7b0000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   low ram: 0 - 1f7b0000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 1f7b0000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bef8
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f7b0000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #4 [00172ba000 - 0017a03e54]          RAMDISK ==> [00172ba000 - 0017a03e54]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #6 [00008ae000 - 00008b10f4]              BRK ==> [00008ae000 - 00008b10f4]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f7b0
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]   HighMem  0x0001f7b0 -> 0x0001f7b0
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0001f7b0
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Using APIC driver default
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127835
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=f2551907-f2d8-4fca-9c65-db29c6645b41 ro quiet quiet splash
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Initializing CPU#0
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] allocated 2578880 bytes of page_cgroup
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Memory: 492544k/515776k available (4578k kernel code, 22444k reserved, 2146k data, 540k init, 0k highmem)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] virtual kernel memory layout:
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     vmalloc : 0xdffb0000 - 0xff7fe000   ( 504 MB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf7b0000   ( 503 MB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Extended CMOS year: 2000
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Apr 11 19:31:38 anirban-laptop kernel: [    0.000000] Detected 1795.687 MHz processor.
Apr 11 19:31:38 anirban-laptop kernel: [    0.001328] Console: colour VGA+ 80x25
Apr 11 19:31:38 anirban-laptop kernel: [    0.001332] console [tty0] enabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.001515] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 11 19:31:38 anirban-laptop kernel: [    0.001522] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.37 BogoMIPS (lpj=7182748)
Apr 11 19:31:38 anirban-laptop kernel: [    0.001537] Security Framework initialized
Apr 11 19:31:38 anirban-laptop kernel: [    0.001552] AppArmor: AppArmor initialized
Apr 11 19:31:38 anirban-laptop kernel: [    0.001558] Mount-cache hash table entries: 512
Apr 11 19:31:38 anirban-laptop kernel: [    0.001664] Initializing cgroup subsys ns
Apr 11 19:31:38 anirban-laptop kernel: [    0.001668] Initializing cgroup subsys cpuacct
Apr 11 19:31:38 anirban-laptop kernel: [    0.001672] Initializing cgroup subsys memory
Apr 11 19:31:38 anirban-laptop kernel: [    0.001678] Initializing cgroup subsys freezer
Apr 11 19:31:38 anirban-laptop kernel: [    0.001680] Initializing cgroup subsys net_cls
Apr 11 19:31:38 anirban-laptop kernel: [    0.001692] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 11 19:31:38 anirban-laptop kernel: [    0.001695] CPU: L2 cache: 2048K
Apr 11 19:31:38 anirban-laptop kernel: [    0.001698] CPU: Physical Processor ID: 0
Apr 11 19:31:38 anirban-laptop kernel: [    0.001699] CPU: Processor Core ID: 0
Apr 11 19:31:38 anirban-laptop kernel: [    0.001703] mce: CPU supports 6 MCE banks
Apr 11 19:31:38 anirban-laptop kernel: [    0.001712] using mwait in idle threads.
Apr 11 19:31:38 anirban-laptop kernel: [    0.001716] Performance Counters: Core2 events, Intel PMU driver.
Apr 11 19:31:38 anirban-laptop kernel: [    0.001733] ... version:                 2
Apr 11 19:31:38 anirban-laptop kernel: [    0.001734] ... bit width:               40
Apr 11 19:31:38 anirban-laptop kernel: [    0.001736] ... generic counters:        2
Apr 11 19:31:38 anirban-laptop kernel: [    0.001738] ... value mask:              000000ffffffffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.001740] ... max period:              000000007fffffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.001742] ... fixed-purpose counters:  3
Apr 11 19:31:38 anirban-laptop kernel: [    0.001743] ... counter mask:            0000000700000003
Apr 11 19:31:38 anirban-laptop kernel: [    0.001747] Checking 'hlt' instruction... OK.
Apr 11 19:31:38 anirban-laptop kernel: [    0.018522] ACPI: Core revision 20090521
Apr 11 19:31:38 anirban-laptop kernel: [    0.044437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 11 19:31:38 anirban-laptop kernel: [    0.084185] CPU0: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
Apr 11 19:31:38 anirban-laptop kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] Initializing CPU#1
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3590.97 BogoMIPS (lpj=7181949)
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] mce: CPU supports 6 MCE banks
Apr 11 19:31:38 anirban-laptop kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Apr 11 19:31:38 anirban-laptop kernel: [    0.173543] CPU1: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
Apr 11 19:31:38 anirban-laptop kernel: [    0.173561] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 11 19:31:38 anirban-laptop kernel: [    0.176026] Brought up 2 CPUs
Apr 11 19:31:38 anirban-laptop kernel: [    0.176029] Total of 2 processors activated (7182.34 BogoMIPS).
Apr 11 19:31:38 anirban-laptop kernel: [    0.176184] Booting paravirtualized kernel on bare hardware
Apr 11 19:31:38 anirban-laptop kernel: [    0.176232] regulator: core version 0.5
Apr 11 19:31:38 anirban-laptop kernel: [    0.176232] Time: 14:01:23  Date: 04/11/10
Apr 11 19:31:38 anirban-laptop kernel: [    0.176232] NET: Registered protocol family 16
Apr 11 19:31:38 anirban-laptop kernel: [    0.176236] EISA bus registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.176246] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Apr 11 19:31:38 anirban-laptop kernel: [    0.176249] ACPI: bus type pci registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.176327] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Apr 11 19:31:38 anirban-laptop kernel: [    0.176330] PCI: Not using MMCONFIG.
Apr 11 19:31:38 anirban-laptop kernel: [    0.177436] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=40
Apr 11 19:31:38 anirban-laptop kernel: [    0.177438] PCI: Using configuration type 1 for base access
Apr 11 19:31:38 anirban-laptop kernel: [    0.180761] bio: create slab <bio-0> at 0
Apr 11 19:31:38 anirban-laptop kernel: [    0.207336] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 11 19:31:38 anirban-laptop kernel: [    0.236292] ACPI: Interpreter enabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.236300] ACPI: (supports S0 S3 S4 S5)
Apr 11 19:31:38 anirban-laptop kernel: [    0.236320] ACPI: Using IOAPIC for interrupt routing
Apr 11 19:31:38 anirban-laptop kernel: [    0.236380] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Apr 11 19:31:38 anirban-laptop kernel: [    0.242598] PCI: MCFG area at f8000000 reserved in ACPI motherboard resources
Apr 11 19:31:38 anirban-laptop kernel: [    0.242601] PCI: Using MMCONFIG for extended config space
Apr 11 19:31:38 anirban-laptop kernel: [    0.253601] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Apr 11 19:31:38 anirban-laptop kernel: [    0.253604] ACPI: EC: driver started in interrupt mode
Apr 11 19:31:38 anirban-laptop kernel: [    0.253688] ACPI: Power Resource [C29B] (on)
Apr 11 19:31:38 anirban-laptop kernel: [    0.253742] ACPI: Power Resource [C1C5] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.253847] ACPI: Power Resource [C3B7] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.253946] ACPI: Power Resource [C3B8] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.254043] ACPI: Power Resource [C3B9] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.254140] ACPI: Power Resource [C3BA] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.254237] ACPI: Power Resource [C3BB] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.254653] ACPI: No dock devices found.
Apr 11 19:31:38 anirban-laptop kernel: [    0.258936] ACPI: PCI Root Bridge [C003] (0000:00)
Apr 11 19:31:38 anirban-laptop kernel: [    0.259847] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.259857] pci 0000:00:1a.7: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.260148] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.260158] pci 0000:00:1b.0: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.260376] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.260385] pci 0000:00:1c.0: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.260607] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.260615] pci 0000:00:1c.1: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.260832] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.260842] pci 0000:00:1c.2: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.261068] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.261078] pci 0000:00:1c.4: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.261889] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.261899] pci 0000:00:1d.7: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.262269] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 11 19:31:38 anirban-laptop kernel: [    0.262276] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
Apr 11 19:31:38 anirban-laptop kernel: [    0.262283] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 007f)
Apr 11 19:31:38 anirban-laptop kernel: [    0.262297] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 02e8 (mask 0007)
Apr 11 19:31:38 anirban-laptop kernel: [    0.262852] pci 0000:00:1f.2: PME# supported from D3hot
Apr 11 19:31:38 anirban-laptop kernel: [    0.262862] pci 0000:00:1f.2: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.263534] pci 0000:10:00.0: PME# supported from D0 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.263547] pci 0000:10:00.0: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.263937] pci 0000:18:00.0: PME# supported from D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.263944] pci 0000:18:00.0: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.264437] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 11 19:31:38 anirban-laptop kernel: [    0.264447] pci 0000:02:04.0: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.264595] pci 0000:00:1e.0: transparent bridge
Apr 11 19:31:38 anirban-laptop kernel: [    0.310138] ACPI: PCI Interrupt Link [C12D] (IRQs 10 11) *5
Apr 11 19:31:38 anirban-laptop kernel: [    0.310367] ACPI: PCI Interrupt Link [C12E] (IRQs *10 11)
Apr 11 19:31:38 anirban-laptop kernel: [    0.310591] ACPI: PCI Interrupt Link [C12F] (IRQs 10 *11)
Apr 11 19:31:38 anirban-laptop kernel: [    0.310805] ACPI: PCI Interrupt Link [C130] (IRQs 10 11) *0, disabled.
Apr 11 19:31:38 anirban-laptop kernel: [    0.311029] ACPI: PCI Interrupt Link [C140] (IRQs *10 11)
Apr 11 19:31:38 anirban-laptop kernel: [    0.311251] ACPI: PCI Interrupt Link [C141] (IRQs *10 11)
Apr 11 19:31:38 anirban-laptop kernel: [    0.311465] ACPI: PCI Interrupt Link [C142] (IRQs 10 11) *0, disabled.
Apr 11 19:31:38 anirban-laptop kernel: [    0.311571] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS 20090521 pci_link-182
Apr 11 19:31:38 anirban-laptop kernel: [    0.311826] SCSI subsystem initialized
Apr 11 19:31:38 anirban-laptop kernel: [    0.312047] usbcore: registered new interface driver usbfs
Apr 11 19:31:38 anirban-laptop kernel: [    0.312047] usbcore: registered new interface driver hub
Apr 11 19:31:38 anirban-laptop kernel: [    0.312047] usbcore: registered new device driver usb
Apr 11 19:31:38 anirban-laptop kernel: [    0.312132] ACPI: WMI: Mapper loaded
Apr 11 19:31:38 anirban-laptop kernel: [    0.312134] PCI: Using ACPI for IRQ routing
Apr 11 19:31:38 anirban-laptop kernel: [    0.324008] Bluetooth: Core ver 2.15
Apr 11 19:31:38 anirban-laptop kernel: [    0.324014] NET: Registered protocol family 31
Apr 11 19:31:38 anirban-laptop kernel: [    0.324015] Bluetooth: HCI device and connection manager initialized
Apr 11 19:31:38 anirban-laptop kernel: [    0.324019] Bluetooth: HCI socket layer initialized
Apr 11 19:31:38 anirban-laptop kernel: [    0.324021] NetLabel: Initializing
Apr 11 19:31:38 anirban-laptop kernel: [    0.324023] NetLabel:  domain hash size = 128
Apr 11 19:31:38 anirban-laptop kernel: [    0.324024] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 11 19:31:38 anirban-laptop kernel: [    0.324040] NetLabel:  unlabeled traffic allowed by default
Apr 11 19:31:38 anirban-laptop kernel: [    0.324079] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 11 19:31:38 anirban-laptop kernel: [    0.324085] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr 11 19:31:38 anirban-laptop kernel: [    0.341589] pnp: PnP ACPI init
Apr 11 19:31:38 anirban-laptop kernel: [    0.341599] ACPI: bus type pnp registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.351125] pnp: PnP ACPI: found 12 devices
Apr 11 19:31:38 anirban-laptop kernel: [    0.351127] ACPI: ACPI bus type pnp unregistered
Apr 11 19:31:38 anirban-laptop kernel: [    0.351132] PnPBIOS: Disabled by ACPI PNP
Apr 11 19:31:38 anirban-laptop kernel: [    0.351143] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351147] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351150] system 00:00: iomem range 0x100000-0x1f7fffff could not be reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351161] system 00:09: ioport range 0x500-0x57f has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351165] system 00:09: ioport range 0x800-0x80f has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351168] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351172] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351178] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351181] system 00:0a: ioport range 0x1000-0x107f has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351184] system 00:0a: ioport range 0x1100-0x113f has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351187] system 00:0a: ioport range 0x1200-0x121f has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351191] system 00:0a: iomem range 0xf8000000-0xfbffffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351194] system 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351197] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351201] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351204] system 00:0a: iomem range 0xfed90000-0xfed99fff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351210] system 00:0b: iomem range 0xcee00-0xcffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351213] system 00:0b: iomem range 0xd2a00-0xd3fff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351217] system 00:0b: iomem range 0xfeda0000-0xfedbffff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.351222] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 11 19:31:38 anirban-laptop kernel: [    0.385923] AppArmor: AppArmor Filesystem Enabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386070] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:08
Apr 11 19:31:38 anirban-laptop kernel: [    0.386072] pci 0000:00:1c.0:   IO window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386085] pci 0000:00:1c.0:   MEM window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386095] pci 0000:00:1c.0:   PREFETCH window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386105] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:10
Apr 11 19:31:38 anirban-laptop kernel: [    0.386107] pci 0000:00:1c.1:   IO window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386121] pci 0000:00:1c.1:   MEM window: 0xe4100000-0xe41fffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386131] pci 0000:00:1c.1:   PREFETCH window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386141] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:18
Apr 11 19:31:38 anirban-laptop kernel: [    0.386143] pci 0000:00:1c.2:   IO window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386154] pci 0000:00:1c.2:   MEM window: 0xe4000000-0xe40fffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386163] pci 0000:00:1c.2:   PREFETCH window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386173] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:28
Apr 11 19:31:38 anirban-laptop kernel: [    0.386179] pci 0000:00:1c.4:   IO window: 0x2000-0x3fff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386190] pci 0000:00:1c.4:   MEM window: 0xe0000000-0xe3ffffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386200] pci 0000:00:1c.4:   PREFETCH window: disabled
Apr 11 19:31:38 anirban-laptop kernel: [    0.386212] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
Apr 11 19:31:38 anirban-laptop kernel: [    0.386215] pci 0000:02:04.0:   IO window: 0x005000-0x0050ff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386226] pci 0000:02:04.0:   IO window: 0x005400-0x0054ff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386236] pci 0000:02:04.0:   PREFETCH window: 0x20000000-0x23ffffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386247] pci 0000:02:04.0:   MEM window: 0x24000000-0x27ffffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386258] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Apr 11 19:31:38 anirban-laptop kernel: [    0.386264] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386277] pci 0000:00:1e.0:   MEM window: 0xe4200000-0xe42fffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386287] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
Apr 11 19:31:38 anirban-laptop kernel: [    0.386321] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [    0.386356] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 11 19:31:38 anirban-laptop kernel: [    0.386388] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 11 19:31:38 anirban-laptop kernel: [    0.386417] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [    0.386464] pci 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [    0.386554] NET: Registered protocol family 2
Apr 11 19:31:38 anirban-laptop kernel: [    0.386662] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.386971] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.387045] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.387107] TCP: Hash tables configured (established 16384 bind 16384)
Apr 11 19:31:38 anirban-laptop kernel: [    0.387110] TCP reno registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.387179] NET: Registered protocol family 1
Apr 11 19:31:38 anirban-laptop kernel: [    0.387240] Trying to unpack rootfs image as initramfs...
Apr 11 19:31:38 anirban-laptop kernel: [    0.592909] Freeing initrd memory: 7463k freed
Apr 11 19:31:38 anirban-laptop kernel: [    0.598386] cpufreq-nforce2: No nForce2 chipset.
Apr 11 19:31:38 anirban-laptop kernel: [    0.598418] Scanning for low memory corruption every 60 seconds
Apr 11 19:31:38 anirban-laptop kernel: [    0.598541] audit: initializing netlink socket (disabled)
Apr 11 19:31:38 anirban-laptop kernel: [    0.598560] type=2000 audit(1270994482.597:1): initialized
Apr 11 19:31:38 anirban-laptop kernel: [    0.608189] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 11 19:31:38 anirban-laptop kernel: [    0.609838] VFS: Disk quotas dquot_6.5.2
Apr 11 19:31:38 anirban-laptop kernel: [    0.609904] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 11 19:31:38 anirban-laptop kernel: [    0.610494] fuse init (API version 7.12)
Apr 11 19:31:38 anirban-laptop kernel: [    0.610588] msgmni has been set to 977
Apr 11 19:31:38 anirban-laptop kernel: [    0.610817] alg: No test for stdrng (krng)
Apr 11 19:31:38 anirban-laptop kernel: [    0.610830] io scheduler noop registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.610833] io scheduler anticipatory registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.610835] io scheduler deadline registered
Apr 11 19:31:38 anirban-laptop kernel: [    0.610883] io scheduler cfq registered (default)
Apr 11 19:31:38 anirban-laptop kernel: [    0.612680] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 11 19:31:38 anirban-laptop kernel: [    0.612793] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 11 19:31:38 anirban-laptop kernel: [    0.618280] ACPI: AC Adapter [C239] (off-line)
Apr 11 19:31:38 anirban-laptop kernel: [    0.618349] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr 11 19:31:38 anirban-laptop kernel: [    0.618353] ACPI: Power Button [PWRF]
Apr 11 19:31:38 anirban-laptop kernel: [    0.618432] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Apr 11 19:31:38 anirban-laptop kernel: [    0.618435] ACPI: Sleep Button [C2BF]
Apr 11 19:31:38 anirban-laptop kernel: [    0.618486] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Apr 11 19:31:38 anirban-laptop kernel: [    0.618557] ACPI: Lid Switch [C153]
Apr 11 19:31:38 anirban-laptop kernel: [    0.618806] fan PNP0C0B:00: registered as cooling_device0
Apr 11 19:31:38 anirban-laptop kernel: [    0.618812] ACPI: Fan [C3BC] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.619011] fan PNP0C0B:01: registered as cooling_device1
Apr 11 19:31:38 anirban-laptop kernel: [    0.619017] ACPI: Fan [C3BD] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.619214] fan PNP0C0B:02: registered as cooling_device2
Apr 11 19:31:38 anirban-laptop kernel: [    0.619220] ACPI: Fan [C3BE] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.619418] fan PNP0C0B:03: registered as cooling_device3
Apr 11 19:31:38 anirban-laptop kernel: [    0.619424] ACPI: Fan [C3BF] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.619625] fan PNP0C0B:04: registered as cooling_device4
Apr 11 19:31:38 anirban-laptop kernel: [    0.619631] ACPI: Fan [C3C0] (off)
Apr 11 19:31:38 anirban-laptop kernel: [    0.620327] ACPI: SSDT 1f7db525 0023D (v01 HP      Cpu0Ist 00003000 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.620954] ACPI: SSDT 1f7db7e7 004BA (v01 HP      Cpu0Cst 00003001 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.623501] Marking TSC unstable due to TSC halts in idle
Apr 11 19:31:38 anirban-laptop kernel: [    0.623527] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 11 19:31:38 anirban-laptop kernel: [    0.623550] processor LNXCPU:00: registered as cooling_device5
Apr 11 19:31:38 anirban-laptop kernel: [    0.623554] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 11 19:31:38 anirban-laptop kernel: [    0.623914] ACPI: SSDT 1f7db45d 000C8 (v01 HP      Cpu1Ist 00003000 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.624392] ACPI: SSDT 1f7db762 00085 (v01 HP      Cpu1Cst 00003000 INTL 20060317)
Apr 11 19:31:38 anirban-laptop kernel: [    0.625494] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 11 19:31:38 anirban-laptop kernel: [    0.625516] processor LNXCPU:01: registered as cooling_device6
Apr 11 19:31:38 anirban-laptop kernel: [    0.625520] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 11 19:31:38 anirban-laptop kernel: [    0.654727] thermal LNXTHERM:01: registered as thermal_zone0
Apr 11 19:31:38 anirban-laptop kernel: [    0.654738] ACPI: Thermal Zone [TZ0] (65 C)
Apr 11 19:31:38 anirban-laptop kernel: [    0.658940] thermal LNXTHERM:02: registered as thermal_zone1
Apr 11 19:31:38 anirban-laptop kernel: [    0.658950] ACPI: Thermal Zone [TZ1] (61 C)
Apr 11 19:31:38 anirban-laptop kernel: [    0.662927] thermal LNXTHERM:03: registered as thermal_zone2
Apr 11 19:31:38 anirban-laptop kernel: [    0.662937] ACPI: Thermal Zone [TZ3] (41 C)
Apr 11 19:31:38 anirban-laptop kernel: [    0.675077] thermal LNXTHERM:04: registered as thermal_zone3
Apr 11 19:31:38 anirban-laptop kernel: [    0.675087] ACPI: Thermal Zone [TZ4] (37 C)
Apr 11 19:31:38 anirban-laptop kernel: [    0.681812] thermal LNXTHERM:05: registered as thermal_zone4
Apr 11 19:31:38 anirban-laptop kernel: [    0.681822] ACPI: Thermal Zone [TZ5] (74 C)
Apr 11 19:31:38 anirban-laptop kernel: [    0.681917] isapnp: Scanning for PnP cards...
Apr 11 19:31:38 anirban-laptop kernel: [    0.723298] ACPI: Battery Slot [C23B] (battery present)
Apr 11 19:31:38 anirban-laptop kernel: [    0.723488] ACPI: Battery Slot [C23A] (battery absent)
Apr 11 19:31:38 anirban-laptop kernel: [    1.039704] isapnp: No Plug & Play device found
Apr 11 19:31:38 anirban-laptop kernel: [    1.041036] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 11 19:31:38 anirban-laptop kernel: [    1.042528] brd: module loaded
Apr 11 19:31:38 anirban-laptop kernel: [    1.043033] loop: module loaded
Apr 11 19:31:38 anirban-laptop kernel: [    1.043112] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr 11 19:31:38 anirban-laptop kernel: [    1.043213] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 11 19:31:38 anirban-laptop kernel: [    1.043344] ahci: SSS flag set, parallel bus scan disabled
Apr 11 19:31:38 anirban-laptop kernel: [    1.043374] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
Apr 11 19:31:38 anirban-laptop kernel: [    1.043378] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
Apr 11 19:31:38 anirban-laptop kernel: [    1.043543] scsi0 : ahci
Apr 11 19:31:38 anirban-laptop kernel: [    1.043645] scsi1 : ahci
Apr 11 19:31:38 anirban-laptop kernel: [    1.043712] scsi2 : ahci
Apr 11 19:31:38 anirban-laptop kernel: [    1.043783] ata1: SATA max UDMA/133 abar m2048@0xe4509000 port 0xe4509100 irq 28
Apr 11 19:31:38 anirban-laptop kernel: [    1.043786] ata2: DUMMY
Apr 11 19:31:38 anirban-laptop kernel: [    1.043787] ata3: DUMMY
Apr 11 19:31:38 anirban-laptop kernel: [    1.043853] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [    1.044019] scsi3 : ata_piix
Apr 11 19:31:38 anirban-laptop kernel: [    1.044087] scsi4 : ata_piix
Apr 11 19:31:38 anirban-laptop kernel: [    1.044641] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x40c0 irq 14
Apr 11 19:31:38 anirban-laptop kernel: [    1.044644] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40c8 irq 15
Apr 11 19:31:38 anirban-laptop kernel: [    1.045615] Fixed MDIO Bus: probed
Apr 11 19:31:38 anirban-laptop kernel: [    1.045652] PPP generic driver version 2.4.2
Apr 11 19:31:38 anirban-laptop kernel: [    1.045745] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 11 19:31:38 anirban-laptop kernel: [    1.045770] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 11 19:31:38 anirban-laptop kernel: [    1.045792] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.045824] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr 11 19:31:38 anirban-laptop kernel: [    1.049747] ehci_hcd 0000:00:1a.7: debug port 1
Apr 11 19:31:38 anirban-laptop kernel: [    1.049778] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe4500000
Apr 11 19:31:38 anirban-laptop kernel: [    1.064032] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr 11 19:31:38 anirban-laptop kernel: [    1.064108] usb usb1: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.064138] hub 1-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.064147] hub 1-0:1.0: 4 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.064230] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 11 19:31:38 anirban-laptop kernel: [    1.064251] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.064283] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr 11 19:31:38 anirban-laptop kernel: [    1.068208] ehci_hcd 0000:00:1d.7: debug port 1
Apr 11 19:31:38 anirban-laptop kernel: [    1.068238] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe4508000
Apr 11 19:31:38 anirban-laptop kernel: [    1.084030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr 11 19:31:38 anirban-laptop kernel: [    1.084094] usb usb2: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.084125] hub 2-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.084132] hub 2-0:1.0: 6 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.084194] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 11 19:31:38 anirban-laptop kernel: [    1.084212] uhci_hcd: USB Universal Host Controller Interface driver
Apr 11 19:31:38 anirban-laptop kernel: [    1.084236] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [    1.084252] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.084286] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr 11 19:31:38 anirban-laptop kernel: [    1.084334] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004020
Apr 11 19:31:38 anirban-laptop kernel: [    1.084427] usb usb3: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.084460] hub 3-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.084467] hub 3-0:1.0: 2 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.084523] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 11 19:31:38 anirban-laptop kernel: [    1.084540] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.084569] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr 11 19:31:38 anirban-laptop kernel: [    1.084618] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00004040
Apr 11 19:31:38 anirban-laptop kernel: [    1.084704] usb usb4: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.084731] hub 4-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.084738] hub 4-0:1.0: 2 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.084791] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 11 19:31:38 anirban-laptop kernel: [    1.084808] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.084840] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Apr 11 19:31:38 anirban-laptop kernel: [    1.084880] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00004060
Apr 11 19:31:38 anirban-laptop kernel: [    1.084967] usb usb5: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.084995] hub 5-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.085002] hub 5-0:1.0: 2 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.085062] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 11 19:31:38 anirban-laptop kernel: [    1.085079] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.085111] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Apr 11 19:31:38 anirban-laptop kernel: [    1.085158] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00004080
Apr 11 19:31:38 anirban-laptop kernel: [    1.085243] usb usb6: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.085270] hub 6-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.085277] hub 6-0:1.0: 2 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.085328] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 11 19:31:38 anirban-laptop kernel: [    1.085346] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 11 19:31:38 anirban-laptop kernel: [    1.085380] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Apr 11 19:31:38 anirban-laptop kernel: [    1.085417] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000040a0
Apr 11 19:31:38 anirban-laptop kernel: [    1.085501] usb usb7: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.085529] hub 7-0:1.0: USB hub found
Apr 11 19:31:38 anirban-laptop kernel: [    1.085535] hub 7-0:1.0: 2 ports detected
Apr 11 19:31:38 anirban-laptop kernel: [    1.085645] PNP: PS/2 Controller [PNP0303:C298,PNP0f13:C299] at 0x60,0x64 irq 1,12
Apr 11 19:31:38 anirban-laptop kernel: [    1.087553] i8042.c: Detected active multiplexing controller, rev 1.1.
Apr 11 19:31:38 anirban-laptop kernel: [    1.088239] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 11 19:31:38 anirban-laptop kernel: [    1.088245] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr 11 19:31:38 anirban-laptop kernel: [    1.088248] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr 11 19:31:38 anirban-laptop kernel: [    1.088251] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr 11 19:31:38 anirban-laptop kernel: [    1.088254] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr 11 19:31:38 anirban-laptop kernel: [    1.088319] mice: PS/2 mouse device common for all mice
Apr 11 19:31:38 anirban-laptop kernel: [    1.088453] rtc_cmos 00:05: RTC can wake from S4
Apr 11 19:31:38 anirban-laptop kernel: [    1.088488] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 11 19:31:38 anirban-laptop kernel: [    1.088527] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr 11 19:31:38 anirban-laptop kernel: [    1.088632] device-mapper: uevent: version 1.0.3
Apr 11 19:31:38 anirban-laptop kernel: [    1.088739] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Apr 11 19:31:38 anirban-laptop kernel: [    1.088826] device-mapper: multipath: version 1.1.0 loaded
Apr 11 19:31:38 anirban-laptop kernel: [    1.088829] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 11 19:31:38 anirban-laptop kernel: [    1.088961] EISA: Probing bus 0 at eisa.0
Apr 11 19:31:38 anirban-laptop kernel: [    1.088970] Cannot allocate resource for EISA slot 1
Apr 11 19:31:38 anirban-laptop kernel: [    1.088973] Cannot allocate resource for EISA slot 2
Apr 11 19:31:38 anirban-laptop kernel: [    1.088975] Cannot allocate resource for EISA slot 3
Apr 11 19:31:38 anirban-laptop kernel: [    1.088977] Cannot allocate resource for EISA slot 4
Apr 11 19:31:38 anirban-laptop kernel: [    1.088980] Cannot allocate resource for EISA slot 5
Apr 11 19:31:38 anirban-laptop kernel: [    1.089015] EISA: Detected 0 cards.
Apr 11 19:31:38 anirban-laptop kernel: [    1.089210] cpuidle: using governor ladder
Apr 11 19:31:38 anirban-laptop kernel: [    1.089345] cpuidle: using governor menu
Apr 11 19:31:38 anirban-laptop kernel: [    1.089884] TCP cubic registered
Apr 11 19:31:38 anirban-laptop kernel: [    1.090055] NET: Registered protocol family 10
Apr 11 19:31:38 anirban-laptop kernel: [    1.090563] lo: Disabled Privacy Extensions
Apr 11 19:31:38 anirban-laptop kernel: [    1.090948] NET: Registered protocol family 17
Apr 11 19:31:38 anirban-laptop kernel: [    1.090966] Bluetooth: L2CAP ver 2.13
Apr 11 19:31:38 anirban-laptop kernel: [    1.090968] Bluetooth: L2CAP socket layer initialized
Apr 11 19:31:38 anirban-laptop kernel: [    1.090971] Bluetooth: SCO (Voice Link) ver 0.6
Apr 11 19:31:38 anirban-laptop kernel: [    1.090973] Bluetooth: SCO socket layer initialized
Apr 11 19:31:38 anirban-laptop kernel: [    1.091015] Bluetooth: RFCOMM TTY layer initialized
Apr 11 19:31:38 anirban-laptop kernel: [    1.091018] Bluetooth: RFCOMM socket layer initialized
Apr 11 19:31:38 anirban-laptop kernel: [    1.091020] Bluetooth: RFCOMM ver 1.11
Apr 11 19:31:38 anirban-laptop kernel: [    1.091564] Using IPI No-Shortcut mode
Apr 11 19:31:38 anirban-laptop kernel: [    1.091633] registered taskstats version 1
Apr 11 19:31:38 anirban-laptop kernel: [    1.091739]   Magic number: 6:259:30
Apr 11 19:31:38 anirban-laptop kernel: [    1.091874] rtc_cmos 00:05: setting system clock to 2010-04-11 14:01:24 UTC (1270994484)
Apr 11 19:31:38 anirban-laptop kernel: [    1.091877] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 11 19:31:38 anirban-laptop kernel: [    1.091879] EDD information not available.
Apr 11 19:31:38 anirban-laptop kernel: [    1.110007] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr 11 19:31:38 anirban-laptop kernel: [    1.224761] ata4.00: ATAPI: TSSTcorpCDW/DVD TS-L462D, HH08, max MWDMA2
Apr 11 19:31:38 anirban-laptop kernel: [    1.272404] ata4.00: configured for MWDMA2
Apr 11 19:31:38 anirban-laptop kernel: [    1.360152] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 11 19:31:38 anirban-laptop kernel: [    1.364030] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 11 19:31:38 anirban-laptop kernel: [    1.364034] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
Apr 11 19:31:38 anirban-laptop kernel: [    1.365677] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 11 19:31:38 anirban-laptop kernel: [    1.367961] ata1.00: ATA-7: ST980811AS, 3.BHD, max UDMA/100
Apr 11 19:31:38 anirban-laptop kernel: [    1.367966] ata1.00: 156301488 sectors, multi 16: LBA48 
Apr 11 19:31:38 anirban-laptop kernel: [    1.373318] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 11 19:31:38 anirban-laptop kernel: [    1.373321] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
Apr 11 19:31:38 anirban-laptop kernel: [    1.374917] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 11 19:31:38 anirban-laptop kernel: [    1.377239] ata1.00: configured for UDMA/100
Apr 11 19:31:38 anirban-laptop kernel: [    1.397624] ata1.00: configured for UDMA/100
Apr 11 19:31:38 anirban-laptop kernel: [    1.397629] ata1: EH complete
Apr 11 19:31:38 anirban-laptop kernel: [    1.397818] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
Apr 11 19:31:38 anirban-laptop kernel: [    1.397933] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 11 19:31:38 anirban-laptop kernel: [    1.397970] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Apr 11 19:31:38 anirban-laptop kernel: [    1.398014] sd 0:0:0:0: [sda] Write Protect is off
Apr 11 19:31:38 anirban-laptop kernel: [    1.398040] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 11 19:31:38 anirban-laptop kernel: [    1.398162]  sda:
Apr 11 19:31:38 anirban-laptop kernel: [    1.431741] scsi 3:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462D HH08 PQ: 0 ANSI: 5
Apr 11 19:31:38 anirban-laptop kernel: [    1.456813]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 11 19:31:38 anirban-laptop kernel: [    1.457166] Uniform CD-ROM driver Revision: 3.20
Apr 11 19:31:38 anirban-laptop kernel: [    1.457352] sr 3:0:0:0: Attached scsi generic sg1 type 5
Apr 11 19:31:38 anirban-laptop kernel: [    1.483293]  sda5 >
Apr 11 19:31:38 anirban-laptop kernel: [    1.483624] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 11 19:31:38 anirban-laptop kernel: [    1.483694] Freeing unused kernel memory: 540k freed
Apr 11 19:31:38 anirban-laptop kernel: [    1.484096] Write protecting the kernel text: 4580k
Apr 11 19:31:38 anirban-laptop kernel: [    1.484166] Write protecting the kernel read-only data: 1840k
Apr 11 19:31:38 anirban-laptop kernel: [    1.500055] Clocksource tsc unstable (delta = -256386766 ns)
Apr 11 19:31:38 anirban-laptop kernel: [    1.594466] Linux agpgart interface v0.103
Apr 11 19:31:38 anirban-laptop kernel: [    1.597132] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr 11 19:31:38 anirban-laptop kernel: [    1.597785] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr 11 19:31:38 anirban-laptop kernel: [    1.600342] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr 11 19:31:38 anirban-laptop kernel: [    1.640126] usb 6-1: new full speed USB device using uhci_hcd and address 2
Apr 11 19:31:38 anirban-laptop kernel: [    1.678021] [drm] Initialized drm 1.1.0 20060810
Apr 11 19:31:38 anirban-laptop kernel: [    1.681967] tg3.c:v3.99 (April 20, 2009)
Apr 11 19:31:38 anirban-laptop kernel: [    1.682032] tg3 0000:18:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 11 19:31:38 anirban-laptop kernel: [    1.691702] tg3 0000:18:00.0: PME# disabled
Apr 11 19:31:38 anirban-laptop kernel: [    1.712315] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [    1.817311] usb 6-1: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    1.825386] Initializing USB Mass Storage driver...
Apr 11 19:31:38 anirban-laptop kernel: [    1.827306] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 11 19:31:38 anirban-laptop kernel: [    1.827503] usbcore: registered new interface driver usb-storage
Apr 11 19:31:38 anirban-laptop kernel: [    1.827513] USB Mass Storage support registered.
Apr 11 19:31:38 anirban-laptop kernel: [    2.159931] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1a:4b:70:18:d0
Apr 11 19:31:38 anirban-laptop kernel: [    2.159936] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
Apr 11 19:31:38 anirban-laptop kernel: [    2.159939] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
Apr 11 19:31:38 anirban-laptop kernel: [    2.159942] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr 11 19:31:38 anirban-laptop kernel: [    2.211319] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:38 anirban-laptop kernel: [    2.264107] usb 6-1: USB disconnect, address 2
Apr 11 19:31:38 anirban-laptop kernel: [    2.335793] [drm] fb0: inteldrmfb frame buffer device
Apr 11 19:31:38 anirban-laptop kernel: [    2.339260] acpi device:02: registered as cooling_device7
Apr 11 19:31:38 anirban-laptop kernel: [    2.339907] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
Apr 11 19:31:38 anirban-laptop kernel: [    2.339936] ACPI: Video Device [C098] (multi-head: yes  rom: no  post: no)
Apr 11 19:31:38 anirban-laptop kernel: [    2.339967] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 11 19:31:38 anirban-laptop kernel: [    2.407155] [drm] LVDS-8: set mode 1280x800 17
Apr 11 19:31:38 anirban-laptop kernel: [    2.533061] usb 6-1: new full speed USB device using uhci_hcd and address 3
Apr 11 19:31:38 anirban-laptop kernel: [    2.615755] Console: switching to colour frame buffer device 160x50
Apr 11 19:31:38 anirban-laptop kernel: [    2.697322] usb 6-1: configuration #1 chosen from 1 choice
Apr 11 19:31:38 anirban-laptop kernel: [    2.721342] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 11 19:31:38 anirban-laptop kernel: [    2.945778] PM: Starting manual resume from disk
Apr 11 19:31:38 anirban-laptop kernel: [    2.973642] EXT4-fs (sda1): barriers enabled
Apr 11 19:31:38 anirban-laptop kernel: [    2.988787] kjournald2 starting: pid 400, dev sda1:8, commit interval 5 seconds
Apr 11 19:31:38 anirban-laptop kernel: [    2.988938] EXT4-fs (sda1): delayed allocation enabled
Apr 11 19:31:38 anirban-laptop kernel: [    2.988943] EXT4-fs: file extents enabled
Apr 11 19:31:38 anirban-laptop kernel: [    2.992993] EXT4-fs: mballoc enabled
Apr 11 19:31:38 anirban-laptop kernel: [    2.993008] EXT4-fs (sda1): mounted filesystem with ordered data mode
Apr 11 19:31:38 anirban-laptop kernel: [    3.903332] type=1505 audit(1270994487.310:2): operation="profile_load" pid=425 name=/usr/share/gdm/guest-session/Xsession
Apr 11 19:31:38 anirban-laptop kernel: [    3.905959] type=1505 audit(1270994487.312:3): operation="profile_load" pid=426 name=/sbin/dhclient3
Apr 11 19:31:38 anirban-laptop kernel: [    3.906696] type=1505 audit(1270994487.312:4): operation="profile_load" pid=426 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 11 19:31:38 anirban-laptop kernel: [    3.907126] type=1505 audit(1270994487.312:5): operation="profile_load" pid=426 name=/usr/lib/connman/scripts/dhclient-script
Apr 11 19:31:38 anirban-laptop kernel: [    3.986819] type=1505 audit(1270994487.392:6): operation="profile_load" pid=427 name=/usr/bin/evince
Apr 11 19:31:38 anirban-laptop kernel: [    3.998979] type=1505 audit(1270994487.405:7): operation="profile_load" pid=427 name=/usr/bin/evince-previewer
Apr 11 19:31:38 anirban-laptop kernel: [    4.006103] type=1505 audit(1270994487.413:8): operation="profile_load" pid=427 name=/usr/bin/evince-thumbnailer
Apr 11 19:31:38 anirban-laptop kernel: [    4.056693] type=1505 audit(1270994487.461:9): operation="profile_load" pid=429 name=/usr/bin/freshclam
Apr 11 19:31:38 anirban-laptop kernel: [    7.732266] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Apr 11 19:31:38 anirban-laptop kernel: [    7.735281] scsi 9:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Apr 11 19:31:38 anirban-laptop kernel: [    7.751255] sr1: scsi-1 drive
Apr 11 19:31:38 anirban-laptop kernel: [    7.751493] sr 9:0:0:0: Attached scsi generic sg2 type 5
Apr 11 19:31:38 anirban-laptop kernel: [    7.751587] sd 9:0:0:1: Attached scsi generic sg3 type 0
Apr 11 19:31:38 anirban-laptop kernel: [    7.761236] sd 9:0:0:1: [sdb] Attached SCSI removable disk
Apr 11 19:31:38 anirban-laptop kernel: [   11.767513] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k 
Apr 11 19:31:38 anirban-laptop kernel: [   11.773884] EXT4-fs (sda1): internal journal on sda1:8
Apr 11 19:31:38 anirban-laptop kernel: [   11.909391] udev: starting version 147
Apr 11 19:31:38 anirban-laptop kernel: [   13.067555] usbcore: registered new interface driver usbserial
Apr 11 19:31:38 anirban-laptop kernel: [   13.067569] USB Serial support registered for generic
Apr 11 19:31:38 anirban-laptop kernel: [   13.067608] usbcore: registered new interface driver usbserial_generic
Apr 11 19:31:38 anirban-laptop kernel: [   13.067610] usbserial: USB Serial Driver core
Apr 11 19:31:38 anirban-laptop kernel: [   13.085529] USB Serial support registered for GSM modem (1-port)
Apr 11 19:31:38 anirban-laptop kernel: [   13.085576] option 6-1:1.0: GSM modem (1-port) converter detected
Apr 11 19:31:38 anirban-laptop kernel: [   13.085664] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Apr 11 19:31:38 anirban-laptop kernel: [   13.085676] option 6-1:1.1: GSM modem (1-port) converter detected
Apr 11 19:31:38 anirban-laptop kernel: [   13.085723] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 11 19:31:38 anirban-laptop kernel: [   13.085734] option 6-1:1.2: GSM modem (1-port) converter detected
Apr 11 19:31:38 anirban-laptop kernel: [   13.085783] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
Apr 11 19:31:38 anirban-laptop kernel: [   13.085802] usbcore: registered new interface driver option
Apr 11 19:31:38 anirban-laptop kernel: [   13.085804] option: v0.7.2:USB Driver for GSM modems
Apr 11 19:31:38 anirban-laptop kernel: [   13.146430] lp: driver loaded but no devices found
Apr 11 19:31:38 anirban-laptop kernel: [   13.146745] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:30c0]
Apr 11 19:31:38 anirban-laptop kernel: [   13.149187] cfg80211: Calling CRDA to update world regulatory domain
Apr 11 19:31:38 anirban-laptop kernel: [   13.272846] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x04b8, PCI irq 16
Apr 11 19:31:38 anirban-laptop kernel: [   13.272853] yenta_cardbus 0000:02:04.0: Socket status: 30000006
Apr 11 19:31:38 anirban-laptop kernel: [   13.272857] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
Apr 11 19:31:38 anirban-laptop kernel: [   13.272869] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
Apr 11 19:31:38 anirban-laptop kernel: [   13.272873] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
Apr 11 19:31:38 anirban-laptop kernel: [   13.273135] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xe4200000 - 0xe42fffff
Apr 11 19:31:38 anirban-laptop kernel: [   13.273138] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
Apr 11 19:31:38 anirban-laptop kernel: [   13.344805] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 11 19:31:38 anirban-laptop kernel: [   13.461816] cfg80211: World regulatory domain updated:
Apr 11 19:31:38 anirban-laptop kernel: [   13.461820]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 11 19:31:38 anirban-laptop kernel: [   13.461823]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 19:31:38 anirban-laptop kernel: [   13.461826]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 11 19:31:38 anirban-laptop kernel: [   13.461828]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 11 19:31:38 anirban-laptop kernel: [   13.461831]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 19:31:38 anirban-laptop kernel: [   13.461833]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 19:31:38 anirban-laptop kernel: [   13.714357] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Apr 11 19:31:38 anirban-laptop kernel: [   13.716806] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Apr 11 19:31:38 anirban-laptop kernel: [   13.717828] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Apr 11 19:31:38 anirban-laptop kernel: [   13.718696] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Apr 11 19:31:38 anirban-laptop kernel: [   13.719707] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Apr 11 19:31:38 anirban-laptop kernel: [   13.743207] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Apr 11 19:31:38 anirban-laptop kernel: [   13.743210] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Apr 11 19:31:38 anirban-laptop kernel: [   13.743347] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 11 19:31:38 anirban-laptop kernel: [   13.800905] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
Apr 11 19:31:38 anirban-laptop kernel: [   13.800911] serio: Synaptics pass-through port at isa0060/serio4/input0
Apr 11 19:31:38 anirban-laptop kernel: [   13.813729] iwl3945 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr 11 19:31:38 anirban-laptop kernel: [   13.813733] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr 11 19:31:38 anirban-laptop kernel: [   13.841791] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
Apr 11 19:31:38 anirban-laptop kernel: [   14.525279] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Apr 11 19:31:38 anirban-laptop kernel: [   14.525301] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 19:31:38 anirban-laptop kernel: [   14.872588] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Apr 11 19:31:40 anirban-laptop kernel: [   17.502082] __ratelimit: 15 callbacks suppressed
Apr 11 19:31:40 anirban-laptop kernel: [   17.502085] type=1505 audit(1270994500.908:15): operation="profile_replace" pid=1029 name=/usr/share/gdm/guest-session/Xsession
Apr 11 19:31:40 anirban-laptop kernel: [   17.503667] type=1505 audit(1270994500.908:16): operation="profile_replace" pid=1030 name=/sbin/dhclient3
Apr 11 19:31:40 anirban-laptop kernel: [   17.504455] type=1505 audit(1270994500.912:17): operation="profile_replace" pid=1030 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 11 19:31:40 anirban-laptop kernel: [   17.504880] type=1505 audit(1270994500.912:18): operation="profile_replace" pid=1030 name=/usr/lib/connman/scripts/dhclient-script
Apr 11 19:31:40 anirban-laptop kernel: [   17.509831] type=1505 audit(1270994500.916:19): operation="profile_replace" pid=1031 name=/usr/bin/evince
Apr 11 19:31:40 anirban-laptop kernel: [   17.521960] type=1505 audit(1270994500.928:20): operation="profile_replace" pid=1031 name=/usr/bin/evince-previewer
Apr 11 19:31:40 anirban-laptop kernel: [   17.529417] type=1505 audit(1270994500.936:21): operation="profile_replace" pid=1031 name=/usr/bin/evince-thumbnailer
Apr 11 19:31:40 anirban-laptop kernel: [   17.535159] tg3 0000:18:00.0: PME# disabled
Apr 11 19:31:40 anirban-laptop kernel: [   17.539418] type=1505 audit(1270994500.944:22): operation="profile_replace" pid=1033 name=/usr/bin/freshclam
Apr 11 19:31:40 anirban-laptop kernel: [   17.541377] type=1505 audit(1270994500.948:23): operation="profile_replace" pid=1034 name=/usr/sbin/clamd
Apr 11 19:31:40 anirban-laptop kernel: [   17.543338] type=1505 audit(1270994500.948:24): operation="profile_replace" pid=1035 name=/usr/lib/cups/backend/cups-pdf
Apr 11 19:31:41 anirban-laptop kernel: [   17.588596] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 11 19:31:42 anirban-laptop kernel: [   19.345417] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:42 anirban-laptop kernel: [   19.487120] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:43 anirban-laptop kernel: [   19.873893] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:43 anirban-laptop kernel: [   20.014162] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:43 anirban-laptop squid[1256]: Squid Parent: child process 1264 started
Apr 11 19:31:47 anirban-laptop kernel: [   23.582953] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:47 anirban-laptop kernel: [   23.723191] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:47 anirban-laptop kernel: [   23.986936] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:47 anirban-laptop kernel: [   24.126946] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:47 anirban-laptop kernel: [   24.443769] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:48 anirban-laptop kernel: [   24.583773] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:31:48 anirban-laptop kernel: [   25.384093] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:31:48 anirban-laptop kernel: [   25.384099] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:31:48 anirban-laptop kernel: [   25.384103] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:31:48 anirban-laptop kernel: [   25.384109] Info fld=0x0
Apr 11 19:31:48 anirban-laptop kernel: [   25.384111] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:31:48 anirban-laptop kernel: [   25.384121] __ratelimit: 9 callbacks suppressed
Apr 11 19:31:55 anirban-laptop kernel: [   31.594196] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:31:55 anirban-laptop kernel: [   31.594202] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:31:55 anirban-laptop kernel: [   31.594208] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:31:55 anirban-laptop kernel: [   31.594216] Info fld=0x0
Apr 11 19:31:55 anirban-laptop kernel: [   31.594219] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:32:01 anirban-laptop kernel: [   37.779140] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:32:01 anirban-laptop kernel: [   37.779146] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:32:01 anirban-laptop kernel: [   37.779153] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:32:01 anirban-laptop kernel: [   37.779161] Info fld=0x0
Apr 11 19:32:01 anirban-laptop kernel: [   37.779164] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:32:07 anirban-laptop kernel: [   43.961495] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:32:07 anirban-laptop kernel: [   43.961501] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:32:07 anirban-laptop kernel: [   43.961507] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:32:07 anirban-laptop kernel: [   43.961515] Info fld=0x0
Apr 11 19:32:07 anirban-laptop kernel: [   43.961518] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:32:14 anirban-laptop kernel: [   50.730276] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:32:14 anirban-laptop kernel: [   50.730282] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:32:14 anirban-laptop kernel: [   50.730288] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:32:14 anirban-laptop kernel: [   50.730296] Info fld=0x0
Apr 11 19:32:14 anirban-laptop kernel: [   50.730299] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:32:20 anirban-laptop kernel: [   56.915968] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:32:20 anirban-laptop kernel: [   56.915973] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:32:20 anirban-laptop kernel: [   56.915979] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:32:20 anirban-laptop kernel: [   56.915987] Info fld=0x0
Apr 11 19:32:20 anirban-laptop kernel: [   56.915990] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:32:26 anirban-laptop kernel: [   63.100274] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:32:26 anirban-laptop kernel: [   63.100280] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:32:26 anirban-laptop kernel: [   63.100286] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:32:26 anirban-laptop kernel: [   63.100294] Info fld=0x0
Apr 11 19:32:26 anirban-laptop kernel: [   63.100297] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:32:32 anirban-laptop kernel: [   69.283464] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 19:32:32 anirban-laptop kernel: [   69.283468] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 19:32:32 anirban-laptop kernel: [   69.283474] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 19:32:32 anirban-laptop kernel: [   69.283481] Info fld=0x0
Apr 11 19:32:32 anirban-laptop kernel: [   69.283484] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 19:33:09 anirban-laptop kernel: [  106.045041] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:33:09 anirban-laptop kernel: [  106.186046] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:33:09 anirban-laptop kernel: [  106.450979] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:33:10 anirban-laptop kernel: [  106.591052] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:33:10 anirban-laptop kernel: [  106.863783] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:33:10 anirban-laptop kernel: [  107.003761] [drm] TV-14: set mode NTSC 480i 0
Apr 11 19:33:39 anirban-laptop kernel: [  136.372514] UDF-fs: Filesystem marked read-only because writing to pseudooverwrite partition is not implemented.
Apr 11 19:33:39 anirban-laptop kernel: [  136.446998] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2010/03/30 11:51 (114a)
Apr 11 19:34:01 anirban-laptop pppd[1921]: pppd 2.4.5 started by root, uid 0
Apr 11 19:34:01 anirban-laptop pppd[1921]: Using interface ppp0
Apr 11 19:34:01 anirban-laptop pppd[1921]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 11 19:34:04 anirban-laptop pppd[1921]: CHAP authentication succeeded
Apr 11 19:34:04 anirban-laptop pppd[1921]: CHAP authentication succeeded
Apr 11 19:34:04 anirban-laptop kernel: [  160.975610] PPP BSD Compression module registered
Apr 11 19:34:04 anirban-laptop kernel: [  161.035612] PPP Deflate Compression module registered
Apr 11 19:34:04 anirban-laptop pppd[1921]: local  IP address 115.117.223.226
Apr 11 19:34:04 anirban-laptop pppd[1921]: remote IP address 172.29.243.161
Apr 11 19:34:04 anirban-laptop pppd[1921]: primary   DNS address 203.200.230.244
Apr 11 19:34:04 anirban-laptop pppd[1921]: secondary DNS address 202.54.29.5
Apr 11 19:44:03 anirban-laptop kernel: [  759.989065] ata4: lost interrupt (Status 0x58)
Apr 11 19:44:03 anirban-laptop kernel: [  760.092931] ata4: soft resetting link
Apr 11 19:44:03 anirban-laptop kernel: [  760.320332] ata4.00: configured for MWDMA2
Apr 11 19:44:03 anirban-laptop kernel: [  760.336762] ata4: EH complete
Apr 11 19:56:56 anirban-laptop kernel: [ 1533.000103] ata4: lost interrupt (Status 0x58)
Apr 11 19:56:56 anirban-laptop kernel: [ 1533.112731] ata4: soft resetting link
Apr 11 19:56:56 anirban-laptop kernel: [ 1533.340385] ata4.00: configured for MWDMA2
Apr 11 19:56:56 anirban-laptop kernel: [ 1533.355827] ata4: EH complete
Apr 11 20:02:01 anirban-laptop kernel: [ 1838.016992] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 11 20:02:36 anirban-laptop kernel: [ 1873.585069] CE: hpet increasing min_delta_ns to 22500 nsec
Apr 11 20:04:43 anirban-laptop kernel: [ 2000.248978] [drm] TV-14: set mode NTSC 480i 0
Apr 11 20:04:44 anirban-laptop kernel: [ 2000.389619] [drm] TV-14: set mode NTSC 480i 0
Apr 11 20:05:30 anirban-laptop pulseaudio[1713]: ratelimit.c: 97 events suppressed
Apr 11 20:06:56 anirban-laptop pulseaudio[1713]: ratelimit.c: 31 events suppressed
Apr 11 20:48:09 anirban-laptop kernel: [ 4606.000058] ata4: lost interrupt (Status 0x58)
Apr 11 20:48:09 anirban-laptop kernel: [ 4606.112062] ata4: soft resetting link
Apr 11 20:48:09 anirban-laptop kernel: [ 4606.348324] ata4.00: configured for MWDMA2
Apr 11 20:48:09 anirban-laptop kernel: [ 4606.359755] ata4: EH complete
Apr 11 21:02:08 anirban-laptop pppd[1921]: Terminating on signal 15
Apr 11 22:55:15 anirban-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr 11 22:55:15 anirban-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="794" x-info="http://www.rsyslog.com"] (re)start
Apr 11 22:55:15 anirban-laptop rsyslogd: rsyslogd's groupid changed to 102
Apr 11 22:55:15 anirban-laptop rsyslogd: rsyslogd's userid changed to 101
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] KERNEL supported cpus:
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   Intel GenuineIntel
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   AMD AuthenticAMD
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   NSC Geode by NSC
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   Centaur CentaurHauls
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7b0000 (usable)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7b0000 - 000000001f7c5400 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7c5400 - 000000001f7e7fb8 (ACPI NVS)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7e7fb8 - 0000000020000000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9a000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] DMI 2.4 present.
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] last_pfn = 0x1f7b0 max_arch_pfn = 0x100000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] modified physical RAM map:
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000001f7b0000 (usable)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 000000001f7b0000 - 000000001f7c5400 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 000000001f7c5400 - 000000001f7e7fb8 (ACPI NVS)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 000000001f7e7fb8 - 0000000020000000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed9a000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f7b0000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] RAMDISK: 172ba000 - 17a03e54
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: RSDP 000fc600 00024 (v02 HP    )
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: XSDT 1f7c81c8 0007C (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: FACP 1f7c8084 000F4 (v04 HP     30C0     00000003 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: DSDT 1f7c84cc 12C10 (v01 HP       nc75xx 00010000 MSFT 03000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: FACS 1f7e7d80 00040
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: SLIC 1f7c8244 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: HPET 1f7c83bc 00038 (v01 HP     30C0     00000001 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: APIC 1f7c83f4 00068 (v01 HP     30C0     00000001 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: MCFG 1f7c845c 0003C (v01 HP     30C0     00000001 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: TCPA 1f7c8498 00032 (v02 HP     30C0     00000001 HP   00000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7db0dc 00059 (v01 HP       HPQNLP 00000001 MSFT 03000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7db135 00328 (v01 HP       HPQSAT 00000001 MSFT 03000001)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbca1 0025F (v01 HP      Cpu0Tst 00003000 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbf00 000A6 (v01 HP      Cpu1Tst 00003000 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbfa6 004D7 (v01 HP        CpuPm 00003000 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] 503MB LOWMEM available.
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   mapped low ram: 0 - 1f7b0000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   low ram: 0 - 1f7b0000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 1f7b0000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bef8
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f7b0000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #4 [00172ba000 - 0017a03e54]          RAMDISK ==> [00172ba000 - 0017a03e54]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #6 [00008ae000 - 00008b10f4]              BRK ==> [00008ae000 - 00008b10f4]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f7b0
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]   HighMem  0x0001f7b0 -> 0x0001f7b0
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0001f7b0
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Using APIC driver default
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127835
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=f2551907-f2d8-4fca-9c65-db29c6645b41 ro quiet quiet splash
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Initializing CPU#0
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] allocated 2578880 bytes of page_cgroup
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Memory: 492544k/515776k available (4578k kernel code, 22444k reserved, 2146k data, 540k init, 0k highmem)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] virtual kernel memory layout:
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     vmalloc : 0xdffb0000 - 0xff7fe000   ( 504 MB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf7b0000   ( 503 MB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Extended CMOS year: 2000
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Apr 11 22:55:15 anirban-laptop kernel: [    0.000000] Detected 1795.875 MHz processor.
Apr 11 22:55:15 anirban-laptop kernel: [    0.001337] Console: colour VGA+ 80x25
Apr 11 22:55:15 anirban-laptop kernel: [    0.001340] console [tty0] enabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.001526] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 11 22:55:15 anirban-laptop kernel: [    0.001533] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.75 BogoMIPS (lpj=7183500)
Apr 11 22:55:15 anirban-laptop kernel: [    0.001548] Security Framework initialized
Apr 11 22:55:15 anirban-laptop kernel: [    0.001563] AppArmor: AppArmor initialized
Apr 11 22:55:15 anirban-laptop kernel: [    0.001570] Mount-cache hash table entries: 512
Apr 11 22:55:15 anirban-laptop kernel: [    0.001677] Initializing cgroup subsys ns
Apr 11 22:55:15 anirban-laptop kernel: [    0.001681] Initializing cgroup subsys cpuacct
Apr 11 22:55:15 anirban-laptop kernel: [    0.001685] Initializing cgroup subsys memory
Apr 11 22:55:15 anirban-laptop kernel: [    0.001691] Initializing cgroup subsys freezer
Apr 11 22:55:15 anirban-laptop kernel: [    0.001693] Initializing cgroup subsys net_cls
Apr 11 22:55:15 anirban-laptop kernel: [    0.001706] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 11 22:55:15 anirban-laptop kernel: [    0.001708] CPU: L2 cache: 2048K
Apr 11 22:55:15 anirban-laptop kernel: [    0.001711] CPU: Physical Processor ID: 0
Apr 11 22:55:15 anirban-laptop kernel: [    0.001713] CPU: Processor Core ID: 0
Apr 11 22:55:15 anirban-laptop kernel: [    0.001717] mce: CPU supports 6 MCE banks
Apr 11 22:55:15 anirban-laptop kernel: [    0.001726] using mwait in idle threads.
Apr 11 22:55:15 anirban-laptop kernel: [    0.001730] Performance Counters: Core2 events, Intel PMU driver.
Apr 11 22:55:15 anirban-laptop kernel: [    0.001747] ... version:                 2
Apr 11 22:55:15 anirban-laptop kernel: [    0.001748] ... bit width:               40
Apr 11 22:55:15 anirban-laptop kernel: [    0.001750] ... generic counters:        2
Apr 11 22:55:15 anirban-laptop kernel: [    0.001752] ... value mask:              000000ffffffffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.001754] ... max period:              000000007fffffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.001756] ... fixed-purpose counters:  3
Apr 11 22:55:15 anirban-laptop kernel: [    0.001757] ... counter mask:            0000000700000003
Apr 11 22:55:15 anirban-laptop kernel: [    0.001761] Checking 'hlt' instruction... OK.
Apr 11 22:55:15 anirban-laptop kernel: [    0.018525] ACPI: Core revision 20090521
Apr 11 22:55:15 anirban-laptop kernel: [    0.044438] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 11 22:55:15 anirban-laptop kernel: [    0.084244] CPU0: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
Apr 11 22:55:15 anirban-laptop kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] Initializing CPU#1
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3590.97 BogoMIPS (lpj=7181942)
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] mce: CPU supports 6 MCE banks
Apr 11 22:55:15 anirban-laptop kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Apr 11 22:55:15 anirban-laptop kernel: [    0.173546] CPU1: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
Apr 11 22:55:15 anirban-laptop kernel: [    0.173564] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 11 22:55:15 anirban-laptop kernel: [    0.176027] Brought up 2 CPUs
Apr 11 22:55:15 anirban-laptop kernel: [    0.176030] Total of 2 processors activated (7182.72 BogoMIPS).
Apr 11 22:55:15 anirban-laptop kernel: [    0.176186] Booting paravirtualized kernel on bare hardware
Apr 11 22:55:15 anirban-laptop kernel: [    0.176232] regulator: core version 0.5
Apr 11 22:55:15 anirban-laptop kernel: [    0.176232] Time: 17:24:57  Date: 04/11/10
Apr 11 22:55:15 anirban-laptop kernel: [    0.176232] NET: Registered protocol family 16
Apr 11 22:55:15 anirban-laptop kernel: [    0.176237] EISA bus registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.176247] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Apr 11 22:55:15 anirban-laptop kernel: [    0.176250] ACPI: bus type pci registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.176330] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Apr 11 22:55:15 anirban-laptop kernel: [    0.176334] PCI: Not using MMCONFIG.
Apr 11 22:55:15 anirban-laptop kernel: [    0.177447] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=40
Apr 11 22:55:15 anirban-laptop kernel: [    0.177450] PCI: Using configuration type 1 for base access
Apr 11 22:55:15 anirban-laptop kernel: [    0.180775] bio: create slab <bio-0> at 0
Apr 11 22:55:15 anirban-laptop kernel: [    0.207342] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 11 22:55:15 anirban-laptop kernel: [    0.236289] ACPI: Interpreter enabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.236297] ACPI: (supports S0 S3 S4 S5)
Apr 11 22:55:15 anirban-laptop kernel: [    0.236317] ACPI: Using IOAPIC for interrupt routing
Apr 11 22:55:15 anirban-laptop kernel: [    0.236373] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Apr 11 22:55:15 anirban-laptop kernel: [    0.244115] PCI: MCFG area at f8000000 reserved in ACPI motherboard resources
Apr 11 22:55:15 anirban-laptop kernel: [    0.244118] PCI: Using MMCONFIG for extended config space
Apr 11 22:55:15 anirban-laptop kernel: [    0.255138] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Apr 11 22:55:15 anirban-laptop kernel: [    0.255141] ACPI: EC: driver started in interrupt mode
Apr 11 22:55:15 anirban-laptop kernel: [    0.255220] ACPI: Power Resource [C29B] (on)
Apr 11 22:55:15 anirban-laptop kernel: [    0.255275] ACPI: Power Resource [C1C5] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.255380] ACPI: Power Resource [C3B7] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.255481] ACPI: Power Resource [C3B8] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.255579] ACPI: Power Resource [C3B9] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.255676] ACPI: Power Resource [C3BA] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.255773] ACPI: Power Resource [C3BB] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.256197] ACPI: No dock devices found.
Apr 11 22:55:15 anirban-laptop kernel: [    0.260480] ACPI: PCI Root Bridge [C003] (0000:00)
Apr 11 22:55:15 anirban-laptop kernel: [    0.261390] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.261399] pci 0000:00:1a.7: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.261686] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.261695] pci 0000:00:1b.0: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.261918] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.261927] pci 0000:00:1c.0: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.262147] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.262157] pci 0000:00:1c.1: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.262379] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.262389] pci 0000:00:1c.2: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.262607] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.262617] pci 0000:00:1c.4: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.263419] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.263429] pci 0000:00:1d.7: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.263799] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 11 22:55:15 anirban-laptop kernel: [    0.263806] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
Apr 11 22:55:15 anirban-laptop kernel: [    0.263813] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 007f)
Apr 11 22:55:15 anirban-laptop kernel: [    0.263828] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 02e8 (mask 0007)
Apr 11 22:55:15 anirban-laptop kernel: [    0.264380] pci 0000:00:1f.2: PME# supported from D3hot
Apr 11 22:55:15 anirban-laptop kernel: [    0.264390] pci 0000:00:1f.2: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.265061] pci 0000:10:00.0: PME# supported from D0 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.265074] pci 0000:10:00.0: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.265463] pci 0000:18:00.0: PME# supported from D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.265470] pci 0000:18:00.0: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.265957] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 11 22:55:15 anirban-laptop kernel: [    0.265967] pci 0000:02:04.0: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.266119] pci 0000:00:1e.0: transparent bridge
Apr 11 22:55:15 anirban-laptop kernel: [    0.311691] ACPI: PCI Interrupt Link [C12D] (IRQs 10 11) *5
Apr 11 22:55:15 anirban-laptop kernel: [    0.311919] ACPI: PCI Interrupt Link [C12E] (IRQs *10 11)
Apr 11 22:55:15 anirban-laptop kernel: [    0.312150] ACPI: PCI Interrupt Link [C12F] (IRQs 10 *11)
Apr 11 22:55:15 anirban-laptop kernel: [    0.312364] ACPI: PCI Interrupt Link [C130] (IRQs 10 11) *0, disabled.
Apr 11 22:55:15 anirban-laptop kernel: [    0.312588] ACPI: PCI Interrupt Link [C140] (IRQs *10 11)
Apr 11 22:55:15 anirban-laptop kernel: [    0.312811] ACPI: PCI Interrupt Link [C141] (IRQs *10 11)
Apr 11 22:55:15 anirban-laptop kernel: [    0.313028] ACPI: PCI Interrupt Link [C142] (IRQs 10 11) *0, disabled.
Apr 11 22:55:15 anirban-laptop kernel: [    0.313133] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS 20090521 pci_link-182
Apr 11 22:55:15 anirban-laptop kernel: [    0.313387] SCSI subsystem initialized
Apr 11 22:55:15 anirban-laptop kernel: [    0.313412] usbcore: registered new interface driver usbfs
Apr 11 22:55:15 anirban-laptop kernel: [    0.313412] usbcore: registered new interface driver hub
Apr 11 22:55:15 anirban-laptop kernel: [    0.313412] usbcore: registered new device driver usb
Apr 11 22:55:15 anirban-laptop kernel: [    0.313412] ACPI: WMI: Mapper loaded
Apr 11 22:55:15 anirban-laptop kernel: [    0.313412] PCI: Using ACPI for IRQ routing
Apr 11 22:55:15 anirban-laptop kernel: [    0.324010] Bluetooth: Core ver 2.15
Apr 11 22:55:15 anirban-laptop kernel: [    0.324026] NET: Registered protocol family 31
Apr 11 22:55:15 anirban-laptop kernel: [    0.324026] Bluetooth: HCI device and connection manager initialized
Apr 11 22:55:15 anirban-laptop kernel: [    0.324026] Bluetooth: HCI socket layer initialized
Apr 11 22:55:15 anirban-laptop kernel: [    0.324026] NetLabel: Initializing
Apr 11 22:55:15 anirban-laptop kernel: [    0.324026] NetLabel:  domain hash size = 128
Apr 11 22:55:15 anirban-laptop kernel: [    0.324026] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 11 22:55:15 anirban-laptop kernel: [    0.324040] NetLabel:  unlabeled traffic allowed by default
Apr 11 22:55:15 anirban-laptop kernel: [    0.324077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 11 22:55:15 anirban-laptop kernel: [    0.324083] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr 11 22:55:15 anirban-laptop kernel: [    0.340007] pnp: PnP ACPI init
Apr 11 22:55:15 anirban-laptop kernel: [    0.340018] ACPI: bus type pnp registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.349547] pnp: PnP ACPI: found 12 devices
Apr 11 22:55:15 anirban-laptop kernel: [    0.349550] ACPI: ACPI bus type pnp unregistered
Apr 11 22:55:15 anirban-laptop kernel: [    0.349554] PnPBIOS: Disabled by ACPI PNP
Apr 11 22:55:15 anirban-laptop kernel: [    0.349564] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349568] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349572] system 00:00: iomem range 0x100000-0x1f7fffff could not be reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349583] system 00:09: ioport range 0x500-0x57f has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349586] system 00:09: ioport range 0x800-0x80f has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349589] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349593] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349599] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349602] system 00:0a: ioport range 0x1000-0x107f has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349606] system 00:0a: ioport range 0x1100-0x113f has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349609] system 00:0a: ioport range 0x1200-0x121f has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349612] system 00:0a: iomem range 0xf8000000-0xfbffffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349615] system 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349619] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349622] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349625] system 00:0a: iomem range 0xfed90000-0xfed99fff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349631] system 00:0b: iomem range 0xcee00-0xcffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349634] system 00:0b: iomem range 0xd2a00-0xd3fff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349638] system 00:0b: iomem range 0xfeda0000-0xfedbffff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.349641] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 11 22:55:15 anirban-laptop kernel: [    0.384339] AppArmor: AppArmor Filesystem Enabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384482] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:08
Apr 11 22:55:15 anirban-laptop kernel: [    0.384485] pci 0000:00:1c.0:   IO window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384498] pci 0000:00:1c.0:   MEM window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384507] pci 0000:00:1c.0:   PREFETCH window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384517] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:10
Apr 11 22:55:15 anirban-laptop kernel: [    0.384520] pci 0000:00:1c.1:   IO window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384533] pci 0000:00:1c.1:   MEM window: 0xe4100000-0xe41fffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384543] pci 0000:00:1c.1:   PREFETCH window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384553] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:18
Apr 11 22:55:15 anirban-laptop kernel: [    0.384555] pci 0000:00:1c.2:   IO window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384568] pci 0000:00:1c.2:   MEM window: 0xe4000000-0xe40fffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384578] pci 0000:00:1c.2:   PREFETCH window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384588] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:28
Apr 11 22:55:15 anirban-laptop kernel: [    0.384594] pci 0000:00:1c.4:   IO window: 0x2000-0x3fff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384607] pci 0000:00:1c.4:   MEM window: 0xe0000000-0xe3ffffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384617] pci 0000:00:1c.4:   PREFETCH window: disabled
Apr 11 22:55:15 anirban-laptop kernel: [    0.384629] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
Apr 11 22:55:15 anirban-laptop kernel: [    0.384632] pci 0000:02:04.0:   IO window: 0x005000-0x0050ff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384642] pci 0000:02:04.0:   IO window: 0x005400-0x0054ff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384653] pci 0000:02:04.0:   PREFETCH window: 0x20000000-0x23ffffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384664] pci 0000:02:04.0:   MEM window: 0x24000000-0x27ffffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384675] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Apr 11 22:55:15 anirban-laptop kernel: [    0.384681] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384694] pci 0000:00:1e.0:   MEM window: 0xe4200000-0xe42fffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384704] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
Apr 11 22:55:15 anirban-laptop kernel: [    0.384738] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:15 anirban-laptop kernel: [    0.384774] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 11 22:55:15 anirban-laptop kernel: [    0.384806] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 11 22:55:15 anirban-laptop kernel: [    0.384835] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:15 anirban-laptop kernel: [    0.384883] pci 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:15 anirban-laptop kernel: [    0.384971] NET: Registered protocol family 2
Apr 11 22:55:15 anirban-laptop kernel: [    0.385076] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.385381] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.385458] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.385521] TCP: Hash tables configured (established 16384 bind 16384)
Apr 11 22:55:15 anirban-laptop kernel: [    0.385524] TCP reno registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.385593] NET: Registered protocol family 1
Apr 11 22:55:15 anirban-laptop kernel: [    0.385651] Trying to unpack rootfs image as initramfs...
Apr 11 22:55:15 anirban-laptop kernel: [    0.591240] Freeing initrd memory: 7463k freed
Apr 11 22:55:15 anirban-laptop kernel: [    0.596727] cpufreq-nforce2: No nForce2 chipset.
Apr 11 22:55:15 anirban-laptop kernel: [    0.596759] Scanning for low memory corruption every 60 seconds
Apr 11 22:55:15 anirban-laptop kernel: [    0.596878] audit: initializing netlink socket (disabled)
Apr 11 22:55:15 anirban-laptop kernel: [    0.596896] type=2000 audit(1271006696.596:1): initialized
Apr 11 22:55:15 anirban-laptop kernel: [    0.606517] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 11 22:55:15 anirban-laptop kernel: [    0.608165] VFS: Disk quotas dquot_6.5.2
Apr 11 22:55:15 anirban-laptop kernel: [    0.608231] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 11 22:55:15 anirban-laptop kernel: [    0.608825] fuse init (API version 7.12)
Apr 11 22:55:15 anirban-laptop kernel: [    0.608920] msgmni has been set to 977
Apr 11 22:55:15 anirban-laptop kernel: [    0.609153] alg: No test for stdrng (krng)
Apr 11 22:55:15 anirban-laptop kernel: [    0.609168] io scheduler noop registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.609171] io scheduler anticipatory registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.609173] io scheduler deadline registered
Apr 11 22:55:15 anirban-laptop kernel: [    0.609219] io scheduler cfq registered (default)
Apr 11 22:55:15 anirban-laptop kernel: [    0.611015] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 11 22:55:15 anirban-laptop kernel: [    0.611128] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 11 22:55:15 anirban-laptop kernel: [    0.615808] ACPI: AC Adapter [C239] (on-line)
Apr 11 22:55:15 anirban-laptop kernel: [    0.615879] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr 11 22:55:15 anirban-laptop kernel: [    0.615883] ACPI: Power Button [PWRF]
Apr 11 22:55:15 anirban-laptop kernel: [    0.615960] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Apr 11 22:55:15 anirban-laptop kernel: [    0.615963] ACPI: Sleep Button [C2BF]
Apr 11 22:55:15 anirban-laptop kernel: [    0.616018] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Apr 11 22:55:15 anirban-laptop kernel: [    0.616090] ACPI: Lid Switch [C153]
Apr 11 22:55:15 anirban-laptop kernel: [    0.616340] fan PNP0C0B:00: registered as cooling_device0
Apr 11 22:55:15 anirban-laptop kernel: [    0.616347] ACPI: Fan [C3BC] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.616545] fan PNP0C0B:01: registered as cooling_device1
Apr 11 22:55:15 anirban-laptop kernel: [    0.616552] ACPI: Fan [C3BD] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.616749] fan PNP0C0B:02: registered as cooling_device2
Apr 11 22:55:15 anirban-laptop kernel: [    0.616756] ACPI: Fan [C3BE] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.616952] fan PNP0C0B:03: registered as cooling_device3
Apr 11 22:55:15 anirban-laptop kernel: [    0.616958] ACPI: Fan [C3BF] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.617156] fan PNP0C0B:04: registered as cooling_device4
Apr 11 22:55:15 anirban-laptop kernel: [    0.617165] ACPI: Fan [C3C0] (off)
Apr 11 22:55:15 anirban-laptop kernel: [    0.617857] ACPI: SSDT 1f7db525 0023D (v01 HP      Cpu0Ist 00003000 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.618477] ACPI: SSDT 1f7db7e7 004BA (v01 HP      Cpu0Cst 00003001 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.621259] Marking TSC unstable due to TSC halts in idle
Apr 11 22:55:15 anirban-laptop kernel: [    0.621281] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 11 22:55:15 anirban-laptop kernel: [    0.621303] processor LNXCPU:00: registered as cooling_device5
Apr 11 22:55:15 anirban-laptop kernel: [    0.621308] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 11 22:55:15 anirban-laptop kernel: [    0.621659] ACPI: SSDT 1f7db45d 000C8 (v01 HP      Cpu1Ist 00003000 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.622139] ACPI: SSDT 1f7db762 00085 (v01 HP      Cpu1Cst 00003000 INTL 20060317)
Apr 11 22:55:15 anirban-laptop kernel: [    0.623217] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 11 22:55:15 anirban-laptop kernel: [    0.623244] processor LNXCPU:01: registered as cooling_device6
Apr 11 22:55:15 anirban-laptop kernel: [    0.623249] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 11 22:55:15 anirban-laptop kernel: [    0.651673] thermal LNXTHERM:01: registered as thermal_zone0
Apr 11 22:55:15 anirban-laptop kernel: [    0.651682] ACPI: Thermal Zone [TZ0] (65 C)
Apr 11 22:55:15 anirban-laptop kernel: [    0.655896] thermal LNXTHERM:02: registered as thermal_zone1
Apr 11 22:55:15 anirban-laptop kernel: [    0.655907] ACPI: Thermal Zone [TZ1] (61 C)
Apr 11 22:55:15 anirban-laptop kernel: [    0.659905] thermal LNXTHERM:03: registered as thermal_zone2
Apr 11 22:55:15 anirban-laptop kernel: [    0.659914] ACPI: Thermal Zone [TZ3] (40 C)
Apr 11 22:55:15 anirban-laptop kernel: [    0.668987] thermal LNXTHERM:04: registered as thermal_zone3
Apr 11 22:55:15 anirban-laptop kernel: [    0.668996] ACPI: Thermal Zone [TZ4] (37 C)
Apr 11 22:55:15 anirban-laptop kernel: [    0.672694] thermal LNXTHERM:05: registered as thermal_zone4
Apr 11 22:55:15 anirban-laptop kernel: [    0.672703] ACPI: Thermal Zone [TZ5] (74 C)
Apr 11 22:55:15 anirban-laptop kernel: [    0.672780] isapnp: Scanning for PnP cards...
Apr 11 22:55:15 anirban-laptop kernel: [    0.764325] ACPI: Battery Slot [C23B] (battery present)
Apr 11 22:55:15 anirban-laptop kernel: [    0.764517] ACPI: Battery Slot [C23A] (battery absent)
Apr 11 22:55:15 anirban-laptop kernel: [    1.030582] isapnp: No Plug & Play device found
Apr 11 22:55:15 anirban-laptop kernel: [    1.031885] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 11 22:55:15 anirban-laptop kernel: [    1.033399] brd: module loaded
Apr 11 22:55:15 anirban-laptop kernel: [    1.033899] loop: module loaded
Apr 11 22:55:15 anirban-laptop kernel: [    1.033976] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr 11 22:55:15 anirban-laptop kernel: [    1.034081] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 11 22:55:15 anirban-laptop kernel: [    1.034213] ahci: SSS flag set, parallel bus scan disabled
Apr 11 22:55:15 anirban-laptop kernel: [    1.034245] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
Apr 11 22:55:15 anirban-laptop kernel: [    1.034249] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
Apr 11 22:55:15 anirban-laptop kernel: [    1.034413] scsi0 : ahci
Apr 11 22:55:15 anirban-laptop kernel: [    1.034514] scsi1 : ahci
Apr 11 22:55:15 anirban-laptop kernel: [    1.034586] scsi2 : ahci
Apr 11 22:55:15 anirban-laptop kernel: [    1.034659] ata1: SATA max UDMA/133 abar m2048@0xe4509000 port 0xe4509100 irq 28
Apr 11 22:55:15 anirban-laptop kernel: [    1.034662] ata2: DUMMY
Apr 11 22:55:15 anirban-laptop kernel: [    1.034663] ata3: DUMMY
Apr 11 22:55:15 anirban-laptop kernel: [    1.034723] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:15 anirban-laptop kernel: [    1.034871] scsi3 : ata_piix
Apr 11 22:55:15 anirban-laptop kernel: [    1.034944] scsi4 : ata_piix
Apr 11 22:55:15 anirban-laptop kernel: [    1.035499] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x40c0 irq 14
Apr 11 22:55:15 anirban-laptop kernel: [    1.035502] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40c8 irq 15
Apr 11 22:55:15 anirban-laptop kernel: [    1.036492] Fixed MDIO Bus: probed
Apr 11 22:55:15 anirban-laptop kernel: [    1.036531] PPP generic driver version 2.4.2
Apr 11 22:55:15 anirban-laptop kernel: [    1.036625] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 11 22:55:15 anirban-laptop kernel: [    1.036651] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 11 22:55:15 anirban-laptop kernel: [    1.036675] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.036706] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr 11 22:55:15 anirban-laptop kernel: [    1.040644] ehci_hcd 0000:00:1a.7: debug port 1
Apr 11 22:55:15 anirban-laptop kernel: [    1.040675] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe4500000
Apr 11 22:55:15 anirban-laptop kernel: [    1.056026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr 11 22:55:15 anirban-laptop kernel: [    1.056102] usb usb1: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.056135] hub 1-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.056143] hub 1-0:1.0: 4 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.056222] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 11 22:55:15 anirban-laptop kernel: [    1.056244] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.056275] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr 11 22:55:15 anirban-laptop kernel: [    1.060205] ehci_hcd 0000:00:1d.7: debug port 1
Apr 11 22:55:15 anirban-laptop kernel: [    1.060235] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe4508000
Apr 11 22:55:15 anirban-laptop kernel: [    1.076030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr 11 22:55:15 anirban-laptop kernel: [    1.076111] usb usb2: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.076140] hub 2-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.076147] hub 2-0:1.0: 6 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.076211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 11 22:55:15 anirban-laptop kernel: [    1.076230] uhci_hcd: USB Universal Host Controller Interface driver
Apr 11 22:55:15 anirban-laptop kernel: [    1.076254] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:15 anirban-laptop kernel: [    1.076271] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.076302] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr 11 22:55:15 anirban-laptop kernel: [    1.076350] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004020
Apr 11 22:55:15 anirban-laptop kernel: [    1.076444] usb usb3: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.076477] hub 3-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.076484] hub 3-0:1.0: 2 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.076542] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 11 22:55:15 anirban-laptop kernel: [    1.076559] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.076589] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr 11 22:55:15 anirban-laptop kernel: [    1.076636] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00004040
Apr 11 22:55:15 anirban-laptop kernel: [    1.076723] usb usb4: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.076750] hub 4-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.076757] hub 4-0:1.0: 2 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.076812] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 11 22:55:15 anirban-laptop kernel: [    1.076829] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.076861] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Apr 11 22:55:15 anirban-laptop kernel: [    1.076896] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00004060
Apr 11 22:55:15 anirban-laptop kernel: [    1.076980] usb usb5: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.077008] hub 5-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.077014] hub 5-0:1.0: 2 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.077074] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 11 22:55:15 anirban-laptop kernel: [    1.077091] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.077123] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Apr 11 22:55:15 anirban-laptop kernel: [    1.077169] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00004080
Apr 11 22:55:15 anirban-laptop kernel: [    1.077254] usb usb6: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.077281] hub 6-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.077288] hub 6-0:1.0: 2 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.077342] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 11 22:55:15 anirban-laptop kernel: [    1.077359] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 11 22:55:15 anirban-laptop kernel: [    1.077389] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Apr 11 22:55:15 anirban-laptop kernel: [    1.077426] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000040a0
Apr 11 22:55:15 anirban-laptop kernel: [    1.077510] usb usb7: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    1.077538] hub 7-0:1.0: USB hub found
Apr 11 22:55:15 anirban-laptop kernel: [    1.077545] hub 7-0:1.0: 2 ports detected
Apr 11 22:55:15 anirban-laptop kernel: [    1.077655] PNP: PS/2 Controller [PNP0303:C298,PNP0f13:C299] at 0x60,0x64 irq 1,12
Apr 11 22:55:15 anirban-laptop kernel: [    1.079568] i8042.c: Detected active multiplexing controller, rev 1.1.
Apr 11 22:55:15 anirban-laptop kernel: [    1.080321] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 11 22:55:15 anirban-laptop kernel: [    1.080327] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr 11 22:55:15 anirban-laptop kernel: [    1.080331] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr 11 22:55:15 anirban-laptop kernel: [    1.080334] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr 11 22:55:15 anirban-laptop kernel: [    1.080337] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr 11 22:55:15 anirban-laptop kernel: [    1.080397] mice: PS/2 mouse device common for all mice
Apr 11 22:55:15 anirban-laptop kernel: [    1.080539] rtc_cmos 00:05: RTC can wake from S4
Apr 11 22:55:15 anirban-laptop kernel: [    1.080571] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 11 22:55:15 anirban-laptop kernel: [    1.080610] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr 11 22:55:15 anirban-laptop kernel: [    1.080719] device-mapper: uevent: version 1.0.3
Apr 11 22:55:15 anirban-laptop kernel: [    1.080814] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Apr 11 22:55:15 anirban-laptop kernel: [    1.080936] device-mapper: multipath: version 1.1.0 loaded
Apr 11 22:55:15 anirban-laptop kernel: [    1.080939] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 11 22:55:15 anirban-laptop kernel: [    1.081075] EISA: Probing bus 0 at eisa.0
Apr 11 22:55:15 anirban-laptop kernel: [    1.081084] Cannot allocate resource for EISA slot 1
Apr 11 22:55:15 anirban-laptop kernel: [    1.081086] Cannot allocate resource for EISA slot 2
Apr 11 22:55:15 anirban-laptop kernel: [    1.081088] Cannot allocate resource for EISA slot 3
Apr 11 22:55:15 anirban-laptop kernel: [    1.081091] Cannot allocate resource for EISA slot 4
Apr 11 22:55:15 anirban-laptop kernel: [    1.081093] Cannot allocate resource for EISA slot 5
Apr 11 22:55:15 anirban-laptop kernel: [    1.081116] EISA: Detected 0 cards.
Apr 11 22:55:15 anirban-laptop kernel: [    1.081325] cpuidle: using governor ladder
Apr 11 22:55:15 anirban-laptop kernel: [    1.081462] cpuidle: using governor menu
Apr 11 22:55:15 anirban-laptop kernel: [    1.082002] TCP cubic registered
Apr 11 22:55:15 anirban-laptop kernel: [    1.082178] NET: Registered protocol family 10
Apr 11 22:55:15 anirban-laptop kernel: [    1.082693] lo: Disabled Privacy Extensions
Apr 11 22:55:15 anirban-laptop kernel: [    1.083079] NET: Registered protocol family 17
Apr 11 22:55:15 anirban-laptop kernel: [    1.083097] Bluetooth: L2CAP ver 2.13
Apr 11 22:55:15 anirban-laptop kernel: [    1.083099] Bluetooth: L2CAP socket layer initialized
Apr 11 22:55:15 anirban-laptop kernel: [    1.083102] Bluetooth: SCO (Voice Link) ver 0.6
Apr 11 22:55:15 anirban-laptop kernel: [    1.083104] Bluetooth: SCO socket layer initialized
Apr 11 22:55:15 anirban-laptop kernel: [    1.083144] Bluetooth: RFCOMM TTY layer initialized
Apr 11 22:55:15 anirban-laptop kernel: [    1.083148] Bluetooth: RFCOMM socket layer initialized
Apr 11 22:55:15 anirban-laptop kernel: [    1.083150] Bluetooth: RFCOMM ver 1.11
Apr 11 22:55:15 anirban-laptop kernel: [    1.083717] Using IPI No-Shortcut mode
Apr 11 22:55:15 anirban-laptop kernel: [    1.083806] registered taskstats version 1
Apr 11 22:55:15 anirban-laptop kernel: [    1.083923]   Magic number: 6:989:440
Apr 11 22:55:15 anirban-laptop kernel: [    1.083954] pcieport-driver 0000:00:1c.1: hash matches
Apr 11 22:55:15 anirban-laptop kernel: [    1.084052] rtc_cmos 00:05: setting system clock to 2010-04-11 17:24:58 UTC (1271006698)
Apr 11 22:55:15 anirban-laptop kernel: [    1.084055] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 11 22:55:15 anirban-laptop kernel: [    1.084057] EDD information not available.
Apr 11 22:55:15 anirban-laptop kernel: [    1.101891] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr 11 22:55:15 anirban-laptop kernel: [    1.224695] ata4.00: ATAPI: TSSTcorpCDW/DVD TS-L462D, HH08, max MWDMA2
Apr 11 22:55:15 anirban-laptop kernel: [    1.272358] ata4.00: configured for MWDMA2
Apr 11 22:55:15 anirban-laptop kernel: [    1.352103] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 11 22:55:15 anirban-laptop kernel: [    1.354762] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 11 22:55:15 anirban-laptop kernel: [    1.354766] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
Apr 11 22:55:15 anirban-laptop kernel: [    1.356465] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 11 22:55:15 anirban-laptop kernel: [    1.358755] ata1.00: ATA-7: ST980811AS, 3.BHD, max UDMA/100
Apr 11 22:55:15 anirban-laptop kernel: [    1.358759] ata1.00: 156301488 sectors, multi 16: LBA48 
Apr 11 22:55:15 anirban-laptop kernel: [    1.363995] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 11 22:55:15 anirban-laptop kernel: [    1.363999] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
Apr 11 22:55:15 anirban-laptop kernel: [    1.365715] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 11 22:55:15 anirban-laptop kernel: [    1.368032] ata1.00: configured for UDMA/100
Apr 11 22:55:15 anirban-laptop kernel: [    1.384696] ata1.00: configured for UDMA/100
Apr 11 22:55:15 anirban-laptop kernel: [    1.384699] ata1: EH complete
Apr 11 22:55:15 anirban-laptop kernel: [    1.384848] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
Apr 11 22:55:15 anirban-laptop kernel: [    1.384962] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 11 22:55:15 anirban-laptop kernel: [    1.385009] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Apr 11 22:55:15 anirban-laptop kernel: [    1.385070] sd 0:0:0:0: [sda] Write Protect is off
Apr 11 22:55:15 anirban-laptop kernel: [    1.385098] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 11 22:55:15 anirban-laptop kernel: [    1.385234]  sda:
Apr 11 22:55:15 anirban-laptop kernel: [    1.418803] scsi 3:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462D HH08 PQ: 0 ANSI: 5
Apr 11 22:55:15 anirban-laptop kernel: [    1.443899]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 11 22:55:15 anirban-laptop kernel: [    1.444239] Uniform CD-ROM driver Revision: 3.20
Apr 11 22:55:15 anirban-laptop kernel: [    1.444367] sr 3:0:0:0: Attached scsi generic sg1 type 5
Apr 11 22:55:15 anirban-laptop kernel: [    1.470383]  sda5 >
Apr 11 22:55:15 anirban-laptop kernel: [    1.470651] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 11 22:55:15 anirban-laptop kernel: [    1.470694] Freeing unused kernel memory: 540k freed
Apr 11 22:55:15 anirban-laptop kernel: [    1.471079] Write protecting the kernel text: 4580k
Apr 11 22:55:15 anirban-laptop kernel: [    1.471149] Write protecting the kernel read-only data: 1840k
Apr 11 22:55:15 anirban-laptop kernel: [    1.500060] Clocksource tsc unstable (delta = -262428208 ns)
Apr 11 22:55:15 anirban-laptop kernel: [    1.603756] Linux agpgart interface v0.103
Apr 11 22:55:15 anirban-laptop kernel: [    1.607046] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr 11 22:55:15 anirban-laptop kernel: [    1.607722] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr 11 22:55:15 anirban-laptop kernel: [    1.610342] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr 11 22:55:15 anirban-laptop kernel: [    1.686433] [drm] Initialized drm 1.1.0 20060810
Apr 11 22:55:15 anirban-laptop kernel: [    1.690330] tg3.c:v3.99 (April 20, 2009)
Apr 11 22:55:15 anirban-laptop kernel: [    1.690393] tg3 0000:18:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 11 22:55:15 anirban-laptop kernel: [    1.697107] tg3 0000:18:00.0: PME# disabled
Apr 11 22:55:15 anirban-laptop kernel: [    1.701703] usb 6-1: new full speed USB device using uhci_hcd and address 2
Apr 11 22:55:15 anirban-laptop kernel: [    1.702008] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:15 anirban-laptop kernel: [    2.016078] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1a:4b:70:18:d0
Apr 11 22:55:15 anirban-laptop kernel: [    2.016083] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
Apr 11 22:55:15 anirban-laptop kernel: [    2.016086] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
Apr 11 22:55:15 anirban-laptop kernel: [    2.016088] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr 11 22:55:15 anirban-laptop kernel: [    2.147306] usb 6-1: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    2.156506] Initializing USB Mass Storage driver...
Apr 11 22:55:15 anirban-laptop kernel: [    2.158248] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 11 22:55:15 anirban-laptop kernel: [    2.158390] usbcore: registered new interface driver usb-storage
Apr 11 22:55:15 anirban-laptop kernel: [    2.158393] USB Mass Storage support registered.
Apr 11 22:55:15 anirban-laptop kernel: [    2.204199] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:15 anirban-laptop kernel: [    2.328900] [drm] fb0: inteldrmfb frame buffer device
Apr 11 22:55:15 anirban-laptop kernel: [    2.332513] acpi device:02: registered as cooling_device7
Apr 11 22:55:15 anirban-laptop kernel: [    2.333365] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
Apr 11 22:55:15 anirban-laptop kernel: [    2.333396] ACPI: Video Device [C098] (multi-head: yes  rom: no  post: no)
Apr 11 22:55:15 anirban-laptop kernel: [    2.333432] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 11 22:55:15 anirban-laptop kernel: [    2.400361] [drm] LVDS-8: set mode 1280x800 17
Apr 11 22:55:15 anirban-laptop kernel: [    2.497113] usb 6-1: USB disconnect, address 2
Apr 11 22:55:15 anirban-laptop kernel: [    2.626352] Console: switching to colour frame buffer device 160x50
Apr 11 22:55:15 anirban-laptop kernel: [    2.741041] usb 6-1: new full speed USB device using uhci_hcd and address 3
Apr 11 22:55:15 anirban-laptop kernel: [    2.929338] usb 6-1: configuration #1 chosen from 1 choice
Apr 11 22:55:15 anirban-laptop kernel: [    2.939300] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 11 22:55:15 anirban-laptop kernel: [    2.954918] PM: Starting manual resume from disk
Apr 11 22:55:15 anirban-laptop kernel: [    2.958369] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Apr 11 22:55:15 anirban-laptop kernel: [    2.958373] EXT4-fs (sda1): write access will be enabled during recovery
Apr 11 22:55:15 anirban-laptop kernel: [    2.982938] EXT4-fs (sda1): barriers enabled
Apr 11 22:55:15 anirban-laptop kernel: [    6.132037] kjournald2 starting: pid 432, dev sda1:8, commit interval 5 seconds
Apr 11 22:55:15 anirban-laptop kernel: [    6.132188] EXT4-fs (sda1): delayed allocation enabled
Apr 11 22:55:15 anirban-laptop kernel: [    6.132193] EXT4-fs: file extents enabled
Apr 11 22:55:15 anirban-laptop kernel: [    6.136237] EXT4-fs: mballoc enabled
Apr 11 22:55:15 anirban-laptop kernel: [    6.136253] EXT4-fs (sda1): orphan cleanup on readonly fs
Apr 11 22:55:15 anirban-laptop kernel: [    6.136468] EXT4-fs (sda1): 9 orphan inodes deleted
Apr 11 22:55:15 anirban-laptop kernel: [    6.136472] EXT4-fs (sda1): recovery complete
Apr 11 22:55:15 anirban-laptop kernel: [    6.196849] EXT4-fs (sda1): mounted filesystem with ordered data mode
Apr 11 22:55:15 anirban-laptop kernel: [    7.121454] type=1505 audit(1271006704.536:2): operation="profile_load" pid=457 name=/usr/share/gdm/guest-session/Xsession
Apr 11 22:55:15 anirban-laptop kernel: [    7.123835] type=1505 audit(1271006704.536:3): operation="profile_load" pid=458 name=/sbin/dhclient3
Apr 11 22:55:15 anirban-laptop kernel: [    7.124631] type=1505 audit(1271006704.540:4): operation="profile_load" pid=458 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 11 22:55:15 anirban-laptop kernel: [    7.125043] type=1505 audit(1271006704.540:5): operation="profile_load" pid=458 name=/usr/lib/connman/scripts/dhclient-script
Apr 11 22:55:15 anirban-laptop kernel: [    7.216098] type=1505 audit(1271006704.632:6): operation="profile_load" pid=459 name=/usr/bin/evince
Apr 11 22:55:15 anirban-laptop kernel: [    7.228086] type=1505 audit(1271006704.644:7): operation="profile_load" pid=459 name=/usr/bin/evince-previewer
Apr 11 22:55:15 anirban-laptop kernel: [    7.235078] type=1505 audit(1271006704.648:8): operation="profile_load" pid=459 name=/usr/bin/evince-thumbnailer
Apr 11 22:55:15 anirban-laptop kernel: [    7.297116] type=1505 audit(1271006704.712:9): operation="profile_load" pid=461 name=/usr/bin/freshclam
Apr 11 22:55:15 anirban-laptop kernel: [    7.323115] type=1505 audit(1271006704.736:10): operation="profile_load" pid=462 name=/usr/sbin/clamd
Apr 11 22:55:15 anirban-laptop kernel: [    7.332880] type=1505 audit(1271006704.748:11): operation="profile_load" pid=463 name=/usr/lib/cups/backend/cups-pdf
Apr 11 22:55:15 anirban-laptop kernel: [    7.940283] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Apr 11 22:55:15 anirban-laptop kernel: [    7.943264] scsi 9:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Apr 11 22:55:15 anirban-laptop kernel: [    7.959246] sr1: scsi-1 drive
Apr 11 22:55:15 anirban-laptop kernel: [    7.959420] sr 9:0:0:0: Attached scsi generic sg2 type 5
Apr 11 22:55:15 anirban-laptop kernel: [    7.959523] sd 9:0:0:1: Attached scsi generic sg3 type 0
Apr 11 22:55:15 anirban-laptop kernel: [    7.969264] sd 9:0:0:1: [sdb] Attached SCSI removable disk
Apr 11 22:55:15 anirban-laptop kernel: [   15.219248] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k 
Apr 11 22:55:15 anirban-laptop kernel: [   15.256547] EXT4-fs (sda1): internal journal on sda1:8
Apr 11 22:55:15 anirban-laptop kernel: [   15.393424] udev: starting version 147
Apr 11 22:55:15 anirban-laptop kernel: [   16.509103] usbcore: registered new interface driver usbserial
Apr 11 22:55:15 anirban-laptop kernel: [   16.509120] USB Serial support registered for generic
Apr 11 22:55:15 anirban-laptop kernel: [   16.509166] usbcore: registered new interface driver usbserial_generic
Apr 11 22:55:15 anirban-laptop kernel: [   16.509169] usbserial: USB Serial Driver core
Apr 11 22:55:15 anirban-laptop kernel: [   16.511428] USB Serial support registered for GSM modem (1-port)
Apr 11 22:55:15 anirban-laptop kernel: [   16.511469] option 6-1:1.0: GSM modem (1-port) converter detected
Apr 11 22:55:15 anirban-laptop kernel: [   16.511549] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Apr 11 22:55:15 anirban-laptop kernel: [   16.511561] option 6-1:1.1: GSM modem (1-port) converter detected
Apr 11 22:55:15 anirban-laptop kernel: [   16.511614] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 11 22:55:15 anirban-laptop kernel: [   16.511625] option 6-1:1.2: GSM modem (1-port) converter detected
Apr 11 22:55:15 anirban-laptop kernel: [   16.511683] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
Apr 11 22:55:15 anirban-laptop kernel: [   16.511702] usbcore: registered new interface driver option
Apr 11 22:55:15 anirban-laptop kernel: [   16.511704] option: v0.7.2:USB Driver for GSM modems
Apr 11 22:55:15 anirban-laptop kernel: [   16.577954] lp: driver loaded but no devices found
Apr 11 22:55:15 anirban-laptop kernel: [   16.609117] cfg80211: Calling CRDA to update world regulatory domain
Apr 11 22:55:15 anirban-laptop kernel: [   16.813264] cfg80211: World regulatory domain updated:
Apr 11 22:55:15 anirban-laptop kernel: [   16.813267]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 11 22:55:15 anirban-laptop kernel: [   16.813270]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 22:55:15 anirban-laptop kernel: [   16.813273]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 11 22:55:15 anirban-laptop kernel: [   16.813275]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 11 22:55:15 anirban-laptop kernel: [   16.813278]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 22:55:15 anirban-laptop kernel: [   16.813280]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 22:55:15 anirban-laptop kernel: [   17.086534] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:30c0]
Apr 11 22:55:15 anirban-laptop kernel: [   17.129245] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 11 22:55:15 anirban-laptop kernel: [   17.212841] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0cb8, PCI irq 16
Apr 11 22:55:15 anirban-laptop kernel: [   17.212849] yenta_cardbus 0000:02:04.0: Socket status: 30000006
Apr 11 22:55:15 anirban-laptop kernel: [   17.212853] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
Apr 11 22:55:15 anirban-laptop kernel: [   17.212864] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
Apr 11 22:55:15 anirban-laptop kernel: [   17.212868] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
Apr 11 22:55:15 anirban-laptop kernel: [   17.213136] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xe4200000 - 0xe42fffff
Apr 11 22:55:15 anirban-laptop kernel: [   17.213140] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
Apr 11 22:55:15 anirban-laptop kernel: [   17.506347] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Apr 11 22:55:15 anirban-laptop kernel: [   17.506351] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Apr 11 22:55:15 anirban-laptop kernel: [   17.506477] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 11 22:55:15 anirban-laptop kernel: [   17.576544] iwl3945 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr 11 22:55:15 anirban-laptop kernel: [   17.576547] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr 11 22:55:15 anirban-laptop kernel: [   17.625709] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
Apr 11 22:55:15 anirban-laptop kernel: [   17.625715] serio: Synaptics pass-through port at isa0060/serio4/input0
Apr 11 22:55:15 anirban-laptop kernel: [   17.668377] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
Apr 11 22:55:15 anirban-laptop kernel: [   18.076173] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Apr 11 22:55:15 anirban-laptop kernel: [   18.078540] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Apr 11 22:55:15 anirban-laptop kernel: [   18.079513] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Apr 11 22:55:15 anirban-laptop kernel: [   18.080339] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Apr 11 22:55:15 anirban-laptop kernel: [   18.081345] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Apr 11 22:55:16 anirban-laptop kernel: [   18.808910] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Apr 11 22:55:16 anirban-laptop kernel: [   18.808923] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 11 22:55:16 anirban-laptop kernel: [   19.129739] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Apr 11 22:55:19 anirban-laptop kernel: [   21.952743] tg3 0000:18:00.0: PME# disabled
Apr 11 22:55:19 anirban-laptop kernel: [   22.005716] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 11 22:55:20 anirban-laptop kernel: [   23.102495] __ratelimit: 9 callbacks suppressed
Apr 11 22:55:20 anirban-laptop kernel: [   23.102498] type=1505 audit(1271006720.517:15): operation="profile_replace" pid=1135 name=/usr/share/gdm/guest-session/Xsession
Apr 11 22:55:20 anirban-laptop kernel: [   23.104130] type=1505 audit(1271006720.517:16): operation="profile_replace" pid=1136 name=/sbin/dhclient3
Apr 11 22:55:20 anirban-laptop kernel: [   23.104954] type=1505 audit(1271006720.517:17): operation="profile_replace" pid=1136 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 11 22:55:20 anirban-laptop kernel: [   23.105389] type=1505 audit(1271006720.521:18): operation="profile_replace" pid=1136 name=/usr/lib/connman/scripts/dhclient-script
Apr 11 22:55:20 anirban-laptop kernel: [   23.109188] type=1505 audit(1271006720.525:19): operation="profile_replace" pid=1137 name=/usr/bin/evince
Apr 11 22:55:20 anirban-laptop kernel: [   23.122321] type=1505 audit(1271006720.536:20): operation="profile_replace" pid=1137 name=/usr/bin/evince-previewer
Apr 11 22:55:20 anirban-laptop kernel: [   23.129322] type=1505 audit(1271006720.544:21): operation="profile_replace" pid=1137 name=/usr/bin/evince-thumbnailer
Apr 11 22:55:20 anirban-laptop kernel: [   23.139518] type=1505 audit(1271006720.552:22): operation="profile_replace" pid=1139 name=/usr/bin/freshclam
Apr 11 22:55:20 anirban-laptop kernel: [   23.141512] type=1505 audit(1271006720.556:23): operation="profile_replace" pid=1140 name=/usr/sbin/clamd
Apr 11 22:55:20 anirban-laptop kernel: [   23.143402] type=1505 audit(1271006720.556:24): operation="profile_replace" pid=1141 name=/usr/lib/cups/backend/cups-pdf
Apr 11 22:55:22 anirban-laptop squid[1293]: Squid Parent: child process 1295 started
Apr 11 22:55:22 anirban-laptop kernel: [   25.443935] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:23 anirban-laptop kernel: [   25.585624] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:23 anirban-laptop kernel: [   25.923845] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:23 anirban-laptop kernel: [   26.071224] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:26 anirban-laptop kernel: [   29.266389] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:55:26 anirban-laptop kernel: [   29.266393] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:55:26 anirban-laptop kernel: [   29.266397] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:55:26 anirban-laptop kernel: [   29.266403] Info fld=0x0
Apr 11 22:55:26 anirban-laptop kernel: [   29.266405] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 11 22:55:26 anirban-laptop kernel: [   29.266415] __ratelimit: 9 callbacks suppressed
Apr 11 22:55:26 anirban-laptop kernel: [   29.527801] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:27 anirban-laptop kernel: [   29.667796] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:27 anirban-laptop kernel: [   29.935895] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:27 anirban-laptop kernel: [   30.076201] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:27 anirban-laptop kernel: [   30.355875] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:27 anirban-laptop kernel: [   30.496197] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:31 anirban-laptop kernel: [   34.477240] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 11 22:55:32 anirban-laptop kernel: [   35.422584] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:55:32 anirban-laptop kernel: [   35.422589] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:55:32 anirban-laptop kernel: [   35.422593] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:55:32 anirban-laptop kernel: [   35.422599] Info fld=0x0
Apr 11 22:55:32 anirban-laptop kernel: [   35.422601] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 22:55:39 anirban-laptop kernel: [   41.633801] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:55:39 anirban-laptop kernel: [   41.633805] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:55:39 anirban-laptop kernel: [   41.633809] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:55:39 anirban-laptop kernel: [   41.633815] Info fld=0x0
Apr 11 22:55:39 anirban-laptop kernel: [   41.633817] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 22:55:45 anirban-laptop kernel: [   47.616975] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:45 anirban-laptop kernel: [   47.689026] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:55:45 anirban-laptop kernel: [   47.689029] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:55:45 anirban-laptop kernel: [   47.689034] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:55:45 anirban-laptop kernel: [   47.689039] Info fld=0x0
Apr 11 22:55:45 anirban-laptop kernel: [   47.689041] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 11 22:55:45 anirban-laptop kernel: [   47.759821] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:45 anirban-laptop kernel: [   48.039048] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:45 anirban-laptop kernel: [   48.179632] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:45 anirban-laptop kernel: [   48.488052] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:46 anirban-laptop kernel: [   48.635445] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:46 anirban-laptop kernel: [   49.039004] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:46 anirban-laptop kernel: [   49.178989] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:48 anirban-laptop kernel: [   50.652892] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:48 anirban-laptop kernel: [   50.796080] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:48 anirban-laptop kernel: [   51.063739] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:48 anirban-laptop kernel: [   51.203935] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:48 anirban-laptop kernel: [   51.467716] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:49 anirban-laptop kernel: [   51.607800] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:49 anirban-laptop kernel: [   51.878996] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:49 anirban-laptop kernel: [   52.019009] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:49 anirban-laptop kernel: [   52.297679] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:49 anirban-laptop kernel: [   52.441124] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:50 anirban-laptop kernel: [   52.715753] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:50 anirban-laptop kernel: [   52.855991] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:50 anirban-laptop kernel: [   53.123764] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:50 anirban-laptop kernel: [   53.264027] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:50 anirban-laptop kernel: [   53.551012] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:51 anirban-laptop kernel: [   53.692586] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:51 anirban-laptop kernel: [   54.083945] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:51 anirban-laptop kernel: [   54.225027] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:52 anirban-laptop kernel: [   54.627635] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:52 anirban-laptop kernel: [   54.770598] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:52 anirban-laptop kernel: [   54.870301] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:55:52 anirban-laptop kernel: [   54.870304] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:55:52 anirban-laptop kernel: [   54.870309] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:55:52 anirban-laptop kernel: [   54.870314] Info fld=0x0
Apr 11 22:55:52 anirban-laptop kernel: [   54.870316] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 11 22:55:52 anirban-laptop kernel: [   55.159568] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:52 anirban-laptop kernel: [   55.300892] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:53 anirban-laptop kernel: [   55.683865] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:53 anirban-laptop kernel: [   55.823986] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:55:58 anirban-laptop kernel: [   60.933763] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:55:58 anirban-laptop kernel: [   60.933768] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:55:58 anirban-laptop kernel: [   60.933772] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:55:58 anirban-laptop kernel: [   60.933778] Info fld=0x0
Apr 11 22:55:58 anirban-laptop kernel: [   60.933780] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 11 22:56:02 anirban-laptop kernel: [   65.107281] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:56:02 anirban-laptop kernel: [   65.247925] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:56:02 anirban-laptop kernel: [   65.518881] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:56:03 anirban-laptop kernel: [   65.658959] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:56:03 anirban-laptop kernel: [   65.926961] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:56:03 anirban-laptop kernel: [   66.067340] [drm] TV-14: set mode NTSC 480i 0
Apr 11 22:56:04 anirban-laptop kernel: [   66.959860] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:56:04 anirban-laptop kernel: [   66.959865] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:56:04 anirban-laptop kernel: [   66.959869] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:56:04 anirban-laptop kernel: [   66.959875] Info fld=0x0
Apr 11 22:56:04 anirban-laptop kernel: [   66.959877] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 11 22:56:10 anirban-laptop kernel: [   73.138488] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 11 22:56:10 anirban-laptop kernel: [   73.138493] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 22:56:10 anirban-laptop kernel: [   73.138497] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 11 22:56:10 anirban-laptop kernel: [   73.138503] Info fld=0x0
Apr 11 22:56:10 anirban-laptop kernel: [   73.138505] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 11 22:56:37 anirban-laptop kernel: [   99.624051] CE: hpet increasing min_delta_ns to 22500 nsec
Apr 11 22:56:37 anirban-laptop kernel: [   99.765146] UDF-fs: Filesystem marked read-only because writing to pseudooverwrite partition is not implemented.
Apr 11 22:56:37 anirban-laptop kernel: [   99.839845] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2010/03/30 11:51 (114a)
Apr 11 22:56:55 anirban-laptop pppd[2019]: pppd 2.4.5 started by root, uid 0
Apr 11 22:56:55 anirban-laptop pppd[2019]: Using interface ppp0
Apr 11 22:56:55 anirban-laptop pppd[2019]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 11 22:56:57 anirban-laptop pppd[2019]: CHAP authentication succeeded
Apr 11 22:56:57 anirban-laptop pppd[2019]: CHAP authentication succeeded
Apr 11 22:56:57 anirban-laptop kernel: [  120.301313] PPP BSD Compression module registered
Apr 11 22:56:57 anirban-laptop kernel: [  120.330585] PPP Deflate Compression module registered
Apr 11 22:56:58 anirban-laptop pppd[2019]: local  IP address 219.64.78.177
Apr 11 22:56:58 anirban-laptop pppd[2019]: remote IP address 172.29.243.161
Apr 11 22:56:58 anirban-laptop pppd[2019]: primary   DNS address 203.200.230.244
Apr 11 22:56:58 anirban-laptop pppd[2019]: secondary DNS address 202.54.29.5
Apr 11 23:04:20 anirban-laptop pppd[2019]: Terminating on signal 15
Apr 11 23:04:20 anirban-laptop pppd[2019]: Connect time 7.4 minutes.
Apr 11 23:04:20 anirban-laptop pppd[2019]: Sent 210436 bytes, received 1136762 bytes.
Apr 11 23:05:05 anirban-laptop kernel: [  607.768111] usb 6-1: USB disconnect, address 3
Apr 11 23:05:05 anirban-laptop kernel: [  607.769464] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Apr 11 23:05:05 anirban-laptop kernel: [  607.769490] option 6-1:1.0: device disconnected
Apr 11 23:05:05 anirban-laptop kernel: [  607.769581] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Apr 11 23:05:05 anirban-laptop kernel: [  607.769597] option 6-1:1.1: device disconnected
Apr 11 23:05:05 anirban-laptop kernel: [  607.769685] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Apr 11 23:05:05 anirban-laptop kernel: [  607.769700] option 6-1:1.2: device disconnected
Apr 11 23:05:15 anirban-laptop kernel: [  618.024079] usb 6-1: new full speed USB device using uhci_hcd and address 4
Apr 11 23:05:15 anirban-laptop kernel: [  618.240229] usb 6-1: configuration #1 chosen from 1 choice
Apr 11 23:05:15 anirban-laptop kernel: [  618.244134] scsi10 : SCSI emulation for USB Mass Storage devices
Apr 11 23:05:15 anirban-laptop kernel: [  618.488103] usb 6-1: USB disconnect, address 4
Apr 11 23:05:16 anirban-laptop kernel: [  618.728064] usb 6-1: new full speed USB device using uhci_hcd and address 5
Apr 11 23:05:16 anirban-laptop kernel: [  618.887232] usb 6-1: configuration #1 chosen from 1 choice
Apr 11 23:05:16 anirban-laptop kernel: [  618.893261] option 6-1:1.0: GSM modem (1-port) converter detected
Apr 11 23:05:16 anirban-laptop kernel: [  618.893344] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Apr 11 23:05:16 anirban-laptop kernel: [  618.895593] option 6-1:1.1: GSM modem (1-port) converter detected
Apr 11 23:05:16 anirban-laptop kernel: [  618.895683] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 11 23:05:16 anirban-laptop kernel: [  618.902963] option 6-1:1.2: GSM modem (1-port) converter detected
Apr 11 23:05:16 anirban-laptop kernel: [  618.903058] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
Apr 11 23:05:16 anirban-laptop kernel: [  618.904352] scsi14 : SCSI emulation for USB Mass Storage devices
Apr 11 23:05:21 anirban-laptop kernel: [  623.912174] scsi 14:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Apr 11 23:05:21 anirban-laptop kernel: [  623.915156] scsi 14:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Apr 11 23:05:21 anirban-laptop kernel: [  623.944131] sr1: scsi-1 drive
Apr 11 23:05:21 anirban-laptop kernel: [  623.944338] sr 14:0:0:0: Attached scsi generic sg2 type 5
Apr 11 23:05:21 anirban-laptop kernel: [  623.944446] sd 14:0:0:1: Attached scsi generic sg3 type 0
Apr 11 23:05:21 anirban-laptop kernel: [  623.971489] sd 14:0:0:1: [sdb] Attached SCSI removable disk
Apr 11 23:05:22 anirban-laptop kernel: [  625.359136] sr 14:0:0:0: [sr1] Device not ready
Apr 11 23:05:22 anirban-laptop kernel: [  625.359141] sr 14:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 23:05:22 anirban-laptop kernel: [  625.359145] sr 14:0:0:0: [sr1] Sense Key : Not Ready [current] 
Apr 11 23:05:22 anirban-laptop kernel: [  625.359151] sr 14:0:0:0: [sr1] Add. Sense: Medium not present
Apr 11 23:05:22 anirban-laptop kernel: [  625.371139] sr 14:0:0:0: [sr1] Device not ready
Apr 11 23:05:22 anirban-laptop kernel: [  625.371142] sr 14:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 23:05:22 anirban-laptop kernel: [  625.371146] sr 14:0:0:0: [sr1] Sense Key : Not Ready [current] 
Apr 11 23:05:22 anirban-laptop kernel: [  625.371150] sr 14:0:0:0: [sr1] Add. Sense: Medium not present
Apr 11 23:05:22 anirban-laptop kernel: [  625.381139] sr 14:0:0:0: [sr1] Device not ready
Apr 11 23:05:22 anirban-laptop kernel: [  625.381142] sr 14:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 23:05:22 anirban-laptop kernel: [  625.381146] sr 14:0:0:0: [sr1] Sense Key : Not Ready [current] 
Apr 11 23:05:22 anirban-laptop kernel: [  625.381150] sr 14:0:0:0: [sr1] Add. Sense: Medium not present
Apr 11 23:05:22 anirban-laptop kernel: [  625.393139] sr 14:0:0:0: [sr1] Device not ready
Apr 11 23:05:22 anirban-laptop kernel: [  625.393141] sr 14:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 23:05:22 anirban-laptop kernel: [  625.393145] sr 14:0:0:0: [sr1] Sense Key : Not Ready [current] 
Apr 11 23:05:22 anirban-laptop kernel: [  625.393149] sr 14:0:0:0: [sr1] Add. Sense: Medium not present
Apr 11 23:05:22 anirban-laptop kernel: [  625.393195] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.393213] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.393231] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.393250] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.393268] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.393288] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.393312] sr 14:0:0:0: [sr1] unaligned transfer
Apr 11 23:05:22 anirban-laptop kernel: [  625.405122] sr 14:0:0:0: [sr1] Device not ready
Apr 11 23:05:22 anirban-laptop kernel: [  625.405125] sr 14:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 23:05:22 anirban-laptop kernel: [  625.405129] sr 14:0:0:0: [sr1] Sense Key : Not Ready [current] 
Apr 11 23:05:22 anirban-laptop kernel: [  625.405134] sr 14:0:0:0: [sr1] Add. Sense: Medium not present
Apr 11 23:05:22 anirban-laptop kernel: [  625.417142] sr 14:0:0:0: [sr1] Device not ready
Apr 11 23:05:22 anirban-laptop kernel: [  625.417146] sr 14:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 11 23:05:22 anirban-laptop kernel: [  625.417151] sr 14:0:0:0: [sr1] Sense Key : Not Ready [current] 
Apr 11 23:05:22 anirban-laptop kernel: [  625.417156] sr 14:0:0:0: [sr1] Add. Sense: Medium not present
Apr 11 23:05:42 anirban-laptop pppd[2510]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Apr 11 23:05:42 anirban-laptop pppd[2510]: pppd 2.4.5 started by root, uid 0
Apr 11 23:05:42 anirban-laptop pppd[2510]: Using interface ppp0
Apr 11 23:05:42 anirban-laptop pppd[2510]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 11 23:05:42 anirban-laptop pppd[2510]: CHAP authentication succeeded
Apr 11 23:05:42 anirban-laptop pppd[2510]: CHAP authentication succeeded
Apr 11 23:05:43 anirban-laptop pppd[2510]: local  IP address 115.117.212.1
Apr 11 23:05:43 anirban-laptop pppd[2510]: remote IP address 172.29.243.161
Apr 11 23:05:43 anirban-laptop pppd[2510]: primary   DNS address 203.200.230.244
Apr 11 23:05:43 anirban-laptop pppd[2510]: secondary DNS address 202.54.29.5
Apr 11 23:06:36 anirban-laptop pppd[2510]: Terminating on signal 15
Apr 11 23:06:36 anirban-laptop pppd[2510]: Connect time 0.9 minutes.
Apr 11 23:06:36 anirban-laptop pppd[2510]: Sent 28047 bytes, received 47421 bytes.
Apr 11 23:07:43 anirban-laptop pppd[2660]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Apr 11 23:07:43 anirban-laptop pppd[2660]: pppd 2.4.5 started by root, uid 0
Apr 11 23:07:43 anirban-laptop pppd[2660]: Removed stale lock on ttyUSB0 (pid 2510)
Apr 11 23:07:43 anirban-laptop pppd[2660]: Using interface ppp0
Apr 11 23:07:43 anirban-laptop pppd[2660]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 11 23:07:46 anirban-laptop pppd[2660]: CHAP authentication succeeded
Apr 11 23:07:46 anirban-laptop pppd[2660]: CHAP authentication succeeded
Apr 11 23:07:46 anirban-laptop pppd[2660]: local  IP address 115.117.234.84
Apr 11 23:07:46 anirban-laptop pppd[2660]: remote IP address 172.29.243.161
Apr 11 23:07:46 anirban-laptop pppd[2660]: primary   DNS address 203.200.230.244
Apr 11 23:07:46 anirban-laptop pppd[2660]: secondary DNS address 202.54.29.5
Apr 12 02:36:02 anirban-laptop kernel: [13256.771922] [drm] TV-14: set mode NTSC 480i 0
Apr 12 02:36:02 anirban-laptop kernel: [13256.911978] [drm] TV-14: set mode NTSC 480i 0
Apr 12 02:36:43 anirban-laptop pulseaudio[1814]: ratelimit.c: 117 events suppressed
Apr 12 02:49:51 anirban-laptop kernel: [14085.988954] ata4: lost interrupt (Status 0x58)
Apr 12 02:49:51 anirban-laptop kernel: [14086.105824] ata4: soft resetting link
Apr 12 02:49:51 anirban-laptop kernel: [14086.332330] ata4.00: configured for MWDMA2
Apr 12 02:49:52 anirban-laptop kernel: [14086.344764] ata4: EH complete
Apr 12 03:12:30 anirban-laptop kernel: Kernel logging (proc) stopped.
Apr 12 10:29:35 anirban-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr 12 10:29:35 anirban-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="837" x-info="http://www.rsyslog.com"] (re)start
Apr 12 10:29:35 anirban-laptop rsyslogd: rsyslogd's groupid changed to 102
Apr 12 10:29:36 anirban-laptop rsyslogd: rsyslogd's userid changed to 101
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] KERNEL supported cpus:
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   Intel GenuineIntel
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   AMD AuthenticAMD
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   NSC Geode by NSC
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   Centaur CentaurHauls
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7b0000 (usable)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7b0000 - 000000001f7c5400 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7c5400 - 000000001f7e7fb8 (ACPI NVS)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 000000001f7e7fb8 - 0000000020000000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9a000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] DMI 2.4 present.
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] last_pfn = 0x1f7b0 max_arch_pfn = 0x100000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] modified physical RAM map:
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000001f7b0000 (usable)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 000000001f7b0000 - 000000001f7c5400 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 000000001f7c5400 - 000000001f7e7fb8 (ACPI NVS)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 000000001f7e7fb8 - 0000000020000000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed9a000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f7b0000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] RAMDISK: 172ba000 - 17a03e54
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: RSDP 000fc600 00024 (v02 HP    )
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: XSDT 1f7c81c8 0007C (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: FACP 1f7c8084 000F4 (v04 HP     30C0     00000003 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: DSDT 1f7c84cc 12C10 (v01 HP       nc75xx 00010000 MSFT 03000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: FACS 1f7e7d80 00040
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: SLIC 1f7c8244 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: HPET 1f7c83bc 00038 (v01 HP     30C0     00000001 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: APIC 1f7c83f4 00068 (v01 HP     30C0     00000001 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: MCFG 1f7c845c 0003C (v01 HP     30C0     00000001 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: TCPA 1f7c8498 00032 (v02 HP     30C0     00000001 HP   00000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7db0dc 00059 (v01 HP       HPQNLP 00000001 MSFT 03000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7db135 00328 (v01 HP       HPQSAT 00000001 MSFT 03000001)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbca1 0025F (v01 HP      Cpu0Tst 00003000 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbf00 000A6 (v01 HP      Cpu1Tst 00003000 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: SSDT 1f7dbfa6 004D7 (v01 HP        CpuPm 00003000 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] 503MB LOWMEM available.
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   mapped low ram: 0 - 1f7b0000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   low ram: 0 - 1f7b0000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 1f7b0000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bef8
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f7b0000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #4 [00172ba000 - 0017a03e54]          RAMDISK ==> [00172ba000 - 0017a03e54]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #6 [00008ae000 - 00008b10f4]              BRK ==> [00008ae000 - 00008b10f4]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f7b0
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]   HighMem  0x0001f7b0 -> 0x0001f7b0
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0001f7b0
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Using APIC driver default
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127835
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=f2551907-f2d8-4fca-9c65-db29c6645b41 ro quiet quiet splash
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Initializing CPU#0
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] allocated 2578880 bytes of page_cgroup
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Memory: 492544k/515776k available (4578k kernel code, 22444k reserved, 2146k data, 540k init, 0k highmem)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] virtual kernel memory layout:
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     vmalloc : 0xdffb0000 - 0xff7fe000   ( 504 MB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf7b0000   ( 503 MB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Extended CMOS year: 2000
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Apr 12 10:29:36 anirban-laptop kernel: [    0.000000] Detected 1795.691 MHz processor.
Apr 12 10:29:36 anirban-laptop kernel: [    0.001327] Console: colour VGA+ 80x25
Apr 12 10:29:36 anirban-laptop kernel: [    0.001330] console [tty0] enabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.001509] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 12 10:29:36 anirban-laptop kernel: [    0.001514] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.38 BogoMIPS (lpj=7182764)
Apr 12 10:29:36 anirban-laptop kernel: [    0.001529] Security Framework initialized
Apr 12 10:29:36 anirban-laptop kernel: [    0.001545] AppArmor: AppArmor initialized
Apr 12 10:29:36 anirban-laptop kernel: [    0.001551] Mount-cache hash table entries: 512
Apr 12 10:29:36 anirban-laptop kernel: [    0.001655] Initializing cgroup subsys ns
Apr 12 10:29:36 anirban-laptop kernel: [    0.001659] Initializing cgroup subsys cpuacct
Apr 12 10:29:36 anirban-laptop kernel: [    0.001663] Initializing cgroup subsys memory
Apr 12 10:29:36 anirban-laptop kernel: [    0.001669] Initializing cgroup subsys freezer
Apr 12 10:29:36 anirban-laptop kernel: [    0.001672] Initializing cgroup subsys net_cls
Apr 12 10:29:36 anirban-laptop kernel: [    0.001684] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 12 10:29:36 anirban-laptop kernel: [    0.001686] CPU: L2 cache: 2048K
Apr 12 10:29:36 anirban-laptop kernel: [    0.001689] CPU: Physical Processor ID: 0
Apr 12 10:29:36 anirban-laptop kernel: [    0.001690] CPU: Processor Core ID: 0
Apr 12 10:29:36 anirban-laptop kernel: [    0.001694] mce: CPU supports 6 MCE banks
Apr 12 10:29:36 anirban-laptop kernel: [    0.001703] using mwait in idle threads.
Apr 12 10:29:36 anirban-laptop kernel: [    0.001708] Performance Counters: Core2 events, Intel PMU driver.
Apr 12 10:29:36 anirban-laptop kernel: [    0.001724] ... version:                 2
Apr 12 10:29:36 anirban-laptop kernel: [    0.001725] ... bit width:               40
Apr 12 10:29:36 anirban-laptop kernel: [    0.001727] ... generic counters:        2
Apr 12 10:29:36 anirban-laptop kernel: [    0.001729] ... value mask:              000000ffffffffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.001731] ... max period:              000000007fffffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.001733] ... fixed-purpose counters:  3
Apr 12 10:29:36 anirban-laptop kernel: [    0.001734] ... counter mask:            0000000700000003
Apr 12 10:29:36 anirban-laptop kernel: [    0.001738] Checking 'hlt' instruction... OK.
Apr 12 10:29:36 anirban-laptop kernel: [    0.018521] ACPI: Core revision 20090521
Apr 12 10:29:36 anirban-laptop kernel: [    0.044435] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 12 10:29:36 anirban-laptop kernel: [    0.084145] CPU0: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
Apr 12 10:29:36 anirban-laptop kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] Initializing CPU#1
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3590.97 BogoMIPS (lpj=7181956)
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] mce: CPU supports 6 MCE banks
Apr 12 10:29:36 anirban-laptop kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Apr 12 10:29:36 anirban-laptop kernel: [    0.173544] CPU1: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
Apr 12 10:29:36 anirban-laptop kernel: [    0.173562] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 12 10:29:36 anirban-laptop kernel: [    0.176025] Brought up 2 CPUs
Apr 12 10:29:36 anirban-laptop kernel: [    0.176028] Total of 2 processors activated (7182.36 BogoMIPS).
Apr 12 10:29:36 anirban-laptop kernel: [    0.176185] Booting paravirtualized kernel on bare hardware
Apr 12 10:29:36 anirban-laptop kernel: [    0.176232] regulator: core version 0.5
Apr 12 10:29:36 anirban-laptop kernel: [    0.176232] Time:  4:59:21  Date: 04/12/10
Apr 12 10:29:36 anirban-laptop kernel: [    0.176232] NET: Registered protocol family 16
Apr 12 10:29:36 anirban-laptop kernel: [    0.176235] EISA bus registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.176245] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Apr 12 10:29:36 anirban-laptop kernel: [    0.176248] ACPI: bus type pci registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.176328] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Apr 12 10:29:36 anirban-laptop kernel: [    0.176332] PCI: Not using MMCONFIG.
Apr 12 10:29:36 anirban-laptop kernel: [    0.177435] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=40
Apr 12 10:29:36 anirban-laptop kernel: [    0.177437] PCI: Using configuration type 1 for base access
Apr 12 10:29:36 anirban-laptop kernel: [    0.180757] bio: create slab <bio-0> at 0
Apr 12 10:29:36 anirban-laptop kernel: [    0.207052] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 12 10:29:36 anirban-laptop kernel: [    0.236289] ACPI: Interpreter enabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.236297] ACPI: (supports S0 S3 S4 S5)
Apr 12 10:29:36 anirban-laptop kernel: [    0.236317] ACPI: Using IOAPIC for interrupt routing
Apr 12 10:29:36 anirban-laptop kernel: [    0.236374] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Apr 12 10:29:36 anirban-laptop kernel: [    0.243656] PCI: MCFG area at f8000000 reserved in ACPI motherboard resources
Apr 12 10:29:36 anirban-laptop kernel: [    0.243659] PCI: Using MMCONFIG for extended config space
Apr 12 10:29:36 anirban-laptop kernel: [    0.254672] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Apr 12 10:29:36 anirban-laptop kernel: [    0.254675] ACPI: EC: driver started in interrupt mode
Apr 12 10:29:36 anirban-laptop kernel: [    0.254755] ACPI: Power Resource [C29B] (on)
Apr 12 10:29:36 anirban-laptop kernel: [    0.254809] ACPI: Power Resource [C1C5] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.254914] ACPI: Power Resource [C3B7] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.255016] ACPI: Power Resource [C3B8] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.255114] ACPI: Power Resource [C3B9] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.255211] ACPI: Power Resource [C3BA] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.255309] ACPI: Power Resource [C3BB] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.255726] ACPI: No dock devices found.
Apr 12 10:29:36 anirban-laptop kernel: [    0.260025] ACPI: PCI Root Bridge [C003] (0000:00)
Apr 12 10:29:36 anirban-laptop kernel: [    0.260922] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.260932] pci 0000:00:1a.7: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.261214] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.261223] pci 0000:00:1b.0: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.261443] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.261451] pci 0000:00:1c.0: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.261665] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.261675] pci 0000:00:1c.1: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.261892] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.261902] pci 0000:00:1c.2: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.262118] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.262125] pci 0000:00:1c.4: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.262927] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.262937] pci 0000:00:1d.7: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.263311] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 12 10:29:36 anirban-laptop kernel: [    0.263318] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
Apr 12 10:29:36 anirban-laptop kernel: [    0.263325] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 007f)
Apr 12 10:29:36 anirban-laptop kernel: [    0.263339] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 02e8 (mask 0007)
Apr 12 10:29:36 anirban-laptop kernel: [    0.263901] pci 0000:00:1f.2: PME# supported from D3hot
Apr 12 10:29:36 anirban-laptop kernel: [    0.263911] pci 0000:00:1f.2: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.264591] pci 0000:10:00.0: PME# supported from D0 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.264604] pci 0000:10:00.0: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.264991] pci 0000:18:00.0: PME# supported from D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.264998] pci 0000:18:00.0: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.265488] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 10:29:36 anirban-laptop kernel: [    0.265496] pci 0000:02:04.0: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.265648] pci 0000:00:1e.0: transparent bridge
Apr 12 10:29:36 anirban-laptop kernel: [    0.311215] ACPI: PCI Interrupt Link [C12D] (IRQs 10 11) *5
Apr 12 10:29:36 anirban-laptop kernel: [    0.311443] ACPI: PCI Interrupt Link [C12E] (IRQs *10 11)
Apr 12 10:29:36 anirban-laptop kernel: [    0.311667] ACPI: PCI Interrupt Link [C12F] (IRQs 10 *11)
Apr 12 10:29:36 anirban-laptop kernel: [    0.311882] ACPI: PCI Interrupt Link [C130] (IRQs 10 11) *0, disabled.
Apr 12 10:29:36 anirban-laptop kernel: [    0.312113] ACPI: PCI Interrupt Link [C140] (IRQs *10 11)
Apr 12 10:29:36 anirban-laptop kernel: [    0.312336] ACPI: PCI Interrupt Link [C141] (IRQs *10 11)
Apr 12 10:29:36 anirban-laptop kernel: [    0.312551] ACPI: PCI Interrupt Link [C142] (IRQs 10 11) *0, disabled.
Apr 12 10:29:36 anirban-laptop kernel: [    0.312656] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS 20090521 pci_link-182
Apr 12 10:29:36 anirban-laptop kernel: [    0.312910] SCSI subsystem initialized
Apr 12 10:29:36 anirban-laptop kernel: [    0.312934] usbcore: registered new interface driver usbfs
Apr 12 10:29:36 anirban-laptop kernel: [    0.312934] usbcore: registered new interface driver hub
Apr 12 10:29:36 anirban-laptop kernel: [    0.312934] usbcore: registered new device driver usb
Apr 12 10:29:36 anirban-laptop kernel: [    0.312934] ACPI: WMI: Mapper loaded
Apr 12 10:29:36 anirban-laptop kernel: [    0.312934] PCI: Using ACPI for IRQ routing
Apr 12 10:29:36 anirban-laptop kernel: [    0.324010] Bluetooth: Core ver 2.15
Apr 12 10:29:36 anirban-laptop kernel: [    0.324026] NET: Registered protocol family 31
Apr 12 10:29:36 anirban-laptop kernel: [    0.324026] Bluetooth: HCI device and connection manager initialized
Apr 12 10:29:36 anirban-laptop kernel: [    0.324026] Bluetooth: HCI socket layer initialized
Apr 12 10:29:36 anirban-laptop kernel: [    0.324026] NetLabel: Initializing
Apr 12 10:29:36 anirban-laptop kernel: [    0.324026] NetLabel:  domain hash size = 128
Apr 12 10:29:36 anirban-laptop kernel: [    0.324026] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 12 10:29:36 anirban-laptop kernel: [    0.324037] NetLabel:  unlabeled traffic allowed by default
Apr 12 10:29:36 anirban-laptop kernel: [    0.324074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 12 10:29:36 anirban-laptop kernel: [    0.324080] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr 12 10:29:36 anirban-laptop kernel: [    0.340008] pnp: PnP ACPI init
Apr 12 10:29:36 anirban-laptop kernel: [    0.340018] ACPI: bus type pnp registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.349556] pnp: PnP ACPI: found 12 devices
Apr 12 10:29:36 anirban-laptop kernel: [    0.349559] ACPI: ACPI bus type pnp unregistered
Apr 12 10:29:36 anirban-laptop kernel: [    0.349563] PnPBIOS: Disabled by ACPI PNP
Apr 12 10:29:36 anirban-laptop kernel: [    0.349573] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349577] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349581] system 00:00: iomem range 0x100000-0x1f7fffff could not be reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349592] system 00:09: ioport range 0x500-0x57f has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349595] system 00:09: ioport range 0x800-0x80f has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349599] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349602] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349608] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349611] system 00:0a: ioport range 0x1000-0x107f has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349614] system 00:0a: ioport range 0x1100-0x113f has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349618] system 00:0a: ioport range 0x1200-0x121f has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349621] system 00:0a: iomem range 0xf8000000-0xfbffffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349624] system 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349628] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349631] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349634] system 00:0a: iomem range 0xfed90000-0xfed99fff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349640] system 00:0b: iomem range 0xcee00-0xcffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349644] system 00:0b: iomem range 0xd2a00-0xd3fff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349647] system 00:0b: iomem range 0xfeda0000-0xfedbffff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.349650] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 12 10:29:36 anirban-laptop kernel: [    0.384354] AppArmor: AppArmor Filesystem Enabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384503] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:08
Apr 12 10:29:36 anirban-laptop kernel: [    0.384505] pci 0000:00:1c.0:   IO window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384518] pci 0000:00:1c.0:   MEM window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384528] pci 0000:00:1c.0:   PREFETCH window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384538] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:10
Apr 12 10:29:36 anirban-laptop kernel: [    0.384540] pci 0000:00:1c.1:   IO window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384551] pci 0000:00:1c.1:   MEM window: 0xe4100000-0xe41fffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384561] pci 0000:00:1c.1:   PREFETCH window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384571] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:18
Apr 12 10:29:36 anirban-laptop kernel: [    0.384573] pci 0000:00:1c.2:   IO window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384586] pci 0000:00:1c.2:   MEM window: 0xe4000000-0xe40fffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384596] pci 0000:00:1c.2:   PREFETCH window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384606] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:28
Apr 12 10:29:36 anirban-laptop kernel: [    0.384612] pci 0000:00:1c.4:   IO window: 0x2000-0x3fff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384626] pci 0000:00:1c.4:   MEM window: 0xe0000000-0xe3ffffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384635] pci 0000:00:1c.4:   PREFETCH window: disabled
Apr 12 10:29:36 anirban-laptop kernel: [    0.384647] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
Apr 12 10:29:36 anirban-laptop kernel: [    0.384650] pci 0000:02:04.0:   IO window: 0x005000-0x0050ff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384661] pci 0000:02:04.0:   IO window: 0x005400-0x0054ff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384672] pci 0000:02:04.0:   PREFETCH window: 0x20000000-0x23ffffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384682] pci 0000:02:04.0:   MEM window: 0x24000000-0x27ffffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384693] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Apr 12 10:29:36 anirban-laptop kernel: [    0.384699] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384713] pci 0000:00:1e.0:   MEM window: 0xe4200000-0xe42fffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384723] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
Apr 12 10:29:36 anirban-laptop kernel: [    0.384756] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [    0.384789] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 12 10:29:36 anirban-laptop kernel: [    0.384823] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 12 10:29:36 anirban-laptop kernel: [    0.384852] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [    0.384899] pci 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [    0.384990] NET: Registered protocol family 2
Apr 12 10:29:36 anirban-laptop kernel: [    0.385096] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.385401] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.385477] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.385542] TCP: Hash tables configured (established 16384 bind 16384)
Apr 12 10:29:36 anirban-laptop kernel: [    0.385544] TCP reno registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.385613] NET: Registered protocol family 1
Apr 12 10:29:36 anirban-laptop kernel: [    0.385671] Trying to unpack rootfs image as initramfs...
Apr 12 10:29:36 anirban-laptop kernel: [    0.591252] Freeing initrd memory: 7463k freed
Apr 12 10:29:36 anirban-laptop kernel: [    0.596758] cpufreq-nforce2: No nForce2 chipset.
Apr 12 10:29:36 anirban-laptop kernel: [    0.596789] Scanning for low memory corruption every 60 seconds
Apr 12 10:29:36 anirban-laptop kernel: [    0.596911] audit: initializing netlink socket (disabled)
Apr 12 10:29:36 anirban-laptop kernel: [    0.596929] type=2000 audit(1271048361.596:1): initialized
Apr 12 10:29:36 anirban-laptop kernel: [    0.606546] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 12 10:29:36 anirban-laptop kernel: [    0.608195] VFS: Disk quotas dquot_6.5.2
Apr 12 10:29:36 anirban-laptop kernel: [    0.608261] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 12 10:29:36 anirban-laptop kernel: [    0.608857] fuse init (API version 7.12)
Apr 12 10:29:36 anirban-laptop kernel: [    0.608952] msgmni has been set to 977
Apr 12 10:29:36 anirban-laptop kernel: [    0.609188] alg: No test for stdrng (krng)
Apr 12 10:29:36 anirban-laptop kernel: [    0.609203] io scheduler noop registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.609206] io scheduler anticipatory registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.609208] io scheduler deadline registered
Apr 12 10:29:36 anirban-laptop kernel: [    0.609255] io scheduler cfq registered (default)
Apr 12 10:29:36 anirban-laptop kernel: [    0.611050] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 12 10:29:36 anirban-laptop kernel: [    0.611164] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 12 10:29:36 anirban-laptop kernel: [    0.616790] ACPI: AC Adapter [C239] (off-line)
Apr 12 10:29:36 anirban-laptop kernel: [    0.616861] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr 12 10:29:36 anirban-laptop kernel: [    0.616865] ACPI: Power Button [PWRF]
Apr 12 10:29:36 anirban-laptop kernel: [    0.616943] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Apr 12 10:29:36 anirban-laptop kernel: [    0.616946] ACPI: Sleep Button [C2BF]
Apr 12 10:29:36 anirban-laptop kernel: [    0.616994] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Apr 12 10:29:36 anirban-laptop kernel: [    0.617066] ACPI: Lid Switch [C153]
Apr 12 10:29:36 anirban-laptop kernel: [    0.617316] fan PNP0C0B:00: registered as cooling_device0
Apr 12 10:29:36 anirban-laptop kernel: [    0.617323] ACPI: Fan [C3BC] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.617521] fan PNP0C0B:01: registered as cooling_device1
Apr 12 10:29:36 anirban-laptop kernel: [    0.617528] ACPI: Fan [C3BD] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.617725] fan PNP0C0B:02: registered as cooling_device2
Apr 12 10:29:36 anirban-laptop kernel: [    0.617732] ACPI: Fan [C3BE] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.617928] fan PNP0C0B:03: registered as cooling_device3
Apr 12 10:29:36 anirban-laptop kernel: [    0.617935] ACPI: Fan [C3BF] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.618132] fan PNP0C0B:04: registered as cooling_device4
Apr 12 10:29:36 anirban-laptop kernel: [    0.618140] ACPI: Fan [C3C0] (off)
Apr 12 10:29:36 anirban-laptop kernel: [    0.618829] ACPI: SSDT 1f7db525 0023D (v01 HP      Cpu0Ist 00003000 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.619449] ACPI: SSDT 1f7db7e7 004BA (v01 HP      Cpu0Cst 00003001 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.622240] Marking TSC unstable due to TSC halts in idle
Apr 12 10:29:36 anirban-laptop kernel: [    0.622263] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 12 10:29:36 anirban-laptop kernel: [    0.622285] processor LNXCPU:00: registered as cooling_device5
Apr 12 10:29:36 anirban-laptop kernel: [    0.622289] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 12 10:29:36 anirban-laptop kernel: [    0.622642] ACPI: SSDT 1f7db45d 000C8 (v01 HP      Cpu1Ist 00003000 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.623125] ACPI: SSDT 1f7db762 00085 (v01 HP      Cpu1Cst 00003000 INTL 20060317)
Apr 12 10:29:36 anirban-laptop kernel: [    0.624224] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 12 10:29:36 anirban-laptop kernel: [    0.624251] processor LNXCPU:01: registered as cooling_device6
Apr 12 10:29:36 anirban-laptop kernel: [    0.624256] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 12 10:29:36 anirban-laptop kernel: [    0.650263] thermal LNXTHERM:01: registered as thermal_zone0
Apr 12 10:29:36 anirban-laptop kernel: [    0.650272] ACPI: Thermal Zone [TZ0] (55 C)
Apr 12 10:29:36 anirban-laptop kernel: [    0.654482] thermal LNXTHERM:02: registered as thermal_zone1
Apr 12 10:29:36 anirban-laptop kernel: [    0.654493] ACPI: Thermal Zone [TZ1] (53 C)
Apr 12 10:29:36 anirban-laptop kernel: [    0.658493] thermal LNXTHERM:03: registered as thermal_zone2
Apr 12 10:29:36 anirban-laptop kernel: [    0.658503] ACPI: Thermal Zone [TZ3] (34 C)
Apr 12 10:29:36 anirban-laptop kernel: [    0.667621] thermal LNXTHERM:04: registered as thermal_zone3
Apr 12 10:29:36 anirban-laptop kernel: [    0.667630] ACPI: Thermal Zone [TZ4] (34 C)
Apr 12 10:29:36 anirban-laptop kernel: [    0.671328] thermal LNXTHERM:05: registered as thermal_zone4
Apr 12 10:29:36 anirban-laptop kernel: [    0.671337] ACPI: Thermal Zone [TZ5] (74 C)
Apr 12 10:29:36 anirban-laptop kernel: [    0.671413] isapnp: Scanning for PnP cards...
Apr 12 10:29:36 anirban-laptop kernel: [    0.725874] ACPI: Battery Slot [C23B] (battery present)
Apr 12 10:29:36 anirban-laptop kernel: [    0.726065] ACPI: Battery Slot [C23A] (battery absent)
Apr 12 10:29:36 anirban-laptop kernel: [    1.029325] isapnp: No Plug & Play device found
Apr 12 10:29:36 anirban-laptop kernel: [    1.030630] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 12 10:29:36 anirban-laptop kernel: [    1.032123] brd: module loaded
Apr 12 10:29:36 anirban-laptop kernel: [    1.032628] loop: module loaded
Apr 12 10:29:36 anirban-laptop kernel: [    1.032700] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr 12 10:29:36 anirban-laptop kernel: [    1.032804] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 12 10:29:36 anirban-laptop kernel: [    1.032944] ahci: SSS flag set, parallel bus scan disabled
Apr 12 10:29:36 anirban-laptop kernel: [    1.032975] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
Apr 12 10:29:36 anirban-laptop kernel: [    1.032979] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
Apr 12 10:29:36 anirban-laptop kernel: [    1.033159] scsi0 : ahci
Apr 12 10:29:36 anirban-laptop kernel: [    1.033249] scsi1 : ahci
Apr 12 10:29:36 anirban-laptop kernel: [    1.033314] scsi2 : ahci
Apr 12 10:29:36 anirban-laptop kernel: [    1.033386] ata1: SATA max UDMA/133 abar m2048@0xe4509000 port 0xe4509100 irq 28
Apr 12 10:29:36 anirban-laptop kernel: [    1.033389] ata2: DUMMY
Apr 12 10:29:36 anirban-laptop kernel: [    1.033391] ata3: DUMMY
Apr 12 10:29:36 anirban-laptop kernel: [    1.033452] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [    1.033596] scsi3 : ata_piix
Apr 12 10:29:36 anirban-laptop kernel: [    1.033660] scsi4 : ata_piix
Apr 12 10:29:36 anirban-laptop kernel: [    1.034211] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x40c0 irq 14
Apr 12 10:29:36 anirban-laptop kernel: [    1.034215] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40c8 irq 15
Apr 12 10:29:36 anirban-laptop kernel: [    1.035198] Fixed MDIO Bus: probed
Apr 12 10:29:36 anirban-laptop kernel: [    1.035235] PPP generic driver version 2.4.2
Apr 12 10:29:36 anirban-laptop kernel: [    1.035327] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 12 10:29:36 anirban-laptop kernel: [    1.035354] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 12 10:29:36 anirban-laptop kernel: [    1.035376] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.035408] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr 12 10:29:36 anirban-laptop kernel: [    1.039339] ehci_hcd 0000:00:1a.7: debug port 1
Apr 12 10:29:36 anirban-laptop kernel: [    1.039370] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe4500000
Apr 12 10:29:36 anirban-laptop kernel: [    1.052030] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr 12 10:29:36 anirban-laptop kernel: [    1.052105] usb usb1: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.052136] hub 1-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.052144] hub 1-0:1.0: 4 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.052224] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 12 10:29:36 anirban-laptop kernel: [    1.052245] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.052277] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr 12 10:29:36 anirban-laptop kernel: [    1.056209] ehci_hcd 0000:00:1d.7: debug port 1
Apr 12 10:29:36 anirban-laptop kernel: [    1.056236] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe4508000
Apr 12 10:29:36 anirban-laptop kernel: [    1.068032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr 12 10:29:36 anirban-laptop kernel: [    1.068099] usb usb2: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.068128] hub 2-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.068134] hub 2-0:1.0: 6 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.068197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 12 10:29:36 anirban-laptop kernel: [    1.068215] uhci_hcd: USB Universal Host Controller Interface driver
Apr 12 10:29:36 anirban-laptop kernel: [    1.068239] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [    1.068256] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.068289] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr 12 10:29:36 anirban-laptop kernel: [    1.068336] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004020
Apr 12 10:29:36 anirban-laptop kernel: [    1.068422] usb usb3: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.068456] hub 3-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.068463] hub 3-0:1.0: 2 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.068524] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 12 10:29:36 anirban-laptop kernel: [    1.068541] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.068571] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr 12 10:29:36 anirban-laptop kernel: [    1.068618] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00004040
Apr 12 10:29:36 anirban-laptop kernel: [    1.068705] usb usb4: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.068733] hub 4-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.068739] hub 4-0:1.0: 2 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.068796] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 12 10:29:36 anirban-laptop kernel: [    1.068814] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.068848] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Apr 12 10:29:36 anirban-laptop kernel: [    1.068886] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00004060
Apr 12 10:29:36 anirban-laptop kernel: [    1.068968] usb usb5: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.068996] hub 5-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.069026] hub 5-0:1.0: 2 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.069087] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 12 10:29:36 anirban-laptop kernel: [    1.069104] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.069134] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Apr 12 10:29:36 anirban-laptop kernel: [    1.069181] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00004080
Apr 12 10:29:36 anirban-laptop kernel: [    1.069266] usb usb6: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.069293] hub 6-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.069300] hub 6-0:1.0: 2 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.069353] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 12 10:29:36 anirban-laptop kernel: [    1.069369] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 12 10:29:36 anirban-laptop kernel: [    1.069398] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Apr 12 10:29:36 anirban-laptop kernel: [    1.069433] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000040a0
Apr 12 10:29:36 anirban-laptop kernel: [    1.069519] usb usb7: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.069549] hub 7-0:1.0: USB hub found
Apr 12 10:29:36 anirban-laptop kernel: [    1.069556] hub 7-0:1.0: 2 ports detected
Apr 12 10:29:36 anirban-laptop kernel: [    1.069664] PNP: PS/2 Controller [PNP0303:C298,PNP0f13:C299] at 0x60,0x64 irq 1,12
Apr 12 10:29:36 anirban-laptop kernel: [    1.071540] i8042.c: Detected active multiplexing controller, rev 1.1.
Apr 12 10:29:36 anirban-laptop kernel: [    1.072243] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 12 10:29:36 anirban-laptop kernel: [    1.072250] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr 12 10:29:36 anirban-laptop kernel: [    1.072253] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr 12 10:29:36 anirban-laptop kernel: [    1.072257] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr 12 10:29:36 anirban-laptop kernel: [    1.072260] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr 12 10:29:36 anirban-laptop kernel: [    1.072325] mice: PS/2 mouse device common for all mice
Apr 12 10:29:36 anirban-laptop kernel: [    1.072458] rtc_cmos 00:05: RTC can wake from S4
Apr 12 10:29:36 anirban-laptop kernel: [    1.072493] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 12 10:29:36 anirban-laptop kernel: [    1.072532] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr 12 10:29:36 anirban-laptop kernel: [    1.072640] device-mapper: uevent: version 1.0.3
Apr 12 10:29:36 anirban-laptop kernel: [    1.072730] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Apr 12 10:29:36 anirban-laptop kernel: [    1.072802] device-mapper: multipath: version 1.1.0 loaded
Apr 12 10:29:36 anirban-laptop kernel: [    1.072804] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 12 10:29:36 anirban-laptop kernel: [    1.072928] EISA: Probing bus 0 at eisa.0
Apr 12 10:29:36 anirban-laptop kernel: [    1.072937] Cannot allocate resource for EISA slot 1
Apr 12 10:29:36 anirban-laptop kernel: [    1.072939] Cannot allocate resource for EISA slot 2
Apr 12 10:29:36 anirban-laptop kernel: [    1.072942] Cannot allocate resource for EISA slot 3
Apr 12 10:29:36 anirban-laptop kernel: [    1.072944] Cannot allocate resource for EISA slot 4
Apr 12 10:29:36 anirban-laptop kernel: [    1.072947] Cannot allocate resource for EISA slot 5
Apr 12 10:29:36 anirban-laptop kernel: [    1.072969] EISA: Detected 0 cards.
Apr 12 10:29:36 anirban-laptop kernel: [    1.073169] cpuidle: using governor ladder
Apr 12 10:29:36 anirban-laptop kernel: [    1.073305] cpuidle: using governor menu
Apr 12 10:29:36 anirban-laptop kernel: [    1.073848] TCP cubic registered
Apr 12 10:29:36 anirban-laptop kernel: [    1.074017] NET: Registered protocol family 10
Apr 12 10:29:36 anirban-laptop kernel: [    1.074529] lo: Disabled Privacy Extensions
Apr 12 10:29:36 anirban-laptop kernel: [    1.074910] NET: Registered protocol family 17
Apr 12 10:29:36 anirban-laptop kernel: [    1.074928] Bluetooth: L2CAP ver 2.13
Apr 12 10:29:36 anirban-laptop kernel: [    1.074930] Bluetooth: L2CAP socket layer initialized
Apr 12 10:29:36 anirban-laptop kernel: [    1.074934] Bluetooth: SCO (Voice Link) ver 0.6
Apr 12 10:29:36 anirban-laptop kernel: [    1.074935] Bluetooth: SCO socket layer initialized
Apr 12 10:29:36 anirban-laptop kernel: [    1.074976] Bluetooth: RFCOMM TTY layer initialized
Apr 12 10:29:36 anirban-laptop kernel: [    1.074980] Bluetooth: RFCOMM socket layer initialized
Apr 12 10:29:36 anirban-laptop kernel: [    1.074982] Bluetooth: RFCOMM ver 1.11
Apr 12 10:29:36 anirban-laptop kernel: [    1.075560] Using IPI No-Shortcut mode
Apr 12 10:29:36 anirban-laptop kernel: [    1.075641] registered taskstats version 1
Apr 12 10:29:36 anirban-laptop kernel: [    1.075760]   Magic number: 6:751:969
Apr 12 10:29:36 anirban-laptop kernel: [    1.075881] rtc_cmos 00:05: setting system clock to 2010-04-12 04:59:22 UTC (1271048362)
Apr 12 10:29:36 anirban-laptop kernel: [    1.075885] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 12 10:29:36 anirban-laptop kernel: [    1.075887] EDD information not available.
Apr 12 10:29:36 anirban-laptop kernel: [    1.094687] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr 12 10:29:36 anirban-laptop kernel: [    1.212756] ata4.00: ATAPI: TSSTcorpCDW/DVD TS-L462D, HH08, max MWDMA2
Apr 12 10:29:36 anirban-laptop kernel: [    1.244415] ata4.00: configured for MWDMA2
Apr 12 10:29:36 anirban-laptop kernel: [    1.356135] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 12 10:29:36 anirban-laptop kernel: [    1.360127] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 12 10:29:36 anirban-laptop kernel: [    1.360131] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
Apr 12 10:29:36 anirban-laptop kernel: [    1.361771] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 12 10:29:36 anirban-laptop kernel: [    1.364054] ata1.00: ATA-7: ST980811AS, 3.BHD, max UDMA/100
Apr 12 10:29:36 anirban-laptop kernel: [    1.364059] ata1.00: 156301488 sectors, multi 16: LBA48 
Apr 12 10:29:36 anirban-laptop kernel: [    1.369411] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 12 10:29:36 anirban-laptop kernel: [    1.369415] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
Apr 12 10:29:36 anirban-laptop kernel: [    1.371011] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 12 10:29:36 anirban-laptop kernel: [    1.373333] ata1.00: configured for UDMA/100
Apr 12 10:29:36 anirban-laptop kernel: [    1.393696] ata1.00: configured for UDMA/100
Apr 12 10:29:36 anirban-laptop kernel: [    1.393701] ata1: EH complete
Apr 12 10:29:36 anirban-laptop kernel: [    1.393856] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
Apr 12 10:29:36 anirban-laptop kernel: [    1.393990] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 12 10:29:36 anirban-laptop kernel: [    1.394028] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Apr 12 10:29:36 anirban-laptop kernel: [    1.394072] sd 0:0:0:0: [sda] Write Protect is off
Apr 12 10:29:36 anirban-laptop kernel: [    1.394098] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 10:29:36 anirban-laptop kernel: [    1.394218]  sda:
Apr 12 10:29:36 anirban-laptop kernel: [    1.395034] scsi 3:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462D HH08 PQ: 0 ANSI: 5
Apr 12 10:29:36 anirban-laptop kernel: [    1.396240] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 12 10:29:36 anirban-laptop kernel: [    1.396245] Uniform CD-ROM driver Revision: 3.20
Apr 12 10:29:36 anirban-laptop kernel: [    1.396385] sr 3:0:0:0: Attached scsi generic sg1 type 5
Apr 12 10:29:36 anirban-laptop kernel: [    1.454754]  sda1 sda2 < sda5 >
Apr 12 10:29:36 anirban-laptop kernel: [    1.481568] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 12 10:29:36 anirban-laptop kernel: [    1.481639] Freeing unused kernel memory: 540k freed
Apr 12 10:29:36 anirban-laptop kernel: [    1.482027] Write protecting the kernel text: 4580k
Apr 12 10:29:36 anirban-laptop kernel: [    1.482096] Write protecting the kernel read-only data: 1840k
Apr 12 10:29:36 anirban-laptop kernel: [    1.500053] Clocksource tsc unstable (delta = -267141820 ns)
Apr 12 10:29:36 anirban-laptop kernel: [    1.591426] Linux agpgart interface v0.103
Apr 12 10:29:36 anirban-laptop kernel: [    1.594154] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr 12 10:29:36 anirban-laptop kernel: [    1.594791] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr 12 10:29:36 anirban-laptop kernel: [    1.603827] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr 12 10:29:36 anirban-laptop kernel: [    1.642526] usb 6-1: new full speed USB device using uhci_hcd and address 2
Apr 12 10:29:36 anirban-laptop kernel: [    1.656661] [drm] Initialized drm 1.1.0 20060810
Apr 12 10:29:36 anirban-laptop kernel: [    1.704874] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [    1.784917] tg3.c:v3.99 (April 20, 2009)
Apr 12 10:29:36 anirban-laptop kernel: [    1.784974] tg3 0000:18:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 12 10:29:36 anirban-laptop kernel: [    1.795703] tg3 0000:18:00.0: PME# disabled
Apr 12 10:29:36 anirban-laptop kernel: [    1.815443] usb 6-1: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    1.823220] Initializing USB Mass Storage driver...
Apr 12 10:29:36 anirban-laptop kernel: [    1.825270] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 12 10:29:36 anirban-laptop kernel: [    1.825357] usbcore: registered new interface driver usb-storage
Apr 12 10:29:36 anirban-laptop kernel: [    1.825361] USB Mass Storage support registered.
Apr 12 10:29:36 anirban-laptop kernel: [    2.069109] usb 6-1: USB disconnect, address 2
Apr 12 10:29:36 anirban-laptop kernel: [    2.091099] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1a:4b:70:18:d0
Apr 12 10:29:36 anirban-laptop kernel: [    2.091103] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
Apr 12 10:29:36 anirban-laptop kernel: [    2.091106] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
Apr 12 10:29:36 anirban-laptop kernel: [    2.091109] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr 12 10:29:36 anirban-laptop kernel: [    2.206343] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:36 anirban-laptop kernel: [    2.320055] usb 6-1: new full speed USB device using uhci_hcd and address 3
Apr 12 10:29:36 anirban-laptop kernel: [    2.330893] [drm] fb0: inteldrmfb frame buffer device
Apr 12 10:29:36 anirban-laptop kernel: [    2.334411] acpi device:02: registered as cooling_device7
Apr 12 10:29:36 anirban-laptop kernel: [    2.335119] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
Apr 12 10:29:36 anirban-laptop kernel: [    2.335149] ACPI: Video Device [C098] (multi-head: yes  rom: no  post: no)
Apr 12 10:29:36 anirban-laptop kernel: [    2.335185] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 12 10:29:36 anirban-laptop kernel: [    2.403493] [drm] LVDS-8: set mode 1280x800 17
Apr 12 10:29:36 anirban-laptop kernel: [    2.500325] usb 6-1: configuration #1 chosen from 1 choice
Apr 12 10:29:36 anirban-laptop kernel: [    2.626026] Console: switching to colour frame buffer device 160x50
Apr 12 10:29:36 anirban-laptop kernel: [    2.627264] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 12 10:29:36 anirban-laptop kernel: [    2.977850] PM: Starting manual resume from disk
Apr 12 10:29:36 anirban-laptop kernel: [    3.016058] EXT4-fs (sda1): barriers enabled
Apr 12 10:29:36 anirban-laptop kernel: [    3.031183] kjournald2 starting: pid 419, dev sda1:8, commit interval 5 seconds
Apr 12 10:29:36 anirban-laptop kernel: [    3.031383] EXT4-fs (sda1): delayed allocation enabled
Apr 12 10:29:36 anirban-laptop kernel: [    3.031386] EXT4-fs: file extents enabled
Apr 12 10:29:36 anirban-laptop kernel: [    3.035417] EXT4-fs: mballoc enabled
Apr 12 10:29:36 anirban-laptop kernel: [    3.035431] EXT4-fs (sda1): mounted filesystem with ordered data mode
Apr 12 10:29:36 anirban-laptop kernel: [    3.956803] type=1505 audit(1271048365.380:2): operation="profile_load" pid=444 name=/usr/share/gdm/guest-session/Xsession
Apr 12 10:29:36 anirban-laptop kernel: [    3.959398] type=1505 audit(1271048365.380:3): operation="profile_load" pid=445 name=/sbin/dhclient3
Apr 12 10:29:36 anirban-laptop kernel: [    3.960169] type=1505 audit(1271048365.380:4): operation="profile_load" pid=445 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 12 10:29:36 anirban-laptop kernel: [    3.960577] type=1505 audit(1271048365.380:5): operation="profile_load" pid=445 name=/usr/lib/connman/scripts/dhclient-script
Apr 12 10:29:36 anirban-laptop kernel: [    4.040195] type=1505 audit(1271048365.462:6): operation="profile_load" pid=446 name=/usr/bin/evince
Apr 12 10:29:36 anirban-laptop kernel: [    4.052225] type=1505 audit(1271048365.473:7): operation="profile_load" pid=446 name=/usr/bin/evince-previewer
Apr 12 10:29:36 anirban-laptop kernel: [    4.059207] type=1505 audit(1271048365.481:8): operation="profile_load" pid=446 name=/usr/bin/evince-thumbnailer
Apr 12 10:29:36 anirban-laptop kernel: [    4.121272] type=1505 audit(1271048365.544:9): operation="profile_load" pid=448 name=/usr/bin/freshclam
Apr 12 10:29:36 anirban-laptop kernel: [    7.629287] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Apr 12 10:29:36 anirban-laptop kernel: [    7.632282] scsi 9:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Apr 12 10:29:36 anirban-laptop kernel: [    7.648258] sr1: scsi-1 drive
Apr 12 10:29:36 anirban-laptop kernel: [    7.648438] sr 9:0:0:0: Attached scsi generic sg2 type 5
Apr 12 10:29:36 anirban-laptop kernel: [    7.648544] sd 9:0:0:1: Attached scsi generic sg3 type 0
Apr 12 10:29:36 anirban-laptop kernel: [    7.658256] sd 9:0:0:1: [sdb] Attached SCSI removable disk
Apr 12 10:29:36 anirban-laptop kernel: [   11.865361] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k 
Apr 12 10:29:36 anirban-laptop kernel: [   11.878916] EXT4-fs (sda1): internal journal on sda1:8
Apr 12 10:29:36 anirban-laptop kernel: [   11.995531] udev: starting version 147
Apr 12 10:29:36 anirban-laptop kernel: [   12.511604] usbcore: registered new interface driver usbserial
Apr 12 10:29:36 anirban-laptop kernel: [   12.511621] USB Serial support registered for generic
Apr 12 10:29:36 anirban-laptop kernel: [   12.511664] usbcore: registered new interface driver usbserial_generic
Apr 12 10:29:36 anirban-laptop kernel: [   12.511666] usbserial: USB Serial Driver core
Apr 12 10:29:36 anirban-laptop kernel: [   12.512137] cfg80211: Calling CRDA to update world regulatory domain
Apr 12 10:29:36 anirban-laptop kernel: [   12.525774] USB Serial support registered for GSM modem (1-port)
Apr 12 10:29:36 anirban-laptop kernel: [   12.525820] option 6-1:1.0: GSM modem (1-port) converter detected
Apr 12 10:29:36 anirban-laptop kernel: [   12.525907] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Apr 12 10:29:36 anirban-laptop kernel: [   12.525919] option 6-1:1.1: GSM modem (1-port) converter detected
Apr 12 10:29:36 anirban-laptop kernel: [   12.525968] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 12 10:29:36 anirban-laptop kernel: [   12.525979] option 6-1:1.2: GSM modem (1-port) converter detected
Apr 12 10:29:36 anirban-laptop kernel: [   12.526028] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
Apr 12 10:29:36 anirban-laptop kernel: [   12.526047] usbcore: registered new interface driver option
Apr 12 10:29:36 anirban-laptop kernel: [   12.526049] option: v0.7.2:USB Driver for GSM modems
Apr 12 10:29:36 anirban-laptop kernel: [   12.716353] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:30c0]
Apr 12 10:29:36 anirban-laptop kernel: [   12.844851] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0cb8, PCI irq 16
Apr 12 10:29:36 anirban-laptop kernel: [   12.844858] yenta_cardbus 0000:02:04.0: Socket status: 30000006
Apr 12 10:29:36 anirban-laptop kernel: [   12.844863] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
Apr 12 10:29:36 anirban-laptop kernel: [   12.844874] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
Apr 12 10:29:36 anirban-laptop kernel: [   12.844878] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
Apr 12 10:29:36 anirban-laptop kernel: [   12.845158] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xe4200000 - 0xe42fffff
Apr 12 10:29:36 anirban-laptop kernel: [   12.845162] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
Apr 12 10:29:36 anirban-laptop kernel: [   13.144369] lp: driver loaded but no devices found
Apr 12 10:29:36 anirban-laptop kernel: [   13.159392] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
Apr 12 10:29:36 anirban-laptop kernel: [   13.159400] serio: Synaptics pass-through port at isa0060/serio4/input0
Apr 12 10:29:36 anirban-laptop kernel: [   13.199902] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
Apr 12 10:29:36 anirban-laptop kernel: [   13.308114] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Apr 12 10:29:36 anirban-laptop kernel: [   13.308118] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Apr 12 10:29:36 anirban-laptop kernel: [   13.308267] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 12 10:29:36 anirban-laptop kernel: [   13.377257] iwl3945 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr 12 10:29:36 anirban-laptop kernel: [   13.377261] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr 12 10:29:36 anirban-laptop kernel: [   13.870594] cfg80211: World regulatory domain updated:
Apr 12 10:29:36 anirban-laptop kernel: [   13.870598]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 12 10:29:36 anirban-laptop kernel: [   13.870601]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 12 10:29:36 anirban-laptop kernel: [   13.870604]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 12 10:29:36 anirban-laptop kernel: [   13.870606]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 12 10:29:36 anirban-laptop kernel: [   13.870609]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 12 10:29:36 anirban-laptop kernel: [   13.870611]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 12 10:29:36 anirban-laptop kernel: [   13.901048] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Apr 12 10:29:36 anirban-laptop kernel: [   13.903400] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Apr 12 10:29:36 anirban-laptop kernel: [   13.904396] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Apr 12 10:29:36 anirban-laptop kernel: [   13.905218] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Apr 12 10:29:36 anirban-laptop kernel: [   13.906219] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Apr 12 10:29:36 anirban-laptop kernel: [   14.388045] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 12 10:29:36 anirban-laptop kernel: [   14.512282] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Apr 12 10:29:36 anirban-laptop kernel: [   14.512295] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 12 10:29:36 anirban-laptop kernel: [   14.688059] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Apr 12 10:29:38 anirban-laptop kernel: [   16.677996] tg3 0000:18:00.0: PME# disabled
Apr 12 10:29:38 anirban-laptop kernel: [   16.731392] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 12 10:29:39 anirban-laptop pppd[1068]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Apr 12 10:29:39 anirban-laptop pppd[1068]: pppd 2.4.5 started by root, uid 0
Apr 12 10:29:39 anirban-laptop pppd[1068]: Using interface ppp0
Apr 12 10:29:39 anirban-laptop pppd[1068]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 12 10:29:40 anirban-laptop kernel: [   18.667024] __ratelimit: 15 callbacks suppressed
Apr 12 10:29:40 anirban-laptop kernel: [   18.667027] type=1505 audit(1271048380.089:15): operation="profile_replace" pid=1133 name=/usr/share/gdm/guest-session/Xsession
Apr 12 10:29:40 anirban-laptop kernel: [   18.668655] type=1505 audit(1271048380.089:16): operation="profile_replace" pid=1134 name=/sbin/dhclient3
Apr 12 10:29:40 anirban-laptop kernel: [   18.669410] type=1505 audit(1271048380.093:17): operation="profile_replace" pid=1134 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 12 10:29:40 anirban-laptop kernel: [   18.669808] type=1505 audit(1271048380.093:18): operation="profile_replace" pid=1134 name=/usr/lib/connman/scripts/dhclient-script
Apr 12 10:29:40 anirban-laptop kernel: [   18.674785] type=1505 audit(1271048380.097:19): operation="profile_replace" pid=1135 name=/usr/bin/evince
Apr 12 10:29:40 anirban-laptop kernel: [   18.687014] type=1505 audit(1271048380.109:20): operation="profile_replace" pid=1135 name=/usr/bin/evince-previewer
Apr 12 10:29:40 anirban-laptop kernel: [   18.694104] type=1505 audit(1271048380.117:21): operation="profile_replace" pid=1135 name=/usr/bin/evince-thumbnailer
Apr 12 10:29:40 anirban-laptop pppd[1068]: CHAP authentication succeeded
Apr 12 10:29:40 anirban-laptop pppd[1068]: CHAP authentication succeeded
Apr 12 10:29:40 anirban-laptop kernel: [   18.704638] type=1505 audit(1271048380.125:22): operation="profile_replace" pid=1139 name=/usr/bin/freshclam
Apr 12 10:29:40 anirban-laptop kernel: [   18.706507] type=1505 audit(1271048380.129:23): operation="profile_replace" pid=1140 name=/usr/sbin/clamd
Apr 12 10:29:40 anirban-laptop kernel: [   18.708328] type=1505 audit(1271048380.129:24): operation="profile_replace" pid=1141 name=/usr/lib/cups/backend/cups-pdf
Apr 12 10:29:40 anirban-laptop kernel: [   18.780927] PPP BSD Compression module registered
Apr 12 10:29:40 anirban-laptop kernel: [   18.818539] PPP Deflate Compression module registered
Apr 12 10:29:40 anirban-laptop pppd[1068]: local  IP address 219.64.66.3
Apr 12 10:29:40 anirban-laptop pppd[1068]: remote IP address 172.29.243.161
Apr 12 10:29:40 anirban-laptop pppd[1068]: primary   DNS address 203.200.230.244
Apr 12 10:29:40 anirban-laptop pppd[1068]: secondary DNS address 202.54.29.5
Apr 12 10:29:41 anirban-laptop kernel: [   19.947444] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:41 anirban-laptop kernel: [   20.088031] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:41 anirban-laptop kernel: [   20.438104] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:42 anirban-laptop kernel: [   20.578988] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:43 anirban-laptop squid[1363]: Squid Parent: child process 1369 started
Apr 12 10:29:48 anirban-laptop kernel: [   25.875831] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:48 anirban-laptop kernel: [   26.015811] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:48 anirban-laptop kernel: [   26.279263] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:48 anirban-laptop kernel: [   26.420487] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:48 anirban-laptop kernel: [   26.571565] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:29:48 anirban-laptop kernel: [   26.571571] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:29:48 anirban-laptop kernel: [   26.571577] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:29:48 anirban-laptop kernel: [   26.571585] Info fld=0x0
Apr 12 10:29:48 anirban-laptop kernel: [   26.571588] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 12 10:29:48 anirban-laptop kernel: [   26.571602] __ratelimit: 9 callbacks suppressed
Apr 12 10:29:48 anirban-laptop kernel: [   26.742950] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:49 anirban-laptop kernel: [   26.882929] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:29:54 anirban-laptop kernel: [   32.627383] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:29:54 anirban-laptop kernel: [   32.627389] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:29:54 anirban-laptop kernel: [   32.627395] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:29:54 anirban-laptop kernel: [   32.627404] Info fld=0x0
Apr 12 10:29:54 anirban-laptop kernel: [   32.627407] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 12 10:30:00 anirban-laptop kernel: [   38.653665] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:30:00 anirban-laptop kernel: [   38.653671] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:30:00 anirban-laptop kernel: [   38.653677] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:30:00 anirban-laptop kernel: [   38.653685] Info fld=0x0
Apr 12 10:30:00 anirban-laptop kernel: [   38.653688] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
Apr 12 10:30:07 anirban-laptop kernel: [   45.399228] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:30:07 anirban-laptop kernel: [   45.399232] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:30:07 anirban-laptop kernel: [   45.399237] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:30:07 anirban-laptop kernel: [   45.399243] Info fld=0x0
Apr 12 10:30:07 anirban-laptop kernel: [   45.399245] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 12 10:30:13 anirban-laptop kernel: [   51.583133] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:30:13 anirban-laptop kernel: [   51.583138] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:30:13 anirban-laptop kernel: [   51.583142] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:30:13 anirban-laptop kernel: [   51.583148] Info fld=0x0
Apr 12 10:30:13 anirban-laptop kernel: [   51.583150] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 12 10:30:15 anirban-laptop kernel: [   53.556384] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:30:15 anirban-laptop kernel: [   53.697511] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:30:16 anirban-laptop kernel: [   53.983347] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:30:16 anirban-laptop kernel: [   54.123852] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:30:16 anirban-laptop kernel: [   54.391355] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:30:16 anirban-laptop kernel: [   54.533003] [drm] TV-14: set mode NTSC 480i 0
Apr 12 10:30:19 anirban-laptop kernel: [   57.769502] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:30:19 anirban-laptop kernel: [   57.769507] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:30:19 anirban-laptop kernel: [   57.769512] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:30:19 anirban-laptop kernel: [   57.769517] Info fld=0x0
Apr 12 10:30:19 anirban-laptop kernel: [   57.769519] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 12 10:30:26 anirban-laptop kernel: [   63.950938] sr 3:0:0:0: [sr0] Unhandled sense code
Apr 12 10:30:26 anirban-laptop kernel: [   63.950944] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:30:26 anirban-laptop kernel: [   63.950950] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 12 10:30:26 anirban-laptop kernel: [   63.950958] Info fld=0x0
Apr 12 10:30:26 anirban-laptop kernel: [   63.950961] sr 3:0:0:0: [sr0] Add. Sense: No seek complete
Apr 12 10:30:44 anirban-laptop kernel: [   82.550791] UDF-fs: Filesystem marked read-only because writing to pseudooverwrite partition is not implemented.
Apr 12 10:30:44 anirban-laptop kernel: [   82.642548] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2010/03/30 11:51 (114a)
Apr 12 10:45:25 anirban-laptop kernel: [  962.992086] ata4: lost interrupt (Status 0x58)
Apr 12 10:45:25 anirban-laptop kernel: [  963.091890] ata4: soft resetting link
Apr 12 10:45:25 anirban-laptop kernel: [  963.321313] ata4.00: configured for MWDMA2
Apr 12 10:45:25 anirban-laptop kernel: [  963.335013] ata4: EH complete
Apr 12 10:54:55 anirban-laptop kernel: [ 1533.000046] ata4: lost interrupt (Status 0x58)
Apr 12 10:54:55 anirban-laptop kernel: [ 1533.117104] ata4: soft resetting link
Apr 12 10:54:55 anirban-laptop kernel: [ 1533.353375] ata4.00: configured for MWDMA2
Apr 12 10:54:55 anirban-laptop kernel: [ 1533.369253] ata4: EH complete
Apr 12 10:57:02 anirban-laptop kernel: [ 1659.988139] ata4: lost interrupt (Status 0x58)
Apr 12 10:57:02 anirban-laptop kernel: [ 1660.105156] ata4: soft resetting link
Apr 12 10:57:02 anirban-laptop kernel: [ 1660.332382] ata4.00: configured for MWDMA2
Apr 12 10:57:02 anirban-laptop kernel: [ 1660.347887] ata4: EH complete
```

---

