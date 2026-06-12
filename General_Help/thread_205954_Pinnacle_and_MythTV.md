---
title: "Pinnacle and MythTV"
date: 2006-06-29
forum: General Help
---

### Post by Thanatios on 2006-06-29
Hello everyone :)
First I want to say, that I have been using Ubuntu for the past 3 days, and I can say that its really nice.

Well I today desided to install my TV card on Ubuntu, and so I started searching around and found a guide for MythTV. I don't know if this program is recommended or not, but thats the only program I know about right now.

I myself have a Pinnacle Studio PCTV video card, its 3 years old by now, but still works like a charm.
Well so I have installed MythTV. But how do I know what type of card I have? And how do I find out the Video Source name? Is there a guide that ectually explains what to put in at the setup/configuration? If so, can someone help me then with this.

Also a question: How do you know, if Ubuntu detected the TVCard or not?

I would be thankfull.
Cheers :)

---

### Post by MonkeyNet on 2006-06-29
Hey there,

I found the best Ubuntu guide for mythtv was [here]("http://hyams.webhop.net/mythtv/myth_ubuntu.html"). Because the pinnacle card will not work with IVTV drivers, you can skip this step altogether. Also, don't worry about the nVidia drivers if you don't have one :)

If you want to know if Ubuntu has already detected your card, you can use the System -> Administration -> Device Manager. Go through your devices and see if you can find the card. Mine for example is a CX23880 and the device for video is /dev/video0.

I would suggest installing tvtime (sudo apt-get install tvtime). This way you can test your TV Card and see if it is working.

The guides are very helpful. Let me know if you have problems.

Cheers,

Andrew

---

### Post by Thanatios on 2006-06-29
Thank you for your reply! :D 

Looks like I get no signal at TVTime. =/
I myself have 2 video devices: A Digital Camera and a TV Card (Pinnacle PCTV).
And both dont work. Maybe I have to install some kind of Videodrivers? Any suggestions?

Thanks in advance

---

### Post by MonkeyNet on 2006-06-29
OK. When you go into the device manager, do you find the TV tuner card?

If you change to the advanced tab, and scroll through sub menu on the left under the tv card, you will see whether the device is mapped to either /dev/video0 or /dev/video1, etc.

In my case I have two TV cards, so the one I use for most TV is /dev/video0

In /etc/tvtime/tvtime.xml, i changed the following line

```
<option name="V4LDevice" value="/dev/video0">
```

This means that when I start TVTime, it maps to the video0 device. See how you go with this for now

---

### Post by Thanatios on 2006-06-29
Well I looked trough it all. And this is what I see at device manager:
[http://img121.imageshack.us/img121/2350/video6az.png](http://img121.imageshack.us/img121/2350/video6az.png)

It just says Video Device. So I guess it does need some kind of program to use it, or something like that. :-k

---

### Post by MonkeyNet on 2006-06-29
[QUOTE=Thanatios]Well I looked trough it all. And this is what I see at device manager:
[http://img121.imageshack.us/img121/2350/video6az.png](http://img121.imageshack.us/img121/2350/video6az.png)

It just says Video Device. So I guess it does need some kind of program to use it, or something like that. :-k[/QUOTE]

Right. From the link it appears that your capture card is set to /dev/video0. The one that you have highlighted in the screenshoot is /dev/vbi0, but if you look at the second one down, you will see it should be /dev/video0.

Edit the tvtime.xml file and make sure that the device is set to /dev/video0

If it is, can you post a dmesg output for bttv
```
dmesg | grep bttv
```

That should tell me whether the card is functioning properly

---

### Post by vigleik on 2006-06-29
Mythtv is a great program, though a little bit hard to set up. But it will NOT help you get your TV card working. In fact, forget about mythtv until after you've figured out how load the correct driver for your card and manage to watch TV some other way. I don't know about your card, so I can't tell you exactly how you should do that, but it looks like some of the above posts have some good advice.

Once your card is working you can proceed with the installation of mythtv. There are several good howtos on the forum. Anyway, making your TV card work is the hardest part and it has to be done first.

Vigleik

---

### Post by Thanatios on 2006-06-30
well it looks like the tvtime.xml is read-only. And I cant change the permissions =/
It just keeps saying: You do not have permission to write to this folder.
While I'm on my Root account. Very weard =/

---

### Post by MonkeyNet on 2006-06-30
[QUOTE=Thanatios]well it looks like the tvtime.xml is read-only. And I cant change the permissions =/
It just keeps saying: You do not have permission to write to this folder.
While I'm on my Root account. Very weard =/[/QUOTE]

Make sure that tvtime is not running when you edit the file. Also the permissions on the files should be as follows;

-rw-r--r--   1 root root 17278 2006-06-30 22:16 tvtime.xml

Have you tried doing the dmesg?

---

### Post by Thanatios on 2006-06-30
The Video Device below the one I showed you is video1. So thats what I changed.

 <!-- This sets the default capture device to use. -->
  <option name="V4LDevice" value="/dev/video1"/>

But it still gives no signal. This is the dmesg:
```
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fbac0
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa000
[17179569.184000] ACPI: RSDT (v001 AMIINT INTEL845 0x00000010 MSFT 0x00000097) @ 0x3fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT INTEL845 0x00000011 MSFT 0x00000097) @ 0x3fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT INTEL845 0x00000009 MSFT 0x00000097) @ 0x3fff00c0
[17179569.184000] ACPI: DSDT (v001  INTEL   P4I45E 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda6 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3074.206 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.284000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.284000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179573.312000] Memory: 1028816k/1048512k available (1976k kernel code, 18932k reserved, 606k data, 288k init, 131008k highmem)
[17179573.312000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.392000] Calibrating delay using timer specific routine.. 6153.24 BogoMIPS (lpj=12306492)
[17179573.392000] Security Framework v1.0.0 initialized
[17179573.392000] SELinux:  Disabled at boot.
[17179573.392000] Mount-cache hash table entries: 512
[17179573.392000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179573.392000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179573.392000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179573.392000] CPU: L2 cache: 512K
[17179573.392000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179573.392000] mtrr: v2.0 (20020519)
[17179573.392000] CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
[17179573.392000] Enabling fast FPU save and restore... done.
[17179573.392000] Enabling unmasked SIMD FPU exception support... done.
[17179573.392000] Checking 'hlt' instruction... OK.
[17179573.408000] checking if image is initramfs... it is
[17179573.856000] Freeing initrd memory: 6613k freed
[17179573.872000] ACPI: Looking for DSDT ... not found!
[17179573.876000] ENABLING IO-APIC IRQs
[17179573.876000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179574.016000] NET: Registered protocol family 16
[17179574.016000] EISA bus registered
[17179574.016000] ACPI: bus type pci registered
[17179574.020000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=3
[17179574.020000] PCI: Using configuration type 1
[17179574.020000] ACPI: Subsystem revision 20051216
[17179574.028000] ACPI: Interpreter enabled
[17179574.028000] ACPI: Using IOAPIC for interrupt routing
[17179574.028000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.028000] PCI: Probing PCI hardware (bus 00)
[17179574.032000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179574.032000] PCI quirk: region 0400-043f claimed by ICH4 GPIO
[17179574.032000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.032000] Boot video device is 0000:01:00.0
[17179574.032000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.032000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.032000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHB._PRT]
[17179574.036000] ACPI: Power Resource [URP1] (off)
[17179574.036000] ACPI: Power Resource [URP2] (off)
[17179574.036000] ACPI: Power Resource [FDDP] (off)
[17179574.036000] ACPI: Power Resource [LPTP] (off)
[17179574.036000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.036000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179574.036000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179574.036000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179574.036000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.036000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.036000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.036000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179574.036000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.036000] pnp: PnP ACPI init
[17179574.040000] pnp: PnP ACPI: found 10 devices
[17179574.040000] PnPBIOS: Disabled by ACPI PNP
[17179574.040000] PCI: Using ACPI for IRQ routing
[17179574.040000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.044000] PCI: Bridge: 0000:00:01.0
[17179574.044000]   IO window: disabled.
[17179574.044000]   MEM window: ddd00000-dfdfffff
[17179574.044000]   PREFETCH window: bdb00000-ddafffff
[17179574.044000] PCI: Bridge: 0000:00:1e.0
[17179574.044000]   IO window: c000-cfff
[17179574.044000]   MEM window: dfe00000-dfefffff
[17179574.044000]   PREFETCH window: ddb00000-ddbfffff
[17179574.044000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.044000] audit: initializing netlink socket (disabled)
[17179574.044000] audit(1151677884.044:1): initialized
[17179574.044000] highmem bounce pool size: 64 pages
[17179574.044000] VFS: Disk quotas dquot_6.5.1
[17179574.044000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.044000] Initializing Cryptographic API
[17179574.044000] io scheduler noop registered
[17179574.044000] io scheduler anticipatory registered
[17179574.044000] io scheduler deadline registered
[17179574.044000] io scheduler cfq registered
[17179574.044000] isapnp: Scanning for PnP cards...
[17179574.400000] isapnp: No Plug & Play device found
[17179574.412000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.412000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.412000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.412000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.412000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.412000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.416000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.416000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.416000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.416000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.416000] mice: PS/2 mouse device common for all mice
[17179574.416000] EISA: Probing bus 0 at eisa.0
[17179574.416000] EISA: Detected 0 cards.
[17179574.416000] NET: Registered protocol family 2
[17179574.452000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.452000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179574.452000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.452000] TCP: Hash tables configured (established 262144 bind 65536)
[17179574.452000] TCP reno registered
[17179574.452000] TCP bic registered
[17179574.452000] NET: Registered protocol family 1
[17179574.452000] NET: Registered protocol family 8
[17179574.452000] NET: Registered protocol family 20
[17179574.452000] Using IPI Shortcut mode
[17179574.452000] ACPI wakeup devices:
[17179574.452000] USB1 USB2 USB3 EHCI ICHB PS2K UAR1  MC9
[17179574.452000] ACPI: (supports S0 S1 S4 S5)
[17179574.452000] Freeing unused kernel memory: 288k freed
[17179574.496000] vga16fb: initializing
[17179574.496000] vga16fb: mapped to 0xc00a0000
[17179574.640000] Console: switching to colour frame buffer device 80x25
[17179574.640000] fb0: VGA16 VGA frame buffer device
[17179574.732000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.760000] Capability LSM initialized
[17179575.792000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179576.316000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179576.316000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179576.316000] ICH4: chipset revision 2
[17179576.316000] ICH4: not 100% native mode: will probe irqs later
[17179576.316000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[17179576.316000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[17179576.316000] Probing IDE interface ide0...
[17179576.604000] hda: Maxtor 6Y080L0, ATA DISK drive
[17179577.276000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.288000] Probing IDE interface ide1...
[17179578.024000] hdc: SAMSUNG CDRW/DVD SM-352B, ATAPI CD/DVD-ROM drive
[17179578.696000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.700000] hda: max request size: 128KiB
[17179578.708000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179578.708000] hda: cache flushes supported
[17179578.708000]  hda: hda1 hda2 < hda5 hda6 hda7 >
[17179578.752000] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.752000] Uniform CD-ROM driver Revision: 3.20
[17179579.760000] usbcore: registered new driver usbfs
[17179579.760000] usbcore: registered new driver hub
[17179579.760000] USB Universal Host Controller Interface driver v2.3
[17179579.760000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179579.760000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.760000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.764000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.764000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000e400
[17179579.764000] hub 1-0:1.0: USB hub found
[17179579.764000] hub 1-0:1.0: 2 ports detected
[17179579.868000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179579.868000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179579.868000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179579.868000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179579.868000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000e800
[17179579.868000] hub 2-0:1.0: USB hub found
[17179579.868000] hub 2-0:1.0: 2 ports detected
[17179579.972000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179579.972000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.972000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.972000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.972000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000ec00
[17179579.972000] hub 3-0:1.0: USB hub found
[17179579.972000] hub 3-0:1.0: 2 ports detected
[17179580.076000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179580.076000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179580.076000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179580.076000] ehci_hcd 0000:00:1d.7: debug port 1
[17179580.076000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179580.076000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179580.076000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xdffffc00
[17179580.080000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.080000] hub 4-0:1.0: USB hub found
[17179580.080000] hub 4-0:1.0: 6 ports detected
[17179580.296000] Attempting manual resume
[17179580.320000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179580.320000] EXT3-fs: write access will be enabled during recovery.
[17179580.900000] EXT3-fs: recovery complete.
[17179580.900000] kjournald starting.  Commit interval 5 seconds
[17179580.916000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.968000] usb 2-1: new low speed USB device using uhci_hcd and address 2[17179581.380000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17179592.172000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.176000] agpgart: Detected an Intel i845 Chipset.
[17179592.180000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179592.248000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.268000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.544000] nvidia: module license 'NVIDIA' taints kernel.
[17179592.552000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179592.552000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179592.572000] Real Time Clock Driver v1.12
[17179592.616000] input: PC Speaker as /class/input/input1
[17179592.784000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179592.784000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179593.100000] intel8x0_measure_ac97_clock: measured 54550 usecs
[17179593.100000] intel8x0: clocking to 48000
[17179593.280000] parport: PnPBIOS parport detected.
[17179593.280000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179593.324000] usbcore: registered new driver hiddev
[17179593.344000] input: Microsoft Basic Optical Mouse as /class/input/input2
[17179593.344000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1
[17179593.344000] usbcore: registered new driver usbhid
[17179593.344000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.348000] Linux video capture interface: v1.00
[17179593.400000] Floppy drive(s): fd0 is 1.44M
[17179593.420000] FDC 0 is a post-1991 82077
[17179593.424000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. SONIX sn9c102 + Pas106
[17179593.424000] usbcore: registered new driver spca5xx
[17179593.424000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179593.432000] hw_random: RNG not detected
[17179593.448000] ts: Compaq touchscreen protocol output
[17179593.476000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24a
[17179593.476000] usbcore: registered new driver sn9c102
[17179593.644000] bttv: driver version 0.9.16 loaded
[17179593.644000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179593.644000] bttv: Bt8xx card found (0).
[17179593.644000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179593.644000] bttv0: Bt878 (rev 17) at 0000:03:07.0, irq: 177, latency: 32, mmio: 0xddbfe000
[17179593.644000] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[17179593.644000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected][17179593.644000] bttv0: gpio: en=00000000, out=00000000 in=00ff1bff [init]
[17179593.644000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.648000] bttv0: miro: id=6 tuner=5 radio=no stereo=no
[17179593.648000] bttv0: using tuner=5
[17179593.648000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.648000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179593.652000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179593.652000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179593.688000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179593.688000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[17179593.688000] tuner 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17179593.724000] bttv0: registered device video1
[17179593.724000] bttv0: registered device vbi0
[17179593.724000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179593.780000] 8139too Fast Ethernet driver 0.9.27
[17179593.780000] ACPI: PCI Interrupt 0000:03:0a.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179593.780000] eth0: RealTek RTL8139 at 0xf8a64f00, 00:0b:6a:30:af:da, IRQ 201
[17179593.780000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179593.780000] bt878: AUDIO driver version 0.0.0 loaded
[17179593.780000] bt878: Bt878 AUDIO function found (0).
[17179593.784000] ACPI: PCI Interrupt 0000:03:07.1[A] -> GSI 16 (level, low) -> IRQ 177
[17179593.784000] bt878(0): Bt878 (rev 17) at 03:07.1, irq: 177, latency: 32, memory: 0xddbff000
[17179593.792000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179594.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179594.164000] lp0: using parport0 (interrupt-driven).
[17179594.216000] Adding 265032k swap on /dev/hda7.  Priority:-1 extents:1 across:265032k
[17179594.352000] EXT3 FS on hda6, internal journal
[17179594.480000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.480000] md: bitmap version 4.39
[17179594.880000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179595.496000] NET: Registered protocol family 17
[17179595.832000] cdrom: open failed.
[17179597.692000] NET: Registered protocol family 10
[17179597.692000] lo: Disabled Privacy Extensions
[17179597.692000] IPv6 over IPv4 tunneling driver
[17179603.504000] ACPI: Power Button (FF) [PWRF]
[17179603.504000] ACPI: Power Button (CM) [PWRB]
[17179603.596000] ibm_acpi: ec object not found
[17179603.628000] pcc_acpi: loading...
[17179608.020000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179608.020000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179608.020000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179608.368000] eth0: no IPv6 routers present
[17179609.172000] apm: BIOS not found.
[17179619.564000] Bluetooth: Core ver 2.8
[17179619.564000] NET: Registered protocol family 31
[17179619.564000] Bluetooth: HCI device and connection manager initialized
[17179619.564000] Bluetooth: HCI socket layer initialized
[17179619.584000] Bluetooth: L2CAP ver 2.8
[17179619.584000] Bluetooth: L2CAP socket layer initialized
[17179619.588000] Bluetooth: RFCOMM socket layer initialized
[17179619.588000] Bluetooth: RFCOMM TTY layer initialized
[17179619.588000] Bluetooth: RFCOMM ver 1.7

```

Note: The TV Card works perfect on Windows, and also in Kopete it does detect it:
[http://img103.imageshack.us/img103/6360/workskopete0pr.png](http://img103.imageshack.us/img103/6360/workskopete0pr.png)
Really hope someone will fix this =/

---

### Post by Thanatios on 2006-06-30
Sorry for the double post, but this is the only way to get a reply, since all the other topics are on top =(

---

### Post by teet on 2006-06-30
[http://www2.truman.edu/~dat725/htpc_single.html](http://www2.truman.edu/~dat725/htpc_single.html)

I put this guide together (more for myself than anything), but you may find it helpful since I think your card is a BTTV card.  Specifically this section:  [http://www2.truman.edu/~dat725/htpc_single.html#htpc2](http://www2.truman.edu/~dat725/htpc_single.html#htpc2)

Based on the links from my guide, it appears that your card number should be 39, 52, or, 94.  I have no idea what your tuner number should be, but this may at least put you on the right track.  Once you figure out your card/tuner number
it is seriously only a 5 minute process to get your tv card up and running.

-teet

---

### Post by MonkeyNet on 2006-07-01
Also, have a look at the V4L wiki at

[this address]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page").

It has a list of the BTTV cards support and the tuner settings for them. Out of curiosity, when you run TVTime have you specified your frequency settings?

For some reason with mine, I select Australia, and the channels are not what they should be, but they are all there.

---

### Post by Thanatios on 2006-07-01
I got the TV Card to work on TVTime. But to get it to work on Mythtv I need to get an account at Zap2It. But thats for USA and Canada only. So is there any other Zap2It-like website that gives channels to countries in west-europe? =/

---

### Post by MonkeyNet on 2006-07-01
Not being from West Europe I am not sure. However, have you installed xmltv yet? It has scripts for many different countries.

Depending on which country you are in, you will use a different script. ie. For Australia, I use tv_grab_au.

More information is at [XMLTV]("http://membled.com/work/apps/xmltv/") homepage.

The original tv_grab_au that I used for Australia had problems, so I use a custom version of the script that I found by doing a Google search.

Remember, Google is your friend :)

Glad you finally got the card configured. Good luck. Make sure to post how you went

---

### Post by Thanatios on 2006-07-02
I know that it isnt really smart to ask it here, I should be searching it myself at google, but I have been searching all day by now, and cant find the tv_grab_nl file. :/

Maybe there is some kind of website for all the TV Grabbers? From all countries?

---

### Post by MonkeyNet on 2006-10-30
> **Thanatios said:**
> I know that it isnt really smart to ask it here, I should be searching it myself at google, but I have been searching all day by now, and cant find the tv_grab_nl file. :/

Maybe there is some kind of website for all the TV Grabbers? From all countries?

The XMLTV Package should include the tv_grab_nl script by default. How did you install it?

You can try doing a locate on your machine for the file and see if it is there, but make sure the locate database is up to date;

```
root@dapper#updatedb
```

```
root@dapper#locate tv_grab_nl
```

---

