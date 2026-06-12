---
title: "Ubuntu random shutdown"
date: 2009-09-10
forum: General Help
---

### Post by HankTorrents on 2009-09-10
I am running on a dell 9300 inspiron. How can I gather the necessary information to tell why it shuts down in random intervals. I was playing a game one and it shut down, I have been on the internet a few times and it has shut down. I only installed ubunutu on this laptop a few days ago with all the updates. any help would be greatly appreciated. Oh to add I am running 8.04 hardy

---

### Post by earthpigg on 2009-09-10
system -> administration -> system log viewier.

whenever something funky happens to your Linux system, write down the time so you can find it later in the system logs.

if you think you see relevant stuff, please post here in ```
code tags

``` and not > quotes
 so we can read it easily.

---

### Post by HankTorrents on 2009-09-10
Ok, next time it shuts down I'll be sure to do that

to test

```
code
```

---

### Post by HankTorrents on 2009-09-10
ok so it jus turned off here is the info



```
Sep 10 19:12:57 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Sep 10 19:28:44 broozer -- MARK --
Sep 10 19:48:44 broozer -- MARK --
Sep 10 19:59:13 broozer kernel: [  818.058725] ACPI: Critical trip point
Sep 10 19:59:16 broozer exiting on signal 15
Sep 10 20:00:09 broozer syslogd 1.5.0#1ubuntu1: restart.
Sep 10 20:00:09 broozer kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep 10 20:00:09 broozer kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep 10 20:00:09 broozer kernel: Symbols match kernel version 2.6.24.
Sep 10 20:00:09 broozer kernel: Loaded 17649 symbols from 91 modules.
Sep 10 20:00:09 broozer kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 10 20:00:09 broozer kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 10 20:00:09 broozer kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep 10 20:00:09 broozer kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffda000 (usable)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 000000007ffda000 - 0000000080000000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep 10 20:00:09 broozer kernel: [    0.000000] 1151MB HIGHMEM available.
Sep 10 20:00:09 broozer kernel: [    0.000000] 896MB LOWMEM available.
Sep 10 20:00:09 broozer kernel: [    0.000000] Zone PFN ranges:
Sep 10 20:00:09 broozer kernel: [    0.000000]   DMA             0 ->     4096
Sep 10 20:00:09 broozer kernel: [    0.000000]   Normal       4096 ->   229376
Sep 10 20:00:09 broozer kernel: [    0.000000]   HighMem    229376 ->   524250
Sep 10 20:00:09 broozer kernel: [    0.000000] Movable zone start PFN for each node
Sep 10 20:00:09 broozer kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 10 20:00:09 broozer kernel: [    0.000000]     0:        0 ->   524250
Sep 10 20:00:09 broozer kernel: [    0.000000] DMI 2.3 present.
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: RSDT 7FFDA7D3, 0040 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: FACP 7FFDB400, 0074 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: DSDT 7FFDC000, 25EB (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: FACS 7FFEA800, 0040
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: APIC 7FFDBC00, 0068 (r1 DELL    CPi R   27D5031D ASL        47)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: MCFG 7FFDBBC0, 003E (r16 DELL    CPi R   27D5031D ASL        61)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: BOOT 7FFDB7C0, 0028 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: SSDT 7FFDABE6, 0280 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: SSDT 7FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: SSDT 7FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 10 20:00:09 broozer kernel: [    0.000000] Processor #0 6:13 APIC version 20
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep 10 20:00:09 broozer kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 10 20:00:09 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 10 20:00:09 broozer kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 10 20:00:09 broozer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 10 20:00:09 broozer kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep 10 20:00:09 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep 10 20:00:09 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep 10 20:00:09 broozer kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520155
Sep 10 20:00:09 broozer kernel: [    0.000000] Kernel command line: root=UUID=983074b0-55d2-4305-aecb-3cfb9caafeb4 ro quiet splash
Sep 10 20:00:09 broozer kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 10 20:00:09 broozer kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 10 20:00:09 broozer kernel: [    0.000000] Initializing CPU#0
Sep 10 20:00:09 broozer kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 10 20:00:09 broozer kernel: [    0.000000] Detected 1995.068 MHz processor.
Sep 10 20:00:09 broozer kernel: [    6.429218] Console: colour VGA+ 80x25
Sep 10 20:00:09 broozer kernel: [    6.429222] console [tty0] enabled
Sep 10 20:00:09 broozer kernel: [    6.429535] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 10 20:00:09 broozer kernel: [    6.429912] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 10 20:00:09 broozer kernel: [    6.524790] Memory: 2067184k/2097000k available (2181k kernel code, 28672k reserved, 1006k data, 368k init, 1179496k highmem)
Sep 10 20:00:09 broozer kernel: [    6.524798] virtual kernel memory layout:
Sep 10 20:00:09 broozer kernel: [    6.524799]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 10 20:00:09 broozer kernel: [    6.524800]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 10 20:00:09 broozer kernel: [    6.524801]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep 10 20:00:09 broozer kernel: [    6.524802]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep 10 20:00:09 broozer kernel: [    6.524803]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep 10 20:00:09 broozer kernel: [    6.524805]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep 10 20:00:09 broozer kernel: [    6.524806]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep 10 20:00:09 broozer kernel: [    6.524809] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 10 20:00:09 broozer kernel: [    6.524857] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 10 20:00:09 broozer kernel: [    6.601934] Calibrating delay using timer specific routine.. 3800.30 BogoMIPS (lpj=7600614)
Sep 10 20:00:09 broozer kernel: [    6.601969] Security Framework initialized
Sep 10 20:00:09 broozer kernel: [    6.601978] SELinux:  Disabled at boot.
Sep 10 20:00:09 broozer kernel: [    6.601997] AppArmor: AppArmor initialized
Sep 10 20:00:09 broozer kernel: [    6.602001] Failure registering capabilities with primary security module.
Sep 10 20:00:09 broozer kernel: [    6.602012] Mount-cache hash table entries: 512
Sep 10 20:00:09 broozer kernel: [    6.602166] Initializing cgroup subsys ns
Sep 10 20:00:09 broozer kernel: [    6.602174] Initializing cgroup subsys cpuacct
Sep 10 20:00:09 broozer kernel: [    6.602198] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 10 20:00:09 broozer kernel: [    6.602200] CPU: L2 cache: 2048K
Sep 10 20:00:09 broozer kernel: [    6.602213] Compat vDSO mapped to ffffe000.
Sep 10 20:00:09 broozer kernel: [    6.602229] Checking 'hlt' instruction... OK.
Sep 10 20:00:09 broozer kernel: [    6.614411] SMP alternatives: switching to UP code
Sep 10 20:00:09 broozer kernel: [    6.616206] Freeing SMP alternatives: 11k freed
Sep 10 20:00:09 broozer kernel: [    6.616322] Early unpacking initramfs... done
Sep 10 20:00:09 broozer kernel: [    6.955772] ACPI: Core revision 20070126
Sep 10 20:00:09 broozer kernel: [    6.955821] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 10 20:00:09 broozer kernel: [    6.958314] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Sep 10 20:00:09 broozer kernel: [    6.958332] Total of 1 processors activated (3800.30 BogoMIPS).
Sep 10 20:00:09 broozer kernel: [    6.958533] ENABLING IO-APIC IRQs
Sep 10 20:00:09 broozer kernel: [    6.958720] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 10 20:00:09 broozer kernel: [    7.076765] Brought up 1 CPUs
Sep 10 20:00:09 broozer kernel: [    7.076951] net_namespace: 64 bytes
Sep 10 20:00:09 broozer kernel: [    7.076961] Booting paravirtualized kernel on bare hardware
Sep 10 20:00:09 broozer kernel: [    7.077398] Time:  2:59:41  Date: 09/11/09
Sep 10 20:00:09 broozer kernel: [    7.077422] NET: Registered protocol family 16
Sep 10 20:00:09 broozer kernel: [    7.077601] EISA bus registered
Sep 10 20:00:09 broozer kernel: [    7.077627] ACPI: bus type pci registered
Sep 10 20:00:09 broozer kernel: [    7.118441] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
Sep 10 20:00:09 broozer kernel: [    7.118443] PCI: Using configuration type 1
Sep 10 20:00:09 broozer kernel: [    7.118457] Setting up standard PCI resources
Sep 10 20:00:09 broozer kernel: [    7.126049] ACPI: Interpreter enabled
Sep 10 20:00:09 broozer kernel: [    7.126054] ACPI: (supports S0 S3 S4 S5)
Sep 10 20:00:09 broozer kernel: [    7.126064] ACPI: Using IOAPIC for interrupt routing
Sep 10 20:00:09 broozer kernel: [    7.136252] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 10 20:00:09 broozer kernel: [    7.136926] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep 10 20:00:09 broozer kernel: [    7.136930] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep 10 20:00:09 broozer kernel: [    7.137633] PCI: Transparent bridge - 0000:00:1e.0
Sep 10 20:00:09 broozer kernel: [    7.143248] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Sep 10 20:00:09 broozer kernel: [    7.143339] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Sep 10 20:00:09 broozer kernel: [    7.143427] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep 10 20:00:09 broozer kernel: [    7.143513] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
Sep 10 20:00:09 broozer kernel: [    7.143591] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 20:00:09 broozer kernel: [    7.143669] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 20:00:09 broozer kernel: [    7.143747] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 20:00:09 broozer kernel: [    7.143854] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 10 20:00:09 broozer kernel: [    7.143881] pnp: PnP ACPI init
Sep 10 20:00:09 broozer kernel: [    7.143887] ACPI: bus type pnp registered
Sep 10 20:00:09 broozer kernel: [    7.155335] pnpacpi: exceeded the max number of mem resources: 12
Sep 10 20:00:09 broozer kernel: [    7.165294] pnp: PnP ACPI: found 11 devices
Sep 10 20:00:09 broozer kernel: [    7.165296] ACPI: ACPI bus type pnp unregistered
Sep 10 20:00:09 broozer kernel: [    7.165299] PnPBIOS: Disabled by ACPI PNP
Sep 10 20:00:09 broozer kernel: [    7.165489] PCI: Using ACPI for IRQ routing
Sep 10 20:00:09 broozer kernel: [    7.165491] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 10 20:00:09 broozer kernel: [    7.191448] NET: Registered protocol family 8
Sep 10 20:00:09 broozer kernel: [    7.191450] NET: Registered protocol family 20
Sep 10 20:00:09 broozer kernel: [    7.191596] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 10 20:00:09 broozer kernel: [    7.191600] hpet0: 3 64-bit timers, 14318180 Hz
Sep 10 20:00:09 broozer kernel: [    7.192396] AppArmor: AppArmor Filesystem Enabled
Sep 10 20:00:09 broozer kernel: [    7.194461] Time: tsc clocksource has been installed.
Sep 10 20:00:09 broozer kernel: [    7.200531] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200534] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200536] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200539] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200541] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200544] system 00:00: iomem range 0x7ffda000-0x7fffffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200549] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200552] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200554] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200557] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200560] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200562] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200568] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200572] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200575] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200579] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200582] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200584] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep 10 20:00:09 broozer kernel: [    7.200587] system 00:03: ioport range 0x1060-0x107f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200589] system 00:03: ioport range 0x1080-0x10bf has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200592] system 00:03: ioport range 0x10c0-0x10df has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200596] system 00:03: ioport range 0x10e0-0x10ff has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200602] system 00:08: ioport range 0x900-0x90f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200605] system 00:08: ioport range 0x910-0x91f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200607] system 00:08: ioport range 0x920-0x92f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200609] system 00:08: ioport range 0x930-0x93f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.200612] system 00:08: ioport range 0x940-0x97f has been reserved
Sep 10 20:00:09 broozer kernel: [    7.223750] PCI: Bridge: 0000:00:01.0
Sep 10 20:00:09 broozer kernel: [    7.223753]   IO window: d000-dfff
Sep 10 20:00:09 broozer kernel: [    7.223756]   MEM window: dfd00000-dfefffff
Sep 10 20:00:09 broozer kernel: [    7.223758]   PREFETCH window: d0000000-d7ffffff
Sep 10 20:00:09 broozer kernel: [    7.223771] PCI: Bus 4, cardbus bridge: 0000:03:01.0
Sep 10 20:00:09 broozer kernel: [    7.223773]   IO window: 00001400-000014ff
Sep 10 20:00:09 broozer kernel: [    7.223777]   IO window: 00001800-000018ff
Sep 10 20:00:09 broozer kernel: [    7.223781]   PREFETCH window: 88000000-8bffffff
Sep 10 20:00:09 broozer kernel: [    7.223785]   MEM window: 8c000000-8fffffff
Sep 10 20:00:09 broozer kernel: [    7.223791] PCI: Bridge: 0000:00:1e.0
Sep 10 20:00:09 broozer kernel: [    7.223792]   IO window: disabled.
Sep 10 20:00:09 broozer kernel: [    7.223797]   MEM window: dfc00000-dfcfffff
Sep 10 20:00:09 broozer kernel: [    7.223801]   PREFETCH window: disabled.
Sep 10 20:00:09 broozer kernel: [    7.223819] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 20:00:09 broozer kernel: [    7.223851] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
Sep 10 20:00:09 broozer kernel: [    7.223854] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Sep 10 20:00:09 broozer kernel: [    7.223869] NET: Registered protocol family 2
Sep 10 20:00:09 broozer kernel: [    7.251875] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 10 20:00:09 broozer kernel: [    7.252090] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 10 20:00:09 broozer kernel: [    7.252838] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 10 20:00:09 broozer kernel: [    7.253297] TCP: Hash tables configured (established 131072 bind 65536)
Sep 10 20:00:09 broozer kernel: [    7.253300] TCP reno registered
Sep 10 20:00:09 broozer kernel: [    7.261036] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Sep 10 20:00:09 broozer kernel: [    7.578541]  it is
Sep 10 20:00:09 broozer kernel: [    7.922505] Freeing initrd memory: 7319k freed
Sep 10 20:00:09 broozer kernel: [    7.922716] Simple Boot Flag at 0x79 set to 0x1
Sep 10 20:00:09 broozer kernel: [    7.923109] audit: initializing netlink socket (disabled)
Sep 10 20:00:09 broozer kernel: [    7.923124] audit(1252637981.488:1): initialized
Sep 10 20:00:09 broozer kernel: [    7.923336] highmem bounce pool size: 64 pages
Sep 10 20:00:09 broozer kernel: [    7.925116] VFS: Disk quotas dquot_6.5.1
Sep 10 20:00:09 broozer kernel: [    7.925188] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 10 20:00:09 broozer kernel: [    7.925324] io scheduler noop registered
Sep 10 20:00:09 broozer kernel: [    7.925326] io scheduler anticipatory registered
Sep 10 20:00:09 broozer kernel: [    7.925328] io scheduler deadline registered
Sep 10 20:00:09 broozer kernel: [    7.925340] io scheduler cfq registered (default)
Sep 10 20:00:09 broozer kernel: [    7.925568] assign_interrupt_mode Found MSI capability
Sep 10 20:00:09 broozer kernel: [    7.925820] isapnp: Scanning for PnP cards...
Sep 10 20:00:09 broozer kernel: [    8.189876] Clocksource tsc unstable (delta = -201410374 ns)
Sep 10 20:00:09 broozer kernel: [    8.193872] Time: hpet clocksource has been installed.
Sep 10 20:00:09 broozer kernel: [    8.264170] isapnp: No Plug & Play device found
Sep 10 20:00:09 broozer kernel: [    8.289586] Real Time Clock Driver v1.12ac
Sep 10 20:00:09 broozer kernel: [    8.289691] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 10 20:00:09 broozer kernel: [    8.290224] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 20:00:09 broozer kernel: [    8.290232] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Sep 10 20:00:09 broozer kernel: [    8.290834] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 10 20:00:09 broozer kernel: [    8.290899] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 10 20:00:09 broozer kernel: [    8.290991] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 10 20:00:09 broozer kernel: [    8.294923] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 10 20:00:09 broozer kernel: [    8.294927] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 10 20:00:09 broozer kernel: [    8.296649] mice: PS/2 mouse device common for all mice
Sep 10 20:00:09 broozer kernel: [    8.296755] EISA: Probing bus 0 at eisa.0
Sep 10 20:00:09 broozer kernel: [    8.296762] Cannot allocate resource for EISA slot 1
Sep 10 20:00:09 broozer kernel: [    8.296790] EISA: Detected 0 cards.
Sep 10 20:00:09 broozer kernel: [    8.296793] cpuidle: using governor ladder
Sep 10 20:00:09 broozer kernel: [    8.296795] cpuidle: using governor menu
Sep 10 20:00:09 broozer kernel: [    8.296883] NET: Registered protocol family 1
Sep 10 20:00:09 broozer kernel: [    8.296909] Using IPI No-Shortcut mode
Sep 10 20:00:09 broozer kernel: [    8.296941] registered taskstats version 1
Sep 10 20:00:09 broozer kernel: [    8.297051]   Magic number: 9:495:965
Sep 10 20:00:09 broozer kernel: [    8.297058]   hash matches device ttyb6
Sep 10 20:00:09 broozer kernel: [    8.297137] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 10 20:00:09 broozer kernel: [    8.297141] EDD information not available.
Sep 10 20:00:09 broozer kernel: [    8.297338] Freeing unused kernel memory: 368k freed
Sep 10 20:00:09 broozer kernel: [    8.297364] Write protecting the kernel read-only data: 802k
Sep 10 20:00:09 broozer kernel: [    8.300681] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 10 20:00:09 broozer kernel: [    9.236896] fuse init (API version 7.9)
Sep 10 20:00:09 broozer kernel: [    9.252638] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Sep 10 20:00:09 broozer kernel: [    9.252644] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep 10 20:00:09 broozer kernel: [    9.252657] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep 10 20:00:09 broozer kernel: [    9.255924] ACPI: Thermal Zone [THM] (93 C)
Sep 10 20:00:09 broozer kernel: [    9.743846] usbcore: registered new interface driver usbfs
Sep 10 20:00:09 broozer kernel: [    9.743870] usbcore: registered new interface driver hub
Sep 10 20:00:09 broozer kernel: [    9.752876] usbcore: registered new device driver usb
Sep 10 20:00:09 broozer kernel: [    9.764935] USB Universal Host Controller Interface driver v3.0
Sep 10 20:00:09 broozer kernel: [    9.764997] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 20:00:09 broozer kernel: [    9.765016] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 10 20:00:09 broozer kernel: [    9.765360] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Sep 10 20:00:09 broozer kernel: [    9.765394] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
Sep 10 20:00:09 broozer kernel: [    9.765526] usb usb1: configuration #1 chosen from 1 choice
Sep 10 20:00:09 broozer kernel: [    9.765550] hub 1-0:1.0: USB hub found
Sep 10 20:00:09 broozer kernel: [    9.765555] hub 1-0:1.0: 2 ports detected
Sep 10 20:00:09 broozer kernel: [    9.843560] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 20:00:09 broozer kernel: [    9.843580] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 10 20:00:09 broozer kernel: [    9.843606] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Sep 10 20:00:09 broozer kernel: [    9.843642] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
Sep 10 20:00:09 broozer kernel: [    9.843750] usb usb2: configuration #1 chosen from 1 choice
Sep 10 20:00:09 broozer kernel: [    9.843771] hub 2-0:1.0: USB hub found
Sep 10 20:00:09 broozer kernel: [    9.843776] hub 2-0:1.0: 2 ports detected
Sep 10 20:00:09 broozer kernel: [    9.899847] SCSI subsystem initialized
Sep 10 20:00:09 broozer kernel: [    9.922180] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Sep 10 20:00:09 broozer kernel: [    9.922199] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 10 20:00:09 broozer kernel: [    9.922222] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Sep 10 20:00:09 broozer kernel: [    9.922254] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
Sep 10 20:00:09 broozer kernel: [    9.922362] usb usb3: configuration #1 chosen from 1 choice
Sep 10 20:00:09 broozer kernel: [    9.922385] hub 3-0:1.0: USB hub found
Sep 10 20:00:09 broozer kernel: [    9.922390] hub 3-0:1.0: 2 ports detected
Sep 10 20:00:09 broozer kernel: [   10.000855] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Sep 10 20:00:09 broozer kernel: [   10.000873] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep 10 20:00:09 broozer kernel: [   10.000896] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Sep 10 20:00:09 broozer kernel: [   10.000931] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
Sep 10 20:00:09 broozer kernel: [   10.001036] usb usb4: configuration #1 chosen from 1 choice
Sep 10 20:00:09 broozer kernel: [   10.001058] hub 4-0:1.0: USB hub found
Sep 10 20:00:09 broozer kernel: [   10.001062] hub 4-0:1.0: 2 ports detected
Sep 10 20:00:09 broozer kernel: [   10.079673] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 20:00:09 broozer kernel: [   10.079691] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 10 20:00:09 broozer kernel: [   10.079715] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Sep 10 20:00:09 broozer kernel: [   10.082693] ehci_hcd 0000:00:1d.7: debug port 1
Sep 10 20:00:09 broozer kernel: [   10.082706] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
Sep 10 20:00:09 broozer kernel: [   10.094600] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 10 20:00:09 broozer kernel: [   10.094698] usb usb5: configuration #1 chosen from 1 choice
Sep 10 20:00:09 broozer kernel: [   10.094720] hub 5-0:1.0: USB hub found
Sep 10 20:00:09 broozer kernel: [   10.094729] hub 5-0:1.0: 8 ports detected
Sep 10 20:00:09 broozer kernel: [   10.174926] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 19
Sep 10 20:00:09 broozer kernel: [   10.225121] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 10 20:00:09 broozer kernel: [   10.239589] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Sep 10 20:00:09 broozer kernel: [   10.252060] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Sep 10 20:00:09 broozer kernel: [   10.252069] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Sep 10 20:00:09 broozer kernel: [   10.252076] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Sep 10 20:00:09 broozer kernel: [   10.282986] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Sep 10 20:00:09 broozer kernel: [   10.283009] b44.c:v2.0
Sep 10 20:00:09 broozer kernel: [   10.283115] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 20:00:09 broozer kernel: [   10.283163] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 10 20:00:09 broozer kernel: [   10.298449] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:e0:6d:16
Sep 10 20:00:09 broozer kernel: [   10.301742] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep 10 20:00:09 broozer kernel: [   10.419203] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 20:00:09 broozer kernel: [   10.425258] scsi0 : ata_piix
Sep 10 20:00:09 broozer kernel: [   10.427505] scsi1 : ata_piix
Sep 10 20:00:09 broozer kernel: [   10.427652] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Sep 10 20:00:09 broozer kernel: [   10.427655] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Sep 10 20:00:09 broozer kernel: [   10.458010] ata1.00: ATA-6: WDC WD400VE-75HDT0, 09.07D09, max UDMA/100
Sep 10 20:00:09 broozer kernel: [   10.458014] ata1.00: 78140160 sectors, multi 8: LBA 
Sep 10 20:00:09 broozer kernel: [   10.458017] ata1.00: applying bridge limits
Sep 10 20:00:09 broozer kernel: [   10.459034] ata1.00: configured for UDMA/100
Sep 10 20:00:09 broozer kernel: [   10.468314] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B101, max UDMA/33
Sep 10 20:00:09 broozer kernel: [   10.473176] ata2.00: configured for UDMA/33
Sep 10 20:00:09 broozer kernel: [   10.473291] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400VE-75HD 09.0 PQ: 0 ANSI: 5
Sep 10 20:00:09 broozer kernel: [   10.473933] scsi 1:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B101 PQ: 0 ANSI: 5
Sep 10 20:00:09 broozer kernel: [   10.485816] Driver 'sd' needs updating - please use bus_type methods
Sep 10 20:00:09 broozer kernel: [   10.485888] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 20:00:09 broozer kernel: [   10.485899] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 20:00:09 broozer kernel: [   10.485918] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 20:00:09 broozer kernel: [   10.485962] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 20:00:09 broozer kernel: [   10.485970] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 20:00:09 broozer kernel: [   10.485987] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 20:00:09 broozer kernel: [   10.485990]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep 10 20:00:09 broozer kernel: [   10.499522]  sda1 sda2 < sda5 >
Sep 10 20:00:09 broozer kernel: [   10.500311] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 10 20:00:09 broozer kernel: [   10.505335] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 10 20:00:09 broozer kernel: [   10.505354] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep 10 20:00:09 broozer kernel: [   10.516914] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep 10 20:00:09 broozer kernel: [   10.516918] Uniform CD-ROM driver Revision: 3.20
Sep 10 20:00:09 broozer kernel: [   10.592686] Attempting manual resume
Sep 10 20:00:09 broozer kernel: [   10.606701] kjournald starting.  Commit interval 5 seconds
Sep 10 20:00:09 broozer kernel: [   10.606711] EXT3-fs: mounted filesystem with ordered data mode.
Sep 10 20:00:09 broozer kernel: [   13.136336] Linux agpgart interface v0.102
Sep 10 20:00:09 broozer kernel: [   13.250654] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 10 20:00:09 broozer kernel: [   13.296927] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 10 20:00:09 broozer kernel: [   13.601985] ACPI: AC Adapter [AC] (on-line)
Sep 10 20:00:09 broozer kernel: [   13.644224] iTCO_vendor_support: vendor-support=0
Sep 10 20:00:09 broozer kernel: [   13.684572] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep 10 20:00:09 broozer kernel: [   13.684656] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
Sep 10 20:00:09 broozer kernel: [   13.684695] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep 10 20:00:09 broozer kernel: [   13.825940] input: Lid Switch as /devices/virtual/input/input2
Sep 10 20:00:09 broozer kernel: [   13.826569] ACPI: Lid Switch [LID]
Sep 10 20:00:09 broozer kernel: [   13.827350] input: Power Button (CM) as /devices/virtual/input/input3
Sep 10 20:00:09 broozer kernel: [   13.834609] ACPI: Power Button (CM) [PBTN]
Sep 10 20:00:09 broozer kernel: [   13.834685] input: Sleep Button (CM) as /devices/virtual/input/input4
Sep 10 20:00:09 broozer kernel: [   13.846683] ACPI: Sleep Button (CM) [SBTN]
Sep 10 20:00:09 broozer kernel: [   14.061748] ACPI: Battery Slot [BAT0] (battery present)
Sep 10 20:00:09 broozer kernel: [   14.141794] input: PC Speaker as /devices/platform/pcspkr/input/input5
Sep 10 20:00:09 broozer kernel: [   14.497395] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
Sep 10 20:00:09 broozer kernel: [   14.530405] input: PS/2 Mouse as /devices/virtual/input/input6
Sep 10 20:00:09 broozer kernel: [   14.552544] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
Sep 10 20:00:09 broozer kernel: [   14.593689] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17
Sep 10 20:00:09 broozer kernel: [   14.593694] Socket status: 30000006
Sep 10 20:00:09 broozer kernel: [   14.593698] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Sep 10 20:00:09 broozer kernel: [   14.593703] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
Sep 10 20:00:09 broozer kernel: [   14.695624] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep 10 20:00:09 broozer kernel: [   14.695627] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep 10 20:00:09 broozer kernel: [   14.746989] sdhci: Secure Digital Host Controller Interface driver
Sep 10 20:00:09 broozer kernel: [   14.746992] sdhci: Copyright(c) Pierre Ossman
Sep 10 20:00:09 broozer kernel: [   14.747036] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
Sep 10 20:00:09 broozer kernel: [   14.747059] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
Sep 10 20:00:09 broozer kernel: [   14.747120] mmc0: SDHCI at 0xdfcfc700 irq 18 DMA
Sep 10 20:00:09 broozer kernel: [   14.810084] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Sep 10 20:00:09 broozer kernel: [   14.810090] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Sep 10 20:00:09 broozer kernel: [   14.810187] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Sep 10 20:00:09 broozer kernel: [   14.855315] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Sep 10 20:00:09 broozer kernel: [   15.759084] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input8
Sep 10 20:00:09 broozer kernel: [   15.767831] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Sep 10 20:00:09 broozer kernel: [   16.212091] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep 10 20:00:09 broozer kernel: [   17.418050] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Sep 10 20:00:09 broozer kernel: [   17.418100] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 20:00:09 broozer kernel: [   17.421441] cs: IO port probe 0x100-0x3af: clean.
Sep 10 20:00:09 broozer kernel: [   17.423265] cs: IO port probe 0x3e0-0x4ff: clean.
Sep 10 20:00:09 broozer kernel: [   17.424043] cs: IO port probe 0x820-0x8ff: clean.
Sep 10 20:00:09 broozer kernel: [   17.424676] cs: IO port probe 0xc00-0xcf7: clean.
Sep 10 20:00:09 broozer kernel: [   17.425463] cs: IO port probe 0xa00-0xaff: clean.
Sep 10 20:00:09 broozer kernel: [   17.467284] intel8x0_measure_ac97_clock: measured 55311 usecs
Sep 10 20:00:09 broozer kernel: [   17.467286] intel8x0: clocking to 48000
Sep 10 20:00:09 broozer kernel: [   17.575080] lp: driver loaded but no devices found
Sep 10 20:00:09 broozer kernel: [   17.740941] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
Sep 10 20:00:09 broozer kernel: [   17.821888] EXT3 FS on sda1, internal journal
Sep 10 20:00:09 broozer kernel: [   18.168072] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 10 20:00:09 broozer kernel: [   18.368367] No dock devices found.
Sep 10 20:00:09 broozer kernel: [   19.044684] apm: BIOS not found.
Sep 10 20:00:10 broozer kernel: [   19.098021] ppdev: user-space parallel port driver
Sep 10 20:00:10 broozer kernel: [   19.113503] audit(1252638010.237:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4898 profile="/usr/sbin/cupsd" namespace="default"
Sep 10 20:00:10 broozer dhcdbd: Started up.
Sep 10 20:00:10 broozer kernel: [   47.994014] Marking TSC unstable due to: cpufreq changes.
Sep 10 20:00:11 broozer kernel: [   49.567142] Bluetooth: Core ver 2.11
Sep 10 20:00:11 broozer kernel: [   49.568034] NET: Registered protocol family 31
Sep 10 20:00:11 broozer kernel: [   49.568043] Bluetooth: HCI device and connection manager initialized
Sep 10 20:00:11 broozer kernel: [   49.568050] Bluetooth: HCI socket layer initialized
Sep 10 20:00:11 broozer kernel: [   19.869470] Bluetooth: L2CAP ver 2.9
Sep 10 20:00:11 broozer kernel: [   19.869475] Bluetooth: L2CAP socket layer initialized
Sep 10 20:00:11 broozer kernel: [   19.899884] Bluetooth: RFCOMM socket layer initialized
Sep 10 20:00:11 broozer kernel: [   19.899901] Bluetooth: RFCOMM TTY layer initialized
Sep 10 20:00:11 broozer kernel: [   19.899903] Bluetooth: RFCOMM ver 1.8
Sep 10 20:00:14 broozer kernel: [   20.238987] [drm] Initialized drm 1.1.0 20060810
Sep 10 20:00:14 broozer kernel: [   20.243289] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 20:00:14 broozer kernel: [   20.243371] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Sep 10 20:00:18 broozer kernel: [   51.162964] [drm] Setting GART location based on new memory map
Sep 10 20:00:18 broozer kernel: [   51.164061] [drm] Loading R300 Microcode
Sep 10 20:00:18 broozer kernel: [   51.164156] [drm] writeback test succeeded in 1 usecs
Sep 10 20:00:41 broozer kernel: [   57.231392] NET: Registered protocol family 10
Sep 10 20:00:41 broozer kernel: [   57.232217] lo: Disabled Privacy Extensions
Sep 10 20:00:41 broozer kernel: [   57.234258] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 10 20:00:52 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep 10 20:00:54 broozer kernel: [   26.992313] NET: Registered protocol family 17
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu

```

---

### Post by earthpigg on 2009-09-10
hi,

how do you connect to the internet? as many details as you can provide, please.

---

### Post by HankTorrents on 2009-09-10
I use a linksys wireless N router WRT150N.My ISP is cox. I am 10 feet away from the router. Below is the information on my NIC and wireless card
I am trying to figure out what else I could give you but nothing comes to mind. If you want any more info I 'll be happy to provide. Also thanks for your help its greatly appreciated.


```
description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e0:6d:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:26:4b:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.107 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

---

### Post by HankTorrents on 2009-09-10
It now comes mind that you might also mean how do I get my laptop to connect. I let it auto-connect with the stored password to the router. whats a lil odd is that it only has two bars of signal while I am in the same room

---

### Post by earthpigg on 2009-09-10
well, it might be related to networking but i am kind of doubting it.

could you look through your other system logs for same time frame?

somewhere is going to be something that will stand out to you as an error.

---

### Post by HankTorrents on 2009-09-11
Nothing that I could notice but I am new at doing this, I jus made the final switch from my mac onto this laptop my friend gave me. (bigger screen)

But I didnt notice anything to strange, seasoned eyes may be able to see what my dont. 


```
Sep  9 18:06:13 broozer kernel: [   20.428536] Bluetooth: RFCOMM socket layer initialized
Sep  9 18:06:13 broozer kernel: [   20.428550] Bluetooth: RFCOMM TTY layer initialized
Sep  9 18:06:13 broozer kernel: [   20.428551] Bluetooth: RFCOMM ver 1.8
Sep  9 18:06:15 broozer kernel: [   20.750368] [drm] Initialized drm 1.1.0 20060810
Sep  9 18:06:15 broozer kernel: [   20.754573] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  9 18:06:15 broozer kernel: [   20.754646] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Sep  9 18:06:19 broozer kernel: [   52.371143] [drm] Setting GART location based on new memory map
Sep  9 18:06:19 broozer kernel: [   52.372509] [drm] Loading R300 Microcode
Sep  9 18:06:19 broozer kernel: [   52.372558] [drm] writeback test succeeded in 1 usecs
Sep  9 18:06:57 broozer kernel: [   58.167270] NET: Registered protocol family 10
Sep  9 18:06:57 broozer kernel: [   58.168036] lo: Disabled Privacy Extensions
Sep  9 18:06:57 broozer kernel: [   58.169947] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  9 18:07:08 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  9 18:07:10 broozer kernel: [   27.532271] NET: Registered protocol family 17
Sep  9 18:07:12 broozer kernel: [   29.012587] UDF-fs: No VRS found
Sep  9 18:07:18 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep  9 18:07:18 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep  9 18:07:18 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep  9 18:07:18 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Sep  9 18:26:07 broozer -- MARK --
Sep  9 18:46:07 broozer -- MARK --
Sep  9 19:06:07 broozer -- MARK --
Sep  9 19:26:07 broozer -- MARK --
Sep  9 19:46:07 broozer -- MARK --
Sep  9 20:06:07 broozer -- MARK --
Sep  9 20:26:07 broozer -- MARK --
Sep  9 20:46:07 broozer -- MARK --
Sep  9 21:06:07 broozer -- MARK --
Sep  9 21:26:07 broozer -- MARK --
Sep  9 21:46:07 broozer -- MARK --
Sep  9 22:06:07 broozer -- MARK --
Sep  9 22:10:32 broozer kernel: [ 1885.613054] usb 4-2: USB disconnect, address 2
Sep  9 22:10:34 broozer kernel: [ 1886.443708] usb 4-2: new low speed USB device using uhci_hcd and address 3
Sep  9 22:10:34 broozer kernel: [ 1886.533796] usb 4-2: configuration #1 chosen from 1 choice
Sep  9 22:10:34 broozer kernel: [ 1886.556331] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input10
Sep  9 22:10:34 broozer kernel: [ 1886.582946] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.3-2
Sep  9 22:26:07 broozer -- MARK --
Sep  9 22:32:51 broozer kernel: [ 2226.990782] ACPI: Critical trip point
Sep  9 22:32:54 broozer exiting on signal 15
Sep  9 22:33:48 broozer syslogd 1.5.0#1ubuntu1: restart.
Sep  9 22:33:48 broozer kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep  9 22:33:48 broozer kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep  9 22:33:48 broozer kernel: Symbols match kernel version 2.6.24.
Sep  9 22:33:48 broozer kernel: Loaded 17998 symbols from 93 modules.
Sep  9 22:33:48 broozer kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  9 22:33:48 broozer kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  9 22:33:48 broozer kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep  9 22:33:48 broozer kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffda000 (usable)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 000000007ffda000 - 0000000080000000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep  9 22:33:48 broozer kernel: [    0.000000] 1151MB HIGHMEM available.
Sep  9 22:33:48 broozer kernel: [    0.000000] 896MB LOWMEM available.
Sep  9 22:33:48 broozer kernel: [    0.000000] Zone PFN ranges:
Sep  9 22:33:48 broozer kernel: [    0.000000]   DMA             0 ->     4096
Sep  9 22:33:48 broozer kernel: [    0.000000]   Normal       4096 ->   229376
Sep  9 22:33:48 broozer kernel: [    0.000000]   HighMem    229376 ->   524250
Sep  9 22:33:48 broozer kernel: [    0.000000] Movable zone start PFN for each node
Sep  9 22:33:48 broozer kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  9 22:33:48 broozer kernel: [    0.000000]     0:        0 ->   524250
Sep  9 22:33:48 broozer kernel: [    0.000000] DMI 2.3 present.
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: RSDT 7FFDA7D3, 0040 (r1 DELL    CPi R   27D5031D ASL        61)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: FACP 7FFDB400, 0074 (r1 DELL    CPi R   27D5031D ASL        61)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: DSDT 7FFDC000, 25EB (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: FACS 7FFEA800, 0040
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: APIC 7FFDBC00, 0068 (r1 DELL    CPi R   27D5031D ASL        47)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: MCFG 7FFDBBC0, 003E (r16 DELL    CPi R   27D5031D ASL        61)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: BOOT 7FFDB7C0, 0028 (r1 DELL    CPi R   27D5031D ASL        61)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: SSDT 7FFDABE6, 0280 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: SSDT 7FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: SSDT 7FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  9 22:33:48 broozer kernel: [    0.000000] Processor #0 6:13 APIC version 20
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  9 22:33:48 broozer kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  9 22:33:48 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  9 22:33:48 broozer kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  9 22:33:48 broozer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  9 22:33:48 broozer kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep  9 22:33:48 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep  9 22:33:48 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep  9 22:33:48 broozer kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520155
Sep  9 22:33:48 broozer kernel: [    0.000000] Kernel command line: root=UUID=983074b0-55d2-4305-aecb-3cfb9caafeb4 ro quiet splash
Sep  9 22:33:48 broozer kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep  9 22:33:48 broozer kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep  9 22:33:48 broozer kernel: [    0.000000] Initializing CPU#0
Sep  9 22:33:48 broozer kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  9 22:33:48 broozer kernel: [    0.000000] Detected 1995.025 MHz processor.
Sep  9 22:33:48 broozer kernel: [    6.626134] Console: colour VGA+ 80x25
Sep  9 22:33:48 broozer kernel: [    6.626138] console [tty0] enabled
Sep  9 22:33:48 broozer kernel: [    6.626450] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  9 22:33:48 broozer kernel: [    6.626829] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  9 22:33:48 broozer kernel: [    6.721691] Memory: 2067184k/2097000k available (2181k kernel code, 28672k reserved, 1006k data, 368k init, 1179496k highmem)
Sep  9 22:33:48 broozer kernel: [    6.721699] virtual kernel memory layout:
Sep  9 22:33:48 broozer kernel: [    6.721700]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep  9 22:33:48 broozer kernel: [    6.721701]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  9 22:33:48 broozer kernel: [    6.721703]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  9 22:33:48 broozer kernel: [    6.721704]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  9 22:33:48 broozer kernel: [    6.721705]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep  9 22:33:48 broozer kernel: [    6.721706]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep  9 22:33:48 broozer kernel: [    6.721707]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep  9 22:33:48 broozer kernel: [    6.721710] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  9 22:33:48 broozer kernel: [    6.721759] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep  9 22:33:48 broozer kernel: [    6.801746] Calibrating delay using timer specific routine.. 3994.28 BogoMIPS (lpj=7988573)
Sep  9 22:33:48 broozer kernel: [    6.801778] Security Framework initialized
Sep  9 22:33:48 broozer kernel: [    6.801787] SELinux:  Disabled at boot.
Sep  9 22:33:48 broozer kernel: [    6.801804] AppArmor: AppArmor initialized
Sep  9 22:33:48 broozer kernel: [    6.801808] Failure registering capabilities with primary security module.
Sep  9 22:33:48 broozer kernel: [    6.801817] Mount-cache hash table entries: 512
Sep  9 22:33:48 broozer kernel: [    6.801959] Initializing cgroup subsys ns
Sep  9 22:33:48 broozer kernel: [    6.801965] Initializing cgroup subsys cpuacct
Sep  9 22:33:48 broozer kernel: [    6.801987] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  9 22:33:48 broozer kernel: [    6.801989] CPU: L2 cache: 2048K
Sep  9 22:33:48 broozer kernel: [    6.802002] Compat vDSO mapped to ffffe000.
Sep  9 22:33:48 broozer kernel: [    6.802016] Checking 'hlt' instruction... OK.
Sep  9 22:33:48 broozer kernel: [    6.818083] SMP alternatives: switching to UP code
Sep  9 22:33:48 broozer kernel: [    6.819722] Freeing SMP alternatives: 11k freed
Sep  9 22:33:48 broozer kernel: [    6.819829] Early unpacking initramfs... done
Sep  9 22:33:48 broozer kernel: [    7.127636] ACPI: Core revision 20070126
Sep  9 22:33:48 broozer kernel: [    7.127680] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep  9 22:33:48 broozer kernel: [    7.129905] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Sep  9 22:33:48 broozer kernel: [    7.129921] Total of 1 processors activated (3994.28 BogoMIPS).
Sep  9 22:33:48 broozer kernel: [    7.130104] ENABLING IO-APIC IRQs
Sep  9 22:33:48 broozer kernel: [    7.130288] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  9 22:33:48 broozer kernel: [    7.250215] Brought up 1 CPUs
Sep  9 22:33:48 broozer kernel: [    7.250397] net_namespace: 64 bytes
Sep  9 22:33:48 broozer kernel: [    7.250409] Booting paravirtualized kernel on bare hardware
Sep  9 22:33:48 broozer kernel: [    7.250843] Time:  5:33:20  Date: 09/10/09
Sep  9 22:33:48 broozer kernel: [    7.250866] NET: Registered protocol family 16
Sep  9 22:33:48 broozer kernel: [    7.251048] EISA bus registered
Sep  9 22:33:48 broozer kernel: [    7.251074] ACPI: bus type pci registered
Sep  9 22:33:48 broozer kernel: [    7.291903] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
Sep  9 22:33:48 broozer kernel: [    7.291905] PCI: Using configuration type 1
Sep  9 22:33:48 broozer kernel: [    7.291917] Setting up standard PCI resources
Sep  9 22:33:48 broozer kernel: [    7.299580] ACPI: Interpreter enabled
Sep  9 22:33:48 broozer kernel: [    7.299583] ACPI: (supports S0 S3 S4 S5)
Sep  9 22:33:48 broozer kernel: [    7.299593] ACPI: Using IOAPIC for interrupt routing
Sep  9 22:33:48 broozer kernel: [    7.309817] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  9 22:33:48 broozer kernel: [    7.310491] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep  9 22:33:48 broozer kernel: [    7.310495] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep  9 22:33:48 broozer kernel: [    7.311194] PCI: Transparent bridge - 0000:00:1e.0
Sep  9 22:33:48 broozer kernel: [    7.316795] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Sep  9 22:33:48 broozer kernel: [    7.316886] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Sep  9 22:33:48 broozer kernel: [    7.316975] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep  9 22:33:48 broozer kernel: [    7.317063] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
Sep  9 22:33:48 broozer kernel: [    7.317138] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  9 22:33:48 broozer kernel: [    7.317216] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  9 22:33:48 broozer kernel: [    7.317294] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  9 22:33:48 broozer kernel: [    7.317402] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  9 22:33:48 broozer kernel: [    7.317429] pnp: PnP ACPI init
Sep  9 22:33:48 broozer kernel: [    7.317434] ACPI: bus type pnp registered
Sep  9 22:33:48 broozer kernel: [    7.328867] pnpacpi: exceeded the max number of mem resources: 12
Sep  9 22:33:48 broozer kernel: [    7.338811] pnp: PnP ACPI: found 11 devices
Sep  9 22:33:48 broozer kernel: [    7.338815] ACPI: ACPI bus type pnp unregistered
Sep  9 22:33:48 broozer kernel: [    7.338818] PnPBIOS: Disabled by ACPI PNP
Sep  9 22:33:48 broozer kernel: [    7.339008] PCI: Using ACPI for IRQ routing
Sep  9 22:33:48 broozer kernel: [    7.339014] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  9 22:33:48 broozer kernel: [    7.364890] NET: Registered protocol family 8
Sep  9 22:33:48 broozer kernel: [    7.364894] NET: Registered protocol family 20
Sep  9 22:33:48 broozer kernel: [    7.365038] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep  9 22:33:48 broozer kernel: [    7.365042] hpet0: 3 64-bit timers, 14318180 Hz
Sep  9 22:33:48 broozer kernel: [    7.365837] AppArmor: AppArmor Filesystem Enabled
Sep  9 22:33:48 broozer kernel: [    7.367903] Time: tsc clocksource has been installed.
Sep  9 22:33:48 broozer kernel: [    7.373970] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373973] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373976] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373981] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373983] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373986] system 00:00: iomem range 0x7ffda000-0x7fffffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373989] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373991] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373994] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373997] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.373999] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.374002] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.374009] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep  9 22:33:48 broozer kernel: [    7.374012] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep  9 22:33:48 broozer kernel: [    7.374014] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep  9 22:33:48 broozer kernel: [    7.374019] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep  9 22:33:48 broozer kernel: [    7.374022] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep  9 22:33:48 broozer kernel: [    7.374024] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep  9 22:33:48 broozer kernel: [    7.374029] system 00:03: ioport range 0x1060-0x107f has been reserved
```

---

### Post by HankTorrents on 2009-09-11
My computer jus shut down again, here is some more info

```
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep 10 20:01:00 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Sep 10 20:20:08 broozer -- MARK --
Sep 10 20:40:08 broozer -- MARK --
Sep 10 21:00:08 broozer -- MARK --
Sep 10 21:20:08 broozer -- MARK --
Sep 10 21:40:08 broozer -- MARK --
Sep 10 21:42:47 broozer kernel: [ 1549.045102] ACPI: Critical trip point
Sep 10 21:42:49 broozer exiting on signal 15
Sep 10 21:44:04 broozer syslogd 1.5.0#1ubuntu1: restart.
Sep 10 21:44:04 broozer kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep 10 21:44:04 broozer kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep 10 21:44:04 broozer kernel: Symbols match kernel version 2.6.24.
Sep 10 21:44:04 broozer kernel: Loaded 17649 symbols from 91 modules.
Sep 10 21:44:04 broozer kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 10 21:44:04 broozer kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 10 21:44:04 broozer kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep 10 21:44:04 broozer kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffda000 (usable)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 000000007ffda000 - 0000000080000000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep 10 21:44:04 broozer kernel: [    0.000000] 1151MB HIGHMEM available.
Sep 10 21:44:04 broozer kernel: [    0.000000] 896MB LOWMEM available.
Sep 10 21:44:04 broozer kernel: [    0.000000] Zone PFN ranges:
Sep 10 21:44:04 broozer kernel: [    0.000000]   DMA             0 ->     4096
Sep 10 21:44:04 broozer kernel: [    0.000000]   Normal       4096 ->   229376
Sep 10 21:44:04 broozer kernel: [    0.000000]   HighMem    229376 ->   524250
Sep 10 21:44:04 broozer kernel: [    0.000000] Movable zone start PFN for each node
Sep 10 21:44:04 broozer kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 10 21:44:04 broozer kernel: [    0.000000]     0:        0 ->   524250
Sep 10 21:44:04 broozer kernel: [    0.000000] DMI 2.3 present.
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: RSDT 7FFDA7D3, 0040 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: FACP 7FFDB400, 0074 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: DSDT 7FFDC000, 25EB (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: FACS 7FFEA800, 0040
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: APIC 7FFDBC00, 0068 (r1 DELL    CPi R   27D5031D ASL        47)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: MCFG 7FFDBBC0, 003E (r16 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: BOOT 7FFDB7C0, 0028 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: SSDT 7FFDABE6, 0280 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: SSDT 7FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: SSDT 7FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 10 21:44:04 broozer kernel: [    0.000000] Processor #0 6:13 APIC version 20
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep 10 21:44:04 broozer kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 10 21:44:04 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 10 21:44:04 broozer kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 10 21:44:04 broozer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 10 21:44:04 broozer kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep 10 21:44:04 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep 10 21:44:04 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep 10 21:44:04 broozer kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520155
Sep 10 21:44:04 broozer kernel: [    0.000000] Kernel command line: root=UUID=983074b0-55d2-4305-aecb-3cfb9caafeb4 ro quiet splash
Sep 10 21:44:04 broozer kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 10 21:44:04 broozer kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 10 21:44:04 broozer kernel: [    0.000000] Initializing CPU#0
Sep 10 21:44:04 broozer kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 10 21:44:04 broozer kernel: [    0.000000] Detected 1995.067 MHz processor.
Sep 10 21:44:04 broozer kernel: [    6.062437] Console: colour VGA+ 80x25
Sep 10 21:44:04 broozer kernel: [    6.062441] console [tty0] enabled
Sep 10 21:44:04 broozer kernel: [    6.062753] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 10 21:44:04 broozer kernel: [    6.063131] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 10 21:44:04 broozer kernel: [    6.158100] Memory: 2067184k/2097000k available (2181k kernel code, 28672k reserved, 1006k data, 368k init, 1179496k highmem)
Sep 10 21:44:04 broozer kernel: [    6.158108] virtual kernel memory layout:
Sep 10 21:44:04 broozer kernel: [    6.158109]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 10 21:44:04 broozer kernel: [    6.158110]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 10 21:44:04 broozer kernel: [    6.158111]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep 10 21:44:04 broozer kernel: [    6.158112]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep 10 21:44:04 broozer kernel: [    6.158114]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep 10 21:44:04 broozer kernel: [    6.158115]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep 10 21:44:04 broozer kernel: [    6.158116]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep 10 21:44:04 broozer kernel: [    6.158119] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 10 21:44:04 broozer kernel: [    6.158168] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 10 21:44:04 broozer kernel: [    6.238155] Calibrating delay using timer specific routine.. 3994.23 BogoMIPS (lpj=7988464)
Sep 10 21:44:04 broozer kernel: [    6.238189] Security Framework initialized
Sep 10 21:44:04 broozer kernel: [    6.238198] SELinux:  Disabled at boot.
Sep 10 21:44:04 broozer kernel: [    6.238215] AppArmor: AppArmor initialized
Sep 10 21:44:04 broozer kernel: [    6.238219] Failure registering capabilities with primary security module.
Sep 10 21:44:04 broozer kernel: [    6.238228] Mount-cache hash table entries: 512
Sep 10 21:44:04 broozer kernel: [    6.238370] Initializing cgroup subsys ns
Sep 10 21:44:04 broozer kernel: [    6.238376] Initializing cgroup subsys cpuacct
Sep 10 21:44:04 broozer kernel: [    6.238398] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 10 21:44:04 broozer kernel: [    6.238401] CPU: L2 cache: 2048K
Sep 10 21:44:04 broozer kernel: [    6.238414] Compat vDSO mapped to ffffe000.
Sep 10 21:44:04 broozer kernel: [    6.238428] Checking 'hlt' instruction... OK.
Sep 10 21:44:04 broozer kernel: [    6.254492] SMP alternatives: switching to UP code
Sep 10 21:44:04 broozer kernel: [    6.256131] Freeing SMP alternatives: 11k freed
Sep 10 21:44:04 broozer kernel: [    6.256237] Early unpacking initramfs... done
Sep 10 21:44:04 broozer kernel: [    6.564272] ACPI: Core revision 20070126
Sep 10 21:44:04 broozer kernel: [    6.564317] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 10 21:44:04 broozer kernel: [    6.566707] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Sep 10 21:44:04 broozer kernel: [    6.566723] Total of 1 processors activated (3994.23 BogoMIPS).
Sep 10 21:44:04 broozer kernel: [    6.566908] ENABLING IO-APIC IRQs
Sep 10 21:44:04 broozer kernel: [    6.567091] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 10 21:44:04 broozer kernel: [    6.713967] Brought up 1 CPUs
Sep 10 21:44:04 broozer kernel: [    6.714133] net_namespace: 64 bytes
Sep 10 21:44:04 broozer kernel: [    6.714144] Booting paravirtualized kernel on bare hardware
Sep 10 21:44:04 broozer kernel: [    6.714540] Time:  4:43:28  Date: 09/11/09
Sep 10 21:44:04 broozer kernel: [    6.714561] NET: Registered protocol family 16
Sep 10 21:44:04 broozer kernel: [    6.714728] EISA bus registered
Sep 10 21:44:04 broozer kernel: [    6.714752] ACPI: bus type pci registered
Sep 10 21:44:04 broozer kernel: [    6.752379] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
Sep 10 21:44:04 broozer kernel: [    6.752381] PCI: Using configuration type 1
Sep 10 21:44:04 broozer kernel: [    6.752393] Setting up standard PCI resources
Sep 10 21:44:04 broozer kernel: [    6.759430] ACPI: Interpreter enabled
Sep 10 21:44:04 broozer kernel: [    6.759433] ACPI: (supports S0 S3 S4 S5)
Sep 10 21:44:04 broozer kernel: [    6.759443] ACPI: Using IOAPIC for interrupt routing
Sep 10 21:44:04 broozer kernel: [    6.768832] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 10 21:44:04 broozer kernel: [    6.769456] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep 10 21:44:04 broozer kernel: [    6.769460] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep 10 21:44:04 broozer kernel: [    6.770104] PCI: Transparent bridge - 0000:00:1e.0
Sep 10 21:44:04 broozer kernel: [    6.775211] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Sep 10 21:44:04 broozer kernel: [    6.775293] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Sep 10 21:44:04 broozer kernel: [    6.775373] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep 10 21:44:04 broozer kernel: [    6.775453] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
Sep 10 21:44:04 broozer kernel: [    6.775522] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:44:04 broozer kernel: [    6.775594] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:44:04 broozer kernel: [    6.775665] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:44:04 broozer kernel: [    6.775763] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 10 21:44:04 broozer kernel: [    6.775788] pnp: PnP ACPI init
Sep 10 21:44:04 broozer kernel: [    6.775794] ACPI: bus type pnp registered
Sep 10 21:44:04 broozer kernel: [    6.786263] pnpacpi: exceeded the max number of mem resources: 12
Sep 10 21:44:04 broozer kernel: [    6.795339] pnp: PnP ACPI: found 11 devices
Sep 10 21:44:04 broozer kernel: [    6.795341] ACPI: ACPI bus type pnp unregistered
Sep 10 21:44:04 broozer kernel: [    6.795344] PnPBIOS: Disabled by ACPI PNP
Sep 10 21:44:04 broozer kernel: [    6.795518] PCI: Using ACPI for IRQ routing
Sep 10 21:44:04 broozer kernel: [    6.795520] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 10 21:44:04 broozer kernel: [    6.825884] NET: Registered protocol family 8
Sep 10 21:44:04 broozer kernel: [    6.825886] NET: Registered protocol family 20
Sep 10 21:44:04 broozer kernel: [    6.826027] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 10 21:44:04 broozer kernel: [    6.826031] hpet0: 3 64-bit timers, 14318180 Hz
Sep 10 21:44:04 broozer kernel: [    6.827062] AppArmor: AppArmor Filesystem Enabled
Sep 10 21:44:04 broozer kernel: [    6.829877] Time: tsc clocksource has been installed.
Sep 10 21:44:04 broozer kernel: [    6.837901] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837904] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837906] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837909] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837912] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837914] system 00:00: iomem range 0x7ffda000-0x7fffffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837917] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837920] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837922] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837925] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837928] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837930] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837936] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837938] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837941] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837945] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837948] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837950] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep 10 21:44:04 broozer kernel: [    6.837953] system 00:03: ioport range 0x1060-0x107f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837955] system 00:03: ioport range 0x1080-0x10bf has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837958] system 00:03: ioport range 0x10c0-0x10df has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837960] system 00:03: ioport range 0x10e0-0x10ff has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837966] system 00:08: ioport range 0x900-0x90f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837968] system 00:08: ioport range 0x910-0x91f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837971] system 00:08: ioport range 0x920-0x92f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837973] system 00:08: ioport range 0x930-0x93f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.837976] system 00:08: ioport range 0x940-0x97f has been reserved
Sep 10 21:44:04 broozer kernel: [    6.868296] PCI: Bridge: 0000:00:01.0
Sep 10 21:44:04 broozer kernel: [    6.868299]   IO window: d000-dfff
Sep 10 21:44:04 broozer kernel: [    6.868302]   MEM window: dfd00000-dfefffff
Sep 10 21:44:04 broozer kernel: [    6.868304]   PREFETCH window: d0000000-d7ffffff
Sep 10 21:44:04 broozer kernel: [    6.868315] PCI: Bus 4, cardbus bridge: 0000:03:01.0
Sep 10 21:44:04 broozer kernel: [    6.868317]   IO window: 00001400-000014ff
Sep 10 21:44:04 broozer kernel: [    6.868321]   IO window: 00001800-000018ff
Sep 10 21:44:04 broozer kernel: [    6.868325]   PREFETCH window: 88000000-8bffffff
Sep 10 21:44:04 broozer kernel: [    6.868329]   MEM window: 8c000000-8fffffff
Sep 10 21:44:04 broozer kernel: [    6.868333] PCI: Bridge: 0000:00:1e.0
Sep 10 21:44:04 broozer kernel: [    6.868335]   IO window: disabled.
Sep 10 21:44:04 broozer kernel: [    6.868340]   MEM window: dfc00000-dfcfffff
Sep 10 21:44:04 broozer kernel: [    6.868343]   PREFETCH window: disabled.
Sep 10 21:44:04 broozer kernel: [    6.868358] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:44:04 broozer kernel: [    6.868388] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
Sep 10 21:44:04 broozer kernel: [    6.868392] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Sep 10 21:44:04 broozer kernel: [    6.868405] NET: Registered protocol family 2
Sep 10 21:44:04 broozer kernel: [    6.905891] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 10 21:44:04 broozer kernel: [    6.906086] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 10 21:44:04 broozer kernel: [    6.906765] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 10 21:44:04 broozer kernel: [    6.907178] TCP: Hash tables configured (established 131072 bind 65536)
Sep 10 21:44:04 broozer kernel: [    6.907181] TCP reno registered
Sep 10 21:44:04 broozer kernel: [    6.917977] checking if image is initramfs... it is
Sep 10 21:44:04 broozer kernel: [    7.519502] Freeing initrd memory: 7319k freed
Sep 10 21:44:04 broozer kernel: [    7.519698] Simple Boot Flag at 0x79 set to 0x1
Sep 10 21:44:04 broozer kernel: [    7.520056] audit: initializing netlink socket (disabled)
Sep 10 21:44:04 broozer kernel: [    7.520070] audit(1252644208.256:1): initialized
Sep 10 21:44:04 broozer kernel: [    7.520262] highmem bounce pool size: 64 pages
Sep 10 21:44:04 broozer kernel: [    7.521896] VFS: Disk quotas dquot_6.5.1
Sep 10 21:44:04 broozer kernel: [    7.521960] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 10 21:44:04 broozer kernel: [    7.522084] io scheduler noop registered
Sep 10 21:44:04 broozer kernel: [    7.522086] io scheduler anticipatory registered
Sep 10 21:44:04 broozer kernel: [    7.522088] io scheduler deadline registered
Sep 10 21:44:04 broozer kernel: [    7.522097] io scheduler cfq registered (default)
Sep 10 21:44:04 broozer kernel: [    7.522310] assign_interrupt_mode Found MSI capability
Sep 10 21:44:04 broozer kernel: [    7.522540] isapnp: Scanning for PnP cards...
Sep 10 21:44:04 broozer kernel: [    7.876405] isapnp: No Plug & Play device found
Sep 10 21:44:04 broozer kernel: [    7.899414] Real Time Clock Driver v1.12ac
Sep 10 21:44:04 broozer kernel: [    7.899506] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 10 21:44:04 broozer kernel: [    7.899989] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:44:04 broozer kernel: [    7.899998] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Sep 10 21:44:04 broozer kernel: [    7.900523] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 10 21:44:04 broozer kernel: [    7.900581] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 10 21:44:04 broozer kernel: [    7.900662] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 10 21:44:04 broozer kernel: [    7.905419] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 10 21:44:04 broozer kernel: [    7.905423] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 10 21:44:04 broozer kernel: [    7.909360] mice: PS/2 mouse device common for all mice
Sep 10 21:44:04 broozer kernel: [    7.909454] EISA: Probing bus 0 at eisa.0
Sep 10 21:44:04 broozer kernel: [    7.909461] Cannot allocate resource for EISA slot 1
Sep 10 21:44:04 broozer kernel: [    7.909487] EISA: Detected 0 cards.
Sep 10 21:44:04 broozer kernel: [    7.909490] cpuidle: using governor ladder
Sep 10 21:44:04 broozer kernel: [    7.909492] cpuidle: using governor menu
Sep 10 21:44:04 broozer kernel: [    7.909573] NET: Registered protocol family 1
Sep 10 21:44:04 broozer kernel: [    7.909597] Using IPI No-Shortcut mode
Sep 10 21:44:04 broozer kernel: [    7.909627] registered taskstats version 1
Sep 10 21:44:04 broozer kernel: [    7.909718]   Magic number: 9:948:716
Sep 10 21:44:04 broozer kernel: [    7.909809] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 10 21:44:04 broozer kernel: [    7.909811] EDD information not available.
Sep 10 21:44:04 broozer kernel: [    7.909990] Freeing unused kernel memory: 368k freed
Sep 10 21:44:04 broozer kernel: [    7.910013] Write protecting the kernel read-only data: 802k
Sep 10 21:44:04 broozer kernel: [    7.913057] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 10 21:44:04 broozer kernel: [    9.077844] fuse init (API version 7.9)
Sep 10 21:44:04 broozer kernel: [    9.092166] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Sep 10 21:44:04 broozer kernel: [    9.092172] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep 10 21:44:04 broozer kernel: [    9.092183] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep 10 21:44:04 broozer kernel: [    9.095402] ACPI: Thermal Zone [THM] (91 C)
Sep 10 21:44:04 broozer kernel: [    9.525764] usbcore: registered new interface driver usbfs
Sep 10 21:44:04 broozer kernel: [    9.525787] usbcore: registered new interface driver hub
Sep 10 21:44:04 broozer kernel: [    9.532351] usbcore: registered new device driver usb
Sep 10 21:44:04 broozer kernel: [    9.540345] USB Universal Host Controller Interface driver v3.0
Sep 10 21:44:04 broozer kernel: [    9.540399] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:44:04 broozer kernel: [    9.540415] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 10 21:44:04 broozer kernel: [    9.540735] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Sep 10 21:44:04 broozer kernel: [    9.540766] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
Sep 10 21:44:04 broozer kernel: [    9.540883] usb usb1: configuration #1 chosen from 1 choice
Sep 10 21:44:04 broozer kernel: [    9.540905] hub 1-0:1.0: USB hub found
Sep 10 21:44:04 broozer kernel: [    9.540910] hub 1-0:1.0: 2 ports detected
Sep 10 21:44:04 broozer kernel: [    9.644362] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:44:04 broozer kernel: [    9.644380] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 10 21:44:04 broozer kernel: [    9.644405] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Sep 10 21:44:04 broozer kernel: [    9.644437] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
Sep 10 21:44:04 broozer kernel: [    9.644537] usb usb2: configuration #1 chosen from 1 choice
Sep 10 21:44:04 broozer kernel: [    9.644557] hub 2-0:1.0: USB hub found
Sep 10 21:44:04 broozer kernel: [    9.644562] hub 2-0:1.0: 2 ports detected
Sep 10 21:44:04 broozer kernel: [    9.664642] SCSI subsystem initialized
Sep 10 21:44:04 broozer kernel: [    9.748296] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:44:04 broozer kernel: [    9.748313] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 10 21:44:04 broozer kernel: [    9.748333] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Sep 10 21:44:04 broozer kernel: [    9.748364] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
Sep 10 21:44:04 broozer kernel: [    9.748462] usb usb3: configuration #1 chosen from 1 choice
Sep 10 21:44:04 broozer kernel: [    9.748482] hub 3-0:1.0: USB hub found
Sep 10 21:44:04 broozer kernel: [    9.748487] hub 3-0:1.0: 2 ports detected
Sep 10 21:44:04 broozer kernel: [    9.852232] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Sep 10 21:44:04 broozer kernel: [    9.852249] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep 10 21:44:04 broozer kernel: [    9.852269] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Sep 10 21:44:04 broozer kernel: [    9.852300] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
Sep 10 21:44:04 broozer kernel: [    9.852399] usb usb4: configuration #1 chosen from 1 choice
Sep 10 21:44:04 broozer kernel: [    9.852418] hub 4-0:1.0: USB hub found
Sep 10 21:44:04 broozer kernel: [    9.852423] hub 4-0:1.0: 2 ports detected
Sep 10 21:44:04 broozer kernel: [    9.956345] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:44:04 broozer kernel: [    9.956363] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 10 21:44:04 broozer kernel: [    9.956385] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Sep 10 21:44:04 broozer kernel: [    9.960301] ehci_hcd 0000:00:1d.7: debug port 1
Sep 10 21:44:04 broozer kernel: [    9.960313] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
Sep 10 21:44:04 broozer kernel: [    9.976088] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 10 21:44:04 broozer kernel: [    9.976180] usb usb5: configuration #1 chosen from 1 choice
Sep 10 21:44:04 broozer kernel: [    9.976201] hub 5-0:1.0: USB hub found
Sep 10 21:44:04 broozer kernel: [    9.976207] hub 5-0:1.0: 8 ports detected
Sep 10 21:44:04 broozer kernel: [   10.081945] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:44:04 broozer kernel: [   10.134664] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 10 21:44:04 broozer kernel: [   10.155481] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:44:04 broozer kernel: [   10.171973] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Sep 10 21:44:04 broozer kernel: [   10.171980] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Sep 10 21:44:04 broozer kernel: [   10.171986] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Sep 10 21:44:04 broozer kernel: [   10.211972] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Sep 10 21:44:04 broozer kernel: [   10.211989] b44.c:v2.0
Sep 10 21:44:04 broozer kernel: [   10.212026] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:44:04 broozer kernel: [   10.212064] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 10 21:44:04 broozer kernel: [   10.232208] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:e0:6d:16
Sep 10 21:44:04 broozer kernel: [   10.239960] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep 10 21:44:04 broozer kernel: [   10.323868] Clocksource tsc unstable (delta = -11852258539 ns)
Sep 10 21:44:04 broozer kernel: [   10.328280] Time: hpet clocksource has been installed.
Sep 10 21:44:04 broozer kernel: [   10.329940] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:44:04 broozer kernel: [   10.330117] scsi0 : ata_piix
Sep 10 21:44:04 broozer kernel: [   10.330249] scsi1 : ata_piix
Sep 10 21:44:04 broozer kernel: [   10.330380] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Sep 10 21:44:04 broozer kernel: [   10.330383] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Sep 10 21:44:04 broozer kernel: [   10.336468] ata1.00: ATA-6: WDC WD400VE-75HDT0, 09.07D09, max UDMA/100
Sep 10 21:44:04 broozer kernel: [   10.336472] ata1.00: 78140160 sectors, multi 8: LBA 
Sep 10 21:44:04 broozer kernel: [   10.336474] ata1.00: applying bridge limits
Sep 10 21:44:04 broozer kernel: [   10.337479] ata1.00: configured for UDMA/100
Sep 10 21:44:04 broozer kernel: [   10.346382] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B101, max UDMA/33
Sep 10 21:44:04 broozer kernel: [   10.350794] ata2.00: configured for UDMA/33
Sep 10 21:44:04 broozer kernel: [   10.350893] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400VE-75HD 09.0 PQ: 0 ANSI: 5
Sep 10 21:44:04 broozer kernel: [   10.351483] scsi 1:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B101 PQ: 0 ANSI: 5
Sep 10 21:44:04 broozer kernel: [   10.361804] Driver 'sd' needs updating - please use bus_type methods
Sep 10 21:44:04 broozer kernel: [   10.361869] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 21:44:04 broozer kernel: [   10.361879] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 21:44:04 broozer kernel: [   10.361895] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 21:44:04 broozer kernel: [   10.361934] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 21:44:04 broozer kernel: [   10.361942] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 21:44:04 broozer kernel: [   10.361957] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 21:44:04 broozer kernel: [   10.361960]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep 10 21:44:04 broozer kernel: [   10.382068]  sda1 sda2 < sda5 >
Sep 10 21:44:04 broozer kernel: [   10.382728] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 10 21:44:04 broozer kernel: [   10.387322] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 10 21:44:04 broozer kernel: [   10.387338] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep 10 21:44:04 broozer kernel: [   10.403055] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep 10 21:44:04 broozer kernel: [   10.403059] Uniform CD-ROM driver Revision: 3.20
Sep 10 21:44:04 broozer kernel: [   10.465883] Attempting manual resume
Sep 10 21:44:04 broozer kernel: [   10.478696] kjournald starting.  Commit interval 5 seconds
Sep 10 21:44:04 broozer kernel: [   10.478705] EXT3-fs: mounted filesystem with ordered data mode.
Sep 10 21:44:04 broozer kernel: [   12.481087] Linux agpgart interface v0.102
Sep 10 21:44:04 broozer kernel: [   12.563653] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 10 21:44:04 broozer kernel: [   12.613682] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 10 21:44:04 broozer kernel: [   12.881354] ACPI: AC Adapter [AC] (on-line)
Sep 10 21:44:04 broozer kernel: [   13.259787] ACPI: Battery Slot [BAT0] (battery present)
Sep 10 21:44:04 broozer kernel: [   13.259920] input: Lid Switch as /devices/virtual/input/input2
Sep 10 21:44:04 broozer kernel: [   13.260372] ACPI: Lid Switch [LID]
Sep 10 21:44:04 broozer kernel: [   13.260412] input: Power Button (CM) as /devices/virtual/input/input3
Sep 10 21:44:04 broozer kernel: [   13.268557] ACPI: Power Button (CM) [PBTN]
Sep 10 21:44:04 broozer kernel: [   13.268609] input: Sleep Button (CM) as /devices/virtual/input/input4
Sep 10 21:44:04 broozer kernel: [   13.284541] ACPI: Sleep Button (CM) [SBTN]
Sep 10 21:44:04 broozer kernel: [   13.568451] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
Sep 10 21:44:04 broozer kernel: [   13.697078] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17
Sep 10 21:44:04 broozer kernel: [   13.697081] Socket status: 30000006
Sep 10 21:44:04 broozer kernel: [   13.697084] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Sep 10 21:44:04 broozer kernel: [   13.697089] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
Sep 10 21:44:04 broozer kernel: [   13.732414] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep 10 21:44:04 broozer kernel: [   13.732418] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep 10 21:44:04 broozer kernel: [   13.876200] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Sep 10 21:44:04 broozer kernel: [   13.876204] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Sep 10 21:44:04 broozer kernel: [   13.876289] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:44:04 broozer kernel: [   13.920158] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Sep 10 21:44:04 broozer kernel: [   13.952149] sdhci: Secure Digital Host Controller Interface driver
Sep 10 21:44:04 broozer kernel: [   13.952153] sdhci: Copyright(c) Pierre Ossman
Sep 10 21:44:04 broozer kernel: [   14.408629] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input5
Sep 10 21:44:04 broozer kernel: [   14.419853] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Sep 10 21:44:04 broozer kernel: [   14.827616] iTCO_vendor_support: vendor-support=0
Sep 10 21:44:04 broozer kernel: [   14.860274] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep 10 21:44:04 broozer kernel: [   14.860394] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
Sep 10 21:44:04 broozer kernel: [   14.860438] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep 10 21:44:04 broozer kernel: [   15.223472] input: PC Speaker as /devices/platform/pcspkr/input/input6
Sep 10 21:44:04 broozer kernel: [   15.492012] input: PS/2 Mouse as /devices/virtual/input/input7
Sep 10 21:44:04 broozer kernel: [   15.524556] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Sep 10 21:44:04 broozer kernel: [   15.663760] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep 10 21:44:04 broozer kernel: [   16.747033] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Sep 10 21:44:04 broozer kernel: [   16.747059] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
Sep 10 21:44:04 broozer kernel: [   16.747080] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:44:04 broozer kernel: [   16.747131] mmc0: SDHCI at 0xdfcfc700 irq 18 DMA
Sep 10 21:44:04 broozer kernel: [   16.754059] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:44:04 broozer kernel: [   16.765721] cs: IO port probe 0x100-0x3af: clean.
Sep 10 21:44:04 broozer kernel: [   16.767418] cs: IO port probe 0x3e0-0x4ff: clean.
Sep 10 21:44:04 broozer kernel: [   16.768128] cs: IO port probe 0x820-0x8ff: clean.
Sep 10 21:44:04 broozer kernel: [   16.768718] cs: IO port probe 0xc00-0xcf7: clean.
Sep 10 21:44:04 broozer kernel: [   16.769450] cs: IO port probe 0xa00-0xaff: clean.
Sep 10 21:44:04 broozer kernel: [   16.818475] intel8x0_measure_ac97_clock: measured 55390 usecs
Sep 10 21:44:04 broozer kernel: [   16.818478] intel8x0: clocking to 48000
Sep 10 21:44:04 broozer kernel: [   16.916816] lp: driver loaded but no devices found
Sep 10 21:44:04 broozer kernel: [   17.068223] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
Sep 10 21:44:04 broozer kernel: [   17.142907] EXT3 FS on sda1, internal journal
Sep 10 21:44:04 broozer kernel: [   17.454688] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 10 21:44:04 broozer kernel: [   17.639398] No dock devices found.
Sep 10 21:44:05 broozer kernel: [   18.253847] apm: BIOS not found.
Sep 10 21:44:05 broozer kernel: [   18.303086] ppdev: user-space parallel port driver
Sep 10 21:44:05 broozer kernel: [   18.317245] audit(1252644245.576:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4905 profile="/usr/sbin/cupsd" namespace="default"
Sep 10 21:44:05 broozer dhcdbd: Started up.
Sep 10 21:44:05 broozer kernel: [   27.558480] Marking TSC unstable due to: cpufreq changes.
Sep 10 21:44:06 broozer kernel: [   18.957330] Bluetooth: Core ver 2.11
Sep 10 21:44:06 broozer kernel: [   18.958163] NET: Registered protocol family 31
Sep 10 21:44:06 broozer kernel: [   18.958166] Bluetooth: HCI device and connection manager initialized
Sep 10 21:44:06 broozer kernel: [   18.958169] Bluetooth: HCI socket layer initialized
Sep 10 21:44:06 broozer kernel: [   28.456214] Bluetooth: L2CAP ver 2.9
Sep 10 21:44:06 broozer kernel: [   28.456220] Bluetooth: L2CAP socket layer initialized
Sep 10 21:44:07 broozer kernel: [   19.029035] Bluetooth: RFCOMM socket layer initialized
Sep 10 21:44:07 broozer kernel: [   19.029048] Bluetooth: RFCOMM TTY layer initialized
Sep 10 21:44:07 broozer kernel: [   19.029050] Bluetooth: RFCOMM ver 1.8
Sep 10 21:44:09 broozer kernel: [   19.328204] [drm] Initialized drm 1.1.0 20060810
Sep 10 21:44:09 broozer kernel: [   19.332427] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:44:09 broozer kernel: [   19.332498] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Sep 10 21:44:12 broozer kernel: [   48.822555] [drm] Setting GART location based on new memory map
Sep 10 21:44:12 broozer kernel: [   48.823952] [drm] Loading R300 Microcode
Sep 10 21:44:12 broozer kernel: [   48.824001] [drm] writeback test succeeded in 1 usecs
Sep 10 21:45:15 broozer kernel: [   54.814815] NET: Registered protocol family 10
Sep 10 21:45:15 broozer kernel: [   54.815562] lo: Disabled Privacy Extensions
Sep 10 21:45:15 broozer kernel: [   54.817492] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 10 21:45:26 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep 10 21:45:28 broozer kernel: [   25.918612] NET: Registered protocol family 17
Sep 10 21:45:34 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep 10 21:45:34 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep 10 21:45:34 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep 10 21:45:34 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
```

---

### Post by HankTorrents on 2009-09-11
and guess what it did twice? I had to reboot twice before being able to get on here

```
Sep 10 21:52:19 broozer kernel: [  249.358506] ACPI: Critical trip point
Sep 10 21:52:22 broozer exiting on signal 15
Sep 10 21:53:37 broozer syslogd 1.5.0#1ubuntu1: restart.
Sep 10 21:53:37 broozer kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep 10 21:53:37 broozer kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep 10 21:53:37 broozer kernel: Symbols match kernel version 2.6.24.
Sep 10 21:53:37 broozer kernel: Loaded 17649 symbols from 91 modules.
Sep 10 21:53:37 broozer kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 10 21:53:37 broozer kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 10 21:53:37 broozer kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep 10 21:53:37 broozer kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffda000 (usable)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 000000007ffda000 - 0000000080000000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep 10 21:53:37 broozer kernel: [    0.000000] 1151MB HIGHMEM available.
Sep 10 21:53:37 broozer kernel: [    0.000000] 896MB LOWMEM available.
Sep 10 21:53:37 broozer kernel: [    0.000000] Zone PFN ranges:
Sep 10 21:53:37 broozer kernel: [    0.000000]   DMA             0 ->     4096
Sep 10 21:53:37 broozer kernel: [    0.000000]   Normal       4096 ->   229376
Sep 10 21:53:37 broozer kernel: [    0.000000]   HighMem    229376 ->   524250
Sep 10 21:53:37 broozer kernel: [    0.000000] Movable zone start PFN for each node
Sep 10 21:53:37 broozer kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 10 21:53:37 broozer kernel: [    0.000000]     0:        0 ->   524250
Sep 10 21:53:37 broozer kernel: [    0.000000] DMI 2.3 present.
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: RSDT 7FFDA7D3, 0040 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: FACP 7FFDB400, 0074 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: DSDT 7FFDC000, 25EB (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: FACS 7FFEA800, 0040
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: APIC 7FFDBC00, 0068 (r1 DELL    CPi R   27D5031D ASL        47)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: MCFG 7FFDBBC0, 003E (r16 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: BOOT 7FFDB7C0, 0028 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: SSDT 7FFDABE6, 0280 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: SSDT 7FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: SSDT 7FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 10 21:53:37 broozer kernel: [    0.000000] Processor #0 6:13 APIC version 20
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep 10 21:53:37 broozer kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 10 21:53:37 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 10 21:53:37 broozer kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 10 21:53:37 broozer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 10 21:53:37 broozer kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep 10 21:53:37 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep 10 21:53:37 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep 10 21:53:37 broozer kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520155
Sep 10 21:53:37 broozer kernel: [    0.000000] Kernel command line: root=UUID=983074b0-55d2-4305-aecb-3cfb9caafeb4 ro quiet splash
Sep 10 21:53:37 broozer kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 10 21:53:37 broozer kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 10 21:53:37 broozer kernel: [    0.000000] Initializing CPU#0
Sep 10 21:53:37 broozer kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 10 21:53:37 broozer kernel: [    0.000000] Detected 1514.759 MHz processor.
Sep 10 21:53:37 broozer kernel: [    8.913854] Console: colour VGA+ 80x25
Sep 10 21:53:37 broozer kernel: [    8.913861] console [tty0] enabled
Sep 10 21:53:37 broozer kernel: [    8.914317] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 10 21:53:37 broozer kernel: [    8.914867] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 10 21:53:37 broozer kernel: [    9.052628] Memory: 2067184k/2097000k available (2181k kernel code, 28672k reserved, 1006k data, 368k init, 1179496k highmem)
Sep 10 21:53:37 broozer kernel: [    9.052641] virtual kernel memory layout:
Sep 10 21:53:37 broozer kernel: [    9.052643]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 10 21:53:37 broozer kernel: [    9.052644]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 10 21:53:37 broozer kernel: [    9.052646]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep 10 21:53:37 broozer kernel: [    9.052647]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep 10 21:53:37 broozer kernel: [    9.052648]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep 10 21:53:37 broozer kernel: [    9.052650]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep 10 21:53:37 broozer kernel: [    9.052651]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep 10 21:53:37 broozer kernel: [    9.052655] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 10 21:53:37 broozer kernel: [    9.052729] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 10 21:53:37 broozer kernel: [    9.132495] Calibrating delay using timer specific routine.. 3021.72 BogoMIPS (lpj=6043448)
Sep 10 21:53:37 broozer kernel: [    9.132546] Security Framework initialized
Sep 10 21:53:37 broozer kernel: [    9.132558] SELinux:  Disabled at boot.
Sep 10 21:53:37 broozer kernel: [    9.132584] AppArmor: AppArmor initialized
Sep 10 21:53:37 broozer kernel: [    9.132590] Failure registering capabilities with primary security module.
Sep 10 21:53:37 broozer kernel: [    9.132604] Mount-cache hash table entries: 512
Sep 10 21:53:37 broozer kernel: [    9.132810] Initializing cgroup subsys ns
Sep 10 21:53:37 broozer kernel: [    9.132817] Initializing cgroup subsys cpuacct
Sep 10 21:53:37 broozer kernel: [    9.132848] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 10 21:53:37 broozer kernel: [    9.132851] CPU: L2 cache: 2048K
Sep 10 21:53:37 broozer kernel: [    9.132870] Compat vDSO mapped to ffffe000.
Sep 10 21:53:37 broozer kernel: [    9.132891] Checking 'hlt' instruction... OK.
Sep 10 21:53:37 broozer kernel: [    9.148950] SMP alternatives: switching to UP code
Sep 10 21:53:37 broozer kernel: [    9.151314] Freeing SMP alternatives: 11k freed
Sep 10 21:53:37 broozer kernel: [    9.151468] Early unpacking initramfs... done
Sep 10 21:53:37 broozer kernel: [    9.599083] ACPI: Core revision 20070126
Sep 10 21:53:37 broozer kernel: [    9.599149] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 10 21:53:37 broozer kernel: [    9.603359] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Sep 10 21:53:37 broozer kernel: [    9.603382] Total of 1 processors activated (3021.72 BogoMIPS).
Sep 10 21:53:37 broozer kernel: [    9.603648] ENABLING IO-APIC IRQs
Sep 10 21:53:37 broozer kernel: [    9.603870] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 10 21:53:37 broozer kernel: [    9.750260] Brought up 1 CPUs
Sep 10 21:53:37 broozer kernel: [    9.750502] net_namespace: 64 bytes
Sep 10 21:53:37 broozer kernel: [    9.750516] Booting paravirtualized kernel on bare hardware
Sep 10 21:53:37 broozer kernel: [    9.751088] Time:  4:52:53  Date: 09/11/09
Sep 10 21:53:37 broozer kernel: [    9.751118] NET: Registered protocol family 16
Sep 10 21:53:37 broozer kernel: [    9.751360] EISA bus registered
Sep 10 21:53:37 broozer kernel: [    9.751394] ACPI: bus type pci registered
Sep 10 21:53:37 broozer kernel: [    9.805180] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
Sep 10 21:53:37 broozer kernel: [    9.805183] PCI: Using configuration type 1
Sep 10 21:53:37 broozer kernel: [    9.805202] Setting up standard PCI resources
Sep 10 21:53:37 broozer kernel: [    9.815165] ACPI: Interpreter enabled
Sep 10 21:53:37 broozer kernel: [    9.815169] ACPI: (supports S0 S3 S4 S5)
Sep 10 21:53:37 broozer kernel: [    9.815183] ACPI: Using IOAPIC for interrupt routing
Sep 10 21:53:37 broozer kernel: [    9.828667] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 10 21:53:37 broozer kernel: [    9.829554] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep 10 21:53:37 broozer kernel: [    9.829562] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep 10 21:53:37 broozer kernel: [    9.830481] PCI: Transparent bridge - 0000:00:1e.0
Sep 10 21:53:37 broozer kernel: [    9.837876] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Sep 10 21:53:37 broozer kernel: [    9.837996] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Sep 10 21:53:37 broozer kernel: [    9.838113] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep 10 21:53:37 broozer kernel: [    9.838226] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
Sep 10 21:53:37 broozer kernel: [    9.838326] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:53:37 broozer kernel: [    9.838431] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:53:37 broozer kernel: [    9.838533] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:53:37 broozer kernel: [    9.838673] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 10 21:53:37 broozer kernel: [    9.838709] pnp: PnP ACPI init
Sep 10 21:53:37 broozer kernel: [    9.838719] ACPI: bus type pnp registered
Sep 10 21:53:37 broozer kernel: [    9.853811] pnpacpi: exceeded the max number of mem resources: 12
Sep 10 21:53:37 broozer kernel: [    9.866929] pnp: PnP ACPI: found 11 devices
Sep 10 21:53:37 broozer kernel: [    9.866932] ACPI: ACPI bus type pnp unregistered
Sep 10 21:53:37 broozer kernel: [    9.866936] PnPBIOS: Disabled by ACPI PNP
Sep 10 21:53:37 broozer kernel: [    9.867187] PCI: Using ACPI for IRQ routing
Sep 10 21:53:37 broozer kernel: [    9.867190] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 10 21:53:37 broozer kernel: [    9.901396] NET: Registered protocol family 8
Sep 10 21:53:37 broozer kernel: [    9.901398] NET: Registered protocol family 20
Sep 10 21:53:37 broozer kernel: [    9.901588] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 10 21:53:37 broozer kernel: [    9.901593] hpet0: 3 64-bit timers, 14318180 Hz
Sep 10 21:53:37 broozer kernel: [    9.902644] AppArmor: AppArmor Filesystem Enabled
Sep 10 21:53:37 broozer kernel: [    9.905367] Time: tsc clocksource has been installed.
Sep 10 21:53:37 broozer kernel: [    9.913365] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913369] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913373] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913376] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913379] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913383] system 00:00: iomem range 0x7ffda000-0x7fffffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913387] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913390] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913396] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913400] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913403] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913407] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913414] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913417] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913420] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913429] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913433] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913436] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep 10 21:53:37 broozer kernel: [    9.913439] system 00:03: ioport range 0x1060-0x107f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913442] system 00:03: ioport range 0x1080-0x10bf has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913446] system 00:03: ioport range 0x10c0-0x10df has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913449] system 00:03: ioport range 0x10e0-0x10ff has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913459] system 00:08: ioport range 0x900-0x90f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913463] system 00:08: ioport range 0x910-0x91f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913466] system 00:08: ioport range 0x920-0x92f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913469] system 00:08: ioport range 0x930-0x93f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.913472] system 00:08: ioport range 0x940-0x97f has been reserved
Sep 10 21:53:37 broozer kernel: [    9.943953] PCI: Bridge: 0000:00:01.0
Sep 10 21:53:37 broozer kernel: [    9.943956]   IO window: d000-dfff
Sep 10 21:53:37 broozer kernel: [    9.943960]   MEM window: dfd00000-dfefffff
Sep 10 21:53:37 broozer kernel: [    9.943963]   PREFETCH window: d0000000-d7ffffff
Sep 10 21:53:37 broozer kernel: [    9.943977] PCI: Bus 4, cardbus bridge: 0000:03:01.0
Sep 10 21:53:37 broozer kernel: [    9.943980]   IO window: 00001400-000014ff
Sep 10 21:53:37 broozer kernel: [    9.943988]   IO window: 00001800-000018ff
Sep 10 21:53:37 broozer kernel: [    9.943993]   PREFETCH window: 88000000-8bffffff
Sep 10 21:53:37 broozer kernel: [    9.943999]   MEM window: 8c000000-8fffffff
Sep 10 21:53:37 broozer kernel: [    9.944004] PCI: Bridge: 0000:00:1e.0
Sep 10 21:53:37 broozer kernel: [    9.944006]   IO window: disabled.
Sep 10 21:53:37 broozer kernel: [    9.944015]   MEM window: dfc00000-dfcfffff
Sep 10 21:53:37 broozer kernel: [    9.944020]   PREFETCH window: disabled.
Sep 10 21:53:37 broozer kernel: [    9.944041] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:53:37 broozer kernel: [    9.944086] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
Sep 10 21:53:37 broozer kernel: [    9.944090] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Sep 10 21:53:37 broozer kernel: [    9.944111] NET: Registered protocol family 2
Sep 10 21:53:37 broozer kernel: [    9.981032] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 10 21:53:37 broozer kernel: [    9.981314] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 10 21:53:37 broozer kernel: [    9.982299] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 10 21:53:37 broozer kernel: [    9.982900] TCP: Hash tables configured (established 131072 bind 65536)
Sep 10 21:53:37 broozer kernel: [    9.982904] TCP reno registered
Sep 10 21:53:37 broozer kernel: [    9.993096] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Sep 10 21:53:37 broozer kernel: [   10.411652]  it is
Sep 10 21:53:37 broozer kernel: [   10.865863] Freeing initrd memory: 7319k freed
Sep 10 21:53:37 broozer kernel: [   10.866139] Simple Boot Flag at 0x79 set to 0x1
Sep 10 21:53:37 broozer kernel: [   10.866656] audit: initializing netlink socket (disabled)
Sep 10 21:53:37 broozer kernel: [   10.866676] audit(1252644773.712:1): initialized
Sep 10 21:53:37 broozer kernel: [   10.866951] highmem bounce pool size: 64 pages
Sep 10 21:53:37 broozer kernel: [   10.869316] VFS: Disk quotas dquot_6.5.1
Sep 10 21:53:37 broozer kernel: [   10.869409] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 10 21:53:37 broozer kernel: [   10.869587] io scheduler noop registered
Sep 10 21:53:37 broozer kernel: [   10.869589] io scheduler anticipatory registered
Sep 10 21:53:37 broozer kernel: [   10.869592] io scheduler deadline registered
Sep 10 21:53:37 broozer kernel: [   10.869605] io scheduler cfq registered (default)
Sep 10 21:53:37 broozer kernel: [   10.869908] assign_interrupt_mode Found MSI capability
Sep 10 21:53:37 broozer kernel: [   10.870235] isapnp: Scanning for PnP cards...
Sep 10 21:53:37 broozer kernel: [   11.224250] isapnp: No Plug & Play device found
Sep 10 21:53:37 broozer kernel: [   11.256882] Real Time Clock Driver v1.12ac
Sep 10 21:53:37 broozer kernel: [   11.257013] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 10 21:53:37 broozer kernel: [   11.257921] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:53:37 broozer kernel: [   11.257935] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Sep 10 21:53:37 broozer kernel: [   11.258677] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 10 21:53:37 broozer kernel: [   11.258763] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 10 21:53:37 broozer kernel: [   11.258881] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 10 21:53:37 broozer kernel: [   11.263655] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 10 21:53:37 broozer kernel: [   11.263660] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 10 21:53:37 broozer kernel: [   11.269353] mice: PS/2 mouse device common for all mice
Sep 10 21:53:37 broozer kernel: [   11.269487] EISA: Probing bus 0 at eisa.0
Sep 10 21:53:37 broozer kernel: [   11.269495] Cannot allocate resource for EISA slot 1
Sep 10 21:53:37 broozer kernel: [   11.269533] EISA: Detected 0 cards.
Sep 10 21:53:37 broozer kernel: [   11.269537] cpuidle: using governor ladder
Sep 10 21:53:37 broozer kernel: [   11.269539] cpuidle: using governor menu
Sep 10 21:53:37 broozer kernel: [   11.269656] NET: Registered protocol family 1
Sep 10 21:53:37 broozer kernel: [   11.269692] Using IPI No-Shortcut mode
Sep 10 21:53:37 broozer kernel: [   11.269735] registered taskstats version 1
Sep 10 21:53:37 broozer kernel: [   11.269877]   Magic number: 9:604:868
Sep 10 21:53:37 broozer kernel: [   11.269942]   hash matches device ptyw6
Sep 10 21:53:37 broozer kernel: [   11.270000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 10 21:53:37 broozer kernel: [   11.270003] EDD information not available.
Sep 10 21:53:37 broozer kernel: [   11.270257] Freeing unused kernel memory: 368k freed
Sep 10 21:53:37 broozer kernel: [   11.270298] Write protecting the kernel read-only data: 802k
Sep 10 21:53:37 broozer kernel: [   11.274177] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 10 21:53:37 broozer kernel: [   12.511764] fuse init (API version 7.9)
Sep 10 21:53:37 broozer kernel: [   12.532392] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Sep 10 21:53:37 broozer kernel: [   12.532402] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep 10 21:53:37 broozer kernel: [   12.532417] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep 10 21:53:37 broozer kernel: [   12.536858] ACPI: Thermal Zone [THM] (90 C)
Sep 10 21:53:37 broozer kernel: [   13.177171] usbcore: registered new interface driver usbfs
Sep 10 21:53:37 broozer kernel: [   13.177206] usbcore: registered new interface driver hub
Sep 10 21:53:37 broozer kernel: [   13.193148] usbcore: registered new device driver usb
Sep 10 21:53:37 broozer kernel: [   13.207716] USB Universal Host Controller Interface driver v3.0
Sep 10 21:53:37 broozer kernel: [   13.207798] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:53:37 broozer kernel: [   13.207821] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 10 21:53:37 broozer kernel: [   13.208278] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Sep 10 21:53:37 broozer kernel: [   13.208322] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
Sep 10 21:53:37 broozer kernel: [   13.208493] usb usb1: configuration #1 chosen from 1 choice
Sep 10 21:53:37 broozer kernel: [   13.208524] hub 1-0:1.0: USB hub found
Sep 10 21:53:37 broozer kernel: [   13.208531] hub 1-0:1.0: 2 ports detected
Sep 10 21:53:37 broozer kernel: [   13.309233] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:53:37 broozer kernel: [   13.309259] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 10 21:53:37 broozer kernel: [   13.309294] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Sep 10 21:53:37 broozer kernel: [   13.309340] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
Sep 10 21:53:37 broozer kernel: [   13.309488] usb usb2: configuration #1 chosen from 1 choice
Sep 10 21:53:37 broozer kernel: [   13.309516] hub 2-0:1.0: USB hub found
Sep 10 21:53:37 broozer kernel: [   13.309525] hub 2-0:1.0: 2 ports detected
Sep 10 21:53:37 broozer kernel: [   13.383256] SCSI subsystem initialized
Sep 10 21:53:37 broozer kernel: [   13.413225] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:53:37 broozer kernel: [   13.413250] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 10 21:53:37 broozer kernel: [   13.413280] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Sep 10 21:53:37 broozer kernel: [   13.413319] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
Sep 10 21:53:37 broozer kernel: [   13.413462] usb usb3: configuration #1 chosen from 1 choice
Sep 10 21:53:37 broozer kernel: [   13.413490] hub 3-0:1.0: USB hub found
Sep 10 21:53:37 broozer kernel: [   13.413497] hub 3-0:1.0: 2 ports detected
Sep 10 21:53:37 broozer kernel: [   13.517215] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Sep 10 21:53:37 broozer kernel: [   13.517238] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep 10 21:53:37 broozer kernel: [   13.517267] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Sep 10 21:53:37 broozer kernel: [   13.517314] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
Sep 10 21:53:37 broozer kernel: [   13.517455] usb usb4: configuration #1 chosen from 1 choice
Sep 10 21:53:37 broozer kernel: [   13.517482] hub 4-0:1.0: USB hub found
Sep 10 21:53:37 broozer kernel: [   13.517489] hub 4-0:1.0: 2 ports detected
Sep 10 21:53:37 broozer kernel: [   13.621413] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:53:37 broozer kernel: [   13.621439] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 10 21:53:37 broozer kernel: [   13.621469] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Sep 10 21:53:37 broozer kernel: [   13.625398] ehci_hcd 0000:00:1d.7: debug port 1
Sep 10 21:53:37 broozer kernel: [   13.625417] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
Sep 10 21:53:37 broozer kernel: [   13.641087] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 10 21:53:37 broozer kernel: [   13.641218] usb usb5: configuration #1 chosen from 1 choice
Sep 10 21:53:37 broozer kernel: [   13.641247] hub 5-0:1.0: USB hub found
Sep 10 21:53:37 broozer kernel: [   13.641255] hub 5-0:1.0: 8 ports detected
Sep 10 21:53:37 broozer kernel: [   13.747174] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:53:37 broozer kernel: [   13.799822] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 10 21:53:37 broozer kernel: [   13.815825] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:53:37 broozer kernel: [   13.833092] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Sep 10 21:53:37 broozer kernel: [   13.833101] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Sep 10 21:53:37 broozer kernel: [   13.833110] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Sep 10 21:53:37 broozer kernel: [   13.877127] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Sep 10 21:53:37 broozer kernel: [   13.877158] b44.c:v2.0
Sep 10 21:53:37 broozer kernel: [   13.877346] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:53:37 broozer kernel: [   13.877407] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 10 21:53:37 broozer kernel: [   13.897468] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:e0:6d:16
Sep 10 21:53:37 broozer kernel: [   13.901708] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep 10 21:53:37 broozer kernel: [   14.057078] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:53:37 broozer kernel: [   14.057916] scsi0 : ata_piix
Sep 10 21:53:37 broozer kernel: [   14.058280] scsi1 : ata_piix
Sep 10 21:53:37 broozer kernel: [   14.058472] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Sep 10 21:53:37 broozer kernel: [   14.058476] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Sep 10 21:53:37 broozer kernel: [   14.221586] ata1.00: ATA-6: WDC WD400VE-75HDT0, 09.07D09, max UDMA/100
Sep 10 21:53:37 broozer kernel: [   14.221592] ata1.00: 78140160 sectors, multi 8: LBA 
Sep 10 21:53:37 broozer kernel: [   14.221595] ata1.00: applying bridge limits
Sep 10 21:53:37 broozer kernel: [   14.229597] ata1.00: configured for UDMA/100
Sep 10 21:53:37 broozer kernel: [   14.401008] Clocksource tsc unstable (delta = -15697257220 ns)
Sep 10 21:53:37 broozer kernel: [   14.405051] Time: hpet clocksource has been installed.
Sep 10 21:53:37 broozer kernel: [   14.412340] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B101, max UDMA/33
Sep 10 21:53:37 broozer kernel: [   14.418432] ata2.00: configured for UDMA/33
Sep 10 21:53:37 broozer kernel: [   14.418586] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400VE-75HD 09.0 PQ: 0 ANSI: 5
Sep 10 21:53:37 broozer kernel: [   14.419427] scsi 1:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B101 PQ: 0 ANSI: 5
Sep 10 21:53:37 broozer kernel: [   14.435921] Driver 'sd' needs updating - please use bus_type methods
Sep 10 21:53:37 broozer kernel: [   14.436022] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 21:53:37 broozer kernel: [   14.436036] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 21:53:37 broozer kernel: [   14.436060] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 21:53:37 broozer kernel: [   14.436116] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 21:53:37 broozer kernel: [   14.436127] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 21:53:37 broozer kernel: [   14.436149] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 21:53:37 broozer kernel: [   14.436153]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep 10 21:53:37 broozer kernel: [   14.465952]  sda1 sda2 < sda5 >
Sep 10 21:53:37 broozer kernel: [   14.467792] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 10 21:53:37 broozer kernel: [   14.474406] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 10 21:53:37 broozer kernel: [   14.474426] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep 10 21:53:37 broozer kernel: [   14.489637] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep 10 21:53:37 broozer kernel: [   14.489644] Uniform CD-ROM driver Revision: 3.20
Sep 10 21:53:37 broozer kernel: [   14.587273] Attempting manual resume
Sep 10 21:53:37 broozer kernel: [   14.605597] kjournald starting.  Commit interval 5 seconds
Sep 10 21:53:37 broozer kernel: [   14.605611] EXT3-fs: mounted filesystem with ordered data mode.
Sep 10 21:53:37 broozer kernel: [   17.931828] Linux agpgart interface v0.102
Sep 10 21:53:37 broozer kernel: [   18.023428] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 10 21:53:37 broozer kernel: [   18.079242] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 10 21:53:37 broozer kernel: [   18.469994] ACPI: AC Adapter [AC] (on-line)
Sep 10 21:53:37 broozer kernel: [   19.126869] ACPI: Battery Slot [BAT0] (battery present)
Sep 10 21:53:37 broozer kernel: [   19.126948] input: Lid Switch as /devices/virtual/input/input2
Sep 10 21:53:37 broozer kernel: [   19.127541] ACPI: Lid Switch [LID]
Sep 10 21:53:37 broozer kernel: [   19.127600] input: Power Button (CM) as /devices/virtual/input/input3
Sep 10 21:53:37 broozer kernel: [   19.138007] ACPI: Power Button (CM) [PBTN]
Sep 10 21:53:37 broozer kernel: [   19.138069] input: Sleep Button (CM) as /devices/virtual/input/input4
Sep 10 21:53:37 broozer kernel: [   19.153911] ACPI: Sleep Button (CM) [SBTN]
Sep 10 21:53:37 broozer kernel: [   19.400829] iTCO_vendor_support: vendor-support=0
Sep 10 21:53:37 broozer kernel: [   19.466355] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep 10 21:53:37 broozer kernel: [   19.466468] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
Sep 10 21:53:37 broozer kernel: [   19.466515] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep 10 21:53:37 broozer kernel: [   19.688704] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep 10 21:53:37 broozer kernel: [   19.688710] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep 10 21:53:37 broozer kernel: [   19.806951] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
Sep 10 21:53:37 broozer kernel: [   19.874787] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Sep 10 21:53:37 broozer kernel: [   19.874793] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Sep 10 21:53:37 broozer kernel: [   19.930525] sdhci: Secure Digital Host Controller Interface driver
Sep 10 21:53:37 broozer kernel: [   19.930529] sdhci: Copyright(c) Pierre Ossman
Sep 10 21:53:37 broozer kernel: [   19.935313] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17
Sep 10 21:53:37 broozer kernel: [   19.935318] Socket status: 30000006
Sep 10 21:53:37 broozer kernel: [   19.935321] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Sep 10 21:53:37 broozer kernel: [   19.935327] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
Sep 10 21:53:37 broozer kernel: [   19.986269] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:53:37 broozer kernel: [   20.024072] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Sep 10 21:53:37 broozer kernel: [   20.980932] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input5
Sep 10 21:53:37 broozer kernel: [   20.992892] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Sep 10 21:53:37 broozer kernel: [   21.212929] input: PC Speaker as /devices/platform/pcspkr/input/input6
Sep 10 21:53:37 broozer kernel: [   21.426514] input: PS/2 Mouse as /devices/virtual/input/input7
Sep 10 21:53:37 broozer kernel: [   21.455978] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Sep 10 21:53:37 broozer kernel: [   22.289134] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep 10 21:53:37 broozer kernel: [   23.600372] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Sep 10 21:53:37 broozer kernel: [   23.600412] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
Sep 10 21:53:37 broozer kernel: [   23.600442] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:53:37 broozer kernel: [   23.600516] mmc0: SDHCI at 0xdfcfc700 irq 18 DMA
Sep 10 21:53:37 broozer kernel: [   23.607264] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:53:37 broozer kernel: [   23.624265] cs: IO port probe 0x100-0x3af: clean.
Sep 10 21:53:37 broozer kernel: [   23.626670] cs: IO port probe 0x3e0-0x4ff: clean.
Sep 10 21:53:37 broozer kernel: [   23.627700] cs: IO port probe 0x820-0x8ff: clean.
Sep 10 21:53:37 broozer kernel: [   23.628534] cs: IO port probe 0xc00-0xcf7: clean.
Sep 10 21:53:37 broozer kernel: [   23.629572] cs: IO port probe 0xa00-0xaff: clean.
Sep 10 21:53:37 broozer kernel: [   23.684133] intel8x0_measure_ac97_clock: measured 55310 usecs
Sep 10 21:53:37 broozer kernel: [   23.684137] intel8x0: clocking to 48000
Sep 10 21:53:37 broozer kernel: [   23.826286] lp: driver loaded but no devices found
Sep 10 21:53:37 broozer kernel: [   24.044885] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
Sep 10 21:53:37 broozer kernel: [   24.153203] EXT3 FS on sda1, internal journal
Sep 10 21:53:37 broozer kernel: [   24.602211] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 10 21:53:37 broozer kernel: [   24.877031] No dock devices found.
Sep 10 21:53:37 broozer kernel: [   25.766715] apm: BIOS not found.
Sep 10 21:53:38 broozer kernel: [   25.837101] ppdev: user-space parallel port driver
Sep 10 21:53:38 broozer kernel: [   25.857882] audit(1252644818.203:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4911 profile="/usr/sbin/cupsd" namespace="default"
Sep 10 21:53:38 broozer dhcdbd: Started up.
Sep 10 21:53:38 broozer kernel: [   32.442001] Marking TSC unstable due to: cpufreq changes.
Sep 10 21:53:39 broozer kernel: [   26.777362] Bluetooth: Core ver 2.11
Sep 10 21:53:39 broozer kernel: [   26.778049] NET: Registered protocol family 31
Sep 10 21:53:39 broozer kernel: [   26.778056] Bluetooth: HCI device and connection manager initialized
Sep 10 21:53:39 broozer kernel: [   26.778060] Bluetooth: HCI socket layer initialized
Sep 10 21:53:39 broozer kernel: [   26.838019] Bluetooth: L2CAP ver 2.9
Sep 10 21:53:39 broozer kernel: [   26.838031] Bluetooth: L2CAP socket layer initialized
Sep 10 21:53:39 broozer kernel: [   26.887115] Bluetooth: RFCOMM socket layer initialized
Sep 10 21:53:39 broozer kernel: [   26.887138] Bluetooth: RFCOMM TTY layer initialized
Sep 10 21:53:39 broozer kernel: [   26.887140] Bluetooth: RFCOMM ver 1.8
Sep 10 21:53:42 broozer kernel: [   27.319847] [drm] Initialized drm 1.1.0 20060810
Sep 10 21:53:42 broozer kernel: [   27.325556] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:53:42 broozer kernel: [   27.325661] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Sep 10 21:53:45 broozer kernel: [   69.033432] [drm] Setting GART location based on new memory map
Sep 10 21:53:45 broozer kernel: [   69.034882] [drm] Loading R300 Microcode
Sep 10 21:53:45 broozer kernel: [   69.034953] [drm] writeback test succeeded in 1 usecs
Sep 10 21:53:53 broozer exiting on signal 15
Sep 10 21:55:11 broozer syslogd 1.5.0#1ubuntu1: restart.
Sep 10 21:55:11 broozer kernel: Inspecting /boot/System.map-2.6.24-24-generic
Sep 10 21:55:11 broozer kernel: Loaded 27919 symbols from /boot/System.map-2.6.24-24-generic.
Sep 10 21:55:11 broozer kernel: Symbols match kernel version 2.6.24.
Sep 10 21:55:11 broozer kernel: Loaded 17649 symbols from 91 modules.
Sep 10 21:55:11 broozer kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 10 21:55:11 broozer kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 10 21:55:11 broozer kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
Sep 10 21:55:11 broozer kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffda000 (usable)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 000000007ffda000 - 0000000080000000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep 10 21:55:11 broozer kernel: [    0.000000] 1151MB HIGHMEM available.
Sep 10 21:55:11 broozer kernel: [    0.000000] 896MB LOWMEM available.
Sep 10 21:55:11 broozer kernel: [    0.000000] Zone PFN ranges:
Sep 10 21:55:11 broozer kernel: [    0.000000]   DMA             0 ->     4096
Sep 10 21:55:11 broozer kernel: [    0.000000]   Normal       4096 ->   229376
Sep 10 21:55:11 broozer kernel: [    0.000000]   HighMem    229376 ->   524250
Sep 10 21:55:11 broozer kernel: [    0.000000] Movable zone start PFN for each node
Sep 10 21:55:11 broozer kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 10 21:55:11 broozer kernel: [    0.000000]     0:        0 ->   524250
Sep 10 21:55:11 broozer kernel: [    0.000000] DMI 2.3 present.
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: RSDT 7FFDA7D3, 0040 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: FACP 7FFDB400, 0074 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: DSDT 7FFDC000, 25EB (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: FACS 7FFEA800, 0040
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: APIC 7FFDBC00, 0068 (r1 DELL    CPi R   27D5031D ASL        47)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: MCFG 7FFDBBC0, 003E (r16 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: BOOT 7FFDB7C0, 0028 (r1 DELL    CPi R   27D5031D ASL        61)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: SSDT 7FFDABE6, 0280 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: SSDT 7FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: SSDT 7FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 10 21:55:11 broozer kernel: [    0.000000] Processor #0 6:13 APIC version 20
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep 10 21:55:11 broozer kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 10 21:55:11 broozer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 10 21:55:11 broozer kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 10 21:55:11 broozer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 10 21:55:11 broozer kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Sep 10 21:55:11 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep 10 21:55:11 broozer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep 10 21:55:11 broozer kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520155
Sep 10 21:55:11 broozer kernel: [    0.000000] Kernel command line: root=UUID=983074b0-55d2-4305-aecb-3cfb9caafeb4 ro quiet splash
Sep 10 21:55:11 broozer kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 10 21:55:11 broozer kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 10 21:55:11 broozer kernel: [    0.000000] Initializing CPU#0
Sep 10 21:55:11 broozer kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 10 21:55:11 broozer kernel: [    0.000000] Detected 1995.064 MHz processor.
Sep 10 21:55:11 broozer kernel: [    6.100678] Console: colour VGA+ 80x25
Sep 10 21:55:11 broozer kernel: [    6.100681] console [tty0] enabled
Sep 10 21:55:11 broozer kernel: [    6.100993] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 10 21:55:11 broozer kernel: [    6.101371] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 10 21:55:11 broozer kernel: [    6.196335] Memory: 2067184k/2097000k available (2181k kernel code, 28672k reserved, 1006k data, 368k init, 1179496k highmem)
Sep 10 21:55:11 broozer kernel: [    6.196344] virtual kernel memory layout:
Sep 10 21:55:11 broozer kernel: [    6.196345]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 10 21:55:11 broozer kernel: [    6.196346]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 10 21:55:11 broozer kernel: [    6.196347]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep 10 21:55:11 broozer kernel: [    6.196348]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep 10 21:55:11 broozer kernel: [    6.196349]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
Sep 10 21:55:11 broozer kernel: [    6.196350]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
Sep 10 21:55:11 broozer kernel: [    6.196351]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
Sep 10 21:55:11 broozer kernel: [    6.196354] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 10 21:55:11 broozer kernel: [    6.196403] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 10 21:55:11 broozer kernel: [    6.276391] Calibrating delay using timer specific routine.. 3994.24 BogoMIPS (lpj=7988487)
Sep 10 21:55:11 broozer kernel: [    6.276424] Security Framework initialized
Sep 10 21:55:11 broozer kernel: [    6.276433] SELinux:  Disabled at boot.
Sep 10 21:55:11 broozer kernel: [    6.276450] AppArmor: AppArmor initialized
Sep 10 21:55:11 broozer kernel: [    6.276454] Failure registering capabilities with primary security module.
Sep 10 21:55:11 broozer kernel: [    6.276463] Mount-cache hash table entries: 512
Sep 10 21:55:11 broozer kernel: [    6.276606] Initializing cgroup subsys ns
Sep 10 21:55:11 broozer kernel: [    6.276612] Initializing cgroup subsys cpuacct
Sep 10 21:55:11 broozer kernel: [    6.276635] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 10 21:55:11 broozer kernel: [    6.276637] CPU: L2 cache: 2048K
Sep 10 21:55:11 broozer kernel: [    6.276650] Compat vDSO mapped to ffffe000.
Sep 10 21:55:11 broozer kernel: [    6.276664] Checking 'hlt' instruction... OK.
Sep 10 21:55:11 broozer kernel: [    6.292729] SMP alternatives: switching to UP code
Sep 10 21:55:11 broozer kernel: [    6.294367] Freeing SMP alternatives: 11k freed
Sep 10 21:55:11 broozer kernel: [    6.294473] Early unpacking initramfs... done
Sep 10 21:55:11 broozer kernel: [    6.603279] ACPI: Core revision 20070126
Sep 10 21:55:11 broozer kernel: [    6.603324] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 10 21:55:11 broozer kernel: [    6.606399] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Sep 10 21:55:11 broozer kernel: [    6.606415] Total of 1 processors activated (3994.24 BogoMIPS).
Sep 10 21:55:11 broozer kernel: [    6.606605] ENABLING IO-APIC IRQs
Sep 10 21:55:11 broozer kernel: [    6.606788] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 10 21:55:11 broozer kernel: [    6.752202] Brought up 1 CPUs
Sep 10 21:55:11 broozer kernel: [    6.752367] net_namespace: 64 bytes
Sep 10 21:55:11 broozer kernel: [    6.752378] Booting paravirtualized kernel on bare hardware
Sep 10 21:55:11 broozer kernel: [    6.752774] Time:  4:54:35  Date: 09/11/09
Sep 10 21:55:11 broozer kernel: [    6.752796] NET: Registered protocol family 16
Sep 10 21:55:11 broozer kernel: [    6.752962] EISA bus registered
Sep 10 21:55:11 broozer kernel: [    6.752985] ACPI: bus type pci registered
Sep 10 21:55:11 broozer kernel: [    6.790599] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
Sep 10 21:55:11 broozer kernel: [    6.790601] PCI: Using configuration type 1
Sep 10 21:55:11 broozer kernel: [    6.790613] Setting up standard PCI resources
Sep 10 21:55:11 broozer kernel: [    6.797804] ACPI: Interpreter enabled
Sep 10 21:55:11 broozer kernel: [    6.797807] ACPI: (supports S0 S3 S4 S5)
Sep 10 21:55:11 broozer kernel: [    6.797817] ACPI: Using IOAPIC for interrupt routing
Sep 10 21:55:11 broozer kernel: [    6.807236] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 10 21:55:11 broozer kernel: [    6.807857] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep 10 21:55:11 broozer kernel: [    6.807861] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep 10 21:55:11 broozer kernel: [    6.808506] PCI: Transparent bridge - 0000:00:1e.0
Sep 10 21:55:11 broozer kernel: [    6.813619] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Sep 10 21:55:11 broozer kernel: [    6.813701] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Sep 10 21:55:11 broozer kernel: [    6.813781] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep 10 21:55:11 broozer kernel: [    6.813860] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
Sep 10 21:55:11 broozer kernel: [    6.813930] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:55:11 broozer kernel: [    6.814001] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:55:11 broozer kernel: [    6.814073] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 10 21:55:11 broozer kernel: [    6.814170] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 10 21:55:11 broozer kernel: [    6.814195] pnp: PnP ACPI init
Sep 10 21:55:11 broozer kernel: [    6.814201] ACPI: bus type pnp registered
Sep 10 21:55:11 broozer kernel: [    6.824672] pnpacpi: exceeded the max number of mem resources: 12
Sep 10 21:55:11 broozer kernel: [    6.833759] pnp: PnP ACPI: found 11 devices
Sep 10 21:55:11 broozer kernel: [    6.833761] ACPI: ACPI bus type pnp unregistered
Sep 10 21:55:11 broozer kernel: [    6.833764] PnPBIOS: Disabled by ACPI PNP
Sep 10 21:55:11 broozer kernel: [    6.833939] PCI: Using ACPI for IRQ routing
Sep 10 21:55:11 broozer kernel: [    6.833941] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 10 21:55:11 broozer kernel: [    6.864115] NET: Registered protocol family 8
Sep 10 21:55:11 broozer kernel: [    6.864117] NET: Registered protocol family 20
Sep 10 21:55:11 broozer kernel: [    6.864258] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 10 21:55:11 broozer kernel: [    6.864262] hpet0: 3 64-bit timers, 14318180 Hz
Sep 10 21:55:11 broozer kernel: [    6.865292] AppArmor: AppArmor Filesystem Enabled
Sep 10 21:55:11 broozer kernel: [    6.868108] Time: tsc clocksource has been installed.
Sep 10 21:55:11 broozer kernel: [    6.876132] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876135] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876137] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876140] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876142] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876145] system 00:00: iomem range 0x7ffda000-0x7fffffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876148] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876151] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876153] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876156] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876159] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876161] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876166] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876169] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876171] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876176] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876179] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876181] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep 10 21:55:11 broozer kernel: [    6.876184] system 00:03: ioport range 0x1060-0x107f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876186] system 00:03: ioport range 0x1080-0x10bf has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876189] system 00:03: ioport range 0x10c0-0x10df has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876191] system 00:03: ioport range 0x10e0-0x10ff has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876197] system 00:08: ioport range 0x900-0x90f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876199] system 00:08: ioport range 0x910-0x91f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876202] system 00:08: ioport range 0x920-0x92f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876204] system 00:08: ioport range 0x930-0x93f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.876206] system 00:08: ioport range 0x940-0x97f has been reserved
Sep 10 21:55:11 broozer kernel: [    6.906527] PCI: Bridge: 0000:00:01.0
Sep 10 21:55:11 broozer kernel: [    6.906529]   IO window: d000-dfff
Sep 10 21:55:11 broozer kernel: [    6.906532]   MEM window: dfd00000-dfefffff
Sep 10 21:55:11 broozer kernel: [    6.906535]   PREFETCH window: d0000000-d7ffffff
Sep 10 21:55:11 broozer kernel: [    6.906545] PCI: Bus 4, cardbus bridge: 0000:03:01.0
Sep 10 21:55:11 broozer kernel: [    6.906547]   IO window: 00001400-000014ff
Sep 10 21:55:11 broozer kernel: [    6.906551]   IO window: 00001800-000018ff
Sep 10 21:55:11 broozer kernel: [    6.906555]   PREFETCH window: 88000000-8bffffff
Sep 10 21:55:11 broozer kernel: [    6.906560]   MEM window: 8c000000-8fffffff
Sep 10 21:55:11 broozer kernel: [    6.906564] PCI: Bridge: 0000:00:1e.0
Sep 10 21:55:11 broozer kernel: [    6.906565]   IO window: disabled.
Sep 10 21:55:11 broozer kernel: [    6.906570]   MEM window: dfc00000-dfcfffff
Sep 10 21:55:11 broozer kernel: [    6.906574]   PREFETCH window: disabled.
Sep 10 21:55:11 broozer kernel: [    6.906589] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:55:11 broozer kernel: [    6.906619] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
Sep 10 21:55:11 broozer kernel: [    6.906623] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Sep 10 21:55:11 broozer kernel: [    6.906635] NET: Registered protocol family 2
Sep 10 21:55:11 broozer kernel: [    6.944118] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 10 21:55:11 broozer kernel: [    6.944313] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 10 21:55:11 broozer kernel: [    6.945008] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 10 21:55:11 broozer kernel: [    6.945420] TCP: Hash tables configured (established 131072 bind 65536)
Sep 10 21:55:11 broozer kernel: [    6.945423] TCP reno registered
Sep 10 21:55:11 broozer kernel: [    6.956208] checking if image is initramfs... it is
Sep 10 21:55:11 broozer kernel: [    7.556832] Freeing initrd memory: 7319k freed
Sep 10 21:55:11 broozer kernel: [    7.557024] Simple Boot Flag at 0x79 set to 0x1
Sep 10 21:55:11 broozer kernel: [    7.557379] audit: initializing netlink socket (disabled)
Sep 10 21:55:11 broozer kernel: [    7.557393] audit(1252644875.256:1): initialized
Sep 10 21:55:11 broozer kernel: [    7.557585] highmem bounce pool size: 64 pages
Sep 10 21:55:11 broozer kernel: [    7.559201] VFS: Disk quotas dquot_6.5.1
Sep 10 21:55:11 broozer kernel: [    7.559266] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 10 21:55:11 broozer kernel: [    7.559391] io scheduler noop registered
Sep 10 21:55:11 broozer kernel: [    7.559393] io scheduler anticipatory registered
Sep 10 21:55:11 broozer kernel: [    7.559395] io scheduler deadline registered
Sep 10 21:55:11 broozer kernel: [    7.559405] io scheduler cfq registered (default)
Sep 10 21:55:11 broozer kernel: [    7.559619] assign_interrupt_mode Found MSI capability
Sep 10 21:55:11 broozer kernel: [    7.559868] isapnp: Scanning for PnP cards...
Sep 10 21:55:11 broozer kernel: [    7.913723] isapnp: No Plug & Play device found
Sep 10 21:55:11 broozer kernel: [    7.936475] Real Time Clock Driver v1.12ac
Sep 10 21:55:11 broozer kernel: [    7.936567] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 10 21:55:11 broozer kernel: [    7.937056] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:55:11 broozer kernel: [    7.937064] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Sep 10 21:55:11 broozer kernel: [    7.937592] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 10 21:55:11 broozer kernel: [    7.937650] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 10 21:55:11 broozer kernel: [    7.937729] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 10 21:55:11 broozer kernel: [    7.942531] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 10 21:55:11 broozer kernel: [    7.942535] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 10 21:55:11 broozer kernel: [    7.943640] mice: PS/2 mouse device common for all mice
Sep 10 21:55:11 broozer kernel: [    7.943735] EISA: Probing bus 0 at eisa.0
Sep 10 21:55:11 broozer kernel: [    7.943741] Cannot allocate resource for EISA slot 1
Sep 10 21:55:11 broozer kernel: [    7.943768] EISA: Detected 0 cards.
Sep 10 21:55:11 broozer kernel: [    7.943771] cpuidle: using governor ladder
Sep 10 21:55:11 broozer kernel: [    7.943772] cpuidle: using governor menu
Sep 10 21:55:11 broozer kernel: [    7.943851] NET: Registered protocol family 1
Sep 10 21:55:11 broozer kernel: [    7.943875] Using IPI No-Shortcut mode
Sep 10 21:55:11 broozer kernel: [    7.943904] registered taskstats version 1
Sep 10 21:55:11 broozer kernel: [    7.943995]   Magic number: 9:157:919
Sep 10 21:55:11 broozer kernel: [    7.944083] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 10 21:55:11 broozer kernel: [    7.944085] EDD information not available.
Sep 10 21:55:11 broozer kernel: [    7.944262] Freeing unused kernel memory: 368k freed
Sep 10 21:55:11 broozer kernel: [    7.944285] Write protecting the kernel read-only data: 802k
Sep 10 21:55:11 broozer kernel: [    7.948345] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 10 21:55:11 broozer kernel: [    9.111562] fuse init (API version 7.9)
Sep 10 21:55:11 broozer kernel: [    9.125854] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Sep 10 21:55:11 broozer kernel: [    9.125860] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep 10 21:55:11 broozer kernel: [    9.125872] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Sep 10 21:55:11 broozer kernel: [    9.129005] ACPI: Thermal Zone [THM] (90 C)
Sep 10 21:55:11 broozer kernel: [    9.554404] usbcore: registered new interface driver usbfs
Sep 10 21:55:11 broozer kernel: [    9.554426] usbcore: registered new interface driver hub
Sep 10 21:55:11 broozer kernel: [    9.566610] usbcore: registered new device driver usb
Sep 10 21:55:11 broozer kernel: [    9.578569] USB Universal Host Controller Interface driver v3.0
Sep 10 21:55:11 broozer kernel: [    9.578623] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:55:11 broozer kernel: [    9.578640] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 10 21:55:11 broozer kernel: [    9.578961] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Sep 10 21:55:11 broozer kernel: [    9.578993] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
Sep 10 21:55:11 broozer kernel: [    9.579107] usb usb1: configuration #1 chosen from 1 choice
Sep 10 21:55:11 broozer kernel: [    9.579128] hub 1-0:1.0: USB hub found
Sep 10 21:55:11 broozer kernel: [    9.579133] hub 1-0:1.0: 2 ports detected
Sep 10 21:55:11 broozer kernel: [    9.682589] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:55:11 broozer kernel: [    9.682605] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 10 21:55:11 broozer kernel: [    9.682630] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Sep 10 21:55:11 broozer kernel: [    9.682663] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
Sep 10 21:55:11 broozer kernel: [    9.682764] usb usb2: configuration #1 chosen from 1 choice
Sep 10 21:55:11 broozer kernel: [    9.682784] hub 2-0:1.0: USB hub found
Sep 10 21:55:11 broozer kernel: [    9.682788] hub 2-0:1.0: 2 ports detected
Sep 10 21:55:11 broozer kernel: [    9.695259] SCSI subsystem initialized
Sep 10 21:55:11 broozer kernel: [    9.786534] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:55:11 broozer kernel: [    9.786551] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 10 21:55:11 broozer kernel: [    9.786571] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Sep 10 21:55:11 broozer kernel: [    9.786602] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
Sep 10 21:55:11 broozer kernel: [    9.786699] usb usb3: configuration #1 chosen from 1 choice
Sep 10 21:55:11 broozer kernel: [    9.786719] hub 3-0:1.0: USB hub found
Sep 10 21:55:11 broozer kernel: [    9.786724] hub 3-0:1.0: 2 ports detected
Sep 10 21:55:11 broozer kernel: [    9.890456] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Sep 10 21:55:11 broozer kernel: [    9.890473] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep 10 21:55:11 broozer kernel: [    9.890494] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Sep 10 21:55:11 broozer kernel: [    9.890525] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
Sep 10 21:55:11 broozer kernel: [    9.890623] usb usb4: configuration #1 chosen from 1 choice
Sep 10 21:55:11 broozer kernel: [    9.890642] hub 4-0:1.0: USB hub found
Sep 10 21:55:11 broozer kernel: [    9.890647] hub 4-0:1.0: 2 ports detected
Sep 10 21:55:11 broozer kernel: [    9.994589] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:55:11 broozer kernel: [    9.994607] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 10 21:55:11 broozer kernel: [    9.994629] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Sep 10 21:55:11 broozer kernel: [    9.998544] ehci_hcd 0000:00:1d.7: debug port 1
Sep 10 21:55:11 broozer kernel: [    9.998556] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
Sep 10 21:55:11 broozer kernel: [   10.014311] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 10 21:55:11 broozer kernel: [   10.014405] usb usb5: configuration #1 chosen from 1 choice
Sep 10 21:55:11 broozer kernel: [   10.014426] hub 5-0:1.0: USB hub found
Sep 10 21:55:11 broozer kernel: [   10.014431] hub 5-0:1.0: 8 ports detected
Sep 10 21:55:11 broozer kernel: [   10.119679] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:55:11 broozer kernel: [   10.172396] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 10 21:55:11 broozer kernel: [   10.193264] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Sep 10 21:55:11 broozer kernel: [   10.210195] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Sep 10 21:55:11 broozer kernel: [   10.210202] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Sep 10 21:55:11 broozer kernel: [   10.210208] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Sep 10 21:55:11 broozer kernel: [   10.250194] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Sep 10 21:55:11 broozer kernel: [   10.250211] b44.c:v2.0
Sep 10 21:55:11 broozer kernel: [   10.250250] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:55:11 broozer kernel: [   10.250291] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 10 21:55:11 broozer kernel: [   10.270433] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:e0:6d:16
Sep 10 21:55:11 broozer kernel: [   10.278182] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep 10 21:55:11 broozer kernel: [   10.362094] Clocksource tsc unstable (delta = -11695523458 ns)
Sep 10 21:55:11 broozer kernel: [   10.366269] Time: hpet clocksource has been installed.
Sep 10 21:55:11 broozer kernel: [   10.368461] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:55:11 broozer kernel: [   10.368639] scsi0 : ata_piix
Sep 10 21:55:11 broozer kernel: [   10.368774] scsi1 : ata_piix
Sep 10 21:55:11 broozer kernel: [   10.368906] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Sep 10 21:55:11 broozer kernel: [   10.368909] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Sep 10 21:55:11 broozer kernel: [   10.374517] ata1.00: ATA-6: WDC WD400VE-75HDT0, 09.07D09, max UDMA/100
Sep 10 21:55:11 broozer kernel: [   10.374521] ata1.00: 78140160 sectors, multi 8: LBA 
Sep 10 21:55:11 broozer kernel: [   10.374523] ata1.00: applying bridge limits
Sep 10 21:55:11 broozer kernel: [   10.375516] ata1.00: configured for UDMA/100
Sep 10 21:55:11 broozer kernel: [   10.384498] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B101, max UDMA/33
Sep 10 21:55:11 broozer kernel: [   10.388928] ata2.00: configured for UDMA/33
Sep 10 21:55:11 broozer kernel: [   10.389026] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400VE-75HD 09.0 PQ: 0 ANSI: 5
Sep 10 21:55:11 broozer kernel: [   10.389614] scsi 1:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B101 PQ: 0 ANSI: 5
Sep 10 21:55:11 broozer kernel: [   10.400446] Driver 'sd' needs updating - please use bus_type methods
Sep 10 21:55:11 broozer kernel: [   10.400525] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 21:55:11 broozer kernel: [   10.400535] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 21:55:11 broozer kernel: [   10.400551] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 21:55:11 broozer kernel: [   10.400590] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Sep 10 21:55:11 broozer kernel: [   10.400598] sd 0:0:0:0: [sda] Write Protect is off
Sep 10 21:55:11 broozer kernel: [   10.400613] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 10 21:55:11 broozer kernel: [   10.400616]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep 10 21:55:11 broozer kernel: [   10.425137]  sda1 sda2 < sda5 >
Sep 10 21:55:11 broozer kernel: [   10.425950] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 10 21:55:11 broozer kernel: [   10.431056] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 10 21:55:11 broozer kernel: [   10.431073] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep 10 21:55:11 broozer kernel: [   10.446789] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep 10 21:55:11 broozer kernel: [   10.446794] Uniform CD-ROM driver Revision: 3.20
Sep 10 21:55:11 broozer kernel: [   10.509502] Attempting manual resume
Sep 10 21:55:11 broozer kernel: [   10.522236] kjournald starting.  Commit interval 5 seconds
Sep 10 21:55:11 broozer kernel: [   10.522246] EXT3-fs: mounted filesystem with ordered data mode.
Sep 10 21:55:11 broozer kernel: [   12.531800] Linux agpgart interface v0.102
Sep 10 21:55:11 broozer kernel: [   12.610511] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 10 21:55:11 broozer kernel: [   12.659799] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 10 21:55:11 broozer kernel: [   12.956170] ACPI: AC Adapter [AC] (on-line)
Sep 10 21:55:11 broozer kernel: [   13.382540] ACPI: Battery Slot [BAT0] (battery present)
Sep 10 21:55:11 broozer kernel: [   13.382595] input: Lid Switch as /devices/virtual/input/input2
Sep 10 21:55:11 broozer kernel: [   13.383139] ACPI: Lid Switch [LID]
Sep 10 21:55:11 broozer kernel: [   13.383178] input: Power Button (CM) as /devices/virtual/input/input3
Sep 10 21:55:11 broozer kernel: [   13.395257] ACPI: Power Button (CM) [PBTN]
Sep 10 21:55:11 broozer kernel: [   13.395302] input: Sleep Button (CM) as /devices/virtual/input/input4
Sep 10 21:55:11 broozer kernel: [   13.407257] ACPI: Sleep Button (CM) [SBTN]
Sep 10 21:55:11 broozer kernel: [   13.599839] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
Sep 10 21:55:11 broozer kernel: [   13.727846] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17
Sep 10 21:55:11 broozer kernel: [   13.727851] Socket status: 30000006
Sep 10 21:55:11 broozer kernel: [   13.727853] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Sep 10 21:55:11 broozer kernel: [   13.727858] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
Sep 10 21:55:11 broozer kernel: [   14.439322] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input5
Sep 10 21:55:11 broozer kernel: [   14.450617] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Sep 10 21:55:11 broozer kernel: [   14.562641] sdhci: Secure Digital Host Controller Interface driver
Sep 10 21:55:11 broozer kernel: [   14.562644] sdhci: Copyright(c) Pierre Ossman
Sep 10 21:55:11 broozer kernel: [   14.562708] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
Sep 10 21:55:11 broozer kernel: [   14.562728] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:55:11 broozer kernel: [   14.562794] mmc0: SDHCI at 0xdfcfc700 irq 18 DMA
Sep 10 21:55:11 broozer kernel: [   14.658499] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep 10 21:55:11 broozer kernel: [   14.658503] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep 10 21:55:11 broozer kernel: [   14.765926] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Sep 10 21:55:11 broozer kernel: [   14.765930] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Sep 10 21:55:11 broozer kernel: [   14.766038] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Sep 10 21:55:11 broozer kernel: [   14.809190] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Sep 10 21:55:11 broozer kernel: [   15.167096] input: PC Speaker as /devices/platform/pcspkr/input/input6
Sep 10 21:55:11 broozer kernel: [   15.214169] iTCO_vendor_support: vendor-support=0
Sep 10 21:55:11 broozer kernel: [   15.238671] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep 10 21:55:11 broozer kernel: [   15.467060] input: PS/2 Mouse as /devices/virtual/input/input7
Sep 10 21:55:11 broozer kernel: [   15.499837] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Sep 10 21:55:11 broozer kernel: [   15.513591] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
Sep 10 21:55:11 broozer kernel: [   15.513623] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep 10 21:55:11 broozer kernel: [   15.674726] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep 10 21:55:11 broozer kernel: [   16.822780] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Sep 10 21:55:11 broozer kernel: [   16.822828] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:55:11 broozer kernel: [   16.827894] cs: IO port probe 0x100-0x3af: clean.
Sep 10 21:55:11 broozer kernel: [   16.829582] cs: IO port probe 0x3e0-0x4ff: clean.
Sep 10 21:55:11 broozer kernel: [   16.830283] cs: IO port probe 0x820-0x8ff: clean.
Sep 10 21:55:11 broozer kernel: [   16.830866] cs: IO port probe 0xc00-0xcf7: clean.
Sep 10 21:55:11 broozer kernel: [   16.831587] cs: IO port probe 0xa00-0xaff: clean.
Sep 10 21:55:11 broozer kernel: [   16.875708] intel8x0_measure_ac97_clock: measured 55397 usecs
Sep 10 21:55:11 broozer kernel: [   16.875711] intel8x0: clocking to 48000
Sep 10 21:55:11 broozer kernel: [   16.974541] lp: driver loaded but no devices found
Sep 10 21:55:11 broozer kernel: [   17.126024] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
Sep 10 21:55:11 broozer kernel: [   17.201339] EXT3 FS on sda1, internal journal
Sep 10 21:55:11 broozer kernel: [   17.507270] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 10 21:55:11 broozer kernel: [   17.689897] No dock devices found.
Sep 10 21:55:12 broozer kernel: [   18.304013] apm: BIOS not found.
Sep 10 21:55:12 broozer kernel: [   18.360819] ppdev: user-space parallel port driver
Sep 10 21:55:12 broozer kernel: [   18.375160] audit(1252644912.567:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4900 profile="/usr/sbin/cupsd" namespace="default"
Sep 10 21:55:12 broozer dhcdbd: Started up.
Sep 10 21:55:12 broozer kernel: [   46.129857] Marking TSC unstable due to: cpufreq changes.
Sep 10 21:55:13 broozer kernel: [   23.764828] Bluetooth: Core ver 2.11
Sep 10 21:55:13 broozer kernel: [   23.765353] NET: Registered protocol family 31
Sep 10 21:55:13 broozer kernel: [   23.765356] Bluetooth: HCI device and connection manager initialized
Sep 10 21:55:13 broozer kernel: [   23.765360] Bluetooth: HCI socket layer initialized
Sep 10 21:55:13 broozer kernel: [   23.795379] Bluetooth: L2CAP ver 2.9
Sep 10 21:55:13 broozer kernel: [   23.795384] Bluetooth: L2CAP socket layer initialized
Sep 10 21:55:13 broozer kernel: [   19.084786] Bluetooth: RFCOMM socket layer initialized
Sep 10 21:55:13 broozer kernel: [   19.084928] Bluetooth: RFCOMM TTY layer initialized
Sep 10 21:55:13 broozer kernel: [   19.084931] Bluetooth: RFCOMM ver 1.8
Sep 10 21:55:16 broozer kernel: [   19.395113] [drm] Initialized drm 1.1.0 20060810
Sep 10 21:55:16 broozer kernel: [   19.399294] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep 10 21:55:16 broozer kernel: [   19.399367] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Sep 10 21:55:19 broozer kernel: [   48.948224] [drm] Setting GART location based on new memory map
Sep 10 21:55:19 broozer kernel: [   48.949619] [drm] Loading R300 Microcode
Sep 10 21:55:19 broozer kernel: [   48.949668] [drm] writeback test succeeded in 1 usecs
Sep 10 21:55:52 broozer kernel: [   54.648824] NET: Registered protocol family 10
Sep 10 21:55:52 broozer kernel: [   54.649626] lo: Disabled Privacy Extensions
Sep 10 21:55:52 broozer kernel: [   54.651549] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 10 21:56:03 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep 10 21:56:06 broozer kernel: [   26.023029] NET: Registered protocol family 17
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
```

---

### Post by earthpigg on 2009-09-11
```
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep 10 21:56:12 broozer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
```

well, that's the pattern.

google says this is a bug with older versions of ubuntu.

have you been doing in-place upgrades for years and years instead of fresh installs every release or two?

sometimes in-place upgrades can leave old bugs in place.

---

### Post by HankTorrents on 2009-09-11
I am using 8.04, tried 9.01 but didnt like it. did weird things with the volume and few other things do you think if I upgraded to 8.10 it will be better?

---

### Post by P4man on 2009-09-11
I see this in your logs:

> Sep  9 22:32:51 broozer kernel: [ 2226.990782] ACPI: Critical trip point

Looks like your cpu is overheating and the system is shutting down to prevent damage. Can you tell if your cpu fan is running at all? I know one some machines there was a problem with gutsy and/or hardy and cpu fans not running (resulting in overheating).

---

### Post by earthpigg on 2009-09-11
> **P4man said:**
> I see this in your logs:



Looks like your cpu is overheating and the system is shutting down to prevent damage. Can you tell if your cpu fan is running at all? I know one some machines there was a problem with gutsy and/or hardy and cpu fans not running (resulting in overheating).

good catch, p4man.

to install lm-sensors, which *may or may not* give useful hardware readouts, depending on your motherboard:
```
sudo apt-get install lm-sensors
```

to configure it:
```
sudo sensors-detect
```

to give us something to work with:
```
sensors
```


post output of the final command, assuming it runs.


also, open your case and look inside with your computer turned on. 

are the fans running? if not, thats your problem.

is there a bunch of dust all over the place? if so, that is your problem.

---

### Post by P4man on 2009-09-11
> **earthpigg said:**
> 

also, open your case and look inside with your computer turned on. 


A dell inspiron is a laptop. Asking him to open the case might be stretching it. Although its a relatively old machine, and it might not be a bad idea to open it to clean the fans.

---

### Post by HankTorrents on 2009-09-11
Actually I have no issue opening up the laptop, and I was thinking of doing it to clear out dust balls in it. I have hardware experince from my computer classes back in high school, wroking at CompUSA and Geeksquad. I am just getting us to using ubuntu all the time and it commands, though I am building up a list of commands that I enjoy using in the terminal. Anyways long story short I am sticking with Linux from now on haha.

---

### Post by HankTorrents on 2009-09-12
Ok so I took it apart and man were the fans and sinks clogged.cleaned them out and seems to sound better also here is the out put
Though it doesnt look like it has the sensors needed




```
Next adapter: SMBus I801 adapter at 10c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x1d01
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

```

---

