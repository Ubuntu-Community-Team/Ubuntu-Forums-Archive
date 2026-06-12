---
title: "Ubuntu gone weird after monitor problem-urgent"
date: 2010-07-09
forum: General Help
---

### Post by satish_j on 2010-07-09
My monitor recently stopped working(H/W problem)..after getting it repaired,the ubuntu system is acting weird in the sense that after running for some time,it sort of freezes and does not allow to open any new applications.
On trying to open new application,the mouse curosr goes to busy mode and a new tab on task bar is displayed showing(starting '*App*'),but after some 10-15 sec,the bar is gone,mouse cursor back to its idle mode and the application is never opened.
REstarting the system takes it back to proper state,but after sometime-same prob..I cant open any application,not even system monitor to see whether cpu is being utilized to max.
Also,i have noticed one more thing on starting the system,i transferred 1 file(CUT FILE) from linux partition to windows partition and it got transferred successfully.After sometime,when the above prob came,i rebooted the system to see that the file is again present in Linux partition(And also windows parttion).THis is even after cutting the file and not copying.
SEriously and urgently seeking help on this???

---

### Post by hangfire on 2010-07-09
> **satish_j said:**
> My monitor recently stopped working(H/W problem)..after getting it repaired,the ubuntu system is acting weird in the sense that after running for some time,it sort of freezes and does not allow to open any new applications.

Something happened while your computer was being repaired. You've got some debugging work to do. Keep trying things until the problem goes away.

Basic debugging ideas, in no particular order:
1. Run memtest86+, it should be in your boot menu. Let it run a long time, like overnight.
2. Remove all USB devices. Try your mouse in a different USB port.
3. Unmount that windows partition.
4. Check for runaway processes with a console running the **top **command. Leave it running where you can see it and check it when the seizures happen.

Good luck.

---

### Post by satish_j on 2010-07-10
i cannot understand how a file that is being deleted from a folder on desktop(and then,also deleted from trash)reappears in the same folder after the problem is faced and the system is restarted???
below is my dmesg output..just wondering f anything can be found from this...
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 21:47:28 UTC 2009 (Ubuntu 2.6.24-23.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000002f7f0000 - 000000002f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f7f3000 - 000000002f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4b20
[    0.000000] Entering add_active_range(0, 0, 194544) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194544
[    0.000000]   HighMem    194544 ->   194544
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194544
[    0.000000] On node 0 totalpages: 194544
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1487 pages used for memmap
[    0.000000]   Normal zone: 188961 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F65A0 checksum 0
[    0.000000] ACPI: RSDP 000F65A0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 2F7F3040, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 2F7F30C0, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 2F7F3180, 3FD0 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 2F7F0000, 0040
[    0.000000] ACPI: APIC 2F7F71C0, 0068 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:cf400000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 193025
[    0.000000] Kernel command line: root=UUID=a0e89d83-6f9d-4d39-91b7-4db80eb01738 ro splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2398.904 MHz processor.
[   18.760088] Console: colour VGA+ 80x25
[   18.760094] console [tty0] enabled
[   18.763573] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.764495] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.782751] Memory: 759164k/778176k available (2179k kernel code, 18336k reserved, 1008k data, 368k init, 0k highmem)
[   18.782824] virtual kernel memory layout:
[   18.782825]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   18.782827]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.782828]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[   18.782829]     lowmem  : 0xc0000000 - 0xef7f0000   ( 759 MB)
[   18.782830]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   18.782832]       .data : 0xc0320c78 - 0xc041cdc4   (1008 kB)
[   18.782833]       .text : 0xc0100000 - 0xc0320c78   (2179 kB)
[   18.783204] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.783342] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.863264] Calibrating delay using timer specific routine.. 4802.21 BogoMIPS (lpj=9604424)
[   18.863385] Security Framework initialized
[   18.863437] SELinux:  Disabled at boot.
[   18.863497] AppArmor: AppArmor initialized
[   18.863547] Failure registering capabilities with primary security module.
[   18.863605] Mount-cache hash table entries: 512
[   18.863799] Initializing cgroup subsys ns
[   18.863850] Initializing cgroup subsys cpuacct
[   18.863910] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   18.863921] monitor/mwait feature present.
[   18.863968] using mwait in idle threads.
[   18.864020] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.864101] CPU: L2 cache: 1024K
[   18.864148] CPU: Hyper-Threading is disabled
[   18.864195] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000441d 00000000 00000000 00000000
[   18.864208] Compat vDSO mapped to ffffe000.
[   18.864272] Checking 'hlt' instruction... OK.
[   18.879831] SMP alternatives: switching to UP code
[   18.882099] Freeing SMP alternatives: 11k freed
[   18.882301] Early unpacking initramfs... done
[   19.250797] ACPI: Core revision 20070126
[   19.250916] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.274584] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
[   19.274737] Total of 1 processors activated (4802.21 BogoMIPS).
[   19.274919] ENABLING IO-APIC IRQs
[   19.275148] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.422221] Brought up 1 CPUs
[   19.422293] CPU0 attaching sched-domain:
[   19.422298]  domain 0: span 01
[   19.422300]   groups: 01
[   19.422528] net_namespace: 64 bytes
[   19.422582] Booting paravirtualized kernel on bare hardware
[   19.423323] Time: 12:37:39  Date: 07/10/10
[   19.423401] NET: Registered protocol family 16
[   19.423729] EISA bus registered
[   19.423800] ACPI: bus type pci registered
[   19.449847] PCI: PCI BIOS revision 2.10 entry at 0xfb090, last bus=1
[   19.449897] PCI: Using configuration type 1
[   19.449948] Setting up standard PCI resources
[   19.462203] ACPI: EC: Look up EC in DSDT
[   19.466938] ACPI: Interpreter enabled
[   19.466988] ACPI: (supports S0 S1 S4 S5)
[   19.467180] ACPI: Using IOAPIC for interrupt routing
[   19.473420] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.473969] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   19.473972] * this clock source is slow. If you are sure your timer does not have
[   19.473973] * this bug, please use "acpi_pm_good" to disable the workaround
[   19.474225] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   19.474277] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   19.474724] PCI: Transparent bridge - 0000:00:1e.0
[   19.474798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.475010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   19.481570] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   19.482144] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   19.482708] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   19.483271] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   19.483837] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.484476] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.485113] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.485750] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   19.486342] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.486433] pnp: PnP ACPI init
[   19.486488] ACPI: bus type pnp registered
[   19.491017] pnp: PnP ACPI: found 16 devices
[   19.491066] ACPI: ACPI bus type pnp unregistered
[   19.491117] PnPBIOS: Disabled by ACPI PNP
[   19.491490] PCI: Using ACPI for IRQ routing
[   19.491539] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.506048] NET: Registered protocol family 8
[   19.506096] NET: Registered protocol family 20
[   19.506229] AppArmor: AppArmor Filesystem Enabled
[   19.509992] Time: tsc clocksource has been installed.
[   19.518028] system 00:01: ioport range 0xb78-0xb7b has been reserved
[   19.518080] system 00:01: ioport range 0xf78-0xf7b has been reserved
[   19.518129] system 00:01: ioport range 0xa78-0xa7b has been reserved
[   19.518179] system 00:01: ioport range 0xe78-0xe7b has been reserved
[   19.518228] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[   19.518279] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[   19.518328] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   19.518378] system 00:01: ioport range 0x294-0x297 has been reserved
[   19.518440] system 00:0e: ioport range 0x400-0x4bf could not be reserved
[   19.518495] system 00:0f: iomem range 0xcb200-0xcbfff has been reserved
[   19.518545] system 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[   19.518596] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   19.518647] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   19.518697] system 00:0f: iomem range 0x2f7f0000-0x2f7fffff could not be reserved
[   19.518757] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   19.518807] system 00:0f: iomem range 0x100000-0x2f7effff could not be reserved
[   19.518865] system 00:0f: iomem range 0xfec00000-0xfec00fff could not be reserved
[   19.518925] system 00:0f: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.518984] system 00:0f: iomem range 0xffb00000-0xffbfffff could not be reserved
[   19.519043] system 00:0f: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.519102] system 00:0f: iomem range 0xe0000-0xeffff has been reserved
[   19.549669] PCI: Bridge: 0000:00:1e.0
[   19.549719]   IO window: d000-dfff
[   19.549770]   MEM window: e8000000-e80fffff
[   19.549818]   PREFETCH window: disabled.
[   19.549879] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.549893] NET: Registered protocol family 2
[   19.589943] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.590464] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.591705] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.592691] TCP: Hash tables configured (established 131072 bind 65536)
[   19.592743] TCP reno registered
[   19.602088] checking if image is initramfs... it is
[   20.048931] Switched to high resolution mode on CPU 0
[   20.326169] Freeing initrd memory: 7308k freed
[   20.327216] audit: initializing netlink socket (disabled)
[   20.327289] audit(1278765459.420:1): initialized
[   20.330117] VFS: Disk quotas dquot_6.5.1
[   20.330266] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.330514] io scheduler noop registered
[   20.330562] io scheduler anticipatory registered
[   20.330609] io scheduler deadline registered
[   20.330668] io scheduler cfq registered (default)
[   20.330733] Boot video device is 0000:00:02.0
[   20.331158] isapnp: Scanning for PnP cards...
[   20.683378] isapnp: No Plug & Play device found
[   20.723936] Real Time Clock Driver v1.12ac
[   20.724123] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.724312] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.724509] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.725418] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.725800] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.726968] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.727120] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.727320] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.729731] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.729784] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.735586] mice: PS/2 mouse device common for all mice
[   20.735783] EISA: Probing bus 0 at eisa.0
[   20.735869] EISA: Detected 0 cards.
[   20.735917] cpuidle: using governor ladder
[   20.735965] cpuidle: using governor menu
[   20.736120] NET: Registered protocol family 1
[   20.736201] Using IPI No-Shortcut mode
[   20.736289] registered taskstats version 1
[   20.736437]   Magic number: 2:609:632
[   20.736536]   hash matches device ptycb
[   20.736652] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.736701] EDD information not available.
[   20.737254] Freeing unused kernel memory: 368k freed
[   20.737328] Write protecting the kernel read-only data: 806k
[   20.763445] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.030465] fuse init (API version 7.9)
[   22.049507] ACPI: Fan [FAN] (on)
[   22.056357] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.057900] ACPI: Thermal Zone [THRM] (22 C)
[   22.574855] usbcore: registered new interface driver usbfs
[   22.574891] usbcore: registered new interface driver hub
[   22.579684] usbcore: registered new device driver usb
[   22.594632] USB Universal Host Controller Interface driver v3.0
[   22.594733] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.594749] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.594754] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.595130] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.595164] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e200
[   22.595341] usb usb1: configuration #1 chosen from 1 choice
[   22.595379] hub 1-0:1.0: USB hub found
[   22.595388] hub 1-0:1.0: 2 ports detected
[   22.695530] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   22.695552] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.695558] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.695590] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.695622] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e000
[   22.695780] usb usb2: configuration #1 chosen from 1 choice
[   22.695813] hub 2-0:1.0: USB hub found
[   22.695822] hub 2-0:1.0: 2 ports detected
[   22.799315] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   22.799339] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.799344] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.799378] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.799410] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e100
[   22.799567] usb usb3: configuration #1 chosen from 1 choice
[   22.799600] hub 3-0:1.0: USB hub found
[   22.799608] hub 3-0:1.0: 2 ports detected
[   22.896584] 8139too Fast Ethernet driver 0.9.28
[   22.907659] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   22.907678] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.907682] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.907714] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   22.911632] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.911645] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8180000
[   22.926971] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.927137] usb usb4: configuration #1 chosen from 1 choice
[   22.927172] hub 4-0:1.0: USB hub found
[   22.927182] hub 4-0:1.0: 6 ports detected
[   22.953710] SCSI subsystem initialized
[   23.002354] libata version 3.00 loaded.
[   23.030973] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 17 (level, low) -> IRQ 20
[   23.031726] eth0: RealTek RTL8139 at 0xd000, 00:e0:b1:b2:8c:3f, IRQ 20
[   23.031729] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   23.031752] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.032478] eth1: RealTek RTL8139 at 0xd100, 00:05:07:01:58:cf, IRQ 16
[   23.032481] eth1:  Identified 8139 chip type 'RTL-8139C'
[   23.045933] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   23.064286] ata_piix 0000:00:1f.1: version 2.12
[   23.064316] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   23.064388] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.070172] scsi0 : ata_piix
[   23.078828] scsi1 : ata_piix
[   23.079739] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   23.079743] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   23.094699] Floppy drive(s): fd0 is 1.44M
[   23.114304] FDC 0 is a post-1991 82077
[   23.250639] ata1.00: ATA-7: SAMSUNG SP0411N, TW100-11, max UDMA/100
[   23.250647] ata1.00: 78242976 sectors, multi 16: LBA48 
[   23.260390] ata1.01: ATA-7: WDC WD1600AABB-22PUA0, 00.07H00, max UDMA/100
[   23.260395] ata1.01: 312581808 sectors, multi 16: LBA48 
[   23.266582] ata1.00: configured for UDMA/100
[   23.275129] ata1.01: configured for UDMA/100
[   23.593842] ata2.00: ATAPI: MOSER BAER DH-22A8P, UM71, max UDMA/66
[   23.765387] ata2.00: configured for UDMA/66
[   23.765570] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0411N  TW10 PQ: 0 ANSI: 5
[   23.766050] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1600AABB-2 00.0 PQ: 0 ANSI: 5
[   23.767328] scsi 1:0:0:0: CD-ROM            MOSER    BAER DH-22A8P    UM71 PQ: 0 ANSI: 5
[   23.783730] Driver 'sd' needs updating - please use bus_type methods
[   23.783859] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   23.783879] sd 0:0:0:0: [sda] Write Protect is off
[   23.783883] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.783911] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.783979] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   23.783995] sd 0:0:0:0: [sda] Write Protect is off
[   23.783999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.784026] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.784030]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   23.803182]  sda5 sda6 sda7 >
[   23.840713] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.840798] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   23.840819] sd 0:0:1:0: [sdb] Write Protect is off
[   23.840823] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.840852] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.840914] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   23.840930] sd 0:0:1:0: [sdb] Write Protect is off
[   23.840934] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.840961] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.840965]  sdb: sdb1 sdb2 sdb3
[   23.848938] sd 0:0:1:0: [sdb] Attached SCSI disk
[   23.860593] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.860625] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   23.860650] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   23.867306] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.867316] Uniform CD-ROM driver Revision: 3.20
[   23.867399] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.774583] Attempting manual resume
[   24.774589] swsusp: Resume From Partition 8:7
[   24.774592] PM: Checking swsusp image.
[   24.774807] PM: Resume from disk failed.
[   24.813883] kjournald starting.  Commit interval 5 seconds
[   24.813902] EXT3-fs: mounted filesystem with ordered data mode.
[   35.361073] Linux agpgart interface v0.102
[   35.455875] intel_rng: FWH not detected
[   35.676443] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.732386] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.774052] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.823329] agpgart: Detected an Intel 830M Chipset.
[   35.823615] agpgart: Detected 8060K stolen memory.
[   35.839085] agpgart: AGP aperture is 128M @ 0xe0000000
[   35.920984] input: Power Button (FF) as /devices/virtual/input/input3
[   35.938181] ACPI: Power Button (FF) [PWRF]
[   35.938281] input: Power Button (CM) as /devices/virtual/input/input4
[   35.951813] ACPI: Power Button (CM) [PWRB]
[   35.951922] input: Sleep Button (CM) as /devices/virtual/input/input5
[   35.967790] ACPI: Sleep Button (CM) [SLPB]
[   36.174575] iTCO_vendor_support: vendor-support=0
[   36.227152] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.300118] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   36.405546] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   36.422939] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   36.422984] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.892464] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.951900] eth1: link down
[   38.160893] parport_pc 00:09: reported by Plug and Play ACPI
[   38.160950] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   38.438918] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   38.438952] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   38.762049] intel8x0_measure_ac97_clock: measured 53584 usecs
[   38.762057] intel8x0: clocking to 48000
[   38.845804] NET: Registered protocol family 10
[   38.846131] lo: Disabled Privacy Extensions
[   38.847050] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   40.900219] lp0: using parport0 (interrupt-driven).
[   41.037902] Adding 602396k swap on /dev/sda7.  Priority:-1 extents:1 across:602396k
[   41.710182] EXT3 FS on sda6, internal journal
[   43.127375] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.055477] No dock devices found.
[   45.514910] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   45.514919] apm: overridden by ACPI.
[   45.831417] ppdev: user-space parallel port driver
[   46.037067] audit(1278745686.356:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5136 profile="/usr/sbin/cupsd" namespace="default"
[   48.970155] Bluetooth: Core ver 2.11
[   48.971070] NET: Registered protocol family 31
[   48.971076] Bluetooth: HCI device and connection manager initialized
[   48.971082] Bluetooth: HCI socket layer initialized
[   49.016688] Bluetooth: L2CAP ver 2.9
[   49.016695] Bluetooth: L2CAP socket layer initialized
[   49.085649] Bluetooth: RFCOMM socket layer initialized
[   49.085675] Bluetooth: RFCOMM TTY layer initialized
[   49.085678] Bluetooth: RFCOMM ver 1.8
[   49.483665] eth0: no IPv6 routers present
[   51.935295] [drm] Initialized drm 1.1.0 20060810
[   51.957412] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   51.957425] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   51.957546] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   96.742298] PPP generic driver version 2.4.2
[   96.788499] NET: Registered protocol family 17
[   97.091239] NET: Registered protocol family 24

```
THe folders inside root folder are all owned by root user,barring 'home' and 'tmp' folders,which are owned by me..Is it ok??I remember donloading a file yesterday which failed and gave some error related to /tmp folder(i did not took the screenshot).

---

### Post by satish_j on 2010-07-10
iam really getting frustated now..ubuntu is restoring back all the time.tried googling and found some related issues.ihave tried booting the system from live CD and running fsck on ubuntu partition.it came clean.
also(from some thread with similar issue),i tried renaming /media/.hal-mtab to /media/.hal-mtab-old and reboot..that also didn't worked...
Afer some time,i cannot even delete files from my desktop,it says "Read only file system"
/var/log folder also does not contain messages folder and syslog folder
??????

---

### Post by stoneage on 2010-07-10
Could it be a problem with the HDD ?

---

### Post by satish_j on 2010-07-11
finally narrowed it down...and ya,it is an HDD issue...
Iam dual booting XP and the prob is being faced in XP as well.So,i tried formatting the C partion,but cannot format as the setup gave error as 
"seup as unable to format the patition.the disk may be damaged.Make sure that the dive is switched on and properly connected to your computer..."
Now,iam guessing whether there is any workaround for this or i have to get an new disc now???
My windows and linux both were on same HD(on diff partitions)and i have a second HD(that contains a lot of data).can this problem have affectd the second HD also???

---

### Post by satish_j on 2010-08-03
Ah,it was hardware issue..iam kinda relieved as otherwise,it led me to think of any other possible bug in Ubuntu..Replaced the HDD and Ubuntu is up and running..

---

