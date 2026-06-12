---
title: "Servers need reboot often"
date: 2010-12-13
forum: General Help
---

### Post by gypsumwolf on 2010-12-13
I have 2 Linux servers that I work on. They both run Ubuntu Server Edition, one is 10.04 and the other is 10.10. Just about every morning they need to be rebooted in-order for them to respond as a print and Apache server.

One is a Sempron CPU and the other a AMD K6-2.

What are problems which might make this happen?

---

### Post by gypsumwolf on 2010-12-13
My guesses would be:

1) Not enough airflow inside case lets these servers overheat.

2) The power flow from the power company or in the buildings are not constant and I would need to add a UPS battery backup.

3) The routers the server is connected to have something going on with them.

---

### Post by efflandt on 2010-12-13
Do any of them have nics that use the **tulip** module?  I don't know if that is still an issue, but years ago I had a problem where overnight an old Netgear nic using tulip stopped responding and I was unable to make an outgoing connection unless I pinged it from elsewhere on the LAN.  Although, I do not have that trouble with a DEC chip that now uses tulip on an old K6/2-400 running IPCop w/squid.  So with the built-in DEC nic and a different nic using different module, I have no network issues and only automatically reboot it weekly (from cron) to clear its measly 128 MB RAM.

I have also had trouble with a certain Dlink card, I think 530TX+ using **8139too** module, where it can go into a frenzy trying to auto-negotiate speed with some devices (causing heavy packet loss) unless I force it back to 10baseT (full duplex works).  So for that I have to use **mii-tool -A 10baseT-FD eth0** (or whichever device).  By only advertising that speed, I have a headless PC in my basement that has been running continuously since July 2006 without rebooting and no issues.

So other than checking the logs for anything unusual, if a server is not responding, first see it can access the network itself, and without any packet loss.

---

### Post by gypsumwolf on 2010-12-16
Well I had the same issue on 4 different computers and 2 different routers and 2 different states. I am trying a UPC battery backup to see if it is because of some random power issue.

I am attaching the router and the server both to the upc.

---

### Post by efflandt on 2010-12-16
What are the symptoms?  And have you checked the logs for anything unusual.  Kind of difficult to troubleshoot with no information about what is NOT working (ie, why do you feel you have to reboot).

---

### Post by gypsumwolf on 2010-12-16
As soon as I reboot then I can access my website with my domain name. I am not running a dns server.

---

### Post by gypsumwolf on 2010-12-20
The Battery backup did not change anything, but i did find out something interesting. I was at work and tried it in the morning and it worked, then I tried it in the afternoon and it did not work, so I called my wife and she tried to go to my website at home in our internal network and it worked for her. After she did that I tried to go to it from work and it worked right away. We both used the same Domain Name to try and access it every time.

It seems like the computer may be asleep and then it wakes up on my local network but not from an external network.

lspci
```

00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

last few lines of: /var/log/messages
```

Dec 20 20:00:39 hostname kernel: [335895.910735] type=1400 audit(1292893239.741:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6880 comm="apparmor_parser"
Dec 20 20:00:39 hostname kernel: [335895.982927] type=1400 audit(1292893239.813:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6884 comm="apparmor_parser"
Dec 20 20:00:46 hostname kernel: [335902.788809] udev[7033]: starting version 163
Dec 20 20:00:55 hostname kernel: [335912.101856] type=1400 audit(1292893255.933:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7104 comm="apparmor_parser"
Dec 20 20:00:55 hostname kernel: [335912.102280] type=1400 audit(1292893255.933:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7104 comm="apparmor_parser"
Dec 20 20:00:55 hostname kernel: [335912.102498] type=1400 audit(1292893255.933:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7104 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.266045] type=1400 audit(1292893256.097:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7105 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.436493] type=1400 audit(1292893256.269:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7106 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.778189] type=1400 audit(1292893256.609:18): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7142 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.778607] type=1400 audit(1292893256.609:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7142 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.778821] type=1400 audit(1292893256.609:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7142 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.939744] type=1400 audit(1292893256.769:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7143 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335913.097823] type=1400 audit(1292893256.929:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7144 comm="apparmor_parser"

```

my entire dmesg
```

[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 0 - 1fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130943
[    0.000000] free_area_init_node: node 0, pgdat c083ea40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x0c] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dffc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1600000 s39872 r0 d21568 u2097152
[    0.000000] pcpu-alloc: s39872 r0 d21568 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic-pae root=/dev/mapper/unserv-root ro quiet
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2620800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (38 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009f965c]   TEXT DATA BSS
[    0.000000]   #3 [001753a000 - 0018034000]         RAMDISK
[    0.000000]   #4 [000009f800 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009fa000 - 0000a01106]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001401000]         BOOTMEM
[    0.000000]   #11 [0001401000 - 0001401004]         BOOTMEM
[    0.000000]   #12 [0001401040 - 0001401100]         BOOTMEM
[    0.000000]   #13 [0001401100 - 0001401160]         BOOTMEM
[    0.000000]   #14 [0001401180 - 0001402980]         BOOTMEM
[    0.000000]   #15 [0001402980 - 00014029af]         BOOTMEM
[    0.000000]   #16 [00014029c0 - 0001402ae0]         BOOTMEM
[    0.000000]   #17 [0001402b00 - 0001402b40]         BOOTMEM
[    0.000000]   #18 [0001402b40 - 0001402b80]         BOOTMEM
[    0.000000]   #19 [0001402b80 - 0001402bc0]         BOOTMEM
[    0.000000]   #20 [0001402bc0 - 0001402c00]         BOOTMEM
[    0.000000]   #21 [0001402c00 - 0001402c40]         BOOTMEM
[    0.000000]   #22 [0001402c40 - 0001402c80]         BOOTMEM
[    0.000000]   #23 [0001402c80 - 0001402cc0]         BOOTMEM
[    0.000000]   #24 [0001402cc0 - 0001402cd0]         BOOTMEM
[    0.000000]   #25 [0001402d00 - 0001402d50]         BOOTMEM
[    0.000000]   #26 [0001402d80 - 0001402dd0]         BOOTMEM
[    0.000000]   #27 [0001600000 - 000160f000]         BOOTMEM
[    0.000000]   #28 [0001404e00 - 0001404e04]         BOOTMEM
[    0.000000]   #29 [0001404e40 - 0001404e44]         BOOTMEM
[    0.000000]   #30 [0001404e80 - 0001404e84]         BOOTMEM
[    0.000000]   #31 [0001404ec0 - 0001404ec4]         BOOTMEM
[    0.000000]   #32 [0001404f00 - 0001404fa8]         BOOTMEM
[    0.000000]   #33 [0001404fc0 - 0001405028]         BOOTMEM
[    0.000000]   #34 [0001402e00 - 0001404e00]         BOOTMEM
[    0.000000]   #35 [0001405040 - 0001445040]         BOOTMEM
[    0.000000]   #36 [0001445040 - 0001465040]         BOOTMEM
[    0.000000]   #37 [000160f000 - 000188ed80]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 496160k/524224k available (5085k kernel code, 27612k reserved, 2432k data, 704k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xe07f0000 - 0xffbfe000   ( 500 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.000000]       .init : 0xc0858000 - 0xc0908000   ( 704 kB)
[    0.000000]       .data : 0xc05f748a - 0xc0857768   (2432 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f748a   (5085 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1599.520 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.04 BogoMIPS (lpj=6398080)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004053] Security Framework initialized
[    0.004102] AppArmor: AppArmor initialized
[    0.004105] Yama: becoming mindful.
[    0.004205] Mount-cache hash table entries: 512
[    0.004447] Initializing cgroup subsys ns
[    0.004455] Initializing cgroup subsys cpuacct
[    0.004462] Initializing cgroup subsys memory
[    0.004477] Initializing cgroup subsys devices
[    0.004482] Initializing cgroup subsys freezer
[    0.004486] Initializing cgroup subsys net_cls
[    0.004533] mce: CPU supports 4 MCE banks
[    0.004569] Performance Events: AMD PMU driver.
[    0.004579] ... version:                0
[    0.004582] ... bit width:              48
[    0.004585] ... generic registers:      4
[    0.004588] ... value mask:             0000ffffffffffff
[    0.004591] ... max period:             00007fffffffffff
[    0.004594] ... fixed-purpose events:   0
[    0.004597] ... event mask:             000000000000000f
[    0.005584] SMP alternatives: switching to UP code
[    0.016072] Freeing SMP alternatives: 24k freed
[    0.016147] ACPI: Core revision 20100428
[    0.024017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024034] ftrace: allocating 22394 entries in 44 pages
[    0.032150] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.033234] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072921] CPU0: AMD Athlon(tm) XP 1900+ stepping 02
[    0.076000] Brought up 1 CPUs
[    0.076000] Total of 1 processors activated (3199.04 BogoMIPS).
[    0.076000] devtmpfs: initialized
[    0.076000] regulator: core version 0.5
[    0.076000] Time:  3:42:21  Date: 12/17/10
[    0.076000] NET: Registered protocol family 16
[    0.076000] EISA bus registered
[    0.076000] ACPI: bus type pci registered
[    0.083970] PCI: PCI BIOS revision 2.10 entry at 0xfd7ee, last bus=1
[    0.083974] PCI: Using configuration type 1 for base access
[    0.085633] bio: create slab <bio-0> at 0
[    0.086582] ACPI: EC: Look up EC in DSDT
[    0.092807] ACPI: Interpreter enabled
[    0.092814] ACPI: (supports S0 S1 S4 S5)
[    0.092844] ACPI: Using IOAPIC for interrupt routing
[    0.098275] ACPI: No dock devices found.
[    0.098284] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.098461] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.098770] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.098776] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.098780] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000fffff] (ignored)
[    0.098785] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xffffffff] (ignored)
[    0.098821] pci 0000:00:00.0: reg 10: [mem 0xd4000000-0xd7ffffff pref]
[    0.098906] pci 0000:00:01.0: supports D1
[    0.099008] pci 0000:00:07.1: reg 20: [io  0x1400-0x140f]
[    0.099070] pci 0000:00:07.2: reg 20: [io  0x1420-0x143f]
[    0.099133] pci 0000:00:07.3: reg 20: [io  0x1440-0x145f]
[    0.099210] pci 0000:00:07.4: quirk: [io  0x6800-0x687f] claimed by vt82c686 HW-mon
[    0.099216] pci 0000:00:07.4: quirk: [io  0x0400-0x040f] claimed by vt82c686 SMB
[    0.099257] pci 0000:00:07.5: reg 10: [io  0x1000-0x10ff]
[    0.099264] pci 0000:00:07.5: reg 14: [io  0x1414-0x1417]
[    0.099271] pci 0000:00:07.5: reg 18: [io  0x1410-0x1413]
[    0.099335] pci 0000:00:0f.0: reg 10: [mem 0xd0000000-0xd00000ff]
[    0.099343] pci 0000:00:0f.0: reg 14: [io  0x1418-0x141f]
[    0.099350] pci 0000:00:0f.0: reg 18: [io  0x1800-0x18ff]
[    0.099378] pci 0000:00:0f.0: supports D2
[    0.099382] pci 0000:00:0f.0: PME# supported from D2 D3hot D3cold
[    0.099388] pci 0000:00:0f.0: PME# disabled
[    0.099418] pci 0000:00:12.0: reg 10: [io  0x1c00-0x1cff]
[    0.099425] pci 0000:00:12.0: reg 14: [mem 0xd0000400-0xd00004ff]
[    0.099457] pci 0000:00:12.0: supports D1 D2
[    0.099460] pci 0000:00:12.0: PME# supported from D1 D2 D3hot
[    0.099465] pci 0000:00:12.0: PME# disabled
[    0.099524] pci 0000:01:00.0: reg 10: [mem 0xd1000000-0xd1ffffff]
[    0.099531] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff pref]
[    0.099549] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.099595] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.099601] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.099607] pci 0000:00:01.0:   bridge window [mem 0xd1000000-0xd1ffffff]
[    0.099613] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.099621] pci_bus 0000:00: on NUMA node 0
[    0.099628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[    0.103447] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.103620] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[    0.103808] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.104009] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[    0.104261] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 9 14 15) *0
[    0.104510] ACPI: PCI Interrupt Link [LNKS] (IRQs 3 4 5 6 7 10 14 15) *0
[    0.104577] HEST: Table is not found!
[    0.104767] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.104772] vgaarb: loaded
[    0.105074] SCSI subsystem initialized
[    0.105249] libata version 3.00 loaded.
[    0.105366] usbcore: registered new interface driver usbfs
[    0.105398] usbcore: registered new interface driver hub
[    0.105455] usbcore: registered new device driver usb
[    0.105712] ACPI: WMI: Mapper loaded
[    0.105717] PCI: Using ACPI for IRQ routing
[    0.105724] PCI: pci_cache_line_size set to 32 bytes
[    0.105785] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.105790] reserve RAM buffer: 000000001fff0000 - 000000001fffffff 
[    0.105983] NetLabel: Initializing
[    0.105986] NetLabel:  domain hash size = 128
[    0.105989] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.106015] NetLabel:  unlabeled traffic allowed by default
[    0.106095] Switching to clocksource tsc
[    0.122172] AppArmor: AppArmor Filesystem Enabled
[    0.122221] pnp: PnP ACPI init
[    0.122269] ACPI: bus type pnp registered
[    0.125746] ACPI Error: Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) (20100428/dsopcode-597)
[    0.125758] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node df81d9d8), AE_AML_BUFFER_LIMIT
[    0.125790] ACPI Error (uteval-0250): Method execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node df81d9d8), AE_AML_BUFFER_LIMIT
[    0.125800] pnp 00:0c: can't evaluate _CRS: 12298
[    0.126363] pnp: PnP ACPI: found 13 devices
[    0.126366] ACPI: ACPI bus type pnp unregistered
[    0.126373] PnPBIOS: Disabled by ACPI PNP
[    0.126409] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.126414] system 00:08: [io  0x8000-0x807f] has been reserved
[    0.126419] system 00:08: [io  0x6800-0x687f] has been reserved
[    0.126424] system 00:08: [io  0x0400-0x040f] has been reserved
[    0.126430] system 00:08: [mem 0xfffc0000-0xffffffff] has been reserved
[    0.126435] system 00:08: [mem 0xfff80000-0xfffbffff] has been reserved
[    0.126440] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.126445] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.163532] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.163539] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.163543] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.163552] pci 0000:00:01.0:   bridge window [mem 0xd1000000-0xd1ffffff]
[    0.163558] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.163583] pci 0000:00:01.0: setting latency timer to 64
[    0.163590] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.163594] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    0.163600] pci_bus 0000:01: resource 1 [mem 0xd1000000-0xd1ffffff]
[    0.163604] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff pref]
[    0.163699] NET: Registered protocol family 2
[    0.163819] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.164196] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.164567] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.164908] TCP: Hash tables configured (established 16384 bind 16384)
[    0.164912] TCP reno registered
[    0.164918] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.164942] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.165123] NET: Registered protocol family 1
[    0.165158] pci 0000:00:00.0: Applying VIA southbridge workaround
[    0.165166] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.165175] pci 0000:00:07.0: Enabling VIA external APIC routing
[    0.165234] pci 0000:01:00.0: Boot video device
[    0.165238] PCI: CLS 32 bytes, default 32
[    0.165470] Simple Boot Flag at 0x36 set to 0x1
[    0.165739] cpufreq-nforce2: No nForce2 chipset.
[    0.165796] Scanning for low memory corruption every 60 seconds
[    0.166043] audit: initializing netlink socket (disabled)
[    0.166066] type=2000 audit(1292557341.164:1): initialized
[    0.180266] Trying to unpack rootfs image as initramfs...
[    0.198273] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.206293] VFS: Disk quotas dquot_6.5.2
[    0.206504] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.207610] fuse init (API version 7.14)
[    0.207751] msgmni has been set to 969
[    0.215188] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.215197] io scheduler noop registered
[    0.215200] io scheduler deadline registered
[    0.215219] io scheduler cfq registered (default)
[    0.215429] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.215468] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.215812] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.215824] ACPI: Power Button [PWRB]
[    0.215903] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.215909] ACPI: Power Button [PWRF]
[    0.216090] ACPI: acpi_idle registered with cpuidle
[    0.218437] ERST: Table is not found!
[    0.218877] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.219079] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.219233] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.219680] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.219858] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.221737] brd: module loaded
[    0.226057] isapnp: Scanning for PnP cards...
[    0.232484] loop: module loaded
[    0.233755] Fixed MDIO Bus: probed
[    0.233814] PPP generic driver version 2.4.2
[    0.238038] tun: Universal TUN/TAP device driver, 1.6
[    0.238047] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.238351] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.238403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.238426] uhci_hcd: USB Universal Host Controller Interface driver
[    0.238897] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 9
[    0.238920] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKU] -> GSI 9 (level, low) -> IRQ 9
[    0.238943] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    0.239006] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    0.239071] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001420
[    0.239358] hub 1-0:1.0: USB hub found
[    0.239369] hub 1-0:1.0: 2 ports detected
[    0.239459] uhci_hcd 0000:00:07.3: PCI INT D -> Link[LNKU] -> GSI 9 (level, low) -> IRQ 9
[    0.239471] uhci_hcd 0000:00:07.3: UHCI Host Controller
[    0.239535] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[    0.239560] uhci_hcd 0000:00:07.3: irq 9, io base 0x00001440
[    0.239753] hub 2-0:1.0: USB hub found
[    0.239761] hub 2-0:1.0: 2 ports detected
[    0.239934] PNP: PS/2 Controller [PNP0303:KBC] at 0x60,0x64 irq 1
[    0.239938] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.240130] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.240325] mice: PS/2 mouse device common for all mice
[    0.240545] rtc_cmos 00:03: RTC can wake from S4
[    0.240625] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.240678] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.240889] device-mapper: uevent: version 1.0.3
[    0.290374] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.294080] device-mapper: multipath: version 1.1.1 loaded
[    0.294093] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.294516] EISA: Probing bus 0 at eisa.0
[    0.294534] Cannot allocate resource for EISA slot 1
[    0.294564] Cannot allocate resource for EISA slot 6
[    0.294573] Cannot allocate resource for EISA slot 8
[    0.294576] EISA: Detected 0 cards.
[    0.298399] cpuidle: using governor ladder
[    0.298408] cpuidle: using governor menu
[    0.298957] TCP cubic registered
[    0.299243] NET: Registered protocol family 10
[    0.299789] lo: Disabled Privacy Extensions
[    0.300093] NET: Registered protocol family 17
[    0.300174] powernow-k8: Processor cpuid 662 not supported
[    0.300225] Using IPI No-Shortcut mode
[    0.300441] PM: Resume from disk failed.
[    0.300464] registered taskstats version 1
[    0.300690]   Magic number: 6:314:715
[    0.300873] rtc_cmos 00:03: setting system clock to 2010-12-17 03:42:22 UTC (1292557342)
[    0.300879] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.300882] EDD information not available.
[    0.901649] isapnp: No Plug & Play device found
[    1.039595] Freeing initrd memory: 11240k freed
[    1.073609] Freeing unused kernel memory: 704k freed
[    1.075698] Write protecting the kernel text: 5088k
[    1.075803] Write protecting the kernel read-only data: 2012k
[    1.122507] udev[63]: starting version 163
[    1.484153] pata_via 0000:00:07.1: version 0.3.4
[    1.495318] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.514585] scsi0 : pata_via
[    1.529209] scsi1 : pata_via
[    1.530381] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1400 irq 14
[    1.530387] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1408 irq 15
[    1.541517] Floppy drive(s): fd0 is 1.44M
[    1.541637] 8139cp 0000:00:12.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.560099] FDC 0 is a post-1991 82077
[    1.693549] ata1.00: ATA-6: WDC WD2000JB-00FUA0, 15.05R15, max UDMA/100
[    1.693558] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.693591] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.709483] ata1.00: configured for UDMA/33
[    1.709743] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JB-00F 15.0 PQ: 0 ANSI: 5
[    1.710110] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.710412] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.710513] sd 0:0:0:0: [sda] Write Protect is off
[    1.710517] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.710560] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.710854]  sda: sda1 sda2 < sda5 >
[    1.745262] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.888348] ata2.00: ATAPI: Hewlett-Packard CD-Writer  cd16f, 1.1D, max UDMA/33
[    1.888396] ata2.01: ATAPI: SAMSUNG DVD-ROM SD-616F, F100, max UDMA/33
[    1.920353] ata2.00: configured for UDMA/33
[    1.928456] ata2.01: configured for UDMA/33
[    1.933810] scsi 1:0:0:0: CD-ROM            HP       CD-Writer cd16f  1.1D PQ: 0 ANSI: 5
[    1.941017] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.941029] Uniform CD-ROM driver Revision: 3.20
[    1.941296] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.941434] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.941997] scsi 1:0:1:0: CD-ROM            SAMSUNG  DVD-ROM SD-616F  F100 PQ: 0 ANSI: 5
[    1.943921] sr1: scsi3-mmc drive: 1x/40x cd/rw xa/form2 cdda tray
[    1.944216] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.944356] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.968240] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.968381] 8139too 0000:00:12.0: enabling device (0000 -> 0003)
[    1.968397]   alloc irq_desc for 17 on node -1
[    1.968401]   alloc kstat_irqs on node -1
[    1.968417] 8139too 0000:00:12.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.969671] 8139too 0000:00:12.0: eth0: RealTek RTL8139 at 0x1c00, 00:e0:18:57:e7:e2, IRQ 17
[    2.578339] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    2.578352] EXT4-fs (dm-0): write access will be enabled during recovery
[    4.203817] EXT4-fs (dm-0): orphan cleanup on readonly fs
[    4.203849] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932171
[    4.203944] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932170
[    4.203959] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932169
[    4.203974] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932168
[    4.203987] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932167
[    4.203998] EXT4-fs (dm-0): 5 orphan inodes deleted
[    4.204012] EXT4-fs (dm-0): recovery complete
[    4.534268] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   10.636758] Adding 1535996k swap on /dev/mapper/unserv-swap_1.  Priority:-1 extents:1 across:1535996k 
[   10.660446] udev[303]: starting version 163
[   10.894517] ACPI: resource vt596_smbus [io  0x0400-0x0407] conflicts with ACPI region SMIO [??? 0x00000400-0x00000407 flags 0x4f]
[   10.894527] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.942688] parport_pc: VIA 686A/8231 detected
[   10.942696] parport_pc: probing current configuration
[   10.942716] parport_pc: Current parallel port base: 0x378
[   10.942800] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   10.949395] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.956708] lp: driver loaded but no devices found
[   11.156849] ACPI: resource via686a [io  0x6800-0x687f] conflicts with ACPI region HMIO [??? 0x00006800-0x0000684f flags 0x4f]
[   11.156858] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.157676] lp0: using parport0 (interrupt-driven).
[   11.157785] parport_pc: VIA parallel port: io=0x378, irq=7
[   11.159088] Linux agpgart interface v0.103
[   11.163401] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   11.276082] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   11.513328] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   11.801142] type=1400 audit(1292557353.995:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=465 comm="apparmor_parser"
[   11.801580] type=1400 audit(1292557353.995:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=465 comm="apparmor_parser"
[   11.801855] type=1400 audit(1292557353.995:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=465 comm="apparmor_parser"
[   11.866675] ppdev: user-space parallel port driver
[   11.996853] [drm] Initialized drm 1.1.0 20060810
[   12.208700] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   12.212799] ACPI: PCI Interrupt Link [LNKS] enabled at IRQ 10
[   12.212825] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKS] -> GSI 10 (level, low) -> IRQ 10
[   12.212997] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
[   12.265051]   alloc irq_desc for 16 on node -1
[   12.265060]   alloc kstat_irqs on node -1
[   12.265078] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.276342] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x436300a1)
[   12.276742] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   12.320131] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   12.320360] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   12.320365] [drm] nouveau 0000:01:00.0: BMP version 5.40
[   12.320371] [drm] nouveau 0000:01:00.0: Bios version 04.36.20.30
[   12.320377] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2
[   12.320383] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00009c40
[   12.320391] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02010310 00009c40
[   12.320395] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01010312 00000000
[   12.320399] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02020321 00000303
[   12.320657] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode
[   12.320663] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xF062
[   12.320718] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xF526
[   12.321916] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xF79F
[   12.321966] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xF912
[   12.322060] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF92F
[   12.322255] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0xF94C
[   12.328052] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0xF9D5
[   12.328065] [drm] nouveau 0000:01:00.0: Detected 256MiB VRAM
[   12.342647] [TTM] Zone  kernel: Available graphics memory: 254064 kiB.
[   12.342653] [TTM] Initializing pool allocator.
[   12.342848] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   12.342872] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   12.342918] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[   12.342924] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   12.343378] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   12.345601] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   12.345621] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   12.345631] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   12.395935] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   12.396554] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   12.397203] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   12.398716] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   12.398722] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[   12.398728] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
[   12.398734] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[   12.536061] No connectors reported connected with modes
[   12.536079] [drm] Cannot find any crtc or sizes - going 1024x768
[   12.536741] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x49000, bo de42d800
[   12.542624] Console: switching to colour frame buffer device 128x48
[   12.544239] fb0: nouveaufb frame buffer device
[   12.544243] drm: registered panic notifier
[   12.544251] Slow work thread pool: Starting up
[   12.544393] Slow work thread pool: Ready
[   12.544414] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   14.463590] type=1400 audit(1292557356.655:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=628 comm="apparmor_parser"
[   14.474799] type=1400 audit(1292557356.667:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[   14.475134] type=1400 audit(1292557356.667:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[   14.489309] type=1400 audit(1292557356.683:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=633 comm="apparmor_parser"
[   14.521859] type=1400 audit(1292557356.715:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=634 comm="apparmor_parser"
[   14.955744] type=1400 audit(1292557357.147:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=712 comm="apparmor_parser"
[   22.928019] eth0: no IPv6 routers present
[29259.533188] unattended-upgr[1712]: segfault at 0 ip 001c87f1 sp bfd825cc error 4 in libc-2.12.1.so[154000+157000]
[114880.911196] unattended-upgr[7137]: segfault at 0 ip 003977f1 sp bfc7392c error 4 in libc-2.12.1.so[323000+157000]
[201020.325852] unattended-upgr[15113]: segfault at 0 ip 003257f1 sp bfddb5dc error 4 in libc-2.12.1.so[2b1000+157000]
[288427.818474] unattended-upgr[17671]: segfault at 0 ip 004907f1 sp bfc6233c error 4 in libc-2.12.1.so[41c000+157000]
[335868.457867] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[335868.468621] SGI XFS Quota Management subsystem
[335868.489015] JFS: nTxBlock = 3969, nTxLock = 31758
[335868.540385] NTFS driver 2.1.29 [Flags: R/O MODULE].
[335868.587338] QNX4 filesystem 0.2.3 registered.
[335868.656596] Btrfs loaded
[335895.910735] type=1400 audit(1292893239.741:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6880 comm="apparmor_parser"
[335895.982927] type=1400 audit(1292893239.813:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6884 comm="apparmor_parser"
[335902.788809] udev[7033]: starting version 163
[335912.101856] type=1400 audit(1292893255.933:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7104 comm="apparmor_parser"
[335912.102280] type=1400 audit(1292893255.933:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7104 comm="apparmor_parser"
[335912.102498] type=1400 audit(1292893255.933:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7104 comm="apparmor_parser"
[335912.266045] type=1400 audit(1292893256.097:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7105 comm="apparmor_parser"
[335912.436493] type=1400 audit(1292893256.269:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7106 comm="apparmor_parser"
[335912.778189] type=1400 audit(1292893256.609:18): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7142 comm="apparmor_parser"
[335912.778607] type=1400 audit(1292893256.609:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7142 comm="apparmor_parser"
[335912.778821] type=1400 audit(1292893256.609:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7142 comm="apparmor_parser"
[335912.939744] type=1400 audit(1292893256.769:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7143 comm="apparmor_parser"
[335913.097823] type=1400 audit(1292893256.929:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7144 comm="apparmor_parser"

```

---

### Post by sandyd on 2010-12-20
> **gypsumwolf said:**
> The Battery backup did not change anything, but i did find out something interesting. I was at work and tried it in the morning and it worked, then I tried it in the afternoon and it did not work, so I called my wife and she tried to go to my website at home in our internal network and it worked for her. After she did that I tried to go to it from work and it worked right away. We both used the same Domain Name to try and access it every time.

It seems like the computer may be asleep and then it wakes up on my local network but not from an external network.

lspci
```

00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```last few lines of: /var/log/messages
```

Dec 20 20:00:39 hostname kernel: [335895.910735] type=1400 audit(1292893239.741:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6880 comm="apparmor_parser"
Dec 20 20:00:39 hostname kernel: [335895.982927] type=1400 audit(1292893239.813:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6884 comm="apparmor_parser"
Dec 20 20:00:46 hostname kernel: [335902.788809] udev[7033]: starting version 163
Dec 20 20:00:55 hostname kernel: [335912.101856] type=1400 audit(1292893255.933:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7104 comm="apparmor_parser"
Dec 20 20:00:55 hostname kernel: [335912.102280] type=1400 audit(1292893255.933:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7104 comm="apparmor_parser"
Dec 20 20:00:55 hostname kernel: [335912.102498] type=1400 audit(1292893255.933:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7104 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.266045] type=1400 audit(1292893256.097:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7105 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.436493] type=1400 audit(1292893256.269:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7106 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.778189] type=1400 audit(1292893256.609:18): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7142 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.778607] type=1400 audit(1292893256.609:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7142 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.778821] type=1400 audit(1292893256.609:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7142 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335912.939744] type=1400 audit(1292893256.769:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7143 comm="apparmor_parser"
Dec 20 20:00:56 hostname kernel: [335913.097823] type=1400 audit(1292893256.929:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7144 comm="apparmor_parser"

```my entire dmesg
```

[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 0 - 1fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130943
[    0.000000] free_area_init_node: node 0, pgdat c083ea40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x0c] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dffc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1600000 s39872 r0 d21568 u2097152
[    0.000000] pcpu-alloc: s39872 r0 d21568 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic-pae root=/dev/mapper/unserv-root ro quiet
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2620800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (38 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009f965c]   TEXT DATA BSS
[    0.000000]   #3 [001753a000 - 0018034000]         RAMDISK
[    0.000000]   #4 [000009f800 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009fa000 - 0000a01106]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001401000]         BOOTMEM
[    0.000000]   #11 [0001401000 - 0001401004]         BOOTMEM
[    0.000000]   #12 [0001401040 - 0001401100]         BOOTMEM
[    0.000000]   #13 [0001401100 - 0001401160]         BOOTMEM
[    0.000000]   #14 [0001401180 - 0001402980]         BOOTMEM
[    0.000000]   #15 [0001402980 - 00014029af]         BOOTMEM
[    0.000000]   #16 [00014029c0 - 0001402ae0]         BOOTMEM
[    0.000000]   #17 [0001402b00 - 0001402b40]         BOOTMEM
[    0.000000]   #18 [0001402b40 - 0001402b80]         BOOTMEM
[    0.000000]   #19 [0001402b80 - 0001402bc0]         BOOTMEM
[    0.000000]   #20 [0001402bc0 - 0001402c00]         BOOTMEM
[    0.000000]   #21 [0001402c00 - 0001402c40]         BOOTMEM
[    0.000000]   #22 [0001402c40 - 0001402c80]         BOOTMEM
[    0.000000]   #23 [0001402c80 - 0001402cc0]         BOOTMEM
[    0.000000]   #24 [0001402cc0 - 0001402cd0]         BOOTMEM
[    0.000000]   #25 [0001402d00 - 0001402d50]         BOOTMEM
[    0.000000]   #26 [0001402d80 - 0001402dd0]         BOOTMEM
[    0.000000]   #27 [0001600000 - 000160f000]         BOOTMEM
[    0.000000]   #28 [0001404e00 - 0001404e04]         BOOTMEM
[    0.000000]   #29 [0001404e40 - 0001404e44]         BOOTMEM
[    0.000000]   #30 [0001404e80 - 0001404e84]         BOOTMEM
[    0.000000]   #31 [0001404ec0 - 0001404ec4]         BOOTMEM
[    0.000000]   #32 [0001404f00 - 0001404fa8]         BOOTMEM
[    0.000000]   #33 [0001404fc0 - 0001405028]         BOOTMEM
[    0.000000]   #34 [0001402e00 - 0001404e00]         BOOTMEM
[    0.000000]   #35 [0001405040 - 0001445040]         BOOTMEM
[    0.000000]   #36 [0001445040 - 0001465040]         BOOTMEM
[    0.000000]   #37 [000160f000 - 000188ed80]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 496160k/524224k available (5085k kernel code, 27612k reserved, 2432k data, 704k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xe07f0000 - 0xffbfe000   ( 500 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.000000]       .init : 0xc0858000 - 0xc0908000   ( 704 kB)
[    0.000000]       .data : 0xc05f748a - 0xc0857768   (2432 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f748a   (5085 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1599.520 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.04 BogoMIPS (lpj=6398080)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004053] Security Framework initialized
[    0.004102] AppArmor: AppArmor initialized
[    0.004105] Yama: becoming mindful.
[    0.004205] Mount-cache hash table entries: 512
[    0.004447] Initializing cgroup subsys ns
[    0.004455] Initializing cgroup subsys cpuacct
[    0.004462] Initializing cgroup subsys memory
[    0.004477] Initializing cgroup subsys devices
[    0.004482] Initializing cgroup subsys freezer
[    0.004486] Initializing cgroup subsys net_cls
[    0.004533] mce: CPU supports 4 MCE banks
[    0.004569] Performance Events: AMD PMU driver.
[    0.004579] ... version:                0
[    0.004582] ... bit width:              48
[    0.004585] ... generic registers:      4
[    0.004588] ... value mask:             0000ffffffffffff
[    0.004591] ... max period:             00007fffffffffff
[    0.004594] ... fixed-purpose events:   0
[    0.004597] ... event mask:             000000000000000f
[    0.005584] SMP alternatives: switching to UP code
[    0.016072] Freeing SMP alternatives: 24k freed
[    0.016147] ACPI: Core revision 20100428
[    0.024017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024034] ftrace: allocating 22394 entries in 44 pages
[    0.032150] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.033234] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072921] CPU0: AMD Athlon(tm) XP 1900+ stepping 02
[    0.076000] Brought up 1 CPUs
[    0.076000] Total of 1 processors activated (3199.04 BogoMIPS).
[    0.076000] devtmpfs: initialized
[    0.076000] regulator: core version 0.5
[    0.076000] Time:  3:42:21  Date: 12/17/10
[    0.076000] NET: Registered protocol family 16
[    0.076000] EISA bus registered
[    0.076000] ACPI: bus type pci registered
[    0.083970] PCI: PCI BIOS revision 2.10 entry at 0xfd7ee, last bus=1
[    0.083974] PCI: Using configuration type 1 for base access
[    0.085633] bio: create slab <bio-0> at 0
[    0.086582] ACPI: EC: Look up EC in DSDT
[    0.092807] ACPI: Interpreter enabled
[    0.092814] ACPI: (supports S0 S1 S4 S5)
[    0.092844] ACPI: Using IOAPIC for interrupt routing
[    0.098275] ACPI: No dock devices found.
[    0.098284] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.098461] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.098770] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.098776] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.098780] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000fffff] (ignored)
[    0.098785] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xffffffff] (ignored)
[    0.098821] pci 0000:00:00.0: reg 10: [mem 0xd4000000-0xd7ffffff pref]
[    0.098906] pci 0000:00:01.0: supports D1
[    0.099008] pci 0000:00:07.1: reg 20: [io  0x1400-0x140f]
[    0.099070] pci 0000:00:07.2: reg 20: [io  0x1420-0x143f]
[    0.099133] pci 0000:00:07.3: reg 20: [io  0x1440-0x145f]
[    0.099210] pci 0000:00:07.4: quirk: [io  0x6800-0x687f] claimed by vt82c686 HW-mon
[    0.099216] pci 0000:00:07.4: quirk: [io  0x0400-0x040f] claimed by vt82c686 SMB
[    0.099257] pci 0000:00:07.5: reg 10: [io  0x1000-0x10ff]
[    0.099264] pci 0000:00:07.5: reg 14: [io  0x1414-0x1417]
[    0.099271] pci 0000:00:07.5: reg 18: [io  0x1410-0x1413]
[    0.099335] pci 0000:00:0f.0: reg 10: [mem 0xd0000000-0xd00000ff]
[    0.099343] pci 0000:00:0f.0: reg 14: [io  0x1418-0x141f]
[    0.099350] pci 0000:00:0f.0: reg 18: [io  0x1800-0x18ff]
[    0.099378] pci 0000:00:0f.0: supports D2
[    0.099382] pci 0000:00:0f.0: PME# supported from D2 D3hot D3cold
[    0.099388] pci 0000:00:0f.0: PME# disabled
[    0.099418] pci 0000:00:12.0: reg 10: [io  0x1c00-0x1cff]
[    0.099425] pci 0000:00:12.0: reg 14: [mem 0xd0000400-0xd00004ff]
[    0.099457] pci 0000:00:12.0: supports D1 D2
[    0.099460] pci 0000:00:12.0: PME# supported from D1 D2 D3hot
[    0.099465] pci 0000:00:12.0: PME# disabled
[    0.099524] pci 0000:01:00.0: reg 10: [mem 0xd1000000-0xd1ffffff]
[    0.099531] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff pref]
[    0.099549] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.099595] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.099601] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.099607] pci 0000:00:01.0:   bridge window [mem 0xd1000000-0xd1ffffff]
[    0.099613] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.099621] pci_bus 0000:00: on NUMA node 0
[    0.099628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[    0.103447] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.103620] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[    0.103808] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.104009] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[    0.104261] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 9 14 15) *0
[    0.104510] ACPI: PCI Interrupt Link [LNKS] (IRQs 3 4 5 6 7 10 14 15) *0
[    0.104577] HEST: Table is not found!
[    0.104767] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.104772] vgaarb: loaded
[    0.105074] SCSI subsystem initialized
[    0.105249] libata version 3.00 loaded.
[    0.105366] usbcore: registered new interface driver usbfs
[    0.105398] usbcore: registered new interface driver hub
[    0.105455] usbcore: registered new device driver usb
[    0.105712] ACPI: WMI: Mapper loaded
[    0.105717] PCI: Using ACPI for IRQ routing
[    0.105724] PCI: pci_cache_line_size set to 32 bytes
[    0.105785] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.105790] reserve RAM buffer: 000000001fff0000 - 000000001fffffff 
[    0.105983] NetLabel: Initializing
[    0.105986] NetLabel:  domain hash size = 128
[    0.105989] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.106015] NetLabel:  unlabeled traffic allowed by default
[    0.106095] Switching to clocksource tsc
[    0.122172] AppArmor: AppArmor Filesystem Enabled
[    0.122221] pnp: PnP ACPI init
[    0.122269] ACPI: bus type pnp registered
[    0.125746] ACPI Error: Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) (20100428/dsopcode-597)
[    0.125758] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node df81d9d8), AE_AML_BUFFER_LIMIT
[    0.125790] ACPI Error (uteval-0250): Method execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node df81d9d8), AE_AML_BUFFER_LIMIT
[    0.125800] pnp 00:0c: can't evaluate _CRS: 12298
[    0.126363] pnp: PnP ACPI: found 13 devices
[    0.126366] ACPI: ACPI bus type pnp unregistered
[    0.126373] PnPBIOS: Disabled by ACPI PNP
[    0.126409] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.126414] system 00:08: [io  0x8000-0x807f] has been reserved
[    0.126419] system 00:08: [io  0x6800-0x687f] has been reserved
[    0.126424] system 00:08: [io  0x0400-0x040f] has been reserved
[    0.126430] system 00:08: [mem 0xfffc0000-0xffffffff] has been reserved
[    0.126435] system 00:08: [mem 0xfff80000-0xfffbffff] has been reserved
[    0.126440] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.126445] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.163532] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.163539] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.163543] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.163552] pci 0000:00:01.0:   bridge window [mem 0xd1000000-0xd1ffffff]
[    0.163558] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.163583] pci 0000:00:01.0: setting latency timer to 64
[    0.163590] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.163594] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    0.163600] pci_bus 0000:01: resource 1 [mem 0xd1000000-0xd1ffffff]
[    0.163604] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff pref]
[    0.163699] NET: Registered protocol family 2
[    0.163819] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.164196] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.164567] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.164908] TCP: Hash tables configured (established 16384 bind 16384)
[    0.164912] TCP reno registered
[    0.164918] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.164942] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.165123] NET: Registered protocol family 1
[    0.165158] pci 0000:00:00.0: Applying VIA southbridge workaround
[    0.165166] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.165175] pci 0000:00:07.0: Enabling VIA external APIC routing
[    0.165234] pci 0000:01:00.0: Boot video device
[    0.165238] PCI: CLS 32 bytes, default 32
[    0.165470] Simple Boot Flag at 0x36 set to 0x1
[    0.165739] cpufreq-nforce2: No nForce2 chipset.
[    0.165796] Scanning for low memory corruption every 60 seconds
[    0.166043] audit: initializing netlink socket (disabled)
[    0.166066] type=2000 audit(1292557341.164:1): initialized
[    0.180266] Trying to unpack rootfs image as initramfs...
[    0.198273] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.206293] VFS: Disk quotas dquot_6.5.2
[    0.206504] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.207610] fuse init (API version 7.14)
[    0.207751] msgmni has been set to 969
[    0.215188] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.215197] io scheduler noop registered
[    0.215200] io scheduler deadline registered
[    0.215219] io scheduler cfq registered (default)
[    0.215429] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.215468] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.215812] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.215824] ACPI: Power Button [PWRB]
[    0.215903] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.215909] ACPI: Power Button [PWRF]
[    0.216090] ACPI: acpi_idle registered with cpuidle
[    0.218437] ERST: Table is not found!
[    0.218877] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.219079] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.219233] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.219680] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.219858] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.221737] brd: module loaded
[    0.226057] isapnp: Scanning for PnP cards...
[    0.232484] loop: module loaded
[    0.233755] Fixed MDIO Bus: probed
[    0.233814] PPP generic driver version 2.4.2
[    0.238038] tun: Universal TUN/TAP device driver, 1.6
[    0.238047] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.238351] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.238403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.238426] uhci_hcd: USB Universal Host Controller Interface driver
[    0.238897] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 9
[    0.238920] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKU] -> GSI 9 (level, low) -> IRQ 9
[    0.238943] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    0.239006] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    0.239071] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001420
[    0.239358] hub 1-0:1.0: USB hub found
[    0.239369] hub 1-0:1.0: 2 ports detected
[    0.239459] uhci_hcd 0000:00:07.3: PCI INT D -> Link[LNKU] -> GSI 9 (level, low) -> IRQ 9
[    0.239471] uhci_hcd 0000:00:07.3: UHCI Host Controller
[    0.239535] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[    0.239560] uhci_hcd 0000:00:07.3: irq 9, io base 0x00001440
[    0.239753] hub 2-0:1.0: USB hub found
[    0.239761] hub 2-0:1.0: 2 ports detected
[    0.239934] PNP: PS/2 Controller [PNP0303:KBC] at 0x60,0x64 irq 1
[    0.239938] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.240130] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.240325] mice: PS/2 mouse device common for all mice
[    0.240545] rtc_cmos 00:03: RTC can wake from S4
[    0.240625] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.240678] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.240889] device-mapper: uevent: version 1.0.3
[    0.290374] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.294080] device-mapper: multipath: version 1.1.1 loaded
[    0.294093] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.294516] EISA: Probing bus 0 at eisa.0
[    0.294534] Cannot allocate resource for EISA slot 1
[    0.294564] Cannot allocate resource for EISA slot 6
[    0.294573] Cannot allocate resource for EISA slot 8
[    0.294576] EISA: Detected 0 cards.
[    0.298399] cpuidle: using governor ladder
[    0.298408] cpuidle: using governor menu
[    0.298957] TCP cubic registered
[    0.299243] NET: Registered protocol family 10
[    0.299789] lo: Disabled Privacy Extensions
[    0.300093] NET: Registered protocol family 17
[    0.300174] powernow-k8: Processor cpuid 662 not supported
[    0.300225] Using IPI No-Shortcut mode
[    0.300441] PM: Resume from disk failed.
[    0.300464] registered taskstats version 1
[    0.300690]   Magic number: 6:314:715
[    0.300873] rtc_cmos 00:03: setting system clock to 2010-12-17 03:42:22 UTC (1292557342)
[    0.300879] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.300882] EDD information not available.
[    0.901649] isapnp: No Plug & Play device found
[    1.039595] Freeing initrd memory: 11240k freed
[    1.073609] Freeing unused kernel memory: 704k freed
[    1.075698] Write protecting the kernel text: 5088k
[    1.075803] Write protecting the kernel read-only data: 2012k
[    1.122507] udev[63]: starting version 163
[    1.484153] pata_via 0000:00:07.1: version 0.3.4
[    1.495318] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.514585] scsi0 : pata_via
[    1.529209] scsi1 : pata_via
[    1.530381] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1400 irq 14
[    1.530387] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1408 irq 15
[    1.541517] Floppy drive(s): fd0 is 1.44M
[    1.541637] 8139cp 0000:00:12.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.560099] FDC 0 is a post-1991 82077
[    1.693549] ata1.00: ATA-6: WDC WD2000JB-00FUA0, 15.05R15, max UDMA/100
[    1.693558] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.693591] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.709483] ata1.00: configured for UDMA/33
[    1.709743] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JB-00F 15.0 PQ: 0 ANSI: 5
[    1.710110] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.710412] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.710513] sd 0:0:0:0: [sda] Write Protect is off
[    1.710517] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.710560] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.710854]  sda: sda1 sda2 < sda5 >
[    1.745262] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.888348] ata2.00: ATAPI: Hewlett-Packard CD-Writer  cd16f, 1.1D, max UDMA/33
[    1.888396] ata2.01: ATAPI: SAMSUNG DVD-ROM SD-616F, F100, max UDMA/33
[    1.920353] ata2.00: configured for UDMA/33
[    1.928456] ata2.01: configured for UDMA/33
[    1.933810] scsi 1:0:0:0: CD-ROM            HP       CD-Writer cd16f  1.1D PQ: 0 ANSI: 5
[    1.941017] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.941029] Uniform CD-ROM driver Revision: 3.20
[    1.941296] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.941434] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.941997] scsi 1:0:1:0: CD-ROM            SAMSUNG  DVD-ROM SD-616F  F100 PQ: 0 ANSI: 5
[    1.943921] sr1: scsi3-mmc drive: 1x/40x cd/rw xa/form2 cdda tray
[    1.944216] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.944356] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.968240] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.968381] 8139too 0000:00:12.0: enabling device (0000 -> 0003)
[    1.968397]   alloc irq_desc for 17 on node -1
[    1.968401]   alloc kstat_irqs on node -1
[    1.968417] 8139too 0000:00:12.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.969671] 8139too 0000:00:12.0: eth0: RealTek RTL8139 at 0x1c00, 00:e0:18:57:e7:e2, IRQ 17
[    2.578339] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    2.578352] EXT4-fs (dm-0): write access will be enabled during recovery
[    4.203817] EXT4-fs (dm-0): orphan cleanup on readonly fs
[    4.203849] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932171
[    4.203944] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932170
[    4.203959] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932169
[    4.203974] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932168
[    4.203987] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 3932167
[    4.203998] EXT4-fs (dm-0): 5 orphan inodes deleted
[    4.204012] EXT4-fs (dm-0): recovery complete
[    4.534268] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   10.636758] Adding 1535996k swap on /dev/mapper/unserv-swap_1.  Priority:-1 extents:1 across:1535996k 
[   10.660446] udev[303]: starting version 163
[   10.894517] ACPI: resource vt596_smbus [io  0x0400-0x0407] conflicts with ACPI region SMIO [??? 0x00000400-0x00000407 flags 0x4f]
[   10.894527] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.942688] parport_pc: VIA 686A/8231 detected
[   10.942696] parport_pc: probing current configuration
[   10.942716] parport_pc: Current parallel port base: 0x378
[   10.942800] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   10.949395] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.956708] lp: driver loaded but no devices found
[   11.156849] ACPI: resource via686a [io  0x6800-0x687f] conflicts with ACPI region HMIO [??? 0x00006800-0x0000684f flags 0x4f]
[   11.156858] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.157676] lp0: using parport0 (interrupt-driven).
[   11.157785] parport_pc: VIA parallel port: io=0x378, irq=7
[   11.159088] Linux agpgart interface v0.103
[   11.163401] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   11.276082] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   11.513328] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   11.801142] type=1400 audit(1292557353.995:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=465 comm="apparmor_parser"
[   11.801580] type=1400 audit(1292557353.995:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=465 comm="apparmor_parser"
[   11.801855] type=1400 audit(1292557353.995:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=465 comm="apparmor_parser"
[   11.866675] ppdev: user-space parallel port driver
[   11.996853] [drm] Initialized drm 1.1.0 20060810
[   12.208700] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   12.212799] ACPI: PCI Interrupt Link [LNKS] enabled at IRQ 10
[   12.212825] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKS] -> GSI 10 (level, low) -> IRQ 10
[   12.212997] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
[   12.265051]   alloc irq_desc for 16 on node -1
[   12.265060]   alloc kstat_irqs on node -1
[   12.265078] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.276342] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x436300a1)
[   12.276742] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   12.320131] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   12.320360] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   12.320365] [drm] nouveau 0000:01:00.0: BMP version 5.40
[   12.320371] [drm] nouveau 0000:01:00.0: Bios version 04.36.20.30
[   12.320377] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2
[   12.320383] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00009c40
[   12.320391] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02010310 00009c40
[   12.320395] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01010312 00000000
[   12.320399] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02020321 00000303
[   12.320657] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode
[   12.320663] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xF062
[   12.320718] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xF526
[   12.321916] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xF79F
[   12.321966] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xF912
[   12.322060] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF92F
[   12.322255] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0xF94C
[   12.328052] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0xF9D5
[   12.328065] [drm] nouveau 0000:01:00.0: Detected 256MiB VRAM
[   12.342647] [TTM] Zone  kernel: Available graphics memory: 254064 kiB.
[   12.342653] [TTM] Initializing pool allocator.
[   12.342848] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   12.342872] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   12.342918] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[   12.342924] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   12.343378] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   12.345601] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   12.345621] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   12.345631] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   12.395935] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   12.396554] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   12.397203] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   12.398716] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   12.398722] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[   12.398728] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
[   12.398734] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[   12.536061] No connectors reported connected with modes
[   12.536079] [drm] Cannot find any crtc or sizes - going 1024x768
[   12.536741] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x49000, bo de42d800
[   12.542624] Console: switching to colour frame buffer device 128x48
[   12.544239] fb0: nouveaufb frame buffer device
[   12.544243] drm: registered panic notifier
[   12.544251] Slow work thread pool: Starting up
[   12.544393] Slow work thread pool: Ready
[   12.544414] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   14.463590] type=1400 audit(1292557356.655:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=628 comm="apparmor_parser"
[   14.474799] type=1400 audit(1292557356.667:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[   14.475134] type=1400 audit(1292557356.667:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[   14.489309] type=1400 audit(1292557356.683:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=633 comm="apparmor_parser"
[   14.521859] type=1400 audit(1292557356.715:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=634 comm="apparmor_parser"
[   14.955744] type=1400 audit(1292557357.147:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=712 comm="apparmor_parser"
[   22.928019] eth0: no IPv6 routers present
[29259.533188] unattended-upgr[1712]: segfault at 0 ip 001c87f1 sp bfd825cc error 4 in libc-2.12.1.so[154000+157000]
[114880.911196] unattended-upgr[7137]: segfault at 0 ip 003977f1 sp bfc7392c error 4 in libc-2.12.1.so[323000+157000]
[201020.325852] unattended-upgr[15113]: segfault at 0 ip 003257f1 sp bfddb5dc error 4 in libc-2.12.1.so[2b1000+157000]
[288427.818474] unattended-upgr[17671]: segfault at 0 ip 004907f1 sp bfc6233c error 4 in libc-2.12.1.so[41c000+157000]
[335868.457867] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[335868.468621] SGI XFS Quota Management subsystem
[335868.489015] JFS: nTxBlock = 3969, nTxLock = 31758
[335868.540385] NTFS driver 2.1.29 [Flags: R/O MODULE].
[335868.587338] QNX4 filesystem 0.2.3 registered.
[335868.656596] Btrfs loaded
[335895.910735] type=1400 audit(1292893239.741:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6880 comm="apparmor_parser"
[335895.982927] type=1400 audit(1292893239.813:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=6884 comm="apparmor_parser"
[335902.788809] udev[7033]: starting version 163
[335912.101856] type=1400 audit(1292893255.933:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7104 comm="apparmor_parser"
[335912.102280] type=1400 audit(1292893255.933:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7104 comm="apparmor_parser"
[335912.102498] type=1400 audit(1292893255.933:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7104 comm="apparmor_parser"
[335912.266045] type=1400 audit(1292893256.097:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7105 comm="apparmor_parser"
[335912.436493] type=1400 audit(1292893256.269:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7106 comm="apparmor_parser"
[335912.778189] type=1400 audit(1292893256.609:18): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=7142 comm="apparmor_parser"
[335912.778607] type=1400 audit(1292893256.609:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7142 comm="apparmor_parser"
[335912.778821] type=1400 audit(1292893256.609:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=7142 comm="apparmor_parser"
[335912.939744] type=1400 audit(1292893256.769:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7143 comm="apparmor_parser"
[335913.097823] type=1400 audit(1292893256.929:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=7144 comm="apparmor_parser"

```
do you ahve wakeup on lan enabled in your bios?

---

### Post by gypsumwolf on 2010-12-20
BIOS does not have that option.

A simple work-around that may work is making a cron job to do a small task every so often.

maybe I need to do acpi=off or noacpi or something in grub?

I notice other people have had this same issue.

[http://fixunix.com/ubuntu/535519-ubuntu-home-server-suspends-itself.html]("http://fixunix.com/ubuntu/535519-ubuntu-home-server-suspends-itself.html")

[http://ubuntuforums.org/showthread.php?t=1397722]("http://ubuntuforums.org/showthread.php?t=1397722")

This one is Solaris
[http://www.unix.com/solaris/17975-remove-server-sleep-mode.html]("http://www.unix.com/solaris/17975-remove-server-sleep-mode.html")

---

### Post by gypsumwolf on 2010-12-21
I set up a cron job to access hard drive every hour. The cron job works, but I still have to wait and see if it keeps the server awake.

Shouldn't it wake up if someone tries to use the server from the internet even if there is no wake-on-lan bios option?

Would it be a setting in my router like
> Filter Anonymous Internet Requests

When enabled, this feature keeps your network from being "pinged" or detected, by other Internet users. It also hides your network ports. Both make it more difficult for outside users to enter your network. This filter is selected by default. Deselect the feature to allow anonymous Internet requests.

If I turn that off would that let it wake up?

or could it be the SPI firewall?
> Firewall Protection
	

A firewall enhances network security and uses Stateful Packet Inspection (SPI) for more detailed review of data packets entering your network. Select Enabled to use a firewall, or Disabled to disable it.

---

### Post by gypsumwolf on 2010-12-21
I set cron to run a script every hour and then delete the file that is created once a day. It seems to be working at the moment my server is still up. To be sure this is keeping it alive I need to wait a day or 2. Maybe it's just because my bios does not have the wake-on-lan option?

---

### Post by gypsumwolf on 2011-01-02
What actually seems to work is setting up a cron job to ping the gateway every hour. So far my server is up and solid. This bug needs to be fixed asap. I would say it is a big black mark on Ubuntu Server Edition.

---

