---
title: "help mounting phone in ubuntu"
date: 2010-03-21
forum: General Help
---

### Post by cadogan281 on 2010-03-21
i have a samsung code,windows mobile 6 (cdma) without the micro sd card in it.i want too be able too mount the phone and create an exact copy (dd sector by sector) of the onboard memory to save as a image file.ive looked around and tried different things,but it still cant figure it out.when i type lsusb,this is what shows up:

root@ubuntu:/home/ubuntu# lsusb
Bus 001 Device 004: ID 04e8:6619 Samsung Electronics Co., Ltd MITs Sync
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0461:0010 Primax Electronics, Ltd 
Bus 002 Device 002: ID 0461:4d20 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@ubuntu:/home/ubuntu# 

the mount command brings up this:
root@ubuntu:/etc# mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
root@ubuntu:/etc# 

and df -h gives me this:
root@ubuntu:/etc# df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.5G   46M  1.4G   4% /
udev                  1.5G  232K  1.5G   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  1.5G  220K  1.5G   1% /dev/shm
tmpfs                 1.5G   36K  1.5G   1% /tmp
none                  1.5G   96K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
root@ubuntu:/etc# 


the first device on the list should be the phone.(samsung) i cant enable mass storage on my phone,since the card is in it.and if i put the card in it,that would only access from the card and not internal storage.since it says its plugged in,how would i go about mounting it and making a dd image copy of it?iam also using the ubuntu 9 live version. also i the filesystem on the phone is tfat or vfat.thanks

---

### Post by NightwishFan on 2010-03-21
Can you browse the files on the phone? Also give me the output of:
```
sudo fdisk -l
```

---

### Post by cadogan281 on 2010-03-21
root@ubuntu:/etc# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       59378   476848128    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           59378       60802    11433984    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
root@ubuntu:/etc# 

it wont let me go through the files in ubuntu.i also checked disk utility but its not listed.i guess it would be considered a windows ce o.s. also.

---

### Post by NightwishFan on 2010-03-21
Can you edit the files on the phone in something else like Windows? You may not be able to.

---

### Post by cadogan281 on 2010-03-21
no i tried that also.there is a setting in the phone too turn on active sync or mass storage.i tried mass storage too see if it would fix it,but doesnt let me cause there is no memory card.is it cause ubuntu cant handle the windows cd/tfat file systems?

---

### Post by NightwishFan on 2010-03-21
No, it handles them fine. It just isn't appearing as a mount point.

Try this. Disconnect the phone, and open the Log Viewer under System -> Administration. Watch the SYSLOG and plug your phone in. Post the related output that occurs when you connect it. It may highlight in black.

---

### Post by cadogan281 on 2010-03-21
here is the syslog info:

Mar 21 08:26:48 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 21 08:26:48 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1358" x-info="http://www.rsyslog.com"] (re)start
Mar 21 08:26:48 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Mar 21 08:26:48 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Mar 21 08:26:48 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ee0000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ef0000 - 00000000b7f00000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b8000000 - 00000000c0000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] DMI present.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] last_pfn = 0xb7ee0 max_arch_pfn = 0x100000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Mar 21 08:26:48 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
Mar 21 08:26:48 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   2 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   3 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   4 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   5 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   6 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   7 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 21 08:26:48 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000b7ee0000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ef0000 - 00000000b7f00000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b8000000 - 00000000c0000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Mar 21 08:26:48 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] RAMDISK: 7fa82000 - 7ffff098
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007fa82000 - 000000007ffff097 to 008ad000 - 00e2a097
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: RSDP 000f7500 00024 (v02 HPQOEM)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: XSDT b7ee3100 00054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: FACP b7ee7e80 000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: DSDT b7ee32c0 04B61 (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: FACS b7ee0000 00040
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: SLIC b7ee80c0 00176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: SSDT b7ee8280 0095E (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: HPET b7ee8c40 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: MCFG b7ee8cc0 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: APIC b7ee7fc0 00098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] 2054MB HIGHMEM available.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Mar 21 08:26:48 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #5 [00008a9000 - 00008ac5b0]              BRK ==> [00008a9000 - 00008ac5b0]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f53c0] f53c0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x000b7ee0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 21 08:26:48 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000b7ee0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] On node 0 totalpages: 753263
Mar 21 08:26:48 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem zone: 4110 pages used for memmap
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem zone: 521940 pages, LIFO batch:31
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using APIC driver default
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Mar 21 08:26:48 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages at c2710000, static data 35612 bytes
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747377
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] allocated 15067200 bytes of page_cgroup
Mar 21 08:26:48 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000b7ee0)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Memory: 2959336k/3013504k available (4565k kernel code, 52852k reserved, 2143k data, 540k init, 2104200k highmem)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 21 08:26:48 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Detected 2712.787 MHz processor.
Mar 21 08:26:48 ubuntu kernel: [    0.000011] spurious 8259A interrupt: IRQ7.
Mar 21 08:26:48 ubuntu kernel: [    0.003280] Console: colour VGA+ 80x25
Mar 21 08:26:48 ubuntu kernel: [    0.003282] console [tty0] enabled
Mar 21 08:26:48 ubuntu kernel: [    0.003415] hpet clockevent registered
Mar 21 08:26:48 ubuntu kernel: [    0.003417] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Mar 21 08:26:48 ubuntu kernel: [    0.003423] Calibrating delay loop (skipped), value calculated using timer frequency.. 5425.57 BogoMIPS (lpj=10851148)
Mar 21 08:26:48 ubuntu kernel: [    0.003436] Security Framework initialized
Mar 21 08:26:48 ubuntu kernel: [    0.003450] AppArmor: AppArmor initialized
Mar 21 08:26:48 ubuntu kernel: [    0.003456] Mount-cache hash table entries: 512
Mar 21 08:26:48 ubuntu kernel: [    0.003539] Initializing cgroup subsys ns
Mar 21 08:26:48 ubuntu kernel: [    0.003542] Initializing cgroup subsys cpuacct
Mar 21 08:26:48 ubuntu kernel: [    0.003545] Initializing cgroup subsys memory
Mar 21 08:26:48 ubuntu kernel: [    0.003549] Initializing cgroup subsys freezer
Mar 21 08:26:48 ubuntu kernel: [    0.003551] Initializing cgroup subsys net_cls
Mar 21 08:26:48 ubuntu kernel: [    0.003560] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.003562] CPU: L2 Cache: 512K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.003564] CPU: Physical Processor ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.003565] CPU: Processor Core ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.003567] mce: CPU supports 6 MCE banks
Mar 21 08:26:48 ubuntu kernel: [    0.003574] using C1E aware idle routine
Mar 21 08:26:48 ubuntu kernel: [    0.003579] Performance Counters: AMD PMU driver.
Mar 21 08:26:48 ubuntu kernel: [    0.003584] ... version:                 0
Mar 21 08:26:48 ubuntu kernel: [    0.003585] ... bit width:               48
Mar 21 08:26:48 ubuntu kernel: [    0.003586] ... generic counters:        4
Mar 21 08:26:48 ubuntu kernel: [    0.003588] ... value mask:              0000ffffffffffff
Mar 21 08:26:48 ubuntu kernel: [    0.003589] ... max period:              00007fffffffffff
Mar 21 08:26:48 ubuntu kernel: [    0.003591] ... fixed-purpose counters:  0
Mar 21 08:26:48 ubuntu kernel: [    0.003592] ... counter mask:            000000000000000f
Mar 21 08:26:48 ubuntu kernel: [    0.003595] Checking 'hlt' instruction... OK.
Mar 21 08:26:48 ubuntu kernel: [    0.017599] ACPI: Core revision 20090521
Mar 21 08:26:48 ubuntu kernel: [    0.024515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 21 08:26:48 ubuntu kernel: [    0.066966] CPU0: AMD Athlon(tm) II X2 215 Processor stepping 02
Mar 21 08:26:48 ubuntu kernel: [    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
Mar 21 08:26:48 ubuntu kernel: [    0.004000] Initializing CPU#1
Mar 21 08:26:48 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 5424.64 BogoMIPS (lpj=10849283)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Mar 21 08:26:48 ubuntu kernel: [    0.004000] mce: CPU supports 6 MCE banks
Mar 21 08:26:48 ubuntu kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Mar 21 08:26:48 ubuntu kernel: [    0.152484] CPU1: AMD Athlon(tm) II X2 215 Processor stepping 02
Mar 21 08:26:48 ubuntu kernel: [    0.152494] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 21 08:26:48 ubuntu kernel: [    0.156010] Brought up 2 CPUs
Mar 21 08:26:48 ubuntu kernel: [    0.156012] Total of 2 processors activated (10850.21 BogoMIPS).
Mar 21 08:26:48 ubuntu kernel: [    0.156092] CPU0 attaching sched-domain:
Mar 21 08:26:48 ubuntu kernel: [    0.156094]  domain 0: span 0-1 level MC
Mar 21 08:26:48 ubuntu kernel: [    0.156096]   groups: 0 1
Mar 21 08:26:48 ubuntu kernel: [    0.156100] CPU1 attaching sched-domain:
Mar 21 08:26:48 ubuntu kernel: [    0.156101]  domain 0: span 0-1 level MC
Mar 21 08:26:48 ubuntu kernel: [    0.156103]   groups: 1 0
Mar 21 08:26:48 ubuntu kernel: [    0.156158] Booting paravirtualized kernel on bare hardware
Mar 21 08:26:48 ubuntu kernel: [    0.156158] regulator: core version 0.5
Mar 21 08:26:48 ubuntu kernel: [    0.156158] Time:  8:25:25  Date: 03/21/10
Mar 21 08:26:48 ubuntu kernel: [    0.156158] NET: Registered protocol family 16
Mar 21 08:26:48 ubuntu kernel: [    0.156164] EISA bus registered
Mar 21 08:26:48 ubuntu kernel: [    0.156176] ACPI: bus type pci registered
Mar 21 08:26:48 ubuntu kernel: [    0.156229] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Mar 21 08:26:48 ubuntu kernel: [    0.156232] PCI: MCFG area at f0000000 reserved in E820
Mar 21 08:26:48 ubuntu kernel: [    0.156233] PCI: Using MMCONFIG for extended config space
Mar 21 08:26:48 ubuntu kernel: [    0.156235] PCI: Using configuration type 1 for base access
Mar 21 08:26:48 ubuntu kernel: [    0.156818] bio: create slab <bio-0> at 0
Mar 21 08:26:48 ubuntu kernel: [    0.156818] ACPI: EC: Look up EC in DSDT
Mar 21 08:26:48 ubuntu kernel: [    0.164071] ACPI: Interpreter enabled
Mar 21 08:26:48 ubuntu kernel: [    0.164077] ACPI: (supports S0 S1 S3 S4 S5)
Mar 21 08:26:48 ubuntu kernel: [    0.164098] ACPI: Using IOAPIC for interrupt routing
Mar 21 08:26:48 ubuntu kernel: [    0.168675] ACPI: No dock devices found.
Mar 21 08:26:48 ubuntu kernel: [    0.168766] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 21 08:26:48 ubuntu kernel: [    0.168959] pci 0000:00:01.1: reg 10 io port: [0xff00-0xff3f]
Mar 21 08:26:48 ubuntu kernel: [    0.168969] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
Mar 21 08:26:48 ubuntu kernel: [    0.168972] pci 0000:00:01.1: reg 24 io port: [0x1c40-0x1c7f]
Mar 21 08:26:48 ubuntu kernel: [    0.168990] pci 0000:00:01.1: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.168995] pci 0000:00:01.1: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169037] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169057] pci 0000:00:02.0: supports D1 D2
Mar 21 08:26:48 ubuntu kernel: [    0.169059] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169061] pci 0000:00:02.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169081] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
Mar 21 08:26:48 ubuntu kernel: [    0.169104] pci 0000:00:02.1: supports D1 D2
Mar 21 08:26:48 ubuntu kernel: [    0.169106] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169109] pci 0000:00:02.1: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169161] pci 0000:00:05.0: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
Mar 21 08:26:48 ubuntu kernel: [    0.169185] pci 0000:00:05.0: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169188] pci 0000:00:05.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169216] pci 0000:00:07.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169219] pci 0000:00:07.0: reg 14 io port: [0xfc00-0xfc07]
Mar 21 08:26:48 ubuntu kernel: [    0.169239] pci 0000:00:07.0: supports D1 D2
Mar 21 08:26:48 ubuntu kernel: [    0.169240] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169244] pci 0000:00:07.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169262] pci 0000:00:08.0: reg 10 io port: [0x9f0-0x9f7]
Mar 21 08:26:48 ubuntu kernel: [    0.169265] pci 0000:00:08.0: reg 14 io port: [0xbf0-0xbf3]
Mar 21 08:26:48 ubuntu kernel: [    0.169268] pci 0000:00:08.0: reg 18 io port: [0x970-0x977]
Mar 21 08:26:48 ubuntu kernel: [    0.169271] pci 0000:00:08.0: reg 1c io port: [0xb70-0xb73]
Mar 21 08:26:48 ubuntu kernel: [    0.169274] pci 0000:00:08.0: reg 20 io port: [0xf700-0xf70f]
Mar 21 08:26:48 ubuntu kernel: [    0.169277] pci 0000:00:08.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169304] pci 0000:00:08.1: reg 10 io port: [0x9e0-0x9e7]
Mar 21 08:26:48 ubuntu kernel: [    0.169307] pci 0000:00:08.1: reg 14 io port: [0xbe0-0xbe3]
Mar 21 08:26:48 ubuntu kernel: [    0.169310] pci 0000:00:08.1: reg 18 io port: [0x960-0x967]
Mar 21 08:26:48 ubuntu kernel: [    0.169313] pci 0000:00:08.1: reg 1c io port: [0xb60-0xb63]
Mar 21 08:26:48 ubuntu kernel: [    0.169316] pci 0000:00:08.1: reg 20 io port: [0xf200-0xf20f]
Mar 21 08:26:48 ubuntu kernel: [    0.169319] pci 0000:00:08.1: reg 24 32bit mmio: [0xfe02b000-0xfe02bfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169360] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169362] pci 0000:00:09.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169389] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169391] pci 0000:00:0b.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169418] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169420] pci 0000:00:0c.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169434] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169438] pci 0000:00:0d.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169442] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169446] pci 0000:00:0d.0: reg 30 32bit mmio: [0x000000-0x01ffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169551] pci 0000:00:04.0: transparent bridge
Mar 21 08:26:48 ubuntu kernel: [    0.169554] pci 0000:00:04.0: bridge io port: [0xe000-0xefff]
Mar 21 08:26:48 ubuntu kernel: [    0.169556] pci 0000:00:04.0: bridge 32bit mmio: [0xfd700000-0xfd7fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169559] pci 0000:00:04.0: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169591] pci 0000:00:09.0: bridge io port: [0xd000-0xdfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169593] pci 0000:00:09.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169596] pci 0000:00:09.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169628] pci 0000:00:0b.0: bridge io port: [0xc000-0xcfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169630] pci 0000:00:0b.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169633] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169662] pci 0000:04:00.0: reg 10 64bit mmio: [0xfd9ff000-0xfd9fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169698] pci 0000:04:00.0: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169701] pci 0000:04:00.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169739] pci 0000:00:0c.0: bridge io port: [0xb000-0xbfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169741] pci 0000:00:0c.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169744] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169751] pci_bus 0000:00: on NUMA node 0
Mar 21 08:26:48 ubuntu kernel: [    0.169754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 21 08:26:48 ubuntu kernel: [    0.169890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Mar 21 08:26:48 ubuntu kernel: [    0.197392] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197489] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197583] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197677] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197772] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.197866] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197959] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198053] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198149] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198242] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198337] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198432] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198528] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198622] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198717] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198812] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198908] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199003] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.199099] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.199226] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199348] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199469] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199589] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199708] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Mar 21 08:26:48 ubuntu kernel: [    0.199828] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199949] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200077] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200197] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200317] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200439] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200564] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200688] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200808] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200928] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201048] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.201169] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.201290] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201410] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201539] SCSI subsystem initialized
Mar 21 08:26:48 ubuntu kernel: [    0.201579] libata version 3.00 loaded.
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new interface driver usbfs
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new interface driver hub
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new device driver usb
Mar 21 08:26:48 ubuntu kernel: [    0.201579] ACPI: WMI: Mapper loaded
Mar 21 08:26:48 ubuntu kernel: [    0.201579] PCI: Using ACPI for IRQ routing
Mar 21 08:26:48 ubuntu kernel: [    0.212006] Bluetooth: Core ver 2.15
Mar 21 08:26:48 ubuntu kernel: [    0.212015] NET: Registered protocol family 31
Mar 21 08:26:48 ubuntu kernel: [    0.212015] Bluetooth: HCI device and connection manager initialized
Mar 21 08:26:48 ubuntu kernel: [    0.212015] Bluetooth: HCI socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    0.212016] NetLabel: Initializing
Mar 21 08:26:48 ubuntu kernel: [    0.212017] NetLabel:  domain hash size = 128
Mar 21 08:26:48 ubuntu kernel: [    0.212019] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 21 08:26:48 ubuntu kernel: [    0.212028] NetLabel:  unlabeled traffic allowed by default
Mar 21 08:26:48 ubuntu kernel: [    0.212052] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
Mar 21 08:26:48 ubuntu kernel: [    0.212055] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Mar 21 08:26:48 ubuntu kernel: [    0.228008] pnp: PnP ACPI init
Mar 21 08:26:48 ubuntu kernel: [    0.228025] ACPI: bus type pnp registered
Mar 21 08:26:48 ubuntu kernel: [    0.229898] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) 20090521 dsopcode-596
Mar 21 08:26:48 ubuntu kernel: [    0.229904] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.MEM_._CRS] (Node f7017f60), AE_AML_BUFFER_LIMIT
Mar 21 08:26:48 ubuntu kernel: [    0.229924] ACPI Error (uteval-0256): Method execution failed [\_SB_.MEM_._CRS] (Node f7017f60), AE_AML_BUFFER_LIMIT
Mar 21 08:26:48 ubuntu kernel: [    0.229930] pnp 00:09: can't evaluate _CRS: 12298
Mar 21 08:26:48 ubuntu kernel: [    0.229966] pnp: PnP ACPI: found 10 devices
Mar 21 08:26:48 ubuntu kernel: [    0.229967] ACPI: ACPI bus type pnp unregistered
Mar 21 08:26:48 ubuntu kernel: [    0.229970] PnPBIOS: Disabled by ACPI PNP
Mar 21 08:26:48 ubuntu kernel: [    0.229979] system 00:01: ioport range 0x1000-0x107f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229981] system 00:01: ioport range 0x1080-0x10ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229983] system 00:01: ioport range 0x1400-0x147f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229985] system 00:01: ioport range 0x1480-0x14ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229987] system 00:01: ioport range 0x1800-0x187f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229989] system 00:01: ioport range 0x1880-0x18ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229993] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229995] system 00:02: ioport range 0x800-0x87f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229997] system 00:02: ioport range 0x294-0x297 has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.230002] system 00:08: iomem range 0xf0000000-0xf3ffffff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.264619] AppArmor: AppArmor Filesystem Enabled
Mar 21 08:26:48 ubuntu kernel: [    0.264642] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Mar 21 08:26:48 ubuntu kernel: [    0.264644] pci 0000:00:04.0:   IO window: 0xe000-0xefff
Mar 21 08:26:48 ubuntu kernel: [    0.264647] pci 0000:00:04.0:   MEM window: 0xfd700000-0xfd7fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264650] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
Mar 21 08:26:48 ubuntu kernel: [    0.264654] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Mar 21 08:26:48 ubuntu kernel: [    0.264656] pci 0000:00:09.0:   IO window: 0xd000-0xdfff
Mar 21 08:26:48 ubuntu kernel: [    0.264658] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264661] pci 0000:00:09.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264663] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Mar 21 08:26:48 ubuntu kernel: [    0.264665] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
Mar 21 08:26:48 ubuntu kernel: [    0.264668] pci 0000:00:0b.0:   MEM window: 0xfdb00000-0xfdbfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264670] pci 0000:00:0b.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
Mar 21 08:26:48 ubuntu kernel: [    0.264673] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Mar 21 08:26:48 ubuntu kernel: [    0.264675] pci 0000:00:0c.0:   IO window: 0xb000-0xbfff
Mar 21 08:26:48 ubuntu kernel: [    0.264677] pci 0000:00:0c.0:   MEM window: 0xfd900000-0xfd9fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264679] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264687] pci 0000:00:04.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264691] pci 0000:00:09.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264694] pci 0000:00:0b.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264697] pci 0000:00:0c.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264701] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264703] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264705] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Mar 21 08:26:48 ubuntu kernel: [    0.264706] pci_bus 0000:01: resource 1 mem: [0xfd700000-0xfd7fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264708] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264710] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264712] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264714] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Mar 21 08:26:48 ubuntu kernel: [    0.264716] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264717] pci_bus 0000:02: resource 2 pref mem [0xfdc00000-0xfdcfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264719] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
Mar 21 08:26:48 ubuntu kernel: [    0.264721] pci_bus 0000:03: resource 1 mem: [0xfdb00000-0xfdbfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264723] pci_bus 0000:03: resource 2 pref mem [0xfda00000-0xfdafffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264725] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
Mar 21 08:26:48 ubuntu kernel: [    0.264727] pci_bus 0000:04: resource 1 mem: [0xfd900000-0xfd9fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264729] pci_bus 0000:04: resource 2 pref mem [0xfd800000-0xfd8fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264756] NET: Registered protocol family 2
Mar 21 08:26:48 ubuntu kernel: [    0.264826] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265050] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265516] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265732] TCP: Hash tables configured (established 131072 bind 65536)
Mar 21 08:26:48 ubuntu kernel: [    0.265734] TCP reno registered
Mar 21 08:26:48 ubuntu kernel: [    0.265804] NET: Registered protocol family 1
Mar 21 08:26:48 ubuntu kernel: [    0.265853] Trying to unpack rootfs image as initramfs...
Mar 21 08:26:48 ubuntu kernel: [    0.500482] Switched to high resolution mode on CPU 1
Mar 21 08:26:48 ubuntu kernel: [    0.503953] Switched to high resolution mode on CPU 0
Mar 21 08:26:48 ubuntu kernel: [    1.240431] Freeing initrd memory: 5620k freed
Mar 21 08:26:48 ubuntu kernel: [    1.242588] cpufreq-nforce2: No nForce2 chipset.
Mar 21 08:26:48 ubuntu kernel: [    1.242606] Scanning for low memory corruption every 60 seconds
Mar 21 08:26:48 ubuntu kernel: [    1.242679] audit: initializing netlink socket (disabled)
Mar 21 08:26:48 ubuntu kernel: [    1.242690] type=2000 audit(1269159926.240:1): initialized
Mar 21 08:26:48 ubuntu kernel: [    1.248960] highmem bounce pool size: 64 pages
Mar 21 08:26:48 ubuntu kernel: [    1.248964] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 21 08:26:48 ubuntu kernel: [    1.249902] VFS: Disk quotas dquot_6.5.2
Mar 21 08:26:48 ubuntu kernel: [    1.249942] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 21 08:26:48 ubuntu kernel: [    1.250322] fuse init (API version 7.12)
Mar 21 08:26:48 ubuntu kernel: [    1.250377] msgmni has been set to 1682
Mar 21 08:26:48 ubuntu kernel: [    1.250546] alg: No test for stdrng (krng)
Mar 21 08:26:48 ubuntu kernel: [    1.250567] io scheduler noop registered
Mar 21 08:26:48 ubuntu kernel: [    1.250569] io scheduler anticipatory registered
Mar 21 08:26:48 ubuntu kernel: [    1.250570] io scheduler deadline registered
Mar 21 08:26:48 ubuntu kernel: [    1.250600] io scheduler cfq registered (default)
Mar 21 08:26:48 ubuntu kernel: [    1.250698] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250743] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250792] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250843] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250894] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250949] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251008] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251071] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251075] pci 0000:00:0d.0: Boot video device
Mar 21 08:26:48 ubuntu kernel: [    1.251149]   alloc irq_desc for 24 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251151]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251157] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X
Mar 21 08:26:48 ubuntu kernel: [    1.251162] pcieport-driver 0000:00:09.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.251217]   alloc irq_desc for 25 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251218]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251221] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X
Mar 21 08:26:48 ubuntu kernel: [    1.251225] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.251275]   alloc irq_desc for 26 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251276]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251279] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X
Mar 21 08:26:48 ubuntu kernel: [    1.251282] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.251322] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 21 08:26:48 ubuntu kernel: [    1.251340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 21 08:26:48 ubuntu kernel: [    1.251425] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 21 08:26:48 ubuntu kernel: [    1.251428] ACPI: Power Button [PWRF]
Mar 21 08:26:48 ubuntu kernel: [    1.251464] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Mar 21 08:26:48 ubuntu kernel: [    1.251466] ACPI: Power Button [PWRB]
Mar 21 08:26:48 ubuntu kernel: [    1.251506] fan PNP0C0B:00: registered as cooling_device0
Mar 21 08:26:48 ubuntu kernel: [    1.251509] ACPI: Fan [FAN] (on)
Mar 21 08:26:48 ubuntu kernel: [    1.251734] processor LNXCPU:00: registered as cooling_device1
Mar 21 08:26:48 ubuntu kernel: [    1.251760] processor LNXCPU:01: registered as cooling_device2
Mar 21 08:26:48 ubuntu kernel: [    1.253978] ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference 20090521 nspredef-946
Mar 21 08:26:48 ubuntu kernel: [    1.253984] ACPI: Expecting a [Reference] package element, found type 0
Mar 21 08:26:48 ubuntu kernel: [    1.253985] ACPI: Invalid passive threshold
Mar 21 08:26:48 ubuntu kernel: [    1.254214] thermal LNXTHERM:01: registered as thermal_zone0
Mar 21 08:26:48 ubuntu kernel: [    1.254218] ACPI: Thermal Zone [THRM] (40 C)
Mar 21 08:26:48 ubuntu kernel: [    1.254258] isapnp: Scanning for PnP cards...
Mar 21 08:26:48 ubuntu kernel: [    1.606935] isapnp: No Plug & Play device found
Mar 21 08:26:48 ubuntu kernel: [    1.607732] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 21 08:26:48 ubuntu kernel: [    1.608513] brd: module loaded
Mar 21 08:26:48 ubuntu kernel: [    1.608787] loop: module loaded
Mar 21 08:26:48 ubuntu kernel: [    1.608839] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Mar 21 08:26:48 ubuntu kernel: [    1.608968] sata_nv 0000:00:08.0: version 3.5
Mar 21 08:26:48 ubuntu kernel: [    1.609204] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Mar 21 08:26:48 ubuntu kernel: [    1.609208]   alloc irq_desc for 20 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609210]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609219] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Mar 21 08:26:48 ubuntu kernel: [    1.609246] sata_nv 0000:00:08.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.609330] scsi0 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609406] scsi1 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609508] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf700 irq 20
Mar 21 08:26:48 ubuntu kernel: [    1.609510] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf708 irq 20
Mar 21 08:26:48 ubuntu kernel: [    1.609717] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
Mar 21 08:26:48 ubuntu kernel: [    1.609719]   alloc irq_desc for 21 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609721]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609727] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 21 (level, low) -> IRQ 21
Mar 21 08:26:48 ubuntu kernel: [    1.609746] sata_nv 0000:00:08.1: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.609863] scsi2 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609900] scsi3 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609994] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf200 irq 21
Mar 21 08:26:48 ubuntu kernel: [    1.609996] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf208 irq 21
Mar 21 08:26:48 ubuntu kernel: [    1.610485] Fixed MDIO Bus: probed
Mar 21 08:26:48 ubuntu kernel: [    1.610507] PPP generic driver version 2.4.2
Mar 21 08:26:48 ubuntu kernel: [    1.610577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 21 08:26:48 ubuntu kernel: [    1.610786] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    1.610788]   alloc irq_desc for 23 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.610789]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.610795] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    1.610803] ehci_hcd 0000:00:02.1: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.610805] ehci_hcd 0000:00:02.1: EHCI Host Controller
Mar 21 08:26:48 ubuntu kernel: [    1.610840] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Mar 21 08:26:48 ubuntu kernel: [    1.610862] ehci_hcd 0000:00:02.1: debug port 1
Mar 21 08:26:48 ubuntu kernel: [    1.610866] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Mar 21 08:26:48 ubuntu kernel: [    1.610880] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
Mar 21 08:26:48 ubuntu kernel: [    1.621189] ata3: SATA link down (SStatus 0 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.624531] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Mar 21 08:26:48 ubuntu kernel: [    1.624620] usb usb1: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    1.624640] hub 1-0:1.0: USB hub found
Mar 21 08:26:48 ubuntu kernel: [    1.624646] hub 1-0:1.0: 10 ports detected
Mar 21 08:26:48 ubuntu kernel: [    1.624701] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 21 08:26:48 ubuntu kernel: [    1.624952] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Mar 21 08:26:48 ubuntu kernel: [    1.624956]   alloc irq_desc for 22 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.624957]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.624966] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
Mar 21 08:26:48 ubuntu kernel: [    1.624979] ohci_hcd 0000:00:02.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.624981] ohci_hcd 0000:00:02.0: OHCI Host Controller
Mar 21 08:26:48 ubuntu kernel: [    1.625005] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Mar 21 08:26:48 ubuntu kernel: [    1.625029] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfe02f000
Mar 21 08:26:48 ubuntu kernel: [    1.682027] usb usb2: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    1.682043] hub 2-0:1.0: USB hub found
Mar 21 08:26:48 ubuntu kernel: [    1.682049] hub 2-0:1.0: 10 ports detected
Mar 21 08:26:48 ubuntu kernel: [    1.682087] uhci_hcd: USB Universal Host Controller Interface driver
Mar 21 08:26:48 ubuntu kernel: [    1.682145] PNP: No PS/2 controller found. Probing ports directly.
Mar 21 08:26:48 ubuntu kernel: [    1.684313] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 21 08:26:48 ubuntu kernel: [    1.684318] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 21 08:26:48 ubuntu kernel: [    1.684355] mice: PS/2 mouse device common for all mice
Mar 21 08:26:48 ubuntu kernel: [    1.684417] rtc_cmos 00:05: RTC can wake from S4
Mar 21 08:26:48 ubuntu kernel: [    1.684444] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Mar 21 08:26:48 ubuntu kernel: [    1.684480] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Mar 21 08:26:48 ubuntu kernel: [    1.684551] device-mapper: uevent: version 1.0.3
Mar 21 08:26:48 ubuntu kernel: [    1.684645] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Mar 21 08:26:48 ubuntu kernel: [    1.684715] device-mapper: multipath: version 1.1.0 loaded
Mar 21 08:26:48 ubuntu kernel: [    1.684718] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 21 08:26:48 ubuntu kernel: [    1.684800] EISA: Probing bus 0 at eisa.0
Mar 21 08:26:48 ubuntu kernel: [    1.684804] Cannot allocate resource for EISA slot 1
Mar 21 08:26:48 ubuntu kernel: [    1.684821] EISA: Detected 0 cards.
Mar 21 08:26:48 ubuntu kernel: [    1.684904] cpuidle: using governor ladder
Mar 21 08:26:48 ubuntu kernel: [    1.684905] cpuidle: using governor menu
Mar 21 08:26:48 ubuntu kernel: [    1.685246] TCP cubic registered
Mar 21 08:26:48 ubuntu kernel: [    1.685347] NET: Registered protocol family 10
Mar 21 08:26:48 ubuntu kernel: [    1.685656] lo: Disabled Privacy Extensions
Mar 21 08:26:48 ubuntu kernel: [    1.685879] NET: Registered protocol family 17
Mar 21 08:26:48 ubuntu kernel: [    1.685891] Bluetooth: L2CAP ver 2.13
Mar 21 08:26:48 ubuntu kernel: [    1.685892] Bluetooth: L2CAP socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685894] Bluetooth: SCO (Voice Link) ver 0.6
Mar 21 08:26:48 ubuntu kernel: [    1.685896] Bluetooth: SCO socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685937] Bluetooth: RFCOMM TTY layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685939] Bluetooth: RFCOMM socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685940] Bluetooth: RFCOMM ver 1.11
Mar 21 08:26:48 ubuntu kernel: [    1.685956] powernow-k8: Found 1 AMD Athlon(tm) II X2 215 Processor processors (2 cpu cores) (version 2.20.00)
Mar 21 08:26:48 ubuntu kernel: [    1.685988] powernow-k8:    0 : pstate 0 (2700 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685990] powernow-k8:    1 : pstate 1 (2100 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685991] powernow-k8:    2 : pstate 2 (1500 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685993] powernow-k8:    3 : pstate 3 (800 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.686106] Using IPI No-Shortcut mode
Mar 21 08:26:48 ubuntu kernel: [    1.686153] PM: Resume from disk failed.
Mar 21 08:26:48 ubuntu kernel: [    1.686161] registered taskstats version 1
Mar 21 08:26:48 ubuntu kernel: [    1.686249]   Magic number: 2:779:422
Mar 21 08:26:48 ubuntu kernel: [    1.686341] rtc_cmos 00:05: setting system clock to 2010-03-21 08:25:27 UTC (1269159927)
Mar 21 08:26:48 ubuntu kernel: [    1.686345] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 21 08:26:48 ubuntu kernel: [    1.686347] EDD information not available.
Mar 21 08:26:48 ubuntu kernel: [    1.764043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.788144] ata1.00: ATA-8: Hitachi HDP725050GLA360, GM4OA57A, max UDMA/133
Mar 21 08:26:48 ubuntu kernel: [    1.788147] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 21 08:26:48 ubuntu kernel: [    1.804151] ata1.00: configured for UDMA/133
Mar 21 08:26:48 ubuntu kernel: [    1.804270] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
Mar 21 08:26:48 ubuntu kernel: [    1.804376] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 21 08:26:48 ubuntu kernel: [    1.804404] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Mar 21 08:26:48 ubuntu kernel: [    1.804430] sd 0:0:0:0: [sda] Write Protect is off
Mar 21 08:26:48 ubuntu kernel: [    1.804432] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 21 08:26:48 ubuntu kernel: [    1.804445] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 21 08:26:48 ubuntu kernel: [    1.804535]  sda: sda1 sda2 sda3
Mar 21 08:26:48 ubuntu kernel: [    1.827930] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 21 08:26:48 ubuntu kernel: [    1.960044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.968141] ata2.00: ATAPI: hp      DVD-RAM GH40L, RB0A, max UDMA/100
Mar 21 08:26:48 ubuntu kernel: [    1.984154] ata2.00: configured for UDMA/100
Mar 21 08:26:48 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Mar 21 08:26:48 ubuntu kernel: [    1.989783] scsi 1:0:0:0: CD-ROM            hp       DVD-RAM GH40L    RB0A PQ: 0 ANSI: 5
Mar 21 08:26:48 ubuntu kernel: [    1.994047] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 21 08:26:48 ubuntu kernel: [    1.994049] Uniform CD-ROM driver Revision: 3.20
Mar 21 08:26:48 ubuntu kernel: [    1.994114] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 21 08:26:48 ubuntu kernel: [    1.994150] sr 1:0:0:0: Attached scsi generic sg1 type 5
Mar 21 08:26:48 ubuntu kernel: [    2.004462] ata4: SATA link down (SStatus 0 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    2.004512] Freeing unused kernel memory: 540k freed
Mar 21 08:26:48 ubuntu kernel: [    2.004737] Write protecting the kernel text: 4568k
Mar 21 08:26:48 ubuntu kernel: [    2.004764] Write protecting the kernel read-only data: 1836k
Mar 21 08:26:48 ubuntu kernel: [    2.052535] usb 1-5: new high speed USB device using ehci_hcd and address 4
Mar 21 08:26:48 ubuntu kernel: [    2.095329] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Mar 21 08:26:48 ubuntu kernel: [    2.095602] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    2.095607] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    2.095611] forcedeth 0000:00:07.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    2.190522] usb 1-5: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    2.492032] usb 2-1: new low speed USB device using ohci_hcd and address 2
Mar 21 08:26:48 ubuntu kernel: [    2.612905] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:e6:ba:14:d8:36
Mar 21 08:26:48 ubuntu kernel: [    2.612910] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Mar 21 08:26:48 ubuntu kernel: [    2.721938] usb 2-1: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    2.728674] usbcore: registered new interface driver hiddev
Mar 21 08:26:48 ubuntu kernel: [    2.734020] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
Mar 21 08:26:48 ubuntu kernel: [    2.734078] generic-usb 0003:0461:4D20.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:02.0-1/input0
Mar 21 08:26:48 ubuntu kernel: [    2.734092] usbcore: registered new interface driver usbhid
Mar 21 08:26:48 ubuntu kernel: [    2.734094] usbhid: v2.6:USB HID core driver
Mar 21 08:26:48 ubuntu kernel: [    3.023623] xor: automatically using best checksumming function: pIII_sse
Mar 21 08:26:48 ubuntu kernel: [    3.028515] usb 2-2: new low speed USB device using ohci_hcd and address 3
Mar 21 08:26:48 ubuntu kernel: [    3.040003]    pIII_sse  : 10878.000 MB/sec
Mar 21 08:26:48 ubuntu kernel: [    3.040006] xor: using function: pIII_sse (10878.000 MB/sec)
Mar 21 08:26:48 ubuntu kernel: [    3.041713] device-mapper: dm-raid45: initialized v0.2594b
Mar 21 08:26:48 ubuntu kernel: [    3.229858] usb 2-2: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    3.240230] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
Mar 21 08:26:48 ubuntu kernel: [    3.240286] generic-usb 0003:0461:0010.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:02.0-2/input0
Mar 21 08:26:48 ubuntu kernel: [    3.252832] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input5
Mar 21 08:26:48 ubuntu kernel: [    3.252887] generic-usb 0003:0461:0010.0003: input,hidraw2: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:02.0-2/input1
Mar 21 08:26:48 ubuntu kernel: [    5.289275] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar 21 08:26:48 ubuntu kernel: [    5.391253] ISO 9660 Extensions: RRIP_1991A
Mar 21 08:26:48 ubuntu kernel: [    5.684341] aufs 2-standalone.tree-30-20090727
Mar 21 08:26:48 ubuntu kernel: [    5.918524] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Mar 21 08:26:48 ubuntu kernel: [   82.929313] udev: starting version 147
Mar 21 08:26:50 ubuntu kernel: [   84.668498] usbcore: registered new interface driver usbserial
Mar 21 08:26:50 ubuntu kernel: [   84.668513] USB Serial support registered for generic
Mar 21 08:26:50 ubuntu kernel: [   84.668533] usbcore: registered new interface driver usbserial_generic
Mar 21 08:26:50 ubuntu kernel: [   84.668535] usbserial: USB Serial Driver core
Mar 21 08:26:50 ubuntu kernel: [   85.052266] USB Serial support registered for PocketPC PDA
Mar 21 08:26:50 ubuntu kernel: [   85.052290] ipaq 1-5:1.0: PocketPC PDA converter detected
Mar 21 08:26:50 ubuntu kernel: [   85.053074] usb 1-5: PocketPC PDA converter now attached to ttyUSB0
Mar 21 08:26:50 ubuntu kernel: [   85.053099] usbcore: registered new interface driver ipaq
Mar 21 08:26:50 ubuntu kernel: [   85.053102] ipaq: v0.5:USB PocketPC PDA driver
Mar 21 08:26:51 ubuntu avahi-daemon[1700]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Mar 21 08:26:51 ubuntu avahi-daemon[1700]: Successfully dropped root privileges.
Mar 21 08:26:51 ubuntu avahi-daemon[1700]: avahi-daemon 0.6.25 starting up.
Mar 21 08:26:51 ubuntu kernel: [   85.605461] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Mar 21 08:26:51 ubuntu kernel: [   85.605476] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
Mar 21 08:26:52 ubuntu avahi-daemon[1700]: Successfully called chroot().
Mar 21 08:26:52 ubuntu avahi-daemon[1700]: Successfully dropped remaining capabilities.
Mar 21 08:26:54 ubuntu avahi-daemon[1701]: chroot.c: open() failed: No such file or directory
Mar 21 08:26:54 ubuntu avahi-daemon[1700]: Failed to open /etc/resolv.conf: Invalid argument
Mar 21 08:26:54 ubuntu avahi-daemon[1700]: No service file found in /etc/avahi/services.
Mar 21 08:26:54 ubuntu avahi-daemon[1700]: Network interface enumeration completed.
Mar 21 08:26:54 ubuntu avahi-daemon[1700]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 21 08:26:54 ubuntu avahi-daemon[1700]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1100639166.
Mar 21 08:26:56 ubuntu NetworkManager: <info>  starting...
Mar 21 08:26:56 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Mar 21 08:26:56 ubuntu kernel: [   90.754728] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Mar 21 08:26:57 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/net/eth0, iface: eth0)
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 21 08:26:57 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Mar 21 08:26:57 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 21 08:26:57 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin Generic
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin Gobi
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin Option High-Speed
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin Huawei
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin Ericsson MBM
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin MotoC
Mar 21 08:26:57 ubuntu modem-manager: Loaded plugin Nokia
Mar 21 08:26:58 ubuntu modem-manager: Loaded plugin Novatel
Mar 21 08:26:58 ubuntu NetworkManager: <info>  Wireless now enabled by radio killswitch
Mar 21 08:26:58 ubuntu NetworkManager:    SCPlugin-Ifupdown: (147901168) ... get_connections.
Mar 21 08:26:58 ubuntu NetworkManager:    SCPlugin-Ifupdown: (147901168) ... get_connections (managed=false): return empty list.
Mar 21 08:26:58 ubuntu modem-manager: Loaded plugin Option
Mar 21 08:26:58 ubuntu modem-manager: Loaded plugin Sierra
Mar 21 08:26:58 ubuntu modem-manager: Loaded plugin ZTE
Mar 21 08:26:58 ubuntu modem-manager: (ttyUSB0) opening serial device...
Mar 21 08:26:58 ubuntu modem-manager: (ttyUSB0): probe requested by plugin 'Generic'
Mar 21 08:26:59 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'forcedeth')
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): now managed
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): preparing device.
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 21 08:26:59 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:07.0/net/eth0
Mar 21 08:26:59 ubuntu kernel: [   93.504705]   alloc irq_desc for 27 on node -1
Mar 21 08:26:59 ubuntu kernel: [   93.504708]   alloc kstat_irqs on node -1
Mar 21 08:26:59 ubuntu kernel: [   93.504716] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 21 08:26:59 ubuntu NetworkManager: <info>  modem-manager is now available
Mar 21 08:26:59 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 21 08:26:59 ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 21 08:26:59 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 21 08:27:00 ubuntu NetworkManager: <info>  dhclient started with pid 1911
Mar 21 08:27:00 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 21 08:27:00 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 21 08:27:00 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 21 08:27:00 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 21 08:27:00 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 21 08:27:00 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 21 08:27:00 ubuntu dhclient: All rights reserved.
Mar 21 08:27:00 ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 21 08:27:00 ubuntu dhclient: 
Mar 21 08:27:00 ubuntu kernel: [   95.063121] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Mar 21 08:27:00 ubuntu kernel: [   95.063126] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Mar 21 08:27:00 ubuntu kernel: [   95.063145] HDA Intel 0000:00:05.0: setting latency timer to 64
Mar 21 08:27:00 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Mar 21 08:27:00 ubuntu dhclient: Listening on LPF/eth0/90:e6:ba:14:d8:36
Mar 21 08:27:00 ubuntu dhclient: Sending on   LPF/eth0/90:e6:ba:14:d8:36
Mar 21 08:27:00 ubuntu dhclient: Sending on   Socket/fallback
Mar 21 08:27:01 ubuntu avahi-daemon[1700]: Registering new address record for fe80::92e6:baff:fe14:d836 on eth0.*.
Mar 21 08:27:01 ubuntu kernel: [   95.908535] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Mar 21 08:27:01 ubuntu kernel: [   95.908614] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
Mar 21 08:27:02 ubuntu init: ubiquity main process (2013) terminated with status 1
Mar 21 08:27:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar 21 08:27:04 ubuntu dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Mar 21 08:27:04 ubuntu dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
Mar 21 08:27:04 ubuntu dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Mar 21 08:27:05 ubuntu dhclient: bound to 192.168.1.100 -- renewal in 42085 seconds.
Mar 21 08:27:05 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Mar 21 08:27:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 21 08:27:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 21 08:27:05 ubuntu NetworkManager: <info>    address 192.168.1.100
Mar 21 08:27:05 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 21 08:27:05 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Mar 21 08:27:05 ubuntu NetworkManager: <info>    nameserver '68.87.76.182'
Mar 21 08:27:05 ubuntu NetworkManager: <info>    nameserver '68.87.78.134'
Mar 21 08:27:05 ubuntu NetworkManager: <info>    domain name 'hsd1.ca.comcast.net.'
Mar 21 08:27:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 21 08:27:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 21 08:27:05 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 21 08:27:05 ubuntu avahi-daemon[1700]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.100.
Mar 21 08:27:05 ubuntu avahi-daemon[1700]: New relevant interface eth0.IPv4 for mDNS.
Mar 21 08:27:05 ubuntu avahi-daemon[1700]: Registering new address record for 192.168.1.100 on eth0.IPv4.
Mar 21 08:27:05 ubuntu cron[2083]: (CRON) INFO (pidfile fd = 3)
Mar 21 08:27:06 ubuntu cron[2120]: (CRON) STARTUP (fork ok)
Mar 21 08:27:06 ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 21 08:27:06 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 21 08:27:06 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 21 08:27:06 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 21 08:27:07 ubuntu cron[2120]: (CRON) INFO (Running @reboot jobs)
Mar 21 08:27:07 ubuntu acpid: client connected from 2297[107:114]
Mar 21 08:27:08 ubuntu gdm-binary[2049]: WARNING: Unable to find users: no seat-id found
Mar 21 08:27:10 ubuntu modem-manager: (ttyUSB0) closing serial device...
Mar 21 08:27:10 ubuntu kernel: [  104.312020] eth0: no IPv6 routers present
Mar 21 08:27:11 ubuntu kernel: [  105.515470] lp: driver loaded but no devices found
Mar 21 08:27:12 ubuntu kernel: [  106.319053] ppdev: user-space parallel port driver
Mar 21 08:27:14 ubuntu console-kit-daemon[1749]: WARNING: Couldn't read /proc/1716/environ: Failed to open file '/proc/1716/environ': No such file or directory
Mar 21 08:27:15 ubuntu udev-configure-printer: add /module/lp
Mar 21 08:27:15 ubuntu udev-configure-printer: Failed to get parent
Mar 21 08:27:16 ubuntu acpid: client connected from 2363[0:0]
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2
Mar 21 08:27:19 ubuntu udev-configure-printer: Failed to get parent
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-0:1.0
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-2
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-1
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2/2-2
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 0461:0010
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2/2-1
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 0461:4D20
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb2/2-2
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 0461:0010
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1
Mar 21 08:27:19 ubuntu udev-configure-printer: Failed to get parent
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-5
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:19 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-5/1-5:1.0
Mar 21 08:27:19 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1/1-5
Mar 21 08:27:19 ubuntu udev-configure-printer: Device vendor/product is 04E8:6619
Mar 21 08:27:19 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 21 08:27:20 ubuntu ntpdate[2647]: adjust time server 91.189.94.4 offset -0.159120 sec
Mar 21 08:27:28 ubuntu kernel: [  122.556924] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 21 08:27:28 ubuntu kernel: [  122.556928] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:28 ubuntu kernel: [  122.556931] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 21 08:27:28 ubuntu kernel: [  122.556935] Info fld=0x1caba
Mar 21 08:27:28 ubuntu kernel: [  122.556936] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 21 08:27:28 ubuntu kernel: [  122.556940] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:28 ubuntu kernel: [  122.556944] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:28 ubuntu kernel: [  122.556946] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:28 ubuntu kernel: [  122.556948] Buffer I/O error on device sr0, logical block 117436
Mar 21 08:27:28 ubuntu kernel: [  122.556949] Buffer I/O error on device sr0, logical block 117437
Mar 21 08:27:28 ubuntu kernel: [  122.556951] Buffer I/O error on device sr0, logical block 117438
Mar 21 08:27:28 ubuntu kernel: [  122.556953] Buffer I/O error on device sr0, logical block 117439
Mar 21 08:27:28 ubuntu kernel: [  122.556955] Buffer I/O error on device sr0, logical block 117440
Mar 21 08:27:28 ubuntu kernel: [  122.556957] Buffer I/O error on device sr0, logical block 117441
Mar 21 08:27:28 ubuntu kernel: [  122.556959] Buffer I/O error on device sr0, logical block 117442
Mar 21 08:27:28 ubuntu kernel: [  122.556960] Buffer I/O error on device sr0, logical block 117443
Mar 21 08:27:34 ubuntu kernel: [  128.797836] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 21 08:27:34 ubuntu kernel: [  128.797840] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:34 ubuntu kernel: [  128.797842] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 21 08:27:34 ubuntu kernel: [  128.797846] Info fld=0x1caca
Mar 21 08:27:34 ubuntu kernel: [  128.797848] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
Mar 21 08:27:34 ubuntu kernel: [  128.797851] end_request: I/O error, dev sr0, sector 469800
Mar 21 08:27:34 ubuntu kernel: [  128.797855] __ratelimit: 6 callbacks suppressed
Mar 21 08:27:34 ubuntu kernel: [  128.797857] Buffer I/O error on device sr0, logical block 117450
Mar 21 08:27:34 ubuntu kernel: [  128.797860] Buffer I/O error on device sr0, logical block 117451
Mar 21 08:27:34 ubuntu kernel: [  128.797862] Buffer I/O error on device sr0, logical block 117452
Mar 21 08:27:34 ubuntu kernel: [  128.797864] Buffer I/O error on device sr0, logical block 117453
Mar 21 08:27:34 ubuntu kernel: [  128.797866] Buffer I/O error on device sr0, logical block 117454
Mar 21 08:27:34 ubuntu kernel: [  128.797868] Buffer I/O error on device sr0, logical block 117455
Mar 21 08:27:34 ubuntu kernel: [  128.797869] Buffer I/O error on device sr0, logical block 117456
Mar 21 08:27:34 ubuntu kernel: [  128.797871] Buffer I/O error on device sr0, logical block 117457
Mar 21 08:27:34 ubuntu kernel: [  128.797873] Buffer I/O error on device sr0, logical block 117458
Mar 21 08:27:34 ubuntu kernel: [  128.797875] Buffer I/O error on device sr0, logical block 117459
Mar 21 08:27:40 ubuntu kernel: [  134.980655] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.980659] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.980662] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.980664] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.980668] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.980671] __ratelimit: 54 callbacks suppressed
Mar 21 08:27:40 ubuntu kernel: [  134.980673] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.980676] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  134.980773] SQUASHFS error: squashfs_read_data failed to read block 0xe2cc939
Mar 21 08:27:40 ubuntu kernel: [  134.980776] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980778] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980786] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980788] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980791] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980793] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980796] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980797] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980801] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980803] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.985668] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.985672] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.985676] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.985677] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.985681] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.985685] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.985688] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  134.991204] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.991209] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.991212] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.991214] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.991218] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.991222] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.991224] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  134.996223] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.996227] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.996231] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.996232] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.996236] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.996240] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.996242] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  135.001316] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.001321] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.001324] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.001325] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.001330] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.001334] Buffer I/O error on device sr0, logical block 117436
Mar 21 08:27:40 ubuntu kernel: [  135.001337] Buffer I/O error on device sr0, logical block 117437
Mar 21 08:27:40 ubuntu kernel: [  135.006509] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.006514] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.006518] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.006519] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.006524] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.011762] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.011766] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.011770] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.011771] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.011775] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.016706] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.016710] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.016714] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.016715] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.016719] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.021469] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.021474] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.021478] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.021479] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.021484] end_request: I/O error, dev sr0, sector 469752
Mar 21 08:27:40 ubuntu kernel: [  135.024733] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.024735] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.024738] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.024739] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.024742] end_request: I/O error, dev sr0, sector 469752
Mar 21 08:27:40 ubuntu kernel: [  135.028005] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.028009] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.028013] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.028014] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.028018] end_request: I/O error, dev sr0, sector 469752
Mar 21 08:27:45 ubuntu kernel: [  139.499234] CPU0 attaching NULL sched-domain.
Mar 21 08:27:45 ubuntu kernel: [  139.499240] CPU1 attaching NULL sched-domain.
Mar 21 08:27:45 ubuntu kernel: [  139.528544] CPU0 attaching sched-domain:
Mar 21 08:27:45 ubuntu kernel: [  139.528548]  domain 0: span 0-1 level MC
Mar 21 08:27:45 ubuntu kernel: [  139.528550]   groups: 0 1
Mar 21 08:27:45 ubuntu kernel: [  139.528553]   domain 1: span 0-1 level CPU
Mar 21 08:27:45 ubuntu kernel: [  139.528555]    groups: 0-1 (__cpu_power = 2048)
Mar 21 08:27:45 ubuntu kernel: [  139.528560] CPU1 attaching sched-domain:
Mar 21 08:27:45 ubuntu kernel: [  139.528561]  domain 0: span 0-1 level MC
Mar 21 08:27:45 ubuntu kernel: [  139.528563]   groups: 1 0
Mar 21 08:27:45 ubuntu kernel: [  139.528565]   domain 1: span 0-1 level CPU
Mar 21 08:27:45 ubuntu kernel: [  139.528567]    groups: 0-1 (__cpu_power = 2048)
Mar 21 08:27:57 ubuntu kernel: [  151.845598] CPU0 attaching NULL sched-domain.
Mar 21 08:27:57 ubuntu kernel: [  151.845603] CPU1 attaching NULL sched-domain.
Mar 21 08:27:57 ubuntu kernel: [  151.860586] CPU0 attaching sched-domain:
Mar 21 08:27:57 ubuntu kernel: [  151.860590]  domain 0: span 0-1 level MC
Mar 21 08:27:57 ubuntu kernel: [  151.860592]   groups: 0 1
Mar 21 08:27:57 ubuntu kernel: [  151.860597] CPU1 attaching sched-domain:
Mar 21 08:27:57 ubuntu kernel: [  151.860599]  domain 0: span 0-1 level MC
Mar 21 08:27:57 ubuntu kernel: [  151.860600]   groups: 1 0
Mar 21 09:15:00 ubuntu kernel: [ 2974.996878] usb 1-5: USB disconnect, address 4
Mar 21 09:15:00 ubuntu kernel: [ 2974.997254] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:15:00 ubuntu kernel: [ 2974.997285] ipaq 1-5:1.0: device disconnected
Mar 21 09:15:31 ubuntu kernel: [ 3005.856074] usb 1-6: new high speed USB device using ehci_hcd and address 5
Mar 21 09:15:31 ubuntu kernel: [ 3005.990057] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:15:31 ubuntu kernel: [ 3005.990978] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:15:31 ubuntu kernel: [ 3005.991430] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:16:04 ubuntu kernel: [ 3038.299162] usb 1-6: USB disconnect, address 5
Mar 21 09:16:04 ubuntu kernel: [ 3038.299438] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:16:04 ubuntu kernel: [ 3038.299466] ipaq 1-6:1.0: device disconnected
Mar 21 09:16:25 ubuntu kernel: [ 3059.928075] usb 1-6: new high speed USB device using ehci_hcd and address 6
Mar 21 09:16:25 ubuntu kernel: [ 3060.061964] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:16:25 ubuntu kernel: [ 3060.064923] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:16:25 ubuntu kernel: [ 3060.065424] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:17:01 ubuntu CRON[3832]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 21 09:17:10 ubuntu kernel: [ 3105.150691] usb 1-6: USB disconnect, address 6
Mar 21 09:17:10 ubuntu kernel: [ 3105.150973] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:17:10 ubuntu kernel: [ 3105.151001] ipaq 1-6:1.0: device disconnected
Mar 21 09:17:28 ubuntu kernel: [ 3122.948074] usb 1-6: new high speed USB device using ehci_hcd and address 7
Mar 21 09:17:28 ubuntu kernel: [ 3123.082106] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:17:28 ubuntu kernel: [ 3123.083160] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:17:28 ubuntu kernel: [ 3123.083598] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:17:40 ubuntu kernel: [ 3134.746268] usb 1-6: USB disconnect, address 7
Mar 21 09:17:40 ubuntu kernel: [ 3134.746553] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:17:40 ubuntu kernel: [ 3134.746582] ipaq 1-6:1.0: device disconnected
Mar 21 09:17:52 ubuntu kernel: [ 3146.952062] usb 1-6: new high speed USB device using ehci_hcd and address 8
Mar 21 09:17:52 ubuntu kernel: [ 3147.085976] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:17:52 ubuntu kernel: [ 3147.086900] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:17:52 ubuntu kernel: [ 3147.087346] usb 1-6: PocketPC PDA converter now attached to ttyUSB0

---

### Post by NightwishFan on 2010-03-21
I meant post only the relevant lines. :KS

If you want to add the whole log, edit and place in CODE tags. CODE is the symbol in advanced editing that looks like this: #

EDIT: Skimmed, it offered no help to me other than the device was recognized.

---

### Post by cadogan281 on 2010-03-21
kern.log,messages,and syslog are all in black.its that what you mean?

---

### Post by NightwishFan on 2010-03-21
I meant when you inserted the phone, some messages would append to the end of the log in bold. I apologize for not being clear.

Sorry to say I perused the log and it says nothing to me except the device was recognized. I do not think the mentioned "usb0" is mountable.

---

### Post by cadogan281 on 2010-03-21
[INDENT]```
 Mar 21 08:26:48 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Mar 21 08:26:48 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ee0000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ef0000 - 00000000b7f00000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b8000000 - 00000000c0000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] DMI present.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] last_pfn = 0xb7ee0 max_arch_pfn = 0x100000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Mar 21 08:26:48 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
Mar 21 08:26:48 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   2 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   3 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   4 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   5 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   6 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   7 disabled
Mar 21 08:26:48 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 21 08:26:48 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000b7ee0000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ef0000 - 00000000b7f00000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b8000000 - 00000000c0000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Mar 21 08:26:48 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] RAMDISK: 7fa82000 - 7ffff098
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007fa82000 - 000000007ffff097 to 008ad000 - 00e2a097
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: RSDP 000f7500 00024 (v02 HPQOEM)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: XSDT b7ee3100 00054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: FACP b7ee7e80 000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: DSDT b7ee32c0 04B61 (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: FACS b7ee0000 00040
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: SLIC b7ee80c0 00176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: SSDT b7ee8280 0095E (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: HPET b7ee8c40 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: MCFG b7ee8cc0 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: APIC b7ee7fc0 00098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] 2054MB HIGHMEM available.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Mar 21 08:26:48 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #5 [00008a9000 - 00008ac5b0]              BRK ==> [00008a9000 - 00008ac5b0]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f53c0] f53c0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x000b7ee0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 21 08:26:48 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000b7ee0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] On node 0 totalpages: 753263
Mar 21 08:26:48 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem zone: 4110 pages used for memmap
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem zone: 521940 pages, LIFO batch:31
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using APIC driver default
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Mar 21 08:26:48 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages at c2710000, static data 35612 bytes
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747377
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] allocated 15067200 bytes of page_cgroup
Mar 21 08:26:48 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000b7ee0)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Memory: 2959336k/3013504k available (4565k kernel code, 52852k reserved, 2143k data, 540k init, 2104200k highmem)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 21 08:26:48 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Detected 2712.787 MHz processor.
Mar 21 08:26:48 ubuntu kernel: [    0.000011] spurious 8259A interrupt: IRQ7.
Mar 21 08:26:48 ubuntu kernel: [    0.003280] Console: colour VGA+ 80x25
Mar 21 08:26:48 ubuntu kernel: [    0.003282] console [tty0] enabled
Mar 21 08:26:48 ubuntu kernel: [    0.003415] hpet clockevent registered
Mar 21 08:26:48 ubuntu kernel: [    0.003417] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Mar 21 08:26:48 ubuntu kernel: [    0.003423] Calibrating delay loop (skipped), value calculated using timer frequency.. 5425.57 BogoMIPS (lpj=10851148)
Mar 21 08:26:48 ubuntu kernel: [    0.003436] Security Framework initialized
Mar 21 08:26:48 ubuntu kernel: [    0.003450] AppArmor: AppArmor initialized
Mar 21 08:26:48 ubuntu kernel: [    0.003456] Mount-cache hash table entries: 512
Mar 21 08:26:48 ubuntu kernel: [    0.003539] Initializing cgroup subsys ns
Mar 21 08:26:48 ubuntu kernel: [    0.003542] Initializing cgroup subsys cpuacct
Mar 21 08:26:48 ubuntu kernel: [    0.003545] Initializing cgroup subsys memory
Mar 21 08:26:48 ubuntu kernel: [    0.003549] Initializing cgroup subsys freezer
Mar 21 08:26:48 ubuntu kernel: [    0.003551] Initializing cgroup subsys net_cls
Mar 21 08:26:48 ubuntu kernel: [    0.003560] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.003562] CPU: L2 Cache: 512K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.003564] CPU: Physical Processor ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.003565] CPU: Processor Core ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.003567] mce: CPU supports 6 MCE banks
Mar 21 08:26:48 ubuntu kernel: [    0.003574] using C1E aware idle routine
Mar 21 08:26:48 ubuntu kernel: [    0.003579] Performance Counters: AMD PMU driver.
Mar 21 08:26:48 ubuntu kernel: [    0.003584] ... version:                 0
Mar 21 08:26:48 ubuntu kernel: [    0.003585] ... bit width:               48
Mar 21 08:26:48 ubuntu kernel: [    0.003586] ... generic counters:        4
Mar 21 08:26:48 ubuntu kernel: [    0.003588] ... value mask:              0000ffffffffffff
Mar 21 08:26:48 ubuntu kernel: [    0.003589] ... max period:              00007fffffffffff
Mar 21 08:26:48 ubuntu kernel: [    0.003591] ... fixed-purpose counters:  0
Mar 21 08:26:48 ubuntu kernel: [    0.003592] ... counter mask:            000000000000000f
Mar 21 08:26:48 ubuntu kernel: [    0.003595] Checking 'hlt' instruction... OK.
Mar 21 08:26:48 ubuntu kernel: [    0.017599] ACPI: Core revision 20090521
Mar 21 08:26:48 ubuntu kernel: [    0.024515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 21 08:26:48 ubuntu kernel: [    0.066966] CPU0: AMD Athlon(tm) II X2 215 Processor stepping 02
Mar 21 08:26:48 ubuntu kernel: [    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
Mar 21 08:26:48 ubuntu kernel: [    0.004000] Initializing CPU#1
Mar 21 08:26:48 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 5424.64 BogoMIPS (lpj=10849283)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Mar 21 08:26:48 ubuntu kernel: [    0.004000] mce: CPU supports 6 MCE banks
Mar 21 08:26:48 ubuntu kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Mar 21 08:26:48 ubuntu kernel: [    0.152484] CPU1: AMD Athlon(tm) II X2 215 Processor stepping 02
Mar 21 08:26:48 ubuntu kernel: [    0.152494] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 21 08:26:48 ubuntu kernel: [    0.156010] Brought up 2 CPUs
Mar 21 08:26:48 ubuntu kernel: [    0.156012] Total of 2 processors activated (10850.21 BogoMIPS).
Mar 21 08:26:48 ubuntu kernel: [    0.156092] CPU0 attaching sched-domain:
Mar 21 08:26:48 ubuntu kernel: [    0.156094]  domain 0: span 0-1 level MC
Mar 21 08:26:48 ubuntu kernel: [    0.156096]   groups: 0 1
Mar 21 08:26:48 ubuntu kernel: [    0.156100] CPU1 attaching sched-domain:
Mar 21 08:26:48 ubuntu kernel: [    0.156101]  domain 0: span 0-1 level MC
Mar 21 08:26:48 ubuntu kernel: [    0.156103]   groups: 1 0
Mar 21 08:26:48 ubuntu kernel: [    0.156158] Booting paravirtualized kernel on bare hardware
Mar 21 08:26:48 ubuntu kernel: [    0.156158] regulator: core version 0.5
Mar 21 08:26:48 ubuntu kernel: [    0.156158] Time:  8:25:25  Date: 03/21/10
Mar 21 08:26:48 ubuntu kernel: [    0.156158] NET: Registered protocol family 16
Mar 21 08:26:48 ubuntu kernel: [    0.156164] EISA bus registered
Mar 21 08:26:48 ubuntu kernel: [    0.156176] ACPI: bus type pci registered
Mar 21 08:26:48 ubuntu kernel: [    0.156229] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Mar 21 08:26:48 ubuntu kernel: [    0.156232] PCI: MCFG area at f0000000 reserved in E820
Mar 21 08:26:48 ubuntu kernel: [    0.156233] PCI: Using MMCONFIG for extended config space
Mar 21 08:26:48 ubuntu kernel: [    0.156235] PCI: Using configuration type 1 for base access
Mar 21 08:26:48 ubuntu kernel: [    0.156818] bio: create slab <bio-0> at 0
Mar 21 08:26:48 ubuntu kernel: [    0.156818] ACPI: EC: Look up EC in DSDT
Mar 21 08:26:48 ubuntu kernel: [    0.164071] ACPI: Interpreter enabled
Mar 21 08:26:48 ubuntu kernel: [    0.164077] ACPI: (supports S0 S1 S3 S4 S5)
Mar 21 08:26:48 ubuntu kernel: [    0.164098] ACPI: Using IOAPIC for interrupt routing
Mar 21 08:26:48 ubuntu kernel: [    0.168675] ACPI: No dock devices found.
Mar 21 08:26:48 ubuntu kernel: [    0.168766] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 21 08:26:48 ubuntu kernel: [    0.168959] pci 0000:00:01.1: reg 10 io port: [0xff00-0xff3f]
Mar 21 08:26:48 ubuntu kernel: [    0.168969] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
Mar 21 08:26:48 ubuntu kernel: [    0.168972] pci 0000:00:01.1: reg 24 io port: [0x1c40-0x1c7f]
Mar 21 08:26:48 ubuntu kernel: [    0.168990] pci 0000:00:01.1: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.168995] pci 0000:00:01.1: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169037] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169057] pci 0000:00:02.0: supports D1 D2
Mar 21 08:26:48 ubuntu kernel: [    0.169059] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169061] pci 0000:00:02.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169081] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
Mar 21 08:26:48 ubuntu kernel: [    0.169104] pci 0000:00:02.1: supports D1 D2
Mar 21 08:26:48 ubuntu kernel: [    0.169106] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169109] pci 0000:00:02.1: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169161] pci 0000:00:05.0: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
Mar 21 08:26:48 ubuntu kernel: [    0.169185] pci 0000:00:05.0: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169188] pci 0000:00:05.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169216] pci 0000:00:07.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169219] pci 0000:00:07.0: reg 14 io port: [0xfc00-0xfc07]
Mar 21 08:26:48 ubuntu kernel: [    0.169239] pci 0000:00:07.0: supports D1 D2
Mar 21 08:26:48 ubuntu kernel: [    0.169240] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169244] pci 0000:00:07.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169262] pci 0000:00:08.0: reg 10 io port: [0x9f0-0x9f7]
Mar 21 08:26:48 ubuntu kernel: [    0.169265] pci 0000:00:08.0: reg 14 io port: [0xbf0-0xbf3]
Mar 21 08:26:48 ubuntu kernel: [    0.169268] pci 0000:00:08.0: reg 18 io port: [0x970-0x977]
Mar 21 08:26:48 ubuntu kernel: [    0.169271] pci 0000:00:08.0: reg 1c io port: [0xb70-0xb73]
Mar 21 08:26:48 ubuntu kernel: [    0.169274] pci 0000:00:08.0: reg 20 io port: [0xf700-0xf70f]
Mar 21 08:26:48 ubuntu kernel: [    0.169277] pci 0000:00:08.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169304] pci 0000:00:08.1: reg 10 io port: [0x9e0-0x9e7]
Mar 21 08:26:48 ubuntu kernel: [    0.169307] pci 0000:00:08.1: reg 14 io port: [0xbe0-0xbe3]
Mar 21 08:26:48 ubuntu kernel: [    0.169310] pci 0000:00:08.1: reg 18 io port: [0x960-0x967]
Mar 21 08:26:48 ubuntu kernel: [    0.169313] pci 0000:00:08.1: reg 1c io port: [0xb60-0xb63]
Mar 21 08:26:48 ubuntu kernel: [    0.169316] pci 0000:00:08.1: reg 20 io port: [0xf200-0xf20f]
Mar 21 08:26:48 ubuntu kernel: [    0.169319] pci 0000:00:08.1: reg 24 32bit mmio: [0xfe02b000-0xfe02bfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169360] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169362] pci 0000:00:09.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169389] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169391] pci 0000:00:0b.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169418] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169420] pci 0000:00:0c.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169434] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169438] pci 0000:00:0d.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169442] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169446] pci 0000:00:0d.0: reg 30 32bit mmio: [0x000000-0x01ffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169551] pci 0000:00:04.0: transparent bridge
Mar 21 08:26:48 ubuntu kernel: [    0.169554] pci 0000:00:04.0: bridge io port: [0xe000-0xefff]
Mar 21 08:26:48 ubuntu kernel: [    0.169556] pci 0000:00:04.0: bridge 32bit mmio: [0xfd700000-0xfd7fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169559] pci 0000:00:04.0: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169591] pci 0000:00:09.0: bridge io port: [0xd000-0xdfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169593] pci 0000:00:09.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169596] pci 0000:00:09.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169628] pci 0000:00:0b.0: bridge io port: [0xc000-0xcfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169630] pci 0000:00:0b.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169633] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169662] pci 0000:04:00.0: reg 10 64bit mmio: [0xfd9ff000-0xfd9fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169698] pci 0000:04:00.0: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169701] pci 0000:04:00.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169739] pci 0000:00:0c.0: bridge io port: [0xb000-0xbfff]
Mar 21 08:26:48 ubuntu kernel: [    0.169741] pci 0000:00:0c.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169744] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.169751] pci_bus 0000:00: on NUMA node 0
Mar 21 08:26:48 ubuntu kernel: [    0.169754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 21 08:26:48 ubuntu kernel: [    0.169890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Mar 21 08:26:48 ubuntu kernel: [    0.197392] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197489] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197583] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197677] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197772] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.197866] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197959] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198053] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198149] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198242] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198337] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198432] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198528] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198622] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198717] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198812] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198908] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199003] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.199099] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.199226] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199348] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199469] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199589] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199708] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Mar 21 08:26:48 ubuntu kernel: [    0.199828] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199949] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200077] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200197] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200317] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200439] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200564] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200688] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200808] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200928] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201048] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.201169] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.201290] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201410] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201539] SCSI subsystem initialized
Mar 21 08:26:48 ubuntu kernel: [    0.201579] libata version 3.00 loaded.
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new interface driver usbfs
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new interface driver hub
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new device driver usb
Mar 21 08:26:48 ubuntu kernel: [    0.201579] ACPI: WMI: Mapper loaded
Mar 21 08:26:48 ubuntu kernel: [    0.201579] PCI: Using ACPI for IRQ routing
Mar 21 08:26:48 ubuntu kernel: [    0.212006] Bluetooth: Core ver 2.15
Mar 21 08:26:48 ubuntu kernel: [    0.212015] NET: Registered protocol family 31
Mar 21 08:26:48 ubuntu kernel: [    0.212015] Bluetooth: HCI device and connection manager initialized
Mar 21 08:26:48 ubuntu kernel: [    0.212015] Bluetooth: HCI socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    0.212016] NetLabel: Initializing
Mar 21 08:26:48 ubuntu kernel: [    0.212017] NetLabel:  domain hash size = 128
Mar 21 08:26:48 ubuntu kernel: [    0.212019] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 21 08:26:48 ubuntu kernel: [    0.212028] NetLabel:  unlabeled traffic allowed by default
Mar 21 08:26:48 ubuntu kernel: [    0.212052] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
Mar 21 08:26:48 ubuntu kernel: [    0.212055] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Mar 21 08:26:48 ubuntu kernel: [    0.228008] pnp: PnP ACPI init
Mar 21 08:26:48 ubuntu kernel: [    0.228025] ACPI: bus type pnp registered
Mar 21 08:26:48 ubuntu kernel: [    0.229898] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) 20090521 dsopcode-596
Mar 21 08:26:48 ubuntu kernel: [    0.229904] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.MEM_._CRS] (Node f7017f60), AE_AML_BUFFER_LIMIT
Mar 21 08:26:48 ubuntu kernel: [    0.229924] ACPI Error (uteval-0256): Method execution failed [\_SB_.MEM_._CRS] (Node f7017f60), AE_AML_BUFFER_LIMIT
Mar 21 08:26:48 ubuntu kernel: [    0.229930] pnp 00:09: can't evaluate _CRS: 12298
Mar 21 08:26:48 ubuntu kernel: [    0.229966] pnp: PnP ACPI: found 10 devices
Mar 21 08:26:48 ubuntu kernel: [    0.229967] ACPI: ACPI bus type pnp unregistered
Mar 21 08:26:48 ubuntu kernel: [    0.229970] PnPBIOS: Disabled by ACPI PNP
Mar 21 08:26:48 ubuntu kernel: [    0.229979] system 00:01: ioport range 0x1000-0x107f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229981] system 00:01: ioport range 0x1080-0x10ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229983] system 00:01: ioport range 0x1400-0x147f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229985] system 00:01: ioport range 0x1480-0x14ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229987] system 00:01: ioport range 0x1800-0x187f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229989] system 00:01: ioport range 0x1880-0x18ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229993] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229995] system 00:02: ioport range 0x800-0x87f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229997] system 00:02: ioport range 0x294-0x297 has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.230002] system 00:08: iomem range 0xf0000000-0xf3ffffff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.264619] AppArmor: AppArmor Filesystem Enabled
Mar 21 08:26:48 ubuntu kernel: [    0.264642] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Mar 21 08:26:48 ubuntu kernel: [    0.264644] pci 0000:00:04.0:   IO window: 0xe000-0xefff
Mar 21 08:26:48 ubuntu kernel: [    0.264647] pci 0000:00:04.0:   MEM window: 0xfd700000-0xfd7fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264650] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
Mar 21 08:26:48 ubuntu kernel: [    0.264654] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Mar 21 08:26:48 ubuntu kernel: [    0.264656] pci 0000:00:09.0:   IO window: 0xd000-0xdfff
Mar 21 08:26:48 ubuntu kernel: [    0.264658] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264661] pci 0000:00:09.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264663] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Mar 21 08:26:48 ubuntu kernel: [    0.264665] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
Mar 21 08:26:48 ubuntu kernel: [    0.264668] pci 0000:00:0b.0:   MEM window: 0xfdb00000-0xfdbfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264670] pci 0000:00:0b.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
Mar 21 08:26:48 ubuntu kernel: [    0.264673] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Mar 21 08:26:48 ubuntu kernel: [    0.264675] pci 0000:00:0c.0:   IO window: 0xb000-0xbfff
Mar 21 08:26:48 ubuntu kernel: [    0.264677] pci 0000:00:0c.0:   MEM window: 0xfd900000-0xfd9fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264679] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264687] pci 0000:00:04.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264691] pci 0000:00:09.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264694] pci 0000:00:0b.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264697] pci 0000:00:0c.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    0.264701] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264703] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264705] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Mar 21 08:26:48 ubuntu kernel: [    0.264706] pci_bus 0000:01: resource 1 mem: [0xfd700000-0xfd7fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264708] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264710] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264712] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264714] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Mar 21 08:26:48 ubuntu kernel: [    0.264716] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264717] pci_bus 0000:02: resource 2 pref mem [0xfdc00000-0xfdcfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264719] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
Mar 21 08:26:48 ubuntu kernel: [    0.264721] pci_bus 0000:03: resource 1 mem: [0xfdb00000-0xfdbfffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264723] pci_bus 0000:03: resource 2 pref mem [0xfda00000-0xfdafffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264725] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
Mar 21 08:26:48 ubuntu kernel: [    0.264727] pci_bus 0000:04: resource 1 mem: [0xfd900000-0xfd9fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264729] pci_bus 0000:04: resource 2 pref mem [0xfd800000-0xfd8fffff]
Mar 21 08:26:48 ubuntu kernel: [    0.264756] NET: Registered protocol family 2
Mar 21 08:26:48 ubuntu kernel: [    0.264826] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265050] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265516] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265732] TCP: Hash tables configured (established 131072 bind 65536)
Mar 21 08:26:48 ubuntu kernel: [    0.265734] TCP reno registered
Mar 21 08:26:48 ubuntu kernel: [    0.265804] NET: Registered protocol family 1
Mar 21 08:26:48 ubuntu kernel: [    0.265853] Trying to unpack rootfs image as initramfs...
Mar 21 08:26:48 ubuntu kernel: [    0.500482] Switched to high resolution mode on CPU 1
Mar 21 08:26:48 ubuntu kernel: [    0.503953] Switched to high resolution mode on CPU 0
Mar 21 08:26:48 ubuntu kernel: [    1.240431] Freeing initrd memory: 5620k freed
Mar 21 08:26:48 ubuntu kernel: [    1.242588] cpufreq-nforce2: No nForce2 chipset.
Mar 21 08:26:48 ubuntu kernel: [    1.242606] Scanning for low memory corruption every 60 seconds
Mar 21 08:26:48 ubuntu kernel: [    1.242679] audit: initializing netlink socket (disabled)
Mar 21 08:26:48 ubuntu kernel: [    1.242690] type=2000 audit(1269159926.240:1): initialized
Mar 21 08:26:48 ubuntu kernel: [    1.248960] highmem bounce pool size: 64 pages
Mar 21 08:26:48 ubuntu kernel: [    1.248964] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 21 08:26:48 ubuntu kernel: [    1.249902] VFS: Disk quotas dquot_6.5.2
Mar 21 08:26:48 ubuntu kernel: [    1.249942] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 21 08:26:48 ubuntu kernel: [    1.250322] fuse init (API version 7.12)
Mar 21 08:26:48 ubuntu kernel: [    1.250377] msgmni has been set to 1682
Mar 21 08:26:48 ubuntu kernel: [    1.250546] alg: No test for stdrng (krng)
Mar 21 08:26:48 ubuntu kernel: [    1.250567] io scheduler noop registered
Mar 21 08:26:48 ubuntu kernel: [    1.250569] io scheduler anticipatory registered
Mar 21 08:26:48 ubuntu kernel: [    1.250570] io scheduler deadline registered
Mar 21 08:26:48 ubuntu kernel: [    1.250600] io scheduler cfq registered (default)
Mar 21 08:26:48 ubuntu kernel: [    1.250698] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250743] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250792] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250843] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250894] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250949] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251008] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251071] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251075] pci 0000:00:0d.0: Boot video device
Mar 21 08:26:48 ubuntu kernel: [    1.251149]   alloc irq_desc for 24 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251151]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251157] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X
Mar 21 08:26:48 ubuntu kernel: [    1.251162] pcieport-driver 0000:00:09.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.251217]   alloc irq_desc for 25 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251218]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251221] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X
Mar 21 08:26:48 ubuntu kernel: [    1.251225] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.251275]   alloc irq_desc for 26 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251276]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.251279] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X
Mar 21 08:26:48 ubuntu kernel: [    1.251282] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.251322] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 21 08:26:48 ubuntu kernel: [    1.251340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 21 08:26:48 ubuntu kernel: [    1.251425] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 21 08:26:48 ubuntu kernel: [    1.251428] ACPI: Power Button [PWRF]
Mar 21 08:26:48 ubuntu kernel: [    1.251464] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Mar 21 08:26:48 ubuntu kernel: [    1.251466] ACPI: Power Button [PWRB]
Mar 21 08:26:48 ubuntu kernel: [    1.251506] fan PNP0C0B:00: registered as cooling_device0
Mar 21 08:26:48 ubuntu kernel: [    1.251509] ACPI: Fan [FAN] (on)
Mar 21 08:26:48 ubuntu kernel: [    1.251734] processor LNXCPU:00: registered as cooling_device1
Mar 21 08:26:48 ubuntu kernel: [    1.251760] processor LNXCPU:01: registered as cooling_device2
Mar 21 08:26:48 ubuntu kernel: [    1.253978] ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference 20090521 nspredef-946
Mar 21 08:26:48 ubuntu kernel: [    1.253984] ACPI: Expecting a [Reference] package element, found type 0
Mar 21 08:26:48 ubuntu kernel: [    1.253985] ACPI: Invalid passive threshold
Mar 21 08:26:48 ubuntu kernel: [    1.254214] thermal LNXTHERM:01: registered as thermal_zone0
Mar 21 08:26:48 ubuntu kernel: [    1.254218] ACPI: Thermal Zone [THRM] (40 C)
Mar 21 08:26:48 ubuntu kernel: [    1.254258] isapnp: Scanning for PnP cards...
Mar 21 08:26:48 ubuntu kernel: [    1.606935] isapnp: No Plug & Play device found
Mar 21 08:26:48 ubuntu kernel: [    1.607732] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 21 08:26:48 ubuntu kernel: [    1.608513] brd: module loaded
Mar 21 08:26:48 ubuntu kernel: [    1.608787] loop: module loaded
Mar 21 08:26:48 ubuntu kernel: [    1.608839] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Mar 21 08:26:48 ubuntu kernel: [    1.608968] sata_nv 0000:00:08.0: version 3.5
Mar 21 08:26:48 ubuntu kernel: [    1.609204] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Mar 21 08:26:48 ubuntu kernel: [    1.609208]   alloc irq_desc for 20 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609210]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609219] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Mar 21 08:26:48 ubuntu kernel: [    1.609246] sata_nv 0000:00:08.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.609330] scsi0 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609406] scsi1 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609508] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf700 irq 20
Mar 21 08:26:48 ubuntu kernel: [    1.609510] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf708 irq 20
Mar 21 08:26:48 ubuntu kernel: [    1.609717] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
Mar 21 08:26:48 ubuntu kernel: [    1.609719]   alloc irq_desc for 21 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609721]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.609727] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 21 (level, low) -> IRQ 21
Mar 21 08:26:48 ubuntu kernel: [    1.609746] sata_nv 0000:00:08.1: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.609863] scsi2 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609900] scsi3 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609994] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf200 irq 21
Mar 21 08:26:48 ubuntu kernel: [    1.609996] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf208 irq 21
Mar 21 08:26:48 ubuntu kernel: [    1.610485] Fixed MDIO Bus: probed
Mar 21 08:26:48 ubuntu kernel: [    1.610507] PPP generic driver version 2.4.2
Mar 21 08:26:48 ubuntu kernel: [    1.610577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 21 08:26:48 ubuntu kernel: [    1.610786] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    1.610788]   alloc irq_desc for 23 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.610789]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.610795] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    1.610803] ehci_hcd 0000:00:02.1: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.610805] ehci_hcd 0000:00:02.1: EHCI Host Controller
Mar 21 08:26:48 ubuntu kernel: [    1.610840] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Mar 21 08:26:48 ubuntu kernel: [    1.610862] ehci_hcd 0000:00:02.1: debug port 1
Mar 21 08:26:48 ubuntu kernel: [    1.610866] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Mar 21 08:26:48 ubuntu kernel: [    1.610880] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
Mar 21 08:26:48 ubuntu kernel: [    1.621189] ata3: SATA link down (SStatus 0 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.624531] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Mar 21 08:26:48 ubuntu kernel: [    1.624620] usb usb1: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    1.624640] hub 1-0:1.0: USB hub found
Mar 21 08:26:48 ubuntu kernel: [    1.624646] hub 1-0:1.0: 10 ports detected
Mar 21 08:26:48 ubuntu kernel: [    1.624701] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 21 08:26:48 ubuntu kernel: [    1.624952] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Mar 21 08:26:48 ubuntu kernel: [    1.624956]   alloc irq_desc for 22 on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.624957]   alloc kstat_irqs on node -1
Mar 21 08:26:48 ubuntu kernel: [    1.624966] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
Mar 21 08:26:48 ubuntu kernel: [    1.624979] ohci_hcd 0000:00:02.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    1.624981] ohci_hcd 0000:00:02.0: OHCI Host Controller
Mar 21 08:26:48 ubuntu kernel: [    1.625005] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Mar 21 08:26:48 ubuntu kernel: [    1.625029] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfe02f000
Mar 21 08:26:48 ubuntu kernel: [    1.682027] usb usb2: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    1.682043] hub 2-0:1.0: USB hub found
Mar 21 08:26:48 ubuntu kernel: [    1.682049] hub 2-0:1.0: 10 ports detected
Mar 21 08:26:48 ubuntu kernel: [    1.682087] uhci_hcd: USB Universal Host Controller Interface driver
Mar 21 08:26:48 ubuntu kernel: [    1.682145] PNP: No PS/2 controller found. Probing ports directly.
Mar 21 08:26:48 ubuntu kernel: [    1.684313] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 21 08:26:48 ubuntu kernel: [    1.684318] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 21 08:26:48 ubuntu kernel: [    1.684355] mice: PS/2 mouse device common for all mice
Mar 21 08:26:48 ubuntu kernel: [    1.684417] rtc_cmos 00:05: RTC can wake from S4
Mar 21 08:26:48 ubuntu kernel: [    1.684444] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Mar 21 08:26:48 ubuntu kernel: [    1.684480] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Mar 21 08:26:48 ubuntu kernel: [    1.684551] device-mapper: uevent: version 1.0.3
Mar 21 08:26:48 ubuntu kernel: [    1.684645] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Mar 21 08:26:48 ubuntu kernel: [    1.684715] device-mapper: multipath: version 1.1.0 loaded
Mar 21 08:26:48 ubuntu kernel: [    1.684718] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 21 08:26:48 ubuntu kernel: [    1.684800] EISA: Probing bus 0 at eisa.0
Mar 21 08:26:48 ubuntu kernel: [    1.684804] Cannot allocate resource for EISA slot 1
Mar 21 08:26:48 ubuntu kernel: [    1.684821] EISA: Detected 0 cards.
Mar 21 08:26:48 ubuntu kernel: [    1.684904] cpuidle: using governor ladder
Mar 21 08:26:48 ubuntu kernel: [    1.684905] cpuidle: using governor menu
Mar 21 08:26:48 ubuntu kernel: [    1.685246] TCP cubic registered
Mar 21 08:26:48 ubuntu kernel: [    1.685347] NET: Registered protocol family 10
Mar 21 08:26:48 ubuntu kernel: [    1.685656] lo: Disabled Privacy Extensions
Mar 21 08:26:48 ubuntu kernel: [    1.685879] NET: Registered protocol family 17
Mar 21 08:26:48 ubuntu kernel: [    1.685891] Bluetooth: L2CAP ver 2.13
Mar 21 08:26:48 ubuntu kernel: [    1.685892] Bluetooth: L2CAP socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685894] Bluetooth: SCO (Voice Link) ver 0.6
Mar 21 08:26:48 ubuntu kernel: [    1.685896] Bluetooth: SCO socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685937] Bluetooth: RFCOMM TTY layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685939] Bluetooth: RFCOMM socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685940] Bluetooth: RFCOMM ver 1.11
Mar 21 08:26:48 ubuntu kernel: [    1.685956] powernow-k8: Found 1 AMD Athlon(tm) II X2 215 Processor processors (2 cpu cores) (version 2.20.00)
Mar 21 08:26:48 ubuntu kernel: [    1.685988] powernow-k8:    0 : pstate 0 (2700 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685990] powernow-k8:    1 : pstate 1 (2100 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685991] powernow-k8:    2 : pstate 2 (1500 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685993] powernow-k8:    3 : pstate 3 (800 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.686106] Using IPI No-Shortcut mode
Mar 21 08:26:48 ubuntu kernel: [    1.686153] PM: Resume from disk failed.
Mar 21 08:26:48 ubuntu kernel: [    1.686161] registered taskstats version 1
Mar 21 08:26:48 ubuntu kernel: [    1.686249]   Magic number: 2:779:422
Mar 21 08:26:48 ubuntu kernel: [    1.686341] rtc_cmos 00:05: setting system clock to 2010-03-21 08:25:27 UTC (1269159927)
Mar 21 08:26:48 ubuntu kernel: [    1.686345] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 21 08:26:48 ubuntu kernel: [    1.686347] EDD information not available.
Mar 21 08:26:48 ubuntu kernel: [    1.764043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.788144] ata1.00: ATA-8: Hitachi HDP725050GLA360, GM4OA57A, max UDMA/133
Mar 21 08:26:48 ubuntu kernel: [    1.788147] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 21 08:26:48 ubuntu kernel: [    1.804151] ata1.00: configured for UDMA/133
Mar 21 08:26:48 ubuntu kernel: [    1.804270] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
Mar 21 08:26:48 ubuntu kernel: [    1.804376] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 21 08:26:48 ubuntu kernel: [    1.804404] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Mar 21 08:26:48 ubuntu kernel: [    1.804430] sd 0:0:0:0: [sda] Write Protect is off
Mar 21 08:26:48 ubuntu kernel: [    1.804432] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 21 08:26:48 ubuntu kernel: [    1.804445] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 21 08:26:48 ubuntu kernel: [    1.804535]  sda: sda1 sda2 sda3
Mar 21 08:26:48 ubuntu kernel: [    1.827930] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 21 08:26:48 ubuntu kernel: [    1.960044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.968141] ata2.00: ATAPI: hp      DVD-RAM GH40L, RB0A, max UDMA/100
Mar 21 08:26:48 ubuntu kernel: [    1.984154] ata2.00: configured for UDMA/100
Mar 21 08:26:48 ubuntu kernel: [    1.989783] scsi 1:0:0:0: CD-ROM            hp       DVD-RAM GH40L    RB0A PQ: 0 ANSI: 5
Mar 21 08:26:48 ubuntu kernel: [    1.994047] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 21 08:26:48 ubuntu kernel: [    1.994049] Uniform CD-ROM driver Revision: 3.20
Mar 21 08:26:48 ubuntu kernel: [    1.994114] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 21 08:26:48 ubuntu kernel: [    1.994150] sr 1:0:0:0: Attached scsi generic sg1 type 5
Mar 21 08:26:48 ubuntu kernel: [    2.004462] ata4: SATA link down (SStatus 0 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    2.004512] Freeing unused kernel memory: 540k freed
Mar 21 08:26:48 ubuntu kernel: [    2.004737] Write protecting the kernel text: 4568k
Mar 21 08:26:48 ubuntu kernel: [    2.004764] Write protecting the kernel read-only data: 1836k
Mar 21 08:26:48 ubuntu kernel: [    2.052535] usb 1-5: new high speed USB device using ehci_hcd and address 4
Mar 21 08:26:48 ubuntu kernel: [    2.095329] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Mar 21 08:26:48 ubuntu kernel: [    2.095602] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    2.095607] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    2.095611] forcedeth 0000:00:07.0: setting latency timer to 64
Mar 21 08:26:48 ubuntu kernel: [    2.190522] usb 1-5: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    2.492032] usb 2-1: new low speed USB device using ohci_hcd and address 2
Mar 21 08:26:48 ubuntu kernel: [    2.612905] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:e6:ba:14:d8:36
Mar 21 08:26:48 ubuntu kernel: [    2.612910] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Mar 21 08:26:48 ubuntu kernel: [    2.721938] usb 2-1: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    2.728674] usbcore: registered new interface driver hiddev
Mar 21 08:26:48 ubuntu kernel: [    2.734020] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
Mar 21 08:26:48 ubuntu kernel: [    2.734078] generic-usb 0003:0461:4D20.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:02.0-1/input0
Mar 21 08:26:48 ubuntu kernel: [    2.734092] usbcore: registered new interface driver usbhid
Mar 21 08:26:48 ubuntu kernel: [    2.734094] usbhid: v2.6:USB HID core driver
Mar 21 08:26:48 ubuntu kernel: [    3.023623] xor: automatically using best checksumming function: pIII_sse
Mar 21 08:26:48 ubuntu kernel: [    3.028515] usb 2-2: new low speed USB device using ohci_hcd and address 3
Mar 21 08:26:48 ubuntu kernel: [    3.040003]    pIII_sse  : 10878.000 MB/sec
Mar 21 08:26:48 ubuntu kernel: [    3.040006] xor: using function: pIII_sse (10878.000 MB/sec)
Mar 21 08:26:48 ubuntu kernel: [    3.041713] device-mapper: dm-raid45: initialized v0.2594b
Mar 21 08:26:48 ubuntu kernel: [    3.229858] usb 2-2: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    3.240230] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
Mar 21 08:26:48 ubuntu kernel: [    3.240286] generic-usb 0003:0461:0010.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:02.0-2/input0
Mar 21 08:26:48 ubuntu kernel: [    3.252832] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input5
Mar 21 08:26:48 ubuntu kernel: [    3.252887] generic-usb 0003:0461:0010.0003: input,hidraw2: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:02.0-2/input1
Mar 21 08:26:48 ubuntu kernel: [    5.289275] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar 21 08:26:48 ubuntu kernel: [    5.391253] ISO 9660 Extensions: RRIP_1991A
Mar 21 08:26:48 ubuntu kernel: [    5.684341] aufs 2-standalone.tree-30-20090727
Mar 21 08:26:48 ubuntu kernel: [    5.918524] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Mar 21 08:26:48 ubuntu kernel: [   82.929313] udev: starting version 147
Mar 21 08:26:50 ubuntu kernel: [   84.668498] usbcore: registered new interface driver usbserial
Mar 21 08:26:50 ubuntu kernel: [   84.668513] USB Serial support registered for generic
Mar 21 08:26:50 ubuntu kernel: [   84.668533] usbcore: registered new interface driver usbserial_generic
Mar 21 08:26:50 ubuntu kernel: [   84.668535] usbserial: USB Serial Driver core
Mar 21 08:26:50 ubuntu kernel: [   85.052266] USB Serial support registered for PocketPC PDA
Mar 21 08:26:50 ubuntu kernel: [   85.052290] ipaq 1-5:1.0: PocketPC PDA converter detected
Mar 21 08:26:50 ubuntu kernel: [   85.053074] usb 1-5: PocketPC PDA converter now attached to ttyUSB0
Mar 21 08:26:50 ubuntu kernel: [   85.053099] usbcore: registered new interface driver ipaq
Mar 21 08:26:50 ubuntu kernel: [   85.053102] ipaq: v0.5:USB PocketPC PDA driver
Mar 21 08:26:51 ubuntu kernel: [   85.605461] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Mar 21 08:26:51 ubuntu kernel: [   85.605476] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
Mar 21 08:26:56 ubuntu kernel: [   90.754728] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 21 08:26:59 ubuntu kernel: [   93.504705]   alloc irq_desc for 27 on node -1
Mar 21 08:26:59 ubuntu kernel: [   93.504708]   alloc kstat_irqs on node -1
Mar 21 08:26:59 ubuntu kernel: [   93.504716] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
Mar 21 08:27:00 ubuntu kernel: [   95.063121] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Mar 21 08:27:00 ubuntu kernel: [   95.063126] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Mar 21 08:27:00 ubuntu kernel: [   95.063145] HDA Intel 0000:00:05.0: setting latency timer to 64
Mar 21 08:27:01 ubuntu kernel: [   95.908535] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Mar 21 08:27:01 ubuntu kernel: [   95.908614] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
Mar 21 08:27:10 ubuntu kernel: [  104.312020] eth0: no IPv6 routers present
Mar 21 08:27:11 ubuntu kernel: [  105.515470] lp: driver loaded but no devices found
Mar 21 08:27:12 ubuntu kernel: [  106.319053] ppdev: user-space parallel port driver
Mar 21 08:27:28 ubuntu kernel: [  122.556924] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 21 08:27:28 ubuntu kernel: [  122.556928] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:28 ubuntu kernel: [  122.556931] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 21 08:27:28 ubuntu kernel: [  122.556935] Info fld=0x1caba
Mar 21 08:27:28 ubuntu kernel: [  122.556936] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 21 08:27:28 ubuntu kernel: [  122.556940] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:28 ubuntu kernel: [  122.556944] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:28 ubuntu kernel: [  122.556946] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:28 ubuntu kernel: [  122.556948] Buffer I/O error on device sr0, logical block 117436
Mar 21 08:27:28 ubuntu kernel: [  122.556949] Buffer I/O error on device sr0, logical block 117437
Mar 21 08:27:28 ubuntu kernel: [  122.556951] Buffer I/O error on device sr0, logical block 117438
Mar 21 08:27:28 ubuntu kernel: [  122.556953] Buffer I/O error on device sr0, logical block 117439
Mar 21 08:27:28 ubuntu kernel: [  122.556955] Buffer I/O error on device sr0, logical block 117440
Mar 21 08:27:28 ubuntu kernel: [  122.556957] Buffer I/O error on device sr0, logical block 117441
Mar 21 08:27:28 ubuntu kernel: [  122.556959] Buffer I/O error on device sr0, logical block 117442
Mar 21 08:27:28 ubuntu kernel: [  122.556960] Buffer I/O error on device sr0, logical block 117443
Mar 21 08:27:34 ubuntu kernel: [  128.797836] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 21 08:27:34 ubuntu kernel: [  128.797840] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:34 ubuntu kernel: [  128.797842] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 21 08:27:34 ubuntu kernel: [  128.797846] Info fld=0x1caca
Mar 21 08:27:34 ubuntu kernel: [  128.797848] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
Mar 21 08:27:34 ubuntu kernel: [  128.797851] end_request: I/O error, dev sr0, sector 469800
Mar 21 08:27:34 ubuntu kernel: [  128.797855] __ratelimit: 6 callbacks suppressed
Mar 21 08:27:34 ubuntu kernel: [  128.797857] Buffer I/O error on device sr0, logical block 117450
Mar 21 08:27:34 ubuntu kernel: [  128.797860] Buffer I/O error on device sr0, logical block 117451
Mar 21 08:27:34 ubuntu kernel: [  128.797862] Buffer I/O error on device sr0, logical block 117452
Mar 21 08:27:34 ubuntu kernel: [  128.797864] Buffer I/O error on device sr0, logical block 117453
Mar 21 08:27:34 ubuntu kernel: [  128.797866] Buffer I/O error on device sr0, logical block 117454
Mar 21 08:27:34 ubuntu kernel: [  128.797868] Buffer I/O error on device sr0, logical block 117455
Mar 21 08:27:34 ubuntu kernel: [  128.797869] Buffer I/O error on device sr0, logical block 117456
Mar 21 08:27:34 ubuntu kernel: [  128.797871] Buffer I/O error on device sr0, logical block 117457
Mar 21 08:27:34 ubuntu kernel: [  128.797873] Buffer I/O error on device sr0, logical block 117458
Mar 21 08:27:34 ubuntu kernel: [  128.797875] Buffer I/O error on device sr0, logical block 117459
Mar 21 08:27:40 ubuntu kernel: [  134.980655] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.980659] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.980662] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.980664] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.980668] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.980671] __ratelimit: 54 callbacks suppressed
Mar 21 08:27:40 ubuntu kernel: [  134.980673] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.980676] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  134.980773] SQUASHFS error: squashfs_read_data failed to read block 0xe2cc939
Mar 21 08:27:40 ubuntu kernel: [  134.980776] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980778] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980786] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980788] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980791] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980793] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980796] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980797] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.980801] SQUASHFS error: Unable to read fragment cache entry [e2cc939]
Mar 21 08:27:40 ubuntu kernel: [  134.980803] SQUASHFS error: Unable to read page, block e2cc939, size 1614c
Mar 21 08:27:40 ubuntu kernel: [  134.985668] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.985672] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.985676] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.985677] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.985681] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.985685] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.985688] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  134.991204] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.991209] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.991212] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.991214] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.991218] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.991222] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.991224] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  134.996223] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.996227] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.996231] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.996232] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.996236] end_request: I/O error, dev sr0, sector 469736
Mar 21 08:27:40 ubuntu kernel: [  134.996240] Buffer I/O error on device sr0, logical block 117434
Mar 21 08:27:40 ubuntu kernel: [  134.996242] Buffer I/O error on device sr0, logical block 117435
Mar 21 08:27:40 ubuntu kernel: [  135.001316] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.001321] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.001324] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.001325] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.001330] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.001334] Buffer I/O error on device sr0, logical block 117436
Mar 21 08:27:40 ubuntu kernel: [  135.001337] Buffer I/O error on device sr0, logical block 117437
Mar 21 08:27:40 ubuntu kernel: [  135.006509] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.006514] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.006518] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.006519] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.006524] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.011762] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.011766] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.011770] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.011771] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.011775] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.016706] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.016710] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.016714] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.016715] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.016719] end_request: I/O error, dev sr0, sector 469744
Mar 21 08:27:40 ubuntu kernel: [  135.021469] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.021474] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.021478] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.021479] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.021484] end_request: I/O error, dev sr0, sector 469752
Mar 21 08:27:40 ubuntu kernel: [  135.024733] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.024735] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.024738] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.024739] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.024742] end_request: I/O error, dev sr0, sector 469752
Mar 21 08:27:40 ubuntu kernel: [  135.028005] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.028009] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.028013] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.028014] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.028018] end_request: I/O error, dev sr0, sector 469752
Mar 21 08:27:45 ubuntu kernel: [  139.499234] CPU0 attaching NULL sched-domain.
Mar 21 08:27:45 ubuntu kernel: [  139.499240] CPU1 attaching NULL sched-domain.
Mar 21 08:27:45 ubuntu kernel: [  139.528544] CPU0 attaching sched-domain:
Mar 21 08:27:45 ubuntu kernel: [  139.528548]  domain 0: span 0-1 level MC
Mar 21 08:27:45 ubuntu kernel: [  139.528550]   groups: 0 1
Mar 21 08:27:45 ubuntu kernel: [  139.528553]   domain 1: span 0-1 level CPU
Mar 21 08:27:45 ubuntu kernel: [  139.528555]    groups: 0-1 (__cpu_power = 2048)
Mar 21 08:27:45 ubuntu kernel: [  139.528560] CPU1 attaching sched-domain:
Mar 21 08:27:45 ubuntu kernel: [  139.528561]  domain 0: span 0-1 level MC
Mar 21 08:27:45 ubuntu kernel: [  139.528563]   groups: 1 0
Mar 21 08:27:45 ubuntu kernel: [  139.528565]   domain 1: span 0-1 level CPU
Mar 21 08:27:45 ubuntu kernel: [  139.528567]    groups: 0-1 (__cpu_power = 2048)
Mar 21 08:27:57 ubuntu kernel: [  151.845598] CPU0 attaching NULL sched-domain.
Mar 21 08:27:57 ubuntu kernel: [  151.845603] CPU1 attaching NULL sched-domain.
Mar 21 08:27:57 ubuntu kernel: [  151.860586] CPU0 attaching sched-domain:
Mar 21 08:27:57 ubuntu kernel: [  151.860590]  domain 0: span 0-1 level MC
Mar 21 08:27:57 ubuntu kernel: [  151.860592]   groups: 0 1
Mar 21 08:27:57 ubuntu kernel: [  151.860597] CPU1 attaching sched-domain:
Mar 21 08:27:57 ubuntu kernel: [  151.860599]  domain 0: span 0-1 level MC
Mar 21 08:27:57 ubuntu kernel: [  151.860600]   groups: 1 0
Mar 21 09:15:00 ubuntu kernel: [ 2974.996878] usb 1-5: USB disconnect, address 4
Mar 21 09:15:00 ubuntu kernel: [ 2974.997254] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:15:00 ubuntu kernel: [ 2974.997285] ipaq 1-5:1.0: device disconnected
Mar 21 09:15:31 ubuntu kernel: [ 3005.856074] usb 1-6: new high speed USB device using ehci_hcd and address 5
Mar 21 09:15:31 ubuntu kernel: [ 3005.990057] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:15:31 ubuntu kernel: [ 3005.990978] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:15:31 ubuntu kernel: [ 3005.991430] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:16:04 ubuntu kernel: [ 3038.299162] usb 1-6: USB disconnect, address 5
Mar 21 09:16:04 ubuntu kernel: [ 3038.299438] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:16:04 ubuntu kernel: [ 3038.299466] ipaq 1-6:1.0: device disconnected
Mar 21 09:16:25 ubuntu kernel: [ 3059.928075] usb 1-6: new high speed USB device using ehci_hcd and address 6
Mar 21 09:16:25 ubuntu kernel: [ 3060.061964] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:16:25 ubuntu kernel: [ 3060.064923] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:16:25 ubuntu kernel: [ 3060.065424] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:17:10 ubuntu kernel: [ 3105.150691] usb 1-6: USB disconnect, address 6
Mar 21 09:17:10 ubuntu kernel: [ 3105.150973] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:17:10 ubuntu kernel: [ 3105.151001] ipaq 1-6:1.0: device disconnected
Mar 21 09:17:28 ubuntu kernel: [ 3122.948074] usb 1-6: new high speed USB device using ehci_hcd and address 7
Mar 21 09:17:28 ubuntu kernel: [ 3123.082106] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:17:28 ubuntu kernel: [ 3123.083160] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:17:28 ubuntu kernel: [ 3123.083598] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:17:40 ubuntu kernel: [ 3134.746268] usb 1-6: USB disconnect, address 7
Mar 21 09:17:40 ubuntu kernel: [ 3134.746553] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:17:40 ubuntu kernel: [ 3134.746582] ipaq 1-6:1.0: device disconnected
Mar 21 09:17:52 ubuntu kernel: [ 3146.952062] usb 1-6: new high speed USB device using ehci_hcd and address 8
Mar 21 09:17:52 ubuntu kernel: [ 3147.085976] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:17:52 ubuntu kernel: [ 3147.086900] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:17:52 ubuntu kernel: [ 3147.087346] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:29:25 ubuntu kernel: [ 3839.973549] usb 1-6: USB disconnect, address 8
Mar 21 09:29:25 ubuntu kernel: [ 3839.973826] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:29:25 ubuntu kernel: [ 3839.973855] ipaq 1-6:1.0: device disconnected
Mar 21 09:29:48 ubuntu kernel: [ 3862.432535] usb 1-6: new high speed USB device using ehci_hcd and address 9
Mar 21 09:29:48 ubuntu kernel: [ 3862.570004] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:29:48 ubuntu kernel: [ 3862.570978] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:29:48 ubuntu kernel: [ 3862.571844] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:35:23 ubuntu kernel: [ 4197.650374] usb 1-6: USB disconnect, address 9
Mar 21 09:35:23 ubuntu kernel: [ 4197.650693] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:35:23 ubuntu kernel: [ 4197.650722] ipaq 1-6:1.0: device disconnected
Mar 21 09:35:29 ubuntu kernel: [ 4203.576079] usb 1-6: new high speed USB device using ehci_hcd and address 10
Mar 21 09:35:29 ubuntu kernel: [ 4203.709976] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:35:29 ubuntu kernel: [ 4203.710892] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:35:29 ubuntu kernel: [ 4203.711348] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:35:36 ubuntu kernel: [ 4210.188701] usb 1-6: USB disconnect, address 10
Mar 21 09:35:36 ubuntu kernel: [ 4210.188984] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:35:36 ubuntu kernel: [ 4210.189013] ipaq 1-6:1.0: device disconnected
Mar 21 09:35:52 ubuntu kernel: [ 4226.796080] usb 1-6: new high speed USB device using ehci_hcd and address 11
Mar 21 09:35:52 ubuntu kernel: [ 4226.930542] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:35:52 ubuntu kernel: [ 4226.931453] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:35:52 ubuntu kernel: [ 4226.931919] usb 1-6: PocketPC PDA converter now attached to ttyUSB0








```[/INDENT]

---

### Post by cadogan281 on 2010-03-21
this was the other code just incase you needed it.so its mounted as ttyUSB0 but i cant access it?

```
 
Mar 21 08:26:48 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 21 08:26:48 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1358" x-info="http://www.rsyslog.com"] (re)start
Mar 21 08:26:48 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Mar 21 08:26:48 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Mar 21 08:26:48 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ee0000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b7ef0000 - 00000000b7f00000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b8000000 - 00000000c0000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] DMI present.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] last_pfn = 0xb7ee0 max_arch_pfn = 0x100000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 21 08:26:48 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000b7ee0000 (usable)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b7ef0000 - 00000000b7f00000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000b8000000 - 00000000c0000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 21 08:26:48 ubuntu kernel: [    0.000000] RAMDISK: 7fa82000 - 7ffff098
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007fa82000 - 000000007ffff097 to 008ad000 - 00e2a097
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: RSDP 000f7500 00024 (v02 HPQOEM)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: XSDT b7ee3100 00054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: FACP b7ee7e80 000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: DSDT b7ee32c0 04B61 (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: FACS b7ee0000 00040
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: SLIC b7ee80c0 00176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: SSDT b7ee8280 0095E (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: HPET b7ee8c40 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: MCFG b7ee8cc0 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: APIC b7ee7fc0 00098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] 2054MB HIGHMEM available.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Mar 21 08:26:48 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #5 [00008a9000 - 00008ac5b0]              BRK ==> [00008a9000 - 00008ac5b0]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 21 08:26:48 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f53c0] f53c0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 21 08:26:48 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x000b7ee0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 21 08:26:48 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000b7ee0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using APIC driver default
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 21 08:26:48 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 21 08:26:48 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages at c2710000, static data 35612 bytes
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747377
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Mar 21 08:26:48 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 21 08:26:48 ubuntu kernel: [    0.000000] allocated 15067200 bytes of page_cgroup
Mar 21 08:26:48 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000b7ee0)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Memory: 2959336k/3013504k available (4565k kernel code, 52852k reserved, 2143k data, 540k init, 2104200k highmem)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 21 08:26:48 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 21 08:26:48 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 21 08:26:48 ubuntu kernel: [    0.000000] Detected 2712.787 MHz processor.
Mar 21 08:26:48 ubuntu kernel: [    0.003280] Console: colour VGA+ 80x25
Mar 21 08:26:48 ubuntu kernel: [    0.003282] console [tty0] enabled
Mar 21 08:26:48 ubuntu kernel: [    0.003417] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Mar 21 08:26:48 ubuntu kernel: [    0.003423] Calibrating delay loop (skipped), value calculated using timer frequency.. 5425.57 BogoMIPS (lpj=10851148)
Mar 21 08:26:48 ubuntu kernel: [    0.003436] Security Framework initialized
Mar 21 08:26:48 ubuntu kernel: [    0.003450] AppArmor: AppArmor initialized
Mar 21 08:26:48 ubuntu kernel: [    0.003456] Mount-cache hash table entries: 512
Mar 21 08:26:48 ubuntu kernel: [    0.003539] Initializing cgroup subsys ns
Mar 21 08:26:48 ubuntu kernel: [    0.003542] Initializing cgroup subsys cpuacct
Mar 21 08:26:48 ubuntu kernel: [    0.003545] Initializing cgroup subsys memory
Mar 21 08:26:48 ubuntu kernel: [    0.003549] Initializing cgroup subsys freezer
Mar 21 08:26:48 ubuntu kernel: [    0.003551] Initializing cgroup subsys net_cls
Mar 21 08:26:48 ubuntu kernel: [    0.003560] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.003562] CPU: L2 Cache: 512K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.003564] CPU: Physical Processor ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.003565] CPU: Processor Core ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.003567] mce: CPU supports 6 MCE banks
Mar 21 08:26:48 ubuntu kernel: [    0.003574] using C1E aware idle routine
Mar 21 08:26:48 ubuntu kernel: [    0.003579] Performance Counters: AMD PMU driver.
Mar 21 08:26:48 ubuntu kernel: [    0.003584] ... version:                 0
Mar 21 08:26:48 ubuntu kernel: [    0.003585] ... bit width:               48
Mar 21 08:26:48 ubuntu kernel: [    0.003586] ... generic counters:        4
Mar 21 08:26:48 ubuntu kernel: [    0.003588] ... value mask:              0000ffffffffffff
Mar 21 08:26:48 ubuntu kernel: [    0.003589] ... max period:              00007fffffffffff
Mar 21 08:26:48 ubuntu kernel: [    0.003591] ... fixed-purpose counters:  0
Mar 21 08:26:48 ubuntu kernel: [    0.003592] ... counter mask:            000000000000000f
Mar 21 08:26:48 ubuntu kernel: [    0.003595] Checking 'hlt' instruction... OK.
Mar 21 08:26:48 ubuntu kernel: [    0.017599] ACPI: Core revision 20090521
Mar 21 08:26:48 ubuntu kernel: [    0.024515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 21 08:26:48 ubuntu kernel: [    0.066966] CPU0: AMD Athlon(tm) II X2 215 Processor stepping 02
Mar 21 08:26:48 ubuntu kernel: [    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
Mar 21 08:26:48 ubuntu kernel: [    0.004000] Initializing CPU#1
Mar 21 08:26:48 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 5424.64 BogoMIPS (lpj=10849283)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 21 08:26:48 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Mar 21 08:26:48 ubuntu kernel: [    0.004000] mce: CPU supports 6 MCE banks
Mar 21 08:26:48 ubuntu kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Mar 21 08:26:48 ubuntu kernel: [    0.152484] CPU1: AMD Athlon(tm) II X2 215 Processor stepping 02
Mar 21 08:26:48 ubuntu kernel: [    0.152494] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 21 08:26:48 ubuntu kernel: [    0.156010] Brought up 2 CPUs
Mar 21 08:26:48 ubuntu kernel: [    0.156012] Total of 2 processors activated (10850.21 BogoMIPS).
Mar 21 08:26:48 ubuntu kernel: [    0.156158] Booting paravirtualized kernel on bare hardware
Mar 21 08:26:48 ubuntu kernel: [    0.156158] regulator: core version 0.5
Mar 21 08:26:48 ubuntu kernel: [    0.156158] Time:  8:25:25  Date: 03/21/10
Mar 21 08:26:48 ubuntu kernel: [    0.156158] NET: Registered protocol family 16
Mar 21 08:26:48 ubuntu kernel: [    0.156164] EISA bus registered
Mar 21 08:26:48 ubuntu kernel: [    0.156176] ACPI: bus type pci registered
Mar 21 08:26:48 ubuntu kernel: [    0.156229] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Mar 21 08:26:48 ubuntu kernel: [    0.156232] PCI: MCFG area at f0000000 reserved in E820
Mar 21 08:26:48 ubuntu kernel: [    0.156233] PCI: Using MMCONFIG for extended config space
Mar 21 08:26:48 ubuntu kernel: [    0.156235] PCI: Using configuration type 1 for base access
Mar 21 08:26:48 ubuntu kernel: [    0.156818] bio: create slab <bio-0> at 0
Mar 21 08:26:48 ubuntu kernel: [    0.164071] ACPI: Interpreter enabled
Mar 21 08:26:48 ubuntu kernel: [    0.164077] ACPI: (supports S0 S1 S3 S4 S5)
Mar 21 08:26:48 ubuntu kernel: [    0.164098] ACPI: Using IOAPIC for interrupt routing
Mar 21 08:26:48 ubuntu kernel: [    0.168675] ACPI: No dock devices found.
Mar 21 08:26:48 ubuntu kernel: [    0.168766] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 21 08:26:48 ubuntu kernel: [    0.168990] pci 0000:00:01.1: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.168995] pci 0000:00:01.1: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169059] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169061] pci 0000:00:02.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169106] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169109] pci 0000:00:02.1: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169185] pci 0000:00:05.0: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169188] pci 0000:00:05.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169240] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169244] pci 0000:00:07.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169360] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169362] pci 0000:00:09.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169389] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169391] pci 0000:00:0b.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169418] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169420] pci 0000:00:0c.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.169551] pci 0000:00:04.0: transparent bridge
Mar 21 08:26:48 ubuntu kernel: [    0.169698] pci 0000:04:00.0: PME# supported from D3hot D3cold
Mar 21 08:26:48 ubuntu kernel: [    0.169701] pci 0000:04:00.0: PME# disabled
Mar 21 08:26:48 ubuntu kernel: [    0.197392] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197489] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197583] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197677] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197772] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.197866] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.197959] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198053] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198149] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198242] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198337] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198432] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198528] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198622] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.198717] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198812] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.198908] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199003] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.199099] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Mar 21 08:26:48 ubuntu kernel: [    0.199226] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199348] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199469] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199589] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199708] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Mar 21 08:26:48 ubuntu kernel: [    0.199828] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.199949] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200077] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200197] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200317] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200439] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200564] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.200688] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200808] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.200928] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201048] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.201169] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
Mar 21 08:26:48 ubuntu kernel: [    0.201290] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201410] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0
Mar 21 08:26:48 ubuntu kernel: [    0.201539] SCSI subsystem initialized
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new interface driver usbfs
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new interface driver hub
Mar 21 08:26:48 ubuntu kernel: [    0.201579] usbcore: registered new device driver usb
Mar 21 08:26:48 ubuntu kernel: [    0.201579] ACPI: WMI: Mapper loaded
Mar 21 08:26:48 ubuntu kernel: [    0.201579] PCI: Using ACPI for IRQ routing
Mar 21 08:26:48 ubuntu kernel: [    0.212006] Bluetooth: Core ver 2.15
Mar 21 08:26:48 ubuntu kernel: [    0.212015] NET: Registered protocol family 31
Mar 21 08:26:48 ubuntu kernel: [    0.212015] Bluetooth: HCI device and connection manager initialized
Mar 21 08:26:48 ubuntu kernel: [    0.212015] Bluetooth: HCI socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    0.212016] NetLabel: Initializing
Mar 21 08:26:48 ubuntu kernel: [    0.212017] NetLabel:  domain hash size = 128
Mar 21 08:26:48 ubuntu kernel: [    0.212019] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 21 08:26:48 ubuntu kernel: [    0.212028] NetLabel:  unlabeled traffic allowed by default
Mar 21 08:26:48 ubuntu kernel: [    0.212052] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
Mar 21 08:26:48 ubuntu kernel: [    0.212055] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Mar 21 08:26:48 ubuntu kernel: [    0.228008] pnp: PnP ACPI init
Mar 21 08:26:48 ubuntu kernel: [    0.228025] ACPI: bus type pnp registered
Mar 21 08:26:48 ubuntu kernel: [    0.229898] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) 20090521 dsopcode-596
Mar 21 08:26:48 ubuntu kernel: [    0.229904] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.MEM_._CRS] (Node f7017f60), AE_AML_BUFFER_LIMIT
Mar 21 08:26:48 ubuntu kernel: [    0.229924] ACPI Error (uteval-0256): Method execution failed [\_SB_.MEM_._CRS] (Node f7017f60), AE_AML_BUFFER_LIMIT
Mar 21 08:26:48 ubuntu kernel: [    0.229966] pnp: PnP ACPI: found 10 devices
Mar 21 08:26:48 ubuntu kernel: [    0.229967] ACPI: ACPI bus type pnp unregistered
Mar 21 08:26:48 ubuntu kernel: [    0.229970] PnPBIOS: Disabled by ACPI PNP
Mar 21 08:26:48 ubuntu kernel: [    0.229979] system 00:01: ioport range 0x1000-0x107f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229981] system 00:01: ioport range 0x1080-0x10ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229983] system 00:01: ioport range 0x1400-0x147f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229985] system 00:01: ioport range 0x1480-0x14ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229987] system 00:01: ioport range 0x1800-0x187f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229989] system 00:01: ioport range 0x1880-0x18ff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229993] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229995] system 00:02: ioport range 0x800-0x87f has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.229997] system 00:02: ioport range 0x294-0x297 has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.230002] system 00:08: iomem range 0xf0000000-0xf3ffffff has been reserved
Mar 21 08:26:48 ubuntu kernel: [    0.264619] AppArmor: AppArmor Filesystem Enabled
Mar 21 08:26:48 ubuntu kernel: [    0.264642] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Mar 21 08:26:48 ubuntu kernel: [    0.264644] pci 0000:00:04.0:   IO window: 0xe000-0xefff
Mar 21 08:26:48 ubuntu kernel: [    0.264647] pci 0000:00:04.0:   MEM window: 0xfd700000-0xfd7fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264650] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
Mar 21 08:26:48 ubuntu kernel: [    0.264654] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Mar 21 08:26:48 ubuntu kernel: [    0.264656] pci 0000:00:09.0:   IO window: 0xd000-0xdfff
Mar 21 08:26:48 ubuntu kernel: [    0.264658] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264661] pci 0000:00:09.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264663] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Mar 21 08:26:48 ubuntu kernel: [    0.264665] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
Mar 21 08:26:48 ubuntu kernel: [    0.264668] pci 0000:00:0b.0:   MEM window: 0xfdb00000-0xfdbfffff
Mar 21 08:26:48 ubuntu kernel: [    0.264670] pci 0000:00:0b.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
Mar 21 08:26:48 ubuntu kernel: [    0.264673] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Mar 21 08:26:48 ubuntu kernel: [    0.264675] pci 0000:00:0c.0:   IO window: 0xb000-0xbfff
Mar 21 08:26:48 ubuntu kernel: [    0.264677] pci 0000:00:0c.0:   MEM window: 0xfd900000-0xfd9fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264679] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
Mar 21 08:26:48 ubuntu kernel: [    0.264756] NET: Registered protocol family 2
Mar 21 08:26:48 ubuntu kernel: [    0.264826] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265050] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265516] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 21 08:26:48 ubuntu kernel: [    0.265732] TCP: Hash tables configured (established 131072 bind 65536)
Mar 21 08:26:48 ubuntu kernel: [    0.265734] TCP reno registered
Mar 21 08:26:48 ubuntu kernel: [    0.265804] NET: Registered protocol family 1
Mar 21 08:26:48 ubuntu kernel: [    0.265853] Trying to unpack rootfs image as initramfs...
Mar 21 08:26:48 ubuntu kernel: [    1.240431] Freeing initrd memory: 5620k freed
Mar 21 08:26:48 ubuntu kernel: [    1.242588] cpufreq-nforce2: No nForce2 chipset.
Mar 21 08:26:48 ubuntu kernel: [    1.242606] Scanning for low memory corruption every 60 seconds
Mar 21 08:26:48 ubuntu kernel: [    1.242679] audit: initializing netlink socket (disabled)
Mar 21 08:26:48 ubuntu kernel: [    1.242690] type=2000 audit(1269159926.240:1): initialized
Mar 21 08:26:48 ubuntu kernel: [    1.248960] highmem bounce pool size: 64 pages
Mar 21 08:26:48 ubuntu kernel: [    1.248964] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 21 08:26:48 ubuntu kernel: [    1.249902] VFS: Disk quotas dquot_6.5.2
Mar 21 08:26:48 ubuntu kernel: [    1.249942] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 21 08:26:48 ubuntu kernel: [    1.250322] fuse init (API version 7.12)
Mar 21 08:26:48 ubuntu kernel: [    1.250377] msgmni has been set to 1682
Mar 21 08:26:48 ubuntu kernel: [    1.250546] alg: No test for stdrng (krng)
Mar 21 08:26:48 ubuntu kernel: [    1.250567] io scheduler noop registered
Mar 21 08:26:48 ubuntu kernel: [    1.250569] io scheduler anticipatory registered
Mar 21 08:26:48 ubuntu kernel: [    1.250570] io scheduler deadline registered
Mar 21 08:26:48 ubuntu kernel: [    1.250600] io scheduler cfq registered (default)
Mar 21 08:26:48 ubuntu kernel: [    1.250698] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250743] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250792] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250843] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250894] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.250949] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251008] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251071] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 21 08:26:48 ubuntu kernel: [    1.251322] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 21 08:26:48 ubuntu kernel: [    1.251340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 21 08:26:48 ubuntu kernel: [    1.251425] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 21 08:26:48 ubuntu kernel: [    1.251428] ACPI: Power Button [PWRF]
Mar 21 08:26:48 ubuntu kernel: [    1.251464] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Mar 21 08:26:48 ubuntu kernel: [    1.251466] ACPI: Power Button [PWRB]
Mar 21 08:26:48 ubuntu kernel: [    1.251506] fan PNP0C0B:00: registered as cooling_device0
Mar 21 08:26:48 ubuntu kernel: [    1.251509] ACPI: Fan [FAN] (on)
Mar 21 08:26:48 ubuntu kernel: [    1.251734] processor LNXCPU:00: registered as cooling_device1
Mar 21 08:26:48 ubuntu kernel: [    1.251760] processor LNXCPU:01: registered as cooling_device2
Mar 21 08:26:48 ubuntu kernel: [    1.253978] ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference 20090521 nspredef-946
Mar 21 08:26:48 ubuntu kernel: [    1.253985] ACPI: Invalid passive threshold
Mar 21 08:26:48 ubuntu kernel: [    1.254214] thermal LNXTHERM:01: registered as thermal_zone0
Mar 21 08:26:48 ubuntu kernel: [    1.254218] ACPI: Thermal Zone [THRM] (40 C)
Mar 21 08:26:48 ubuntu kernel: [    1.254258] isapnp: Scanning for PnP cards...
Mar 21 08:26:48 ubuntu kernel: [    1.606935] isapnp: No Plug & Play device found
Mar 21 08:26:48 ubuntu kernel: [    1.607732] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 21 08:26:48 ubuntu kernel: [    1.608513] brd: module loaded
Mar 21 08:26:48 ubuntu kernel: [    1.608787] loop: module loaded
Mar 21 08:26:48 ubuntu kernel: [    1.608839] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Mar 21 08:26:48 ubuntu kernel: [    1.609204] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Mar 21 08:26:48 ubuntu kernel: [    1.609219] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
Mar 21 08:26:48 ubuntu kernel: [    1.609330] scsi0 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609406] scsi1 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609508] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf700 irq 20
Mar 21 08:26:48 ubuntu kernel: [    1.609510] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf708 irq 20
Mar 21 08:26:48 ubuntu kernel: [    1.609717] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
Mar 21 08:26:48 ubuntu kernel: [    1.609727] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 21 (level, low) -> IRQ 21
Mar 21 08:26:48 ubuntu kernel: [    1.609863] scsi2 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609900] scsi3 : sata_nv
Mar 21 08:26:48 ubuntu kernel: [    1.609994] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf200 irq 21
Mar 21 08:26:48 ubuntu kernel: [    1.609996] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf208 irq 21
Mar 21 08:26:48 ubuntu kernel: [    1.610485] Fixed MDIO Bus: probed
Mar 21 08:26:48 ubuntu kernel: [    1.610507] PPP generic driver version 2.4.2
Mar 21 08:26:48 ubuntu kernel: [    1.610577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 21 08:26:48 ubuntu kernel: [    1.610786] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    1.610795] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    1.610805] ehci_hcd 0000:00:02.1: EHCI Host Controller
Mar 21 08:26:48 ubuntu kernel: [    1.610840] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Mar 21 08:26:48 ubuntu kernel: [    1.610862] ehci_hcd 0000:00:02.1: debug port 1
Mar 21 08:26:48 ubuntu kernel: [    1.610880] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
Mar 21 08:26:48 ubuntu kernel: [    1.621189] ata3: SATA link down (SStatus 0 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.624531] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Mar 21 08:26:48 ubuntu kernel: [    1.624620] usb usb1: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    1.624640] hub 1-0:1.0: USB hub found
Mar 21 08:26:48 ubuntu kernel: [    1.624646] hub 1-0:1.0: 10 ports detected
Mar 21 08:26:48 ubuntu kernel: [    1.624701] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 21 08:26:48 ubuntu kernel: [    1.624952] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Mar 21 08:26:48 ubuntu kernel: [    1.624966] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
Mar 21 08:26:48 ubuntu kernel: [    1.624981] ohci_hcd 0000:00:02.0: OHCI Host Controller
Mar 21 08:26:48 ubuntu kernel: [    1.625005] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Mar 21 08:26:48 ubuntu kernel: [    1.625029] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfe02f000
Mar 21 08:26:48 ubuntu kernel: [    1.682027] usb usb2: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    1.682043] hub 2-0:1.0: USB hub found
Mar 21 08:26:48 ubuntu kernel: [    1.682049] hub 2-0:1.0: 10 ports detected
Mar 21 08:26:48 ubuntu kernel: [    1.682087] uhci_hcd: USB Universal Host Controller Interface driver
Mar 21 08:26:48 ubuntu kernel: [    1.682145] PNP: No PS/2 controller found. Probing ports directly.
Mar 21 08:26:48 ubuntu kernel: [    1.684313] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 21 08:26:48 ubuntu kernel: [    1.684318] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 21 08:26:48 ubuntu kernel: [    1.684355] mice: PS/2 mouse device common for all mice
Mar 21 08:26:48 ubuntu kernel: [    1.684417] rtc_cmos 00:05: RTC can wake from S4
Mar 21 08:26:48 ubuntu kernel: [    1.684444] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Mar 21 08:26:48 ubuntu kernel: [    1.684480] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Mar 21 08:26:48 ubuntu kernel: [    1.684551] device-mapper: uevent: version 1.0.3
Mar 21 08:26:48 ubuntu kernel: [    1.684645] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Mar 21 08:26:48 ubuntu kernel: [    1.684715] device-mapper: multipath: version 1.1.0 loaded
Mar 21 08:26:48 ubuntu kernel: [    1.684718] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 21 08:26:48 ubuntu kernel: [    1.684800] EISA: Probing bus 0 at eisa.0
Mar 21 08:26:48 ubuntu kernel: [    1.684804] Cannot allocate resource for EISA slot 1
Mar 21 08:26:48 ubuntu kernel: [    1.684821] EISA: Detected 0 cards.
Mar 21 08:26:48 ubuntu kernel: [    1.684904] cpuidle: using governor ladder
Mar 21 08:26:48 ubuntu kernel: [    1.684905] cpuidle: using governor menu
Mar 21 08:26:48 ubuntu kernel: [    1.685246] TCP cubic registered
Mar 21 08:26:48 ubuntu kernel: [    1.685347] NET: Registered protocol family 10
Mar 21 08:26:48 ubuntu kernel: [    1.685656] lo: Disabled Privacy Extensions
Mar 21 08:26:48 ubuntu kernel: [    1.685879] NET: Registered protocol family 17
Mar 21 08:26:48 ubuntu kernel: [    1.685891] Bluetooth: L2CAP ver 2.13
Mar 21 08:26:48 ubuntu kernel: [    1.685892] Bluetooth: L2CAP socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685894] Bluetooth: SCO (Voice Link) ver 0.6
Mar 21 08:26:48 ubuntu kernel: [    1.685896] Bluetooth: SCO socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685937] Bluetooth: RFCOMM TTY layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685939] Bluetooth: RFCOMM socket layer initialized
Mar 21 08:26:48 ubuntu kernel: [    1.685940] Bluetooth: RFCOMM ver 1.11
Mar 21 08:26:48 ubuntu kernel: [    1.685956] powernow-k8: Found 1 AMD Athlon(tm) II X2 215 Processor processors (2 cpu cores) (version 2.20.00)
Mar 21 08:26:48 ubuntu kernel: [    1.685988] powernow-k8:    0 : pstate 0 (2700 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685990] powernow-k8:    1 : pstate 1 (2100 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685991] powernow-k8:    2 : pstate 2 (1500 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.685993] powernow-k8:    3 : pstate 3 (800 MHz)
Mar 21 08:26:48 ubuntu kernel: [    1.686106] Using IPI No-Shortcut mode
Mar 21 08:26:48 ubuntu kernel: [    1.686161] registered taskstats version 1
Mar 21 08:26:48 ubuntu kernel: [    1.686249]   Magic number: 2:779:422
Mar 21 08:26:48 ubuntu kernel: [    1.686341] rtc_cmos 00:05: setting system clock to 2010-03-21 08:25:27 UTC (1269159927)
Mar 21 08:26:48 ubuntu kernel: [    1.686345] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 21 08:26:48 ubuntu kernel: [    1.686347] EDD information not available.
Mar 21 08:26:48 ubuntu kernel: [    1.764043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.788144] ata1.00: ATA-8: Hitachi HDP725050GLA360, GM4OA57A, max UDMA/133
Mar 21 08:26:48 ubuntu kernel: [    1.788147] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 21 08:26:48 ubuntu kernel: [    1.804151] ata1.00: configured for UDMA/133
Mar 21 08:26:48 ubuntu kernel: [    1.804270] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
Mar 21 08:26:48 ubuntu kernel: [    1.804376] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 21 08:26:48 ubuntu kernel: [    1.804404] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Mar 21 08:26:48 ubuntu kernel: [    1.804430] sd 0:0:0:0: [sda] Write Protect is off
Mar 21 08:26:48 ubuntu kernel: [    1.804445] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 21 08:26:48 ubuntu kernel: [    1.804535]  sda: sda1 sda2 sda3
Mar 21 08:26:48 ubuntu kernel: [    1.827930] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 21 08:26:48 ubuntu kernel: [    1.960044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    1.968141] ata2.00: ATAPI: hp      DVD-RAM GH40L, RB0A, max UDMA/100
Mar 21 08:26:48 ubuntu kernel: [    1.984154] ata2.00: configured for UDMA/100
Mar 21 08:26:48 ubuntu kernel: [    1.989783] scsi 1:0:0:0: CD-ROM            hp       DVD-RAM GH40L    RB0A PQ: 0 ANSI: 5
Mar 21 08:26:48 ubuntu kernel: [    1.994047] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 21 08:26:48 ubuntu kernel: [    1.994049] Uniform CD-ROM driver Revision: 3.20
Mar 21 08:26:48 ubuntu kernel: [    1.994150] sr 1:0:0:0: Attached scsi generic sg1 type 5
Mar 21 08:26:48 ubuntu kernel: [    2.004462] ata4: SATA link down (SStatus 0 SControl 300)
Mar 21 08:26:48 ubuntu kernel: [    2.004512] Freeing unused kernel memory: 540k freed
Mar 21 08:26:48 ubuntu kernel: [    2.004737] Write protecting the kernel text: 4568k
Mar 21 08:26:48 ubuntu kernel: [    2.004764] Write protecting the kernel read-only data: 1836k
Mar 21 08:26:48 ubuntu kernel: [    2.052535] usb 1-5: new high speed USB device using ehci_hcd and address 4
Mar 21 08:26:48 ubuntu kernel: [    2.095329] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Mar 21 08:26:48 ubuntu kernel: [    2.095602] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    2.095607] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Mar 21 08:26:48 ubuntu kernel: [    2.190522] usb 1-5: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    2.492032] usb 2-1: new low speed USB device using ohci_hcd and address 2
Mar 21 08:26:48 ubuntu kernel: [    2.612905] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:e6:ba:14:d8:36
Mar 21 08:26:48 ubuntu kernel: [    2.612910] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Mar 21 08:26:48 ubuntu kernel: [    2.721938] usb 2-1: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    2.728674] usbcore: registered new interface driver hiddev
Mar 21 08:26:48 ubuntu kernel: [    2.734020] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
Mar 21 08:26:48 ubuntu kernel: [    2.734078] generic-usb 0003:0461:4D20.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:02.0-1/input0
Mar 21 08:26:48 ubuntu kernel: [    2.734092] usbcore: registered new interface driver usbhid
Mar 21 08:26:48 ubuntu kernel: [    2.734094] usbhid: v2.6:USB HID core driver
Mar 21 08:26:48 ubuntu kernel: [    3.023623] xor: automatically using best checksumming function: pIII_sse
Mar 21 08:26:48 ubuntu kernel: [    3.028515] usb 2-2: new low speed USB device using ohci_hcd and address 3
Mar 21 08:26:48 ubuntu kernel: [    3.040003]    pIII_sse  : 10878.000 MB/sec
Mar 21 08:26:48 ubuntu kernel: [    3.040006] xor: using function: pIII_sse (10878.000 MB/sec)
Mar 21 08:26:48 ubuntu kernel: [    3.041713] device-mapper: dm-raid45: initialized v0.2594b
Mar 21 08:26:48 ubuntu kernel: [    3.229858] usb 2-2: configuration #1 chosen from 1 choice
Mar 21 08:26:48 ubuntu kernel: [    3.240230] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
Mar 21 08:26:48 ubuntu kernel: [    3.240286] generic-usb 0003:0461:0010.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:02.0-2/input0
Mar 21 08:26:48 ubuntu kernel: [    3.252832] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input5
Mar 21 08:26:48 ubuntu kernel: [    3.252887] generic-usb 0003:0461:0010.0003: input,hidraw2: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:02.0-2/input1
Mar 21 08:26:48 ubuntu kernel: [    5.684341] aufs 2-standalone.tree-30-20090727
Mar 21 08:26:48 ubuntu kernel: [    5.918524] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Mar 21 08:26:48 ubuntu kernel: [   82.929313] udev: starting version 147
Mar 21 08:26:50 ubuntu kernel: [   84.668498] usbcore: registered new interface driver usbserial
Mar 21 08:26:50 ubuntu kernel: [   84.668513] USB Serial support registered for generic
Mar 21 08:26:50 ubuntu kernel: [   84.668533] usbcore: registered new interface driver usbserial_generic
Mar 21 08:26:50 ubuntu kernel: [   84.668535] usbserial: USB Serial Driver core
Mar 21 08:26:50 ubuntu kernel: [   85.052266] USB Serial support registered for PocketPC PDA
Mar 21 08:26:50 ubuntu kernel: [   85.052290] ipaq 1-5:1.0: PocketPC PDA converter detected
Mar 21 08:26:50 ubuntu kernel: [   85.053074] usb 1-5: PocketPC PDA converter now attached to ttyUSB0
Mar 21 08:26:50 ubuntu kernel: [   85.053099] usbcore: registered new interface driver ipaq
Mar 21 08:26:50 ubuntu kernel: [   85.053102] ipaq: v0.5:USB PocketPC PDA driver
Mar 21 08:26:51 ubuntu kernel: [   85.605461] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Mar 21 08:26:51 ubuntu kernel: [   85.605476] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
Mar 21 08:26:56 ubuntu kernel: [   90.754728] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 21 08:27:00 ubuntu kernel: [   95.063121] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Mar 21 08:27:00 ubuntu kernel: [   95.063126] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Mar 21 08:27:01 ubuntu kernel: [   95.908535] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Mar 21 08:27:01 ubuntu kernel: [   95.908614] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
Mar 21 08:27:11 ubuntu kernel: [  105.515470] lp: driver loaded but no devices found
Mar 21 08:27:12 ubuntu kernel: [  106.319053] ppdev: user-space parallel port driver
Mar 21 08:27:28 ubuntu kernel: [  122.556924] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 21 08:27:28 ubuntu kernel: [  122.556928] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:28 ubuntu kernel: [  122.556931] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 21 08:27:28 ubuntu kernel: [  122.556935] Info fld=0x1caba
Mar 21 08:27:28 ubuntu kernel: [  122.556936] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 21 08:27:34 ubuntu kernel: [  128.797836] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 21 08:27:34 ubuntu kernel: [  128.797840] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:34 ubuntu kernel: [  128.797842] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 21 08:27:34 ubuntu kernel: [  128.797846] Info fld=0x1caca
Mar 21 08:27:34 ubuntu kernel: [  128.797848] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
Mar 21 08:27:34 ubuntu kernel: [  128.797855] __ratelimit: 6 callbacks suppressed
Mar 21 08:27:40 ubuntu kernel: [  134.980655] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.980659] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.980662] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.980664] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.980671] __ratelimit: 54 callbacks suppressed
Mar 21 08:27:40 ubuntu kernel: [  134.985668] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.985672] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.985676] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.985677] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.991204] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.991209] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.991212] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.991214] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  134.996223] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  134.996227] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  134.996231] Info fld=0x1caba, ILI
Mar 21 08:27:40 ubuntu kernel: [  134.996232] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.001316] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.001321] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.001324] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.001325] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.006509] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.006514] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.006518] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.006519] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.011762] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.011766] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.011770] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.011771] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.016706] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.016710] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.016714] Info fld=0x1cabc, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.016715] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.021469] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.021474] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.021478] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.021479] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.024733] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.024735] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.024738] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.024739] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 08:27:40 ubuntu kernel: [  135.028005] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 21 08:27:40 ubuntu kernel: [  135.028009] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 21 08:27:40 ubuntu kernel: [  135.028013] Info fld=0x1cabe, ILI
Mar 21 08:27:40 ubuntu kernel: [  135.028014] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 21 09:15:00 ubuntu kernel: [ 2974.996878] usb 1-5: USB disconnect, address 4
Mar 21 09:15:00 ubuntu kernel: [ 2974.997254] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:15:00 ubuntu kernel: [ 2974.997285] ipaq 1-5:1.0: device disconnected
Mar 21 09:15:31 ubuntu kernel: [ 3005.856074] usb 1-6: new high speed USB device using ehci_hcd and address 5
Mar 21 09:15:31 ubuntu kernel: [ 3005.990057] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:15:31 ubuntu kernel: [ 3005.990978] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:15:31 ubuntu kernel: [ 3005.991430] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:16:04 ubuntu kernel: [ 3038.299162] usb 1-6: USB disconnect, address 5
Mar 21 09:16:04 ubuntu kernel: [ 3038.299438] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:16:04 ubuntu kernel: [ 3038.299466] ipaq 1-6:1.0: device disconnected
Mar 21 09:16:25 ubuntu kernel: [ 3059.928075] usb 1-6: new high speed USB device using ehci_hcd and address 6
Mar 21 09:16:25 ubuntu kernel: [ 3060.061964] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:16:25 ubuntu kernel: [ 3060.064923] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:16:25 ubuntu kernel: [ 3060.065424] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:17:10 ubuntu kernel: [ 3105.150691] usb 1-6: USB disconnect, address 6
Mar 21 09:17:10 ubuntu kernel: [ 3105.150973] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:17:10 ubuntu kernel: [ 3105.151001] ipaq 1-6:1.0: device disconnected
Mar 21 09:17:28 ubuntu kernel: [ 3122.948074] usb 1-6: new high speed USB device using ehci_hcd and address 7
Mar 21 09:17:28 ubuntu kernel: [ 3123.082106] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:17:28 ubuntu kernel: [ 3123.083160] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:17:28 ubuntu kernel: [ 3123.083598] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:17:40 ubuntu kernel: [ 3134.746268] usb 1-6: USB disconnect, address 7
Mar 21 09:17:40 ubuntu kernel: [ 3134.746553] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:17:40 ubuntu kernel: [ 3134.746582] ipaq 1-6:1.0: device disconnected
Mar 21 09:17:52 ubuntu kernel: [ 3146.952062] usb 1-6: new high speed USB device using ehci_hcd and address 8
Mar 21 09:17:52 ubuntu kernel: [ 3147.085976] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:17:52 ubuntu kernel: [ 3147.086900] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:17:52 ubuntu kernel: [ 3147.087346] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:29:25 ubuntu kernel: [ 3839.973549] usb 1-6: USB disconnect, address 8
Mar 21 09:29:25 ubuntu kernel: [ 3839.973826] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:29:25 ubuntu kernel: [ 3839.973855] ipaq 1-6:1.0: device disconnected
Mar 21 09:29:48 ubuntu kernel: [ 3862.432535] usb 1-6: new high speed USB device using ehci_hcd and address 9
Mar 21 09:29:48 ubuntu kernel: [ 3862.570004] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:29:48 ubuntu kernel: [ 3862.570978] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:29:48 ubuntu kernel: [ 3862.571844] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:35:23 ubuntu kernel: [ 4197.650374] usb 1-6: USB disconnect, address 9
Mar 21 09:35:23 ubuntu kernel: [ 4197.650693] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:35:23 ubuntu kernel: [ 4197.650722] ipaq 1-6:1.0: device disconnected
Mar 21 09:35:29 ubuntu kernel: [ 4203.576079] usb 1-6: new high speed USB device using ehci_hcd and address 10
Mar 21 09:35:29 ubuntu kernel: [ 4203.709976] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:35:29 ubuntu kernel: [ 4203.710892] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:35:29 ubuntu kernel: [ 4203.711348] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
Mar 21 09:35:36 ubuntu kernel: [ 4210.188701] usb 1-6: USB disconnect, address 10
Mar 21 09:35:36 ubuntu kernel: [ 4210.188984] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 21 09:35:36 ubuntu kernel: [ 4210.189013] ipaq 1-6:1.0: device disconnected
Mar 21 09:35:52 ubuntu kernel: [ 4226.796080] usb 1-6: new high speed USB device using ehci_hcd and address 11
Mar 21 09:35:52 ubuntu kernel: [ 4226.930542] usb 1-6: configuration #1 chosen from 1 choice
Mar 21 09:35:52 ubuntu kernel: [ 4226.931453] ipaq 1-6:1.0: PocketPC PDA converter detected
Mar 21 09:35:52 ubuntu kernel: [ 4226.931919] usb 1-6: PocketPC PDA converter now attached to ttyUSB0






```

---

### Post by NightwishFan on 2010-03-21
I do not have any answers for you. Though I will not say it is impossible. Perhaps wait for other replys to this thread.

---

### Post by cadogan281 on 2010-03-21
thanks for the help though.hopefully other people may know some more about it.atleast its getting closer too getting it working.:)

---

### Post by NightwishFan on 2010-03-21
True. I know about how to mount things in Linux, but I will not advise someone to do something either error prone or I have not tried myself. I do not own a phone so I do not know how they work.

---

