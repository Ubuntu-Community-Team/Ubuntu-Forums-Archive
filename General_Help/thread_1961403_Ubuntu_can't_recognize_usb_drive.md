---
title: "Ubuntu can't recognize usb drive"
date: 2012-04-19
forum: General Help
---

### Post by hemoali on 2012-04-19
10 can't read the usb storage only (that means usb Bluetooth and usb keyboard usb printer are recognized well)
why ??
when I use 

   ```
 hemoali@Ibrahim-PC:~$ sudo fdisk -l
    [sudo] password for hemoali: 
    
    Disk /dev/sda: 40.0 GB, 40020664320 bytes
    255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x0008bca1
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *        2048    76089343    38043648   83  Linux
    /dev/sda2        76091390    78163967     1036289    5  Extended
    /dev/sda5        76091392    78163967     1036288   82  Linux swap / Solaris
    hemoali@Ibrahim-PC:~$ 

```
It doesn't show up my flash drive ??!!!

when I connect the flash and use 

   ```
 hemoali@Ibrahim-PC:~$ lsusb
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
    Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
    ***Bus 001 Device 008: ID 3538:0059 Power Quotient International Co., Ltd*** 
```
the bold one is my flash
if I removed it look

    ```
hemoali@Ibrahim-PC:~$ lsusb
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
    Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
```

also dmesg command output 

    ```
[    0.183129] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
    [    0.183173] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
    [    0.183217] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
    [    0.183262] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
    [    0.183355] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
    [    0.183364] vgaarb: loaded
    [    0.183366] vgaarb: bridge control possible 0000:00:02.0
    [    0.183578] SCSI subsystem initialized
    [    0.183645] libata version 3.00 loaded.
    [    0.183691] usbcore: registered new interface driver usbfs
    [    0.183701] usbcore: registered new interface driver hub
    [    0.183727] usbcore: registered new device driver usb
    [    0.183813] PCI: Using ACPI for IRQ routing
    [    0.189857] PCI: pci_cache_line_size set to 64 bytes
    [    0.189919] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
    [    0.189922] reserve RAM buffer: 000000007f5e0000 - 000000007fffffff 
    [    0.190036] NetLabel: Initializing
    [    0.190039] NetLabel:  domain hash size = 128
    [    0.190040] NetLabel:  protocols = UNLABELED CIPSOv4
    [    0.190051] NetLabel:  unlabeled traffic allowed by default
    [    0.190097] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
    [    0.190102] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
    [    0.190106] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
    [    0.200088] Switching to clocksource hpet
    [    0.203868] Switched to NOHz mode on CPU #0
    [    0.203930] Switched to NOHz mode on CPU #1
    [    0.207160] AppArmor: AppArmor Filesystem Enabled
    [    0.207195] pnp: PnP ACPI init
    [    0.207213] ACPI: bus type pnp registered
    [    0.207309] pnp 00:00: [bus 00-ff]
    [    0.207312] pnp 00:00: [io  0x0cf8-0x0cff]
    [    0.207314] pnp 00:00: [io  0x0000-0x0cf7 window]
    [    0.207316] pnp 00:00: [io  0x0d00-0xffff window]
    [    0.207318] pnp 00:00: [mem 0x000a0000-0x000bffff window]
    [    0.207320] pnp 00:00: [mem 0x000c0000-0x000dffff window]
    [    0.207323] pnp 00:00: [mem 0x7f600000-0xfebfffff window]
    [    0.207393] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
    [    0.207457] pnp 00:01: [io  0x0010-0x001f]
    [    0.207459] pnp 00:01: [io  0x0022-0x003f]
    [    0.207460] pnp 00:01: [io  0x0044-0x005f]
    [    0.207462] pnp 00:01: [io  0x0062-0x0063]
    [    0.207464] pnp 00:01: [io  0x0065-0x006f]
    [    0.207466] pnp 00:01: [io  0x0074-0x007f]
    [    0.207468] pnp 00:01: [io  0x0091-0x0093]
    [    0.207469] pnp 00:01: [io  0x00a2-0x00bf]
    [    0.207471] pnp 00:01: [io  0x00e0-0x00ef]
    [    0.207473] pnp 00:01: [io  0x04d0-0x04d1]
    [    0.207475] pnp 00:01: [io  0x0290-0x029f]
    [    0.207477] pnp 00:01: [io  0x0800-0x087f]
    [    0.207478] pnp 00:01: [io  0x0290-0x0294]
    [    0.207480] pnp 00:01: [io  0x0880-0x088f]
    [    0.207534] system 00:01: [io  0x04d0-0x04d1] has been reserved
    [    0.207536] system 00:01: [io  0x0290-0x029f] has been reserved
    [    0.207539] system 00:01: [io  0x0800-0x087f] has been reserved
    [    0.207541] system 00:01: [io  0x0290-0x0294] has been reserved
    [    0.207543] system 00:01: [io  0x0880-0x088f] has been reserved
    [    0.207546] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
    [    0.207558] pnp 00:02: [dma 4]
    [    0.207560] pnp 00:02: [io  0x0000-0x000f]
    [    0.207561] pnp 00:02: [io  0x0080-0x0090]
    [    0.207563] pnp 00:02: [io  0x0094-0x009f]
    [    0.207565] pnp 00:02: [io  0x00c0-0x00df]
    [    0.207593] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
    [    0.207638] pnp 00:03: [irq 0 disabled]
    [    0.207648] pnp 00:03: [irq 8]
    [    0.207650] pnp 00:03: [mem 0xfed00000-0xfed003ff]
    [    0.207677] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
    [    0.207702] pnp 00:04: [io  0x0070-0x0073]
    [    0.207728] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
    [    0.207737] pnp 00:05: [io  0x0061]
    [    0.207766] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
    [    0.207775] pnp 00:06: [io  0x00f0-0x00ff]
    [    0.207779] pnp 00:06: [irq 13]
    [    0.207805] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
    [    0.207908] pnp 00:07: [io  0x03f0-0x03f5]
    [    0.207910] pnp 00:07: [io  0x03f7]
    [    0.207915] pnp 00:07: [irq 6]
    [    0.207917] pnp 00:07: [dma 2]
    [    0.207955] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
    [    0.208138] pnp 00:08: [io  0x03f8-0x03ff]
    [    0.208143] pnp 00:08: [irq 4]
    [    0.208198] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
    [    0.208363] pnp 00:09: [io  0x0378-0x037f]
    [    0.208368] pnp 00:09: [irq 7]
    [    0.208411] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
    [    0.208491] pnp 00:0a: [io  0x0060]
    [    0.208493] pnp 00:0a: [io  0x0064]
    [    0.208498] pnp 00:0a: [irq 1]
    [    0.208526] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
    [    0.208554] pnp 00:0b: [io  0x0400-0x04cf]
    [    0.208595] system 00:0b: [io  0x0400-0x04cf] has been reserved
    [    0.208598] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
    [    0.208772] pnp 00:0c: [mem 0xc0000000-0xcfffffff]
    [    0.208821] system 00:0c: [mem 0xc0000000-0xcfffffff] has been reserved
    [    0.208824] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
    [    0.208963] pnp 00:0d: [mem 0x000cb400-0x000cbfff]
    [    0.208965] pnp 00:0d: [mem 0x000f0000-0x000f7fff]
    [    0.208967] pnp 00:0d: [mem 0x000f8000-0x000fbfff]
    [    0.208969] pnp 00:0d: [mem 0x000fc000-0x000fffff]
    [    0.208971] pnp 00:0d: [mem 0x7f5e0000-0x7f5fffff]
    [    0.208973] pnp 00:0d: [mem 0x00000000-0x0009ffff]
    [    0.208975] pnp 00:0d: [mem 0x00100000-0x7f5dffff]
    [    0.208977] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
    [    0.208979] pnp 00:0d: [mem 0xfed13000-0xfed1dfff]
    [    0.208981] pnp 00:0d: [mem 0xfed20000-0xfed8ffff]
    [    0.208983] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
    [    0.208984] pnp 00:0d: [mem 0xffb00000-0xffb7ffff]
    [    0.208986] pnp 00:0d: [mem 0xfff00000-0xffffffff]
    [    0.208988] pnp 00:0d: [mem 0x000e0000-0x000effff]
    [    0.209044] system 00:0d: [mem 0x000cb400-0x000cbfff] has been reserved
    [    0.209047] system 00:0d: [mem 0x000f0000-0x000f7fff] could not be reserved
    [    0.209050] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
    [    0.209052] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
    [    0.209055] system 00:0d: [mem 0x7f5e0000-0x7f5fffff] could not be reserved
    [    0.209057] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
    [    0.209060] system 00:0d: [mem 0x00100000-0x7f5dffff] could not be reserved
    [    0.209063] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
    [    0.209065] system 00:0d: [mem 0xfed13000-0xfed1dfff] has been reserved
    [    0.209068] system 00:0d: [mem 0xfed20000-0xfed8ffff] has been reserved
    [    0.209070] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
    [    0.209073] system 00:0d: [mem 0xffb00000-0xffb7ffff] has been reserved
    [    0.209075] system 00:0d: [mem 0xfff00000-0xffffffff] has been reserved
    [    0.209078] system 00:0d: [mem 0x000e0000-0x000effff] has been reserved
    [    0.209081] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
    [    0.209098] pnp 00:0e: [mem 0xffb80000-0xffbfffff]
    [    0.209136] pnp 00:0e: Plug and Play ACPI device, IDs INT0800 (active)
    [    0.209142] pnp: PnP ACPI: found 15 devices
    [    0.209143] ACPI: ACPI bus type pnp unregistered
    [    0.209147] PnPBIOS: Disabled by ACPI PNP
    [    0.245129] PCI: max bus depth: 1 pci_try_num: 2
    [    0.245168] pci 0000:00:1c.0: BAR 14: assigned [mem 0x7f600000-0x7f7fffff]
    [    0.245172] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7f800000-0x7f9fffff 64bit pref]
    [    0.245174] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
    [    0.245178] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
    [    0.245182] pci 0000:00:1c.0:   bridge window [mem 0x7f600000-0x7f7fffff]
    [    0.245186] pci 0000:00:1c.0:   bridge window [mem 0x7f800000-0x7f9fffff 64bit pref]
    [    0.245193] pci 0000:02:00.0: BAR 6: assigned [mem 0xe1120000-0xe113ffff pref]
    [    0.245196] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
    [    0.245198] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
    [    0.245203] pci 0000:00:1c.1:   bridge window [mem 0xe0000000-0xe0ffffff]
    [    0.245207] pci 0000:00:1c.1:   bridge window [mem 0xe1100000-0xe11fffff 64bit pref]
    [    0.245213] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
    [    0.245216] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
    [    0.245221] pci 0000:00:1e.0:   bridge window [mem disabled]
    [    0.245224] pci 0000:00:1e.0:   bridge window [mem pref disabled]
    [    0.245253] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
    [    0.245258] pci 0000:00:1c.0: setting latency timer to 64
    [    0.245268] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
    [    0.245272] pci 0000:00:1c.1: setting latency timer to 64
    [    0.245278] pci 0000:00:1e.0: setting latency timer to 64
    [    0.245281] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
    [    0.245284] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
    [    0.245286] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
    [    0.245288] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
    [    0.245290] pci_bus 0000:00: resource 8 [mem 0x7f600000-0xfebfffff]
    [    0.245293] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
    [    0.245295] pci_bus 0000:01: resource 1 [mem 0x7f600000-0x7f7fffff]
    [    0.245297] pci_bus 0000:01: resource 2 [mem 0x7f800000-0x7f9fffff 64bit pref]
    [    0.245300] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
    [    0.245302] pci_bus 0000:02: resource 1 [mem 0xe0000000-0xe0ffffff]
    [    0.245305] pci_bus 0000:02: resource 2 [mem 0xe1100000-0xe11fffff 64bit pref]
    [    0.245307] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
    [    0.245309] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
    [    0.245311] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
    [    0.245313] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
    [    0.245316] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
    [    0.245318] pci_bus 0000:03: resource 8 [mem 0x7f600000-0xfebfffff]
    [    0.245367] NET: Registered protocol family 2
    [    0.245440] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
    [    0.245674] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
    [    0.246149] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
    [    0.246399] TCP: Hash tables configured (established 131072 bind 65536)
    [    0.246401] TCP reno registered
    [    0.246405] UDP hash table entries: 512 (order: 2, 16384 bytes)
    [    0.246415] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
    [    0.246518] NET: Registered protocol family 1
    [    0.246543] pci 0000:00:02.0: Boot video device
    [    0.246641] PCI: CLS 32 bytes, default 64
    [    0.246958] audit: initializing netlink socket (disabled)
    [    0.246967] type=2000 audit(1334843863.240:1): initialized
    [    0.268435] highmem bounce pool size: 64 pages
    [    0.268440] HugeTLB registered 4 MB page size, pre-allocated 0 pages
    [    0.277598] VFS: Disk quotas dquot_6.5.2
    [    0.277669] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
    [    0.278314] fuse init (API version 7.16)
    [    0.278401] msgmni has been set to 1680
    [    0.278704] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
    [    0.278728] io scheduler noop registered
    [    0.278730] io scheduler deadline registered
    [    0.278742] io scheduler cfq registered (default)
    [    0.278840] pcieport 0000:00:1c.0: setting latency timer to 64
    [    0.278885] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
    [    0.278940] pcieport 0000:00:1c.1: setting latency timer to 64
    [    0.278975] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
    [    0.279049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
    [    0.279071] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
    [    0.279143] intel_idle: MWAIT substates: 0x22220
    [    0.279145] intel_idle: does not run on family 6 model 23
    [    0.279216] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
    [    0.279222] ACPI: Power Button [PWRB]
    [    0.279270] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
    [    0.279273] ACPI: Power Button [PWRF]
    [    0.279300] ACPI: acpi_idle registered with cpuidle
    [    0.280579] ERST: Table is not found!
    [    0.280652] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
    [    0.301010] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
    [    0.301157] isapnp: Scanning for PnP cards...
    [    0.413108] Freeing initrd memory: 13332k freed
    [    0.654027] isapnp: No Plug & Play device found
    [    0.708665] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
    [    0.708986] Linux agpgart interface v0.103
    [    0.709065] agpgart-intel 0000:00:00.0: Intel G33 Chipset
    [    0.709125] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
    [    0.709741] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
    [    0.709855] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
    [    0.710987] brd: module loaded
    [    0.711519] loop: module loaded
    [    0.711654] ata_piix 0000:00:1f.2: version 2.13
    [    0.711678] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
    [    0.711683] ata_piix 0000:00:1f.2: MAP [ IDE IDE P1 P3 ]
    [    0.711715] ata_piix 0000:00:1f.2: setting latency timer to 64
    [    0.711994] scsi0 : ata_piix
    [    0.712080] scsi1 : ata_piix
    [    0.712542] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
    [    0.712544] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
    [    0.712874] Fixed MDIO Bus: probed
    [    0.712896] PPP generic driver version 2.4.2
    [    0.712936] tun: Universal TUN/TAP device driver, 1.6
    [    0.712937] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
    [    0.713008] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
    [    0.713027] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
    [    0.713040] ehci_hcd 0000:00:1d.7: setting latency timer to 64
    [    0.713043] ehci_hcd 0000:00:1d.7: EHCI Host Controller
    [    0.713074] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
    [    0.713089] ehci_hcd 0000:00:1d.7: using broken periodic workaround
    [    0.716981] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
    [    0.716995] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe1284000
    [    0.732019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
    [    0.732226] hub 1-0:1.0: USB hub found
    [    0.732230] hub 1-0:1.0: 8 ports detected
    [    0.732296] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
    [    0.732307] uhci_hcd: USB Universal Host Controller Interface driver
    [    0.732326] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
    [    0.732331] uhci_hcd 0000:00:1d.0: setting latency timer to 64
    [    0.732334] uhci_hcd 0000:00:1d.0: UHCI Host Controller
    [    0.732364] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
    [    0.732386] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e100
    [    0.732487] hub 2-0:1.0: USB hub found
    [    0.732490] hub 2-0:1.0: 2 ports detected
    [    0.732545] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
    [    0.732551] uhci_hcd 0000:00:1d.1: setting latency timer to 64
    [    0.732554] uhci_hcd 0000:00:1d.1: UHCI Host Controller
    [    0.732589] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
    [    0.732618] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e200
    [    0.732717] hub 3-0:1.0: USB hub found
    [    0.732720] hub 3-0:1.0: 2 ports detected
    [    0.732778] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
    [    0.732783] uhci_hcd 0000:00:1d.2: setting latency timer to 64
    [    0.732786] uhci_hcd 0000:00:1d.2: UHCI Host Controller
    [    0.732817] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
    [    0.732845] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e300
    [    0.732946] hub 4-0:1.0: USB hub found
    [    0.732949] hub 4-0:1.0: 2 ports detected
    [    0.732999] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
    [    0.733004] uhci_hcd 0000:00:1d.3: setting latency timer to 64
    [    0.733007] uhci_hcd 0000:00:1d.3: UHCI Host Controller
    [    0.733035] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
    [    0.733064] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e400
    [    0.733164] hub 5-0:1.0: USB hub found
    [    0.733167] hub 5-0:1.0: 2 ports detected
    [    0.733272] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
    [    0.733274] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
    [    0.733434] serio: i8042 KBD port at 0x60,0x64 irq 1
    [    0.733518] mousedev: PS/2 mouse device common for all mice
    [    0.733636] rtc_cmos 00:04: RTC can wake from S4
    [    0.733719] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
    [    0.733741] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
    [    0.733821] device-mapper: uevent: version 1.0.3
    [    0.733892] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
    [    0.733919] EISA: Probing bus 0 at eisa.0
    [    0.733921] EISA: Cannot allocate resource for mainboard
    [    0.733922] Cannot allocate resource for EISA slot 1
    [    0.733924] Cannot allocate resource for EISA slot 2
    [    0.733926] Cannot allocate resource for EISA slot 3
    [    0.733928] Cannot allocate resource for EISA slot 4
    [    0.733929] Cannot allocate resource for EISA slot 5
    [    0.733931] Cannot allocate resource for EISA slot 6
    [    0.733932] Cannot allocate resource for EISA slot 7
    [    0.733934] Cannot allocate resource for EISA slot 8
    [    0.733936] EISA: Detected 0 cards.
    [    0.733943] cpufreq-nforce2: No nForce2 chipset.
    [    0.733946] cpuidle: using governor ladder
    [    0.733947] cpuidle: using governor menu
    [    0.733949] EFI Variables Facility v0.08 2004-May-17
    [    0.734214] TCP cubic registered
    [    0.734338] NET: Registered protocol family 10
    [    0.734887] NET: Registered protocol family 17
    [    0.734900] Registering the dns_resolver key type
    [    0.734919] Using IPI No-Shortcut mode
    [    0.734985] PM: Hibernation image not present or could not be loaded.
    [    0.734996] registered taskstats version 1
    [    0.744080]   Magic number: 8:236:989
    [    0.744166] rtc_cmos 00:04: setting system clock to 2012-04-19 13:57:44 UTC (1334843864)
    [    0.746268] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
    [    0.746271] EDD information not available.
    [    0.752923] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
    [    0.868385] ata2.01: NODEV after polling detection
    [    0.876376] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN00, max UDMA/100
    [    0.877631] ata1.01: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
    [    0.877636] ata1.01: 78165360 sectors, multi 16: LBA 
    [    0.892308] ata2.00: configured for UDMA/100
    [    0.893428] ata1.01: configured for UDMA/100
    [    0.893609] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
    [    0.893717] sd 0:0:1:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
    [    0.893739] sd 0:0:1:0: Attached scsi generic sg0 type 0
    [    0.893762] sd 0:0:1:0: [sda] Write Protect is off
    [    0.893765] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
    [    0.893784] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [    0.897490] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN00 PQ: 0 ANSI: 5
    [    0.901212] sr0: scsi3-mmc drive: 10x/10x writer dvd-ram cd/rw xa/form2 cdda tray
    [    0.901217] cdrom: Uniform CD-ROM driver Revision: 3.20
    [    0.901378] sr 1:0:0:0: Attached scsi CD-ROM sr0
    [    0.901428] sr 1:0:0:0: Attached scsi generic sg1 type 5
    [    0.940362]  sda: sda1 sda2 < sda5 >
    [    0.940701] sd 0:0:1:0: [sda] Attached SCSI disk
    [    0.940737] Freeing unused kernel memory: 696k freed
    [    0.940941] Write protecting the kernel text: 5344k
    [    0.940982] Write protecting the kernel read-only data: 2192k
    [    0.954910] udevd[85]: starting version 173
    [    1.006250] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
    [    1.006272] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
    [    1.006310] r8169 0000:02:00.0: setting latency timer to 64
    [    1.006367] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
    [    1.007082] r8169 0000:02:00.0: eth0: RTL8102e at 0xf8016000, 00:24:1d:93:88:d3, XID 14a00000 IRQ 42
    [    1.037579] Floppy drive(s): fd0 is 1.44M
    [    1.044034] usb 1-4: new high speed USB device number 2 using ehci_hcd
    [    1.055733] FDC 0 is a post-1991 82077
    [    1.181263] usbcore: registered new interface driver uas
    [    1.244018] Refined TSC clocksource calibration: 2499.940 MHz.
    [    1.244026] Switching to clocksource tsc
    [    1.632018] usb 4-1: new low speed USB device number 2 using uhci_hcd
    [    1.836398] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
    [    1.836498] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.2-1/input0
    [    1.836511] usbcore: registered new interface driver usbhid
    [    1.836512] usbhid: USB HID core driver
    [    2.056017] usb 4-2: new full speed USB device number 3 using uhci_hcd
    [    6.401563] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
    [    6.401566] EXT4-fs (sda1): write access will be enabled during recovery
    [    6.448548] EXT4-fs (sda1): recovery complete
    [    6.448700] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
    [   10.036584] udevd[302]: starting version 173
    [   12.583981] lp: driver loaded but no devices found
    [   13.288245] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
    [   13.526452] parport_pc 00:09: reported by Plug and Play ACPI
    [   13.526500] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
    [   13.536734] ppdev: user-space parallel port driver
    [   13.620239] lp0: using parport0 (interrupt-driven).
    [   13.669748] intel_rng: FWH not detected
    [   13.773266] leds_ss4200: no LED devices found
    [   14.378942] [drm] Initialized drm 1.1.0 20060810
    [   14.871279] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
    [   14.871285] i915 0000:00:02.0: setting latency timer to 64
    [   14.883160] i915 0000:00:02.0: irq 43 for MSI/MSI-X
    [   14.883167] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
    [   14.883168] [drm] Driver supports precise vblank timestamp query.
    [   14.883201] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
    [   14.898854] [drm] initialized overlay support
    [   14.969164] fbcon: inteldrmfb (fb0) is primary device
    [   14.969893] Console: switching to colour frame buffer device 170x48
    [   14.969918] fb0: inteldrmfb frame buffer device
    [   14.969919] drm: registered panic notifier
    [   14.969977] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
    [   16.284302] Bluetooth: Core ver 2.16
    [   16.284349] NET: Registered protocol family 31
    [   16.284351] Bluetooth: HCI device and connection manager initialized
    [   16.284354] Bluetooth: HCI socket layer initialized
    [   16.284355] Bluetooth: L2CAP socket layer initialized
    [   16.284596] Bluetooth: SCO socket layer initialized
    [   16.528780] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
    [   16.528964] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
    [   16.528992] HDA Intel 0000:00:1b.0: setting latency timer to 64
    [   17.575142] Bluetooth: Generic Bluetooth USB driver ver 0.6
    [   17.575667] usbcore: registered new interface driver btusb
    [   18.248107] type=1400 audit(1334843882.000:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=717 comm="apparmor_parser"
    [   18.248116] type=1400 audit(1334843882.000:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
    [   18.248463] type=1400 audit(1334843882.000:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=717 comm="apparmor_parser"
    [   18.248474] type=1400 audit(1334843882.000:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
    [   18.248684] type=1400 audit(1334843882.000:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=717 comm="apparmor_parser"
    [   18.248698] type=1400 audit(1334843882.000:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=716 comm="apparmor_parser"
    [   24.145108] init: failsafe main process (815) killed by TERM signal
    [   31.075259] type=1400 audit(1334843894.824:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=921 comm="apparmor_parser"
    [   31.075623] type=1400 audit(1334843894.824:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=921 comm="apparmor_parser"
    [   31.075848] type=1400 audit(1334843894.824:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=921 comm="apparmor_parser"
    [   31.193780] type=1400 audit(1334843894.944:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=918 comm="apparmor_parser"
    [   31.194215] type=1400 audit(1334843894.944:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=918 comm="apparmor_parser"
    [   31.317943] type=1400 audit(1334843895.068:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=920 comm="apparmor_parser"
    [   31.440193] type=1400 audit(1334843895.192:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=926 comm="apparmor_parser"
    [   31.440901] type=1400 audit(1334843895.192:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=926 comm="apparmor_parser"
    [   31.444270] type=1400 audit(1334843895.196:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=927 comm="apparmor_parser"
    [   31.444716] type=1400 audit(1334843895.196:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=927 comm="apparmor_parser"
    [   35.568309] r8169 0000:02:00.0: eth0: link down
    [   35.568314] r8169 0000:02:00.0: eth0: link down
    [   35.568595] ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   35.903821] init: apport pre-start process (983) terminated with status 1
    [   35.907059] init: apport post-stop process (1021) terminated with status 1
    [   37.253232] r8169 0000:02:00.0: eth0: link up
    [   37.253465] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
    [   41.792700] vboxdrv: Found 2 processor cores.
    [   41.792795] vboxdrv: fAsync=0 offMin=0x2a3 offMax=0x186a
    [   41.792844] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
    [   41.792846] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000).
    [   44.318956] vboxpci: IOMMU not found (not registered)
    [   47.536010] eth0: no IPv6 routers present
    [   48.068434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [   48.068437] Bluetooth: BNEP filters: protocol multicast
    [   48.646352] Bluetooth: RFCOMM TTY layer initialized
    [   48.646358] Bluetooth: RFCOMM socket layer initialized
    [   48.646360] Bluetooth: RFCOMM ver 1.11
    [   62.326114] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
    [   65.350543] init: plymouth-stop pre-start process (1580) terminated with status 1
    [   65.910066] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
    [  215.749862] usb 1-4: USB disconnect, device number 2
    [  397.464067] usb 4-2: USB disconnect, device number 3
    [  397.464917] btusb_intr_complete: hci0 urb f6f7f600 failed to resubmit (19)
    [  397.464932] btusb_bulk_complete: hci0 urb f6f7f280 failed to resubmit (19)
    [  397.465920] btusb_bulk_complete: hci0 urb f6f7fe80 failed to resubmit (19)
    [  397.465957] btusb_send_frame: hci0 urb f1248980 submission failed
    [  406.756027] usb 3-2: new full speed USB device number 2 using uhci_hcd
    [  406.900063] usb 3-2: device descriptor read/all, error -71
    [  407.012042] usb 3-2: new full speed USB device number 3 using uhci_hcd
    [  420.440033] usb 1-6: new high speed USB device number 6 using ehci_hcd
    [  675.472065] usb 3-2: USB disconnect, device number 3
    [  675.473080] btusb_intr_complete: hci0 urb f6f7f200 failed to resubmit (19)
    [  675.473095] btusb_bulk_complete: hci0 urb f6f7f380 failed to resubmit (19)
    [  675.474081] btusb_bulk_complete: hci0 urb f6f7f480 failed to resubmit (19)
    [  675.474118] btusb_send_frame: hci0 urb f6d47b80 submission failed
    [  694.761689] usb 1-6: USB disconnect, device number 6
    [  703.488025] usb 4-2: new full speed USB device number 4 using uhci_hcd
    [  703.631961] usb 4-2: device descriptor read/all, error -71
    [  703.744028] usb 4-2: new full speed USB device number 5 using uhci_hcd
    [  710.012032] usb 1-4: new high speed USB device number 8 using ehci_hcd
    [  717.995878] usb 1-4: USB disconnect, device number 8
    [  730.812039] usb 1-4: new high speed USB device number 9 using ehci_hcd
    hemoali@Ibrahim-PC:~$
```


what is the solution ?/

---

### Post by matt_symes on 2012-04-20
Hi
> 
[  406.756027] usb 3-2: new full speed USB device number 2 using uhci_hcd
[  406.900063] usb 3-2: device descriptor read/all, error -71
[  407.012042] usb 3-2: new full speed USB device number 3 using uhci_hcd
[  420.440033] usb 1-6: new high speed USB device number 6 using ehci_hcd
[  675.472065] usb 3-2: USB disconnect, device number 3This is the error (from the kernel sources); a protocol error.

```
#define EPROTO          71      /* Protocol error */
```Are you using an external HUB ? Have you tried different ports ? Have you plugged the device into a USB2 port using the bound ehci_hcd driver  ?

uhci_hcd. Is the device even a USB2 device ?

Have you tried the old scheme for USB devices ?

Make sure the device is not plugged in and from the terminal

```
echo Y > sudo tee /sys/module/usbcore/parameters/old_scheme_first
```Plug the device back in. Is the device recognised ?

Kind regards

---

