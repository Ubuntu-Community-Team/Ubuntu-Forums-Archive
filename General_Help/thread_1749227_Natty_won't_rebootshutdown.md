---
title: "Natty won't reboot/shutdown"
date: 2011-05-04
forum: General Help
---

### Post by blimbo on 2011-05-04
Natty won't shutdown for me - the start up/shutting down graphic comes up and the 'light' go down from 5 to 3 then it just hangs there.

Is there a shutdown log? I've looked in /var/log/messages but there's nothing relevant there.

---

### Post by ikt on 2011-05-04
Should be in the syslog, there's also the option of switching to another vterm and seeing if there's any strange output there.

---

### Post by blimbo on 2011-05-05
This is the output of my syslog. The first line is the last one before I did a sudo reboot. Nothing obvious as to why it's not shutting down properly. Any ideas?

```
May  5 13:23:10 translocon AptDaemon: INFO: Initializing daemon
May  5 13:25:23 translocon sudo: pam_sm_authenticate: Called
May  5 13:25:23 translocon sudo: pam_sm_authenticate: username = [xxxxxxx]
May  5 13:25:23 translocon kernel: Kernel logging (proc) stopped.
May  5 13:25:23 translocon rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="736" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  5 13:29:40 translocon kernel: imklog 4.6.4, log source = /proc/kmsg started.
May  5 13:29:40 translocon rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="773" x-info="http://www.rsyslog.com"] (re)start
May  5 13:29:40 translocon rsyslogd: rsyslogd's groupid changed to 103
May  5 13:29:40 translocon rsyslogd: rsyslogd's userid changed to 101
May  5 13:29:40 translocon rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  5 13:29:40 translocon kernel: [    0.000000] Initializing cgroup subsys cpuset
May  5 13:29:40 translocon kernel: [    0.000000] Initializing cgroup subsys cpu
May  5 13:29:40 translocon kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
May  5 13:29:40 translocon kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=a717e728-70c3-44c7-87ff-e07b8f369d09 ro quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
May  5 13:29:40 translocon kernel: [    0.000000] BIOS-provided physical RAM map:
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000091800 (usable)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 0000000000091800 - 00000000000a0000 (reserved)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf278000 (usable)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000cf278000 - 00000000cf2bc000 (reserved)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000cf2bc000 - 00000000cf5b7000 (usable)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000cf5b7000 - 00000000cf5e7000 (reserved)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000cf5e7000 - 00000000cf7e7000 (ACPI NVS)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000cf7e7000 - 00000000cf7ff000 (ACPI data)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000cf7ff000 - 00000000cf800000 (usable)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 00000000ffc20000 (reserved)
May  5 13:29:40 translocon kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000022e000000 (usable)
May  5 13:29:40 translocon kernel: [    0.000000] NX (Execute Disable) protection: active
May  5 13:29:40 translocon kernel: [    0.000000] DMI 2.6 present.
May  5 13:29:40 translocon kernel: [    0.000000] DMI: Dell Inc. OptiPlex 990/06D7TR, BIOS A02 02/26/2011
May  5 13:29:40 translocon kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May  5 13:29:40 translocon kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
May  5 13:29:40 translocon kernel: [    0.000000] No AGP bridge found
May  5 13:29:40 translocon kernel: [    0.000000] last_pfn = 0x22e000 max_arch_pfn = 0x400000000
May  5 13:29:40 translocon kernel: [    0.000000] MTRR default type: uncachable
May  5 13:29:40 translocon kernel: [    0.000000] MTRR fixed ranges enabled:
May  5 13:29:40 translocon kernel: [    0.000000]   00000-9FFFF write-back
May  5 13:29:40 translocon kernel: [    0.000000]   A0000-BFFFF uncachable
May  5 13:29:40 translocon kernel: [    0.000000]   C0000-FFFFF write-protect
May  5 13:29:40 translocon kernel: [    0.000000] MTRR variable ranges enabled:
May  5 13:29:40 translocon kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
May  5 13:29:40 translocon kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
May  5 13:29:40 translocon kernel: [    0.000000]   2 base 0C0000000 mask FF0000000 write-back
May  5 13:29:40 translocon kernel: [    0.000000]   3 base 100000000 mask F00000000 write-back
May  5 13:29:40 translocon kernel: [    0.000000]   4 base 200000000 mask FE0000000 write-back
May  5 13:29:40 translocon kernel: [    0.000000]   5 base 220000000 mask FF0000000 write-back
May  5 13:29:40 translocon kernel: [    0.000000]   6 base 22E000000 mask FFE000000 uncachable
May  5 13:29:40 translocon kernel: [    0.000000]   7 base 0FFC00000 mask FFFC00000 write-protect
May  5 13:29:40 translocon kernel: [    0.000000]   8 disabled
May  5 13:29:40 translocon kernel: [    0.000000]   9 disabled
May  5 13:29:40 translocon kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  5 13:29:40 translocon kernel: [    0.000000] last_pfn = 0xcf800 max_arch_pfn = 0x400000000
May  5 13:29:40 translocon kernel: [    0.000000] found SMP MP-table at [ffff8800000f20a0] f20a0
May  5 13:29:40 translocon kernel: [    0.000000] initial memory mapped : 0 - 20000000
May  5 13:29:40 translocon kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cf800000
May  5 13:29:40 translocon kernel: [    0.000000]  0000000000 - 00cf800000 page 2M
May  5 13:29:40 translocon kernel: [    0.000000] kernel direct mapping tables up to cf800000 @ 1fffb000-20000000
May  5 13:29:40 translocon kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000022e000000
May  5 13:29:40 translocon kernel: [    0.000000]  0100000000 - 022e000000 page 2M
May  5 13:29:40 translocon kernel: [    0.000000] kernel direct mapping tables up to 22e000000 @ cf5ad000-cf5b7000
May  5 13:29:40 translocon kernel: [    0.000000] RAMDISK: 35c78000 - 36e34000
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: RSDP 00000000000fe300 00024 (v02 DELL  )
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: XSDT 00000000cf7fde18 00074 (v01 DELL    CBX3    06222004 MSFT 00010013)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: FACP 00000000cf787d98 000F4 (v04 DELL    CBX3    06222004 MSFT 00010013)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110112/tbfadt-369)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCF7E4E40/0x00000000CF7E4D40, using 32 (20110112/tbfadt-486)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: DSDT 00000000cf771018 07485 (v02 INT430 SYSFexxx 00001001 INTL 20090903)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: FACS 00000000cf7e4e40 00040
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: APIC 00000000cf7fcf18 000CC (v02 DELL    CBX3    06222004 MSFT 00010013)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: TCPA 00000000cf7e5d18 00032 (v02                 00000000      00000000)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: MCFG 00000000cf7e5c98 0003C (v01 DELL   SNDYBRDG 06222004 MSFT 00000097)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: HPET 00000000cf7e5c18 00038 (v01 A M I   PCHHPET 06222004 AMI. 00000003)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: BOOT 00000000cf7e5b98 00028 (v01 DELL   CBX3     06222004 AMI  00010013)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: SSDT 00000000cf77e018 00804 (v01  PmRef  Cpu0Ist 00003000 INTL 20090903)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: SSDT 00000000cf77d018 00996 (v01  PmRef    CpuPm 00003000 INTL 20090903)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: DMAR 00000000cf7e4a18 000B0 (v01 INTEL      SNB  00000001 INTL 00000001)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: SLIC 00000000cf788a18 00176 (v03 DELL    CBX3    06222004 MSFT 00010013)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 13:29:40 translocon kernel: [    0.000000] No NUMA configuration found
May  5 13:29:40 translocon kernel: [    0.000000] Faking a node at 0000000000000000-000000022e000000
May  5 13:29:40 translocon kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000022e000000
May  5 13:29:40 translocon kernel: [    0.000000]   NODE_DATA [000000022dffb000 - 000000022dffffff]
May  5 13:29:40 translocon kernel: [    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880225e00000-ffff88022cffffff] on node 0
May  5 13:29:40 translocon kernel: [    0.000000] Zone PFN ranges:
May  5 13:29:40 translocon kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May  5 13:29:40 translocon kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May  5 13:29:40 translocon kernel: [    0.000000]   Normal   0x00100000 -> 0x0022e000
May  5 13:29:40 translocon kernel: [    0.000000] Movable zone start PFN for each node
May  5 13:29:40 translocon kernel: [    0.000000] early_node_map[5] active PFN ranges
May  5 13:29:40 translocon kernel: [    0.000000]     0: 0x00000010 -> 0x00000091
May  5 13:29:40 translocon kernel: [    0.000000]     0: 0x00000100 -> 0x000cf278
May  5 13:29:40 translocon kernel: [    0.000000]     0: 0x000cf2bc -> 0x000cf5b7
May  5 13:29:40 translocon kernel: [    0.000000]     0: 0x000cf7ff -> 0x000cf800
May  5 13:29:40 translocon kernel: [    0.000000]     0: 0x00100000 -> 0x0022e000
May  5 13:29:40 translocon kernel: [    0.000000] On node 0 totalpages: 2086133
May  5 13:29:40 translocon kernel: [    0.000000]   DMA zone: 56 pages used for memmap
May  5 13:29:40 translocon kernel: [    0.000000]   DMA zone: 6 pages reserved
May  5 13:29:40 translocon kernel: [    0.000000]   DMA zone: 3907 pages, LIFO batch:0
May  5 13:29:40 translocon kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
May  5 13:29:40 translocon kernel: [    0.000000]   DMA32 zone: 830892 pages, LIFO batch:31
May  5 13:29:40 translocon kernel: [    0.000000]   Normal zone: 16912 pages used for memmap
May  5 13:29:40 translocon kernel: [    0.000000]   Normal zone: 1220080 pages, LIFO batch:31
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  5 13:29:40 translocon kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: IRQ0 used by override.
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: IRQ2 used by override.
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: IRQ9 used by override.
May  5 13:29:40 translocon kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  5 13:29:40 translocon kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
May  5 13:29:40 translocon kernel: [    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
May  5 13:29:40 translocon kernel: [    0.000000] nr_irqs_gsi: 40
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 0000000000091000 - 0000000000092000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000cf278000 - 00000000cf2bc000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000cf5b7000 - 00000000cf5e7000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000cf5e7000 - 00000000cf7e7000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000cf7e7000 - 00000000cf7ff000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000cf800000 - 00000000fed1c000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ffc00000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffc20000
May  5 13:29:40 translocon kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc20000 - 0000000100000000
May  5 13:29:40 translocon kernel: [    0.000000] Allocating PCI resources starting at cf800000 (gap: cf800000:2f51c000)
May  5 13:29:40 translocon kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  5 13:29:40 translocon kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
May  5 13:29:40 translocon kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cf000000 s84416 r8192 d22080 u131072
May  5 13:29:40 translocon kernel: [    0.000000] pcpu-alloc: s84416 r8192 d22080 u131072 alloc=1*2097152
May  5 13:29:40 translocon kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
May  5 13:29:40 translocon kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2054879
May  5 13:29:40 translocon kernel: [    0.000000] Policy zone: Normal
May  5 13:29:40 translocon kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=a717e728-70c3-44c7-87ff-e07b8f369d09 ro quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
May  5 13:29:40 translocon kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  5 13:29:40 translocon kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
May  5 13:29:40 translocon kernel: [    0.000000] Checking aperture...
May  5 13:29:40 translocon kernel: [    0.000000] No AGP bridge found
```

---

### Post by MattKP on 2011-05-20
Are you running fglrx? If so your problem might be related to ours [http://ubuntuforums.org/showthread.php?t=1720894](http://ubuntuforums.org/showthread.php?t=1720894)

---

### Post by jonathansfl on 2012-01-24
i have the same problem shutting off my Tabletkiosk tablet pc. if i kill gnome i can shutdown from the terminal window, but i can't shutdown or restart from the button with my mouse. it tries, but it sits there forever after the desktop disappears.

this happened on 10.04 also, so we upgraded hoping that would help, but it didn't.

---

