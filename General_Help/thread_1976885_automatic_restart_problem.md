---
title: "automatic restart problem"
date: 2012-05-09
forum: General Help
---

### Post by songhk on 2012-05-09
Recently when I used my computer, my computer restarted automatically.

Ubuntu 12.04
Linux 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Is this problem related to the partition?
When I installed Ubuntu 12.04, I chose to use entire disk, and Ubuntu automatically configured it.

partition information
/dev/sda1   ext4          /    923.6 GB         boot    
/dev/sda2   extended             7.91GB   
/dev/sda5   linux-swap           7.91GB

I need comments.
Thanks

---

### Post by smurphy on 2012-05-09
How should a partition be culprit for a restart ?

Eventually you should check in the /var/log directory, if there are not some hints why the system restarted.
check the syslog.log or kern.log file - they may tell you what was going on.

---

### Post by songhk on 2012-05-09
Dear smurphy

I checked the reboot information. 
My computer was rebooted at 9:04am today as follows.

reboot   system boot  3.2.0-24-generic Wed May  9 09:04 - 10:30  (01:25)


And here is the output of /var/log/syslog  

/var/log/syslog


May  9 07:53:41 swordfish rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="753" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
May  9 07:53:57 swordfish anacron[12517]: Job `cron.daily' terminated
May  9 07:53:57 swordfish anacron[12517]: Normal exit (1 job run)
May  9 08:17:01 swordfish CRON[12923]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  9 09:04:47 swordfish kernel: imklog 5.8.6, log source = /proc/kmsg started.
May  9 09:04:47 swordfish rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="788" x-info="http://www.rsyslog.com"] start
May  9 09:04:47 swordfish rsyslogd: rsyslogd's groupid changed to 103
May  9 09:04:47 swordfish rsyslogd: rsyslogd's userid changed to 101
May  9 09:04:47 swordfish rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
May  9 09:04:47 swordfish kernel: [    0.000000] Initializing cgroup subsys cpuset
May  9 09:04:47 swordfish kernel: [    0.000000] Initializing cgroup subsys cpu
May  9 09:04:47 swordfish kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@yellow) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
May  9 09:04:47 swordfish kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1fa1e5b9-b632-4aaa-af25-1b7036647204 ro acpi=force quiet splash vt.handoff=7
May  9 09:04:47 swordfish kernel: [    0.000000] KERNEL supported cpus:
May  9 09:04:47 swordfish kernel: [    0.000000]   Intel GenuineIntel
May  9 09:04:47 swordfish kernel: [    0.000000]   AMD AuthenticAMD
May  9 09:04:47 swordfish kernel: [    0.000000]   Centaur CentaurHauls
May  9 09:04:47 swordfish kernel: [    0.000000] BIOS-provided physical RAM map:
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000040200000 - 00000000bad81000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bad81000 - 00000000badd8000 (ACPI NVS)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000badd8000 - 00000000badfb000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000badfb000 - 00000000badfd000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000badfd000 - 00000000bae0d000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae0d000 - 00000000bae1a000 (ACPI NVS)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae1a000 - 00000000bae3c000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae3c000 - 00000000bae7f000 (ACPI NVS)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae7f000 - 00000000bb000000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bb800000 - 00000000bfa00000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023fe00000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000] NX (Execute Disable) protection: active
May  9 09:04:47 swordfish kernel: [    0.000000] DMI 2.6 present.
May  9 09:04:47 swordfish kernel: [    0.000000] DMI: ECS H61H2-M3/H61H2-M3, BIOS 4.6.4 03/29/2011
May  9 09:04:47 swordfish kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000] No AGP bridge found
May  9 09:04:47 swordfish kernel: [    0.000000] last_pfn = 0x23fe00 max_arch_pfn = 0x400000000
May  9 09:04:47 swordfish kernel: [    0.000000] MTRR default type: uncachable
May  9 09:04:47 swordfish kernel: [    0.000000] MTRR fixed ranges enabled:
May  9 09:04:47 swordfish kernel: [    0.000000]   00000-9FFFF write-back
May  9 09:04:47 swordfish kernel: [    0.000000]   A0000-BFFFF uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   C0000-CFFFF write-protect
May  9 09:04:47 swordfish kernel: [    0.000000]   D0000-E7FFF uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   E8000-FFFFF write-protect
May  9 09:04:47 swordfish kernel: [    0.000000] MTRR variable ranges enabled:
May  9 09:04:47 swordfish kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
May  9 09:04:47 swordfish kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
May  9 09:04:47 swordfish kernel: [    0.000000]   2 base 0BB800000 mask FFF800000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   4 base 0C0000000 mask FC0000000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   5 base 23FE00000 mask FFFE00000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   6 disabled
May  9 09:04:47 swordfish kernel: [    0.000000]   7 disabled
May  9 09:04:47 swordfish kernel: [    0.000000]   8 disabled
May  9 09:04:47 swordfish kernel: [    0.000000]   9 disabled
May  9 09:04:47 swordfish kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  9 09:04:47 swordfish kernel: [    0.000000] original variable MTRRs
May  9 09:04:47 swordfish kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 1, base: 8GB, range: 1GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 2, base: 3000MB, range: 8MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 4, base: 3GB, range: 1GB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 5, base: 9214MB, range: 2MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] total RAM covered: 8118M
May  9 09:04:47 swordfish kernel: [    0.000000] Found optimal setting for mtrr clean up
May  9 09:04:47 swordfish kernel: [    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 7  	lose cover RAM: 0G
May  9 09:04:47 swordfish kernel: [    0.000000] New variable MTRRs
May  9 09:04:47 swordfish kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 2, base: 3000MB, range: 8MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 5, base: 8GB, range: 1GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 6, base: 9214MB, range: 2MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] e820 update range: 00000000bb800000 - 0000000100000000 (usable) ==> (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000] last_pfn = 0xbb000 max_arch_pfn = 0x400000000
May  9 09:04:47 swordfish kernel: [    0.000000] found SMP MP-table at [ffff8800000fce80] fce80
May  9 09:04:47 swordfish kernel: [    0.000000] initial memory mapped : 0 - 20000000
May  9 09:04:47 swordfish kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
May  9 09:04:47 swordfish kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bb000000
May  9 09:04:47 swordfish kernel: [    0.000000]  0000000000 - 00bb000000 page 2M
May  9 09:04:47 swordfish kernel: [    0.000000] kernel direct mapping tables up to bb000000 @ 1fffc000-20000000
May  9 09:04:47 swordfish kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000023fe00000
May  9 09:04:47 swordfish kernel: [    0.000000]  0100000000 - 023fe00000 page 2M
May  9 09:04:47 swordfish kernel: [    0.000000] kernel direct mapping tables up to 23fe00000 @ baff6000-bb000000
May  9 09:04:47 swordfish kernel: [    0.000000] RAMDISK: 364e8000 - 3726c000
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: XSDT 00000000badce070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: FACP 00000000badd6a98 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: DSDT 00000000badce168 0892F (v02 ALASKA    A M I 00000010 INTL 20051117)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: FACS 00000000bae11f80 00040
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: APIC 00000000badd6b90 00092 (v03 ALASKA    A M I 01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: SSDT 00000000badd6c28 001D6 (v01 AMICPU     PROC 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: MCFG 00000000badd6e00 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: SLIC 00000000badd6e40 00176 (v01 AMI    APTIO    01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: WDTT 00000000badd6fb8 00194 (v02 ALASKA    A M I 01072009 AMI  00000000)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: HPET 00000000badd7150 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: ASPT 00000000badd7188 00034 (v07 ALASKA PerfTune 01072009 AMI  00000000)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  9 09:04:47 swordfish kernel: [    0.000000] No NUMA configuration found
May  9 09:04:47 swordfish kernel: [    0.000000] Faking a node at 0000000000000000-000000023fe00000
May  9 09:04:47 swordfish kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000023fe00000
May  9 09:04:47 swordfish kernel: [    0.000000]   NODE_DATA [000000023fdfb000 - 000000023fdfffff]
May  9 09:04:47 swordfish kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237400000-ffff88023f3fffff] on node 0
May  9 09:04:47 swordfish kernel: [    0.000000] Zone PFN ranges:
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May  9 09:04:47 swordfish kernel: [    0.000000]   Normal   0x00100000 -> 0x0023fe00
May  9 09:04:47 swordfish kernel: [    0.000000] Movable zone start PFN for each node
May  9 09:04:47 swordfish kernel: [    0.000000] early_node_map[7] active PFN ranges
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00020200 -> 0x00040000
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00040200 -> 0x000bad81
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x000badfb -> 0x000badfd
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x000bae7f -> 0x000bb000
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00100000 -> 0x0023fe00
May  9 09:04:47 swordfish kernel: [    0.000000] On node 0 totalpages: 2074770
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA zone: 64 pages used for memmap
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA zone: 5 pages reserved
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA32 zone: 744260 pages, LIFO batch:31
May  9 09:04:47 swordfish kernel: [    0.000000]   Normal zone: 20472 pages used for memmap
May  9 09:04:47 swordfish kernel: [    0.000000]   Normal zone: 1289736 pages, LIFO batch:31
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
May  9 09:04:47 swordfish kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IRQ0 used by override.
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IRQ2 used by override.
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IRQ9 used by override.
May  9 09:04:47 swordfish kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
May  9 09:04:47 swordfish kernel: [    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
May  9 09:04:47 swordfish kernel: [    0.000000] nr_irqs_gsi: 40
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bad81000 - 00000000badd8000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000badd8000 - 00000000badfb000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000badfd000 - 00000000bae0d000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bae0d000 - 00000000bae1a000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bae1a000 - 00000000bae3c000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bae3c000 - 00000000bae7f000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bb800000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000bfa00000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000fed1c000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
May  9 09:04:47 swordfish kernel: [    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:3f31c000)
May  9 09:04:47 swordfish kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  9 09:04:47 swordfish kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
May  9 09:04:47 swordfish kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023fa00000 s83072 r8192 d23424 u262144
May  9 09:04:47 swordfish kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
May  9 09:04:47 swordfish kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
May  9 09:04:47 swordfish kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2037909
May  9 09:04:47 swordfish kernel: [    0.000000] Policy zone: Normal
May  9 09:04:47 swordfish kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1fa1e5b9-b632-4aaa-af25-1b7036647204 ro acpi=force quiet splash vt.handoff=7
May  9 09:04:47 swordfish kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  9 09:04:47 swordfish kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
May  9 09:04:47 swordfish kernel: [    0.000000] Checking aperture...
May  9 09:04:47 swordfish kernel: [    0.000000] No AGP bridge found
May  9 09:04:47 swordfish kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
May  9 09:04:47 swordfish kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
May  9 09:04:47 swordfish kernel: [    0.000000] Memory: 8071372k/9435136k available (6566k kernel code, 1136056k absent, 227708k reserved, 6637k data, 920k init)
May  9 09:04:47 swordfish kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
May  9 09:04:47 swordfish kernel: [    0.000000] Hierarchical RCU implementation.
May  9 09:04:47 swordfish kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
May  9 09:04:47 swordfish kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
May  9 09:04:47 swordfish kernel: [    0.000000] Extended CMOS year: 2000
May  9 09:04:47 swordfish kernel: [    0.000000] vt handoff: transparent VT on vt#7
May  9 09:04:47 swordfish kernel: [    0.000000] Console: colour dummy device 80x25
May  9 09:04:47 swordfish kernel: [    0.000000] console [tty0] enabled
May  9 09:04:47 swordfish kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
May  9 09:04:47 swordfish kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  9 09:04:47 swordfish kernel: [    0.000000] hpet clockevent registered
May  9 09:04:47 swordfish kernel: [    0.000000] Fast TSC calibration using PIT
May  9 09:04:47 swordfish kernel: [    0.004000] Detected 3392.137 MHz processor.
May  9 09:04:47 swordfish kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.27 BogoMIPS (lpj=13568548)
May  9 09:04:47 swordfish kernel: [    0.000004] pid_max: default: 32768 minimum: 301
May  9 09:04:47 swordfish kernel: [    0.000019] Security Framework initialized
May  9 09:04:47 swordfish kernel: [    0.000029] AppArmor: AppArmor initialized
May  9 09:04:47 swordfish kernel: [    0.000030] Yama: becoming mindful.
May  9 09:04:47 swordfish kernel: [    0.000538] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
May  9 09:04:47 swordfish kernel: [    0.001788] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  9 09:04:47 swordfish kernel: [    0.002275] Mount-cache hash table entries: 256
May  9 09:04:47 swordfish kernel: [    0.002348] Initializing cgroup subsys cpuacct
May  9 09:04:47 swordfish kernel: [    0.002351] Initializing cgroup subsys memory
May  9 09:04:47 swordfish kernel: [    0.002356] Initializing cgroup subsys devices
May  9 09:04:47 swordfish kernel: [    0.002357] Initializing cgroup subsys freezer
May  9 09:04:47 swordfish kernel: [    0.002358] Initializing cgroup subsys blkio
May  9 09:04:47 swordfish kernel: [    0.002362] Initializing cgroup subsys perf_event
May  9 09:04:47 swordfish kernel: [    0.002381] CPU: Physical Processor ID: 0
May  9 09:04:47 swordfish kernel: [    0.002382] CPU: Processor Core ID: 0
May  9 09:04:47 swordfish kernel: [    0.002385] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
May  9 09:04:47 swordfish kernel: [    0.002385] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
May  9 09:04:47 swordfish kernel: [    0.002388] mce: CPU supports 9 MCE banks
May  9 09:04:47 swordfish kernel: [    0.002398] CPU0: Thermal monitoring enabled (TM1)
May  9 09:04:47 swordfish kernel: [    0.002404] using mwait in idle threads.
May  9 09:04:47 swordfish kernel: [    0.004149] ACPI: Core revision 20110623
May  9 09:04:47 swordfish kernel: [    0.006610] ftrace: allocating 27049 entries in 107 pages
May  9 09:04:47 swordfish kernel: [    0.013618] x2apic not enabled, IRQ remapping init failed
May  9 09:04:47 swordfish kernel: [    0.014017] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  9 09:04:47 swordfish kernel: [    0.053585] CPU0: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz stepping 07
May  9 09:04:47 swordfish kernel: [    0.160553] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
May  9 09:04:47 swordfish kernel: [    0.160556] PEBS disabled due to CPU errata.
May  9 09:04:47 swordfish kernel: [    0.160558] ... version:                3
May  9 09:04:47 swordfish kernel: [    0.160559] ... bit width:              48
May  9 09:04:47 swordfish kernel: [    0.160559] ... generic registers:      4
May  9 09:04:47 swordfish kernel: [    0.160560] ... value mask:             0000ffffffffffff
May  9 09:04:47 swordfish kernel: [    0.160561] ... max period:             000000007fffffff
May  9 09:04:47 swordfish kernel: [    0.160562] ... fixed-purpose events:   3
May  9 09:04:47 swordfish kernel: [    0.160563] ... event mask:             000000070000000f
May  9 09:04:47 swordfish kernel: [    0.160666] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.160714] Booting Node   0, Processors  #1
May  9 09:04:47 swordfish kernel: [    0.160715] smpboot cpu 1: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.268337] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.268400]  #2
May  9 09:04:47 swordfish kernel: [    0.268401] smpboot cpu 2: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.376017] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.376075]  #3
May  9 09:04:47 swordfish kernel: [    0.376076] smpboot cpu 3: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.483693] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.483750]  #4
May  9 09:04:47 swordfish kernel: [    0.483751] smpboot cpu 4: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.591469] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.591535]  #5
May  9 09:04:47 swordfish kernel: [    0.591536] smpboot cpu 5: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.699154] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.699213]  #6
May  9 09:04:47 swordfish kernel: [    0.699214] smpboot cpu 6: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.806830] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.806888]  #7 Ok.
May  9 09:04:47 swordfish kernel: [    0.806889] smpboot cpu 7: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.914506] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.914529] Brought up 8 CPUs
May  9 09:04:47 swordfish kernel: [    0.914531] Total of 8 processors activated (54276.05 BogoMIPS).
May  9 09:04:47 swordfish kernel: [    0.921436] devtmpfs: initialized
May  9 09:04:47 swordfish kernel: [    0.921984] EVM: security.selinux
May  9 09:04:47 swordfish kernel: [    0.921985] EVM: security.SMACK64
May  9 09:04:47 swordfish kernel: [    0.921986] EVM: security.capability
May  9 09:04:47 swordfish kernel: [    0.922001] PM: Registering ACPI NVS region at bad81000 (356352 bytes)
May  9 09:04:47 swordfish kernel: [    0.922005] PM: Registering ACPI NVS region at bae0d000 (53248 bytes)
May  9 09:04:47 swordfish kernel: [    0.922007] PM: Registering ACPI NVS region at bae3c000 (274432 bytes)
May  9 09:04:47 swordfish kernel: [    0.922509] print_constraints: dummy: 
May  9 09:04:47 swordfish kernel: [    0.922537] RTC time: 14:04:26, date: 05/09/12
May  9 09:04:47 swordfish kernel: [    0.922558] NET: Registered protocol family 16
May  9 09:04:47 swordfish kernel: [    0.922623] Trying to unpack rootfs image as initramfs...
May  9 09:04:47 swordfish kernel: [    0.922624] ACPI: bus type pci registered
May  9 09:04:47 swordfish kernel: [    0.922663] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May  9 09:04:47 swordfish kernel: [    0.922665] PCI: not using MMCONFIG
May  9 09:04:47 swordfish kernel: [    0.922666] PCI: Using configuration type 1 for base access
May  9 09:04:47 swordfish kernel: [    0.923248] bio: create slab <bio-0> at 0
May  9 09:04:47 swordfish kernel: [    0.923292] ACPI: Added _OSI(Module Device)
May  9 09:04:47 swordfish kernel: [    0.923293] ACPI: Added _OSI(Processor Device)
May  9 09:04:47 swordfish kernel: [    0.923294] ACPI: Added _OSI(3.0 _SCP Extensions)
May  9 09:04:47 swordfish kernel: [    0.923296] ACPI: Added _OSI(Processor Aggregator Device)
May  9 09:04:47 swordfish kernel: [    0.924080] ACPI: EC: Look up EC in DSDT
May  9 09:04:47 swordfish kernel: [    0.924969] ACPI: Executed 1 blocks of module-level executable AML code
May  9 09:04:47 swordfish kernel: [    0.926679] ACPI: SSDT 00000000bae19898 006F4 (v01    AMI      IST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.926940] ACPI: Dynamic OEM Table Load:
May  9 09:04:47 swordfish kernel: [    0.926942] ACPI: SSDT           (null) 006F4 (v01    AMI      IST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.926964] ACPI: SSDT 00000000bae10d98 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.927163] ACPI: Dynamic OEM Table Load:
May  9 09:04:47 swordfish kernel: [    0.927165] ACPI: SSDT           (null) 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.927689] ACPI: Interpreter enabled
May  9 09:04:47 swordfish kernel: [    0.927691] ACPI: (supports S0 S3 S4 S5)
May  9 09:04:47 swordfish kernel: [    0.927703] ACPI: Using IOAPIC for interrupt routing
May  9 09:04:47 swordfish kernel: [    0.927717] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May  9 09:04:47 swordfish kernel: [    0.927750] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
May  9 09:04:47 swordfish kernel: [    0.966033] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
May  9 09:04:47 swordfish kernel: [    0.968741] ACPI: No dock devices found.
May  9 09:04:47 swordfish kernel: [    0.968742] HEST: Table not found.
May  9 09:04:47 swordfish kernel: [    0.968744] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May  9 09:04:47 swordfish kernel: [    0.968856] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May  9 09:04:47 swordfish kernel: [    0.968978] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    0.968980] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    0.968981] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    0.968983] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
May  9 09:04:47 swordfish kernel: [    0.968984] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    0.968987] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000c8000-0x000dffff] (conflicts with Video ROM [mem 0x000c0000-0x000cd7ff])
May  9 09:04:47 swordfish kernel: [    0.968994] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
May  9 09:04:47 swordfish kernel: [    0.969021] pci 0000:00:02.0: [8086:0102] type 0 class 0x000300
May  9 09:04:47 swordfish kernel: [    0.969029] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
May  9 09:04:47 swordfish kernel: [    0.969034] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.969038] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
May  9 09:04:47 swordfish kernel: [    0.969082] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
May  9 09:04:47 swordfish kernel: [    0.969103] pci 0000:00:16.0: reg 10: [mem 0xfe407000-0xfe40700f 64bit]
May  9 09:04:47 swordfish kernel: [    0.969174] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969178] pci 0000:00:16.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969207] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
May  9 09:04:47 swordfish kernel: [    0.969226] pci 0000:00:1a.0: reg 10: [mem 0xfe406000-0xfe4063ff]
May  9 09:04:47 swordfish kernel: [    0.969311] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969315] pci 0000:00:1a.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969337] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
May  9 09:04:47 swordfish kernel: [    0.969351] pci 0000:00:1b.0: reg 10: [mem 0xfe400000-0xfe403fff 64bit]
May  9 09:04:47 swordfish kernel: [    0.969414] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969417] pci 0000:00:1b.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969437] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.969510] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969514] pci 0000:00:1c.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969535] pci 0000:00:1c.1: [8086:244e] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.969609] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969612] pci 0000:00:1c.1: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969635] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.969709] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969712] pci 0000:00:1c.4: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969741] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
May  9 09:04:47 swordfish kernel: [    0.969761] pci 0000:00:1d.0: reg 10: [mem 0xfe405000-0xfe4053ff]
May  9 09:04:47 swordfish kernel: [    0.969846] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969850] pci 0000:00:1d.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969871] pci 0000:00:1f.0: [8086:1c5c] type 0 class 0x000601
May  9 09:04:47 swordfish kernel: [    0.969986] pci 0000:00:1f.2: [8086:1c00] type 0 class 0x000101
May  9 09:04:47 swordfish kernel: [    0.969999] pci 0000:00:1f.2: reg 10: [io  0xf110-0xf117]
May  9 09:04:47 swordfish kernel: [    0.970006] pci 0000:00:1f.2: reg 14: [io  0xf100-0xf103]
May  9 09:04:47 swordfish kernel: [    0.970014] pci 0000:00:1f.2: reg 18: [io  0xf0f0-0xf0f7]
May  9 09:04:47 swordfish kernel: [    0.970021] pci 0000:00:1f.2: reg 1c: [io  0xf0e0-0xf0e3]
May  9 09:04:47 swordfish kernel: [    0.970028] pci 0000:00:1f.2: reg 20: [io  0xf0d0-0xf0df]
May  9 09:04:47 swordfish kernel: [    0.970035] pci 0000:00:1f.2: reg 24: [io  0xf0c0-0xf0cf]
May  9 09:04:47 swordfish kernel: [    0.970077] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
May  9 09:04:47 swordfish kernel: [    0.970091] pci 0000:00:1f.3: reg 10: [mem 0xfe404000-0xfe4040ff 64bit]
May  9 09:04:47 swordfish kernel: [    0.970110] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
May  9 09:04:47 swordfish kernel: [    0.970140] pci 0000:00:1f.5: [8086:1c08] type 0 class 0x000101
May  9 09:04:47 swordfish kernel: [    0.970154] pci 0000:00:1f.5: reg 10: [io  0xf0b0-0xf0b7]
May  9 09:04:47 swordfish kernel: [    0.970161] pci 0000:00:1f.5: reg 14: [io  0xf0a0-0xf0a3]
May  9 09:04:47 swordfish kernel: [    0.970168] pci 0000:00:1f.5: reg 18: [io  0xf090-0xf097]
May  9 09:04:47 swordfish kernel: [    0.970175] pci 0000:00:1f.5: reg 1c: [io  0xf080-0xf083]
May  9 09:04:47 swordfish kernel: [    0.970182] pci 0000:00:1f.5: reg 20: [io  0xf070-0xf07f]
May  9 09:04:47 swordfish kernel: [    0.970190] pci 0000:00:1f.5: reg 24: [io  0xf060-0xf06f]
May  9 09:04:47 swordfish kernel: [    0.970272] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
May  9 09:04:47 swordfish kernel: [    0.970343] pci 0000:02:00.0: [1283:8893] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.970499] pci 0000:02:00.0: supports D1 D2
May  9 09:04:47 swordfish kernel: [    0.970500] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.970506] pci 0000:02:00.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.970530] pci 0000:00:1c.1: PCI bridge to [bus 02-03] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970540] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970541] pci 0000:00:1c.1:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970543] pci 0000:00:1c.1:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970544] pci 0000:00:1c.1:   bridge window [mem 0xbfa00000-0xffffffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970695] pci 0000:02:00.0: PCI bridge to [bus 03-03] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970721] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970722] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970723] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970725] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970726] pci 0000:02:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970728] pci 0000:02:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970729] pci 0000:02:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970731] pci 0000:02:00.0:   bridge window [mem 0xbfa00000-0xffffffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970806] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
May  9 09:04:47 swordfish kernel: [    0.970825] pci 0000:04:00.0: reg 10: [io  0xe000-0xe0ff]
May  9 09:04:47 swordfish kernel: [    0.970858] pci 0000:04:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.970879] pci 0000:04:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.970968] pci 0000:04:00.0: supports D1 D2
May  9 09:04:47 swordfish kernel: [    0.970969] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.970974] pci 0000:04:00.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.978222] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
May  9 09:04:47 swordfish kernel: [    0.978225] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
May  9 09:04:47 swordfish kernel: [    0.978233] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.978249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  9 09:04:47 swordfish kernel: [    0.978299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
May  9 09:04:47 swordfish kernel: [    0.978315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
May  9 09:04:47 swordfish kernel: [    0.978332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
May  9 09:04:47 swordfish kernel: [    0.978410]  pci0000:00: Requesting ACPI _OSC control (0x1d)
May  9 09:04:47 swordfish kernel: [    0.978534]  pci0000:00: ACPI _OSC control (0x1c) granted
May  9 09:04:47 swordfish kernel: [    0.980437] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980466] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980492] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0
May  9 09:04:47 swordfish kernel: [    0.980519] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980546] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
May  9 09:04:47 swordfish kernel: [    0.980572] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
May  9 09:04:47 swordfish kernel: [    0.980599] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980625] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980692] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
May  9 09:04:47 swordfish kernel: [    0.980696] vgaarb: loaded
May  9 09:04:47 swordfish kernel: [    0.980697] vgaarb: bridge control possible 0000:00:02.0
May  9 09:04:47 swordfish kernel: [    0.980753] i2c-core: driver [aat2870] using legacy suspend method
May  9 09:04:47 swordfish kernel: [    0.980754] i2c-core: driver [aat2870] using legacy resume method
May  9 09:04:47 swordfish kernel: [    0.980791] SCSI subsystem initialized
May  9 09:04:47 swordfish kernel: [    0.980824] libata version 3.00 loaded.
May  9 09:04:47 swordfish kernel: [    0.980850] usbcore: registered new interface driver usbfs
May  9 09:04:47 swordfish kernel: [    0.980856] usbcore: registered new interface driver hub
May  9 09:04:47 swordfish kernel: [    0.980868] usbcore: registered new device driver usb
May  9 09:04:47 swordfish kernel: [    0.980913] PCI: Using ACPI for IRQ routing
May  9 09:04:47 swordfish kernel: [    0.987031] PCI: pci_cache_line_size set to 64 bytes
May  9 09:04:47 swordfish kernel: [    0.987085] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
May  9 09:04:47 swordfish kernel: [    0.987086] reserve RAM buffer: 00000000bad81000 - 00000000bbffffff 
May  9 09:04:47 swordfish kernel: [    0.987088] reserve RAM buffer: 00000000badfd000 - 00000000bbffffff 
May  9 09:04:47 swordfish kernel: [    0.987090] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
May  9 09:04:47 swordfish kernel: [    0.987091] reserve RAM buffer: 000000023fe00000 - 000000023fffffff 
May  9 09:04:47 swordfish kernel: [    0.987150] NetLabel: Initializing
May  9 09:04:47 swordfish kernel: [    0.987151] NetLabel:  domain hash size = 128
May  9 09:04:47 swordfish kernel: [    0.987152] NetLabel:  protocols = UNLABELED CIPSOv4
May  9 09:04:47 swordfish kernel: [    0.987158] NetLabel:  unlabeled traffic allowed by default
May  9 09:04:47 swordfish kernel: [    0.987187] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
May  9 09:04:47 swordfish kernel: [    0.987191] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
May  9 09:04:47 swordfish kernel: [    0.989196] Switching to clocksource hpet
May  9 09:04:47 swordfish kernel: [    0.992994] AppArmor: AppArmor Filesystem Enabled
May  9 09:04:47 swordfish kernel: [    0.993008] pnp: PnP ACPI init
May  9 09:04:47 swordfish kernel: [    0.993016] ACPI: bus type pnp registered
May  9 09:04:47 swordfish kernel: [    0.993107] pnp 00:00: [bus 00-ff]
May  9 09:04:47 swordfish kernel: [    0.993108] pnp 00:00: [io  0x0cf8-0x0cff]
May  9 09:04:47 swordfish kernel: [    0.993110] pnp 00:00: [io  0x0000-0x0cf7 window]
May  9 09:04:47 swordfish kernel: [    0.993111] pnp 00:00: [io  0x0d00-0xffff window]
May  9 09:04:47 swordfish kernel: [    0.993112] pnp 00:00: [mem 0x000a0000-0x000bffff window]
May  9 09:04:47 swordfish kernel: [    0.993113] pnp 00:00: [mem 0x000c8000-0x000dffff window]
May  9 09:04:47 swordfish kernel: [    0.993115] pnp 00:00: [mem 0xbfa00000-0xffffffff window]
May  9 09:04:47 swordfish kernel: [    0.993116] pnp 00:00: [mem 0x00000000 window]
May  9 09:04:47 swordfish kernel: [    0.993157] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
May  9 09:04:47 swordfish kernel: [    0.993189] pnp 00:01: [mem 0xfed10000-0xfed19fff]
May  9 09:04:47 swordfish kernel: [    0.993192] pnp 00:01: [mem 0xe0000000-0xefffffff]
May  9 09:04:47 swordfish kernel: [    0.993193] pnp 00:01: [mem 0xfed90000-0xfed93fff]
May  9 09:04:47 swordfish kernel: [    0.993194] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
May  9 09:04:47 swordfish kernel: [    0.993195] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
May  9 09:04:47 swordfish kernel: [    0.993221] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993222] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993224] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993225] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993227] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993229] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
May  9 09:04:47 swordfish kernel: [    0.993295] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
May  9 09:04:47 swordfish kernel: [    0.993296] pnp 00:02: [io  0x0a20-0x0a3f]
May  9 09:04:47 swordfish kernel: [    0.993297] pnp 00:02: [io  0x0a30-0x0a3f]
May  9 09:04:47 swordfish kernel: [    0.993298] pnp 00:02: [io  0x0a20-0x0a2f]
May  9 09:04:47 swordfish kernel: [    0.993317] system 00:02: [io  0x0a20-0x0a3f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993319] system 00:02: [io  0x0a30-0x0a3f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993320] system 00:02: [io  0x0a20-0x0a2f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993322] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
May  9 09:04:47 swordfish kernel: [    0.993348] pnp 00:03: [io  0x0060]
May  9 09:04:47 swordfish kernel: [    0.993349] pnp 00:03: [io  0x0064]
May  9 09:04:47 swordfish kernel: [    0.993357] pnp 00:03: [irq 12]
May  9 09:04:47 swordfish kernel: [    0.993373] pnp 00:03: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
May  9 09:04:47 swordfish kernel: [    0.993542] pnp 00:04: [io  0x03f8-0x03ff]
May  9 09:04:47 swordfish kernel: [    0.993546] pnp 00:04: [irq 4]
May  9 09:04:47 swordfish kernel: [    0.993547] pnp 00:04: [dma 0 disabled]
May  9 09:04:47 swordfish kernel: [    0.993583] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
May  9 09:04:47 swordfish kernel: [    0.993589] pnp 00:05: [dma 4]
May  9 09:04:47 swordfish kernel: [    0.993590] pnp 00:05: [io  0x0000-0x000f]
May  9 09:04:47 swordfish kernel: [    0.993591] pnp 00:05: [io  0x0081-0x0083]
May  9 09:04:47 swordfish kernel: [    0.993592] pnp 00:05: [io  0x0087]
May  9 09:04:47 swordfish kernel: [    0.993593] pnp 00:05: [io  0x0089-0x008b]
May  9 09:04:47 swordfish kernel: [    0.993594] pnp 00:05: [io  0x008f]
May  9 09:04:47 swordfish kernel: [    0.993595] pnp 00:05: [io  0x00c0-0x00df]
May  9 09:04:47 swordfish kernel: [    0.993609] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
May  9 09:04:47 swordfish kernel: [    0.993614] pnp 00:06: [io  0x0070-0x0071]
May  9 09:04:47 swordfish kernel: [    0.993618] pnp 00:06: [irq 8]
May  9 09:04:47 swordfish kernel: [    0.993631] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
May  9 09:04:47 swordfish kernel: [    0.993635] pnp 00:07: [io  0x0061]
May  9 09:04:47 swordfish kernel: [    0.993646] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
May  9 09:04:47 swordfish kernel: [    0.993655] pnp 00:08: [io  0x0010-0x001f]
May  9 09:04:47 swordfish kernel: [    0.993656] pnp 00:08: [io  0x0022-0x003f]
May  9 09:04:47 swordfish kernel: [    0.993657] pnp 00:08: [io  0x0044-0x005f]
May  9 09:04:47 swordfish kernel: [    0.993659] pnp 00:08: [io  0x0062-0x0063]
May  9 09:04:47 swordfish kernel: [    0.993660] pnp 00:08: [io  0x0065-0x006f]
May  9 09:04:47 swordfish kernel: [    0.993661] pnp 00:08: [io  0x0072-0x007f]
May  9 09:04:47 swordfish kernel: [    0.993662] pnp 00:08: [io  0x0080]
May  9 09:04:47 swordfish kernel: [    0.993663] pnp 00:08: [io  0x0084-0x0086]
May  9 09:04:47 swordfish kernel: [    0.993664] pnp 00:08: [io  0x0088]
May  9 09:04:47 swordfish kernel: [    0.993665] pnp 00:08: [io  0x008c-0x008e]
May  9 09:04:47 swordfish kernel: [    0.993666] pnp 00:08: [io  0x0090-0x009f]
May  9 09:04:47 swordfish kernel: [    0.993667] pnp 00:08: [io  0x00a2-0x00bf]
May  9 09:04:47 swordfish kernel: [    0.993668] pnp 00:08: [io  0x00e0-0x00ef]
May  9 09:04:47 swordfish kernel: [    0.993669] pnp 00:08: [io  0x04d0-0x04d1]
May  9 09:04:47 swordfish kernel: [    0.993693] system 00:08: [io  0x04d0-0x04d1] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993695] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
May  9 09:04:47 swordfish kernel: [    0.993699] pnp 00:09: [io  0x00f0-0x00ff]
May  9 09:04:47 swordfish kernel: [    0.993703] pnp 00:09: [irq 13]
May  9 09:04:47 swordfish kernel: [    0.993717] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
May  9 09:04:47 swordfish kernel: [    0.993810] pnp 00:0a: [io  0x0400-0x0453]
May  9 09:04:47 swordfish kernel: [    0.993811] pnp 00:0a: [io  0x0458-0x047f]
May  9 09:04:47 swordfish kernel: [    0.993812] pnp 00:0a: [io  0x1180-0x119f]
May  9 09:04:47 swordfish kernel: [    0.993813] pnp 00:0a: [io  0x0500-0x057f]
May  9 09:04:47 swordfish kernel: [    0.993815] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
May  9 09:04:47 swordfish kernel: [    0.993816] pnp 00:0a: [mem 0xfec00000-0xfecfffff]
May  9 09:04:47 swordfish kernel: [    0.993817] pnp 00:0a: [mem 0xfed08000-0xfed08fff]
May  9 09:04:47 swordfish kernel: [    0.993818] pnp 00:0a: [mem 0xff000000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    0.993839] system 00:0a: [io  0x0400-0x0453] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993840] system 00:0a: [io  0x0458-0x047f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993842] system 00:0a: [io  0x1180-0x119f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993843] system 00:0a: [io  0x0500-0x057f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993845] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993847] system 00:0a: [mem 0xfec00000-0xfecfffff] could not be reserved
May  9 09:04:47 swordfish kernel: [    0.993848] system 00:0a: [mem 0xfed08000-0xfed08fff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993850] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993851] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
May  9 09:04:47 swordfish kernel: [    0.993871] pnp 00:0b: [io  0x0454-0x0457]
May  9 09:04:47 swordfish kernel: [    0.993889] system 00:0b: [io  0x0454-0x0457] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993891] system 00:0b: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
May  9 09:04:47 swordfish kernel: [    0.993949] pnp 00:0c: [mem 0xfed00000-0xfed003ff]
May  9 09:04:47 swordfish kernel: [    0.993969] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
May  9 09:04:47 swordfish kernel: [    0.994062] pnp: PnP ACPI: found 13 devices
May  9 09:04:47 swordfish kernel: [    0.994063] ACPI: ACPI bus type pnp unregistered
May  9 09:04:47 swordfish kernel: [    0.999897] PCI: max bus depth: 2 pci_try_num: 3
May  9 09:04:47 swordfish kernel: [    0.999936] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
May  9 09:04:47 swordfish kernel: [    0.999947] pci 0000:02:00.0: PCI bridge to [bus 03-03]
May  9 09:04:47 swordfish kernel: [    0.999969] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
May  9 09:04:47 swordfish kernel: [    0.999980] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
May  9 09:04:47 swordfish kernel: [    0.999983] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
May  9 09:04:47 swordfish kernel: [    0.999989] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    1.000005] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  9 09:04:47 swordfish kernel: [    1.000009] pci 0000:00:1c.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000018] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    1.000021] pci 0000:00:1c.1: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000030] pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  9 09:04:47 swordfish kernel: [    1.000037] pci 0000:02:00.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000044] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  9 09:04:47 swordfish kernel: [    1.000048] pci 0000:00:1c.4: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000051] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    1.000052] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    1.000054] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    1.000055] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    1.000057] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    1.000058] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    1.000059] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    1.000061] pci_bus 0000:02: resource 7 [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    1.000062] pci_bus 0000:03: resource 8 [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    1.000063] pci_bus 0000:03: resource 9 [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    1.000065] pci_bus 0000:03: resource 10 [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    1.000066] pci_bus 0000:03: resource 11 [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    1.000067] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
May  9 09:04:47 swordfish kernel: [    1.000069] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    1.000087] NET: Registered protocol family 2
May  9 09:04:47 swordfish kernel: [    1.000237] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  9 09:04:47 swordfish kernel: [    1.000868] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May  9 09:04:47 swordfish kernel: [    1.001854] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May  9 09:04:47 swordfish kernel: [    1.001971] TCP: Hash tables configured (established 524288 bind 65536)
May  9 09:04:47 swordfish kernel: [    1.001973] TCP reno registered
May  9 09:04:47 swordfish kernel: [    1.001983] UDP hash table entries: 4096 (order: 5, 131072 bytes)
May  9 09:04:47 swordfish kernel: [    1.002007] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
May  9 09:04:47 swordfish kernel: [    1.002070] NET: Registered protocol family 1
May  9 09:04:47 swordfish kernel: [    1.002080] pci 0000:00:02.0: Boot video device
May  9 09:04:47 swordfish kernel: [    1.002092] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    1.128904] pci 0000:00:1a.0: PCI INT A disabled
May  9 09:04:47 swordfish kernel: [    1.128927] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  9 09:04:47 swordfish kernel: [    1.256539] pci 0000:00:1d.0: PCI INT A disabled
May  9 09:04:47 swordfish kernel: [    1.256558] PCI: CLS 64 bytes, default 64
May  9 09:04:47 swordfish kernel: [    1.256560] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
May  9 09:04:47 swordfish kernel: [    1.256561] Placing 64MB software IO TLB between ffff8800b6d81000 - ffff8800bad81000
May  9 09:04:47 swordfish kernel: [    1.256563] software IO TLB at phys 0xb6d81000 - 0xbad81000
May  9 09:04:47 swordfish kernel: [    1.256976] audit: initializing netlink socket (disabled)
May  9 09:04:47 swordfish kernel: [    1.256983] type=2000 audit(1336572266.036:1): initialized
May  9 09:04:47 swordfish kernel: [    1.280532] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  9 09:04:47 swordfish kernel: [    1.297780] VFS: Disk quotas dquot_6.5.2
May  9 09:04:47 swordfish kernel: [    1.297812] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  9 09:04:47 swordfish kernel: [    1.298094] fuse init (API version 7.17)
May  9 09:04:47 swordfish kernel: [    1.298145] msgmni has been set to 15764
May  9 09:04:47 swordfish kernel: [    1.298383] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May  9 09:04:47 swordfish kernel: [    1.298402] io scheduler noop registered
May  9 09:04:47 swordfish kernel: [    1.298403] io scheduler deadline registered
May  9 09:04:47 swordfish kernel: [    1.298419] io scheduler cfq registered (default)
May  9 09:04:47 swordfish kernel: [    1.298482] pcieport 0000:00:1c.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.298524] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [    1.298582] pcieport 0000:00:1c.4: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.298619] pcieport 0000:00:1c.4: irq 41 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [    1.298688] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
May  9 09:04:47 swordfish kernel: [    1.298692] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
May  9 09:04:47 swordfish kernel: [    1.298707] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
May  9 09:04:47 swordfish kernel: [    1.298708] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
May  9 09:04:47 swordfish kernel: [    1.298712] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
May  9 09:04:47 swordfish kernel: [    1.298721] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  9 09:04:47 swordfish kernel: [    1.298734] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  9 09:04:47 swordfish kernel: [    1.298762] intel_idle: MWAIT substates: 0x1120
May  9 09:04:47 swordfish kernel: [    1.298763] intel_idle: v0.4 model 0x2A
May  9 09:04:47 swordfish kernel: [    1.298764] intel_idle: lapic_timer_reliable_states 0xffffffff
May  9 09:04:47 swordfish kernel: [    1.298829] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May  9 09:04:47 swordfish kernel: [    1.298833] ACPI: Power Button [PWRB]
May  9 09:04:47 swordfish kernel: [    1.298856] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  9 09:04:47 swordfish kernel: [    1.298858] ACPI: Power Button [PWRF]
May  9 09:04:47 swordfish kernel: [    1.301286] ERST: Table is not found!
May  9 09:04:47 swordfish kernel: [    1.301288] GHES: HEST is not enabled!
May  9 09:04:47 swordfish kernel: [    1.301327] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May  9 09:04:47 swordfish kernel: [    1.321678] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 09:04:47 swordfish kernel: [    1.321769] Freeing initrd memory: 13840k freed
May  9 09:04:47 swordfish kernel: [    1.548374] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 09:04:47 swordfish kernel: [    1.595765] Linux agpgart interface v0.103
May  9 09:04:47 swordfish kernel: [    1.595808] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
May  9 09:04:47 swordfish kernel: [    1.595901] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
May  9 09:04:47 swordfish kernel: [    1.597196] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
May  9 09:04:47 swordfish kernel: [    1.597288] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
May  9 09:04:47 swordfish kernel: [    1.598095] brd: module loaded
May  9 09:04:47 swordfish kernel: [    1.598508] loop: module loaded
May  9 09:04:47 swordfish kernel: [    1.598597] ata_piix 0000:00:1f.2: version 2.13
May  9 09:04:47 swordfish kernel: [    1.598612] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  9 09:04:47 swordfish kernel: [    1.598617] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
May  9 09:04:47 swordfish kernel: [    1.751133] ata_piix 0000:00:1f.2: SCR access via SIDPR is available but doesn't work
May  9 09:04:47 swordfish kernel: [    1.751145] ata_piix 0000:00:1f.2: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.751339] scsi0 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.751385] scsi1 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.751874] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf0d0 irq 14
May  9 09:04:47 swordfish kernel: [    1.751876] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf0d8 irq 15
May  9 09:04:47 swordfish kernel: [    1.751888] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  9 09:04:47 swordfish kernel: [    1.751893] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
May  9 09:04:47 swordfish kernel: [    1.751927] ata_piix 0000:00:1f.5: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.752050] scsi2 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.752089] scsi3 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.752623] ata3: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf070 irq 19
May  9 09:04:47 swordfish kernel: [    1.752626] ata4: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf078 irq 19
May  9 09:04:47 swordfish kernel: [    1.752796] Fixed MDIO Bus: probed
May  9 09:04:47 swordfish kernel: [    1.752808] tun: Universal TUN/TAP device driver, 1.6
May  9 09:04:47 swordfish kernel: [    1.752809] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  9 09:04:47 swordfish kernel: [    1.752836] PPP generic driver version 2.4.2
May  9 09:04:47 swordfish kernel: [    1.752894] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  9 09:04:47 swordfish kernel: [    1.752905] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    1.752918] ehci_hcd 0000:00:1a.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.752920] ehci_hcd 0000:00:1a.0: EHCI Host Controller
May  9 09:04:47 swordfish kernel: [    1.752944] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
May  9 09:04:47 swordfish kernel: [    1.752965] ehci_hcd 0000:00:1a.0: debug port 2
May  9 09:04:47 swordfish kernel: [    1.756853] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
May  9 09:04:47 swordfish kernel: [    1.756863] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe406000
May  9 09:04:47 swordfish kernel: [    1.771063] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
May  9 09:04:47 swordfish kernel: [    1.771174] hub 1-0:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    1.771177] hub 1-0:1.0: 2 ports detected
May  9 09:04:47 swordfish kernel: [    1.771214] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  9 09:04:47 swordfish kernel: [    1.771223] ehci_hcd 0000:00:1d.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.771226] ehci_hcd 0000:00:1d.0: EHCI Host Controller
May  9 09:04:47 swordfish kernel: [    1.771255] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May  9 09:04:47 swordfish kernel: [    1.771272] ehci_hcd 0000:00:1d.0: debug port 2
May  9 09:04:47 swordfish kernel: [    1.775141] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
May  9 09:04:47 swordfish kernel: [    1.775150] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe405000
May  9 09:04:47 swordfish kernel: [    1.791006] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
May  9 09:04:47 swordfish kernel: [    1.791111] hub 2-0:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    1.791113] hub 2-0:1.0: 2 ports detected
May  9 09:04:47 swordfish kernel: [    1.791145] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  9 09:04:47 swordfish kernel: [    1.791150] uhci_hcd: USB Universal Host Controller Interface driver
May  9 09:04:47 swordfish kernel: [    1.791174] usbcore: registered new interface driver libusual
May  9 09:04:47 swordfish kernel: [    1.791195] i8042: PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
May  9 09:04:47 swordfish kernel: [    1.791196] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
May  9 09:04:47 swordfish kernel: [    1.791571] serio: i8042 KBD port at 0x60,0x64 irq 1
May  9 09:04:47 swordfish kernel: [    1.791575] serio: i8042 AUX port at 0x60,0x64 irq 12
May  9 09:04:47 swordfish kernel: [    1.791645] mousedev: PS/2 mouse device common for all mice
May  9 09:04:47 swordfish kernel: [    1.791732] rtc_cmos 00:06: RTC can wake from S4
May  9 09:04:47 swordfish kernel: [    1.791815] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
May  9 09:04:47 swordfish kernel: [    1.791840] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May  9 09:04:47 swordfish kernel: [    1.791882] device-mapper: uevent: version 1.0.3
May  9 09:04:47 swordfish kernel: [    1.791921] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
May  9 09:04:47 swordfish kernel: [    1.792026] cpuidle: using governor ladder
May  9 09:04:47 swordfish kernel: [    1.792189] cpuidle: using governor menu
May  9 09:04:47 swordfish kernel: [    1.792190] EFI Variables Facility v0.08 2004-May-17
May  9 09:04:47 swordfish kernel: [    1.792300] TCP cubic registered
May  9 09:04:47 swordfish kernel: [    1.792354] NET: Registered protocol family 10
May  9 09:04:47 swordfish kernel: [    1.792584] NET: Registered protocol family 17
May  9 09:04:47 swordfish kernel: [    1.792591] Registering the dns_resolver key type
May  9 09:04:47 swordfish kernel: [    1.792672] PM: Hibernation image not present or could not be loaded.
May  9 09:04:47 swordfish kernel: [    1.792679] registered taskstats version 1
May  9 09:04:47 swordfish kernel: [    1.805133]   Magic number: 12:665:80
May  9 09:04:47 swordfish kernel: [    1.805245] rtc_cmos 00:06: setting system clock to 2012-05-09 14:04:27 UTC (1336572267)
May  9 09:04:47 swordfish kernel: [    1.806272] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  9 09:04:47 swordfish kernel: [    1.806273] EDD information not available.
May  9 09:04:47 swordfish kernel: [    2.082193] usb 1-1: new high-speed USB device number 2 using ehci_hcd
May  9 09:04:47 swordfish kernel: [    2.214694] hub 1-1:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    2.214897] hub 1-1:1.0: 4 ports detected
May  9 09:04:47 swordfish kernel: [    2.225821] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  9 09:04:47 swordfish kernel: [    2.225949] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  9 09:04:47 swordfish kernel: [    2.233989] ata3.00: ATAPI: HL-DT-ST DVDRAM GH24NS70, GN00, max UDMA/100
May  9 09:04:47 swordfish kernel: [    2.234271] ata4.00: ATA-8: WDC WD10EADX-22TDHB0, 77.04D77, max UDMA/133
May  9 09:04:47 swordfish kernel: [    2.234274] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  9 09:04:47 swordfish kernel: [    2.242157] ata4.00: configured for UDMA/133
May  9 09:04:47 swordfish kernel: [    2.249925] ata3.00: configured for UDMA/100
May  9 09:04:47 swordfish kernel: [    2.253699] Refined TSC clocksource calibration: 3392.295 MHz.
May  9 09:04:47 swordfish kernel: [    2.253705] Switching to clocksource tsc
May  9 09:04:47 swordfish kernel: [    2.258404] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS70  GN00 PQ: 0 ANSI: 5
May  9 09:04:47 swordfish kernel: [    2.267027] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  9 09:04:47 swordfish kernel: [    2.267032] cdrom: Uniform CD-ROM driver Revision: 3.20
May  9 09:04:47 swordfish kernel: [    2.267205] sr 2:0:0:0: Attached scsi CD-ROM sr0
May  9 09:04:47 swordfish kernel: [    2.267289] sr 2:0:0:0: Attached scsi generic sg0 type 5
May  9 09:04:47 swordfish kernel: [    2.267604] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EADX-22T 77.0 PQ: 0 ANSI: 5
May  9 09:04:47 swordfish kernel: [    2.267803] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
May  9 09:04:47 swordfish kernel: [    2.267812] sd 3:0:0:0: Attached scsi generic sg1 type 0
May  9 09:04:47 swordfish kernel: [    2.268102] sd 3:0:0:0: [sda] Write Protect is off
May  9 09:04:47 swordfish kernel: [    2.268105] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  9 09:04:47 swordfish kernel: [    2.268198] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 09:04:47 swordfish kernel: [    2.298537]  sda: sda1 sda2 < sda5 >
May  9 09:04:47 swordfish kernel: [    2.299524] sd 3:0:0:0: [sda] Attached SCSI disk
May  9 09:04:47 swordfish kernel: [    2.300506] Freeing unused kernel memory: 920k freed
May  9 09:04:47 swordfish kernel: [    2.300574] Write protecting the kernel read-only data: 12288k
May  9 09:04:47 swordfish kernel: [    2.303700] Freeing unused kernel memory: 1608k freed
May  9 09:04:47 swordfish kernel: [    2.306077] Freeing unused kernel memory: 1196k freed
May  9 09:04:47 swordfish kernel: [    2.325490] usb 2-1: new high-speed USB device number 2 using ehci_hcd
May  9 09:04:47 swordfish kernel: [    2.326664] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  9 09:04:47 swordfish kernel: [    2.326683] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    2.326713] r8169 0000:04:00.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    2.326780] r8169 0000:04:00.0: irq 42 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [    2.327100] r8169 0000:04:00.0: eth0: RTL8105e at 0xffffc90000c74000, 10:78:d2:21:83:6b, XID 00a00000 IRQ 42
May  9 09:04:47 swordfish kernel: [    2.461680] hub 2-1:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    2.461765] hub 2-1:1.0: 6 ports detected
May  9 09:04:47 swordfish kernel: [    2.511319] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
May  9 09:04:47 swordfish kernel: [    2.511321] EXT4-fs (sda1): write access will be enabled during recovery
May  9 09:04:47 swordfish kernel: [    2.732507] usb 2-1.6: new low-speed USB device number 3 using ehci_hcd
May  9 09:04:47 swordfish kernel: [    2.834130] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input2
May  9 09:04:47 swordfish kernel: [    2.834242] generic-usb 0003:03F0:0F0C.0001: input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.0-1.6/input0
May  9 09:04:47 swordfish kernel: [    2.840004] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input3
May  9 09:04:47 swordfish kernel: [    2.840298] generic-usb 0003:03F0:0F0C.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.0-1.6/input1
May  9 09:04:47 swordfish kernel: [    2.840308] usbcore: registered new interface driver usbhid
May  9 09:04:47 swordfish kernel: [    2.840309] usbhid: USB HID core driver
May  9 09:04:47 swordfish kernel: [    5.840405] EXT4-fs (sda1): orphan cleanup on readonly fs
May  9 09:04:47 swordfish kernel: [    5.840411] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314426
May  9 09:04:47 swordfish kernel: [    5.840447] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314192
May  9 09:04:47 swordfish kernel: [    5.840454] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314329
May  9 09:04:47 swordfish kernel: [    5.840458] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314319
May  9 09:04:47 swordfish kernel: [    5.840464] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55318181
May  9 09:04:47 swordfish kernel: [    5.840480] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315569
May  9 09:04:47 swordfish kernel: [    5.840501] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 26083479
May  9 09:04:47 swordfish kernel: [    5.877241] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101511
May  9 09:04:47 swordfish kernel: [    5.877275] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101510
May  9 09:04:47 swordfish kernel: [    5.877296] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101507
May  9 09:04:47 swordfish kernel: [    5.877319] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101506
May  9 09:04:47 swordfish kernel: [    5.877326] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101503
May  9 09:04:47 swordfish kernel: [    5.877332] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101502
May  9 09:04:47 swordfish kernel: [    5.877338] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101499
May  9 09:04:47 swordfish kernel: [    5.877344] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101498
May  9 09:04:47 swordfish kernel: [    5.877351] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101495
May  9 09:04:47 swordfish kernel: [    5.877356] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101492
May  9 09:04:47 swordfish kernel: [    5.877363] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316519
May  9 09:04:47 swordfish kernel: [    5.891354] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316511
May  9 09:04:47 swordfish kernel: [    5.918796] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389461
May  9 09:04:47 swordfish kernel: [    5.918833] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389460
May  9 09:04:47 swordfish kernel: [    5.918840] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389459
May  9 09:04:47 swordfish kernel: [    5.918843] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389458
May  9 09:04:47 swordfish kernel: [    5.918849] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389457
May  9 09:04:47 swordfish kernel: [    5.918855] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101487
May  9 09:04:47 swordfish kernel: [    5.930694] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101484
May  9 09:04:47 swordfish kernel: [    5.930718] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101479
May  9 09:04:47 swordfish kernel: [    5.930738] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101475
May  9 09:04:47 swordfish kernel: [    5.930744] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101474
May  9 09:04:47 swordfish kernel: [    5.931795] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099200
May  9 09:04:47 swordfish kernel: [    5.931834] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099199
May  9 09:04:47 swordfish kernel: [    5.931840] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099198
May  9 09:04:47 swordfish kernel: [    5.931848] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099196
May  9 09:04:47 swordfish kernel: [    5.931854] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099195
May  9 09:04:47 swordfish kernel: [    5.931860] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099194
May  9 09:04:47 swordfish kernel: [    5.931866] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099193
May  9 09:04:47 swordfish kernel: [    5.931872] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099192
May  9 09:04:47 swordfish kernel: [    5.931878] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099191
May  9 09:04:47 swordfish kernel: [    5.931884] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099190
May  9 09:04:47 swordfish kernel: [    5.931890] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099189
May  9 09:04:47 swordfish kernel: [    5.931896] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099188
May  9 09:04:47 swordfish kernel: [    5.931906] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099187
May  9 09:04:47 swordfish kernel: [    5.931913] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099186
May  9 09:04:47 swordfish kernel: [    5.931919] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099182
May  9 09:04:47 swordfish kernel: [    5.945716] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313639
May  9 09:04:47 swordfish kernel: [    5.945744] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316509
May  9 09:04:47 swordfish kernel: [    5.945750] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316510
May  9 09:04:47 swordfish kernel: [    5.945756] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316508
May  9 09:04:47 swordfish kernel: [    5.945762] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316507
May  9 09:04:47 swordfish kernel: [    5.953968] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315568
May  9 09:04:47 swordfish kernel: [    5.953994] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315562
May  9 09:04:47 swordfish kernel: [    5.954000] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315630
May  9 09:04:47 swordfish kernel: [    5.976827] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953723
May  9 09:04:47 swordfish kernel: [    5.976862] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953722
May  9 09:04:47 swordfish kernel: [    5.976868] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953600
May  9 09:04:47 swordfish kernel: [    5.976875] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953579
May  9 09:04:47 swordfish kernel: [    5.976882] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953564
May  9 09:04:47 swordfish kernel: [    5.976891] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953537
May  9 09:04:47 swordfish kernel: [    5.976897] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953444
May  9 09:04:47 swordfish kernel: [    5.976904] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953426
May  9 09:04:47 swordfish kernel: [    5.976911] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953298
May  9 09:04:47 swordfish kernel: [    5.976917] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953265
May  9 09:04:47 swordfish kernel: [    5.976933] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953257
May  9 09:04:47 swordfish kernel: [    5.976939] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25952961
May  9 09:04:47 swordfish kernel: [    5.977775] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314165
May  9 09:04:47 swordfish kernel: [    5.977814] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313646
May  9 09:04:47 swordfish kernel: [    5.977820] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315555
May  9 09:04:47 swordfish kernel: [    5.977826] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315483
May  9 09:04:47 swordfish kernel: [    5.977833] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315622
May  9 09:04:47 swordfish kernel: [    6.287768] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55318292
May  9 09:04:47 swordfish kernel: [    6.287812] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55318281
May  9 09:04:47 swordfish kernel: [    6.287820] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315621
May  9 09:04:47 swordfish kernel: [    6.287826] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315620
May  9 09:04:47 swordfish kernel: [    6.287832] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313700
May  9 09:04:47 swordfish kernel: [    6.287839] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315544
May  9 09:04:47 swordfish kernel: [    6.295099] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314893
May  9 09:04:47 swordfish kernel: [    6.295138] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313955
May  9 09:04:47 swordfish kernel: [    6.295145] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315571
May  9 09:04:47 swordfish kernel: [    6.296969] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315438
May  9 09:04:47 swordfish kernel: [    6.297001] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315291
May  9 09:04:47 swordfish kernel: [    6.297018] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313988
May  9 09:04:47 swordfish kernel: [    6.297040] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313522
May  9 09:04:47 swordfish kernel: [    6.297047] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314197
May  9 09:04:47 swordfish kernel: [    6.297053] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315545
May  9 09:04:47 swordfish kernel: [    6.297059] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314849
May  9 09:04:47 swordfish kernel: [    6.297066] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313985
May  9 09:04:47 swordfish kernel: [    6.297072] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313647
May  9 09:04:47 swordfish kernel: [    6.297078] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314922
May  9 09:04:47 swordfish kernel: [    6.297084] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314169
May  9 09:04:47 swordfish kernel: [    6.297090] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389449
May  9 09:04:47 swordfish kernel: [    6.297096] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389448
May  9 09:04:47 swordfish kernel: [    6.297102] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389447
May  9 09:04:47 swordfish kernel: [    6.297110] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313818
May  9 09:04:47 swordfish kernel: [    6.297117] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313811
May  9 09:04:47 swordfish kernel: [    6.297123] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314894
May  9 09:04:47 swordfish kernel: [    6.297128] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313742
May  9 09:04:47 swordfish kernel: [    6.314572] EXT4-fs (sda1): 96 orphan inodes deleted
May  9 09:04:47 swordfish kernel: [    6.314576] EXT4-fs (sda1): recovery complete
May  9 09:04:47 swordfish kernel: [    6.920821] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
May  9 09:04:47 swordfish kernel: [   21.529105] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 09:04:47 swordfish kernel: [   21.595280] lp: driver loaded but no devices found
May  9 09:04:47 swordfish kernel: [   21.596613] [drm] Initialized drm 1.1.0 20060810
May  9 09:04:47 swordfish kernel: [   21.598466] it87: Found IT8721F chip at 0xa30, revision 1
May  9 09:04:47 swordfish kernel: [   21.598504] ACPI: resource it87 [io  0x0a35-0x0a36] conflicts with ACPI region ECIO [io 0xa30-0xb2f]
May  9 09:04:47 swordfish kernel: [   21.598505] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May  9 09:04:47 swordfish kernel: [   21.599945] mei: module is from the staging directory, the quality is unknown, you have been warned.
May  9 09:04:47 swordfish kernel: [   21.600181] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [   21.600188] mei 0000:00:16.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [   21.600239] mei 0000:00:16.0: irq 43 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [   21.602023] wmi: Mapper loaded
May  9 09:04:47 swordfish kernel: [   21.607482] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [   21.607487] i915 0000:00:02.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [   21.623486] Adding 8297468k swap on /dev/sda5.  Priority:-1 extents:1 across:8297468k 
May  9 09:04:47 swordfish kernel: [   21.634011] type=1400 audit(1336572287.381:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=419 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634017] type=1400 audit(1336572287.381:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634226] type=1400 audit(1336572287.381:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=419 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634234] type=1400 audit(1336572287.381:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634375] type=1400 audit(1336572287.385:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=419 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634383] type=1400 audit(1336572287.385:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.656083] i915 0000:00:02.0: irq 44 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [   21.656087] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
May  9 09:04:47 swordfish kernel: [   21.656088] [drm] Driver supports precise vblank timestamp query.
May  9 09:04:47 swordfish kernel: [   21.656108] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
May  9 09:04:47 swordfish kernel: [   21.668286] it87: Found IT8721F chip at 0xa30, revision 1
May  9 09:04:47 swordfish kernel: [   21.668319] ACPI: resource it87 [io  0x0a35-0x0a36] conflicts with ACPI region ECIO [io 0xa30-0xb2f]
May  9 09:04:47 swordfish kernel: [   21.668320] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May  9 09:04:47 swordfish kernel: [   21.936107] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  9 09:04:47 swordfish kernel: [   21.962827] fbcon: inteldrmfb (fb0) is primary device
May  9 09:04:47 swordfish kernel: [   21.962892] Console: switching to colour frame buffer device 210x65
May  9 09:04:47 swordfish kernel: [   21.962917] fb0: inteldrmfb frame buffer device
May  9 09:04:47 swordfish kernel: [   21.962918] drm: registered panic notifier
May  9 09:04:47 swordfish kernel: [   21.962925] No ACPI video bus found
May  9 09:04:47 swordfish kernel: [   21.962974] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
May  9 09:04:47 swordfish kernel: [   21.963015] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May  9 09:04:47 swordfish kernel: [   21.963091] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [   21.963113] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [   22.014672] init: failsafe main process (762) killed by TERM signal
May  9 09:04:47 swordfish kernel: [   22.026891] Bluetooth: Core ver 2.16
May  9 09:04:47 swordfish kernel: [   22.026903] NET: Registered protocol family 31
May  9 09:04:47 swordfish kernel: [   22.026904] Bluetooth: HCI device and connection manager initialized
May  9 09:04:47 swordfish kernel: [   22.026905] Bluetooth: HCI socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.026906] Bluetooth: L2CAP socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.026909] Bluetooth: SCO socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.027838] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  9 09:04:47 swordfish kernel: [   22.027839] Bluetooth: BNEP filters: protocol multicast
May  9 09:04:47 swordfish kernel: [   22.062219] Bluetooth: RFCOMM TTY layer initialized
May  9 09:04:47 swordfish kernel: [   22.062223] Bluetooth: RFCOMM socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.062224] Bluetooth: RFCOMM ver 1.11
May  9 09:04:47 swordfish kernel: [   22.064576] ppdev: user-space parallel port driver
May  9 09:04:47 swordfish kernel: [   22.069613] type=1400 audit(1336572287.821:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=849 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   22.069864] type=1400 audit(1336572287.821:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=849 comm="apparmor_parser"
May  9 09:04:47 swordfish polkitd[821]: started daemon version 0.104 using authority implementation `local' version `0.104'
May  9 09:04:47 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: init!
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: update_system_hostname
May  9 09:04:47 swordfish NetworkManager[814]:    SCPluginIfupdown: management mode: unmanaged
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth0, iface: eth0)
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: end _init.
May  9 09:04:47 swordfish NetworkManager[814]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  9 09:04:47 swordfish NetworkManager[814]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  9 09:04:47 swordfish NetworkManager[814]:    Ifupdown: get unmanaged devices count: 0
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: (25310000) ... get_connections.
May  9 09:04:47 swordfish NetworkManager[814]:    SCPlugin-Ifupdown: (25310000) ... get_connections (managed=false): return empty list.
May  9 09:04:47 swordfish NetworkManager[814]:    keyfile: parsing Wired connection 1 ... 
May  9 09:04:47 swordfish NetworkManager[814]:    keyfile:     read connection 'Wired connection 1'
May  9 09:04:47 swordfish NetworkManager[814]:    Ifupdown: get unmanaged devices count: 0
May  9 09:04:47 swordfish NetworkManager[814]: <info> modem-manager is now available
May  9 09:04:47 swordfish NetworkManager[814]: <info> monitoring kernel firmware directory '/lib/firmware'.
May  9 09:04:47 swordfish NetworkManager[814]: <info> WiFi enabled by radio killswitch; enabled by state file
May  9 09:04:47 swordfish NetworkManager[814]: <info> WWAN enabled by radio killswitch; enabled by state file
May  9 09:04:47 swordfish NetworkManager[814]: <info> WiMAX enabled by radio killswitch; enabled by state file
May  9 09:04:47 swordfish NetworkManager[814]: <info> Networking is enabled by state file
May  9 09:04:47 swordfish NetworkManager[814]: <warn> failed to allocate link cache: (-10) Operation not supported
May  9 09:04:47 swordfish NetworkManager[814]: <info> (eth0): carrier is OFF
May  9 09:04:47 swordfish NetworkManager[814]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
May  9 09:04:47 swordfish NetworkManager[814]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May  9 09:04:47 swordfish NetworkManager[814]: <info> (eth0): now managed
May  9 09:04:47 swordfish NetworkManager[814]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  9 09:04:47 swordfish NetworkManager[814]: <info> (eth0): bringing up device.
May  9 09:04:48 swordfish NetworkManager[814]: <info> (eth0): preparing device.
May  9 09:04:48 swordfish NetworkManager[814]: <info> (eth0): deactivating device (reason 'managed') [2]
May  9 09:04:48 swordfish kernel: [   22.327273] r8169 0000:04:00.0: eth0: link down
May  9 09:04:48 swordfish kernel: [   22.327303] r8169 0000:04:00.0: eth0: link down
May  9 09:04:48 swordfish kernel: [   22.327655] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 09:04:48 swordfish kernel: [   22.327843] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 09:04:48 swordfish kernel: [   22.385367] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
May  9 09:04:48 swordfish kernel: [   22.448223] type=1400 audit(1336572288.201:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=879 comm="apparmor_parser"
May  9 09:04:48 swordfish kernel: [   22.448482] type=1400 audit(1336572288.201:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=886 comm="apparmor_parser"
May  9 09:04:48 swordfish kernel: [   22.509214] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
May  9 09:04:48 swordfish kernel: [   22.509268] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
May  9 09:04:48 swordfish kernel: [   22.509321] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
May  9 09:04:48 swordfish kernel: [   22.509376] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
May  9 09:04:48 swordfish kernel: [   22.509419] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
May  9 09:04:48 swordfish kernel: [   22.509478] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
May  9 09:04:48 swordfish kernel: [   22.509513] input: HDA Intel PCH Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
May  9 09:04:48 swordfish cron[954]: (CRON) INFO (pidfile fd = 3)
May  9 09:04:48 swordfish anacron[978]: Anacron 2.3 started on 2012-05-09
May  9 09:04:48 swordfish acpid: starting up with proc fs
May  9 09:04:48 swordfish acpid: 35 rules loaded
May  9 09:04:48 swordfish acpid: waiting for events: event logging is off
May  9 09:04:48 swordfish cron[1023]: (CRON) STARTUP (fork ok)
May  9 09:04:48 swordfish cron[1023]: (CRON) INFO (Running @reboot jobs)
May  9 09:04:48 swordfish udev-configure-printer: add /module/lp
May  9 09:04:48 swordfish udev-configure-printer: Failed to get parent
May  9 09:04:48 swordfish acpid: client connected from 1029[0:0]
May  9 09:04:48 swordfish acpid: 1 client rule loaded
May  9 09:04:48 swordfish kernel: [   22.740082] init: alsa-restore main process (952) terminated with status 99
May  9 09:04:48 swordfish anacron[978]: Normal exit (0 jobs run)
May  9 09:04:48 swordfish dbus[785]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
May  9 09:04:48 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.Accounts'
May  9 09:04:48 swordfish accounts-daemon[1149]: started daemon version 0.6.15
May  9 09:04:48 swordfish kernel: [   22.994828] init: plymouth-stop pre-start process (1163) terminated with status 1
May  9 09:04:48 swordfish dbus[785]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
May  9 09:04:48 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
May  9 09:04:49 swordfish dbus[785]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
May  9 09:04:49 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.UPower'
May  9 09:04:49 swordfish anacron[1341]: Anacron 2.3 started on 2012-05-09
May  9 09:04:49 swordfish anacron[1341]: Normal exit (0 jobs run)
May  9 09:04:49 swordfish dbus[785]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
May  9 09:04:49 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.ColorManager'
May  9 09:04:49 swordfish dbus[785]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
May  9 09:04:49 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
May  9 09:04:49 swordfish rtkit-daemon[1449]: Successfully called chroot.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Successfully dropped privileges.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Successfully limited resources.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Running.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Watchdog thread running.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Canary thread running.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Successfully made thread 1447 of process 1447 (n/a) owned by '104' high priority at nice level -11.
May  9 09:04:49 swordfish rtkit-daemon[1449]: Supervising 1 threads of 1 processes of 1 users.
May  9 09:04:49 swordfish NetworkManager[814]: <info> (eth0): carrier now ON (device state 20)
May  9 09:04:49 swordfish NetworkManager[814]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May  9 09:04:49 swordfish NetworkManager[814]: <info> Auto-activating connection 'Wired connection 1'.
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) starting connection 'Wired connection 1'
May  9 09:04:49 swordfish NetworkManager[814]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  9 09:04:49 swordfish NetworkManager[814]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  9 09:04:49 swordfish NetworkManager[814]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  9 09:04:49 swordfish kernel: [   23.901329] r8169 0000:04:00.0: eth0: link up
May  9 09:04:49 swordfish kernel: [   23.901674] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  9 09:04:49 swordfish NetworkManager[814]: <info> dhclient started with pid 1456
May  9 09:04:49 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  9 09:04:49 swordfish dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  9 09:04:49 swordfish dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  9 09:04:49 swordfish dhclient: All rights reserved.
May  9 09:04:49 swordfish dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  9 09:04:49 swordfish dhclient: 
May  9 09:04:49 swordfish NetworkManager[814]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May  9 09:04:49 swordfish dhclient: Listening on LPF/eth0/10:78:d2:21:83:6b
May  9 09:04:49 swordfish dhclient: Sending on   LPF/eth0/10:78:d2:21:83:6b
May  9 09:04:49 swordfish dhclient: Sending on   Socket/fallback
May  9 09:04:49 swordfish dhclient: DHCPREQUEST of 76.31.91.157 on eth0 to 255.255.255.255 port 67
May  9 09:04:50 swordfish rtkit-daemon[1449]: Successfully made thread 1459 of process 1447 (n/a) owned by '104' RT at priority 5.
May  9 09:04:50 swordfish rtkit-daemon[1449]: Supervising 2 threads of 1 processes of 1 users.
May  9 09:04:50 swordfish rtkit-daemon[1449]: Successfully made thread 1460 of process 1447 (n/a) owned by '104' RT at priority 5.
May  9 09:04:50 swordfish rtkit-daemon[1449]: Supervising 3 threads of 1 processes of 1 users.
May  9 09:04:50 swordfish rtkit-daemon[1449]: Successfully made thread 1463 of process 1463 (n/a) owned by '104' high priority at nice level -11.
May  9 09:04:50 swordfish rtkit-daemon[1449]: Supervising 4 threads of 2 processes of 1 users.
May  9 09:04:50 swordfish pulseaudio[1463]: [pulseaudio] pid.c: Daemon already running.
May  9 09:04:52 swordfish dhclient: DHCPREQUEST of 76.31.91.157 on eth0 to 255.255.255.255 port 67
May  9 09:04:52 swordfish dhclient: DHCPACK of 76.31.91.157 from 96.120.16.45
May  9 09:04:52 swordfish dhclient: bound to 76.31.91.157 -- renewal in 88813 seconds.
May  9 09:04:52 swordfish NetworkManager[814]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May  9 09:04:52 swordfish NetworkManager[814]: <info>   address 76.31.91.157
May  9 09:04:52 swordfish NetworkManager[814]: <info>   prefix 23 (255.255.254.0)
May  9 09:04:52 swordfish NetworkManager[814]: <info>   gateway 76.31.90.1
May  9 09:04:52 swordfish NetworkManager[814]: <info>   hostname 'swordfish'
May  9 09:04:52 swordfish NetworkManager[814]: <info>   nameserver '75.75.76.76'
May  9 09:04:52 swordfish NetworkManager[814]: <info>   nameserver '75.75.75.75'
May  9 09:04:52 swordfish NetworkManager[814]: <info>   domain name 'hsd1.tx.comcast.net.'
May  9 09:04:52 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  9 09:04:52 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May  9 09:04:53 swordfish NetworkManager[814]: <info> DNS: starting dnsmasq...
May  9 09:04:53 swordfish NetworkManager[814]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May  9 09:04:53 swordfish dnsmasq[1469]: started, version 2.59 cache disabled
May  9 09:04:53 swordfish dnsmasq[1469]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  9 09:04:53 swordfish dnsmasq[1469]: using nameserver 75.75.75.75#53
May  9 09:04:53 swordfish dnsmasq[1469]: using nameserver 75.75.76.76#53
May  9 09:04:53 swordfish NetworkManager[814]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  9 09:04:53 swordfish NetworkManager[814]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May  9 09:04:53 swordfish NetworkManager[814]: <info> Activation (eth0) successful, device activated.
May  9 09:04:53 swordfish NetworkManager[814]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May  9 09:04:53 swordfish dbus[785]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  9 09:04:53 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  9 09:04:56 swordfish rtkit-daemon[1449]: Successfully made thread 1684 of process 1684 (n/a) owned by '1000' high priority at nice level -11.
May  9 09:04:56 swordfish rtkit-daemon[1449]: Supervising 4 threads of 2 processes of 2 users.
May  9 09:04:56 swordfish dbus[785]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May  9 09:04:56 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.UDisks'
May  9 09:04:56 swordfish rtkit-daemon[1449]: Successfully made thread 1708 of process 1684 (n/a) owned by '1000' RT at priority 5.
May  9 09:04:56 swordfish rtkit-daemon[1449]: Supervising 5 threads of 2 processes of 2 users.
May  9 09:04:56 swordfish rtkit-daemon[1449]: Successfully made thread 1709 of process 1684 (n/a) owned by '1000' RT at priority 5.
May  9 09:04:56 swordfish rtkit-daemon[1449]: Supervising 6 threads of 2 processes of 2 users.
May  9 09:05:00 swordfish kernel: [   34.282135] eth0: no IPv6 routers present
May  9 09:04:59 swordfish ntpdate[1531]: step time server 91.189.94.4 offset -2.537931 sec
May  9 09:05:09 swordfish goa[1998]: goa-daemon version 3.4.0 starting [main.c:112, main()]
May  9 09:05:55 swordfish dbus[785]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
May  9 09:05:56 swordfish AptDaemon: INFO: Initializing daemon
May  9 09:05:57 swordfish AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May  9 09:05:57 swordfish dbus[785]: [system] Successfully activated service 'org.freedesktop.PackageKit'
May  9 09:05:57 swordfish AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
May  9 09:05:57 swordfish AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e7f98116d2a54f48892db6b3933da8be
May  9 09:05:57 swordfish AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/e7f98116d2a54f48892db6b3933da8be
May  9 09:06:02 swordfish AptDaemon.PackageKit: INFO: Get updates()
May  9 09:06:03 swordfish AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/e7f98116d2a54f48892db6b3933da8be
May  9 09:06:08 swordfish dbus[785]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
May  9 09:06:09 swordfish dbus[785]: [system] Successfully activated service 'com.ubuntu.SystemService'
May  9 09:11:57 swordfish AptDaemon: INFO: Quitting due to inactivity
May  9 09:11:57 swordfish AptDaemon: INFO: Quitting was requested
May  9 09:17:01 swordfish CRON[2501]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  9 10:17:01 swordfish CRON[3859]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by songhk on 2012-05-09
The output of /var/log/kern.log
Could you check my log file. I need comment why my computer restarted automatically on 9:04 am today. 

Thanks


May  9 09:04:47 swordfish kernel: imklog 5.8.6, log source = /proc/kmsg started.
May  9 09:04:47 swordfish kernel: [    0.000000] Initializing cgroup subsys cpuset
May  9 09:04:47 swordfish kernel: [    0.000000] Initializing cgroup subsys cpu
May  9 09:04:47 swordfish kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@yellow) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
May  9 09:04:47 swordfish kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1fa1e5b9-b632-4aaa-af25-1b7036647204 ro acpi=force quiet splash vt.handoff=7
May  9 09:04:47 swordfish kernel: [    0.000000] KERNEL supported cpus:
May  9 09:04:47 swordfish kernel: [    0.000000]   Intel GenuineIntel
May  9 09:04:47 swordfish kernel: [    0.000000]   AMD AuthenticAMD
May  9 09:04:47 swordfish kernel: [    0.000000]   Centaur CentaurHauls
May  9 09:04:47 swordfish kernel: [    0.000000] BIOS-provided physical RAM map:
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000040200000 - 00000000bad81000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bad81000 - 00000000badd8000 (ACPI NVS)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000badd8000 - 00000000badfb000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000badfb000 - 00000000badfd000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000badfd000 - 00000000bae0d000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae0d000 - 00000000bae1a000 (ACPI NVS)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae1a000 - 00000000bae3c000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae3c000 - 00000000bae7f000 (ACPI NVS)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bae7f000 - 00000000bb000000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000bb800000 - 00000000bfa00000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023fe00000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000] NX (Execute Disable) protection: active
May  9 09:04:47 swordfish kernel: [    0.000000] DMI 2.6 present.
May  9 09:04:47 swordfish kernel: [    0.000000] DMI: ECS H61H2-M3/H61H2-M3, BIOS 4.6.4 03/29/2011
May  9 09:04:47 swordfish kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
May  9 09:04:47 swordfish kernel: [    0.000000] No AGP bridge found
May  9 09:04:47 swordfish kernel: [    0.000000] last_pfn = 0x23fe00 max_arch_pfn = 0x400000000
May  9 09:04:47 swordfish kernel: [    0.000000] MTRR default type: uncachable
May  9 09:04:47 swordfish kernel: [    0.000000] MTRR fixed ranges enabled:
May  9 09:04:47 swordfish kernel: [    0.000000]   00000-9FFFF write-back
May  9 09:04:47 swordfish kernel: [    0.000000]   A0000-BFFFF uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   C0000-CFFFF write-protect
May  9 09:04:47 swordfish kernel: [    0.000000]   D0000-E7FFF uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   E8000-FFFFF write-protect
May  9 09:04:47 swordfish kernel: [    0.000000] MTRR variable ranges enabled:
May  9 09:04:47 swordfish kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
May  9 09:04:47 swordfish kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
May  9 09:04:47 swordfish kernel: [    0.000000]   2 base 0BB800000 mask FFF800000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   4 base 0C0000000 mask FC0000000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   5 base 23FE00000 mask FFFE00000 uncachable
May  9 09:04:47 swordfish kernel: [    0.000000]   6 disabled
May  9 09:04:47 swordfish kernel: [    0.000000]   7 disabled
May  9 09:04:47 swordfish kernel: [    0.000000]   8 disabled
May  9 09:04:47 swordfish kernel: [    0.000000]   9 disabled
May  9 09:04:47 swordfish kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  9 09:04:47 swordfish kernel: [    0.000000] original variable MTRRs
May  9 09:04:47 swordfish kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 1, base: 8GB, range: 1GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 2, base: 3000MB, range: 8MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 4, base: 3GB, range: 1GB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 5, base: 9214MB, range: 2MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] total RAM covered: 8118M
May  9 09:04:47 swordfish kernel: [    0.000000] Found optimal setting for mtrr clean up
May  9 09:04:47 swordfish kernel: [    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 7  	lose cover RAM: 0G
May  9 09:04:47 swordfish kernel: [    0.000000] New variable MTRRs
May  9 09:04:47 swordfish kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 2, base: 3000MB, range: 8MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 5, base: 8GB, range: 1GB, type WB
May  9 09:04:47 swordfish kernel: [    0.000000] reg 6, base: 9214MB, range: 2MB, type UC
May  9 09:04:47 swordfish kernel: [    0.000000] e820 update range: 00000000bb800000 - 0000000100000000 (usable) ==> (reserved)
May  9 09:04:47 swordfish kernel: [    0.000000] last_pfn = 0xbb000 max_arch_pfn = 0x400000000
May  9 09:04:47 swordfish kernel: [    0.000000] found SMP MP-table at [ffff8800000fce80] fce80
May  9 09:04:47 swordfish kernel: [    0.000000] initial memory mapped : 0 - 20000000
May  9 09:04:47 swordfish kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
May  9 09:04:47 swordfish kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bb000000
May  9 09:04:47 swordfish kernel: [    0.000000]  0000000000 - 00bb000000 page 2M
May  9 09:04:47 swordfish kernel: [    0.000000] kernel direct mapping tables up to bb000000 @ 1fffc000-20000000
May  9 09:04:47 swordfish kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000023fe00000
May  9 09:04:47 swordfish kernel: [    0.000000]  0100000000 - 023fe00000 page 2M
May  9 09:04:47 swordfish kernel: [    0.000000] kernel direct mapping tables up to 23fe00000 @ baff6000-bb000000
May  9 09:04:47 swordfish kernel: [    0.000000] RAMDISK: 364e8000 - 3726c000
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: XSDT 00000000badce070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: FACP 00000000badd6a98 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: DSDT 00000000badce168 0892F (v02 ALASKA    A M I 00000010 INTL 20051117)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: FACS 00000000bae11f80 00040
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: APIC 00000000badd6b90 00092 (v03 ALASKA    A M I 01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: SSDT 00000000badd6c28 001D6 (v01 AMICPU     PROC 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: MCFG 00000000badd6e00 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: SLIC 00000000badd6e40 00176 (v01 AMI    APTIO    01072009 AMI  00010013)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: WDTT 00000000badd6fb8 00194 (v02 ALASKA    A M I 01072009 AMI  00000000)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: HPET 00000000badd7150 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: ASPT 00000000badd7188 00034 (v07 ALASKA PerfTune 01072009 AMI  00000000)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  9 09:04:47 swordfish kernel: [    0.000000] No NUMA configuration found
May  9 09:04:47 swordfish kernel: [    0.000000] Faking a node at 0000000000000000-000000023fe00000
May  9 09:04:47 swordfish kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000023fe00000
May  9 09:04:47 swordfish kernel: [    0.000000]   NODE_DATA [000000023fdfb000 - 000000023fdfffff]
May  9 09:04:47 swordfish kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237400000-ffff88023f3fffff] on node 0
May  9 09:04:47 swordfish kernel: [    0.000000] Zone PFN ranges:
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May  9 09:04:47 swordfish kernel: [    0.000000]   Normal   0x00100000 -> 0x0023fe00
May  9 09:04:47 swordfish kernel: [    0.000000] Movable zone start PFN for each node
May  9 09:04:47 swordfish kernel: [    0.000000] early_node_map[7] active PFN ranges
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00020200 -> 0x00040000
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00040200 -> 0x000bad81
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x000badfb -> 0x000badfd
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x000bae7f -> 0x000bb000
May  9 09:04:47 swordfish kernel: [    0.000000]     0: 0x00100000 -> 0x0023fe00
May  9 09:04:47 swordfish kernel: [    0.000000] On node 0 totalpages: 2074770
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA zone: 64 pages used for memmap
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA zone: 5 pages reserved
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
May  9 09:04:47 swordfish kernel: [    0.000000]   DMA32 zone: 744260 pages, LIFO batch:31
May  9 09:04:47 swordfish kernel: [    0.000000]   Normal zone: 20472 pages used for memmap
May  9 09:04:47 swordfish kernel: [    0.000000]   Normal zone: 1289736 pages, LIFO batch:31
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
May  9 09:04:47 swordfish kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IRQ0 used by override.
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IRQ2 used by override.
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: IRQ9 used by override.
May  9 09:04:47 swordfish kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  9 09:04:47 swordfish kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
May  9 09:04:47 swordfish kernel: [    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
May  9 09:04:47 swordfish kernel: [    0.000000] nr_irqs_gsi: 40
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bad81000 - 00000000badd8000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000badd8000 - 00000000badfb000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000badfd000 - 00000000bae0d000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bae0d000 - 00000000bae1a000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bae1a000 - 00000000bae3c000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bae3c000 - 00000000bae7f000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bb800000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000bfa00000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000fed1c000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
May  9 09:04:47 swordfish kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
May  9 09:04:47 swordfish kernel: [    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:3f31c000)
May  9 09:04:47 swordfish kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  9 09:04:47 swordfish kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
May  9 09:04:47 swordfish kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023fa00000 s83072 r8192 d23424 u262144
May  9 09:04:47 swordfish kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
May  9 09:04:47 swordfish kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
May  9 09:04:47 swordfish kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2037909
May  9 09:04:47 swordfish kernel: [    0.000000] Policy zone: Normal
May  9 09:04:47 swordfish kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1fa1e5b9-b632-4aaa-af25-1b7036647204 ro acpi=force quiet splash vt.handoff=7
May  9 09:04:47 swordfish kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  9 09:04:47 swordfish kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
May  9 09:04:47 swordfish kernel: [    0.000000] Checking aperture...
May  9 09:04:47 swordfish kernel: [    0.000000] No AGP bridge found
May  9 09:04:47 swordfish kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
May  9 09:04:47 swordfish kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
May  9 09:04:47 swordfish kernel: [    0.000000] Memory: 8071372k/9435136k available (6566k kernel code, 1136056k absent, 227708k reserved, 6637k data, 920k init)
May  9 09:04:47 swordfish kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
May  9 09:04:47 swordfish kernel: [    0.000000] Hierarchical RCU implementation.
May  9 09:04:47 swordfish kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
May  9 09:04:47 swordfish kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
May  9 09:04:47 swordfish kernel: [    0.000000] Extended CMOS year: 2000
May  9 09:04:47 swordfish kernel: [    0.000000] vt handoff: transparent VT on vt#7
May  9 09:04:47 swordfish kernel: [    0.000000] Console: colour dummy device 80x25
May  9 09:04:47 swordfish kernel: [    0.000000] console [tty0] enabled
May  9 09:04:47 swordfish kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
May  9 09:04:47 swordfish kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  9 09:04:47 swordfish kernel: [    0.000000] hpet clockevent registered
May  9 09:04:47 swordfish kernel: [    0.000000] Fast TSC calibration using PIT
May  9 09:04:47 swordfish kernel: [    0.004000] Detected 3392.137 MHz processor.
May  9 09:04:47 swordfish kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.27 BogoMIPS (lpj=13568548)
May  9 09:04:47 swordfish kernel: [    0.000004] pid_max: default: 32768 minimum: 301
May  9 09:04:47 swordfish kernel: [    0.000019] Security Framework initialized
May  9 09:04:47 swordfish kernel: [    0.000029] AppArmor: AppArmor initialized
May  9 09:04:47 swordfish kernel: [    0.000030] Yama: becoming mindful.
May  9 09:04:47 swordfish kernel: [    0.000538] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
May  9 09:04:47 swordfish kernel: [    0.001788] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  9 09:04:47 swordfish kernel: [    0.002275] Mount-cache hash table entries: 256
May  9 09:04:47 swordfish kernel: [    0.002348] Initializing cgroup subsys cpuacct
May  9 09:04:47 swordfish kernel: [    0.002351] Initializing cgroup subsys memory
May  9 09:04:47 swordfish kernel: [    0.002356] Initializing cgroup subsys devices
May  9 09:04:47 swordfish kernel: [    0.002357] Initializing cgroup subsys freezer
May  9 09:04:47 swordfish kernel: [    0.002358] Initializing cgroup subsys blkio
May  9 09:04:47 swordfish kernel: [    0.002362] Initializing cgroup subsys perf_event
May  9 09:04:47 swordfish kernel: [    0.002381] CPU: Physical Processor ID: 0
May  9 09:04:47 swordfish kernel: [    0.002382] CPU: Processor Core ID: 0
May  9 09:04:47 swordfish kernel: [    0.002385] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
May  9 09:04:47 swordfish kernel: [    0.002385] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
May  9 09:04:47 swordfish kernel: [    0.002388] mce: CPU supports 9 MCE banks
May  9 09:04:47 swordfish kernel: [    0.002398] CPU0: Thermal monitoring enabled (TM1)
May  9 09:04:47 swordfish kernel: [    0.002404] using mwait in idle threads.
May  9 09:04:47 swordfish kernel: [    0.004149] ACPI: Core revision 20110623
May  9 09:04:47 swordfish kernel: [    0.006610] ftrace: allocating 27049 entries in 107 pages
May  9 09:04:47 swordfish kernel: [    0.013618] x2apic not enabled, IRQ remapping init failed
May  9 09:04:47 swordfish kernel: [    0.014017] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  9 09:04:47 swordfish kernel: [    0.053585] CPU0: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz stepping 07
May  9 09:04:47 swordfish kernel: [    0.160553] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
May  9 09:04:47 swordfish kernel: [    0.160556] PEBS disabled due to CPU errata.
May  9 09:04:47 swordfish kernel: [    0.160558] ... version:                3
May  9 09:04:47 swordfish kernel: [    0.160559] ... bit width:              48
May  9 09:04:47 swordfish kernel: [    0.160559] ... generic registers:      4
May  9 09:04:47 swordfish kernel: [    0.160560] ... value mask:             0000ffffffffffff
May  9 09:04:47 swordfish kernel: [    0.160561] ... max period:             000000007fffffff
May  9 09:04:47 swordfish kernel: [    0.160562] ... fixed-purpose events:   3
May  9 09:04:47 swordfish kernel: [    0.160563] ... event mask:             000000070000000f
May  9 09:04:47 swordfish kernel: [    0.160666] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.160714] Booting Node   0, Processors  #1
May  9 09:04:47 swordfish kernel: [    0.160715] smpboot cpu 1: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.268337] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.268400]  #2
May  9 09:04:47 swordfish kernel: [    0.268401] smpboot cpu 2: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.376017] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.376075]  #3
May  9 09:04:47 swordfish kernel: [    0.376076] smpboot cpu 3: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.483693] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.483750]  #4
May  9 09:04:47 swordfish kernel: [    0.483751] smpboot cpu 4: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.591469] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.591535]  #5
May  9 09:04:47 swordfish kernel: [    0.591536] smpboot cpu 5: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.699154] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.699213]  #6
May  9 09:04:47 swordfish kernel: [    0.699214] smpboot cpu 6: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.806830] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.806888]  #7 Ok.
May  9 09:04:47 swordfish kernel: [    0.806889] smpboot cpu 7: start_ip = 99000
May  9 09:04:47 swordfish kernel: [    0.914506] NMI watchdog enabled, takes one hw-pmu counter.
May  9 09:04:47 swordfish kernel: [    0.914529] Brought up 8 CPUs
May  9 09:04:47 swordfish kernel: [    0.914531] Total of 8 processors activated (54276.05 BogoMIPS).
May  9 09:04:47 swordfish kernel: [    0.921436] devtmpfs: initialized
May  9 09:04:47 swordfish kernel: [    0.921984] EVM: security.selinux
May  9 09:04:47 swordfish kernel: [    0.921985] EVM: security.SMACK64
May  9 09:04:47 swordfish kernel: [    0.921986] EVM: security.capability
May  9 09:04:47 swordfish kernel: [    0.922001] PM: Registering ACPI NVS region at bad81000 (356352 bytes)
May  9 09:04:47 swordfish kernel: [    0.922005] PM: Registering ACPI NVS region at bae0d000 (53248 bytes)
May  9 09:04:47 swordfish kernel: [    0.922007] PM: Registering ACPI NVS region at bae3c000 (274432 bytes)
May  9 09:04:47 swordfish kernel: [    0.922509] print_constraints: dummy: 
May  9 09:04:47 swordfish kernel: [    0.922537] RTC time: 14:04:26, date: 05/09/12
May  9 09:04:47 swordfish kernel: [    0.922558] NET: Registered protocol family 16
May  9 09:04:47 swordfish kernel: [    0.922623] Trying to unpack rootfs image as initramfs...
May  9 09:04:47 swordfish kernel: [    0.922624] ACPI: bus type pci registered
May  9 09:04:47 swordfish kernel: [    0.922663] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May  9 09:04:47 swordfish kernel: [    0.922665] PCI: not using MMCONFIG
May  9 09:04:47 swordfish kernel: [    0.922666] PCI: Using configuration type 1 for base access
May  9 09:04:47 swordfish kernel: [    0.923248] bio: create slab <bio-0> at 0
May  9 09:04:47 swordfish kernel: [    0.923292] ACPI: Added _OSI(Module Device)
May  9 09:04:47 swordfish kernel: [    0.923293] ACPI: Added _OSI(Processor Device)
May  9 09:04:47 swordfish kernel: [    0.923294] ACPI: Added _OSI(3.0 _SCP Extensions)
May  9 09:04:47 swordfish kernel: [    0.923296] ACPI: Added _OSI(Processor Aggregator Device)
May  9 09:04:47 swordfish kernel: [    0.924080] ACPI: EC: Look up EC in DSDT
May  9 09:04:47 swordfish kernel: [    0.924969] ACPI: Executed 1 blocks of module-level executable AML code
May  9 09:04:47 swordfish kernel: [    0.926679] ACPI: SSDT 00000000bae19898 006F4 (v01    AMI      IST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.926940] ACPI: Dynamic OEM Table Load:
May  9 09:04:47 swordfish kernel: [    0.926942] ACPI: SSDT           (null) 006F4 (v01    AMI      IST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.926964] ACPI: SSDT 00000000bae10d98 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.927163] ACPI: Dynamic OEM Table Load:
May  9 09:04:47 swordfish kernel: [    0.927165] ACPI: SSDT           (null) 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
May  9 09:04:47 swordfish kernel: [    0.927689] ACPI: Interpreter enabled
May  9 09:04:47 swordfish kernel: [    0.927691] ACPI: (supports S0 S3 S4 S5)
May  9 09:04:47 swordfish kernel: [    0.927703] ACPI: Using IOAPIC for interrupt routing
May  9 09:04:47 swordfish kernel: [    0.927717] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May  9 09:04:47 swordfish kernel: [    0.927750] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
May  9 09:04:47 swordfish kernel: [    0.966033] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
May  9 09:04:47 swordfish kernel: [    0.968741] ACPI: No dock devices found.
May  9 09:04:47 swordfish kernel: [    0.968742] HEST: Table not found.
May  9 09:04:47 swordfish kernel: [    0.968744] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May  9 09:04:47 swordfish kernel: [    0.968856] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May  9 09:04:47 swordfish kernel: [    0.968978] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    0.968980] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    0.968981] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    0.968983] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
May  9 09:04:47 swordfish kernel: [    0.968984] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    0.968987] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000c8000-0x000dffff] (conflicts with Video ROM [mem 0x000c0000-0x000cd7ff])
May  9 09:04:47 swordfish kernel: [    0.968994] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
May  9 09:04:47 swordfish kernel: [    0.969021] pci 0000:00:02.0: [8086:0102] type 0 class 0x000300
May  9 09:04:47 swordfish kernel: [    0.969029] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
May  9 09:04:47 swordfish kernel: [    0.969034] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.969038] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
May  9 09:04:47 swordfish kernel: [    0.969082] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
May  9 09:04:47 swordfish kernel: [    0.969103] pci 0000:00:16.0: reg 10: [mem 0xfe407000-0xfe40700f 64bit]
May  9 09:04:47 swordfish kernel: [    0.969174] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969178] pci 0000:00:16.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969207] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
May  9 09:04:47 swordfish kernel: [    0.969226] pci 0000:00:1a.0: reg 10: [mem 0xfe406000-0xfe4063ff]
May  9 09:04:47 swordfish kernel: [    0.969311] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969315] pci 0000:00:1a.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969337] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
May  9 09:04:47 swordfish kernel: [    0.969351] pci 0000:00:1b.0: reg 10: [mem 0xfe400000-0xfe403fff 64bit]
May  9 09:04:47 swordfish kernel: [    0.969414] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969417] pci 0000:00:1b.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969437] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.969510] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969514] pci 0000:00:1c.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969535] pci 0000:00:1c.1: [8086:244e] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.969609] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969612] pci 0000:00:1c.1: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969635] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.969709] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969712] pci 0000:00:1c.4: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969741] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
May  9 09:04:47 swordfish kernel: [    0.969761] pci 0000:00:1d.0: reg 10: [mem 0xfe405000-0xfe4053ff]
May  9 09:04:47 swordfish kernel: [    0.969846] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.969850] pci 0000:00:1d.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.969871] pci 0000:00:1f.0: [8086:1c5c] type 0 class 0x000601
May  9 09:04:47 swordfish kernel: [    0.969986] pci 0000:00:1f.2: [8086:1c00] type 0 class 0x000101
May  9 09:04:47 swordfish kernel: [    0.969999] pci 0000:00:1f.2: reg 10: [io  0xf110-0xf117]
May  9 09:04:47 swordfish kernel: [    0.970006] pci 0000:00:1f.2: reg 14: [io  0xf100-0xf103]
May  9 09:04:47 swordfish kernel: [    0.970014] pci 0000:00:1f.2: reg 18: [io  0xf0f0-0xf0f7]
May  9 09:04:47 swordfish kernel: [    0.970021] pci 0000:00:1f.2: reg 1c: [io  0xf0e0-0xf0e3]
May  9 09:04:47 swordfish kernel: [    0.970028] pci 0000:00:1f.2: reg 20: [io  0xf0d0-0xf0df]
May  9 09:04:47 swordfish kernel: [    0.970035] pci 0000:00:1f.2: reg 24: [io  0xf0c0-0xf0cf]
May  9 09:04:47 swordfish kernel: [    0.970077] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
May  9 09:04:47 swordfish kernel: [    0.970091] pci 0000:00:1f.3: reg 10: [mem 0xfe404000-0xfe4040ff 64bit]
May  9 09:04:47 swordfish kernel: [    0.970110] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
May  9 09:04:47 swordfish kernel: [    0.970140] pci 0000:00:1f.5: [8086:1c08] type 0 class 0x000101
May  9 09:04:47 swordfish kernel: [    0.970154] pci 0000:00:1f.5: reg 10: [io  0xf0b0-0xf0b7]
May  9 09:04:47 swordfish kernel: [    0.970161] pci 0000:00:1f.5: reg 14: [io  0xf0a0-0xf0a3]
May  9 09:04:47 swordfish kernel: [    0.970168] pci 0000:00:1f.5: reg 18: [io  0xf090-0xf097]
May  9 09:04:47 swordfish kernel: [    0.970175] pci 0000:00:1f.5: reg 1c: [io  0xf080-0xf083]
May  9 09:04:47 swordfish kernel: [    0.970182] pci 0000:00:1f.5: reg 20: [io  0xf070-0xf07f]
May  9 09:04:47 swordfish kernel: [    0.970190] pci 0000:00:1f.5: reg 24: [io  0xf060-0xf06f]
May  9 09:04:47 swordfish kernel: [    0.970272] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
May  9 09:04:47 swordfish kernel: [    0.970343] pci 0000:02:00.0: [1283:8893] type 1 class 0x000604
May  9 09:04:47 swordfish kernel: [    0.970499] pci 0000:02:00.0: supports D1 D2
May  9 09:04:47 swordfish kernel: [    0.970500] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.970506] pci 0000:02:00.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.970530] pci 0000:00:1c.1: PCI bridge to [bus 02-03] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970540] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970541] pci 0000:00:1c.1:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970543] pci 0000:00:1c.1:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970544] pci 0000:00:1c.1:   bridge window [mem 0xbfa00000-0xffffffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970695] pci 0000:02:00.0: PCI bridge to [bus 03-03] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970721] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970722] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970723] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970725] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970726] pci 0000:02:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970728] pci 0000:02:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970729] pci 0000:02:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970731] pci 0000:02:00.0:   bridge window [mem 0xbfa00000-0xffffffff] (subtractive decode)
May  9 09:04:47 swordfish kernel: [    0.970806] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
May  9 09:04:47 swordfish kernel: [    0.970825] pci 0000:04:00.0: reg 10: [io  0xe000-0xe0ff]
May  9 09:04:47 swordfish kernel: [    0.970858] pci 0000:04:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.970879] pci 0000:04:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.970968] pci 0000:04:00.0: supports D1 D2
May  9 09:04:47 swordfish kernel: [    0.970969] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May  9 09:04:47 swordfish kernel: [    0.970974] pci 0000:04:00.0: PME# disabled
May  9 09:04:47 swordfish kernel: [    0.978222] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
May  9 09:04:47 swordfish kernel: [    0.978225] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
May  9 09:04:47 swordfish kernel: [    0.978233] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    0.978249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  9 09:04:47 swordfish kernel: [    0.978299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
May  9 09:04:47 swordfish kernel: [    0.978315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
May  9 09:04:47 swordfish kernel: [    0.978332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
May  9 09:04:47 swordfish kernel: [    0.978410]  pci0000:00: Requesting ACPI _OSC control (0x1d)
May  9 09:04:47 swordfish kernel: [    0.978534]  pci0000:00: ACPI _OSC control (0x1c) granted
May  9 09:04:47 swordfish kernel: [    0.980437] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980466] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980492] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0
May  9 09:04:47 swordfish kernel: [    0.980519] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980546] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
May  9 09:04:47 swordfish kernel: [    0.980572] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
May  9 09:04:47 swordfish kernel: [    0.980599] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980625] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
May  9 09:04:47 swordfish kernel: [    0.980692] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
May  9 09:04:47 swordfish kernel: [    0.980696] vgaarb: loaded
May  9 09:04:47 swordfish kernel: [    0.980697] vgaarb: bridge control possible 0000:00:02.0
May  9 09:04:47 swordfish kernel: [    0.980753] i2c-core: driver [aat2870] using legacy suspend method
May  9 09:04:47 swordfish kernel: [    0.980754] i2c-core: driver [aat2870] using legacy resume method
May  9 09:04:47 swordfish kernel: [    0.980791] SCSI subsystem initialized
May  9 09:04:47 swordfish kernel: [    0.980824] libata version 3.00 loaded.
May  9 09:04:47 swordfish kernel: [    0.980850] usbcore: registered new interface driver usbfs
May  9 09:04:47 swordfish kernel: [    0.980856] usbcore: registered new interface driver hub
May  9 09:04:47 swordfish kernel: [    0.980868] usbcore: registered new device driver usb
May  9 09:04:47 swordfish kernel: [    0.980913] PCI: Using ACPI for IRQ routing
May  9 09:04:47 swordfish kernel: [    0.987031] PCI: pci_cache_line_size set to 64 bytes
May  9 09:04:47 swordfish kernel: [    0.987085] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
May  9 09:04:47 swordfish kernel: [    0.987086] reserve RAM buffer: 00000000bad81000 - 00000000bbffffff 
May  9 09:04:47 swordfish kernel: [    0.987088] reserve RAM buffer: 00000000badfd000 - 00000000bbffffff 
May  9 09:04:47 swordfish kernel: [    0.987090] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
May  9 09:04:47 swordfish kernel: [    0.987091] reserve RAM buffer: 000000023fe00000 - 000000023fffffff 
May  9 09:04:47 swordfish kernel: [    0.987150] NetLabel: Initializing
May  9 09:04:47 swordfish kernel: [    0.987151] NetLabel:  domain hash size = 128
May  9 09:04:47 swordfish kernel: [    0.987152] NetLabel:  protocols = UNLABELED CIPSOv4
May  9 09:04:47 swordfish kernel: [    0.987158] NetLabel:  unlabeled traffic allowed by default
May  9 09:04:47 swordfish kernel: [    0.987187] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
May  9 09:04:47 swordfish kernel: [    0.987191] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
May  9 09:04:47 swordfish kernel: [    0.989196] Switching to clocksource hpet
May  9 09:04:47 swordfish kernel: [    0.992994] AppArmor: AppArmor Filesystem Enabled
May  9 09:04:47 swordfish kernel: [    0.993008] pnp: PnP ACPI init
May  9 09:04:47 swordfish kernel: [    0.993016] ACPI: bus type pnp registered
May  9 09:04:47 swordfish kernel: [    0.993107] pnp 00:00: [bus 00-ff]
May  9 09:04:47 swordfish kernel: [    0.993108] pnp 00:00: [io  0x0cf8-0x0cff]
May  9 09:04:47 swordfish kernel: [    0.993110] pnp 00:00: [io  0x0000-0x0cf7 window]
May  9 09:04:47 swordfish kernel: [    0.993111] pnp 00:00: [io  0x0d00-0xffff window]
May  9 09:04:47 swordfish kernel: [    0.993112] pnp 00:00: [mem 0x000a0000-0x000bffff window]
May  9 09:04:47 swordfish kernel: [    0.993113] pnp 00:00: [mem 0x000c8000-0x000dffff window]
May  9 09:04:47 swordfish kernel: [    0.993115] pnp 00:00: [mem 0xbfa00000-0xffffffff window]
May  9 09:04:47 swordfish kernel: [    0.993116] pnp 00:00: [mem 0x00000000 window]
May  9 09:04:47 swordfish kernel: [    0.993157] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
May  9 09:04:47 swordfish kernel: [    0.993189] pnp 00:01: [mem 0xfed10000-0xfed19fff]
May  9 09:04:47 swordfish kernel: [    0.993192] pnp 00:01: [mem 0xe0000000-0xefffffff]
May  9 09:04:47 swordfish kernel: [    0.993193] pnp 00:01: [mem 0xfed90000-0xfed93fff]
May  9 09:04:47 swordfish kernel: [    0.993194] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
May  9 09:04:47 swordfish kernel: [    0.993195] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
May  9 09:04:47 swordfish kernel: [    0.993221] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993222] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993224] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993225] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993227] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993229] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
May  9 09:04:47 swordfish kernel: [    0.993295] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
May  9 09:04:47 swordfish kernel: [    0.993296] pnp 00:02: [io  0x0a20-0x0a3f]
May  9 09:04:47 swordfish kernel: [    0.993297] pnp 00:02: [io  0x0a30-0x0a3f]
May  9 09:04:47 swordfish kernel: [    0.993298] pnp 00:02: [io  0x0a20-0x0a2f]
May  9 09:04:47 swordfish kernel: [    0.993317] system 00:02: [io  0x0a20-0x0a3f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993319] system 00:02: [io  0x0a30-0x0a3f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993320] system 00:02: [io  0x0a20-0x0a2f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993322] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
May  9 09:04:47 swordfish kernel: [    0.993348] pnp 00:03: [io  0x0060]
May  9 09:04:47 swordfish kernel: [    0.993349] pnp 00:03: [io  0x0064]
May  9 09:04:47 swordfish kernel: [    0.993357] pnp 00:03: [irq 12]
May  9 09:04:47 swordfish kernel: [    0.993373] pnp 00:03: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
May  9 09:04:47 swordfish kernel: [    0.993542] pnp 00:04: [io  0x03f8-0x03ff]
May  9 09:04:47 swordfish kernel: [    0.993546] pnp 00:04: [irq 4]
May  9 09:04:47 swordfish kernel: [    0.993547] pnp 00:04: [dma 0 disabled]
May  9 09:04:47 swordfish kernel: [    0.993583] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
May  9 09:04:47 swordfish kernel: [    0.993589] pnp 00:05: [dma 4]
May  9 09:04:47 swordfish kernel: [    0.993590] pnp 00:05: [io  0x0000-0x000f]
May  9 09:04:47 swordfish kernel: [    0.993591] pnp 00:05: [io  0x0081-0x0083]
May  9 09:04:47 swordfish kernel: [    0.993592] pnp 00:05: [io  0x0087]
May  9 09:04:47 swordfish kernel: [    0.993593] pnp 00:05: [io  0x0089-0x008b]
May  9 09:04:47 swordfish kernel: [    0.993594] pnp 00:05: [io  0x008f]
May  9 09:04:47 swordfish kernel: [    0.993595] pnp 00:05: [io  0x00c0-0x00df]
May  9 09:04:47 swordfish kernel: [    0.993609] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
May  9 09:04:47 swordfish kernel: [    0.993614] pnp 00:06: [io  0x0070-0x0071]
May  9 09:04:47 swordfish kernel: [    0.993618] pnp 00:06: [irq 8]
May  9 09:04:47 swordfish kernel: [    0.993631] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
May  9 09:04:47 swordfish kernel: [    0.993635] pnp 00:07: [io  0x0061]
May  9 09:04:47 swordfish kernel: [    0.993646] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
May  9 09:04:47 swordfish kernel: [    0.993655] pnp 00:08: [io  0x0010-0x001f]
May  9 09:04:47 swordfish kernel: [    0.993656] pnp 00:08: [io  0x0022-0x003f]
May  9 09:04:47 swordfish kernel: [    0.993657] pnp 00:08: [io  0x0044-0x005f]
May  9 09:04:47 swordfish kernel: [    0.993659] pnp 00:08: [io  0x0062-0x0063]
May  9 09:04:47 swordfish kernel: [    0.993660] pnp 00:08: [io  0x0065-0x006f]
May  9 09:04:47 swordfish kernel: [    0.993661] pnp 00:08: [io  0x0072-0x007f]
May  9 09:04:47 swordfish kernel: [    0.993662] pnp 00:08: [io  0x0080]
May  9 09:04:47 swordfish kernel: [    0.993663] pnp 00:08: [io  0x0084-0x0086]
May  9 09:04:47 swordfish kernel: [    0.993664] pnp 00:08: [io  0x0088]
May  9 09:04:47 swordfish kernel: [    0.993665] pnp 00:08: [io  0x008c-0x008e]
May  9 09:04:47 swordfish kernel: [    0.993666] pnp 00:08: [io  0x0090-0x009f]
May  9 09:04:47 swordfish kernel: [    0.993667] pnp 00:08: [io  0x00a2-0x00bf]
May  9 09:04:47 swordfish kernel: [    0.993668] pnp 00:08: [io  0x00e0-0x00ef]
May  9 09:04:47 swordfish kernel: [    0.993669] pnp 00:08: [io  0x04d0-0x04d1]
May  9 09:04:47 swordfish kernel: [    0.993693] system 00:08: [io  0x04d0-0x04d1] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993695] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
May  9 09:04:47 swordfish kernel: [    0.993699] pnp 00:09: [io  0x00f0-0x00ff]
May  9 09:04:47 swordfish kernel: [    0.993703] pnp 00:09: [irq 13]
May  9 09:04:47 swordfish kernel: [    0.993717] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
May  9 09:04:47 swordfish kernel: [    0.993810] pnp 00:0a: [io  0x0400-0x0453]
May  9 09:04:47 swordfish kernel: [    0.993811] pnp 00:0a: [io  0x0458-0x047f]
May  9 09:04:47 swordfish kernel: [    0.993812] pnp 00:0a: [io  0x1180-0x119f]
May  9 09:04:47 swordfish kernel: [    0.993813] pnp 00:0a: [io  0x0500-0x057f]
May  9 09:04:47 swordfish kernel: [    0.993815] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
May  9 09:04:47 swordfish kernel: [    0.993816] pnp 00:0a: [mem 0xfec00000-0xfecfffff]
May  9 09:04:47 swordfish kernel: [    0.993817] pnp 00:0a: [mem 0xfed08000-0xfed08fff]
May  9 09:04:47 swordfish kernel: [    0.993818] pnp 00:0a: [mem 0xff000000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    0.993839] system 00:0a: [io  0x0400-0x0453] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993840] system 00:0a: [io  0x0458-0x047f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993842] system 00:0a: [io  0x1180-0x119f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993843] system 00:0a: [io  0x0500-0x057f] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993845] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993847] system 00:0a: [mem 0xfec00000-0xfecfffff] could not be reserved
May  9 09:04:47 swordfish kernel: [    0.993848] system 00:0a: [mem 0xfed08000-0xfed08fff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993850] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993851] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
May  9 09:04:47 swordfish kernel: [    0.993871] pnp 00:0b: [io  0x0454-0x0457]
May  9 09:04:47 swordfish kernel: [    0.993889] system 00:0b: [io  0x0454-0x0457] has been reserved
May  9 09:04:47 swordfish kernel: [    0.993891] system 00:0b: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
May  9 09:04:47 swordfish kernel: [    0.993949] pnp 00:0c: [mem 0xfed00000-0xfed003ff]
May  9 09:04:47 swordfish kernel: [    0.993969] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
May  9 09:04:47 swordfish kernel: [    0.994062] pnp: PnP ACPI: found 13 devices
May  9 09:04:47 swordfish kernel: [    0.994063] ACPI: ACPI bus type pnp unregistered
May  9 09:04:47 swordfish kernel: [    0.999897] PCI: max bus depth: 2 pci_try_num: 3
May  9 09:04:47 swordfish kernel: [    0.999936] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
May  9 09:04:47 swordfish kernel: [    0.999947] pci 0000:02:00.0: PCI bridge to [bus 03-03]
May  9 09:04:47 swordfish kernel: [    0.999969] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
May  9 09:04:47 swordfish kernel: [    0.999980] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
May  9 09:04:47 swordfish kernel: [    0.999983] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
May  9 09:04:47 swordfish kernel: [    0.999989] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    1.000005] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  9 09:04:47 swordfish kernel: [    1.000009] pci 0000:00:1c.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000018] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    1.000021] pci 0000:00:1c.1: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000030] pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  9 09:04:47 swordfish kernel: [    1.000037] pci 0000:02:00.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000044] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  9 09:04:47 swordfish kernel: [    1.000048] pci 0000:00:1c.4: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.000051] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    1.000052] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    1.000054] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    1.000055] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    1.000057] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    1.000058] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    1.000059] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    1.000061] pci_bus 0000:02: resource 7 [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    1.000062] pci_bus 0000:03: resource 8 [io  0x0000-0x0cf7]
May  9 09:04:47 swordfish kernel: [    1.000063] pci_bus 0000:03: resource 9 [io  0x0d00-0xffff]
May  9 09:04:47 swordfish kernel: [    1.000065] pci_bus 0000:03: resource 10 [mem 0x000a0000-0x000bffff]
May  9 09:04:47 swordfish kernel: [    1.000066] pci_bus 0000:03: resource 11 [mem 0xbfa00000-0xffffffff]
May  9 09:04:47 swordfish kernel: [    1.000067] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
May  9 09:04:47 swordfish kernel: [    1.000069] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
May  9 09:04:47 swordfish kernel: [    1.000087] NET: Registered protocol family 2
May  9 09:04:47 swordfish kernel: [    1.000237] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  9 09:04:47 swordfish kernel: [    1.000868] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May  9 09:04:47 swordfish kernel: [    1.001854] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May  9 09:04:47 swordfish kernel: [    1.001971] TCP: Hash tables configured (established 524288 bind 65536)
May  9 09:04:47 swordfish kernel: [    1.001973] TCP reno registered
May  9 09:04:47 swordfish kernel: [    1.001983] UDP hash table entries: 4096 (order: 5, 131072 bytes)
May  9 09:04:47 swordfish kernel: [    1.002007] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
May  9 09:04:47 swordfish kernel: [    1.002070] NET: Registered protocol family 1
May  9 09:04:47 swordfish kernel: [    1.002080] pci 0000:00:02.0: Boot video device
May  9 09:04:47 swordfish kernel: [    1.002092] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    1.128904] pci 0000:00:1a.0: PCI INT A disabled
May  9 09:04:47 swordfish kernel: [    1.128927] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  9 09:04:47 swordfish kernel: [    1.256539] pci 0000:00:1d.0: PCI INT A disabled
May  9 09:04:47 swordfish kernel: [    1.256558] PCI: CLS 64 bytes, default 64
May  9 09:04:47 swordfish kernel: [    1.256560] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
May  9 09:04:47 swordfish kernel: [    1.256561] Placing 64MB software IO TLB between ffff8800b6d81000 - ffff8800bad81000
May  9 09:04:47 swordfish kernel: [    1.256563] software IO TLB at phys 0xb6d81000 - 0xbad81000
May  9 09:04:47 swordfish kernel: [    1.256976] audit: initializing netlink socket (disabled)
May  9 09:04:47 swordfish kernel: [    1.256983] type=2000 audit(1336572266.036:1): initialized
May  9 09:04:47 swordfish kernel: [    1.280532] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  9 09:04:47 swordfish kernel: [    1.297780] VFS: Disk quotas dquot_6.5.2
May  9 09:04:47 swordfish kernel: [    1.297812] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  9 09:04:47 swordfish kernel: [    1.298094] fuse init (API version 7.17)
May  9 09:04:47 swordfish kernel: [    1.298145] msgmni has been set to 15764
May  9 09:04:47 swordfish kernel: [    1.298383] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May  9 09:04:47 swordfish kernel: [    1.298402] io scheduler noop registered
May  9 09:04:47 swordfish kernel: [    1.298403] io scheduler deadline registered
May  9 09:04:47 swordfish kernel: [    1.298419] io scheduler cfq registered (default)
May  9 09:04:47 swordfish kernel: [    1.298482] pcieport 0000:00:1c.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.298524] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [    1.298582] pcieport 0000:00:1c.4: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.298619] pcieport 0000:00:1c.4: irq 41 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [    1.298688] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
May  9 09:04:47 swordfish kernel: [    1.298692] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
May  9 09:04:47 swordfish kernel: [    1.298707] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
May  9 09:04:47 swordfish kernel: [    1.298708] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
May  9 09:04:47 swordfish kernel: [    1.298712] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
May  9 09:04:47 swordfish kernel: [    1.298721] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  9 09:04:47 swordfish kernel: [    1.298734] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  9 09:04:47 swordfish kernel: [    1.298762] intel_idle: MWAIT substates: 0x1120
May  9 09:04:47 swordfish kernel: [    1.298763] intel_idle: v0.4 model 0x2A
May  9 09:04:47 swordfish kernel: [    1.298764] intel_idle: lapic_timer_reliable_states 0xffffffff
May  9 09:04:47 swordfish kernel: [    1.298829] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May  9 09:04:47 swordfish kernel: [    1.298833] ACPI: Power Button [PWRB]
May  9 09:04:47 swordfish kernel: [    1.298856] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  9 09:04:47 swordfish kernel: [    1.298858] ACPI: Power Button [PWRF]
May  9 09:04:47 swordfish kernel: [    1.301286] ERST: Table is not found!
May  9 09:04:47 swordfish kernel: [    1.301288] GHES: HEST is not enabled!
May  9 09:04:47 swordfish kernel: [    1.301327] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May  9 09:04:47 swordfish kernel: [    1.321678] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 09:04:47 swordfish kernel: [    1.321769] Freeing initrd memory: 13840k freed
May  9 09:04:47 swordfish kernel: [    1.548374] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 09:04:47 swordfish kernel: [    1.595765] Linux agpgart interface v0.103
May  9 09:04:47 swordfish kernel: [    1.595808] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
May  9 09:04:47 swordfish kernel: [    1.595901] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
May  9 09:04:47 swordfish kernel: [    1.597196] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
May  9 09:04:47 swordfish kernel: [    1.597288] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
May  9 09:04:47 swordfish kernel: [    1.598095] brd: module loaded
May  9 09:04:47 swordfish kernel: [    1.598508] loop: module loaded
May  9 09:04:47 swordfish kernel: [    1.598597] ata_piix 0000:00:1f.2: version 2.13
May  9 09:04:47 swordfish kernel: [    1.598612] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  9 09:04:47 swordfish kernel: [    1.598617] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
May  9 09:04:47 swordfish kernel: [    1.751133] ata_piix 0000:00:1f.2: SCR access via SIDPR is available but doesn't work
May  9 09:04:47 swordfish kernel: [    1.751145] ata_piix 0000:00:1f.2: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.751339] scsi0 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.751385] scsi1 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.751874] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf0d0 irq 14
May  9 09:04:47 swordfish kernel: [    1.751876] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf0d8 irq 15
May  9 09:04:47 swordfish kernel: [    1.751888] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  9 09:04:47 swordfish kernel: [    1.751893] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
May  9 09:04:47 swordfish kernel: [    1.751927] ata_piix 0000:00:1f.5: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.752050] scsi2 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.752089] scsi3 : ata_piix
May  9 09:04:47 swordfish kernel: [    1.752623] ata3: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf070 irq 19
May  9 09:04:47 swordfish kernel: [    1.752626] ata4: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf078 irq 19
May  9 09:04:47 swordfish kernel: [    1.752796] Fixed MDIO Bus: probed
May  9 09:04:47 swordfish kernel: [    1.752808] tun: Universal TUN/TAP device driver, 1.6
May  9 09:04:47 swordfish kernel: [    1.752809] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  9 09:04:47 swordfish kernel: [    1.752836] PPP generic driver version 2.4.2
May  9 09:04:47 swordfish kernel: [    1.752894] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  9 09:04:47 swordfish kernel: [    1.752905] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    1.752918] ehci_hcd 0000:00:1a.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.752920] ehci_hcd 0000:00:1a.0: EHCI Host Controller
May  9 09:04:47 swordfish kernel: [    1.752944] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
May  9 09:04:47 swordfish kernel: [    1.752965] ehci_hcd 0000:00:1a.0: debug port 2
May  9 09:04:47 swordfish kernel: [    1.756853] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
May  9 09:04:47 swordfish kernel: [    1.756863] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe406000
May  9 09:04:47 swordfish kernel: [    1.771063] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
May  9 09:04:47 swordfish kernel: [    1.771174] hub 1-0:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    1.771177] hub 1-0:1.0: 2 ports detected
May  9 09:04:47 swordfish kernel: [    1.771214] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  9 09:04:47 swordfish kernel: [    1.771223] ehci_hcd 0000:00:1d.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    1.771226] ehci_hcd 0000:00:1d.0: EHCI Host Controller
May  9 09:04:47 swordfish kernel: [    1.771255] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May  9 09:04:47 swordfish kernel: [    1.771272] ehci_hcd 0000:00:1d.0: debug port 2
May  9 09:04:47 swordfish kernel: [    1.775141] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
May  9 09:04:47 swordfish kernel: [    1.775150] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe405000
May  9 09:04:47 swordfish kernel: [    1.791006] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
May  9 09:04:47 swordfish kernel: [    1.791111] hub 2-0:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    1.791113] hub 2-0:1.0: 2 ports detected
May  9 09:04:47 swordfish kernel: [    1.791145] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  9 09:04:47 swordfish kernel: [    1.791150] uhci_hcd: USB Universal Host Controller Interface driver
May  9 09:04:47 swordfish kernel: [    1.791174] usbcore: registered new interface driver libusual
May  9 09:04:47 swordfish kernel: [    1.791195] i8042: PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
May  9 09:04:47 swordfish kernel: [    1.791196] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
May  9 09:04:47 swordfish kernel: [    1.791571] serio: i8042 KBD port at 0x60,0x64 irq 1
May  9 09:04:47 swordfish kernel: [    1.791575] serio: i8042 AUX port at 0x60,0x64 irq 12
May  9 09:04:47 swordfish kernel: [    1.791645] mousedev: PS/2 mouse device common for all mice
May  9 09:04:47 swordfish kernel: [    1.791732] rtc_cmos 00:06: RTC can wake from S4
May  9 09:04:47 swordfish kernel: [    1.791815] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
May  9 09:04:47 swordfish kernel: [    1.791840] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May  9 09:04:47 swordfish kernel: [    1.791882] device-mapper: uevent: version 1.0.3
May  9 09:04:47 swordfish kernel: [    1.791921] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
May  9 09:04:47 swordfish kernel: [    1.792026] cpuidle: using governor ladder
May  9 09:04:47 swordfish kernel: [    1.792189] cpuidle: using governor menu
May  9 09:04:47 swordfish kernel: [    1.792190] EFI Variables Facility v0.08 2004-May-17
May  9 09:04:47 swordfish kernel: [    1.792300] TCP cubic registered
May  9 09:04:47 swordfish kernel: [    1.792354] NET: Registered protocol family 10
May  9 09:04:47 swordfish kernel: [    1.792584] NET: Registered protocol family 17
May  9 09:04:47 swordfish kernel: [    1.792591] Registering the dns_resolver key type
May  9 09:04:47 swordfish kernel: [    1.792672] PM: Hibernation image not present or could not be loaded.
May  9 09:04:47 swordfish kernel: [    1.792679] registered taskstats version 1
May  9 09:04:47 swordfish kernel: [    1.805133]   Magic number: 12:665:80
May  9 09:04:47 swordfish kernel: [    1.805245] rtc_cmos 00:06: setting system clock to 2012-05-09 14:04:27 UTC (1336572267)
May  9 09:04:47 swordfish kernel: [    1.806272] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  9 09:04:47 swordfish kernel: [    1.806273] EDD information not available.
May  9 09:04:47 swordfish kernel: [    2.082193] usb 1-1: new high-speed USB device number 2 using ehci_hcd
May  9 09:04:47 swordfish kernel: [    2.214694] hub 1-1:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    2.214897] hub 1-1:1.0: 4 ports detected
May  9 09:04:47 swordfish kernel: [    2.225821] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  9 09:04:47 swordfish kernel: [    2.225949] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  9 09:04:47 swordfish kernel: [    2.233989] ata3.00: ATAPI: HL-DT-ST DVDRAM GH24NS70, GN00, max UDMA/100
May  9 09:04:47 swordfish kernel: [    2.234271] ata4.00: ATA-8: WDC WD10EADX-22TDHB0, 77.04D77, max UDMA/133
May  9 09:04:47 swordfish kernel: [    2.234274] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  9 09:04:47 swordfish kernel: [    2.242157] ata4.00: configured for UDMA/133
May  9 09:04:47 swordfish kernel: [    2.249925] ata3.00: configured for UDMA/100
May  9 09:04:47 swordfish kernel: [    2.253699] Refined TSC clocksource calibration: 3392.295 MHz.
May  9 09:04:47 swordfish kernel: [    2.253705] Switching to clocksource tsc
May  9 09:04:47 swordfish kernel: [    2.258404] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS70  GN00 PQ: 0 ANSI: 5
May  9 09:04:47 swordfish kernel: [    2.267027] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  9 09:04:47 swordfish kernel: [    2.267032] cdrom: Uniform CD-ROM driver Revision: 3.20
May  9 09:04:47 swordfish kernel: [    2.267205] sr 2:0:0:0: Attached scsi CD-ROM sr0
May  9 09:04:47 swordfish kernel: [    2.267289] sr 2:0:0:0: Attached scsi generic sg0 type 5
May  9 09:04:47 swordfish kernel: [    2.267604] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EADX-22T 77.0 PQ: 0 ANSI: 5
May  9 09:04:47 swordfish kernel: [    2.267803] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
May  9 09:04:47 swordfish kernel: [    2.267812] sd 3:0:0:0: Attached scsi generic sg1 type 0
May  9 09:04:47 swordfish kernel: [    2.268102] sd 3:0:0:0: [sda] Write Protect is off
May  9 09:04:47 swordfish kernel: [    2.268105] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  9 09:04:47 swordfish kernel: [    2.268198] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 09:04:47 swordfish kernel: [    2.298537]  sda: sda1 sda2 < sda5 >
May  9 09:04:47 swordfish kernel: [    2.299524] sd 3:0:0:0: [sda] Attached SCSI disk
May  9 09:04:47 swordfish kernel: [    2.300506] Freeing unused kernel memory: 920k freed
May  9 09:04:47 swordfish kernel: [    2.300574] Write protecting the kernel read-only data: 12288k
May  9 09:04:47 swordfish kernel: [    2.303700] Freeing unused kernel memory: 1608k freed
May  9 09:04:47 swordfish kernel: [    2.306077] Freeing unused kernel memory: 1196k freed
May  9 09:04:47 swordfish kernel: [    2.325490] usb 2-1: new high-speed USB device number 2 using ehci_hcd
May  9 09:04:47 swordfish kernel: [    2.326664] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  9 09:04:47 swordfish kernel: [    2.326683] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [    2.326713] r8169 0000:04:00.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [    2.326780] r8169 0000:04:00.0: irq 42 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [    2.327100] r8169 0000:04:00.0: eth0: RTL8105e at 0xffffc90000c74000, 10:78:d2:21:83:6b, XID 00a00000 IRQ 42
May  9 09:04:47 swordfish kernel: [    2.461680] hub 2-1:1.0: USB hub found
May  9 09:04:47 swordfish kernel: [    2.461765] hub 2-1:1.0: 6 ports detected
May  9 09:04:47 swordfish kernel: [    2.511319] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
May  9 09:04:47 swordfish kernel: [    2.511321] EXT4-fs (sda1): write access will be enabled during recovery
May  9 09:04:47 swordfish kernel: [    2.732507] usb 2-1.6: new low-speed USB device number 3 using ehci_hcd
May  9 09:04:47 swordfish kernel: [    2.834130] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input2
May  9 09:04:47 swordfish kernel: [    2.834242] generic-usb 0003:03F0:0F0C.0001: input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.0-1.6/input0
May  9 09:04:47 swordfish kernel: [    2.840004] input: BTC USB Multimedia Cordless Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input3
May  9 09:04:47 swordfish kernel: [    2.840298] generic-usb 0003:03F0:0F0C.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Kit] on usb-0000:00:1d.0-1.6/input1
May  9 09:04:47 swordfish kernel: [    2.840308] usbcore: registered new interface driver usbhid
May  9 09:04:47 swordfish kernel: [    2.840309] usbhid: USB HID core driver
May  9 09:04:47 swordfish kernel: [    5.840405] EXT4-fs (sda1): orphan cleanup on readonly fs
May  9 09:04:47 swordfish kernel: [    5.840411] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314426
May  9 09:04:47 swordfish kernel: [    5.840447] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314192
May  9 09:04:47 swordfish kernel: [    5.840454] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314329
May  9 09:04:47 swordfish kernel: [    5.840458] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314319
May  9 09:04:47 swordfish kernel: [    5.840464] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55318181
May  9 09:04:47 swordfish kernel: [    5.840480] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315569
May  9 09:04:47 swordfish kernel: [    5.840501] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 26083479
May  9 09:04:47 swordfish kernel: [    5.877241] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101511
May  9 09:04:47 swordfish kernel: [    5.877275] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101510
May  9 09:04:47 swordfish kernel: [    5.877296] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101507
May  9 09:04:47 swordfish kernel: [    5.877319] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101506
May  9 09:04:47 swordfish kernel: [    5.877326] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101503
May  9 09:04:47 swordfish kernel: [    5.877332] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101502
May  9 09:04:47 swordfish kernel: [    5.877338] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101499
May  9 09:04:47 swordfish kernel: [    5.877344] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101498
May  9 09:04:47 swordfish kernel: [    5.877351] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101495
May  9 09:04:47 swordfish kernel: [    5.877356] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101492
May  9 09:04:47 swordfish kernel: [    5.877363] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316519
May  9 09:04:47 swordfish kernel: [    5.891354] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316511
May  9 09:04:47 swordfish kernel: [    5.918796] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389461
May  9 09:04:47 swordfish kernel: [    5.918833] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389460
May  9 09:04:47 swordfish kernel: [    5.918840] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389459
May  9 09:04:47 swordfish kernel: [    5.918843] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389458
May  9 09:04:47 swordfish kernel: [    5.918849] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389457
May  9 09:04:47 swordfish kernel: [    5.918855] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101487
May  9 09:04:47 swordfish kernel: [    5.930694] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101484
May  9 09:04:47 swordfish kernel: [    5.930718] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101479
May  9 09:04:47 swordfish kernel: [    5.930738] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101475
May  9 09:04:47 swordfish kernel: [    5.930744] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56101474
May  9 09:04:47 swordfish kernel: [    5.931795] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099200
May  9 09:04:47 swordfish kernel: [    5.931834] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099199
May  9 09:04:47 swordfish kernel: [    5.931840] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099198
May  9 09:04:47 swordfish kernel: [    5.931848] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099196
May  9 09:04:47 swordfish kernel: [    5.931854] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099195
May  9 09:04:47 swordfish kernel: [    5.931860] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099194
May  9 09:04:47 swordfish kernel: [    5.931866] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099193
May  9 09:04:47 swordfish kernel: [    5.931872] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099192
May  9 09:04:47 swordfish kernel: [    5.931878] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099191
May  9 09:04:47 swordfish kernel: [    5.931884] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099190
May  9 09:04:47 swordfish kernel: [    5.931890] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099189
May  9 09:04:47 swordfish kernel: [    5.931896] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099188
May  9 09:04:47 swordfish kernel: [    5.931906] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099187
May  9 09:04:47 swordfish kernel: [    5.931913] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099186
May  9 09:04:47 swordfish kernel: [    5.931919] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 56099182
May  9 09:04:47 swordfish kernel: [    5.945716] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313639
May  9 09:04:47 swordfish kernel: [    5.945744] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316509
May  9 09:04:47 swordfish kernel: [    5.945750] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316510
May  9 09:04:47 swordfish kernel: [    5.945756] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316508
May  9 09:04:47 swordfish kernel: [    5.945762] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55316507
May  9 09:04:47 swordfish kernel: [    5.953968] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315568
May  9 09:04:47 swordfish kernel: [    5.953994] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315562
May  9 09:04:47 swordfish kernel: [    5.954000] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315630
May  9 09:04:47 swordfish kernel: [    5.976827] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953723
May  9 09:04:47 swordfish kernel: [    5.976862] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953722
May  9 09:04:47 swordfish kernel: [    5.976868] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953600
May  9 09:04:47 swordfish kernel: [    5.976875] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953579
May  9 09:04:47 swordfish kernel: [    5.976882] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953564
May  9 09:04:47 swordfish kernel: [    5.976891] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953537
May  9 09:04:47 swordfish kernel: [    5.976897] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953444
May  9 09:04:47 swordfish kernel: [    5.976904] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953426
May  9 09:04:47 swordfish kernel: [    5.976911] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953298
May  9 09:04:47 swordfish kernel: [    5.976917] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953265
May  9 09:04:47 swordfish kernel: [    5.976933] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25953257
May  9 09:04:47 swordfish kernel: [    5.976939] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 25952961
May  9 09:04:47 swordfish kernel: [    5.977775] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314165
May  9 09:04:47 swordfish kernel: [    5.977814] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313646
May  9 09:04:47 swordfish kernel: [    5.977820] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315555
May  9 09:04:47 swordfish kernel: [    5.977826] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315483
May  9 09:04:47 swordfish kernel: [    5.977833] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315622
May  9 09:04:47 swordfish kernel: [    6.287768] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55318292
May  9 09:04:47 swordfish kernel: [    6.287812] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55318281
May  9 09:04:47 swordfish kernel: [    6.287820] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315621
May  9 09:04:47 swordfish kernel: [    6.287826] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315620
May  9 09:04:47 swordfish kernel: [    6.287832] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313700
May  9 09:04:47 swordfish kernel: [    6.287839] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315544
May  9 09:04:47 swordfish kernel: [    6.295099] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314893
May  9 09:04:47 swordfish kernel: [    6.295138] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313955
May  9 09:04:47 swordfish kernel: [    6.295145] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315571
May  9 09:04:47 swordfish kernel: [    6.296969] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315438
May  9 09:04:47 swordfish kernel: [    6.297001] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315291
May  9 09:04:47 swordfish kernel: [    6.297018] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313988
May  9 09:04:47 swordfish kernel: [    6.297040] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313522
May  9 09:04:47 swordfish kernel: [    6.297047] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314197
May  9 09:04:47 swordfish kernel: [    6.297053] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55315545
May  9 09:04:47 swordfish kernel: [    6.297059] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314849
May  9 09:04:47 swordfish kernel: [    6.297066] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313985
May  9 09:04:47 swordfish kernel: [    6.297072] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313647
May  9 09:04:47 swordfish kernel: [    6.297078] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314922
May  9 09:04:47 swordfish kernel: [    6.297084] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314169
May  9 09:04:47 swordfish kernel: [    6.297090] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389449
May  9 09:04:47 swordfish kernel: [    6.297096] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389448
May  9 09:04:47 swordfish kernel: [    6.297102] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 35389447
May  9 09:04:47 swordfish kernel: [    6.297110] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313818
May  9 09:04:47 swordfish kernel: [    6.297117] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313811
May  9 09:04:47 swordfish kernel: [    6.297123] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55314894
May  9 09:04:47 swordfish kernel: [    6.297128] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55313742
May  9 09:04:47 swordfish kernel: [    6.314572] EXT4-fs (sda1): 96 orphan inodes deleted
May  9 09:04:47 swordfish kernel: [    6.314576] EXT4-fs (sda1): recovery complete
May  9 09:04:47 swordfish kernel: [    6.920821] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
May  9 09:04:47 swordfish kernel: [   21.529105] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 09:04:47 swordfish kernel: [   21.595280] lp: driver loaded but no devices found
May  9 09:04:47 swordfish kernel: [   21.596613] [drm] Initialized drm 1.1.0 20060810
May  9 09:04:47 swordfish kernel: [   21.598466] it87: Found IT8721F chip at 0xa30, revision 1
May  9 09:04:47 swordfish kernel: [   21.598504] ACPI: resource it87 [io  0x0a35-0x0a36] conflicts with ACPI region ECIO [io 0xa30-0xb2f]
May  9 09:04:47 swordfish kernel: [   21.598505] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May  9 09:04:47 swordfish kernel: [   21.599945] mei: module is from the staging directory, the quality is unknown, you have been warned.
May  9 09:04:47 swordfish kernel: [   21.600181] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [   21.600188] mei 0000:00:16.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [   21.600239] mei 0000:00:16.0: irq 43 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [   21.602023] wmi: Mapper loaded
May  9 09:04:47 swordfish kernel: [   21.607482] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  9 09:04:47 swordfish kernel: [   21.607487] i915 0000:00:02.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [   21.623486] Adding 8297468k swap on /dev/sda5.  Priority:-1 extents:1 across:8297468k 
May  9 09:04:47 swordfish kernel: [   21.634011] type=1400 audit(1336572287.381:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=419 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634017] type=1400 audit(1336572287.381:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634226] type=1400 audit(1336572287.381:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=419 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634234] type=1400 audit(1336572287.381:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634375] type=1400 audit(1336572287.385:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=419 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.634383] type=1400 audit(1336572287.385:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   21.656083] i915 0000:00:02.0: irq 44 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [   21.656087] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
May  9 09:04:47 swordfish kernel: [   21.656088] [drm] Driver supports precise vblank timestamp query.
May  9 09:04:47 swordfish kernel: [   21.656108] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
May  9 09:04:47 swordfish kernel: [   21.668286] it87: Found IT8721F chip at 0xa30, revision 1
May  9 09:04:47 swordfish kernel: [   21.668319] ACPI: resource it87 [io  0x0a35-0x0a36] conflicts with ACPI region ECIO [io 0xa30-0xb2f]
May  9 09:04:47 swordfish kernel: [   21.668320] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
May  9 09:04:47 swordfish kernel: [   21.936107] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  9 09:04:47 swordfish kernel: [   21.962827] fbcon: inteldrmfb (fb0) is primary device
May  9 09:04:47 swordfish kernel: [   21.962892] Console: switching to colour frame buffer device 210x65
May  9 09:04:47 swordfish kernel: [   21.962917] fb0: inteldrmfb frame buffer device
May  9 09:04:47 swordfish kernel: [   21.962918] drm: registered panic notifier
May  9 09:04:47 swordfish kernel: [   21.962925] No ACPI video bus found
May  9 09:04:47 swordfish kernel: [   21.962974] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
May  9 09:04:47 swordfish kernel: [   21.963015] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May  9 09:04:47 swordfish kernel: [   21.963091] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
May  9 09:04:47 swordfish kernel: [   21.963113] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
May  9 09:04:47 swordfish kernel: [   22.014672] init: failsafe main process (762) killed by TERM signal
May  9 09:04:47 swordfish kernel: [   22.026891] Bluetooth: Core ver 2.16
May  9 09:04:47 swordfish kernel: [   22.026903] NET: Registered protocol family 31
May  9 09:04:47 swordfish kernel: [   22.026904] Bluetooth: HCI device and connection manager initialized
May  9 09:04:47 swordfish kernel: [   22.026905] Bluetooth: HCI socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.026906] Bluetooth: L2CAP socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.026909] Bluetooth: SCO socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.027838] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  9 09:04:47 swordfish kernel: [   22.027839] Bluetooth: BNEP filters: protocol multicast
May  9 09:04:47 swordfish kernel: [   22.062219] Bluetooth: RFCOMM TTY layer initialized
May  9 09:04:47 swordfish kernel: [   22.062223] Bluetooth: RFCOMM socket layer initialized
May  9 09:04:47 swordfish kernel: [   22.062224] Bluetooth: RFCOMM ver 1.11
May  9 09:04:47 swordfish kernel: [   22.064576] ppdev: user-space parallel port driver
May  9 09:04:47 swordfish kernel: [   22.069613] type=1400 audit(1336572287.821:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=849 comm="apparmor_parser"
May  9 09:04:47 swordfish kernel: [   22.069864] type=1400 audit(1336572287.821:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=849 comm="apparmor_parser"
May  9 09:04:48 swordfish kernel: [   22.327273] r8169 0000:04:00.0: eth0: link down
May  9 09:04:48 swordfish kernel: [   22.327303] r8169 0000:04:00.0: eth0: link down
May  9 09:04:48 swordfish kernel: [   22.327655] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 09:04:48 swordfish kernel: [   22.327843] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 09:04:48 swordfish kernel: [   22.385367] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
May  9 09:04:48 swordfish kernel: [   22.448223] type=1400 audit(1336572288.201:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=879 comm="apparmor_parser"
May  9 09:04:48 swordfish kernel: [   22.448482] type=1400 audit(1336572288.201:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=886 comm="apparmor_parser"
May  9 09:04:48 swordfish kernel: [   22.509214] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
May  9 09:04:48 swordfish kernel: [   22.509268] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
May  9 09:04:48 swordfish kernel: [   22.509321] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
May  9 09:04:48 swordfish kernel: [   22.509376] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
May  9 09:04:48 swordfish kernel: [   22.509419] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
May  9 09:04:48 swordfish kernel: [   22.509478] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
May  9 09:04:48 swordfish kernel: [   22.509513] input: HDA Intel PCH Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
May  9 09:04:48 swordfish kernel: [   22.740082] init: alsa-restore main process (952) terminated with status 99
May  9 09:04:48 swordfish kernel: [   22.994828] init: plymouth-stop pre-start process (1163) terminated with status 1
May  9 09:04:49 swordfish kernel: [   23.901329] r8169 0000:04:00.0: eth0: link up
May  9 09:04:49 swordfish kernel: [   23.901674] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  9 09:05:00 swordfish kernel: [   34.282135] eth0: no IPv6 routers present

---

