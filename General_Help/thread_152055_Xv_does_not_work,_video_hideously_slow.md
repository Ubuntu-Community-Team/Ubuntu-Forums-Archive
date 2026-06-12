---
title: "Xv does not work, video hideously slow"
date: 2006-03-29
forum: General Help
---

### Post by RoboJ1M on 2006-03-29
Hi,

First off, bear with me as I'm new at this.
I have Linux experience, but only with LEAF (Linux Embedded Application Firewall).

I've finally gotten round to wiping my main PC and installing Ubuntu with the goal of learning how to put together a fabulous MythTV based house network.

But Xv does not appear to be working. The "test" button in the media sink selector succeeds after boot.

But then if I try to run any video apps, they don't use Xv or fail completely (Totem & GXine).

After that, the "test" button no longer works until I reboot.

I have an ATI Radeon 9600 Pro (R350).
I think I wish I didn't. ](*,) 

I have installed the latest ATI drivers as according to the HOWTO on these forums.

I have also used:

```
sudo aticonfig --<Something ro other>
```

to add:
```
 
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```

to /etc/X11/xorg.conf

And that's where I got to.

I don't know how to start finding the problem, logs of errors, etc.

Can anybody help me?

Thanks,

J1M.

---

### Post by dcstar on 2006-03-29
[QUOTE=RoboJ1M]
......
I don't know how to start finding the problem, logs of errors, etc.

Can anybody help me?

Thanks,

J1M.[/QUOTE]
Test your video driver installation with "glxinfo"

Log files should be in /var/log, use Applications-System Tools-System Log to view them.

---

### Post by RoboJ1M on 2006-03-29
I shall do that after work and post it tomorrow, thankyou.

(No internet connection at home :()

J1M.

---

### Post by RoboJ1M on 2006-03-30
OK, here we go. Log files.

I've forgotten xorg.conf (sorry), but that just loads fglrx and sets VideoOverlay on and OpenGLOverlay off

**dmesg** 

```
000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.610000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.611000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.622000] Memory: 510476k/524224k available (1622k kernel code, 13180k reserved, 730k data, 168k init, 0k highmem)
[4294667.622000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.622000] Calibrating delay loop... 5472.25 BogoMIPS (lpj=2736128)
[4294667.645000] Security Framework v1.0.0 initialized
[4294667.645000] SELinux:  Disabled at boot.
[4294667.645000] Mount-cache hash table entries: 512
[4294667.645000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[4294667.645000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[4294667.645000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.645000] CPU: L2 cache: 512K
[4294667.645000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00000400 00000000 00000000
[4294667.645000] Intel machine check architecture supported.
[4294667.645000] Intel machine check reporting enabled on CPU#0.
[4294667.645000] CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
[4294667.645000] CPU0: Thermal monitoring enabled
[4294667.645000] CPU: Intel(R) Pentium(R) 4 CPU 2.50GHz stepping 07
[4294667.645000] Enabling fast FPU save and restore... done.
[4294667.645000] Enabling unmasked SIMD FPU exception support... done.
[4294667.645000] Checking 'hlt' instruction... OK.
[4294667.649000] checking if image is initramfs... it is
[4294668.110000] Freeing initrd memory: 5492k freed
[4294668.115000] ACPI: Looking for DSDT in initrd... not found!
[4294668.161000]  not found!
[4294668.178000] ENABLING IO-APIC IRQs
[4294668.178000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.289000] NET: Registered protocol family 16
[4294668.289000] ACPI: bus type pci registered
[4294668.301000] PCI: PCI BIOS revision 2.10 entry at 0xfb040, last bus=2
[4294668.301000] PCI: Using configuration type 1
[4294668.301000] mtrr: v2.0 (20020519)
[4294668.301000] ACPI: Subsystem revision 20050729
[4294668.314000] ACPI: Interpreter enabled
[4294668.314000] ACPI: Using IOAPIC for interrupt routing
[4294668.315000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.315000] PCI: Probing PCI hardware (bus 00)
[4294668.315000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.319000] Boot video device is 0000:01:00.0
[4294668.319000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.352000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.352000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[4294668.353000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294668.354000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294668.354000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294668.355000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294668.355000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294668.355000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294668.356000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294668.356000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294668.362000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.362000] pnp: PnP ACPI init
[4294668.369000] pnp: PnP ACPI: found 14 devices
[4294668.369000] PnPBIOS: Disabled by ACPI PNP
[4294668.369000] PCI: Using ACPI for IRQ routing
[4294668.369000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.388000] pnp: 00:00: ioport range 0x400-0x4bf could not be reserved
[4294668.389000] audit: initializing netlink socket (disabled)
[4294668.389000] audit: initialized
[4294668.389000] VFS: Disk quotas dquot_6.5.1
[4294668.389000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.389000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.389000] devfs: boot_options: 0x0
[4294668.389000] Initializing Cryptographic API
[4294668.389000] isapnp: Scanning for PnP cards...
[4294668.742000] isapnp: No Plug & Play device found
[4294668.758000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294668.760000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.760000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.760000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.761000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.761000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.762000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.762000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.763000] io scheduler noop registered
[4294668.763000] io scheduler anticipatory registered
[4294668.763000] io scheduler deadline registered
[4294668.763000] io scheduler cfq registered
[4294668.763000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.763000] NET: Registered protocol family 2
[4294668.772000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.772000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294668.772000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.772000] TCP: Hash tables configured (established 32768 bind 32768)
[4294668.772000] NET: Registered protocol family 8
[4294668.772000] NET: Registered protocol family 20
[4294668.772000] ACPI wakeup devices: 
[4294668.772000] SLPB PCI0 HUB0 USB0 USB1 MODM UAR1 UAR2 
[4294668.772000] ACPI: (supports S0 S1 S4 S5)
[4294668.773000] Freeing unused kernel memory: 168k freed
[4294668.786000] vga16fb: initializing
[4294668.786000] vga16fb: mapped to 0xc00a0000
[4294668.907000] Console: switching to colour frame buffer device 80x30
[4294668.907000] fb0: VGA16 VGA frame buffer device
[4294668.919000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.045000] Capability LSM initialized
[4294670.055000] NET: Registered protocol family 1
[4294670.065000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.065000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.065000] ACPI: bus type ide registered
[4294670.073000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294670.073000] ICH2: chipset revision 5
[4294670.073000] ICH2: not 100% native mode: will probe irqs later
[4294670.073000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294670.073000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294670.073000] Probing IDE interface ide0...
[4294670.337000] hda: ST3120026A, ATA DISK drive
[4294670.592000] hdb: ST380021A, ATA DISK drive
[4294670.643000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294670.643000] Probing IDE interface ide1...
[4294671.315000] hdc: SONY DVD RW DRU-510A, ATAPI CD/DVD-ROM drive
[4294672.029000] hdd: LITE-ON LTR-52246S, ATAPI CD/DVD-ROM drive
[4294672.080000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.080000] Probing IDE interface ide2...
[4294672.593000] Probing IDE interface ide3...
[4294673.105000] Probing IDE interface ide4...
[4294673.617000] Probing IDE interface ide5...
[4294674.132000] hda: max request size: 1024KiB
[4294674.132000] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.132000] hda: cache flushes supported
[4294674.133000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 >
[4294674.183000] hdb: max request size: 128KiB
[4294674.183000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294674.183000] hdb: cache flushes not supported
[4294674.183000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294674.202000] hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache
[4294674.202000] Uniform CD-ROM driver Revision: 3.20
[4294674.212000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294674.613000] Attempting manual resume
[4294674.613000] swsusp: Suspend partition has wrong signature?
[4294674.652000] usbcore: registered new driver usbfs
[4294674.652000] usbcore: registered new driver hub
[4294674.653000] USB Universal Host Controller Interface driver v2.2
[4294674.653000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
[4294674.653000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294674.653000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801BA/BAM USB (Hub #1)
[4294674.715000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294674.715000] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000b000
[4294674.715000] hub 1-0:1.0: USB hub found
[4294674.715000] hub 1-0:1.0: 2 ports detected
[4294674.718000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 23
[4294674.718000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294674.718000] uhci_hcd 0000:00:1f.4: Intel Corporation 82801BA/BAM USB (Hub #2)
[4294674.780000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294674.780000] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000b800
[4294674.780000] hub 2-0:1.0: USB hub found
[4294674.780000] hub 2-0:1.0: 2 ports detected
[4294674.821000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294674.821000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294674.821000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294674.844000] e100: eth0: e100_probe: addr 0xd8000000, irq 17, MAC addr 00:A0:C9:9A:76:85
[4294677.350000] ACPI: Fan [FAN] (on)
[4294677.353000] ACPI: CPU0 (power states: C1[C1])
[4294677.353000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294677.357000] ACPI: Thermal Zone [THRM] (44 C)
[4294677.571000] Attempting manual resume
[4294677.571000] swsusp: Suspend partition has wrong signature?
[4294677.584000] kjournald starting.  Commit interval 5 seconds
[4294677.584000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.542000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.742000] Adding 1494004k swap on /dev/hda6.  Priority:-1 extents:1
[4294681.992000] EXT3 FS on hda1, internal journal
[4294683.980000] parport: PnPBIOS parport detected.
[4294683.980000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294684.068000] lp0: using parport0 (interrupt-driven).
[4294684.097000] mice: PS/2 mouse device common for all mice
[4294684.167000] Linux agpgart interface v0.101 (c) Dave Jones
[4294684.195000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294684.198000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294684.198000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294684.198000] [fglrx] module loaded - fglrx 8.23.7 [Mar  6 2006] on minor 0
[4294684.480000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294685.065000] ts: Compaq touchscreen protocol output
[4294687.723000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294688.412000] cdrom: open failed.
[4294688.449000] cdrom: open failed.
[4294689.322000] kjournald starting.  Commit interval 5 seconds
[4294689.322000] EXT3 FS on hda5, internal journal
[4294689.322000] EXT3-fs: mounted filesystem with ordered data mode.
[4294689.358000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294689.418000] NTFS volume version 3.1.
[4294690.732000] agpgart: Detected an Intel i845 Chipset.
[4294690.751000] agpgart: AGP aperture is 64M @ 0xd0000000
[4294690.999000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.105000] shpchp: shpc_init : shpc_cap_offset == 0
[4294691.105000] shpchp: shpc_init : shpc_cap_offset == 0
[4294691.105000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.268000] hw_random: RNG not detected
[4294692.746000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294692.746000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294693.054000] intel8x0_measure_ac97_clock: measured 49308 usecs
[4294693.054000] intel8x0: clocking to 48000
[4294693.517000] Linux video capture interface: v1.00
[4294693.583000] bttv: Unknown symbol tveeprom_read
[4294693.584000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294693.676000] bttv: Unknown symbol tveeprom_read
[4294693.677000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294693.686000] bt878: Unknown symbol bttv_read_gpio
[4294693.686000] bt878: Unknown symbol bttv_write_gpio
[4294693.686000] bt878: Unknown symbol bttv_gpio_enable
[4294693.764000] bttv: Unknown symbol tveeprom_read
[4294693.765000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294693.845000] ACPI: PCI Interrupt 0000:02:03.1[A] -> GSI 23 (level, low) -> IRQ 23
[4294694.003000] bttv: Unknown symbol tveeprom_read
[4294694.004000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294694.004000] bt878: Unknown symbol bttv_read_gpio
[4294694.004000] bt878: Unknown symbol bttv_write_gpio
[4294694.004000] bt878: Unknown symbol bttv_gpio_enable
[4294694.237000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294695.955000] Real Time Clock Driver v1.12
[4294696.047000] input: PC Speaker
[4294696.150000] Floppy drive(s): fd0 is 1.44M
[4294696.165000] FDC 0 is a post-1991 82077
[4294698.630000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294698.660000] NET: Registered protocol family 17
[4294747.401000] ACPI: Power Button (FF) [PWRF]
[4294747.401000] ACPI: Power Button (CM) [PWRB]
[4294747.402000] ACPI: Sleep Button (CM) [SLPB]
[4294747.499000] ibm_acpi: ec object not found
[4294751.227000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294751.227000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294751.227000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294751.227000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294751.228000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294751.228000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294751.228000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294751.228000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294751.238000] [fglrx] free  AGP = 54800384
[4294751.238000] [fglrx] max   AGP = 54800384
[4294751.238000] [fglrx] free  LFB = 116002816
[4294751.238000] [fglrx] max   LFB = 116002816
[4294751.238000] [fglrx] free  Inv = 0
[4294751.238000] [fglrx] max   Inv = 0
[4294751.238000] [fglrx] total Inv = 0
[4294751.238000] [fglrx] total TIM = 0
[4294751.238000] [fglrx] total FB  = 0
[4294751.238000] [fglrx] total AGP = 16384
[4294754.593000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294754.593000] apm: overridden by ACPI.
[4294756.244000] Bluetooth: Core ver 2.7
[4294756.244000] NET: Registered protocol family 31
[4294756.244000] Bluetooth: HCI device and connection manager initialized
[4294756.244000] Bluetooth: HCI socket layer initialized
[4294756.256000] Bluetooth: L2CAP ver 2.7
[4294756.256000] Bluetooth: L2CAP socket layer initialized
[4294756.302000] Bluetooth: RFCOMM ver 1.5
[4294756.302000] Bluetooth: RFCOMM socket layer initialized
[4294756.302000] Bluetooth: RFCOMM TTY layer initialized
[4294765.705000] NET: Registered protocol family 10
[4294765.705000] Disabled Privacy Extensions on device c031eb40(lo)
[4294765.706000] IPv6 over IPv4 tunneling driver
[4294776.636000] eth0: no IPv6 routers present

```

**glxinfo**

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float, 
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5695 (8.23.7)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, 
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers, 
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object, 
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None

```

**xvinfo**

```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 115
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
    number of attributes: 12
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

```

---

### Post by RoboJ1M on 2006-03-30
Anybody?
The drivers appear to be loaded.
fgl_glxgears --info says 500fps.

But video just says NOOOOO!

Thanks,

J1M.

---

### Post by RoboJ1M on 2006-03-31
How about does anybody know where else I could go to ask this question? Somewhere authorative on Ati + Xv + GNOME?

Thanks,

J1M.

---

### Post by Lord Illidan on 2006-03-31
I don't think OpenGl is installed correctly, 500 fps doesn't cut it.

I think,  if you are really desperate, you should get an NVIDIA card.

---

### Post by RoboJ1M on 2006-03-31
I'm not desperate as such.
I just don't want to go too much further until I have really fundemental things like video overlay working.

I've just found out about fgl_glxinfo, that's the next thing I can post I guess.

What I don't get is if it's not working, why is nothing going *BANG*?

I would have expected a rash of errors.

Maybe it's because I installed the Ubuntu version of fglrx and then replaced it with the latest version?

J1M.

---

### Post by RoboJ1M on 2006-03-31
Another thing I notice while installing the latest ATI drivers:

It popped up warnings that the source in /usr/src/linux appeared to be not configured.

Could that mean anything?

Thanks,

J1M.

---

### Post by Lord Illidan on 2006-03-31
[QUOTE=RoboJ1M]I'm not desperate as such.
I just don't want to go too much further until I have really fundemental things like video overlay working.

I've just found out about fgl_glxinfo, that's the next thing I can post I guess.

What I don't get is if it's not working, why is nothing going *BANG*?

I would have expected a rash of errors.

Maybe it's because I installed the Ubuntu version of fglrx and then replaced it with the latest version?

J1M.[/QUOTE]

Try this howto : [https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29)

---

### Post by RoboJ1M on 2006-03-31
Brilliant!

I'll try that this weekend, as well as dumping the kernel source I have hanging about for something else I was doing.

That should get rid of the unconfigured kernel source warnings.

Further to that, there is also a detailed HOWTO over at Rage3D I found.

Including this:

> There's a script:
/usr/share/fglrx/fglrx-uninstall.sh

Haven't used it though.

Or you can delete /lib/modules/fglrx, and stuff in /usr, search with:

find /usr | grep fglrx

Which might be handy to uninstall the junk I've got in there at the moment.

Maybe.... ><;;

Thanks,

J1M.

---

