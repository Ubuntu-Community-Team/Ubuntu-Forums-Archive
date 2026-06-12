---
title: "Some logs growing at very high rates"
date: 2010-05-12
forum: General Help
---

### Post by Tymorus on 2010-05-12
I upgraded from 9.10 to 10.4 on May 7.  I have discovered, by system warning, that the /var partition is very full.  After taking a look I discovered that the following logs have all grown to the size of about 1GB:


[LIST]
[*]kern.log
[*]messages
[*]ufw.log
[/LIST]
I will show a few sections from the above logs below:

These llines are from the beginning of the day the upgrade was done until a few minutes after it's completion.  These logs are quite long and I cannot possilbly post the full ones anywhere.  If any more pieces of them are needed I would be happy to provide them.

I need to know the cause of these long logs and how to stop them before my /var partition is filled.

[SIZE=4]Kern.log[SIZE=1]
[/SIZE][/SIZE]```

May  7 11:15:27 tymorus-desktop kernel: [132549.790117] usb 1-6: new high speed USB device using ehci_hcd and address 5
May  7 11:15:27 tymorus-desktop kernel: [132549.941971] usb 1-6: configuration #1 chosen from 1 choice
May  7 11:15:27 tymorus-desktop kernel: [132549.943338] scsi8 : SCSI emulation for USB Mass Storage devices
May  7 11:15:27 tymorus-desktop kernel: [132549.943492] usb-storage: device found at 5
May  7 11:15:27 tymorus-desktop kernel: [132549.943496] usb-storage: waiting for device to settle before scanning
May  7 11:15:32 tymorus-desktop kernel: [132554.940303] usb-storage: device scan complete
May  7 11:15:32 tymorus-desktop kernel: [132554.940781] scsi 8:0:0:0: Direct-Access     Seagate  FreeAgent Go     102F PQ: 0 ANSI: 4
May  7 11:15:32 tymorus-desktop kernel: [132554.941398] sd 8:0:0:0: Attached scsi generic sg3 type 0
May  7 11:15:32 tymorus-desktop kernel: [132554.950573] sd 8:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  7 11:15:32 tymorus-desktop kernel: [132554.951561] sd 8:0:0:0: [sdc] Write Protect is off
May  7 11:15:32 tymorus-desktop kernel: [132554.951567] sd 8:0:0:0: [sdc] Mode Sense: 1c 00 00 00
May  7 11:15:32 tymorus-desktop kernel: [132554.951572] sd 8:0:0:0: [sdc] Assuming drive cache: write through
May  7 11:15:32 tymorus-desktop kernel: [132554.953003] sd 8:0:0:0: [sdc] Assuming drive cache: write through
May  7 11:15:32 tymorus-desktop kernel: [132554.953010]  sdc: sdc1
May  7 11:15:32 tymorus-desktop kernel: [132554.980758] sd 8:0:0:0: [sdc] Assuming drive cache: write through
May  7 11:15:32 tymorus-desktop kernel: [132554.980765] sd 8:0:0:0: [sdc] Attached SCSI disk
May  7 11:16:24 tymorus-desktop kernel: [132606.821437] ISO 9660 Extensions: Microsoft Joliet Level 3
May  7 11:16:24 tymorus-desktop kernel: [132606.831663] ISO 9660 Extensions: RRIP_1991A
May  7 14:16:24 tymorus-desktop kernel: [143407.061307] type=1503 audit(1273256184.935:37): operation="open" pid=19619 parent=19618 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
May  7 14:17:01 tymorus-desktop kernel: [143443.405919] cron[23231]: segfault at 0 ip (null) sp 00007fff60396348 error 14 in cron[400000+9000]
May  7 14:18:06 tymorus-desktop kernel: [143508.167891] udev: starting version 151
May  7 14:26:42 tymorus-desktop kernel: [144024.893005] type=1505 audit(1273256802.765:38): operation="profile_replace" pid=15567 name=/usr/share/gdm/guest-session/Xsession
May  7 14:26:42 tymorus-desktop kernel: [144025.052513] type=1505 audit(1273256802.925:39): operation="profile_replace" pid=15568 name=/sbin/dhclient3
May  7 14:26:42 tymorus-desktop kernel: [144025.052662] type=1505 audit(1273256802.925:40): operation="profile_replace" pid=15568 name=/usr/lib/NetworkManager/nm-dhcp-client.action
May  7 14:26:42 tymorus-desktop kernel: [144025.052749] type=1505 audit(1273256802.925:41): operation="profile_replace" pid=15568 name=/usr/lib/connman/scripts/dhclient-script
May  7 14:26:51 tymorus-desktop kernel: [144033.163369] type=1505 audit(1273256811.035:42): operation="profile_replace" pid=15569 name=/usr/bin/evince
May  7 14:26:51 tymorus-desktop kernel: [144033.167331] type=1505 audit(1273256811.035:43): operation="profile_replace" pid=15569 name=/usr/bin/evince-previewer
May  7 14:26:51 tymorus-desktop kernel: [144033.217776] type=1505 audit(1273256811.085:44): operation="profile_replace" pid=15569 name=/usr/bin/evince-thumbnailer
May  7 14:26:51 tymorus-desktop kernel: [144033.319606] type=1505 audit(1273256811.185:45): operation="profile_replace" pid=15571 name=/usr/bin/freshclam
May  7 14:26:51 tymorus-desktop kernel: [144033.373688] type=1505 audit(1273256811.245:46): operation="profile_replace" pid=15572 name=/usr/sbin/clamd
May  7 14:26:51 tymorus-desktop kernel: [144033.573540] type=1505 audit(1273256811.445:47): operation="profile_replace" pid=15573 name=/usr/lib/cups/backend/cups-pdf
May  7 14:26:51 tymorus-desktop kernel: [144033.573791] type=1505 audit(1273256811.445:48): operation="profile_replace" pid=15573 name=/usr/sbin/cupsd
May  7 14:26:51 tymorus-desktop kernel: [144033.652381] type=1505 audit(1273256811.525:49): operation="profile_replace" pid=15574 name=/usr/sbin/mysqld
May  7 14:26:51 tymorus-desktop kernel: [144033.724103] type=1505 audit(1273256811.595:50): operation="profile_replace" pid=15575 name=/usr/sbin/mysqld-akonadi
May  7 14:26:51 tymorus-desktop kernel: [144033.790856] type=1505 audit(1273256811.665:51): operation="profile_replace" pid=15576 name=/usr/sbin/tcpdump
May  7 14:36:18 tymorus-desktop kernel: [144600.496302] CPU0 attaching NULL sched-domain.
May  7 14:36:18 tymorus-desktop kernel: [144600.496310] CPU1 attaching NULL sched-domain.
May  7 14:36:18 tymorus-desktop kernel: [144600.530111] CPU0 attaching sched-domain:
May  7 14:36:18 tymorus-desktop kernel: [144600.530117]  domain 0: span 0-1 level MC
May  7 14:36:18 tymorus-desktop kernel: [144600.530122]   groups: 0 1
May  7 14:36:18 tymorus-desktop kernel: [144600.530130] CPU1 attaching sched-domain:
May  7 14:36:18 tymorus-desktop kernel: [144600.530134]  domain 0: span 0-1 level MC
May  7 14:36:18 tymorus-desktop kernel: [144600.530138]   groups: 1 0
May  7 14:44:00 tymorus-desktop kernel: [145062.660123] type=1503 audit(1273257840.535:52): operation="open" pid=2492 parent=2491 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
May  7 14:44:01 tymorus-desktop kernel: [145063.317629] type=1503 audit(1273257841.185:53): operation="open" pid=2551 parent=2550 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
May  7 15:15:42 tymorus-desktop kernel: [146964.902563] type=1505 audit(1273259742.775:54): operation="profile_replace" pid=23679 name=/usr/share/gdm/guest-session/Xsession
May  7 15:15:42 tymorus-desktop kernel: [146965.033620] type=1505 audit(1273259742.905:55): operation="profile_replace" pid=23680 name=/sbin/dhclient3
May  7 15:15:42 tymorus-desktop kernel: [146965.033765] type=1505 audit(1273259742.905:56): operation="profile_replace" pid=23680 name=/usr/lib/NetworkManager/nm-dhcp-client.action
May  7 15:15:42 tymorus-desktop kernel: [146965.033823] type=1505 audit(1273259742.905:57): operation="profile_replace" pid=23680 name=/usr/lib/connman/scripts/dhclient-script
May  7 15:15:46 tymorus-desktop kernel: [146968.990896] type=1505 audit(1273259746.865:58): operation="profile_replace" pid=23681 name=/usr/bin/evince
May  7 15:15:46 tymorus-desktop kernel: [146968.992431] type=1505 audit(1273259746.865:59): operation="profile_replace" pid=23681 name=/usr/bin/evince-previewer
May  7 15:15:46 tymorus-desktop kernel: [146968.993464] type=1505 audit(1273259746.865:60): operation="profile_replace" pid=23681 name=/usr/bin/evince-thumbnailer
May  7 15:15:46 tymorus-desktop kernel: [146969.100867] type=1505 audit(1273259746.975:61): operation="profile_replace" pid=23683 name=/usr/bin/freshclam
May  7 15:15:47 tymorus-desktop kernel: [146969.157139] type=1505 audit(1273259747.025:62): operation="profile_replace" pid=23684 name=/usr/sbin/clamd
May  7 15:15:47 tymorus-desktop kernel: [146969.383235] type=1505 audit(1273259747.255:63): operation="profile_replace" pid=23685 name=/usr/lib/cups/backend/cups-pdf
May  7 15:20:42 tymorus-desktop kernel: [147264.362506] __ratelimit: 12 callbacks suppressed
May  7 15:20:42 tymorus-desktop kernel: [147264.362509] type=1505 audit(1273260042.236:68): operation="profile_replace" pid=27944 name=/sbin/dhclient3
May  7 15:20:42 tymorus-desktop kernel: [147264.363115] type=1505 audit(1273260042.236:69): operation="profile_replace" pid=27944 name=/usr/lib/NetworkManager/nm-dhcp-client.action
May  7 15:20:42 tymorus-desktop kernel: [147264.363452] type=1505 audit(1273260042.236:70): operation="profile_replace" pid=27944 name=/usr/lib/connman/scripts/dhclient-script
May  7 15:20:44 tymorus-desktop kernel: Kernel logging (proc) stopped.
May  7 15:20:45 tymorus-desktop kernel: imklog: Cannot read proc file system, 1.
May  7 15:52:11 tymorus-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Command line: root=UUID=25cf6f53-53a4-48bb-ae93-80c3c92b1579 ro quiet splash 
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] KERNEL supported cpus:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   Intel GenuineIntel
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   AMD AuthenticAMD
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   Centaur CentaurHauls
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098400 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 0000000000098400 - 00000000000a0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfedf800 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfedf800 - 00000000bfee0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] DMI present.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] last_pfn = 0xbfedf max_arch_pfn = 0x400000000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] MTRR default type: uncachable
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   00000-9FFFF write-back
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   A0000-EFFFF uncachable
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] MTRR variable ranges enabled:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   3 disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   4 disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   5 disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   6 disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   7 disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] modified physical RAM map:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000098400 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000098400 - 00000000000a0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bfedf800 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfedf800 - 00000000bfee0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfef0000 - 00000000bff00000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] initial memory mapped : 0 - 20000000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bfedf000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  00bfe00000 - 00bfedf000 page 4k
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] kernel direct mapping tables up to bfedf000 @ 10000-15000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] RAMDISK: 377ff000 - 37fef7af
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f83a0 00024 (v02 HPQOEM)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: XSDT 00000000bfee30c0 00054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: FACP 00000000bfee7900 000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: DSDT 00000000bfee3280 0463B (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: FACS 00000000bfee0000 00040
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: SLIC 00000000bfee7b40 00176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: HPET 00000000bfee7d00 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: MCFG 00000000bfee7d80 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: APIC 00000000bfee7a40 00084 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: SSDT 00000000bfee82e0 00304 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] No NUMA configuration found
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Faking a node at 0000000000000000-00000000bfedf000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000000bfedf000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   bootmap [0000000000018000 -  000000000002ffdf] pages 18
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bfedf000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #3 [00377ff000 - 0037fef7af]          RAMDISK ==> [00377ff000 - 0037fef7af]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #4 [0000098400 - 0000100000]    BIOS reserved ==> [0000098400 - 0000100000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a740]              BRK ==> [0001a2a000 - 0001a2a740]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f5f10] f5f10
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880002000000-ffff8800049fffff] on node 0
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Zone PFN ranges:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Movable zone start PFN for each node
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x00000098
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000bfedf
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] On node 0 totalpages: 786023
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA zone: 109 pages reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA zone: 3811 pages, LIFO batch:0
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA32 zone: 10693 pages used for memmap
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA32 zone: 771354 pages, LIFO batch:31
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] nr_irqs_gsi: 24
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000098000 - 0000000000099000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000099000 - 00000000000a0000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:30100000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 775165
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Policy zone: DMA32
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Kernel command line: root=UUID=25cf6f53-53a4-48bb-ae93-80c3c92b1579 ro quiet splash 
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Initializing CPU#0
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Checking aperture...
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] No AGP bridge found
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Memory: 3081844k/3144572k available (5409k kernel code, 480k absent, 62248k reserved, 2976k data, 876k init)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Hierarchical RCU implementation.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] console [tty0] enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] hpet clockevent registered
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Fast TSC calibration using PIT
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Detected 2200.711 MHz processor.
May  7 15:52:12 tymorus-desktop kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4401.42 BogoMIPS (lpj=22007110)
May  7 15:52:12 tymorus-desktop kernel: [    0.010039] Security Framework initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.010059] AppArmor: AppArmor initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.010467] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.012969] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.014097] Mount-cache hash table entries: 256
May  7 15:52:12 tymorus-desktop kernel: [    0.014273] Initializing cgroup subsys ns
May  7 15:52:12 tymorus-desktop kernel: [    0.014279] Initializing cgroup subsys cpuacct
May  7 15:52:12 tymorus-desktop kernel: [    0.014283] Initializing cgroup subsys memory
May  7 15:52:12 tymorus-desktop kernel: [    0.014291] Initializing cgroup subsys devices
May  7 15:52:12 tymorus-desktop kernel: [    0.014294] Initializing cgroup subsys freezer
May  7 15:52:12 tymorus-desktop kernel: [    0.014296] Initializing cgroup subsys net_cls
May  7 15:52:12 tymorus-desktop kernel: [    0.014318] CPU: L1 I cache: 32K, L1 D cache: 32K
May  7 15:52:12 tymorus-desktop kernel: [    0.014321] CPU: L2 cache: 2048K
May  7 15:52:12 tymorus-desktop kernel: [    0.014324] CPU 0/0x0 -> Node 0
May  7 15:52:12 tymorus-desktop kernel: [    0.014326] CPU: Physical Processor ID: 0
May  7 15:52:12 tymorus-desktop kernel: [    0.014328] CPU: Processor Core ID: 0
May  7 15:52:12 tymorus-desktop kernel: [    0.014332] mce: CPU supports 6 MCE banks
May  7 15:52:12 tymorus-desktop kernel: [    0.014340] CPU0: Thermal monitoring enabled (TM2)
May  7 15:52:12 tymorus-desktop kernel: [    0.014346] using mwait in idle threads.
May  7 15:52:12 tymorus-desktop kernel: [    0.014347] Performance Events: Core2 events, Intel PMU driver.
May  7 15:52:12 tymorus-desktop kernel: [    0.014354] ... version:                2
May  7 15:52:12 tymorus-desktop kernel: [    0.014356] ... bit width:              40
May  7 15:52:12 tymorus-desktop kernel: [    0.014357] ... generic registers:      2
May  7 15:52:12 tymorus-desktop kernel: [    0.014359] ... value mask:             000000ffffffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.014361] ... max period:             000000007fffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.014362] ... fixed-purpose events:   3
May  7 15:52:12 tymorus-desktop kernel: [    0.014364] ... event mask:             0000000700000003
May  7 15:52:12 tymorus-desktop kernel: [    0.017555] ACPI: Core revision 20090903
May  7 15:52:12 tymorus-desktop kernel: [    0.030022] ftrace: converting mcount calls to 0f 1f 44 00 00
May  7 15:52:12 tymorus-desktop kernel: [    0.030032] ftrace: allocating 22518 entries in 89 pages
May  7 15:52:12 tymorus-desktop kernel: [    0.040065] Setting APIC routing to flat
May  7 15:52:12 tymorus-desktop kernel: [    0.040378] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  7 15:52:12 tymorus-desktop kernel: [    0.144850] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
May  7 15:52:12 tymorus-desktop kernel: [    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] Initializing CPU#1
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: L2 cache: 2048K
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU 1/0x1 -> Node 0
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: Physical Processor ID: 0
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: Processor Core ID: 1
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
May  7 15:52:12 tymorus-desktop kernel: [    0.300085] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
May  7 15:52:12 tymorus-desktop kernel: [    0.300092] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May  7 15:52:12 tymorus-desktop kernel: [    0.310018] Brought up 2 CPUs
May  7 15:52:12 tymorus-desktop kernel: [    0.310021] Total of 2 processors activated (8802.70 BogoMIPS).
May  7 15:52:12 tymorus-desktop kernel: [    0.310435] CPU0 attaching sched-domain:
May  7 15:52:12 tymorus-desktop kernel: [    0.310438]  domain 0: span 0-1 level MC
May  7 15:52:12 tymorus-desktop kernel: [    0.310441]   groups: 0 1
May  7 15:52:12 tymorus-desktop kernel: [    0.310447] CPU1 attaching sched-domain:
May  7 15:52:12 tymorus-desktop kernel: [    0.310449]  domain 0: span 0-1 level MC
May  7 15:52:12 tymorus-desktop kernel: [    0.310451]   groups: 1 0
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] devtmpfs: initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] regulator: core version 0.5
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] Time: 15:51:29  Date: 05/07/10
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] NET: Registered protocol family 16
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] Trying to unpack rootfs image as initramfs...
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] ACPI: bus type pci registered
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] PCI: MCFG area at f0000000 reserved in E820
May  7 15:52:12 tymorus-desktop kernel: [    0.311321] PCI: Using MMCONFIG at f0000000 - f3ffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.311323] PCI: Using configuration type 1 for base access
May  7 15:52:12 tymorus-desktop kernel: [    0.320152] bio: create slab <bio-0> at 0
May  7 15:52:12 tymorus-desktop kernel: [    0.320846] ACPI: EC: Look up EC in DSDT
May  7 15:52:12 tymorus-desktop kernel: [    0.326678] ACPI: Interpreter enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.326684] ACPI: (supports S0 S1 S3 S4 S5)
May  7 15:52:12 tymorus-desktop kernel: [    0.326713] ACPI: Using IOAPIC for interrupt routing
May  7 15:52:12 tymorus-desktop kernel: [    0.330909] ACPI: No dock devices found.
May  7 15:52:12 tymorus-desktop kernel: [    0.331014] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  7 15:52:12 tymorus-desktop kernel: [    0.331130] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.331133] pci 0000:00:01.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331197] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
May  7 15:52:12 tymorus-desktop kernel: [    0.331239] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.331243] pci 0000:00:1b.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331286] pci 0000:00:1d.0: reg 20 io port: [0xff00-0xff1f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331335] pci 0000:00:1d.1: reg 20 io port: [0xfe00-0xfe1f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331384] pci 0000:00:1d.2: reg 20 io port: [0xfd00-0xfd1f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331432] pci 0000:00:1d.3: reg 20 io port: [0xfc00-0xfc1f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331480] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
May  7 15:52:12 tymorus-desktop kernel: [    0.331526] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.331530] pci 0000:00:1d.7: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331687] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
May  7 15:52:12 tymorus-desktop kernel: [    0.331693] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
May  7 15:52:12 tymorus-desktop kernel: [    0.331699] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
May  7 15:52:12 tymorus-desktop kernel: [    0.331706] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
May  7 15:52:12 tymorus-desktop kernel: [    0.331712] pci 0000:00:1f.1: reg 20 io port: [0xfb00-0xfb0f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331759] pci 0000:00:1f.2: reg 10 io port: [0xfa00-0xfa07]
May  7 15:52:12 tymorus-desktop kernel: [    0.331765] pci 0000:00:1f.2: reg 14 io port: [0xf900-0xf903]
May  7 15:52:12 tymorus-desktop kernel: [    0.331771] pci 0000:00:1f.2: reg 18 io port: [0xf800-0xf807]
May  7 15:52:12 tymorus-desktop kernel: [    0.331777] pci 0000:00:1f.2: reg 1c io port: [0xf700-0xf703]
May  7 15:52:12 tymorus-desktop kernel: [    0.331782] pci 0000:00:1f.2: reg 20 io port: [0xf600-0xf60f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331788] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfdffe000-0xfdffe3ff]
May  7 15:52:12 tymorus-desktop kernel: [    0.331812] pci 0000:00:1f.2: PME# supported from D3hot
May  7 15:52:12 tymorus-desktop kernel: [    0.331816] pci 0000:00:1f.2: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331863] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331917] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.331926] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.331936] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.331941] pci 0000:01:00.0: reg 24 io port: [0xdf00-0xdf7f]
May  7 15:52:12 tymorus-desktop kernel: [    0.331946] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfbfe0000-0xfbffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332011] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332014] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332018] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332054] pci 0000:02:01.0: reg 10 32bit mmio: [0xfdeff000-0xfdefffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332102] pci 0000:02:01.0: supports D1 D2
May  7 15:52:12 tymorus-desktop kernel: [    0.332104] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
May  7 15:52:12 tymorus-desktop kernel: [    0.332108] pci 0000:02:01.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332144] pci 0000:02:04.0: reg 10 32bit mmio: [0xfdee0000-0xfdeeffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332150] pci 0000:02:04.0: reg 14 io port: [0xef00-0xef07]
May  7 15:52:12 tymorus-desktop kernel: [    0.332191] pci 0000:02:04.0: PME# supported from D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.332195] pci 0000:02:04.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332232] pci 0000:02:08.0: reg 10 32bit mmio: [0xfdefe000-0xfdefefff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332239] pci 0000:02:08.0: reg 14 io port: [0xee00-0xee3f]
May  7 15:52:12 tymorus-desktop kernel: [    0.332280] pci 0000:02:08.0: supports D1 D2
May  7 15:52:12 tymorus-desktop kernel: [    0.332282] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.332286] pci 0000:02:08.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332323] pci 0000:00:1e.0: transparent bridge
May  7 15:52:12 tymorus-desktop kernel: [    0.332327] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332331] pci 0000:00:1e.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.332347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  7 15:52:12 tymorus-desktop kernel: [    0.332493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May  7 15:52:12 tymorus-desktop kernel: [    0.343398] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343506] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  7 15:52:12 tymorus-desktop kernel: [    0.343610] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343713] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343816] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343919] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  7 15:52:12 tymorus-desktop kernel: [    0.344024] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  7 15:52:12 tymorus-desktop kernel: [    0.344128] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 9 10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.344261] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
May  7 15:52:12 tymorus-desktop kernel: [    0.344265] vgaarb: loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.344381] SCSI subsystem initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.344495] libata version 3.00 loaded.
May  7 15:52:12 tymorus-desktop kernel: [    0.344564] usbcore: registered new interface driver usbfs
May  7 15:52:12 tymorus-desktop kernel: [    0.344576] usbcore: registered new interface driver hub
May  7 15:52:12 tymorus-desktop kernel: [    0.344607] usbcore: registered new device driver usb
May  7 15:52:12 tymorus-desktop kernel: [    0.344735] ACPI: WMI: Mapper loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.344736] PCI: Using ACPI for IRQ routing
May  7 15:52:12 tymorus-desktop kernel: [    0.344894] NetLabel: Initializing
May  7 15:52:12 tymorus-desktop kernel: [    0.344896] NetLabel:  domain hash size = 128
May  7 15:52:12 tymorus-desktop kernel: [    0.344897] NetLabel:  protocols = UNLABELED CIPSOv4
May  7 15:52:12 tymorus-desktop kernel: [    0.344910] NetLabel:  unlabeled traffic allowed by default
May  7 15:52:12 tymorus-desktop kernel: [    0.344944] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
May  7 15:52:12 tymorus-desktop kernel: [    0.344948] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
May  7 15:52:12 tymorus-desktop kernel: [    0.350032] Switching to clocksource tsc
May  7 15:52:12 tymorus-desktop kernel: [    0.351887] AppArmor: AppArmor Filesystem Enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.351911] pnp: PnP ACPI init
May  7 15:52:12 tymorus-desktop kernel: [    0.351929] ACPI: bus type pnp registered
May  7 15:52:12 tymorus-desktop kernel: [    0.353488] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 688 (bits) (20090903/dsopcode-596)
May  7 15:52:12 tymorus-desktop kernel: [    0.353495] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.MEM_._CRS] (Node ffff8800bc641fc0), AE_AML_BUFFER_LIMIT
May  7 15:52:12 tymorus-desktop kernel: [    0.353519] ACPI Error (uteval-0250): Method execution failed [\_SB_.MEM_._CRS] (Node ffff8800bc641fc0), AE_AML_BUFFER_LIMIT
May  7 15:52:12 tymorus-desktop kernel: [    0.353526] pnp 00:0b: can't evaluate _CRS: 12298
May  7 15:52:12 tymorus-desktop kernel: [    0.353582] pnp: PnP ACPI: found 12 devices
May  7 15:52:12 tymorus-desktop kernel: [    0.353584] ACPI: ACPI bus type pnp unregistered
May  7 15:52:12 tymorus-desktop kernel: [    0.353598] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353601] system 00:01: ioport range 0x800-0x87f has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353604] system 00:01: ioport range 0x294-0x297 has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353606] system 00:01: ioport range 0x880-0x88f has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353613] system 00:08: ioport range 0x400-0x4bf has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353620] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.358351] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
May  7 15:52:12 tymorus-desktop kernel: [    0.358354] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
May  7 15:52:12 tymorus-desktop kernel: [    0.358358] pci 0000:00:01.0:   MEM window: 0xf8000000-0xfbffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.358362] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.358367] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
May  7 15:52:12 tymorus-desktop kernel: [    0.358370] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
May  7 15:52:12 tymorus-desktop kernel: [    0.358374] pci 0000:00:1e.0:   MEM window: 0xfde00000-0xfdefffff
May  7 15:52:12 tymorus-desktop kernel: [    0.358378] pci 0000:00:1e.0:   PREFETCH window: disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.358392]   alloc irq_desc for 16 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.358394]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.358400] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [    0.358405] pci 0000:00:01.0: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.358412] pci 0000:00:1e.0: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.358418] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358420] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358423] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358425] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358427] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358430] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358432] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358434] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358436] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
May  7 15:52:12 tymorus-desktop kernel: [    0.358486] NET: Registered protocol family 2
May  7 15:52:12 tymorus-desktop kernel: [    0.358664] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.360006] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.365392] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.366007] TCP: Hash tables configured (established 524288 bind 65536)
May  7 15:52:12 tymorus-desktop kernel: [    0.366010] TCP reno registered
May  7 15:52:12 tymorus-desktop kernel: [    0.366155] NET: Registered protocol family 1
May  7 15:52:12 tymorus-desktop kernel: [    0.366276] pci 0000:01:00.0: Boot video device
May  7 15:52:12 tymorus-desktop kernel: [    0.366290] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
May  7 15:52:12 tymorus-desktop kernel: [    0.366570] Scanning for low memory corruption every 60 seconds
May  7 15:52:12 tymorus-desktop kernel: [    0.366717] audit: initializing netlink socket (disabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.366728] type=2000 audit(1273247488.359:1): initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.375840] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  7 15:52:12 tymorus-desktop kernel: [    0.377171] VFS: Disk quotas dquot_6.5.2
May  7 15:52:12 tymorus-desktop kernel: [    0.377223] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.377810] fuse init (API version 7.13)
May  7 15:52:12 tymorus-desktop kernel: [    0.377894] msgmni has been set to 6019
May  7 15:52:12 tymorus-desktop kernel: [    0.378108] alg: No test for stdrng (krng)
May  7 15:52:12 tymorus-desktop kernel: [    0.378160] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May  7 15:52:12 tymorus-desktop kernel: [    0.378163] io scheduler noop registered
May  7 15:52:12 tymorus-desktop kernel: [    0.378165] io scheduler anticipatory registered
May  7 15:52:12 tymorus-desktop kernel: [    0.378167] io scheduler deadline registered
May  7 15:52:12 tymorus-desktop kernel: [    0.378198] io scheduler cfq registered (default)
May  7 15:52:12 tymorus-desktop kernel: [    0.378331]   alloc irq_desc for 24 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.378333]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.378342] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
May  7 15:52:12 tymorus-desktop kernel: [    0.378348] pcieport 0000:00:01.0: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.378414] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  7 15:52:12 tymorus-desktop kernel: [    0.378436] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  7 15:52:12 tymorus-desktop kernel: [    0.378533] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
May  7 15:52:12 tymorus-desktop kernel: [    0.378536] ACPI: Power Button [PWRB]
May  7 15:52:12 tymorus-desktop kernel: [    0.378595] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  7 15:52:12 tymorus-desktop kernel: [    0.378598] ACPI: Power Button [PWRF]
May  7 15:52:12 tymorus-desktop kernel: [    0.378644] fan PNP0C0B:00: registered as cooling_device0
May  7 15:52:12 tymorus-desktop kernel: [    0.378649] ACPI: Fan [FAN] (on)
May  7 15:52:12 tymorus-desktop kernel: [    0.379108] ACPI: SSDT 00000000bfee7e00 001B7 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.379304] processor LNXCPU:00: registered as cooling_device1
May  7 15:52:12 tymorus-desktop kernel: [    0.379472] ACPI: SSDT 00000000bfee8210 000CE (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.379674] processor LNXCPU:01: registered as cooling_device2
May  7 15:52:12 tymorus-desktop kernel: [    0.381686] thermal LNXTHERM:01: registered as thermal_zone0
May  7 15:52:12 tymorus-desktop kernel: [    0.381693] ACPI: Thermal Zone [THRM] (35 C)
May  7 15:52:12 tymorus-desktop kernel: [    0.383051] Linux agpgart interface v0.103
May  7 15:52:12 tymorus-desktop kernel: [    0.383089] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.384314] brd: module loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.384768] loop: module loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.384853] input: Macintosh mouse button emulation as /devices/virtual/input/input2
May  7 15:52:12 tymorus-desktop kernel: [    0.384953] ata_piix 0000:00:1f.1: version 2.13
May  7 15:52:12 tymorus-desktop kernel: [    0.384973]   alloc irq_desc for 18 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.384975]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.384983] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May  7 15:52:12 tymorus-desktop kernel: [    0.385021] ata_piix 0000:00:1f.1: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.385132] scsi0 : ata_piix
May  7 15:52:12 tymorus-desktop kernel: [    0.385203] scsi1 : ata_piix
May  7 15:52:12 tymorus-desktop kernel: [    0.385612] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
May  7 15:52:12 tymorus-desktop kernel: [    0.385615] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
May  7 15:52:12 tymorus-desktop kernel: [    0.385926] Fixed MDIO Bus: probed
May  7 15:52:12 tymorus-desktop kernel: [    0.385959] PPP generic driver version 2.4.2
May  7 15:52:12 tymorus-desktop kernel: [    0.385997] tun: Universal TUN/TAP device driver, 1.6
May  7 15:52:12 tymorus-desktop kernel: [    0.385998] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  7 15:52:12 tymorus-desktop kernel: [    0.386087] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  7 15:52:12 tymorus-desktop kernel: [    0.386109]   alloc irq_desc for 23 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.386111]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.386116] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  7 15:52:12 tymorus-desktop kernel: [    0.386131] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.386135] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.386166] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
May  7 15:52:12 tymorus-desktop kernel: [    0.386187] ehci_hcd 0000:00:1d.7: using broken periodic workaround
May  7 15:52:12 tymorus-desktop kernel: [    0.390082] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
May  7 15:52:12 tymorus-desktop kernel: [    0.390127] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
May  7 15:52:12 tymorus-desktop kernel: [    0.394202] ata2: port disabled. ignoring.
May  7 15:52:12 tymorus-desktop kernel: [    0.409577] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
May  7 15:52:12 tymorus-desktop kernel: [    0.409735] usb usb1: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.409764] hub 1-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.409772] hub 1-0:1.0: 8 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.409843] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  7 15:52:12 tymorus-desktop kernel: [    0.409859] uhci_hcd: USB Universal Host Controller Interface driver
May  7 15:52:12 tymorus-desktop kernel: [    0.409917] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  7 15:52:12 tymorus-desktop kernel: [    0.409927] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.409930] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.409966] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May  7 15:52:12 tymorus-desktop kernel: [    0.409993] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
May  7 15:52:12 tymorus-desktop kernel: [    0.410075] usb usb2: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410099] hub 2-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410106] hub 2-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410150]   alloc irq_desc for 19 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.410152]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.410159] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  7 15:52:12 tymorus-desktop kernel: [    0.410165] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.410168] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.410199] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
May  7 15:52:12 tymorus-desktop kernel: [    0.410230] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
May  7 15:52:12 tymorus-desktop kernel: [    0.410314] usb usb3: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410337] hub 3-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410343] hub 3-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410382] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May  7 15:52:12 tymorus-desktop kernel: [    0.410387] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.410390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.410423] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
May  7 15:52:12 tymorus-desktop kernel: [    0.410451] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
May  7 15:52:12 tymorus-desktop kernel: [    0.410529] usb usb4: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410558] hub 4-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410564] hub 4-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410605] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [    0.410611] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.410614] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.410641] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
May  7 15:52:12 tymorus-desktop kernel: [    0.410669] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
May  7 15:52:12 tymorus-desktop kernel: [    0.410748] usb usb5: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410771] hub 5-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410779] hub 5-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410865] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  7 15:52:12 tymorus-desktop kernel: [    0.410867] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  7 15:52:12 tymorus-desktop kernel: [    0.411511] serio: i8042 KBD port at 0x60,0x64 irq 1
May  7 15:52:12 tymorus-desktop kernel: [    0.411629] mice: PS/2 mouse device common for all mice
May  7 15:52:12 tymorus-desktop kernel: [    0.411738] rtc_cmos 00:04: RTC can wake from S4
May  7 15:52:12 tymorus-desktop kernel: [    0.411777] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  7 15:52:12 tymorus-desktop kernel: [    0.411804] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
May  7 15:52:12 tymorus-desktop kernel: [    0.411928] device-mapper: uevent: version 1.0.3
May  7 15:52:12 tymorus-desktop kernel: [    0.412048] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
May  7 15:52:12 tymorus-desktop kernel: [    0.412109] device-mapper: multipath: version 1.1.0 loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.412112] device-mapper: multipath round-robin: version 1.0.0 loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.412263] cpuidle: using governor ladder
May  7 15:52:12 tymorus-desktop kernel: [    0.412265] cpuidle: using governor menu
May  7 15:52:12 tymorus-desktop kernel: [    0.412595] TCP cubic registered
May  7 15:52:12 tymorus-desktop kernel: [    0.412711] NET: Registered protocol family 10
May  7 15:52:12 tymorus-desktop kernel: [    0.413148] lo: Disabled Privacy Extensions
May  7 15:52:12 tymorus-desktop kernel: [    0.413408] NET: Registered protocol family 17
May  7 15:52:12 tymorus-desktop kernel: [    0.414645] PM: Resume from disk failed.
May  7 15:52:12 tymorus-desktop kernel: [    0.414658] registered taskstats version 1
May  7 15:52:12 tymorus-desktop kernel: [    0.414939]   Magic number: 10:448:891
May  7 15:52:12 tymorus-desktop kernel: [    0.415018] rtc_cmos 00:04: setting system clock to 2010-05-07 15:51:29 UTC (1273247489)
May  7 15:52:12 tymorus-desktop kernel: [    0.415021] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  7 15:52:12 tymorus-desktop kernel: [    0.415023] EDD information not available.
May  7 15:52:12 tymorus-desktop kernel: [    0.439590] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
May  7 15:52:12 tymorus-desktop kernel: [    0.490414] Freeing initrd memory: 8129k freed
May  7 15:52:12 tymorus-desktop kernel: [    0.606242] ata1.01: ATA-7: MAXTOR STM3320620A, 3.AAE, max UDMA/100
May  7 15:52:12 tymorus-desktop kernel: [    0.606248] ata1.01: 625142448 sectors, multi 16: LBA48 
May  7 15:52:12 tymorus-desktop kernel: [    0.606274] ata1.01: limited to UDMA/33 due to 40-wire cable
May  7 15:52:12 tymorus-desktop kernel: [    0.689308] ata1.01: configured for UDMA/33
May  7 15:52:12 tymorus-desktop kernel: [    0.689478] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May  7 15:52:12 tymorus-desktop kernel: [    0.689630] sd 0:0:1:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
May  7 15:52:12 tymorus-desktop kernel: [    0.689666] sd 0:0:1:0: Attached scsi generic sg0 type 0
May  7 15:52:12 tymorus-desktop kernel: [    0.689677] sd 0:0:1:0: [sda] Write Protect is off
May  7 15:52:12 tymorus-desktop kernel: [    0.689680] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
May  7 15:52:12 tymorus-desktop kernel: [    0.689703] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  7 15:52:12 tymorus-desktop kernel: [    0.689853]  sda: sda1 sda2 < sda5 sda6
May  7 15:52:12 tymorus-desktop kernel: [    0.789927] usb 1-6: new high speed USB device using ehci_hcd and address 3
May  7 15:52:12 tymorus-desktop kernel: [    0.793638]  sda7 >
May  7 15:52:12 tymorus-desktop kernel: [    0.794004] sd 0:0:1:0: [sda] Attached SCSI disk
May  7 15:52:12 tymorus-desktop kernel: [    0.794026] Freeing unused kernel memory: 876k freed
May  7 15:52:12 tymorus-desktop kernel: [    0.794402] Write protecting the kernel read-only data: 7680k
May  7 15:52:12 tymorus-desktop kernel: [    0.808626] udev: starting version 151
May  7 15:52:12 tymorus-desktop kernel: [    0.900233] ahci 0000:00:1f.2: version 3.0
May  7 15:52:12 tymorus-desktop kernel: [    0.900257] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  7 15:52:12 tymorus-desktop kernel: [    0.900299]   alloc irq_desc for 25 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.900301]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.900311] ahci 0000:00:1f.2: irq 25 for MSI/MSI-X
May  7 15:52:12 tymorus-desktop kernel: [    0.900374] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
May  7 15:52:12 tymorus-desktop kernel: [    0.900378] ahci 0000:00:1f.2: flags: 64bit ncq led clo 
May  7 15:52:12 tymorus-desktop kernel: [    0.900382] ahci 0000:00:1f.2: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [    0.908621] scsi2 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908717] scsi3 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908773] scsi4 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908827] scsi5 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908960] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.908963] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.908966] ata5: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.908969] ata6: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.909669] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
May  7 15:52:12 tymorus-desktop kernel: [    0.909671] e100: Copyright(c) 1999-2006 Intel Corporation
May  7 15:52:12 tymorus-desktop kernel: [    0.909707]   alloc irq_desc for 20 on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.909709]   alloc kstat_irqs on node -1
May  7 15:52:12 tymorus-desktop kernel: [    0.909717] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  7 15:52:12 tymorus-desktop kernel: [    0.933198] e100 0000:02:08.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.933721] e100: eth0: e100_probe: addr 0xfdefe000, irq 20, MAC addr 00:1e:8c:2a:16:1e
May  7 15:52:12 tymorus-desktop kernel: [    0.941794] usb 1-6: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.948169] Initializing USB Mass Storage driver...
May  7 15:52:12 tymorus-desktop kernel: [    0.948283] scsi6 : SCSI emulation for USB Mass Storage devices
May  7 15:52:12 tymorus-desktop kernel: [    0.948363] usbcore: registered new interface driver usb-storage
May  7 15:52:12 tymorus-desktop kernel: [    0.948366] USB Mass Storage support registered.
May  7 15:52:12 tymorus-desktop kernel: [    0.948371] usb-storage: device found at 3
May  7 15:52:12 tymorus-desktop kernel: [    0.948373] usb-storage: waiting for device to settle before scanning
May  7 15:52:12 tymorus-desktop kernel: [    1.060066] usb 1-7: new high speed USB device using ehci_hcd and address 4
May  7 15:52:12 tymorus-desktop kernel: [    1.212177] usb 1-7: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    1.212522] scsi7 : SCSI emulation for USB Mass Storage devices
May  7 15:52:12 tymorus-desktop kernel: [    1.212654] usb-storage: device found at 4
May  7 15:52:12 tymorus-desktop kernel: [    1.212656] usb-storage: waiting for device to settle before scanning
May  7 15:52:12 tymorus-desktop kernel: [    1.245596] EXT3-fs: INFO: recovery required on readonly filesystem.
May  7 15:52:12 tymorus-desktop kernel: [    1.245600] EXT3-fs: write access will be enabled during recovery.
May  7 15:52:12 tymorus-desktop kernel: [    1.250098] ata6: SATA link down (SStatus 0 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250129] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250151] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250169] ata5: SATA link down (SStatus 0 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250920] ata3.00: ATA-7: ST3500630AS, 3.CHL, max UDMA/100
May  7 15:52:12 tymorus-desktop kernel: [    1.250922] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
May  7 15:52:12 tymorus-desktop kernel: [    1.251063] ata4.00: ATAPI: TSSTcorp CDDVDW TS-H653N, 0609, max UDMA/33, ATAPI AN
May  7 15:52:12 tymorus-desktop kernel: [    1.251922] ata3.00: configured for UDMA/100
May  7 15:52:12 tymorus-desktop kernel: [    1.252062] scsi 2:0:0:0: Direct-Access     ATA      ST3500630AS      3.CH PQ: 0 ANSI: 5
May  7 15:52:12 tymorus-desktop kernel: [    1.252231] sd 2:0:0:0: Attached scsi generic sg1 type 0
May  7 15:52:12 tymorus-desktop kernel: [    1.252264] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  7 15:52:12 tymorus-desktop kernel: [    1.252317] sd 2:0:0:0: [sdb] Write Protect is off
May  7 15:52:12 tymorus-desktop kernel: [    1.252320] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  7 15:52:12 tymorus-desktop kernel: [    1.252342] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  7 15:52:12 tymorus-desktop kernel: [    1.252465]  sdb:
May  7 15:52:12 tymorus-desktop kernel: [    1.252500] ata4.00: configured for UDMA/33
May  7 15:52:12 tymorus-desktop kernel: [    1.253527] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653N  0609 PQ: 0 ANSI: 5
May  7 15:52:12 tymorus-desktop kernel: [    1.257301] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
May  7 15:52:12 tymorus-desktop kernel: [    1.257306] Uniform CD-ROM driver Revision: 3.20
May  7 15:52:12 tymorus-desktop kernel: [    1.257450] sr 3:0:0:0: Attached scsi CD-ROM sr0
May  7 15:52:12 tymorus-desktop kernel: [    1.257497] sr 3:0:0:0: Attached scsi generic sg2 type 5
May  7 15:52:12 tymorus-desktop kernel: [    1.278314]  sdb1 sdb2
May  7 15:52:12 tymorus-desktop kernel: [    1.278580] sd 2:0:0:0: [sdb] Attached SCSI disk
May  7 15:52:12 tymorus-desktop kernel: [    1.282218] ohci1394 0000:02:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  7 15:52:12 tymorus-desktop kernel: [    1.342109] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
May  7 15:52:12 tymorus-desktop kernel: [    1.490039] usb 3-1: new low speed USB device using uhci_hcd and address 2
May  7 15:52:12 tymorus-desktop kernel: [    1.675386] usb 3-1: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    1.686761] usbcore: registered new interface driver hiddev
May  7 15:52:12 tymorus-desktop kernel: [    1.728070] input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
May  7 15:52:12 tymorus-desktop kernel: [    1.728164] generic-usb 0003:045E:00B9.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:1d.1-1/input0
May  7 15:52:12 tymorus-desktop kernel: [    1.728186] usbcore: registered new interface driver usbhid
May  7 15:52:12 tymorus-desktop kernel: [    1.728189] usbhid: v2.6:USB HID core driver
May  7 15:52:12 tymorus-desktop kernel: [    2.660208] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c000002e99a]
May  7 15:52:12 tymorus-desktop kernel: [    5.941568] usb-storage: device scan complete
May  7 15:52:12 tymorus-desktop kernel: [    5.942048] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent Go     102F PQ: 0 ANSI: 4
May  7 15:52:12 tymorus-desktop kernel: [    5.942527] sd 6:0:0:0: Attached scsi generic sg3 type 0
May  7 15:52:12 tymorus-desktop kernel: [    5.943279] sd 6:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  7 15:52:12 tymorus-desktop kernel: [    5.943652] sd 6:0:0:0: [sdc] Write Protect is off
May  7 15:52:12 tymorus-desktop kernel: [    5.943657] sd 6:0:0:0: [sdc] Mode Sense: 1c 00 00 00
May  7 15:52:12 tymorus-desktop kernel: [    5.943661] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May  7 15:52:12 tymorus-desktop kernel: [    5.944648] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May  7 15:52:12 tymorus-desktop kernel: [    5.944654]  sdc: sdc1
May  7 15:52:12 tymorus-desktop kernel: [    5.971768] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May  7 15:52:12 tymorus-desktop kernel: [    5.971772] sd 6:0:0:0: [sdc] Attached SCSI disk
May  7 15:52:12 tymorus-desktop kernel: [    6.210573] usb-storage: device scan complete
May  7 15:52:12 tymorus-desktop kernel: [    6.211307] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.211919] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.212413] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213043] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213501] sd 7:0:0:0: Attached scsi generic sg4 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213698] sd 7:0:0:1: Attached scsi generic sg5 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213836] sd 7:0:0:2: Attached scsi generic sg6 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213959] sd 7:0:0:3: Attached scsi generic sg7 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.215749] sd 7:0:0:0: [sdd] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [    6.219909] sd 7:0:0:1: [sde] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [    6.220528] sd 7:0:0:2: [sdf] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [    6.221273] sd 7:0:0:3: [sdg] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [   13.723570] kjournald starting.  Commit interval 5 seconds
May  7 15:52:12 tymorus-desktop kernel: [   13.723588] EXT3-fs: sda6: orphan cleanup on readonly fs
May  7 15:52:12 tymorus-desktop kernel: [   13.723598] ext3_orphan_cleanup: deleting unreferenced inode 548870
May  7 15:52:12 tymorus-desktop kernel: [   13.723642] ext3_orphan_cleanup: deleting unreferenced inode 548869
May  7 15:52:12 tymorus-desktop kernel: [   13.723654] ext3_orphan_cleanup: deleting unreferenced inode 548868
May  7 15:52:12 tymorus-desktop kernel: [   13.723666] ext3_orphan_cleanup: deleting unreferenced inode 548867
May  7 15:52:12 tymorus-desktop kernel: [   13.723671] ext3_orphan_cleanup: deleting unreferenced inode 548866
May  7 15:52:12 tymorus-desktop kernel: [   13.723679] ext3_orphan_cleanup: deleting unreferenced inode 2392738
May  7 15:52:12 tymorus-desktop kernel: [   13.723699] ext3_orphan_cleanup: deleting unreferenced inode 1032197
May  7 15:52:12 tymorus-desktop kernel: [   13.740569] ext3_orphan_cleanup: deleting unreferenced inode 925702
May  7 15:52:12 tymorus-desktop kernel: [   13.749133] ext3_orphan_cleanup: deleting unreferenced inode 3416102
May  7 15:52:12 tymorus-desktop kernel: [   13.763910] ext3_orphan_cleanup: deleting unreferenced inode 3416113
May  7 15:52:12 tymorus-desktop kernel: [   13.767094] ext3_orphan_cleanup: deleting unreferenced inode 3416154
May  7 15:52:12 tymorus-desktop kernel: [   13.773329] ext3_orphan_cleanup: deleting unreferenced inode 3416155
May  7 15:52:12 tymorus-desktop kernel: [   13.773348] ext3_orphan_cleanup: deleting unreferenced inode 3416175
May  7 15:52:12 tymorus-desktop kernel: [   13.776627] ext3_orphan_cleanup: deleting unreferenced inode 3416189
May  7 15:52:12 tymorus-desktop kernel: [   13.776647] ext3_orphan_cleanup: deleting unreferenced inode 3416221
May  7 15:52:12 tymorus-desktop kernel: [   13.781712] ext3_orphan_cleanup: deleting unreferenced inode 3416328
May  7 15:52:12 tymorus-desktop kernel: [   13.781734] ext3_orphan_cleanup: deleting unreferenced inode 713194
May  7 15:52:12 tymorus-desktop kernel: [   13.794400] EXT3-fs: sda6: 17 orphan inodes deleted
May  7 15:52:12 tymorus-desktop kernel: [   13.794404] EXT3-fs: recovery complete.
May  7 15:52:12 tymorus-desktop kernel: [   13.901769] EXT3-fs: mounted filesystem with ordered data mode.
May  7 15:52:12 tymorus-desktop kernel: [   16.097279] Adding 281096k swap on /dev/sda7.  Priority:-1 extents:1 across:281096k 
May  7 15:52:12 tymorus-desktop kernel: [   16.506019] udev: starting version 151
May  7 15:52:12 tymorus-desktop kernel: [   17.888234] type=1505 audit(1273261906.966:2):  operation="profile_load" pid=552 name="/sbin/dhclient3"
May  7 15:52:12 tymorus-desktop kernel: [   17.888903] type=1505 audit(1273261906.966:3):  operation="profile_load" pid=552 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  7 15:52:12 tymorus-desktop kernel: [   17.889245] type=1505 audit(1273261906.966:4):  operation="profile_load" pid=552 name="/usr/lib/connman/scripts/dhclient-script"
May  7 15:52:12 tymorus-desktop kernel: [   18.402072] vga16fb: initializing
May  7 15:52:12 tymorus-desktop kernel: [   18.402076] vga16fb: mapped to 0xffff8800000a0000
May  7 15:52:12 tymorus-desktop kernel: [   18.402186] fb0: VGA16 VGA frame buffer device
May  7 15:52:12 tymorus-desktop kernel: [   19.585105] nvidia: module license 'NVIDIA' taints kernel.
May  7 15:52:12 tymorus-desktop kernel: [   19.585109] Disabling lock debugging due to kernel taint
May  7 15:52:12 tymorus-desktop kernel: [   20.073675] EXT3 FS on sda6, internal journal
May  7 15:52:12 tymorus-desktop kernel: [   20.204103] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [   20.204115] nvidia 0000:01:00.0: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [   20.204120] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
May  7 15:52:12 tymorus-desktop kernel: [   20.204724] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
May  7 15:52:12 tymorus-desktop kernel: [   20.221932] lp: driver loaded but no devices found
May  7 15:52:12 tymorus-desktop kernel: [   20.264947] Console: switching to colour frame buffer device 80x30
May  7 15:52:12 tymorus-desktop kernel: [   20.598755] ip_tables: (C) 2000-2006 Netfilter Core Team
May  7 15:52:12 tymorus-desktop kernel: [   20.947725] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
May  7 15:52:12 tymorus-desktop kernel: [   20.948256] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
May  7 15:52:12 tymorus-desktop kernel: [   20.948259] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
May  7 15:52:12 tymorus-desktop kernel: [   20.948260] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
May  7 15:52:12 tymorus-desktop kernel: [   22.247651] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  7 15:52:12 tymorus-desktop kernel: [   22.324676] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [   22.324717] HDA Intel 0000:00:1b.0: setting latency timer to 64
May  7 15:52:12 tymorus-desktop kernel: [   22.564730] hda_codec: ALC1200: BIOS auto-probing.
May  7 15:52:12 tymorus-desktop kernel: [   22.566481] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
May  7 15:52:12 tymorus-desktop kernel: [   40.021914] kjournald starting.  Commit interval 5 seconds
May  7 15:52:12 tymorus-desktop kernel: [   40.022168] EXT3 FS on sda1, internal journal
May  7 15:52:12 tymorus-desktop kernel: [   40.022176] EXT3-fs: mounted filesystem with ordered data mode.
May  7 15:52:14 tymorus-desktop kernel: [   45.334276] type=1505 audit(1273261934.415:5):  operation="profile_load" pid=1144 name="/usr/share/gdm/guest-session/Xsession"
May  7 15:52:14 tymorus-desktop kernel: [   45.335932] type=1505 audit(1273261934.415:6):  operation="profile_replace" pid=1145 name="/sbin/dhclient3"
May  7 15:52:14 tymorus-desktop kernel: [   45.336558] type=1505 audit(1273261934.415:7):  operation="profile_replace" pid=1145 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  7 15:52:14 tymorus-desktop kernel: [   45.336904] type=1505 audit(1273261934.415:8):  operation="profile_replace" pid=1145 name="/usr/lib/connman/scripts/dhclient-script"
May  7 15:52:14 tymorus-desktop kernel: [   45.388635] type=1505 audit(1273261934.465:9):  operation="profile_load" pid=1146 name="/usr/bin/evince"
May  7 15:52:14 tymorus-desktop kernel: [   45.396630] type=1505 audit(1273261934.475:10):  operation="profile_load" pid=1146 name="/usr/bin/evince-previewer"
May  7 15:52:14 tymorus-desktop kernel: [   45.401861] type=1505 audit(1273261934.484:11):  operation="profile_load" pid=1146 name="/usr/bin/evince-thumbnailer"
May  7 15:52:14 tymorus-desktop kernel: [   45.748736] type=1505 audit(1273261934.824:12):  operation="profile_load" pid=1148 name="/usr/bin/freshclam"
May  7 15:52:14 tymorus-desktop kernel: [   45.811338] type=1505 audit(1273261934.895:13):  operation="profile_load" pid=1149 name="/usr/sbin/clamd"
May  7 15:52:14 tymorus-desktop kernel: [   45.849188] type=1505 audit(1273261934.924:14):  operation="profile_load" pid=1152 name="/usr/lib/cups/backend/cups-pdf"
May  7 15:52:16 tymorus-desktop kernel: [   47.181373] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  7 15:52:16 tymorus-desktop kernel: [   47.190152] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
May  7 15:52:16 tymorus-desktop kernel: [   47.220910] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  7 15:52:19 tymorus-desktop kernel: [   50.030057] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  7 15:52:19 tymorus-desktop kernel: [   50.030075] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  7 15:52:19 tymorus-desktop kernel: [   50.283606] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.283618] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.283636] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.344970] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130 
May  7 15:52:19 tymorus-desktop kernel: [   50.344990] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130 
May  7 15:52:19 tymorus-desktop kernel: [   50.345028] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130 
May  7 15:52:19 tymorus-desktop kernel: [   50.534065] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.534078] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.534104] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.784889] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.784902] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:19 tymorus-desktop kernel: [   50.784927] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342 
May  7 15:52:20 tymorus-desktop kernel: [   50.928616] ppdev: user-space parallel port driver
May  7 15:52:20 tymorus-desktop kernel: [   50.985738] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:20 tymorus-desktop kernel: [   50.985750] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:20 tymorus-desktop kernel: [   50.985774] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:20 tymorus-desktop kernel: [   51.571521] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223 
May  7 15:52:20 tymorus-desktop kernel: [   51.571534] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223 
May  7 15:52:20 tymorus-desktop kernel: [   51.571551] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223 
May  7 15:52:21 tymorus-desktop kernel: [   51.990077] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  7 15:52:21 tymorus-desktop kernel: [   51.990095] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  7 15:52:21 tymorus-desktop kernel: [   52.212664] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:21 tymorus-desktop kernel: [   52.212676] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:21 tymorus-desktop kernel: [   52.212701] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:21 tymorus-desktop kernel: [   52.490180] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30343 PROTO=UDP SPT=50583 DPT=53 LEN=31 
May  7 15:52:21 tymorus-desktop kernel: [   52.490192] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30343 PROTO=UDP SPT=50583 DPT=53 LEN=31 
May  7 15:52:21 tymorus-desktop kernel: [   52.618654] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=126 TOS=0x00 PREC=0x00 TTL=255 ID=52006 DF PROTO=UDP SPT=53 DPT=50583 LEN=106 
May  7 15:52:21 tymorus-desktop kernel: [   52.618891] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30344 PROTO=UDP SPT=56434 DPT=53 LEN=31 
May  7 15:52:21 tymorus-desktop kernel: [   52.618901] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30344 PROTO=UDP SPT=56434 DPT=53 LEN=31 
May  7 15:52:21 tymorus-desktop kernel: [   52.738936] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=126 TOS=0x00 PREC=0x00 TTL=255 ID=52007 DF PROTO=UDP SPT=53 DPT=56434 LEN=106 
May  7 15:52:22 tymorus-desktop kernel: [   53.747887] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40910 DF PROTO=UDP SPT=37685 DPT=53 LEN=40 
May  7 15:52:22 tymorus-desktop kernel: [   53.747900] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40910 DF PROTO=UDP SPT=37685 DPT=53 LEN=40 
May  7 15:52:22 tymorus-desktop kernel: [   53.799758] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223 
May  7 15:52:22 tymorus-desktop kernel: [   53.799778] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223 
May  7 15:52:22 tymorus-desktop kernel: [   53.799802] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223 
May  7 15:52:22 tymorus-desktop kernel: [   53.824897] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=121 TOS=0x00 PREC=0x00 TTL=255 ID=52008 DF PROTO=UDP SPT=53 DPT=37685 LEN=101 
May  7 15:52:22 tymorus-desktop kernel: [   53.825044] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40918 DF PROTO=UDP SPT=57530 DPT=53 LEN=58 
May  7 15:52:22 tymorus-desktop kernel: [   53.825055] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40918 DF PROTO=UDP SPT=57530 DPT=53 LEN=58 
May  7 15:52:22 tymorus-desktop kernel: [   53.852676] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=540 TOS=0x00 PREC=0x00 TTL=255 ID=52009 DF PROTO=UDP SPT=53 DPT=57530 LEN=520 
May  7 15:52:22 tymorus-desktop kernel: [   53.852753] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40921 DF PROTO=UDP SPT=55209 DPT=53 LEN=58 
May  7 15:52:22 tymorus-desktop kernel: [   53.852769] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40921 DF PROTO=UDP SPT=55209 DPT=53 LEN=58 
May  7 15:52:22 tymorus-desktop kernel: [   53.879471] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=540 TOS=0x00 PREC=0x00 TTL=255 ID=52010 DF PROTO=UDP SPT=53 DPT=55209 LEN=520 
May  7 15:52:22 tymorus-desktop kernel: [   53.879558] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40923 DF PROTO=UDP SPT=41826 DPT=53 LEN=40 
May  7 15:52:22 tymorus-desktop kernel: [   53.879574] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40923 DF PROTO=UDP SPT=41826 DPT=53 LEN=40 
May  7 15:52:23 tymorus-desktop kernel: [   53.960786] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=255 ID=52011 DF PROTO=UDP SPT=53 DPT=41826 LEN=56 
May  7 15:52:23 tymorus-desktop kernel: [   54.061176] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:23 tymorus-desktop kernel: [   54.061195] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:23 tymorus-desktop kernel: [   54.210678] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:23 tymorus-desktop kernel: [   54.210768] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:23 tymorus-desktop kernel: [   54.360365] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:23 tymorus-desktop kernel: [   54.361278] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:11 tymorus-desktop kernel: [   54.439641] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:11 tymorus-desktop kernel: [   54.439653] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:11 tymorus-desktop kernel: [   54.439681] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318 
May  7 15:52:11 tymorus-desktop kernel: [   54.512469] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:11 tymorus-desktop kernel: [   54.516701] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:11 tymorus-desktop kernel: [   54.667852] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
May  7 15:52:13 tymorus-desktop kernel: [   56.603806] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=142 TOS=0x00 PREC=0x00 TTL=128 ID=3579 PROTO=UDP SPT=17500 DPT=17500 LEN=122 
May  7 15:52:14 tymorus-desktop kernel: [   57.370037] eth0: no IPv6 routers present
May  7 15:52:18 tymorus-desktop kernel: [   62.192645] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=34118 DF PROTO=TCP SPT=52195 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
May  7 15:52:18 tymorus-desktop kernel: [   62.192672] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=34118 DF PROTO=TCP SPT=52195 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0 
May  7 15:52:18 tymorus-desktop kernel: [   62.192699] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x10 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=4713 DPT=52195 WINDOW=0 RES=0x00 ACK RST URGP=0 
May  7 15:52:18 tymorus-desktop kernel: [   62.192711] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x10 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=4713 DPT=52195 WINDOW=0 RES=0x00 ACK RST URGP=0 
May  7 15:52:21 tymorus-desktop kernel: [   65.118153] CPU0 attaching NULL sched-domain.
May  7 15:52:21 tymorus-desktop kernel: [   65.118159] CPU1 attaching NULL sched-domain.
May  7 15:52:21 tymorus-desktop kernel: [   65.170146] CPU0 attaching sched-domain:
May  7 15:52:21 tymorus-desktop kernel: [   65.170152]  domain 0: span 0-1 level MC
May  7 15:52:21 tymorus-desktop kernel: [   65.170157]   groups: 0 1
May  7 15:52:21 tymorus-desktop kernel: [   65.170166] CPU1 attaching sched-domain:
May  7 15:52:21 tymorus-desktop kernel: [   65.170170]  domain 0: span 0-1 level MC
May  7 15:52:21 tymorus-desktop kernel: [   65.170174]   groups: 1 0
May  7 15:52:23 tymorus-desktop kernel: [   66.801470] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=42216 DF PROTO=UDP SPT=41319 DPT=53 LEN=48 
May  7 15:52:23 tymorus-desktop kernel: [   66.801483] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=42216 DF PROTO=UDP SPT=41319 DPT=53 LEN=48 
May  7 15:52:23 tymorus-desktop kernel: [   66.862330] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=52012 DF PROTO=UDP SPT=53 DPT=41319 LEN=99 
May  7 15:52:24 tymorus-desktop kernel: [   68.286016] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42364 DF PROTO=UDP SPT=51085 DPT=53 LEN=45 
May  7 15:52:24 tymorus-desktop kernel: [   68.286030] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42364 DF PROTO=UDP SPT=51085 DPT=53 LEN=45 
May  7 15:52:25 tymorus-desktop kernel: [   68.378045] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=81 TOS=0x00 PREC=0x00 TTL=255 ID=52013 DF PROTO=UDP SPT=53 DPT=51085 LEN=61 
May  7 15:52:25 tymorus-desktop kernel: [   68.378227] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=9343 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.378240] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=9343 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.495789] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=64 TOS=0x00 PREC=0x00 TTL=244 ID=31728 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4356 RES=0x00 ACK SYN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.495831] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9344 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=46 RES=0x00 ACK URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.495887] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=129 TOS=0x00 PREC=0x00 TTL=64 ID=9345 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=46 RES=0x00 ACK PSH URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.616024] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=219 TOS=0x00 PREC=0x00 TTL=244 ID=33818 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK PSH URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.616057] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=33821 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK FIN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.616108] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9346 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=54 RES=0x00 ACK URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.616153] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9347 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=54 RES=0x00 ACK FIN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.616287] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42397 DF PROTO=UDP SPT=36488 DPT=53 LEN=45 
May  7 15:52:25 tymorus-desktop kernel: [   68.616297] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42397 DF PROTO=UDP SPT=36488 DPT=53 LEN=45 
May  7 15:52:25 tymorus-desktop kernel: [   68.693285] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=81 TOS=0x00 PREC=0x00 TTL=255 ID=52014 DF PROTO=UDP SPT=53 DPT=36488 LEN=61 
May  7 15:52:25 tymorus-desktop kernel: [   68.693401] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25793 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.693413] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25793 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.732276] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=35887 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.811081] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=64 TOS=0x00 PREC=0x00 TTL=244 ID=37256 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4356 RES=0x00 ACK SYN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.811123] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25794 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=46 RES=0x00 ACK URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.811187] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=324 TOS=0x00 PREC=0x00 TTL=64 ID=25795 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=46 RES=0x00 ACK PSH URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.957049] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=296 TOS=0x00 PREC=0x00 TTL=244 ID=39779 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK PSH URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.957103] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=39781 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK FIN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.957136] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25796 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=54 RES=0x00 ACK URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   68.957194] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25797 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=54 RES=0x00 ACK FIN URGP=0 
May  7 15:52:25 tymorus-desktop kernel: [   69.073203] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=41921 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK URGP=0 
May  7 15:52:28 tymorus-desktop kernel: [   71.412904] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3593 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:28 tymorus-desktop kernel: [   71.677017] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3594 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:28 tymorus-desktop kernel: [   72.175650] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3595 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:29 tymorus-desktop kernel: [   72.439735] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3597 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:29 tymorus-desktop kernel: [   72.938969] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3598 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:29 tymorus-desktop kernel: [   73.204356] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3599 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:30 tymorus-desktop kernel: [   74.298542] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3603 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:31 tymorus-desktop kernel: [   75.061061] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3604 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:32 tymorus-desktop kernel: [   75.825769] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3605 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:33 tymorus-desktop kernel: [   76.919291] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3610 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:34 tymorus-desktop kernel: [   77.682176] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3611 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:35 tymorus-desktop kernel: [   78.446679] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3612 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:36 tymorus-desktop kernel: [   79.479989] vboxdrv: Trying to deactivate the NMI watchdog permanently...
May  7 15:52:36 tymorus-desktop kernel: [   79.479993] vboxdrv: Successfully done.
May  7 15:52:36 tymorus-desktop kernel: [   79.479995] vboxdrv: Found 2 processor cores.
May  7 15:52:36 tymorus-desktop kernel: [   79.480124] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e23a20
May  7 15:52:36 tymorus-desktop kernel: [   79.480141] vboxdrv: fAsync=0 offMin=0x160 offMax=0x84b
May  7 15:52:36 tymorus-desktop kernel: [   79.480800] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May  7 15:52:36 tymorus-desktop kernel: [   79.480802] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
May  7 15:52:36 tymorus-desktop kernel: [   79.538029] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=43489 DF PROTO=UDP SPT=56728 DPT=53 LEN=50 
May  7 15:52:36 tymorus-desktop kernel: [   79.538041] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=43489 DF PROTO=UDP SPT=56728 DPT=53 LEN=50 
May  7 15:52:36 tymorus-desktop kernel: [   79.539215] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3616 PROTO=UDP SPT=137 DPT=137 LEN=58 
May  7 15:52:36 tymorus-desktop kernel: [   79.746142] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=52015 DF PROTO=UDP SPT=53 DPT=56728 LEN=66 
May  7 15:52:36 tymorus-desktop kernel: [   80.302070] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3617 PROTO=UDP SPT=137 DPT=137 LEN=58 

```

---

### Post by Tymorus on 2010-05-12
[SIZE=4]Messages[/SIZE]
```

May  7 07:53:53 tymorus-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1293" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May  7 11:15:27 tymorus-desktop kernel: [132549.790117] usb 1-6: new high speed USB device using ehci_hcd and address 5
May  7 11:15:27 tymorus-desktop kernel: [132549.941971] usb 1-6: configuration #1 chosen from 1 choice
May  7 11:15:27 tymorus-desktop kernel: [132549.943338] scsi8 : SCSI emulation for USB Mass Storage devices
May  7 11:15:32 tymorus-desktop kernel: [132554.940781] scsi 8:0:0:0: Direct-Access     Seagate  FreeAgent Go     102F PQ: 0 ANSI: 4
May  7 11:15:32 tymorus-desktop kernel: [132554.941398] sd 8:0:0:0: Attached scsi generic sg3 type 0
May  7 11:15:32 tymorus-desktop kernel: [132554.950573] sd 8:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  7 11:15:32 tymorus-desktop kernel: [132554.951561] sd 8:0:0:0: [sdc] Write Protect is off
May  7 11:15:32 tymorus-desktop kernel: [132554.953010]  sdc: sdc1
May  7 11:15:32 tymorus-desktop kernel: [132554.980765] sd 8:0:0:0: [sdc] Attached SCSI disk
May  7 14:16:24 tymorus-desktop kernel: [143407.061307] type=1503 audit(1273256184.935:37): operation="open" pid=19619 parent=19618 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
May  7 14:17:01 tymorus-desktop kernel: [143443.405919] cron[23231]: segfault at 0 ip (null) sp 00007fff60396348 error 14 in cron[400000+9000]
May  7 14:18:06 tymorus-desktop kernel: [143508.167891] udev: starting version 151
May  7 14:26:42 tymorus-desktop kernel: [144024.893005] type=1505 audit(1273256802.765:38): operation="profile_replace" pid=15567 name=/usr/share/gdm/guest-session/Xsession
May  7 14:26:42 tymorus-desktop kernel: [144025.052513] type=1505 audit(1273256802.925:39): operation="profile_replace" pid=15568 name=/sbin/dhclient3
May  7 14:26:42 tymorus-desktop kernel: [144025.052662] type=1505 audit(1273256802.925:40): operation="profile_replace" pid=15568 name=/usr/lib/NetworkManager/nm-dhcp-client.action
May  7 14:26:42 tymorus-desktop kernel: [144025.052749] type=1505 audit(1273256802.925:41): operation="profile_replace" pid=15568 name=/usr/lib/connman/scripts/dhclient-script
May  7 14:26:51 tymorus-desktop kernel: [144033.163369] type=1505 audit(1273256811.035:42): operation="profile_replace" pid=15569 name=/usr/bin/evince
May  7 14:26:51 tymorus-desktop kernel: [144033.167331] type=1505 audit(1273256811.035:43): operation="profile_replace" pid=15569 name=/usr/bin/evince-previewer
May  7 14:26:51 tymorus-desktop kernel: [144033.217776] type=1505 audit(1273256811.085:44): operation="profile_replace" pid=15569 name=/usr/bin/evince-thumbnailer
May  7 14:26:51 tymorus-desktop kernel: [144033.319606] type=1505 audit(1273256811.185:45): operation="profile_replace" pid=15571 name=/usr/bin/freshclam
May  7 14:26:51 tymorus-desktop kernel: [144033.373688] type=1505 audit(1273256811.245:46): operation="profile_replace" pid=15572 name=/usr/sbin/clamd
May  7 14:26:51 tymorus-desktop kernel: [144033.573540] type=1505 audit(1273256811.445:47): operation="profile_replace" pid=15573 name=/usr/lib/cups/backend/cups-pdf
May  7 14:26:51 tymorus-desktop kernel: [144033.573791] type=1505 audit(1273256811.445:48): operation="profile_replace" pid=15573 name=/usr/sbin/cupsd
May  7 14:26:51 tymorus-desktop kernel: [144033.652381] type=1505 audit(1273256811.525:49): operation="profile_replace" pid=15574 name=/usr/sbin/mysqld
May  7 14:26:51 tymorus-desktop kernel: [144033.724103] type=1505 audit(1273256811.595:50): operation="profile_replace" pid=15575 name=/usr/sbin/mysqld-akonadi
May  7 14:26:51 tymorus-desktop kernel: [144033.790856] type=1505 audit(1273256811.665:51): operation="profile_replace" pid=15576 name=/usr/sbin/tcpdump
May  7 14:44:00 tymorus-desktop kernel: [145062.660123] type=1503 audit(1273257840.535:52): operation="open" pid=2492 parent=2491 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
May  7 14:44:01 tymorus-desktop kernel: [145063.317629] type=1503 audit(1273257841.185:53): operation="open" pid=2551 parent=2550 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
May  7 15:15:42 tymorus-desktop kernel: [146964.902563] type=1505 audit(1273259742.775:54): operation="profile_replace" pid=23679 name=/usr/share/gdm/guest-session/Xsession
May  7 15:15:42 tymorus-desktop kernel: [146965.033620] type=1505 audit(1273259742.905:55): operation="profile_replace" pid=23680 name=/sbin/dhclient3
May  7 15:15:42 tymorus-desktop kernel: [146965.033765] type=1505 audit(1273259742.905:56): operation="profile_replace" pid=23680 name=/usr/lib/NetworkManager/nm-dhcp-client.action
May  7 15:15:42 tymorus-desktop kernel: [146965.033823] type=1505 audit(1273259742.905:57): operation="profile_replace" pid=23680 name=/usr/lib/connman/scripts/dhclient-script
May  7 15:15:46 tymorus-desktop kernel: [146968.990896] type=1505 audit(1273259746.865:58): operation="profile_replace" pid=23681 name=/usr/bin/evince
May  7 15:15:46 tymorus-desktop kernel: [146968.992431] type=1505 audit(1273259746.865:59): operation="profile_replace" pid=23681 name=/usr/bin/evince-previewer
May  7 15:15:46 tymorus-desktop kernel: [146968.993464] type=1505 audit(1273259746.865:60): operation="profile_replace" pid=23681 name=/usr/bin/evince-thumbnailer
May  7 15:15:46 tymorus-desktop kernel: [146969.100867] type=1505 audit(1273259746.975:61): operation="profile_replace" pid=23683 name=/usr/bin/freshclam
May  7 15:15:47 tymorus-desktop kernel: [146969.157139] type=1505 audit(1273259747.025:62): operation="profile_replace" pid=23684 name=/usr/sbin/clamd
May  7 15:15:47 tymorus-desktop kernel: [146969.383235] type=1505 audit(1273259747.255:63): operation="profile_replace" pid=23685 name=/usr/lib/cups/backend/cups-pdf
May  7 15:20:42 tymorus-desktop kernel: [147264.362506] __ratelimit: 12 callbacks suppressed
May  7 15:20:42 tymorus-desktop kernel: [147264.362509] type=1505 audit(1273260042.236:68): operation="profile_replace" pid=27944 name=/sbin/dhclient3
May  7 15:20:42 tymorus-desktop kernel: [147264.363115] type=1505 audit(1273260042.236:69): operation="profile_replace" pid=27944 name=/usr/lib/NetworkManager/nm-dhcp-client.action
May  7 15:20:42 tymorus-desktop kernel: [147264.363452] type=1505 audit(1273260042.236:70): operation="profile_replace" pid=27944 name=/usr/lib/connman/scripts/dhclient-script
May  7 15:20:44 tymorus-desktop kernel: Kernel logging (proc) stopped.
May  7 15:20:45 tymorus-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="28098" x-info="http://www.rsyslog.com"] (re)start
May  7 15:20:45 tymorus-desktop rsyslogd: rsyslogd's groupid changed to 102
May  7 15:20:45 tymorus-desktop rsyslogd: rsyslogd's userid changed to 101
May  7 15:50:21 tymorus-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="28098" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  7 15:52:11 tymorus-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  7 15:52:11 tymorus-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1110" x-info="http://www.rsyslog.com"] (re)start
May  7 15:52:11 tymorus-desktop rsyslogd: rsyslogd's groupid changed to 102
May  7 15:52:12 tymorus-desktop rsyslogd: rsyslogd's userid changed to 101
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Command line: root=UUID=25cf6f53-53a4-48bb-ae93-80c3c92b1579 ro quiet splash
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] KERNEL supported cpus:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   Intel GenuineIntel
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   AMD AuthenticAMD
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   Centaur CentaurHauls
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098400 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 0000000000098400 - 00000000000a0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfedf800 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfedf800 - 00000000bfee0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] DMI present.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] last_pfn = 0xbfedf max_arch_pfn = 0x400000000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] modified physical RAM map:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000098400 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000098400 - 00000000000a0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bfedf800 (usable)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfedf800 - 00000000bfee0000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000bfef0000 - 00000000bff00000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bfedf000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] RAMDISK: 377ff000 - 37fef7af
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f83a0 00024 (v02 HPQOEM)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: XSDT 00000000bfee30c0 00054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: FACP 00000000bfee7900 000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: DSDT 00000000bfee3280 0463B (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: FACS 00000000bfee0000 00040
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: SLIC 00000000bfee7b40 00176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: HPET 00000000bfee7d00 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: MCFG 00000000bfee7d80 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: APIC 00000000bfee7a40 00084 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: SSDT 00000000bfee82e0 00304 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] No NUMA configuration found
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Faking a node at 0000000000000000-00000000bfedf000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000000bfedf000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   bootmap [0000000000018000 -  000000000002ffdf] pages 18
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bfedf000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #3 [00377ff000 - 0037fef7af]          RAMDISK ==> [00377ff000 - 0037fef7af]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #4 [0000098400 - 0000100000]    BIOS reserved ==> [0000098400 - 0000100000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a740]              BRK ==> [0001a2a000 - 0001a2a740]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f5f10] f5f10
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Zone PFN ranges:
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Movable zone start PFN for each node
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x00000098
May  7 15:52:12 tymorus-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000bfedf
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000098000 - 0000000000099000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000099000 - 00000000000a0000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:30100000)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 775165
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Policy zone: DMA32
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Kernel command line: root=UUID=25cf6f53-53a4-48bb-ae93-80c3c92b1579 ro quiet splash
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Initializing CPU#0
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Checking aperture...
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] No AGP bridge found
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Memory: 3081844k/3144572k available (5409k kernel code, 480k absent, 62248k reserved, 2976k data, 876k init)
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Hierarchical RCU implementation.
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] console [tty0] enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Fast TSC calibration using PIT
May  7 15:52:12 tymorus-desktop kernel: [    0.000000] Detected 2200.711 MHz processor.
May  7 15:52:12 tymorus-desktop kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4401.42 BogoMIPS (lpj=22007110)
May  7 15:52:12 tymorus-desktop kernel: [    0.010039] Security Framework initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.010059] AppArmor: AppArmor initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.010467] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.012969] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.014097] Mount-cache hash table entries: 256
May  7 15:52:12 tymorus-desktop kernel: [    0.014273] Initializing cgroup subsys ns
May  7 15:52:12 tymorus-desktop kernel: [    0.014279] Initializing cgroup subsys cpuacct
May  7 15:52:12 tymorus-desktop kernel: [    0.014283] Initializing cgroup subsys memory
May  7 15:52:12 tymorus-desktop kernel: [    0.014291] Initializing cgroup subsys devices
May  7 15:52:12 tymorus-desktop kernel: [    0.014294] Initializing cgroup subsys freezer
May  7 15:52:12 tymorus-desktop kernel: [    0.014296] Initializing cgroup subsys net_cls
May  7 15:52:12 tymorus-desktop kernel: [    0.014318] CPU: L1 I cache: 32K, L1 D cache: 32K
May  7 15:52:12 tymorus-desktop kernel: [    0.014321] CPU: L2 cache: 2048K
May  7 15:52:12 tymorus-desktop kernel: [    0.014324] CPU 0/0x0 -> Node 0
May  7 15:52:12 tymorus-desktop kernel: [    0.014326] CPU: Physical Processor ID: 0
May  7 15:52:12 tymorus-desktop kernel: [    0.014328] CPU: Processor Core ID: 0
May  7 15:52:12 tymorus-desktop kernel: [    0.014332] mce: CPU supports 6 MCE banks
May  7 15:52:12 tymorus-desktop kernel: [    0.014340] CPU0: Thermal monitoring enabled (TM2)
May  7 15:52:12 tymorus-desktop kernel: [    0.014346] using mwait in idle threads.
May  7 15:52:12 tymorus-desktop kernel: [    0.014347] Performance Events: Core2 events, Intel PMU driver.
May  7 15:52:12 tymorus-desktop kernel: [    0.014354] ... version:                2
May  7 15:52:12 tymorus-desktop kernel: [    0.014356] ... bit width:              40
May  7 15:52:12 tymorus-desktop kernel: [    0.014357] ... generic registers:      2
May  7 15:52:12 tymorus-desktop kernel: [    0.014359] ... value mask:             000000ffffffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.014361] ... max period:             000000007fffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.014362] ... fixed-purpose events:   3
May  7 15:52:12 tymorus-desktop kernel: [    0.014364] ... event mask:             0000000700000003
May  7 15:52:12 tymorus-desktop kernel: [    0.017555] ACPI: Core revision 20090903
May  7 15:52:12 tymorus-desktop kernel: [    0.030022] ftrace: converting mcount calls to 0f 1f 44 00 00
May  7 15:52:12 tymorus-desktop kernel: [    0.030032] ftrace: allocating 22518 entries in 89 pages
May  7 15:52:12 tymorus-desktop kernel: [    0.040065] Setting APIC routing to flat
May  7 15:52:12 tymorus-desktop kernel: [    0.040378] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  7 15:52:12 tymorus-desktop kernel: [    0.144850] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
May  7 15:52:12 tymorus-desktop kernel: [    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] Initializing CPU#1
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: L2 cache: 2048K
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU 1/0x1 -> Node 0
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: Physical Processor ID: 0
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU: Processor Core ID: 1
May  7 15:52:12 tymorus-desktop kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
May  7 15:52:12 tymorus-desktop kernel: [    0.300085] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
May  7 15:52:12 tymorus-desktop kernel: [    0.300092] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May  7 15:52:12 tymorus-desktop kernel: [    0.310018] Brought up 2 CPUs
May  7 15:52:12 tymorus-desktop kernel: [    0.310021] Total of 2 processors activated (8802.70 BogoMIPS).
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] devtmpfs: initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] regulator: core version 0.5
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] Time: 15:51:29  Date: 05/07/10
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] NET: Registered protocol family 16
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] Trying to unpack rootfs image as initramfs...
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] ACPI: bus type pci registered
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
May  7 15:52:12 tymorus-desktop kernel: [    0.310550] PCI: MCFG area at f0000000 reserved in E820
May  7 15:52:12 tymorus-desktop kernel: [    0.311321] PCI: Using MMCONFIG at f0000000 - f3ffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.311323] PCI: Using configuration type 1 for base access
May  7 15:52:12 tymorus-desktop kernel: [    0.320152] bio: create slab <bio-0> at 0
May  7 15:52:12 tymorus-desktop kernel: [    0.326678] ACPI: Interpreter enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.326684] ACPI: (supports S0 S1 S3 S4 S5)
May  7 15:52:12 tymorus-desktop kernel: [    0.326713] ACPI: Using IOAPIC for interrupt routing
May  7 15:52:12 tymorus-desktop kernel: [    0.330909] ACPI: No dock devices found.
May  7 15:52:12 tymorus-desktop kernel: [    0.331014] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  7 15:52:12 tymorus-desktop kernel: [    0.331130] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.331133] pci 0000:00:01.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331239] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.331243] pci 0000:00:1b.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331526] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.331530] pci 0000:00:1d.7: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.331812] pci 0000:00:1f.2: PME# supported from D3hot
May  7 15:52:12 tymorus-desktop kernel: [    0.331816] pci 0000:00:1f.2: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332104] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
May  7 15:52:12 tymorus-desktop kernel: [    0.332108] pci 0000:02:01.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332191] pci 0000:02:04.0: PME# supported from D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.332195] pci 0000:02:04.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332282] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
May  7 15:52:12 tymorus-desktop kernel: [    0.332286] pci 0000:02:08.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.332323] pci 0000:00:1e.0: transparent bridge
May  7 15:52:12 tymorus-desktop kernel: [    0.343398] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343506] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  7 15:52:12 tymorus-desktop kernel: [    0.343610] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343713] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343816] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.343919] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  7 15:52:12 tymorus-desktop kernel: [    0.344024] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May  7 15:52:12 tymorus-desktop kernel: [    0.344128] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 9 10 11 12 14 15)
May  7 15:52:12 tymorus-desktop kernel: [    0.344261] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
May  7 15:52:12 tymorus-desktop kernel: [    0.344265] vgaarb: loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.344381] SCSI subsystem initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.344564] usbcore: registered new interface driver usbfs
May  7 15:52:12 tymorus-desktop kernel: [    0.344576] usbcore: registered new interface driver hub
May  7 15:52:12 tymorus-desktop kernel: [    0.344607] usbcore: registered new device driver usb
May  7 15:52:12 tymorus-desktop kernel: [    0.344735] ACPI: WMI: Mapper loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.344736] PCI: Using ACPI for IRQ routing
May  7 15:52:12 tymorus-desktop kernel: [    0.344894] NetLabel: Initializing
May  7 15:52:12 tymorus-desktop kernel: [    0.344896] NetLabel:  domain hash size = 128
May  7 15:52:12 tymorus-desktop kernel: [    0.344897] NetLabel:  protocols = UNLABELED CIPSOv4
May  7 15:52:12 tymorus-desktop kernel: [    0.344910] NetLabel:  unlabeled traffic allowed by default
May  7 15:52:12 tymorus-desktop kernel: [    0.344944] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
May  7 15:52:12 tymorus-desktop kernel: [    0.344948] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
May  7 15:52:12 tymorus-desktop kernel: [    0.350032] Switching to clocksource tsc
May  7 15:52:12 tymorus-desktop kernel: [    0.351887] AppArmor: AppArmor Filesystem Enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.351911] pnp: PnP ACPI init
May  7 15:52:12 tymorus-desktop kernel: [    0.351929] ACPI: bus type pnp registered
May  7 15:52:12 tymorus-desktop kernel: [    0.353488] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 688 (bits) (20090903/dsopcode-596)
May  7 15:52:12 tymorus-desktop kernel: [    0.353495] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.MEM_._CRS] (Node ffff8800bc641fc0), AE_AML_BUFFER_LIMIT
May  7 15:52:12 tymorus-desktop kernel: [    0.353519] ACPI Error (uteval-0250): Method execution failed [\_SB_.MEM_._CRS] (Node ffff8800bc641fc0), AE_AML_BUFFER_LIMIT
May  7 15:52:12 tymorus-desktop kernel: [    0.353582] pnp: PnP ACPI: found 12 devices
May  7 15:52:12 tymorus-desktop kernel: [    0.353584] ACPI: ACPI bus type pnp unregistered
May  7 15:52:12 tymorus-desktop kernel: [    0.353598] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353601] system 00:01: ioport range 0x800-0x87f has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353604] system 00:01: ioport range 0x294-0x297 has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353606] system 00:01: ioport range 0x880-0x88f has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353613] system 00:08: ioport range 0x400-0x4bf has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.353620] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
May  7 15:52:12 tymorus-desktop kernel: [    0.358351] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
May  7 15:52:12 tymorus-desktop kernel: [    0.358354] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
May  7 15:52:12 tymorus-desktop kernel: [    0.358358] pci 0000:00:01.0:   MEM window: 0xf8000000-0xfbffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.358362] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
May  7 15:52:12 tymorus-desktop kernel: [    0.358367] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
May  7 15:52:12 tymorus-desktop kernel: [    0.358370] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
May  7 15:52:12 tymorus-desktop kernel: [    0.358374] pci 0000:00:1e.0:   MEM window: 0xfde00000-0xfdefffff
May  7 15:52:12 tymorus-desktop kernel: [    0.358378] pci 0000:00:1e.0:   PREFETCH window: disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.358400] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [    0.358486] NET: Registered protocol family 2
May  7 15:52:12 tymorus-desktop kernel: [    0.358664] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.360006] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.365392] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.366007] TCP: Hash tables configured (established 524288 bind 65536)
May  7 15:52:12 tymorus-desktop kernel: [    0.366010] TCP reno registered
May  7 15:52:12 tymorus-desktop kernel: [    0.366155] NET: Registered protocol family 1
May  7 15:52:12 tymorus-desktop kernel: [    0.366290] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
May  7 15:52:12 tymorus-desktop kernel: [    0.366570] Scanning for low memory corruption every 60 seconds
May  7 15:52:12 tymorus-desktop kernel: [    0.366717] audit: initializing netlink socket (disabled)
May  7 15:52:12 tymorus-desktop kernel: [    0.366728] type=2000 audit(1273247488.359:1): initialized
May  7 15:52:12 tymorus-desktop kernel: [    0.375840] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  7 15:52:12 tymorus-desktop kernel: [    0.377171] VFS: Disk quotas dquot_6.5.2
May  7 15:52:12 tymorus-desktop kernel: [    0.377223] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  7 15:52:12 tymorus-desktop kernel: [    0.377810] fuse init (API version 7.13)
May  7 15:52:12 tymorus-desktop kernel: [    0.377894] msgmni has been set to 6019
May  7 15:52:12 tymorus-desktop kernel: [    0.378108] alg: No test for stdrng (krng)
May  7 15:52:12 tymorus-desktop kernel: [    0.378160] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May  7 15:52:12 tymorus-desktop kernel: [    0.378163] io scheduler noop registered
May  7 15:52:12 tymorus-desktop kernel: [    0.378165] io scheduler anticipatory registered
May  7 15:52:12 tymorus-desktop kernel: [    0.378167] io scheduler deadline registered
May  7 15:52:12 tymorus-desktop kernel: [    0.378198] io scheduler cfq registered (default)
May  7 15:52:12 tymorus-desktop kernel: [    0.378414] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  7 15:52:12 tymorus-desktop kernel: [    0.378436] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  7 15:52:12 tymorus-desktop kernel: [    0.378533] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
May  7 15:52:12 tymorus-desktop kernel: [    0.378536] ACPI: Power Button [PWRB]
May  7 15:52:12 tymorus-desktop kernel: [    0.378595] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  7 15:52:12 tymorus-desktop kernel: [    0.378598] ACPI: Power Button [PWRF]
May  7 15:52:12 tymorus-desktop kernel: [    0.378644] fan PNP0C0B:00: registered as cooling_device0
May  7 15:52:12 tymorus-desktop kernel: [    0.378649] ACPI: Fan [FAN] (on)
May  7 15:52:12 tymorus-desktop kernel: [    0.379108] ACPI: SSDT 00000000bfee7e00 001B7 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.379304] processor LNXCPU:00: registered as cooling_device1
May  7 15:52:12 tymorus-desktop kernel: [    0.379472] ACPI: SSDT 00000000bfee8210 000CE (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
May  7 15:52:12 tymorus-desktop kernel: [    0.379674] processor LNXCPU:01: registered as cooling_device2
May  7 15:52:12 tymorus-desktop kernel: [    0.381686] thermal LNXTHERM:01: registered as thermal_zone0
May  7 15:52:12 tymorus-desktop kernel: [    0.381693] ACPI: Thermal Zone [THRM] (35 C)
May  7 15:52:12 tymorus-desktop kernel: [    0.383051] Linux agpgart interface v0.103
May  7 15:52:12 tymorus-desktop kernel: [    0.383089] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
May  7 15:52:12 tymorus-desktop kernel: [    0.384314] brd: module loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.384768] loop: module loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.384853] input: Macintosh mouse button emulation as /devices/virtual/input/input2
May  7 15:52:12 tymorus-desktop kernel: [    0.384983] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May  7 15:52:12 tymorus-desktop kernel: [    0.385132] scsi0 : ata_piix
May  7 15:52:12 tymorus-desktop kernel: [    0.385203] scsi1 : ata_piix
May  7 15:52:12 tymorus-desktop kernel: [    0.385612] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
May  7 15:52:12 tymorus-desktop kernel: [    0.385615] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
May  7 15:52:12 tymorus-desktop kernel: [    0.385926] Fixed MDIO Bus: probed
May  7 15:52:12 tymorus-desktop kernel: [    0.385959] PPP generic driver version 2.4.2
May  7 15:52:12 tymorus-desktop kernel: [    0.385997] tun: Universal TUN/TAP device driver, 1.6
May  7 15:52:12 tymorus-desktop kernel: [    0.385998] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  7 15:52:12 tymorus-desktop kernel: [    0.386087] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  7 15:52:12 tymorus-desktop kernel: [    0.386116] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  7 15:52:12 tymorus-desktop kernel: [    0.386135] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.386166] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
May  7 15:52:12 tymorus-desktop kernel: [    0.386187] ehci_hcd 0000:00:1d.7: using broken periodic workaround
May  7 15:52:12 tymorus-desktop kernel: [    0.390127] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
May  7 15:52:12 tymorus-desktop kernel: [    0.409577] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
May  7 15:52:12 tymorus-desktop kernel: [    0.409735] usb usb1: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.409764] hub 1-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.409772] hub 1-0:1.0: 8 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.409843] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  7 15:52:12 tymorus-desktop kernel: [    0.409859] uhci_hcd: USB Universal Host Controller Interface driver
May  7 15:52:12 tymorus-desktop kernel: [    0.409917] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May  7 15:52:12 tymorus-desktop kernel: [    0.409930] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.409966] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May  7 15:52:12 tymorus-desktop kernel: [    0.409993] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
May  7 15:52:12 tymorus-desktop kernel: [    0.410075] usb usb2: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410099] hub 2-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410106] hub 2-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410159] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  7 15:52:12 tymorus-desktop kernel: [    0.410168] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.410199] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
May  7 15:52:12 tymorus-desktop kernel: [    0.410230] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
May  7 15:52:12 tymorus-desktop kernel: [    0.410314] usb usb3: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410337] hub 3-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410343] hub 3-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410382] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May  7 15:52:12 tymorus-desktop kernel: [    0.410390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.410423] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
May  7 15:52:12 tymorus-desktop kernel: [    0.410451] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
May  7 15:52:12 tymorus-desktop kernel: [    0.410529] usb usb4: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410558] hub 4-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410564] hub 4-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410605] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [    0.410614] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May  7 15:52:12 tymorus-desktop kernel: [    0.410641] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
May  7 15:52:12 tymorus-desktop kernel: [    0.410669] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
May  7 15:52:12 tymorus-desktop kernel: [    0.410748] usb usb5: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.410771] hub 5-0:1.0: USB hub found
May  7 15:52:12 tymorus-desktop kernel: [    0.410779] hub 5-0:1.0: 2 ports detected
May  7 15:52:12 tymorus-desktop kernel: [    0.410865] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  7 15:52:12 tymorus-desktop kernel: [    0.410867] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  7 15:52:12 tymorus-desktop kernel: [    0.411511] serio: i8042 KBD port at 0x60,0x64 irq 1
May  7 15:52:12 tymorus-desktop kernel: [    0.411629] mice: PS/2 mouse device common for all mice
May  7 15:52:12 tymorus-desktop kernel: [    0.411738] rtc_cmos 00:04: RTC can wake from S4
May  7 15:52:12 tymorus-desktop kernel: [    0.411777] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  7 15:52:12 tymorus-desktop kernel: [    0.411804] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
May  7 15:52:12 tymorus-desktop kernel: [    0.411928] device-mapper: uevent: version 1.0.3
May  7 15:52:12 tymorus-desktop kernel: [    0.412048] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
May  7 15:52:12 tymorus-desktop kernel: [    0.412109] device-mapper: multipath: version 1.1.0 loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.412112] device-mapper: multipath round-robin: version 1.0.0 loaded
May  7 15:52:12 tymorus-desktop kernel: [    0.412263] cpuidle: using governor ladder
May  7 15:52:12 tymorus-desktop kernel: [    0.412265] cpuidle: using governor menu
May  7 15:52:12 tymorus-desktop kernel: [    0.412595] TCP cubic registered
May  7 15:52:12 tymorus-desktop kernel: [    0.412711] NET: Registered protocol family 10
May  7 15:52:12 tymorus-desktop kernel: [    0.413148] lo: Disabled Privacy Extensions
May  7 15:52:12 tymorus-desktop kernel: [    0.413408] NET: Registered protocol family 17
May  7 15:52:12 tymorus-desktop kernel: [    0.414658] registered taskstats version 1
May  7 15:52:12 tymorus-desktop kernel: [    0.414939]   Magic number: 10:448:891
May  7 15:52:12 tymorus-desktop kernel: [    0.415018] rtc_cmos 00:04: setting system clock to 2010-05-07 15:51:29 UTC (1273247489)
May  7 15:52:12 tymorus-desktop kernel: [    0.415021] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  7 15:52:12 tymorus-desktop kernel: [    0.415023] EDD information not available.
May  7 15:52:12 tymorus-desktop kernel: [    0.439590] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
May  7 15:52:12 tymorus-desktop kernel: [    0.490414] Freeing initrd memory: 8129k freed
May  7 15:52:12 tymorus-desktop kernel: [    0.606242] ata1.01: ATA-7: MAXTOR STM3320620A, 3.AAE, max UDMA/100
May  7 15:52:12 tymorus-desktop kernel: [    0.606248] ata1.01: 625142448 sectors, multi 16: LBA48
May  7 15:52:12 tymorus-desktop kernel: [    0.606274] ata1.01: limited to UDMA/33 due to 40-wire cable
May  7 15:52:12 tymorus-desktop kernel: [    0.689308] ata1.01: configured for UDMA/33
May  7 15:52:12 tymorus-desktop kernel: [    0.689478] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May  7 15:52:12 tymorus-desktop kernel: [    0.689630] sd 0:0:1:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
May  7 15:52:12 tymorus-desktop kernel: [    0.689666] sd 0:0:1:0: Attached scsi generic sg0 type 0
May  7 15:52:12 tymorus-desktop kernel: [    0.689677] sd 0:0:1:0: [sda] Write Protect is off
May  7 15:52:12 tymorus-desktop kernel: [    0.689703] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  7 15:52:12 tymorus-desktop kernel: [    0.689853]  sda: sda1 sda2 < sda5 sda6
May  7 15:52:12 tymorus-desktop kernel: [    0.789927] usb 1-6: new high speed USB device using ehci_hcd and address 3
May  7 15:52:12 tymorus-desktop kernel: [    0.793638]  sda7 >
May  7 15:52:12 tymorus-desktop kernel: [    0.794004] sd 0:0:1:0: [sda] Attached SCSI disk
May  7 15:52:12 tymorus-desktop kernel: [    0.794026] Freeing unused kernel memory: 876k freed
May  7 15:52:12 tymorus-desktop kernel: [    0.794402] Write protecting the kernel read-only data: 7680k
May  7 15:52:12 tymorus-desktop kernel: [    0.808626] udev: starting version 151
May  7 15:52:12 tymorus-desktop kernel: [    0.900257] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May  7 15:52:12 tymorus-desktop kernel: [    0.900374] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
May  7 15:52:12 tymorus-desktop kernel: [    0.900378] ahci 0000:00:1f.2: flags: 64bit ncq led clo
May  7 15:52:12 tymorus-desktop kernel: [    0.908621] scsi2 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908717] scsi3 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908773] scsi4 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908827] scsi5 : ahci
May  7 15:52:12 tymorus-desktop kernel: [    0.908960] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.908963] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.908966] ata5: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.908969] ata6: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 25
May  7 15:52:12 tymorus-desktop kernel: [    0.909669] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
May  7 15:52:12 tymorus-desktop kernel: [    0.909671] e100: Copyright(c) 1999-2006 Intel Corporation
May  7 15:52:12 tymorus-desktop kernel: [    0.909717] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  7 15:52:12 tymorus-desktop kernel: [    0.933198] e100 0000:02:08.0: PME# disabled
May  7 15:52:12 tymorus-desktop kernel: [    0.933721] e100: eth0: e100_probe: addr 0xfdefe000, irq 20, MAC addr 00:1e:8c:2a:16:1e
May  7 15:52:12 tymorus-desktop kernel: [    0.941794] usb 1-6: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    0.948169] Initializing USB Mass Storage driver...
May  7 15:52:12 tymorus-desktop kernel: [    0.948283] scsi6 : SCSI emulation for USB Mass Storage devices
May  7 15:52:12 tymorus-desktop kernel: [    0.948363] usbcore: registered new interface driver usb-storage
May  7 15:52:12 tymorus-desktop kernel: [    0.948366] USB Mass Storage support registered.
May  7 15:52:12 tymorus-desktop kernel: [    1.060066] usb 1-7: new high speed USB device using ehci_hcd and address 4
May  7 15:52:12 tymorus-desktop kernel: [    1.212177] usb 1-7: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    1.212522] scsi7 : SCSI emulation for USB Mass Storage devices
May  7 15:52:12 tymorus-desktop kernel: [    1.245596] EXT3-fs: INFO: recovery required on readonly filesystem.
May  7 15:52:12 tymorus-desktop kernel: [    1.245600] EXT3-fs: write access will be enabled during recovery.
May  7 15:52:12 tymorus-desktop kernel: [    1.250098] ata6: SATA link down (SStatus 0 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250129] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250151] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250169] ata5: SATA link down (SStatus 0 SControl 300)
May  7 15:52:12 tymorus-desktop kernel: [    1.250920] ata3.00: ATA-7: ST3500630AS, 3.CHL, max UDMA/100
May  7 15:52:12 tymorus-desktop kernel: [    1.250922] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
May  7 15:52:12 tymorus-desktop kernel: [    1.251063] ata4.00: ATAPI: TSSTcorp CDDVDW TS-H653N, 0609, max UDMA/33, ATAPI AN
May  7 15:52:12 tymorus-desktop kernel: [    1.251922] ata3.00: configured for UDMA/100
May  7 15:52:12 tymorus-desktop kernel: [    1.252062] scsi 2:0:0:0: Direct-Access     ATA      ST3500630AS      3.CH PQ: 0 ANSI: 5
May  7 15:52:12 tymorus-desktop kernel: [    1.252231] sd 2:0:0:0: Attached scsi generic sg1 type 0
May  7 15:52:12 tymorus-desktop kernel: [    1.252264] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  7 15:52:12 tymorus-desktop kernel: [    1.252317] sd 2:0:0:0: [sdb] Write Protect is off
May  7 15:52:12 tymorus-desktop kernel: [    1.252342] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  7 15:52:12 tymorus-desktop kernel: [    1.252465]  sdb:
May  7 15:52:12 tymorus-desktop kernel: [    1.252500] ata4.00: configured for UDMA/33
May  7 15:52:12 tymorus-desktop kernel: [    1.253527] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653N  0609 PQ: 0 ANSI: 5
May  7 15:52:12 tymorus-desktop kernel: [    1.257301] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
May  7 15:52:12 tymorus-desktop kernel: [    1.257306] Uniform CD-ROM driver Revision: 3.20
May  7 15:52:12 tymorus-desktop kernel: [    1.257497] sr 3:0:0:0: Attached scsi generic sg2 type 5
May  7 15:52:12 tymorus-desktop kernel: [    1.278314]  sdb1 sdb2
May  7 15:52:12 tymorus-desktop kernel: [    1.278580] sd 2:0:0:0: [sdb] Attached SCSI disk
May  7 15:52:12 tymorus-desktop kernel: [    1.282218] ohci1394 0000:02:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May  7 15:52:12 tymorus-desktop kernel: [    1.342109] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
May  7 15:52:12 tymorus-desktop kernel: [    1.490039] usb 3-1: new low speed USB device using uhci_hcd and address 2
May  7 15:52:12 tymorus-desktop kernel: [    1.675386] usb 3-1: configuration #1 chosen from 1 choice
May  7 15:52:12 tymorus-desktop kernel: [    1.686761] usbcore: registered new interface driver hiddev
May  7 15:52:12 tymorus-desktop kernel: [    1.728070] input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
May  7 15:52:12 tymorus-desktop kernel: [    1.728164] generic-usb 0003:045E:00B9.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:1d.1-1/input0
May  7 15:52:12 tymorus-desktop kernel: [    1.728186] usbcore: registered new interface driver usbhid
May  7 15:52:12 tymorus-desktop kernel: [    1.728189] usbhid: v2.6:USB HID core driver
May  7 15:52:12 tymorus-desktop kernel: [    5.942048] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent Go     102F PQ: 0 ANSI: 4
May  7 15:52:12 tymorus-desktop kernel: [    5.942527] sd 6:0:0:0: Attached scsi generic sg3 type 0
May  7 15:52:12 tymorus-desktop kernel: [    5.943279] sd 6:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
May  7 15:52:12 tymorus-desktop kernel: [    5.943652] sd 6:0:0:0: [sdc] Write Protect is off
May  7 15:52:12 tymorus-desktop kernel: [    5.944654]  sdc: sdc1
May  7 15:52:12 tymorus-desktop kernel: [    5.971772] sd 6:0:0:0: [sdc] Attached SCSI disk
May  7 15:52:12 tymorus-desktop kernel: [    6.211307] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.211919] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.212413] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213043] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213501] sd 7:0:0:0: Attached scsi generic sg4 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213698] sd 7:0:0:1: Attached scsi generic sg5 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213836] sd 7:0:0:2: Attached scsi generic sg6 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.213959] sd 7:0:0:3: Attached scsi generic sg7 type 0
May  7 15:52:12 tymorus-desktop kernel: [    6.215749] sd 7:0:0:0: [sdd] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [    6.219909] sd 7:0:0:1: [sde] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [    6.220528] sd 7:0:0:2: [sdf] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [    6.221273] sd 7:0:0:3: [sdg] Attached SCSI removable disk
May  7 15:52:12 tymorus-desktop kernel: [   13.723570] kjournald starting.  Commit interval 5 seconds
May  7 15:52:12 tymorus-desktop kernel: [   13.723588] EXT3-fs: sda6: orphan cleanup on readonly fs
May  7 15:52:12 tymorus-desktop kernel: [   13.794400] EXT3-fs: sda6: 17 orphan inodes deleted
May  7 15:52:12 tymorus-desktop kernel: [   13.794404] EXT3-fs: recovery complete.
May  7 15:52:12 tymorus-desktop kernel: [   13.901769] EXT3-fs: mounted filesystem with ordered data mode.
May  7 15:52:12 tymorus-desktop kernel: [   16.097279] Adding 281096k swap on /dev/sda7.  Priority:-1 extents:1 across:281096k
May  7 15:52:12 tymorus-desktop kernel: [   16.506019] udev: starting version 151
May  7 15:52:12 tymorus-desktop kernel: [   17.888234] type=1505 audit(1273261906.966:2):  operation="profile_load" pid=552 name="/sbin/dhclient3"
May  7 15:52:12 tymorus-desktop kernel: [   17.888903] type=1505 audit(1273261906.966:3):  operation="profile_load" pid=552 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  7 15:52:12 tymorus-desktop kernel: [   17.889245] type=1505 audit(1273261906.966:4):  operation="profile_load" pid=552 name="/usr/lib/connman/scripts/dhclient-script"
May  7 15:52:12 tymorus-desktop kernel: [   18.402076] vga16fb: mapped to 0xffff8800000a0000
May  7 15:52:12 tymorus-desktop kernel: [   18.402186] fb0: VGA16 VGA frame buffer device
May  7 15:52:12 tymorus-desktop kernel: [   19.585105] nvidia: module license 'NVIDIA' taints kernel.
May  7 15:52:12 tymorus-desktop kernel: [   19.585109] Disabling lock debugging due to kernel taint
May  7 15:52:12 tymorus-desktop kernel: [   20.073675] EXT3 FS on sda6, internal journal
May  7 15:52:12 tymorus-desktop kernel: [   20.204103] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [   20.204120] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
May  7 15:52:12 tymorus-desktop kernel: [   20.204724] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
May  7 15:52:12 tymorus-desktop kernel: [   20.221932] lp: driver loaded but no devices found
May  7 15:52:12 tymorus-desktop kernel: [   20.264947] Console: switching to colour frame buffer device 80x30
May  7 15:52:12 tymorus-desktop kernel: [   20.598755] ip_tables: (C) 2000-2006 Netfilter Core Team
May  7 15:52:12 tymorus-desktop kernel: [   20.947725] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
May  7 15:52:12 tymorus-desktop kernel: [   20.948256] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
May  7 15:52:12 tymorus-desktop kernel: [   20.948259] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
May  7 15:52:12 tymorus-desktop kernel: [   20.948260] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
May  7 15:52:12 tymorus-desktop kernel: [   22.247651] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  7 15:52:12 tymorus-desktop kernel: [   22.324676] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  7 15:52:12 tymorus-desktop kernel: [   22.564730] hda_codec: ALC1200: BIOS auto-probing.
May  7 15:52:12 tymorus-desktop kernel: [   22.566481] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
May  7 15:52:12 tymorus-desktop kernel: [   40.021914] kjournald starting.  Commit interval 5 seconds
May  7 15:52:12 tymorus-desktop kernel: [   40.022168] EXT3 FS on sda1, internal journal
May  7 15:52:12 tymorus-desktop kernel: [   40.022176] EXT3-fs: mounted filesystem with ordered data mode.
May  7 15:52:14 tymorus-desktop kernel: [   45.334276] type=1505 audit(1273261934.415:5):  operation="profile_load" pid=1144 name="/usr/share/gdm/guest-session/Xsession"
May  7 15:52:14 tymorus-desktop kernel: [   45.335932] type=1505 audit(1273261934.415:6):  operation="profile_replace" pid=1145 name="/sbin/dhclient3"
May  7 15:52:14 tymorus-desktop kernel: [   45.336558] type=1505 audit(1273261934.415:7):  operation="profile_replace" pid=1145 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  7 15:52:14 tymorus-desktop kernel: [   45.336904] type=1505 audit(1273261934.415:8):  operation="profile_replace" pid=1145 name="/usr/lib/connman/scripts/dhclient-script"
May  7 15:52:14 tymorus-desktop kernel: [   45.388635] type=1505 audit(1273261934.465:9):  operation="profile_load" pid=1146 name="/usr/bin/evince"
May  7 15:52:14 tymorus-desktop kernel: [   45.396630] type=1505 audit(1273261934.475:10):  operation="profile_load" pid=1146 name="/usr/bin/evince-previewer"
May  7 15:52:14 tymorus-desktop kernel: [   45.401861] type=1505 audit(1273261934.484:11):  operation="profile_load" pid=1146 name="/usr/bin/evince-thumbnailer"
May  7 15:52:14 tymorus-desktop kernel: [   45.748736] type=1505 audit(1273261934.824:12):  operation="profile_load" pid=1148 name="/usr/bin/freshclam"
May  7 15:52:14 tymorus-desktop kernel: [   45.811338] type=1505 audit(1273261934.895:13):  operation="profile_load" pid=1149 name="/usr/sbin/clamd"
May  7 15:52:14 tymorus-desktop kernel: [   45.849188] type=1505 audit(1273261934.924:14):  operation="profile_load" pid=1152 name="/usr/lib/cups/backend/cups-pdf"
May  7 15:52:16 tymorus-desktop kernel: [   47.181373] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  7 15:52:16 tymorus-desktop kernel: [   47.190152] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
May  7 15:52:16 tymorus-desktop kernel: [   47.220910] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  7 15:52:19 tymorus-desktop kernel: [   50.030057] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:19 tymorus-desktop kernel: [   50.030075] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:19 tymorus-desktop kernel: [   50.283606] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.283618] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.283636] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.344970] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130
May  7 15:52:19 tymorus-desktop kernel: [   50.344990] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130
May  7 15:52:19 tymorus-desktop kernel: [   50.345028] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130
May  7 15:52:19 tymorus-desktop kernel: [   50.534065] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.534078] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.534104] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.784889] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.784902] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.784927] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:20 tymorus-desktop kernel: [   50.928616] ppdev: user-space parallel port driver
May  7 15:52:20 tymorus-desktop kernel: [   50.985738] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:20 tymorus-desktop kernel: [   50.985750] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:20 tymorus-desktop kernel: [   50.985774] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:20 tymorus-desktop kernel: [   51.571521] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:20 tymorus-desktop kernel: [   51.571534] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:20 tymorus-desktop kernel: [   51.571551] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:21 tymorus-desktop kernel: [   51.990077] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:21 tymorus-desktop kernel: [   51.990095] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:21 tymorus-desktop kernel: [   52.212664] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:21 tymorus-desktop kernel: [   52.212676] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:21 tymorus-desktop kernel: [   52.212701] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:21 tymorus-desktop kernel: [   52.490180] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30343 PROTO=UDP SPT=50583 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.490192] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30343 PROTO=UDP SPT=50583 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.618654] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=126 TOS=0x00 PREC=0x00 TTL=255 ID=52006 DF PROTO=UDP SPT=53 DPT=50583 LEN=106
May  7 15:52:21 tymorus-desktop kernel: [   52.618891] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30344 PROTO=UDP SPT=56434 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.618901] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30344 PROTO=UDP SPT=56434 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.738936] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=126 TOS=0x00 PREC=0x00 TTL=255 ID=52007 DF PROTO=UDP SPT=53 DPT=56434 LEN=106
May  7 15:52:22 tymorus-desktop kernel: [   53.747887] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40910 DF PROTO=UDP SPT=37685 DPT=53 LEN=40
May  7 15:52:22 tymorus-desktop kernel: [   53.747900] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40910 DF PROTO=UDP SPT=37685 DPT=53 LEN=40
May  7 15:52:22 tymorus-desktop kernel: [   53.799758] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:22 tymorus-desktop kernel: [   53.799778] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:22 tymorus-desktop kernel: [   53.799802] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:22 tymorus-desktop kernel: [   53.824897] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=121 TOS=0x00 PREC=0x00 TTL=255 ID=52008 DF PROTO=UDP SPT=53 DPT=37685 LEN=101
May  7 15:52:22 tymorus-desktop kernel: [   53.825044] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40918 DF PROTO=UDP SPT=57530 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.825055] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40918 DF PROTO=UDP SPT=57530 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.852676] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=540 TOS=0x00 PREC=0x00 TTL=255 ID=52009 DF PROTO=UDP SPT=53 DPT=57530 LEN=520
May  7 15:52:22 tymorus-desktop kernel: [   53.852753] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40921 DF PROTO=UDP SPT=55209 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.852769] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40921 DF PROTO=UDP SPT=55209 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.879471] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=540 TOS=0x00 PREC=0x00 TTL=255 ID=52010 DF PROTO=UDP SPT=53 DPT=55209 LEN=520
May  7 15:52:22 tymorus-desktop kernel: [   53.879558] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40923 DF PROTO=UDP SPT=41826 DPT=53 LEN=40
May  7 15:52:22 tymorus-desktop kernel: [   53.879574] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40923 DF PROTO=UDP SPT=41826 DPT=53 LEN=40
May  7 15:52:23 tymorus-desktop kernel: [   53.960786] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=255 ID=52011 DF PROTO=UDP SPT=53 DPT=41826 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.061176] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.061195] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.210678] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.210768] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.360365] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.361278] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:11 tymorus-desktop kernel: [   54.439641] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:11 tymorus-desktop kernel: [   54.439653] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:11 tymorus-desktop kernel: [   54.439681] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:11 tymorus-desktop kernel: [   54.512469] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:11 tymorus-desktop kernel: [   54.516701] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:11 tymorus-desktop kernel: [   54.667852] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:13 tymorus-desktop kernel: [   56.603806] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=142 TOS=0x00 PREC=0x00 TTL=128 ID=3579 PROTO=UDP SPT=17500 DPT=17500 LEN=122
May  7 15:52:18 tymorus-desktop kernel: [   62.192645] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=34118 DF PROTO=TCP SPT=52195 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0
May  7 15:52:18 tymorus-desktop kernel: [   62.192672] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=34118 DF PROTO=TCP SPT=52195 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0
May  7 15:52:18 tymorus-desktop kernel: [   62.192699] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x10 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=4713 DPT=52195 WINDOW=0 RES=0x00 ACK RST URGP=0
May  7 15:52:18 tymorus-desktop kernel: [   62.192711] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x10 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=4713 DPT=52195 WINDOW=0 RES=0x00 ACK RST URGP=0
May  7 15:52:23 tymorus-desktop kernel: [   66.801470] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=42216 DF PROTO=UDP SPT=41319 DPT=53 LEN=48
May  7 15:52:23 tymorus-desktop kernel: [   66.801483] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=42216 DF PROTO=UDP SPT=41319 DPT=53 LEN=48
May  7 15:52:23 tymorus-desktop kernel: [   66.862330] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=52012 DF PROTO=UDP SPT=53 DPT=41319 LEN=99
May  7 15:52:24 tymorus-desktop kernel: [   68.286016] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42364 DF PROTO=UDP SPT=51085 DPT=53 LEN=45
May  7 15:52:24 tymorus-desktop kernel: [   68.286030] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42364 DF PROTO=UDP SPT=51085 DPT=53 LEN=45
May  7 15:52:25 tymorus-desktop kernel: [   68.378045] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=81 TOS=0x00 PREC=0x00 TTL=255 ID=52013 DF PROTO=UDP SPT=53 DPT=51085 LEN=61
May  7 15:52:25 tymorus-desktop kernel: [   68.378227] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=9343 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.378240] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=9343 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.495789] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=64 TOS=0x00 PREC=0x00 TTL=244 ID=31728 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4356 RES=0x00 ACK SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.495831] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9344 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=46 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.495887] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=129 TOS=0x00 PREC=0x00 TTL=64 ID=9345 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=46 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616024] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=219 TOS=0x00 PREC=0x00 TTL=244 ID=33818 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616057] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=33821 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616108] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9346 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=54 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616153] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9347 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=54 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616287] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42397 DF PROTO=UDP SPT=36488 DPT=53 LEN=45
May  7 15:52:25 tymorus-desktop kernel: [   68.616297] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42397 DF PROTO=UDP SPT=36488 DPT=53 LEN=45
May  7 15:52:25 tymorus-desktop kernel: [   68.693285] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=81 TOS=0x00 PREC=0x00 TTL=255 ID=52014 DF PROTO=UDP SPT=53 DPT=36488 LEN=61
May  7 15:52:25 tymorus-desktop kernel: [   68.693401] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25793 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.693413] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25793 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.732276] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=35887 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.811081] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=64 TOS=0x00 PREC=0x00 TTL=244 ID=37256 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4356 RES=0x00 ACK SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.811123] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25794 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=46 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.811187] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=324 TOS=0x00 PREC=0x00 TTL=64 ID=25795 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=46 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957049] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=296 TOS=0x00 PREC=0x00 TTL=244 ID=39779 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957103] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=39781 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957136] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25796 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=54 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957194] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25797 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=54 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   69.073203] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=41921 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK URGP=0
May  7 15:52:28 tymorus-desktop kernel: [   71.412904] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3593 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:28 tymorus-desktop kernel: [   71.677017] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3594 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:28 tymorus-desktop kernel: [   72.175650] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3595 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:29 tymorus-desktop kernel: [   72.439735] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3597 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:29 tymorus-desktop kernel: [   72.938969] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3598 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:29 tymorus-desktop kernel: [   73.204356] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3599 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:30 tymorus-desktop kernel: [   74.298542] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3603 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:31 tymorus-desktop kernel: [   75.061061] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3604 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:32 tymorus-desktop kernel: [   75.825769] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3605 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:33 tymorus-desktop kernel: [   76.919291] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3610 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:34 tymorus-desktop kernel: [   77.682176] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3611 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:35 tymorus-desktop kernel: [   78.446679] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3612 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:36 tymorus-desktop kernel: [   79.480124] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e23a20
May  7 15:52:36 tymorus-desktop kernel: [   79.480141] vboxdrv: fAsync=0 offMin=0x160 offMax=0x84b
May  7 15:52:36 tymorus-desktop kernel: [   79.480800] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May  7 15:52:36 tymorus-desktop kernel: [   79.538029] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=43489 DF PROTO=UDP SPT=56728 DPT=53 LEN=50
May  7 15:52:36 tymorus-desktop kernel: [   79.538041] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=43489 DF PROTO=UDP SPT=56728 DPT=53 LEN=50
May  7 15:52:36 tymorus-desktop kernel: [   79.539215] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3616 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:36 tymorus-desktop kernel: [   79.746142] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=52015 DF PROTO=UDP SPT=53 DPT=56728 LEN=66
May  7 15:52:36 tymorus-desktop kernel: [   80.302070] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3617 PROTO=UDP SPT=137 DPT=137 LEN=58

```

---

### Post by Tymorus on 2010-05-12
[SIZE=4]Ufw.log[/SIZE]
```

May  7 15:52:19 tymorus-desktop kernel: [   50.030057] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:19 tymorus-desktop kernel: [   50.030075] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:19 tymorus-desktop kernel: [   50.283606] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.283618] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.283636] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.344970] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130
May  7 15:52:19 tymorus-desktop kernel: [   50.344990] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130
May  7 15:52:19 tymorus-desktop kernel: [   50.345028] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=150 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=130
May  7 15:52:19 tymorus-desktop kernel: [   50.534065] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.534078] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.534104] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.784889] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.784902] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:19 tymorus-desktop kernel: [   50.784927] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=362 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=342
May  7 15:52:20 tymorus-desktop kernel: [   50.985738] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:20 tymorus-desktop kernel: [   50.985750] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:20 tymorus-desktop kernel: [   50.985774] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:20 tymorus-desktop kernel: [   51.571521] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:20 tymorus-desktop kernel: [   51.571534] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:20 tymorus-desktop kernel: [   51.571551] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:21 tymorus-desktop kernel: [   51.990077] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:21 tymorus-desktop kernel: [   51.990095] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
May  7 15:52:21 tymorus-desktop kernel: [   52.212664] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:21 tymorus-desktop kernel: [   52.212676] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:21 tymorus-desktop kernel: [   52.212701] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:21 tymorus-desktop kernel: [   52.490180] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30343 PROTO=UDP SPT=50583 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.490192] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30343 PROTO=UDP SPT=50583 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.618654] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=126 TOS=0x00 PREC=0x00 TTL=255 ID=52006 DF PROTO=UDP SPT=53 DPT=50583 LEN=106
May  7 15:52:21 tymorus-desktop kernel: [   52.618891] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30344 PROTO=UDP SPT=56434 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.618901] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=30344 PROTO=UDP SPT=56434 DPT=53 LEN=31
May  7 15:52:21 tymorus-desktop kernel: [   52.738936] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=126 TOS=0x00 PREC=0x00 TTL=255 ID=52007 DF PROTO=UDP SPT=53 DPT=56434 LEN=106
May  7 15:52:22 tymorus-desktop kernel: [   53.747887] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40910 DF PROTO=UDP SPT=37685 DPT=53 LEN=40
May  7 15:52:22 tymorus-desktop kernel: [   53.747900] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40910 DF PROTO=UDP SPT=37685 DPT=53 LEN=40
May  7 15:52:22 tymorus-desktop kernel: [   53.799758] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:22 tymorus-desktop kernel: [   53.799778] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:22 tymorus-desktop kernel: [   53.799802] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=243 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=223
May  7 15:52:22 tymorus-desktop kernel: [   53.824897] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=121 TOS=0x00 PREC=0x00 TTL=255 ID=52008 DF PROTO=UDP SPT=53 DPT=37685 LEN=101
May  7 15:52:22 tymorus-desktop kernel: [   53.825044] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40918 DF PROTO=UDP SPT=57530 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.825055] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40918 DF PROTO=UDP SPT=57530 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.852676] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=540 TOS=0x00 PREC=0x00 TTL=255 ID=52009 DF PROTO=UDP SPT=53 DPT=57530 LEN=520
May  7 15:52:22 tymorus-desktop kernel: [   53.852753] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40921 DF PROTO=UDP SPT=55209 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.852769] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40921 DF PROTO=UDP SPT=55209 DPT=53 LEN=58
May  7 15:52:22 tymorus-desktop kernel: [   53.879471] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=540 TOS=0x00 PREC=0x00 TTL=255 ID=52010 DF PROTO=UDP SPT=53 DPT=55209 LEN=520
May  7 15:52:22 tymorus-desktop kernel: [   53.879558] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40923 DF PROTO=UDP SPT=41826 DPT=53 LEN=40
May  7 15:52:22 tymorus-desktop kernel: [   53.879574] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40923 DF PROTO=UDP SPT=41826 DPT=53 LEN=40
May  7 15:52:23 tymorus-desktop kernel: [   53.960786] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=255 ID=52011 DF PROTO=UDP SPT=53 DPT=41826 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.061176] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.061195] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.210678] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.210768] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.360365] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:23 tymorus-desktop kernel: [   54.361278] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:11 tymorus-desktop kernel: [   54.439641] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:11 tymorus-desktop kernel: [   54.439653] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:11 tymorus-desktop kernel: [   54.439681] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.79 DST=224.0.0.251 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=318
May  7 15:52:11 tymorus-desktop kernel: [   54.512469] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:11 tymorus-desktop kernel: [   54.516701] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:11 tymorus-desktop kernel: [   54.667852] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=91.189.94.4 DST=192.168.1.79 LEN=76 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56
May  7 15:52:13 tymorus-desktop kernel: [   56.603806] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=142 TOS=0x00 PREC=0x00 TTL=128 ID=3579 PROTO=UDP SPT=17500 DPT=17500 LEN=122
May  7 15:52:18 tymorus-desktop kernel: [   62.192645] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=34118 DF PROTO=TCP SPT=52195 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0
May  7 15:52:18 tymorus-desktop kernel: [   62.192672] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x10 PREC=0x00 TTL=64 ID=34118 DF PROTO=TCP SPT=52195 DPT=4713 WINDOW=32792 RES=0x00 SYN URGP=0
May  7 15:52:18 tymorus-desktop kernel: [   62.192699] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x10 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=4713 DPT=52195 WINDOW=0 RES=0x00 ACK RST URGP=0
May  7 15:52:18 tymorus-desktop kernel: [   62.192711] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x10 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=4713 DPT=52195 WINDOW=0 RES=0x00 ACK RST URGP=0
May  7 15:52:23 tymorus-desktop kernel: [   66.801470] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=42216 DF PROTO=UDP SPT=41319 DPT=53 LEN=48
May  7 15:52:23 tymorus-desktop kernel: [   66.801483] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=68 TOS=0x00 PREC=0x00 TTL=64 ID=42216 DF PROTO=UDP SPT=41319 DPT=53 LEN=48
May  7 15:52:23 tymorus-desktop kernel: [   66.862330] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=119 TOS=0x00 PREC=0x00 TTL=255 ID=52012 DF PROTO=UDP SPT=53 DPT=41319 LEN=99
May  7 15:52:24 tymorus-desktop kernel: [   68.286016] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42364 DF PROTO=UDP SPT=51085 DPT=53 LEN=45
May  7 15:52:24 tymorus-desktop kernel: [   68.286030] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42364 DF PROTO=UDP SPT=51085 DPT=53 LEN=45
May  7 15:52:25 tymorus-desktop kernel: [   68.378045] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=81 TOS=0x00 PREC=0x00 TTL=255 ID=52013 DF PROTO=UDP SPT=53 DPT=51085 LEN=61
May  7 15:52:25 tymorus-desktop kernel: [   68.378227] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=9343 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.378240] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=9343 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.495789] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=64 TOS=0x00 PREC=0x00 TTL=244 ID=31728 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4356 RES=0x00 ACK SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.495831] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9344 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=46 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.495887] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=129 TOS=0x00 PREC=0x00 TTL=64 ID=9345 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=46 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616024] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=219 TOS=0x00 PREC=0x00 TTL=244 ID=33818 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616057] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=33821 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616108] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9346 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=54 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616153] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=9347 DF PROTO=TCP SPT=59336 DPT=8245 WINDOW=54 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.616287] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42397 DF PROTO=UDP SPT=36488 DPT=53 LEN=45
May  7 15:52:25 tymorus-desktop kernel: [   68.616297] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=192.168.1.254 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=42397 DF PROTO=UDP SPT=36488 DPT=53 LEN=45
May  7 15:52:25 tymorus-desktop kernel: [   68.693285] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=192.168.1.254 DST=192.168.1.79 LEN=81 TOS=0x00 PREC=0x00 TTL=255 ID=52014 DF PROTO=UDP SPT=53 DPT=36488 LEN=61
May  7 15:52:25 tymorus-desktop kernel: [   68.693401] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25793 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.693413] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25793 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=5840 RES=0x00 SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.732276] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=35887 DF PROTO=TCP SPT=8245 DPT=59336 WINDOW=4433 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.811081] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=64 TOS=0x00 PREC=0x00 TTL=244 ID=37256 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4356 RES=0x00 ACK SYN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.811123] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25794 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=46 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.811187] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=324 TOS=0x00 PREC=0x00 TTL=64 ID=25795 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=46 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957049] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=296 TOS=0x00 PREC=0x00 TTL=244 ID=39779 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK PSH URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957103] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=39781 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957136] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25796 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=54 RES=0x00 ACK URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   68.957194] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.79 DST=204.16.252.79 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=25797 DF PROTO=TCP SPT=59337 DPT=8245 WINDOW=54 RES=0x00 ACK FIN URGP=0
May  7 15:52:25 tymorus-desktop kernel: [   69.073203] [UFW AUDIT] IN=eth0 OUT= MAC=00:1e:8c:2a:16:1e:00:24:56:00:a0:99:08:00 SRC=204.16.252.79 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=244 ID=41921 DF PROTO=TCP SPT=8245 DPT=59337 WINDOW=4628 RES=0x00 ACK URGP=0
May  7 15:52:28 tymorus-desktop kernel: [   71.412904] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3593 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:28 tymorus-desktop kernel: [   71.677017] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3594 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:28 tymorus-desktop kernel: [   72.175650] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3595 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:29 tymorus-desktop kernel: [   72.439735] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3597 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:29 tymorus-desktop kernel: [   72.938969] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3598 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:29 tymorus-desktop kernel: [   73.204356] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3599 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:30 tymorus-desktop kernel: [   74.298542] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3603 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:31 tymorus-desktop kernel: [   75.061061] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3604 PROTO=UDP SPT=137 DPT=137 LEN=58
May  7 15:52:32 tymorus-desktop kernel: [   75.825769] [UFW AUDIT] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:23:4e:43:6c:bb:08:00 SRC=192.168.1.107 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3605 PROTO=UDP SPT=137 DPT=137 LEN=58

```

---

### Post by john newbuntu on 2010-05-13
This could be a "ufw" configuration issue.  I'm guessing that the level of logging is either at high or full. I'd suggest looking at /etc/ufw/ufw.conf for LOGLEVEL parameter.  If you see this to be anything other than "low" or "off", you might want to reset this to "low" by using the following command from a terminal:
```
sudo ufw logging low
```If you are not a terminal person, install gufw (sudo apt-get install gufw). Then go to system->admin->firewall config.  Then to edit->pref and set level to low.

---

### Post by Tymorus on 2010-05-13
I set the logging to low and I noticed it still produced an undesirable amount of lines in my logs, so I just turned it off.  Thanks for the help.

---

