---
title: "Ubuntu freezing on logon prompt for about 3 mins then again at login for about  1 min"
date: 2011-07-24
forum: General Help
---

### Post by joshmo on 2011-07-24
Hello, as the title states, I have been having this problem for two days now, trying to solve it but with no success. I have tried updating my kernel from 2.6.38-8-generic to 2.6.38-10 (since 2.6.39 was not available when i tried the update) but on updating grub, I get a syntax error. I have also read through this thread [HTML] http://ubuntuforums.org/showthread.php?p=11077303 [/HTML] which has not managed to solve my issue. I have been using this version of Ubuntu (11.04) for about a month and a half now and this is the first time am running into this. Am using a Compaq Presario CQ40 Laptop with AMD Turion X2 and ATI Radeon 3200 HD

---

### Post by galvatron408 on 2011-07-24
hmm, what takes 3 minutes to time out before it skips to the next?

Well, anyway, when the freeze happens, press ctrl+alt+f1 and login. Then you'll want to tail -f /var/log/messages (or if you're on 11.04, then it's tail -f /var/log/syslog)

what's it waiting for?

---

### Post by joshmo on 2011-07-24
my bad...seems i didnt give enough info. When the laptop boots up, the logon prompt appears but then the system freezes as i cant enter anything or move the mouse around. After about 3 minutes, the system becomes responsive and I can logon. When I enter the password to logon, the system hangs on the desktop with nothing for about a minute or longer then everything loads. Tried removing all startup programs but the problem was still the same. Gonna try the tail command and see what happens.

---

### Post by galvatron408 on 2011-07-24
ok, then, what I would do is....

boot in to runlevel 3 to see if the freeze exists. If it does, at least you'll see what line it hangs on. If it doesn't, that's fine too.

When runlevel 3 is done booting, then switch to runlevel 5 to see if you see the freeze.

A lot of times, when a linux distro is freezing the way you describe it, it means that the cpu is at 100% utilisation. Basically, it's too busy doing whatever it is doing to give cpu cycles to the GUI and mouse. There's really no other reason I can think of as to why it freezes and then comes back (other than a timeout; but then again, you said the mouse freezes too).

---

### Post by joshmo on 2011-07-24
I managed to make get the syslog info of the system but I cant understand over half of what it says. Got lost in some kernel stuff. I renamed the initial syslog file so the one generated is entirely for the session to show my problem. I have failed to attach it because of size limits so here it is 
```

Jul 25 01:08:09 my_comp kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jul 25 01:08:09 my_comp rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1046" x-info="http://www.rsyslog.com"] (re)start
Jul 25 01:08:10 my_comp rsyslogd: rsyslogd's groupid changed to 103
Jul 25 01:08:10 my_comp rsyslogd: rsyslogd's userid changed to 101
Jul 25 01:08:09 my_comp rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Successfully dropped root privileges.
Jul 25 01:08:10 my_comp avahi-daemon[1066]: avahi-daemon 0.6.30 starting up.
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Successfully called chroot().
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Successfully dropped remaining capabilities.
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Loading service file /services/udisks.service.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> NetworkManager (version 0.8.3.998) is starting...
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> trying to start the modem manager...
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Network interface enumeration completed.
Jul 25 01:08:10 my_comp kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 25 01:08:10 my_comp kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 25 01:08:10 my_comp kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jul 25 01:08:10 my_comp kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000afd70000 (usable)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe58000 (usable)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afe58000 - 00000000afebf000 (ACPI NVS)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeea000 (usable)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afeea000 - 00000000afeff000 (ACPI data)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e1000000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Jul 25 01:08:10 my_comp kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jul 25 01:08:10 my_comp kernel: [    0.000000] DMI 2.4 present.
Jul 25 01:08:10 my_comp kernel: [    0.000000] DMI: Hewlett-Packard Compaq Presario CQ40 Notebook PC/30FE, BIOS F.55 07/06/2010
Jul 25 01:08:10 my_comp kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul 25 01:08:10 my_comp kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul 25 01:08:10 my_comp kernel: [    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000
Jul 25 01:08:10 my_comp kernel: [    0.000000] MTRR default type: uncachable
Jul 25 01:08:10 my_comp kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 25 01:08:10 my_comp kernel: [    0.000000]   00000-9FFFF write-back
Jul 25 01:08:10 my_comp kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 25 01:08:10 my_comp kernel: [    0.000000]   C0000-FFFFF write-through
Jul 25 01:08:10 my_comp kernel: [    0.000000] MTRR variable ranges enabled:
Jul 25 01:08:10 my_comp kernel: [    0.000000]   0 base 00FFF00000 mask FFFFF00000 write-protect
Jul 25 01:08:10 my_comp kernel: [    0.000000]   1 base 0000000000 mask FF80000000 write-back
Jul 25 01:08:10 my_comp kernel: [    0.000000]   2 base 0080000000 mask FFE0000000 write-back
Jul 25 01:08:10 my_comp kernel: [    0.000000]   3 base 00A0000000 mask FFF0000000 write-back
Jul 25 01:08:10 my_comp kernel: [    0.000000]   4 disabled
Jul 25 01:08:10 my_comp kernel: [    0.000000]   5 disabled
Jul 25 01:08:10 my_comp kernel: [    0.000000]   6 disabled
Jul 25 01:08:10 my_comp kernel: [    0.000000]   7 disabled
Jul 25 01:08:10 my_comp kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 25 01:08:10 my_comp kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Jul 25 01:08:10 my_comp kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 25 01:08:10 my_comp kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul 25 01:08:10 my_comp kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul 25 01:08:10 my_comp kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul 25 01:08:10 my_comp kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Jul 25 01:08:10 my_comp kernel: [    0.000000] RAMDISK: 35c20000 - 36e08000
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: XSDT afefe120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: FACP afefd000 000F4 (v04 HP     REPLEY   00000003 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: DSDT afeee000 0A632 (v01 HP     REPLEY   F0000000 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: FACS afe61000 00040
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: HPET afefc000 00038 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: APIC afefb000 00084 (v02 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: MCFG afefa000 0003C (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: MSCT afef9000 0004E (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: BOOT afeed000 00028 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: SLIC afeec000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: SSDT afeeb000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: SRAT afeea000 00078 (v03 AMD    AMD CRB  00000001 AMD  00000001)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 25 01:08:10 my_comp kernel: [    0.000000] 1927MB HIGHMEM available.
Jul 25 01:08:10 my_comp kernel: [    0.000000] 887MB LOWMEM available.
Jul 25 01:08:10 my_comp kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 25 01:08:10 my_comp kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 25 01:08:10 my_comp kernel: [    0.000000] Zone PFN ranges:
Jul 25 01:08:10 my_comp kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 25 01:08:10 my_comp kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 25 01:08:10 my_comp kernel: [    0.000000]   HighMem  0x000377fe -> 0x000aff00
Jul 25 01:08:10 my_comp kernel: [    0.000000] Movable zone start PFN for each node
Jul 25 01:08:10 my_comp kernel: [    0.000000] early_node_map[5] active PFN ranges
Jul 25 01:08:10 my_comp kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 25 01:08:10 my_comp kernel: [    0.000000]     0: 0x00000100 -> 0x000afd70
Jul 25 01:08:10 my_comp kernel: [    0.000000]     0: 0x000afdbf -> 0x000afe58
Jul 25 01:08:10 my_comp kernel: [    0.000000]     0: 0x000afebf -> 0x000afeea
Jul 25 01:08:10 my_comp kernel: [    0.000000]     0: 0x000afeff -> 0x000aff00
Jul 25 01:08:10 my_comp kernel: [    0.000000] On node 0 totalpages: 720324
Jul 25 01:08:10 my_comp kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4620200
Jul 25 01:08:10 my_comp kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 25 01:08:10 my_comp kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 25 01:08:10 my_comp kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 25 01:08:10 my_comp kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul 25 01:08:10 my_comp kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul 25 01:08:10 my_comp kernel: [    0.000000]   HighMem zone: 3855 pages used for memmap
Jul 25 01:08:10 my_comp kernel: [    0.000000]   HighMem zone: 489256 pages, LIFO batch:31
Jul 25 01:08:10 my_comp kernel: [    0.000000] Using APIC driver default
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 25 01:08:10 my_comp kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 25 01:08:10 my_comp kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 25 01:08:10 my_comp kernel: [    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
Jul 25 01:08:10 my_comp kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 25 01:08:10 my_comp kernel: [    0.000000] nr_irqs_gsi: 40
Jul 25 01:08:10 my_comp kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 25 01:08:10 my_comp kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 25 01:08:10 my_comp kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 25 01:08:10 my_comp kernel: [    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 25 01:08:10 my_comp kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 25 01:08:10 my_comp kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
Jul 25 01:08:10 my_comp kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
Jul 25 01:08:10 my_comp kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 25 01:08:10 my_comp kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714693
Jul 25 01:08:10 my_comp kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=dede56cd-fa70-49da-bcc6-75a2a59cda86 ro quiet splash
Jul 25 01:08:10 my_comp kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Initializing CPU#0
Jul 25 01:08:10 my_comp kernel: [    0.000000] allocated 14412480 bytes of page_cgroup
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Registering HINFO record with values 'I686'/'LINUX'.
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Server startup complete. Host name is my_comp.local. Local service cookie is 3547419126.
Jul 25 01:08:10 my_comp avahi-daemon[1066]: Service "my_comp" (/services/udisks.service) successfully established.
Jul 25 01:08:10 my_comp kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 25 01:08:10 my_comp kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000aff00)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Memory: 2815936k/2882560k available (5188k kernel code, 65360k reserved, 2540k data, 700k init, 1972444k highmem)
Jul 25 01:08:10 my_comp kernel: [    0.000000] virtual kernel memory layout:
Jul 25 01:08:10 my_comp kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul 25 01:08:10 my_comp kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 25 01:08:10 my_comp kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 25 01:08:10 my_comp kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 25 01:08:10 my_comp kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Jul 25 01:08:10 my_comp kernel: [    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
Jul 25 01:08:10 my_comp kernel: [    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
Jul 25 01:08:10 my_comp kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 25 01:08:10 my_comp kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 25 01:08:10 my_comp kernel: [    0.000000] Hierarchical RCU implementation.
Jul 25 01:08:10 my_comp kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 25 01:08:10 my_comp kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Jul 25 01:08:10 my_comp kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
Jul 25 01:08:10 my_comp kernel: [    0.000000] CPU 0 irqstacks, hard=f3408000 soft=f340a000
Jul 25 01:08:10 my_comp kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 25 01:08:10 my_comp kernel: [    0.000000] Console: colour dummy device 80x25
Jul 25 01:08:10 my_comp kernel: [    0.000000] console [tty0] enabled
Jul 25 01:08:10 my_comp kernel: [    0.000000] hpet clockevent registered
Jul 25 01:08:10 my_comp kernel: [    0.000000] Fast TSC calibration using PIT
Jul 25 01:08:10 my_comp kernel: [    0.000000] Detected 2200.274 MHz processor.
Jul 25 01:08:10 my_comp kernel: [    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.54 BogoMIPS (lpj=8801096)
Jul 25 01:08:10 my_comp kernel: [    0.008011] pid_max: default: 32768 minimum: 301
Jul 25 01:08:10 my_comp kernel: [    0.008044] Security Framework initialized
Jul 25 01:08:10 my_comp kernel: [    0.008068] AppArmor: AppArmor initialized
Jul 25 01:08:10 my_comp kernel: [    0.008070] Yama: becoming mindful.
Jul 25 01:08:10 my_comp kernel: [    0.012037] Mount-cache hash table entries: 512
Jul 25 01:08:10 my_comp kernel: [    0.012210] Initializing cgroup subsys ns
Jul 25 01:08:10 my_comp kernel: [    0.012215] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Jul 25 01:08:10 my_comp kernel: [    0.012219] Initializing cgroup subsys cpuacct
Jul 25 01:08:10 my_comp kernel: [    0.012226] Initializing cgroup subsys memory
Jul 25 01:08:10 my_comp kernel: [    0.012237] Initializing cgroup subsys devices
Jul 25 01:08:10 my_comp kernel: [    0.012241] Initializing cgroup subsys freezer
Jul 25 01:08:10 my_comp kernel: [    0.012244] Initializing cgroup subsys net_cls
Jul 25 01:08:10 my_comp kernel: [    0.012247] Initializing cgroup subsys blkio
Jul 25 01:08:10 my_comp kernel: [    0.012289] CPU: Physical Processor ID: 0
Jul 25 01:08:10 my_comp kernel: [    0.012292] CPU: Processor Core ID: 0
Jul 25 01:08:10 my_comp kernel: [    0.012296] mce: CPU supports 5 MCE banks
Jul 25 01:08:10 my_comp kernel: [    0.015833] ACPI: Core revision 20110112
Jul 25 01:08:10 my_comp kernel: [    0.024016] ftrace: allocating 23640 entries in 47 pages
Jul 25 01:08:10 my_comp kernel: [    0.028104] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 25 01:08:10 my_comp kernel: [    0.028498] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 25 01:08:10 my_comp kernel: [    0.071876] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-74 stepping 01
Jul 25 01:08:10 my_comp kernel: [    0.072003] Performance Events: AMD PMU driver.
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... version:                0
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... bit width:              48
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... generic registers:      4
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... value mask:             0000ffffffffffff
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... max period:             00007fffffffffff
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... fixed-purpose events:   0
Jul 25 01:08:10 my_comp kernel: [    0.072003] ... event mask:             000000000000000f
Jul 25 01:08:10 my_comp kernel: [    0.072003] CPU 1 irqstacks, hard=f34d0000 soft=f34d2000
Jul 25 01:08:10 my_comp kernel: [    0.072003] Booting Node   0, Processors  #1
Jul 25 01:08:10 my_comp kernel: [    0.012000] Initializing CPU#1
Jul 25 01:08:10 my_comp kernel: [    0.160009] TSC synchronization [CPU#0 -> CPU#1]:
Jul 25 01:08:10 my_comp kernel: [    0.160009] Measured 239420922 cycles TSC warp between CPUs, turning off TSC clock.
Jul 25 01:08:10 my_comp kernel: [    0.160009] Marking TSC unstable due to check_tsc_sync_source failed
Jul 25 01:08:10 my_comp kernel: [    0.160022] Brought up 2 CPUs
Jul 25 01:08:10 my_comp kernel: [    0.160024] Total of 2 processors activated (8790.02 BogoMIPS).
Jul 25 01:08:10 my_comp kernel: [    0.160325] devtmpfs: initialized
Jul 25 01:08:10 my_comp kernel: [    0.161390] print_constraints: dummy: 
Jul 25 01:08:10 my_comp kernel: [    0.161454] Time:  1:07:42  Date: 07/25/11
Jul 25 01:08:10 my_comp kernel: [    0.161501] NET: Registered protocol family 16
Jul 25 01:08:10 my_comp kernel: [    0.161541] Trying to unpack rootfs image as initramfs...
Jul 25 01:08:10 my_comp kernel: [    0.161654] EISA bus registered
Jul 25 01:08:10 my_comp kernel: [    0.161699] TOM: 00000000c0000000 aka 3072M
Jul 25 01:08:10 my_comp kernel: [    0.161702] Fam 10h mmconf [e0000000, e0ffffff]
Jul 25 01:08:10 my_comp kernel: [    0.161804] Extended Config Space enabled on 0 nodes
Jul 25 01:08:10 my_comp kernel: [    0.161816] ACPI: bus type pci registered
Jul 25 01:08:10 my_comp kernel: [    0.161932] PCI: MMCONFIG for domain 0000 [bus 00-0f] at [mem 0xe0000000-0xe0ffffff] (base 0xe0000000)
Jul 25 01:08:10 my_comp kernel: [    0.161936] PCI: MMCONFIG at [mem 0xe0000000-0xe0ffffff] reserved in E820
Jul 25 01:08:10 my_comp kernel: [    0.161938] PCI: Using MMCONFIG for extended config space
Jul 25 01:08:10 my_comp kernel: [    0.161940] PCI: Using configuration type 1 for base access
Jul 25 01:08:10 my_comp kernel: [    0.161965] mtrr: your CPUs had inconsistent fixed MTRR settings
Jul 25 01:08:10 my_comp kernel: [    0.161967] mtrr: probably your BIOS does not setup all CPUs.
Jul 25 01:08:10 my_comp kernel: [    0.161968] mtrr: corrected configuration.
Jul 25 01:08:10 my_comp kernel: [    0.176386] bio: create slab <bio-0> at 0
Jul 25 01:08:10 my_comp kernel: [    0.178061] ACPI: EC: Look up EC in DSDT
Jul 25 01:08:10 my_comp kernel: [    0.179638] ACPI: Executed 1 blocks of module-level executable AML code
Jul 25 01:08:10 my_comp kernel: [    0.182000] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 25 01:08:10 my_comp kernel: [    0.212076] ACPI: Interpreter enabled
Jul 25 01:08:10 my_comp kernel: [    0.212081] ACPI: (supports S0 S3 S4 S5)
Jul 25 01:08:10 my_comp kernel: [    0.212106] ACPI: Using IOAPIC for interrupt routing
Jul 25 01:08:10 my_comp kernel: [    0.212628] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Jul 25 01:08:10 my_comp kernel: [    0.216165] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Jul 25 01:08:10 my_comp kernel: [    0.358652] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 25 01:08:10 my_comp kernel: [    0.358851] ACPI: No dock devices found.
Jul 25 01:08:10 my_comp kernel: [    0.358854] HEST: Table not found.
Jul 25 01:08:10 my_comp kernel: [    0.358858] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 25 01:08:10 my_comp kernel: [    0.359395] \_SB_.PCI0:_OSC request failed
Jul 25 01:08:10 my_comp kernel: [    0.359397] _OSC request data:1 8 1f 
Jul 25 01:08:10 my_comp kernel: [    0.359403] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 25 01:08:10 my_comp kernel: [    0.360386] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jul 25 01:08:10 my_comp kernel: [    0.360389] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jul 25 01:08:10 my_comp kernel: [    0.360392] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jul 25 01:08:10 my_comp kernel: [    0.360395] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Jul 25 01:08:10 my_comp kernel: [    0.360398] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Jul 25 01:08:10 my_comp kernel: [    0.360401] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Jul 25 01:08:10 my_comp kernel: [    0.360404] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Jul 25 01:08:10 my_comp kernel: [    0.360407] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Jul 25 01:08:10 my_comp kernel: [    0.360410] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Jul 25 01:08:10 my_comp kernel: [    0.360413] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Jul 25 01:08:10 my_comp kernel: [    0.360416] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Jul 25 01:08:10 my_comp kernel: [    0.360418] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Jul 25 01:08:10 my_comp kernel: [    0.360421] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Jul 25 01:08:10 my_comp kernel: [    0.360424] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Jul 25 01:08:10 my_comp kernel: [    0.360427] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Jul 25 01:08:10 my_comp kernel: [    0.360430] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
Jul 25 01:08:10 my_comp kernel: [    0.360433] pci_root PNP0A08:00: host bridge window [mem 0xe1000000-0xffffffff]
Jul 25 01:08:10 my_comp kernel: [    0.360441] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cebff]
Jul 25 01:08:10 my_comp kernel: [    0.360464] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
Jul 25 01:08:10 my_comp kernel: [    0.360538] pci 0000:00:01.0: [103c:9602] type 1 class 0x000604
Jul 25 01:08:10 my_comp kernel: [    0.360626] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
Jul 25 01:08:10 my_comp kernel: [    0.360670] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 25 01:08:10 my_comp kernel: [    0.360674] pci 0000:00:04.0: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.360695] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
Jul 25 01:08:10 my_comp kernel: [    0.360738] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 25 01:08:10 my_comp kernel: [    0.360742] pci 0000:00:05.0: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.360763] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
Jul 25 01:08:10 my_comp kernel: [    0.360806] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 25 01:08:10 my_comp kernel: [    0.360810] pci 0000:00:06.0: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.360830] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jul 25 01:08:10 my_comp kernel: [    0.360873] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul 25 01:08:10 my_comp kernel: [    0.360877] pci 0000:00:07.0: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.360952] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
Jul 25 01:08:10 my_comp kernel: [    0.360977] pci 0000:00:11.0: reg 10: [io  0x8038-0x803f]
Jul 25 01:08:10 my_comp kernel: [    0.360990] pci 0000:00:11.0: reg 14: [io  0x804c-0x804f]
Jul 25 01:08:10 my_comp kernel: [    0.361002] pci 0000:00:11.0: reg 18: [io  0x8030-0x8037]
Jul 25 01:08:10 my_comp kernel: [    0.361015] pci 0000:00:11.0: reg 1c: [io  0x8048-0x804b]
Jul 25 01:08:10 my_comp kernel: [    0.361027] pci 0000:00:11.0: reg 20: [io  0x8010-0x801f]
Jul 25 01:08:10 my_comp kernel: [    0.361040] pci 0000:00:11.0: reg 24: [mem 0xd2508000-0xd25083ff]
Jul 25 01:08:10 my_comp kernel: [    0.361097] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jul 25 01:08:10 my_comp kernel: [    0.361114] pci 0000:00:12.0: reg 10: [mem 0xd2507000-0xd2507fff]
Jul 25 01:08:10 my_comp kernel: [    0.361195] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
Jul 25 01:08:10 my_comp kernel: [    0.361213] pci 0000:00:12.1: reg 10: [mem 0xd2506000-0xd2506fff]
Jul 25 01:08:10 my_comp kernel: [    0.361301] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jul 25 01:08:10 my_comp kernel: [    0.361325] pci 0000:00:12.2: reg 10: [mem 0xd2508500-0xd25085ff]
Jul 25 01:08:10 my_comp kernel: [    0.361414] pci 0000:00:12.2: supports D1 D2
Jul 25 01:08:10 my_comp kernel: [    0.361416] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 25 01:08:10 my_comp kernel: [    0.361421] pci 0000:00:12.2: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.361448] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jul 25 01:08:10 my_comp kernel: [    0.361466] pci 0000:00:13.0: reg 10: [mem 0xd2505000-0xd2505fff]
Jul 25 01:08:10 my_comp kernel: [    0.361547] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
Jul 25 01:08:10 my_comp kernel: [    0.361564] pci 0000:00:13.1: reg 10: [mem 0xd2504000-0xd2504fff]
Jul 25 01:08:10 my_comp kernel: [    0.361652] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jul 25 01:08:10 my_comp kernel: [    0.361677] pci 0000:00:13.2: reg 10: [mem 0xd2508400-0xd25084ff]
Jul 25 01:08:10 my_comp kernel: [    0.361765] pci 0000:00:13.2: supports D1 D2
Jul 25 01:08:10 my_comp kernel: [    0.361768] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 25 01:08:10 my_comp kernel: [    0.361773] pci 0000:00:13.2: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.361804] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jul 25 01:08:10 my_comp kernel: [    0.361926] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jul 25 01:08:10 my_comp kernel: [    0.361947] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jul 25 01:08:10 my_comp kernel: [    0.361960] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jul 25 01:08:10 my_comp kernel: [    0.361972] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jul 25 01:08:10 my_comp kernel: [    0.361985] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jul 25 01:08:10 my_comp kernel: [    0.361997] pci 0000:00:14.1: reg 20: [io  0x8000-0x800f]
Jul 25 01:08:10 my_comp kernel: [    0.362060] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jul 25 01:08:10 my_comp kernel: [    0.362088] pci 0000:00:14.2: reg 10: [mem 0xd2500000-0xd2503fff 64bit]
Jul 25 01:08:10 my_comp kernel: [    0.362162] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 25 01:08:10 my_comp kernel: [    0.362167] pci 0000:00:14.2: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.362185] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jul 25 01:08:10 my_comp kernel: [    0.362280] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jul 25 01:08:10 my_comp kernel: [    0.362340] pci 0000:00:18.0: [1022:1300] type 0 class 0x000600
Jul 25 01:08:10 my_comp kernel: [    0.362374] pci 0000:00:18.1: [1022:1301] type 0 class 0x000600
Jul 25 01:08:10 my_comp kernel: [    0.362402] pci 0000:00:18.2: [1022:1302] type 0 class 0x000600
Jul 25 01:08:10 my_comp kernel: [    0.362431] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
Jul 25 01:08:10 my_comp kernel: [    0.362465] pci 0000:00:18.4: [1022:1304] type 0 class 0x000600
Jul 25 01:08:10 my_comp kernel: [    0.362571] pci 0000:01:05.0: [1002:9612] type 0 class 0x000300
Jul 25 01:08:10 my_comp kernel: [    0.362584] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.362592] pci 0000:01:05.0: reg 14: [io  0x7000-0x70ff]
Jul 25 01:08:10 my_comp kernel: [    0.362600] pci 0000:01:05.0: reg 18: [mem 0xd2400000-0xd240ffff]
Jul 25 01:08:10 my_comp kernel: [    0.362617] pci 0000:01:05.0: reg 24: [mem 0xd2300000-0xd23fffff]
Jul 25 01:08:10 my_comp kernel: [    0.362637] pci 0000:01:05.0: supports D1 D2
Jul 25 01:08:10 my_comp kernel: [    0.362654] pci 0000:01:05.1: [1002:960f] type 0 class 0x000403
Jul 25 01:08:10 my_comp kernel: [    0.362667] pci 0000:01:05.1: reg 10: [mem 0xd2410000-0xd2413fff]
Jul 25 01:08:10 my_comp kernel: [    0.362711] pci 0000:01:05.1: supports D1 D2
Jul 25 01:08:10 my_comp kernel: [    0.362794] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul 25 01:08:10 my_comp kernel: [    0.362800] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jul 25 01:08:10 my_comp kernel: [    0.362804] pci 0000:00:01.0:   bridge window [mem 0xd2300000-0xd24fffff]
Jul 25 01:08:10 my_comp kernel: [    0.362810] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.362848] pci 0000:00:04.0: PCI bridge to [bus 02-07]
Jul 25 01:08:10 my_comp kernel: [    0.362854] pci 0000:00:04.0:   bridge window [io  0x3000-0x6fff]
Jul 25 01:08:10 my_comp kernel: [    0.362858] pci 0000:00:04.0:   bridge window [mem 0xd1300000-0xd22fffff]
Jul 25 01:08:10 my_comp kernel: [    0.362863] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.362917] pci 0000:08:00.0: [197b:2382] type 0 class 0x000880
Jul 25 01:08:10 my_comp kernel: [    0.362936] pci 0000:08:00.0: reg 10: [mem 0xd1200300-0xd12003ff]
Jul 25 01:08:10 my_comp kernel: [    0.363006] pci 0000:08:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.363074] pci 0000:08:00.2: [197b:2381] type 0 class 0x000805
Jul 25 01:08:10 my_comp kernel: [    0.363093] pci 0000:08:00.2: reg 10: [mem 0xd1200200-0xd12002ff]
Jul 25 01:08:10 my_comp kernel: [    0.363224] pci 0000:08:00.3: [197b:2383] type 0 class 0x000880
Jul 25 01:08:10 my_comp kernel: [    0.363243] pci 0000:08:00.3: reg 10: [mem 0xd1200100-0xd12001ff]
Jul 25 01:08:10 my_comp kernel: [    0.363375] pci 0000:08:00.4: [197b:2384] type 0 class 0x000880
Jul 25 01:08:10 my_comp kernel: [    0.363394] pci 0000:08:00.4: reg 10: [mem 0xd1200000-0xd12000ff]
Jul 25 01:08:10 my_comp kernel: [    0.368043] pci 0000:00:05.0: PCI bridge to [bus 08-08]
Jul 25 01:08:10 my_comp kernel: [    0.368048] pci 0000:00:05.0:   bridge window [io  0xfffff000-0x0000] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.368052] pci 0000:00:05.0:   bridge window [mem 0xd1200000-0xd12fffff]
Jul 25 01:08:10 my_comp kernel: [    0.368058] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.368153] pci 0000:09:00.0: [14e4:4315] type 0 class 0x000280
Jul 25 01:08:10 my_comp kernel: [    0.368176] pci 0000:09:00.0: reg 10: [mem 0xd1100000-0xd1103fff 64bit]
Jul 25 01:08:10 my_comp kernel: [    0.368261] pci 0000:09:00.0: supports D1 D2
Jul 25 01:08:10 my_comp kernel: [    0.376072] pci 0000:00:06.0: PCI bridge to [bus 09-09]
Jul 25 01:08:10 my_comp kernel: [    0.376078] pci 0000:00:06.0:   bridge window [io  0xfffff000-0x0000] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.376082] pci 0000:00:06.0:   bridge window [mem 0xd1100000-0xd11fffff]
Jul 25 01:08:10 my_comp kernel: [    0.376088] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.376153] pci 0000:0a:00.0: [10ec:8136] type 0 class 0x000200
Jul 25 01:08:10 my_comp kernel: [    0.376170] pci 0000:0a:00.0: reg 10: [io  0x2000-0x20ff]
Jul 25 01:08:10 my_comp kernel: [    0.376197] pci 0000:0a:00.0: reg 18: [mem 0xd1010000-0xd1010fff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.376215] pci 0000:0a:00.0: reg 20: [mem 0xd1000000-0xd100ffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.376228] pci 0000:0a:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.376264] pci 0000:0a:00.0: supports D1 D2
Jul 25 01:08:10 my_comp kernel: [    0.376266] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 25 01:08:10 my_comp kernel: [    0.376276] pci 0000:0a:00.0: PME# disabled
Jul 25 01:08:10 my_comp kernel: [    0.384041] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
Jul 25 01:08:10 my_comp kernel: [    0.384047] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
Jul 25 01:08:10 my_comp kernel: [    0.384051] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.384057] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.384130] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384136] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
Jul 25 01:08:10 my_comp kernel: [    0.384142] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.384147] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.384151] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384154] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384157] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384160] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384163] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384166] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384169] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384172] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384175] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384178] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384182] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384185] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384188] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384191] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384194] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384197] pci 0000:00:14.4:   bridge window [mem 0xe1000000-0xffffffff] (subtractive decode)
Jul 25 01:08:10 my_comp kernel: [    0.384255] pci_bus 0000:00: on NUMA node 0
Jul 25 01:08:10 my_comp kernel: [    0.384259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384381] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Jul 25 01:08:10 my_comp kernel: [    0.384797] \_SB_.PCI0:_OSC request failed
Jul 25 01:08:10 my_comp kernel: [    0.384799] _OSC request data:1 1f 1f 
Jul 25 01:08:10 my_comp kernel: [    0.384804]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul 25 01:08:10 my_comp kernel: [    0.384839] \_SB_.PCI0:_OSC request failed
Jul 25 01:08:10 my_comp kernel: [    0.384841] _OSC request data:1 0 1d 
Jul 25 01:08:10 my_comp kernel: [    0.394810] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.394858] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.394903] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.394948] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.394993] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.395038] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.395083] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.395129] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 01:08:10 my_comp kernel: [    0.395276] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Jul 25 01:08:10 my_comp kernel: [    0.395283] vgaarb: loaded
Jul 25 01:08:10 my_comp kernel: [    0.395535] SCSI subsystem initialized
Jul 25 01:08:10 my_comp kernel: [    0.395616] libata version 3.00 loaded.
Jul 25 01:08:10 my_comp kernel: [    0.395676] usbcore: registered new interface driver usbfs
Jul 25 01:08:10 my_comp kernel: [    0.395690] usbcore: registered new interface driver hub
Jul 25 01:08:10 my_comp kernel: [    0.395722] usbcore: registered new device driver usb
Jul 25 01:08:10 my_comp kernel: [    0.395985] wmi: Mapper loaded
Jul 25 01:08:10 my_comp kernel: [    0.395987] PCI: Using ACPI for IRQ routing
Jul 25 01:08:10 my_comp kernel: [    0.395990] PCI: pci_cache_line_size set to 64 bytes
Jul 25 01:08:10 my_comp kernel: [    0.396297] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jul 25 01:08:10 my_comp kernel: [    0.396301] reserve RAM buffer: 00000000afd70000 - 00000000afffffff 
Jul 25 01:08:10 my_comp kernel: [    0.396304] reserve RAM buffer: 00000000afe58000 - 00000000afffffff 
Jul 25 01:08:10 my_comp kernel: [    0.396307] reserve RAM buffer: 00000000afeea000 - 00000000afffffff 
Jul 25 01:08:10 my_comp kernel: [    0.396310] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
Jul 25 01:08:10 my_comp kernel: [    0.396430] NetLabel: Initializing
Jul 25 01:08:10 my_comp kernel: [    0.396432] NetLabel:  domain hash size = 128
Jul 25 01:08:10 my_comp kernel: [    0.396434] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 25 01:08:10 my_comp kernel: [    0.396448] NetLabel:  unlabeled traffic allowed by default
Jul 25 01:08:10 my_comp kernel: [    0.396527] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 25 01:08:10 my_comp kernel: [    0.396533] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 25 01:08:10 my_comp kernel: [    0.398565] Switching to clocksource hpet
Jul 25 01:08:10 my_comp kernel: [    0.398797] Switched to NOHz mode on CPU #0
Jul 25 01:08:10 my_comp kernel: [    0.398583] Switched to NOHz mode on CPU #1
Jul 25 01:08:10 my_comp kernel: [    0.404811] AppArmor: AppArmor Filesystem Enabled
Jul 25 01:08:10 my_comp kernel: [    0.404853] pnp: PnP ACPI init
Jul 25 01:08:10 my_comp kernel: [    0.404878] ACPI: bus type pnp registered
Jul 25 01:08:10 my_comp kernel: [    0.405432] pnp 00:00: [bus 00-ff]
Jul 25 01:08:10 my_comp kernel: [    0.405436] pnp 00:00: [io  0x0000-0x0cf7 window]
Jul 25 01:08:10 my_comp kernel: [    0.405439] pnp 00:00: [io  0x0d00-0xffff window]
Jul 25 01:08:10 my_comp kernel: [    0.405442] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jul 25 01:08:10 my_comp kernel: [    0.405444] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Jul 25 01:08:10 my_comp kernel: [    0.405447] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Jul 25 01:08:10 my_comp kernel: [    0.405453] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Jul 25 01:08:10 my_comp kernel: [    0.405456] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Jul 25 01:08:10 my_comp kernel: [    0.405459] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jul 25 01:08:10 my_comp kernel: [    0.405461] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  ModemManager (version 0.4) starting...
Jul 25 01:08:10 my_comp kernel: [    0.405464] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Jul 25 01:08:10 my_comp kernel: [    0.405467] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Jul 25 01:08:10 my_comp kernel: [    0.405470] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Jul 25 01:08:10 my_comp kernel: [    0.405472] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Jul 25 01:08:10 my_comp kernel: [    0.405475] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Jul 25 01:08:10 my_comp kernel: [    0.405478] pnp 00:00: [mem 0x000ec000-0x000effff window]
Jul 25 01:08:10 my_comp kernel: [    0.405480] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
Jul 25 01:08:10 my_comp kernel: [    0.405483] pnp 00:00: [mem 0xe1000000-0xffffffff window]
Jul 25 01:08:10 my_comp kernel: [    0.405486] pnp 00:00: [io  0x0cf8-0x0cff]
Jul 25 01:08:10 my_comp kernel: [    0.405582] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jul 25 01:08:10 my_comp kernel: [    0.405634] pnp 00:01: [mem 0xfec00000-0xfec00fff]
Jul 25 01:08:10 my_comp kernel: [    0.405636] pnp 00:01: [mem 0xfee00000-0xfee00fff]
Jul 25 01:08:10 my_comp kernel: [    0.405711] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 25 01:08:10 my_comp kernel: [    0.405714] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.405718] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 01:08:10 my_comp kernel: [    0.405871] pnp 00:02: [io  0x0000-0x000f]
Jul 25 01:08:10 my_comp kernel: [    0.405874] pnp 00:02: [io  0x0081-0x008f]
Jul 25 01:08:10 my_comp kernel: [    0.405876] pnp 00:02: [io  0x00c0-0x00df]
Jul 25 01:08:10 my_comp kernel: [    0.405879] pnp 00:02: [dma 4]
Jul 25 01:08:10 my_comp kernel: [    0.405919] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 25 01:08:10 my_comp kernel: [    0.405929] pnp 00:03: [io  0x00f0-0x00fe]
Jul 25 01:08:10 my_comp kernel: [    0.405977] pnp 00:03: [irq 13]
Jul 25 01:08:10 my_comp kernel: [    0.406017] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 25 01:08:10 my_comp kernel: [    0.406081] pnp 00:04: [io  0x0070-0x0071]
Jul 25 01:08:10 my_comp kernel: [    0.406118] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 25 01:08:10 my_comp kernel: [    0.406128] pnp 00:05: [io  0x0061]
Jul 25 01:08:10 my_comp kernel: [    0.406165] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Jul 25 01:08:10 my_comp kernel: [    0.406177] pnp 00:06: [io  0x0060]
Jul 25 01:08:10 my_comp kernel: [    0.406179] pnp 00:06: [io  0x0064]
Jul 25 01:08:10 my_comp kernel: [    0.406181] pnp 00:06: [io  0x0068]
Jul 25 01:08:10 my_comp kernel: [    0.406183] pnp 00:06: [io  0x006c]
Jul 25 01:08:10 my_comp kernel: [    0.406223] pnp 00:06: [irq 1]
Jul 25 01:08:10 my_comp kernel: [    0.406263] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 25 01:08:10 my_comp kernel: [    0.406309] pnp 00:07: [irq 12]
Jul 25 01:08:10 my_comp kernel: [    0.406349] pnp 00:07: Plug and Play ACPI device, IDs AUI0216 SYN0153 AUI0217 PNP0f13 (active)
Jul 25 01:08:10 my_comp kernel: [    0.406362] pnp 00:08: [io  0x0010-0x001f]
Jul 25 01:08:10 my_comp kernel: [    0.406365] pnp 00:08: [io  0x002e-0x002f]
Jul 25 01:08:10 my_comp kernel: [    0.406367] pnp 00:08: [io  0x0072-0x0073]
Jul 25 01:08:10 my_comp kernel: [    0.406369] pnp 00:08: [io  0x0080]
Jul 25 01:08:10 my_comp kernel: [    0.406371] pnp 00:08: [io  0x00b0-0x00b1]
Jul 25 01:08:10 my_comp kernel: [    0.406374] pnp 00:08: [io  0x0092]
Jul 25 01:08:10 my_comp kernel: [    0.406376] pnp 00:08: [io  0x0400-0x04cf]
Jul 25 01:08:10 my_comp kernel: [    0.406378] pnp 00:08: [io  0x04d0-0x04d1]
Jul 25 01:08:10 my_comp kernel: [    0.406380] pnp 00:08: [io  0x04d6]
Jul 25 01:08:10 my_comp kernel: [    0.406383] pnp 00:08: [io  0x0680-0x06ff]
Jul 25 01:08:10 my_comp kernel: [    0.406385] pnp 00:08: [io  0x077a]
Jul 25 01:08:10 my_comp kernel: [    0.406387] pnp 00:08: [io  0x0c00-0x0c01]
Jul 25 01:08:10 my_comp kernel: [    0.406389] pnp 00:08: [io  0x0c14]
Jul 25 01:08:10 my_comp kernel: [    0.406391] pnp 00:08: [io  0x0c50-0x0c52]
Jul 25 01:08:10 my_comp kernel: [    0.406394] pnp 00:08: [io  0x0c6c]
Jul 25 01:08:10 my_comp kernel: [    0.406396] pnp 00:08: [io  0x0c6f]
Jul 25 01:08:10 my_comp kernel: [    0.406398] pnp 00:08: [io  0x0cd0-0x0cdb]
Jul 25 01:08:10 my_comp kernel: [    0.406476] system 00:08: [io  0x0400-0x04cf] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406479] system 00:08: [io  0x04d0-0x04d1] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406482] system 00:08: [io  0x04d6] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406485] system 00:08: [io  0x0680-0x06ff] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406488] system 00:08: [io  0x077a] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406491] system 00:08: [io  0x0c00-0x0c01] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406494] system 00:08: [io  0x0c14] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406497] system 00:08: [io  0x0c50-0x0c52] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406500] system 00:08: [io  0x0c6c] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406503] system 00:08: [io  0x0c6f] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406506] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406509] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 01:08:10 my_comp kernel: [    0.406525] pnp 00:09: [mem 0x000e0000-0x000fffff]
Jul 25 01:08:10 my_comp kernel: [    0.406527] pnp 00:09: [mem 0xfff00000-0xffffffff]
Jul 25 01:08:10 my_comp kernel: [    0.406595] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Jul 25 01:08:10 my_comp kernel: [    0.406599] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
Jul 25 01:08:10 my_comp kernel: [    0.406602] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 25 01:08:10 my_comp kernel: [    0.452130] pnp 00:0a: [io  0xfd60-0xfd63]
Jul 25 01:08:10 my_comp kernel: [    0.452170] pnp 00:0a: [irq 4]
Jul 25 01:08:10 my_comp kernel: [    0.452217] pnp 00:0a: Plug and Play ACPI device, IDs ENE0100 (active)
Jul 25 01:08:10 my_comp kernel: [    0.452523] pnp: PnP ACPI: found 11 devices
Jul 25 01:08:10 my_comp kernel: [    0.452525] ACPI: ACPI bus type pnp unregistered
Jul 25 01:08:10 my_comp kernel: [    0.452528] PnPBIOS: Disabled by ACPI PNP
Jul 25 01:08:10 my_comp kernel: [    0.489470] pci 0000:08:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489478] pci 0000:0a:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489560] pci 0000:00:05.0: BAR 15: assigned [mem 0xd2600000-0xd26fffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489567] pci 0000:00:07.0: BAR 14: assigned [mem 0xd2700000-0xd27fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489571] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul 25 01:08:10 my_comp kernel: [    0.489575] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489580] pci 0000:00:01.0:   bridge window [mem 0xd2300000-0xd24fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489584] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.489590] pci 0000:00:04.0: PCI bridge to [bus 02-07]
Jul 25 01:08:10 my_comp kernel: [    0.489593] pci 0000:00:04.0:   bridge window [io  0x3000-0x6fff]
Jul 25 01:08:10 my_comp kernel: [    0.489598] pci 0000:00:04.0:   bridge window [mem 0xd1300000-0xd22fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489602] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.489609] pci 0000:08:00.0: BAR 6: assigned [mem 0xd2600000-0xd260ffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489612] pci 0000:00:05.0: PCI bridge to [bus 08-08]
Jul 25 01:08:10 my_comp kernel: [    0.489614] pci 0000:00:05.0:   bridge window [io  disabled]
Jul 25 01:08:10 my_comp kernel: [    0.489619] pci 0000:00:05.0:   bridge window [mem 0xd1200000-0xd12fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489623] pci 0000:00:05.0:   bridge window [mem 0xd2600000-0xd26fffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489629] pci 0000:00:06.0: PCI bridge to [bus 09-09]
Jul 25 01:08:10 my_comp kernel: [    0.489631] pci 0000:00:06.0:   bridge window [io  disabled]
Jul 25 01:08:10 my_comp kernel: [    0.489636] pci 0000:00:06.0:   bridge window [mem 0xd1100000-0xd11fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489640] pci 0000:00:06.0:   bridge window [mem pref disabled]
Jul 25 01:08:10 my_comp kernel: [    0.489646] pci 0000:0a:00.0: BAR 6: assigned [mem 0xd1020000-0xd103ffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489649] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
Jul 25 01:08:10 my_comp kernel: [    0.489652] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
Jul 25 01:08:10 my_comp kernel: [    0.489657] pci 0000:00:07.0:   bridge window [mem 0xd2700000-0xd27fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489661] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.489667] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
Jul 25 01:08:10 my_comp kernel: [    0.489704] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
Jul 25 01:08:10 my_comp kernel: [    0.489711] pci 0000:00:14.4:   bridge window [mem disabled]
Jul 25 01:08:10 my_comp kernel: [    0.489716] pci 0000:00:14.4:   bridge window [mem pref disabled]
Jul 25 01:08:10 my_comp kernel: [    0.489731] pci 0000:00:01.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.489748] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 01:08:10 my_comp kernel: [    0.489751] pci 0000:00:04.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.489761] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 01:08:10 my_comp kernel: [    0.489765] pci 0000:00:05.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.489774] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 01:08:10 my_comp kernel: [    0.489777] pci 0000:00:06.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.489786] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 25 01:08:10 my_comp kernel: [    0.489790] pci 0000:00:07.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.489799] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 25 01:08:10 my_comp kernel: [    0.489802] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 25 01:08:10 my_comp kernel: [    0.489804] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 25 01:08:10 my_comp kernel: [    0.489807] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 25 01:08:10 my_comp kernel: [    0.489810] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489813] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 25 01:08:10 my_comp kernel: [    0.489816] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
Jul 25 01:08:10 my_comp kernel: [    0.489818] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489821] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
Jul 25 01:08:10 my_comp kernel: [    0.489824] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
Jul 25 01:08:10 my_comp kernel: [    0.489827] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
Jul 25 01:08:10 my_comp kernel: [    0.489830] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489833] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
Jul 25 01:08:10 my_comp kernel: [    0.489835] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
Jul 25 01:08:10 my_comp kernel: [    0.489838] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
Jul 25 01:08:10 my_comp kernel: [    0.489841] pci_bus 0000:00: resource 19 [mem 0xe1000000-0xffffffff]
Jul 25 01:08:10 my_comp kernel: [    0.489844] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489847] pci_bus 0000:01: resource 1 [mem 0xd2300000-0xd24fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489850] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.489853] pci_bus 0000:02: resource 0 [io  0x3000-0x6fff]
Jul 25 01:08:10 my_comp kernel: [    0.489856] pci_bus 0000:02: resource 1 [mem 0xd1300000-0xd22fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489859] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.489862] pci_bus 0000:08: resource 1 [mem 0xd1200000-0xd12fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489865] pci_bus 0000:08: resource 2 [mem 0xd2600000-0xd26fffff pref]
Jul 25 01:08:10 my_comp kernel: [    0.489868] pci_bus 0000:09: resource 1 [mem 0xd1100000-0xd11fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489871] pci_bus 0000:0a: resource 0 [io  0x2000-0x2fff]
Jul 25 01:08:10 my_comp kernel: [    0.489874] pci_bus 0000:0a: resource 1 [mem 0xd2700000-0xd27fffff]
Jul 25 01:08:10 my_comp kernel: [    0.489876] pci_bus 0000:0a: resource 2 [mem 0xd1000000-0xd10fffff 64bit pref]
Jul 25 01:08:10 my_comp kernel: [    0.489879] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
Jul 25 01:08:10 my_comp kernel: [    0.489882] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
Jul 25 01:08:10 my_comp kernel: [    0.489885] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
Jul 25 01:08:10 my_comp kernel: [    0.489888] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
Jul 25 01:08:10 my_comp kernel: [    0.489891] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 25 01:08:10 my_comp kernel: [    0.489893] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489896] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 25 01:08:10 my_comp kernel: [    0.489899] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
Jul 25 01:08:10 my_comp kernel: [    0.489902] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489905] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
Jul 25 01:08:10 my_comp kernel: [    0.489908] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
Jul 25 01:08:10 my_comp kernel: [    0.489910] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
Jul 25 01:08:10 my_comp kernel: [    0.489913] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
Jul 25 01:08:10 my_comp kernel: [    0.489916] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
Jul 25 01:08:10 my_comp kernel: [    0.489919] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
Jul 25 01:08:10 my_comp kernel: [    0.489922] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
Jul 25 01:08:10 my_comp kernel: [    0.489925] pci_bus 0000:80: resource 19 [mem 0xe1000000-0xffffffff]
Jul 25 01:08:10 my_comp kernel: [    0.489970] NET: Registered protocol family 2
Jul 25 01:08:10 my_comp kernel: [    0.490054] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.490357] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.491117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.491477] TCP: Hash tables configured (established 131072 bind 65536)
Jul 25 01:08:10 my_comp kernel: [    0.491480] TCP reno registered
Jul 25 01:08:10 my_comp kernel: [    0.491484] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.491498] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.491622] NET: Registered protocol family 1
Jul 25 01:08:10 my_comp kernel: [    0.491637] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Jul 25 01:08:10 my_comp kernel: [    0.491803] pci 0000:01:05.0: Boot video device
Jul 25 01:08:10 my_comp kernel: [    0.491872] PCI: CLS 64 bytes, default 64
Jul 25 01:08:10 my_comp kernel: [    0.491936] Simple Boot Flag at 0x44 set to 0x1
Jul 25 01:08:10 my_comp kernel: [    0.492290] cpufreq-nforce2: No nForce2 chipset.
Jul 25 01:08:10 my_comp kernel: [    0.492448] audit: initializing netlink socket (disabled)
Jul 25 01:08:10 my_comp kernel: [    0.492460] type=2000 audit(1311556062.492:1): initialized
Jul 25 01:08:10 my_comp kernel: [    0.503199] highmem bounce pool size: 64 pages
Jul 25 01:08:10 my_comp kernel: [    0.503205] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 25 01:08:10 my_comp kernel: [    0.505183] VFS: Disk quotas dquot_6.5.2
Jul 25 01:08:10 my_comp kernel: [    0.505245] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 25 01:08:10 my_comp kernel: [    0.506003] fuse init (API version 7.16)
Jul 25 01:08:10 my_comp kernel: [    0.506104] msgmni has been set to 1647
Jul 25 01:08:10 my_comp kernel: [    0.506429] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 25 01:08:10 my_comp kernel: [    0.506493] io scheduler noop registered
Jul 25 01:08:10 my_comp kernel: [    0.506496] io scheduler deadline registered
Jul 25 01:08:10 my_comp kernel: [    0.506514] io scheduler cfq registered (default)
Jul 25 01:08:10 my_comp kernel: [    0.506688] pcieport 0000:00:04.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.506736] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
Jul 25 01:08:10 my_comp kernel: [    0.506797] pcieport 0000:00:05.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.506832] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
Jul 25 01:08:10 my_comp kernel: [    0.506888] pcieport 0000:00:06.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.506923] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
Jul 25 01:08:10 my_comp kernel: [    0.506978] pcieport 0000:00:07.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    0.507013] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
Jul 25 01:08:10 my_comp kernel: [    0.507110] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 25 01:08:10 my_comp kernel: [    0.507140] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 25 01:08:10 my_comp kernel: [    0.512396] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 25 01:08:10 my_comp kernel: [    0.515569] ACPI: AC Adapter [ACAD] (on-line)
Jul 25 01:08:10 my_comp kernel: [    0.515638] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jul 25 01:08:10 my_comp kernel: [    0.515645] ACPI: Power Button [PWRB]
Jul 25 01:08:10 my_comp kernel: [    0.515705] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Jul 25 01:08:10 my_comp kernel: [    0.515801] ACPI: Lid Switch [LID]
Jul 25 01:08:10 my_comp kernel: [    0.515850] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 25 01:08:10 my_comp kernel: [    0.515853] ACPI: Power Button [PWRF]
Jul 25 01:08:10 my_comp kernel: [    0.516140] ACPI: acpi_idle registered with cpuidle
Jul 25 01:08:10 my_comp kernel: [    0.636707] thermal LNXTHERM:00: registered as thermal_zone0
Jul 25 01:08:10 my_comp kernel: [    0.636710] ACPI: Thermal Zone [TZ01] (67 C)
Jul 25 01:08:10 my_comp kernel: [    0.636737] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 25 01:08:10 my_comp kernel: [    0.636801] ERST: Table is not found!
Jul 25 01:08:10 my_comp kernel: [    0.636916] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 25 01:08:10 my_comp kernel: [    0.637412] isapnp: Scanning for PnP cards...
Jul 25 01:08:10 my_comp kernel: [    0.650189] Freeing initrd memory: 18336k freed
Jul 25 01:08:10 my_comp kernel: [    0.688070] ACPI: Battery Slot [BAT0] (battery absent)
Jul 25 01:08:10 my_comp kernel: [    1.021906] isapnp: No Plug & Play device found
Jul 25 01:08:10 my_comp kernel: [    1.160416] Linux agpgart interface v0.103
Jul 25 01:08:10 my_comp kernel: [    1.161814] brd: module loaded
Jul 25 01:08:10 my_comp kernel: [    1.162460] loop: module loaded
Jul 25 01:08:10 my_comp kernel: [    1.162580] i2c-core: driver [adp5520] using legacy suspend method
Jul 25 01:08:10 my_comp kernel: [    1.162583] i2c-core: driver [adp5520] using legacy resume method
Jul 25 01:08:10 my_comp kernel: [    1.162789] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 01:08:10 my_comp kernel: [    1.162873] pata_acpi 0000:00:14.1: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.163304] Fixed MDIO Bus: probed
Jul 25 01:08:10 my_comp kernel: [    1.163356] PPP generic driver version 2.4.2
Jul 25 01:08:10 my_comp kernel: [    1.163401] tun: Universal TUN/TAP device driver, 1.6
Jul 25 01:08:10 my_comp kernel: [    1.163403] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 25 01:08:10 my_comp kernel: [    1.163497] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 25 01:08:10 my_comp kernel: [    1.163552] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 25 01:08:10 my_comp kernel: [    1.163576] ehci_hcd 0000:00:12.2: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.163581] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 25 01:08:10 my_comp kernel: [    1.163621] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 25 01:08:10 my_comp kernel: [    1.163739] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 25 01:08:10 my_comp kernel: [    1.163763] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Jul 25 01:08:10 my_comp kernel: [    1.163780] ehci_hcd 0000:00:12.2: debug port 1
Jul 25 01:08:10 my_comp kernel: [    1.163816] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2508500
Jul 25 01:08:10 my_comp kernel: [    1.172055] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 25 01:08:10 my_comp kernel: [    1.172211] hub 1-0:1.0: USB hub found
Jul 25 01:08:10 my_comp kernel: [    1.172216] hub 1-0:1.0: 6 ports detected
Jul 25 01:08:10 my_comp kernel: [    1.172385] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 25 01:08:10 my_comp kernel: [    1.172413] ehci_hcd 0000:00:13.2: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.172418] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 25 01:08:10 my_comp kernel: [    1.172465] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 25 01:08:10 my_comp kernel: [    1.172544] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 25 01:08:10 my_comp kernel: [    1.172566] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Jul 25 01:08:10 my_comp kernel: [    1.172582] ehci_hcd 0000:00:13.2: debug port 1
Jul 25 01:08:10 my_comp kernel: [    1.172614] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2508400
Jul 25 01:08:10 my_comp kernel: [    1.184061] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 25 01:08:10 my_comp kernel: [    1.184210] hub 2-0:1.0: USB hub found
Jul 25 01:08:10 my_comp kernel: [    1.184216] hub 2-0:1.0: 6 ports detected
Jul 25 01:08:10 my_comp kernel: [    1.184366] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 25 01:08:10 my_comp kernel: [    1.184415] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 01:08:10 my_comp kernel: [    1.184433] ohci_hcd 0000:00:12.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.184438] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 25 01:08:10 my_comp kernel: [    1.184484] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 25 01:08:10 my_comp kernel: [    1.184577] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2507000
Jul 25 01:08:10 my_comp kernel: [    1.244162] hub 3-0:1.0: USB hub found
Jul 25 01:08:10 my_comp kernel: [    1.244203] hub 3-0:1.0: 3 ports detected
Jul 25 01:08:10 my_comp kernel: [    1.244293] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 01:08:10 my_comp kernel: [    1.244308] ohci_hcd 0000:00:12.1: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.244312] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 25 01:08:10 my_comp kernel: [    1.244353] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 25 01:08:10 my_comp kernel: [    1.244432] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2506000
Jul 25 01:08:10 my_comp kernel: [    1.304163] hub 4-0:1.0: USB hub found
Jul 25 01:08:10 my_comp kernel: [    1.304204] hub 4-0:1.0: 3 ports detected
Jul 25 01:08:10 my_comp kernel: [    1.304295] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 01:08:10 my_comp kernel: [    1.304309] ohci_hcd 0000:00:13.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.304313] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 25 01:08:10 my_comp kernel: [    1.304364] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 25 01:08:10 my_comp kernel: [    1.308089] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2505000
Jul 25 01:08:10 my_comp kernel: [    1.368161] hub 5-0:1.0: USB hub found
Jul 25 01:08:10 my_comp kernel: [    1.368201] hub 5-0:1.0: 3 ports detected
Jul 25 01:08:10 my_comp kernel: [    1.368293] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 01:08:10 my_comp kernel: [    1.368308] ohci_hcd 0000:00:13.1: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.368312] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 25 01:08:10 my_comp kernel: [    1.368353] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 25 01:08:10 my_comp kernel: [    1.372078] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2504000
Jul 25 01:08:10 my_comp kernel: [    1.432153] hub 6-0:1.0: USB hub found
Jul 25 01:08:10 my_comp kernel: [    1.432160] hub 6-0:1.0: 3 ports detected
Jul 25 01:08:10 my_comp kernel: [    1.432249] uhci_hcd: USB Universal Host Controller Interface driver
Jul 25 01:08:10 my_comp kernel: [    1.432361] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 25 01:08:10 my_comp kernel: [    1.464763] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 25 01:08:10 my_comp kernel: [    1.464771] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 25 01:08:10 my_comp kernel: [    1.464917] mousedev: PS/2 mouse device common for all mice
Jul 25 01:08:10 my_comp kernel: [    1.466938] rtc_cmos 00:04: RTC can wake from S4
Jul 25 01:08:10 my_comp kernel: [    1.467035] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jul 25 01:08:10 my_comp kernel: [    1.467099] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Jul 25 01:08:10 my_comp kernel: [    1.467206] device-mapper: uevent: version 1.0.3
Jul 25 01:08:10 my_comp kernel: [    1.467305] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Jul 25 01:08:10 my_comp kernel: [    1.467479] device-mapper: multipath: version 1.2.0 loaded
Jul 25 01:08:10 my_comp kernel: [    1.467482] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 25 01:08:10 my_comp kernel: [    1.467577] EISA: Probing bus 0 at eisa.0
Jul 25 01:08:10 my_comp kernel: [    1.467580] EISA: Cannot allocate resource for mainboard
Jul 25 01:08:10 my_comp kernel: [    1.467583] Cannot allocate resource for EISA slot 1
Jul 25 01:08:10 my_comp kernel: [    1.467586] Cannot allocate resource for EISA slot 2
Jul 25 01:08:10 my_comp kernel: [    1.467588] Cannot allocate resource for EISA slot 3
Jul 25 01:08:10 my_comp kernel: [    1.467591] Cannot allocate resource for EISA slot 4
Jul 25 01:08:10 my_comp kernel: [    1.467593] Cannot allocate resource for EISA slot 5
Jul 25 01:08:10 my_comp kernel: [    1.467596] Cannot allocate resource for EISA slot 6
Jul 25 01:08:10 my_comp kernel: [    1.467598] Cannot allocate resource for EISA slot 7
Jul 25 01:08:10 my_comp kernel: [    1.467600] Cannot allocate resource for EISA slot 8
Jul 25 01:08:10 my_comp kernel: [    1.467603] EISA: Detected 0 cards.
Jul 25 01:08:10 my_comp kernel: [    1.467745] cpuidle: using governor ladder
Jul 25 01:08:10 my_comp kernel: [    1.467747] cpuidle: using governor menu
Jul 25 01:08:10 my_comp kernel: [    1.468113] TCP cubic registered
Jul 25 01:08:10 my_comp kernel: [    1.468254] NET: Registered protocol family 10
Jul 25 01:08:10 my_comp kernel: [    1.468871] NET: Registered protocol family 17
Jul 25 01:08:10 my_comp kernel: [    1.468895] Registering the dns_resolver key type
Jul 25 01:08:10 my_comp kernel: [    1.468962] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-74 (2 cpu cores) (version 2.20.00)
Jul 25 01:08:10 my_comp kernel: [    1.469016] powernow-k8:    0 : pstate 0 (2200 MHz)
Jul 25 01:08:10 my_comp kernel: [    1.469018] powernow-k8:    1 : pstate 1 (1100 MHz)
Jul 25 01:08:10 my_comp kernel: [    1.469021] powernow-k8:    2 : pstate 2 (550 MHz)
Jul 25 01:08:10 my_comp kernel: [    1.470268] Using IPI No-Shortcut mode
Jul 25 01:08:10 my_comp kernel: [    1.470393] PM: Hibernation image not present or could not be loaded.
Jul 25 01:08:10 my_comp kernel: [    1.470407] registered taskstats version 1
Jul 25 01:08:10 my_comp kernel: [    1.470910]   Magic number: 3:53:105
Jul 25 01:08:10 my_comp kernel: [    1.470924] usbmon usbmon1: hash matches
Jul 25 01:08:10 my_comp kernel: [    1.471080] rtc_cmos 00:04: setting system clock to 2011-07-25 01:07:43 UTC (1311556063)
Jul 25 01:08:10 my_comp kernel: [    1.471084] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 25 01:08:10 my_comp kernel: [    1.471086] EDD information not available.
Jul 25 01:08:10 my_comp kernel: [    1.471226] Freeing unused kernel memory: 700k freed
Jul 25 01:08:10 my_comp kernel: [    1.471715] Write protecting the kernel text: 5192k
Jul 25 01:08:10 my_comp kernel: [    1.471801] Write protecting the kernel read-only data: 2148k
Jul 25 01:08:10 my_comp kernel: [    1.484089] usb 1-6: new high speed USB device using ehci_hcd and address 2
Jul 25 01:08:10 my_comp kernel: [    1.502547] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 25 01:08:10 my_comp kernel: [    1.508273] <30>udev[68]: starting version 167
Jul 25 01:08:10 my_comp kernel: [    1.604170] scsi0 : pata_atiixp
Jul 25 01:08:10 my_comp kernel: [    1.608028] scsi1 : pata_atiixp
Jul 25 01:08:10 my_comp kernel: [    1.608665] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8000 irq 14
Jul 25 01:08:10 my_comp kernel: [    1.608668] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8008 irq 15
Jul 25 01:08:10 my_comp kernel: [    1.622376] ahci 0000:00:11.0: version 3.0
Jul 25 01:08:10 my_comp kernel: [    1.622414] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 25 01:08:10 my_comp kernel: [    1.622597] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0xf impl SATA mode
Jul 25 01:08:10 my_comp kernel: [    1.622602] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc sxs 
Jul 25 01:08:10 my_comp kernel: [    1.625044] scsi2 : ahci
Jul 25 01:08:10 my_comp kernel: [    1.625335] scsi3 : ahci
Jul 25 01:08:10 my_comp kernel: [    1.627694] scsi4 : ahci
Jul 25 01:08:10 my_comp kernel: [    1.628684] scsi5 : ahci
Jul 25 01:08:10 my_comp kernel: [    1.630008] scsi6 : ahci
Jul 25 01:08:10 my_comp kernel: [    1.631632] scsi7 : ahci
Jul 25 01:08:10 my_comp kernel: [    1.632079] ata3: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508100 irq 22
Jul 25 01:08:10 my_comp kernel: [    1.632084] ata4: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508180 irq 22
Jul 25 01:08:10 my_comp kernel: [    1.632089] ata5: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508200 irq 22
Jul 25 01:08:10 my_comp kernel: [    1.632093] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
Jul 25 01:08:10 my_comp kernel: [    1.632096] ata7: DUMMY
Jul 25 01:08:10 my_comp kernel: [    1.632097] ata8: DUMMY
Jul 25 01:08:10 my_comp kernel: [    1.689803] sdhci: Secure Digital Host Controller Interface driver
Jul 25 01:08:10 my_comp kernel: [    1.689807] sdhci: Copyright(c) Pierre Ossman
Jul 25 01:08:10 my_comp kernel: [    1.704948] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 25 01:08:10 my_comp kernel: [    1.704996] r8169 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 25 01:08:10 my_comp kernel: [    1.705044] r8169 0000:0a:00.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.705101] r8169 0000:0a:00.0: irq 44 for MSI/MSI-X
Jul 25 01:08:10 my_comp kernel: [    1.705663] r8169 0000:0a:00.0: eth0: RTL8102e at 0xf806a000, 00:23:5a:36:b6:e4, XID 04c00000 IRQ 44
Jul 25 01:08:10 my_comp kernel: [    1.708346] sdhci-pci 0000:08:00.0: SDHCI controller found [197b:2382] (rev 0)
Jul 25 01:08:10 my_comp kernel: [    1.708370] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 01:08:10 my_comp kernel: [    1.708426] sdhci-pci 0000:08:00.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [    1.708441] mmc0: no vmmc regulator found
Jul 25 01:08:10 my_comp kernel: [    1.708539] Registered led device: mmc0::
Jul 25 01:08:10 my_comp kernel: [    1.708632] mmc0: SDHCI controller on PCI [0000:08:00.0] using ADMA
Jul 25 01:08:10 my_comp kernel: [    1.708645] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
Jul 25 01:08:10 my_comp kernel: [    1.708659] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 01:08:10 my_comp kernel: [    1.708731] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
Jul 25 01:08:10 my_comp kernel: [    1.708739] sdhci-pci 0000:08:00.2: PCI INT A disabled
Jul 25 01:08:10 my_comp kernel: [    1.709381] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Jul 25 01:08:10 my_comp kernel: [    1.714169] acpi device:04: registered as cooling_device2
Jul 25 01:08:10 my_comp kernel: [    1.714303] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4
Jul 25 01:08:10 my_comp kernel: [    1.714383] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul 25 01:08:10 my_comp kernel: [    1.952097] ata4: SATA link down (SStatus 0 SControl 300)
Jul 25 01:08:10 my_comp kernel: [    1.952139] ata5: SATA link down (SStatus 0 SControl 300)
Jul 25 01:08:10 my_comp kernel: [    2.124052] ata3: softreset failed (device not ready)
Jul 25 01:08:10 my_comp kernel: [    2.124056] ata3: applying SB600 PMP SRST workaround and retrying
Jul 25 01:08:10 my_comp kernel: [    2.296062] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 25 01:08:10 my_comp kernel: [    2.347072] ata3.00: ATA-8: ST9320325AS, 0001SDM1, max UDMA/133
Jul 25 01:08:10 my_comp kernel: [    2.347077] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 25 01:08:10 my_comp kernel: [    2.349282] ata3.00: configured for UDMA/133
Jul 25 01:08:10 my_comp kernel: [    2.349535] scsi 2:0:0:0: Direct-Access     ATA      ST9320325AS      0001 PQ: 0 ANSI: 5
Jul 25 01:08:10 my_comp kernel: [    2.349767] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jul 25 01:08:10 my_comp kernel: [    2.349794] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jul 25 01:08:10 my_comp kernel: [    2.349877] sd 2:0:0:0: [sda] Write Protect is off
Jul 25 01:08:10 my_comp kernel: [    2.349881] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 25 01:08:10 my_comp kernel: [    2.349905] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 25 01:08:10 my_comp kernel: [    2.463542]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 > sda4
Jul 25 01:08:10 my_comp kernel: [    2.464151] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 25 01:08:10 my_comp kernel: [    2.528054] ata6: softreset failed (device not ready)
Jul 25 01:08:10 my_comp kernel: [    2.528060] ata6: applying SB600 PMP SRST workaround and retrying
Jul 25 01:08:10 my_comp kernel: [    2.700064] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 25 01:08:10 my_comp kernel: [    2.712790] ata6.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
Jul 25 01:08:10 my_comp kernel: [    2.726448] ata6.00: configured for UDMA/100
Jul 25 01:08:10 my_comp kernel: [    2.728046] scsi 5:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
Jul 25 01:08:10 my_comp kernel: [    2.731769] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 25 01:08:10 my_comp kernel: [    2.731773] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 25 01:08:10 my_comp kernel: [    2.731912] sr 5:0:0:0: Attached scsi CD-ROM sr0
Jul 25 01:08:10 my_comp kernel: [    2.732017] sr 5:0:0:0: Attached scsi generic sg1 type 5
Jul 25 01:08:10 my_comp kernel: [    4.418926] uvesafb: (C) 1988-2005, ATI Technologies Inc. , RS780, 01.00, OEM: ATI ATOMBIOS, VBE v3.0
Jul 25 01:08:10 my_comp kernel: [    4.439421] uvesafb: protected mode interface info at c000:a252
Jul 25 01:08:10 my_comp kernel: [    4.439427] uvesafb: pmi: set display start = c00ca2f4, set palette = c00ca3b2
Jul 25 01:08:10 my_comp kernel: [    4.439494] uvesafb: VBIOS/hardware supports DDC2 transfers
Jul 25 01:08:10 my_comp kernel: [    4.506056] uvesafb: monitor limits: vf = 60 Hz, hf = 49 kHz, clk = 69 MHz
Jul 25 01:08:10 my_comp kernel: [    4.506199] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=8192
Jul 25 01:08:10 my_comp kernel: [    4.510740] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
Jul 25 01:08:10 my_comp kernel: [    4.736365] Console: switching to colour frame buffer device 90x25
Jul 25 01:08:10 my_comp kernel: [    4.736445] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
Jul 25 01:08:10 my_comp kernel: [    4.956998] uvesafb: framebuffer at 0xc0000000, mapped to 0xf8100000, using 6144k, total 16384k
Jul 25 01:08:10 my_comp kernel: [    4.957000] fb0: VESA VGA frame buffer device
Jul 25 01:08:10 my_comp kernel: [    5.070860] EXT4-fs (sda9): INFO: recovery required on readonly filesystem
Jul 25 01:08:10 my_comp kernel: [    5.070865] EXT4-fs (sda9): write access will be enabled during recovery
Jul 25 01:08:10 my_comp kernel: [    6.680410] EXT4-fs (sda9): orphan cleanup on readonly fs
Jul 25 01:08:10 my_comp kernel: [    6.680422] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1075979
Jul 25 01:08:10 my_comp kernel: [    6.680468] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 821143
Jul 25 01:08:10 my_comp kernel: [    6.680556] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 821141
Jul 25 01:08:10 my_comp kernel: [    6.680575] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 821650
Jul 25 01:08:10 my_comp kernel: [    6.680659] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 804826
Jul 25 01:08:10 my_comp kernel: [    6.680680] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1068056
Jul 25 01:08:10 my_comp kernel: [    6.680700] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 786828
Jul 25 01:08:10 my_comp kernel: [    6.680719] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 789046
Jul 25 01:08:10 my_comp kernel: [    6.680776] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048988
Jul 25 01:08:10 my_comp kernel: [    6.680788] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048987
Jul 25 01:08:10 my_comp kernel: [    6.680798] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048973
Jul 25 01:08:10 my_comp kernel: [    6.680809] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048972
Jul 25 01:08:10 my_comp kernel: [    6.680820] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048921
Jul 25 01:08:10 my_comp kernel: [    6.680829] EXT4-fs (sda9): 13 orphan inodes deleted
Jul 25 01:08:10 my_comp kernel: [    6.680832] EXT4-fs (sda9): recovery complete
Jul 25 01:08:10 my_comp kernel: [    7.113974] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
Jul 25 01:08:10 my_comp kernel: [   25.179050] <30>udev[426]: starting version 167
Jul 25 01:08:10 my_comp kernel: [   25.236546] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
Jul 25 01:08:10 my_comp kernel: [   25.261175] lp: driver loaded but no devices found
Jul 25 01:08:10 my_comp kernel: [   25.337937] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 25 01:08:10 my_comp kernel: [   25.372864] lib80211: common routines for IEEE802.11 drivers
Jul 25 01:08:10 my_comp kernel: [   25.372870] lib80211_crypt: registered algorithm 'NULL'
Jul 25 01:08:10 my_comp kernel: [   25.463676] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 25 01:08:10 my_comp kernel: [   25.477477] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 01:08:10 my_comp kernel: [   25.477487] jmb38x_ms 0000:08:00.3: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [   25.524247] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jul 25 01:08:10 my_comp kernel: [   25.525519] SP5100 TCO timer: mmio address 0xfec000f0 already in use
Jul 25 01:08:10 my_comp kernel: [   25.560778] type=1400 audit(1311521887.585:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=661 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   25.561177] type=1400 audit(1311521887.585:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=661 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   25.561434] type=1400 audit(1311521887.585:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=661 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   25.561763] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 25 01:08:10 my_comp kernel: [   25.561770] Disabling lock debugging due to kernel taint
Jul 25 01:08:10 my_comp kernel: [   25.781037] IR NEC protocol handler initialized
Jul 25 01:08:10 my_comp kernel: [   25.781520] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xc0
Jul 25 01:08:10 my_comp kernel: [   25.781523] ene_ir: PLL freq = 1406
Jul 25 01:08:10 my_comp kernel: [   25.781525] ene_ir: KB3926C detected
Jul 25 01:08:10 my_comp kernel: [   25.781538] ene_ir: Firmware regs: c0 00
Jul 25 01:08:10 my_comp kernel: [   25.781540] ene_ir: Hardware features:
Jul 25 01:08:10 my_comp kernel: [   25.781542] ene_ir: * Uses GPIO 40 for IR demodulated input
Jul 25 01:08:10 my_comp kernel: [   25.789568] IR RC5(x) protocol handler initialized
Jul 25 01:08:10 my_comp kernel: [   25.796116] IR RC6 protocol handler initialized
Jul 25 01:08:10 my_comp kernel: [   25.803617] IR JVC protocol handler initialized
Jul 25 01:08:10 my_comp kernel: [   25.809792] IR Sony protocol handler initialized
Jul 25 01:08:10 my_comp kernel: [   25.816263] lirc_dev: IR Remote Control driver registered, major 251 
Jul 25 01:08:10 my_comp kernel: [   25.817801] IR LIRC bridge handler initialized
Jul 25 01:08:10 my_comp kernel: [   25.884331] Registered IR keymap rc-rc6-mce
Jul 25 01:08:10 my_comp kernel: [   25.884594] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input5
Jul 25 01:08:10 my_comp kernel: [   25.884778] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
Jul 25 01:08:10 my_comp kernel: [   25.889381] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
Jul 25 01:08:10 my_comp kernel: [   25.889387] ene_ir: driver has been succesfully loaded
Jul 25 01:08:10 my_comp kernel: [   26.066214] input: HP WMI hotkeys as /devices/virtual/input/input6
Jul 25 01:08:10 my_comp kernel: [   26.097211] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 25 01:08:10 my_comp kernel: [   26.110322] wl 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 01:08:10 my_comp kernel: [   26.110333] wl 0000:09:00.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [   26.143241] Linux video capture interface: v2.00
Jul 25 01:08:10 my_comp kernel: [   26.162229] uvcvideo: Found UVC 1.00 device USB Camera Device (174f:5216)
Jul 25 01:08:10 my_comp kernel: [   26.172257] lib80211_crypt: registered algorithm 'TKIP'
Jul 25 01:08:10 my_comp kernel: [   26.192313] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul 25 01:08:10 my_comp kernel: [   26.221641] input: USB Camera Device as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input7
Jul 25 01:08:10 my_comp kernel: [   26.222638] usbcore: registered new interface driver uvcvideo
Jul 25 01:08:10 my_comp kernel: [   26.222643] USB Video Class driver (v1.0.0)
Jul 25 01:08:10 my_comp kernel: [   26.311315] [fglrx] Maximum main memory to use for locked dma buffers: 2627 MBytes.
Jul 25 01:08:10 my_comp kernel: [   26.311404] [fglrx]   vendor: 1002 device: 9612 count: 1
Jul 25 01:08:10 my_comp kernel: [   26.312121] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jul 25 01:08:10 my_comp kernel: [   26.312139] pci 0000:01:05.0: power state changed by ACPI to D0
Jul 25 01:08:10 my_comp kernel: [   26.312144] pci 0000:01:05.0: power state changed by ACPI to D0
Jul 25 01:08:10 my_comp kernel: [   26.312193] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 01:08:10 my_comp kernel: [   26.312201] pci 0000:01:05.0: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [   26.312759] [fglrx] Kernel PAT support is enabled
Jul 25 01:08:10 my_comp kernel: [   26.312786] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
Jul 25 01:08:10 my_comp kernel: [   26.344517] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
Jul 25 01:08:10 my_comp kernel: [   26.403055] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 01:08:10 my_comp kernel: [   26.403104] HDA Intel 0000:00:14.2: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [   26.488664] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jul 25 01:08:10 my_comp kernel: [   26.490429] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jul 25 01:08:10 my_comp kernel: [   26.491515] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 25 01:08:10 my_comp kernel: [   26.491603] HDA Intel 0000:01:05.1: setting latency timer to 64
Jul 25 01:08:10 my_comp kernel: [   26.645918] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
Jul 25 01:08:10 my_comp kernel: [   26.691437] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
Jul 25 01:08:10 my_comp kernel: [   27.963171] type=1400 audit(1311521889.985:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1078 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   27.963626] type=1400 audit(1311521889.985:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1077 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   27.977415] type=1400 audit(1311521890.001:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1078 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   27.977677] type=1400 audit(1311521890.001:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1078 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   27.992199] type=1400 audit(1311521890.017:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1080 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   28.001211] type=1400 audit(1311521890.025:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1084 comm="apparmor_parser"
Jul 25 01:08:10 my_comp kernel: [   28.011021] type=1400 audit(1311521890.033:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1080 comm="apparmor_parser"
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Linktop
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Gobi
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin SimTech
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Option
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Generic
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Huawei
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin X22X
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin AnyData
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Ericsson MBM
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Sierra
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Option High-Speed
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Novatel
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Longcheer
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin MotoC
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin Nokia
Jul 25 01:08:10 my_comp modem-manager[1088]: <info>  Loaded plugin ZTE
Jul 25 01:08:10 my_comp polkitd[1160]: started daemon version 0.101 using authority implementation `local' version `0.101'
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: init!
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: update_system_hostname
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPluginIfupdown: management mode: unmanaged
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:09:00.0/net/eth1, iface: eth1)
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:09:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:0a:00.0/net/eth0, iface: eth0)
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:0a:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: end _init.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    Ifupdown: get unmanaged devices count: 0
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: (143540256) ... get_connections.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: (143540256) ... get_connections (managed=false): return empty list.
Jul 25 01:08:10 my_comp NetworkManager[1069]:    keyfile: parsing Auto eth0 ... 
Jul 25 01:08:10 my_comp NetworkManager[1069]:    keyfile:     read connection 'Auto eth0'
Jul 25 01:08:10 my_comp NetworkManager[1069]:    Ifupdown: get unmanaged devices count: 0
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:06.0/0000:09:00.0/net/eth1/rfkill1) (driver <unknown>)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/hp-wmi/rfkill/rfkill0) (driver hp-wmi)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> Networking is enabled by state file
Jul 25 01:08:10 my_comp NetworkManager[1069]: <error> [1311521890.213979] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): now managed
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): bringing up device.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): preparing device.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): deactivating device (reason: 2).
Jul 25 01:08:10 my_comp NetworkManager[1069]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): carrier is OFF
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 25 01:08:10 my_comp gdm-binary[1056]: WARNING: Unable to find users: no seat-id found
Jul 25 01:08:10 my_comp kernel: [   28.267536] r8169 0000:0a:00.0: eth0: link down
Jul 25 01:08:10 my_comp kernel: [   28.267809] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): now managed
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): bringing up device.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): preparing device.
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth0): deactivating device (reason: 2).
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> modem-manager is now available
Jul 25 01:08:10 my_comp NetworkManager[1069]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> Trying to start the supplicant...
Jul 25 01:08:10 my_comp kernel: [   28.332938] ppdev: user-space parallel port driver
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): supplicant manager state:  down -> idle
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): device state change: 2 -> 3 (reason 0)
Jul 25 01:08:10 my_comp NetworkManager[1069]: <info> (eth1): supplicant interface state:  starting -> ready
Jul 25 01:08:10 my_comp kernel: [   28.492713] [fglrx] ATIF platform detected with notification ID: 0x81
Jul 25 01:08:10 my_comp init: apport pre-start process (1339) terminated with status 1
Jul 25 01:08:10 my_comp anacron[1387]: Anacron 2.3 started on 2011-07-25
Jul 25 01:08:10 my_comp acpid: starting up with proc fs
Jul 25 01:08:10 my_comp acpid: 34 rules loaded
Jul 25 01:08:10 my_comp acpid: waiting for events: event logging is off
Jul 25 01:08:10 my_comp cron[1351]: (CRON) INFO (pidfile fd = 3)
Jul 25 01:08:10 my_comp cron[1398]: (CRON) STARTUP (fork ok)
Jul 25 01:08:10 my_comp cron[1398]: (CRON) INFO (Running @reboot jobs)
Jul 25 01:08:10 my_comp init: apport post-stop process (1404) terminated with status 1
Jul 25 01:08:10 my_comp kernel: [   28.628573] Intel AES-NI instructions are not detected.
Jul 25 01:08:10 my_comp kernel: [   28.912769] [fglrx] GART Table is not in FRAME_BUFFER range 
Jul 25 01:08:10 my_comp kernel: [   28.914535] padlock_aes: VIA PadLock not detected.
Jul 25 01:08:10 my_comp kernel: [   28.917117] [fglrx] Could not enable MSI; System prevented initialization
Jul 25 01:08:10 my_comp kernel: [   28.917936] [fglrx] Firegl kernel thread PID: 1440
Jul 25 01:08:10 my_comp kernel: [   28.918042] [fglrx] Firegl kernel thread PID: 1441
Jul 25 01:08:10 my_comp kernel: [   28.918141] [fglrx] Firegl kernel thread PID: 1442
Jul 25 01:08:10 my_comp kernel: [   28.918525] [fglrx] IRQ 18 Enabled
Jul 25 01:08:10 my_comp anacron[1387]: Will run job `cron.monthly' in 15 min.
Jul 25 01:08:10 my_comp anacron[1387]: Jobs will be executed sequentially
Jul 25 01:08:10 my_comp kernel: [   28.953824] padlock_sha: VIA PadLock Hash Engine not detected.
Jul 25 01:08:11 my_comp modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.38-8-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Jul 25 01:08:11 my_comp kernel: [   29.721360] Adding 2880508k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2880508k 
Jul 25 01:08:11 my_comp kernel: [   29.741244] [fglrx] Gart USWC size:864 M.
Jul 25 01:08:11 my_comp kernel: [   29.741250] [fglrx] Gart cacheable size:342 M.
Jul 25 01:08:11 my_comp kernel: [   29.741256] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul 25 01:08:11 my_comp kernel: [   29.741260] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Jul 25 01:08:11 my_comp avahi-daemon[1066]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::221:ff:feb6:5ea5.
Jul 25 01:08:11 my_comp avahi-daemon[1066]: New relevant interface eth1.IPv6 for mDNS.
Jul 25 01:08:11 my_comp avahi-daemon[1066]: Registering new address record for fe80::221:ff:feb6:5ea5 on eth1.*.
Jul 25 01:08:16 my_comp gdm-simple-greeter[1786]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jul 25 01:08:16 my_comp kernel: [   34.564225] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro,commit=0
Jul 25 01:08:17 my_comp gdm-simple-greeter[1786]: WARNING: Unable to load CK history: no seat-id found
Jul 25 01:08:17 my_comp gdm-simple-greeter[1786]: WARNING: Unable to parse history: (null)   4#012
Jul 25 01:08:19 my_comp kernel: [   37.865535] vboxdrv: Found 2 processor cores.
Jul 25 01:08:19 my_comp kernel: [   37.865685] vboxdrv: fAsync=1 offMin=0xe454014 offMax=0xe454014
Jul 25 01:08:19 my_comp kernel: [   37.865766] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Jul 25 01:08:19 my_comp kernel: [   37.865769] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
Jul 25 01:08:19 my_comp NetworkManager[1069]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jul 25 01:08:19 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jul 25 01:08:19 my_comp NetworkManager[1069]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jul 25 01:08:20 my_comp kernel: [   38.904057] eth1: no IPv6 routers present
Jul 25 01:08:21 my_comp init: plymouth-stop pre-start process (2681) terminated with status 1
Jul 25 01:09:19 my_comp NetworkManager[1069]: <warn> Could not get scan request result: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jul 25 01:09:27 my_comp gdm-simple-greeter[1786]: WARNING: SelectUser org.freedesktop.DBus.Error.NoReply raised: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.#012
Jul 25 01:09:53 my_comp gdm-simple-greeter[1786]: WARNING: BeginVerificationForUser org.freedesktop.DBus.Error.NoReply raised: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.#012
Jul 25 01:10:18 my_comp init: mysql post-start process (1460) terminated with status 1
Jul 25 01:10:50 my_comp NetworkManager[1069]: <warn> could not get scan results: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken..
Jul 25 01:10:50 my_comp NetworkManager[1069]: <warn> Could not get scan request result: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jul 25 01:10:53 my_comp gdm-session-worker[1789]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jul 25 01:11:06 my_comp gdm-session-worker[1789]: pam_sm_authenticate: Called
Jul 25 01:11:06 my_comp gdm-session-worker[1789]: pam_sm_authenticate: username = [username]
Jul 25 01:11:06 my_comp gdm-session-worker[2755]: Passphrase file wrapped
Jul 25 01:12:08 my_comp acpid: client connected from 3054[113:123]
Jul 25 01:12:08 my_comp acpid: 1 client rule loaded
Jul 25 01:12:44 my_comp sudo: pam_sm_authenticate: Called
Jul 25 01:12:44 my_comp sudo: pam_sm_authenticate: username = [username]
Jul 25 01:12:44 my_comp sudo: pam_sm_authenticate: /home/username is already mounted

```

---

### Post by joshmo on 2011-07-24
> **galvatron408 said:**
> ok, then, what I would do is....

boot in to runlevel 3 to see if the freeze exists. If it does, at least you'll see what line it hangs on. If it doesn't, that's fine too.

When runlevel 3 is done booting, then switch to runlevel 5 to see if you see the freeze.

A lot of times, when a linux distro is freezing the way you describe it, it means that the cpu is at 100% utilisation. Basically, it's too busy doing whatever it is doing to give cpu cycles to the GUI and mouse. There's really no other reason I can think of as to why it freezes and then comes back (other than a timeout; but then again, you said the mouse freezes too).

How do I get to these runlevel's you're talking about? am not really an expert at linux :). I wouldnt understand how the CPU would be working hard all of a sudden, my system updated on Friday night, half of saturday was okay and then later on in the day I got this problem without installing anything else.

---

### Post by galvatron408 on 2011-07-24
The first thing I do when I look at these logs is to scan for time differences. So, I saw that most of the log said 01:08. That's pretty fast. Then.....

Jul 25 01:08:21 my_comp init: plymouth-stop pre-start process (2681) terminated with status 1
Jul 25 01:09:19 my_comp NetworkManager[1069]: <warn> Could not get scan request result: Did not receive a reply. Possible causes include: the remote 
What this means is....

@ 01:08:21, a log entry was entered and then NetworkManager was fired off

NetworkManager kind of sat there until finally @ 01:09:19 (almost a minute later), it returned and said.... <warn> blah...

so, can you try to disable NetworkManager to see what happens? Here is the ubuntu doc. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

Just search for the word disable. It's on there, I checked.

---

### Post by galvatron408 on 2011-07-24
oooh hey, I did a quick google search and that's what people have reported!

I took the following from: [http://ubuntuforums.org/archive/index.php/t-1627423.html](http://ubuntuforums.org/archive/index.php/t-1627423.html)

"I think the ndiswrapper doesn't work along with the rt2870sta 64Bit driver.

It just freezes the system after the first request:

syslog:

Nov 24 07:16:19 hope kernel: [  464.931810]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Nov 24 07:16:29 hope NetworkManager[1015]: <warn> Could not get  scan request result: Did not receive a reply. Possible causes include:  the remote application did not send a reply, the message bus security  policy blocked the reply, the reply timeout expired, or the network  connection was broken."

---

### Post by joshmo on 2011-07-24
> **galvatron408 said:**
> The first thing I do when I look at these logs is to scan for time differences. So, I saw that most of the log said 01:08. That's pretty fast. Then.....

Jul 25 01:08:21 my_comp init: plymouth-stop pre-start process (2681) terminated with status 1
Jul 25 01:09:19 my_comp NetworkManager[1069]: <warn> Could not get scan request result: Did not receive a reply. Possible causes include: the remote 
What this means is....

@ 01:08:21, a log entry was entered and then NetworkManager was fired off

NetworkManager kind of sat there until finally @ 01:09:19 (almost a minute later), it returned and said.... <warn> blah...

so, can you try to disable NetworkManager to see what happens? Here is the ubuntu doc. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

Just search for the word disable. It's on there, I checked.

I disabled NetworkManager using the following command since the one in the link provided was not working.
/etc/init.d/network-manager stop I also uninstalled the wireless drivers, but the problem is still persisting. I read through the second link you provided but I did not get to understand the solution suggested there. Here is an updated syslog on my most recent startup.

```

Jul 25 03:23:19 my_comp kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jul 25 03:23:19 my_comp rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1039" x-info="http://www.rsyslog.com"] (re)start
Jul 25 03:23:19 my_comp rsyslogd: rsyslogd's groupid changed to 103
Jul 25 03:23:19 my_comp rsyslogd: rsyslogd's userid changed to 101
Jul 25 03:23:19 my_comp rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 25 03:23:19 my_comp kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 25 03:23:19 my_comp kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 25 03:23:19 my_comp kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jul 25 03:23:19 my_comp kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000afd70000 (usable)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe58000 (usable)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afe58000 - 00000000afebf000 (ACPI NVS)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeea000 (usable)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afeea000 - 00000000afeff000 (ACPI data)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e1000000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Jul 25 03:23:19 my_comp kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jul 25 03:23:19 my_comp kernel: [    0.000000] DMI 2.4 present.
Jul 25 03:23:19 my_comp kernel: [    0.000000] DMI: Hewlett-Packard Compaq Presario CQ40 Notebook PC/30FE, BIOS F.55 07/06/2010
Jul 25 03:23:19 my_comp kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul 25 03:23:19 my_comp kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul 25 03:23:19 my_comp kernel: [    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000
Jul 25 03:23:19 my_comp kernel: [    0.000000] MTRR default type: uncachable
Jul 25 03:23:19 my_comp kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 25 03:23:19 my_comp kernel: [    0.000000]   00000-9FFFF write-back
Jul 25 03:23:19 my_comp kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 25 03:23:19 my_comp kernel: [    0.000000]   C0000-FFFFF write-through
Jul 25 03:23:19 my_comp kernel: [    0.000000] MTRR variable ranges enabled:
Jul 25 03:23:19 my_comp kernel: [    0.000000]   0 base 00FFF00000 mask FFFFF00000 write-protect
Jul 25 03:23:19 my_comp kernel: [    0.000000]   1 base 0000000000 mask FF80000000 write-back
Jul 25 03:23:19 my_comp kernel: [    0.000000]   2 base 0080000000 mask FFE0000000 write-back
Jul 25 03:23:19 my_comp kernel: [    0.000000]   3 base 00A0000000 mask FFF0000000 write-back
Jul 25 03:23:19 my_comp kernel: [    0.000000]   4 disabled
Jul 25 03:23:19 my_comp kernel: [    0.000000]   5 disabled
Jul 25 03:23:19 my_comp kernel: [    0.000000]   6 disabled
Jul 25 03:23:19 my_comp kernel: [    0.000000]   7 disabled
Jul 25 03:23:19 my_comp kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 25 03:23:19 my_comp kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Jul 25 03:23:19 my_comp kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 25 03:23:19 my_comp kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul 25 03:23:19 my_comp kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul 25 03:23:19 my_comp kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul 25 03:23:19 my_comp kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Jul 25 03:23:19 my_comp kernel: [    0.000000] RAMDISK: 35c20000 - 36e08000
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: XSDT afefe120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: FACP afefd000 000F4 (v04 HP     REPLEY   00000003 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: DSDT afeee000 0A632 (v01 HP     REPLEY   F0000000 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: FACS afe61000 00040
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: HPET afefc000 00038 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: APIC afefb000 00084 (v02 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: MCFG afefa000 0003C (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: MSCT afef9000 0004E (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: BOOT afeed000 00028 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: SLIC afeec000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: SSDT afeeb000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: SRAT afeea000 00078 (v03 AMD    AMD CRB  00000001 AMD  00000001)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 25 03:23:19 my_comp kernel: [    0.000000] 1927MB HIGHMEM available.
Jul 25 03:23:19 my_comp kernel: [    0.000000] 887MB LOWMEM available.
Jul 25 03:23:19 my_comp kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 25 03:23:19 my_comp kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 25 03:23:19 my_comp kernel: [    0.000000] Zone PFN ranges:
Jul 25 03:23:19 my_comp kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 25 03:23:19 my_comp kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 25 03:23:19 my_comp kernel: [    0.000000]   HighMem  0x000377fe -> 0x000aff00
Jul 25 03:23:19 my_comp kernel: [    0.000000] Movable zone start PFN for each node
Jul 25 03:23:19 my_comp kernel: [    0.000000] early_node_map[5] active PFN ranges
Jul 25 03:23:19 my_comp kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 25 03:23:19 my_comp kernel: [    0.000000]     0: 0x00000100 -> 0x000afd70
Jul 25 03:23:19 my_comp kernel: [    0.000000]     0: 0x000afdbf -> 0x000afe58
Jul 25 03:23:19 my_comp kernel: [    0.000000]     0: 0x000afebf -> 0x000afeea
Jul 25 03:23:19 my_comp kernel: [    0.000000]     0: 0x000afeff -> 0x000aff00
Jul 25 03:23:19 my_comp kernel: [    0.000000] On node 0 totalpages: 720324
Jul 25 03:23:19 my_comp kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4620200
Jul 25 03:23:19 my_comp kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 25 03:23:19 my_comp kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 25 03:23:19 my_comp kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 25 03:23:19 my_comp kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul 25 03:23:19 my_comp kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul 25 03:23:19 my_comp kernel: [    0.000000]   HighMem zone: 3855 pages used for memmap
Jul 25 03:23:19 my_comp kernel: [    0.000000]   HighMem zone: 489256 pages, LIFO batch:31
Jul 25 03:23:19 my_comp kernel: [    0.000000] Using APIC driver default
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 25 03:23:19 my_comp kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 25 03:23:19 my_comp kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 25 03:23:19 my_comp kernel: [    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
Jul 25 03:23:19 my_comp kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 25 03:23:19 my_comp kernel: [    0.000000] nr_irqs_gsi: 40
Jul 25 03:23:19 my_comp kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 25 03:23:19 my_comp kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 25 03:23:19 my_comp kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 25 03:23:19 my_comp kernel: [    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 25 03:23:19 my_comp kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 25 03:23:19 my_comp kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
Jul 25 03:23:19 my_comp kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
Jul 25 03:23:19 my_comp kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 25 03:23:19 my_comp kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714693
Jul 25 03:23:19 my_comp kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=dede56cd-fa70-49da-bcc6-75a2a59cda86 ro quiet splash
Jul 25 03:23:19 my_comp kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Initializing CPU#0
Jul 25 03:23:19 my_comp kernel: [    0.000000] allocated 14412480 bytes of page_cgroup
Jul 25 03:23:19 my_comp kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 25 03:23:19 my_comp kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000aff00)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Memory: 2815936k/2882560k available (5188k kernel code, 65360k reserved, 2540k data, 700k init, 1972444k highmem)
Jul 25 03:23:19 my_comp kernel: [    0.000000] virtual kernel memory layout:
Jul 25 03:23:19 my_comp kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul 25 03:23:19 my_comp kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 25 03:23:19 my_comp kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 25 03:23:19 my_comp kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 25 03:23:19 my_comp kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Jul 25 03:23:19 my_comp kernel: [    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
Jul 25 03:23:19 my_comp kernel: [    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
Jul 25 03:23:19 my_comp kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 25 03:23:19 my_comp kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 25 03:23:19 my_comp kernel: [    0.000000] Hierarchical RCU implementation.
Jul 25 03:23:19 my_comp kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 25 03:23:19 my_comp kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Jul 25 03:23:19 my_comp kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
Jul 25 03:23:19 my_comp kernel: [    0.000000] CPU 0 irqstacks, hard=f3408000 soft=f340a000
Jul 25 03:23:19 my_comp kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 25 03:23:19 my_comp kernel: [    0.000000] Console: colour dummy device 80x25
Jul 25 03:23:19 my_comp kernel: [    0.000000] console [tty0] enabled
Jul 25 03:23:19 my_comp kernel: [    0.000000] hpet clockevent registered
Jul 25 03:23:19 my_comp kernel: [    0.000000] Fast TSC calibration using PIT
Jul 25 03:23:19 my_comp kernel: [    0.000000] Detected 2200.209 MHz processor.
Jul 25 03:23:19 my_comp kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.41 BogoMIPS (lpj=8800836)
Jul 25 03:23:19 my_comp kernel: [    0.004011] pid_max: default: 32768 minimum: 301
Jul 25 03:23:19 my_comp kernel: [    0.004044] Security Framework initialized
Jul 25 03:23:19 my_comp kernel: [    0.004068] AppArmor: AppArmor initialized
Jul 25 03:23:19 my_comp kernel: [    0.004070] Yama: becoming mindful.
Jul 25 03:23:19 my_comp kernel: [    0.004146] Mount-cache hash table entries: 512
Jul 25 03:23:19 my_comp kernel: [    0.004319] Initializing cgroup subsys ns
Jul 25 03:23:19 my_comp kernel: [    0.004324] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Jul 25 03:23:19 my_comp kernel: [    0.004328] Initializing cgroup subsys cpuacct
Jul 25 03:23:19 my_comp kernel: [    0.004334] Initializing cgroup subsys memory
Jul 25 03:23:19 my_comp kernel: [    0.004345] Initializing cgroup subsys devices
Jul 25 03:23:19 my_comp kernel: [    0.004349] Initializing cgroup subsys freezer
Jul 25 03:23:19 my_comp kernel: [    0.004352] Initializing cgroup subsys net_cls
Jul 25 03:23:19 my_comp kernel: [    0.004355] Initializing cgroup subsys blkio
Jul 25 03:23:19 my_comp kernel: [    0.004398] CPU: Physical Processor ID: 0
Jul 25 03:23:19 my_comp kernel: [    0.004400] CPU: Processor Core ID: 0
Jul 25 03:23:19 my_comp kernel: [    0.004404] mce: CPU supports 5 MCE banks
Jul 25 03:23:19 my_comp kernel: [    0.008055] ACPI: Core revision 20110112
Jul 25 03:23:19 my_comp kernel: [    0.016015] ftrace: allocating 23640 entries in 47 pages
Jul 25 03:23:19 my_comp kernel: [    0.024105] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 25 03:23:19 my_comp kernel: [    0.024500] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 25 03:23:19 my_comp kernel: [    0.067257] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-74 stepping 01
Jul 25 03:23:19 my_comp kernel: [    0.068003] Performance Events: AMD PMU driver.
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... version:                0
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... bit width:              48
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... generic registers:      4
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... value mask:             0000ffffffffffff
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... max period:             00007fffffffffff
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... fixed-purpose events:   0
Jul 25 03:23:19 my_comp kernel: [    0.068003] ... event mask:             000000000000000f
Jul 25 03:23:19 my_comp kernel: [    0.068003] CPU 1 irqstacks, hard=f34d0000 soft=f34d2000
Jul 25 03:23:19 my_comp kernel: [    0.068003] Booting Node   0, Processors  #1
Jul 25 03:23:19 my_comp kernel: [    0.008000] Initializing CPU#1
Jul 25 03:23:19 my_comp kernel: [    0.156009] TSC synchronization [CPU#0 -> CPU#1]:
Jul 25 03:23:19 my_comp kernel: [    0.156009] Measured 239396172 cycles TSC warp between CPUs, turning off TSC clock.
Jul 25 03:23:19 my_comp kernel: [    0.156009] Marking TSC unstable due to check_tsc_sync_source failed
Jul 25 03:23:19 my_comp kernel: [    0.156022] Brought up 2 CPUs
Jul 25 03:23:19 my_comp kernel: [    0.156025] Total of 2 processors activated (8789.91 BogoMIPS).
Jul 25 03:23:19 my_comp kernel: [    0.156330] devtmpfs: initialized
Jul 25 03:23:19 my_comp kernel: [    0.157388] print_constraints: dummy: 
Jul 25 03:23:19 my_comp kernel: [    0.157453] Time:  3:22:53  Date: 07/25/11
Jul 25 03:23:19 my_comp kernel: [    0.157499] NET: Registered protocol family 16
Jul 25 03:23:19 my_comp kernel: [    0.157540] Trying to unpack rootfs image as initramfs...
Jul 25 03:23:19 my_comp kernel: [    0.157652] EISA bus registered
Jul 25 03:23:19 my_comp kernel: [    0.157697] TOM: 00000000c0000000 aka 3072M
Jul 25 03:23:19 my_comp kernel: [    0.157701] Fam 10h mmconf [e0000000, e0ffffff]
Jul 25 03:23:19 my_comp kernel: [    0.157803] Extended Config Space enabled on 0 nodes
Jul 25 03:23:19 my_comp kernel: [    0.157815] ACPI: bus type pci registered
Jul 25 03:23:19 my_comp kernel: [    0.157931] PCI: MMCONFIG for domain 0000 [bus 00-0f] at [mem 0xe0000000-0xe0ffffff] (base 0xe0000000)
Jul 25 03:23:19 my_comp kernel: [    0.157936] PCI: MMCONFIG at [mem 0xe0000000-0xe0ffffff] reserved in E820
Jul 25 03:23:19 my_comp kernel: [    0.157938] PCI: Using MMCONFIG for extended config space
Jul 25 03:23:19 my_comp kernel: [    0.157940] PCI: Using configuration type 1 for base access
Jul 25 03:23:19 my_comp kernel: [    0.157964] mtrr: your CPUs had inconsistent fixed MTRR settings
Jul 25 03:23:19 my_comp kernel: [    0.157966] mtrr: probably your BIOS does not setup all CPUs.
Jul 25 03:23:19 my_comp kernel: [    0.157968] mtrr: corrected configuration.
Jul 25 03:23:19 my_comp kernel: [    0.172378] bio: create slab <bio-0> at 0
Jul 25 03:23:19 my_comp kernel: [    0.174061] ACPI: EC: Look up EC in DSDT
Jul 25 03:23:19 my_comp kernel: [    0.175639] ACPI: Executed 1 blocks of module-level executable AML code
Jul 25 03:23:19 my_comp kernel: [    0.177997] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 25 03:23:19 my_comp kernel: [    0.208075] ACPI: Interpreter enabled
Jul 25 03:23:19 my_comp kernel: [    0.208081] ACPI: (supports S0 S3 S4 S5)
Jul 25 03:23:19 my_comp kernel: [    0.208106] ACPI: Using IOAPIC for interrupt routing
Jul 25 03:23:19 my_comp kernel: [    0.208625] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Jul 25 03:23:19 my_comp kernel: [    0.208912] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Jul 25 03:23:19 my_comp kernel: [    0.358661] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 25 03:23:19 my_comp kernel: [    0.358857] ACPI: No dock devices found.
Jul 25 03:23:19 my_comp kernel: [    0.358859] HEST: Table not found.
Jul 25 03:23:19 my_comp kernel: [    0.358863] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 25 03:23:19 my_comp kernel: [    0.359404] \_SB_.PCI0:_OSC request failed
Jul 25 03:23:19 my_comp kernel: [    0.359406] _OSC request data:1 8 1f 
Jul 25 03:23:19 my_comp kernel: [    0.359412] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 25 03:23:19 my_comp kernel: [    0.360401] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jul 25 03:23:19 my_comp kernel: [    0.360404] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jul 25 03:23:19 my_comp kernel: [    0.360407] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jul 25 03:23:19 my_comp kernel: [    0.360410] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Jul 25 03:23:19 my_comp kernel: [    0.360413] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Jul 25 03:23:19 my_comp kernel: [    0.360416] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Jul 25 03:23:19 my_comp kernel: [    0.360419] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Jul 25 03:23:19 my_comp kernel: [    0.360421] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Jul 25 03:23:19 my_comp kernel: [    0.360424] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Jul 25 03:23:19 my_comp kernel: [    0.360427] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Jul 25 03:23:19 my_comp kernel: [    0.360430] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Jul 25 03:23:19 my_comp kernel: [    0.360433] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Jul 25 03:23:19 my_comp kernel: [    0.360436] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Jul 25 03:23:19 my_comp kernel: [    0.360439] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Jul 25 03:23:19 my_comp kernel: [    0.360442] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Jul 25 03:23:19 my_comp kernel: [    0.360445] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
Jul 25 03:23:19 my_comp kernel: [    0.360448] pci_root PNP0A08:00: host bridge window [mem 0xe1000000-0xffffffff]
Jul 25 03:23:19 my_comp kernel: [    0.360456] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cebff]
Jul 25 03:23:19 my_comp kernel: [    0.360479] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
Jul 25 03:23:19 my_comp kernel: [    0.360552] pci 0000:00:01.0: [103c:9602] type 1 class 0x000604
Jul 25 03:23:19 my_comp kernel: [    0.360641] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
Jul 25 03:23:19 my_comp kernel: [    0.360685] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 25 03:23:19 my_comp kernel: [    0.360689] pci 0000:00:04.0: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.360710] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
Jul 25 03:23:19 my_comp kernel: [    0.360753] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 25 03:23:19 my_comp kernel: [    0.360757] pci 0000:00:05.0: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.360778] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
Jul 25 03:23:19 my_comp kernel: [    0.360821] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 25 03:23:19 my_comp kernel: [    0.360825] pci 0000:00:06.0: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.360846] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jul 25 03:23:19 my_comp kernel: [    0.360889] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul 25 03:23:19 my_comp kernel: [    0.360893] pci 0000:00:07.0: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.360967] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
Jul 25 03:23:19 my_comp kernel: [    0.360992] pci 0000:00:11.0: reg 10: [io  0x8038-0x803f]
Jul 25 03:23:19 my_comp kernel: [    0.361004] pci 0000:00:11.0: reg 14: [io  0x804c-0x804f]
Jul 25 03:23:19 my_comp kernel: [    0.361017] pci 0000:00:11.0: reg 18: [io  0x8030-0x8037]
Jul 25 03:23:19 my_comp kernel: [    0.361030] pci 0000:00:11.0: reg 1c: [io  0x8048-0x804b]
Jul 25 03:23:19 my_comp kernel: [    0.361042] pci 0000:00:11.0: reg 20: [io  0x8010-0x801f]
Jul 25 03:23:19 my_comp kernel: [    0.361055] pci 0000:00:11.0: reg 24: [mem 0xd2508000-0xd25083ff]
Jul 25 03:23:19 my_comp kernel: [    0.361112] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jul 25 03:23:19 my_comp kernel: [    0.361129] pci 0000:00:12.0: reg 10: [mem 0xd2507000-0xd2507fff]
Jul 25 03:23:19 my_comp kernel: [    0.361211] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
Jul 25 03:23:19 my_comp kernel: [    0.361228] pci 0000:00:12.1: reg 10: [mem 0xd2506000-0xd2506fff]
Jul 25 03:23:19 my_comp kernel: [    0.361316] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jul 25 03:23:19 my_comp kernel: [    0.361340] pci 0000:00:12.2: reg 10: [mem 0xd2508500-0xd25085ff]
Jul 25 03:23:19 my_comp kernel: [    0.361429] pci 0000:00:12.2: supports D1 D2
Jul 25 03:23:19 my_comp kernel: [    0.361432] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 25 03:23:19 my_comp kernel: [    0.361437] pci 0000:00:12.2: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.361464] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jul 25 03:23:19 my_comp kernel: [    0.361482] pci 0000:00:13.0: reg 10: [mem 0xd2505000-0xd2505fff]
Jul 25 03:23:19 my_comp kernel: [    0.361563] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
Jul 25 03:23:19 my_comp kernel: [    0.361581] pci 0000:00:13.1: reg 10: [mem 0xd2504000-0xd2504fff]
Jul 25 03:23:19 my_comp kernel: [    0.361669] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jul 25 03:23:19 my_comp kernel: [    0.361693] pci 0000:00:13.2: reg 10: [mem 0xd2508400-0xd25084ff]
Jul 25 03:23:19 my_comp kernel: [    0.361782] pci 0000:00:13.2: supports D1 D2
Jul 25 03:23:19 my_comp kernel: [    0.361785] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 25 03:23:19 my_comp kernel: [    0.361790] pci 0000:00:13.2: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.361821] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jul 25 03:23:19 my_comp kernel: [    0.361943] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jul 25 03:23:19 my_comp kernel: [    0.361964] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jul 25 03:23:19 my_comp kernel: [    0.361976] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jul 25 03:23:19 my_comp kernel: [    0.361989] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jul 25 03:23:19 my_comp kernel: [    0.362001] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jul 25 03:23:19 my_comp kernel: [    0.362014] pci 0000:00:14.1: reg 20: [io  0x8000-0x800f]
Jul 25 03:23:19 my_comp kernel: [    0.362077] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jul 25 03:23:19 my_comp kernel: [    0.362105] pci 0000:00:14.2: reg 10: [mem 0xd2500000-0xd2503fff 64bit]
Jul 25 03:23:19 my_comp kernel: [    0.362178] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 25 03:23:19 my_comp kernel: [    0.362184] pci 0000:00:14.2: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.362201] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jul 25 03:23:19 my_comp kernel: [    0.362297] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jul 25 03:23:19 my_comp kernel: [    0.362355] pci 0000:00:18.0: [1022:1300] type 0 class 0x000600
Jul 25 03:23:19 my_comp kernel: [    0.362389] pci 0000:00:18.1: [1022:1301] type 0 class 0x000600
Jul 25 03:23:19 my_comp kernel: [    0.362417] pci 0000:00:18.2: [1022:1302] type 0 class 0x000600
Jul 25 03:23:19 my_comp kernel: [    0.362446] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
Jul 25 03:23:19 my_comp kernel: [    0.362480] pci 0000:00:18.4: [1022:1304] type 0 class 0x000600
Jul 25 03:23:19 my_comp kernel: [    0.362587] pci 0000:01:05.0: [1002:9612] type 0 class 0x000300
Jul 25 03:23:19 my_comp kernel: [    0.362600] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.362608] pci 0000:01:05.0: reg 14: [io  0x7000-0x70ff]
Jul 25 03:23:19 my_comp kernel: [    0.362615] pci 0000:01:05.0: reg 18: [mem 0xd2400000-0xd240ffff]
Jul 25 03:23:19 my_comp kernel: [    0.362633] pci 0000:01:05.0: reg 24: [mem 0xd2300000-0xd23fffff]
Jul 25 03:23:19 my_comp kernel: [    0.362653] pci 0000:01:05.0: supports D1 D2
Jul 25 03:23:19 my_comp kernel: [    0.362669] pci 0000:01:05.1: [1002:960f] type 0 class 0x000403
Jul 25 03:23:19 my_comp kernel: [    0.362682] pci 0000:01:05.1: reg 10: [mem 0xd2410000-0xd2413fff]
Jul 25 03:23:19 my_comp kernel: [    0.362726] pci 0000:01:05.1: supports D1 D2
Jul 25 03:23:19 my_comp kernel: [    0.362809] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul 25 03:23:19 my_comp kernel: [    0.362815] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jul 25 03:23:19 my_comp kernel: [    0.362819] pci 0000:00:01.0:   bridge window [mem 0xd2300000-0xd24fffff]
Jul 25 03:23:19 my_comp kernel: [    0.362825] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.362864] pci 0000:00:04.0: PCI bridge to [bus 02-07]
Jul 25 03:23:19 my_comp kernel: [    0.362869] pci 0000:00:04.0:   bridge window [io  0x3000-0x6fff]
Jul 25 03:23:19 my_comp kernel: [    0.362873] pci 0000:00:04.0:   bridge window [mem 0xd1300000-0xd22fffff]
Jul 25 03:23:19 my_comp kernel: [    0.362879] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.362932] pci 0000:08:00.0: [197b:2382] type 0 class 0x000880
Jul 25 03:23:19 my_comp kernel: [    0.362951] pci 0000:08:00.0: reg 10: [mem 0xd1200300-0xd12003ff]
Jul 25 03:23:19 my_comp kernel: [    0.363022] pci 0000:08:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.363089] pci 0000:08:00.2: [197b:2381] type 0 class 0x000805
Jul 25 03:23:19 my_comp kernel: [    0.363108] pci 0000:08:00.2: reg 10: [mem 0xd1200200-0xd12002ff]
Jul 25 03:23:19 my_comp kernel: [    0.363240] pci 0000:08:00.3: [197b:2383] type 0 class 0x000880
Jul 25 03:23:19 my_comp kernel: [    0.363259] pci 0000:08:00.3: reg 10: [mem 0xd1200100-0xd12001ff]
Jul 25 03:23:19 my_comp kernel: [    0.363390] pci 0000:08:00.4: [197b:2384] type 0 class 0x000880
Jul 25 03:23:19 my_comp kernel: [    0.363409] pci 0000:08:00.4: reg 10: [mem 0xd1200000-0xd12000ff]
Jul 25 03:23:19 my_comp kernel: [    0.368043] pci 0000:00:05.0: PCI bridge to [bus 08-08]
Jul 25 03:23:19 my_comp kernel: [    0.368049] pci 0000:00:05.0:   bridge window [io  0xfffff000-0x0000] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.368053] pci 0000:00:05.0:   bridge window [mem 0xd1200000-0xd12fffff]
Jul 25 03:23:19 my_comp kernel: [    0.368059] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.368154] pci 0000:09:00.0: [14e4:4315] type 0 class 0x000280
Jul 25 03:23:19 my_comp kernel: [    0.368177] pci 0000:09:00.0: reg 10: [mem 0xd1100000-0xd1103fff 64bit]
Jul 25 03:23:19 my_comp kernel: [    0.368262] pci 0000:09:00.0: supports D1 D2
Jul 25 03:23:19 my_comp kernel: [    0.376073] pci 0000:00:06.0: PCI bridge to [bus 09-09]
Jul 25 03:23:19 my_comp kernel: [    0.376078] pci 0000:00:06.0:   bridge window [io  0xfffff000-0x0000] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.376082] pci 0000:00:06.0:   bridge window [mem 0xd1100000-0xd11fffff]
Jul 25 03:23:19 my_comp kernel: [    0.376088] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.376150] pci 0000:0a:00.0: [10ec:8136] type 0 class 0x000200
Jul 25 03:23:19 my_comp kernel: [    0.376166] pci 0000:0a:00.0: reg 10: [io  0x2000-0x20ff]
Jul 25 03:23:19 my_comp kernel: [    0.376193] pci 0000:0a:00.0: reg 18: [mem 0xd1010000-0xd1010fff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.376211] pci 0000:0a:00.0: reg 20: [mem 0xd1000000-0xd100ffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.376224] pci 0000:0a:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.376260] pci 0000:0a:00.0: supports D1 D2
Jul 25 03:23:19 my_comp kernel: [    0.376262] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 25 03:23:19 my_comp kernel: [    0.376272] pci 0000:0a:00.0: PME# disabled
Jul 25 03:23:19 my_comp kernel: [    0.384044] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
Jul 25 03:23:19 my_comp kernel: [    0.384050] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
Jul 25 03:23:19 my_comp kernel: [    0.384054] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.384060] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.384133] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384139] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
Jul 25 03:23:19 my_comp kernel: [    0.384145] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.384150] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.384154] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384157] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384160] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384163] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384166] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384169] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384172] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384175] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384178] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384181] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384185] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384188] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384191] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384194] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384197] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384200] pci 0000:00:14.4:   bridge window [mem 0xe1000000-0xffffffff] (subtractive decode)
Jul 25 03:23:19 my_comp kernel: [    0.384258] pci_bus 0000:00: on NUMA node 0
Jul 25 03:23:19 my_comp kernel: [    0.384262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Jul 25 03:23:19 my_comp kernel: [    0.384802] \_SB_.PCI0:_OSC request failed
Jul 25 03:23:19 my_comp kernel: [    0.384804] _OSC request data:1 1f 1f 
Jul 25 03:23:19 my_comp kernel: [    0.384809]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul 25 03:23:19 my_comp kernel: [    0.384845] \_SB_.PCI0:_OSC request failed
Jul 25 03:23:19 my_comp kernel: [    0.384847] _OSC request data:1 0 1d 
Jul 25 03:23:19 my_comp kernel: [    0.394845] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.394893] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.394939] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.394985] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.395030] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.395075] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.395121] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.395167] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Jul 25 03:23:19 my_comp kernel: [    0.395315] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Jul 25 03:23:19 my_comp kernel: [    0.395322] vgaarb: loaded
Jul 25 03:23:19 my_comp kernel: [    0.395574] SCSI subsystem initialized
Jul 25 03:23:19 my_comp kernel: [    0.395656] libata version 3.00 loaded.
Jul 25 03:23:19 my_comp kernel: [    0.395716] usbcore: registered new interface driver usbfs
Jul 25 03:23:19 my_comp kernel: [    0.395730] usbcore: registered new interface driver hub
Jul 25 03:23:19 my_comp kernel: [    0.395761] usbcore: registered new device driver usb
Jul 25 03:23:19 my_comp kernel: [    0.396047] wmi: Mapper loaded
Jul 25 03:23:19 my_comp kernel: [    0.396049] PCI: Using ACPI for IRQ routing
Jul 25 03:23:19 my_comp kernel: [    0.396053] PCI: pci_cache_line_size set to 64 bytes
Jul 25 03:23:19 my_comp kernel: [    0.396336] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jul 25 03:23:19 my_comp kernel: [    0.396339] reserve RAM buffer: 00000000afd70000 - 00000000afffffff 
Jul 25 03:23:19 my_comp kernel: [    0.396342] reserve RAM buffer: 00000000afe58000 - 00000000afffffff 
Jul 25 03:23:19 my_comp kernel: [    0.396345] reserve RAM buffer: 00000000afeea000 - 00000000afffffff 
Jul 25 03:23:19 my_comp kernel: [    0.396348] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
Jul 25 03:23:19 my_comp kernel: [    0.396465] NetLabel: Initializing
Jul 25 03:23:19 my_comp kernel: [    0.396466] NetLabel:  domain hash size = 128
Jul 25 03:23:19 my_comp kernel: [    0.396468] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 25 03:23:19 my_comp kernel: [    0.396481] NetLabel:  unlabeled traffic allowed by default
Jul 25 03:23:19 my_comp kernel: [    0.396560] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul 25 03:23:19 my_comp kernel: [    0.396565] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 25 03:23:19 my_comp kernel: [    0.398597] Switching to clocksource hpet
Jul 25 03:23:19 my_comp kernel: [    0.398898] Switched to NOHz mode on CPU #0
Jul 25 03:23:19 my_comp kernel: [    0.398688] Switched to NOHz mode on CPU #1
Jul 25 03:23:19 my_comp kernel: [    0.404800] AppArmor: AppArmor Filesystem Enabled
Jul 25 03:23:19 my_comp kernel: [    0.404842] pnp: PnP ACPI init
Jul 25 03:23:19 my_comp kernel: [    0.404867] ACPI: bus type pnp registered
Jul 25 03:23:19 my_comp kernel: [    0.405416] pnp 00:00: [bus 00-ff]
Jul 25 03:23:19 my_comp kernel: [    0.405419] pnp 00:00: [io  0x0000-0x0cf7 window]
Jul 25 03:23:19 my_comp kernel: [    0.405422] pnp 00:00: [io  0x0d00-0xffff window]
Jul 25 03:23:19 my_comp kernel: [    0.405425] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jul 25 03:23:19 my_comp kernel: [    0.405428] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Jul 25 03:23:19 my_comp kernel: [    0.405430] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Jul 25 03:23:19 my_comp kernel: [    0.405437] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Jul 25 03:23:19 my_comp kernel: [    0.405439] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Jul 25 03:23:19 my_comp kernel: [    0.405442] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jul 25 03:23:19 my_comp kernel: [    0.405445] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Jul 25 03:23:19 my_comp kernel: [    0.405447] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Jul 25 03:23:19 my_comp kernel: [    0.405450] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Jul 25 03:23:19 my_comp kernel: [    0.405453] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Jul 25 03:23:19 my_comp kernel: [    0.405455] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Jul 25 03:23:19 my_comp kernel: [    0.405458] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Jul 25 03:23:19 my_comp kernel: [    0.405461] pnp 00:00: [mem 0x000ec000-0x000effff window]
Jul 25 03:23:19 my_comp kernel: [    0.405464] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
Jul 25 03:23:19 my_comp kernel: [    0.405466] pnp 00:00: [mem 0xe1000000-0xffffffff window]
Jul 25 03:23:19 my_comp kernel: [    0.405469] pnp 00:00: [io  0x0cf8-0x0cff]
Jul 25 03:23:19 my_comp kernel: [    0.405563] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jul 25 03:23:19 my_comp kernel: [    0.405614] pnp 00:01: [mem 0xfec00000-0xfec00fff]
Jul 25 03:23:19 my_comp kernel: [    0.405617] pnp 00:01: [mem 0xfee00000-0xfee00fff]
Jul 25 03:23:19 my_comp kernel: [    0.405692] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 25 03:23:19 my_comp kernel: [    0.405695] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.405699] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 03:23:19 my_comp kernel: [    0.405855] pnp 00:02: [io  0x0000-0x000f]
Jul 25 03:23:19 my_comp kernel: [    0.405858] pnp 00:02: [io  0x0081-0x008f]
Jul 25 03:23:19 my_comp kernel: [    0.405860] pnp 00:02: [io  0x00c0-0x00df]
Jul 25 03:23:19 my_comp kernel: [    0.405863] pnp 00:02: [dma 4]
Jul 25 03:23:19 my_comp kernel: [    0.405903] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 25 03:23:19 my_comp kernel: [    0.405913] pnp 00:03: [io  0x00f0-0x00fe]
Jul 25 03:23:19 my_comp kernel: [    0.405962] pnp 00:03: [irq 13]
Jul 25 03:23:19 my_comp kernel: [    0.406002] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 25 03:23:19 my_comp kernel: [    0.406065] pnp 00:04: [io  0x0070-0x0071]
Jul 25 03:23:19 my_comp kernel: [    0.406103] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 25 03:23:19 my_comp kernel: [    0.406112] pnp 00:05: [io  0x0061]
Jul 25 03:23:19 my_comp kernel: [    0.406149] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Jul 25 03:23:19 my_comp kernel: [    0.406161] pnp 00:06: [io  0x0060]
Jul 25 03:23:19 my_comp kernel: [    0.406164] pnp 00:06: [io  0x0064]
Jul 25 03:23:19 my_comp kernel: [    0.406166] pnp 00:06: [io  0x0068]
Jul 25 03:23:19 my_comp kernel: [    0.406168] pnp 00:06: [io  0x006c]
Jul 25 03:23:19 my_comp kernel: [    0.406207] pnp 00:06: [irq 1]
Jul 25 03:23:19 my_comp kernel: [    0.406248] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 25 03:23:19 my_comp kernel: [    0.406294] pnp 00:07: [irq 12]
Jul 25 03:23:19 my_comp kernel: [    0.406334] pnp 00:07: Plug and Play ACPI device, IDs AUI0216 SYN0153 AUI0217 PNP0f13 (active)
Jul 25 03:23:19 my_comp kernel: [    0.406348] pnp 00:08: [io  0x0010-0x001f]
Jul 25 03:23:19 my_comp kernel: [    0.406350] pnp 00:08: [io  0x002e-0x002f]
Jul 25 03:23:19 my_comp kernel: [    0.406352] pnp 00:08: [io  0x0072-0x0073]
Jul 25 03:23:19 my_comp kernel: [    0.406355] pnp 00:08: [io  0x0080]
Jul 25 03:23:19 my_comp kernel: [    0.406357] pnp 00:08: [io  0x00b0-0x00b1]
Jul 25 03:23:19 my_comp kernel: [    0.406359] pnp 00:08: [io  0x0092]
Jul 25 03:23:19 my_comp kernel: [    0.406361] pnp 00:08: [io  0x0400-0x04cf]
Jul 25 03:23:19 my_comp kernel: [    0.406363] pnp 00:08: [io  0x04d0-0x04d1]
Jul 25 03:23:19 my_comp kernel: [    0.406366] pnp 00:08: [io  0x04d6]
Jul 25 03:23:19 my_comp kernel: [    0.406368] pnp 00:08: [io  0x0680-0x06ff]
Jul 25 03:23:19 my_comp kernel: [    0.406370] pnp 00:08: [io  0x077a]
Jul 25 03:23:19 my_comp kernel: [    0.406372] pnp 00:08: [io  0x0c00-0x0c01]
Jul 25 03:23:19 my_comp kernel: [    0.406375] pnp 00:08: [io  0x0c14]
Jul 25 03:23:19 my_comp kernel: [    0.406377] pnp 00:08: [io  0x0c50-0x0c52]
Jul 25 03:23:19 my_comp kernel: [    0.406379] pnp 00:08: [io  0x0c6c]
Jul 25 03:23:19 my_comp kernel: [    0.406381] pnp 00:08: [io  0x0c6f]
Jul 25 03:23:19 my_comp kernel: [    0.406383] pnp 00:08: [io  0x0cd0-0x0cdb]
Jul 25 03:23:19 my_comp kernel: [    0.406461] system 00:08: [io  0x0400-0x04cf] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406464] system 00:08: [io  0x04d0-0x04d1] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406467] system 00:08: [io  0x04d6] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406470] system 00:08: [io  0x0680-0x06ff] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406473] system 00:08: [io  0x077a] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406476] system 00:08: [io  0x0c00-0x0c01] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406479] system 00:08: [io  0x0c14] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406482] system 00:08: [io  0x0c50-0x0c52] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406485] system 00:08: [io  0x0c6c] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406487] system 00:08: [io  0x0c6f] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406490] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406494] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 03:23:19 my_comp kernel: [    0.406509] pnp 00:09: [mem 0x000e0000-0x000fffff]
Jul 25 03:23:19 my_comp kernel: [    0.406512] pnp 00:09: [mem 0xfff00000-0xffffffff]
Jul 25 03:23:19 my_comp kernel: [    0.406580] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Jul 25 03:23:19 my_comp kernel: [    0.406584] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
Jul 25 03:23:19 my_comp kernel: [    0.406587] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 25 03:23:19 my_comp kernel: [    0.456129] pnp 00:0a: [io  0xfd60-0xfd63]
Jul 25 03:23:19 my_comp kernel: [    0.456169] pnp 00:0a: [irq 4]
Jul 25 03:23:19 my_comp kernel: [    0.456215] pnp 00:0a: Plug and Play ACPI device, IDs ENE0100 (active)
Jul 25 03:23:19 my_comp kernel: [    0.456519] pnp: PnP ACPI: found 11 devices
Jul 25 03:23:19 my_comp kernel: [    0.456521] ACPI: ACPI bus type pnp unregistered
Jul 25 03:23:19 my_comp kernel: [    0.456524] PnPBIOS: Disabled by ACPI PNP
Jul 25 03:23:19 my_comp kernel: [    0.493464] pci 0000:08:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493472] pci 0000:0a:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493555] pci 0000:00:05.0: BAR 15: assigned [mem 0xd2600000-0xd26fffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493561] pci 0000:00:07.0: BAR 14: assigned [mem 0xd2700000-0xd27fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493565] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul 25 03:23:19 my_comp kernel: [    0.493569] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493574] pci 0000:00:01.0:   bridge window [mem 0xd2300000-0xd24fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493578] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.493584] pci 0000:00:04.0: PCI bridge to [bus 02-07]
Jul 25 03:23:19 my_comp kernel: [    0.493587] pci 0000:00:04.0:   bridge window [io  0x3000-0x6fff]
Jul 25 03:23:19 my_comp kernel: [    0.493592] pci 0000:00:04.0:   bridge window [mem 0xd1300000-0xd22fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493597] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.493603] pci 0000:08:00.0: BAR 6: assigned [mem 0xd2600000-0xd260ffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493607] pci 0000:00:05.0: PCI bridge to [bus 08-08]
Jul 25 03:23:19 my_comp kernel: [    0.493609] pci 0000:00:05.0:   bridge window [io  disabled]
Jul 25 03:23:19 my_comp kernel: [    0.493614] pci 0000:00:05.0:   bridge window [mem 0xd1200000-0xd12fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493618] pci 0000:00:05.0:   bridge window [mem 0xd2600000-0xd26fffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493624] pci 0000:00:06.0: PCI bridge to [bus 09-09]
Jul 25 03:23:19 my_comp kernel: [    0.493626] pci 0000:00:06.0:   bridge window [io  disabled]
Jul 25 03:23:19 my_comp kernel: [    0.493631] pci 0000:00:06.0:   bridge window [mem 0xd1100000-0xd11fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493634] pci 0000:00:06.0:   bridge window [mem pref disabled]
Jul 25 03:23:19 my_comp kernel: [    0.493641] pci 0000:0a:00.0: BAR 6: assigned [mem 0xd1020000-0xd103ffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493644] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
Jul 25 03:23:19 my_comp kernel: [    0.493647] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
Jul 25 03:23:19 my_comp kernel: [    0.493651] pci 0000:00:07.0:   bridge window [mem 0xd2700000-0xd27fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493656] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.493662] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
Jul 25 03:23:19 my_comp kernel: [    0.493699] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
Jul 25 03:23:19 my_comp kernel: [    0.493706] pci 0000:00:14.4:   bridge window [mem disabled]
Jul 25 03:23:19 my_comp kernel: [    0.493710] pci 0000:00:14.4:   bridge window [mem pref disabled]
Jul 25 03:23:19 my_comp kernel: [    0.493726] pci 0000:00:01.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.493742] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 03:23:19 my_comp kernel: [    0.493746] pci 0000:00:04.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.493756] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 03:23:19 my_comp kernel: [    0.493760] pci 0000:00:05.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.493768] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 03:23:19 my_comp kernel: [    0.493772] pci 0000:00:06.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.493781] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 25 03:23:19 my_comp kernel: [    0.493785] pci 0000:00:07.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.493794] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 25 03:23:19 my_comp kernel: [    0.493797] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 25 03:23:19 my_comp kernel: [    0.493799] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 25 03:23:19 my_comp kernel: [    0.493802] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 25 03:23:19 my_comp kernel: [    0.493805] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493808] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 25 03:23:19 my_comp kernel: [    0.493811] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
Jul 25 03:23:19 my_comp kernel: [    0.493813] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493816] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
Jul 25 03:23:19 my_comp kernel: [    0.493819] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
Jul 25 03:23:19 my_comp kernel: [    0.493822] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
Jul 25 03:23:19 my_comp kernel: [    0.493825] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493828] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
Jul 25 03:23:19 my_comp kernel: [    0.493830] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
Jul 25 03:23:19 my_comp kernel: [    0.493833] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
Jul 25 03:23:19 my_comp kernel: [    0.493836] pci_bus 0000:00: resource 19 [mem 0xe1000000-0xffffffff]
Jul 25 03:23:19 my_comp kernel: [    0.493839] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493842] pci_bus 0000:01: resource 1 [mem 0xd2300000-0xd24fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493845] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.493848] pci_bus 0000:02: resource 0 [io  0x3000-0x6fff]
Jul 25 03:23:19 my_comp kernel: [    0.493851] pci_bus 0000:02: resource 1 [mem 0xd1300000-0xd22fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493854] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.493857] pci_bus 0000:08: resource 1 [mem 0xd1200000-0xd12fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493860] pci_bus 0000:08: resource 2 [mem 0xd2600000-0xd26fffff pref]
Jul 25 03:23:19 my_comp kernel: [    0.493863] pci_bus 0000:09: resource 1 [mem 0xd1100000-0xd11fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493866] pci_bus 0000:0a: resource 0 [io  0x2000-0x2fff]
Jul 25 03:23:19 my_comp kernel: [    0.493869] pci_bus 0000:0a: resource 1 [mem 0xd2700000-0xd27fffff]
Jul 25 03:23:19 my_comp kernel: [    0.493872] pci_bus 0000:0a: resource 2 [mem 0xd1000000-0xd10fffff 64bit pref]
Jul 25 03:23:19 my_comp kernel: [    0.493875] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
Jul 25 03:23:19 my_comp kernel: [    0.493877] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
Jul 25 03:23:19 my_comp kernel: [    0.493880] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
Jul 25 03:23:19 my_comp kernel: [    0.493883] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
Jul 25 03:23:19 my_comp kernel: [    0.493886] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 25 03:23:19 my_comp kernel: [    0.493888] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493891] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 25 03:23:19 my_comp kernel: [    0.493894] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
Jul 25 03:23:19 my_comp kernel: [    0.493897] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493900] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
Jul 25 03:23:19 my_comp kernel: [    0.493903] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
Jul 25 03:23:19 my_comp kernel: [    0.493905] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
Jul 25 03:23:19 my_comp kernel: [    0.493908] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
Jul 25 03:23:19 my_comp kernel: [    0.493911] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
Jul 25 03:23:19 my_comp kernel: [    0.493914] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
Jul 25 03:23:19 my_comp kernel: [    0.493917] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
Jul 25 03:23:19 my_comp kernel: [    0.493920] pci_bus 0000:80: resource 19 [mem 0xe1000000-0xffffffff]
Jul 25 03:23:19 my_comp kernel: [    0.493968] NET: Registered protocol family 2
Jul 25 03:23:19 my_comp kernel: [    0.494047] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.494345] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.495091] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.495439] TCP: Hash tables configured (established 131072 bind 65536)
Jul 25 03:23:19 my_comp kernel: [    0.495442] TCP reno registered
Jul 25 03:23:19 my_comp kernel: [    0.495447] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.495462] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.495590] NET: Registered protocol family 1
Jul 25 03:23:19 my_comp kernel: [    0.495606] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Jul 25 03:23:19 my_comp kernel: [    0.495774] pci 0000:01:05.0: Boot video device
Jul 25 03:23:19 my_comp kernel: [    0.495835] PCI: CLS 64 bytes, default 64
Jul 25 03:23:19 my_comp kernel: [    0.495899] Simple Boot Flag at 0x44 set to 0x1
Jul 25 03:23:19 my_comp kernel: [    0.496250] cpufreq-nforce2: No nForce2 chipset.
Jul 25 03:23:19 my_comp kernel: [    0.496407] audit: initializing netlink socket (disabled)
Jul 25 03:23:19 my_comp kernel: [    0.496418] type=2000 audit(1311564172.492:1): initialized
Jul 25 03:23:19 my_comp kernel: [    0.507167] highmem bounce pool size: 64 pages
Jul 25 03:23:19 my_comp kernel: [    0.507174] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 25 03:23:19 my_comp kernel: [    0.509174] VFS: Disk quotas dquot_6.5.2
Jul 25 03:23:19 my_comp kernel: [    0.509236] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 25 03:23:19 my_comp kernel: [    0.509991] fuse init (API version 7.16)
Jul 25 03:23:19 my_comp kernel: [    0.510094] msgmni has been set to 1647
Jul 25 03:23:19 my_comp kernel: [    0.510415] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 25 03:23:19 my_comp kernel: [    0.510481] io scheduler noop registered
Jul 25 03:23:19 my_comp kernel: [    0.510483] io scheduler deadline registered
Jul 25 03:23:19 my_comp kernel: [    0.510501] io scheduler cfq registered (default)
Jul 25 03:23:19 my_comp kernel: [    0.510679] pcieport 0000:00:04.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.510726] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
Jul 25 03:23:19 my_comp kernel: [    0.510788] pcieport 0000:00:05.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.510823] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
Jul 25 03:23:19 my_comp kernel: [    0.510880] pcieport 0000:00:06.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.510915] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
Jul 25 03:23:19 my_comp kernel: [    0.510970] pcieport 0000:00:07.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    0.511005] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
Jul 25 03:23:19 my_comp kernel: [    0.511101] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 25 03:23:19 my_comp kernel: [    0.511131] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 25 03:23:19 my_comp kernel: [    0.513090] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 25 03:23:19 my_comp kernel: [    0.515897] ACPI: AC Adapter [ACAD] (on-line)
Jul 25 03:23:19 my_comp kernel: [    0.515966] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jul 25 03:23:19 my_comp kernel: [    0.515973] ACPI: Power Button [PWRB]
Jul 25 03:23:19 my_comp kernel: [    0.516084] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Jul 25 03:23:19 my_comp kernel: [    0.516187] ACPI: Lid Switch [LID]
Jul 25 03:23:19 my_comp kernel: [    0.516237] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 25 03:23:19 my_comp kernel: [    0.516241] ACPI: Power Button [PWRF]
Jul 25 03:23:19 my_comp kernel: [    0.516498] ACPI: acpi_idle registered with cpuidle
Jul 25 03:23:19 my_comp kernel: [    0.635569] thermal LNXTHERM:00: registered as thermal_zone0
Jul 25 03:23:19 my_comp kernel: [    0.635572] ACPI: Thermal Zone [TZ01] (66 C)
Jul 25 03:23:19 my_comp kernel: [    0.635601] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 25 03:23:19 my_comp kernel: [    0.635665] ERST: Table is not found!
Jul 25 03:23:19 my_comp kernel: [    0.635782] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 25 03:23:19 my_comp kernel: [    0.636186] isapnp: Scanning for PnP cards...
Jul 25 03:23:19 my_comp kernel: [    0.645917] Freeing initrd memory: 18336k freed
Jul 25 03:23:19 my_comp kernel: [    0.688068] ACPI: Battery Slot [BAT0] (battery absent)
Jul 25 03:23:19 my_comp kernel: [    1.020504] isapnp: No Plug & Play device found
Jul 25 03:23:19 my_comp kernel: [    1.132473] Linux agpgart interface v0.103
Jul 25 03:23:19 my_comp kernel: [    1.133840] brd: module loaded
Jul 25 03:23:19 my_comp kernel: [    1.134480] loop: module loaded
Jul 25 03:23:19 my_comp kernel: [    1.134596] i2c-core: driver [adp5520] using legacy suspend method
Jul 25 03:23:19 my_comp kernel: [    1.134598] i2c-core: driver [adp5520] using legacy resume method
Jul 25 03:23:19 my_comp kernel: [    1.134811] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 03:23:19 my_comp kernel: [    1.134895] pata_acpi 0000:00:14.1: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.135323] Fixed MDIO Bus: probed
Jul 25 03:23:19 my_comp kernel: [    1.135369] PPP generic driver version 2.4.2
Jul 25 03:23:19 my_comp kernel: [    1.135417] tun: Universal TUN/TAP device driver, 1.6
Jul 25 03:23:19 my_comp kernel: [    1.135419] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 25 03:23:19 my_comp kernel: [    1.135513] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 25 03:23:19 my_comp kernel: [    1.135565] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 25 03:23:19 my_comp kernel: [    1.135589] ehci_hcd 0000:00:12.2: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.135594] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 25 03:23:19 my_comp kernel: [    1.135638] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 25 03:23:19 my_comp kernel: [    1.136092] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 25 03:23:19 my_comp kernel: [    1.136115] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Jul 25 03:23:19 my_comp kernel: [    1.136133] ehci_hcd 0000:00:12.2: debug port 1
Jul 25 03:23:19 my_comp kernel: [    1.136164] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2508500
Jul 25 03:23:19 my_comp kernel: [    1.148056] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 25 03:23:19 my_comp kernel: [    1.148234] hub 1-0:1.0: USB hub found
Jul 25 03:23:19 my_comp kernel: [    1.148239] hub 1-0:1.0: 6 ports detected
Jul 25 03:23:19 my_comp kernel: [    1.148415] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 25 03:23:19 my_comp kernel: [    1.148443] ehci_hcd 0000:00:13.2: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.148447] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 25 03:23:19 my_comp kernel: [    1.148500] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 25 03:23:19 my_comp kernel: [    1.148578] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 25 03:23:19 my_comp kernel: [    1.148600] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Jul 25 03:23:19 my_comp kernel: [    1.148617] ehci_hcd 0000:00:13.2: debug port 1
Jul 25 03:23:19 my_comp kernel: [    1.148649] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2508400
Jul 25 03:23:19 my_comp kernel: [    1.160056] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 25 03:23:19 my_comp kernel: [    1.160200] hub 2-0:1.0: USB hub found
Jul 25 03:23:19 my_comp kernel: [    1.160206] hub 2-0:1.0: 6 ports detected
Jul 25 03:23:19 my_comp kernel: [    1.160359] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 25 03:23:19 my_comp kernel: [    1.160408] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 03:23:19 my_comp kernel: [    1.160424] ohci_hcd 0000:00:12.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.160428] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 25 03:23:19 my_comp kernel: [    1.160474] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 25 03:23:19 my_comp kernel: [    1.160568] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2507000
Jul 25 03:23:19 my_comp kernel: [    1.220159] hub 3-0:1.0: USB hub found
Jul 25 03:23:19 my_comp kernel: [    1.220200] hub 3-0:1.0: 3 ports detected
Jul 25 03:23:19 my_comp kernel: [    1.220288] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 03:23:19 my_comp kernel: [    1.220302] ohci_hcd 0000:00:12.1: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.220307] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 25 03:23:19 my_comp kernel: [    1.220358] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 25 03:23:19 my_comp kernel: [    1.220437] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2506000
Jul 25 03:23:19 my_comp kernel: [    1.280164] hub 4-0:1.0: USB hub found
Jul 25 03:23:19 my_comp kernel: [    1.280204] hub 4-0:1.0: 3 ports detected
Jul 25 03:23:19 my_comp kernel: [    1.280297] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 03:23:19 my_comp kernel: [    1.280311] ohci_hcd 0000:00:13.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.280315] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 25 03:23:19 my_comp kernel: [    1.280360] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 25 03:23:19 my_comp kernel: [    1.284087] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2505000
Jul 25 03:23:19 my_comp kernel: [    1.344156] hub 5-0:1.0: USB hub found
Jul 25 03:23:19 my_comp kernel: [    1.344197] hub 5-0:1.0: 3 ports detected
Jul 25 03:23:19 my_comp kernel: [    1.344335] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 03:23:19 my_comp kernel: [    1.344350] ohci_hcd 0000:00:13.1: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.344354] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 25 03:23:19 my_comp kernel: [    1.344396] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 25 03:23:19 my_comp kernel: [    1.348079] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2504000
Jul 25 03:23:19 my_comp kernel: [    1.408187] hub 6-0:1.0: USB hub found
Jul 25 03:23:19 my_comp kernel: [    1.408227] hub 6-0:1.0: 3 ports detected
Jul 25 03:23:19 my_comp kernel: [    1.408319] uhci_hcd: USB Universal Host Controller Interface driver
Jul 25 03:23:19 my_comp kernel: [    1.408431] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 25 03:23:19 my_comp kernel: [    1.444111] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 25 03:23:19 my_comp kernel: [    1.444127] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 25 03:23:19 my_comp kernel: [    1.444277] mousedev: PS/2 mouse device common for all mice
Jul 25 03:23:19 my_comp kernel: [    1.446935] rtc_cmos 00:04: RTC can wake from S4
Jul 25 03:23:19 my_comp kernel: [    1.447028] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jul 25 03:23:19 my_comp kernel: [    1.447092] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Jul 25 03:23:19 my_comp kernel: [    1.447195] device-mapper: uevent: version 1.0.3
Jul 25 03:23:19 my_comp kernel: [    1.447296] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Jul 25 03:23:19 my_comp kernel: [    1.447473] device-mapper: multipath: version 1.2.0 loaded
Jul 25 03:23:19 my_comp kernel: [    1.447477] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 25 03:23:19 my_comp kernel: [    1.447569] EISA: Probing bus 0 at eisa.0
Jul 25 03:23:19 my_comp kernel: [    1.447572] EISA: Cannot allocate resource for mainboard
Jul 25 03:23:19 my_comp kernel: [    1.447575] Cannot allocate resource for EISA slot 1
Jul 25 03:23:19 my_comp kernel: [    1.447577] Cannot allocate resource for EISA slot 2
Jul 25 03:23:19 my_comp kernel: [    1.447580] Cannot allocate resource for EISA slot 3
Jul 25 03:23:19 my_comp kernel: [    1.447582] Cannot allocate resource for EISA slot 4
Jul 25 03:23:19 my_comp kernel: [    1.447585] Cannot allocate resource for EISA slot 5
Jul 25 03:23:19 my_comp kernel: [    1.447587] Cannot allocate resource for EISA slot 6
Jul 25 03:23:19 my_comp kernel: [    1.447590] Cannot allocate resource for EISA slot 7
Jul 25 03:23:19 my_comp kernel: [    1.447592] Cannot allocate resource for EISA slot 8
Jul 25 03:23:19 my_comp kernel: [    1.447594] EISA: Detected 0 cards.
Jul 25 03:23:19 my_comp kernel: [    1.447737] cpuidle: using governor ladder
Jul 25 03:23:19 my_comp kernel: [    1.447740] cpuidle: using governor menu
Jul 25 03:23:19 my_comp kernel: [    1.448094] TCP cubic registered
Jul 25 03:23:19 my_comp kernel: [    1.448229] NET: Registered protocol family 10
Jul 25 03:23:19 my_comp kernel: [    1.448845] NET: Registered protocol family 17
Jul 25 03:23:19 my_comp kernel: [    1.448868] Registering the dns_resolver key type
Jul 25 03:23:19 my_comp kernel: [    1.448940] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-74 (2 cpu cores) (version 2.20.00)
Jul 25 03:23:19 my_comp kernel: [    1.448990] powernow-k8:    0 : pstate 0 (2200 MHz)
Jul 25 03:23:19 my_comp kernel: [    1.448992] powernow-k8:    1 : pstate 1 (1100 MHz)
Jul 25 03:23:19 my_comp kernel: [    1.448994] powernow-k8:    2 : pstate 2 (550 MHz)
Jul 25 03:23:19 my_comp kernel: [    1.450110] Using IPI No-Shortcut mode
Jul 25 03:23:19 my_comp kernel: [    1.450220] PM: Hibernation image not present or could not be loaded.
Jul 25 03:23:19 my_comp kernel: [    1.450235] registered taskstats version 1
Jul 25 03:23:19 my_comp kernel: [    1.450732]   Magic number: 3:24:362
Jul 25 03:23:19 my_comp kernel: [    1.450896] rtc_cmos 00:04: setting system clock to 2011-07-25 03:22:54 UTC (1311564174)
Jul 25 03:23:19 my_comp kernel: [    1.450900] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 25 03:23:19 my_comp kernel: [    1.450902] EDD information not available.
Jul 25 03:23:19 my_comp kernel: [    1.451042] Freeing unused kernel memory: 700k freed
Jul 25 03:23:19 my_comp kernel: [    1.451530] Write protecting the kernel text: 5192k
Jul 25 03:23:19 my_comp kernel: [    1.451616] Write protecting the kernel read-only data: 2148k
Jul 25 03:23:19 my_comp kernel: [    1.480585] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 25 03:23:19 my_comp kernel: [    1.485699] <30>udev[67]: starting version 167
Jul 25 03:23:19 my_comp kernel: [    1.572101] usb 1-6: new high speed USB device using ehci_hcd and address 3
Jul 25 03:23:19 my_comp kernel: [    1.615171] sdhci: Secure Digital Host Controller Interface driver
Jul 25 03:23:19 my_comp kernel: [    1.615175] sdhci: Copyright(c) Pierre Ossman
Jul 25 03:23:19 my_comp kernel: [    1.619570] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 25 03:23:19 my_comp kernel: [    1.619608] r8169 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 25 03:23:19 my_comp kernel: [    1.619654] r8169 0000:0a:00.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.619711] r8169 0000:0a:00.0: irq 44 for MSI/MSI-X
Jul 25 03:23:19 my_comp kernel: [    1.627523] scsi0 : pata_atiixp
Jul 25 03:23:19 my_comp kernel: [    1.630119] scsi1 : pata_atiixp
Jul 25 03:23:19 my_comp kernel: [    1.630808] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8000 irq 14
Jul 25 03:23:19 my_comp kernel: [    1.630812] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8008 irq 15
Jul 25 03:23:19 my_comp kernel: [    1.635578] sdhci-pci 0000:08:00.0: SDHCI controller found [197b:2382] (rev 0)
Jul 25 03:23:19 my_comp kernel: [    1.635601] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 03:23:19 my_comp kernel: [    1.635683] sdhci-pci 0000:08:00.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [    1.635696] mmc0: no vmmc regulator found
Jul 25 03:23:19 my_comp kernel: [    1.635736] Registered led device: mmc0::
Jul 25 03:23:19 my_comp kernel: [    1.635798] mmc0: SDHCI controller on PCI [0000:08:00.0] using ADMA
Jul 25 03:23:19 my_comp kernel: [    1.635809] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
Jul 25 03:23:19 my_comp kernel: [    1.635822] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 03:23:19 my_comp kernel: [    1.635829] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
Jul 25 03:23:19 my_comp kernel: [    1.635836] sdhci-pci 0000:08:00.2: PCI INT A disabled
Jul 25 03:23:19 my_comp kernel: [    1.664113] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Jul 25 03:23:19 my_comp kernel: [    1.670928] r8169 0000:0a:00.0: eth0: RTL8102e at 0xf8064000, 00:23:5a:36:b6:e4, XID 04c00000 IRQ 44
Jul 25 03:23:19 my_comp kernel: [    1.671186] acpi device:04: registered as cooling_device2
Jul 25 03:23:19 my_comp kernel: [    1.671308] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4
Jul 25 03:23:19 my_comp kernel: [    1.671389] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul 25 03:23:19 my_comp kernel: [    1.789768] ahci 0000:00:11.0: version 3.0
Jul 25 03:23:19 my_comp kernel: [    1.789803] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 25 03:23:19 my_comp kernel: [    1.790012] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0xf impl SATA mode
Jul 25 03:23:19 my_comp kernel: [    1.790016] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc sxs 
Jul 25 03:23:19 my_comp kernel: [    1.792453] scsi2 : ahci
Jul 25 03:23:19 my_comp kernel: [    1.792630] scsi3 : ahci
Jul 25 03:23:19 my_comp kernel: [    1.792724] scsi4 : ahci
Jul 25 03:23:19 my_comp kernel: [    1.792824] scsi5 : ahci
Jul 25 03:23:19 my_comp kernel: [    1.792924] scsi6 : ahci
Jul 25 03:23:19 my_comp kernel: [    1.793022] scsi7 : ahci
Jul 25 03:23:19 my_comp kernel: [    1.793184] ata3: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508100 irq 22
Jul 25 03:23:19 my_comp kernel: [    1.793189] ata4: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508180 irq 22
Jul 25 03:23:19 my_comp kernel: [    1.793193] ata5: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508200 irq 22
Jul 25 03:23:19 my_comp kernel: [    1.793198] ata6: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508280 irq 22
Jul 25 03:23:19 my_comp kernel: [    1.793201] ata7: DUMMY
Jul 25 03:23:19 my_comp kernel: [    1.793202] ata8: DUMMY
Jul 25 03:23:19 my_comp kernel: [    2.036056] usb 3-2: new full speed USB device using ohci_hcd and address 2
Jul 25 03:23:19 my_comp kernel: [    2.112077] ata4: SATA link down (SStatus 0 SControl 300)
Jul 25 03:23:19 my_comp kernel: [    2.112160] ata5: SATA link down (SStatus 0 SControl 300)
Jul 25 03:23:19 my_comp kernel: [    2.220812] usbcore: registered new interface driver uas
Jul 25 03:23:19 my_comp kernel: [    2.223452] Initializing USB Mass Storage driver...
Jul 25 03:23:19 my_comp kernel: [    2.223625] usb-storage 3-2:1.0: device ignored
Jul 25 03:23:19 my_comp kernel: [    2.223698] usb-storage 3-2:1.1: device ignored
Jul 25 03:23:19 my_comp kernel: [    2.223812] usb-storage 3-2:1.2: device ignored
Jul 25 03:23:19 my_comp kernel: [    2.223855] usbcore: registered new interface driver usb-storage
Jul 25 03:23:19 my_comp kernel: [    2.223857] USB Mass Storage support registered.
Jul 25 03:23:19 my_comp kernel: [    2.284066] ata3: softreset failed (device not ready)
Jul 25 03:23:19 my_comp kernel: [    2.284073] ata3: applying SB600 PMP SRST workaround and retrying
Jul 25 03:23:19 my_comp kernel: [    2.284094] ata6: softreset failed (device not ready)
Jul 25 03:23:19 my_comp kernel: [    2.284098] ata6: applying SB600 PMP SRST workaround and retrying
Jul 25 03:23:19 my_comp kernel: [    2.456066] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 25 03:23:19 my_comp kernel: [    2.456099] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 25 03:23:19 my_comp kernel: [    2.468804] ata6.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
Jul 25 03:23:19 my_comp kernel: [    2.482450] ata6.00: configured for UDMA/100
Jul 25 03:23:19 my_comp kernel: [    2.500711] ata3.00: ATA-8: ST9320325AS, 0001SDM1, max UDMA/133
Jul 25 03:23:19 my_comp kernel: [    2.500715] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 25 03:23:19 my_comp kernel: [    2.502926] ata3.00: configured for UDMA/133
Jul 25 03:23:19 my_comp kernel: [    2.503165] scsi 2:0:0:0: Direct-Access     ATA      ST9320325AS      0001 PQ: 0 ANSI: 5
Jul 25 03:23:19 my_comp kernel: [    2.503394] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jul 25 03:23:19 my_comp kernel: [    2.503474] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jul 25 03:23:19 my_comp kernel: [    2.503542] sd 2:0:0:0: [sda] Write Protect is off
Jul 25 03:23:19 my_comp kernel: [    2.503546] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 25 03:23:19 my_comp kernel: [    2.503571] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 25 03:23:19 my_comp kernel: [    2.504572] scsi 5:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
Jul 25 03:23:19 my_comp kernel: [    2.508298] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 25 03:23:19 my_comp kernel: [    2.508302] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 25 03:23:19 my_comp kernel: [    2.508431] sr 5:0:0:0: Attached scsi CD-ROM sr0
Jul 25 03:23:19 my_comp kernel: [    2.508520] sr 5:0:0:0: Attached scsi generic sg1 type 5
Jul 25 03:23:19 my_comp kernel: [    2.618456]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 > sda4
Jul 25 03:23:19 my_comp kernel: [    2.619084] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 25 03:23:19 my_comp kernel: [    4.279469] uvesafb: (C) 1988-2005, ATI Technologies Inc. , RS780, 01.00, OEM: ATI ATOMBIOS, VBE v3.0
Jul 25 03:23:19 my_comp kernel: [    4.299918] uvesafb: protected mode interface info at c000:a252
Jul 25 03:23:19 my_comp kernel: [    4.299923] uvesafb: pmi: set display start = c00ca2f4, set palette = c00ca3b2
Jul 25 03:23:19 my_comp kernel: [    4.299990] uvesafb: VBIOS/hardware supports DDC2 transfers
Jul 25 03:23:19 my_comp kernel: [    4.366731] uvesafb: monitor limits: vf = 60 Hz, hf = 49 kHz, clk = 69 MHz
Jul 25 03:23:19 my_comp kernel: [    4.366873] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=8192
Jul 25 03:23:19 my_comp kernel: [    4.371462] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
Jul 25 03:23:19 my_comp kernel: [    4.588486] Console: switching to colour frame buffer device 90x25
Jul 25 03:23:19 my_comp kernel: [    4.588567] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
Jul 25 03:23:19 my_comp kernel: [    4.809178] uvesafb: framebuffer at 0xc0000000, mapped to 0xf8100000, using 6144k, total 16384k
Jul 25 03:23:19 my_comp kernel: [    4.809181] fb0: VESA VGA frame buffer device
Jul 25 03:23:19 my_comp kernel: [    4.928624] EXT4-fs (sda9): INFO: recovery required on readonly filesystem
Jul 25 03:23:19 my_comp kernel: [    4.928629] EXT4-fs (sda9): write access will be enabled during recovery
Jul 25 03:23:19 my_comp kernel: [    5.186939] usb 3-2: USB disconnect, address 2
Jul 25 03:23:19 my_comp kernel: [    6.626502] EXT4-fs (sda9): orphan cleanup on readonly fs
Jul 25 03:23:19 my_comp kernel: [    6.626515] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 801137
Jul 25 03:23:19 my_comp kernel: [    6.626663] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 794144
Jul 25 03:23:19 my_comp kernel: [    6.626726] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 801144
Jul 25 03:23:19 my_comp kernel: [    6.626745] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 801141
Jul 25 03:23:19 my_comp kernel: [    6.626764] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1058297
Jul 25 03:23:19 my_comp kernel: [    6.626785] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 793933
Jul 25 03:23:19 my_comp kernel: [    6.626853] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 797405
Jul 25 03:23:19 my_comp kernel: [    6.626873] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048988
Jul 25 03:23:19 my_comp kernel: [    6.626884] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048987
Jul 25 03:23:19 my_comp kernel: [    6.626894] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048973
Jul 25 03:23:19 my_comp kernel: [    6.626904] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048972
Jul 25 03:23:19 my_comp kernel: [    6.626914] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 1048921
Jul 25 03:23:19 my_comp kernel: [    6.626922] EXT4-fs (sda9): 12 orphan inodes deleted
Jul 25 03:23:19 my_comp kernel: [    6.626925] EXT4-fs (sda9): recovery complete
Jul 25 03:23:19 my_comp kernel: [    7.056471] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
Jul 25 03:23:19 my_comp kernel: [   24.441942] <30>udev[418]: starting version 167
Jul 25 03:23:19 my_comp kernel: [   24.514054] lp: driver loaded but no devices found
Jul 25 03:23:19 my_comp kernel: [   24.536990] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
Jul 25 03:23:19 my_comp kernel: [   24.649396] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 25 03:23:19 my_comp kernel: [   24.649407] jmb38x_ms 0000:08:00.3: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [   24.651250] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 25 03:23:19 my_comp kernel: [   24.692260] type=1400 audit(1311529997.741:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=590 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   24.692672] type=1400 audit(1311529997.741:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=590 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   24.692924] type=1400 audit(1311529997.741:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=590 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   24.705004] IR NEC protocol handler initialized
Jul 25 03:23:19 my_comp kernel: [   24.708376] IR RC5(x) protocol handler initialized
Jul 25 03:23:19 my_comp kernel: [   24.708885] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xc0
Jul 25 03:23:19 my_comp kernel: [   24.708888] ene_ir: PLL freq = 1406
Jul 25 03:23:19 my_comp kernel: [   24.708890] ene_ir: KB3926C detected
Jul 25 03:23:19 my_comp kernel: [   24.708904] ene_ir: Firmware regs: c0 00
Jul 25 03:23:19 my_comp kernel: [   24.708906] ene_ir: Hardware features:
Jul 25 03:23:19 my_comp kernel: [   24.708908] ene_ir: * Uses GPIO 40 for IR demodulated input
Jul 25 03:23:19 my_comp kernel: [   24.711241] IR RC6 protocol handler initialized
Jul 25 03:23:19 my_comp kernel: [   24.723168] IR JVC protocol handler initialized
Jul 25 03:23:19 my_comp kernel: [   24.726529] IR Sony protocol handler initialized
Jul 25 03:23:19 my_comp kernel: [   24.739150] lirc_dev: IR Remote Control driver registered, major 251 
Jul 25 03:23:19 my_comp kernel: [   24.740732] IR LIRC bridge handler initialized
Jul 25 03:23:19 my_comp kernel: [   24.768785] Registered IR keymap rc-rc6-mce
Jul 25 03:23:19 my_comp kernel: [   24.769054] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input5
Jul 25 03:23:19 my_comp kernel: [   24.769960] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
Jul 25 03:23:19 my_comp kernel: [   24.774751] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
Jul 25 03:23:19 my_comp kernel: [   24.774758] ene_ir: driver has been succesfully loaded
Jul 25 03:23:19 my_comp kernel: [   24.860792] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 25 03:23:19 my_comp kernel: [   24.903352] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jul 25 03:23:19 my_comp kernel: [   24.903488] SP5100 TCO timer: mmio address 0xfec000f0 already in use
Jul 25 03:23:19 my_comp kernel: [   25.133765] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 25 03:23:19 my_comp kernel: [   25.133773] Disabling lock debugging due to kernel taint
Jul 25 03:23:19 my_comp kernel: [   25.214554] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 25 03:23:19 my_comp kernel: [   25.371321] input: HP WMI hotkeys as /devices/virtual/input/input6
Jul 25 03:23:19 my_comp kernel: [   25.437843] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul 25 03:23:19 my_comp kernel: [   25.480361] [fglrx] Maximum main memory to use for locked dma buffers: 2627 MBytes.
Jul 25 03:23:19 my_comp kernel: [   25.480455] [fglrx]   vendor: 1002 device: 9612 count: 1
Jul 25 03:23:19 my_comp kernel: [   25.481080] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jul 25 03:23:19 my_comp kernel: [   25.481099] pci 0000:01:05.0: power state changed by ACPI to D0
Jul 25 03:23:19 my_comp kernel: [   25.481104] pci 0000:01:05.0: power state changed by ACPI to D0
Jul 25 03:23:19 my_comp kernel: [   25.481114] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 25 03:23:19 my_comp kernel: [   25.481120] pci 0000:01:05.0: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [   25.481703] [fglrx] Kernel PAT support is enabled
Jul 25 03:23:19 my_comp kernel: [   25.481732] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
Jul 25 03:23:19 my_comp kernel: [   25.546430] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 25 03:23:19 my_comp kernel: [   25.546486] HDA Intel 0000:00:14.2: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [   25.648382] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jul 25 03:23:19 my_comp kernel: [   25.648503] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jul 25 03:23:19 my_comp kernel: [   25.649032] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 25 03:23:19 my_comp kernel: [   25.649121] HDA Intel 0000:01:05.1: setting latency timer to 64
Jul 25 03:23:19 my_comp kernel: [   25.686166] Linux video capture interface: v2.00
Jul 25 03:23:19 my_comp kernel: [   25.696715] uvcvideo: Found UVC 1.00 device USB Camera Device (174f:5216)
Jul 25 03:23:19 my_comp kernel: [   25.731186] input: USB Camera Device as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input9
Jul 25 03:23:19 my_comp kernel: [   25.731284] usbcore: registered new interface driver uvcvideo
Jul 25 03:23:19 my_comp kernel: [   25.731287] USB Video Class driver (v1.0.0)
Jul 25 03:23:19 my_comp kernel: [   25.855515] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
Jul 25 03:23:19 my_comp kernel: [   25.897638] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Successfully dropped root privileges.
Jul 25 03:23:19 my_comp avahi-daemon[1061]: avahi-daemon 0.6.30 starting up.
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Successfully called chroot().
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Successfully dropped remaining capabilities.
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Loading service file /services/udisks.service.
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> NetworkManager (version 0.8.3.998) is starting...
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 25 03:23:19 my_comp kernel: [   26.732609] type=1400 audit(1311529999.781:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1071 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   26.735836] type=1400 audit(1311529999.781:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1070 comm="apparmor_parser"
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Network interface enumeration completed.
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Registering HINFO record with values 'I686'/'LINUX'.
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Server startup complete. Host name is my_comp.local. Local service cookie is 2921589008.
Jul 25 03:23:19 my_comp avahi-daemon[1061]: Service "my_comp" (/services/udisks.service) successfully established.
Jul 25 03:23:19 my_comp kernel: [   26.737618] type=1400 audit(1311529999.785:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1071 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   26.737876] type=1400 audit(1311529999.785:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1071 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   26.752467] type=1400 audit(1311529999.801:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1072 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   26.755542] type=1400 audit(1311529999.801:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1074 comm="apparmor_parser"
Jul 25 03:23:19 my_comp kernel: [   26.761855] type=1400 audit(1311529999.809:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1072 comm="apparmor_parser"
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> trying to start the modem manager...
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  ModemManager (version 0.4) starting...
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Linktop
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Gobi
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin SimTech
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Option
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Generic
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Huawei
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin X22X
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin AnyData
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Ericsson MBM
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Sierra
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Option High-Speed
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Novatel
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Longcheer
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin MotoC
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin Nokia
Jul 25 03:23:19 my_comp modem-manager[1144]: <info>  Loaded plugin ZTE
Jul 25 03:23:19 my_comp polkitd[1147]: started daemon version 0.101 using authority implementation `local' version `0.101'
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: init!
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: update_system_hostname
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPluginIfupdown: management mode: managed
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:0a:00.0/net/eth0, iface: eth0)
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:0a:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: end _init.
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: (138203680) ... get_connections.
Jul 25 03:23:19 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: (138203680) connections count: 0
Jul 25 03:23:19 my_comp NetworkManager[1065]:    keyfile: parsing Auto eth0 ... 
Jul 25 03:23:19 my_comp NetworkManager[1065]:    keyfile:     read connection 'Auto eth0'
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/hp-wmi/rfkill/rfkill0) (driver hp-wmi)
Jul 25 03:23:19 my_comp gdm-binary[1052]: WARNING: Unable to find users: no seat-id found
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> Networking is enabled by state file
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): carrier is OFF
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): now managed
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): bringing up device.
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): preparing device.
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> (eth0): deactivating device (reason: 2).
Jul 25 03:23:19 my_comp kernel: [   26.935443] r8169 0000:0a:00.0: eth0: link down
Jul 25 03:23:19 my_comp kernel: [   26.935743] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> modem-manager is now available
Jul 25 03:23:19 my_comp NetworkManager[1065]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 25 03:23:19 my_comp NetworkManager[1065]: <info> Trying to start the supplicant...
Jul 25 03:23:20 my_comp kernel: [   27.184433] [fglrx] ATIF platform detected with notification ID: 0x81
Jul 25 03:23:20 my_comp kernel: [   27.529609] [fglrx] GART Table is not in FRAME_BUFFER range 
Jul 25 03:23:20 my_comp kernel: [   27.529933] [fglrx] Could not enable MSI; System prevented initialization
Jul 25 03:23:20 my_comp kernel: [   27.530749] [fglrx] Firegl kernel thread PID: 1268
Jul 25 03:23:20 my_comp kernel: [   27.530912] [fglrx] Firegl kernel thread PID: 1269
Jul 25 03:23:20 my_comp kernel: [   27.530988] [fglrx] Firegl kernel thread PID: 1270
Jul 25 03:23:20 my_comp kernel: [   27.531367] [fglrx] IRQ 18 Enabled
Jul 25 03:23:20 my_comp init: apport pre-start process (1279) terminated with status 1
Jul 25 03:23:20 my_comp cron[1288]: (CRON) INFO (pidfile fd = 3)
Jul 25 03:23:20 my_comp acpid: starting up with proc fs
Jul 25 03:23:20 my_comp acpid: 34 rules loaded
Jul 25 03:23:20 my_comp acpid: waiting for events: event logging is off
Jul 25 03:23:20 my_comp anacron[1326]: Anacron 2.3 started on 2011-07-25
Jul 25 03:23:20 my_comp init: apport post-stop process (1333) terminated with status 1
Jul 25 03:23:20 my_comp cron[1371]: (CRON) STARTUP (fork ok)
Jul 25 03:23:20 my_comp cron[1371]: (CRON) INFO (Running @reboot jobs)
Jul 25 03:23:20 my_comp anacron[1326]: Normal exit (0 jobs run)
Jul 25 03:23:21 my_comp kernel: [   28.505775] ppdev: user-space parallel port driver
Jul 25 03:23:21 my_comp kernel: [   28.915909] Intel AES-NI instructions are not detected.
Jul 25 03:23:21 my_comp kernel: [   28.933441] padlock_aes: VIA PadLock not detected.
Jul 25 03:23:22 my_comp kernel: [   28.967178] [fglrx] Gart USWC size:864 M.
Jul 25 03:23:22 my_comp kernel: [   28.967184] [fglrx] Gart cacheable size:342 M.
Jul 25 03:23:22 my_comp kernel: [   28.967190] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul 25 03:23:22 my_comp kernel: [   28.967193] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Jul 25 03:23:22 my_comp kernel: [   29.075594] padlock_sha: VIA PadLock Hash Engine not detected.
Jul 25 03:23:22 my_comp modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.38-8-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Jul 25 03:23:22 my_comp kernel: [   29.359195] Adding 2880508k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2880508k 
Jul 25 03:23:25 my_comp anacron[1856]: Anacron 2.3 started on 2011-07-25
Jul 25 03:23:25 my_comp anacron[1856]: Normal exit (0 jobs run)
Jul 25 03:23:26 my_comp gdm-simple-greeter[1787]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jul 25 03:23:26 my_comp kernel: [   33.859854] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro,commit=0
Jul 25 03:23:27 my_comp gdm-simple-greeter[1787]: WARNING: Unable to load CK history: no seat-id found
Jul 25 03:23:27 my_comp gdm-simple-greeter[1787]: WARNING: Unable to parse history: (null)   4#012
Jul 25 03:23:29 my_comp kernel: [   36.277499] vboxdrv: Found 2 processor cores.
Jul 25 03:23:29 my_comp kernel: [   36.278227] vboxdrv: fAsync=1 offMin=0xe44e011 offMax=0xe44e011
Jul 25 03:23:29 my_comp kernel: [   36.279145] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Jul 25 03:23:29 my_comp kernel: [   36.279149] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
Jul 25 03:23:29 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jul 25 03:23:29 my_comp NetworkManager[1065]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jul 25 03:23:29 my_comp NetworkManager[1065]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jul 25 03:23:30 my_comp init: plymouth-stop pre-start process (2678) terminated with status 1
Jul 25 03:24:33 my_comp init: mysql post-start process (1328) terminated with status 1
Jul 25 03:25:59 my_comp gdm-session-worker[1790]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jul 25 03:26:12 my_comp gdm-session-worker[1790]: pam_sm_authenticate: Called
Jul 25 03:26:12 my_comp gdm-session-worker[1790]: pam_sm_authenticate: username = [user]
Jul 25 03:26:12 my_comp gdm-session-worker[2753]: Passphrase file wrapped
Jul 25 03:27:03 my_comp acpid: client connected from 2997[113:123]
Jul 25 03:27:03 my_comp acpid: 1 client rule loaded

```Something I had also left out that could be of importance, I occasionally get a weird UI when I log on which goes away and back to the default after I logout and log back i. I have attached a screenshot

---

### Post by galvatron408 on 2011-07-24
stopping net-manager doesn't disable it. just go to "system -> preferences -> startup applications and uncheck network manager

i think you attached the wrong picture

---

### Post by joshmo on 2011-07-25
I managed to get to the root of the problem. I had set large buffer pool size values for InnoDB in MySQL. When the mysql process started during startup it was slowing down the PC. Tried stopping the process and restarting it when already logged on and the effect was the same. I reverted the values back to defaults and all was okay. I am going to mark the thread solved but for another unrelated question, does that mean that Ubuntu processes are started before you logon and if so, when at the startup point are they started?

About the screenshot, it was the intended picture, the UI had some kind of Windows ME look instead of the Ubuntu look. Dunno what the problem was. I have attached the two screenshots, the Ubuntu normal look and the weird windows ME one.

---

### Post by galvatron408 on 2011-07-25
great. i knew you would figure it out sooner or later. those logs are your friend.

i don't know about the screen shots. i've never seen my screen theme change like that.

---

