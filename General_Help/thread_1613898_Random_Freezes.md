---
title: "Random Freezes?"
date: 2010-11-05
forum: General Help
---

### Post by thebarisaxkid on 2010-11-05
I am experiencing random freeze's in 10.10 (happened very few times in 10.04).  When it the system freeze's, the caps lock and scroll lock lights start blinking.  ( I believe this indicates a kernal panic.)  Here is a link to the previous thread about this problem:

[http://ubuntuforums.org/showthread.php?t=1610292](http://ubuntuforums.org/showthread.php?t=1610292)

Someone had suggested that I should post the log files so here they are (its a long one):

"messages" log
[PHP]Nov  5 00:19:48 james-Inspiron-1520 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov  5 00:19:48 james-Inspiron-1520 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1005" x-info="http://www.rsyslog.com"] (re)start
Nov  5 00:19:48 james-Inspiron-1520 rsyslogd: rsyslogd's groupid changed to 103
Nov  5 00:19:48 james-Inspiron-1520 rsyslogd: rsyslogd's userid changed to 101
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe6d800 (usable)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 000000007fe6d800 - 0000000080000000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] DMI 2.4 present.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] last_pfn = 0x7fe6d max_arch_pfn = 0x100000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] modified physical RAM map:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 0000000000100000 - 000000007fe6d800 (usable)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 000000007fe6d800 - 0000000080000000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] RAMDISK: 375aa000 - 37ff0000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Allocated new RAMDISK: 009a5000 - 013eaf11
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Move RAMDISK from 00000000375aa000 - 0000000037feff10 to 009a5000 - 013eaf10
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: RSDP 000fbbf0 00024 (v02 DELL  )
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: XSDT 7fe6f200 0005C (v01 DELL    M08     27D70B05 ASL  00000061)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: FACP 7fe6f09c 000F4 (v04 DELL    M08     27D70B05 ASL  00000061)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: DSDT 7fe6f800 0565E (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: FACS 7fe7e000 00040
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: HPET 7fe6f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: APIC 7fe6f400 00068 (v01 DELL    M08     27D70B05 ASL  00000047)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: MCFG 7fe6f3c0 0003E (v16 DELL    M08     27D70B05 ASL  00000061)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: SLIC 7fe6f49c 00176 (v01 DELL    M08     27D70B05 ASL  00000061)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: BOOT 7fe6efc0 00028 (v01 DELL    M08     27D70B05 ASL  00000061)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: SSDT 7fe6da40 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] 1158MB HIGHMEM available.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] 887MB LOWMEM available.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   low ram: 0 - 377fe000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Zone PFN ranges:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fe6d
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Movable zone start PFN for each node
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     0: 0x00000100 -> 0x0007fe6d
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Using APIC driver default
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519680
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=ada49d2e-3784-49f1-b74f-a3d8425ea0b0 ro quiet splash
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Initializing CPU#0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] allocated 10477680 bytes of page_cgroup
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Subtract (47 early reservations)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #3 [000009f000 - 0000100000]   BIOS reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #4 [00009a1000 - 00009a4188]             BRK
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #8 [00009a5000 - 00013eb000]     NEW RAMDISK
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #9 [00013eb000 - 00013ec000]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #10 [00013ec000 - 00023ec000]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #11 [00023ec000 - 00023ec004]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #12 [00023ec040 - 00023ec100]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #13 [00023ec100 - 00023ec154]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #14 [00023ec180 - 00023ef180]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #15 [00023ef180 - 00023ef1f0]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #16 [00023ef200 - 00023f5200]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #17 [00023f5200 - 00023f5225]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #18 [00023f5240 - 00023f5267]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #19 [00023f5280 - 00023f5408]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #20 [00023f5440 - 00023f5480]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #21 [00023f5480 - 00023f54c0]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #22 [00023f54c0 - 00023f5500]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #23 [00023f5500 - 00023f5540]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #24 [00023f5540 - 00023f5580]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #25 [00023f5580 - 00023f55c0]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #26 [00023f55c0 - 00023f5600]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #27 [00023f5600 - 00023f5640]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #28 [00023f5640 - 00023f5680]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #29 [00023f5680 - 00023f56c0]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #30 [00023f56c0 - 00023f5700]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #31 [00023f5700 - 00023f5710]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #32 [00023f5740 - 00023f5750]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #33 [00023f5780 - 00023f57ea]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #34 [00023f5800 - 00023f586a]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #35 [0002400000 - 000240e000]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #36 [0002600000 - 000260e000]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #37 [00023f7880 - 00023f7884]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #38 [00023f78c0 - 00023f78c4]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #39 [00023f7900 - 00023f7908]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #40 [00023f7940 - 00023f7948]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #41 [00023f7980 - 00023f7a28]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #42 [00023f7a40 - 00023f7aa8]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #43 [00023f7ac0 - 00023fbac0]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #44 [000240e000 - 000248e000]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #45 [000248e000 - 00024ce000]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]   #46 [000260e000 - 000300c070]         BOOTMEM
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fe6d)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Memory: 2048128k/2095540k available (4928k kernel code, 46964k reserved, 2336k data, 684k init, 1186236k highmem)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] virtual kernel memory layout:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]       .data : 0xc05d030e - 0xc0818668   (2336 kB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d030e   (4928 kB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Hierarchical RCU implementation.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Extended CMOS year: 2000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Console: colour VGA+ 80x25
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] console [tty0] enabled
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Fast TSC calibration using PIT
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.000000] Detected 1462.918 MHz processor.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 2925.83 BogoMIPS (lpj=5851672)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004014] pid_max: default: 32768 minimum: 301
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004040] Security Framework initialized
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004063] AppArmor: AppArmor initialized
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004065] Yama: becoming mindful.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004140] Mount-cache hash table entries: 512
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004321] Initializing cgroup subsys ns
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004327] Initializing cgroup subsys cpuacct
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004333] Initializing cgroup subsys memory
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004345] Initializing cgroup subsys devices
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004348] Initializing cgroup subsys freezer
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004352] Initializing cgroup subsys net_cls
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004390] CPU: Physical Processor ID: 0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004393] CPU: Processor Core ID: 0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004397] mce: CPU supports 6 MCE banks
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004409] CPU0: Thermal monitoring enabled (TM2)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004414] using mwait in idle threads.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004424] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004432] PEBS disabled due to CPU errata.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004441] ... version:                2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004444] ... bit width:              40
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004446] ... generic registers:      2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004449] ... value mask:             000000ffffffffff
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004452] ... max period:             000000007fffffff
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004454] ... fixed-purpose events:   3
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.004457] ... event mask:             0000000700000003
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.011837] ACPI: Core revision 20100428
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.022596] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.022603] ftrace: allocating 21758 entries in 43 pages
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.028017] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.028423] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.068118] CPU0: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz stepping 0d
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.072000] Booting Node   0, Processors  #1 Ok.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.008000] Initializing CPU#1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.160019] Brought up 2 CPUs
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.160024] Total of 2 processors activated (5851.79 BogoMIPS).
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.160545] devtmpfs: initialized
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161403] regulator: core version 0.5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161442] Time:  0:19:27  Date: 11/05/10
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161499] NET: Registered protocol family 16
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161533] Trying to unpack rootfs image as initramfs...
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161685] EISA bus registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161697] ACPI: bus type pci registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161803] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161808] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161811] PCI: Using MMCONFIG for extended config space
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.161813] PCI: Using configuration type 1 for base access
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.168478] bio: create slab <bio-0> at 0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.206068] ACPI: SSDT 7fe6e576 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.206068] ACPI: Dynamic OEM Table Load:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.206068] ACPI: SSDT (null) 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.206068] ACPI: SSDT 7fe6df0c 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.206068] ACPI: Dynamic OEM Table Load:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.206068] ACPI: SSDT (null) 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.208546] ACPI: SSDT 7fe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.209174] ACPI: Dynamic OEM Table Load:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.209179] ACPI: SSDT (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.209385] ACPI: SSDT 7fe6e4f1 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.209996] ACPI: Dynamic OEM Table Load:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.210001] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.210098] ACPI: Interpreter enabled
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.210103] ACPI: (supports S0 S3 S4 S5)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.210136] ACPI: Using IOAPIC for interrupt routing
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.267750] ACPI: No dock devices found.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.267759] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.292459] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.343627] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.343634] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.343641] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.343649] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.352034] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.352141] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.352782] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.352811] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.352919] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.353158] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.353161] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.353771] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.375959] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.376158] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.376334] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.376512] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.376689] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.376874] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377057] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377217] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377307] HEST: Table is not found!
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377445] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377455] vgaarb: loaded
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377696] SCSI subsystem initialized
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377889] usbcore: registered new interface driver usbfs
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377908] usbcore: registered new interface driver hub
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.377946] usbcore: registered new device driver usb
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378314] ACPI: WMI: Mapper loaded
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378318] PCI: Using ACPI for IRQ routing
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378650] NetLabel: Initializing
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378653] NetLabel:  domain hash size = 128
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378655] NetLabel:  protocols = UNLABELED CIPSOv4
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378672] NetLabel:  unlabeled traffic allowed by default
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378724] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378734] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.378742] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.384049] Switching to clocksource tsc
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.400520] AppArmor: AppArmor Filesystem Enabled
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.400547] pnp: PnP ACPI init
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.400575] ACPI: bus type pnp registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.426711] pnp 00:09: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.426718] pnp 00:09: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.426879] pnp 00:0a: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.426885] pnp 00:0a: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.426890] pnp 00:0a: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.426895] pnp 00:0a: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455720] pnp: PnP ACPI: found 12 devices
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455725] ACPI: ACPI bus type pnp unregistered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455731] PnPBIOS: Disabled by ACPI PNP
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455754] system 00:05: [io  0x0c80-0x0cff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455767] system 00:08: [mem 0xfed00000-0xfed003ff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455776] system 00:09: [io  0x0900-0x097f] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455780] system 00:09: [io  0x04d0-0x04d1] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455789] system 00:0a: [io  0xf400-0xf4fe] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455794] system 00:0a: [io  0x1080-0x10bf] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455798] system 00:0a: [io  0x10c0-0x10df] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455802] system 00:0a: [io  0x0809] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455811] system 00:0b: [mem 0x00000000-0x0009efff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455815] system 00:0b: [mem 0x0009f000-0x0009ffff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455820] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455824] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455829] system 00:0b: [mem 0x00100000-0x7fe6d7ff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455833] system 00:0b: [mem 0x7fe6d800-0x7fefffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455837] system 00:0b: [mem 0x7ff00000-0x7fffffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455842] system 00:0b: [mem 0x7ff00000-0x806fffff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455846] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455851] system 00:0b: [mem 0xffa00000-0xffafffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455855] system 00:0b: [mem 0xfec00000-0xfec0ffff] could not be reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455860] system 00:0b: [mem 0xfee00000-0xfee0ffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455864] system 00:0b: [mem 0xfed20000-0xfed8ffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455868] system 00:0b: [mem 0xfeda0000-0xfeda3fff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455873] system 00:0b: [mem 0xfeda4000-0xfeda4fff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455877] system 00:0b: [mem 0xfeda5000-0xfeda5fff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455881] system 00:0b: [mem 0xfeda6000-0xfeda6fff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455886] system 00:0b: [mem 0xfed18000-0xfed1bfff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.455890] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492724] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492732] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492737] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492742] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492746] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492751] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492755] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492762] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492767] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff 64bit pref]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492775] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492780] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492789] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492797] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492808] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492813] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492822] pci 0000:00:1c.1:   bridge window [mem 0xf9f00000-0xf9ffffff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492829] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492840] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492845] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492854] pci 0000:00:1c.3:   bridge window [mem 0xf9c00000-0xf9efffff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492861] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf81fffff 64bit pref]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492873] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492875] pci 0000:00:1e.0:   bridge window [io  disabled]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492884] pci 0000:00:1e.0:   bridge window [mem 0xf9b00000-0xf9bfffff]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492891] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492932] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492954] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.492986] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.493016] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.493166] NET: Registered protocol family 2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.493270] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.493642] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.494290] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.494698] TCP: Hash tables configured (established 131072 bind 65536)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.494702] TCP reno registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.494708] UDP hash table entries: 512 (order: 2, 16384 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.494724] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.494878] NET: Registered protocol family 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.495225] Simple Boot Flag at 0x79 set to 0x1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.495514] cpufreq-nforce2: No nForce2 chipset.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.495575] Scanning for low memory corruption every 60 seconds
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.495777] audit: initializing netlink socket (disabled)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.495797] type=2000 audit(1288916367.492:1): initialized
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.510992] highmem bounce pool size: 64 pages
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.511001] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.513223] VFS: Disk quotas dquot_6.5.2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.513322] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.514207] fuse init (API version 7.14)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.514343] msgmni has been set to 1683
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.514760] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.514765] io scheduler noop registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.514768] io scheduler deadline registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.514788] io scheduler cfq registered (default)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.515844] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.516009] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.516339] ACPI: AC Adapter [AC] (on-line)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.516457] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.517003] ACPI: Lid Switch [LID]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.517072] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.517079] ACPI: Power Button [PBTN]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.517147] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.517153] ACPI: Sleep Button [SBTN]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.527683] Marking TSC unstable due to TSC halts in idle
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.535897] Switching to clocksource hpet
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.547243] thermal LNXTHERM:01: registered as thermal_zone0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.547258] ACPI: Thermal Zone [THM] (60 C)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.547449] ERST: Table is not found!
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.547767] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.550121] brd: module loaded
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.550950] loop: module loaded
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.551260] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.557056] isapnp: Scanning for PnP cards...
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.564047] scsi0 : ata_piix
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.572035] scsi1 : ata_piix
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.581413] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.581418] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.581924] Fixed MDIO Bus: probed
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.581975] PPP generic driver version 2.4.2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582053] tun: Universal TUN/TAP device driver, 1.6
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582056] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582180] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582226] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582255] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582307] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.582349] ehci_hcd 0000:00:1a.7: debug port 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.586250] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.597341] ACPI: Battery Slot [BAT0] (battery present)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612247] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612469] hub 1-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612477] hub 1-0:1.0: 4 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612618] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612651] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612716] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.612755] ehci_hcd 0000:00:1d.7: debug port 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.616680] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640152] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640367] hub 2-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640375] hub 2-0:1.0: 6 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640509] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640535] uhci_hcd: USB Universal Host Controller Interface driver
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640591] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640610] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640665] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640703] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640877] hub 3-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640883] hub 3-0:1.0: 2 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.640993] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641010] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641064] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641112] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641289] hub 4-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641295] hub 4-0:1.0: 2 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641394] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641409] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641456] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641489] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641658] hub 5-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641665] hub 5-0:1.0: 2 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641759] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641773] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641827] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.641859] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642034] hub 6-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642040] hub 6-0:1.0: 2 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642133] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642147] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642196] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642229] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642395] hub 7-0:1.0: USB hub found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642400] hub 7-0:1.0: 2 ports detected
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.642599] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645428] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645439] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645533] mice: PS/2 mouse device common for all mice
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645716] rtc_cmos 00:03: RTC can wake from S4
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645780] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645818] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.645989] device-mapper: uevent: version 1.0.3
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.654296] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.663857] Freeing initrd memory: 10520k freed
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671437] device-mapper: multipath: version 1.1.1 loaded
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671444] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671702] EISA: Probing bus 0 at eisa.0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671785] EISA: Mainboard NW_FFFF detected.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671810] Cannot allocate resource for EISA slot 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671813] Cannot allocate resource for EISA slot 2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671816] Cannot allocate resource for EISA slot 3
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.671845] EISA: Detected 0 cards.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.672096] cpuidle: using governor ladder
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.672252] cpuidle: using governor menu
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.672747] TCP cubic registered
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.672940] NET: Registered protocol family 10
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.673488] lo: Disabled Privacy Extensions
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.673850] NET: Registered protocol family 17
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.675230] Using IPI No-Shortcut mode
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.675389] registered taskstats version 1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.675870]   Magic number: 2:672:303
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.675908] tty tty32: hash matches
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.675997] rtc_cmos 00:03: setting system clock to 2010-11-05 00:19:28 UTC (1288916368)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.676023] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.676025] EDD information not available.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.677578] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.776437] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D300, max UDMA/33
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.812342] ata1.00: configured for UDMA/33
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.915913] isapnp: No Plug & Play device found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.918346] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D300 PQ: 0 ANSI: 5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.930498] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.930502] Uniform CD-ROM driver Revision: 3.20
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.930730] sr 0:0:0:0: Attached scsi generic sg0 type 5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.930825] Freeing unused kernel memory: 684k freed
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.931328] Write protecting the kernel text: 4932k
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.931407] Write protecting the kernel read-only data: 1976k
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    0.958553] udev[87]: starting version 163
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.055631] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.063847] sdhci: Secure Digital Host Controller Interface driver
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.063852] sdhci: Copyright(c) Pierre Ossman
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.089188] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.089235] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.091414] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.097151] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.137223] usb 6-2: new low speed USB device using uhci_hcd and address 2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.137345] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.206493] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.206670] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.206675] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.241537] scsi2 : ahci
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.243710] scsi3 : ahci
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.243856] scsi4 : ahci
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.244264] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 44
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.244268] ata4: DUMMY
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.244272] ata5: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 44
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.248104] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.248164] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.308114] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.308150] b44: b44.c:v2.0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.330224] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:a8:b4:64
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.355058] usbcore: registered new interface driver hiddev
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.370651] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input4
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.370798] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2/input0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.384075] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2/input1
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.384101] usbcore: registered new interface driver usbhid
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.384104] usbhid: USB HID core driver
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.564085] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.564117] ata5: SATA link down (SStatus 0 SControl 300)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.612589] ata3.00: ATA-8: WDC WD1200BEVS-75UST0, 01.01A01, max UDMA/133
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.612594] ata3.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.613586] ata3.00: configured for UDMA/133
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.628299] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-7 01.0 PQ: 0 ANSI: 5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.628525] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.628535] sd 2:0:0:0: Attached scsi generic sg1 type 0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.628618] sd 2:0:0:0: [sda] Write Protect is off
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.628678] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.629104]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.698764] sd 2:0:0:0: [sda] Attached SCSI disk
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    1.740175] firewire_core: created device fw0: GUID 314fc0001d4825a1, S400
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    2.244421] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    2.244429] EXT4-fs (sda5): write access will be enabled during recovery
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    2.875115] EXT4-fs (sda5): orphan cleanup on readonly fs
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    2.875541] EXT4-fs (sda5): 15 orphan inodes deleted
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    2.875546] EXT4-fs (sda5): recovery complete
Nov  5 00:19:48 james-Inspiron-1520 kernel: [    3.302462] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   14.432903] udev[387]: starting version 163
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   14.485409] lp: driver loaded but no devices found
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   14.490659] Adding 2441212k swap on /dev/sda3.  Priority:-1 extents:1 across:2441212k 
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   14.737942] Linux agpgart interface v0.103
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.277522] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.286439] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.317316] r852: driver loaded succesfully
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.341265] input: Dell WMI hotkeys as /devices/virtual/input/input5
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.355905] cfg80211: Calling CRDA to update world regulatory domain
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394836] cfg80211: World regulatory domain updated:
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394841]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394846]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394851]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394855]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394859]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.394862]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.405130] nvidia: module license 'NVIDIA' taints kernel.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.405136] Disabling lock debugging due to kernel taint
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.442179] type=1400 audit(1288930783.263:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=706 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.443182] type=1400 audit(1288930783.263:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.443730] type=1400 audit(1288930783.263:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.558363] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000/0x0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.558368] Synaptics: Clickpad mode enabled
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.558374] serio: Synaptics pass-through port at isa0060/serio1/input0
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.567804] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.594539] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.687222] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.734171] acpi device:30: registered as cooling_device2
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.737838] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2d/LNXVIDEO:00/input/input7
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.738084] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.738177] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.797094] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.798147] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.798151] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.798154] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.876478] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.876605] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   15.985976] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   16.065866] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   16.771577] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   16.771600] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   16.771772] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   16.772151] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   19.741232] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.064476] type=1400 audit(1288930788.883:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1056 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.069701] type=1400 audit(1288930788.891:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1057 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.071228] type=1400 audit(1288930788.891:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1057 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.071783] type=1400 audit(1288930788.891:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1057 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.076985] ppdev: user-space parallel port driver
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.082985] type=1400 audit(1288930788.903:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1058 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.085516] type=1400 audit(1288930788.907:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1062 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.086760] type=1400 audit(1288930788.907:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1062 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.101963] type=1400 audit(1288930788.923:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1129 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.113514] type=1400 audit(1288930788.935:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1058 comm="apparmor_parser"
Nov  5 00:19:48 james-Inspiron-1520 kernel: [   21.137985] type=1400 audit(1288930788.959:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1058 comm="apparmor_parser"
Nov  5 00:19:49 james-Inspiron-1520 kernel: [   21.260058] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov  5 00:19:50 james-Inspiron-1520 kernel: [   21.388598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  5 00:19:50 james-Inspiron-1520 kernel: [   21.420181] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  5 00:19:50 james-Inspiron-1520 kernel: [   22.778073] vboxdrv: fAsync=0 offMin=0x1ce offMax=0x738
Nov  5 00:19:50 james-Inspiron-1520 kernel: [   22.778880] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Nov  5 00:19:52 james-Inspiron-1520 kernel: [   24.928457] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Nov  5 00:19:53 james-Inspiron-1520 kernel: [   25.233253] EXT4-fs (sda6): re-mounted. Opts: commit=0
Nov  5 00:19:54 james-Inspiron-1520 kernel: [   26.848860] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Nov  5 00:19:55 james-Inspiron-1520 kernel: [   27.778974] EXT4-fs (sda6): re-mounted. Opts: commit=0
Nov  5 00:19:56 james-Inspiron-1520 kernel: [   29.081617] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[/PHP]

If you actually read through the whole thing, I give you mad props

---

### Post by HermanAB on 2010-11-05
Howdy,

For the past year or so, the freezing trouble seems to be due to bad video drivers. (Before, it was bad CDROM drivers, but nobody use CDs anymore) My own Sony Laptop has the same issue.  My solution is to use the VESA video driver.

VESA is the generic driver that is used during installation.  It works on all video cards.  However, it doesn't provide video accelleration, so no fancy 3-D desktop for me, but I prefer reliability over fancy graphics.

---

### Post by rob.arntfield on 2010-11-05
have you checked out [this Page]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") ?

---

### Post by thebarisaxkid on 2010-11-05
Aww, oh well.  Thanks for the help you guys!  Hopefully they will fix this bug soon.

---

### Post by HermanAB on 2010-11-05
Don't be too optimistic about a new driver.  I've been stuck using the Vesa driver for a year already.

---

### Post by thebarisaxkid on 2010-11-05
> **HermanAB said:**
> Don't be too optimistic about a new driver.  I've been stuck using the Vesa driver for a year already.

Do you mean pessimistic?  That would make more sense.

---

