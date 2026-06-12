---
title: "Computer frozen by morning, everyday."
date: 2010-11-23
forum: General Help
---

### Post by Philip550c on 2010-11-23
Ok I have been battling with my machine for a while now, it cannot go 24 hours without freezing, i leave it on at night and in the morning it is frozen. I want to use it as a content server to my mobile devices but I have to be home to use it because it always needs a reset. I did a memtest and there were many errors, I realized that my ram voltages were under the min req. I boosted the voltage and ran memtest for 48 hours, no errors. This machine used to be stable for over two years, same hardware, I switched the case and now it wont last a day. I am running 10.10 64bit, I would post log files but I dont know which one would be useful. Any recommendations? I believe it becomes unstable when the screensaver activates. Also sometimes it wont fully boot but will go to the command line and other times it will give random error messages when grub is trying to load. Every week I solve one problem and then something else goes wrong. I have been using ubuntu since hardy on this machine and only lately (10.04 & 10.10) have the problems been occuring. Thanks in advance.

---

### Post by matt_symes on 2010-11-23
Hi

 > I switched the case and now it wont last a day.

Case and PSU?

Kind regards.

---

### Post by Philip550c on 2010-11-23
> **matt_symes said:**
> Hi

 

Case and PSU?

Kind regards.

No just the case

---

### Post by damang111 on 2010-11-23
post logs for last few days from /var/log/messages, /var/log/syslog .

could be anything.  most likely hardware related, power supply, ram, etc .

---

### Post by matt_symes on 2010-11-23
Hi

> **damang111 said:**
> post logs for last few days from /var/log/messages, /var/log/syslog .

could be anything.  most likely hardware related, power supply, ram, etc .

Good call. Also post them inside code tags. Use the # sign in the message toolbar.

```
Like this
```
Kind regards

---

### Post by Philip550c on 2010-11-23
> **damang111 said:**
> post logs for last few days from /var/log/messages, /var/log/syslog .

could be anything.  most likely hardware related, power supply, ram, etc .

When I try to load those logs they load for a second and then gedit says it cannot detect the character encoding but i could load the files messages.1 and syslog.1, is this normal? Here is what they say:

SYSLOG.1

```
Nov 20 00:17:01 philip-desktop CRON[8109]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 20 00:27:30 philip-desktop kernel: [ 7968.071273] usb 2-1: new high speed USB device using ehci_hcd and address 3
Nov 20 00:27:30 philip-desktop kernel: [ 7968.260271] Initializing USB Mass Storage driver...
Nov 20 00:27:30 philip-desktop kernel: [ 7968.260449] scsi10 : usb-storage 2-1:1.0
Nov 20 00:27:30 philip-desktop kernel: [ 7968.260521] usbcore: registered new interface driver usb-storage
Nov 20 00:27:30 philip-desktop kernel: [ 7968.260522] USB Mass Storage support registered.
Nov 20 00:27:31 philip-desktop kernel: [ 7969.260934] scsi 10:0:0:0: Direct-Access     Motorola A855             0001 PQ: 0 ANSI: 2
Nov 20 00:27:31 philip-desktop kernel: [ 7969.262021] sd 10:0:0:0: Attached scsi generic sg2 type 0
Nov 20 00:27:31 philip-desktop kernel: [ 7969.265783] sd 10:0:0:0: [sdb] Attached SCSI removable disk
Nov 20 00:39:01 philip-desktop CRON[8149]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 20 00:43:09 philip-desktop sudo: pam_sm_authenticate: Called
Nov 20 00:43:09 philip-desktop sudo: pam_sm_authenticate: username = [philip]
Nov 20 00:44:51 philip-desktop sudo: pam_sm_authenticate: Called
Nov 20 00:44:51 philip-desktop sudo: pam_sm_authenticate: username = [philip]
Nov 20 00:50:17 philip-desktop kernel: [ 9335.240027] usb 2-1: reset high speed USB device using ehci_hcd and address 3
Nov 22 17:31:33 philip-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 22 17:31:33 philip-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="996" x-info="http://www.rsyslog.com"] (re)start
Nov 22 17:31:33 philip-desktop rsyslogd: rsyslogd's groupid changed to 103
Nov 22 17:31:33 philip-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 22 17:31:33 philip-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=80e1f0c8-97bc-46fd-82ab-15337f8c59c1 ro quiet splash
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee2000 (ACPI NVS)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfee2000 - 00000000dfef0000 (ACPI data)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] DMI 2.4 present.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] No AGP bridge found
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] MTRR default type: uncachable
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   00000-9FFFF write-back
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   C0000-CCFFF write-protect
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   CD000-EFFFF uncachable
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   F0000-FFFFF write-through
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   2 base 100000000 mask FE0000000 write-back
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   3 base 0DFF00000 mask FFFF00000 uncachable
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   4 disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   5 disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   6 disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   7 disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] last_pfn = 0xdfee0 max_arch_pfn = 0x400000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] modified physical RAM map:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfee0000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000dfee0000 - 00000000dfee2000 (ACPI NVS)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000dfee2000 - 00000000dfef0000 (ACPI data)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dff00000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000f4000000 - 00000000f8000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f5670] f5670
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dfee0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  0000000000 - 00dfe00000 page 2M
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  00dfe00000 - 00dfee0000 page 4k
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] kernel direct mapping tables up to dfee0000 @ 16000-1c000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  0100000000 - 0120000000 page 2M
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] kernel direct mapping tables up to 120000000 @ 1a000-20000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] RAMDISK: 36fbf000 - 37ff0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f7070 00014 (v00 GBT   )
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: RSDT 00000000dfee2040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: FACP 00000000dfee20c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: DSDT 00000000dfee2180 04C5A (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: FACS 00000000dfee0000 00040
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: HPET 00000000dfee6f40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: MCFG 00000000dfee6fc0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: EUDS 00000000dfee7000 00560 (v01 GBT             00000000      00000000)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: TAMG 00000000dfee7560 06852 (v01 GBT    GBT   B0 5455312E BG?? 00020101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: APIC 00000000dfee6e40 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: SSDT 00000000dfeee420 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] No NUMA configuration found
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000120000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00120000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000dfee0
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] On node 0 totalpages: 1048173
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA zone: 3925 pages, LIFO batch:0
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA32 zone: 898840 pages, LIFO batch:31
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   Normal zone: 1792 pages used for memmap
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   Normal zone: 129280 pages, LIFO batch:31
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] nr_irqs_gsi: 40
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] early_res array is doubled to 64 at [1b000 - 1b7ff]
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfee0000 - 00000000dfee2000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfee2000 - 00000000dfef0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfef0000 - 00000000dff00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000f4000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Allocating PCI resources starting at dff00000 (gap: dff00000:14100000)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1032045
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Policy zone: Normal
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=80e1f0c8-97bc-46fd-82ab-15337f8c59c1 ro quiet splash
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Checking aperture...
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] No AGP bridge found
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] early_res array is doubled to 128 at [23800 - 247ff]
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Subtract (57 early reservations)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #2 [0036fbf000 - 0037ff0000]         RAMDISK
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #3 [0001d18000 - 0001d180f6]             BRK
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #4 [00000f5680 - 0000100000]   BIOS reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #5 [00000f5670 - 00000f5680]    MP-table mpf
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #6 [000009dc00 - 00000f0d00]   BIOS reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #7 [00000f0eb4 - 00000f5670]   BIOS reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #8 [00000f0d00 - 00000f0eb4]    MP-table mpc
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #12 [000001a000 - 000001b000]         PGTABLE
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #14 [0001d18100 - 0001d19100]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #18 [0100200000 - 0103c00000]        MEMMAP 0
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #20 [0001d19100 - 0001d31100]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #21 [0001d31100 - 0001d34100]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #22 [0001d35000 - 0001d36000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #25 [0001d176c0 - 0001d17928]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #26 [0001d17940 - 0001d179a8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #27 [0001d179c0 - 0001d17a28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #28 [0001d17a40 - 0001d17aa8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #29 [0001d17ac0 - 0001d17b28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #30 [0001d17b40 - 0001d17ba8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #31 [0001d17bc0 - 0001d17c28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #32 [0001d17c40 - 0001d17ca8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #33 [0001d17cc0 - 0001d17d28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #34 [0001d17d40 - 0001d17da8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #35 [0001d17dc0 - 0001d17e28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #36 [0001d17e40 - 0001d17e60]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #37 [0001d17e80 - 0001d17ea0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #38 [0001d17ec0 - 0001d17f2a]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #39 [0001d17f40 - 0001d17faa]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #40 [0001e00000 - 0001e1e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #42 [0001f00000 - 0001f1e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #43 [0001f80000 - 0001f9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #44 [0001d17fc0 - 0001d17fc8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #45 [0001d34100 - 0001d34108]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #46 [0001d34140 - 0001d34150]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #47 [0001d34180 - 0001d341a0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #48 [0001d341c0 - 0001d342f0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #49 [0001d34300 - 0001d34350]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #50 [0001d34380 - 0001d343d0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #51 [0001d36000 - 0001d3e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #52 [0001d34400 - 0001d34640]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #53 [0001f9e000 - 0005f9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #54 [0001d3e000 - 0001d5e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #55 [0001d5e000 - 0001d9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #56 [000001b800 - 0000023800]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Memory: 4036652k/4718592k available (5708k kernel code, 525900k absent, 156040k reserved, 5382k data, 908k init)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:712
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] console [tty0] enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] hpet clockevent registered
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Detected 2800.579 MHz processor.
Nov 22 17:31:33 philip-desktop kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5601.15 BogoMIPS (lpj=28005790)
Nov 22 17:31:33 philip-desktop kernel: [    0.010011] pid_max: default: 32768 minimum: 301
Nov 22 17:31:33 philip-desktop kernel: [    0.010030] Security Framework initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.010046] AppArmor: AppArmor initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.010047] Yama: becoming mindful.
Nov 22 17:31:33 philip-desktop kernel: [    0.010385] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.012021] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.012796] Mount-cache hash table entries: 256
Nov 22 17:31:33 philip-desktop kernel: [    0.012917] Initializing cgroup subsys ns
Nov 22 17:31:33 philip-desktop kernel: [    0.012922] Initializing cgroup subsys cpuacct
Nov 22 17:31:33 philip-desktop kernel: [    0.012925] Initializing cgroup subsys memory
Nov 22 17:31:33 philip-desktop kernel: [    0.012932] Initializing cgroup subsys devices
Nov 22 17:31:33 philip-desktop kernel: [    0.012934] Initializing cgroup subsys freezer
Nov 22 17:31:33 philip-desktop kernel: [    0.012936] Initializing cgroup subsys net_cls
Nov 22 17:31:33 philip-desktop kernel: [    0.012960] CPU: Physical Processor ID: 0
Nov 22 17:31:33 philip-desktop kernel: [    0.012961] CPU: Processor Core ID: 0
Nov 22 17:31:33 philip-desktop kernel: [    0.012963] mce: CPU supports 6 MCE banks
Nov 22 17:31:33 philip-desktop kernel: [    0.012969] CPU0: Thermal monitoring enabled (TM2)
Nov 22 17:31:33 philip-desktop kernel: [    0.012973] using mwait in idle threads.
Nov 22 17:31:33 philip-desktop kernel: [    0.012974] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Nov 22 17:31:33 philip-desktop kernel: [    0.012981] ... version:                2
Nov 22 17:31:33 philip-desktop kernel: [    0.012982] ... bit width:              40
Nov 22 17:31:33 philip-desktop kernel: [    0.012983] ... generic registers:      2
Nov 22 17:31:33 philip-desktop kernel: [    0.012984] ... value mask:             000000ffffffffff
Nov 22 17:31:33 philip-desktop kernel: [    0.012986] ... max period:             000000007fffffff
Nov 22 17:31:33 philip-desktop kernel: [    0.012987] ... fixed-purpose events:   3
Nov 22 17:31:33 philip-desktop kernel: [    0.012988] ... event mask:             0000000700000003
Nov 22 17:31:33 philip-desktop kernel: [    0.015078] ACPI: Core revision 20100428
Nov 22 17:31:33 philip-desktop kernel: [    0.019796] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov 22 17:31:33 philip-desktop kernel: [    0.019801] ftrace: allocating 22680 entries in 89 pages
Nov 22 17:31:33 philip-desktop kernel: [    0.028257] Setting APIC routing to flat
Nov 22 17:31:33 philip-desktop kernel: [    0.028564] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 22 17:31:33 philip-desktop kernel: [    0.128599] CPU0: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz stepping 0a
Nov 22 17:31:33 philip-desktop kernel: [    0.130000] Booting Node   0, Processors  #1
Nov 22 17:31:33 philip-desktop kernel: [    0.290014] Brought up 2 CPUs
Nov 22 17:31:33 philip-desktop kernel: [    0.290016] Total of 2 processors activated (11201.31 BogoMIPS).
Nov 22 17:31:33 philip-desktop kernel: [    0.290561] devtmpfs: initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.290561] regulator: core version 0.5
Nov 22 17:31:33 philip-desktop kernel: [    0.290574] Time:  1:31:17  Date: 11/23/10
Nov 22 17:31:33 philip-desktop kernel: [    0.290604] NET: Registered protocol family 16
Nov 22 17:31:33 philip-desktop kernel: [    0.290621] Trying to unpack rootfs image as initramfs...
Nov 22 17:31:33 philip-desktop kernel: [    0.290704] ACPI: bus type pci registered
Nov 22 17:31:33 philip-desktop kernel: [    0.290759] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
Nov 22 17:31:33 philip-desktop kernel: [    0.290761] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
Nov 22 17:31:33 philip-desktop kernel: [    0.298954] PCI: Using configuration type 1 for base access
Nov 22 17:31:33 philip-desktop kernel: [    0.310067] bio: create slab <bio-0> at 0
Nov 22 17:31:33 philip-desktop kernel: [    0.310827] ACPI: EC: Look up EC in DSDT
Nov 22 17:31:33 philip-desktop kernel: [    0.317109] ACPI Warning: Incorrect checksum in table [TAMG] - 0x41, should be 0x40 (20100428/tbutils-314)
Nov 22 17:31:33 philip-desktop kernel: [    0.317115] ACPI: SSDT 00000000dfeede00 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317299] ACPI: Dynamic OEM Table Load:
Nov 22 17:31:33 philip-desktop kernel: [    0.317302] ACPI: SSDT (null) 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317466] ACPI: SSDT 00000000dfeee2c0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317644] ACPI: Dynamic OEM Table Load:
Nov 22 17:31:33 philip-desktop kernel: [    0.317646] ACPI: SSDT (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317693] ACPI: Interpreter enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.317695] ACPI: (supports S0 S3 S4 S5)
Nov 22 17:31:33 philip-desktop kernel: [    0.317710] ACPI: Using IOAPIC for interrupt routing
Nov 22 17:31:33 philip-desktop kernel: [    0.321702] ACPI: No dock devices found.
Nov 22 17:31:33 philip-desktop kernel: [    0.321705] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 22 17:31:33 philip-desktop kernel: [    0.321788] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
Nov 22 17:31:33 philip-desktop kernel: [    0.321945] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Nov 22 17:31:33 philip-desktop kernel: [    0.321947] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.321949] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.321951] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.321953] pci_root PNP0A03:00: host bridge window [mem 0xdff00000-0xfebfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.322012] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.322014] pci 0000:00:01.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.322070] pci 0000:00:1a.0: reg 20: [io  0xff00-0xff1f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322127] pci 0000:00:1a.1: reg 20: [io  0xfe00-0xfe1f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322183] pci 0000:00:1a.2: reg 20: [io  0xfd00-0xfd1f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322230] pci 0000:00:1a.7: reg 10: [mem 0xfdfff000-0xfdfff3ff]
Nov 22 17:31:33 philip-desktop kernel: [    0.322293] pci 0000:00:1b.0: reg 10: [mem 0xfdff8000-0xfdffbfff 64bit]
Nov 22 17:31:33 philip-desktop kernel: [    0.322328] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.322331] pci 0000:00:1b.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.322386] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.322389] pci 0000:00:1c.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.322445] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.322448] pci 0000:00:1c.1: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.322503] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.322507] pci 0000:00:1c.3: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.322563] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.322566] pci 0000:00:1c.4: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.322611] pci 0000:00:1d.0: reg 20: [io  0xfc00-0xfc1f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322666] pci 0000:00:1d.1: reg 20: [io  0xfb00-0xfb1f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322723] pci 0000:00:1d.2: reg 20: [io  0xfa00-0xfa1f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322770] pci 0000:00:1d.7: reg 10: [mem 0xfdffe000-0xfdffe3ff]
Nov 22 17:31:33 philip-desktop kernel: [    0.322906] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
Nov 22 17:31:33 philip-desktop kernel: [    0.322909] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
Nov 22 17:31:33 philip-desktop kernel: [    0.322912] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
Nov 22 17:31:33 philip-desktop kernel: [    0.322915] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
Nov 22 17:31:33 philip-desktop kernel: [    0.322964] pci 0000:00:1f.2: reg 10: [io  0xf900-0xf907]
Nov 22 17:31:33 philip-desktop kernel: [    0.322969] pci 0000:00:1f.2: reg 14: [io  0xf800-0xf803]
Nov 22 17:31:33 philip-desktop kernel: [    0.322973] pci 0000:00:1f.2: reg 18: [io  0xf700-0xf707]
Nov 22 17:31:33 philip-desktop kernel: [    0.322978] pci 0000:00:1f.2: reg 1c: [io  0xf600-0xf603]
Nov 22 17:31:33 philip-desktop kernel: [    0.322982] pci 0000:00:1f.2: reg 20: [io  0xf500-0xf51f]
Nov 22 17:31:33 philip-desktop kernel: [    0.322987] pci 0000:00:1f.2: reg 24: [mem 0xfdffd000-0xfdffd7ff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323013] pci 0000:00:1f.2: PME# supported from D3hot
Nov 22 17:31:33 philip-desktop kernel: [    0.323016] pci 0000:00:1f.2: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.323039] pci 0000:00:1f.3: reg 10: [mem 0xfdffc000-0xfdffc0ff 64bit]
Nov 22 17:31:33 philip-desktop kernel: [    0.323050] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
Nov 22 17:31:33 philip-desktop kernel: [    0.323105] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323112] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.323120] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
Nov 22 17:31:33 philip-desktop kernel: [    0.323124] pci 0000:01:00.0: reg 24: [io  0xcf00-0xcf7f]
Nov 22 17:31:33 philip-desktop kernel: [    0.323129] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.323166] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov 22 17:31:33 philip-desktop kernel: [    0.323169] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323171] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323175] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.323210] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Nov 22 17:31:33 philip-desktop kernel: [    0.323213] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.323217] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.323222] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.323290] pci 0000:03:00.0: reg 10: [mem 0xfd800000-0xfd9fffff 64bit]
Nov 22 17:31:33 philip-desktop kernel: [    0.323363] pci 0000:03:00.0: supports D1 D2
Nov 22 17:31:33 philip-desktop kernel: [    0.323365] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Nov 22 17:31:33 philip-desktop kernel: [    0.323370] pci 0000:03:00.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.323391] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 22 17:31:33 philip-desktop kernel: [    0.323400] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Nov 22 17:31:33 philip-desktop kernel: [    0.323403] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.323407] pci 0000:00:1c.1:   bridge window [mem 0xfd800000-0xfd9fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323411] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.323513] pci 0000:04:00.0: reg 24: [mem 0xfdefe000-0xfdefffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323548] pci 0000:04:00.0: PME# supported from D3hot
Nov 22 17:31:33 philip-desktop kernel: [    0.323552] pci 0000:04:00.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.323595] pci 0000:04:00.1: reg 10: [io  0xbf00-0xbf07]
Nov 22 17:31:33 philip-desktop kernel: [    0.323604] pci 0000:04:00.1: reg 14: [io  0xbe00-0xbe03]
Nov 22 17:31:33 philip-desktop kernel: [    0.323611] pci 0000:04:00.1: reg 18: [io  0xbd00-0xbd07]
Nov 22 17:31:33 philip-desktop kernel: [    0.323619] pci 0000:04:00.1: reg 1c: [io  0xbc00-0xbc03]
Nov 22 17:31:33 philip-desktop kernel: [    0.323627] pci 0000:04:00.1: reg 20: [io  0xbb00-0xbb0f]
Nov 22 17:31:33 philip-desktop kernel: [    0.323682] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 22 17:31:33 philip-desktop kernel: [    0.323694] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
Nov 22 17:31:33 philip-desktop kernel: [    0.323697] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323700] pci 0000:00:1c.3:   bridge window [mem 0xfde00000-0xfdefffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323705] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.323764] pci 0000:05:00.0: reg 10: [io  0xee00-0xeeff]
Nov 22 17:31:33 philip-desktop kernel: [    0.323782] pci 0000:05:00.0: reg 18: [mem 0xfdbff000-0xfdbfffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.323795] pci 0000:05:00.0: reg 20: [mem 0xfdbe0000-0xfdbeffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.323802] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.323837] pci 0000:05:00.0: supports D1 D2
Nov 22 17:31:33 philip-desktop kernel: [    0.323839] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.323843] pci 0000:05:00.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.340021] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
Nov 22 17:31:33 philip-desktop kernel: [    0.340026] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340030] pci 0000:00:1c.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340035] pci 0000:00:1c.4:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.340079] pci 0000:06:02.0: reg 10: [mem 0xfdde0000-0xfddeffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340085] pci 0000:06:02.0: reg 14: [io  0xdf00-0xdf07]
Nov 22 17:31:33 philip-desktop kernel: [    0.340129] pci 0000:06:02.0: PME# supported from D0 D3hot D3cold
Nov 22 17:31:33 philip-desktop kernel: [    0.340132] pci 0000:06:02.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.340164] pci 0000:06:07.0: reg 10: [mem 0xfddff000-0xfddff7ff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340170] pci 0000:06:07.0: reg 14: [mem 0xfddf8000-0xfddfbfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340208] pci 0000:06:07.0: supports D1 D2
Nov 22 17:31:33 philip-desktop kernel: [    0.340210] pci 0000:06:07.0: PME# supported from D0 D1 D2 D3hot
Nov 22 17:31:33 philip-desktop kernel: [    0.340213] pci 0000:06:07.0: PME# disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.340246] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.340249] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340252] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.340257] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.340260] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.340261] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.340263] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.340265] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.340267] pci 0000:00:1e.0:   bridge window [mem 0xdff00000-0xfebfffff] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.340296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 22 17:31:33 philip-desktop kernel: [    0.340429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Nov 22 17:31:33 philip-desktop kernel: [    0.340469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Nov 22 17:31:33 philip-desktop kernel: [    0.340510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Nov 22 17:31:33 philip-desktop kernel: [    0.340560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Nov 22 17:31:33 philip-desktop kernel: [    0.340601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Nov 22 17:31:33 philip-desktop kernel: [    0.353080] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353155] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353229] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353302] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353375] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.353448] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353521] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353595] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353630] HEST: Table is not found!
Nov 22 17:31:33 philip-desktop kernel: [    0.353705] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Nov 22 17:31:33 philip-desktop kernel: [    0.353710] vgaarb: loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.353827] SCSI subsystem initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.353898] libata version 3.00 loaded.
Nov 22 17:31:33 philip-desktop kernel: [    0.353935] usbcore: registered new interface driver usbfs
Nov 22 17:31:33 philip-desktop kernel: [    0.353943] usbcore: registered new interface driver hub
Nov 22 17:31:33 philip-desktop kernel: [    0.353960] usbcore: registered new device driver usb
Nov 22 17:31:33 philip-desktop kernel: [    0.354056] ACPI: WMI: Mapper loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.354057] PCI: Using ACPI for IRQ routing
Nov 22 17:31:33 philip-desktop kernel: [    0.354059] PCI: pci_cache_line_size set to 64 bytes
Nov 22 17:31:33 philip-desktop kernel: [    0.354149] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
Nov 22 17:31:33 philip-desktop kernel: [    0.354151] reserve RAM buffer: 00000000dfee0000 - 00000000dfffffff 
Nov 22 17:31:33 philip-desktop kernel: [    0.354228] NetLabel: Initializing
Nov 22 17:31:33 philip-desktop kernel: [    0.354229] NetLabel:  domain hash size = 128
Nov 22 17:31:33 philip-desktop kernel: [    0.354230] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 22 17:31:33 philip-desktop kernel: [    0.354240] NetLabel:  unlabeled traffic allowed by default
Nov 22 17:31:33 philip-desktop kernel: [    0.354263] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Nov 22 17:31:33 philip-desktop kernel: [    0.354267] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 22 17:31:33 philip-desktop kernel: [    0.354271] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Nov 22 17:31:33 philip-desktop kernel: [    0.360023] Switching to clocksource tsc
Nov 22 17:31:33 philip-desktop kernel: [    0.367478] AppArmor: AppArmor Filesystem Enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.367494] pnp: PnP ACPI init
Nov 22 17:31:33 philip-desktop kernel: [    0.367510] ACPI: bus type pnp registered
Nov 22 17:31:33 philip-desktop kernel: [    0.369270] pnp: PnP ACPI: found 11 devices
Nov 22 17:31:33 philip-desktop kernel: [    0.369272] ACPI: ACPI bus type pnp unregistered
Nov 22 17:31:33 philip-desktop kernel: [    0.369282] system 00:01: [io  0x04d0-0x04d1] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369285] system 00:01: [io  0x0290-0x029f] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369287] system 00:01: [io  0x0800-0x087f] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369289] system 00:01: [io  0x0290-0x0294] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369291] system 00:01: [io  0x0880-0x088f] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369296] system 00:07: [io  0x0400-0x04cf] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369298] system 00:07: [io  0x04d2-0x04ff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369302] system 00:08: [mem 0xf4000000-0xf7ffffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369306] system 00:09: [mem 0x000d6000-0x000d7fff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369308] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369310] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369313] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369315] system 00:09: [mem 0xdfee0000-0xdfefffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369317] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369319] system 00:09: [mem 0x00100000-0xdfedffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369321] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369323] system 00:09: [mem 0xfed10000-0xfed1dfff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369325] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369327] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369329] system 00:09: [mem 0xffb00000-0xffb7ffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369331] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369333] system 00:09: [mem 0x000e0000-0x000effff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.374870] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf01fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374874] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374876] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374879] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374882] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374884] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374886] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374889] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov 22 17:31:33 philip-desktop kernel: [    0.374891] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374894] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374896] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374900] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Nov 22 17:31:33 philip-desktop kernel: [    0.374902] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374906] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf01fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374909] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374914] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Nov 22 17:31:33 philip-desktop kernel: [    0.374916] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374920] pci 0000:00:1c.1:   bridge window [mem 0xfd800000-0xfd9fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374923] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374928] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
Nov 22 17:31:33 philip-desktop kernel: [    0.374930] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374934] pci 0000:00:1c.3:   bridge window [mem 0xfde00000-0xfdefffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374937] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374943] pci 0000:05:00.0: BAR 6: assigned [mem 0xfdb00000-0xfdb0ffff pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374945] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
Nov 22 17:31:33 philip-desktop kernel: [    0.374948] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374952] pci 0000:00:1c.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374955] pci 0000:00:1c.4:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374961] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
Nov 22 17:31:33 philip-desktop kernel: [    0.374963] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374967] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374970] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Nov 22 17:31:33 philip-desktop kernel: [    0.374981]   alloc irq_desc for 16 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.374982]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.374988] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.374991] pci 0000:00:01.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.374997] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Nov 22 17:31:33 philip-desktop kernel: [    0.375000] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.375004] pci 0000:00:1c.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.375010] pci 0000:00:1c.1: enabling device (0006 -> 0007)
Nov 22 17:31:33 philip-desktop kernel: [    0.375013]   alloc irq_desc for 17 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.375014]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.375017] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 22 17:31:33 philip-desktop kernel: [    0.375020] pci 0000:00:1c.1: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.375026]   alloc irq_desc for 19 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.375027]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.375030] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.375033] pci 0000:00:1c.3: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.375039] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.375042] pci 0000:00:1c.4: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.375047] pci 0000:00:1e.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.375051] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Nov 22 17:31:33 philip-desktop kernel: [    0.375052] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375054] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375056] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375057] pci_bus 0000:00: resource 8 [mem 0xdff00000-0xfebfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375059] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375061] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375063] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.375064] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375066] pci_bus 0000:02: resource 1 [mem 0xf0000000-0xf01fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375068] pci_bus 0000:02: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.375070] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375071] pci_bus 0000:03: resource 1 [mem 0xfd800000-0xfd9fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375073] pci_bus 0000:03: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.375075] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375076] pci_bus 0000:04: resource 1 [mem 0xfde00000-0xfdefffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375078] pci_bus 0000:04: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.375080] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375082] pci_bus 0000:05: resource 1 [mem 0xfdc00000-0xfdcfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375084] pci_bus 0000:05: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.375085] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375087] pci_bus 0000:06: resource 1 [mem 0xfdd00000-0xfddfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375089] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
Nov 22 17:31:33 philip-desktop kernel: [    0.375090] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375092] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375093] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000dffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375095] pci_bus 0000:06: resource 8 [mem 0xdff00000-0xfebfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.375127] NET: Registered protocol family 2
Nov 22 17:31:33 philip-desktop kernel: [    0.375248] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.376200] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.379565] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.380029] TCP: Hash tables configured (established 524288 bind 65536)
Nov 22 17:31:33 philip-desktop kernel: [    0.380031] TCP reno registered
Nov 22 17:31:33 philip-desktop kernel: [    0.380041] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.380073] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.380198] NET: Registered protocol family 1
Nov 22 17:31:33 philip-desktop kernel: [    0.419895] pci 0000:01:00.0: Boot video device
Nov 22 17:31:33 philip-desktop kernel: [    0.419913] PCI: CLS 4 bytes, default 64
Nov 22 17:31:33 philip-desktop kernel: [    0.419916] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Nov 22 17:31:33 philip-desktop kernel: [    0.419918] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
Nov 22 17:31:33 philip-desktop kernel: [    0.419920] software IO TLB at phys 0x1f9e000 - 0x5f9e000
Nov 22 17:31:33 philip-desktop kernel: [    0.420102] Scanning for low memory corruption every 60 seconds
Nov 22 17:31:33 philip-desktop kernel: [    0.420233] audit: initializing netlink socket (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.420243] type=2000 audit(1290475877.410:1): initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.431160] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 22 17:31:33 philip-desktop kernel: [    0.432228] VFS: Disk quotas dquot_6.5.2
Nov 22 17:31:33 philip-desktop kernel: [    0.432268] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.432688] fuse init (API version 7.14)
Nov 22 17:31:33 philip-desktop kernel: [    0.432748] msgmni has been set to 7884
Nov 22 17:31:33 philip-desktop kernel: [    0.432951] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov 22 17:31:33 philip-desktop kernel: [    0.432953] io scheduler noop registered
Nov 22 17:31:33 philip-desktop kernel: [    0.432955] io scheduler deadline registered
Nov 22 17:31:33 philip-desktop kernel: [    0.432984] io scheduler cfq registered (default)
Nov 22 17:31:33 philip-desktop kernel: [    0.433074] pcieport 0000:00:01.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.433092]   alloc irq_desc for 40 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433094]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433102] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.433147] pcieport 0000:00:1c.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.433172]   alloc irq_desc for 41 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433173]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433179] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.433240] pcieport 0000:00:1c.1: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.433265]   alloc irq_desc for 42 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433266]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433271] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.433332] pcieport 0000:00:1c.3: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.433359]   alloc irq_desc for 43 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433360]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433365] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.433427] pcieport 0000:00:1c.4: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.433452]   alloc irq_desc for 44 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433453]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.433459] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.433532] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 22 17:31:33 philip-desktop kernel: [    0.433610] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 22 17:31:33 philip-desktop kernel: [    0.433670] intel_idle: MWAIT substates: 0x22220
Nov 22 17:31:33 philip-desktop kernel: [    0.433672] intel_idle: does not run on family 6 model 23
Nov 22 17:31:33 philip-desktop kernel: [    0.433748] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Nov 22 17:31:33 philip-desktop kernel: [    0.433752] ACPI: Power Button [PWRB]
Nov 22 17:31:33 philip-desktop kernel: [    0.433792] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov 22 17:31:33 philip-desktop kernel: [    0.433794] ACPI: Power Button [PWRF]
Nov 22 17:31:33 philip-desktop kernel: [    0.433974] ACPI: acpi_idle registered with cpuidle
Nov 22 17:31:33 philip-desktop kernel: [    0.434051] Marking TSC unstable due to TSC halts in idle
Nov 22 17:31:33 philip-desktop kernel: [    0.435710] ERST: Table is not found!
Nov 22 17:31:33 philip-desktop kernel: [    0.435855] Linux agpgart interface v0.103
Nov 22 17:31:33 philip-desktop kernel: [    0.435873] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.436846] brd: module loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.437208] loop: module loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.437369] pata_acpi 0000:04:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.437394] pata_acpi 0000:04:00.1: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.437405] pata_acpi 0000:04:00.1: PCI INT B disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.437603] Fixed MDIO Bus: probed
Nov 22 17:31:33 philip-desktop kernel: [    0.437627] PPP generic driver version 2.4.2
Nov 22 17:31:33 philip-desktop kernel: [    0.437650] tun: Universal TUN/TAP device driver, 1.6
Nov 22 17:31:33 philip-desktop kernel: [    0.437651] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 22 17:31:33 philip-desktop kernel: [    0.437709] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 22 17:31:33 philip-desktop kernel: [    0.437723]   alloc irq_desc for 18 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.437724]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.437730] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 17:31:33 philip-desktop kernel: [    0.437744] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.437747] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.437770] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Nov 22 17:31:33 philip-desktop kernel: [    0.441670] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
Nov 22 17:31:33 philip-desktop kernel: [    0.441684] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
Nov 22 17:31:33 philip-desktop kernel: [    0.445719] Switching to clocksource hpet
Nov 22 17:31:33 philip-desktop kernel: [    0.471271] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Nov 22 17:31:33 philip-desktop kernel: [    0.471396] hub 1-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.471401] hub 1-0:1.0: 6 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.471474]   alloc irq_desc for 23 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.471475]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.471481] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 17:31:33 philip-desktop kernel: [    0.471504] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.471507] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.471541] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Nov 22 17:31:33 philip-desktop kernel: [    0.475425] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
Nov 22 17:31:33 philip-desktop kernel: [    0.475442] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
Nov 22 17:31:33 philip-desktop kernel: [    0.491266] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 22 17:31:33 philip-desktop kernel: [    0.491400] hub 2-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.491404] hub 2-0:1.0: 6 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.491470] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 22 17:31:33 philip-desktop kernel: [    0.491485] uhci_hcd: USB Universal Host Controller Interface driver
Nov 22 17:31:33 philip-desktop kernel: [    0.491548] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.491556] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.491559] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.491589] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Nov 22 17:31:33 philip-desktop kernel: [    0.491621] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
Nov 22 17:31:33 philip-desktop kernel: [    0.491707] hub 3-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.491710] hub 3-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.491754]   alloc irq_desc for 21 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.491755]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.491761] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov 22 17:31:33 philip-desktop kernel: [    0.491765] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.491767] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.491794] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Nov 22 17:31:33 philip-desktop kernel: [    0.491820] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
Nov 22 17:31:33 philip-desktop kernel: [    0.491902] hub 4-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.491905] hub 4-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.491949] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 17:31:33 philip-desktop kernel: [    0.491953] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.491955] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.491978] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Nov 22 17:31:33 philip-desktop kernel: [    0.491998] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
Nov 22 17:31:33 philip-desktop kernel: [    0.492077] hub 5-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492080] hub 5-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492126] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 17:31:33 philip-desktop kernel: [    0.492130] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.492133] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.492157] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Nov 22 17:31:33 philip-desktop kernel: [    0.492177] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
Nov 22 17:31:33 philip-desktop kernel: [    0.492264] hub 6-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492267] hub 6-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492311] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.492316] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.492318] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.492343] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Nov 22 17:31:33 philip-desktop kernel: [    0.492369] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
Nov 22 17:31:33 philip-desktop kernel: [    0.492451] hub 7-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492454] hub 7-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492497] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 17:31:33 philip-desktop kernel: [    0.492501] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.492504] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.492529] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Nov 22 17:31:33 philip-desktop kernel: [    0.492550] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
Nov 22 17:31:33 philip-desktop kernel: [    0.492634] hub 8-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492639] hub 8-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492726] PNP: No PS/2 controller found. Probing ports directly.
Nov 22 17:31:33 philip-desktop kernel: [    0.493083] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 22 17:31:33 philip-desktop kernel: [    0.493087] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 22 17:31:33 philip-desktop kernel: [    0.493167] mice: PS/2 mouse device common for all mice
Nov 22 17:31:33 philip-desktop kernel: [    0.493256] rtc_cmos 00:04: RTC can wake from S4
Nov 22 17:31:33 philip-desktop kernel: [    0.493289] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Nov 22 17:31:33 philip-desktop kernel: [    0.493310] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Nov 22 17:31:33 philip-desktop kernel: [    0.493381] device-mapper: uevent: version 1.0.3
Nov 22 17:31:33 philip-desktop kernel: [    0.493446] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Nov 22 17:31:33 philip-desktop kernel: [    0.493492] device-mapper: multipath: version 1.1.1 loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.493494] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.493628] cpuidle: using governor ladder
Nov 22 17:31:33 philip-desktop kernel: [    0.493664] cpuidle: using governor menu
Nov 22 17:31:33 philip-desktop kernel: [    0.493862] TCP cubic registered
Nov 22 17:31:33 philip-desktop kernel: [    0.493951] NET: Registered protocol family 10
Nov 22 17:31:33 philip-desktop kernel: [    0.494214] lo: Disabled Privacy Extensions
Nov 22 17:31:33 philip-desktop kernel: [    0.494355] NET: Registered protocol family 17
Nov 22 17:31:33 philip-desktop kernel: [    0.495242] PM: Resume from disk failed.
Nov 22 17:31:33 philip-desktop kernel: [    0.495252] registered taskstats version 1
Nov 22 17:31:33 philip-desktop kernel: [    0.495550]   Magic number: 2:340:509
Nov 22 17:31:33 philip-desktop kernel: [    0.495634] rtc_cmos 00:04: setting system clock to 2010-11-23 01:31:17 UTC (1290475877)
Nov 22 17:31:33 philip-desktop kernel: [    0.495636] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 22 17:31:33 philip-desktop kernel: [    0.495638] EDD information not available.
Nov 22 17:31:33 philip-desktop kernel: [    0.570735] Freeing initrd memory: 16580k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.576458] Freeing unused kernel memory: 908k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.576782] Write protecting the kernel read-only data: 10240k
Nov 22 17:31:33 philip-desktop kernel: [    0.576924] Freeing unused kernel memory: 416k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.577167] Freeing unused kernel memory: 1644k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.589515] udev[77]: starting version 163
Nov 22 17:31:33 philip-desktop kernel: [    0.649694] ahci 0000:00:1f.2: version 3.0
Nov 22 17:31:33 philip-desktop kernel: [    0.649710] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.649750]   alloc irq_desc for 45 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.649752]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.649760] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.649799] ahci: SSS flag set, parallel bus scan disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.649828] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Nov 22 17:31:33 philip-desktop kernel: [    0.649831] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems 
Nov 22 17:31:33 philip-desktop kernel: [    0.649835] ahci 0000:00:1f.2: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.661936] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.661958] r8169 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.662000] r8169 0000:05:00.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.662040]   alloc irq_desc for 46 on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.662042]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [    0.662056] r8169 0000:05:00.0: irq 46 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [    0.662411] r8169 0000:05:00.0: eth0: RTL8168c/8111c at 0xffffc90000674000, 00:24:1d:c6:93:ce, XID 1c4000c0 IRQ 46
Nov 22 17:31:33 philip-desktop kernel: [    0.672921] pata_jmicron 0000:04:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.672954] pata_jmicron 0000:04:00.1: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.678831] firewire_ohci 0000:06:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 17:31:33 philip-desktop kernel: [    0.680083] scsi0 : pata_jmicron
Nov 22 17:31:33 philip-desktop kernel: [    0.682789] scsi1 : pata_jmicron
Nov 22 17:31:33 philip-desktop kernel: [    0.683333] ata1: PATA max UDMA/100 cmd 0xbf00 ctl 0xbe00 bmdma 0xbb00 irq 16
Nov 22 17:31:33 philip-desktop kernel: [    0.683336] ata2: PATA max UDMA/100 cmd 0xbd00 ctl 0xbc00 bmdma 0xbb08 irq 16
Nov 22 17:31:33 philip-desktop kernel: [    0.740043] firewire_ohci: Added fw-ohci device 0000:06:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Nov 22 17:31:33 philip-desktop kernel: [    0.770069] scsi2 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770173] scsi3 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770236] scsi4 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770285] scsi5 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770335] scsi6 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770383] scsi7 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770501] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770503] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770505] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770508] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770510] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770512] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770547] ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.781286] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Nov 22 17:31:33 philip-desktop kernel: [    0.781292] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Nov 22 17:31:33 philip-desktop kernel: [    0.781299] ahci 0000:04:00.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [    0.781437] scsi8 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.781492] scsi9 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.781557] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 19
Nov 22 17:31:33 philip-desktop kernel: [    0.781561] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 19
Nov 22 17:31:33 philip-desktop kernel: [    0.791312] usb 1-1: new high speed USB device using ehci_hcd and address 2
Nov 22 17:31:33 philip-desktop kernel: [    1.110023] ata3: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.131300] ata9: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.231336] firewire_core: created device fw0: GUID 00cb62800000241d, S400
Nov 22 17:31:33 philip-desktop kernel: [    1.310027] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.347252] ata10.00: ATA-8: ST9250410AS, D005SDM1, max UDMA/133
Nov 22 17:31:33 philip-desktop kernel: [    1.347257] ata10.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 22 17:31:33 philip-desktop kernel: [    1.349163] ata10.00: configured for UDMA/133
Nov 22 17:31:33 philip-desktop kernel: [    1.460016] usb 4-1: new full speed USB device using uhci_hcd and address 2
Nov 22 17:31:33 philip-desktop kernel: [    1.480020] ata4: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.861268] ata5: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.921258] usb 6-2: new full speed USB device using uhci_hcd and address 2
Nov 22 17:31:33 philip-desktop kernel: [    2.112249] hub 6-2:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    2.114211] hub 6-2:1.0: 3 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    2.231268] ata6: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    2.391211] usb 6-2.2: new full speed USB device using uhci_hcd and address 3
Nov 22 17:31:33 philip-desktop kernel: [    2.641211] usb 6-2.3: new full speed USB device using uhci_hcd and address 4
Nov 22 17:31:33 philip-desktop kernel: [    2.781259] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    2.782844] ata7.00: ATAPI: ATAPI   iHAS324   Y, BL1W, max UDMA/100
Nov 22 17:31:33 philip-desktop kernel: [    2.785078] ata7.00: configured for UDMA/100
Nov 22 17:31:33 philip-desktop kernel: [    2.802846] scsi 6:0:0:0: CD-ROM            ATAPI    iHAS324   Y      BL1W PQ: 0 ANSI: 5
Nov 22 17:31:33 philip-desktop kernel: [    2.805016] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 22 17:31:33 philip-desktop kernel: [    2.805019] Uniform CD-ROM driver Revision: 3.20
Nov 22 17:31:33 philip-desktop kernel: [    2.805096] sr 6:0:0:0: Attached scsi CD-ROM sr0
Nov 22 17:31:33 philip-desktop kernel: [    2.805138] sr 6:0:0:0: Attached scsi generic sg0 type 5
Nov 22 17:31:33 philip-desktop kernel: [    2.808057] usbcore: registered new interface driver hiddev
Nov 22 17:31:33 philip-desktop kernel: [    2.813478] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.2/6-2.2:1.0/input/input2
Nov 22 17:31:33 philip-desktop kernel: [    2.813538] generic-usb 0003:046D:C71B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-2.2/input0
Nov 22 17:31:33 philip-desktop kernel: [    2.822803] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.3/6-2.3:1.0/input/input3
Nov 22 17:31:33 philip-desktop kernel: [    2.822932] generic-usb 0003:046D:C71C.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-2.3/input0
Nov 22 17:31:33 philip-desktop kernel: [    2.822944] usbcore: registered new interface driver usbhid
Nov 22 17:31:33 philip-desktop kernel: [    2.822945] usbhid: USB HID core driver
Nov 22 17:31:33 philip-desktop kernel: [    3.150021] ata8: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    3.170139] scsi 9:0:0:0: Direct-Access     ATA      ST9250410AS      D005 PQ: 0 ANSI: 5
Nov 22 17:31:33 philip-desktop kernel: [    3.170255] sd 9:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Nov 22 17:31:33 philip-desktop kernel: [    3.170258] sd 9:0:0:0: Attached scsi generic sg1 type 0
Nov 22 17:31:33 philip-desktop kernel: [    3.170299] sd 9:0:0:0: [sda] Write Protect is off
Nov 22 17:31:33 philip-desktop kernel: [    3.170301] sd 9:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 22 17:31:33 philip-desktop kernel: [    3.170319] sd 9:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 17:31:33 philip-desktop kernel: [    3.170435]  sda: sda1 sda2 < sda5 >
Nov 22 17:31:33 philip-desktop kernel: [    3.246142] sd 9:0:0:0: [sda] Attached SCSI disk
Nov 22 17:31:33 philip-desktop kernel: [    3.628276] Btrfs loaded
Nov 22 17:31:33 philip-desktop kernel: [    3.631578] xor: automatically using best checksumming function: generic_sse
Nov 22 17:31:33 philip-desktop kernel: [    3.680004]    generic_sse: 10703.600 MB/sec
Nov 22 17:31:33 philip-desktop kernel: [    3.680006] xor: using function: generic_sse (10703.600 MB/sec)
Nov 22 17:31:33 philip-desktop kernel: [    3.681764] device-mapper: dm-raid45: initialized v0.2594b
Nov 22 17:31:33 philip-desktop kernel: [    3.919137] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Nov 22 17:31:33 philip-desktop kernel: [    3.919141] EXT4-fs (sda1): write access will be enabled during recovery
Nov 22 17:31:33 philip-desktop kernel: [    6.382350] EXT4-fs (sda1): orphan cleanup on readonly fs
Nov 22 17:31:33 philip-desktop kernel: [    6.382357] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5242988
Nov 22 17:31:33 philip-desktop kernel: [    6.382401] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5242992
Nov 22 17:31:33 philip-desktop kernel: [    6.382415] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5242989
Nov 22 17:31:33 philip-desktop kernel: [    6.382430] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1852069
Nov 22 17:31:33 philip-desktop kernel: [    6.382452] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1835198
Nov 22 17:31:33 philip-desktop kernel: [    6.382464] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1851232
Nov 22 17:31:33 philip-desktop kernel: [    6.382477] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1852038
Nov 22 17:31:33 philip-desktop kernel: [    6.382488] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1852078
Nov 22 17:31:33 philip-desktop kernel: [    6.382506] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1852070
Nov 22 17:31:33 philip-desktop kernel: [    6.382518] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5242968
Nov 22 17:31:33 philip-desktop kernel: [    6.382528] EXT4-fs (sda1): 10 orphan inodes deleted
Nov 22 17:31:33 philip-desktop kernel: [    6.382531] EXT4-fs (sda1): recovery complete
Nov 22 17:31:33 philip-desktop kernel: [    6.938574] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Nov 22 17:31:33 philip-desktop kernel: [   15.540462] udev[460]: starting version 163
Nov 22 17:31:33 philip-desktop kernel: [   15.629527] Adding 9936892k swap on /dev/sda5.  Priority:-1 extents:1 across:9936892k 
Nov 22 17:31:33 philip-desktop kernel: [   15.676743] lp: driver loaded but no devices found
Nov 22 17:31:33 philip-desktop kernel: [   15.779102] cfg80211: Calling CRDA to update world regulatory domain
Nov 22 17:31:33 philip-desktop kernel: [   15.779350] Linux video capture interface: v2.00
Nov 22 17:31:33 philip-desktop kernel: [   15.815638] nvidia: module license 'NVIDIA' taints kernel.
Nov 22 17:31:33 philip-desktop kernel: [   15.815641] Disabling lock debugging due to kernel taint
Nov 22 17:31:33 philip-desktop kernel: [   15.911216] cfg80211: World regulatory domain updated:
Nov 22 17:31:33 philip-desktop kernel: [   15.911218]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 22 17:31:33 philip-desktop kernel: [   15.911220]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911222]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911224]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911226]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911228]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911405] IR NEC protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   15.959345]   alloc irq_desc for 22 on node -1
Nov 22 17:31:33 philip-desktop kernel: [   15.959348]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [   15.959354] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 22 17:31:33 philip-desktop kernel: [   15.959400]   alloc irq_desc for 47 on node -1
Nov 22 17:31:33 philip-desktop kernel: [   15.959401]   alloc kstat_irqs on node -1
Nov 22 17:31:33 philip-desktop kernel: [   15.959408] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Nov 22 17:31:33 philip-desktop kernel: [   15.959430] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [   15.960919] cx23885 driver version 0.0.2 loaded
Nov 22 17:31:33 philip-desktop kernel: [   15.960948] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 22 17:31:33 philip-desktop kernel: [   15.961299] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
Nov 22 17:31:33 philip-desktop kernel: [   16.238935] IR RC5(x) protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.240350] IR RC6 protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.242281] IR JVC protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.243677] IR Sony protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.246034] lirc_dev: IR Remote Control driver registered, major 249 
Nov 22 17:31:33 philip-desktop kernel: [   16.247073] IR LIRC bridge handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.350753] tveeprom 0-0050: Hauppauge model 78521, rev C1E9, serial# 2954264
Nov 22 17:31:33 philip-desktop kernel: [   16.350756] tveeprom 0-0050: MAC address is 00:0d:fe:2d:14:18
Nov 22 17:31:33 philip-desktop kernel: [   16.350758] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
Nov 22 17:31:33 philip-desktop kernel: [   16.350761] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Nov 22 17:31:33 philip-desktop kernel: [   16.350763] tveeprom 0-0050: audio processor is CX23887 (idx 42)
Nov 22 17:31:33 philip-desktop kernel: [   16.350765] tveeprom 0-0050: decoder processor is CX23887 (idx 37)
Nov 22 17:31:33 philip-desktop kernel: [   16.350766] tveeprom 0-0050: has radio
Nov 22 17:31:33 philip-desktop kernel: [   16.350768] cx23885[0]: hauppauge eeprom: model=78521
Nov 22 17:31:33 philip-desktop kernel: [   16.354169] cx25840 2-0044: cx23887 A/V decoder found @ 0x88 (cx23885[0])
Nov 22 17:31:33 philip-desktop kernel: [   16.364936] Registered IR keymap rc-rc6-mce
Nov 22 17:31:33 philip-desktop kernel: [   16.365000] input: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/virtual/rc/rc0/input4
Nov 22 17:31:33 philip-desktop kernel: [   16.365042] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/virtual/rc/rc0
Nov 22 17:31:33 philip-desktop kernel: [   16.365066] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
Nov 22 17:31:33 philip-desktop kernel: [   16.365081] mceusb 4-1:1.0: Registered SMK eHome Infrared Transceiver on usb4:2
Nov 22 17:31:33 philip-desktop kernel: [   16.365111] usbcore: registered new interface driver mceusb
Nov 22 17:31:33 philip-desktop kernel: [   16.498618] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [   16.498625] nvidia 0000:01:00.0: setting latency timer to 64
Nov 22 17:31:33 philip-desktop kernel: [   16.498629] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Nov 22 17:31:33 philip-desktop kernel: [   16.498796] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.21  Thu Nov  4 21:16:27 PDT 2010
Nov 22 17:31:33 philip-desktop kernel: [   16.612565] phy0: Selected rate control algorithm 'minstrel'
Nov 22 17:31:33 philip-desktop kernel: [   16.612953] phy0: hwaddr 00:22:3f:5c:ad:4f, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
Nov 22 17:31:33 philip-desktop kernel: [   16.623983] rtl8187: Customer ID is 0xFF
Nov 22 17:31:33 philip-desktop kernel: [   16.624405] Registered led device: rtl8187-phy0::radio
Nov 22 17:31:33 philip-desktop kernel: [   16.624422] Registered led device: rtl8187-phy0::tx
Nov 22 17:31:33 philip-desktop kernel: [   16.624435] Registered led device: rtl8187-phy0::rx
Nov 22 17:31:33 philip-desktop kernel: [   16.625475] rtl8187: wireless switch is on
Nov 22 17:31:33 philip-desktop kernel: [   16.625538] usbcore: registered new interface driver rtl8187
Nov 22 17:31:33 philip-desktop kernel: [   16.865595] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Nov 22 17:31:33 philip-desktop avahi-daemon[1020]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Nov 22 17:31:33 philip-desktop avahi-daemon[1020]: Successfully dropped root privileges.
Nov 22 17:31:33 philip-desktop avahi-daemon[1020]: avahi-daemon 0.6.27 starting up.
Nov 22 17:31:33 philip-desktop avahi-daemon[1020]: Successfully called chroot().
Nov 22 17:31:33 philip-desktop avahi-daemon[1020]: Successfully dropped remaining capabilities.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> NetworkManager (version 0.8.1) is starting...
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> trying to start the modem manager...
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: init!
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: update_system_hostname
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPluginIfupdown: management mode: unmanaged
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:05:00.0/net/eth0, iface: eth0)
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: end _init.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    Ifupdown: get unmanaged devices count: 0
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: (31661520) ... get_connections.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: (31661520) ... get_connections (managed=false): return empty list.
Nov 22 17:31:33 philip-desktop modem-manager: ModemManager (version 0.4) starting...
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Longcheer
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Gobi
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Sierra
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Huawei
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Option
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin AnyData
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin SimTech
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Ericsson MBM
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Option High-Speed
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin ZTE
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin MotoC
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Nokia
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Novatel
Nov 22 17:31:33 philip-desktop modem-manager: Loaded plugin Generic
Nov 22 17:31:33 philip-desktop modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Nov 22 17:31:33 philip-desktop modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Nov 22 17:31:33 philip-desktop modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Nov 22 17:31:33 philip-desktop modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Nov 22 17:31:33 philip-desktop NetworkManager[1018]:    Ifupdown: get unmanaged devices count: 0
Nov 22 17:31:33 philip-desktop avahi-daemon[1020]: No service file found in /etc/avahi/services.
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> Networking is enabled by state file
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8187' ifindex: 3)
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> (wlan0): now managed
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Nov 22 17:31:33 philip-desktop NetworkManager[1018]: <info> (wlan0): bringing up device.
Nov 22 17:31:34 philip-desktop kernel: [   17.169916] cx25840 2-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
Nov 22 17:31:34 philip-desktop kernel: [   17.181390] tuner 1-0042: chip found @ 0x84 (cx23885[0])
Nov 22 17:31:34 philip-desktop kernel: [   17.232154] tda829x 1-0042: could not clearly identify tuner address, defaulting to 60
Nov 22 17:31:34 philip-desktop kernel: [   17.261636] tda18271 1-0060: creating new instance
Nov 22 17:31:34 philip-desktop kernel: [   17.310378] TDA18271HD/C1 detected @ 1-0060
Nov 22 17:31:34 philip-desktop init: apport pre-start process (1220) terminated with status 1
Nov 22 17:31:34 philip-desktop cron[1227]: (CRON) INFO (pidfile fd = 3)
Nov 22 17:31:34 philip-desktop acpid: starting up with proc fs
Nov 22 17:31:34 philip-desktop init: apport post-stop process (1235) terminated with status 1
Nov 22 17:31:34 philip-desktop acpid: 36 rules loaded
Nov 22 17:31:34 philip-desktop acpid: waiting for events: event logging is off
Nov 22 17:31:34 philip-desktop anacron[1285]: Anacron 2.3 started on 2010-11-22
Nov 22 17:31:34 philip-desktop cron[1301]: (CRON) STARTUP (fork ok)
Nov 22 17:31:34 philip-desktop cron[1301]: (CRON) INFO (Running @reboot jobs)
Nov 22 17:31:34 philip-desktop anacron[1285]: Will run job `cron.daily' in 5 min.
Nov 22 17:31:34 philip-desktop anacron[1285]: Jobs will be executed sequentially
Nov 22 17:31:34 philip-desktop kernel: [   17.841452] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Nov 22 17:31:34 philip-desktop kernel: [   17.841455] vboxdrv: Successfully done.
Nov 22 17:31:34 philip-desktop kernel: [   17.841456] vboxdrv: Found 2 processor cores.
Nov 22 17:31:34 philip-desktop kernel: [   17.841538] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e73d60
Nov 22 17:31:34 philip-desktop kernel: [   17.841552] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x7d5
Nov 22 17:31:34 philip-desktop kernel: [   17.841587] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Nov 22 17:31:34 philip-desktop kernel: [   17.841588] vboxdrv: Successfully loaded version 3.2.10 (interface 0x00140001).
Nov 22 17:31:36 philip-desktop avahi-daemon[1020]: Network interface enumeration completed.
Nov 22 17:31:36 philip-desktop avahi-daemon[1020]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 22 17:31:36 philip-desktop avahi-daemon[1020]: Server startup complete. Host name is philip-desktop.local. Local service cookie is 1022828554.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (wlan0): preparing device.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (wlan0): deactivating device (reason: 2).
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): carrier is OFF
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): now managed
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): bringing up device.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): preparing device.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): deactivating device (reason: 2).
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.4/0000:05:00.0/net/eth0
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): carrier now ON (device state 2)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> modem-manager is now available
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Trying to start the supplicant...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) starting connection 'Auto eth0'
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 22 17:31:36 philip-desktop modem-manager: (net/vboxnet0): could not get port's parent device
Nov 22 17:31:36 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Nov 22 17:31:36 philip-desktop kernel: [   19.222453] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 22 17:31:36 philip-desktop kernel: [   19.224497] r8169 0000:05:00.0: eth0: link up
Nov 22 17:31:36 philip-desktop kernel: [   19.224502] r8169 0000:05:00.0: eth0: link up
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> dhclient started with pid 1562
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (wlan0): supplicant manager state:  down -> idle
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Nov 22 17:31:36 philip-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Nov 22 17:31:36 philip-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Nov 22 17:31:36 philip-desktop dhclient: All rights reserved.
Nov 22 17:31:36 philip-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Nov 22 17:31:36 philip-desktop dhclient: 
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov 22 17:31:36 philip-desktop dhclient: Listening on LPF/eth0/00:24:1d:c6:93:ce
Nov 22 17:31:36 philip-desktop dhclient: Sending on   LPF/eth0/00:24:1d:c6:93:ce
Nov 22 17:31:36 philip-desktop dhclient: Sending on   Socket/fallback
Nov 22 17:31:36 philip-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (wlan0): supplicant interface state:  starting -> ready
Nov 22 17:31:36 philip-desktop dhclient: DHCPOFFER of 192.168.1.6 from 192.168.1.1
Nov 22 17:31:36 philip-desktop dhclient: DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
Nov 22 17:31:36 philip-desktop dhclient: DHCPACK of 192.168.1.6 from 192.168.1.1
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> (eth0): DHCPv4 state changed preinit -> bound
Nov 22 17:31:36 philip-desktop dhclient: bound to 192.168.1.6 -- renewal in 38697 seconds.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info>   address 192.168.1.6
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info>   prefix 24 (255.255.255.0)
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info>   gateway 192.168.1.1
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info>   nameserver '192.168.1.1'
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 22 17:31:36 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov 22 17:31:36 philip-desktop avahi-daemon[1020]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.6.
Nov 22 17:31:36 philip-desktop avahi-daemon[1020]: New relevant interface eth0.IPv4 for mDNS.
Nov 22 17:31:36 philip-desktop avahi-daemon[1020]: Registering new address record for 192.168.1.6 on eth0.IPv4.
Nov 22 17:31:37 philip-desktop kernel: [   20.006837] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 22 17:31:37 philip-desktop kernel: [   20.400356] tda829x 1-0042: type set to tda8295+18271
Nov 22 17:31:37 philip-desktop NetworkManager[1018]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Nov 22 17:31:37 philip-desktop NetworkManager[1018]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Nov 22 17:31:37 philip-desktop NetworkManager[1018]: <info> Activation (eth0) successful, device activated.
Nov 22 17:31:37 philip-desktop NetworkManager[1018]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 22 17:31:38 philip-desktop avahi-daemon[1020]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:1dff:fec6:93ce.
Nov 22 17:31:38 philip-desktop avahi-daemon[1020]: New relevant interface eth0.IPv6 for mDNS.
Nov 22 17:31:38 philip-desktop avahi-daemon[1020]: Registering new address record for fe80::224:1dff:fec6:93ce on eth0.*.
Nov 22 17:31:39 philip-desktop ntpdate[1772]: step time server 91.189.94.4 offset 0.607506 sec
Nov 22 17:31:39 philip-desktop kernel: [   22.020429] cx23885[0]/0: registered device video0 [v4l2]
Nov 22 17:31:41 philip-desktop kernel: [   23.494343] cx23885[0]: registered device video1 [mpeg]
Nov 22 17:31:41 philip-desktop kernel: [   23.494346] cx23885_dvb_register() allocating 1 frontend(s)
Nov 22 17:31:41 philip-desktop kernel: [   23.494348] cx23885[0]: cx23885 based dvb card
Nov 22 17:31:41 philip-desktop kernel: [   23.525357] MT2131: successfully identified at address 0x61
Nov 22 17:31:41 philip-desktop kernel: [   23.526988] DVB: registering new adapter (cx23885[0])
Nov 22 17:31:41 philip-desktop kernel: [   23.526991] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Nov 22 17:31:41 philip-desktop kernel: [   23.527219] cx23885_dev_checkrevision() Hardware revision = 0xb1
Nov 22 17:31:41 philip-desktop kernel: [   23.527226] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xfd800000
Nov 22 17:31:41 philip-desktop kernel: [   23.527232] cx23885 0000:03:00.0: setting latency timer to 64
Nov 22 17:31:41 philip-desktop kernel: [   23.527294]   alloc irq_desc for 48 on node -1
Nov 22 17:31:41 philip-desktop kernel: [   23.527296]   alloc kstat_irqs on node -1
Nov 22 17:31:41 philip-desktop kernel: [   23.527311] cx23885 0000:03:00.0: irq 48 for MSI/MSI-X
Nov 22 17:31:41 philip-desktop gdm-binary[1810]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 22 17:31:41 philip-desktop gdm-simple-slave[1884]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 22 17:31:41 philip-desktop kernel: [   23.596979] ppdev: user-space parallel port driver
Nov 22 17:31:41 philip-desktop gdm-binary[1810]: WARNING: Unable to find users: no seat-id found
Nov 22 17:31:41 philip-desktop acpid: client connected from 1901[0:0]
Nov 22 17:31:41 philip-desktop acpid: 1 client rule loaded
Nov 22 17:31:42 philip-desktop acpid: client connected from 1901[0:0]
Nov 22 17:31:42 philip-desktop acpid: 1 client rule loaded
Nov 22 17:31:42 philip-desktop gdm-session-worker[1949]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Successfully called chroot.
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Successfully dropped privileges.
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Successfully limited resources.
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Running.
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Watchdog thread running.
Nov 22 17:31:42 philip-desktop polkitd[1968]: started daemon version 0.96 using authority implementation `local' version `0.96'
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Canary thread running.
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Successfully made thread 1956 of process 1956 (n/a) owned by '113' high priority at nice level -11.
Nov 22 17:31:42 philip-desktop rtkit-daemon[1961]: Supervising 1 threads of 1 processes of 1 users.
Nov 22 17:31:44 philip-desktop kernel: [   26.624603] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 22 17:31:44 philip-desktop gdm-simple-greeter[1948]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Nov 22 17:31:44 philip-desktop rtkit-daemon[1961]: Successfully made thread 2043 of process 1956 (n/a) owned by '113' RT at priority 5.
Nov 22 17:31:44 philip-desktop rtkit-daemon[1961]: Supervising 2 threads of 1 processes of 1 users.
Nov 22 17:31:44 philip-desktop rtkit-daemon[1961]: Successfully made thread 2044 of process 1956 (n/a) owned by '113' RT at priority 5.
Nov 22 17:31:44 philip-desktop rtkit-daemon[1961]: Supervising 3 threads of 1 processes of 1 users.
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 56.
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: snd_pcm_dump():
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: Soft volume PCM
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: Control: PCM Playback Volume
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: min_dB: -51
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: max_dB: 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: resolution: 256
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: Its setup is:
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   stream       : CAPTURE
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   format       : S16_LE
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   subformat    : STD
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   channels     : 2
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   rate         : 44100
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   msbits       : 16
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   buffer_size  : 88192
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_size  : 44096
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_time  : 999909
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_step  : 1
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   avail_min    : 87310
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_event : 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   start_threshold  : -1
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   stop_threshold   : 6205960286516543488
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   silence_threshold: 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   silence_size : 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   boundary     : 6205960286516543488
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c: Its setup is:
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   stream       : CAPTURE
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   format       : S16_LE
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   subformat    : STD
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   channels     : 2
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   rate         : 44100
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   msbits       : 16
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   buffer_size  : 88192
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_size  : 44096
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_time  : 999909
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_step  : 1
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   avail_min    : 87310
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   period_event : 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   start_threshold  : -1
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   stop_threshold   : 6205960286516543488
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   silence_threshold: 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   silence_size : 0
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   boundary     : 6205960286516543488
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   appl_ptr     : 87360
Nov 22 17:31:46 philip-desktop pulseaudio[1956]: alsa-util.c:   hw_ptr       : 87360
Nov 22 17:31:47 philip-desktop kernel: [   30.021264] eth0: no IPv6 routers present
Nov 22 17:36:35 philip-desktop anacron[1285]: Job `cron.daily' started
Nov 22 17:36:35 philip-desktop anacron[2068]: Updated timestamp for job `cron.daily' to 2010-11-22
Nov 22 17:39:01 philip-desktop CRON[2109]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

---

### Post by Philip550c on 2010-11-23
MESSAGES.1

```
Nov 22 17:31:33 philip-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 22 17:31:33 philip-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="996" x-info="http://www.rsyslog.com"] (re)start
Nov 22 17:31:33 philip-desktop rsyslogd: rsyslogd's groupid changed to 103
Nov 22 17:31:33 philip-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=80e1f0c8-97bc-46fd-82ab-15337f8c59c1 ro quiet splash
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee2000 (ACPI NVS)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfee2000 - 00000000dfef0000 (ACPI data)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] DMI 2.4 present.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] No AGP bridge found
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] last_pfn = 0xdfee0 max_arch_pfn = 0x400000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] modified physical RAM map:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfee0000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000dfee0000 - 00000000dfee2000 (ACPI NVS)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000dfee2000 - 00000000dfef0000 (ACPI data)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dff00000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000f4000000 - 00000000f8000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f5670] f5670
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dfee0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] RAMDISK: 36fbf000 - 37ff0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f7070 00014 (v00 GBT   )
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: RSDT 00000000dfee2040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: FACP 00000000dfee20c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: DSDT 00000000dfee2180 04C5A (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: FACS 00000000dfee0000 00040
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: HPET 00000000dfee6f40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: MCFG 00000000dfee6fc0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: EUDS 00000000dfee7000 00560 (v01 GBT             00000000      00000000)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: TAMG 00000000dfee7560 06852 (v01 GBT    GBT   B0 5455312E BG?? 00020101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: APIC 00000000dfee6e40 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: SSDT 00000000dfeee420 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] No NUMA configuration found
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000120000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00120000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000dfee0
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfee0000 - 00000000dfee2000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfee2000 - 00000000dfef0000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfef0000 - 00000000dff00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000f4000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Allocating PCI resources starting at dff00000 (gap: dff00000:14100000)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1032045
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Policy zone: Normal
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=80e1f0c8-97bc-46fd-82ab-15337f8c59c1 ro quiet splash
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Checking aperture...
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] No AGP bridge found
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Subtract (57 early reservations)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #2 [0036fbf000 - 0037ff0000]         RAMDISK
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #3 [0001d18000 - 0001d180f6]             BRK
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #4 [00000f5680 - 0000100000]   BIOS reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #5 [00000f5670 - 00000f5680]    MP-table mpf
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #6 [000009dc00 - 00000f0d00]   BIOS reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #7 [00000f0eb4 - 00000f5670]   BIOS reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #8 [00000f0d00 - 00000f0eb4]    MP-table mpc
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #12 [000001a000 - 000001b000]         PGTABLE
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #14 [0001d18100 - 0001d19100]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #18 [0100200000 - 0103c00000]        MEMMAP 0
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #20 [0001d19100 - 0001d31100]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #21 [0001d31100 - 0001d34100]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #22 [0001d35000 - 0001d36000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #25 [0001d176c0 - 0001d17928]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #26 [0001d17940 - 0001d179a8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #27 [0001d179c0 - 0001d17a28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #28 [0001d17a40 - 0001d17aa8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #29 [0001d17ac0 - 0001d17b28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #30 [0001d17b40 - 0001d17ba8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #31 [0001d17bc0 - 0001d17c28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #32 [0001d17c40 - 0001d17ca8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #33 [0001d17cc0 - 0001d17d28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #34 [0001d17d40 - 0001d17da8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #35 [0001d17dc0 - 0001d17e28]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #36 [0001d17e40 - 0001d17e60]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #37 [0001d17e80 - 0001d17ea0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #38 [0001d17ec0 - 0001d17f2a]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #39 [0001d17f40 - 0001d17faa]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #40 [0001e00000 - 0001e1e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #42 [0001f00000 - 0001f1e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #43 [0001f80000 - 0001f9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #44 [0001d17fc0 - 0001d17fc8]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #45 [0001d34100 - 0001d34108]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #46 [0001d34140 - 0001d34150]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #47 [0001d34180 - 0001d341a0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #48 [0001d341c0 - 0001d342f0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #49 [0001d34300 - 0001d34350]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #50 [0001d34380 - 0001d343d0]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #51 [0001d36000 - 0001d3e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #52 [0001d34400 - 0001d34640]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #53 [0001f9e000 - 0005f9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #54 [0001d3e000 - 0001d5e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #55 [0001d5e000 - 0001d9e000]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000]   #56 [000001b800 - 0000023800]         BOOTMEM
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Memory: 4036652k/4718592k available (5708k kernel code, 525900k absent, 156040k reserved, 5382k data, 908k init)
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:712
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] console [tty0] enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Nov 22 17:31:33 philip-desktop kernel: [    0.000000] Detected 2800.579 MHz processor.
Nov 22 17:31:33 philip-desktop kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5601.15 BogoMIPS (lpj=28005790)
Nov 22 17:31:33 philip-desktop kernel: [    0.010011] pid_max: default: 32768 minimum: 301
Nov 22 17:31:33 philip-desktop kernel: [    0.010030] Security Framework initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.010046] AppArmor: AppArmor initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.010047] Yama: becoming mindful.
Nov 22 17:31:33 philip-desktop kernel: [    0.010385] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.012021] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.012796] Mount-cache hash table entries: 256
Nov 22 17:31:33 philip-desktop kernel: [    0.012917] Initializing cgroup subsys ns
Nov 22 17:31:33 philip-desktop kernel: [    0.012922] Initializing cgroup subsys cpuacct
Nov 22 17:31:33 philip-desktop kernel: [    0.012925] Initializing cgroup subsys memory
Nov 22 17:31:33 philip-desktop kernel: [    0.012932] Initializing cgroup subsys devices
Nov 22 17:31:33 philip-desktop kernel: [    0.012934] Initializing cgroup subsys freezer
Nov 22 17:31:33 philip-desktop kernel: [    0.012936] Initializing cgroup subsys net_cls
Nov 22 17:31:33 philip-desktop kernel: [    0.012960] CPU: Physical Processor ID: 0
Nov 22 17:31:33 philip-desktop kernel: [    0.012961] CPU: Processor Core ID: 0
Nov 22 17:31:33 philip-desktop kernel: [    0.012963] mce: CPU supports 6 MCE banks
Nov 22 17:31:33 philip-desktop kernel: [    0.012969] CPU0: Thermal monitoring enabled (TM2)
Nov 22 17:31:33 philip-desktop kernel: [    0.012973] using mwait in idle threads.
Nov 22 17:31:33 philip-desktop kernel: [    0.012974] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Nov 22 17:31:33 philip-desktop kernel: [    0.012981] ... version:                2
Nov 22 17:31:33 philip-desktop kernel: [    0.012982] ... bit width:              40
Nov 22 17:31:33 philip-desktop kernel: [    0.012983] ... generic registers:      2
Nov 22 17:31:33 philip-desktop kernel: [    0.012984] ... value mask:             000000ffffffffff
Nov 22 17:31:33 philip-desktop kernel: [    0.012986] ... max period:             000000007fffffff
Nov 22 17:31:33 philip-desktop kernel: [    0.012987] ... fixed-purpose events:   3
Nov 22 17:31:33 philip-desktop kernel: [    0.012988] ... event mask:             0000000700000003
Nov 22 17:31:33 philip-desktop kernel: [    0.015078] ACPI: Core revision 20100428
Nov 22 17:31:33 philip-desktop kernel: [    0.019796] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov 22 17:31:33 philip-desktop kernel: [    0.019801] ftrace: allocating 22680 entries in 89 pages
Nov 22 17:31:33 philip-desktop kernel: [    0.028257] Setting APIC routing to flat
Nov 22 17:31:33 philip-desktop kernel: [    0.028564] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 22 17:31:33 philip-desktop kernel: [    0.128599] CPU0: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz stepping 0a
Nov 22 17:31:33 philip-desktop kernel: [    0.130000] Booting Node   0, Processors  #1
Nov 22 17:31:33 philip-desktop kernel: [    0.290014] Brought up 2 CPUs
Nov 22 17:31:33 philip-desktop kernel: [    0.290016] Total of 2 processors activated (11201.31 BogoMIPS).
Nov 22 17:31:33 philip-desktop kernel: [    0.290561] devtmpfs: initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.290561] regulator: core version 0.5
Nov 22 17:31:33 philip-desktop kernel: [    0.290574] Time:  1:31:17  Date: 11/23/10
Nov 22 17:31:33 philip-desktop kernel: [    0.290604] NET: Registered protocol family 16
Nov 22 17:31:33 philip-desktop kernel: [    0.290621] Trying to unpack rootfs image as initramfs...
Nov 22 17:31:33 philip-desktop kernel: [    0.290704] ACPI: bus type pci registered
Nov 22 17:31:33 philip-desktop kernel: [    0.290759] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
Nov 22 17:31:33 philip-desktop kernel: [    0.290761] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
Nov 22 17:31:33 philip-desktop kernel: [    0.298954] PCI: Using configuration type 1 for base access
Nov 22 17:31:33 philip-desktop kernel: [    0.310067] bio: create slab <bio-0> at 0
Nov 22 17:31:33 philip-desktop kernel: [    0.317109] ACPI Warning: Incorrect checksum in table [TAMG] - 0x41, should be 0x40 (20100428/tbutils-314)
Nov 22 17:31:33 philip-desktop kernel: [    0.317115] ACPI: SSDT 00000000dfeede00 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317299] ACPI: Dynamic OEM Table Load:
Nov 22 17:31:33 philip-desktop kernel: [    0.317302] ACPI: SSDT (null) 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317466] ACPI: SSDT 00000000dfeee2c0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317644] ACPI: Dynamic OEM Table Load:
Nov 22 17:31:33 philip-desktop kernel: [    0.317646] ACPI: SSDT (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Nov 22 17:31:33 philip-desktop kernel: [    0.317693] ACPI: Interpreter enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.317695] ACPI: (supports S0 S3 S4 S5)
Nov 22 17:31:33 philip-desktop kernel: [    0.317710] ACPI: Using IOAPIC for interrupt routing
Nov 22 17:31:33 philip-desktop kernel: [    0.321702] ACPI: No dock devices found.
Nov 22 17:31:33 philip-desktop kernel: [    0.321705] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 22 17:31:33 philip-desktop kernel: [    0.321788] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
Nov 22 17:31:33 philip-desktop kernel: [    0.321945] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Nov 22 17:31:33 philip-desktop kernel: [    0.321947] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.321949] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.321951] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.321953] pci_root PNP0A03:00: host bridge window [mem 0xdff00000-0xfebfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.322906] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
Nov 22 17:31:33 philip-desktop kernel: [    0.322909] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
Nov 22 17:31:33 philip-desktop kernel: [    0.322912] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
Nov 22 17:31:33 philip-desktop kernel: [    0.322915] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
Nov 22 17:31:33 philip-desktop kernel: [    0.323166] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov 22 17:31:33 philip-desktop kernel: [    0.323210] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Nov 22 17:31:33 philip-desktop kernel: [    0.323391] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 22 17:31:33 philip-desktop kernel: [    0.323400] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Nov 22 17:31:33 philip-desktop kernel: [    0.323682] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 22 17:31:33 philip-desktop kernel: [    0.323694] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
Nov 22 17:31:33 philip-desktop kernel: [    0.340021] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
Nov 22 17:31:33 philip-desktop kernel: [    0.340246] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
Nov 22 17:31:33 philip-desktop kernel: [    0.353080] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353155] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353229] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353302] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353375] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 22 17:31:33 philip-desktop kernel: [    0.353448] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353521] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353595] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Nov 22 17:31:33 philip-desktop kernel: [    0.353630] HEST: Table is not found!
Nov 22 17:31:33 philip-desktop kernel: [    0.353705] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Nov 22 17:31:33 philip-desktop kernel: [    0.353710] vgaarb: loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.353827] SCSI subsystem initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.353935] usbcore: registered new interface driver usbfs
Nov 22 17:31:33 philip-desktop kernel: [    0.353943] usbcore: registered new interface driver hub
Nov 22 17:31:33 philip-desktop kernel: [    0.353960] usbcore: registered new device driver usb
Nov 22 17:31:33 philip-desktop kernel: [    0.354056] ACPI: WMI: Mapper loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.354057] PCI: Using ACPI for IRQ routing
Nov 22 17:31:33 philip-desktop kernel: [    0.354228] NetLabel: Initializing
Nov 22 17:31:33 philip-desktop kernel: [    0.354229] NetLabel:  domain hash size = 128
Nov 22 17:31:33 philip-desktop kernel: [    0.354230] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 22 17:31:33 philip-desktop kernel: [    0.354240] NetLabel:  unlabeled traffic allowed by default
Nov 22 17:31:33 philip-desktop kernel: [    0.354263] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Nov 22 17:31:33 philip-desktop kernel: [    0.354267] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 22 17:31:33 philip-desktop kernel: [    0.354271] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Nov 22 17:31:33 philip-desktop kernel: [    0.360023] Switching to clocksource tsc
Nov 22 17:31:33 philip-desktop kernel: [    0.367478] AppArmor: AppArmor Filesystem Enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.367494] pnp: PnP ACPI init
Nov 22 17:31:33 philip-desktop kernel: [    0.367510] ACPI: bus type pnp registered
Nov 22 17:31:33 philip-desktop kernel: [    0.369270] pnp: PnP ACPI: found 11 devices
Nov 22 17:31:33 philip-desktop kernel: [    0.369272] ACPI: ACPI bus type pnp unregistered
Nov 22 17:31:33 philip-desktop kernel: [    0.369282] system 00:01: [io  0x04d0-0x04d1] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369285] system 00:01: [io  0x0290-0x029f] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369287] system 00:01: [io  0x0800-0x087f] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369289] system 00:01: [io  0x0290-0x0294] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369291] system 00:01: [io  0x0880-0x088f] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369296] system 00:07: [io  0x0400-0x04cf] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369298] system 00:07: [io  0x04d2-0x04ff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369302] system 00:08: [mem 0xf4000000-0xf7ffffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369306] system 00:09: [mem 0x000d6000-0x000d7fff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369308] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369310] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369313] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369315] system 00:09: [mem 0xdfee0000-0xdfefffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369317] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369319] system 00:09: [mem 0x00100000-0xdfedffff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369321] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369323] system 00:09: [mem 0xfed10000-0xfed1dfff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369325] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369327] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369329] system 00:09: [mem 0xffb00000-0xffb7ffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369331] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.369333] system 00:09: [mem 0x000e0000-0x000effff] has been reserved
Nov 22 17:31:33 philip-desktop kernel: [    0.374870] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf01fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374874] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374876] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374879] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374882] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374884] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374886] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374889] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov 22 17:31:33 philip-desktop kernel: [    0.374891] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374894] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374896] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374900] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Nov 22 17:31:33 philip-desktop kernel: [    0.374902] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374906] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf01fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374909] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374914] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Nov 22 17:31:33 philip-desktop kernel: [    0.374916] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374920] pci 0000:00:1c.1:   bridge window [mem 0xfd800000-0xfd9fffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374923] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374928] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
Nov 22 17:31:33 philip-desktop kernel: [    0.374930] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374934] pci 0000:00:1c.3:   bridge window [mem 0xfde00000-0xfdefffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374937] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374943] pci 0000:05:00.0: BAR 6: assigned [mem 0xfdb00000-0xfdb0ffff pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374945] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
Nov 22 17:31:33 philip-desktop kernel: [    0.374948] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374952] pci 0000:00:1c.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374955] pci 0000:00:1c.4:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Nov 22 17:31:33 philip-desktop kernel: [    0.374961] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
Nov 22 17:31:33 philip-desktop kernel: [    0.374963] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374967] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
Nov 22 17:31:33 philip-desktop kernel: [    0.374970] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Nov 22 17:31:33 philip-desktop kernel: [    0.374988] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.374997] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Nov 22 17:31:33 philip-desktop kernel: [    0.375000] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.375010] pci 0000:00:1c.1: enabling device (0006 -> 0007)
Nov 22 17:31:33 philip-desktop kernel: [    0.375017] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 22 17:31:33 philip-desktop kernel: [    0.375030] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.375039] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.375127] NET: Registered protocol family 2
Nov 22 17:31:33 philip-desktop kernel: [    0.375248] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.376200] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.379565] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.380029] TCP: Hash tables configured (established 524288 bind 65536)
Nov 22 17:31:33 philip-desktop kernel: [    0.380031] TCP reno registered
Nov 22 17:31:33 philip-desktop kernel: [    0.380041] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.380073] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.380198] NET: Registered protocol family 1
Nov 22 17:31:33 philip-desktop kernel: [    0.419916] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Nov 22 17:31:33 philip-desktop kernel: [    0.419918] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
Nov 22 17:31:33 philip-desktop kernel: [    0.419920] software IO TLB at phys 0x1f9e000 - 0x5f9e000
Nov 22 17:31:33 philip-desktop kernel: [    0.420102] Scanning for low memory corruption every 60 seconds
Nov 22 17:31:33 philip-desktop kernel: [    0.420233] audit: initializing netlink socket (disabled)
Nov 22 17:31:33 philip-desktop kernel: [    0.420243] type=2000 audit(1290475877.410:1): initialized
Nov 22 17:31:33 philip-desktop kernel: [    0.431160] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 22 17:31:33 philip-desktop kernel: [    0.432228] VFS: Disk quotas dquot_6.5.2
Nov 22 17:31:33 philip-desktop kernel: [    0.432268] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 22 17:31:33 philip-desktop kernel: [    0.432688] fuse init (API version 7.14)
Nov 22 17:31:33 philip-desktop kernel: [    0.432748] msgmni has been set to 7884
Nov 22 17:31:33 philip-desktop kernel: [    0.432951] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov 22 17:31:33 philip-desktop kernel: [    0.432953] io scheduler noop registered
Nov 22 17:31:33 philip-desktop kernel: [    0.432955] io scheduler deadline registered
Nov 22 17:31:33 philip-desktop kernel: [    0.432984] io scheduler cfq registered (default)
Nov 22 17:31:33 philip-desktop kernel: [    0.433532] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 22 17:31:33 philip-desktop kernel: [    0.433610] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 22 17:31:33 philip-desktop kernel: [    0.433748] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Nov 22 17:31:33 philip-desktop kernel: [    0.433752] ACPI: Power Button [PWRB]
Nov 22 17:31:33 philip-desktop kernel: [    0.433792] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov 22 17:31:33 philip-desktop kernel: [    0.433794] ACPI: Power Button [PWRF]
Nov 22 17:31:33 philip-desktop kernel: [    0.434051] Marking TSC unstable due to TSC halts in idle
Nov 22 17:31:33 philip-desktop kernel: [    0.435710] ERST: Table is not found!
Nov 22 17:31:33 philip-desktop kernel: [    0.435855] Linux agpgart interface v0.103
Nov 22 17:31:33 philip-desktop kernel: [    0.435873] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 22 17:31:33 philip-desktop kernel: [    0.436846] brd: module loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.437208] loop: module loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.437369] pata_acpi 0000:04:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.437405] pata_acpi 0000:04:00.1: PCI INT B disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.437603] Fixed MDIO Bus: probed
Nov 22 17:31:33 philip-desktop kernel: [    0.437627] PPP generic driver version 2.4.2
Nov 22 17:31:33 philip-desktop kernel: [    0.437650] tun: Universal TUN/TAP device driver, 1.6
Nov 22 17:31:33 philip-desktop kernel: [    0.437651] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 22 17:31:33 philip-desktop kernel: [    0.437709] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 22 17:31:33 philip-desktop kernel: [    0.437730] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 17:31:33 philip-desktop kernel: [    0.437747] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.437770] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Nov 22 17:31:33 philip-desktop kernel: [    0.441684] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
Nov 22 17:31:33 philip-desktop kernel: [    0.445719] Switching to clocksource hpet
Nov 22 17:31:33 philip-desktop kernel: [    0.471271] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Nov 22 17:31:33 philip-desktop kernel: [    0.471396] hub 1-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.471401] hub 1-0:1.0: 6 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.471481] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 17:31:33 philip-desktop kernel: [    0.471507] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.471541] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Nov 22 17:31:33 philip-desktop kernel: [    0.475442] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
Nov 22 17:31:33 philip-desktop kernel: [    0.491266] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 22 17:31:33 philip-desktop kernel: [    0.491400] hub 2-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.491404] hub 2-0:1.0: 6 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.491470] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 22 17:31:33 philip-desktop kernel: [    0.491485] uhci_hcd: USB Universal Host Controller Interface driver
Nov 22 17:31:33 philip-desktop kernel: [    0.491548] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.491559] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.491589] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Nov 22 17:31:33 philip-desktop kernel: [    0.491621] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
Nov 22 17:31:33 philip-desktop kernel: [    0.491707] hub 3-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.491710] hub 3-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.491761] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov 22 17:31:33 philip-desktop kernel: [    0.491767] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.491794] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Nov 22 17:31:33 philip-desktop kernel: [    0.491820] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
Nov 22 17:31:33 philip-desktop kernel: [    0.491902] hub 4-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.491905] hub 4-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.491949] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 17:31:33 philip-desktop kernel: [    0.491955] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.491978] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Nov 22 17:31:33 philip-desktop kernel: [    0.491998] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
Nov 22 17:31:33 philip-desktop kernel: [    0.492077] hub 5-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492080] hub 5-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492126] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 17:31:33 philip-desktop kernel: [    0.492133] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.492157] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Nov 22 17:31:33 philip-desktop kernel: [    0.492177] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
Nov 22 17:31:33 philip-desktop kernel: [    0.492264] hub 6-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492267] hub 6-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492311] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.492318] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.492343] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Nov 22 17:31:33 philip-desktop kernel: [    0.492369] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
Nov 22 17:31:33 philip-desktop kernel: [    0.492451] hub 7-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492454] hub 7-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492497] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 17:31:33 philip-desktop kernel: [    0.492504] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 22 17:31:33 philip-desktop kernel: [    0.492529] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Nov 22 17:31:33 philip-desktop kernel: [    0.492550] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
Nov 22 17:31:33 philip-desktop kernel: [    0.492634] hub 8-0:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    0.492639] hub 8-0:1.0: 2 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    0.492726] PNP: No PS/2 controller found. Probing ports directly.
Nov 22 17:31:33 philip-desktop kernel: [    0.493083] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 22 17:31:33 philip-desktop kernel: [    0.493087] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 22 17:31:33 philip-desktop kernel: [    0.493167] mice: PS/2 mouse device common for all mice
Nov 22 17:31:33 philip-desktop kernel: [    0.493256] rtc_cmos 00:04: RTC can wake from S4
Nov 22 17:31:33 philip-desktop kernel: [    0.493289] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Nov 22 17:31:33 philip-desktop kernel: [    0.493310] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Nov 22 17:31:33 philip-desktop kernel: [    0.493381] device-mapper: uevent: version 1.0.3
Nov 22 17:31:33 philip-desktop kernel: [    0.493446] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Nov 22 17:31:33 philip-desktop kernel: [    0.493492] device-mapper: multipath: version 1.1.1 loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.493494] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.493628] cpuidle: using governor ladder
Nov 22 17:31:33 philip-desktop kernel: [    0.493664] cpuidle: using governor menu
Nov 22 17:31:33 philip-desktop kernel: [    0.493862] TCP cubic registered
Nov 22 17:31:33 philip-desktop kernel: [    0.493951] NET: Registered protocol family 10
Nov 22 17:31:33 philip-desktop kernel: [    0.494214] lo: Disabled Privacy Extensions
Nov 22 17:31:33 philip-desktop kernel: [    0.494355] NET: Registered protocol family 17
Nov 22 17:31:33 philip-desktop kernel: [    0.495252] registered taskstats version 1
Nov 22 17:31:33 philip-desktop kernel: [    0.495550]   Magic number: 2:340:509
Nov 22 17:31:33 philip-desktop kernel: [    0.495634] rtc_cmos 00:04: setting system clock to 2010-11-23 01:31:17 UTC (1290475877)
Nov 22 17:31:33 philip-desktop kernel: [    0.495636] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 22 17:31:33 philip-desktop kernel: [    0.495638] EDD information not available.
Nov 22 17:31:33 philip-desktop kernel: [    0.570735] Freeing initrd memory: 16580k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.576458] Freeing unused kernel memory: 908k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.576782] Write protecting the kernel read-only data: 10240k
Nov 22 17:31:33 philip-desktop kernel: [    0.576924] Freeing unused kernel memory: 416k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.577167] Freeing unused kernel memory: 1644k freed
Nov 22 17:31:33 philip-desktop kernel: [    0.589515] udev[77]: starting version 163
Nov 22 17:31:33 philip-desktop kernel: [    0.649710] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.649799] ahci: SSS flag set, parallel bus scan disabled
Nov 22 17:31:33 philip-desktop kernel: [    0.649828] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Nov 22 17:31:33 philip-desktop kernel: [    0.649831] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems 
Nov 22 17:31:33 philip-desktop kernel: [    0.661936] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 22 17:31:33 philip-desktop kernel: [    0.661958] r8169 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.662411] r8169 0000:05:00.0: eth0: RTL8168c/8111c at 0xffffc90000674000, 00:24:1d:c6:93:ce, XID 1c4000c0 IRQ 46
Nov 22 17:31:33 philip-desktop kernel: [    0.672921] pata_jmicron 0000:04:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [    0.678831] firewire_ohci 0000:06:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 17:31:33 philip-desktop kernel: [    0.680083] scsi0 : pata_jmicron
Nov 22 17:31:33 philip-desktop kernel: [    0.682789] scsi1 : pata_jmicron
Nov 22 17:31:33 philip-desktop kernel: [    0.683333] ata1: PATA max UDMA/100 cmd 0xbf00 ctl 0xbe00 bmdma 0xbb00 irq 16
Nov 22 17:31:33 philip-desktop kernel: [    0.683336] ata2: PATA max UDMA/100 cmd 0xbd00 ctl 0xbc00 bmdma 0xbb08 irq 16
Nov 22 17:31:33 philip-desktop kernel: [    0.740043] firewire_ohci: Added fw-ohci device 0000:06:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Nov 22 17:31:33 philip-desktop kernel: [    0.770069] scsi2 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770173] scsi3 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770236] scsi4 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770285] scsi5 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770335] scsi6 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770383] scsi7 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.770501] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770503] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770505] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770508] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770510] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770512] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 45
Nov 22 17:31:33 philip-desktop kernel: [    0.770547] ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 22 17:31:33 philip-desktop kernel: [    0.781286] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Nov 22 17:31:33 philip-desktop kernel: [    0.781292] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Nov 22 17:31:33 philip-desktop kernel: [    0.781437] scsi8 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.781492] scsi9 : ahci
Nov 22 17:31:33 philip-desktop kernel: [    0.781557] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 19
Nov 22 17:31:33 philip-desktop kernel: [    0.781561] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 19
Nov 22 17:31:33 philip-desktop kernel: [    0.791312] usb 1-1: new high speed USB device using ehci_hcd and address 2
Nov 22 17:31:33 philip-desktop kernel: [    1.110023] ata3: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.131300] ata9: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.231336] firewire_core: created device fw0: GUID 00cb62800000241d, S400
Nov 22 17:31:33 philip-desktop kernel: [    1.310027] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.347252] ata10.00: ATA-8: ST9250410AS, D005SDM1, max UDMA/133
Nov 22 17:31:33 philip-desktop kernel: [    1.347257] ata10.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 22 17:31:33 philip-desktop kernel: [    1.349163] ata10.00: configured for UDMA/133
Nov 22 17:31:33 philip-desktop kernel: [    1.460016] usb 4-1: new full speed USB device using uhci_hcd and address 2
Nov 22 17:31:33 philip-desktop kernel: [    1.480020] ata4: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.861268] ata5: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    1.921258] usb 6-2: new full speed USB device using uhci_hcd and address 2
Nov 22 17:31:33 philip-desktop kernel: [    2.112249] hub 6-2:1.0: USB hub found
Nov 22 17:31:33 philip-desktop kernel: [    2.114211] hub 6-2:1.0: 3 ports detected
Nov 22 17:31:33 philip-desktop kernel: [    2.231268] ata6: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    2.391211] usb 6-2.2: new full speed USB device using uhci_hcd and address 3
Nov 22 17:31:33 philip-desktop kernel: [    2.641211] usb 6-2.3: new full speed USB device using uhci_hcd and address 4
Nov 22 17:31:33 philip-desktop kernel: [    2.781259] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    2.782844] ata7.00: ATAPI: ATAPI   iHAS324   Y, BL1W, max UDMA/100
Nov 22 17:31:33 philip-desktop kernel: [    2.785078] ata7.00: configured for UDMA/100
Nov 22 17:31:33 philip-desktop kernel: [    2.802846] scsi 6:0:0:0: CD-ROM            ATAPI    iHAS324   Y      BL1W PQ: 0 ANSI: 5
Nov 22 17:31:33 philip-desktop kernel: [    2.805016] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 22 17:31:33 philip-desktop kernel: [    2.805019] Uniform CD-ROM driver Revision: 3.20
Nov 22 17:31:33 philip-desktop kernel: [    2.805138] sr 6:0:0:0: Attached scsi generic sg0 type 5
Nov 22 17:31:33 philip-desktop kernel: [    2.808057] usbcore: registered new interface driver hiddev
Nov 22 17:31:33 philip-desktop kernel: [    2.813478] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.2/6-2.2:1.0/input/input2
Nov 22 17:31:33 philip-desktop kernel: [    2.813538] generic-usb 0003:046D:C71B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-2.2/input0
Nov 22 17:31:33 philip-desktop kernel: [    2.822803] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.3/6-2.3:1.0/input/input3
Nov 22 17:31:33 philip-desktop kernel: [    2.822932] generic-usb 0003:046D:C71C.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-2.3/input0
Nov 22 17:31:33 philip-desktop kernel: [    2.822944] usbcore: registered new interface driver usbhid
Nov 22 17:31:33 philip-desktop kernel: [    2.822945] usbhid: USB HID core driver
Nov 22 17:31:33 philip-desktop kernel: [    3.150021] ata8: SATA link down (SStatus 0 SControl 300)
Nov 22 17:31:33 philip-desktop kernel: [    3.170139] scsi 9:0:0:0: Direct-Access     ATA      ST9250410AS      D005 PQ: 0 ANSI: 5
Nov 22 17:31:33 philip-desktop kernel: [    3.170255] sd 9:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Nov 22 17:31:33 philip-desktop kernel: [    3.170258] sd 9:0:0:0: Attached scsi generic sg1 type 0
Nov 22 17:31:33 philip-desktop kernel: [    3.170299] sd 9:0:0:0: [sda] Write Protect is off
Nov 22 17:31:33 philip-desktop kernel: [    3.170319] sd 9:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 17:31:33 philip-desktop kernel: [    3.170435]  sda: sda1 sda2 < sda5 >
Nov 22 17:31:33 philip-desktop kernel: [    3.246142] sd 9:0:0:0: [sda] Attached SCSI disk
Nov 22 17:31:33 philip-desktop kernel: [    3.628276] Btrfs loaded
Nov 22 17:31:33 philip-desktop kernel: [    3.631578] xor: automatically using best checksumming function: generic_sse
Nov 22 17:31:33 philip-desktop kernel: [    3.680004]    generic_sse: 10703.600 MB/sec
Nov 22 17:31:33 philip-desktop kernel: [    3.680006] xor: using function: generic_sse (10703.600 MB/sec)
Nov 22 17:31:33 philip-desktop kernel: [    3.681764] device-mapper: dm-raid45: initialized v0.2594b
Nov 22 17:31:33 philip-desktop kernel: [    3.919137] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Nov 22 17:31:33 philip-desktop kernel: [    3.919141] EXT4-fs (sda1): write access will be enabled during recovery
Nov 22 17:31:33 philip-desktop kernel: [    6.382350] EXT4-fs (sda1): orphan cleanup on readonly fs
Nov 22 17:31:33 philip-desktop kernel: [    6.382528] EXT4-fs (sda1): 10 orphan inodes deleted
Nov 22 17:31:33 philip-desktop kernel: [    6.382531] EXT4-fs (sda1): recovery complete
Nov 22 17:31:33 philip-desktop kernel: [    6.938574] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Nov 22 17:31:33 philip-desktop kernel: [   15.540462] udev[460]: starting version 163
Nov 22 17:31:33 philip-desktop kernel: [   15.629527] Adding 9936892k swap on /dev/sda5.  Priority:-1 extents:1 across:9936892k 
Nov 22 17:31:33 philip-desktop kernel: [   15.676743] lp: driver loaded but no devices found
Nov 22 17:31:33 philip-desktop kernel: [   15.779102] cfg80211: Calling CRDA to update world regulatory domain
Nov 22 17:31:33 philip-desktop kernel: [   15.779350] Linux video capture interface: v2.00
Nov 22 17:31:33 philip-desktop kernel: [   15.815638] nvidia: module license 'NVIDIA' taints kernel.
Nov 22 17:31:33 philip-desktop kernel: [   15.815641] Disabling lock debugging due to kernel taint
Nov 22 17:31:33 philip-desktop kernel: [   15.911216] cfg80211: World regulatory domain updated:
Nov 22 17:31:33 philip-desktop kernel: [   15.911218]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 22 17:31:33 philip-desktop kernel: [   15.911220]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911222]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911224]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911226]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911228]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 17:31:33 philip-desktop kernel: [   15.911405] IR NEC protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   15.959354] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 22 17:31:33 philip-desktop kernel: [   15.960919] cx23885 driver version 0.0.2 loaded
Nov 22 17:31:33 philip-desktop kernel: [   15.960948] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 22 17:31:33 philip-desktop kernel: [   15.961299] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
Nov 22 17:31:33 philip-desktop kernel: [   16.238935] IR RC5(x) protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.240350] IR RC6 protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.242281] IR JVC protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.243677] IR Sony protocol handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.246034] lirc_dev: IR Remote Control driver registered, major 249 
Nov 22 17:31:33 philip-desktop kernel: [   16.247073] IR LIRC bridge handler initialized
Nov 22 17:31:33 philip-desktop kernel: [   16.350753] tveeprom 0-0050: Hauppauge model 78521, rev C1E9, serial# 2954264
Nov 22 17:31:33 philip-desktop kernel: [   16.350756] tveeprom 0-0050: MAC address is 00:0d:fe:2d:14:18
Nov 22 17:31:33 philip-desktop kernel: [   16.350758] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
Nov 22 17:31:33 philip-desktop kernel: [   16.350761] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Nov 22 17:31:33 philip-desktop kernel: [   16.350763] tveeprom 0-0050: audio processor is CX23887 (idx 42)
Nov 22 17:31:33 philip-desktop kernel: [   16.350765] tveeprom 0-0050: decoder processor is CX23887 (idx 37)
Nov 22 17:31:33 philip-desktop kernel: [   16.350766] tveeprom 0-0050: has radio
Nov 22 17:31:33 philip-desktop kernel: [   16.350768] cx23885[0]: hauppauge eeprom: model=78521
Nov 22 17:31:33 philip-desktop kernel: [   16.354169] cx25840 2-0044: cx23887 A/V decoder found @ 0x88 (cx23885[0])
Nov 22 17:31:33 philip-desktop kernel: [   16.364936] Registered IR keymap rc-rc6-mce
Nov 22 17:31:33 philip-desktop kernel: [   16.365000] input: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/virtual/rc/rc0/input4
Nov 22 17:31:33 philip-desktop kernel: [   16.365042] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/virtual/rc/rc0
Nov 22 17:31:33 philip-desktop kernel: [   16.365066] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
Nov 22 17:31:33 philip-desktop kernel: [   16.365081] mceusb 4-1:1.0: Registered SMK eHome Infrared Transceiver on usb4:2
Nov 22 17:31:33 philip-desktop kernel: [   16.365111] usbcore: registered new interface driver mceusb
Nov 22 17:31:33 philip-desktop kernel: [   16.498618] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 17:31:33 philip-desktop kernel: [   16.498629] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Nov 22 17:31:33 philip-desktop kernel: [   16.498796] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.21  Thu Nov  4 21:16:27 PDT 2010
Nov 22 17:31:33 philip-desktop kernel: [   16.612953] phy0: hwaddr 00:22:3f:5c:ad:4f, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
Nov 22 17:31:33 philip-desktop kernel: [   16.623983] rtl8187: Customer ID is 0xFF
Nov 22 17:31:33 philip-desktop kernel: [   16.625475] rtl8187: wireless switch is on
Nov 22 17:31:33 philip-desktop kernel: [   16.625538] usbcore: registered new interface driver rtl8187
Nov 22 17:31:33 philip-desktop kernel: [   16.865595] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Nov 22 17:31:34 philip-desktop kernel: [   17.169916] cx25840 2-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
Nov 22 17:31:34 philip-desktop kernel: [   17.181390] tuner 1-0042: chip found @ 0x84 (cx23885[0])
Nov 22 17:31:34 philip-desktop kernel: [   17.232154] tda829x 1-0042: could not clearly identify tuner address, defaulting to 60
Nov 22 17:31:34 philip-desktop kernel: [   17.261636] tda18271 1-0060: creating new instance
Nov 22 17:31:34 philip-desktop kernel: [   17.310378] TDA18271HD/C1 detected @ 1-0060
Nov 22 17:31:34 philip-desktop kernel: [   17.841538] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e73d60
Nov 22 17:31:34 philip-desktop kernel: [   17.841552] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x7d5
Nov 22 17:31:34 philip-desktop kernel: [   17.841587] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Nov 22 17:31:36 philip-desktop kernel: [   19.222453] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 22 17:31:36 philip-desktop kernel: [   19.224497] r8169 0000:05:00.0: eth0: link up
Nov 22 17:31:36 philip-desktop kernel: [   19.224502] r8169 0000:05:00.0: eth0: link up
Nov 22 17:31:37 philip-desktop kernel: [   20.006837] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 22 17:31:37 philip-desktop kernel: [   20.400356] tda829x 1-0042: type set to tda8295+18271
Nov 22 17:31:39 philip-desktop kernel: [   22.020429] cx23885[0]/0: registered device video0 [v4l2]
Nov 22 17:31:41 philip-desktop kernel: [   23.494343] cx23885[0]: registered device video1 [mpeg]
Nov 22 17:31:41 philip-desktop kernel: [   23.494346] cx23885_dvb_register() allocating 1 frontend(s)
Nov 22 17:31:41 philip-desktop kernel: [   23.494348] cx23885[0]: cx23885 based dvb card
Nov 22 17:31:41 philip-desktop kernel: [   23.525357] MT2131: successfully identified at address 0x61
Nov 22 17:31:41 philip-desktop kernel: [   23.526988] DVB: registering new adapter (cx23885[0])
Nov 22 17:31:41 philip-desktop kernel: [   23.526991] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Nov 22 17:31:41 philip-desktop kernel: [   23.527219] cx23885_dev_checkrevision() Hardware revision = 0xb1
Nov 22 17:31:41 philip-desktop kernel: [   23.527226] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xfd800000
Nov 22 17:31:41 philip-desktop kernel: [   23.596979] ppdev: user-space parallel port driver
Nov 22 17:31:44 philip-desktop kernel: [   26.624603] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Nov 22 17:46:10 philip-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="996" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
```

---

### Post by matt_symes on 2010-11-23
Hi

BTW: If all the hardware is the same, have you double checked all the connectors and ensured the boards are seated correct. All the fans are connected correctly and it not overheating.

If it was stable for two years and the only thing that was changed was the  case and no new hardware or software updates were added then i would be tempted to look there as a start.

Do you know what software updates, if any, have been installed since you changed the case?

> I have been using ubuntu since hardy on this machine and only lately (10.04 & 10.10) have the problems been occuring.Have you just installed these? When? How? Where are the logs from (hardy, 10.04, 10.10)?

The problem is it could be sooooooo many things.

Kind regards

---

### Post by Philip550c on 2010-11-23
> **matt_symes said:**
> Hi

BTW: If all the hardware is the same, have you double checked all the connectors and ensured the boards are seated correct. All the fans are connected correctly and it not overheating.

If it was stable for two years and the only thing that was changed was the  case and no new hardware or software updates were added then i would be tempted to look there as a start.

Do you know what software updates, if any, have been installed since you changed the case?

Have you just installed these? When? How? Where are the logs from (hardy, 10.04, 10.10)?

The problem is it could be sooooooo many things.

Kind regards

Its not overheating, the new case has a double the fans, I have water cooling and its freezing in my house. I have pulled the board out and reseated it as well. I have def changed the software after changing the case, i tried a fresh install of 10.04 and 10.10. So no logs for the old OS's. Sorry if I wasn't clear

---

### Post by matt_symes on 2010-11-23
Hi

Alright. Is it random freezing?

Take a look at this...........

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

Kind regards

---

### Post by Philip550c on 2010-11-23
> **matt_symes said:**
> Hi

Alright. Is it random freezing?

Take a look at this...........

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

Kind regards

Sort of, it happens when I'm not using it or when I reboot. Ill go to bed and wake up and its frozen, I can use it all day fine but if I restart or if i just leave it alone, theres no telling if it'll load up or work correctly.

---

### Post by clhsharky on 2010-11-23
Philip550c

What video chip and driver are you using?

Ive had that problem in past with certain screensavers, turn off SS and let monitor go to sleep. If that solves morning freeze you know where problem lyes.
If you have SS set to random, choose one simple SS or a picture file. It might be just one screensaver that is problem.

Your video driver might not handle all the newer fancy screensavers in latest releases, or maybe its a bug.

Sharky

---

### Post by Philip550c on 2010-11-23
> **clhsharky said:**
> Philip550c

What video chip and driver are you using?

Ive had that problem in past with certain screensavers, turn off SS and let monitor go to sleep. If that solves morning freeze you know where problem lyes.
If you have SS set to random, choose one simple SS or a picture file. It might be just one screensaver that is problem.

Your video driver might not handle all the newer fancy screensavers in latest releases, or maybe its a bug.

Sharky

Thanks for helping. My video card is an Nvidia GTS250 and my drivers are 260.19.21, the screensaver is electricsheep and it runs fine while im watching it but I think maybe when the monitor goes to sleep it freezes.

---

### Post by matt_symes on 2010-11-24
Hi

> **Philip550c said:**
> Thanks for helping. My video card is an Nvidia GTS250 and my drivers are 260.19.21, the screensaver is electricsheep and it runs fine while im watching it but I think maybe when the monitor goes to sleep it freezes.

You might be able to test this. At a terminal type

xset dpms force suspend

Other options are standby,  off, on for above. This will put your monitor to sleep.

You can also type 

sudo pm-suspend

At the  terminal to suspend you PC.

Do either of these cause your freezing?

Kind regards

---

### Post by Philip550c on 2010-11-26
> **matt_symes said:**
> Hi



You might be able to test this. At a terminal type

xset dpms force suspend

Other options are standby,  off, on for above. This will put your monitor to sleep.

You can also type 

sudo pm-suspend

At the  terminal to suspend you PC.

Do either of these cause your freezing?

Kind regards

Neither of those commands froze the computer. And the computer was still working this morning. I started watching a movie today though and halfway through it froze and the audio went into a loop. I guess Im gonna completely wipe the drives and start fresh and see what happens.

---

### Post by tgalati4 on 2010-11-26
I would suspect a bad power supply.  Check the voltages with a voltmeter.  Your 5 VDC and 12 VDC need to be pretty close to those values.  Sometimes you can see the voltages in BIOS.  Sometimes the voltages look OK, but they sag under load causing random problems.  Pull the power supply from another computer, or purchase a replacement with a 30-day return policy.  If it still freezes with the new power supply, then it's something else.  It could also be a chip delamination.  Put your finger on the large chips while it is running.  The real hot ones could be failing.  You might also need to clean and reapply thermal grease to the CPU and GPU if they are older machines and haven't been cleaned out in a while.

---

### Post by matt_symes on 2010-11-27
Hi

After it freezes, what mesages does dmesg display?

Kind regards

---

### Post by Philip550c on 2010-11-29
> **matt_symes said:**
> Hi

After it freezes, what mesages does dmesg display?

Kind regards

how do i check that?

---

### Post by Philip550c on 2010-11-29
> **tgalati4 said:**
> I would suspect a bad power supply.  Check the voltages with a voltmeter.  Your 5 VDC and 12 VDC need to be pretty close to those values.  Sometimes you can see the voltages in BIOS.  Sometimes the voltages look OK, but they sag under load causing random problems.  Pull the power supply from another computer, or purchase a replacement with a 30-day return policy.  If it still freezes with the new power supply, then it's something else.  It could also be a chip delamination.  Put your finger on the large chips while it is running.  The real hot ones could be failing.  You might also need to clean and reapply thermal grease to the CPU and GPU if they are older machines and haven't been cleaned out in a while.

I'll check it out thank you. I have this power supply and its less than a year old. [http://www.newegg.com/Product/Product.aspx?Item=N82E16817703013]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817703013") I have recently changed the thermal grease and my computer is water cooled btw.

---

