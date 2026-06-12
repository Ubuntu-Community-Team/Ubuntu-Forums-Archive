---
title: "Computer Crashing W/ Ubuntu 9.10 and winXP"
date: 2009-11-25
forum: General Help
---

### Post by uknowho008 on 2009-11-25
Hey guys, I'm trying to help a friend with an Intel P4, HP computer. It used to run fine with XP but it started crashing a lot and running extremely slow. so I reinstalled XP and it had the same problem, so I installed Ubuntu for them at it runs much better but crashes when curtain programs run, for instance opening a power point file in openoffice. anyway I'm thinking maybe the processor is overheating?? any other ideas?

running cat on /var/log/messages gives me lines and lines of

```
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.349021] CPU0: Temperature/speed normal
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.355571] CPU0: Temperature/speed normal
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.363433] CPU0: Temperature/speed normal
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.369990] CPU0: Temperature/speed normal
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.377199] CPU0: Temperature/speed normal
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.384727] CPU0: Temperature/speed normal
Nov 25 18:06:01 pebbles-desktop kernel: [ 4124.390628] CPU0: Temperature/speed normal
Nov 25 18:06:02 pebbles-desktop kernel: [ 4124.398821] CPU0: Temperature/speed normal
Nov 25 18:06:02 pebbles-desktop kernel: [ 4124.407993] CPU0: Temperature/speed normal

```

but here is /var/log/messages from the time of opening a pps file and rebooting after the computer crashes

```
Nov 25 20:06:30 pebbles-desktop pulseaudio[1671]: pid.c: Stale PID file, overwriting.
Nov 25 20:06:30 pebbles-desktop pulseaudio[1671]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Nov 25 20:06:30 pebbles-desktop pulseaudio[1671]: alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Nov 25 20:06:31 pebbles-desktop pulseaudio[1671]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-A3AwXSVk3J: Connection refused
Nov 25 20:06:41 pebbles-desktop pulseaudio[1740]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Nov 25 20:06:41 pebbles-desktop pulseaudio[1740]: alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Nov 25 20:07:18 pebbles-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov 25 20:07:18 pebbles-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="843" x-info="http://www.rsyslog.com"] (re)start
Nov 25 20:07:18 pebbles-desktop rsyslogd: rsyslogd's groupid changed to 102
Nov 25 20:07:18 pebbles-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] KERNEL supported cpus:
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   Intel GenuineIntel
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   NSC Geode by NSC
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   Centaur CentaurHauls
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 000000001f7f0000 - 000000001f7f3000 (ACPI NVS)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 000000001f7f3000 - 000000001f800000 (ACPI data)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] DMI 2.3 present.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] last_pfn = 0x1f7f0 max_arch_pfn = 0x100000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] modified physical RAM map:
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000001f7f0000 (usable)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 000000001f7f0000 - 000000001f7f3000 (ACPI NVS)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 000000001f7f3000 - 000000001f800000 (ACPI data)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f7f0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] RAMDISK: 172e9000 - 17a338c9
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] ACPI Error: A valid RSDP was not found 20090521 tbxfroot-219
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] 503MB LOWMEM available.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   mapped low ram: 0 - 1f7f0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   low ram: 0 - 1f7f0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 1f7f0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   node 0 bootmap 00011000 - 00014f00
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f7f0000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #4 [00172e9000 - 0017a338c9]          RAMDISK ==> [00172e9000 - 0017a338c9]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #6 [00008a9000 - 00008ac194]              BRK ==> [00008a9000 - 00008ac194]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] found SMP MP-table at [c00f5f00] f5f00
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f7f0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]   HighMem  0x0001f7f0 -> 0x0001f7f0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0001f7f0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Using APIC driver default
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     Virtual Wire compatibility mode.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] MPTABLE: OEM ID: OEM00000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] MPTABLE: Product ID: PROD00000000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Processors: 1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Allocating PCI resources starting at 1f800000 (gap: 1f800000:df400000)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127887
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=356f5461-cdd3-4112-823c-02d896965bf4 ro quiet splash
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Initializing CPU#0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] allocated 2579840 bytes of page_cgroup
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Memory: 493040k/516032k available (4565k kernel code, 22364k reserved, 2143k data, 540k init, 0k highmem)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] virtual kernel memory layout:
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     vmalloc : 0xdfff0000 - 0xff7fe000   ( 504 MB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Nov 25 20:07:18 pebbles-desktop kernel: [    0.000000] Detected 2800.264 MHz processor.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.001380] Console: colour VGA+ 80x25
Nov 25 20:07:18 pebbles-desktop kernel: [    0.001386] console [tty0] enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.52 BogoMIPS (lpj=11201056)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004036] Security Framework initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004062] AppArmor: AppArmor initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004073] Mount-cache hash table entries: 512
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004235] Initializing cgroup subsys ns
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004243] Initializing cgroup subsys cpuacct
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004249] Initializing cgroup subsys memory
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004261] Initializing cgroup subsys freezer
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004265] Initializing cgroup subsys net_cls
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004288] CPU: Trace cache: 12K uops, L1 D cache: 8K
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004293] CPU: L2 cache: 512K
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004297] CPU: Hyper-Threading is disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004304] mce: CPU supports 4 MCE banks
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004317] CPU0: Thermal monitoring enabled (TM1)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004330] Performance Counters: no PMU driver, software counters only.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.004338] Checking 'hlt' instruction... OK.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.020922] SMP alternatives: switching to UP code
Nov 25 20:07:18 pebbles-desktop kernel: [    0.030919] Freeing SMP alternatives: 19k freed
Nov 25 20:07:18 pebbles-desktop kernel: [    0.031140] ExtINT not setup in hardware but reported by MP table
Nov 25 20:07:18 pebbles-desktop kernel: [    0.031429] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.071126] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
Nov 25 20:07:18 pebbles-desktop kernel: [    0.176293] Brought up 1 CPUs
Nov 25 20:07:18 pebbles-desktop kernel: [    0.176298] Total of 1 processors activated (5600.52 BogoMIPS).
Nov 25 20:07:18 pebbles-desktop kernel: [    0.176699] Booting paravirtualized kernel on bare hardware
Nov 25 20:07:18 pebbles-desktop kernel: [    0.176957] regulator: core version 0.5
Nov 25 20:07:18 pebbles-desktop kernel: [    0.176983] Time:  4:07:05  Date: 11/26/09
Nov 25 20:07:18 pebbles-desktop kernel: [    0.177050] NET: Registered protocol family 16
Nov 25 20:07:18 pebbles-desktop kernel: [    0.177240] EISA bus registered
Nov 25 20:07:18 pebbles-desktop kernel: [    0.205406] PCI: PCI BIOS revision 2.10 entry at 0xfb9b0, last bus=1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.205409] PCI: Using configuration type 1 for base access
Nov 25 20:07:18 pebbles-desktop kernel: [    0.206804] bio: create slab <bio-0> at 0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.206887] ACPI: Interpreter disabled.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207065] SCSI subsystem initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207209] usbcore: registered new interface driver usbfs
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207231] usbcore: registered new interface driver hub
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207263] usbcore: registered new device driver usb
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207402] PCI: Probing PCI hardware
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207933] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Nov 25 20:07:18 pebbles-desktop kernel: [    0.207940] pci 0000:00:1d.7: PME# disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208013] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208015] * this clock source is slow. If you are sure your timer does not have
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208016] * this bug, please use "acpi_pm_good" to disable the workaround
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208064] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208069] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208317] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208322] pci 0000:00:1f.5: PME# disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208445] pci 0000:01:0b.0: PME# supported from D2 D3hot D3cold
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208451] pci 0000:01:0b.0: PME# disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208550] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208555] pci 0000:01:0c.0: PME# disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208652] pci 0000:01:0d.0: PME# supported from D2 D3hot D3cold
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208657] pci 0000:01:0d.0: PME# disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.208688] pci 0000:00:1e.0: transparent bridge
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209123] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:24c0]
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209294] Bluetooth: Core ver 2.15
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209351] NET: Registered protocol family 31
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209354] Bluetooth: HCI device and connection manager initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209359] Bluetooth: HCI socket layer initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209362] NetLabel: Initializing
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209365] NetLabel:  domain hash size = 128
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209368] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 25 20:07:18 pebbles-desktop kernel: [    0.209386] NetLabel:  unlabeled traffic allowed by default
Nov 25 20:07:18 pebbles-desktop kernel: [    0.211669] pnp: PnP ACPI: disabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.211684] PnPBIOS: Scanning system for PnP BIOS support...
Nov 25 20:07:18 pebbles-desktop kernel: [    0.211767] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc3b0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.211771] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc3e0, dseg 0xf0000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212415] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212435] system 00:08: iomem range 0x0-0x9ffff could not be reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212441] system 00:08: iomem range 0xffb00000-0xffb7ffff has been reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212445] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212450] system 00:08: iomem range 0xfec00000-0xfec0ffff could not be reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212455] system 00:08: iomem range 0xfee00000-0xfee0ffff has been reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212460] system 00:08: iomem range 0x100000-0xffffff could not be reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212468] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212473] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212477] system 00:09: iomem range 0xf8000-0xfffff could not be reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212482] system 00:09: iomem range 0xcb200-0xcbfff has been reserved
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212705] AppArmor: AppArmor Filesystem Enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212738] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212744] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212751] pci 0000:00:1e.0:   MEM window: 0xec000000-0xedffffff
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212758] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x200fffff
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212856] NET: Registered protocol family 2
Nov 25 20:07:18 pebbles-desktop kernel: [    0.212990] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.213338] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.213489] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.213624] TCP: Hash tables configured (established 16384 bind 16384)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.213628] TCP reno registered
Nov 25 20:07:18 pebbles-desktop kernel: [    0.213723] NET: Registered protocol family 1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.213819] Trying to unpack rootfs image as initramfs...
Nov 25 20:07:18 pebbles-desktop kernel: [    0.456275] Freeing initrd memory: 7466k freed
Nov 25 20:07:18 pebbles-desktop kernel: [    0.470121] cpufreq-nforce2: No nForce2 chipset.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.470166] Scanning for low memory corruption every 60 seconds
Nov 25 20:07:18 pebbles-desktop kernel: [    0.470370] audit: initializing netlink socket (disabled)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.470405] type=2000 audit(1259208425.467:1): initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.478940] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov 25 20:07:18 pebbles-desktop kernel: [    0.480543] VFS: Disk quotas dquot_6.5.2
Nov 25 20:07:18 pebbles-desktop kernel: [    0.480611] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481297] fuse init (API version 7.12)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481393] msgmni has been set to 977
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481673] alg: No test for stdrng (krng)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481692] io scheduler noop registered
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481695] io scheduler anticipatory registered
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481698] io scheduler deadline registered
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481759] io scheduler cfq registered (default)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.481987] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 25 20:07:18 pebbles-desktop kernel: [    0.482019] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 25 20:07:18 pebbles-desktop kernel: [    0.482180] isapnp: Scanning for PnP cards...
Nov 25 20:07:18 pebbles-desktop kernel: [    0.836109] isapnp: No Plug & Play device found
Nov 25 20:07:18 pebbles-desktop kernel: [    0.837583] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    0.837704] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 25 20:07:18 pebbles-desktop kernel: [    0.838142] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 25 20:07:18 pebbles-desktop kernel: [    0.839336] brd: module loaded
Nov 25 20:07:18 pebbles-desktop kernel: [    0.839879] loop: module loaded
Nov 25 20:07:18 pebbles-desktop kernel: [    0.840048] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.840231] ata_piix 0000:00:1f.1: PCI->APIC IRQ transform: INT A -> IRQ 16
Nov 25 20:07:18 pebbles-desktop kernel: [    0.840447] scsi0 : ata_piix
Nov 25 20:07:18 pebbles-desktop kernel: [    0.840578] scsi1 : ata_piix
Nov 25 20:07:18 pebbles-desktop kernel: [    0.840624] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Nov 25 20:07:18 pebbles-desktop kernel: [    0.840628] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Nov 25 20:07:18 pebbles-desktop kernel: [    0.841673] Fixed MDIO Bus: probed
Nov 25 20:07:18 pebbles-desktop kernel: [    0.841722] PPP generic driver version 2.4.2
Nov 25 20:07:18 pebbles-desktop kernel: [    0.841858] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 25 20:07:18 pebbles-desktop kernel: [    0.841892] ehci_hcd 0000:00:1d.7: PCI->APIC IRQ transform: INT D -> IRQ 23
Nov 25 20:07:18 pebbles-desktop kernel: [    0.841920] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 25 20:07:18 pebbles-desktop kernel: [    0.841997] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.846231] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee080000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.859962] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860085] usb usb1: configuration #1 chosen from 1 choice
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860125] hub 1-0:1.0: USB hub found
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860139] hub 1-0:1.0: 6 ports detected
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860228] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860255] uhci_hcd: USB Universal Host Controller Interface driver
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860315] uhci_hcd 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 16
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860332] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860382] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860419] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860517] usb usb2: configuration #1 chosen from 1 choice
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860551] hub 2-0:1.0: USB hub found
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860561] hub 2-0:1.0: 2 ports detected
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860629] uhci_hcd 0000:00:1d.1: PCI->APIC IRQ transform: INT B -> IRQ 19
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860642] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860689] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860721] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860825] usb usb3: configuration #1 chosen from 1 choice
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860858] hub 3-0:1.0: USB hub found
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860877] hub 3-0:1.0: 2 ports detected
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860937] uhci_hcd 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860950] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 25 20:07:18 pebbles-desktop kernel: [    0.860991] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Nov 25 20:07:18 pebbles-desktop kernel: [    0.861023] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Nov 25 20:07:18 pebbles-desktop kernel: [    0.861116] usb usb4: configuration #1 chosen from 1 choice
Nov 25 20:07:18 pebbles-desktop kernel: [    0.861150] hub 4-0:1.0: USB hub found
Nov 25 20:07:18 pebbles-desktop kernel: [    0.861160] hub 4-0:1.0: 2 ports detected
Nov 25 20:07:18 pebbles-desktop kernel: [    0.861299] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
Nov 25 20:07:18 pebbles-desktop kernel: [    0.863546] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.863555] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 25 20:07:18 pebbles-desktop kernel: [    0.863631] mice: PS/2 mouse device common for all mice
Nov 25 20:07:18 pebbles-desktop kernel: [    0.863735] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.863759] rtc0: alarms up to one day, 114 bytes nvram
Nov 25 20:07:18 pebbles-desktop kernel: [    0.863906] device-mapper: uevent: version 1.0.3
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864055] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864156] device-mapper: multipath: version 1.1.0 loaded
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864160] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864322] EISA: Probing bus 0 at eisa.0
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864360] EISA: Detected 0 cards.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864421] cpuidle: using governor ladder
Nov 25 20:07:18 pebbles-desktop kernel: [    0.864424] cpuidle: using governor menu
Nov 25 20:07:18 pebbles-desktop kernel: [    0.865015] TCP cubic registered
Nov 25 20:07:18 pebbles-desktop kernel: [    0.865162] NET: Registered protocol family 10
Nov 25 20:07:18 pebbles-desktop kernel: [    0.865654] lo: Disabled Privacy Extensions
Nov 25 20:07:18 pebbles-desktop kernel: [    0.865987] NET: Registered protocol family 17
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866015] Bluetooth: L2CAP ver 2.13
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866017] Bluetooth: L2CAP socket layer initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866022] Bluetooth: SCO (Voice Link) ver 0.6
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866025] Bluetooth: SCO socket layer initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866090] Bluetooth: RFCOMM TTY layer initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866095] Bluetooth: RFCOMM socket layer initialized
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866097] Bluetooth: RFCOMM ver 1.11
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866127] Using IPI No-Shortcut mode
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866245] registered taskstats version 1
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866397]   Magic number: 1:471:111
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866481] rtc_cmos 00:03: setting system clock to 2009-11-26 04:07:06 UTC (1259208426)
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866485] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 25 20:07:18 pebbles-desktop kernel: [    0.866488] EDD information not available.
Nov 25 20:07:18 pebbles-desktop kernel: [    0.892608] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 25 20:07:18 pebbles-desktop kernel: [    1.016241] ata2.00: ATAPI: LITE-ON DVD+RW SOHW-822S, VPPA, max UDMA/33
Nov 25 20:07:18 pebbles-desktop kernel: [    1.016285] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148A, B402, max UDMA/33
Nov 25 20:07:18 pebbles-desktop kernel: [    1.032137] ata2.00: configured for UDMA/33
Nov 25 20:07:18 pebbles-desktop kernel: [    1.048136] ata2.01: configured for UDMA/33
Nov 25 20:07:18 pebbles-desktop kernel: [    1.064247] ata1.00: ATA-6: ST3160021A, 8.01, max UDMA/100
Nov 25 20:07:18 pebbles-desktop kernel: [    1.064251] ata1.00: 312581808 sectors, multi 16: LBA48 
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080132] ata1.00: configured for UDMA/100
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080297] scsi 0:0:0:0: Direct-Access     ATA      ST3160021A       8.01 PQ: 0 ANSI: 5
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080470] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080519] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080577] sd 0:0:0:0: [sda] Write Protect is off
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080611] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 20:07:18 pebbles-desktop kernel: [    1.080778]  sda:
Nov 25 20:07:18 pebbles-desktop kernel: [    1.081723] scsi 1:0:0:0: CD-ROM            LITE-ON  DVD+RW SOHW-822S VPPA PQ: 0 ANSI: 5
Nov 25 20:07:18 pebbles-desktop kernel: [    1.085628] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Nov 25 20:07:18 pebbles-desktop kernel: [    1.085634] Uniform CD-ROM driver Revision: 3.20
Nov 25 20:07:18 pebbles-desktop kernel: [    1.085824] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 25 20:07:18 pebbles-desktop kernel: [    1.086249] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B402 PQ: 0 ANSI: 5
Nov 25 20:07:18 pebbles-desktop kernel: [    1.089367] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
Nov 25 20:07:18 pebbles-desktop kernel: [    1.089517] sr 1:0:1:0: Attached scsi generic sg2 type 5
Nov 25 20:07:18 pebbles-desktop kernel: [    1.092497]  sda1 sda2 sda3
Nov 25 20:07:18 pebbles-desktop kernel: [    1.102156] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 25 20:07:18 pebbles-desktop kernel: [    1.102180] Freeing unused kernel memory: 540k freed
Nov 25 20:07:18 pebbles-desktop kernel: [    1.103048] Write protecting the kernel text: 4568k
Nov 25 20:07:18 pebbles-desktop kernel: [    1.103078] Write protecting the kernel read-only data: 1836k
Nov 25 20:07:18 pebbles-desktop kernel: [    1.250596] Linux agpgart interface v0.103
Nov 25 20:07:18 pebbles-desktop kernel: [    1.269204] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Nov 25 20:07:18 pebbles-desktop kernel: [    1.269361] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
Nov 25 20:07:18 pebbles-desktop kernel: [    1.271696] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
Nov 25 20:07:18 pebbles-desktop kernel: [    1.336150] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov 25 20:07:18 pebbles-desktop kernel: [    1.336207] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Nov 25 20:07:18 pebbles-desktop kernel: [    1.340247] 8139too Fast Ethernet driver 0.9.28
Nov 25 20:07:18 pebbles-desktop kernel: [    1.340308] 8139too 0000:01:0c.0: PCI->APIC IRQ transform: INT A -> IRQ 23
Nov 25 20:07:18 pebbles-desktop kernel: [    1.341412] eth0: RealTek RTL8139 at 0xc800, 00:11:09:a1:81:f3, IRQ 23
Nov 25 20:07:18 pebbles-desktop kernel: [    1.481379] ohci1394 0000:01:0d.0: PCI->APIC IRQ transform: INT A -> IRQ 23
Nov 25 20:07:18 pebbles-desktop kernel: [    1.541945] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[ed002000-ed0027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 25 20:07:18 pebbles-desktop kernel: [    1.603946] usb 2-2: new full speed USB device using uhci_hcd and address 2
Nov 25 20:07:18 pebbles-desktop kernel: [    1.800061] usb 2-2: configuration #1 chosen from 1 choice
Nov 25 20:07:18 pebbles-desktop kernel: [    2.071898] usb 4-1: new full speed USB device using uhci_hcd and address 2
Nov 25 20:07:18 pebbles-desktop kernel: [    2.257854] usb 4-1: configuration #1 chosen from 1 choice
Nov 25 20:07:18 pebbles-desktop kernel: [    2.268931] Initializing USB Mass Storage driver...
Nov 25 20:07:18 pebbles-desktop kernel: [    2.269089] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 25 20:07:18 pebbles-desktop kernel: [    2.269197] usbcore: registered new interface driver usb-storage
Nov 25 20:07:18 pebbles-desktop kernel: [    2.269202] USB Mass Storage support registered.
Nov 25 20:07:18 pebbles-desktop kernel: [    2.791217] PM: Starting manual resume from disk
Nov 25 20:07:18 pebbles-desktop kernel: [    2.795521] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Nov 25 20:07:18 pebbles-desktop kernel: [    2.795528] EXT4-fs (sda1): write access will be enabled during recovery
Nov 25 20:07:18 pebbles-desktop kernel: [    2.807294] EXT4-fs (sda1): barriers enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    3.303806] kjournald2 starting: pid 322, dev sda1:8, commit interval 5 seconds
Nov 25 20:07:18 pebbles-desktop kernel: [    3.303847] EXT4-fs (sda1): delayed allocation enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    3.303852] EXT4-fs: file extents enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    3.304962] EXT4-fs: mballoc enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    3.304981] EXT4-fs (sda1): recovery complete
Nov 25 20:07:18 pebbles-desktop kernel: [    3.314084] EXT4-fs (sda1): mounted filesystem with ordered data mode
Nov 25 20:07:18 pebbles-desktop kernel: [    3.829960] type=1505 audit(1259208429.461:2): operation="profile_load" pid=345 name=/usr/share/gdm/guest-session/Xsession
Nov 25 20:07:18 pebbles-desktop kernel: [    3.833542] type=1505 audit(1259208429.465:3): operation="profile_load" pid=346 name=/sbin/dhclient3
Nov 25 20:07:18 pebbles-desktop kernel: [    3.834138] type=1505 audit(1259208429.465:4): operation="profile_load" pid=346 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 25 20:07:18 pebbles-desktop kernel: [    3.834460] type=1505 audit(1259208429.465:5): operation="profile_load" pid=346 name=/usr/lib/connman/scripts/dhclient-script
Nov 25 20:07:18 pebbles-desktop kernel: [    3.861290] type=1505 audit(1259208429.493:6): operation="profile_load" pid=347 name=/usr/bin/evince
Nov 25 20:07:18 pebbles-desktop kernel: [    3.871319] type=1505 audit(1259208429.501:7): operation="profile_load" pid=347 name=/usr/bin/evince-previewer
Nov 25 20:07:18 pebbles-desktop kernel: [    3.877193] type=1505 audit(1259208429.509:8): operation="profile_load" pid=347 name=/usr/bin/evince-thumbnailer
Nov 25 20:07:18 pebbles-desktop kernel: [    3.894724] type=1505 audit(1259208429.525:9): operation="profile_load" pid=349 name=/usr/lib/cups/backend/cups-pdf
Nov 25 20:07:18 pebbles-desktop kernel: [    3.895422] type=1505 audit(1259208429.525:10): operation="profile_load" pid=349 name=/usr/sbin/cupsd
Nov 25 20:07:18 pebbles-desktop kernel: [    4.926844] Adding 997912k swap on /dev/sda2.  Priority:-1 extents:1 across:997912k 
Nov 25 20:07:18 pebbles-desktop kernel: [    5.006136] udev: starting version 147
Nov 25 20:07:18 pebbles-desktop kernel: [    5.937815] lp: driver loaded but no devices found
Nov 25 20:07:18 pebbles-desktop kernel: [    6.335176] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 25 20:07:18 pebbles-desktop kernel: [    6.541594] intel_rng: FWH not detected
Nov 25 20:07:18 pebbles-desktop kernel: [    6.874605] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 25 20:07:18 pebbles-desktop kernel: [    6.955918] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input2
Nov 25 20:07:18 pebbles-desktop kernel: [    7.129476] EXT4-fs (sda1): internal journal on sda1:8
Nov 25 20:07:18 pebbles-desktop kernel: [    7.235938] Intel ICH 0000:00:1f.5: PCI->APIC IRQ transform: INT B -> IRQ 17
Nov 25 20:07:18 pebbles-desktop kernel: [    7.272488] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.275484] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.278483] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.281481] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.282007] sd 2:0:0:0: Attached scsi generic sg3 type 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.282128] sd 2:0:0:1: Attached scsi generic sg4 type 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.282245] sd 2:0:0:2: Attached scsi generic sg5 type 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.282359] sd 2:0:0:3: Attached scsi generic sg6 type 0
Nov 25 20:07:18 pebbles-desktop kernel: [    7.526440] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Nov 25 20:07:18 pebbles-desktop kernel: [    7.531415] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Nov 25 20:07:18 pebbles-desktop kernel: [    7.536418] sd 2:0:0:2: [sdd] Attached SCSI removable disk
Nov 25 20:07:18 pebbles-desktop kernel: [    7.541429] sd 2:0:0:3: [sde] Attached SCSI removable disk
Nov 25 20:07:18 pebbles-desktop kernel: [    7.563605] intel8x0_measure_ac97_clock: measured 53077 usecs (2558 samples)
Nov 25 20:07:18 pebbles-desktop kernel: [    7.563610] intel8x0: clocking to 48000
Nov 25 20:07:18 pebbles-desktop kernel: [    7.690336] EXT4-fs (sda3): barriers enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    7.692112] kjournald2 starting: pid 666, dev sda3:8, commit interval 5 seconds
Nov 25 20:07:18 pebbles-desktop kernel: [    7.692482] EXT4-fs (sda3): internal journal on sda3:8
Nov 25 20:07:18 pebbles-desktop kernel: [    7.692488] EXT4-fs (sda3): delayed allocation enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    7.692492] EXT4-fs: file extents enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    7.712967] EXT4-fs: mballoc enabled
Nov 25 20:07:18 pebbles-desktop kernel: [    7.712993] EXT4-fs (sda3): mounted filesystem with ordered data mode
Nov 25 20:07:18 pebbles-desktop kernel: [    8.582692] __ratelimit: 3 callbacks suppressed
Nov 25 20:07:18 pebbles-desktop kernel: [    8.582697] type=1505 audit(1259208434.213:12): operation="profile_replace" pid=725 name=/usr/share/gdm/guest-session/Xsession
Nov 25 20:07:18 pebbles-desktop kernel: [    8.585428] type=1505 audit(1259208434.217:13): operation="profile_replace" pid=726 name=/sbin/dhclient3
Nov 25 20:07:18 pebbles-desktop kernel: [    8.586027] type=1505 audit(1259208434.217:14): operation="profile_replace" pid=726 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 25 20:07:18 pebbles-desktop kernel: [    8.586351] type=1505 audit(1259208434.217:15): operation="profile_replace" pid=726 name=/usr/lib/connman/scripts/dhclient-script
Nov 25 20:07:18 pebbles-desktop kernel: [    8.594474] type=1505 audit(1259208434.225:16): operation="profile_replace" pid=727 name=/usr/bin/evince
Nov 25 20:07:18 pebbles-desktop kernel: [    8.604866] type=1505 audit(1259208434.237:17): operation="profile_replace" pid=727 name=/usr/bin/evince-previewer
Nov 25 20:07:18 pebbles-desktop kernel: [    8.610897] type=1505 audit(1259208434.241:18): operation="profile_replace" pid=727 name=/usr/bin/evince-thumbnailer
Nov 25 20:07:18 pebbles-desktop kernel: [    8.620871] type=1505 audit(1259208434.253:19): operation="profile_replace" pid=729 name=/usr/lib/cups/backend/cups-pdf
Nov 25 20:07:18 pebbles-desktop kernel: [    8.621575] type=1505 audit(1259208434.253:20): operation="profile_replace" pid=729 name=/usr/sbin/cupsd
Nov 25 20:07:18 pebbles-desktop kernel: [    8.625946] type=1505 audit(1259208434.257:21): operation="profile_replace" pid=730 name=/usr/sbin/tcpdump
Nov 25 20:07:18 pebbles-desktop kernel: [   10.416218] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7404
Nov 25 20:07:18 pebbles-desktop kernel: [   10.416251] usbcore: registered new interface driver usblp
Nov 25 20:07:18 pebbles-desktop kernel: [   11.645715] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov 25 20:07:18 pebbles-desktop kernel: [   11.705230] ppdev: user-space parallel port driver
Nov 25 20:07:20 pebbles-desktop kernel: [   14.584175] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Nov 25 20:07:29 pebbles-desktop pulseaudio[1410]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Nov 25 20:07:29 pebbles-desktop pulseaudio[1410]: alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
```

Hope somebody can make sense of that. Thanks for the help.

---

