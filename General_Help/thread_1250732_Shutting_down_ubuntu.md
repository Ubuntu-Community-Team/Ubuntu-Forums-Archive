---
title: "Shutting down ubuntu"
date: 2009-08-26
forum: General Help
---

### Post by madarieder on 2009-08-26
when I attempt to shut it down, the whole ubuntu screen runs through smoothly, but then it turns to a black screen and a white blinking light. 

I am dual booting xp and ubuntu. XP shuts down just fine. Help?

---

### Post by P4man on 2009-08-27
You are running 9.10 alpha4 right ? Always a good idea to mention that ;)

Have a look in the log files if you see anything that might give an indication. System > adminstration > log file viewer. Find the last entries before the failed shut down and post them here.

---

### Post by wojox on 2009-08-27
What has the world come to when the children of today describe the cursor as a white blinking light?

---

### Post by madarieder on 2009-08-27
> **wojox said:**
> What has the world come to when the children of today describe the cursor as a white blinking light?

Because, it isn't a cursor. its a hyphen. - <------

---

### Post by madarieder on 2009-08-27
> **P4man said:**
> You are running 9.10 alpha4 right ? Always a good idea to mention that ;)

Have a look in the log files if you see anything that might give an indication. System > adminstration > log file viewer. Find the last entries before the failed shut down and post them here.

under what section would that be?

---

### Post by P4man on 2009-08-27
just look in "messages". You'll see date time on the left, shouldnt be hard to scroll back to the moment you shut it down.

---

### Post by madarieder on 2009-08-27
> Aug 27 10:40:45 adam-laptop kernel: [   12.009896] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
Aug 27 10:40:45 adam-laptop kernel: [   12.010103] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Aug 27 10:40:45 adam-laptop kernel: [   12.492464] Registered led device: ath9k-phy0::radio
Aug 27 10:40:45 adam-laptop kernel: [   12.492505] Registered led device: ath9k-phy0::assoc
Aug 27 10:40:45 adam-laptop kernel: [   12.492544] Registered led device: ath9k-phy0::tx
Aug 27 10:40:45 adam-laptop kernel: [   12.492582] Registered led device: ath9k-phy0::rx
Aug 27 10:40:45 adam-laptop kernel: [   12.492622] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8aa0000, irq=17
Aug 27 10:40:45 adam-laptop kernel: [   13.490110] lp: driver loaded but no devices found
Aug 27 10:40:45 adam-laptop kernel: [   14.283822] Adding 1164672k swap on /dev/sda6.  Priority:-1 extents:1 across:1164672k 
Aug 27 10:40:45 adam-laptop kernel: [   15.068002] EXT4-fs (sda5): internal journal on sda5:8
Aug 27 10:40:45 adam-laptop kernel: [   16.731012] type=1505 audit(1251387643.029:2): operation="profile_load" pid=1847 name=/usr/share/gdm/guest-session/Xsession
Aug 27 10:40:45 adam-laptop kernel: [   16.750837] type=1505 audit(1251387643.047:3): operation="profile_load" pid=1848 name=/sbin/dhclient3
Aug 27 10:40:45 adam-laptop kernel: [   16.751541] type=1505 audit(1251387643.047:4): operation="profile_load" pid=1848 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Aug 27 10:40:45 adam-laptop kernel: [   16.751857] type=1505 audit(1251387643.047:5): operation="profile_load" pid=1848 name=/usr/lib/connman/scripts/dhclient-script
Aug 27 10:40:45 adam-laptop kernel: [   16.768971] type=1505 audit(1251387643.067:6): operation="profile_load" pid=1849 name=/usr/sbin/tcpdump
Aug 27 10:40:45 adam-laptop kernel: [   16.779960] type=1505 audit(1251387643.075:7): operation="profile_load" pid=1850 name=/usr/lib/cups/backend/cups-pdf
Aug 27 10:40:45 adam-laptop kernel: [   16.780670] type=1505 audit(1251387643.079:8): operation="profile_load" pid=1850 name=/usr/sbin/cupsd
Aug 27 10:40:45 adam-laptop kernel: [   16.817222] type=1505 audit(1251387643.115:9): operation="profile_load" pid=1851 name=/usr/bin/evince
Aug 27 10:40:45 adam-laptop kernel: [   16.823602] type=1505 audit(1251387643.119:10): operation="profile_load" pid=1851 name=/usr/bin/evince-previewer
Aug 27 10:40:45 adam-laptop kernel: [   16.827612] type=1505 audit(1251387643.123:11): operation="profile_load" pid=1851 name=/usr/bin/evince-thumbnailer
Aug 27 10:40:49 adam-laptop kernel: [   22.929887] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 27 10:40:49 adam-laptop kernel: [   22.976865] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 27 10:40:49 adam-laptop kernel: [   23.120073] ppdev: user-space parallel port driver
Aug 27 10:40:52 adam-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="2072" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 27 12:27:02 adam-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.



is that what you're looking for?

---

### Post by P4man on 2009-08-27
Not much in there. Can you check syslog ?  For refence here is what it gives on my system just before powering down:
> 
Aug 27 19:48:50 bob-desktop console-kit-daemon[3183]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Aug 27 19:48:50 bob-desktop init: tty2 main process (2308) killed by TERM signal
Aug 27 19:48:50 bob-desktop init: tty4 main process (2302) killed by TERM signal
Aug 27 19:48:50 bob-desktop init: tty5 main process (2303) killed by TERM signal
Aug 27 19:48:50 bob-desktop init: tty3 main process (2309) killed by TERM signal
Aug 27 19:48:50 bob-desktop init: tty6 main process (2310) killed by TERM signal
Aug 27 19:48:50 bob-desktop init: tty1 main process (3849) killed by TERM signal
Aug 27 19:48:52 bob-desktop lircd-0.8.4a[2541]: caught signal
Aug 27 19:48:55 bob-desktop nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_76_62_6e_65_74)
Aug 27 19:49:00 bob-desktop exiting on signal 15

<here it powers off>

Aug 27 19:50:21 bob-desktop syslogd 1.5.0#5ubuntu3: restart.

---

### Post by madarieder on 2009-08-27
> **P4man said:**
> Not much in there. Can you check syslog ?  For refence here is what it gives on my system just before powering down:

I checked. It only shows startup, nothing about shutting down.

---

### Post by P4man on 2009-08-27
Can you post it anyway? There must be something in there :)

---

### Post by madarieder on 2009-08-27
```
Aug 27 13:03:39 adam-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Aug 27 13:03:39 adam-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="2009" x-info="http://www.rsyslog.com"] (re)start
Aug 27 13:03:39 adam-laptop rsyslogd: rsyslogd's groupid changed to 102
Aug 27 13:03:39 adam-laptop rsyslogd: rsyslogd's userid changed to 101
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Linux version 2.6.31-7-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-3ubuntu1) ) #27-Ubuntu SMP Mon Aug 24 17:33:49 UTC 2009 (Ubuntu 2.6.31-7.27-generic)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] KERNEL supported cpus:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Intel GenuineIntel
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   AMD AuthenticAMD
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   NSC Geode by NSC
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Centaur CentaurHauls
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7a0000 (usable)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 000000003f7ae000 - 000000003f7f0000 (ACPI NVS)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] DMI present.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] last_pfn = 0x3f7a0 max_arch_pfn = 0x100000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] MTRR default type: uncachable
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   00000-9FFFF write-back
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   A0000-DFFFF uncachable
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   E0000-EFFFF write-through
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   F0000-FFFFF write-protect
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   0 base 000000000 mask 0C0000000 write-back
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   1 base 03F800000 mask 0FF800000 uncachable
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   2 disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   3 disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   4 disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   5 disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   6 disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   7 disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] modified physical RAM map:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000003f7a0000 (usable)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 000000003f7ae000 - 000000003f7f0000 (ACPI NVS)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 000000003f7f0000 - 000000003f800000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] RAMDISK: 2f313000 - 2f9f7a9b
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: RSDP 000fb9e0 00014 (v00 ACPIAM)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: RSDT 3f7a0000 0003C (v01 A_M_I_ OEMRSDT  07000924 MSFT 00000097)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: FACP 3f7a0200 00084 (v02 A_M_I_ OEMFACP  07000924 MSFT 00000097)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: DSDT 3f7a0430 06A52 (v01  A1311 A1311000 00000000 INTL 20051117)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: FACS 3f7ae000 00040
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: APIC 3f7a0390 0005C (v01 A_M_I_ OEMAPIC  07000924 MSFT 00000097)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: MCFG 3f7a03f0 0003C (v01 A_M_I_ OEMMCFG  07000924 MSFT 00000097)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: OEMB 3f7ae040 00061 (v01 A_M_I_ AMI_OEM  07000924 MSFT 00000097)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: HPET 3f7a6e90 00038 (v01 A_M_I_ OEMHPET  07000924 MSFT 00000097)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: SSDT 3f7aeb80 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] 127MB HIGHMEM available.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] 887MB LOWMEM available.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #3 [0000100000 - 000089b040]    TEXT DATA BSS ==> [0000100000 - 000089b040]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #4 [002f313000 - 002f9f7a9b]          RAMDISK ==> [002f313000 - 002f9f7a9b]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #6 [000089c000 - 000089f1f8]              BRK ==> [000089c000 - 000089f1f8]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Zone PFN ranges:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f7a0
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0003f7a0
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] On node 0 totalpages: 259887
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c0771060, node_mem_map c1000200
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   HighMem zone: 256 pages used for memmap
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]   HighMem zone: 32418 pages, LIFO batch:7
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Using APIC driver default
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35036 bytes
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257855
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-7-generic root=UUID=60b89cbf-0353-4687-ad41-c5e02215cfd7 ro quiet splash
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Initializing CPU#0
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] allocated 5199680 bytes of page_cgroup
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f7a0)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Memory: 1010060k/1040000k available (4539k kernel code, 29016k reserved, 2111k data, 536k init, 130696k highmem)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] virtual kernel memory layout:
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]       .init : 0xc0787000 - 0xc080d000   ( 536 kB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]       .data : 0xc056ec04 - 0xc077e928   (2111 kB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc056ec04   (4539 kB)
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Aug 27 13:03:39 adam-laptop kernel: [    0.000000] Detected 1599.901 MHz processor.
Aug 27 13:03:39 adam-laptop kernel: [    0.001761] Console: colour VGA+ 80x25
Aug 27 13:03:39 adam-laptop kernel: [    0.001768] console [tty0] enabled
Aug 27 13:03:39 adam-laptop kernel: [    0.002007] hpet clockevent registered
Aug 27 13:03:39 adam-laptop kernel: [    0.002017] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug 27 13:03:39 adam-laptop kernel: [    0.002028] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.80 BogoMIPS (lpj=6399604)
Aug 27 13:03:39 adam-laptop kernel: [    0.002065] Security Framework initialized
Aug 27 13:03:39 adam-laptop kernel: [    0.002104] AppArmor: AppArmor initialized
Aug 27 13:03:39 adam-laptop kernel: [    0.002119] Mount-cache hash table entries: 512
Aug 27 13:03:39 adam-laptop kernel: [    0.002347] Initializing cgroup subsys ns
Aug 27 13:03:39 adam-laptop kernel: [    0.002357] Initializing cgroup subsys cpuacct
Aug 27 13:03:39 adam-laptop kernel: [    0.002365] Initializing cgroup subsys memory
Aug 27 13:03:39 adam-laptop kernel: [    0.002377] Initializing cgroup subsys freezer
Aug 27 13:03:39 adam-laptop kernel: [    0.002382] Initializing cgroup subsys net_cls
Aug 27 13:03:39 adam-laptop kernel: [    0.002407] CPU: L1 I cache: 32K, L1 D cache: 24K
Aug 27 13:03:39 adam-laptop kernel: [    0.002413] CPU: L2 cache: 512K
Aug 27 13:03:39 adam-laptop kernel: [    0.002418] CPU: Physical Processor ID: 0
Aug 27 13:03:39 adam-laptop kernel: [    0.002422] CPU: Processor Core ID: 0
Aug 27 13:03:39 adam-laptop kernel: [    0.002428] using mwait in idle threads.
Aug 27 13:03:39 adam-laptop kernel: [    0.002439] Performance Counters: Atom events, Intel PMU driver.
Aug 27 13:03:39 adam-laptop kernel: [    0.002454] ... version:                 3
Aug 27 13:03:39 adam-laptop kernel: [    0.002458] ... bit width:               40
Aug 27 13:03:39 adam-laptop kernel: [    0.002462] ... generic counters:        2
Aug 27 13:03:39 adam-laptop kernel: [    0.002466] ... value mask:              000000ffffffffff
Aug 27 13:03:39 adam-laptop kernel: [    0.002471] ... max period:              000000007fffffff
Aug 27 13:03:39 adam-laptop kernel: [    0.002476] ... fixed-purpose counters:  3
Aug 27 13:03:39 adam-laptop kernel: [    0.002480] ... counter mask:            0000000700000003
Aug 27 13:03:39 adam-laptop kernel: [    0.002488] Checking 'hlt' instruction... OK.
Aug 27 13:03:39 adam-laptop kernel: [    0.019969] ACPI: Core revision 20090521
Aug 27 13:03:39 adam-laptop kernel: [    0.036505] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 27 13:03:39 adam-laptop kernel: [    0.076581] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Aug 27 13:03:39 adam-laptop kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Aug 27 13:03:39 adam-laptop kernel: [    0.004000] Initializing CPU#1
Aug 27 13:03:39 adam-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3199.61 BogoMIPS (lpj=6399229)
Aug 27 13:03:39 adam-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
Aug 27 13:03:39 adam-laptop kernel: [    0.004000] CPU: L2 cache: 512K
Aug 27 13:03:39 adam-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Aug 27 13:03:39 adam-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
Aug 27 13:03:39 adam-laptop kernel: [    0.164281] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Aug 27 13:03:39 adam-laptop kernel: [    0.164315] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 27 13:03:39 adam-laptop kernel: [    0.168051] Brought up 2 CPUs
Aug 27 13:03:39 adam-laptop kernel: [    0.168060] Total of 2 processors activated (6399.41 BogoMIPS).
Aug 27 13:03:39 adam-laptop kernel: [    0.168128] CPU0 attaching sched-domain:
Aug 27 13:03:39 adam-laptop kernel: [    0.168135]  domain 0: span 0-1 level SIBLING
Aug 27 13:03:39 adam-laptop kernel: [    0.168141]   groups: 0 1
Aug 27 13:03:39 adam-laptop kernel: [    0.168151] CPU1 attaching sched-domain:
Aug 27 13:03:39 adam-laptop kernel: [    0.168156]  domain 0: span 0-1 level SIBLING
Aug 27 13:03:39 adam-laptop kernel: [    0.168161]   groups: 1 0
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] Booting paravirtualized kernel on bare hardware
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] regulator: core version 0.5
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] Time: 13:03:21  Date: 08/27/09
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] NET: Registered protocol family 16
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] EISA bus registered
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] ACPI: bus type pci registered
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Aug 27 13:03:39 adam-laptop kernel: [    0.168522] PCI: Not using MMCONFIG.
Aug 27 13:03:39 adam-laptop kernel: [    0.172013] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Aug 27 13:03:39 adam-laptop kernel: [    0.172018] PCI: Using configuration type 1 for base access
Aug 27 13:03:39 adam-laptop kernel: [    0.184098] bio: create slab <bio-0> at 0
Aug 27 13:03:39 adam-laptop kernel: [    0.185761] ACPI: EC: Look up EC in DSDT
Aug 27 13:03:39 adam-laptop kernel: [    0.200035] ACPI: Interpreter enabled
Aug 27 13:03:39 adam-laptop kernel: [    0.200051] ACPI: (supports S0 S1 S3 S4 S5)
Aug 27 13:03:39 adam-laptop kernel: [    0.200113] ACPI: Using IOAPIC for interrupt routing
Aug 27 13:03:39 adam-laptop kernel: [    0.200221] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Aug 27 13:03:39 adam-laptop kernel: [    0.204083] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Aug 27 13:03:39 adam-laptop kernel: [    0.204091] PCI: Using MMCONFIG for extended config space
Aug 27 13:03:39 adam-laptop kernel: [    0.216336] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Aug 27 13:03:39 adam-laptop kernel: [    0.216343] ACPI: EC: driver started in poll mode
Aug 27 13:03:39 adam-laptop kernel: [    0.216424] ACPI: No dock devices found.
Aug 27 13:03:39 adam-laptop kernel: [    0.216636] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 27 13:03:39 adam-laptop kernel: [    0.216758] pci 0000:00:02.0: reg 10 32bit mmio: [0xf7e00000-0xf7e7ffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.216758] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
Aug 27 13:03:39 adam-laptop kernel: [    0.216758] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.216758] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf7dc0000-0xf7dfffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.216758] pci 0000:00:02.1: reg 10 32bit mmio: [0xf7e80000-0xf7efffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.220046] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7db8000-0xf7dbbfff]
Aug 27 13:03:39 adam-laptop kernel: [    0.220124] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.220133] pci 0000:00:1b.0: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.220244] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.220252] pci 0000:00:1c.0: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.220365] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.220373] pci 0000:00:1c.1: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.220489] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.220497] pci 0000:00:1c.3: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.220583] pci 0000:00:1d.0: reg 20 io port: [0xd400-0xd41f]
Aug 27 13:03:39 adam-laptop kernel: [    0.220668] pci 0000:00:1d.1: reg 20 io port: [0xd480-0xd49f]
Aug 27 13:03:39 adam-laptop kernel: [    0.220753] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
Aug 27 13:03:39 adam-laptop kernel: [    0.220838] pci 0000:00:1d.3: reg 20 io port: [0xd880-0xd89f]
Aug 27 13:03:39 adam-laptop kernel: [    0.220927] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf7db7c00-0xf7db7fff]
Aug 27 13:03:39 adam-laptop kernel: [    0.221007] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.221015] pci 0000:00:1d.7: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.221214] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Aug 27 13:03:39 adam-laptop kernel: [    0.221223] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Aug 27 13:03:39 adam-laptop kernel: [    0.221231] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0380 (mask 0003)
Aug 27 13:03:39 adam-laptop kernel: [    0.221240] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
Aug 27 13:03:39 adam-laptop kernel: [    0.221248] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
Aug 27 13:03:39 adam-laptop kernel: [    0.221314] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Aug 27 13:03:39 adam-laptop kernel: [    0.221327] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Aug 27 13:03:39 adam-laptop kernel: [    0.221340] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
Aug 27 13:03:39 adam-laptop kernel: [    0.221353] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
Aug 27 13:03:39 adam-laptop kernel: [    0.221366] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
Aug 27 13:03:39 adam-laptop kernel: [    0.221450] pci 0000:00:1f.2: reg 10 io port: [0xd080-0xd087]
Aug 27 13:03:39 adam-laptop kernel: [    0.221463] pci 0000:00:1f.2: reg 14 io port: [0xd000-0xd003]
Aug 27 13:03:39 adam-laptop kernel: [    0.221475] pci 0000:00:1f.2: reg 18 io port: [0xcc00-0xcc07]
Aug 27 13:03:39 adam-laptop kernel: [    0.221488] pci 0000:00:1f.2: reg 1c io port: [0xc880-0xc883]
Aug 27 13:03:39 adam-laptop kernel: [    0.221501] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc80f]
Aug 27 13:03:39 adam-laptop kernel: [    0.221514] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf7db7800-0xf7db7bff]
Aug 27 13:03:39 adam-laptop kernel: [    0.221561] pci 0000:00:1f.2: PME# supported from D3hot
Aug 27 13:03:39 adam-laptop kernel: [    0.221569] pci 0000:00:1f.2: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.221760] pci 0000:02:00.0: reg 10 64bit mmio: [0xfbff0000-0xfbffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.221859] pci 0000:02:00.0: supports D1
Aug 27 13:03:39 adam-laptop kernel: [    0.221864] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.221873] pci 0000:02:00.0: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.221975] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xfbffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.221989] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf0000000-0xf6ffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.222076] pci 0000:01:00.0: reg 10 64bit mmio: [0xf7fc0000-0xf7ffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.222092] pci 0000:01:00.0: reg 18 io port: [0xec00-0xec7f]
Aug 27 13:03:39 adam-laptop kernel: [    0.222186] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 27 13:03:39 adam-laptop kernel: [    0.222196] pci 0000:01:00.0: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.222288] pci 0000:00:1c.3: bridge io port: [0xe000-0xefff]
Aug 27 13:03:39 adam-laptop kernel: [    0.222297] pci 0000:00:1c.3: bridge 32bit mmio: [0xf7f00000-0xf7ffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.222379] pci 0000:00:1e.0: transparent bridge
Aug 27 13:03:39 adam-laptop kernel: [    0.222427] pci_bus 0000:00: on NUMA node 0
Aug 27 13:03:39 adam-laptop kernel: [    0.222444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 27 13:03:39 adam-laptop kernel: [    0.222795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
Aug 27 13:03:39 adam-laptop kernel: [    0.222894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Aug 27 13:03:39 adam-laptop kernel: [    0.245421] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Aug 27 13:03:39 adam-laptop kernel: [    0.245421] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Aug 27 13:03:39 adam-laptop kernel: [    0.245421] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Aug 27 13:03:39 adam-laptop kernel: [    0.248028] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Aug 27 13:03:39 adam-laptop kernel: [    0.248269] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Aug 27 13:03:39 adam-laptop kernel: [    0.248512] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Aug 27 13:03:39 adam-laptop kernel: [    0.248753] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Aug 27 13:03:39 adam-laptop kernel: [    0.248993] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Aug 27 13:03:39 adam-laptop kernel: [    0.249531] SCSI subsystem initialized
Aug 27 13:03:39 adam-laptop kernel: [    0.249531] libata version 3.00 loaded.
Aug 27 13:03:39 adam-laptop kernel: [    0.249531] usbcore: registered new interface driver usbfs
Aug 27 13:03:39 adam-laptop kernel: [    0.249531] usbcore: registered new interface driver hub
Aug 27 13:03:39 adam-laptop kernel: [    0.249531] usbcore: registered new device driver usb
Aug 27 13:03:39 adam-laptop kernel: [    0.252113] ACPI: WMI: Mapper loaded
Aug 27 13:03:39 adam-laptop kernel: [    0.252113] PCI: Using ACPI for IRQ routing
Aug 27 13:03:39 adam-laptop kernel: [    0.272023] Bluetooth: Core ver 2.15
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] NET: Registered protocol family 31
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] Bluetooth: HCI device and connection manager initialized
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] Bluetooth: HCI socket layer initialized
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] NetLabel: Initializing
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] NetLabel:  domain hash size = 128
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] NetLabel:  unlabeled traffic allowed by default
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 27 13:03:39 adam-laptop kernel: [    0.272424] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug 27 13:03:39 adam-laptop kernel: [    0.296368] pnp: PnP ACPI init
Aug 27 13:03:39 adam-laptop kernel: [    0.296410] ACPI: bus type pnp registered
Aug 27 13:03:39 adam-laptop kernel: [    0.301524] pnp: PnP ACPI: found 13 devices
Aug 27 13:03:39 adam-laptop kernel: [    0.301531] ACPI: ACPI bus type pnp unregistered
Aug 27 13:03:39 adam-laptop kernel: [    0.301539] PnPBIOS: Disabled by ACPI PNP
Aug 27 13:03:39 adam-laptop kernel: [    0.301568] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301589] system 00:08: ioport range 0x25c-0x25f has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301597] system 00:08: ioport range 0x380-0x383 has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301604] system 00:08: ioport range 0x400-0x41f has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301611] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301618] system 00:08: ioport range 0x800-0x87f has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301625] system 00:08: ioport range 0x480-0x4bf has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301633] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301641] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301648] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301656] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301663] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301671] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301686] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301693] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301706] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301721] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301728] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301735] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.301742] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
Aug 27 13:03:39 adam-laptop kernel: [    0.337463] AppArmor: AppArmor Filesystem Enabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337550] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
Aug 27 13:03:39 adam-laptop kernel: [    0.337556] pci 0000:00:1c.0:   IO window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337565] pci 0000:00:1c.0:   MEM window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337573] pci 0000:00:1c.0:   PREFETCH window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337583] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Aug 27 13:03:39 adam-laptop kernel: [    0.337587] pci 0000:00:1c.1:   IO window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337598] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xfbffffff
Aug 27 13:03:39 adam-laptop kernel: [    0.337608] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
Aug 27 13:03:39 adam-laptop kernel: [    0.337621] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01
Aug 27 13:03:39 adam-laptop kernel: [    0.337629] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
Aug 27 13:03:39 adam-laptop kernel: [    0.337639] pci 0000:00:1c.3:   MEM window: 0xf7f00000-0xf7ffffff
Aug 27 13:03:39 adam-laptop kernel: [    0.337647] pci 0000:00:1c.3:   PREFETCH window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337656] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Aug 27 13:03:39 adam-laptop kernel: [    0.337661] pci 0000:00:1e.0:   IO window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337670] pci 0000:00:1e.0:   MEM window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337678] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug 27 13:03:39 adam-laptop kernel: [    0.337704]   alloc irq_desc for 16 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.337709]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.337722] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 27 13:03:39 adam-laptop kernel: [    0.337732] pci 0000:00:1c.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.337747]   alloc irq_desc for 17 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.337752]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.337760] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 27 13:03:39 adam-laptop kernel: [    0.337769] pci 0000:00:1c.1: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.337784]   alloc irq_desc for 19 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.337788]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.337796] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 27 13:03:39 adam-laptop kernel: [    0.337805] pci 0000:00:1c.3: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.337819] pci 0000:00:1e.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.337828] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337835] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337842] pci_bus 0000:02: resource 1 mem: [0xf8000000-0xfbffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337848] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf6ffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337855] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337861] pci_bus 0000:01: resource 1 mem: [0xf7f00000-0xf7ffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337868] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337874] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
Aug 27 13:03:39 adam-laptop kernel: [    0.337951] NET: Registered protocol family 2
Aug 27 13:03:39 adam-laptop kernel: [    0.338167] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.338864] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.339838] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.340317] TCP: Hash tables configured (established 131072 bind 65536)
Aug 27 13:03:39 adam-laptop kernel: [    0.340327] TCP reno registered
Aug 27 13:03:39 adam-laptop kernel: [    0.340580] NET: Registered protocol family 1
Aug 27 13:03:39 adam-laptop kernel: [    0.340714] Trying to unpack rootfs image as initramfs...
Aug 27 13:03:39 adam-laptop kernel: [    0.500351] Switched to high resolution mode on CPU 1
Aug 27 13:03:39 adam-laptop kernel: [    0.504005] Switched to high resolution mode on CPU 0
Aug 27 13:03:39 adam-laptop kernel: [    0.677703] Freeing initrd memory: 7058k freed
Aug 27 13:03:39 adam-laptop kernel: [    0.685594] cpufreq-nforce2: No nForce2 chipset.
Aug 27 13:03:39 adam-laptop kernel: [    0.685874] Scanning for low memory corruption every 60 seconds
Aug 27 13:03:39 adam-laptop kernel: [    0.686464] audit: initializing netlink socket (disabled)
Aug 27 13:03:39 adam-laptop kernel: [    0.686492] type=2000 audit(1251378200.685:1): initialized
Aug 27 13:03:39 adam-laptop kernel: [    0.704112] highmem bounce pool size: 64 pages
Aug 27 13:03:39 adam-laptop kernel: [    0.704127] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 27 13:03:39 adam-laptop kernel: [    0.711471] VFS: Disk quotas dquot_6.5.2
Aug 27 13:03:39 adam-laptop kernel: [    0.711697] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 27 13:03:39 adam-laptop kernel: [    0.714362] fuse init (API version 7.12)
Aug 27 13:03:39 adam-laptop kernel: [    0.714802] msgmni has been set to 1732
Aug 27 13:03:39 adam-laptop kernel: [    0.715340] alg: No test for stdrng (krng)
Aug 27 13:03:39 adam-laptop kernel: [    0.715367] io scheduler noop registered
Aug 27 13:03:39 adam-laptop kernel: [    0.715372] io scheduler anticipatory registered
Aug 27 13:03:39 adam-laptop kernel: [    0.715377] io scheduler deadline registered
Aug 27 13:03:39 adam-laptop kernel: [    0.715581] io scheduler cfq registered (default)
Aug 27 13:03:39 adam-laptop kernel: [    0.715606] pci 0000:00:02.0: Boot video device
Aug 27 13:03:39 adam-laptop kernel: [    0.716051]   alloc irq_desc for 24 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.716057]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.716076] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
Aug 27 13:03:39 adam-laptop kernel: [    0.716094] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.716561]   alloc irq_desc for 25 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.716567]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.716582] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
Aug 27 13:03:39 adam-laptop kernel: [    0.716599] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.717056]   alloc irq_desc for 26 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.717061]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    0.717077] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
Aug 27 13:03:39 adam-laptop kernel: [    0.717093] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    0.717678] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 27 13:03:39 adam-laptop kernel: [    0.718149] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 27 13:03:39 adam-laptop kernel: [    0.718832] ACPI: AC Adapter [AC0] (off-line)
Aug 27 13:03:39 adam-laptop kernel: [    0.719191] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Aug 27 13:03:39 adam-laptop kernel: [    0.719200] ACPI: Power Button [PWRF]
Aug 27 13:03:39 adam-laptop kernel: [    0.719420] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Aug 27 13:03:39 adam-laptop kernel: [    0.720693] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 27 13:03:39 adam-laptop kernel: [    0.733901] ACPI: Lid Switch [LID]
Aug 27 13:03:39 adam-laptop kernel: [    0.734140] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Aug 27 13:03:39 adam-laptop kernel: [    0.734150] ACPI: Sleep Button [SLPB]
Aug 27 13:03:39 adam-laptop kernel: [    0.734340] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Aug 27 13:03:39 adam-laptop kernel: [    0.734348] ACPI: Power Button [PWRB]
Aug 27 13:03:39 adam-laptop kernel: [    0.735927] ACPI: SSDT 3f7ae180 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Aug 27 13:03:39 adam-laptop kernel: [    0.736990] ACPI: SSDT 3f7ae450 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Aug 27 13:03:39 adam-laptop kernel: [    0.737790] Monitor-Mwait will be used to enter C-1 state
Aug 27 13:03:39 adam-laptop kernel: [    0.737854] Monitor-Mwait will be used to enter C-2 state
Aug 27 13:03:39 adam-laptop kernel: [    0.737915] Monitor-Mwait will be used to enter C-3 state
Aug 27 13:03:39 adam-laptop kernel: [    0.737931] Marking TSC unstable due to TSC halts in idle
Aug 27 13:03:39 adam-laptop kernel: [    0.738069] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug 27 13:03:39 adam-laptop kernel: [    0.738207] processor LNXCPU:00: registered as cooling_device0
Aug 27 13:03:39 adam-laptop kernel: [    0.738217] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 27 13:03:39 adam-laptop kernel: [    0.738978] ACPI: SSDT 3f7ae0b0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
Aug 27 13:03:39 adam-laptop kernel: [    0.739667] ACPI: SSDT 3f7ae3c0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
Aug 27 13:03:39 adam-laptop kernel: [    0.740852] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Aug 27 13:03:39 adam-laptop kernel: [    0.740982] processor LNXCPU:01: registered as cooling_device1
Aug 27 13:03:39 adam-laptop kernel: [    0.740993] ACPI: Processor [CPU1] (supports 8 throttling states)
Aug 27 13:03:39 adam-laptop kernel: [    0.760894] thermal LNXTHERM:01: registered as thermal_zone0
Aug 27 13:03:39 adam-laptop kernel: [    0.760913] ACPI: Thermal Zone [TZ00] (55 C)
Aug 27 13:03:39 adam-laptop kernel: [    0.761389] isapnp: Scanning for PnP cards...
Aug 27 13:03:39 adam-laptop kernel: [    1.016356] ACPI: Battery Slot [BAT0] (battery present)
Aug 27 13:03:39 adam-laptop kernel: [    1.115921] isapnp: No Plug & Play device found
Aug 27 13:03:39 adam-laptop kernel: [    1.125010] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 27 13:03:39 adam-laptop kernel: [    1.131226] brd: module loaded
Aug 27 13:03:39 adam-laptop kernel: [    1.133817] loop: module loaded
Aug 27 13:03:39 adam-laptop kernel: [    1.134266] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Aug 27 13:03:39 adam-laptop kernel: [    1.134767] ahci 0000:00:1f.2: version 3.0
Aug 27 13:03:39 adam-laptop kernel: [    1.134800]   alloc irq_desc for 18 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    1.134805]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    1.134820] ahci 0000:00:1f.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Aug 27 13:03:39 adam-laptop kernel: [    1.134876]   alloc irq_desc for 27 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    1.134881]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    1.134897] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
Aug 27 13:03:39 adam-laptop kernel: [    1.135010] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Aug 27 13:03:39 adam-laptop kernel: [    1.135018] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
Aug 27 13:03:39 adam-laptop kernel: [    1.135028] ahci 0000:00:1f.2: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.135388] scsi0 : ahci
Aug 27 13:03:39 adam-laptop kernel: [    1.135835] scsi1 : ahci
Aug 27 13:03:39 adam-laptop kernel: [    1.136427] scsi2 : ahci
Aug 27 13:03:39 adam-laptop kernel: [    1.136738] scsi3 : ahci
Aug 27 13:03:39 adam-laptop kernel: [    1.137300] ata1: SATA max UDMA/133 abar m1024@0xf7db7800 port 0xf7db7900 irq 27
Aug 27 13:03:39 adam-laptop kernel: [    1.137307] ata2: DUMMY
Aug 27 13:03:39 adam-laptop kernel: [    1.137313] ata3: SATA max UDMA/133 abar m1024@0xf7db7800 port 0xf7db7a00 irq 27
Aug 27 13:03:39 adam-laptop kernel: [    1.137318] ata4: DUMMY
Aug 27 13:03:39 adam-laptop kernel: [    1.137761] ata_piix 0000:00:1f.1: version 2.13
Aug 27 13:03:39 adam-laptop kernel: [    1.137789] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 27 13:03:39 adam-laptop kernel: [    1.137856] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.138005] scsi4 : ata_piix
Aug 27 13:03:39 adam-laptop kernel: [    1.138324] scsi5 : ata_piix
Aug 27 13:03:39 adam-laptop kernel: [    1.141196] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug 27 13:03:39 adam-laptop kernel: [    1.141204] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug 27 13:03:39 adam-laptop kernel: [    1.141587] ata6: port disabled. ignoring.
Aug 27 13:03:39 adam-laptop kernel: [    1.146905] Fixed MDIO Bus: probed
Aug 27 13:03:39 adam-laptop kernel: [    1.146922] PPP generic driver version 2.4.2
Aug 27 13:03:39 adam-laptop kernel: [    1.147479] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 27 13:03:39 adam-laptop kernel: [    1.147539]   alloc irq_desc for 23 on node -1
Aug 27 13:03:39 adam-laptop kernel: [    1.147545]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [    1.147559] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 27 13:03:39 adam-laptop kernel: [    1.147588] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.147596] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 27 13:03:39 adam-laptop kernel: [    1.147761] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug 27 13:03:39 adam-laptop kernel: [    1.151683] ehci_hcd 0000:00:1d.7: debug port 1
Aug 27 13:03:39 adam-laptop kernel: [    1.151694] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Aug 27 13:03:39 adam-laptop kernel: [    1.151727] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7db7c00
Aug 27 13:03:39 adam-laptop kernel: [    1.165029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 27 13:03:39 adam-laptop kernel: [    1.165314] usb usb1: configuration #1 chosen from 1 choice
Aug 27 13:03:39 adam-laptop kernel: [    1.165463] hub 1-0:1.0: USB hub found
Aug 27 13:03:39 adam-laptop kernel: [    1.165482] hub 1-0:1.0: 8 ports detected
Aug 27 13:03:39 adam-laptop kernel: [    1.165707] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 27 13:03:39 adam-laptop kernel: [    1.165833] uhci_hcd: USB Universal Host Controller Interface driver
Aug 27 13:03:39 adam-laptop kernel: [    1.165916] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 27 13:03:39 adam-laptop kernel: [    1.165931] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.165939] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 27 13:03:39 adam-laptop kernel: [    1.166106] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug 27 13:03:39 adam-laptop kernel: [    1.166150] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
Aug 27 13:03:39 adam-laptop kernel: [    1.166416] usb usb2: configuration #1 chosen from 1 choice
Aug 27 13:03:39 adam-laptop kernel: [    1.166562] hub 2-0:1.0: USB hub found
Aug 27 13:03:39 adam-laptop kernel: [    1.166580] hub 2-0:1.0: 2 ports detected
Aug 27 13:03:39 adam-laptop kernel: [    1.166676] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 27 13:03:39 adam-laptop kernel: [    1.166690] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.166698] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 27 13:03:39 adam-laptop kernel: [    1.166847] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug 27 13:03:39 adam-laptop kernel: [    1.166903] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
Aug 27 13:03:39 adam-laptop kernel: [    1.167168] usb usb3: configuration #1 chosen from 1 choice
Aug 27 13:03:39 adam-laptop kernel: [    1.167308] hub 3-0:1.0: USB hub found
Aug 27 13:03:39 adam-laptop kernel: [    1.167324] hub 3-0:1.0: 2 ports detected
Aug 27 13:03:39 adam-laptop kernel: [    1.167418] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 27 13:03:39 adam-laptop kernel: [    1.167432] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.167439] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 27 13:03:39 adam-laptop kernel: [    1.167589] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug 27 13:03:39 adam-laptop kernel: [    1.167644] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
Aug 27 13:03:39 adam-laptop kernel: [    1.167904] usb usb4: configuration #1 chosen from 1 choice
Aug 27 13:03:39 adam-laptop kernel: [    1.168114] hub 4-0:1.0: USB hub found
Aug 27 13:03:39 adam-laptop kernel: [    1.168133] hub 4-0:1.0: 2 ports detected
Aug 27 13:03:39 adam-laptop kernel: [    1.168236] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Aug 27 13:03:39 adam-laptop kernel: [    1.168250] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    1.168258] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 27 13:03:39 adam-laptop kernel: [    1.168424] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Aug 27 13:03:39 adam-laptop kernel: [    1.168480] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
Aug 27 13:03:39 adam-laptop kernel: [    1.168745] usb usb5: configuration #1 chosen from 1 choice
Aug 27 13:03:39 adam-laptop kernel: [    1.168889] hub 5-0:1.0: USB hub found
Aug 27 13:03:39 adam-laptop kernel: [    1.168908] hub 5-0:1.0: 2 ports detected
Aug 27 13:03:39 adam-laptop kernel: [    1.169374] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 27 13:03:39 adam-laptop kernel: [    1.192417] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 27 13:03:39 adam-laptop kernel: [    1.192432] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 27 13:03:39 adam-laptop kernel: [    1.192977] mice: PS/2 mouse device common for all mice
Aug 27 13:03:39 adam-laptop kernel: [    1.193756] rtc_cmos 00:03: RTC can wake from S4
Aug 27 13:03:39 adam-laptop kernel: [    1.193935] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Aug 27 13:03:39 adam-laptop kernel: [    1.193982] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Aug 27 13:03:39 adam-laptop kernel: [    1.194504] device-mapper: uevent: version 1.0.3
Aug 27 13:03:39 adam-laptop kernel: [    1.194874] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Aug 27 13:03:39 adam-laptop kernel: [    1.195051] device-mapper: multipath: version 1.1.0 loaded
Aug 27 13:03:39 adam-laptop kernel: [    1.195058] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 27 13:03:39 adam-laptop kernel: [    1.195608] EISA: Probing bus 0 at eisa.0
Aug 27 13:03:39 adam-laptop kernel: [    1.195652] EISA: Detected 0 cards.
Aug 27 13:03:39 adam-laptop kernel: [    1.196709] cpuidle: using governor ladder
Aug 27 13:03:39 adam-laptop kernel: [    1.198288] cpuidle: using governor menu
Aug 27 13:03:39 adam-laptop kernel: [    1.200061] TCP cubic registered
Aug 27 13:03:39 adam-laptop kernel: [    1.201027] NET: Registered protocol family 10
Aug 27 13:03:39 adam-laptop kernel: [    1.202043] lo: Disabled Privacy Extensions
Aug 27 13:03:39 adam-laptop kernel: [    1.202800] NET: Registered protocol family 17
Aug 27 13:03:39 adam-laptop kernel: [    1.202988] Bluetooth: L2CAP ver 2.13
Aug 27 13:03:39 adam-laptop kernel: [    1.202993] Bluetooth: L2CAP socket layer initialized
Aug 27 13:03:39 adam-laptop kernel: [    1.203000] Bluetooth: SCO (Voice Link) ver 0.6
Aug 27 13:03:39 adam-laptop kernel: [    1.203004] Bluetooth: SCO socket layer initialized
Aug 27 13:03:39 adam-laptop kernel: [    1.203084] Bluetooth: RFCOMM TTY layer initialized
Aug 27 13:03:39 adam-laptop kernel: [    1.203091] Bluetooth: RFCOMM socket layer initialized
Aug 27 13:03:39 adam-laptop kernel: [    1.203096] Bluetooth: RFCOMM ver 1.11
Aug 27 13:03:39 adam-laptop kernel: [    1.204321] Using IPI No-Shortcut mode
Aug 27 13:03:39 adam-laptop kernel: [    1.204821] PM: Resume from disk failed.
Aug 27 13:03:39 adam-laptop kernel: [    1.204849] registered taskstats version 1
Aug 27 13:03:39 adam-laptop kernel: [    1.205112]   Magic number: 5:931:79
Aug 27 13:03:39 adam-laptop kernel: [    1.205245] rtc_cmos 00:03: setting system clock to 2009-08-27 13:03:22 UTC (1251378202)
Aug 27 13:03:39 adam-laptop kernel: [    1.205253] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 27 13:03:39 adam-laptop kernel: [    1.205258] EDD information not available.
Aug 27 13:03:39 adam-laptop kernel: [    1.211253] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Aug 27 13:03:39 adam-laptop kernel: [    1.456207] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 27 13:03:39 adam-laptop kernel: [    1.457720] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Aug 27 13:03:39 adam-laptop kernel: [    1.457938] ata1.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133
Aug 27 13:03:39 adam-laptop kernel: [    1.457954] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 27 13:03:39 adam-laptop kernel: [    1.459783] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Aug 27 13:03:39 adam-laptop kernel: [    1.460136] ata1.00: configured for UDMA/133
Aug 27 13:03:39 adam-laptop kernel: [    1.460188] ata3: SATA link down (SStatus 0 SControl 300)
Aug 27 13:03:39 adam-laptop kernel: [    1.476221] usb 1-2: new high speed USB device using ehci_hcd and address 2
Aug 27 13:03:39 adam-laptop kernel: [    1.476585] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
Aug 27 13:03:39 adam-laptop kernel: [    1.477366] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug 27 13:03:39 adam-laptop kernel: [    1.477543] sd 0:0:0:0: [sda] Write Protect is off
Aug 27 13:03:39 adam-laptop kernel: [    1.477550] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 27 13:03:39 adam-laptop kernel: [    1.477559] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 27 13:03:39 adam-laptop kernel: [    1.477650] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 27 13:03:39 adam-laptop kernel: [    1.477988]  sda: sda1 sda2 <
Aug 27 13:03:39 adam-laptop kernel: [    1.500076] Clocksource tsc unstable (delta = -213602283 ns)
Aug 27 13:03:39 adam-laptop kernel: [    1.519474]  sda5 sda6 > sda3 sda4
Aug 27 13:03:39 adam-laptop kernel: [    1.539037] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 27 13:03:39 adam-laptop kernel: [    1.539096] Freeing unused kernel memory: 536k freed
Aug 27 13:03:39 adam-laptop kernel: [    1.539604] Write protecting the kernel text: 4540k
Aug 27 13:03:39 adam-laptop kernel: [    1.539683] Write protecting the kernel read-only data: 1824k
Aug 27 13:03:39 adam-laptop kernel: [    1.693390] usb 1-2: configuration #1 chosen from 1 choice
Aug 27 13:03:39 adam-laptop kernel: [    1.747357] Linux agpgart interface v0.103
Aug 27 13:03:39 adam-laptop kernel: [    1.754736] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Aug 27 13:03:39 adam-laptop kernel: [    1.754962] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Aug 27 13:03:39 adam-laptop kernel: [    1.757847] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Aug 27 13:03:39 adam-laptop kernel: [    1.769598] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:21/input/input6
Aug 27 13:03:39 adam-laptop kernel: [    1.769781] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug 27 13:03:39 adam-laptop kernel: [    1.814706] [drm] Initialized drm 1.1.0 20060810
Aug 27 13:03:39 adam-laptop kernel: [    1.843884] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 27 13:03:39 adam-laptop kernel: [    1.843895] i915 0000:00:02.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    2.072047] [drm] fb0: inteldrmfb frame buffer device
Aug 27 13:03:39 adam-laptop kernel: [    2.072070] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Aug 27 13:03:39 adam-laptop kernel: [    2.397076] [drm] LVDS-8: set mode 1024x600 e
Aug 27 13:03:39 adam-laptop kernel: [    2.767057] Console: switching to colour frame buffer device 128x37
Aug 27 13:03:39 adam-laptop kernel: [    4.052412] PM: Starting manual resume from disk
Aug 27 13:03:39 adam-laptop kernel: [    4.052421] PM: Resume from partition 8:6
Aug 27 13:03:39 adam-laptop kernel: [    4.052425] PM: Checking hibernation image.
Aug 27 13:03:39 adam-laptop kernel: [    4.052711] PM: Resume from disk failed.
Aug 27 13:03:39 adam-laptop kernel: [    4.084860] EXT4-fs (sda5): barriers enabled
Aug 27 13:03:39 adam-laptop kernel: [    4.104462] kjournald2 starting: pid 1094, dev sda5:8, commit interval 5 seconds
Aug 27 13:03:39 adam-laptop kernel: [    4.104520] EXT4-fs (sda5): delayed allocation enabled
Aug 27 13:03:39 adam-laptop kernel: [    4.104547] EXT4-fs: file extents enabled
Aug 27 13:03:39 adam-laptop kernel: [    4.111091] EXT4-fs: mballoc enabled
Aug 27 13:03:39 adam-laptop kernel: [    4.111124] EXT4-fs (sda5): mounted filesystem with ordered data mode
Aug 27 13:03:39 adam-laptop kernel: [    8.725289] udev: starting version 146
Aug 27 13:03:39 adam-laptop kernel: [    9.048105] eeepc_laptop: Eee PC Hotkey Driver
Aug 27 13:03:39 adam-laptop kernel: [    9.048688] eeepc_laptop: Hotkey init flags 0x41
Aug 27 13:03:39 adam-laptop kernel: [    9.048984] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
Aug 27 13:03:39 adam-laptop kernel: [    9.060051] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
Aug 27 13:03:39 adam-laptop kernel: [    9.070989] eeepc_laptop: TPD (8000000) not reported by BIOS, enabling anyway
Aug 27 13:03:39 adam-laptop kernel: [    9.071001] eeepc_laptop: Get control methods supported: 0xe101711
Aug 27 13:03:39 adam-laptop kernel: [    9.071172] input: Asus EeePC extra buttons as /devices/virtual/input/input7
Aug 27 13:03:39 adam-laptop kernel: [    9.677538] atl1c 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 27 13:03:39 adam-laptop kernel: [    9.677564] atl1c 0000:01:00.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [    9.677636] atl1c 0000:01:00.0: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    9.677650] atl1c 0000:01:00.0: PME# disabled
Aug 27 13:03:39 adam-laptop kernel: [    9.679752] intel_rng: FWH not detected
Aug 27 13:03:39 adam-laptop kernel: [    9.713316] cfg80211: Calling CRDA to update world regulatory domain
Aug 27 13:03:39 adam-laptop kernel: [    9.794764] atl1c 0000:01:00.0: version 1.0.0.1-NAPI
Aug 27 13:03:39 adam-laptop kernel: [    9.860440] Linux video capture interface: v2.00
Aug 27 13:03:39 adam-laptop kernel: [   10.071726] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (13d3:5095)
Aug 27 13:03:39 adam-laptop kernel: [   10.086886] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8
Aug 27 13:03:39 adam-laptop kernel: [   10.087184] usbcore: registered new interface driver uvcvideo
Aug 27 13:03:39 adam-laptop kernel: [   10.087327] USB Video Class driver (v0.1.0)
Aug 27 13:03:39 adam-laptop kernel: [   10.520478] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 27 13:03:39 adam-laptop kernel: [   10.520505] ath9k 0000:02:00.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [   10.570962] ath: EEPROM regdomain: 0x60
Aug 27 13:03:39 adam-laptop kernel: [   10.570971] ath: EEPROM indicates we should expect a direct regpair map
Aug 27 13:03:39 adam-laptop kernel: [   10.570981] ath: Country alpha2 being used: 00
Aug 27 13:03:39 adam-laptop kernel: [   10.570987] ath: Regpair used: 0x60
Aug 27 13:03:39 adam-laptop kernel: [   10.771818] phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 27 13:03:39 adam-laptop kernel: [   10.774162] Registered led device: ath9k-phy0::radio
Aug 27 13:03:39 adam-laptop kernel: [   10.774215] Registered led device: ath9k-phy0::assoc
Aug 27 13:03:39 adam-laptop kernel: [   10.774265] Registered led device: ath9k-phy0::tx
Aug 27 13:03:39 adam-laptop kernel: [   10.774313] Registered led device: ath9k-phy0::rx
Aug 27 13:03:39 adam-laptop kernel: [   10.774361] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8a80000, irq=17
Aug 27 13:03:39 adam-laptop kernel: [   10.937879] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000
Aug 27 13:03:39 adam-laptop kernel: [   11.014064] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Aug 27 13:03:39 adam-laptop kernel: [   11.161239]   alloc irq_desc for 22 on node -1
Aug 27 13:03:39 adam-laptop kernel: [   11.161246]   alloc kstat_irqs on node -1
Aug 27 13:03:39 adam-laptop kernel: [   11.161260] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 27 13:03:39 adam-laptop kernel: [   11.161326] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 27 13:03:39 adam-laptop kernel: [   11.163964] cfg80211: World regulatory domain updated:
Aug 27 13:03:39 adam-laptop kernel: [   11.163979] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 27 13:03:39 adam-laptop kernel: [   11.163995] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 27 13:03:39 adam-laptop kernel: [   11.164070] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 27 13:03:39 adam-laptop kernel: [   11.164083] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 27 13:03:39 adam-laptop kernel: [   11.164096] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 27 13:03:39 adam-laptop kernel: [   11.164109] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 27 13:03:39 adam-laptop kernel: [   11.268854] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
Aug 27 13:03:39 adam-laptop kernel: [   11.269049] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Aug 27 13:03:39 adam-laptop kernel: [   12.906510] lp: driver loaded but no devices found
Aug 27 13:03:39 adam-laptop kernel: [   13.622728] Adding 1164672k swap on /dev/sda6.  Priority:-1 extents:1 across:1164672k 
Aug 27 13:03:39 adam-laptop kernel: [   13.705120] EXT4-fs (sda5): internal journal on sda5:8
Aug 27 13:03:39 adam-laptop kernel: [   15.847472] type=1505 audit(1251396217.141:2): operation="profile_load" pid=1784 name=/usr/share/gdm/guest-session/Xsession
Aug 27 13:03:39 adam-laptop kernel: [   15.878379] type=1505 audit(1251396217.170:3): operation="profile_load" pid=1785 name=/sbin/dhclient3
Aug 27 13:03:39 adam-laptop kernel: [   15.878917] type=1505 audit(1251396217.170:4): operation="profile_load" pid=1785 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Aug 27 13:03:39 adam-laptop kernel: [   15.879230] type=1505 audit(1251396217.170:5): operation="profile_load" pid=1785 name=/usr/lib/connman/scripts/dhclient-script
Aug 27 13:03:39 adam-laptop kernel: [   15.900668] type=1505 audit(1251396217.194:6): operation="profile_load" pid=1786 name=/usr/sbin/tcpdump
Aug 27 13:03:39 adam-laptop kernel: [   15.916894] type=1505 audit(1251396217.210:7): operation="profile_load" pid=1787 name=/usr/lib/cups/backend/cups-pdf
Aug 27 13:03:39 adam-laptop kernel: [   15.917622] type=1505 audit(1251396217.210:8): operation="profile_load" pid=1787 name=/usr/sbin/cupsd
Aug 27 13:03:39 adam-laptop kernel: [   16.089276] type=1505 audit(1251396217.383:9): operation="profile_load" pid=1788 name=/usr/bin/evince
Aug 27 13:03:39 adam-laptop kernel: [   16.095565] type=1505 audit(1251396217.387:10): operation="profile_load" pid=1788 name=/usr/bin/evince-previewer
Aug 27 13:03:39 adam-laptop kernel: [   16.099560] type=1505 audit(1251396217.390:11): operation="profile_load" pid=1788 name=/usr/bin/evince-thumbnailer
Aug 27 13:03:41 adam-laptop acpid: client connected from 2196[107:114]
Aug 27 13:03:42 adam-laptop gdm-binary[2242]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): Enabling debugging
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 1: signum=15 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 15 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 2: signum=2 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 2 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 3: signum=4 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 4 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 4: signum=7 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 7 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 5: signum=8 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 8 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 6: signum=1 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 1 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 7: signum=6 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 6 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 8: signum=10 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 10 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Adding handler 9: signum=12 0x804dc70
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSignalHandler: Registering for 12 signals
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSlave: Registering /org/gnome/DisplayManager/Slave1
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSlave: starting slave
Aug 27 13:03:42 adam-laptop gdm-simple-slave[2245]: DEBUG(+): GdmSlave: Starting slave
```

Enjoy :P

---

### Post by P4man on 2009-08-27
hint: put code tags around it, so it gets reduced in size with scroll bars :)

Your log doesnt show anything from the shutdown.. is that all there is in it ? It start with the boot, im interested in what comes before that ?

---

### Post by P4man on 2009-08-27
if its not in syslog, then check syslog.0

---

### Post by madarieder on 2009-08-27
> **P4man said:**
> if its not in syslog, then check syslog.0
I don't believe I have a syslog.0

---

