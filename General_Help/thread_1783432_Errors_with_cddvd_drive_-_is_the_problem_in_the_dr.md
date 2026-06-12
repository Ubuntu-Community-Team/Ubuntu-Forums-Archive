---
title: "Errors with cd/dvd drive - is the problem in the drivers?"
date: 2011-06-15
forum: General Help
---

### Post by HotForLinux on 2011-06-15
I am having problems with a cd/dvd drive and I would like to know if it could be a driver problem or what?
I can boot from cdroms but I almost always have problems mounting the cdrom's filesystem.

The laptop has been working for years with the same ubuntu release (hardy) but there are always a couple of warnings  during boot time saying that certain drivers should be updated but I don't know how.


These are the persistent messages from **dmesg** output:
```

[   12.693449] Driver 'sd' needs updating - please use bus_type methods
[   12.700371] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.708884] sd 0:0:0:0: [sda] Write Protect is off
[   12.715663] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.716147] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.725436] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.732841] Driver 'sr' needs updating - please use bus_type methods
[   12.739815] sd 0:0:0:0: [sda] Write Protect is off
[   12.746810] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.747211] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.754996]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   12.763647] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.777490] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.784487] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   12.795542] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.802494] Uniform CD-ROM driver Revision: 3.20
[   12.809501] sr 1:0:0:0: Attached scsi CD-ROM sr0
```


These is the fstab line  for the cdrom:
```

# <file system>        <mount point>   <type>      <options>       <dump>  <pass>
/dev/scd0        /media/cdrom0    iso9660        user,auto,exec            0    0
```This is the full output of **dmesg** after trying to work with the cdrom drive: taking the cd out, putting it in again, trying to mount by hand,  etc.:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-29-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Fri May 27 18:38:38 UTC 2011 (Ubuntu 2.6.24-29.90-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7dfffc (usable)
[    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 631MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 391135) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   391135
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   391135
[    0.000000] On node 0 totalpages: 391135
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1263 pages used for memmap
[    0.000000]   HighMem zone: 160496 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 5F7F8D10, 6E13 (r1 TOSINV SONOMA       1004 INTL  2002036)
[    0.000000] ACPI: FACS 5F7FFFC0, 0040
[    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 5F7F88B5, 0237 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5f800000:a0700000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 388080
[    0.000000] Kernel command line: root=UUID=101d90ae-ebe6-48a2-b01b-51421c9cbfc7 ro vga=791
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01c01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.004 MHz processor.
[    8.556093] Console: colour dummy device 80x25
[    8.556098] console [tty0] enabled
[    8.556582] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.557055] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.632024] Memory: 1538440k/1564540k available (2183k kernel code, 24904k reserved, 1008k data, 368k init, 647036k highmem)
[    8.632047] virtual kernel memory layout:
[    8.632048]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.632049]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.632051]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.632052]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.632053]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[    8.632055]       .data : 0xc0321d0a - 0xc041ddc4   (1008 kB)
[    8.632056]       .text : 0xc0100000 - 0xc0321d0a   (2183 kB)
[    8.632080] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.632149] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.632213] Calibrating delay loop (skipped), using tsc calculated value.. 3192.00 BogoMIPS (lpj=6384016)
[    8.632258] Security Framework initialized
[    8.632273] SELinux:  Disabled at boot.
[    8.632296] AppArmor: AppArmor initialized
[    8.632304] Failure registering capabilities with primary security module.
[    8.632318] Mount-cache hash table entries: 512
[    8.632492] Initializing cgroup subsys ns
[    8.632506] Initializing cgroup subsys cpuacct
[    8.632522] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    8.632536] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.632541] CPU: L2 cache: 2048K
[    8.632548] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00042040 00000180 00000000 00000000 00000000
[    8.632559] Compat vDSO mapped to ffffe000.
[    8.632577] Checking 'hlt' instruction... OK.
[    8.648581] SMP alternatives: switching to UP code
[    8.650580] Freeing SMP alternatives: 11k freed
[    8.650711] Early unpacking initramfs... done
[    9.051169] ACPI: Core revision 20070126
[    9.051252] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.054175] ACPI: setting ELCR to 0200 (from 0c20)
[    9.121301] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    9.121318] SMP motherboard not detected.
[    9.121323] Local APIC not detected. Using dummy APIC emulation.
[    9.121371] Brought up 1 CPUs
[    9.121390] CPU0 attaching sched-domain:
[    9.121393]  domain 0: span 01
[    9.121395]   groups: 01
[    9.121586] net_namespace: 64 bytes
[    9.121597] Booting paravirtualized kernel on bare hardware
[    9.122084] Time: 23:32:56  Date: 06/15/11
[    9.122114] NET: Registered protocol family 16
[    9.122314] EISA bus registered
[    9.122339] ACPI: bus type pci registered
[    9.122468] PCI: PCI BIOS revision 2.10 entry at 0xea7d4, last bus=5
[    9.122474] PCI: Using configuration type 1
[    9.122485] Setting up standard PCI resources
[    9.125088] ACPI: EC: Look up EC in DSDT
[    9.132451] ACPI: Interpreter enabled
[    9.132457] ACPI: (supports S0 S3 S4 S5)
[    9.132474] ACPI: Using PIC for interrupt routing
[    9.153303] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    9.153310] ACPI: EC: driver started in poll mode
[    9.153353] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.154115] Force enabled HPET at base address 0xfed00000
[    9.154121] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.154129] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[    9.154956] PCI: Transparent bridge - 0000:00:1e.0
[    9.155043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.155456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.155633] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.155825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.182579] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[    9.182749] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    9.182860] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[    9.182969] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    9.183078] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[    9.183187] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[    9.183338] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[    9.183447] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[    9.183582] ACPI: Power Resource [PFA1] (off)
[    9.183626] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.183660] pnp: PnP ACPI init
[    9.183669] ACPI: bus type pnp registered
[    9.191724] pnp: PnP ACPI: found 9 devices
[    9.191730] ACPI: ACPI bus type pnp unregistered
[    9.191735] PnPBIOS: Disabled by ACPI PNP
[    9.191960] PCI: Using ACPI for IRQ routing
[    9.191966] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.192005] PCI: Cannot allocate resource region 0 of device 0000:05:06.0
[    9.214269] NET: Registered protocol family 8
[    9.214274] NET: Registered protocol family 20
[    9.214455] hpet clockevent registered
[    9.214462] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.214470] hpet0: 3 64-bit timers, 14318180 Hz
[    9.215505] AppArmor: AppArmor Filesystem Enabled
[    9.218456] Time: tsc clocksource has been installed.
[    9.226486] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    9.226494] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    9.226500] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    9.226506] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    9.226513] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    9.226519] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    9.226525] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    9.226531] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    9.226541] system 00:05: ioport range 0x300-0x36f has been reserved
[    9.226547] system 00:05: ioport range 0x800-0x80f has been reserved
[    9.226553] system 00:05: ioport range 0x1000-0x107f has been reserved
[    9.226559] system 00:05: ioport range 0x1300-0x133f has been reserved
[    9.226565] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[    9.226572] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[    9.226578] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[    9.226584] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[    9.226590] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[    9.256979] PCI: Bridge: 0000:00:1c.0
[    9.256985]   IO window: c000-dfff
[    9.256993]   MEM window: cc000000-cfffffff
[    9.256999]   PREFETCH window: 9c000000-9fffffff
[    9.257008] PCI: Bridge: 0000:00:1c.1
[    9.257013]   IO window: a000-bfff
[    9.257020]   MEM window: c8000000-cbffffff
[    9.257027]   PREFETCH window: 98000000-9bffffff
[    9.257043] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[    9.257047]   IO window: 00008000-000080ff
[    9.257055]   IO window: 00008400-000084ff
[    9.257062]   PREFETCH window: 88000000-8bffffff
[    9.257069]   MEM window: bc000000-bfffffff
[    9.257076] PCI: Bridge: 0000:00:1e.0
[    9.257081]   IO window: 8000-9fff
[    9.257089]   MEM window: b8000000-c7ffffff
[    9.257095]   PREFETCH window: 88000000-97ffffff
[    9.257293] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    9.257299] PCI: setting IRQ 10 as level-triggered
[    9.257304] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    9.257316] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.257494] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    9.257500] PCI: setting IRQ 11 as level-triggered
[    9.257504] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    9.257516] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.257529] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.257701] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    9.257707] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    9.257726] NET: Registered protocol family 2
[    9.294445] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.294677] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.295479] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.295948] TCP: Hash tables configured (established 131072 bind 65536)
[    9.295955] TCP reno registered
[    9.306536] checking if image is initramfs... it is
[    9.717998] Switched to high resolution mode on CPU 0
[   10.093167] Freeing initrd memory: 7716k freed
[   10.093799] audit: initializing netlink socket (disabled)
[   10.093824] audit(1308180777.400:1): initialized
[   10.094032] highmem bounce pool size: 64 pages
[   10.096020] VFS: Disk quotas dquot_6.5.1
[   10.096101] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.096261] io scheduler noop registered
[   10.096267] io scheduler anticipatory registered
[   10.096271] io scheduler deadline registered
[   10.096285] io scheduler cfq registered (default)
[   10.096301] Boot video device is 0000:00:02.0
[   10.096500] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.096553] assign_interrupt_mode Found MSI capability
[   10.096604] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.096645] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.096741] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.096793] assign_interrupt_mode Found MSI capability
[   10.096838] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.096872] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.097121] isapnp: Scanning for PnP cards...
[   10.450784] isapnp: No Plug & Play device found
[   10.478835] Real Time Clock Driver v1.12ac
[   10.478961] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.479817] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   10.479825] PCI: setting IRQ 5 as level-triggered
[   10.479830] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   10.479845] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   10.480510] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.480589] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.480693] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.485529] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.488176] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.488183] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.488189] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.488194] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.488198] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.497255] mice: PS/2 mouse device common for all mice
[   10.497370] EISA: Probing bus 0 at eisa.0
[   10.497380] Cannot allocate resource for EISA slot 1
[   10.497407] Cannot allocate resource for EISA slot 8
[   10.497411] EISA: Detected 0 cards.
[   10.497416] cpuidle: using governor ladder
[   10.497421] cpuidle: using governor menu
[   10.497520] NET: Registered protocol family 1
[   10.497551] Using IPI No-Shortcut mode
[   10.497591] registered taskstats version 1
[   10.497712]   Magic number: 15:46:555
[   10.497756]   hash matches device ptya1
[   10.497810]   hash matches device PNP0C0F:06
[   10.497822] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.497827] EDD information not available.
[   10.498029] Freeing unused kernel memory: 368k freed
[   10.498060] Write protecting the kernel read-only data: 807k
[   10.504052] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.593073] vesafb: framebuffer at 0xa0000000, mapped to 0xf8880000, using 3072k, total 7872k
[   10.593103] vesafb: mode is 1024x768x16, linelength=2048, pages=4
[   10.593108] vesafb: scrolling: redraw
[   10.593113] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   10.593231] Console: switching to colour frame buffer device 128x48
[   10.608587] fb0: VESA VGA frame buffer device
[   10.720736] fuse init (API version 7.9)
[   10.733175] ACPI: Transitioning device [FAN1] to D3
[   10.733323] ACPI: Transitioning device [FAN1] to D3
[   10.733467] ACPI: Fan [FAN1] (off)
[   10.739600] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.739794] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.739996] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   10.805010] ACPI: Thermal Zone [TZCR] (57 C)
[   10.812981] ACPI: Thermal Zone [TZCL] (43 C)
[   11.212482] Clocksource tsc unstable (delta = -4637812036 ns)
[   11.216471] Time: hpet clocksource has been installed.
[   11.416640] usbcore: registered new interface driver usbfs
[   11.416836] usbcore: registered new interface driver hub
[   11.424302] usbcore: registered new device driver usb
[   11.436295] USB Universal Host Controller Interface driver v3.0
[   11.442133] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   11.447764] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   11.453538] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.453543] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.487022] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.493013] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   11.522965] usb usb1: configuration #1 chosen from 1 choice
[   11.528971] hub 1-0:1.0: USB hub found
[   11.548195] hub 1-0:1.0: 2 ports detected
[   11.676395] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   11.682434] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   11.688686] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.688690] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.694927] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.701197] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[   11.707519] usb usb2: configuration #1 chosen from 1 choice
[   11.713752] hub 2-0:1.0: USB hub found
[   11.719884] hub 2-0:1.0: 2 ports detected
[   11.746595] SCSI subsystem initialized
[   11.811942] libata version 3.00 loaded.
[   11.839991] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   11.846071] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.846076] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.852083] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.858079] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[   11.864111] usb usb3: configuration #1 chosen from 1 choice
[   11.870081] hub 3-0:1.0: USB hub found
[   11.875954] hub 3-0:1.0: 2 ports detected
[   11.983866] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.989904] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.989909] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.996321] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   12.002419] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[   12.008663] usb usb4: configuration #1 chosen from 1 choice
[   12.014852] hub 4-0:1.0: USB hub found
[   12.020983] hub 4-0:1.0: 2 ports detected
[   12.127887] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[   12.133924] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   12.140018] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.140022] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.147319] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.157437] ehci_hcd 0000:00:1d.7: debug port 1
[   12.163582] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.163590] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[   12.183547] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.189903] usb usb5: configuration #1 chosen from 1 choice
[   12.196226] hub 5-0:1.0: USB hub found
[   12.202435] hub 5-0:1.0: 8 ports detected
[   12.311928] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[   12.318152] PCI: setting IRQ 6 as level-triggered
[   12.318157] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[   12.374298] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.391612] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.398515] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.398531] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   12.411261] ahci 0000:00:1f.2: version 3.0
[   12.411273] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.418203] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   12.425011] ahci: probe of 0000:00:1f.2 failed with error -22
[   12.435012] ata_piix 0000:00:1f.2: version 2.12
[   12.435018] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   12.579842] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.586822] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.586905] scsi0 : ata_piix
[   12.593895] scsi1 : ata_piix
[   12.601591] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[   12.608527] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[   12.618764] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[   12.625585] ata1.00: 156301488 sectors, multi 16: LBA48 
[   12.632295] ata1.00: applying bridge limits
[   12.640543] ata1.00: configured for UDMA/100
[   12.652535] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830S, 1.00, max UDMA/33
[   12.662172] ata2.00: configured for UDMA/33
[   12.668909] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[   12.676421] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830S  1.00 PQ: 0 ANSI: 5
[   12.693449] Driver 'sd' needs updating - please use bus_type methods
[   12.700371] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.708884] sd 0:0:0:0: [sda] Write Protect is off
[   12.715663] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.716147] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.725436] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.732841] Driver 'sr' needs updating - please use bus_type methods
[   12.739815] sd 0:0:0:0: [sda] Write Protect is off
[   12.746810] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.747211] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.754996]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   12.763647] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.777490] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.784487] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   12.795542] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.802494] Uniform CD-ROM driver Revision: 3.20
[   12.809501] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.857252] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1bbae17]
[   12.949832] Attempting manual resume
[   12.956858] swsusp: Resume From Partition 8:6
[   12.956859] PM: Checking swsusp image.
[   12.956988] PM: Resume from disk failed.
[   12.980053] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   12.987237] ReiserFS: sda5: using ordered data mode
[   12.994982] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   13.010153] ReiserFS: sda5: checking transaction log (sda5)
[   13.018264] ReiserFS: sda5: Using r5 hash to sort names
[   16.760767] iTCO_vendor_support: vendor-support=0
[   16.832296] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   16.839148] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   16.845665] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.924183] Linux agpgart interface v0.102
[   16.999728] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   17.076066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.324371] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.509393] input: Power Button (FF) as /devices/virtual/input/input3
[   17.543564] ACPI: Power Button (FF) [PWRF]
[   17.550144] input: Lid Switch as /devices/virtual/input/input4
[   17.571639] ACPI: Lid Switch [LID0]
[   17.578154] input: Power Button (CM) as /devices/virtual/input/input5
[   17.603545] agpgart: Detected an Intel 915GM Chipset.
[   17.610550] agpgart: Detected 7932K stolen memory.
[   17.634762] ACPI: Power Button (CM) [PWRB]
[   17.641182] agpgart: AGP aperture is 256M @ 0xa0000000
[   17.771336] intel_rng: FWH not detected
[   17.863453] ACPI: Battery Slot [BAT1] (battery present)
[   18.214954] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[   18.221433] Yenta: Enabling burst memory read transactions
[   18.227809] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.234143] Yenta: Routing CardBus interrupts to PCI
[   18.240451] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[   18.306966] ACPI: AC Adapter [AC] (on-line)
[   18.374774] ieee80211_crypt: registered algorithm 'NULL'
[   18.434672] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.441007] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.479203] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[   18.485535] Socket status: 30000006
[   18.491813] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   18.498180] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   18.504567] cs: IO port probe 0x8000-0x9fff: clean.
[   18.511303] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[   18.517510] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[   19.034770] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   19.066055] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   19.123731] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   19.157198] sdhci: Secure Digital Host Controller Interface driver
[   19.163790] sdhci: Copyright(c) Pierre Ossman
[   19.171477] sdhci: SDHCI controller found at 0000:05:06.4 [104c:8034] (rev 0)
[   19.178197] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   19.185154] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   19.192245] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[   19.199241] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   19.209626] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[   19.216841] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   19.242343] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[   19.360818] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.368434] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.376948] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.421426] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.022672] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   20.030470] synaptics: Toshiba Satellite M45 detected, limiting rate to 40pps.
[   20.089536] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   21.394120] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   21.402115] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   21.410177] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   21.410209] sky2 0000:01:00.0: v1.20 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[   21.445403] udev: renamed network interface eth0 to eth1
[   21.483142] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[   21.491559] cs: IO port probe 0x100-0x3af: clean.
[   21.501097] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.509906] cs: IO port probe 0x820-0x8ff: clean.
[   21.518586] cs: IO port probe 0xc00-0xcf7: clean.
[   21.532961] cs: IO port probe 0xa00-0xaff: clean.
[   21.543464] ieee80211_crypt: registered algorithm 'WEP'
[   21.608982] sky2 eth0: addr 00:a0:d1:bb:ae:17
[   21.617163] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   21.625646] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   21.699129] intel8x0_measure_ac97_clock: measured 55449 usecs
[   21.707093] intel8x0: clocking to 48000
[   21.855499] lp: driver loaded but no devices found
[   22.099377] NET: Registered protocol family 17
[   22.116279] Adding 208836k swap on /dev/sda3.  Priority:-1 extents:1 across:208836k
[   22.116642] Adding 1277128k swap on /dev/sda6.  Priority:-2 extents:1 across:1277128k
[   22.709208] device-mapper: uevent: version 1.0.3
[   22.709239] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   22.898062] NET: Registered protocol family 10
[   22.898293] lo: Disabled Privacy Extensions
[   24.700353] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.754803] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   24.849904] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.250617] eth1: no IPv6 routers present
[   25.641732] ACPI: Error installing notify handler
[   25.641792] No dock devices found.
[   26.352621] sky2 eth0: enabling interface
[   26.356450] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.384314] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   26.384336] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   26.720334] ppdev: user-space parallel port driver
[   26.721693] sky2 eth0: disabling interface
[   26.824534] audit(1308173641.980:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5858 profile="/usr/sbin/cupsd" namespace="default"
[   26.916803] sky2 eth0: enabling interface
[   26.920734] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.946734] apm: BIOS not found.
[   42.075491] Marking TSC unstable due to: cpufreq changes.
[   29.709776] [drm] Initialized drm 1.1.0 20060810
[   29.714387] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   29.714397] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.714470] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   63.936168] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   67.169034] UDF-fs: No VRS found
[   67.171337] ISO 9660 Extensions: Microsoft Joliet Level 3
[   67.172594] ISOFS: changing to secondary root
[   76.160154] VFS: busy inodes on changed media.
[   76.163794] VFS: busy inodes on changed media.
[   95.714028] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   95.714039] ata2.00: BMDMA stat 0x25
[   95.714057] ata2.00: cmd a0/01:00:00:00:08/00:00:00:00:00/a0 tag 0 dma 2048 in
[   95.714060]          cdb 28 00 00 01 96 dc 00 00  01 00 00 00 00 00 00 00
[   95.714064]          res 51/50:13:10:10:08/00:00:00:00:00/a0 Emask 0x1 (device error)
[   95.714071] ata2.00: status: { DRDY ERR }
[   95.714105] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   95.714113] sr 1:0:0:0: [sr0] Sense Key : Aborted Command [current] [descriptor]
[   95.714122] Descriptor sense data with sense descriptors (in hex):
[   95.714127]         72 0b 14 00 00 00 00 0e 09 0c 00 50 00 13 00 10 
[   95.714142]         00 10 00 08 a0 51 
[   95.714150] sr 1:0:0:0: [sr0] Add. Sense: Recorded entity not found
[   95.714160] end_request: I/O error, dev sr0, sector 416624
[   95.716298] ISOFS: unable to read i-node block
[  133.611441] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  133.614793] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  133.614797]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  133.614800]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[  133.618185] ata2.00: status: { DRDY ERR }
[  133.634511] VFS: busy inodes on changed media.
[  133.649344] VFS: busy inodes on changed media.
[   66.834080] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   66.835949] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[   66.835951]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[   66.835952]          res 51/50:13:10:1c:10/00:00:00:00:00/b0 Emask 0x1 (device error)
[   66.837806] ata2.00: status: { DRDY ERR }
[   66.840534] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   66.842502] sr: Sense Key : Aborted Command [current] [descriptor]
[   66.842506] sr: Add. Sense: Recorded entity not found
[   66.843028] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   66.844965] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[   66.844966]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   66.844968]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x2 (HSM violation)
[   66.846923] ata2: soft resetting link
[  133.812161] ata2.00: configured for UDMA/33
[  133.812181] ata2: EH complete
[  133.824280] VFS: busy inodes on changed media.
[  136.136115] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  136.139229] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  136.139232]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  136.139235]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[  136.142423] ata2.00: status: { DRDY }
[  136.145602] ata2: soft resetting link
[  136.179202] ata2.00: NODEV after polling detection
[  136.179211] ata2.00: revalidation failed (errno=-2)
[  136.182332] ata2: failed to recover some devices, retrying in 5 secs
[  136.381745] ata2: soft resetting link
[  136.384800] ata2.00: NODEV after polling detection
[  136.384808] ata2.00: revalidation failed (errno=-2)
[  136.387903] ata2: failed to recover some devices, retrying in 5 secs
[  136.587756] ata2: soft resetting link
[  136.590433] ata2.00: NODEV after polling detection
[  136.590441] ata2.00: revalidation failed (errno=-2)
[  136.593523] ata2.00: disabled
[  136.597809] ata2: soft resetting link
[  136.599185] ata2: EH complete
[  136.610566] VFS: busy inodes on changed media.
[  136.622496] VFS: busy inodes on changed media.
[   68.310134] VFS: busy inodes on changed media.
[   68.320269] VFS: busy inodes on changed media.
[   68.342013] VFS: busy inodes on changed media.
[   68.352186] VFS: busy inodes on changed media.
[   68.366105] VFS: busy inodes on changed media.
[   68.376647] VFS: busy inodes on changed media.
[  139.790062] UDF-fs: No partition found (1)
[  139.790884] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  141.158546] UDF-fs: No partition found (1)
[  141.159362] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  141.446631] UDF-fs: No partition found (1)
[  141.447711] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  141.974216] UDF-fs: No partition found (1)
[  141.975087] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  144.544483] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  147.519275] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  148.795307] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  297.922336] spurious 8259A interrupt: IRQ7.
```

---

### Post by HotForLinux on 2011-06-17
- Bump -

---

