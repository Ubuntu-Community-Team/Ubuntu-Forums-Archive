---
title: "sudden unasked-for  logout"
date: 2009-08-15
forum: General Help
---

### Post by bigred1 on 2009-08-15
I just upgraded to Jaunty (from 8.04 through 8.10 to 9.04).

Every five-10 minutes as I work, the system  suddenly logs out without my asking for it. I did not do anything such as pressing a key to log me out; in one case I was clicking the Firefox launch icon; in another I was dragging the Firefox scrollbar; in another I was clickning the minimized-app icon for Rhythmbox to restore it.

I can then log in with my password, but of course all my apps have been shut down; and it is a real bother to have this happen while you are working.

Help! I can't work with a computer that suddenly logs me out. Any ideas?

(By the way, in a perhaps-unrelated phenomenon, the "Shutdown" button (icon of green running person) no longer offers an option to shut down. Instead, there is an option to log out and I can shut down from the logged-out window. This is a hassle, but a small one compared to the above. I don't know if it is related. It began happening during the intermediate stage of upgrade, when I was at 8.10, and is still present now as I use 9.04.)

---

### Post by blueridgedog on 2009-08-15
Perhaps you can find some error reporting in the logs that can help out.  Can you post the output of:

```
dmesg
```

and

```
tail /var/log/messages
```

You should capture these as soon as you can, so any error resulting in the forced end of your session can be seen.  It may provide a clue.

---

### Post by CatKiller on 2009-08-16
I don't think you're being logged out. I think X is crashing. When X restarts it will take you to the login screen.

---

### Post by jdemarco on 2009-08-16
> **CatKiller said:**
> I don't think you're being logged out. I think X is crashing. When X restarts it will take you to the login screen.

Agreed.

I had the same problem and it turned out to be firefox. In my case X would just hang for a bit, and then crash. I recommend purging firefox, and reinstall.

---

### Post by bigred1 on 2009-08-16
> **blueridgedog said:**
>  Can you post the output of dmesg and
tail /var/log/messages  You should capture these as soon as you can, so any error resulting in the forced end of your session can be seen.  It may provide a clue.

Thanks, here are the outputs, right after three crashes in three minutes:

*tail /var/log/messages*
```
Aug 16 23:43:41 fox-desktop kernel: [ 6351.459444] r8169: eth0: link up
Aug 16 23:43:41 fox-desktop kernel: [ 6351.459451] r8169: eth0: link up
Aug 16 23:43:41 fox-desktop kernel: [ 6351.868373] NET: Registered protocol family 17
Aug 16 23:43:45 fox-desktop pulseaudio[6040]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Aug 16 20:47:02 fox-desktop pulseaudio[6522]: pid.c: Stale PID file, overwriting.
Aug 16 20:47:02 fox-desktop pulseaudio[6522]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Aug 16 20:48:26 fox-desktop pulseaudio[6867]: pid.c: Stale PID file, overwriting.
Aug 16 20:48:26 fox-desktop pulseaudio[6867]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Aug 16 20:48:55 fox-desktop pulseaudio[7171]: pid.c: Stale PID file, overwriting.
Aug 16 20:48:55 fox-desktop pulseaudio[7171]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
```

*dmesg*
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f216000 (usable)
[    0.000000]  BIOS-e820: 000000007f216000 - 000000007f259000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f259000 - 000000007f331000 (reserved)
[    0.000000]  BIOS-e820: 000000007f331000 - 000000007f334000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f334000 - 000000007f3e0000 (reserved)
[    0.000000]  BIOS-e820: 000000007f3e0000 - 000000007f3e6000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f3e6000 - 000000007f3e7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f3e7000 - 000000007f3e9000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f3e9000 - 000000007f3ea000 (reserved)
[    0.000000]  BIOS-e820: 000000007f3ea000 - 000000007f3f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f3f0000 - 000000007f400000 (reserved)
[    0.000000]  BIOS-e820: 000000007f400000 - 000000007f600000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fd310
[    0.000000] Entering add_active_range(0, 0, 521728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521728
[    0.000000] On node 0 totalpages: 521728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290068 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F03C0 checksum 0
[    0.000000] ACPI: RSDP 000F03C0, 0024 (r2  INTEL)
[    0.000000] ACPI: XSDT 7F3E7F10, 0044 (r1  INTEL   DG31PR  6222004 MSFT    10013)
[    0.000000] ACPI: FACP 7F3E5D90, 00F4 (r4  INTEL   DG31PR  6222004 MSFT    10013)
[    0.000000] ACPI: DSDT 7F3E0010, 49ED (r1  INTEL   DG31PR        0 INTL 20051117)
[    0.000000] ACPI: FACS 7F3E6E40, 0040
[    0.000000] ACPI: APIC 7F3E5F10, 006C (r2  INTEL   DG31PR  6222004 MSFT    10013)
[    0.000000] ACPI: HPET 7F3EED10, 0038 (r1  INTEL ICH7HPET  6222004 AMI.        1)
[    0.000000] ACPI: MCFG 7F3EEC10, 003C (r1 INTEL  DG31PR    6222004 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f600000:7f71c000)
[    0.000000] Built 1 zonelists.  Total pages: 517652
[    0.000000] Kernel command line: root=UUID=6901508c-5eab-4aef-af3d-8a66b745d79a ro single
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1599.999 MHz processor.
[   18.599198] Console: colour VGA+ 80x25
[   18.602398] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.602723] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.698305] Memory: 2055560k/2086912k available (2015k kernel code, 28120k reserved, 915k data, 364k init, 1167448k highmem)
[   18.698397] virtual kernel memory layout:
[   18.698398]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.698399]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.698400]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.698402]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.698403]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   18.698404]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   18.698405]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   18.698810] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.698942] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.699162] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   18.699300] hpet0: 3 64-bit timers, 14318180 Hz
[   18.780361] Calibrating delay using timer specific routine.. 3202.45 BogoMIPS (lpj=6404907)
[   18.780480] Security Framework v1.0.0 initialized
[   18.780535] SELinux:  Disabled at boot.
[   18.780594] Mount-cache hash table entries: 512
[   18.780770] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   18.780777] monitor/mwait feature present.
[   18.780827] using mwait in idle threads.
[   18.780878] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.780950] CPU: L2 cache: 1024K
[   18.780997] CPU: Physical Processor ID: 0
[   18.781045] CPU: Processor Core ID: 0
[   18.781093] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   18.781102] Compat vDSO mapped to ffffe000.
[   18.781162] Checking 'hlt' instruction... OK.
[   18.796524] SMP alternatives: switching to UP code
[   18.796989] Early unpacking initramfs... done
[   19.138646] ACPI: Core revision 20070126
[   19.138736] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.141013] CPU0: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   19.141125] SMP alternatives: switching to SMP code
[   19.141252] Booting processor 1/1 eip 3000
[   19.151400] Initializing CPU#1
[   19.228344] Calibrating delay using timer specific routine.. 3199.93 BogoMIPS (lpj=6399875)
[   19.228351] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   19.228356] monitor/mwait feature present.
[   19.228358] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.228360] CPU: L2 cache: 1024K
[   19.228363] CPU: Physical Processor ID: 0
[   19.228364] CPU: Processor Core ID: 1
[   19.228366] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   19.228845] CPU1: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   19.229312] Total of 2 processors activated (6402.39 BogoMIPS).
[   19.229507] ENABLING IO-APIC IRQs
[   19.229724] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.376427] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.396516] Brought up 2 CPUs
[   19.501267] migration_cost=65
[   19.501487] Booting paravirtualized kernel on bare hardware
[   19.501595] Time: 18:58:09  Date: 07/16/109
[   19.501663] NET: Registered protocol family 16
[   19.501792] EISA bus registered
[   19.501841] ACPI: bus type pci registered
[   19.513726] PCI: Using configuration type 1
[   19.513775] Setting up standard PCI resources
[   19.521760] ACPI: EC: Look up EC in DSDT
[   19.525032] ACPI: Interpreter enabled
[   19.525083] ACPI: (supports S0 S1 S3 S4 S5)
[   19.525272] ACPI: Using IOAPIC for interrupt routing
[   19.525836] ACPI: System BIOS is requesting _OSI(Linux)
[   19.525888] ACPI: Please test with "acpi_osi=!Linux"
[   19.525889] Please send dmidecode to linux-acpi@vger.kernel.org
[   19.532298] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.532408] PCI: Probing PCI hardware (bus 00)
[   19.532961] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   19.533018] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   19.533582] PCI: Transparent bridge - 0000:00:1e.0
[   19.533686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.533826] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   19.533937] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   19.534018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   19.537081] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   19.537499] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.537913] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   19.538329] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   19.538743] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[   19.539196] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[   19.539649] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[   19.540102] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   19.540559] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.540620] pnp: PnP ACPI init
[   19.540673] ACPI: bus type pnp registered
[   19.543500] pnp: PnP ACPI: found 14 devices
[   19.543551] ACPI: ACPI bus type pnp unregistered
[   19.543603] PnPBIOS: Disabled by ACPI PNP
[   19.543698] PCI: Using ACPI for IRQ routing
[   19.543748] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.543896] NET: Registered protocol family 8
[   19.543946] NET: Registered protocol family 20
[   19.544053] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   19.544110] pnp: 00:01: iomem range 0xe0000000-0xe3ffffff has been reserved
[   19.544172] pnp: 00:02: ioport range 0x400-0x47f has been reserved
[   19.544227] pnp: 00:02: ioport range 0x1180-0x119f has been reserved
[   19.544282] pnp: 00:02: ioport range 0x500-0x53f has been reserved
[   19.544337] pnp: 00:02: iomem range 0xfec00000-0xfecfffff has been reserved
[   19.544395] Time: tsc clocksource has been installed.
[   19.544452] Switched to high resolution mode on CPU 0
[   19.544507] Switched to high resolution mode on CPU 1
[   19.544541] pnp: 00:02: iomem range 0xfee00000-0xfee0ffff has been reserved
[   19.544545] pnp: 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   19.544548] pnp: 00:02: iomem range 0xffb00000-0xffcfffff could not be reserved
[   19.544553] pnp: 00:03: ioport range 0x290-0x29f has been reserved
[   19.574872] PCI: Bridge: 0000:00:01.0
[   19.574921]   IO window: disabled.
[   19.574970]   MEM window: disabled.
[   19.575018]   PREFETCH window: disabled.
[   19.575068] PCI: Bridge: 0000:00:1c.0
[   19.575116]   IO window: disabled.
[   19.575165]   MEM window: disabled.
[   19.575214]   PREFETCH window: disabled.
[   19.575265] PCI: Bridge: 0000:00:1c.1
[   19.575314]   IO window: d000-dfff
[   19.575364]   MEM window: fea00000-feafffff
[   19.575414]   PREFETCH window: disabled.
[   19.575465] PCI: Bridge: 0000:00:1e.0
[   19.575512]   IO window: disabled.
[   19.575562]   MEM window: disabled.
[   19.575611]   PREFETCH window: disabled.
[   19.575673] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.575771] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.575788] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.575885] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.575904] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.576722] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.576732] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.576744] NET: Registered protocol family 2
[   19.628396] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.628520] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   19.629403] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.629785] TCP: Hash tables configured (established 131072 bind 65536)
[   19.629841] TCP reno registered
[   19.644540] checking if image is initramfs... it is
[   20.318261] Freeing initrd memory: 7062k freed
[   20.318883] audit: initializing netlink socket (disabled)
[   20.318948] audit(1250449089.220:1): initialized
[   20.319087] highmem bounce pool size: 64 pages
[   20.321051] VFS: Disk quotas dquot_6.5.1
[   20.321147] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.321289] io scheduler noop registered
[   20.321338] io scheduler anticipatory registered
[   20.321388] io scheduler deadline registered
[   20.321450] io scheduler cfq registered (default)
[   20.321514] Boot video device is 0000:00:02.0
[   20.321760] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.321797] assign_interrupt_mode Found MSI capability
[   20.321850] Allocate Port Service[0000:00:01.0:pcie00]
[   20.321927] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.321967] assign_interrupt_mode Found MSI capability
[   20.322019] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.322049] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.322126] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.322166] assign_interrupt_mode Found MSI capability
[   20.322218] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.322251] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.322387] isapnp: Scanning for PnP cards...
[   20.676189] isapnp: No Plug & Play device found
[   20.697657] Real Time Clock Driver v1.12ac
[   20.697900] hpet_resources: 0xfed00000 is busy
[   20.697922] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.698088] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.698746] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.699522] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.699716] input: Macintosh mouse button emulation as /class/input/input0
[   20.699851] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[   20.702219] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.702273] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.702492] mice: PS/2 mouse device common for all mice
[   20.702647] EISA: Probing bus 0 at eisa.0
[   20.702723] EISA: Detected 0 cards.
[   20.702850] TCP cubic registered
[   20.702908] NET: Registered protocol family 1
[   20.702975] Using IPI No-Shortcut mode
[   20.703171]   Magic number: 5:566:999
[   20.703230]   hash matches device ttyaf
[   20.703346]   hash matches device 00:01
[   20.703394]   hash matches device pnp0
[   20.703586] Freeing unused kernel memory: 364k freed
[   20.736366] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.904594] AppArmor: AppArmor initialized<5>audit(1250449089.720:2):  type=1505 info="AppArmor initialized" pid=1200
[   20.911032] fuse init (API version 7.8)
[   20.915838] Failure registering capabilities with primary security module.
[   20.953589] ACPI: SSDT 7F3EB590, 04EC (r1    AMI      IST        1 MSFT  3000001)
[   20.954105] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.954234] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.954363] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.954490] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.954618] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.954746] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.434739] SCSI subsystem initialized
[   21.439671] libata version 2.21 loaded.
[   21.441217] ata_piix 0000:00:1f.1: version 2.11
[   21.441232] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   21.441361] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.441431] scsi0 : ata_piix
[   21.441518] scsi1 : ata_piix
[   21.441666] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001e0f0 irq 14
[   21.441743] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001e0f8 irq 15
[   21.495789] usbcore: registered new interface driver usbfs
[   21.495873] usbcore: registered new interface driver hub
[   21.495953] usbcore: registered new device driver usb
[   21.496862] USB Universal Host Controller Interface driver v3.0
[   21.544080] FDC 0 is a post-1991 82077
[   21.768507] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-H44N, RB01, max UDMA/66
[   21.768739] ata1.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[   21.768799] ata1.01: 160086528 sectors, multi 16: LBA 
[   21.768862] ata1.00: limited to UDMA/33 due to 40-wire cable
[   21.768915] ata1.01: limited to UDMA/33 due to 40-wire cable
[   21.940495] ata1.00: configured for UDMA/33
[   21.956668] ata1.01: configured for UDMA/33
[   21.956750] ata2: port disabled. ignoring.
[   21.960151] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H44N  RB01 PQ: 0 ANSI: 5
[   21.960629] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   21.960979] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   21.961156] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   21.961279] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.961316] scsi2 : ata_piix
[   21.961518] scsi3 : ata_piix
[   21.961707] ata3: SATA max UDMA/133 cmd 0x0001e0e0 ctl 0x0001e0d2 bmdma 0x0001e0a0 irq 17
[   21.961784] ata4: SATA max UDMA/133 cmd 0x0001e0c0 ctl 0x0001e0b2 bmdma 0x0001e0a8 irq 17
[   22.136355] ata3.00: ATA-7: WDC WD1600AAJS-22PSA0, 05.06H05, max UDMA/133
[   22.136418] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   22.153390] ata3.00: configured for UDMA/133
[   22.318993] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-2 05.0 PQ: 0 ANSI: 5
[   22.319443] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   22.319553] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.319557] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.319728] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   22.319835] ehci_hcd 0000:00:1d.7: debug port 1
[   22.319890] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   22.319903] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfeb84000
[   22.323859] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.324042] usb usb1: configuration #1 chosen from 1 choice
[   22.324125] hub 1-0:1.0: USB hub found
[   22.324180] hub 1-0:1.0: 8 ports detected
[   22.428469] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   22.428582] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.428586] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.428670] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   22.428773] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000e080
[   22.428927] usb usb2: configuration #1 chosen from 1 choice
[   22.429006] hub 2-0:1.0: USB hub found
[   22.429060] hub 2-0:1.0: 2 ports detected
[   22.532353] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   22.532471] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.532475] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.532555] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   22.532657] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[   22.532801] usb usb3: configuration #1 chosen from 1 choice
[   22.532879] hub 3-0:1.0: USB hub found
[   22.532933] hub 3-0:1.0: 2 ports detected
[   22.636338] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   22.636451] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.636454] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.636534] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   22.636635] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e040
[   22.636790] usb usb4: configuration #1 chosen from 1 choice
[   22.636867] hub 4-0:1.0: USB hub found
[   22.636921] hub 4-0:1.0: 2 ports detected
[   22.740322] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   22.740436] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.740439] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.740514] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   22.740613] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e020
[   22.740760] usb usb5: configuration #1 chosen from 1 choice
[   22.740842] hub 5-0:1.0: USB hub found
[   22.740895] hub 5-0:1.0: 2 ports detected
[   22.844440] r8169 Gigabit Ethernet driver 2.2LK loaded
[   22.844515] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.844628] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   22.844826] eth0: RTL8168b/8111b at 0xf8852000, 00:1c:c0:10:11:33, XID 38500000 IRQ 17
[   22.876247] sd 0:0:1:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   22.877294] sd 0:0:1:0: [sda] Write Protect is off
[   22.877356] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   22.890634] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.895606] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   22.895688] Uniform CD-ROM driver Revision: 3.20
[   22.895785] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   22.895794] sd 0:0:1:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   22.895867] sd 0:0:1:0: [sda] Write Protect is off
[   22.895921] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   22.895937] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.896017]  sda: sda1
[   22.905368] sd 0:0:1:0: [sda] Attached SCSI disk
[   22.906296] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   22.906362] sd 2:0:0:0: [sdb] Write Protect is off
[   22.906413] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.906429] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.906543] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   22.906607] sd 2:0:0:0: [sdb] Write Protect is off
[   22.906658] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.906673] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.906751]  sdb: sdb1 sdb2 < sdb5 >
[   22.933675] sd 2:0:0:0: [sdb] Attached SCSI disk
[   22.937760] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   22.937838] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   22.937916] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   23.221839] Attempting manual resume
[   23.221888] swsusp: Resume From Partition 8:21
[   23.221890] PM: Checking swsusp image.
[   23.222080] PM: Resume from disk failed.
[   23.236192] EXT3-fs: INFO: recovery required on readonly filesystem.
[   23.236252] EXT3-fs: write access will be enabled during recovery.
[   23.332225] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   23.510938] usb 2-1: configuration #1 chosen from 1 choice
[   23.752188] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   23.919832] usb 3-1: configuration #1 chosen from 1 choice
[   24.160123] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   24.342815] usb 3-2: configuration #1 chosen from 1 choice
[   24.355633] usbcore: registered new interface driver hiddev
[   24.370941] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   24.371055] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2
[   24.371208] usbcore: registered new interface driver usbhid
[   24.371268] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.544915] kjournald starting.  Commit interval 5 seconds
[   24.544926] EXT3-fs: recovery complete.
[   24.547112] EXT3-fs: mounted filesystem with ordered data mode.
[   32.772961] udev: starting version 141
[   32.773052] udev: deprecated sysfs layout; update the kernel or disable CONFIG_SYSFS_DEPRECATED; some udev features will not work correctly
[   33.516299] Linux video capture interface: v2.00
[   33.561993] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   33.562123] quickcam: Kernel:2.6.22-14-generic bus:3 class:FF subclass:FF vendor:046D product:0840
[   33.567628] quickcam: Sensor HDCS-1000/1100 detected
[   33.569542] quickcam: Registered device: /dev/video0
[   33.569659] usbcore: registered new interface driver quickcam
[   33.580692] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10C2
[   33.580827] usbcore: registered new interface driver usblp
[   33.580883] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   33.604802] Linux agpgart interface v0.102 (c) Dave Jones
[   33.632880] agpgart: Detected an Intel G33 Chipset.
[   33.633505] agpgart: Detected 7164K stolen memory.
[   33.647729] agpgart: AGP aperture is 256M @ 0xd0000000
[   33.666921] iTCO_vendor_support: vendor-support=0
[   33.668337] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   33.668474] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   33.668586] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.691519] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   33.691521]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   33.691523]  you are certain that your <4>intel_rng: system has a functional
[   33.691524]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   33.894886] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.895022] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.099558] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   34.348406] lp: driver loaded but no devices found
[   34.525989] Adding 6040400k swap on /dev/sdb5.  Priority:-1 extents:1 across:6040400k
[   34.908810] EXT3 FS on sdb1, internal journal
[   35.385439] audit(1250449104.220:3):  type=1505 operation="profile_load" info="unsupported interface version" pid=4280
[   35.442822] audit(1250449104.220:4):  type=1505 operation="profile_load" info="unsupported interface version" pid=4286
[   35.600769] audit(1250449104.720:5):  type=1505 operation="profile_load" info="unsupported interface version" pid=4293
[   35.635091] audit(1250449104.720:6):  type=1505 operation="profile_load" info="unsupported interface version" pid=4299
[ 6341.552542] No dock devices found.
[ 6341.571386] input: Power Button (FF) as /class/input/input3
[ 6341.571404] ACPI: Power Button (FF) [PWRF]
[ 6341.571504] input: Sleep Button (CM) as /class/input/input4
[ 6341.571522] ACPI: Sleep Button (CM) [SLPB]
[ 6341.571557] input: Power Button (CM) as /class/input/input5
[ 6341.571577] ACPI: Power Button (CM) [PWRB]
[ 6343.328598] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[ 6343.388899] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 6343.404205] NFSD: starting 90-second grace period
[ 6344.447961] NET: Registered protocol family 10
[ 6344.448069] lo: Disabled Privacy Extensions
[ 6346.337873] Bluetooth: Core ver 2.11
[ 6346.338229] NET: Registered protocol family 31
[ 6346.338233] Bluetooth: HCI device and connection manager initialized
[ 6346.338236] Bluetooth: HCI socket layer initialized
[ 6346.511205] Bluetooth: L2CAP ver 2.8
[ 6346.511210] Bluetooth: L2CAP socket layer initialized
[ 6346.649536] Bluetooth: SCO (Voice Link) ver 0.6
[ 6346.649541] Bluetooth: SCO socket layer initialized
[ 6346.708271] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[ 6346.708275] Bluetooth: BNEP filters: protocol multicast
[ 6346.722835] Bridge firewalling registered
[ 6347.174729] Failure registering capabilities with primary security module.
[ 6347.439363] ppdev: user-space parallel port driver
[ 6348.897278] [drm] Initialized drm 1.1.0 20060810
[ 6348.941292] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 6348.943913] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 6348.944499] [drm:i915_getparam] *ERROR* i915_getparam called with no initialization
[ 6349.412188] set status page addr 0x0012b000
[ 6349.950841] [drm:i915_getparam] *ERROR* Unknown parameter 5
[ 6351.459444] r8169: eth0: link up
[ 6351.459451] r8169: eth0: link up
[ 6351.868373] NET: Registered protocol family 17
[ 6362.114399] eth0: no IPv6 routers present
[ 6545.495507] [drm:i915_getparam] *ERROR* i915_getparam called with no initialization
[ 6545.755255] set status page addr 0x0012b000
[ 6545.791078] [drm:i915_getparam] *ERROR* Unknown parameter 5
[ 6628.256831] [drm:i915_getparam] *ERROR* i915_getparam called with no initialization
[ 6628.515992] set status page addr 0x0012b000
[ 6628.552197] [drm:i915_getparam] *ERROR* Unknown parameter 5
[ 6659.300139] [drm:i915_getparam] *ERROR* i915_getparam called with no initialization
[ 6659.559546] set status page addr 0x0012b000
[ 6659.595297] [drm:i915_getparam] *ERROR* Unknown parameter 5


```

---

### Post by bigred1 on 2009-08-16
> **CatKiller said:**
> I don't think you're being logged out. I think X is crashing. When X restarts it will take you to the login screen.

Thanks, that could well be. How can I determine if X crashed?

---

### Post by bigred1 on 2009-08-16
> **jdemarco said:**
> Agreed.

I had the same problem and it turned out to be firefox. In my case X would just hang for a bit, and then crash. I recommend purging firefox, and reinstall.

I uninstalled FF, Epiphany, and all Flash-related software. I am using Opera and Konqueror for the moment.

The problem still occurs, however.

---

### Post by bigred1 on 2009-08-16
I may have found the reason.

My old *menu.lst *was modified by the upgrade.

The old Hardy boot-entry was still default, and was being loaded instead of the new Jaunty entries. (I would not have thought this possible, since Hardy was presumably overwritten by Jaunty, but both kernels are actually at */boot*).

So now, I'll just have to see if the problem recurs.

---

### Post by bigred1 on 2009-11-19
And the [same problem occurred]("http://ubuntuforums.org/showthread.php?p=8349881#post8349881"), with the same solution, on the later upgrade to Karmic. 

Here is the [official Release Note]("http://www.ubuntu.com/getubuntu/releasenotes/910#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version").

---

### Post by larryk335 on 2010-05-08
I was watching youtube short and my monitor just went black. with the login screen displayed.  I logged in and I went on viewing  the video for another five minutes (est) then the screen just went black again.  I would really like anyone to tell me how to reset that timer.  I dont think my system crashed because as soon as I relogged in it took reight back to where I was.  Also I just upgraded to 10.4.  It has something to do with the new upgrade from 9.04

---

### Post by blueridgedog on 2010-05-08
There is nothing in the logs you posted to point to significant issue.  I think, like another suggested, that X (the window system) is crashing.  

I suggest troubleshooting it from that angle first.  Take a look at the standard document on the subject:

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

