---
title: "Connecting to the Internet with gNewSense"
date: 2010-09-27
forum: General Help
---

### Post by foxxxy on 2010-09-27
Hi guys, I'm having a problem connecting to the Internet on my gNewSense installation. My Internet works fine through Ubuntu and Windows, but not through gNewSense, is there anyway of fixing this? Thanks in advance.

---

### Post by foxxxy on 2010-09-27
I was looking around and somebody mentioned to type the command "dmesg" and paste the results, so here they are. 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-24-generic (root@sandbox) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Sep 10 19:00:20 UTC 2009 (Ubuntu 2.6.24-24.59gnewsense9-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7f0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000faa60
[    0.000000] Entering add_active_range(0, 0, 129008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   129008
[    0.000000]   HighMem    129008 ->   129008
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   129008
[    0.000000] On node 0 totalpages: 129008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00EA410 checksum 0
[    0.000000] ACPI: RSDP 000EA410, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 000E5E40, 007C (r1 COMPAQ CPQ0064  20030710             0)
[    0.000000] ACPI: FACP 000E5EF8, 0074 (r1 COMPAQ SPRINGD         1             0)
[    0.000000] ACPI: DSDT 000E6008, 0D7D (r1 COMPAQ     DSDT        1 MSFT  100000E)
[    0.000000] ACPI: FACS 000E5E00, 0040
[    0.000000] ACPI: SSDT 000E6D85, 05FE (r1 COMPAQ  PROJECT        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E7383, 053A (r1 COMPAQ CORE_PNP        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E78BD, 01F2 (r1 COMPAQ CORE_UTL        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E7AAF, 032E (r1 COMPAQ VILLTBL1        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E7DDD, 053F (r1 COMPAQ LGCYLITE        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E831C, 0167 (r1 COMPAQ    UART2        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E8483, 014E (r1 COMPAQ   FLOPPY        1 MSFT  100000E)
[    0.000000] ACPI: APIC 000E5F6C, 0068 (r1 COMPAQ SPRINGD         1             0)
[    0.000000] ACPI: SSDT 000EA16D, 00B2 (r1 COMPAQ     APIC        1 MSFT  100000E)
[    0.000000] ACPI: ASF! 000E5FD4, 0034 (r16 COMPAQ SPRINGD         1             0)
[    0.000000] ACPI: SSDT 000E8A3F, 040F (r1 COMPAQ PNP_PRSS        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E8E4E, 016D (r1 COMPAQ UR2_PRSS        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E8FBB, 0119 (r1 COMPAQ FPY_PRSS        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E9189, 0167 (r1 COMPAQ       S3        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E92F0, 00E3 (r1 COMPAQ  CORE_S3        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E93D3, 013E (r1 COMPAQ   PIDETM        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E9955, 016B (r1 COMPAQ     GTF0        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E9511, 0143 (r1 COMPAQ   SIDETM        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E9DA0, 0170 (r1 COMPAQ     GTF3        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000E9F10, 00F0 (r1 COMPAQ      L08        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 000EA371, 0054 (r1 COMPAQ    FINIS        1 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 128001
[    0.000000] Kernel command line: initrd=initrd.gz boot=casper quiet splash BOOT_IMAGE=vmlinuz 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2660.045 MHz processor.
[   17.333468] Console: colour VGA+ 80x25
[   17.333472] console [tty0] enabled
[   17.333795] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.334072] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.344039] Memory: 499708k/516032k available (2178k kernel code, 15672k reserved, 1013k data, 368k init, 0k highmem)
[   17.344048] virtual kernel memory layout:
[   17.344049]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.344050]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.344051]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   17.344052]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
[   17.344053]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   17.344054]       .data : 0xc03208e8 - 0xc041ddc4   (1013 kB)
[   17.344055]       .text : 0xc0100000 - 0xc03208e8   (2178 kB)
[   17.344058] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.344099] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.423926] Calibrating delay using timer specific routine.. 5324.95 BogoMIPS (lpj=10649912)
[   17.423954] Security Framework initialized
[   17.423962] SELinux:  Disabled at boot.
[   17.423977] AppArmor: AppArmor initialized
[   17.423981] Failure registering capabilities with primary security module.
[   17.423990] Mount-cache hash table entries: 512
[   17.424131] Initializing cgroup subsys ns
[   17.424135] Initializing cgroup subsys cpuacct
[   17.424147] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   17.424161] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   17.424163] CPU: L2 cache: 512K
[   17.424166] CPU: Hyper-Threading is disabled
[   17.424169] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043080 00004400 00000000 00000000 00000000
[   17.424181] Compat vDSO mapped to ffffe000.
[   17.424196] Checking 'hlt' instruction... OK.
[   17.440294] SMP alternatives: switching to UP code
[   17.441937] Freeing SMP alternatives: 11k freed
[   17.442087] Early unpacking initramfs... done
[   17.753120] ACPI: Core revision 20070126
[   17.753163] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.755587] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 07
[   17.755626] Total of 1 processors activated (5324.95 BogoMIPS).
[   17.755759] ENABLING IO-APIC IRQs
[   17.755936] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.902812] Brought up 1 CPUs
[   17.902833] CPU0 attaching sched-domain:
[   17.902836]  domain 0: span 01
[   17.902838]   groups: 01
[   17.903044] net_namespace: 64 bytes
[   17.903055] Booting paravirtualized kernel on bare hardware
[   17.903612] Time:  9:25:24  Date: 09/27/10
[   17.903640] NET: Registered protocol family 16
[   17.903881] EISA bus registered
[   17.903906] ACPI: bus type pci registered
[   17.904223] PCI: PCI BIOS revision 2.20 entry at 0xec5a9, last bus=5
[   17.904226] PCI: Using configuration type 1
[   17.904239] Setting up standard PCI resources
[   17.905629] ACPI: EC: Look up EC in DSDT
[   17.907014] ACPI: Interpreter enabled
[   17.907018] ACPI: (supports S0 S1 S3 S4 S5)
[   17.907033] ACPI: Using IOAPIC for interrupt routing
[   17.910693] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.911198] Force enabled HPET at base address 0xfed00000
[   17.911205] PCI: Enabled i801 SMBus device
[   17.911211] PCI quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[   17.911214] PCI quirk: region fa00-fa3f claimed by ICH4 GPIO
[   17.911584] PCI: Transparent bridge - 0000:00:1e.0
[   17.911605] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.911813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   17.917245] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[   17.917325] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
[   17.917403] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 14 15)
[   17.917481] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[   17.917559] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[   17.917637] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   17.917716] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   17.917795] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)
[   17.917952] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.917991] pnp: PnP ACPI init
[   17.918001] ACPI: bus type pnp registered
[   17.920476] pnp: PnP ACPI: found 14 devices
[   17.920480] ACPI: ACPI bus type pnp unregistered
[   17.920485] PnPBIOS: Disabled by ACPI PNP
[   17.920762] PCI: Using ACPI for IRQ routing
[   17.920766] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.978590] NET: Registered protocol family 8
[   17.978593] NET: Registered protocol family 20
[   17.978717] hpet clockevent registered
[   17.978722] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.978727] hpet0: 3 64-bit timers, 14318180 Hz
[   17.979771] AppArmor: AppArmor Filesystem Enabled
[   17.982569] Time: tsc clocksource has been installed.
[   17.990604] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   17.990612] system 00:0c: ioport range 0x400-0x41f has been reserved
[   17.990615] system 00:0c: ioport range 0x420-0x43f has been reserved
[   17.990618] system 00:0c: ioport range 0x440-0x45f has been reserved
[   17.990620] system 00:0c: ioport range 0x460-0x47f has been reserved
[   17.990623] system 00:0c: ioport range 0xf800-0xf81f has been reserved
[   17.990626] system 00:0c: ioport range 0xf820-0xf83f has been reserved
[   17.990628] system 00:0c: ioport range 0xf840-0xf85f has been reserved
[   17.990631] system 00:0c: ioport range 0xf860-0xf87f has been reserved
[   17.990634] system 00:0c: ioport range 0xfa00-0xfa3f has been reserved
[   17.990637] system 00:0c: ioport range 0xfc00-0xfc7f could not be reserved
[   17.990641] system 00:0c: ioport range 0xfc80-0xfcff has been reserved
[   17.990644] system 00:0c: ioport range 0xfe00-0xfe7f has been reserved
[   17.990646] system 00:0c: ioport range 0xfe80-0xfeff has been reserved
[   17.990660] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   17.990664] system 00:0d: iomem range 0x100000-0x1f7fffff could not be reserved
[   17.990666] system 00:0d: iomem range 0x1f800000-0x1f8fffff could not be reserved
[   17.990669] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   17.990672] system 00:0d: iomem range 0xfec01000-0xffffffff could not be reserved
[   17.990675] system 00:0d: iomem range 0xcc600-0xdffff has been reserved
[   18.021104] PCI: Bridge: 0000:00:1e.0
[   18.021107]   IO window: disabled.
[   18.021112]   MEM window: fc500000-fc7fffff
[   18.021116]   PREFETCH window: disabled.
[   18.021131] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.021144] NET: Registered protocol family 2
[   18.058473] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.058720] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   18.058800] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.058881] TCP: Hash tables configured (established 16384 bind 16384)
[   18.058883] TCP reno registered
[   18.070509] checking if image is initramfs... it is
[   18.481351] Switched to high resolution mode on CPU 0
[   18.675562] Freeing initrd memory: 7089k freed
[   18.676248] audit: initializing netlink socket (disabled)
[   18.676266] audit(1285579525.228:1): initialized
[   18.678652] VFS: Disk quotas dquot_6.5.1
[   18.678739] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.678907] io scheduler noop registered
[   18.678910] io scheduler anticipatory registered
[   18.678912] io scheduler deadline registered
[   18.678925] io scheduler cfq registered (default)
[   18.678940] Boot video device is 0000:00:02.0
[   18.679269] isapnp: Scanning for PnP cards...
[   19.032578] isapnp: No Plug & Play device found
[   19.066715] Real Time Clock Driver v1.12ac
[   19.066827] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.066957] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.067114] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.068191] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.069138] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.069219] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.069346] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   19.072056] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.072061] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.079890] mice: PS/2 mouse device common for all mice
[   19.080025] EISA: Probing bus 0 at eisa.0
[   19.080033] Cannot allocate resource for EISA slot 1
[   19.080063] EISA: Detected 0 cards.
[   19.080066] cpuidle: using governor ladder
[   19.080068] cpuidle: using governor menu
[   19.080176] NET: Registered protocol family 1
[   19.080210] Using IPI No-Shortcut mode
[   19.080250] registered taskstats version 1
[   19.080351]   Magic number: 10:375:425
[   19.080471] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.080472] EDD information not available.
[   19.080916] Freeing unused kernel memory: 368k freed
[   19.080941] Write protecting the kernel read-only data: 808k
[   19.111730] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.284150] fuse init (API version 7.9)
[   20.305825] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.305844] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.719691] usbcore: registered new interface driver usbfs
[   20.719721] usbcore: registered new interface driver hub
[   20.728116] usbcore: registered new device driver usb
[   20.739598] USB Universal Host Controller Interface driver v3.0
[   20.739682] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.739696] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.739700] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.740045] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.740076] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001440
[   20.740232] usb usb1: configuration #1 chosen from 1 choice
[   20.740265] hub 1-0:1.0: USB hub found
[   20.740272] hub 1-0:1.0: 2 ports detected
[   20.843438] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   20.843452] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.843457] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.843484] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.843512] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001460
[   20.843644] usb usb2: configuration #1 chosen from 1 choice
[   20.843672] hub 2-0:1.0: USB hub found
[   20.843679] hub 2-0:1.0: 2 ports detected
[   20.939337] SCSI subsystem initialized
[   20.949597] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.949614] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.949618] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.949650] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.949679] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001480
[   20.949808] usb usb3: configuration #1 chosen from 1 choice
[   20.949834] hub 3-0:1.0: USB hub found
[   20.949841] hub 3-0:1.0: 2 ports detected
[   20.987291] libata version 3.00 loaded.
[   21.051021] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   21.051038] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.051042] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.051083] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   21.054995] ehci_hcd 0000:00:1d.7: debug port 1
[   21.055002] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   21.055013] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc480000
[   21.082709] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   21.094679] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.094837] usb usb4: configuration #1 chosen from 1 choice
[   21.094865] hub 4-0:1.0: USB hub found
[   21.094874] hub 4-0:1.0: 8 ports detected
[   21.107499] Floppy drive(s): fd0 is 1.44M
[   21.128681] FDC 0 is a post-1991 82077
[   21.198624] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   21.198634] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   21.198693] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.198708] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   21.198721] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   21.198755] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.198765] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   21.207962] ata_piix 0000:00:1f.1: version 2.12
[   21.207984] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   21.208036] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.211369] scsi0 : ata_piix
[   21.212353] scsi1 : ata_piix
[   21.212550] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x14c0 irq 14
[   21.212553] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x14c8 irq 15
[   21.529945] ata1.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0D08, max UDMA/33
[   21.701180] hub 4-0:1.0: over-current change on port 7
[   21.701456] ata1.00: configured for UDMA/33
[   21.869416] ata2.01: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/100
[   21.869421] ata2.01: 78165360 sectors, multi 16: LBA 
[   21.884858] ata2.01: configured for UDMA/100
[   21.892628] end_request: I/O error, dev fd0, sector 0
[   21.894685] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0D08 PQ: 0 ANSI: 5
[   21.895236] scsi 1:0:1:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[   21.895312] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   22.044233] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   22.048238] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   22.048290] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   22.048353] scsi2 : ata_piix
[   22.048693] scsi3 : ata_piix
[   22.048735] ata3: SATA max UDMA/133 cmd 0x14f8 ctl 0x1810 bmdma 0x14d0 irq 18
[   22.048738] ata4: SATA max UDMA/133 cmd 0x1800 ctl 0x1814 bmdma 0x14d8 irq 18
[   22.216266] usb 1-1: configuration #1 chosen from 1 choice
[   22.392602] Driver 'sd' needs updating - please use bus_type methods
[   22.394568] sd 1:0:1:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   22.394585] sd 1:0:1:0: [sda] Write Protect is off
[   22.394588] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   22.394611] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.394672] sd 1:0:1:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   22.394685] sd 1:0:1:0: [sda] Write Protect is off
[   22.394688] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   22.394709] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.394714]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.402214] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   22.402221] Uniform CD-ROM driver Revision: 3.20
[   22.402289] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   22.455197] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   22.611378] usb 3-2: configuration #1 chosen from 1 choice
[   22.614480] usbcore: registered new interface driver hiddev
[   22.627336] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   22.638839] input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1
[   22.642279] input: Microsoft LifeChat LX-3000  as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.3/input/input3
[   22.654760] input,hidraw1: USB HID v1.00 Device [Microsoft LifeChat LX-3000 ] on usb-0000:00:1d.2-2
[   22.654783] usbcore: registered new interface driver usbhid
[   22.654788] /nfs/.sda3/gnewsense-builder-temp-dir/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.929989] end_request: I/O error, dev fd0, sector 0
[   23.098528]  sda1
[   23.098623] sd 1:0:1:0: [sda] Attached SCSI disk
[   23.110096] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   23.110120] sd 1:0:1:0: Attached scsi generic sg1 type 0
[   24.011235] end_request: I/O error, dev fd0, sector 0
[   24.460827] ISO 9660 Extensions: Microsoft Joliet Level 3
[   24.465088] ISO 9660 Extensions: RRIP_1991A
[   24.487078] loop: module loaded
[   24.592449] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   24.793122] Registering unionfs 1.4
[   24.793128] unionfs: debugging is not enabled
[   61.568300] Linux agpgart interface v0.102
[   61.727328] agpgart: Detected an Intel 865 Chipset.
[   61.727434] agpgart: Detected 8060K stolen memory.
[   61.774325] agpgart: AGP aperture is 128M @ 0xf0000000
[   61.975317] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.082145] input: Power Button (FF) as /devices/virtual/input/input4
[   62.094275] ACPI: Power Button (FF) [PWRF]
[   62.094434] input: Power Button (CM) as /devices/virtual/input/input5
[   62.110232] ACPI: Power Button (CM) [PBTN]
[   62.118312] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.972285] iTCO_vendor_support: vendor-support=0
[   63.004004] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   63.004154] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   63.004161] iTCO_wdt: No card detected
[   63.115716] intel_rng: Firmware space is locked read-only. If you can't or
[   63.115720] intel_rng: don't want to disable this in firmware setup, and if
[   63.115721] intel_rng: you are certain that your system has a functional
[   63.115722] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   64.261041] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   64.756431] parport_pc 00:07: reported by Plug and Play ACPI
[   64.756484] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   64.916373] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   64.916404] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   65.155077] usbcore: registered new interface driver snd-usb-audio
[   65.334176] intel8x0_measure_ac97_clock: measured 54866 usecs
[   65.334181] intel8x0: clocking to 48000
[   69.061747] ip_tables: (C) 2000-2006 Netfilter Core Team
[   71.476126] No dock devices found.
[   74.585306] apm: BIOS not found.
[   74.717190] lp0: using parport0 (interrupt-driven).
[   74.767851] ppdev: user-space parallel port driver
[   79.879662] Bluetooth: Core ver 2.11
[   79.880487] NET: Registered protocol family 31
[   79.880493] Bluetooth: HCI device and connection manager initialized
[   79.880498] Bluetooth: HCI socket layer initialized
[   79.933943] Bluetooth: L2CAP ver 2.9
[   79.933948] Bluetooth: L2CAP socket layer initialized
[   80.182121] Bluetooth: RFCOMM socket layer initialized
[   80.182396] Bluetooth: RFCOMM TTY layer initialized
[   80.182400] Bluetooth: RFCOMM ver 1.8
[   86.552018] [drm] Initialized drm 1.1.0 20060810
[   86.694814] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   86.694826] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   86.694919] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   99.507387] NET: Registered protocol family 10
[   99.507952] lo: Disabled Privacy Extensions


```

---

### Post by nikR on 2010-09-29
Try to reinstall driver for your network card

---

