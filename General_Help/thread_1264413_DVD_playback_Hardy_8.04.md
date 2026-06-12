---
title: "DVD playback Hardy 8.04"
date: 2009-09-12
forum: General Help
---

### Post by duckgoesoink on 2009-09-12
Hi everyone,

I'm having trouble enabling DVD playback on Hardy 8.04. I stopped using Ubuntu for a few months, but now I've reinstalled it and followed the steps I'd previously written down for DVD playback (worked like a charm a few months ago) - but this time it isn't working. The DVD drive makes noises but no player will let me open the disc.

[LIST]
[*]I installed Ubuntu Restricted Extras.
[*]I enabled Medibuntu sources.
[*]I installed totem-xine.
[*]I pasted this into the terminal: sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot
[*]Then: sudo /usr/share/doc/libdvdread3/install-css.sh
[*]I restarted the computer then configured Totem-Xine as default.
[/LIST]

I tried with VLC, but nothing happens. And I tried searching the forums, but I couldn't find anything related to Hardy... (bad searching perhaps?)

Thanks a lot for any help or suggestions.

---

### Post by Bucky Ball on 2009-09-12
[http://ubuntu-tutorials.com/2008/07/01/enable-commercial-dvd-playback-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/07/01/enable-commercial-dvd-playback-on-ubuntu-804/)

... might help, from here:

[http://au.altavista.com/web/results?itag=ody&q=enable+dvd+playback+hardy+8.04&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=enable+dvd+playback+hardy+8.04&kgs=0&kls=0)

Never restrict your searches to the forum. There are tutorials all over and the forums also pop up in a general search. I personally never search the forums specifically. Half the time I end up here from a general search if there is anything pertinent to my prob. :)

---

### Post by duckgoesoink on 2009-09-12
Hi, thanks a lot for your suggestions. I did search Google for solutions to my problem, but most of the results I got were for the latest version of Ubuntu, or said to do stuff I already did. Hence my search through the forums.

I did already see the site you linked to, but it seems it just tells me what I've already done? (Installing libdvdread3 and/or libdvdcss2.) I tried it anyway, still no luck. I have rebooted a few times, no change.

Any more ideas?

Cheers

---

### Post by rocket16 on 2009-09-12
**When you tried Totem to play the DVD, didn't it ask for additional plugin? If not, try it once more, and see whether it asks for a plugin or not. If yes, then just click that, and wait for the plugin to be installed.**

---

### Post by duckgoesoink on 2009-09-12
> **rocket16 said:**
> **When you tried Totem to play the DVD, didn't it ask for additional plugin? If not, try it once more, and see whether it asks for a plugin or not. If yes, then just click that, and wait for the plugin to be installed.**

Hi, thanks for the suggestion, but neither Totem nor VLC asked for plugins (since I started using Ubuntu a couple of years ago, I've always had to follow a few steps to set it up manually).

I tried running totem-xine as sudo, but the option to play a disc is greyed out. I also get this message in the terminal:
```
** (totem-xine:8578): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

```
I tried running vlc as sudo, but it doesn't work either. VLC says:
```
Unable to open 'dvd:///dev/scd0'
```
and the terminal says:
```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD

```

I would appreciate a human explanation of the errors (I don't really understand terminal garble).

Thanks a lot :-)

---

### Post by P4man on 2009-09-12
Does the dvd show up at all in places > computer ? Im thinking perhaps you're having problem accessing or reading the DVD, and it has nothing to do with codecs to read or decrypt it. Does it read data cds or dvds ?

edit: our posts crossed, but it seems I was right. Let me look at those messages...

---

### Post by duckgoesoink on 2009-09-12
> **P4man said:**
> Does the dvd show up at all in places > computer ? Im thinking perhaps you're having problem accessing or reading the DVD, and it has nothing to do with codecs to read or decrypt it. Does it read data cds or dvds ?

Hi, thanks for the reply. It does successfully read data CDs and DVDs, but is really having issues with commercial DVDs. I tried using different DVDs - some of them (but not all) show up in Places > Computer, but still none of them play... They all cause the disc drive to do spinny stuff (you can hear it trying).

When I go to Computer in Nautilus and try to open the CD-RW/DVD-+RW Drive, it says:
Unable to mount location, No media in the drive.

---

### Post by P4man on 2009-09-12
So you got a problem with the dvd drive. (Im assuming you are sure those cds/dvds are fine by themselve and play on a different OS or computer).

Can you open a terminal and type

```
dmesg > log.txt
```

then attach your log.txt (in your homefolder) to a post here so we can have a look?

---

### Post by duckgoesoink on 2009-09-12
The DVD drive works fine on Vista, and has previously worked fine on Feisty and Hardy... (the discs work on other computers too).

The log.txt is too big to attach - there is a limit of 19.5 KB for this filetype. I'll throw it in code tags.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Aug 18 17:04:53 UTC 2009 (Ubuntu 2.6.24-24.59-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffa8000 (usable)
[    0.000000]  BIOS-e820: 000000003ffa8000 - 000000003ffb0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffbe000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262056
[    0.000000] On node 0 totalpages: 262056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32425 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7AF0 checksum 0
[    0.000000] ACPI: RSDP 000F7AF0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFB0000, 0040 (r1 AMI    OEMRSDT   2000715 MSFT       97)
[    0.000000] ACPI: FACP 3FFB0200, 0084 (r2 AMI    OEMFACP   2000715 MSFT       97)
[    0.000000] ACPI: DSDT 3FFB05E0, 8918 (r1  F3J00 F3J00001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFBE000, 0040
[    0.000000] ACPI: APIC 3FFB0390, 005C (r1 AMI    OEMAPIC   2000715 MSFT       97)
[    0.000000] ACPI: MCFG 3FFB03F0, 003C (r1 AMI    OEMMCFG   2000715 MSFT       97)
[    0.000000] ACPI: BOOT 3FFB05B0, 0028 (r1 AMI    OEMBOOT   2000715 MSFT       97)
[    0.000000] ACPI: SLIC 3FFB0430, 0176 (r1 AMI    OEMSLIC   2000715 MSFT       97)
[    0.000000] ACPI: OEMB 3FFBE040, 0046 (r1 AMI    AMI_OEM   2000715 MSFT       97)
[    0.000000] ACPI: HPET 3FFB8F00, 0038 (r1 AMI        ASUS  2000715 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260009
[    0.000000] Kernel command line: root=UUID=5d4b8625-2a5c-44a0-b5ff-e8336206890a ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.576 MHz processor.
[   16.272780] Console: colour VGA+ 80x25
[   16.272784] console [tty0] enabled
[   16.273051] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.273346] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.296588] Memory: 1027072k/1048224k available (2181k kernel code, 20504k reserved, 1006k data, 368k init, 130720k highmem)
[   16.296595] virtual kernel memory layout:
[   16.296596]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.296597]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.296598]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.296599]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.296600]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   16.296601]       .data : 0xc0321548 - 0xc041cdc4   (1006 kB)
[   16.296602]       .text : 0xc0100000 - 0xc0321548   (2181 kB)
[   16.296606] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.296636] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.296781] hpet clockevent registered
[   16.376666] Calibrating delay using timer specific routine.. 3328.90 BogoMIPS (lpj=6657803)
[   16.376683] Security Framework initialized
[   16.376687] SELinux:  Disabled at boot.
[   16.376698] AppArmor: AppArmor initialized
[   16.376702] Failure registering capabilities with primary security module.
[   16.376709] Mount-cache hash table entries: 512
[   16.376813] Initializing cgroup subsys ns
[   16.376817] Initializing cgroup subsys cpuacct
[   16.376826] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   16.376834] monitor/mwait feature present.
[   16.376835] using mwait in idle threads.
[   16.376839] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.376842] CPU: L2 cache: 2048K
[   16.376844] CPU: Physical Processor ID: 0
[   16.376845] CPU: Processor Core ID: 0
[   16.376849] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   16.376857] Compat vDSO mapped to ffffe000.
[   16.376868] Checking 'hlt' instruction... OK.
[   16.393041] SMP alternatives: switching to UP code
[   16.394702] Early unpacking initramfs... done
[   16.738755] ACPI: Core revision 20070126
[   16.738808] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.795779] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   16.795796] SMP alternatives: switching to SMP code
[   16.796543] Booting processor 1/1 eip 3000
[   16.806747] Initializing CPU#1
[   16.899857] Calibrating delay using timer specific routine.. 3072.74 BogoMIPS (lpj=6145492)
[   16.899864] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   16.899869] monitor/mwait feature present.
[   16.899872] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.899874] CPU: L2 cache: 2048K
[   16.899876] CPU: Physical Processor ID: 0
[   16.899877] CPU: Processor Core ID: 1
[   16.899880] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   16.900462] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   16.900485] Total of 2 processors activated (6401.64 BogoMIPS).
[   16.900679] ENABLING IO-APIC IRQs
[   16.900869] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.047743] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   17.067727] Brought up 2 CPUs
[   17.067752] CPU0 attaching sched-domain:
[   17.067755]  domain 0: span 03
[   17.067757]   groups: 01 02
[   17.067760] CPU1 attaching sched-domain:
[   17.067762]  domain 0: span 03
[   17.067763]   groups: 02 01
[   17.068007] net_namespace: 64 bytes
[   17.068019] Booting paravirtualized kernel on bare hardware
[   17.068490] Time: 11:27:04  Date: 09/12/09
[   17.068518] NET: Registered protocol family 16
[   17.068732] EISA bus registered
[   17.068737] ACPI: bus type pci registered
[   17.068989] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   17.068991] PCI: Using configuration type 1
[   17.069012] Setting up standard PCI resources
[   17.073139] ACPI: EC: Look up EC in DSDT
[   17.079618] APIC error on CPU1: 00(40)
[   17.133496] ACPI: Interpreter enabled
[   17.133499] ACPI: (supports S0 S1 S3 S4 S5)
[   17.133520] ACPI: Using IOAPIC for interrupt routing
[   17.141540] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   17.141543] ACPI: EC: driver started in poll mode
[   17.141682] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.142479] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   17.142483] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   17.143931] PCI: Transparent bridge - 0000:00:1e.0
[   17.143981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.144172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   17.144285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   17.144399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   17.144514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   17.144632] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   17.157738] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   17.157903] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 12)
[   17.158065] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[   17.158226] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 12)
[   17.158387] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12) *0, disabled.
[   17.158550] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[   17.158712] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 12) *0, disabled.
[   17.158874] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 12)
[   17.159029] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.159062] pnp: PnP ACPI init
[   17.159070] ACPI: bus type pnp registered
[   17.161476] pnp: PnP ACPI: found 13 devices
[   17.161479] ACPI: ACPI bus type pnp unregistered
[   17.161483] PnPBIOS: Disabled by ACPI PNP
[   17.161728] PCI: Using ACPI for IRQ routing
[   17.161731] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.203515] NET: Registered protocol family 8
[   17.203518] NET: Registered protocol family 20
[   17.203555] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.203559] hpet0: 3 64-bit timers, 14318180 Hz
[   17.204592] AppArmor: AppArmor Filesystem Enabled
[   17.207388] Time: tsc clocksource has been installed.
[   17.207402] Switched to high resolution mode on CPU 0
[   17.207506] Switched to high resolution mode on CPU 1
[   17.220368] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   17.220379] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.220381] system 00:08: ioport range 0x800-0x87f has been reserved
[   17.220384] system 00:08: ioport range 0x480-0x4bf has been reserved
[   17.220387] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   17.220390] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   17.220393] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   17.220397] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   17.220400] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   17.220403] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   17.220411] system 00:0a: ioport range 0x250-0x253 has been reserved
[   17.220414] system 00:0a: ioport range 0x256-0x25f has been reserved
[   17.220417] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   17.220419] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   17.220422] system 00:0a: iomem range 0xfec10000-0xfec17fff has been reserved
[   17.220425] system 00:0a: iomem range 0xfec18000-0xfec1ffff has been reserved
[   17.220428] system 00:0a: iomem range 0xfec20000-0xfec27fff has been reserved
[   17.220434] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[   17.220440] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   17.220443] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   17.220445] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   17.220448] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[   17.220451] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   17.250877] PCI: Bridge: 0000:00:01.0
[   17.250879]   IO window: disabled.
[   17.250882]   MEM window: f9f00000-fdffffff
[   17.250886]   PREFETCH window: bdf00000-ddefffff
[   17.250890] PCI: Bridge: 0000:00:1c.0
[   17.250893]   IO window: c000-cfff
[   17.250899]   MEM window: fe000000-fe0fffff
[   17.250903]   PREFETCH window: disabled.
[   17.250909] PCI: Bridge: 0000:00:1c.1
[   17.250910]   IO window: disabled.
[   17.250916]   MEM window: fe100000-fe1fffff
[   17.250920]   PREFETCH window: disabled.
[   17.250926] PCI: Bridge: 0000:00:1c.2
[   17.250929]   IO window: d000-dfff
[   17.250935]   MEM window: fe200000-fe9fffff
[   17.250940]   PREFETCH window: ddf00000-dfefffff
[   17.250946] PCI: Bridge: 0000:00:1e.0
[   17.250948]   IO window: disabled.
[   17.250953]   MEM window: fea00000-feafffff
[   17.250958]   PREFETCH window: disabled.
[   17.250976] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.250981] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.251005] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.251011] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.251035] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   17.251041] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.251066] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.251071] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.251086] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.251097] NET: Registered protocol family 2
[   17.288286] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.288501] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.288952] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.289169] TCP: Hash tables configured (established 131072 bind 65536)
[   17.289172] TCP reno registered
[   17.300345] checking if image is initramfs... it is
[   17.978234] Freeing initrd memory: 7326k freed
[   17.978398] Simple Boot Flag at 0x52 set to 0x1
[   17.979106] audit: initializing netlink socket (disabled)
[   17.979119] audit(1252754824.448:1): initialized
[   17.979324] highmem bounce pool size: 64 pages
[   17.981451] VFS: Disk quotas dquot_6.5.1
[   17.981531] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.981668] io scheduler noop registered
[   17.981670] io scheduler anticipatory registered
[   17.981672] io scheduler deadline registered
[   17.981683] io scheduler cfq registered (default)
[   17.981801] Boot video device is 0000:01:00.0
[   17.981917] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.981957] assign_interrupt_mode Found MSI capability
[   17.981989] Allocate Port Service[0000:00:01.0:pcie00]
[   17.982075] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.982135] assign_interrupt_mode Found MSI capability
[   17.982188] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.982224] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.982332] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.982391] assign_interrupt_mode Found MSI capability
[   17.982439] Allocate Port Service[0000:00:1c.1:pcie00]
[   17.982473] Allocate Port Service[0000:00:1c.1:pcie02]
[   17.982579] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.982638] assign_interrupt_mode Found MSI capability
[   17.982685] Allocate Port Service[0000:00:1c.2:pcie00]
[   17.982719] Allocate Port Service[0000:00:1c.2:pcie02]
[   17.982995] isapnp: Scanning for PnP cards...
[   18.337402] isapnp: No Plug & Play device found
[   18.364350] Real Time Clock Driver v1.12ac
[   18.364552] hpet_resources: 0xfed00000 is busy
[   18.364601] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.365912] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.365984] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.366089] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   18.368682] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.370103] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.370108] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.370110] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.370113] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.370115] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.389641] mice: PS/2 mouse device common for all mice
[   18.389769] EISA: Probing bus 0 at eisa.0
[   18.389807] EISA: Detected 0 cards.
[   18.389810] cpuidle: using governor ladder
[   18.389811] cpuidle: using governor menu
[   18.389893] NET: Registered protocol family 1
[   18.389920] Using IPI No-Shortcut mode
[   18.389951] registered taskstats version 1
[   18.390063]   Magic number: 9:12:479
[   18.390131] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.390133] EDD information not available.
[   18.390317] Freeing unused kernel memory: 368k freed
[   18.390342] Write protecting the kernel read-only data: 802k
[   18.422619] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.609811] fuse init (API version 7.9)
[   19.628633] ACPI: SSDT 3FFB8F40, 0D24 (r1    AMI   CPU1PM        1 INTL  2002026)
[   19.629260] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   19.629265] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.629326] ACPI: SSDT 3FFB9C70, 0D24 (r1    AMI   CPU2PM        1 INTL  2002026)
[   19.629977] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   19.629982] ACPI: Processor [CPU2] (supports 8 throttling states)
[   19.631590] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.636900] ACPI: Thermal Zone [THRM] (57 C)
[   19.998070] r8169 Gigabit Ethernet driver 2.2LK loaded
[   19.998101] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.998124] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   19.998520] eth0: RTL8168b/8111b at 0xf8854000, 00:1e:8c:61:4b:80, XID 38000000 IRQ 219
[   20.038577] usbcore: registered new interface driver usbfs
[   20.038602] usbcore: registered new interface driver hub
[   20.038871] SCSI subsystem initialized
[   20.038898] usbcore: registered new device driver usb
[   20.071192] USB Universal Host Controller Interface driver v3.0
[   20.071255] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   20.071267] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.071271] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.071511] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.071545] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
[   20.071684] usb usb1: configuration #1 chosen from 1 choice
[   20.071710] hub 1-0:1.0: USB hub found
[   20.071716] hub 1-0:1.0: 2 ports detected
[   20.074648] libata version 3.00 loaded.
[   20.174952] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   20.174965] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.174970] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.174996] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.175028] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e880
[   20.175145] usb usb2: configuration #1 chosen from 1 choice
[   20.175171] hub 2-0:1.0: USB hub found
[   20.175176] hub 2-0:1.0: 2 ports detected
[   20.278778] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.278790] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.278794] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.278818] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.278851] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   20.278966] usb usb3: configuration #1 chosen from 1 choice
[   20.278990] hub 3-0:1.0: USB hub found
[   20.278994] hub 3-0:1.0: 2 ports detected
[   20.382598] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   20.382610] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   20.382615] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   20.382643] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   20.382677] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e480
[   20.382795] usb usb4: configuration #1 chosen from 1 choice
[   20.382820] hub 4-0:1.0: USB hub found
[   20.382825] hub 4-0:1.0: 2 ports detected
[   20.486577] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.512902] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   20.512916] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.512920] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.512949] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.516871] ehci_hcd 0000:00:1d.7: debug port 1
[   20.516877] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.516884] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
[   20.521104] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   20.531268] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.531384] usb usb5: configuration #1 chosen from 1 choice
[   20.531411] hub 5-0:1.0: USB hub found
[   20.531417] hub 5-0:1.0: 8 ports detected
[   20.539275] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.634285] ata_piix 0000:00:1f.2: version 2.12
[   20.634297] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   20.634348] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   20.634395] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.634600] scsi0 : ata_piix
[   20.635162] scsi1 : ata_piix
[   20.636157] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   20.636160] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   20.798229] ata1.00: ATA-8: ST9120817AS, 3.AAA, max UDMA/133
[   20.798234] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   20.814207] ata1.00: configured for UDMA/133
[   21.133862] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PR03, max UDMA/33
[   21.305529] ata2.00: configured for UDMA/33
[   21.305676] scsi 0:0:0:0: Direct-Access     ATA      ST9120817AS      3.AA PQ: 0 ANSI: 5
[   21.309447] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PR03 PQ: 0 ANSI: 5
[   21.321223] Driver 'sd' needs updating - please use bus_type methods
[   21.321300] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.321313] sd 0:0:0:0: [sda] Write Protect is off
[   21.321315] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.321332] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.321386] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.321396] sd 0:0:0:0: [sda] Write Protect is off
[   21.321399] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.321415] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.321419]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.341360]  sda1 sda2 < sda5 sda6 sda7 >
[   21.369763] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.374014] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.374035] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.389583] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.389588] Uniform CD-ROM driver Revision: 3.20
[   21.389639] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.393949] usb 5-4: new high speed USB device using ehci_hcd and address 3
[   21.745578] usb 5-4: configuration #1 chosen from 1 choice
[   21.824577] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000159349]
[   22.223685] usb 5-8: new high speed USB device using ehci_hcd and address 5
[   22.356393] usb 5-8: configuration #1 chosen from 1 choice
[   22.356690] usbcore: registered new interface driver libusual
[   22.362195] Initializing USB Mass Storage driver...
[   22.436866] Attempting manual resume
[   22.436869] swsusp: Resume From Partition 8:7
[   22.436871] PM: Checking swsusp image.
[   22.437071] PM: Resume from disk failed.
[   22.472075] kjournald starting.  Commit interval 5 seconds
[   22.472090] EXT3-fs: mounted filesystem with ordered data mode.
[   22.595115] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   22.773259] usb 2-1: configuration #1 chosen from 1 choice
[   23.014468] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   23.275415] usb 3-1: configuration #1 chosen from 1 choice
[   23.279678] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.279755] usb-storage: device found at 3
[   23.279757] usb-storage: waiting for device to settle before scanning
[   23.279775] usbcore: registered new interface driver usb-storage
[   23.279782] USB Mass Storage support registered.
[   28.270516] usb-storage: device scan complete
[   28.271014] scsi 2:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[   28.272600] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   28.273473] sd 2:0:0:0: [sdb] Write Protect is off
[   28.273477] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   28.273481] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   28.274470] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   28.275350] sd 2:0:0:0: [sdb] Write Protect is off
[   28.275354] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   28.275357] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   28.275362]  sdb:<6>input: PC Speaker as /devices/platform/pcspkr/input/input2
[   30.201448] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.308322] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.393636] iTCO_vendor_support: vendor-support=0
[   30.504499] Linux agpgart interface v0.102
[   30.603126] input: Power Button (FF) as /devices/virtual/input/input3
[   30.642750] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.642849] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   30.642887] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.666731] ACPI: Power Button (FF) [PWRF]
[   30.666846] input: Lid Switch as /devices/virtual/input/input4
[   30.701550] ACPI: Lid Switch [LID]
[   30.701613] input: Power Button (CM) as /devices/virtual/input/input5
[   30.762567] ACPI: Power Button (CM) [PWRB]
[   30.762631] input: Sleep Button (CM) as /devices/virtual/input/input6
[   30.813203] intel_rng: FWH not detected
[   30.826471] ACPI: Sleep Button (CM) [SLPB]
[   30.826487] asus-laptop: Asus Laptop Support version 0.42
[   30.826720] asus-laptop:   F3JC model detected
[   30.830167] Registered led device: asus:touchpad
[   30.908502] ricoh-mmc: Ricoh MMC Controller disabling driver
[   30.908506] ricoh-mmc: Copyright(c) Philip Langdale
[   30.908552] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   30.908564] ricoh-mmc: Controller is now disabled.
[   31.113476] sdhci: Secure Digital Host Controller Interface driver
[   31.113479] sdhci: Copyright(c) Pierre Ossman
[   31.113527] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 19)
[   31.113548] ACPI: PCI Interrupt 0000:06:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[   31.113568] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   31.113622] mmc0: SDHCI at 0xfeaff400 irq 17 DMA
[   31.224926] ACPI: AC Adapter [AC0] (on-line)
[   31.346093] ACPI: Battery Slot [BAT0] (battery present)
[   31.407925] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/LNXVIDEO:00/input/input7
[   31.466477] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.637974] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   31.637978] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   31.638128] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.638143] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   31.638166] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   31.779065] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   31.788349] usbcore: registered new interface driver hiddev
[   31.802683] input: Genius       NetScroll+Mini Traveler as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input8
[   31.802747] Bluetooth: Core ver 2.11
[   31.822821] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   31.835123] NET: Registered protocol family 31
[   31.835126] Bluetooth: HCI device and connection manager initialized
[   31.835131] Bluetooth: HCI socket layer initialized
[   31.857029] input,hidraw0: USB HID v1.10 Mouse [Genius       NetScroll+Mini Traveler] on usb-0000:00:1d.1-1
[   31.857052] usbcore: registered new interface driver usbhid
[   31.857056] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.927855] Linux video capture interface: v2.00
[   31.957960] Bluetooth: HCI USB driver ver 2.9
[   31.960297] usbcore: registered new interface driver hci_usb
[   31.975604] stk11xx: Syntek USB2.0 webcam driver startup
[   31.975639] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[   31.975642] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x0501.
[   31.975645] stk11xx: Release: 0005
[   31.975647] stk11xx: Number of interfaces : 1
[   31.977343] stk11xx: Initialize USB2.0 Syntek Camera
[   32.005482] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.005517] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.177387]  sdb1
[   32.177468] sd 2:0:0:0: [sdb] Attached SCSI disk
[   32.177518] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   32.222541] stk11xx: Syntek USB2.0 Camera is ready
[   32.222583] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[   32.222616] usbcore: registered new interface driver usb_stk11xx_driver
[   32.222620] stk11xx: v1.3.1 : Syntek USB Video Camera
[   32.871473] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   32.874259] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   33.191413] lp: driver loaded but no devices found
[   33.296135] Adding 1429744k swap on /dev/sda7.  Priority:-1 extents:1 across:1429744k
[   33.840154] EXT3 FS on sda6, internal journal
[   34.951637] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.410199] No dock devices found.
[   35.736921] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFD) is beyond end of object [20070126]
[   35.736942] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node f7c24c48), AE_AML_PACKAGE_LIMIT
[   35.736991] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
[   35.737188] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFD) is beyond end of object [20070126]
[   35.737206] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node f7c24e58), AE_AML_PACKAGE_LIMIT
[   35.737255] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
[   36.466584] apm: BIOS not found.
[   36.602476] ppdev: user-space parallel port driver
[   36.719279] audit(1252747643.643:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5291 profile="/usr/sbin/cupsd" namespace="default"
[   38.419332] r8169: eth0: link up
[   38.419345] r8169: eth0: link up
[   38.430404] Bluetooth: L2CAP ver 2.9
[   38.430409] Bluetooth: L2CAP socket layer initialized
[   38.507914] Bluetooth: RFCOMM socket layer initialized
[   38.507930] Bluetooth: RFCOMM TTY layer initialized
[   38.507932] Bluetooth: RFCOMM ver 1.8
[   41.589079] NET: Registered protocol family 17
[   47.730522] NET: Registered protocol family 10
[   47.730791] lo: Disabled Privacy Extensions
[   47.731704] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.000598] eth0: no IPv6 routers present
[   62.280054] CPU0 attaching NULL sched-domain.
[   62.280068] CPU1 attaching NULL sched-domain.
[   62.302995] CPU0 attaching sched-domain:
[   62.303004]  domain 0: span 03
[   62.303007]   groups: 01 02
[   62.303015] CPU1 attaching sched-domain:
[   62.303018]  domain 0: span 03
[   62.303020]   groups: 02 01
[ 3573.375382] UDF-fs: No VRS found
[ 3573.387954] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 3573.387982] ISOFS: changing to secondary root
[ 3627.538500] UDF-fs: Partition marked readonly; forcing readonly mount
[ 3627.598377] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO', timestamp 2009/09/11 20:29 (1078)
[ 3630.306041] attempt to access beyond end of device
[ 3630.306054] sr0: rw=0, want=2098424, limit=2097151
[ 3630.306058] Buffer I/O error on device sr0, logical block 524605
[ 3630.306065] attempt to access beyond end of device
[ 3630.306069] sr0: rw=0, want=2098428, limit=2097151
[ 3630.306072] Buffer I/O error on device sr0, logical block 524606
[ 3630.306080] attempt to access beyond end of device
[ 3630.306085] sr0: rw=0, want=2098432, limit=2097151
[ 3630.306090] Buffer I/O error on device sr0, logical block 524607
[ 3630.306095] attempt to access beyond end of device
[ 3630.306099] sr0: rw=0, want=2098436, limit=2097151
[ 3630.306104] Buffer I/O error on device sr0, logical block 524608
[ 3630.306111] attempt to access beyond end of device
[ 3630.306116] sr0: rw=0, want=2098440, limit=2097151
[ 3630.306120] Buffer I/O error on device sr0, logical block 524609
[ 3630.306125] attempt to access beyond end of device
[ 3630.306130] sr0: rw=0, want=2098444, limit=2097151
[ 3630.306134] Buffer I/O error on device sr0, logical block 524610
[ 3630.306144] attempt to access beyond end of device
[ 3630.306148] sr0: rw=0, want=2098448, limit=2097151
[ 3630.306153] Buffer I/O error on device sr0, logical block 524611
[ 3630.306158] attempt to access beyond end of device
[ 3630.306163] sr0: rw=0, want=2098452, limit=2097151
[ 3630.306168] Buffer I/O error on device sr0, logical block 524612
[ 3630.306174] attempt to access beyond end of device
[ 3630.306179] sr0: rw=0, want=2098424, limit=2097151
[ 3630.306183] Buffer I/O error on device sr0, logical block 524605
[ 3630.306188] attempt to access beyond end of device
[ 3630.306193] sr0: rw=0, want=2098428, limit=2097151
[ 3630.306197] Buffer I/O error on device sr0, logical block 524606
[ 3630.306210] attempt to access beyond end of device
[ 3630.306214] sr0: rw=0, want=2098424, limit=2097151
[ 3630.306220] attempt to access beyond end of device
[ 3630.306224] sr0: rw=0, want=2098428, limit=2097151
[ 3630.306240] attempt to access beyond end of device
[ 3630.306245] sr0: rw=0, want=2098424, limit=2097151
[ 3630.306250] attempt to access beyond end of device
[ 3630.306264] sr0: rw=0, want=2098428, limit=2097151
[ 3630.306805] attempt to access beyond end of device
[ 3630.306809] sr0: rw=0, want=4195572, limit=2097151
[ 3630.306813] attempt to access beyond end of device
[ 3630.306817] sr0: rw=0, want=4195576, limit=2097151
[ 3630.306822] attempt to access beyond end of device
[ 3630.306825] sr0: rw=0, want=4195580, limit=2097151
[ 3630.306828] attempt to access beyond end of device
[ 3630.306831] sr0: rw=0, want=4195584, limit=2097151
[ 3630.306836] attempt to access beyond end of device
[ 3630.306839] sr0: rw=0, want=4195588, limit=2097151
[ 3630.306842] attempt to access beyond end of device
[ 3630.306844] sr0: rw=0, want=4195592, limit=2097151
[ 3630.306848] attempt to access beyond end of device
[ 3630.306851] sr0: rw=0, want=4195596, limit=2097151
[ 3630.306854] attempt to access beyond end of device
[ 3630.306857] sr0: rw=0, want=4195600, limit=2097151
[ 3630.306861] attempt to access beyond end of device
[ 3630.306864] sr0: rw=0, want=4195572, limit=2097151
[ 3630.306866] attempt to access beyond end of device
[ 3630.306869] sr0: rw=0, want=4195576, limit=2097151
[ 3630.306875] attempt to access beyond end of device
[ 3630.306878] sr0: rw=0, want=4195572, limit=2097151
[ 3630.306881] attempt to access beyond end of device
[ 3630.306884] sr0: rw=0, want=4195576, limit=2097151
[ 3630.306893] attempt to access beyond end of device
[ 3630.306896] sr0: rw=0, want=4195572, limit=2097151
[ 3630.306898] attempt to access beyond end of device
[ 3630.306901] sr0: rw=0, want=4195576, limit=2097151
[ 3630.307512] attempt to access beyond end of device
[ 3630.307515] sr0: rw=0, want=6292720, limit=2097151
[ 3630.307519] attempt to access beyond end of device
[ 3630.307522] sr0: rw=0, want=6292724, limit=2097151
[ 3630.307527] attempt to access beyond end of device
[ 3630.307530] sr0: rw=0, want=6292728, limit=2097151
[ 3630.307533] attempt to access beyond end of device
[ 3630.307536] sr0: rw=0, want=6292732, limit=2097151
[ 3630.307540] attempt to access beyond end of device
[ 3630.307543] sr0: rw=0, want=6292736, limit=2097151
[ 3630.307546] attempt to access beyond end of device
[ 3630.307548] sr0: rw=0, want=6292740, limit=2097151
[ 3630.307553] attempt to access beyond end of device
[ 3630.307555] sr0: rw=0, want=6292744, limit=2097151
[ 3630.307558] attempt to access beyond end of device
[ 3630.307561] sr0: rw=0, want=6292748, limit=2097151
[ 3630.307564] attempt to access beyond end of device
[ 3630.307567] sr0: rw=0, want=6292720, limit=2097151
[ 3630.307570] attempt to access beyond end of device
[ 3630.307572] sr0: rw=0, want=6292724, limit=2097151
[ 3630.307578] attempt to access beyond end of device
[ 3630.307582] sr0: rw=0, want=6292720, limit=2097151
[ 3630.307584] attempt to access beyond end of device
[ 3630.307587] sr0: rw=0, want=6292724, limit=2097151
[ 3630.307597] attempt to access beyond end of device
[ 3630.307600] sr0: rw=0, want=6292720, limit=2097151
[ 3630.307603] attempt to access beyond end of device
[ 3630.307606] sr0: rw=0, want=6292724, limit=2097151
[ 3630.308235] attempt to access beyond end of device
[ 3630.308239] sr0: rw=0, want=8389868, limit=2097151
[ 3630.308243] attempt to access beyond end of device
[ 3630.308245] sr0: rw=0, want=8389872, limit=2097151
[ 3630.308250] attempt to access beyond end of device
[ 3630.308254] sr0: rw=0, want=8389876, limit=2097151
[ 3630.308257] attempt to access beyond end of device
[ 3630.308260] sr0: rw=0, want=8389880, limit=2097151
[ 3630.308266] attempt to access beyond end of device
[ 3630.308269] sr0: rw=0, want=8389884, limit=2097151
[ 3630.308272] attempt to access beyond end of device
[ 3630.308274] sr0: rw=0, want=8389888, limit=2097151
[ 3630.308278] attempt to access beyond end of device
[ 3630.308281] sr0: rw=0, want=8389892, limit=2097151
[ 3630.308284] attempt to access beyond end of device
[ 3630.308287] sr0: rw=0, want=8389896, limit=2097151
[ 3630.308291] attempt to access beyond end of device
[ 3630.308293] sr0: rw=0, want=8389868, limit=2097151
[ 3630.308296] attempt to access beyond end of device
[ 3630.308298] sr0: rw=0, want=8389872, limit=2097151
[ 3630.308305] attempt to access beyond end of device
[ 3630.308308] sr0: rw=0, want=8389868, limit=2097151
[ 3630.308310] attempt to access beyond end of device
[ 3630.308313] sr0: rw=0, want=8389872, limit=2097151
[ 3630.308322] attempt to access beyond end of device
[ 3630.308326] sr0: rw=0, want=8389868, limit=2097151
[ 3630.308329] attempt to access beyond end of device
[ 3630.308332] sr0: rw=0, want=8389872, limit=2097151
[ 3815.307060] UDF-fs: Partition marked readonly; forcing readonly mount
[ 3815.367022] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DORA_PIRATEADV_EU_AU', timestamp 2005/12/21 05:51 (1078)
[ 4933.934442] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
```

Thanks a bunch for your help.

---

### Post by P4man on 2009-09-12
well, I think you can tell yourself from that log there is a problem :)
i've seen those " Buffer I/O error on device sr0"  in countless bug reports, with solutions ranging from updating the DVD firmware, to upgrading to a newer kernel, to booting with the cd drive open (I kid you not) and changing IDE channel or settings, 

Too many possible causes and solution that i could give you a straightforward answer Im afraid. Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951)

and everywhere else when you google "Buffer I/O error on device sr0".

---

### Post by duckgoesoink on 2009-09-13
Thanks a lot for your input. I had a good look all over the internet, and it's all a bit complicated for me, so I guess I just won't be watching DVDs on Ubuntu anymore.

---

