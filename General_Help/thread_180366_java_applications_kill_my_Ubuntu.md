---
title: "java applications kill my Ubuntu"
date: 2006-05-22
forum: General Help
---

### Post by ed_agamemnon on 2006-05-22
first off, i have a relatively ordinary - but by no means bad - laptop (inspiron 1300), running at 1.5ghz (celeron) with 256mb RAM and an i810 intel video chipset.

I'm running a 686 kernel (on a dist-upgraded Dapper), have tweaked hdparam, got the new i915 graphics drivers, disabled unnecessary services, disabled GNOME menu icons, given up on GNOME, installed fluxbox, replaced OpenOffice with abiword and GNumeric, replaced firefox with swiftfox, replaced nautilus with thunar, etc etc. let me tell you, my computer's still slow!

how is it slow?
- visible screen redraws
- long application loading times, even 40/50 seconds for gnome-terminal
- unresponsive GNOME menus and GTK applications
- jumpy mouse movements when CPU usage is over 60%

anyway...

the general sluggishness i put up with on day-to-day applications is NOTHING compared to what happens when I run a java based program such as Frostwire or Azureus. running the two at the same time slows the computer to such a point where window-redraws take several minutes, delays mouse clicks up to a minute and generally makes the computer entirely unusable. if i eventually manage to kill the applications the system is still slow and java continues to run in the background at 75-90% CPU usage (according to the 'top' command). running 'free' however shows i have a good 50MB of RAM and a ton of SWAP left.

'killall'-ing java solves the system hang and returns me to where i was before: a less than satisfactory sluggish desktop.

anyway, i'm basically resigned to having a slow-ish computer - but there must be a solution to this java problem! should i be using a different one than the repo version? is there just some nifty script i should be running?

hope to get some answers from you guys :)

p.s

please do not tell me to:
1) buy more RAM
2) try Xubuntu
3) not use Azureus, try bittornado or uTorrent with WINE
4) not use Frostwire, use Limewire instead
5) do a fresh CD install (clean Breezy suffered the same problems)

---

### Post by ed_agamemnon on 2006-05-22
*bump*

---

### Post by GadgetsGuy on 2006-05-24
I agree - the frostwire java usage in my process manager is well over 270MB (causing CPU to jump to 100% solid) when everything else is below 20MB.

I think this needs to be addressed.

---

### Post by adamkane on 2006-05-24
Install Sun Java via an alternate method. 
1. deb install
2. download package from Sun, and install according to cut-and-paste howto.

Find out which non-java apps are causing problems with Task Manager.

---

### Post by dmizer on 2006-05-24
something is wrong with your setup.  you have more machine than me and i have no problem running open office org or a host of other java apps.

normal day to day use does not include jumpy mouse or screen redraws. (admitedly i do see screen redraw on closing open office but that's a huge program).

furthermore, my machine is capable of running a windowed vm of win2000 via qemu.  that's two full os running on the same machine.  when i run qemu, i sometimes get a laggy mouse and occasional screen redraws, but that's two os running at the same time.

i have a 850mhz pIII with 256M of ram.  you have done some of the tweaking that i would have suggested, but your machine is certainly capable of handling full on ubuntu.

do you have errors in your dmesg?  because something is definately not right with how your system is running.

---

### Post by ed_agamemnon on 2006-05-24
thanks for all your advice guys, i'm in the process of getting a clean, fresh, safe, and dencent (hopefully) java! :)

dmizer, you're definately right, there's something pretty fishy with my computer - anyway, here's my dmesg output, see what you think:

```
[4294667.296000] Linux version 2.6.15-23-686 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu May 18 17:31:41 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000f7d3800 (usable)
[4294667.296000]  BIOS-e820: 000000000f7d3800 - 0000000010000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[4294667.296000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 247MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 63443
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 59347 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc970
[4294667.296000] ACPI: RSDT (v001 DELL    D05     0x27d50c16 ASL  0x00000061) @ 0x0f7d4425
[4294667.296000] ACPI: FADT (v001 DELL    D05     0x27d50c16 ASL  0x00000061) @ 0x0f7d4c00
[4294667.296000] ACPI: MADT (v001 DELL    D05     0x27d50c16 ASL  0x00000047) @ 0x0f7d5400
[4294667.296000] ACPI: MCFG (v016 DELL    D05     0x27d50c16 ASL  0x00000061) @ 0x0f7d53c0
[4294667.296000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x0f7d4658
[4294667.296000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x0f7d445d
[4294667.296000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:13 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:d0000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash rootflags=data=writeback
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1496.444 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.652000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)[4294669.652000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.659000] Memory: 240128k/253772k available (2095k kernel code, 12972k reserved, 591k data, 332k init, 0k highmem)
[4294669.659000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.719000] Calibrating delay using timer specific routine.. 2995.94 BogoMIPS (lpj=1497970)
[4294669.719000] Security Framework v1.0.0 initialized
[4294669.719000] SELinux:  Disabled at boot.
[4294669.719000] Mount-cache hash table entries: 512
[4294669.719000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[4294669.719000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[4294669.719000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294669.719000] CPU: L2 cache: 1024K
[4294669.719000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[4294669.719000] mtrr: v2.0 (20020519)
[4294669.719000] Enabling fast FPU save and restore... done.
[4294669.719000] Enabling unmasked SIMD FPU exception support... done.
[4294669.719000] Checking 'hlt' instruction... OK.
[4294669.723000] SMP alternatives: switching to UP code
[4294669.723000] checking if image is initramfs... it is
[4294670.397000] Freeing initrd memory: 6809k freed
[4294670.412000] ACPI: Looking for DSDT ... not found!
[4294670.467000] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[4294670.467000] Total of 1 processors activated (2995.94 BogoMIPS).
[4294670.467000] ENABLING IO-APIC IRQs
[4294670.467000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294670.579000] Brought up 1 CPUs
[4294670.579000] NET: Registered protocol family 16
[4294670.579000] EISA bus registered
[4294670.579000] ACPI: bus type pci registered
[4294670.595000] PCI: PCI BIOS revision 2.10 entry at 0xfba7e, last bus=13
[4294670.595000] PCI: Using MMCONFIG
[4294670.595000] ACPI: Subsystem revision 20051216
[4294670.612000] ACPI: Interpreter enabled
[4294670.612000] ACPI: Using IOAPIC for interrupt routing
[4294670.613000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.613000] PCI: Probing PCI hardware (bus 00)
[4294670.613000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.629000] Boot video device is 0000:00:02.0
[4294670.630000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[4294670.630000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[4294670.630000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.630000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.630000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.651000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[4294670.651000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[4294670.652000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[4294670.652000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[4294670.652000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294670.653000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294670.653000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294670.654000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[4294670.654000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[4294670.655000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[4294670.655000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.655000] pnp: PnP ACPI init
[4294670.675000] pnp: PnP ACPI: found 10 devices
[4294670.675000] PnPBIOS: Disabled by ACPI PNP
[4294670.675000] PCI: Using ACPI for IRQ routing
[4294670.675000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.724000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[4294670.724000] pnp: 00:01: ioport range 0x1000-0x1005 could not be reserved
[4294670.724000] pnp: 00:01: ioport range 0x1008-0x100f could not be reserved
[4294670.724000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
[4294670.724000] pnp: 00:02: ioport range 0x1006-0x1007 has been reserved
[4294670.724000] pnp: 00:02: ioport range 0x100a-0x1059 could not be reserved
[4294670.724000] pnp: 00:02: ioport range 0x1060-0x107f has been reserved
[4294670.724000] pnp: 00:02: ioport range 0x1080-0x10bf has been reserved
[4294670.724000] pnp: 00:02: ioport range 0x10c0-0x10df has been reserved
[4294670.724000] pnp: 00:07: ioport range 0x900-0x90f has been reserved
[4294670.724000] pnp: 00:07: ioport range 0x910-0x91f has been reserved
[4294670.724000] pnp: 00:07: ioport range 0x920-0x92f has been reserved
[4294670.724000] pnp: 00:07: ioport range 0x930-0x93f has been reserved
[4294670.724000] pnp: 00:07: ioport range 0x940-0x97f has been reserved
[4294670.724000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294670.724000] PCI: Bridge: 0000:00:1c.0
[4294670.724000]   IO window: disabled.
[4294670.724000]   MEM window: disabled.
[4294670.724000]   PREFETCH window: disabled.
[4294670.724000] PCI: Bridge: 0000:00:1c.3
[4294670.724000]   IO window: d000-dfff
[4294670.724000]   MEM window: dfc00000-dfdfffff
[4294670.724000]   PREFETCH window: d0000000-d01fffff
[4294670.724000] PCI: Bridge: 0000:00:1e.0
[4294670.724000]   IO window: disabled.
[4294670.725000]   MEM window: dfb00000-dfbfffff
[4294670.725000]   PREFETCH window: disabled.
[4294670.725000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294670.725000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294670.725000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[4294670.725000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[4294670.725000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.725000] audit: initializing netlink socket (disabled)
[4294670.725000] audit(1148508150.723:1): initialized
[4294670.725000] VFS: Disk quotas dquot_6.5.1
[4294670.725000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.725000] Initializing Cryptographic API
[4294670.725000] io scheduler noop registered
[4294670.725000] io scheduler anticipatory registered
[4294670.725000] io scheduler deadline registered
[4294670.725000] io scheduler cfq registered
[4294670.726000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294670.726000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294670.726000] assign_interrupt_mode Found MSI capability
[4294670.726000] Allocate Port Service[pcie00]
[4294670.726000] Allocate Port Service[pcie02]
[4294670.726000] Allocate Port Service[pcie03]
[4294670.726000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[4294670.726000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[4294670.726000] assign_interrupt_mode Found MSI capability
[4294670.726000] Allocate Port Service[pcie00]
[4294670.726000] Allocate Port Service[pcie02]
[4294670.726000] Allocate Port Service[pcie03]
[4294670.726000] isapnp: Scanning for PnP cards...
[4294671.083000] isapnp: No Plug & Play device found
[4294671.101000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.101000] i8042.c: Warning: Keylock active.
[4294671.102000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.102000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.102000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.105000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.105000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.105000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.105000] mice: PS/2 mouse device common for all mice
[4294671.106000] EISA: Probing bus 0 at eisa.0
[4294671.106000] Cannot allocate resource for EISA slot 1
[4294671.106000] EISA: Detected 0 cards.
[4294671.106000] NET: Registered protocol family 2
[4294671.110000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.116000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[4294671.116000] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[4294671.116000] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[4294671.116000] TCP: Hash tables configured (established 8192 bind 8192)
[4294671.116000] TCP reno registered
[4294671.116000] TCP bic registered
[4294671.116000] NET: Registered protocol family 1
[4294671.116000] NET: Registered protocol family 8
[4294671.116000] NET: Registered protocol family 20
[4294671.116000] Using IPI No-Shortcut mode
[4294671.116000] ACPI wakeup devices:
[4294671.116000]  LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 AZAL MODM PCIE RP01 RP02 RP03 RP04 RP05 RP06
[4294671.116000] ACPI: (supports S0 S3 S4 S5)
[4294671.116000] Freeing unused kernel memory: 332k freed
[4294671.165000] vga16fb: initializing
[4294671.165000] vga16fb: mapped to 0xc00a0000
[4294671.299000] Console: switching to colour frame buffer device 80x25
[4294671.299000] fb0: VGA16 VGA frame buffer device
[4294672.409000] Capability LSM initialized
[4294672.441000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294672.441000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294672.447000] ACPI: Thermal Zone [THM] (34 C)
[4294672.912000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294672.912000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[4294672.912000] ICH6: chipset revision 3
[4294672.912000] ICH6: not 100% native mode: will probe irqs later
[4294672.912000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:DMA
[4294672.912000] Probing IDE interface ide0...
[4294673.315000] hda: ST9408114A, ATA DISK drive
[4294673.920000] hdb: TSSTcorpCD-RW/DVD-ROM TSL462C, ATAPI CD/DVD-ROM drive
[4294673.986000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.022000] hda: max request size: 1024KiB
[4294674.030000] hda: 78140160 sectors (40007 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.030000] hda: cache flushes supported
[4294674.030000]  hda: hda1 hda2 < hda5 >
[4294674.092000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[4294674.092000] Uniform CD-ROM driver Revision: 3.20
[4294675.254000] usbcore: registered new driver usbfs
[4294675.255000] usbcore: registered new driver hub
[4294675.256000] USB Universal Host Controller Interface driver v2.3
[4294675.256000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294675.256000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.256000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294675.257000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.257000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000bf80
[4294675.257000] hub 1-0:1.0: USB hub found
[4294675.257000] hub 1-0:1.0: 2 ports detected
[4294675.358000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 209
[4294675.358000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.358000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294675.358000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.358000] uhci_hcd 0000:00:1d.1: irq 209, io base 0x0000bf60
[4294675.358000] hub 2-0:1.0: USB hub found
[4294675.358000] hub 2-0:1.0: 2 ports detected
[4294675.467000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[4294675.467000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.467000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294675.467000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.467000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x0000bf40
[4294675.467000] hub 3-0:1.0: USB hub found
[4294675.467000] hub 3-0:1.0: 2 ports detected
[4294675.583000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[4294675.583000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294675.583000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294675.583000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294675.583000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000bf20
[4294675.583000] hub 4-0:1.0: USB hub found
[4294675.583000] hub 4-0:1.0: 2 ports detected
[4294675.695000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 169
[4294675.695000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.695000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294675.695000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.695000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.695000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294675.695000] ehci_hcd 0000:00:1d.7: irq 169, io mem 0xb0000000
[4294675.699000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.700000] hub 5-0:1.0: USB hub found
[4294675.700000] hub 5-0:1.0: 8 ports detected
[4294675.857000] Probing IDE interface ide1...
[4294676.540000] Attempting manual resume
[4294676.551000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294676.551000] EXT3-fs: write access will be enabled during recovery.
[4294676.789000] EXT3-fs: recovery complete.
[4294676.789000] kjournald starting.  Commit interval 5 seconds
[4294676.789000] EXT3-fs: mounted filesystem with writeback data mode.
[4294690.079000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.182000] agpgart: Detected an Intel 915GM Chipset.
[4294690.182000] agpgart: Detected 7932K stolen memory.
[4294690.202000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294690.239000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.304000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.633000] Real Time Clock Driver v1.12
[4294690.646000] hw_random: RNG not detected
[4294690.652000] input: PC Speaker as /class/input/input1
[4294690.795000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294690.795000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294691.039000] b44.c:v0.97 (Nov 30, 2005)
[4294691.039000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 217
[4294691.043000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:22:91:d9:df
[4294691.283000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[4294691.321000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294691.681000] ts: Compaq touchscreen protocol output
[4294693.327000] lp: driver loaded but no devices found
[4294694.021000] Adding 730916k swap on /dev/hda5.  Priority:-1 extents:1 across:730916k
[4294694.154000] EXT3 FS on hda1, internal journal
[4294694.300000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.300000] md: bitmap version 4.39
[4294694.725000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294697.899000] ACPI: AC Adapter [AC] (on-line)
[4294697.901000] ACPI: Battery Slot [BAT0] (battery absent)
[4294698.085000] ACPI: Lid Switch [LID]
[4294698.085000] ACPI: Power Button (CM) [PBTN]
[4294698.085000] ACPI: Sleep Button (CM) [SBTN]
[4294698.176000] ibm_acpi: ec object not found
[4294698.360000] pcc_acpi: loading...
[4294698.528000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294698.528000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[4294705.480000] apm: BIOS not found.
[4294705.877000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[4294706.014000] ndiswrapper: driver bcmwl5a () loaded
[4294706.014000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 209
[4294706.022000] ndiswrapper: using irq 209
[4294707.493000] wlan0: vendor: ''
[4294707.493000] wlan0: ndiswrapper ethernet device 00:14:a4:60:4e:4f using driver bcmwl5a, 14E4:4318.5.conf
[4294707.493000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4294711.414000] [drm] Initialized drm 1.0.1 20051102
[4294711.440000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294711.440000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[4294759.646000] NET: Registered protocol family 10
[4294759.647000] lo: Disabled Privacy Extensions
[4294759.647000] IPv6 over IPv4 tunneling driver
[4294785.111000] NET: Registered protocol family 17
[4294794.255000] wlan0: no IPv6 routers present

```

can't see anything especially interesting - i'll have a try with a clean Dapper when it's finished...

---

### Post by dmizer on 2006-05-24
if you haven't gone to dapper yet, i'd start by disabling ipv6.

---

### Post by ed_agamemnon on 2006-05-25
i've never done that before; how do i disable ipv6? :)

thankyou!

---

### Post by vinodis on 2006-05-25
I am using NetBeans Java/J2EE IDE without any issues on Kubuntu. I have 512MB RAM + your same configs. But I am using the Sun JRE/JDK 1.5 not the default one.

---

### Post by dmizer on 2006-05-25
[QUOTE=ed_agamemnon]i've never done that before; how do i disable ipv6? :)

thankyou![/QUOTE]
no problem ... check the wiki here:
[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

---

### Post by ed_agamemnon on 2006-05-25
ok, ipv6 disabled.
azureus instant notifications disabled.
sun-java5-bin installed from multiverse.

off to reboot - let's see what happens...

---

### Post by Darkmoon_UK on 2008-02-15
I am guessing he never came back because it worked...

...the default installed Java with Ubuntu is not the Sun version and totally dies with Azureus.

I had the same problem and installing proper Sun Java solved everything for me.

---

