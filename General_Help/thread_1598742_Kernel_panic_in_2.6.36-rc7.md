---
title: "Kernel panic in 2.6.36-rc7"
date: 2010-10-16
forum: General Help
---

### Post by pixnaps on 2010-10-16
I followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=9962335&postcount=93") to install 2.6.36-rc7

Unfortunately, it doesn't work for me.  After booting, it displays the splash screen and a couple of startup programs (e.g. guake), but then crashes to a screen of console data.

Here's the relevant section of /var/log/messages
```
Oct 16 22:09:23 rc-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 16 22:09:23 rc-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="771" x-info="http://www.rsyslog.com"] (re)start
Oct 16 22:09:23 rc-laptop rsyslogd: rsyslogd's groupid changed to 103
Oct 16 22:09:23 rc-laptop rsyslogd: rsyslogd's userid changed to 101
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Linux version 2.6.36-020636rc7-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201010070908 SMP Thu Oct 7 10:21:05 UTC 2010
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f680000 (usable)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 000000003f680000 - 000000003f700000 (ACPI NVS)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] DMI present.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] last_pfn = 0x3f680 max_arch_pfn = 0x100000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PAT not supported by CPU.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] modified physical RAM map:
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000003f680000 (usable)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 000000003f680000 - 000000003f700000 (ACPI NVS)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] found SMP MP-table at [c00f7670] f7670
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] RAMDISK: 2eeb6000 - 2f920000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: RSDP 000f75e0 00014 (v00 TOSCPL)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: RSDT 3f6888c2 00054 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: FACP 3f690c78 00074 (v01 TOSCPL CALISTGA 06040000 LOHR 0000005A)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: DSDT 3f68a62d 0664B (v01 TOSCPL CALISTGA 06040000 INTL 20060608)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: FACS 3f691fc0 00040
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: SLIC 3f690cec 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: APIC 3f690e62 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: HPET 3f690eca 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: MCFG 3f690f02 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: BOOT 3f690fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: APIC 3f690f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: SSDT 3f689fda 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: SSDT 3f689948 00692 (v01 SataRe  SataSec 00001000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: SSDT 3f688ea2 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: SSDT 3f688dfc 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: SSDT 3f688916 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] 126MB HIGHMEM available.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] 887MB LOWMEM available.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f680
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Movable zone start PFN for each node
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0003f680
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Using APIC driver default
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s32896 r0 d24448 u2097152
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] pcpu-alloc: s32896 r0 d24448 u2097152 alloc=1*4194304
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257570
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636rc7-generic root=UUID=d238eec3-238a-4ba0-9d9e-e48de8456c42 ro quiet splash ipv6.disable=1
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Initializing CPU#0
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] allocated 5194220 bytes of page_cgroup
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Subtract (53 early reservations)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #2 [0000100000 - 00009d3824]   TEXT DATA BSS
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #3 [002eeb6000 - 002f920000]         RAMDISK
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #4 [00009d4000 - 00009d70f4]             BRK
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #5 [00000f7680 - 0000100000]   BIOS reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #6 [00000f7670 - 00000f7680]    MP-table mpf
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #7 [000009f800 - 000009fd71]   BIOS reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #8 [000009fef5 - 00000f7670]   BIOS reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #9 [000009fd71 - 000009fef5]    MP-table mpc
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #14 [0001001000 - 00017f1000]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #15 [00017f1000 - 00017f1004]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #16 [00017f1040 - 00017f1100]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #17 [00017f1100 - 00017f1154]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #18 [00017f1180 - 00017f4180]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #19 [00017f4180 - 00017f418c]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #20 [00017f41c0 - 00017f47c0]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #21 [00017f47c0 - 00017f47e5]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #22 [00017f4800 - 00017f4827]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #23 [00017f4840 - 00017f4a00]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #24 [00017f4a00 - 00017f4a40]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #25 [00017f4a40 - 00017f4a80]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #26 [00017f4a80 - 00017f4ac0]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #27 [00017f4ac0 - 00017f4b00]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #28 [00017f4b00 - 00017f4b40]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #29 [00017f4b40 - 00017f4b80]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #30 [00017f4b80 - 00017f4bc0]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #31 [00017f4bc0 - 00017f4c00]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #32 [00017f4c00 - 00017f4c40]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #33 [00017f4c40 - 00017f4c80]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #34 [00017f4c80 - 00017f4cc0]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #35 [00017f4cc0 - 00017f4d00]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #36 [00017f4d00 - 00017f4d40]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #37 [00017f4d40 - 00017f4d50]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #38 [00017f4d80 - 00017f4d90]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #39 [00017f4dc0 - 00017f4e40]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #40 [00017f4e40 - 00017f4ec0]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #41 [0001800000 - 000180e000]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #42 [0001a00000 - 0001a0e000]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #43 [00017f6ec0 - 00017f6ec4]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #44 [00017f6f00 - 00017f6f04]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #45 [00017f6f40 - 00017f6f48]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #46 [00017f6f80 - 00017f6f88]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #47 [00017f6fc0 - 00017f7068]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #48 [00017f7080 - 00017f70e8]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #49 [00017f7100 - 00017fb100]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #50 [000180e000 - 000188e000]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #51 [000188e000 - 00018ce000]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]   #52 [0001a0e000 - 0001f021ec]         BOOTMEM
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f680)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Memory: 1004524k/1038848k available (4999k kernel code, 33876k reserved, 2399k data, 740k init, 129544k highmem)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] virtual kernel memory layout:
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]       .init : 0xc083a000 - 0xc08f3000   ( 740 kB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]       .data : 0xc05e1f1f - 0xc0839b28   (2399 kB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc05e1f1f   (4999 kB)
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] console [tty0] enabled
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Oct 16 22:09:23 rc-laptop kernel: [    0.000000] Detected 1729.065 MHz processor.
Oct 16 22:09:23 rc-laptop kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.13 BogoMIPS (lpj=6916260)
Oct 16 22:09:23 rc-laptop kernel: [    0.004014] pid_max: default: 32768 minimum: 301
Oct 16 22:09:23 rc-laptop kernel: [    0.004038] Security Framework initialized
Oct 16 22:09:23 rc-laptop kernel: [    0.004067] AppArmor: AppArmor initialized
Oct 16 22:09:23 rc-laptop kernel: [    0.004131] Mount-cache hash table entries: 512
Oct 16 22:09:23 rc-laptop kernel: [    0.004305] Initializing cgroup subsys ns
Oct 16 22:09:23 rc-laptop kernel: [    0.004310] Initializing cgroup subsys cpuacct
Oct 16 22:09:23 rc-laptop kernel: [    0.004316] Initializing cgroup subsys memory
Oct 16 22:09:23 rc-laptop kernel: [    0.004330] Initializing cgroup subsys devices
Oct 16 22:09:23 rc-laptop kernel: [    0.004334] Initializing cgroup subsys freezer
Oct 16 22:09:23 rc-laptop kernel: [    0.004337] Initializing cgroup subsys net_cls
Oct 16 22:09:23 rc-laptop kernel: [    0.004378] CPU: Physical Processor ID: 0
Oct 16 22:09:23 rc-laptop kernel: [    0.004381] CPU: Processor Core ID: 0
Oct 16 22:09:23 rc-laptop kernel: [    0.004385] mce: CPU supports 6 MCE banks
Oct 16 22:09:23 rc-laptop kernel: [    0.004401] using mwait in idle threads.
Oct 16 22:09:23 rc-laptop kernel: [    0.004411] Performance Events: Core events, core PMU driver.
Oct 16 22:09:23 rc-laptop kernel: [    0.004423] ... version:                1
Oct 16 22:09:23 rc-laptop kernel: [    0.004425] ... bit width:              40
Oct 16 22:09:23 rc-laptop kernel: [    0.004428] ... generic registers:      2
Oct 16 22:09:23 rc-laptop kernel: [    0.004430] ... value mask:             000000ffffffffff
Oct 16 22:09:23 rc-laptop kernel: [    0.004433] ... max period:             000000007fffffff
Oct 16 22:09:23 rc-laptop kernel: [    0.004436] ... fixed-purpose events:   0
Oct 16 22:09:23 rc-laptop kernel: [    0.004438] ... event mask:             0000000000000003
Oct 16 22:09:23 rc-laptop kernel: [    0.013147] ACPI: Core revision 20100702
Oct 16 22:09:23 rc-laptop kernel: [    0.013153] TOSHIBA Satellite detected - force copy of DSDT to local memory
Oct 16 22:09:23 rc-laptop kernel: [    0.016791] ACPI: Forced DSDT copy: length 0x0664B copied locally, original unmapped
Oct 16 22:09:23 rc-laptop kernel: [    0.024011] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 16 22:09:23 rc-laptop kernel: [    0.024022] ftrace: allocating 26008 entries in 51 pages
Oct 16 22:09:23 rc-laptop kernel: [    0.028073] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 16 22:09:23 rc-laptop kernel: [    0.032240] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 16 22:09:23 rc-laptop kernel: [    0.071941] CPU0: Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Oct 16 22:09:23 rc-laptop kernel: [    0.072000] Booting Node   0, Processors  #1 Ok.
Oct 16 22:09:23 rc-laptop kernel: [    0.008000] Initializing CPU#1
Oct 16 22:09:23 rc-laptop kernel: [    0.160021] Brought up 2 CPUs
Oct 16 22:09:23 rc-laptop kernel: [    0.160027] Total of 2 processors activated (6916.20 BogoMIPS).
Oct 16 22:09:23 rc-laptop kernel: [    0.160624] devtmpfs: initialized
Oct 16 22:09:23 rc-laptop kernel: [    0.161306] regulator: core version 0.5
Oct 16 22:09:23 rc-laptop kernel: [    0.161342] Time: 22:09:06  Date: 10/16/10
Oct 16 22:09:23 rc-laptop kernel: [    0.161398] NET: Registered protocol family 16
Oct 16 22:09:23 rc-laptop kernel: [    0.161552] EISA bus registered
Oct 16 22:09:23 rc-laptop kernel: [    0.161563] ACPI: bus type pci registered
Oct 16 22:09:23 rc-laptop kernel: [    0.161656] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Oct 16 22:09:23 rc-laptop kernel: [    0.161662] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Oct 16 22:09:23 rc-laptop kernel: [    0.161664] PCI: Using MMCONFIG for extended config space
Oct 16 22:09:23 rc-laptop kernel: [    0.161667] PCI: Using configuration type 1 for base access
Oct 16 22:09:23 rc-laptop kernel: [    0.164103] bio: create slab <bio-0> at 0
Oct 16 22:09:23 rc-laptop kernel: [    0.172033] ACPI: BIOS _OSI(Linux) query ignored
Oct 16 22:09:23 rc-laptop kernel: [    0.179196] ACPI: SSDT 3f689648 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.180322] ACPI: Dynamic OEM Table Load:
Oct 16 22:09:23 rc-laptop kernel: [    0.180326] ACPI: SSDT (null) 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.180679] ACPI: SSDT 3f689101 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.181135] ACPI: Dynamic OEM Table Load:
Oct 16 22:09:23 rc-laptop kernel: [    0.181140] ACPI: SSDT (null) 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.181612] ACPI: SSDT 3f689880 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.182082] ACPI: Dynamic OEM Table Load:
Oct 16 22:09:23 rc-laptop kernel: [    0.182086] ACPI: SSDT (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.182264] ACPI: SSDT 3f6895c3 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.182722] ACPI: Dynamic OEM Table Load:
Oct 16 22:09:23 rc-laptop kernel: [    0.182726] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Oct 16 22:09:23 rc-laptop kernel: [    0.182996] ACPI: Interpreter enabled
Oct 16 22:09:23 rc-laptop kernel: [    0.183001] ACPI: (supports S0 S3 S4 S5)
Oct 16 22:09:23 rc-laptop kernel: [    0.183028] ACPI: Using IOAPIC for interrupt routing
Oct 16 22:09:23 rc-laptop kernel: [    0.229143] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Oct 16 22:09:23 rc-laptop kernel: [    0.229630] ACPI: No dock devices found.
Oct 16 22:09:23 rc-laptop kernel: [    0.229635] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Oct 16 22:09:23 rc-laptop kernel: [    0.230046] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Oct 16 22:09:23 rc-laptop kernel: [    0.232480] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Oct 16 22:09:23 rc-laptop kernel: [    0.232486] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
Oct 16 22:09:23 rc-laptop kernel: [    0.232494] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1670 (mask 000f)
Oct 16 22:09:23 rc-laptop kernel: [    0.232892] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 16 22:09:23 rc-laptop kernel: [    0.233204] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Oct 16 22:09:23 rc-laptop kernel: [    0.233221] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
Oct 16 22:09:23 rc-laptop kernel: [    0.233576] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Oct 16 22:09:23 rc-laptop kernel: [    0.233592] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
Oct 16 22:09:23 rc-laptop kernel: [    0.234322] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
Oct 16 22:09:23 rc-laptop kernel: [    0.234414] pci_bus 0000:07: [bus 07-0a] partially hidden behind transparent bridge 0000:06 [bus 06-06]
Oct 16 22:09:23 rc-laptop kernel: [    0.240637] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Oct 16 22:09:23 rc-laptop kernel: [    0.240709] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Oct 16 22:09:23 rc-laptop kernel: [    0.240780] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Oct 16 22:09:23 rc-laptop kernel: [    0.240850] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Oct 16 22:09:23 rc-laptop kernel: [    0.240920] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Oct 16 22:09:23 rc-laptop kernel: [    0.240991] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Oct 16 22:09:23 rc-laptop kernel: [    0.241061] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Oct 16 22:09:23 rc-laptop kernel: [    0.241132] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Oct 16 22:09:23 rc-laptop kernel: [    0.241171] HEST: Table is not found!
Oct 16 22:09:23 rc-laptop kernel: [    0.241259] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 16 22:09:23 rc-laptop kernel: [    0.241279] vgaarb: loaded
Oct 16 22:09:23 rc-laptop kernel: [    0.241489] SCSI subsystem initialized
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] usbcore: registered new interface driver usbfs
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] usbcore: registered new interface driver hub
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] usbcore: registered new device driver usb
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] ACPI: WMI: Mapper loaded
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] PCI: Using ACPI for IRQ routing
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] NetLabel: Initializing
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] NetLabel:  domain hash size = 128
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] NetLabel:  unlabeled traffic allowed by default
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 16 22:09:23 rc-laptop kernel: [    0.241510] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Oct 16 22:09:23 rc-laptop kernel: [    0.248024] Switching to clocksource tsc
Oct 16 22:09:23 rc-laptop kernel: [    0.258212] AppArmor: AppArmor Filesystem Enabled
Oct 16 22:09:23 rc-laptop kernel: [    0.258236] pnp: PnP ACPI init
Oct 16 22:09:23 rc-laptop kernel: [    0.258265] ACPI: bus type pnp registered
Oct 16 22:09:23 rc-laptop kernel: [    0.279989] pnp: PnP ACPI: found 10 devices
Oct 16 22:09:23 rc-laptop kernel: [    0.279993] ACPI: ACPI bus type pnp unregistered
Oct 16 22:09:23 rc-laptop kernel: [    0.279997] PnPBIOS: Disabled by ACPI PNP
Oct 16 22:09:23 rc-laptop kernel: [    0.280017] system 00:01: [io  0xfe00-0xfe7f] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280021] system 00:01: [io  0xfe80-0xfeff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280025] system 00:01: [io  0xff00-0xff7f] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280030] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280034] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280039] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280043] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280047] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280051] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280055] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280059] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280069] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280077] system 00:06: [io  0x0800-0x080f] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280081] system 00:06: [io  0x1000-0x107f] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.280085] system 00:06: [io  0x1180-0x11bf] has been reserved
Oct 16 22:09:23 rc-laptop kernel: [    0.316739] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316744] pci 0000:00:1e.0: BAR 13: assigned [io  0x5000-0x5fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316749] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 16 22:09:23 rc-laptop kernel: [    0.316754] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316762] pci 0000:00:1c.0:   bridge window [mem 0xd6000000-0xd7ffffff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316769] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316779] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
Oct 16 22:09:23 rc-laptop kernel: [    0.316784] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316792] pci 0000:00:1c.1:   bridge window [mem 0xd8000000-0xd9ffffff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316799] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316809] pci 0000:05:00.0: BAR 6: assigned [mem 0xd4000000-0xd401ffff pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316814] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
Oct 16 22:09:23 rc-laptop kernel: [    0.316819] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316827] pci 0000:00:1c.2:   bridge window [mem 0xda000000-0xdbffffff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316833] pci 0000:00:1c.2:   bridge window [mem 0xd4000000-0xd5ffffff 64bit pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316845] pci 0000:06:04.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316850] pci 0000:06:04.0: BAR 16: assigned [mem 0x44000000-0x47ffffff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316854] pci 0000:06:04.0: BAR 0: assigned [mem 0xdc006000-0xdc006fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316862] pci 0000:06:04.0: BAR 0: set to [mem 0xdc006000-0xdc006fff] (PCI address [0xdc006000-0xdc006fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316867] pci 0000:06:04.0: BAR 13: assigned [io  0x5000-0x50ff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316871] pci 0000:06:04.0: BAR 14: assigned [io  0x5400-0x54ff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316875] pci 0000:06:04.0: CardBus bridge to [bus 07-0a]
Oct 16 22:09:23 rc-laptop kernel: [    0.316878] pci 0000:06:04.0:   bridge window [io  0x5000-0x50ff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316885] pci 0000:06:04.0:   bridge window [io  0x5400-0x54ff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316892] pci 0000:06:04.0:   bridge window [mem 0x40000000-0x43ffffff pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316900] pci 0000:06:04.0:   bridge window [mem 0x44000000-0x47ffffff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316907] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
Oct 16 22:09:23 rc-laptop kernel: [    0.316912] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316920] pci 0000:00:1e.0:   bridge window [mem 0xdc000000-0xdc0fffff]
Oct 16 22:09:23 rc-laptop kernel: [    0.316927] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
Oct 16 22:09:23 rc-laptop kernel: [    0.316962] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 16 22:09:23 rc-laptop kernel: [    0.316989] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Oct 16 22:09:23 rc-laptop kernel: [    0.317015] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 16 22:09:23 rc-laptop kernel: [    0.317047] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 16 22:09:23 rc-laptop kernel: [    0.317182] NET: Registered protocol family 2
Oct 16 22:09:23 rc-laptop kernel: [    0.317279] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.317621] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.318616] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.319066] TCP: Hash tables configured (established 131072 bind 65536)
Oct 16 22:09:23 rc-laptop kernel: [    0.319070] TCP reno registered
Oct 16 22:09:23 rc-laptop kernel: [    0.319075] UDP hash table entries: 512 (order: 2, 16384 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.319091] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.319241] NET: Registered protocol family 1
Oct 16 22:09:23 rc-laptop kernel: [    0.319510] Trying to unpack rootfs image as initramfs...
Oct 16 22:09:23 rc-laptop kernel: [    0.705331] Freeing initrd memory: 10664k freed
Oct 16 22:09:23 rc-laptop kernel: [    0.713019] Simple Boot Flag at 0x36 set to 0x1
Oct 16 22:09:23 rc-laptop kernel: [    0.713295] cpufreq-nforce2: No nForce2 chipset.
Oct 16 22:09:23 rc-laptop kernel: [    0.713335] Scanning for low memory corruption every 60 seconds
Oct 16 22:09:23 rc-laptop kernel: [    0.713570] audit: initializing netlink socket (disabled)
Oct 16 22:09:23 rc-laptop kernel: [    0.713588] type=2000 audit(1287266946.708:1): initialized
Oct 16 22:09:23 rc-laptop kernel: [    0.727074] highmem bounce pool size: 64 pages
Oct 16 22:09:23 rc-laptop kernel: [    0.727082] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Oct 16 22:09:23 rc-laptop kernel: [    0.729077] VFS: Disk quotas dquot_6.5.2
Oct 16 22:09:23 rc-laptop kernel: [    0.729162] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 16 22:09:23 rc-laptop kernel: [    0.729992] fuse init (API version 7.15)
Oct 16 22:09:23 rc-laptop kernel: [    0.730128] msgmni has been set to 1729
Oct 16 22:09:23 rc-laptop kernel: [    0.730443] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 16 22:09:23 rc-laptop kernel: [    0.730447] io scheduler noop registered
Oct 16 22:09:23 rc-laptop kernel: [    0.730450] io scheduler deadline registered
Oct 16 22:09:23 rc-laptop kernel: [    0.730471] io scheduler cfq registered (default)
Oct 16 22:09:23 rc-laptop kernel: [    0.730692] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 16 22:09:23 rc-laptop kernel: [    0.730721] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 16 22:09:23 rc-laptop kernel: [    0.730998] ACPI: AC Adapter [ACAD] (on-line)
Oct 16 22:09:23 rc-laptop kernel: [    0.731112] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Oct 16 22:09:23 rc-laptop kernel: [    0.731136] ACPI: Lid Switch [LID0]
Oct 16 22:09:23 rc-laptop kernel: [    0.731195] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Oct 16 22:09:23 rc-laptop kernel: [    0.731201] ACPI: Power Button [PWRB]
Oct 16 22:09:23 rc-laptop kernel: [    0.731278] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Oct 16 22:09:23 rc-laptop kernel: [    0.731283] ACPI: Power Button [PWRF]
Oct 16 22:09:23 rc-laptop kernel: [    0.734349] Marking TSC unstable due to TSC halts in idle
Oct 16 22:09:23 rc-laptop kernel: [    0.734437] Switching to clocksource hpet
Oct 16 22:09:23 rc-laptop kernel: [    0.760336] ERST: Table is not found!
Oct 16 22:09:23 rc-laptop kernel: [    0.760355] isapnp: Scanning for PnP cards...
Oct 16 22:09:23 rc-laptop kernel: [    0.804506] ACPI: EC: GPE storm detected, transactions will use polling mode
Oct 16 22:09:23 rc-laptop kernel: [    0.960095] ACPI: Battery Slot [BAT1] (battery present)
Oct 16 22:09:23 rc-laptop kernel: [    1.114535] isapnp: No Plug & Play device found
Oct 16 22:09:23 rc-laptop kernel: [    1.114812] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 16 22:09:23 rc-laptop kernel: [    1.116815] brd: module loaded
Oct 16 22:09:23 rc-laptop kernel: [    1.117546] loop: module loaded
Oct 16 22:09:23 rc-laptop kernel: [    1.117836] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 16 22:09:23 rc-laptop kernel: [    1.117844] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Oct 16 22:09:23 rc-laptop kernel: [    1.272163] scsi0 : ata_piix
Oct 16 22:09:23 rc-laptop kernel: [    1.272298] scsi1 : ata_piix
Oct 16 22:09:23 rc-laptop kernel: [    1.273339] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
Oct 16 22:09:23 rc-laptop kernel: [    1.273344] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
Oct 16 22:09:23 rc-laptop kernel: [    1.273808] Fixed MDIO Bus: probed
Oct 16 22:09:23 rc-laptop kernel: [    1.273853] PPP generic driver version 2.4.2
Oct 16 22:09:23 rc-laptop kernel: [    1.273914] tun: Universal TUN/TAP device driver, 1.6
Oct 16 22:09:23 rc-laptop kernel: [    1.273917] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 16 22:09:23 rc-laptop kernel: [    1.274027] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 16 22:09:23 rc-laptop kernel: [    1.274070] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 16 22:09:23 rc-laptop kernel: [    1.274093] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 16 22:09:23 rc-laptop kernel: [    1.274138] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Oct 16 22:09:23 rc-laptop kernel: [    1.274164] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Oct 16 22:09:23 rc-laptop kernel: [    1.274179] ehci_hcd 0000:00:1d.7: debug port 1
Oct 16 22:09:23 rc-laptop kernel: [    1.278086] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdc444000
Oct 16 22:09:23 rc-laptop kernel: [    1.292021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 16 22:09:23 rc-laptop kernel: [    1.292179] hub 1-0:1.0: USB hub found
Oct 16 22:09:23 rc-laptop kernel: [    1.292186] hub 1-0:1.0: 8 ports detected
Oct 16 22:09:23 rc-laptop kernel: [    1.292309] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 16 22:09:23 rc-laptop kernel: [    1.292328] uhci_hcd: USB Universal Host Controller Interface driver
Oct 16 22:09:23 rc-laptop kernel: [    1.292364] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 16 22:09:23 rc-laptop kernel: [    1.292378] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 16 22:09:23 rc-laptop kernel: [    1.292422] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 16 22:09:23 rc-laptop kernel: [    1.292453] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Oct 16 22:09:23 rc-laptop kernel: [    1.292619] hub 2-0:1.0: USB hub found
Oct 16 22:09:23 rc-laptop kernel: [    1.292625] hub 2-0:1.0: 2 ports detected
Oct 16 22:09:23 rc-laptop kernel: [    1.292712] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 16 22:09:23 rc-laptop kernel: [    1.292725] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 16 22:09:23 rc-laptop kernel: [    1.292771] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Oct 16 22:09:23 rc-laptop kernel: [    1.292814] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
Oct 16 22:09:23 rc-laptop kernel: [    1.292979] hub 3-0:1.0: USB hub found
Oct 16 22:09:23 rc-laptop kernel: [    1.292987] hub 3-0:1.0: 2 ports detected
Oct 16 22:09:23 rc-laptop kernel: [    1.293069] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 16 22:09:23 rc-laptop kernel: [    1.293082] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 16 22:09:23 rc-laptop kernel: [    1.293124] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Oct 16 22:09:23 rc-laptop kernel: [    1.293169] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Oct 16 22:09:23 rc-laptop kernel: [    1.293339] hub 4-0:1.0: USB hub found
Oct 16 22:09:23 rc-laptop kernel: [    1.293344] hub 4-0:1.0: 2 ports detected
Oct 16 22:09:23 rc-laptop kernel: [    1.293426] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Oct 16 22:09:23 rc-laptop kernel: [    1.293439] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 16 22:09:23 rc-laptop kernel: [    1.293486] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Oct 16 22:09:23 rc-laptop kernel: [    1.293528] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Oct 16 22:09:23 rc-laptop kernel: [    1.293680] hub 5-0:1.0: USB hub found
Oct 16 22:09:23 rc-laptop kernel: [    1.293686] hub 5-0:1.0: 2 ports detected
Oct 16 22:09:23 rc-laptop kernel: [    1.293855] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 16 22:09:23 rc-laptop kernel: [    1.294198] i8042.c: Detected active multiplexing controller, rev 1.1.
Oct 16 22:09:23 rc-laptop kernel: [    1.294284] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 16 22:09:23 rc-laptop kernel: [    1.294295] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct 16 22:09:23 rc-laptop kernel: [    1.294299] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct 16 22:09:23 rc-laptop kernel: [    1.294303] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct 16 22:09:23 rc-laptop kernel: [    1.294308] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct 16 22:09:23 rc-laptop kernel: [    1.294413] mice: PS/2 mouse device common for all mice
Oct 16 22:09:23 rc-laptop kernel: [    1.294591] rtc_cmos 00:07: RTC can wake from S4
Oct 16 22:09:23 rc-laptop kernel: [    1.294650] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Oct 16 22:09:23 rc-laptop kernel: [    1.294686] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Oct 16 22:09:23 rc-laptop kernel: [    1.294833] device-mapper: uevent: version 1.0.3
Oct 16 22:09:23 rc-laptop kernel: [    1.295009] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
Oct 16 22:09:23 rc-laptop kernel: [    1.295108] device-mapper: multipath: version 1.1.1 loaded
Oct 16 22:09:23 rc-laptop kernel: [    1.295112] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 16 22:09:23 rc-laptop kernel: [    1.295299] EISA: Probing bus 0 at eisa.0
Oct 16 22:09:23 rc-laptop kernel: [    1.295308] Cannot allocate resource for EISA slot 1
Oct 16 22:09:23 rc-laptop kernel: [    1.295311] Cannot allocate resource for EISA slot 2
Oct 16 22:09:23 rc-laptop kernel: [    1.295314] Cannot allocate resource for EISA slot 3
Oct 16 22:09:23 rc-laptop kernel: [    1.295317] Cannot allocate resource for EISA slot 4
Oct 16 22:09:23 rc-laptop kernel: [    1.295320] Cannot allocate resource for EISA slot 5
Oct 16 22:09:23 rc-laptop kernel: [    1.295336] EISA: Detected 0 cards.
Oct 16 22:09:23 rc-laptop kernel: [    1.295516] cpuidle: using governor ladder
Oct 16 22:09:23 rc-laptop kernel: [    1.295670] cpuidle: using governor menu
Oct 16 22:09:23 rc-laptop kernel: [    1.296156] TCP cubic registered
Oct 16 22:09:23 rc-laptop kernel: [    1.296159] IPv6: Loaded, but administratively disabled, reboot required to enable
Oct 16 22:09:23 rc-laptop kernel: [    1.296164] NET: Registered protocol family 17
Oct 16 22:09:23 rc-laptop kernel: [    1.296188] Registering the dns_resolver key type
Oct 16 22:09:23 rc-laptop kernel: [    1.296607] Using IPI No-Shortcut mode
Oct 16 22:09:23 rc-laptop kernel: [    1.296745] registered taskstats version 1
Oct 16 22:09:23 rc-laptop kernel: [    1.297124] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Oct 16 22:09:23 rc-laptop kernel: [    1.297175]   Magic number: 14:178:199
Oct 16 22:09:23 rc-laptop kernel: [    1.297334] rtc_cmos 00:07: setting system clock to 2010-10-16 22:09:07 UTC (1287266947)
Oct 16 22:09:23 rc-laptop kernel: [    1.297339] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 16 22:09:23 rc-laptop kernel: [    1.297341] EDD information not available.
Oct 16 22:09:23 rc-laptop kernel: [    1.436494] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.90, max UDMA/33
Oct 16 22:09:23 rc-laptop kernel: [    1.436853] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL130M, max UDMA/100
Oct 16 22:09:23 rc-laptop kernel: [    1.436858] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 16 22:09:23 rc-laptop kernel: [    1.444500] ata1.00: configured for UDMA/100
Oct 16 22:09:23 rc-laptop kernel: [    1.444731] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL13 PQ: 0 ANSI: 5
Oct 16 22:09:23 rc-laptop kernel: [    1.444922] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Oct 16 22:09:23 rc-laptop kernel: [    1.444944] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 16 22:09:23 rc-laptop kernel: [    1.445006] sd 0:0:0:0: [sda] Write Protect is off
Oct 16 22:09:23 rc-laptop kernel: [    1.445100] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 16 22:09:23 rc-laptop kernel: [    1.452368] ata2.00: configured for UDMA/33
Oct 16 22:09:23 rc-laptop kernel: [    1.454726] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.90 PQ: 0 ANSI: 5
Oct 16 22:09:23 rc-laptop kernel: [    1.459331] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 16 22:09:23 rc-laptop kernel: [    1.459336] cdrom: Uniform CD-ROM driver Revision: 3.20
Oct 16 22:09:23 rc-laptop kernel: [    1.459535] sr 1:0:0:0: Attached scsi generic sg1 type 5
Oct 16 22:09:23 rc-laptop kernel: [    1.512823]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Oct 16 22:09:23 rc-laptop kernel: [    1.513518] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 16 22:09:23 rc-laptop kernel: [    1.513575] Freeing unused kernel memory: 740k freed
Oct 16 22:09:23 rc-laptop kernel: [    1.514108] Write protecting the kernel text: 5000k
Oct 16 22:09:23 rc-laptop kernel: [    1.514184] Write protecting the kernel read-only data: 2048k
Oct 16 22:09:23 rc-laptop kernel: [    1.536523] udev[71]: starting version 163
Oct 16 22:09:23 rc-laptop kernel: [    1.734656] sdhci: Secure Digital Host Controller Interface driver
Oct 16 22:09:23 rc-laptop kernel: [    1.734661] sdhci: Copyright(c) Pierre Ossman
Oct 16 22:09:23 rc-laptop kernel: [    1.739589] sdhci-pci 0000:06:04.3: SDHCI controller found [104c:803c] (rev 0)
Oct 16 22:09:23 rc-laptop kernel: [    1.739616] sdhci-pci 0000:06:04.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 16 22:09:23 rc-laptop kernel: [    1.739670] mmc0: no vmmc regulator found
Oct 16 22:09:23 rc-laptop kernel: [    1.740464] mmc0: SDHCI controller on PCI [0000:06:04.3] using DMA
Oct 16 22:09:23 rc-laptop kernel: [    1.744491] firewire_ohci 0000:06:04.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 16 22:09:23 rc-laptop kernel: [    1.747417] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 16 22:09:23 rc-laptop kernel: [    1.747447] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 16 22:09:23 rc-laptop kernel: [    1.747986] r8169 0000:05:00.0: eth0: RTL8101e at 0xf80e8000, 00:1b:38:42:01:f1, XID 94200000 IRQ 40
Oct 16 22:09:23 rc-laptop kernel: [    1.800131] firewire_ohci: Added fw-ohci device 0000:06:04.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Oct 16 22:09:23 rc-laptop kernel: [    2.304176] firewire_core: created device fw0: GUID 00023f78a8406924, S400
Oct 16 22:09:23 rc-laptop kernel: [    2.414761] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Oct 16 22:09:23 rc-laptop kernel: [    4.596483] Adding 2048252k swap on /dev/sda5.  Priority:-1 extents:1 across:2048252k 
Oct 16 22:09:23 rc-laptop kernel: [    6.979046] udev[332]: starting version 163
Oct 16 22:09:23 rc-laptop kernel: [    8.984336] Linux agpgart interface v0.103
Oct 16 22:09:23 rc-laptop kernel: [    9.028219] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Oct 16 22:09:23 rc-laptop kernel: [    9.028725] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Oct 16 22:09:23 rc-laptop kernel: [    9.031605] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Oct 16 22:09:23 rc-laptop kernel: [    9.072170] acpi device:07: registered as cooling_device2
Oct 16 22:09:23 rc-laptop kernel: [    9.072320] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input4
Oct 16 22:09:23 rc-laptop kernel: [    9.072399] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct 16 22:09:23 rc-laptop kernel: [    9.090025] tifm_7xx1 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 16 22:09:23 rc-laptop kernel: [    9.230407] apparmor_parser[483]: segfault at 0 ip b7669158 sp bfbd532c error 4 in libc-2.12.1.so[b75f5000+157000]
Oct 16 22:09:23 rc-laptop kernel: [    9.254405] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 16 22:09:23 rc-laptop kernel: [    9.444862] lp: driver loaded but no devices found
Oct 16 22:09:23 rc-laptop kernel: [    9.493644] [drm] Initialized drm 1.1.0 20060810
Oct 16 22:09:23 rc-laptop kernel: [    9.549003] yenta_cardbus 0000:06:04.0: CardBus bridge found [1179:ff00]
Oct 16 22:09:23 rc-laptop kernel: [    9.549033] yenta_cardbus 0000:06:04.0: Enabling burst memory read transactions
Oct 16 22:09:23 rc-laptop kernel: [    9.549041] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
Oct 16 22:09:23 rc-laptop kernel: [    9.549045] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
Oct 16 22:09:23 rc-laptop kernel: [    9.549052] yenta_cardbus 0000:06:04.0: TI: mfunc 0x10aa1b22, devctl 0x64
Oct 16 22:09:23 rc-laptop kernel: [    9.780865] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
Oct 16 22:09:23 rc-laptop kernel: [    9.780872] yenta_cardbus 0000:06:04.0: Socket status: 30000006
Oct 16 22:09:23 rc-laptop kernel: [    9.780878] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #06 to #0a
Oct 16 22:09:23 rc-laptop kernel: [    9.780893] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
Oct 16 22:09:23 rc-laptop kernel: [    9.780898] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: excluding 0x5000-0x50ff 0x5400-0x54ff
Oct 16 22:09:23 rc-laptop kernel: [    9.788189] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0xdc000000-0xdc0fffff]
Oct 16 22:09:23 rc-laptop kernel: [    9.788195] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdc000000-0xdc0fffff: excluding 0xdc000000-0xdc00ffff
Oct 16 22:09:23 rc-laptop kernel: [    9.788214] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
Oct 16 22:09:23 rc-laptop kernel: [    9.788218] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
Oct 16 22:09:23 rc-laptop kernel: [    9.806629] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 16 22:09:23 rc-laptop kernel: [    9.809769] [drm] set up 7M of stolen space
Oct 16 22:09:23 rc-laptop kernel: [    9.898160] apparmor_parser[609]: segfault at 0 ip b7652158 sp bfa56d6c error 4 in libc-2.12.1.so[b75de000+157000]
Oct 16 22:09:23 rc-laptop kernel: [    9.915507] intel_rng: FWH not detected
Oct 16 22:09:23 rc-laptop kernel: [    9.915992] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Oct 16 22:09:23 rc-laptop kernel: [    9.916629] [drm] initialized overlay support
Oct 16 22:09:23 rc-laptop kernel: [   10.024119] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
Oct 16 22:09:23 rc-laptop kernel: [   10.024129] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
Oct 16 22:09:23 rc-laptop kernel: [   10.044852] cfg80211: Calling CRDA to update world regulatory domain
Oct 16 22:09:23 rc-laptop kernel: [   10.063929] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
Oct 16 22:09:23 rc-laptop kernel: [   10.585248] Console: switching to colour frame buffer device 160x50
Oct 16 22:09:23 rc-laptop kernel: [   10.593879] fb0: inteldrmfb frame buffer device
Oct 16 22:09:23 rc-laptop kernel: [   10.593882] drm: registered panic notifier
Oct 16 22:09:23 rc-laptop kernel: [   10.593901] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 16 22:09:23 rc-laptop kernel: [   10.599418] leds_ss4200: no LED devices found
Oct 16 22:09:23 rc-laptop kernel: [   10.636338] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Oct 16 22:09:23 rc-laptop kernel: [   10.822422] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
Oct 16 22:09:23 rc-laptop kernel: [   10.824540] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
Oct 16 22:09:23 rc-laptop kernel: [   10.825434] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Oct 16 22:09:23 rc-laptop kernel: [   10.826171] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Oct 16 22:09:23 rc-laptop kernel: [   10.826987] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
Oct 16 22:09:23 rc-laptop kernel: [   10.827065] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Oct 16 22:09:23 rc-laptop kernel: [   10.827142] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
Oct 16 22:09:23 rc-laptop kernel: [   10.827221] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Oct 16 22:09:23 rc-laptop kernel: [   10.955158] ath5k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 16 22:09:23 rc-laptop kernel: [   10.955241] ath5k 0000:04:00.0: registered as 'phy0'
Oct 16 22:09:23 rc-laptop kernel: [   11.636060] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 16 22:09:23 rc-laptop kernel: [   12.086776] cfg80211: World regulatory domain updated:
Oct 16 22:09:23 rc-laptop kernel: [   12.086782]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 16 22:09:23 rc-laptop kernel: [   12.086786]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:09:23 rc-laptop kernel: [   12.086790]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:09:23 rc-laptop kernel: [   12.086794]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:09:23 rc-laptop kernel: [   12.086798]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:09:23 rc-laptop kernel: [   12.086802]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:09:23 rc-laptop kernel: [   12.189623] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)
Oct 16 22:09:24 rc-laptop kernel: [   17.930049] apparmor_parser[877]: segfault at 0 ip 08051034 sp bf93cf80 error 4
Oct 16 22:09:24 rc-laptop kernel: [   17.930059] apparmor_parser[876]: segfault at 0 ip 08051034 sp bf80de70 error 4 in apparmor_parser[8048000+be000]
Oct 16 22:09:24 rc-laptop kernel: [   17.930070]  in apparmor_parser[8048000+be000]
Oct 16 22:09:25 rc-laptop kernel: [   18.943479] apparmor_parser[908]: segfault at 0 ip 08051034 sp bfe24200 error 4 in apparmor_parser[8048000+be000]
Oct 16 22:09:25 rc-laptop kernel: [   19.668690] ppdev: user-space parallel port driver
Oct 16 22:09:29 rc-laptop kernel: [   22.906205] r8169 0000:05:00.0: eth0: link up
Oct 16 22:09:29 rc-laptop kernel: [   22.906226] r8169 0000:05:00.0: eth0: link up
Oct 16 22:09:35 rc-laptop kernel: [   28.883125] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Oct 16 22:09:36 rc-laptop pulseaudio[1435]: lock-autospawn.c: Cannot access autospawn lock.
Oct 16 22:09:43 rc-laptop kernel: [   37.320024] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Oct 16 22:10:05 rc-laptop kernel: [   59.371651] *pde = 00000000 
Oct 16 22:10:05 rc-laptop kernel: [   59.371884] Modules linked in: binfmt_misc parport_pc ppdev arc4 snd_hda_codec_realtek snd_hda_intel snd_hda_codec ath5k snd_hwdep snd_pcm snd_seq_midi snd_rawmidi pcmcia snd_seq_midi_event joydev mac80211 ath snd_seq cfg80211 i915 drm_kms_helper yenta_socket pcmcia_rsrc snd_timer drm i2c_algo_bit psmouse shpchp lp tifm_7xx1 tifm_core pcmcia_core snd_seq_device intel_agp serio_raw agpgart video output snd soundcore parport snd_page_alloc r8169 firewire_ohci sdhci_pci sdhci firewire_core led_class crc_itu_t mii
Oct 16 22:10:05 rc-laptop kernel: [   59.372662] 
Oct 16 22:10:05 rc-laptop kernel: [   59.372686] Pid: 1030, comm: python Not tainted 2.6.36-020636rc7-generic #201010070908 IAKAA/Satellite A135
Oct 16 22:10:05 rc-laptop kernel: [   59.372815] EIP: 0060:[<c04a20ba>] EFLAGS: 00010297 CPU: 0
Oct 16 22:10:05 rc-laptop kernel: [   59.372889] EIP is at evdev_do_ioctl+0x49a/0x5a0
Oct 16 22:10:05 rc-laptop kernel: [   59.372952] EAX: 00000258 EBX: 00000019 ECX: 00000014 EDX: f7153c00
Oct 16 22:10:05 rc-laptop kernel: [   59.373036] ESI: 00000014 EDI: ef2d76c0 EBP: ef7edf40 ESP: ef7ededc
Oct 16 22:10:05 rc-laptop kernel: [   59.373119]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Oct 16 22:10:05 rc-laptop kernel: [   59.373320]  fffff000 ef7d19f8 bfaa191b f7153c00 c17e52ac ef7d9b70 ef7edf2c c01fabb7
Oct 16 22:10:05 rc-laptop kernel: [   59.373448] <0> fffb3e58 ef7d9b70 c17e52ac 3a1db065 b7396548 ef7d19f8 ef659dc0 fffb3e58
Oct 16 22:10:05 rc-laptop kernel: [   59.373586] <0> 01000246 ef7d19f8 00000007 b7396548 ef7edfac c05ddd68 ef466a00 ef466a48
Oct 16 22:10:05 rc-laptop kernel: [   59.373765]  [<c01fabb7>] ? handle_mm_fault+0x287/0x2c0
Oct 16 22:10:05 rc-laptop kernel: [   59.373838]  [<c05ddd68>] ? do_page_fault+0x248/0x490
Oct 16 22:10:05 rc-laptop kernel: [   59.373908]  [<c04a2229>] ? evdev_ioctl_handler+0x69/0x70
Oct 16 22:10:05 rc-laptop kernel: [   59.373981]  [<c04a2230>] ? evdev_ioctl+0x0/0x20
Oct 16 22:10:05 rc-laptop kernel: [   59.374045]  [<c04a2247>] ? evdev_ioctl+0x17/0x20
Oct 16 22:10:05 rc-laptop kernel: [   59.374110]  [<c022d0db>] ? vfs_ioctl+0x3b/0x50
Oct 16 22:10:05 rc-laptop kernel: [   59.374172]  [<c022dc74>] ? do_vfs_ioctl+0x64/0x1c0
Oct 16 22:10:05 rc-laptop kernel: [   59.374240]  [<c030b635>] ? security_file_ioctl+0x15/0x20
Oct 16 22:10:05 rc-laptop kernel: [   59.374312]  [<c022de27>] ? sys_ioctl+0x57/0x70
Oct 16 22:10:05 rc-laptop kernel: [   59.374376]  [<c0102cdf>] ? sysenter_do_call+0x12/0x28
Oct 16 22:10:05 rc-laptop kernel: [   59.409212] ---[ end trace dbfc1ee5962c53a2 ]---
Oct 16 22:10:09 rc-laptop kernel: [   63.251617] dropbox[1596]: segfault at 0 ip b64a04bc sp bfb53740 error 4 in libpango-1.0.so.0.2800.1[b6486000+3f000]
Oct 16 22:12:25 rc-laptop kernel: [  199.201109] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Oct 16 22:12:26 rc-laptop kernel: [  200.568612] cfg80211: Calling CRDA to update world regulatory domain
Oct 16 22:12:26 rc-laptop kernel: [  200.589846] cfg80211: World regulatory domain updated:
Oct 16 22:12:26 rc-laptop kernel: [  200.589932]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 16 22:12:26 rc-laptop kernel: [  200.590032]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:12:26 rc-laptop kernel: [  200.590127]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:12:26 rc-laptop kernel: [  200.590222]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:12:26 rc-laptop kernel: [  200.590316]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:12:26 rc-laptop kernel: [  200.590411]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 16 22:12:44 rc-laptop kernel: [  218.643636] SysRq : Keyboard mode set to system default
Oct 16 22:12:46 rc-laptop kernel: [  220.134583] SysRq : Terminate All Tasks
```
In particular, "EIP is at evdev_do_ioctl+0x49a/0x5a0", and there are segfaults in apparmor_parser and dropbox

Any suggestions for how to fix this?

---

